---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: 5e43e9e23e52885325eaf1eb4d460a60dc110567
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205386"
---
# Unregister-PSSessionConfiguration

## SYNOPSIS
Supprime les configurations de sessions inscrites de l'ordinateur.

## SYNTAX

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Unregister-PSSessionConfiguration` applet de commande supprime les configurations de session inscrites de l’ordinateur. Cette applet de commande est conçue pour permettre aux administrateurs système de gérer les configurations de session personnalisées pour les utilisateurs.

Pour que la modification prenne effet, `Unregister-PSSessionConfiguration` redémarre le service **WinRM** . Pour empêcher le redémarrage, spécifiez le paramètre **NoServiceRestart** .

Si vous supprimez accidentellement les configurations de session **Microsoft. PowerShell** ou **Microsoft. powershell32** par défaut, utilisez l' `Enable-PSRemoting` applet de commande pour les restaurer. Pour plus d’informations, consultez [about_session_configurations](About/about_Session_Configurations.md).

## EXEMPLES

### Exemple 1 : supprimer une configuration de session

Cet exemple supprime la configuration de session **MaintenanceShell** de l’ordinateur.

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### Exemple 2 : supprimer une configuration de session et redémarrer le service WinRM

Dans cet exemple, nous supprimons la configuration **MaintenanceShell** et redémarrons le service WinRM. Le paramètre **force** supprime tous les messages utilisateur pour redémarrer le service **WinRM** sans demander confirmation.

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### Exemple 3 : supprimer toutes les configurations de session

Cet exemple montre deux façons de supprimer toutes les configurations de session sur l’ordinateur. Les deux commandes ont le même effet et peuvent être utilisées indifféremment.

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### Exemple 4 : annuler l’inscription sans redémarrage

Cet exemple montre l’effet de l’utilisation du paramètre **NoServiceRestart** pour empêcher le redémarrage d’un service qui perturberait les sessions sur l’ordinateur.

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

`Unregister-PSSessionConfiguration`Supprime la configuration de session **MaintenanceShell** .
Toutefois, étant donné que la commande utilise le paramètre **NoServiceRestart** , le service **WinRM** n’est pas redémarré et la modification n’est pas encore totalement effective.

Ensuite, `Get-PSSessionConfiguration` tente d’accéder à la session **MaintenanceShell** . Étant donné que la session a été supprimée de la table de ressources WS-Management, `Get-PSSessionConfiguration` ne peut pas la retourner.

L' `New-PSSession` applet de commande crée une session à l’aide de la configuration **MaintenanceShell** . La commande a réussi. Ensuite, redémarrez le service **WinRM** .

Enfin, l' `New-PSSession` applet de commande tente de créer une session qui utilise la configuration **MaintenanceShell** . Cette fois-ci, la session échoue car la configuration **MaintenanceShell** a été supprimée lors du redémarrage du service WinRM.

## PARAMETERS

### -Force

Indique que l’applet de commande ne vous invite pas à confirmer et à redémarrer le service **WinRM** sans demander confirmation. Le redémarrage du service permet d'appliquer la modification de configuration.

Pour éviter un redémarrage et supprimer l'invite de redémarrage, utilisez le paramètre **NoServiceRestart** .

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

### -Name

Spécifie les noms des configurations de sessions à supprimer. Entrez un nom de configuration de session ou un modèle de nom de configuration. Les caractères génériques sont autorisés. Ce paramètre est obligatoire.

Vous pouvez également diriger une configuration de session vers `Unregister-PSSessionConfiguration` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoServiceRestart

Indique que cette applet de commande ne redémarre pas le service **WinRM** et supprime l’invite de redémarrage du service.

Par défaut, lorsque vous exécutez une `Unregister-PSSessionConfiguration` commande, vous êtes invité à redémarrer le service **WinRM** pour que la modification prenne effet. Tant que le service **WinRM** n’est pas redémarré, les utilisateurs peuvent toujours utiliser la configuration de session non inscrite, même si `Get-PSSessionConfiguration` ne la trouve pas.

Pour redémarrer le service **WinRM** sans demander confirmation, spécifiez le paramètre **force** . Pour redémarrer manuellement le service **WinRM** , utilisez l' `Restart-Service` applet de commande.

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

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

### Microsoft. PowerShell. Commands. PSSessionConfigurationCommands # PSSessionConfiguration

Vous pouvez diriger un objet de configuration de session de `Get-PSSessionConfiguration` vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne pas d'objets.

## REMARQUES

Pour exécuter cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
