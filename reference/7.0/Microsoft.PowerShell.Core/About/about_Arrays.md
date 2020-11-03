---
description: Décrit les tableaux, qui sont des structures de données conçues pour stocker des collections d’éléments.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: 2283c36d899c3ea743f6c379dc686ec583d7a36c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206785"
---
# <a name="about-arrays"></a>À propos des tableaux

## <a name="short-description"></a>Description courte
Décrit les tableaux, qui sont des structures de données conçues pour stocker des collections d’éléments.

## <a name="long-description"></a>Description longue

Un tableau est une structure de données conçue pour stocker une collection d’éléments.
Les éléments peuvent être du même type ou de types différents.

À compter de Windows PowerShell 3,0, une collection de zéro ou un objet a des propriétés de tableaux.

## <a name="creating-and-initializing-an-array"></a>Création et initialisation d’un tableau

Pour créer et initialiser un tableau, assignez plusieurs valeurs à une variable. Les valeurs stockées dans le tableau sont délimitées par une virgule et séparées du nom de la variable par l’opérateur d’assignation ( `=` ).

Par exemple, pour créer un tableau nommé `$A` qui contient les sept valeurs numériques (int) de 22, 5, 10, 8, 12, 9 et 80, tapez :

```powershell
$A = 22,5,10,8,12,9,80
```

La virgule peut également être utilisée pour initialiser un tableau à un seul élément en plaçant la virgule avant l’élément unique.

Par exemple, pour créer un tableau d’éléments unique nommé `$B` contenant la valeur unique 7, tapez :

```powershell
$B = ,7
```

Vous pouvez également créer et initialiser un tableau à l’aide de l’opérateur de plage ( `..` ).
L’exemple suivant crée un tableau contenant les valeurs de 5 à 8.

```powershell
$C = 5..8
```

En conséquence, `$C` contient quatre valeurs : 5, 6, 7 et 8.

Quand aucun type de données n’est spécifié, PowerShell crée chaque tableau en tant que tableau d’objets ( **System. Object []** ). Pour déterminer le type de données d’un tableau, utilisez la méthode **GetType ()** . Par exemple, pour déterminer le type de données du `$A` tableau, tapez :

```powershell
$A.GetType()
```

Pour créer un tableau fortement typé, autrement dit un tableau qui peut contenir uniquement des valeurs d’un type particulier, effectuez un cast de la variable en type tableau, tel que **String []** , **long []** ou **Int32 []** . Pour effectuer un cast d’un tableau, faites précéder le nom de la variable d’un type de tableau entre crochets. Par exemple, pour créer un tableau d’entiers 32 bits nommé `$ia` contenant quatre entiers (1500, 2230, 3350 et 4000), tapez :

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

Par conséquent, le `$ia` tableau peut contenir uniquement des entiers.

Vous pouvez créer des tableaux qui sont convertis en n’importe quel type pris en charge dans le Framework Microsoft .NET. Par exemple, les objets qui `Get-Process` récupèrent pour représenter des processus sont du type **System. Diagnostics. Process** . Pour créer un tableau d’objets de processus fortement typé, entrez la commande suivante :

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a>Opérateur de sous-expression de tableau

L’opérateur de sous-expression de tableau crée un tableau à partir des instructions qu’il contient. Quelle que soit l’instruction produite par l’opérateur, l’opérateur la place dans un tableau. Même s’il y a zéro ou un objet.

La syntaxe de l’opérateur Array est la suivante :

```syntax
@( ... )
```

Vous pouvez utiliser l’opérateur de tableau pour créer un tableau de zéro ou un objet. Par exemple :

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

L’opérateur Array est utile dans les scripts lorsque vous obtenez des objets, mais que vous ne connaissez pas le nombre d’objets que vous obtenez. Par exemple :

```powershell
$p = @(Get-Process Notepad)
```

Pour plus d’informations sur l’opérateur de sous-expression de tableau, consultez [about_Operators](about_Operators.md).

## <a name="accessing-and-using-array-elements"></a>Accès et utilisation d’éléments de tableau

### <a name="reading-an-array"></a>Lecture d’un tableau

Vous pouvez faire référence à un tableau à l’aide de son nom de variable. Pour afficher tous les éléments du tableau, tapez le nom du tableau. Par exemple, en supposant `$a` que est un tableau contenant des entiers 0, 1, 2, jusqu’à 9, en tapant :

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

Vous pouvez faire référence aux éléments d’un tableau à l’aide d’un index, en commençant à la position 0. Placez le numéro d’index entre crochets. Par exemple, pour afficher le premier élément du `$a` tableau, tapez :

```powershell
$a[0]
```

```Output
0
```

Pour afficher le troisième élément dans le `$a` tableau, tapez :

```powershell
$a[2]
```

```Output
2
```

