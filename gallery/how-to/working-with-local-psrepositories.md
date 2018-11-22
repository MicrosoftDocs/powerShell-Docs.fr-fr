---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery, powershell, applet de commande, psgallery, psget
title: Utilisation de PSRepositories local
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619196"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="77c20-103">Utilisation des référentiels PowerShellGet locaux</span><span class="sxs-lookup"><span data-stu-id="77c20-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="77c20-104">Les référentiels de prise en charge du module PowerShellGet autre que PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="77c20-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="77c20-105">Ces applets de commande permettent les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="77c20-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="77c20-106">Prend en charge un ensemble de modules PowerShell approuvé et validé préalable pour une utilisation dans votre environnement</span><span class="sxs-lookup"><span data-stu-id="77c20-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="77c20-107">Un pipeline CI/CD qui génère des modules PowerShell ou des scripts de test</span><span class="sxs-lookup"><span data-stu-id="77c20-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="77c20-108">Envoyer des scripts et modules PowerShell aux systèmes qui ne peut pas accéder à internet</span><span class="sxs-lookup"><span data-stu-id="77c20-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="77c20-109">Cet article décrit comment configurer un référentiel PowerShell local.</span><span class="sxs-lookup"><span data-stu-id="77c20-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="77c20-110">Cet article décrit également la [OfflinePowerShellGetDeploy][] module disponible à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="77c20-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="77c20-111">Ce module contient des applets de commande pour installer la dernière version de PowerShellGet dans votre référentiel local.</span><span class="sxs-lookup"><span data-stu-id="77c20-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="77c20-112">Types de référentiel local</span><span class="sxs-lookup"><span data-stu-id="77c20-112">Local repository types</span></span>

<span data-ttu-id="77c20-113">Il existe deux façons de créer un PSRepository local : NuGet serveur ou partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="77c20-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="77c20-114">Chaque type présente des avantages et des inconvénients :</span><span class="sxs-lookup"><span data-stu-id="77c20-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="77c20-115">Serveur NuGet</span><span class="sxs-lookup"><span data-stu-id="77c20-115">NuGet Server</span></span>

| <span data-ttu-id="77c20-116">Avantages</span><span class="sxs-lookup"><span data-stu-id="77c20-116">Advantages</span></span>| <span data-ttu-id="77c20-117">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="77c20-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="77c20-118">Reproduit fidèlement les fonctionnalités de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="77c20-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="77c20-119">Application multiniveau requiert la planification des opérations et support</span><span class="sxs-lookup"><span data-stu-id="77c20-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="77c20-120">NuGet s’intègre à Visual Studio, les autres outils</span><span class="sxs-lookup"><span data-stu-id="77c20-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="77c20-121">Modèle d’authentification et de gestion des comptes NuGet nécessité</span><span class="sxs-lookup"><span data-stu-id="77c20-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="77c20-122">NuGet prend en charge les métadonnées dans `.Nupkg` packages</span><span class="sxs-lookup"><span data-stu-id="77c20-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="77c20-123">Publication nécessite la gestion de la clé d’API et de maintenance</span><span class="sxs-lookup"><span data-stu-id="77c20-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="77c20-124">Fournit la recherche, administration de package, etc.</span><span class="sxs-lookup"><span data-stu-id="77c20-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="77c20-125">Partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="77c20-125">File Share</span></span>

| <span data-ttu-id="77c20-126">Avantages</span><span class="sxs-lookup"><span data-stu-id="77c20-126">Advantages</span></span>| <span data-ttu-id="77c20-127">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="77c20-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="77c20-128">Facile à configurer, sauvegarder et mettre à jour</span><span class="sxs-lookup"><span data-stu-id="77c20-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="77c20-129">Métadonnées utilisées par PowerShellGet n’est pas disponible</span><span class="sxs-lookup"><span data-stu-id="77c20-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="77c20-130">Modèle de sécurité simple - autorisations utilisateur sur le partage</span><span class="sxs-lookup"><span data-stu-id="77c20-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="77c20-131">Aucune interface utilisateur au-delà de partage de fichiers de base</span><span class="sxs-lookup"><span data-stu-id="77c20-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="77c20-132">Aucune contrainte telles que le remplacement des éléments existants</span><span class="sxs-lookup"><span data-stu-id="77c20-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="77c20-133">Une sécurité limitée et aucun enregistrement de qui ce qui met à jour</span><span class="sxs-lookup"><span data-stu-id="77c20-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="77c20-134">PowerShellGet fonctionne avec le type et prend en charge la localisation des versions et l’installation de dépendance.</span><span class="sxs-lookup"><span data-stu-id="77c20-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="77c20-135">Toutefois, certaines fonctionnalités de PowerShell Gallery ne sont pas disponibles pour les serveurs de base de NuGet ou des partages de fichiers.</span><span class="sxs-lookup"><span data-stu-id="77c20-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="77c20-136">Tout est un package - aucune distinction des scripts, modules, les ressources DSC, capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="77c20-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="77c20-137">Serveurs de partage de fichiers ne peut pas voir les métadonnées du package, y compris les balises.</span><span class="sxs-lookup"><span data-stu-id="77c20-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="77c20-138">Création d’un référentiel local</span><span class="sxs-lookup"><span data-stu-id="77c20-138">Creating a local repository</span></span>

