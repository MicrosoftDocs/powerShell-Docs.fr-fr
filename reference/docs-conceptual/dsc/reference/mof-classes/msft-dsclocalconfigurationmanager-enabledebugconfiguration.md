---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: EnableDebugConfiguration, méthode
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953436"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="b8854-103">EnableDebugConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="b8854-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="b8854-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="b8854-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8854-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8854-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="b8854-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8854-106">Parameters</span></span>

<span data-ttu-id="b8854-107">*BreakAll* \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="b8854-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="b8854-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b8854-108">Return value</span></span>

<span data-ttu-id="b8854-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b8854-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8854-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b8854-110">Remarks</span></span>

<span data-ttu-id="b8854-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="b8854-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8854-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b8854-112">Requirements</span></span>

<span data-ttu-id="b8854-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b8854-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b8854-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8854-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b8854-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8854-115">See also</span></span>

[<span data-ttu-id="b8854-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b8854-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
