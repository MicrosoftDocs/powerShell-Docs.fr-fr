---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 5c7783cb6f865aead9aae7ae0df77d9ee2db7b16
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391355"
---
# Receive-PSSession

## SYNOPSIS

Obtient les résultats des commandes dans des sessions déconnectées

## SYNTAXE

### Session (par défaut)

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### Id

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ComputerSessionName

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerInstanceId

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriSessionName

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Session

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

L' `Receive-PSSession` applet de commande obtient les résultats des commandes qui s’exécutent dans les sessions PowerShell ( **PSSession** ) qui ont été déconnectées. Si la session est actuellement connectée, `Receive-PSSession` obtient les résultats des commandes qui étaient en cours d’exécution lorsque la session a été déconnectée. Si la session est encore déconnectée, `Receive-PSSession` se connecte à la session, reprend toutes les commandes qui ont été interrompues et obtient les résultats des commandes en cours d’exécution dans la session.

Cette applet de commande a été introduite dans PowerShell 3,0.

Vous pouvez utiliser une `Receive-PSSession` en plus de ou au lieu d’une `Connect-PSSession` commande.
`Receive-PSSession` peut se connecter à une session déconnectée ou reconnectée qui a été démarrée dans d’autres sessions ou sur d’autres ordinateurs.

`Receive-PSSession` fonctionne sur les **sessions PSSession** qui ont été déconnectées intentionnellement à l’aide de l’applet de commande `Disconnect-PSSession` ou du `Invoke-Command` paramètre **InDisconnectedSession** . Ou déconnectés involontairement par une interruption du réseau.

Si vous utilisez l' `Receive-PSSession` applet de commande pour vous connecter à une session dans laquelle aucune commande n’est en cours d’exécution ou suspendue, `Receive-PSSession` se connecte à la session, mais ne retourne aucune sortie ni erreur.

Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).

Certains exemples utilisent la projection pour réduire la longueur de ligne et améliorer la lisibilité. Pour plus d’informations, consultez [about_Splatting](./About/about_Splatting.md).

## EXEMPLES

### Exemple 1 : se connecter à une session PSSession

Cet exemple se connecte à une session sur un ordinateur distant et obtient les résultats des commandes qui s’exécutent dans une session.

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

Le `Receive-PSSession` spécifie l’ordinateur distant avec le paramètre **ComputerName** . Le paramètre **Name** identifie la session ITTask sur l’ordinateur SERVEUR01. L’exemple obtient les résultats des commandes qui étaient en cours d’exécution dans la session ITTask.

Étant donné que la commande n’utilise pas le paramètre **distarget** , les résultats s’affichent sur la ligne de commande.

### Exemple 2 : obtenir les résultats de toutes les commandes sur les sessions déconnectées

Cet exemple obtient les résultats de toutes les commandes exécutées dans toutes les sessions déconnectées sur deux ordinateurs distants.

Si une session n’a pas été déconnectée ou n’exécute pas de commandes, `Receive-PSSession` ne se connecte pas à la session et ne retourne aucune sortie ni erreur.

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

`Get-PSSession` utilise le paramètre **ComputerName** pour spécifier les ordinateurs distants. Les objets sont envoyés dans le pipeline à `Receive-PSSession` .

### Exemple 3 : obtenir les résultats d’un script en cours d’exécution dans une session

Cet exemple utilise l' `Receive-PSSession` applet de commande pour obtenir les résultats d’un script qui s’exécutait dans la session d’un ordinateur distant.

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

La commande utilise les paramètres **ComputerName** et **Name** pour identifier la session déconnectée.
Elle utilise le paramètre **distarget** avec la valeur Job pour demander `Receive-PSSession` à de retourner les résultats en tant que tâche. Le paramètre **JobName** spécifie un nom pour le travail dans la session reconnectée.
Le paramètre **Credential** exécute la `Receive-PSSession` commande à l’aide des autorisations d’un administrateur de domaine.

La sortie indique que `Receive-PSSession` a retourné les résultats sous la forme d’un travail dans la session active. Pour obtenir les résultats du travail, utilisez une `Receive-Job` commande

### Exemple 4 : obtenir des résultats après une panne réseau

Cet exemple utilise l' `Receive-PSSession` applet de commande pour obtenir les résultats d’un travail après qu’une panne du réseau a interrompu une connexion de session. PowerShell tente automatiquement de reconnecter la session une fois par seconde pendant les quatre minutes suivantes et abandonne l’effort uniquement si toutes les tentatives de l’intervalle de quatre minutes échouent.

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

