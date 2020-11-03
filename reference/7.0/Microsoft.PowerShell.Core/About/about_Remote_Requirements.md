---
description: Décrit la configuration requise et la configuration requise pour l’exécution de commandes distantes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: dc744a7c945bfccb876087ba8b13413674c52dd5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208162"
---
# <a name="about-remote-requirements"></a>À propos des exigences à distance

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit la configuration requise et la configuration requise pour l’exécution de commandes distantes dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Cette rubrique décrit la configuration requise, les exigences des utilisateurs et les ressources requises pour établir des connexions à distance et exécuter des commandes distantes dans PowerShell. Il fournit également des instructions pour la configuration des opérations à distance.

Remarque : de nombreuses cmdlets (y compris les applets de commande obtenir-service, obtenir-traiter, obtenir-WMIObject, obtenir-EventLog et Get-WinEvent) obtiennent des objets à partir d’ordinateurs distants à l’aide des méthodes de Microsoft .NET Framework pour récupérer les objets. Ils n’utilisent pas l’infrastructure de communication à distance PowerShell. Les conditions requises dans ce document ne s’appliquent pas à ces applets de commande.

Pour rechercher les applets de commande qui ont un paramètre ComputerName, mais n’utilisez pas la communication à distance PowerShell, lisez la description du paramètre ComputerName des applets de commande.

## <a name="system-requirements"></a>CONFIGURATION SYSTÈME REQUISE

Pour exécuter des sessions à distance sur Windows PowerShell 3,0, les ordinateurs locaux et distants doivent disposer des éléments suivants :

- Windows PowerShell 3,0 ou version ultérieure
- Le Microsoft .NET Framework 4 ou version ultérieure
- Windows Remote Management 3,0

Pour exécuter des sessions à distance sur Windows PowerShell 2,0, les ordinateurs locaux et distants doivent disposer des éléments suivants :

- Windows PowerShell 2,0 ou version ultérieure
- Le Microsoft .NET Framework 2,0 ou version ultérieure
- Windows Remote Management 2,0

Vous pouvez créer des sessions à distance entre des ordinateurs exécutant Windows PowerShell 2,0 et Windows PowerShell 3,0. Toutefois, les fonctionnalités qui s’exécutent uniquement sur Windows PowerShell 3,0, telles que la possibilité de se déconnecter et de se reconnecter aux sessions, sont disponibles uniquement lorsque les deux ordinateurs exécutent Windows PowerShell 3,0.

Pour rechercher le numéro de version d’une version installée de PowerShell, utilisez la variable automatique $PSVersionTable.

Windows Remote Management (WinRM) 3,0 et Microsoft .NET Framework 4 sont inclus dans Windows 8, Windows Server 2012 et les versions plus récentes du système d’exploitation Windows. WinRM 3,0 est inclus dans Windows Management Framework 3,0 pour les systèmes d’exploitation plus anciens. Si l’ordinateur ne dispose pas de la version requise de WinRM ou du Framework Microsoft .NET, l’installation échoue.

## <a name="user-permissions"></a>AUTORISATIONS DE L’UTILISATEUR

Pour créer des sessions à distance et exécuter des commandes à distance, par défaut, l’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur distant ou fournir les informations d’identification d’un administrateur. Sinon, la commande échoue.

Les autorisations requises pour créer des sessions et exécuter des commandes sur un ordinateur distant (ou dans une session à distance sur l’ordinateur local) sont établies par la configuration de session (également appelée « point de terminaison ») sur l’ordinateur distant auquel la session se connecte. Plus précisément, le descripteur de sécurité de la configuration de session détermine qui a accès à la configuration de session et qui peut l’utiliser pour se connecter.

Les descripteurs de sécurité sur les configurations de session par défaut, Microsoft. PowerShell, Microsoft. PowerShell32 et Microsoft. PowerShell. Workflow, autorisent l’accès uniquement aux membres du groupe administrateurs.

Si l’utilisateur actuel n’est pas autorisé à utiliser la configuration de session, la commande permettant d’exécuter une commande (qui utilise une session temporaire) ou de créer une session persistante sur l’ordinateur distant échoue. L’utilisateur peut utiliser le paramètre ConfigurationName des applets de commande qui créent des sessions pour sélectionner une autre configuration de session, si celle-ci est disponible.

