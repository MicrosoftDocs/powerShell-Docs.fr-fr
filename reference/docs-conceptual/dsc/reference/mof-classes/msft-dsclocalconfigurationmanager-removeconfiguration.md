---
ms.date: 07/17/2020
ms.topic: reference
title: RemoveConfiguration, méthode
description: RemoveConfiguration, méthode
ms.openlocfilehash: d5988ac014c457407c56a097c9a376427376eb3f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650726"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="08c47-103">RemoveConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="08c47-103">RemoveConfiguration method</span></span>

<span data-ttu-id="08c47-104">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="08c47-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="08c47-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08c47-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="08c47-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08c47-106">Parameters</span></span>

<span data-ttu-id="08c47-107">**Stage** \[in\] Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="08c47-107">**Stage** \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="08c47-108">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="08c47-108">The following values are valid:</span></span>

|<span data-ttu-id="08c47-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="08c47-109">Value</span></span> |<span data-ttu-id="08c47-110">Description</span><span class="sxs-lookup"><span data-stu-id="08c47-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="08c47-111">**1**</span><span class="sxs-lookup"><span data-stu-id="08c47-111">**1**</span></span> | <span data-ttu-id="08c47-112">Document de configuration **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="08c47-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="08c47-113">**2**</span><span class="sxs-lookup"><span data-stu-id="08c47-113">**2**</span></span> | <span data-ttu-id="08c47-114">Document de configuration **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="08c47-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="08c47-115">**4**</span><span class="sxs-lookup"><span data-stu-id="08c47-115">**4**</span></span> | <span data-ttu-id="08c47-116">Document de configuration **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="08c47-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="08c47-117">*Force* \[in\] **true** pour forcer la suppression de la configuration.</span><span class="sxs-lookup"><span data-stu-id="08c47-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="08c47-118">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="08c47-118">Return value</span></span>

<span data-ttu-id="08c47-119">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="08c47-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="08c47-120">Notes</span><span class="sxs-lookup"><span data-stu-id="08c47-120">Remarks</span></span>

<span data-ttu-id="08c47-121">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="08c47-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="08c47-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="08c47-122">Requirements</span></span>

<span data-ttu-id="08c47-123">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="08c47-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="08c47-124">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="08c47-124">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="08c47-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08c47-125">See also</span></span>

[<span data-ttu-id="08c47-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="08c47-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
