---
ms.date: 01/08/2020
keywords: dsc,powershell,configuration,installation
title: Service collecteur DSC
ms.openlocfilehash: 821f183c91e805154323f9f6a42f7f5006499182
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500721"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="735a8-103">Service collecteur Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="735a8-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="735a8-104">Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="735a8-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="735a8-105">Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="735a8-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="735a8-106">Le gestionnaire de configuration local peut être centralisée par une solution de service collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-106">Local Configuration Manager (LCM) can be centrally managed by a Pull Service solution.</span></span> <span data-ttu-id="735a8-107">Lorsque vous utilisez cette approche, le nœud géré est inscrit auprès d’un service et se voit affecter une configuration dans les paramètres LCM.</span><span class="sxs-lookup"><span data-stu-id="735a8-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span> <span data-ttu-id="735a8-108">La configuration et toutes les ressources DSC nécessaires en tant que dépendances de la configuration sont téléchargées sur l’ordinateur et utilisées par le Gestionnaire de configuration local pour gérer la configuration.</span><span class="sxs-lookup"><span data-stu-id="735a8-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span> <span data-ttu-id="735a8-109">Des informations sur l’état de l’ordinateur géré sont chargées sur le service pour créer des rapports.</span><span class="sxs-lookup"><span data-stu-id="735a8-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span> <span data-ttu-id="735a8-110">Ce concept est appelé « service collecteur ».</span><span class="sxs-lookup"><span data-stu-id="735a8-110">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="735a8-111">Les options actuelles du service d’extraction sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="735a8-111">The current options for pull service include:</span></span>

- <span data-ttu-id="735a8-112">Service de Configuration d’état souhaité d’Azure Automation</span><span class="sxs-lookup"><span data-stu-id="735a8-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="735a8-113">Service collecteur exécuté sur Windows Server</span><span class="sxs-lookup"><span data-stu-id="735a8-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="735a8-114">Solutions open source gérées par la communauté</span><span class="sxs-lookup"><span data-stu-id="735a8-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="735a8-115">Partage SMB</span><span class="sxs-lookup"><span data-stu-id="735a8-115">An SMB share</span></span>

<span data-ttu-id="735a8-116">L’échelle recommandée pour chaque solution est la suivante :</span><span class="sxs-lookup"><span data-stu-id="735a8-116">The recommended scale for each solution is as follows:</span></span>

|                   <span data-ttu-id="735a8-117">Solution</span><span class="sxs-lookup"><span data-stu-id="735a8-117">Solution</span></span>                   |              <span data-ttu-id="735a8-118">Nœuds clients</span><span class="sxs-lookup"><span data-stu-id="735a8-118">Client nodes</span></span>              |
| -------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="735a8-119">Serveur Windows Pull utilisant une base de données MDB/ESENT</span><span class="sxs-lookup"><span data-stu-id="735a8-119">Windows Pull Server using MDB/ESENT database</span></span> | <span data-ttu-id="735a8-120">Jusqu’à 500 nœuds</span><span class="sxs-lookup"><span data-stu-id="735a8-120">Up to 500 nodes</span></span>                        |
| <span data-ttu-id="735a8-121">Serveur Windows Pull utilisant une base de données SQL</span><span class="sxs-lookup"><span data-stu-id="735a8-121">Windows Pull Server using SQL database</span></span>       | <span data-ttu-id="735a8-122">Jusqu’à 3 500 nœuds</span><span class="sxs-lookup"><span data-stu-id="735a8-122">Up to 3500 nodes</span></span>                       |
| <span data-ttu-id="735a8-123">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="735a8-123">Azure Automation DSC</span></span>                         | <span data-ttu-id="735a8-124">Petits et grands environnements</span><span class="sxs-lookup"><span data-stu-id="735a8-124">Both small and large environments</span></span>      |

