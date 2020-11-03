---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 0024bb83b983d0b13e2fbfafb24505849acf15f6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202826"
---
# Get-FormatData

## SYNOPSIS
Obtient les données de mise en forme de la session active.

## SYNTAX

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## Description

L' `Get-FormatData` applet de commande obtient les données de mise en forme de la session active.

Les données de mise en forme de la session incluent la mise en forme des données des `Format.ps1xml` fichiers de mise en forme, tels que ceux de l' `$PSHOME` annuaire, la mise en forme des données des modules que vous importez dans la session et la mise en forme des données pour les commandes que vous importez dans votre session à l’aide de l’applet de commande `Import-PSSession` .

Vous pouvez utiliser cette applet de commande pour examiner les données de mise en forme. Ensuite, vous pouvez utiliser l' `Export-FormatData` applet de commande pour sérialiser les objets, les convertir en XML et les enregistrer dans des `Format.ps1xml` fichiers.

Pour plus d’informations sur la mise en forme des fichiers dans PowerShell, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

## EXEMPLES

### Exemple 1 : récupération de toutes les données de mise en forme

Cet exemple obtient toutes les données de mise en forme de la session.

```powershell
Get-FormatData
```

### Exemple 2 : récupérer les données de mise en forme par nom de type

Cet exemple obtient les éléments de données de mise en forme dont les noms commencent par `System.Management.Automation.Cmd` .

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### Exemple 3 : examiner un objet de données de mise en forme

Cet exemple illustre comment obtenir un objet de données de mise en forme et examiner ses propriétés.

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### Exemple 4 : récupérer des données de mise en forme et les exporter

Cet exemple montre comment utiliser `Get-FormatData` et `Export-FormatData` pour exporter les données de mise en forme ajoutées par un module.

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

Les quatre premières commandes utilisent les `Get-FormatData` applets de commande, `Import-Module` et `Compare-Object` pour identifier le type de format que le module **BitsTransfer** ajoute à la session.

La cinquième commande utilise l' `Get-FormatData` applet de commande pour récupérer le type de format ajouté par le module **BitsTransfer** . Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet de type de format à l’applet de commande `Export-FormatData` , qui le convertit en XML et l’enregistre dans le `format.ps1xml` fichier spécifié.

La dernière commande affiche un extrait du `format.ps1xml` contenu du fichier.

### Exemple 5 : récupérer des données de mise en forme en fonction de la version spécifiée de PowerShell

Cet exemple montre comment utiliser `Get-FormatData` pour obtenir les données de format pour un **TypeName** et une version PowerShell spécifiés.

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## PARAMETERS

### -PowerShellVersion

Spécifiez la version de PowerShell que cette applet de commande obtient pour les données de mise en forme. Entrez un nombre à deux chiffres, séparé par un point.

Ce paramètre a été ajouté dans PowerShell 5,1 pour améliorer la compatibilité lors de la communication à distance d’ordinateurs exécutant des versions antérieures de PowerShell.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Spécifie les noms de types que cette applet de commande obtient pour les données de mise en forme.
Entrez les noms des types.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. ExtendedTypeDefinition

## REMARQUES

## LIENS CONNEXES

[Export-FormatData](Export-FormatData.md)

[Update-FormatData](Update-FormatData.md)
