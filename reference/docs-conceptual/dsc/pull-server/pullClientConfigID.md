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
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="81325-104">Configurer un client Pull à l’aide d’ID de configuration dans PowerShell 5.0 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="81325-104">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="81325-105">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="81325-105">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81325-106">Le serveur collecteur (fonctionnalité Windows *Service DSC* ) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="81325-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="81325-107">Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="81325-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="81325-108">Avant de configurer un client Pull, vous devez configurer un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="81325-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="81325-109">Bien que cet ordre ne soit pas obligatoire, il facilite le dépannage et vous permet de vous assurer que l’inscription a réussi.</span><span class="sxs-lookup"><span data-stu-id="81325-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="81325-110">Pour configurer un serveur Pull, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="81325-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="81325-111">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="81325-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="81325-112">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="81325-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="81325-113">Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état.</span><span class="sxs-lookup"><span data-stu-id="81325-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="81325-114">Les sections suivantes montrent comment configurer un client Pull avec un partage SMB ou un serveur Pull DSC HTTP.</span><span class="sxs-lookup"><span data-stu-id="81325-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="81325-115">Quand le Gestionnaire de configuration local du nœud est actualisé, il contacte l’emplacement configuré pour télécharger toutes les configurations affectées.</span><span class="sxs-lookup"><span data-stu-id="81325-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="81325-116">Si des ressources requises n’existent pas sur le nœud, il les télécharge automatiquement à partir de l’emplacement configuré.</span><span class="sxs-lookup"><span data-stu-id="81325-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="81325-117">Si le nœud est configuré avec un [serveur de rapports](reportServer.md), il signale ensuite l’état de l’opération.</span><span class="sxs-lookup"><span data-stu-id="81325-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="81325-118">Cette rubrique s’applique à PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="81325-118">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="81325-119">Pour des informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="81325-119">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="81325-120">Configurer le Gestionnaire de configuration local du client Pull</span><span class="sxs-lookup"><span data-stu-id="81325-120">Configure the pull client LCM</span></span>

<span data-ttu-id="81325-121">L’exécution de l’un des exemples ci-dessous crée un dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="81325-121">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="81325-122">Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="81325-122">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="81325-123">Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="81325-123">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="81325-124">Exemple :</span><span class="sxs-lookup"><span data-stu-id="81325-124">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="81325-125">ID de configuration</span><span class="sxs-lookup"><span data-stu-id="81325-125">Configuration ID</span></span>

