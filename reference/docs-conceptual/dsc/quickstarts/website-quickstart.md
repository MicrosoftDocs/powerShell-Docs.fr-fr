---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Démarrage rapide - Créer un site web avec DSC
description: Ce guide de démarrage rapide montre comment créer un nouveau site web à l’aide d’une configuration DSC.
ms.openlocfilehash: ece1ae964bce00a4102de4b13d99d6ee1259117a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650903"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a><span data-ttu-id="f9cde-104">Démarrage rapide : créer un site Web avec Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="f9cde-104">Quickstart - Create a website with Desired State Configuration (DSC)</span></span>

> <span data-ttu-id="f9cde-105">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f9cde-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f9cde-106">Cet exercice vous guide dans la création et l’application d’une configuration DSC (Configuration d’état souhaité) du début à la fin.</span><span class="sxs-lookup"><span data-stu-id="f9cde-106">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span> <span data-ttu-id="f9cde-107">L’exemple que nous utiliserons garantit qu’un serveur dispose de la fonctionnalité `Web-Server` (IIS) activée et que le contenu d’un site Web « Hello World » simple est présent dans le répertoire `inetpub\wwwroot` de ce serveur.</span><span class="sxs-lookup"><span data-stu-id="f9cde-107">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="f9cde-108">Pour une vue d’ensemble de DSC et de son fonctionnement, consultez [Présentation de la configuration de l’état souhaité pour les décideurs](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="f9cde-108">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="f9cde-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f9cde-109">Requirements</span></span>

<span data-ttu-id="f9cde-110">Pour exécuter cet exemple, vous avez besoin d’un ordinateur exécutant Windows Server 2012 ou une version ultérieure et PowerShell version 4.0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f9cde-110">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="f9cde-111">Écrire et placer le fichier index.htm</span><span class="sxs-lookup"><span data-stu-id="f9cde-111">Write and place the index.htm file</span></span>

<span data-ttu-id="f9cde-112">Tout d’abord, nous allons créer le fichier HTML qui va nous servir de contenu du site Web.</span><span class="sxs-lookup"><span data-stu-id="f9cde-112">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="f9cde-113">Dans votre dossier racine, créez un dossier nommé `test`.</span><span class="sxs-lookup"><span data-stu-id="f9cde-113">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="f9cde-114">Dans un éditeur de texte, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="f9cde-114">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="f9cde-115">Enregistrez-le en tant que `index.htm` dans le dossier `test` que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="f9cde-115">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="f9cde-116">Écrire la configuration</span><span class="sxs-lookup"><span data-stu-id="f9cde-116">Write the configuration</span></span>

<span data-ttu-id="f9cde-117">Une [configuration DSC](../configurations/configurations.md) est une fonction PowerShell spéciale qui définit la façon dont vous souhaitez configurer un ou plusieurs ordinateurs cibles (nœuds).</span><span class="sxs-lookup"><span data-stu-id="f9cde-117">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="f9cde-118">Dans l’ISE PowerShell, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f9cde-118">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="f9cde-119">Enregistrez le fichier sous le nom `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="f9cde-119">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="f9cde-120">Vous pouvez voir qu’il ressemble à une fonction PowerShell, avec l’ajout du mot clé **Configuration** utilisé avant le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="f9cde-120">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="f9cde-121">Le bloc **Nœud** spécifie le nœud cible à configurer.</span><span class="sxs-lookup"><span data-stu-id="f9cde-121">The **Node** block specifies the target node to be configured.</span></span> <span data-ttu-id="f9cde-122">Dans ce cas, `localhost`.</span><span class="sxs-lookup"><span data-stu-id="f9cde-122">In this case, `localhost`.</span></span>

<span data-ttu-id="f9cde-123">La configuration appelle deux [ressources](../resources/resources.md), **WindowsFeature** et **File**.</span><span class="sxs-lookup"><span data-stu-id="f9cde-123">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="f9cde-124">Les ressources s’assurent que le nœud cible est dans l’état défini par la configuration.</span><span class="sxs-lookup"><span data-stu-id="f9cde-124">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="f9cde-125">Compiler la configuration</span><span class="sxs-lookup"><span data-stu-id="f9cde-125">Compile the configuration</span></span>

