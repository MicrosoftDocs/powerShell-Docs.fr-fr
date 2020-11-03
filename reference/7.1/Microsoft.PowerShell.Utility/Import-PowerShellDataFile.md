---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: f83718f56a3c01ca59fcda697201ff4a3598b54a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202769"
---
# Import-PowerShellDataFile

## SYNOPSIS
Importe des valeurs à partir d’un `.PSD1` fichier sans appeler son contenu.

## SYNTAX

### ByPath (par défaut)

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## Description

L' `Import-PowerShellDataFile` applet de commande importe en toute sécurité des paires clé-valeur à partir de tables de hachage définies dans un `.PSD1` fichier. Les valeurs peuvent être importées à l’aide `Invoke-Expression` de sur le contenu du fichier.
Toutefois, `Invoke-Expression` exécute tout code contenu dans le fichier. Cela peut produire des résultats indésirables ou exécuter du code non sécurisé. `Import-PowerShellDataFile` importe les données sans appeler le code.

## EXEMPLES

### Exemple 1 : récupérer des valeurs à partir de PSD1

Cet exemple récupère les paires clé-valeur stockées dans la Hashtable conservée dans le `Configuration.psd1` fichier. `Get-Content` est utilisé pour afficher le contenu du `Configuration.psd1` fichier.

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## PARAMETERS

### -LiteralPath

Chemin d’accès au fichier en cours d’importation. Tous les caractères du chemin d’accès sont traités comme des valeurs littérales.
Les caractères génériques ne sont pas traités.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Chemin d’accès au fichier en cours d’importation. Les caractères génériques sont autorisés, mais seul le premier fichier correspondant est importé.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

## SORTIES

### System.Collections.Hashtable

## REMARQUES

## LIENS CONNEXES

[Invoke-Expression](Invoke-Expression.md)

[Import-LocalizedData](Import-LocalizedData.md)

