---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: EnableDebugConfiguration, méthode
ms.openlocfilehash: be75b1012f49db79eb75a68c6912ffd5772bf16f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464092"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="85cb1-103">EnableDebugConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="85cb1-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="85cb1-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="85cb1-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="85cb1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85cb1-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="85cb1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85cb1-106">Parameters</span></span>

<span data-ttu-id="85cb1-107">**BreakAll** \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="85cb1-107">**BreakAll** \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="85cb1-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="85cb1-108">Return value</span></span>

<span data-ttu-id="85cb1-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="85cb1-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="85cb1-110">Notes</span><span class="sxs-lookup"><span data-stu-id="85cb1-110">Remarks</span></span>

<span data-ttu-id="85cb1-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="85cb1-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="85cb1-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="85cb1-112">Requirements</span></span>

<span data-ttu-id="85cb1-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="85cb1-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="85cb1-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="85cb1-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="85cb1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85cb1-115">See also</span></span>

[<span data-ttu-id="85cb1-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="85cb1-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
