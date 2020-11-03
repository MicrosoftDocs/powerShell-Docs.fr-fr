---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 4ddc9af276f1d24cc687652d96ffba77897305f0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201389"
---
# Export-Alias

## SYNOPSIS
Exporte des informations sur les alias actuellement définis dans un fichier.

## SYNTAX

### ByPath (par défaut)

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Export-Alias` applet de commande exporte les alias dans la session active dans un fichier.
Si le fichier de sortie n'existe pas, l'applet de commande le crée.

`Export-Alias` peut exporter les alias dans une étendue particulière ou toutes les étendues, il peut générer les données au format CSV ou sous la forme d’une série de commandes de Set-Alias que vous pouvez ajouter à une session ou à un profil PowerShell.

## EXEMPLES

### Exemple 1 : exporter un alias

```powershell
Export-Alias -Path "alias.csv"
```

Cette commande exporte les informations d'alias actuelles dans un fichier nommé Alias.csv dans le répertoire actif.

### Exemple 2 : exporter un alias à moins que le fichier d’exportation existe déjà

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

Cette commande exporte les alias dans la session active dans un fichier Alias.csv.

Étant donné que le paramètre **NoClobber** est spécifié, la commande échoue si un fichier Alias.csv existe déjà dans le répertoire actif.

### Exemple 3 : ajouter des alias à un fichier

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

Cette commande ajoute les alias dans la session active au fichier Alias.csv.

La commande utilise le paramètre **Description** pour ajouter une description aux commentaires en haut du fichier.

La commande utilise également le paramètre **force** pour remplacer les fichiers Alias.csv existants, même s’ils ont l’attribut de lecture seule.

### Exemple 4 : exporter des alias en tant que script

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

Cet exemple montre comment utiliser le format de fichier de script `Export-Alias` généré par.

La première commande exporte les alias dans la session dans le fichier Alias.ps1.
Elle utilise le paramètre **As** avec la valeur script pour générer un fichier qui contient une commande Set-Alias pour chaque alias.

La deuxième commande ajoute les alias dans le fichier Alias.ps1 au profil CurrentUser CurrentHost.
Le chemin d’accès au profil est enregistré dans la `$Profile` variable.
La commande utilise l' `Get-Content` applet de commande pour récupérer les alias à partir du fichier Alias.ps1 et de l' `Add-Content` applet de commande pour les ajouter au profil.
Pour plus d'informations, consultez about_Providers.

Les troisième et quatrième commandes ajoutent les alias dans le fichier Alias.ps1 à une session à distance sur l’ordinateur SERVEUR01.
La troisième commande utilise l' `New-PSSession` applet de commande pour créer la session.
La quatrième commande utilise le paramètre **filePath** de l' `Invoke-Command` applet de commande pour exécuter le fichier Alias.ps1 dans la nouvelle session.

## PARAMETERS

### -Append

Indique que cette applet de commande ajoute la sortie au fichier spécifié, au lieu de remplacer le contenu existant de ce fichier.

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

### -As

Spécifie le format de sortie.
CSV est le format par défaut.
Les valeurs valides pour ce paramètre sont :

- CSV.
Format de valeurs séparées par des virgules (CSV).
- Script.
Crée une `Set-Alias` commande pour chaque alias exporté.
Si vous nommez le fichier de sortie avec une extension de nom de fichier .ps1, vous pouvez l'exécuter comme un script pour ajouter les alias à toute session.

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### Description

Spécifie la description du fichier exporté.
La description s'affiche en tant que commentaire en haut du fichier, après les informations d'en-tête.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

Remplace le fichier de sortie, même si l'attribut en lecture seule est défini sur le fichier.

Par défaut, `Export-Alias` remplace les fichiers sans avertissement, sauf si l’attribut en lecture seule ou masqué est défini ou si le paramètre **NoClobber** est utilisé dans la commande.
Le paramètre **NoClobber** est prioritaire sur le paramètre **force** quand les deux sont utilisés dans une commande.

Le paramètre **force** ne peut pas forcer le `Export-Alias` remplacement des fichiers par l’attribut Hidden.

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

### -LiteralPath

Spécifie le chemin d'accès au fichier de sortie.
Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.
Aucun caractère n’est interprété en tant que caractère générique.
Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie les noms sous la forme d’un tableau des alias à exporter.
Les caractères génériques sont autorisés.

Par défaut, `Export-Alias` exporte tous les alias dans la session ou l’étendue.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoClobber

Indique que cette applet `Export-Alias` de commande empêche de remplacer les fichiers, même si le paramètre **force** est utilisé dans la commande.

Si le paramètre **NoClobber** est omis, `Export-Alias` remplace un fichier existant sans avertissement, sauf si l’attribut en lecture seule est défini sur le fichier.
*NoClobber* est prioritaire sur le paramètre **force** , qui permet `Export-Alias` de remplacer un fichier par l’attribut de lecture seule.

*NoClobber* n’empêche pas le paramètre **Append** d’ajouter du contenu à un fichier existant.

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

### -PassThru

Retourne un objet représentant l’élément que vous utilisez.
Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Path

Spécifie le chemin d'accès au fichier de sortie.
Les caractères génériques sont autorisés, mais la valeur de chemin d'accès résultante doit être résolue en un seul nom de fichier.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Étendue

Spécifie l'étendue à partir de laquelle les alias doivent être exportés.
Les valeurs valides pour ce paramètre sont :

- Global
- Local
- Script
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues où 0 est la portée actuelle et 1 est son parent)

La valeur par défaut est Local.
Pour plus d'informations, consultez about_Scopes.

```yaml
Type: System.String
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

### Aucun.

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### None ou System. Management. Automation. AliasInfo

Quand vous utilisez le paramètre **PassThru** , `Export-Alias` retourne un objet **System. Management. Automation. AliasInfo** qui représente l’alias.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* Vous pouvez uniquement exporter des alias vers un fichier.

## LIENS CONNEXES

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)
