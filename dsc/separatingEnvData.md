---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Séparation des données de configuration et d’environnement
ms.openlocfilehash: 3c7f1ba93b4438b3eb440dc1f2349eff0606ac0a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188120"
---
# <a name="separating-configuration-and-environment-data"></a>Séparation des données de configuration et d’environnement

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Il peut être utile de séparer les données utilisées dans une configuration DSC de la configuration elle-même en s’aidant des données de configuration.
Pour y parvenir, vous pouvez utiliser une seule et même configuration pour plusieurs environnements.

Par exemple, si vous développez une application, vous pouvez utiliser une seule configuration pour les environnements de développement et de production et utiliser les données de configuration pour spécifier les données de chaque environnement.

## <a name="what-is-configuration-data"></a>Définition des données de configuration

Les données de configuration sont des données définies dans une table de hachage. Elles sont ensuite transférées à une configuration DSC au moment de la compilation de cette configuration.

Pour une description détaillée de la table de hachage **ConfigurationData**, voir [Utilisation des données de configuration](configData.md).

## <a name="a-simple-example"></a>Un exemple simple

Examinons un exemple très simple pour voir comment cela fonctionne.
Nous allons créer une configuration unique qui garantit la présence d’**IIS** sur certains nœuds et la présence d’**Hyper-V** sur d’autres :

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

La dernière ligne de ce script compile la configuration en transférant `$MyData` en tant que valeur du paramètre **ConfigurationData**.

Cela conduit à la création de deux fichiers MOF :

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` spécifie deux nœuds différents, chacun avec son propre `NodeName` et `Role`. La configuration crée les blocs **Nœud** de façon dynamique en prenant la collection de nœuds qu’elle obtient à partir de `$MyData` (en particulier, `$AllNodes`) et filtre cette collection sur la propriété `Role`.

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Utilisation des données de configuration pour définir les environnements de développement et de production

Examinons un exemple complet qui utilise une configuration unique pour configurer les environnements de développement et de production d’un site web. Dans l’environnement de développement, IIS et SQL Server sont installés sur un même nœud. Dans l’environnement de production, IIS et SQL Server sont installés sur des nœuds séparés. Nous allons utiliser un fichier de données de configuration .psd1 pour spécifier les données des deux environnements.

 ### <a name="configuration-data-file"></a>Fichier de données de configuration

Nous définissons les données de l’environnement de développement et de production dans un fichier nommé `DevProdEnvData.psd1` comme suit :

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

### <a name="configuration-script-file"></a>Fichier de script de configuration

À présent, dans la configuration (qui est définie dans un fichier `.ps1`), nous allons filtrer les nœuds indiqués dans `DevProdEnvData.psd1` selon leur rôle (`MSSQL`, `Dev` ou les deux), puis les configurer en conséquence.
Dans l’environnement de développement, SQL Server et IIS se trouvent sur le même nœud, tandis que dans l’environnement de production, ils se trouvent sur deux nœuds différents.
Le contenu du site est également différent, comme spécifié par les propriétés `SiteContents`.

À la fin du script de configuration, nous appelons la configuration (nous la compilons dans un document MOF), en passant `DevProdEnvData.psd1` comme paramètre `$ConfigurationData`.

>**Remarque :** Cette configuration exige l’installation des modules `xSqlPs` et `xWebAdministration` sur le nœud cible.

Nous allons définir la configuration dans un fichier nommé `MyWebApp.ps1` :

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

Lorsque vous exécutez cette configuration, trois fichiers MOF sont créés (un pour chaque entrée nommée du tableau **AllNodes**) :

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Utilisation des données n’appartenant pas à un nœud

Vous pouvez ajouter des clés supplémentaires à la table de hachage **ConfigurationData** pour les données qui ne sont pas spécifiques à un nœud.
La configuration suivante vérifie la présence de deux sites web.
Les données de chaque site web sont définies dans le tableau **AllNodes**.
Le fichier `Config.xml` étant utilisé pour les deux sites web, nous le définissons dans une clé supplémentaire appelée `NonNodeData`.
Notez que vous pouvez avoir autant de clés supplémentaires que vous le souhaitez et les nommer comme bon vous semble.
`NonNodeData` n’est pas un terme réservé. Il correspond simplement au nom que nous avons décidé de donner à cette clé supplémentaire.

Accédez aux clés supplémentaires en utilisant la variable spéciale **$ConfigurationData**.
Dans cet exemple, `ConfigFileContents` est accessible avec la ligne :
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 dans le bloc de ressources `File`.


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
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
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a>Voir aussi
- [Utilisation des données de configuration](configData.md)
- [Options relatives aux informations d’identification dans les données de configuration](configDataCredentials.md)
- [Configurations DSC](configurations.md)
