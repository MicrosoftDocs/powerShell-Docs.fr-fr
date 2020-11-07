---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 3d38ac38fb06f3dd414e9549ea4f279e47b2aff8
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347361"
---
# Connect-PSSession

## SYNOPSIS
Se reconnecte aux sessions déconnectées.

## SYNTAXE

### Nom (par défaut)

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### session

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameGuid

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerName

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriGuid

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ConnectionUri

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Connect-PSSession` applet de commande se reconnecte aux sessions PowerShell gérées par l’utilisateur ( **sessions PSSession** ) qui ont été déconnectées. Elle fonctionne sur les sessions déconnectées intentionnellement, par exemple en utilisant l' `Disconnect-PSSession` applet de commande ou le paramètre **InDisconnectedSession** de l’applet de commande `Invoke-Command` , et celles qui ont été déconnectées de manière involontaire, par exemple suite à une panne réseau temporaire.

`Connect-PSSession` peut se connecter à n’importe quelle session déconnectée qui a été démarrée par le même utilisateur. Celles-ci incluent celles qui ont été démarrées par ou déconnectées d’autres sessions sur d’autres ordinateurs.

Toutefois, `Connect-PSSession` ne peut pas se connecter à des sessions interrompues ou fermées, ou à des sessions interactives démarrées à l’aide de l’applet de commande `Enter-PSSession` . En outre, vous ne pouvez pas connecter une session à une session démarrée par un autre utilisateur, sauf si vous pouvez fournir les informations d'identification de l'utilisateur qui a créé la session.

Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : se reconnecter à une session

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

Cette commande se reconnecte à la session ITTask sur l'ordinateur Server01.

La sortie montre que la commande a réussi. L' **État** de la session est ouvert et la **disponibilité** est disponible, ce qui indique que vous pouvez exécuter des commandes dans la session.

### Exemple 2 : effet de la déconnexion et de la reconnexion

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

Cet exemple montre l'effet de la déconnexion et de la reconnexion à une session.

La première commande utilise l' `Get-PSSession` applet de commande. Sans le paramètre **ComputerName** , la commande récupère uniquement les sessions qui ont été créées dans la session active.

La sortie indique que la commande récupère la session Backups sur l'ordinateur local. L' **État** de la session est ouvert et la **disponibilité** est disponible.

La deuxième commande utilise l' `Get-PSSession` applet de commande pour récupérer les objets **PSSession** qui ont été créés dans la session active et l' `Disconnect-PSSession` applet de commande pour déconnecter les sessions. La sortie indique que la session Backups a été déconnectée. L' **État** de la session est disconnected et la **disponibilité** est None.

La troisième commande utilise l' `Get-PSSession` applet de commande pour récupérer les objets **PSSession** qui ont été créés dans la session active et l' `Connect-PSSession` applet de commande pour reconnecter les sessions. La sortie indique que la session Backups a été reconnectée. L' **État** de la session est ouvert et la **disponibilité** est disponible.

Si vous utilisez l' `Connect-PSSession` applet de commande sur une session qui n’est pas déconnectée, la commande n’affecte pas la session et ne génère pas d’erreurs.

### Exemple 3 : série de commandes dans un scénario d’entreprise

Cette série de commandes montre comment l' `Connect-PSSession` applet de commande peut être utilisée dans un scénario d’entreprise. Dans ce cas, un administrateur système démarre une tâche de longue durée dans une session sur un ordinateur distant. Après le démarrage de la tâche, l'administrateur se déconnecte de la session et rentre chez lui.
Plus tard dans la soirée, l’administrateur se connecte à son ordinateur privé et vérifie que la tâche s’est exécutée jusqu’à ce qu’elle soit terminée.

L’administrateur commence par créer des sessions sur un ordinateur distant et à exécuter un script dans la session. La première commande utilise l' `New-PSSession` applet de commande pour créer la session ITTask sur l’ordinateur distant SERVEUR01. La commande utilise le paramètre **ConfigurationName** pour spécifier la configuration de session ITTasks. La commande enregistre les sessions dans la `$s` variable.

Deuxième applet de commande `Invoke-Command` pour démarrer une tâche en arrière-plan dans la session dans la `$s` variable. Elle utilise le paramètre **FilePath** pour exécuter le script dans la tâche en arrière-plan.

La troisième commande utilise l' `Disconnect-PSSession` applet de commande pour se déconnecter de la session dans la `$s` variable. La commande utilise le paramètre **OutputBufferingMode** avec la valeur Drop pour empêcher le blocage du script au cas où il devrait transmettre une sortie à la session. Elle utilise le paramètre **IdleTimeoutSec** pour étendre le délai d’expiration de session à 15 heures. Lorsque la commande est terminée, l’administrateur verrouille son ordinateur et le soir.

Plus tard le soir, l’administrateur démarre son ordinateur privé, se connecte au réseau d’entreprise et démarre PowerShell. La quatrième commande utilise l' `Get-PSSession` applet de commande pour récupérer les sessions sur l’ordinateur SERVEUR01. La commande recherche la session ITTask. La cinquième commande utilise l' `Connect-PSSession` applet de commande pour se connecter à la session ITTask. La commande enregistre la session dans la variable `$s`.

La sixième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Job` commande dans la session de la `$s` variable. La sortie indique que la tâche s’est terminée avec succès. La septième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Receive-Job` commande dans la session dans la `$s` variable de la session. La commande enregistre les résultats dans la `$BackupSpecs` variable. La huitième commande utilise l' `Invoke-Command` applet de commande pour exécuter un autre script dans la session. La commande utilise la valeur de la `$BackupSpecs` variable de la session comme entrée pour le script.

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

La neuvième commande se déconnecte de la session dans la `$s` variable. L’administrateur ferme PowerShell et ferme l’ordinateur. Il peut se reconnecter à la session le jour suivant et vérifier le statut du script à partir de son ordinateur professionnel.

## PARAMÈTRES

### -AllowRedirection

Indique que cette applet de commande autorise la redirection de cette connexion vers un autre URI.

Quand vous utilisez le paramètre **ConnectionURI** , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI. Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.

Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount**. Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la variable de préférence **$PSSessionOption** . La valeur par défaut est 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Spécifie le nom d'une application. Cette applet de commande se connecte uniquement aux sessions qui utilisent l’application spécifiée.

Entrez le segment de nom d'application de l'URI de connexion. Par exemple, dans l’URI de connexion suivant, le nom de l’application est WSMan : `http://localhost:5985/WSMAN` . Le nom d'application d'une session est stocké dans la propriété **Runspace.ConnectionInfo.AppName** de la session.

