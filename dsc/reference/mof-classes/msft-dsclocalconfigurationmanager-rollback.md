---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047379"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="49f88-103">Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="49f88-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="49f88-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="49f88-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="49f88-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49f88-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="49f88-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49f88-106">Parameters</span></span>

<span data-ttu-id="49f88-107">*configurationNumber* \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="49f88-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="49f88-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="49f88-108">Return value</span></span>

<span data-ttu-id="49f88-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="49f88-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="49f88-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="49f88-110">Remarks</span></span>

<span data-ttu-id="49f88-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="49f88-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="49f88-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="49f88-112">Requirements</span></span>

<span data-ttu-id="49f88-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="49f88-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="49f88-114">\*\*Espace de noms : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="49f88-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="49f88-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49f88-115">See also</span></span>

[<span data-ttu-id="49f88-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="49f88-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)