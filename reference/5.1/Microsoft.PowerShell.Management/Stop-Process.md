---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 4efa22e8f2a7339e381d92270c1b127054c219cb
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "93206289"
---
# Stop-Process

## SYNOPSIS
Arrête un ou plusieurs processus en cours d'exécution.

## SYNTAX

### ID (par défaut)

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Nom

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L’applet de commande **Stop-Process** arrête un ou plusieurs processus en cours d’exécution.
Vous pouvez spécifier un processus par nom de processus ou ID de processus (PID), ou passer un objet processus à **Stop-Process** .
**Stop-Process** fonctionne uniquement sur les processus qui s’exécutent sur l’ordinateur local.

Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, pour arrêter un processus qui n’appartient pas à l’utilisateur actuel, vous devez démarrer PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.
En outre, vous n’êtes pas invité à confirmer la demande, sauf si vous spécifiez le paramètre *Confirm* .

## EXEMPLES

### Exemple 1 : arrêter toutes les instances d’un processus

```
PS C:\> Stop-Process -Name "notepad"
```

Cette commande arrête toutes les instances du processus Notepad (Bloc-notes) sur l’ordinateur
Chaque instance du bloc-notes s’exécute dans son propre processus.
Elle utilise le paramètre *Name* pour spécifier les processus, qui ont tous le même nom.
Si vous utilisez le paramètre *ID* pour arrêter les mêmes processus, vous devez répertorier les ID de processus de chaque instance du bloc-notes.

### Exemple 2 : arrêter une instance spécifique d’un processus

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

Cette commande arrête une instance particulière du processus Notepad.
Elle utilise l’ID de processus 3952 pour identifier le processus.
Le paramètre *Confirm* indique à PowerShell qu’il vous invite à arrêter le processus.
Étant donné que l’invite comprend le nom du processus en plus de son ID, c’est la meilleure pratique.
Le paramètre *PassThru* passe l’objet processus au formateur pour l’affichage.
Sans ce paramètre, il n’y aurait aucun affichage après une commande **Stop-Process** .

### Exemple 3 : arrêter un processus et détecter qu’il s’est arrêté

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

Cette série de commandes démarre et arrête le processus Calc, puis détecte les processus qui se sont arrêtés.

La première commande démarre une instance de la calculatrice.

La deuxième commande utilise la méthode d' **extraction** de données obtient un objet qui représente le processus Calc, puis le stocke dans la variable $p.

La troisième commande arrête le processus Calc.
Elle utilise le paramètre *InputObject* pour passer l’objet à **Stop-Process** .

La dernière commande obtient tous les processus qui étaient en cours d’exécution sur l’ordinateur mais qui sont maintenant arrêtés.
Elle utilise la **méthode « Process-process »** pour récupérer tous les processus sur l’ordinateur.
L’opérateur de pipeline (|) passe les résultats à l’applet de commande Where-Object, qui sélectionne ceux pour lesquels la valeur de la propriété **HasExited** est $true.
**HasExited** n’est qu’une des propriétés des objets Process.
Pour rechercher toutes les propriétés, tapez `Get-Process | Get-Member` .

### Exemple 4 : arrêter un processus qui n’appartient pas à l’utilisateur actuel

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

Ces commandes montrent l’effet de l’utilisation de *force* pour arrêter un processus qui n’appartient pas à l’utilisateur.

La première commande utilise la méthode **« Process-process »** pour récupérer le processus Lsass.
Un opérateur de pipeline envoie le processus à **Stop-Process** pour l’arrêter.
Comme indiqué dans l’exemple de sortie, la première commande échoue avec un message d’accès refusé, car ce processus ne peut être arrêté que par un membre du groupe Administrateurs sur l’ordinateur.

Lorsque PowerShell est ouvert à l’aide de l’option Exécuter en tant qu’administrateur et que la commande est répétée, PowerShell vous invite à confirmer l’exécution.

La deuxième commande spécifie *force* pour supprimer l’invite.
Le processus est alors arrêté sans confirmation.

## PARAMETERS

### -Force

Arrête les processus spécifiés sans inviter à confirmer l’opération.
Par défaut, **Stop-Process** vous invite à confirmer l’opération avant d’arrêter tout processus qui n’appartient pas à l’utilisateur actuel.

Pour rechercher le propriétaire d’un processus, utilisez l' `Get-CimInstance` applet de commande pour obtenir un objet **Win32_Process** qui représente le processus, puis utilisez la méthode **GetOwner** de l’objet.

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

### -Id

Spécifie les ID de processus à arrêter.
Lorsque vous spécifiez plusieurs identificateurs, séparez-les à l'aide de virgules.
Pour rechercher le PID d’un processus, tapez `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets de processus à arrêter.
Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des processus à arrêter.
Vous pouvez taper plusieurs noms de processus, en les séparant par des virgules, ou utiliser des caractères génériques.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Retourne un objet qui représente le processus.
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

### System.Diagnostics.Process

Vous pouvez diriger un objet processus vers cette applet de commande.

## SORTIES

### Aucun, System. Diagnostics. Process

Cette applet de commande retourne un objet **System. Diagnostics. Process** qui représente le processus arrêté, si vous spécifiez le paramètre *PassThru* .
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* Vous pouvez également faire référence à **Stop-Process** par ses alias intégrés, **Kill** et **SPPS** . Pour plus d'informations, consultez about_Aliases.

  Vous pouvez également utiliser les propriétés et les méthodes de l’objet **Win32_Process** Windows Management Instrumentation (WMI) dans Windows PowerShell.
Pour plus d’informations, consultez `Get-CimInstance` et le kit de développement logiciel (SDK) WMI.

* Lorsque vous arrêtez des processus, sachez que l’arrêt d’un processus peut arrêter les processus et les services qui dépendent du processus.
Dans certains cas extrêmes, l’arrêt d’un processus peut entraîner l’arrêt de Windows.

## LIENS CONNEXES

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