<span data-ttu-id="81325-126">Les exemples ci-dessous affectent à la propriété **ConfigurationID** du Gestionnaire de configuration local un **GUID** précédemment créé à cet effet.</span><span class="sxs-lookup"><span data-stu-id="81325-126">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="81325-127">Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="81325-127">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="81325-128">Le fichier MOF de configuration sur le serveur collecteur doit être nommé `ConfigurationID.mof`, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="81325-128">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="81325-129">Pour plus d’informations, consultez [Publier des configurations vers un serveur Pull (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="81325-129">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="81325-130">Vous pouvez créer un **GUID** aléatoire à l’aide de l’exemple ci-dessous, ou en utilisant l’applet de commande [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).</span><span class="sxs-lookup"><span data-stu-id="81325-130">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="81325-131">Pour plus d’informations sur l’utilisation des **GUID** dans votre environnement, consultez [Planifier les GUID](secureserver.md#guids).</span><span class="sxs-lookup"><span data-stu-id="81325-131">For more information about using **Guids** in your environment, see [Plan for Guids](secureserver.md#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="81325-132">Configurer un client Pull pour télécharger des configurations</span><span class="sxs-lookup"><span data-stu-id="81325-132">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="81325-133">Chaque client doit être configuré en mode **Pull** et il faut lui fournir l’URL du serveur Pull où sa configuration est stockée.</span><span class="sxs-lookup"><span data-stu-id="81325-133">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="81325-134">Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="81325-134">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="81325-135">Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration que vous décorez avec l’attribut **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="81325-135">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="81325-136">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="81325-136">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="81325-137">Serveur Pull DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="81325-137">HTTP DSC Pull Server</span></span>

<span data-ttu-id="81325-138">Le script suivant configure le gestionnaire de configuration local pour extraire les configurations d’un serveur nommé « CONTOSO-PullSrv ».</span><span class="sxs-lookup"><span data-stu-id="81325-138">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="81325-139">Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="81325-139">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="81325-140">**ServerUrl** spécifie l’URL de l’extraction DSC</span><span class="sxs-lookup"><span data-stu-id="81325-140">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="81325-141">Partage SMB</span><span class="sxs-lookup"><span data-stu-id="81325-141">SMB Share</span></span>

<span data-ttu-id="81325-142">Le script suivant configure le Gestionnaire de configuration local de façon à extraire des configurations du partage SMB `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="81325-142">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="81325-143">Dans le script, le bloc **ConfigurationRepositoryShare** définit le serveur Pull, qui dans le cas présent est simplement un partage SMB.</span><span class="sxs-lookup"><span data-stu-id="81325-143">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="81325-144">Configurer un client Pull pour télécharger des ressources</span><span class="sxs-lookup"><span data-stu-id="81325-144">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="81325-145">Si vous spécifiez uniquement un bloc **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** dans votre configuration du Gestionnaire de configuration local (comme dans les exemples précédents), le client Pull extrait les ressources à partir du même emplacement que celui où il récupère ses configurations.</span><span class="sxs-lookup"><span data-stu-id="81325-145">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="81325-146">Vous pouvez également spécifier des emplacements distincts pour les ressources.</span><span class="sxs-lookup"><span data-stu-id="81325-146">You can also specify separate locations for resources.</span></span> <span data-ttu-id="81325-147">Pour spécifier un emplacement de ressources en tant que serveur distinct, utilisez le bloc **ResourceRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="81325-147">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="81325-148">Pour spécifier un emplacement de ressources en tant que partage SMB, utilisez le bloc **ResourceRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="81325-148">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="81325-149">Vous pouvez combiner **ConfigurationRepositoryWeb** avec **ResourceRepositoryShare** , ou **ConfigurationRepositoryShare** avec **ResourceRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="81325-149">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="81325-150">Aucun exemple de ce type de combinaison n’est fourni ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="81325-150">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="81325-151">Serveur Pull DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="81325-151">HTTP DSC Pull Server</span></span>

<span data-ttu-id="81325-152">La métaconfiguration suivante configure un client Pull pour qu’il obtienne sa configuration à partir de **CONTOSO-PullSrv** et ses ressources à partir de **CONTOSO-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="81325-152">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="81325-153">Partage SMB</span><span class="sxs-lookup"><span data-stu-id="81325-153">SMB Share</span></span>

<span data-ttu-id="81325-154">L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations à partir du partage SMB `\\SMBPullServer\Configurations` et les ressources à partir du partage SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="81325-154">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="81325-155">Télécharger automatiquement les ressources en mode Push</span><span class="sxs-lookup"><span data-stu-id="81325-155">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="81325-156">À compter de PowerShell 5.0, vos clients Pull peuvent télécharger des modules à partir d’un partage SMB, même quand ils sont configurés pour le mode **Push**.</span><span class="sxs-lookup"><span data-stu-id="81325-156">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="81325-157">C’est particulièrement utile dans les scénarios où vous ne souhaitez pas configurer de serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="81325-157">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="81325-158">Le bloc **ResourceRepositoryShare** peut être utilisé sans spécifier de **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="81325-158">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="81325-159">L’exemple suivant montre une métaconfiguration qui configure un client pour extraire des ressources à partir d’un partage SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="81325-159">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="81325-160">Quand une configuration est fournie au nœud par le biais d’une opération **PUSH** , il télécharge automatiquement toutes les ressources requises à partir du partage spécifié.</span><span class="sxs-lookup"><span data-stu-id="81325-160">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="81325-161">Configurer un client Pull pour signaler l’état</span><span class="sxs-lookup"><span data-stu-id="81325-161">Set up a Pull Client to report status</span></span>

<span data-ttu-id="81325-162">Par défaut, les nœuds n’envoient pas de rapports à un serveur Pull configuré.</span><span class="sxs-lookup"><span data-stu-id="81325-162">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="81325-163">Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports, mais vous devez créer un bloc **ReportRepositoryWeb** pour configurer les rapports.</span><span class="sxs-lookup"><span data-stu-id="81325-163">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="81325-164">Serveur Pull DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="81325-164">HTTP DSC Pull Server</span></span>

<span data-ttu-id="81325-165">L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations et les ressources, et à envoyer des données de rapport à un seul serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="81325-165">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="81325-166">Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="81325-166">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="81325-167">Un serveur de rapports ne peut pas être un serveur SMB.</span><span class="sxs-lookup"><span data-stu-id="81325-167">A report server cannot be an SMB server.</span></span> <span data-ttu-id="81325-168">La métaconfiguration suivante configure un client collecteur de façon à obtenir sa configuration de **CONTOSO-PullSrv** et ses ressources de **CONTOSO-ResourceSrv** , et à envoyer des rapports d’état à **CONTOSO-ReportSrv** :</span><span class="sxs-lookup"><span data-stu-id="81325-168">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv** , and to send status reports to **CONTOSO-ReportSrv** :</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="81325-169">Partage SMB</span><span class="sxs-lookup"><span data-stu-id="81325-169">SMB Share</span></span>

<span data-ttu-id="81325-170">Un serveur de rapports ne peut pas être un partage SMB.</span><span class="sxs-lookup"><span data-stu-id="81325-170">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="81325-171">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="81325-171">Next Steps</span></span>

<span data-ttu-id="81325-172">Une fois le client Pull configuré, vous pouvez utiliser les guides suivants pour effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="81325-172">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="81325-173">Publier des configurations vers un serveur Pull (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="81325-173">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="81325-174">Empaqueter et charger des ressources dans un serveur Pull (v4)</span><span class="sxs-lookup"><span data-stu-id="81325-174">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="81325-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81325-175">See Also</span></span>

- [<span data-ttu-id="81325-176">Configuration d’un client collecteur à l’aide du nom de configuration</span><span class="sxs-lookup"><span data-stu-id="81325-176">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
