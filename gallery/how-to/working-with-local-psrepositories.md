---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery, powershell, applet de commande, psgallery, psget
title: Travailler avec des PSRepository locaux
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084094"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="c74ba-103">Utilisation des référentiels PowerShellGet locaux</span><span class="sxs-lookup"><span data-stu-id="c74ba-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="c74ba-104">Le module PowerShellGet prend en charge des référentiels autres que PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c74ba-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="c74ba-105">Ces cmdlets gèrent les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="c74ba-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="c74ba-106">prise en charge d’un ensemble approuvé et prévalidé de modules PowerShell dans l’environnement ;</span><span class="sxs-lookup"><span data-stu-id="c74ba-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="c74ba-107">test d’un pipeline CI/CD qui génère des modules ou des scripts PowerShell ;</span><span class="sxs-lookup"><span data-stu-id="c74ba-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="c74ba-108">envoi de scripts et de modules PowerShell aux systèmes qui n’ont pas accès à Internet.</span><span class="sxs-lookup"><span data-stu-id="c74ba-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="c74ba-109">Cet article explique comment configurer un référentiel PowerShell local.</span><span class="sxs-lookup"><span data-stu-id="c74ba-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="c74ba-110">Il aborde également le module [OfflinePowerShellGetDeploy][] disponible sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c74ba-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="c74ba-111">Ce module contient des cmdlets permettant d’installer la dernière version de PowerShellGet dans un référentiel local.</span><span class="sxs-lookup"><span data-stu-id="c74ba-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="c74ba-112">Types de référentiels locaux</span><span class="sxs-lookup"><span data-stu-id="c74ba-112">Local repository types</span></span>

<span data-ttu-id="c74ba-113">Il existe deux moyens de créer un PSRepository local : un serveur NuGet ou un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c74ba-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="c74ba-114">Chacun présente des avantages et des inconvénients :</span><span class="sxs-lookup"><span data-stu-id="c74ba-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="c74ba-115">Serveur NuGet</span><span class="sxs-lookup"><span data-stu-id="c74ba-115">NuGet Server</span></span>

| <span data-ttu-id="c74ba-116">Avantages</span><span class="sxs-lookup"><span data-stu-id="c74ba-116">Advantages</span></span>| <span data-ttu-id="c74ba-117">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="c74ba-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="c74ba-118">Reproduction fidèle des fonctionnalités de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="c74ba-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="c74ba-119">Application multiniveau exigeant planification des opérations et support</span><span class="sxs-lookup"><span data-stu-id="c74ba-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="c74ba-120">Intégration de NuGet à Visual Studio, autres outils</span><span class="sxs-lookup"><span data-stu-id="c74ba-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="c74ba-121">Modèle d’authentification et gestion des comptes NuGet nécessaires</span><span class="sxs-lookup"><span data-stu-id="c74ba-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="c74ba-122">NuGet prend en charge les métadonnées dans les packages `.Nupkg`</span><span class="sxs-lookup"><span data-stu-id="c74ba-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="c74ba-123">Gestion de clés API et maintenance nécessaires à la publication</span><span class="sxs-lookup"><span data-stu-id="c74ba-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="c74ba-124">Fonctionnalités de recherche, d’administration de packages, etc.</span><span class="sxs-lookup"><span data-stu-id="c74ba-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="c74ba-125">Partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="c74ba-125">File Share</span></span>

| <span data-ttu-id="c74ba-126">Avantages</span><span class="sxs-lookup"><span data-stu-id="c74ba-126">Advantages</span></span>| <span data-ttu-id="c74ba-127">Inconvénients</span><span class="sxs-lookup"><span data-stu-id="c74ba-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="c74ba-128">Facilité de configuration, de sauvegarde et de maintenance</span><span class="sxs-lookup"><span data-stu-id="c74ba-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="c74ba-129">Indisponibilité des métadonnées utilisées par PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c74ba-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="c74ba-130">Simplicité du modèle de sécurité (autorisations utilisateur sur le partage)</span><span class="sxs-lookup"><span data-stu-id="c74ba-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="c74ba-131">Pas d’interface utilisateur au-delà du partage de fichiers de base</span><span class="sxs-lookup"><span data-stu-id="c74ba-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="c74ba-132">Pas de contraintes comme le remplacement des éléments existants</span><span class="sxs-lookup"><span data-stu-id="c74ba-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="c74ba-133">Sécurité limitée et pas d’enregistrement de l’auteur des mises à jour</span><span class="sxs-lookup"><span data-stu-id="c74ba-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="c74ba-134">PowerShellGet fonctionne avec les deux types et prend en charge la localisation des versions et l’installation des dépendances.</span><span class="sxs-lookup"><span data-stu-id="c74ba-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="c74ba-135">Toutefois, certaines fonctionnalités compatibles avec PowerShell Gallery ne sont pas disponibles pour les partages de fichiers et les serveurs NuGet de base.</span><span class="sxs-lookup"><span data-stu-id="c74ba-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="c74ba-136">Tout est un package : pas de différentiation des scripts, modules, ressources DSC ou capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="c74ba-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="c74ba-137">Les serveurs de partage de fichiers ne voient pas les métadonnées des packages, et notamment les balises.</span><span class="sxs-lookup"><span data-stu-id="c74ba-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="c74ba-138">Créer un référentiel local</span><span class="sxs-lookup"><span data-stu-id="c74ba-138">Creating a local repository</span></span>

