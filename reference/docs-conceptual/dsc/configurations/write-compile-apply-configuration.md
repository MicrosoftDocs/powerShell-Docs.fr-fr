---
ms.date: 06/22/2020
keywords: dsc,powershell,configuration,service,installation
title: Écrire, compiler et appliquer une configuration
description: Cet exercice vous guide dans la création et l’application d’une configuration DSC du début à la fin. Dans l’exemple suivant, vous allez apprendre à écrire et à appliquer une configuration très simple
ms.openlocfilehash: f173fe0dc6cd73e2b49bb8c44a9ee1a53eab475f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645026"
---
# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="276c4-105">Écrire, compiler et appliquer une configuration</span><span class="sxs-lookup"><span data-stu-id="276c4-105">Write, Compile, and Apply a Configuration</span></span>

> <span data-ttu-id="276c4-106">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="276c4-106">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="276c4-107">Cet exercice vous guide dans la création et l’application d’une configuration DSC (Configuration d’état souhaité) du début à la fin.</span><span class="sxs-lookup"><span data-stu-id="276c4-107">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span> <span data-ttu-id="276c4-108">Dans l’exemple suivant, vous allez apprendre à écrire et à appliquer une configuration très simple.</span><span class="sxs-lookup"><span data-stu-id="276c4-108">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="276c4-109">La configuration vérifiera qu’il existe un fichier « HelloWorld.txt » sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="276c4-109">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span>
<span data-ttu-id="276c4-110">Si vous supprimez le fichier, DSC le recréera lors de sa prochaine fois mise à jour.</span><span class="sxs-lookup"><span data-stu-id="276c4-110">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="276c4-111">Pour obtenir une vue d’ensemble de DSC et de son fonctionnement, consultez [Présentation de Desired State Configuration pour les développeurs](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="276c4-111">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="276c4-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="276c4-112">Requirements</span></span>

<span data-ttu-id="276c4-113">Pour exécuter cet exemple, vous avez besoin d’un ordinateur exécutant PowerShell 4.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="276c4-113">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="276c4-114">Écrire la configuration</span><span class="sxs-lookup"><span data-stu-id="276c4-114">Write the configuration</span></span>

<span data-ttu-id="276c4-115">Une [configuration DSC](configurations.md) est une fonction PowerShell spéciale qui définit la façon dont vous souhaitez configurer un ou plusieurs ordinateurs cibles (nœuds).</span><span class="sxs-lookup"><span data-stu-id="276c4-115">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="276c4-116">Dans PowerShell ISE ou un autre éditeur PowerShell, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="276c4-116">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when
    # this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a
        # source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="276c4-117">Dans les scénarios plus avancés où plusieurs modules doivent être importés afin que vous puissiez utiliser de nombreuses ressources DSC dans la même configuration, veillez à placer chaque module sur une ligne distincte à l’aide de `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="276c4-117">In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a separate line using `Import-DscResource`.</span></span> <span data-ttu-id="276c4-118">Cela est plus facile à gérer dans le contrôle de code source et requis lors de l’utilisation de DSC dans Azure State Configuration.</span><span class="sxs-lookup"><span data-stu-id="276c4-118">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="276c4-119">Enregistrez le fichier en tant que « HelloWorld.ps1 ».</span><span class="sxs-lookup"><span data-stu-id="276c4-119">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="276c4-120">La définition d’une configuration s’apparente à celle d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="276c4-120">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="276c4-121">Le bloc **Nœud** spécifie le nœud cible à configurer, dans ce cas `localhost`.</span><span class="sxs-lookup"><span data-stu-id="276c4-121">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="276c4-122">La configuration appelle une [ressource](../resources/resources.md), la ressource `File`.</span><span class="sxs-lookup"><span data-stu-id="276c4-122">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="276c4-123">Les ressources s’assurent que le nœud cible est dans l’état défini par la configuration.</span><span class="sxs-lookup"><span data-stu-id="276c4-123">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="276c4-124">Compiler la configuration</span><span class="sxs-lookup"><span data-stu-id="276c4-124">Compile the configuration</span></span>

<span data-ttu-id="276c4-125">Pour qu’une configuration DSC soit appliquée à un nœud, elle doit tout d’abord être compilée dans un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="276c4-125">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span> <span data-ttu-id="276c4-126">L’exécution de la configuration, comme une fonction, compilera un fichier `.mof` pour chaque nœud défini par le bloc `Node`.</span><span class="sxs-lookup"><span data-stu-id="276c4-126">Running the configuration, like a function, will compile one `.mof` file for every Node defined by the `Node` block.</span></span> <span data-ttu-id="276c4-127">Pour exécuter la configuration, vous devez _dot sourcer_ votre script `HelloWorld.ps1` dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="276c4-127">In order to run the configuration, you need to _dot source_ your `HelloWorld.ps1` script into the current scope.</span></span> <span data-ttu-id="276c4-128">Pour plus d’informations, consultez [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="276c4-128">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="276c4-129">_Dot sourcez_ votre script `HelloWorld.ps1` en tapant le chemin où vous l’avez stocké, après le `. ` (point, espace).</span><span class="sxs-lookup"><span data-stu-id="276c4-129">_Dot source_ your `HelloWorld.ps1` script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="276c4-130">Vous pouvez ensuite exécuter votre configuration en l’appelant comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="276c4-130">You may then, run your configuration by calling it like a function.</span></span> <span data-ttu-id="276c4-131">Vous pouvez également appeler la fonction de configuration au bas du script afin de ne pas avoir à dot sourcer.</span><span class="sxs-lookup"><span data-stu-id="276c4-131">You could also invoke the configuration function at the bottom of the script so that you don't need to dot-source.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="276c4-132">Cela génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="276c4-132">This generates the following output:</span></span>

```Output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="276c4-133">Appliquer la configuration</span><span class="sxs-lookup"><span data-stu-id="276c4-133">Apply the configuration</span></span>

<span data-ttu-id="276c4-134">Maintenant que vous disposez du fichier MOF compilé, vous pouvez appliquer la configuration au nœud cible (dans ce cas, l’ordinateur local) en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="276c4-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="276c4-135">L’applet de commande `Start-DscConfiguration` indique au [Gestionnaire de configuration local](../managing-nodes/metaConfig.md), le moteur de DSC, qu’il doit appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="276c4-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span> <span data-ttu-id="276c4-136">Le LCM est chargé d’appeler les ressources DSC pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="276c4-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="276c4-137">Utilisez le code ci-dessous pour exécuter l’applet de commande `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="276c4-137">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="276c4-138">Spécifiez le chemin du répertoire où est stocké votre fichier `localhost.mof` au paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="276c4-138">Specify the directory path where your `localhost.mof` is stored to the **Path** parameter.</span></span> <span data-ttu-id="276c4-139">L’applet de commande `Start-DSCConfiguration` recherche tous les fichiers `<computername>.mof` dans le répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="276c4-139">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any `<computername>.mof` files.</span></span> <span data-ttu-id="276c4-140">L’applet de commande `Start-DSCConfiguration` tente d’appliquer chaque fichier `.mof` trouvé au `computername` spécifié par le nom de fichier (« localhost », « server01 », « dc-02 », etc.).</span><span class="sxs-lookup"><span data-stu-id="276c4-140">The `Start-DSCConfiguration` cmdlet attempts to apply each `.mof` file it finds to the `computername` specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="276c4-141">Si le paramètre `-Wait` n’est pas spécifié, `Start-DSCConfiguration` crée une tâche en arrière-plan pour exécuter l’opération.</span><span class="sxs-lookup"><span data-stu-id="276c4-141">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="276c4-142">Le fait de spécifier le paramètre `-Verbose` vous permet de regarder la sortie **détaillée** de l’opération.</span><span class="sxs-lookup"><span data-stu-id="276c4-142">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="276c4-143">`-Wait` et `-Verbose` sont tous deux des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="276c4-143">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="276c4-144">Tester la configuration</span><span class="sxs-lookup"><span data-stu-id="276c4-144">Test the configuration</span></span>

<span data-ttu-id="276c4-145">Une fois l’applet de commande `Start-DSCConfiguration` terminée, vous devez voir un fichier `HelloWorld.txt` à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="276c4-145">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a `HelloWorld.txt` file in the location you specified.</span></span> <span data-ttu-id="276c4-146">Vous pouvez vérifier le contenu avec l’applet de commande [Get-Content](/powershell/module/microsoft.powershell.management/get-content).</span><span class="sxs-lookup"><span data-stu-id="276c4-146">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="276c4-147">Vous pouvez également _tester_ l’état actuel à l’aide de [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="276c4-147">You can also _test_ the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="276c4-148">La sortie doit être `True` si le nœud est actuellement conforme à la configuration appliquée.</span><span class="sxs-lookup"><span data-stu-id="276c4-148">The output should be `True` if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```Output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```Output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="276c4-149">Réapplication de la configuration</span><span class="sxs-lookup"><span data-stu-id="276c4-149">Re-applying the configuration</span></span>

<span data-ttu-id="276c4-150">Pour voir votre configuration réappliquée, vous pouvez supprimer le fichier texte créé par votre configuration.</span><span class="sxs-lookup"><span data-stu-id="276c4-150">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="276c4-151">Utilisez l’applet de commande `Start-DSCConfiguration` avec le paramètre `-UseExisting`.</span><span class="sxs-lookup"><span data-stu-id="276c4-151">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="276c4-152">Le paramètre `-UseExisting` fait en sorte que `Start-DSCConfiguration` réapplique le fichier « current.mof », qui représente la dernière configuration correcte appliquée.</span><span class="sxs-lookup"><span data-stu-id="276c4-152">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="276c4-153">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="276c4-153">Next steps</span></span>

- <span data-ttu-id="276c4-154">En savoir plus sur les configurations DSC sous [Configurations DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="276c4-154">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="276c4-155">Consultez les ressources DSC disponibles et découvrez comment créer des ressources DSC personnalisées sous [Ressources DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="276c4-155">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="276c4-156">Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="276c4-156">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
