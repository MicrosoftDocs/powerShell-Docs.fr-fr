---
description: PowerShell offre la possibilité d’ajouter dynamiquement de nouvelles propriétés et de modifier la mise en forme de la sortie des objets dans le pipeline.
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 7937d4e59f2e73c8b52e9957dd143b6d48eeae57
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206665"
---
# <a name="about-calculated-properties"></a>À propos des propriétés calculées

## <a name="short-description"></a>Description courte

PowerShell offre la possibilité d’ajouter dynamiquement de nouvelles propriétés et de modifier la mise en forme de la sortie des objets dans le pipeline.

## <a name="long-description"></a>Description longue

Un certain nombre d’applets de commande PowerShell transforment, agrègent ou traitent des objets d’entrée en objets de sortie à l’aide de paramètres qui permettent d’ajouter de nouvelles propriétés à ces objets de sortie. Ces paramètres peuvent être utilisés pour générer de nouvelles propriétés calculées sur les objets de sortie en fonction des valeurs des objets d’entrée.
La propriété calculée est définie par une [Hashtable](about_hash_tables.md) contenant des paires clé-valeur qui spécifient le nom de la nouvelle propriété, une expression pour calculer la valeur et des informations de mise en forme facultatives.

## <a name="supported-cmdlets"></a>Applets de commande prises en charge

Les applets de commande suivantes prennent en charge les valeurs de propriété calculées pour le paramètre **Property** . Les `Format-*` applets de commande prennent également en charge les valeurs calculées pour le paramètre **GroupBy** .

La liste suivante détaille les applets de commande qui prennent en charge les propriétés calculées et les paires clé-valeur prises en charge par chaque applet de commande.

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - `name`/`label` -facultatif (ajouté dans PowerShell 6. x)
  - `expression`
  - `width` -facultatif
  - `alignment` -facultatif

- `Format-Custom`
  - `expression`
  - `depth` -facultatif

- `Format-List`
  - `name`/`label` -facultatif
  - `expression`
  - `formatstring` -facultatif

  Ce même jeu de paires clé-valeur s’applique également aux valeurs de propriété calculées transmises au paramètre **GroupBy** pour toutes les `Format-*` applets de commande.

- `Format-Table`
  - `name`/`label` -facultatif
  - `expression`
  - `formatstring` -facultatif
  - `width` -facultatif
  - `alignment` -facultatif

- `Format-Wide`
  - `expression`
  - `formatstring` -facultatif

- `Group-Object`
  - `expression`

- `Measure-Object`
  - Ne prend en charge qu’un bloc de script pour l’expression, et non une Hashtable.
  - Non pris en charge dans PowerShell 5,1 et versions antérieures.

- `Select-Object`
  - `name`/`label` -facultatif
  - `expression`

- `Sort-Object`
  - `expression`
  - `ascending`/`descending` -facultatif

