---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: f5b8d82b2f2a30c176ab01be42201434842a0454
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "93205761"
---
# Enter-PSSession

## SYNOPSIS
Démarre une session interactive avec un ordinateur distant.

## SYNTAX

### ComputerName (par défaut)

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### SSHHost

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### session

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### Uri

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### InstanceId

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### Id

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### Nom

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### VMId

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### VMName

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### ContainerId

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## Description

L' `Enter-PSSession` applet de commande démarre une session interactive avec un seul ordinateur distant.
Pendant la session, les commandes que vous tapez s’exécutent sur l’ordinateur distant, comme si vous tapiez directement sur l’ordinateur distant. Vous ne pouvez avoir qu'une seule session interactive à la fois.

En général, vous utilisez le paramètre **ComputerName** pour spécifier le nom de l'ordinateur distant.
Toutefois, vous pouvez également utiliser une session que vous créez à l’aide `New-PSSession` de l’applet de commande pour la session interactive. Toutefois, vous ne pouvez pas utiliser les `Disconnect-PSSession` applets de commande, ou pour vous déconnecter `Connect-PSSession` ou vous `Receive-PSSession` reconnecter à une session interactive.

À compter de PowerShell 6,0, vous pouvez utiliser Secure Shell (SSH) pour établir une connexion à un ordinateur distant, si SSH est disponible sur l’ordinateur local et que l’ordinateur distant est configuré avec un point de terminaison SSH PowerShell. L’avantage d’une session à distance PowerShell basée sur SSH est qu’elle fonctionne sur plusieurs plateformes (Windows, Linux, macOS). Pour la communication à distance basée sur SSH, vous utilisez le jeu de paramètres **hostname** pour spécifier l’ordinateur distant et les informations de connexion appropriées. Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

Pour mettre fin à la session interactive et vous déconnecter de l’ordinateur distant, utilisez l’applet de commande `Exit-PSSession` ou tapez `exit` .

## EXEMPLES

### Exemple 1 : démarrer une session interactive

```
PS> Enter-PSSession
[localhost]: PS>
```

Cette commande démarre une session interactive sur l'ordinateur local. L'invite de commandes change pour vous indiquer que vous exécutez à présent les commandes dans une autre session.

Les commandes que vous entrez s'exécutent dans la nouvelle session. Les résultats sont retournés à la session par défaut sous forme de texte.

### Exemple 2 : utiliser une session interactive

La première commande utilise l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec Serveur01, un ordinateur distant. Quand la session démarre, l'invite de commandes change pour inclure le nom de l'ordinateur.

La deuxième commande obtient le processus PowerShell et redirige la sortie vers le fichier Process.txt. La commande est envoyée à l'ordinateur distant, et le fichier est enregistré sur ce dernier.

La troisième commande utilise le mot clé **Exit** pour mettre fin à la session interactive et fermer la connexion.
La quatrième commande vérifie que le fichier Process.txt se trouve sur l'ordinateur distant. Une `Get-ChildItem` commande (« dir ») sur l’ordinateur local ne peut pas trouver le fichier.

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

Cette commande montre comment utiliser une session interactive avec un ordinateur distant.

### Exemple 3 : utiliser le paramètre de session

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

Ces commandes utilisent le paramètre **session** de `Enter-PSSession` pour exécuter la session interactive dans une session PowerShell existante ( **PSSession** ).

### Exemple 4 : démarrer une session interactive et spécifier les paramètres du port et des informations d’identification

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

Cette commande démarre une session interactive sur l'ordinateur Server01. Elle utilise le paramètre **port** pour spécifier le port et le paramètre **Credential** pour spécifier le compte d’un utilisateur qui a l’autorisation de se connecter à l’ordinateur distant.

### Exemple 5 : arrêter une session interactive

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

Cet exemple montre comment démarrer et arrêter une session interactive. La première commande utilise l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec l’ordinateur SERVEUR01.

La deuxième commande utilise l' `Exit-PSSession` applet de commande pour mettre fin à la session. Vous pouvez également utiliser le mot clé **Exit** pour mettre fin à la session interactive. `Exit-PSSession` et **Exit** ont le même effet.

### Exemple 6 : démarrer une session interactive à l’aide de SSH

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

Cet exemple montre comment démarrer une session interactive à l’aide de Secure Shell (SSH). Si SSH est configuré sur l’ordinateur distant pour demander des mots de passe, vous recevrez une invite de mot de passe.
Dans le cas contraire, vous devrez utiliser l’authentification utilisateur basée sur une clé SSH.

