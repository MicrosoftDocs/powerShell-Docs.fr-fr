---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceSet, méthode
description: ResourceSet, méthode
ms.openlocfilehash: 2554ff5805d7ed9518bd283565dc879a0fdfdfd0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650697"
---
# <a name="resourceset-method"></a><span data-ttu-id="cf0b9-103">ResourceSet, méthode</span><span class="sxs-lookup"><span data-stu-id="cf0b9-103">ResourceSet method</span></span>

<span data-ttu-id="cf0b9-104">Appelle directement la méthode **Set** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="cf0b9-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf0b9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf0b9-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="cf0b9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf0b9-106">Parameters</span></span>

<span data-ttu-id="cf0b9-107">**ResourceType** \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="cf0b9-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="cf0b9-108">**ModuleName** \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="cf0b9-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="cf0b9-109">**resourceProperty** \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="cf0b9-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="cf0b9-110">Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="cf0b9-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="cf0b9-111">**RebootRequired** \[out\] En retour, cette propriété prend la valeur **true** si le nœud cible doit être redémarré.</span><span class="sxs-lookup"><span data-stu-id="cf0b9-111">**RebootRequired** \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="cf0b9-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="cf0b9-112">Return value</span></span>

<span data-ttu-id="cf0b9-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="cf0b9-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf0b9-114">Notes</span><span class="sxs-lookup"><span data-stu-id="cf0b9-114">Remarks</span></span>

<span data-ttu-id="cf0b9-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="cf0b9-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cf0b9-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cf0b9-116">Requirements</span></span>

<span data-ttu-id="cf0b9-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cf0b9-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cf0b9-118">**Espace de noms**  : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf0b9-118">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cf0b9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf0b9-119">See also</span></span>

[<span data-ttu-id="cf0b9-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cf0b9-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
