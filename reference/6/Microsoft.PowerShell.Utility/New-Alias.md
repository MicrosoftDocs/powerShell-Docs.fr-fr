---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: f3ae6a8873b82fd0efe39f677c640917ce9dd779
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204577"
---
# New-Alias

## SYNOPSIS
Crée un alias.

## SYNTAX

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L’applet de commande **New-alias** crée un alias dans la session PowerShell active.
Les alias créés à l’aide de **New-alias** ne sont pas enregistrés quand vous quittez la session ou fermez PowerShell.
Vous pouvez utiliser l'applet de commande Export-Alias pour enregistrer vos informations d'alias dans un fichier.
Vous pouvez par la suite utiliser **Import-alias** pour récupérer les informations d’alias enregistrées.

## EXEMPLES

### Exemple 1 : créer un alias pour une applet de commande

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

Cette commande crée un alias nommé List pour représenter l’applet de commande Get-ChildItem.

### Exemple 2 : créer un alias en lecture seule pour une applet de commande

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

Cette commande crée un alias nommé W pour représenter l’applet de commande Get-WmiObject.
Il crée une description, un alias WMI rapide, pour l’alias et le rend accessible en lecture seule.
La dernière ligne de la commande utilise Get-Alias pour obtenir le nouvel alias et le dirige vers Format-List pour afficher toutes les informations le concernant.

## PARAMETERS

### Description

Spécifie une description de l'alias.
Vous pouvez entrer n'importe quelle chaîne.
Si la description inclut des espaces, mettez-la entre guillemets.

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

Indique que l’applet de commande agit comme Set-Alias si l’alias nommé existe déjà.

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

### -Name

Spécifie le nouvel alias.
Vous pouvez utiliser des caractères alphanumériques dans un alias, mais le premier caractère ne peut pas être un nombre.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option

Spécifie la valeur de la propriété **options** de l’alias.
Les valeurs autorisées sont :

- None : l’alias n’a pas de contraintes (valeur par défaut)
- ReadOnly : l’alias peut être supprimé, mais il ne peut pas être modifié, sauf en utilisant le paramètre **force**
- Constante : l’alias ne peut pas être supprimé ou modifié
- Privé : l’alias est uniquement disponible dans l’étendue actuelle
- Options AllScope : l’alias est copié vers toutes les nouvelles étendues créées
- Non spécifié : l’option n’est pas spécifiée

Pour afficher la propriété **options** de tous les alias dans la session, tapez `Get-Alias | Format-Table -Property Name, Options -AutoSize` .

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
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

### -Étendue

Spécifie l'étendue du nouvel alias.
Les valeurs valides pour ce paramètre sont :

- Global
- Local
- Script
- Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent).

Local est la valeur par défaut.
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

### -Value

Spécifie le nom de l'élément d'applet de commande ou de commande auquel est associé un alias.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### None ou System. Management. Automation. AliasInfo

Quand vous utilisez le paramètre *PassThru* , **New-alias** génère un objet **System. Management. Automation. AliasInfo** qui représente le nouvel alias.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* Pour créer un alias, utilisez `Set-Alias` ou `New-Alias` . Pour modifier un alias, utilisez `Set-Alias` . Pour supprimer un alias, utilisez `Remove-Item` .

## LIENS CONNEXES

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[Set-Alias](Set-Alias.md)
