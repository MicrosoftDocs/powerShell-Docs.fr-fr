---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203494"
---
# Set-Service

## SYNOPSIS
Démarre, arrête et interrompt un service, puis modifie ses propriétés.

## SYNTAX

### Nom (par défaut)

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Set-Service` applet de commande modifie les propriétés d’un service, telles que l' **État** , la **Description** , **DisplayName** et **startupType** . `Set-Service` permet de démarrer, d’arrêter, de suspendre ou de suspendre un service. Pour identifier un service, entrez son nom de service ou envoyez un objet de service. Ou, envoyez un nom de service ou un objet de service dans le pipeline à `Set-Service` .

## EXEMPLES

### Exemple 1 : modifier un nom complet

Dans cet exemple, le nom complet d’un service est modifié. Pour afficher le nom d’affichage d’origine, utilisez `Get-Service` .

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

`Set-Service` utilise le paramètre **Name** pour spécifier le nom du service, **LanmanWorkstation** . Le paramètre **DisplayName** spécifie le nouveau nom complet, la **station de travail LanMan** .

### Exemple 2 : modifier le type de démarrage des services

Cet exemple montre comment modifier le type de démarrage d’un service.

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

`Set-Service` utilise le paramètre **Name** pour spécifier le nom du service, **bits** . Le paramètre **startupType** définit le service sur **Automatic** .

`Get-Service` utilise le paramètre **Name** pour spécifier le service **bits** et envoie l’objet vers le pipeline. `Select-Object` utilise le paramètre **Property** pour afficher l’état du service **bits** .

### Exemple 3 : modifier la description d’un service

Cet exemple modifie la description du service BITS et affiche le résultat.

L' `Get-CimInstance` applet de commande est utilisée car elle retourne un objet **Win32_Service** qui comprend la **Description** du service.

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

`Get-CimInstance` envoie l’objet dans le pipeline à `Format-List` et affiche le nom et la description du service. À des fins de comparaison, la commande est exécutée avant et après la mise à jour de la description.

`Set-Service` utilise le paramètre **Name** pour spécifier le service **bits** . Le paramètre **Description** spécifie le texte mis à jour pour la description des services.

### Exemple 4 : démarrer un service

Dans cet exemple, un service est démarré.

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

`Set-Service` utilise le paramètre **Name** pour spécifier le service, **WinRM** . Le paramètre **Status** utilise la valeur **en cours d’exécution** pour démarrer le service. Le paramètre **PassThru** génère un objet **ServiceController** qui affiche les résultats.

### Exemple 5 : suspendre un service

Cet exemple utilise le pipeline pour suspendre le service.

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

`Get-Service` utilise le paramètre **Name** pour spécifier le service de **planification** et envoie l’objet dans le pipeline. `Set-Service` utilise le paramètre **Status** pour définir le service comme étant **suspendu** .

### Exemple 6 : arrêter un service

Cet exemple utilise une variable pour arrêter un service.

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

`Get-Service` utilise le paramètre **Name** pour spécifier le service, **Schedule** . L’objet est stocké dans la variable, `$S` . `Set-Service` utilise le paramètre **InputObject** et spécifie l’objet stocké `$S` . Le paramètre **Status** définit le service sur **Stopped** .

## PARAMETERS

### -ComputerName

Spécifie un ou plusieurs ordinateurs. Pour les ordinateurs distants, tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet. Si le paramètre **ComputerName** n’est pas spécifié, la commande s’exécute sur l’ordinateur local.

Ce paramètre ne s’appuie pas sur la communication à distance PowerShell. Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Vous invite à confirmer l’exécution `Set-Service` .

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

### Description

Spécifie une nouvelle description pour le service.

La description du service s’affiche dans gestion de l' **ordinateur, services** . La **Description** n’est pas une propriété de l' `Get-Service` objet **ServiceController** . Pour afficher la description du service, utilisez `Get-CimInstance` qui retourne un objet **Win32_Service** qui représente le service.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

Spécifie le nouveau nom d'affichage du service.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie un objet **ServiceController** qui représente le service à modifier. Entrez une variable qui contient l’objet ou tapez une commande ou une expression qui obtient l’objet, par exemple une `Get-Service` commande. Vous pouvez utiliser le pipeline pour envoyer un objet de service à `Set-Service` .

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie le nom du service à modifier. Les caractères génériques ne sont pas autorisés. Vous pouvez utiliser le pipeline pour envoyer un nom de service à `Set-Service` .

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

Retourne un objet **ServiceController** qui représente les services qui ont été modifiés. Par défaut, `Set-Service` ne génère pas de sortie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartupType

Définit le type de démarrage du service. Les valeurs valides pour ce paramètre sont :

- **Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.
  Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.
- **Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.
- **Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.
- **Démarrage** -indique que le service est un pilote de périphérique Démarré par le chargeur du système. Cette valeur est valide uniquement pour les pilotes de périphérique.
- **Système** : indique que le service est un pilote de périphérique Démarré par la fonction « IOInitSystem () ». Cette valeur est valide uniquement pour les pilotes de périphérique.

 La valeur par défaut est **automatique** .

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### -État

Spécifie l’état du service.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- **Suspendu** . suspend le service.
- **Exécution en cours** . démarre le service.
- **Arrêté** . arrête le service.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe si `Set-Service` s’exécute. L’applet de commande n’est pas exécutée.

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

### System. ServiceProcess. ServiceController, System. String

Vous pouvez utiliser le pipeline pour envoyer un objet de service ou une chaîne qui contient un nom de service à `Set-Service` .

## SORTIES

### System.ServiceProcess.ServiceController

Par défaut, `Set-Service` ne retourne aucun objet. Utilisez le paramètre **PassThru** pour générer un objet **ServiceController** .

## REMARQUES

`Set-Service` requiert des autorisations élevées. Utilisez l’option **exécuter en tant qu’administrateur** .

`Set-Service` ne peut contrôler des services que si l’utilisateur actuel dispose des autorisations nécessaires pour gérer les services. Si une commande ne fonctionne pas correctement, vous ne disposez peut-être pas des autorisations requises.

Pour rechercher le nom de service ou le nom d’affichage d’un service, utilisez `Get-Service` . Les noms de service figurent dans la colonne **nom** et les noms complets sont dans la colonne **DisplayName** .

## LIENS CONNEXES

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
