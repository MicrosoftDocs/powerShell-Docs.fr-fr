---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: ResourceTest, méthode
ms.openlocfilehash: 7ef65227342091cb2a5063aaf95a2780d217f85a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463803"
---
# <a name="resourcetest-method"></a><span data-ttu-id="90f35-103">ResourceTest, méthode</span><span class="sxs-lookup"><span data-stu-id="90f35-103">ResourceTest method</span></span>

<span data-ttu-id="90f35-104">Appelle directement la méthode **Test** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="90f35-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="90f35-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90f35-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="90f35-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90f35-106">Parameters</span></span>

<span data-ttu-id="90f35-107">**ResourceType** \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="90f35-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="90f35-108">**ModuleName** \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="90f35-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="90f35-109">\***resourceProperty** \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="90f35-109">\***resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="90f35-110">Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="90f35-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="90f35-111">*InDesiredState*\* \[out\] En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="90f35-111">*InDesiredState*\* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="90f35-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="90f35-112">Return value</span></span>

<span data-ttu-id="90f35-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="90f35-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="90f35-114">Notes</span><span class="sxs-lookup"><span data-stu-id="90f35-114">Remarks</span></span>

<span data-ttu-id="90f35-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="90f35-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="90f35-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="90f35-116">Requirements</span></span>

<span data-ttu-id="90f35-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="90f35-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="90f35-118">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="90f35-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="90f35-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90f35-119">See also</span></span>

[<span data-ttu-id="90f35-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="90f35-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
