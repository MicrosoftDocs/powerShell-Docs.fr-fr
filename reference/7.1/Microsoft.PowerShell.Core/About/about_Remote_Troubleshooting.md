---
description: Décrit comment résoudre les problèmes liés aux opérations distantes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: f19cb90a8671cbe0885af817b0cd8849adc79338
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208934"
---
# <a name="about-remote-troubleshooting"></a>À propos du dépannage à distance

## <a name="short-description"></a>Description courte
Décrit comment résoudre les problèmes liés aux opérations distantes dans PowerShell.

## <a name="long-description"></a>Description longue

Cette section décrit certains des problèmes que vous pouvez rencontrer lors de l’utilisation des fonctionnalités de communication à distance de PowerShell basées sur la technologie de WS-Management et qui suggère des solutions à ces problèmes.

Avant d’utiliser la communication à distance PowerShell, consultez [about_Remote](about_remote.md) et [about_Remote_Requirements](about_Remote_Requirements.md) pour obtenir des conseils sur la configuration et l’utilisation de base. En outre, les rubriques d’aide de chacune des applets de commande de communication à distance, en particulier les descriptions des paramètres, ont des informations utiles conçues pour vous aider à éviter les problèmes.

> [!NOTE]
> Pour afficher ou modifier les paramètres de l’ordinateur local sur le lecteur WSMan :, y compris les modifications apportées aux configurations de session, aux hôtes approuvés, aux ports ou aux écouteurs, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

## <a name="troubleshooting-permission-and-authentication-issues"></a>Résolution des problèmes d’autorisation et d’authentification

Cette section traite des problèmes de communication à distance liés aux autorisations de l’utilisateur et de l’ordinateur et aux exigences de communication à distance.

### <a name="how-to-run-as-administrator"></a>Comment exécuter en tant qu’administrateur

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

Pour démarrer une session à distance sur l’ordinateur local, ou pour afficher ou modifier les paramètres de l’ordinateur local dans le lecteur WSMan :, y compris les modifications apportées aux configurations de session, aux hôtes approuvés, aux ports ou aux écouteurs, démarrez Windows PowerShell avec l’option **exécuter en tant qu’administrateur** .

Pour démarrer Windows PowerShell avec l’option **exécuter en tant qu’administrateur** :

- Cliquez avec le bouton droit sur une icône Windows PowerShell (ou Windows PowerShell ISE), puis cliquez sur **exécuter en tant qu’administrateur**.

  Pour démarrer Windows PowerShell avec l’option **exécuter en tant qu’administrateur** dans Windows 7 et windows Server 2008 R2.

- Dans la barre des tâches Windows, cliquez avec le bouton droit sur l’icône Windows PowerShell, puis cliquez sur **exécuter en tant qu’administrateur**.

  Dans Windows Server 2008 R2, l’icône Windows PowerShell est épinglée par défaut à la barre des tâches.

### <a name="how-to-enable-remoting"></a>Comment activer la communication à distance

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

Aucune configuration n’est requise pour permettre à un ordinateur d’envoyer des commandes distantes.
Toutefois, pour recevoir des commandes à distance, la communication à distance PowerShell doit être activée sur l’ordinateur. L’activation de comprend le démarrage du service WinRM, la définition du type de démarrage pour le service WinRM sur automatique, la création d’écouteurs pour les connexions HTTP et HTTPs et la création de configurations de session par défaut.

La communication à distance Windows PowerShell est activée sur Windows Server 2012 et les versions plus récentes de Windows Server par défaut. Sur tous les autres systèmes, exécutez l' `Enable-PSRemoting` applet de commande pour activer la communication à distance. Vous pouvez également exécuter l' `Enable-PSRemoting` applet de commande pour réactiver la communication à distance sur Windows server 2012 et les versions plus récentes de Windows Server si la communication à distance est désactivée.

