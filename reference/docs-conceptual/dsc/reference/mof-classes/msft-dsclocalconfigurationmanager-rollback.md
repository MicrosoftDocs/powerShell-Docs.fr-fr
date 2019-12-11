---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RollBack, méthode
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954936"
---
# <a name="rollback-method"></a><span data-ttu-id="8c526-103">RollBack, méthode</span><span class="sxs-lookup"><span data-stu-id="8c526-103">RollBack method</span></span>

<span data-ttu-id="8c526-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="8c526-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c526-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c526-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="8c526-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c526-106">Parameters</span></span>

<span data-ttu-id="8c526-107">*configurationNumber* \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="8c526-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="8c526-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8c526-108">Return value</span></span>

<span data-ttu-id="8c526-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8c526-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c526-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="8c526-110">Remarks</span></span>

<span data-ttu-id="8c526-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="8c526-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c526-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8c526-112">Requirements</span></span>

<span data-ttu-id="8c526-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8c526-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8c526-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8c526-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8c526-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c526-115">See also</span></span>

[<span data-ttu-id="8c526-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8c526-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
