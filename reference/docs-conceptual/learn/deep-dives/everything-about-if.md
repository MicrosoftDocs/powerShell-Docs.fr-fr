---
title: Tout ce que vous avez toujours voulu savoir sur l’instruction IF
description: À l’instar de nombreux autres langages, PowerShell comporte des instructions pour l’exécution conditionnelle de code dans vos scripts.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6ffb70af694e80430d31991045b9fadc1a2cc3f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149522"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a>Tout ce que vous avez toujours voulu savoir sur l’instruction IF

À l’instar de nombreux autres langages, PowerShell comporte des instructions pour l’exécution conditionnelle de code dans vos scripts. L’une de ces instructions est l’instruction [if][]. Nous allons aujourd’hui étudier de manière approfondie l’une des commandes les plus fondamentales de PowerShell.

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu. Consultez son blog à l’adresse [PowerShellExplained.com][].

## <a name="conditional-execution"></a>Exécution conditionnelle

Vos scripts doivent souvent prendre des décisions et exécuter une logique différente en fonction de ces décisions.
C’est ce qu’on appelle une exécution conditionnelle. Vous avez une instruction ou une valeur à évaluer, et vous exécutez une autre section de code en fonction de cette évaluation. C’est là précisément qu’intervient l’instruction `if`.

## <a name="the-if-statement"></a>L’instruction if

Voici un exemple de base de l’instruction `if` :

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

L’instruction `if` commence par évaluer l’expression entre parenthèses. Si l’évaluation génère une valeur `$true`, elle exécute l’élément `scriptblock` entre les accolades. Si la valeur est `$false`, elle ignore cet élément scriptblock.

Dans l’exemple précédent, l’instruction `if` a simplement évalué la variable `$condition`. Cette valeur `$true` aurait exécuté la commande `Write-Output` à l’intérieur du scriptblock.

Dans certains langages, vous pouvez placer une simple ligne de code après l’instruction `if` afin de l’exécuter. Ce n’est pas le cas dans PowerShell. Vous devez fournir un élément `scriptblock` complet avec entre accolades pour que l’instruction fonctionne correctement.

## <a name="comparison-operators"></a>Opérateurs de comparaison

Le plus souvent, l’instruction `if` sert à comparer deux éléments. PowerShell propose des opérateurs spéciaux pour différents scénarios de comparaison. Lorsque vous utilisez un opérateur de comparaison, la valeur à gauche est comparée à la valeur à droite.

### <a name="-eq-for-equality"></a>-eq pour égalité

L’opérateur `-eq` vérifie l’égalité entre deux valeurs pour s’assurer qu’elles sont égales.

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

Dans cet exemple, je prends une valeur connue `5` et je la compare à ma valeur `$value` pour vérifier si elles correspondent.

Un cas d’utilisation possible consiste à vérifier l’état d’une valeur avant d’effectuer une action sur celle-ci. Vous pouvez obtenir un service et vérifier que l’état était en cours d’exécution avant d’appeler `Restart-Service` sur ce service.

Dans d’autres langages comme C#, il est courant d’utiliser `==` pour l’égalité (ex : `5 == $value`), mais cela ne fonctionne pas avec PowerShell. Une autre erreur courante commise consiste à utiliser le signe égal (ex : `5 = $value`) qui est réservé à l’attribution de valeurs aux variables. En plaçant votre valeur connue sur la partie gauche, vous limitez les risques de produire cette erreur.

Cet opérateur (et d’autres) comportent quelques variantes.

- `-eq` égalité, sans respect de la casse
- `-ieq` égalité, sans respect de la casse
- `-ceq` égalité, avec respect de la casse

### <a name="-ne-not-equal"></a>-ne non égal à

De nombreux opérateurs intègrent un opérateur associé qui vérifie le résultat inverse. `-ne` vérifie que les valeurs ne sont pas égales.

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

Utilisez-le pour vous assurer que l’action s’exécute uniquement si la valeur n’est pas `5`. Ce type d’opérateur est notamment utile pour vérifier si un service était à l’état en cours d’exécution avant d’essayer de le démarrer.

**Variantes :**