La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions. Elle ne modifie pas l'application utilisée par la session.

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur dans la commande pour se reconnecter à la session déconnectée. Les valeurs valides pour ce paramètre sont :

- Default
- De base
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

La valeur par défaut est Default.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) dans MSDN Library.

> [!CAUTION]
> l'authentification CredSSP (Credential Security Support Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui nécessitent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux. Ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez une `Get-Item` `Get-ChildItem` commande ou dans le lecteur de certificat PowerShell :.

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie les ordinateurs sur lesquels sont stockées les sessions déconnectées. Les sessions sont stockées sur l’ordinateur qui se trouve côté serveur ou reçoit la fin d’une connexion. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur. Les caractères génériques ne sont pas autorisés. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.)

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationName

Se connecte uniquement à des sessions qui utilisent la configuration de session spécifiée.

Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session. Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` . Le nom de configuration d'une session est stocké dans la propriété **ConfigurationName** de la session.

La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions. Elle ne modifie pas la configuration de session utilisée par la session.

Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Spécifie les URI des points de terminaison de connexion pour les sessions déconnectées.

L’URI doit être complet. Le format de cette chaîne est le suivant :

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

La valeur par défaut est la suivante :

`http://localhost:5985/WSMAN`

Si vous ne spécifiez pas d’URI de connexion, vous pouvez utiliser les paramètres **UseSSL** et **port** pour spécifier les valeurs d’URI de connexion.