L' `New-PSSession` applet de commande crée une session sur l’ordinateur SERVEUR01 et enregistre la session dans la `$s` variable. La `$s` variable indique que l' **État** est ouvert et que la **disponibilité** est disponible. Ces valeurs indiquent que vous êtes connecté à la session et que vous pouvez exécuter des commandes dans la session.

L' `Invoke-Command` applet de commande exécute un script dans la session de la `$s` variable. Le script commence à s'exécuter et à retourner des données, mais une panne réseau se produit, qui interrompt la session. L'utilisateur doit quitter la session et redémarrer l'ordinateur local.

Lorsque l’ordinateur redémarre, l’utilisateur démarre PowerShell et exécute une `Get-PSSession` commande pour obtenir les sessions sur l’ordinateur SERVEUR01. La sortie indique que la session **Active Directory** existe toujours sur l’ordinateur SERVEUR01. L' **État** indique que la session **Active Directory** est déconnectée. La valeur de **disponibilité** None indique que la session n’est connectée à aucune session cliente.

L' `Receive-PSSession` applet de commande se reconnecte à la session **ad** et obtient les résultats du script qui s’est exécuté dans la session. La commande utilise le paramètre **distarget** pour demander les résultats dans un travail nommé **ADJob**. La commande retourne un objet de traitement et la sortie indique que le script est toujours en cours d’exécution.

L' `Get-PSSession` applet de commande est utilisée pour vérifier l’état de la tâche. La sortie confirme que l' `Receive-PSSession` applet de commande s’est reconnectée à la session **ad** , qui est désormais ouverte et disponible pour les commandes. Et, le script a repris l’exécution et obtient les résultats du script.

### Exemple 5 : reconnexion à des sessions déconnectées

Cet exemple utilise l' `Receive-PSSession` applet de commande pour se reconnecter aux sessions qui ont été intentionnellement déconnectées et obtenir les résultats des tâches qui étaient en cours d’exécution dans les sessions.

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

L' `Invoke-Command` applet de commande exécute un script sur trois ordinateurs distants. Étant donné que le script rassemble et synthétise les données de plusieurs bases de données, le script prend souvent une durée prolongée. La commande utilise le paramètre **InDisconnectedSession** qui démarre les scripts, puis déconnecte immédiatement les sessions. Le paramètre **SessionOption** étend la valeur **IdleTimeout** de la session déconnectée. Les sessions déconnectées sont considérées comme inactives à partir du moment où elles sont déconnectées. Il est important de définir le délai d’inactivité suffisamment longtemps pour que les commandes puissent se terminer et que vous puissiez vous reconnecter à la session. Vous pouvez définir la valeur **IdleTimeout** uniquement lorsque vous créez la **session PSSession** et la modifier uniquement lorsque vous vous déconnectez. Vous ne pouvez pas modifier la valeur **IdleTimeout** quand vous vous connectez à une **session PSSession** ou recevez ses résultats. Après l’exécution de la commande, l’utilisateur quitte PowerShell et ferme l’ordinateur.

Le lendemain, l’utilisateur reprend Windows, démarre PowerShell et utilise `Get-PSSession` pour recevoir les sessions dans lesquelles les scripts étaient en cours d’exécution. La commande identifie les sessions par le nom d’ordinateur, le nom de session et le nom de la configuration de session, et enregistre les sessions dans la `$s` variable. La valeur de la `$s` variable s’affiche et indique que les sessions sont déconnectées, mais qu’elles ne sont pas occupées.

L' `Receive-PSSession` applet de commande se connecte aux sessions dans la `$s` variable et obtient les résultats.
La commande enregistre les résultats dans la `$Results` variable. La `$s` variable s’affiche et indique que les sessions sont connectées et disponibles pour les commandes.

Les résultats du script dans la `$Results` variable s’affichent dans la console PowerShell. Si l’un des résultats est inattendu, l’utilisateur peut exécuter des commandes dans les sessions pour examiner la cause racine.

### Exemple 6 : exécution d’un travail dans une session déconnectée

Cet exemple montre ce qui arrive à un travail qui s’exécute dans une session déconnectée.

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

L' `New-PSSession` applet de commande crée la session de test sur l’ordinateur SERVEUR01. La commande enregistre la session dans la variable `$s`.

L' `Invoke-Command` applet de commande exécute une commande dans la session de la `$s` variable. La commande utilise le paramètre **AsJob** pour exécuter la commande en tant que tâche et crée l’objet de traitement dans la session active.
La commande retourne un objet de traitement qui est enregistré dans la `$j` variable. La `$j` variable affiche l’objet de traitement.

