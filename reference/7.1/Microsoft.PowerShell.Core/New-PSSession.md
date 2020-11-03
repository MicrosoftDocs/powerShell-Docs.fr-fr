---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: e5dedf3d161f2687bddfbd09740812d8c5cbaa77
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205673"
---
# New-PSSession

## SYNOPSIS
Crée une connexion persistante à un ordinateur local ou distant.

## SYNTAX

### ComputerName (par défaut)

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### Uri

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### VMId

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### VMName

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### session

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### ContainerId

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### UseWindowsPowerShellParameterSet

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### SSHHost

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### SSHHostHashParam

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## Description

L' `New-PSSession` applet de commande crée une session PowerShell ( **PSSession** ) sur un ordinateur local ou distant. Lorsque vous créez une **session PSSession** , PowerShell établit une connexion permanente à l’ordinateur distant.

Utilisez une **session PSSession** pour exécuter plusieurs commandes qui partagent des données, telles qu’une fonction ou la valeur d’une variable. Pour exécuter des commandes dans une **session PSSession** , utilisez l’applet de commande `Invoke-Command` . Pour utiliser la **session PSSession** pour interagir directement avec un ordinateur distant, utilisez l’applet de commande `Enter-PSSession` . Pour plus d’informations, consultez [about_PSSessions](about/about_PSSessions.md).

Vous pouvez exécuter des commandes sur un ordinateur distant sans créer de **session PSSession** à l’aide des paramètres **ComputerName** de `Enter-PSSession` ou `Invoke-Command` . Quand vous utilisez le paramètre **ComputerName** , PowerShell crée une connexion temporaire qui est utilisée pour la commande et qui est ensuite fermée.

À compter de PowerShell 6,0, vous pouvez utiliser Secure Shell (SSH) pour établir une connexion à et créer une session sur un ordinateur distant, si SSH est disponible sur l’ordinateur local et que l’ordinateur distant est configuré avec un point de terminaison SSH PowerShell. L’avantage d’une session à distance PowerShell basée sur SSH est qu’elle peut fonctionner sur plusieurs plateformes (Windows, Linux, macOS). Pour les sessions SSH, vous utilisez le **nom d’hôte** ou le jeu de paramètres **SSHConnection** pour spécifier l’ordinateur distant et les informations de connexion appropriées. Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

> [!NOTE]
> Lors de l’utilisation de la communication à distance WSMan à partir d’un client Linux ou macOS avec un point de terminaison HTTPs où le certificat de serveur n’est pas approuvé (par exemple, un certificat auto-signé). Vous devez fournir un `PSSessionOption` qui comprend `-SkipCACheck` et `-SkipCNCheck` pour établir correctement la connexion. Ne le faites que si vous êtes dans un environnement dans lequel vous pouvez être certain du certificat de serveur et de la connexion réseau au système cible.

## EXEMPLES

### Exemple 1 : créer une session sur l’ordinateur local

```powershell
$s = New-PSSession
```

Cette commande crée une session **PSSession** sur l’ordinateur local et enregistre la **session PSSession** dans la `$s` variable.

Vous pouvez maintenant utiliser cette **session PSSession** pour exécuter des commandes sur l’ordinateur local.

### Exemple 2 : créer une session sur un ordinateur distant

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

Cette commande crée une **session PSSession** sur l’ordinateur SERVEUR01 et l’enregistre dans la `$Server01` variable.

Lorsque vous créez plusieurs objets **PSSession** , assignez-les à des variables avec des noms utiles. Cela vous aidera à gérer les objets **PSSession** dans les commandes suivantes.

### Exemple 3 : créer des sessions sur plusieurs ordinateurs

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

Cette commande crée trois objets **PSSession** , un sur chacun des ordinateurs spécifiés par le paramètre **ComputerName** .

