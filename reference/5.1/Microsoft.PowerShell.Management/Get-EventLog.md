---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204021"
---
# Get-EventLog

## SYNOPSIS
Obtient les événements dans un journal des événements ou une liste des journaux des événements sur l’ordinateur local ou les ordinateurs distants.

## SYNTAX

### LogName (par défaut)

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### List

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## Description

L' `Get-EventLog` applet de commande obtient les événements et les journaux des événements à partir des ordinateurs locaux et distants. Par défaut, `Get-EventLog` obtient les journaux à partir de l’ordinateur local. Pour récupérer des journaux à partir d’ordinateurs distants, utilisez le paramètre **ComputerName** .

Vous pouvez utiliser les `Get-EventLog` paramètres et les valeurs de propriété pour rechercher des événements. L’applet de commande obtient les événements qui correspondent aux valeurs de propriétés spécifiées.

Les applets de commande PowerShell qui contiennent le `EventLog` nom fonctionnent uniquement sur les journaux des événements Windows classiques, tels que l’application, le système ou la sécurité. Pour récupérer les journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures de Windows, utilisez `Get-WinEvent` .

> [!NOTE]
> `Get-EventLog` utilise une API Win32 déconseillée. Les résultats peuvent ne pas être précis. Utilisez plutôt l’applet de commande `Get-WinEvent` .

## EXEMPLES

### Exemple 1 : récupérer les journaux des événements sur l’ordinateur local

Cet exemple affiche la liste des journaux des événements disponibles sur l’ordinateur local. Les noms de la colonne log sont utilisés avec le paramètre **logname** pour spécifier le journal dans lequel les événements sont recherchés.

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

L' `Get-EventLog` applet de commande utilise le paramètre **List** pour afficher les journaux disponibles.

### Exemple 2 : récupérer les entrées récentes à partir d’un journal des événements sur l’ordinateur local

Cet exemple obtient les entrées récentes du journal des événements système.

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements système. Le paramètre le plus **récent** retourne les cinq événements les plus récents.

### Exemple 3 : Rechercher toutes les sources pour un nombre spécifique d’entrées dans un journal des événements

Cet exemple montre comment rechercher toutes les sources incluses dans les 1000 entrées les plus récentes dans le journal des événements système.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système. Le paramètre le plus **récent** sélectionne les événements les plus récents 1000. Les objets d’événement sont stockés dans la `$Events` variable. Les `$Events` objets sont envoyés dans le pipeline à l’applet de commande `Group-Object` .
`Group-Object` utilise le paramètre **Property** pour regrouper les objets par source et compte le nombre d’objets pour chaque source. Le paramètre **NoElement** supprime les membres du groupe de la sortie.
L' `Sort-Object` applet de commande utilise le paramètre **Property** pour effectuer un tri selon le nombre de chaque nom de source.
Le paramètre **décroissant** trie la liste dans l’ordre par nombre de la plus élevée à la plus faible.

### Exemple 4 : obtenir des événements d’erreur à partir d’un journal des événements spécifique

Cet exemple obtient les événements d’erreur du journal des événements système.

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système. Le paramètre **entryType** filtre les événements pour afficher uniquement les événements d’erreur.

### Exemple 5 : récupérer des événements à partir d’un journal des événements avec un InstanceId et une valeur source

Cet exemple obtient les événements du journal système pour un InstanceId et une source spécifiques.

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système. Le paramètre **InstanceID** sélectionne les événements avec l’ID d’instance spécifié. Le paramètre **source** spécifie la propriété de l’événement.

### Exemple 6 : récupération d’événements à partir de plusieurs ordinateurs

Cette commande obtient les événements du journal des événements système sur trois ordinateurs : Serveur01, Server02 et Server03.

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système. Le paramètre **ComputerName** utilise une chaîne séparée par des virgules pour répertorier les ordinateurs à partir desquels vous souhaitez obtenir les journaux des événements.

### Exemple 7 : obtenir tous les événements qui incluent un mot spécifique dans le message

Cette commande obtient tous les événements du journal des événements système qui contiennent un mot spécifique dans le message de l’événement. Il est possible que la valeur de votre paramètre de **message** spécifié soit incluse dans le contenu du message, mais ne s’affiche pas sur la console PowerShell.

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements système. Le paramètre **message** spécifie un mot à rechercher dans le champ message de chaque événement.

### Exemple 8 : afficher les valeurs de propriété d’un événement

Cet exemple montre comment afficher toutes les propriétés et valeurs d’un événement.

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements système. Le paramètre le plus **récent** sélectionne l’objet événement le plus récent. L’objet est stocké dans la `$A` variable. L’objet dans la `$A` variable est envoyé dans le pipeline à l’applet de commande `Select-Object` .
`Select-Object` utilise le paramètre **Property** avec un astérisque ( `*` ) pour sélectionner toutes les propriétés de l’objet.

### Exemple 9 : obtenir des événements à partir d’un journal des événements à l’aide d’un ID de source et d’événement

Cet exemple obtient les événements d’une source et d’un ID d’événement spécifiés.

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements de l’application. Le paramètre **source** spécifie le nom de l’application, Outlook. Les objets sont envoyés dans le pipeline à l’applet de commande `Where-Object` . Pour chaque objet dans le pipeline, l’applet de commande `Where-Object` utilise la variable `$_.EventID` pour comparer la propriété de l’ID d’événement à la valeur spécifiée. Les objets sont envoyés dans le pipeline à l’applet de commande `Select-Object` . `Select-Object` utilise le paramètre **Property** pour sélectionner les propriétés à afficher dans la console PowerShell.

