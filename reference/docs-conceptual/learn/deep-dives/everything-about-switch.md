---
title: Tout ce que vous avez toujours voulu savoir sur l’instruction switch
description: L’instruction switch dans PowerShell offre des fonctionnalités qui n’existent pas dans d’autres langages.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 685a5691599408a0d54ca99bf383bcd7702322a6
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469716"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a>Tout ce que vous avez toujours voulu savoir sur l’instruction switch

À l’instar de nombreux autres langages, PowerShell a des commandes pour contrôler le flux d’exécution dans vos scripts. [switch][] est une de ces instructions et, dans PowerShell, elle offre des fonctionnalités qui n’existent pas dans d’autres langages. Aujourd’hui, nous nous intéressons à l’utilisation de l’instruction `switch` de PowerShell.

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu avec nous. Consultez son blog sur [PowerShellExplained.com][].

## <a name="the-if-statement"></a>Instruction `if`

Une des premières instructions que vous apprenez est l’instruction `if`. Elle vous permet d’exécuter un bloc de script si une affirmation est `$true`.

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

Vous pouvez avoir une logique bien plus compliquée en utilisant les instructions `elseif` et `else`. Voici un exemple où j’ai une valeur numérique pour le jour de la semaine et où je veux obtenir le nom sous la forme d’une chaîne.

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

Il s’avère qu’il s’agit d’un cas de figure courant et qu’il existe de nombreuses façons de le traiter. Une de ces façons est via une instruction `switch`.

## <a name="switch-statement"></a>Instruction switch

L’instruction `switch` vous permet de fournir une variable et une liste de valeurs possibles. Si la valeur correspond à la variable, son scriptblock est exécuté.

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

Pour cet exemple, la valeur de `$day` correspond à une des valeurs numériques ; le nom correct est alors affecté à `$result`. Nous n’effectuons qu’une affectation de variable dans cet exemple, mais vous pouvez exécuter n’importe quelle instruction PowerShell dans ces blocs de script.

### <a name="assign-to-a-variable"></a>Affecter à une variable

Nous pouvons écrire ce dernier exemple d’une autre façon.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

Nous plaçons la valeur sur le pipeline PowerShell et nous l’affectons à `$result`. Vous pouvez effectuer la même chose avec les instructions `if` et `foreach`.

### <a name="default"></a>Default

Nous pouvons utiliser le mot clé `default` pour identifier ce qui doit se produire s’il n’y a pas de correspondance.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

Ici, nous retournons la valeur `Unknown` dans le cas « default ».

### <a name="strings"></a>Chaînes

Dans ces derniers exemples, j’ai mis en correspondance des nombres, mais vous pouvez également faire correspondre des chaînes.

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

J’ai décidé de ne pas placer ici de guillemets autour des correspondances de `Component`,`Role` et `Location`, pour mettre en évidence le fait qu’ils sont facultatifs. `switch` les traite comme une chaîne dans la plupart des cas.

## <a name="arrays"></a>Tableaux

Une des fonctionnalités intéressantes de l'instruction `switch` de PowerShell est la façon dont elle traite les tableaux. Si vous donnez un tableau à `switch`, elle traite chaque élément de cette collection.

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

Si vous avez des éléments qui se répètent dans votre tableau, ils sont mis en correspondance plusieurs fois par la section appropriée.

### <a name="psitem"></a>PSItem

Vous pouvez utiliser `$PSItem` ou `$_` pour référencer l’élément actif qui a été traité. Quand nous faisons une correspondance simple, `$PSItem` est la valeur que nous mettons en correspondance. Je ferai des correspondances avancées dans la section suivante où cette variable est utilisée.

## <a name="parameters"></a>Paramètres

Une fonctionnalité unique de l'instruction `switch` de PowerShell est qu’elle a plusieurs [paramètres de commutateur][] qui modifient son fonctionnement.

### <a name="-casesensitive"></a>-CaseSensitive

Par défaut, les correspondances ne sont pas sensibles à la casse. Si vous devez respecter la casse, vous pouvez utiliser `-CaseSensitive`. Ceci peut être utilisé en combinaison avec les autres paramètres de commutateur.

### <a name="-wildcard"></a>-Wildcard

Nous pouvons activer la prise en charge des caractères génériques avec le commutateur `-wildcard`. Ceci utilise la même logique de caractères génériques que l’opérateur `-like` pour établir chaque correspondance.

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

Ici, nous traitons un message, puis nous le plaçons sur des flux différents en fonction du contenu.

### <a name="-regex"></a>-Regex

L’instruction switch prend en charge les correspondances d’expressions régulières exactement comme les caractères génériques.

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

