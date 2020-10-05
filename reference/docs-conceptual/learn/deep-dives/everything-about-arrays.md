---
title: Tout ce que vous avez toujours voulu savoir sur les tableaux
description: Les tableaux constituent une fonctionnalité fondamentale de la plupart des langages de programmation.
ms.date: 07/07/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 307189bf27d383159d34181eca4dac1f77792e51
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91543370"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a>Tout ce que vous avez toujours voulu savoir sur les tableaux

Les [tableaux][] constituent une fonctionnalité fondamentale de la plupart des langages de programmation. Il s’agit d’une collection de valeurs ou d’objets qu’il est difficile d’éviter. Examinons plus en détails les tableaux et ce qu’ils ont à offrir.

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu. Consultez son blog à l’adresse [PowerShellExplained.com][].

## <a name="what-is-an-array"></a>Qu’est-ce qu’un tableau ?

Commençons par une description technique de base des tableaux et de leur utilisation dans la plupart des langages de programmation avant de passer aux autres usages qu’en fait PowerShell.

Un tableau est une structure de données qui sert de collection de plusieurs éléments. Il est possible de boucler sur le tableau ou d’accéder à certains éléments individuellement à l’aide d’un index. Le tableau est créé sous la forme d’un bloc séquentiel de mémoire dans lequel chaque valeur est stockée juste à côté de l’autre.

Ces différents détails seront expliqués au fur et à mesure.

## <a name="basic-usage"></a>Utilisation de base

Étant donné que les tableaux sont une fonctionnalité de base de PowerShell, il existe une syntaxe simple pour les utiliser dans PowerShell.

### <a name="create-an-array"></a>Création d’un tableau

`@()` permet de créer un tableau vide.

```powershell
PS> $data = @()
PS> $data.count
0
```

Il est possible de créer un tableau et de l’amorcer avec des valeurs en les plaçant simplement entre les parenthèses `@()`.

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

Ce tableau contient 4 éléments. Lorsque l’on appelle la variable `$data`, la liste des éléments s’affiche. S’il s’agit d’un tableau de chaînes, on obtient une ligne par chaîne.

Le tableau peut être déclaré sur plusieurs lignes. La virgule, facultative dans ce cas, est généralement omise.

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

L’avantage qu’il y a à déclarer les tableaux sur plusieurs lignes est qu’ils sont plus faciles à lire lorsqu’ils comportent plusieurs éléments, ainsi qu’à comparer avec les versions précédentes dans le cadre du contrôle de code source.

#### <a name="other-syntax"></a>Autre syntaxe

Il est communément admis que `@()` est la syntaxe pour créer un tableau, mais les listes séparées par des virgules fonctionnent la plupart du temps.

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a>Write-Output pour créer des tableaux

Petite astuce intéressante, vous pouvez utiliser `Write-Output` pour créer rapidement des chaînes au niveau de la console.

```powershell
$data = Write-Output Zero One Two Three
```

C’est pratique, car il n’est pas nécessaire de placer de guillemets autour des chaînes lorsque le paramètre accepte des chaînes. Si cette pratique est clairement à éviter dans un script, elle reste intéressante dans la console.

### <a name="accessing-items"></a>Accès aux éléments

Maintenant que nous disposons d’un tableau contenant des éléments, il s’agit d’accéder à ces éléments et de les mettre à jour.

#### <a name="offset"></a>Offset

Pour accéder à des éléments individuels, on utilise les crochets `[]` avec une valeur de décalage commençant à 0. Voici comment obtenir le premier élément du tableau :

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

La raison pour laquelle nous utilisons ici 0 est que le premier élément se trouve au début de la liste, ce qui implique d’employer un décalage de 0 élément pour y accéder. Pour atteindre le deuxième élément, il faudrait un décalage de 1 permettant d’ignorer le premier élément.

```powershell
PS> $data[1]
One
```

Par conséquent, le dernier élément est associé à un décalage de 3.

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a>Index

Le choix des valeurs de cet exemple semble maintenant plus clair. Ce que nous avons jusqu’ici appelé décalage dans un souci d’exactitude est plus communément nommé index. Il s’agit d’un index qui commence à `0`. Nous parlerons d’index pour désigner le décalage dans la suite de cet article.