Pour configurer un ordinateur pour qu’il reçoive des commandes à distance, utilisez l’applet de commande `Enable-PSRemoting` . La commande suivante active tous les paramètres distants requis, active les configurations de session et redémarre le service WinRM pour que les modifications soient effectives.

`Enable-PSRemoting`

Pour supprimer toutes les invites utilisateur, tapez :

`Enable-PSRemoting -Force`

Pour plus d’informations, consultez [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).

### <a name="how-to-enable-remoting-in-an-enterprise"></a>Comment activer la communication à distance dans une entreprise

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Pour permettre à un seul ordinateur de recevoir des commandes PowerShell à distance et d’accepter des connexions, utilisez l’applet de commande `Enable-PSRemoting` .

Pour activer la communication à distance pour plusieurs ordinateurs dans une entreprise, vous pouvez utiliser les options mises à l’échelle suivantes.

- Pour configurer des écouteurs pour la communication à distance, activez la stratégie **de groupe autoriser la configuration automatique des écouteurs** .

- Pour définir le type de démarrage du Windows Remote Management (WinRM) sur automatique sur plusieurs ordinateurs, utilisez l' `Set-Service` applet de commande.

- Pour activer une exception de pare-feu, utilisez la stratégie de groupe **pare-feu Windows : autoriser les exceptions de port local** .

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a>Comment activer des écouteurs à l’aide d’une stratégie de groupe

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Pour configurer les écouteurs pour tous les ordinateurs d’un domaine, activez la stratégie **autoriser la configuration automatique des écouteurs** dans le chemin d’accès stratégie de groupe suivant :

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

Activez la stratégie et spécifiez les filtres IPv4 et IPv6. Les caractères génériques ( `*` ) sont autorisés.

### <a name="how-to-enable-remoting-on-public-networks"></a>Comment activer la communication à distance sur des réseaux publics

```
ERROR:  Unable to check the status of the firewall
```

L' `Enable-PSRemoting` applet de commande renvoie cette erreur lorsque le réseau local est public et que le paramètre **SkipNetworkProfileCheck** n’est pas utilisé dans la commande.

Sur les versions serveur de Windows, `Enable-PSRemoting` fonctionne sur tous les types d’emplacement réseau. Elle crée des règles de pare-feu qui autorisent l’accès à distance aux réseaux privés et de domaine (« personnel » et « de travail »). Pour les réseaux publics, elle crée des règles de pare-feu qui autorisent l’accès à distance à partir du même sous-réseau local.

Sur les versions client de Windows, `Enable-PSRemoting` fonctionne sur les réseaux privés et de domaine. Par défaut, elle échoue sur les réseaux publics, mais si vous utilisez le paramètre **SkipNetworkProfileCheck** , `Enable-PSRemoting` réussit et crée une règle de pare-feu qui autorise le trafic à partir du même sous-réseau local.

Pour supprimer la restriction de sous-réseau local sur les réseaux publics et autoriser l’accès à distance à partir de n’importe quel emplacement, exécutez la commande suivante :

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

L' `Set-NetFirewallRule` applet de commande est exportée par le module netsecurity.

> [!NOTE]
> Dans Windows PowerShell 2,0, sur les ordinateurs exécutant des versions serveur de Windows, `Enable-PSRemoting` crée des règles de pare-feu qui autorisent l’accès à distance sur des réseaux privés, de domaine et publics. Sur les ordinateurs qui exécutent des versions client de Windows, `Enable-PSRemoting` crée des règles de pare-feu qui autorisent l’accès à distance uniquement sur les réseaux privés et de domaine.

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a>Comment activer une exception de pare-feu à l’aide d’une stratégie de groupe

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Pour activer une exception de pare-feu pour dans tous les ordinateurs d’un domaine, activez la stratégie **pare-feu Windows : autoriser les exceptions de port local** dans le chemin d’accès stratégie de groupe suivant :

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

