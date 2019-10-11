---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RollBack, méthode
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954936"
---
# <a name="rollback-method"></a><span data-ttu-id="bc91a-103">RollBack, méthode</span><span class="sxs-lookup"><span data-stu-id="bc91a-103">RollBack method</span></span>

<span data-ttu-id="bc91a-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="bc91a-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc91a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc91a-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="bc91a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bc91a-106">Parameters</span></span>

<span data-ttu-id="bc91a-107">*configurationNumber* \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="bc91a-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="bc91a-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bc91a-108">Return value</span></span>

<span data-ttu-id="bc91a-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bc91a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc91a-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="bc91a-110">Remarks</span></span>

<span data-ttu-id="bc91a-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="bc91a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bc91a-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bc91a-112">Requirements</span></span>

<span data-ttu-id="bc91a-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bc91a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bc91a-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bc91a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bc91a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc91a-115">See also</span></span>

[<span data-ttu-id="bc91a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bc91a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
