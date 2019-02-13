---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679364"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c73e7-103">Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c73e7-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c73e7-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="c73e7-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="c73e7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c73e7-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="c73e7-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c73e7-106">Parameters</span></span>

<span data-ttu-id="c73e7-107">*configurationNumber* \[in\] Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="c73e7-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c73e7-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c73e7-108">Return value</span></span>

<span data-ttu-id="c73e7-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c73e7-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c73e7-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="c73e7-110">Remarks</span></span>

<span data-ttu-id="c73e7-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="c73e7-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c73e7-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c73e7-112">Requirements</span></span>

<span data-ttu-id="c73e7-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c73e7-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c73e7-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c73e7-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c73e7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c73e7-115">See also</span></span>

[<span data-ttu-id="c73e7-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c73e7-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)