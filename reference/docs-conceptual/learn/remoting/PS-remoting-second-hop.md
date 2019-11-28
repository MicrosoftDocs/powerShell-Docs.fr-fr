---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Effectuer le deuxième saut dans la communication à distance PowerShell
ms.openlocfilehash: 567d75009f7d53e9e95e5480b275ec3991cfb9f5
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417632"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Effectuer le deuxième saut dans la communication à distance PowerShell

Le « problème du deuxième saut » fait référence à une situation de ce type :

1. Vous êtes connecté à _ServerA_.
2. À partir de _ServerA_, vous démarrez une session PowerShell à distance pour vous connecter à _ServerB_.
3. Une commande exécutée sur _ServerB_ via votre session de communication à distance PowerShell tente d’accéder à une ressource sur _ServerC_.
4. L’accès à la ressource sur _ServerC_ est refusé, car les informations d’identification utilisées pour créer la session de communication à distance PowerShell ne sont pas transmises de _ServerB_ à _ServerC_.

Il existe plusieurs moyens de résoudre ce problème. Dans cette rubrique, nous allons étudier quelques-unes des solutions les plus courantes pour le problème du deuxième saut.

## <a name="credssp"></a>CredSSP

Vous pouvez utiliser le [protocole CredSSP (Credential Security Support Provider)](/windows/win32/secauthn/credential-security-support-provider) pour l’authentification. Le protocole CredSSP mettant en cache les informations d’identification sur le serveur distant (_ServerB_), son utilisation vous expose à des risques de vol de ces informations. Si l’ordinateur distant est compromis, la personne malveillante a accès aux informations d’identification de l’utilisateur. CredSSP est désactivé par défaut sur les ordinateurs clients et serveurs. Vous devez activer CredSSP uniquement dans les environnements les plus approuvés, Par exemple un administrateur de domaine qui se connecte à un contrôleur de domaine, car le contrôleur de domaine est hautement approuvé.

