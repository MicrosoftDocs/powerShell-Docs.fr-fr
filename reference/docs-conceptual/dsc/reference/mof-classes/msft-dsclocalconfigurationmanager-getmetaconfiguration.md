---
ms.date: 07/17/2020
ms.topic: reference
title: GetMetaConfiguration, méthode
description: GetMetaConfiguration, méthode
ms.openlocfilehash: deca6b8ec342a34543bbe0e1fabbc2a740a88feb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644717"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="5066d-103">GetMetaConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="5066d-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="5066d-104">Obtenez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="5066d-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="5066d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5066d-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="5066d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5066d-106">Parameters</span></span>

<span data-ttu-id="5066d-107">**MetaConfiguration** \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCMetaConfiguration** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="5066d-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="5066d-108">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="5066d-108">Return value</span></span>

<span data-ttu-id="5066d-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5066d-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5066d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="5066d-110">Remarks</span></span>

<span data-ttu-id="5066d-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="5066d-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5066d-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5066d-112">Requirements</span></span>

<span data-ttu-id="5066d-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5066d-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5066d-114">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5066d-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5066d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5066d-115">See also</span></span>

[<span data-ttu-id="5066d-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5066d-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
