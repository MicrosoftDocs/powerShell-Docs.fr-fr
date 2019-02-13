---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679472"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fddaf-103">Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fddaf-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fddaf-104">Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="fddaf-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="fddaf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fddaf-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="fddaf-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fddaf-106">Parameters</span></span>

<span data-ttu-id="fddaf-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="fddaf-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fddaf-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="fddaf-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="fddaf-109">*jobId* \[in\] ID du travail pour lequel envoyer la configuration.</span><span class="sxs-lookup"><span data-stu-id="fddaf-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="fddaf-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="fddaf-110">Return value</span></span>

<span data-ttu-id="fddaf-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="fddaf-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fddaf-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="fddaf-112">Remarks</span></span>

<span data-ttu-id="fddaf-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="fddaf-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fddaf-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fddaf-114">Requirements</span></span>

<span data-ttu-id="fddaf-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fddaf-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fddaf-116">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fddaf-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fddaf-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fddaf-117">See also</span></span>

[<span data-ttu-id="fddaf-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fddaf-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)