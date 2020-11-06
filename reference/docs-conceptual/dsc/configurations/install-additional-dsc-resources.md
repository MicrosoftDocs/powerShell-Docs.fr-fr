---
ms.date: 12/12/2018
keywords: dsc,powershell,ressource,galerie,configuration
title: Installer des ressources DSC supplémentaires
description: Cet article répertorie les ressources DSC incluses dans le module PSDesiredStateConfiguration. Il explique également comment rechercher et installer des ressources à partir de PowerShell Gallery.
ms.openlocfilehash: e75561ed539e06716c9a103f905b9d1e4f3e71d3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645129"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="e3924-105">Installer des ressources DSC supplémentaires</span><span class="sxs-lookup"><span data-stu-id="e3924-105">Install Additional DSC Resources</span></span>

<span data-ttu-id="e3924-106">PowerShell inclut plusieurs ressources prêtes à l’emploi (OOB) pour Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="e3924-106">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="e3924-107">Le module **PSDesiredStateConfiguration** contient toutes les ressources OOB DSC disponibles sur votre instance spécifique de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3924-107">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="e3924-108">Il s’agit d’une liste des ressources OOB incluses dans PowerShell 4.0 et d’une description des fonctionnalités de chaque ressource.</span><span class="sxs-lookup"><span data-stu-id="e3924-108">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="e3924-109">Cette liste est incomplète car le nombre de ressources OOB a augmenté avec chaque version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3924-109">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|      <span data-ttu-id="e3924-110">Ressource</span><span class="sxs-lookup"><span data-stu-id="e3924-110">Resource</span></span>      |                                                                                       <span data-ttu-id="e3924-111">Description</span><span class="sxs-lookup"><span data-stu-id="e3924-111">Description</span></span>                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e3924-112">**File**</span><span class="sxs-lookup"><span data-stu-id="e3924-112">**File**</span></span>           | <span data-ttu-id="e3924-113">Contrôle l’état des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="e3924-113">Controls the state of files and directories.</span></span> <span data-ttu-id="e3924-114">Copie les fichiers d’une **source** vers une **destination** et les met à jour à chaque modification de la **source** en comparant les dates, les sommes de contrôle et les hachages.</span><span class="sxs-lookup"><span data-stu-id="e3924-114">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span> |
| <span data-ttu-id="e3924-115">**Archive**</span><span class="sxs-lookup"><span data-stu-id="e3924-115">**Archive**</span></span>        | <span data-ttu-id="e3924-116">Décompresse les archives et un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="e3924-116">Unpacks archives and a specified location.</span></span> <span data-ttu-id="e3924-117">Valide les archives avec une **somme de contrôle** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e3924-117">Validates the archives with a specified **Checksum**.</span></span>                                                                                         |
| <span data-ttu-id="e3924-118">**Environment**</span><span class="sxs-lookup"><span data-stu-id="e3924-118">**Environment**</span></span>    | <span data-ttu-id="e3924-119">Gère les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="e3924-119">Manages environment variables.</span></span>                                                                                                                                                           |
| <span data-ttu-id="e3924-120">**Groupe**</span><span class="sxs-lookup"><span data-stu-id="e3924-120">**Group**</span></span>          | <span data-ttu-id="e3924-121">Gère les groupes locaux et contrôle l’appartenance au groupe.</span><span class="sxs-lookup"><span data-stu-id="e3924-121">Manages local groups and controls group membership.</span></span>                                                                                                                                      |
| <span data-ttu-id="e3924-122">**Journal**</span><span class="sxs-lookup"><span data-stu-id="e3924-122">**Log**</span></span>            | <span data-ttu-id="e3924-123">Consigne des messages dans le journal des événements `Microsoft-Windows-Desired State Configuration/Analytic`.</span><span class="sxs-lookup"><span data-stu-id="e3924-123">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>                                                                                               |
| <span data-ttu-id="e3924-124">**Package**</span><span class="sxs-lookup"><span data-stu-id="e3924-124">**Package**</span></span>        | <span data-ttu-id="e3924-125">Installe ou désinstalle des packages à l’aide des paramètres **Arguments** , **LogPath** , **ReturnCode** , entre autres.</span><span class="sxs-lookup"><span data-stu-id="e3924-125">Installs or uninstalls packages using **Arguments** , **LogPath** , **ReturnCode** , other settings.</span></span>                                                                                        |
| <span data-ttu-id="e3924-126">**Registre**</span><span class="sxs-lookup"><span data-stu-id="e3924-126">**Registry**</span></span>       | <span data-ttu-id="e3924-127">Gère les valeurs et clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="e3924-127">Manages registry keys and values.</span></span>                                                                                                                                                        |
| <span data-ttu-id="e3924-128">**Script**</span><span class="sxs-lookup"><span data-stu-id="e3924-128">**Script**</span></span>         | <span data-ttu-id="e3924-129">Vous permet de concevoir vos propres blocs de script [get-test-set](../resources/get-test-set.md).</span><span class="sxs-lookup"><span data-stu-id="e3924-129">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>                                                                                                |
| <span data-ttu-id="e3924-130">**Service**</span><span class="sxs-lookup"><span data-stu-id="e3924-130">**Service**</span></span>        | <span data-ttu-id="e3924-131">Configure les services Windows.</span><span class="sxs-lookup"><span data-stu-id="e3924-131">Configures Windows services.</span></span>                                                                                                                                                             |
| <span data-ttu-id="e3924-132">**Utilisateur**</span><span class="sxs-lookup"><span data-stu-id="e3924-132">**User**</span></span>           | <span data-ttu-id="e3924-133">Gère les attributs et les utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="e3924-133">Manages local users and attributes.</span></span>                                                                                                                                                      |
| <span data-ttu-id="e3924-134">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="e3924-134">**WindowsFeature**</span></span> | <span data-ttu-id="e3924-135">Supprime des rôles et des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="e3924-135">Manages roles and features.</span></span>                                                                                                                                                              |
| <span data-ttu-id="e3924-136">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="e3924-136">**WindowsProcess**</span></span> | <span data-ttu-id="e3924-137">Configure les processus Windows.</span><span class="sxs-lookup"><span data-stu-id="e3924-137">Configures Windows processes.</span></span>                                                                                                                                                            |

