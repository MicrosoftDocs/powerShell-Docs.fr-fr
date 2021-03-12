---
description: Décrit comment utiliser des opérateurs pour assigner des valeurs à des variables.
Locale: en-US
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: 469c482ea8dbf2af315ed64129b8e790b66840e4
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194551"
---
# <a name="about-assignment-operators"></a>À propos des opérateurs d’assignation

## <a name="short-description"></a>Description courte
Décrit comment utiliser des opérateurs pour assigner des valeurs à des variables.

## <a name="long-description"></a>Description longue

Les opérateurs d’assignation affectent une ou plusieurs valeurs à une variable. Ils peuvent effectuer des opérations numériques sur les valeurs avant l’assignation.

PowerShell prend en charge les opérateurs d’assignation suivants.

|Opérateur|Description                                                  |
|--------|-------------------------------------------------------------|
|=       |Affecte la valeur spécifiée à une variable.         |
|+=      |Augmente la valeur d’une variable par la valeur spécifiée, ou |
|        |Ajoute la valeur spécifiée à la valeur existante.           |
|-=      |Réduit la valeur d’une variable par la valeur spécifiée.    |
|*=      |Multiplie la valeur d’une variable par la valeur spécifiée, ou|
|        |Ajoute la valeur spécifiée à la valeur existante.           |
|/=      |Divise la valeur d’une variable par la valeur spécifiée.      |
|%=      |Divise la valeur d’une variable par la valeur spécifiée et   |
|        |affecte ensuite le reste (modulo) à la variable.        |
|++      |Augmente la valeur d’une variable, d’une propriété qui est assignée ou   |
|        |élément de tableau de 1.                                          |
|--      |Diminue la valeur d’une variable, d’une propriété qui est assignée ou   |
|        |élément de tableau de 1.                                          |

## <a name="syntax"></a>Syntaxe

La syntaxe des opérateurs d’assignation est la suivante :

`<assignable-expression>` `<assignment-operator>` `<value>`

Les expressions assignables incluent des variables et des propriétés. La valeur peut être une valeur unique, un tableau de valeurs, ou une commande, une expression ou une instruction.

Les opérateurs d’incrémentation et de décrémentation sont des opérateurs unaires. Chaque possède des versions de préfixe et de suffixe.

`<assignable-expression><operator>`
`<operator><assignable-expression>`

L’expression pouvant être assignée doit être un nombre ou être convertible en un nombre.

## <a name="assigning-values"></a>Assigner des valeurs

Les variables sont nommées espaces mémoire qui stockent des valeurs. Vous stockez les valeurs dans des variables à l’aide de l’opérateur d’assignation `=` . La nouvelle valeur peut remplacer la valeur existante de la variable, ou vous pouvez ajouter une nouvelle valeur à la valeur existante.

L’opérateur d’assignation de base est le signe égal `=` `(ASCII 61)` . Par exemple, l’instruction suivante assigne la valeur PowerShell à la `$MyShell` variable :

```powershell
$MyShell = "PowerShell"
```

Lorsque vous affectez une valeur à une variable dans PowerShell, la variable est créée si elle n’existait pas déjà. Par exemple, la première des deux instructions d’assignation suivantes crée la `$a` variable et assigne une valeur de 6 à `$a` . La deuxième instruction d’assignation assigne une valeur de 12 à `$a` . La première instruction crée une variable. La deuxième instruction modifie uniquement sa valeur :

```powershell
$a = 6
$a = 12
```

Les variables dans PowerShell n’ont pas un type de données spécifique, sauf si vous effectuez un cast.
Quand une variable contient un seul objet, la variable prend le type de données de cet objet. Quand une variable contient une collection d’objets, la variable a le type de données System. Object. Par conséquent, vous pouvez assigner n’importe quel type d’objet à la collection. L’exemple suivant montre que vous pouvez ajouter des objets de processus, des objets de service, des chaînes et des entiers à une variable sans générer d’erreur :

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

Étant donné que l’opérateur `=` d’assignation a une priorité inférieure à celle de l’opérateur de pipeline `|` , les parenthèses ne sont pas requises pour assigner le résultat d’un pipeline de commande à une variable. Par exemple, la commande suivante trie les services sur l’ordinateur, puis assigne les services triés à la `$a` variable :

