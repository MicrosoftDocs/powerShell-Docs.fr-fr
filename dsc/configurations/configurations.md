---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurations DSC
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401449"
---
# <a name="dsc-configurations"></a><span data-ttu-id="9d3a9-103">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="9d3a9-103">DSC Configurations</span></span>

> <span data-ttu-id="9d3a9-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9d3a9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9d3a9-105">Les configurations DSC sont des scripts PowerShell qui définissent un type spécial de fonction.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="9d3a9-106">Pour définir une configuration, utilisez le mot clé PowerShell **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="9d3a9-107">Enregistrez le script sous un `.ps1` fichier.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="9d3a9-108">Syntaxe de configuration</span><span class="sxs-lookup"><span data-stu-id="9d3a9-108">Configuration syntax</span></span>

<span data-ttu-id="9d3a9-109">Un script de configuration comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9d3a9-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="9d3a9-110">Le bloc **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-110">The **Configuration** block.</span></span> <span data-ttu-id="9d3a9-111">Il s’agit du bloc de script le plus externe.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-111">This is the outermost script block.</span></span> <span data-ttu-id="9d3a9-112">Pour le définir, utilisez le mot clé **Configuration**, puis attribuez-lui un nom.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="9d3a9-113">Ici, le nom de la configuration est « MyDscConfiguration ».</span><span class="sxs-lookup"><span data-stu-id="9d3a9-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="9d3a9-114">Un ou plusieurs blocs **Node**.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-114">One or more **Node** blocks.</span></span> <span data-ttu-id="9d3a9-115">Ils définissent les nœuds (ordinateurs ou machines virtuelles) que vous configurez.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="9d3a9-116">Dans la configuration ci-dessus, un bloc **Node** cible un ordinateur nommé « TEST-PC1 ».</span><span class="sxs-lookup"><span data-stu-id="9d3a9-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="9d3a9-117">Le bloc de nœud peut accepter plusieurs noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="9d3a9-118">Un ou plusieurs blocs de ressources.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-118">One or more resource blocks.</span></span> <span data-ttu-id="9d3a9-119">C’est là que la configuration définit les propriétés pour les ressources qu’elle configure.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="9d3a9-120">Ici, nous avons deux blocs de ressources qui appellent tous les deux la ressource « WindowsFeature ».</span><span class="sxs-lookup"><span data-stu-id="9d3a9-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="9d3a9-121">Dans un bloc **Configuration**, vous pouvez faire tout ce qu’il est possible de faire dans une fonction PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="9d3a9-122">Par exemple, dans l’exemple précédent, si vous ne vouliez pas coder en dur le nom de l’ordinateur cible dans la configuration, vous auriez pu ajouter un paramètre pour le nom du nœud :</span><span class="sxs-lookup"><span data-stu-id="9d3a9-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="9d3a9-123">Dans cet exemple, vous spécifiez le nom du nœud en le passant comme paramètre **ComputerName** quand vous compilez la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="9d3a9-124">Par défaut, le nom est « localhost ».</span><span class="sxs-lookup"><span data-stu-id="9d3a9-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="9d3a9-125">Le **nœud** bloc peut également accepter plusieurs noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="9d3a9-126">Dans l’exemple ci-dessus, vous pouvez utiliser la `-ComputerName` paramètre ou une liste de pass séparées par des virgules d’ordinateurs directement à la **nœud** bloc.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="9d3a9-127">Lorsque vous spécifiez une liste d’ordinateurs à la **nœud** bloc, au sein d’une Configuration, vous devez utiliser la notation de tableau.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="9d3a9-128">Compilation de la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-128">Compiling the configuration</span></span>

