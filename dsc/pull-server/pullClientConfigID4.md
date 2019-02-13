---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurer un Client collecteur à l’aide des ID de Configuration dans PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678293"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="c5696-103">Configurer un Client collecteur à l’aide des ID de Configuration dans PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="c5696-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="c5696-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c5696-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5696-105">Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="c5696-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="c5696-106">Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="c5696-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="c5696-107">Avant de configurer un client collecteur, vous devez configurer un serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="c5696-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="c5696-108">Bien que cette commande ne soit pas obligatoire, elle facilite le dépannage et vous permet de vous assurer que l’inscription a réussi.</span><span class="sxs-lookup"><span data-stu-id="c5696-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="c5696-109">Pour configurer un serveur collecteur, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="c5696-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="c5696-110">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="c5696-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="c5696-111">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="c5696-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="c5696-112">Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état.</span><span class="sxs-lookup"><span data-stu-id="c5696-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="c5696-113">Les sections suivantes vous montrent comment configurer un client collecteur avec un partage SMB ou un serveur d’extraction DSC HTTP.</span><span class="sxs-lookup"><span data-stu-id="c5696-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="c5696-114">Lorsque Gestionnaire de configuration local du nœud est actualisé, il vous recontacte pour l’emplacement configuré pour télécharger toutes les configurations sont affectées.</span><span class="sxs-lookup"><span data-stu-id="c5696-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="c5696-115">Si toutes les ressources requises n’existent pas sur le nœud, il les télécharge automatiquement à partir de l’emplacement configuré.</span><span class="sxs-lookup"><span data-stu-id="c5696-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="c5696-116">Si le nœud est configuré avec un [serveur de rapports](reportServer.md), il sera ensuite l’état de l’opération.</span><span class="sxs-lookup"><span data-stu-id="c5696-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="c5696-117">Configurer le client d’extraction LCM</span><span class="sxs-lookup"><span data-stu-id="c5696-117">Configure the pull client LCM</span></span>

<span data-ttu-id="c5696-118">L’exécution d’un des exemples ci-dessous crée un nouveau dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="c5696-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="c5696-119">Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="c5696-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="c5696-120">Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="c5696-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="c5696-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c5696-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="c5696-122">ID de configuration</span><span class="sxs-lookup"><span data-stu-id="c5696-122">Configuration ID</span></span>

<span data-ttu-id="c5696-123">Les exemples ci-dessous ensemble la **ConfigurationID** propriété du Gestionnaire de configuration local à un **Guid** qui avait été précédemment créé à cet effet.</span><span class="sxs-lookup"><span data-stu-id="c5696-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="c5696-124">Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="c5696-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="c5696-125">Le fichier MOF de configuration sur le serveur collecteur doit être nommé `ConfigurationID.mof`, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="c5696-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="c5696-126">Pour plus d’informations, consultez [publier les Configurations à un serveur collecteur (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="c5696-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="c5696-127">Vous pouvez créer un aléatoire **Guid** à l’aide de l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c5696-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="c5696-128">Configurer un Client collecteur à télécharger les Configurations</span><span class="sxs-lookup"><span data-stu-id="c5696-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="c5696-129">Chaque client doit être configuré dans **extraction** mode et l’url du serveur collecteur où sa configuration est stockée.</span><span class="sxs-lookup"><span data-stu-id="c5696-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="c5696-130">Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c5696-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="c5696-131">Pour configurer le LCM, vous créez un type spécial de configuration, avec un **LocalConfigurationManager** bloc.</span><span class="sxs-lookup"><span data-stu-id="c5696-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="c5696-132">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="c5696-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="c5696-133">Serveur collecteur de DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="c5696-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="c5696-134">Si le serveur collecteur est configuré comme un service web, vous définissez le **DownloadManagerName** à **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="c5696-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="c5696-135">Le **WebDownloadManager** requiert que vous spécifiiez un **ServerUrl** à la **DownloadManagerCustomData** clé.</span><span class="sxs-lookup"><span data-stu-id="c5696-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="c5696-136">Vous pouvez également spécifier une valeur pour **AllowUnsecureConnection**, comme dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c5696-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="c5696-137">Le script suivant configure le gestionnaire de configuration local de façon à extraire des configurations d’un serveur nommé « PullServer ».</span><span class="sxs-lookup"><span data-stu-id="c5696-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

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

## <a name="smb-share"></a><span data-ttu-id="c5696-138">Partage SMB</span><span class="sxs-lookup"><span data-stu-id="c5696-138">SMB Share</span></span>

<span data-ttu-id="c5696-139">Si le serveur collecteur est configuré comme un partage de fichiers SMB, plutôt qu’un service web, vous définissez le **DownloadManagerName** à **DscFileDownloadManager** plutôt que **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="c5696-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="c5696-140">Le **DscFileDownloadManager** requiert que vous spécifiiez un **SourcePath** propriété dans le **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="c5696-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="c5696-141">Le script suivant configure le gestionnaire de configuration local de façon à extraire d’un partage SMB nommé « SmbDscShare » sur un serveur nommé « CONTOSO-SERVER ».</span><span class="sxs-lookup"><span data-stu-id="c5696-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="c5696-142">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c5696-142">Next Steps</span></span>

<span data-ttu-id="c5696-143">Une fois que le client d’extraction a été configuré, vous pouvez utiliser les guides suivants pour effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5696-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="c5696-144">Publier des configurations vers un serveur Pull (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="c5696-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="c5696-145">Empaqueter et charger des ressources vers un serveur Pull (v4)</span><span class="sxs-lookup"><span data-stu-id="c5696-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="c5696-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5696-146">See Also</span></span>

- [<span data-ttu-id="c5696-147">Configurer un serveur de collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="c5696-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="c5696-148">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="c5696-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
