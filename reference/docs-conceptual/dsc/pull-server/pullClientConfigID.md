---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Configurer un client Pull à l’aide d’ID de configuration dans PowerShell 5.0 et ultérieur
description: Cet article explique comment configurer un client Pull à l’aide d’ID de configuration dans PowerShell 5.0 et ultérieur
ms.openlocfilehash: 601858c08ce9a893a8941823d27fef3a60882b48
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664310"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configurer un client Pull à l’aide d’ID de configuration dans PowerShell 5.0 et ultérieur

> S’applique à : Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC* ) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

Avant de configurer un client Pull, vous devez configurer un serveur Pull. Bien que cet ordre ne soit pas obligatoire, il facilite le dépannage et vous permet de vous assurer que l’inscription a réussi. Pour configurer un serveur Pull, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état. Les sections suivantes montrent comment configurer un client Pull avec un partage SMB ou un serveur Pull DSC HTTP. Quand le Gestionnaire de configuration local du nœud est actualisé, il contacte l’emplacement configuré pour télécharger toutes les configurations affectées. Si des ressources requises n’existent pas sur le nœud, il les télécharge automatiquement à partir de l’emplacement configuré. Si le nœud est configuré avec un [serveur de rapports](reportServer.md), il signale ensuite l’état de l’opération.

> [!NOTE]
> Cette rubrique s’applique à PowerShell 5.0. Pour des informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurer le Gestionnaire de configuration local du client Pull

L’exécution de l’un des exemples ci-dessous crée un dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration. Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.

Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration. Exemple :

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID de configuration

Les exemples ci-dessous affectent à la propriété **ConfigurationID** du Gestionnaire de configuration local un **GUID** précédemment créé à cet effet. Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur. Le fichier MOF de configuration sur le serveur collecteur doit être nommé `ConfigurationID.mof`, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible. Pour plus d’informations, consultez [Publier des configurations vers un serveur Pull (v4/v5)](publishConfigs.md).

Vous pouvez créer un **GUID** aléatoire à l’aide de l’exemple ci-dessous, ou en utilisant l’applet de commande [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).

```powershell
[System.Guid]::NewGuid()
```

Pour plus d’informations sur l’utilisation des **GUID** dans votre environnement, consultez [Planifier les GUID](secureserver.md#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurer un client Pull pour télécharger des configurations

Chaque client doit être configuré en mode **Pull** et il faut lui fournir l’URL du serveur Pull où sa configuration est stockée. Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires. Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration que vous décorez avec l’attribut **DSCLocalConfigurationManager**. Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Serveur Pull DSC HTTP

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

Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur. **ServerUrl** spécifie l’URL de l’extraction DSC

### <a name="smb-share"></a>Partage SMB

Le script suivant configure le Gestionnaire de configuration local de façon à extraire des configurations du partage SMB `\\SMBPullServer\Pull`.

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

Dans le script, le bloc **ConfigurationRepositoryShare** définit le serveur Pull, qui dans le cas présent est simplement un partage SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurer un client Pull pour télécharger des ressources

Si vous spécifiez uniquement un bloc **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** dans votre configuration du Gestionnaire de configuration local (comme dans les exemples précédents), le client Pull extrait les ressources à partir du même emplacement que celui où il récupère ses configurations. Vous pouvez également spécifier des emplacements distincts pour les ressources. Pour spécifier un emplacement de ressources en tant que serveur distinct, utilisez le bloc **ResourceRepositoryWeb**. Pour spécifier un emplacement de ressources en tant que partage SMB, utilisez le bloc **ResourceRepositoryShare**.

> [!NOTE]
> Vous pouvez combiner **ConfigurationRepositoryWeb** avec **ResourceRepositoryShare** , ou **ConfigurationRepositoryShare** avec **ResourceRepositoryWeb**. Aucun exemple de ce type de combinaison n’est fourni ci-dessous.

### <a name="http-dsc-pull-server"></a>Serveur Pull DSC HTTP

La métaconfiguration suivante configure un client Pull pour qu’il obtienne sa configuration à partir de **CONTOSO-PullSrv** et ses ressources à partir de **CONTOSO-ResourceSrv**.

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

L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations à partir du partage SMB `\\SMBPullServer\Configurations` et les ressources à partir du partage SMB `\\SMBPullServer\Resources`.

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

#### <a name="automatically-download-resources-in-push-mode"></a>Télécharger automatiquement les ressources en mode Push

À compter de PowerShell 5.0, vos clients Pull peuvent télécharger des modules à partir d’un partage SMB, même quand ils sont configurés pour le mode **Push**. C’est particulièrement utile dans les scénarios où vous ne souhaitez pas configurer de serveur Pull. Le bloc **ResourceRepositoryShare** peut être utilisé sans spécifier de **ConfigurationRepositoryShare**. L’exemple suivant montre une métaconfiguration qui configure un client pour extraire des ressources à partir d’un partage SMB `\\SMBPullServer\Resources`. Quand une configuration est fournie au nœud par le biais d’une opération **PUSH** , il télécharge automatiquement toutes les ressources requises à partir du partage spécifié.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Configurer un client Pull pour signaler l’état

Par défaut, les nœuds n’envoient pas de rapports à un serveur Pull configuré. Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports, mais vous devez créer un bloc **ReportRepositoryWeb** pour configurer les rapports.

### <a name="http-dsc-pull-server"></a>Serveur Pull DSC HTTP

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

Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb**. Un serveur de rapports ne peut pas être un serveur SMB. La métaconfiguration suivante configure un client collecteur de façon à obtenir sa configuration de **CONTOSO-PullSrv** et ses ressources de **CONTOSO-ResourceSrv** , et à envoyer des rapports d’état à **CONTOSO-ReportSrv** :

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

Une fois le client Pull configuré, vous pouvez utiliser les guides suivants pour effectuer les étapes suivantes :

- [Publier des configurations vers un serveur Pull (v4/v5)](publishConfigs.md)
- [Empaqueter et charger des ressources dans un serveur Pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Voir aussi

- [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)