#### <a name="special-index-tricks"></a>Astuces concernant les index

Dans la plupart des langages, on ne peut spécifier qu’un seul nombre comme index et on récupère un seul élément.
PowerShell est bien plus flexible. Il est possible d’utiliser plusieurs index à la fois. Fournir une liste d’index permet de sélectionner plusieurs éléments.

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

Les éléments sont retournés dans l’ordre des index fournis. Si l’on duplique un index, on récupère cet élément les deux fois.

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

Il est possible de spécifier une séquence de nombres avec l’opérateur `..` intégré.

```powershell
PS> $data[1..3]
One
Two
Three
```

Cela fonctionne également en sens inverse.

```powershell
PS> $data[3..1]
Three
Two
One
```

Vous pouvez utiliser des valeurs d’index négatives pour suivre un décalage à partir de la fin. Par conséquent, si vous avez besoin du dernier élément de la liste, vous pouvez employer `-1`.

```powershell
PS> $data[-1]
Three
```

Attention à l’opérateur `..`. La séquence `0..-1` et `-1..0` correspond aux valeurs `0,-1` et `-1,0`. Il est facile de voir `$data[0..-1]` et de croire qu’elle énumère tous les éléments si l’on oublie ce détail. `$data[0..-1]` donne la même valeur que `$data[0,-1]`, à savoir le premier et le dernier élément du tableau (sans aucune autre valeur).

#### <a name="out-of-bounds"></a>Hors limites

Dans la plupart des langages, si l’on tente d’accéder à un index d’élément qui se trouve au-delà de la fin du tableau, on obtient un certain type d’erreur ou une exception. PowerShell ne retourne rien.

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a>Impossible d’indexer dans un tableau Null

Si vous tentez d’indexer une variable `$null` comme un tableau, vous recevez une exception `System.Management.Automation.RuntimeException` avec le message `Cannot index into a null array`.

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

Par conséquent, vérifiez que vos tableaux ne sont pas `$null` avant d’essayer d’accéder aux éléments qu’ils contiennent.

#### <a name="count"></a>Count

Les tableaux et autres collections possèdent une propriété count qui indique le nombre d’éléments qu’ils contiennent.

```powershell
PS> $data.count
4
```

Dans la version 3.0 de PowerShell, une propriété count a été ajoutée à la plupart des objets. Pour un seul objet, elle doit donner le nombre `1`.

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

Même `$null` possède une propriété count, à ceci près qu’elle retourne `0`.

```powershell
PS> $null.count
0
```

Cet aspect présente quelques pièges, que nous examinerons lorsque nous aborderons les tableaux `$null` ou vides plus loin dans cet article.

#### <a name="off-by-one-errors"></a>Erreur par décalage de un

Le fait que les tableaux commencent à l’index 0 représente une source d’erreur de programmation courante. Les erreurs par décalage de un peuvent être introduites de deux façons.

La première consiste à penser mentalement que l’on souhaite le deuxième élément et à utiliser l’index `2`, pour en fin de compte obtenir le troisième élément. De même, on peut être tenté de considérer qu’il suffit de prendre le nombre total d’éléments (dans notre exemple, 4) pour accéder au dernier élément.

```powershell
$data[ $data.count ]
```

PowerShell autorise sans problème cette manipulation et se contente de fournir l’élément qui se trouve précisément à l’index 4 : `$null`. Il faudrait utiliser `$data.count - 1`, ou `-1` comme nous l’avons vu ci-dessus.

```powershell
PS> $data[ $data.count - 1 ]
Three
```

C’est là que vous pouvez utiliser l’index `-1` pour récupérer le dernier élément.

```powershell
PS> $data[ -1 ]
Three
```

Lee Dailey a également indiqué que l’on peut utiliser `$data.GetUpperBound(0)` pour récupérer le numéro d’index maximal.

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

La seconde erreur la plus courante consiste à boucler sur la liste et à ne pas s’arrêter au bon moment. Nous reviendrons sur ce sujet lorsque nous parlerons de la boucle `for`.

### <a name="updating-items"></a>Mise à jour des éléments

Le même index peut servir à mettre à jour des éléments existants dans le tableau. Il nous donne un accès direct à des éléments individuels.

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

