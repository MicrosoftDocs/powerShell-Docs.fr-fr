---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfiguration, méthode
description: GetConfiguration, méthode
ms.openlocfilehash: a49f810bd227142c8c3ae4de45f69450400e4e8c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650884"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="0df85-103">GetConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="0df85-103">GetConfiguration method</span></span>

<span data-ttu-id="0df85-104">Envoie le document de configuration au nœud géré et utilise la méthode **Get** de l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="0df85-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0df85-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0df85-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="0df85-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0df85-106">Parameters</span></span>

<span data-ttu-id="0df85-107">**configurationData** \[in\] Spécifie les données de configuration à envoyer.</span><span class="sxs-lookup"><span data-stu-id="0df85-107">**configurationData** \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="0df85-108">**configurations** \[out\] En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="0df85-108">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0df85-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="0df85-109">Return value</span></span>

<span data-ttu-id="0df85-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0df85-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0df85-111">Notes</span><span class="sxs-lookup"><span data-stu-id="0df85-111">Remarks</span></span>

<span data-ttu-id="0df85-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0df85-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0df85-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0df85-113">Requirements</span></span>

<span data-ttu-id="0df85-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0df85-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0df85-115">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0df85-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0df85-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0df85-116">See also</span></span>

[<span data-ttu-id="0df85-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0df85-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