La commande utilise l’opérateur d’assignation (=) pour assigner les nouveaux objets **PSSession** aux variables : `$s1` , `$s2` , `$s3` . Elle attribue la **session** SERVEUR01 à `$s1` , la session **PSSession** Server02 à `$s2` et la **session PSSession** Server03 à `$s3` .

Lorsque vous assignez plusieurs objets à une série de variables, PowerShell assigne respectivement chaque objet à une variable de la série. S'il y a plus d'objets que de variables, tous les objets restants sont affectés à la dernière variable. S'il y a plus de variables que d'objets, les autres variables sont vides (null).

### Exemple 4 : créer une session avec un port spécifié

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

Cette commande crée une session **PSSession** sur l’ordinateur SERVEUR01 qui se connecte au port 8081 du serveur et utilise le protocole SSL. La nouvelle session **PSSession** utilise une autre configuration de session appelée E12.

Avant de définir le port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant afin d'écouter sur le port 8081. Pour plus d’informations, consultez la description du paramètre de **port** .

### Exemple 5 : créer une session basée sur une session existante

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

Cette commande crée une **session PSSession** avec les mêmes propriétés qu’une **session PSSession** existante. Vous pouvez utiliser ce format de commande lorsque les ressources d’une **session PSSession** existante sont épuisées et qu’une nouvelle **session PSSession** est nécessaire pour décharger une partie de la demande.

La commande utilise le paramètre **session** de `New-PSSession` pour spécifier la session **PSSession** enregistrée dans la `$s` variable. Elle utilise les informations d'identification de l'utilisateur Domain1\Admin01 pour terminer la commande.

### Exemple 6 : créer une session avec une étendue globale dans un autre domaine

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

Cet exemple montre comment créer une **session PSSession** avec une portée globale sur un ordinateur situé dans un autre domaine.

Par défaut, les objets **PSSession** créés sur la ligne de commande sont créés avec une portée locale et les objets **PSSession** créés dans un script ont une portée de script.

Pour créer une **session PSSession** avec une portée globale, créez une **session** PSSession, puis stockez la **session PSSession** dans une variable qui est convertie en portée globale. Dans ce cas, la `$s` variable est convertie en portée globale.

La commande utilise le paramètre **ComputerName** pour spécifier l'ordinateur distant. Étant donné que l’ordinateur se trouve dans un domaine différent de celui du compte d’utilisateur, le nom complet de l’ordinateur est spécifié avec les informations d’identification de l’utilisateur.

### Exemple 7 : créer des sessions pour de nombreux ordinateurs

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

Cette commande crée une session **PSSession** sur chacun des ordinateurs 200 listés dans le fichier Servers.txt et stocke la **session PSSession** résultante dans la `$rs` variable. Les objets **PSSession** ont une limite de limitation de 50.

Vous pouvez utiliser ce format de commande lorsque les noms des ordinateurs sont stockés dans une base de données, une feuille de calcul, un fichier texte ou tout autre format convertible en texte.

### Exemple 8 : créer une session à l’aide d’un URI

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

Cette commande crée une **session PSSession** sur l’ordinateur SERVEUR01 et le stocke dans la `$s` variable. Elle utilise le paramètre **URI** pour spécifier le protocole de transport, l’ordinateur distant, le port et une autre configuration de session. Elle utilise également le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de créer une session sur l’ordinateur distant.

### Exemple 9 : exécuter une tâche en arrière-plan dans un ensemble de sessions

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

Ces commandes créent un ensemble d’objets **PSSession** , puis exécutent une tâche en arrière-plan dans chacun des objets **PSSession** .

La première commande crée une **session PSSession** sur chacun des ordinateurs figurant dans le fichier Servers.txt. Elle utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** . La valeur du paramètre **ComputerName** est une commande qui utilise l' `Get-Content` applet de commande pour obtenir la liste des noms d’ordinateur du fichier Servers.txt.

