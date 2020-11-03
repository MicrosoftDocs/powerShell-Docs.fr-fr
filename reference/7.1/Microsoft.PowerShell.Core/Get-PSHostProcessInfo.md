---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 655cc02e10bdb11092412271c16a002ab89089c3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205133"
---
# Get-PSHostProcessInfo

## SYNOPSIS
Obtient des informations sur le traitement de l’hôte PowerShell.

## SYNTAX

### ProcessNameParameterSet (par défaut)

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### ProcessParameterSet

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### ProcessIdParameterSet

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## Description

L' `Get-PSHostProcessInfo` applet de commande obtient des informations sur les processus hôtes PowerShell en cours d’exécution sur l’ordinateur local.

À compter de PowerShell 6,2, cette applet de commande est prise en charge sur les plateformes non-Windows.

## EXEMPLES

### 1 : obtenir la liste des hôtes PowerShell en cours d’exécution sur le système

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### 2 : obtenir les informations de l’hôte PowerShell pour un nom de processus spécifique

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## PARAMETERS

### -Id

Spécifie un processus par l’ID de processus. Pour obtenir un ID de processus, exécutez l’applet de commande `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un processus par le nom du processus. Pour obtenir un nom de processus, exécutez l’applet de commande `Get-Process` .

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Processus

Spécifie un processus par l’objet processus. La façon la plus simple d’utiliser ce paramètre consiste à enregistrer les résultats d’une `Get-Process` commande qui retourne le processus que vous souhaitez entrer dans une variable, puis à spécifier la variable comme valeur de ce paramètre.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Diagnostics.Process

Vous pouvez diriger un objet **processus** de `Get-Process` vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. PSHostProcessInfo

## REMARQUES

## LIENS CONNEXES

[Get-Process](../Microsoft.PowerShell.Management/get-process.md)

