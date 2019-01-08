---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047250"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0a151-103">Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0a151-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0a151-104">Arrête la modification de la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="0a151-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a151-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a151-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="0a151-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a151-106">Parameters</span></span>

<span data-ttu-id="0a151-107">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="0a151-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a151-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0a151-108">Return value</span></span>

<span data-ttu-id="0a151-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0a151-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a151-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="0a151-110">Remarks</span></span>

<span data-ttu-id="0a151-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0a151-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a151-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0a151-112">Requirements</span></span>

<span data-ttu-id="0a151-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0a151-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0a151-114">\*\*Espace de noms : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0a151-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0a151-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a151-115">See also</span></span>

[<span data-ttu-id="0a151-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0a151-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)