La commande utilise le paramètre **Credential** pour créer les objets **PSSession** qui ont l’autorisation d’un administrateur de domaine, et elle utilise le paramètre **ThrottleLimit** pour limiter la commande à 16 connexions simultanées. La commande enregistre les objets **PSSession** dans la `$s` variable.

La deuxième commande utilise le paramètre **AsJob** de l' `Invoke-Command` applet de commande pour démarrer une tâche en arrière-plan qui exécute une `Get-Process PowerShell` commande dans chacun des objets **PSSession** dans `$s` .

Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](About/about_Jobs.md) et [about_Remote_Jobs](About/about_Remote_Jobs.md).

### Exemple 10 : créer une session pour un ordinateur à l’aide de son URI

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

Cette commande crée un objet **PSSession** qui se connecte à un ordinateur spécifié par un URI au lieu d’un nom d’ordinateur.

### Exemple 11 : créer une option de session

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

Cet exemple montre comment créer un objet d’option de session et utiliser le paramètre **SessionOption** .

La première commande utilise l' `New-PSSessionOption` applet de commande pour créer une option de session. Elle enregistre l’objet **SessionOption** résultant dans la `$so` variable.

La deuxième commande utilise l'option d'une nouvelle session. La commande utilise l' `New-PSSession` applet de commande pour créer une nouvelle session. La valeur du paramètre SessionOption est l’objet **SessionOption** dans la `$so` variable.

### Exemple 12 : créer une session à l’aide de SSH

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

Cet exemple montre comment créer une **session PSSession** à l’aide de Secure Shell (SSH). Si SSH est configuré sur l’ordinateur distant pour demander des mots de passe, vous recevrez une invite de mot de passe. Dans le cas contraire, vous devrez utiliser l’authentification utilisateur basée sur une clé SSH.

### Exemple 13 : créer une session à l’aide de SSH et spécifier le port et la clé d’authentification utilisateur

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

Cet exemple montre comment créer une **session PSSession** à l’aide de Secure Shell (SSH). Elle utilise le paramètre **port** pour spécifier le port à utiliser et le paramètre **keyFilePath** pour spécifier une clé RSA utilisée pour identifier et authentifier l’utilisateur sur l’ordinateur distant.

### Exemple 14 : créer plusieurs sessions à l’aide de SSH

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

Cet exemple montre comment créer plusieurs sessions à l’aide de Secure Shell (SSH) et du jeu de paramètres **SSHConnection** . Le paramètre **SSHConnection** prend un tableau de tables de hachage qui contiennent des informations de connexion pour chaque session. Notez que cet exemple requiert que SSH soit configuré sur les ordinateurs distants cibles pour prendre en charge l’authentification des utilisateurs basée sur les clés.

## PARAMETERS

### -AllowRedirection

Indique que cette applet de commande autorise la redirection de cette connexion vers un autre Uniform Resource Identifier (URI).

Quand vous utilisez le paramètre **ConnectionURI** , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI. Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.

Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount** . Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la variable de préférence **$PSSessionOption** . La valeur par défaut est 5.

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

Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion.
La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.

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

Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur.
Les valeurs valides pour ce paramètre sont :

- Default
- Basic
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

Spécifie un tableau de noms d’ordinateurs. Cette applet de commande crée une connexion permanente ( **PSSession** ) sur l’ordinateur spécifié. Si vous entrez plusieurs noms d’ordinateur, `New-PSSession` crée plusieurs objets **PSSession** , un pour chaque ordinateur. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs distants. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.). Lorsque l'ordinateur distant se trouve dans un domaine différent de celui de l'utilisateur, le nom de domaine complet est obligatoire. Vous pouvez également diriger un nom d’ordinateur, entre guillemets, vers `New-PSSession` .

Pour utiliser une adresse IP dans la valeur du paramètre **ComputerName** , la commande doit inclure le paramètre **Credential** . En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local. Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).

Pour inclure l’ordinateur local dans la valeur du paramètre **ComputerName** , démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

