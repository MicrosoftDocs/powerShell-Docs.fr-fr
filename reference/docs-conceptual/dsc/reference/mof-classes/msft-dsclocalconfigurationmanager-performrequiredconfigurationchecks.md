---
ms.date: 07/17/2020
ms.topic: reference
title: PerformRequiredConfigurationChecks, méthode
description: PerformRequiredConfigurationChecks, méthode
ms.openlocfilehash: c5e847cda6376f4266cc771dc947032a279e25f4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650826"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="114a9-103">PerformRequiredConfigurationChecks, méthode</span><span class="sxs-lookup"><span data-stu-id="114a9-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="114a9-104">Commence une vérification de cohérence à l’aide du Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="114a9-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="114a9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="114a9-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="114a9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="114a9-106">Parameters</span></span>

<span data-ttu-id="114a9-107">**Flags** \[in\] Masque de bits qui spécifie le type de vérification de cohérence à exécuter.</span><span class="sxs-lookup"><span data-stu-id="114a9-107">**Flags** \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="114a9-108">Les valeurs suivantes sont valides et peuvent être combinées à l’aide d’une opération **OR** au niveau du bit :</span><span class="sxs-lookup"><span data-stu-id="114a9-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="114a9-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="114a9-109">Value</span></span> |<span data-ttu-id="114a9-110">Description</span><span class="sxs-lookup"><span data-stu-id="114a9-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="114a9-111">**1**</span><span class="sxs-lookup"><span data-stu-id="114a9-111">**1**</span></span> | <span data-ttu-id="114a9-112">Vérification de cohérence normale.</span><span class="sxs-lookup"><span data-stu-id="114a9-112">A normal consistency check.</span></span> |
|<span data-ttu-id="114a9-113">**2**</span><span class="sxs-lookup"><span data-stu-id="114a9-113">**2**</span></span> | <span data-ttu-id="114a9-114">Poursuite d’une vérification de cohérence après un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="114a9-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="114a9-115">Cette valeur ne doit pas être combinée avec d’autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="114a9-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="114a9-116">**4**</span><span class="sxs-lookup"><span data-stu-id="114a9-116">**4**</span></span> | <span data-ttu-id="114a9-117">La configuration doit être extraite du serveur collecteur spécifié dans la métaconfiguration du nœud.</span><span class="sxs-lookup"><span data-stu-id="114a9-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="114a9-118">Cette valeur doit toujours être combinée avec **1** avec une valeur de **5** .</span><span class="sxs-lookup"><span data-stu-id="114a9-118">This value should always be combined with **1** , for a value of **5** .</span></span> |
|<span data-ttu-id="114a9-119">**8**</span><span class="sxs-lookup"><span data-stu-id="114a9-119">**8**</span></span> | <span data-ttu-id="114a9-120">Envoyez l’état au serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="114a9-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="114a9-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="114a9-121">Return value</span></span>

<span data-ttu-id="114a9-122">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="114a9-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="114a9-123">Notes</span><span class="sxs-lookup"><span data-stu-id="114a9-123">Remarks</span></span>

<span data-ttu-id="114a9-124">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="114a9-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="114a9-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="114a9-125">Requirements</span></span>

<span data-ttu-id="114a9-126">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="114a9-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="114a9-127">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="114a9-127">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="114a9-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="114a9-128">See also</span></span>

[<span data-ttu-id="114a9-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="114a9-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