- `-ne` non égal à, sans respect de la casse
- `-ine` non égal à, sans respect de la casse
- `-cne` non égal à, avec respect de la casse

Il s’agit de variantes inverses de `-eq`. Je regroupe ces types lorsque je répertorie des variantes pour d’autres opérateurs.

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a>-gt -ge -lt -le pour supérieur à ou inférieur à

Ces opérateurs servent à vérifier si une valeur est supérieure ou inférieure à une autre valeur.
Les valeurs `-gt -ge -lt -le` signifient GreaterThan (supérieur à), GreaterThanOrEqual (supérieur ou égal à), LessThan (inférieur à) et LessThanOrEqual (inférieur ou égal à).

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

**Variantes :**

- `-gt` supérieur à
- `-igt` supérieur à, sans respect de la casse
- `-cgt` supérieur à, avec respect de la casse
- `-ge` supérieur ou égal à
- `-ige` supérieur ou égal à, sans respect de la casse
- `-cge` supérieur ou égal à, avec respect de la casse
- `-lt` inférieur à
- `-ilt` inférieur à, sans respect de la casse
- `-clt` inférieur à, avec respect de la casse
- `-le` inférieur ou égal à
- `-ile` inférieur ou égal à, sans respect de la casse
- `-cle` inférieur ou égal à, avec respect de la casse

Il n’y a aucune raison d’utiliser des options qui respectent ou non la casse pour ces opérateurs.

### <a name="-like-wildcard-matches"></a>-like correspondances de caractères génériques

PowerShell possède sa propre syntaxe de correspondance de modèles de caractères génériques, et vous pouvez l’utiliser avec l’opérateur `-like`. Ces modèles de caractères génériques sont assez simples.

- `?` représente n'importe quel caractère unique
- `*` représente n’importe quel nombre de caractères

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

Il est important de souligner que le modèle correspond à la chaîne entière. Si vous devez mettre en correspondance un élément au milieu de la chaîne, vous devez placer le symbole `*` aux deux extrémités de celle-ci.

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

**Variantes :**

- `-like` caractère générique, sans respect de la casse
- `-ilike` caractère générique, sans respect de la casse
- `-clike` caractère générique, avec respect de la casse
- `-notlike` caractère générique sans correspondance, sans respect de la casse
- `-inotlike` caractère générique sans correspondance, sans respect de la casse
- `-cnotlike` caractère générique sans correspondance, avec respect de la casse

### <a name="-match-regular-expression"></a>-match expression régulière

L’opérateur `-match` vous permet de vérifier la correspondance d’une chaîne en fonction d’une expression régulière. Utilisez cet opérateur si les modèles de caractères génériques ne vous offrent pas assez de souplesse.

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

Par défaut, un modèle d’expression régulière (regex) représente n’importe quelle partie de la chaîne. Vous pouvez donc définir la correspondance d’une sous-chaîne de la façon suivante :

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

Regex est un langage complexe, qui mérite d’être examiné. J’aborderai plus en détail l’opérateur `-match` et [les nombreuses façons d’utiliser regex][] dans un autre article.

**Variantes :**

- `-match` regex, sans respect de la casse
- `-imatch` regex, sans respect de la casse
- `-cmatch` regex, avec respect de la casse
- `-notmatch` regex sans correspondance, sans respect de la casse
- `-inotmatch` regex sans correspondance, sans respect de la casse
- `-cnotmatch` regex sans correspondance, avec respect de la casse

### <a name="-is-of-type"></a>-is de type

Vous pouvez vérifier le type d’une valeur à l’aide de l’opérateur `-is`.

```powershell
if ( $value -is [string] )
{
    # do something
}
```

Vous pouvez l’utiliser avec des classes ou pour accepter différents objets sur le pipeline. Vous pouvez utiliser un service ou un nom de service comme entrée. Puis pour vérifier si vous disposez d’un service et pour extraire le service si vous avez uniquement le nom.

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

**Variantes :**

- `-is` de type
- `-isnot` non de type

## <a name="collection-operators"></a>Ensemble d’opérateurs

