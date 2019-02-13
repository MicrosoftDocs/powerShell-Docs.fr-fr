---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678007"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6259f-103">Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6259f-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6259f-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="6259f-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="6259f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6259f-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="6259f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6259f-106">Parameters</span></span>

<span data-ttu-id="6259f-107">*BreakAll* \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="6259f-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="6259f-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6259f-108">Return value</span></span>

<span data-ttu-id="6259f-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6259f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6259f-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6259f-110">Remarks</span></span>

<span data-ttu-id="6259f-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="6259f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6259f-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6259f-112">Requirements</span></span>

<span data-ttu-id="6259f-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6259f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6259f-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6259f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6259f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6259f-115">See also</span></span>

[<span data-ttu-id="6259f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6259f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)