---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Améliorations de DSC dans WMF 5.1
ms.openlocfilehash: a5efa38ce791a893580316bad7b61a6689153a86
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416672"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Améliorations de la configuration de l’état souhaité (DSC) dans WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Améliorations des ressources de classe DSC

Dans WMF 5.1, nous avons résolu les problèmes connus suivants :

- Get-DscConfiguration peut retourner des valeurs vides (Null) ou des erreurs si un type complexe/de table de hachage est retourné par la fonction Get() d’une ressource DSC basée sur une classe.
- Get-DscConfiguration retourne une erreur si des informations d’identification RunAs sont utilisées dans une configuration DSC.
- Une ressource basée sur une classe ne peut pas être utilisée dans une configuration composite.
- Start-DscConfiguration se bloque si une ressource basée sur une classe a une propriété de son propre type.
- Une ressource basée sur une classe ne peut pas être utilisée comme ressource exclusive.

## <a name="dsc-resource-debugging-improvements"></a>Améliorations du débogage des ressources DSC

Dans WMF 5.0, le débogueur PowerShell ne s’arrêtait pas directement sur la méthode de ressource basée sur une classe (Get/Set/Test). Dans WMF 5.1, le débogueur s’arrête sur la méthode de ressource basée sur une classe de la même façon que sur des méthodes de ressources basées sur un fichier MOF.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>Le client collecteur DSC prend en charge TLS 1.1 et TLS 1.2

Avant, le client collecteur DSC ne prenait en charge que SSL 3.0 et TLS 1.0 sur des connexions HTTPS. Quand il est contraint d’utiliser des protocoles plus sécurisés, le client collecteur cesse de fonctionner. Dans WMF 5.1, le client collecteur DSC ne prend plus en charge SSL 3.0, mais prend en charge les protocoles plus sécurisés TLS 1.1 et TLS 1.2.

## <a name="improved-pull-server-registration"></a>Inscription du serveur collecteur améliorée

Dans les versions antérieures de WMF, les inscriptions/demandes de création de rapports simultanées auprès d’un serveur collecteur DSC lors de l’utilisation de la base de données ESENT aboutissaient à un échec de l’inscription/de la création de rapport par le Gestionnaire de configuration local. Dans ce cas, les journaux des événements sur le serveur collecteur affichent l’erreur « Le nom d’instance est déjà utilisé ». Elle était due au fait que le modèle utilisé pour accéder à la base de données ESENT dans un scénario multithread était incorrect. Dans WMF 5.1, ce problème a été résolu. Les inscriptions ou demandes de création de rapports simultanées (impliquant la base de données ESENT) fonctionnent correctement dans WMF 5.1. Ce problème s’applique uniquement à la base de données ESENT et ne s’applique pas à la base de données OLE DB.

## <a name="enable-circular-log-on-esent-database-instance"></a>Activer le journal circulaire sur l’instance de la base de données ESENT

Dans la version antérieure de DSC-PullServer, les fichiers journaux de la base de données ESENT saturaient l’espace disque du serveur collecteur, car l’instance de la base de données était créée sans journalisation circulaire. Dans cette version, vous pouvez utiliser le fichier web.config du serveur collecteur pour contrôler le comportement de la journalisation circulaire. Par défaut, CircularLogging a la valeur TRUE.

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>Prise en charge WOW64 pour le mot clé Configuration

Le mot clé `Configuration` est maintenant pris en charge dans WOW64 sur un ordinateur 64 bits. Cela signifie qu’une configuration DSC peut être définie et compilée dans un processus 32 bits tel que Windows PowerShell ISE (x86) exécuté sur un ordinateur 64 bits.

## <a name="pull-partial-configuration-naming-convention"></a>Convention de nommage pour une configuration partielle de collecte

Dans la version précédente, la convention de nommage pour une configuration partielle précisait que le nom du fichier MOF dans le service/serveur collecteur devait correspondre au nom de configuration partielle spécifié dans les paramètres du gestionnaire de configuration local qui, à son tour, devait correspondre au nom de configuration incorporé dans le fichier MOF.

Consultez les captures instantanées ci-dessous :

- Paramètres de configuration locale qui définissent une configuration partielle qu’un nœud est autorisé à recevoir.

  ![Exemple de métaconfiguration](../images/DSC-improvements/MetaConfigPartialOne.png)

- Exemple de définition d’une configuration partielle

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

- « ConfigurationName » incorporé dans le fichier MOF généré

  ![Exemple de fichier mof généré](../images/DSC-improvements/PartialGeneratedMof.png)

