---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: 891c62692ce694e7e7238814a4dc30da59f7c98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205122"
---
# Get-PSSessionCapability

## SYNOPSIS
Obtient les fonctionnalités d’un utilisateur spécifique sur une configuration de session avec restriction.

## SYNTAX

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## Description

L’applet de commande **obtenir-PSSessionCapability** obtient les fonctionnalités d’un utilisateur spécifique sur une configuration de session avec restriction.
Utilisez cette applet de commande pour auditer les configurations de session personnalisées pour les utilisateurs.

À compter de Windows PowerShell 5,0, vous pouvez utiliser la propriété **RoleDefinitions** dans un fichier de configuration de session (. PSSC).
L’utilisation de cette propriété vous permet d’accorder aux utilisateurs des fonctionnalités différentes sur un point de terminaison unique en fonction de l’appartenance à un groupe.
L’applet de commande **obtenir-PSSessionCapability** réduit la complexité lors de l’audit de ces points de terminaison en vous permettant de déterminer les fonctionnalités exactes accordées à un utilisateur.

Par défaut, l’applet de commande **obtenir-PSSessionCapability** retourne une liste de commandes que l’utilisateur spécifié peut exécuter dans le point de terminaison spécifié.
Cela équivaut à l’exécution de la **commande de commande** dans le point de terminaison spécifié par l’utilisateur.
Quand elle est exécutée avec le paramètre *Full* , cette applet de commande retourne un objet **InitialSessionState** .
Cet objet contient des détails sur l’instance d’exécution PowerShell avec laquelle l’utilisateur spécifié interagit pour le point de terminaison spécifié.
Il comprend des informations telles que le mode de langage, la stratégie d’exécution et les variables d’environnement.

## EXEMPLES

### Exemple 1 : obtenir les commandes disponibles pour un utilisateur

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

Cet exemple retourne les commandes disponibles pour l’utilisateur CONTOSO\User lors de la connexion au point de terminaison con Endpoint1 sur l’ordinateur local.

### Exemple 2 : obtenir des détails sur une instance d’exécution pour un utilisateur

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

Cet exemple retourne des détails sur l’instance d’exécution avec laquelle l’utilisateur CONTOSO\User interagit lors de la connexion au point de terminaison avec restriction Endpoint1.

## PARAMETERS

### -ConfigurationName

Spécifie la configuration de session avec restriction (point de terminaison) que vous Inspectez.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

Indique que cette applet de commande retourne l’intégralité de l’état de session initial pour l’utilisateur spécifié sur le point de terminaison spécifié.

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

### -Username

Spécifie l’utilisateur dont vous Inspectez les fonctionnalités.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

### System. Management. Automation. AliasInfo

### System. Management. Automation. FunctionInfo

### System.Management.Automation.Runspaces.InitialSessionState

## REMARQUES

## LIENS CONNEXES

[New-PSRoleCapabilityFile](New-PSRoleCapabilityFile.md)