Cette stratégie permet aux membres du groupe Administrateurs sur l’ordinateur d’utiliser le **pare-feu Windows** dans le **panneau de configuration** pour créer une exception de pare-feu pour le service Windows Remote Management.

Si la configuration de la stratégie est incorrecte, vous pouvez recevoir l’erreur suivante :

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

Une erreur de configuration dans la stratégie génère une valeur vide pour la propriété **ListeningOn** . Utilisez la commande suivante pour vérifier la valeur.

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a>Comment définir le type de démarrage du service WinRM

```
ERROR:  ACCESS IS DENIED
```

La communication à distance PowerShell dépend du service Windows Remote Management (WinRM).
Le service doit être en cours d’exécution pour prendre en charge les commandes distantes.

Sur les versions serveur de Windows, le type de démarrage du service Windows Remote Management (WinRM) est automatique.

Toutefois, sur les versions client de Windows, le service WinRM est désactivé par défaut.

Pour définir le type de démarrage d’un service sur un ordinateur distant, utilisez l’applet de commande `Set-Service` .

Pour exécuter la commande sur plusieurs ordinateurs, vous pouvez créer un fichier texte ou un fichier CSV portant le nom de l’ordinateur.

Par exemple, les commandes suivantes obtiennent une liste de noms d’ordinateurs à partir du `Servers.txt` fichier, puis définit le type de démarrage du service WinRM sur tous les ordinateurs sur **automatique**.

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

Pour afficher les résultats, utilisez l' `Get-WMIObject` applet de commande avec l’objet **Win32_Service** . Pour plus d’informations, consultez [set-service](xref:Microsoft.PowerShell.Management.Set-Service).

### <a name="how-to-recreate-the-default-session-configurations"></a>Comment recréer les configurations de session par défaut

```
ERROR:  ACCESS IS DENIED
```

Pour vous connecter à l’ordinateur local et exécuter des commandes à distance, l’ordinateur local doit inclure des configurations de session pour les commandes distantes.

Lorsque vous utilisez `Enable-PSRemoting` , il crée des configurations de session par défaut sur l’ordinateur local. Les utilisateurs distants utilisent ces configurations de session chaque fois qu’une commande à distance n’inclut pas le paramètre **ConfigurationName** .

Si les configurations par défaut sur un ordinateur ne sont pas inscrites ou supprimées, utilisez l' `Enable-PSRemoting` applet de commande pour les recréer. Vous pouvez utiliser cette applet de commande à plusieurs reprises. Elle ne génère pas d’erreurs si une fonctionnalité est déjà configurée.

Si vous modifiez les configurations de session par défaut et souhaitez restaurer les configurations de session par défaut d’origine, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer les configurations de session modifiées, puis utilisez l' `Enable-PSRemoting` applet de commande pour les restaurer.
`Enable-PSRemoting` ne modifie pas les configurations de session existantes.

> [!NOTE]
> Lorsque `Enable-PSRemoting` restaure la configuration de session par défaut, elle ne crée pas de descripteurs de sécurité explicites pour les configurations. Au lieu de cela, les configurations héritent du descripteur de sécurité de RootSDDL, qui est sécurisé par défaut.

Pour afficher le descripteur de sécurité RootSDDL, tapez :

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

Pour modifier le RootSDDL, utilisez l' `Set-Item` applet de commande dans le lecteur WSMan :. Pour modifier le descripteur de sécurité d’une configuration de session, utilisez l’applet de commande `Set-PSSessionConfiguration` avec les paramètres **SecurityDescriptorSDDL** ou **ShowSecurityDescriptorUI** .

Pour plus d’informations sur le lecteur WSMan :, consultez la rubrique d’aide pour le fournisseur WSMan (« obtenir-Help WSMan »).

### <a name="how-to-provide-administrator-credentials"></a>Comment fournir des informations d’identification d’administrateur

```
ERROR:  ACCESS IS DENIED
```

