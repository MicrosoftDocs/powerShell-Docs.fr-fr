---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForAny
ms.openlocfilehash: 39e90f0df3459b8891ed46e02ae82c45a285e7f5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047319"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="bb92f-103">Ressource DSC WaitForAny</span><span class="sxs-lookup"><span data-stu-id="bb92f-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="bb92f-104">S'applique à : Windows PowerShell 5.1 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="bb92f-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="bb92f-105">La ressource de configuration d’état souhaité (DSC) **WaitForSome** peut être utilisée dans un bloc de nœud dans une [configuration DSC](../../../configurations/configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="bb92f-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="bb92f-106">La ressource réussit si la ressource spécifiée par la propriété **ResourceName** est dans l’état souhaité sur tous les nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="bb92f-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="bb92f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb92f-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="bb92f-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bb92f-108">Properties</span></span>

|  <span data-ttu-id="bb92f-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="bb92f-109">Property</span></span>  |  <span data-ttu-id="bb92f-110">Description</span><span class="sxs-lookup"><span data-stu-id="bb92f-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="bb92f-111">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="bb92f-111">ResourceName</span></span>| <span data-ttu-id="bb92f-112">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="bb92f-112">The resource name to depend on.</span></span> <span data-ttu-id="bb92f-113">Si cette ressource appartient à une configuration différente, mettez en forme le nom comme ceci : "[__type_ressource__]__nom_ressource__::[__nom_configuration__]::[__nom_configuration__]"</span><span class="sxs-lookup"><span data-stu-id="bb92f-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="bb92f-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="bb92f-114">NodeName</span></span>| <span data-ttu-id="bb92f-115">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="bb92f-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="bb92f-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="bb92f-116">RetryIntervalSec</span></span>| <span data-ttu-id="bb92f-117">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="bb92f-117">The number of seconds before retrying.</span></span> <span data-ttu-id="bb92f-118">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="bb92f-118">Minimum is 1.</span></span>|
| <span data-ttu-id="bb92f-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="bb92f-119">RetryCount</span></span>| <span data-ttu-id="bb92f-120">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="bb92f-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="bb92f-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="bb92f-121">ThrottleLimit</span></span>| <span data-ttu-id="bb92f-122">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="bb92f-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="bb92f-123">La valeur par défaut est new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="bb92f-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="bb92f-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bb92f-124">DependsOn</span></span> | <span data-ttu-id="bb92f-125">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="bb92f-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bb92f-126">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bb92f-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="bb92f-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb92f-127">Example</span></span>

<span data-ttu-id="bb92f-128">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="bb92f-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
