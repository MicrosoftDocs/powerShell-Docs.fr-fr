---
ms.date: 12/12/2018
keywords: DSC, powershell, configuration, service, le programme d’installation
title: Écrire, compiler et appliquer une configuration
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401275"
---
> <span data-ttu-id="dc2dc-103">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dc2dc-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="dc2dc-104">Écrire, compiler et appliquer une configuration</span><span class="sxs-lookup"><span data-stu-id="dc2dc-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="dc2dc-105">Cet exercice vous guide dans la création et l’application d’une configuration DSC (Configuration d’état souhaité) du début à la fin.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="dc2dc-106">Dans l’exemple suivant, vous allez apprendre à écrire et appliquer une Configuration très simple.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="dc2dc-107">La Configuration garantit qu'un fichier « HelloWorld.txt » existe sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="dc2dc-108">Si vous supprimez le fichier, DSC il recrée la prochaine fois qu’il met à jour.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="dc2dc-109">Pour une vue d’ensemble de DSC et de son fonctionnement, consultez [Desired State Configuration de présentation pour les développeurs](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="dc2dc-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc2dc-110">Requirements</span></span>

<span data-ttu-id="dc2dc-111">Pour exécuter cet exemple, vous devez un ordinateur qui exécute PowerShell 4.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="dc2dc-112">Écrire la configuration</span><span class="sxs-lookup"><span data-stu-id="dc2dc-112">Write the configuration</span></span>

<span data-ttu-id="dc2dc-113">Une [configuration DSC](configurations.md) est une fonction PowerShell spéciale qui définit la façon dont vous souhaitez configurer un ou plusieurs ordinateurs cibles (nœuds).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="dc2dc-114">Dans PowerShell ISE, ou un autre éditeur de PowerShell, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="dc2dc-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="dc2dc-115">Enregistrez le fichier en tant que « HelloWorld.ps1 ».</span><span class="sxs-lookup"><span data-stu-id="dc2dc-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="dc2dc-116">La définition d’une Configuration est comme la définition d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="dc2dc-117">Le bloc **Nœud** spécifie le nœud cible à configurer, dans ce cas `localhost`.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="dc2dc-118">La configuration appelle une [ressources](../resources/resources.md), le `File` ressource.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="dc2dc-119">Les ressources s’assurent que le nœud cible est dans l’état défini par la configuration.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="dc2dc-120">Compiler la configuration</span><span class="sxs-lookup"><span data-stu-id="dc2dc-120">Compile the configuration</span></span>

<span data-ttu-id="dc2dc-121">Pour qu’une configuration DSC soit appliquée à un nœud, elle doit tout d’abord être compilée dans un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="dc2dc-122">Exécution de la configuration, comme une fonction, compilera un fichier « .mof » pour chaque nœud défini par le `Node` bloc.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="dc2dc-123">Pour exécuter la configuration, vous devez *source de point* votre script de « HelloWorld.ps1 » dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="dc2dc-124">Pour plus d’informations, consultez [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="dc2dc-125">*Source de point* votre script de « HelloWorld.ps1 » en tapant dans le chemin d’accès où vous avez stocké, après le `. ` (point, espace).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="dc2dc-126">Vous pouvez ensuite exécuter votre configuration en l’appelant comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-126">You may then, run your configuration by calling it like a Function.</span></span>

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="dc2dc-127">Cela génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="dc2dc-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="dc2dc-128">Appliquer la configuration</span><span class="sxs-lookup"><span data-stu-id="dc2dc-128">Apply the configuration</span></span>

<span data-ttu-id="dc2dc-129">Maintenant que vous disposez du fichier MOF compilé, vous pouvez appliquer la configuration au nœud cible (dans ce cas, l’ordinateur local) en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="dc2dc-130">Le `Start-DscConfiguration` applet de commande indique le [Gestionnaire de Configuration Local (LCM)](../managing-nodes/metaConfig.md), le moteur de DSC, pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="dc2dc-131">Le LCM est chargé d’appeler les ressources DSC pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="dc2dc-132">Le code ci-dessous permet d’exécuter le `Start-DSCConfiguration` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="dc2dc-133">Spécifiez le chemin du répertoire où se trouve votre « localhost.mof » à la `-Path` paramètre.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="dc2dc-134">Le `Start-DSCConfiguration` applet de commande recherche dans le répertoire spécifié pour les «\<computername\>.mof « fichiers.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="dc2dc-135">Le `Start-DSCConfiguration` applet de commande tente d’appliquer chaque fichier « .mof » trouvé pour le nom d’ordinateur spécifié par le nom de fichier (« localhost », « server01 », « dc-02 », etc.).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="dc2dc-136">Si le `-Wait` paramètre n’est pas spécifié, `Start-DSCConfiguration` crée une tâche en arrière-plan pour exécuter l’opération.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="dc2dc-137">En spécifiant le `-Verbose` paramètre vous permet de regarder le **Verbose** sortie de l’opération.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="dc2dc-138">`-Wait`, et `-Verbose` sont les deux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="dc2dc-139">Tester la configuration</span><span class="sxs-lookup"><span data-stu-id="dc2dc-139">Test the configuration</span></span>

<span data-ttu-id="dc2dc-140">Une fois le `Start-DSCConfiguration` applet de commande est terminée, vous devriez voir un fichier « HelloWorld.txt » dans l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="dc2dc-141">Vous pouvez vérifier le contenu avec le [Get-Content](/powershell/module/microsoft.powershell.management/get-content) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="dc2dc-142">Vous pouvez également *tester* l’état actuel à l’aide [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="dc2dc-143">La sortie doit être « True » si le nœud est actuellement compatible avec la Configuration appliquée.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="dc2dc-144">Ré-appliquer la configuration</span><span class="sxs-lookup"><span data-stu-id="dc2dc-144">Re-applying the configuration</span></span>

<span data-ttu-id="dc2dc-145">Pour afficher votre configuration sont appliquées à nouveau, vous pouvez supprimer le fichier texte créé par votre Configuration.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="dc2dc-146">L’utilisation du `Start-DSCConfiguration` applet de commande avec le `-UseExisting` paramètre.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="dc2dc-147">Le `-UseExisting` paramètre demande à `Start-DSCConfiguration` pour ré-appliquer le fichier « current.mof », qui représente le plus récemment correctement appliqué configuration.</span><span class="sxs-lookup"><span data-stu-id="dc2dc-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="dc2dc-148">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="dc2dc-148">Next steps</span></span>

- <span data-ttu-id="dc2dc-149">En savoir plus sur les configurations DSC sous [Configurations DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="dc2dc-150">Consultez les ressources DSC disponibles et découvrez comment créer des ressources DSC personnalisées sous [Ressources DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="dc2dc-151">Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="dc2dc-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
