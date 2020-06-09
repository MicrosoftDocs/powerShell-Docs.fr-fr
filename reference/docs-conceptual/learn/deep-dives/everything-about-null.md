---
title: Tout ce que vous avez toujours voulu savoir sur $null
description: La variable PowerShell $null semble souvent être simple, mais elle présente de nombreuses subtilités. Examinons $null pour savoir ce qui se passe quand vous rencontrez de manière inattendue une valeur Null.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149472"
---
# <a name="everything-you-wanted-to-know-about-null"></a>Tout ce que vous avez toujours voulu savoir sur $null

La variable PowerShell `$null` semble souvent être simple, mais elle présente de nombreuses subtilités. Examinons `$null` pour savoir ce qui se passe quand vous rencontrez de manière inattendue une valeur `$null`.

> [!NOTE]
> La [version d’origine][] de cet article est apparue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu avec nous. Consultez son blog à l’adresse [PowerShellExplained.com][].

## <a name="what-is-null"></a>Qu’est-ce qu’une valeur Null ?

Vous pouvez considérer Null comme une valeur inconnue ou vide. Une variable a la valeur Null tant que vous ne lui avez pas attribué une valeur ou un objet. Cela peut être important car certaines commandes exige une valeur et génèrent des erreurs si la valeur est Null.

### <a name="powershell-null"></a>Variable PowerShell $null

`$null` est une variable automatique de PowerShell utilisée pour représenter une valeur Null. Vous pouvez l’affecter à des variables, l’utiliser dans des comparaisons et l’utiliser comme espace réservé pour une valeur Null dans une collection.

PowerShell traite `$null` comme un objet avec une valeur Null. C’est différent de ce que vous pouvez attendre si vous êtes habitué à un autre langage.

## <a name="examples-of-null"></a>Exemples de variable $null

Chaque fois que vous essayez d’utiliser une variable que vous n’avez pas initialisée, la valeur est `$null`. C’est l’une des façons les plus courantes pour les valeurs `$null` d’entrer dans votre code.

```powershell
PS> $null -eq $undefinedVariable
True
```

Si vous tapez mal un nom de variable, PowerShell le voit comme une variable différente et la valeur est `$null`.

L’autre façon de trouver les valeurs `$null` est quand elles proviennent d’autres commandes qui ne vous donnent aucun résultat.

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a>Impact de $null

Les valeurs `$null` affectent votre code différemment en fonction de l’endroit où elles s’affichent.

### <a name="in-strings"></a>Dans des chaînes

Si vous utilisez `$null` dans une chaîne, il s’agit d’une valeur vide (ou d’une chaîne vide).

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

C’est l’une des raisons pour lesquelles j’aime placer les variables entre crochets quand elles sont utilisées dans des messages de journal. Il est encore plus important d’identifier les limites de vos valeurs de variables quand la valeur se trouve à la fin de la chaîne.

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

Cela permet de repérer facilement les chaînes vides et les valeurs `$null`.

### <a name="in-numeric-equation"></a>Dans une équation numérique

Quand une valeur `$null` est utilisée dans une équation numérique, vos résultats ne sont pas valides s’ils ne génèrent pas d’erreur. Parfois, `$null` prend la valeur `0`, et dans d’autres cas, elle constitue la totalité du résultat `$null`.
Voici un exemple de multiplication qui donne 0 ou `$null` en fonction de l’ordre des valeurs.

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a>À la place d’une collection

Une collection vous permet d’utiliser un index pour accéder à des valeurs. Si vous essayez de créer une indexation dans une collection qui est en fait `null`, vous obtenez l’erreur suivante : `Cannot index into a null array`.

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

Si vous disposez d’une collection, mais que vous tentez d’accéder à un élément qui ne se trouve pas dans la collection, vous obtenez le résultat `$null`.

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a>À la place d’un objet

Si vous tentez d’accéder à une propriété ou à une sous-propriété d’un objet qui n’a pas la propriété spécifiée, vous obtenez une valeur `$null` comme ce serait le cas pour une variable non définie. Dans ce cas, le fait que la variable ait la valeur `$null` ou qu’elle soit un objet réel n’a pas d’importance.

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a>Méthode sur une expression ayant une valeur Null

L’appel d’une méthode sur un objet `$null` lève un `RuntimeException`.

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

Chaque fois que je vois l’expression `You cannot call a method on a null-valued expression`, la première chose que je recherche est l’endroit où j’appelle une méthode sur une variable sans vérifier au préalable si sa valeur est `$null`.

## <a name="checking-for-null"></a>Recherche de $null

Vous avez peut-être remarqué que je place toujours le `$null` à gauche lors de la recherche de `$null` dans mes exemples. Cela est intentionnel et accepté comme bonne pratique PowerShell. Dans certains scénarios, le fait de le placer à droite ne vous donne pas le résultat attendu.

