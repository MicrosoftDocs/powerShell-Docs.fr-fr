---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode SendConfigurationApply de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c578f4f52d3ea70e7bcf683ac204d6e484d4630d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0f8c8-103">Méthode SendConfigurationApply de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0f8c8-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0f8c8-104">Envoie le document de configuration au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="0f8c8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f8c8-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="0f8c8-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f8c8-106">Parameters</span></span>
----------

<span data-ttu-id="0f8c8-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="0f8c8-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0f8c8-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0f8c8-109">Return value</span></span>
------------

<span data-ttu-id="0f8c8-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f8c8-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="0f8c8-111">Remarks</span></span>

<span data-ttu-id="0f8c8-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f8c8-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0f8c8-113">Requirements</span></span>
------------
><span data-ttu-id="0f8c8-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0f8c8-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0f8c8-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f8c8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0f8c8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f8c8-116">See also</span></span>


[<span data-ttu-id="0f8c8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0f8c8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)