---
ms.date: 01/17/2019
keywords: dsc,powershell,configuration,installation
title: Redémarrer un nœud
description: De nombreux paramètres de configuration peuvent nécessiter le redémarrage de l’ordinateur pour finaliser la modification de la configuration. Cet article explique comment gérer les redémarrages dans une configuration.
ms.openlocfilehash: d2b0f77c34ebcb006821da1f4f8d7c4b046f7a95
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645119"
---
# <a name="reboot-a-node"></a><span data-ttu-id="b2aca-105">Redémarrer un nœud</span><span class="sxs-lookup"><span data-stu-id="b2aca-105">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="b2aca-106">Cette rubrique explique comment redémarrer un nœud.</span><span class="sxs-lookup"><span data-stu-id="b2aca-106">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="b2aca-107">Pour que le redémarrage réussisse, les paramètres **ActionAfterReboot** et **RebootNodeIfNeeded** du Gestionnaire de configuration local doivent être configurés correctement.</span><span class="sxs-lookup"><span data-stu-id="b2aca-107">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span> <span data-ttu-id="b2aca-108">Pour en savoir plus sur les paramètres du Gestionnaire de configuration local, consultez [Configurer le Gestionnaire de configuration local](../managing-nodes/metaConfig.md) ou [Configurer le Gestionnaire de configuration local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="b2aca-108">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="b2aca-109">Les nœuds peuvent être redémarrés à partir d’une ressource, à l’aide de l’indicateur `$global:DSCMachineStatus`.</span><span class="sxs-lookup"><span data-stu-id="b2aca-109">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="b2aca-110">L’affectation de la valeur `1` à cet indicateur dans la fonction `Set-TargetResource` force le Gestionnaire de configuration local à redémarrer le nœud juste après la méthode **Set** de la ressource actuelle.</span><span class="sxs-lookup"><span data-stu-id="b2aca-110">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="b2aca-111">Grâce à cet indicateur, la ressource **PendingReboot** dans le module de la ressource DSC [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) détecte si un redémarrage est en attente en dehors de DSC.</span><span class="sxs-lookup"><span data-stu-id="b2aca-111">Using this flag, the **PendingReboot** resource in the [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC Resource module detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="b2aca-112">Vos [configurations](configurations.md) peuvent effectuer des étapes qui nécessitent un redémarrage du nœud,</span><span class="sxs-lookup"><span data-stu-id="b2aca-112">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="b2aca-113">par exemple :</span><span class="sxs-lookup"><span data-stu-id="b2aca-113">This could include things such as:</span></span>

- <span data-ttu-id="b2aca-114">Mises à jour Windows</span><span class="sxs-lookup"><span data-stu-id="b2aca-114">Windows updates</span></span>
- <span data-ttu-id="b2aca-115">Installation de logiciel</span><span class="sxs-lookup"><span data-stu-id="b2aca-115">Software install</span></span>
- <span data-ttu-id="b2aca-116">Renommages de fichiers</span><span class="sxs-lookup"><span data-stu-id="b2aca-116">File renames</span></span>
- <span data-ttu-id="b2aca-117">Renommage d’ordinateur</span><span class="sxs-lookup"><span data-stu-id="b2aca-117">Computer rename</span></span>

<span data-ttu-id="b2aca-118">La ressource **PendingReboot** vérifie des emplacements d’ordinateurs spécifiques pour déterminer si un redémarrage est en attente.</span><span class="sxs-lookup"><span data-stu-id="b2aca-118">The **PendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="b2aca-119">Si le nœud nécessite un redémarrage en dehors de DSC, la ressource **PendingReboot** affecte la valeur `1` à l’indicateur `$global:DSCMachineStatus` pour forcer un redémarrage et résoudre la condition en attente.</span><span class="sxs-lookup"><span data-stu-id="b2aca-119">If the Node requires a reboot outside of DSC, the **PendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="b2aca-120">Toute ressource DSC peut forcer le Gestionnaire de configuration local à redémarrer le nœud en définissant cet indicateur dans la fonction `Set-TargetResource`.</span><span class="sxs-lookup"><span data-stu-id="b2aca-120">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="b2aca-121">Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="b2aca-121">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="b2aca-122">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2aca-122">Syntax</span></span>

