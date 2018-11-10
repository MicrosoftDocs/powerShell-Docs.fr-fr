---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Prendre en main PowerShell Gallery
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225673"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="31bdc-103">Bien démarrer avec PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="31bdc-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="31bdc-104">Le meilleur moyen d’installer des packages à partir de PowerShell Gallery est d’utiliser les cmdlets du module [PowerShellGet](/powershell/module/powershellget).</span><span class="sxs-lookup"><span data-stu-id="31bdc-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="31bdc-105">Il est inutile de se connecter pour télécharger des éléments de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="31bdc-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="31bdc-106">Il est possible de télécharger un package directement à partir de PowerShell Gallery, mais cela est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="31bdc-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="31bdc-107">Pour plus d’informations, consultez [Téléchargement manuel de package](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="31bdc-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="31bdc-108">Détecter des packages sur PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="31bdc-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="31bdc-109">Pour rechercher des packages sur PowerShell Gallery, vous pouvez utiliser le contrôle **Rechercher** sur ce site web, ou parcourir les pages Modules et Scripts.</span><span class="sxs-lookup"><span data-stu-id="31bdc-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="31bdc-110">Une autre possibilité consiste à exécuter les cmdlets [Find-Module][] et [Find-Script][], selon le type d’élément, avec `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="31bdc-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="31bdc-111">Vous pouvez filtrer les résultats de la galerie avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="31bdc-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="31bdc-112">Name</span><span class="sxs-lookup"><span data-stu-id="31bdc-112">Name</span></span>
- <span data-ttu-id="31bdc-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="31bdc-113">AllVersions</span></span>
- <span data-ttu-id="31bdc-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="31bdc-114">MinimumVersion</span></span>
- <span data-ttu-id="31bdc-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="31bdc-115">RequiredVersion</span></span>
- <span data-ttu-id="31bdc-116">Légende</span><span class="sxs-lookup"><span data-stu-id="31bdc-116">Tag</span></span>
- <span data-ttu-id="31bdc-117">Includes</span><span class="sxs-lookup"><span data-stu-id="31bdc-117">Includes</span></span>
- <span data-ttu-id="31bdc-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="31bdc-118">DscResource</span></span>
- <span data-ttu-id="31bdc-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="31bdc-119">RoleCapability</span></span>
- <span data-ttu-id="31bdc-120">Commande</span><span class="sxs-lookup"><span data-stu-id="31bdc-120">Command</span></span>
- <span data-ttu-id="31bdc-121">Filtre</span><span class="sxs-lookup"><span data-stu-id="31bdc-121">Filter</span></span>

<span data-ttu-id="31bdc-122">Si vous êtes uniquement intéressé par la détection de ressources DSC spécifiques dans PowerShell Gallery, vous pouvez exécuter l’applet de commande [Find-DscResource].</span><span class="sxs-lookup"><span data-stu-id="31bdc-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="31bdc-123">Find-DscResource retourne des données sur les ressources DSC contenues dans la galerie.</span><span class="sxs-lookup"><span data-stu-id="31bdc-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="31bdc-124">Étant donné que les ressources DSC sont toujours transmises dans le cadre d’un module, vous devez toujours exécuter [Install-Module][] pour installer ces ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="31bdc-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="31bdc-125">En savoir plus sur les packages de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="31bdc-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="31bdc-126">Maintenant que vous avez identifié un package qui vous intéresse, vous voulez probablement en savoir plus à son sujet.</span><span class="sxs-lookup"><span data-stu-id="31bdc-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="31bdc-127">Pour cela, examinez la page correspondante sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="31bdc-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="31bdc-128">Elle présente toutes les métadonnées chargées avec le package.</span><span class="sxs-lookup"><span data-stu-id="31bdc-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="31bdc-129">Ces métadonnées, fournies par l’auteur du package, ne sont pas vérifiées par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="31bdc-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="31bdc-130">Le propriétaire du package est fortement associé au compte PowerShell Gallery utilisé pour publier le package ; il est plus fiable que le champ Auteur.</span><span class="sxs-lookup"><span data-stu-id="31bdc-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="31bdc-131">Si vous découvrez un package publié qui vous semble suspect, cliquez sur **Signaler un abus** sur la page du package.</span><span class="sxs-lookup"><span data-stu-id="31bdc-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="31bdc-132">Si vous exécutez [Find-Module][] ou [Find-Script][], vous pouvez afficher ces données dans l’objet PSGetModuleInfo retourné.</span><span class="sxs-lookup"><span data-stu-id="31bdc-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="31bdc-133">Par exemple, l’exécution de `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="31bdc-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="31bdc-134">retourne des données dans le module PSReadLine dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="31bdc-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="31bdc-135">Télécharger des packages de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="31bdc-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="31bdc-136">Nous conseillons le processus suivant pour télécharger des packages de PowerShell Gallery :</span><span class="sxs-lookup"><span data-stu-id="31bdc-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="31bdc-137">Inspecter</span><span class="sxs-lookup"><span data-stu-id="31bdc-137">Inspect</span></span>

