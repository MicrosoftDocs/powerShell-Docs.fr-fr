---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: c55a7ef01171e63e8c64ee03446ca1bdcd838e2a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204757"
---
# Remove-Service

## SYNOPSIS
Supprime un service Windows.

## SYNTAX

### Nom (par défaut)

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Remove-Service` applet de commande supprime un service Windows dans le registre et dans la base de données du service.

L' `Remove-Service` applet de commande a été introduite dans PowerShell 6,0.

## EXEMPLES

### Exemple 1 : supprimer un service

Cela supprime un service nommé TestService.

```powershell
Remove-Service -Name "TestService"
```

### Exemple 2 : supprimer un service à l’aide du nom complet

Cet exemple supprime un service nommé TestService. La commande utilise `Get-Service` pour obtenir un objet qui représente le service TestService à l’aide du nom complet. L’opérateur de pipeline ( `|` ) dirige l’objet vers `Remove-Service` , qui supprime le service.

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## PARAMETERS

### -InputObject

Spécifie les objets **ServiceController** qui représentent les services à supprimer. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

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

Spécifie les noms des services à supprimer. Les caractères génériques sont autorisés.

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
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

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .

## LIENS CONNEXES

[Get-Service](Get-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
