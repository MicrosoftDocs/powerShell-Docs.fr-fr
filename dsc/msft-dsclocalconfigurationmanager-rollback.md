---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219876"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b35e3-103">Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b35e3-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b35e3-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="b35e3-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="b35e3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b35e3-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="b35e3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b35e3-106">Parameters</span></span>
----------

<span data-ttu-id="b35e3-107">*configurationNumber* \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="b35e3-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b35e3-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b35e3-108">Return value</span></span>
------------

<span data-ttu-id="b35e3-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b35e3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b35e3-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="b35e3-110">Remarks</span></span>

<span data-ttu-id="b35e3-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="b35e3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b35e3-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b35e3-112">Requirements</span></span>
------------
><span data-ttu-id="b35e3-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b35e3-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b35e3-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b35e3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b35e3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b35e3-115">See also</span></span>


[<span data-ttu-id="b35e3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b35e3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)