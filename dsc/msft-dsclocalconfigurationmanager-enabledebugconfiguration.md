---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3e189-103">Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3e189-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3e189-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="3e189-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="3e189-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e189-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="3e189-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e189-106">Parameters</span></span>
----------

<span data-ttu-id="3e189-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3e189-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="3e189-108">Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="3e189-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="3e189-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3e189-109">Return value</span></span>
------------

<span data-ttu-id="3e189-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3e189-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e189-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="3e189-111">Remarks</span></span>

<span data-ttu-id="3e189-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="3e189-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e189-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e189-113">Requirements</span></span>
------------
><span data-ttu-id="3e189-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3e189-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3e189-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3e189-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3e189-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e189-116">See also</span></span>


[<span data-ttu-id="3e189-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3e189-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



