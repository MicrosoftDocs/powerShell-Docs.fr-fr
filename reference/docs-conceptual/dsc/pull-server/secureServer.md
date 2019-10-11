---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Bonnes pratiques pour le serveur collecteur
ms.openlocfilehash: a3c4ca039b1e061a9246848bef6aeecebcd89011
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953526"
---
# <a name="pull-server-best-practices"></a>Bonnes pratiques pour le serveur collecteur

S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](/powershell/dsc/pull-server/pullserver#community-solutions-for-pull-service).

Résumé : Ce document vise à fournir une procédure et une extensibilité pour aider les ingénieurs qui préparent la solution. Les informations qu’il contient indiquent les bonnes pratiques identifiées par les clients puis validées par l’équipe du produit qui garantit que les recommandations sont innovantes et considérées comme stables.

| |Informations sur le document|
|:---|:---|
Auteur | Michael Greene
Réviseurs | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Publié | Avril 2015

## <a name="abstract"></a>Résumé

Ce document a pour but de fournir des conseils officiels à toute personne planifiant l’implémentation d’un serveur collecteur Windows PowerShell DSC (Desired State Configuration). Un serveur collecteur est un service simple dont le déploiement ne devrait prendre que quelques minutes. Bien que ce document propose des procédures techniques pouvant être utilisées dans un déploiement, il est surtout une référence de bonnes pratiques et de points à prendre en compte avant d’effectuer un déploiement.
Les lecteurs doivent avoir une connaissance de base de DSC et des termes utilisés pour décrire les composants inclus dans un déploiement DSC. Pour plus d’informations, consultez la rubrique [Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell](/powershell/dsc/overview).
Étant donné que DSC est supposé évoluer à la cadence du cloud, la technologie sous-jacente qui inclut le serveur collecteur devrait également évoluer et introduire de nouvelles fonctionnalités. L’annexe de ce document comprend un tableau de versions qui fournit des références aux versions précédentes et aux solutions novatrices pour encourager les conceptions innovantes.

Les deux principales sections de ce document sont les suivantes :

- Planification de la configuration
- Guide d’installation

### <a name="versions-of-the-windows-management-framework"></a>Versions de Windows Management Framework

Les informations contenues dans ce document s’appliquent à Windows Management Framework 5.0. Même si WMF 5.0 n’est pas nécessaire au déploiement et au fonctionnement d’un serveur collecteur, elle est la version ciblée par ce document.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration

DSC (Desired State Configuration) est une plateforme de gestion qui permet de déployer et de gérer les données de configuration à l’aide d’une syntaxe nommée MOF (Managed Object Format) pour décrire le modèle CIM (Common Information Model). Un projet open source, OMI (Open Management Infrastructure), existe pour pousser le développement de ces normes sur les plateformes comme les systèmes d’exploitation Linux et de matériel réseau. Pour plus d’informations, consultez la [page DMTF proposant des liens vers les spécifications MOF](https://www.dmtf.org/standards/cim) et la page relative aux [documents et la source OMI](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell fournit un ensemble d’extensions de langage pour DSC que vous pouvez utiliser pour créer et gérer des configurations déclaratives.

### <a name="pull-server-role"></a>Rôle serveur collecteur

Un serveur collecteur fournit un service centralisé pour stocker des configurations qui seront accessibles aux nœuds cibles.

Vous pouvez déployer le rôle serveur collecteur comme instance de serveur web ou partage de fichiers SMB. La fonctionnalité de serveur web inclut une interface OData et peut éventuellement inclure des fonctionnalités permettant aux nœuds cibles d’envoyer une confirmation de réussite ou d’échec quand les configurations sont appliquées. Cette fonctionnalité est utile dans les environnements comportant un grand nombre de nœuds cibles.
Après avoir configuré un nœud cible (également appelé « client ») pour pointer vers le serveur collecteur, téléchargez et appliquez les données de configuration les plus récentes et tous les scripts nécessaires. Vous pouvez effectuer ces opérations en un seul déploiement ou comme une tâche récurrente qui considère aussi le serveur collecteur comme important pour gérer les changements au besoin. Pour plus d’informations, consultez [Serveurs collecteurs Windows PowerShell DSC](/powershell/dsc/pullServer/pullserver) et

[Modes de configuration d’émission et de collecte](/powershell/dsc/pullServer/pullserver).

## <a name="configuration-planning"></a>Planification de la configuration

Si vous voulez déployer des logiciels d’entreprise, vous pouvez collecter certaines informations à l’avance pour faciliter la planification de l’architecture appropriée et vous préparer aux étapes nécessaires pour effectuer le déploiement. Les sections suivantes fournissent des informations sur la préparation et sur les connexions d’organisation qui devront probablement être établies à l’avance.

### <a name="software-requirements"></a>Configuration logicielle requise

Pour déployer un serveur collecteur, la fonctionnalité Service DSC de Windows Server est obligatoire. Cette fonctionnalité a été introduite dans Windows Server 2012 et a été mise à jour au fil des versions de WMF (Windows Management Framework).

### <a name="software-downloads"></a>Téléchargements de logiciels

En plus de l’installation de contenu le plus récent à partir de Windows Update, il existe deux téléchargements qu’il est préférable d’utiliser pour déployer un serveur collecteur DSC : La dernière version de Windows Management Framework et un module DSC pour automatiser le provisionnement des serveurs collecteurs.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 inclut une fonctionnalité appelée « Service DSC ». Service DSC fournit les fonctionnalités de serveur collecteur, notamment les fichiers binaires qui prennent en charge le point de terminaison OData.
WMF est inclus dans Windows Server et est mis à jour en continu entre les versions de Windows Server. Les [nouvelles versions de WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) peuvent inclure des mises à jour de la fonctionnalité Service DSC. C’est pourquoi il est recommandé de télécharger la dernière version de WMF et de consulter les notes de publication afin de déterminer si la version inclut une mise à jour de la fonctionnalité Service DSC. Vous devez également examiner la section des notes de publication qui indique si l’état de conception d’un scénario ou d’une mise à jour est répertorié comme stable ou expérimental.
Pour avoir un cycle de versions en continu, des fonctionnalités peuvent être déclarées stables, ce qui signifie qu’elles sont prêtes à être utilisées dans un environnement de production, même si WMF est publié en préversion.
Autres fonctionnalités qui ont déjà été mises à jour par des versions de WMF (voir les Notes de publication de WMF pour plus d’informations) :

- Windows PowerShell Environnement d’écriture de scripts intégré (ISE) de Windows PowerShell
- Services web Windows PowerShell (Extension IIS Management OData)
- Windows PowerShell Desired State Configuration (DSC)
- WinRM (Windows Remote Management) WMI (Windows Management Instrumentation)

### <a name="dsc-resource"></a>Ressource DSC

Un déploiement de serveur collecteur peut être simplifié en configurant le service à l’aide d’un script de configuration DSC. Ce document présente des scripts de configuration qui peuvent être utilisés pour déployer un nœud de serveur prêt pour la production. Pour utiliser des scripts de configuration, un module DSC est obligatoire mais il n’est pas inclus dans Windows Server. Ce module obligatoire, appelé **xPSDesiredStateConfiguration**, inclut la ressource DSC **xDscWebService**. Vous pouvez télécharger le module xPSDesiredStateConfiguration [ici](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Utilisez l’applet de commande `Install-Module` à partir du module **PowerShellGet**.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Le module **PowerShellGet** télécharge le module dans :

`C:\Program Files\Windows PowerShell\Modules`

Tâche de planification|
---|
Avez-vous accès aux fichiers d’installation de Windows Server 2012 R2 ?|
L’environnement de déploiement disposera-t-il d’un accès à Internet pour télécharger WMF et le module à partir de la galerie en ligne ?|
Comment allez-vous installer les dernières mises à jour de sécurité après l’installation du système d’exploitation ?|
L’environnement disposera-t-il d’un accès à Internet pour obtenir les mises à jour ou d’un serveur WSUS (Windows Server Update Services) local ?|
Avez-vous accès aux fichiers d’installation de Windows Server qui contiennent déjà les mises à jour par l’intermédiaire de l’injection hors connexion ?|

### <a name="hardware-requirements"></a>Configuration matérielle requise

Les déploiements de serveurs collecteurs sont pris en charge sur les serveurs physiques et virtuels. La configuration requise du serveur collecteur s’aligne sur celle de Windows Server 2012 R2.

Processeur : 1,4 GHz 64 bits Mémoire : 512 Mo Espace disque : 32 Go Réseau : carte Gigabit Ethernet

Tâche de planification|
---|
Effectuerez-vous le déploiement sur du matériel physique ou sur une plateforme de virtualisation ?|
Quelle est la procédure pour demander un nouveau serveur dans votre environnement cible ?|
Combien de temps faut-il en moyenne pour rendre un serveur disponible ?|
Un serveur de quelle taille demandez-vous ?|

### <a name="accounts"></a>Comptes

Aucun compte de service en particulier n’est exigé pour déployer une instance de serveur collecteur.
Toutefois, dans certains scénarios, le site web peut s’exécuter dans le contexte d’un compte d’utilisateur local.
Par exemple, s’il est nécessaire d’accéder à un partage de stockage pour du contenu de site web et que le serveur Windows Server ou l’appareil hébergeant le partage de stockage ne sont pas joints à un domaine.

### <a name="dns-records"></a>Enregistrements DNS

Lors de la configuration de clients, vous aurez besoin d’un nom de serveur pour utiliser un environnement de serveur collecteur.
Dans les environnements de test, on utilise généralement le nom d’hôte du serveur. On peut aussi utiliser l’adresse IP du serveur si la résolution de noms DNS n’est pas disponible.
Dans les environnements de production ou dans un environnement lab destiné à représenter un déploiement de production, il est conseillé de créer un enregistrement DNS CNAME.

Un CNAME DNS vous permet de créer un alias pour faire référence à votre enregistrement d’hôte (A).
L’objectif d’avoir un enregistrement de nom supplémentaire est d’augmenter la flexibilité dans le cas où une modification s’avérerait nécessaire.
Un CNAME permet d’isoler la configuration du client afin que les modifications apportées à l’environnement de serveur, telles que le remplacement d’un serveur collecteur ou l’ajout de serveurs collecteurs supplémentaires, ne nécessitent pas une modification correspondante dans la configuration du client.

Quand vous choisissez un nom pour l’enregistrement DNS, gardez à l’esprit l’architecture de la solution.
Si vous utilisez l’équilibrage de charge, le certificat servant à sécuriser le trafic sur HTTPS doit partager le même nom que l’enregistrement DNS.

Scénario |Bonne pratique
:---|:---
Environnement de test |Reproduisez l’environnement de production planifié, si possible. Un nom d’hôte de serveur convient aux configurations simples. Si DNS n’est pas disponible, une adresse IP peut être utilisée à la place d’un nom d’hôte.|
Déploiement à nœud unique |Créez un enregistrement DNS CNAME qui pointe vers le nom d’hôte du serveur.|

Pour plus d’informations, consultez [Configuration du tourniquet (round robin) DNS dans Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Tâche de planification|
---|
Savez-vous qui contacter pour créer et modifier des enregistrements DNS ?|
Combien de temps faut-il en moyenne pour demander un enregistrement DNS ?|
Avez-vous besoin de demander des enregistrements de nom d’hôte (A) statiques pour les serveurs ?|
Que demanderez-vous comme CNAME ?|
Le cas échéant, quel type de solution d’équilibrage de charge utiliserez-vous ? (pour plus d’informations, voir la section intitulée « Équilibrage de la charge »)|

### <a name="public-key-infrastructure"></a>Infrastructure à clé publique (PKI)

Aujourd’hui, la plupart des organisations exigent que le trafic réseau, en particulier le trafic qui inclut des données sensibles comme le mode de configuration des serveurs, soit validé et/ou chiffré pendant le transit.
Bien qu’il soit possible de déployer un serveur collecteur à l’aide de HTTP, ce qui facilite les demandes des clients en texte en clair, il est recommandé de sécuriser le trafic à l’aide de HTTPS. Vous pouvez configurer le service pour utiliser HTTPS à l’aide d’un ensemble de paramètres dans la ressource DSC **xPSDesiredStateConfiguration**.

Les critères de certificat pour sécuriser le trafic HTTPS pour le serveur collecteur ne sont pas différents de ceux pour sécuriser un site web HTTPS. Le modèle de **serveur web** dans un service de certificats Windows Server est conforme aux fonctionnalités demandées.

Tâche de planification|
---|
Si les demandes de certificats ne sont pas automatisées, qui devrez-vous contacter pour demander un certificat ?|
Combien de temps faut-il en moyenne pour la demande ?|
Comment le fichier de certificat vous sera-t-il transféré ?|
Comment la clé privée de certificat vous sera-t-elle transférée ?|
Quelle est la durée d’expiration par défaut ?|
Avez-vous choisi, pour l’environnement de serveur collecteur, un nom DNS que vous pouvez utiliser comme nom du certificat ?|

### <a name="choosing-an-architecture"></a>Choix d’une architecture

Vous pouvez déployer un serveur collecteur à l’aide d’un service web hébergé sur IIS ou d’un partage de fichiers SMB. Dans la plupart des cas, l’option de service web offre une plus grande souplesse. Il n’est pas rare que le trafic HTTPS traverse les limites du réseau, tandis que le trafic SMB est souvent filtré ou bloqué entre les réseaux. Le service web offre également la possibilité d’inclure un serveur de mise en conformité ou Web Reporting Manager (ces deux sujets seront traités dans une future version de ce document) qui fournissent un mécanisme permettant aux clients de signaler l’état à un serveur pour une visibilité centralisée.
SMB fournit une option pour les environnements où la stratégie indique qu’un serveur web ne doit pas être utilisé et pour les autres exigences liées à l’environnement qui font qu’un rôle serveur web n’est pas souhaitable.
Dans les deux cas, n’oubliez pas d’évaluer les exigences de signature et de chiffrement du trafic. HTTPS, la signature SMB et les stratégies IPSEC sont toutes des options qui méritent d’être examinées.

#### <a name="load-balancing"></a>Équilibrage de charge

Les clients qui interagissent avec le service web adressent une demande d’informations qui sont retournées dans une réponse unique. Aucune demande séquentielle n’est nécessaire. La plateforme d’équilibrage de charge n’a donc pas besoin de garantir la conservation des sessions sur un serveur unique à un moment donné.

Tâche de planification|
---|
Quelle solution sera utilisée pour le trafic d’équilibrage de charge entre les serveurs ?|
Si vous utilisez un programme d’équilibrage de charge matérielle, qui acceptera une demande d’ajout d’une nouvelle configuration à l’appareil ?|
Combien de temps faut-il en moyenne pour faire une demande de configuration d’un nouveau service web à charge équilibrée ?|
Quelles informations seront nécessaires pour la demande ?|
Devrez-vous demander une adresse IP supplémentaire ou l’équipe responsable de l’équilibrage de charge gérera-t-elle ce point ?|
Avez-vous des enregistrements DNS obligatoires, et seront-ils exigés par l’équipe responsable de la configuration de la solution d’équilibrage de charge ?|
La solution d’équilibrage de charge exige-t-elle que l’infrastructure à clé publique (PKI) soit gérée par l’appareil ou peut-elle équilibrer la charge du trafic HTTPS tant qu’il n’y a aucune exigence liée à la session ?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Configurations et modules intermédiaires sur le serveur collecteur

Dans le cadre de la planification de la configuration, vous devez réfléchir aux modules et configurations DSC qui seront hébergés par le serveur. Pour les besoins de la planification de la configuration, il est important de comprendre le mode de préparation et de déploiement du contenu sur un serveur collecteur.

Cette section sera prochainement développée et incluse dans un Guide des opérations du serveur collecteur DSC.  Ce guide décrira le processus de gestion des configurations et des modules avec l’automatisation jour après jour.

#### <a name="dsc-modules"></a>Modules DSC

Les clients qui demandent une configuration doivent disposer des modules DSC obligatoires. Le serveur collecteur dispose d’une fonctionnalité qui permet d’automatiser la distribution sur demande des modules DSC aux clients. Si vous déployez un serveur collecteur pour la première fois, peut-être dans le cadre d’un laboratoire ou à des fins de démonstration de concept, vous allez probablement dépendre des modules DSC qui sont disponibles à partir de dépôts publics tels que PowerShell Gallery ou des dépôts GitHub PowerShell.org pour les modules DSC.

Il est essentiel de se rappeler que même pour les sources en ligne approuvées telles que PowerShell Gallery, tout module téléchargé à partir d’un dépôt public doit être vérifié par quelqu’un disposant d’une expérience PowerShell et d’une connaissance de l’environnement dans lequel les modules seront utilisés avant de les utiliser en production. Profitez de l’exécution de cette tâche pour rechercher dans le module tout contenu pouvant être supprimé, telle que la documentation et les exemples de script. Vous réduisez ainsi la bande passante réseau par client lors de leur première demande, quand les modules sont téléchargés sur le réseau à partir du serveur vers le client.

Chaque module doit être empaqueté dans un format spécifique, un fichier ZIP nommé NomModule_Version.zip, qui comprend le contenu du module. Une fois le fichier copié sur le serveur, un fichier de somme de contrôle doit être créé. Quand les clients se connectent au serveur, la somme de contrôle est utilisée pour vérifier que le contenu du module DSC n’a pas changé depuis sa publication.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Tâche de planification|
---|
Si vous planifiez un environnement de test ou de laboratoire, quels scénarios sont essentiels pour la validation ?|
Existe-t-il des modules à la disposition du public qui contiennent des ressources permettant de couvrir tout ce dont vous avez besoin ou devrez-vous créer vos propres ressources ?|
Votre environnement aura-t-il accès à Internet pour récupérer les modules publics ?|
Qui sera chargé de la vérification des modules DSC ?|
Si vous planifiez un environnement de production, qu’allez-vous utiliser comme dépôt local pour le stockage des modules DSC ?|
Une équipe centrale acceptera-t-elle les modules DSC des équipes d’application ? Quelle sera la procédure ?|
Automatiserez-vous l’empaquetage, la copie et la création d’une somme de contrôle pour les modules DSC prêts pour la production sur le serveur, à partir de votre dépôt source ?|
Votre équipe sera-t-elle également responsable de la gestion de la plateforme d’automatisation ?|

#### <a name="dsc-configurations"></a>Configurations DSC

Le rôle d’un serveur collecteur est de fournir un mécanisme centralisé pour la distribution des configurations DSC aux nœuds du client. Les configurations sont stockées sur le serveur sous la forme de documents MOF.
Chaque document est nommé avec un **Guid** unique. Quand les clients sont configurés pour se connecter à un serveur Pull, ils reçoivent également le **Guid** pour la configuration qu’ils doivent demander. Ce système de référencement des configurations par **Guid** garantit que chaque configuration est unique. Il offre aussi une flexibilité certaine, car il permet d’appliquer aussi bien une configuration avec une granularité spécifique par nœud qu’une configuration de rôle englobant plusieurs serveurs qui doivent avoir des configurations identiques.

#### <a name="guids"></a>Guids

Il convient d’apporter une attention supplémentaire à la planification des **Guids** de configuration lors de l’examen détaillé du déploiement d’un serveur Pull. Il n’existe aucune exigence spécifique concernant la façon de gérer les **Guids**, et il est probable que le processus sera propre à chaque environnement. Le processus peut aller du simple au complexe : un fichier CSV stocké de manière centralisée, une table SQL simple, une base de données de gestion des configurations (CMDB) ou une solution complexe nécessitant l’intégration à un autre outil ou une autre solution logicielle. Il existe deux approches générales :

- **Affectation de Guids par serveur** : fournit un moyen de garantir que chaque configuration de serveur est contrôlée individuellement. Cette approche fournit un niveau de précision autour des mises à jour et peut fonctionner correctement dans les environnements comportant peu de serveurs.
- **Affectation de Guids par rôle serveur** : tous les serveurs qui exécutent la même fonction, tels que les serveurs web, utilisent le même GUID pour référencer les données de configuration nécessaires.  Sachez que si de nombreux serveurs partagent le même GUID, tous sont mis à jour simultanément quand la configuration change.

  Le GUID doit être considéré comme une donnée sensible, car il peut être exploité par une personne ayant des intentions malveillantes pour recueillir des informations sur la façon dont les serveurs sont déployés et configurés dans votre environnement. Pour plus d’informations, consultez [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (Allocation de Guids de manière sécurisée dans la configuration de l’état désiré de PowerShell en mode Pull).

Tâche de planification|
---|
Qui sera chargé de la copie des configurations dans le dossier des serveurs collecteurs quand elles seront prêtes ?|
Si les configurations sont créées par une équipe d’application, quelle sera la procédure pour les transmettre ?|
Allez-vous exploiter un dépôt pour stocker les configurations à mesure qu’elles seront créées, entre les équipes ?|
Allez-vous automatiser le processus de copie des configurations sur le serveur et de création d’une somme de contrôle quand elles seront prêtes ?|
Comment mapperez-vous les Guids à des serveurs ou des rôles, et où seront-ils stockés ?|
Quel processus allez-vous utiliser pour configurer les machines clients et comment s’intégreront-elles à votre processus de création et de stockage de Guids de configuration ?|

## <a name="installation-guide"></a>Guide d’installation

*Les scripts fournis dans ce document sont des exemples stables. Examinez toujours attentivement les scripts avant de les exécuter dans un environnement de production.*

### <a name="prerequisites"></a>Conditions préalables

Pour vérifier la version de PowerShell installée sur votre serveur, utilisez la commande suivante.

```powershell
$PSVersionTable.PSVersion
```

Si possible, effectuez une mise à niveau avec la version la plus récente de Windows Management Framework.
Téléchargez ensuite le module `xPsDesiredStateConfiguration` à l’aide de la commande suivante.

```powershell
Install-Module xPSDesiredStateConfiguration
```

La commande vous demande votre approbation avant de télécharger le module.

### <a name="installation-and-configuration-scripts"></a>Installation et configuration de scripts

La meilleure méthode pour déployer un serveur collecteur DSC consiste à utiliser un script de configuration DSC. Ce document présente les scripts, notamment les paramètres de base permettant de configurer uniquement le service web DSC et les paramètres avancés permettant de configurer de bout en bout Windows Server comprenant un service web DSC.

Remarque :  Actuellement, le module DSC `xPSDesiredStateConfiguration` exige que le serveur utilise les paramètres régionaux en-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Configuration de base pour Windows Server 2012

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Configuration avancée pour Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>Vérifier les fonctionnalités du serveur collecteur

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Configurer les clients

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>Références, extraits de code et exemples supplémentaires

Cet exemple montre comment démarrer manuellement une connexion au client (nécessitant WMF5) pour les tests.

```powershell
Update-DscConfiguration –Wait -Verbose
```

L’applet de commande [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) est utilisée pour ajouter un enregistrement CNAME de type à une zone DNS.

La fonction PowerShell permettant de [créer une somme de contrôle et de publier un document MOF DSC sur un serveur collecteur SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) génère automatiquement la somme de contrôle exigée, puis copie les fichiers de configuration MOF et de somme de contrôle sur le serveur collecteur SMB.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Annexe - Présentation des types de fichiers de données du service ODATA

Un fichier de données est stocké pour créer des informations pendant le déploiement d’un serveur collecteur qui inclut le service web OData. Le type de fichier dépend du système d’exploitation, comme décrit ci-dessous.

- **Windows Server 2012** Le type de fichier est toujours .mdb
- **Windows Server 2012 R2** Le type de fichier est .edb par défaut, sauf si le type .mdb est spécifié dans la configuration

Dans l’[exemple de script avancé](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) d’installation un serveur collecteur, vous trouverez également un exemple de la façon de contrôler automatiquement les paramètres du fichier web.config pour empêcher tout risque d’erreur provoquée par le type de fichier.
