---
ms.date: 07/16/2020
ms.topic: reference
title: Ressource DSC WaitForSome
description: Ressource DSC WaitForSome
ms.openlocfilehash: bc9c3df2b476e7046ccfe6257acc1d1641e7594b
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143090"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="a5a36-103">Ressource DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="a5a36-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="a5a36-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a5a36-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="a5a36-105">La ressource de configuration d’état souhaité (DSC) **WaitForSome** peut être utilisée dans un bloc de nœud dans une [configuration DSC](../../../configurations/configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="a5a36-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

<span data-ttu-id="a5a36-106">La ressource réussit si la ressource spécifiée dans la propriété **ResourceName** est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount** ) défini par la propriété **NodeName** .</span><span class="sxs-lookup"><span data-stu-id="a5a36-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount** ) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="a5a36-107">La ressource **WaitForSome** utilise Windows Remote Management pour vérifier l’état d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="a5a36-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="a5a36-108">Pour plus d’informations sur la configuration requise des ports et de la sécurité pour WinRM, consultez [Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="a5a36-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

## <a name="syntax"></a><span data-ttu-id="a5a36-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5a36-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="a5a36-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a5a36-110">Properties</span></span>

|<span data-ttu-id="a5a36-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="a5a36-111">Property</span></span> |<span data-ttu-id="a5a36-112">Description</span><span class="sxs-lookup"><span data-stu-id="a5a36-112">Description</span></span> |
|---|---|
|<span data-ttu-id="a5a36-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="a5a36-113">NodeCount</span></span> |<span data-ttu-id="a5a36-114">Le nombre minimal de nœuds qui doivent être dans l’état souhaité pour que cette ressource réussisse.</span><span class="sxs-lookup"><span data-stu-id="a5a36-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="a5a36-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="a5a36-115">NodeName</span></span> |<span data-ttu-id="a5a36-116">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="a5a36-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="a5a36-117">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="a5a36-117">ResourceName</span></span> |<span data-ttu-id="a5a36-118">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="a5a36-118">The resource name to depend on.</span></span> <span data-ttu-id="a5a36-119">Si cette ressource appartient à une configuration différente, mettez le nom sous la forme `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="a5a36-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="a5a36-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a5a36-120">RetryIntervalSec</span></span> |<span data-ttu-id="a5a36-121">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="a5a36-121">The number of seconds before retrying.</span></span> <span data-ttu-id="a5a36-122">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="a5a36-122">Minimum is 1.</span></span> |
|<span data-ttu-id="a5a36-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="a5a36-123">RetryCount</span></span> |<span data-ttu-id="a5a36-124">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="a5a36-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="a5a36-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a5a36-125">ThrottleLimit</span></span> |<span data-ttu-id="a5a36-126">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="a5a36-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a5a36-127">La valeur par défaut est `New-CimSession` par défaut.</span><span class="sxs-lookup"><span data-stu-id="a5a36-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a5a36-128">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="a5a36-128">Common properties</span></span>

|<span data-ttu-id="a5a36-129">Propriété</span><span class="sxs-lookup"><span data-stu-id="a5a36-129">Property</span></span> |<span data-ttu-id="a5a36-130">Description</span><span class="sxs-lookup"><span data-stu-id="a5a36-130">Description</span></span> |
|---|---|
|<span data-ttu-id="a5a36-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a5a36-131">DependsOn</span></span> |<span data-ttu-id="a5a36-132">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="a5a36-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a5a36-133">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a5a36-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="a5a36-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a5a36-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="a5a36-135">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="a5a36-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="a5a36-136">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a5a36-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="a5a36-137">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="a5a36-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5a36-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5a36-138">Example</span></span>

<span data-ttu-id="a5a36-139">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a5a36-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
