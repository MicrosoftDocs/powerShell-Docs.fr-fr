---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply, méthode
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727043"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="d3ac1-103">SendMetaConfigurationApply, méthode</span><span class="sxs-lookup"><span data-stu-id="d3ac1-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="d3ac1-104">Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="d3ac1-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3ac1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3ac1-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d3ac1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3ac1-106">Parameters</span></span>

<span data-ttu-id="d3ac1-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="d3ac1-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d3ac1-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="d3ac1-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d3ac1-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d3ac1-109">Return value</span></span>

<span data-ttu-id="d3ac1-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d3ac1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3ac1-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="d3ac1-111">Remarks</span></span>

<span data-ttu-id="d3ac1-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="d3ac1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3ac1-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d3ac1-113">Requirements</span></span>

<span data-ttu-id="d3ac1-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d3ac1-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d3ac1-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d3ac1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d3ac1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3ac1-116">See also</span></span>

[<span data-ttu-id="d3ac1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d3ac1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