```powershell
$a = Get-Service | Sort-Object -Property name
```

Vous pouvez également assigner la valeur créée par une instruction à une variable, comme dans l’exemple suivant :

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

Cet exemple assigne zéro à la `$a` variable si la valeur de `$b` est inférieure à zéro. Elle assigne la valeur de `$b` à `$a` si la valeur de `$b` n’est pas inférieure à zéro.

### <a name="the-assignment-operator"></a>Opérateur d’assignation

L’opérateur `=` d’assignation affecte des valeurs aux variables. Si la variable a déjà une valeur, l’opérateur d’assignation `=` remplace la valeur sans avertissement.

L’instruction suivante assigne la valeur entière 6 à la `$a` variable :

```powershell
$a = 6
```

Pour assigner une valeur de chaîne à une variable, mettez la valeur de chaîne entre guillemets, comme suit :

```powershell
$a = "baseball"
```

Pour assigner un tableau (plusieurs valeurs) à une variable, séparez les valeurs par des virgules, comme suit :

```powershell
$a = "apple", "orange", "lemon", "grape"
```

Pour affecter une table de hachage à une variable, utilisez la notation de table de hachage standard dans PowerShell. Tapez un arobase `@` suivi de paires clé/valeur séparées par des points-virgules `;` et placées entre accolades `{ }` . Par exemple, pour affecter une table de hachage à la `$a` variable, tapez :

```powershell
$a = @{one=1; two=2; three=3}
```

Pour assigner des valeurs hexadécimales à une variable, faites précéder la valeur de `0x` .
PowerShell convertit la valeur hexadécimale (0x10) en valeur décimale (dans ce cas, 16) et assigne cette valeur à la `$a` variable. Par exemple, pour affecter une valeur de 0x10 à la `$a` variable, tapez :

```powershell
$a = 0x10
```

Pour assigner une valeur exponentielle à une variable, tapez le numéro racine, la lettre `e` et un nombre qui représente un multiple de 10. Par exemple, pour affecter la valeur 3,1415 à la puissance 1 000 à la `$a` variable, tapez :

```powershell
$a = 3.1415e3
```

PowerShell peut également convertir des kilo-octets `KB` , des mégaoctets `MB` et des gigaoctets `GB` en octets. Par exemple, pour affecter une valeur de 10 kilo-octets à la `$a` variable, tapez :

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a>Assignation par l’opérateur d’addition

L’opérateur d’assignation d’addition `+=` incrémente la valeur d’une variable ou ajoute la valeur spécifiée à la valeur existante. L’action varie selon que la variable a un type numérique ou chaîne et si la variable contient une valeur unique (une valeur scalaire) ou plusieurs valeurs (une collection).

L' `+=` opérateur combine deux opérations. Tout d’abord, il ajoute, puis il affecte.
Par conséquent, les instructions suivantes sont équivalentes :

```powershell
$a += 2
$a = ($a + 2)
```

Lorsque la variable contient une valeur numérique unique, l' `+=` opérateur incrémente la valeur existante de la valeur du côté droit de l’opérateur. L’opérateur assigne ensuite la valeur résultante à la variable. L’exemple suivant montre comment utiliser l' `+=` opérateur pour augmenter la valeur d’une variable :

```powershell
$a = 4
$a += 2
$a
```

```
6
```

Lorsque la valeur de la variable est une chaîne, la valeur située à droite de l’opérateur est ajoutée à la chaîne, comme suit :

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

Lorsque la valeur de la variable est un tableau, l' `+=` opérateur ajoute les valeurs du côté droit de l’opérateur au tableau. À moins que le tableau ne soit explicitement typé par Cast, vous pouvez ajouter n’importe quel type de valeur au tableau, comme suit :

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

et

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

Lorsque la valeur d’une variable est une table de hachage, l' `+=` opérateur ajoute la valeur située à droite de l’opérateur à la table de hachage. Toutefois, étant donné que le seul type que vous pouvez ajouter à une table de hachage est une autre table de hachage, toutes les autres affectations échouent.

