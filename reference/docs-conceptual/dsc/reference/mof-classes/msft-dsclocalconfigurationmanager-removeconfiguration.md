---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration, méthode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953396"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="4f582-103">RemoveConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="4f582-103">RemoveConfiguration method</span></span>

<span data-ttu-id="4f582-104">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="4f582-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="4f582-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f582-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="4f582-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f582-106">Parameters</span></span>

<span data-ttu-id="4f582-107">*Stage* \[in\] Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="4f582-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="4f582-108">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="4f582-108">The following values are valid:</span></span>

|<span data-ttu-id="4f582-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="4f582-109">Value</span></span> |<span data-ttu-id="4f582-110">Description</span><span class="sxs-lookup"><span data-stu-id="4f582-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="4f582-111">**1**</span><span class="sxs-lookup"><span data-stu-id="4f582-111">**1**</span></span> | <span data-ttu-id="4f582-112">Document de configuration **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="4f582-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="4f582-113">**2**</span><span class="sxs-lookup"><span data-stu-id="4f582-113">**2**</span></span> | <span data-ttu-id="4f582-114">Document de configuration **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="4f582-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="4f582-115">**4**</span><span class="sxs-lookup"><span data-stu-id="4f582-115">**4**</span></span> | <span data-ttu-id="4f582-116">Document de configuration **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="4f582-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="4f582-117">*Force* \[in\] **true** pour forcer la suppression de la configuration.</span><span class="sxs-lookup"><span data-stu-id="4f582-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4f582-118">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="4f582-118">Return value</span></span>

<span data-ttu-id="4f582-119">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4f582-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4f582-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="4f582-120">Remarks</span></span>

<span data-ttu-id="4f582-121">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="4f582-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f582-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4f582-122">Requirements</span></span>

<span data-ttu-id="4f582-123">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4f582-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4f582-124">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4f582-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4f582-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f582-125">See also</span></span>

[<span data-ttu-id="4f582-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4f582-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