Vous pouvez récupérer une partie du tableau à l’aide d’un opérateur de plage pour l’index. Par exemple, pour récupérer les deuxième et cinquième éléments du tableau, vous devez taper :

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

Nombre de nombres négatifs à partir de la fin du tableau. Par exemple, « -1 » fait référence au dernier élément du tableau. Pour afficher les trois derniers éléments du tableau, dans l’ordre croissant de l’index, tapez :

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

Si vous tapez des index négatifs dans l’ordre décroissant, votre sortie change.

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

Toutefois, soyez prudent lorsque vous utilisez cette notation. La notation passe de la limite de fin au début du tableau.

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

En outre, une erreur courante consiste à supposer que `$a[0..-2]` fait référence à tous les éléments du tableau, à l’exception du dernier. Elle fait référence aux premier, dernier et dernier élément dans le tableau.

Vous pouvez utiliser l’opérateur plus ( `+` ) pour combiner des plages avec une liste d’éléments dans un tableau. Par exemple, pour afficher les éléments aux positions d’index 0, 2 et 4 à 6, tapez :

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

En outre, pour répertorier plusieurs plages et éléments individuels, vous pouvez utiliser l’opérateur plus. Par exemple, pour répertorier les éléments de zéro à deux, quatre à six et l’élément à huitième type de position :

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a>Itérations sur les éléments de tableau

Vous pouvez également utiliser des constructions de boucle, telles que ForEach, pour et des boucles While, pour faire référence aux éléments d’un tableau. Par exemple, pour utiliser une boucle ForEach afin d’afficher les éléments du `$a` tableau, tapez :

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

La boucle ForEach itère au sein du tableau et retourne chaque valeur dans le tableau jusqu’à atteindre la fin du tableau.

La boucle for est utile lorsque vous incrémentez des compteurs tout en examinant les éléments d’un tableau. Par exemple, pour utiliser une boucle for pour retourner toutes les autres valeurs dans un tableau, tapez :

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

Vous pouvez utiliser une boucle while pour afficher les éléments d’un tableau jusqu’à ce qu’une condition définie n’ait plus la valeur true. Par exemple, pour afficher les éléments du `$a` tableau alors que l’index du tableau est inférieur à 4, tapez :

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a>Propriétés des tableaux

### <a name="count-or-length-or-longlength"></a>Count ou Length ou LongLength

Pour déterminer le nombre d’éléments contenus dans un tableau, utilisez la `Length` propriété ou son `Count` alias. `Longlength` est utile si le tableau contient plus de 2 147 483 647 éléments.

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a>Rank

Retourne le nombre de dimensions du tableau. La plupart des tableaux dans PowerShell ont une seule dimension, uniquement. Même lorsque vous pensez que vous créez un tableau multidimensionnel ; comme dans l’exemple suivant :

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

