---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203989"
---
# Get-Service

## SYNOPSIS
Obtient les services présents sur un ordinateur local ou distant.

## SYNTAX

### Valeur par défaut (par défaut)

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## Description

L’applet de commande **obtenir-service** obtient les objets qui représentent les services sur un ordinateur local ou sur un ordinateur distant, y compris les services en cours d’exécution et arrêtés.

Vous pouvez demander à cette applet de commande d’obtenir uniquement des services particuliers en spécifiant le nom de service ou le nom d’affichage des services, ou vous pouvez diriger les objets de service vers cette applet de commande.

## EXEMPLES

### Exemple 1 : récupération de tous les services sur l’ordinateur

```powershell
Get-Service
```

Cette commande obtient tous les services sur l’ordinateur.
Il se comporte comme si vous aviez tapé `Get-Service *` .
L’affichage par défaut répertorie l’état, le nom et le nom d’affichage de chaque service.

### Exemple 2 : obtenir les services qui commencent par une chaîne de recherche

```powershell
Get-Service "wmi*"
```

Cette commande récupère des services dont le nom de service commence par WMI (l’acronyme de Windows Management Instrumentation).

### Exemple 3 : afficher les services qui incluent une chaîne de recherche

```powershell
Get-Service -Displayname "*network*"
```

Cette commande affiche les services dont le nom d’affichage comprend le mot réseau.
La recherche du nom d’affichage permet de rechercher des services associés au réseau, y compris lorsque leur nom n’inclut pas le mot « Net » (xmlprov, le service d’approvisionnement réseau, par exemple).

### Exemple 4 : obtenir des services qui commencent par une chaîne de recherche et une exclusion

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

Ces commandes obtiennent uniquement les services dont les noms de service commencent par Win, à l’exception du service WinRM.

### Exemple 5 : afficher les services actuellement actifs

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

Cette commande affiche uniquement les services qui sont actuellement actifs.
Elle utilise l’applet de commande **obten-service** pour récupérer tous les services sur l’ordinateur.
L’opérateur de pipeline (|) passe les résultats à l’applet de commande Where-Object, qui sélectionne uniquement les services dont la propriété Status est égale à Running.

Status n’est qu’une des propriétés des objets Service.
Pour afficher toutes les propriétés, tapez `Get-Service | Get-Member` .

### Exemple 6 : obtenir les services sur un ordinateur distant

```powershell
Get-Service -ComputerName "Server02"
```

Cette commande obtient les services présents sur l’ordinateur distant Server02.

Étant donné que le paramètre *ComputerName* de la fenêtre **obtenir le service** n’utilise pas la communication à distance Windows PowerShell, vous pouvez utiliser ce paramètre même si l’ordinateur n’est pas configuré pour la communication à distance dans Windows PowerShell.

### Exemple 7 : répertorier les services sur l’ordinateur local qui ont des services dépendants

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

La première commande utilise l’applet de commande **obten-service** pour récupérer les services sur l’ordinateur.
Un opérateur de pipeline (|) envoie les services à l’applet de commande **Where-Object** , qui sélectionne les services dont la propriété **DependentServices** n’a pas la valeur null.

Un autre opérateur de pipeline envoie les résultats à l’applet de commande Format-List.
La commande utilise son paramètre *Property* pour afficher le nom du service, le nom des services dépendants et une propriété calculée qui affiche le nombre de services dépendants de chaque service.

### Exemple 8 : trier les services par valeur de propriété

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

Cette commande montre que lorsque vous triez des services dans l’ordre croissant en fonction de la valeur de leur propriété **Status** , les services arrêtés s’affichent avant l’exécution des services.
Cela est dû au fait que la valeur de Status est une énumération, dans laquelle Stopped a la valeur 1, et Running a la valeur 4.

Pour répertorier d’abord les services en cours d’exécution, utilisez le paramètre *décroissant* de l’applet de commande Sort-Object.

### Exemple 9 : récupérer des services sur plusieurs ordinateurs

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

Cette commande utilise l’applet de commande **obtenir-service** pour exécuter une commande Get-Service WinRM sur deux ordinateurs distants et sur l’ordinateur local (« localhost »).