Lorsque vous utilisez les opérateurs précédents avec une valeur unique, le résultat est `$true` ou `$false`. Avec un ensemble d’opérateurs, la procédure est légèrement différente. Chaque élément de l’ensemble est évalué, et l’opérateur retourne chaque valeur correspondant à `$true`.

```powershell
PS> 1,2,3,4 -eq 3
3
```

Cette méthode fonctionne également avec une instruction `if`. Par conséquent, une valeur est retournée par votre opérateur, puis l’instruction entière est `$true`.

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

Mais cette méthode cache un petit piège que je tiens à signaler. Lorsque vous utilisez l’opérateur `-ne` de cette manière, il est facile d’appliquer par erreur la logique de manière inversée. L’utilisation de `-ne` avec un ensemble d’opérateurs retourne `$true` si un élément de l’ensemble ne correspond pas à votre valeur.

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

Cela peut sembler astucieux, mais nous disposons des opérateurs `-contains` et `-in` encore plus efficaces. Et l’opérateur `-notcontains` répond exactement à vos besoins.

### <a name="-contains"></a>-contains

L’opérateur `-contains` recherche votre valeur dans l’ensemble. Dès qu’il trouve une correspondance, il retourne `$true`.

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

Il s’agit de la méthode recommandée pour déterminer si un ensemble contient votre valeur. L’utilisation de `Where-Object` (ou `-eq`) parcourt chaque fois la liste entière mais ce processus est beaucoup plus lent.

**Variantes :**

- `-contains` correspondance, sans respect de la casse
- `-icontains` correspondance, sans respect de la casse
- `-ccontains` correspondance, avec respect de la casse
- `-notcontains` sans correspondance, sans respect de la casse
- `-inotcontains` sans correspondance, sans respect de la casse
- `-cnotcontains` sans correspondance, avec respect de la casse

### <a name="-in"></a>-in

L’opérateur `-in` est similaire à l’opérateur `-contains`, sauf que l’ensemble se trouve sur le côté droit.

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

**Variantes :**

- `-in` correspondance, sans respect de la casse
- `-iin` correspondance, sans respect de la casse
- `-cin` correspondance, avec respect de la casse
- `-notin` sans correspondance, sans respect de la casse
- `-inotin` sans correspondance, sans respect de la casse
- `-cnotin` sans correspondance, avec respect de la casse

## <a name="logical-operators"></a>Opérateurs logiques

Les opérateurs logiques sont utilisés pour inverser ou combiner d’autres expressions.

### <a name="-not"></a>-not

L’opérateur `-not` retourne une expression de `$false` à `$true` ou de `$true` à `$false`. Voici un exemple dans lequel effectuer une action lorsque `Test-Path` est `$false`.

```powershell
if ( -not ( Test-Path -Path $path ) )
```

La plupart des opérateurs dont nous avons parlé proposent une variante dans laquelle vous n’avez pas besoin d’utiliser l’opérateur `-not`. Mais cet opérateur est parfois utile.

### <a name="-operator"></a>! operator

Vous pouvez utiliser `!` comme alias pour `-not`.

```powershell
if ( -not $value ){}
if ( !$value ){}
```

Peut-être avez-vous remarqué que l’opérateur `!` était davantage utilisé par les personnes qui maîtrisent d’autres langages, comme C# . Je préfère le saisir car j’ai parfois du mal à le repérer quand j’examine rapidement mes scripts.

### <a name="-and"></a>-and

Vous pouvez combiner des expressions avec l’opérateur `-and`. Dans ce cas, les deux côtés doivent être `$true` pour que l’expression entière soit `$true`.

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

Dans cet exemple, `$age` doit être supérieur ou égal à 13 pour le côté gauche, et inférieur à 55 pour le côté droit. J’ai ajouté d’autres parenthèses pour le rendre plus clair dans cet exemple, mais elles sont facultatives tant que l’expression est simple. Voici le même exemple sans parenthèses.

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

L’évaluation se produit de gauche à droite. Si le premier élément a la valeur `$false`, il s’arrête prématurément et n’effectue pas la comparaison appropriée. Cela est pratique lorsque vous devez vérifier qu’une valeur existe avant de l’utiliser. Par exemple, `Test-Path` génère une erreur si vous lui attribuez un chemin d’accès `$null`.

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a>-or

