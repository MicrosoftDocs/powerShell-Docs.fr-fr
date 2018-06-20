---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Création d’un pipeline d’intégration continue et de déploiement continu avec DSC
ms.openlocfilehash: ce0f2ed79f5f96a1c38e0beaf32529aba7538963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190551"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="90336-103">Création d’un pipeline d’intégration continue et de déploiement continu avec DSC</span><span class="sxs-lookup"><span data-stu-id="90336-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="90336-104">Cet exemple montre comment créer un pipeline d’intégration continue/déploiement continu (CI/CD) à l’aide de PowerShell, DSC, Pester et Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="90336-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="90336-105">Une fois le pipeline est créé et configuré, vous pouvez l’utiliser pour totalement déployer, configurer et tester un serveur DNS et ses enregistrements d’hôte associés.</span><span class="sxs-lookup"><span data-stu-id="90336-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="90336-106">Ce processus simule la première partie d’un pipeline qui sera utilisée dans un environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="90336-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="90336-107">Un pipeline CI/CD automatisé vous permet de mettre à jour les logiciels avec plus de rapidité et de fiabilité, garantissant que tout le code est testé et qu’une version actuelle de votre code est disponible à tout moment.</span><span class="sxs-lookup"><span data-stu-id="90336-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="90336-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="90336-108">Prerequisites</span></span>

