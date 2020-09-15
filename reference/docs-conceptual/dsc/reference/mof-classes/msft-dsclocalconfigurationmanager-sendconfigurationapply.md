---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: SendConfigurationApply, méthode
ms.openlocfilehash: 9b684790e5a7d6c7bdf074caca6040e13807f1ca
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464313"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="53099-103">SendConfigurationApply, méthode</span><span class="sxs-lookup"><span data-stu-id="53099-103">SendConfigurationApply method</span></span>

<span data-ttu-id="53099-104">Envoie le document de configuration au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="53099-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="53099-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53099-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="53099-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="53099-106">Parameters</span></span>

<span data-ttu-id="53099-107">**ConfigurationData** \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="53099-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="53099-108">**force** \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="53099-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="53099-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="53099-109">Return value</span></span>

<span data-ttu-id="53099-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="53099-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="53099-111">Notes</span><span class="sxs-lookup"><span data-stu-id="53099-111">Remarks</span></span>

<span data-ttu-id="53099-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="53099-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="53099-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="53099-113">Requirements</span></span>

<span data-ttu-id="53099-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="53099-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="53099-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="53099-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="53099-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53099-116">See also</span></span>

[<span data-ttu-id="53099-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="53099-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
