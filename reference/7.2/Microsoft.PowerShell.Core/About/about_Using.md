---
description: Vous permet d’indiquer les espaces de noms qui sont utilisés dans la session.
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: ba3833f522265ad240d376b07c5add393c4b2721
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "99595909"
---
# <a name="about-using"></a><span data-ttu-id="08189-103">À propos de l’utilisation de</span><span class="sxs-lookup"><span data-stu-id="08189-103">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="08189-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="08189-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="08189-105">Vous permet d’indiquer les espaces de noms qui sont utilisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="08189-105">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="08189-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="08189-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="08189-107">L' `using` instruction vous permet de spécifier les espaces de noms qui sont utilisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="08189-107">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="08189-108">L’ajout d’espaces de noms simplifie l’utilisation des classes et membres .NET et vous permet d’importer des classes à partir de modules de script et d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="08189-108">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="08189-109">Les `using` instructions doivent précéder toutes les autres instructions dans un script ou un module.</span><span class="sxs-lookup"><span data-stu-id="08189-109">The `using` statements must come before any other statements in a script or module.</span></span> <span data-ttu-id="08189-110">Aucune instruction sans commentaire ne peut le précéder, y compris les paramètres.</span><span class="sxs-lookup"><span data-stu-id="08189-110">No uncommented statement can precede it, including parameters.</span></span>

<span data-ttu-id="08189-111">L' `using` instruction ne doit pas contenir de variables.</span><span class="sxs-lookup"><span data-stu-id="08189-111">The `using` statement must not contain any variables.</span></span>

<span data-ttu-id="08189-112">L' `using` instruction ne doit pas être confondue avec le `using:` modificateur de portée pour les variables.</span><span class="sxs-lookup"><span data-stu-id="08189-112">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="08189-113">Pour plus d’informations, consultez [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="08189-113">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="namespace-syntax"></a><span data-ttu-id="08189-114">Syntaxe d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="08189-114">Namespace syntax</span></span>

<span data-ttu-id="08189-115">Pour spécifier des espaces de noms .NET à partir desquels résoudre les types :</span><span class="sxs-lookup"><span data-stu-id="08189-115">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="08189-116">La spécification d’un espace de noms facilite la référence des types par leurs noms courts.</span><span class="sxs-lookup"><span data-stu-id="08189-116">Specifying a namespace makes it easier to reference types by their short names.</span></span>

## <a name="module-syntax"></a><span data-ttu-id="08189-117">Syntaxe de module</span><span class="sxs-lookup"><span data-stu-id="08189-117">Module syntax</span></span>

<span data-ttu-id="08189-118">Pour charger des classes à partir d’un module PowerShell :</span><span class="sxs-lookup"><span data-stu-id="08189-118">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="08189-119">La valeur de `<module-name>` peut être un nom de module, une spécification de module complète ou un chemin d’accès à un fichier de module.</span><span class="sxs-lookup"><span data-stu-id="08189-119">The value of `<module-name>` can be a module name, a full module specification, or a path to a module file.</span></span>

<span data-ttu-id="08189-120">Lorsque `<module-name>` est un chemin d’accès, le chemin d’accès peut être complet ou relatif.</span><span class="sxs-lookup"><span data-stu-id="08189-120">When `<module-name>` is a path, the path can be fully qualified or relative.</span></span> <span data-ttu-id="08189-121">Un chemin d’accès relatif est résolu par rapport au script qui contient l’instruction using.</span><span class="sxs-lookup"><span data-stu-id="08189-121">A relative path is resolved relative to the script that contains the using statement.</span></span>

<span data-ttu-id="08189-122">Quand `<module-name>` est un nom ou une spécification de module, PowerShell recherche le module spécifié dans le **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="08189-122">When `<module-name>` is a name or module specification, PowerShell searches the **PSModulePath** for the specified module.</span></span>

<span data-ttu-id="08189-123">Une spécification de module est une table de hachage qui contient les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="08189-123">A module specification is a hash table that has the following keys.</span></span>

- <span data-ttu-id="08189-124">`ModuleName` - **Obligatoire** Spécifie le nom du module.</span><span class="sxs-lookup"><span data-stu-id="08189-124">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="08189-125">`GUID` - **Facultatif** Spécifie le GUID du module.</span><span class="sxs-lookup"><span data-stu-id="08189-125">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="08189-126">Il est également **nécessaire** de spécifier l’une des trois clés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="08189-126">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="08189-127">Ces clés ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="08189-127">These keys can't be used together.</span></span>
  - <span data-ttu-id="08189-128">`ModuleVersion` -Spécifie une version minimale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="08189-128">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="08189-129">`RequiredVersion` -Spécifie une version exacte et obligatoire du module.</span><span class="sxs-lookup"><span data-stu-id="08189-129">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="08189-130">`MaximumVersion` -Spécifie la version maximale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="08189-130">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

<span data-ttu-id="08189-131">L' `using module` instruction importe des classes à partir du module racine ( `ModuleToProcess` ) d’un module de script ou d’un module binaire.</span><span class="sxs-lookup"><span data-stu-id="08189-131">The `using module` statement imports classes from the root module (`ModuleToProcess`) of a script module or binary module.</span></span> <span data-ttu-id="08189-132">Elle n’importe pas régulièrement les classes définies dans les modules imbriqués ou les classes définies dans les scripts qui sont insérés dans le module.</span><span class="sxs-lookup"><span data-stu-id="08189-132">It does not consistently import classes defined in nested modules or classes defined in scripts that are dot-sourced into the module.</span></span> <span data-ttu-id="08189-133">Les classes que vous souhaitez mettre à la disposition des utilisateurs en dehors du module doivent être définies dans le module racine.</span><span class="sxs-lookup"><span data-stu-id="08189-133">Classes that you want to be available to users outside of the module should be defined in the root module.</span></span>