### Exemple 7 : démarrer une session interactive à l’aide de SSH et spécifier le port et la clé d’authentification utilisateur

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

Cet exemple montre comment démarrer une session interactive à l’aide de SSH. Elle utilise le paramètre **port** pour spécifier le port à utiliser et le paramètre **keyFilePath** pour spécifier une clé RSA utilisée pour authentifier l’utilisateur sur l’ordinateur distant.

## PARAMETERS

### -AllowRedirection

Autorise la redirection de cette connexion vers un autre URI (Uniform Resource Identifier). Par défaut, la redirection n'est pas autorisée.

Quand vous utilisez le paramètre **ConnectionURI** , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI. Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.

Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount** . Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la `$PSSessionOption` variable de préférence. La valeur par défaut est 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Spécifie le segment de nom d'application de l'URI de connexion. Utilisez ce paramètre pour spécifier le nom de l'application quand vous n'utilisez pas le paramètre **ConnectionURI** dans la commande.

La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local. Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN. Cette valeur convient pour la plupart des utilisations. Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).

Le service **WinRM** utilise le nom de l’application pour sélectionner un écouteur afin de traiter la demande de connexion. La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur. Les valeurs valides pour ce paramètre sont :

- Default
- Basic
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

La valeur par défaut est Default.

L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [enum AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action. Entrez l’empreinte numérique du certificat.

Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.

Pour obtenir un certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur du certificat PowerShell :

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie un nom d’ordinateur. Cette applet de commande démarre une session interactive avec l’ordinateur distant spécifié. Entrez uniquement un nom d'ordinateur. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet de l'ordinateur. Vous pouvez également diriger un nom d’ordinateur vers `Enter-PSSession` .

Pour utiliser une adresse IP dans la valeur du paramètre **ComputerName** , la commande doit inclure le paramètre **Credential** . En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local. Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).

Remarque : dans Windows Vista et les versions ultérieures du système d’exploitation Windows, pour inclure l’ordinateur local dans la valeur du paramètre **ComputerName** , vous devez démarrer PowerShell avec l’option Exécuter en tant qu’administrateur.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

Spécifie la configuration de session utilisée pour la session interactive.

Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session. Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` .

Lorsqu’il est utilisé avec SSH, il spécifie le sous-système à utiliser sur la cible, comme défini dans sshd_config. La valeur par défaut pour SSH est le `powershell` sous-système.

La configuration d'une session se trouve sur l'ordinateur distant. Si la configuration de session spécifiée n'existe pas sur l'ordinateur distant, la commande échoue.

La valeur par défaut est la valeur de la `$PSSessionConfigurationName` variable de préférence sur l’ordinateur local. Si cette variable de préférence n'est pas définie, la valeur par défaut est Microsoft.PowerShell. Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Spécifie un URI qui définit le point de terminaison de connexion pour la session. L’URI doit être complet. Le format de cette chaîne est le suivant :

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

La valeur par défaut est la suivante :

`http://localhost:5985/WSMAN`

Si vous ne spécifiez pas un **ConnectionURI** , vous pouvez utiliser les paramètres **UseSSL** , **ComputerName** , **Port** et **ApplicationName** pour spécifier les valeurs **ConnectionURI** .

Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS. Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée à l’aide des ports standard : 80 pour HTTP et 443 pour HTTPs. Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.

Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Spécifie l’ID d’un conteneur.

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage. Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs. Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.

Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur. Pour créer une session de bouclage, omettez le paramètre **ComputerName** ou affectez-lui la valeur. (point), localhost ou le nom de l’ordinateur local.

Par défaut, les sessions de bouclage sont créées à l’aide d’un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.

Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage. Si vous utilisez **EnableNetworkAccess** quand vous créez une session sur un ordinateur distant, la commande s’exécute correctement, mais le paramètre est ignoré.

Vous pouvez également autoriser l'accès à distance dans une session de bouclage à l'aide de la valeur **CredSSP** du paramètre **Authentication** , qui délègue les informations d'identification de session à d'autres ordinateurs.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Spécifie un nom d’ordinateur pour une connexion Secure Shell (SSH). Cela est similaire au paramètre **ComputerName** , à ceci près que la connexion à l’ordinateur distant s’effectue à l’aide de SSH plutôt que de Windows WinRM. Ce paramètre prend en charge la spécification du nom d’utilisateur et/ou du port dans le cadre de la valeur de paramètre de nom d’hôte à l’aide du formulaire `user@hostname:port` . Le nom d’utilisateur et/ou le port spécifié dans le cadre du nom d’hôte est prioritaire sur les `-UserName` `-Port` paramètres et, s’ils sont spécifiés. Cela permet de transmettre plusieurs noms d’ordinateur à ce paramètre, où certains ont des noms d’utilisateur et/ou des ports spécifiques, tandis que d’autres utilisent le nom d’utilisateur et/ou le port à partir des `-UserName` `-Port` paramètres et.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

