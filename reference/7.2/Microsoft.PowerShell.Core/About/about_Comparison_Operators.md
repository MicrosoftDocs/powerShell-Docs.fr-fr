---
description: Décrit les opérateurs qui comparent des valeurs dans PowerShell.
Locale: en-US
ms.date: 02/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: 73a83e1cd93c3467857d5eded8ad6c384e548937
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685305"
---
# <a name="about-comparison-operators"></a>À propos des opérateurs de comparaison

## <a name="short-description"></a>Description courte

Les opérateurs de comparaison dans PowerShell peuvent comparer deux valeurs ou filtrer les éléments d’une collection par rapport à une valeur d’entrée.

## <a name="long-description"></a>Description longue

Les opérateurs de comparaison vous permettent de comparer des valeurs ou de rechercher des valeurs qui correspondent aux modèles spécifiés. PowerShell comprend les opérateurs de comparaison suivants :

|    Type     |   Opérateur   |              Test de comparaison              |
| ----------- | ------------ | ----------------------------------------- |
| Égalité    | -eq          | equals                                    |
|             | -ne          | n’est pas égal à                                |
|             | -gt          | supérieur à                              |
|             | -ge          | supérieur ou égal à                     |
|             | -lt          | inférieur à                                 |
|             | -le          | inférieur ou égal à                        |
| Matching    | -like        | la chaîne correspond au modèle de caractère générique           |
|             | -notlike     | la chaîne ne correspond pas au modèle de caractère générique    |
|             | -match       | la chaîne correspond au modèle Regex              |
|             | -notmatch    | la chaîne ne correspond pas au modèle Regex       |
| Remplacement | -remplacer     | remplace les chaînes correspondant à un modèle Regex |
| Containment | -contains    | la collection contient une valeur               |
|             | -notcontains | la collection ne contient pas de valeur       |
|             | -in          | la valeur se trouve dans une collection                  |
|             | -NOTIN       | la valeur ne se trouve pas dans une collection              |
| Type        | -est          | les deux objets sont du même type            |
|             | -IsNot       | les objets ne sont pas du même type         |

## <a name="common-features"></a>Fonctionnalités communes

Par défaut, tous les opérateurs de comparaison ne respectent pas la casse. Pour rendre un opérateur de comparaison sensible à la casse, ajoutez un `c` après `-` . Par exemple, `-ceq` est la version qui respecte la casse de `-eq` . Pour rendre le non-respect de la casse explicite, ajoutez un `i` avant `-` . Par exemple, `-ieq` est la version de non-respect de la casse explicite de `-eq` .

Lorsque l’entrée d’un opérateur est une valeur scalaire, l’opérateur retourne une valeur **booléenne** . Lorsque l’entrée est une collection, l’opérateur retourne les éléments de la collection qui correspondent à la valeur de droite de l’expression.
S’il n’y a aucune correspondance dans la collection, les opérateurs de comparaison retournent un tableau vide. Par exemple :

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

Il existe quelques exceptions :

- Les opérateurs de relation contenant-contenu et type retournent toujours une valeur **booléenne**
- L' `-replace` opérateur retourne le résultat de remplacement
- Les `-match` `-notmatch` opérateurs et remplissent également la `$Matches` variable automatique.

## <a name="equality-operators"></a>Opérateurs d’égalité

### <a name="-eq-and--ne"></a>-eq et -ne

Lorsque la partie gauche est scalaire, `-eq` retourne **true** si le côté droit est une correspondance exacte ; sinon, `-eq` retourne **false**. `-ne` fait l’inverse ; elle retourne **false** lorsque les deux côtés correspondent ; Sinon, `-ne` retourne la valeur true.

Exemple :

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

Lorsque la partie gauche est une collection, `-eq` retourne les membres qui correspondent à la partie droite, tout en `-ne` les filtrant.

Exemple :

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

Ces opérateurs traitent tous les éléments de la collection. Exemple :

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

Les opérateurs d’égalité acceptent deux objets, et pas seulement une collection scalaire ou.
Mais il n’est pas garanti que le résultat de la comparaison soit significatif pour l’utilisateur final.
L’exemple suivant illustre le problème.

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

Dans cet exemple, nous avons créé deux objets avec des propriétés identiques. Pourtant, le résultat du test d’égalité est **false** , car il s’agit d’objets différents. Pour créer des classes comparables, vous devez implémenter [System \<T> . IEquatable][2] dans votre classe. L’exemple suivant illustre l’implémentation partielle d’une classe **MyFileInfoSet** qui implémente [System. IEquatable \<T>][2] et a deux propriétés, **file** et **Size**. La `Equals()` méthode retourne la valeur true si les propriétés de fichier et de taille de deux objets **MyFileInfoSet** sont identiques.

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

