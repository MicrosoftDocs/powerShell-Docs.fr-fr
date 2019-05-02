---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078639"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="69b25-103">Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="69b25-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="69b25-104">Obtient la sortie de l’agent de configuration associée à un travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="69b25-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="69b25-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69b25-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="69b25-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="69b25-106">Parameters</span></span>

<span data-ttu-id="69b25-107">*jobId* \[in\] ID du travail pour lequel obtenir les données de sortie.</span><span class="sxs-lookup"><span data-stu-id="69b25-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="69b25-108">*resumeOutputBookmark* \[in\] Spécifie que la sortie doit être une continuation à partir d’un signet précédent.</span><span class="sxs-lookup"><span data-stu-id="69b25-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="69b25-109">*output* \[out\] Sortie pour le travail spécifié.</span><span class="sxs-lookup"><span data-stu-id="69b25-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="69b25-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="69b25-110">Return value</span></span>

<span data-ttu-id="69b25-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="69b25-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="69b25-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="69b25-112">Remarks</span></span>

<span data-ttu-id="69b25-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="69b25-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="69b25-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="69b25-114">Requirements</span></span>

<span data-ttu-id="69b25-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="69b25-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="69b25-116">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="69b25-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="69b25-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69b25-117">See also</span></span>

[<span data-ttu-id="69b25-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="69b25-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)