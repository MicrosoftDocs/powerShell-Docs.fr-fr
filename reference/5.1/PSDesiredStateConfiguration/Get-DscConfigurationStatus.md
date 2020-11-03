---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203969"
---
# Get-DscConfigurationStatus

## SYNOPSIS
Récupère des données sur les exécutions de configuration terminées.

## SYNTAX

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-DscConfigurationStatus** récupère des informations détaillées sur les exécutions de la configuration terminée sur le système.
Par défaut, elle retourne les informations relatives à la dernière exécution de la configuration.
Cette applet de commande est utile pour rechercher des informations historiques sur les exécutions de configuration, telles que le moment où les configurations ont été exécutées, l’état des exécutions, le nombre de ressources dans les configurations et les ressources qui ont réussi ou échoué.

## EXEMPLES

### Exemple 1 : récupérer des informations sur la dernière exécution de la configuration

```
PS C:\> Get-DscConfigurationStatus
```

Cette commande obtient des informations sur la dernière exécution de la configuration.

### Exemple 2 : récupérer des informations sur toutes les configurations

```
PS C:\> Get-DscConfigurationStatus -All
```

Cette commande obtient des informations sur toutes les configurations qui ont été exécutées sur le système, y compris la vérification de cohérence de la configuration d’état souhaité (DSC) Windows PowerShell.

### Exemple 3 : obtenir des informations sur la configuration exécutée sur un ordinateur distant

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

Cette commande obtient les détails de l’exécution de la configuration de l’ordinateur distant nommé SERVEUR01.
Le transport WSMan est utilisé pour se connecter à l’ordinateur distant et nécessite que l’utilisateur qui se connecte soit un administrateur sur l’ordinateur distant.

## PARAMETERS

### -All
Indique que cette applet de commande récupère des informations sur toutes les exécutions de configuration sur l’ordinateur, y compris l’application de configuration et la vérification de cohérence.

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

### -AsJob
Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan.

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

### -CimSession
Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.
Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) ou [CimSession](/powershell/module/cimcmdlets/get-cimsession) .
La valeur par défaut est la session active sur l’ordinateur local.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.
Si ce paramètre est omis ou si la valeur `0` est entrée, Windows PowerShell calcule une limite de limitation optimale pour l’applet de commande en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur.
Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