> [!NOTE]
> La valeur de `expression` peut être un bloc de script au lieu d’une Hashtable. Pour plus d’informations, consultez la section [Remarques](#notes) .

## <a name="hashtable-key-definitions"></a>Définitions de clé de la Hashtable

- `name`/`label` -Spécifie le nom de la propriété en cours de création. Vous pouvez utiliser `name` ou son alias, `label` , interchangeable.
- `expression` : Bloc de script utilisé pour calculer la valeur de la nouvelle propriété.
- `alignment` -Utilisé par les applets de commande qui produisent une sortie tabulaire pour définir la manière dont les valeurs sont affichées dans une colonne. La valeur doit être `'left'` , `'center'` ou `'right'` .
- `formatstring` : Spécifie une chaîne de format qui définit la façon dont la valeur est mise en forme pour la sortie. Pour plus d’informations sur les chaînes de format, consultez [types de format dans .net](/dotnet/standard/base-types/formatting-types).
- `width` -Spécifie la largeur maximale d’une colonne dans une table lorsque la valeur est affichée. La valeur doit être supérieure à `0` .
- `depth` -Le paramètre **Depth** de `Format-Custom` spécifie la profondeur d’expansion pour toutes les propriétés. La `depth` clé vous permet de spécifier la profondeur d’expansion par propriété.
- `ascending` / `descending` -Vous permet de spécifier l’ordre de tri pour une ou plusieurs propriétés. Il s’agit de valeurs booléennes.

Les clés Hashtable n’ont pas besoin d’être épelées tant que le préfixe de nom spécifié n’est pas ambigu. Par exemple, `n` peut être utilisé à la place de `Name` et `e` peut être utilisé à la place de `Expression` .

## <a name="examples"></a>Exemples

### <a name="compare-object"></a>Compare-Object

Avec les propriétés calculées, vous pouvez contrôler la façon dont les propriétés des objets d’entrée sont comparées. Dans cet exemple, au lieu de comparer directement les valeurs, les valeurs sont comparées au résultat de l’opération arithmétique (modulo de 2).

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a>ConvertTo-Html

`ConvertTo-Html` peut convertir une collection d’objets en tableau HTML.
Les propriétés calculées vous permettent de contrôler la façon dont la table est présentée.

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

Cet exemple crée une table HTML contenant une liste d’alias PowerShell et les paramètres de nombre pour chaque commande avec alias. Les valeurs de la colonne **ParameterCount** sont centrées.

### <a name="format-custom"></a>Format-Custom

`Format-Custom` fournit une vue personnalisée d’un objet dans un format semblable à une définition de classe. Les objets plus complexes peuvent contenir des membres profondément imbriqués avec des types complexes. Le paramètre **Depth** de `Format-Custom` spécifie la profondeur d’expansion pour toutes les propriétés. La `depth` clé vous permet de spécifier la profondeur d’expansion par propriété.

Dans cet exemple, la `depth` clé simplifie la sortie personnalisée pour l' `Get-Date` applet de commande. `Get-Date` retourne un objet **DateTime** . La propriété de **Date** de cet objet est également un objet **DateTime** , de sorte que l’objet est imbriqué.

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a>Format-List

Dans cet exemple, nous utilisons des propriétés calculées pour modifier le nom et le format de la sortie de `Get-ChildItem` .

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a>Format-Table

Dans cet exemple, la propriété calculée ajoute une propriété de **type** utilisée pour classifier les fichiers selon le type de contenu.

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a>Format-Wide

L' `Format-Wide` applet de commande vous permet d’afficher la valeur d’une propriété pour les objets d’une collection sous la forme d’une liste à plusieurs colonnes.

Pour cet exemple, nous souhaitons voir le nom de fichier et la taille (en kilo-octets) comme une liste étendue. Étant donné que `Format-Wide` n’affiche pas plus d’une propriété, nous utilisons une propriété calculée pour combiner la valeur de deux propriétés en une seule valeur.

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a>Group-Object

L' `Group-Object` applet de commande affiche les objets dans des groupes en fonction de la valeur d’une propriété spécifiée. Dans cet exemple, la propriété calculée compte le nombre de fichiers de chaque type de contenu.

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a>Measure-Object

L' `Measure-Object` applet de commande calcule les propriétés numériques des objets. Dans cet exemple, nous utilisons une propriété calculée pour obtenir le nombre ( **somme** ) des nombres, compris entre 1 et 10, qui sont uniformément divisibles par 3.

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> Contrairement aux autres applets de commande, `Measure-Object` n’accepte pas de Hashtable pour les propriétés calculées. Vous devez utiliser un bloc de script.

### <a name="select-object"></a>Select-Object

Vous pouvez utiliser des propriétés calculées pour ajouter des membres supplémentaires à la sortie d’objets avec l’applet de commande `Select-Object` . Dans cet exemple, nous répertorions les alias PowerShell qui commencent par la lettre `C` . À l’aide de `Select-Object` , nous sortons l’alias, l’applet de commande à laquelle il est mappé et le nombre de paramètres définis pour l’applet de commande. À l’aide d’une propriété calculée, nous pouvons créer la propriété **ParameterCount** .

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a>Sort-Object

À l’aide des propriétés calculées, vous pouvez trier les données dans différents ordres par propriété. Cet exemple trie les données d’un fichier CSV dans l’ordre croissant par **Date** . Mais dans chaque date, il trie les lignes par ordre décroissant de **UnitsSold** .

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a>Notes

- Vous pouvez spécifier _directement_ le bloc de script d’expression, en tant qu’argument, au lieu de le spécifier comme `Expression` entrée dans une Hashtable. Par exemple :

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  Cet exemple est pratique pour les applets de commande qui ne nécessitent pas (ou prennent en charge) le nommage d’une propriété via la `Name` clé, par exemple `Sort-Object` , `Group-Object` et `Measure-Object` .

  Pour les applets de commande qui prennent en charge l’attribution d’un nom à la propriété, le bloc de script est converti en une chaîne et utilisé comme nom de la propriété dans la sortie.

- `Expression` les blocs de script s’exécutent dans des portées _enfants_ , ce qui signifie que les variables de l’appelant ne peuvent pas être modifiées directement.

- La logique de pipeline est appliquée à la sortie des `Expression` blocs de script. Cela signifie que la génération d’un tableau à un seul élément entraîne le désencapsulage de ce tableau.

- Pour la plupart des cmdlets, les erreurs contenues dans les blocs de script d’expression sont ignorées en mode silencieux.
  Pour `Sort-Object` , les erreurs d’instruction et de fin de script sont _générées_ , mais elles ne terminent pas l’instruction.

## <a name="see-also"></a>Voir aussi

[about_Hash_Tables](about_hash_tables.md)

[Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[Format-Custom](xref:Microsoft.PowerShell.Utility.Format-Custom)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Format-Wide](xref:Microsoft.PowerShell.Utility.Format-Wide)

[Group-Object](xref:Microsoft.PowerShell.Utility.Group-Object)

[Measure-Object](xref:Microsoft.PowerShell.Utility.Measure-Object)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Sort-Object](xref:Microsoft.PowerShell.Utility.Sort-Object)

[Types de format dans .NET](/dotnet/standard/base-types/formatting-types)