Si l’on tente de mettre à jour un élément qui se trouve au-delà du dernier élément, on obtient une erreur `Index was outside the bounds of the array.`.

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

Nous reviendrons sur ce point plus tard lorsque nous évoquerons l’agrandissement d’un tableau.

### <a name="iteration"></a>Itération

À un moment donné, il peut être nécessaire de parcourir toute la liste et d’effectuer une action pour chacun des éléments du tableau.

#### <a name="pipeline"></a>Pipeline

Les tableaux et le pipeline PowerShell sont conçus pour fonctionner ensemble. Il s’agit de l’une des méthodes les plus simples pour traiter ces valeurs. Lorsque l’on transmet un tableau à un pipeline, chacun des éléments du tableau est traité individuellement.

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

Si vous n’avez pas encore rencontré `$PSItem`, sachez qu’il s’agit de la même chose que `$_`. Vous pouvez utiliser celui de votre choix, car ils représentent tous deux l’objet actuel dans le pipeline.

#### <a name="foreach-loop"></a>Boucle foreach

La boucle `ForEach` fonctionne bien avec les collections, suivant la syntaxe : `foreach ( <variable> in <collection> )`.

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a>Méthode foreach

Point que j’ai tendance à oublier, elle fonctionne bien pour les opérations simples. PowerShell autorise l’appel à `.ForEach()` sur une collection.

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

`.foreach()` accepte un paramètre qui est un bloc de script. Vous pouvez enlever les parenthèses pour n’indiquer que le bloc de script.

```powershell
$data.foreach{"Item [$PSItem]"}
```

Cette syntaxe, moins connue, fonctionne exactement de la même façon. Cette méthode `foreach` a été ajoutée dans la version 4.0 de PowerShell.

#### <a name="for-loop"></a>Boucle for

La boucle `for`, très utilisée dans la plupart des langages, l’est assez peu dans PowerShell. Quand on la rencontre, c’est souvent dans le contexte d’un parcours de tableau.

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

La première chose à faire est d’initialiser un `$index` à `0`. Ensuite, nous ajoutons la condition selon laquelle `$index` doit être inférieur à `$data.count`. Enfin, nous spécifions que, à chaque itération, l’index doit augmenter de `1`. Dans ce cas, `$index++` est la version abrégée de `$index = $index + 1`.

Chaque fois que vous utilisez une boucle `for`, portez une attention particulière à la condition. Il s’agit ici de `$index -lt $data.count`. Il est facile de se tromper sur la condition en introduisant par erreur un décalage de un dans la logique. `$index -le $data.count` et `$index -lt ($data.count - 1)` sont incorrects. En résulterait le traitement de trop ou trop peu d’éléments dans le résultat. Il s’agit de l’erreur classique de décalage de un.

#### <a name="switch-loop"></a>Boucle switch

On peut facilement passer à côté de cette boucle. Si l’on donne un tableau à une [instruction switch][], elle vérifie chacun des éléments du tableau.

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

L’instruction switch présente de nombreuses applications intéressantes. Voir à ce sujet l’article suivant :

- [Tout ce que vous avez toujours voulu savoir sur l’instruction switch][instruction switch]

#### <a name="updating-values"></a>Mise à jour des valeurs

Lorsque le tableau est une collection de chaînes ou d’entiers (types valeur), il peut être intéressant de mettre à jour les valeurs dans le tableau au fur et à mesure qu’il est parcouru. La plupart des boucles ci-dessus comportent une variable contenant une copie de la valeur. Si l’on met à jour cette variable, la valeur d’origine dans le tableau n’est pas mise à jour.

Il existe une exception à cette règle : la boucle `for`. Elle permet de parcourir un tableau et de mettre à jour des valeurs à l’intérieur.

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

Cet exemple prend une valeur par son index, effectue quelques modifications, puis utilise ce même index pour la réassigner.

## <a name="arrays-of-objects"></a>Tableaux d'objets

Jusqu’à présent, la seule chose que nos tableaux comportaient était un type valeur, mais ils peuvent également contenir des objets.

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

De nombreuses cmdlets retournent des collections d’objets sous forme de tableaux lorsqu’elles sont assignées à une variable.

```powershell
$processList = Get-Process
```

Toutes les fonctionnalités de base que nous avons déjà évoquées s’appliquent aussi à des tableaux d’objets ; cependant, certains points méritent d’être soulignés.

