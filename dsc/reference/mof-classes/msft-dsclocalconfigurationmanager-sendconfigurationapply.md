---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode SendConfigurationApply de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047245"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="91a22-103">Méthode SendConfigurationApply de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="91a22-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="91a22-104">Envoie le document de configuration au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="91a22-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="91a22-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91a22-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="91a22-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91a22-106">Parameters</span></span>

<span data-ttu-id="91a22-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="91a22-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="91a22-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="91a22-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="91a22-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="91a22-109">Return value</span></span>

<span data-ttu-id="91a22-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="91a22-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="91a22-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="91a22-111">Remarks</span></span>

<span data-ttu-id="91a22-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="91a22-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="91a22-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="91a22-113">Requirements</span></span>

<span data-ttu-id="91a22-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="91a22-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="91a22-115">\*\*Espace de noms : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="91a22-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="91a22-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91a22-116">See also</span></span>

[<span data-ttu-id="91a22-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="91a22-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)