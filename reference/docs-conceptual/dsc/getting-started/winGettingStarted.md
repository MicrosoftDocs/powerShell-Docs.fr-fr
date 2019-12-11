---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Prendre en main la fonctionnalité DSC (Desired State Configuration) pour Windows
ms.openlocfilehash: a9346b96693acdbad9bacbd4b6ca85971e17a3d1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417766"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="8be9e-103">Prendre en main la fonctionnalité DSC (Desired State Configuration) pour Windows</span><span class="sxs-lookup"><span data-stu-id="8be9e-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="8be9e-104">Cette rubrique explique comment prendre en main la fonctionnalité DSC (Desired State Configuration) PowerShell pour Windows.</span><span class="sxs-lookup"><span data-stu-id="8be9e-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="8be9e-105">Pour obtenir des informations générales sur DSC, consultez [Prendre en main la fonctionnalité DSC (Desired State Configuration) Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="8be9e-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="8be9e-106">Versions du système d’exploitation Windows prises en charge</span><span class="sxs-lookup"><span data-stu-id="8be9e-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="8be9e-107">Les versions suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="8be9e-107">The following versions are supported:</span></span>

- <span data-ttu-id="8be9e-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="8be9e-108">Windows Server 2019</span></span>
- <span data-ttu-id="8be9e-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8be9e-109">Windows Server 2016</span></span>
- <span data-ttu-id="8be9e-110">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8be9e-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="8be9e-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8be9e-111">Windows Server 2012</span></span>
- <span data-ttu-id="8be9e-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="8be9e-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="8be9e-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8be9e-113">Windows 10</span></span>
- <span data-ttu-id="8be9e-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="8be9e-114">Windows 8.1</span></span>
- <span data-ttu-id="8be9e-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="8be9e-115">Windows 7</span></span>

<span data-ttu-id="8be9e-116">La référence SKU de produit autonome [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) ne contient pas d’implémentation de l’état de configuration souhaité, de sorte qu’elle ne peut pas être gérée par PowerShell DSC ni par la configuration de l’état Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="8be9e-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="8be9e-117">Installation de DSC</span><span class="sxs-lookup"><span data-stu-id="8be9e-117">Installing DSC</span></span>

<span data-ttu-id="8be9e-118">La fonctionnalité Desired State Configuration de PowerShell est incluse dans Windows et mise à jour par le biais de Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="8be9e-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="8be9e-119">La version la plus récente est [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="8be9e-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="8be9e-120">Vous n’avez pas besoin d’activer la fonctionnalité « DSC-Service » de Windows Server pour gérer un ordinateur à l’aide de DSC.</span><span class="sxs-lookup"><span data-stu-id="8be9e-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="8be9e-121">Cette fonctionnalité est uniquement nécessaire lors de la création d’une instance de serveur Pull Windows.</span><span class="sxs-lookup"><span data-stu-id="8be9e-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="8be9e-122">Utilisation de DSC pour Windows</span><span class="sxs-lookup"><span data-stu-id="8be9e-122">Using DSC for Windows</span></span>

<span data-ttu-id="8be9e-123">Les sections suivantes expliquent comment créer et exécuter des configurations DSC sur les ordinateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="8be9e-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="8be9e-124">Création d’un document MOF de configuration</span><span class="sxs-lookup"><span data-stu-id="8be9e-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="8be9e-125">Le mot clé Windows PowerShell « Configuration » permet de créer une configuration.</span><span class="sxs-lookup"><span data-stu-id="8be9e-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="8be9e-126">Suivez les étapes décrites ci-dessous pour créer un document de configuration à l’aide de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8be9e-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="8be9e-127">Définissez une configuration et créez le document de configuration :</span><span class="sxs-lookup"><span data-stu-id="8be9e-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="8be9e-128">Installer un module contenant des ressources DSC</span><span class="sxs-lookup"><span data-stu-id="8be9e-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="8be9e-129">La fonctionnalité Desired State Configuration de Windows PowerShell inclut des modules intégrés contenant des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="8be9e-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="8be9e-130">Vous pouvez également charger des modules à partir de sources externes, telles que PowerShell Gallery, à l’aide des cmdlets PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8be9e-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="8be9e-131">Appliquer la configuration à l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="8be9e-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="8be9e-132">La configuration de documents (fichiers MOF) peut être appliquée à l’ordinateur à l’aide de la cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="8be9e-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="8be9e-133">Obtient l’état actuel de la configuration</span><span class="sxs-lookup"><span data-stu-id="8be9e-133">Get the current state of the configuration</span></span>

<span data-ttu-id="8be9e-134">La cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) interroge l’état actuel de l’ordinateur et retourne les valeurs actuelles de la configuration.</span><span class="sxs-lookup"><span data-stu-id="8be9e-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="8be9e-135">La cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) retourne la méta-configuration actuelle appliquée à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8be9e-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="8be9e-136">Supprimer la configuration actuelle d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="8be9e-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="8be9e-137">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="8be9e-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="8be9e-138">Configurer les paramètres dans le Configuration Manager Manager local</span><span class="sxs-lookup"><span data-stu-id="8be9e-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="8be9e-139">Appliquez un fichier MOF de méta-configuration à l’ordinateur à l’aide de la cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="8be9e-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="8be9e-140">Doit spécifier le chemin du fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="8be9e-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="8be9e-141">Fichiers journaux de la fonctionnalité Desired State Configuration de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8be9e-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="8be9e-142">Les journaux pour DSC sont écrits dans le journal des événements Windows dans le chemin d’accès `Microsoft-Windows-Dsc/Operational`.</span><span class="sxs-lookup"><span data-stu-id="8be9e-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="8be9e-143">Des journaux supplémentaires à des fins de débogage peuvent être activés en suivant les étapes décrites dans [Où se trouvent les journaux des événements DSC](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="8be9e-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
