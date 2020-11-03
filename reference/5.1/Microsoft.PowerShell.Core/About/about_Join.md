---
description: Décrit comment l’opérateur de jointure (-Join) combine plusieurs chaînes en une seule chaîne.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: 3e5bf4363adbded29dc58facde00f6597abeb697
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207653"
---
# <a name="about-join"></a><span data-ttu-id="354f6-104">À propos de Join</span><span class="sxs-lookup"><span data-stu-id="354f6-104">About join</span></span>

## <a name="short-description"></a><span data-ttu-id="354f6-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="354f6-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="354f6-106">Décrit comment l’opérateur de jointure (-Join) combine plusieurs chaînes en une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="354f6-106">Describes how the join operator (-join) combines multiple strings into a single string.</span></span>

## <a name="long-description"></a><span data-ttu-id="354f6-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="354f6-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="354f6-108">L’opérateur Join concatène un ensemble de chaînes en une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="354f6-108">The join operator concatenates a set of strings into a single string.</span></span> <span data-ttu-id="354f6-109">Les chaînes sont ajoutées à la chaîne résultante dans l’ordre dans lequel elles apparaissent dans la commande.</span><span class="sxs-lookup"><span data-stu-id="354f6-109">The strings are appended to the resulting string in the order that they appear in the command.</span></span>

### <a name="syntax"></a><span data-ttu-id="354f6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="354f6-110">Syntax</span></span>

<span data-ttu-id="354f6-111">Le diagramme suivant illustre la syntaxe de l’opérateur de jointure.</span><span class="sxs-lookup"><span data-stu-id="354f6-111">The following diagram shows the syntax for the join operator.</span></span>

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a><span data-ttu-id="354f6-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="354f6-112">Parameters</span></span>

<span data-ttu-id="354f6-113">String [] : spécifie une ou plusieurs chaînes à joindre.</span><span class="sxs-lookup"><span data-stu-id="354f6-113">String[] - Specifies one or more strings to be joined.</span></span>

<span data-ttu-id="354f6-114">Delimiter : spécifie un ou plusieurs caractères placés entre les chaînes concaténées.</span><span class="sxs-lookup"><span data-stu-id="354f6-114">Delimiter - Specifies one or more characters placed between the concatenated strings.</span></span> <span data-ttu-id="354f6-115">La valeur par défaut est aucun délimiteur ("").</span><span class="sxs-lookup"><span data-stu-id="354f6-115">The default is no delimiter ("").</span></span>

<span data-ttu-id="354f6-116">Notes</span><span class="sxs-lookup"><span data-stu-id="354f6-116">Remarks</span></span>

<span data-ttu-id="354f6-117">L’opérateur de jointure unaire (-Join <String [] >) a une priorité plus élevée qu’une virgule.</span><span class="sxs-lookup"><span data-stu-id="354f6-117">The unary join operator (-join <string[]>) has higher precedence than a comma.</span></span> <span data-ttu-id="354f6-118">Par conséquent, si vous soumettez une liste de chaînes séparées par des virgules à l’opérateur de jointure unaire, seule la première chaîne (avant la première virgule) est soumise à l’opérateur de jointure.</span><span class="sxs-lookup"><span data-stu-id="354f6-118">As a result, if you submit a comma-separated list of strings to the unary join operator, only the first string (before the first comma) is submitted to the join operator.</span></span>

<span data-ttu-id="354f6-119">Pour utiliser l’opérateur de jointure unaire, mettez les chaînes entre parenthèses, ou stockez les chaînes dans une variable, puis soumettez la variable à joindre.</span><span class="sxs-lookup"><span data-stu-id="354f6-119">To use the unary join operator, enclose the strings in parentheses, or store the strings in a variable, and then submit the variable to join.</span></span>

<span data-ttu-id="354f6-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="354f6-120">For example:</span></span>

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a><span data-ttu-id="354f6-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="354f6-121">Examples</span></span>

<span data-ttu-id="354f6-122">L’instruction suivante joint trois chaînes :</span><span class="sxs-lookup"><span data-stu-id="354f6-122">The following statement joins three strings:</span></span>

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

<span data-ttu-id="354f6-123">L’instruction suivante joint trois chaînes délimitées par un espace :</span><span class="sxs-lookup"><span data-stu-id="354f6-123">The following statement joins three strings delimited by a space:</span></span>

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

<span data-ttu-id="354f6-124">Les instructions suivantes utilisent un délimiteur de plusieurs caractères pour joindre trois chaînes :</span><span class="sxs-lookup"><span data-stu-id="354f6-124">The following statements use a multiple-character delimiter to join three strings:</span></span>

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

<span data-ttu-id="354f6-125">L’instruction suivante joint les lignes d’une chaîne ici dans une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="354f6-125">The following statement joins the lines in a here-string into a single string.</span></span> <span data-ttu-id="354f6-126">Étant donné qu’une chaîne ici est une chaîne, les lignes de la chaîne ici doivent être fractionnées avant de pouvoir être jointes.</span><span class="sxs-lookup"><span data-stu-id="354f6-126">Because a here-string is one string, the lines in the here-string must be split before they can be joined.</span></span> <span data-ttu-id="354f6-127">Vous pouvez utiliser cette méthode pour rattacher les chaînes dans un fichier XML qui a été enregistré dans une chaîne ici :</span><span class="sxs-lookup"><span data-stu-id="354f6-127">You can use this method to rejoin the strings in an XML file that has been saved in a here-string:</span></span>

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a><span data-ttu-id="354f6-128">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="354f6-128">SEE ALSO</span></span>

[<span data-ttu-id="354f6-129">about_Operators</span><span class="sxs-lookup"><span data-stu-id="354f6-129">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="354f6-130">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="354f6-130">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="354f6-131">about_Split</span><span class="sxs-lookup"><span data-stu-id="354f6-131">about_Split</span></span>](about_Split.md)