Spécifie la configuration de session utilisée pour la nouvelle session **PSSession** .

Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session. Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/PowerShell` .

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

Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS. Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs. Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.

Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Spécifie un tableau d’ID de conteneurs. Cette applet de commande démarre une session interactive avec chacun des conteneurs spécifiés. Utilisez la `docker ps` commande pour obtenir la liste des ID de conteneur. Pour plus d’informations, consultez l’aide de la commande [dockr PS](https://docs.docker.com/engine/reference/commandline/ps/) .

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage. Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs. Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.

Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur. Pour créer une session de bouclage, omettez le paramètre **ComputerName** ou définissez sa valeur sur point (.), localhost ou le nom de l’ordinateur local.

Par défaut, cette applet de commande crée des sessions de bouclage à l’aide d’un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.

Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage. Si vous utilisez **EnableNetworkAccess** quand vous créez une session sur un ordinateur distant, la commande s’exécute correctement, mais le paramètre est ignoré.

Vous pouvez également activer l’accès à distance dans une session de bouclage en utilisant la valeur CredSSP du paramètre **Authentication** , qui délègue les informations d’identification de session à d’autres ordinateurs.

Pour protéger l’ordinateur contre les accès malveillants, les sessions de bouclage déconnectées qui ont des jetons interactifs, qui sont créés à l’aide du paramètre **EnableNetworkAccess** , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée. Les sessions déconnectées qui utilisent l'authentification CredSSP peuvent être reconnectées à partir d'autres ordinateurs. Pour plus d'informations, consultez `Disconnect-PSSession`.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Spécifie un tableau de noms d’ordinateurs pour une connexion Secure Shell (SSH). Cela est similaire au paramètre ComputerName, à ceci près que la connexion à l’ordinateur distant s’effectue à l’aide de SSH plutôt que de Windows WinRM.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
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

Spécifie un nom convivial pour la **session PSSession** .

Vous pouvez utiliser le nom pour faire référence à la **session PSSession** quand vous utilisez d’autres applets de commande, telles que `Get-PSSession` et `Enter-PSSession` . Le nom n'a pas obligatoirement à être unique sur l'ordinateur ou dans la session active.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Spécifie le port réseau sur l’ordinateur distant utilisé pour cette connexion. Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion. Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.

Avant d’utiliser un autre port, vous devez configurer l’écouteur WinRM sur l’ordinateur distant pour qu’il écoute sur ce port. Utilisez les commandes suivantes pour configurer l'écouteur :

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé. Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute. Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.

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

Spécifie un tableau d’objets **PSSession** que cette applet de commande utilise comme modèle pour la nouvelle **session PSSession** . Ce paramètre crée de nouveaux objets **PSSession** qui ont les mêmes propriétés que les objets **PSSession** spécifiés.

Entrez une variable qui contient les objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu’une `New-PSSession` commande ou `Get-PSSession` .

Les objets **PSSession** qui en résultent ont les mêmes nom d’ordinateur, nom d’application, URI de connexion, port, nom de configuration, limite de limitation et valeur de protocole SSL (SSL) que les originaux, mais ils ont un nom complet, un ID et un ID d’instance (Guid) différents.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Spécifie les options avancées pour la session. Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.

Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie. Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.

Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session. Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.

Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` . Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md). Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

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

### -SSHConnection

Ce paramètre prend un tableau de tables de hachage dans lequel chaque table de hachage contient un ou plusieurs paramètres de connexion nécessaires pour établir une connexion Secure Shell (SSH) (nom d’hôte, port, nom d’utilisateur, KeyFilePath).

Les paramètres de connexion Hashtable sont les mêmes que ceux définis pour le jeu de paramètres **hostname** .

Le paramètre **SSHConnection** est utile pour créer plusieurs sessions où chaque session requiert des informations de connexion différentes.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
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

### -ThrottleLimit

Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
Si vous omettez ce paramètre ou entrez la valeur 0 (zéro), la valeur par défaut 32 est utilisée.