Examinez l’exemple suivant et essayez de prédire les résultats :

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

Si je ne définis pas `$value`, le premier résultat est `$true` et notre message est `The array is $null`. Le piège ici est qu’il est possible de créer un `$value` qui permet que les deux aient la valeur `$false`

```powershell
$value = @( $null )
```

Dans ce cas, `$value` est un tableau qui contient une valeur `$null`. `-eq` vérifie chaque valeur du tableau et retourne la valeur `$null` qui est mise en correspondance. Le résultat obtenu est `$false`. `-ne` retourne tout ce qui ne correspond pas à `$null` et, dans le cas présent, il n’y a aucun résultat. (Cette expression renvoie également la valeur `$false`.) Aucune ne renvoie `$true` même s’il semble que l’une d’entre elles le devrait.

Nous pouvons non seulement créer une valeur qui les fait renvoyer toutes les deux `$false`, mais il est également possible de créer une valeur où elles renvoient toutes les deux la valeur `$true`. Mathias Jessen (@IISResetMe) a un [bon billet][] qui fournit des informations détaillées sur ce scénario.

### <a name="psscriptanalyzer-and-vscode"></a>PSScriptAnalyzer et VSCode

Le module [PSScriptAnalyzer][] comprend une règle appelée `PSPossibleIncorrectComparisonWithNull` qui vérifie ce problème.

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

Étant donné que VS Code utilise également les règles PSScriptAnalyser, il met également cela en évidence ou l’identifie comme un problème dans votre script.

### <a name="simple-if-check"></a>Contrôle « if » simple

Une façon courante pour les gens de rechercher une valeur non $null consiste à utiliser une instruction `if()` simple sans la comparaison.

```powershell
if ( $value )
{
    Do-Something
}
```

Si la valeur est `$null`, le résultat est `$false`. Cela est facile à lire, mais veillez à ce qu’il recherche exactement ce que vous attendez. Je lis cette ligne de code comme suit :

> Si `$value` a une valeur.

Mais tout ne se résume pas à ça. Cette ligne indique en fait :

> Si `$value` n’a pas la valeur `$null`, `0`, `$false` ou une `empty string`

Voici un exemple plus complet de cette instruction.

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

Il est tout à fait possible d’utiliser un contrôle `if` de base à condition de se rappeler que ces autres valeurs comptent comme `$false` et pas seulement qu’une variable a une valeur.

J’ai rencontré ce problème lors de la refactorisation de code il y a quelques jours. Il avait un contrôle de propriété de base comme celle-ci.

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

Je voulais affecter une valeur à la propriété de l’objet uniquement si elle existait. Dans la plupart des cas, l’objet d’origine comportait une valeur qui renvoyait `$true` dans l’instruction `if`. Mais j’ai rencontré un problème dans lequel la valeur n’était parfois pas définie. J’ai débogué le code et trouvé que l’objet avait la propriété mais il s’agissait d’une valeur de chaîne vide. Cela a empêché sa mise à jour avec la logique précédente. J’ai donc ajouté un contrôle de `$null` approprié, après quoi tout a fonctionné.

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

Ce sont de petits bogues comme ceux-là qui sont difficiles à repérer et qui me font contrôler de manière intensive les valeurs de `$null`.

## <a name="nullcount"></a>$null.Count

Si vous essayez d’accéder à une propriété sur une valeur `$null`, cette propriété a également la valeur `$null`. La propriété `count` est l’exception à cette règle.

```powershell
PS> $value = $null
PS> $value.count
0
```

Quand vous avez une valeur `$null`, `count` a la valeur `0`. Cette propriété spéciale est ajoutée par PowerShell.

### <a name="pscustomobject-count"></a>[PSCustomObject] Count

Dans PowerShell, presque tous les objets ont cette propriété count. Une exception importante est `[PSCustomObject]` dans Windows PowerShell 5.1. (Cela est corrigé dans PowerShell 6.0.) Il n’a pas de propriété count. Vous obtenez donc une valeur `$null` si vous essayez de l’utiliser. Je le mentionne ici pour que vous ne tentiez pas d’utiliser `.Count` au lieu d’un contrôle de `$null`.

L’exécution de cet exemple sur Windows PowerShell 5.1 et sur PowerShell 6.0 donne des résultats différents.

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a>Valeur Null vide

Il existe un type spécial de `$null` qui agit différemment des autres. Je vais l’appeler la valeur `$null` vide, mais il s’agit véritablement d’une valeur [System.Management.Automation.Internal.AutomationNull][]. Cette valeur `$null` vide est celle que vous obtenez comme résultat d’une fonction ou d’un bloc de script qui ne retourne rien (résultat void).

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

