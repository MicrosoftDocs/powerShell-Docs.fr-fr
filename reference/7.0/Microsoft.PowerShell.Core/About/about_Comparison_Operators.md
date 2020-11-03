---
description: Décrit les opérateurs qui comparent des valeurs dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: d6096de14d0bb8c7ba86c0585806b86cf3bb921a
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208557"
---
# <a name="about-comparison-operators"></a>À propos des opérateurs de comparaison

## <a name="short-description"></a>Description courte
Décrit les opérateurs qui comparent des valeurs dans PowerShell.

## <a name="long-description"></a>Description longue

Les opérateurs de comparaison vous permettent de spécifier des conditions pour comparer des valeurs et Rechercher des valeurs qui correspondent aux modèles spécifiés. Pour utiliser un opérateur de comparaison, spécifiez les valeurs que vous souhaitez comparer avec un opérateur qui sépare ces valeurs.

PowerShell comprend les opérateurs de comparaison suivants :

| Type        | Opérateurs    | Description                                 |
| ----------- | ------------ | --------------------------------------------|
| Égalité    | -eq          | est égal à                                      |
|             | -ne          | n’est pas égal à                                  |
|             | -gt          | supérieur à                                |
|             | -ge          | supérieur ou égal à                       |
|             | -lt          | inférieur à                                   |
|             | -le          | inférieur ou égal à                          |
|             |              |                                             |
| Matching    | -like        | Retourne la valeur true lorsque la chaîne correspond au caractère générique   |
|             |              | modèle                                     |
|             | -notlike     | Retourne la valeur true lorsque la chaîne ne correspond pas     |
|             |              | modèle de caractère générique                            |
|             | -match       | Retourne la valeur true lorsque la chaîne correspond à Regex      |
|             |              | répétition $matches contient des chaînes correspondantes |
|             | -notmatch    | Retourne la valeur true lorsque la chaîne ne correspond pas     |
|             |              | modèle Regex ; $matches contient une correspondance   |
|             |              | chaînes                                     |
|             |              |                                             |
| Containment | -contains    | Retourne la valeur true lorsque la valeur de référence contenue |
|             |              | dans une collection                             |
|             | -notcontains | Retourne la valeur true lorsque la valeur de référence n’est pas       |
|             |              | contenu dans une collection                   |
|             | -in          | Retourne la valeur true lorsque la valeur de test contenue dans un |
|             |              | collection                                  |
|             | -NOTIN       | Retourne la valeur true lorsque la valeur de test n’est pas contenue  |
|             |              | dans une collection                             |
|             |              |                                             |
| Remplacement | -remplacer     | Remplace un modèle de chaîne                   |
|             |              |                                             |
| Type        | -est          | Retourne la valeur true si les deux objets sont identiques    |
|             |              | type                                        |
|             | -IsNot       | Retourne la valeur true si les objets ne sont pas identiques|
|             |              | type                                        |

Par défaut, tous les opérateurs de comparaison ne respectent pas la casse. Pour faire en sorte qu’un opérateur de comparaison respecte la casse, faites précéder le nom de l’opérateur d’un `c` . Par exemple, la version qui respecte la casse `-eq` est `-ceq` . Pour rendre le non-respect de la casse explicite, faites précéder l’opérateur d’un `i` . Par exemple, la version explicite de la casse de `-eq` est `-ieq` .

Lorsque l’entrée d’un opérateur est une valeur scalaire, les opérateurs de comparaison retournent une valeur booléenne. Lorsque l’entrée est une collection de valeurs, les opérateurs de comparaison retournent toutes les valeurs correspondantes. S’il n’existe aucune correspondance dans une collection, les opérateurs de comparaison retournent un tableau vide.

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

Les exceptions sont les opérateurs de relation contenant-contenu, les opérateurs in et les opérateurs de type, qui retournent toujours une valeur **booléenne** .

> [!NOTE]
> Si vous devez comparer une valeur à `$null` , vous devez `$null` la placer sur le côté gauche de la comparaison. Lorsque vous comparez `$null` à un **objet []** , le résultat est **false** , car l’objet de comparaison est un tableau. Lorsque vous comparez un tableau à `$null` , la comparaison filtre toutes les `$null` valeurs stockées dans le tableau. Par exemple :
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

### <a name="equality-operators"></a>Opérateurs d'égalité

Les opérateurs d’égalité ( `-eq` , `-ne` ) retournent une valeur true ou les correspondances lorsqu’une ou plusieurs des valeurs d’entrée sont identiques au modèle spécifié. La totalité du modèle doit correspondre à une valeur entière.

Exemple :

