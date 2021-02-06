---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 91d0274e485573de96d9960fa49f6d327156a79a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603664"
---
# Update-FormatData

## SYNOPSIS
Met à jour les données de mise en forme dans la session active.

## SYNTAXE

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Update-FormatData` applet de commande recharge les données de mise en forme des fichiers de mise en forme dans la session active. Cette applet de commande vous permet de mettre à jour les données de mise en forme sans redémarrer PowerShell.

Sans paramètres, `Update-FormatData` recharge les fichiers de mise en forme qu’il a chargés précédemment.
Vous pouvez utiliser les paramètres de `Update-FormatData` pour ajouter de nouveaux fichiers de mise en forme à la session.

Les fichiers de mise en forme sont des fichiers texte au format XML avec l' `format.ps1xml` extension de nom de fichier. Les données de mise en forme des fichiers définissent l'affichage des objets Microsoft .NET Framework dans la session.

Lorsque PowerShell démarre, il charge les données de format à partir du code source PowerShell. Toutefois, vous pouvez créer des fichiers format.ps1XML personnalisés pour mettre à jour la mise en forme dans la session active. Vous pouvez utiliser `Update-FormatData` pour recharger les données de mise en forme dans la session active sans redémarrer PowerShell. Cela est utile quand vous avez ajouté ou modifié un fichier de mise en forme et que vous ne voulez pas interrompre la session.

Pour plus d’informations sur la mise en forme des fichiers dans PowerShell, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

## EXEMPLES

### Exemple 1 : recharger les fichiers de mise en forme déjà chargés

```powershell
Update-FormatData
```

Cette commande recharge les fichiers de mise en forme déjà chargés.

### Exemple 2 : recharger les fichiers de mise en forme et les fichiers de mise en forme de trace et de journalisation

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

Cette commande recharge les fichiers de mise en forme dans la session, y compris deux nouveaux fichiers, Trace.format.ps1xml et Log.format.ps1xml.

Étant donné que la commande utilise le paramètre **AppendPath** , les données de mise en forme des nouveaux fichiers sont chargées après les données de mise en forme des fichiers intégrés.

Le paramètre **AppendPath** est utilisé, car les nouveaux fichiers contiennent des données de mise en forme pour les objets qui ne sont pas référencés dans les fichiers intégrés.

### Exemple 3 : modifier un fichier de mise en forme et le recharger

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

Cet exemple illustre comment recharger un fichier de mise en forme une fois que vous l'avez modifié.

La première commande ajoute le fichier NewFiles.format.ps1xml à la session. Elle utilise le paramètre **prependpath** , car le fichier contient des données de mise en forme pour les objets qui sont référencés dans les fichiers intégrés.

Après avoir ajouté le fichier XML NewFiles.format.ps1et l’avoir testé dans ces sessions, l’auteur modifie le fichier.

La deuxième commande utilise l' `Update-FormatData` applet de commande pour recharger les fichiers de mise en forme. Étant donné que le fichier XML NewFiles.format.ps1a été précédemment chargé, le `Update-FormatData` recharge automatiquement sans utiliser de paramètres.

## PARAMETERS

### -AppendPath

Spécifie les fichiers de mise en forme que cette applet de commande ajoute à la session. Les fichiers sont chargés après que PowerShell a chargé les fichiers de mise en forme intégrés.

Lors de la mise en forme d’objets .NET, PowerShell utilise la première définition de mise en forme qu’il trouve pour chaque type .NET. Si vous utilisez le paramètre **AppendPath** , PowerShell recherche les données à partir des fichiers intégrés avant de rencontrer les données de mise en forme que vous ajoutez.

Utilisez ce paramètre pour ajouter un fichier mettant en forme un objet .NET qui n'est pas référencé dans les fichiers de mise en forme intégrés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PrependPath

Spécifie les fichiers de mise en forme que cette applet de commande ajoute à la session. Les fichiers sont chargés avant que PowerShell ne charge les fichiers de mise en forme intégrés.

Lors de la mise en forme d’objets .NET, PowerShell utilise la première définition de mise en forme qu’il trouve pour chaque type .NET. Si vous utilisez le paramètre **prependpath** , PowerShell recherche les données à partir des fichiers que vous ajoutez avant de rencontrer les données de mise en forme des fichiers intégrés.

Utilisez ce paramètre pour ajouter un fichier mettant en forme un objet .NET qui est également référencé dans les fichiers de mise en forme intégrés.

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

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

### System.String

Vous pouvez diriger une chaîne qui contient le chemin d’accès d’ajout vers `Update-FormatData` .

## SORTIES

### None

L'applet de commande ne retourne aucune sortie.

## REMARQUES

- `Update-FormatData` met également à jour les données de mise en forme pour les commandes de la session qui ont été importées à partir de modules. Si le fichier de mise en forme d’un module est modifié, vous pouvez exécuter une `Update-FormatData` commande pour mettre à jour les données de mise en forme des commandes importées. Il est inutile de réimporter le module.

## LIENS CONNEXES

[Get-FormatData](Get-FormatData.md)

[Export-FormatData](Export-FormatData.md)
