---
ms.date: 01/17/2019
keywords: dsc,powershell,configuration,setup
title: Redémarrer un nœud
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954026"
---
# <a name="reboot-a-node"></a><span data-ttu-id="b4425-103">Redémarrer un nœud</span><span class="sxs-lookup"><span data-stu-id="b4425-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="b4425-104">Cette rubrique explique comment redémarrer un nœud.</span><span class="sxs-lookup"><span data-stu-id="b4425-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="b4425-105">Pour que le redémarrage réussisse, les paramètres **ActionAfterReboot** et **RebootNodeIfNeeded** du Gestionnaire de configuration local doivent être configurés correctement.</span><span class="sxs-lookup"><span data-stu-id="b4425-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="b4425-106">Pour en savoir plus sur les paramètres du Gestionnaire de configuration local, consultez [Configurer le Gestionnaire de configuration local](../managing-nodes/metaConfig.md) ou [Configurer le Gestionnaire de configuration local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="b4425-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="b4425-107">Les nœuds peuvent être redémarrés à partir d’une ressource, à l’aide de l’indicateur `$global:DSCMachineStatus`.</span><span class="sxs-lookup"><span data-stu-id="b4425-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="b4425-108">L’affectation de la valeur `1` à cet indicateur dans la fonction `Set-TargetResource` force le Gestionnaire de configuration local à redémarrer le nœud juste après la méthode **Set** de la ressource actuelle.</span><span class="sxs-lookup"><span data-stu-id="b4425-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="b4425-109">Grâce à cet indicateur, la ressource **PendingReboot** dans le module de la ressource DSC [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) détecte si un redémarrage est en attente en dehors de DSC.</span><span class="sxs-lookup"><span data-stu-id="b4425-109">Using this flag, the **PendingReboot** resource in the [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC Resource module detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="b4425-110">Vos [configurations](configurations.md) peuvent effectuer des étapes qui nécessitent un redémarrage du nœud,</span><span class="sxs-lookup"><span data-stu-id="b4425-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="b4425-111">par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4425-111">This could include things such as:</span></span>

- <span data-ttu-id="b4425-112">Mises à jour Windows</span><span class="sxs-lookup"><span data-stu-id="b4425-112">Windows updates</span></span>
- <span data-ttu-id="b4425-113">Installation de logiciel</span><span class="sxs-lookup"><span data-stu-id="b4425-113">Software install</span></span>
- <span data-ttu-id="b4425-114">Renommages de fichiers</span><span class="sxs-lookup"><span data-stu-id="b4425-114">File renames</span></span>
- <span data-ttu-id="b4425-115">Renommage d’ordinateur</span><span class="sxs-lookup"><span data-stu-id="b4425-115">Computer rename</span></span>

<span data-ttu-id="b4425-116">La ressource **PendingReboot** vérifie des emplacements d’ordinateurs spécifiques pour déterminer si un redémarrage est en attente.</span><span class="sxs-lookup"><span data-stu-id="b4425-116">The **PendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="b4425-117">Si le nœud nécessite un redémarrage en dehors de DSC, la ressource **PendingReboot** affecte la valeur `1` à l’indicateur `$global:DSCMachineStatus` pour forcer un redémarrage et résoudre la condition en attente.</span><span class="sxs-lookup"><span data-stu-id="b4425-117">If the Node requires a reboot outside of DSC, the **PendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="b4425-118">Toute ressource DSC peut forcer le Gestionnaire de configuration local à redémarrer le nœud en définissant cet indicateur dans la fonction `Set-TargetResource`.</span><span class="sxs-lookup"><span data-stu-id="b4425-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="b4425-119">Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="b4425-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="b4425-120">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4425-120">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="b4425-121">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b4425-121">Properties</span></span>

| <span data-ttu-id="b4425-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="b4425-122">Property</span></span> | <span data-ttu-id="b4425-123">Description</span><span class="sxs-lookup"><span data-stu-id="b4425-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b4425-124">Name</span><span class="sxs-lookup"><span data-stu-id="b4425-124">Name</span></span>| <span data-ttu-id="b4425-125">Paramètre obligatoire qui doit être unique pour chaque instance de la ressource au sein d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="b4425-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="b4425-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="b4425-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="b4425-127">Ignorer les redémarrages déclenchés par le composant des services à base de composants.</span><span class="sxs-lookup"><span data-stu-id="b4425-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="b4425-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="b4425-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="b4425-129">Ignorer les redémarrages déclenchés par Windows Update.</span><span class="sxs-lookup"><span data-stu-id="b4425-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="b4425-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="b4425-130">SkipPendingFileRename</span></span> | <span data-ttu-id="b4425-131">Ignorer les redémarrages en attente dus à un renommage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b4425-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="b4425-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="b4425-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="b4425-133">Ignorer les redémarrages déclenchés par le client ConfigMgr.</span><span class="sxs-lookup"><span data-stu-id="b4425-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="b4425-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="b4425-134">SkipComputerRename</span></span> | <span data-ttu-id="b4425-135">Ignorer les redémarrages déclenchés par un renommage d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b4425-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="b4425-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b4425-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="b4425-137">Prise en charge dans v5.</span><span class="sxs-lookup"><span data-stu-id="b4425-137">Supported in v5.</span></span> <span data-ttu-id="b4425-138">Exécute la ressource en tant que l’utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="b4425-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="b4425-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b4425-139">DependsOn</span></span> | <span data-ttu-id="b4425-140">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="b4425-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b4425-141">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b4425-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="b4425-142">Pour plus d’informations, consultez [Utilisation de DependsOn](resource-depends-on.md).</span><span class="sxs-lookup"><span data-stu-id="b4425-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="b4425-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="b4425-143">Example</span></span>

<span data-ttu-id="b4425-144">L’exemple suivant installe Microsoft Exchange à l’aide de la ressource [xExchange](https://github.com/PowerShell/xExchange).</span><span class="sxs-lookup"><span data-stu-id="b4425-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="b4425-145">Tout au long de l’installation, la ressource **PendingReboot** est utilisée pour redémarrer le nœud.</span><span class="sxs-lookup"><span data-stu-id="b4425-145">Throughout the install, the **PendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="b4425-146">Cet exemple nécessite les informations d’identification d’un compte disposant des droits nécessaires pour ajouter un serveur Exchange à la forêt.</span><span class="sxs-lookup"><span data-stu-id="b4425-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="b4425-147">Pour plus d’informations sur l’utilisation des informations d’identification dans DSC, consultez [Gestion des informations d’identification dans DSC](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b4425-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
> <span data-ttu-id="b4425-148">Cet exemple part du principe que vous avez configuré votre Gestionnaire de configuration local de façon à autoriser les redémarrages et à poursuivre la configuration après un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="b4425-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="b4425-149">Emplacement de téléchargement</span><span class="sxs-lookup"><span data-stu-id="b4425-149">Where to Download</span></span>

<span data-ttu-id="b4425-150">Vous pouvez télécharger les ressources utilisées dans cette rubrique aux emplacements suivants, ou à l’aide de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b4425-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="b4425-151">ComputerManagementDsc</span><span class="sxs-lookup"><span data-stu-id="b4425-151">ComputerManagementDsc</span></span>](https://github.com/PowerShell/ComputerManagementDsc)
- [<span data-ttu-id="b4425-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="b4425-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
