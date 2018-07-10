---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892397"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="95f28-103">Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="95f28-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="95f28-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="95f28-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="95f28-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95f28-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="95f28-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95f28-106">Parameters</span></span>

<span data-ttu-id="95f28-107">*BreakAll* \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="95f28-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="95f28-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="95f28-108">Return value</span></span>

<span data-ttu-id="95f28-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="95f28-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="95f28-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="95f28-110">Remarks</span></span>

<span data-ttu-id="95f28-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="95f28-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="95f28-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="95f28-112">Requirements</span></span>

<span data-ttu-id="95f28-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="95f28-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="95f28-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="95f28-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="95f28-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95f28-115">See also</span></span>

[<span data-ttu-id="95f28-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="95f28-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)