Pour créer une session PSSession ou exécuter des commandes sur un ordinateur distant, par défaut, l’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur distant. Les informations d’identification sont parfois nécessaires même lorsque l’utilisateur actuel est connecté à un compte membre du groupe administrateurs.

Si l’utilisateur actuel est membre du groupe Administrateurs sur l’ordinateur distant, ou peut fournir les informations d’identification d’un membre du groupe administrateurs, utilisez le paramètre **Credential** des `New-PSSession` `Enter-PSSession` `Invoke-Command` applets de commande ou pour vous connecter à distance.

Par exemple, la commande suivante fournit les informations d’identification d’un administrateur.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

Pour plus d’informations sur le paramètre **Credential** , consultez [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) ou [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).

### <a name="how-to-enable-remoting-for-non-administrative-users"></a>Comment activer la communication à distance pour les utilisateurs non-administrateurs

```
ERROR:  ACCESS IS DENIED
```

Pour établir une session PSSession ou exécuter une commande sur un ordinateur distant, l’utilisateur doit avoir l’autorisation d’utiliser les configurations de session sur l’ordinateur distant.

Par défaut, seuls les membres du groupe Administrateurs sur un ordinateur sont autorisés à utiliser les configurations de session par défaut. Par conséquent, seuls les membres du groupe administrateurs peuvent se connecter à l’ordinateur à distance.

Pour permettre à d’autres utilisateurs de se connecter à l’ordinateur local, accordez à l’utilisateur des autorisations d’exécution sur les configurations de session par défaut sur l’ordinateur local.

La commande suivante ouvre une feuille de propriétés qui vous permet de modifier le descripteur de sécurité de la configuration de session Microsoft. PowerShell par défaut sur l’ordinateur local.

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

Pour plus d’informations, consultez [about_session_configurations](about_Session_Configurations.md).

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a>Comment activer la communication à distance pour les administrateurs dans d’autres domaines

```
ERROR:  ACCESS IS DENIED
```

Lorsqu’un utilisateur d’un autre domaine est membre du groupe Administrateurs sur l’ordinateur local, l’utilisateur ne peut pas se connecter à distance à l’ordinateur local avec des privilèges d’administrateur. Par défaut, les connexions à distance à partir d’autres domaines s’exécutent avec uniquement des jetons de privilège d’utilisateur standard.

Toutefois, vous pouvez utiliser l’entrée de Registre **LocalAccountTokenFilterPolicy** pour modifier le comportement par défaut et autoriser les utilisateurs distants qui sont membres du groupe administrateurs à s’exécuter avec des privilèges d’administrateur.

> [!CAUTION]
> L’entrée **LocalAccountTokenFilterPolicy** désactive les restrictions distantes du contrôle de compte d’utilisateur pour tous les utilisateurs de tous les ordinateurs concernés. Examinez attentivement les implications de ce paramètre avant de modifier la stratégie.

Pour modifier la stratégie, utilisez la commande suivante pour définir la valeur de l’entrée de Registre **LocalAccountTokenFilterPolicy** sur 1.

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a>Utilisation d’une adresse IP dans une commande à distance

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

Le paramètre **ComputerName** des `New-PSSession` applets de commande, `Enter-PSSession` et `Invoke-Command` accepte une adresse IP en tant que valeur valide. Toutefois, étant donné que l’authentification Kerberos ne prend pas en charge les adresses IP, l’authentification NTLM est utilisée par défaut chaque fois que vous spécifiez une adresse IP.

Lorsque vous utilisez l’authentification NTLM, la procédure suivante est requise pour la communication à distance.

1. Configurez l’ordinateur pour le transport HTTPs ou ajoutez les adresses IP des ordinateurs distants à la liste TrustedHosts sur l’ordinateur local.

