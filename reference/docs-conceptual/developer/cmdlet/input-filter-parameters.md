---
title: Paramètres de filtre d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364388"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="311dc-102">Paramètres de filtre d’entrée</span><span class="sxs-lookup"><span data-stu-id="311dc-102">Input Filter Parameters</span></span>

<span data-ttu-id="311dc-103">Une applet de commande peut définir des paramètres `Filter`, `Include` et `Exclude` qui filtrent le jeu d’objets d’entrée que l’applet de commande affecte.</span><span class="sxs-lookup"><span data-stu-id="311dc-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="311dc-104">En règle générale, l’ensemble d’objets d’entrée est spécifié par un paramètre `InputObject`, `Path` ou `Name`.</span><span class="sxs-lookup"><span data-stu-id="311dc-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="311dc-105">Par exemple, une applet de commande peut avoir un paramètre `Path` qui accepte plusieurs chemins d’accès à l’aide de caractères génériques, et chaque chemin d’accès pointe vers un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="311dc-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="311dc-106">Utilisés ensemble, les paramètres `Filter`, `Include` et `Exclude` qualifient plus précisément les chemins d’accès de l’applet de commande à chaque fois qu’elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="311dc-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="311dc-107">Paramètres include et Exclude</span><span class="sxs-lookup"><span data-stu-id="311dc-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="311dc-108">Les paramètres `Include` et `Exclude` identifient les objets qui sont inclus ou exclus de l’ensemble d’objets d’entrée transmis à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="311dc-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="311dc-109">Utilisez ces paramètres lorsque le filtre peut être exprimé dans le langage générique standard.</span><span class="sxs-lookup"><span data-stu-id="311dc-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="311dc-110">(Pour plus d’informations sur les caractères génériques, consultez [prise en charge des caractères génériques dans les paramètres d’applet de](./supporting-wildcard-characters-in-cmdlet-parameters.md)commande.) Le paramètre `Include` comprend tous les objets dont les noms correspondent au filtre d’inclusion.</span><span class="sxs-lookup"><span data-stu-id="311dc-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="311dc-111">Le paramètre `Exclude` exclut tous les objets dont les noms correspondent au filtre.</span><span class="sxs-lookup"><span data-stu-id="311dc-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="311dc-112">Paramètre de filtre</span><span class="sxs-lookup"><span data-stu-id="311dc-112">Filter Parameter</span></span>

<span data-ttu-id="311dc-113">Le paramètre `Filter` spécifie un filtre qui n’est pas exprimé dans le langage générique standard.</span><span class="sxs-lookup"><span data-stu-id="311dc-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="311dc-114">Par exemple, les interfaces de service Active Directory (ADSI) ou les filtres SQL peuvent être passés à l’applet de commande par le biais de son paramètre `Filter`.</span><span class="sxs-lookup"><span data-stu-id="311dc-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="311dc-115">Dans les applets de commande fournies par Windows PowerShell, ces filtres sont spécifiés par les fournisseurs Windows PowerShell qui utilisent l’applet de commande pour accéder à un magasin de données.</span><span class="sxs-lookup"><span data-stu-id="311dc-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="311dc-116">Chaque fournisseur définit généralement son propre filtre.</span><span class="sxs-lookup"><span data-stu-id="311dc-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="311dc-117">Filtrage si aucun jeu d’objets d’entrée n’est spécifié</span><span class="sxs-lookup"><span data-stu-id="311dc-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="311dc-118">Si aucun jeu d’objets d’entrée n’est spécifié, cela signifie généralement que vous filtrez par rapport à tous les objets.</span><span class="sxs-lookup"><span data-stu-id="311dc-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="311dc-119">Pour plus d’informations, consultez la rubrique[obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="311dc-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="311dc-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="311dc-120">See Also</span></span>

[<span data-ttu-id="311dc-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="311dc-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)