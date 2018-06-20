---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186692"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1fdcd-103">Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1fdcd-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1fdcd-104">Commence une vérification de cohérence à l’aide du Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="1fdcd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fdcd-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="1fdcd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1fdcd-106">Parameters</span></span>
----------

<span data-ttu-id="1fdcd-107">*Flags* \[in\] Masque de bits qui spécifie le type de vérification de cohérence à exécuter.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="1fdcd-108">Les valeurs suivantes sont valides et peuvent être combinées à l’aide d’une opération **OR** au niveau du bit :</span><span class="sxs-lookup"><span data-stu-id="1fdcd-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="1fdcd-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="1fdcd-109">Value</span></span> |<span data-ttu-id="1fdcd-110">Description</span><span class="sxs-lookup"><span data-stu-id="1fdcd-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="1fdcd-111">**1**</span><span class="sxs-lookup"><span data-stu-id="1fdcd-111">**1**</span></span> | <span data-ttu-id="1fdcd-112">Vérification de cohérence normale.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-112">A normal consistency check.</span></span> |
|<span data-ttu-id="1fdcd-113">**2**</span><span class="sxs-lookup"><span data-stu-id="1fdcd-113">**2**</span></span> | <span data-ttu-id="1fdcd-114">Poursuite d’une vérification de cohérence après un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="1fdcd-115">Cette valeur ne doit pas être combinée avec d’autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="1fdcd-116">**4**</span><span class="sxs-lookup"><span data-stu-id="1fdcd-116">**4**</span></span> | <span data-ttu-id="1fdcd-117">La configuration doit être extraite du serveur collecteur spécifié dans la métaconfiguration du nœud.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="1fdcd-118">Cette valeur doit toujours être combinée avec **1** avec une valeur de **5**.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="1fdcd-119">**8**</span><span class="sxs-lookup"><span data-stu-id="1fdcd-119">**8**</span></span> | <span data-ttu-id="1fdcd-120">Envoyez l’état au serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1fdcd-121">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1fdcd-121">Return value</span></span>
------------

<span data-ttu-id="1fdcd-122">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fdcd-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="1fdcd-123">Remarks</span></span>

<span data-ttu-id="1fdcd-124">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="1fdcd-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1fdcd-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1fdcd-125">Requirements</span></span>
------------
><span data-ttu-id="1fdcd-126">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1fdcd-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1fdcd-127">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1fdcd-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1fdcd-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fdcd-128">See also</span></span>


[<span data-ttu-id="1fdcd-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1fdcd-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)