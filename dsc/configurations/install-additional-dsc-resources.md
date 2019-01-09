---
ms.date: 12/12/2018
keywords: DSC, powershell, ressource, galerie, le programme d’installation
title: Installer des ressources DSC supplémentaires
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401695"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="69161-103">Installer des ressources DSC supplémentaires</span><span class="sxs-lookup"><span data-stu-id="69161-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="69161-104">PowerShell inclut plusieurs ressources Out-of-the-box pour Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="69161-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="69161-105">Le **PSDesiredStateConfiguration** module contient toutes les ressources OOB DSC disponibles sur votre instance spécifique de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69161-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="69161-106">Il s’agit d’une liste des ressources OOB incluses dans PowerShell 4.0 et une description des fonctionnalités de la ressource.</span><span class="sxs-lookup"><span data-stu-id="69161-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="69161-107">Il s’agit d’une liste incomplète, comme le nombre de ressources OOB a augmenté avec chaque version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69161-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="69161-108">Resource</span><span class="sxs-lookup"><span data-stu-id="69161-108">Resource</span></span>  |<span data-ttu-id="69161-109">Description</span><span class="sxs-lookup"><span data-stu-id="69161-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="69161-110">**File**</span><span class="sxs-lookup"><span data-stu-id="69161-110">**File**</span></span>|<span data-ttu-id="69161-111">Contrôle l’état des fichiers et répertoires.</span><span class="sxs-lookup"><span data-stu-id="69161-111">Controls the state of files and directories.</span></span> <span data-ttu-id="69161-112">Copie les fichiers à partir d’un **Source** à un **Destination** et les met à jour lorsque le **Source** modifications en comparant les dates, les sommes de contrôle et les hachages.</span><span class="sxs-lookup"><span data-stu-id="69161-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="69161-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="69161-113">**Archive**</span></span>|<span data-ttu-id="69161-114">Décompresse les archives et un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="69161-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="69161-115">Valide les archives avec un **somme de contrôle**.</span><span class="sxs-lookup"><span data-stu-id="69161-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="69161-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="69161-116">**Environment**</span></span>|<span data-ttu-id="69161-117">Gère les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="69161-117">Manages environment variables.</span></span>|
|<span data-ttu-id="69161-118">**Groupe**</span><span class="sxs-lookup"><span data-stu-id="69161-118">**Group**</span></span>|<span data-ttu-id="69161-119">Gère les groupes locaux et contrôle l’appartenance au groupe.</span><span class="sxs-lookup"><span data-stu-id="69161-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="69161-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="69161-120">**Log**</span></span>|<span data-ttu-id="69161-121">Écrit des messages à la `Microsoft-Windows-Desired State Configuration/Analytic` journal des événements.</span><span class="sxs-lookup"><span data-stu-id="69161-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="69161-122">**Package**</span><span class="sxs-lookup"><span data-stu-id="69161-122">**Package**</span></span>|<span data-ttu-id="69161-123">Installe ou désinstalle des packages à l’aide **Arguments**, **LogPath**, **ReturnCode**, autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="69161-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="69161-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="69161-124">**Registry**</span></span>|<span data-ttu-id="69161-125">Gère les valeurs et clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="69161-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="69161-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="69161-126">**Script**</span></span>|<span data-ttu-id="69161-127">Vous pouvez ainsi concevoir votre propre [get-test-set](../resources/get-test-set.md) blocs de script.</span><span class="sxs-lookup"><span data-stu-id="69161-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="69161-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="69161-128">**Service**</span></span>|<span data-ttu-id="69161-129">Configure les services Windows.</span><span class="sxs-lookup"><span data-stu-id="69161-129">Configures Windows services.</span></span>|
|<span data-ttu-id="69161-130">**User**</span><span class="sxs-lookup"><span data-stu-id="69161-130">**User**</span></span> |<span data-ttu-id="69161-131">Gère les attributs et les utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="69161-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="69161-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="69161-132">**WindowsFeature**</span></span>|<span data-ttu-id="69161-133">Gère les rôles et fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="69161-133">Manages roles and features.</span></span>|
|<span data-ttu-id="69161-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="69161-134">**WindowsProcess**</span></span>|<span data-ttu-id="69161-135">Configure les processus Windows.</span><span class="sxs-lookup"><span data-stu-id="69161-135">Configures Windows processes.</span></span>|

