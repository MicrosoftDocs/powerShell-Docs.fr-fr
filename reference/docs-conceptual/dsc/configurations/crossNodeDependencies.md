---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Spécification de dépendances entre nœuds
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954106"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="e4cf8-103">Spécification de dépendances entre nœuds</span><span class="sxs-lookup"><span data-stu-id="e4cf8-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="e4cf8-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e4cf8-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e4cf8-105">DSC fournit des ressources spéciales, **WaitForAll**, **WaitForAny** et **WaitForSome**, qui peuvent être utilisées dans les configurations pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="e4cf8-106">Le comportement de ces ressources est le suivant :</span><span class="sxs-lookup"><span data-stu-id="e4cf8-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="e4cf8-107">**WaitForAll** : réussit si la ressource spécifiée est dans l’état souhaité sur tous les nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="e4cf8-108">**WaitForAny** : réussit si la ressource spécifiée est dans l’état souhaité sur au moins l’un des nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="e4cf8-109">**WaitForSome** : spécifie une propriété **NodeCount** en plus d’une propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="e4cf8-110">La ressource réussit si elle est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4cf8-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4cf8-111">Syntax</span></span>

<span data-ttu-id="e4cf8-112">Les ressources **WaitForAll** et **WaitForAny** partagent la même syntaxe.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="e4cf8-113">Remplacez \<ResourceType\> dans l’exemple ci-dessous par **WaitForAny** ou **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="e4cf8-114">Comme pour le mot clé **DependsOn**, vous devrez appliquer au nom le format "[ResourceType]ResourceName".</span><span class="sxs-lookup"><span data-stu-id="e4cf8-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="e4cf8-115">Si la ressource appartient à une [configuration](configurations.md) distincte, incluez **ConfigurationName** dans la chaîne mise en forme "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="e4cf8-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="e4cf8-116">**NodeName** représente l’ordinateur ou le nœud sur lequel la ressource actuelle doit attendre.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="e4cf8-117">La ressource **WaitForSome** affiche une syntaxe similaire à l’exemple ci-dessus, mais ajoute la clé **NodeCount**.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="e4cf8-118">**NodeCount** indique le nombre de nœuds sur lesquels la ressource actuelle doit attendre.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="e4cf8-119">Toutes les ressources **WaitForXXXX** partagent les clés de syntaxe suivantes.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="e4cf8-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="e4cf8-120">Property</span></span>|  <span data-ttu-id="e4cf8-121">Description</span><span class="sxs-lookup"><span data-stu-id="e4cf8-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="e4cf8-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="e4cf8-122">RetryIntervalSec</span></span>| <span data-ttu-id="e4cf8-123">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-123">The number of seconds before retrying.</span></span> <span data-ttu-id="e4cf8-124">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-124">Minimum is 1.</span></span>|
| <span data-ttu-id="e4cf8-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="e4cf8-125">RetryCount</span></span>| <span data-ttu-id="e4cf8-126">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="e4cf8-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e4cf8-127">ThrottleLimit</span></span>| <span data-ttu-id="e4cf8-128">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="e4cf8-129">La valeur par défaut est `New-CimSession` par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="e4cf8-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e4cf8-130">DependsOn</span></span> | <span data-ttu-id="e4cf8-131">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e4cf8-132">Pour plus d’informations, consultez [DependsOn](resource-depends-on.md).</span><span class="sxs-lookup"><span data-stu-id="e4cf8-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="e4cf8-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e4cf8-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="e4cf8-134">Voir [Exécution de DSC avec les informations d’identification de l’utilisateur](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="e4cf8-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="e4cf8-135">Utilisation de ressources WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="e4cf8-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="e4cf8-136">Chaque ressource **WaitForXXXX** attend que les ressources spécifiées soient terminées sur le nœud spécifié.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="e4cf8-137">Les autres ressources dans la même configuration peuvent ensuite *dépendre* de la ressource **WaitForXXXX** à l’aide de la clé **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="e4cf8-138">Par exemple, dans la configuration suivante, le nœud cible attend que la ressource **xADDomain** se termine sur le nœud **MyDC** avec un nombre maximal de 30 tentatives, à des intervalles de 15 secondes, avant que le nœud cible ne puisse joindre le domaine.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="e4cf8-139">Par défaut, les ressources **WaitForXXX** effectuent une tentative, puis échouent.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="e4cf8-140">Même si ce n’est pas obligatoire, vous spécifiez généralement les valeurs **RetryCount** et **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="e4cf8-141">Lorsque vous compilez la configuration, deux fichiers « .mof » sont générés.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="e4cf8-142">Appliquez ces deux fichiers « .mof » aux nœuds cibles à l’aide de l’applet de commande [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)</span><span class="sxs-lookup"><span data-stu-id="e4cf8-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="e4cf8-143">Les ressources **WaitForXXX** utilisent Windows Remote Management pour vérifier l’état d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="e4cf8-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="e4cf8-144">Pour plus d’informations sur la configuration requise des ports et de la sécurité pour WinRM, consultez [Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="e4cf8-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4cf8-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4cf8-145">See Also</span></span>

- [<span data-ttu-id="e4cf8-146">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="e4cf8-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="e4cf8-147">Utiliser des dépendances de ressources</span><span class="sxs-lookup"><span data-stu-id="e4cf8-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="e4cf8-148">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="e4cf8-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="e4cf8-149">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="e4cf8-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
