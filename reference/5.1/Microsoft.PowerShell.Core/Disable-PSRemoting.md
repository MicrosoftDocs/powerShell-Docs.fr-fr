---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202338"
---
# Disable-PSRemoting

## SYNOPSIS
Empêche les points de terminaison PowerShell de recevoir des connexions à distance.

## SYNTAX

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Disable-PSRemoting` applet de commande bloque l’accès à distance à toutes les configurations de point de terminaison de session Windows PowerShell sur l’ordinateur local. Cela comprend tous les points de terminaison créés par PowerShell 6 ou version ultérieure.

Pour réactiver l’accès à distance à toutes les configurations de session, utilisez l’applet de commande `Enable-PSRemoting` . Cela comprend tous les points de terminaison créés par PowerShell 6 ou version ultérieure. Pour activer l’accès à distance aux configurations de session sélectionnées, utilisez le paramètre **AccessMode** de l’applet de commande `Set-PSSessionConfiguration` .
Vous pouvez également utiliser les `Enable-PSSessionConfiguration` applets de commande et `Disable-PSSessionConfiguration` pour activer et désactiver les configurations de session pour tous les utilisateurs. Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

> [!NOTE]
> Même après `Disable-PSRemoting` l’exécution, vous pouvez toujours établir des connexions de bouclage sur l’ordinateur local. Une connexion de bouclage est une session PowerShell à distance qui provient de et se connecte à la même machine locale. Les sessions à distance provenant de sources externes restent bloquées. Pour les connexions de bouclage, vous devez utiliser des informations d’identification implicites avec le paramètre **EnableNetworkAccess** . Pour plus d’informations sur les connexions de bouclage, consultez [New-PSSession](New-PSSession.md).

Pour exécuter cette applet de commande, démarrez Windows PowerShell avec l’option **exécuter en tant qu’administrateur** .

## EXEMPLES

### Exemple 1 : empêcher l’accès à distance à toutes les configurations de session

Cet exemple empêche l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur.

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Exemple 2 : empêcher l’accès à distance à toutes les configurations de session sans invite de confirmation

Cet exemple empêche l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur sans demander confirmation.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
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
New-PSSession -ComputerName localhost
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
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

L' `Enable-PSRemoting` applet de commande réactive l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur. Le paramètre **force** supprime toutes les invites utilisateur et redémarre le service WinRM sans demander confirmation. La nouvelle sortie indique que les descripteurs de sécurité **AccessDenied** ont été supprimés de toutes les configurations de session.

### Exemple 5 : connexions de bouclage avec des configurations de point de terminaison de session désactivées

Cet exemple montre comment les configurations de point de terminaison sont désactivées et montre comment établir une connexion de bouclage à un point de terminaison désactivé. `Disable-PSRemoting` désactive toutes les configurations de point de terminaison de session PowerShell.

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

La première utilisation des `New-PSSession` tentatives de création d’une session à distance sur l’ordinateur local. Ce type de connexion traverse la pile réseau et n’est pas un bouclage. Par conséquent, la tentative de connexion au point de terminaison désactivé échoue avec une erreur **accès refusé** .

La deuxième utilisation de `New-PSSession` tente également de créer une session à distance sur l’ordinateur local.
Dans ce cas, elle est réussie, car il s’agit d’une connexion de bouclage qui contourne la pile réseau.

Une connexion de bouclage est créée lorsque les conditions suivantes sont remplies :

- Le nom de l’ordinateur auquel se connecter est « localhost ».
- Aucune information d’identification n’est transmise. L’utilisateur actuellement connecté (informations d’identification implicites) est utilisé pour la connexion.
- Le paramètre de commutateur **EnableNetworkAccess** est utilisé.

Pour plus d’informations sur les connexions de bouclage, consultez le document [New-PSSession](New-PSSession.md) .

### Exemple 6 : empêcher l’accès à distance aux configurations de session qui ont des descripteurs de sécurité personnalisés

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
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

Désormais `Get-PSSessionConfiguration` , les `Format-Table` applets de commande et indiquent qu’un descripteur de sécurité **AccessDenied** pour tous les utilisateurs du réseau est ajouté à toutes les configurations de session, y compris la configuration de la session de **test** . Bien que les autres descripteurs de sécurité ne soient pas modifiés, le descripteur de sécurité « network_deny_all » est prioritaire. Cela est illustré par la tentative d’utilisation `New-PSSession` de pour se connecter à la configuration de la session de **test** .

### Exemple 7 : réactiver l’accès à distance aux configurations de session sélectionnées

Cet exemple illustre comment réactiver l'accès à distance uniquement pour les configurations de session sélectionnées. Après la désactivation de toutes les configurations de session, nous réactivons une session spécifique.

L' `Set-PSSessionConfiguration` applet de commande est utilisée pour modifier **Microsoft.** Configuration de session ServerManager. Le paramètre **AccessMode** avec la valeur **Remote** Reactive l’accès à distance à la configuration.

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
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

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
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

### Aucun

Vous ne pouvez pas diriger d’objets vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

- La désactivation des configurations de session n’annule pas toutes les modifications apportées par les `Enable-PSRemoting` applets de commande ou `Enable-PSSessionConfiguration` . Vous devrez peut-être annuler manuellement les modifications suivantes.

  1. Arrêter et désactiver le service WinRM.
  2. Supprimer l'écouteur qui accepte les demandes sur toutes les adresses IP.
  3. Désactiver les exceptions de pare-feu pour les communications WS-Management.
  4. Restaurer la valeur de LocalAccountTokenFilterPolicy sur 0, ce qui restreint l'accès à distance aux membres du groupe Administrateurs sur l'ordinateur.

  Une configuration de session est un groupe de paramètres qui définissent l'environnement d'une session. Toutes les sessions qui se connectent à l'ordinateur doivent utiliser l'une des configurations de session enregistrées sur l'ordinateur. En refusant l'accès à distance à toutes les configurations de session, vous empêchez effectivement les utilisateurs distants d'établir des sessions de connexion à l'ordinateur.

  Dans Windows PowerShell 2,0, `Disable-PSRemoting` ajoute une entrée Deny_All aux descripteurs de sécurité de toutes les configurations de session. Ce paramètre empêche tous les utilisateurs de créer des sessions gérées par l’utilisateur sur l’ordinateur local. Dans Windows PowerShell 3,0, `Disable-PSRemoting` ajoute une entrée Network_Deny_All aux descripteurs de sécurité de toutes les configurations de session. Ce paramètre empêche les utilisateurs d’autres ordinateurs de créer des sessions gérées par l’utilisateur sur l’ordinateur local, mais permet aux utilisateurs de l’ordinateur local de créer des sessions de bouclage gérées par l’utilisateur.

  Dans Windows PowerShell 2,0, `Disable-PSRemoting` est l’équivalent de `Disable-PSSessionConfiguration -Name *` . Dans Windows PowerShell 3,0 et versions ultérieures, `Disable-PSRemoting` est l’équivalent de `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
