---
ms.date: 08/23/2017
keywords: powershell,applet de commande
title: Désinstaller Accès Web Windows PowerShell
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952951"
---
# <a name="uninstall-windows-powershell-web-access"></a>désinstaller Accès Web Windows PowerShell

Mise à jour : 24 juin 2013

S’applique à : Windows Server 2012 R2, Windows Server 2012

Les étapes décrites dans cette rubrique suppriment le site web Accès Web Windows PowerShell et l’application correspondante du serveur de passerelle où elle est installée.

## <a name="notify-users"></a>Notifier les utilisateurs

Avant de commencer, informez les utilisateurs de la console Web de la suppression du site web.

La désinstallation d’Accès Web Windows PowerShell ne désinstalle pas IIS ni d’autres fonctionnalités automatiquement installées, car Accès Web Windows PowerShell en a besoin pour s’exécuter.
Le processus de désinstallation laisse les fonctionnalités installées dont dépendait Accès Web Windows PowerShell ; vous pouvez désinstaller ces fonctionnalités séparément si besoin.

## <a name="recommended-quick-uninstallation"></a>Désinstallation (rapide) recommandée

Les procédures de cette section vous permettent de désinstaller :

- l’application Accès Web Windows PowerShell et
- la fonctionnalité Accès Web Windows PowerShell

à l’aide d’applets de commande Windows PowerShell.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Étape 1 : Supprimer l’application web à l’aide d’applets de commande

1. Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell.

    -   Sur le Bureau Windows, cliquez avec le bouton droit sur **Windows PowerShell** dans la barre des tâches.

    -   Dans l’écran d’**accueil** de Windows, cliquez sur **Windows PowerShell**.

2. Tapez `Uninstall-PswaWebApplication` puis appuyez sur **Entrée**.
   1. Si vous avez défini un nom de site web personnalisé, ajoutez le paramètre `-WebsiteName` à votre commande et spécifiez le nom du site web.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Si vous avez utilisé une application web personnalisée (et non pas l’application par défaut, **pswa**), ajoutez le paramètre `-WebApplicationName` à votre commande et spécifiez le nom de l’application web.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Si vous utilisez un certificat de test, ajoutez le paramètre `DeleteTestCertificate` à l’applet de commande, comme indiqué dans l’exemple suivant.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Étape 2 : Désinstaller Accès Web Windows PowerShell à l’aide d’applets de commande

1. Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés. Si une session est déjà ouverte, passez à l’étape suivante.

    -   Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

    -   Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

1. Tapez ce qui suit, puis appuyez sur **Entrée**, où *computer_name* représente le nom de l’ordinateur distant sur lequel vous souhaitez installer Accès Web Windows PowerShell, le cas échéant. Le paramètre `-Restart` redémarre automatiquement les serveurs de destination si la suppression l’exige.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Pour installer des rôles et fonctionnalités sur un disque dur virtuel hors connexion, vous devez ajouter les paramètres `-ComputerName` et `-VHD`. Le paramètre `-ComputerName` contient le nom du serveur sur lequel monter le disque dur virtuel tandis que le paramètre `-VHD` contient le chemin d’accès au fichier VHD sur le serveur spécifié.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Une fois l’installation terminée, vérifiez que vous avez bien supprimé Accès Web Windows PowerShell. Pour cela, ouvrez la page **Tous les serveurs** dans le Gestionnaire de serveur, sélectionnez un serveur sur lequel vous avez installé la fonctionnalité, puis examinez la vignette **Rôles et fonctionnalités** dans la page du serveur sélectionné.

    Vous pouvez également exécuter l’applet de commande `Get-WindowsFeature` ciblée sur le serveur sélectionné (Get-WindowsFeature -ComputerName &lt;*nom_ordinateur*&gt;) pour afficher la liste des rôles et des fonctionnalités installés sur le serveur.

## <a name="custom-uninstallation"></a>Désinstallation personnalisée

Les procédures de cette section vous permettent de désinstaller l’application web Accès Web Windows PowerShell et la fonctionnalité Accès Web Windows PowerShell en utilisant l’Assistant Suppression de rôles et de fonctionnalités dans le Gestionnaire de serveur et la console du Gestionnaire des services Internet.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Étape 1 : Supprimer l’application web à l’aide du Gestionnaire des services Internet


1. Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes. Si elle est déjà ouverte, passez à l’étape suivante.

    -   Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows. Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.

    -   Sur l’écran d’**accueil** de Windows, tapez une partie du nom **Gestionnaire des services Internet (IIS)**. Cliquez sur le raccourci quand il s’affiche dans les résultats **Applications**.

1. Dans le volet de l’arborescence du Gestionnaire des services Internet, sélectionnez le site web qui exécute l’application web Accès Web Windows PowerShell.

1. Dans le volet **Actions**, sous **Gérer le site web**, cliquez sur **Arrêter**.

1. Dans le volet de l’arborescence, cliquez avec le bouton droit sur l’application web dans le site web qui exécute l’application web Accès Web Windows PowerShell, puis cliquez sur **Supprimer**.

1. Dans le volet de l’arborescence, sélectionnez **Pools d’applications**, sélectionnez le dossier du pool d’applications Accès Web Windows PowerShell, cliquez sur **Arrêter** dans le volet **Actions**, puis cliquez sur **Supprimer** dans le volet de contenu.

1. Fermez le Gestionnaire des services Internet (IIS).

> ![Avertissement](images/SecurityNote.jpeg)**Remarque** :
>
> Le certificat n’est pas supprimé durant la désinstallation.
>
> Si vous avez créé un certificat auto-signé ou utilisé un certificat de test et que vous souhaitez le supprimer, supprimez le certificat dans le Gestionnaire des services Internet.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Étape 2 : Désinstaller Accès Web Windows PowerShell à l’aide de l’Assistant Suppression de rôles et de fonctionnalités

1. Si le Gestionnaire de serveur est déjà ouvert, passez à l’étape suivante. S’il n’est pas déjà ouvert, ouvrez-le en effectuant l’une des opérations suivantes.

    -   Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.

    -   Dans l’écran d’**accueil** de Windows, cliquez sur **Gestionnaire de serveur**.

1. Dans le menu **Gérer**, cliquez sur **Supprimer des rôles et fonctionnalités**.

1. Dans la page **Sélectionner le serveur de destination**, sélectionnez le serveur ou le disque dur virtuel hors connexion sur lequel vous souhaitez supprimer la fonctionnalité. Pour sélectionner un disque dur virtuel hors connexion, choisissez d’abord le serveur sur lequel monter le disque dur virtuel, puis sélectionnez le fichier VHD. Une fois que vous avez sélectionné le serveur de destination, cliquez sur **Suivant**.

1. Cliquez de nouveau sur **Suivant** pour passer à la page **Supprimer des fonctionnalités**.

1. Décochez la case **Accès Web Windows PowerShell**, puis cliquez sur **Suivant**.

1. Dans la page **Confirmer les sélections pour la suppression**, cliquez sur **Supprimer**.

## <a name="see-also"></a>Voir aussi

- [Installer et utiliser Accès Web Windows PowerShell](install-and-use-windows-powershell-web-access.md)
- [Aide du Gestionnaire des services Internet](https://technet.microsoft.com/library/cc732664.aspx)