<span data-ttu-id="08189-134">Lors du développement d’un module de script, il est courant d’apporter des modifications au code, puis de charger la nouvelle version du module en utilisant `Import-Module` avec le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="08189-134">During development of a script module, it is common to make changes to the code then load the new version of the module using `Import-Module` with the **Force** parameter.</span></span> <span data-ttu-id="08189-135">Cela ne fonctionne que pour les modifications apportées aux fonctions du module racine uniquement.</span><span class="sxs-lookup"><span data-stu-id="08189-135">This works for changes to functions in the root module only.</span></span> <span data-ttu-id="08189-136">`Import-Module` ne recharge pas les modules imbriqués.</span><span class="sxs-lookup"><span data-stu-id="08189-136">`Import-Module` does not reload any nested modules.</span></span> <span data-ttu-id="08189-137">En outre, il n’existe aucun moyen de charger les classes mises à jour.</span><span class="sxs-lookup"><span data-stu-id="08189-137">Also, there is no way to load any updated classes.</span></span>

<span data-ttu-id="08189-138">Pour vous assurer que vous exécutez la version la plus récente, vous devez décharger le module à l’aide de l’applet de commande `Remove-Module` .</span><span class="sxs-lookup"><span data-stu-id="08189-138">To ensure that you are running the latest version, you must unload the module using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="08189-139">`Remove-Module` supprime le module racine, tous les modules imbriqués et toutes les classes définies dans les modules.</span><span class="sxs-lookup"><span data-stu-id="08189-139">`Remove-Module` removes the root module, all nested modules, and any classes defined in the modules.</span></span> <span data-ttu-id="08189-140">Vous pouvez ensuite recharger le module et les classes à l’aide `Import-Module` de et de l' `using module` instruction.</span><span class="sxs-lookup"><span data-stu-id="08189-140">Then you can reload the module and the classes using `Import-Module` and the `using module` statement.</span></span>

## <a name="assembly-syntax"></a><span data-ttu-id="08189-141">Syntaxe d’assembly</span><span class="sxs-lookup"><span data-stu-id="08189-141">Assembly syntax</span></span>

<span data-ttu-id="08189-142">Pour précharger des types à partir d’un assembly .NET :</span><span class="sxs-lookup"><span data-stu-id="08189-142">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
```

<span data-ttu-id="08189-143">Le chargement d’un assembly précharge les types .NET de cet assembly dans un script au moment de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="08189-143">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="08189-144">Cela vous permet de créer de nouvelles classes PowerShell qui utilisent des types de l’assembly préchargé.</span><span class="sxs-lookup"><span data-stu-id="08189-144">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="08189-145">Si vous ne créez pas de nouvelles classes PowerShell, utilisez `Add-Type` plutôt l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="08189-145">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="08189-146">Pour plus d’informations, consultez [Add-type](xref:Microsoft.PowerShell.Utility.Add-Type).</span><span class="sxs-lookup"><span data-stu-id="08189-146">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="08189-147">Exemples</span><span class="sxs-lookup"><span data-stu-id="08189-147">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="08189-148">Exemple 1 : ajouter des espaces de noms pour la résolution TypeName</span><span class="sxs-lookup"><span data-stu-id="08189-148">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="08189-149">Le script suivant obtient le hachage de chiffrement pour la chaîne « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="08189-149">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="08189-150">Notez comment `using namespace System.Text` et `using namespace System.IO` simplifient les références à `[UnicodeEncoding]` dans `System.Text` et `[Stream]` et à `[MemoryStream]` dans `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="08189-150">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="08189-151">Exemple 2 : charger des classes à partir d’un module de script</span><span class="sxs-lookup"><span data-stu-id="08189-151">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="08189-152">Dans cet exemple, nous disposons d’un module de script PowerShell nommé **CardGames** qui définit les classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="08189-152">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="08189-153">**CardGames. Deck**</span><span class="sxs-lookup"><span data-stu-id="08189-153">**CardGames.Deck**</span></span>
- <span data-ttu-id="08189-154">**CardGames. carte**</span><span class="sxs-lookup"><span data-stu-id="08189-154">**CardGames.Card**</span></span>

<span data-ttu-id="08189-155">`Import-Module` et l' `#requires` instruction importent uniquement les fonctions de module, les alias et les variables, comme défini par le module.</span><span class="sxs-lookup"><span data-stu-id="08189-155">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="08189-156">Les classes ne sont pas importées.</span><span class="sxs-lookup"><span data-stu-id="08189-156">Classes are not imported.</span></span> <span data-ttu-id="08189-157">La `using module` commande importe le module et charge également les définitions de classe.</span><span class="sxs-lookup"><span data-stu-id="08189-157">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="08189-158">Exemple 3 : charger des classes à partir d’un assembly</span><span class="sxs-lookup"><span data-stu-id="08189-158">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="08189-159">Cet exemple charge un assembly afin que ses classes puissent être utilisées pour créer de nouvelles classes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08189-159">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="08189-160">Le script suivant crée une nouvelle classe PowerShell dérivée de la classe **DirectoryContext** .</span><span class="sxs-lookup"><span data-stu-id="08189-160">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```
