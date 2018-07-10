---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892682"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0e443-103">Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0e443-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0e443-104">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="0e443-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e443-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e443-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="0e443-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e443-106">Parameters</span></span>

<span data-ttu-id="0e443-107">*Stage* \[in\] Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="0e443-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="0e443-108">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="0e443-108">The following values are valid:</span></span>

|<span data-ttu-id="0e443-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="0e443-109">Value</span></span> |<span data-ttu-id="0e443-110">Description</span><span class="sxs-lookup"><span data-stu-id="0e443-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="0e443-111">**1**</span><span class="sxs-lookup"><span data-stu-id="0e443-111">**1**</span></span> | <span data-ttu-id="0e443-112">Document de configuration **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="0e443-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="0e443-113">**2**</span><span class="sxs-lookup"><span data-stu-id="0e443-113">**2**</span></span> | <span data-ttu-id="0e443-114">Document de configuration **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="0e443-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="0e443-115">**4**</span><span class="sxs-lookup"><span data-stu-id="0e443-115">**4**</span></span> | <span data-ttu-id="0e443-116">Document de configuration **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="0e443-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="0e443-117">*Force* \[in\] **true** pour forcer la suppression de la configuration.</span><span class="sxs-lookup"><span data-stu-id="0e443-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0e443-118">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0e443-118">Return value</span></span>

<span data-ttu-id="0e443-119">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0e443-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e443-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="0e443-120">Remarks</span></span>

<span data-ttu-id="0e443-121">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0e443-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e443-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0e443-122">Requirements</span></span>

<span data-ttu-id="0e443-123">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0e443-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0e443-124">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0e443-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0e443-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e443-125">See also</span></span>

[<span data-ttu-id="0e443-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0e443-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)