### <a name="accessing-properties"></a>Accès aux propriétés

Il est possible d’utiliser un index pour accéder à un élément individuel dans une collection, comme avec les types valeur.

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

Les propriétés sont accessibles et peuvent être mises à jour directement.

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a>Propriétés des tableaux

Il faut normalement énumérer ainsi l’ensemble de la liste pour accéder à toutes les propriétés :

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

Il est également possible d’utiliser la cmdlet `Select-Object -ExpandProperty`.

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

Cependant, PowerShell offre la possibilité de demander directement `LastName`. PowerShell les énumère tous automatiquement et retourne une liste nettoyée.

```powershell
PS> $data.LastName

Marquette
Doe
```

L’énumération se produit toujours, mais la complexité sous-jacente n’est pas visible.

### <a name="where-object-filtering"></a>Filtrage Where-Object

C’est là qu’intervient `Where-Object`, qui permet de filtrer et de sélectionner des objets à extraire du tableau en fonction de leurs propriétés.

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

Il est possible d’écrire la même requête pour obtenir le `FirstName` recherché.

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a>Where()

Les tableaux comportent une méthode `Where()` qui permet de spécifier un `scriptblock` pour le filtre.

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

Cette fonctionnalité a été ajoutée dans la version 4.0 de PowerShell.

### <a name="updating-objects-in-loops"></a>Mise à jour des objets dans les boucles

Avec les types valeur, la seule façon de mettre à jour le tableau consiste à utiliser une boucle for, car il faut connaître l’index pour remplacer la valeur. Les objets offrent davantage de possibilités, car il s’agit de types référence. Voici un exemple rapide :

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

Cette boucle parcourt chaque objet du tableau `$data`. Étant donné que les objets sont des types référence, la variable `$person` fait précisément référence à l’objet qui se trouve dans le tableau. Ainsi, mettre à jour ses propriétés a pour effet de mettre à jour l’original.

Il n’est cependant pas possible de remplacer l’intégralité de l’objet de cette façon. Si vous essayez d’assigner un nouvel objet à la variable `$person`, vous mettez à jour la référence de variable sur une autre valeur qui ne pointe plus vers l’objet d’origine du tableau, ce qui ne donne pas le résultat attendu :

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a>Opérateurs

Les opérateurs de PowerShell fonctionnent également sur les tableaux. Certains ont un comportement légèrement différent.

### <a name="-join"></a>-join

L’opérateur `-join` étant le plus évident, examinons-le en premier. Il est très intéressant à utiliser. Il joint tous les éléments du tableau avec le caractère ou la chaîne spécifié.

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

L’une des fonctionnalités les plus utiles de l’opérateur `-join` est le fait qu’il gère les éléments uniques.

```powershell
PS> 1 -join '-'
1
```

C’est particulièrement pratique dans les messages de journalisation et les commentaires.

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a>-join $array

Voici une astuce intelligente signalée par Lee Dailey. Pour tout joindre sans délimiteur, au lieu de procéder ainsi :

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

Il est possible d’utiliser `-join` en mettant le tableau en paramètre sans préfixe. Regardez cet exemple pour en voir une illustration.

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a>-replace et -split

Les autres opérateurs, comme `-replace` et `-split`, s’exécutent sur chacun des éléments du tableau. Je ne pense pas les avoir déjà utilisés de cette manière, mais en voici un exemple.

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a>-contains

L’opérateur `-contains` permet de regarder si un tableau de valeurs contient une valeur spécifiée.

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a>-in

Pour vérifier la correspondance entre une valeur unique et différentes valeurs, vous pouvez utiliser l’opérateur `-in`. La valeur se trouve du côté gauche et le tableau du côté droit de l’opérateur.

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

Cette opération peut être coûteuse si la liste est volumineuse. Un modèle regex peut se révéler utile quand il y a de nombreuses valeurs à vérifier.

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a>-eq et -ne

L’égalité peut être compliquée avec les tableaux. Lorsque le tableau se trouve sur le côté gauche, chacun des éléments est comparé. Au lieu de retourner `True`, elle retourne l’objet qui correspond.

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

L’opérateur `-ne` donne toutes les valeurs qui ne sont pas égales à la valeur spécifiée.

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

