---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: cee14ce93af87d33b4d9d9665c3ef5aaa2aec1d5
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387445"
---
# Get-PSSession

## SYNOPSIS
Obtient les sessions PowerShell sur les ordinateurs locaux et distants.

## SYNTAXE

### Nom (par défaut)

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### ComputerInstanceId

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ComputerName

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-ThrottleLimit <Int32>] [-State <SessionFilterState>]
 [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUri

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-ThrottleLimit <Int32>] [-State <SessionFilterState>]
 [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### VMName

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### ContainerId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### ContainerIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### VMId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -VMId <Guid[]> [<CommonParameters>]
```

### VMIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMId <Guid[]> [<CommonParameters>]
```

### VMNameInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### InstanceId

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### Id

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## DESCRIPTION

L' `Get-PSSession` applet de commande obtient les sessions PowerShell gérées par l’utilisateur ( **sessions PSSession** ) sur les ordinateurs locaux et distants.

À compter de Windows PowerShell 3,0, les sessions sont stockées sur les ordinateurs à l’extrémité distante de chaque connexion. Vous pouvez utiliser les paramètres **ComputerName** ou **ConnectionUri** de `Get-PSSession` pour récupérer les sessions qui se connectent à l’ordinateur local ou aux ordinateurs distants, même s’ils n’ont pas été créés dans la session active.

Sans paramètres, `Get-PSSession` obtient toutes les sessions qui ont été créées dans la session active.

Utilisez les paramètres de filtrage, y compris **Name** , **ID** , **InstanceID** , **State** , **applicationName** et **ConfigurationName** , pour effectuer une sélection parmi les sessions `Get-PSSession` retournées par.

Utilisez les paramètres restants pour configurer la connexion temporaire dans laquelle la `Get-PSSession` commande s’exécute lorsque vous utilisez les paramètres **ComputerName** ou **ConnectionUri** .

Remarque : dans Windows PowerShell 2,0, sans paramètres, `Get-PSSession` obtient toutes les sessions qui ont été créées dans la session active. Le paramètre **ComputerName** obtient les sessions qui ont été créées dans la session active et se connecte à l’ordinateur spécifié.

Pour plus d’informations sur les sessions PowerShell, consultez [about_PSSessions](about/about_PSSessions.md).

## EXEMPLES

### Exemple 1 : accéder aux sessions créées dans la session active

```powershell
Get-PSSession
```

Cette commande obtient toutes les **sessions PSSession** qui ont été créées dans la session active. Il n’obtient pas les **sessions PSSession** qui ont été créés dans d’autres sessions ou sur d’autres ordinateurs, même s’ils se connectent à cet ordinateur.

### Exemple 2 : accéder aux sessions connectées à l’ordinateur local

```powershell
Get-PSSession -ComputerName "localhost"
```

Cette commande obtient les **sessions PSSession** qui sont connectés à l’ordinateur local. Pour indiquer l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.)

La commande retourne toutes les sessions sur l'ordinateur local, même si elles ont été créées dans différentes sessions ou sur des ordinateurs différents.

### Exemple 3 : obtenir des sessions connectées à un ordinateur

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

Cette commande obtient les **sessions PSSession** qui sont connectés à l’ordinateur Server02.

La commande retourne toutes les sessions sur Server02, même si elles ont été créées dans différentes sessions ou sur des ordinateurs différents.

La sortie montre que deux sessions ont l'état Disconnected et la disponibilité Busy. Elles ont été créées dans différentes sessions et sont en cours d'utilisation. La session ScheduledJobs, qui est ouverte et disponible, a été créée dans la session active.

### Exemple 4 : enregistrer les résultats de cette commande

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

Cet exemple montre comment enregistrer les résultats d’une `Get-PSSession` commande dans plusieurs variables.

La première commande utilise l' `New-PSSession` applet de commande pour créer des **sessions PSSession** sur trois ordinateurs distants.

La deuxième commande utilise une `Get-PSSession` applet de commande pour obtenir les trois **sessions PSSession**. Il enregistre ensuite chaque **sessions PSSession** dans une variable distincte.

