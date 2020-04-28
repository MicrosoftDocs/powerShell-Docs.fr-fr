---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: RollBack, méthode
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954936"
---
# <a name="rollback-method"></a><span data-ttu-id="f94bb-103">RollBack, méthode</span><span class="sxs-lookup"><span data-stu-id="f94bb-103">RollBack method</span></span>

<span data-ttu-id="f94bb-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="f94bb-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="f94bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f94bb-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="f94bb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f94bb-106">Parameters</span></span>

<span data-ttu-id="f94bb-107">*configurationNumber* \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="f94bb-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f94bb-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="f94bb-108">Return value</span></span>

<span data-ttu-id="f94bb-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f94bb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f94bb-110">Notes</span><span class="sxs-lookup"><span data-stu-id="f94bb-110">Remarks</span></span>

<span data-ttu-id="f94bb-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="f94bb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f94bb-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f94bb-112">Requirements</span></span>

<span data-ttu-id="f94bb-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f94bb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f94bb-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94bb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f94bb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f94bb-115">See also</span></span>

[<span data-ttu-id="f94bb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f94bb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
