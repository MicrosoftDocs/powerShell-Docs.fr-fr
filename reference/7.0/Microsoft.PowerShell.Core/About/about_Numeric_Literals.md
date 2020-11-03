---
description: Les littéraux numériques et réels peuvent avoir des suffixes de type et de multiplicateur.
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des littéraux numériques
ms.openlocfilehash: 8e26e8c67b1acadc75a67cd51bd6adb07fb7daf3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206778"
---
# <a name="about-numeric-literals"></a>À propos des littéraux numériques

Il existe deux types de littéraux numériques : entier et réel. Les deux peuvent avoir des suffixes de type et multiplicateur.

## <a name="integer-literals"></a>Littéraux d'entier

Les littéraux entiers peuvent être écrits en notation décimale, hexadécimale ou binaire.
Les littéraux hexadécimaux sont préfixés par `0x` et les littéraux binaires sont préfixés avec `0b` pour les distinguer des nombres décimaux.

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
| n      | BigInteger (type de données)           | Ajouté dans PowerShell 7,0 |
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

Les suffixes de multiplicateur peuvent être utilisés en combinaison avec n’importe quel suffixe de type, mais doivent être présents après le suffixe de type. Par exemple, le littéral `100gbL` est incorrect, mais le littéral `100Lgb` est valide.

Si un multiplicateur crée une valeur qui dépasse les valeurs possibles pour le type numérique que le suffixe spécifie, le littéral est incorrect. Par exemple, le littéral `1usgb` est incorrect, car la valeur `1gb` est supérieure à ce qui est autorisé pour le `[ushort]` type spécifié par le `us` suffixe.

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

## <a name="examples"></a>Exemples

Le tableau suivant contient plusieurs exemples de littéraux numériques et répertorie leur type et leur valeur :

|   Number     |  Type      |    Valeur     |
| -----------: | ---------- | -----------: |
|         100  | Int32      |          100 |
|        100u  | UInt32     |          100 |
|        100D  | Decimal    |          100 |
|        100l  | Int64      |          100 |
|       100uL  | UInt64     |          100 |
|       100us  | UInt16     |          100 |
|       100uy  | Byte       |          100 |
|        100y  | SByte      |          100 |
|         1e2  | Double     |          100 |
|        1. E2  | Double     |          100 |
|       0x1e2  | Int32      |          482 |
|      0x1e2L  | Int64      |          482 |
|      0x1e2D  | Int32      |         7725 |
|        482D  | Decimal    |          482 |
|       482gb  | Int64      | 517543559168 |
|       482ngb | BigInteger | 517543559168 |
|    0x1e2lgb  | Int64      | 517543559168 |
|   0b1011011  | Int32      |           91 |
|  Égale  | Int32      |           -1 |
| -0xFFFFFFFF  | Int32      |            1 |
| 0xFFFFFFFFu  | UInt32     |   4294967295 |

### <a name="working-with-binary-or-hexadecimal-numbers"></a>Utilisation de nombres binaires ou hexadécimaux

Les littéraux binaires ou hexadécimaux trop grands peuvent retourner au `[bigint]` lieu d’échouer à l’analyse, si et seulement si le `n` suffixe est spécifié. Les bits de signe sont toujours respectés au-dessus des `[decimal]` plages paires, mais :

- Si une chaîne binaire est un multiple de 8 bits de long, le bit le plus élevé est traité comme le bit de signe.
- Si une chaîne hexadécimale, dont la longueur est un multiple de 8, a le premier chiffre avec 8 ou plus, le chiffre est traité comme négatif.

La spécification d’un suffixe non signé sur des littéraux binaires et hexadécimaux ignore les bits de signe. Par exemple, `0xFFFFFFFF` retourne `-1` , mais `0xFFFFFFFFu` retourne le `[uint]::MaxValue` de 4294967295.

Le préfixe du littéral avec un `0` contournera cette opération et sera traité comme non signé.
Par exemple : `0b011111111`. Cela peut être nécessaire lors de l’utilisation de littéraux dans la `[bigint]` plage, car les `u` `n` suffixes et ne peuvent pas être combinés.

Vous pouvez également nier les littéraux binaires et hexadécimaux à l’aide du `-` préfixe. Cela peut entraîner un nombre positif, car les bits de signe sont autorisés.