### Exemple 10 : obtenir des événements et les regrouper par une propriété

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système. Le paramètre **username** comprend le `*` caractère générique astérisque () pour spécifier une partie du nom d’utilisateur. Les objets d’événement sont envoyés dans le pipeline à l’applet de commande `Group-Object` . `Group-Object` utilise le paramètre **Property** pour spécifier que la propriété **username** est utilisée pour regrouper les objets et compter le nombre d’objets pour chaque nom d’utilisateur. Le paramètre **NoElement** supprime les membres du groupe de la sortie. Les objets sont envoyés dans le pipeline à l’applet de commande `Select-Object` .
`Select-Object` utilise le paramètre **Property** pour sélectionner les propriétés à afficher dans la console PowerShell.

### Exemple 11 : obtenir des événements qui se sont produits pendant une plage de dates et d’heures spécifique

Cet exemple obtient les événements d’erreur du journal des événements système pour une plage de dates et d’heures spécifiée. Les paramètres **Before** et **after** définissent la plage de dates et d’heures, mais sont exclus de la sortie.

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

L' `Get-Date` applet de commande utilise le paramètre **Date** pour spécifier une date et une heure. Les objets **DateTime** sont stockés dans les `$Begin` `$End` variables et. L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système. Le paramètre **entryType** spécifie le type d’événement d’erreur. La plage de dates et d’heures est définie par le paramètre **after** et `$Begin` la variable, ainsi que par la variable et le paramètre **Before** `$End` .

## PARAMETERS

### -Après

Obtient les événements qui se sont produits après une date et une heure spécifiées. La date et l’heure du paramètre **after** sont exclues de la sortie. Entrez un objet **DateTime** , tel que la valeur retournée par l’applet de commande `Get-Date` .

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsBaseObject

Indique que cette applet de commande retourne un objet **System. Diagnostics. EventLogEntry** standard pour chaque événement. Sans ce paramètre, `Get-EventLog` retourne un objet **PSObject** étendu avec des propriétés **EventLogName** , **source** et **InstanceID** supplémentaires.

Pour voir l’effet de ce paramètre, dirigez les événements vers l’applet de commande `Get-Member` et examinez la valeur **TypeName** dans le résultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

Indique que cette applet de commande retourne la sortie sous forme de chaînes, au lieu d’objets.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Avant

Obtient les événements qui se sont produits avant une date et une heure spécifiées. La date et l’heure du paramètre **Before** sont exclues de la sortie. Entrez un objet **DateTime** , tel que la valeur retournée par l’applet de commande `Get-Date` .

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Ce paramètre spécifie le nom NetBIOS de l’ordinateur distant, l’adresse IP (Internet Protocol) ou un nom de domaine complet (FQDN).

Si le paramètre **ComputerName** n’est pas spécifié, `Get-EventLog` l’ordinateur local est utilisé par défaut. Le paramètre accepte également un point ( `.` ) pour spécifier l’ordinateur local.

Le paramètre **ComputerName** ne repose pas sur la communication à distance Windows PowerShell. Vous pouvez utiliser `Get-EventLog` avec le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EntryType

Spécifie, sous forme de tableau de chaînes, le type d’entrée des événements que cette applet de commande obtient.

Les valeurs valides pour ce paramètre sont :

- Erreur
- Information
- FailureAudit
- SuccessAudit
- Avertissement

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

Spécifie les valeurs d’index à extraire du journal des événements. Le paramètre accepte une chaîne de valeurs séparées par des virgules.

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Spécifie les ID d’instance à récupérer à partir du journal des événements. Le paramètre accepte une chaîne de valeurs séparées par des virgules.

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -List

Affiche la liste des journaux des événements sur l’ordinateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

Spécifie le nom d’un journal des événements. Pour rechercher les noms de journaux `Get-EventLog -List` , utilisez. Les caractères génériques sont autorisés. Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Message

Spécifie une chaîne dans le message de l’événement. Vous pouvez utiliser ce paramètre pour rechercher des messages qui contiennent certains mots ou certaines expressions. Les caractères génériques sont autorisés.

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Plus récent

Commence par les événements les plus récents et obtient le nombre d’événements spécifié. Le nombre d’événements est requis, par exemple `-Newest 100` . Spécifie le nombre maximal d’événements qui sont retournés.

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Spécifie, sous forme de tableau de chaînes, les sources qui ont été écrites dans le journal que cette applet de commande obtient. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -UserName

Spécifie, sous forme de tableau de chaînes, les noms d’utilisateur associés à des événements. Entrez des noms ou des modèles de nom, tels que `User01` , `User*` ou `Domain01\User*` . Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’entrée vers `Get-EventLog` .

## SORTIES

### System. Diagnostics. EventLogEntry. System. Diagnostics. EventLog. System.String

Si le paramètre **logname** est spécifié, la sortie est une collection d’objets **System. Diagnostics. EventLogEntry** .

Si seul le paramètre **List** est spécifié, la sortie est une collection d’objets **System. Diagnostics. EventLog** .

Si les paramètres **List** et **AsString** sont tous les deux spécifiés, la sortie est une collection d’objets **System. String** .

## REMARQUES

Les applets de commande `Get-EventLog` et ne `Get-WinEvent` sont pas prises en charge dans le environnement de préinstallation Windows (WinPE) (Windows PE).

## LIENS CONNEXES

[Clear-EventLog](Clear-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