<span data-ttu-id="9d3a9-129">Avant de pouvoir promulguer une configuration, vous devez la compiler dans un document MOF.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="9d3a9-130">Pour cela, appelez la configuration comme pour une fonction PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="9d3a9-131">La dernière ligne de l’exemple, qui contient uniquement le nom de la configuration, appelle la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="9d3a9-132">Pour appeler une configuration, la fonction doit se trouver dans la portée globale (comme pour toutes les fonctions PowerShell).</span><span class="sxs-lookup"><span data-stu-id="9d3a9-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="9d3a9-133">Vous avez le choix entre « dot sourcer » le script, exécuter le script de configuration avec la touche F5 ou cliquer sur le bouton **Exécuter le script** dans l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="9d3a9-134">Pour « dot sourcer » le script, exécutez la commande `. .\myConfig.ps1`, où `myConfig.ps1` correspond au nom du fichier de script qui contient votre configuration.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="9d3a9-135">Quand vous appelez la configuration, elle :</span><span class="sxs-lookup"><span data-stu-id="9d3a9-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="9d3a9-136">Résout toutes les variables.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-136">Resolves all variables</span></span>
- <span data-ttu-id="9d3a9-137">Crée un dossier dans le répertoire actif portant le même nom que la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="9d3a9-138">Crée un fichier nommé _nom_nœud_.mof dans le nouveau répertoire, où _nom_nœud_ correspond au nom du nœud cible de la configuration.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="9d3a9-139">S’il existe plusieurs nœuds, un fichier MOF est créé pour chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="9d3a9-140">Le fichier MOF contient toutes les informations de configuration du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="9d3a9-141">Il est donc important de le sécuriser.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-141">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="9d3a9-142">Pour plus d’informations, consultez [Sécurisation du fichier MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="9d3a9-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="9d3a9-143">Après la compilation de la première configuration, vous obtenez la structure de dossiers suivante :</span><span class="sxs-lookup"><span data-stu-id="9d3a9-143">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="9d3a9-144">Si la configuration prend un paramètre, comme dans le deuxième exemple, le paramètre doit être fourni au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="9d3a9-145">Voici à quoi cela ressemble :</span><span class="sxs-lookup"><span data-stu-id="9d3a9-145">Here's how that would look:</span></span>

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

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="9d3a9-146">Utilisation de nouvelles ressources dans la configuration</span><span class="sxs-lookup"><span data-stu-id="9d3a9-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="9d3a9-147">Si vous avez exécuté les exemples précédents, vous avez peut-être remarqué un avertissement disant que vous utilisez une ressource sans l’avoir importée explicitement.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="9d3a9-148">Actuellement, DSC est fourni avec 12 ressources contenues dans le module PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="9d3a9-149">Une nouvelle cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), peut être utilisée pour déterminer quelles ressources sont installées sur le système et lesquelles peuvent être utilisées par le gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="9d3a9-150">Une fois ces modules placés dans `$env:PSModulePath` et correctement reconnus par [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ils doivent encore être chargés dans votre configuration.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="9d3a9-151">**Import-DscResource** est un mot clé dynamique qui peut être reconnu uniquement au sein d’un **Configuration** bloc, il n’est pas une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="9d3a9-152">**Import-DscResource** accepte deux paramètres :</span><span class="sxs-lookup"><span data-stu-id="9d3a9-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="9d3a9-153">**ModuleName** est recommandé pour l’utilisation d’**Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="9d3a9-154">Il accepte le nom du module qui contient les ressources à importer (ainsi qu’un tableau de chaînes comprenant des noms de modules).</span><span class="sxs-lookup"><span data-stu-id="9d3a9-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="9d3a9-155">**Name** correspond au nom de la ressource à importer.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="9d3a9-156">Il ne s’agit pas du nom convivial retourné comme « Name » par [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), mais du nom de classe utilisé lors de la définition du schéma de la ressource (retourné comme **ResourceType** par [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="9d3a9-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="9d3a9-157">Pour plus d’informations sur l’utilisation de `Import-DSCResource`, consultez [Import-DSCResource à l’aide de](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="9d3a9-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="9d3a9-158">Différences de v4 et v5 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d3a9-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="9d3a9-159">Il existe des différences dans où les ressources DSC besoin d’être stocké dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="9d3a9-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="9d3a9-160">Pour plus d’informations, consultez [emplacement de la ressource](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="9d3a9-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d3a9-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d3a9-161">See Also</span></span>

- [<span data-ttu-id="9d3a9-162">Présentation de la configuration de l’état souhaité de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d3a9-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="9d3a9-163">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="9d3a9-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="9d3a9-164">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="9d3a9-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
