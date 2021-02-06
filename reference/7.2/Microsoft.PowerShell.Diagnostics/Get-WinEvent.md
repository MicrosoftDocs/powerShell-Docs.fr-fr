---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-winevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WinEvent
ms.openlocfilehash: 742ef9b19294b93be9a2b7dce58bad913d8fd27b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596528"
---
# Get-WinEvent

## SYNOPSIS
Obtient les événements à partir des journaux des événements et des fichiers journaux de suivi d'événements sur les ordinateurs locaux et distants.

## SYNTAXE

### GetLogSet (par défaut)

```
Get-WinEvent [[-LogName] <String[]>] [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### ListLogSet

```
Get-WinEvent [-ListLog] <String[]> [-ComputerName <String>] [-Credential <PSCredential>] [-Force]
 [<CommonParameters>]
```

### ListProviderSet

```
Get-WinEvent [-ListProvider] <String[]> [-ComputerName <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### GetProviderSet

```
Get-WinEvent [-ProviderName] <String[]> [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### AUT

```
Get-WinEvent [-Path] <String[]> [-MaxEvents <Int64>] [-Credential <PSCredential>]
 [-FilterXPath <String>] [-Oldest] [<CommonParameters>]
```

### HashQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterHashtable] <Hashtable[]> [-Force] [-Oldest] [<CommonParameters>]
```

### XmlQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterXml] <XmlDocument> [-Oldest] [<CommonParameters>]
```

## Description

L' `Get-WinEvent` applet de commande obtient les événements des journaux des événements, y compris les journaux classiques, tels que les journaux **système** et d' **application** . L’applet de commande obtient les données des journaux des événements qui sont générés par la technologie du journal des événements Windows introduite dans Windows Vista. Et les événements des fichiers journaux générés par **suivi d’v nements pour Windows (ETW)**. Par défaut, `Get-WinEvent` retourne les informations d’événement dans l’ordre le plus récent au plus ancien.

`Get-WinEvent` répertorie les journaux des événements et les fournisseurs de journaux d’événements. Pour interrompre la commande, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>. Vous pouvez obtenir les événements à partir des journaux sélectionnés ou des journaux générés par les fournisseurs d'événements sélectionnés. En outre, vous pouvez combiner des événements provenant de plusieurs sources dans une seule commande.
`Get-WinEvent` permet de filtrer les événements à l’aide de requêtes XPath, de requêtes XML structurées et de requêtes de table de hachage.

Si vous n’exécutez pas PowerShell en tant qu’administrateur, vous pouvez voir des messages d’erreur indiquant que vous ne pouvez pas récupérer d’informations sur un journal.

## EXEMPLES

### Exemple 1 : obtenir tous les journaux d’un ordinateur local

Cette commande obtient tous les journaux des événements sur l’ordinateur local. Les journaux sont répertoriés dans l’ordre dans lequel ils sont affichés `Get-WinEvent` . Les journaux classiques sont extraits en premier, suivis des nouveaux journaux des événements Windows.
Il est possible que la valeur **RecordCount** d’un journal soit null, ce qui est vide ou zéro.

```powershell
Get-WinEvent -ListLog *
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14500 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        3015 CxAudioSvcLog
Circular            20971520             ForwardedEvents
Circular            20971520           0 HardwareEvents
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **ListLog** utilise le `*` caractère générique astérisque () pour afficher des informations sur chaque journal.

### Exemple 2 : récupérer le journal d’installation classique

Cette commande obtient un objet **EventLogConfiguration** qui représente le journal **d’installation** classique. L’objet comprend des informations sur le journal, telles que la taille du fichier, le fournisseur, le chemin d’accès au fichier et si le journal est activé.

```powershell
Get-WinEvent -ListLog Setup | Format-List -Property *
```

```Output
FileSize                       : 69632
IsLogFull                      : False
LastAccessTime                 : 3/13/2019 09:41:46
LastWriteTime                  : 3/13/2019 09:41:46
OldestRecordNumber             : 1
RecordCount                    : 23
LogName                        : Setup
LogType                        : Operational
LogIsolation                   : Application
IsEnabled                      : True
IsClassicLog                   : False
SecurityDescriptor             : O:BAG:SYD: ...
LogFilePath                    : %SystemRoot%\System32\Winevt\Logs\Setup.evtx
MaximumSizeInBytes             : 1052672
LogMode                        : Circular
OwningProviderName             : Microsoft-Windows-Eventlog
ProviderNames                  : {Microsoft-Windows-WUSA, Microsoft-Windows-ActionQueue...
ProviderLevel                  :
ProviderKeywords               :
ProviderBufferSize             : 64
ProviderMinimumNumberOfBuffers : 0
ProviderMaximumNumberOfBuffers : 64
ProviderLatency                : 1000
ProviderControlGuid            :
```

L' `Get-WinEvent` applet de commande utilise le paramètre **ListLog** pour spécifier le journal **d’installation** . L’objet est envoyé dans le pipeline à l’applet de commande `Format-List` . `Format-List` utilise le paramètre **Property** avec le `*` caractère générique astérisque () pour afficher chaque propriété.

### Exemple 3 : obtenir des journaux des événements à partir d’un serveur

Cette commande obtient uniquement les journaux des événements sur l’ordinateur local qui contiennent des événements. Il est possible que la valeur **RecordCount** d’un journal soit null ou zéro. L’exemple utilise la `$_` variable. Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md).

