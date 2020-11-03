---
description: Décrit les opérateurs qui effectuent des opérations arithmétiques dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: 3ece7464198ff52fe6c22ccc54ceede84288bd7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206762"
---
# <a name="about-arithmetic-operators"></a>À propos des opérateurs arithmétiques

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit les opérateurs qui effectuent des opérations arithmétiques dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les opérateurs arithmétiques calculent des valeurs numériques. Vous pouvez utiliser un ou plusieurs opérateurs arithmétiques pour ajouter, soustraire, multiplier et diviser des valeurs, et pour calculer le reste (modulo) d’une opération de division.

En outre, l’opérateur d’addition ( `+` ) et l’opérateur de multiplication ( `*` ) fonctionnent également sur les chaînes, les tableaux et les tables de hachage. L’opérateur d’addition concatène l’entrée. L’opérateur de multiplication retourne plusieurs copies de l’entrée. Vous pouvez même mélanger des types d’objet dans une instruction arithmétique. La méthode utilisée pour évaluer l’instruction est déterminée par le type de l’objet le plus à gauche dans l’expression.

À compter de PowerShell 2,0, tous les opérateurs arithmétiques fonctionnent sur des nombres 64 bits.

À compter de PowerShell 3,0, le `-shr` (Shift-Right) et `-shl` (Shift-Left) sont ajoutés pour prendre en charge l’arithmétique au niveau du bit dans PowerShell.

PowerShell prend en charge les opérateurs arithmétiques suivants :

|Opérateur|Description                       |Exemple                      |
|--------|----------------------------------|-----------------------------|
| +      |Ajoute des entiers. concatène       |`6 + 2`                      |
|        |les chaînes, les tableaux et les tables de hachage. |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |Soustrait une valeur d’une autre  |`6 - 2`                      |
|        |value                             |                             |
| -      |Fait d’un nombre un nombre négatif  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |Multiplier des nombres ou copier des chaînes  |`6 * 2`                      |
|        |et tableaux le nombre spécifié   |`@("!") * 4`                 |
|        |de fois.                         |`"!" * 3`                    |
| /      |Divise deux valeurs.               |`6 / 2`                      |
| %      |Modulo-retourne le reste de|`7 % 2`                      |
|        |opération de division.             |                             |
|-bande   |ET au niveau du bit                       |`5 -band 3`                  |
|-bnot   |NOT au niveau du bit                       |`-bnot 5`                    |
|-Bor    |Opération de bits OR                        |`5 -bor 0x03`                |
|-bxor   |Opération de bits XOR                       |`5 -bxor 3`                  |
|-SHL    |Décale les bits vers la gauche           |`102 -shl 2`                 |
|-SHR    |Décale les bits vers la droite          |`102 -shr 2`                 |

Les opérateurs au niveau du bit fonctionnent uniquement sur les types entiers.

## <a name="operator-precedence"></a>PRIORITÉ DES OPÉRATEURS

PowerShell traite les opérateurs arithmétiques dans l’ordre suivant :

|Priorité|Opérateur          |Description                            |
|----------|------------------|---------------------------------------|
|1         | `()`             |Parenthèses                            |
|2         | `-`              |Pour un nombre négatif ou un opérateur unaire|
|3         | `*`, `/`, `%`    |Pour la multiplication et la Division        |
|4         | `+`, `-`         |Pour l’addition et la soustraction           |
|5         | `-band`, `-bnot` |Pour les opérations au niveau du bit                 |
|5         | `-bor`, `-bxor`  |Pour les opérations au niveau du bit                 |
|5         | `-shr`, `-shl`   |Pour les opérations au niveau du bit                 |

PowerShell traite les expressions de gauche à droite en fonction des règles de précédence. Les exemples suivants illustrent l’effet des règles de précédence :

|Expression |Résultats|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

L’ordre dans lequel PowerShell évalue les expressions peut différer des autres langages de programmation et de script que vous avez utilisés. L’exemple suivant montre une instruction d’assignation complexe.

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

