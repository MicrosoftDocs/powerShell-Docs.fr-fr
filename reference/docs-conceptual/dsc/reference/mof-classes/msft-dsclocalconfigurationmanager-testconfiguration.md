---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: TestConfiguration, méthode
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954866"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="edf24-103">TestConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="edf24-103">TestConfiguration method</span></span>

<span data-ttu-id="edf24-104">Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.</span><span class="sxs-lookup"><span data-stu-id="edf24-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="edf24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edf24-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="edf24-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="edf24-106">Parameters</span></span>

<span data-ttu-id="edf24-107">*configurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="edf24-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="edf24-108">*InDesiredState* \[out\] En retour, indique si le nœud géré est dans l’état spécifié par le document de configuration.</span><span class="sxs-lookup"><span data-stu-id="edf24-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="edf24-109">*ResourcesInDesiredState* \[out\] En retour, contient une instance incorporée de la classe **MSFT_ResourceInDesiredState** qui spécifie les ressources qui sont dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="edf24-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="edf24-110">*ResourcesNotInDesiredState* \[out\] En retour, contient une instance incorporée de la classe **MSFT_ResourceNotInDesiredState** qui spécifie les ressources qui ne sont pas dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="edf24-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="edf24-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="edf24-111">Return value</span></span>

<span data-ttu-id="edf24-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="edf24-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="edf24-113">Notes</span><span class="sxs-lookup"><span data-stu-id="edf24-113">Remarks</span></span>

<span data-ttu-id="edf24-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="edf24-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="edf24-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="edf24-115">Requirements</span></span>

<span data-ttu-id="edf24-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="edf24-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="edf24-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="edf24-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="edf24-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edf24-118">See also</span></span>

[<span data-ttu-id="edf24-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="edf24-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
