---
ms.date: 08/23/2017
keywords: powershell,applet de commande
title: installer et utiliser Accès Web Windows PowerShell
ms.openlocfilehash: 53558f9be5065c7f630f06e535ddab4d7ad72d9e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58056717"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Installer et utiliser Accès Web Windows PowerShell

Mise à jour : 5 novembre 2013 (modifié le 23 août 2017)

S'applique à : Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Introduction

Accès Web Windows PowerShell, introduit dans Windows Server 2012, joue le rôle d’une passerelle Windows PowerShell en fournissant une console web Windows PowerShell qui cible un ordinateur distant. Elle permet aux professionnels de l’informatique d’exécuter des commandes et des scripts Windows PowerShell à partir d’une console Windows PowerShell dans un navigateur web, sans nécessiter Windows PowerShell, ni de logiciel de gestion à distance ou d’installation d’un plug-in de navigateur sur le périphérique client. Tout ce qui est nécessaire pour exécuter la console web Windows PowerShell est une passerelle Accès Web Windows PowerShell correctement configurée, et un navigateur d’appareil client qui prend en charge JavaScript et accepte les cookies.

Un périphérique client est par exemple un ordinateur portable, un ordinateur personnel non professionnel, une tablette, une borne Web publique, un ordinateur sans système d’exploitation Windows ou encore un navigateur de téléphone portable. Les informaticiens peuvent effectuer des tâches de gestion stratégiques sur des serveurs Windows distants à partir de périphériques ayant accès à une connexion Internet et à un navigateur Web.

Après avoir installé et configuré correctement la passerelle, les utilisateurs peuvent accéder à une console Windows PowerShell à l’aide d’un navigateur web. Quand les utilisateurs ouvrent le site web Accès Web Windows PowerShell sécurisé, ils peuvent exécuter une console web Windows PowerShell après une authentification réussie.

L’installation et la configuration d’Accès Web Windows PowerShell forment un processus en trois étapes :

