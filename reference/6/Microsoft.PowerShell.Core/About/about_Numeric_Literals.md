---
description: Les littéraux numériques et réels peuvent avoir des suffixes de type et de multiplicateur.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des littéraux numériques
ms.openlocfilehash: dc1a55dbec1f0de99e06011645e6884b37480233
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354827"
---
# <a name="about-numeric-literals"></a>À propos des littéraux numériques

Il existe deux types de littéraux numériques : entier et réel. Les deux peuvent avoir des suffixes de type et multiplicateur.

## <a name="integer-literals"></a>Littéraux d'entier

Les littéraux entiers peuvent être écrits en notation décimale ou hexadécimale. Les littéraux hexadécimaux sont précédés de `0x` pour les distinguer des nombres décimaux.

Les littéraux entiers peuvent avoir un suffixe de type et un suffixe multiplicateur.

| Suffixe |            Signification             |          Notes           |
| ------ | ------------------------------ | ----------------------- |
| o      | type de données Byte signé          | Ajouté dans PowerShell 6,2 |
| uy     | type de données Byte non signé        | Ajouté dans PowerShell 6,2 |
| s      | short (type de données)                | Ajouté dans PowerShell 6,2 |
| us     | type de données Short non signé       | Ajouté dans PowerShell 6,2 |
| l      | long (type de données)                 |                         |
| u      | type de données int ou long non signé | Ajouté dans PowerShell 6,2 |
| ul     | type de données long non signé        | Ajouté dans PowerShell 6,2 |
| kb     | multiplicateur de kilo-octets            |                         |
| mb     | multiplicateur de mégaoctets            |                         |
| moins     | multiplicateur de gigaoctets            |                         |
| to     | multiplicateur de téraoctets            |                         |
| gérés     | multiplicateur de pétaoctet            |                         |

Le type d’un littéral entier est déterminé par sa valeur, le suffixe de type et le suffixe multiplicateur numérique.

Pour un littéral d’entier sans suffixe de type :

- Si la valeur peut être représentée par le type `[int]` , il s’agit de son type.
- Sinon, si la valeur peut être représentée par le type `[long]` , il s’agit de son type.
- Sinon, si la valeur peut être représentée par le type `[decimal]` , il s’agit de son type.
- Dans le cas contraire, il est représenté par le type `[double]` .

Pour un littéral d’entier avec un suffixe de type :

- Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[uint]` son type est `[uint]` .
- Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[ulong]` son type est `[ulong]` .
- Si sa valeur peut être représentée par le type spécifié, alors il s’agit de son type.
- Dans le cas contraire, ce littéral est incorrect.

## <a name="real-literals"></a>Littéraux réels

Les littéraux réels ne peuvent être écrits qu’en notation décimale. Cette notation peut inclure des valeurs fractionnaires à la suite d’une virgule décimale et d’une notation scientifique à l’aide d’une partie exponentielle.

La partie exponentielle comprend un « e » suivi d’un signe facultatif (+/-) et d’un nombre représentant l’exposant. Par exemple, la valeur littérale `1e2` est égale à la valeur numérique 100.

Les littéraux réels peuvent avoir un suffixe de type et un suffixe multiplicateur.

| Suffixe |       Signification       |
| ------ | ------------------- |
| d      | type de données decimal   |
| kb     | multiplicateur de kilo-octets |
| mb     | multiplicateur de mégaoctets |
| moins     | multiplicateur de gigaoctets |
| to     | multiplicateur de téraoctets |
| gérés     | multiplicateur de pétaoctet |

Il existe deux types de littéraux réels : double et Decimal. Celles-ci sont indiquées par l’absence ou la présence, respectivement, du suffixe de type décimal. PowerShell ne prend pas en charge la représentation littérale d’une `[float]` valeur. Un littéral réel double a le type `[double]` . Un littéral réel décimal a le type `[decimal]` .
Les zéros de fin dans la partie fractionnaire d’un littéral réel décimal sont significatifs.

Si la valeur des chiffres de la partie exposant dans un `[double]` littéral réel est inférieure à la valeur minimale prise en charge, la valeur de ce `[double]` littéral réel est 0. Si la valeur des chiffres de la partie exposant dans un `[decimal]` littéral réel est inférieure à la valeur minimale prise en charge, ce littéral est incorrect. Si la valeur des chiffres de la partie exposant dans un `[double]` `[decimal]` littéral réel ou est supérieure à la valeur maximale prise en charge, ce littéral est incorrect.

> [!NOTE]
> La syntaxe autorise un littéral double réel à avoir un suffixe de type long.
> PowerShell traite ce cas comme un littéral d’entier dont la valeur est représentée par le type `[long]` . Cette fonctionnalité a été conservée à des fins de compatibilité descendante avec les versions antérieures de PowerShell. Toutefois, les programmeurs sont déconseillés d’utiliser des littéraux entiers de ce formulaire, car ils peuvent facilement masquer la valeur réelle du littéral. Par exemple, `1.2L` a la valeur 1, `1.2345e1L` a la valeur 12 et `1.2345e-5L` a la valeur 0, aucune d’entre elles étant immédiatement évidente.