Spécifie l'ID d'une session existante. `Enter-PSSession` utilise la session spécifiée pour la session interactive.

Pour Rechercher l’ID d’une session, utilisez l' `Get-PSSession` applet de commande.

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Spécifie l'ID d'instance d'une session existante. `Enter-PSSession` utilise la session spécifiée pour la session interactive.

L'ID d'instance est un GUID. Pour Rechercher l’ID d’instance d’une session, utilisez l’applet de commande `Get-PSSession` . Vous pouvez également utiliser les paramètres **session** , **Name** ou **ID** pour spécifier une session existante. Vous pouvez utiliser le paramètre **ComputerName** pour démarrer une session temporaire.

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -KeyFilePath

Spécifie un chemin de fichier de clé utilisé par Secure Shell (SSH) pour authentifier un utilisateur sur un ordinateur distant.

SSH permet d’effectuer l’authentification des utilisateurs via des clés privées/publiques comme alternative à l’authentification de base par mot de passe. Si l’ordinateur distant est configuré pour l’authentification de clé, ce paramètre peut être utilisé pour fournir la clé qui identifie l’utilisateur.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie le nom convivial d'une session existante. `Enter-PSSession` utilise la session spécifiée pour la session interactive.

Si le nom que vous spécifiez correspond à plusieurs sessions, la commande échoue. Vous pouvez également utiliser les paramètres **session** , **InstanceID** ou **ID** pour spécifier une session existante. Vous pouvez utiliser le paramètre **ComputerName** pour démarrer une session temporaire.

Pour établir un nom convivial pour une session, utilisez le paramètre **Name** de l' `New-PSSession` applet de commande.

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

Spécifie le port réseau sur l’ordinateur distant utilisé pour cette commande.

Dans PowerShell 6,0, ce paramètre était inclus dans le jeu de paramètres de **nom d’hôte** qui prend en charge les connexions Secure Shell (SSH).

**WinRM (jeu de paramètres ComputerName)**

Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion. Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.

Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port. Utilisez les commandes suivantes pour configurer l'écouteur :

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé. Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

**SSH (jeu de paramètres HostName)**

Pour se connecter à un ordinateur distant, l’ordinateur distant doit être configuré avec le service SSH (SSHD) et doit être à l’écoute sur le port utilisé par la connexion. Le port par défaut pour SSH est 22.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

Indique que la **session PSSession** s’exécute en tant qu’administrateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

Spécifie une session PowerShell ( **PSSession** ) à utiliser pour la session interactive. Ce paramètre accepte un objet de session. Vous pouvez également utiliser les paramètres **Name** , **InstanceID** ou **ID** pour spécifier une **session PSSession** .

Entrez une variable qui contient un objet de session ou une commande qui crée ou obtient un objet de session, tel qu’une `New-PSSession` `Get-PSSession` commande ou. Vous pouvez également diriger un objet de session vers `Enter-PSSession` . Vous ne pouvez envoyer qu’une seule **session PSSession** à l’aide de ce paramètre. Si vous entrez une variable qui contient plusieurs sessions **PSSession** , la commande échoue.

Lorsque vous utilisez `Exit-PSSession` ou le mot clé **Exit** , la session interactive se termine, mais la session **PSSession** que vous avez créée reste ouverte et disponible.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Définit des options avancées pour la session. Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.

Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie. Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.

Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session. Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.

Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez `New-PSSessionOption` .
Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md). Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

Indique que la connexion à distance est établie à l’aide d’Secure Shell (SSH).

Par défaut, PowerShell utilise Windows WinRM pour se connecter à un ordinateur distant. Ce commutateur force PowerShell à utiliser le jeu de paramètres HostName pour établir une connexion à distance basée sur SSH.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sous-système

Spécifie le sous-système SSH utilisé pour la nouvelle **session PSSession** .

Cela spécifie le sous-système à utiliser sur la cible, tel que défini dans sshd_config. Le sous-système démarre une version spécifique de PowerShell avec des paramètres prédéfinis. Si le sous-système spécifié n’existe pas sur l’ordinateur distant, la commande échoue.

