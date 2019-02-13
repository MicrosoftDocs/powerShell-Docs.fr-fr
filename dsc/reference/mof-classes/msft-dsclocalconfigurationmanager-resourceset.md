---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode ResourceSet de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678289"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e3636-103">Méthode ResourceSet de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e3636-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e3636-104">Appelle directement la méthode **Set** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="e3636-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3636-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3636-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="e3636-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3636-106">Parameters</span></span>

<span data-ttu-id="e3636-107">*ResourceType* \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="e3636-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="e3636-108">*ModuleName* \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="e3636-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="e3636-109">*resourceProperty* \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="e3636-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="e3636-110">Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="e3636-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="e3636-111">*RebootRequired* \[out\] En retour, cette propriété prend la valeur **true** si le nœud cible doit être redémarré.</span><span class="sxs-lookup"><span data-stu-id="e3636-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="e3636-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e3636-112">Return value</span></span>

<span data-ttu-id="e3636-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e3636-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3636-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="e3636-114">Remarks</span></span>

<span data-ttu-id="e3636-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="e3636-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3636-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e3636-116">Requirements</span></span>

<span data-ttu-id="e3636-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e3636-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e3636-118">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e3636-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e3636-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3636-119">See also</span></span>

[<span data-ttu-id="e3636-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e3636-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)