Par exemple, la commande suivante affecte une table de hachage à la `$a` variable.
Ensuite, il utilise l' `+=` opérateur pour ajouter une autre table de hachage à la table de hachage existante, en ajoutant une nouvelle paire clé/valeur à la table de hachage existante.
Cette commande fonctionne correctement, comme indiqué dans la sortie :

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

La commande suivante tente d’ajouter un entier « 1 » à la table de hachage dans la `$a` variable. Échec de cette commande :

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a>Assignation par l’opérateur de soustraction

L’opérateur d’assignation par soustraction `-=` décrémente la valeur d’une variable en fonction de la valeur spécifiée sur le côté droit de l’opérateur. Cet opérateur ne peut pas être utilisé avec des variables de chaîne et ne peut pas être utilisé pour supprimer un élément d’une collection.

L' `-=` opérateur combine deux opérations. En premier lieu, il soustrait, puis il affecte. Par conséquent, les instructions suivantes sont équivalentes :

```powershell
$a -= 2
$a = ($a - 2)
```

L’exemple suivant montre comment utiliser l' `-=` opérateur pour réduire la valeur d’une variable :

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

Vous pouvez également utiliser l' `-=` opérateur d’assignation pour réduire la valeur d’un membre d’un tableau numérique. Pour ce faire, spécifiez l’index de l’élément de tableau que vous souhaitez modifier. Dans l’exemple suivant, la valeur du troisième élément d’un tableau (élément 2) est diminuée de 1 :

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

Vous ne pouvez pas utiliser l' `-=` opérateur pour supprimer les valeurs d’une variable. Pour supprimer toutes les valeurs assignées à une variable, utilisez les applets de [commande Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item) ou [Clear-variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) pour affecter une valeur de `$null` ou `""` à la variable.

```powershell
$a = $null
```

Pour supprimer une valeur particulière d’un tableau, utilisez la notation de tableau pour assigner une valeur `$null` à l’élément particulier. Par exemple, l’instruction suivante supprime la deuxième valeur (position d’index 1) d’un tableau :

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

Pour supprimer une variable, utilisez l’applet de commande [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) . Cette méthode est utile lorsque la variable est explicitement convertie en un type de données particulier et que vous souhaitez une variable non typée. La commande suivante supprime la `$a` variable :

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a>Assignation par opérateur de multiplication

L’opérateur d’assignation par multiplication `*=` multiplie une valeur numérique ou ajoute le nombre spécifié de copies de la valeur de chaîne d’une variable.

Lorsqu’une variable contient une valeur numérique unique, cette valeur est multipliée par la valeur située à droite de l’opérateur. Par exemple, l’exemple suivant montre comment utiliser l' `*=` opérateur pour multiplier la valeur d’une variable :

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

Dans ce cas, l' `*=` opérateur combine deux opérations. Tout d’abord, il multiplie, puis l’assigne. Par conséquent, les instructions suivantes sont équivalentes :

```powershell
$a *= 2
$a = ($a * 2)
```

Lorsqu’une variable contient une valeur de chaîne, PowerShell ajoute le nombre spécifié de chaînes à la valeur, comme suit :

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

Pour multiplier un élément d’un tableau, utilisez un index pour identifier l’élément que vous souhaitez multiplier. Par exemple, la commande suivante multiplie le premier élément du tableau (position d’index 0) par 2 :

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a>Opérateur d’assignation par division

L’opérateur Assignment par division `/=` divise une valeur numérique par la valeur spécifiée sur le côté droit de l’opérateur. L’opérateur ne peut pas être utilisé avec des variables de chaîne.

L' `/=` opérateur combine deux opérations. Tout d’abord, elle est divisée, puis assignée. Par conséquent, les deux instructions suivantes sont équivalentes :

```powershell
$a /= 2
$a = ($a / 2)
```

Par exemple, la commande suivante utilise l' `/=` opérateur pour diviser la valeur d’une variable :

```powershell
$a = 8
$a /=2
$a
```

```
4
```

Pour diviser un élément d’un tableau, utilisez un index pour identifier l’élément que vous souhaitez modifier. Par exemple, la commande suivante divise le deuxième élément du tableau (position d’index 1) par 2 :

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a>L’opérateur d’assignation par Modulo

