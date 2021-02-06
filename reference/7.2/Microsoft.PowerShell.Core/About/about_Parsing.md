---
description: Décrit comment PowerShell analyse les commandes.
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: a5ce30b2ad9aff7dd8b54e7a62937013a61cd278
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603494"
---
# <a name="about-parsing"></a>À propos de l’analyse

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit comment PowerShell analyse les commandes.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Lorsque vous entrez une commande à l’invite de commandes, PowerShell divise le texte de la commande en une série de segments appelés _jetons_ , puis détermine comment interpréter chaque jeton.

Par exemple, si vous tapez :

```powershell
Write-Host book
```

PowerShell divise la commande en deux jetons, `Write-Host` et `book` , et interprète chaque jeton indépendamment à l’aide de l’un des deux modes d’analyse principaux : le mode expression et le mode argument.

> [!NOTE]
> Comme PowerShell analyse l’entrée de commande, il tente de résoudre les noms de commande en applets de commande ou exécutables natifs. Si un nom de commande n’a pas de correspondance exacte, PowerShell ajoute `Get-` à la commande en tant que verbe par défaut. Par exemple, PowerShell est analysé `Process` comme `Get-Process` . Il n’est pas recommandé d’utiliser cette fonctionnalité pour les raisons suivantes :
>
> - C’est inefficace. PowerShell effectue une recherche à plusieurs moments.
> - Les programmes externes portant le même nom sont résolus en premier, ce qui signifie que vous ne pouvez pas exécuter l’applet de commande prévue.
> - `Get-Help` et `Get-Command` ne reconnaissent pas les noms sans verbe.

### <a name="expression-mode"></a>Mode expression

Le mode expression est conçu pour combiner des expressions, requis pour la manipulation de valeurs dans un langage de script. Les expressions sont des représentations de valeurs dans la syntaxe PowerShell et peuvent être simples ou composites, par exemple :

Les expressions littérales sont des représentations directes de leurs valeurs : 

```powershell
'hello', 32
```

Les expressions de variable comportent la valeur de la variable qu’elles référencent : 

```powershell
$x, $script:path
```
Les opérateurs combinent d’autres expressions à des fins d’évaluation : 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- Les _littéraux de chaîne de caractères_ doivent être placés entre guillemets.
- Les _nombres_ sont traités comme des valeurs numériques plutôt que comme une série de caractères (à moins d’être placés dans une séquence d’échappement).
- Les _opérateurs_, y compris les opérateurs unaires tels que et `-` et les `-not` opérateurs binaires comme `+` et `-gt` , sont interprétés comme des opérateurs et appliquent leurs opérations respectives sur leurs arguments (opérandes).
- Les _expressions d’attribut et de conversion_ sont analysées en tant qu’expressions et appliquées à des expressions subordonnées, par exemple `[int] '7'` .
- Les _références de variable_ sont évaluées en fonction de leurs valeurs, mais la _projection_ (c’est-à-dire le collage de jeux de paramètres préremplis) est interdite et provoque une erreur d’analyse.
- Tout autre objet sera traité comme une commande à appeler.

### <a name="argument-mode"></a>Mode d’argument

Lors de l’analyse, PowerShell cherche d’abord à interpréter l’entrée en tant qu’expression. Mais lorsqu’un appel de commande est rencontré, l’analyse continue en mode argument.

Le mode d’argument est conçu pour l’analyse des arguments et des paramètres pour les commandes dans un environnement de Shell. Toute entrée est traitée comme une chaîne développable, sauf si elle utilise l’une des syntaxes suivantes :

- Le signe dollar ( `$` ) commence une référence variable (uniquement si elle est suivie d’un nom de variable valide, sinon elle est interprétée comme faisant partie de la chaîne développable).
- Les guillemets ( `'` et `"` ) commencent les valeurs de chaîne
- Les parenthèses (et) délimitent `(` les `)` nouvelles expressions.
- L’opérateur de sous-expression ( `$(` ...) délimite les `)` expressions incorporées.
- `{`Les `}` nouveaux blocs de script sont délimitées par des accolades (et).
- La fonction initiale arobase ( `@` ) commence par les syntaxes d’expressions telles que la projection ( `@args` ), les tableaux ( `@(1,2,3)` ) et les tables de hachage ( `@{a=1;b=2}` ).
- Les virgules ( `,` ) présentent des listes passées en tant que tableaux, sauf lorsque la commande à appeler est une application native, auquel cas elles sont interprétées comme faisant partie de la chaîne développable. Les virgules initiales, consécutives ou de fin ne sont pas prises en charge.

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
Les valeurs des expressions incorporées sont converties en chaînes.

