---
ms.date: 11/06/2018
title: Travailler avec des PSRepository locaux
description: Le module PowerShellGet prend en charge des référentiels autres que PowerShell Gallery. Cet article explique comment configurer un référentiel PowerShell local.
ms.openlocfilehash: 24a2fd23124b3897952d64a347d103d9ee10248f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662359"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="1fbb8-104">Utilisation des référentiels PowerShellGet privés</span><span class="sxs-lookup"><span data-stu-id="1fbb8-104">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="1fbb8-105">Le module PowerShellGet prend en charge des référentiels autres que PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-105">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="1fbb8-106">Ces cmdlets gèrent les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="1fbb8-106">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="1fbb8-107">prise en charge d’un ensemble approuvé et prévalidé de modules PowerShell dans l’environnement ;</span><span class="sxs-lookup"><span data-stu-id="1fbb8-107">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="1fbb8-108">test d’un pipeline CI/CD qui génère des modules ou des scripts PowerShell ;</span><span class="sxs-lookup"><span data-stu-id="1fbb8-108">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="1fbb8-109">envoi de scripts et de modules PowerShell aux systèmes qui n’ont pas accès à Internet.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-109">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="1fbb8-110">Fournir des scripts et des modules PowerShell accessibles uniquement à votre organisation</span><span class="sxs-lookup"><span data-stu-id="1fbb8-110">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="1fbb8-111">Cet article explique comment configurer un référentiel PowerShell local.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-111">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="1fbb8-112">Il aborde également le module [OfflinePowerShellGetDeploy][] disponible sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-112">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="1fbb8-113">Ce module contient des cmdlets permettant d’installer la dernière version de PowerShellGet dans un référentiel local.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-113">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="1fbb8-114">Types de référentiels locaux</span><span class="sxs-lookup"><span data-stu-id="1fbb8-114">Local repository types</span></span>

<span data-ttu-id="1fbb8-115">Il existe deux moyens de créer un PSRepository local : un serveur NuGet ou un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-115">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="1fbb8-116">Chacun présente des avantages et des inconvénients :</span><span class="sxs-lookup"><span data-stu-id="1fbb8-116">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="1fbb8-117">Serveur NuGet</span><span class="sxs-lookup"><span data-stu-id="1fbb8-117">NuGet Server</span></span>

| <span data-ttu-id="1fbb8-118">Avantages</span><span class="sxs-lookup"><span data-stu-id="1fbb8-118">Advantages</span></span>| <span data-ttu-id="1fbb8-119">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="1fbb8-119">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="1fbb8-120">Reproduction fidèle des fonctionnalités de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="1fbb8-120">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="1fbb8-121">Application multiniveau exigeant planification des opérations et support</span><span class="sxs-lookup"><span data-stu-id="1fbb8-121">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="1fbb8-122">Intégration de NuGet à Visual Studio, autres outils</span><span class="sxs-lookup"><span data-stu-id="1fbb8-122">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="1fbb8-123">Modèle d’authentification et gestion des comptes NuGet nécessaires</span><span class="sxs-lookup"><span data-stu-id="1fbb8-123">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="1fbb8-124">NuGet prend en charge les métadonnées dans les packages `.Nupkg`</span><span class="sxs-lookup"><span data-stu-id="1fbb8-124">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="1fbb8-125">Gestion de clés API et maintenance nécessaires à la publication</span><span class="sxs-lookup"><span data-stu-id="1fbb8-125">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="1fbb8-126">Fonctionnalités de recherche, d’administration de packages, etc.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-126">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="1fbb8-127">Partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="1fbb8-127">File Share</span></span>

| <span data-ttu-id="1fbb8-128">Avantages</span><span class="sxs-lookup"><span data-stu-id="1fbb8-128">Advantages</span></span>| <span data-ttu-id="1fbb8-129">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="1fbb8-129">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="1fbb8-130">Facilité de configuration, de sauvegarde et de maintenance</span><span class="sxs-lookup"><span data-stu-id="1fbb8-130">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="1fbb8-131">Indisponibilité des métadonnées utilisées par PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1fbb8-131">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="1fbb8-132">Simplicité du modèle de sécurité (autorisations utilisateur sur le partage)</span><span class="sxs-lookup"><span data-stu-id="1fbb8-132">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="1fbb8-133">Pas d’interface utilisateur au-delà du partage de fichiers de base</span><span class="sxs-lookup"><span data-stu-id="1fbb8-133">No UI beyond basic file share</span></span> |
| <span data-ttu-id="1fbb8-134">Pas de contraintes comme le remplacement des éléments existants</span><span class="sxs-lookup"><span data-stu-id="1fbb8-134">No constraints such as replacing existing items</span></span> | <span data-ttu-id="1fbb8-135">Sécurité limitée et pas d’enregistrement de l’auteur des mises à jour</span><span class="sxs-lookup"><span data-stu-id="1fbb8-135">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="1fbb8-136">PowerShellGet fonctionne avec les deux types et prend en charge la localisation des versions et l’installation des dépendances.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-136">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="1fbb8-137">Toutefois, certaines fonctionnalités compatibles avec PowerShell Gallery ne sont pas disponibles pour les partages de fichiers et les serveurs NuGet de base.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-137">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="1fbb8-138">Tout est un package : pas de différentiation des scripts, modules, ressources DSC ou capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-138">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="1fbb8-139">Les serveurs de partage de fichiers ne voient pas les métadonnées des packages, et notamment les balises.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-139">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="1fbb8-140">Créer un référentiel local</span><span class="sxs-lookup"><span data-stu-id="1fbb8-140">Creating a local repository</span></span>

