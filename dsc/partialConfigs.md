---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configurations partielles du service de configuration d’état souhaité PowerShell"
ms.openlocfilehash: 2c5f29ee2940f4b7955219e97275ffa2695f9dee
ms.sourcegitcommit: aa6890031dad3f2981b24c58893d134bdf4e8655
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2017
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="ec49c-103">Configurations partielles du service de configuration d’état souhaité PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec49c-103">PowerShell Desired State Configuration partial configurations</span></span>

><span data-ttu-id="ec49c-104">S’applique à : Windows PowerShell 5.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="ec49c-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="ec49c-105">Dans PowerShell 5.0, la configuration d’état souhaité (DSC) permet de distribuer des fragments de configuration provenant de plusieurs sources.</span><span class="sxs-lookup"><span data-stu-id="ec49c-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="ec49c-106">Le gestionnaire de configuration local sur le nœud cible réunit les fragments avant de les appliquer sous forme de configuration unique.</span><span class="sxs-lookup"><span data-stu-id="ec49c-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="ec49c-107">Cette fonctionnalité permet de partager le contrôle de la configuration entre plusieurs personnes ou équipes.</span><span class="sxs-lookup"><span data-stu-id="ec49c-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="ec49c-108">Par exemple, si deux équipes ou plus de développeurs collaborent sur un service, elles peuvent avoir besoin de créer des configurations propres pour gérer leur partie du service.</span><span class="sxs-lookup"><span data-stu-id="ec49c-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="ec49c-109">Chacune de ces configurations peut être extraite de différents serveurs collecteurs et ajoutée à différents stades de développement.</span><span class="sxs-lookup"><span data-stu-id="ec49c-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="ec49c-110">Les configurations partielles permettent également à différents utilisateurs ou équipes de contrôler les divers aspects de la configuration des nœuds sans avoir à coordonner la modification d’un document de configuration unique.</span><span class="sxs-lookup"><span data-stu-id="ec49c-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="ec49c-111">Par exemple, une équipe peut être chargée de déployer une machine virtuelle et un système d’exploitation, tandis qu’une autre peut déployer d’autres applications et services sur cette machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="ec49c-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="ec49c-112">Avec les configurations partielles, chaque équipe peut créer sa propre configuration, sans qu’elle soit inutilement compliquée.</span><span class="sxs-lookup"><span data-stu-id="ec49c-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="ec49c-113">Vous pouvez utiliser des configurations partielles en mode par envoi ou par extraction, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="ec49c-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="ec49c-114">Configurations partielles en mode par envoi</span><span class="sxs-lookup"><span data-stu-id="ec49c-114">Partial configurations in push mode</span></span>
<span data-ttu-id="ec49c-115">Pour utiliser des configurations partielles en mode par envoi, vous configurez le gestionnaire de configuration local sur le nœud cible de façon à recevoir les configurations partielles.</span><span class="sxs-lookup"><span data-stu-id="ec49c-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="ec49c-116">Chaque configuration partielle doit être envoyée à la cible à l’aide de l’applet de commande Publish-DSCConfiguration.</span><span class="sxs-lookup"><span data-stu-id="ec49c-116">Each partial configuration must be pushed to the target by using the Publish-DSCConfiguration cmdlet.</span></span> <span data-ttu-id="ec49c-117">Le nœud cible combine ensuite la configuration partielle en une configuration unique, que vous pouvez appliquer en appelant l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="ec49c-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="ec49c-118">Configuration du gestionnaire de configuration local pour les configurations partielles en mode par émission</span><span class="sxs-lookup"><span data-stu-id="ec49c-118">Configuring the LCM for push-mode partial configurations</span></span>
<span data-ttu-id="ec49c-119">Pour configurer le gestionnaire de configuration local pour les configurations partielles en mode par envoi, vous créez une configuration **DSCLocalConfigurationManager** avec un bloc **PartialConfiguration** pour chaque configuration partielle.</span><span class="sxs-lookup"><span data-stu-id="ec49c-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="ec49c-120">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuring the Local Configuration Manager](https://technet.microsoft.com/en-us/library/mt421188.aspx).</span><span class="sxs-lookup"><span data-stu-id="ec49c-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](https://technet.microsoft.com/en-us/library/mt421188.aspx).</span></span> <span data-ttu-id="ec49c-121">L’exemple suivant montre une configuration de gestionnaire de configuration local avec deux configurations partielles : une qui déploie le système d’exploitation, et l’autre qui déploie et configure SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ec49c-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="ec49c-122">Le paramètre **RefreshMode** pour chaque configuration partielle est défini sur « Émission ».</span><span class="sxs-lookup"><span data-stu-id="ec49c-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="ec49c-123">Les noms des blocs **PartialConfiguration** (dans le cas présent, « ServiceAccountConfig » et « SharePointConfig ») doivent correspondre exactement aux noms des configurations envoyées au nœud cible.</span><span class="sxs-lookup"><span data-stu-id="ec49c-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

><span data-ttu-id="ec49c-124">**Remarque :** Le nom de chaque bloc **PartialConfiguration** doit correspondre au nom réel de la configuration tel qu’il est spécifié dans le script de configuration, et non pas au nom du fichier MOF, qui doit être le nom du nœud cible ou de l’hôte local (`localhost`).</span><span class="sxs-lookup"><span data-stu-id="ec49c-124">**Note:** The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="ec49c-125">Publication et démarrage de configurations partielles en mode par émission</span><span class="sxs-lookup"><span data-stu-id="ec49c-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="ec49c-126">Vous appelez ensuite [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) pour chaque configuration, en passant les dossiers contenant les documents de configuration comme paramètres **Path**.</span><span class="sxs-lookup"><span data-stu-id="ec49c-126">You then call [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="ec49c-127">`Publish-DSCConfiguration` place les fichiers MOF de configuration sur les nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="ec49c-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="ec49c-128">Après avoir publié les deux configurations, vous pouvez appeler `Start-DSCConfiguration –UseExisting` sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="ec49c-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="ec49c-129">Par exemple, si vous avez compilé les documents MOF de configuration suivants sur le nœud de création :</span><span class="sxs-lookup"><span data-stu-id="ec49c-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


    Directory: C:\PartialConfigTest


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
d-----        8/11/2016   1:55 PM                ServiceAccountConfig                                                                                                                  
d-----       11/17/2016   4:14 PM                SharePointConfig                                                                                                                                    


    Directory: C:\PartialConfigTest\ServiceAccountConfig


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
-a----        8/11/2016   2:02 PM           2034 TestVM.mof                                                                                                                                


    Directory: C:\DscTests\SharePointConfig


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
-a----       11/17/2016   4:14 PM           1930 TestVM.mof                                                                                                                                     
```

<span data-ttu-id="ec49c-130">vous devez publier et exécuter les configurations comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec49c-130">You would publish and run the configurations as follows:</span></span>

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command                  
--     ----            -------------   -----         -----------     --------             -------                  
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

><span data-ttu-id="ec49c-131">**Remarque :** L’utilisateur qui exécute l’applet de commande [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) doit disposer de privilèges d’administrateur sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="ec49c-131">**Note:** The user running the [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="ec49c-132">Configurations partielles en mode par extraction</span><span class="sxs-lookup"><span data-stu-id="ec49c-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="ec49c-133">Les configurations partielles peuvent être extraites d’un ou plusieurs serveurs collecteurs (pour plus d’informations sur les serveurs collecteurs, consultez [Serveurs collecteurs de la configuration d’état souhaité Windows PowerShell](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="ec49c-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="ec49c-134">Pour ce faire, vous devez configurer le gestionnaire de configuration local sur le nœud cible de façon à extraire les configurations partielles, et nommer et localiser correctement les documents de configuration sur les serveurs collecteurs.</span><span class="sxs-lookup"><span data-stu-id="ec49c-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="ec49c-135">Configuration du gestionnaire de configuration local pour les configurations en mode par extraction</span><span class="sxs-lookup"><span data-stu-id="ec49c-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="ec49c-136">Pour configurer le gestionnaire de configuration local de façon à extraire les configurations partielles d’un serveur collecteur, vous définissez le serveur collecteur dans un bloc **ConfigurationRepositoryWeb** (pour un serveur collecteur HTTP) ou **ConfigurationRepositoryShare** (pour un serveur collecteur SMB).</span><span class="sxs-lookup"><span data-stu-id="ec49c-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="ec49c-137">Vous créez ensuite des blocs **PartialConfiguration** qui font référence au serveur collecteur à l’aide de la propriété **ConfigurationSource**.</span><span class="sxs-lookup"><span data-stu-id="ec49c-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="ec49c-138">Vous devez également créer un bloc **Settings** pour spécifier que le gestionnaire de configuration local utilise le mode par extraction, et pour indiquer le paramètre **ConfigurationNames** ou **ConfigurationID** utilisé par le serveur collecteur et le nœud cible pour identifier les configurations.</span><span class="sxs-lookup"><span data-stu-id="ec49c-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="ec49c-139">La métaconfiguration suivante définit un serveur collecteur HTTP nommé CONTOSO-PullSrv et deux configurations partielles qui l’utilisent.</span><span class="sxs-lookup"><span data-stu-id="ec49c-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="ec49c-140">Pour plus d’informations sur la configuration du gestionnaire de configuration local à l’aide de **ConfigurationNames**, consultez [Configuration d’un client collecteur à l’aide de noms de configuration](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="ec49c-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="ec49c-141">Pour plus d’informations sur la configuration du gestionnaire de configuration local à l’aide de **ConfigurationID**, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="ec49c-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="ec49c-142">Configuration du gestionnaire de configuration local pour les configurations en mode par extraction à l’aide de noms de configuration</span><span class="sxs-lookup"><span data-stu-id="ec49c-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="ec49c-143">Configuration du gestionnaire de configuration local pour les configurations en mode par extraction à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="ec49c-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="ec49c-144">Vous pouvez extraire des configurations partielles de plusieurs serveurs collecteurs : vous devez simplement définir chaque serveur collecteur, puis faire référence au serveur collecteur approprié dans chaque bloc **PartialConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="ec49c-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="ec49c-145">Après avoir créé la métaconfiguration, vous devez l’exécuter pour créer un document de configuration (un fichier MOF), puis appeler [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) pour configurer le gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="ec49c-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="ec49c-146">Attribution de noms et placement des documents de configuration sur le serveur collecteur (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="ec49c-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="ec49c-147">Les documents de configuration partielle doivent être placés dans le dossier spécifié comme **ConfigurationPath** dans le fichier `web.config` pour le serveur collecteur (généralement `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="ec49c-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> 

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="ec49c-148">Attribution de noms aux documents de configuration sur le serveur collecteur dans PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="ec49c-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="ec49c-149">Si vous extrayez une seule configuration partielle d’un serveur collecteur individuel, vous pouvez donner n’importe quel nom au document de configuration.</span><span class="sxs-lookup"><span data-stu-id="ec49c-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="ec49c-150">Si vous extrayez plusieurs configurations partielles d’un serveur collecteur, vous pouvez nommer le document de configuration `<ConfigurationName>.mof` (où _ConfigurationName_ est le nom de la configuration partielle) ou `<ConfigurationName>.<NodeName>.mof` (où _ConfigurationName_ est le nom de la configuration partielle et _NodeName_ le nom du nœud cible).</span><span class="sxs-lookup"><span data-stu-id="ec49c-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where _ConfigurationName_ is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  _ConfigurationName_ is the name of the partial configuration, and _NodeName_ is the name of the target node.</span></span> <span data-ttu-id="ec49c-151">Vous pouvez ainsi extraire des configurations du serveur collecteur DSC Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="ec49c-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="ec49c-152">Attribution de noms aux documents de configuration sur le serveur collecteur dans PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ec49c-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="ec49c-153">Les documents de configuration doivent être nommés comme suit : `ConfigurationName.mof`, où _ConfigurationName_ est le nom de la configuration partielle.</span><span class="sxs-lookup"><span data-stu-id="ec49c-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where _ConfigurationName_ is the name of the partial configuration.</span></span> <span data-ttu-id="ec49c-154">Dans notre exemple, les documents de configuration doivent être nommés comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec49c-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="ec49c-155">Attribution de noms et placement des documents de configuration sur le serveur collecteur (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="ec49c-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="ec49c-156">Les documents de configuration partielle doivent être placés dans le dossier spécifié comme **ConfigurationPath** dans le fichier `web.config` pour le serveur collecteur (généralement `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="ec49c-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="ec49c-157">Les documents de configuration doivent être nommés comme suit : _ConfigurationName_,</span><span class="sxs-lookup"><span data-stu-id="ec49c-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="ec49c-158">_ConfigurationID_`.mof`, où _ConfigurationName_ est le nom de la configuration partielle et _ConfigurationID_ est l’ID de configuration défini dans le gestionnaire de configuration local sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="ec49c-158">_ConfigurationID_`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="ec49c-159">Dans notre exemple, les documents de configuration doivent être nommés comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec49c-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="ec49c-160">Exécution des configurations partielles d’un serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="ec49c-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="ec49c-161">Une fois que le gestionnaire de configuration local a été configuré sur le nœud cible et que les documents de configuration ont été créés et correctement nommés sur le serveur collecteur, le nœud cible extrait les configurations partielles, les combine et applique la configuration obtenue à intervalles réguliers, comme spécifié par la propriété **RefreshFrequencyMins** du gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="ec49c-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="ec49c-162">Si vous voulez forcer une actualisation, vous pouvez appeler l’applet de commande [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) pour extraire les configurations, puis `Start-DSCConfiguration –UseExisting` pour les appliquer.</span><span class="sxs-lookup"><span data-stu-id="ec49c-162">If you want to force a refresh, you can call the [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="ec49c-163">Configurations partielles en modes mixtes par envoi et par extraction</span><span class="sxs-lookup"><span data-stu-id="ec49c-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="ec49c-164">Vous pouvez également associer les modes mixtes par envoi et par extraction pour les configurations partielles.</span><span class="sxs-lookup"><span data-stu-id="ec49c-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="ec49c-165">Autrement dit, vous pouvez avoir une configuration partielle extraite d’un serveur collecteur et une autre envoyée.</span><span class="sxs-lookup"><span data-stu-id="ec49c-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="ec49c-166">Spécifiez le mode d’actualisation pour chaque configuration partielle, comme décrit dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="ec49c-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="ec49c-167">Par exemple, la métaconfiguration suivante décrit le même scénario, avec la configuration partielle `ServiceAccountConfig` en mode par extraction et la configuration partielle `SharePointConfig` en mode par envoi.</span><span class="sxs-lookup"><span data-stu-id="ec49c-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="ec49c-168">Modes mixtes par envoi et par extraction à l’aide de ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="ec49c-168">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="ec49c-169">Modes mixtes par envoi et par extraction à l’aide de ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="ec49c-169">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="ec49c-170">Notez que le paramètre **RefreshMode** spécifié dans le bloc de paramètres est « Pull », mais que le paramètre **RefreshMode** de la configuration partielle `SharePointConfig` est « Push ».</span><span class="sxs-lookup"><span data-stu-id="ec49c-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="ec49c-171">Nommez et localisez les fichiers MOF de configuration comme décrit ci-dessus selon leur mode d’actualisation respectif.</span><span class="sxs-lookup"><span data-stu-id="ec49c-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="ec49c-172">Appelez **Publish-DSCConfiguration** pour publier la configuration partielle `SharePointConfig`, puis attendez que la configuration `ServiceAccountConfig` soit extraite du serveur collecteur ou forcez une actualisation en appelant [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span><span class="sxs-lookup"><span data-stu-id="ec49c-172">Call **Publish-DSCConfiguration** to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="ec49c-173">Exemple de configuration partielle ServiceAccountConfig</span><span class="sxs-lookup"><span data-stu-id="ec49c-173">Example ServiceAccountConfig Partial Configuration</span></span>

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
## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="ec49c-174">Exemple de configuration partielle SharePointConfig</span><span class="sxs-lookup"><span data-stu-id="ec49c-174">Example SharePointConfig Partial Configuration</span></span>
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
##<a name="see-also"></a><span data-ttu-id="ec49c-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec49c-175">See Also</span></span> 

<span data-ttu-id="ec49c-176">**Concepts**
[Serveurs collecteurs de la configuration d’état souhaité Windows PowerShell](pullServer.md)</span><span class="sxs-lookup"><span data-stu-id="ec49c-176">**Concepts**
[Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)</span></span> 

[<span data-ttu-id="ec49c-177">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="ec49c-177">Windows Configuring the Local Configuration Manager</span></span>](https://technet.microsoft.com/en-us/library/mt421188.aspx) 

