---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678788"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e6386-103">Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e6386-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e6386-104">Envoie le document de configuration au nœud géré et utilise la méthode **Get** de l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="e6386-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6386-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6386-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="e6386-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6386-106">Parameters</span></span>

<span data-ttu-id="e6386-107">*configurationData* \[in\] Spécifie les données de configuration à envoyer.</span><span class="sxs-lookup"><span data-stu-id="e6386-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="e6386-108">*configurations* \[out\] En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="e6386-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="e6386-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e6386-109">Return value</span></span>

<span data-ttu-id="e6386-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e6386-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6386-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="e6386-111">Remarks</span></span>

<span data-ttu-id="e6386-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="e6386-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6386-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e6386-113">Requirements</span></span>

<span data-ttu-id="e6386-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e6386-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e6386-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6386-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e6386-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6386-116">See also</span></span>

[<span data-ttu-id="e6386-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e6386-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)