Si vous la comparez à `$null`, vous obtenez une valeur `$null`. Quand elle est utilisée dans une évaluation où une valeur est nécessaire, la valeur est toujours `$null`. Mais si vous la placez dans un tableau, elle est traitée comme un tableau vide.

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

Vous pouvez avoir un tableau qui contient une valeur `$null` et sa valeur `count` est `1`. Toutefois, si vous placez un résultat vide dans un tableau, il n’est pas comptabilisé comme un élément. Le nombre est `0`.

Si vous traitez la valeur `$null` vide comme une collection, elle est vide.

### <a name="pipeline"></a>Pipeline

Le principal moment où vous voyez la différence est lors de l’utilisation du pipeline. Vous pouvez acheminer une valeur `$null` mais pas une valeur `$null` vide.

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

En fonction de votre code, vous devez tenir compte de la valeur `$null` dans votre logique.

Recherchez d’abord la valeur `$null`

- Filtrer les valeurs Null sur le pipeline (`... | Where {$null -ne $_} | ...`)
- Gérer-la dans la fonction pipeline

## <a name="foreach"></a>foreach

L’une de mes fonctionnalités préférées de `foreach` est qu’il n’effectue pas d’énumération sur une collection `$null`.

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

Cela m’évite d’avoir à contrôler les valeurs `$null` dans la collection avant de l’énumérer. Si vous disposez d’une collection de valeurs de `$null`, `$node` peut toujours avoir une valeur `$null`.

La variable foreach a commencé à fonctionner de cette manière avec PowerShell 3.0. Si vous êtes sur une version antérieure, ce n’est pas le cas. Il s’agit de l’un des principaux changements à connaître lors du rétroportage de code pour la compatibilité 2.0.

## <a name="value-types"></a>Types valeur

Techniquement, seuls les types référence peuvent avoir une valeur `$null`. Mais PowerShell est très généreux et permet que les variables soient de n’importe quel type. Si vous décidez de typer fortement un type valeur, il ne peut pas être `$null`.
PowerShell convertit `$null`en une valeur par défaut pour de nombreux types.

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

Certains types n’ont pas de conversion valide à partir de `$null`. Ces types génèrent une erreur `Cannot convert null to type`.

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a>Paramètres de fonction

Il est très courant d’utiliser une valeur fortement typée dans des paramètres de fonction. Nous apprenons généralement à définir les types de nos paramètres, même si nous avons tendance à ne pas définir les types d’autres variables dans nos scripts. Vous avez peut-être déjà des variables fortement typées dans vos fonctions et vous ne vous en rendez même pas compte.

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

Dès que vous définissez le type du paramètre en tant que `string`, la valeur ne peut jamais être `$null`. Il est courant de vérifier si une valeur est `$null` pour voir si l’utilisateur a, ou non, fourni une valeur.

```powershell
if ( $null -ne $Value ){...}
```

`$Value` est une chaîne vide `''` quand aucune valeur n’est fournie. Utilisez la variable automatique `$PSBoundParameters.Value` à la place.

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

`$PSBoundParameters` contient uniquement les paramètres qui ont été spécifiés lors de l’appel de la fonction.
Vous pouvez également utiliser la méthode `ContainsKey` pour rechercher la propriété.

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a>IsNotNullOrEmpty

Si la valeur est une chaîne, vous pouvez utiliser une fonction de chaîne statique pour vérifier si la valeur est `$null` ou une chaîne vide en même temps.

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

Il m’arrive souvent de l’utiliser quand je sais que le type valeur doit être une chaîne.

## <a name="when-i-null-check"></a>Quand je contrôle les valeurs $null

Je suis un générateur de script prudent. Chaque fois que j’appelle une fonction et que je l’affecte à une variable, je vérifie si elle comprend une valeur `$null`.

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

Je préfère de beaucoup utiliser `if` ou `foreach` plutôt que `try/catch`. Ne vous méprenez pas : j’utilise encore beaucoup `try/catch`. Toutefois, si je peux tester une condition d’erreur ou un jeu de résultats vide, je peux autoriser que la gestion de mes exceptions concerne les véritables exceptions.

J’ai également tendance à rechercher les valeurs `$null` avant de créer une indexation dans une valeur ou d’appeler des méthodes sur un objet. Comme ces deux actions échouent pour un objet `$null`, je trouve qu’il est important de d’abord les valider. J’ai déjà abordé ces scénarios précédemment dans cette publication.

### <a name="no-results-scenario"></a>Scénario sans résultat

Il est important de savoir que différentes fonctions et commandes gèrent le scénario sans résultat différemment. De nombreuses commandes PowerShell retournent la valeur `$null` vide et une erreur dans le flux d’erreurs. Mais d’autres lèvent des exceptions ou vous donnent un objet d’état. Il vous appartient quand même de découvrir comment les commandes que vous utilisez traitent les scénarios sans résultat et les scénarios d’erreur.