L’opérateur `-or` vous permet de spécifier deux expressions, et retourne `$true` si l’une d’elles est `$true`.

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

Comme avec l’opérateur `-and`, l’évaluation se produit de gauche à droite. Hormis le fait que si la première partie est `$true`, l’instruction entière est `$true` et elle ignore le reste de l’expression.

Notez également le fonctionnement de la syntaxe pour ces opérateurs. Vous avez besoin de deux expressions distinctes. Certains utilisateurs essaient d’effectuer une opération semblable à celle-ci `$value -eq 5 -or 6`, sans se rendre compte de leur erreur.

### <a name="-xor-exclusive-or"></a>-xor or exclusif

Cet opérateur est un peu particulier. `-xor` permet à une seule expression de renvoyer la valeur `$true`. Par conséquent, si les deux éléments sont `$false` ou `$true`, l’expression entière est `$false`. Cela revient à affirmer que cette expression est uniquement `$true` lorsque les résultats de l’expression sont différents.

Il est très peu probable qu’une personne utilise cet opérateur logique, et je ne vois aucun exemple où il pourrait être utile.

## <a name="bitwise-operators"></a>Opérateurs de bits

Les opérateurs de bits effectuent des calculs sur les bits dans les valeurs et génèrent une nouvelle valeur comme résultat. L’apprentissage des [opérateurs de bits][] dépasse le cadre de cet article, mais en voici la liste.

- `-band` binaire AND
- `-bor` binaire OR
- `-bxor` binaire OR exclusif
- `-bnot` binaire NOT
- `-shl` décalage vers la gauche
- `-shr` décalage vers la droite

## <a name="powershell-expressions"></a>Expressions PowerShell

Nous pouvons utiliser PowerShell normalement dans l’instruction de condition.

```powershell
if ( Test-Path -Path $Path )
```

`Test-Path` retourne `$true` ou `$false` lorsqu’il s’exécute. Cela s’applique également aux commandes qui retournent d’autres valeurs.

```powershell
if ( Get-Process Notepad* )
```

L’expression renvoie la valeur `$true` s’il existe un processus retourné, et `$false` dans le cas contraire. Vous pouvez tout à fait utiliser des expressions de pipeline ou d’autres instructions PowerShell comme suit :

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

Ces expressions peuvent être combinées avec les opérateurs `-and` et `-or`, mais vous devrez peut-être utiliser des parenthèses pour les décomposer en sous-expressions.

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a>Recherche de $null

Si vous n’obtenez aucun résultat ou une valeur `$null`, la valeur `$false` s’affiche dans l’instruction `if`. Lorsqu’il s’agit de vérifier spécifiquement `$null`, il est recommandé de placer `$null` sur le côté gauche.

```powershell
if ( $null -eq $value )
```

Il existe quelques nuances lorsque vous utilisez des valeurs `$null` dans PowerShell. Si vous souhaitez approfondir vos connaissances, j’ai préparé un article intitulé [Tout ce que vous avez toujours voulu savoir sur $null][].

### <a name="variable-assignment"></a>Attribution de variables

J’allais oublier d’ajouter cet opérateur jusqu’à ce que [Prasoon Karunan V][] me le rappelle.

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

Normalement, lorsque vous attribuez une valeur à une variable, la valeur n’est pas transmise au pipeline ni à la console. Lorsque vous attribuez une variable dans une sous-expression, elle est transmise au pipeline.

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

Vous remarquez que l’attribution de `$first` n’a pas de sortie, contrairement à l’attribution de `$second` ? Lorsqu’une attribution est effectuée dans une instruction `if`, elle s’exécute de la même manière que l’attribution `$second` ci-dessus. Voici un exemple d’utilisation assez clair :

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

Si une valeur est attribuée à `$process`, l’instruction est `$true` et `$process` s’arrête.

Veillez à ne pas confondre cela avec `-eq`, car il ne s’agit pas d’une vérification d’égalité. Il s’agit d’une fonctionnalité plus complexe dont la plupart des utilisateurs ignorent le processus.

