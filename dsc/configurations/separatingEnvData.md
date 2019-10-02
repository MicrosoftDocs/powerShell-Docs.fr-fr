---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Séparation des données de configuration et d’environnement
ms.openlocfilehash: b16243fc9096f786a25ed20868e94a3aa85e403e
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323247"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="b3333-103">Séparation des données de configuration et d’environnement</span><span class="sxs-lookup"><span data-stu-id="b3333-103">Separating configuration and environment data</span></span>

><span data-ttu-id="b3333-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b3333-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b3333-105">Il peut être utile de séparer les données utilisées dans une configuration DSC de la configuration elle-même en s’aidant des données de configuration.</span><span class="sxs-lookup"><span data-stu-id="b3333-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="b3333-106">Pour y parvenir, vous pouvez utiliser une seule et même configuration pour plusieurs environnements.</span><span class="sxs-lookup"><span data-stu-id="b3333-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="b3333-107">Par exemple, si vous développez une application, vous pouvez utiliser une seule configuration pour les environnements de développement et de production et utiliser les données de configuration pour spécifier les données de chaque environnement.</span><span class="sxs-lookup"><span data-stu-id="b3333-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="b3333-108">Définition des données de configuration</span><span class="sxs-lookup"><span data-stu-id="b3333-108">What is configuration data?</span></span>

<span data-ttu-id="b3333-109">Les données de configuration sont des données définies dans une table de hachage. Elles sont ensuite transférées à une configuration DSC au moment de la compilation de cette configuration.</span><span class="sxs-lookup"><span data-stu-id="b3333-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="b3333-110">Pour une description détaillée de la table de hachage **ConfigurationData**, voir [Utilisation des données de configuration](configData.md).</span><span class="sxs-lookup"><span data-stu-id="b3333-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="b3333-111">Un exemple simple</span><span class="sxs-lookup"><span data-stu-id="b3333-111">A simple example</span></span>

<span data-ttu-id="b3333-112">Examinons un exemple très simple pour voir comment cela fonctionne.</span><span class="sxs-lookup"><span data-stu-id="b3333-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="b3333-113">Nous allons créer une configuration unique qui garantit la présence d’**IIS** sur certains nœuds et la présence d’**Hyper-V** sur d’autres :</span><span class="sxs-lookup"><span data-stu-id="b3333-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

<span data-ttu-id="b3333-114">La dernière ligne de ce script compile la configuration en transférant `$MyData` en tant que valeur du paramètre **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="b3333-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="b3333-115">Cela conduit à la création de deux fichiers MOF :</span><span class="sxs-lookup"><span data-stu-id="b3333-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="b3333-116">`$MyData` spécifie deux nœuds différents, chacun avec son propre `NodeName` et `Role`.</span><span class="sxs-lookup"><span data-stu-id="b3333-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="b3333-117">La configuration crée les blocs **Nœud** de façon dynamique en prenant la collection de nœuds qu’elle obtient à partir de `$MyData` (en particulier, `$AllNodes`) et filtre cette collection sur la propriété `Role`.</span><span class="sxs-lookup"><span data-stu-id="b3333-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="b3333-118">Utilisation des données de configuration pour définir les environnements de développement et de production</span><span class="sxs-lookup"><span data-stu-id="b3333-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="b3333-119">Examinons un exemple complet qui utilise une configuration unique pour configurer les environnements de développement et de production d’un site web.</span><span class="sxs-lookup"><span data-stu-id="b3333-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="b3333-120">Dans l’environnement de développement, IIS et SQL Server sont installés sur un même nœud.</span><span class="sxs-lookup"><span data-stu-id="b3333-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="b3333-121">Dans l’environnement de production, IIS et SQL Server sont installés sur des nœuds séparés.</span><span class="sxs-lookup"><span data-stu-id="b3333-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="b3333-122">Nous allons utiliser un fichier de données de configuration .psd1 pour spécifier les données des deux environnements.</span><span class="sxs-lookup"><span data-stu-id="b3333-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="b3333-123">Fichier de données de configuration</span><span class="sxs-lookup"><span data-stu-id="b3333-123">Configuration data file</span></span>

