---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: TestConfiguration, méthode
ms.openlocfilehash: 0611c4d5543c49b879bef9b60cafdd0b055c9b86
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464296"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="9a33f-103">TestConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="9a33f-103">TestConfiguration method</span></span>

<span data-ttu-id="9a33f-104">Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.</span><span class="sxs-lookup"><span data-stu-id="9a33f-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a33f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a33f-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="9a33f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a33f-106">Parameters</span></span>

<span data-ttu-id="9a33f-107">**configurationData** \[in\] Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="9a33f-107">**configurationData** \[in\] Environment data for the configuration.</span></span>

<span data-ttu-id="9a33f-108">**InDesiredState** \[out\] En retour, indique si le nœud géré est dans l’état spécifié par le document de configuration.</span><span class="sxs-lookup"><span data-stu-id="9a33f-108">**InDesiredState** \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="9a33f-109">**ResourcesInDesiredState** \[out\] En retour, contient une instance incorporée de la classe **MSFT_ResourceInDesiredState** qui spécifie les ressources qui sont dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="9a33f-109">**ResourcesInDesiredState** \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="9a33f-110">**ResourcesNotInDesiredState** \[out\] En retour, contient une instance incorporée de la classe **MSFT_ResourceNotInDesiredState** qui spécifie les ressources qui ne sont pas dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="9a33f-110">**ResourcesNotInDesiredState** \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="9a33f-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="9a33f-111">Return value</span></span>

<span data-ttu-id="9a33f-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9a33f-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a33f-113">Notes</span><span class="sxs-lookup"><span data-stu-id="9a33f-113">Remarks</span></span>

<span data-ttu-id="9a33f-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="9a33f-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a33f-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9a33f-115">Requirements</span></span>

<span data-ttu-id="9a33f-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9a33f-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9a33f-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9a33f-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9a33f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a33f-118">See also</span></span>

[<span data-ttu-id="9a33f-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9a33f-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
