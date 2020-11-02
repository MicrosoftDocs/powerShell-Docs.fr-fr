---
ms.date: 07/17/2020
ms.topic: reference
title: StopConfiguration, méthode
description: StopConfiguration, méthode
ms.openlocfilehash: 854c0dbe8554c08413735a5a7bc872776e0b0a6c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644627"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="29a19-103">StopConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="29a19-103">StopConfiguration method</span></span>

<span data-ttu-id="29a19-104">Arrête la modification de la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="29a19-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="29a19-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29a19-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="29a19-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29a19-106">Parameters</span></span>

<span data-ttu-id="29a19-107">**force** \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="29a19-107">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="29a19-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="29a19-108">Return value</span></span>

<span data-ttu-id="29a19-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="29a19-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="29a19-110">Notes</span><span class="sxs-lookup"><span data-stu-id="29a19-110">Remarks</span></span>

<span data-ttu-id="29a19-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="29a19-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="29a19-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="29a19-112">Requirements</span></span>

<span data-ttu-id="29a19-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="29a19-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="29a19-114">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="29a19-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="29a19-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29a19-115">See also</span></span>

[<span data-ttu-id="29a19-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="29a19-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
