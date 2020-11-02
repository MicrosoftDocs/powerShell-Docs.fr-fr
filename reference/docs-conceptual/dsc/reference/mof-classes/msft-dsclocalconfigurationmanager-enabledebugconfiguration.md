---
ms.date: 07/17/2020
ms.topic: reference
title: EnableDebugConfiguration, méthode
description: EnableDebugConfiguration, méthode
ms.openlocfilehash: 536366e6e1627a249f3bc2dc19bfd8ff3de42117
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644779"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="18ad2-103">EnableDebugConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="18ad2-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="18ad2-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="18ad2-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="18ad2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18ad2-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="18ad2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18ad2-106">Parameters</span></span>

<span data-ttu-id="18ad2-107">**BreakAll** \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="18ad2-107">**BreakAll** \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="18ad2-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="18ad2-108">Return value</span></span>

<span data-ttu-id="18ad2-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="18ad2-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="18ad2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="18ad2-110">Remarks</span></span>

<span data-ttu-id="18ad2-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="18ad2-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="18ad2-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="18ad2-112">Requirements</span></span>

<span data-ttu-id="18ad2-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="18ad2-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="18ad2-114">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="18ad2-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="18ad2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18ad2-115">See also</span></span>

[<span data-ttu-id="18ad2-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="18ad2-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
