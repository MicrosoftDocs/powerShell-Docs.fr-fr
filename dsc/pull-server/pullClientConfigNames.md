---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configurer un Client collecteur à l’aide de noms de Configuration dans PowerShell 5.0 et versions ultérieures
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679148"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Configurer un Client collecteur à l’aide de noms de Configuration dans PowerShell 5.0 et versions ultérieures

> S’applique à : Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

Avant de configurer un client collecteur, vous devez configurer un serveur collecteur. Bien que cette commande ne soit pas obligatoire, elle facilite le dépannage et vous permet de vous assurer que l’inscription a réussi. Pour configurer un serveur collecteur, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état. Les sections suivantes vous montrent comment configurer un client collecteur avec un partage SMB ou un serveur d’extraction DSC HTTP. Lorsque Gestionnaire de configuration local du nœud est actualisé, il vous recontacte pour l’emplacement configuré pour télécharger toutes les configurations sont affectées. Si toutes les ressources requises n’existent pas sur le nœud, il les télécharge automatiquement à partir de l’emplacement configuré. Si le nœud est configuré avec un [serveur de rapports](reportServer.md), il sera ensuite l’état de l’opération.

> **Remarque** : Cette rubrique s’applique à PowerShell 5.0.
Pour plus d’informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [configurer un client collecteur à l’aide des ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurer le client d’extraction LCM

L’exécution d’un des exemples ci-dessous crée un nouveau dossier de sortie nommé **PullClientConfigName** et y place un fichier MOF de métaconfiguration. Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.

Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration. Par exemple :

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nom de la configuration

Les exemples ci-dessous définit les **ConfigurationName** propriété du Gestionnaire de configuration local pour le nom d’une Configuration précédemment compilée, créé à cet effet. Le **ConfigurationName** est ce que le Gestionnaire de configuration local utilise pour rechercher la configuration appropriée sur le serveur collecteur. Le fichier MOF de configuration sur le serveur collecteur doit être nommé `<ConfigurationName>.mof`, dans ce cas, « ClientConfig.mof ». Pour plus d’informations, consultez [publier les Configurations à un serveur collecteur (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurer un Client collecteur à télécharger les Configurations

Chaque client doit être configuré dans **extraction** mode et l’url du serveur collecteur où sa configuration est stockée. Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires. Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration que vous décorez avec l’attribut **DSCLocalConfigurationManager**. Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig.md).

Le script suivant configure le gestionnaire de configuration local pour extraire les configurations d’un serveur nommé « CONTOSO-PullSrv ».

- Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur. La propriété **ServerURL** spécifie le point de terminaison pour le serveur collecteur.

- La propriété **RegistrationKey** est une clé partagée entre tous les nœuds clients d’un serveur collecteur et ce serveur collecteur. La même valeur est stockée dans un fichier sur le serveur collecteur.
  > **Remarque** : Clés d’enregistrement fonctionnent uniquement avec **web** serveurs collecteurs. Vous devez encore utiliser **ConfigurationID** avec un serveur Pull **SMB**.
  > Pour plus d’informations sur la configuration d’un serveur collecteur à l’aide de **ConfigurationID**, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigId.md)

- La propriété **ConfigurationNames** est un tableau qui spécifie les noms des configurations destinées au nœud client.
  >**Remarque :** Si vous spécifiez plusieurs valeurs dans **ConfigurationNames**, vous devez également spécifier des blocs **PartialConfiguration** dans votre configuration.
  >Pour plus d’informations sur les configurations partielles, voir [Configurations partielles du service de configuration d’état souhaité PowerShell](partialConfigs.md).

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurer un Client collecteur pour télécharger des ressources

Si vous spécifiez uniquement un **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquer dans votre configuration du LCM (comme dans l’exemple précédent), le client d’extraction extraira les ressources du même emplacement où sont stockés vos fichiers « .mof ». Vous pouvez également spécifier différents emplacements où les clients peuvent télécharger des ressources. Pour spécifier un serveur de ressources, vous utilisez un bloc **ResourceRepositoryWeb** (pour un serveur collecteur web) ou **ResourceRepositoryShare** (pour un serveur collecteur SMB).

L’exemple suivant montre une métaconfiguration qui configure un client à télécharger les configurations à partir d’un serveur collecteur et les ressources à partir d’un partage SMB.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurer un Client collecteur pour signaler l’état

Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports. Création de rapports n’est pas configurée pour les clients par défaut. Pour configurer un client pour signaler l’état, vous devez créer un **ReportRepositoryWeb** bloc. L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations et les ressources, et à envoyer des données de rapport à un seul serveur collecteur.

> [!NOTE]
> Un serveur de rapports ne peut pas être un partage SMB.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Voir aussi

* [Configuration d’un client collecteur à l’aide de l’ID de configuration](PullClientConfigNames.md)
* [Configuration d’un serveur collecteur web DSC](pullServer.md)