```powershell
Get-WinEvent -ListLog * -ComputerName localhost | Where-Object { $_.RecordCount }
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14546 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        2990 CxAudioSvcLog
Circular             1052672           9 MSFTVPN Setup
Circular             1052672         282 OAlerts
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **ListLog** utilise le `*` caractère générique astérisque () pour afficher des informations sur chaque journal. Le paramètre **ComputerName** spécifie d’extraire les journaux de l’ordinateur local, **localhost**. Les objets sont envoyés dans le pipeline à l’applet de commande `Where-Object` . `Where-Object` utilise `$_.RecordCount` pour retourner uniquement les journaux qui contiennent des données. `$_` variable qui représente l’objet actuel dans le pipeline. **RecordCount** est une propriété de l’objet avec une valeur non null.

### Exemple 4 : récupérer des journaux d’événements à partir de plusieurs serveurs

Cet exemple récupère les objets qui représentent les journaux des événements d' **application** sur trois ordinateurs : Serveur01, Server02 et Server03. Le mot clé **foreach** est utilisé, car le paramètre **ComputerName** n’accepte qu’une seule valeur. Pour plus d’informations, consultez [about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md).

```powershell
$S = 'Server01', 'Server02', 'Server03'
ForEach ($Server in $S) {
  Get-WinEvent -ListLog Application -ComputerName $Server |
    Select-Object LogMode, MaximumSizeInBytes, RecordCount, LogName,
      @{name='ComputerName'; expression={$Server}} |
    Format-Table -AutoSize
}
```

```Output
 LogMode MaximumSizeInBytes RecordCount LogName     ComputerName
 ------- ------------------ ----------- -------     ------------
Circular           15532032       14577 Application Server01
Circular           15532032        9689 Application Server02
Circular           15532032        5309 Application Server03
```

La variable `$S` stocke les noms de trois serveurs : **SERVEUR01**, **Server02** et **Server03**. L’instruction **foreach** utilise une boucle pour traiter chaque serveur, `($Server in $S)` . Le bloc de script entre accolades ( `{ }` ) exécute la `Get-WinEvent` commande. Le paramètre **ListLog** spécifie le journal des **applications** . Le paramètre **ComputerName** utilise la variable `$Server` pour récupérer les informations de journalisation à partir de chaque serveur.

Les objets sont envoyés dans le pipeline à l’applet de commande `Select-Object` . `Select-Object` Obtient les propriétés **LogMode**, **MaximumSizeInBytes**, **RecordCount**, **logname** et utilise une expression calculée pour afficher le nom de l' **ordinateur** à l’aide de la `$Server` variable. Les objets sont envoyés dans le pipeline à l' `Format-Table` applet de commande pour afficher la sortie dans la console PowerShell. Le paramètre **AutoSize** met en forme la sortie en fonction de l’écran.

### Exemple 5 : récupération des fournisseurs de journaux des événements et des noms de journaux

Cette commande obtient les fournisseurs de journaux d’événements et les journaux dans lesquels ils écrivent.

```powershell
Get-WinEvent -ListProvider *
```

```Output
Name     : .NET Runtime
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : .NET Runtime Optimization Service
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **ListProvider** utilise le `*` caractère générique astérisque () pour afficher des informations sur chaque fournisseur. Dans la sortie, le **nom** est le fournisseur et **LogLinks** est le journal dans lequel le fournisseur écrit.

