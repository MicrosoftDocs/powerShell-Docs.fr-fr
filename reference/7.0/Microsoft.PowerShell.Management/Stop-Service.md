---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: 9dd0e04476d9f935d3284c30d1628b31417c14c2
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346290"
---
# Stop-Service

## SYNOPSIS
Arrête un ou plusieurs services en cours d'exécution.

## SYNTAXE

### InputObject (valeur par défaut)

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Default

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Stop-Service` applet de commande envoie un message d’arrêt au contrôleur de services Windows pour chacun des services spécifiés. Vous pouvez spécifier les services par leur nom de service ou leur nom d’affichage, ou vous pouvez utiliser le paramètre **InputObject** pour passer un objet de service qui représente le service que vous souhaitez arrêter.

## EXEMPLES

### Exemple 1 : arrêter un service sur l’ordinateur local

```
PS C:\> Stop-Service -Name "sysmonlog"
```

Cette commande arrête le service Journaux et alertes de performance (SysmonLog) sur l’ordinateur local.

### Exemple 2 : arrêter un service à l’aide du nom complet

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

Cette commande arrête le service Telnet sur l’ordinateur local. La commande utilise `Get-Service` pour récupérer un objet qui représente le service Telnet. L’opérateur de pipeline ( `|` ) dirige l’objet vers `Stop-Service` , qui arrête le service.

### Exemple 3 : arrêter un service qui a des services dépendants

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

Cet exemple arrête le service IISAdmin sur l’ordinateur local. Étant donné que l’arrêt de ce service arrête également les services qui dépendent du service IISAdmin, il est préférable de faire précéder d' `Stop-Service` une commande qui répertorie les services qui dépendent du service IISAdmin.

La première commande répertorie les services qui dépendent d’IISAdmin. Elle utilise `Get-Service` pour récupérer un objet qui représente le service IISAdmin. L’opérateur de pipeline ( `|` ) transmet le résultat à l’applet de commande `Format-List` . La commande utilise le paramètre **Property** de `Format-List` pour répertorier uniquement les propriétés **Name** et **DependentServices** du service.

La deuxième commande arrête le service IISAdmin. Le paramètre **force** est requis pour arrêter un service qui a des services dépendants. La commande utilise le paramètre **Confirm** pour demander la confirmation de l’utilisateur avant d’arrêter chaque service.

## PARAMÈTRES

### -DisplayName

Spécifie les noms d’affichage des services à arrêter.
Les caractères génériques sont autorisés.

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

Spécifie les services que cette applet de commande omet. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que s *. Les caractères génériques sont autorisés.

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

### -Force

Force l’applet de commande à arrêter un service même si ce service a des services dépendants.

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

### -Include

Spécifie les services que cette applet de commande arrête. La valeur de ce paramètre qualifie le paramètre **Name** . Entrez un élément ou un modèle de nom, tel que s *. Les caractères génériques sont autorisés.

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

Spécifie les objets **ServiceController** qui représentent les services à arrêter. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des services à arrêter. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -NOWAIT

Indique que cette applet de commande utilise l’option no Wait.

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

### -PassThru

Retourne un objet qui représente le nouveau service. Par défaut, cette applet de commande ne génère aucun résultat.

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

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

Vous pouvez diriger un objet de service ou une chaîne qui contient le nom d’un service vers cette applet de commande.

## SORTIES

### Aucun, System. ServiceProcess. ServiceController

Cette applet de commande génère un objet **System. ServiceProcess. ServiceController** qui représente le service, si vous utilisez le paramètre **PassThru** . Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

Vous pouvez également faire référence à `Stop-Service` par son alias intégré, **spsv**. Pour plus d'informations, consultez about_Aliases.

`Stop-Service` peut contrôler les services uniquement lorsque l’utilisateur actuel est autorisé à le faire. Si une commande ne fonctionne pas correctement, cela signifie peut-être que vous ne disposez pas des autorisations requises.

Pour rechercher les noms de service et les noms d’affichage des services sur votre système, tapez `Get-Service` . Les noms de service s’affichent dans la colonne **nom** et les noms d’affichage apparaissent dans la colonne **DisplayName** .

## LIENS CONNEXES

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