<span data-ttu-id="735a8-125">**La solution recommandée**, qui est à la fois l’option offrant le plus de fonctionnalités, est [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="735a8-125">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span> <span data-ttu-id="735a8-126">Aucune limite supérieure du nombre de nœuds par compte Automation n’a été identifiée.</span><span class="sxs-lookup"><span data-stu-id="735a8-126">An upper limit for number of nodes per Automation Account has not been identified.</span></span>

<span data-ttu-id="735a8-127">Le service Azure peut gérer les nœuds locaux dans des centres de données privés ou dans des clouds publics tels qu’Azure et AWS.</span><span class="sxs-lookup"><span data-stu-id="735a8-127">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span> <span data-ttu-id="735a8-128">Pour les environnements où les serveurs ne peut pas se connecter directement à Internet, envisagez de limiter le trafic sortant à la seule plage IP Azure publiée (voir [Plages d’adresses IP Azure Datacenter](https://www.microsoft.com/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="735a8-128">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="735a8-129">Fonctionnalités du service en ligne qui ne sont actuellement pas disponibles dans le service d’extraction sur Windows Server :</span><span class="sxs-lookup"><span data-stu-id="735a8-129">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="735a8-130">Toutes les données sont chiffrées, en transit comme au repos</span><span class="sxs-lookup"><span data-stu-id="735a8-130">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="735a8-131">Les certificats clients sont créés et gérés automatiquement</span><span class="sxs-lookup"><span data-stu-id="735a8-131">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="735a8-132">Magasin des secrets pour une gestion centralisée des [mots de passe/informations d’identification](/azure/automation/automation-credentials), ou des [variables](/azure/automation/automation-variables) telles que les noms des serveurs ou les chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="735a8-132">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="735a8-133">Gestion centralisée du nœud [configuration du LCM](../managing-nodes/metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="735a8-133">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="735a8-134">Assignation centralisée de configurations aux nœuds clients</span><span class="sxs-lookup"><span data-stu-id="735a8-134">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="735a8-135">Mise des modifications de la configuration en « groupes de contrôle de validité » pour effectuer des tests avant la production</span><span class="sxs-lookup"><span data-stu-id="735a8-135">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="735a8-136">Création de rapports graphiques</span><span class="sxs-lookup"><span data-stu-id="735a8-136">Graphical reporting</span></span>
  - <span data-ttu-id="735a8-137">Détails de l’état au niveau de la granularité de la ressource DSC</span><span class="sxs-lookup"><span data-stu-id="735a8-137">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="735a8-138">Messages d’erreur en clair des ordinateurs clients pour la résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="735a8-138">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="735a8-139">[Intégration à Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) pour les alertes, tâches automatisées, application Android/iOS pour les rapports et les alertes</span><span class="sxs-lookup"><span data-stu-id="735a8-139">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="735a8-140">Service collecteur DSC dans Windows Server</span><span class="sxs-lookup"><span data-stu-id="735a8-140">DSC pull service in Windows Server</span></span>

<span data-ttu-id="735a8-141">Il est possible de configurer un service collecteur pour l’exécuter sur Windows Server.</span><span class="sxs-lookup"><span data-stu-id="735a8-141">It is possible to configure a pull service to run on Windows Server.</span></span> <span data-ttu-id="735a8-142">Notez que la solution de service collecteur incluse dans Windows Server contient uniquement les fonctionnalités de stockage des configurations/modules à télécharger, et les fonctionnalités de capture de données de rapport dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="735a8-142">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data into a database.</span></span> <span data-ttu-id="735a8-143">Elle ne contient pas les nombreuses fonctionnalités offertes par le service dans Azure et n’est donc pas un bon outil pour évaluer la manière dont le service doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="735a8-143">It does not include many of the capabilities offered by the service in Azure and so, is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="735a8-144">Le service collecteur proposé dans Windows Server est un service web dans IIS qui utilise une interface OData pour mettre les fichiers de configuration DSC à la disposition des nœuds cibles quand ceux-ci en ont besoin.</span><span class="sxs-lookup"><span data-stu-id="735a8-144">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="735a8-145">Configuration requise pour utiliser un serveur collecteur :</span><span class="sxs-lookup"><span data-stu-id="735a8-145">Requirements for using a pull server:</span></span>

- <span data-ttu-id="735a8-146">Un serveur en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="735a8-146">A server running:</span></span>
  - <span data-ttu-id="735a8-147">WMF/PowerShell 4.0 ou version supérieure</span><span class="sxs-lookup"><span data-stu-id="735a8-147">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="735a8-148">Rôle serveur IIS</span><span class="sxs-lookup"><span data-stu-id="735a8-148">IIS server role</span></span>
  - <span data-ttu-id="735a8-149">Service DSC</span><span class="sxs-lookup"><span data-stu-id="735a8-149">DSC Service</span></span>
- <span data-ttu-id="735a8-150">Idéalement, des moyens de générer un certificat pour sécuriser les informations d’identification transmises au gestionnaire de configuration local sur les nœuds cibles</span><span class="sxs-lookup"><span data-stu-id="735a8-150">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="735a8-151">La meilleure façon de configurer Windows Server pour héberger un service collecteur est d’utiliser une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="735a8-151">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span> <span data-ttu-id="735a8-152">Vous trouverez ci-dessous un exemple de script.</span><span class="sxs-lookup"><span data-stu-id="735a8-152">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="735a8-153">Systèmes de base de données pris en charge</span><span class="sxs-lookup"><span data-stu-id="735a8-153">Supported database systems</span></span>

| <span data-ttu-id="735a8-154">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="735a8-154">WMF 4.0</span></span> |       <span data-ttu-id="735a8-155">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="735a8-155">WMF 5.0</span></span>        |       <span data-ttu-id="735a8-156">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="735a8-156">WMF 5.1</span></span>        | <span data-ttu-id="735a8-157">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="735a8-157">WMF 5.1 (Windows Server Insider Preview 17090)</span></span> |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| <span data-ttu-id="735a8-158">MDB</span><span class="sxs-lookup"><span data-stu-id="735a8-158">MDB</span></span>     | <span data-ttu-id="735a8-159">ESENT (par défaut), MDB</span><span class="sxs-lookup"><span data-stu-id="735a8-159">ESENT (Default), MDB</span></span> | <span data-ttu-id="735a8-160">ESENT (par défaut), MDB</span><span class="sxs-lookup"><span data-stu-id="735a8-160">ESENT (Default), MDB</span></span> | <span data-ttu-id="735a8-161">ESENT (par défaut), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="735a8-161">ESENT (Default), SQL Server, MDB</span></span>               |

<span data-ttu-id="735a8-162">À compter de la version 17090 de Windows Server, SQL Server est une option prise en charge du service collecteur (fonctionnalité Windows *Service DSC*).</span><span class="sxs-lookup"><span data-stu-id="735a8-162">Starting in release 17090 of Windows Server, SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="735a8-163">Vous disposez ainsi d’une nouvelle option pour mettre à l’échelle les grands environnements DSC qui n’ont pas été migrés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="735a8-163">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="735a8-164">La prise en charge de SQL Server ne sera pas ajoutée aux versions précédentes de WMF 5.1 (ou versions antérieures) et sera uniquement disponible dans les versions de Windows Server supérieures ou égales à 17090.</span><span class="sxs-lookup"><span data-stu-id="735a8-164">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="735a8-165">Pour configurer le serveur collecteur de manière à utiliser SQL Server, définissez **SqlProvider** sur `$true` et **SqlConnectionString** sur une chaîne de connexion SQL Server valide.</span><span class="sxs-lookup"><span data-stu-id="735a8-165">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="735a8-166">Pour plus d’informations, consultez [Chaînes de connexion SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="735a8-166">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="735a8-167">Pour obtenir un exemple de configuration de SQL Server avec **xDscWebService**, lisez d’abord [Utilisation de la ressource xDSCWebService](#using-the-xdscwebservice-resource), puis consultez l’exemple [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 sur GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="735a8-167">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="735a8-168">Utilisation de la ressource xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="735a8-168">Using the xDscWebService resource</span></span>

<span data-ttu-id="735a8-169">Le moyen le plus simple de configurer un serveur collecteur web consiste à utiliser la ressource **xDscWebService** qui se trouve dans le module **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="735a8-169">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="735a8-170">Les étapes suivantes expliquent comment utiliser la ressource dans une `Configuration` qui configure le service web.</span><span class="sxs-lookup"><span data-stu-id="735a8-170">The following steps explain how to use the resource in a `Configuration` that sets up the web service.</span></span>

1. <span data-ttu-id="735a8-171">Appelez l’applet de commande [Install-Module](/powershell/module/PowerShellGet/Install-Module) pour installer le module **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="735a8-171">Call the [Install-Module](/powershell/module/PowerShellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>

   > [!NOTE]
   > <span data-ttu-id="735a8-172">`Install-Module` est inclus dans le module **PowerShellGet** de PowerShell 5.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="735a8-172">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0 and higher.</span></span>

1. <span data-ttu-id="735a8-173">Obtenez un certificat SSL pour le serveur collecteur DSC auprès d’une autorité de certification approuvée, au sein de votre organisation ou auprès d’une autorité publique.</span><span class="sxs-lookup"><span data-stu-id="735a8-173">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="735a8-174">Le certificat reçu de l’autorité est généralement au format PFX.</span><span class="sxs-lookup"><span data-stu-id="735a8-174">The certificate received from the authority is usually in the PFX format.</span></span>
1. <span data-ttu-id="735a8-175">Installez le certificat sur le nœud qui sera le serveur DSC à l’emplacement par défaut, c’est-à-dire `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="735a8-175">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="735a8-176">Notez l’empreinte de certificat.</span><span class="sxs-lookup"><span data-stu-id="735a8-176">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="735a8-177">Sélectionnez un GUID à utiliser comme clé d’inscription.</span><span class="sxs-lookup"><span data-stu-id="735a8-177">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="735a8-178">Pour en générer un à l’aide de PowerShell, entrez ce qui suit à l’invite PowerShell et appuyez sur Entrée : `[guid]::newGuid()` ou `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="735a8-178">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="735a8-179">Cette clé est utilisée par les nœuds clients comme une clé partagée pour l’authentification lors de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="735a8-179">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="735a8-180">Pour plus d’informations, consultez la section Clé d’inscription ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="735a8-180">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="735a8-181">Dans PowerShell ISE, démarrez (<kbd>F5</kbd>) le script de configuration suivant (inclus dans le dossier du module **xPSDesiredStateConfiguration** en tant que `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="735a8-181">In the PowerShell ISE, start (<kbd>F5</kbd>) the following configuration script (included in the folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`) .</span></span> <span data-ttu-id="735a8-182">Ce script configure le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-182">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. <span data-ttu-id="735a8-183">Exécutez la configuration, en passant l’empreinte du certificat SSL comme paramètre **certificateThumbPrint** et une clé d’inscription GUID comme paramètre **RegistrationKey** :</span><span class="sxs-lookup"><span data-stu-id="735a8-183">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="735a8-184">Clé d’inscription</span><span class="sxs-lookup"><span data-stu-id="735a8-184">Registration Key</span></span>

<span data-ttu-id="735a8-185">Pour que les nœuds clients puissent s’inscrire auprès du serveur afin de pouvoir utiliser les noms de configuration au lieu de l’ID de configuration, une clé d’inscription, créée par la configuration ci-dessus, est enregistrée dans un fichier nommé `RegistrationKeys.txt` dans `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="735a8-185">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="735a8-186">La clé d’inscription fonctionne comme un secret partagé utilisé lors de l’inscription initiale par le client avec le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-186">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="735a8-187">Le client génère un certificat auto-signé qui est utilisé pour l’authentification unique auprès du serveur collecteur, une fois l’inscription terminée.</span><span class="sxs-lookup"><span data-stu-id="735a8-187">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="735a8-188">L’empreinte de ce certificat est stockée localement et associée à l’URL du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-188">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="735a8-189">Les clés d’inscription ne sont pas prises en charge dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="735a8-189">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="735a8-190">Pour configurer un nœud pour l’authentification auprès du serveur collecteur, la clé d’inscription doit se trouver dans la métaconfiguration de tous les nœuds cibles que vous prévoyez d’inscrire auprès de ce serveur.</span><span class="sxs-lookup"><span data-stu-id="735a8-190">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="735a8-191">Notez que la propriété **RegistrationKey** dans la métaconfiguration ci-dessous est supprimée une fois que l’ordinateur cible a été correctement inscrit, et que la valeur doit correspondre à celle stockée dans le fichier `RegistrationKeys.txt` sur le serveur collecteur (« 140a952b-b9d6-406b-b416-e0f759c9c0e4 » dans cet exemple).</span><span class="sxs-lookup"><span data-stu-id="735a8-191">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="735a8-192">Conservez la valeur de la clé d’inscription en lieu sûr, car elle permet d’inscrire n’importe quel ordinateur cible auprès du serveur.</span><span class="sxs-lookup"><span data-stu-id="735a8-192">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> <span data-ttu-id="735a8-193">La section **ReportServerWeb** permet d’envoyer les données de rapport au serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-193">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="735a8-194">Si la propriété **ConfigurationID** est absente du fichier de métaconfiguration, cela signifie implicitement que ce serveur collecteur prend en charge la version V2 du protocole du serveur collecteur et donc qu’une inscription initiale est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="735a8-194">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="735a8-195">Inversement, si la propriété **ConfigurationID** est présente, la version V1 du protocole du serveur collecteur est utilisée et il n’y a pas de traitement de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="735a8-195">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="735a8-196">Dans un scénario PUSH, la version actuelle contient un bogue qui demande de définir une propriété ConfigurationID dans le fichier de métaconfiguration pour les nœuds qui n’ont jamais été inscrits auprès d’un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="735a8-196">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="735a8-197">Cette opération permet de forcer le protocole du serveur collecteur V1 et d’éviter les messages d’échec d’inscription.</span><span class="sxs-lookup"><span data-stu-id="735a8-197">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="735a8-198">Placement des configurations et des ressources</span><span class="sxs-lookup"><span data-stu-id="735a8-198">Placing configurations and resources</span></span>

<span data-ttu-id="735a8-199">Une fois l’installation du serveur collecteur terminée, vous placez les modules et configurations à extraire par les nœuds cibles dans les dossiers définis par les propriétés **ConfigurationPath** et **ModulePath** de la configuration du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-199">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="735a8-200">Ces fichiers doivent se trouver dans un format spécifique afin que le serveur collecteur puisse les traiter correctement.</span><span class="sxs-lookup"><span data-stu-id="735a8-200">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="735a8-201">Format du package de module de ressources DSC</span><span class="sxs-lookup"><span data-stu-id="735a8-201">DSC resource module package format</span></span>

<span data-ttu-id="735a8-202">Chaque module de ressources doit être compressé et nommé selon le modèle suivant : `{Module Name}_{Module Version}.zip`</span><span class="sxs-lookup"><span data-stu-id="735a8-202">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="735a8-203">Par exemple, un module **xWebAdminstration** avec une version de module 3.1.2.0 est nommé `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="735a8-203">For example, a module named **xWebAdminstration** with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span> <span data-ttu-id="735a8-204">Chaque version d’un module doit être contenue dans un seul fichier zip.</span><span class="sxs-lookup"><span data-stu-id="735a8-204">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="735a8-205">Étant donné que chaque fichier zip ne contient qu’une seule version d’une ressource, le format du module ajouté dans WMF 5.0, qui contient plusieurs versions de module dans un seul répertoire, n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="735a8-205">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="735a8-206">Cela signifie qu’avant de créer le package des modules de ressources DSC à utiliser avec le serveur collecteur, vous devez apporter une petite modification à la structure de répertoires.</span><span class="sxs-lookup"><span data-stu-id="735a8-206">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="735a8-207">Le format par défaut des modules contenant des ressources DSC dans WMF 5.0 est `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="735a8-207">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="735a8-208">Avant de créer des packages pour le serveur collecteur, supprimez le dossier **{Module version}** afin que le chemin devienne `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="735a8-208">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="735a8-209">Ensuite, compressez le dossier comme décrit ci-dessus, et placez ces fichiers zip dans le dossier **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="735a8-209">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="735a8-210">Utilisez `New-DscChecksum {module zip file}` afin de créer un fichier de somme de contrôle pour le module qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="735a8-210">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="735a8-211">Format du fichier MOF de configuration</span><span class="sxs-lookup"><span data-stu-id="735a8-211">Configuration MOF format</span></span>

<span data-ttu-id="735a8-212">Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration.</span><span class="sxs-lookup"><span data-stu-id="735a8-212">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="735a8-213">Pour créer une somme de contrôle, appelez l’applet de commande [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum).</span><span class="sxs-lookup"><span data-stu-id="735a8-213">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="735a8-214">L’applet de commande prend un paramètre **Path** qui spécifie le dossier où se trouve la configuration MOF.</span><span class="sxs-lookup"><span data-stu-id="735a8-214">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="735a8-215">L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration.</span><span class="sxs-lookup"><span data-stu-id="735a8-215">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="735a8-216">S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier.</span><span class="sxs-lookup"><span data-stu-id="735a8-216">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="735a8-217">Placez les fichiers MOF et leurs fichiers de somme de contrôle associés dans le dossier **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="735a8-217">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="735a8-218">Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="735a8-218">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="735a8-219">Outils</span><span class="sxs-lookup"><span data-stu-id="735a8-219">Tooling</span></span>

<span data-ttu-id="735a8-220">Pour faciliter la configuration, la validation et la gestion du serveur collecteur, les outils suivants sont fournis comme exemples dans la dernière version du module xPSDesiredStateConfiguration :</span><span class="sxs-lookup"><span data-stu-id="735a8-220">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="735a8-221">Module permettant de créer le package des modules de ressources DSC et les fichiers de configuration à utiliser sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-221">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="735a8-222">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span><span class="sxs-lookup"><span data-stu-id="735a8-222">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span></span>
   <span data-ttu-id="735a8-223">Exemples ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="735a8-223">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="735a8-224">Script qui valide la configuration du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-224">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="735a8-225">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span><span class="sxs-lookup"><span data-stu-id="735a8-225">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="735a8-226">Solutions de service collecteur de la communauté</span><span class="sxs-lookup"><span data-stu-id="735a8-226">Community Solutions for Pull Service</span></span>

<span data-ttu-id="735a8-227">La communauté DSC a créé plusieurs solutions pour implémenter le protocole de service collecteur.</span><span class="sxs-lookup"><span data-stu-id="735a8-227">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span> <span data-ttu-id="735a8-228">Pour les environnements locaux, elle offre des fonctionnalités de service collecteur et la possibilité de contribuer en retour avec des améliorations incrémentielles.</span><span class="sxs-lookup"><span data-stu-id="735a8-228">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="735a8-229">Tug</span><span class="sxs-lookup"><span data-stu-id="735a8-229">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="735a8-230">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="735a8-230">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="735a8-231">Configuration du client collecteur</span><span class="sxs-lookup"><span data-stu-id="735a8-231">Pull client configuration</span></span>

<span data-ttu-id="735a8-232">Les rubriques suivantes décrivent la configuration des clients collecteurs en détail :</span><span class="sxs-lookup"><span data-stu-id="735a8-232">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="735a8-233">Configurer un client collecteur DSC à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="735a8-233">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="735a8-234">Configurer un client collecteur DSC à l’aide du nom de configuration</span><span class="sxs-lookup"><span data-stu-id="735a8-234">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="735a8-235">Configurations partielles</span><span class="sxs-lookup"><span data-stu-id="735a8-235">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="735a8-236">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="735a8-236">See also</span></span>

- [<span data-ttu-id="735a8-237">Vue d’ensemble de la configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="735a8-237">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="735a8-238">Application des configurations</span><span class="sxs-lookup"><span data-stu-id="735a8-238">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="735a8-239">Utilisation d’un serveur de rapports DSC</span><span class="sxs-lookup"><span data-stu-id="735a8-239">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="735a8-240">[[MS-DSCPM] : protocole de modèle Pull Desired State Configuration](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span><span class="sxs-lookup"><span data-stu-id="735a8-240">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span></span>
- <span data-ttu-id="735a8-241">[[MS-DSCPM] : errata de protocole de modèle Pull Desired State Configuration](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span><span class="sxs-lookup"><span data-stu-id="735a8-241">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span></span>