### Exemple 6 : obtenir tous les fournisseurs de journaux des événements qui écrivent dans un journal spécifique

Cette commande obtient tous les fournisseurs qui écrivent dans le journal des **applications** .

```powershell
(Get-WinEvent -ListLog Application).ProviderNames
```

```Output
.NET Runtime
.NET Runtime Optimization Service
Application
Application Error
Application Hang
Application Management
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **ListLog** utilise l' **application** pour obtenir des objets pour ce journal. **ProviderNames** est une propriété de l’objet et affiche les fournisseurs qui écrivent dans le journal des **applications** .

### Exemple 7 : obtenir les noms des fournisseurs de journaux des événements qui contiennent une chaîne spécifique

Cette commande obtient les fournisseurs de journaux des événements dont les noms incluent une chaîne spécifique dans le nom du fournisseur.

```powershell
Get-WinEvent -ListProvider *Policy*
```

```Output
Name     : Group Policy Applications
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Client
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Data Sources
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **ListProvider** utilise le `*` caractère générique astérisque () pour rechercher une **stratégie** n’importe où dans le nom du fournisseur.

### Exemple 8 : récupération des ID d’événement générés par le fournisseur d’événements

Cette commande répertorie les ID d’événement générés par le fournisseur d’événements **Microsoft-Windows-GroupPolicy** , ainsi que la description de l’événement.

```powershell
(Get-WinEvent -ListProvider Microsoft-Windows-GroupPolicy).Events | Format-Table Id, Description
```

```Output
  Id  Description
  --  -----------
1500  The Group Policy settings for the computer were processed successfully...
1501  The Group Policy settings for the user were processed successfully...
4115  Group Policy Service started.
4116  Started the Group Policy service initialization phase.
4117  Group Policy Session started.
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **ListProvider** spécifie le fournisseur, **Microsoft-Windows-GroupPolicy**. L’expression est placée entre parenthèses et utilise la propriété **Events** pour récupérer des objets. Les objets sont envoyés dans le pipeline à l’applet de commande `Format-Table` . `Format-Table` affiche l' **ID** et la **Description** des objets d’événement.

### Exemple 9 : récupérer des informations de journal à partir des propriétés de l’objet d’événement

Cet exemple montre comment obtenir des informations sur le contenu d’un journal à l’aide des propriétés de l’objet d’événement.
Les objets d’événement sont stockés dans une variable, puis regroupés et comptabilisés par ID et **niveau** d' **événement** .

```powershell
$Event = Get-WinEvent -LogName 'Windows PowerShell'
$Event.Count
$Event | Group-Object -Property Id -NoElement | Sort-Object -Property Count -Descending
$Event | Group-Object -Property LevelDisplayName -NoElement
```

```Output
195

Count  Name
-----  ----
  147  600
   22  400
   21  601
    3  403
    2  103

Count  Name
-----  ----
    2  Warning
  193  Information
```

L' `Get-WinEvent` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements **Windows PowerShell** . Les objets d’événement sont stockés dans la `$Event` variable. La propriété **Count** de `$Event` affiche le nombre total d’événements journalisés.

La `$Event` variable est envoyée dans le pipeline à l’applet de commande `Group-Object` . `Group-Object` utilise le paramètre **Property** pour spécifier la propriété **ID** et compte les objets par la valeur de l’ID d’événement. Le paramètre **NoElement** supprime d’autres propriétés de la sortie des objets. Les objets groupés sont envoyés dans le pipeline à l’applet de commande `Sort-Object` . `Sort-Object` utilise le paramètre **Property** pour trier les objets par **nombre**. Le paramètre **Descending** affiche la sortie en nombre, de la plus élevée à la plus faible. Dans la sortie, la colonne **Count** contient le nombre total de chaque événement. La colonne **nom** contient les numéros d’ID d’événement groupés.

La `$Event` variable est envoyée dans le pipeline à l’applet de commande `Group-Object` . `Group-Object` utilise le paramètre **Property** pour spécifier la propriété **LevelDisplayName** et compte les objets par **LevelDisplayName**. Les objets sont regroupés en fonction des niveaux tels que l' **Avertissement** et les **informations**.
Le paramètre **NoElement** supprime d’autres propriétés de la sortie. Dans la sortie, la colonne **Count** contient le nombre total de chaque événement. La colonne **nom** contient le **LevelDisplayName** groupé.

### Exemple 10 : obtenir des événements d’erreur dont le nom contient une chaîne spécifiée

Cet exemple utilise une chaîne séparée par des virgules de noms de journaux. La sortie est regroupée en fonction du niveau de l’erreur ou de l’avertissement et du nom du journal.

```powershell
Get-WinEvent -LogName *PowerShell*, Microsoft-Windows-Kernel-WHEA* |
  Group-Object -Property LevelDisplayName, LogName -NoElement |
    Format-Table -AutoSize
