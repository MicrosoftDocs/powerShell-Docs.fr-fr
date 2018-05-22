---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f9358-103">Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f9358-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f9358-104">Obtient la sortie de l’agent de configuration associée à un travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="f9358-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="f9358-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9358-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="f9358-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f9358-106">Parameters</span></span>
----------

<span data-ttu-id="f9358-107">*jobId* \[in\] ID du travail pour lequel obtenir les données de sortie.</span><span class="sxs-lookup"><span data-stu-id="f9358-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="f9358-108">*resumeOutputBookmark* \[in\] Spécifie que la sortie doit être une continuation à partir d’un signet précédent.</span><span class="sxs-lookup"><span data-stu-id="f9358-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="f9358-109">*output* \[out\] Sortie pour le travail spécifié.</span><span class="sxs-lookup"><span data-stu-id="f9358-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="f9358-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f9358-110">Return value</span></span>
------------

<span data-ttu-id="f9358-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f9358-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9358-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="f9358-112">Remarks</span></span>

<span data-ttu-id="f9358-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="f9358-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9358-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f9358-114">Requirements</span></span>
------------
><span data-ttu-id="f9358-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f9358-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f9358-116">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f9358-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f9358-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9358-117">See also</span></span>


[<span data-ttu-id="f9358-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f9358-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)