<span data-ttu-id="b3333-124">Nous définissons les données de l’environnement de développement et de production dans un fichier nommé `DevProdEnvData.psd1` comme suit :</span><span class="sxs-lookup"><span data-stu-id="b3333-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a><span data-ttu-id="b3333-125">Fichier de script de configuration</span><span class="sxs-lookup"><span data-stu-id="b3333-125">Configuration script file</span></span>

<span data-ttu-id="b3333-126">À présent, dans la configuration (qui est définie dans un fichier `.ps1`), nous allons filtrer les nœuds indiqués dans `DevProdEnvData.psd1` selon leur rôle (`MSSQL`, `Dev` ou les deux), puis les configurer en conséquence.</span><span class="sxs-lookup"><span data-stu-id="b3333-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="b3333-127">Dans l’environnement de développement, SQL Server et IIS se trouvent sur le même nœud, tandis que dans l’environnement de production, ils se trouvent sur deux nœuds différents.</span><span class="sxs-lookup"><span data-stu-id="b3333-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="b3333-128">Le contenu du site est également différent, comme spécifié par les propriétés `SiteContents`.</span><span class="sxs-lookup"><span data-stu-id="b3333-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="b3333-129">À la fin du script de configuration, nous appelons la configuration (nous la compilons dans un document MOF), en passant `DevProdEnvData.psd1` comme paramètre `$ConfigurationData`.</span><span class="sxs-lookup"><span data-stu-id="b3333-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="b3333-130">**Remarque :** Cette configuration exige l’installation des modules `xSqlPs` et `xWebAdministration` sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="b3333-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="b3333-131">Nous allons définir la configuration dans un fichier nommé `MyWebApp.ps1` :</span><span class="sxs-lookup"><span data-stu-id="b3333-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="b3333-132">Lorsque vous exécutez cette configuration, trois fichiers MOF sont créés (un pour chaque entrée nommée du tableau **AllNodes**) :</span><span class="sxs-lookup"><span data-stu-id="b3333-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="b3333-133">Utilisation des données n’appartenant pas à un nœud</span><span class="sxs-lookup"><span data-stu-id="b3333-133">Using non-node data</span></span>

<span data-ttu-id="b3333-134">Vous pouvez ajouter des clés supplémentaires à la table de hachage **ConfigurationData** pour les données qui ne sont pas spécifiques à un nœud.</span><span class="sxs-lookup"><span data-stu-id="b3333-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="b3333-135">La configuration suivante vérifie la présence de deux sites web.</span><span class="sxs-lookup"><span data-stu-id="b3333-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="b3333-136">Les données de chaque site web sont définies dans le tableau **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="b3333-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="b3333-137">Le fichier `Config.xml` étant utilisé pour les deux sites web, nous le définissons dans une clé supplémentaire appelée `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="b3333-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="b3333-138">Notez que vous pouvez avoir autant de clés supplémentaires que vous le souhaitez et les nommer comme bon vous semble.</span><span class="sxs-lookup"><span data-stu-id="b3333-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="b3333-139">`NonNodeData` n’est pas un terme réservé. Il correspond simplement au nom que nous avons décidé de donner à cette clé supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b3333-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="b3333-140">Accédez aux clés supplémentaires en utilisant la variable spéciale **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="b3333-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="b3333-141">Dans cet exemple, `ConfigFileContents` est accessible avec la ligne :</span><span class="sxs-lookup"><span data-stu-id="b3333-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="b3333-142">dans le bloc de ressources `File`.</span><span class="sxs-lookup"><span data-stu-id="b3333-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

        @{
            NodeName = "VM-1"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },


        @{
            NodeName = "VM-2"
            SiteContents = "C:\Site2"
            SiteName = "Website2"
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="b3333-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3333-143">See Also</span></span>
- [<span data-ttu-id="b3333-144">Utilisation des données de configuration</span><span class="sxs-lookup"><span data-stu-id="b3333-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="b3333-145">Options relatives aux informations d’identification dans les données de configuration</span><span class="sxs-lookup"><span data-stu-id="b3333-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="b3333-146">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="b3333-146">DSC Configurations</span></span>](configurations.md)
