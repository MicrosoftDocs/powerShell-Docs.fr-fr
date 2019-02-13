---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679005"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cad3b-103">Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cad3b-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cad3b-104">Appelle directement la méthode **Get** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="cad3b-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="cad3b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cad3b-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="cad3b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cad3b-106">Parameters</span></span>

<span data-ttu-id="cad3b-107">*ResourceType* \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="cad3b-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="cad3b-108">*ModuleName* \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="cad3b-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="cad3b-109">*resourceProperty* \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="cad3b-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="cad3b-110">Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="cad3b-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="cad3b-111">*configurations* \[out\] En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="cad3b-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="cad3b-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="cad3b-112">Return value</span></span>

<span data-ttu-id="cad3b-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="cad3b-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cad3b-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="cad3b-114">Remarks</span></span>

<span data-ttu-id="cad3b-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="cad3b-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cad3b-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cad3b-116">Requirements</span></span>

<span data-ttu-id="cad3b-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cad3b-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cad3b-118">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cad3b-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cad3b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cad3b-119">See also</span></span>

[<span data-ttu-id="cad3b-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cad3b-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)