[int]$r = $a.Rank
"`$a rank: $r"
```

```Output
$a rank: 1
```

L’exemple suivant montre comment créer un tableau véritablement multidimensionnel à l’aide du .NET Framework.

```powershell
[int[,]]$rank2 = [int[,]]::new(5,5)
$rank2.rank
```

```Output
2
```

## <a name="methods-of-arrays"></a>Méthodes de tableaux

### <a name="clear"></a>Effacer

Affecte à toutes les valeurs d’élément la _valeur par défaut_ du type d’élément du tableau.
La méthode Clear () ne réinitialise pas la taille du tableau.

Dans l’exemple suivant, `$a` il s’agit d’un tableau d’objets.

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

Dans cet exemple, `$intA` est explicitement typé pour contenir des entiers.

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a>ForEach

Permet d’itérer sur tous les éléments du tableau et d’effectuer une opération donnée pour chaque élément du tableau.

La méthode ForEach a plusieurs surcharges qui effectuent des opérations différentes.

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a>ForEach (expression scriptblock)

#### <a name="foreachscriptblock-expression-object-arguments"></a>ForEach (expression scriptblock, Object [] arguments)

Cette méthode a été ajoutée dans PowerShell v4.

> [!NOTE]
> La syntaxe requiert l’utilisation d’un bloc de script. Les parenthèses sont facultatives si le scriptblock est le seul paramètre. En outre, il ne doit pas y avoir d’espace entre la méthode et la parenthèse ouvrante ou l’accolade ouvrante.

L’exemple suivant montre comment utiliser la méthode ForEach. Dans ce cas, l’objectif est de générer la valeur carrée des éléments dans le tableau.

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

Tout comme le `-ArgumentList` paramètre de `ForEach-Object` , le `arguments` paramètre permet de passer un tableau d’arguments à un bloc de script configuré pour les accepter.

Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about_Splatting.md#splatting-with-arrays).

#### <a name="foreachtype-converttotype"></a>ForEach (type convertToType)

La `ForEach` méthode peut être utilisée pour effectuer un cast rapide des éléments vers un autre type. l’exemple suivant montre comment convertir une liste de dates de chaîne en `[DateTime]` type.

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a>ForEach (String NomPropriété)

#### <a name="foreachstring-propertyname-object-newvalue"></a>ForEach (String NomPropriété, Object [] newValue)

La `ForEach` méthode peut également être utilisée pour récupérer rapidement ou définir des valeurs de propriété pour chaque élément de la collection.

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a>ForEach (String methodName)

#### <a name="foreachstring-methodname-object-arguments"></a>ForEach (String methodName, Object [] arguments)

Enfin, `ForEach` les méthodes peuvent être utilisées pour exécuter une méthode sur chaque élément de la collection.

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

Tout comme le `-ArgumentList` paramètre de `ForEach-Object` , le `arguments` paramètre permet de passer un tableau d’arguments à un bloc de script configuré pour les accepter.

> [!NOTE]
> À partir de Windows PowerShell 3,0, la récupération des propriétés et l’exécution de méthodes pour chaque élément d’une collection peut également être accomplie à l’aide de « méthodes des objets scalaires et des collections ». vous pouvez en savoir plus à ce sujet [about_methods](about_methods.md).

### <a name="where"></a>Où

Permet de filtrer ou de sélectionner les éléments du tableau. Le script doit avoir une valeur autre que : zéro (0), une chaîne vide `$false` ou `$null` pour l’élément à afficher après `Where`

Il existe une définition pour la `Where` méthode.

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> La syntaxe requiert l’utilisation d’un bloc de script. Les parenthèses sont facultatives si le scriptblock est le seul paramètre. En outre, il ne doit pas y avoir d’espace entre la méthode et la parenthèse ouvrante ou l’accolade ouvrante.

`Expression`Est un scriptblock qui est requis pour le filtrage, l' `mode` argument facultatif autorise des fonctionnalités de sélection supplémentaires et l' `numberToReturn` argument facultatif permet de limiter le nombre d’éléments retournés à partir du filtre.

Les valeurs acceptables pour `mode` sont les suivantes :

- Valeur par défaut (0)-retourne tous les éléments
- First (1) : retourne le premier élément
- Last (2) : retourne le dernier élément
- Ignorer jusqu’à (3)-ignorer les éléments tant que la condition n’a pas la valeur true, le retourne les éléments restants
- Until (4)-renvoyer tous les éléments jusqu’à ce que condition ait la valeur true
- Split (5) : retourne un tableau de deux éléments
  - Le premier élément contient des éléments correspondants
  - Le deuxième élément contient les éléments restants.

L’exemple suivant montre comment sélectionner tous les nombres impairs dans le tableau.

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

Cet exemple montre comment sélectionner les chaînes qui ne sont pas vides.

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a>Default

Le `Default` mode filtre les éléments à l’aide du `Expression` scriptblock.

Si un `numberToReturn` est fourni, il spécifie le nombre maximal d’éléments à retourner.

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> Le `Default` mode et le `First` mode retournent tous deux les premiers `numberToReturn` éléments () et peuvent être utilisés indifféremment.

#### <a name="last"></a>Dernier

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a>Ignorer jusqu’à

Le `SkipUntil` mode ignore tous les objets d’une collection jusqu’à ce qu’un objet passe le filtre d’expression de bloc de script. Elle retourne ensuite **tous les** éléments de collection restants sans les tester. _Un seul élément de passage est testé_ .

Cela signifie que la collection retournée contient à la fois des éléments de _réussite_ et de _non-passage_ qui n’ont pas été testés.

Le nombre d’éléments retournés peut être limité en passant une valeur à l' `numberToReturn` argument.

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a>Until

Le `Until` mode inverse le `SkipUntil` mode.  Elle retourne **tous les** éléments d’une collection jusqu’à ce qu’un élément passe l’expression de bloc de script. Une fois qu’un élément a _réussi_ l’expression scriptblock, la `Where` méthode arrête le traitement des éléments.

Cela signifie que vous recevez le premier jeu de _non-passage_ d’éléments à partir de la `Where` méthode. _Une fois qu'_ un élément est passé, les autres éléments ne sont pas testés ou retournés.

Le nombre d’éléments retournés peut être limité en passant une valeur à l' `numberToReturn` argument.

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> `Until`Et `SkipUntil` fonctionnent sous le principe de ne pas tester un lot d’éléments.
>
> `Until` retourne les éléments **avant** la première _passe_ .
>
> `SkipUntil` retourne tous les éléments **après** la première _passe_ , y compris le premier élément passant.

#### <a name="split"></a>Split

Le `Split` mode fractionne, ou regroupe les éléments de la collection en deux collections distinctes. Ceux qui passent l’expression scriptblock et ceux qui ne le sont pas.

Si un `numberToReturn` est spécifié, la première collection contient les éléments qui _passent_ , et non pas la valeur spécifiée.

Les objets restants, y compris ceux qui **passent** le filtre d’expression, sont retournés dans la deuxième collection.

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a>Obtient les membres d’un tableau

Pour récupérer les propriétés et les méthodes d’un tableau, telles que la propriété Length et la méthode **SetValue** , utilisez le paramètre **InputObject** de l’applet de commande `Get-Member` .

Quand vous dirigez un tableau vers `Get-Member` , PowerShell envoie les éléments un par un et `Get-Member` retourne le type de chaque élément dans le tableau (en ignorant les doublons).

Quand vous utilisez le paramètre **InputObject** , `Get-Member` retourne les membres du tableau.

Par exemple, la commande suivante obtient les membres de la `$a` variable tableau.

```powershell
Get-Member -InputObject $a
```

Vous pouvez également obtenir les membres d’un tableau en tapant une virgule (,) avant la valeur redirigée vers l' `Get-Member` applet de commande. La virgule fait du tableau le deuxième élément dans un tableau de tableaux. PowerShell conduit les tableaux un par un et `Get-Member` retourne les membres du tableau. Comme les deux exemples suivants.

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a>Manipulation d’un tableau

Vous pouvez modifier les éléments d’un tableau, ajouter un élément à un tableau et combiner les valeurs de deux tableaux dans un troisième tableau.

Pour modifier la valeur d’un élément particulier dans un tableau, spécifiez le nom du tableau et l’index de l’élément que vous souhaitez modifier, puis utilisez l’opérateur d’assignation ( `=` ) pour spécifier une nouvelle valeur pour l’élément. Par exemple, pour modifier la valeur du deuxième élément du `$a` tableau (position d’index 1) sur 10, tapez :

```powershell
$a[1] = 10
```

Vous pouvez également utiliser la méthode **SetValue** d’un tableau pour modifier une valeur. L’exemple suivant remplace la deuxième valeur (position d’index 1) du `$a` tableau par 500 :

```powershell
$a.SetValue(500,1)
```

Vous pouvez utiliser l' `+=` opérateur pour ajouter un élément à un tableau. L’exemple suivant montre comment ajouter un élément au `$a` tableau.

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> Lorsque vous utilisez l' `+=` opérateur, PowerShell crée en fait un nouveau tableau avec les valeurs du tableau d’origine et la valeur ajoutée. Cela peut entraîner des problèmes de performances si l’opération est répétée plusieurs fois ou si la taille du tableau est trop importante.

Il n’est pas facile de supprimer des éléments d’un tableau, mais vous pouvez créer un nouveau tableau qui contient uniquement les éléments sélectionnés d’un tableau existant. Par exemple, pour créer le `$t` tableau avec tous les éléments du tableau, à l' `$a` exception de la valeur de la position d’index 2, tapez :

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

Pour combiner deux tableaux en un seul tableau, utilisez l’opérateur plus ( `+` ). L’exemple suivant crée deux tableaux, les combine, puis affiche le tableau combiné résultant.

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

Par conséquent, le `$z` tableau contient 1, 3, 5 et 9.

Pour supprimer un tableau, assignez une valeur `$null` au tableau. La commande suivante supprime le tableau dans la `$a` variable.

`$a = $null`

Vous pouvez également utiliser l' `Remove-Item` applet de commande, mais l’affectation d’une valeur `$null` à est plus rapide, en particulier pour les grands tableaux.

## <a name="arrays-of-zero-or-one"></a>Tableaux de zéro ou un

À compter de Windows PowerShell 3,0, une collection de zéro ou un objet a la propriété Count et length. En outre, vous pouvez indexer dans un tableau d’un objet. Cette fonctionnalité vous aide à éviter les erreurs de script qui se produisent lorsqu’une commande qui attend une collection reçoit moins de deux éléments.

Les exemples suivants illustrent cette fonctionnalité.

### <a name="zero-objects"></a>Zéro objet

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a>Un objet

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a>Prise en charge de l’indexation pour les objets System. Tuple

PowerShell 6,1 a ajouté la prise en charge de l’accès indexé des objets **Tuple** , comme les tableaux.
Par exemple :

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

Contrairement aux tableaux et autres objets de collection, les objets **Tuple** sont traités comme un objet unique lorsqu’ils sont transmis via le pipeline ou par des paramètres qui prennent en charge des tableaux d’objets.

Pour plus d’informations, consultez [System. Tuple](/dotnet/api/system.tuple).

## <a name="see-also"></a>Voir aussi

- [about_Assignment_Operators](about_Assignment_Operators.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Operators](about_Operators.md)
- [about_For](about_For.md)
- [about_Foreach](about_Foreach.md)
- [about_While](about_While.md)