## <a name="alternate-execution-path"></a>Autre chemin d'accès d'exécution

L’instruction `if` vous permet de spécifier une action non seulement lorsque l’instruction est `$true`, mais également quand elle est `$false`. C’est ici qu’intervient l’instruction `else`.

### <a name="else"></a>else

L’instruction `else` constitue toujours la dernière partie de l’instruction `if` lorsqu’elle est utilisée.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

Dans cet exemple, nous vérifions la valeur `$path` pour s’assurer qu’il s’agit d’un fichier. Si nous trouvons le fichier, nous le déplaçons. Sinon, nous créons un avertissement. Ce type de logique de création de branche est très courant.

### <a name="nested-if"></a>if imbriqué

Les instructions `if` et `else` prennent un bloc de script, ce qui nous permet de placer n’importe quelle commande PowerShell à l’intérieur de celles-ci, y compris une autre instruction `if`. Vous pouvez ainsi utiliser une logique bien plus complexe.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

Dans cet exemple, nous testons d’abord le bon chemin d’accès puis nous y effectuons une action. En cas d’échec, nous procédons à une autre vérification et fournissons des informations plus détaillées à l’utilisateur.

### <a name="elseif"></a>elseif

Nous ne sommes pas limités à une seule vérification conditionnelle. Nous pouvons chaîner des instructions `if` et `else` au lieu de les imbriquer à l’aide de l’instruction `elseif`.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

L’exécution s’effectue de haut en bas. L’instruction `if` en haut de la liste est évaluée en premier. Si la valeur est `$false`, l’instruction descend jusqu’au prochain élément `elseif` ou `else` dans la liste. Le dernier élément `else` est l’action par défaut à effectuer si aucune des autres ne retourne `$true`.

### <a name="switch"></a>commutateur

À ce stade, il est important de mentionner l’instruction `switch`. Cette instruction fournit une autre syntaxe permettant d’effectuer plusieurs comparaisons avec une valeur. Avec l’instruction `switch`, vous spécifiez une expression et ce résultat est comparé à plusieurs valeurs différentes. Si l’une de ces valeurs correspond, le bloc de code correspondant est exécuté. Prenons cet exemple :

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

trois valeurs possibles peuvent correspondre à `$itemType`. Dans ce cas, la valeur correspond à `Role`. J’ai utilisé un exemple simple pour vous présenter l’opérateur `switch`. J’aborderai plus en détail le thème [Tout ce que vous avez toujours voulu savoir sur l’instruction switch][] dans un autre article.

## <a name="pipeline"></a>Pipeline

Le pipeline est une fonctionnalité unique et importante de PowerShell. Toute valeur qui n’est pas supprimée ou affectée à une variable est placée dans le pipeline. L’instruction `if` permet de tirer parti du pipeline d’une manière qui n’est pas toujours évidente.

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

Chaque bloc de script place les résultats des commandes ou la valeur dans le pipeline. Nous attribuons ensuite le résultat de l’instruction if à la variable `$discount`. Cet exemple peut simplement attribuer ces valeurs à la variable `$discount` directement dans chaque élément scriptblock. Je ne dis pas que je l’utilise souvent avec l’instruction `if`, mais je me rappelle l’avoir fait récemment.

### <a name="array-inline"></a>Tableau en ligne

Voici une fonction appelée [Invoke-SnowSql][] qui lance un exécutable avec plusieurs arguments de ligne de commande. Voici un clip dans lequel j’utilise cette fonction pour créer le tableau d’arguments.

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

Les variables `$Debug` et `$Path` sont des paramètres de la fonction, fournis par l’utilisateur final.
Je les évalue en ligne dans l’initialisation de mon tableau. Si `$Debug` a la valeur true, ces valeurs sont placées dans `$snowSqlParam`, à l’emplacement approprié. Il en va de même pour la variable `$Path`.

## <a name="simplify-complex-operations"></a>Simplifier les opérations complexes

Vous vous retrouverez inévitablement dans une situation dans laquelle votre instruction if déborde sur le côté droit de l’écran en raison d’un trop grand nombre de comparaisons à vérifier.

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

