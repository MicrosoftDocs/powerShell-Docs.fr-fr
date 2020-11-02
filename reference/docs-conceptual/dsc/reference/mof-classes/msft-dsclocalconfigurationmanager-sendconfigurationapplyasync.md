---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApplyAsync, méthode
description: SendConfigurationApplyAsync, méthode
ms.openlocfilehash: 92c9d03a7653e72b1ff04084caea4a8b5aadb0e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644793"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="3164f-103">SendConfigurationApplyAsync, méthode</span><span class="sxs-lookup"><span data-stu-id="3164f-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="3164f-104">Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="3164f-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="3164f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3164f-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="3164f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3164f-106">Parameters</span></span>

<span data-ttu-id="3164f-107">**ConfigurationData** \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="3164f-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="3164f-108">**force** \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="3164f-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="3164f-109">**jobId** \[in\] ID du travail pour lequel envoyer la configuration.</span><span class="sxs-lookup"><span data-stu-id="3164f-109">**jobId** \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="3164f-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="3164f-110">Return value</span></span>

<span data-ttu-id="3164f-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3164f-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3164f-112">Notes</span><span class="sxs-lookup"><span data-stu-id="3164f-112">Remarks</span></span>

<span data-ttu-id="3164f-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="3164f-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3164f-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3164f-114">Requirements</span></span>

<span data-ttu-id="3164f-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3164f-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3164f-116">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3164f-116">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3164f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3164f-117">See also</span></span>

[<span data-ttu-id="3164f-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3164f-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
