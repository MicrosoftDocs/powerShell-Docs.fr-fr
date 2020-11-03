---
description: Décrit une instruction de langage que vous pouvez utiliser pour exécuter un bloc de commande en fonction des résultats d’un test conditionnel.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 4008c1c8738b6911949d79882cc6909be2edbe97
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207373"
---
# <a name="about-while"></a><span data-ttu-id="845a8-104">À propos de while</span><span class="sxs-lookup"><span data-stu-id="845a8-104">About While</span></span>

## <a name="short-description"></a><span data-ttu-id="845a8-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="845a8-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="845a8-106">Décrit une instruction de langage que vous pouvez utiliser pour exécuter un bloc de commande en fonction des résultats d’un test conditionnel.</span><span class="sxs-lookup"><span data-stu-id="845a8-106">Describes a language statement that you can use to run a command block based on the results of a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="845a8-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="845a8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="845a8-108">L’instruction while (également appelée « boucle while ») est une construction de langage permettant de créer une boucle qui exécute des commandes dans un bloc de commande tant qu’un test conditionnel prend la valeur true.</span><span class="sxs-lookup"><span data-stu-id="845a8-108">The While statement (also known as a While loop) is a language construct for creating a loop that runs commands in a command block as long as a conditional test evaluates to true.</span></span> <span data-ttu-id="845a8-109">L’instruction while est plus facile à construire qu’une instruction for, car sa syntaxe est moins compliquée.</span><span class="sxs-lookup"><span data-stu-id="845a8-109">The While statement is easier to construct than a For statement because its syntax is less complicated.</span></span> <span data-ttu-id="845a8-110">En outre, il est plus souple que l’instruction foreach, car vous spécifiez un test conditionnel dans l’instruction while pour contrôler le nombre de fois que la boucle s’exécute.</span><span class="sxs-lookup"><span data-stu-id="845a8-110">In addition, it is more flexible than the Foreach statement because you specify a conditional test in the While statement to control how many times the loop runs.</span></span>

<span data-ttu-id="845a8-111">L’exemple suivant illustre la syntaxe de l’instruction while :</span><span class="sxs-lookup"><span data-stu-id="845a8-111">The following shows the While statement syntax:</span></span>

```powershell
while (<condition>){<statement list>}
```

<span data-ttu-id="845a8-112">Quand vous exécutez une instruction while, PowerShell évalue la `<condition>` section de l’instruction avant d’entrer dans la `<statement list>` section.</span><span class="sxs-lookup"><span data-stu-id="845a8-112">When you run a While statement, PowerShell evaluates the `<condition>` section of the statement before entering the `<statement list>` section.</span></span> <span data-ttu-id="845a8-113">La partie condition de l’instruction correspond à true ou false.</span><span class="sxs-lookup"><span data-stu-id="845a8-113">The condition portion of the statement resolves to either true or false.</span></span> <span data-ttu-id="845a8-114">Tant que la condition reste vraie, PowerShell réexécute la `<statement list>` section.</span><span class="sxs-lookup"><span data-stu-id="845a8-114">As long as the condition remains true, PowerShell reruns the `<statement list>` section.</span></span>

<span data-ttu-id="845a8-115">La `<statement list>` section de l’instruction contient une ou plusieurs commandes qui sont exécutées chaque fois que la boucle est entrée ou répétée.</span><span class="sxs-lookup"><span data-stu-id="845a8-115">The `<statement list>` section of the statement contains one or more commands that are run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="845a8-116">Par exemple, l’instruction while suivante affiche les nombres 1 à 3 Si la variable $val n’a pas été créée ou si la $val variable a été créée et initialisée à 0.</span><span class="sxs-lookup"><span data-stu-id="845a8-116">For example, the following While statement displays the numbers 1 through 3 if the $val variable has not been created or if the $val variable has been created and initialized to 0.</span></span>

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

<span data-ttu-id="845a8-117">Dans cet exemple, la condition ($val n’est pas égale à 3) est vraie alors que $val \= 0, 1, 2.</span><span class="sxs-lookup"><span data-stu-id="845a8-117">In this example, the condition ($val is not equal to 3) is true while $val \= 0, 1, 2.</span></span> <span data-ttu-id="845a8-118">Chaque fois que la boucle est utilisée, $val est incrémenté de 1 à l’aide de l' \+ \+ opérateur d’incrémentation unaire ($Val \+ \+ ).</span><span class="sxs-lookup"><span data-stu-id="845a8-118">Each time through the loop, $val is incremented by 1 using the \+\+ unary increment operator ($val\+\+).</span></span> <span data-ttu-id="845a8-119">La dernière fois dans la boucle, $val \= 3.</span><span class="sxs-lookup"><span data-stu-id="845a8-119">The last time through the loop, $val \= 3.</span></span> <span data-ttu-id="845a8-120">Lorsque $val est égal à 3, l’instruction de condition prend la valeur false et la boucle se termine.</span><span class="sxs-lookup"><span data-stu-id="845a8-120">When $val equals 3, the condition statement evaluates to false, and the loop exits.</span></span>

<span data-ttu-id="845a8-121">Pour écrire facilement cette commande à l’invite de commandes PowerShell, vous pouvez l’entrer de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="845a8-121">To conveniently write this command at the PowerShell command prompt, you can enter it in the following way:</span></span>

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

<span data-ttu-id="845a8-122">Notez que le point-virgule sépare la première commande qui ajoute 1 à $val de la deuxième commande qui écrit la valeur de $val dans la console.</span><span class="sxs-lookup"><span data-stu-id="845a8-122">Notice that the semicolon separates the first command that adds 1 to $val from the second command that writes the value of $val to the console.</span></span>

## <a name="see-also"></a><span data-ttu-id="845a8-123">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="845a8-123">SEE ALSO</span></span>

[<span data-ttu-id="845a8-124">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="845a8-124">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="845a8-125">about_Do</span><span class="sxs-lookup"><span data-stu-id="845a8-125">about_Do</span></span>](about_Do.md)

[<span data-ttu-id="845a8-126">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="845a8-126">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="845a8-127">about_For</span><span class="sxs-lookup"><span data-stu-id="845a8-127">about_For</span></span>](about_For.md)

[<span data-ttu-id="845a8-128">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="845a8-128">about_Language_Keywords</span></span>](about_Language_Keywords.md)
