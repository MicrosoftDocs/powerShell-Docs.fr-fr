---
external help file: Restore-DSCConfiguration.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/restore-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-DscConfiguration
ms.openlocfilehash: 823032f7665d9ec83faa59c37560510e049efdd2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203934"
---
# Restore-DscConfiguration

## SYNOPSIS
Réapplique la configuration précédente pour le nœud.

## SYNTAX

```
Restore-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description
L’applet de commande **Restore-DscConfiguration** réapplique la configuration précédente pour le nœud, si une configuration précédente existe.
Spécifiez les ordinateurs à l'aide de sessions CIM (Common Information Model).
Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande restaure la configuration de l'ordinateur local.
S’il n’existe pas de configuration précédente pour un nœud particulier, cette applet de commande retourne un message d’erreur.

Cette applet de commande ne prend pas en charge le paramètre **Confirm** .

## EXEMPLES

### Exemple 1 : restaurer la configuration de l’ordinateur local

```
PS C:\> Restore-DscConfiguration
```

Cette commande restaure la configuration de l'ordinateur local.

### Exemple 2 : restaurer la configuration d’un ordinateur spécifié

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Restore-DscConfiguration -CimSession $Session
```

Cet exemple restaure la configuration d'un ordinateur spécifié par une session CIM.
L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.
Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.

La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable $Session.
La commande vous invite à entrer un mot de passe.
Pour plus d'informations, voir `Get-Help New-CimSession`.

La deuxième commande restaure la configuration des ordinateurs identifiés par les objets **CimSession** stockés dans la variable $Session (dans ce cas, l'ordinateur nommé Server01).

## PARAMETERS

### -AsJob
Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.

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

### -CimSession
Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.
Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande **New-CimSession** ou **CimSession** .

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.

```yaml
Type: System.Int32
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

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
