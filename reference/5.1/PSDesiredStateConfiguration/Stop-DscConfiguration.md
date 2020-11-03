---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203086"
---
# Stop-DscConfiguration

## SYNOPSIS
Arrête une tâche de configuration en cours d’exécution.

## SYNTAX

### Tous

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Stop-DscConfiguration` applet de commande arrête une tâche de configuration en cours d’exécution. Spécifiez les ordinateurs auxquels cette applet de commande s’applique en utilisant des sessions Common Information Model (CIM). Si aucune tâche de configuration n’est en cours d’exécution, cette cmdlet renvoie un message d’avertissement.

`Stop-DscConfiguration` est uniquement disponible dans le cadre du [correctif cumulatif de novembre 2014 pour Windows RT 8,1, Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) à partir de la bibliothèque de support Microsoft. Avant d’utiliser cette applet de commande, passez en revue les informations [contenues dans Nouveautés de Windows PowerShell 5,0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)

## EXEMPLES

### Exemple 1 : arrêter une tâche de configuration

Dans cet exemple, une session CIM est créée à l’aide de l’applet de commande `New-CimSession` . L’objet **CimSession** est utilisé pour arrêter un travail de configuration en cours d’exécution.

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

`New-CimSession` utilise le paramètre **ComputerName** pour spécifier l’ordinateur SERVEUR01. Le paramètre Credential spécifie le compte **d'** utilisateur. L’objet **CimSession** est stocké dans la `$Session` variable. Lorsque la commande est exécutée, vous êtes invité à entrer le mot de passe du compte d’utilisateur.

`Stop-DscConfiguration` utilise le paramètre **CimSession** et l’objet stocké dans `$Session` pour arrêter la tâche de configuration.

## PARAMETERS

### -AsJob

Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan. Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).

Pour utiliser le paramètre **AsJob** , les ordinateurs locaux et distants doivent être configurés pour la communication à distance. Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir PowerShell avec l’option **exécuter en tant qu’administrateur** . Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

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

### -CimSession

Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant. Entrez un nom d’ordinateur ou un objet de session, tel que la sortie de `New-CimSession` ou `Get-CimSession` .

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

### -Confirm

`Stop-DscConfiguration` ne prend pas en charge le paramètre **Confirm** . Si le paramètre **Confirm** est utilisé, une erreur s’affiche.

Pour les applets de commande PowerShell qui prennent en charge la vérification, l’utilisation du paramètre vous invite à **confirmer** l’exécution d’une commande.

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

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

### -ThrottleLimit

Spécifie le nombre maximal d’opérations simultanées pouvant être établi pour exécuter l’applet de commande.

Si ce paramètre est omis ou si la valeur `0` est entrée, PowerShell calcule une limite de limitation optimale en fonction du nombre d’applets de commande CIM en cours d’exécution sur l’ordinateur. Le seuil de limitation s’applique uniquement à l’applet de commande active et non à la session ou à l’ordinateur.

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

### Aucun

## SORTIES

### Aucun

## REMARQUES

## LIENS CONNEXES

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Update-DscConfiguration](Update-DscConfiguration.md)

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/overview)
