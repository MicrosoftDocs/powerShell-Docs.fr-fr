---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfiguration, méthode
description: SendConfiguration, méthode
ms.openlocfilehash: 3939a76ab6672b49559847b0ef1408f1c7be6d0c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650553"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="555da-103">SendConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="555da-103">SendConfiguration method</span></span>

<span data-ttu-id="555da-104">Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.</span><span class="sxs-lookup"><span data-stu-id="555da-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="555da-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="555da-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="555da-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="555da-106">Parameters</span></span>

<span data-ttu-id="555da-107">**ConfigurationData** \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="555da-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="555da-108">**force** \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="555da-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="555da-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="555da-109">Return value</span></span>

<span data-ttu-id="555da-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="555da-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="555da-111">Notes</span><span class="sxs-lookup"><span data-stu-id="555da-111">Remarks</span></span>

<span data-ttu-id="555da-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="555da-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="555da-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="555da-113">Requirements</span></span>

<span data-ttu-id="555da-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="555da-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="555da-115">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="555da-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="555da-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="555da-116">See also</span></span>

[<span data-ttu-id="555da-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="555da-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
