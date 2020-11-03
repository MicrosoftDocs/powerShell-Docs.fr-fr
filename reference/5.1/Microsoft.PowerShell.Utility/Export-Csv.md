---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 5a76f8ec454ad8144f193d8927f913b89a429fec
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203306"
---
# Export-Csv

## SYNOPSIS
Convertit des objets en une série de chaînes de valeurs séparées par des virgules (CSV) et enregistre les chaînes dans un fichier.

## SYNTAX

### Délimiteur (par défaut)

```
Export-Csv [[-Path] <string>] [[-Delimiter] <char>] -InputObject <psobject> [-LiteralPath <string>]
 [-Force] [-NoClobber] [-Encoding <string>] [-Append] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### UseCulture

```
Export-Csv [[-Path] <string>] -InputObject <psobject> [-LiteralPath <string>] [-Force] [-NoClobber]
 [-Encoding <string>] [-Append] [-UseCulture] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Export-CSV` applet de commande crée un fichier csv contenant les objets que vous envoyez. Chaque objet est une ligne qui contient une liste séparée par des virgules des valeurs de propriété de l’objet. Vous pouvez utiliser l' `Export-CSV` applet de commande pour créer des feuilles de calcul et partager des données avec des programmes qui acceptent les fichiers CSV comme entrée.

Ne mettez pas en forme les objets avant de les envoyer à l’applet de commande `Export-CSV` . Si `Export-CSV` reçoit des objets mis en forme, le fichier CSV contient les propriétés de format au lieu des propriétés de l’objet. Pour exporter uniquement les propriétés sélectionnées d’un objet, utilisez l’applet de commande `Select-Object` .

## EXEMPLES

### Exemple 1 : exporter des propriétés de processus vers un fichier CSV

Cet exemple sélectionne les objets de **processus** avec des propriétés spécifiques, exporte les objets dans un fichier CSV.

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

L' `Get-Process` applet de commande obtient les objets de **processus** . Le paramètre **Name** filtre la sortie pour inclure uniquement les objets processus WmiPrvSE. Les objets processus sont envoyés dans le pipeline à l’applet de commande `Select-Object` . `Select-Object` utilise le paramètre **Property** pour sélectionner un sous-ensemble de propriétés de l’objet Process. Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` convertit les objets processus en une série de chaînes CSV. Le paramètre **path** spécifie que le fichier WmiData.csv est enregistré dans le répertoire actif. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6. L' `Import-Csv` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.

### Exemple 2 : exporter des processus vers un fichier délimité par des virgules

Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier CSV.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

L' `Get-Process` applet de commande obtient les objets de **processus** . Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` convertit les objets processus en une série de chaînes CSV.
Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.

### Exemple 3 : exporter des processus vers un fichier délimité par des points-virgules

Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier avec un délimiteur de point-virgule.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

L' `Get-Process` applet de commande obtient les objets de **processus** . Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` convertit les objets processus en une série de chaînes CSV.
Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif. Le paramètre **Delimiter** spécifie un point-virgule pour séparer les valeurs de chaîne. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.

### Exemple 4 : exporter des processus à l’aide du séparateur de liste de la culture actuelle

Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier. Le délimiteur est le séparateur de liste de la culture actuelle.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** et affiche le séparateur de liste par défaut de la culture actuelle. L' `Get-Process` applet de commande obtient les objets de **processus** .
Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` convertit les objets processus en une série de chaînes CSV. Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif. Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle comme délimiteur. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.

### Exemple 5 : exporter des processus avec des informations de type

Cet exemple explique comment inclure les informations d’en-tête **#TYPE** dans un fichier CSV. L’en-tête **#TYPE** est la valeur par défaut dans les versions antérieures à PowerShell 6,0.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

L' `Get-Process` applet de commande obtient les objets de **processus** . Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` convertit les objets processus en une série de chaînes CSV.
Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.

### Exemple 6 : exporter et ajouter des objets dans un fichier CSV

Cet exemple décrit comment exporter des objets dans un fichier CSV et utiliser le paramètre **Append** pour ajouter des objets à un fichier existant.

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

L' `Get-Service` applet de commande obtient les objets de service. Le paramètre **DisplayName** retourne les services qui contiennent l’application Word. Les objets de service sont envoyés dans le pipeline à l’applet de commande `Select-Object` . `Select-Object` utilise le paramètre **Property** pour spécifier les propriétés **DisplayName** et **Status** . La `$AppService` variable stocke les objets.

