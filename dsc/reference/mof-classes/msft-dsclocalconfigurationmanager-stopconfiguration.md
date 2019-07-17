---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration, méthode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726985"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="66db2-103">StopConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="66db2-103">StopConfiguration method</span></span>

<span data-ttu-id="66db2-104">Arrête la modification de la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="66db2-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="66db2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66db2-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="66db2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66db2-106">Parameters</span></span>

<span data-ttu-id="66db2-107">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="66db2-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="66db2-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="66db2-108">Return value</span></span>

<span data-ttu-id="66db2-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="66db2-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="66db2-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="66db2-110">Remarks</span></span>

<span data-ttu-id="66db2-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="66db2-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="66db2-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="66db2-112">Requirements</span></span>

<span data-ttu-id="66db2-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="66db2-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="66db2-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="66db2-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="66db2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66db2-115">See also</span></span>

[<span data-ttu-id="66db2-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="66db2-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
