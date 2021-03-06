---
ms.date: 04/11/2018
keywords: dsc,powershell,configuration,installation
title: Configuration d’un serveur collecteur SMB DSC
description: Un serveur collecteur SMB DSC est un ordinateur qui héberge des partages de fichiers SMB qui fournissent des fichiers de configuration DSC et des ressources DSC aux nœuds cibles quand ces derniers les demandent.
ms.openlocfilehash: 4ac1b0db719fa124d6fa9a654acb64ec24d9ea41
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658433"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Configuration d’un serveur collecteur SMB DSC

S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC* ) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

Un serveur collecteur [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) DSC est un ordinateur qui héberge des partages de fichiers SMB qui fournissent des fichiers de configuration DSC et des ressources DSC aux nœuds cibles quand ces derniers les demandent.

Pour utiliser un serveur collecteur SMB pour DSC, vous devez effectuer les étapes suivantes :

- Configurer un partage de fichiers SMB sur un serveur qui exécute PowerShell 4.0 ou version ultérieure
- Configurer un client qui exécute PowerShell 4.0 ou version ultérieure pour l’extraction à partir de ce partage SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Utilisation de la ressource xSmbShare pour créer un partage de fichiers SMB

Il existe plusieurs façons de configurer un partage de fichiers SMB, mais nous allons le faire à l’aide de DSC.

### <a name="install-the-xsmbshare-resource"></a>Installer la ressource xSmbShare

Appelez l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module) pour installer le module **xSmbShare** .

> [!NOTE]
> `Install-Module` est inclus dans le module **PowerShellGet** de PowerShell 5.0.
> **xSmbShare** contient la ressource DSC **xSmbShare** qui peut être utilisée pour créer un partage de fichiers SMB.

### <a name="create-the-directory-and-file-share"></a>Créer le répertoire et le partage de fichiers

La configuration suivante utilise la ressource **File** pour créer le répertoire du partage et la ressource **xSmbShare** pour configurer le partage SMB :

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

La configuration crée le répertoire `C:\DscSmbShare`, s’il n’existe pas, et utilise ensuite ce répertoire comme partage de fichiers SMB. L’autorisation **FullAccess** doit être accordée à tous les comptes qui doivent écrire dans le partage de fichiers ou en supprimer un élément. L’autorisation **ReadAccess** doit être accordée à tous les nœuds clients qui obtiennent des configurations et/ou des ressources DSC à partir du partage.

> [!NOTE]
> DSC s’exécutant sous le compte système par défaut, l’ordinateur doit avoir accès au partage.

### <a name="give-file-system-access-to-the-pull-client"></a>Donner accès au système de fichiers pour le client collecteur

L’autorisation **ReadAccess** accordée à un nœud client permet à ce dernier d’accéder au partage SMB, mais pas aux fichiers et dossiers dans ce partage. Vous devez accorder explicitement aux nœuds clients l’accès au dossier et aux sous-dossiers du partage SMB. Vous pouvez le faire avec DSC à l’aide de la ressource **cNtfsPermissionEntry** , qui est contenue dans le module [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0).
La configuration suivante ajoute un bloc **cNtfsPermissionEntry** qui accorde un accès ReadAndExecute au client collecteur :

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a>Placement des configurations et des ressources

Enregistrez les fichiers MOF de configuration et/ou les ressources DSC que les nœuds clients doivent extraire dans le dossier de partage SMB.

Les fichiers MOF de configuration doivent être nommés *ConfigurationID* .mof, où *ConfigurationID* est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible. Pour plus d’informations sur la configuration des clients collecteurs, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md).

> [!NOTE]
> Vous devez utiliser les ID de configuration si vous utilisez un serveur collecteur SMB. Les noms de configuration ne sont pas pris en charge pour SMB.

Chaque module de ressources doit être compressé et nommé selon le modèle suivant : `{Module Name}_{Module Version}.zip` Par exemple, un module xWebAdminstration avec une version de module 3.1.2.0 est nommé « xWebAdministration_3.2.1.0.zip ». Chaque version d’un module doit être contenue dans un seul fichier zip. Les versions distinctes d’un module dans un fichier zip ne sont pas prises en charge.
Avant de créer le package des modules de ressources DSC à utiliser avec le serveur collecteur, vous devez apporter une petite modification à la structure de répertoires.

Le format par défaut des modules contenant des ressources DSC dans WMF 5.0 est `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Avant de créer des packages pour le serveur collecteur, supprimez simplement le dossier `{Module version}` afin que le chemin devienne `{Module Folder}\DscResources\{DSC Resource Folder}\`. Ensuite, compressez le dossier comme décrit ci-dessus, et placez ces fichiers zip dans le dossier de partage SMB.

## <a name="creating-the-mof-checksum"></a>Création de la somme de contrôle MOF

Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration. Pour créer une somme de contrôle, appelez l’applet de commande [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum). L’applet de commande prend un paramètre `Path` qui spécifie le dossier où se trouve la configuration MOF. L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration. S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier.

Le fichier de somme de contrôle doit être présent dans le même répertoire que celui du fichier MOF de configuration (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` par défaut), et avoir le même nom, mais avec l’extension `.checksum`.

> [!NOTE]
> Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.

## <a name="setting-up-a-pull-client-for-smb"></a>Configuration d’un client collecteur pour SMB

Pour configurer un client qui extrait des configurations et/ou des ressources à partir d’un partage SMB, configurez le Gestionnaire de configuration local (LCM) du client avec des blocs **ConfigurationRepositoryShare** et **ResourceRepositoryShare** qui spécifient le partage à partir duquel les configurations et les ressources DSC sont extraites.

Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md).

> [!NOTE]
> Par souci de simplicité, cet exemple utilise **PSDscAllowPlainTextPassword** pour autoriser la transmission d’un mot de passe en texte clair au paramètre **Informations d’identification** . Pour plus d’informations sur la transmission plus sécurisée d’informations d’identification, consultez [Options d’informations d’identification dans les données de configuration](../configurations/configDataCredentials.md). Vous **DEVEZ** spécifier un **ConfigurationID** dans le bloc **Paramètres** d’une métaconfiguration pour un serveur d’extraction SMB, même si vous ne faites qu’extraire des ressources.

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a>Remerciements

Un remerciement particulier aux personnes suivantes :

- Mike F. Robbins, dont les billets sur l’utilisation de SMB pour DSC ont permis de documenter le contenu de cette rubrique. Son blog : [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, qui a créé le module **cNtfsAccessControl** . La source de ce module se trouve dans [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](../overview/overview.md)

[Application des configurations](enactingConfigurations.md)

[Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md)
