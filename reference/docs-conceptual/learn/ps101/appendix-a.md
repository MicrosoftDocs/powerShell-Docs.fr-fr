---
title: Annexe A - Syntaxe de l’aide
description: Cet article explique comment lire et comprendre la syntaxe d’une applet de commande telle que présentée par Get-Help.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fe218f2a9af1ad1ee6b88740414ecede0194bd
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99596715"
---
# <a name="appendix-a---help-syntax"></a><span data-ttu-id="acc0e-103">Annexe A - Syntaxe de l’aide</span><span class="sxs-lookup"><span data-stu-id="acc0e-103">Appendix A - Help Syntax</span></span>

<span data-ttu-id="acc0e-104">L’exemple suivant montre comment obtenir la section **SYNTAXE** de l’aide pour l’applet de commande `Get-EventLog`.</span><span class="sxs-lookup"><span data-stu-id="acc0e-104">The following example shows the **SYNTAX** section of the help for the `Get-EventLog` cmdlet.</span></span>

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

<span data-ttu-id="acc0e-105">Dans cet exemple, seule la partie pertinente de l’aide est indiquée.</span><span class="sxs-lookup"><span data-stu-id="acc0e-105">Only the relevant portion of the help is shown in this example.</span></span>

<span data-ttu-id="acc0e-106">La syntaxe est principalement composée de plusieurs séries de crochets ouvrants et fermants (`[]`).</span><span class="sxs-lookup"><span data-stu-id="acc0e-106">The syntax is primarily made up of several sets of opening and closing brackets (`[]`).</span></span> <span data-ttu-id="acc0e-107">Ceux-ci ont deux significations différentes selon la façon dont ils sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="acc0e-107">These have two different meanings depending on how they're used.</span></span> <span data-ttu-id="acc0e-108">Tout ce qui est contenu entre crochets est facultatif, sauf s’il s’agit d’une série de crochets vides `[]`.</span><span class="sxs-lookup"><span data-stu-id="acc0e-108">Anything contained within square brackets is optional unless they're a set of empty square brackets `[]`.</span></span> <span data-ttu-id="acc0e-109">Les crochets vides s’affichent uniquement après un type de données comme `<string[]>`.</span><span class="sxs-lookup"><span data-stu-id="acc0e-109">Empty square brackets only appear after a datatype such as `<string[]>`.</span></span> <span data-ttu-id="acc0e-110">Cela signifie qu’un paramètre particulier peut accepter plusieurs valeurs de ce type.</span><span class="sxs-lookup"><span data-stu-id="acc0e-110">This means that particular parameter can accept more than one value of that type.</span></span>

<span data-ttu-id="acc0e-111">Le premier paramètre du premier jeu de paramètres de `Get-EventLog` est **LogName**.</span><span class="sxs-lookup"><span data-stu-id="acc0e-111">The first parameter in the first parameter set of `Get-EventLog` is **LogName**.</span></span> <span data-ttu-id="acc0e-112">LogName est placé entre crochets, ce qui signifie qu’il s’agit d’un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="acc0e-112">LogName is surrounded by square brackets which means that it's a positional parameter.</span></span> <span data-ttu-id="acc0e-113">En d’autres termes, le fait de spécifier le nom du paramètre lui-même est facultatif, à condition qu’il soit spécifié à l’emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="acc0e-113">In other words, specifying the name of the parameter itself is optional as long as it's specified in the correct position.</span></span> <span data-ttu-id="acc0e-114">Les informations incluses entre crochets pointus (`<>`) après le nom du paramètre indiquent qu’il a besoin d’une seule valeur **string** (chaîne).</span><span class="sxs-lookup"><span data-stu-id="acc0e-114">The information in the angle brackets (`<>`) after the parameter name indicates that it needs a single **string** value.</span></span> <span data-ttu-id="acc0e-115">Comme l’ensemble du nom de paramètre et du type de données ne sont pas placés entre crochets angulaires, le paramètre **LogName** est obligatoire lors de l’utilisation de ce jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="acc0e-115">The entire parameter name and datatype are not surrounded by square brackets so the **LogName** parameter is required when using this parameter set.</span></span>

```powershell
Get-EventLog [-LogName] <String>
```

