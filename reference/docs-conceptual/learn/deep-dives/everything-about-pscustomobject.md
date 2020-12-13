---
title: Tout ce que vous avez toujours voulu savoir sur PSCustomObject
description: PSCustomObject est un moyen simple de créer des données structurées.
ms.date: 10/05/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ccbdcdae5ad38f555233dffbed7e8a6ec2b0726b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "91772318"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a>Tout ce que vous avez toujours voulu savoir sur PSCustomObject

`PSCustomObject` est un très bon outil à ajouter à votre gamme d’outils PowerShell. Commençons par les concepts de base, puis nous passerons aux fonctionnalités plus avancées. L’idée sous-jacente de l’utilisation d’un `PSCustomObject` est d’avoir un moyen simple pour créer des données structurées. Jetez un coup d’œil au premier exemple et vous aurez une meilleure idée de ce que cela signifie.

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][]. L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu. Consultez son blog sur [PowerShellExplained.com][].

## <a name="creating-a-pscustomobject"></a>Création d’un PSCustomObject

J’aime bien utiliser `[PSCustomObject]` dans PowerShell. La création d’un objet utilisable n’a jamais été aussi facile.
Pour cette raison, je vais passer sous silence toutes les autres façons de créer un objet, mais je dois mentionner que la plupart de ces exemples sont en PowerShell 3.0 et ultérieur.

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

Cette méthode fonctionne bien pour moi, car j’utilise des tables de hachage pour à peu près tout. Mais il y a des fois où je voudrais que PowerShell traite les tables de hachage comme un objet. Là où vous remarquez d’abord la différence est quand vous voulez utiliser `Format-Table` ou `Export-CSV`, et que vous réalisez qu’une table de hachage est simplement une collection de paires clé/valeur.

Vous pouvez ensuite accéder aux valeurs et les utiliser comme vous le feriez avec un objet normal.

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a>Conversion d’une table de hachage

Tant que nous traitons de ce sujet : savez-vous que vous pouvez faire ceci :

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

Je préfère créer l’objet entièrement, mais vous devez parfois utiliser d’abord une table de hachage. Cet exemple fonctionne, car le constructeur prend une table de hachage pour les propriétés de l’objet. Il est important de remarquer que si cette méthode fonctionne, elle n’est pas exactement équivalente. La plus grande différence est que l’ordre des propriétés n’est pas conservé.

### <a name="legacy-approach"></a>Approche héritée

Vous avez peut-être vu des personnes utiliser `New-Object` pour créer des objets personnalisés.

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

Cette façon de faire est un peu lente, mais elle peut être votre meilleure option sur les premières versions de PowerShell.

### <a name="saving-to-a-file"></a>Enregistrement dans un fichier

Je trouve que la meilleure façon d’enregistrer une table de hachage dans un fichier est de l’enregistrer au format JSON. Vous pouvez la réimporter dans un `[PSCustomObject]`

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

Je présente d’autres moyens d’enregistrer des objets dans un fichier dans mon article sur [Les nombreuses façons de lire et d’écrire des fichiers][].

## <a name="working-with-properties"></a>Utilisation de propriétés

### <a name="adding-properties"></a>Ajout de propriétés

Vous pouvez toujours ajouter de nouvelles propriétés à votre `PSCustomObject` avec `Add-Member`.

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a>Supprimer des propriétés

Vous pouvez aussi supprimer des propriétés dans un objet.

```powershell
$myObject.psobject.properties.remove('ID')
```

`psobject` est une propriété masquée qui vous permet d’accéder aux métadonnées de l’objet de base.

### <a name="enumerating-property-names"></a>Énumération des noms des propriétés

Vous avez parfois besoin d’une liste de tous les noms des propriétés sur un objet.

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

Nous pouvons également obtenir cette même liste à partir de la propriété `psobject`.

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a>Accès dynamique aux propriétés

J’ai déjà mentionné que vous pouvez accéder directement aux valeurs des propriétés.

```powershell
$myObject.Name
```

Vous pouvez aussi utiliser une chaîne pour le nom de la propriété.

```powershell
$myObject.'Name'
```

