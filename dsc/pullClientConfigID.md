---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configuration d’un client collecteur à l’aide de l’ID de configuration"
ms.openlocfilehash: bb14bff95c626b65e2d0d0072c39e4c571cea4b0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="e3b68-103">Configuration d’un client collecteur à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="e3b68-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="e3b68-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e3b68-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e3b68-105">Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL où contacter le serveur collecteur pour obtenir des configurations.</span><span class="sxs-lookup"><span data-stu-id="e3b68-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="e3b68-106">Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e3b68-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="e3b68-107">Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration que vous décorez avec l’attribut **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="e3b68-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="e3b68-108">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="e3b68-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="e3b68-109">**Remarque** : Cette rubrique s’applique à PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="e3b68-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="e3b68-110">Pour des informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="e3b68-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="e3b68-111">Le script suivant configure le gestionnaire de configuration local pour extraire les configurations d’un serveur nommé « CONTOSO-PullSrv ».</span><span class="sxs-lookup"><span data-stu-id="e3b68-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="e3b68-112">Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="e3b68-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="e3b68-113">Paramètre **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="e3b68-113">The **ServerURL**</span></span>

<span data-ttu-id="e3b68-114">Quand le script s’exécute, il crée un dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="e3b68-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="e3b68-115">Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="e3b68-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="e3b68-116">Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="e3b68-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="e3b68-117">Par exemple : `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="e3b68-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="e3b68-118">ID de configuration</span><span class="sxs-lookup"><span data-stu-id="e3b68-118">Configuration ID</span></span>

<span data-ttu-id="e3b68-119">Le script définit la propriété **ConfigurationID** du gestionnaire de configuration local sur un GUID déjà créé à cet effet (vous pouvez créer un GUID à l’aide de l’applet de commande **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="e3b68-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="e3b68-120">Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="e3b68-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="e3b68-121">Le fichier MOF de configuration sur le serveur collecteur doit être nommé _ConfigurationID_.mof, où _ConfigurationID_ est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="e3b68-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="e3b68-122">Serveur collecteur SMB</span><span class="sxs-lookup"><span data-stu-id="e3b68-122">SMB pull server</span></span>

<span data-ttu-id="e3b68-123">Pour configurer un client de façon à extraire des configurations d’un serveur SMB, utilisez un bloc **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="e3b68-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="e3b68-124">Dans un bloc **ConfigurationRepositoryShare**, vous spécifiez le chemin du serveur en définissant la propriété **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="e3b68-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="e3b68-125">La métaconfiguration suivante configure le nœud cible de façon à extraire des configurations d’un serveur collecteur SMB nommé **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="e3b68-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="e3b68-126">Serveurs de ressources et de rapports</span><span class="sxs-lookup"><span data-stu-id="e3b68-126">Resource and report servers</span></span>

<span data-ttu-id="e3b68-127">Si vous spécifiez uniquement un bloc **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** dans votre configuration du gestionnaire de configuration local (comme dans l’exemple précédent), le client collecteur extrait des ressources du serveur spécifié, mais il ne lui envoie pas de rapport.</span><span class="sxs-lookup"><span data-stu-id="e3b68-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="e3b68-128">Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports, mais vous devez créer un bloc **ReportRepositoryWeb** pour configurer les rapports.</span><span class="sxs-lookup"><span data-stu-id="e3b68-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span> 

<span data-ttu-id="e3b68-129">L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations et les ressources, et à envoyer des données de rapport à un seul serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="e3b68-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="e3b68-130">Vous pouvez également spécifier différents serveurs collecteurs pour les ressources et les rapports.</span><span class="sxs-lookup"><span data-stu-id="e3b68-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="e3b68-131">Pour spécifier un serveur de ressources, vous utilisez un bloc **ResourceRepositoryWeb** (pour un serveur collecteur web) ou **ResourceRepositoryShare** (pour un serveur collecteur SMB).</span><span class="sxs-lookup"><span data-stu-id="e3b68-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="e3b68-132">Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="e3b68-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="e3b68-133">Un serveur de rapports ne peut pas être un serveur SMB.</span><span class="sxs-lookup"><span data-stu-id="e3b68-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="e3b68-134">La métaconfiguration suivante configure un client collecteur de façon à obtenir sa configuration de **CONTOSO-PullSrv** et ses ressources de **CONTOSO-ResourceSrv**, et à envoyer des rapports d’état à **CONTOSO-ReportSrv** :</span><span class="sxs-lookup"><span data-stu-id="e3b68-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e3b68-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3b68-135">See Also</span></span>

* [<span data-ttu-id="e3b68-136">Configuration d’un client collecteur à l’aide du nom de configuration</span><span class="sxs-lookup"><span data-stu-id="e3b68-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

