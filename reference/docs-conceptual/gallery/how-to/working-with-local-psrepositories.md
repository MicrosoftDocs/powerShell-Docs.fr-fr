---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery, powershell, applet de commande, psgallery, psget
title: Travailler avec des PSRepository locaux
ms.openlocfilehash: 421b73c141c7551224e2298f51464a19bc736d0e
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837577"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="1939a-103">Utilisation des référentiels PowerShellGet privés</span><span class="sxs-lookup"><span data-stu-id="1939a-103">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="1939a-104">Le module PowerShellGet prend en charge des référentiels autres que PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1939a-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="1939a-105">Ces cmdlets gèrent les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="1939a-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="1939a-106">prise en charge d’un ensemble approuvé et prévalidé de modules PowerShell dans l’environnement ;</span><span class="sxs-lookup"><span data-stu-id="1939a-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="1939a-107">test d’un pipeline CI/CD qui génère des modules ou des scripts PowerShell ;</span><span class="sxs-lookup"><span data-stu-id="1939a-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="1939a-108">envoi de scripts et de modules PowerShell aux systèmes qui n’ont pas accès à Internet.</span><span class="sxs-lookup"><span data-stu-id="1939a-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="1939a-109">Fournir des scripts et des modules PowerShell accessibles uniquement à votre organisation</span><span class="sxs-lookup"><span data-stu-id="1939a-109">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="1939a-110">Cet article explique comment configurer un référentiel PowerShell local.</span><span class="sxs-lookup"><span data-stu-id="1939a-110">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="1939a-111">Il aborde également le module [OfflinePowerShellGetDeploy][] disponible sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1939a-111">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="1939a-112">Ce module contient des cmdlets permettant d’installer la dernière version de PowerShellGet dans un référentiel local.</span><span class="sxs-lookup"><span data-stu-id="1939a-112">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="1939a-113">Types de référentiels locaux</span><span class="sxs-lookup"><span data-stu-id="1939a-113">Local repository types</span></span>

<span data-ttu-id="1939a-114">Il existe deux moyens de créer un PSRepository local : un serveur NuGet ou un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1939a-114">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="1939a-115">Chacun présente des avantages et des inconvénients :</span><span class="sxs-lookup"><span data-stu-id="1939a-115">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="1939a-116">Serveur NuGet</span><span class="sxs-lookup"><span data-stu-id="1939a-116">NuGet Server</span></span>

| <span data-ttu-id="1939a-117">Avantages</span><span class="sxs-lookup"><span data-stu-id="1939a-117">Advantages</span></span>| <span data-ttu-id="1939a-118">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="1939a-118">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="1939a-119">Reproduction fidèle des fonctionnalités de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="1939a-119">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="1939a-120">Application multiniveau exigeant planification des opérations et support</span><span class="sxs-lookup"><span data-stu-id="1939a-120">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="1939a-121">Intégration de NuGet à Visual Studio, autres outils</span><span class="sxs-lookup"><span data-stu-id="1939a-121">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="1939a-122">Modèle d’authentification et gestion des comptes NuGet nécessaires</span><span class="sxs-lookup"><span data-stu-id="1939a-122">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="1939a-123">NuGet prend en charge les métadonnées dans les packages `.Nupkg`</span><span class="sxs-lookup"><span data-stu-id="1939a-123">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="1939a-124">Gestion de clés API et maintenance nécessaires à la publication</span><span class="sxs-lookup"><span data-stu-id="1939a-124">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="1939a-125">Fonctionnalités de recherche, d’administration de packages, etc.</span><span class="sxs-lookup"><span data-stu-id="1939a-125">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="1939a-126">Partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="1939a-126">File Share</span></span>

