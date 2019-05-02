---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Spécification de dépendances entre nœuds
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080201"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="01635-103">Spécification de dépendances entre nœuds</span><span class="sxs-lookup"><span data-stu-id="01635-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="01635-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="01635-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="01635-105">DSC fournit des ressources spéciales, **WaitForAll**, **WaitForAny** et **WaitForSome**, qui peuvent être utilisées dans les configurations pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="01635-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="01635-106">Le comportement de ces ressources est le suivant :</span><span class="sxs-lookup"><span data-stu-id="01635-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="01635-107">**WaitForAll** : réussit si la ressource spécifiée est dans l’état souhaité sur tous les nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="01635-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="01635-108">**WaitForAny** : réussit si la ressource spécifiée est dans l’état souhaité sur au moins l’un des nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="01635-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="01635-109">**WaitForSome** : spécifie une propriété **NodeCount** en plus d’une propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="01635-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="01635-110">La ressource réussit si elle est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="01635-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="01635-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01635-111">Syntax</span></span>

<span data-ttu-id="01635-112">Les ressources **WaitForAll** et **WaitForAny** partagent la même syntaxe.</span><span class="sxs-lookup"><span data-stu-id="01635-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="01635-113">Remplacez \<ResourceType\> dans l’exemple ci-dessous par **WaitForAny** ou **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="01635-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="01635-114">Comme pour le mot clé **DependsOn**, vous devrez appliquer au nom le format "[ResourceType]ResourceName".</span><span class="sxs-lookup"><span data-stu-id="01635-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="01635-115">Si la ressource appartient à une [configuration](configurations.md) distincte, incluez **ConfigurationName** dans la chaîne mise en forme "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="01635-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="01635-116">**NodeName** représente l’ordinateur ou le nœud sur lequel la ressource actuelle doit attendre.</span><span class="sxs-lookup"><span data-stu-id="01635-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="01635-117">La ressource **WaitForSome** affiche une syntaxe similaire à l’exemple ci-dessus, mais ajoute la clé **NodeCount**.</span><span class="sxs-lookup"><span data-stu-id="01635-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="01635-118">**NodeCount** indique le nombre de nœuds sur lesquels la ressource actuelle doit attendre.</span><span class="sxs-lookup"><span data-stu-id="01635-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="01635-119">Toutes les ressources **WaitForXXXX** partagent les clés de syntaxe suivantes.</span><span class="sxs-lookup"><span data-stu-id="01635-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="01635-120">|  Propriété  |  Description   | | RetryIntervalSec| Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="01635-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="01635-121">La valeur minimale est 1.| | RetryCount|Le nombre maximum de nouvelles tentatives.| | ThrottleLimit| Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="01635-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="01635-122">La valeur par défaut est `New-CimSession`.| | DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="01635-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="01635-123">Pour plus d’informations, consultez [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | Voir [Utilisation de DSC avec des informations d’identification d’utilisateur](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="01635-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="01635-124">Utilisation de ressources WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="01635-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="01635-125">Chaque ressource **WaitForXXXX** attend que les ressources spécifiées soient terminées sur le nœud spécifié.</span><span class="sxs-lookup"><span data-stu-id="01635-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="01635-126">Les autres ressources dans la même configuration peuvent ensuite *dépendre* de la ressource **WaitForXXXX** à l’aide de la clé **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="01635-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="01635-127">Par exemple, dans la configuration suivante, le nœud cible attend que la ressource **xADDomain** se termine sur le nœud **MyDC** avec un nombre maximal de 30 tentatives, à des intervalles de 15 secondes, avant que le nœud cible ne puisse joindre le domaine.</span><span class="sxs-lookup"><span data-stu-id="01635-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="01635-128">Lorsque vous compilez la configuration, deux fichiers « .mof » sont générés.</span><span class="sxs-lookup"><span data-stu-id="01635-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="01635-129">Appliquez ces deux fichiers « .mof » aux nœuds cibles à l’aide de l’applet de commande [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)</span><span class="sxs-lookup"><span data-stu-id="01635-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="01635-130">**Remarque :** par défaut les ressources WaitForXXX effectuent une tentative, puis échouent.</span><span class="sxs-lookup"><span data-stu-id="01635-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="01635-131">Même si ce n’est pas obligatoire, vous spécifiez généralement les valeurs **RetryCount** et **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="01635-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="01635-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01635-132">See Also</span></span>

- [<span data-ttu-id="01635-133">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="01635-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="01635-134">Utiliser des dépendances de ressources</span><span class="sxs-lookup"><span data-stu-id="01635-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="01635-135">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="01635-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="01635-136">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="01635-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
