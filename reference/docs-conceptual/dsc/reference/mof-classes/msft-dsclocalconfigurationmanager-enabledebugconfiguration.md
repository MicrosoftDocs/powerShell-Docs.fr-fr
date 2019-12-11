---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration, méthode
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953436"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="f2054-103">EnableDebugConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="f2054-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="f2054-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="f2054-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2054-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2054-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="f2054-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2054-106">Parameters</span></span>

<span data-ttu-id="f2054-107">*BreakAll* \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="f2054-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="f2054-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f2054-108">Return value</span></span>

<span data-ttu-id="f2054-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f2054-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2054-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="f2054-110">Remarks</span></span>

<span data-ttu-id="f2054-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="f2054-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2054-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f2054-112">Requirements</span></span>

<span data-ttu-id="f2054-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f2054-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f2054-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2054-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f2054-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2054-115">See also</span></span>

[<span data-ttu-id="f2054-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f2054-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
