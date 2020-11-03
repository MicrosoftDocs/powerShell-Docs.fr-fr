---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203965"
---
# Get-DscConfiguration

## SYNOPSIS
Obtient la configuration actuelle des nœuds.

## SYNTAX

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-DscConfiguration** obtient la configuration actuelle des nœuds, si la configuration existe.
Spécifiez les ordinateurs à l'aide de sessions CIM (Common Information Model).
Si vous ne spécifiez pas d'ordinateur cible, l'applet de commande obtient la configuration de l'ordinateur local.

## EXEMPLES

### Exemple 1 : obtenir la configuration de l’ordinateur local

```
PS C:\> Get-DscConfiguration
```

Cette commande obtient l’état actuel de l’ordinateur local.

### Exemple 2 : obtenir la configuration d’un ordinateur spécifié

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

Cet exemple obtient l’état actuel à partir d’un ordinateur spécifié par une session CIM.
L'exemple crée une session CIM pour un ordinateur nommé Server01 à utiliser avec l'applet de commande.
Vous pouvez aussi créer un tableau de sessions CIM pour appliquer l'applet de commande à plusieurs ordinateurs spécifiés.

La première commande crée une session CIM à l'aide de l'applet de commande **New-CimSession** , puis stocke l'objet **CimSession** dans la variable **$Session** .
La commande vous invite à entrer un mot de passe.
Pour plus d'informations, voir `Get-Help New-CimSession`.

La deuxième commande obtient la configuration actuelle des ordinateurs identifiés par les objets **CimSession** stockés dans la variable **$Session** (dans ce cas, l'ordinateur nommé Server01).

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
Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .
La valeur par défaut est la session active sur l’ordinateur local.

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
Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.
Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.

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

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
