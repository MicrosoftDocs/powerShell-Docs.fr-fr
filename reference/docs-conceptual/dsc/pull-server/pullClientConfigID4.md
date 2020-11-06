---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Configurer un client Pull à l’aide d’ID de configuration dans PowerShell 4.0
description: Cet article explique comment configurer un client Pull à l’aide d’ID de configuration dans PowerShell 4.0
ms.openlocfilehash: 2a3d7b79f29030620cddc2b2131cb4432e41e4eb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649012"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="be595-104">Configurer un client Pull à l’aide d’ID de configuration dans PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="be595-104">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="be595-105">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="be595-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be595-106">Le serveur collecteur (fonctionnalité Windows *Service DSC* ) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="be595-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="be595-107">Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="be595-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="be595-108">Avant de configurer un client Pull, vous devez configurer un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="be595-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="be595-109">Bien que cet ordre ne soit pas obligatoire, il facilite le dépannage et vous permet de vous assurer que l’inscription a réussi.</span><span class="sxs-lookup"><span data-stu-id="be595-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="be595-110">Pour configurer un serveur Pull, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="be595-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="be595-111">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="be595-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="be595-112">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="be595-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="be595-113">Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état.</span><span class="sxs-lookup"><span data-stu-id="be595-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="be595-114">Les sections suivantes montrent comment configurer un client Pull avec un partage SMB ou un serveur Pull DSC HTTP.</span><span class="sxs-lookup"><span data-stu-id="be595-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="be595-115">Quand le Gestionnaire de configuration local du nœud est actualisé, il contacte l’emplacement configuré pour télécharger toutes les configurations affectées.</span><span class="sxs-lookup"><span data-stu-id="be595-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="be595-116">Si des ressources requises n’existent pas sur le nœud, il les télécharge automatiquement à partir de l’emplacement configuré.</span><span class="sxs-lookup"><span data-stu-id="be595-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="be595-117">Si le nœud est configuré avec un [serveur de rapports](reportServer.md), il signale ensuite l’état de l’opération.</span><span class="sxs-lookup"><span data-stu-id="be595-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="be595-118">Configurer le Gestionnaire de configuration local du client Pull</span><span class="sxs-lookup"><span data-stu-id="be595-118">Configure the pull client LCM</span></span>

<span data-ttu-id="be595-119">L’exécution de l’un des exemples ci-dessous crée un dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="be595-119">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="be595-120">Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="be595-120">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="be595-121">Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="be595-121">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="be595-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="be595-122">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="be595-123">ID de configuration</span><span class="sxs-lookup"><span data-stu-id="be595-123">Configuration ID</span></span>

<span data-ttu-id="be595-124">Les exemples ci-dessous affectent à la propriété **ConfigurationID** du Gestionnaire de configuration local un **GUID** précédemment créé à cet effet.</span><span class="sxs-lookup"><span data-stu-id="be595-124">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="be595-125">Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="be595-125">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="be595-126">Le fichier MOF de configuration sur le serveur collecteur doit être nommé `ConfigurationID.mof`, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="be595-126">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="be595-127">Pour plus d’informations, consultez [Publier des configurations vers un serveur Pull (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="be595-127">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="be595-128">Vous pouvez créer un **GUID** aléatoire à l’aide de l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="be595-128">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="be595-129">Configurer un client Pull pour télécharger des configurations</span><span class="sxs-lookup"><span data-stu-id="be595-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="be595-130">Chaque client doit être configuré en mode **Pull** et il faut lui fournir l’URL du serveur Pull où sa configuration est stockée.</span><span class="sxs-lookup"><span data-stu-id="be595-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="be595-131">Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="be595-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="be595-132">Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration, avec un bloc **LocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="be595-132">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="be595-133">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="be595-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="be595-134">Serveur Pull DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="be595-134">HTTP DSC Pull Server</span></span>

<span data-ttu-id="be595-135">Si le serveur Pull est configuré comme un service web, définissez **DownloadManagerName** sur **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="be595-135">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="be595-136">**WebDownloadManager** requiert que vous spécifiiez une propriété **ServerUrl** pour la clé **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="be595-136">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="be595-137">Vous pouvez également spécifier une valeur pour **AllowUnsecureConnection** , comme dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="be595-137">You can also specify a value for **AllowUnsecureConnection** , as in the example below.</span></span> <span data-ttu-id="be595-138">Le script suivant configure le gestionnaire de configuration local de façon à extraire des configurations d’un serveur nommé « PullServer ».</span><span class="sxs-lookup"><span data-stu-id="be595-138">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="be595-139">Partage SMB</span><span class="sxs-lookup"><span data-stu-id="be595-139">SMB Share</span></span>

<span data-ttu-id="be595-140">Si le serveur collecteur est configuré comme un partage de fichiers SMB au lieu d’un service web, vous spécifiez **DownloadManagerName** sur **DscFileDownloadManager** au lieu de **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="be595-140">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="be595-141">**DscFileDownloadManager** requiert que vous spécifiiez une propriété **SourcePath** dans **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="be595-141">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="be595-142">Le script suivant configure le gestionnaire de configuration local de façon à extraire d’un partage SMB nommé « SmbDscShare » sur un serveur nommé « CONTOSO-SERVER ».</span><span class="sxs-lookup"><span data-stu-id="be595-142">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="be595-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="be595-143">Next Steps</span></span>

<span data-ttu-id="be595-144">Une fois le client Pull configuré, vous pouvez utiliser les guides suivants pour effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="be595-144">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="be595-145">Publier des configurations vers un serveur Pull (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="be595-145">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="be595-146">Empaqueter et charger des ressources dans un serveur Pull (v4)</span><span class="sxs-lookup"><span data-stu-id="be595-146">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="be595-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be595-147">See Also</span></span>

- [<span data-ttu-id="be595-148">Configurer un serveur collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="be595-148">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="be595-149">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="be595-149">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
