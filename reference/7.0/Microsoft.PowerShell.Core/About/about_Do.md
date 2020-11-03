---
description: Exécute une ou plusieurs fois une liste d’instructions, sous réserve d’une condition while ou until.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: ee4d7fbb53c5d1e9dd72243385f7eca0f4665623
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208230"
---
# <a name="about-do"></a><span data-ttu-id="96dce-104">À propos de</span><span class="sxs-lookup"><span data-stu-id="96dce-104">About Do</span></span>

## <a name="short-description"></a><span data-ttu-id="96dce-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="96dce-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="96dce-106">Exécute une ou plusieurs fois une liste d’instructions, sous réserve d’une condition while ou until.</span><span class="sxs-lookup"><span data-stu-id="96dce-106">Runs a statement list one or more times, subject to a While or Until condition.</span></span>

## <a name="long-description"></a><span data-ttu-id="96dce-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="96dce-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="96dce-108">Le mot clé do fonctionne avec le mot clé While ou le mot clé Until pour exécuter les instructions dans un bloc de script, sous réserve d’une condition.</span><span class="sxs-lookup"><span data-stu-id="96dce-108">The Do keyword works with the While keyword or the Until keyword to run the statements in a script block, subject to a condition.</span></span> <span data-ttu-id="96dce-109">Contrairement à la boucle while associée, le bloc de script dans une boucle do s’exécute toujours au moins une fois.</span><span class="sxs-lookup"><span data-stu-id="96dce-109">Unlike the related While loop, the script block in a Do loop always runs at least once.</span></span>

<span data-ttu-id="96dce-110">Une boucle **do-while** est une variété de la boucle while.</span><span class="sxs-lookup"><span data-stu-id="96dce-110">A **Do-While** loop is a variety of the While loop.</span></span> <span data-ttu-id="96dce-111">Dans une boucle **do-while** , la condition est évaluée après l’exécution du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="96dce-111">In a **Do-While** loop, the condition is evaluated after the script block has run.</span></span> <span data-ttu-id="96dce-112">Comme dans une boucle while, le bloc de script est répété tant que la condition prend la valeur true.</span><span class="sxs-lookup"><span data-stu-id="96dce-112">As in a While loop, the script block is repeated as long as the condition evaluates to true.</span></span>

<span data-ttu-id="96dce-113">À l’instar d’une boucle **do-while** , une boucle **Do-Until** s’exécute toujours au moins une fois avant que la condition soit évaluée.</span><span class="sxs-lookup"><span data-stu-id="96dce-113">Like a **Do-While** loop, a **Do-Until** loop always runs at least once before the condition is evaluated.</span></span> <span data-ttu-id="96dce-114">Toutefois, le bloc de script s’exécute uniquement lorsque la condition a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="96dce-114">However, the script block runs only while the condition is false.</span></span>

<span data-ttu-id="96dce-115">Les mots clés de contrôle de *continuation continue* et *break* peuvent être utilisés dans une boucle **do-while** ou dans une boucle **Do-Until** .</span><span class="sxs-lookup"><span data-stu-id="96dce-115">The *Continue* and *Break* flow control keywords can be used in a **Do-While** loop or in a **Do-Until** loop.</span></span>

### <a name="syntax"></a><span data-ttu-id="96dce-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96dce-116">Syntax</span></span>

<span data-ttu-id="96dce-117">L’exemple suivant illustre la syntaxe de l’instruction **do-while** :</span><span class="sxs-lookup"><span data-stu-id="96dce-117">The following shows the syntax of the **Do-While** statement:</span></span>

```powershell
do {<statement list>} while (<condition>)
```

<span data-ttu-id="96dce-118">L’exemple suivant illustre la syntaxe de l’instruction **Do-Until** :</span><span class="sxs-lookup"><span data-stu-id="96dce-118">The following shows the syntax of the **Do-Until** statement:</span></span>

```powershell
do {<statement list>} until (<condition>)
```

<span data-ttu-id="96dce-119">La liste d’instructions contient une ou plusieurs instructions qui s’exécutent chaque fois que la boucle est entrée ou répétée.</span><span class="sxs-lookup"><span data-stu-id="96dce-119">The statement list contains one or more statements that run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="96dce-120">La partie condition de l’instruction correspond à true ou false.</span><span class="sxs-lookup"><span data-stu-id="96dce-120">The condition portion of the statement resolves to true or false.</span></span>

### <a name="example"></a><span data-ttu-id="96dce-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="96dce-121">Example</span></span>

<span data-ttu-id="96dce-122">L’exemple suivant d’une instruction do compte les éléments d’un tableau jusqu’à ce qu’il atteigne un élément avec une valeur de 0.</span><span class="sxs-lookup"><span data-stu-id="96dce-122">The following example of a Do statement counts the items in an array until it reaches an item with a value of 0.</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

<span data-ttu-id="96dce-123">L’exemple suivant utilise le mot clé until.</span><span class="sxs-lookup"><span data-stu-id="96dce-123">The following example uses the Until keyword.</span></span> <span data-ttu-id="96dce-124">Notez que l’opérateur différent de ( `-ne` ) est remplacé par l’opérateur égal à ( `-eq` ).</span><span class="sxs-lookup"><span data-stu-id="96dce-124">Notice that the not equal to operator (`-ne`) is replaced by the equal to operator (`-eq`).</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

<span data-ttu-id="96dce-125">L’exemple suivant écrit toutes les valeurs d’un tableau, en ignorant toute valeur inférieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="96dce-125">The following example writes all the values of an array, skipping any value that is less than zero.</span></span>

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a><span data-ttu-id="96dce-126">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="96dce-126">SEE ALSO</span></span>

[<span data-ttu-id="96dce-127">about_While</span><span class="sxs-lookup"><span data-stu-id="96dce-127">about_While</span></span>](about_While.md)

[<span data-ttu-id="96dce-128">about_Operators</span><span class="sxs-lookup"><span data-stu-id="96dce-128">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="96dce-129">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="96dce-129">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="96dce-130">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="96dce-130">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="96dce-131">about_Break</span><span class="sxs-lookup"><span data-stu-id="96dce-131">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="96dce-132">about_Continue</span><span class="sxs-lookup"><span data-stu-id="96dce-132">about_Continue</span></span>](about_Continue.md)
