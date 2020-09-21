---
ms.date: 07/14/2020
keywords: dsc,powershell,configuration,installation
title: ApplyConfiguration, méthode
ms.openlocfilehash: bec74ccd6f75448484adfd26bf8a4af4e224eb3f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463837"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="452ff-103">ApplyConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="452ff-103">ApplyConfiguration method</span></span>

<span data-ttu-id="452ff-104">Utilise l’agent de configuration pour appliquer la configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="452ff-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="452ff-105">S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="452ff-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="452ff-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="452ff-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="452ff-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="452ff-107">Parameters</span></span>

### <a name="force"></a><span data-ttu-id="452ff-108">force</span><span class="sxs-lookup"><span data-stu-id="452ff-108">force</span></span>

<span data-ttu-id="452ff-109">Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="452ff-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="452ff-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="452ff-110">Return value</span></span>

<span data-ttu-id="452ff-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="452ff-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="452ff-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="452ff-112">Remarks</span></span>

<span data-ttu-id="452ff-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="452ff-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="452ff-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="452ff-114">Requirements</span></span>

<span data-ttu-id="452ff-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="452ff-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="452ff-116">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="452ff-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="452ff-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="452ff-117">See also</span></span>

[<span data-ttu-id="452ff-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="452ff-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
