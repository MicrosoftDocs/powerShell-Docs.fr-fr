---
ms.date: 06/27/2017
keywords: powershell,applet de commande
title: Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell
ms.openlocfilehash: 9bc1be125ebab4e9ba29ba832b442777e9bfc859
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500884"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell

Mise à jour : 24 juin 2013

S’applique à : Windows Server 2012 R2, Windows Server 2012

La fonctionnalité Accès Web Windows PowerShell dans Windows Server 2012 R2 et Windows Server 2012 a un modèle de sécurité restrictif. Les utilisateurs doivent recevoir explicitement une autorisation d’accès avant de pouvoir se connecter à la passerelle Accès Web Windows PowerShell et utiliser la console web Windows PowerShell.

## <a name="configuring-authorization-rules-and-site-security"></a>Configuration des règles d’autorisation et de la sécurité du site

Une fois Accès Web Windows PowerShell installé et la passerelle configurée, les utilisateurs peuvent ouvrir la page de connexion dans un navigateur, mais ils ne peuvent pas se connecter tant que l’administrateur d’Accès Web Windows PowerShell ne leur a pas octroyé explicitement un accès. Le contrôle d’accès d’« Accès Web Windows PowerShell » est géré à l’aide de l’ensemble des applets de commande Windows PowerShell décrit dans le tableau suivant. Il n’existe aucune interface utilisateur graphique équivalente pour ajouter ou gérer les règles d’autorisation.
Consultez [Applets de commande d’Accès Web Windows PowerShell](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Les administrateurs peuvent définir `{0-n}` règles d’authentification pour Accès Web Windows PowerShell. La sécurité par défaut est restrictive plutôt que permissive ; les règles à authentification zéro signifient qu’aucun utilisateur n’a accès à quoi que ce soit.

[Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) et [Test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) dans Windows Server 2012 R2 incluent un paramètre Credential qui permet d’ajouter et de tester les règles d’autorisation d’Accès Web Windows PowerShell depuis un ordinateur distant ou une session Accès Web Windows PowerShell active. Comme avec d’autres applets de commande Windows PowerShell disposant d’un paramètre Credential, vous pouvez définir un objet PSCredential comme valeur du paramètre. Pour créer un objet PSCredential qui contient les informations d’identification que vous souhaitez transmettre à un ordinateur distant, exécutez l’applet de commande [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential).

Les règles d’authentification Accès Web Windows PowerShell sont des règles de liste verte. Chaque règle est une définition d’une connexion autorisée entre des utilisateurs, des ordinateurs cibles et des [configurations de session](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) Windows PowerShell particulières (également appelées points de terminaison ou _instances d’exécution_) sur des ordinateurs cibles spécifiés.
Pour obtenir une explication sur **les instances d’exécution**, consultez [Beginning Use of PowerShell Runspaces](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> Il suffit qu’une règle soit satisfaite pour qu’un utilisateur obtienne l’accès. Si un utilisateur se voit accorder l’accès à un seul ordinateur avec accès linguistique complet ou avec accès uniquement aux applets de commande de gestion à distance Windows PowerShell, depuis la console web, il peut se connecter à d’autres ordinateurs qui sont connectés au premier ordinateur cible. La façon la plus sûre de configurer Accès Web Windows PowerShell consiste à autoriser les utilisateurs à accéder uniquement à des configurations de session contrainte pour les autoriser à accomplir des tâches spécifiques qu’ils ont normalement besoin d’effectuer à distance.

Les applets de commande référencées dans [Applets de commande d’Accès Web Windows PowerShell](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) permettent de créer un ensemble de règles d’accès qui sont utilisées pour autoriser un utilisateur sur la passerelle Accès Web Windows PowerShell. Ces règles diffèrent des listes de contrôle d’accès sur l’ordinateur de destination et constituent une couche de sécurité supplémentaire pour l’accès par le Web. La section suivante fournit davantage de détails sur la sécurité.

Si des utilisateurs ne parviennent pas à traverser l’une des couches de sécurité précédentes, ils reçoivent un message générique « Accès refusé » dans leur fenêtre de navigateur. Bien que les détails sur la sécurité soient consignés sur le serveur passerelle, aucune information n’est fournie aux utilisateurs finals quant au nombre de couches de sécurité qu’ils ont traversées ou quant à la couche au niveau de laquelle l’échec d’authentification ou de connexion a échoué.

Pour plus d’informations sur la configuration de règles d’autorisation, consultez [Configuration des règles d’autorisation](#configuring-authorization-rules-and-site-security) dans cette rubrique.

### <a name="security"></a>Sécurité

Le modèle de sécurité Accès Web Windows PowerShell comporte quatre couches entre un utilisateur final de la console web et un ordinateur cible. Les administrateurs d’Accès Web Windows PowerShell peuvent ajouter des couches de sécurité par le biais d’une configuration complémentaire dans la console du Gestionnaire des services Internet. Pour plus d’informations sur la sécurisation des sites web dans la console du Gestionnaire des services Internet, consultez [Configurer la sécurité du serveur web (IIS 7)](https://technet.microsoft.com/library/cc731278).

Pour plus d’informations sur les conseils d’utilisation d’IIS et la prévention des attaques par déni de service, consultez [Best Practices for Preventing DoS/Denial of Service Attacks](https://technet.microsoft.com/library/cc750213) (Bonnes pratiques de prévention des attaques par déni de service).
Un administrateur peut également acheter et installer des logiciels d’authentification supplémentaires.

Le tableau suivant décrit les quatre couches de sécurité entre les utilisateurs finals et les ordinateurs cibles.

|Level|Couche|
|-|-|
|1|[fonctionnalités de sécurité du serveur web IIS](#iis-web-server-security-features)|
|2|[authentification de la passerelle basée sur les formulaires Accès Web Windows PowerShell](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[règles d’autorisation d’Accès Web Windows PowerShell](#windows-powershell-web-access-authorization-rules)|
|4|[règles d’autorisation et d’authentification cibles](#target-authentication-and-authorization-rules)|

Vous pouvez trouver des informations détaillées sur chaque couche sous les titres suivants :

#### <a name="iis-web-server-security-features"></a>Fonctionnalités de sécurité du serveur web IIS

Les utilisateurs d’Accès Web Windows PowerShell doivent toujours fournir un nom d’utilisateur et un mot de passe pour authentifier leurs comptes sur la passerelle. Cependant, les administrateurs d’Accès Web Windows PowerShell peuvent également activer ou désactiver l’authentification facultative des certificats clients (consultez [installer et utiliser Accès Web Windows PowerShell](install-and-use-windows-powershell-web-access.md) pour activer un certificat de test puis pour configurer un certificat authentique).

Pour la fonctionnalité de certificat client facultatif, les utilisateurs doivent posséder un certificat client valide en plus de leur nom d’utilisateur/mot de passe. Cette fonctionnalité fait partie de la configuration du serveur web (IIS). Quand la couche du certificat client est activée, la page de connexion à Accès Web Windows PowerShell invite les utilisateurs à fournir des certificats valides avant d’évaluer leurs informations d’identification de connexion. L’authentification de certificat client vérifie automatiquement la présence du certificat client. Si aucun certificat valide n’est trouvé, Accès Web Windows PowerShell en informe les utilisateurs, pour qu’ils puissent fournir ce certificat. Si un certificat client valide est trouvé, Accès Web Windows PowerShell ouvre la page de connexion pour que les utilisateurs indiquent leur nom d’utilisateur et leur mot de passe.

Il s’agit d’un exemple de paramètres de sécurité supplémentaires offerts par le serveur Web IIS. Pour plus d’informations sur d’autres fonctionnalités de sécurité IIS, consultez [Configurer la sécurité du serveur web (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Authentification de la passerelle basée sur les formulaires Accès Web Windows PowerShell

La page de connexion d’Accès Web Windows PowerShell requiert un ensemble d’informations d’identification (nom d’utilisateur et mot de passe) et offre aux utilisateurs la possibilité de fournir des informations d’identification différentes pour l’ordinateur cible.
Si l’utilisateur ne fournit pas d’autres informations d’identification, le nom d’utilisateur et le mot de passe principaux utilisés pour se connecter à la passerelle sont également utilisés pour se connecter à l’ordinateur cible.

Les informations d’identification requises sont authentifiées sur la passerelle Accès Web Windows PowerShell. Ces informations d’identification doivent être des comptes d’utilisateurs valides sur le serveur de passerelle Accès Web Windows PowerShell local ou dans Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Règles d’autorisation d’Accès Web Windows PowerShell

Une fois que l’utilisateur est authentifié au niveau de la passerelle, l’Accès Web Windows PowerShell passe en revue les règles d’autorisation pour vérifier si l’utilisateur a accès à l’ordinateur cible demandé. Une fois que l’autorisation a été accordée; les informations d’identification de l’utilisateur sont transmises à l’ordinateur cible.

Ces règles sont évaluées uniquement après qu’un utilisateur a été authentifié par la passerelle et avant qu’un utilisateur puisse être authentifié sur un ordinateur cible.

#### <a name="target-authentication-and-authorization-rules"></a>Règles d’autorisation et d’authentification cibles

La couche finale de sécurité pour Accès Web Windows PowerShell est la configuration de sécurité elle-même de l’ordinateur cible. Les utilisateurs doivent avoir les droits d’accès appropriés configurés sur l’ordinateur cible, ainsi que dans les règles d’autorisation d’Accès Web Windows PowerShell, pour exécuter une console web Windows PowerShell qui affecte un ordinateur cible par le biais d’Accès Web Windows PowerShell.

Cette couche offre les mêmes mécanismes de sécurité que ceux qui évalueraient les tentatives de connexion si les utilisateurs créaient une session Windows PowerShell à distance sur un ordinateur cible depuis Windows PowerShell en exécutant les applets de commande [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) ou [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession).

Par défaut, Accès Web Windows PowerShell utilise les nom d’utilisateur et mot de passe principaux pour l’authentification sur la passerelle et l’ordinateur cible. La page de connexion web, dans une section intitulée **Paramètres de connexion facultatifs**, permet aux utilisateurs de fournir des informations d’identification différentes pour l’ordinateur cible, si nécessaire. Si l’utilisateur ne fournit pas d’autres informations d’identification, le nom d’utilisateur et le mot de passe principaux utilisés pour se connecter à la passerelle sont également utilisés pour se connecter à l’ordinateur cible.

Les règles d’autorisation peuvent servir à accorder aux utilisateurs un accès à une configuration de session particulière. Vous pouvez créer des _instances d’exécution restreintes_ ou des configurations de session pour Accès Web Windows PowerShell, puis autoriser des utilisateurs spécifiques à se connecter uniquement à des configurations de session spécifiques quand ils se connectent à Accès Web Windows PowerShell. Vous pouvez utiliser des listes de contrôle d’accès pour identifier les utilisateurs qui ont accès à des points de terminaison spécifiques et pour restreindre davantage l’accès à un point de terminaison pour un ensemble donné d’utilisateurs en appliquant les règles d’autorisation décrites dans cette section. Pour plus d’informations sur les instances d’exécution restreintes, consultez [Creating a constrained runspace](/powershell/scripting/developer/hosting/creating-a-constrained-runspace).

### <a name="configuring-authorization-rules"></a>Configuration des règles d’autorisation

Les administrateurs souhaitent probablement la même règle d’autorisation pour les utilisateurs d’Accès Web Windows PowerShell que celle déjà définie dans leur environnement pour la gestion à distance Windows PowerShell. La première procédure de cette section décrit comment ajouter une règle d’autorisation sécurisée qui accorde l’accès à un utilisateur qui se connecte pour gérer un seul ordinateur dans une seule configuration de session. La seconde procédure décrit comment supprimer une règle d’autorisation dont vous n’avez plus besoin.

Si vous envisagez d’utiliser des configurations de sessions personnalisées pour autoriser des utilisateurs spécifiques à travailler uniquement dans des instances d’exécution restreintes dans Accès Web Windows PowerShell, créez vos configurations de sessions personnalisées avant d’ajouter des règles d’autorisation qui s’y réfèrent. Vous ne pouvez pas utiliser les applets de commande d’Accès Web Windows PowerShell pour créer des configurations de sessions personnalisées. Pour plus d’informations sur la création de configurations de session personnalisée, consultez [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Les applets de commande d’Accès Web Windows PowerShell prennent en charge un seul caractère générique, un astérisque ( \* ). Les caractères génériques dans les chaînes ne sont pas pris en charge. Utilisez un seul astérisque par propriété (utilisateurs, ordinateurs ou configurations de sessions).

> [!NOTE]
> Pour découvrir d’autres façons d’utiliser des règles d’autorisation pour accorder un accès aux utilisateurs et mieux sécuriser l’environnement d’Accès Web Windows PowerShell, consultez [Autres exemples de scénarios de règles d’autorisation](#other-authorization-rule-scenario-examples) dans cette rubrique.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Pour ajouter une règle d’autorisation restrictive

1. Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.

   - Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

   - Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

2. **Étape facultative** Pour restreindre l’accès utilisateur à l’aide de configurations de session :

   Vérifiez que les configurations de session que vous voulez utiliser existent déjà dans vos règles.

   Si elles n’ont pas encore été créées, utilisez les instructions relatives à la création de configurations de session dans [About Session Configuration Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Cette règle d’autorisation permet à un utilisateur donné d’accéder à un ordinateur sur le réseau auquel il a généralement accès, avec un accès à une configuration de session spécifique limitée aux besoins habituels de l’utilisateur en matière de scripts et de cmdlets. Tapez ce qui suit, puis appuyez sur **Entrée**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - Dans l’exemple suivant, un utilisateur nommé _JSmith_ dans le domaine _Contoso_ se voit accorder un accès pour gérer l’ordinateur _Contoso_214_ et utiliser une configuration de session nommée _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Vérifiez que la règle a été créée en exécutant l’applet de commande **Get-PswaAuthorizationRule** ou `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Par exemple : `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Pour supprimer une règle d’autorisation

1. Si aucune session Windows PowerShell n’est déjà ouverte, consultez l’étape 1 de la procédure [pour ajouter une règle d’autorisation restrictive](#to-add-a-restrictive-authorization-rule) dans cette section.

2. Tapez la commande suivante, puis appuyez sur **Entrée**, où *rule ID* représente l’ID unique de la règle à supprimer.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Si vous ne connaissez pas le numéro de l’ID mais que vous connaissez le nom convivial de la règle à supprimer, vous pouvez obtenir le nom de la règle, puis le faire suivre dans un pipe à l’applet de commande `Remove-PswaAuthorizationRule` pour supprimer la règle, comme dans l’exemple suivant :

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> Vous n’êtes pas invité à confirmer la suppression de la règle d’autorisation spécifiée ; elle est supprimée quand vous appuyez sur **Entrée**. Soyez certain de vouloir supprimer la règle d’autorisation avant d’exécuter l’applet de commande `Remove-PswaAuthorizationRule`.

#### <a name="other-authorization-rule-scenario-examples"></a>Autres exemples de scénarios de règles d’autorisation

Chaque session Windows PowerShell utilise une configuration de session ; si aucune n’est spécifiée pour une session, Windows PowerShell utilise la configuration de session Windows PowerShell prédéfinie par défaut, appelée Microsoft.PowerShell. La configuration de session par défaut inclut toutes les applets de commande disponibles sur un ordinateur. Les administrateurs peuvent limiter l’accès à tous les ordinateurs en définissant une configuration de session avec une instance d’exécution restreinte (une gamme limitée d’applets de commande et de tâches que les utilisateurs finals peuvent effectuer). Un utilisateur auquel est accordé l’accès à un ordinateur avec accès linguistique complet ou uniquement les applets de commande de gestion à distance Windows PowerShell peut se connecter à d’autres ordinateurs qui sont connectés au premier ordinateur. La définition d’une instance d’exécution restreinte peut empêcher les utilisateurs d’accéder à d’autres ordinateurs depuis leur instance d’exécution Windows PowerShell autorisée, et elle renforce la sécurité de votre environnement Accès Web Windows PowerShell. Il est possible de distribuer la configuration de session (à l’aide d’une stratégie de groupe) à tous les ordinateurs que les administrateurs veulent rendre accessibles par le biais d’Accès Web Windows PowerShell. Pour plus d’informations sur les configurations de session, consultez [about_Session_Configurations](/powershell/module/Microsoft.PowerShell.Core/About/about_session_configurations).
Voici quelques exemples de ce scénario.

- Un administrateur crée un point de terminaison, appelé **PswaEndpoint**, avec une instance d’exécution restreinte. Il crée ensuite une règle, `*,*,PswaEndpoint`, et distribue le point de terminaison à d’autres ordinateurs. La règle permet à tous les utilisateurs d’accéder à tous les ordinateurs avec le point de terminaison **PswaEndpoint**.
  Si aucune autre règle d’autorisation n’est définie dans le jeu de règles, les ordinateurs n’ayant pas ce point de terminaison seront inaccessibles.

- L’administrateur a créé un point de terminaison avec une instance d’exécution restreinte appelée **PswaEndpoint**, puis souhaite en restreindre l’accès à des utilisateurs spécifiques. L’administrateur crée un groupe d’utilisateurs appelé **Level1Support**, puis définit la règle suivante : **Level1Support,\*,PswaEndpoint**. La règle accorde à tous les utilisateurs inclus dans le groupe **Level1Support** un accès à tous les ordinateurs dotés de la configuration **PswaEndpoint**. De même, l’accès peut être limité à un ensemble d’ordinateurs spécifique.

- Certains administrateurs accordent à certains utilisateurs un accès privilégié. Par exemple, un administrateur crée deux groupes d’utilisateurs, **Admins** et **BasicSupport**. Il crée également un point de terminaison avec une instance d’exécution restreinte appelée **PswaEndpoint**, puis définit les deux règles suivantes : **Admins,\*,\*** et **BasicSupport,\*,PswaEndpoint**. La première règle octroie à tous les utilisateurs du groupe **Admin** un accès à tous les ordinateurs, et la seconde règle octroie à tous les utilisateurs du groupe **BasicSupport** un accès aux seuls ordinateurs dotés de **PswaEndpoint**.

- Un administrateur a configuré un environnement de test privé et souhaite autoriser tous les utilisateurs réseau approuvés à accéder à tous les ordinateurs du réseau auxquels ils ont normalement accès, avec un accès à toutes les configurations de sessions auxquelles ils ont normalement accès. S’agissant d’un environnement de test privé, l’administrateur crée une règle d’autorisation non sécurisée. - L’administrateur exécute l’applet de commande `Add-PswaAuthorizationRule * * *`, qui utilise le caractère générique **\*** pour représenter tous les utilisateurs, tous les ordinateurs et toutes les configurations. - Cette règle est l’équivalent de la commande suivante : `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Cette règle n’est pas recommandée dans un environnement sécurisé ; elle contourne la couche de sécurité de la règle d’autorisation fournie par Accès Web Windows PowerShell.

- Un administrateur doit autoriser les utilisateurs à se connecter aux ordinateurs cibles dans un environnement qui inclut à la fois des groupes de travail et des domaines, où les ordinateurs des groupes de travail sont de temps en temps utilisés pour se connecter aux ordinateurs cibles dans les domaines et où les ordinateurs des domaines sont de temps en temps utilisés pour se connecter aux ordinateurs cibles dans les groupes de travail. L’administrateur possède un serveur de passerelle, *PswaServer*, dans un groupe de travail et l’ordinateur cible *srv1.contoso.com* se trouve dans un domaine. L’utilisateur *Chris* est un utilisateur local autorisé à la fois sur le serveur de passerelle du groupe de travail et l’ordinateur cible. Son nom d’utilisateur sur le serveur du groupe de travail est *chrisLocal* et son nom d’utilisateur sur l’ordinateur cible est *contoso\\chris*. Pour autoriser l’accès à srv1.contoso.com à Chris, l’administrateur ajoute la règle suivante.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

L’exemple de règle précédent authentifie Chris sur le serveur de passerelle, puis autorise son accès à *srv1*. Dans la page de connexion, Chris doit fournir un deuxième ensemble d’informations d’identification dans la zone **Paramètres de connexion facultatifs** (*contoso\\chris*). Le serveur de passerelle utilise l’ensemble supplémentaire d’informations d’identification pour l’authentifier sur l’ordinateur cible, *srv1.contoso.com*.

Dans le scénario précédent, Accès Web Windows PowerShell établit une connexion correcte à l’ordinateur cible uniquement une fois que les opérations ci-après ont réussi et qu’au moins une règle d’autorisation l’a autorisée.

1. Authentification sur le serveur de passerelle du groupe de travail en ajoutant un nom d’utilisateur au format *nom_serveur*\\*nom_utilisateur* à la règle d’autorisation

2. Authentification sur l’ordinateur cible en utilisant les informations d’identification supplémentaires fournies dans la page de connexion, dans la zone **Paramètres de connexion facultatifs**

   > [!NOTE]
   > Si la passerelle et les ordinateurs cibles se trouvent dans des groupes de travail ou domaines différents, une relation d’approbation doit être établie entre les deux ordinateurs du groupe de travail, les deux domaines ou entre le groupe de travail et le domaine. Il n’est pas possible de configurer cette relation à l’aide des applets de commande des règles d’autorisation d’Accès Web Windows PowerShell. Les règles d’autorisation ne définissent pas une relation d’approbation entre des ordinateurs ; elles peuvent uniquement autoriser les utilisateurs à se connecter à des ordinateurs cibles et configurations de sessions spécifiques. Pour plus d’informations sur la manière de configurer une relation d’approbation entre différents domaines, consultez [Création d’approbations de domaine et de forêt](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794775(v=ws.10)).
   > Pour plus d’informations sur la manière d’ajouter des ordinateurs de groupe de travail à une liste d’hôtes approuvés, consultez [Administration à distance à l’aide du Gestionnaire de serveur](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759202(v=ws.11)).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Utilisation d’un seul jeu de règles d’autorisation pour plusieurs sites

Les règles d’autorisation sont stockées dans un fichier XML. Par défaut, le nom de chemin du fichier XML est `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

Le chemin du fichier XML des règles d’autorisation est stocké dans le fichier **powwa.config**, qui se trouve dans `$env:windir\Web\PowershellWebAccess\data`. L’administrateur peut modifier la référence au chemin par défaut dans **powwa.config** pour satisfaire des préférences ou exigences. Autoriser l’administrateur à modifier l’emplacement du fichier permet à plusieurs passerelles Accès Web Windows PowerShell d’utiliser les mêmes règles d’autorisation, si une telle configuration est souhaitée.

## <a name="session-management"></a>Gestion des sessions

Par défaut, Accès Web Windows PowerShell limite un utilisateur à trois sessions simultanées. Vous pouvez modifier le fichier **web.config** de l’application web dans le Gestionnaire des services Internet afin de prendre en charge un nombre différent de sessions par utilisateur. Le chemin du fichier **web.config** est `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Par défaut, le serveur Web IIS est configuré pour redémarrer le pool d’applications si des paramètres sont modifiés. Par exemple, le pool d’applications est redémarré si des modifications sont apportées au fichier **web.config**. >Dans la mesure où la fonctionnalité **Accès Web Windows PowerShell** utilise les états de session en mémoire, >les utilisateurs connectés à des sessions **Accès Web Windows PowerShell** perdent leurs sessions, une fois que le pool d’applications a redémarré.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Définition de paramètres par défaut sur la page de connexion.

Si votre passerelle Accès Web Windows PowerShell s’exécute sur Windows Server 2012 R2, vous pouvez configurer les valeurs par défaut pour les paramètres affichés dans la page de connexion Accès Web Windows PowerShell. Vous pouvez configurer les valeurs du fichier **web.config** décrit dans le paragraphe précédent. Les valeurs par défaut des paramètres de la page de connexion se trouvent dans la section **appSettings** du fichier web.config ; ce qui suit est un exemple de la section **appSettings**. Les valeurs valides pour la plupart de ces paramètres sont les mêmes que celles des paramètres correspondants de l’applet de commande [New-PSSession](/powershell/module/Microsoft.PowerShell.Core/New-PSSession) dans Windows PowerShell.

Par exemple, la clé `defaultApplicationName`, comme indiqué dans le bloc de code suivant, est la valeur de la variable de préférence **$PSSessionApplicationName** sur l’ordinateur cible.

```xml
  <appSettings>
      <add key="maxSessionsAllowedPerUser" value="3"/>
      <add key="defaultPortNumber" value="5985"/>
      <add key="defaultSSLPortNumber" value="5986"/>
      <add key="defaultApplicationName" value="WSMAN"/>
      <add key="defaultUseSslSelection" value="0"/>
      <add key="defaultAuthenticationType" value="0"/>
      <add key="defaultAllowRedirection" value="0"/>
      <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
  </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Expirations de délais et déconnexions non planifiées

Les sessions Accès Web Windows PowerShell expirent. Dans Accès Web Windows PowerShell sur Windows Server 2012, un message d’expiration de délai est affiché après 15 minutes d’inactivité de session. Si l’utilisateur ne répond pas dans les cinq minutes qui suivent l’affichage du message, la session est interrompue et l’utilisateur est déconnecté. Vous pouvez modifier les délais d’expiration des sessions dans les paramètres de site web, dans le Gestionnaire des services Internet.

Dans Accès Web Windows PowerShell sur Windows Server 2012 R2, les sessions expirent par défaut après 20 minutes d’inactivité. Si les utilisateurs sont déconnectés de sessions de la console web en raison d’erreurs réseau ou d’autres défaillances ou arrêts non planifiés, et non parce qu’ils ont eux-mêmes fermé les sessions, les sessions Accès Web Windows PowerShell continuent de s’exécuter, connectées aux ordinateurs cibles, jusqu’à ce que le délai d’expiration côté client soit écoulé. La session est déconnectée après les 20 minutes définies par défaut, ou au terme du délai spécifié par l’administrateur de la passerelle, le délai le plus court étant appliqué.

Si le serveur de passerelle exécute Windows Server 2012 R2, Accès Web Windows PowerShell permet aux utilisateurs de se reconnecter ultérieurement aux sessions enregistrées. Toutefois, quand des erreurs de réseau, des arrêts non planifiés ou d’autres défaillances provoquent la déconnexion des sessions, les utilisateurs ne peuvent pas accéder aux sessions enregistrées ou s’y reconnecter, tant que le délai d’expiration spécifié par l’administrateur de la passerelle n’est pas écoulé.

## <a name="see-also"></a>Voir aussi

[Installer et utiliser Accès Web Windows PowerShell](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831611(v=ws.11))

[about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_Session_Configurations)

[Applets de commande d’Accès Web Windows PowerShell](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
