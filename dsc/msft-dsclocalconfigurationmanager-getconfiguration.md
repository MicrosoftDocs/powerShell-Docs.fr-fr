---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892540"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8287c-103">Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8287c-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8287c-104">Envoie le document de configuration au nœud géré et utilise la méthode **Get** de l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="8287c-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="8287c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8287c-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="8287c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8287c-106">Parameters</span></span>

<span data-ttu-id="8287c-107">*configurationData* \[in\] Spécifie les données de configuration à envoyer.</span><span class="sxs-lookup"><span data-stu-id="8287c-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="8287c-108">*configurations* \[out\] En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="8287c-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="8287c-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8287c-109">Return value</span></span>

<span data-ttu-id="8287c-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8287c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8287c-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="8287c-111">Remarks</span></span>

<span data-ttu-id="8287c-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="8287c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8287c-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8287c-113">Requirements</span></span>

<span data-ttu-id="8287c-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8287c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8287c-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8287c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8287c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8287c-116">See also</span></span>

[<span data-ttu-id="8287c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8287c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)