<span data-ttu-id="69161-136">Les ressources OOB autorisent un bon point de départ pour les opérations courantes.</span><span class="sxs-lookup"><span data-stu-id="69161-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="69161-137">Si les ressources prêtes à l’emploi ne répondent pas à vos besoins, vous pouvez écrire votre propre [ressource personnalisée](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="69161-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="69161-138">Avant d’écrire une ressource personnalisée pour résoudre votre problème, vous devriez rechercher via la multitude de ressources DSC qui ont déjà été créés par Microsoft et la Communauté PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69161-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="69161-139">Vous pouvez trouver les ressources DSC dans les deux le [PowerShell Gallery](https://www.powershellgallery.com/) et [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="69161-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="69161-140">Vous pouvez également installer les ressources DSC directement à partir de la console PowerShell à l’aide [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="69161-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="69161-141">Installation de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="69161-141">Installing PowerShellGet</span></span>

<span data-ttu-id="69161-142">Pour déterminer si vous avez déjà **PowerShell** obtenir, ou pour obtenir de l’aide de l’installer, consultez le guide suivant : [Installation de PowerShellGet](/powershell/gallery/installing-psget)</span><span class="sxs-lookup"><span data-stu-id="69161-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="69161-143">Recherche de ressources DSC à l’aide de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="69161-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="69161-144">Une fois **PowerShellGet** est installé sur votre système, vous pouvez rechercher et installer des ressources DSC hébergées dans le [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="69161-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="69161-145">Tout d’abord, utilisez le [Find-DSCResource](/powershell/module/powershellget/find-dscresource) applet de commande pour rechercher des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="69161-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="69161-146">Lorsque vous exécutez `Find-DSCResource` pour la première fois, vous voyez l’invite suivante pour installer le fournisseur « NuGet ».</span><span class="sxs-lookup"><span data-stu-id="69161-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

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

<span data-ttu-id="69161-147">Après en appuyant sur « y », le fournisseur « NuGet » est installé, vous voyez une liste de ressources DSC que vous pouvez installer à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="69161-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="69161-148">Liste n’est pas affichée, car il est très volumineux.</span><span class="sxs-lookup"><span data-stu-id="69161-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="69161-149">Vous pouvez également spécifier le `-Name` paramètre à l’aide des caractères génériques, ou `-Filter` paramètre sans caractères génériques pour limiter votre recherche.</span><span class="sxs-lookup"><span data-stu-id="69161-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="69161-150">Cet exemple tente de trouver une ressource de « Fuseau horaire » DSC en utilisant les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="69161-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69161-151">Actuellement, il existe un bogue dans le `Find-DSCResource` applet de commande qui empêche l’utilisation des caractères génériques dans les deux le `-Name` et `-Filter` paramètres.</span><span class="sxs-lookup"><span data-stu-id="69161-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="69161-152">Le deuxième exemple ci-dessous montre un à l’aide de la solution de contournement `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="69161-152">The second example below shows a workaround using `Where-Object`.</span></span>

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

<span data-ttu-id="69161-153">Vous pouvez également utiliser `Where-Object` pour rechercher des ressources DSC avec un filtrage plus précis.</span><span class="sxs-lookup"><span data-stu-id="69161-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="69161-154">Cette approche sera plus lente que la base de paramètres de filtrage.</span><span class="sxs-lookup"><span data-stu-id="69161-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="69161-155">Pour plus d’informations sur le filtrage, consultez [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="69161-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="69161-156">Installation des ressources DSC à l’aide de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="69161-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="69161-157">Pour installer une ressource DSC, utilisez le [Install-Module](/powershell/module/PowershellGet/Install-Module) applet de commande, en spécifiant le nom du module figurant sous **Module** nom dans vos résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="69161-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="69161-158">La ressource « Fuseau horaire » existe dans le module « ComputerManagementDSC », de sorte qu’il que le module de cet exemple installe.</span><span class="sxs-lookup"><span data-stu-id="69161-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="69161-159">Si vous n’avez pas approuvé la PowerShell gallery, vous voyez l’avertissement ci-dessous demander de confirmation, et qui vous indiquent comment éviter les invites suivantes sur installe.</span><span class="sxs-lookup"><span data-stu-id="69161-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="69161-160">Appuyez sur « y » pour continuer l’installation du module.</span><span class="sxs-lookup"><span data-stu-id="69161-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="69161-161">Après l’installation, vous pouvez vérifier que votre nouvelle ressource est installé à l’aide de [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="69161-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

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

<span data-ttu-id="69161-162">Vous pouvez également afficher les autres ressources dans votre module nouvellement installé, en spécifiant le `-ModuleName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="69161-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="69161-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69161-163">See also</span></span>

- [<span data-ttu-id="69161-164">Présentation des ressources</span><span class="sxs-lookup"><span data-stu-id="69161-164">What are Resources?</span></span>](../resources/resources.md)
