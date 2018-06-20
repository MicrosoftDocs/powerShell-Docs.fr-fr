---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configurations DSC
ms.openlocfilehash: d98bf0e85c12103d9b1eeded155bab1af364bd4c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188443"
---
# <a name="dsc-configurations"></a><span data-ttu-id="9d58d-103">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="9d58d-103">DSC Configurations</span></span>

><span data-ttu-id="9d58d-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9d58d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9d58d-105">Les configurations DSC sont des scripts PowerShell qui définissent un type spécial de fonction.</span><span class="sxs-lookup"><span data-stu-id="9d58d-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="9d58d-106">Pour définir une configuration, utilisez le mot clé PowerShell **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="9d58d-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="9d58d-107">Enregistrez le script comme fichier .ps1.</span><span class="sxs-lookup"><span data-stu-id="9d58d-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="9d58d-108">Syntaxe de configuration</span><span class="sxs-lookup"><span data-stu-id="9d58d-108">Configuration syntax</span></span>

<span data-ttu-id="9d58d-109">Un script de configuration comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9d58d-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="9d58d-110">Le bloc **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="9d58d-110">The **Configuration** block.</span></span> <span data-ttu-id="9d58d-111">Il s’agit du bloc de script le plus externe.</span><span class="sxs-lookup"><span data-stu-id="9d58d-111">This is the outermost script block.</span></span> <span data-ttu-id="9d58d-112">Pour le définir, utilisez le mot clé **Configuration**, puis attribuez-lui un nom.</span><span class="sxs-lookup"><span data-stu-id="9d58d-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="9d58d-113">Ici, le nom de la configuration est « MyDscConfiguration ».</span><span class="sxs-lookup"><span data-stu-id="9d58d-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="9d58d-114">Un ou plusieurs blocs **Node**.</span><span class="sxs-lookup"><span data-stu-id="9d58d-114">One or more **Node** blocks.</span></span> <span data-ttu-id="9d58d-115">Ils définissent les nœuds (ordinateurs ou machines virtuelles) que vous configurez.</span><span class="sxs-lookup"><span data-stu-id="9d58d-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="9d58d-116">Dans la configuration ci-dessus, un bloc **Node** cible un ordinateur nommé « TEST-PC1 ».</span><span class="sxs-lookup"><span data-stu-id="9d58d-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="9d58d-117">Un ou plusieurs blocs de ressources.</span><span class="sxs-lookup"><span data-stu-id="9d58d-117">One or more resource blocks.</span></span> <span data-ttu-id="9d58d-118">C’est là que la configuration définit les propriétés pour les ressources qu’elle configure.</span><span class="sxs-lookup"><span data-stu-id="9d58d-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="9d58d-119">Ici, nous avons deux blocs de ressources qui appellent tous les deux la ressource « WindowsFeature ».</span><span class="sxs-lookup"><span data-stu-id="9d58d-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="9d58d-120">Dans un bloc **Configuration**, vous pouvez faire tout ce qu’il est possible de faire dans une fonction PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d58d-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="9d58d-121">Par exemple, dans l’exemple précédent, si vous ne vouliez pas coder en dur le nom de l’ordinateur cible dans la configuration, vous auriez pu ajouter un paramètre pour le nom du nœud :</span><span class="sxs-lookup"><span data-stu-id="9d58d-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName

```

<span data-ttu-id="9d58d-122">Dans cet exemple, vous spécifiez le nom du nœud en le passant comme paramètre **ComputerName** quand vous compilez la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="9d58d-123">Par défaut, le nom est « localhost ».</span><span class="sxs-lookup"><span data-stu-id="9d58d-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="9d58d-124">Compilation de la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-124">Compiling the configuration</span></span>

<span data-ttu-id="9d58d-125">Avant de pouvoir promulguer une configuration, vous devez la compiler dans un document MOF.</span><span class="sxs-lookup"><span data-stu-id="9d58d-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="9d58d-126">Pour cela, appelez la configuration comme pour une fonction PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d58d-126">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="9d58d-127">La dernière ligne de l’exemple, qui contient uniquement le nom de la configuration, appelle la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="9d58d-128">**Remarque** : Pour appeler une configuration, la fonction doit se trouver dans la portée globale (comme pour toutes les fonctions PowerShell).</span><span class="sxs-lookup"><span data-stu-id="9d58d-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
><span data-ttu-id="9d58d-129">Vous avez le choix entre « dot sourcer » le script, exécuter le script de configuration avec la touche F5 ou cliquer sur le bouton **Exécuter le script** dans l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="9d58d-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
><span data-ttu-id="9d58d-130">Pour « dot sourcer » le script, exécutez la commande `. .\myConfig.ps1`, où `myConfig.ps1` correspond au nom du fichier de script qui contient votre configuration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="9d58d-131">Quand vous appelez la configuration, elle :</span><span class="sxs-lookup"><span data-stu-id="9d58d-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="9d58d-132">Résout toutes les variables.</span><span class="sxs-lookup"><span data-stu-id="9d58d-132">Resolves all variables</span></span>
- <span data-ttu-id="9d58d-133">Crée un dossier dans le répertoire actif portant le même nom que la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="9d58d-134">Crée un fichier nommé _nom_nœud_.mof dans le nouveau répertoire, où _nom_nœud_ correspond au nom du nœud cible de la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
    <span data-ttu-id="9d58d-135">S’il existe plusieurs nœuds, un fichier MOF est créé pour chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="9d58d-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="9d58d-136">**Remarque** : Le fichier MOF contient toutes les informations de configuration du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="9d58d-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="9d58d-137">Il est donc important de le sécuriser.</span><span class="sxs-lookup"><span data-stu-id="9d58d-137">Because of this, it’s important to keep it secure.</span></span>
><span data-ttu-id="9d58d-138">Pour plus d’informations, consultez [Sécurisation du fichier MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="9d58d-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="9d58d-139">Après la compilation de la première configuration, vous obtenez la structure de dossiers suivante :</span><span class="sxs-lookup"><span data-stu-id="9d58d-139">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="9d58d-140">Si la configuration prend un paramètre, comme dans le deuxième exemple, le paramètre doit être fourni au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="9d58d-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="9d58d-141">Voici à quoi cela ressemble :</span><span class="sxs-lookup"><span data-stu-id="9d58d-141">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-dependson"></a><span data-ttu-id="9d58d-142">Utilisation de DependsOn</span><span class="sxs-lookup"><span data-stu-id="9d58d-142">Using DependsOn</span></span>

<span data-ttu-id="9d58d-143">**DependsOn** est un mot clé DSC très utile.</span><span class="sxs-lookup"><span data-stu-id="9d58d-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="9d58d-144">En général (même si ce n’est pas toujours le cas), DSC applique les ressources dans l’ordre dans lequel elles figurent dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="9d58d-145">Toutefois, **DependsOn** spécifie les ressources qui dépendent d’autres ressources, et le gestionnaire de configuration local permet de s’assurer qu’elles sont appliquées dans le bon ordre, quel que soit l’ordre dans lequel les instances de ressources sont définies.</span><span class="sxs-lookup"><span data-stu-id="9d58d-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="9d58d-146">Par exemple, une configuration peut spécifier qu’une instance de la ressource **User** dépend de l’existence d’une instance **Group** :</span><span class="sxs-lookup"><span data-stu-id="9d58d-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="9d58d-147">Utilisation de nouvelles ressources dans la configuration</span><span class="sxs-lookup"><span data-stu-id="9d58d-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="9d58d-148">Si vous avez exécuté les exemples précédents, vous avez peut-être remarqué un avertissement disant que vous utilisez une ressource sans l’avoir importée explicitement.</span><span class="sxs-lookup"><span data-stu-id="9d58d-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="9d58d-149">Actuellement, DSC est fourni avec 12 ressources contenues dans le module PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="9d58d-150">Les autres ressources des modules externes doivent être placées dans `$env:PSModulePath` pour être reconnues par le gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="9d58d-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="9d58d-151">Une nouvelle applet de commande, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), peut être utilisée pour déterminer quelles ressources sont installées sur le système et lesquelles peuvent être utilisées par le gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="9d58d-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="9d58d-152">Une fois ces modules placés dans `$env:PSModulePath` et correctement reconnus par [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ils doivent encore être chargés dans votre configuration.</span><span class="sxs-lookup"><span data-stu-id="9d58d-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="9d58d-153">**Import-DscResource** est un mot clé dynamique qui peut être reconnu uniquement au sein d’un bloc **Configuration** (ce n’est donc pas une applet de commande).</span><span class="sxs-lookup"><span data-stu-id="9d58d-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="9d58d-154">**Import-DscResource** accepte deux paramètres :</span><span class="sxs-lookup"><span data-stu-id="9d58d-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="9d58d-155">**ModuleName** est recommandé pour l’utilisation d’**Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="9d58d-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="9d58d-156">Il accepte le nom du module qui contient les ressources à importer (ainsi qu’un tableau de chaînes comprenant des noms de modules).</span><span class="sxs-lookup"><span data-stu-id="9d58d-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="9d58d-157">**Name** correspond au nom de la ressource à importer.</span><span class="sxs-lookup"><span data-stu-id="9d58d-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="9d58d-158">Il ne s’agit pas du nom convivial retourné comme « Name » par [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), mais du nom de classe utilisé lors de la définition du schéma de la ressource (retourné comme **ResourceType** par [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="9d58d-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d58d-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d58d-159">See Also</span></span>
* [<span data-ttu-id="9d58d-160">Présentation de la configuration de l’état souhaité de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d58d-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="9d58d-161">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="9d58d-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="9d58d-162">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="9d58d-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)