| <span data-ttu-id="1939a-127">Avantages</span><span class="sxs-lookup"><span data-stu-id="1939a-127">Advantages</span></span>| <span data-ttu-id="1939a-128">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="1939a-128">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="1939a-129">Facilité de configuration, de sauvegarde et de maintenance</span><span class="sxs-lookup"><span data-stu-id="1939a-129">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="1939a-130">Indisponibilité des métadonnées utilisées par PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1939a-130">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="1939a-131">Simplicité du modèle de sécurité (autorisations utilisateur sur le partage)</span><span class="sxs-lookup"><span data-stu-id="1939a-131">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="1939a-132">Pas d’interface utilisateur au-delà du partage de fichiers de base</span><span class="sxs-lookup"><span data-stu-id="1939a-132">No UI beyond basic file share</span></span> |
| <span data-ttu-id="1939a-133">Pas de contraintes comme le remplacement des éléments existants</span><span class="sxs-lookup"><span data-stu-id="1939a-133">No constraints such as replacing existing items</span></span> | <span data-ttu-id="1939a-134">Sécurité limitée et pas d’enregistrement de l’auteur des mises à jour</span><span class="sxs-lookup"><span data-stu-id="1939a-134">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="1939a-135">PowerShellGet fonctionne avec les deux types et prend en charge la localisation des versions et l’installation des dépendances.</span><span class="sxs-lookup"><span data-stu-id="1939a-135">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="1939a-136">Toutefois, certaines fonctionnalités compatibles avec PowerShell Gallery ne sont pas disponibles pour les partages de fichiers et les serveurs NuGet de base.</span><span class="sxs-lookup"><span data-stu-id="1939a-136">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="1939a-137">Tout est un package : pas de différentiation des scripts, modules, ressources DSC ou capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="1939a-137">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="1939a-138">Les serveurs de partage de fichiers ne voient pas les métadonnées des packages, et notamment les balises.</span><span class="sxs-lookup"><span data-stu-id="1939a-138">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="1939a-139">Créer un référentiel local</span><span class="sxs-lookup"><span data-stu-id="1939a-139">Creating a local repository</span></span>

<span data-ttu-id="1939a-140">L’article suivant présente les étapes de configuration d’un serveur NuGet.</span><span class="sxs-lookup"><span data-stu-id="1939a-140">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="1939a-141">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="1939a-141">[NuGet.Server][]</span></span>

