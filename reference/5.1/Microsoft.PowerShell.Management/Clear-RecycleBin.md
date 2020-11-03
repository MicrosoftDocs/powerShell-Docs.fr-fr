---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 9314aaf7c444f9a1159b301135d4130737daa439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204062"
---
# Clear-RecycleBin

## SYNOPSIS
Efface le contenu d’une corbeille.

## SYNTAX

### Tous

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Clear-RecycleBin` applet de commande supprime le contenu de la corbeille d’un ordinateur. Cette action est semblable à l’utilisation de la **Corbeille vide** Windows.

## EXEMPLES

### 1 : effacer toutes les corbeilles

Dans cet exemple, toutes les corbeilles de l’ordinateur local sont effacées.

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

`Clear-RecycleBin` invite l’utilisateur à confirmer l’effacement de toutes les corbeilles sur l’ordinateur local.

### 2 : effacer une corbeille spécifiée

Cet exemple efface la Corbeille pour une lettre de lecteur spécifiée.

```powershell
Clear-RecycleBin -DriveLetter C
```

`Clear-RecycleBin` utilise le paramètre **LettreLecteur** pour spécifier la corbeille sur le volume **C** . L’utilisateur est invité à confirmer l’exécution de la commande.

### 3 : effacer toutes les corbeilles sans confirmation

Cet exemple ne demande pas de confirmation pour effacer les corbeilles de l’ordinateur local.

```powershell
Clear-RecycleBin -Force
```

`Clear-RecycleBin` utilise le paramètre **force** et ne demande pas à l’utilisateur de confirmer l’effacement de toutes les corbeilles sur l’ordinateur local.

Une alternative consiste à remplacer `-Force` par `-Confirm:$false` .

## PARAMETERS

### -LettreLecteur

Spécifie la corbeille à effacer pour une lettre de lecteur unique ou un tableau de lettres de lecteur.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

Spécifie que l’utilisateur n’est pas invité à confirmer l’effacement d’une corbeille.

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

### -Confirm

Demande une confirmation de l’utilisateur avant d’exécuter l’applet de commande. L’utilisateur est invité à confirmer, même si le paramètre **Confirm** n’est pas spécifié.

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

Montre ce qui se passe si `Clear-RecycleBin` s’exécute. L’applet de commande n’est pas exécutée.

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

## SORTIES

### Aucun

## REMARQUES

## LIENS CONNEXES