Dans cet exemple, l’expression `$a++` est évaluée avant `$b[$a]` .
`$a++`L’évaluation de modifie la valeur de `$a` lorsqu’elle est utilisée dans l’instruction `$c[$a++]` , mais avant qu’elle ne soit utilisée dans `$b[$a]` . La variable `$a` de `$b[$a]` est égal `1` à, pas `0` ; par conséquent, l’instruction assigne une valeur à `$b[1]` , et non à `$b[0]` .

Le code ci-dessus équivaut à :

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a>DIVISION ET ARRONDI

Lorsque le quotient d’une opération de division est un entier, PowerShell arrondit la valeur à l’entier le plus proche. Lorsque la valeur est `.5` , elle est arrondie à l’entier pair le plus proche.

L’exemple suivant montre l’effet de l’arrondi à l’entier pair le plus proche.

|Expression      |Résultats|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

Notez que **_5/2_ = 2,5** est arrondi à **2** . Toutefois, **_7/2_ = 3,5** est arrondi à **4** .

Vous pouvez utiliser la `[Math]` classe pour bénéficier d’un comportement d’arrondi différent.

|                          Expression                          | Résultats |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

Pour plus d’informations, consultez la méthode [Math. Round](/dotnet/api/system.math.round) .

## <a name="adding-and-multiplying-non-numeric-types"></a>AJOUT ET MULTIPLICATION DE TYPES NON NUMÉRIQUES

Vous pouvez ajouter des nombres, des chaînes, des tableaux et des tables de hachage. Et, vous pouvez multiplier des nombres, des chaînes et des tableaux. Toutefois, vous ne pouvez pas multiplier les tables de hachage.

Lorsque vous ajoutez des chaînes, des tableaux ou des tables de hachage, les éléments sont concaténés. Lorsque vous concaténez des collections, telles que des tableaux ou des tables de hachage, un nouvel objet contenant les objets des deux collections est créé. Si vous essayez de concaténer des tables de hachage qui ont la même clé, l’opération échoue.

Par exemple, les commandes suivantes créent deux tableaux, puis les ajoutent :

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

Vous pouvez également effectuer des opérations arithmétiques sur des objets de types différents.
L’opération exécutée par PowerShell est déterminée par le type de Microsoft .NET Framework de l’objet le plus à gauche dans l’opération. PowerShell tente de convertir tous les objets de l’opération en .NET Framework type du premier objet. S’il parvient à convertir les objets, il effectue l’opération appropriée au type de .NET Framework du premier objet. Si la conversion de l’un des objets échoue, l’opération échoue.

Les exemples suivants illustrent l’utilisation des opérateurs d’addition et de multiplication. dans les opérations qui incluent des types d’objets différents. Supposons que `$array = 1,2,3` :

|Expression       |Résultats                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |`1`,`2`,`3`,`16`       |
|`$array + "file"`|`1`,`2`,`3`,`file`     |
|`$array * 2`     |`1`,`2`,`3`,`1`,`2`,`3`|
|`"file" * 3`     |`filefilefile`         |

Étant donné que la méthode utilisée pour évaluer les instructions est déterminée par l’objet le plus à gauche, l’addition et la multiplication dans PowerShell ne sont pas strictement commutatables. Par exemple, `(a + b)` n’est pas toujours égal à `(b + a)` et `(ab)` n’est pas toujours égal à `(ba)` .

Les exemples suivants illustrent ce principe :

|Expression   |Résultats                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |+ 16 + "fichier" '                                       |

Les tables de hachage sont un cas légèrement différent. Vous pouvez ajouter des tables de hachage à une autre table de hachage, à condition que les tables de hachage ajoutées n’aient pas de clés dupliquées.

L’exemple suivant montre comment ajouter des tables de hachage les unes aux autres.

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

L’exemple suivant génère une erreur, car l’une des clés est dupliquée dans les deux tables de hachage.

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

En outre, vous pouvez ajouter une table de hachage à un tableau. et, l’ensemble de la table de hachage devient un élément dans le tableau.

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

