---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b4d4c901268344ba67d77e4dc982042bfc2abd78
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222205"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="75fe4-103">Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="75fe4-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="75fe4-104">Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.</span><span class="sxs-lookup"><span data-stu-id="75fe4-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="75fe4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75fe4-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="75fe4-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="75fe4-106">Parameters</span></span>
----------

<span data-ttu-id="75fe4-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="75fe4-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="75fe4-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="75fe4-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="75fe4-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="75fe4-109">Return value</span></span>
------------

<span data-ttu-id="75fe4-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="75fe4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="75fe4-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="75fe4-111">Remarks</span></span>

<span data-ttu-id="75fe4-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="75fe4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="75fe4-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="75fe4-113">Requirements</span></span>
------------
><span data-ttu-id="75fe4-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="75fe4-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="75fe4-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="75fe4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="75fe4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75fe4-116">See also</span></span>


[<span data-ttu-id="75fe4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="75fe4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)