L’objet de session dans la `$s` variable est envoyé vers le pipeline vers `Disconnect-PSSession` et la session est déconnectée.

La `$j` variable s’affiche et montre l’effet de la déconnexion de l’objet de traitement dans la `$j` variable. L'état de la tâche est maintenant Déconnecté.

La `Receive-Job` est exécutée sur la tâche dans la `$j` variable. La sortie indique que la tâche a commencé à retourner une sortie avant la déconnexion de la session et que la tâche a été déconnectée.

L' `Connect-PSSession` applet de commande est exécutée dans la même session cliente. La commande se reconnecte à la session de test sur l’ordinateur SERVEUR01 et enregistre la session dans la `$s2` variable.

L' `Receive-PSSession` applet de commande obtient les résultats du travail qui s’exécutait dans la session. Étant donné que la commande est exécutée dans la même session, `Receive-PSSession` retourne les résultats sous la forme d’un travail par défaut et réutilise le même objet de traitement. La commande enregistre la tâche dans la `$j2` variable. L' `Receive-Job` applet de commande obtient les résultats de la tâche dans la `$j` variable.

## PARAMÈTRES

### -AllowRedirection

Indique que cette applet de commande autorise la redirection de cette connexion vers un autre Uniform Resource Identifier (URI).

Quand vous utilisez le paramètre **ConnectionURI** , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI. Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.

Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount**. Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la `$PSSessionOption` variable de préférence. La valeur par défaut est 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Spécifie une application. Cette applet de commande se connecte uniquement aux sessions qui utilisent l’application spécifiée.

Entrez le segment de nom d'application de l'URI de connexion. Par exemple, dans l’URI de connexion suivant, WSMan est le nom de l’application : `http://localhost:5985/WSMAN` .

Le nom d'application d'une session est stocké dans la propriété **Runspace.ConnectionInfo.AppName** de la session.

La valeur du paramètre est utilisée pour sélectionner et filtrer les sessions. Elle ne modifie pas l’application utilisée par la session.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur dans la commande pour se reconnecter à une session déconnectée. Les valeurs valides pour ce paramètre sont :

- Default
- De base
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

La valeur par défaut est Default.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> L’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Les certificats peuvent être mappés uniquement aux comptes d’utilisateurs locaux et ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez une `Get-Item` `Get-ChildItem` commande ou dans le `Cert:` lecteur PowerShell.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie l'ordinateur sur lequel est stockée la session déconnectée. Les sessions sont stockées sur l’ordinateur qui se trouve à l’extrémité du serveur ou de la réception d’une connexion. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet (FQDN) d’un ordinateur.
Les caractères génériques ne sont pas autorisés. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ), `$env:COMPUTERNAME` ou localhost.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConfigurationName

Spécifie le nom d’une configuration de session. Cette applet de commande se connecte uniquement aux sessions qui utilisent la configuration de session spécifiée.

Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session. Si vous spécifiez uniquement le nom de la configuration, l'URI de schéma suivant est ajouté :

`http://schemas.microsoft.com/powershell`.

Le nom de configuration d'une session est stocké dans la propriété **ConfigurationName** de la session.

La valeur du paramètre est utilisée pour sélectionner et filtrer les sessions. Elle ne modifie pas la configuration de session utilisée par la session.

Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](./About/about_Session_Configurations.md).

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Spécifie un URI qui définit le point de terminaison de connexion utilisé pour se reconnecter à la session déconnectée.

L’URI doit être complet. Le format de la chaîne est le suivant :

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

La valeur par défaut est la suivante :

`http://localhost:5985/WSMAN`

Si vous ne spécifiez pas d’URI de connexion, vous pouvez utiliser les paramètres **UseSSL** , **ComputerName** , **port** et **applicationName** pour spécifier les valeurs d’URI de connexion.

Les valeurs valides du segment **Transport** de l'URI sont HTTP et HTTPS. Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs. Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.

Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Spécifie l’ID d’une session déconnectée. Le paramètre **ID** fonctionne uniquement lorsque la session déconnectée a déjà été connectée à la session active.

Ce paramètre est valide, mais il n’est pas effectif, lorsque la session est stockée sur l’ordinateur local, mais n’a pas été connectée à la session active.

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -InstanceId

Spécifie l'ID d'instance de la session déconnectée. L’ID d’instance est un GUID qui identifie de façon unique une **session PSSession** sur un ordinateur local ou distant. L’ID d’instance est stocké dans la propriété **InstanceID** de la **session PSSession**.

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobName

Spécifie un nom convivial pour le travail `Receive-PSSession` retourné par.

