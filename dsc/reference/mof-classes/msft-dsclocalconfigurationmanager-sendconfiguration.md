---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfiguration, méthode
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734330"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="0fd26-103">SendConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="0fd26-103">SendConfiguration method</span></span>

<span data-ttu-id="0fd26-104">Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.</span><span class="sxs-lookup"><span data-stu-id="0fd26-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="0fd26-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fd26-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="0fd26-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0fd26-106">Parameters</span></span>

<span data-ttu-id="0fd26-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="0fd26-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="0fd26-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="0fd26-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0fd26-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0fd26-109">Return value</span></span>

<span data-ttu-id="0fd26-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0fd26-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0fd26-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="0fd26-111">Remarks</span></span>

<span data-ttu-id="0fd26-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0fd26-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0fd26-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0fd26-113">Requirements</span></span>

<span data-ttu-id="0fd26-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0fd26-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0fd26-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0fd26-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0fd26-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fd26-116">See also</span></span>

[<span data-ttu-id="0fd26-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0fd26-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
