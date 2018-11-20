---
ms.date: 04/11/2018
keywords: dsc,powershell,configuration,setup
title: Service collecteur DSC
ms.openlocfilehash: 2ef48b88cc9e14da452e0d19e5a0f43fc8a95ab2
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619158"
---
# <a name="desired-state-configuration-pull-service"></a>Service collecteur Desired State Configuration

> S’applique à : Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

La gestion du Gestionnaire de configuration local peut être centralisée par une solution de service collecteur.
Lorsque vous utilisez cette approche, le nœud géré est inscrit auprès d’un service et se voit affecter une configuration dans les paramètres LCM.
La configuration et toutes les ressources DSC nécessaires en tant que dépendances de la configuration sont téléchargées sur l’ordinateur et utilisées par le Gestionnaire de configuration local pour gérer la configuration.
Des informations sur l’état de l’ordinateur géré sont chargées sur le service pour créer des rapports.
Ce concept est appelé « service collecteur ».

Les options actuelles du service d’extraction sont les suivantes :

- Service de Configuration d’état souhaité d’Azure Automation
- Service collecteur exécuté sur Windows Server
- Solutions open source gérées par la communauté
- Partage SMB

**La solution recommandée**, qui est à la fois l’option offrant le plus de fonctionnalités, est [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

Le service Azure peut gérer les nœuds locaux dans des centres de données privés ou dans des clouds publics tels qu’Azure et AWS.
Pour les environnements où les serveurs ne peut pas se connecter directement à Internet, envisagez de limiter le trafic sortant à la seule plage IP Azure publiée (voir [Plages d’adresses IP Azure Datacenter](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Fonctionnalités du service en ligne qui ne sont actuellement pas disponibles dans le service d’extraction sur Windows Server :
- Toutes les données sont chiffrées, en transit comme au repos
- Les certificats clients sont créés et gérés automatiquement
- Magasin des secrets pour une gestion centralisée des [mots de passe/informations d’identification](/azure/automation/automation-credentials), ou des [variables](/azure/automation/automation-variables) telles que les noms des serveurs ou les chaînes de connexion
- Gestion centralisée du nœud [configuration du LCM](metaConfig.md#basic-settings)
- Assignation centralisée de configurations aux nœuds clients
- Mise des modifications de la configuration en « groupes de contrôle de validité » pour effectuer des tests avant la production
- Création de rapports graphiques
  - Détails de l’état au niveau de la granularité de la ressource DSC
  - Messages d’erreur en clair des ordinateurs clients pour la résolution des problèmes
- [Intégration à Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) pour les alertes, tâches automatisées, application Android/iOS pour les rapports et les alertes

## <a name="dsc-pull-service-in-windows-server"></a>Service collecteur DSC dans Windows Server

Il est possible de configurer un service collecteur pour l’exécuter sur Windows Server.
Notez que la solution de service collecteur incluse dans Windows Server contient uniquement les fonctionnalités de stockage des configurations/modules à télécharger, et les fonctionnalités de capture de données de rapport dans la base de données.
Elle ne contient pas les nombreuses fonctionnalités offertes par le service dans Azure et n’est donc pas un bon outil pour évaluer la manière dont le service doit être utilisé.

Le service collecteur proposé dans Windows Server est un service web dans IIS qui utilise une interface OData pour mettre les fichiers de configuration DSC à la disposition des nœuds cibles quand ceux-ci en ont besoin.

Configuration requise pour utiliser un serveur collecteur :

- Un serveur en cours d’exécution :
  - WMF/PowerShell 5.0 ou version supérieure
  - Rôle serveur IIS
  - Service DSC
- Idéalement, des moyens de générer un certificat pour sécuriser les informations d’identification transmises au gestionnaire de configuration local sur les nœuds cibles

La meilleure façon de configurer Windows Server pour héberger un service collecteur est d’utiliser une configuration DSC.
Vous trouverez ci-dessous un exemple de script.

### <a name="supported-database-systems"></a>Systèmes de base de données pris en charge

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (par défaut), MDB |ESENT (par défaut), MDB|ESENT (par défaut), SQL Server, MDB

À compter de la version 17090 de [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server constitue une option prise en charge du service collecteur (fonctionnalité Windows *Service DSC*).  Vous disposez ainsi d’une nouvelle option pour mettre à l’échelle les grands environnements DSC qui n’ont pas été migrés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> **Remarque** : La prise en charge de SQL Server ne sera pas ajoutée aux versions précédentes de WMF 5.1 (ou versions antérieures) et sera uniquement disponible dans les versions de Windows Server supérieures ou égales à 17090.

Pour configurer le serveur collecteur de manière à utiliser SQL Server, définissez **SqlProvider** sur `$true` et **SqlConnectionString** sur une chaîne de connexion SQL Server valide.  Pour plus d’informations, consultez [Chaînes de connexion SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Pour obtenir un exemple de configuration de SQL Server avec **xDscWebService**, lisez d’abord [Utilisation de la ressource xDSCWebService](#using-the-xdscwebservice-resource), puis consultez l’exemple [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 sur GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Utilisation de la ressource xDSCWebService

Le moyen le plus simple de configurer un serveur collecteur web consiste à utiliser la ressource **xDscWebService** qui se trouve dans le module **xPSDesiredStateConfiguration**.
Les étapes suivantes expliquent comment utiliser la ressource dans une configuration qui configure le service web.

1. Appelez l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module) pour installer le module **xPSDesiredStateConfiguration**. **Remarque** : **Install-Module** est inclus dans le module **PowerShellGet** de PowerShell 5.0. Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0 ici : [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
1. Obtenez un certificat SSL pour le serveur collecteur DSC auprès d’une autorité de certification approuvée, au sein de votre organisation ou auprès d’une autorité publique. Le certificat reçu de l’autorité est généralement au format PFX. Installez le certificat sur le nœud qui sera le serveur DSC à l’emplacement par défaut, c’est-à-dire : CERT:\LocalMachine\My. Notez l’empreinte de certificat.
1. Sélectionnez un GUID à utiliser comme clé d’inscription. Pour en générer un à l’aide de PowerShell, entrez ce qui suit à l’invite PowerShell et appuyez sur Entrée : « ``` [guid]::newGuid()``` » ou « ```New-Guid``` ». Cette clé est utilisée par les nœuds clients comme une clé partagée pour l’authentification lors de l’inscription. Pour plus d’informations, consultez la section Clé d’inscription ci-dessous.
1. Dans PowerShell ISE, démarrez (F5) le script de configuration suivant (situé dans le dossier Examples du module **xPSDesiredStateConfiguration** en tant que Sample_xDscWebServiceRegistration.ps1). Ce script configure le serveur collecteur.

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

1. Exécutez la configuration, en passant l’empreinte du certificat SSL comme paramètre **certificateThumbPrint** et une clé d’inscription GUID comme paramètre **RegistrationKey** :

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Clé d’inscription

Pour que les nœuds clients puissent s’inscrire auprès du serveur afin de pouvoir utiliser les noms de configuration au lieu de l’ID de configuration, une clé d’inscription, créée par la configuration ci-dessus, est enregistrée dans un fichier nommé `RegistrationKeys.txt` dans `C:\Program Files\WindowsPowerShell\DscService`. La clé d’inscription fonctionne comme un secret partagé utilisé lors de l’inscription initiale par le client avec le serveur collecteur. Le client génère un certificat auto-signé qui est utilisé pour l’authentification unique auprès du serveur collecteur, une fois l’inscription terminée. L’empreinte de ce certificat est stockée localement et associée à l’URL du serveur collecteur.
> **Remarque** : Les clés d’inscription ne sont pas prises en charge dans PowerShell 4.0.

Pour configurer un nœud pour l’authentification auprès du serveur collecteur, la clé d’inscription doit se trouver dans la métaconfiguration de tous les nœuds cibles que vous prévoyez d’inscrire auprès de ce serveur. Notez que la propriété **RegistrationKey** dans la métaconfiguration ci-dessous est supprimée une fois que l’ordinateur cible a été correctement inscrit, et que la valeur « 140a952b-b9d6-406b-b416-e0f759c9c0e4 » doit correspondre à la valeur stockée dans le fichier RegistrationKeys.txt sur le serveur collecteur. Conservez la valeur de la clé d’inscription en lieu sûr, car elle permet d’inscrire n’importe quel ordinateur cible auprès du serveur.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

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

> **Remarque** : la section **ReportServerWeb** permet d’envoyer les données de rapport au serveur collecteur.

Si la propriété **ConfigurationID** est absente du fichier de métaconfiguration, cela signifie implicitement que ce serveur collecteur prend en charge la version V2 du protocole du serveur collecteur et donc qu’une inscription initiale est nécessaire.
Inversement, si la propriété **ConfigurationID** est présente, la version V1 du protocole du serveur collecteur est utilisée et il n’y a pas de traitement de l’inscription.

>**Remarque** : Dans un scénario PUSH, la version actuelle contient un bogue qui demande de définir une propriété ConfigurationID dans le fichier de métaconfiguration pour les nœuds qui n’ont jamais été inscrits auprès d’un serveur collecteur. Cette opération permet de forcer le protocole du serveur collecteur V1 et d’éviter les messages d’échec d’inscription.

## <a name="placing-configurations-and-resources"></a>Placement des configurations et des ressources

Une fois l’installation du serveur collecteur terminée, vous placez les modules et configurations à extraire par les nœuds cibles dans les dossiers définis par les propriétés **ConfigurationPath** et **ModulePath** de la configuration du serveur collecteur.
Ces fichiers doivent se trouver dans un format spécifique afin que le serveur collecteur puisse les traiter correctement.

### <a name="dsc-resource-module-package-format"></a>Format du package de module de ressources DSC

Chaque module de ressources doit être compressé et nommé selon le modèle suivant : `{Module Name}_{Module Version}.zip`
Par exemple, un module xWebAdminstration avec une version de module 3.1.2.0 est nommé « xWebAdministration_3.2.1.0.zip ».
Chaque version d’un module doit être contenue dans un seul fichier zip.
Étant donné que chaque fichier zip ne contient qu’une seule version d’une ressource, le format du module ajouté dans WMF 5.0, qui contient plusieurs versions de module dans un seul répertoire, n’est pas pris en charge.
Cela signifie qu’avant de créer le package des modules de ressources DSC à utiliser avec le serveur collecteur, vous devez apporter une petite modification à la structure de répertoires.
Le format par défaut des modules contenant les ressources DSC dans WMF 5.0 est « {Dossier du module}\{{Version du module}\DscResources\{Dossier des ressources DSC}\' ».
Avant de créer les packages pour le serveur collecteur, supprimez le dossier **{Version du module}** pour transformer le chemin en « {Dossier du module}\DscResources\{Dossier des ressources DSC}\' ».
Ensuite, compressez le dossier comme décrit ci-dessus, et placez ces fichiers zip dans le dossier **ModulePath**.

Utilisez `New-DscChecksum {module zip file}` afin de créer un fichier de somme de contrôle pour le module qui vient d’être ajouté.

### <a name="configuration-mof-format"></a>Format du fichier MOF de configuration

Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration.
Pour créer une somme de contrôle, appelez l’applet de commande [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum).
L’applet de commande prend un paramètre **Path** qui spécifie le dossier où se trouve la configuration MOF.
L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration.
S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier.
Placez les fichiers MOF et leurs fichiers de somme de contrôle associés dans le dossier **ConfigurationPath**.

>**Remarque** : Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.

### <a name="tooling"></a>Outils

Pour faciliter la configuration, la validation et la gestion du serveur collecteur, les outils suivants sont fournis comme exemples dans la dernière version du module xPSDesiredStateConfiguration :

1. Module permettant de créer le package des modules de ressources DSC et les fichiers de configuration à utiliser sur le serveur collecteur. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Exemples ci-dessous :

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Script qui valide la configuration du serveur collecteur. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Solutions de service collecteur de la communauté

La communauté DSC a créé plusieurs solutions pour implémenter le protocole de service collecteur.
Pour les environnements locaux, elle offre des fonctionnalités de service collecteur et la possibilité de contribuer en retour avec des améliorations incrémentielles.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Configuration du client collecteur

Les rubriques suivantes décrivent la configuration des clients collecteurs en détail :

- [Configuration d’un client collecteur DSC à l’aide de l’ID de configuration](pullClientConfigID.md)
- [Configuration d’un client collecteur DSC à l’aide du nom de configuration](pullClientConfigNames.md)
- [Configurations partielles](partialConfigs.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell](overview.md)
- [Application des configurations](enactingConfigurations.md)
- [Utilisation d’un serveur de rapports DSC](reportServer.md)
- [[MS-DSCPM] : protocole de modèle Pull Configuration d'état souhaité](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM] : errata de modèle Pull Configuration d'état souhaité](https://msdn.microsoft.com/library/mt612824.aspx)
