---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Configurations partielles du service de configuration d’état souhaité PowerShell
description: DSC permet de distribuer des fragments de configuration provenant de plusieurs sources. Le gestionnaire de configuration local (LCM) sur le nœud cible réunit les fragments avant de les appliquer sous forme de configuration unique.
ms.openlocfilehash: 3afe5d684cabec9c8ab528347610b6dd00c5d4e9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661608"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="f02de-105">Configurations partielles du service de configuration d’état souhaité PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02de-105">PowerShell Desired State Configuration partial configurations</span></span>

> <span data-ttu-id="f02de-106">S’applique à : Windows PowerShell 5.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="f02de-106">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="f02de-107">Dans PowerShell 5.0, la configuration d’état souhaité (DSC) permet de distribuer des fragments de configuration provenant de plusieurs sources.</span><span class="sxs-lookup"><span data-stu-id="f02de-107">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="f02de-108">Le gestionnaire de configuration local sur le nœud cible réunit les fragments avant de les appliquer sous forme de configuration unique.</span><span class="sxs-lookup"><span data-stu-id="f02de-108">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="f02de-109">Cette fonctionnalité permet de partager le contrôle de la configuration entre plusieurs personnes ou équipes.</span><span class="sxs-lookup"><span data-stu-id="f02de-109">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="f02de-110">Par exemple, si deux équipes ou plus de développeurs collaborent sur un service, elles peuvent avoir besoin de créer des configurations propres pour gérer leur partie du service.</span><span class="sxs-lookup"><span data-stu-id="f02de-110">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="f02de-111">Chacune de ces configurations peut être extraite de différents serveurs collecteurs et ajoutée à différents stades de développement.</span><span class="sxs-lookup"><span data-stu-id="f02de-111">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="f02de-112">Les configurations partielles permettent également à différents utilisateurs ou équipes de contrôler les divers aspects de la configuration des nœuds sans avoir à coordonner la modification d’un document de configuration unique.</span><span class="sxs-lookup"><span data-stu-id="f02de-112">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="f02de-113">Par exemple, une équipe peut être chargée de déployer une machine virtuelle et un système d’exploitation, tandis qu’une autre peut déployer d’autres applications et services sur cette machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="f02de-113">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="f02de-114">Avec les configurations partielles, chaque équipe peut créer sa propre configuration, sans qu’elle soit inutilement compliquée.</span><span class="sxs-lookup"><span data-stu-id="f02de-114">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="f02de-115">Vous pouvez utiliser des configurations partielles en mode par envoi ou par extraction, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="f02de-115">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="f02de-116">Configurations partielles en mode par envoi</span><span class="sxs-lookup"><span data-stu-id="f02de-116">Partial configurations in push mode</span></span>

