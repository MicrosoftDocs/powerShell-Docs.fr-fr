---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218839"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ba9b3-103">Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ba9b3-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ba9b3-104">Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="ba9b3-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="ba9b3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba9b3-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ba9b3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba9b3-106">Parameters</span></span>
----------

<span data-ttu-id="ba9b3-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="ba9b3-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ba9b3-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="ba9b3-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ba9b3-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ba9b3-109">Return value</span></span>
------------

<span data-ttu-id="ba9b3-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ba9b3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba9b3-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="ba9b3-111">Remarks</span></span>

<span data-ttu-id="ba9b3-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="ba9b3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba9b3-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ba9b3-113">Requirements</span></span>
------------
><span data-ttu-id="ba9b3-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ba9b3-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ba9b3-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba9b3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ba9b3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba9b3-116">See also</span></span>


[<span data-ttu-id="ba9b3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ba9b3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)