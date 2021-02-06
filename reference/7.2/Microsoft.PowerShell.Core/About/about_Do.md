---
description: Exécute une ou plusieurs fois une liste d’instructions, sous réserve d’une condition while ou until.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 412a13669e86df5804dd74d75fcb5b4389192c79
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598373"
---
# <a name="about-do"></a><span data-ttu-id="26a43-103">À propos de</span><span class="sxs-lookup"><span data-stu-id="26a43-103">About Do</span></span>

## <a name="short-description"></a><span data-ttu-id="26a43-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="26a43-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="26a43-105">Exécute une ou plusieurs fois une liste d’instructions, sous réserve d’une condition while ou until.</span><span class="sxs-lookup"><span data-stu-id="26a43-105">Runs a statement list one or more times, subject to a While or Until condition.</span></span>

## <a name="long-description"></a><span data-ttu-id="26a43-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="26a43-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="26a43-107">Le mot clé do fonctionne avec le mot clé While ou le mot clé Until pour exécuter les instructions dans un bloc de script, sous réserve d’une condition.</span><span class="sxs-lookup"><span data-stu-id="26a43-107">The Do keyword works with the While keyword or the Until keyword to run the statements in a script block, subject to a condition.</span></span> <span data-ttu-id="26a43-108">Contrairement à la boucle while associée, le bloc de script dans une boucle do s’exécute toujours au moins une fois.</span><span class="sxs-lookup"><span data-stu-id="26a43-108">Unlike the related While loop, the script block in a Do loop always runs at least once.</span></span>

<span data-ttu-id="26a43-109">Une boucle **do-while** est une variété de la boucle while.</span><span class="sxs-lookup"><span data-stu-id="26a43-109">A **Do-While** loop is a variety of the While loop.</span></span> <span data-ttu-id="26a43-110">Dans une boucle **do-while** , la condition est évaluée après l’exécution du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="26a43-110">In a **Do-While** loop, the condition is evaluated after the script block has run.</span></span> <span data-ttu-id="26a43-111">Comme dans une boucle while, le bloc de script est répété tant que la condition prend la valeur true.</span><span class="sxs-lookup"><span data-stu-id="26a43-111">As in a While loop, the script block is repeated as long as the condition evaluates to true.</span></span>

<span data-ttu-id="26a43-112">À l’instar d’une boucle **do-while** , une boucle **Do-Until** s’exécute toujours au moins une fois avant que la condition soit évaluée.</span><span class="sxs-lookup"><span data-stu-id="26a43-112">Like a **Do-While** loop, a **Do-Until** loop always runs at least once before the condition is evaluated.</span></span> <span data-ttu-id="26a43-113">Toutefois, le bloc de script s’exécute uniquement lorsque la condition a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="26a43-113">However, the script block runs only while the condition is false.</span></span>

<span data-ttu-id="26a43-114">Les mots clés de contrôle de *continuation continue* et *break* peuvent être utilisés dans une boucle **do-while** ou dans une boucle **Do-Until** .</span><span class="sxs-lookup"><span data-stu-id="26a43-114">The *Continue* and *Break* flow control keywords can be used in a **Do-While** loop or in a **Do-Until** loop.</span></span>

### <a name="syntax"></a><span data-ttu-id="26a43-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26a43-115">Syntax</span></span>

<span data-ttu-id="26a43-116">L’exemple suivant illustre la syntaxe de l’instruction **do-while** :</span><span class="sxs-lookup"><span data-stu-id="26a43-116">The following shows the syntax of the **Do-While** statement:</span></span>

```powershell
do {<statement list>} while (<condition>)
```

<span data-ttu-id="26a43-117">L’exemple suivant illustre la syntaxe de l’instruction **Do-Until** :</span><span class="sxs-lookup"><span data-stu-id="26a43-117">The following shows the syntax of the **Do-Until** statement:</span></span>

```powershell
do {<statement list>} until (<condition>)
```

<span data-ttu-id="26a43-118">La liste d’instructions contient une ou plusieurs instructions qui s’exécutent chaque fois que la boucle est entrée ou répétée.</span><span class="sxs-lookup"><span data-stu-id="26a43-118">The statement list contains one or more statements that run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="26a43-119">La partie condition de l’instruction correspond à true ou false.</span><span class="sxs-lookup"><span data-stu-id="26a43-119">The condition portion of the statement resolves to true or false.</span></span>

### <a name="example"></a><span data-ttu-id="26a43-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="26a43-120">Example</span></span>

<span data-ttu-id="26a43-121">L’exemple suivant d’une instruction do compte les éléments d’un tableau jusqu’à ce qu’il atteigne un élément avec une valeur de 0.</span><span class="sxs-lookup"><span data-stu-id="26a43-121">The following example of a Do statement counts the items in an array until it reaches an item with a value of 0.</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

<span data-ttu-id="26a43-122">L’exemple suivant utilise le mot clé until.</span><span class="sxs-lookup"><span data-stu-id="26a43-122">The following example uses the Until keyword.</span></span> <span data-ttu-id="26a43-123">Notez que l’opérateur différent de ( `-ne` ) est remplacé par l’opérateur égal à ( `-eq` ).</span><span class="sxs-lookup"><span data-stu-id="26a43-123">Notice that the not equal to operator (`-ne`) is replaced by the equal to operator (`-eq`).</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

<span data-ttu-id="26a43-124">L’exemple suivant écrit toutes les valeurs d’un tableau, en ignorant toute valeur inférieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="26a43-124">The following example writes all the values of an array, skipping any value that is less than zero.</span></span>

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a><span data-ttu-id="26a43-125">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="26a43-125">SEE ALSO</span></span>

[<span data-ttu-id="26a43-126">about_While</span><span class="sxs-lookup"><span data-stu-id="26a43-126">about_While</span></span>](about_While.md)

[<span data-ttu-id="26a43-127">about_Operators</span><span class="sxs-lookup"><span data-stu-id="26a43-127">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="26a43-128">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="26a43-128">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="26a43-129">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="26a43-129">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="26a43-130">about_Break</span><span class="sxs-lookup"><span data-stu-id="26a43-130">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="26a43-131">about_Continue</span><span class="sxs-lookup"><span data-stu-id="26a43-131">about_Continue</span></span>](about_Continue.md)

