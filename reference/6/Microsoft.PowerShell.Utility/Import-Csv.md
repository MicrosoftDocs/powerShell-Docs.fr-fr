---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/8/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Csv
ms.openlocfilehash: ed70095cd5c1ab199bdab1eee06504c8eef7a418
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203778"
---
# Import-Csv

## SYNOPSIS
Crée des objets personnalisés de type tableau à partir des éléments dans un fichier de valeurs séparées par des virgules (CSV).

## SYNTAX

### DelimiterPath (par défaut)

```
Import-Csv [[-Delimiter] <Char>] [-Path] <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### DelimiterLiteralPath

```
Import-Csv [[-Delimiter] <Char>] -LiteralPath <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CulturePath

```
Import-Csv [-Path] <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CultureLiteralPath

```
Import-Csv -LiteralPath <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

## Description

L' `Import-Csv` applet de commande crée des objets personnalisés de type table à partir des éléments des fichiers CSV. Chaque colonne du fichier CSV devient une propriété de l’objet personnalisé et les éléments des lignes deviennent les valeurs de propriété. `Import-Csv` fonctionne sur n’importe quel fichier CSV, y compris les fichiers générés par l’applet de commande `Export-Csv` .

Vous pouvez utiliser les paramètres de l' `Import-Csv` applet de commande pour spécifier la ligne d’en-tête de colonne et le séparateur d’éléments, ou directement `Import-Csv` pour utiliser le séparateur de liste pour la culture actuelle comme délimiteur d’élément.

Vous pouvez également utiliser les `ConvertTo-Csv` applets de commande et `ConvertFrom-Csv` pour convertir des objets en chaînes CSV (et inversement). Ces applets de commande sont les mêmes que les `Export-CSV` applets de commande et `Import-Csv` , à ceci près qu’elles ne traitent pas les fichiers.

Si une entrée de ligne d’en-tête dans un fichier CSV contient une valeur vide ou null, PowerShell insère un nom de ligne d’en-tête par défaut et affiche un message d’avertissement.

À compter de PowerShell 6,0, `Import-Csv` prend désormais en charge le format de fichier journal étendu W3C.

## EXEMPLES

### Exemple 1 : importer des objets de processus

Cet exemple montre comment exporter, puis importer un fichier CSV d’objets de processus.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
$P = Import-Csv -Path .\Processes.csv
$P | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name                       MemberType   Definition
----                       ----------   ----------
Equals                     Method       bool Equals(System.Object obj)
GetHashCode                Method       int GetHashCode()
GetType                    Method       type GetType()
ToString                   Method       string ToString()
BasePriority               NoteProperty string BasePriority=8
Company                    NoteProperty string Company=Microsoft Corporation
...
```

```powershell
$P | Format-Table
```

```Output
Name                   SI Handles VM            WS        PM        NPM    Path
----                   -- ------- --            --        --        ---    ----
ApplicationFrameHost   4  407     2199293489152 15884288  15151104  23792  C:\WINDOWS\system32\ApplicationFrameHost.exe
...
wininit                0  157     2199112204288 4591616   1630208   10376
winlogon               4  233     2199125549056 7659520   2826240   10992  C:\WINDOWS\System32\WinLogon.exe
WinStore.App           4  846     873435136     33652736  26607616  55432  C:\Program Files\WindowsApps\Microsoft.WindowsStore_11712.1001.13.0_x64__8weky...
WmiPrvSE               0  201     2199100219392 8830976   3297280   10632  C:\WINDOWS\system32\wbem\wmiprvse.exe
WmiPrvSE               0  407     2199157727232 18509824  12922880  16624  C:\WINDOWS\system32\wbem\wmiprvse.exe
WUDFHost               0  834     2199310204928 51945472  87441408  24984  C:\Windows\System32\WUDFHost.exe
```

L' `Get-Process` applet de commande envoie les objets de processus vers le dessous du pipeline `Export-Csv` . L' `Export-Csv` applet de commande convertit les objets processus en chaînes CSV et enregistre les chaînes dans le fichier Processes.csv. L' `Import-Csv` applet de commande importe les chaînes CSV à partir du fichier Processes.csv.
Les chaînes sont enregistrées dans la `$P` variable. La `$P` variable est envoyée dans le pipeline à l’applet de commande `Get-Member` qui affiche les propriétés des chaînes CSV importées. La `$P` variable est envoyée dans le pipeline à l’applet de commande `Format-Table` et affiche les objets.

### Exemple 2 : spécifier le délimiteur

Cet exemple montre comment utiliser le paramètre **Delimiter** de l’applet de commande `Import-Csv` .

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter :
$P = Import-Csv -Path .\Processes.csv -Delimiter :
$P | Format-Table
```

L' `Get-Process` applet de commande envoie les objets de processus vers le dessous du pipeline `Export-Csv` . L' `Export-Csv` applet de commande convertit les objets processus en chaînes CSV et enregistre les chaînes dans le fichier Processes.csv.
Le paramètre **Delimiter** est utilisé pour spécifier un séparateur deux-points. L' `Import-Csv` applet de commande importe les chaînes CSV à partir du fichier Processes.csv. Les chaînes sont enregistrées dans la `$P` variable. `$P`La variable est envoyée à l’applet de commande via le pipeline `Format-Table` .

