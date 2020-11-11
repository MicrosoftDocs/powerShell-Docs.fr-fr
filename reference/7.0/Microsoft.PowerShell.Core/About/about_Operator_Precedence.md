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
# <a name="about-operator-precedence"></a>À propos de la priorité des opérateurs

## <a name="short-description"></a>DESCRIPTION COURTE
Répertorie les opérateurs PowerShell par ordre de priorité.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les opérateurs PowerShell vous permettent de construire des expressions simples, mais puissantes. Cette rubrique répertorie les opérateurs dans l’ordre de priorité. L’ordre de priorité est l’ordre dans lequel PowerShell évalue les opérateurs lorsque plusieurs opérateurs s’affichent dans la même expression.

Lorsque les opérateurs ont la même priorité, PowerShell les évalue de gauche à droite, tels qu’ils apparaissent dans l’expression. Les exceptions sont les opérateurs d’assignation, les opérateurs de conversion et les opérateurs de négation ( `!` , `-not` , `-bnot` ), qui sont évalués de droite à gauche.

Vous pouvez utiliser des boîtiers, tels que des parenthèses, pour remplacer l’ordre de priorité standard et forcer PowerShell à évaluer la partie fermée d’une expression avant une partie non comprise.

Dans la liste suivante, les opérateurs sont répertoriés dans l’ordre dans lequel ils sont évalués. Les opérateurs sur la même ligne ou dans le même groupe ont une priorité égale.

La colonne opérateur répertorie les opérateurs. La colonne référence répertorie la rubrique d’aide PowerShell dans laquelle l’opérateur est décrit. Pour afficher la rubrique, tapez `get-help <topic-name>` .

|         OPERATOR         |           FAIRE            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | [about_Operators][]            |
| `. ?.` (accès aux membres)   | [about_Operators][]            |
| `::` statique            | [about_Operators][]            |
| `[0] ?[0]` (opérateur d’index) | [about_Operators][]         |
| `[int]` (opérateurs de cast) | [about_Operators][]            |
| `-split` unaire         | [about_Split][]                |
| `-join` unaire          | [about_Join][]                 |
| `,` (opérateur virgule)     | [about_Operators][]            |
| `++ --`                  | [about_Assignment_Operators][] |
| `! -not`                 | [about_Logical_Operators][]    |
| `..` (opérateur de plage)    | [about_Operators][]            |
| `-f` (opérateur format)   | [about_Operators][]            |
| `-` (unaire/négative)     | [about_Arithmetic_Operators][] |
| `* / %`                  | [about_Arithmetic_Operators][] |
| `+ -`                    | [about_Arithmetic_Operators][] |

Le groupe d’opérateurs suivant a la même priorité. Leurs variantes qui respectent la casse et qui ne respectent pas explicitement la casse ont la même priorité.

|         OPERATOR          |           FAIRE            |
| ------------------------- | ------------------------------ |
| `-split` binaire2         | [about_Split][]                |
| `-join` binaire2          | [about_Join][]                 |
| `-is -isnot -as`          | [about_Type_Operators][]       |
| `-eq -ne -gt -gt -lt -le` | [about_Comparison_Operators][] |
| `-like -notlike`          | [about_Comparison_Operators][] |
| `-match -notmatch`        | [about_Comparison_Operators][] |
| `-in -notIn`              | [about_Comparison_Operators][] |
| `-contains -notContains`  | [about_Comparison_Operators][] |
| `-replace`                | [about_Comparison_Operators][] |

La liste reprend ici avec les opérateurs suivants dans l’ordre de priorité :

|                OPERATOR                 |           FAIRE            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | [about_Arithmetic_Operators][] |
| `-and -or -xor`                         | [about_Logical_Operators][]    |

Les éléments suivants ne sont pas des opérateurs true. Elles font partie de la syntaxe de commande de PowerShell, et non de la syntaxe des expressions. L’assignation est toujours la dernière action qui se produit.

|                SYNTAXE                   |           FAIRE            |
| --------------------------------------- | ------------------------------ |
| `.` (point-source)                        | [about_Operators][]            |
| `&` invoqu                              | [about_Operators][]            |
| `? <if-true> : <if-false>` (Opérateur ternaire) | [about_Operators][]      |
| `??` (opérateur de coalesage null)            | [about_Operators][]            |
| <code>&#124;</code> (opérateur de pipeline) | [about_Operators][]            |
| `> >> 2> 2>> 2>&1`                      | [about_Redirection][]          |
| <code>&& &#124;&#124;</code> (opérateurs de chaîne de pipeline) | [about_Operators][] |
| `= += -= *= /= %= ??=`                  | [about_Assignment_Operators][] |

## <a name="examples"></a>EXEMPLES

Les deux commandes suivantes montrent les opérateurs arithmétiques et l’effet de l’utilisation de parenthèses pour forcer PowerShell à évaluer d’abord la partie fermée de l’expression.

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

L’exemple suivant obtient les fichiers texte en lecture seule à partir du répertoire local et les enregistre dans la `$read_only` variable.

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

Elle est équivalente à l’exemple suivant.

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

Étant donné que l’opérateur de pipeline ( `|` ) a une priorité plus élevée que l’opérateur d’assignation ( `=` ), les fichiers que l' `Get-ChildItem` applet de commande obtient sont envoyés à l' `Where-Object` applet de commande pour le filtrage avant de les assigner à la `$read_only` variable.

L’exemple suivant montre que l’opérateur d’index est prioritaire sur l’opérateur de conversion.

Cette expression crée un tableau de trois chaînes. Elle utilise ensuite l’opérateur index avec la valeur 0 pour sélectionner le premier objet dans le tableau, qui est la première chaîne. Enfin, il convertit l’objet sélectionné en chaîne. Dans ce cas, le cast n’a aucun effet.

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

Cette expression utilise des parenthèses pour forcer l’opération de conversion avant la sélection de l’index. Par conséquent, le tableau entier est casté en une chaîne (unique). Ensuite, l’opérateur index sélectionne le premier élément dans le tableau de chaînes, qui est le premier caractère.

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

Dans l’exemple suivant, étant donné que l' `-gt` opérateur (supérieur à) a une priorité plus élevée que l' `-and` opérateur (and logique), le résultat de l’expression est false.

```powershell
PS> 2 -gt 4 -and 1
False
```

Elle est équivalente à l’expression suivante.

```powershell
PS> (2 -gt 4) -and 1
False
```

Si l’opérateur-and a une priorité plus élevée, la réponse est TRUE.

```powershell
PS> 2 -gt (4 -and 1)
True
```

Toutefois, cet exemple illustre un principe important de la gestion de la priorité des opérateurs. Lorsqu’une expression est difficile à interpréter par des personnes, utilisez des parenthèses pour forcer l’ordre d’évaluation, même lorsqu’elle force la priorité des opérateurs par défaut. Les parenthèses rendent vos intentions claires pour les personnes qui lisent et gèrent vos scripts.

## <a name="see-also"></a>VOIR AUSSI

[about_Operators][]

[about_Assignment_Operators][]

[about_Comparison_Operators][]

[about_Arithmetic_Operators][]

[about_Join][]

[about_Redirection][]

[about_Scopes][]

[about_Split][]

[about_Type_Operators][]

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
