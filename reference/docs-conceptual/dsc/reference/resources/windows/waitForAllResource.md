---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForAll
ms.openlocfilehash: 1bdaa63812766cfe5ec0778ef07689109683b994
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953016"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="5d994-103">Ressource DSC WaitForAll</span><span class="sxs-lookup"><span data-stu-id="5d994-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="5d994-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="5d994-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="5d994-105">La ressource de configuration d’état souhaité (DSC) **WaitForAll** peut être utilisée dans un bloc de nœud dans une [configuration DSC](../../../configurations/configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="5d994-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="5d994-106">La ressource réussit si la ressource spécifiée par la propriété **ResourceName** est dans l’état souhaité sur tous les nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="5d994-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="5d994-107">La ressource **WaitForAll** utilise Windows Remote Management pour vérifier l’état d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="5d994-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="5d994-108">Pour plus d’informations sur la configuration requise des ports et de la sécurité pour WinRM, consultez [Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="5d994-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="5d994-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d994-109">Syntax</span></span>

```Syntax
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="5d994-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5d994-110">Properties</span></span>

|<span data-ttu-id="5d994-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="5d994-111">Property</span></span> |<span data-ttu-id="5d994-112">Description</span><span class="sxs-lookup"><span data-stu-id="5d994-112">Description</span></span> |
|---|---|
|<span data-ttu-id="5d994-113">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="5d994-113">ResourceName</span></span> |<span data-ttu-id="5d994-114">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="5d994-114">The resource name to depend on.</span></span> <span data-ttu-id="5d994-115">Si cette ressource appartient à une configuration différente, mettez le nom sous la forme `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="5d994-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="5d994-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="5d994-116">NodeName</span></span> |<span data-ttu-id="5d994-117">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="5d994-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="5d994-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="5d994-118">RetryIntervalSec</span></span> |<span data-ttu-id="5d994-119">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="5d994-119">The number of seconds before retrying.</span></span> <span data-ttu-id="5d994-120">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="5d994-120">Minimum is 1.</span></span> |
|<span data-ttu-id="5d994-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="5d994-121">RetryCount</span></span> |<span data-ttu-id="5d994-122">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="5d994-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="5d994-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="5d994-123">ThrottleLimit</span></span> |<span data-ttu-id="5d994-124">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="5d994-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="5d994-125">La valeur par défaut est `New-CimSession` par défaut.</span><span class="sxs-lookup"><span data-stu-id="5d994-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="5d994-126">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="5d994-126">Common properties</span></span>

|<span data-ttu-id="5d994-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="5d994-127">Property</span></span> |<span data-ttu-id="5d994-128">Description</span><span class="sxs-lookup"><span data-stu-id="5d994-128">Description</span></span> |
|---|---|
|<span data-ttu-id="5d994-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5d994-129">DependsOn</span></span> |<span data-ttu-id="5d994-130">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="5d994-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5d994-131">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5d994-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="5d994-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="5d994-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="5d994-133">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="5d994-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="5d994-134">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="5d994-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="5d994-135">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="5d994-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="5d994-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="5d994-136">Example</span></span>

<span data-ttu-id="5d994-137">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="5d994-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>