```
PendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="b2aca-123">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b2aca-123">Properties</span></span>

| <span data-ttu-id="b2aca-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="b2aca-124">Property</span></span> | <span data-ttu-id="b2aca-125">Description</span><span class="sxs-lookup"><span data-stu-id="b2aca-125">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b2aca-126">Name</span><span class="sxs-lookup"><span data-stu-id="b2aca-126">Name</span></span>| <span data-ttu-id="b2aca-127">Paramètre obligatoire qui doit être unique pour chaque instance de la ressource au sein d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="b2aca-127">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="b2aca-128">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="b2aca-128">SkipComponentBasedServicing</span></span> | <span data-ttu-id="b2aca-129">Ignorer les redémarrages déclenchés par le composant des services à base de composants.</span><span class="sxs-lookup"><span data-stu-id="b2aca-129">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="b2aca-130">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="b2aca-130">SkipWindowsUpdate</span></span> | <span data-ttu-id="b2aca-131">Ignorer les redémarrages déclenchés par Windows Update.</span><span class="sxs-lookup"><span data-stu-id="b2aca-131">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="b2aca-132">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="b2aca-132">SkipPendingFileRename</span></span> | <span data-ttu-id="b2aca-133">Ignorer les redémarrages en attente dus à un renommage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b2aca-133">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="b2aca-134">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="b2aca-134">SkipCcmClientSDK</span></span> | <span data-ttu-id="b2aca-135">Ignorer les redémarrages déclenchés par le client ConfigMgr.</span><span class="sxs-lookup"><span data-stu-id="b2aca-135">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="b2aca-136">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="b2aca-136">SkipComputerRename</span></span> | <span data-ttu-id="b2aca-137">Ignorer les redémarrages déclenchés par un renommage d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b2aca-137">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="b2aca-138">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b2aca-138">PSDSCRunAsCredential</span></span> | <span data-ttu-id="b2aca-139">Prise en charge dans v5.</span><span class="sxs-lookup"><span data-stu-id="b2aca-139">Supported in v5.</span></span> <span data-ttu-id="b2aca-140">Exécute la ressource en tant que l’utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2aca-140">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="b2aca-141">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b2aca-141">DependsOn</span></span> | <span data-ttu-id="b2aca-142">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="b2aca-142">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b2aca-143">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType** , la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b2aca-143">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType** , the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="b2aca-144">Pour plus d’informations, consultez [Utilisation de DependsOn](resource-depends-on.md).</span><span class="sxs-lookup"><span data-stu-id="b2aca-144">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="b2aca-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2aca-145">Example</span></span>

<span data-ttu-id="b2aca-146">L’exemple suivant installe Microsoft Exchange à l’aide de la ressource [xExchange](https://github.com/PowerShell/xExchange).</span><span class="sxs-lookup"><span data-stu-id="b2aca-146">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span> <span data-ttu-id="b2aca-147">Tout au long de l’installation, la ressource **PendingReboot** est utilisée pour redémarrer le nœud.</span><span class="sxs-lookup"><span data-stu-id="b2aca-147">Throughout the install, the **PendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="b2aca-148">Cet exemple nécessite les informations d’identification d’un compte disposant des droits nécessaires pour ajouter un serveur Exchange à la forêt.</span><span class="sxs-lookup"><span data-stu-id="b2aca-148">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="b2aca-149">Pour plus d’informations sur l’utilisation des informations d’identification dans DSC, consultez [Gestion des informations d’identification dans DSC](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b2aca-149">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module ComputerManagementDsc

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        PendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="b2aca-150">Cet exemple part du principe que vous avez configuré votre Gestionnaire de configuration local de façon à autoriser les redémarrages et à poursuivre la configuration après un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="b2aca-150">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="b2aca-151">Emplacement de téléchargement</span><span class="sxs-lookup"><span data-stu-id="b2aca-151">Where to Download</span></span>

<span data-ttu-id="b2aca-152">Vous pouvez télécharger les ressources utilisées dans cette rubrique aux emplacements suivants, ou à l’aide de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b2aca-152">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="b2aca-153">ComputerManagementDsc</span><span class="sxs-lookup"><span data-stu-id="b2aca-153">ComputerManagementDsc</span></span>](https://github.com/PowerShell/ComputerManagementDsc)
- [<span data-ttu-id="b2aca-154">xExchange</span><span class="sxs-lookup"><span data-stu-id="b2aca-154">xExchange</span></span>](https://github.com/PowerShell/xExchange)
