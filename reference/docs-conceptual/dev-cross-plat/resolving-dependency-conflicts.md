---
title: Résolution des conflits de dépendances d’assembly de module PowerShell
description: Lors de l’écriture d’un module PowerShell binaire en C#, il est naturel de prendre des dépendances envers d’autres packages ou bibliothèques afin de fournir des fonctionnalités.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 93bb39bdd440c7f97c27aa81e68f68331569b69e
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810400"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a><span data-ttu-id="3686b-103">Résolution des conflits de dépendances d’assembly de module PowerShell</span><span class="sxs-lookup"><span data-stu-id="3686b-103">Resolving PowerShell module assembly dependency conflicts</span></span>

<span data-ttu-id="3686b-104">Lors de l’écriture d’un module PowerShell binaire en C#, il est naturel de prendre des dépendances envers d’autres packages ou bibliothèques afin de fournir des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3686b-104">When writing a binary PowerShell module in C#, it's natural to take dependencies on other packages or libraries to provide functionality.</span></span> <span data-ttu-id="3686b-105">Le recours à des dépendances envers d’autres bibliothèques est souhaitable pour la réutilisation du code.</span><span class="sxs-lookup"><span data-stu-id="3686b-105">Taking dependencies on other libraries is desirable for code reuse.</span></span> <span data-ttu-id="3686b-106">PowerShell charge toujours les assemblys dans le même contexte.</span><span class="sxs-lookup"><span data-stu-id="3686b-106">PowerShell always loads assemblies into the same context.</span></span> <span data-ttu-id="3686b-107">Cela pose des problèmes lorsque les dépendances d’un module sont en conflit avec des DLL déjà chargées, et peut empêcher l’utilisation de deux modules autrement non associés dans la même session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-107">This presents issues when a module's dependencies conflict with already-loaded DLLs and may prevent using two otherwise unrelated modules in the same PowerShell session.</span></span>

<span data-ttu-id="3686b-108">Lorsque ce problème se produit, un message d’erreur semblable à celui-ci s’affiche :</span><span class="sxs-lookup"><span data-stu-id="3686b-108">If you've had this problem, you've seen an error message like this:</span></span>

![Message d’erreur de conflit de chargement d’assembly](./media/resolving-dependency-conflicts/moduleconflict.png)

<span data-ttu-id="3686b-110">Cet article examine pourquoi les conflits de dépendances se produisent dans PowerShell, et présente différentes manières d’atténuer les problèmes de conflit de dépendances.</span><span class="sxs-lookup"><span data-stu-id="3686b-110">This article looks at some of the ways dependency conflicts occur in PowerShell and ways to mitigate dependency conflict issues.</span></span> <span data-ttu-id="3686b-111">Même si vous n’êtes pas auteur de module, vous trouverez dans cet article quelques astuces qui pourront vous aider en cas de conflit de dépendances dans les modules que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="3686b-111">Even if you're not a module author, there are some tricks in here that might help you with dependency conflicts occurring in modules that you use.</span></span>

## <a name="why-do-dependency-conflicts-occur"></a><span data-ttu-id="3686b-112">Pourquoi les conflits de dépendances se produisent-ils ?</span><span class="sxs-lookup"><span data-stu-id="3686b-112">Why do dependency conflicts occur?</span></span>

