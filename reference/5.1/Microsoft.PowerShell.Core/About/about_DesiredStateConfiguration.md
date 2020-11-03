---
description: Fournit une brève introduction à la fonctionnalité de configuration d’état souhaité (DSC) PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 2f043104c67078b98355b3e54171a8993e534837
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208730"
---
# <a name="about_desiredstateconfiguration"></a><span data-ttu-id="4fb9e-104">about_DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4fb9e-104">about_DesiredStateConfiguration</span></span>

## <a name="short-description"></a><span data-ttu-id="4fb9e-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="4fb9e-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="4fb9e-106">Fournit une brève introduction à la fonctionnalité de configuration d’état souhaité (DSC) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-106">Provides a brief introduction to the PowerShell Desired State Configuration (DSC) feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="4fb9e-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="4fb9e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="4fb9e-108">DSC est une plateforme de gestion dans PowerShell qui permet de déployer et de gérer les données de configuration des services logiciels, et de gérer l’environnement dans lequel ces services s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-108">DSC is a management platform in PowerShell that enables deploying and managing configuration data for software services, and managing the environment in which these services run.</span></span>

<span data-ttu-id="4fb9e-109">DSC fournit un ensemble d’extensions de langage PowerShell, de nouvelles applets de commande et de ressources que vous pouvez utiliser pour spécifier de façon déclarative la manière dont vous souhaitez que l’état de votre environnement logiciel soit configuré.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-109">DSC provides a set of PowerShell language extensions, new cmdlets, and resources that you can use to declaratively specify how you want the state of your software environment to be configured.</span></span> <span data-ttu-id="4fb9e-110">DSC vous permet également de mettre à jour et de gérer des configurations existantes.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-110">It also provides a means to maintain and manage existing configurations.</span></span>

<span data-ttu-id="4fb9e-111">DSC est introduit dans PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-111">DSC is introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="4fb9e-112">Pour plus d’informations sur DSC, consultez [vue d’ensemble de la configuration de l’état souhaité PowerShell](/powershell/scripting/dsc/overview/overview) dans la bibliothèque TechNet.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-112">For detailed information about DSC, see [PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview) in the TechNet Library.</span></span>

## <a name="developing-dsc-resources-with-classes"></a><span data-ttu-id="4fb9e-113">DÉVELOPPEMENT DE RESSOURCES DSC AVEC DES CLASSES</span><span class="sxs-lookup"><span data-stu-id="4fb9e-113">DEVELOPING DSC RESOURCES WITH CLASSES</span></span>