1. Utilisez le paramètre **Credential** dans toutes les commandes distantes.

   Cela est nécessaire même lorsque vous soumettez les informations d’identification de l’utilisateur actuel.

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a>Connexion à distance à partir d’un ordinateur basé sur un groupe de travail

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

Lorsque l’ordinateur local n’est pas dans un domaine, la procédure suivante est requise pour la communication à distance.

1. Configurez l’ordinateur pour le transport HTTPs ou ajoutez les noms des ordinateurs distants à la liste TrustedHosts sur l’ordinateur local.

1. Vérifiez qu’un mot de passe est défini sur l’ordinateur basé sur un groupe de travail. Si un mot de passe n’est pas défini ou si la valeur du mot de passe est vide, vous ne pouvez pas exécuter de commandes distantes.

   Pour définir le mot de passe de votre compte d’utilisateur, utilisez comptes d’utilisateur dans le panneau de configuration.

1. Utilisez le paramètre **Credential** dans toutes les commandes distantes.

   Cela est nécessaire même lorsque vous soumettez les informations d’identification de l’utilisateur actuel.

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a>Comment ajouter un ordinateur à la liste des hôtes approuvés

L’élément TrustedHosts peut contenir une liste séparée par des virgules de noms d’ordinateur, d’adresses IP et de noms de domaine complets. Les caractères génériques sont autorisés.

Pour afficher ou modifier la liste des hôtes approuvés, utilisez le lecteur WSMan :. L’élément TrustedHost est dans le `WSMan:\localhost\Client` nœud.

Seuls les membres du groupe Administrateurs sur l’ordinateur sont autorisés à modifier la liste des hôtes approuvés sur l’ordinateur.

ATTENTION : la valeur que vous définissez pour l’élément TrustedHosts affecte tous les utilisateurs de l’ordinateur.

Pour afficher la liste des hôtes approuvés, utilisez la commande suivante :

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

Vous pouvez également utiliser l' `Set-Location` applet de commande (alias = CD) pour naviguer dans le lecteur WSMan : vers l’emplacement. Par exemple :

```powershell
cd WSMan:\localhost\Client; dir
```

Pour ajouter tous les ordinateurs à la liste des hôtes approuvés, utilisez la commande suivante, qui place la valeur * (tout) dans le nom de l’ordinateur

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

Vous pouvez également utiliser un caractère générique ( `*` ) pour ajouter tous les ordinateurs d’un domaine particulier à la liste des hôtes approuvés. Par exemple, la commande suivante ajoute tous les ordinateurs du domaine fabrikam à la liste des hôtes approuvés.

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

Pour ajouter les noms de certains ordinateurs à la liste des hôtes approuvés, utilisez le format de commande suivant :

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

où chaque valeur `<ComputerName>` doit avoir le format suivant :

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

Par exemple :

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

Pour ajouter un nom d'ordinateur à une liste existante d'hôtes approuvés, enregistrez d'abord la valeur actuelle dans une variable, puis affectez-lui une liste séparée par des virgules qui inclut les valeurs actuelles et nouvelles.

Par exemple, pour ajouter l'ordinateur Serveur01 à une liste existante d'hôtes approuvés, utilisez la commande suivante :

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

Pour ajouter les adresses IP d’ordinateurs particuliers à la liste des hôtes approuvés, utilisez le format de commande suivant :

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

Par exemple :

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

Pour ajouter un ordinateur à la liste TrustedHosts d’un ordinateur distant, utilisez l' `Connect-WSMan` applet de commande pour ajouter un nœud pour l’ordinateur distant au lecteur WSMan : sur l’ordinateur local. Utilisez ensuite une `Set-Item` commande pour ajouter l’ordinateur.

Pour plus d’informations sur l’applet de commande `Connect-WSMan` , consultez [connect-wsman](xref:Microsoft.WSMan.Management.Connect-WSMan).

## <a name="troubleshooting-computer-configuration-issues"></a>Résolution des problèmes de configuration de l’ordinateur

