---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679245"
---
# <a name="powershell-remoting-security-considerations"></a>Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell

La communication à distance PowerShell est la méthode recommandée pour gérer les systèmes Windows. La communication à distance PowerShell est activée par défaut dans Windows Server 2012 R2. Ce document couvre les questions de sécurité, les recommandations et les bonnes pratiques lors de l’utilisation de la communication à distance PowerShell.

## <a name="what-is-powershell-remoting"></a>Présentation de la communication à distance PowerShell

La communication à distance Powershell utilise la [Gestion à distance de Windows (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), l’implémentation par Microsoft du protocole [Gestion des services Web (WS-Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf), pour permettre aux utilisateurs d’exécuter des commandes PowerShell sur des ordinateurs distants. Pour plus d’informations sur l’utilisation de la communication à distance PowerShell, voir [Exécution de commandes à distance](https://technet.microsoft.com/library/dd819505.aspx).

La communication à distance PowerShell n’est pas identique à l’utilisation du paramètre **ComputerName** d’une applet de commande pour l’exécuter sur un ordinateur distant, qui utilise l’appel de procédure distante (RPC) en tant que protocole sous-jacent.

## <a name="powershell-remoting-default-settings"></a>Paramètres par défaut de la communication à distance PowerShell

La communication à distance PowerShell et WinRM écoutent sur les ports suivants :

- HTTP : 5985
- HTTPS : 5986

Par défaut, la communication à distance PowerShell autorise uniquement les connexions des membres du groupe de l’administrateur. Les sessions étant lancées dans le contexte de l’utilisateur, tous les contrôles d’accès au système d’exploitation appliqués à des utilisateurs et des groupes continuent de leur être appliqués pendant la connexion via la communication à distance PowerShell.

Sur les réseaux privés, la règle de Pare-feu Windows par défaut pour la communication à distance PowerShell accepte toutes les connexions. Sur les réseaux publics, la règle de Pare-feu Windows par défaut autorise les connexions de communication à distance PowerShell uniquement sur le même sous-réseau. Vous devez modifier explicitement cette règle pour ouvrir la communication à distance PowerShell à toutes les connexions sur un réseau public.

>**Avertissement :** La règle de pare-feu pour les réseaux publics est destinée à protéger l’ordinateur contre les tentatives de connexions externes potentiellement malveillantes. Soyez prudent lors de la suppression de cette règle.

## <a name="process-isolation"></a>Isolation des processus

La communication à distance PowerShell utilise [WinRM](https://msdn.microsoft.com/library/windows/desktop/aa384426) pour la communication entre les ordinateurs.
WinRM s’exécute comme service sous le compte de service réseau et génère des processus isolés exécutés comme comptes d’utilisateur pour héberger les instances de PowerShell. Une instance de PowerShell exécutée comme un utilisateur n’a pas accès à un processus utilisant une instance de PowerShell exécutée comme autre utilisateur.

## <a name="event-logs-generated-by-powershell-remoting"></a>Journaux des événements générés par la communication à distance PowerShell

FireEye a fourni un bon résumé des journaux des événements et autres preuves de sécurité générés par les sessions de communication à distance PowerShell, disponible sur [Investigating PowerShell Attacks](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Protocoles de transport et chiffrement

Il est utile de prendre en compte la connexion de communication à distance PowerShell sous deux angles : l’authentification initiale et les communications en cours.

Quel que soit le protocole de transport utilisé (HTTP ou HTTPS), la communication à distance PowerShell chiffre toujours toutes les communications après l’authentification initiale avec une clé symétrique AES-256 par session.

### <a name="initial-authentication"></a>Authentification initiale

L’authentification confirme l’identité du client auprès du serveur et, idéalement, du serveur auprès du client.

Quand un client se connecte à un serveur de domaine à l’aide de son nom d’ordinateur (par exemple, serveur01 ou serveur01.contoso.com), le protocole d’authentification par défaut est [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garantit l’identité de l’utilisateur et l’identité du serveur sans envoyer aucune sorte d’informations d’identification réutilisables.

Quand un client se connecte à un serveur de domaine avec son adresse IP ou qu’il se connecte à un serveur de groupe de travail, l’authentification Kerberos n’est pas possible. Dans ce cas, la communication à distance PowerShell s’appuie sur le [protocole d’authentification NTLM](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). Le protocole d’authentification NTLM garantit l’identité de l’utilisateur sans envoyer aucune sorte d’informations d’identification délégables. Pour prouver l’identité de l’utilisateur, le protocole NTLM nécessite que le client et le serveur calculent une clé de session à partir du mot de passe de l’utilisateur sans jamais s’échanger le mot de passe proprement dit. Le serveur ne connaissant en général pas le mot de passe de l’utilisateur, il communique avec le contrôleur de domaine qui connaît ce mot de passe et calcule la clé de session pour le serveur.

Le protocole NTLM ne garantit cependant pas l’identité du serveur. Comme avec tous les protocoles qui utilisent NTLM pour l’authentification, un pirate ayant accès au compte d’un ordinateur appartenant à un domaine peut appeler le contrôleur de domaine pour calculer une clé de session NTLM et donc emprunter l’identité du serveur.

L’authentification NTLM est désactivée par défaut, mais peut être autorisée en configurant SSL sur le serveur cible ou en configurant le paramètre WinRM TrustedHosts sur le client.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Utilisation de certificats SSL pour valider l’identité du serveur pendant les connexions NTLM

Étant donné que le protocole d’authentification NTLM ne peut pas garantir l’identité du serveur cible (seulement qu’il connaît déjà votre mot de passe), vous pouvez configurer des serveurs cibles pour utiliser SSL pour la communication à distance PowerShell. L’attribution d’un certificat SSL au serveur cible (s’il est émis par une autorité de certification également approuvée par le client) active l’authentification NTLM qui garantit l’identité de l’utilisateur et l’identité du serveur.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Erreurs d’identité de serveur NTLM ignorées

S’il n’est pas possible de déployer un certificat SSL sur un serveur pour les connexions NTLM, vous pouvez supprimer les erreurs d’identité obtenues en ajoutant le serveur à la liste **TrustedHosts** de WinRM. Notez que l’ajout d’un nom de serveur à la liste TrustedHosts ne doit pas être considéré comme une forme de déclaration de fiabilité des hôtes eux-mêmes, puisque le protocole d’authentification NTLM ne peut pas garantir que vous vous connectez en fait à l’hôte souhaité.
Vous devez plutôt considérer le paramètre TrustedHosts comme représentant la liste des hôtes pour lesquels vous voulez supprimer l’erreur générée par l’impossibilité de vérifier l’identité du serveur.


### <a name="ongoing-communication"></a>Communications en cours

Une fois l’authentification initiale terminée, le [protocole de communication à distance PowerShell](https://msdn.microsoft.com/library/dd357801.aspx) chiffre toutes les communications en cours avec une clé symétrique AES-256 par session.


## <a name="making-the-second-hop"></a>Second saut

Par défaut, la communication à distance PowerShell utilise Kerberos (s’il est disponible) ou NTLM pour l’authentification. Ces deux protocoles permettent de s’authentifier auprès de l’ordinateur distant sans lui envoyer d’informations d’identification.
Il s’agit de la méthode la plus sûre pour s’authentifier mais, comme l’ordinateur distant ne dispose pas des informations d’identification de l’utilisateur, il ne peut pas accéder aux autres ordinateurs ni services au nom de l’utilisateur.
Ce problème est connu sous le nom de « deuxième saut ».

Il existe plusieurs moyens de l’éviter. Pour connaître la description de ces méthodes, ainsi que les avantages et les inconvénients de chacune, consultez [Effectuer le deuxième saut dans la communication à distance PowerShell](PS-remoting-second-hop.md).