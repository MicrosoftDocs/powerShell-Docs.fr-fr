---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 61f1d13628763710f01cf0c2ec413f446e4bdd39
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205545"
---
# Connect-PSSession

## SYNOPSIS
Se reconnecte aux sessions déconnectées.

## SYNTAX

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

## Description

L’applet de commande **Connect-PSSession** se reconnecte aux sessions PowerShell gérées par l’utilisateur ( **sessions PSSession** ) qui ont été déconnectées.
Elle fonctionne sur les sessions déconnectées intentionnellement, par exemple en utilisant l’applet de commande Disconnect-PSSession ou le paramètre *InDisconnectedSession* de l’applet de commande Invoke-Command, et celles qui ont été déconnectées de manière involontaire, par exemple en cas de panne réseau temporaire.

**Connect-PSSession** peut se connecter à n’importe quelle session déconnectée qui a été démarrée par le même utilisateur.
Celles-ci incluent celles qui ont été démarrées par ou déconnectées d’autres sessions sur d’autres ordinateurs.

Toutefois, **Connect-PSSession** ne peut pas se connecter aux sessions interrompues ou fermées, ou les sessions interactives démarrées à l’aide de l’applet de commande Enter-PSSession.
En outre, vous ne pouvez pas connecter une session à une session démarrée par un autre utilisateur, sauf si vous pouvez fournir les informations d'identification de l'utilisateur qui a créé la session.

Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez about_Remote_Disconnected_Sessions.

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

La sortie montre que la commande a réussi.
L' **État** de la session est ouvert et la **disponibilité** est disponible, ce qui indique que vous pouvez exécuter des commandes dans la session.

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

La première commande utilise l’applet de commande Get-PSSession.
Sans le paramètre *ComputerName* , la commande récupère uniquement les sessions qui ont été créées dans la session active.

La sortie indique que la commande récupère la session Backups sur l'ordinateur local.
L' **État** de la session est ouvert et la **disponibilité** est disponible.

La deuxième commande utilise l’applet de commande **obten-PSSession** pour récupérer les objets **PSSession** qui ont été créés dans la session active et l’applet de commande **Disconnect-PSSession** pour déconnecter les sessions.
La sortie indique que la session Backups a été déconnectée.
L' **État** de la session est disconnected et la **disponibilité** est None.

La troisième commande utilise l’applet de commande **obten-PSSession** pour récupérer les objets **PSSession** qui ont été créés dans la session active et l’applet de commande **Connect-PSSession** pour reconnecter les sessions.
La sortie indique que la session Backups a été reconnectée.
L' **État** de la session est ouvert et la **disponibilité** est disponible.

Si vous utilisez l’applet de commande **Connect-PSSession** sur une session qui n’est pas déconnectée, la commande n’affecte pas la session et ne génère pas d’erreur.

### Exemple 3 : série de commandes dans un scénario d’entreprise

```
The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the **New-PSSession** cmdlet to create the ITTask session on the Server01 remote computer. The command uses the *ConfigurationName* parameter to specify the ITTasks session configuration. The command saves the sessions in the $s variable.
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks

 The second command **Invoke-Command** cmdlet to start a background job in the session in the $s variable. It uses the *FilePath* parameter to run the script in the background job.
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

The third command uses the Disconnect-PSSession cmdlet to disconnect from the session in the $s variable. The command uses the *OutputBufferingMode* parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session. It uses the *IdleTimeoutSec* parameter to extend the session time-out to 15 hours.When the command is completed, the administrator locks her computer and goes home for the evening.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell. The fourth command uses the Get-PSSession cmdlet to get the sessions on the Server01 computer. The command finds the ITTask session.The fifth command uses the **Connect-PSSession** cmdlet to connect to the ITTask session. The command saves the session in the $s variable.
PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

The sixth command uses the **Invoke-Command** cmdlet to run a Get-Job command in the session in the $s variable. The output shows that the job finished successfully.The seventh command uses the **Invoke-Command** cmdlet to run a Receive-Job command in the session in the $s variable in the session. The command saves the results in the $BackupSpecs variable.The eighth command uses the **Invoke-Command** cmdlet to runs another script in the session. The command uses the value of the $BackupSpecs variable in the session as input to the script.


PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

The ninth command disconnects from the session in the $s variable.The administrator closes PowerShell and closes the computer. She can reconnect to the session on the next day and check the script status from her work computer.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

Cette série de commandes montre comment l'applet de commande **Connect-PSSession** peut être utilisée dans un scénario d'entreprise.
Dans ce cas, un administrateur système démarre une tâche de longue durée dans une session sur un ordinateur distant.
Après le démarrage de la tâche, l'administrateur se déconnecte de la session et rentre chez lui.
Plus tard dans la soirée, l’administrateur se connecte à son ordinateur privé et vérifie que la tâche s’est exécutée jusqu’à ce qu’elle soit terminée.

## PARAMETERS

### -AllowRedirection

Indique que cette applet de commande autorise la redirection de cette connexion vers un autre URI.

Quand vous utilisez le paramètre *ConnectionURI* , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.
Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.

Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount** .
Utilisez le paramètre *MaximumRedirection* de l’applet de commande New-PSSessionOption ou définissez la propriété **MaximumConnectionRedirectionCount** de la variable de préférence **$PSSessionOption** .
La valeur par défaut est 5.

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

Spécifie le nom d'une application.
Cette applet de commande se connecte uniquement aux sessions qui utilisent l’application spécifiée.

Entrez le segment de nom d'application de l'URI de connexion.
Par exemple, dans l’URI de connexion suivant, le nom de l’application est WSMan : `http://localhost:5985/WSMAN` .
Le nom d'application d'une session est stocké dans la propriété **Runspace.ConnectionInfo.AppName** de la session.