#### <a name="-eq"></a>-eq

Description : égal à. Contient une valeur identique.

Exemple :

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

#### <a name="-ne"></a>-ne

Description : différent de. Contient une valeur différente.

Exemple :

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

#### <a name="-gt"></a>-gt

Description : supérieur à.

Exemple :

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> Cela ne doit pas être confondu avec `>` , l’opérateur « supérieur à » dans de nombreux autres langages de programmation. Dans PowerShell, `>` est utilisé pour la redirection. Pour plus d’informations, consultez [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).

#### <a name="-ge"></a>-ge

Description : supérieur ou égal à.

Exemple :

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

#### <a name="-lt"></a>-lt

Description : inférieur à.

Exemple :

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

#### <a name="-le"></a>-le

Description : inférieur ou égal à.

Exemple :

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

### <a name="matching-operators"></a>Opérateurs correspondants

Les opérateurs like ( `-like` et `-notlike` ) recherchent les éléments qui correspondent ou ne correspondent pas à un modèle spécifié à l’aide d’expressions génériques.

La syntaxe est :

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

Les opérateurs de correspondance ( `-match` et `-notmatch` ) recherchent les éléments qui correspondent ou ne correspondent pas à un modèle spécifié à l’aide d’expressions régulières.

Les opérateurs de correspondance remplissent la `$Matches` variable automatique lorsque l’entrée (l’argument côté gauche) de l’opérateur est un objet scalaire unique. Quand l’entrée est scalaire, les `-match` `-notmatch` opérateurs et retournent une valeur booléenne et définissent la valeur de la `$Matches` variable automatique sur les composants correspondants de l’argument.

La syntaxe est :

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

#### <a name="-like"></a>-like

Description : correspondance à l’aide du caractère générique ( \* ).

Exemple :

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

#### <a name="-notlike"></a>-notlike

Description : ne correspond pas à l’aide du caractère générique ( \* ).

Exemple :

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a>-match

Description : correspond à une chaîne à l’aide d’expressions régulières. Quand l’entrée est scalaire, elle remplit la `$Matches` variable automatique.

Si l’entrée est une collection, les `-match` `-notmatch` opérateurs et retournent les membres correspondants de cette collection, mais l’opérateur ne remplit pas la `$Matches` variable.

Par exemple, la commande suivante envoie une collection de chaînes à l' `-match` opérateur. L' `-match` opérateur retourne les éléments de la collection qui correspondent à. Elle ne remplit pas la `$Matches` variable automatique.

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

En revanche, la commande suivante envoie une chaîne unique à l' `-match` opérateur. L' `-match` opérateur retourne une valeur booléenne et remplit la `$Matches` variable automatique. La `$Matches` variable automatique est une **Hashtable** . Si aucun regroupement ou capture n’est utilisé, une seule clé est remplie.
La `0` clé représente tout le texte qui a été mis en correspondance. Pour plus d’informations sur le regroupement et la capture à l’aide d’expressions régulières, consultez [about_regular_expressions](about_Regular_Expressions.md).

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