<span data-ttu-id="77c20-139">L’article suivant répertorie les étapes pour configurer votre propre serveur NuGet.</span><span class="sxs-lookup"><span data-stu-id="77c20-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="77c20-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="77c20-140">[NuGet.Server][]</span></span>

<span data-ttu-id="77c20-141">Suivez les étapes jusqu’au moment de l’ajout de packages.</span><span class="sxs-lookup"><span data-stu-id="77c20-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="77c20-142">Les étapes pour [publication d’un package](#publishing-to-a-local-repository) sont traités plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="77c20-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="77c20-143">Pour un référentiel sur le partage de fichiers, assurez-vous que vos utilisateurs disposent des autorisations pour accéder au partage de fichier.</span><span class="sxs-lookup"><span data-stu-id="77c20-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="77c20-144">L’inscription d’un référentiel local</span><span class="sxs-lookup"><span data-stu-id="77c20-144">Registering a local repository</span></span>

<span data-ttu-id="77c20-145">Avant de pouvoir utiliser un référentiel, elle doit être inscrite à l’aide de la `Register-PSRepository` commande.</span><span class="sxs-lookup"><span data-stu-id="77c20-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="77c20-146">Dans les exemples ci-dessous, le **InstallationPolicy** a la valeur *approuvé*, sur l’hypothèse que vous faites confiance à votre propre référentiel.</span><span class="sxs-lookup"><span data-stu-id="77c20-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="77c20-147">Prenez note de la différence entre la façon dont les deux commandes gérer **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="77c20-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="77c20-148">Un fichier sur le partage de référentiels, les **SourceLocation** et **ScriptSourceLocation** doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="77c20-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="77c20-149">Pour un référentiel sur le web, ils doivent être différents, c’est le cas dans cet exemple terminer par un « / » est ajouté à la **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="77c20-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="77c20-150">Si vous souhaitez PSRepository nouvellement créé soit le référentiel par défaut, vous devez annuler l’inscription de tous les autres PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="77c20-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="77c20-151">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="77c20-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="77c20-152">Le nom de référentiel 'PSGallery' est réservé pour une utilisation par PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="77c20-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="77c20-153">Vous pouvez annuler l’inscription PSGallery, mais vous ne pouvez pas réutiliser le nom PSGallery pour un autre référentiel.</span><span class="sxs-lookup"><span data-stu-id="77c20-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="77c20-154">Si vous devez restaurer le référentiel PSGallery, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="77c20-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="77c20-155">Publication sur un dépôt local</span><span class="sxs-lookup"><span data-stu-id="77c20-155">Publishing to a local repository</span></span>

<span data-ttu-id="77c20-156">Une fois que vous avez inscrit PSRepository local, vous pouvez publier sur votre PSRepository local.</span><span class="sxs-lookup"><span data-stu-id="77c20-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="77c20-157">Il existe deux principaux scénarios de publication : publication de votre propre module et publication d’un module à partir de la PSGallery.</span><span class="sxs-lookup"><span data-stu-id="77c20-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="77c20-158">Publication d’un module que vous avez créés</span><span class="sxs-lookup"><span data-stu-id="77c20-158">Publishing a module you authored</span></span>