Il y a plus d’exemples d’utilisation d’expressions régulières dans un autre article que j’ai écrit : [Les nombreuses façons d’utiliser les expressions régulières][].

### <a name="-file"></a>-File

Une fonctionnalité peu connue de l’instruction switch est qu’elle peut traiter un fichier avec le paramètre `-File`. Vous utilisez `-file` avec un chemin vers un fichier au lieu de lui donner une expression de variable.

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

Elle fonctionne de la même façon qu’elle traite un tableau. Dans cet exemple, je la combine avec la correspondance de caractères génériques et j’utilise `$PSItem`. Ceci va traiter un fichier journal et le convertir en messages d’avertissement et d’erreur en fonction des correspondances des expressions régulières.

## <a name="advanced-details"></a>Détails avancés

Maintenant que vous avez pris connaissance de toutes ces fonctionnalités documentées, nous pouvons les utiliser dans le contexte d’un traitement plus avancé.

### <a name="expressions"></a>Expressions

`switch` peut porter sur une expression au lieu d’une variable.

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

Le résultat de l’évaluation de l’expression est la valeur utilisée pour la correspondance.

### <a name="multiple-matches"></a>Correspondances multiples

Vous avez peut-être déjà rencontré cela, mais `switch` peut établir une correspondance avec plusieurs conditions. C’est particulièrement vrai lors de l’utilisation de correspondances `-wildcard` ou `-regex`. Vous pouvez ajouter la même condition plusieurs fois : dans ce cas, toutes sont déclenchées.

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

Ces trois instructions sont déclenchées. Ceci montre que chaque condition est vérifiée (dans l’ordre). Ceci vaut aussi pour le traitement des tableaux où chaque élément vérifie chaque condition.

### <a name="continue"></a>Continue

Normalement, ce serait le moment d’introduire l’instruction `break`, mais il est préférable de d’abord apprendre à utiliser `continue`. À l’instar d’une boucle `foreach`, `continue` poursuit sur l’élément suivant de la collection ou quitte l’instruction `switch` s’il n’y a plus d’éléments. Nous pouvons réécrire ce dernier exemple avec des instructions continue de façon à ce qu’une seule instruction s’exécute.

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

Au lieu de mettre en correspondance les trois éléments, le premier est mis en correspondance et l’instruction switch continue à la valeur suivante. Comme il n’y a plus de valeurs à traiter, l’instruction switch se termine. L’exemple suivant montre comment un caractère générique peut correspondre à plusieurs éléments.

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

Comme une ligne du fichier d’entrée peut contenir à la fois le mot `Error` et le mot `Warning`, nous voulons seulement que le premier s’exécute, puis nous poursuivons le traitement du fichier.

### <a name="break"></a>Arrêter

Une instruction `break` quitte l’instruction switch. Il s’agit du même comportement que celui présenté par `continue` pour les valeurs uniques. La différence apparaît lors du traitement d’un tableau. `break` arrête tout traitement dans l’instruction switch et `continue` passe à l’élément suivant.

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

Dans le cas présent, si nous atteignons des lignes commençant par `Error`, nous obtenons une erreur et l’instruction switch s’arrête.
C’est ce que l’instruction `break` fait pour nous. Si nous trouvons `Error` dans la chaîne et pas seulement au début, nous l’écrivons en tant qu’avertissement. Nous faisons la même chose pour `Warning`. Il est possible qu’une ligne ait à la fois le mot `Error` et le mot `Warning`, mais nous ne devons traiter qu’un seul de ces mots. C’est ce que fait l’instruction `continue` pour nous.

### <a name="break-labels"></a>Étiquette de break

L’instruction `switch` prend en charge les étiquettes `break/continue`, tout comme `foreach`.

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

Personnellement, je n’aime pas utiliser des étiquettes de break, mais je voulais en parler car elles induisent de la confusion si vous ne les avez jamais vues auparavant. Quand vous avez plusieurs instructions `switch` ou `foreach` imbriquées, vous pouvez souhaiter quitter plus que l’élément le plus intérieur. Vous pouvez placer une étiquette sur une instruction `switch` qui peut être la cible de votre `break`.

### <a name="enum"></a>Enum

PowerShell 5.0 nous a apporté les énumérations et nous pouvons les utiliser dans une instruction switch.

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

Si vous voulez conserver tout sous forme d’énumérations fortement typées, vous pouvez les placer entre parenthèses.

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

Les parenthèses sont nécessaires ici afin que l’instruction switch ne traite pas la valeur `[Context]::Location` comme chaîne littérale.

### <a name="scriptblock"></a>ScriptBlock