La commande s’exécute sur les ordinateurs distants et les résultats sont retournés à l’ordinateur local.
Un opérateur de pipeline (|) envoie les résultats à l’applet de commande **format-table** , qui met en forme les services sous la forme d’une table.
La commande **format-table** utilise le paramètre *Property* pour spécifier les propriétés affichées dans le tableau, y compris la propriété **MachineName** .

### Exemple 10 : obtenir les services dépendants d’un service

```powershell
Get-Service "WinRM" -RequiredServices
```

Cette commande obtient les services requis par le service WinRM.

La commande retourne la valeur de la propriété **ServicesDependedOn** du service.

### Exemple 11 : obtenir un service par le biais de l’opérateur de pipeline

```powershell
"WinRM" | Get-Service
```

Cette commande obtient le service WinRM présent sur l’ordinateur local.
Cet exemple montre que vous pouvez diriger une chaîne de nom de service (placée entre guillemets) vers **le service d’extraction** .

## PARAMETERS

### -ComputerName

Obtient les services qui s’exécutent sur les ordinateurs spécifiés.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet (FQDN) d’un ordinateur distant.
Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.
Vous pouvez utiliser le paramètre *ComputerName* de la commande **par procuration de service** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DependentServices

Indique que cette applet de commande obtient uniquement les services qui dépendent du service spécifié.

Par défaut, cette applet de commande obtient tous les services.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

Spécifie, sous forme de tableau de chaînes, les noms d’affichage des services à récupérer.
Les caractères génériques sont autorisés.
Par défaut, cette applet de commande obtient tous les services sur l’ordinateur.

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

Spécifie, sous forme de tableau de chaînes, un ou des services que cette applet de commande exclut de l’opération.
La valeur de ce paramètre qualifie le paramètre *Name* .
Entrez un élément ou un modèle de nom, tel que « s* ».
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Spécifie, sous la forme d’un tableau de chaînes, un ou des services inclus dans l’opération par cette applet de commande.
La valeur de ce paramètre qualifie le paramètre *Name* .
Entrez un élément ou un modèle de nom, tel que « s* ».
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

Spécifie les objets **ServiceController** représentant les services à récupérer.
Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.
Vous pouvez également diriger un objet service vers cette applet de commande.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des services à récupérer.
Les caractères génériques sont autorisés.
Par défaut, cette applet de commande obtient tous les services sur l’ordinateur.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -RequiredServices

Indique que cette applet de commande obtient uniquement les services dont ce service a besoin.

Ce paramètre obtient la valeur de la propriété **ServicesDependedOn** du service.
Par défaut, cette applet de commande obtient tous les services.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. ServiceProcess. ServiceController, System. String

Vous pouvez diriger un objet de service ou un nom de service vers cette applet de commande.

## SORTIES

### System.ServiceProcess.ServiceController

Cette applet de commande retourne des objets qui représentent les services sur l’ordinateur.

## REMARQUES

Vous pouvez également faire référence à la mise en **service** à l’aide de son alias intégré, « GSV ». Pour plus d'informations, consultez about_Aliases.

Cette applet de commande peut afficher les services uniquement lorsque l’utilisateur actuel a l’autorisation de les afficher.
Si cette applet de commande n’affiche pas de services, vous n’avez peut-être pas l’autorisation de les afficher.

Pour rechercher le nom du service et le nom d’affichage de chaque service sur votre système, tapez `Get-Service` .
Les noms de service figurent dans la colonne Name et les noms d'affichage apparaissent dans la colonne DisplayName.

Lorsque vous procédez à un tri dans l’ordre croissant en fonction de la valeur d’état, les services arrêtés (Stopped) apparaissent avant les services en cours d’exécution (Running).
La propriété Status d’un service est une valeur énumérée dans laquelle le nom des états représente des valeurs entières.
Le tri repose sur la valeur entière, et non sur le nom.
« Running » apparaît avant « Stopped », car « Stopped » a la valeur « 1 » et « Running » a la valeur « 4 ».

## LIENS CONNEXES

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
