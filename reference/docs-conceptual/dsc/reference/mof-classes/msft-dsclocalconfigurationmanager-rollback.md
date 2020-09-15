---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: RollBack, méthode
ms.openlocfilehash: 301b8926d2ebf1ebe524f52a67928d34e26d860e
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464330"
---
# <a name="rollback-method"></a><span data-ttu-id="0eebb-103">RollBack, méthode</span><span class="sxs-lookup"><span data-stu-id="0eebb-103">RollBack method</span></span>

<span data-ttu-id="0eebb-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="0eebb-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="0eebb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eebb-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="0eebb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0eebb-106">Parameters</span></span>

<span data-ttu-id="0eebb-107">**configurationNumber** \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="0eebb-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0eebb-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="0eebb-108">Return value</span></span>

<span data-ttu-id="0eebb-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0eebb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0eebb-110">Notes</span><span class="sxs-lookup"><span data-stu-id="0eebb-110">Remarks</span></span>

<span data-ttu-id="0eebb-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0eebb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0eebb-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0eebb-112">Requirements</span></span>

<span data-ttu-id="0eebb-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0eebb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0eebb-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0eebb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0eebb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eebb-115">See also</span></span>

[<span data-ttu-id="0eebb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0eebb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
