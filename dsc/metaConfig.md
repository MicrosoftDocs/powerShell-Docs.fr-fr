---
ms.date: 10/11/2017
keywords: dsc,powershell,configuration,setup
title: Configuration du Gestionnaire de configuration local
ms.openlocfilehash: 924abe12aa865989e83c975b599b3b65ddd45655
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="configuring-the-local-configuration-manager"></a>Configuration du Gestionnaire de configuration local

> S’applique à : Windows PowerShell 5.0

Le Gestionnaire de configuration local est le moteur de la fonctionnalité DSC (Desired State Configuration).
Le LCM s’exécute sur chaque nœud cible pour analyser et appliquer les configurations transmises au nœud.
Il a également en charge plusieurs autres opérations liées à DSC, notamment les suivantes.

- Déterminer le mode d’actualisation (push ou pull).
- Spécifier la fréquence à laquelle un nœud extrait et applique les configurations.
- Associer le nœud à un service d’extraction.
- Spécifier des configurations partielles.

Un type spécial de configuration vous permet de configurer le LCM pour définir chacun de ces comportements.
Les sections qui suivent décrivent comment configurer le LCM.

Windows PowerShell 5.0 a introduit de nouveaux paramètres permettant de gérer le Gestionnaire de configuration local.
Pour plus d’informations sur la configuration du Gestionnaire de configuration local dans Windows PowerShell 4.0, consultez [Configuration du Gestionnaire de configuration local dans les versions précédentes de Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Création et application d’une configuration du LCM

Pour configurer le LCM, vous devez créer et exécuter un type spécial de configuration appliquant les paramètres du LCM.
Pour spécifier une configuration du LCM, utilisez l’attribut DscLocalConfigurationManager.
L’exemple ci-dessous montre une configuration simple qui définit le LCM en mode par envoi.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

Le processus d’application des paramètres au Gestionnaire de configuration local est similaire à l’application d’une configuration DSC.
Vous allez créer une configuration du LCM, la compiler dans un fichier MOF, puis l’appliquer au nœud.
À la différence des configurations DSC, vous n’appliquez pas de configuration du gestionnaire de configuration local en appelant l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).
Au lieu de cela, vous appelez [DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) en spécifiant le chemin du fichier MOF de configuration du LCM comme paramètre.
Après avoir appliqué la configuration du LCM, vous pouvez afficher ses propriétés en appelant l’applet de commande [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).

Une configuration du LCM peut contenir des blocs pour un ensemble limité de ressources uniquement.
Dans l’exemple précédent, **Settings** est la seule ressource appelée.
Voici les autres ressources disponibles :

* **ConfigurationRepositoryWeb** : spécifie un service d’extraction HTTP pour les configurations.
* **ConfigurationRepositoryShare** : spécifie un partage SMB pour les configurations.
* **ResourceRepositoryWeb** : spécifie un service d’extraction HTTP pour les modules.
* **ResourceRepositoryShare** : spécifie un partage SMB pour les modules.
* **ReportServerWeb** : spécifie un service d’extraction HTTP auquel les rapports sont envoyés.
* **PartialConfiguration** : fournit des données pour activer des configurations partielles.

## <a name="basic-settings"></a>Paramètres de base

À la différence de la spécification de points de terminaison/de chemins et de configurations partielles du service d’extraction, toutes les propriétés du Gestionnaire de configuration local sont configurées dans un bloc **Paramètres**.
Un bloc **Settings** définit les propriétés suivantes.