<span data-ttu-id="c74ba-139">L’article suivant présente les étapes de configuration d’un serveur NuGet.</span><span class="sxs-lookup"><span data-stu-id="c74ba-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="c74ba-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="c74ba-140">[NuGet.Server][]</span></span>

<span data-ttu-id="c74ba-141">Suivez les étapes jusqu’à l’ajout de packages.</span><span class="sxs-lookup"><span data-stu-id="c74ba-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="c74ba-142">La procédure de [publication d’un package](#publishing-to-a-local-repository) est traitée plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="c74ba-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="c74ba-143">Dans le cas d’un référentiel sur partage de fichiers, vérifiez que vos utilisateurs disposent des autorisations nécessaires pour accéder au partage de fichier.</span><span class="sxs-lookup"><span data-stu-id="c74ba-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="c74ba-144">Inscrire un référentiel local</span><span class="sxs-lookup"><span data-stu-id="c74ba-144">Registering a local repository</span></span>

<span data-ttu-id="c74ba-145">Un référentiel doit être inscrit à l’aide de la commande `Register-PSRepository` pour être utilisable.</span><span class="sxs-lookup"><span data-stu-id="c74ba-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="c74ba-146">Dans les exemples ci-dessous, **InstallationPolicy** a pour valeur *Trusted*, partant du principe que vous faites confiance à votre propre référentiel.</span><span class="sxs-lookup"><span data-stu-id="c74ba-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="c74ba-147">Remarquez la différence entre les deux commandes en matière de gestion de **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="c74ba-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="c74ba-148">Pour les référentiels sur partage de fichiers, **SourceLocation** et **ScriptSourceLocation** doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="c74ba-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="c74ba-149">Dans le cas d’un référentiel web, ils doivent être différents : dans cet exemple, une barre oblique « / » de fin est ajoutée à **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="c74ba-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="c74ba-150">Pour que le nouveau PSRepository soit le référentiel par défaut, il faut annuler l’inscription de tous les autres PSRepository.</span><span class="sxs-lookup"><span data-stu-id="c74ba-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="c74ba-151">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c74ba-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="c74ba-152">Le nom de référentiel « PSGallery » est réservé à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c74ba-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="c74ba-153">Il est possible d’annuler l’inscription de PSGallery, mais pas de réutiliser le nom PSGallery pour un autre référentiel.</span><span class="sxs-lookup"><span data-stu-id="c74ba-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="c74ba-154">Si vous devez restaurer PSGallery, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c74ba-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="c74ba-155">Publier sur un référentiel local</span><span class="sxs-lookup"><span data-stu-id="c74ba-155">Publishing to a local repository</span></span>

<span data-ttu-id="c74ba-156">Vous pouvez publier sur votre PSRepository local dès qu’il est inscrit.</span><span class="sxs-lookup"><span data-stu-id="c74ba-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="c74ba-157">Il existe deux grands scénarios de publication : votre propre module ou un module provenant de PSGallery.</span><span class="sxs-lookup"><span data-stu-id="c74ba-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="c74ba-158">Publier un module créé par vos soins</span><span class="sxs-lookup"><span data-stu-id="c74ba-158">Publishing a module you authored</span></span>

