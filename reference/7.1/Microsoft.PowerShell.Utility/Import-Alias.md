---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 50bc53d284fada31cf01b0504d89128eeb1710e2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202777"
---
# Import-Alias

## SYNOPSIS
Importe une liste d'alias à partir d'un fichier.

## SYNTAX

### ByPath (par défaut)

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Import-Alias` applet de commande importe une liste d’alias à partir d’un fichier.

À compter de Windows PowerShell 3,0, en tant que fonctionnalité de sécurité, `Import-Alias` ne remplace pas les alias existants par défaut.
Pour remplacer un alias existant, après avoir garanti la sécurité du contenu du fichier alias, utilisez le paramètre **Force** .

## EXEMPLES

### Exemple 1 : importer des alias à partir d’un fichier

```powershell
Import-Alias test.txt
```

Cette commande importe les informations d'alias à partir d'un fichier nommé test.txt.

## PARAMETERS

### -Force

Permet à l'applet de commande d'importer un alias qui est déjà défini ou en lecture seule.
Vous pouvez utiliser la commande suivante pour afficher des informations sur les alias actuellement définis :

`Get-Alias | Select-Object Name, Options`

Si l'alias correspondant est en lecture seule, il s'affichera dans la valeur de la propriété **Options** .

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

Spécifie le chemin d'accès à un fichier qui inclut des informations sur les alias exportés.
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
Accept pipeline input: True (ByPropertyName, ByValue)
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

Spécifie le chemin d'accès à un fichier qui inclut des informations sur les alias exportés.
Les caractères génériques sont autorisés, mais ils doivent correspondre à un nom unique.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Étendue

Spécifie l'étendue dans laquelle les alias sont importés.
Les valeurs valides pour ce paramètre sont :

- Global
- Local
- Script
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)

La valeur par défaut est local.
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

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Import-Alias` .

## SORTIES

### None ou System. Management. Automation. AliasInfo

Quand vous utilisez le paramètre **PassThru** , `Import-Alias` retourne un objet **System. Management. Automation. AliasInfo** qui représente l’alias.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