Le tableau suivant fournit plusieurs exemples de valeurs traitées en mode expression et en mode argument, ainsi que l’évaluation de ces valeurs. Nous supposons que la valeur de la variable `a` est `4` .

|       Exemple        |    Mode    |      Résultats       |
| -------------------- | ---------- | ----------------- |
| `2`                  | Expression | 2 (entier)       |
| `` `2``              | Expression | "2" (commande)     |
| `echo 2`             | Expression | 2 (entier)       |
| `2+2`                | Expression | 4 (entier)       |
| `echo 2+2`           | Argument   | "2 + 2" (chaîne)    |
| `echo(2+2)`          | Expression | 4 (entier)       |
| `$a`                 | Expression | 4 (entier)       |
| `echo $a`            | Expression | 4 (entier)       |
| `$a+2`               | Expression | 6 (entier)       |
| `echo $a+2`          | Argument   | 4 + 2 (chaîne)      |
| `$-`                 | Argument   | "$-" (commande)    |
| `echo $-`            | Argument   | "$-" (chaîne)     |
| `a$a`                | Expression | « a $ a » (commande)   |
| `echo a$a`           | Argument   | « A4 » (chaîne)     |
| `a'$a'`              | Expression | « a $ a » (commande)   |
| `echo a'$a'`         | Argument   | « a $ a » (chaîne)    |
| `a"$a"`              | Expression | « a $ a » (commande)   |
| `echo a"$a"`         | Argument   | « A4 » (chaîne)     |
| `a$(2)`              | Expression | « a $ (2) » (commande) |
| `echo a$(2)`         | Argument   | « a2 » (chaîne)     |

Chaque jeton peut être interprété comme un type d’objet, tel qu’une valeur booléenne ou une chaîne. PowerShell tente de déterminer le type de l’objet à partir de l’expression.
Le type d’objet dépend du type de paramètre attendu par une commande et de la manière dont PowerShell sait comment convertir l’argument en type correct. Le tableau suivant présente plusieurs exemples des types affectés aux valeurs retournées par les expressions.

|       Exemple          |    Mode    |     Résultats      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | argument   | «  ! 1 » (chaîne)   |
| `Write-Output (!1)`    | expression | False (booléen) |
| `Write-Output (2)`     | expression | 2 (entier)     |
| `Set-Variable AB A,B`  | argument   | 'A', 'B' (tableau) |
| `CMD /CECHO A,B`       | argument   | 'A, B' (chaîne)  |
| `CMD /CECHO $AB`       | expression | 'A', 'B' (tableau) |
| `CMD /CECHO :$AB`      | argument   | ' : A B' (chaîne) |

Le symbole d’analyse d’arrêt ( `--%` ), introduit dans powershell 3,0, indique à PowerShell de s’abstenir d’interpréter l’entrée comme des commandes ou des expressions PowerShell.

Quand vous appelez un programme exécutable dans PowerShell, placez le symbole d’analyse des arrêts avant les arguments du programme. Cette technique est beaucoup plus facile que d’utiliser des caractères d’échappement pour éviter une mauvaise interprétation.

Lorsqu’il rencontre un symbole d’analyse d’arrêt, PowerShell traite les caractères restants de la ligne comme un littéral. La seule interprétation qu’il effectue est la substitution de valeurs pour les variables d’environnement qui utilisent la notation Windows standard, telle que `%USERPROFILE%` .

Le symbole d’analyse Stop est effectif uniquement jusqu’au saut de ligne ou au caractère de pipeline suivant. Vous ne pouvez pas utiliser un caractère de continuation ( `` ` `` ) pour étendre son effet ou utiliser un délimiteur de commande ( `;` ) pour terminer son effet.

Par exemple, la commande suivante appelle le programme **icacls** .

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

Pour exécuter cette commande dans PowerShell 2,0, vous devez utiliser des caractères d’échappement pour empêcher PowerShell d’interpréter les parenthèses.

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

À compter de PowerShell 3,0, vous pouvez utiliser le symbole d’analyse stop.

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell envoie la chaîne de commande suivante au programme **icacls** :

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> Symbole d’analyse Stop uniquement destiné à être utilisé sur les plateformes Windows.

## <a name="see-also"></a>VOIR AUSSI

[about_Command_Syntax](about_Command_Syntax.md)