Nous pouvons utiliser un scriptblock pour effectuer si nécessaire l’évaluation d’une correspondance.

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

Ceci ajoute de la complexité et peut rendre votre instruction `switch` difficile à lire. Dans la plupart des cas où vous utiliseriez quelque chose comme ceci, il serait préférable d’utiliser des instructions `if` et `elseif`. J’envisagerais de l’utiliser si j’avais déjà une grande instruction switch en place et que j’avais besoin de deux éléments pour atteindre le même bloc d’évaluation.

Une chose dont je pense qu’elle augmente la lisibilité est de placer le scriptblock entre parenthèses.

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

Il s’exécute pareillement et offre une meilleure décomposition visuelle quand vous le regardez rapidement.

### <a name="regex-matches"></a>$matches pour les expressions régulières

Nous devons revisiter regex pour expliquer quelque chose qui n’est pas immédiatement évident. L’utilisation de regex remplit la variable `$matches`. J’explique de façon plus détaillée l’utilisation de `$matches` quand je parle des [Les nombreuses façons d’utiliser les expressions régulières][]. Voici un exemple rapide qui le montre en action avec des correspondances nommées.

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a>$null

Vous pouvez mettre en correspondance une valeur de `$null` qui ne doit pas nécessairement être la valeur par défaut.

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

Il en va de même pour une chaîne vide.

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a>Expression de constante

Lee Dailey a fait remarquer que nous pouvions utiliser une expression `$true` de constante pour évaluer des éléments `[bool]`.
Imaginez si nous avons plusieurs vérifications booléennes qui doivent se produire.

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

Il s’agit d’une méthode propre pour évaluer et entreprendre des actions selon l’état de plusieurs champs booléens. L’avantage est que vous pouvez faire en sorte qu’une correspondance inverse l’état d’une valeur qui n’a pas encore été évaluée.

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

Définir `$isEnabled` sur `$true` dans cet exemple permet de garantir que `$isVisible` est également défini sur `$true`. Ensuite, quand `$isVisible` est évalué, son scriptblock est appelé. C’est un peu contre-intuitif, mais c’est une utilisation intelligente de la mécanique.

### <a name="switch-automatic-variable"></a>Variable automatique $switch

Quand l’instruction `switch` traite ses valeurs, elle crée un énumérateur et l’appelle `$switch`. Il s’agit d’une variable automatique créée par PowerShell et vous pouvez la manipuler directement.

Ceci m’a été signalé par [/u/frmadsen](https://www.reddit.com/user/frmadsen)

<div class="reddit-embed" data-embed-media="www.redditmedia.com" data-embed-parent="false" data-embed-live="false" data-embed-uuid="8f6edbf1-abc6-4513-971e-ccd1d202889d" data-embed-created="2018-12-25T22:05:33.986Z"><a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">Commentaire</a> de la discussion <a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">Que dois-je apprendre en tant qu’étudiant en informatique pour maîtriser PowerShell ?</a>.</div><script async src="https://www.redditstatic.com/comment-embed.js"></script>

Vous obtenez les résultats suivants :

```Output
2
4
```

En déplaçant l’énumérateur vers l’avant, l’élément suivant n’est pas traité par l’instruction `switch`, mais vous pouvez accéder à cette valeur directement. Je pense que ce ne serait pas raisonnable.

## <a name="other-patterns"></a>Autres modèles

### <a name="hashtables"></a>Tables de hachage

Une de mes publications les plus consultées est celle qui est consacrée aux [tables de hachage][]. Un des cas d’usage d’une `hashtable` est d’en faire une table de recherche. Il s’agit d’une approche alternative à un modèle courant où l’on utilise souvent une instruction `switch`.

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

Si je constate que j’utilise une instruction `switch` seulement comme une structure pour la recherche, j’utilise alors souvent une `hashtable` à la place.

### <a name="enum"></a>Enum

PowerShell 5.0 a introduit `Enum` et c’est également une option dans ce cas.

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

Nous aurions pu rechercher pendant toute la journée différentes façons de résoudre ce problème. Je voulais simplement être sûr que vous sachiez qu’il y avait différentes options.

## <a name="final-words"></a>Le mot de la fin

L’instruction switch est simple en apparence, mais elle offre des fonctionnalités avancées dont la plupart des gens ne savent pas qu’elles sont disponibles. Combiner ensemble ces fonctionnalités transforme le tout en une puissante fonctionnalité. J’espère que vous avez appris des choses que vous ne connaissiez pas encore.

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[Paramètres de commutateur]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[Les nombreuses façons d’utiliser les expressions régulières]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[Tables de hachage]: everything-about-hashtable.md