<span data-ttu-id="acc0e-116">Le deuxième paramètre est **InstanceId**.</span><span class="sxs-lookup"><span data-stu-id="acc0e-116">The second parameter is **InstanceId**.</span></span> <span data-ttu-id="acc0e-117">Notez que le nom de paramètre et le type de données sont tous deux placés en totalité entre crochets angulaires.</span><span class="sxs-lookup"><span data-stu-id="acc0e-117">Notice that the parameter name and the datatype are both completely surrounded by square brackets.</span></span> <span data-ttu-id="acc0e-118">Cela signifie que le paramètre **InstanceId** est facultatif, et non obligatoire.</span><span class="sxs-lookup"><span data-stu-id="acc0e-118">This means that the **InstanceId** parameter is optional, not mandatory.</span></span> <span data-ttu-id="acc0e-119">Notez également qu’**InstanceId** est placé entre sa propre série de crochets angulaires.</span><span class="sxs-lookup"><span data-stu-id="acc0e-119">Also notice that **InstanceId** is surrounded by its own set of square brackets.</span></span> <span data-ttu-id="acc0e-120">Comme avec le paramètre **LogName**, cela signifie que le paramètre est positionnel.</span><span class="sxs-lookup"><span data-stu-id="acc0e-120">As with the **LogName** parameter, this means the parameter is positional.</span></span> <span data-ttu-id="acc0e-121">Il y a une dernière série de crochets angulaires après le type de données.</span><span class="sxs-lookup"><span data-stu-id="acc0e-121">There's one last set of square brackets after the datatype.</span></span> <span data-ttu-id="acc0e-122">Cela signifie qu’il peut accepter plusieurs valeurs sous la forme d’une table ou d’une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="acc0e-122">This means that it can accept more than one value in the form of an array or a comma-separated list.</span></span>

```
[[-InstanceId] <Int64[]>]
```

<span data-ttu-id="acc0e-123">Le deuxième jeu de paramètres a un paramètre **List**.</span><span class="sxs-lookup"><span data-stu-id="acc0e-123">The second parameter set has a **List** parameter.</span></span> <span data-ttu-id="acc0e-124">Il s’agit d’un paramètre booléen car aucun type de données ne suit le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="acc0e-124">It's a switch parameter because there's no datatype following the parameter name.</span></span> <span data-ttu-id="acc0e-125">Quand le paramètre **List** est spécifié, la valeur est **True**.</span><span class="sxs-lookup"><span data-stu-id="acc0e-125">When the **List** parameter is specified, the value is **True**.</span></span> <span data-ttu-id="acc0e-126">Quand il n’est pas spécifié, la valeur est **False**.</span><span class="sxs-lookup"><span data-stu-id="acc0e-126">When it's not specified, the value is **False**.</span></span>

```
[-List]
```

<span data-ttu-id="acc0e-127">Les informations sur la syntaxe d’une commande peuvent également être récupérées avec `Get-Command` à l’aide du paramètre **Syntax**.</span><span class="sxs-lookup"><span data-stu-id="acc0e-127">The syntax information for a command can also be retrieved using `Get-Command` using the **Syntax** parameter.</span></span> <span data-ttu-id="acc0e-128">Il s’agit d’un raccourci pratique que j’utilise tout le temps.</span><span class="sxs-lookup"><span data-stu-id="acc0e-128">This is a handy shortcut that I use all the time.</span></span> <span data-ttu-id="acc0e-129">Il me permet d’apprendre rapidement comment utiliser une commande sans avoir à passer en revue plusieurs pages d’informations d’aide.</span><span class="sxs-lookup"><span data-stu-id="acc0e-129">It allows me to quickly learn how to use a command without having to sift through multiple pages of help information.</span></span> <span data-ttu-id="acc0e-130">Si je vois que j’ai besoin d’informations supplémentaires, je reviens au contenu de l’aide.</span><span class="sxs-lookup"><span data-stu-id="acc0e-130">If I end up needing more information, then I'll revert to using the actual help content.</span></span>

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

<span data-ttu-id="acc0e-131">Plus vous utilisez le système d’aide dans PowerShell, plus il est facile de mémoriser les différentes nuances.</span><span class="sxs-lookup"><span data-stu-id="acc0e-131">The more you use the help system in PowerShell, the easier remembering all of the different nuances becomes.</span></span> <span data-ttu-id="acc0e-132">Avant même de vous en apercevoir, son utilisation devient une seconde nature.</span><span class="sxs-lookup"><span data-stu-id="acc0e-132">Before you know it, using it becomes second nature.</span></span>
