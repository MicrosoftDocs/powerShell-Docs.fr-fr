---
ms.date: 06/22/2020
keywords: dsc,powershell,configuration,service,installation
title: Écrire, compiler et appliquer une configuration
ms.openlocfilehash: 9acb2db882795d7150326fadb2964deb1105b2cc
ms.sourcegitcommit: 7eea0885dd7ac90ab36e5664501438a292217f7f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85295673"
---
# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="16c71-103">Écrire, compiler et appliquer une configuration</span><span class="sxs-lookup"><span data-stu-id="16c71-103">Write, Compile, and Apply a Configuration</span></span>

> <span data-ttu-id="16c71-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="16c71-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="16c71-105">Cet exercice vous guide dans la création et l’application d’une configuration DSC (Configuration d’état souhaité) du début à la fin.</span><span class="sxs-lookup"><span data-stu-id="16c71-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span> <span data-ttu-id="16c71-106">Dans l’exemple suivant, vous allez apprendre à écrire et à appliquer une configuration très simple.</span><span class="sxs-lookup"><span data-stu-id="16c71-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="16c71-107">La configuration vérifiera qu’il existe un fichier « HelloWorld.txt » sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="16c71-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span>
<span data-ttu-id="16c71-108">Si vous supprimez le fichier, DSC le recréera lors de sa prochaine fois mise à jour.</span><span class="sxs-lookup"><span data-stu-id="16c71-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="16c71-109">Pour obtenir une vue d’ensemble de DSC et de son fonctionnement, consultez [Présentation de Desired State Configuration pour les développeurs](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="16c71-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="16c71-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="16c71-110">Requirements</span></span>

<span data-ttu-id="16c71-111">Pour exécuter cet exemple, vous avez besoin d’un ordinateur exécutant PowerShell 4.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="16c71-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="16c71-112">Écrire la configuration</span><span class="sxs-lookup"><span data-stu-id="16c71-112">Write the configuration</span></span>

<span data-ttu-id="16c71-113">Une [configuration DSC](configurations.md) est une fonction PowerShell spéciale qui définit la façon dont vous souhaitez configurer un ou plusieurs ordinateurs cibles (nœuds).</span><span class="sxs-lookup"><span data-stu-id="16c71-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="16c71-114">Dans PowerShell ISE ou un autre éditeur PowerShell, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="16c71-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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
> <span data-ttu-id="16c71-115">Dans les scénarios plus avancés où plusieurs modules doivent être importés afin que vous puissiez utiliser de nombreuses ressources DSC dans la même configuration, veillez à placer chaque module sur une ligne distincte à l’aide de `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="16c71-115">In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a separate line using `Import-DscResource`.</span></span> <span data-ttu-id="16c71-116">Cela est plus facile à gérer dans le contrôle de code source et requis lors de l’utilisation de DSC dans Azure State Configuration.</span><span class="sxs-lookup"><span data-stu-id="16c71-116">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="16c71-117">Enregistrez le fichier en tant que « HelloWorld.ps1 ».</span><span class="sxs-lookup"><span data-stu-id="16c71-117">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="16c71-118">La définition d’une configuration s’apparente à celle d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="16c71-118">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="16c71-119">Le bloc **Nœud** spécifie le nœud cible à configurer, dans ce cas `localhost`.</span><span class="sxs-lookup"><span data-stu-id="16c71-119">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="16c71-120">La configuration appelle une [ressource](../resources/resources.md), la ressource `File`.</span><span class="sxs-lookup"><span data-stu-id="16c71-120">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="16c71-121">Les ressources s’assurent que le nœud cible est dans l’état défini par la configuration.</span><span class="sxs-lookup"><span data-stu-id="16c71-121">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="16c71-122">Compiler la configuration</span><span class="sxs-lookup"><span data-stu-id="16c71-122">Compile the configuration</span></span>

<span data-ttu-id="16c71-123">Pour qu’une configuration DSC soit appliquée à un nœud, elle doit tout d’abord être compilée dans un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="16c71-123">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span> <span data-ttu-id="16c71-124">L’exécution de la configuration, comme une fonction, compilera un fichier `.mof` pour chaque nœud défini par le bloc `Node`.</span><span class="sxs-lookup"><span data-stu-id="16c71-124">Running the configuration, like a function, will compile one `.mof` file for every Node defined by the `Node` block.</span></span> <span data-ttu-id="16c71-125">Pour exécuter la configuration, vous devez _dot sourcer_ votre script `HelloWorld.ps1` dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="16c71-125">In order to run the configuration, you need to _dot source_ your `HelloWorld.ps1` script into the current scope.</span></span> <span data-ttu-id="16c71-126">Pour plus d’informations, consultez [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="16c71-126">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="16c71-127">_Dot sourcez_ votre script `HelloWorld.ps1` en tapant le chemin où vous l’avez stocké, après le `. ` (point, espace).</span><span class="sxs-lookup"><span data-stu-id="16c71-127">_Dot source_ your `HelloWorld.ps1` script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="16c71-128">Vous pouvez ensuite exécuter votre configuration en l’appelant comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="16c71-128">You may then, run your configuration by calling it like a function.</span></span> <span data-ttu-id="16c71-129">Vous pouvez également appeler la fonction de configuration au bas du script afin de ne pas avoir à dot sourcer.</span><span class="sxs-lookup"><span data-stu-id="16c71-129">You could also invoke the configuration function at the bottom of the script so that you don't need to dot-source.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="16c71-130">Cela génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="16c71-130">This generates the following output:</span></span>

```Output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="16c71-131">Appliquer la configuration</span><span class="sxs-lookup"><span data-stu-id="16c71-131">Apply the configuration</span></span>