## <a name="initializing-to-null"></a>Initialisation sur $null

J’ai pris, entre autres, l’habitude d’initialiser toutes mes variables avant de les utiliser. Vous devez effectuer cette opération dans d’autres langages. En haut de ma fonction ou quand j’entre une boucle foreach, je définis toutes les valeurs que j’utilise.

Voici un scénario que je veux que vous examiniez en détail. Il s’agit d’un exemple de bogue que j’ai déjà recherché.

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

On s’attend à ce que `Get-Something` retourne soit un résultat, soit une valeur `$null` vide. Si une erreur se produit, nous la consignons. Nous vérifions ensuite que nous avons obtenu un résultat valide avant de le traiter.

Le masquage du bogue se produit dans ce code quand `Get-Something` lève une exception et n’affecte pas de valeur à `$result`. Comme il échoue avant l’affectation, nous n’affectons même pas `$null` à la variable `$result`. `$result` contient encore le `$result` valide précédent provenant d’autres itérations.
Définissez la commande `Update-Something` pour qu’elle s’exécute plusieurs fois sur le même objet dans cet exemple.

Je définis `$result` sur `$null` directement dans la boucle foreach avant de l’utiliser pour atténuer ce problème.

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a>Problèmes d’étendue

Cela permet également d’atténuer les problèmes de portée. Dans cet exemple, nous affectons plusieurs fois des valeurs à `$result` dans une boucle. Toutefois, étant donné que PowerShell permet que des valeurs de variables extérieures à la fonction débordent dans l’étendue de la fonction active, leur initialisation à l’intérieur de votre fonction atténue les bogues qui peuvent être introduits de cette façon.

Une variable non initialisée dans votre fonction n’a pas une valeur `$null` si elle est définie sur une valeur d’une étendue parente.
L’étendue parente peut être une autre fonction qui appelle votre fonction et utilise les mêmes noms de variables.

Si je prends ce même exemple `Do-something` et que je supprime la boucle, j’obtiens quelque chose ressemblant à l’exemple suivant :

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

Si l’appel à `Get-Something` lève une exception, mon contrôle des valeurs `$null` trouve `$result` dans `Invoke-Something`. L’initialisation de la valeur dans votre fonction atténue ce problème.

Le nommage de variables est difficile et il est courant qu’un auteur utilise les mêmes noms de variables dans plusieurs fonctions. Je sais que j’utilise tout le temps `$node`,`$result` et `$data`. C’est pourquoi il est très facile pour des valeurs de différentes étendues de s’afficher dans des emplacements où elles ne devraient pas être.

## <a name="redirect-output-to-null"></a>Rediriger la sortie vers $null

Je parle des valeurs `$null` dans l’ensemble de cet article, mais le sujet n’est pas complet si je ne mentionne pas la redirection de la sortie vers `$null`. Vous avez parfois des commandes qui génèrent des informations ou des objets que vous voulez supprimer. C’est le cas de la redirection de la sortie vers `$null`.

### <a name="out-null"></a>Out-Null

La commande Out-Null est le moyen intégré de rediriger des données de pipeline vers `$null`.

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a>Attribuer à $null

Vous pouvez attribuer les résultats d’une commande à `$null` pour obtenir le même effet qu’en utilisant `Out-Null`.

```powershell
$null = New-Item -Type Directory -Path $path
```

Étant donné que `$null` est une valeur constante, vous ne pouvez jamais la remplacer. Je n’aime pas la façon dont cela se présente dans mon code, mais l’exécution est souvent plus rapide qu’avec `Out-Null`.

### <a name="redirect-to-null"></a>Rediriger vers $null

Vous pouvez également utiliser l’opérateur de redirection pour envoyer la sortie vers `$null`.

```powershell
New-Item -Type Directory -Path $path > $null
```

Si vous utilisez des exécutables de ligne de commande qui génèrent les sorties sur les différents flux. Vous pouvez rediriger tous les flux de sortie vers `$null` comme suit :

```powershell
git status *> $null
```

## <a name="summary"></a>Résumé

J’ai abordé beaucoup de sujets dans ce billet et je sais que cet article est plus morcelé que la plupart de mes analyses approfondies. Cela est dû au fait que les valeurs `$null` peuvent apparaître à de nombreux endroits différents dans PowerShell et que toutes les formes sont spécifiques à l’emplacement où vous les trouvez. J’espère que vous avez désormais une meilleure compréhension des valeurs `$null` et une connaissance des scénarios les plus nébuleux que vous pouvez rencontrer.

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[bon billet]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