L’opérateur d’assignation par Modulo `%=` divise la valeur d’une variable par la valeur située à droite de l’opérateur. L' `%=` opérateur assigne ensuite le reste (appelé modulo) à la variable. Vous pouvez utiliser cet opérateur uniquement lorsqu’une variable contient une valeur numérique unique. Vous ne pouvez pas utiliser cet opérateur quand une variable contient une variable de chaîne ou un tableau.

L' `%=` opérateur combine deux opérations. Tout d’abord, il divise et détermine le reste, puis il assigne le reste à la variable. Par conséquent, les instructions suivantes sont équivalentes :

```powershell
$a %= 2
$a = ($a % 2)
```

L’exemple suivant montre comment utiliser l' `%=` opérateur pour enregistrer le modulo d’un quotient :

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a>Opérateurs d’incrémentation et de décrémentation

L’opérateur `++` d’incrément augmente la valeur d’une variable de 1. Lorsque vous utilisez l’opérateur d’incrément dans une instruction simple, aucune valeur n’est retournée. Pour afficher le résultat, affichez la valeur de la variable, comme suit :

```powershell
$a = 7
++$a
$a
```

```
8
```

Pour forcer le retour d’une valeur, placez la variable et l’opérateur entre parenthèses, comme suit :

```powershell
$a = 7
(++$a)
```

```
8
```

L’opérateur d’incrément peut être placé avant (préfixe) ou après (postfix) une variable. La version préfixée de l’opérateur incrémente une variable avant que sa valeur ne soit utilisée dans l’instruction, comme suit :

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

La version suffixée de l’opérateur incrémente une variable une fois que sa valeur est utilisée dans l’instruction. Dans l’exemple suivant, les `$c` `$a` variables et ont des valeurs différentes, car la valeur est assignée à `$c` avant `$a` les modifications :

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

L’opérateur `--` de décrémentation réduit la valeur d’une variable de 1. Comme avec l’opérateur d’incrémentation, aucune valeur n’est retournée lorsque vous utilisez l’opérateur dans une instruction simple. Utilisez des parenthèses pour retourner une valeur, comme suit :

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

La version préfixée de l’opérateur décrémente une variable avant que sa valeur ne soit utilisée dans l’instruction, comme suit :

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

La version suffixée de l’opérateur décrémente une variable une fois que sa valeur est utilisée dans l’instruction. Dans l’exemple suivant, les `$d` `$a` variables et ont des valeurs différentes, car la valeur est assignée à `$d` avant `$a` les modifications :

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a>Types de Framework Microsoft .NET

Par défaut, lorsqu’une variable n’a qu’une seule valeur, la valeur assignée à la variable détermine le type de données de la variable. Par exemple, la commande suivante crée une variable qui a le type « Integer » (System. Int32) :

```powershell
$a = 6
```

Pour rechercher le type de .NET Framework d’une variable, utilisez la méthode **GetType** et sa propriété **FullName** , comme suit. Veillez à inclure les parenthèses après le nom de la méthode **GetType** , même si l’appel de la méthode n’a pas d’argument :

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

Pour créer une variable qui contient une chaîne, assignez une valeur de chaîne à la variable. Pour indiquer que la valeur est une chaîne, mettez-la entre guillemets, comme suit :

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

Si la première valeur assignée à la variable est une chaîne, PowerShell traite toutes les opérations comme des opérations de chaîne et convertit les nouvelles valeurs en chaînes.
Cela se produit dans l’exemple suivant :

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

Si la première valeur est un entier, PowerShell traite toutes les opérations comme des opérations d’entiers et convertit les nouvelles valeurs en entiers. Cela se produit dans l’exemple suivant :

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

Vous pouvez effectuer un cast d’une nouvelle variable scalaire en tout type de .NET Framework en plaçant le nom du type entre crochets qui précèdent le nom de la variable ou la première valeur de l’affectation. Lorsque vous effectuez un cast d’une variable, vous pouvez déterminer les types de données qui peuvent être stockés dans la variable. Et vous pouvez déterminer le comportement de la variable lorsque vous la manipulez.

Par exemple, la commande suivante convertit la variable en type chaîne :

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