|  Propriété  |  Type  |  Description   |
|----------- |------- |--------------- |
| ActionAfterReboot| string| Spécifie le comportement après un redémarrage survenant pendant l’application d’une configuration. Les valeurs possibles sont __ContinueConfiguration__ et __StopConfiguration__. <ul><li> Avec la valeur __ContinueConfiguration__, l’application de la configuration actuelle se poursuit après le redémarrage de l’ordinateur. Il s’agit de la valeur par défaut</li><li>Avec la valeur __StopConfiguration__, l’application de la configuration actuelle s’arrête après le redémarrage de l’ordinateur.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ si de nouvelles configurations téléchargées dans le service d’extraction sont autorisées à remplacer les anciennes sur le nœud cible. Autrement, définissez-la sur $FALSE.|
| CertificateID| string| Empreinte d’un certificat utilisée pour sécuriser les informations d’identification transmise dans une configuration. Pour plus d’informations, consultez [Want to secure credentials in Windows PowerShell Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)? (Sécuriser les informations d’identification dans DSC Windows PowerShell). <br> __Remarque :__ ceci est géré automatiquement si vous utilisez le service d’extraction Azure Automation DSC.|
| ConfigurationDownloadManagers| CimInstance[]| Obsolète. Utilisez les blocs __ConfigurationRepositoryWeb__ et __ConfigurationRepositoryShare__ pour définir les points de terminaison du service d’extraction de configuration.|
| ConfigurationID| string| Pour la rétrocompatibilité avec des versions plus anciennes du service d’extraction. Un GUID qui identifie le fichier de configuration à obtenir d’un service d’extraction. Le nœud extrait les configurations du service d’extraction si le nom du fichier de configuration MOF est ConfigurationID.mof.<br> __Remarque__ : si vous définissez cette propriété, l’enregistrement du nœud auprès d’un service d’extraction avec __RegistrationKey__ ne fonctionne pas. Pour plus d’informations, consultez [Configuration d’un client collecteur à l’aide des noms de configuration](pullClientConfigNames.md).|
| ConfigurationMode| string | Spécifie de quelle façon le LCM applique réellement la configuration aux nœuds cibles. Les valeurs possibles sont __"ApplyOnly"__,__"ApplyAndMonitor"__ et __"ApplyAndAutoCorrect"__. <ul><li>La valeur __ApplyOnly__ indique à DSC d’appliquer la configuration et de ne faire aucune autre opération, sauf si une nouvelle configuration est transmise au nœud cible ou est extraite d’un service. Après l’application initiale d’une nouvelle configuration, DSC ne vérifie pas si le nœud cible est encore dans l’état précédemment configuré. Notez que DSC tente d’appliquer la configuration jusqu’à ce que l’opération aboutisse avant que __ApplyOnly__ ne prenne effet. </li><li> La valeur __ApplyAndMonitor__ est la valeur par défaut. indique au LCM d’appliquer chaque nouvelle configuration. Après l’application initiale d’une nouvelle configuration, DSC vérifie si le nœud cible est dans l’état souhaité et, si ce n’est pas le cas, signale l’écart dans les journaux. Notez que DSC tente d’appliquer la configuration jusqu’à ce que l’opération aboutisse avant que __ApplyAndMonitor__ ne prenne effet.</li><li>La valeur __ApplyAndAutoCorrect__ indique à DSC d’appliquer chaque nouvelle configuration. Après l’application initiale d’une nouvelle configuration, DSC vérifie si le nœud cible est dans l’état souhaité et, si ce n’est pas le cas, il signale l’écart dans les journaux, puis il réapplique la configuration actuelle.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Fréquence, en minutes, à laquelle la configuration actuelle est vérifiée et appliquée. Cette propriété est ignorée si la propriété ConfigurationMode est définie sur ApplyOnly. La valeur par défaut est 15.|
| DebugMode| string| Les valeurs possibles sont __None__, __ForceModuleImport__ et __All__. <ul><li>Définissez cette propriété sur __None__ pour utiliser les ressources mises en cache. Il s’agit de la valeur par défaut qui doit être utilisée dans les scénarios de production.</li><li>Définissez cette propriété sur __ForceModuleImport__ pour forcer le gestionnaire de configuration local à recharger tous les modules de ressources DSC, même ceux ayant déjà été chargés et mis en cache. Ce comportement diminue les performances de DSC, car chaque module utilisé est systématiquement rechargé. En général, vous utilisez cette valeur lors du débogage d’une ressource.</li><li>Dans cette version, __All__ est équivalent à __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| bool| Définissez cette propriété sur __$true__ pour redémarrer automatiquement le nœud après l’application d’une configuration nécessitant un redémarrage. Sinon, vous devez redémarrer manuellement le nœud. La valeur par défaut est __$false__. Pour utiliser ce paramètre lorsqu’une condition de redémarrage est imposée par autre chose que DSC (par exemple Windows Installer), combinez ce paramètre avec le module [xPendingReboot](https://github.com/powershell/xpendingreboot).|
| RefreshMode| string| Spécifie de quelle façon le LCM obtient les configurations. Les valeurs possibles sont __Disabled__, __Push__ et __Pull__. <ul><li>La valeur __Disabled__ désactive les configurations DSC pour ce nœud.</li><li> La valeur __Push__ lance les configurations en appelant l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). Chaque configuration est immédiatement appliquée au nœud. Il s'agit de la valeur par défaut.</li><li>__Pull__ : le nœud est configuré pour vérifier régulièrement les configurations disponibles sur un service d’extraction ou un chemin SMB. Si cette propriété a la valeur __Pull__, vous devez spécifier un chemin HTTP (service) ou SMB (partage) dans un bloc __ConfigurationRepositoryWeb__ ou __ConfigurationRepositoryShare__.</li></ul>|
| RefreshFrequencyMins| Uint32| L’intervalle de temps, en minutes, auquel le LCM contrôle un service d’extraction pour obtenir des configurations mises à jour. Cette valeur est ignorée si le LCM n’est pas configuré en mode d’extraction. La valeur par défaut est 30.|
| ReportManagers| CimInstance[]| Obsolète. Utilisez des blocs __ReportServerWeb__ pour définir un point de terminaison permettant d’envoyer les données de rapport à un service d’extraction.|
| ResourceModuleManagers| CimInstance[]| Obsolète. Utilisez des blocs __ResourceRepositoryWeb__ et __ResourceRepositoryShare__ pour définir respectivement les points de terminaison HTTP ou les chemins SMB du service d’extraction.|
| PartialConfigurations| CimInstance| Non implémentée. Ne pas utiliser.|
| StatusRetentionTimeInDays | UInt32| Nombre de jours pendant lesquels le LCM conserve l’état de la configuration actuelle.|

