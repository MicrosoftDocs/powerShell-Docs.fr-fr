---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3fd52-103">Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3fd52-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3fd52-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="3fd52-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="3fd52-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fd52-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="3fd52-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3fd52-106">Parameters</span></span>
----------

<span data-ttu-id="3fd52-107">*configurationNumber* \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="3fd52-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="3fd52-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3fd52-108">Return value</span></span>
------------

<span data-ttu-id="3fd52-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3fd52-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3fd52-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="3fd52-110">Remarks</span></span>

<span data-ttu-id="3fd52-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="3fd52-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3fd52-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3fd52-112">Requirements</span></span>
------------
><span data-ttu-id="3fd52-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3fd52-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3fd52-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3fd52-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3fd52-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fd52-115">See also</span></span>


[<span data-ttu-id="3fd52-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3fd52-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)