<span data-ttu-id="1939a-142">Suivez les étapes jusqu’à l’ajout de packages.</span><span class="sxs-lookup"><span data-stu-id="1939a-142">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="1939a-143">La procédure de [publication d’un package](#publishing-to-a-local-repository) est traitée plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="1939a-143">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="1939a-144">Dans le cas d’un référentiel sur partage de fichiers, vérifiez que vos utilisateurs disposent des autorisations nécessaires pour accéder au partage de fichier.</span><span class="sxs-lookup"><span data-stu-id="1939a-144">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="1939a-145">Inscrire un référentiel local</span><span class="sxs-lookup"><span data-stu-id="1939a-145">Registering a local repository</span></span>

<span data-ttu-id="1939a-146">Un référentiel doit être inscrit à l’aide de la commande `Register-PSRepository` pour être utilisable.</span><span class="sxs-lookup"><span data-stu-id="1939a-146">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="1939a-147">Dans les exemples ci-dessous, **InstallationPolicy** a pour valeur *Trusted*, partant du principe que vous faites confiance à votre propre référentiel.</span><span class="sxs-lookup"><span data-stu-id="1939a-147">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="1939a-148">Remarquez la différence entre les deux commandes en matière de gestion de **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="1939a-148">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="1939a-149">Pour les référentiels sur partage de fichiers, **SourceLocation** et **ScriptSourceLocation** doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="1939a-149">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="1939a-150">Dans le cas d’un référentiel web, ils doivent être différents : dans cet exemple, une barre oblique « / » de fin est ajoutée à **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="1939a-150">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="1939a-151">Pour que le nouveau PSRepository soit le référentiel par défaut, il faut annuler l’inscription de tous les autres PSRepository.</span><span class="sxs-lookup"><span data-stu-id="1939a-151">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="1939a-152">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1939a-152">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="1939a-153">Le nom de référentiel « PSGallery » est réservé à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1939a-153">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="1939a-154">Il est possible d’annuler l’inscription de PSGallery, mais pas de réutiliser le nom PSGallery pour un autre référentiel.</span><span class="sxs-lookup"><span data-stu-id="1939a-154">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="1939a-155">Si vous devez restaurer PSGallery, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1939a-155">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="1939a-156">Publier sur un référentiel local</span><span class="sxs-lookup"><span data-stu-id="1939a-156">Publishing to a local repository</span></span>

<span data-ttu-id="1939a-157">Vous pouvez publier sur votre PSRepository local dès qu’il est inscrit.</span><span class="sxs-lookup"><span data-stu-id="1939a-157">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="1939a-158">Il existe deux grands scénarios de publication : votre propre module ou un module provenant de PSGallery.</span><span class="sxs-lookup"><span data-stu-id="1939a-158">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="1939a-159">Publier un module créé par vos soins</span><span class="sxs-lookup"><span data-stu-id="1939a-159">Publishing a module you authored</span></span>

<span data-ttu-id="1939a-160">Utilisez `Publish-Module` et `Publish-Script` pour publier votre module sur votre PSRepository local, comme sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1939a-160">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="1939a-161">Spécifiez l’emplacement de votre code.</span><span class="sxs-lookup"><span data-stu-id="1939a-161">Specify the location for your code</span></span>
- <span data-ttu-id="1939a-162">Indiquez une clé API.</span><span class="sxs-lookup"><span data-stu-id="1939a-162">Supply an API key</span></span>
- <span data-ttu-id="1939a-163">Spécifiez le nom du référentiel.</span><span class="sxs-lookup"><span data-stu-id="1939a-163">Specify the repository name.</span></span> <span data-ttu-id="1939a-164">Par exemple : `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="1939a-164">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="1939a-165">Vous devez créer un compte dans le serveur NuGet, puis vous connecter pour générer et enregistrer la clé API.</span><span class="sxs-lookup"><span data-stu-id="1939a-165">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="1939a-166">Pour un partage de fichiers, utilisez une chaîne non vide comme valeur NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="1939a-166">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="1939a-167">Exemples :</span><span class="sxs-lookup"><span data-stu-id="1939a-167">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> <span data-ttu-id="1939a-168">Pour des raisons de sécurité, les clés API ne doivent pas être codées en dur dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="1939a-168">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="1939a-169">Utilisez un système de gestion de clés sécurisé.</span><span class="sxs-lookup"><span data-stu-id="1939a-169">Use a secure key management system.</span></span> <span data-ttu-id="1939a-170">Quand vous exécutez une commande manuellement, les clés API ne doivent pas être transmises en texte brut pour éviter qu’il soit journalisé. L’applet de commande `Read-Host` peut être utilisée pour transmettre en toute sécurité la valeur de la clé API.</span><span class="sxs-lookup"><span data-stu-id="1939a-170">When executing a command manually, API keys should not be passed as plain-text to avoid it being logged, the `Read-Host` cmdlet can be used to safely pass the value of the API key.</span></span>

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="1939a-171">Publier un module provenant de PSGallery</span><span class="sxs-lookup"><span data-stu-id="1939a-171">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="1939a-172">Pour publier un module provenant de PSGallery sur votre PSRepository local, vous pouvez utiliser la cmdlet « Save-Package ».</span><span class="sxs-lookup"><span data-stu-id="1939a-172">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="1939a-173">Spécifiez le nom du package.</span><span class="sxs-lookup"><span data-stu-id="1939a-173">Specify the Name of the Package</span></span>
- <span data-ttu-id="1939a-174">Spécifiez « NuGet » comme fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1939a-174">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="1939a-175">Spécifiez l’emplacement PSGallery comme source (https://www.powershellgallery.com/api/v2).</span><span class="sxs-lookup"><span data-stu-id="1939a-175">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="1939a-176">Spécifiez le chemin de votre référentiel local.</span><span class="sxs-lookup"><span data-stu-id="1939a-176">Specify the path to your local Repository</span></span>

<span data-ttu-id="1939a-177">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1939a-177">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="1939a-178">Si votre PSRepository local est un référentiel web, la publication comporte une étape supplémentaire, qui utilise nuget.exe.</span><span class="sxs-lookup"><span data-stu-id="1939a-178">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="1939a-179">Voir la documentation sur [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="1939a-179">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="1939a-180">Installer PowerShellGet sur un système déconnecté</span><span class="sxs-lookup"><span data-stu-id="1939a-180">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="1939a-181">Il est difficile de déployer PowerShellGet dans des environnements où les systèmes doivent être déconnectés d’Internet.</span><span class="sxs-lookup"><span data-stu-id="1939a-181">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="1939a-182">PowerShellGet comporte un processus de démarrage qui installe la dernière version la première fois qu’il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="1939a-182">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="1939a-183">Le module OfflinePowerShellGetDeploy de PowerShell Gallery fournit des cmdlets qui gèrent ce processus de démarrage.</span><span class="sxs-lookup"><span data-stu-id="1939a-183">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="1939a-184">Pour démarrer un déploiement hors connexion :</span><span class="sxs-lookup"><span data-stu-id="1939a-184">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="1939a-185">Téléchargez et installez OfflinePowerShellGetDeploy sur votre système connecté à Internet et vos systèmes déconnectés.</span><span class="sxs-lookup"><span data-stu-id="1939a-185">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="1939a-186">Téléchargez PowerShellGet et ses dépendances sur le système connecté à Internet avec la cmdlet `Save-PowerShellGetForOffline`.</span><span class="sxs-lookup"><span data-stu-id="1939a-186">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="1939a-187">Copiez PowerShellGet et ses dépendances du système connecté à Internet au système déconnecté.</span><span class="sxs-lookup"><span data-stu-id="1939a-187">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="1939a-188">Utilisez `Install-PowerShellGetOffline` sur le système déconnecté pour placer PowerShellGet et ses dépendances dans les dossiers correspondants.</span><span class="sxs-lookup"><span data-stu-id="1939a-188">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="1939a-189">Les commandes suivantes utilisent `Save-PowerShellGetForOffline` pour placer tous les composants dans un dossier `f:\OfflinePowerShellGet`.</span><span class="sxs-lookup"><span data-stu-id="1939a-189">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="1939a-190">Rendez maintenant le contenu de `F:\OfflinePowerShellGet` accessible à vos systèmes déconnectés.</span><span class="sxs-lookup"><span data-stu-id="1939a-190">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="1939a-191">Exécutez la cmdlet `Install-PowerShellGetOffline` pour installer PowerShellGet sur le système déconnecté.</span><span class="sxs-lookup"><span data-stu-id="1939a-191">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="1939a-192">Il est important de ne pas exécuter PowerShellGet dans la session PowerShell avant d’avoir exécuté ces commandes.</span><span class="sxs-lookup"><span data-stu-id="1939a-192">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="1939a-193">Une fois PowerShellGet chargé dans la session, il n’est plus possible de mettre à jour les composants.</span><span class="sxs-lookup"><span data-stu-id="1939a-193">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="1939a-194">Si vous lancez PowerShellGet par erreur, quittez et redémarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1939a-194">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="1939a-195">Une fois que vous avez exécuté ces commandes, vous pouvez publier PowerShellGet dans votre référentiel local.</span><span class="sxs-lookup"><span data-stu-id="1939a-195">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> <span data-ttu-id="1939a-196">Pour des raisons de sécurité, les clés API ne doivent pas être codées en dur dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="1939a-196">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="1939a-197">Utilisez un système de gestion de clés sécurisé.</span><span class="sxs-lookup"><span data-stu-id="1939a-197">Use a secure key management system.</span></span> <span data-ttu-id="1939a-198">Quand vous exécutez une commande manuellement, les clés API ne doivent pas être transmises en texte brut pour éviter qu’il soit journalisé. L’applet de commande `Read-Host` peut être utilisée pour transmettre en toute sécurité la valeur de la clé API.</span><span class="sxs-lookup"><span data-stu-id="1939a-198">When executing a command manually, API keys should not be passed as plain-text to avoid it being logged, the `Read-Host` cmdlet can be used to safely pass the value of the API key.</span></span>

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="1939a-199">Utiliser des solutions de packaging pour héberger des référentiels PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1939a-199">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="1939a-200">Vous pouvez également utiliser des solutions de packaging comme Azure Artifacts pour héberger un référentiel PowerShellGet privé ou public.</span><span class="sxs-lookup"><span data-stu-id="1939a-200">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="1939a-201">Pour obtenir des informations complémentaires et des instructions, consultez la [documentation Azure Artifacts](/azure/devops/artifacts/tutorials/private-powershell-library).</span><span class="sxs-lookup"><span data-stu-id="1939a-201">For more information and instructions, see the [Azure Artifacts documentation](/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