Quand PowerShell assigne un tableau d’objets à un tableau de variables, il assigne le premier objet à la première variable, le deuxième à la deuxième variable, et ainsi de suite. S'il y a plus d'objets que de variables, il affecte tous les autres objets à la dernière variable dans le tableau. S'il y a plus de variables que d'objets, les variables supplémentaires ne sont pas utilisées.

### Exemple 5 : supprimer une session à l’aide d’un ID d’instance

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

Cet exemple montre comment obtenir une **session PSSession** à l’aide de son ID d’instance, puis comment supprimer la **session PSSession**.

La première commande obtient toutes les **sessions PSSession** qui ont été créées dans la session active. Elle envoie le **sessions PSSession** à l’applet de commande Format-Table, qui affiche les propriétés **ComputerName** et **InstanceID** de chaque **session PSSession**.

La deuxième commande utilise l' `Get-PSSession` applet de commande pour obtenir une **session PSSession** particulière et l’enregistrer dans la `$s` variable. La commande utilise le paramètre **InstanceID** pour identifier la **session PSSession**.

La troisième commande utilise l’applet de commande Remove-PSSession pour supprimer la **session PSSession** dans la `$s` variable.

### Exemple 6 : obtenir une session portant un nom particulier

Les commandes de cet exemple montrent comment rechercher une session qui a un format de nom particulier et qui utilise une configuration de session particulière, puis comment se connecter à la session. Vous pouvez utiliser une commande similaire à celle-ci pour rechercher une session dans laquelle un collègue a démarré une tâche et vous connecter pour terminer la tâche.

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

La première commande obtient les sessions sur les ordinateurs distants Server02 et Server12 dont les noms commencent par BackupJob et utilisent la configuration de session ITTasks. La commande utilise le paramètre **Name** pour spécifier le modèle de nom et le paramètre **ConfigurationName** pour spécifier la configuration de session. La valeur du paramètre **SessionOption** est une table de hachage qui définit la valeur d' **OperationTimeout** sur 240 000 millisecondes (4 minutes). Ce paramètre donne plus de temps à la commande. Les paramètres **ConfigurationName** et **SessionOption** sont utilisés pour configurer les sessions temporaires dans lesquelles l’applet de commande `Get-PSSession` s’exécute sur chaque ordinateur. La sortie indique que la commande retourne la session BackupJob04. La session est déconnectée et la **disponibilité** est None, ce qui indique qu’elle n’est pas en cours d’utilisation.

La deuxième commande utilise l' `Get-PSSession` applet de commande pour accéder à la session BackupJob04 et l’applet de commande Connect-PSSession pour se connecter à la session. La commande enregistre la session dans la variable $s.

La troisième commande obtient la session stockée dans la variable $s. La sortie indique que la `Connect-PSSession` commande a réussi. La session est dans l'état **Opened** et est utilisable.

### Exemple 7 : obtenir une session à l’aide de son ID

```powershell
Get-PSSession -Id 2
```

Cette commande obtient la **session PSSession** avec l’ID 2. Étant donné que la valeur de la propriété **ID** n’est unique que dans la session active, le paramètre **ID** n’est valide que pour les commandes locales.

## PARAMÈTRES

### -AllowRedirection

Indique que cette applet de commande autorise la redirection de cette connexion vers un autre Uniform Resource Identifier (URI). Par défaut, PowerShell ne redirige pas les connexions.

Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ConnectionUri** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Spécifie le nom d'une application. Cette applet de commande se connecte uniquement aux sessions qui utilisent l’application spécifiée.

Entrez le segment de nom d'application de l'URI de connexion. Par exemple, dans l’URI de connexion suivant, le nom de l’application est WSMan : `http://localhost:5985/WSMAN` . Le nom d'application d'une session est stocké dans la propriété **Runspace.ConnectionInfo.AppName** de la session.

La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions. Elle ne modifie pas l'application utilisée par la session.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de la session dans laquelle la `Get-PSSession` commande s’exécute.

Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** ou **ConnectionUri** .

Les valeurs valides pour ce paramètre sont :

- Default
- De base
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential.

