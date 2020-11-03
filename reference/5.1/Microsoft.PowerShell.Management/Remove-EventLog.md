---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203565"
---
# Remove-EventLog

## SYNOPSIS
Supprime un journal des événements ou annule l'inscription d'une source d'événement.

## SYNTAX

### Valeur par défaut (par défaut)

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Source

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Remove-EventLog** supprime un fichier journal des événements d’un ordinateur local ou distant et annule l’inscription de toutes ses sources d’événement pour le journal.
Vous pouvez également utiliser cette applet de commande pour annuler l’inscription des sources d’événement sans supprimer de journaux des événements.

Les applets de commande qui contiennent le nom **EventLog** , les applets de commande **EventLog** , fonctionnent uniquement sur les journaux des événements classiques.
Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures du système d’exploitation Windows, utilisez la WinEvent.

ATTENTION : cette applet de commande peut supprimer les journaux des événements du système d’exploitation, ce qui peut entraîner des échecs d’application et un comportement inattendu du système.

## EXEMPLES

### Exemple 1 : supprimer un journal des événements de l’ordinateur local

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

Cette commande supprime le journal des événements MyLog de l’ordinateur local et annule l’inscription de ses sources d’événement.

### Exemple 2 : supprimer un journal des événements de plusieurs ordinateurs

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

Cette commande supprime les journaux des événements MyLog et TestLog de l’ordinateur local et des ordinateurs distants SERVEUR01 et Server02.
La commande annule également l’inscription des sources d’événement de ces journaux.

### Exemple 3 : supprimer une source d’événement

```
PS C:\> Remove-EventLog -Source "MyApp"
```

Cette commande supprime la source d’événement MyApp des journaux sur l’ordinateur local.
Une fois la commande terminée, le programme MyApp ne peut pas écrire dans les journaux des événements.

### Exemple 4 : supprimer un journal des événements et confirmer l’action

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

Ces commandes montrent comment répertorier les journaux des événements sur un ordinateur et vérifier qu’une commande **Remove-EventLog** a réussi.

### Exemple 5 : supprimer une source d’événement et confirmer l’action

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

Ces commandes utilisent l’applet de commande Get-WmiObject pour répertorier les sources d’événement présentes sur l’ordinateur local.
Vous pouvez utiliser ces commandes pour vérifier la réussite d’une commande ou pour supprimer une source d’événement.

La première commande obtient les sources d’événement du journal des événements TestLog présent sur l’ordinateur local.
MyApp fait partie de ces sources.

La deuxième commande utilise le paramètre *source* de **Remove-EventLog** pour supprimer la source d’événement MyApp.

La troisième commande est identique à la première.
Elle indique que la source d’événement MyApp a été supprimée.

## PARAMETERS

### -ComputerName
Spécifie un ordinateur distant.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.
Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.
Vous pouvez utiliser le paramètre *ComputerName* de **Remove-EventLog** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
Spécifie les journaux des événements.
Entrez le nom du journal d’un ou plusieurs journaux des événements, en les séparant par des virgules.
Le nom du journal est la valeur de la propriété **log** , et non *et non LogDisplayName* , les caractères génériques ne sont pas autorisés.
Ce paramètre est obligatoire.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
Spécifie les sources d’événements que cette applet de commande annule.
Entrez les noms des sources, et non le nom de l’exécutable, en les séparant par des virgules.

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

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

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne retourne aucune sortie.

## REMARQUES

* Pour utiliser **Remove-EventLog** sur Windows Vista et les versions ultérieures du système d’exploitation Windows, démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.

  Si vous supprimez un journal des événements et que vous recréez le journal par la suite, vous ne pourrez pas inscrire les mêmes sources d’événement.
Les applications qui ont utilisé les sources d’événement pour écrire des entrées dans le journal d’origine ne pourront rien écrire dans le nouveau journal.

* Lorsque vous annulez l’inscription d’une source d’événement d’un journal particulier, vous pouvez empêcher la source d’événement d’écrire des entrées dans d’autres journaux des événements.

## LIENS CONNEXES

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