```

```Output
Count  Name
-----  ----
    1  Error, PowerShellCore/Operational
   26  Information, Microsoft-Windows-Kernel-WHEA/Operational
  488  Information, Microsoft-Windows-PowerShell/Operational
   77  Information, PowerShellCore/Operational
 9835  Information, Windows PowerShell
   19  Verbose, PowerShellCore/Operational
  444  Warning, Microsoft-Windows-PowerShell/Operational
  512  Warning, PowerShellCore/Operational
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **logname** utilise une chaîne séparée par des virgules avec le `*` caractère générique astérisque () pour spécifier les noms des journaux. Les objets sont envoyés dans le pipeline à l’applet de commande `Group-Object` . `Group-Object` utilise le paramètre **Property** pour regrouper les objets par **LevelDisplayName** et **logname**. Le paramètre **NoElement** supprime d’autres propriétés de la sortie. Les objets groupés sont envoyés dans le pipeline à l’applet de commande `Format-Table` . `Format-Table` utilise le paramètre **AutoSize** pour mettre en forme les colonnes. La colonne **nombre** contient le nombre total de chaque événement. La colonne **nom** contient les **LevelDisplayName** et **logname** groupés.

### Exemple 11 : récupérer des événements à partir d’un journal des événements Archivé

`Get-WinEvent` peut récupérer des informations sur les événements à partir de fichiers journaux enregistrés. Cet exemple utilise un journal PowerShell archivé qui est stocké sur l’ordinateur local.

```powershell
Get-WinEvent -Path 'C:\Test\Windows PowerShell.evtx'
```

```Output
   ProviderName: PowerShell

TimeCreated              Id LevelDisplayName  Message
-----------              -- ----------------  -------
3/15/2019 13:54:13      403 Information       Engine state is changed from Available to Stopped...
3/15/2019 13:54:13      400 Information       Engine state is changed from None to Available...
3/15/2019 13:54:13      600 Information       Provider "Variable" is Started...
3/15/2019 13:54:13      600 Information       Provider "Function" is Started...
3/15/2019 13:54:13      600 Information       Provider "FileSystem" is Started...
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **path** spécifie le répertoire et le nom de fichier.

### Exemple 12 : obtenir un nombre spécifique d’événements à partir d’un journal des événements Archivé

Ces commandes obtiennent un nombre spécifique d’événements à partir d’un journal des événements Archivé. `Get-WinEvent` possède des paramètres qui peuvent obtenir un nombre maximal d’événements ou les événements les plus anciens. Cet exemple utilise un journal PowerShell archivé qui est stocké dans **C:\Test\PowerShellCore Operational. evtx**.

```powershell
Get-WinEvent -Path 'C:\Test\PowerShellCore Operational.evtx' -MaxEvents 100
```

```Output
   ProviderName: PowerShellCore

TimeCreated                 Id   LevelDisplayName  Message
-----------                 --   ----------------  -------
3/15/2019 09:54:54        4104   Warning           Creating Scriptblock text (1 of 1):...
3/15/2019 09:37:13       40962   Information       PowerShell console is ready for user input
3/15/2019 07:56:24        4104   Warning           Creating Scriptblock text (1 of 1):...
...
3/7/2019 10:53:22        40961   Information       PowerShell console is starting up
3/7/2019 10:53:22         8197   Verbose           Runspace state changed to Opening
3/7/2019 10:53:22         8195   Verbose           Opening RunspacePool
```

L' `Get-WinEvent` applet de commande obtient les informations de journalisation de l’ordinateur. Le paramètre **path** spécifie le répertoire et le nom de fichier. Le paramètre **MaxEvents** spécifie que 100 enregistrements sont affichés, du plus récent au plus ancien.

### Exemple 13 : Suivi d’v nements pour Windows

Suivi d’v nements pour Windows (ETW) écrit des événements dans le journal lorsque des événements se produisent. Les événements sont stockés dans l’ordre le plus ancien au plus récent. Un fichier ETW archivé est enregistré en tant que `.etl` **tracelog. etl**.
Les événements sont répertoriés dans l’ordre dans lequel ils sont écrits dans le journal. le paramètre le *plus ancien* est donc requis.

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl' -Oldest |
  Sort-Object -Property TimeCreated -Descending |
    Select-Object -First 100
```

