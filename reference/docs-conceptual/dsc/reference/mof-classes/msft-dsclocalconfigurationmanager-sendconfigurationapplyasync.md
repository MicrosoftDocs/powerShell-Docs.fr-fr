---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApplyAsync, méthode
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953376"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="bdd40-103">SendConfigurationApplyAsync, méthode</span><span class="sxs-lookup"><span data-stu-id="bdd40-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="bdd40-104">Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="bdd40-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="bdd40-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdd40-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="bdd40-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdd40-106">Parameters</span></span>

<span data-ttu-id="bdd40-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="bdd40-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="bdd40-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="bdd40-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="bdd40-109">*jobId* \[in\] ID du travail pour lequel envoyer la configuration.</span><span class="sxs-lookup"><span data-stu-id="bdd40-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="bdd40-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bdd40-110">Return value</span></span>

<span data-ttu-id="bdd40-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bdd40-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bdd40-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="bdd40-112">Remarks</span></span>

<span data-ttu-id="bdd40-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="bdd40-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bdd40-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bdd40-114">Requirements</span></span>

<span data-ttu-id="bdd40-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bdd40-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bdd40-116">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bdd40-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bdd40-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdd40-117">See also</span></span>

[<span data-ttu-id="bdd40-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bdd40-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)