---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: ResourceGet, méthode
ms.openlocfilehash: aa7671989db6f4a98d879fd449d09503eddbeda3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463956"
---
# <a name="resourceget-method"></a><span data-ttu-id="7897f-103">ResourceGet, méthode</span><span class="sxs-lookup"><span data-stu-id="7897f-103">ResourceGet method</span></span>

<span data-ttu-id="7897f-104">Appelle directement la méthode **Get** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="7897f-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="7897f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7897f-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="7897f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7897f-106">Parameters</span></span>

<span data-ttu-id="7897f-107">**ResourceType** \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="7897f-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="7897f-108">**ModuleName** \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="7897f-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="7897f-109">**resourceProperty** \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="7897f-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="7897f-110">Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="7897f-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="7897f-111">**configurations** \[out\] En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="7897f-111">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="7897f-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7897f-112">Return value</span></span>

<span data-ttu-id="7897f-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7897f-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7897f-114">Notes</span><span class="sxs-lookup"><span data-stu-id="7897f-114">Remarks</span></span>

<span data-ttu-id="7897f-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="7897f-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7897f-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7897f-116">Requirements</span></span>

<span data-ttu-id="7897f-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7897f-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7897f-118">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7897f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7897f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7897f-119">See also</span></span>

[<span data-ttu-id="7897f-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7897f-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