<span data-ttu-id="e3924-138">Les ressources OOB constituent un bon point de départ pour les opérations courantes.</span><span class="sxs-lookup"><span data-stu-id="e3924-138">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="e3924-139">Si les ressources OOB ne répondent pas à vos besoins, vous pouvez écrire votre propre [ressource personnalisée](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="e3924-139">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="e3924-140">Avant d’écrire une ressource personnalisée pour résoudre votre problème, vous devriez consulter les nombreuses ressources DSC déjà créées par Microsoft et la Communauté PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3924-140">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="e3924-141">Vous trouverez des ressources DSC dans [PowerShell Gallery](https://www.powershellgallery.com/) et [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="e3924-141">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="e3924-142">Vous pouvez également installer des ressources DSC directement à partir de la console PowerShell à l’aide de [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="e3924-142">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="e3924-143">Installation de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e3924-143">Installing PowerShellGet</span></span>

<span data-ttu-id="e3924-144">Pour déterminer si vous disposez déjà de **PowerShellGet** , ou pour obtenir de l’aide sur son installation, consultez le guide suivant : [Installation de PowerShellGet](/powershell/scripting/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="e3924-144">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/scripting/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="e3924-145">Recherche de ressources DSC à l’aide de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e3924-145">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="e3924-146">Une fois **PowerShellGet** installé sur votre système, vous pouvez rechercher et installer des ressources DSC hébergées dans [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="e3924-146">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="e3924-147">Tout d’abord, utilisez l’applet de commande [Find-DSCResource](/powershell/module/powershellget/find-dscresource) pour rechercher des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="e3924-147">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="e3924-148">Lorsque vous exécutez `Find-DSCResource` pour la première fois, le message suivant vous invite à installer le « fournisseur NuGet ».</span><span class="sxs-lookup"><span data-stu-id="e3924-148">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies'
or 'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install
the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201
-Force'. Do you want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="e3924-149">Appuyez sur « y » pour installer le fournisseur NuGet et afficher la liste des ressources DSC que vous pouvez installer à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e3924-149">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="e3924-150">Cette liste n’est pas visible car elle est très longue.</span><span class="sxs-lookup"><span data-stu-id="e3924-150">List is not shown because it is very large.</span></span>

<span data-ttu-id="e3924-151">Vous pouvez également spécifier le paramètre `-Name` à l’aide de caractères génériques, ou le paramètre `-Filter` sans caractères génériques pour affiner votre recherche.</span><span class="sxs-lookup"><span data-stu-id="e3924-151">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="e3924-152">Cet exemple tente de trouver une ressource DSC « TimeZone » (fuseau horaire) en utilisant les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="e3924-152">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3924-153">Actuellement, un bogue dans l’applet de commande `Find-DSCResource` empêche l’utilisation des caractères génériques dans les paramètres `-Name` et `-Filter`.</span><span class="sxs-lookup"><span data-stu-id="e3924-153">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="e3924-154">Le second exemple ci-dessous montre une solution de contournement qui utilise `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="e3924-154">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="e3924-155">Vous pouvez également utiliser `Where-Object` pour rechercher des ressources DSC avec un filtrage plus précis.</span><span class="sxs-lookup"><span data-stu-id="e3924-155">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="e3924-156">Cette approche sera plus lente que l’utilisation des paramètres de filtrage intégrés.</span><span class="sxs-lookup"><span data-stu-id="e3924-156">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="e3924-157">Pour plus d’informations sur le filtrage, consultez [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="e3924-157">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="e3924-158">Installation de ressources DSC à l’aide de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e3924-158">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="e3924-159">Pour installer une ressource DSC, utilisez l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module), en spécifiant le nom du module figurant sous **Module** dans vos résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="e3924-159">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="e3924-160">La ressource « TimeZone » existe dans le module « ComputerManagementDSC », et c’est donc ce module que l’exemple installe.</span><span class="sxs-lookup"><span data-stu-id="e3924-160">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="e3924-161">Si vous n’avez pas approuvé PowerShell Gallery, l’avertissement ci-dessous vous demande de confirmer et vous explique comment éviter ces invites lors des prochaines installations.</span><span class="sxs-lookup"><span data-stu-id="e3924-161">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to
install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="e3924-162">Appuyez sur « y » pour continuer l’installation du module.</span><span class="sxs-lookup"><span data-stu-id="e3924-162">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="e3924-163">Après l’installation, vous pouvez vérifier que votre nouvelle ressource est installée à l’aide de [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="e3924-163">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="e3924-164">Vous pouvez également afficher d’autres ressources de votre module nouvellement installé en spécifiant le paramètre `-ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="e3924-164">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="e3924-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3924-165">See also</span></span>

- [<span data-ttu-id="e3924-166">Présentation des ressources</span><span class="sxs-lookup"><span data-stu-id="e3924-166">What are Resources?</span></span>](../resources/resources.md)
