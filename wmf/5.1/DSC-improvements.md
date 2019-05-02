---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Améliorations de DSC dans WMF 5.1
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085526"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="ef8f4-103">Améliorations de la configuration de l’état souhaité (DSC) dans WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ef8f4-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="ef8f4-104">Améliorations des ressources de classe DSC</span><span class="sxs-lookup"><span data-stu-id="ef8f4-104">DSC class resource improvements</span></span>

<span data-ttu-id="ef8f4-105">Dans WMF 5.1, nous avons résolu les problèmes connus suivants :</span><span class="sxs-lookup"><span data-stu-id="ef8f4-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="ef8f4-106">Get-DscConfiguration peut retourner des valeurs vides (Null) ou des erreurs si un type complexe/de table de hachage est retourné par la fonction Get() d’une ressource DSC basée sur une classe.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="ef8f4-107">Get-DscConfiguration retourne une erreur si des informations d’identification RunAs sont utilisées dans une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="ef8f4-108">Une ressource basée sur une classe ne peut pas être utilisée dans une configuration composite.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="ef8f4-109">Start-DscConfiguration se bloque si une ressource basée sur une classe a une propriété de son propre type.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="ef8f4-110">Une ressource basée sur une classe ne peut pas être utilisée comme ressource exclusive.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="ef8f4-111">Améliorations du débogage des ressources DSC</span><span class="sxs-lookup"><span data-stu-id="ef8f4-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="ef8f4-112">Dans WMF 5.0, le débogueur PowerShell ne s’arrêtait pas directement sur la méthode de ressource basée sur une classe (Get/Set/Test).</span><span class="sxs-lookup"><span data-stu-id="ef8f4-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="ef8f4-113">Dans WMF 5.1, le débogueur s’arrête sur la méthode de ressource basée sur une classe de la même façon que sur des méthodes de ressources basées sur un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="ef8f4-114">Le client collecteur DSC prend en charge TLS 1.1 et TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="ef8f4-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="ef8f4-115">Avant, le client collecteur DSC ne prenait en charge que SSL 3.0 et TLS 1.0 sur des connexions HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="ef8f4-116">Quand il est contraint d’utiliser des protocoles plus sécurisés, le client collecteur cesse de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="ef8f4-117">Dans WMF 5.1, le client collecteur DSC ne prend plus en charge SSL 3.0, mais prend en charge les protocoles plus sécurisés TLS 1.1 et TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="ef8f4-118">Inscription du serveur collecteur améliorée</span><span class="sxs-lookup"><span data-stu-id="ef8f4-118">Improved pull server registration</span></span>

<span data-ttu-id="ef8f4-119">Dans les versions antérieures de WMF, les inscriptions/demandes de création de rapports simultanées auprès d’un serveur collecteur DSC lors de l’utilisation de la base de données ESENT aboutissaient à un échec de l’inscription/de la création de rapport par le Gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="ef8f4-120">Dans ce cas, les journaux des événements sur le serveur collecteur affichent l’erreur « Le nom d’instance est déjà utilisé ».</span><span class="sxs-lookup"><span data-stu-id="ef8f4-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="ef8f4-121">Cela est dû à l’utilisation d’un modèle incorrect pour accéder à la base de données ESENT dans un scénario multithread.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="ef8f4-122">Dans WMF 5.1, ce problème a été résolu.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="ef8f4-123">Les inscriptions ou demandes de création de rapports simultanées (impliquant la base de données ESENT) fonctionnent correctement dans WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="ef8f4-124">Ce problème s’applique uniquement à la base de données ESENT et ne s’applique pas à la base de données OLE DB.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="ef8f4-125">Activer le journal circulaire sur l’instance de la base de données ESENT</span><span class="sxs-lookup"><span data-stu-id="ef8f4-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="ef8f4-126">Dans la version antérieure de DSC-PullServer, les fichiers journaux de la base de données ESENT saturaient l’espace disque du serveur collecteur, car l’instance de la base de données était créée sans journalisation circulaire.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="ef8f4-127">Dans cette version, vous pouvez utiliser le fichier web.config du serveur collecteur pour contrôler le comportement de la journalisation circulaire.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="ef8f4-128">Par défaut, CircularLogging a la valeur TRUE.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="ef8f4-129">Convention de nommage pour une configuration partielle de collecte</span><span class="sxs-lookup"><span data-stu-id="ef8f4-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="ef8f4-130">Dans la version précédente, la convention de nommage pour une configuration partielle précisait que le nom du fichier MOF dans le service/serveur collecteur devait correspondre au nom de configuration partielle spécifié dans les paramètres du gestionnaire de configuration local qui, à son tour, devait correspondre au nom de configuration incorporé dans le fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="ef8f4-131">Consultez les captures instantanées ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ef8f4-131">See the snapshots below:</span></span>