## <a name="pull-service"></a>Service d’extraction

La configuration du LCM permet de définir les types de services d’extraction suivants :

- **Serveur de configuration** : référentiel pour les configurations DSC. Définissez les serveurs de configuration à l’aide des blocs **ConfigurationRepositoryWeb** (pour les serveurs web) et **ConfigurationRepositoryShare** (pour les serveurs SMB).
- **Serveur de ressources** : référentiel pour les ressources DSC, packagées comme modules PowerShell. Définissez les serveurs de ressources à l’aide des blocs **ResourceRepositoryWeb** (pour les serveurs web) et **ResourceRepositoryShare** (pour les serveurs SMB).
- **Serveur de rapports** : service vers lequel DSC envoie les données de rapports. Définissez les serveurs de rapports à l’aide des blocs **ReportServerWeb**. Un serveur de rapports doit être un service web.

Pour plus d’informations sur le service collecteur, consultez [Service collecteur Desired State Configuration](pullServer.md).

## <a name="configuration-server-blocks"></a>Blocs de serveur de configuration

Pour définir un serveur de configuration web, créez un bloc **ConfigurationRepositoryWeb**.
Un bloc **ConfigurationRepositoryWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|AllowUnsecureConnection|bool|Définissez cette propriété sur **$TRUE** pour autoriser le nœud à se connecter au serveur sans authentification. Définissez-la sur **$FALSE** pour rendre l’authentification obligatoire.|
|CertificateID|string|Empreinte d’un certificat utilisée pour l’authentification auprès du serveur.|
|ConfigurationNames|String[]|Tableau des noms des configurations à extraire par le nœud cible. Ils sont utilisés uniquement si le nœud est enregistré auprès du service d’extraction à l’aide d’une propriété **RegistrationKey**. Pour plus d’informations, consultez [Configuration d’un client collecteur à l’aide des noms de configuration](pullClientConfigNames.md).|
|RegistrationKey|string|Un GUID sous lequel le nœud est enregistré auprès du service d’extraction. Pour plus d’informations, consultez [Configuration d’un client collecteur à l’aide des noms de configuration](pullClientConfigNames.md).|
|ServerURL|string|L’URL du service de configuration.|

