---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configurer un Client collecteur à l’aide de noms de Configuration dans PowerShell 5.0 et versions ultérieures
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401786"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="54369-103">Configurer un Client collecteur à l’aide de noms de Configuration dans PowerShell 5.0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="54369-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="54369-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="54369-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54369-105">Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="54369-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="54369-106">Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="54369-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="54369-107">Avant de configurer un client collecteur, vous devez configurer un serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="54369-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="54369-108">Bien que cette commande n’est pas obligatoire, il facilite le dépannage et vous permet de s’assurer que l’inscription a réussi.</span><span class="sxs-lookup"><span data-stu-id="54369-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="54369-109">Pour configurer un serveur collecteur, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="54369-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="54369-110">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="54369-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="54369-111">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="54369-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="54369-112">Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état.</span><span class="sxs-lookup"><span data-stu-id="54369-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="54369-113">Les sections suivantes vous montrent comment configurer un client collecteur avec un partage SMB ou un serveur d’extraction DSC HTTP.</span><span class="sxs-lookup"><span data-stu-id="54369-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="54369-114">Lorsque Gestionnaire de configuration local du nœud est actualisé, il vous recontacte pour l’emplacement configuré pour télécharger toutes les configurations sont affectées.</span><span class="sxs-lookup"><span data-stu-id="54369-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="54369-115">Si toutes les ressources requises n’existent pas sur le nœud, il les télécharge automatiquement à partir de l’emplacement configuré.</span><span class="sxs-lookup"><span data-stu-id="54369-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="54369-116">Si le nœud est configuré avec un [serveur de rapports](reportServer.md), il sera ensuite l’état de l’opération.</span><span class="sxs-lookup"><span data-stu-id="54369-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="54369-117">**Remarque** : Cette rubrique s’applique à PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="54369-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="54369-118">Pour plus d’informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [configurer un client collecteur à l’aide des ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="54369-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="54369-119">Configurer le client d’extraction LCM</span><span class="sxs-lookup"><span data-stu-id="54369-119">Configure the pull client LCM</span></span>

<span data-ttu-id="54369-120">L’exécution d’un des exemples ci-dessous crée un nouveau dossier de sortie nommé **PullClientConfigName** et y place un fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="54369-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="54369-121">Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="54369-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="54369-122">Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="54369-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="54369-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="54369-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="54369-124">Nom de la configuration</span><span class="sxs-lookup"><span data-stu-id="54369-124">Configuration Name</span></span>

<span data-ttu-id="54369-125">Les exemples ci-dessous définissent la propriété **ConfigurationName** du Gestionnaire de configuration local pour le nom d’une Configuration précédemment compilée, créée à cet effet.</span><span class="sxs-lookup"><span data-stu-id="54369-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="54369-126">Le **ConfigurationName** est ce que le Gestionnaire de configuration local utilise pour rechercher la configuration appropriée sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="54369-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="54369-127">Le fichier MOF de configuration sur le serveur collecteur doit être nommé `<ConfigurationName>.mof`, dans ce cas, « ClientConfig.mof ».</span><span class="sxs-lookup"><span data-stu-id="54369-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="54369-128">Pour plus d’informations, consultez [publier les Configurations à un serveur collecteur (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="54369-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="54369-129">Configurer un Client collecteur à télécharger les Configurations</span><span class="sxs-lookup"><span data-stu-id="54369-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="54369-130">Chaque client doit être configuré dans **extraction** mode et l’url du serveur collecteur où sa configuration est stockée.</span><span class="sxs-lookup"><span data-stu-id="54369-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="54369-131">Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="54369-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="54369-132">Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration que vous décorez avec l’attribut **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="54369-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="54369-133">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="54369-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="54369-134">Le script suivant configure le gestionnaire de configuration local pour extraire les configurations d’un serveur nommé « CONTOSO-PullSrv ».</span><span class="sxs-lookup"><span data-stu-id="54369-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="54369-135">Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="54369-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="54369-136">La propriété **ServerURL** spécifie le point de terminaison pour le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="54369-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="54369-137">La propriété **RegistrationKey** est une clé partagée entre tous les nœuds clients d’un serveur collecteur et ce serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="54369-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="54369-138">La même valeur est stockée dans un fichier sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="54369-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="54369-139">**Remarque** : Clés d’enregistrement fonctionnent uniquement avec **web** serveurs collecteurs.</span><span class="sxs-lookup"><span data-stu-id="54369-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="54369-140">Vous devez encore utiliser **ConfigurationID** avec un serveur Pull **SMB**.</span><span class="sxs-lookup"><span data-stu-id="54369-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="54369-141">Pour plus d’informations sur la configuration d’un serveur collecteur à l’aide de **ConfigurationID**, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="54369-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="54369-142">La propriété **ConfigurationNames** est un tableau qui spécifie les noms des configurations destinées au nœud client.</span><span class="sxs-lookup"><span data-stu-id="54369-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="54369-143">**Remarque :** Si vous spécifiez plusieurs valeurs dans **ConfigurationNames**, vous devez également spécifier des blocs **PartialConfiguration** dans votre configuration.</span><span class="sxs-lookup"><span data-stu-id="54369-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="54369-144">Pour plus d’informations sur les configurations partielles, voir [Configurations partielles du service de configuration d’état souhaité PowerShell](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="54369-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="54369-145">Configurer un Client collecteur pour télécharger des ressources</span><span class="sxs-lookup"><span data-stu-id="54369-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="54369-146">Si vous spécifiez uniquement un **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquer dans votre configuration du LCM (comme dans l’exemple précédent), le client d’extraction extraira les ressources du même emplacement où sont stockés vos fichiers « .mof ».</span><span class="sxs-lookup"><span data-stu-id="54369-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="54369-147">Vous pouvez également spécifier différents emplacements où les clients peuvent télécharger des ressources.</span><span class="sxs-lookup"><span data-stu-id="54369-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="54369-148">Pour spécifier un serveur de ressources, vous utilisez un bloc **ResourceRepositoryWeb** (pour un serveur collecteur web) ou **ResourceRepositoryShare** (pour un serveur collecteur SMB).</span><span class="sxs-lookup"><span data-stu-id="54369-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="54369-149">L’exemple suivant montre une métaconfiguration qui configure un client à télécharger les configurations à partir d’un serveur collecteur et les ressources à partir d’un partage SMB.</span><span class="sxs-lookup"><span data-stu-id="54369-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="54369-150">Configurer un Client collecteur pour signaler l’état</span><span class="sxs-lookup"><span data-stu-id="54369-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="54369-151">Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports.</span><span class="sxs-lookup"><span data-stu-id="54369-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="54369-152">Création de rapports n’est pas configurée pour les clients par défaut.</span><span class="sxs-lookup"><span data-stu-id="54369-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="54369-153">Pour configurer un client pour signaler l’état, vous devez créer un **ReportRepositoryWeb** bloc.</span><span class="sxs-lookup"><span data-stu-id="54369-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="54369-154">L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations et les ressources, et à envoyer des données de rapport à un seul serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="54369-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="54369-155">Un serveur de rapports ne peut pas être un partage SMB.</span><span class="sxs-lookup"><span data-stu-id="54369-155">A report server cannot be an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="54369-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54369-156">See Also</span></span>

* [<span data-ttu-id="54369-157">Configuration d’un client collecteur à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="54369-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="54369-158">Configuration d’un serveur collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="54369-158">Setting up a DSC web pull server</span></span>](pullServer.md)