<span data-ttu-id="16c71-132">Maintenant que vous disposez du fichier MOF compilé, vous pouvez appliquer la configuration au nœud cible (dans ce cas, l’ordinateur local) en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="16c71-132">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="16c71-133">L’applet de commande `Start-DscConfiguration` indique au [Gestionnaire de configuration local](../managing-nodes/metaConfig.md), le moteur de DSC, qu’il doit appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="16c71-133">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span> <span data-ttu-id="16c71-134">Le LCM est chargé d’appeler les ressources DSC pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="16c71-134">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="16c71-135">Utilisez le code ci-dessous pour exécuter l’applet de commande `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="16c71-135">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="16c71-136">Spécifiez le chemin du répertoire où est stocké votre fichier `localhost.mof` au paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="16c71-136">Specify the directory path where your `localhost.mof` is stored to the **Path** parameter.</span></span> <span data-ttu-id="16c71-137">L’applet de commande `Start-DSCConfiguration` recherche tous les fichiers `<computername>.mof` dans le répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="16c71-137">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any `<computername>.mof` files.</span></span> <span data-ttu-id="16c71-138">L’applet de commande `Start-DSCConfiguration` tente d’appliquer chaque fichier `.mof` trouvé au `computername` spécifié par le nom de fichier (« localhost », « server01 », « dc-02 », etc.).</span><span class="sxs-lookup"><span data-stu-id="16c71-138">The `Start-DSCConfiguration` cmdlet attempts to apply each `.mof` file it finds to the `computername` specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="16c71-139">Si le paramètre `-Wait` n’est pas spécifié, `Start-DSCConfiguration` crée une tâche en arrière-plan pour exécuter l’opération.</span><span class="sxs-lookup"><span data-stu-id="16c71-139">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="16c71-140">Le fait de spécifier le paramètre `-Verbose` vous permet de regarder la sortie **détaillée** de l’opération.</span><span class="sxs-lookup"><span data-stu-id="16c71-140">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="16c71-141">`-Wait` et `-Verbose` sont tous deux des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="16c71-141">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="16c71-142">Tester la configuration</span><span class="sxs-lookup"><span data-stu-id="16c71-142">Test the configuration</span></span>

<span data-ttu-id="16c71-143">Une fois l’applet de commande `Start-DSCConfiguration` terminée, vous devez voir un fichier `HelloWorld.txt` à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="16c71-143">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a `HelloWorld.txt` file in the location you specified.</span></span> <span data-ttu-id="16c71-144">Vous pouvez vérifier le contenu avec l’applet de commande [Get-Content](/powershell/module/microsoft.powershell.management/get-content).</span><span class="sxs-lookup"><span data-stu-id="16c71-144">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="16c71-145">Vous pouvez également _tester_ l’état actuel à l’aide de [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="16c71-145">You can also _test_ the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="16c71-146">La sortie doit être `True` si le nœud est actuellement conforme à la configuration appliquée.</span><span class="sxs-lookup"><span data-stu-id="16c71-146">The output should be `True` if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="16c71-147">Réapplication de la configuration</span><span class="sxs-lookup"><span data-stu-id="16c71-147">Re-applying the configuration</span></span>

<span data-ttu-id="16c71-148">Pour voir votre configuration réappliquée, vous pouvez supprimer le fichier texte créé par votre configuration.</span><span class="sxs-lookup"><span data-stu-id="16c71-148">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="16c71-149">Utilisez l’applet de commande `Start-DSCConfiguration` avec le paramètre `-UseExisting`.</span><span class="sxs-lookup"><span data-stu-id="16c71-149">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="16c71-150">Le paramètre `-UseExisting` fait en sorte que `Start-DSCConfiguration` réapplique le fichier « current.mof », qui représente la dernière configuration correcte appliquée.</span><span class="sxs-lookup"><span data-stu-id="16c71-150">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="16c71-151">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="16c71-151">Next steps</span></span>

- <span data-ttu-id="16c71-152">En savoir plus sur les configurations DSC sous [Configurations DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="16c71-152">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="16c71-153">Consultez les ressources DSC disponibles et découvrez comment créer des ressources DSC personnalisées sous [Ressources DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="16c71-153">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="16c71-154">Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="16c71-154">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
