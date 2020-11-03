---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: eb20101fda394b97fc6470e32a8a70665101471b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201633"
---
# Enter-PSHostProcess

## SYNOPSIS
Se connecte à et entre dans une session interactive avec un processus local.

## SYNTAX

### ProcessIdParameterSet (par défaut)

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessParameterSet

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessNameParameterSet

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### PSHostProcessInfoParameterSet

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### PipeNameParameterSet

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## Description

L' `Enter-PSHostProcess` applet de commande se connecte à et entre dans une session interactive avec un processus local. À compter de PowerShell 6,2, cette applet de commande est prise en charge sur les plateformes non-Windows.

Au lieu de créer un nouveau processus pour héberger PowerShell et exécuter une session à distance, la session distante interactive est exécutée dans un processus existant qui exécute déjà PowerShell. Quand vous interagissez avec une session à distance sur un processus spécifié, vous pouvez énumérer les instances d’exécution en cours d’exécution, puis sélectionner une instance d’exécution à déboguer en exécutant `Debug-Runspace` ou `Enable-RunspaceDebug` .

Le processus que vous souhaitez entrer doit héberger PowerShell (System.Management.Automation.dll).
Vous devez être membre du groupe Administrateurs sur l’ordinateur sur lequel le processus est trouvé, ou vous devez être l’utilisateur qui exécute le script qui a démarré le processus.

Une fois que vous avez sélectionné une instance d’exécution à déboguer, une session de débogage à distance est ouverte pour l’instance d’exécution si elle exécute actuellement une commande ou s’il est arrêté dans le débogueur. Vous pouvez ensuite déboguer le script de l’instance d’exécution de la même façon que vous le feriez pour d’autres scripts de session à distance.

Détachez d’une session de débogage, puis la session interactive avec le processus, en exécutant deux fois exit ou arrêtez l’exécution du script en exécutant la commande du débogueur Quit existant.

Si vous spécifiez un processus à l’aide du paramètre **Name** et qu’un seul processus est trouvé avec le nom spécifié, le processus est entré. Si plusieurs processus portant le nom spécifié sont trouvés, PowerShell retourne une erreur et répertorie tous les processus trouvés avec le nom spécifié.

Pour prendre en charge l’attachement à des processus sur des ordinateurs distants, l' `Enter-PSHostProcess` applet de commande est activée sur un ordinateur distant spécifié, ce qui vous permet d’attacher un processus local dans une session PowerShell distante.

## EXEMPLES

### Exemple 1 : démarrer le débogage d’une instance d’exécution dans le processus PowerShell ISE

Dans cet exemple, vous exécutez `Enter-PSHostProcess` à partir de la console PowerShell pour entrer dans le processus PowerShell ISE. Dans la session interactive obtenue, vous pouvez trouver une instance d’exécution que vous souhaitez déboguer en exécutant `Get-Runspace` , puis déboguer l’instance d’exécution.

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## PARAMETERS

### -AppDomainName

Spécifie un nom de domaine d’application auquel se connecter en cas d’omission, utilise **DefaultAppDomain** . Utilisez `Get-PSHostProcessInfo` pour afficher les noms de domaine d’application.

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostProcessInfo

Spécifie un objet **PSHostProcessInfo** qui peut être connecté à avec PowerShell. Utilisez `Get-PSHostProcessInfo` pour récupérer l’objet.

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

Spécifie un processus par l’ID de processus. Pour obtenir un ID de processus, exécutez l’applet de commande `Get-Process` .

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un processus par le nom du processus. Pour obtenir un nom de processus, exécutez l’applet de commande `Get-Process` . Vous pouvez également obtenir des noms de processus à partir de la boîte de dialogue Propriétés d’un processus dans le gestionnaire des tâches.

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Processus

Spécifie un processus par l’objet processus. La façon la plus simple d’utiliser ce paramètre consiste à enregistrer les résultats d’une `Get-Process` commande qui retourne le processus que vous souhaitez entrer dans une variable, puis à spécifier la variable comme valeur de ce paramètre.

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CustomPipeName

Obtient ou définit le nom de canal nommé personnalisé auquel se connecter. Cela est généralement utilisé conjointement avec `pwsh -CustomPipeName` .

Ce paramètre a été introduit dans PowerShell 6,2.

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Diagnostics.Process

## SORTIES

## REMARQUES

`Enter-PSHostProcess` Impossible d’entrer dans le processus de la session PowerShell dans laquelle vous exécutez la commande. Toutefois, vous pouvez entrer le processus d’une autre session PowerShell ou une session PowerShell ISE qui s’exécute en même temps que la session dans laquelle vous exécutez `Enter-PSHostProcess` .

`Enter-PSHostProcess` peut entrer uniquement les processus qui hébergent PowerShell. Autrement dit, ils ont chargé le moteur PowerShell.

Pour quitter un processus au sein du processus, tapez **Exit** , puis appuyez sur <kbd>entrée</kbd>.

## LIENS CONNEXES

[Exit-PSHostProcess](Exit-PSHostProcess.md)

[Get-PSHostProcessInfo](Get-PSHostProcessInfo.md)
