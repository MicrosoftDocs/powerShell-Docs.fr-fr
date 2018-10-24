---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Prendre en main PowerShell Gallery
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523031"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="0eb6a-103">Prendre en main PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="0eb6a-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="0eb6a-104">Le meilleur moyen d’installer des éléments à partir de PowerShell Gallery est d’utiliser les applets de commande dans le module [PowerShellGet](/powershell/module/powershellget).</span><span class="sxs-lookup"><span data-stu-id="0eb6a-104">The proper way to install items from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="0eb6a-105">Il est inutile de se connecter pour télécharger des éléments de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="0eb6a-106">Il est possible de télécharger un package directement à partir de PowerShell Gallery, mais cela est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="0eb6a-107">Pour plus d’informations, consultez [Téléchargement manuel de package](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span><span class="sxs-lookup"><span data-stu-id="0eb6a-107">For more details, see [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span></span>  


## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="0eb6a-108">Détection d’éléments dans PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="0eb6a-108">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="0eb6a-109">Vous pouvez rechercher des éléments dans PowerShell Gallery à l’aide du contrôle **Rechercher** sur ce site web, ou en parcourant les pages des modules et des scripts.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-109">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="0eb6a-110">Vous pouvez également rechercher des éléments dans PowerShell Gallery en exécutant les applets de commande [Find-Module][] et [Find-Script][], selon le type d’élément, avec `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-110">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="0eb6a-111">Vous pouvez filtrer les résultats de la galerie avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="0eb6a-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="0eb6a-112">Name</span><span class="sxs-lookup"><span data-stu-id="0eb6a-112">Name</span></span>
- <span data-ttu-id="0eb6a-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="0eb6a-113">AllVersions</span></span>
- <span data-ttu-id="0eb6a-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0eb6a-114">MinimumVersion</span></span>
- <span data-ttu-id="0eb6a-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0eb6a-115">RequiredVersion</span></span>
- <span data-ttu-id="0eb6a-116">Légende</span><span class="sxs-lookup"><span data-stu-id="0eb6a-116">Tag</span></span>
- <span data-ttu-id="0eb6a-117">Includes</span><span class="sxs-lookup"><span data-stu-id="0eb6a-117">Includes</span></span>
- <span data-ttu-id="0eb6a-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="0eb6a-118">DscResource</span></span>
- <span data-ttu-id="0eb6a-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="0eb6a-119">RoleCapability</span></span>
- <span data-ttu-id="0eb6a-120">Commande</span><span class="sxs-lookup"><span data-stu-id="0eb6a-120">Command</span></span>
- <span data-ttu-id="0eb6a-121">Filtre</span><span class="sxs-lookup"><span data-stu-id="0eb6a-121">Filter</span></span>

<span data-ttu-id="0eb6a-122">Si vous êtes uniquement intéressé par la détection de ressources DSC spécifiques dans PowerShell Gallery, vous pouvez exécuter l’applet de commande [Find-DscResource].</span><span class="sxs-lookup"><span data-stu-id="0eb6a-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="0eb6a-123">Find-DscResource retourne des données sur les ressources DSC contenues dans la galerie.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="0eb6a-124">Étant donné que les ressources DSC sont toujours transmises dans le cadre d’un module, vous devez toujours exécuter [Install-Module][] pour installer ces ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="0eb6a-125">En savoir plus sur les éléments de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="0eb6a-125">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="0eb6a-126">Une fois que vous avez identifié un élément qui vous intéresse, vous pouvez en savoir plus à son sujet.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-126">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="0eb6a-127">Pour cela, examinez la page spécifique de cet élément dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-127">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="0eb6a-128">Dans cette page, vous serez en mesure de voir toutes les métadonnées chargées avec l’élément.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-128">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="0eb6a-129">Ces métadonnées associées à un élément sont fournies par l’auteur de l’élément et ne sont pas vérifiées par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-129">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="0eb6a-130">Le propriétaire de l’élément est fortement associé au compte PowerShell Gallery utilisé pour publier l’élément et est plus fiable que le champ Auteur.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-130">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="0eb6a-131">Si vous détectez un élément publié qui vous semble suspect, cliquez sur **Signaler un abus** dans la page de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-131">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="0eb6a-132">Si vous exécutez [Find-Module][] ou [Find-Script][], vous pouvez afficher ces données dans l’objet PSGetModuleInfo retourné.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="0eb6a-133">Par exemple, l’exécution de `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="0eb6a-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="0eb6a-134">retourne des données dans le module PSReadLine dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="0eb6a-135">Téléchargement d’éléments de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="0eb6a-135">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="0eb6a-136">Nous conseillons le processus suivant lors du téléchargement des éléments de PowerShell Gallery :</span><span class="sxs-lookup"><span data-stu-id="0eb6a-136">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="0eb6a-137">Inspecter</span><span class="sxs-lookup"><span data-stu-id="0eb6a-137">Inspect</span></span>

<span data-ttu-id="0eb6a-138">Pour télécharger un élément de PowerShell Gallery pour inspection, exécutez l’applet de commande [Save-Module][] ou [Save-Script][], selon le type d’élément.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-138">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="0eb6a-139">Cela vous permet d’enregistrer l’élément localement sans l’installer et d’inspecter son contenu.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-139">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="0eb6a-140">N’oubliez pas de supprimer l’élément enregistré manuellement.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-140">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="0eb6a-141">Certains de ces éléments sont créés par Microsoft et d’autres sont créés par la communauté PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-141">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="0eb6a-142">Microsoft recommande de passer en revue le contenu et le code des éléments de cette galerie avant l’installation.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-142">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="0eb6a-143">Si vous détectez un élément publié qui vous semble suspect, cliquez sur **Signaler un abus** dans la page de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-143">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="0eb6a-144">Installer</span><span class="sxs-lookup"><span data-stu-id="0eb6a-144">Install</span></span>

<span data-ttu-id="0eb6a-145">Pour installer un élément de PowerShell Gallery à utiliser, exécutez l’applet de commande [Install-Module][] ou [Install-Script][], selon le type d’élément.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-145">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="0eb6a-146">[Install-Module][] installe le module dans `$env:ProgramFiles\WindowsPowerShell\Modules` par défaut.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="0eb6a-147">Cette opération nécessite un compte d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-147">This requires an administrator account.</span></span> <span data-ttu-id="0eb6a-148">Si vous ajoutez le paramètre `-Scope CurrentUser`, le module est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="0eb6a-149">[Install-Script][] installe le script dans `$env:ProgramFiles\WindowsPowerShell\Scripts` par défaut.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="0eb6a-150">Cette opération nécessite un compte d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-150">This requires an administrator account.</span></span> <span data-ttu-id="0eb6a-151">Si vous ajoutez le paramètre `-Scope CurrentUser`, le script est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="0eb6a-152">Par défaut, [Install-Module][] et [Install-Script][] installent la version la plus récente d’un élément.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="0eb6a-153">Pour installer une version antérieure de l’élément, ajoutez le paramètre `-RequiredVersion`.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-153">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="0eb6a-154">Déployez</span><span class="sxs-lookup"><span data-stu-id="0eb6a-154">Deploy</span></span>

<span data-ttu-id="0eb6a-155">Pour déployer un élément de PowerShell Gallery sur Azure Automation, cliquez sur **Déployer sur Azure Automation** dans la page de détails de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-155">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="0eb6a-156">Vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-156">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="0eb6a-157">Notez que le déploiement d’éléments avec des dépendances va déployer toutes les dépendances sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-157">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="0eb6a-158">Le bouton « Déployer sur Azure Automation » peut être désactivé en ajoutant la balise **AzureAutomationNotSupported** aux métadonnées de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="0eb6a-159">Pour plus d’informations sur Azure Automation, consultez la documentation [Azure Automation](/azure/automation).</span><span class="sxs-lookup"><span data-stu-id="0eb6a-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="0eb6a-160">Mise à jour d’éléments de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="0eb6a-160">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="0eb6a-161">Pour mettre à jour les éléments installés à partir de PowerShell Gallery, exécutez l’applet de commande [Update-Module][] ou [Update-Script][].</span><span class="sxs-lookup"><span data-stu-id="0eb6a-161">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="0eb6a-162">Quand elle est exécutée sans paramètre supplémentaire, [Update-Module][] tente de mettre à jour chaque module installé en exécutant [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="0eb6a-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="0eb6a-163">Pour mettre à jour les modules de façon sélective, ajoutez le paramètre `-Name`.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="0eb6a-164">De même, quand elle est exécutée sans paramètre supplémentaire, [Update-Script][] tente également de mettre à jour chaque script installé en exécutant [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="0eb6a-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="0eb6a-165">Pour mettre à jour les scripts de façon sélective, ajoutez le paramètre `-Name`.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="0eb6a-166">Répertorier les éléments que vous avez installés à partir de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="0eb6a-166">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="0eb6a-167">Pour connaître les modules que vous avez installés à partir de PowerShell Gallery, exécutez l’applet de commande [Get-InstalledModule][].</span><span class="sxs-lookup"><span data-stu-id="0eb6a-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="0eb6a-168">Cette commande répertorie tous les modules qui ont été installés directement à partir de PowerShell Gallery sur votre système.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="0eb6a-169">De même, pour connaître les scripts que vous avez installés à partir de PowerShell Gallery, exécutez l’applet de commande [Get-InstalledScript][].</span><span class="sxs-lookup"><span data-stu-id="0eb6a-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="0eb6a-170">Cette commande répertorie tous les scripts qui ont été installés directement à partir de PowerShell Gallery sur votre système.</span><span class="sxs-lookup"><span data-stu-id="0eb6a-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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