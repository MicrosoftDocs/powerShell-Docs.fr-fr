---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: StopConfiguration, méthode
ms.openlocfilehash: 76e50c98b09dca86983320918c6899082580672a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463701"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="a71b1-103">StopConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="a71b1-103">StopConfiguration method</span></span>

<span data-ttu-id="a71b1-104">Arrête la modification de la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="a71b1-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="a71b1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a71b1-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="a71b1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a71b1-106">Parameters</span></span>

<span data-ttu-id="a71b1-107">**force** \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="a71b1-107">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a71b1-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="a71b1-108">Return value</span></span>

<span data-ttu-id="a71b1-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a71b1-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a71b1-110">Notes</span><span class="sxs-lookup"><span data-stu-id="a71b1-110">Remarks</span></span>

<span data-ttu-id="a71b1-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="a71b1-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a71b1-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a71b1-112">Requirements</span></span>

<span data-ttu-id="a71b1-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a71b1-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a71b1-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a71b1-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a71b1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a71b1-115">See also</span></span>

[<span data-ttu-id="a71b1-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a71b1-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
