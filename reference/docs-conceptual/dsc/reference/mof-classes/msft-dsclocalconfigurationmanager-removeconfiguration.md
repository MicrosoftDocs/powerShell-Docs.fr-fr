---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: RemoveConfiguration, méthode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953396"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="c7ce3-103">RemoveConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="c7ce3-103">RemoveConfiguration method</span></span>

<span data-ttu-id="c7ce3-104">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="c7ce3-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7ce3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7ce3-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="c7ce3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7ce3-106">Parameters</span></span>

<span data-ttu-id="c7ce3-107">*Stage* \[in\] Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c7ce3-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="c7ce3-108">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="c7ce3-108">The following values are valid:</span></span>

|<span data-ttu-id="c7ce3-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="c7ce3-109">Value</span></span> |<span data-ttu-id="c7ce3-110">Description</span><span class="sxs-lookup"><span data-stu-id="c7ce3-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="c7ce3-111">**1**</span><span class="sxs-lookup"><span data-stu-id="c7ce3-111">**1**</span></span> | <span data-ttu-id="c7ce3-112">Document de configuration **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="c7ce3-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="c7ce3-113">**2**</span><span class="sxs-lookup"><span data-stu-id="c7ce3-113">**2**</span></span> | <span data-ttu-id="c7ce3-114">Document de configuration **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="c7ce3-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="c7ce3-115">**4**</span><span class="sxs-lookup"><span data-stu-id="c7ce3-115">**4**</span></span> | <span data-ttu-id="c7ce3-116">Document de configuration **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="c7ce3-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="c7ce3-117">*Force* \[in\] **true** pour forcer la suppression de la configuration.</span><span class="sxs-lookup"><span data-stu-id="c7ce3-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7ce3-118">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c7ce3-118">Return value</span></span>

<span data-ttu-id="c7ce3-119">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c7ce3-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7ce3-120">Notes</span><span class="sxs-lookup"><span data-stu-id="c7ce3-120">Remarks</span></span>

<span data-ttu-id="c7ce3-121">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="c7ce3-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7ce3-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c7ce3-122">Requirements</span></span>

<span data-ttu-id="c7ce3-123">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c7ce3-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c7ce3-124">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c7ce3-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c7ce3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7ce3-125">See also</span></span>

[<span data-ttu-id="c7ce3-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c7ce3-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