Les `$AppService` objets sont envoyés dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` convertit les objets de service en une série de chaînes CSV. Le paramètre **path** spécifie que le fichier Services.csv est enregistré dans le répertoire actif. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.

Les `Get-Service` applets de commande et `Select-Object` sont répétées pour les services qui contiennent le mot Windows. La `$WinService` variable stocke les objets de service. L' `Export-Csv` applet de commande utilise le paramètre **Append** pour spécifier que les `$WinService` objets sont ajoutés au fichier de Services.csv existant. L' `Get-Content` applet de commande est répétée pour afficher le fichier mis à jour qui comprend les données ajoutées.

### Exemple 7 : l’applet de commande format au sein d’un pipeline crée des résultats inattendus

Cet exemple montre pourquoi il est important de ne pas utiliser une applet de commande format dans un pipeline. Lors de la réception d’une sortie inattendue, corrigez la syntaxe du pipeline.

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

L' `Get-Date` applet de commande obtient l’objet **DateTime** . L’objet est envoyé dans le pipeline à l’applet de commande `Select-Object` . `Select-Object` utilise le paramètre **Property** pour sélectionner un sous-ensemble de propriétés d’objet. L’objet est envoyé dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` Convertit l’objet au format CSV. Le paramètre **path** spécifie que le fichier DateTime.csv est enregistré dans le répertoire actif. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier CSV situé dans le répertoire actif.

Lorsque l' `Format-Table` applet de commande est utilisée dans le pipeline pour sélectionner des propriétés, des résultats inattendus sont reçus. `Format-Table` envoie des objets de format de table vers l’applet de commande au lieu de l' `Export-Csv` objet **DateTime** . `Export-Csv` convertit les objets de format de table en une série de chaînes CSV. L' `Get-Content` applet de commande affiche le fichier CSV qui contient les objets de format de table.

### Exemple 8 : utilisation du paramètre force pour remplacer les fichiers en lecture seule

Cet exemple crée un fichier vide en lecture seule et utilise le paramètre **force** pour mettre à jour le fichier.

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

L' `New-Item` applet de commande utilise les paramètres **path** et **ItemType** pour créer le fichier ReadOnly.csv dans le répertoire actif. L' `Set-ItemProperty` applet de commande utilise les paramètres **Name** et **value** pour affecter la valeur true à la propriété **IsReadOnly** du fichier. L' `Get-Process` applet de commande obtient les objets de **processus** . Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` convertit les objets processus en une série de chaînes CSV. Le paramètre **path** spécifie que le fichier ReadOnly.csv est enregistré dans le répertoire actif. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6. La sortie indique que le fichier n’est pas écrit parce que l’accès est refusé.

Le paramètre **force** est ajouté à l' `Export-Csv` applet de commande pour forcer l’exportation à écrire dans le fichier. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.

### Exemple 9 : utilisation du paramètre force avec Append

Cet exemple montre comment utiliser les paramètres **force** et **Append** . Lorsque ces paramètres sont combinés, les propriétés d’objets non appariées peuvent être écrites dans un fichier CSV.

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

Une expression crée le **PSCustomObject** avec les propriétés **Name** et **version** . Les valeurs sont stockées dans la `$Content` variable. La `$Content` variable est envoyée dans le pipeline à l’applet de commande `Export-Csv` . `Export-Csv` utilise le paramètre **path** et enregistre le fichier ParmFile.csv dans le répertoire actif. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.

Une autre expression crée un **PSCustomObject** avec le **nom** et les propriétés de l' **édition** . Les valeurs sont stockées dans la `$AdditionalContent` variable. La `$AdditionalContent` variable est envoyée dans le pipeline à l’applet de commande `Export-Csv` . Le paramètre **Append** est utilisé pour ajouter les données au fichier. L’ajout échoue en raison d’une incompatibilité de nom de propriété entre la **version** et l' **édition** .

Le `Export-Csv` paramètre **force** de l’applet de commande est utilisé pour forcer l’exportation à écrire dans le fichier. La propriété **Edition** est ignorée. L' `Import-Csv` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.

## PARAMETERS

### -Append

Utilisez ce paramètre pour `Export-CSV` Ajouter la sortie CSV à la fin du fichier spécifié. Sans ce paramètre, `Export-CSV` remplace le contenu du fichier sans avertissement.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Délimiteur

