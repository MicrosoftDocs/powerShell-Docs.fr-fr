---
ms.date: 08/23/2017
keywords: powershell,applet de commande
title: utiliser la console web Windows PowerShell
ms.openlocfilehash: 9a5d6d825dc82710466768bc612b012dd80937da
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978659"
---
# <a name="use-the-web-based-windows-powershell-console"></a>Utiliser la console web Windows PowerShell

Mise à jour : 24 juin 2013

S’applique à : Windows Server 2012 R2, Windows Server 2012

Accès Web Windows PowerShell permet aux utilisateurs de se connecter à un site web sécurisé, pour pouvoir utiliser des sessions, des applets de commande et des scripts Windows PowerShell pour gérer un ordinateur distant.

Comme la console Windows PowerShell s’exécute dans un navigateur web, elle peut être ouverte depuis un grand nombre d’appareils clients différents : elle fonctionne donc sur presque tous les appareils avec un navigateur web.

La console web Windows PowerShell a pour cible un ordinateur distant spécifié par les utilisateurs dans le cadre du processus de connexion.

Cette rubrique décrit comment se connecter et commencer à utiliser la console web Accès Web Windows PowerShell.

Elle ne décrit pas comment utiliser Windows PowerShell ou exécuter des applets de commande ou des scripts. Pour plus d’informations sur la façon d’utiliser Windows PowerShell et pour accéder à des ressources de script, consultez la section [Voir aussi](#see-also) à la fin de cette rubrique.

## <a name="supported-browsers-and-client-devices"></a>Navigateurs et périphériques clients pris en charge

Accès Web Windows PowerShell prend en charge les navigateurs suivants. Bien que les navigateurs mobiles ne soient pas officiellement pris en charge, nombre d’entre eux sont susceptibles de pouvoir exécuter la console web Windows PowerShell. D’autres navigateurs acceptant les cookies, exécutant JavaScript et exécutant des sites web HTTPS sont censés fonctionner, mais n’ont pas été testés officiellement.

### <a name="supported-desktop-computer-browsers"></a>Navigateurs d’ordinateur de bureau pris en charge

- Windows Internet Explorer for Microsoft Windows 8.0, 9.0, 10.0 et 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m pour Windows
- Apple Safari 5.1.2 pour Windows
- Apple Safari 5.1.2 pour Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Navigateurs ou appareils mobiles testés de façon minimale

- Windows Phone 7 et 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari pour système d’exploitation iPhone 5.0.1
- Apple Safari pour le système d’exploitation 5.0.1 de l’iPad 2

### <a name="browser-requirements"></a>Configuration requise des navigateurs

Pour utiliser la console web Accès Web Windows PowerShell, les navigateurs doivent :

- autoriser les cookies à partir du site web de la passerelle Accès Web Windows PowerShell ;
- être en mesure d’ouvrir et de lire des pages HTTPS ;
- ouvrir et exécuter des sites web qui utilisent JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>Connexion à l’accès Web Windows PowerShell

Votre administrateur Accès Web Windows PowerShell doit vous fournir une URL qui est l’adresse du site web de la passerelle Accès Web Windows PowerShell de votre organisation. Par défaut, l’adresse de ce site web est `https://<server_name>/pswa`.

Avant de vous connecter à Accès Web Windows PowerShell, vérifiez que vous disposez du nom ou de l’adresse IP de l’ordinateur distant que vous souhaitez gérer. Vous devez être un utilisateur autorisé sur l’ordinateur distant et celui-ci doit être configuré pour autoriser la gestion à distance. Pour plus d’informations sur la configuration de votre ordinateur pour autoriser la gestion à distance, consultez [Activer et utiliser des commandes distantes dans Windows PowerShell](/powershell/module/microsoft.powershell.core/enable-psremoting).

Le moyen le plus simple de configurer un ordinateur de façon à autoriser la gestion à distance consiste à exécuter la cmdlet `Enable-PSRemoting -force` sur l’ordinateur, dans une session Windows PowerShell ouverte avec des droits d’utilisateur élevés (**Exécuter en tant qu’administrateur**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Pour se connecter à Windows PowerShell Web Access

1. Ouvrez le site web Accès Web Windows PowerShell dans une fenêtre ou un onglet de navigateur Internet.

1. Dans la page de connexion à Accès Web Windows PowerShell, indiquez votre nom d’utilisateur réseau, votre mot de passe et le nom de l’ordinateur que vous souhaitez gérer (et sur lequel vous êtes un utilisateur autorisé). Si l’administrateur Accès Web Windows PowerShell vous a demandé d’utiliser un URI de site personnalisé ou de serveur proxy plutôt qu’un nom d’ordinateur, sélectionnez **URI de connexion** dans le champ **Type de connexion**, puis spécifiez l’URI.

   > [!NOTE]
   > - Si l’ordinateur de destination est dans un groupe de travail, utilisez la syntaxe suivante pour fournir votre nom d’utilisateur et vous connecter à l’ordinateur : `<workgroup_name>\<user_name>`
   > - Si l’ordinateur de destination est le serveur de passerelle, vous pouvez spécifier `localhost` dans le champ Nom de l’ordinateur.
   > - Si l’ordinateur de destination est le serveur de passerelle et qu’il est dans un groupe de travail, vous devez utiliser `<workgroup name>\<user_name>` dans le champ Nom d’utilisateur. Vous pouvez utiliser `localhost` dans le champ Nom de l’ordinateur.

1. La section **Paramètres de connexion facultatifs** porte sur les exigences d’autorisation de l’ordinateur distant que vous souhaitez gérer. Pour plus d’informations sur les paramètres équivalents aux paramètres de connexion facultatifs, consultez l’aide de l’applet de commande [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

   En général, les informations d’identification que vous passez par le biais de la passerelle Accès Web Windows PowerShell sont identiques à celles reconnues par l’ordinateur distant que vous souhaitez gérer. Toutefois, si vous souhaitez utiliser des informations d’identification différentes pour gérer l’ordinateur spécifié à l’étape 2, développez la section **Paramètres de connexion facultatifs** et spécifiez les autres informations d’identification. Sinon, passez à l’étape 6.

1. Si l’administrateur Accès Web Windows PowerShell a créé une configuration de session personnalisée pour les utilisateurs d’Accès Web Windows PowerShell, tapez le nom de cette configuration se session dans le champ **Nom de la configuration**. Pour plus d’informations sur les configurations de session, consultez [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Conservez le **Type d’authentification** **Par défaut**, sauf indication contraire de l’administrateur Accès Web Windows PowerShell.

1. Cliquez sur **Se connecter**.

## <a name="signing-out-and-timing-out"></a>Déconnexion et dépassement de délais

Vous serez déconnecté de votre session web Windows PowerShell dans les cas suivants.

- Clic sur le bouton **Se déconnecter** dans le coin inférieur droit de la console (Windows Server 2012 uniquement).
- Clic sur le bouton **Enregistrer** ou **Quitter** dans le coin inférieur droit de la console (Windows Server 2012 R2 uniquement). Cliquez sur **Enregistrer** pour enregistrer et fermer votre session Accès Web Windows PowerShell ; vous pouvez vous reconnecter à la session ultérieurement. Quand vous vous reconnectez à Accès Web Windows PowerShell, une liste de vos sessions enregistrées s’affiche ; vous pouvez sélectionner et vous reconnecter à une session enregistrée ou démarrer une nouvelle session. Le nombre maximal de sessions ouvertes autorisées à la fois enregistrées et actives par utilisateur, est configuré par l’administrateur de la passerelle.

  Cliquez sur **Quitter** pour quitter la session Accès Web Windows PowerShell sans l’enregistrer.

- Tentative de connexion pour gérer un autre ordinateur distant dans la même session de navigateur ou sous un nouvel onglet de la même session de navigateur. (Cela ne s’applique pas si le serveur de passerelle exécute Windows Server 2012 R2 ; l’exécution d’Accès Web Windows PowerShell sur Windows Server 2012 R2 autorise plusieurs sessions utilisateur sous de nouveaux onglets dans la même session de navigateur.) Pour plus d’informations sur la façon d’utiliser plusieurs sessions actives sur le même ordinateur, consultez « Connexion simultanée à plusieurs ordinateurs cibles » dans la section [Limitations de la console web](#limitations-of-the-web-based-console) de cette rubrique.

- 20 minutes d’inactivité au cours de la session. L’administrateur de la passerelle peut personnaliser le délai d’inactivité. Pour plus d’informations, consultez [Gestion des sessions](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

  - Si vous êtes déconnecté d’une session de la console web en raison d’une erreur réseau ou d’autres défaillances ou arrêts non planifiés, et non parce que vous avez vous-même fermé la session, la session Accès Web Windows PowerShell continue de s’exécuter, connectée à l’ordinateur cible, jusqu’à ce que le délai d’expiration côté client soit écoulé. Par défaut, ce délai est de 20 minutes et est configuré par l’administrateur de la passerelle. La session est déconnectée après les 20 minutes définies par défaut, ou au terme du délai spécifié par l’administrateur de la passerelle, le délai le plus court étant appliqué.

    Si le serveur de passerelle exécute Windows Server 2012 R2, Accès Web Windows PowerShell permet aux utilisateurs de se reconnecter ultérieurement aux sessions enregistrées. Toutefois, vous ne pouvez pas accéder à ces sessions ou vous y reconnecter tant que le délai d’expiration spécifié par l’administrateur de la passerelle n’est pas écoulé.

- Fermeture de la fenêtre ou de l’onglet de navigateur.

- Mise hors tension ou déconnexion du périphérique client sur lequel le navigateur s’exécute.

- Exécution de la commande **Exit** dans la console web. Cette commande ne fonctionne pas si la configuration de session à laquelle vous êtes connecté est configurée pour prendre en charge le mode [NoLanguage](/dotnet/api/system.management.automation.pslanguagemode) ou si elle est dans une instance d’exécution restreinte.

Si vous voulez vous reconnecter, rouvrez la page web Accès Web Windows PowerShell et connectez-vous en effectuant les étapes de la section [Connexion à Accès Web Windows PowerShell](#signing-in-to-windows-powershell-web-access) de cette rubrique.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Différences dans la console Windows PowerShell Web

Une fois que vous vous êtes connecté à Accès Web Windows PowerShell, une console web Windows PowerShell s’ouvre dans la fenêtre ou l’onglet de votre navigateur. La console étant connectée à l’ordinateur distant que vous avez spécifié lors du processus de connexion, seuls les applets de commande ou scripts Windows PowerShell disponibles sur cet ordinateur distant peuvent être utilisés dans la console. Cette section décrit d’autres limitations des consoles Accès Web Windows PowerShell et les différences entre les consoles Accès Web Windows PowerShell et la console **PowerShell.exe** installée.

### <a name="functional-disparity-with-powershellexe"></a>Différences fonctionnelles avec PowerShell.exe

La plupart des fonctionnalités hôtes de Windows PowerShell sont disponibles dans la console web Accès Web Windows PowerShell, mais certaines fonctionnalités ne sont pas accessibles.

- Affichage imbriqué de la progression.

  Accès Web Windows PowerShell affiche une interface utilisateur graphique de progression pour les applets de commande qui indiquent la progression, mais seules les informations de progression de niveau supérieur sont affichées.

- Modification de la couleur d’entrée.

  La couleur d’entrée (premier plan et arrière-plan) ne peut pas être modifiée. Le style des messages de sortie, d’avertissement, de commentaires et d’erreur peut être modifié en exécutant un script.

- PSHostRawUserInterface.

  Accès Web Windows PowerShell est implémenté sur la gestion à distance Windows PowerShell et utilise une instance d’exécution distante. Accès Web Windows PowerShell n’implémente pas certaines méthodes dans cette interface (par exemple les commandes qui écrivent dans la console Windows). Les commandes telles que **PowerTab** ne fonctionnent pas dans Accès Web Windows PowerShell.

- Touches de fonction.

  Accès Web Windows PowerShell ne prend pas en charge certaines touches de fonction, souvent car ces commandes sont réservées par le navigateur.

### <a name="unsupported-shortcut-keys"></a>Touches de raccourci non prises en charge

 Touches de fonction   |                                                                                         Action
--------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Ctrl+C          | Dans Accès Web Windows PowerShell, **Ctrl+C** est utilisé par le navigateur pour copier du contenu. La console propose un bouton **Annuler**, et les utilisateurs peuvent également utiliser **Ctrl+Q** pour annuler des commandes.
Alt-Espace, e, l | Parcourir la mémoire tampon d’écran
Alt+Espace, e, f | Rechercher du texte dans la mémoire tampon d’écran
Alt+Espace, e, k | Sélectionner du texte à copier à partir de la mémoire tampon d’écran
Alt+Espace, e, p | Coller le contenu du Presse-papiers dans la console Windows PowerShell
Alt+Espace, c    | Fermer la console Windows PowerShell
Ctrl+Pause      | Forcer la fermeture de la fenêtre Windows PowerShell
Ctrl+Origine       | Supprimer à partir du début de la ligne de commande actuelle
Ctrl+Fin        | Supprimer jusqu’à la fin de la ligne de commande
F1              | Déplacer le curseur d’un caractère vers la droite sur la ligne de commande
F2              | Créer une commande en copiant la dernière commande jusqu’au caractère que vous tapez
F3              | Terminer la ligne de commande avec le contenu de votre dernière ligne de commande
F4              | Supprimer des caractères à la position du curseur
F5              | Parcourir l’historique des commandes (des plus récentes au plus anciennes). Pour accéder aux commandes de l’historique dans Accès Web Windows PowerShell, cliquez sur les boutons de défilement **Historique** dans la console web.
F7              | Sélectionner de manière interactive une commande dans votre historique de commandes
F8              | Parcourir l’historique en affichant les commandes qui correspondent au texte actif
F9              | Exécuter une commande numérotée spécifique de l’historique
Page précédente         | Exécuter la première commande de l’historique
Page suivante       | Exécuter la dernière commande de l’historique
Alt+F7          | Effacer la liste de l’historique de commandes

### <a name="limitations-of-the-web-based-console"></a>Limitations de la console web

- Double-saut

  Vous pouvez rencontrer la limitation relative au double-saut (connexion à un second ordinateur à partir de la première connexion) si vous tentez de créer ou de travailler sur une nouvelle session à l’aide d’Accès Web Windows PowerShell.
  Accès Web Windows PowerShell utilise une instance d’exécution à distance et, actuellement, **PowerShell.exe** ne prend pas en charge l’établissement d’une connexion à distance vers un second ordinateur à partir d’une instance d’exécution à distance. Si vous essayez de vous connecter à un deuxième ordinateur distant à partir d’une connexion existante, par exemple avec la cmdlet **Enter-PSSession**, vous risquez de recevoir différents messages d’erreur, comme &euro;Impossible de récupérer les ressources réseau.

  Pour éviter les erreurs de double-saut, votre administrateur doit configurer l’authentification CredSSP dans l’environnement réseau de votre organisation. Pour plus d’informations sur la configuration de l’authentification CredSSP, consultez [CredSSP pour la communication à distance au deuxième saut](https://devblogs.microsoft.com/powershell/credssp-for-second-hop-remoting/) sur le blog de PowerShell. Vous pouvez également fournir des informations d’identification explicites quand vous voulez gérer un second ordinateur distant ; il est peu probable que des informations d’identification implicites autorisent le second saut.

- Communication à distance

  Accès Web Windows PowerShell utilise et présente les mêmes limitations qu’une session Windows PowerShell à distance. Les commandes qui appellent directement des API de console Windows, telles que celles pour éditeurs basés sur console ou pour programmes de menu basé sur du texte, ne fonctionnent pas car les commandes ne lisent ni n’écrivent dans des canaux d’entrée, de sortie et d’erreur. Par conséquent, les commandes qui lancent un fichier exécutable, comme **notepad.exe**, ou qui affichent une interface utilisateur graphique, comme `OpenGridView` ou `ogv`, ne fonctionnent pas. Votre expérience est affectée par ce comportement ; pour vous, Accès Web Windows PowerShell semble ne pas répondre à votre commande.

- Saisie semi-automatique via la touche Tab

  La saisie semi-automatique par le biais de la touche Tab ne fonctionne pas dans une configuration de session avec une instance d’exécution restreinte ou en mode **NoLanguage**. Bien que les administrateurs puissent configurer une session pour prendre en charge la saisie semi-automatique via la touche TAB, cette pratique est déconseillée pour des raisons de sécurité car elle peut exposer les informations suivantes aux utilisateurs non autorisés :

  - chemins d’accès de système de fichiers internes ;
  - dossiers partagés sur les ordinateurs internes ;
  - variables dans l’instance d’exécution ;
  - types chargés ou espaces de noms du .NET Framework ;
  - Variables d'environnement

- Session **NoLanguage** ou instance d’exécution restreinte

  Les utilisateurs connectés à une configuration de session **NoLanguage** ou à une instance d’exécution restreinte dans Accès Web Windows PowerShell ne peuvent pas exécuter la commande **Quitter** pour mettre fin à la session. Pour se déconnecter, les utilisateurs doivent cliquer sur **Se déconnecter** dans la page de console.

- Connexion simultanée à plusieurs ordinateurs cibles.

  Si le serveur de passerelle exécute Windows Server 2012, Accès Web Windows PowerShell n’autorise qu’une seule connexion d’ordinateur distant par session de navigateur. Il n’autorise pas les utilisateurs à se connecter à plusieurs ordinateurs distants à l’aide d’onglets de navigateur distincts. Quand vous ouvrez un nouvel onglet ou une nouvelle fenêtre de navigateur, Accès Web Windows PowerShell vous invite à mettre fin à votre session active et à démarrer une nouvelle session, afin que vous puissiez vous connecter au nouvel (ou au même) ordinateur distant. Si toutefois vous souhaitez ouvrir plusieurs sessions sur différents ordinateurs distants, une fonctionnalité d’Internet Explorer vous permet d’établir une nouvelle session. Pour démarrer une nouvelle session de navigateur dans Internet Explorer, appuyez sur **Alt**, ouvrez le menu **Fichier**, puis sélectionnez **Nouvelle session**. Ensuite, ouvrez le site web Accès Web Windows PowerShell dans la nouvelle session et connectez-vous pour accéder à un autre ordinateur distant.

  Quand la passerelle Accès Web Windows PowerShell s’exécute sur Windows Server 2012 R2, les utilisateurs peuvent ouvrir plusieurs connexions à des ordinateurs distants dans différents onglets de navigateur. Si vous souhaitez ouvrir plusieurs connexions à un ordinateur distant à l’aide de la console web Windows PowerShell, vérifiez auprès de votre administrateur de passerelle Accès Web Windows PowerShell que cette fonctionnalité est prise en charge par le serveur de passerelle.

- Sessions Windows PowerShell persistantes (reconnexion).

  Une fois le délai d’expiration de la passerelle Accès Web Windows PowerShell atteint, la connexion à distance entre la passerelle et l’ordinateur cible est fermée. Ceci arrête toutes les applets de commande et scripts en cours. Il est conseillé d’utiliser l’infrastructure **-Job** Windows PowerShell quand vous effectuez des tâches longues, de manière à pouvoir démarrer des travaux, vous déconnecter de l’ordinateur, vous reconnecter ultérieurement et conserver les travaux. Un autre avantage offert par les applets de commande **-Job** est la possibilité de les démarrer à l’aide d’Accès Web Windows PowerShell, de se déconnecter puis de se reconnecter ultérieurement, en exécutant Accès Web Windows PowerShell ou un autre hôte (comme l’environnement d’écriture de scripts intégré de Windows PowerShell).

- Redimensionnement de la console.

  Vous pouvez redimensionner la fenêtre de console **PowerShell.exe** des trois manières suivantes :

  - en faisant glisser et en ajustant la taille de la fenêtre de console avec la souris ;
  - en modifiant les propriétés de hauteur et de largeur à l’aide d’une interface utilisateur graphique destinée aux propriétés de la console ;
  - en modifiant la hauteur et la largeur des fenêtres de console avec une applet de commande.

    La fenêtre de console Accès Web Windows PowerShell peut être configurée comme suit à l’aide des applets de commande. Dans l’exemple suivant, un utilisateur affecte la valeur **20** à la largeur de la console Accès Web Windows PowerShell.

    ```powershell
    $newSize = $Host.UI.RawUI.WindowSize
    $newSize.Width = $newSize.Width - 20
    $oldSize = $Host.UI.RawUI.WindowSize
    $Host.UI.RawUI.WindowSize = $newSize
    ```

    Vous pouvez modifier la hauteur de la console d’une manière similaire.

    D’autres exemples de personnalisation de l’affichage de la console sont disponibles sur le [blog de l’équipe Windows PowerShell](https://devblogs.microsoft.com/powershell).

## <a name="see-also"></a>Voir aussi

- [Hey, Scripting Guy !](https://devblogs.microsoft.com/scripting/)
