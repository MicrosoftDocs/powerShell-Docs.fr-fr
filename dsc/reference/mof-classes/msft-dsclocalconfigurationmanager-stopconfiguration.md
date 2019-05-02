---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078235"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="18b24-103">Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="18b24-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="18b24-104">Arrête la modification de la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="18b24-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="18b24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18b24-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="18b24-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18b24-106">Parameters</span></span>

<span data-ttu-id="18b24-107">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="18b24-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="18b24-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="18b24-108">Return value</span></span>

<span data-ttu-id="18b24-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="18b24-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="18b24-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="18b24-110">Remarks</span></span>

<span data-ttu-id="18b24-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="18b24-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="18b24-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="18b24-112">Requirements</span></span>

<span data-ttu-id="18b24-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="18b24-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="18b24-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="18b24-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="18b24-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18b24-115">See also</span></span>

[<span data-ttu-id="18b24-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="18b24-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)