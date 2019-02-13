---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677622"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="60b6e-103">Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="60b6e-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="60b6e-104">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="60b6e-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="60b6e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60b6e-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="60b6e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60b6e-106">Parameters</span></span>

<span data-ttu-id="60b6e-107">*Stage* \[in\] Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="60b6e-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="60b6e-108">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="60b6e-108">The following values are valid:</span></span>

|<span data-ttu-id="60b6e-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="60b6e-109">Value</span></span> |<span data-ttu-id="60b6e-110">Description</span><span class="sxs-lookup"><span data-stu-id="60b6e-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="60b6e-111">**1**</span><span class="sxs-lookup"><span data-stu-id="60b6e-111">**1**</span></span> | <span data-ttu-id="60b6e-112">Document de configuration **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="60b6e-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="60b6e-113">**2**</span><span class="sxs-lookup"><span data-stu-id="60b6e-113">**2**</span></span> | <span data-ttu-id="60b6e-114">Document de configuration **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="60b6e-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="60b6e-115">**4**</span><span class="sxs-lookup"><span data-stu-id="60b6e-115">**4**</span></span> | <span data-ttu-id="60b6e-116">Document de configuration **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="60b6e-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="60b6e-117">*Force* \[in\] **true** pour forcer la suppression de la configuration.</span><span class="sxs-lookup"><span data-stu-id="60b6e-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="60b6e-118">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="60b6e-118">Return value</span></span>

<span data-ttu-id="60b6e-119">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="60b6e-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="60b6e-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="60b6e-120">Remarks</span></span>

<span data-ttu-id="60b6e-121">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="60b6e-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="60b6e-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="60b6e-122">Requirements</span></span>

<span data-ttu-id="60b6e-123">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="60b6e-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="60b6e-124">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="60b6e-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="60b6e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60b6e-125">See also</span></span>

[<span data-ttu-id="60b6e-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="60b6e-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)