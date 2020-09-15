---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: GetConfigurationResultOutput, méthode
ms.openlocfilehash: 9c81082c28b2ffcc329264d29784782deaa9779d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464075"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="0e3fe-103">GetConfigurationResultOutput, méthode</span><span class="sxs-lookup"><span data-stu-id="0e3fe-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="0e3fe-104">Obtient la sortie de l’agent de configuration associée à un travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e3fe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e3fe-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="0e3fe-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e3fe-106">Parameters</span></span>

<span data-ttu-id="0e3fe-107">**jobId** \[in\] ID du travail pour lequel obtenir les données de sortie.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-107">**jobId** \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="0e3fe-108">**resumeOutputBookmark** \[in\] Spécifie que la sortie doit être une continuation à partir d’un signet précédent.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-108">**resumeOutputBookmark** \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="0e3fe-109">**output** \[out\] Sortie pour le travail spécifié.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-109">**output** \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="0e3fe-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="0e3fe-110">Return value</span></span>

<span data-ttu-id="0e3fe-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e3fe-112">Notes</span><span class="sxs-lookup"><span data-stu-id="0e3fe-112">Remarks</span></span>

<span data-ttu-id="0e3fe-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e3fe-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0e3fe-114">Requirements</span></span>

<span data-ttu-id="0e3fe-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0e3fe-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0e3fe-116">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0e3fe-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0e3fe-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e3fe-117">See also</span></span>

[<span data-ttu-id="0e3fe-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0e3fe-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