La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions.
Elle ne modifie pas l'application utilisée par la session.

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
- Basic
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

La valeur par défaut est Default.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) dans MSDN Library.

ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.
Ce mécanisme augmente le risque de sécurité lié à l'opération distante.
Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

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

Les certificats sont utilisés dans l'authentification par certificat client.
Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux.
Ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez une commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.

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

Spécifie les ordinateurs sur lesquels sont stockées les sessions déconnectées.
Les sessions sont stockées sur l’ordinateur qui se trouve côté serveur ou reçoit la fin d’une connexion.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur.
Les caractères génériques ne sont pas autorisés.
Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.)

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

Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.
Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` .
Le nom de configuration d'une session est stocké dans la propriété **ConfigurationName** de la session.

La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions.
Elle ne modifie pas la configuration de session utilisée par la session.

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

L’URI doit être complet.
Le format de cette chaîne est le suivant :

`\<Transport\>://\<ComputerName\>:\<Port\>/\<ApplicationName\>`

La valeur par défaut est la suivante :

`http://localhost:5985/WSMAN`

Si vous ne spécifiez pas d’URI de connexion, vous pouvez utiliser les paramètres *UseSSL* et *port* pour spécifier les valeurs d’URI de connexion.

Les valeurs valides du segment **Transport** de l'URI sont HTTP et HTTPS.
Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.
Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.

Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre *AllowRedirection* dans la commande.

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

Spécifie un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

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

Spécifie les ID des sessions déconnectées.
Le paramètre *ID* fonctionne uniquement lorsque la session déconnectée a déjà été connectée à la session active.

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

L’ID d’instance est stocké dans la propriété **InstanceID** de la **session PSSession** .

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

Spécifie le port réseau sur l'ordinateur distant qui est utilisé pour se reconnecter à la session.
Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.
Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.

Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.
Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

N'utilisez pas le paramètre *Port* à moins que vous n'y soyez obligé.
Le port défini dans la commande s'applique à tous les ordinateurs ou toutes les sessions sur lesquelles la commande s'exécute.
Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

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

Spécifie les sessions déconnectées.
Entrez une variable qui contient les objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu’une commande Get-PSSession.

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

Spécifie les options avancées pour la session.
Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l’applet de commande New-PSSessionOption, ou une table de hachage dans laquelle les clés sont des noms d’options de session et les valeurs sont des valeurs d’option de session.

Les valeurs par défaut des options sont déterminées par la valeur de la variable de préférence PSSessionOption, si elle est définie.
Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.

Les valeurs des options de la session sont prioritaires sur les valeurs par défaut des sessions définies dans la variable de préférence $PSSessionOption et dans la configuration de session.
Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.

Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez New-PSSessionOption.
Pour plus d’informations sur la variable de préférence **$PSSessionOption** , consultez [about_Preference_Variables](About/about_Preference_Variables.md).
Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

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

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.
Le paramètre *UseSSL* est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.

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

* **Connect-PSSession** se reconnecte uniquement aux sessions déconnectées, c’est-à-dire aux sessions dont la valeur de la propriété **State** est disconnected. Seules les sessions connectées à, ou qui se terminent à, les ordinateurs qui exécutent Windows PowerShell 3,0 ou des versions ultérieures peuvent être déconnectées et reconnectées.
* Si vous utilisez **Connect-PSSession** sur une session qui n’est pas déconnectée, la commande n’affecte pas la session et elle ne génère pas d’erreurs.
* Les sessions de bouclage déconnectées avec des jetons interactifs, qui sont créés à l’aide du paramètre *EnableNetworkAccess* , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée. Cette restriction protège l'ordinateur contre tout accès malveillant.
* La valeur de la propriété **State** d’une session **PSSession** est relative à la session active.
Par conséquent, la valeur **Disconnected** signifie que la session **PSSession** n’est pas connectée à la session active. Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions. Elle peut être connectée à une autre session. Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability** .

  Une propriété **Availability** avec la valeur None signifie que vous pouvez vous connecter à la session.
La valeur Busy indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.

  Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [RunspaceState, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) dans MSDN Library.

  Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [RunspaceAvailability, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) dans MSDN Library.

* Vous ne pouvez pas modifier la valeur du délai d’inactivité d’une **session PSSession** quand vous vous connectez à la **session PSSession** . Le paramètre *SessionOption* de **Connect-PSSession** prend un objet **SessionOption** ayant une valeur **IdleTimeout** . Toutefois, la valeur **IdleTimeout** de l’objet **SessionOption** et la valeur **IdleTimeout** de la variable $PSSessionOption sont ignorées lors de la connexion à une **session PSSession** .

  Vous pouvez définir et modifier le délai d’inactivité d’une **session PSSession** quand vous créez la **session PSSession** , à l’aide des applets de commande **New-PSSession** ou **Invoke-Command** , et lorsque vous vous déconnectez de la **session PSSession** .

  La propriété **IdleTimeout** d’une session **PSSession** est critique pour les sessions déconnectées, car elle détermine la durée pendant laquelle une session déconnectée est conservée sur l’ordinateur distant.
Une session déconnectée est considérée comme inactive dès qu'elle est déconnectée, même si elle comprend des commandes en cours d'exécution.

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
