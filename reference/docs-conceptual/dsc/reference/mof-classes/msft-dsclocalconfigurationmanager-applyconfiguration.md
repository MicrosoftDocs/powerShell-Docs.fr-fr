---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ApplyConfiguration, méthode
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953456"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="512d8-103">ApplyConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="512d8-103">ApplyConfiguration method</span></span>

<span data-ttu-id="512d8-104">Utilise l’agent de configuration pour appliquer la configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="512d8-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="512d8-105">S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="512d8-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="512d8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="512d8-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="512d8-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="512d8-107">Parameters</span></span>

<span data-ttu-id="512d8-108">*force* \[in\] Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="512d8-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="512d8-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="512d8-109">Return value</span></span>

<span data-ttu-id="512d8-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="512d8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="512d8-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="512d8-111">Remarks</span></span>

<span data-ttu-id="512d8-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="512d8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="512d8-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="512d8-113">Requirements</span></span>

<span data-ttu-id="512d8-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="512d8-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="512d8-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="512d8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="512d8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="512d8-116">See also</span></span>

[<span data-ttu-id="512d8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="512d8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