La valeur par défaut est Default.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (x509) d’un compte d’utilisateur qui a l’autorisation de créer la session dans laquelle la `Get-PSSession` commande s’exécute. Entrez l’empreinte numérique du certificat.

Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** ou **ConnectionUri** .

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir une empreinte numérique de certificat, utilisez une commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie un tableau de noms d’ordinateurs. Obtient les sessions qui se connectent aux ordinateurs spécifiés.
Les caractères génériques ne sont pas autorisés. Il n’y a pas de valeur par défaut.

À compter de Windows PowerShell 3,0, les objets **PSSession** sont stockés sur les ordinateurs à l’extrémité distante de chaque connexion. Pour obtenir les sessions sur les ordinateurs spécifiés, PowerShell crée une connexion temporaire à chaque ordinateur et exécute une `Get-PSSession` commande.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ou de plusieurs ordinateurs. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.).

Remarque : ce paramètre obtient les sessions uniquement à partir d’ordinateurs qui exécutent Windows PowerShell 3,0 ou des versions ultérieures de PowerShell. Les versions antérieures ne stockent pas de sessions.

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConfigurationName

Spécifie le nom d’une configuration. Cette applet de commande obtient uniquement les sessions qui utilisent la configuration de session spécifiée.

Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session. Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` . Le nom de configuration d'une session est stocké dans la propriété **ConfigurationName** de la session.

La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions. Elle ne modifie pas la configuration de session utilisée par la session.

Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, VMNameInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Spécifie un URI qui définit le point de terminaison de connexion pour la session temporaire dans laquelle la `Get-PSSession` commande s’exécute. L’URI doit être complet.

Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ConnectionUri** .

Le format de cette chaîne est :

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

La valeur par défaut est `http://localhost:5985/WSMAN`.

Si vous ne spécifiez pas de **ConnectionUri** , vous pouvez utiliser les paramètres **UseSSL** , **ComputerName** , **port** et **applicationName** pour spécifier les valeurs **ConnectionUri** . Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS. Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs. Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.

Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

Ce paramètre obtient les sessions uniquement à partir d’ordinateurs qui exécutent Windows PowerShell 3,0 ou des versions ultérieures de Windows PowerShell. Les versions antérieures ne stockent pas de sessions.

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Spécifie un tableau d’ID de conteneurs. Cette applet de commande démarre une session interactive avec chacun des conteneurs spécifiés. Utilisez la `docker ps` commande pour obtenir la liste des ID de conteneur. Pour plus d’informations, consultez l’aide de la commande [dockr PS](https://docs.docker.com/engine/reference/commandline/ps/) .

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Spécifie les informations d’identification de l’utilisateur. Cette applet de commande exécute la commande avec les autorisations de l’utilisateur spécifié. Spécifiez un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur distant et d’exécuter une `Get-PSSession` commande. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** ou **ConnectionUri** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Spécifie un tableau d’ID de session. Cette applet de commande obtient uniquement les sessions avec les ID spécifiés. Tapez un ou plusieurs ID, en les séparant par des virgules, ou utilisez l’opérateur de plage (..) pour spécifier une plage d’ID. Vous ne pouvez pas utiliser le paramètre ID avec le paramètre **ComputerName** .

Un ID est un entier qui identifie de façon unique les sessions gérées par l’utilisateur dans la session active. Il est plus facile à mémoriser et à taper que **InstanceID** , mais il n’est unique que dans la session active. L'ID d'une session est stocké dans la propriété ID de la session.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Spécifie un tableau d’ID d’instance de sessions. Cette applet de commande obtient uniquement les sessions avec les ID d’instance spécifiés.

L'ID d'instance est un GUID qui identifie une session sur un ordinateur local ou distant. L' **InstanceID** est unique, même si plusieurs sessions sont en cours d’exécution dans PowerShell.

L'ID d'instance d'une session est stocké dans la propriété **InstanceID** de la session.

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, VMNameInstanceId, ContainerIdInstanceId, VMIdInstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms de sessions. Cette applet de commande obtient uniquement les sessions qui ont les noms conviviaux spécifiés. Les caractères génériques sont autorisés.

Le nom convivial d'une session est stocké dans la propriété **Name** de la session.

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Port

Spécifie le port réseau spécifié qui est utilisé pour la connexion temporaire dans laquelle la `Get-PSSession` commande s’exécute. Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion. Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.

Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port. Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** ou **ConnectionUri** .

N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé. Le **port** défini dans la commande s’applique à tous les ordinateurs ou sessions sur lesquels la commande s’exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

Spécifie les options avancées pour la session. Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l’applet de commande New-PSSessionOption, ou une table de hachage dans laquelle les clés sont des noms d’options de session et les valeurs sont des valeurs d’option de session.

Les valeurs par défaut des options sont déterminées par la valeur de la variable de préférence PSSessionOption, si elle est définie. Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.

Les valeurs des options de la session sont prioritaires sur les valeurs par défaut des sessions définies dans la variable de préférence $PSSessionOption et dans la configuration de session. Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.

Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez `New-PSSessionOption` .
Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md). Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -État