Nous pouvons aller plus loin et utiliser une variable pour le nom de la propriété.

```powershell
$property = 'Name'
$myObject.$property
```

Je sais que ça paraît étrange, mais cela fonctionne.

### <a name="convert-pscustomobject-into-a-hashtable"></a>Convertir PSCustomObject en table de hachage

Pour continuer à partir de la dernière section, vous pouvez parcourir dynamiquement les propriétés et créer une table de hachage à partir de celles-ci.

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a>Test des propriétés

Si vous avez besoin de savoir si une propriété existe, vous pouvez simplement vérifier que cette propriété a une valeur.

```powershell
if( $null -ne $myObject.ID )
```

Toutefois, comme la valeur peut être `$null`, vous pouvez vérifier si elle existe en la recherchant dans `psobject.properties`.

```powershell
if( $myobject.psobject.properties.match('ID').Count )
```

## <a name="adding-object-methods"></a>Ajout de méthodes d’objet

Si vous devez ajouter une méthode de script à un objet, vous pouvez le faire avec `Add-Member` et un `ScriptBlock`. Vous devez utiliser la variable automatique `this` pour référencer l’objet actif. Voici un `scriptblock` pour transformer un objet en table de hachage. (même code que dans le dernier exemple)

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

Ensuite, nous l’ajoutons à notre objet en tant que propriété de script.

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

Nous pouvons ensuite appeler notre fonction comme suit :

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a>Objets et types valeur

Les objets et les types valeur ne gèrent pas les affectations de variables de la même façon. Si vous affectez des types valeur entre eux, seule la valeur est copiée dans la nouvelle variable.

```powershell
$first = 1
$second = $first
$second = 2
```

Dans ce cas, `$first` vaut 1 et `$second` vaut 2.

Les variables d’objet contiennent une référence à l’objet réel. Quand vous affectez un objet à une nouvelle variable, elle fait toujours référence au même objet.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

Comme `$third` et `$fourth` référencent la même instance d’un objet, `$third.key` et `$fourth.Key` valent tous deux 4.

### <a name="psobjectcopy"></a>psobject.copy()

Si vous avez besoin d’une copie réelle d’un objet, vous pouvez le cloner.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

Le clonage crée une copie superficielle de l’objet. Ils ont maintenant des instances différentes et dans cet exemple, `$third.key` vaut 3 et `$fourth.Key` vaut 4.

J’appelle ceci une copie superficielle, car si vous avez des objets imbriqués (où les propriétés contiennent d’autres objets), seules les valeurs du plus haut niveau sont copiées. Les objets enfants se référencent mutuellement.

### <a name="pstypename-for-custom-object-types"></a>PSTypeName pour les types d’objets personnalisés

Maintenant que nous disposons d’un objet, nous pouvons effectuer quelques autres opérations qui ne sont peut-être pas si évidentes. La première chose à faire est de lui donner un `PSTypeName`. Voici comment je vois procéder la plupart des gens :

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

J’ai récemment découvert une autre façon de le faire à partir de ce [Posté par /u/markekraus][]. J’ai un peu investigué et j’ai trouvé d’autres billets sur l’idée de [Adam Bertram][] et [Mike Shepard][], où ils parlent de cette approche qui vous permet de le définir inline.

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

J’aime bien la façon dont cela s’intègre parfaitement dans le langage. Maintenant que nous disposons d’un objet avec un nom de type correct, nous pouvons effectuer d’autres opérations.

> [!NOTE]
> Vous pouvez également créer des types PowerShell personnalisés à l’aide de classes PowerShell. Pour plus d’informations, consultez [Présentation des classes PowerShell](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes).

## <a name="using-defaultpropertyset-the-long-way"></a>Utilisation de DefaultPropertySet (la méthode longue)