Un exemple évident de comparaison d’objets arbitraires consiste à déterminer s’ils ont la valeur null. Toutefois, si vous devez déterminer si une variable est `$null` , vous devez placer le `$null` côté gauche de l’opérateur d’égalité. Le fait de le placer sur le côté droit ne fait pas ce que vous attendez.

Prenons l’exemple d' `$a` un tableau contenant des éléments null :

```powershell
$a = 1, 2, $null, 4, $null, 6
```

Les tests suivants n' `$a` ont pas la valeur null.

```powershell
$null -ne $a
```

```output
True
```

Les éléments suivants, cependant, décodent tous les éléments null de `$a` :

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a>-gt,-GE,-LT et-le

`-gt`, `-ge` , `-lt` et `-le` se comportent de façon très similaire. Lorsque les deux côtés sont scalaires, ils retournent la **valeur true** ou **false** en fonction de la comparaison des deux côtés :

| Opérateur | Retourne la valeur true lorsque...                   |
| -------- | -------------------------------------- |
| -gt      | La partie gauche est supérieure          |
| -ge      | Le côté gauche est supérieur ou égal à |
| -lt      | La partie gauche est plus petite          |
| -le      | La partie gauche est plus petite ou égale |

Dans les exemples suivants, toutes les instructions retournent la valeur true.

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> Dans la plupart des langages de programmation, l’opérateur « supérieur à » est `>` . Dans PowerShell, ce caractère est utilisé pour la redirection. Pour plus d’informations, consultez [about_Redirection][3].

Lorsque la partie gauche est une collection, ces opérateurs comparent chaque membre de la collection avec le côté droit. En fonction de leur logique, ils conservent ou ignorent le membre.

Exemple :

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

Ces opérateurs fonctionnent avec toute classe qui implémente [System. IComparable][1].

Exemples :

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

L’exemple suivant montre qu’il n’y a aucun symbole sur un clavier américain QWERTY trié après « a ». Il alimente un jeu contenant tous les symboles de ce type à l' `-gt` opérateur pour les comparer à « a ». La sortie est un tableau vide.

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

Si les deux côtés des opérateurs ne sont pas raisonnablement comparables, ces opérateurs déclenchent une erreur sans fin d’achèvement.

## <a name="matching-operators"></a>Opérateurs correspondants

Les opérateurs correspondants ( `-like` , `-notlike` , `-match` et `-notmatch` ) recherchent les éléments qui correspondent ou ne correspondent pas à un modèle spécifié. Le modèle pour `-like` et `-notlike` est une expression générique (contenant `*` , `?` et `[ ]` ), tandis que `-match` et `-notmatch` acceptent une expression régulière (Regex).

La syntaxe est :

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

Lorsque l’entrée de ces opérateurs est une valeur scalaire, ils retournent une valeur **booléenne** . Lorsque l’entrée est une collection de valeurs, les opérateurs retournent tous les membres correspondants. S’il n’existe aucune correspondance dans une collection, les opérateurs retournent un tableau vide.

### <a name="-like-and--notlike"></a>-like et-NOTLIKE

`-like` et `-notlike` se comportent de la même façon `-eq` que et `-ne` , mais le côté droit peut être une chaîne contenant des [caractères génériques](about_Wildcards.md).

Exemple :

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a>-match et-notmatch

`-match` et `-notmatch` utilisent des expressions régulières pour rechercher le modèle dans les valeurs de gauche. Les expressions régulières peuvent correspondre à des modèles complexes tels que des adresses de messagerie, des chemins d’accès UNC ou des numéros de téléphone mis en forme. La chaîne de droite doit respecter les règles d' [expressions régulières](about_Regular_Expressions.md) .

Exemples scalaires :

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

Si l’entrée est une collection, les opérateurs retournent les membres correspondants de cette collection.

Exemples de collection :

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

`-match` et `-notmatch` prennent en charge les groupes de capture Regex. Chaque fois qu’ils s’exécutent, ils remplacent la `$Matches` variable automatique. Lorsque `<input>` est une collection `$Matches` , la variable est `$null` . `$Matches` est une **Hashtable** qui a toujours une clé nommée « 0 », qui stocke la correspondance entière. Si l’expression régulière contient des groupes de capture, le `$Matches` contient des clés supplémentaires pour chaque groupe.

Exemple :

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

Pour plus d’informations, consultez [about_regular_expressions](about_Regular_Expressions.md).

## <a name="replacement-operator"></a>Opérateur de remplacement

### <a name="replacement-with-regular-expressions"></a>Remplacement à l’aide d’expressions régulières

Comme `-match` , l' `-replace` opérateur utilise des expressions régulières pour rechercher le modèle spécifié. Mais contrairement à `-match` , elle remplace les correspondances par une autre valeur spécifiée.

Syntaxe :

```
<input> -replace <regular-expression>, <substitute>
```

