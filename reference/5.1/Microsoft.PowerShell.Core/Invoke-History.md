---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 613b460678186380b518a0bc04abc426c1038a84
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202278"
---
# Invoke-History

## SYNOPSIS
Exécute des commandes à partir de l'historique de session.

## SYNTAX

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Invoke-History` applet de commande exécute des commandes à partir de l’historique de session. Vous pouvez passer des objets représentant les commandes de Get-History à `Invoke-History` ou vous pouvez identifier les commandes dans l’historique actuel à l’aide de leur numéro d' **identification** . Pour rechercher le numéro d’identification d’une commande, utilisez l’applet de commande `Get-History` .

L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .
Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé. Cette applet de commande fonctionne uniquement avec l’historique de session. Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

## EXEMPLES

### Exemple 1 : exécuter la commande la plus récente dans l’historique

Cet exemple exécute la dernière commande, ou la plus récente, dans l’historique de session. Vous pouvez abréger cette commande en tant que `r` , l’alias de `Invoke-History` .

```powershell
Invoke-History
```

### Exemple 2 : exécuter la commande avec un ID spécifié

Cet exemple exécute la commande dans l’historique de session avec l' **Id** 132. Étant donné que le nom du paramètre **ID** est facultatif, vous pouvez abréger cette commande comme suit : `Invoke-History 132` , `ihy 132` ou `r 132` .

```powershell
Invoke-History -Id 132
```

### Exemple 3 : exécuter la commande la plus récente à l’aide du texte de la commande

Cet exemple exécute la commande la plus récente `Get-Process` dans l’historique de session. Lorsque vous tapez des caractères pour le paramètre **ID** , `Invoke-History` exécute la première commande trouvée qui correspond au modèle, en commençant par les commandes les plus récentes.

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> Les critères spéciaux ne respectent pas la casse, mais le modèle correspond au début de la ligne.

### Exemple 4 : exécuter une séquence de commandes à partir de l’historique

Cet exemple exécute les commandes 16 à 24. Étant donné que vous ne pouvez répertorier qu’une seule valeur d' **ID** , la commande utilise l' `ForEach-Object` applet de commande pour exécuter la `Invoke-History` commande une fois pour chaque valeur d' **ID** .

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### Exemple 5

Cet exemple exécute les sept commandes dans l’historique qui se terminent par la commande 255 (249 à 255). Elle utilise l' `Get-History` applet de commande pour récupérer les commandes. Étant donné que vous ne pouvez répertorier qu’une seule valeur d' **ID** , la commande utilise l' `ForEach-Object` applet de commande pour exécuter la `Invoke-History` commande une fois pour chaque valeur d' **ID** .

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## PARAMETERS

### -Id

Spécifie l' **ID** d’une commande dans l’historique. Vous pouvez taper le numéro d' **identification** de la commande ou les premiers caractères de la commande.

Si vous tapez des caractères, `Invoke-History` correspond d’abord aux commandes les plus récentes. Si vous omettez ce paramètre, `Invoke-History` exécute la dernière commande, ou la plus récente. Pour rechercher le numéro d' **identification** d’une commande, utilisez l’applet de commande `Get-History` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
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

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

Vous pouvez diriger un **ID** d’historique vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne génère pas de sortie, mais la sortie peut être générée par les commandes qui `Invoke-History` s’exécutent.

## REMARQUES

L'historique de session est une liste des commandes entrées pendant la session. L'historique de session représente l'ordre d'exécution, l'état et les heures de début et de fin de la commande. Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser. Pour plus d’informations sur l’historique de session, consultez [about_History](About/about_History.md).

Vous pouvez également faire référence à `Invoke-History` par ses alias intégrés `r` et `ihy` . Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).

## LIENS CONNEXES

[Add-History](Add-History.md)

[Clear-History](Clear-History.md)

[Get-History](Get-History.md)
