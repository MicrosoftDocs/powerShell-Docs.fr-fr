---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078309"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c5c61-103">Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c5c61-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c5c61-104">Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="c5c61-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5c61-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5c61-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c5c61-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5c61-106">Parameters</span></span>

<span data-ttu-id="c5c61-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="c5c61-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="c5c61-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="c5c61-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c5c61-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c5c61-109">Return value</span></span>

<span data-ttu-id="c5c61-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c5c61-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5c61-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5c61-111">Remarks</span></span>

<span data-ttu-id="c5c61-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="c5c61-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5c61-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c5c61-113">Requirements</span></span>

<span data-ttu-id="c5c61-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c5c61-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c5c61-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c5c61-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c5c61-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5c61-116">See also</span></span>

[<span data-ttu-id="c5c61-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c5c61-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)