La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

Spécifie le nom d’utilisateur du compte utilisé pour créer une session sur l’ordinateur distant. La méthode d’authentification de l’utilisateur dépend de la configuration de Secure Shell (SSH) sur l’ordinateur distant.

Si SSH est configuré pour l’authentification de base par mot de passe, vous êtes invité à entrer le mot de passe de l’utilisateur.

Si SSH est configuré pour l’authentification utilisateur basée sur une clé, un chemin d’accès de fichier de clé peut être fourni via le paramètre KeyFilePath et aucune invite de mot de passe n’est générée. Notez que si le fichier de clé de l’utilisateur client se trouve dans un emplacement connu SSH, le paramètre KeyFilePath n’est pas nécessaire pour l’authentification basée sur les clés et l’authentification de l’utilisateur aura lieu automatiquement en fonction du nom d’utilisateur. Pour plus d’informations, consultez la documentation SSH sur l’authentification des utilisateurs basée sur les clés.

Ce paramètre n’est pas obligatoire. Si aucun paramètre de nom d’utilisateur n’est spécifié, le nom d’utilisateur actuellement connecté est utilisé pour la connexion.

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

Indique que cette applet de commande utilise le protocole SSL pour établir une connexion à l’ordinateur distant.
Par défaut, SSL n'est pas utilisé.

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau. Le paramètre **UseSSL** offre une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.

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

Spécifie un tableau d’ID de machines virtuelles. Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés. Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez la commande suivante :

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Spécifie un tableau de noms d'ordinateurs virtuels. Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés. Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez l' `Get-VM` applet de commande.

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Sous-système

Spécifie le sous-système SSH utilisé pour la nouvelle **session PSSession** .

Cela spécifie le sous-système à utiliser sur la cible, tel que défini dans sshd_config.
Le sous-système démarre une version spécifique de PowerShell avec des paramètres prédéfinis.
Si le sous-système spécifié n’existe pas sur l’ordinateur distant, la commande échoue.

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

### -UseWindowsPowerShell

{{Renseigner la description UseWindowsPowerShell}}

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. String, System. URI, System. Management. Automation. instances d’exécution. PSSession

Vous pouvez diriger une chaîne, un URI ou un objet de session vers cette applet de commande.

## SORTIES

### System. Management. Automation. instances d’exécution. PSSession

## REMARQUES

- Cette applet de commande utilise l’infrastructure de communication à distance PowerShell. Pour utiliser cette applet de commande, l’ordinateur local et les ordinateurs distants doivent être configurés pour la communication à distance PowerShell. Pour plus d'informations, consultez [about_Remote_Requirements](About/about_Remote_Requirements.md).
- Pour créer une **session PSSession** sur l’ordinateur local, démarrez PowerShell avec l’option Exécuter en tant qu’administrateur.
- Lorsque vous avez terminé avec la **session PSSession** , utilisez l' `Remove-PSSession` applet de commande pour supprimer la **session PSSession** et libérer ses ressources.
- Les jeux de paramètres **hostname** et **SSHConnection** ont été inclus à partir de PowerShell 6,0.
  Elles ont été ajoutées pour fournir une communication à distance PowerShell basée sur Secure Shell (SSH). SSH et PowerShell sont tous deux pris en charge sur plusieurs plateformes (Windows, Linux, macOS) et la communication à distance PowerShell fonctionne sur ces plateformes où PowerShell et SSH sont installés et configurés. Cela est différent de la version précédente de Windows uniquement qui est basée sur WinRM, et la plupart des fonctionnalités et limitations spécifiques à WinRM ne s’appliquent pas. Par exemple, les quotas basés sur WinRM, les options de session, la configuration de point de terminaison personnalisée et les fonctionnalités de déconnexion/reconnexion ne sont actuellement pas pris en charge. Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## LIENS CONNEXES

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

