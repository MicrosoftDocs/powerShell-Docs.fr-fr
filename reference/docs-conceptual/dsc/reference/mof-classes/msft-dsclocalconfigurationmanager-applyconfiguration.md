---
ms.date: 07/14/2020
ms.topic: reference
title: ApplyConfiguration, méthode
description: ApplyConfiguration, méthode
ms.openlocfilehash: aa99221b33d39c3ecc70156a11eaee10b540e2dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664277"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="d2c80-103">ApplyConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="d2c80-103">ApplyConfiguration method</span></span>

<span data-ttu-id="d2c80-104">Utilise l’agent de configuration pour appliquer la configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="d2c80-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="d2c80-105">S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="d2c80-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2c80-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2c80-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d2c80-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2c80-107">Parameters</span></span>

### <a name="force"></a><span data-ttu-id="d2c80-108">force</span><span class="sxs-lookup"><span data-stu-id="d2c80-108">force</span></span>

<span data-ttu-id="d2c80-109">Si la valeur est **true** , la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="d2c80-109">If this is **true** , the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2c80-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="d2c80-110">Return value</span></span>

<span data-ttu-id="d2c80-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d2c80-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2c80-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="d2c80-112">Remarks</span></span>

<span data-ttu-id="d2c80-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="d2c80-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2c80-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2c80-114">Requirements</span></span>

<span data-ttu-id="d2c80-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d2c80-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d2c80-116">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2c80-116">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d2c80-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2c80-117">See also</span></span>

[<span data-ttu-id="d2c80-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d2c80-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
