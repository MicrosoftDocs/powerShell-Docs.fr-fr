---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApply, méthode
description: SendConfigurationApply, méthode
ms.openlocfilehash: 9bd63220644e096b348f71ee9d4ac216af6a7ccc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648972"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="86e58-103">SendConfigurationApply, méthode</span><span class="sxs-lookup"><span data-stu-id="86e58-103">SendConfigurationApply method</span></span>

<span data-ttu-id="86e58-104">Envoie le document de configuration au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="86e58-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="86e58-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86e58-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="86e58-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86e58-106">Parameters</span></span>

<span data-ttu-id="86e58-107">**ConfigurationData** \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="86e58-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="86e58-108">**force** \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="86e58-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="86e58-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="86e58-109">Return value</span></span>

<span data-ttu-id="86e58-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="86e58-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="86e58-111">Notes</span><span class="sxs-lookup"><span data-stu-id="86e58-111">Remarks</span></span>

<span data-ttu-id="86e58-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="86e58-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="86e58-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="86e58-113">Requirements</span></span>

<span data-ttu-id="86e58-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="86e58-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="86e58-115">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="86e58-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="86e58-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86e58-116">See also</span></span>

[<span data-ttu-id="86e58-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="86e58-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