<span data-ttu-id="f9cde-126">Pour qu’une configuration DSC soit appliquée à un nœud, elle doit tout d’abord être compilée dans un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="f9cde-126">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span> <span data-ttu-id="f9cde-127">Pour ce faire, vous exécutez la configuration comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="f9cde-127">To do this, you run the configuration like a function.</span></span> <span data-ttu-id="f9cde-128">Dans une console PowerShell, accédez au dossier où vous avez enregistré votre configuration et exécutez les commandes suivantes pour compiler la configuration dans un fichier MOF :</span><span class="sxs-lookup"><span data-stu-id="f9cde-128">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="f9cde-129">Cela génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f9cde-129">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="f9cde-130">La première ligne rend la fonction de configuration disponible dans la console.</span><span class="sxs-lookup"><span data-stu-id="f9cde-130">The first line makes the configuration function available in the console.</span></span> <span data-ttu-id="f9cde-131">La deuxième ligne exécute la configuration.</span><span class="sxs-lookup"><span data-stu-id="f9cde-131">The second line runs the configuration.</span></span> <span data-ttu-id="f9cde-132">Il en résulte qu’un nouveau dossier, nommé `WebsiteTest` est créé en tant que sous-dossier du dossier actif.</span><span class="sxs-lookup"><span data-stu-id="f9cde-132">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span> <span data-ttu-id="f9cde-133">Le dossier `WebsiteTest` contient un fichier nommé `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="f9cde-133">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span> <span data-ttu-id="f9cde-134">C’est ce fichier qui peut ensuite être appliqué au nœud cible.</span><span class="sxs-lookup"><span data-stu-id="f9cde-134">This is the file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="f9cde-135">Appliquer la configuration</span><span class="sxs-lookup"><span data-stu-id="f9cde-135">Apply the configuration</span></span>

<span data-ttu-id="f9cde-136">Maintenant que vous disposez du fichier MOF compilé, vous pouvez appliquer la configuration au nœud cible (dans ce cas, l’ordinateur local) en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="f9cde-136">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="f9cde-137">L’applet de commande `Start-DscConfiguration` indique au [LCM (Local Configuration Manager, gestionnaire de configuration local)](../managing-nodes/metaConfig.md), le moteur de DSC, d’appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="f9cde-137">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span> <span data-ttu-id="f9cde-138">Le LCM est chargé d’appeler les ressources DSC pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="f9cde-138">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f9cde-139">Pour permettre l’exécution de DSC, Windows doit être configuré pour recevoir des commandes à distance PowerShell, même lorsque vous exécutez une configuration `localhost`.</span><span class="sxs-lookup"><span data-stu-id="f9cde-139">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands, even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="f9cde-140">Pour configurer facilement et correctement votre environnement, exécutez simplement `Set-WsManQuickConfig -Force` dans un terminal PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="f9cde-140">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="f9cde-141">Dans une console PowerShell, accédez au dossier où vous avez enregistré votre configuration et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f9cde-141">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="f9cde-142">Tester la configuration</span><span class="sxs-lookup"><span data-stu-id="f9cde-142">Test the configuration</span></span>

<span data-ttu-id="f9cde-143">Vous pouvez appeler l’applet de commande [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) pour vérifier si la configuration a réussi.</span><span class="sxs-lookup"><span data-stu-id="f9cde-143">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="f9cde-144">Vous pouvez également tester les résultats directement, dans ce cas en accédant à `http://localhost/` dans un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="f9cde-144">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span> <span data-ttu-id="f9cde-145">Vous devez voir la page HTML « Hello World » que vous avez créée lors de la première étape dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="f9cde-145">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9cde-146">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f9cde-146">Next steps</span></span>

- <span data-ttu-id="f9cde-147">En savoir plus sur les configurations DSC sous [Configurations DSC](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="f9cde-147">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="f9cde-148">Consultez les ressources DSC disponibles et découvrez comment créer des ressources DSC personnalisées sous [Ressources DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="f9cde-148">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="f9cde-149">Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="f9cde-149">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
