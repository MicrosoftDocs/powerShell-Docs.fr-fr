---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuration d’un client collecteur à l’aide de l’ID de configuration
ms.openlocfilehash: b4a45c4d014b3c4fc0140ad492f81474b260065a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187491"
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a>Configuration d’un client collecteur à l’aide de l’ID de configuration

> S’applique à : Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL où contacter le serveur collecteur pour obtenir des configurations. Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires. Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration que vous décorez avec l’attribut **DSCLocalConfigurationManager**. Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](metaConfig.md).

> **Remarque** : Cette rubrique s’applique à PowerShell 5.0. Pour des informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)

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

Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur. Paramètre **ServerURL**

Quand le script s’exécute, il crée un dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration. Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.

Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration. Par exemple : `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## <a name="configuration-id"></a>ID de configuration

Le script définit la propriété **ConfigurationID** du gestionnaire de configuration local sur un GUID déjà créé à cet effet (vous pouvez créer un GUID à l’aide de l’applet de commande **New-Guid**). Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur. Le fichier MOF de configuration sur le serveur collecteur doit être nommé _ConfigurationID_.mof, où _ConfigurationID_ est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.

## <a name="smb-pull-server"></a>Serveur collecteur SMB

Pour configurer un client de façon à extraire des configurations d’un serveur SMB, utilisez un bloc **ConfigurationRepositoryShare**. Dans un bloc **ConfigurationRepositoryShare**, vous spécifiez le chemin du serveur en définissant la propriété **SourcePath**. La métaconfiguration suivante configure le nœud cible de façon à extraire des configurations d’un serveur collecteur SMB nommé **SMBPullServer**.

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
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a>Serveurs de ressources et de rapports

Si vous spécifiez uniquement un bloc **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** dans votre configuration du gestionnaire de configuration local (comme dans l’exemple précédent), le client collecteur extrait des ressources du serveur spécifié, mais il ne lui envoie pas de rapport. Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports, mais vous devez créer un bloc **ReportRepositoryWeb** pour configurer les rapports.

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

Vous pouvez également spécifier différents serveurs collecteurs pour les ressources et les rapports. Pour spécifier un serveur de ressources, vous utilisez un bloc **ResourceRepositoryWeb** (pour un serveur collecteur web) ou **ResourceRepositoryShare** (pour un serveur collecteur SMB).
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

## <a name="see-also"></a>Voir aussi

* [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)