<span data-ttu-id="1fbb8-141">L’article suivant présente les étapes de configuration d’un serveur NuGet.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-141">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="1fbb8-142">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="1fbb8-142">[NuGet.Server][]</span></span>

<span data-ttu-id="1fbb8-143">Suivez les étapes jusqu’à l’ajout de packages.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-143">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="1fbb8-144">La procédure de [publication d’un package](#publishing-to-a-local-repository) est traitée plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-144">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="1fbb8-145">Dans le cas d’un référentiel sur partage de fichiers, vérifiez que vos utilisateurs disposent des autorisations nécessaires pour accéder au partage de fichier.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-145">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="1fbb8-146">Inscrire un référentiel local</span><span class="sxs-lookup"><span data-stu-id="1fbb8-146">Registering a local repository</span></span>

<span data-ttu-id="1fbb8-147">Un référentiel doit être inscrit à l’aide de la commande `Register-PSRepository` pour être utilisable.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-147">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="1fbb8-148">Dans les exemples ci-dessous, **InstallationPolicy** a pour valeur *Trusted* , partant du principe que vous faites confiance à votre propre référentiel.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-148">In the examples below, the **InstallationPolicy** is set to *Trusted* , on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="1fbb8-149">Remarquez la différence entre les deux commandes en matière de gestion de **ScriptSourceLocation** .</span><span class="sxs-lookup"><span data-stu-id="1fbb8-149">Take note of the difference between how the two commands handle **ScriptSourceLocation** .</span></span> <span data-ttu-id="1fbb8-150">Pour les référentiels sur partage de fichiers, **SourceLocation** et **ScriptSourceLocation** doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-150">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="1fbb8-151">Dans le cas d’un référentiel web, ils doivent être différents : dans cet exemple, une barre oblique « / » de fin est ajoutée à **SourceLocation** .</span><span class="sxs-lookup"><span data-stu-id="1fbb8-151">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation** .</span></span>

<span data-ttu-id="1fbb8-152">Pour que le nouveau PSRepository soit le référentiel par défaut, il faut annuler l’inscription de tous les autres PSRepository.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-152">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="1fbb8-153">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1fbb8-153">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="1fbb8-154">Le nom de référentiel « PSGallery » est réservé à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-154">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="1fbb8-155">Il est possible d’annuler l’inscription de PSGallery, mais pas de réutiliser le nom PSGallery pour un autre référentiel.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-155">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="1fbb8-156">Si vous devez restaurer PSGallery, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1fbb8-156">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="1fbb8-157">Publier sur un référentiel local</span><span class="sxs-lookup"><span data-stu-id="1fbb8-157">Publishing to a local repository</span></span>

<span data-ttu-id="1fbb8-158">Vous pouvez publier sur votre PSRepository local dès qu’il est inscrit.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-158">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="1fbb8-159">Il existe deux grands scénarios de publication : votre propre module ou un module provenant de PSGallery.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-159">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="1fbb8-160">Publier un module créé par vos soins</span><span class="sxs-lookup"><span data-stu-id="1fbb8-160">Publishing a module you authored</span></span>

<span data-ttu-id="1fbb8-161">Utilisez `Publish-Module` et `Publish-Script` pour publier votre module sur votre PSRepository local, comme sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-161">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="1fbb8-162">Spécifiez l’emplacement de votre code.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-162">Specify the location for your code</span></span>
- <span data-ttu-id="1fbb8-163">Indiquez une clé API.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-163">Supply an API key</span></span>
- <span data-ttu-id="1fbb8-164">Spécifiez le nom du référentiel.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-164">Specify the repository name.</span></span> <span data-ttu-id="1fbb8-165">Par exemple : `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="1fbb8-165">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="1fbb8-166">Vous devez créer un compte dans le serveur NuGet, puis vous connecter pour générer et enregistrer la clé API.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-166">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="1fbb8-167">Pour un partage de fichiers, utilisez une chaîne non vide comme valeur NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-167">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="1fbb8-168">Exemples :</span><span class="sxs-lookup"><span data-stu-id="1fbb8-168">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> <span data-ttu-id="1fbb8-169">Pour des raisons de sécurité, les clés API ne doivent pas être codées en dur dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-169">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="1fbb8-170">Utilisez un système de gestion de clés sécurisé.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-170">Use a secure key management system.</span></span> <span data-ttu-id="1fbb8-171">Quand vous exécutez une commande manuellement, les clés API ne doivent pas être transmises en texte brut pour éviter qu’il soit journalisé. L’applet de commande `Read-Host` peut être utilisée pour transmettre en toute sécurité la valeur de la clé API.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-171">When executing a command manually, API keys should not be passed as plain-text to avoid it being logged, the `Read-Host` cmdlet can be used to safely pass the value of the API key.</span></span>

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="1fbb8-172">Publier un module provenant de PSGallery</span><span class="sxs-lookup"><span data-stu-id="1fbb8-172">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="1fbb8-173">Pour publier un module provenant de PSGallery sur votre PSRepository local, vous pouvez utiliser la cmdlet « Save-Package ».</span><span class="sxs-lookup"><span data-stu-id="1fbb8-173">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="1fbb8-174">Spécifiez le nom du package.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-174">Specify the Name of the Package</span></span>
- <span data-ttu-id="1fbb8-175">Spécifiez « NuGet » comme fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-175">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="1fbb8-176">Spécifiez l’emplacement PSGallery comme source (https://www.powershellgallery.com/api/v2).</span><span class="sxs-lookup"><span data-stu-id="1fbb8-176">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="1fbb8-177">Spécifiez le chemin de votre référentiel local.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-177">Specify the path to your local Repository</span></span>