PowerShell décide pour nous des propriétés à afficher par défaut. Un grand nombre de commandes natives ont un [fichier de mise en forme][] `.ps1xml` qui effectue tout ce gros travail de mise en forme. Selon ce [Posté par Boe Prox][], il existe un autre moyen d’effectuer cette opération sur notre objet personnalisé en utilisant simplement PowerShell. Nous pouvons lui fournir un `MemberSet` qu’il va utiliser.

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet('DefaultDisplayPropertySet',[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

Maintenant, quand mon objet apparaît dans le shell de commandes, il ne montre par défaut que ces seules propriétés.

### <a name="update-typedata-with-defaultpropertyset"></a>Update-TypeData avec DefaultPropertySet

C’est bien, mais j’ai récemment vu un meilleur moyen en regardant [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged]. Jeffrey utilisait [Update-TypeData][] pour spécifier les propriétés par défaut.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

C’est tellement simple que je pourrais pratiquement m’en rappeler si je n’avais pas ce billet comme référence rapide. Je peux maintenant créer facilement des objets avec un grand nombre de propriétés et en avoir néanmoins une vue bien propre quand je les regarde dans le shell. Si j’ai besoin d’accéder à ces autres propriétés ou de les voir, elles sont cependant toujours là.

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a>Update-TypeData avec ScriptProperty

Une autre chose que j’ai tirée de cette vidéo était la création de propriétés de script pour vos objets. C’est le bon moment pour souligner que cela fonctionne également pour les objets existants.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

Vous pouvez faire cela avant que votre objet soit créé ou bien après : cela fonctionne dans les deux cas. Voici ce qui diffère de l’utilisation de `Add-Member` avec une propriété de script. Quand vous utilisez `Add-Member` de la façon dont j’ai parlé plus haut, il existe seulement sur cette instance spécifique de l’objet. Celui-ci s’applique à tous les objets avec ce `TypeName`.

## <a name="function-parameters"></a>Paramètres de fonction

Vous pouvez maintenant utiliser ces types personnalisés pour les paramètres dans vos fonctions et vos scripts. Vous pouvez avoir une fonction qui crée ces objets personnalisés, puis les passer à d’autres fonctions.

```powershell
param( [PSTypeName('My.Object')]$Data )
```

PowerShell exige que l’objet soit du type que vous avez spécifié. Il génère une erreur de validation si le type ne correspond pas automatiquement, pour vous éviter de le tester dans votre code. Un bon exemple où on laisse PowerShell faire ce qu’il fait le mieux.

### <a name="function-outputtype"></a>OutputType pour les fonctions

Vous pouvez également définir un `OutputType` pour vos fonctions avancées.

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

La valeur de l’attribut **OutputType** n’est qu’une note de documentation. Elle n’est pas dérivée du code de la fonction et n’est pas comparée à la sortie réelle de la fonction.

La raison principale pour laquelle vous utilisez un type de sortie est de faire en sorte que les méta-informations sur votre fonction reflètent vos intentions. Par exemple, `Get-Command` et `Get-Help` peuvent en tirer parti dans votre environnement de développement. Si vous voulez plus d’informations, consultez l’aide pour celui-ci : [about_Functions_OutputTypeAttribute][].

Cela dit, si vous utilisez Pester pour effectuer les tests unitaires de vos fonctions, il serait judicieux de vérifier que les objets en sortie correspondent à votre **OutputType**. Cela pourrait intercepter les variables qui arrivent dans le pipe alors qu’elles ne le devraient pas.

## <a name="closing-thoughts"></a>Réflexions finales

Le contexte de tout ceci concernait `[PSCustomObject]`, mais beaucoup de ces informations s’appliquent aux objets en général.

J’ai vu la plupart de ces fonctionnalités en passant, mais je ne les avait jamais vues présentées sous la forme d’une collection d’informations sur `PSCustomObject`. Pas plus tard que la semaine dernière, je suis tombé sur une autre fonctionnalité et j’ai été étonné de ne pas l’avoir déjà vue. Je voulais rassembler toutes ces idées pour vous en donner la vision la plus large possible et pour vous les faire découvrir si jamais vous avez l’occasion de les utiliser. J’espère que vous avez appris quelque chose et que vous pourrez vous en servir dans vos scripts.

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Posté par Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[Fichier de mise en forme]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[Les nombreuses façons de lire et d’écrire des fichiers]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[Posté par /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