Toutefois, vous ne pouvez pas ajouter d’autres types à une table de hachage.

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

Bien que les opérateurs d’addition soient très utiles, utilisez les opérateurs d’assignation pour ajouter des éléments aux tableaux de hachage et aux tableaux. Pour plus d’informations, consultez [about_Assignment_Operators](about_Assignment_Operators.md). Les exemples suivants utilisent l' `+=` opérateur d’assignation pour ajouter des éléments à un tableau :

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a>CONVERSION DE TYPE EN FONCTION DU RÉSULTAT

PowerShell sélectionne automatiquement le type de .NET Framework numérique qui exprime le mieux le résultat sans perte de précision. Par exemple :

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

Si le résultat d’une opération est trop grand pour le type, le type du résultat est élargi pour s’adapter au résultat, comme dans l’exemple suivant :

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

Le type du résultat n’est pas nécessairement le même que l’un des opérandes. Dans l’exemple suivant, la valeur négative ne peut pas être convertie en entier non signé et l’entier non signé est trop grand pour être converti en `Int32` :

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

Dans cet exemple, `Int64` peut prendre en charge les deux types.

Le `System.Decimal` type est une exception. Si l’un des opérandes a le type décimal, le résultat sera du type décimal. Si le résultat est trop grand pour le type décimal, il n’est pas converti en double. Au lieu de cela, une erreur est générée.

|Expression               |Résultats                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a>OPÉRATEURS ARITHMÉTIQUES ET VARIABLES

Vous pouvez également utiliser des opérateurs arithmétiques avec des variables. Les opérateurs agissent sur les valeurs des variables. Les exemples suivants illustrent l’utilisation d’opérateurs arithmétiques avec des variables :

| Expression                                    |Résultats      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a>OPÉRATEURS ARITHMÉTIQUES ET COMMANDES

En général, vous utilisez les opérateurs arithmétiques dans les expressions avec des nombres, des chaînes et des tableaux. Toutefois, vous pouvez également utiliser des opérateurs arithmétiques avec les objets retournés par les commandes et avec les propriétés de ces objets.

Les exemples suivants montrent comment utiliser les opérateurs arithmétiques dans les expressions avec des commandes PowerShell :

```powershell
(get-date) + (new-timespan -day 1)
```

L’opérateur parenthèse force l’évaluation de l' `get-date` applet de commande et l’évaluation de l’expression de l' `new-timespan -day 1` applet de commande, dans cet ordre. Les deux résultats sont ensuite ajoutés à l’aide de l' `+` opérateur.

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

Dans l’expression ci-dessus, chaque espace de travail de processus ( `$_.ws` ) est multiplié par `2` ; et, le résultat, comparé `50mb` pour voir s’il est supérieur à.

## <a name="bitwise-operators"></a>Opérateurs au niveau du bit

PowerShell prend en charge les opérateurs de bits standard, y compris les opérateurs de bits and ( `-bAnd` ), les opérateurs or inclusifs et exclusifs ( `-bOr` and `-bXor` ) et not au niveau du bit ( `-bNot` ).

À compter de PowerShell 2,0, tous les opérateurs au niveau du bit fonctionnent avec des entiers 64 bits.

À compter de PowerShell 3,0, le `-shr` (Shift-Right) et `-shl` (Shift-Left) sont introduits pour prendre en charge l’arithmétique au niveau du bit dans PowerShell.

PowerShell prend en charge les opérateurs de bits suivants.

| Opérateur | Description            | Expression   | Résultats |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | ET au niveau du bit            | `10 -band 3` | 2      |
| `-bor`   | Or au niveau du bit (inclusive) | `10 -bor 3`  | 11     |
| `-bxor`  | Or au niveau du bit (exclusif) | `10 -bxor 3` | 9      |
| `-bnot`  | NOT au niveau du bit            | `-bNot 10`   | -11    |
| `-shl`   | Décalage vers la gauche             | `102 -shl 2` | 408    |
| `-shr`   | Décalage vers la droite            | `102 -shr 1` | 51     |