<span data-ttu-id="90336-109">Pour utiliser cet exemple, vous devez maîtriser les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="90336-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="90336-110">Les concepts CI-CD.</span><span class="sxs-lookup"><span data-stu-id="90336-110">CI-CD concepts.</span></span> <span data-ttu-id="90336-111">Le [modèle de pipeline de mise en production](http://aka.ms/thereleasepipelinemodelpdf) constitue une bonne référence.</span><span class="sxs-lookup"><span data-stu-id="90336-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="90336-112">Contrôle de source [Git](https://git-scm.com/)</span><span class="sxs-lookup"><span data-stu-id="90336-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="90336-113">L’infrastructure de test [Pester](https://github.com/pester/Pester)</span><span class="sxs-lookup"><span data-stu-id="90336-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="90336-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="90336-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="90336-115">Ce dont vous aurez besoin</span><span class="sxs-lookup"><span data-stu-id="90336-115">What you will need</span></span>

<span data-ttu-id="90336-116">Pour générer et exécuter cet exemple, vous aurez besoin d’un environnement comportant plusieurs ordinateurs et/ou machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="90336-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="90336-117">Client</span><span class="sxs-lookup"><span data-stu-id="90336-117">Client</span></span>

<span data-ttu-id="90336-118">Il s’agit de l’ordinateur sur lequel vous allez effectuer toutes les tâches pour configurer et exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="90336-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="90336-119">L’ordinateur client doit être un ordinateur Windows avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="90336-119">The client computer must be a Windows computer with the following installed:</span></span>
- [<span data-ttu-id="90336-120">Git</span><span class="sxs-lookup"><span data-stu-id="90336-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="90336-121">référentiel git local cloné à partir de https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="90336-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="90336-122">un éditeur de texte, par exemple [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="90336-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="90336-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="90336-123">TFSSrv1</span></span>

<span data-ttu-id="90336-124">L’ordinateur qui héberge le serveur TFS sur lequel vous allez définir votre build et votre version.</span><span class="sxs-lookup"><span data-stu-id="90336-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="90336-125">[Team Foundation Server 2017](https://www.visualstudio.com/tfs/) doit être installé sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="90336-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="90336-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="90336-126">BuildAgent</span></span>

<span data-ttu-id="90336-127">L’ordinateur qui exécute l’agent de build Windows qui crée le projet.</span><span class="sxs-lookup"><span data-stu-id="90336-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="90336-128">Un agent de build doit être installé et en cours d’exécution sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="90336-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="90336-129">Consultez [Déployer un agent sur Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) pour savoir comment installer et exécuter un agent de build Windows.</span><span class="sxs-lookup"><span data-stu-id="90336-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="90336-130">Vous devez également installer les modules DSC `xDnsServer` et `xNetworking` sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="90336-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="90336-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="90336-131">TestAgent1</span></span>

<span data-ttu-id="90336-132">Il s’agit de l’ordinateur configuré comme serveur DNS par la configuration DSC dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="90336-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="90336-133">L’ordinateur doit exécuter [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="90336-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="90336-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="90336-134">TestAgent2</span></span>

<span data-ttu-id="90336-135">Il s’agit de l’ordinateur qui héberge le site Web que cet exemple configure.</span><span class="sxs-lookup"><span data-stu-id="90336-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="90336-136">L’ordinateur doit exécuter [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="90336-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="90336-137">Ajouter le code à TFS</span><span class="sxs-lookup"><span data-stu-id="90336-137">Add the code to TFS</span></span>

<span data-ttu-id="90336-138">Nous commencerons par créer un référentiel Git dans TFS, puis nous importerons le code de votre référentiel local vers l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="90336-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="90336-139">Si vous n’avez pas déjà cloné le référentiel Demo_CI sur votre ordinateur client, faites-le maintenant en exécutant la commande git suivante :</span><span class="sxs-lookup"><span data-stu-id="90336-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="90336-140">Sur votre ordinateur client, accédez à votre serveur TFS dans un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="90336-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="90336-141">Dans TFS, [créez un nouveau projet d’équipe](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) intitulé Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="90336-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

    <span data-ttu-id="90336-142">Assurez-vous que l’option **Contrôle de version** est définie sur **Git**.</span><span class="sxs-lookup"><span data-stu-id="90336-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="90336-143">Sur votre ordinateur client, ajoutez un accès à distance au référentiel que vous venez de créer dans TFS avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="90336-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

    `git remote add tfs <YourTFSRepoURL>`

    <span data-ttu-id="90336-144">Où `<YourTFSRepoURL>` est le clone de l’URL dans le référentiel TFS que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="90336-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

    <span data-ttu-id="90336-145">Si vous ne savez pas où trouver cette URL, consultez [Cloner un référentiel Git existant](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span><span class="sxs-lookup"><span data-stu-id="90336-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="90336-146">Transmettez le code de votre référentiel local à votre référentiel TFS avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="90336-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

    `git push tfs --all`
1. <span data-ttu-id="90336-147">Le référentiel TFS contiendra le code Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="90336-147">The TFS repository will be populated with the Demo_CI code.</span></span>

><span data-ttu-id="90336-148">**Remarque :** cet exemple utilise le code dans la branche `ci-cd-example` du référentiel Git.</span><span class="sxs-lookup"><span data-stu-id="90336-148">**Note:** This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
><span data-ttu-id="90336-149">Veillez à spécifier cette branche en tant que branche par défaut dans votre projet TFS, et pour les déclencheurs CI/CD que vous créez.</span><span class="sxs-lookup"><span data-stu-id="90336-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="90336-150">Présentation du code</span><span class="sxs-lookup"><span data-stu-id="90336-150">Understanding the code</span></span>

<span data-ttu-id="90336-151">Avant de créer les pipelines de build et de déploiement, examinons le code pour comprendre ce qui se passe.</span><span class="sxs-lookup"><span data-stu-id="90336-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="90336-152">Sur votre ordinateur client, ouvrez votre éditeur de texte favori et accédez à la racine de votre référentiel Git Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="90336-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="90336-153">La configuration DSC</span><span class="sxs-lookup"><span data-stu-id="90336-153">The DSC configuration</span></span>

<span data-ttu-id="90336-154">Ouvrez le fichier `DNSServer.ps1` (depuis la racine du référentiel local Demo_CI, `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="90336-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="90336-155">Ce fichier contient la configuration DSC qui configure le serveur DNS.</span><span class="sxs-lookup"><span data-stu-id="90336-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="90336-156">Le voici dans son intégralité :</span><span class="sxs-lookup"><span data-stu-id="90336-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="90336-157">Notez l’instruction `Node` :</span><span class="sxs-lookup"><span data-stu-id="90336-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="90336-158">Elle recherche tous les nœuds qui ont été définis comme ayant un rôle de `DNSServer` dans les [données de configuration](configData.md), créées par le script `DevEnv.ps1`.</span><span class="sxs-lookup"><span data-stu-id="90336-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="90336-159">Il est important d’utiliser les données de configuration pour définir des nœuds lors de l’opération CI car les informations sur les nœuds sont susceptibles de changer entre les environnements, et ces données de configuration vous permet de modifier facilement les informations des nœuds sans modifier le code de la configuration.</span><span class="sxs-lookup"><span data-stu-id="90336-159">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="90336-160">Dans le premier bloc de ressources, la configuration appelle [WindowsFeature](windowsFeatureResource.md) pour s’assurer que la fonctionnalité DNS est activée.</span><span class="sxs-lookup"><span data-stu-id="90336-160">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="90336-161">Les blocs de ressources qui suivent appellent des ressources à partir du module [xDnsServer](https://github.com/PowerShell/xDnsServer) pour configurer la zone principale et les enregistrements DNS.</span><span class="sxs-lookup"><span data-stu-id="90336-161">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="90336-162">Notez que les deux blocs `xDnsRecord` sont encapsulés dans des boucles `foreach` qui forment une itération via des tableaux dans les données de configuration.</span><span class="sxs-lookup"><span data-stu-id="90336-162">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="90336-163">Là encore, les données de configuration sont créées par le script `DevEnv.ps1`, ce que allons examiner maintenant.</span><span class="sxs-lookup"><span data-stu-id="90336-163">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="90336-164">Données de configuration</span><span class="sxs-lookup"><span data-stu-id="90336-164">Configuration data</span></span>

<span data-ttu-id="90336-165">Le fichier `DevEnv.ps1` (depuis la racine du référentiel local Demo_CI, `./InfraDNS/DevEnv.ps1`) spécifie les données de configuration spécifiques à l’environnement dans une table de hachage, puis passe cette table de hachage à un appel à la fonction `New-DscConfigurationDataDocument`, définie dans `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="90336-165">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="90336-166">Le fichier `DevEnv.ps1` :</span><span class="sxs-lookup"><span data-stu-id="90336-166">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="90336-167">La fonction `New-DscConfigurationDataDocument` (définie dans `\Assets\DscPipelineTools\DscPipelineTools.psm1`) crée par programmation un document de données de configuration à partir de la table de hachage (données du nœud) et un tableau (données non-nœud), qui sont transmis comme les paramètres `RawEnvData` et `OtherEnvData`.</span><span class="sxs-lookup"><span data-stu-id="90336-167">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="90336-168">Dans notre cas, seul le paramètre `RawEnvData` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="90336-168">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="90336-169">Le script de build psake</span><span class="sxs-lookup"><span data-stu-id="90336-169">The psake build script</span></span>

<span data-ttu-id="90336-170">Le script de build [psake](https://github.com/psake/psake) défini dans `Build.ps1` (depuis la racine du référentiel Demo_CI, `./InfraDNS/Build.ps1`) définit les tâches qui font partie de la build.</span><span class="sxs-lookup"><span data-stu-id="90336-170">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="90336-171">Il définit également les autres tâches dont dépend chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="90336-171">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="90336-172">Lorsqu’il est appelé, le script psake garantit que la tâche spécifiée (ou la tâche nommée `Default` si aucune tâche n’est spécifiée) s’exécute et que toutes les dépendances s’exécutent également (cette opération est récursive afin que les dépendances de dépendances s’exécutent, et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="90336-172">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="90336-173">Dans cet exemple, la tâche `Default` est définie ainsi :</span><span class="sxs-lookup"><span data-stu-id="90336-173">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="90336-174">La tâche `Default` n’a aucune implémentation elle-même, mais a une dépendance sur la tâche `CompileConfigs`.</span><span class="sxs-lookup"><span data-stu-id="90336-174">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="90336-175">La chaîne de dépendances de tâches qui en résulte garantit l’exécution de toutes les tâches figurant dans le script de build.</span><span class="sxs-lookup"><span data-stu-id="90336-175">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="90336-176">Dans cet exemple, le script psake est appelé par un appel à `Invoke-PSake` dans le fichier `Initiate.ps1` (situé à la racine du référentiel Demo_CI) :</span><span class="sxs-lookup"><span data-stu-id="90336-176">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="90336-177">Lorsque nous créons la définition de build pour notre exemple dans TFS, nous fournissons notre fichier de script psake comme paramètre `fileName` pour ce script.</span><span class="sxs-lookup"><span data-stu-id="90336-177">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="90336-178">Le script de build définit les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="90336-178">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="90336-179">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="90336-179">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="90336-180">Exécute `DevEnv.ps1`, qui génère le fichier de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="90336-180">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="90336-181">InstallModules</span><span class="sxs-lookup"><span data-stu-id="90336-181">InstallModules</span></span>

<span data-ttu-id="90336-182">Installe les modules requis par la configuration `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="90336-182">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="90336-183">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="90336-183">ScriptAnalysis</span></span>

<span data-ttu-id="90336-184">Appelle [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="90336-184">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="90336-185">UnitTests</span><span class="sxs-lookup"><span data-stu-id="90336-185">UnitTests</span></span>

<span data-ttu-id="90336-186">Exécute les tests unitaires [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="90336-186">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="90336-187">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="90336-187">CompileConfigs</span></span>

<span data-ttu-id="90336-188">Compile la configuration (`DNSServer.ps1`) dans un fichier MOF, en utilisant les données de configuration générées par la tâche `GenerateEnvironmentFiles`.</span><span class="sxs-lookup"><span data-stu-id="90336-188">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="90336-189">Clean</span><span class="sxs-lookup"><span data-stu-id="90336-189">Clean</span></span>

<span data-ttu-id="90336-190">Crée les dossiers utilisés pour l’exemple, puis supprime les résultats des tests, les fichiers de données de configuration et les modules des exécutions précédentes.</span><span class="sxs-lookup"><span data-stu-id="90336-190">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="90336-191">Le script de déploiement psake</span><span class="sxs-lookup"><span data-stu-id="90336-191">The psake deploy script</span></span>

<span data-ttu-id="90336-192">Le script de déploiement [psake](https://github.com/psake/psake) défini dans `Deploy.ps1` (depuis la racine du référentiel Demo_CI, `./InfraDNS/Deploy.ps1`) définit les tâches qui déploient et exécutent la configuration.</span><span class="sxs-lookup"><span data-stu-id="90336-192">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="90336-193">`Deploy.ps1` définit les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="90336-193">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="90336-194">DeployModules</span><span class="sxs-lookup"><span data-stu-id="90336-194">DeployModules</span></span>

<span data-ttu-id="90336-195">Démarre une session PowerShell sur `TestAgent1` et installe les modules contenant les ressources DSC requises pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="90336-195">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="90336-196">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="90336-196">DeployConfigs</span></span>

<span data-ttu-id="90336-197">Appelle l’applet de commande [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) pour exécuter la configuration sur `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="90336-197">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="90336-198">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="90336-198">IntegrationTests</span></span>

<span data-ttu-id="90336-199">Exécute les tests d’intégration [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="90336-199">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="90336-200">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="90336-200">AcceptanceTests</span></span>

<span data-ttu-id="90336-201">Exécute les tests d’acceptation [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="90336-201">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="90336-202">Clean</span><span class="sxs-lookup"><span data-stu-id="90336-202">Clean</span></span>

<span data-ttu-id="90336-203">Supprime tous les modules installés lors des exécutions précédentes et garantit l’existence du dossier de résultats de test.</span><span class="sxs-lookup"><span data-stu-id="90336-203">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="90336-204">Scripts de tests</span><span class="sxs-lookup"><span data-stu-id="90336-204">Test scripts</span></span>

<span data-ttu-id="90336-205">Les tests d’acceptation, d’intégration et unitaires sont définis dans les scripts du dossier `Tests` (depuis la racine du référentiel Demo_CI, `./InfraDNS/Tests`), puis placés dans des fichiers nommés `DNSServer.tests.ps1` dans leurs dossiers respectifs.</span><span class="sxs-lookup"><span data-stu-id="90336-205">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="90336-206">Les scripts de test utilisent la syntaxe [Pester](https://github.com/pester/Pester/wiki) et [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="90336-206">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="90336-207">Tests unitaires</span><span class="sxs-lookup"><span data-stu-id="90336-207">Unit tests</span></span>

<span data-ttu-id="90336-208">Les tests unitaires testent les configurations DSC elles-mêmes pour s’assurer que les configurations exécuteront les tâches prévues.</span><span class="sxs-lookup"><span data-stu-id="90336-208">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="90336-209">Le script de test unitaire utilise la syntaxe [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="90336-209">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="90336-210">Tests d’intégration</span><span class="sxs-lookup"><span data-stu-id="90336-210">Integration tests</span></span>

<span data-ttu-id="90336-211">Les tests d’intégration testent la configuration du système pour s’assurer, le système est configuré comme prévu lors de son intégration avec d’autres composants.</span><span class="sxs-lookup"><span data-stu-id="90336-211">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="90336-212">Ces tests sont exécutés sur le nœud cible après que ce dernier a été configuré avec DSC.</span><span class="sxs-lookup"><span data-stu-id="90336-212">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="90336-213">Le script de test d’intégration utilise une combinaison des syntaxes [Pester](https://github.com/pester/Pester/wiki) et [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="90336-213">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="90336-214">Tests d’acceptation</span><span class="sxs-lookup"><span data-stu-id="90336-214">Acceptance tests</span></span>

<span data-ttu-id="90336-215">Les tests d’acceptation testent le système pour s’assurer qu’il se comporte comme prévu.</span><span class="sxs-lookup"><span data-stu-id="90336-215">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="90336-216">Par exemple, ils vérifient qu'une page web renvoie les informations appropriées lorsqu’elle est interrogée.</span><span class="sxs-lookup"><span data-stu-id="90336-216">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="90336-217">Ces tests sont exécutés à distance à partir du nœud cible afin de tester des scénarios en conditions réelles.</span><span class="sxs-lookup"><span data-stu-id="90336-217">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="90336-218">Le script de test d’intégration utilise une combinaison des syntaxes [Pester](https://github.com/pester/Pester/wiki) et [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="90336-218">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="90336-219">Définir la build</span><span class="sxs-lookup"><span data-stu-id="90336-219">Define the build</span></span>

<span data-ttu-id="90336-220">Maintenant que nous avons chargé notre code sur TFS et examiné son comportement, nous allons définir notre build.</span><span class="sxs-lookup"><span data-stu-id="90336-220">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="90336-221">Ici, nous aborderons uniquement les étapes de build que vous ajouterez à la build.</span><span class="sxs-lookup"><span data-stu-id="90336-221">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="90336-222">Pour obtenir des instructions sur la création d’une définition de build dans TFS, consultez [Créer et mettre en file d’attente une définition de build](https://www.visualstudio.com/en-us/docs/build/define/create).</span><span class="sxs-lookup"><span data-stu-id="90336-222">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="90336-223">Créez une définition de build (sélectionnez le modèle **vide**) nommée « InfraDNS ».</span><span class="sxs-lookup"><span data-stu-id="90336-223">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="90336-224">Ajoutez les étapes suivantes à votre définition de build :</span><span class="sxs-lookup"><span data-stu-id="90336-224">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="90336-225">Script PowerShell</span><span class="sxs-lookup"><span data-stu-id="90336-225">PowerShell Script</span></span>
- <span data-ttu-id="90336-226">Publier les résultats des tests</span><span class="sxs-lookup"><span data-stu-id="90336-226">Publish Test Results</span></span>
- <span data-ttu-id="90336-227">Copier les fichiers</span><span class="sxs-lookup"><span data-stu-id="90336-227">Copy Files</span></span>
- <span data-ttu-id="90336-228">Publier l’artefact</span><span class="sxs-lookup"><span data-stu-id="90336-228">Publish Artifact</span></span>

<span data-ttu-id="90336-229">Après avoir ajouté ces étapes de build, modifiez les propriétés de chaque étape comme suit :</span><span class="sxs-lookup"><span data-stu-id="90336-229">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="90336-230">Script PowerShell</span><span class="sxs-lookup"><span data-stu-id="90336-230">PowerShell Script</span></span>

1. <span data-ttu-id="90336-231">Définissez la propriété **Type** sur `File Path`.</span><span class="sxs-lookup"><span data-stu-id="90336-231">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="90336-232">Définissez la propriété **Chemin d'accès du script** sur `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="90336-232">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="90336-233">Ajoutez la valeur `-fileName build` à la propriété **Arguments**.</span><span class="sxs-lookup"><span data-stu-id="90336-233">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="90336-234">Cette étape de la build exécute le fichier `initiate.ps1`, qui appelle le script de build psake.</span><span class="sxs-lookup"><span data-stu-id="90336-234">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="90336-235">Publier les résultats des tests</span><span class="sxs-lookup"><span data-stu-id="90336-235">Publish Test Results</span></span>

1. <span data-ttu-id="90336-236">Définissez **Format des résultats des tests** sur `NUnit`</span><span class="sxs-lookup"><span data-stu-id="90336-236">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="90336-237">Définissez **Fichiers des résultats des tests** sur `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="90336-237">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="90336-238">Définissez **Titre de la série de tests** sur `Unit`.</span><span class="sxs-lookup"><span data-stu-id="90336-238">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="90336-239">Vérifiez que les cases **Options de contrôle** **Activé** et **Toujours exécuter** sont cochées.</span><span class="sxs-lookup"><span data-stu-id="90336-239">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="90336-240">Cette étape de build exécute des tests unitaires dans le script Pester que nous avons examiné précédemment, puis stocke les résultats dans le dossier `InfraDNS/Tests/Results/*.xml`.</span><span class="sxs-lookup"><span data-stu-id="90336-240">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="90336-241">Copier les fichiers</span><span class="sxs-lookup"><span data-stu-id="90336-241">Copy Files</span></span>

1. <span data-ttu-id="90336-242">Ajoutez chacune des lignes suivantes à **Contents** :</span><span class="sxs-lookup"><span data-stu-id="90336-242">Add each of the following lines to **Contents**:</span></span>

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. <span data-ttu-id="90336-243">Définissez **TargetFolder** sur `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="90336-243">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="90336-244">Cette étape copie la build et les scripts de test dans le répertoire intermédiaire afin de pouvoir publier ces éléments comme des artefacts de build à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="90336-244">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="90336-245">Publier l’artefact</span><span class="sxs-lookup"><span data-stu-id="90336-245">Publish Artifact</span></span>

1. <span data-ttu-id="90336-246">Définissez **Chemin d'accès à publier** sur `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="90336-246">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="90336-247">Définissez **Nom de l'artefact** sur `Deploy`</span><span class="sxs-lookup"><span data-stu-id="90336-247">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="90336-248">Définissez **Type d'artefact** sur `Server`</span><span class="sxs-lookup"><span data-stu-id="90336-248">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="90336-249">Sélectionnez `Enabled` dans **Options de contrôle**</span><span class="sxs-lookup"><span data-stu-id="90336-249">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="90336-250">Activer l’intégration continue</span><span class="sxs-lookup"><span data-stu-id="90336-250">Enable continuous integration</span></span>

<span data-ttu-id="90336-251">Nous allons maintenant configurer un déclencheur qui génère le projet chaque fois qu’une modification est apportée à la branche `ci-cd-example` du référentiel git.</span><span class="sxs-lookup"><span data-stu-id="90336-251">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="90336-252">Dans TFS, cliquez sur l’onglet **Build et version** </span><span class="sxs-lookup"><span data-stu-id="90336-252">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="90336-253">Sélectionnez la définition de build `DNS Infra`, puis cliquez sur **Modifier**</span><span class="sxs-lookup"><span data-stu-id="90336-253">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="90336-254">Cliquez sur l’onglet **Déclencheurs** </span><span class="sxs-lookup"><span data-stu-id="90336-254">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="90336-255">Sélectionnez **Continuous integration (CI)**, puis `refs/heads/ci-cd-example` dans la liste déroulante de la branche</span><span class="sxs-lookup"><span data-stu-id="90336-255">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="90336-256">Cliquez sur **Enregistrer**, puis sur **OK**</span><span class="sxs-lookup"><span data-stu-id="90336-256">Click **Save** and then **OK**</span></span>

<span data-ttu-id="90336-257">Désormais, chaque modification apportée au référentiel git TFS génère une build automatisée.</span><span class="sxs-lookup"><span data-stu-id="90336-257">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="90336-258">Créer la définition de version</span><span class="sxs-lookup"><span data-stu-id="90336-258">Create the release definition</span></span>

<span data-ttu-id="90336-259">Nous allons créer une définition de version afin de déployer le projet dans l’environnement de développement à chaque ajout de code.</span><span class="sxs-lookup"><span data-stu-id="90336-259">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="90336-260">Pour ce faire, ajoutez une nouvelle définition de version associée à la définition de build `InfraDNS` que vous avez créée précédemment.</span><span class="sxs-lookup"><span data-stu-id="90336-260">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="90336-261">Veillez à sélectionner **Continuous deployment** afin de déclencher une nouvelle version chaque fois qu’une nouvelle build est terminée.</span><span class="sxs-lookup"><span data-stu-id="90336-261">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="90336-262">Consultez l’article ([Guide pratique pour utiliser des définitions de version](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) et configurez la comme suit :</span><span class="sxs-lookup"><span data-stu-id="90336-262">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="90336-263">Ajoutez les étapes suivantes à la définition de version :</span><span class="sxs-lookup"><span data-stu-id="90336-263">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="90336-264">Script PowerShell</span><span class="sxs-lookup"><span data-stu-id="90336-264">PowerShell Script</span></span>
- <span data-ttu-id="90336-265">Publier les résultats des tests</span><span class="sxs-lookup"><span data-stu-id="90336-265">Publish Test Results</span></span>
- <span data-ttu-id="90336-266">Publier les résultats des tests</span><span class="sxs-lookup"><span data-stu-id="90336-266">Publish Test Results</span></span>

<span data-ttu-id="90336-267">Modifiez les étapes comme suit :</span><span class="sxs-lookup"><span data-stu-id="90336-267">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="90336-268">Script PowerShell</span><span class="sxs-lookup"><span data-stu-id="90336-268">PowerShell Script</span></span>

1. <span data-ttu-id="90336-269">Définissez le champ **Chemin d'accès du script** sur `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="90336-269">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="90336-270">Définissez le champ **Arguments** sur `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="90336-270">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="90336-271">Première publication des résultats des tests</span><span class="sxs-lookup"><span data-stu-id="90336-271">First Publish Test Results</span></span>

1. <span data-ttu-id="90336-272">Sélectionnez `NUnit` pour le champ **Format des résultats des tests** </span><span class="sxs-lookup"><span data-stu-id="90336-272">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="90336-273">Définissez le champ **Fichiers des résultats des tests** sur `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="90336-273">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="90336-274">Définissez le champ **Titre de la série de tests** sur `Integration`</span><span class="sxs-lookup"><span data-stu-id="90336-274">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="90336-275">Sous **Options de contrôle**, cochez la case **Toujours exécuter**</span><span class="sxs-lookup"><span data-stu-id="90336-275">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="90336-276">Seconde publication des résultats des tests</span><span class="sxs-lookup"><span data-stu-id="90336-276">Second Publish Test Results</span></span>

1. <span data-ttu-id="90336-277">Sélectionnez `NUnit` pour le champ **Format des résultats des tests** </span><span class="sxs-lookup"><span data-stu-id="90336-277">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="90336-278">Définissez le champ **Fichiers des résultats des tests** sur `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="90336-278">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="90336-279">Définissez le champ **Titre de la série de tests** sur `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="90336-279">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="90336-280">Sous **Options de contrôle**, cochez la case **Toujours exécuter**</span><span class="sxs-lookup"><span data-stu-id="90336-280">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="90336-281">Vérifier les résultats</span><span class="sxs-lookup"><span data-stu-id="90336-281">Verify your results</span></span>

<span data-ttu-id="90336-282">Désormais, chaque fois que vous transmettez des modifications de la branche `ci-cd-example` vers TFS, une nouvelle build démarre.</span><span class="sxs-lookup"><span data-stu-id="90336-282">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="90336-283">Si la build se termine correctement, un nouveau déploiement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="90336-283">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="90336-284">Vous pouvez vérifier le résultat du déploiement en ouvrant un navigateur sur l’ordinateur client, puis en accédant à `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="90336-284">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="90336-285">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="90336-285">Next steps</span></span>

<span data-ttu-id="90336-286">Cet exemple configure le serveur DNS `TestAgent1` afin que l’URL `www.contoso.com` soit résolue en `TestAgent2`, mais il ne déploie pas réellement un site Web.</span><span class="sxs-lookup"><span data-stu-id="90336-286">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="90336-287">Le schéma pour effectuer cette opération est fourni dans le référentiel, sous le dossier `WebApp`.</span><span class="sxs-lookup"><span data-stu-id="90336-287">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="90336-288">Vous pouvez utiliser les stubs fournis pour créer des scripts psake, des tests Pester et des configurations DSC afin de déployer votre propre site Web.</span><span class="sxs-lookup"><span data-stu-id="90336-288">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>