<span data-ttu-id="4fb9e-114">À compter de PowerShell 5,0, vous pouvez développer des ressources DSC à l’aide de classes.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-114">Starting in PowerShell 5.0, you can develop DSC resources by using classes.</span></span>
<span data-ttu-id="4fb9e-115">Pour plus d’informations, consultez [about_Classes](about_Classes.md)et [écriture d’une ressource DSC personnalisée avec les classes PowerShell](/previous-versions//dn948461(v=technet.10)) sur Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-115">For more information, see [about_Classes](about_Classes.md), and [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)) on Microsoft TechNet.</span></span>

## <a name="using-dsc"></a><span data-ttu-id="4fb9e-116">UTILISATION DE DSC</span><span class="sxs-lookup"><span data-stu-id="4fb9e-116">USING DSC</span></span>

<span data-ttu-id="4fb9e-117">Pour utiliser DSC pour configurer votre environnement, commencez par définir un bloc de script PowerShell à l’aide du mot clé configuration, suivi d’un identificateur, qui est à son tour suivi de la paire d’accolades délimitant le bloc.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-117">To use DSC to configure your environment, first define a PowerShell script block using the Configuration keyword, followed by an identifier, which is in turn followed by the pair of curly braces delimiting the block.</span></span> <span data-ttu-id="4fb9e-118">Dans le bloc de configuration, vous pouvez définir des blocs de nœuds qui spécifient l’état de configuration souhaité pour chaque nœud (ordinateur) de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-118">Inside the configuration block you can define node blocks that specify the desired configuration state for each node (computer) in the environment.</span></span> <span data-ttu-id="4fb9e-119">Un bloc node commence par le mot clé node, suivi du nom de l’ordinateur cible, qui peut être une variable.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-119">A node block starts with the Node keyword, followed by the name of the target computer, which can be a variable.</span></span> <span data-ttu-id="4fb9e-120">Après le nom de l’ordinateur, placez les accolades qui délimitent le bloc de nœud.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-120">After the computer name, come the curly braces that delimit the node block.</span></span> <span data-ttu-id="4fb9e-121">À l’intérieur du bloc node, vous pouvez définir des blocs de ressources pour configurer des ressources spécifiques.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-121">Inside the node block, you can define resource blocks to configure specific resources.</span></span> <span data-ttu-id="4fb9e-122">Un bloc de ressources commence par le nom de type de la ressource, suivi de l’identificateur que vous souhaitez spécifier pour ce bloc, suivi des accolades qui délimitent le bloc, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-122">A resource block starts with the type name of the resource, followed by the identifier you want to specify for that block, followed by the curly braces that delimit the block, as shown in the following example.</span></span>

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

<span data-ttu-id="4fb9e-123">Pour créer une configuration, appelez le bloc de configuration de la même façon que vous appelez une fonction PowerShell, en transmettant tous les paramètres attendus que vous avez définis (deux dans l’exemple ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="4fb9e-123">To create a configuration, invoke the Configuration block the same way you would invoke a PowerShell function, passing in any expected parameters you may have defined (two in the example above).</span></span> <span data-ttu-id="4fb9e-124">Par exemple, dans ce cas :</span><span class="sxs-lookup"><span data-stu-id="4fb9e-124">For example, in this case:</span></span>

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

<span data-ttu-id="4fb9e-125">Cela génère un fichier MOF par nœud dans le chemin d’accès que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-125">This generates a MOF file per node at the path you specify.</span></span> <span data-ttu-id="4fb9e-126">Ces fichiers MOF spécifient la configuration souhaitée pour chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-126">These MOF files specify the desired configuration for each node.</span></span> <span data-ttu-id="4fb9e-127">Ensuite, utilisez l’applet de commande suivante pour analyser les fichiers MOF de configuration, envoyer la configuration correspondante à chaque nœud et appliquer ces configurations.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-127">Next, use the following cmdlet to parse the configuration MOF files, send each node its corresponding configuration, and enact those configurations.</span></span> <span data-ttu-id="4fb9e-128">Notez que vous n’avez pas besoin de créer un fichier MOF distinct pour les ressources DSC basées sur une classe.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-128">Note that you do not need to create a separate MOF file for class-based DSC resources.</span></span>

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a><span data-ttu-id="4fb9e-129">UTILISATION DE DSC POUR MAINTENIR L’ÉTAT DE CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="4fb9e-129">USING DSC TO MAINTAIN CONFIGURATION STATE</span></span>

<span data-ttu-id="4fb9e-130">Avec DSC, la configuration est idempotent.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-130">With DSC, configuration is idempotent.</span></span> <span data-ttu-id="4fb9e-131">Cela signifie que si vous utilisez DSC pour mettre en œuvre la même configuration plusieurs fois, l’état de configuration qui en résulte sera toujours le même.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-131">This means that if you use DSC to enact the same configuration more than once, the resulting configuration state will always be the same.</span></span> <span data-ttu-id="4fb9e-132">Pour cette raison, si vous pensez que tous les nœuds de votre environnement peuvent avoir été dérives de l’état souhaité de la configuration, vous pouvez réactiver la même configuration DSC pour rétablir l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-132">Because of this, if you suspect that any nodes in your environment may have drifted from the desired state of configuration, you can enact the same DSC configuration again to bring them back to the desired state.</span></span> <span data-ttu-id="4fb9e-133">Vous n’avez pas besoin de modifier le script de configuration pour ne traiter que les ressources dont l’État est dérivé de l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-133">You do not need to modify the configuration script to address only those resources whose state has drifted from the desired state.</span></span>

<span data-ttu-id="4fb9e-134">L’exemple suivant montre comment vérifier si l’état réel de la configuration sur un nœud donné est dérivé de la dernière configuration DSC sur le nœud.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-134">The following example shows how you can verify whether the actual state of configuration on a given node has drifted from the last DSC configuration enacted on the node.</span></span> <span data-ttu-id="4fb9e-135">Dans cet exemple, nous vérifions la configuration de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-135">In this example we are checking the configuration of the local computer.</span></span>

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a><span data-ttu-id="4fb9e-136">RESSOURCES DSC INTÉGRÉES</span><span class="sxs-lookup"><span data-stu-id="4fb9e-136">BUILT-IN DSC RESOURCES</span></span>

<span data-ttu-id="4fb9e-137">Vous pouvez utiliser les ressources intégrées suivantes dans vos scripts de configuration :</span><span class="sxs-lookup"><span data-stu-id="4fb9e-137">You can use the following built-in resources in your configuration scripts:</span></span>

|<span data-ttu-id="4fb9e-138">Nom</span><span class="sxs-lookup"><span data-stu-id="4fb9e-138">Name</span></span>                  |<span data-ttu-id="4fb9e-139">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4fb9e-139">Properties</span></span>                                         |
|----------------------|---------------------------------------------------|
|<span data-ttu-id="4fb9e-140">Fichier</span><span class="sxs-lookup"><span data-stu-id="4fb9e-140">File</span></span>                  |<span data-ttu-id="4fb9e-141">{DestinationPath, attributs, Checksum, contenu...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-141">{DestinationPath, Attributes, Checksum, Content...}</span></span>|
|<span data-ttu-id="4fb9e-142">Archivage</span><span class="sxs-lookup"><span data-stu-id="4fb9e-142">Archive</span></span>               |<span data-ttu-id="4fb9e-143">{Destination, chemin d’accès, somme de contrôle, informations d’identification...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-143">{Destination, Path, Checksum, Credential...}</span></span>       |
|<span data-ttu-id="4fb9e-144">Environnement</span><span class="sxs-lookup"><span data-stu-id="4fb9e-144">Environment</span></span>           |<span data-ttu-id="4fb9e-145">{Nom, DependsOn, vérifier, chemin d’accès...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-145">{Name, DependsOn, Ensure, Path...}</span></span>                 |
|<span data-ttu-id="4fb9e-146">Groupe</span><span class="sxs-lookup"><span data-stu-id="4fb9e-146">Group</span></span>                 |<span data-ttu-id="4fb9e-147">{GroupName, Credential, DependsOn, Description...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-147">{GroupName, Credential, DependsOn, Description...}</span></span> |
|<span data-ttu-id="4fb9e-148">Journal</span><span class="sxs-lookup"><span data-stu-id="4fb9e-148">Log</span></span>                   |<span data-ttu-id="4fb9e-149">{Message, DependsOn, PsDscRunAsCredential}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-149">{Message, DependsOn, PsDscRunAsCredential}</span></span>         |
|<span data-ttu-id="4fb9e-150">Paquet</span><span class="sxs-lookup"><span data-stu-id="4fb9e-150">Package</span></span>               |<span data-ttu-id="4fb9e-151">{Nom, chemin d’accès, ProductId, arguments...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-151">{Name, Path, ProductId, Arguments...}</span></span>              |
|<span data-ttu-id="4fb9e-152">Registre</span><span class="sxs-lookup"><span data-stu-id="4fb9e-152">Registry</span></span>              |<span data-ttu-id="4fb9e-153">{Key, ValueName, DependsOn, vérifiez...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-153">{Key, ValueName, DependsOn, Ensure...}</span></span>             |
|<span data-ttu-id="4fb9e-154">Script</span><span class="sxs-lookup"><span data-stu-id="4fb9e-154">Script</span></span>                |<span data-ttu-id="4fb9e-155">{GetScript, Setscript s’exécute, TestScript, Credential...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-155">{GetScript, SetScript, TestScript, Credential...}</span></span>  |
|<span data-ttu-id="4fb9e-156">Service</span><span class="sxs-lookup"><span data-stu-id="4fb9e-156">Service</span></span>               |<span data-ttu-id="4fb9e-157">{Nom, BuiltInAccount, informations d’identification, dépendances...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-157">{Name, BuiltInAccount, Credential, Dependencies...}</span></span>|
|<span data-ttu-id="4fb9e-158">Utilisateur</span><span class="sxs-lookup"><span data-stu-id="4fb9e-158">User</span></span>                  |<span data-ttu-id="4fb9e-159">{UserName, DependsOn, description, Disabled...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-159">{UserName, DependsOn, Description, Disabled...}</span></span>    |
|<span data-ttu-id="4fb9e-160">WaitForAll</span><span class="sxs-lookup"><span data-stu-id="4fb9e-160">WaitForAll</span></span>            |<span data-ttu-id="4fb9e-161">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-161">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="4fb9e-162">WaitForAny</span><span class="sxs-lookup"><span data-stu-id="4fb9e-162">WaitForAny</span></span>            |<span data-ttu-id="4fb9e-163">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-163">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="4fb9e-164">WaitForSome</span><span class="sxs-lookup"><span data-stu-id="4fb9e-164">WaitForSome</span></span>           |<span data-ttu-id="4fb9e-165">{NodeCount, NodeName, ResourceName, DependsOn...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-165">{NodeCount, NodeName, ResourceName, DependsOn...}</span></span>  |
|<span data-ttu-id="4fb9e-166">WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="4fb9e-166">WindowsFeature</span></span>        |<span data-ttu-id="4fb9e-167">{Nom, informations d’identification, DependsOn, vérifier...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-167">{Name, Credential, DependsOn, Ensure...}</span></span>           |
|<span data-ttu-id="4fb9e-168">WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="4fb9e-168">WindowsOptionalFeature</span></span>|<span data-ttu-id="4fb9e-169">{Nom, DependsOn, vérifier, LogLevel...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-169">{Name, DependsOn, Ensure, LogLevel...}</span></span>             |
|<span data-ttu-id="4fb9e-170">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="4fb9e-170">WindowsProcess</span></span>        |<span data-ttu-id="4fb9e-171">{Arguments, chemin d’accès, informations d’identification, DependsOn...}</span><span class="sxs-lookup"><span data-stu-id="4fb9e-171">{Arguments, Path, Credential, DependsOn...}</span></span>        |

<span data-ttu-id="4fb9e-172">Pour obtenir la liste des ressources DSC disponibles sur votre système, exécutez l' `Get-DscResource` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-172">To get a list of available DSC resources on your system, run the `Get-DscResource` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="4fb9e-173">Dans les versions de PowerShell inférieures à 7.0, `Get-DscResource` ne trouve pas les ressources DSC basées sur une classe.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-173">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="4fb9e-174">L’exemple de cette rubrique montre comment utiliser les ressources file et WindowsFeature.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-174">The example in this topic demonstrates how to use the File and WindowsFeature resources.</span></span> <span data-ttu-id="4fb9e-175">Pour afficher toutes les propriétés que vous pouvez utiliser avec une ressource, insérez le curseur dans le mot clé de ressource (par exemple, fichier) dans votre script de configuration dans PowerShell ISE, maintenez la <kbd>touche Ctrl</kbd> + <kbd>espace</kbd> enfoncée.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-175">To see all properties that you can use with a resource, insert the cursor in the resource keyword (for example, File) within your configuration script in PowerShell ISE, hold down <kbd>CTRL</kbd>+<kbd>SPACEBAR</kbd></span></span>

## <a name="find-more-resources"></a><span data-ttu-id="4fb9e-176">RECHERCHER D’AUTRES RESSOURCES</span><span class="sxs-lookup"><span data-stu-id="4fb9e-176">FIND MORE RESOURCES</span></span>

<span data-ttu-id="4fb9e-177">Vous pouvez télécharger, installer et découvrir de nombreuses autres ressources DSC disponibles qui ont été créées par la communauté d’utilisateurs PowerShell et DSC, et par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-177">You can download, install, and learn about many other available DSC resources that have been created by the PowerShell and DSC user community, and by Microsoft.</span></span> <span data-ttu-id="4fb9e-178">Visitez le [PowerShell Gallery](https://www.powershellgallery.com/) pour parcourir les ressources DSC disponibles et en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="4fb9e-178">Visit the [PowerShell Gallery](https://www.powershellgallery.com/) to browse and learn about available DSC resources.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fb9e-179">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="4fb9e-179">SEE ALSO</span></span>

[<span data-ttu-id="4fb9e-180">Vue d’ensemble de la configuration d’état souhaité PowerShell</span><span class="sxs-lookup"><span data-stu-id="4fb9e-180">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="4fb9e-181">Ressources de configuration d’état souhaité PowerShell intégrées</span><span class="sxs-lookup"><span data-stu-id="4fb9e-181">Built-In PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/resources)

[<span data-ttu-id="4fb9e-182">Créer des ressources de configuration d’état souhaité PowerShell personnalisées</span><span class="sxs-lookup"><span data-stu-id="4fb9e-182">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