Les opérateurs au niveau du bit agissent sur le format binaire d’une valeur. Par exemple, la structure de bits pour le nombre 10 est 00001010 (sur la base de 1 octet) et la structure de bits pour le nombre 3 est 00000011. Lorsque vous utilisez un opérateur au niveau du bit pour comparer 10 à 3, les bits individuels de chaque octet sont comparés.

Dans une opération AND au niveau du bit, le bit résultant est défini sur 1 uniquement lorsque les deux bits d’entrée ont la valeur 1.

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

Dans une opération or au niveau du bit (inclusive), le bit résultant est défini sur 1 lorsque l’un des bits d’entrée ou les deux sont 1. Le bit résultant est défini sur 0 uniquement lorsque les deux bits d’entrée ont la valeur 0.

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

Dans une opération de bits or (exclusive), le bit résultant est défini sur 1 uniquement lorsqu’un bit d’entrée est 1.

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

L’opérateur de bits NOT est un opérateur unaire qui produit le complément binaire de la valeur. Un bit de 1 est défini sur 0 et un bit de 0 est défini sur 1.

Par exemple, le complément binaire de 0 est égal à-1, l’entier non signé maximal (0xFFFFFFFF) et le complément binaire-1 à 0.

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

Dans une opération de décalage vers la gauche au niveau du bit, tous les bits sont déplacés vers la gauche, où « n » est la valeur de l’opérande de droite. Un zéro est inséré à l’endroit.

Lorsque l’opérande gauche est une valeur entière (32 bits), les 5 bits inférieurs de l’opérande droit déterminent le nombre de bits de l’opérande gauche qui sont décalés.

Lorsque l’opérande gauche est une valeur longue (64 bits), les 6 bits inférieurs de l’opérande droit déterminent le nombre de bits de l’opérande gauche qui sont décalés.

|Expression |Résultats|Résultat binaire|
|-----------|------|-------------|
|`21 -shl 0`|21    |0001 0101    |
|`21 -shl 1`|42    |0010 1010    |
|`21 -shl 2`|84    |0101 0100    |

Dans une opération de décalage vers la droite au niveau du bit, tous les bits sont déplacés vers la droite, où « n » est spécifié par l’opérande de droite. L’opérateur Shift-Right (-SHR) insère un zéro à l’emplacement le plus à gauche lors du décalage d’une valeur positive ou non signée vers la droite.

Lorsque l’opérande gauche est une valeur entière (32 bits), les 5 bits inférieurs de l’opérande droit déterminent le nombre de bits de l’opérande gauche qui sont décalés.

Lorsque l’opérande gauche est une valeur longue (64 bits), les 6 bits inférieurs de l’opérande droit déterminent le nombre de bits de l’opérande gauche qui sont décalés.

|Expression              |Résultats      |Binary     |Hex         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | 21         | 0001 0101 | 0x15       |
|`21 -shr 1`             | 10         | 0000 1010 | 0x0A       |
|`21 -shr 2`             | 5          | 0000 0101 | 0x05       |
|`21 -shr 31`            | 0          | 0000 0000 | 0x00       |
|`21 -shr 32`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 64`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 65`            | 10         | 0000 1010 | 0x0A       |
|`21 -shr 66`            | 5          | 0000 0101 | 0x05       |
|`[int]::MaxValue -shr 1`| 1073741823 |           | 0x3FFFFFFF |
|`[int]::MinValue -shr 1`| -1073741824|           | 0xC0000000 |
|`-1 -shr 1`             | -1         |           | Égale |

## <a name="see-also"></a>VOIR AUSSI

- [about_arrays](about_Arrays.md)
- [about_assignment_operators](about_Assignment_Operators.md)
- [about_comparison_operators](about_Comparison_Operators.md)
- [about_hash_tables](about_Hash_Tables.md)
- [about_operators](about_Operators.md)
- [about_variables](about_Variables.md)
- [Obtient la date](xref:Microsoft.PowerShell.Utility.Get-Date)
- [New-TimeSpan](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
