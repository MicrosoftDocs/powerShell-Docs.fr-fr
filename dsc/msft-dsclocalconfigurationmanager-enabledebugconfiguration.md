---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e8ddc-103">Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e8ddc-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e8ddc-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="e8ddc-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="e8ddc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8ddc-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="e8ddc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8ddc-106">Parameters</span></span>
----------

<span data-ttu-id="e8ddc-107">*BreakAll* \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="e8ddc-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8ddc-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e8ddc-108">Return value</span></span>
------------

<span data-ttu-id="e8ddc-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e8ddc-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8ddc-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8ddc-110">Remarks</span></span>

<span data-ttu-id="e8ddc-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="e8ddc-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8ddc-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8ddc-112">Requirements</span></span>
------------
><span data-ttu-id="e8ddc-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e8ddc-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e8ddc-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e8ddc-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e8ddc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8ddc-115">See also</span></span>


[<span data-ttu-id="e8ddc-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e8ddc-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)