<span data-ttu-id="f02de-117">Pour utiliser des configurations partielles en mode par envoi, vous configurez le gestionnaire de configuration local sur le nœud cible de façon à recevoir les configurations partielles.</span><span class="sxs-lookup"><span data-stu-id="f02de-117">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="f02de-118">Chaque configuration partielle doit être envoyée à la cible à l’aide de l’applet de commande `Publish-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="f02de-118">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="f02de-119">Le nœud cible associe ensuite la configuration partielle à une configuration unique, que vous pouvez appliquer en appelant l’applet de commande [Start-DscConfigurationxt](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="f02de-119">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="f02de-120">Configuration du gestionnaire de configuration local pour les configurations partielles en mode par émission</span><span class="sxs-lookup"><span data-stu-id="f02de-120">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="f02de-121">Pour configurer le gestionnaire de configuration local pour les configurations partielles en mode par envoi, vous créez une configuration **DSCLocalConfigurationManager** avec un bloc **PartialConfiguration** pour chaque configuration partielle.</span><span class="sxs-lookup"><span data-stu-id="f02de-121">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="f02de-122">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md) (Configuration du gestionnaire de configuration local).</span><span class="sxs-lookup"><span data-stu-id="f02de-122">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span> <span data-ttu-id="f02de-123">L’exemple suivant montre une configuration de gestionnaire de configuration local avec deux configurations partielles : une qui déploie le système d’exploitation, et l’autre qui déploie et configure SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f02de-123">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="f02de-124">Le paramètre **RefreshMode** pour chaque configuration partielle est défini sur « Émission ».</span><span class="sxs-lookup"><span data-stu-id="f02de-124">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="f02de-125">Les noms des blocs **PartialConfiguration** (dans le cas présent, « ServiceAccountConfig » et « SharePointConfig ») doivent correspondre exactement aux noms des configurations envoyées au nœud cible.</span><span class="sxs-lookup"><span data-stu-id="f02de-125">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="f02de-126">Le nom de chaque bloc **PartialConfiguration** doit correspondre au nom réel de la configuration tel qu’il est spécifié dans le script de configuration, et non pas au nom du fichier MOF, qui doit être le nom du nœud cible ou de l’hôte local (`localhost`).</span><span class="sxs-lookup"><span data-stu-id="f02de-126">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="f02de-127">Publication et démarrage de configurations partielles en mode par émission</span><span class="sxs-lookup"><span data-stu-id="f02de-127">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="f02de-128">Vous appelez ensuite [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) pour chaque configuration, en passant les dossiers contenant les documents de configuration comme paramètres **Path**.</span><span class="sxs-lookup"><span data-stu-id="f02de-128">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="f02de-129">`Publish-DSCConfiguration` place les fichiers MOF de configuration sur les nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="f02de-129">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="f02de-130">Après avoir publié les deux configurations, vous pouvez appeler `Start-DSCConfiguration –UseExisting` sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="f02de-130">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="f02de-131">Par exemple, si vous avez compilé les documents MOF de configuration suivants sur le nœud de création :</span><span class="sxs-lookup"><span data-stu-id="f02de-131">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

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

<span data-ttu-id="f02de-132">vous devez publier et exécuter les configurations comme suit :</span><span class="sxs-lookup"><span data-stu-id="f02de-132">You would publish and run the configurations as follows:</span></span>

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
> <span data-ttu-id="f02de-133">L’utilisateur qui exécute l’applet de commande [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) doit disposer de privilèges d’administrateur sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="f02de-133">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="f02de-134">Configurations partielles en mode par extraction</span><span class="sxs-lookup"><span data-stu-id="f02de-134">Partial configurations in pull mode</span></span>

<span data-ttu-id="f02de-135">Les configurations partielles peuvent être extraites d’un ou plusieurs serveurs collecteurs (pour plus d’informations sur les serveurs collecteurs, consultez [Serveurs collecteurs de la configuration d’état souhaité Windows PowerShell](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="f02de-135">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="f02de-136">Pour ce faire, vous devez configurer le gestionnaire de configuration local sur le nœud cible de façon à extraire les configurations partielles, et nommer et localiser correctement les documents de configuration sur les serveurs collecteurs.</span><span class="sxs-lookup"><span data-stu-id="f02de-136">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="f02de-137">Configuration du gestionnaire de configuration local pour les configurations en mode par extraction</span><span class="sxs-lookup"><span data-stu-id="f02de-137">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="f02de-138">Pour configurer le gestionnaire de configuration local de façon à extraire les configurations partielles d’un serveur collecteur, vous définissez le serveur collecteur dans un bloc **ConfigurationRepositoryWeb** (pour un serveur collecteur HTTP) ou **ConfigurationRepositoryShare** (pour un serveur collecteur SMB).</span><span class="sxs-lookup"><span data-stu-id="f02de-138">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="f02de-139">Vous créez ensuite des blocs **PartialConfiguration** qui font référence au serveur collecteur à l’aide de la propriété **ConfigurationSource**.</span><span class="sxs-lookup"><span data-stu-id="f02de-139">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="f02de-140">Vous devez également créer un bloc **Settings** pour spécifier que le gestionnaire de configuration local utilise le mode par extraction, et pour indiquer le paramètre **ConfigurationNames** ou **ConfigurationID** utilisé par le serveur collecteur et le nœud cible pour identifier les configurations.</span><span class="sxs-lookup"><span data-stu-id="f02de-140">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="f02de-141">La métaconfiguration suivante définit un serveur collecteur HTTP nommé CONTOSO-PullSrv et deux configurations partielles qui l’utilisent.</span><span class="sxs-lookup"><span data-stu-id="f02de-141">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="f02de-142">Pour plus d’informations sur la configuration du gestionnaire de configuration local à l’aide de **ConfigurationNames** , consultez [Configuration d’un client collecteur à l’aide de noms de configuration](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="f02de-142">For more information about configuring the LCM using **ConfigurationNames** , see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="f02de-143">Pour plus d’informations sur la configuration du gestionnaire de configuration local à l’aide de **ConfigurationID** , consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="f02de-143">For information about configuring the LCM using **ConfigurationID** , see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="f02de-144">Configuration du gestionnaire de configuration local pour les configurations en mode par extraction à l’aide de noms de configuration</span><span class="sxs-lookup"><span data-stu-id="f02de-144">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="f02de-145">Configuration du gestionnaire de configuration local pour les configurations en mode par extraction à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="f02de-145">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="f02de-146">Vous pouvez extraire des configurations partielles de plusieurs serveurs collecteurs : vous devez simplement définir chaque serveur collecteur, puis faire référence au serveur collecteur approprié dans chaque bloc **PartialConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="f02de-146">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="f02de-147">Après avoir créé la métaconfiguration, vous devez l’exécuter pour créer un document de configuration (un fichier MOF), puis appeler [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) pour configurer le gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="f02de-147">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="f02de-148">Attribution de noms et placement des documents de configuration sur le serveur collecteur (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="f02de-148">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="f02de-149">Les documents de configuration partielle doivent être placés dans le dossier spécifié comme **ConfigurationPath** dans le fichier `web.config` pour le serveur collecteur (généralement `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="f02de-149">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="f02de-150">Attribution de noms aux documents de configuration sur le serveur collecteur dans PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f02de-150">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="f02de-151">Si vous extrayez une seule configuration partielle d’un serveur collecteur individuel, vous pouvez donner n’importe quel nom au document de configuration.</span><span class="sxs-lookup"><span data-stu-id="f02de-151">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="f02de-152">Si vous extrayez plusieurs configurations partielles d’un serveur collecteur, vous pouvez nommer le document de configuration `<ConfigurationName>.mof` (où *ConfigurationName* est le nom de la configuration partielle) ou `<ConfigurationName>.<NodeName>.mof` (où *ConfigurationName* est le nom de la configuration partielle et *NodeName* le nom du nœud cible).</span><span class="sxs-lookup"><span data-stu-id="f02de-152">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="f02de-153">Vous pouvez ainsi extraire des configurations du serveur collecteur DSC Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="f02de-153">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="f02de-154">Attribution de noms aux documents de configuration sur le serveur collecteur dans PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f02de-154">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="f02de-155">Les documents de configuration doivent être nommés comme suit : `ConfigurationName.mof`, où *ConfigurationName* est le nom de la configuration partielle.</span><span class="sxs-lookup"><span data-stu-id="f02de-155">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="f02de-156">Dans notre exemple, les documents de configuration doivent être nommés comme suit :</span><span class="sxs-lookup"><span data-stu-id="f02de-156">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="f02de-157">Attribution de noms et placement des documents de configuration sur le serveur collecteur (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="f02de-157">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="f02de-158">Les documents de configuration partielle doivent être placés dans le dossier spécifié comme **ConfigurationPath** dans le fichier `web.config` pour le serveur collecteur (généralement `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="f02de-158">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="f02de-159">Les documents de configuration doivent être nommés comme suit : `<ConfigurationName>.<ConfigurationID>.mof`, où _ConfigurationName_ est le nom de la configuration partielle et _ConfigurationID_ est l’ID de configuration défini dans le gestionnaire de configuration local sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="f02de-159">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="f02de-160">Dans notre exemple, les documents de configuration doivent être nommés comme suit :</span><span class="sxs-lookup"><span data-stu-id="f02de-160">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="f02de-161">Exécution des configurations partielles d’un serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="f02de-161">Running partial configurations from a pull server</span></span>

<span data-ttu-id="f02de-162">Une fois que le gestionnaire de configuration local a été configuré sur le nœud cible et que les documents de configuration ont été créés et correctement nommés sur le serveur collecteur, le nœud cible extrait les configurations partielles, les combine et applique la configuration obtenue à intervalles réguliers, comme spécifié par la propriété **RefreshFrequencyMins** du gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="f02de-162">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="f02de-163">Si vous voulez forcer une actualisation, vous pouvez appeler l’applet de commande [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) pour extraire les configurations, puis `Start-DSCConfiguration –UseExisting` pour les appliquer.</span><span class="sxs-lookup"><span data-stu-id="f02de-163">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="f02de-164">Configurations partielles en modes mixtes par envoi et par extraction</span><span class="sxs-lookup"><span data-stu-id="f02de-164">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="f02de-165">Vous pouvez également associer les modes mixtes par envoi et par extraction pour les configurations partielles.</span><span class="sxs-lookup"><span data-stu-id="f02de-165">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="f02de-166">Autrement dit, vous pouvez avoir une configuration partielle extraite d’un serveur collecteur et une autre envoyée.</span><span class="sxs-lookup"><span data-stu-id="f02de-166">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="f02de-167">Spécifiez le mode d’actualisation pour chaque configuration partielle, comme décrit dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="f02de-167">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="f02de-168">Par exemple, la métaconfiguration suivante décrit le même scénario, avec la configuration partielle `ServiceAccountConfig` en mode par extraction et la configuration partielle `SharePointConfig` en mode par envoi.</span><span class="sxs-lookup"><span data-stu-id="f02de-168">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="f02de-169">Modes mixtes par envoi et par extraction à l’aide de ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="f02de-169">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="f02de-170">Modes mixtes par envoi et par extraction à l’aide de ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="f02de-170">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="f02de-171">Notez que le paramètre **RefreshMode** spécifié dans le bloc de paramètres est « Pull », mais que le paramètre **RefreshMode** de la configuration partielle `SharePointConfig` est « Push ».</span><span class="sxs-lookup"><span data-stu-id="f02de-171">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="f02de-172">Nommez et localisez les fichiers MOF de configuration comme décrit ci-dessus selon leur mode d’actualisation respectif.</span><span class="sxs-lookup"><span data-stu-id="f02de-172">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="f02de-173">Appelez `Publish-DSCConfiguration` pour publier la configuration partielle `SharePointConfig`, puis attendez que la configuration `ServiceAccountConfig` soit extraite du serveur collecteur ou forcez une actualisation en appelant [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="f02de-173">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="f02de-174">Exemple de configuration partielle ServiceAccountConfig</span><span class="sxs-lookup"><span data-stu-id="f02de-174">Example ServiceAccountConfig Partial Configuration</span></span>

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

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="f02de-175">Exemple de configuration partielle SharePointConfig</span><span class="sxs-lookup"><span data-stu-id="f02de-175">Example SharePointConfig Partial Configuration</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f02de-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f02de-176">See Also</span></span>

[<span data-ttu-id="f02de-177">Serveurs collecteurs de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02de-177">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="f02de-178">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="f02de-178">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
