---
description: Répertorie les opérateurs PowerShell par ordre de priorité.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: 602a99d6acee63177d45425d90f8fcd47766fb93
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207990"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="c05b2-104">À propos de la priorité des opérateurs</span><span class="sxs-lookup"><span data-stu-id="c05b2-104">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="c05b2-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="c05b2-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c05b2-106">Répertorie les opérateurs PowerShell par ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="c05b2-106">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="c05b2-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="c05b2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c05b2-108">Les opérateurs PowerShell vous permettent de construire des expressions simples, mais puissantes.</span><span class="sxs-lookup"><span data-stu-id="c05b2-108">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="c05b2-109">Cette rubrique répertorie les opérateurs dans l’ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="c05b2-109">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="c05b2-110">L’ordre de priorité est l’ordre dans lequel PowerShell évalue les opérateurs lorsque plusieurs opérateurs s’affichent dans la même expression.</span><span class="sxs-lookup"><span data-stu-id="c05b2-110">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="c05b2-111">Lorsque les opérateurs ont la même priorité, PowerShell les évalue de gauche à droite, tels qu’ils apparaissent dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="c05b2-111">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="c05b2-112">Les exceptions sont les opérateurs d’assignation, les opérateurs de conversion et les opérateurs de négation ( `!` , `-not` , `-bnot` ), qui sont évalués de droite à gauche.</span><span class="sxs-lookup"><span data-stu-id="c05b2-112">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="c05b2-113">Vous pouvez utiliser des boîtiers, tels que des parenthèses, pour remplacer l’ordre de priorité standard et forcer PowerShell à évaluer la partie fermée d’une expression avant une partie non comprise.</span><span class="sxs-lookup"><span data-stu-id="c05b2-113">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="c05b2-114">Dans la liste suivante, les opérateurs sont répertoriés dans l’ordre dans lequel ils sont évalués.</span><span class="sxs-lookup"><span data-stu-id="c05b2-114">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="c05b2-115">Les opérateurs sur la même ligne ou dans le même groupe ont une priorité égale.</span><span class="sxs-lookup"><span data-stu-id="c05b2-115">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="c05b2-116">La colonne opérateur répertorie les opérateurs.</span><span class="sxs-lookup"><span data-stu-id="c05b2-116">The Operator column lists the operators.</span></span> <span data-ttu-id="c05b2-117">La colonne référence répertorie la rubrique d’aide PowerShell dans laquelle l’opérateur est décrit.</span><span class="sxs-lookup"><span data-stu-id="c05b2-117">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="c05b2-118">Pour afficher la rubrique, tapez `get-help <topic-name>` .</span><span class="sxs-lookup"><span data-stu-id="c05b2-118">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="c05b2-119">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="c05b2-119">OPERATOR</span></span>         |           <span data-ttu-id="c05b2-120">FAIRE</span><span class="sxs-lookup"><span data-stu-id="c05b2-120">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() ()`             | <span data-ttu-id="c05b2-121">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-121">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-122">`.` (accès aux membres)</span><span class="sxs-lookup"><span data-stu-id="c05b2-122">`.` (member access)</span></span>      | <span data-ttu-id="c05b2-123">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-123">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-124">`::` statique</span><span class="sxs-lookup"><span data-stu-id="c05b2-124">`::` (static)</span></span>            | <span data-ttu-id="c05b2-125">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-125">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-126">`[0]` (opérateur d’index)</span><span class="sxs-lookup"><span data-stu-id="c05b2-126">`[0]` (index operator)</span></span>   | <span data-ttu-id="c05b2-127">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-127">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-128">`[int]` (opérateurs de cast)</span><span class="sxs-lookup"><span data-stu-id="c05b2-128">`[int]` (cast operators)</span></span> | <span data-ttu-id="c05b2-129">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-129">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-130">`-split` unaire</span><span class="sxs-lookup"><span data-stu-id="c05b2-130">`-split` (unary)</span></span>         | <span data-ttu-id="c05b2-131">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-131">[about_Split][]</span></span>                |
| <span data-ttu-id="c05b2-132">`-join` unaire</span><span class="sxs-lookup"><span data-stu-id="c05b2-132">`-join` (unary)</span></span>          | <span data-ttu-id="c05b2-133">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-133">[about_Join][]</span></span>                 |
| <span data-ttu-id="c05b2-134">`,` (opérateur virgule)</span><span class="sxs-lookup"><span data-stu-id="c05b2-134">`,` (comma operator)</span></span>     | <span data-ttu-id="c05b2-135">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-135">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="c05b2-136">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-136">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="c05b2-137">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-137">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="c05b2-138">`..` (opérateur de plage)</span><span class="sxs-lookup"><span data-stu-id="c05b2-138">`..` (range operator)</span></span>    | <span data-ttu-id="c05b2-139">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-139">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-140">`-f` (opérateur format)</span><span class="sxs-lookup"><span data-stu-id="c05b2-140">`-f` (format operator)</span></span>   | <span data-ttu-id="c05b2-141">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-141">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-142">`-` (unaire/négative)</span><span class="sxs-lookup"><span data-stu-id="c05b2-142">`-` (unary/negative)</span></span>     | <span data-ttu-id="c05b2-143">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-143">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="c05b2-144">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-144">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="c05b2-145">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-145">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="c05b2-146">Le groupe d’opérateurs suivant a la même priorité.</span><span class="sxs-lookup"><span data-stu-id="c05b2-146">The following group of operators have equal precedence.</span></span> <span data-ttu-id="c05b2-147">Leurs variantes qui respectent la casse et qui ne respectent pas explicitement la casse ont la même priorité.</span><span class="sxs-lookup"><span data-stu-id="c05b2-147">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="c05b2-148">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="c05b2-148">OPERATOR</span></span>          |           <span data-ttu-id="c05b2-149">FAIRE</span><span class="sxs-lookup"><span data-stu-id="c05b2-149">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="c05b2-150">`-split` binaire2</span><span class="sxs-lookup"><span data-stu-id="c05b2-150">`-split` (binary)</span></span>         | <span data-ttu-id="c05b2-151">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-151">[about_Split][]</span></span>                |
| <span data-ttu-id="c05b2-152">`-join` binaire2</span><span class="sxs-lookup"><span data-stu-id="c05b2-152">`-join` (binary)</span></span>          | <span data-ttu-id="c05b2-153">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-153">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="c05b2-154">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-154">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="c05b2-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-155">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="c05b2-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-156">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="c05b2-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-157">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="c05b2-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-158">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="c05b2-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-159">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="c05b2-160">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-160">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="c05b2-161">La liste reprend ici avec les opérateurs suivants dans l’ordre de priorité :</span><span class="sxs-lookup"><span data-stu-id="c05b2-161">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="c05b2-162">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="c05b2-162">OPERATOR</span></span>                 |           <span data-ttu-id="c05b2-163">FAIRE</span><span class="sxs-lookup"><span data-stu-id="c05b2-163">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="c05b2-164">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-164">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="c05b2-165">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-165">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="c05b2-166">Les éléments suivants ne sont pas des opérateurs true.</span><span class="sxs-lookup"><span data-stu-id="c05b2-166">The following items are not true operators.</span></span> <span data-ttu-id="c05b2-167">Elles font partie de la syntaxe de commande de PowerShell, et non de la syntaxe des expressions.</span><span class="sxs-lookup"><span data-stu-id="c05b2-167">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="c05b2-168">L’assignation est toujours la dernière action qui se produit.</span><span class="sxs-lookup"><span data-stu-id="c05b2-168">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="c05b2-169">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c05b2-169">SYNTAX</span></span>                   |           <span data-ttu-id="c05b2-170">FAIRE</span><span class="sxs-lookup"><span data-stu-id="c05b2-170">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="c05b2-171">`.` (point-source)</span><span class="sxs-lookup"><span data-stu-id="c05b2-171">`.` (dot-source)</span></span>                        | <span data-ttu-id="c05b2-172">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-172">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-173">`&` invoqu</span><span class="sxs-lookup"><span data-stu-id="c05b2-173">`&` (call)</span></span>                              | <span data-ttu-id="c05b2-174">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-174">[about_Operators][]</span></span>            |
| <span data-ttu-id="c05b2-175"><code>&#124;</code> (opérateur de pipeline)</span><span class="sxs-lookup"><span data-stu-id="c05b2-175"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="c05b2-176">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-176">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="c05b2-177">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-177">[about_Redirection][]</span></span>          |
| `= += -= *= /= %=`                      | <span data-ttu-id="c05b2-178">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-178">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="c05b2-179">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c05b2-179">EXAMPLES</span></span>