Les membres du groupe Administrateurs sur un ordinateur peuvent déterminer qui est autorisé à se connecter à distance à l’ordinateur en modifiant les descripteurs de sécurité sur les configurations de session par défaut et en créant de nouvelles configurations de session avec des descripteurs de sécurité différents.

Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](about_Session_Configurations.md).

## <a name="windows-network-locations"></a>EMPLACEMENTS RÉSEAU WINDOWS

À compter de Windows PowerShell 3,0, l’applet de commande Enable-PSRemoting peut activer la communication à distance sur les versions client et serveur de Windows sur des réseaux privés, de domaine et publics.

Sur les versions serveur de Windows avec des réseaux privés et de domaine, l’applet de commande Enable-PSRemoting crée des règles de pare-feu qui autorisent l’accès à distance illimité. Il crée également une règle de pare-feu pour les réseaux publics qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local. Cette règle de pare-feu de sous-réseau local est activée par défaut sur les versions serveur de Windows sur les réseaux publics, mais Enable-PSRemoting réapplique la règle en cas de modification ou de suppression.

Sur les versions client de Windows avec des réseaux privés et de domaine, par défaut, l’applet de commande Enable-PSRemoting crée des règles de pare-feu qui autorisent l’accès à distance illimité.

Pour activer la communication à distance sur les versions client de Windows avec des réseaux publics, utilisez le paramètre SkipNetworkProfileCheck de l’applet de commande Enable-PSRemoting. Il crée une règle de pare-feu qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local.

Pour supprimer la restriction de sous-réseau local sur les réseaux publics et autoriser l’accès à distance à partir de tous les emplacements sur les versions client et serveur de Windows, utilisez l’applet de commande Set-NetFirewallRule dans le module netsecurity. Exécutez la commande suivante :

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

Dans Windows PowerShell 2,0, sur les versions serveur de Windows, Enable-PSRemoting crée des règles de pare-feu qui autorisent l’accès à distance sur tous les réseaux.

Dans Windows PowerShell 2,0, sur les versions client de Windows, Enable-PSRemoting ne crée des règles de pare-feu que sur les réseaux privés et de domaine. Si l’emplacement réseau est public, Enable-PSRemoting échoue.

## <a name="run-as-administrator"></a>EXÉCUTER EN TANT QU’ADMINISTRATEUR

Des privilèges d’administrateur sont requis pour les opérations de communication à distance suivantes :

- Établissement d’une connexion à distance à l’ordinateur local. Ce scénario est communément appelé « bouclage ».

- Gestion des configurations de session sur l’ordinateur local.

- Affichage et modification des paramètres de WS-Management sur l’ordinateur local. Il s’agit des paramètres du nœud LocalHost du lecteur WSMAN :.

Pour effectuer ces tâches, vous devez démarrer PowerShell avec l’option « Exécuter en tant qu’administrateur », même si vous êtes membre du groupe Administrateurs sur l’ordinateur local.

Dans Windows 7 et Windows Server 2008 R2, pour démarrer Windows PowerShell avec l’option « Exécuter en tant qu’administrateur » :

1. Cliquez sur Démarrer, sur tous les programmes, sur accessoires, puis sur le dossier Windows PowerShell.
2. Cliquez avec le bouton droit sur Windows PowerShell, puis cliquez sur Exécuter en tant qu’administrateur.

Pour démarrer Windows PowerShell avec l’option « Exécuter en tant qu’administrateur » :

1. Cliquez sur Démarrer, sur tous les programmes, puis sur le dossier Windows PowerShell.
2. Cliquez avec le bouton droit sur Windows PowerShell, puis cliquez sur Exécuter en tant qu’administrateur.

L’option « Exécuter en tant qu’administrateur » est également disponible dans d’autres entrées de l’Explorateur Windows pour Windows PowerShell, y compris les raccourcis. Il vous suffit de cliquer avec le bouton droit sur l’élément, puis de cliquer sur « Exécuter en tant qu’administrateur ».

Quand vous démarrez Windows PowerShell à partir d’un autre programme, tel que Cmd.exe, utilisez l’option « Exécuter en tant qu’administrateur » pour démarrer le programme.

## <a name="how-to-configure-your-computer-for-remoting"></a>COMMENT CONFIGURER VOTRE ORDINATEUR POUR LA COMMUNICATION À DISTANCE

