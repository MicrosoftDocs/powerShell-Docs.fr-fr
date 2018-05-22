---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e002c-103">Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e002c-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e002c-104">Arrête la modification de la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="e002c-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="e002c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e002c-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="e002c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e002c-106">Parameters</span></span>
----------

<span data-ttu-id="e002c-107">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="e002c-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e002c-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e002c-108">Return value</span></span>
------------

<span data-ttu-id="e002c-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e002c-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e002c-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="e002c-110">Remarks</span></span>

<span data-ttu-id="e002c-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="e002c-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e002c-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e002c-112">Requirements</span></span>
------------
><span data-ttu-id="e002c-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e002c-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e002c-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e002c-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e002c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e002c-115">See also</span></span>


[<span data-ttu-id="e002c-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e002c-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)