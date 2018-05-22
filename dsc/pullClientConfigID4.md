---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL où contacter le serveur collecteur pour obtenir des configurations. Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires. Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration appelé « métaconfiguration ». Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Gestionnaire de configuration local de la configuration d’état souhaité Windows PowerShell 4.0](metaConfig4.md)

Le script suivant configure le gestionnaire de configuration local de façon à extraire des configurations d’un serveur nommé « PullServer ».

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

Dans le script, **DownloadManagerCustomData** passe l’URL du serveur collecteur et (dans cet exemple) permet une connexion non sécurisée.

Quand le script s’exécute, il crée un dossier de sortie appelé **SimpleMetaConfigurationForPull** et y place un fichier MOF de métaconfiguration.

Pour appliquer la configuration, utilisez **Set-DscLocalConfigurationManager** avec des paramètres pour **ComputerName** (utilisez « localhost ») et **Path** (chemin de l’emplacement du fichier localhost.meta.mof du nœud cible). Par exemple :
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>ID de configuration
Le script définit la propriété **ConfigurationID** du gestionnaire de configuration local sur un GUID précédemment créé à cet effet (vous pouvez créer un GUID à l’aide de l’applet de commande **New-Guid**). Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur. Le fichier MOF de configuration sur le serveur collecteur doit être nommé `ConfigurationID.mof`, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.

## <a name="pulling-from-an-smb-server"></a>Extraction à partir d’un serveur SMB

Si le serveur collecteur est configuré comme un partage de fichiers SMB au lieu d’un service web, vous spécifiez **DscFileDownloadManager** au lieu de **WebDownLoadManager**.
**DscFileDownloadManager** prend une propriété **SourcePath** au lieu de **ServerUrl**. Le script suivant configure le gestionnaire de configuration local de façon à extraire d’un partage SMB nommé « SmbDscShare » sur un serveur nommé « CONTOSO-SERVER » :

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Voir aussi

- [Configuration d’un serveur collecteur web DSC](pullServer.md)
- [Configuration d’un serveur collecteur SMB DSC](pullServerSMB.md)