1. [Installer Accès Web Windows PowerShell](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Configurer la passerelle](#configure-the-gateway)
1. [Configurer une règle d’autorisation restrictive](#configure-a-restrictive-authorization-rule)

Avant d’installer et de configurer Accès Web Windows PowerShell, nous vous recommandons de lire ce guide dans son intégralité, qui inclut des instructions sur la façon d’installer, de sécuriser et de désinstaller cette fonctionnalité. La rubrique [Utiliser la console web Windows PowerShell](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) décrit comment les utilisateurs se connectent à la console web, et couvre les limitations et les différences entre la console Windows PowerShell basée sur le web et la console **powershell.exe**. Les utilisateurs finaux de la console web doivent lire la rubrique [Utiliser la console web Windows PowerShell](use-the-web-based-windows-powershell-console.md), mais il n’est pas nécessaire qu’ils lisent le reste de ce guide.

Cette rubrique ne fournit pas d’instructions détaillées sur les opérations du serveur Web IIS : elle décrit seulement les étapes nécessaires pour configurer la passerelle Accès Web Windows PowerShell. Pour plus d’informations sur la configuration et la sécurisation des sites web dans IIS, voir les ressources de documentation IIS dans la section Voir aussi.

Le diagramme suivant illustre le fonctionnement d’Accès Web Windows PowerShell.

![Diagramme Windows PowerShell Web Access](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Configuration requise pour exécuter Accès Web Windows PowerShell

Accès Web Windows PowerShell nécessite l’exécution, sur le serveur sur lequel la passerelle doit s’exécuter, d’un serveur web (IIS), de .NET Framework 4.5 et de Windows PowerShell 3.0 ou Windows PowerShell 4.0. Vous pouvez installer Accès Web Windows PowerShell sur un serveur qui exécute Windows Server 2012 R2 ou Windows Server 2012 en utilisant l’Assistant Ajout de rôles et de fonctionnalités dans le Gestionnaire de serveur ou des applets de commande de déploiement Windows PowerShell pour le Gestionnaire de serveur. Quand vous installez Accès Web Windows PowerShell à l’aide du Gestionnaire de serveur ou de ses applets de commande de déploiement, les rôles et fonctionnalités requis sont automatiquement ajoutés dans le cadre du processus d’installation.

Accès Web Windows PowerShell permet aux utilisateurs distants d’accéder aux ordinateurs de votre organisation en utilisant Windows PowerShell dans un navigateur web. Bien qu’Accès Web Windows PowerShell soit un outil de gestion pratique et puissant, l’accès web présente des risques de sécurité et doit être configuré de manière aussi sécurisée que possible. Nous recommandons aux administrateurs qui configurent la passerelle Accès Web Windows PowerShell d’utiliser les couches de sécurité disponibles, à la fois les règles d’autorisation basées sur des applets de commande incluses avec Accès Web Windows PowerShell et les couches de sécurité disponibles dans le serveur web (IIS) et les applications tierces. Cette documentation contient à la fois des exemples non sécurisés destinés uniquement aux environnements de test et des exemples recommandés pour des déploiements sécurisés.

## <a name="browser-and-client-device-support"></a>Prise en charge de navigateurs et de périphériques clients

Accès Web Windows PowerShell prend en charge les navigateurs suivants. Bien que les navigateurs mobiles ne soient pas officiellement pris en charge, nombre d’entre eux sont susceptibles de pouvoir exécuter la console web Windows PowerShell.
D’autres navigateurs acceptant les cookies, exécutant JavaScript et exécutant des sites Web HTTPS sont censés fonctionner, mais n’ont pas été testés officiellement.

### <a name="supported-desktop-computer-browsers"></a>Navigateurs d’ordinateur de bureau pris en charge

- Windows Internet Explorer for Microsoft Windows 8.0, 9.0, 10.0 et 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m pour Windows
- Apple Safari 5.1.2 pour Windows
- Apple Safari 5.1.2 pour Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Navigateurs ou appareils mobiles testés de façon minimale

- Windows Phone 7 et 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari pour système d’exploitation iPhone 5.0.1
- Apple Safari pour système d’exploitation iPad 2 5.0.1

### <a name="browser-requirements"></a>Configuration requise des navigateurs

Pour utiliser la console web Accès Web Windows PowerShell, les navigateurs doivent :

- autoriser les cookies à partir du site web de la passerelle Accès Web Windows PowerShell ;
- être en mesure d’ouvrir et de lire des pages HTTPS ;
- ouvrir et exécuter des sites web qui utilisent JavaScript.

## <a name="recommended-quick-deployment"></a>Déploiement rapide recommandé

Vous pouvez installer la passerelle Accès Web Windows PowerShell sur un serveur qui exécute Windows Server 2012 R2 ou Windows Server 2012 en utilisant des applets de commande Windows PowerShell, ou l’Assistant Ajout de rôles et de fonctionnalités qui s’ouvre à partir du Gestionnaire de serveur. Pour une installation et une configuration rapides, utilisez les applets de commande Windows PowerShell, comme décrit dans cette section.

1. [Installer Accès Web Windows PowerShell](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Configurer la passerelle](#configure-the-gateway)
1. [Configurer une règle d’autorisation restrictive](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Installer Accès Web Windows PowerShell à l’aide d’applets de commande PowerShell

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Pour installer Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell

1. Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.

   - Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.
   - Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

   > [!NOTE]
   > Dans Windows PowerShell 3.0 et 4.0, il n’est pas nécessaire d’importer le module d’applet de commande du Gestionnaire de serveur dans la session Windows PowerShell avant d’exécuter des applets de commande qui font partie du module. Un module est automatiquement importé la première fois que vous exécutez une applet de commande qui fait partie du module.
   > En outre, les applets de commande Windows PowerShell ne respectent pas la casse.

1. Tapez ce qui suit, puis appuyez sur **Entrée**, où *computer_name* représente le nom de l’ordinateur distant sur lequel vous souhaitez installer Accès Web Windows PowerShell, le cas échéant. Le paramètre `-Restart` redémarre automatiquement les serveurs de destination, si besoin.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Installer Accès Web Windows PowerShell à l’aide d’applets de commande Windows PowerShell n’ajoute pas les outils de gestion de serveur web (IIS) par défaut. Si vous voulez installer les outils de gestion sur le même serveur que la passerelle Accès Web Windows PowerShell, ajoutez le paramètre `-IncludeManagementTools` à la commande d’installation (comme indiqué dans cette étape). Si vous gérez le site web Accès Web Windows PowerShell à partir d’un ordinateur distant, installez le composant logiciel enfichable Gestionnaire des services Internet en installant les [outils d’administration de serveur distant pour Windows 8.1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) ou les [outils d’administration pour serveur distant pour Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) sur l’ordinateur à partir duquel vous voulez gérer la passerelle.

   Pour installer des rôles et fonctionnalités sur un disque dur virtuel hors connexion, vous devez ajouter les paramètres `-ComputerName` et `-VHD` . Le paramètre `-ComputerName` contient le nom du serveur sur lequel monter le disque dur virtuel tandis que le paramètre `-VHD` contient le chemin d’accès au fichier VHD sur le serveur spécifié.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Quand l’installation est terminée, vérifiez qu’Accès Web Windows PowerShell a été installé sur les serveurs de destination en exécutant l’applet de commande `Get-WindowsFeature` sur un serveur de destination, dans une console Windows PowerShell ouverte avec des droits d’utilisateur élevés. Vous pouvez également vérifier qu’Accès Web Windows PowerShell a été installé dans la console Gestionnaire de serveur en sélectionnant un serveur de destination dans la page **Tous les serveurs**, puis en affichant la vignette **Rôles et fonctionnalités** du serveur sélectionné. Vous pouvez aussi afficher le fichier Lisez-moi associé à Accès Web Windows PowerShell.

1. Une fois cette fonctionnalité installée, vous êtes invité à consulter le fichier Lisez-moi dans lequel se trouvent des instructions d’installation requises simples pour la passerelle. Ces instructions d’installation se trouvent également dans la section suivante, [Configurer la passerelle](#configure-the-gateway). Le chemin du fichier Lisez-moi est `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Configurer la passerelle

L’applet de commande **Install-PswaWebApplication** constitue un moyen rapide de configurer l’Accès Web Windows PowerShell. Bien que vous puissiez ajouter le paramètre `UseTestCertificate` à l’applet de commande `Install-PswaWebApplication` pour installer un certificat SSL auto-signé à des fins de test, cette pratique n’est pas sécurisée ; pour un environnement de production sécurisé, utilisez toujours un certificat SSL valide qui a été signé par une autorité de certification. Les administrateurs peuvent remplacer le certificat de test par le certificat signé de leur choix à l’aide de la console du Gestionnaire des services Internet.

Vous pouvez terminer la configuration de l’application web Accès Web Windows PowerShell en exécutant l’applet de commande `Install-PswaWebApplication` ou en effectuant les étapes de configuration via l’interface graphique dans le Gestionnaire des services Internet.
Par défaut, l’applet de commande installe l’application web, **pswa** (et son pool d’applications, **pswa_pool**), dans le conteneur **Site Web par défaut**, comme indiqué dans le Gestionnaire des services Internet ; si vous le voulez, vous pouvez obliger l’applet de commande à modifier le conteneur de site par défaut de l’application web. Le Gestionnaire des services Internet propose des options de configuration pour les applications web, telles que la modification du numéro de port ou du certificat SSL (Secure Sockets Layer).

> **![Note de sécurité](images/securitynote.jpeg) Note de sécurité** Nous recommandons vivement aux administrateurs de configurer la passerelle pour qu’elle utilise un certificat valide signé par une autorité de certification.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Pour configurer la passerelle Accès Web Windows PowerShell avec un certificat de test à l’aide de Install-PswaWebApplication

1. Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell.

   - Sur le Bureau Windows, cliquez avec le bouton droit sur **Windows PowerShell** dans la barre des tâches.
   - Dans l’écran d’**accueil** de Windows, cliquez sur **Windows PowerShell**.

2. Tapez ce qui suit, puis appuyez sur **Entrée**.

   `Install-PswaWebApplication -UseTestCertificate`

   > **![Note de sécurité](images/securitynote.jpeg) Note de sécurité** Le paramètre `UseTestCertificate` doit uniquement être utilisé dans un environnement de test privé. Pour un environnement de production sécurisé, nous vous recommandons d’utiliser un certificat valide signé par une autorité de certification.

   L’exécution de l’applet de commande permet d’installer l’application web Accès Web Windows PowerShell au sein du conteneur de site web IIS par défaut. L’applet de commande crée l’infrastructure nécessaire pour exécuter Accès Web Windows PowerShell sur le site web par défaut, `https://<server_name>/pswa`. Pour installer l’application Web dans un autre site Web, indiquez son nom en ajoutant le paramètre `WebSiteName` . Pour modifier le nom de l’application Web (par défaut, il s’agit de `pswa`), ajoutez le paramètre `WebApplicationName` .

   Les paramètres suivants peuvent être configurés en exécutant l’applet de commande. Vous pouvez les modifier manuellement dans la console du Gestionnaire des services Internet, si vous le souhaitez.

   - Path: /pswa
   - ApplicationPool : pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

   **Example** : `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   Dans cet exemple, le site web obtenu pour Accès Web Windows PowerShell est `https://<server_name>/myWebApp`.

   > [!NOTE]
   > Vous ne pouvez pas vous connecter tant que les utilisateurs ne se voient pas accorder l’accès au site web en ajoutant des règles d’autorisation. Pour plus d’informations, consultez [Configurer une règle d’autorisation restrictive](#configure-a-restrictive-authorization-rule) et [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Pour configurer la passerelle Windows PowerShell Web Access avec un certificat authentique à l’aide de Install-PswaWebApplication et IIS Manager

1. Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell.

   - Sur le Bureau Windows, cliquez avec le bouton droit sur **Windows PowerShell** dans la barre des tâches.
   - Dans l’écran d’**accueil** de Windows, cliquez sur **Windows PowerShell**.

2. Tapez ce qui suit, puis appuyez sur **Entrée**.

   `Install-PswaWebApplication`

   Les paramètres de passerelle suivants peuvent être configurés en exécutant l’applet de commande. Vous pouvez les modifier manuellement dans la console du Gestionnaire des services Internet, si vous le souhaitez. Vous pouvez également spécifier des valeurs pour les paramètres `WebsiteName` et `WebApplicationName` de l’applet de commande `Install-PswaWebApplication` .

   - Path: /pswa
   - ApplicationPool : pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

3. Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes.

   - Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows. Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.
   - Dans l’écran d’**accueil** de Windows, cliquez sur **Gestionnaire de serveur**.

4. Dans le volet de l’arborescence du Gestionnaire des services Internet, développez le nœud du serveur sur lequel Accès Web Windows PowerShell est installé jusqu’à ce que le dossier **Sites** apparaisse. Développez le dossier **Sites**.

5. Sélectionnez le site web dans lequel vous avez installé l’application web d’Accès Web Windows PowerShell.
   Dans le volet **Actions**, cliquez sur **Liaisons**.

6. Dans la boîte de dialogue **Liaisons de site**, cliquez sur **Ajouter**.

7. Dans la boîte de dialogue **Ajouter la liaison de site**, dans le champ **Type**, sélectionnez **https**.

8. Dans le champ **Certificat SSL**, sélectionnez votre certificat signé dans le menu déroulant.
   Cliquez sur **OK**. Pour plus d’informations sur l’obtention d’un certificat, consultez [Pour configurer un certificat SSL dans le Gestionnaire des services Internet](#to-configure-an-ssl-certificate-in-iis-manager) dans cette rubrique.

   L’application web d’Accès Web Windows PowerShell est à présent configurée pour utiliser votre certificat SSL signé.

   Vous pouvez accéder à la fonctionnalité Accès Web Windows PowerShell en ouvrant `https://<server_name>/pswa` dans une fenêtre de navigateur.

   > [!NOTE]
   > Vous ne pouvez pas vous connecter tant que les utilisateurs ne se voient pas accorder l’accès au site web en ajoutant des règles d’autorisation. Pour plus d’informations, consultez [Configurer une règle d’autorisation restrictive](#configure-a-restrictive-authorization-rule) dans cette rubrique, et [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Configurer une règle d’autorisation restrictive

Une fois Accès Web Windows PowerShell installé et la passerelle configurée, les utilisateurs peuvent ouvrir la page de connexion dans un navigateur, mais ils ne peuvent pas se connecter tant que l’administrateur d’Accès Web Windows PowerShell ne leur a pas octroyé explicitement un accès. Le contrôle d’accès d’Accès Web Windows PowerShell est géré à l’aide de l’ensemble d’applets de commande Windows PowerShell décrit dans le tableau suivant. Il n’existe aucune interface utilisateur graphique équivalente pour ajouter ou gérer les règles d’autorisation. Pour plus d’informations sur les applets de commande Accès Web Windows PowerShell, consultez les rubriques de référence des applets de commande, [Applets de commande Accès Web Windows PowerShell](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Pour plus de détails sur les règles d’autorisation et la sécurité d’Accès Web Windows PowerShell, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Pour ajouter une règle d’autorisation restrictive

1. Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.

   - Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.
   - Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

2. Étape facultative pour restreindre l’accès utilisateur à l’aide de configurations de session : Vérifiez que les configurations de session que vous souhaitez utiliser dans vos règles existent déjà. Si elles n’ont pas encore été créées, utilisez les instructions relatives à la création de configurations de session dans [About Session Configuration Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Tapez ce qui suit, puis appuyez sur **Entrée**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Cette règle d’autorisation accorde à un utilisateur spécifique d’accéder à un ordinateur sur le réseau auquel il a généralement accès, avec un accès à une configuration de session spécifique limitée aux besoins habituels de l’utilisateur en matière de script et d’applet de commande.

   Dans l’exemple suivant, un utilisateur nommé `JSmith` dans le domaine `Contoso` se voit accorder un accès pour gérer l’ordinateur `Contoso_214`et utiliser une configuration de session nommée `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Vérifiez que la règle a été créée en exécutant l’applet de commande `Get-PswaAuthorizationRule` ou `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`.

   Par exemple, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Après avoir configuré une règle d’autorisation, les utilisateurs autorisés peuvent se connecter à la console web et commencer à utiliser Accès Web Windows PowerShell.

## <a name="custom-deployment"></a>Déploiement personnalisé

Vous pouvez installer la passerelle Accès Web Windows PowerShell sur un serveur qui exécute Windows Server 2012 R2 ou Windows Server 2012 en utilisant l’Assistant Ajout de rôles et de fonctionnalités dans le Gestionnaire de serveur.
Après avoir installé Accès Web Windows PowerShell, vous pouvez personnaliser la configuration de la passerelle dans le Gestionnaire des services Internet.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Installer Accès Web Windows PowerShell à l’aide de l’Assistant Ajout de rôles et de fonctionnalités

1. Si le Gestionnaire de serveur est déjà ouvert, passez à l’étape suivante. S’il n’est pas déjà ouvert, ouvrez-le en effectuant l’une des opérations suivantes.

   - Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.
   - Dans l’écran d’**accueil** de Windows, cliquez sur **Gestionnaire de serveur**.

2. Dans le menu **Gérer**, cliquez sur **Ajouter des rôles et fonctionnalités**.

3. Dans la page **Sélectionner le type d’installation**, sélectionnez **Installation basée sur un rôle ou une fonctionnalité**.
   Cliquez sur **Suivant**.

4. Dans la page **Sélectionner le serveur de destination**, sélectionnez un serveur dans le pool de serveurs ou sélectionnez un disque dur virtuel hors connexion. Pour sélectionner un disque dur virtuel hors connexion en guise de serveur de destination, choisissez d’abord le serveur sur lequel monter le disque dur virtuel, puis sélectionnez le fichier VHD. Pour plus d’informations sur l’ajout de serveurs à votre pool de serveurs, consultez l’Aide du Gestionnaire de serveur. Une fois que vous avez sélectionné le serveur de destination, cliquez sur **Suivant**.

5. Dans la page **Sélectionner des fonctionnalités** de l’Assistant, développez **Windows PowerShell**, puis sélectionnez **Accès Web Windows PowerShell**.

6. Notez que vous êtes invité à ajouter les fonctionnalités requises, telles que le .NET Framework 4.5 et les services de rôle du serveur web (IIS). Ajoutez les fonctionnalités requises et continuez.

   > [!NOTE]
   > Installer Accès Web Windows PowerShell à l’aide de l’Assistant Ajout de rôles et de fonctionnalités installe également le serveur web (IIS), y compris le composant logiciel enfichable Gestionnaire des services Internet. Le composant logiciel enfichable et d’autres outils de gestion des services Internet IIS sont installés par défaut si vous utilisez l’Assistant Ajout de rôles et de fonctionnalités. Si vous installez Accès Web Windows PowerShell à l’aide d’applets de commande Windows PowerShell comme décrit dans la procédure suivante, les outils de gestion ne sont pas ajoutés par défaut.

7. Dans la page **Confirmer les sélections d’installation**, si les fichiers de fonctionnalités d’Accès Web Windows PowerShell ne sont pas enregistrés sur le serveur de destination que vous avez sélectionné à l’étape 4, cliquez sur **Spécifier un autre chemin d’accès source**, puis indiquez le chemin des fichiers de fonctionnalités. Sinon, cliquez sur **Installer**.

8. Une fois que vous avez cliqué sur **Installer**, la page **Progression de l’installation** affiche la progression de l’installation, les résultats et des messages tels que des avertissements, échecs ou étapes de configuration de post-installation requises pour Accès Web Windows PowerShell. Une fois cette fonctionnalité installée, vous êtes invité à consulter le fichier Lisez-moi dans lequel se trouvent des instructions d’installation requises simples pour la passerelle. Ces instructions sont également incluses dans la présente rubrique. Le chemin du fichier Lisez-moi est `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Configurer la passerelle

Les instructions données dans cette section concernent l’installation de l’application web Accès Web Windows PowerShell dans un sous-répertoire, et non pas dans le répertoire racine de votre site web. Cette procédure est l’équivalent basé sur l’interface graphique utilisateur des actions effectuées par l’applet de commande `Install-PswaWebApplication` . Cette section inclut également des instructions sur la manière d’utiliser le Gestionnaire des services Internet pour configurer la passerelle Accès Web Windows PowerShell en tant que site web racine.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Pour configurer la passerelle dans un site web existant à l’aide du Gestionnaire des services Internet

1. Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes.

   - Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows. Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.
   - Sur l’écran d’**accueil** de Windows, tapez une partie du nom **Gestionnaire des services Internet (IIS)**. Cliquez sur le raccourci quand il s’affiche dans les résultats **Applications**.

2. Créez un pool d’applications pour Accès Web Windows PowerShell. Développez le nœud du serveur de passerelle dans l’arborescence du Gestionnaire des services Internet, sélectionnez **Pools d’applications**, puis cliquez sur **Ajouter un pool d’applications** dans le volet **Actions**.

3. Ajoutez un nouveau pool d’applications portant le nom **pswa_pool** ou indiquez un autre nom. Cliquez sur **OK**.

4. Dans le volet de l’arborescence du Gestionnaire des services Internet, développez le nœud du serveur sur lequel Accès Web Windows PowerShell est installé jusqu’à ce que le dossier **Sites** apparaisse. Sélectionnez le dossier **Sites**.

5. Cliquez avec le bouton droit sur le site web (par exemple, **Site web par défaut**) auquel vous voulez ajouter le site web Accès Web Windows PowerShell, puis cliquez sur **Ajouter une application**.

6. Dans le champ **Alias**, tapez pswa ou indiquez un autre alias. L’alias devient le nom du répertoire virtuel. Par exemple, **pswa** dans l’URL suivante représente l’alias spécifié au cours de cette étape : `https://<server-name>/pswa`.

7. Dans le champ **Pool d’applications**, sélectionnez le pool d’applications que vous avez créé à l’étape 3.

8. Dans le champ **Chemin d’accès physique**, naviguez jusqu’à l’emplacement de l’application. Vous pouvez utiliser l’emplacement par défaut, `$env:windir/Web/PowerShellWebAccess/wwwroot`. Cliquez sur **OK**.

9. Suivez les étapes de la procédure [Pour configurer un certificat SSL dans le Gestionnaire des services Internet](#to-configure-an-ssl-certificate-in-iis-manager) dans cette rubrique.

10. ![](images/SecurityNote.jpeg) Étape de sécurité facultative :

    Avec le site web sélectionné dans l’arborescence, double-cliquez sur **Paramètres SSL** dans le volet de contenu.
    Sélectionnez **Exiger SSL**, puis dans le volet **Actions**, cliquez sur **Appliquer**. Dans le volet **Paramètres SSL**, vous pouvez éventuellement exiger que les utilisateurs qui se connectent au site web d’Accès Web Windows PowerShell possèdent des certificats clients. Ceux-ci aident à vérifier l’identité d’un utilisateur de périphérique client. Pour plus d’informations sur la manière dont l’exigence de certificats clients permet de renforcer la sécurité d’Accès Web Windows PowerShell, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md) dans ce guide.

11. Ouvrez une session de navigateur sur un périphérique client. Pour plus d’informations sur les navigateurs et périphériques pris en charge, consultez [Prise en charge de navigateurs et de périphériques client](#browser-and-client-device-support) dans cette rubrique.

12. Ouvrez le nouveau site web Accès Web Windows PowerShell, **https://\<*nom_serveur_de_passerelle*\>/pswa**.

    Le navigateur doit afficher la page de connexion de la console d’Accès Web Windows PowerShell.

    > [!NOTE]
    > Vous ne pouvez pas vous connecter tant que les utilisateurs ne se voient pas accorder l’accès au site web en ajoutant des règles d’autorisation. Pour plus d’informations, consultez [Configurer une règle d’autorisation restrictive](#configure-a-restrictive-authorization-rule) dans cette rubrique, et [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. Dans une session Windows PowerShell qui a été ouverte avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur), exécutez le script suivant dans lequel *application_pool_name* représente le nom du pool d’applications que vous avez créé à l’étape 3, afin de donner les droits d’accès au pool d’applications dans le fichier d’autorisations.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Pour afficher les droits d’accès existants sur le fichier d’autorisations, exécutez la commande suivante :

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Pour configurer la passerelle comme site web racine avec un certificat de test à l’aide du Gestionnaire des services Internet

1. Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes.

   - Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows. Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.
   - Sur l’écran d’**accueil** de Windows, tapez une partie du nom **Gestionnaire des services Internet (IIS)**. Cliquez sur le raccourci quand il s’affiche dans les résultats **Applications**.

1. Dans le volet de l’arborescence du Gestionnaire des services Internet, développez le nœud du serveur sur lequel Accès Web Windows PowerShell est installé jusqu’à ce que le dossier **Sites** apparaisse. Sélectionnez le dossier **Sites**.

1. Dans le volet **Actions**, cliquez sur **Ajouter un site Web**.

1. Tapez le nom du site web, comme **Accès Web Windows PowerShell**.

1. Un pool d’applications est créé automatiquement pour le nouveau site web. Pour utiliser un autre pool d’applications, cliquez sur **Sélectionner** pour sélectionner un pool d’applications à associer au nouveau site web. Sélectionnez l’autre pool d’applications dans la boîte de dialogue **Sélectionner un pool d’applications**, puis cliquez sur **OK**.

1. Dans la zone de texte **Chemin d’accès physique**, accédez à %windir%/Web/PowerShellWebAccess/wwwroot.

1. Dans le champ **Type** de la zone **Liaison**, sélectionnez **https**.

1. Assignez au site web un numéro de port qui n’est pas déjà utilisé par un autre site ou une autre application.
   Pour localiser les ports ouverts, vous pouvez exécuter la commande **netstat** dans une fenêtre d’invite de commandes. Le numéro de port par défaut est 443.

   Modifiez le port par défaut si un autre site web utilise déjà le port 443 ou si vous avez d’autres raisons d’ordre sécuritaire. Si un autre site web qui s’exécute sur votre serveur de passerelle utilise votre port sélectionné, un avertissement s’affiche quand vous cliquez sur **OK** dans la boîte de dialogue **Ajouter un site Web**. Vous devez utiliser un port inutilisé pour exécuter Accès Web Windows PowerShell.

1. Selon les besoins de votre organisation, spécifiez éventuellement un nom d’hôte qui a du sens pour votre organisation et ses utilisateurs, comme **`www.contoso.com`**. Cliquez sur **OK**.

1. Pour un environnement de production plus sécurisé, nous vous recommandons vivement de fournir un certificat valide signé par une autorité de certification. Vous devez fournir un certificat SSL, car les utilisateurs peuvent uniquement se connecter à Accès Web Windows PowerShell par le biais d’un site web HTTPS. Pour plus d’informations sur l’obtention d’un certificat, consultez [Pour configurer un certificat SSL dans le Gestionnaire des services Internet](#to-configure-an-ssl-certificate-in-iis-manager) dans cette rubrique.

1. Cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter un site Web**.

1. Dans une session Windows PowerShell qui a été ouverte avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur), exécutez le script suivant dans lequel _application_pool_name_ représente le nom du pool d’applications que vous avez créé à l’étape 4, afin de donner les droits d’accès au pool d’applications dans le fichier d’autorisations.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   Pour afficher les droits d’accès existants sur le fichier d’autorisations, exécutez la commande suivante :

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. Avec le nouveau site Web sélectionné dans le volet de l’arborescence du Gestionnaire des services Internet, cliquez sur **Démarrer** dans le volet **Actions** pour démarrer le site Web.

1. Ouvrez une session de navigateur sur un périphérique client. Pour plus d’informations sur les navigateurs et périphériques pris en charge, voir [Prise en charge de navigateurs et de périphériques client](#browser-and-client-device-support) dans ce document.

1. Ouvrez le site web Accès Web Windows PowerShell.

   Dans la mesure où le site web racine pointe vers le dossier Accès Web Windows PowerShell, le navigateur doit afficher la page de connexion Accès Web Windows PowerShell quand vous ouvrez `https://<gateway_server_name>`. Il n’est pas nécessaire d’ajouter **/pswa** à l’URL.

   > [!NOTE]
   > Vous ne pouvez pas vous connecter tant que les utilisateurs ne se voient pas accorder l’accès au site web en ajoutant des règles d’autorisation. Pour plus d’informations, consultez [Configurer une règle d’autorisation restrictive](#configure-a-restrictive-authorization-rule) dans cette rubrique, et [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Configuration d’une règle d’autorisation restrictive

Une fois Accès Web Windows PowerShell installé et la passerelle configurée, les utilisateurs peuvent ouvrir la page de connexion dans un navigateur, mais ils ne peuvent pas se connecter tant que l’administrateur d’Accès Web Windows PowerShell ne leur a pas octroyé explicitement un accès. Le contrôle d’accès d’Accès Web Windows PowerShell est géré à l’aide de l’ensemble d’applets de commande Windows PowerShell décrit dans le tableau suivant. Il n’existe aucune interface utilisateur graphique équivalente pour ajouter ou gérer les règles d’autorisation. Pour plus d’informations sur les applets de commande Accès Web Windows PowerShell, consultez les rubriques de référence des applets de commande, [Applets de commande Accès Web Windows PowerShell](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Pour plus de détails sur les règles d’autorisation et la sécurité d’Accès Web Windows PowerShell, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Ajout d’une règle d’autorisation restrictive

1. Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.

   - Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.
   - Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

1. ![Remarque sur la sécurité](images/SecurityNote.jpeg) Étape facultative pour restreindre l’accès utilisateur à l’aide de configurations de session :

   Vérifiez que les configurations de session que vous souhaitez utiliser dans vos règles existent déjà. Si elles n’ont pas encore été créées, utilisez les instructions relatives à la création de configurations de session dans [About Session Configuration Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Tapez ce qui suit, puis appuyez sur **Entrée**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Cette règle d’autorisation accorde à un utilisateur spécifique l’accès à un ordinateur sur le réseau auquel il a généralement accès, avec un accès à une configuration de session spécifique limitée aux besoins habituels de l’utilisateur en matière de script et d’applet de commande.

   Dans l’exemple suivant, un utilisateur nommé `JSmith` dans le domaine `Contoso` se voit accorder un accès pour gérer l’ordinateur `Contoso_214`et utiliser une configuration de session nommée `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. Vérifiez que la règle a été créée en exécutant l’applet de commande `Get-PswaAuthorizationRule` ou `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

   Par exemple, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   Après avoir configuré une règle d’autorisation, les utilisateurs autorisés peuvent se connecter à la console web et commencer à utiliser Accès Web Windows PowerShell.

## <a name="configure-a-genuine-certificate"></a>Configurer un certificat authentique

Pour un environnement de production sécurisé, utilisez toujours un certificat SSL valide signé par une autorité de certification. La procédure décrite dans cette section détaille comment obtenir et appliquer un certificat SSL valide à partir d’une autorité de certification.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Pour configurer un certificat SSL dans le Gestionnaire des services Internet

1. Dans le volet de l’arborescence du Gestionnaire des services Internet, sélectionnez le serveur sur lequel Accès Web Windows PowerShell est installé.

1. Dans le volet de contenu, double-cliquez sur **Certificats de serveur**.

1. Dans le volet **Actions**, effectuez l’une des opérations suivantes. Pour plus d’informations sur la configuration des certificats de serveur dans IIS, consultez [Configuration des certificats de serveur dans IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Cliquez sur **Importer** pour importer un certificat existant valide depuis un emplacement sur votre réseau.
   - Cliquez sur **Créer une demande de certificat** pour demander un certificat auprès d’une autorité de certification comme [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/) ou [GeoTrust](https://www.geotrust.com/). Le nom courant du certificat doit correspondre à l’en-tête d’hôte dans la demande.

     Par exemple, si le navigateur client demande `http://www.contoso.com/`, le nom commun doit également être `http://www.contoso.com/`. Il s’agit de l’option recommandée la plus sécurisée pour fournir un certificat à la passerelle Accès Web Windows PowerShell.

   - Cliquez sur **Créer un certificat auto-signé** pour créer un certificat que vous pouvez utiliser immédiatement, puis faire signer ultérieurement par une autorité de certification si besoin. Spécifiez un nom convivial pour le certificat auto-signé, comme **Accès Web Windows PowerShell**. Cette option est considérée comme non sécurisée et recommandée uniquement dans un environnement de test privé.

1. Après avoir créé ou obtenu un certificat, sélectionnez le site web auquel il est appliqué (par exemple, le **Site Web par défaut**) dans le volet de l’arborescence du Gestionnaire des services Internet, puis cliquez sur **Liaisons** dans le volet **Actions**.

1. Dans la boîte de dialogue **Ajouter la liaison de site**, ajoutez une liaison **https** pour le site, si aucune n’est déjà affichée. Si vous n’utilisez pas de certificat auto-signé, spécifiez le nom d’hôte de l’étape 3 de cette procédure. Si vous utilisez un certificat auto-signé, vous pouvez ignorer cette étape.

1. Sélectionnez le certificat que vous avez obtenu ou créé à l’étape 3 de cette procédure, puis cliquez sur **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Utilisation de la console Web Windows PowerShell

Une fois qu’Accès Web Windows PowerShell est installé et la configuration de la passerelle terminée comme décrit dans cette rubrique, la console web Windows PowerShell est prête à être utilisée. Pour plus d’informations sur la prise en main de la console web, consultez [Utiliser la console web Windows PowerShell](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Voir aussi

[Documentation d’Internet Information Services (IIS) 7.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[Aide du Gestionnaire des services Internet](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Configure Web Server Security (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[Ressources de déploiement de la sécurité IPsec](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))
