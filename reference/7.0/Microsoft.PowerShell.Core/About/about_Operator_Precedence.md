---
description: Répertorie les opérateurs PowerShell par ordre de priorité.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: 8f0f69f2328343b9655ebd0d7515a469565ff5f5
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483097"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="6224d-104">À propos de la priorité des opérateurs</span><span class="sxs-lookup"><span data-stu-id="6224d-104">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="6224d-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="6224d-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="6224d-106">Répertorie les opérateurs PowerShell par ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="6224d-106">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="6224d-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="6224d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="6224d-108">Les opérateurs PowerShell vous permettent de construire des expressions simples, mais puissantes.</span><span class="sxs-lookup"><span data-stu-id="6224d-108">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="6224d-109">Cette rubrique répertorie les opérateurs dans l’ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="6224d-109">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="6224d-110">L’ordre de priorité est l’ordre dans lequel PowerShell évalue les opérateurs lorsque plusieurs opérateurs s’affichent dans la même expression.</span><span class="sxs-lookup"><span data-stu-id="6224d-110">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="6224d-111">Lorsque les opérateurs ont la même priorité, PowerShell les évalue de gauche à droite, tels qu’ils apparaissent dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="6224d-111">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="6224d-112">Les exceptions sont les opérateurs d’assignation, les opérateurs de conversion et les opérateurs de négation ( `!` , `-not` , `-bnot` ), qui sont évalués de droite à gauche.</span><span class="sxs-lookup"><span data-stu-id="6224d-112">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="6224d-113">Vous pouvez utiliser des boîtiers, tels que des parenthèses, pour remplacer l’ordre de priorité standard et forcer PowerShell à évaluer la partie fermée d’une expression avant une partie non comprise.</span><span class="sxs-lookup"><span data-stu-id="6224d-113">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="6224d-114">Dans la liste suivante, les opérateurs sont répertoriés dans l’ordre dans lequel ils sont évalués.</span><span class="sxs-lookup"><span data-stu-id="6224d-114">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="6224d-115">Les opérateurs sur la même ligne ou dans le même groupe ont une priorité égale.</span><span class="sxs-lookup"><span data-stu-id="6224d-115">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="6224d-116">La colonne opérateur répertorie les opérateurs.</span><span class="sxs-lookup"><span data-stu-id="6224d-116">The Operator column lists the operators.</span></span> <span data-ttu-id="6224d-117">La colonne référence répertorie la rubrique d’aide PowerShell dans laquelle l’opérateur est décrit.</span><span class="sxs-lookup"><span data-stu-id="6224d-117">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="6224d-118">Pour afficher la rubrique, tapez `get-help <topic-name>` .</span><span class="sxs-lookup"><span data-stu-id="6224d-118">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="6224d-119">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="6224d-119">OPERATOR</span></span>         |           <span data-ttu-id="6224d-120">FAIRE</span><span class="sxs-lookup"><span data-stu-id="6224d-120">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | <span data-ttu-id="6224d-121">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-121">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-122">`. ?.` (accès aux membres)</span><span class="sxs-lookup"><span data-stu-id="6224d-122">`. ?.` (member access)</span></span>   | <span data-ttu-id="6224d-123">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-123">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-124">`::` statique</span><span class="sxs-lookup"><span data-stu-id="6224d-124">`::` (static)</span></span>            | <span data-ttu-id="6224d-125">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-125">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-126">`[0] ?[0]` (opérateur d’index)</span><span class="sxs-lookup"><span data-stu-id="6224d-126">`[0] ?[0]` (index operator)</span></span> | <span data-ttu-id="6224d-127">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-127">[about_Operators][]</span></span>         |
| <span data-ttu-id="6224d-128">`[int]` (opérateurs de cast)</span><span class="sxs-lookup"><span data-stu-id="6224d-128">`[int]` (cast operators)</span></span> | <span data-ttu-id="6224d-129">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-129">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-130">`-split` unaire</span><span class="sxs-lookup"><span data-stu-id="6224d-130">`-split` (unary)</span></span>         | <span data-ttu-id="6224d-131">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="6224d-131">[about_Split][]</span></span>                |
| <span data-ttu-id="6224d-132">`-join` unaire</span><span class="sxs-lookup"><span data-stu-id="6224d-132">`-join` (unary)</span></span>          | <span data-ttu-id="6224d-133">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="6224d-133">[about_Join][]</span></span>                 |
| <span data-ttu-id="6224d-134">`,` (opérateur virgule)</span><span class="sxs-lookup"><span data-stu-id="6224d-134">`,` (comma operator)</span></span>     | <span data-ttu-id="6224d-135">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-135">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="6224d-136">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-136">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="6224d-137">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-137">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="6224d-138">`..` (opérateur de plage)</span><span class="sxs-lookup"><span data-stu-id="6224d-138">`..` (range operator)</span></span>    | <span data-ttu-id="6224d-139">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-139">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-140">`-f` (opérateur format)</span><span class="sxs-lookup"><span data-stu-id="6224d-140">`-f` (format operator)</span></span>   | <span data-ttu-id="6224d-141">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-141">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-142">`-` (unaire/négative)</span><span class="sxs-lookup"><span data-stu-id="6224d-142">`-` (unary/negative)</span></span>     | <span data-ttu-id="6224d-143">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-143">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="6224d-144">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-144">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="6224d-145">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-145">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="6224d-146">Le groupe d’opérateurs suivant a la même priorité.</span><span class="sxs-lookup"><span data-stu-id="6224d-146">The following group of operators have equal precedence.</span></span> <span data-ttu-id="6224d-147">Leurs variantes qui respectent la casse et qui ne respectent pas explicitement la casse ont la même priorité.</span><span class="sxs-lookup"><span data-stu-id="6224d-147">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="6224d-148">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="6224d-148">OPERATOR</span></span>          |           <span data-ttu-id="6224d-149">FAIRE</span><span class="sxs-lookup"><span data-stu-id="6224d-149">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="6224d-150">`-split` binaire2</span><span class="sxs-lookup"><span data-stu-id="6224d-150">`-split` (binary)</span></span>         | <span data-ttu-id="6224d-151">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="6224d-151">[about_Split][]</span></span>                |
| <span data-ttu-id="6224d-152">`-join` binaire2</span><span class="sxs-lookup"><span data-stu-id="6224d-152">`-join` (binary)</span></span>          | <span data-ttu-id="6224d-153">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="6224d-153">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="6224d-154">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-154">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="6224d-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-155">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="6224d-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-156">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="6224d-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-157">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="6224d-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-158">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="6224d-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-159">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="6224d-160">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-160">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="6224d-161">La liste reprend ici avec les opérateurs suivants dans l’ordre de priorité :</span><span class="sxs-lookup"><span data-stu-id="6224d-161">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="6224d-162">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="6224d-162">OPERATOR</span></span>                 |           <span data-ttu-id="6224d-163">FAIRE</span><span class="sxs-lookup"><span data-stu-id="6224d-163">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="6224d-164">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-164">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="6224d-165">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-165">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="6224d-166">Les éléments suivants ne sont pas des opérateurs true.</span><span class="sxs-lookup"><span data-stu-id="6224d-166">The following items are not true operators.</span></span> <span data-ttu-id="6224d-167">Elles font partie de la syntaxe de commande de PowerShell, et non de la syntaxe des expressions.</span><span class="sxs-lookup"><span data-stu-id="6224d-167">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="6224d-168">L’assignation est toujours la dernière action qui se produit.</span><span class="sxs-lookup"><span data-stu-id="6224d-168">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="6224d-169">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="6224d-169">SYNTAX</span></span>                   |           <span data-ttu-id="6224d-170">FAIRE</span><span class="sxs-lookup"><span data-stu-id="6224d-170">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="6224d-171">`.` (point-source)</span><span class="sxs-lookup"><span data-stu-id="6224d-171">`.` (dot-source)</span></span>                        | <span data-ttu-id="6224d-172">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-172">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-173">`&` invoqu</span><span class="sxs-lookup"><span data-stu-id="6224d-173">`&` (call)</span></span>                              | <span data-ttu-id="6224d-174">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-174">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-175">`? <if-true> : <if-false>` (Opérateur ternaire)</span><span class="sxs-lookup"><span data-stu-id="6224d-175">`? <if-true> : <if-false>` (Ternary operator)</span></span> | <span data-ttu-id="6224d-176">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-176">[about_Operators][]</span></span>      |
| <span data-ttu-id="6224d-177">`??` (opérateur de coalesage null)</span><span class="sxs-lookup"><span data-stu-id="6224d-177">`??` (null-coalese operator)</span></span>            | <span data-ttu-id="6224d-178">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-178">[about_Operators][]</span></span>            |
| <span data-ttu-id="6224d-179"><code>&#124;</code> (opérateur de pipeline)</span><span class="sxs-lookup"><span data-stu-id="6224d-179"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="6224d-180">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-180">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="6224d-181">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="6224d-181">[about_Redirection][]</span></span>          |
| <span data-ttu-id="6224d-182"><code>&& &#124;&#124;</code> (opérateurs de chaîne de pipeline)</span><span class="sxs-lookup"><span data-stu-id="6224d-182"><code>&& &#124;&#124;</code> (pipeline chain operators)</span></span> | <span data-ttu-id="6224d-183">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-183">[about_Operators][]</span></span> |
| `= += -= *= /= %= ??=`                  | <span data-ttu-id="6224d-184">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-184">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="6224d-185">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6224d-185">EXAMPLES</span></span>

