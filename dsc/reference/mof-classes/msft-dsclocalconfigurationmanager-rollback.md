---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078365"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a7206-103">Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a7206-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a7206-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="a7206-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7206-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7206-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="a7206-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7206-106">Parameters</span></span>

<span data-ttu-id="a7206-107">*configurationNumber* \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="a7206-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a7206-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a7206-108">Return value</span></span>

<span data-ttu-id="a7206-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a7206-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7206-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="a7206-110">Remarks</span></span>

<span data-ttu-id="a7206-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="a7206-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7206-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a7206-112">Requirements</span></span>

<span data-ttu-id="a7206-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a7206-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a7206-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7206-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a7206-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7206-115">See also</span></span>

[<span data-ttu-id="a7206-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a7206-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)