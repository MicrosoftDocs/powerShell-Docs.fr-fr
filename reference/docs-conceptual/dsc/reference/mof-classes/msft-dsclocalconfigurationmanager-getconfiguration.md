---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfiguration, méthode
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955046"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="bff24-103">GetConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="bff24-103">GetConfiguration method</span></span>

<span data-ttu-id="bff24-104">Envoie le document de configuration au nœud géré et utilise la méthode **Get** de l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="bff24-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="bff24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bff24-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="bff24-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bff24-106">Parameters</span></span>

<span data-ttu-id="bff24-107">*configurationData* \[in\] Spécifie les données de configuration à envoyer.</span><span class="sxs-lookup"><span data-stu-id="bff24-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="bff24-108">*configurations* \[out\] En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="bff24-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="bff24-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bff24-109">Return value</span></span>

<span data-ttu-id="bff24-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bff24-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bff24-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="bff24-111">Remarks</span></span>

<span data-ttu-id="bff24-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="bff24-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bff24-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bff24-113">Requirements</span></span>

<span data-ttu-id="bff24-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bff24-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bff24-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bff24-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bff24-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bff24-116">See also</span></span>

[<span data-ttu-id="bff24-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bff24-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
