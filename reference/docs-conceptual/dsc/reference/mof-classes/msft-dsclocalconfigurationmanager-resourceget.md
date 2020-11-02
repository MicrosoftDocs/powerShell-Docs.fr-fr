---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceGet, méthode
description: ResourceGet, méthode
ms.openlocfilehash: bff737f04e02740fa09fd82d7b27c75b11303dad
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650752"
---
# <a name="resourceget-method"></a><span data-ttu-id="b8f21-103">ResourceGet, méthode</span><span class="sxs-lookup"><span data-stu-id="b8f21-103">ResourceGet method</span></span>

<span data-ttu-id="b8f21-104">Appelle directement la méthode **Get** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="b8f21-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8f21-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8f21-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="b8f21-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8f21-106">Parameters</span></span>

<span data-ttu-id="b8f21-107">**ResourceType** \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="b8f21-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="b8f21-108">**ModuleName** \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="b8f21-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b8f21-109">**resourceProperty** \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b8f21-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b8f21-110">Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="b8f21-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b8f21-111">**configurations** \[out\] En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="b8f21-111">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="b8f21-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b8f21-112">Return value</span></span>

<span data-ttu-id="b8f21-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b8f21-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8f21-114">Notes</span><span class="sxs-lookup"><span data-stu-id="b8f21-114">Remarks</span></span>

<span data-ttu-id="b8f21-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="b8f21-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8f21-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b8f21-116">Requirements</span></span>

<span data-ttu-id="b8f21-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b8f21-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b8f21-118">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8f21-118">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b8f21-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8f21-119">See also</span></span>

[<span data-ttu-id="b8f21-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b8f21-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
