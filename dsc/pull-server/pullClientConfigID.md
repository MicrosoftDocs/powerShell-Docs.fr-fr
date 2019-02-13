---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurer un Client collecteur à l’aide des ID de Configuration dans PowerShell 5.0 et versions ultérieures
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678405"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configurer un Client collecteur à l’aide des ID de Configuration dans PowerShell 5.0 et versions ultérieures

> S’applique à : Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

Avant de configurer un client collecteur, vous devez configurer un serveur collecteur. Bien que cette commande ne soit pas obligatoire, elle facilite le dépannage et vous permet de vous assurer que l’inscription a réussi. Pour configurer un serveur collecteur, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état. Les sections suivantes vous montrent comment configurer un client collecteur avec un partage SMB ou un serveur d’extraction DSC HTTP. Lorsque Gestionnaire de configuration local du nœud est actualisé, il vous recontacte pour l’emplacement configuré pour télécharger toutes les configurations sont affectées. Si toutes les ressources requises n’existent pas sur le nœud, il les télécharge automatiquement à partir de l’emplacement configuré. Si le nœud est configuré avec un [serveur de rapports](reportServer.md), il sera ensuite l’état de l’opération.

> **Remarque** : Cette rubrique s’applique à PowerShell 5.0. Pour des informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurer le client d’extraction LCM

L’exécution d’un des exemples ci-dessous crée un nouveau dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration. Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.

Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration. Par exemple :

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID de configuration

Les exemples ci-dessous définit les **ConfigurationID** propriété du Gestionnaire de configuration local à un **Guid** qui avait été précédemment créé à cet effet. Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur. Le fichier MOF de configuration sur le serveur collecteur doit être nommé `ConfigurationID.mof`, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible. Pour plus d’informations, consultez [publier les Configurations à un serveur collecteur (v4/v5)](publishConfigs.md).

Vous pouvez créer un aléatoire **Guid** à l’aide de l’exemple ci-dessous, ou en utilisant le [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) applet de commande.

```powershell
[System.Guid]::NewGuid()
```

Pour plus d’informations sur l’utilisation de **GUID** dans votre environnement, consultez [planifier GUID](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurer un Client collecteur à télécharger les Configurations

Chaque client doit être configuré dans **extraction** mode et l’url du serveur collecteur où sa configuration est stockée. Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires. Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration que vous décorez avec l’attribut **DSCLocalConfigurationManager**. Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Serveur collecteur de DSC HTTP

Le script suivant configure le gestionnaire de configuration local pour extraire les configurations d’un serveur nommé « CONTOSO-PullSrv ».

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur. Le **ServerUrl** Spécifie l’url de l’extraction de DSC

### <a name="smb-share"></a>Partage SMB

Le script suivant configure le LCM à extraire des configurations à partir du partage SMB `\\SMBPullServer\Pull`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

Dans le script, le **ConfigurationRepositoryShare** bloc définit le serveur collecteur, qui dans ce cas, est simplement un partage SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurer un Client collecteur pour télécharger des ressources

Si vous spécifiez uniquement le **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquer dans votre configuration du LCM (comme dans les exemples précédents), le client d’extraction extraira les ressources de la même emplacement il récupère sa configuration. Vous pouvez également spécifier des emplacements distincts pour les ressources. Pour spécifier un emplacement de ressources comme un serveur distinct, utilisez le **ResourceRepositoryWeb** bloc. Pour spécifier un emplacement de ressources comme un partage SMB, utilisez le **ResourceRepositoryShare** bloc.

> [!NOTE]
> Vous pouvez combiner **ConfigurationRepositoryWeb** avec **ResourceRepositoryShare** ou **ConfigurationRepositoryShare** avec **ResourceRepositoryWeb** . Exemples de ce ne sont pas affichés ci-dessous.

### <a name="http-dsc-pull-server"></a>Serveur collecteur de DSC HTTP

La métaconfiguration suivante configure un client collecteur pour obtenir sa configuration de **CONTOSO-PullSrv** et ses ressources de **CONTOSO-ResourceSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Partage SMB

L’exemple suivant montre une métaconfiguration qui configure un client à extraire des configurations à partir du partage SMB `\\SMBPullServer\Configurations`et les ressources à partir du partage SMB `\\SMBPullServer\Resources`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Télécharger automatiquement les ressources en Mode Push

À compter de PowerShell 5.0, vos clients d’extraction peuvent télécharger modules à partir d’un partage SMB, même lorsqu’elles sont configurées pour **Push** mode. Cela est particulièrement utile dans les scénarios où vous ne souhaitez pas configurer un serveur collecteur. Le **ResourceRepositoryShare** bloc peut être utilisé sans spécifier un **ConfigurationRepositoryShare**. L’exemple suivant montre une métaconfiguration qui configure un client pour extraire des ressources à partir d’un partage SMB `\\SMBPullServer\Resources`. Lorsque le nœud est **PUSHED** une configuration, il télécharge automatiquement toutes les ressources requises, à partir du partage spécifié.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurer un Client collecteur pour signaler l’état

Par défaut, nœuds ne seront pas envoyer des rapports à un serveur collecteur configuré. Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports, mais vous devez créer un bloc **ReportRepositoryWeb** pour configurer les rapports.

### <a name="http-dsc-pull-server"></a>Serveur collecteur de DSC HTTP

L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations et les ressources, et à envoyer des données de rapport à un seul serveur collecteur.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb**. Un serveur de rapports ne peut pas être un serveur SMB.
La métaconfiguration suivante configure un client collecteur de façon à obtenir sa configuration de **CONTOSO-PullSrv** et ses ressources de **CONTOSO-ResourceSrv**, et à envoyer des rapports d’état à **CONTOSO-ReportSrv** :

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Partage SMB

Un serveur de rapports ne peut pas être un partage SMB.

## <a name="next-steps"></a>Étapes suivantes

Une fois que le client d’extraction a été configuré, vous pouvez utiliser les guides suivants pour effectuer les étapes suivantes :

- [Publier des configurations vers un serveur Pull (v4/v5)](publishConfigs.md)
- [Empaqueter et charger des ressources vers un serveur Pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Voir aussi

* [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)