Les valeurs valides du segment **Transport** de l'URI sont HTTP et HTTPS. Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs. Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.

Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un `PSCredential` objet généré par l’applet `Get-Credential` de commande. Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Spécifie les ID des sessions déconnectées. Le paramètre **ID** fonctionne uniquement lorsque la session déconnectée a déjà été connectée à la session active.

Ce paramètre est valide, mais il est sans effet si la session est stockée sur l'ordinateur local sans avoir été connectée à la session active.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Spécifie les ID d'instance des sessions déconnectées.

L’ID d’instance est un GUID qui identifie de façon unique une **session PSSession** sur un ordinateur local ou distant.

L’ID d’instance est stocké dans la propriété **InstanceID** de la **session PSSession**.

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie les noms conviviaux des sessions déconnectées.

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Spécifie le port réseau sur l'ordinateur distant qui est utilisé pour se reconnecter à la session. Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion. Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.

Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port. Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé. Le port défini dans la commande s'applique à tous les ordinateurs ou toutes les sessions sur lesquelles la commande s'exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

Spécifie les sessions déconnectées. Entrez une variable qui contient les objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu’une `Get-PSSession` commande.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
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

Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session. Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.

Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` . Pour plus d’informations sur la variable de préférence **$PSSessionOption** , consultez [about_Preference_Variables](About/about_Preference_Variables.md). Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.

La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

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

### -UseSSL

Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour se connecter à la session déconnectée. Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau. Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.

Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
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

### System. Management. Automation. instances d’exécution. PSSession

Vous pouvez diriger une session ( **PSSession** ) vers cette applet de commande.

## SORTIES

### System. Management. Automation. instances d’exécution. PSSession

Cette applet de commande retourne un objet qui représente la session à laquelle elle s’est reconnectée.

## REMARQUES

- Cette applet de commande est disponible uniquement sur les plateformes Windows.

- `Connect-PSSession` se reconnecte uniquement aux sessions déconnectées, c’est-à-dire aux sessions dont la valeur de la propriété **State** est disconnected. Seules les sessions connectées à, ou qui se terminent à, les ordinateurs qui exécutent Windows PowerShell 3,0 ou des versions ultérieures peuvent être déconnectées et reconnectées.

- Si vous utilisez `Connect-PSSession` sur une session qui n’est pas déconnectée, la commande n’affecte pas la session et elle ne génère pas d’erreurs.

- Les sessions de bouclage déconnectées avec des jetons interactifs, qui sont créés à l’aide du paramètre **EnableNetworkAccess** , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée. Cette restriction protège l'ordinateur contre tout accès malveillant.

- La valeur de la propriété **State** d’une session **PSSession** est relative à la session active.
  Par conséquent, la valeur **Disconnected** signifie que la session **PSSession** n’est pas connectée à la session active. Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions. Elle peut être connectée à une autre session. Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability**.

  Une propriété **Availability** avec la valeur None signifie que vous pouvez vous connecter à la session. La valeur Busy indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.

  Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [RunspaceState, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) dans MSDN Library.

  Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [RunspaceAvailability, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) dans MSDN Library.

- Vous ne pouvez pas modifier la valeur du délai d’inactivité d’une **session PSSession** quand vous vous connectez à la **session PSSession**. Le paramètre **SessionOption** de `Connect-PSSession` prend un objet **SessionOption** qui a une valeur **IdleTimeout** . Toutefois, la valeur **IdleTimeout** de l’objet **SessionOption** et la valeur **IdleTimeout** de la `$PSSessionOption` variable sont ignorées lors de la connexion à une **session PSSession**.

  Vous pouvez définir et modifier le délai d’inactivité d’une **session PSSession** quand vous créez la **session PSSession** , à l’aide des `New-PSSession` applets de commande ou `Invoke-Command` , et lorsque vous vous déconnectez de la **session PSSession**.

  La propriété **IdleTimeout** d’une session **PSSession** est critique pour les sessions déconnectées, car elle détermine la durée pendant laquelle une session déconnectée est conservée sur l’ordinateur distant. Une session déconnectée est considérée comme inactive dès qu'elle est déconnectée, même si elle comprend des commandes en cours d'exécution.

## LIENS CONNEXES

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)
