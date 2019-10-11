---
ms.date: 12/12/2018
keywords: dsc,powershell,ressource,galerie,configuration
title: Installer des ressources DSC supplémentaires
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954486"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="d1f3d-103">Installer des ressources DSC supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d1f3d-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="d1f3d-104">PowerShell inclut plusieurs ressources prêtes à l’emploi (OOB) pour Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="d1f3d-105">Le module **PSDesiredStateConfiguration** contient toutes les ressources OOB DSC disponibles sur votre instance spécifique de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="d1f3d-106">Il s’agit d’une liste des ressources OOB incluses dans PowerShell 4.0 et d’une description des fonctionnalités de chaque ressource.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="d1f3d-107">Cette liste est incomplète car le nombre de ressources OOB a augmenté avec chaque version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="d1f3d-108">Resource</span><span class="sxs-lookup"><span data-stu-id="d1f3d-108">Resource</span></span>  |<span data-ttu-id="d1f3d-109">Description</span><span class="sxs-lookup"><span data-stu-id="d1f3d-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="d1f3d-110">**File**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-110">**File**</span></span>|<span data-ttu-id="d1f3d-111">Contrôle l’état des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-111">Controls the state of files and directories.</span></span> <span data-ttu-id="d1f3d-112">Copie les fichiers d’une **source** vers une **destination** et les met à jour à chaque modification de la **source** en comparant les dates, les sommes de contrôle et les hachages.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="d1f3d-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-113">**Archive**</span></span>|<span data-ttu-id="d1f3d-114">Décompresse les archives et un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="d1f3d-115">Valide les archives avec une **somme de contrôle** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="d1f3d-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-116">**Environment**</span></span>|<span data-ttu-id="d1f3d-117">Gère les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-117">Manages environment variables.</span></span>|
|<span data-ttu-id="d1f3d-118">**Groupe**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-118">**Group**</span></span>|<span data-ttu-id="d1f3d-119">Gère les groupes locaux et contrôle l’appartenance au groupe.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="d1f3d-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-120">**Log**</span></span>|<span data-ttu-id="d1f3d-121">Consigne des messages dans le journal des événements `Microsoft-Windows-Desired State Configuration/Analytic`.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="d1f3d-122">**Package**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-122">**Package**</span></span>|<span data-ttu-id="d1f3d-123">Installe ou désinstalle des packages à l’aide des paramètres **Arguments**, **LogPath**, **ReturnCode**, entre autres.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="d1f3d-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-124">**Registry**</span></span>|<span data-ttu-id="d1f3d-125">Gère les valeurs et clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="d1f3d-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-126">**Script**</span></span>|<span data-ttu-id="d1f3d-127">Vous permet de concevoir vos propres blocs de script [get-test-set](../resources/get-test-set.md).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="d1f3d-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-128">**Service**</span></span>|<span data-ttu-id="d1f3d-129">Configure les services Windows.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-129">Configures Windows services.</span></span>|
|<span data-ttu-id="d1f3d-130">**User**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-130">**User**</span></span> |<span data-ttu-id="d1f3d-131">Gère les attributs et les utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="d1f3d-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-132">**WindowsFeature**</span></span>|<span data-ttu-id="d1f3d-133">Supprime des rôles et des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-133">Manages roles and features.</span></span>|
|<span data-ttu-id="d1f3d-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="d1f3d-134">**WindowsProcess**</span></span>|<span data-ttu-id="d1f3d-135">Configure les processus Windows.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-135">Configures Windows processes.</span></span>|

<span data-ttu-id="d1f3d-136">Les ressources OOB constituent un bon point de départ pour les opérations courantes.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="d1f3d-137">Si les ressources OOB ne répondent pas à vos besoins, vous pouvez écrire votre propre [ressource personnalisée](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="d1f3d-138">Avant d’écrire une ressource personnalisée pour résoudre votre problème, vous devriez consulter les nombreuses ressources DSC déjà créées par Microsoft et la Communauté PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="d1f3d-139">Vous trouverez des ressources DSC dans [PowerShell Gallery](https://www.powershellgallery.com/) et [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="d1f3d-140">Vous pouvez également installer des ressources DSC directement à partir de la console PowerShell à l’aide de [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="d1f3d-141">Installation de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d1f3d-141">Installing PowerShellGet</span></span>

<span data-ttu-id="d1f3d-142">Pour déterminer si vous disposez déjà de **PowerShellGet**, ou pour obtenir de l’aide sur son installation, consultez le guide suivant : [Installation de PowerShellGet](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="d1f3d-143">Recherche de ressources DSC à l’aide de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d1f3d-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="d1f3d-144">Une fois **PowerShellGet** installé sur votre système, vous pouvez rechercher et installer des ressources DSC hébergées dans [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="d1f3d-145">Tout d’abord, utilisez l’applet de commande [Find-DSCResource](/powershell/module/powershellget/find-dscresource) pour rechercher des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="d1f3d-146">Lorsque vous exécutez `Find-DSCResource` pour la première fois, le message suivant vous invite à installer le « fournisseur NuGet ».</span><span class="sxs-lookup"><span data-stu-id="d1f3d-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="d1f3d-147">Appuyez sur « y » pour installer le fournisseur NuGet et afficher la liste des ressources DSC que vous pouvez installer à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="d1f3d-148">Cette liste n’est pas visible car elle est très longue.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="d1f3d-149">Vous pouvez également spécifier le paramètre `-Name` à l’aide de caractères génériques, ou le paramètre `-Filter` sans caractères génériques pour affiner votre recherche.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="d1f3d-150">Cet exemple tente de trouver une ressource DSC « TimeZone » (fuseau horaire) en utilisant les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1f3d-151">Actuellement, un bogue dans l’applet de commande `Find-DSCResource` empêche l’utilisation des caractères génériques dans les paramètres `-Name` et `-Filter`.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="d1f3d-152">Le second exemple ci-dessous montre une solution de contournement qui utilise `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-152">The second example below shows a workaround using `Where-Object`.</span></span>

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

<span data-ttu-id="d1f3d-153">Vous pouvez également utiliser `Where-Object` pour rechercher des ressources DSC avec un filtrage plus précis.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="d1f3d-154">Cette approche sera plus lente que l’utilisation des paramètres de filtrage intégrés.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="d1f3d-155">Pour plus d’informations sur le filtrage, consultez [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="d1f3d-156">Installation de ressources DSC à l’aide de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d1f3d-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="d1f3d-157">Pour installer une ressource DSC, utilisez l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module), en spécifiant le nom du module figurant sous **Module** dans vos résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="d1f3d-158">La ressource « TimeZone » existe dans le module « ComputerManagementDSC », et c’est donc ce module que l’exemple installe.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="d1f3d-159">Si vous n’avez pas approuvé PowerShell Gallery, l’avertissement ci-dessous vous demande de confirmer et vous explique comment éviter ces invites lors des prochaines installations.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="d1f3d-160">Appuyez sur « y » pour continuer l’installation du module.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="d1f3d-161">Après l’installation, vous pouvez vérifier que votre nouvelle ressource est installée à l’aide de [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="d1f3d-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

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

<span data-ttu-id="d1f3d-162">Vous pouvez également afficher d’autres ressources de votre module nouvellement installé en spécifiant le paramètre `-ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="d1f3d-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d1f3d-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1f3d-163">See also</span></span>

- [<span data-ttu-id="d1f3d-164">Présentation des ressources</span><span class="sxs-lookup"><span data-stu-id="d1f3d-164">What are Resources?</span></span>](../resources/resources.md)