`Receive-PSSession` retourne un travail lorsque la valeur du paramètre de l’objet de la **cible** est Job ou que le travail en cours d’exécution dans la session déconnectée a été démarré dans la session active.

Si le travail en cours d’exécution dans la session déconnectée a démarré dans la session active, PowerShell réutilise l’objet de traitement d’origine dans la session et ignore la valeur du paramètre **JobName** .

Si le travail en cours d’exécution dans la session déconnectée a été démarré dans une autre session, PowerShell crée un nouvel objet de traitement. Il utilise un nom par défaut, mais vous pouvez utiliser ce paramètre pour modifier le nom.

Si la valeur par défaut ou la valeur explicite du paramètre **untarget** n’est pas Job, la commande est réussie, mais le paramètre **JobName** n’a aucun effet.

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

### -Name

Spécifie le nom convivial de la session déconnectée.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -En-dessous

Détermine la façon dont les résultats de la session sont retournés. Les valeurs valides pour ce paramètre sont :

- **Travail**. retourne les résultats de façon asynchrone dans un objet de traitement. Vous pouvez utiliser le paramètre **JobName** pour spécifier un nom ou un nouveau nom pour la tâche.
- **Hôte**. retourne les résultats dans la ligne de commande (synchrone). Si la commande est reprise ou si les résultats se composent d'un grand nombre d'objets, la réponse peut être retardée.

La valeur par défaut du paramètre de **précible** est host. Si la commande qui est reçue dans une session déconnectée a été démarrée dans la session active, la valeur par défaut du paramètre de la **cible** est le formulaire dans lequel la commande a été démarrée. Si la commande a été démarrée en tant que tâche, elle est retournée par défaut en tant que tâche. Dans le cas contraire, elle est retournée au programme hôte par défaut.

En général, le programme hôte affiche sans retard les objets retournés dans la ligne de commande, mais ce comportement peut varier.

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Spécifie le port réseau de l’ordinateur distant qui est utilisé pour se reconnecter à la session. Pour vous connecter à un ordinateur distant, celui-ci doit être à l’écoute sur le port utilisé par la connexion. Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.

Avant d’utiliser un autre port, vous devez configurer l’écouteur WinRM sur l’ordinateur distant pour qu’il écoute sur ce port. Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

N’utilisez pas le paramètre **port** à moins qu’il soit nécessaire. Le port défini dans la commande s’applique à tous les ordinateurs ou sessions sur lesquels la commande s’exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

