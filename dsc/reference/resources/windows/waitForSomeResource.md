---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForSome
ms.openlocfilehash: 888da1810f0a9233579bad5eef8d5dd556947c61
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059454"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="0c46d-103">Ressource DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="0c46d-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="0c46d-104">S'applique à : Windows PowerShell 5.0 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="0c46d-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="0c46d-105">La ressource de configuration d’état souhaité (DSC) **WaitForSome** peut être utilisée dans un bloc de nœud dans une [configuration DSC](../../../configurations/configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="0c46d-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="0c46d-106">La ressource réussit si la ressource spécifiée dans la propriété **ResourceName** est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="0c46d-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="0c46d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c46d-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0c46d-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0c46d-108">Properties</span></span>

|  <span data-ttu-id="0c46d-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="0c46d-109">Property</span></span>  |  <span data-ttu-id="0c46d-110">Description</span><span class="sxs-lookup"><span data-stu-id="0c46d-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="0c46d-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="0c46d-111">NodeCount</span></span>| <span data-ttu-id="0c46d-112">Le nombre minimal de nœuds qui doivent être dans l’état souhaité pour que cette ressource réussisse.</span><span class="sxs-lookup"><span data-stu-id="0c46d-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="0c46d-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="0c46d-113">NodeName</span></span>| <span data-ttu-id="0c46d-114">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="0c46d-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="0c46d-115">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="0c46d-115">ResourceName</span></span>| <span data-ttu-id="0c46d-116">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="0c46d-116">The resource name to depend on.</span></span> <span data-ttu-id="0c46d-117">Si cette ressource appartient à une configuration différente, mettez en forme le nom comme ceci : "[__type_ressource__]__nom_ressource__::[__nom_configuration__]::[__nom_configuration__]"</span><span class="sxs-lookup"><span data-stu-id="0c46d-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="0c46d-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="0c46d-118">RetryIntervalSec</span></span>| <span data-ttu-id="0c46d-119">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="0c46d-119">The number of seconds before retrying.</span></span> <span data-ttu-id="0c46d-120">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="0c46d-120">Minimum is 1.</span></span>|
| <span data-ttu-id="0c46d-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="0c46d-121">RetryCount</span></span>| <span data-ttu-id="0c46d-122">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="0c46d-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="0c46d-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="0c46d-123">ThrottleLimit</span></span>| <span data-ttu-id="0c46d-124">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="0c46d-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="0c46d-125">La valeur par défaut est new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="0c46d-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="0c46d-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0c46d-126">DependsOn</span></span> | <span data-ttu-id="0c46d-127">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="0c46d-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0c46d-128">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0c46d-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="0c46d-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0c46d-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="0c46d-130">Voir [Exécution de DSC avec les informations d’identification de l’utilisateur](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="0c46d-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="0c46d-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c46d-131">Example</span></span>

<span data-ttu-id="0c46d-132">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="0c46d-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
