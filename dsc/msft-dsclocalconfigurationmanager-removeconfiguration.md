---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189735"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c5882-103">Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c5882-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c5882-104">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="c5882-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="c5882-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5882-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="c5882-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5882-106">Parameters</span></span>
----------

<span data-ttu-id="c5882-107">*Stage* \[in\] Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c5882-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="c5882-108">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="c5882-108">The following values are valid:</span></span>

|<span data-ttu-id="c5882-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="c5882-109">Value</span></span> |<span data-ttu-id="c5882-110">Description</span><span class="sxs-lookup"><span data-stu-id="c5882-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="c5882-111">**1**</span><span class="sxs-lookup"><span data-stu-id="c5882-111">**1**</span></span> | <span data-ttu-id="c5882-112">Document de configuration **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="c5882-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="c5882-113">**2**</span><span class="sxs-lookup"><span data-stu-id="c5882-113">**2**</span></span> | <span data-ttu-id="c5882-114">Document de configuration **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="c5882-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="c5882-115">**4**</span><span class="sxs-lookup"><span data-stu-id="c5882-115">**4**</span></span> | <span data-ttu-id="c5882-116">Document de configuration **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="c5882-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="c5882-117">*Force* \[in\] **true** pour forcer la suppression de la configuration.</span><span class="sxs-lookup"><span data-stu-id="c5882-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c5882-118">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c5882-118">Return value</span></span>
------------

<span data-ttu-id="c5882-119">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c5882-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5882-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5882-120">Remarks</span></span>

<span data-ttu-id="c5882-121">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="c5882-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5882-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c5882-122">Requirements</span></span>
------------
><span data-ttu-id="c5882-123">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c5882-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c5882-124">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c5882-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c5882-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5882-125">See also</span></span>


[<span data-ttu-id="c5882-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c5882-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)