Spécifie un état de session. Cette applet de commande obtient uniquement les sessions dans l’état spécifié. Les valeurs acceptables pour ce paramètre sont : All, Opened, Disconnected, Closed et Broken. La valeur par défaut est All.

La valeur d'état de session dépend des sessions actives. Les sessions qui n'ont pas été créées dans les sessions actives et qui ne sont pas connectées à la session active ont l'état Disconnected même si elles sont connectées à une autre session.

L'état d'une session est stocké dans la propriété **State** de la session.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, VMNameInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter la `Get-PSSession` commande. Si vous omettez ce paramètre ou entrez la valeur 0 (zéro), la valeur par défaut 32 est utilisée. La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour établir la connexion dans laquelle la `Get-PSSession` commande s’exécute. Par défaut, SSL n'est pas utilisé. Si vous utilisez ce paramètre, mais que SSL n'est pas disponible sur le port utilisé pour la commande, celle-ci échoue.

Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Spécifie un tableau d’ID de machines virtuelles. Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés. Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez la commande suivante :

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Spécifie un tableau de noms d'ordinateurs virtuels. Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés. Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez l' `Get-VM` applet de commande.

```yaml
Type: System.String[]
Parameter Sets: VMNameInstanceId, VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. instances d’exécution. PSSession

## REMARQUES

- Cette applet de commande obtient les objets **PSSession** des sessions gérées par l’utilisateur, telles que celles qui sont créées à l’aide des applets de commande New-PSSession, `Enter-PSSession` et Invoke-Command. Elle n’obtient pas la session gérée par le système qui est créée lorsque vous démarrez PowerShell.
- À compter de Windows PowerShell 3,0, les objets **PSSession** sont stockés sur l’ordinateur qui se trouve sur le côté serveur ou reçoit la fin d’une connexion. Pour obtenir les sessions qui sont stockées sur l’ordinateur local ou sur un ordinateur distant, PowerShell établit une session temporaire sur l’ordinateur spécifié et exécute des commandes de requête dans la session.
- Pour obtenir les sessions qui se connectent à un ordinateur distant, utilisez les paramètres **ComputerName** ou **ConnectionUri** pour spécifier l'ordinateur distant. Pour filtrer les sessions que `Get-PSSession` obtient, utilisez les paramètres **Name** , **ID** , **InstanceID** et **State** . Utilisez les paramètres restants pour configurer la session temporaire qui `Get-PSSession` utilise.
- Lorsque vous utilisez les paramètres **ComputerName** ou **ConnectionUri** , `Get-PSSession` obtient uniquement les sessions d’ordinateurs exécutant Windows PowerShell 3,0 et les versions ultérieures de PowerShell.
- La valeur de la propriété **State** d’une session **PSSession** est relative à la session active.
  Par conséquent, la valeur **Disconnected** signifie que la session **PSSession** n’est pas connectée à la session active. Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions. Elle peut être connectée à une autre session. Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session **PSSession** à partir de la session active, utilisez la propriété **Availability** .

Une propriété **Availability** avec la valeur **None** signifie que vous pouvez vous connecter à la session. La valeur **Busy** indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.

Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [énumération RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).

Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [énumération RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).

## LIENS CONNEXES

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
