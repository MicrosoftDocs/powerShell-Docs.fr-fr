---
ms.date: 08/23/2017
keywords: powershell,applet de commande
title: résolution des problèmes d’accès dans Accès Web Windows PowerShell
ms.openlocfilehash: 66e913504cf0c34f8d9ab18b088fb06173aca24c
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733869"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Résolution des problèmes d’accès dans Accès Web Windows PowerShell

Mise à jour : 24 juin 2013 (révisée le 23 août 2017)

S’applique à : Windows Server 2012 R2, Windows Server 2012

Les sections suivantes identifient certains problèmes courants que les utilisateurs peuvent rencontrer quand ils essaient de se connecter à un ordinateur distant à l’aide d’Accès Web Windows PowerShell. Elles incluent des suggestions pour la résolution des problèmes.

## <a name="sign-in-failure"></a>Échec de connexion

L’échec peut avoir les causes suivantes.

- Il n’existe aucune règle d’autorisation qui autorise l’utilisateur à accéder à l’ordinateur, ni configuration de session spécifique sur l’ordinateur distant.

  La sécurité d’Accès Web Windows PowerShell est restrictive ; les utilisateurs doivent recevoir un accès explicite aux ordinateurs distants à l’aide de règles d’autorisation.

  Pour plus d’informations sur la création de règles d’autorisation, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- L’utilisateur n’est pas autorisé à accéder à l’ordinateur de destination. Cet accès est déterminé par des listes de contrôle d’accès.

  Pour plus d’informations, consultez [Connexion à Accès Web Windows PowerShell](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) ou le Blog de l’équipe Windows PowerShell.