Pour plus d’informations sur les questions de sécurité lors de l’utilisation de CredSSP pour la communication à distance PowerShell, voir [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Pour plus d’informations sur les risques de vol des informations d’identification, voir [Atténuation des attaques PtH (Pass-The-Hash) et autres risques de vol des informations d’identification](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Pour accéder à un exemple montrant comment activer et utiliser CredSSP pour la communication à distance PowerShell, consultez [Utiliser CredSSP pour résoudre le problème du deuxième saut](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Avantages

- Fonctionne pour tous les serveurs avec Windows Server 2008 ou une version ultérieure.

### <a name="cons"></a>Inconvénients

- Présente des failles de sécurité.
- Requiert la configuration des rôles client et serveur.

## <a name="kerberos-delegation-unconstrained"></a>Délégation Kerberos (sans contraintes)

Vous pouvez également utiliser la délégation sans contraintes Kerberos pour effectuer le deuxième saut. Toutefois, cette méthode ne fournit aucun contrôle sur l’utilisation des informations d’identification déléguées.

>**Remarque :** Les comptes Active Directory qui ont l’ensemble de propriétés **Ce compte est sensible et ne peut pas être délégué** ne peuvent pas être délégués. Pour plus d’informations, consultez [Priorité à la sécurité : analyser « Ce compte est sensible et ne peut pas être délégué » pour les comptes privilégiés](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) et [Paramètres et outils d’authentification Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Avantages

- Ne requiert pas de programmation particulière.

### <a name="cons"></a>Inconvénients

- Ne prend pas en charge le deuxième saut pour WinRM.
- Ne fournit aucun contrôle sur l’utilisation des informations d’identification, ce qui crée une faille de sécurité.

## <a name="kerberos-constrained-delegation"></a>Délégation Kerberos contrainte

Vous pouvez utiliser la délégation contrainte héritée (non basée sur les ressources) pour effectuer le deuxième saut. Configurez la délégation contrainte Kerberos avec l’option « Utiliser tout protocole d’authentification » pour permettre la transition du protocole.

> [!NOTE]
> Les comptes Active Directory qui ont l’ensemble de propriétés **Ce compte est sensible et ne peut pas être délégué** ne peuvent pas être délégués. Pour plus d’informations, consultez [Priorité à la sécurité : analyser « Ce compte est sensible et ne peut pas être délégué » pour les comptes privilégiés](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) et [Paramètres et outils d’authentification Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Avantages

- Ne requiert pas de programmation particulière.

### <a name="cons"></a>Inconvénients

- Ne prend pas en charge le deuxième saut pour WinRM.
- Doit être configuré sur l’objet Active Directory du serveur distant (_ServerB_).
- Limité à un serveur. Ne peut pas traverser des domaines ou des forêts.
- Requiert des droits pour mettre à jour les objets et le nom des principaux du service (SPN).

## <a name="resource-based-kerberos-constrained-delegation"></a>Délégation Kerberos contrainte basée sur les ressources

La délégation Kerberos contrainte basée sur les ressources (introduite dans Windows Server 2012) permet de configurer la délégation des informations d’identification sur l’objet serveur où résident les ressources.
Dans le scénario du deuxième saut décrit ci-dessus, vous configurez _ServerC_ pour spécifier l’emplacement où il acceptera les informations d’identification déléguées.

>**Remarque :** Les comptes Active Directory qui ont l’ensemble de propriétés **Ce compte est sensible et ne peut pas être délégué** ne peuvent pas être délégués. Pour plus d’informations, consultez [Priorité à la sécurité : analyser « Ce compte est sensible et ne peut pas être délégué » pour les comptes privilégiés](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) et [Paramètres et outils d’authentification Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Avantages

- Informations d’identification non stockées.
- Relativement facile à configurer à l’aide des applets de commande PowerShell, sans programmation particulière.
- Aucun domaine spécial n’est requis.
- Fonctionne à travers des domaines et des forêts.
- Code PowerShell.

### <a name="cons"></a>Inconvénients

- Requiert Windows Server 2012 ou une version ultérieure.
- Ne prend pas en charge le deuxième saut pour WinRM.
- Requiert des droits pour mettre à jour les objets et le nom des principaux du service (SPN).

### <a name="example"></a>Exemple

Examinons un exemple PowerShell qui configure la délégation contrainte basée sur les ressources sur _ServerC_ de façon à autoriser les informations d’identification déléguées à partir d’un _ServerB_.
Cet exemple suppose que tous les serveurs exécutent Windows Server 2012 ou une version ultérieure, et qu’il existe au moins un contrôleur de domaine Windows Server 2012 sur chacun des domaines auquel appartient chaque serveur.

Pour pouvoir configurer la délégation contrainte, vous devez ajouter la fonctionnalité `RSAT-AD-PowerShell` afin d’installer le module Active Directory PowerShell, puis importer ce module dans votre session :

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Plusieurs applets de commande disponibles ont désormais un paramètre **PrincipalsAllowedToDelegateToAccount** :

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

Le paramètre **PrincipalsAllowedToDelegateToAccount** définit l’attribut d’objet Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity** contenant une liste de contrôle d’accès (ACL) qui spécifie quels comptes ont l’autorisation de déléguer les informations d’identification au compte associé (dans notre exemple, il s’agira du compte d’ordinateur de _Server_).

Nous allons maintenant définir les variables que nous utiliserons pour représenter les serveurs :

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (et par conséquent la communication à distance PowerShell) s’exécute en tant que compte d’ordinateur par défaut. Vous pouvez le constater en examinant la propriété **StartName** du service `winrm` :

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Pour que _ServerC_ autorise la délégation à partir d’une session de communication à distance PowerShell sur _ServerB_, nous allons accorder l’accès en donnant comme valeur au paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_ l’objet d’ordinateur de _ServerB_ :

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Le [Centre de distribution de clés (KDC)](/windows/win32/secauthn/key-distribution-center) Kerberos met en cache les tentatives d’accès refusées (cache négatif) pendant 15 minutes. Si _ServerB_ a précédemment essayé d’accéder à _ServerC_, vous devez effacer le cache sur _ServerB_ en appelant la commande suivante :

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Vous pouvez également redémarrer l’ordinateur, ou attendre au moins 15 minutes pour effacer le cache.

Après avoir vidé le cache, vous pouvez exécuter le code de _ServerA_ à _ServerC_ via _ServerB_ :

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

Dans cet exemple, la variable `$using` est utilisée pour rendre la variable `$ServerC` visible pour _ServerB_. Pour plus d’informations sur la variable `$using`, consultez [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Pour permettre à plusieurs serveurs de déléguer les informations d’identification à _ServerC_, donnez comme valeur un tableau au paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_ :

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Si vous souhaitez effectuer le deuxième saut entre domaines, ajoutez le nom de domaine complet (FQDN) du contrôleur du domaine auquel _ServerB_ appartient :

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Pour supprimer la possibilité de déléguer les informations d’identification à ServerC, donnez comme valeur `$null` au paramètre **PrincipalsAllowedToDelegateToAccount** sur _ServerC_ :

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informations sur la délégation Kerberos contrainte basée sur les ressources

- [Nouveautés de l’authentification Kerberos](https://technet.microsoft.com/library/hh831747.aspx)
- [Comment Windows Server 2012 facilite la délégation Kerberos contrainte, partie 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Comment Windows Server 2012 facilite la délégation Kerberos contrainte, partie 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Comprendre la délégation Kerberos contrainte pour les déploiements de proxy d’applications Azure Active Directory avec l’authentification Windows intégrée](https://aka.ms/kcdpaper)
- [[MS-ADA2]: attributs de schéma Active Directory M2.210 msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)
- [[MS-SFU] : extensions du protocole Kerberos : protocole de service pour l’utilisateur et de délégation contrainte 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)
- [Délégation Kerberos contrainte basée sur les ressources](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Administration à distance sans la délégation contrainte à l’aide de PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration avec la commande RunAs

Vous pouvez créer une configuration de session sur _ServerB_ et définir son paramètre **RunAsCredential**.

Pour plus d’informations sur l’utilisation de PSSessionConfiguration et de RunAs afin de résoudre le problème du deuxième saut, consultez [Autre solution de communication à distance PowerShell sur plusieurs sauts](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Avantages

- Fonctionne avec n’importe quel serveur avec WMF 3.0 ou une version ultérieure.

### <a name="cons"></a>Inconvénients

- Nécessite la configuration de **PSSessionConfiguration** et de **RunAs** sur chaque serveur intermédiaire (_ServerB_).
- Nécessite la maintenance des mots de passe lorsqu’un compte de domaine **RunAs** est utilisé

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA vous permet de restreindre les commandes qu’un administrateur peut exécuter au cours d’une session PowerShell. Il peut être utilisé pour résoudre le problème du deuxième saut.

Pour plus d’informations sur JEA, consultez [Juste assez d’administration](/powershell/scripting/learn/remoting/jea/overview).

### <a name="pros"></a>Avantages

- Aucune maintenance des mots de passe lorsque vous utilisez un compte virtuel.

### <a name="cons"></a>Inconvénients

- Nécessite WMF 5.0 ou une version ultérieure.
- Requiert la configuration de chaque serveur intermédiaire (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Transmettre des informations d’identification à l’intérieur d’un bloc de script Invoke-Command

Vous pouvez transmettre des informations d’identification à l’intérieur du paramètre **ScriptBlock** d’un appel à l’applet de commande [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).

### <a name="pros"></a>Avantages

- Ne nécessite pas de configuration particulière du serveur.
- Fonctionne sur n’importe quel serveur exécutant WMF 2.0 ou une version ultérieure.

### <a name="cons"></a>Inconvénients

- Nécessite une technique de programmation délicate.
- Si vous exécutez WMF 2.0, requiert une syntaxe différente pour transmettre des arguments à une session à distance.

### <a name="example"></a>Exemple

L’exemple suivant montre comment transmettre des informations d’identification dans un bloc de script **Invoke-Command** :

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>Voir aussi

[Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell](WinRMSecurity.md)