<span data-ttu-id="31bdc-138">Pour télécharger un package de PowerShell Gallery à des fins d’inspection, exécutez la cmdlet [Save-Module][] ou la cmdlet [Save-Script][], selon le type de package.</span><span class="sxs-lookup"><span data-stu-id="31bdc-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="31bdc-139">Elles permettent d’enregistrer le package localement sans l’installer et d’inspecter son contenu.</span><span class="sxs-lookup"><span data-stu-id="31bdc-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="31bdc-140">N’oubliez pas de supprimer manuellement le package enregistré.</span><span class="sxs-lookup"><span data-stu-id="31bdc-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="31bdc-141">Certains de ces packages sont créés par Microsoft, d’autres par la communauté PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31bdc-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="31bdc-142">Microsoft recommande de passer en revue le contenu et le code des packages de cette galerie avant de les installer.</span><span class="sxs-lookup"><span data-stu-id="31bdc-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="31bdc-143">Si vous découvrez un package publié qui vous semble suspect, cliquez sur **Signaler un abus** sur la page du package.</span><span class="sxs-lookup"><span data-stu-id="31bdc-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="31bdc-144">Installer</span><span class="sxs-lookup"><span data-stu-id="31bdc-144">Install</span></span>

<span data-ttu-id="31bdc-145">Pour installer un package de PowerShell Gallery à des fins d’utilisation, exécutez la cmdlet [Install-Module][] ou la cmdlet [Install-Script][], selon le type de package.</span><span class="sxs-lookup"><span data-stu-id="31bdc-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="31bdc-146">[Install-Module][] installe le module dans `$env:ProgramFiles\WindowsPowerShell\Modules` par défaut.</span><span class="sxs-lookup"><span data-stu-id="31bdc-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="31bdc-147">Cette opération nécessite un compte d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="31bdc-147">This requires an administrator account.</span></span> <span data-ttu-id="31bdc-148">Si vous ajoutez le paramètre `-Scope CurrentUser`, le module est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="31bdc-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="31bdc-149">[Install-Script][] installe le script dans `$env:ProgramFiles\WindowsPowerShell\Scripts` par défaut.</span><span class="sxs-lookup"><span data-stu-id="31bdc-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="31bdc-150">Cette opération nécessite un compte d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="31bdc-150">This requires an administrator account.</span></span> <span data-ttu-id="31bdc-151">Si vous ajoutez le paramètre `-Scope CurrentUser`, le script est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="31bdc-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="31bdc-152">Par défaut, [Install-Module][] et [Install-Script][] installent la dernière version du package.</span><span class="sxs-lookup"><span data-stu-id="31bdc-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="31bdc-153">Pour installer une version antérieure, ajoutez le paramètre `-RequiredVersion`.</span><span class="sxs-lookup"><span data-stu-id="31bdc-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="31bdc-154">Déployez</span><span class="sxs-lookup"><span data-stu-id="31bdc-154">Deploy</span></span>

<span data-ttu-id="31bdc-155">Pour déployer un package de PowerShell Gallery sur Azure Automation, cliquez sur **Déployer sur Azure Automation** sur la page de détails du package.</span><span class="sxs-lookup"><span data-stu-id="31bdc-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="31bdc-156">Le Portail de gestion Azure s’affiche : connectez-vous à l’aide de vos informations d’identification de compte Azure.</span><span class="sxs-lookup"><span data-stu-id="31bdc-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="31bdc-157">Notez que le déploiement de packages comportant des dépendances a pour effet de déployer toutes les dépendances sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="31bdc-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="31bdc-158">Pour désactiver le bouton « Déployer sur Azure Automation », ajoutez la balise **AzureAutomationNotSupported** aux métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="31bdc-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="31bdc-159">Pour plus d’informations sur Azure Automation, consultez la documentation [Azure Automation](/azure/automation).</span><span class="sxs-lookup"><span data-stu-id="31bdc-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="31bdc-160">Mettre à jour des packages de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="31bdc-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="31bdc-161">Pour mettre à jour des packages installés sur PowerShell Gallery, exécutez la cmdlet [Update-Module][] ou la cmdlet [Update-Script][].</span><span class="sxs-lookup"><span data-stu-id="31bdc-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="31bdc-162">Quand elle est exécutée sans paramètre supplémentaire, [Update-Module][] tente de mettre à jour chaque module installé en exécutant [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="31bdc-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="31bdc-163">Pour mettre à jour les modules de façon sélective, ajoutez le paramètre `-Name`.</span><span class="sxs-lookup"><span data-stu-id="31bdc-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="31bdc-164">De même, quand elle est exécutée sans paramètre supplémentaire, [Update-Script][] tente également de mettre à jour chaque script installé en exécutant [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="31bdc-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="31bdc-165">Pour mettre à jour les scripts de façon sélective, ajoutez le paramètre `-Name`.</span><span class="sxs-lookup"><span data-stu-id="31bdc-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="31bdc-166">Lister les packages installés sur PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="31bdc-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="31bdc-167">Pour connaître les modules que vous avez installés à partir de PowerShell Gallery, exécutez l’applet de commande [Get-InstalledModule][].</span><span class="sxs-lookup"><span data-stu-id="31bdc-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="31bdc-168">Cette commande répertorie tous les modules qui ont été installés directement à partir de PowerShell Gallery sur votre système.</span><span class="sxs-lookup"><span data-stu-id="31bdc-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="31bdc-169">De même, pour connaître les scripts que vous avez installés à partir de PowerShell Gallery, exécutez l’applet de commande [Get-InstalledScript][].</span><span class="sxs-lookup"><span data-stu-id="31bdc-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="31bdc-170">Cette commande répertorie tous les scripts qui ont été installés directement à partir de PowerShell Gallery sur votre système.</span><span class="sxs-lookup"><span data-stu-id="31bdc-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
