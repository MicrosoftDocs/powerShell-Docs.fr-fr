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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854465"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="3d7d1-102">Paramètres de filtre d’entrée</span><span class="sxs-lookup"><span data-stu-id="3d7d1-102">Input Filter Parameters</span></span>

<span data-ttu-id="3d7d1-103">Une applet de commande permettre définir `Filter`, `Include`, et `Exclude` paramètres qui filtrent l’ensemble des objets d’entrée qui affecte l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="3d7d1-104">En règle générale, le jeu d’objets d’entrée est spécifié par un `InputObject`, `Path`, ou `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="3d7d1-105">Par exemple, une applet de commande peut avoir un `Path` paramètre qui accepte plusieurs chemins d’accès à l’aide des caractères génériques et chaque chemin pointe vers un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="3d7d1-106">Utilisés conjointement, le `Filter`, `Include`, et `Exclude` davantage de paramètres qualifier les chemins d’accès de l’applet de commande fonctionne sur chaque fois qu’elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="3d7d1-107">Inclure et exclure des paramètres</span><span class="sxs-lookup"><span data-stu-id="3d7d1-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="3d7d1-108">Le `Include` et `Exclude` paramètres identifient les objets qui sont inclus ou exclus de l’ensemble d’objets d’entrée passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="3d7d1-109">Utilisez ces paramètres lorsque le filtre peut être exprimé en langage générique standard.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="3d7d1-110">(Pour plus d’informations sur les caractères génériques, consultez [prenant en charge les caractères génériques dans les paramètres de l’applet de commande](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Le `Include` paramètre inclut tous les objets dont les noms correspondent au filtre de l’inclusion.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="3d7d1-111">Le `Exclude` paramètre exclut tous les objets dont les noms correspondent au filtre.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="3d7d1-112">Paramètre de filtre</span><span class="sxs-lookup"><span data-stu-id="3d7d1-112">Filter Parameter</span></span>

<span data-ttu-id="3d7d1-113">Le `Filter` paramètre spécifie un filtre qui n’est pas exprimé en langage générique standard.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="3d7d1-114">Par exemple, les filtres d’Active Directory Service Interfaces (ADSI) ou SQL peuvent être passées à l’applet de commande via son `Filter` paramètre.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="3d7d1-115">Dans les applets de commande fournies par Windows PowerShell, ces filtres sont spécifiés par les fournisseurs Windows PowerShell qui utilisent l’applet de commande pour accéder à un magasin de données.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="3d7d1-116">Chaque fournisseur définit généralement son propre filtre.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="3d7d1-117">Filtrage si aucun jeu d’objets d’entrée n’est spécifié</span><span class="sxs-lookup"><span data-stu-id="3d7d1-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="3d7d1-118">Si aucun jeu d’objets d’entrée n’est spécifié, cela signifie généralement filtrer par rapport à tous les objets.</span><span class="sxs-lookup"><span data-stu-id="3d7d1-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="3d7d1-119">Pour plus d’informations, consultez[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="3d7d1-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d7d1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d7d1-120">See Also</span></span>

[<span data-ttu-id="3d7d1-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d7d1-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)