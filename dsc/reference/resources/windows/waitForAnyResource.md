---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForAny
ms.openlocfilehash: d15acb3fb34d571eca56ed496eaa9a04b2551ff0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726857"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="56054-103">Ressource DSC WaitForAny</span><span class="sxs-lookup"><span data-stu-id="56054-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="56054-104">S’applique à : Windows PowerShell 5.1 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="56054-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="56054-105">La ressource de configuration d’état souhaité (DSC) **WaitForAny** peut être utilisée dans un bloc de nœud dans une [configuration DSC](../../../configurations/configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="56054-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="56054-106">La ressource réussit si la ressource spécifiée par la propriété **ResourceName** est dans l’état souhaité sur tous les nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="56054-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="56054-107">La ressource **WaitForAny** utilise Windows Remote Management pour vérifier l’état d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="56054-107">**WaitForAny** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="56054-108">Pour plus d’informations sur la configuration requise des ports et de la sécurité pour WinRM, consultez [Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="56054-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="56054-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56054-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="56054-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="56054-110">Properties</span></span>

|  <span data-ttu-id="56054-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="56054-111">Property</span></span>  |  <span data-ttu-id="56054-112">Description</span><span class="sxs-lookup"><span data-stu-id="56054-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="56054-113">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="56054-113">ResourceName</span></span>| <span data-ttu-id="56054-114">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="56054-114">The resource name to depend on.</span></span> <span data-ttu-id="56054-115">Si cette ressource appartient à une configuration différente, mettez en forme le nom comme ceci : "[__type_ressource__]__nom_ressource__::[__nom_configuration__]::[__nom_configuration__]"</span><span class="sxs-lookup"><span data-stu-id="56054-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="56054-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="56054-116">NodeName</span></span>| <span data-ttu-id="56054-117">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="56054-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="56054-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="56054-118">RetryIntervalSec</span></span>| <span data-ttu-id="56054-119">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="56054-119">The number of seconds before retrying.</span></span> <span data-ttu-id="56054-120">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="56054-120">Minimum is 1.</span></span>|
| <span data-ttu-id="56054-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="56054-121">RetryCount</span></span>| <span data-ttu-id="56054-122">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="56054-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="56054-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="56054-123">ThrottleLimit</span></span>| <span data-ttu-id="56054-124">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="56054-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="56054-125">La valeur par défaut est new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="56054-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="56054-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="56054-126">DependsOn</span></span> | <span data-ttu-id="56054-127">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="56054-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="56054-128">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="56054-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="56054-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="56054-129">Example</span></span>

<span data-ttu-id="56054-130">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="56054-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
