---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuration d’un client collecteur à l’aide du nom de configuration
ms.openlocfilehash: d71376d84b9d4b0e74fdccab4b9249b2ca4263cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188089"
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="57c7a-103">Configuration d’un client collecteur à l’aide du nom de configuration</span><span class="sxs-lookup"><span data-stu-id="57c7a-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="57c7a-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="57c7a-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57c7a-105">Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="57c7a-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="57c7a-106">Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="57c7a-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="57c7a-107">Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL où contacter le serveur collecteur pour obtenir des configurations.</span><span class="sxs-lookup"><span data-stu-id="57c7a-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="57c7a-108">Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="57c7a-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="57c7a-109">Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration que vous décorez avec l’attribut **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="57c7a-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="57c7a-110">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="57c7a-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="57c7a-111">**Remarque** : Cette rubrique s’applique à PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="57c7a-111">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="57c7a-112">Pour des informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="57c7a-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="57c7a-113">Le script suivant configure le gestionnaire de configuration local de façon à extraire des configurations d’un serveur nommé « CONTOSO-PullSrv » :</span><span class="sxs-lookup"><span data-stu-id="57c7a-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

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

<span data-ttu-id="57c7a-114">Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="57c7a-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="57c7a-115">La propriété **ServerURL** spécifie le point de terminaison pour le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="57c7a-115">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="57c7a-116">La propriété **RegistrationKey** est une clé partagée entre tous les nœuds clients d’un serveur collecteur et ce serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="57c7a-116">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="57c7a-117">La même valeur est stockée dans un fichier sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="57c7a-117">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="57c7a-118">La propriété **ConfigurationNames** est un tableau qui spécifie les noms des configurations destinées au nœud client.</span><span class="sxs-lookup"><span data-stu-id="57c7a-118">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="57c7a-119">Sur le serveur collecteur, le fichier MOF de configuration pour ce nœud client doit être nommé *ConfigurationNames*.mof, où *ConfigurationNames* correspond à la valeur de la propriété **ConfigurationNames** que vous définissez dans cette métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="57c7a-119">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="57c7a-120">**Remarque :** Si vous spécifiez plusieurs valeurs dans **ConfigurationNames**, vous devez également spécifier des blocs **PartialConfiguration** dans votre configuration.</span><span class="sxs-lookup"><span data-stu-id="57c7a-120">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="57c7a-121">Pour plus d’informations sur les configurations partielles, voir [Configurations partielles du service de configuration d’état souhaité PowerShell](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="57c7a-121">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="57c7a-122">Quand le script s’exécute, il crée un dossier de sortie nommé **PullClientConfigNames** et y place un fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="57c7a-122">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="57c7a-123">Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="57c7a-123">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="57c7a-124">Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="57c7a-124">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="57c7a-125">**Remarque** : Les clés d’enregistrement fonctionnent uniquement avec les serveurs collecteurs web.</span><span class="sxs-lookup"><span data-stu-id="57c7a-125">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="57c7a-126">Vous devez encore utiliser **ConfigurationID** avec un serveur collecteur SMB.</span><span class="sxs-lookup"><span data-stu-id="57c7a-126">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="57c7a-127">Pour plus d’informations sur la configuration d’un serveur collecteur à l’aide de **ConfigurationID**, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="57c7a-127">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="57c7a-128">Serveurs de ressources et de rapports</span><span class="sxs-lookup"><span data-stu-id="57c7a-128">Resource and report servers</span></span>

<span data-ttu-id="57c7a-129">Si vous spécifiez uniquement un bloc **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** dans votre configuration du gestionnaire de configuration local (comme dans l’exemple précédent), le client collecteur extrait des ressources du serveur spécifié, mais il ne lui envoie pas de rapport.</span><span class="sxs-lookup"><span data-stu-id="57c7a-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="57c7a-130">Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports, mais vous devez créer un bloc **ReportRepositoryWeb** pour configurer les rapports.</span><span class="sxs-lookup"><span data-stu-id="57c7a-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="57c7a-131">L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations et les ressources, et à envoyer des données de rapport à un seul serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="57c7a-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="57c7a-132">Vous pouvez également spécifier différents serveurs collecteurs pour les ressources et les rapports.</span><span class="sxs-lookup"><span data-stu-id="57c7a-132">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="57c7a-133">Pour spécifier un serveur de ressources, vous utilisez un bloc **ResourceRepositoryWeb** (pour un serveur collecteur web) ou **ResourceRepositoryShare** (pour un serveur collecteur SMB).</span><span class="sxs-lookup"><span data-stu-id="57c7a-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="57c7a-134">Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="57c7a-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="57c7a-135">Un serveur de rapports ne peut pas être un serveur SMB.</span><span class="sxs-lookup"><span data-stu-id="57c7a-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="57c7a-136">La métaconfiguration suivante configure un client collecteur de façon à obtenir sa configuration de **CONTOSO-PullSrv** et ses ressources de **CONTOSO-ResourceSrv**, et à envoyer des rapports d’état à **CONTOSO-ReportSrv** :</span><span class="sxs-lookup"><span data-stu-id="57c7a-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="57c7a-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57c7a-137">See Also</span></span>

* [<span data-ttu-id="57c7a-138">Configuration d’un client collecteur à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="57c7a-138">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="57c7a-139">Configuration d’un serveur collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="57c7a-139">Setting up a DSC web pull server</span></span>](pullServer.md)