L’exemple suivant convertit la première valeur, au lieu de convertir la variable :

```powershell
$a = [string]27
```

Lorsque vous effectuez un cast d’une variable en un type spécifique, la Convention courante consiste à effectuer un cast de la variable, et non la valeur. Toutefois, vous ne pouvez pas reconvertir le type de données d’une variable existante si sa valeur ne peut pas être convertie dans le nouveau type de données. Pour modifier le type de données, vous devez remplacer sa valeur, comme suit :

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

En outre, lorsque vous faites précéder un nom de variable d’un type de données, le type de cette variable est verrouillé, sauf si vous substituez explicitement le type en spécifiant un autre type de données. Si vous essayez d’assigner une valeur qui n’est pas compatible avec le type existant et que vous ne substituez pas explicitement le type, PowerShell affiche une erreur, comme illustré dans l’exemple suivant :

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

Dans PowerShell, les types de données des variables qui contiennent plusieurs éléments d’un tableau sont gérés différemment des types de données des variables qui contiennent un seul élément. À moins qu’un type de données ne soit spécifiquement affecté à une variable tableau, le type de données est toujours `System.Object []` . Ce type de données est spécifique aux tableaux.

Parfois, vous pouvez remplacer le type par défaut en spécifiant un autre type. Par exemple, la commande suivante convertit la variable en `string []` type de tableau :

```powershell
[string []] $a = "one", "two", "three"
```

Les variables PowerShell peuvent être n’importe quel type de données .NET Framework. En outre, vous pouvez assigner n’importe quel type de données .NET Framework complet disponible dans le processus actuel. Par exemple, la commande suivante spécifie un `System.DateTime` type de données :

```powershell
[System.DateTime]$a = "5/31/2005"
```

Une valeur conforme au type de données est assignée à la variable `System.DateTime` . La valeur de la `$a` variable est la suivante :

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a>Assignation de plusieurs variables

Dans PowerShell, vous pouvez assigner des valeurs à plusieurs variables à l’aide d’une seule commande. Le premier élément de la valeur d’assignation est assigné à la première variable, le deuxième élément est assigné à la deuxième variable, le troisième élément à la troisième variable, et ainsi de suite. Par exemple, la commande suivante affecte la valeur 1 à la `$a` variable, la valeur 2 à la `$b` variable et la valeur 3 à la `$c` variable :

```powershell
$a, $b, $c = 1, 2, 3
```

Si la valeur d’affectation contient plus d’éléments que de variables, toutes les valeurs restantes sont affectées à la dernière variable. Par exemple, la commande suivante contient trois variables et cinq valeurs :

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

Par conséquent, PowerShell affecte la valeur 1 à la `$a` variable et la valeur 2 à la `$b` variable. Elle affecte les valeurs 3, 4 et 5 à la `$c` variable.
Pour assigner les valeurs de la `$c` variable à trois autres variables, utilisez le format suivant :

```powershell
$d, $e, $f = $c
```

Cette commande affecte la valeur 3 à la `$d` variable, la valeur 4 à la `$e` variable et la valeur 5 à la `$f` variable.

Si la valeur d’affectation contient moins d’éléments que de variables, aucune valeur n’est affectée à toutes les variables restantes à la fin. Par exemple, la commande suivante contient trois variables et deux valeurs :

```powershell
$a, $b, $c = 1, 2
```

Par conséquent, PowerShell affecte la valeur 1 à la `$a` variable et la valeur 2 à la `$b` variable. Aucune valeur n’est assignée à la `$c` variable.

Vous pouvez également assigner une valeur unique à plusieurs variables en les chaînageant. Par exemple, la commande suivante affecte une valeur « trois » aux quatre variables :

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a>Applets de commande associées à une variable

Outre l’utilisation d’une opération d’assignation pour définir une valeur de variable, vous pouvez également utiliser l’applet de commande [Set-variable](xref:Microsoft.PowerShell.Utility.Set-Variable) . Par exemple, la commande suivante utilise `Set-Variable` pour assigner un tableau de 1, 2, 3 à la `$a` variable.

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a>Voir aussi

[about_Arrays](about_Arrays.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Variables](about_Variables.md)

[Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[Set-variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