Ces comparaisons peuvent être difficiles à lire et ainsi augmenter le risque d’erreur. Nous pouvons y remédier de plusieurs façons.

### <a name="line-continuation"></a>Continuation de ligne

Dans PowerShell, certains opérateurs vous permettent de prolonger la commande à la ligne suivante. Les opérateurs logiques `-and` et `-or` constituent de bons opérateurs si vous souhaitez fractionner votre expression sur plusieurs lignes.

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

Beaucoup d’éléments interviennent ici, mais placer chaque morceau sur sa propre ligne améliore grandement le processus.
Je l’utilise généralement lorsque j’obtiens plus de deux comparaisons ou quand je dois faire défiler l’écran vers la droite pour lire une logique.

### <a name="pre-calculating-results"></a>Précalcul des résultats

Nous pouvons extraire cette instruction de l’instruction if et vérifier uniquement le résultat.

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

Cette méthode se révèle plus efficace que celle utilisée dans l’exemple précédent. Vous avez également la possibilité d’utiliser un nom de variable qui explique ce que vous êtes en train de vérifier. Il s’agit également d’un exemple de code autodocumenté qui consigne les commentaires inutiles.

### <a name="multiple-if-statements"></a>Instructions if multiples

Nous pouvons la décomposer en plusieurs instructions et les vérifier une par une. Dans ce cas, nous utilisons un indicateur ou une variable de suivi pour combiner les résultats.

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

Je n’ai pas eu à inverser la logique pour que la logique de l’indicateur fonctionne correctement. Chaque évaluation représente une instruction `if` individuelle. L’avantage de cette approche est que lorsque vous effectuez un débogage, vous pouvez déterminer exactement ce que fait la logique. Parallèlement, j’ai pu ajouter des commentaires bien plus pertinents.

L’inconvénient, c’est qu’il faut évidemment écrire bien plus de code. Le code est plus complexe à examiner lorsqu’il prend une seule ligne de logique et l’éclate en 25 lignes ou plus.

### <a name="using-functions"></a>Utilisation des fonctions

Nous pouvons également déplacer toute cette logique de validation dans une fonction. Remarquez à quel point cette logique est simple.

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

Vous devrez toujours créer la fonction pour effectuer la validation, mais ce code est beaucoup plus facile à utiliser. Cela facilite le test de ce code. Dans vos tests, vous pouvez simuler l’appel à `Test-ADDriveConfiguration`, et deux tests suffisent pour cette fonction : un test qui retourne `$true` et un autre qui retourne `$false`. Le test de l’autre fonction est plus simple car le code est vraiment court.

Nous pouvons toujours commencer par le corps de cette fonction, avec une seule ligne, ou opter pour la logique éclatée que nous avons utilisée dans la dernière section. Cela fonctionne bien dans les deux scénarios et vous pouvez ainsi modifier facilement cette implémentation ultérieurement.

## <a name="error-handling"></a>Gestion des erreurs

Une utilisation importante de l’instruction `if` consiste à vérifier les conditions d’erreur avant de rencontrer des erreurs. Un bon exemple consiste à vérifier si un dossier existe déjà avant d’essayer de le créer.

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

Je tiens à souligner que si vous attendez une exception, il ne s’agit pas alors vraiment d’une exception. Vérifiez vos valeurs et validez vos conditions lorsque vous le pouvez.

Si vous souhaitez approfondir un peu plus la gestion des exceptions, j’ai préparé un article intitulé [Tout ce que vous avez toujours voulu savoir sur les exceptions][].

## <a name="final-words"></a>Conclusion

L’instruction `if` est une instruction simple, mais elle constitue un élément fondamental de PowerShell. Vous vous en servirez plusieurs fois dans presque tous les scripts que vous écrirez. J’espère que vous avez désormais une meilleure compréhension de ces concepts.

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[opérateurs de bits]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[les nombreuses façons d’utiliser regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[tout ce que vous avez toujours voulu savoir sur les exceptions]: everything-about-exceptions.md
[Tout ce que vous avez toujours voulu savoir sur $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[Tout ce que vous avez toujours voulu savoir sur l’instruction switch]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