L' `Get-WinEvent` applet de commande obtient les informations de journal à partir du fichier archivé. Le paramètre **path** spécifie le répertoire et le nom de fichier. Le paramètre le **plus ancien** est utilisé pour générer des événements dans l’ordre dans lequel ils sont écrits, du plus ancien au plus récent. Les objets sont envoyés dans le pipeline à l' `Sort-Object` applet de commande. pour cela, les objets sont `Sort-Object` triés par ordre décroissant selon la valeur de la propriété **TimeCreated** . Les objets sont envoyés dans le pipeline à l’applet de commande `Select-Object` qui affiche les événements 100 les plus récents.

### Exemple 14 : récupérer des événements à partir d’un journal de suivi d’événements

Cet exemple montre comment récupérer les événements à partir d’un fichier journal de suivi d’événements ( `.etl` ) et d’un fichier journal Windows PowerShell archivé ( `.evtx` ). Vous pouvez combiner plusieurs types de fichier dans une seule commande.
Étant donné que les fichiers contiennent le même type d' **.NET Framework** objet, **EventLogRecord**, vous pouvez les filtrer avec les mêmes propriétés. La commande requiert le paramètre le **plus ancien** , car elle lit à partir d’un `.etl` fichier, mais le **plus ancien** paramètre s’applique à chaque fichier.

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl', 'C:\Test\Windows PowerShell.evtx' -Oldest |
  Where-Object { $_.Id -eq '403' }
```

L' `Get-WinEvent` applet de commande obtient les informations de journal à partir des fichiers archivés. Le paramètre **path** utilise une liste séparée par des virgules pour spécifier chaque répertoire de fichiers et le nom de fichier. Le paramètre le **plus ancien** est utilisé pour générer des événements dans l’ordre dans lequel ils sont écrits, du plus ancien au plus récent. Les objets sont envoyés dans le pipeline à l’applet de commande `Where-Object` . `Where-Object` utilise un bloc de script pour rechercher des événements avec l' **ID** et **403**. La `$_` variable représente l’objet actuel dans le pipeline et l' **ID** est la propriété de l’ID d’événement.

### Exemple 15 : filtrer les résultats du journal des événements

Cet exemple illustre diverses méthodes permettant de filtrer et de sélectionner des événements à partir d’un journal des événements. Toutes ces commandes obtiennent les événements qui se sont produits au cours des dernières 24 heures à partir du journal des événements **Windows PowerShell** .
Les méthodes de filtrage sont plus efficaces que l’utilisation de l’applet de commande `Where-Object` . Les filtres sont appliqués au fur et à mesure que les objets sont récupérés. `Where-Object` récupère tous les objets, puis applique des filtres à tous les objets.

```powershell
# Using the Where-Object cmdlet:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -LogName 'Windows PowerShell' | Where-Object { $_.TimeCreated -ge $Yesterday }

# Using the FilterHashtable parameter:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -FilterHashtable @{ LogName='Windows PowerShell'; Level=3; StartTime=$Yesterday }