### Exemple 3 : spécifier la culture actuelle pour le délimiteur

Cet exemple montre comment utiliser l' `Import-Csv` applet de commande avec le paramètre **UseCulture** .

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture
Import-Csv -Path .\Processes.csv -UseCulture
```

L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** pour récupérer le séparateur de liste par défaut de la culture actuelle. L' `Get-Process` applet de commande envoie les objets de processus vers le dessous du pipeline `Export-Csv` . L' `Export-Csv` applet de commande convertit les objets processus en chaînes CSV et enregistre les chaînes dans le fichier Processes.csv. Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle. L' `Import-Csv` applet de commande importe les chaînes CSV à partir du fichier Processes.csv.

### Exemple 4 : modifier les noms de propriété dans un objet importé

Cet exemple montre comment utiliser le paramètre **header** de `Import-Csv` pour modifier les noms des propriétés dans l’objet importé résultant.

```powershell
Start-Job -ScriptBlock { Get-Process } | Export-Csv -Path .\Jobs.csv -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from file
$A = Get-Content -Path .\Jobs.csv
$A = $A[1..($A.Count - 1)]
$A | Out-File -FilePath .\Jobs.csv
$J = Import-Csv -Path .\Jobs.csv -Header $Header
$J
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

L' `Start-Job` applet de commande démarre une tâche en arrière-plan qui s’exécute `Get-Process` . Un objet de traitement est envoyé par le pipeline à l’applet de commande `Export-Csv` et converti en une chaîne CSV. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations de type de la sortie CSV et est facultatif dans PowerShell Core.
La `$Header` variable contient un en-tête personnalisé qui remplace les valeurs par défaut suivantes : **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** et **PSJobTypeName** . La `$A` variable utilise l' `Get-Content` applet de commande pour récupérer la chaîne CSV à partir du fichier Jobs.csv. La `$A` variable est utilisée pour supprimer l’en-tête par défaut du fichier. L' `Out-File` applet de commande enregistre la nouvelle version du fichier de Jobs.csv dans la `$A` variable. L' `Import-Csv` applet de commande importe le fichier Jobs.csv et utilise le paramètre d' **en-tête** pour appliquer la `$Header` variable. La `$J` variable contient le **PSCustomObject** importé et affiche l’objet dans la console PowerShell.

### Exemple 5 : créer un objet personnalisé à l’aide d’un fichier CSV

Cet exemple montre comment créer un objet personnalisé dans PowerShell à l’aide d’un fichier CSV.

```powershell
Get-Content -Path .\Links.csv
```

```Output
113207,about_Aliases
113208,about_Arithmetic_Operators
113209,about_Arrays
113210,about_Assignment_Operators
113212,about_Automatic_Variables
113213,about_Break
113214,about_Command_Precedence
113215,about_Command_Syntax
144309,about_Comment_Based_Help
113216,about_CommonParameters
113217,about_Comparison_Operators
113218,about_Continue
113219,about_Core_Commands
113220,about_Data_Section
```

```powershell
$A = Import-Csv -Path .\Links.csv -Header 'LinkID', 'TopicTitle'
$A | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
LinkID      NoteProperty string LinkID=113207
TopicTitle  NoteProperty string TopicTitle=about_Aliases
```

```powershell
$A | Where-Object -Property TopicTitle -Like '*alias*'
```

```Output
LinkID TopicTitle
------ ----------
113207 about_Aliases
```

Pour créer votre fichier Links.csv, utilisez les valeurs indiquées dans la `Get-Content` sortie.

L' `Get-Content` applet de commande affiche le fichier Links.csv. L' `Import-Csv` applet de commande importe le fichier Links.csv. Le paramètre **header** spécifie les noms de propriété **LinkId** et **TopicTitle** . Les objets sont stockés dans la `$A` variable. L' `Get-Member` applet de commande affiche les noms des propriétés à partir du paramètre d' **en-tête** . L' `Where-Object` applet de commande sélectionne des objets avec la propriété **TopicTitle** qui comprend un **alias** .

### Exemple 6 : importer un fichier CSV auquel il manque une valeur

Cet exemple montre comment l' `Import-Csv` applet de commande dans PowerShell répond lorsque la ligne d’en-tête d’un fichier CSV contient une valeur null ou vide. `Import-Csv` remplace le nom par défaut de la ligne d’en-tête manquante qui devient le nom de la propriété de l’objet `Import-Csv` retourné par.

```powershell
Get-Content -Path .\Projects.csv
```

```Output
ProjectID,ProjectName,,Completed
13,Inventory,Redmond,True
440,,FarEast,True
469,Marketing,Europe,False
```

```powershell
Import-Csv -Path .\Projects.csv
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.

ProjectID ProjectName H1      Completed
--------- ----------- --      ---------
13        Inventory   Redmond True
440                   FarEast True
469       Marketing   Europe  False
```

```powershell
(Import-Csv -Path .\Projects.csv).H1
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.
Redmond
FarEast
Europe
```

