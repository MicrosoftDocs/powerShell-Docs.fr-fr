---
title: Tout ce que vous avez toujours voulu savoir sur les tables de hachage
description: Les tables de hachage sont très importantes dans PowerShell, c’est pourquoi il est judicieux de parfaitement les maîtriser.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 60a5172485b9caf6343f54194563cd048648206e
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149512"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a>Tout ce que vous avez toujours voulu savoir sur les tables de hachage

Revenons en arrière pour parler des [tables de hachage][]. Je les utilise tout le temps maintenant. Je les expliquais hier soir à quelqu’un, après la réunion de notre groupe d'utilisateurs, et je me suis rendu compte que j’avais les mêmes lacunes que lui. Les tables de hachage sont très importantes dans PowerShell, c’est pourquoi il est judicieux de parfaitement les maîtriser.

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu. Consultez son blog à l’adresse [PowerShellExplained.com][].

## <a name="hashtable-as-a-collection-of-things"></a>Table de hachage comme collection d’objets

J’aimerais vous présenter tout d’abord le concept de **table de hachage** comme collection dans la définition traditionnelle d’une table de hachage. Cette définition vous donne une compréhension fondamentale de la façon dont les tables de hachage fonctionnent quand elles sont utilisées ultérieurement pour des éléments plus avancés. Omettre cette définition constitue souvent une source de confusion.

## <a name="what-is-an-array"></a>Qu’est-ce qu’un tableau ?

Avant de passer à la définition d’une **table de hachage**, examinons d’abord les [tableaux][]. Dans le cadre de cette discussion, un tableau est une liste ou une collection de valeurs ou d’objets.

```powershell
$array = @(1,2,3,5,7,11)
```

Une fois que vous avez placé vos éléments dans un tableau, vous pouvez utiliser `foreach` pour effectuer une itération au sein de la liste, ou utiliser un index pour accéder à des éléments individuels du tableau.

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

Vous pouvez de la même façon mettre à jour les valeurs à l’aide d’un index.

```powershell
$array[2] = 13
```

Je n’ai fait qu’effleurer le concept des tableaux, mais cela devrait les placer dans le contexte approprié au moment d’aborder les tables de hachage.

## <a name="what-is-a-hashtable"></a>Qu’est-ce qu’une table de hachage ?

Je commencerai par une description technique de base de ce que sont les tables de hachage, d’une manière générale, avant de passer aux autres méthodes utilisées par PowerShell.

Une table de hachage est une structure de données, à l’instar d’un tableau, sauf que vous stockez chaque valeur (objet) à l’aide d’une clé. Il s’agit d’un magasin de clés/valeurs de base. Commençons par créer une table de hachage vide.

```powershell
$ageList = @{}
```

Notez que des accolades, et non des parenthèses, servent à définir une table de hachage. Ajoutons ensuite un élément à l’aide d’une clé comme celle-ci :

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

Le nom de la personne représente la clé, et son âge correspond à la valeur que je souhaite enregistrer.

## <a name="using-the-brackets-for-access"></a>Utilisation de crochets pour l’accès

Après avoir ajouté vos valeurs à la table de hachage, vous pouvez les extraire à l’aide de cette même clé (au lieu d’utiliser un index numérique comme vous le feriez pour un tableau).

```powershell
$ageList['Kevin']
$ageList['Alex']
```

Pour connaître l’âge de Kevin, j’utilise son nom pour y accéder. Nous pouvons également utiliser cette approche pour ajouter ou mettre à jour des valeurs dans la table de hachage, exactement comme si vous utilisiez la fonction `add()` ci-dessus.

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

Vous pouvez utiliser une autre syntaxe pour accéder et mettre à jour les valeurs que je couvrirai dans une section ultérieure. Si vous passez à PowerShell à partir d’un autre langage, ces exemples devraient vous rappeler la façon dont vous utilisiez les tables de hachage auparavant.

### <a name="creating-hashtables-with-values"></a>Création de tables de hachage avec des valeurs

Jusqu’à présent, j’ai créé une table de hachage vide pour ces exemples. Vous pouvez préremplir les clés et les valeurs lors de leur création.

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a>Comme table de recherche