# Using the FilterXML parameter:
$xmlQuery = @'
<QueryList>
  <Query Id="0" Path="Windows PowerShell">
    <Select Path="System">*[System[(Level=3) and
        TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]</Select>
  </Query>
</QueryList>
'@
Get-WinEvent -FilterXML $xmlQuery

# Using the FilterXPath parameter:
$XPath = '*[System[Level=3 and TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]'
Get-WinEvent -LogName 'Windows PowerShell' -FilterXPath $XPath
```

### Exemple 16 : utilisation de FilterHashtable pour récupérer des événements à partir du journal des applications

Cet exemple utilise le paramètre **FilterHashtable** pour récupérer des événements à partir du journal des **applications** . La table de hachage utilise des paires **clé/valeur** . Pour plus d’informations sur le paramètre **FilterHashtable** , consultez [création de requêtes Get-WinEvent avec FilterHashtable](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable).
Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](../Microsoft.PowerShell.Core/about/about_hash_tables.md).

```powershell
$Date = (Get-Date).AddDays(-2)
Get-WinEvent -FilterHashtable @{ LogName='Application'; StartTime=$Date; Id='1003' }
```

L' `Get-Date` applet de commande utilise la méthode **AddDays** pour obtenir une date qui se trouve deux jours avant la date actuelle. L’objet date est stocké dans la `$Date` variable.

L' `Get-WinEvent` applet de commande obtient les informations du journal. Le paramètre **FilterHashtable** est utilisé pour filtrer la sortie. La clé **logname** spécifie la valeur comme journal des **applications** . La clé **StartTime** utilise la valeur stockée dans la `$Date` variable. La clé d' **ID** utilise une valeur d’ID d’événement, **1003**.

### Exemple 17 : utiliser FilterHashtable pour récupérer des erreurs d’application

Cet exemple utilise le paramètre **FilterHashtable** pour rechercher les erreurs d’application Internet Explorer qui se sont produites au cours de la semaine précédente.

```powershell
$StartTime = (Get-Date).AddDays(-7)
Get-WinEvent -FilterHashtable @{
  Logname='Application'
  ProviderName='Application Error'
  Data='iexplore.exe'
  StartTime=$StartTime
}
```

L' `Get-Date` applet de commande utilise la méthode **AddDays** pour obtenir une date qui est sept jours avant la date actuelle. L’objet date est stocké dans la `$StartTime` variable.

L' `Get-WinEvent` applet de commande obtient les informations du journal. Le paramètre **FilterHashtable** est utilisé pour filtrer la sortie. La clé **logname** spécifie la valeur comme journal des **applications** . La clé **providerName** utilise la valeur, **erreur** de l’application, qui est la **source** de l’événement. La clé de **données** utilise la valeur **iexplore.exe** la clé **StartTime** utilise la valeur stockée dans `$StartTime` variable.

### Exemple 18 : utiliser SuppressHashFilter pour filtrer les erreurs d’application

Comme dans l’exemple 16 ci-dessus, cet exemple utilise le paramètre **FilterHashtable** pour récupérer des événements à partir du journal des **applications** . Toutefois, nous ajoutons la clé **SuppressHashFilter** pour filtrer les événements de niveau **informations** .

```powershell
$Date = (Get-Date).AddDays(-2)
$filter = @{
  LogName='Application'
  StartTime=$Date
  SuppressHashFilter=@{Level=4}
}
Get-WinEvent -FilterHashtable $filter
```

Dans cet exemple, `Get-WinEvent` obtient tous les événements du journal des **applications** pour les deux derniers jours, à l’exception de ceux qui ont un **niveau** de 4 (informations).

## PARAMETERS

### -ComputerName

Spécifie le nom de l’ordinateur sur lequel cette applet de commande obtient des événements à partir des journaux des événements. Tapez le nom NetBIOS, une adresse IP ou le nom de domaine complet (FQDN) de l’ordinateur. La valeur par défaut est l’ordinateur local, **localhost**. Ce paramètre accepte uniquement un nom d'ordinateur à la fois.

Pour obtenir les journaux des événements à partir d’ordinateurs distants, configurez le port du pare-feu pour le service journal des événements afin d’autoriser l’accès à distance.

Cette applet de commande ne s’appuie pas sur la communication à distance PowerShell. Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String
Parameter Sets: GetLogSet, ListLogSet, ListProviderSet, GetProviderSet, HashQuerySet, XmlQuerySet
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l'utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**. Ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe. Si vous tapez uniquement le nom du paramètre, vous êtes invité à entrer un nom d’utilisateur et un mot de passe.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterHashtable

Spécifie une requête au format de table de hachage pour sélectionner des événements dans un ou plusieurs journaux des événements. La requête contient une table de hachage avec une ou plusieurs paires **clé/valeur** .

Les requêtes de table de hachage comportent les règles suivantes :

- Les clés et les valeurs ne respectent pas la casse.
- Les caractères génériques ne sont valides que dans les valeurs associées aux clés **logname** et **providerName** .
- Chaque clé ne peut être listée qu’une seule fois dans chaque table de hachage.
- La valeur du **chemin d’accès** accepte les chemins d’accès aux `.etl` `.evt` `.evtx` fichiers journaux, et.
- Les clés **logname**, **path** et **providerName** peuvent être utilisées dans la même requête.
- La clé **userid** peut accepter un identificateur de sécurité (SID) valide ou un nom de compte de domaine qui peut être utilisé pour construire un **objet System. Security. principal. NTAccount** valide.
- La valeur des **données** accepte les données d’événement dans un champ sans nom. Par exemple, les événements dans les journaux des événements classiques.
- `<named-data>` la clé représente un champ de données d’événement nommé.

Quand `Get-WinEvent` ne peut pas interpréter une paire **clé/valeur** , il interprète la clé comme un nom qui respecte la casse pour les données d’événement dans l’événement.

Les paires `Get-WinEvent` **clé/valeur** valides sont les suivantes :

- **LogName**=`<String[]>`
- **Désigne**=`<String[]>`
- **D**=`<String[]>`
- **Mot**=`<Long[]>`
- **IDENTIFI**=`<Int32[]>`
- **Niveau**=`<Int32[]>`
- **Heure**=`<DateTime>`
- **EndTime**=`<DateTime>`
- **IDutilisateur**=`<SID>`
- **Métadonnée**=`<String[]>`
- `<named-data>`=`<String[]>`
- **SuppressHashFilter**=`<Hashtable>`

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: HashQuerySet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXml

Spécifie une requête XML structurée que cette applet de commande sélectionne des événements dans un ou plusieurs journaux des événements.

Pour générer une requête XML valide, utilisez les fonctionnalités **créer une vue personnalisée** et **filtrer le journal actuel** dans Windows Observateur d’événements. Utilisez les éléments de la boîte de dialogue pour créer une requête, puis cliquez sur l'onglet XML pour afficher la requête au format XML. Vous pouvez copier le code XML à partir de l'onglet XML dans la valeur du paramètre **FilterXml**. Pour plus d'informations sur les fonctionnalités de l'Observateur d'événements, consultez l'aide de l'Observateur d'événements.

Utilisez une requête XML pour créer une requête complexe qui contient plusieurs instructions XPath. Le format XML vous permet également d’utiliser un élément **XML de suppression** qui exclut les événements de la requête. Pour plus d’informations sur le schéma XML des requêtes de journal des événements, consultez la section [schéma de requête](/windows/win32/wes/queryschema-schema) et la section requêtes d’événements XML de la [sélection d’événements](/previous-versions/aa385231(v=vs.85)).

Vous pouvez également créer un élément **supprimer** à l’aide du paramètre **FilterHashtable** .

```yaml
Type: System.Xml.XmlDocument
Parameter Sets: XmlQuerySet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXPath

Spécifie une requête XPath que cette applet de commande sélectionne des événements dans un ou plusieurs journaux.

Pour plus d’informations sur le langage XPath, consultez [Référence XPath](/previous-versions/dotnet/netframework-4.0/ms256115(v=vs.100)) et la section filtres de sélection de la [sélection d’événements](/previous-versions/aa385231(v=vs.85)).

```yaml
Type: System.String
Parameter Sets: GetLogSet, GetProviderSet, FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Obtient les journaux de débogage et d'analyse, ainsi que d'autres journaux des événements. Le paramètre **Force** est nécessaire pour obtenir un journal de débogage ou d'analyse quand la valeur du paramètre name comprend des caractères génériques.

Par défaut, l' `Get-WinEvent` applet de commande exclut ces journaux, sauf si vous spécifiez le nom complet d’un journal de débogage ou d’analyse.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, ListLogSet, GetProviderSet, HashQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListLog

Spécifie les journaux des événements. Entrez les noms des journaux des événements dans une liste de valeurs séparées par des virgules. Les caractères génériques sont autorisés. Pour récupérer tous les journaux, utilisez le `*` caractère générique astérisque ().

```yaml
Type: System.String[]
Parameter Sets: ListLogSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ListProvider

Spécifie les fournisseurs de journaux d’événements que cette applet de commande obtient. Le fournisseur du journal des événements est un programme ou service qui enregistre les événements dans le journal des événements.

Entrez les noms des fournisseurs dans une liste de valeurs séparées par des virgules. Les caractères génériques sont autorisés. Pour récupérer les fournisseurs de tous les journaux des événements sur l’ordinateur, utilisez le `*` caractère générique astérisque ().

```yaml
Type: System.String[]
Parameter Sets: ListProviderSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LogName

Spécifie les journaux des événements à partir desquels cette applet de commande obtient des événements. Entrez les noms des journaux des événements dans une liste de valeurs séparées par des virgules. Les caractères génériques sont autorisés. Vous pouvez également diriger les noms de journaux vers l’applet de commande `Get-WinEvent` .

> [!NOTE]
> PowerShell ne limite pas la quantité de journaux que vous pouvez demander. Toutefois, l' `Get-WinEvent` applet de commande interroge l’API Windows qui a une limite de 256. Cela peut compliquer le filtrage de tous vos journaux à la fois. Vous pouvez contourner ce contournement en utilisant une `foreach` boucle pour itérer au sein de chaque journal comme suit : `Get-WinEvent -ListLog * | ForEach-Object{ Get-WinEvent -LogName $_.Logname }`

```yaml
Type: System.String[]
Parameter Sets: GetLogSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -MaxEvents

Spécifie le nombre maximal d’événements qui sont retournés. Entrez un entier tel que 100. La valeur par défaut consiste à retourner tous les événements des journaux ou des fichiers.

```yaml
Type: System.Int64
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Plus ancien

Indique que cette applet de commande obtient les événements dans l’ordre le plus ancien. Par défaut, les événements sont retournés du plus ancien au plus récent.

Ce paramètre est obligatoire pour recevoir des événements `.etl` des `.evt` fichiers et et des journaux de débogage et d’analyse. Dans ces fichiers, les événements sont enregistrés du plus ancien au plus récent, et ne peuvent être retournés que du plus ancien au plus récent.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès aux fichiers journaux des événements à partir desquels cette applet de commande obtient des événements. Entrez les chemins d'accès des fichiers journaux dans une liste de valeurs séparées par des virgules, ou utilisez des caractères génériques pour créer des modèles de chemin d'accès de fichier.

`Get-WinEvent` prend en charge les fichiers avec les `.evt` `.evtx` extensions de nom de fichier, et `.etl` . Vous pouvez inclure les événements de différents fichiers et types de fichier dans la même commande.

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ProviderName

Spécifie, sous forme de tableau de chaînes, les fournisseurs de journaux d’événements à partir desquels cette applet de commande obtient des événements. Entrez les noms des fournisseurs dans une liste de valeurs séparées par des virgules, ou utilisez des caractères génériques pour créer des modèles de nom de fournisseur.

Le fournisseur du journal des événements est un programme ou service qui enregistre les événements dans le journal des événements. Il ne s’agit pas d’un fournisseur PowerShell.

```yaml
Type: System.String[]
Parameter Sets: GetProviderSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. String, System.Xml.Xmldocument, System. Collections. Hashtable

Vous pouvez canaliser un **logname** (chaîne), une requête **FilterXML** ou une requête **FilterHashtable** vers `Get-WinEvent` .

## SORTIES

### System. Diagnostics. Eventing. Reader. EventLogConfiguration, System. Diagnostics. Eventing. Reader. EventLogRecord, System. Diagnostics. Eventing. Reader. ProviderMetadata

Avec le paramètre **ListLog** , `Get-WinEvent` retourne les objets **System. Diagnostics. Eventing. Reader. EventLogConfiguration** .

Avec le paramètre **ListProvider** , `Get-WinEvent` retourne les objets **System. Diagnostics. Eventing. Reader. ProviderMetadata** .

Avec tous les autres paramètres, `Get-WinEvent` retourne les objets **System. Diagnostics. Eventing. Reader. EventLogRecord** .

## REMARQUES

`Get-WinEvent` est conçu pour remplacer l' `Get-EventLog` applet de commande sur les ordinateurs exécutant Windows Vista et les versions ultérieures de Windows. `Get-EventLog` Obtient les événements uniquement dans les journaux des événements classiques. `Get-EventLog` est conservé à des fins de compatibilité descendante.

Les `Get-WinEvent` applets de commande et ne `Get-EventLog` sont pas prises en charge dans l’environnement de préinstallation Windows (Windows PE).

## LIENS CONNEXES

[about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)

[about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)

[Création de requêtes Get-WinEvent avec FilterHashtable](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