<span data-ttu-id="c05b2-180">Les deux commandes suivantes montrent les opérateurs arithmétiques et l’effet de l’utilisation de parenthèses pour forcer PowerShell à évaluer d’abord la partie fermée de l’expression.</span><span class="sxs-lookup"><span data-stu-id="c05b2-180">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="c05b2-181">L’exemple suivant obtient les fichiers texte en lecture seule à partir du répertoire local et les enregistre dans la `$read_only` variable.</span><span class="sxs-lookup"><span data-stu-id="c05b2-181">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="c05b2-182">Elle est équivalente à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c05b2-182">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="c05b2-183">Étant donné que l’opérateur de pipeline ( `|` ) a une priorité plus élevée que l’opérateur d’assignation ( `=` ), les fichiers que l' `Get-ChildItem` applet de commande obtient sont envoyés à l' `Where-Object` applet de commande pour le filtrage avant de les assigner à la `$read_only` variable.</span><span class="sxs-lookup"><span data-stu-id="c05b2-183">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="c05b2-184">L’exemple suivant montre que l’opérateur d’index est prioritaire sur l’opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="c05b2-184">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="c05b2-185">Cette expression crée un tableau de trois chaînes.</span><span class="sxs-lookup"><span data-stu-id="c05b2-185">This expression creates an array of three strings.</span></span> <span data-ttu-id="c05b2-186">Elle utilise ensuite l’opérateur index avec la valeur 0 pour sélectionner le premier objet dans le tableau, qui est la première chaîne.</span><span class="sxs-lookup"><span data-stu-id="c05b2-186">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="c05b2-187">Enfin, il convertit l’objet sélectionné en chaîne.</span><span class="sxs-lookup"><span data-stu-id="c05b2-187">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="c05b2-188">Dans ce cas, le cast n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="c05b2-188">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="c05b2-189">Cette expression utilise des parenthèses pour forcer l’opération de conversion avant la sélection de l’index.</span><span class="sxs-lookup"><span data-stu-id="c05b2-189">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="c05b2-190">Par conséquent, le tableau entier est casté en une chaîne (unique).</span><span class="sxs-lookup"><span data-stu-id="c05b2-190">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="c05b2-191">Ensuite, l’opérateur index sélectionne le premier élément dans le tableau de chaînes, qui est le premier caractère.</span><span class="sxs-lookup"><span data-stu-id="c05b2-191">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="c05b2-192">Dans l’exemple suivant, étant donné que l' `-gt` opérateur (supérieur à) a une priorité plus élevée que l' `-and` opérateur (and logique), le résultat de l’expression est false.</span><span class="sxs-lookup"><span data-stu-id="c05b2-192">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="c05b2-193">Elle est équivalente à l’expression suivante.</span><span class="sxs-lookup"><span data-stu-id="c05b2-193">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="c05b2-194">Si l’opérateur-and a une priorité plus élevée, la réponse est TRUE.</span><span class="sxs-lookup"><span data-stu-id="c05b2-194">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="c05b2-195">Toutefois, cet exemple illustre un principe important de la gestion de la priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="c05b2-195">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="c05b2-196">Lorsqu’une expression est difficile à interpréter par des personnes, utilisez des parenthèses pour forcer l’ordre d’évaluation, même lorsqu’elle force la priorité des opérateurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="c05b2-196">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="c05b2-197">Les parenthèses rendent vos intentions claires pour les personnes qui lisent et gèrent vos scripts.</span><span class="sxs-lookup"><span data-stu-id="c05b2-197">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="c05b2-198">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="c05b2-198">SEE ALSO</span></span>

<span data-ttu-id="c05b2-199">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-199">[about_Operators][]</span></span>

<span data-ttu-id="c05b2-200">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-200">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="c05b2-201">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-201">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="c05b2-202">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-202">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="c05b2-203">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-203">[about_Join][]</span></span>

<span data-ttu-id="c05b2-204">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-204">[about_Redirection][]</span></span>

<span data-ttu-id="c05b2-205">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-205">[about_Scopes][]</span></span>

<span data-ttu-id="c05b2-206">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-206">[about_Split][]</span></span>

<span data-ttu-id="c05b2-207">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c05b2-207">[about_Type_Operators][]</span></span>

<!-- reference links -->
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
