---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configurations partielles du service de configuration d’état souhaité PowerShell
ms.openlocfilehash: 379ecf804329f318e9604c1af43a60a0e24551f1
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417742"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Configurations partielles du service de configuration d’état souhaité PowerShell

_S’applique à : Windows PowerShell 5.0 et ultérieur._

Dans PowerShell 5.0, la configuration d’état souhaité (DSC) permet de distribuer des fragments de configuration provenant de plusieurs sources. Le gestionnaire de configuration local sur le nœud cible réunit les fragments avant de les appliquer sous forme de configuration unique. Cette fonctionnalité permet de partager le contrôle de la configuration entre plusieurs personnes ou équipes. Par exemple, si deux équipes ou plus de développeurs collaborent sur un service, elles peuvent avoir besoin de créer des configurations propres pour gérer leur partie du service. Chacune de ces configurations peut être extraite de différents serveurs collecteurs et ajoutée à différents stades de développement. Les configurations partielles permettent également à différents utilisateurs ou équipes de contrôler les divers aspects de la configuration des nœuds sans avoir à coordonner la modification d’un document de configuration unique. Par exemple, une équipe peut être chargée de déployer une machine virtuelle et un système d’exploitation, tandis qu’une autre peut déployer d’autres applications et services sur cette machine virtuelle. Avec les configurations partielles, chaque équipe peut créer sa propre configuration, sans qu’elle soit inutilement compliquée.

Vous pouvez utiliser des configurations partielles en mode par envoi ou par extraction, ou les deux.

## <a name="partial-configurations-in-push-mode"></a>Configurations partielles en mode par envoi

Pour utiliser des configurations partielles en mode par envoi, vous configurez le gestionnaire de configuration local sur le nœud cible de façon à recevoir les configurations partielles. Chaque configuration partielle doit être envoyée à la cible à l’aide de l’applet de commande `Publish-DSCConfiguration`. Le nœud cible combine ensuite la configuration partielle en une configuration unique, que vous pouvez appliquer en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Configuration du gestionnaire de configuration local pour les configurations partielles en mode par émission

Pour configurer le gestionnaire de configuration local pour les configurations partielles en mode par envoi, vous créez une configuration **DSCLocalConfigurationManager** avec un bloc **PartialConfiguration** pour chaque configuration partielle. Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuring the Local Configuration Manager](/powershell/scripting/dsc/metaConfig). L’exemple suivant montre une configuration de gestionnaire de configuration local avec deux configurations partielles : une qui déploie le système d’exploitation, et l’autre qui déploie et configure SharePoint.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

Le paramètre **RefreshMode** pour chaque configuration partielle est défini sur « Émission ». Les noms des blocs **PartialConfiguration** (dans le cas présent, « ServiceAccountConfig » et « SharePointConfig ») doivent correspondre exactement aux noms des configurations envoyées au nœud cible.

> [!Note]
> Le nom de chaque bloc **PartialConfiguration** doit correspondre au nom réel de la configuration tel qu’il est spécifié dans le script de configuration, et non pas au nom du fichier MOF, qui doit être le nom du nœud cible ou de l’hôte local (`localhost`).

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publication et démarrage de configurations partielles en mode par émission

Vous appelez ensuite [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) pour chaque configuration, en passant les dossiers contenant les documents de configuration comme paramètres **Path**. `Publish-DSCConfiguration` place les fichiers MOF de configuration sur les nœuds cibles. Après avoir publié les deux configurations, vous pouvez appeler `Start-DSCConfiguration –UseExisting` sur le nœud cible.

Par exemple, si vous avez compilé les documents MOF de configuration suivants sur le nœud de création :

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

vous devez publier et exécuter les configurations comme suit :

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> L’utilisateur qui exécute l’applet de commande [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) doit disposer de privilèges d’administrateur sur le nœud cible.

## <a name="partial-configurations-in-pull-mode"></a>Configurations partielles en mode par extraction