<span data-ttu-id="3686b-113">Dans .NET, les conflits de dépendances se produisent lorsque deux versions du même assembly sont chargées dans le même _contexte de chargement d’assembly_.</span><span class="sxs-lookup"><span data-stu-id="3686b-113">In .NET, dependency conflicts occur when two versions of the same assembly are loaded into the same _Assembly Load Context_.</span></span> <span data-ttu-id="3686b-114">Ce terme signifie des choses légèrement différentes sur différentes plateformes .NET ; nous y reviendrons [plus loin](#powershell-and-net).</span><span class="sxs-lookup"><span data-stu-id="3686b-114">This term means slightly different things on different .NET platforms, which is covered [later](#powershell-and-net).</span></span> <span data-ttu-id="3686b-115">Ce conflit est un problème courant qui se produit dans tout logiciel où des dépendances avec version sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="3686b-115">This conflict is a common problem that occurs in any software where versioned dependencies are used.</span></span> <span data-ttu-id="3686b-116">Étant donné qu’il n’existe pas de solution simple et que de nombreux frameworks de résolution de dépendance essaient de résoudre le problème de différentes façons, cette situation est souvent appelée « enfer des dépendances ».</span><span class="sxs-lookup"><span data-stu-id="3686b-116">Because there are no simple solutions, and because many dependency-resolution frameworks try to solve the problem in different ways, this situation is often called "dependency hell".</span></span>

<span data-ttu-id="3686b-117">Les problèmes de conflits sont accrus par le fait qu’un projet ne dépend presque jamais délibérément ou directement de deux versions de la même dépendance.</span><span class="sxs-lookup"><span data-stu-id="3686b-117">Conflict issues are compounded by the fact that a project almost never deliberately or directly depends on two versions of the same dependency.</span></span> <span data-ttu-id="3686b-118">Au lieu de cela, le projet a deux dépendances (ou plus) qui nécessitent chacune une version différente de la même dépendance.</span><span class="sxs-lookup"><span data-stu-id="3686b-118">Instead, the project has two or more dependencies that each require a different version of the same dependency.</span></span>

<span data-ttu-id="3686b-119">Par exemple, imaginez que votre application .NET, `DuckBuilder`, intègre deux dépendances afin d’exécuter des parties de ses fonctionnalités et ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-119">For example, say your .NET application, `DuckBuilder`, brings in two dependencies, to perform parts of its functionality and looks like this:</span></span>

![Deux dépendances de DuckBuilder reposent sur des versions différentes de Newtonsoft.Json](./media/resolving-dependency-conflicts/dep-conflict.jpg)

<span data-ttu-id="3686b-121">`Contoso.ZipTools` et `Fabrikam.FileHelpers` dépendant tous deux de différentes versions de `Newtonsoft.Json`, il peut y avoir un conflit de dépendances en fonction de la façon dont chaque dépendance est chargée.</span><span class="sxs-lookup"><span data-stu-id="3686b-121">Because `Contoso.ZipTools` and `Fabrikam.FileHelpers` both depend on different versions of `Newtonsoft.Json`, there may be a dependency conflict depending on how each dependency is loaded.</span></span>

### <a name="conflicting-with-powershells-dependencies"></a><span data-ttu-id="3686b-122">Conflits avec les dépendances de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3686b-122">Conflicting with PowerShell's dependencies</span></span>

<span data-ttu-id="3686b-123">Dans PowerShell, le problème de conflit de dépendances est accru car les modules PowerShell et les dépendances propres à PowerShell sont chargés dans le même contexte partagé.</span><span class="sxs-lookup"><span data-stu-id="3686b-123">In PowerShell, the dependency conflict issue is magnified because PowerShell modules and PowerShell's own dependencies are loaded into the same shared context.</span></span> <span data-ttu-id="3686b-124">Cela signifie que le moteur PowerShell et tous les modules PowerShell chargés ne doivent pas avoir de dépendances en conflit.</span><span class="sxs-lookup"><span data-stu-id="3686b-124">This means the PowerShell engine and all loaded PowerShell modules must not have conflicting dependencies.</span></span> <span data-ttu-id="3686b-125">`Newtonsoft.Json` offre un exemple classique :</span><span class="sxs-lookup"><span data-stu-id="3686b-125">A classic example of this is `Newtonsoft.Json`:</span></span>

![Le module FictionalTools dépend d’une version plus récente de Newtonsoft.Json que PowerShell](./media/resolving-dependency-conflicts/engine-conflict.jpg)

<span data-ttu-id="3686b-127">Dans cet exemple, le module `FictionalTools` dépend de la version `12.0.3` de `Newtonsoft.Json`, qui est une version plus récente de `Newtonsoft.Json` que la version `11.0.2` fournie dans l’exemple PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-127">In this example, the module `FictionalTools` depends on `Newtonsoft.Json` version `12.0.3`, which is a newer version of `Newtonsoft.Json` than `11.0.2` that ships in the example PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="3686b-128">Il s’agit uniquement d’un exemple ; PowerShell 7 est actuellement fourni avec `Newtonsoft.Json 12.0.3`.</span><span class="sxs-lookup"><span data-stu-id="3686b-128">This is an example and PowerShell 7 currently ships with `Newtonsoft.Json 12.0.3`.</span></span>

<span data-ttu-id="3686b-129">Étant donné que le module dépend d’une version plus récente de l’assembly, il n’acceptera pas la version que PowerShell a déjà chargée.</span><span class="sxs-lookup"><span data-stu-id="3686b-129">Because the module depends on a newer version of the assembly, it won't accept the version that PowerShell already has loaded.</span></span> <span data-ttu-id="3686b-130">Toutefois, comme PowerShell a déjà chargé une version de l’assembly, le module ne peut pas charger sa propre version à l’aide du mécanisme de chargement conventionnel.</span><span class="sxs-lookup"><span data-stu-id="3686b-130">But because PowerShell has already loaded a version of the assembly, the module can't load its own version using the conventional load mechanism.</span></span>

### <a name="conflicting-with-another-modules-dependencies"></a><span data-ttu-id="3686b-131">Conflits avec les dépendances d’un autre module</span><span class="sxs-lookup"><span data-stu-id="3686b-131">Conflicting with another module's dependencies</span></span>

<span data-ttu-id="3686b-132">Un autre scénario courant dans PowerShell est le chargement d’un module qui dépend d’une version d’un assembly, puis le chargement d’un autre module qui dépend d’une version différente de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="3686b-132">Another common scenario in PowerShell is that a module is loaded that depends on one version of an assembly, and then another module is loaded later that depends on a different version of that assembly.</span></span>

<span data-ttu-id="3686b-133">Cela ressemble souvent à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-133">This often looks like the following:</span></span>

![Deux modules PowerShell nécessitent des versions différentes de la dépendance Microsoft.Extensions.Logging](./media/resolving-dependency-conflicts/mod-conflict.jpg)

<span data-ttu-id="3686b-135">Dans ce cas, le module `FictionalTools` nécessite une version plus récente de `Microsoft.Extensions.Logging` que le module `FilesystemManager`.</span><span class="sxs-lookup"><span data-stu-id="3686b-135">In this case, the `FictionalTools` module requires a newer version of `Microsoft.Extensions.Logging` than the `FilesystemManager` module.</span></span>

<span data-ttu-id="3686b-136">Imaginez que ces modules chargent leurs dépendances en plaçant les assemblys de dépendances dans le même répertoire que l’assembly de module racine.</span><span class="sxs-lookup"><span data-stu-id="3686b-136">Imagine these modules load their dependencies by placing the dependency assemblies in the same directory as the root module assembly.</span></span> <span data-ttu-id="3686b-137">Cela permet à .NET de les charger implicitement par nom.</span><span class="sxs-lookup"><span data-stu-id="3686b-137">This allows .NET to implicitly load them by name.</span></span> <span data-ttu-id="3686b-138">Si nous exécutons PowerShell 7 (sur .NET Core 3.1), nous pouvons charger et exécuter `FictionalTools`, puis charger et exécuter `FilesystemManager` sans problème.</span><span class="sxs-lookup"><span data-stu-id="3686b-138">If we're running PowerShell 7 (on top of .NET Core 3.1), we can load and run `FictionalTools`, then load and run `FilesystemManager` without issue.</span></span> <span data-ttu-id="3686b-139">Toutefois, dans une nouvelle session, si nous chargeons et exécutons `FilesystemManager`, puis chargeons `FictionalTools`, nous recevons une `FileLoadException` à partir de la commande `FictionalTools`, car elle nécessite une version plus récente de `Microsoft.Extensions.Logging` que celle qui est chargée.</span><span class="sxs-lookup"><span data-stu-id="3686b-139">However, in a new session, if we load and run `FilesystemManager`, then load `FictionalTools`, we get a `FileLoadException` from the `FictionalTools` command because it requires a newer version of `Microsoft.Extensions.Logging` than the one loaded.</span></span>
<span data-ttu-id="3686b-140">`FictionalTools` ne peut pas charger la version requise, car un assembly du même nom a déjà été chargé.</span><span class="sxs-lookup"><span data-stu-id="3686b-140">`FictionalTools` can't load the version needed because an assembly of the same name has already been loaded.</span></span>

## <a name="powershell-and-net"></a><span data-ttu-id="3686b-141">PowerShell et .NET</span><span class="sxs-lookup"><span data-stu-id="3686b-141">PowerShell and .NET</span></span>

<span data-ttu-id="3686b-142">PowerShell s’exécute sur la plateforme .NET.</span><span class="sxs-lookup"><span data-stu-id="3686b-142">PowerShell runs on the .NET platform.</span></span> <span data-ttu-id="3686b-143">.NET est en définitive responsable de la résolution et du chargement des dépendances d’assemblys. Nous devons donc comprendre comment .NET opère ici afin de comprendre les conflits de dépendances.</span><span class="sxs-lookup"><span data-stu-id="3686b-143">NET is ultimately responsible for resolving and loading assembly dependencies, so we must understand how .NET operates here to understand dependency conflicts.</span></span>

<span data-ttu-id="3686b-144">Nous devons également gérer le fait que différentes versions de PowerShell s’exécutent sur différentes implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="3686b-144">We must also confront the fact that different versions of PowerShell run on different .NET implementations.</span></span> <span data-ttu-id="3686b-145">En général, PowerShell 5.1 et versions antérieures s’exécutent sur le .NET Framework, tandis que PowerShell 6 et versions ultérieures s’exécutent sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3686b-145">In general, PowerShell 5.1 and below run on .NET Framework, while PowerShell 6 and above run on .NET Core.</span></span> <span data-ttu-id="3686b-146">Ces deux implémentations de .NET chargent et gèrent les assemblys différemment.</span><span class="sxs-lookup"><span data-stu-id="3686b-146">These two implementations of .NET load and handle assemblies differently.</span></span>
<span data-ttu-id="3686b-147">Cela signifie que la résolution des conflits de dépendances peut varier en fonction de la plateforme .NET sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="3686b-147">This means that resolving dependency conflicts can vary depending on the underlying .NET platform.</span></span>

### <a name="assembly-load-contexts"></a><span data-ttu-id="3686b-148">Contextes de chargement d’assembly</span><span class="sxs-lookup"><span data-stu-id="3686b-148">Assembly Load Contexts</span></span>

<span data-ttu-id="3686b-149">Dans .NET, un _contexte de chargement d’assembly_ (ALC, Assembly Load Context) est un espace de noms de runtime dans lequel des assemblys sont chargés.</span><span class="sxs-lookup"><span data-stu-id="3686b-149">In .NET, an _Assembly Load Context_ (ALC) that is a runtime namespace into which assemblies are loaded.</span></span> <span data-ttu-id="3686b-150">Les noms des assemblys doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="3686b-150">The assemblies' names must be unique.</span></span> <span data-ttu-id="3686b-151">Ce concept permet aux assemblys d’être résolus de manière unique par nom dans chaque ALC.</span><span class="sxs-lookup"><span data-stu-id="3686b-151">This concept allows assemblies to be uniquely resolved by name in each ALC.</span></span>

### <a name="assembly-reference-loading-in-net"></a><span data-ttu-id="3686b-152">Chargement des références d’assembly dans .NET</span><span class="sxs-lookup"><span data-stu-id="3686b-152">Assembly reference loading in .NET</span></span>

<span data-ttu-id="3686b-153">La sémantique du chargement d’assembly dépend à la fois de l’implémentation .NET (.NET Core ou .NET Framework) et de l’API .NET utilisée pour charger un assembly particulier.</span><span class="sxs-lookup"><span data-stu-id="3686b-153">The semantics of assembly loading depend on both the .NET implementation (.NET Core vs .NET Framework) and the .NET API used to load a particular assembly.</span></span> <span data-ttu-id="3686b-154">Plutôt que d’entrer ici dans les détails, nous vous invitons à consulter les liens fournis dans la section [Lectures supplémentaires](#further-reading), qui expliquent en détail le fonctionnement du chargement d’assembly .NET dans chaque implémentation .NET.</span><span class="sxs-lookup"><span data-stu-id="3686b-154">Rather than go into detail here, there are links in the [Further reading](#further-reading) section that go into great detail on how .NET assembly loading works in each .NET implementation.</span></span>

<span data-ttu-id="3686b-155">Dans cet article, nous allons faire référence aux mécanismes suivants :</span><span class="sxs-lookup"><span data-stu-id="3686b-155">In this article we'll refer to the following mechanisms:</span></span>

- <span data-ttu-id="3686b-156">Chargement d’assembly implicite (`Assembly.Load(AssemblyName)`), lorsque .NET essaie de charger un assembly par nom à partir d’une référence d’assembly statique dans du code .NET</span><span class="sxs-lookup"><span data-stu-id="3686b-156">Implicit assembly loading (effectively `Assembly.Load(AssemblyName)`), when .NET implicitly tries to load an assembly by name from a static assembly reference in .NET code.</span></span>
- <span data-ttu-id="3686b-157">`Assembly.LoadFrom()`, une API de chargement orientée plug-in qui ajoute des gestionnaires pour résoudre les dépendances de la DLL chargée.</span><span class="sxs-lookup"><span data-stu-id="3686b-157">`Assembly.LoadFrom()`, a plugin-oriented loading API that adds handlers to resolve dependencies of the loaded DLL.</span></span> <span data-ttu-id="3686b-158">Cette méthode est susceptible de ne pas résoudre les dépendances comme nous le souhaitons</span><span class="sxs-lookup"><span data-stu-id="3686b-158">This method may not resolve dependencies the way we want.</span></span>
- <span data-ttu-id="3686b-159">`Assembly.LoadFile()`, une API de chargement de base censée charger uniquement l’assembly demandé, et qui ne gère pas de dépendances</span><span class="sxs-lookup"><span data-stu-id="3686b-159">`Assembly.LoadFile()`, a basic loading API intended to load only the assembly asked for and does not handle any dependencies.</span></span>

### <a name="differences-in-net-framework-vs-net-core"></a><span data-ttu-id="3686b-160">Différences entre le .NET Framework et .NET Core</span><span class="sxs-lookup"><span data-stu-id="3686b-160">Differences in .NET Framework vs .NET Core</span></span>

<span data-ttu-id="3686b-161">Le fonctionnement de ces API a changé de manière subtile entre .NET Core et le .NET Framework. Il est donc utile de consulter les [liens](#further-reading) proposés.</span><span class="sxs-lookup"><span data-stu-id="3686b-161">The way these APIs work has changed in subtle ways between .NET Core and .NET Framework, so it's worth reading through the included [links](#further-reading).</span></span> <span data-ttu-id="3686b-162">Il convient surtout de remarquer que les contextes de chargement d’assembly et d’autres mécanismes de résolution d’assembly ont changé entre le .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3686b-162">Importantly, Assembly Load Contexts and other assembly resolution mechanisms have changed between .NET Framework and .NET Core.</span></span>

<span data-ttu-id="3686b-163">En particulier, le .NET Framework dispose des fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="3686b-163">In particular, .NET Framework has the following features:</span></span>

- <span data-ttu-id="3686b-164">Le Global Assembly Cache, pour la résolution d’assembly à l’échelle de la machine</span><span class="sxs-lookup"><span data-stu-id="3686b-164">The Global Assembly Cache, for machine-wide assembly resolution</span></span>
- <span data-ttu-id="3686b-165">Des domaines d’application, qui opèrent comme des bacs à sable en mode in-process pour l’isolation d’assembly, mais présentent également une couche de sérialisation à gérer</span><span class="sxs-lookup"><span data-stu-id="3686b-165">Application Domains, which work like in-process sandboxes for assembly isolation, but also present a serialization layer to contend with</span></span>
- <span data-ttu-id="3686b-166">Un modèle de contexte de chargement d’assembly limité, expliqué en détail [ici](/dotnet/framework/deployment/best-practices-for-assembly-loading), qui a un ensemble fixe de contextes de chargement d’assembly, chacun avec son propre comportement :</span><span class="sxs-lookup"><span data-stu-id="3686b-166">A limited assembly load context model, explained in depth [here](/dotnet/framework/deployment/best-practices-for-assembly-loading), that has a fixed set of assembly load contexts, each with their own behavior:</span></span>
  - <span data-ttu-id="3686b-167">Le contexte de chargement par défaut, où les assemblys sont chargés par défaut</span><span class="sxs-lookup"><span data-stu-id="3686b-167">The default load context, where assemblies are loaded by default</span></span>
  - <span data-ttu-id="3686b-168">Le contexte de chargement source, pour le chargement manuel des assemblys au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="3686b-168">The load-from context, for loading assemblies manually at runtime</span></span>
  - <span data-ttu-id="3686b-169">Le contexte de réflexion uniquement, pour le chargement sécurisé d’assemblys afin de lire leurs métadonnées sans les exécuter</span><span class="sxs-lookup"><span data-stu-id="3686b-169">The reflection-only context, for safely loading assemblies to read their metadata without running them</span></span>
  - <span data-ttu-id="3686b-170">Le mystérieux vide dans lequel résident les assemblys chargés avec `Assembly.LoadFile(string path)` et `Assembly.Load(byte[] asmBytes)`</span><span class="sxs-lookup"><span data-stu-id="3686b-170">The mysterious void that assemblies loaded with `Assembly.LoadFile(string path)` and `Assembly.Load(byte[] asmBytes)` live in</span></span>

<span data-ttu-id="3686b-171">.NET Core (et .NET 5+) a remplacé cette complexité par un modèle plus simple :</span><span class="sxs-lookup"><span data-stu-id="3686b-171">.NET Core (and .NET 5+) has replaced this complexity with a simpler model:</span></span>

- <span data-ttu-id="3686b-172">Aucun Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="3686b-172">No Global Assembly Cache.</span></span> <span data-ttu-id="3686b-173">Les applications apportent toutes leurs propres dépendances.</span><span class="sxs-lookup"><span data-stu-id="3686b-173">Applications bring all their own dependencies.</span></span> <span data-ttu-id="3686b-174">Cela supprime un facteur externe pour la résolution des dépendances dans les applications, ce qui rend la résolution des dépendances plus reproductible.</span><span class="sxs-lookup"><span data-stu-id="3686b-174">This removes an external factor for dependency resolution in applications, making dependency resolution more reproducible.</span></span>
  <span data-ttu-id="3686b-175">PowerShell, en tant qu’hôte de plug-in, complique légèrement cela pour les modules.</span><span class="sxs-lookup"><span data-stu-id="3686b-175">PowerShell, as the plugin host, complicates this slightly for modules.</span></span> <span data-ttu-id="3686b-176">Ses dépendances dans `$PSHOME` sont partagées avec tous les modules</span><span class="sxs-lookup"><span data-stu-id="3686b-176">Its dependencies in `$PSHOME` are shared with all modules.</span></span>
- <span data-ttu-id="3686b-177">Un seul domaine d’application et aucune possibilité d’en créer de nouveaux.</span><span class="sxs-lookup"><span data-stu-id="3686b-177">Only one Application Domain, and no ability to create new ones.</span></span> <span data-ttu-id="3686b-178">Le concept Domaine d’application est conservé dans .NET Core uniquement pour être l’état global du processus .NET</span><span class="sxs-lookup"><span data-stu-id="3686b-178">The Application Domain concept is maintained in .NET Core purely to be the global state of the .NET process.</span></span>
- <span data-ttu-id="3686b-179">Un nouveau modèle de contexte de chargement d’assembly extensible.</span><span class="sxs-lookup"><span data-stu-id="3686b-179">A new, extensible Assembly Load Context model.</span></span> <span data-ttu-id="3686b-180">La résolution d’assembly peut être limitée à un espace de noms en la plaçant dans un nouvel ALC.</span><span class="sxs-lookup"><span data-stu-id="3686b-180">Assembly resolution can be namespaced by putting it in a new ALC.</span></span> <span data-ttu-id="3686b-181">Les processus .NET Core commencent par un ALC unique par défaut dans lequel tous les assemblys sont chargés</span><span class="sxs-lookup"><span data-stu-id="3686b-181">.NET Core processes begin with a single default ALC into which all assemblies are loaded.</span></span> <span data-ttu-id="3686b-182">(à l’exception de ceux chargés avec `Assembly.LoadFile(string)` et `Assembly.Load(byte[])`), mais le processus peut créer et définir ses propres ALC personnalisés avec sa propre logique de chargement.</span><span class="sxs-lookup"><span data-stu-id="3686b-182">(except for those loaded with `Assembly.LoadFile(string)` and `Assembly.Load(byte[])`) But the process can create and define its own custom ALCs with its own loading logic.</span></span> <span data-ttu-id="3686b-183">Lorsqu’un assembly est chargé, le premier ALC dans lequel il est chargé est responsable de la résolution de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="3686b-183">When an assembly is loaded, the first ALC it is loaded into is responsible for resolving its dependencies.</span></span> <span data-ttu-id="3686b-184">Cela permet d’implémenter de puissants mécanismes de chargement de plug-ins .NET</span><span class="sxs-lookup"><span data-stu-id="3686b-184">This creates opportunities to implement powerful .NET plugin loading mechanisms.</span></span>

<span data-ttu-id="3686b-185">Dans les deux implémentations, les assemblys sont chargés tardivement.</span><span class="sxs-lookup"><span data-stu-id="3686b-185">In both implementations, assemblies are loaded lazily.</span></span> <span data-ttu-id="3686b-186">Cela signifie qu’ils sont chargés lorsqu’une méthode nécessitant leur type est exécutée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="3686b-186">This means that they are loaded when a method requiring their type is run for the first time.</span></span>

<span data-ttu-id="3686b-187">Voici par exemple deux versions du même code qui chargent une dépendance à différents moments.</span><span class="sxs-lookup"><span data-stu-id="3686b-187">For example, here are two versions of the same code that load a dependency at different times.</span></span>

<span data-ttu-id="3686b-188">La première charge toujours sa dépendance lorsque `Program.GetRange()` est appelée, car la référence de dépendance est présente lexicalement dans la méthode :</span><span class="sxs-lookup"><span data-stu-id="3686b-188">The first always loads its dependency when `Program.GetRange()` is called, because the dependency reference is lexically present within the method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

<span data-ttu-id="3686b-189">La seconde charge sa dépendance uniquement si le paramètre `limit` est supérieur ou égal à 20, en raison de l’indirection interne via une méthode :</span><span class="sxs-lookup"><span data-stu-id="3686b-189">The second will load its dependency only if the `limit` parameter is 20 or more, because of the internal indirection through a method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

<span data-ttu-id="3686b-190">Il s’agit d’une bonne pratique, car elle réduit la mémoire et les E/S de système de fichiers, et utilise plus efficacement les ressources.</span><span class="sxs-lookup"><span data-stu-id="3686b-190">This is a good practice since it minimizes the memory and filesystem I/O and uses the resources more efficiently.</span></span> <span data-ttu-id="3686b-191">Malheureusement, l’un des effets secondaires est que nous ne savons pas que le chargement de l’assembly a échoué tant que nous n’avons pas atteint le chemin du code qui tente de charger l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3686b-191">The unfortunate a side effect of this is that we won't know that the assembly fails to load until we reach the code path that tries to load the assembly.</span></span>

<span data-ttu-id="3686b-192">Cela peut également créer une condition de minutage pour les conflits de chargement d’assembly.</span><span class="sxs-lookup"><span data-stu-id="3686b-192">It can also create a timing condition for assembly load conflicts.</span></span> <span data-ttu-id="3686b-193">Si deux parties du même programme tentent de charger différentes versions du même assembly, la version chargée dépend du chemin du code exécuté en premier.</span><span class="sxs-lookup"><span data-stu-id="3686b-193">If two parts of the same program try to load different versions of the same assembly, the version loaded depends on which code path is run first.</span></span>

<span data-ttu-id="3686b-194">Pour PowerShell, cela signifie que les facteurs suivants peuvent affecter un conflit de chargement d’assembly :</span><span class="sxs-lookup"><span data-stu-id="3686b-194">For PowerShell, this means that the following factors can affect an assembly load conflict:</span></span>

- <span data-ttu-id="3686b-195">Quel a été le module chargé en premier ?</span><span class="sxs-lookup"><span data-stu-id="3686b-195">Which module was loaded first?</span></span>
- <span data-ttu-id="3686b-196">Le chemin du code qui utilise la bibliothèque de dépendances a-t-il été exécuté ?</span><span class="sxs-lookup"><span data-stu-id="3686b-196">Was the code path that uses the dependency library run?</span></span>
- <span data-ttu-id="3686b-197">PowerShell charge-t-il une dépendance en conflit au démarrage ou uniquement sous certains chemins du code ?</span><span class="sxs-lookup"><span data-stu-id="3686b-197">Does PowerShell load a conflicting dependency at startup or only under certain code paths?</span></span>

## <a name="quick-fixes-and-their-limitations"></a><span data-ttu-id="3686b-198">Correctifs rapides et limitations</span><span class="sxs-lookup"><span data-stu-id="3686b-198">Quick fixes and their limitations</span></span>

<span data-ttu-id="3686b-199">Dans certains cas, il est possible d’effectuer de petits ajustements sur votre module et de résoudre les problèmes avec un minimum d’effort.</span><span class="sxs-lookup"><span data-stu-id="3686b-199">In some cases, it's possible to make small adjustments to your module and fix things with minimal effort.</span></span> <span data-ttu-id="3686b-200">Toutefois, ces solutions ont tendance à présenter des inconvénients.</span><span class="sxs-lookup"><span data-stu-id="3686b-200">But these solutions tend to come with caveats.</span></span> <span data-ttu-id="3686b-201">Même si elles peuvent s’appliquer à votre module, elles ne fonctionneront pas pour chaque module.</span><span class="sxs-lookup"><span data-stu-id="3686b-201">While they may apply to your module, they won't work for every module.</span></span>

### <a name="change-your-dependency-version"></a><span data-ttu-id="3686b-202">Changer votre version de dépendance</span><span class="sxs-lookup"><span data-stu-id="3686b-202">Change your dependency version</span></span>

<span data-ttu-id="3686b-203">Le moyen le plus simple d’éviter les conflits de dépendance consiste à s’accorder sur une dépendance.</span><span class="sxs-lookup"><span data-stu-id="3686b-203">The simplest way to avoid dependency conflicts is to agree on a dependency.</span></span> <span data-ttu-id="3686b-204">Cela peut être possible dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="3686b-204">This may be possible when:</span></span>

- <span data-ttu-id="3686b-205">Votre conflit concerne une dépendance directe de votre module et vous contrôlez la version</span><span class="sxs-lookup"><span data-stu-id="3686b-205">Your conflict is with a direct dependency of your module and you control the version.</span></span>
- <span data-ttu-id="3686b-206">Votre conflit concerne une dépendance indirecte, mais vous pouvez configurer vos dépendances directes de façon à utiliser une version de dépendance indirecte exploitable</span><span class="sxs-lookup"><span data-stu-id="3686b-206">Your conflict is with an indirect dependency, but you can configure your direct dependencies to use a workable indirect dependency version.</span></span>
- <span data-ttu-id="3686b-207">Vous connaissez la version en conflit et vous pouvez vous fier à ce qu’elle ne change pas</span><span class="sxs-lookup"><span data-stu-id="3686b-207">You know the conflicting version and can rely on it not changing.</span></span>

<span data-ttu-id="3686b-208">Le package `Newtonsoft.Json` est un bon exemple de ce dernier scénario.</span><span class="sxs-lookup"><span data-stu-id="3686b-208">The `Newtonsoft.Json` package is a good example of this last scenario.</span></span> <span data-ttu-id="3686b-209">Il s’agit d’une dépendance de PowerShell 6 et versions ultérieures, et il n’est pas utilisé dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-209">This is a dependency of PowerShell 6 and above, and isn't used in Windows PowerShell.</span></span> <span data-ttu-id="3686b-210">Cela signifie qu’un moyen simple de résoudre les conflits de gestion de versions consiste à cibler la version la plus basse de `Newtonsoft.Json` sur les versions de PowerShell que vous souhaitez cibler.</span><span class="sxs-lookup"><span data-stu-id="3686b-210">Meaning a simple way to resolve versioning conflicts is to target the lowest version of `Newtonsoft.Json` across the PowerShell versions you wish to target.</span></span>

<span data-ttu-id="3686b-211">Par exemple, PowerShell 6.2.6 et PowerShell 7.0.2 utilisent actuellement `Newtonsoft.Json` version 12.0.3.</span><span class="sxs-lookup"><span data-stu-id="3686b-211">For example, PowerShell 6.2.6 and PowerShell 7.0.2 both currently use `Newtonsoft.Json` version 12.0.3.</span></span> <span data-ttu-id="3686b-212">Ainsi, pour créer un module ciblant Windows PowerShell, PowerShell 6 et PowerShell 7, vous devez cibler `Newtonsoft.Json 12.0.3` en tant que dépendance et l’inclure dans votre module intégré.</span><span class="sxs-lookup"><span data-stu-id="3686b-212">So, to create a module targeting Windows PowerShell, PowerShell 6, and PowerShell 7, you would target `Newtonsoft.Json 12.0.3` as a dependency and include it in your built module.</span></span> <span data-ttu-id="3686b-213">Quand le module est chargé dans PowerShell 6 ou 7, le propre assembly `Newtonsoft.Json` de PowerShell est déjà chargé.</span><span class="sxs-lookup"><span data-stu-id="3686b-213">When the module is loaded in PowerShell 6 or 7, PowerShell's own `Newtonsoft.Json` assembly is already loaded.</span></span> <span data-ttu-id="3686b-214">En outre, puisqu’il s’agit au moins de la version requise pour votre module, la résolution réussit.</span><span class="sxs-lookup"><span data-stu-id="3686b-214">Also, it is at least the version required for your module, so resolution succeeds.</span></span> <span data-ttu-id="3686b-215">Dans Windows PowerShell, l’assembly n’est pas encore présent dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-215">In Windows PowerShell, the assembly isn't already present in PowerShell.</span></span> <span data-ttu-id="3686b-216">Il est donc chargé à partir de votre dossier de module.</span><span class="sxs-lookup"><span data-stu-id="3686b-216">So, it's loaded from your module folder instead.</span></span>

<span data-ttu-id="3686b-217">En général, lorsque vous ciblez un package PowerShell concret, comme `Microsoft.PowerShell.Sdk` ou `System.Management.Automation`, NuGet doit être en mesure de résoudre les bonnes versions de dépendance requises.</span><span class="sxs-lookup"><span data-stu-id="3686b-217">Generally, when targeting a concrete PowerShell package, like `Microsoft.PowerShell.Sdk` or `System.Management.Automation`, NuGet should be able to resolve the right dependency versions required.</span></span> <span data-ttu-id="3686b-218">Cibler à la fois Windows PowerShell et PowerShell 6+ devient plus difficile, car vous devez choisir entre le ciblage de plusieurs frameworks ou de `PowerShellStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="3686b-218">Targeting both Windows PowerShell and PowerShell 6+ becomes more difficult because you must choose between targeting multiple frameworks or `PowerShellStandard.Library`.</span></span>

<span data-ttu-id="3686b-219">Voici quelques cas où l’épinglage sur une version de dépendance commune ne fonctionnera pas :</span><span class="sxs-lookup"><span data-stu-id="3686b-219">Circumstances where pinning to a common dependency version won't work include:</span></span>

- <span data-ttu-id="3686b-220">Le conflit concerne une dépendance indirecte, et aucune de vos dépendances ne peut être configurée pour utiliser une version commune</span><span class="sxs-lookup"><span data-stu-id="3686b-220">The conflict is with an indirect dependency, and none of your dependencies can be configured to use a common version.</span></span>
- <span data-ttu-id="3686b-221">L’autre version de dépendance est susceptible de changer souvent. Par conséquent, le fait de se fixer sur une version commune n’est qu’un correctif à court terme</span><span class="sxs-lookup"><span data-stu-id="3686b-221">The other dependency version is likely to change often, so settling on a common version is only a short-term fix.</span></span>

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a><span data-ttu-id="3686b-222">Ajouter un gestionnaire d’événements AssemblyResolve pour créer une redirection de liaison dynamique</span><span class="sxs-lookup"><span data-stu-id="3686b-222">Add an AssemblyResolve event handler to create a dynamic binding redirect</span></span>

<span data-ttu-id="3686b-223">Parfois, la modification de votre propre version de dépendance n’est pas possible ou est trop difficile.</span><span class="sxs-lookup"><span data-stu-id="3686b-223">Sometimes changing your own dependency version isn't possible or is too difficult.</span></span> <span data-ttu-id="3686b-224">Une autre option consiste à configurer une redirection de liaison dynamique en inscrivant un gestionnaire d’événements pour l’événement `AssemblyResolve`.</span><span class="sxs-lookup"><span data-stu-id="3686b-224">Another option is to set up a dynamic binding redirect by registering an event handler for the `AssemblyResolve` event.</span></span>

<span data-ttu-id="3686b-225">Comme avec une redirection de liaison statique, l’objectif est de forcer tous les consommateurs d’une dépendance à utiliser le même assembly.</span><span class="sxs-lookup"><span data-stu-id="3686b-225">As with a static binding redirect, the point is to force all consumers of a dependency to use the same actual assembly.</span></span> <span data-ttu-id="3686b-226">Vous interceptez les appels de chargement de la dépendance et les redirigez toujours vers la version souhaitée.</span><span class="sxs-lookup"><span data-stu-id="3686b-226">You intercept calls to load the dependency and always redirect them to the version you want.</span></span>

<span data-ttu-id="3686b-227">Cela ressemble un peu à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="3686b-227">This looks something like this:</span></span>

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

<span data-ttu-id="3686b-228">Techniquement, vous pouvez inscrire un scriptblock dans PowerShell afin de gérer un événement `AssemblyResolve`, mais :</span><span class="sxs-lookup"><span data-stu-id="3686b-228">You can technically register a scriptblock within PowerShell to handle an `AssemblyResolve` event, but:</span></span>

- <span data-ttu-id="3686b-229">Un événement `AssemblyResolve` peut être déclenché sur n’importe quel thread, ce que PowerShell ne pourra pas gérer</span><span class="sxs-lookup"><span data-stu-id="3686b-229">An `AssemblyResolve` event may be triggered on any thread, something that PowerShell will be unable to handle.</span></span>
- <span data-ttu-id="3686b-230">Même lorsque les événements sont gérés sur le bon thread, les concepts de portée de PowerShell signifient que le scriptblck du gestionnaire d’événements doit être écrit avec soin afin de ne pas dépendre de variables définies en dehors.</span><span class="sxs-lookup"><span data-stu-id="3686b-230">Even when events are handled on the right thread, PowerShell's scoping concepts mean that the event handler scriptblock must be written carefully to not depend on variables defined outside it.</span></span>

<span data-ttu-id="3686b-231">Il existe des situations où la redirection vers une version commune ne fonctionnera pas :</span><span class="sxs-lookup"><span data-stu-id="3686b-231">There are situations where redirecting to a common version won't work:</span></span>

- <span data-ttu-id="3686b-232">Lorsque la dépendance a apporté des changements cassants entre les versions, ou lorsque le code dépendant s’appuie sur une fonctionnalité non disponible dans la version vers laquelle vous redirigez</span><span class="sxs-lookup"><span data-stu-id="3686b-232">When the dependency has made breaking changes between versions, or when dependent code relies on a functionality otherwise not available in the version you redirect to.</span></span>
- <span data-ttu-id="3686b-233">Lorsque votre module n’est pas chargé avant la dépendance en conflit.</span><span class="sxs-lookup"><span data-stu-id="3686b-233">When your module isn't loaded before the conflicting dependency.</span></span> <span data-ttu-id="3686b-234">Si vous inscrivez un gestionnaire d’événements `AssemblyResolve` après le chargement de la dépendance, il ne sera jamais déclenché.</span><span class="sxs-lookup"><span data-stu-id="3686b-234">If you register an `AssemblyResolve` event handler after the dependency has been loaded, it will never be fired.</span></span> <span data-ttu-id="3686b-235">Si vous essayez d’éviter les conflits de dépendances avec un autre module, cela peut poser un problème, étant donné que l’autre module peut être chargé en premier</span><span class="sxs-lookup"><span data-stu-id="3686b-235">If you're trying to prevent dependency conflicts with another module, this may be an issue, since the other module may be loaded first.</span></span>

### <a name="use-the-dependency-out-of-process"></a><span data-ttu-id="3686b-236">Utiliser la dépendance hors processus</span><span class="sxs-lookup"><span data-stu-id="3686b-236">Use the dependency out of process</span></span>

<span data-ttu-id="3686b-237">Cette solution concerne davantage les utilisateurs de module que les auteurs de module.</span><span class="sxs-lookup"><span data-stu-id="3686b-237">This solution is more for module users than module authors.</span></span> <span data-ttu-id="3686b-238">Elle convient lorsque vous êtes confronté à un module qui ne fonctionne pas en raison d’un conflit de dépendance existant.</span><span class="sxs-lookup"><span data-stu-id="3686b-238">This is a solution to use when confronted with a module that won't work due to an existing dependency conflict.</span></span>

<span data-ttu-id="3686b-239">Les conflits de dépendances se produisent car deux versions du même assembly sont chargées dans le même processus .NET.</span><span class="sxs-lookup"><span data-stu-id="3686b-239">Dependency conflicts occur because two versions of the same assembly are loaded into the same .NET process.</span></span> <span data-ttu-id="3686b-240">Une solution simple consiste à les charger dans des processus différents, à condition que vous puissiez toujours utiliser les fonctionnalités des deux processus ensemble.</span><span class="sxs-lookup"><span data-stu-id="3686b-240">A simple solution is to load them into different processes, as long as you can still use the functionality from both together.</span></span>

<span data-ttu-id="3686b-241">Dans PowerShell, il existe plusieurs façons d’y parvenir :</span><span class="sxs-lookup"><span data-stu-id="3686b-241">In PowerShell, there are several ways to achieve this:</span></span>

- <span data-ttu-id="3686b-242">Appeler PowerShell en tant que sous-processus</span><span class="sxs-lookup"><span data-stu-id="3686b-242">Invoke PowerShell as a subprocess</span></span>

  <span data-ttu-id="3686b-243">Un moyen simple d’exécuter une commande PowerShell en dehors du processus actuel consiste à démarrer un nouveau processus PowerShell directement avec l’appel de commande :</span><span class="sxs-lookup"><span data-stu-id="3686b-243">A simple way to run a PowerShell command out of the current process is to just start a new PowerShell process directly with the command call:</span></span>

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  <span data-ttu-id="3686b-244">La limitation principale ici est que la restructuration du résultat peut être plus délicate ou plus sujette aux erreurs que d’autres options.</span><span class="sxs-lookup"><span data-stu-id="3686b-244">The main limitation here is that restructuring the result can be trickier or more error prone than other options.</span></span>

- <span data-ttu-id="3686b-245">Système de travail PowerShell</span><span class="sxs-lookup"><span data-stu-id="3686b-245">The PowerShell job system</span></span>

  <span data-ttu-id="3686b-246">Le système de travail PowerShell exécute également des commandes hors processus, en envoyant des commandes à un nouveau processus PowerShell et en retournant les résultats :</span><span class="sxs-lookup"><span data-stu-id="3686b-246">The PowerShell job system also runs commands out of process, by sending commands to a new PowerShell process and returning the results:</span></span>

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  <span data-ttu-id="3686b-247">Dans ce cas, vous devez simplement vous assurer que les variables et l’état sont transmis correctement.</span><span class="sxs-lookup"><span data-stu-id="3686b-247">In this case, you just need to be sure that any variables and state are passed in correctly.</span></span>

  <span data-ttu-id="3686b-248">Le système de travail peut également être un peu lourd quand vous exécutez des commandes de petite taille.</span><span class="sxs-lookup"><span data-stu-id="3686b-248">The job system can also be slightly cumbersome when running small commands.</span></span>

- <span data-ttu-id="3686b-249">Communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="3686b-249">PowerShell remoting</span></span>

  <span data-ttu-id="3686b-250">Lorsqu’elle est disponible, la communication à distance PowerShell peut être un moyen pratique d’exécuter des commandes hors processus.</span><span class="sxs-lookup"><span data-stu-id="3686b-250">When it's available, PowerShell remoting can be a useful way to run commands out of process.</span></span> <span data-ttu-id="3686b-251">Avec elle, vous pouvez créer une nouvelle **PSSession** dans un nouveau processus, appeler ses commandes via la communication à distance PowerShell, puis utiliser les résultats localement avec les autres modules contenant les dépendances en conflit.</span><span class="sxs-lookup"><span data-stu-id="3686b-251">With remoting, you can create a fresh **PSSession** in a new process, call its commands over PowerShell remoting, then use the results locally with the other modules containing the conflicting dependencies.</span></span>

  <span data-ttu-id="3686b-252">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="3686b-252">An example might look like this:</span></span>

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- <span data-ttu-id="3686b-253">Communication à distance implicite vers Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3686b-253">Implicit remoting to Windows PowerShell</span></span>

  <span data-ttu-id="3686b-254">Dans PowerShell 7, une autre option consiste à utiliser l’indicateur `-UseWindowsPowerShell` sur `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="3686b-254">Another option in PowerShell 7 is to use the `-UseWindowsPowerShell` flag on `Import-Module`.</span></span> <span data-ttu-id="3686b-255">Cela permet d’importer le module par le biais d’une session de communication à distance locale dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="3686b-255">This will import the module through a local remoting session into Windows PowerShell:</span></span>

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  <span data-ttu-id="3686b-256">Sachez toutefois que les modules peuvent ne pas fonctionner avec Windows PowerShell ou fonctionner différemment.</span><span class="sxs-lookup"><span data-stu-id="3686b-256">Be aware that modules may not work with, or work differently with Windows PowerShell.</span></span>

#### <a name="when-out-of-process-invocation-should-not-be-used"></a><span data-ttu-id="3686b-257">Quand ne faut-il pas utiliser l’appel hors processus ?</span><span class="sxs-lookup"><span data-stu-id="3686b-257">When out-of-process invocation should not be used</span></span>

<span data-ttu-id="3686b-258">En tant qu’auteur de module, l’appel de commande hors processus est difficile à intégrer dans un module et peut présenter des cas litigieux susceptibles de provoquer des problèmes.</span><span class="sxs-lookup"><span data-stu-id="3686b-258">As a module author, out-of-process command invocation is difficult to bake into a module and may have edge cases that cause issues.</span></span> <span data-ttu-id="3686b-259">En particulier, la communication à distance et les travaux peuvent ne pas être disponibles dans tous les environnements où votre module doit fonctionner.</span><span class="sxs-lookup"><span data-stu-id="3686b-259">In particular, remoting and jobs may not be available in all environments where your module needs to work.</span></span> <span data-ttu-id="3686b-260">Toutefois, le principe général consistant à déplacer l’implémentation hors processus et à permettre au module PowerShell d’être un client allégé peut toujours s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="3686b-260">However, the general principle of moving the implementation out of process and allowing the PowerShell module to be a thinner client, may still be applicable.</span></span>

<span data-ttu-id="3686b-261">En tant qu’utilisateur de module, il existe des cas où l’appel hors processus ne fonctionnera pas :</span><span class="sxs-lookup"><span data-stu-id="3686b-261">As a module user, there are cases where out-of-process invocation won't work:</span></span>

- <span data-ttu-id="3686b-262">Lorsque la communication à distance PowerShell n’est pas disponible car vous n’avez pas les privilèges nécessaires pour l’utiliser ou elle n’est pas activée</span><span class="sxs-lookup"><span data-stu-id="3686b-262">When PowerShell remoting is unavailable because you don't have privileges to use it or it is not enabled.</span></span>
- <span data-ttu-id="3686b-263">Lorsqu’un type .NET particulier doit être généré en tant qu’entrée d’une méthode ou d’une autre commande.</span><span class="sxs-lookup"><span data-stu-id="3686b-263">When a particular .NET type is needed from output as input to a method or another command.</span></span>
  <span data-ttu-id="3686b-264">Les commandes qui s’exécutent via la communication à distance PowerShell émettent des objets désérialisés plutôt que des objets .NET fortement typés.</span><span class="sxs-lookup"><span data-stu-id="3686b-264">Commands running over PowerShell remoting emit deserialized objects rather than strongly-typed .NET objects.</span></span> <span data-ttu-id="3686b-265">Cela signifie que les appels de méthode et les API fortement typées ne fonctionnent pas avec la sortie des commandes importées via la communication à distance</span><span class="sxs-lookup"><span data-stu-id="3686b-265">This means that method calls and strongly typed APIs do not work with the output of commands imported over remoting.</span></span>

## <a name="more-robust-solutions"></a><span data-ttu-id="3686b-266">Solutions plus robustes</span><span class="sxs-lookup"><span data-stu-id="3686b-266">More robust solutions</span></span>

<span data-ttu-id="3686b-267">Avec toutes les solutions précédentes, certains scénarios et modules ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="3686b-267">The previous solutions all had scenarios and modules that don't work.</span></span> <span data-ttu-id="3686b-268">Elles ont toutefois l’avantage d’être relativement simples à implémenter correctement.</span><span class="sxs-lookup"><span data-stu-id="3686b-268">However, they also have the virtue of being relatively simple to implement correctly.</span></span> <span data-ttu-id="3686b-269">Les solutions suivantes sont plus robustes, mais leur implémentation correcte nécessite davantage d’efforts et elles peuvent introduire des bogues subtils si elles ne sont pas écrites avec précaution.</span><span class="sxs-lookup"><span data-stu-id="3686b-269">The following solutions are more robust, but require more effort to implement correctly and can introduce subtle bugs if not written carefully.</span></span>

### <a name="loading-through-net-core-assembly-load-contexts"></a><span data-ttu-id="3686b-270">Chargement par le biais de contextes de chargement d’assembly .NET Core</span><span class="sxs-lookup"><span data-stu-id="3686b-270">Loading through .NET Core Assembly Load Contexts</span></span>

<span data-ttu-id="3686b-271">Les [contextes de chargement d’assembly](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALC) en tant qu’API implémentable ont été introduits dans .NET Core 1.0 afin de répondre spécifiquement à la nécessité de charger plusieurs versions du même assembly dans le même runtime.</span><span class="sxs-lookup"><span data-stu-id="3686b-271">[Assembly Load Contexts](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) as an implementable API were introduced in .NET Core 1.0 to specifically address the need to load multiple versions of the same assembly into the same runtime.</span></span>

<span data-ttu-id="3686b-272">Dans .NET Core et .NET 5, ils offrent la solution la plus fiable au problème de chargement des versions conflictuelles d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="3686b-272">Within .NET Core and .NET 5, they offer the most robust solution to the problem of loading conflicting versions of an assembly.</span></span> <span data-ttu-id="3686b-273">Toutefois, les ALC personnalisés ne sont pas disponibles dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3686b-273">However, custom ALCs are not available in .NET Framework.</span></span> <span data-ttu-id="3686b-274">Cela signifie que cette solution fonctionne uniquement dans PowerShell 6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="3686b-274">This means that this solution only works in PowerShell 6 and above.</span></span>

<span data-ttu-id="3686b-275">Actuellement, le meilleur exemple d’utilisation d’un ALC pour l’isolation des dépendances dans PowerShell se trouve dans PowerShell Editor Services, le serveur de langage pour l’extension PowerShell pour Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3686b-275">Currently, the best example of using an ALC for dependency isolation in PowerShell is in PowerShell Editor Services, the language server for the PowerShell extension for Visual Studio Code.</span></span> <span data-ttu-id="3686b-276">Un [ALC est utilisé](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) pour empêcher que les propres dépendances de PowerShell Editor Services entrent en conflit avec celles des modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-276">An [ALC is used](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) to prevent PowerShell Editor Services' own dependencies from clashing with those in PowerShell modules.</span></span>

<span data-ttu-id="3686b-277">L’implémentation de l’isolation des dépendances de module avec un ALC est conceptuellement difficile, mais nous allons examiner un exemple minimal.</span><span class="sxs-lookup"><span data-stu-id="3686b-277">Implementing module dependency isolation with an ALC is conceptually difficult, but we will work through a minimal example.</span></span> <span data-ttu-id="3686b-278">Imaginez que nous avons un module simple destiné uniquement à fonctionner dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="3686b-278">Imagine we have a simple module that is only intended to work in PowerShell 7.</span></span>
<span data-ttu-id="3686b-279">Le code source est organisé comme suit :</span><span class="sxs-lookup"><span data-stu-id="3686b-279">The source code is organized as follows:</span></span>

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

<span data-ttu-id="3686b-280">L’implémentation de l’applet de commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-280">The cmdlet implementation looks like this:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="3686b-281">Le manifeste (très simplifié) ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-281">The (heavily simplified) manifest, looks like this:</span></span>

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

<span data-ttu-id="3686b-282">Et le `csproj` ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-282">And the `csproj` looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="3686b-283">Lorsque nous générons ce module, la sortie générée présente la disposition suivante :</span><span class="sxs-lookup"><span data-stu-id="3686b-283">When we build this module, the generated output has the following layout:</span></span>

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

<span data-ttu-id="3686b-284">Dans cet exemple, notre problème se trouve dans l’assembly `Shared.Dependency.dll`, qui est notre dépendance en conflit imaginaire.</span><span class="sxs-lookup"><span data-stu-id="3686b-284">In this example, our problem is in the `Shared.Dependency.dll` assembly, which is our imaginary conflicting dependency.</span></span> <span data-ttu-id="3686b-285">Il s’agit de la dépendance que nous devons placer derrière un ALC afin de pouvoir utiliser la version propre au module.</span><span class="sxs-lookup"><span data-stu-id="3686b-285">This is the dependency that we need to put behind an ALC so that we can use the module-specific version.</span></span>

<span data-ttu-id="3686b-286">Nous devons remanier le module afin que :</span><span class="sxs-lookup"><span data-stu-id="3686b-286">We need to re-engineer the module so that:</span></span>

- <span data-ttu-id="3686b-287">Les dépendances de module soient uniquement chargées dans notre ALC personnalisé, et non dans l’ALC de PowerShell, afin qu’il ne puisse y avoir aucun conflit.</span><span class="sxs-lookup"><span data-stu-id="3686b-287">Module dependencies are only loaded into our custom ALC, and not into PowerShell's ALC, so there can be no conflict.</span></span> <span data-ttu-id="3686b-288">De plus, à mesure que nous ajoutons des dépendances à notre projet, nous ne souhaitons pas ajouter continuellement du code pour que le chargement continue à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="3686b-288">Moreover, as we add more dependencies to our project, we don't want to continuously add more code to keep loading working.</span></span> <span data-ttu-id="3686b-289">Au lieu de cela, nous souhaitons avoir une logique de résolution de dépendance générique et réutilisable.</span><span class="sxs-lookup"><span data-stu-id="3686b-289">Instead, we want reusable, generic dependency resolution logic.</span></span>
- <span data-ttu-id="3686b-290">Le chargement du module fonctionne toujours normalement dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-290">Loading the module still works as normal in PowerShell.</span></span> <span data-ttu-id="3686b-291">Les applets de commande et autres types requis par le système de module PowerShell sont définis dans le propre ALC de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-291">Cmdlets and other types that the PowerShell module system needs are defined within PowerShell's own ALC.</span></span>

<span data-ttu-id="3686b-292">Pour répondre à ces deux exigences, nous devons diviser notre module en deux assemblys :</span><span class="sxs-lookup"><span data-stu-id="3686b-292">To mediate these two requirements, we must break up our module into two assemblies:</span></span>

- <span data-ttu-id="3686b-293">Un assembly d’applet de commande, `AlcModule.Cmdlets.dll`, qui contient les définitions de tous les types dont le système de module de PowerShell a besoin pour charger correctement notre module.</span><span class="sxs-lookup"><span data-stu-id="3686b-293">A cmdlets assembly, `AlcModule.Cmdlets.dll`, that contains definitions of all the types that PowerShell's module system needs to load our module correctly.</span></span> <span data-ttu-id="3686b-294">À savoir, toutes les implémentations de la classe de base `Cmdlet` et la classe qui implémente `IModuleAssemblyInitializer`, qui configure le gestionnaire d’événements pour `AssemblyLoadContext.Default.Resolving` afin de charger correctement `AlcModule.Engine.dll` par le biais de notre ALC personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3686b-294">Namely, any implementations of the `Cmdlet` base class and the class that implements `IModuleAssemblyInitializer`, which sets up the event handler for `AssemblyLoadContext.Default.Resolving` to properly load `AlcModule.Engine.dll` through our custom ALC.</span></span> <span data-ttu-id="3686b-295">Comme PowerShell 7 masque délibérément les types définis dans les assemblys chargés dans d’autres ALC, tous les types qui sont censés être exposés publiquement à PowerShell doivent également être définis ici.</span><span class="sxs-lookup"><span data-stu-id="3686b-295">Since PowerShell 7 deliberately hides types defined in assemblies loaded in other ALCs, any types that are meant to be publicly exposed to PowerShell must also be defined here.</span></span> <span data-ttu-id="3686b-296">Pour finir, notre définition d’ALC personnalisée doit être définie dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="3686b-296">Finally, our custom ALC definition needs to be defined in this assembly.</span></span> <span data-ttu-id="3686b-297">À part cela, le moins de code possible doit résider dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="3686b-297">Beyond that, as little code as possible should live in this assembly.</span></span>
- <span data-ttu-id="3686b-298">Un assembly de moteur, `AlcModule.Engine.dll`, qui gère l’implémentation réelle du module.</span><span class="sxs-lookup"><span data-stu-id="3686b-298">An engine assembly, `AlcModule.Engine.dll`, that handles the actual implementation of the module.</span></span>
  <span data-ttu-id="3686b-299">Ses types sont disponibles dans l’ALC PowerShell, mais il sera initialement chargé par le biais de notre ALC personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3686b-299">Types from this are available in the PowerShell ALC, but it will initially be loaded through our custom ALC.</span></span> <span data-ttu-id="3686b-300">Ses dépendances sont chargées uniquement dans l’ALC personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3686b-300">Its dependencies are only loaded into the custom ALC.</span></span> <span data-ttu-id="3686b-301">Il assume en fait le rôle de _pont_ entre les deux ALC.</span><span class="sxs-lookup"><span data-stu-id="3686b-301">Effectively, this becomes a _bridge_ between the two ALCs.</span></span>

<span data-ttu-id="3686b-302">Avec ce concept de pont, notre nouvelle disposition d’assembly ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-302">Using this bridge concept, our new assembly situation looks like this:</span></span>

![Diagramme représentant AlcModule.Engine.dll assumant le rôle de pont entre les deux ALC](./media/resolving-dependency-conflicts/alc-diagram.jpg)

<span data-ttu-id="3686b-304">Pour nous assurer que la logique de sondage de dépendance de l’ALC par défaut ne résout pas les dépendances pour un chargement dans l’ALC personnalisé, nous devons séparer ces deux parties du module dans des répertoires différents.</span><span class="sxs-lookup"><span data-stu-id="3686b-304">To make sure the default ALC's dependency probing logic does not resolve the dependencies to be loaded into the custom ALC, we need to separate these two parts of the module in different directories.</span></span> <span data-ttu-id="3686b-305">La nouvelle disposition de module présente la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="3686b-305">The new module layout has the following structure:</span></span>

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

<span data-ttu-id="3686b-306">Pour voir comment l’implémentation change, nous allons commencer par l’implémentation de `AlcModule.Engine.dll` :</span><span class="sxs-lookup"><span data-stu-id="3686b-306">To see how the implementation changes, we'll start with the implementation of `AlcModule.Engine.dll`:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

<span data-ttu-id="3686b-307">Il s’agit d’un conteneur simple pour la dépendance, `Shared.Dependency.dll`, mais vous devez le considérer comme l’API .NET pour votre fonctionnalité que les applets de commande dans l’autre assembly encapsulent pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-307">This is a simple container for the dependency, `Shared.Dependency.dll`, but you should think of it as the .NET API for your functionality that the cmdlets in the other assembly wrap for PowerShell.</span></span>

<span data-ttu-id="3686b-308">L’applet de commande dans `AlcModule.Cmdlets.dll` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="3686b-308">The cmdlet in `AlcModule.Cmdlets.dll` looks like this:</span></span>

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="3686b-309">À ce stade, si nous chargeons **AlcModule** et exécutons `Test-AlcModule`, nous obtenons une `FileNotFoundException` lorsque l’ALC par défaut tente de charger `Alc.Engine.dll` pour exécuter `EndProcessing()`.</span><span class="sxs-lookup"><span data-stu-id="3686b-309">At this point, if we were to load **AlcModule** and run `Test-AlcModule`, we get a `FileNotFoundException` when the default ALC tries to load `Alc.Engine.dll` to run `EndProcessing()`.</span></span> <span data-ttu-id="3686b-310">C’est bien, car cela signifie que l’ALC par défaut ne peut pas trouver les dépendances que nous souhaitons masquer.</span><span class="sxs-lookup"><span data-stu-id="3686b-310">This is good, since it means the default ALC can't find the dependencies we want to hide.</span></span>

<span data-ttu-id="3686b-311">À présent, nous devons ajouter du code à `AlcModule.Cmdlets.dll` afin qu’elle sache comment résoudre `AlcModule.Engine.dll`.</span><span class="sxs-lookup"><span data-stu-id="3686b-311">Now we need to add code to `AlcModule.Cmdlets.dll` so that it knows how to resolve `AlcModule.Engine.dll`.</span></span> <span data-ttu-id="3686b-312">Tout d’abord, nous devons définir notre ALC personnalisé qui résoudra les assemblys à partir du répertoire `Dependencies` de notre module :</span><span class="sxs-lookup"><span data-stu-id="3686b-312">First we must define our custom ALC that will resolve assemblies from our module's `Dependencies` directory:</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _dependencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                _dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

<span data-ttu-id="3686b-313">Nous devons ensuite associer notre ALC personnalisé à l’événement `Resolving` de l’ALC par défaut, qui est la version d’ALC de l’événement `AssemblyResolve` sur les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="3686b-313">Then we need to hook up our custom ALC to the default ALC's `Resolving` event, which is the ALC version of the `AssemblyResolve` event on Application Domains.</span></span> <span data-ttu-id="3686b-314">Cet événement est déclenché pour rechercher `AlcModule.Engine.dll` lorsque `EndProcessing()` est appelée.</span><span class="sxs-lookup"><span data-stu-id="3686b-314">This event is fired to find `AlcModule.Engine.dll` when `EndProcessing()` is called.</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

<span data-ttu-id="3686b-315">Avec la nouvelle implémentation, examinez la séquence d’appels qui se produit lorsque le module est chargé et que `Test-AlcModule` est exécutée :</span><span class="sxs-lookup"><span data-stu-id="3686b-315">With the new implementation, take a look at the sequence of calls that occurs when the module is loaded and `Test-AlcModule` is run:</span></span>

![Diagramme de séquence des appels avec utilisation de l’ALC personnalisé pour charger les dépendances](./media/resolving-dependency-conflicts/alc-sequence.png)

<span data-ttu-id="3686b-317">Voici quelques points intéressants :</span><span class="sxs-lookup"><span data-stu-id="3686b-317">Some points of interest are:</span></span>

- <span data-ttu-id="3686b-318">L’`IModuleAssemblyInitializer` est exécuté en premier lorsque le module est chargé et définit l’événement `Resolving`.</span><span class="sxs-lookup"><span data-stu-id="3686b-318">The `IModuleAssemblyInitializer` is run first when the module loads and sets the `Resolving` event.</span></span>
- <span data-ttu-id="3686b-319">Nous ne chargeons les dépendances que lorsque `Test-AlcModule` est exécuté et que sa méthode `EndProcessing()` est appelée.</span><span class="sxs-lookup"><span data-stu-id="3686b-319">We don't load the dependencies until `Test-AlcModule` is run and its `EndProcessing()` method is called.</span></span>
- <span data-ttu-id="3686b-320">Lorsque `EndProcessing()` est appelée, l’ALC par défaut ne parvient pas à trouver `AlcModule.Engine.dll` et il déclenche l’événement `Resolving`.</span><span class="sxs-lookup"><span data-stu-id="3686b-320">When `EndProcessing()` is called, the default ALC fails to find `AlcModule.Engine.dll` and fires the `Resolving` event.</span></span>
- <span data-ttu-id="3686b-321">Notre gestionnaire d’événements raccorde l’ALC personnalisé à l’ALC par défaut, et charge uniquement `AlcModule.Engine.dll`.</span><span class="sxs-lookup"><span data-stu-id="3686b-321">Our event handler hooks up the custom ALC to the default ALC and loads `AlcModule.Engine.dll` only.</span></span>
- <span data-ttu-id="3686b-322">Lorsque `AlcEngine.Use()` est appelée dans `AlcModule.Engine.dll`, l’ALC personnalisé intervient afin de résoudre `Shared.Dependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="3686b-322">When `AlcEngine.Use()` is called within `AlcModule.Engine.dll`, the custom ALC again kicks in to resolve `Shared.Dependency.dll`.</span></span> <span data-ttu-id="3686b-323">Plus précisément, il charge toujours _notre_ `Shared.Dependency.dll`, car il n’entre jamais en conflit avec quoi que ce soit dans l’ALC par défaut et ne recherche que dans notre répertoire `Dependencies`.</span><span class="sxs-lookup"><span data-stu-id="3686b-323">Specifically, it always loads _our_ `Shared.Dependency.dll` since it never conflicts with anything in the default ALC and only looks in our `Dependencies` directory.</span></span>

<span data-ttu-id="3686b-324">En assemblant l’implémentation, la nouvelle disposition du code source ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-324">Assembling the implementation, our new source code layout looks like this:</span></span>

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

<span data-ttu-id="3686b-325">AlcModule.Cmdlets.csproj ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-325">AlcModule.Cmdlets.csproj looks like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="3686b-326">AlcModule.Engine.csproj ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3686b-326">AlcModule.Engine.csproj looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="3686b-327">Ainsi, lorsque nous créons le module, notre stratégie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="3686b-327">So, when we build the module, our strategy is:</span></span>

- <span data-ttu-id="3686b-328">Générer `AlcModule.Engine`</span><span class="sxs-lookup"><span data-stu-id="3686b-328">Build `AlcModule.Engine`</span></span>
- <span data-ttu-id="3686b-329">Générer `AlcModule.Cmdlets`</span><span class="sxs-lookup"><span data-stu-id="3686b-329">Build `AlcModule.Cmdlets`</span></span>
- <span data-ttu-id="3686b-330">Copier tout le contenu de `AlcModule.Engine` dans le répertoire `Dependencies` et nous souvenir de ce que nous avons copié</span><span class="sxs-lookup"><span data-stu-id="3686b-330">Copy everything from `AlcModule.Engine` into the `Dependencies` directory, and remember what we copied</span></span>
- <span data-ttu-id="3686b-331">Copier tout le contenu de `AlcModule.Cmdlets` qui n’était pas dans `AlcModule.Engine` dans le répertoire du module de base</span><span class="sxs-lookup"><span data-stu-id="3686b-331">Copy everything from `AlcModule.Cmdlets` that wasn't in `AlcModule.Engine` into the base module directory</span></span>

<span data-ttu-id="3686b-332">La disposition du module étant ici si cruciale pour la séparation des dépendances, voici un script de génération à utiliser à partir de la racine source :</span><span class="sxs-lookup"><span data-stu-id="3686b-332">Since the module layout here is so crucial to dependency separation, here's a build script to use from the source root:</span></span>

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

<span data-ttu-id="3686b-333">Nous disposons finalement d’une approche générale d’utilisation d’un contexte de chargement d’assembly pour isoler les dépendances de notre module qui reste robuste avec le temps, à mesure que d’autres dépendances sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="3686b-333">Finally, we have a general way to use an Assembly Load Context to isolate our module's dependencies that remains robust over time as more dependencies are added.</span></span>

<span data-ttu-id="3686b-334">Pour obtenir un exemple plus détaillé, accédez à ce [dépôt GitHub](https://github.com/rjmholt/ModuleDependencyIsolationExample).</span><span class="sxs-lookup"><span data-stu-id="3686b-334">For a more detailed example, go to this [GitHub repository](https://github.com/rjmholt/ModuleDependencyIsolationExample).</span></span> <span data-ttu-id="3686b-335">Cet exemple montre comment migrer un module afin qu’il utilise un ALC, tout en veillant à ce qu’il reste opérationnel dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3686b-335">This example demonstrates how to migrate a module to use an ALC, while keeping that module working in .NET Framework.</span></span> <span data-ttu-id="3686b-336">Il montre également comment utiliser .NET Standard et PowerShell standard pour simplifier l’implémentation de base.</span><span class="sxs-lookup"><span data-stu-id="3686b-336">It also show how to use .NET Standard and PowerShell Standard to simplify the core implementation.</span></span>

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a><span data-ttu-id="3686b-337">Gestionnaire de résolution d’assembly pour le chargement côte à côte avec `Assembly.LoadFile()`</span><span class="sxs-lookup"><span data-stu-id="3686b-337">Assembly resolve handler for side-by-side loading with `Assembly.LoadFile()`</span></span>

<span data-ttu-id="3686b-338">Une autre méthode, peut-être plus simple, pour accomplir le chargement d’assembly côte à côte consiste à raccorder un événement `AssemblyResolve` à `Assembly.LoadFile()`.</span><span class="sxs-lookup"><span data-stu-id="3686b-338">Another, possibly simpler, way to achieve side-by-side assembly loading is to hook up an `AssemblyResolve` event to `Assembly.LoadFile()`.</span></span> <span data-ttu-id="3686b-339">L’utilisation de `Assembly.LoadFile()` présente l’avantage d’être la solution la plus simple à implémenter, et de fonctionner avec .NET Core et le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3686b-339">Using `Assembly.LoadFile()` has the advantage of being the simplest solution to implement and works with both .NET Core and .NET Framework.</span></span>

<span data-ttu-id="3686b-340">Pour illustrer cela, jetons un coup d’œil à un exemple d’implémentation qui combine des idées de notre exemple de redirection de liaison dynamique et l’exemple de contexte de chargement d’assembly ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="3686b-340">To show this, let's take a look at a quick example of an implementation that combines ideas from our dynamic binding redirect example, and the Assembly Load Context example above.</span></span>

<span data-ttu-id="3686b-341">Ce module, que nous appellerons **LoadFileModule**, a une commande triviale `Test-LoadFile [-Path] <path>`.</span><span class="sxs-lookup"><span data-stu-id="3686b-341">We'll call this module **LoadFileModule**, which has a trivial command `Test-LoadFile [-Path] <path>`.</span></span> <span data-ttu-id="3686b-342">Il prend une dépendance envers l’assembly `CsvHelper` (version 15.0.5).</span><span class="sxs-lookup"><span data-stu-id="3686b-342">This module takes a dependency on the `CsvHelper` assembly (version 15.0.5).</span></span>

<span data-ttu-id="3686b-343">Comme avec le module ALC, nous devons tout d’abord fractionner le module en deux parties.</span><span class="sxs-lookup"><span data-stu-id="3686b-343">As with the ALC module, we must first split up the module into two pieces.</span></span>

<span data-ttu-id="3686b-344">La première partie effectue l’implémentation réelle, `LoadFileModule.Engine` :</span><span class="sxs-lookup"><span data-stu-id="3686b-344">The first part does the actual implementation, `LoadFileModule.Engine`:</span></span>

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

<span data-ttu-id="3686b-345">La deuxième partie est ce que PowerShell charge directement, `LoadFileModule.Cmdlets`.</span><span class="sxs-lookup"><span data-stu-id="3686b-345">The second part is what PowerShell loads directly, `LoadFileModule.Cmdlets`.</span></span> <span data-ttu-id="3686b-346">Nous adoptons une stratégie similaire à celle du module ALC, où nous isolons les dépendances dans un répertoire distinct,</span><span class="sxs-lookup"><span data-stu-id="3686b-346">We use a strategy similar to the ALC module, where we isolate dependencies in a separate directory.</span></span> <span data-ttu-id="3686b-347">mais cette fois-ci nous chargeons tous les assemblys avec un événement de résolution plutôt que simplement `LoadFileModule.Engine.dll`.</span><span class="sxs-lookup"><span data-stu-id="3686b-347">But this time, we load all assemblies in with a resolve event rather than just `LoadFileModule.Engine.dll`.</span></span>

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

<span data-ttu-id="3686b-348">Pour finir, la disposition du module est également similaire au module ALC :</span><span class="sxs-lookup"><span data-stu-id="3686b-348">Finally, the layout of the module is also similar to the ALC module:</span></span>

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

<span data-ttu-id="3686b-349">Une fois cette structure en place, **LoadFileModule** prend désormais en charge le chargement aux côtés d’autres modules avec une dépendance envers **CsvHelper**.</span><span class="sxs-lookup"><span data-stu-id="3686b-349">With this structure in place, **LoadFileModule** now supports being loaded alongside other modules with a dependency on **CsvHelper**.</span></span>

<span data-ttu-id="3686b-350">Étant donné que notre gestionnaire s’applique à **tous** les événements `AssemblyResolve` du domaine d’application, nous devons effectuer ici des choix de conception spécifiques :</span><span class="sxs-lookup"><span data-stu-id="3686b-350">Because our handler applies to **all** `AssemblyResolve` events across the Application Domain, we need to make some specific design choices here:</span></span>

- <span data-ttu-id="3686b-351">Pour réduire la fenêtre pendant laquelle notre événement peut interférer avec un autre chargement, nous ne commençons à gérer le chargement des dépendances générales qu’après le chargement de `LoadFileModule.Engine.dll`.</span><span class="sxs-lookup"><span data-stu-id="3686b-351">To narrow the window in which our event may interfere with other loading, we only start handling general dependency loading after `LoadFileModule.Engine.dll` has been loaded.</span></span>
- <span data-ttu-id="3686b-352">Nous envoyons `LoadFileModule.Engine.dll` dans le répertoire Dependencies, afin qu’il soit chargé par un appel à `LoadFile()` plutôt que par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-352">We push `LoadFileModule.Engine.dll` out into the Dependencies directory, so that it's loaded by a `LoadFile()` call rather than by PowerShell.</span></span> <span data-ttu-id="3686b-353">Cela signifie que ses propres chargements de dépendances déclenchent toujours un événement `AssemblyResolve`, même si un autre `CsvHelper.dll` (par exemple) est chargé dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-353">This means its own dependency loads always raise an `AssemblyResolve` event, even if another `CsvHelper.dll` (for example) is loaded in PowerShell.</span></span>
  <span data-ttu-id="3686b-354">Cela nous donne l’opportunité de trouver la dépendance correcte.</span><span class="sxs-lookup"><span data-stu-id="3686b-354">This gives us the opportunity to find the correct dependency.</span></span>
- <span data-ttu-id="3686b-355">Comme nous devons uniquement résoudre les dépendances propres à notre module, nous sommes obligés de coder un dictionnaire de noms et de versions de dépendances dans notre gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="3686b-355">Since we must only resolve the specific dependencies for our module, we're forced to code a dictionary of dependency names and versions into our handler.</span></span> <span data-ttu-id="3686b-356">Dans notre cas particulier, il serait possible d’utiliser la propriété `ResolveEventArgs.RequestingAssembly` pour déterminer si `CsvHelper` est demandé par notre module.</span><span class="sxs-lookup"><span data-stu-id="3686b-356">In our particular case, it would be possible to use the `ResolveEventArgs.RequestingAssembly` property to work out whether `CsvHelper` is being requested by our module.</span></span> <span data-ttu-id="3686b-357">Mais cela ne fonctionne pas pour les dépendances de dépendances, par exemple si `CsvHelper` lui-même a déclenché un événement `AssemblyResolve`.</span><span class="sxs-lookup"><span data-stu-id="3686b-357">But this doesn't work for dependencies of dependencies; for example, if `CsvHelper` itself raised an `AssemblyResolve` event.</span></span> <span data-ttu-id="3686b-358">Il existe d’autres méthodes plus compliquées pour effectuer cette opération, telles que la comparaison des assemblys demandés aux métadonnées des assemblys dans le répertoire `Dependencies`.</span><span class="sxs-lookup"><span data-stu-id="3686b-358">There are other, harder ways to do this, such as comparing requested assemblies to the metadata of assemblies in the `Dependencies` directory.</span></span> <span data-ttu-id="3686b-359">Toutefois, dans cet exemple nous avons rendu cette vérification plus explicite afin de mettre en évidence le problème et de simplifier l’exemple.</span><span class="sxs-lookup"><span data-stu-id="3686b-359">But, in this example, we've made this checking more explicit to both highlight the issue and simplify the example.</span></span>

<span data-ttu-id="3686b-360">Il s’agit de la principale différence entre la stratégie `LoadFile()` et la stratégie ALC : l’événement `AssemblyResolve` doit traiter toutes les charges dans le domaine d’application, et il est par conséquent beaucoup plus difficile d’éviter que notre résolution des dépendances ne s’entremêle avec d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="3686b-360">This is the key difference between the `LoadFile()` strategy and the ALC strategy: the `AssemblyResolve` event must service all loads in the Application Domain, making it much harder to keep our dependency resolution from being tangled with other modules.</span></span> <span data-ttu-id="3686b-361">Toutefois, l’absence d’ALC dans le .NET Framework rend cette option intéressante.</span><span class="sxs-lookup"><span data-stu-id="3686b-361">However, the lack of ALCs in .NET Framework makes this option worth understanding.</span></span>

### <a name="custom-application-domains"></a><span data-ttu-id="3686b-362">Domaines d’application personnalisés</span><span class="sxs-lookup"><span data-stu-id="3686b-362">Custom Application Domains</span></span>

<span data-ttu-id="3686b-363">La dernière option (et la plus extrême) pour l’isolation d’assembly consiste à utiliser des domaines d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="3686b-363">The final and most extreme option for assembly isolation is to use custom Application Domains.</span></span>
<span data-ttu-id="3686b-364">Les domaines d’application (utilisés au pluriel) sont uniquement disponibles dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3686b-364">Application Domains (used in the plural) are only available in .NET Framework.</span></span> <span data-ttu-id="3686b-365">Ils servent à fournir une isolation in-process entre les parties d’une application .NET.</span><span class="sxs-lookup"><span data-stu-id="3686b-365">They are used to provide in-process isolation between parts of a .NET application.</span></span> <span data-ttu-id="3686b-366">L’une des utilisations consiste à isoler les charges d’assembly les unes des autres au sein du même processus.</span><span class="sxs-lookup"><span data-stu-id="3686b-366">One of the uses is to isolate assembly loads from each other within the same process.</span></span>

<span data-ttu-id="3686b-367">Toutefois, les domaines d’application sont des limites de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="3686b-367">However, Application Domains are serialization boundaries.</span></span> <span data-ttu-id="3686b-368">Les objets d’un domaine d’application ne peuvent pas être référencés et utilisés directement par les objets d’un autre domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="3686b-368">Objects in one Application Domain can't be referenced and used directly by objects in another Application Domain.</span></span> <span data-ttu-id="3686b-369">Vous pouvez contourner ce problème en implémentant `MarshalByRefObject`.</span><span class="sxs-lookup"><span data-stu-id="3686b-369">You can work around this by implementing `MarshalByRefObject`.</span></span> <span data-ttu-id="3686b-370">Toutefois, lorsque vous ne contrôlez pas les types, comme c’est souvent le cas avec les dépendances, il n’est pas possible de forcer une implémentation ici.</span><span class="sxs-lookup"><span data-stu-id="3686b-370">But when you don't control the types, as is often the case with dependencies, it's not possible to force an implementation here.</span></span> <span data-ttu-id="3686b-371">La seule solution consiste à apporter des modifications architecturales importantes.</span><span class="sxs-lookup"><span data-stu-id="3686b-371">The only solution is to make large architectural changes.</span></span> <span data-ttu-id="3686b-372">La limite de sérialisation a également de sérieuses implications en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="3686b-372">The serialization boundary also has serious performance implications.</span></span>

<span data-ttu-id="3686b-373">Étant donné que les domaines d’application présentent cette limitation sérieuse, sont compliqués à implémenter et ne fonctionnent que dans le .NET Framework, nous ne fournirons aucun exemple de la façon dont vous pouvez les utiliser ici.</span><span class="sxs-lookup"><span data-stu-id="3686b-373">Because Application Domains have this serious limitation, are complicated to implement, and only work in .NET Framework, we won't give an example of how you might use them here.</span></span> <span data-ttu-id="3686b-374">Bien qu’ils méritent d’être mentionnés en tant que possibilité, leur utilisation n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="3686b-374">While they're worth mentioning as a possibility, they're not recommended.</span></span>

<span data-ttu-id="3686b-375">Si vous souhaitez essayer d’utiliser un domaine d’application personnalisé, les liens suivants peuvent vous aider :</span><span class="sxs-lookup"><span data-stu-id="3686b-375">If you're interested in trying to use a custom Application Domain, the following links might help:</span></span>

- [<span data-ttu-id="3686b-376">Documentation conceptuelle sur les domaines d’application</span><span class="sxs-lookup"><span data-stu-id="3686b-376">Conceptual documentation on Application Domains</span></span>](/dotnet/framework/app-domains/application-domains)
- [<span data-ttu-id="3686b-377">Exemples d’utilisation de domaines d’application</span><span class="sxs-lookup"><span data-stu-id="3686b-377">Examples for using Application Domains</span></span>](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a><span data-ttu-id="3686b-378">Solutions aux conflits de dépendances qui ne fonctionnent pas pour PowerShell</span><span class="sxs-lookup"><span data-stu-id="3686b-378">Solutions for dependency conflicts that don't work for PowerShell</span></span>

<span data-ttu-id="3686b-379">Pour finir, nous allons aborder certaines possibilités qui peuvent sembler prometteuses lors de l’examen des conflits de dépendances .NET dans .NET, mais qui ne fonctionnent généralement pas pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-379">Finally, we'll address some possibilities that come up when researching .NET dependency conflicts in .NET that can look promising, but generally won't work for PowerShell.</span></span>

<span data-ttu-id="3686b-380">Ces solutions ont comme thème commun le fait qu’il s’agit de modifications apportées aux configurations de déploiement pour un environnement dans lequel vous contrôlez l’application et éventuellement toute la machine.</span><span class="sxs-lookup"><span data-stu-id="3686b-380">These solutions have the common theme that they are changes to deployment configurations for an environment where you control the application and possibly the entire machine.</span></span> <span data-ttu-id="3686b-381">Elles sont orientées vers des scénarios tels que des serveurs web et d’autres applications déployées dans des environnements de serveur, où l’environnement est destiné à héberger l’application et peut être configuré par l’utilisateur du déploiement.</span><span class="sxs-lookup"><span data-stu-id="3686b-381">These solutions are oriented toward scenarios like web servers and other applications deployed to server environments, where the environment is intended to host the application and is free to be configured by the deploying user.</span></span> <span data-ttu-id="3686b-382">Elles ont également tendance à être très orientées vers le .NET Framework, ce qui signifie qu’elles ne fonctionnent pas avec PowerShell 6 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3686b-382">They also tend to be very much .NET Framework oriented, meaning they do not work with PowerShell 6 or above.</span></span>

<span data-ttu-id="3686b-383">Si vous savez que votre module est utilisé uniquement dans des environnements Windows PowerShell 5.1 que vous contrôlez entièrement, certaines d’entre elles peuvent être des options envisageables.</span><span class="sxs-lookup"><span data-stu-id="3686b-383">If you know that your module is only used in Windows PowerShell 5.1 environments that you have total control over, some of these may be options.</span></span> <span data-ttu-id="3686b-384">Toutefois, en règle générale, **les modules ne doivent pas modifier l’état global de la machine comme ceci**.</span><span class="sxs-lookup"><span data-stu-id="3686b-384">In general however, **modules should not modify global machine state like this**.</span></span> <span data-ttu-id="3686b-385">Cela peut rompre des configurations qui provoquent des problèmes dans `powershell.exe`, d’autres modules ou d’autres applications dépendantes qui entraînent l’échec inattendu de votre module.</span><span class="sxs-lookup"><span data-stu-id="3686b-385">It can break configurations that cause problems in `powershell.exe`, other modules, or other dependent applications that cause your module to fail in unexpected ways.</span></span>

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a><span data-ttu-id="3686b-386">Redirection de liaison statique avec app.config pour forcer l’utilisation de la même version de dépendance</span><span class="sxs-lookup"><span data-stu-id="3686b-386">Static binding redirect with app.config to force using the same dependency version</span></span>

<span data-ttu-id="3686b-387">Les applications .NET Framework peuvent tirer parti d’un fichier `app.config` pour configurer de façon déclarative certains comportements de l’application.</span><span class="sxs-lookup"><span data-stu-id="3686b-387">.NET Framework applications can take advantage of an `app.config` file to configure some of the application's behaviors declaratively.</span></span> <span data-ttu-id="3686b-388">Il est possible d’écrire une entrée `app.config` qui configure la liaison d’assembly de façon à rediriger le chargement d’assembly vers une version particulière.</span><span class="sxs-lookup"><span data-stu-id="3686b-388">It's possible to write an `app.config` entry that configures assembly binding to redirect assembly loading to a particular version.</span></span>

<span data-ttu-id="3686b-389">Avec PowerShell, cela pose deux problèmes :</span><span class="sxs-lookup"><span data-stu-id="3686b-389">Two issues with this for PowerShell are:</span></span>

- <span data-ttu-id="3686b-390">.NET Core ne prend pas en charge `app.config`. Par conséquent, cette solution s’applique uniquement à `powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3686b-390">.NET Core does not support `app.config`, so this solution only applies to `powershell.exe`.</span></span>
- <span data-ttu-id="3686b-391">`powershell.exe` est une application partagée qui réside dans le répertoire `System32`</span><span class="sxs-lookup"><span data-stu-id="3686b-391">`powershell.exe` is a shared application that lives in the `System32` directory.</span></span> <span data-ttu-id="3686b-392">Il est probable que votre module ne pourra pas modifier son contenu sur de nombreux systèmes.</span><span class="sxs-lookup"><span data-stu-id="3686b-392">It's likely that your module won't be able to modify its contents on many systems.</span></span> <span data-ttu-id="3686b-393">Même s’il le peut, la modification du fichier `app.config` risque d’invalider une configuration existante ou d’affecter le chargement d’autres modules</span><span class="sxs-lookup"><span data-stu-id="3686b-393">Even if it can, modifying the `app.config` could break an existing configuration or affect the loading of other modules.</span></span>

### <a name="setting-codebase-with-appconfig"></a><span data-ttu-id="3686b-394">Définition de `codebase` avec app.config</span><span class="sxs-lookup"><span data-stu-id="3686b-394">Setting `codebase` with app.config</span></span>

<span data-ttu-id="3686b-395">Pour les mêmes raisons, la configuration du paramètre `codebase` dans `app.config` échouera dans les modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3686b-395">For the same reasons, trying to configure the `codebase` setting in `app.config` is not going to work in PowerShell modules.</span></span>

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a><span data-ttu-id="3686b-396">Installation de dépendances dans le Global Assembly Cache (GAC)</span><span class="sxs-lookup"><span data-stu-id="3686b-396">Installing dependencies to the Global Assembly Cache (GAC)</span></span>

<span data-ttu-id="3686b-397">Une autre façon de résoudre les conflits de version de dépendance dans le .NET Framework consiste à installer les dépendances dans le GAC, afin que différentes versions puissent être chargées côte à côte à partir du GAC.</span><span class="sxs-lookup"><span data-stu-id="3686b-397">Another way to resolve dependency version conflicts in .NET Framework is to install dependencies to the GAC, so that different versions can be loaded side-by-side from the GAC.</span></span>

<span data-ttu-id="3686b-398">Là encore, pour les modules PowerShell, les principaux problèmes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="3686b-398">Again, for PowerShell modules, the chief issues here are:</span></span>

- <span data-ttu-id="3686b-399">Puisque le GAC s’applique uniquement au .NET Framework, cela n’est d’aucune aide dans PowerShell 6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="3686b-399">The GAC only applies to .NET Framework, so this does not help in PowerShell 6 and above.</span></span>
- <span data-ttu-id="3686b-400">L’installation d’assemblys dans le GAC est une modification de l’état global de la machine susceptible d’avoir des effets secondaires dans d’autres applications ou modules.</span><span class="sxs-lookup"><span data-stu-id="3686b-400">Installing assemblies to the GAC is a modification of global machine state and may cause side-effects in other applications or to other modules.</span></span> <span data-ttu-id="3686b-401">Elle peut également être difficile à accomplir correctement, même si votre module dispose des privilèges d’accès requis.</span><span class="sxs-lookup"><span data-stu-id="3686b-401">It may also be difficult to do correctly, even when your module has the required access privileges.</span></span> <span data-ttu-id="3686b-402">Toute erreur peut provoquer des problèmes sérieux à l’échelle de la machine dans d’autres applications .NET.</span><span class="sxs-lookup"><span data-stu-id="3686b-402">Getting it wrong could cause serious, machine-wide issues in other .NET applications.</span></span>

## <a name="further-reading"></a><span data-ttu-id="3686b-403">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="3686b-403">Further reading</span></span>

<span data-ttu-id="3686b-404">Il existe de nombreux articles qui traitent des conflits de dépendances de version d’assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="3686b-404">There's plenty more to read on .NET assembly version dependency conflicts.</span></span> <span data-ttu-id="3686b-405">En voici une sélection :</span><span class="sxs-lookup"><span data-stu-id="3686b-405">Here are some nice jumping off points:</span></span>

- [<span data-ttu-id="3686b-406">.NET : Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="3686b-406">.NET: Assemblies in .NET</span></span>](/dotnet/standard/assembly/)
- [<span data-ttu-id="3686b-407">.NET Core : Algorithme de chargement d’assembly managé</span><span class="sxs-lookup"><span data-stu-id="3686b-407">.NET Core: The managed assembly loading algorithm</span></span>](/dotnet/core/dependency-loading/loading-managed)
- [<span data-ttu-id="3686b-408">.NET Core : Comprendre System.Runtime.Loader.AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="3686b-408">.NET Core: Understanding System.Runtime.Loader.AssemblyLoadContext</span></span>](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [<span data-ttu-id="3686b-409">.NET Core : Discussion relative aux solutions de chargement d’assemblys côte à côte</span><span class="sxs-lookup"><span data-stu-id="3686b-409">.NET Core: Discussion about side-by-side assembly loading solutions</span></span>](https://github.com/dotnet/runtime/issues/13471)
- [<span data-ttu-id="3686b-410">.NET Framework : Redirection des versions d’assemblys</span><span class="sxs-lookup"><span data-stu-id="3686b-410">.NET Framework: Redirecting assembly versions</span></span>](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [<span data-ttu-id="3686b-411">.NET Framework : Bonnes pratiques pour le chargement d’assembly</span><span class="sxs-lookup"><span data-stu-id="3686b-411">.NET Framework: Best practices for assembly loading</span></span>](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [<span data-ttu-id="3686b-412">.NET Framework : Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="3686b-412">.NET Framework: How the runtime locates assemblies</span></span>](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [<span data-ttu-id="3686b-413">.NET Framework : Résoudre les chargements d’assemblys</span><span class="sxs-lookup"><span data-stu-id="3686b-413">.NET Framework: Resolve assembly loads</span></span>](/dotnet/standard/assembly/resolve-loads)
- <span data-ttu-id="3686b-414">[StackOverflow : Assembly binding redirect, how and why?](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why) (Redirection de liaison d’assembly, comment et pourquoi ?)</span><span class="sxs-lookup"><span data-stu-id="3686b-414">[StackOverflow: Assembly binding redirect, how and why?](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why)</span></span>
- [<span data-ttu-id="3686b-415">PowerShell : Discussion relative à l’implémentation d’AssemblyLoadContexts</span><span class="sxs-lookup"><span data-stu-id="3686b-415">PowerShell: Discussion about implementing AssemblyLoadContexts</span></span>](https://github.com/PowerShell/PowerShell/issues/11571)
- [<span data-ttu-id="3686b-416">PowerShell : `Assembly.LoadFile()` ne se charge pas dans l’AssemblyLoadContext par défaut</span><span class="sxs-lookup"><span data-stu-id="3686b-416">PowerShell: `Assembly.LoadFile()` doesn't load into default AssemblyLoadContext</span></span>](https://github.com/PowerShell/PowerShell/issues/12052)
- <span data-ttu-id="3686b-417">[Rick Strahl : When does a .NET assembly dependency get loaded?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded) (Quand une dépendance d’assembly .NET est-elle chargée ?)</span><span class="sxs-lookup"><span data-stu-id="3686b-417">[Rick Strahl: When does a .NET assembly dependency get loaded?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded)</span></span>
- <span data-ttu-id="3686b-418">[Jon Skeet : Summary of versioning in .NET](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/) (Récapitulatif de la gestion de versions dans .NET)</span><span class="sxs-lookup"><span data-stu-id="3686b-418">[Jon Skeet: Summary of versioning in .NET](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)</span></span>
- <span data-ttu-id="3686b-419">[Nate McMaster : Deep dive into .NET Core primitives](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/) (Immersion dans les primitives .NET Core)</span><span class="sxs-lookup"><span data-stu-id="3686b-419">[Nate McMaster: Deep dive into .NET Core primitives](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/)</span></span>
