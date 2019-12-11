---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Améliorations de DSC dans WMF 5.1
ms.openlocfilehash: a5efa38ce791a893580316bad7b61a6689153a86
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416672"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="45e19-103">Améliorations de la configuration de l’état souhaité (DSC) dans WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="45e19-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="45e19-104">Améliorations des ressources de classe DSC</span><span class="sxs-lookup"><span data-stu-id="45e19-104">DSC class resource improvements</span></span>

<span data-ttu-id="45e19-105">Dans WMF 5.1, nous avons résolu les problèmes connus suivants :</span><span class="sxs-lookup"><span data-stu-id="45e19-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="45e19-106">Get-DscConfiguration peut retourner des valeurs vides (Null) ou des erreurs si un type complexe/de table de hachage est retourné par la fonction Get() d’une ressource DSC basée sur une classe.</span><span class="sxs-lookup"><span data-stu-id="45e19-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="45e19-107">Get-DscConfiguration retourne une erreur si des informations d’identification RunAs sont utilisées dans une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="45e19-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="45e19-108">Une ressource basée sur une classe ne peut pas être utilisée dans une configuration composite.</span><span class="sxs-lookup"><span data-stu-id="45e19-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="45e19-109">Start-DscConfiguration se bloque si une ressource basée sur une classe a une propriété de son propre type.</span><span class="sxs-lookup"><span data-stu-id="45e19-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="45e19-110">Une ressource basée sur une classe ne peut pas être utilisée comme ressource exclusive.</span><span class="sxs-lookup"><span data-stu-id="45e19-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="45e19-111">Améliorations du débogage des ressources DSC</span><span class="sxs-lookup"><span data-stu-id="45e19-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="45e19-112">Dans WMF 5.0, le débogueur PowerShell ne s’arrêtait pas directement sur la méthode de ressource basée sur une classe (Get/Set/Test).</span><span class="sxs-lookup"><span data-stu-id="45e19-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="45e19-113">Dans WMF 5.1, le débogueur s’arrête sur la méthode de ressource basée sur une classe de la même façon que sur des méthodes de ressources basées sur un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="45e19-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="45e19-114">Le client collecteur DSC prend en charge TLS 1.1 et TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="45e19-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="45e19-115">Avant, le client collecteur DSC ne prenait en charge que SSL 3.0 et TLS 1.0 sur des connexions HTTPS.</span><span class="sxs-lookup"><span data-stu-id="45e19-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="45e19-116">Quand il est contraint d’utiliser des protocoles plus sécurisés, le client collecteur cesse de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="45e19-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="45e19-117">Dans WMF 5.1, le client collecteur DSC ne prend plus en charge SSL 3.0, mais prend en charge les protocoles plus sécurisés TLS 1.1 et TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="45e19-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="45e19-118">Inscription du serveur collecteur améliorée</span><span class="sxs-lookup"><span data-stu-id="45e19-118">Improved pull server registration</span></span>

<span data-ttu-id="45e19-119">Dans les versions antérieures de WMF, les inscriptions/demandes de création de rapports simultanées auprès d’un serveur collecteur DSC lors de l’utilisation de la base de données ESENT aboutissaient à un échec de l’inscription/de la création de rapport par le Gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="45e19-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="45e19-120">Dans ce cas, les journaux des événements sur le serveur collecteur affichent l’erreur « Le nom d’instance est déjà utilisé ».</span><span class="sxs-lookup"><span data-stu-id="45e19-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="45e19-121">Elle était due au fait que le modèle utilisé pour accéder à la base de données ESENT dans un scénario multithread était incorrect.</span><span class="sxs-lookup"><span data-stu-id="45e19-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="45e19-122">Dans WMF 5.1, ce problème a été résolu.</span><span class="sxs-lookup"><span data-stu-id="45e19-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="45e19-123">Les inscriptions ou demandes de création de rapports simultanées (impliquant la base de données ESENT) fonctionnent correctement dans WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="45e19-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="45e19-124">Ce problème s’applique uniquement à la base de données ESENT et ne s’applique pas à la base de données OLE DB.</span><span class="sxs-lookup"><span data-stu-id="45e19-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="45e19-125">Activer le journal circulaire sur l’instance de la base de données ESENT</span><span class="sxs-lookup"><span data-stu-id="45e19-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="45e19-126">Dans la version antérieure de DSC-PullServer, les fichiers journaux de la base de données ESENT saturaient l’espace disque du serveur collecteur, car l’instance de la base de données était créée sans journalisation circulaire.</span><span class="sxs-lookup"><span data-stu-id="45e19-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="45e19-127">Dans cette version, vous pouvez utiliser le fichier web.config du serveur collecteur pour contrôler le comportement de la journalisation circulaire.</span><span class="sxs-lookup"><span data-stu-id="45e19-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="45e19-128">Par défaut, CircularLogging a la valeur TRUE.</span><span class="sxs-lookup"><span data-stu-id="45e19-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="45e19-129">Prise en charge WOW64 pour le mot clé Configuration</span><span class="sxs-lookup"><span data-stu-id="45e19-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="45e19-130">Le mot clé `Configuration` est maintenant pris en charge dans WOW64 sur un ordinateur 64 bits.</span><span class="sxs-lookup"><span data-stu-id="45e19-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="45e19-131">Cela signifie qu’une configuration DSC peut être définie et compilée dans un processus 32 bits tel que Windows PowerShell ISE (x86) exécuté sur un ordinateur 64 bits.</span><span class="sxs-lookup"><span data-stu-id="45e19-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="45e19-132">Convention de nommage pour une configuration partielle de collecte</span><span class="sxs-lookup"><span data-stu-id="45e19-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="45e19-133">Dans la version précédente, la convention de nommage pour une configuration partielle précisait que le nom du fichier MOF dans le service/serveur collecteur devait correspondre au nom de configuration partielle spécifié dans les paramètres du gestionnaire de configuration local qui, à son tour, devait correspondre au nom de configuration incorporé dans le fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="45e19-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="45e19-134">Consultez les captures instantanées ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="45e19-134">See the snapshots below:</span></span>

