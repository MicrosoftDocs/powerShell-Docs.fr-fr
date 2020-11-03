---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 7f44f1d363c5fae79722fdfb5bd894cb24e00d0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205226"
---
# Get-Service

## SYNOPSIS
Obtient les services sur l’ordinateur.

## SYNTAX

### Valeur par défaut (par défaut)

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## Description

L' `Get-Service` applet de commande obtient les objets qui représentent les services sur un ordinateur, y compris les services en cours d’exécution et arrêtés. Par défaut, lorsque `Get-Service` est exécuté sans paramètres, tous les services de l’ordinateur local sont retournés.

Vous pouvez demander à cette applet de commande d’obtenir uniquement des services particuliers en spécifiant le nom de service ou le nom d’affichage des services, ou vous pouvez diriger les objets de service vers cette applet de commande.

## EXEMPLES

### Exemple 1 : récupération de tous les services sur l’ordinateur

Cet exemple obtient tous les services sur l’ordinateur. Il se comporte comme si vous aviez tapé `Get-Service *` . L’affichage par défaut répertorie l’état, le nom et le nom d’affichage de chaque service.

```powershell
Get-Service
```

### Exemple 2 : obtenir les services qui commencent par une chaîne de recherche

Cet exemple récupère les services dont le nom de service commence par WMI (Windows Management Instrumentation).

```powershell
Get-Service "wmi*"
```

### Exemple 3 : afficher les services qui incluent une chaîne de recherche

Cet exemple affiche les services dont le nom d’affichage comprend le mot réseau. La recherche du nom complet recherche les services liés au réseau même si le nom du service n’inclut pas net, par exemple xmlprov, le service d’approvisionnement réseau.

```powershell
Get-Service -Displayname "*network*"
```

### Exemple 4 : obtenir des services qui commencent par une chaîne de recherche et une exclusion

Cet exemple obtient uniquement les services dont les noms de service commencent par **Win** , à l’exception du service WinRM.

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### Exemple 5 : afficher les services actuellement actifs

Cet exemple affiche uniquement les services dont l’État est en cours d’exécution.

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

`Get-Service` Obtient tous les services sur l’ordinateur et envoie les objets dans le pipeline. L' `Where-Object` applet de commande sélectionne uniquement les services dont la propriété **Status** est égale à Running.

Status n’est qu’une des propriétés des objets Service. Pour afficher toutes les propriétés, tapez `Get-Service | Get-Member` .

### Exemple 6 : répertorier les services sur l’ordinateur qui ont des services dépendants

Cet exemple obtient les services qui ont des services dépendants.

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

L' `Get-Service` applet de commande obtient tous les services sur l’ordinateur et envoie les objets dans le pipeline. L' `Where-Object` applet de commande sélectionne les services dont la propriété **DependentServices** n’est pas null.

Les résultats sont envoyés dans le pipeline à l’applet de commande `Format-List` . Le paramètre **Property** affiche le nom du service, le nom des services dépendants et une propriété calculée qui affiche le nombre de services dépendants pour chaque service.

### Exemple 7 : trier les services par valeur de propriété

Cet exemple montre que lorsque vous triez des services dans l’ordre croissant en fonction de la valeur de leur propriété **Status** , les services arrêtés s’affichent avant l’exécution des services. La raison est que la valeur de **Status** est une énumération, dans laquelle Stopped a la valeur 1 et l’exécution a une valeur de 4. Pour plus d’informations, consultez [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).

Pour répertorier d’abord les services en cours d’exécution, utilisez le paramètre **décroissant** de l’applet de commande `Sort-Object` .

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

### Exemple 8 : obtenir les services dépendants d’un service

Cet exemple obtient les services requis par le service WinRM. La valeur de la propriété **ServicesDependedOn** du service est retournée.

```powershell
Get-Service "WinRM" -RequiredServices
```

### Exemple 9 : obtenir un service par le biais de l’opérateur de pipeline

Cet exemple obtient le service WinRM sur l’ordinateur local. La chaîne de nom de service, placée entre guillemets, est envoyée dans le pipeline à `Get-Service` .

```powershell
"WinRM" | Get-Service
```

## PARAMETERS

### -DependentServices

Indique que cette applet de commande obtient uniquement les services qui dépendent du service spécifié.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

Spécifie, sous forme de tableau de chaînes, les noms d’affichage des services à récupérer. Les caractères génériques sont autorisés.

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
La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que `s*` . Les caractères génériques sont autorisés.

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

Spécifie, sous la forme d’un tableau de chaînes, un ou des services inclus dans l’opération par cette applet de commande. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que `s*` . Les caractères génériques sont autorisés.

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

Spécifie les objets **ServiceController** représentant les services à récupérer. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets. Vous pouvez diriger un objet de service vers cette applet de commande.

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

Spécifie les noms des services à récupérer. Les caractères génériques sont autorisés.

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

Indique que cette applet de commande obtient uniquement les services dont ce service a besoin. Ce paramètre obtient la valeur de la propriété **ServicesDependedOn** du service.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
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

À compter de PowerShell 6,0, les propriétés suivantes sont ajoutées aux objets **ServiceController** : **nom d’utilisateur** , **Description** , **DelayedAutoStart** , **BinaryPathName** et **startupType** .

Vous pouvez également faire référence à `Get-Service` par son alias intégré, `gsv` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Cette applet de commande peut afficher les services uniquement lorsque l’utilisateur actuel a l’autorisation de les afficher. Si cette applet de commande n’affiche pas de services, vous n’avez peut-être pas l’autorisation de les afficher.

Pour rechercher le nom du service et le nom d’affichage de chaque service sur votre système, tapez `Get-Service` . Les noms de service s’affichent dans la colonne nom, et les noms d’affichage apparaissent dans la colonne **DisplayName** .

Lorsque vous triez par ordre croissant selon la valeur de la propriété **Status** , les services arrêtés s’affichent avant l’exécution des services. La propriété **Status** du service est une valeur énumérée et les noms d’État représentent des valeurs entières. L’ordre de tri est basé sur la valeur entière, et non sur le nom. L’état arrêté s’affiche avant, car l’exécution de, car Stopped a la valeur 1, et Running a la valeur 4. Pour plus d’informations, consultez [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).

## LIENS CONNEXES

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)

