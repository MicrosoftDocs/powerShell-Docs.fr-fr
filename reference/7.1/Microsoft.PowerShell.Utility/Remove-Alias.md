---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 7406b2cac771ae7a741af92cd362cce834c59a50
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203665"
---
# Remove-Alias

## SYNOPSIS
Supprimer un alias de la session active.

## SYNTAX

### Valeur par défaut (par défaut)

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## Description

L' `Remove-Alias` applet de commande supprime un alias de la session PowerShell active. Pour supprimer un alias avec la propriété **option** définie sur **ReadOnly** , utilisez le paramètre **force** .

L' `Remove-Alias` applet de commande a été introduite dans PowerShell 6,0.

## EXEMPLES

### Exemple 1 : supprimer un alias

Cet exemple supprime un alias nommé `del` qui représente l' `Remove-Item` applet de commande.

```powershell
Remove-Alias -Name del
```

### Exemple 2 : supprimer tous les alias non constants

Cet exemple supprime tous les alias de la session PowerShell active, à l’exception des alias dont la propriété **options** a la valeur **constant** . Une fois la commande exécutée, les alias sont disponibles dans d’autres sessions PowerShell ou dans de nouvelles sessions PowerShell.

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

`Get-Alias` Obtient tous les alias dans la session PowerShell et envoie les objets dans le pipeline.
`Where-Object` utilise un bloc de script, et la propriété automatique variable ( `$_` ) et **options** représente l’objet de pipeline actuel. Le paramètre **ne** (pas égal à), sélectionne les objets qui n’ont pas de valeur d' **option** définie sur **constant** . `Remove-Alias` utilise le paramètre **force** pour supprimer des alias, y compris des alias en lecture seule, à partir de la session PowerShell.

## PARAMETERS

### -Force

Indique que l’applet de commande supprime un alias, y compris les alias avec la propriété **option** définie sur **ReadOnly** . Le paramètre **force** ne peut pas supprimer un alias avec une propriété **option** définie sur **constant** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie le nom de l’alias à supprimer.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Étendue

Affecte uniquement les alias dans l’étendue spécifiée. La portée par défaut est **local** . Pour plus d’informations, consultez [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).

Les valeurs valides pour ce paramètre sont :

- Global
- Local
- Script
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

Vous pouvez diriger un objet alias vers **Remove-alias** .

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

Les modifications affectent uniquement l’étendue actuelle. Pour supprimer un alias de toutes les sessions, ajoutez une commande **Remove-alias** à votre profil PowerShell.

Pour plus d’informations, consultez [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).

## LIENS CONNEXES

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

