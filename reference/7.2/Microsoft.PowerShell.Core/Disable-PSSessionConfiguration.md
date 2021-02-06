---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: c2f88431c0a09a2d4093c6523467a812812c10bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597335"
---
# Disable-PSSessionConfiguration

## SYNOPSIS
Désactive les configurations de session sur l'ordinateur local.

## SYNTAXE

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Disable-PSSessionConfiguration` applet de commande désactive les configurations de session sur l’ordinateur local, ce qui empêche tous les utilisateurs d’utiliser les configurations de session pour créer des sessions gérées par l’utilisateur (**sessions PSSession**) sur l’ordinateur local. Il s'agit d'une applet de commande avancée conçue pour être utilisée par les administrateurs système pour gérer des configurations de sessions personnalisées pour leurs utilisateurs.

À compter de PowerShell 3,0, l’applet de commande `Disable-PSSessionConfiguration` définit le paramètre **Enabled** de la configuration de session ( `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` ) sur false.

Dans PowerShell 2,0, l' `Disable-PSSessionConfiguration` applet de commande ajoute une entrée **Deny_All** au descripteur de sécurité d’une ou plusieurs configurations de session inscrites.

Sans paramètres, `Disable-PSSessionConfiguration` désactive la configuration **Microsoft. PowerShell** , la configuration par défaut utilisée pour les sessions. À moins que l'utilisateur ne spécifie une autre configuration, les utilisateurs locaux et distants ne peuvent pas créer de sessions qui se connectent à l'ordinateur.

Pour désactiver toutes les configurations de session sur l’ordinateur, utilisez `Disable-PSRemoting` .

## EXEMPLES

### Exemple 1 : désactiver la configuration par défaut

Cet exemple désactive la configuration de session Microsoft. PowerShell.

```powershell
Disable-PSSessionConfiguration
```

### Exemple 2 : désactiver toutes les configurations de sessions inscrites

Cet exemple désactive toutes les configurations de session inscrites sur l’ordinateur.

```powershell
Disable-PSSessionConfiguration -Name *
```

### Exemple 3 : désactiver les configurations de session par nom

Cet exemple désactive toutes les configurations de session dont les noms commencent par Microsoft. Le paramètre **force** supprime toutes les invites utilisateur de l’applet de commande.

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### Exemple 4 : désactiver les configurations de session à l’aide du pipeline

Cet exemple désactive les configurations de session **MaintenanceShell** et **AdminShell** . L’opérateur de pipeline (|) envoie les résultats d’un `Get-PSSessionConfiguration` à `Disable-PSSessionConfiguration` .

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### Exemple 5 : effets de la désactivation d’une configuration de session

Cet exemple montre les autorisations avant et après l’exécution `Disable-PSSessionConfiguration` et l’effet de la désactivation d’une configuration de session.

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> La désactivation de la configuration ne vous empêche pas de modifier la configuration à l’aide de l’applet de commande `Set-PSSessionConfiguration` . Elle empêche uniquement l’utilisation de la configuration.

## PARAMETERS

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

Spécifie un tableau de noms de configurations de session à désactiver. Entrez un ou plusieurs noms de configurations. Les caractères génériques sont autorisés. Vous pouvez également diriger une chaîne qui contient un nom de configuration ou un objet de configuration de session vers `Disable-PSSessionConfiguration` .

Si vous omettez ce paramètre, `Disable-PSSessionConfiguration` désactive la configuration de session Microsoft. PowerShell.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -NoServiceRestart

Utilisé pour empêcher le redémarrage du service WSMan. Il n’est pas nécessaire de redémarrer le service pour désactiver la configuration.

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

### Microsoft. PowerShell. Commands. PSSessionConfigurationCommands # PSSessionConfiguration, System. String

Vous pouvez diriger un objet de configuration de session ou une chaîne qui contient le nom d’une configuration de session vers cette applet de commande.

## SORTIES

### None

Cette applet de commande ne retourne pas d'objets.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

Pour exécuter cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .

## LIENS CONNEXES

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
