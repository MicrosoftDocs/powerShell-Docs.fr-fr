---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 96282d28249f28744cf7dff436fa2e6c601c10ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204674"
---
# Debug-Runspace

## SYNOPSIS
Démarre une session de débogage interactive avec une instance d’exécution.

## SYNTAX

### RunspaceParameterSet (par défaut)

```
Debug-Runspace [-Runspace] <Runspace> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Debug-Runspace [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### IdParameterSet

```
Debug-Runspace [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Debug-Runspace [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Debug-Runspace` applet de commande démarre une session de débogage interactive avec une instance d’exécution active locale ou distante. Vous pouvez trouver une instance d’exécution que vous souhaitez déboguer en exécutant en premier `Get-Process` pour rechercher les processus associés à PowerShell, puis `Enter-PSHostProcess` l’ID de processus spécifié dans le paramètre **ID** pour l’attacher au processus, puis `Get-Runspace` répertorier les instances d’exécution dans le processus hôte PowerShell.

Après avoir sélectionné une instance d’exécution à déboguer, si l’instance d’exécution exécute actuellement une commande ou un script, ou si le script s’est arrêté à un point d’arrêt, PowerShell ouvre une session du débogueur distant pour l’instance d’exécution. Vous pouvez déboguer le script de l’instance d’exécution de la même façon que les scripts de session à distance sont débogués.

Vous pouvez uniquement effectuer un attachement à un processus hôte PowerShell Si vous êtes un administrateur sur l’ordinateur qui exécute le processus, ou si vous exécutez le script que vous souhaitez déboguer. En outre, vous ne pouvez pas entrer dans le processus hôte qui exécute la session PowerShell active. Vous pouvez uniquement entrer un processus hôte qui exécute une autre session PowerShell.

## EXEMPLES

### Exemple 1 : déboguer une instance d’exécution distante

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

Dans cet exemple, vous déboguez une instance d’exécution qui est ouverte sur un ordinateur distant, WS10TestServer. Sur la première ligne de la commande, vous exécutez `Get-Process` sur l’ordinateur distant et filtrez les processus de l’hôte Windows PowerShell. Dans cet exemple, vous souhaitez déboguer le processus ID 1152, le processus hôte Windows PowerShell ISE.

Dans la deuxième commande, vous exécutez `Enter-PSSession` pour ouvrir une session à distance sur WS10TestServer. Dans la troisième commande, vous attachez au processus hôte Windows PowerShell ISE s’exécutant sur le serveur distant en exécutant `Enter-PSHostProcess` et en spécifiant l’ID du processus hôte que vous avez obtenu dans la première commande, 1152.

Dans la quatrième commande, vous répertoriez les instances d’exécution disponibles pour l’ID de processus 1152 en exécutant `Get-Runspace` .
Vous notez le numéro d’ID de l’instance d’exécution occupée ; Il exécute un script que vous souhaitez déboguer.

Dans la dernière commande, vous démarrez le débogage d’une instance d’exécution ouverte qui exécute un script, TestWFVar1.ps1, en exécutant `Debug-Runspace` et en identifiant l’instance d’exécution par son ID, 2, en ajoutant le paramètre **ID** . Étant donné qu’il y a un point d’arrêt dans le script, le débogueur s’ouvre.

## PARAMETERS

### -Id

Spécifie le numéro d’ID d’une instance d’exécution. Vous pouvez exécuter `Get-Runspace` pour afficher les ID d’instance d’exécution.

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Spécifie une instance d’exécution par son ID d’instance, un GUID que vous pouvez afficher en exécutant `Get-Runspace` .

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie une instance d’exécution par son nom. Vous pouvez exécuter `Get-Runspace` pour afficher les noms de instances d’exécution.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Instance d’exécution

Spécifie un objet d’instance d’exécution. La façon la plus simple de fournir une valeur pour ce paramètre consiste à spécifier une variable qui contient les résultats d’une commande filtrée `Get-Runspace` .

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
Default value: True
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
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. instances d’exécution. Runspace

Vous pouvez diriger les résultats d’une `Get-Runspace` commande vers **Debug-Runspace.**

## SORTIES

## REMARQUES

`Debug-Runspace` fonctionne sur les instances d’exécution qui sont à l’état ouvert. Si l’état d’une instance d’exécution passe de ouvert à un autre État, cette instance d’exécution est automatiquement supprimée de la liste en cours d’exécution. Une instance d’exécution est ajoutée à la liste en cours d’exécution uniquement si elle répond aux critères suivants.

- S’il provient de Invoke-Command ; autrement dit, il a un `Invoke-Command` ID de GUID.
- S’il provient de `Debug-Runspace` ; autrement dit, il a un `Debug-Runspace` ID de GUID.
- S’il provient d’un workflow PowerShell et que son ID de tâche de flux de travail est le même que l’ID de tâche de workflow du débogueur actif actuel.

## LIENS CONNEXES

[about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[Debug-Job](../Microsoft.PowerShell.Core/Debug-Job.md)

[Get-Runspace](Get-Runspace.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

[Enter-PSHostProcess](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[Enter-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)
