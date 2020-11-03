---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 237fe83af05de7a97113deb95a831d8295c9f4c4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201637"
---
# Enable-PSSessionConfiguration

## SYNOPSIS
Active les configurations de session sur l'ordinateur local.

## SYNTAX

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Enable-PSSessionConfiguration` applet de commande active les configurations de session inscrites qui ont été désactivées, par exemple à l’aide des `Disable-PSSessionConfiguration` `Disable-PSRemoting` applets de commande ou, ou le paramètre **AccessMode** de `Register-PSSessionConfiguration` . Il s'agit d'une applet de commande avancée conçue pour être utilisée par les administrateurs système pour gérer des configurations de sessions personnalisées pour leurs utilisateurs.

Sans paramètres, `Enable-PSSessionConfiguration` active la configuration **Microsoft. PowerShell** , qui est la configuration par défaut utilisée pour les sessions.

`Enable-PSSessionConfiguration` supprime le paramètre **Deny_All** du descripteur de sécurité des configurations de session affectées, active l’écouteur qui accepte les demandes sur n’importe quelle adresse IP, puis redémarre le service WinRM. À compter de PowerShell 3,0, `Enable-PSSessionConfiguration` définit également la valeur de la propriété **Enabled** de la configuration de session ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` ) sur true. Toutefois, `Enable-PSSessionConfiguration` ne supprime pas ou ne modifie **Network_Deny_All** pas le `AccessMode=Local` paramètre de descripteur de sécurité Network_Deny_All () qui autorise uniquement les utilisateurs de l’ordinateur local à utiliser la configuration de session.

## EXEMPLES

### Exemple 1 : réactiver la session par défaut

Cet exemple réactive la configuration de session **Microsoft. PowerShell** par défaut sur l’ordinateur.

```powershell
Enable-PSSessionConfiguration
```

### Exemple 2 : réactiver les sessions spécifiées

Cet exemple réactive les configurations de session **MaintenanceShell** et **AdminShell** sur l’ordinateur.

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### Exemple 3 : réactiver toutes les sessions

Cet exemple réactive toutes les configurations de session sur l’ordinateur. Ces commandes sont équivalentes.
Par conséquent, vous pouvez utiliser l’une ou l’autre.

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

`Enable-PSSessionConfiguration` ne génère pas d’erreur si vous activez une configuration de session déjà activée.

### Exemple 4 : réactiver une session et spécifier un nouveau descripteur de sécurité

Cet exemple réactive la configuration de session **MaintenanceShell** et spécifie un nouveau descripteur de sécurité pour la configuration.

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## PARAMETERS

### -Force

Indique que l’applet de commande ne vous invite pas à confirmer et à redémarrer le service WinRM sans demander confirmation. Le redémarrage du service permet d'appliquer la modification de configuration.

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

Spécifie les noms des configurations de session à activer. Entrez un ou plusieurs noms de configurations.
Les caractères génériques sont autorisés.

Vous pouvez également diriger une chaîne qui contient un nom de configuration ou un objet de configuration de session vers `Enable-PSSessionConfiguration` .

Si vous omettez ce paramètre, `Enable-PSSessionConfiguration` active la configuration de session **Microsoft. PowerShell** .

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

Indique que l’applet de commande ne redémarre pas le service.

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

### -SecurityDescriptorSddl

Spécifie un descripteur de sécurité avec lequel cette applet de commande remplace le descripteur de sécurité dans la configuration de session.

Si vous omettez ce paramètre, `Enable-PSSessionConfiguration` supprime uniquement l’élément refuser tout du descripteur de sécurité.

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

### -SkipNetworkProfileCheck

Indique que cette applet de commande active la configuration de session lorsque l’ordinateur se trouve sur un réseau public. Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local. Par défaut, `Enable-PSSessionConfiguration` échoue sur un réseau public.

Ce paramètre est conçu pour les versions clientes du système d’exploitation Windows. Les versions serveur du système d’exploitation Windows ont une règle de pare-feu de sous-réseau local pour les réseaux publics. Toutefois, si la règle de pare-feu de sous-réseau local est désactivée sur une version serveur du système d’exploitation Windows, ce paramètre la réactive.

Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module netsecurity. Pour plus d'informations, consultez `Enable-PSRemoting`.

Ce paramètre a été introduit dans PowerShell 3,0.

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

### Aucun

Cette applet de commande ne retourne pas d'objets.

## REMARQUES

Pour utiliser cette applet de commande, vous devez démarrer PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

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