- <span data-ttu-id="45e19-135">Paramètres de configuration locale qui définissent une configuration partielle qu’un nœud est autorisé à recevoir.</span><span class="sxs-lookup"><span data-stu-id="45e19-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Exemple de métaconfiguration](../images/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="45e19-137">Exemple de définition d’une configuration partielle</span><span class="sxs-lookup"><span data-stu-id="45e19-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="45e19-138">« ConfigurationName » incorporé dans le fichier MOF généré</span><span class="sxs-lookup"><span data-stu-id="45e19-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Exemple de fichier mof généré](../images/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="45e19-140">FileName dans le référentiel de configuration de tirage (pull)</span><span class="sxs-lookup"><span data-stu-id="45e19-140">FileName in the pull configuration repository</span></span>

  ![FileName dans le dépôt de configuration](../images/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="45e19-142">Le nom de service Azure Automation a généré des fichiers MOF sous la forme `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="45e19-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="45e19-143">Par conséquent, la configuration ci-dessous est compilée dans PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="45e19-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="45e19-144">Il est ainsi impossible de collecter l’une de vos configurations partielles à partir du service Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="45e19-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="45e19-145">Dans WMF 5.1, une configuration partielle dans le service/serveur collecteur peut être nommée `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="45e19-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="45e19-146">En outre, si un ordinateur collecte une seule configuration d’un service/serveur collecteur, le fichier de configuration dans le dépôt de configuration du serveur collecteur peut avoir n’importe quel nom.</span><span class="sxs-lookup"><span data-stu-id="45e19-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="45e19-147">Cette souplesse d’attribution des noms vous permet de gérer vos nœuds en partie à l’aide du service Azure Automation, où certains éléments de la configuration de votre nœud proviennent d’Azure Automation DSC tandis que d’autres sont gérés par vous en local.</span><span class="sxs-lookup"><span data-stu-id="45e19-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="45e19-148">La métaconfiguration ci-dessous définit un nœud à gérer à la fois localement et par le service Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="45e19-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="45e19-149">Utilisation de PsDscRunAsCredential avec des ressources composites DSC</span><span class="sxs-lookup"><span data-stu-id="45e19-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="45e19-150">Nous avons ajouté la prise en charge de [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) avec des ressources [composites](/powershell/scripting/dsc/authoringresourcecomposite) DSC.</span><span class="sxs-lookup"><span data-stu-id="45e19-150">We have added support for using [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) with DSC [Composite](/powershell/scripting/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="45e19-151">Il est maintenant possible de spécifier une valeur pour **PsDscRunAsCredential** tout en utilisant des ressources composites dans les configurations.</span><span class="sxs-lookup"><span data-stu-id="45e19-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="45e19-152">Le cas échéant, toutes les ressources sont exécutées dans une ressource composite en tant qu’utilisateur RunAs.</span><span class="sxs-lookup"><span data-stu-id="45e19-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="45e19-153">Si une ressource composite en appelle d’autres, toutes ces ressources sont également exécutées en tant qu’utilisateur RunAs.</span><span class="sxs-lookup"><span data-stu-id="45e19-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="45e19-154">Les informations d’identification RunAs sont propagées à tout niveau de la hiérarchie des ressources composites.</span><span class="sxs-lookup"><span data-stu-id="45e19-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="45e19-155">Si une ressource située à l’intérieur d’une ressource composite spécifie sa propre valeur de **PsDscRunAsCredential**, une erreur de fusion se produit pendant la compilation de la configuration.</span><span class="sxs-lookup"><span data-stu-id="45e19-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="45e19-156">Cet exemple illustre l’utilisation de la ressource composite [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) incluse dans le module PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="45e19-156">This example shows usage with the [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="45e19-157">Autorisation des ressources en double identiques dans une configuration</span><span class="sxs-lookup"><span data-stu-id="45e19-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="45e19-158">DSC n’autorise pas et ne gère pas les définitions de ressources conflictuelles dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="45e19-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="45e19-159">Au lieu d’essayer de résoudre le conflit, il échoue tout simplement.</span><span class="sxs-lookup"><span data-stu-id="45e19-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="45e19-160">Avec l’augmentation de la réutilisation des configurations due, entre autres, aux ressources composites, des conflits se produiront plus souvent.</span><span class="sxs-lookup"><span data-stu-id="45e19-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="45e19-161">Quand des définitions de ressources conflictuelles sont identiques, DSC doit agir intelligemment et les autoriser.</span><span class="sxs-lookup"><span data-stu-id="45e19-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="45e19-162">Dans cette version, l’existence de plusieurs instances de ressources ayant des définitions identiques est prise en charge :</span><span class="sxs-lookup"><span data-stu-id="45e19-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="45e19-163">Dans les versions précédentes, le résultat était un échec de compilation dû à un conflit, car les instances de WindowsFeature FE_IIS et WindowsFeature Worker_IIS essayaient de garantir l’installation du rôle « Serveur Web ».</span><span class="sxs-lookup"><span data-stu-id="45e19-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="45e19-164">Notez que *toutes* les propriétés configurées sont identiques dans ces deux configurations.</span><span class="sxs-lookup"><span data-stu-id="45e19-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="45e19-165">Étant donné que *toutes* les propriétés de ces deux ressources sont identiques, désormais la compilation réussit.</span><span class="sxs-lookup"><span data-stu-id="45e19-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="45e19-166">Si les deux ressources présentent des propriétés différentes, elles ne sont pas considérées comme identiques et la compilation échoue.</span><span class="sxs-lookup"><span data-stu-id="45e19-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="45e19-167">Validations des signatures de configurations et de modules DSC</span><span class="sxs-lookup"><span data-stu-id="45e19-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="45e19-168">Dans DSC, les configurations et les modules sont distribués à des ordinateurs gérés à partir du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="45e19-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="45e19-169">Dans le cas où le serveur Pull serait compromis, un attaquant pourrait modifier ses configurations et ses modules pour les distribuer à tous les nœuds gérés.</span><span class="sxs-lookup"><span data-stu-id="45e19-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="45e19-170">Dans WMF 5.1, DSC prend en charge la validation des signatures numériques sur les fichiers catalogue et de configuration (.MOF).</span><span class="sxs-lookup"><span data-stu-id="45e19-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="45e19-171">Cette fonctionnalité empêche les nœuds d’exécuter des configurations ou des fichiers de modules qui ne sont pas signés par un signataire approuvé ou qui ont été falsifiés après avoir été signés par le signataire approuvé.</span><span class="sxs-lookup"><span data-stu-id="45e19-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="45e19-172">Comment signer des configurations et modules</span><span class="sxs-lookup"><span data-stu-id="45e19-172">How to sign configuration and module</span></span>

- <span data-ttu-id="45e19-173">Fichiers de configuration (.mof) : la cmdlet PowerShell existante [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) est étendue de façon à prendre en charge la signature des fichiers MOF.</span><span class="sxs-lookup"><span data-stu-id="45e19-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="45e19-174">Modules : la signature de modules s’effectue en signant le catalogue de module correspondant :</span><span class="sxs-lookup"><span data-stu-id="45e19-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="45e19-175">Créer un fichier catalogue : un fichier catalogue contient une collection de hachages de chiffrement ou d’empreintes.</span><span class="sxs-lookup"><span data-stu-id="45e19-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="45e19-176">Chaque empreinte correspond à un fichier qui est inclus dans le module.</span><span class="sxs-lookup"><span data-stu-id="45e19-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="45e19-177">La nouvelle applet de commande [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog) a été ajoutée pour permettre aux utilisateurs de créer un fichier catalogue pour leur module.</span><span class="sxs-lookup"><span data-stu-id="45e19-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="45e19-178">Signer le fichier catalogue : utilisez [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) pour signer le fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="45e19-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="45e19-179">Placer le fichier catalogue dans le dossier de module.</span><span class="sxs-lookup"><span data-stu-id="45e19-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="45e19-180">Par convention, le fichier catalogue de module doit être placé sous le dossier de module portant le même nom que le module.</span><span class="sxs-lookup"><span data-stu-id="45e19-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="45e19-181">Paramètres du gestionnaire de configuration local pour activer les validations des signatures</span><span class="sxs-lookup"><span data-stu-id="45e19-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="45e19-182">Extraction</span><span class="sxs-lookup"><span data-stu-id="45e19-182">Pull</span></span>

<span data-ttu-id="45e19-183">Le gestionnaire de configuration local d’un nœud effectue une validation des signatures des modules et des configurations en fonction de ses paramètres actifs.</span><span class="sxs-lookup"><span data-stu-id="45e19-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="45e19-184">Par défaut, la validation des signatures est désactivée.</span><span class="sxs-lookup"><span data-stu-id="45e19-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="45e19-185">La validation des signatures peut être activée en ajoutant le bloc « SignatureValidation » à la définition de métaconfiguration du nœud, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="45e19-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="45e19-186">La définition de la métaconfiguration ci-dessus sur un nœud active la validation des signatures sur les configurations et modules téléchargés.</span><span class="sxs-lookup"><span data-stu-id="45e19-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="45e19-187">Le gestionnaire de configuration local effectue les étapes suivantes pour vérifier les signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="45e19-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="45e19-188">Il vérifie que la signature du fichier de configuration (.MOF) est valide avec la cmdlet `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="45e19-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="45e19-189">Il vérifie que l’autorité de certification qui a autorisé le signataire est approuvée.</span><span class="sxs-lookup"><span data-stu-id="45e19-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="45e19-190">Il télécharge les dépendances de ressources/modules de la configuration à un emplacement temporaire.</span><span class="sxs-lookup"><span data-stu-id="45e19-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="45e19-191">Il vérifie la signature du catalogue qui figure dans le module.</span><span class="sxs-lookup"><span data-stu-id="45e19-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="45e19-192">Il recherche un fichier `<moduleName>.cat` et vérifie sa signature avec `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="45e19-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="45e19-193">Il vérifie que l’autorité de certification qui a authentifié le signataire est approuvée.</span><span class="sxs-lookup"><span data-stu-id="45e19-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="45e19-194">Il vérifie que le contenu des modules n’a pas été falsifié avec la nouvelle cmdlet `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="45e19-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="45e19-195">Il lance `Install-Module` sur `$env:ProgramFiles\WindowsPowerShell\Modules\`.</span><span class="sxs-lookup"><span data-stu-id="45e19-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="45e19-196">Il traite la configuration</span><span class="sxs-lookup"><span data-stu-id="45e19-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="45e19-197">la validation des signatures sur le catalogue de module et la configuration n’est effectuée que la première fois où la configuration est appliquée au système et lors du téléchargement et de l’installation du module.</span><span class="sxs-lookup"><span data-stu-id="45e19-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="45e19-198">Les séries de tests de cohérence ne valident pas la signature de Current.mof ni ses dépendances de modules.</span><span class="sxs-lookup"><span data-stu-id="45e19-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="45e19-199">Si la vérification a échoué à un stade, par exemple si la configuration extraite à partir du serveur collecteur n’est pas signée, le traitement de la configuration s’arrête avec l’erreur affichée ci-dessous et tous les fichiers temporaires sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="45e19-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Exemple de configuration de sortie d’erreur](../images/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="45e19-201">De la même manière, l’extraction d’un module dont le catalogue n’est pas signé entraîne l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="45e19-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Exemple de module de sortie d’erreur](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="45e19-203">Envoi</span><span class="sxs-lookup"><span data-stu-id="45e19-203">Push</span></span>

<span data-ttu-id="45e19-204">Une configuration fournie à l’aide d’une transmission de type push peut être falsifiée à sa source avant d’être remise au nœud.</span><span class="sxs-lookup"><span data-stu-id="45e19-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="45e19-205">Le gestionnaire de configuration local effectue des étapes de validation des signatures similaires pour les configurations envoyées ou publiées.</span><span class="sxs-lookup"><span data-stu-id="45e19-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="45e19-206">Voici un exemple complet de validation des signatures pour l’envoi.</span><span class="sxs-lookup"><span data-stu-id="45e19-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="45e19-207">Activez la validation des signatures sur le nœud.</span><span class="sxs-lookup"><span data-stu-id="45e19-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="45e19-208">Créez un exemple de fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="45e19-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="45e19-209">Essayez d’envoyer le fichier de configuration non signé au nœud.</span><span class="sxs-lookup"><span data-stu-id="45e19-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="45e19-211">Signez le fichier de configuration avec un certificat de signature de code.</span><span class="sxs-lookup"><span data-stu-id="45e19-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="45e19-213">Essayez de transmettre par push le fichier MOF signé.</span><span class="sxs-lookup"><span data-stu-id="45e19-213">Try pushing the signed MOF file.</span></span>

  ![PushSignedMofFile](../images/DSC-improvements/PushSignedMof.png)