Cette section traite des problèmes de communication à distance liés à des configurations particulières d’un ordinateur, d’un domaine ou d’une entreprise.

### <a name="how-to-configure-remoting-on-alternate-ports"></a>Comment configurer la communication à distance sur d’autres ports

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

La communication à distance PowerShell utilise le port 80 pour le transport HTTP par défaut. Le port par défaut est utilisé chaque fois que l’utilisateur ne spécifie pas les paramètres **ConnectionUri** ou **port** dans une commande à distance.

Pour modifier le port par défaut utilisé par PowerShell, utilisez `Set-Item` l’applet de commande du lecteur WSMan : pour modifier la valeur du port dans le nœud terminal de l’écouteur.

Par exemple, la commande suivante change le port par défaut en 8080.

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a>Comment configurer la communication à distance avec un serveur proxy

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

Étant donné que la communication à distance PowerShell utilise le protocole HTTP, elle est affectée par les paramètres du proxy HTTP. Dans les entreprises qui ont des serveurs proxy, les utilisateurs ne peuvent pas accéder directement à un ordinateur distant PowerShell.

Pour résoudre ce problème, utilisez les options de paramètre de proxy dans votre commande à distance. Les options suivantes sont disponibles :

- ProxyAccessType
- ProxyAuthentication
- ProxyCredential

Pour définir ces options pour une commande particulière, utilisez la procédure suivante :

1. Utilisez les paramètres **ProxyAccessType** , **ProxyAuthentication** et **ProxyCredential** de l' `New-PSSessionOption` applet de commande pour créer un objet d’option de session avec les paramètres de proxy de votre entreprise. Enregistrer l’objet option est une variable.

1. Utilisez la variable qui contient l’objet option comme valeur du paramètre **SessionOption** d’une `New-PSSession` `Enter-PSSession` commande, ou `Invoke-Command` .

Par exemple, la commande suivante crée un objet d’option de session avec des options de session proxy, puis utilise l’objet pour créer une session à distance.

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

Pour plus d’informations sur l’applet de commande `New-PSSessionOption` , consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

Pour définir ces options pour toutes les commandes distantes dans la session active, utilisez l’objet option qui `New-PSSessionOption` crée dans la valeur de la `$PSSessionOption` variable de préférence. Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md).

Pour définir ces options pour toutes les commandes à distance, toutes les sessions PowerShell sur l’ordinateur local, ajoutez la `$PSSessionOption` variable de préférence à votre profil PowerShell. Pour plus d’informations sur les profils PowerShell, voir [about_Profiles](about_Profiles.md).

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a>Comment détecter une session 32 bits sur un ordinateur 64 bits

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Si l’ordinateur distant exécute une version 64 bits de Windows et que la commande à distance utilise une configuration de session 32 bits, telle que Microsoft. PowerShell32, Windows Remote Management (WinRM) charge un processus WOW64 et Windows redirige automatiquement toutes les références à l' `$env:Windir\System32` annuaire vers le `$env:Windir\SysWOW64` répertoire.

Par conséquent, si vous essayez d’utiliser les outils du répertoire system32 qui n’ont pas d’équivalent dans le répertoire SysWow64, par exemple `Defrag.exe` , les outils sont introuvables dans le répertoire.

Pour Rechercher l’architecture de processeur utilisée dans la session, utilisez la valeur de la variable d’environnement **PROCESSOR_ARCHITECTURE** . La commande suivante recherche l’architecture de processeur de la session dans la `$s` variable.

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](about_Session_Configurations.md).

## <a name="troubleshooting-policy-and-preference-issues"></a>Résolution des problèmes de stratégie et de préférence

Cette section traite des problèmes de communication à distance liés aux stratégies et aux préférences définies sur les ordinateurs locaux et distants.

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a>Comment modifier la stratégie d’exécution pour Import-PSSession et Import-Module

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