<span data-ttu-id="c74ba-159">Utilisez `Publish-Module` et `Publish-Script` pour publier votre module sur votre PSRepository local, comme sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c74ba-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="c74ba-160">Spécifiez l’emplacement de votre code.</span><span class="sxs-lookup"><span data-stu-id="c74ba-160">Specify the location for your code</span></span>
- <span data-ttu-id="c74ba-161">Indiquez une clé API.</span><span class="sxs-lookup"><span data-stu-id="c74ba-161">Supply an API key</span></span>
- <span data-ttu-id="c74ba-162">Spécifiez le nom du référentiel.</span><span class="sxs-lookup"><span data-stu-id="c74ba-162">Specify the repository name.</span></span> <span data-ttu-id="c74ba-163">Par exemple, `-PSRepository LocalPSRepo`.</span><span class="sxs-lookup"><span data-stu-id="c74ba-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="c74ba-164">Vous devez créer un compte dans le serveur NuGet, puis vous connecter pour générer et enregistrer la clé API.</span><span class="sxs-lookup"><span data-stu-id="c74ba-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="c74ba-165">Pour un partage de fichiers, utilisez une chaîne non vide comme valeur NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="c74ba-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="c74ba-166">Exemples :</span><span class="sxs-lookup"><span data-stu-id="c74ba-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="c74ba-167">Pour des raisons de sécurité, les clés API ne doivent pas être codées en dur dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="c74ba-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="c74ba-168">Utilisez un système de gestion de clés sécurisé.</span><span class="sxs-lookup"><span data-stu-id="c74ba-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="c74ba-169">Publier un module provenant de PSGallery</span><span class="sxs-lookup"><span data-stu-id="c74ba-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="c74ba-170">Pour publier un module provenant de PSGallery sur votre PSRepository local, vous pouvez utiliser la cmdlet « Save-Package ».</span><span class="sxs-lookup"><span data-stu-id="c74ba-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="c74ba-171">Spécifiez le nom du package.</span><span class="sxs-lookup"><span data-stu-id="c74ba-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="c74ba-172">Spécifiez « NuGet » comme fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c74ba-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="c74ba-173">Spécifiez l’emplacement PSGallery comme source (https://www.powershellgallery.com/api/v2).</span><span class="sxs-lookup"><span data-stu-id="c74ba-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="c74ba-174">Spécifiez le chemin de votre référentiel local.</span><span class="sxs-lookup"><span data-stu-id="c74ba-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="c74ba-175">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c74ba-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="c74ba-176">Si votre PSRepository local est un référentiel web, la publication comporte une étape supplémentaire, qui utilise nuget.exe.</span><span class="sxs-lookup"><span data-stu-id="c74ba-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="c74ba-177">Voir la documentation sur [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="c74ba-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="c74ba-178">Installer PowerShellGet sur un système déconnecté</span><span class="sxs-lookup"><span data-stu-id="c74ba-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="c74ba-179">Il est difficile de déployer PowerShellGet dans des environnements où les systèmes doivent être déconnectés d’Internet.</span><span class="sxs-lookup"><span data-stu-id="c74ba-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="c74ba-180">PowerShellGet comporte un processus de démarrage qui installe la dernière version la première fois qu’il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c74ba-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="c74ba-181">Le module OfflinePowerShellGetDeploy de PowerShell Gallery fournit des cmdlets qui gèrent ce processus de démarrage.</span><span class="sxs-lookup"><span data-stu-id="c74ba-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="c74ba-182">Pour démarrer un déploiement hors connexion :</span><span class="sxs-lookup"><span data-stu-id="c74ba-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="c74ba-183">Téléchargez et installez OfflinePowerShellGetDeploy sur votre système connecté à Internet et vos systèmes déconnectés.</span><span class="sxs-lookup"><span data-stu-id="c74ba-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="c74ba-184">Téléchargez PowerShellGet et ses dépendances sur le système connecté à Internet avec la cmdlet `Save-PowerShellGetForOffline`.</span><span class="sxs-lookup"><span data-stu-id="c74ba-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="c74ba-185">Copiez PowerShellGet et ses dépendances du système connecté à Internet au système déconnecté.</span><span class="sxs-lookup"><span data-stu-id="c74ba-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="c74ba-186">Utilisez `Install-PowerShellGetOffline` sur le système déconnecté pour placer PowerShellGet et ses dépendances dans les dossiers correspondants.</span><span class="sxs-lookup"><span data-stu-id="c74ba-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="c74ba-187">Les commandes suivantes utilisent `Save-PowerShellGetForOffline` pour placer tous les composants dans un dossier `f:\OfflinePowerShellGet`.</span><span class="sxs-lookup"><span data-stu-id="c74ba-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="c74ba-188">Rendez maintenant le contenu de `F:\OfflinePowerShellGet` accessible à vos systèmes déconnectés.</span><span class="sxs-lookup"><span data-stu-id="c74ba-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="c74ba-189">Exécutez la cmdlet `Install-PowerShellGetOffline` pour installer PowerShellGet sur le système déconnecté.</span><span class="sxs-lookup"><span data-stu-id="c74ba-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="c74ba-190">Il est important de ne pas exécuter PowerShellGet dans la session PowerShell avant d’avoir exécuté ces commandes.</span><span class="sxs-lookup"><span data-stu-id="c74ba-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="c74ba-191">Une fois PowerShellGet chargé dans la session, il n’est plus possible de mettre à jour les composants.</span><span class="sxs-lookup"><span data-stu-id="c74ba-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="c74ba-192">Si vous lancez PowerShellGet par erreur, quittez et redémarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c74ba-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="c74ba-193">Une fois que vous avez exécuté ces commandes, vous pouvez publier PowerShellGet dans votre référentiel local.</span><span class="sxs-lookup"><span data-stu-id="c74ba-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="c74ba-194">Pour des raisons de sécurité, les clés API ne doivent pas être codées en dur dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="c74ba-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="c74ba-195">Utilisez un système de gestion de clés sécurisé.</span><span class="sxs-lookup"><span data-stu-id="c74ba-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