```yaml
Type: System.Int32
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

Spécifie la session déconnectée. Entrez une variable qui contient la **session PSSession** ou une commande qui crée ou obtient la **session PSSession** , telle qu’une `Get-PSSession` commande.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Spécifie les options avancées pour la session. Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.

Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie. Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.

Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session. Toutefois, elles ne sont pas prioritaires sur les valeurs maximales, les quotas ou les limites définies dans la configuration de session.

Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` . Pour plus d’informations sur la variable de préférence **$PSSessionOption** , consultez [about_Preference_Variables](./About/about_Preference_Variables.md). Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](./About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour se connecter à la session déconnectée. Par défaut, SSL n’est pas utilisé.

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau. **UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d'une connexion HTTP.

Si vous utilisez ce paramètre et que le protocole SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: False
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

### System. Management. Automation. instances d’exécution. PSSession

Vous pouvez diriger les objets de session vers cette applet de commande, tels que les objets retournés par l’applet de commande `Get-PSSession` .

### System.Int32

Vous pouvez diriger les ID de session vers cette applet de commande.

### System.Guid

Vous pouvez diriger les ID d’instance des sessions de cette applet de commande.

### System.String

Vous pouvez diriger les noms de session vers cette applet de commande.

## SORTIES

### System. Management. Automation. job ou PSObject

Cette applet de commande retourne les résultats des commandes exécutées dans la session déconnectée, le cas échéant. Si la valeur ou la valeur par défaut du paramètre de **précible** est Job, `Receive-PSSession` retourne un objet de traitement. Sinon, elle retourne des objets qui représentent les résultats de cette commande.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

`Receive-PSSession` Obtient les résultats uniquement à partir des sessions qui ont été déconnectées. Seules les sessions connectées à, ou qui se terminent à, les ordinateurs qui exécutent PowerShell 3,0 ou des versions ultérieures peuvent être déconnectés et reconnectés.

Si les commandes qui étaient en cours d’exécution dans la session déconnectée n’ont pas généré de résultats ou si les résultats ont déjà été retournés à une autre session, `Receive-PSSession` ne génère aucune sortie.

Le mode de mise en mémoire tampon de sortie d’une session détermine la manière dont les commandes dans la session gèrent la sortie lorsque la session est déconnectée. Lorsque la valeur de l’option **OutputBufferingMode** de la session est Drop et que la mémoire tampon de sortie est Full, la commande commence à supprimer output. `Receive-PSSession` Impossible de récupérer cette sortie. Pour plus d’informations sur l’option mode de mise en mémoire tampon de sortie, consultez les articles d’aide pour les applets de commande [New-PSSessionOption](New-PSSessionOption.md) et [New-PSTransportOption](New-PSTransportOption.md) .

Vous ne pouvez pas modifier la valeur du délai d’inactivité d’une **session PSSession** quand vous vous connectez à la **session PSSession** ou recevez des résultats. Le paramètre **SessionOption** de `Receive-PSSession` prend un objet **SessionOption** qui a une valeur **IdleTimeout** . Toutefois, la valeur **IdleTimeout** de l’objet **SessionOption** et la valeur **IdleTimeout** de la `$PSSessionOption` variable sont ignorées lorsqu’il se connecte à une **session PSSession** ou reçoit des résultats.

- Vous pouvez définir et modifier le délai d’inactivité d’une **session PSSession** quand vous créez la **session PSSession** , à l’aide des `New-PSSession` applets de commande ou `Invoke-Command` , et lorsque vous vous déconnectez de la **session PSSession**.
- La propriété **IdleTimeout** d’une session **PSSession** est critique pour les sessions déconnectées, car elle détermine la durée pendant laquelle une session déconnectée est conservée sur l’ordinateur distant. Une session déconnectée est considérée comme inactive dès qu'elle est déconnectée, même si elle comprend des commandes en cours d'exécution.

Si vous démarrez un travail démarrer un travail dans une session à distance à l’aide du paramètre **AsJob** de l’applet de commande `Invoke-Command` , l’objet de traitement est créé dans la session active, même si la tâche est exécutée dans la session à distance. Si vous déconnectez la session à distance, l’objet de traitement de la session active est déconnecté du travail. L’objet de traitement contient tous les résultats qui lui ont été retournés, mais ne reçoit pas les nouveaux résultats de la tâche dans la session déconnectée.

Si un autre client se connecte à la session qui contient le travail en cours d’exécution, les résultats qui ont été remis à l’objet de traitement d’origine dans la session d’origine ne sont pas disponibles dans la session qui vient d’être connectée. Seuls les résultats qui n'ont pas été remis à l'objet de traitement d'origine sont disponibles dans la session reconnectée.

De même, si vous démarrez un script dans une session, puis vous déconnectez de la session, les résultats que le script remet à la session avant la déconnexion ne sont pas disponibles pour un autre client qui se connecte à la session.

Pour éviter la perte de données dans les sessions que vous souhaitez déconnecter, utilisez le paramètre **InDisconnectedSession** de l’applet de commande `Invoke-Command` . Comme ce paramètre empêche le renvoi des résultats à la session active, tous les résultats sont disponibles quand la session est reconnectée.

Vous pouvez également empêcher la perte de données à l’aide de l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande dans la session à distance. Dans ce cas, l'objet de traitement est créé dans la session à distance. Vous ne pouvez pas utiliser l' `Receive-PSSession` applet de commande pour obtenir les résultats de la tâche. Utilisez plutôt l' `Connect-PSSession` applet de commande pour vous connecter à la session, puis utilisez l' `Invoke-Command` applet de commande pour exécuter une `Receive-Job` commande dans la session.

Quand une session qui contient un travail en cours d’exécution est déconnectée puis reconnectée, l’objet de travail d’origine est réutilisé uniquement si le travail est déconnecté et reconnecté à la même session, et si la commande de reconnexion ne spécifie pas un nouveau nom de travail. Si la session est reconnectée à une autre session client ou si un nouveau nom de tâche est spécifié, PowerShell crée un nouvel objet de traitement pour la nouvelle session.

Lorsque vous déconnectez une session **PSSession** , l’état de session est disconnected et la disponibilité est None.

- La valeur de la propriété **State** dépend de la session active. La valeur Disconnected signifie que la session **PSSession** n’est pas connectée à la session active. Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions. Elle peut être connectée à une autre session.
  Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability**.
- Une propriété **Availability** avec la valeur None signifie que vous pouvez vous connecter à la session. La valeur Busy indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.
- Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).
- Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).

## LIENS CONNEXES

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Session_Configurations](./About/about_Session_Configurations.md)

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Remove-PSSession](Remove-PSSession.md)
