---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187764"
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="112cc-103">Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="112cc-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="112cc-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="112cc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="112cc-105">Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL où contacter le serveur collecteur pour obtenir des configurations.</span><span class="sxs-lookup"><span data-stu-id="112cc-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="112cc-106">Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="112cc-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="112cc-107">Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration appelé « métaconfiguration ».</span><span class="sxs-lookup"><span data-stu-id="112cc-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="112cc-108">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Gestionnaire de configuration local de la configuration d’état souhaité Windows PowerShell 4.0](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="112cc-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="112cc-109">Le script suivant configure le gestionnaire de configuration local de façon à extraire des configurations d’un serveur nommé « PullServer ».</span><span class="sxs-lookup"><span data-stu-id="112cc-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="112cc-110">Dans le script, **DownloadManagerCustomData** passe l’URL du serveur collecteur et (dans cet exemple) permet une connexion non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="112cc-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span>

<span data-ttu-id="112cc-111">Quand le script s’exécute, il crée un dossier de sortie appelé **SimpleMetaConfigurationForPull** et y place un fichier MOF de métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="112cc-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="112cc-112">Pour appliquer la configuration, utilisez **Set-DscLocalConfigurationManager** avec des paramètres pour **ComputerName** (utilisez « localhost ») et **Path** (chemin de l’emplacement du fichier localhost.meta.mof du nœud cible).</span><span class="sxs-lookup"><span data-stu-id="112cc-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="112cc-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="112cc-113">For example:</span></span>
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="112cc-114">ID de configuration</span><span class="sxs-lookup"><span data-stu-id="112cc-114">Configuration ID</span></span>
<span data-ttu-id="112cc-115">Le script définit la propriété **ConfigurationID** du gestionnaire de configuration local sur un GUID précédemment créé à cet effet (vous pouvez créer un GUID à l’aide de l’applet de commande **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="112cc-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="112cc-116">Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="112cc-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="112cc-117">Le fichier MOF de configuration sur le serveur collecteur doit être nommé `ConfigurationID.mof`, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="112cc-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="112cc-118">Extraction à partir d’un serveur SMB</span><span class="sxs-lookup"><span data-stu-id="112cc-118">Pulling from an SMB server</span></span>

<span data-ttu-id="112cc-119">Si le serveur collecteur est configuré comme un partage de fichiers SMB au lieu d’un service web, vous spécifiez **DscFileDownloadManager** au lieu de **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="112cc-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="112cc-120">**DscFileDownloadManager** prend une propriété **SourcePath** au lieu de **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="112cc-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="112cc-121">Le script suivant configure le gestionnaire de configuration local de façon à extraire d’un partage SMB nommé « SmbDscShare » sur un serveur nommé « CONTOSO-SERVER » :</span><span class="sxs-lookup"><span data-stu-id="112cc-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="112cc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="112cc-122">See Also</span></span>

- [<span data-ttu-id="112cc-123">Configuration d’un serveur collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="112cc-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="112cc-124">Configuration d’un serveur collecteur SMB DSC</span><span class="sxs-lookup"><span data-stu-id="112cc-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)