Les `Import-PSSession` applets de commande et `Export-PSSession` créent des modules qui contiennent des fichiers de script non signés et des fichiers de mise en forme.

Pour importer les modules créés par ces applets de commande, à l’aide de `Import-PSSession` ou de `Import-Module` , la stratégie d’exécution dans la session active ne peut pas être restreinte ou AllSigned. Pour plus d’informations sur les stratégies d’exécution de PowerShell, consultez [about_Execution_Policies](about_Execution_Policies.md).

Pour importer les modules sans modifier la stratégie d’exécution de l’ordinateur local qui est définie dans le registre, utilisez le paramètre **scope** de `Set-ExecutionPolicy` pour définir une stratégie d’exécution moins restrictive pour un processus unique.

Par exemple, la commande suivante démarre un processus avec la `RemoteSigned` stratégie d’exécution. La modification de la stratégie d’exécution affecte uniquement le processus en cours et ne modifie pas le paramètre de Registre **ExecutionPolicy** PowerShell.

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

Vous pouvez également utiliser le paramètre **ExecutionPolicy** de `PowerShell.exe` pour démarrer une seule session avec une stratégie d’exécution moins restrictive.

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

Pour plus d’informations sur les stratégies d’exécution, consultez [about_Execution_Policies](about_Execution_Policies.md). Pour plus d'informations, voir `PowerShell.exe -?`.

### <a name="how-to-set-and-change-quotas"></a>Définition et modification des quotas

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

Vous pouvez utiliser des quotas pour protéger l’ordinateur local et l’ordinateur distant contre une utilisation excessive des ressources, à la fois accidentelle et malveillante.

Les quotas suivants sont disponibles dans la configuration de base.

- Le fournisseur WSMan (WSMan :) fournit plusieurs paramètres de quota, tels que les paramètres **MaxEnvelopeSizekb** et **MaxProviderRequests** dans le `WSMan:<ComputerName>` nœud, ainsi que les paramètres **MaxConcurrentOperations** , **Propriétés MaxConcurrentOperationsPerUser** et **MaxConnections** dans le `WSMan:<ComputerName>\Service` nœud.

- Vous pouvez protéger l’ordinateur local à l’aide des paramètres **MaximumReceivedDataSizePerCommand** et **MaximumReceivedObjectSize** de l’applet de commande `New-PSSessionOption` et de la variable de `$PSSessionOption` préférence.

- Vous pouvez protéger l’ordinateur distant en ajoutant des restrictions aux configurations de session, par exemple en utilisant les paramètres **MaximumReceivedDataSizePerCommandMB** et **MaximumReceivedObjectSizeMB** de l' `Register-PSSessionConfiguration` applet de commande.

Lorsque les quotas sont en conflit avec une commande, PowerShell génère une erreur.

Pour résoudre l’erreur, modifiez la commande distante pour qu’elle soit conforme au quota. Ou bien, déterminez la source du quota, puis augmentez le quota pour permettre l’exécution de la commande.

Par exemple, la commande suivante augmente le quota de taille d’objet dans la configuration de session Microsoft. PowerShell sur l’ordinateur distant de 10 Mo (valeur par défaut) à 11 Mo.

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

Pour plus d’informations sur l’applet de commande `New-PSSessionOption` , consultez `New-PSSessionOption` .

Pour plus d’informations sur les quotas de WS-Management, consultez [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).

### <a name="how-to-resolve-timeout-errors"></a>Comment résoudre les erreurs de délai d’attente

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

Vous pouvez utiliser des délais d’attente pour protéger l’ordinateur local et l’ordinateur distant contre une utilisation excessive des ressources, à la fois accidentelle et malveillante. Lorsque des délais d’attente sont définis à la fois sur l’ordinateur local et sur l’ordinateur distant, PowerShell utilise les paramètres de délai d’expiration les plus courts.

Les délais d’attente suivants sont disponibles dans la configuration de base.

