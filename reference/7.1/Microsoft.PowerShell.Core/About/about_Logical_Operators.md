---
description: Décrit les opérateurs qui connectent des instructions dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: f8db290b87043451241613358a2f6d4fdf1dc342
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206510"
---
# <a name="about_logical_operators"></a>about_Logical_Operators

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit les opérateurs qui connectent des instructions dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les opérateurs logiques PowerShell connectent des expressions et des instructions, ce qui vous permet d’utiliser une expression unique pour tester plusieurs conditions.

Par exemple, l’instruction suivante utilise l’opérateur and et l’opérateur or pour connecter trois instructions conditionnelles. L’instruction est vraie uniquement lorsque la valeur de $a est supérieure à la valeur de $b, et que $a ou $b est inférieur à
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

PowerShell prend en charge les opérateurs logiques suivants.

|Opérateur|Description                        |Exemple                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |AND logique. TRUE lorsque les deux        |`(1 -eq 1) -and (1 -eq 2)`|
|        |les instructions sont vraies.               |`False`                   |
|`-or`   |OR logique. TRUE lorsque       |`(1 -eq 1) -or (1 -eq 2)` |
|        |l’instruction a la valeur TRUE.                 |`True`                    |
|`-xor`  |OR exclusif logique. TRUE lorsque    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |une seule instruction est vraie         |`False`                   |
|`-not`  |Not logique. Inverse l’instruction |`-not (1 -eq 1)`          |
|        |Cela suit.                      |`False`                   |
|`!`     |Identique à `-not`                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 Remarque :

Les exemples précédents utilisent également l’opérateur de comparaison égal à `-eq` . Pour plus d’informations, consultez [about_Comparison_Operators](about_Comparison_Operators.md). Les exemples utilisent également les valeurs booléennes des entiers. L’entier 0 a la valeur FALSe. Tous les autres entiers ont la valeur TRUE.

La syntaxe des opérateurs logiques est la suivante :

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

Les instructions qui utilisent les opérateurs logiques retournent des valeurs booléennes (TRUE ou FALSe).

Les opérateurs logiques PowerShell évaluent uniquement les instructions requises pour déterminer la valeur de vérité de l’instruction. Si l’opérande gauche dans une instruction qui contient l’opérateur and est FALSe, l’opérande de droite n’est pas évalué.
Si l’opérande gauche dans une instruction qui contient l’instruction ou a la valeur TRUE, l’opérande de droite n’est pas évalué. Par conséquent, vous pouvez utiliser ces instructions de la même façon que vous utilisez l' `If` instruction.

## <a name="see-also"></a>VOIR AUSSI

[about_Operators](about_Operators.md)

[Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[about_Comparison_operators](about_Comparison_Operators.md)

[about_If](about_If.md)

