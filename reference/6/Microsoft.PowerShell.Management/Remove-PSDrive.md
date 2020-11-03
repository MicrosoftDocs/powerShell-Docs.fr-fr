---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 6f34e670a29ee65e4a37314472f89c463f0a49ab
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204758"
---
# Remove-PSDrive

## SYNOPSIS
Supprime les lecteurs PowerShell temporaires et déconnecte les lecteurs réseau mappés.

## SYNTAX

### Nom (par défaut)

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralName

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Remove-PSDrive` applet de commande supprime les lecteurs PowerShell temporaires qui ont été créés à l’aide de l’applet de commande `New-PSDrive` .

À compter de Windows PowerShell 3,0, `Remove-PSDrive` déconnecte également les lecteurs réseau mappés, y compris, mais sans s’y limiter, les lecteurs créés à l’aide du `Persist` paramètre de `New-PSDrive` .

`Remove-PSDrive` Impossible de supprimer les lecteurs physiques ou logiques Windows.

À compter de Windows PowerShell 3,0, lorsqu’un lecteur externe est connecté à l’ordinateur, PowerShell ajoute automatiquement un PSDrive au système de fichiers qui représente le nouveau lecteur.
Vous n’avez pas besoin de redémarrer PowerShell.
De même, lorsqu’un lecteur externe est déconnecté de l’ordinateur, PowerShell supprime automatiquement le PSDrive qui représente le lecteur supprimé.

## EXEMPLES

### Exemple 1 : supprimer un lecteur du système de fichiers

Cette commande supprime un lecteur de système de fichiers temporaire nommé « smp ».

```powershell
Remove-PSDrive -Name smp
```

### Exemple 2 : supprimer les lecteurs réseau mappés

Cette commande utilise `Remove-PSDrive` pour déconnecter les lecteurs réseau mappés X : et S :.

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## PARAMETERS

### -Force

Supprime le lecteur PowerShell actuel.

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

### -LiteralName

Spécifie le nom du lecteur.

La valeur de **LiteralName** est utilisée exactement comme elle est tapée.
Aucun caractère n’est interprété en tant que caractère générique.
Si le nom inclut des caractères d’échappement, entourez-le de guillemets simples (’).
Les guillemets simples indiquent à PowerShell qu’aucun caractère n’est interprété comme séquence d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des lecteurs à supprimer.
Ne tapez pas le signe deux-points (:) après le nom du lecteur.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PSProvider

Spécifie un tableau d’objets **PSProvider** .
Cette applet de commande supprime et déconnecte tous les lecteurs associés au fournisseur PowerShell spécifié.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Étendue

Spécifie une portée pour le lecteur.
Les valeurs acceptables pour ce paramètre sont : global, local et script, ou un nombre relatif à l’étendue actuelle. Les étendues numéro 0 à travers le nombre d’étendues. Le numéro d’étendue actuel est 0 et son parent est 1.
Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.Management.Automation.PSDriveInfo

Vous pouvez diriger un objet lecteur, tel que celui de l' `Get-PSDrive` applet de commande, vers l’applet de commande `Remove-PSDrive` .

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

- L' `Remove-PSDrive` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur PowerShell. Pour répertorier les fournisseurs disponibles dans votre session, utilisez l’applet de commande `Get-PSProvider`. Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Get-PSDrive](Get-PSDrive.md)

[New-PSDrive](New-PSDrive.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