- Le fournisseur WSMan (WSMan :) fournit plusieurs paramètres de délai d’attente côté client et côté service, tels que le paramètre **MaxTimeoutms** dans le `WSMan:<ComputerName>` nœud et les paramètres **EnumerationTimeoutms** et **MaxPacketRetrievalTimeSeconds** dans le `WSMan:<ComputerName>\Service` nœud.

- Vous pouvez protéger l’ordinateur local à l’aide des paramètres **CancelTimeout** , **IdleTimeout** , **OpenTimeout** et **OperationTimeout** de l’applet de commande `New-PSSessionOption` et de la variable de `$PSSessionOption` préférence.

- Vous pouvez également protéger l’ordinateur distant en définissant les valeurs de délai d’attente par programmation dans la configuration de session de la session.

Lorsqu’une valeur de délai d’attente n’autorise pas l’exécution d’une opération, PowerShell met fin à l’opération et génère une erreur.

Pour résoudre l’erreur, modifiez la commande pour qu’elle se termine dans l’intervalle de délai d’attente ou déterminez la source de la limite du délai d’attente, puis augmentez l’intervalle de délai d’attente pour permettre l’exécution de la commande.

Par exemple, les commandes suivantes utilisent l' `New-PSSessionOption` applet de commande pour créer un objet d’option de session avec une valeur **OperationTimeout** de 4 minutes (en ms), puis utiliser l’objet d’option de session pour créer une session à distance.

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

Pour plus d’informations sur les délais d’expiration WS-Management, consultez la rubrique d’aide pour le fournisseur WSMan (type `Get-Help WSMan` ).

Pour plus d’informations sur l’applet de commande `New-PSSessionOption` , consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

## <a name="troubleshooting-unresponsive-behavior"></a>Résolution des problèmes de comportement qui ne répond pas

Cette section traite des problèmes de communication à distance qui empêchent une commande de se terminer et d’empêcher ou de retarder le retour de l’invite PowerShell.

### <a name="how-to-interrupt-a-command"></a>Interruption d’une commande

Certains programmes Windows natifs, tels que les programmes avec une interface utilisateur, les applications console qui demandent une entrée et les applications console qui utilisent l’API de console Win32, ne fonctionnent pas correctement dans l’hôte distant PowerShell.

Lorsque vous utilisez ces programmes, vous pouvez constater un comportement inattendu, tel qu’aucune sortie, sortie partielle ou commande distante qui ne se termine pas.

Pour mettre fin à un programme qui ne répond pas, tapez <kbd>CTRL</kbd> + <kbd>C</kbd>. Pour afficher les erreurs qui ont pu être signalées, tapez `$error` dans l’hôte local et la session à distance.

## <a name="how-to-recover-from-an-operation-failure"></a>Récupération suite à un échec d’opération

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

Cette erreur est retournée lorsqu’une opération est terminée avant qu’elle ne se termine.
En général, il se produit lorsque le service WinRM s’arrête ou redémarre alors que d’autres opérations WinRM sont en cours.

Pour résoudre ce problème, vérifiez que le service WinRM est en cours d’exécution et réessayez d’exécuter la commande.

1. Démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .
1. Exécutez la commande suivante :

   `Start-Service WinRM`

1. Réexécutez la commande qui a généré l’erreur.

## <a name="linux-and-macos-limitations"></a>Limitations de Linux et macOS

### <a name="authentication"></a>Authentification

Seule l’authentification de base fonctionne sur macOS et toute tentative d’utilisation d’autres schémas d’authentification peut entraîner un blocage du processus.

Veuillez consulter les instructions [d’authentification OMI](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) .

## <a name="see-also"></a>VOIR AUSSI

[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[Module d’importation](xref:Microsoft.PowerShell.Core.Import-Module)

[about_Remote](about_Remote.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_Variables](about_Remote_Variables.md)