Si l’opérateur se trouve dans une instruction `if()`, la valeur retournée correspond à une valeur `True`. Si aucune valeur n’est retournée, il s’agit d’une valeur `False`. Les deux instructions suivantes prennent la valeur `True`.

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

Nous reviendrons sur ce sujet lorsque nous parlerons des tests `$null`.

### <a name="-match"></a>-match

L’opérateur `-match` tente de faire correspondre chacun des éléments de la collection.

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

Si `-match` est utilisé avec une valeur unique, une variable spéciale `$Matches` est remplie avec les informations de correspondance. Ce n’est pas le cas lorsque l’on traite un tableau.

Il est possible d’adopter la même approche avec `Select-String`.

```powershell
$servers | Select-String SQL
```

`Select-String`, `-match` et la variable `$matches` sont examinés plus en détail dans un autre billet intitulé [Les nombreuses façons d’utiliser les regex][].

### <a name="null-or-empty"></a>$null ou vide

Il peut être difficile de tester les tableaux `$null` ou vides. Voici les pièges courants des tableaux.

Au premier coup d’œil, cette instruction semble fonctionner.

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

Cependant, nous venons de voir comment `-eq` vérifie chacun des éléments du tableau. Avec un tableau de plusieurs éléments comportant une seule valeur $null, le résultat serait donc `$true`.

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

C’est la raison pour laquelle il est recommandé de placer `$null` du côté gauche de l’opérateur. Ce scénario devient un faux problème.

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

Un tableau `$null` n’est pas la même chose qu’un tableau vide. Si vous savez qu’il s’agit d’un tableau, vérifiez le nombre d’objets qu’il contient. Si le tableau est `$null`, le nombre est `0`.

```powershell
if ( $array.count -gt 0 )
{
    'Array isn't empty'
}
```

Il existe un autre piège à surveiller. Il est possible d’utiliser `count` même s’il n’y a qu’un seul objet, sauf si cet objet est un `PSCustomObject`. Ce bogue a été résolu dans la version 6.1 de PowerShell,
ce qui est une bonne nouvelle. Cependant, nombreux sont ceux qui utilisent toujours la version 5.1 et doivent faire attention à ce point.

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

Si c’est votre cas, vous pouvez encapsuler l’objet dans un tableau avant de compter les éléments pour obtenir un nombre exact.