- FileName dans le référentiel de configuration de tirage (pull)

  ![FileName dans le dépôt de configuration](../images/DSC-improvements/PartialInConfigRepository.png)

  Le nom de service Azure Automation a généré des fichiers MOF sous la forme `<ConfigurationName>.<NodeName>.mof`. Par conséquent, la configuration ci-dessous est compilée dans PartialOne.localhost.mof.

  Il est ainsi impossible de collecter l’une de vos configurations partielles à partir du service Azure Automation.

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

  Dans WMF 5.1, une configuration partielle dans le service/serveur collecteur peut être nommée `<ConfigurationName>.<NodeName>.mof`. En outre, si un ordinateur collecte une seule configuration d’un service/serveur collecteur, le fichier de configuration dans le dépôt de configuration du serveur collecteur peut avoir n’importe quel nom. Cette souplesse d’attribution des noms vous permet de gérer vos nœuds en partie à l’aide du service Azure Automation, où certains éléments de la configuration de votre nœud proviennent d’Azure Automation DSC tandis que d’autres sont gérés par vous en local.

  La métaconfiguration ci-dessous définit un nœud à gérer à la fois localement et par le service Azure Automation.

  ```powershell
  [DscLocalConfigurationManager()]
  Configuration RegistrationMetaConfig
  {
      Settings
      {
          RefreshFrequencyMins = 30
          RefreshMode = "PULL"
      }

      ConfigurationRepositoryWeb web
      {
          ServerURL =  $endPoint
          RegistrationKey = $registrationKey
          ConfigurationNames = $configurationName
      }

      # Partial configuration managed by Azure Automation service.
      PartialConfiguration PartialConfigurationManagedByAzureAutomation
      {
          ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
      }

      # This partial configuration is managed locally.
      PartialConfiguration OnPremisesConfig
      {
          RefreshMode = "PUSH"
          ExclusiveResources = @("Script")
      }

  }

  RegistrationMetaConfig
  Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
  ```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Utilisation de PsDscRunAsCredential avec des ressources composites DSC

Nous avons ajouté la prise en charge de [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) avec des ressources [composites](/powershell/scripting/dsc/authoringresourcecomposite) DSC.

Il est maintenant possible de spécifier une valeur pour **PsDscRunAsCredential** tout en utilisant des ressources composites dans les configurations. Le cas échéant, toutes les ressources sont exécutées dans une ressource composite en tant qu’utilisateur RunAs. Si une ressource composite en appelle d’autres, toutes ces ressources sont également exécutées en tant qu’utilisateur RunAs. Les informations d’identification RunAs sont propagées à tout niveau de la hiérarchie des ressources composites. Si une ressource située à l’intérieur d’une ressource composite spécifie sa propre valeur de **PsDscRunAsCredential**, une erreur de fusion se produit pendant la compilation de la configuration.

Cet exemple illustre l’utilisation de la ressource composite [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) incluse dans le module PSDesiredStateConfiguration.

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Autorisation des ressources en double identiques dans une configuration

DSC n’autorise pas et ne gère pas les définitions de ressources conflictuelles dans une configuration. Au lieu d’essayer de résoudre le conflit, il échoue tout simplement. Avec l’augmentation de la réutilisation des configurations due, entre autres, aux ressources composites, des conflits se produiront plus souvent. Quand des définitions de ressources conflictuelles sont identiques, DSC doit agir intelligemment et les autoriser. Dans cette version, l’existence de plusieurs instances de ressources ayant des définitions identiques est prise en charge :

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

Dans les versions précédentes, le résultat était un échec de compilation dû à un conflit, car les instances de WindowsFeature FE_IIS et WindowsFeature Worker_IIS essayaient de garantir l’installation du rôle « Serveur Web ». Notez que *toutes* les propriétés configurées sont identiques dans ces deux configurations. Étant donné que *toutes* les propriétés de ces deux ressources sont identiques, désormais la compilation réussit.

Si les deux ressources présentent des propriétés différentes, elles ne sont pas considérées comme identiques et la compilation échoue.

## <a name="dsc-module-and-configuration-signing-validations"></a>Validations des signatures de configurations et de modules DSC

Dans DSC, les configurations et les modules sont distribués à des ordinateurs gérés à partir du serveur collecteur. Dans le cas où le serveur Pull serait compromis, un attaquant pourrait modifier ses configurations et ses modules pour les distribuer à tous les nœuds gérés.

Dans WMF 5.1, DSC prend en charge la validation des signatures numériques sur les fichiers catalogue et de configuration (.MOF). Cette fonctionnalité empêche les nœuds d’exécuter des configurations ou des fichiers de modules qui ne sont pas signés par un signataire approuvé ou qui ont été falsifiés après avoir été signés par le signataire approuvé.

