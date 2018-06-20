---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 714bbb286ebbe4ed0f1faa15e03ac4b51a3ee87f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218856"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ce8fe-103">Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ce8fe-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ce8fe-104">Appelle directement la méthode **Test** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="ce8fe-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="ce8fe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce8fe-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="ce8fe-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce8fe-106">Parameters</span></span>
----------

<span data-ttu-id="ce8fe-107">*ResourceType* \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="ce8fe-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="ce8fe-108">*ModuleName* \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="ce8fe-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="ce8fe-109">*resourceProperty* \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="ce8fe-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="ce8fe-110">Utilisez l’applet de commande [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="ce8fe-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="ce8fe-111">*InDesiredState* \[out\] En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="ce8fe-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="ce8fe-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ce8fe-112">Return value</span></span>
------------

<span data-ttu-id="ce8fe-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ce8fe-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce8fe-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="ce8fe-114">Remarks</span></span>

<span data-ttu-id="ce8fe-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="ce8fe-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ce8fe-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce8fe-116">Requirements</span></span>
------------
><span data-ttu-id="ce8fe-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ce8fe-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ce8fe-118">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce8fe-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ce8fe-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce8fe-119">See also</span></span>


[<span data-ttu-id="ce8fe-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ce8fe-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)