```powershell
if ( @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

Pour jouer la sécurité totale, vérifiez si le tableau est `$null`, puis comptez les éléments.

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

### <a name="all--eq"></a>Tout -eq

Récemment, quelqu’un a demandé [comment vérifier la correspondance entre chacune des valeurs d’un tableau et une valeur donnée][].
L’utilisateur Reddit **/u/bis** a proposé cette [Solution][], qui recherche les valeurs incorrectes, puis inverse le résultat.

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a>Ajout d’éléments à des tableaux

La question est maintenant de savoir comment ajouter des éléments à un tableau. La réponse rapide est que ce n’est pas possible. Un tableau a une taille fixe en mémoire. Pour l’agrandir ou y ajouter un seul élément, il faut créer un nouveau tableau et copier toutes les valeurs de l’ancien tableau. On pourrait croire que c’est beaucoup de travail, mais en fait PowerShell masque la complexité liée à la création du nouveau tableau. PowerShell implémente l’opérateur d’addition (`+`) pour les tableaux.

> [!NOTE]
> PowerShell n’implémente pas d’opération de soustraction. Si vous voulez une alternative flexible à un tableau, vous devez utiliser un objet [générique `List`](#generic-list).

### <a name="array-addition"></a>Ajout de tableaux

Il est possible d’utiliser l’opérateur d’addition avec des tableaux pour en créer un nouveau. Prenons donc les deux tableaux suivants :

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

Nous pouvons les ajouter ensemble pour obtenir un nouveau tableau.

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a>Plus égal +=

Il est possible de créer un nouveau tableau sur place et d’y ajouter un élément :

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

N’oubliez pas que, chaque fois que vous utilisez `+=`, vous dupliquez et créez un nouveau tableau. Si ce n’est pas un problème pour les petits jeux de données, la scalabilité est en revanche extrêmement mauvaise.

### <a name="pipeline-assignment"></a>Assignation de pipeline

Vous pouvez assigner les résultats de n’importe quel pipeline dans une variable. Il s’agit d’un tableau s’il contient plusieurs éléments.

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

En général, les pipelines PowerShell classiques à une ligne sont ceux qui viennent le plus souvent à l’esprit. Il est possible d’exploiter le pipeline avec des instructions `foreach()` et d’autres boucles. Au lieu d’ajouter des éléments à un tableau dans une boucle, nous pouvons ainsi déposer des éléments sur le pipeline.

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

## <a name="array-types"></a>Types de tableaux

Par défaut, un tableau dans PowerShell est créé avec le type `[PSObject[]]`. Cela lui permet de contenir n’importe quel type d’objet ou de valeur, car tout est hérité du type de `PSObject`.

### <a name="strongly-typed-arrays"></a>Tableaux fortement typés

On peut créer un tableau de n’importe quel type suivant une syntaxe similaire. Un tableau fortement typé ne peut contenir que des valeurs ou des objets du type spécifié.

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a>ArrayList

L’ajout d’éléments à un tableau est l’une de ses principales limitations, mais il existe d’autres collections qui permettent de résoudre ce problème.

`ArrayList` est généralement l’une des premières solutions qui viennent à l’esprit lorsque l’on a besoin d’un tableau plus rapide à utiliser. Elle fonctionne comme un tableau d’objets là où c’est nécessaire, mais gère rapidement l’ajout d’éléments.

Voici comment créer une `ArrayList` et y ajouter des éléments.

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

Nous appelons .NET pour obtenir ce type. Dans ce cas, nous utilisons le constructeur par défaut pour le créer. Ensuite, nous appelons la méthode `Add` afin d’y ajouter un élément.

La présence de `[void]` au début de la ligne permet de supprimer le code de retour. Certains appels .NET produisent en effet une sortie inattendue.

Si les seules données du tableau sont des chaînes, examinez également [StringBuilder][]. Il s’agit presque de la même chose, mais certaines de ses méthodes servent uniquement à traiter les chaînes. `StringBuilder` est spécialement conçu pour optimiser les performances.

Il est courant de voir des gens abandonner les tableaux pour passer aux `ArrayList`. Cependant, cette pratique provient de l’époque où C# ne bénéficiait pas d’une prise en charge générique. `ArrayList` est déprécié en faveur de la `List[]` générique.

### <a name="generic-list"></a>List générique

Un type générique est un type spécial dans C# qui définit une classe généralisée ; l’utilisateur spécifie les types de données qu’il utilise lors de sa création. Pour obtenir une liste de nombres ou de chaînes, vous devez donc définir une liste de types `int` ou `string`.

Voici comment créer une liste de chaînes.

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

Et voici une liste de nombres.

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

Il est possible d’effectuer une conversion de type (transtypage) d’un tableau existant en une liste comme celle-ci sans créer l’objet au préalable :

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

La syntaxe peut être raccourcie avec l’instruction `using namespace` dans la version 5 et les versions ultérieures de PowerShell. L’instruction `using` doit apparaître en première ligne du script. Avec PowerShell, déclarer un espace de noms permet d’éviter de le mentionner dans les types de données lorsque vous y faites référence.

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

`List` devient ainsi bien plus facile à utiliser.

Il existe une méthode `Add` similaire. Contrairement à ArrayList, il n’y a aucune valeur de retour sur la méthode `Add` ; il n’est donc pas nécessaire de la rendre `void`.

```powershell
$myList.Add(10)
```

Comme pour les autres tableaux, les éléments restent accessibles.

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a>List[PSObject]

Une liste peut être de n’importe quel type. Cependant, si vous ne connaissez pas le type des objets, vous pouvez utiliser `[List[PSObject]]` pour les contenir.

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a>Remove()

`ArrayList` et la `List[]` générique prennent tous deux en charge la suppression d’éléments de la collection.

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

Si vous utilisez des types valeur, il supprime le premier de la liste. Vous pouvez l’appeler à nouveau pour continuer à supprimer cette valeur. Avec des types référence, vous devez indiquer l’objet que vous souhaitez supprimer.

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

La méthode remove retourne `true` si elle a pu trouver l’élément et le supprimer de la collection.

### <a name="more-collections"></a>Autres collections

De nombreuses autres collections peuvent être utilisées, mais nous avons vu les bonnes solutions génériques de remplacement des tableaux.
Pour plus d’informations sur ces autres options, consultez ce [Guist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) compilé par [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html).

## <a name="other-nuances"></a>Autres nuances

Maintenant que nous avons couvert toutes les fonctionnalités majeures, voici quelques points importants à signaler avant de conclure.

### <a name="pre-sized-arrays"></a>Tableaux de taille prédéfinie

Nous avons indiqué que la taille d’un tableau n’est pas modifiable une fois qu’il a été créé. Il est possible de créer un tableau d’une taille prédéfinie en l’appelant avec le constructeur `new($size)`.

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a>Multiplication de tableaux

Petite astuce intéressante : il est possible de multiplier un tableau par un entier.

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a>Initialisation avec 0

Il arrive fréquemment que l’on doive créer un tableau comportant uniquement des zéros. S’il n’est censé contenir que des entiers, vous pouvez utiliser un tableau fortement typé d’entiers, par défaut défini sur des zéros.

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

L’astuce de la multiplication permet également de parvenir à ce résultat.

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

L’avantage de la multiplication est qu’elle permet d’utiliser n’importe quelle valeur. C’est un bon moyen d’obtenir par exemple `255` comme valeur par défaut.

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a>Tableaux imbriqués

Un tableau qui se trouve à l’intérieur d’un tableau est appelé tableau imbriqué. Je ne les utilise pas beaucoup dans PowerShell, à la différence d’autres langages. Envisagez d’avoir recours à un tableau de tableaux lorsque vos données suivent un modèle de type grille.

Voici deux façons de créer un tableau à deux dimensions.

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

La virgule est très importante dans ces exemples. Dans le précédent exemple de tableau normal sur plusieurs lignes, la virgule était facultative. Ce n’est pas le cas avec un tableau multidimensionnel.

La notation d’index change légèrement avec un tableau imbriqué. Reprenons `$data` de l’exemple ci-dessus. La valeur 3 est accessible de la façon suivante :

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

Ajoutez un ensemble de crochets pour chaque niveau d’imbrication de tableau. Le premier concerne le tableau situé le plus à l’extérieur, et ainsi de suite.

### <a name="write-output--noenumerate"></a>Write-Output -NoEnumerate

PowerShell a tendance à désenvelopper ou énumérer les tableaux. Il s’agit d’un aspect fondamental de la façon dont il utilise le pipeline. Cependant, ce comportement n’est pas toujours souhaitable.

J’utilise souvent le pipe pour envoyer les objets vers `Get-Member` afin d’en savoir plus à leur sujet. Lorsqu’il s’agit d’un tableau, il est désenveloppé ; Get-Member voit ses membres et non le tableau proprement dit.

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

Pour éviter cette désencapsulation du tableau, vous pouvez utiliser `Write-Object -NoEnumerate`.

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

Il existe un deuxième moyen de le faire, moins conventionnel et potentiellement à éviter. Vous pouvez placer une virgule devant le tableau avant d’utiliser le pipe.

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a>Tableau retourné

Ce désenveloppement des tableaux se produit également lorsqu’une fonction renvoie ou retourne des valeurs. Ce n’est généralement pas un problème, car il reste possible d’obtenir un tableau si la sortie est assignée à une variable.

Cependant, il s’agit alors d’un nouveau tableau. Si ce point pose problème, vous pouvez utiliser `Write-Output -NoEnumerate $array` ou `return ,$array` pour le contourner.

## <a name="anything-else"></a>Autre chose ?

Cet article comprend beaucoup d’informations. Nous espérons qu’il vous apprendra quelque chose chaque fois que vous le lirez et qu’il vous servira longtemps de référence. S’il vous a été utile, veuillez le partager avec d’autres personnes qui pourraient le trouver intéressant.

Nous vous recommandons de consulter maintenant un billet similaire sur les [tables de hachage][].

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Tableaux]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Instruction switch]: everything-about-switch.md
[Tables de hachage]: everything-about-hashtable.md
[Les nombreuses façons d’utiliser les regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[Comment vérifier la correspondance entre chacune des valeurs d’un tableau et une valeur donnée]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[Solution]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