<span data-ttu-id="6224d-186">Les deux commandes suivantes montrent les opérateurs arithmétiques et l’effet de l’utilisation de parenthèses pour forcer PowerShell à évaluer d’abord la partie fermée de l’expression.</span><span class="sxs-lookup"><span data-stu-id="6224d-186">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="6224d-187">L’exemple suivant obtient les fichiers texte en lecture seule à partir du répertoire local et les enregistre dans la `$read_only` variable.</span><span class="sxs-lookup"><span data-stu-id="6224d-187">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="6224d-188">Elle est équivalente à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6224d-188">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="6224d-189">Étant donné que l’opérateur de pipeline ( `|` ) a une priorité plus élevée que l’opérateur d’assignation ( `=` ), les fichiers que l' `Get-ChildItem` applet de commande obtient sont envoyés à l' `Where-Object` applet de commande pour le filtrage avant de les assigner à la `$read_only` variable.</span><span class="sxs-lookup"><span data-stu-id="6224d-189">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="6224d-190">L’exemple suivant montre que l’opérateur d’index est prioritaire sur l’opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="6224d-190">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="6224d-191">Cette expression crée un tableau de trois chaînes.</span><span class="sxs-lookup"><span data-stu-id="6224d-191">This expression creates an array of three strings.</span></span> <span data-ttu-id="6224d-192">Elle utilise ensuite l’opérateur index avec la valeur 0 pour sélectionner le premier objet dans le tableau, qui est la première chaîne.</span><span class="sxs-lookup"><span data-stu-id="6224d-192">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="6224d-193">Enfin, il convertit l’objet sélectionné en chaîne.</span><span class="sxs-lookup"><span data-stu-id="6224d-193">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="6224d-194">Dans ce cas, le cast n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="6224d-194">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="6224d-195">Cette expression utilise des parenthèses pour forcer l’opération de conversion avant la sélection de l’index.</span><span class="sxs-lookup"><span data-stu-id="6224d-195">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="6224d-196">Par conséquent, le tableau entier est casté en une chaîne (unique).</span><span class="sxs-lookup"><span data-stu-id="6224d-196">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="6224d-197">Ensuite, l’opérateur index sélectionne le premier élément dans le tableau de chaînes, qui est le premier caractère.</span><span class="sxs-lookup"><span data-stu-id="6224d-197">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="6224d-198">Dans l’exemple suivant, étant donné que l' `-gt` opérateur (supérieur à) a une priorité plus élevée que l' `-and` opérateur (and logique), le résultat de l’expression est false.</span><span class="sxs-lookup"><span data-stu-id="6224d-198">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="6224d-199">Elle est équivalente à l’expression suivante.</span><span class="sxs-lookup"><span data-stu-id="6224d-199">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="6224d-200">Si l’opérateur-and a une priorité plus élevée, la réponse est TRUE.</span><span class="sxs-lookup"><span data-stu-id="6224d-200">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="6224d-201">Toutefois, cet exemple illustre un principe important de la gestion de la priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="6224d-201">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="6224d-202">Lorsqu’une expression est difficile à interpréter par des personnes, utilisez des parenthèses pour forcer l’ordre d’évaluation, même lorsqu’elle force la priorité des opérateurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="6224d-202">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="6224d-203">Les parenthèses rendent vos intentions claires pour les personnes qui lisent et gèrent vos scripts.</span><span class="sxs-lookup"><span data-stu-id="6224d-203">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="6224d-204">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="6224d-204">SEE ALSO</span></span>

<span data-ttu-id="6224d-205">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-205">[about_Operators][]</span></span>

<span data-ttu-id="6224d-206">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-206">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="6224d-207">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-207">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="6224d-208">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-208">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="6224d-209">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="6224d-209">[about_Join][]</span></span>

<span data-ttu-id="6224d-210">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="6224d-210">[about_Redirection][]</span></span>

<span data-ttu-id="6224d-211">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="6224d-211">[about_Scopes][]</span></span>

<span data-ttu-id="6224d-212">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="6224d-212">[about_Split][]</span></span>

<span data-ttu-id="6224d-213">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="6224d-213">[about_Type_Operators][]</span></span>

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