Ce type de table de hachage est particulièrement utile en tant que table de recherche. Voici un exemple simple.

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

Dans cet exemple, vous spécifiez un environnement pour la variable `$env`, et celle-ci choisit le serveur approprié. Vous pouvez utiliser un élément `switch($env){...}` pour une sélection comme celle-ci, mais une table de hachage est une option intéressante.

Les avantages sont encore plus visibles quand vous générez dynamiquement la table de recherche en vue d’une utilisation ultérieure. Par conséquent, privilégiez cette approche lorsque vous avez besoin de référencer quelque chose. Je pense que les résultats seraient encore plus évidents si PowerShell ne filtrait pas de façon si efficace le canal avec `Where-Object`. Si vous vous retrouvez dans une situation où les performances sont importantes, cette approche doit être prise en compte.

Je ne dis pas qu’elle est plus rapide, mais elle s’adapte à la règle [Si les performances l’exigent, effectuez un test][].

#### <a name="multiselection"></a>Sélection multiple

En général, considérez une table de hachage comme une paire clé/valeur dans laquelle vous fournissez une clé pour obtenir une valeur. PowerShell vous permet de fournir un tableau de clés pour obtenir plusieurs valeurs.

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

Dans cet exemple, j’utilise la même table de hachage de recherche que ci-dessus et je fournis trois styles de tableaux différents pour obtenir les correspondances. Il s’agit d’une fonction secrète de PowerShell que la plupart des utilisateurs ignorent.

## <a name="iterating-hashtables"></a>Itérations de tables de hachage

Étant donné qu’une table de hachage est une collection de paires clé/valeur, vous pouvez effectuer une itération différemment de celle d’un tableau ou d’une liste d’éléments standard.

La première chose à noter est que si vous dirigez votre table de hachage, le canal le traite comme un objet,

```powershell
PS> $ageList | Measure-Object
count : 1
```

même si la propriété `.count` vous indique le nombre de valeurs qu’elle contient.

```powershell
PS> $ageList.count
2
```

Pour résoudre ce problème, utilisez la propriété `.values` si vous n’avez besoin que des valeurs.

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

Il est souvent plus utile d’énumérer les clés et de les utiliser pour accéder aux valeurs.

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

Voici le même exemple avec une boucle `foreach(){...}`.

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

Nous allons parcourir chaque clé de la table de hachage, puis l’utiliser pour accéder à la valeur. Il s’agit d’un modèle courant lors de l’utilisation de tables de hachage en tant que collection.

### <a name="getenumerator"></a>GetEnumerator()

Cela nous amène à l’instruction `GetEnumerator()`, qui permet d’effectuer une itération dans notre table de hachage.

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