<span data-ttu-id="1fbb8-178">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1fbb8-178">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="1fbb8-179">Si votre PSRepository local est un référentiel web, la publication comporte une étape supplémentaire, qui utilise nuget.exe.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-179">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="1fbb8-180">Voir la documentation sur [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="1fbb8-180">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="1fbb8-181">Installer PowerShellGet sur un système déconnecté</span><span class="sxs-lookup"><span data-stu-id="1fbb8-181">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="1fbb8-182">Il est difficile de déployer PowerShellGet dans des environnements où les systèmes doivent être déconnectés d’Internet.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-182">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="1fbb8-183">PowerShellGet comporte un processus de démarrage qui installe la dernière version la première fois qu’il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-183">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="1fbb8-184">Le module OfflinePowerShellGetDeploy de PowerShell Gallery fournit des cmdlets qui gèrent ce processus de démarrage.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-184">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="1fbb8-185">Pour démarrer un déploiement hors connexion :</span><span class="sxs-lookup"><span data-stu-id="1fbb8-185">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="1fbb8-186">Téléchargez et installez OfflinePowerShellGetDeploy sur votre système connecté à Internet et vos systèmes déconnectés.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-186">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="1fbb8-187">Téléchargez PowerShellGet et ses dépendances sur le système connecté à Internet avec la cmdlet `Save-PowerShellGetForOffline`.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-187">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="1fbb8-188">Copiez PowerShellGet et ses dépendances du système connecté à Internet au système déconnecté.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-188">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="1fbb8-189">Utilisez `Install-PowerShellGetOffline` sur le système déconnecté pour placer PowerShellGet et ses dépendances dans les dossiers correspondants.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-189">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="1fbb8-190">Les commandes suivantes utilisent `Save-PowerShellGetForOffline` pour placer tous les composants dans un dossier `f:\OfflinePowerShellGet`.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-190">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="1fbb8-191">Rendez maintenant le contenu de `F:\OfflinePowerShellGet` accessible à vos systèmes déconnectés.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-191">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="1fbb8-192">Exécutez la cmdlet `Install-PowerShellGetOffline` pour installer PowerShellGet sur le système déconnecté.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-192">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="1fbb8-193">Il est important de ne pas exécuter PowerShellGet dans la session PowerShell avant d’avoir exécuté ces commandes.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-193">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="1fbb8-194">Une fois PowerShellGet chargé dans la session, il n’est plus possible de mettre à jour les composants.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-194">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="1fbb8-195">Si vous lancez PowerShellGet par erreur, quittez et redémarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-195">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="1fbb8-196">Une fois que vous avez exécuté ces commandes, vous pouvez publier PowerShellGet dans votre référentiel local.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-196">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> <span data-ttu-id="1fbb8-197">Pour des raisons de sécurité, les clés API ne doivent pas être codées en dur dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-197">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="1fbb8-198">Utilisez un système de gestion de clés sécurisé.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-198">Use a secure key management system.</span></span> <span data-ttu-id="1fbb8-199">Quand vous exécutez une commande manuellement, les clés API ne doivent pas être transmises en texte brut pour éviter qu’il soit journalisé. L’applet de commande `Read-Host` peut être utilisée pour transmettre en toute sécurité la valeur de la clé API.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-199">When executing a command manually, API keys should not be passed as plain-text to avoid it being logged, the `Read-Host` cmdlet can be used to safely pass the value of the API key.</span></span>

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="1fbb8-200">Utiliser des solutions de packaging pour héberger des référentiels PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1fbb8-200">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="1fbb8-201">Vous pouvez également utiliser des solutions de packaging comme Azure Artifacts pour héberger un référentiel PowerShellGet privé ou public.</span><span class="sxs-lookup"><span data-stu-id="1fbb8-201">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="1fbb8-202">Pour obtenir des informations complémentaires et des instructions, consultez la [documentation Azure Artifacts](/azure/devops/artifacts/tutorials/private-powershell-library).</span><span class="sxs-lookup"><span data-stu-id="1fbb8-202">For more information and instructions, see the [Azure Artifacts documentation](/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
