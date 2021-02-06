---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 4410c8f41fffcaae9c9f447af246f335033d53a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596508"
---
# Disable-PSRemoting

## SYNOPSIS
Empêche les points de terminaison PowerShell de recevoir des connexions à distance.

## SYNTAXE

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Disable-PSRemoting` applet de commande bloque l’accès à distance à toutes les configurations de point de terminaison de session PowerShell version 6 et ultérieures sur l’ordinateur local. Elle n’affecte pas les configurations de point de terminaison Windows PowerShell. Pour désactiver les configurations de point de terminaison de session Windows PowerShell, exécutez `Disable-PSRemoting` la commande à partir d’une session Windows PowerShell.

Pour réactiver l’accès à distance à toutes les configurations de point de terminaison de session PowerShell version 6 et ultérieures, utilisez l’applet de commande `Enable-PSRemoting` . Pour réactiver l’accès à distance à toutes les configurations de point de terminaison de session Windows PowerShell, exécutez `Enable-PSRemoting` à partir d’une session Windows PowerShell.

> [!NOTE]
> Si vous souhaitez désactiver tous les accès à distance PowerShell à un ordinateur Windows local, vous devez exécuter cette commande à partir d’un dans une session PowerShell version 6 ou ultérieure et à partir d’une session Windows PowerShell. Windows PowerShell est installé sur tous les ordinateurs Windows par défaut.

Pour désactiver et réactiver l’accès à distance aux configurations de point de terminaison de session spécifiques, utilisez les `Enable-PSSessionConfiguration` applets de commande et `Disable-PSSessionConfiguration` . Pour définir des configurations d’accès spécifiques à des points de terminaison individuels, utilisez l’applet de commande `Set-PSSessionConfiguration` avec le paramètre **AccessMode** . Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

> [!NOTE]
> Même après `Disable-PSRemoting` l’exécution, vous pouvez toujours établir des connexions de bouclage sur l’ordinateur local. Une connexion de bouclage est une session PowerShell à distance qui provient de et se connecte à la même machine locale. Les sessions à distance provenant de sources externes restent bloquées. Pour les connexions de bouclage, vous devez utiliser des informations d’identification implicites avec le paramètre **EnableNetworkAccess** . Pour plus d’informations sur les connexions de bouclage, consultez [New-PSSession](New-PSSession.md).

Cette applet de commande est disponible uniquement sur la plateforme Windows. Elle n’est pas disponible dans les versions Linux ou macOS de PowerShell. Pour exécuter cette applet de commande, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

## EXEMPLES

### Exemple 1 : empêcher l’accès à distance à toutes les configurations de session PowerShell

Cet exemple empêche l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur.

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Exemple 2 : empêcher l’accès à distance à toutes les configurations de session PowerShell sans invite de confirmation

Cet exemple empêche l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur sans demander confirmation.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Exemple 3 : effets de l’exécution de cette applet de commande

Cet exemple montre l’effet de l’utilisation de l’applet de commande `Disable-PSRemoting` . Pour exécuter cette séquence de commandes, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

Après la désactivation des configurations de sessions, l' `New-PSSession` applet de commande tente de créer une session à distance sur l’ordinateur local (également appelé « bouclage »). Étant donné que l’accès à distance est désactivé sur l’ordinateur local, la commande échoue.

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### Exemple 4 : effets de l’exécution de cette applet de commande et Enable-PSRemoting

Cet exemple montre l’effet sur les configurations de session de à l’aide des `Disable-PSRemoting` applets de commande et `Enable-PSRemoting` .

`Disable-PSRemoting` est utilisé pour désactiver l’accès à distance à toutes les configurations de point de terminaison de session PowerShell. Le paramètre **Force** supprime toutes les invites utilisateur. Les `Get-PSSessionConfiguration` applets de commande et `Format-Table` affichent les configurations de session sur l’ordinateur.

La sortie indique que l’accès aux configurations de point de terminaison est refusé à tous les utilisateurs distants distants disposant d’un jeton réseau. Le groupe Administrateurs sur l’ordinateur local est autorisé à accéder aux configurations de point de terminaison, à condition qu’elles se connectent localement (également appelées « bouclage ») et qu’elles utilisent des informations d’identification implicites.

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

L' `Enable-PSRemoting` applet de commande réactive l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur. Le paramètre **force** supprime toutes les invites utilisateur et redémarre le service WinRM sans demander confirmation. La nouvelle sortie indique que les descripteurs de sécurité **AccessDenied** ont été supprimés de toutes les configurations de session.

### Exemple 5 : connexions de bouclage avec des configurations de point de terminaison de session désactivées

Cet exemple montre comment les configurations de point de terminaison sont désactivées et montre comment établir une connexion de bouclage à un point de terminaison désactivé. `Disable-PSRemoting` désactive toutes les configurations de point de terminaison de session PowerShell.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

La première utilisation des `New-PSSession` tentatives de création d’une session à distance sur l’ordinateur local. Le paramètre **ConfigurationName** est utilisé pour spécifier un point de terminaison PowerShell désactivé. Les informations d’identification sont passées explicitement à la commande via le paramètre **Credential** . Ce type de connexion traverse la pile réseau et n’est pas un bouclage. Par conséquent, la tentative de connexion au point de terminaison désactivé échoue avec une erreur **accès refusé** .

La deuxième utilisation de `New-PSSession` tente également de créer une session à distance sur l’ordinateur local.
Dans ce cas, elle est réussie, car il s’agit d’une connexion de bouclage qui contourne la pile réseau.

Une connexion de bouclage est créée lorsque les conditions suivantes sont remplies :

- Le nom de l’ordinateur auquel se connecter est « localhost ».
- Aucune information d’identification n’est transmise. L’utilisateur actuellement connecté (informations d’identification implicites) est utilisé pour la connexion.
- Le paramètre de commutateur **EnableNetworkAccess** est utilisé.

Pour plus d’informations sur les connexions de bouclage, consultez le document [New-PSSession](New-PSSession.md) .

### Exemple 6 : désactivation de toutes les configurations de point de terminaison de communication à distance PowerShell

Cet exemple montre comment l’exécution de la `Disable-PSRemoting` commande n’affecte pas les configurations de point de terminaison Windows PowerShell. `Get-PSSessionConfiguration` exécuter dans Windows PowerShell affiche toutes les configurations de point de terminaison. Nous voyons que les configurations de point de terminaison Windows PowerShell ne sont pas désactivées.

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

Pour désactiver ces configurations de point de terminaison, la `Disable-PSRemoting` commande doit être exécutée à partir d’une session Windows PowerShell. À présent, `Get-PSSessionConfiguration` exécuter à partir de Windows PowerShell montre que toutes les configurations de point de terminaison sont désactivées.

### Exemple 7 : empêcher l’accès à distance aux configurations de session qui ont des descripteurs de sécurité personnalisés

Cet exemple montre que l' `Disable-PSRemoting` applet de commande désactive l’accès à distance à toutes les configurations de session qui incluent des configurations de session avec des descripteurs de sécurité personnalisés.

`Register-PSSessionConfiguration` crée la configuration de la session de **test** . Le paramètre **filePath** spécifie un fichier de configuration de session qui personnalise la session. Le paramètre **ShowSecurityDescriptorUI** affiche une boîte de dialogue qui définit les autorisations de la configuration de session. Dans la boîte de dialogue autorisations, nous créons des autorisations d’accès complet personnalisées pour l’utilisateur indiqué.

Les `Get-PSSessionConfiguration` applets de commande et `Format-Table` affichent les configurations de session et leurs propriétés. La sortie indique que la configuration de la session de **test** autorise un accès interactif et des autorisations spéciales pour l’utilisateur indiqué.

`Disable-PSRemoting` désactive l’accès à distance à toutes les configurations de session.

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

Désormais `Get-PSSessionConfiguration` , les `Format-Table` applets de commande et indiquent qu’un descripteur de sécurité **AccessDenied** pour tous les utilisateurs du réseau est ajouté à toutes les configurations de session, y compris la configuration de la session de **test** . Bien que les autres descripteurs de sécurité ne soient pas modifiés, le descripteur de sécurité « network_deny_all » est prioritaire. Cela est illustré par la tentative d’utilisation `New-PSSession` de pour se connecter à la configuration de la session de **test** .

### Exemple 8 : réactiver l’accès à distance aux configurations de session sélectionnées

Cet exemple illustre comment réactiver l'accès à distance uniquement pour les configurations de session sélectionnées. Après la désactivation de toutes les configurations de session, nous réactivons une session spécifique.

L' `Set-PSSessionConfiguration` applet de commande est utilisée pour modifier la configuration de session **PowerShell. 6** . Le paramètre **AccessMode** avec la valeur **Remote** Reactive l’accès à distance à la configuration.

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

## PARAMETERS

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

### None

Vous ne pouvez pas diriger d’objets vers cette applet de commande.

## SORTIES

### None

Cette applet de commande ne génère aucune sortie.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

- La désactivation des configurations de session n’annule pas toutes les modifications apportées par les `Enable-PSRemoting` applets de commande ou `Enable-PSSessionConfiguration` . Vous devrez peut-être annuler manuellement les modifications suivantes.

  1. Arrêter et désactiver le service WinRM.
  2. Supprimer l'écouteur qui accepte les demandes sur toutes les adresses IP.
  3. Désactiver les exceptions de pare-feu pour les communications WS-Management.
  4. Restaurer la valeur de LocalAccountTokenFilterPolicy sur 0, ce qui restreint l'accès à distance aux membres du groupe Administrateurs sur l'ordinateur.

- Une configuration de point de terminaison de session est un groupe de paramètres qui définissent l’environnement d’une session.
  Chaque session qui se connecte à l’ordinateur doit utiliser l’une des configurations de point de terminaison de session inscrites sur l’ordinateur. En refusant l’accès à distance à toutes les configurations de point de terminaison de session, vous empêchez efficacement les utilisateurs distants d’établir des sessions qui se connectent à l’ordinateur.

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