- La gestion à distance Windows PowerShell n’est peut-être pas activée sur l’ordinateur de destination.

  Vérifiez que la gestion à distance est activée sur l’ordinateur auquel l’utilisateur essaie de se connecter.

  Pour plus d’informations, consultez [Comment configurer votre ordinateur pour la communication à distance](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Erreur de serveur interne

Quand des utilisateurs essaient de se connecter à Accès Web Windows PowerShell dans une fenêtre Internet Explorer, une page **Erreur de serveur interne** leur est présentée ou *Internet Explorer* cesse de répondre.

Ce problème est propre à Internet Explorer.

### <a name="possible-cause"></a>Cause possible

Il peut survenir pour les utilisateurs qui se sont connectés avec un nom de domaine contenant des caractères chinois ou si un ou plusieurs caractères chinois font partie du nom du serveur de passerelle.

#### <a name="workaround"></a>Solution de contournement

1. [Installer et exécuter Internet Explorer 10](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Remplacez le paramètre Internet Explorer **Mode de document** par *Normes Internet Explorer 10*.
   1. Appuyez sur **F12** pour ouvrir la console Outils de développement.
   1. Dans Internet Explorer 10, cliquez sur **Mode navigateur**, puis sélectionnez *Internet Explorer 10*.
   1. Cliquez sur **Mode de document**, puis sur *Normes Internet Explorer 10*.
   1. Appuyez de nouveau sur **F12** pour fermer la console Outils de développement.
1. Désactivez la configuration automatique du proxy dans Internet Explorer 10.
   1. Cliquez sur **Outils**, puis sur **Options Internet**.
   1. Dans la boîte de dialogue **Options Internet**, sous l’onglet **Connexions**, cliquez sur **Paramètres réseau**.
   1. Décochez la case **Détecter automatiquement les paramètres de connexion**. Cliquez sur **OK**, puis de nouveau sur **OK** pour fermer la boîte de dialogue *Options Internet*.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Impossible de se connecter à un ordinateur de groupe de travail distant

Si l’ordinateur de destination est membre d’un groupe de travail, utilisez la syntaxe suivante pour fournir votre nom d’utilisateur et vous connecter à l’ordinateur : `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Impossible de trouver les outils de gestion de serveur web (IIS) bien que le rôle ait été installé

Si vous avez installé Accès Web Windows PowerShell en utilisant l’applet de commande `Install-WindowsFeature`, les outils de gestion ne sont pas installés, sauf si le paramètre `-IncludeManagementTools` est ajouté à l’applet de commande.

Pour obtenir un exemple, consultez [Pour installer Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Vous pouvez ajouter la console du Gestionnaire des services Internet et d’autres outils de gestion IIS dont vous avez besoin en sélectionnant les outils dans une session de l’**Assistant Ajout de rôles et de fonctionnalités** qui cible le serveur de passerelle.
Vous pouvez ouvrir l’Assistant Ajout de rôles et de fonctionnalités à partir du Gestionnaire de serveur.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Le site web Accès Web Windows PowerShell n’est pas accessible.

Si la Configuration de sécurité renforcée est activée dans Internet Explorer (IE ESC), vous pouvez ajouter le site web Accès Web Windows PowerShell à la liste des sites de confiance.

Une approche moins recommandée en raison des risques de sécurité est de désactiver IE ESC.
Vous pouvez désactiver IE ESC dans la vignette Propriétés de la page Serveur local dans le Gestionnaire de serveur.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Un échec d’autorisation s’est produit. Vérifiez que vous êtes autorisé à vous connecter à l’ordinateur de destination.

Le message d’erreur suivant s’affiche lors d’une tentative de connexion quand le serveur de passerelle est l’ordinateur de destination et qu’il se trouve également dans un groupe de travail.

Quand le serveur de passerelle est également le serveur de destination et qu’il se trouve dans un groupe de travail, spécifiez le nom d’utilisateur, le nom d’ordinateur et le nom du groupe d’utilisateurs.
N’utilisez pas de point (.) tout seul pour représenter le nom de l’ordinateur.

### <a name="scenarios-and-proper-values"></a>Scénarios et valeurs appropriées

#### <a name="all-cases"></a>Tous les cas

Paramètre | Valeur
-- | --
UserName | Nom\_serveur\\nom\_utilisateur<br/>Localhost\\nom\_utilisateur<br/>.\\nom\_utilisateur
UserGroup | Nom\_serveur\\groupe\_utilisateurs<br/>Localhost\\groupe\_s<br/>.\\groupe\_utilisateurs
ComputerGroup | Nom\_serveur\\groupe\_ordinateurs<br/>Localhost\\groupe\_ordinateurs<br/>.\\groupe\_ordinateurs

#### <a name="gateway-server-is-in-a-domain"></a>Serveur de passerelle dans un domaine

Paramètre | Valeur
-- | --
ComputerName | Nom complet du serveur de passerelle ou Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Serveur de passerelle dans un groupe de travail

Paramètre | Valeur
-- | --
ComputerName | Nom du serveur

### <a name="gateway-credentials"></a>Informations d’identification de la passerelle

Connectez-vous à un serveur de passerelle en tant qu’ordinateur cible à l’aide d’informations d’identification formatées de l’une des manières suivantes.

- Nom\_serveur\\nom\_utilisateur
- Localhost\\nom\_utilisateur
- .\\nom\_utilisateur

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Un identificateur de sécurité (SID) est affiché dans une règle d’autorisation

Un identificateur de sécurité (SID) est affiché dans une règle d’autorisation au lieu de la syntaxe nom\_utilisateur/nom\_ordinateur.

Soit la règle n’est plus valide, soit la requête des services de domaine Active Directory a échoué.
Une règle d’autorisation n’est généralement pas valide dans les scénarios où le serveur de passerelle était à un moment donné dans un groupe de travail, puis a par la suite joint un domaine.

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Impossible de se connecter avec la règle en tant qu’adresse IPv6 avec un domaine

Impossible de se connecter à un ordinateur cible spécifié dans des règles d’autorisation sous forme d’adresse IPv6 avec un domaine.

Les règles d’autorisation ne prennent pas en charge une adresse IPv6 sous forme de nom de domaine.

Pour spécifier un ordinateur de destination à l’aide d’une adresse IPv6, utilisez l’adresse IPv6 d’origine (qui contient des deux-points) dans la règle d’autorisation.
Les adresses IPv6 de domaine et numériques (avec des signes deux-points) sont prises en charge en tant que nom d’ordinateur cible dans la page de connexion à Accès Web Windows PowerShell, mais pas dans les règles d’autorisation.

Pour plus d’informations sur les adresses IPv6, consultez [Fonctionnement d’IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Voir aussi

- [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Utiliser la console web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
