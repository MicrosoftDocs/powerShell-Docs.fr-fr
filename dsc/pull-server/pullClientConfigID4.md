---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurer un Client collecteur à l’aide des ID de Configuration dans PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401756"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Configurer un Client collecteur à l’aide des ID de Configuration dans PowerShell 4.0

>S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

Avant de configurer un client collecteur, vous devez configurer un serveur collecteur. Bien que cette commande n’est pas obligatoire, il facilite le dépannage et vous permet de s’assurer que l’inscription a réussi. Pour configurer un serveur collecteur, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état. Les sections suivantes vous montrent comment configurer un client collecteur avec un partage SMB ou un serveur d’extraction DSC HTTP. Lorsque Gestionnaire de configuration local du nœud est actualisé, il vous recontacte pour l’emplacement configuré pour télécharger toutes les configurations sont affectées. Si toutes les ressources requises n’existent pas sur le nœud, il télécharge automatiquement les à partir de l’emplacement configuré. Si le nœud est configuré avec un [serveur de rapports](reportServer.md), il sera ensuite l’état de l’opération.

## <a name="configure-the-pull-client-lcm"></a>Configurer le client d’extraction LCM

L’exécution d’un des exemples ci-dessous crée un nouveau dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration. Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.

Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration. Par exemple :

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID de configuration

Les exemples ci-dessous ensemble la **ConfigurationID** propriété du Gestionnaire de configuration local à un **Guid** qui avait été précédemment créé à cet effet. Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur. Le fichier MOF de configuration sur le serveur collecteur doit être nommé `ConfigurationID.mof`, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible. Pour plus d’informations, consultez [publier les Configurations à un serveur collecteur (v4/v5)](publishConfigs.md).

Vous pouvez créer un aléatoire **Guid** à l’aide de l’exemple ci-dessous.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurer un Client collecteur à télécharger les Configurations

Chaque client doit être configuré dans **extraction** mode et l’url du serveur collecteur où sa configuration est stockée. Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires. Pour configurer le LCM, vous créez un type spécial de configuration, avec un **LocalConfigurationManager** bloc. Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>Serveur collecteur de DSC HTTP

Si le serveur collecteur est configuré comme un service web, vous définissez le **DownloadManagerName** à **WebDownloadManager**. Le **WebDownloadManager** requiert que vous spécifiiez un **ServerUrl** à la **DownloadManagerCustomData** clé. Vous pouvez également spécifier une valeur pour **AllowUnsecureConnection**, comme dans l’exemple ci-dessous. Le script suivant configure le gestionnaire de configuration local de façon à extraire des configurations d’un serveur nommé « PullServer ».

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>Partage SMB

Si le serveur collecteur est configuré comme un partage de fichiers SMB, plutôt qu’un service web, vous définissez le **DownloadManagerName** à **DscFileDownloadManager** plutôt que **WebDownLoadManager**. Le **DscFileDownloadManager** requiert que vous spécifiiez un **SourcePath** propriété dans le **DownloadManagerCustomData**. Le script suivant configure le gestionnaire de configuration local de façon à extraire d’un partage SMB nommé « SmbDscShare » sur un serveur nommé « CONTOSO-SERVER ».

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Étapes suivantes

Une fois que le client d’extraction a été configuré, vous pouvez utiliser les guides suivants pour effectuer les étapes suivantes :

- [Publier des configurations vers un serveur Pull (v4/v5)](publishConfigs.md)
- [Empaqueter et charger des ressources vers un serveur Pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Voir aussi

- [Configurer un serveur de collecteur web DSC](pullServer.md)
- [Configurer un serveur Pull SMB DSC](pullServerSMB.md)