Spécifie un délimiteur pour séparer les valeurs de propriété. La valeur par défaut est une virgule ( `,` ). Entrez un caractère, tel qu’un signe deux-points ( `:` ). Pour spécifier un point-virgule ( `;` ), mettez-le entre guillemets.

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `ASCII`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ASCII` Utilise le jeu de caractères ASCII (7 bits).
- `BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).
- `Default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).
- `OEM` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.
- `Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).
- `UTF7` Utilise UTF-7.
- `UTF8` Utilise UTF-8.
- `UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Ce paramètre permet `Export-Csv` de remplacer les fichiers avec l’attribut de **lecture seule** .

Lorsque les paramètres **force** et **Append** sont combinés, les objets qui contiennent des propriétés incompatibles peuvent être écrits dans un fichier CSV. Seules les propriétés correspondantes sont écrites dans le fichier. Les propriétés non appariées sont ignorées.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets à exporter en tant que chaînes CSV. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient. Vous pouvez également diriger les objets vers `Export-CSV` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d'accès au fichier de sortie CSV. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès comprend des caractères d’échappement, utilisez des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Utilisez ce paramètre pour `Export-CSV` ne pas remplacer un fichier existant. Par défaut, si le fichier existe dans le chemin d’accès spécifié, `Export-CSV` remplace le fichier sans avertissement.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoTypeInformation

Supprime l’en-tête d’informations **#TYPE** de la sortie. Ce paramètre est devenu la valeur par défaut dans PowerShell 6,0 et est inclus à des fins de compatibilité descendante.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Paramètre obligatoire qui spécifie l’emplacement d’enregistrement du fichier de sortie CSV.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément. Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Empêche le traitement de l’applet de commande ou l’apport de modifications. La sortie indique ce qui se produirait si l’applet de commande était exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet avec un adaptateur de système de type étendu (ETS) vers `Export-CSV` .

## SORTIES

### System.String

La liste CSV est envoyée au fichier désigné dans le paramètre Path.

## REMARQUES

L' `Export-CSV` applet de commande convertit les objets que vous envoyez en une série de chaînes CSV et les enregistre dans le fichier texte spécifié. Vous pouvez utiliser `Export-CSV` pour enregistrer des objets dans un fichier CSV, puis utiliser l' `Import-Csv` applet de commande pour créer des objets à partir du fichier CSV.

Dans le fichier CSV, chaque objet est représenté par une liste séparée par des virgules des valeurs de propriété de l'objet. Les valeurs de propriété sont converties en chaînes à l’aide de la méthode **ToString ()** . Les chaînes sont représentées par le nom de la valeur de propriété. 'Export-CSV n’exporte pas les méthodes de l’objet.

Les chaînes CSV sont générées comme suit :

- Par défaut, la première chaîne contient l’en-tête d’informations **#TYPE** , suivi du nom qualifié complet du type d’objet. Par exemple, **#TYPE System. Diagnostics. Process** .
- Si **NoTypeInformation** est utilisé, la première chaîne comprend les en-têtes de colonne. Les en-têtes contiennent les noms de propriété du premier objet sous la forme d’une liste séparée par des virgules.
- Les chaînes restantes contiennent des listes séparées par des virgules des valeurs de propriété de chaque objet.

Lorsque vous envoyez plusieurs objets à `Export-CSV` , `Export-CSV` organise le fichier en fonction des propriétés du premier objet que vous envoyez. Si les objets restants n'ont pas l'une des propriétés spécifiées, la valeur de propriété de cet objet est null (représentation sous forme de deux virgules consécutives). Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété ne sont pas incluses dans le fichier.

Vous pouvez utiliser la `Import-Csv` cmdlet pour recréer des objets à partir des chaînes CSV dans les fichiers. Les objets résultants sont les versions CSV des objets d'origine qui se composent des représentations de chaînes des valeurs de propriété et d'aucune méthode.

Les `ConvertTo-Csv` applets de commande et `ConvertFrom-Csv` convertissent des objets en chaînes CSV et à partir de chaînes CSV. `Export-CSV` est identique à `ConvertTo-CSV` , à ceci près qu’il enregistre les chaînes CSV dans un fichier.

## LIENS CONNEXES

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Format-Table](Format-Table.md)

[Import-Csv](Import-Csv.md)

[Select-Object](Select-Object.md)