## <a name="numeric-multipliers"></a>Multiplicateurs numériques

Pour des raisons pratiques, les littéraux entiers et réels peuvent contenir un multiplicateur numérique, ce qui indique un ensemble de puissances couramment utilisées de 2. Le multiplicateur numérique peut être écrit dans n’importe quelle combinaison de lettres majuscules ou minuscules.

Les suffixes de multiplicateur peuvent être utilisés en combinaison avec `u` les `ul` `l` suffixes de type, et.

### <a name="multiplier-examples"></a>Exemples de multiplicateur

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a>Accélérateurs de type numérique

PowerShell prend en charge les accélérateurs de type suivants :

| Accélérateur |         Notes         |           Description            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | Byte (non signé)                  |
| `[sbyte]`   |                      | Octet (signé)                    |
| `[Int16]`   |                      | Entier de 16 bits                   |
| `[short]`   | alias pour `[int16]`  | Entier de 16 bits                   |
| `[UInt16]`  |                      | entier 16 bits (non signé)        |
| `[ushort]`  | alias pour `[uint16]` | entier 16 bits (non signé)        |
| `[Int32]`   |                      | Entier de 32 bits                   |
| `[int]`     | alias pour `[int32]`  | Entier de 32 bits                   |
| `[UInt32]`  |                      | entier 32 bits (non signé)        |
| `[uint]`    | alias pour `[uint32]` | entier 32 bits (non signé)        |
| `[Int64]`   |                      | Entier 64 bits                   |
| `[long]`    | alias pour `[int64]`  | Entier 64 bits                   |
| `[UInt64]`  |                      | entier 64 bits (non signé)        |
| `[ulong]`   | alias pour `[uint64]` | entier 64 bits (non signé)        |
| `[bigint]`  |                      | Voir [BigInteger, struct][bigint]  |
| `[single]`  |                      | Virgule flottante simple précision  |
| `[float]`   | alias pour `[single]` | Virgule flottante simple précision  |
| `[double]`  |                      | Virgule flottante double précision  |
| `[decimal]` |                      | virgule flottante 128 bits           |

> [!NOTE]
> Les accélérateurs de type suivants ont été ajoutés dans PowerShell 6,2 : `[short]` , `[ushort]` ,, `[uint]` `[ulong]` .

### <a name="working-with-other-numeric-types"></a>Utilisation d’autres types numériques

Pour travailler avec d’autres types numériques, vous devez utiliser des accélérateurs de type, ce qui n’est pas sans problèmes. Par exemple, les valeurs entières élevées sont toujours analysées comme double avant d’être converties en un autre type.

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

La valeur est analysée en premier, ce qui perd la précision dans les plages supérieures.
Pour éviter ce problème, entrez des valeurs sous forme de chaînes, puis convertissez-les :

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a>Exemples

Le tableau suivant contient plusieurs exemples de littéraux numériques et répertorie leur type et leur valeur :

|  Nombre  |  Type   |    Valeur     |
| -------: | ------- | -----------: |
|      100 | Int32   |          100 |
|     100D | Decimal |          100 |
|     100l | Int64   |          100 |
|    100uL | UInt64  |          100 |
|    100us | UInt16  |          100 |
|    100uy | Byte    |          100 |
|     100y | SByte   |          100 |
|      1e2 | Double  |          100 |
|     1. E2 | Double  |          100 |
|    0x1e2 | Int32   |          482 |
|   0x1e2L | Int64   |          482 |
|   0x1e2D | Int32   |         7725 |
|     482D | Decimal |          482 |
|    482gb | Int64   | 517543559168 |
| 0x1e2lgb | Int64   | 517543559168 |

### <a name="commands-that-look-like-numeric-literals"></a>Commandes qui ressemblent à des littéraux numériques

Toute commande ressemblant à un littéral numérique doit être exécutée à l’aide de l’opérateur `&` d’appel (), sinon elle est interprétée comme un nombre du type associé.

### <a name="access-properties-and-methods-of-numeric-objects"></a>Accéder aux propriétés et aux méthodes d’objets numériques

Pour accéder à un membre d’un littéral numérique, il y a des cas où vous devez placer le littéral entre parenthèses.

- Le littéral n’a pas de virgule décimale
- Le littéral n’a pas de chiffres après la virgule décimale
- Le littéral n’a pas de suffixe

Par exemple, l’exemple suivant échoue :

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

Les exemples suivants fonctionnent :

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

Les deux premiers exemples fonctionnent sans mettre la valeur littérale entre parenthèses, car l’analyseur PowerShell peut déterminer où se termine le littéral numérique et la méthode **GetType** démarre.

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
