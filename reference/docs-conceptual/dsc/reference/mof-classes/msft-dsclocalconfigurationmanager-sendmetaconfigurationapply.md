---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: SendMetaConfigurationApply, méthode
ms.openlocfilehash: 896afe2f3370e108b48583aafb33ee7b0eb1301b
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463718"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="e827c-103">SendMetaConfigurationApply, méthode</span><span class="sxs-lookup"><span data-stu-id="e827c-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="e827c-104">Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="e827c-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="e827c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e827c-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e827c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e827c-106">Parameters</span></span>

<span data-ttu-id="e827c-107">**ConfigurationData** \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="e827c-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="e827c-108">**force** \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="e827c-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e827c-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="e827c-109">Return value</span></span>

<span data-ttu-id="e827c-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e827c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e827c-111">Notes</span><span class="sxs-lookup"><span data-stu-id="e827c-111">Remarks</span></span>

<span data-ttu-id="e827c-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="e827c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e827c-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e827c-113">Requirements</span></span>

<span data-ttu-id="e827c-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e827c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e827c-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e827c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e827c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e827c-116">See also</span></span>

[<span data-ttu-id="e827c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e827c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