L’énumérateur vous fournit chaque paire clé/valeur, l’une après l’autre. Il a été conçu spécifiquement pour ce cas d’utilisation. Je tiens à remercier [Mark Kraus](https://get-PowerShellblog.blogspot.com) de m’avoir rappelé ce point.

### <a name="badenumeration"></a>BadEnumeration

Un détail important est que vous ne pouvez pas modifier une opération de hachage pendant son énumération. Si nous commençons par notre exemple `$environments` de base :

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

Toute tentative de définition de chaque clé avec la même valeur de serveur échoue.

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

C’est également le cas même s’il semble que l’opération va réussir :

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

dans cette situation, l’astuce consiste à cloner les clés avant d’effectuer l’énumération.

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a>Table de hachage comme collection de propriétés

Jusqu’à présent, tous les types d’objets que nous avons placés dans la table de hachage étaient identiques. J’ai utilisé des âges dans tous ces exemples, et la clé était le nom de la personne. C’est une excellente méthode lorsque les objets de votre collection portent tous un nom. Une autre façon courante d’utiliser des tables de hachage dans PowerShell consiste à conserver une collection de propriétés où la clé est le nom de la propriété. Nous allons aborder ce concept dans l’exemple suivant.

### <a name="property-based-access"></a>Accès basé sur les propriétés

L’utilisation de l’accès basé sur les propriétés modifie la dynamique des tables de hachage et la manière dont vous pouvez les utiliser dans PowerShell. Voici un exemple standard dans lequel les clés sont traitées comme des propriétés.

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

Comme les exemples ci-dessus, cet exemple ajoute ces clés s’ils n’existent pas déjà dans la table de hachage. Selon la façon dont vous avez défini vos clés et ce que représentent vos valeurs, cette méthode peut générer un résultat quelque peu étrange ou parfait. L’exemple de liste d’âges a fonctionné jusqu’à ce stade. Nous avons besoin d’un nouvel exemple pour que cela continue de fonctionner.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

Nous pouvons ajouter des attributs et y accéder au niveau de `$person`.

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

Et soudain, cette table de hachage commence à ressembler à un véritable objet. Mais il s’agit toujours d’un ensemble de choses, et tous les exemples ci-dessus continueront donc de s’appliquer. Nous nous plaçons simplement d’un autre point de vue.

### <a name="checking-for-keys-and-values"></a>Recherche de clés et de valeurs

Dans la plupart des cas, vous pouvez simplement tester la valeur avec un nom semblable à celui-ci :

```powershell
if( $person.age ){...}
```

Bien que simple, cette méthode est une source de nombreuses erreurs pour moi car j’ai négligé un détail important dans ma logique. J’ai commencé à l’utiliser pour vérifier la présence d’une clé. Lorsque la valeur était `$false` ou égale à zéro, cette instruction retournait `$false` de manière inattendue.

```powershell
if( $person.age -ne $null ){...}
```

Cette méthode contourne ce problème pour les valeurs zéro, mais pas pour les clés $null et inexistantes. La plupart du temps, vous n’avez pas besoin de faire cette distinction, mais il existe des fonctions où cela est nécessaire.

```powershell
if( $person.ContainsKey('age') ){...}
```

Nous disposons également d’une instruction `ContainsValue()` pour le cas où vous devez tester une valeur sans connaître la clé ou itérer l’intégralité de la collection.

### <a name="removing-and-clearing-keys"></a>Suppression et effacement de clés

Vous pouvez supprimer des clés à l’aide de la fonction `.Remove()`.

```powershell
$person.remove('age')
```

L’attribution d’une valeur `$null` a des clés vous laisse une seule clé avec une valeur `$null`.

Une méthode courante pour effacer une table de hachage consiste à l’initialiser simplement afin d’obtenir une table de hachage vide.

```powershell
$person = @{}
```

Bien que cela fonctionne, essayez plutôt d’utiliser la fonction `clear()`.

```powershell
$person.clear()
```

Il s’agit de l’une des instances où l’utilisation de la fonction crée du code autodocumenté et rend les intentions du code très claires.

## <a name="all-the-fun-stuff"></a>Amusons-nous un peu

### <a name="ordered-hashtables"></a>Tables de hachage ordonnées

Par défaut, les tables de hachage ne sont pas ordonnées (ou triées). Dans le contexte traditionnel, l’ordre n’a pas d’importance lorsque vous utilisez toujours une clé pour accéder aux valeurs. Vous souhaiterez peut-être conserver les propriétés dans l’ordre dans lequel vous les définissez. Heureusement, il existe un moyen de le faire grâce au mot clé `ordered`.

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

Désormais, lorsque vous énumérez les clés et les valeurs, elles restent dans cet ordre.

### <a name="inline-hashtables"></a>Tables de hachage en ligne

Lorsque vous définissez une table de hachage sur une ligne, vous pouvez séparer les paires clé/valeur par un point-virgule.

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

Cela s’avère pratique si vous les créez sur le canal.

### <a name="custom-expressions-in-common-pipeline-commands"></a>Expressions personnalisées dans les commandes de pipeline courantes

Il existe quelques applets de commande qui prennent en charge l’utilisation de tables de hachage pour créer des propriétés personnalisées ou calculées. C’est généralement le cas avec `Select-Object` et `Format-Table`. Les tables de hachage comportent une syntaxe spéciale qui ressemble à celle-ci lorsqu’elle est entièrement développée.

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

`name` correspond à la façon dont l’applet de commande étiquetterait cette colonne. `expression` est un bloc de script exécuté où `$_` est la valeur de l’objet sur le canal. Voici ce script en action :

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

Je l’ai placé dans une variable, mais il peut être facilement défini en ligne et vous pouvez raccourcir `name` en `n` et `expression` en `e` à cette étape.

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

Personnellement, je trouve ces commandes un peut trop longues et sources de comportements erronés sur lesquels je ne m’étendrai pas. Je préfère créer une table de hachage ou `pscustomobject` avec tous les champs et propriétés souhaités, au lieu d’utiliser cette approche dans les scripts. Mais il existe beaucoup de codes capables de le faire, et je tenais à vous en informer. Je parlerai de la création d’un objet `pscustomobject` un peu plus tard.

### <a name="custom-sort-expression"></a>Expression de tri personnalisée

Vous pouvez facilement trier une collection si les objets contiennent les données que vous souhaitez trier. Vous pouvez soit ajouter les données à l’objet avant de les trier, soit créer une expression personnalisée pour `Sort-Object`.

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

Dans cet exemple, je prends une liste d’utilisateurs et j’utilise une applet de commande personnalisée pour obtenir des informations supplémentaires uniquement à des fins de tri.

#### <a name="sort-a-list-of-hashtables"></a>Trier une liste de tables de hachage

Si vous souhaitez trier une liste de tables de hachage, vous constaterez que `Sort-Object` ne traite pas vos clés comme des propriétés. Nous pouvons contourner ce problème à l’aide d’une expression de tri personnalisée.

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a>Projection de tables de hachage au niveau d’applets de commande

C’est l’un de mes aspects préférés concernant les tables de hachage, et beaucoup d’utilisateurs n’en sont pas tout de suite conscients.
L’idée est que, au lieu de fournir toutes les propriétés à une applet de commande sur une seule ligne, vous pouvez d’abord les empaqueter dans une table de hachage. Vous pouvez ensuite fournir la table de hachage à la fonction d’une façon spéciale.
Voici un exemple de création d’une étendue DHCP de manière normale.

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

Si vous n’utilisez aucune [projection][], tous ces éléments doivent être définis sur une seule ligne. Cela permet de faire défiler l’écran ou d’encapsuler les éléments là où vous le souhaitez. Comparez maintenant cela à une commande qui utilise la projection.

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

L’utilisation du signe `@` à la place de `$` appelle l’opération de projection.

Prenez quelques instants pour apprécier la lisibilité de cet exemple. Cette commande est identique pour toutes les valeurs. La deuxième est plus facile à comprendre et à gérer à l’avenir.

J’utilise la projection chaque fois que la commande devient trop longue. Trop longue signifie que je dois faire défiler la fenêtre vers la droite. Si j’atteins trois propriétés pour une fonction, il est probable que je les réécrive à l’aide d’une table de hachage projetée.

### <a name="splatting-for-optional-parameters"></a>Projection de paramètres optionnels

L’une des méthodes les plus courantes d’utilisation de la projection consiste à gérer des paramètres facultatifs provenant d’autres emplacements dans mon script. Imaginons une fonction qui encapsule un appel `Get-CIMInstance` avec un argument `$Credential` facultatif.

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

Je commence par créer ma table de hachage avec des paramètres communs. Puis j’ajoute l’élément `$Credential`, s’il existe.
Comme j’utilise ici la projection, je n’ai besoin de l’appel à `Get-CIMInstance` dans mon code qu’une seule fois. Ce modèle de conception est très clair et permet de gérer facilement un grand nombre de paramètres facultatifs.

Pour être honnête, vous pouvez écrire vos commandes et autoriser ainsi des valeurs `$null` dans les paramètres. Vous n’avez tout simplement pas le contrôle sur les autres commandes que vous appelez.

### <a name="multiple-splats"></a>Projections multiples

Vous pouvez projeter plusieurs tables de hachage dans la même applet de commande. Si nous revenons à notre exemple de projection d’origine :

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

Je vais utiliser cette méthode avec un ensemble commun de paramètres que je passe à un grand nombre de commandes.

### <a name="splatting-for-clean-code"></a>Projection pour un code propre

Vous pouvez tout à fait effectuer une projection d’un seul paramètre si vous améliorez le code.

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a>Projection d’exécutables

La projection fonctionne également sur certains exécutables qui utilisent une syntaxe de type `/param:value`. `Robocopy.exe`, par exemple, possède des paramètres tels que celui-ci.

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

J’ignore si tout cela est vraiment utile, mais c’est assez intéressant.

## <a name="adding-hashtables"></a>Ajout de tables de hachage

Les tables de hachage prennent en charge l’opérateur d’addition pour combiner deux tables de hachage.

```powershell
$person += @{Zip = '78701'}
```

Cette approche fonctionne uniquement si les deux tables de hachage ne partagent aucune clé.

## <a name="nested-hashtables"></a>Tables de hachage imbriquées

Nous pouvons utiliser des tables de hachage comme valeurs à l’intérieur d’une table de hachage.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

J’ai commencé avec une table de hachage de base contenant deux clés. J’ai ajouté une clé nommée `location` avec une table de hachage vide. J’ai ensuite ajouté les deux derniers éléments à cette table de hachage `location`. Nous pouvons également effectuer toute cette procédure en ligne.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

Cela crée la même table de hachage que celle que nous étudiée ci-dessus et nous pouvons accéder aux propriétés de la même façon.

```powershell
$person.location.city
Austin
```powershell

There are many ways to approach the structure of your objects. Here is a second way to look at a
nested hashtable.

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

Cette méthode combine le concept d’utilisation de tables de hachage comme une collection d’objets et une collection de propriétés. Les valeurs restent facilement accessibles, même lorsqu’elles sont imbriquées à l’aide de l’approche de votre choix.

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

J’ai tendance à utiliser la propriété dot lorsque je la traite comme une propriété. Il s’agit généralement d’éléments qui me viennent à l’esprit et que j’ai définis de manière statique dans mon code. Si je dois parcourir la liste ou accéder par programmation aux clés, j’utilise les crochets pour fournir le nom de la clé.

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

La possibilité d’imbriquer des tables de hachage vous offre beaucoup de flexibilité et d’options.

### <a name="looking-at-nested-hashtables"></a>Examen des tables de hachage imbriquées

Dès que vous commencez à imbriquer des tables de hachage, vous aurez besoin d’une méthode simple pour les examiner à partir de la console. Si je sélectionne la dernière table de hachage, j’obtiens une sortie semblable à celle-ci :

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

Ma commande préférée pour examiner ces éléments est `ConvertTo-JSON` car elle est très claire, et j’utilise fréquemment JSON pour d’autres choses.

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

Même si vous ne connaissez pas JSON, vous devriez trouver ce que vous recherchez. Il existe une commande `Format-Custom` pour les données structurées comme celle-ci, mais je préfère néanmoins la méthode JSON.

## <a name="creating-objects"></a>Création d'objets

Parfois, vous n’avez besoin que d’un objet, et utiliser une table de hachage pour y conserver des propriétés ne répond pas à vos besoins. Le plus souvent, vous souhaitez afficher les clés en tant que noms de colonne. C’est facile avec l’élément `pscustomobject`.

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

Même si vous ne le créez pas en tant que `pscustomobject` initialement, vous pouvez toujours le convertir ultérieurement si nécessaire.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

J’ai déjà écrit un article détaillé concernant [pscustomobject][], que vous je vous conseille de lire après celui-ci. Il s’appuie sur un grand nombre des éléments appris ici.

## <a name="reading-and-writing-hashtables-to-file"></a>Lecture et écriture de tables de hachage dans un fichier

### <a name="saving-to-csv"></a>Enregistrement au format CSV

L’utilisation d’une table de hachage pour l’enregistrement au format CSV est l’un des problèmes auquel je faisais référence ci-dessus. Convertissez votre table de hachage en un objet `pscustomobject` afin de l’enregistrer correctement au format CSV. Cela vous permet de commencer avec un objet `pscustomobject` en préservant l’ordre des colonnes. Mais vous pouvez le convertir en un objet `pscustomobject` en ligne, si nécessaire.

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

Là encore, consultez mon article sur utilisation d’un objet [pscustomobject][].

### <a name="saving-a-nested-hashtable-to-file"></a>Enregistrement d’une table de hachage imbriquée dans un fichier

Si j’ai besoin d’enregistrer une table de hachage imbriquée dans un fichier, puis de la lire à nouveau, j’utilise pour cela les applets de commande JSON.

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

Il existe deux points importants à noter concernant cette méthode. Tout d’abord, l’objet JSON est écrit en mode multiligne et je dois donc utiliser l’option `-Raw` pour le relire dans une chaîne unique. Deuxièmement, l’objet importé n’est plus un objet `[hashtable]`. C’est maintenant un objet `[pscustomobject]` et cela peut provoquer des problèmes si vous ne vous y attendiez pas.

Si vous avez besoin d’un objet `[hashtable]` lors de l’importation, vous devez utiliser les commandes `Export-CliXml` et `Import-CliXml`.

### <a name="converting-json-to-hashtable"></a>Conversion d’un objet JSON en table de hachage

Si vous avez besoin de convertir un objet JSON en `[hashtable]`, vous pouvez utiliser [JavaScriptSerializer][] dans .NET.

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

### <a name="reading-directly-from-a-file"></a>Lecture directe à partir d’un fichier

Si vous utilisez un fichier contenant une table de hachage avec la syntaxe PowerShell, il existe un moyen de l’importer directement.

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

Cette procédure importe le contenu du fichier dans un objet `scriptblock`, puis vérifie s’il n’existe pas d’autres commandes PowerShell avant de l’exécuter.

Saviez-vous qu’un manifeste de module (fichier psd1) n’est en fait qu’une simple table de hachage ?

## <a name="keys-are-just-strings"></a>Les clés ne sont que des chaînes

Je n’ai pas voulu dévier vers ce sujet jusqu’à présent, mais les clés sont simplement des chaînes. Nous pouvons donc entourer de guillemets l’élément de notre choix pour le transformer en clé.

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

Vous pouvez ainsi créer des éléments très particuliers dont vous n’aviez probablement même pas idée.

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

Mais ce n’est pas parce que vous pouvez réaliser quelque chose que vous devez nécessaire le faire. Ce dernier exemple semble clairement annoncer qu’une erreur va se produire et risque d’être facilement mal interprété par quiconque lira votre code.

Techniquement, votre clé ne doit pas nécessairement être une chaîne, mais les opérations sont bien plus simples à réaliser si vous utilisez uniquement des chaînes.

## <a name="use-in-automatic-variables"></a>Utilisation dans des variables automatiques

### <a name="psboundparameters"></a>$PSBoundParameters

[$PSBoundParameters][] est une variable automatique qui n’existe que dans le contexte d’une fonction. Elle contient tous les paramètres avec lesquels la fonction a été appelée. Il ne s’agit pas exactement d’une table de hachage, mais elle y ressemble suffisamment pour la traiter en tant que telle.

Cela comprend la suppression des clés et leur projection dans d’autres fonctions. Si vous écrivez des fonctions de proxy, examinez cette variable plus en détail.

Pour plus d'informations, consultez [about_Automatic_Variables][].

### <a name="psboundparameters-gotcha"></a>Astuce PSBoundParameters

Une chose importante à retenir est que cette variable comprend uniquement les valeurs passées en tant que paramètres. Si vous utilisez également des paramètres avec des valeurs par défaut, mais qui ne sont pas transmises par l’appelant, `$PSBoundParameters` ne contient pas ces valeurs. Cet aspect est souvent négligé.

### <a name="psdefaultparametervalues"></a>$PSDefaultParameterValues

Cette variable automatique vous permet d’attribuer des valeurs par défaut à une applet de commande sans la modifier.
Prenons cet exemple :

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

Cette variable ajoute une entrée à la table de hachage `$PSDefaultParameterValues` qui définit `UTF8` comme valeur par défaut pour le paramètre `Out-File -Encoding`. Ceci est spécifique à la session et vous devez donc la placer dans votre `$profile`.

Je l’utilise souvent pour préattribuer des valeurs que je saisis très souvent.

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

Cette méthode accepte également les caractères génériques, ce qui vous permet de définir des valeurs en bloc. Voici d’autres exemples d’utilisation :

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

Pour une analyse plus approfondie, reportez-vous à cet article très intéressant sur [Valeurs automatiques par défaut][], écrit par [Michael Sorens][].

## <a name="regex-matches"></a>Regex $Matches

Lorsque vous utilisez l’opérateur `-match`, une variable automatique appelée `$matches` est créée avec les résultats de la correspondance. Si votre expression régulière contient des sous-expressions, ces sous-correspondances sont également répertoriées.

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a>Correspondances nommées

C’est l’une de mes fonctionnalités préférées, et que la plupart des utilisateurs ignorent. Si vous utilisez une correspondance regex nommée, vous pouvez accéder à cette correspondance en recherchant son nom.

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

Dans l’exemple ci-dessus, `(?<Name>.*)` est une sous-expression nommée. Cette valeur est ensuite placée dans la propriété `$Matches.Name`.

## <a name="group-object--ashashtable"></a>Group-Object -AsHashtable

L’une des fonctionnalités les moins connues de `Group-Object` est sa capacité à convertir des jeux de données en une table de hachage.

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

Cette opération ajoute chaque ligne à une table de hachage et utilise la propriété spécifiée comme clé pour y accéder.

## <a name="copying-hashtables"></a>Copie de tables de hachage

Il est important de savoir que les tables de hachage sont des objets. Et chaque variable est simplement une référence à un objet. Cela signifie qu’une copie valide d’une table de hachage demande plus de travail.

### <a name="assigning-reference-types"></a>Attribution de types de références

Quand vous avez une table de hachage et que vous l’attribuez à une deuxième variable, les deux variables pointent vers la même table de hachage.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

Cela a pour effet de les rendre identiques, car la modification des valeurs dans l’une modifie également les valeurs de l’autre. Cela s’applique également lors du passage de tables de hachage dans d’autres fonctions. Si ces fonctions apportent des modifications à cette table de hachage, votre table d’origine est également modifiée.

### <a name="shallow-copies-single-level"></a>Copies superficielles, niveau unique

Si nous utilisons une simple table de hachage telle que notre exemple ci-dessus, nous pouvons utiliser `.Clone()` pour effectuer une copie superficielle.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

Nous pourrons ainsi apporter des modifications de base dans l’une mais sans impacter l’autre.

### <a name="shallow-copies-nested"></a>Copies superficielles, imbriquées

La raison pour laquelle cette copie est dite superficielle vient du fait qu’elle copie uniquement les propriétés de niveau de base. Si l’une de ces propriétés est un type de référence (par exemple, une autre table de hachage), ces objets imbriqués pointent quand même les uns vers les autres.

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

Vous pouvez constater que même si j’ai cloné la table de hachage, la référence à `person` n’a pas été clonée. Nous devons effectuer une copie complète pour obtenir véritablement une seconde table de hachage non liée à la première.

### <a name="deep-copies"></a>Copies complètes

Au moment de rédiger cet article, je ne connaissais aucune solution efficace d’effectuer une copie complète d’une table de hachage (et de la conserver en tant que telle). Et ces informations devaient être écrites noir sur blanc.
Voici une méthode rapide pour cela.

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

Elle ne gère aucun un autre type de référence ou tableau, mais il s’agit d’un bon point de départ.

## <a name="anything-else"></a>Autre chose ?

J’ai abordé beaucoup de concepts dans cet article. Mon espoir est que vous puissiez apprendre quelque chose de nouveau ou approfondir vos connaissances à chaque lecture de cet article. Comme j’ai abordé le spectre complet de cette fonctionnalité, certains aspects ne s’appliquent pas à votre cas pour le moment. C’est tout à fait normal et attendu en fonction du volume du travail que vous effectuez avec PowerShell.

Voici une liste de tous les thèmes que nous avons abordés, au cas où vous souhaiteriez revenir sur un sujet particulier. En règle générale, cette liste est fournie en premier, mais elle a été écrite de haut en bas avec des exemples qui s’appuient sur tout ce qui précède.

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Tables de hachage]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[Tableaux]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Si les performances l’exigent, effectuez un test]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best%20Practices/Performance.md
[Projection]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Valeurs automatiques par défaut]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