<span data-ttu-id="77c20-159">Utilisez `Publish-Module` et `Publish-Script` pour publier votre module sur votre PSRepository local la même façon que vous le feriez pour PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="77c20-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="77c20-160">Spécifier l’emplacement de votre code</span><span class="sxs-lookup"><span data-stu-id="77c20-160">Specify the location for your code</span></span>
- <span data-ttu-id="77c20-161">Fournir une clé d’API</span><span class="sxs-lookup"><span data-stu-id="77c20-161">Supply an API key</span></span>
- <span data-ttu-id="77c20-162">Spécifiez le nom du référentiel.</span><span class="sxs-lookup"><span data-stu-id="77c20-162">Specify the repository name.</span></span> <span data-ttu-id="77c20-163">Par exemple, `-PSRepository LocalPSRepo`.</span><span class="sxs-lookup"><span data-stu-id="77c20-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="77c20-164">Vous devez créer un compte dans le serveur NuGet, puis connectez-vous à générer et enregistrer la clé API.</span><span class="sxs-lookup"><span data-stu-id="77c20-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="77c20-165">Un partage de fichiers, utilisez n’importe quelle chaîne non vide pour la valeur NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="77c20-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="77c20-166">Exemples :</span><span class="sxs-lookup"><span data-stu-id="77c20-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="77c20-167">Pour garantir la sécurité, les clés de l’API ne doivent pas être codées en dur dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="77c20-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="77c20-168">Utilisez un système de gestion sécurisée des clés.</span><span class="sxs-lookup"><span data-stu-id="77c20-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="77c20-169">Publication d’un module à partir de la PSGallery</span><span class="sxs-lookup"><span data-stu-id="77c20-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="77c20-170">Pour publier un module à partir de la PSGallery sur votre PSRepository local, vous pouvez utiliser l’applet de commande « Save-Package ».</span><span class="sxs-lookup"><span data-stu-id="77c20-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="77c20-171">Spécifiez le nom du Package</span><span class="sxs-lookup"><span data-stu-id="77c20-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="77c20-172">Spécifiez 'NuGet' en tant que le fournisseur</span><span class="sxs-lookup"><span data-stu-id="77c20-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="77c20-173">Spécifiez l’emplacement de PSGallery en tant que le (source)https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="77c20-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="77c20-174">Spécifiez le chemin d’accès à votre référentiel local</span><span class="sxs-lookup"><span data-stu-id="77c20-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="77c20-175">Exemple :</span><span class="sxs-lookup"><span data-stu-id="77c20-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="77c20-176">Si votre PSRepository local est basé sur le web, il nécessite une étape supplémentaire qui utilise nuget.exe pour publier.</span><span class="sxs-lookup"><span data-stu-id="77c20-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="77c20-177">Consultez la documentation relative à l’aide de [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="77c20-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="77c20-178">Installation de PowerShellGet sur un système déconnecté</span><span class="sxs-lookup"><span data-stu-id="77c20-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="77c20-179">Déploiement de PowerShellGet est difficile dans les environnements qui requièrent des systèmes à être déconnecté d’internet.</span><span class="sxs-lookup"><span data-stu-id="77c20-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="77c20-180">PowerShellGet a un processus d’amorçage qui installe la dernière version de la première fois, qu'il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="77c20-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="77c20-181">Le module OfflinePowerShellGetDeploy dans PowerShell Gallery fournit des applets de commande qui prennent en charge ce processus d’amorçage.</span><span class="sxs-lookup"><span data-stu-id="77c20-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="77c20-182">Pour démarrer un déploiement hors connexion, vous devez :</span><span class="sxs-lookup"><span data-stu-id="77c20-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="77c20-183">Téléchargez et installez le système OfflinePowerShellGetDeploy votre connecté à internet et vos systèmes déconnectés</span><span class="sxs-lookup"><span data-stu-id="77c20-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="77c20-184">Télécharger PowerShellGet et ses dépendances sur le système connecté à internet à l’aide de la `Save-PowerShellGetForOffline` applet de commande</span><span class="sxs-lookup"><span data-stu-id="77c20-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="77c20-185">Copiez PowerShellGet et ses dépendances à partir du système connecté à internet au système déconnecté</span><span class="sxs-lookup"><span data-stu-id="77c20-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="77c20-186">Utilisez le `Install-PowerShellGetOffline` sur le système déconnecté pour placer PowerShellGet et ses dépendances dans les dossiers appropriés</span><span class="sxs-lookup"><span data-stu-id="77c20-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="77c20-187">Ces commandes utilisent `Save-PowerShellGetForOffline` à placer tous les composants dans un dossier `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="77c20-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="77c20-188">À ce stade, vous devez apporter le contenu de `F:\OfflinePowerShellGet` disponible à vos systèmes déconnectés.</span><span class="sxs-lookup"><span data-stu-id="77c20-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="77c20-189">Exécutez le `Install-PowerShellGetOffline` applet de commande pour installer PowerShellGet sur le système déconnecté.</span><span class="sxs-lookup"><span data-stu-id="77c20-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="77c20-190">Il est important que vous n’exécutez pas PowerShellGet dans la session PowerShell avant d’exécuter ces commandes.</span><span class="sxs-lookup"><span data-stu-id="77c20-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="77c20-191">Une fois que PowerShellGet est chargé dans la session, les composants ne peuvent pas être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="77c20-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="77c20-192">Si vous ne démarrez pas par erreur PowerShellGet, quittez et redémarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77c20-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="77c20-193">Après avoir exécuté ces commandes, vous êtes prêt à publier PowerShellGet dans votre référentiel local.</span><span class="sxs-lookup"><span data-stu-id="77c20-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="77c20-194">Pour garantir la sécurité, les clés de l’API ne doivent pas être codées en dur dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="77c20-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="77c20-195">Utilisez un système de gestion sécurisée des clés.</span><span class="sxs-lookup"><span data-stu-id="77c20-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[NuGet.exe]: /nuget/tools/nuget-exe-cli-reference
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
