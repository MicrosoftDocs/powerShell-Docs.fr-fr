---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: d89d80b296d8800d65c5acfae37434e9b3f3bce9
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201809"
---
# Export-FormatData

## SYNOPSIS
Enregistre les données de mise en forme de la session active dans un fichier de mise en forme.

## SYNTAX

### ByPath (par défaut)

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### ByLiteralPath

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## Description

L' `Export-FormatData` applet de commande crée des fichiers de mise en forme PowerShell (format.ps1XML) à partir des objets de mise en forme de la session active. Elle prend les objets **ExtendedTypeDefinition** qui `Get-FormatData` sont retournées et les enregistre dans un fichier au format XML.

PowerShell utilise les données des fichiers de mise en forme (format.ps1XML) pour générer l’affichage par défaut des objets Microsoft .NET Framework dans la session. Vous pouvez afficher et modifier les fichiers de mise en forme et utiliser l'applet de commande Update-FormatData pour ajouter les données de mise en forme à une session.

Pour plus d’informations sur la mise en forme des fichiers dans PowerShell, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

## EXEMPLES

### Exemple 1 : exporter des données au format de session

```powershell
Get-FormatData -TypeName "*" -PowerShellVersion 5.1 | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

Cette commande exporte toutes les données de format de la session dans le fichier AllFormat.ps1xml.

La commande utilise l' `Get-FormatData` applet de commande pour récupérer les données de format dans la session. La valeur `*` (All) pour le paramètre **TypeName** indique à l’applet de commande d’obtenir toutes les données de la session.

La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données de format de la `Get-FormatData` commande à l’applet de commande `Export-FormatData` , qui exporte les données de format dans le fichier AllFormat.ps1.

La `Export-FormatData` commande utilise le paramètre **IncludeScriptBlock** pour inclure des blocs de script dans les données de format du fichier.

### Exemple 2 : exporter des données de format pour un type

```powershell
$F = Get-FormatData -TypeName "helpinfoshort" -PowerShellVersion 5.1
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

Ces commandes exportent les données de format pour le type **HelpInfoShort** dans le fichier XML Help.format.ps1.

La première commande utilise l' `Get-FormatData` applet de commande pour obtenir les données de format pour le type **HelpInfoShort** et l’enregistre dans la `$F` variable.

La deuxième commande utilise le paramètre **InputObject** de l' `Export-FormatData` applet de commande pour entrer les données de format enregistrées dans la `$F` variable. Elle utilise également le paramètre **IncludeScriptBlock** pour inclure des blocs de script dans la sortie.

### Exemple 3 : exporter des données au format sans bloc de script

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" -PowerShellVersion 5.1 | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

Cet exemple montre comment omettre le paramètre **IncludeScriptBlock** d’une `Export-FormatData` commande.

La première commande utilise l' `Get-FormatData` applet de commande pour obtenir les données de format pour l’objet **System. Diagnostics. Process** que l’applet de commande Get-Process retourne. La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données de mise en forme à l’applet de commande `Export-FormatData` , qui les exporte vers le fichier XML Process.format.ps1dans le répertoire actif.

Dans ce cas, la `Export-FormatData` commande n’utilise pas le paramètre **IncludeScriptBlock** .

La deuxième commande utilise l' `Update-FormatData` applet de commande pour ajouter le Process.format.ps1fichier XML à la session active. La commande utilise le paramètre **prependpath** pour garantir que les données de mise en forme pour les objets de processus dans le fichier XML Process.format.ps1se trouvent avant les données de mise en forme standard pour les objets de processus.

La troisième commande montre les effets de cette modification. La commande utilise l' `Get-Process` applet de commande pour obtenir les processus dont le nom commence par P. La sortie montre que les valeurs de propriété qui sont calculées à l’aide de blocs de script sont manquantes dans l’affichage.

## PARAMETERS

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

### -IncludeScriptBlock

Indique si les blocs de script dans les données de format sont exportés.

Comme les blocs de script contiennent du code et peuvent être utilisés à des fins malveillantes, par défaut, ils ne sont pas exportés.

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

Spécifie les objets de données de mise en forme à exporter. Entrez une variable qui contient les objets ou une commande qui obtient les objets, par exemple une `Get-FormatData` commande. Vous pouvez également diriger les objets de `Get-FormatData` vers `Export-FormatData` .

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie l'emplacement du fichier de sortie. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Indique que l’applet de commande ne remplace pas les fichiers existants. Par défaut, `Export-FormatData` remplace les fichiers sans avertissement, sauf si le fichier a l’attribut de lecture seule.

Pour indiquer au `Export-FormatData` remplacement des fichiers en lecture seule, utilisez le paramètre **force** .

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

### -Path

Spécifie l'emplacement du fichier de sortie.
Entrez un chemin d'accès (facultatif) et un nom de fichier avec une extension de nom de fichier format.ps1xml.
Si vous omettez le chemin d’accès, `Export-FormatData` crée le fichier dans le répertoire actif.

Si vous utilisez une extension de nom de fichier autre que. ps1xml, l' `Update-FormatData` applet de commande ne reconnaît pas le fichier.

Si vous spécifiez un fichier existant, `Export-FormatData` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule. Pour remplacer un fichier en lecture seule, utilisez le paramètre **force** . Pour empêcher le remplacement des fichiers, utilisez le paramètre **NoClobber** .

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. ExtendedTypeDefinition

Vous pouvez diriger les objets **ExtendedTypeDefinition** de `Get-FormatData` vers `Export-FormatData` .

## SORTIES

### Aucun

`Export-FormatData` ne retourne aucun objet.
Il génère un fichier et l'enregistre dans le chemin d'accès spécifié.

## REMARQUES

- Pour utiliser un fichier de mise en forme, y compris un fichier de mise en forme exporté, la stratégie d'exécution de la session doit autoriser l'exécution des scripts et des fichiers de configuration. Pour plus d’informations, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).

## LIENS CONNEXES

[Get-FormatData](Get-FormatData.md)

[Update-FormatData](Update-FormatData.md)