Les ordinateurs exécutant toutes les versions de Windows prises en charge peuvent établir des connexions à distance à et exécuter des commandes distantes dans PowerShell sans aucune configuration. Toutefois, pour recevoir des connexions et autoriser les utilisateurs à créer des sessions PowerShell locales et distantes gérées par l’utilisateur (« sessions PSSession ») et à exécuter des commandes sur l’ordinateur local, vous devez activer la communication à distance PowerShell sur l’ordinateur.

Windows Server 2012 et les versions plus récentes de Windows Server sont activés par défaut pour la communication à distance PowerShell. Si les paramètres sont modifiés, vous pouvez restaurer les paramètres par défaut en exécutant l’applet de commande Enable-PSRemoting.

Sur toutes les autres versions prises en charge de Windows, vous devez exécuter l’applet de commande Enable-PSRemoting pour activer la communication à distance PowerShell.

Les fonctionnalités de communication à distance de PowerShell sont prises en charge par le service WinRM, qui est l’implémentation Microsoft du protocole WS-Management (Web Services for Management). Lorsque vous activez la communication à distance PowerShell, vous modifiez la configuration par défaut de WS-Management et ajoutez la configuration du système qui permet aux utilisateurs de se connecter à WS-Management.

Pour configurer PowerShell pour recevoir des commandes à distance :

1. Démarrez PowerShell avec l’option « Exécuter en tant qu’administrateur ».
2. À l’invite de commandes, tapez : `Enable-PSRemoting`

Pour vérifier que la communication à distance est correctement configurée, exécutez une commande de test telle que la commande suivante, qui crée une session à distance sur l’ordinateur local.

```powershell
New-PSSession
```

Si la communication à distance est correctement configurée, la commande crée une session sur l’ordinateur local et retourne un objet qui représente la session. La sortie doit ressembler à l’exemple de sortie suivant :

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

Si la commande échoue, pour obtenir de l’aide, consultez [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).

## <a name="understand-policies"></a>COMPRENDRE LES STRATÉGIES

Lorsque vous travaillez à distance, vous utilisez deux instances de PowerShell, l’une sur l’ordinateur local et l’autre sur l’ordinateur distant. Par conséquent, votre travail est affecté par les stratégies Windows et les stratégies PowerShell sur les ordinateurs locaux et distants.

En général, avant de vous connecter et lorsque vous établissez la connexion, les stratégies sur l’ordinateur local sont activées. Lorsque vous utilisez la connexion, les stratégies sur l’ordinateur distant sont en vigueur.

## <a name="basic-authentication-limitations-on-linux-and-macos"></a>Limitations de l’authentification de base sur Linux et macOS

Lors de la connexion d’un système Linux ou macOS à Windows, l’authentification de base sur HTTP n’est pas prise en charge. L’authentification de base peut être utilisée sur HTTPs en installant un certificat sur le serveur cible. Le certificat doit avoir un nom CN qui correspond au nom d’hôte, n’a pas expiré ou n’a pas été révoqué. Un certificat auto-signé peut être utilisé à des fins de test.

Pour plus d’informations, consultez [procédure : configurer WINRM pour HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) .

La commande suivante, exécutée à partir d’une invite de commandes avec élévation de privilèges, configure l’écouteur HTTPs sur Windows avec le certificat installé.

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

Sur le côté Linux ou macOS, sélectionnez de base pour authentification et-UseSSl.

> Remarque : l’authentification de base ne peut pas être utilisée avec les comptes de domaine ; un compte local est requis et le compte doit se trouver dans le groupe administrateurs.

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

Une alternative à l’authentification de base sur HTTPs est Negotiate. Cela entraîne l’authentification NTLM entre le client et le serveur, et la charge utile est chiffrée via HTTP.

L’exemple suivant illustre l’utilisation de Negotiate avec New-PSSession :

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> Windows Server nécessite un paramètre de Registre supplémentaire pour permettre aux administrateurs, autres que l’administrateur intégré, de se connecter à l’aide de NTLM.
> Reportez-vous au paramètre de Registre LocalAccountTokenFilterPolicy sous négocier l’authentification dans [l’authentification pour les connexions à distance](/windows/win32/winrm/authentication-for-remote-connections)

## <a name="see-also"></a>VOIR AUSSI

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