Un exemple de script pour simplifier la valeur ConfigurationRepositoryWeb pour des nœuds locaux est disponible – consultez [Génération de configurations DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Pour définir un serveur de configuration SMB, créez un bloc **ConfigurationRepositoryShare**.
Un bloc **ConfigurationRepositoryShare** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|Credential|MSFT_Credential|Informations d’identification utilisées pour l’authentification auprès du partage SMB.|
|SourcePath|string|Chemin du partage SMB.|

## <a name="resource-server-blocks"></a>Blocs de serveur de ressources

Pour définir un serveur de ressources web, créez un bloc **ResourceRepositoryWeb**.
Un bloc **ResourceRepositoryWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|AllowUnsecureConnection|bool|Définissez cette propriété sur **$TRUE** pour autoriser le nœud à se connecter au serveur sans authentification. Définissez-la sur **$FALSE** pour rendre l’authentification obligatoire.|
|CertificateID|string|Empreinte d’un certificat utilisée pour l’authentification auprès du serveur.|
|RegistrationKey|string|Un GUID qui identifie le nœud inscrit auprès du service d’extraction.|
|ServerURL|string|URL du serveur de configuration.|

Un exemple de script pour simplifier la configuration de la valeur ConfigurationRepositoryWeb pour des nœuds locaux est disponible – consultez [Génération de métaconfigurations DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Pour définir un serveur de ressources SMB, créez un bloc **ResourceRepositoryShare**.
Un bloc **ResourceRepositoryShare** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|Credential|MSFT_Credential|Informations d’identification utilisées pour l’authentification auprès du partage SMB. Pour obtenir un exemple de transmission d’informations d’identification, consultez [Configuration d’un serveur d’extraction SMB DSC](pullServerSMB.md)|
|SourcePath|string|Chemin du partage SMB.|

## <a name="report-server-blocks"></a>Blocs de serveur de rapports

Pour définir un serveur de rapports, créez un bloc **ReportServerWeb**.
Le rôle de serveur de rapports n’est pas compatible avec le service d’extraction basé sur SMB.
Un bloc **ReportServerWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|AllowUnsecureConnection|bool|Définissez cette propriété sur **$TRUE** pour autoriser le nœud à se connecter au serveur sans authentification. Définissez-la sur **$FALSE** pour rendre l’authentification obligatoire.|
|CertificateID|string|Empreinte d’un certificat utilisée pour l’authentification auprès du serveur.|
|RegistrationKey|string|Un GUID qui identifie le nœud inscrit auprès du service d’extraction.|
|ServerURL|string|URL du serveur de configuration.|

Un exemple de script pour simplifier la configuration de la valeur ReportServerWeb pour des nœuds locaux est disponible – consultez [Génération de métaconfigurations DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Configurations partielles

Pour définir une configuration partielle, créez un bloc **PartialConfiguration**.
Pour plus d’informations sur les configurations partielles, consultez [Configurations partielles DSC](partialConfigs.md).
Un bloc **PartialConfiguration** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|ConfigurationSource|string[]|Tableau des noms des serveurs de configuration, définis précédemment dans les blocs **ConfigurationRepositoryWeb** et **ConfigurationRepositoryShare**, à partir desquels la configuration partielle est extraite.|
|DependsOn|string{}|Liste des noms des autres configurations à exécuter avant l’application de cette configuration partielle.|
|Description|string|Texte qui décrit la configuration partielle.|
|ExclusiveResources|string[]|Tableau des ressources exclusives de cette configuration partielle.|
|RefreshMode|string|Spécifie de quelle façon le gestionnaire de configuration local obtient cette configuration partielle. Les valeurs possibles sont __Disabled__, __Push__ et __Pull__. <ul><li>La valeur __Disabled__ désactive cette configuration partielle.</li><li> __Push__ : la configuration partielle est transmise au nœud en appelant l’applet de commande [Publish-DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx). Une fois que toutes les configurations partielles pour le nœud ont été obtenues d’un service en mode push ou pull, la configuration peut être démarrée en appelant `Start-DscConfiguration –UseExisting`. Il s'agit de la valeur par défaut.</li><li>La valeur __Pull__ configure le nœud pour vérifier régulièrement si la configuration partielle est disponible sur un service d’extraction. Si cette propriété a la valeur __Pull__, vous devez spécifier un service d’extraction dans une propriété __ConfigurationSource__. Pour plus d’informations sur le service d’extraction Azure Automation, consultez [Vue d’ensemble d’Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|Tableau des noms des serveurs de ressources à partir desquels télécharger les ressources nécessaires pour cette configuration partielle. Ces noms doivent être ceux des points de terminaison du service définis précédemment dans les blocs **ResourceRepositoryWeb** et **ResourceRepositoryShare**.|

__Remarque :__ les configurations partielles sont prises en charge avec Azure Automation DSC, mais une seule configuration peut être extraite du compte Automation de chaque nœud.

## <a name="see-also"></a>Voir aussi

### <a name="concepts"></a>Concepts
[Vue d’ensemble de la configuration d'état souhaité](overview.md)

[Bien démarrer avec Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Autres ressources

[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)

[Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)