L’opérateur remplace tout ou partie d’une valeur par la valeur spécifiée à l’aide d’expressions régulières. Vous pouvez utiliser l’opérateur pour de nombreuses tâches administratives, telles que le changement de nom des fichiers. Par exemple, la commande suivante modifie les extensions de nom de fichier de tous les `.txt` fichiers en `.log` :

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

Par défaut, l' `-replace` opérateur ne respecte pas la casse. Pour respecter la casse, utilisez `-creplace` . Pour le rendre explicitement non sensible à la casse, utilisez `-ireplace` .

Exemples :

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a>Substitutions d’expressions régulières

Il est également possible d’utiliser des expressions régulières pour remplacer dynamiquement du texte à l’aide de groupes de capture et de substitutions. Les groupes de capture peuvent être référencés dans la `<substitute>` chaîne à l’aide du caractère dollar ( `$` ) avant l’identificateur de groupe.

Dans l’exemple suivant, l' `-replace` opérateur accepte un nom d’utilisateur sous la forme `DomainName\Username` et convertit le `Username@DomainName` format :

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> Le `$` caractère a des rôles syntatic dans PowerShell et les expressions régulières :
>
> - Dans PowerShell, entre guillemets doubles, il désigne les variables et agit comme un opérateur de sous-expression.
> - Dans les chaînes de recherche Regex, elle désigne la fin de la ligne
> - Dans les chaînes de substitution Regex, il désigne les groupes capturés. Veillez à placer vos expressions régulières entre des guillemets simples ou insérer un caractère de `` ` `` soulignement () avant.

Par exemple :

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

`$$` dans Regex, il désigne un littéral `$` . This `$$` dans la chaîne de substitution pour inclure un littéral `$` dans le de remplacement résultant. Par exemple :

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

Pour plus d’informations, consultez [about_regular_expressions](about_Regular_Expressions.md) et [substitutions dans les expressions régulières][4].

### <a name="substituting-in-a-collection"></a>Substitution d’une collection

Quand le `<input>` à l' `-replace` opérateur est une collection, PowerShell applique le remplacement à chaque valeur de la collection. Par exemple :

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a>Remplacement à l’aide d’un bloc de script

Dans PowerShell 6 et versions ultérieures, l' `-replace` opérateur accepte également un bloc de script qui effectue le remplacement. Le bloc de script s’exécute une fois pour chaque correspondance.

Syntaxe :

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

Dans le bloc de script, utilisez la `$_` variable automatique pour accéder au texte d’entrée qui est remplacé et à d’autres informations utiles. Le type de classe de cette variable est [System. Text. RegularExpressions. match][2].

L’exemple suivant remplace chaque séquence de trois chiffres par les caractères équivalents. Le bloc de script s’exécute pour chaque ensemble de trois chiffres qui doit être remplacé.

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a>Opérateurs de relation contenant-contenu

Les opérateurs de relation contenant-contenu ( `-contains` , `-notcontains` , `-in` et `-notin` ) sont similaires aux opérateurs d’égalité, sauf qu’ils retournent toujours une valeur **booléenne** , même lorsque l’entrée est une collection. Ces opérateurs cessent de comparer dès qu’ils détectent la première correspondance, tandis que les opérateurs d’égalité évaluent tous les membres d’entrée. Dans une collection très volumineuse, ces opérateurs retournent plus rapidement que les opérateurs d’égalité.

Syntaxe :

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a>-contient et-notcontains

Ces opérateurs indiquent si un jeu comprend un certain élément. `-contains` retourne la valeur true lorsque le côté droit (objet de test) correspond à l’un des éléments du jeu. `-notcontains` retourne false à la place. Lorsque l’objet de test est une collection, ces opérateurs utilisent l’égalité de référence, c’est-à-dire qu’ils vérifient si l’un des éléments du jeu est la même instance de l’objet de test.

Exemples :

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

Exemples plus complexes :

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a>-in et-NOTIN

Les `-in` opérateurs et `notin` ont été introduits dans PowerShell 3 comme l’inverse syntaxique des `contains` opérateurs et `-notcontain` . `-in` retourne la **valeur true** lorsque la partie gauche `<test-object>` correspond à l’un des éléments du jeu. `-notin` retourne **false** à la place. Lorsque l’objet de test est un ensemble, ces opérateurs utilisent l’égalité de référence pour vérifier si l’un des éléments du jeu est la même instance de l’objet de test.

Les exemples suivants font la même chose que les exemples pour `-contain` et `-notcontain` , mais ils sont écrits avec et à la `-in` `-notin` place.

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

Exemples plus complexes :

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a>Comparaison de types

Les opérateurs de comparaison de type ( `-is` et `-isnot` ) sont utilisés pour déterminer si un objet est un type spécifique.

Syntaxe :

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

Exemple :

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a>VOIR AUSSI

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