Il est important de noter que la `$Matches` Hashtable ne contiendra que la première occurrence d’un modèle correspondant.

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> La `0` clé est un **entier** . Vous pouvez utiliser n’importe quelle méthode **Hashtable** pour accéder à la valeur stockée.
>
> ```powershell
> PS> "Good Dog" -match "Dog"
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

L' `-notmatch` opérateur remplit la `$Matches` variable automatique lorsque l’entrée est scalaire et que le résultat est false, qu’il s’agit de la détection d’une correspondance.

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

#### <a name="-notmatch"></a>-notmatch

Description : ne correspond pas à une chaîne. Utilise des expressions régulières. Quand l’entrée est scalaire, elle remplit la `$Matches` variable automatique.

Exemple :

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

### <a name="containment-operators"></a>Opérateurs de relation contenant-contenu

Les opérateurs de relation contenant-contenu ( `-contains` et `-notcontains` ) sont similaires aux opérateurs d’égalité. Toutefois, les opérateurs de relation contenant-contenu retournent toujours une valeur booléenne, même lorsque l’entrée est une collection.

En outre, contrairement aux opérateurs d’égalité, les opérateurs de relation contenant-contenu retournent une valeur dès qu’ils détectent la première correspondance. Les opérateurs d’égalité évaluent toutes les entrées, puis retournent toutes les correspondances dans la collection.

#### <a name="-contains"></a>-contains

Description : opérateur de relation contenant-contenu. Indique si une collection de valeurs de référence comprend une seule valeur de test. Retourne toujours une valeur booléenne. Retourne TRUE uniquement lorsque la valeur de test correspond exactement à au moins une des valeurs de référence.

Lorsque la valeur de test est une collection, l’opérateur Contains utilise l’égalité des références. Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.

Dans une collection de très grande taille, l' `-contains` opérateur retourne les résultats plus rapidement que l’opérateur égal à.

Syntaxe :

`<Reference-values> -contains <Test-value>`

Exemples :

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

#### <a name="-notcontains"></a>-notcontains

Description : opérateur de relation contenant-contenu. Indique si une collection de valeurs de référence comprend une seule valeur de test. Retourne toujours une valeur booléenne. Retourne la valeur TRUE lorsque la valeur de test n’est pas une correspondance exacte pour au moins une des valeurs de référence.

Lorsque la valeur de test est une collection, l’opérateur NotContains utilise l’égalité de référence.

Syntaxe :

`<Reference-values> -notcontains <Test-value>`

Exemples :

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

#### <a name="-in"></a>-in

Description : dans l’opérateur. Indique si une valeur de test apparaît dans une collection de valeurs de référence. Retourne toujours comme valeur booléenne. Retourne TRUE uniquement lorsque la valeur de test correspond exactement à au moins une des valeurs de référence.

Lorsque la valeur de test est une collection, l’opérateur in utilise l’égalité de référence.
Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.

L' `-in` opérateur a été introduit dans PowerShell 3,0.

Syntaxe :

`<Test-value> -in <Reference-values>`

Exemples :

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

#### <a name="-notin"></a>-NOTIN

Description : indique si une valeur de test apparaît dans une collection de valeurs de référence. Retourne toujours une valeur booléenne. Retourne la valeur TRUE lorsque la valeur de test n’est pas une correspondance exacte pour au moins une des valeurs de référence.

Lorsque la valeur de test est une collection, l’opérateur in utilise l’égalité de référence.
Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.

L' `-notin` opérateur a été introduit dans PowerShell 3,0.

Syntaxe :

`<Test-value> -notin <Reference-values>`

Exemples :

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

### <a name="replacement-operator"></a>Opérateur de remplacement

L' `-replace` opérateur remplace tout ou partie d’une valeur par la valeur spécifiée à l’aide d’expressions régulières. Vous pouvez utiliser l' `-replace` opérateur pour de nombreuses tâches administratives, telles que le changement de nom des fichiers. Par exemple, la commande suivante modifie les extensions de nom de fichier de tous les fichiers. txt en. log :

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

La syntaxe de l' `-replace` opérateur est la suivante, où l' `<original>` espace réservé représente les caractères à remplacer, et l' `<substitute>` espace réservé représente les caractères qui les remplacent :

`<input> <operator> <original>, <substitute>`

Par défaut, l' `-replace` opérateur ne respecte pas la casse. Pour respecter la casse, utilisez `-creplace` . Pour le rendre explicitement non sensible à la casse, utilisez `-ireplace` .

Penchez-vous sur les exemples suivants :

```powershell
PS> "book" -replace "B", "C"
```

```Output
Cook
```

```powershell
"book" -ireplace "B", "C"
```

```Output
Cook
```

```powershell
"book" -creplace "B", "C"
```

```Output
book
```

Il est également possible d’utiliser des expressions régulières pour remplacer dynamiquement du texte à l’aide de groupes de capture et de substitutions. Pour plus d’informations, consultez [about_regular_expressions](about_Regular_Expressions.md).

### <a name="scriptblock-substitutions"></a>Substitutions ScriptBlock

À compter de PowerShell 6, vous pouvez utiliser un argument **scriptblock** pour le texte de *substitution* . Le **scriptblock** s’exécute pour chaque correspondance trouvée dans la chaîne *d’entrée* .

Dans le **scriptblock** , utilisez la `$_` variable automatique pour faire référence à l’objet **System. Text. RegularExpressions. match** actuel. L’objet **match** vous donne accès au texte d’entrée actuel qui est remplacé, ainsi qu’à d’autres informations utiles.

Cet exemple remplace chaque séquence de trois décimales par l’équivalent du caractère. Le **scriptblock** est exécuté pour chaque ensemble de trois décimales qui doit être remplacé.

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

### <a name="type-comparison"></a>Comparaison de types

Les opérateurs de comparaison de type ( `-is` et `-isnot` ) sont utilisés pour déterminer si un objet est un type spécifique.

#### <a name="-is"></a>-est

Syntaxe :

`<object> -is <type reference>`

Exemple :

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

#### <a name="-isnot"></a>-IsNot

Syntaxe :

`<object> -isnot <type reference>`

Exemple :

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a>VOIR AUSSI

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)