Si ce paramètre n’est pas utilisé, la valeur par défaut est le sous-système « PowerShell ».

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UserName

Spécifie le nom d’utilisateur du compte utilisé pour créer une session sur l’ordinateur distant. La méthode d’authentification de l’utilisateur dépend de la configuration de Secure Shell (SSH) sur l’ordinateur distant.

Si SSH est configuré pour l’authentification de base par mot de passe, vous êtes invité à entrer le mot de passe de l’utilisateur.

Si SSH est configuré pour l’authentification utilisateur basée sur une clé, un chemin d’accès de fichier de clé peut être fourni via le paramètre **keyFilePath** et aucune invite de mot de passe n’est générée. Notez que si le fichier de clé de l’utilisateur client se trouve dans un emplacement connu SSH, le paramètre **keyFilePath** n’est pas nécessaire pour l’authentification basée sur les clés et l’authentification de l’utilisateur aura lieu automatiquement en fonction du nom d’utilisateur. Pour plus d’informations, consultez la documentation SSH sur l’authentification des utilisateurs basée sur les clés.

Ce paramètre n’est pas obligatoire. Si aucun paramètre de **nom d'** utilisateur n’est spécifié, le nom d’utilisateur actuellement connecté est utilisé pour la connexion.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour établir une connexion à l’ordinateur distant. Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau. Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.

Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Spécifie l’ID d’un ordinateur virtuel.

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMName

Spécifie le nom d'un ordinateur virtuel.

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. String, System. Management. Automation. instances d’exécution. PSSession

Vous pouvez diriger un nom d’ordinateur, une chaîne ou un objet de session vers cette applet de commande.

## SORTIES

### Aucun

L'applet de commande ne retourne aucune sortie.

## REMARQUES

Pour vous connecter à un ordinateur distant, vous devez être membre du groupe Administrateurs sur l'ordinateur distant. Pour démarrer une session interactive sur l’ordinateur local, vous devez démarrer PowerShell avec l’option **exécuter en tant qu’administrateur** .

Lorsque vous utilisez `Enter-PSSession` , votre profil utilisateur sur l’ordinateur distant est utilisé pour la session interactive. Les commandes du profil utilisateur distant, y compris les commandes permettant d’ajouter des modules PowerShell et de changer l’invite de commandes, s’exécutent avant l’affichage de l’invite distante.

`Enter-PSSession` utilise le paramètre de culture de l’interface utilisateur sur l’ordinateur local pour la session interactive. Pour rechercher la culture d’interface utilisateur locale, utilisez la `$UICulture` variable automatique.

`Enter-PSSession` requiert les `Get-Command` applets de commande, `Out-Default` et `Exit-PSSession` . Si ces applets de commande ne sont pas incluses dans la configuration de session sur l’ordinateur distant, les `Enter-PSSession` commandes échouent.

Contrairement `Invoke-Command` à, qui analyse et interprète les commandes avant de les envoyer à l’ordinateur distant, `Enter-PSSession` envoie les commandes directement à l’ordinateur distant sans interprétation.

Si la session que vous souhaitez entrer est occupée à traiter une commande, il peut y avoir un délai avant que PowerShell réponde à la `Enter-PSSession` commande. Vous êtes connecté dès que la session est disponible. Pour annuler la `Enter-PSSession` commande, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.

Le jeu de paramètres **hostname** a été inclus à partir de PowerShell 6,0. Il a été ajouté pour fournir la communication à distance PowerShell basée sur Secure Shell (SSH). SSH et PowerShell sont tous deux pris en charge sur plusieurs plateformes (Windows, Linux, macOS) et la communication à distance PowerShell fonctionne sur ces plateformes où PowerShell et SSH sont installés et configurés. Cela est différent de la version précédente de Windows uniquement qui est basée sur WinRM, et la plupart des fonctionnalités et limitations spécifiques à WinRM ne s’appliquent pas. Par exemple, les quotas basés sur WinRM, les options de session, la configuration de point de terminaison personnalisée et les fonctionnalités de déconnexion/reconnexion ne sont actuellement pas pris en charge. Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

Avant PowerShell 7.1, la communication à distance via SSH ne prenait pas en charge les sessions à distance de deuxième saut. Cette fonctionnalité était limitée aux sessions qui utilisaient WinRM. PowerShell 7.1 permet à `Enter-PSSession` et `Enter-PSHostProcess` de fonctionner dans n’importe quelle session à distance interactive.

## LIENS CONNEXES

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
