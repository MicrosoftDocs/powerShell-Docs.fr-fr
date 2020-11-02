---
ms.date: 07/17/2020
ms.topic: reference
title: RollBack, méthode
description: RollBack, méthode
ms.openlocfilehash: 82ca54ed23a3a892b785f603be3b423def5ee636
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650616"
---
# <a name="rollback-method"></a><span data-ttu-id="84611-103">RollBack, méthode</span><span class="sxs-lookup"><span data-stu-id="84611-103">RollBack method</span></span>

<span data-ttu-id="84611-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="84611-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="84611-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84611-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="84611-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="84611-106">Parameters</span></span>

<span data-ttu-id="84611-107">**configurationNumber** \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="84611-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="84611-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="84611-108">Return value</span></span>

<span data-ttu-id="84611-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="84611-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="84611-110">Notes</span><span class="sxs-lookup"><span data-stu-id="84611-110">Remarks</span></span>

<span data-ttu-id="84611-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="84611-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="84611-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="84611-112">Requirements</span></span>

<span data-ttu-id="84611-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="84611-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="84611-114">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="84611-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="84611-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84611-115">See also</span></span>

[<span data-ttu-id="84611-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="84611-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