### <a name="how-to-sign-configuration-and-module"></a>Comment signer des configurations et modules

- Fichiers de configuration (.mof) : la cmdlet PowerShell existante [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) est étendue de façon à prendre en charge la signature des fichiers MOF.
- Modules : la signature de modules s’effectue en signant le catalogue de module correspondant :
  1. Créer un fichier catalogue : un fichier catalogue contient une collection de hachages de chiffrement ou d’empreintes. Chaque empreinte correspond à un fichier qui est inclus dans le module. La nouvelle applet de commande [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog) a été ajoutée pour permettre aux utilisateurs de créer un fichier catalogue pour leur module.
  2. Signer le fichier catalogue : utilisez [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) pour signer le fichier catalogue.
  3. Placer le fichier catalogue dans le dossier de module. Par convention, le fichier catalogue de module doit être placé sous le dossier de module portant le même nom que le module.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Paramètres du gestionnaire de configuration local pour activer les validations des signatures

#### <a name="pull"></a>Extraction

Le gestionnaire de configuration local d’un nœud effectue une validation des signatures des modules et des configurations en fonction de ses paramètres actifs. Par défaut, la validation des signatures est désactivée. La validation des signatures peut être activée en ajoutant le bloc « SignatureValidation » à la définition de métaconfiguration du nœud, comme indiqué ci-dessous :

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

La définition de la métaconfiguration ci-dessus sur un nœud active la validation des signatures sur les configurations et modules téléchargés. Le gestionnaire de configuration local effectue les étapes suivantes pour vérifier les signatures numériques.

1. Il vérifie que la signature du fichier de configuration (.MOF) est valide avec la cmdlet `Get-AuthenticodeSignature`.
2. Il vérifie que l’autorité de certification qui a autorisé le signataire est approuvée.
3. Il télécharge les dépendances de ressources/modules de la configuration à un emplacement temporaire.
4. Il vérifie la signature du catalogue qui figure dans le module.
   - Il recherche un fichier `<moduleName>.cat` et vérifie sa signature avec `Get-AuthenticodeSignature`.
   - Il vérifie que l’autorité de certification qui a authentifié le signataire est approuvée.
   - Il vérifie que le contenu des modules n’a pas été falsifié avec la nouvelle cmdlet `Test-FileCatalog`.
5. Il lance `Install-Module` sur `$env:ProgramFiles\WindowsPowerShell\Modules\`.
6. Il traite la configuration

> [!NOTE]
> la validation des signatures sur le catalogue de module et la configuration n’est effectuée que la première fois où la configuration est appliquée au système et lors du téléchargement et de l’installation du module.
> Les séries de tests de cohérence ne valident pas la signature de Current.mof ni ses dépendances de modules. Si la vérification a échoué à un stade, par exemple si la configuration extraite à partir du serveur collecteur n’est pas signée, le traitement de la configuration s’arrête avec l’erreur affichée ci-dessous et tous les fichiers temporaires sont supprimés.

![Exemple de configuration de sortie d’erreur](../images/DSC-improvements/PullUnsignedConfigFail.png)

De la même manière, l’extraction d’un module dont le catalogue n’est pas signé entraîne l’erreur suivante :

![Exemple de module de sortie d’erreur](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a>Envoi

Une configuration fournie à l’aide d’une transmission de type push peut être falsifiée à sa source avant d’être remise au nœud. Le gestionnaire de configuration local effectue des étapes de validation des signatures similaires pour les configurations envoyées ou publiées. Voici un exemple complet de validation des signatures pour l’envoi.

- Activez la validation des signatures sur le nœud.

  ```powershell
  [DSCLocalConfigurationManager()]
  Configuration EnableSignatureValidation
  {
      Settings
      {
          RefreshMode = 'PUSH'
      }
      SignatureValidation validations{
          TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
          SignedItemType =  'Configuration','Module'
      }

  }
  EnableSignatureValidation
  Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
  ```

- Créez un exemple de fichier de configuration.

  ```powershell
  # Sample configuration
  Configuration Test
  {

      File foo
      {
          DestinationPath =  "$env:TEMP\signingTest.txt"
          Contents = "ABC"
      }
  }
  Test
  ```

- Essayez d’envoyer le fichier de configuration non signé au nœud.

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- Signez le fichier de configuration avec un certificat de signature de code.

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- Essayez de transmettre par push le fichier MOF signé.

  ![PushSignedMofFile](../images/DSC-improvements/PushSignedMof.png)