Les configurations partielles peuvent être extraites d’un ou plusieurs serveurs collecteurs (pour plus d’informations sur les serveurs collecteurs, consultez [Serveurs collecteurs de la configuration d’état souhaité Windows PowerShell](pullServer.md). Pour ce faire, vous devez configurer le gestionnaire de configuration local sur le nœud cible de façon à extraire les configurations partielles, et nommer et localiser correctement les documents de configuration sur les serveurs collecteurs.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Configuration du gestionnaire de configuration local pour les configurations en mode par extraction

Pour configurer le gestionnaire de configuration local de façon à extraire les configurations partielles d’un serveur collecteur, vous définissez le serveur collecteur dans un bloc **ConfigurationRepositoryWeb** (pour un serveur collecteur HTTP) ou **ConfigurationRepositoryShare** (pour un serveur collecteur SMB). Vous créez ensuite des blocs **PartialConfiguration** qui font référence au serveur collecteur à l’aide de la propriété **ConfigurationSource**. Vous devez également créer un bloc **Settings** pour spécifier que le gestionnaire de configuration local utilise le mode par extraction, et pour indiquer le paramètre **ConfigurationNames** ou **ConfigurationID** utilisé par le serveur collecteur et le nœud cible pour identifier les configurations. La métaconfiguration suivante définit un serveur collecteur HTTP nommé CONTOSO-PullSrv et deux configurations partielles qui l’utilisent.

Pour plus d’informations sur la configuration du gestionnaire de configuration local à l’aide de **ConfigurationNames**, consultez [Configuration d’un client collecteur à l’aide de noms de configuration](pullClientConfigNames.md). Pour plus d’informations sur la configuration du gestionnaire de configuration local à l’aide de **ConfigurationID**, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Configuration du gestionnaire de configuration local pour les configurations en mode par extraction à l’aide de noms de configuration

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Configuration du gestionnaire de configuration local pour les configurations en mode par extraction à l’aide de l’ID de configuration

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

Vous pouvez extraire des configurations partielles de plusieurs serveurs collecteurs : vous devez simplement définir chaque serveur collecteur, puis faire référence au serveur collecteur approprié dans chaque bloc **PartialConfiguration**.

Après avoir créé la métaconfiguration, vous devez l’exécuter pour créer un document de configuration (un fichier MOF), puis appeler [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) pour configurer le gestionnaire de configuration local.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Attribution de noms et placement des documents de configuration sur le serveur collecteur (ConfigurationNames)

Les documents de configuration partielle doivent être placés dans le dossier spécifié comme **ConfigurationPath** dans le fichier `web.config` pour le serveur collecteur (généralement `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Attribution de noms aux documents de configuration sur le serveur collecteur dans PowerShell 5.1

Si vous extrayez une seule configuration partielle d’un serveur collecteur individuel, vous pouvez donner n’importe quel nom au document de configuration. Si vous extrayez plusieurs configurations partielles d’un serveur collecteur, vous pouvez nommer le document de configuration `<ConfigurationName>.mof` (où *ConfigurationName* est le nom de la configuration partielle) ou `<ConfigurationName>.<NodeName>.mof` (où *ConfigurationName* est le nom de la configuration partielle et *NodeName* le nom du nœud cible). Vous pouvez ainsi extraire des configurations du serveur collecteur DSC Azure Automation.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Attribution de noms aux documents de configuration sur le serveur collecteur dans PowerShell 5.0

Les documents de configuration doivent être nommés comme suit : `ConfigurationName.mof`, où *ConfigurationName* est le nom de la configuration partielle. Dans notre exemple, les documents de configuration doivent être nommés comme suit :

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Attribution de noms et placement des documents de configuration sur le serveur collecteur (ConfigurationID)

Les documents de configuration partielle doivent être placés dans le dossier spécifié comme **ConfigurationPath** dans le fichier `web.config` pour le serveur collecteur (généralement `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Les documents de configuration doivent être nommés comme suit : `<ConfigurationName>.<ConfigurationID>.mof`, où _ConfigurationName_ est le nom de la configuration partielle et _ConfigurationID_ est l’ID de configuration défini dans le gestionnaire de configuration local sur le nœud cible. Dans notre exemple, les documents de configuration doivent être nommés comme suit :

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Exécution des configurations partielles d’un serveur collecteur

Une fois que le gestionnaire de configuration local a été configuré sur le nœud cible et que les documents de configuration ont été créés et correctement nommés sur le serveur collecteur, le nœud cible extrait les configurations partielles, les combine et applique la configuration obtenue à intervalles réguliers, comme spécifié par la propriété **RefreshFrequencyMins** du gestionnaire de configuration local. Si vous voulez forcer une actualisation, vous pouvez appeler l’applet de commande [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) pour extraire les configurations, puis `Start-DSCConfiguration –UseExisting` pour les appliquer.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Configurations partielles en modes mixtes par envoi et par extraction

Vous pouvez également associer les modes mixtes par envoi et par extraction pour les configurations partielles. Autrement dit, vous pouvez avoir une configuration partielle extraite d’un serveur collecteur et une autre envoyée. Spécifiez le mode d’actualisation pour chaque configuration partielle, comme décrit dans les sections précédentes. Par exemple, la métaconfiguration suivante décrit le même scénario, avec la configuration partielle `ServiceAccountConfig` en mode par extraction et la configuration partielle `SharePointConfig` en mode par envoi.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Modes mixtes par envoi et par extraction à l’aide de ConfigurationNames

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Modes mixtes par envoi et par extraction à l’aide de ConfigurationID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

Notez que le paramètre **RefreshMode** spécifié dans le bloc de paramètres est « Pull », mais que le paramètre **RefreshMode** de la configuration partielle `SharePointConfig` est « Push ».

Nommez et localisez les fichiers MOF de configuration comme décrit ci-dessus selon leur mode d’actualisation respectif.
Appelez `Publish-DSCConfiguration` pour publier la configuration partielle `SharePointConfig`, puis attendez que la configuration `ServiceAccountConfig` soit extraite du serveur collecteur ou forcez une actualisation en appelant [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Exemple de configuration partielle ServiceAccountConfig

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a>Exemple de configuration partielle SharePointConfig

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>Voir aussi

[Serveurs Pull Desired State Configuration (DSC) PowerShell Windows](pullServer.md)

[Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md)