Pour créer votre fichier Projects.csv, utilisez les valeurs indiquées dans la sortie de l’exemple `Get-Content` .

L' `Get-Content` applet de commande affiche le fichier Projects.csv. La ligne d’en-tête ne contient pas de valeur comprise entre **ProjectName** et **Completed** . L' `Import-Csv` applet de commande importe le fichier Projects.csv et affiche un message d’avertissement, car **H1** est un nom d’en-tête par défaut. La `(Import-Csv -Path
.\Projects.csv).H1` commande obtient les valeurs de propriété **H1** et affiche un avertissement.

## PARAMETERS

### -Délimiteur

Spécifie le délimiteur qui sépare les valeurs de propriété dans le fichier CSV.
La valeur par défaut est une virgule (,).

Entrez un caractère, tel qu'un signe deux-points (:).
Pour spécifier un point-virgule (;) Placez-le entre guillemets simples.

Si vous spécifiez un caractère autre que le délimiteur de chaîne réel dans le fichier, `Import-Csv` ne peut pas créer les objets à partir des chaînes CSV et renverra les chaînes CSV.

```yaml
Type: System.Char
Parameter Sets: DelimiterPath, DelimiterLiteralPath
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Spécifie l’encodage pour le fichier CSV importé. La valeur par défaut est `utf8NoBOM`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- `bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.
- `unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7`: Encode au format UTF-7.
- `utf8`: Encode au format UTF-8.
- `utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- `utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- `utf32`: Encode au format UTF-32.

À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ). Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -En-tête

Spécifie une autre ligne d'en-tête de colonne pour la chaîne importée. L’en-tête de colonne détermine les noms des propriétés des objets créés par `Import-Csv` .

Entrez les en-têtes de colonne sous la forme d’une liste séparée par des virgules. Ne placez pas la chaîne d'en-tête entre guillemets. Mettez chaque en-tête de colonne entre guillemets simples.

Si vous entrez moins d’en-têtes de colonnes qu’il n’y a de colonnes de données, les colonnes de données restantes sont ignorées. Si vous entrez davantage d’en-têtes de colonne qu’il n’y a de colonnes de données, les en-têtes de colonne supplémentaires sont créés avec des colonnes de données vides.

Quand vous utilisez le paramètre **header** , supprimez la ligne d’en-tête d’origine du fichier CSV. Sinon, `Import-Csv` crée un objet supplémentaire à partir des éléments de la ligne d’en-tête.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d'accès au fichier CSV à importer. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: DelimiterLiteralPath, CultureLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d'accès au fichier CSV à importer.
Vous pouvez également diriger un chemin vers `Import-Csv` .

```yaml
Type: System.String[]
Parameter Sets: DelimiterPath, CulturePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément. Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CulturePath, CultureLiteralPath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Import-Csv` .

## SORTIES

### Object

Cette applet de commande retourne les objets décrits par le contenu dans le fichier CSV.

## REMARQUES

Étant donné que les objets importés sont des versions CSV du type d’objet, ils ne sont pas reconnus ni mis en forme par les entrées de mise en forme de type PowerShell qui mettent en forme les versions non-CSV du type d’objet.

Le résultat d’une `Import-Csv` commande est une collection de chaînes qui forment un objet personnalisé de type table. Chaque ligne étant une chaîne distincte, vous pouvez utiliser la propriété **Count** de l’objet pour compter les lignes de la table. Les colonnes sont les propriétés de l'objet et les éléments des lignes sont les valeurs de propriété.

La ligne d'en-tête de colonne détermine le nombre de colonnes et les noms de colonne. Les noms de colonne sont également les noms des propriétés des objets. La première ligne est interprétée comme étant les en-têtes de colonne, sauf si vous utilisez le paramètre **header** pour spécifier des en-têtes de colonne. Si une ligne possède plus de valeurs que la ligne d'en-tête, les valeurs supplémentaires sont ignorées.

Si une valeur est manquante dans la ligne d’en-tête de colonne ou si elle contient une valeur null ou vide, `Import-Csv` utilise **H** suivi d’un nombre pour l’en-tête de colonne et le nom de propriété manquants.

Dans le fichier CSV, chaque objet est représenté par une liste séparée par des virgules des valeurs de propriété de l'objet. Les valeurs de propriété sont converties en chaînes à l’aide de la méthode **ToString ()** de l’objet. elles sont donc représentées par le nom de la valeur de la propriété. `Export-Csv` n’exporte pas les méthodes de l’objet.

`Import-Csv` prend également en charge le format de journal W3C étendu. Les lignes commençant par `#` sont traitées comme des commentaires et ignorées, sauf si le commentaire commence par `#Fields:` et contient une liste délimitée de noms de colonnes. Dans ce cas, l’applet de commande utilise ces noms de colonnes. Il s’agit du format standard pour Windows IIS et d’autres journaux de serveur Web. Pour plus d’informations, consultez [format de fichier journal étendu](https://www.w3.org/TR/WD-logfile.html).

## LIENS CONNEXES

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Export-Csv](Export-Csv.md)

[Get-Culture](Get-Culture.md)
