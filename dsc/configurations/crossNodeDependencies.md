---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Spécification de dépendances entre nœuds
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401162"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="63a46-103">Spécification de dépendances entre nœuds</span><span class="sxs-lookup"><span data-stu-id="63a46-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="63a46-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="63a46-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="63a46-105">DSC fournit des ressources spéciales, **WaitForAll**, **WaitForAny** et **WaitForSome**, qui peuvent être utilisées dans les configurations pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="63a46-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="63a46-106">Le comportement de ces ressources est le suivant :</span><span class="sxs-lookup"><span data-stu-id="63a46-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="63a46-107">**WaitForAll**: Réussit si la ressource spécifiée est dans l’état souhaité sur tous les nœuds cibles définis dans le **NodeName** propriété.</span><span class="sxs-lookup"><span data-stu-id="63a46-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="63a46-108">**WaitForAny**: Réussit si la ressource spécifiée est dans l’état souhaité sur au moins un des nœuds cibles définis dans le **NodeName** propriété.</span><span class="sxs-lookup"><span data-stu-id="63a46-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="63a46-109">**WaitForSome**: Spécifie un **NodeCount** propriété outre un **NodeName** propriété.</span><span class="sxs-lookup"><span data-stu-id="63a46-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="63a46-110">La ressource réussit si elle est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="63a46-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="63a46-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63a46-111">Syntax</span></span>

<span data-ttu-id="63a46-112">Le **WaitForAll** et **WaitForAny** ressources partagent la même syntaxe.</span><span class="sxs-lookup"><span data-stu-id="63a46-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="63a46-113">Remplacez \<ResourceType\> dans l’exemple ci-dessous, avec soit **WaitForAny** ou **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="63a46-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="63a46-114">Comme le **DependsOn** mot clé, vous devez mettre en forme le nom en tant que « [ResourceType] ResourceName ».</span><span class="sxs-lookup"><span data-stu-id="63a46-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="63a46-115">Si la ressource appartient à un distinct [Configuration](configurations.md), incluent le **ConfigurationName** dans la chaîne mise en forme « [ResourceType] ResourceName :: [ConfigurationName] :: [ConfigurationName] ».</span><span class="sxs-lookup"><span data-stu-id="63a46-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="63a46-116">Le **NodeName** est l’ordinateur ou le nœud, sur lequel la ressource actuelle doit attendre.</span><span class="sxs-lookup"><span data-stu-id="63a46-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="63a46-117">Le **WaitForSome** ressource a une syntaxe similaire à l’exemple ci-dessus, mais ajoute le **NodeCount** clé.</span><span class="sxs-lookup"><span data-stu-id="63a46-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="63a46-118">Le **NodeCount** indique le nombre de nœuds doit attendre la ressource actuelle.</span><span class="sxs-lookup"><span data-stu-id="63a46-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="63a46-119">Tous les **WaitForXXXX** partager les clés de syntaxe suivantes.</span><span class="sxs-lookup"><span data-stu-id="63a46-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="63a46-120">|  Propriété |  Description || RetryIntervalSec | Le nombre de secondes avant de réessayer.</span><span class="sxs-lookup"><span data-stu-id="63a46-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="63a46-121">Valeur minimale est 1. | | RetryCount | Le nombre maximal de tentatives. | | ThrottleLimit | Nombre d’ordinateurs à se connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="63a46-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="63a46-122">Valeur par défaut est `New-CimSession` par défaut. | | DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="63a46-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="63a46-123">Pour plus d’informations, consultez [DependsOn](resource-depends-on.md)|| PsDscRunAsCredential | Consultez [à l’aide de DSC avec les informations d’identification utilisateur](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="63a46-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="63a46-124">Utilisation de ressources WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="63a46-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="63a46-125">Chaque **WaitForXXXX** attentes de ressources pour les ressources spécifiées à effectuer sur le nœud spécifié.</span><span class="sxs-lookup"><span data-stu-id="63a46-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="63a46-126">Autres ressources dans la même Configuration peuvent ensuite *dépendent* le **WaitForXXXX** à l’aide de la ressource le **DependsOn** clé.</span><span class="sxs-lookup"><span data-stu-id="63a46-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="63a46-127">Par exemple, dans la configuration suivante, le nœud cible attend que la ressource **xADDomain** se termine sur le nœud **MyDC** avec un nombre maximal de 30 tentatives, à des intervalles de 15 secondes, avant que le nœud cible ne puisse joindre le domaine.</span><span class="sxs-lookup"><span data-stu-id="63a46-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="63a46-128">Lorsque vous compilez la Configuration, deux fichiers « .mof » sont générés.</span><span class="sxs-lookup"><span data-stu-id="63a46-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="63a46-129">Appliquer les deux fichiers « .mof » aux nœuds cibles à l’aide de la [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) applet de commande</span><span class="sxs-lookup"><span data-stu-id="63a46-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="63a46-130">**Remarque :** Par défaut la waitforxxx effectuent une tentative ressources essaient une seule fois, puis échouent.</span><span class="sxs-lookup"><span data-stu-id="63a46-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="63a46-131">Il n’est pas obligatoire, vous devez généralement spécifier un **RetryCount** et **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="63a46-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="63a46-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63a46-132">See Also</span></span>

- [<span data-ttu-id="63a46-133">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="63a46-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="63a46-134">Utiliser les dépendances de ressource</span><span class="sxs-lookup"><span data-stu-id="63a46-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="63a46-135">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="63a46-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="63a46-136">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="63a46-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