Les bits de signe sont acceptés pour les chiffres avec suffixe BigInteger :

- Le paramètre hexadécimal avec suffixe BigInteger traite le bit élevé de tout littéral avec une longueur multiple de 8 caractères comme bit de signe. La longueur n’inclut ni le `0x` préfixe, ni les suffixes.
- Le binaire avec suffixe BigInteger accepte les bits de signe à 96 et 128 caractères, et à tous les 8 caractères après.

### <a name="commands-that-look-like-numeric-literals"></a>Commandes qui ressemblent à des littéraux numériques

Toute commande ressemblant à un littéral numérique valide doit être exécutée à l’aide de l’opérateur d’appel ( `&` ), sinon elle est interprétée comme un nombre. Les littéraux mal formés avec une syntaxe valide `1usgb` , comme, provoquent l’erreur suivante :

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

Toutefois, les littéraux mal formés avec une syntaxe non valide comme `1gbus` seront interprétés comme une chaîne simple standard et peuvent être interprétés comme un nom de commande valide dans les contextes où les commandes peuvent être appelées.

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

## <a name="how-powershell-parses-numeric-literals"></a>Comment PowerShell analyse les littéraux numériques

PowerShell v 7.0 a changé la façon dont les littéraux numériques sont analysés pour activer les nouvelles fonctionnalités.

### <a name="parsing-real-numeric-literals"></a>Analyse des littéraux numériques réels

Si le littéral contient une virgule décimale ou une notation électronique, la chaîne littérale est analysée comme un nombre réel.

- Si le suffixe décimal est présent, puis directement dans `[decimal]` .
- Sinon, analyser en tant que `[Double]` et appliquer le multiplicateur à la valeur. Vérifiez ensuite les suffixes de type et tentez d’effectuer un cast en type approprié.
- Si la chaîne n’a pas de suffixe de type, analyser en tant que `[Double]` .

### <a name="paring-integer-numeric-literals"></a>Littéraux numériques géocouplage Integer

Les littéraux de type entier sont analysés à l’aide des étapes suivantes :

1. Déterminer le format de base
   - Pour les formats binaires, analysez dans `[BigInteger]` .
   - Pour les formats hexadécimaux, analysez dans `[BigInteger]` à l’aide de Casies spéciaux pour conserver les comportements d’origine lorsque la valeur est dans la `[int]` `[long]` plage ou.
   - Si ni Binary ni Hex, ne sont normalement analysés en tant que `[BigInteger]` .
2. Appliquez la valeur de multiplicateur avant de tenter d’effectuer des casts pour vous assurer que les limites du type peuvent être vérifiées correctement sans dépassement de capacité.
3. Vérifiez les suffixes de type.
   - Vérifiez les limites du type et tentez d’analyser ce type.
   - Si aucun suffixe n’est utilisé, la valeur est Bounds-Checked dans l’ordre suivant, ce qui entraîne le premier test réussi déterminant le type du nombre.
     - `[int]`
     - `[long]`
     - `[decimal]` (valeurs littérales de base 10 uniquement)
     - `[double]` (valeurs littérales de base 10 uniquement)
   - Si la valeur est en dehors `[long]` de la plage pour les nombres hexadécimaux et binaires, l’analyse échoue.
   - Si la valeur est en dehors `[double]` de la plage pour le nombre de base 10, l’analyse échoue.
   - Les valeurs supérieures doivent être écrites explicitement à l’aide du `n` suffixe pour analyser le littéral en tant que `BigInteger` .

### <a name="parsing-large-value-literals"></a>Analyse des littéraux de valeur élevée

Auparavant, les valeurs entières supérieures étaient analysées comme double avant d’être transtypées en un autre type. Cela entraîne une perte de précision dans les plages supérieures. Par exemple :

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

Pour éviter ce problème, vous deviez écrire des valeurs sous forme de chaînes, puis les convertir :

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

Dans PowerShell 7,0, vous devez utiliser le `N` suffixe.

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

En outre, les valeurs comprises entre `[ulong]::MaxValue` et `[decimal]::MaxValue` doivent être dénotées à l’aide du suffixe décimal `D` pour assurer la précision. Sans le suffixe, ces valeurs sont analysées comme `[Double]` utilisant le mode d’analyse réelle.

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger?view=netcore-2.2