- <span data-ttu-id="ef8f4-132">Paramètres de configuration locale qui définissent une configuration partielle qu’un nœud est autorisé à recevoir.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Exemple de métaconfiguration](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="ef8f4-134">Exemple de définition d’une configuration partielle</span><span class="sxs-lookup"><span data-stu-id="ef8f4-134">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="ef8f4-135">« ConfigurationName » incorporé dans le fichier MOF généré</span><span class="sxs-lookup"><span data-stu-id="ef8f4-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Exemple de fichier mof généré](../images/PartialGeneratedMof.png)

- <span data-ttu-id="ef8f4-137">FileName dans le référentiel de configuration de tirage (pull)</span><span class="sxs-lookup"><span data-stu-id="ef8f4-137">FileName in the pull configuration repository</span></span>

![FileName dans le dépôt de configuration](../images/PartialInConfigRepository.png)

<span data-ttu-id="ef8f4-139">Le nom de service Azure Automation a généré des fichiers MOF sous la forme `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="ef8f4-140">Par conséquent, la configuration ci-dessous est compilée dans PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="ef8f4-141">Il est ainsi impossible de collecter l’une de vos configurations partielles à partir du service Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

<span data-ttu-id="ef8f4-142">Dans WMF 5.1, une configuration partielle dans le service/serveur collecteur peut être nommée `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="ef8f4-143">En outre, si un ordinateur collecte une seule configuration d’un service/serveur collecteur, le fichier de configuration dans le dépôt de configuration du serveur collecteur peut avoir n’importe quel nom.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="ef8f4-144">Cette souplesse d’attribution des noms vous permet de gérer vos nœuds en partie à l’aide du service Azure Automation, où certains éléments de la configuration de votre nœud proviennent d’Azure Automation DSC tandis que d’autres sont gérés par vous en local.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="ef8f4-145">La métaconfiguration ci-dessous définit un nœud à gérer à la fois localement et par le service Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="ef8f4-146">Utilisation de PsDscRunAsCredential avec des ressources composites DSC</span><span class="sxs-lookup"><span data-stu-id="ef8f4-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="ef8f4-147">Nous avons ajouté la prise en charge de l’utilisation de [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) avec des ressources [composites](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) DSC.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="ef8f4-148">Vous pouvez maintenant spécifier une valeur pour PsDscRunAsCredential lors de l’utilisation des ressources composites dans des configurations.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="ef8f4-149">Le cas échéant, toutes les ressources sont exécutées dans une ressource composite en tant qu’utilisateur RunAs.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="ef8f4-150">Si une ressource composite appelle une autre ressource composite, toutes ses ressources sont également exécutées en tant qu’utilisateur RunAs.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="ef8f4-151">Les informations d’identification RunAs sont propagées à tout niveau de la hiérarchie des ressources composites.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="ef8f4-152">Si une ressource à l’intérieur d’une ressource composite spécifie sa propre valeur pour PsDscRunAsCredential, une erreur de fusion se produit pendant la compilation de la configuration.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="ef8f4-153">Cet exemple illustre son utilisation avec la ressource composite [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) incluse dans le module PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="ef8f4-154">Validations des signatures de configurations et de modules DSC</span><span class="sxs-lookup"><span data-stu-id="ef8f4-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="ef8f4-155">Dans DSC, les configurations et les modules sont distribués à des ordinateurs gérés à partir du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="ef8f4-156">Si le serveur collecteur est compromis, un attaquant peut potentiellement modifier les configurations et les modules sur le serveur collecteur pour les distribuer à tous les nœuds gérés, en les compromettant tous.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="ef8f4-157">Dans WMF 5.1, DSC prend en charge la validation des signatures numériques sur les fichiers catalogue et de configuration (.MOF).</span><span class="sxs-lookup"><span data-stu-id="ef8f4-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="ef8f4-158">Cette fonctionnalité empêche les nœuds d’exécuter des configurations ou des fichiers de modules qui ne sont pas signés par un signataire approuvé ou qui ont été falsifiés après avoir été signés par le signataire approuvé.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="ef8f4-159">Comment signer des configurations et modules</span><span class="sxs-lookup"><span data-stu-id="ef8f4-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="ef8f4-160">Fichiers de configuration (.mof) : la cmdlet PowerShell existante [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) est étendue de façon à prendre en charge la signature des fichiers MOF.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="ef8f4-161">Modules : la signature de modules s’effectue en signant le catalogue de module correspondant :</span><span class="sxs-lookup"><span data-stu-id="ef8f4-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="ef8f4-162">Créer un fichier catalogue : un fichier catalogue contient une collection de hachages de chiffrement ou d’empreintes.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="ef8f4-163">Chaque empreinte correspond à un fichier qui est inclus dans le module.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="ef8f4-164">La nouvelle applet de commande [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) a été ajoutée pour permettre aux utilisateurs de créer un fichier catalogue pour leur module.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="ef8f4-165">Signer le fichier catalogue : utilisez [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) pour signer le fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="ef8f4-166">Placer le fichier catalogue dans le dossier de module.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="ef8f4-167">Par convention, le fichier catalogue de module doit être placé sous le dossier de module portant le même nom que le module.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="ef8f4-168">Paramètres du gestionnaire de configuration local pour activer les validations des signatures</span><span class="sxs-lookup"><span data-stu-id="ef8f4-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="ef8f4-169">Extraction</span><span class="sxs-lookup"><span data-stu-id="ef8f4-169">Pull</span></span>

<span data-ttu-id="ef8f4-170">Le gestionnaire de configuration local d’un nœud effectue une validation des signatures des modules et des configurations en fonction de ses paramètres actifs.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="ef8f4-171">Par défaut, la validation des signatures est désactivée.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="ef8f4-172">La validation des signatures peut être activée en ajoutant le bloc « SignatureValidation » à la définition de métaconfiguration du nœud, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ef8f4-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="ef8f4-173">La définition de la métaconfiguration ci-dessus sur un nœud active la validation des signatures sur les configurations et modules téléchargés.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="ef8f4-174">Le gestionnaire de configuration local effectue les étapes suivantes pour vérifier les signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="ef8f4-175">Il vérifie que la signature d’un fichier de configuration (.MOF) est valide.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="ef8f4-176">Il utilise l’applet de commande PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) qui est étendue dans 5.1 pour prendre en charge la validation des signatures MOF.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="ef8f4-177">Il vérifie que l’autorité de certification qui a autorisé le signataire est approuvée.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="ef8f4-178">Il télécharge les dépendances de ressources/modules de la configuration à un emplacement temporaire.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="ef8f4-179">Il vérifie la signature du catalogue qui figure dans le module.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="ef8f4-180">Il recherche un fichier `<moduleName>.cat` et vérifie sa signature à l’aide de l’applet de commande [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="ef8f4-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="ef8f4-181">Il vérifie que l’autorité de certification qui a authentifié le signataire est approuvée.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="ef8f4-182">Il vérifie que le contenu des modules n’a pas été falsifié à l’aide de la nouvelle applet de commande [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="ef8f4-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="ef8f4-183">Il installe le module dans $env:ProgramFiles\WindowsPowerShell\Modules\.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="ef8f4-184">Il traite la configuration</span><span class="sxs-lookup"><span data-stu-id="ef8f4-184">Process configuration</span></span>

> <span data-ttu-id="ef8f4-185">Remarque : la validation des signatures sur le catalogue de module et la configuration n’est effectuée que la première fois où la configuration est appliquée au système et lors du téléchargement et de l’installation du module.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="ef8f4-186">Les séries de tests de cohérence ne valident pas la signature de Current.mof ni ses dépendances de modules.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="ef8f4-187">Si la vérification a échoué à un stade, par exemple si la configuration extraite à partir du serveur collecteur n’est pas signée, le traitement de la configuration s’arrête avec l’erreur affichée ci-dessous et tous les fichiers temporaires sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Exemple de configuration de sortie d’erreur](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="ef8f4-189">De la même manière, l’extraction d’un module dont le catalogue n’est pas signé entraîne l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="ef8f4-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Exemple de module de sortie d’erreur](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="ef8f4-191">Envoi</span><span class="sxs-lookup"><span data-stu-id="ef8f4-191">Push</span></span>

<span data-ttu-id="ef8f4-192">Une configuration fournie à l’aide d’une transmission de type push peut être falsifiée à sa source avant d’être remise au nœud.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="ef8f4-193">Le gestionnaire de configuration local effectue des étapes de validation des signatures similaires pour les configurations envoyées ou publiées.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="ef8f4-194">Voici un exemple complet de validation des signatures pour l’envoi.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="ef8f4-195">Activez la validation des signatures sur le nœud.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-195">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="ef8f4-196">Créez un exemple de fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-196">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="ef8f4-197">Essayez d’envoyer le fichier de configuration non signé au nœud.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="ef8f4-199">Signez le fichier de configuration avec un certificat de signature de code.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="ef8f4-201">Essayez de transmettre par push le fichier MOF signé.</span><span class="sxs-lookup"><span data-stu-id="ef8f4-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
