---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuration d’état souhaité - Démarrage rapide
ms.openlocfilehash: eb7572f39f7a2710c82f132f42c3502b15c48d0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
> <span data-ttu-id="d48d8-103">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d48d8-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="desired-state-configuration-quick-start"></a><span data-ttu-id="d48d8-104">Configuration d’état souhaité - Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="d48d8-104">Desired State Configuration Quick Start</span></span>

<span data-ttu-id="d48d8-105">Cet exercice vous guide dans la création et l’application d’une configuration DSC (Configuration d’état souhaité) du début à la fin.</span><span class="sxs-lookup"><span data-stu-id="d48d8-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="d48d8-106">L’exemple que nous utiliserons garantit qu’un serveur dispose de la fonctionnalité `Web-Server` (IIS) activée et que le contenu d’un site Web « Hello World » simple est présent dans le répertoire `intepub\wwwroot` de ce serveur.</span><span class="sxs-lookup"><span data-stu-id="d48d8-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="d48d8-107">Pour une vue d’ensemble de DSC et de son fonctionnement, consultez [Présentation de la configuration de l’état souhaité pour les décideurs](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="d48d8-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="d48d8-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d48d8-108">Requirements</span></span>

<span data-ttu-id="d48d8-109">Pour exécuter cet exemple, vous avez besoin d’un ordinateur exécutant Windows Server 2012 ou une version ultérieure et PowerShell version 4.0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d48d8-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="d48d8-110">Écrire et placer le fichier index.htm</span><span class="sxs-lookup"><span data-stu-id="d48d8-110">Write and place the index.htm file</span></span>

<span data-ttu-id="d48d8-111">Tout d’abord, nous allons créer le fichier HTML qui va nous servir de contenu du site Web.</span><span class="sxs-lookup"><span data-stu-id="d48d8-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="d48d8-112">Dans votre dossier racine, créez un dossier nommé `test`.</span><span class="sxs-lookup"><span data-stu-id="d48d8-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="d48d8-113">Dans un éditeur de texte, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="d48d8-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="d48d8-114">Enregistrez-le en tant que `index.htm` dans le dossier `test` que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="d48d8-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="d48d8-115">Écrire la configuration</span><span class="sxs-lookup"><span data-stu-id="d48d8-115">Write the configuration</span></span>

<span data-ttu-id="d48d8-116">Une [configuration DSC](configurations.md) est une fonction PowerShell spéciale qui définit la façon dont vous souhaitez configurer un ou plusieurs ordinateurs cibles (nœuds).</span><span class="sxs-lookup"><span data-stu-id="d48d8-116">A [DSC configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="d48d8-117">Dans l’ISE PowerShell, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d48d8-117">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="d48d8-118">Enregistrez le fichier sous le nom `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="d48d8-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="d48d8-119">Vous pouvez voir qu’il ressemble à une fonction PowerShell, avec l’ajout du mot clé **Configuration** utilisé avant le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d48d8-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="d48d8-120">Le bloc **Nœud** spécifie le nœud cible à configurer, dans ce cas `localhost`.</span><span class="sxs-lookup"><span data-stu-id="d48d8-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="d48d8-121">La configuration appelle deux [ressources](resources.md), [WindowsFeature](windowsFeatureResource.md) et [File](fileResource.md).</span><span class="sxs-lookup"><span data-stu-id="d48d8-121">The configuration calls two [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) and [File](fileResource.md).</span></span>
<span data-ttu-id="d48d8-122">Les ressources s’assurent que le nœud cible est dans l’état défini par la configuration.</span><span class="sxs-lookup"><span data-stu-id="d48d8-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="d48d8-123">Compiler la configuration</span><span class="sxs-lookup"><span data-stu-id="d48d8-123">Compile the configuration</span></span>

<span data-ttu-id="d48d8-124">Pour qu’une configuration DSC soit appliquée à un nœud, elle doit tout d’abord être compilée dans un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="d48d8-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="d48d8-125">Pour ce faire, vous exécutez la configuration comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="d48d8-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="d48d8-126">Dans une console PowerShell, accédez au dossier où vous avez enregistré votre configuration et exécutez les commandes suivantes pour compiler la configuration dans un fichier MOF :</span><span class="sxs-lookup"><span data-stu-id="d48d8-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="d48d8-127">Cela génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d48d8-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="d48d8-128">La première ligne rend la fonction de configuration disponible dans la console.</span><span class="sxs-lookup"><span data-stu-id="d48d8-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="d48d8-129">La deuxième ligne exécute la configuration.</span><span class="sxs-lookup"><span data-stu-id="d48d8-129">The second line runs the configuration.</span></span>
<span data-ttu-id="d48d8-130">Il en résulte qu’un nouveau dossier, nommé `WebsiteTest` est créé en tant que sous-dossier du dossier actif.</span><span class="sxs-lookup"><span data-stu-id="d48d8-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="d48d8-131">Le dossier `WebsiteTest` contient un fichier nommé `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="d48d8-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="d48d8-132">C’est ce fichier qui peut ensuite être appliqué au nœud cible.</span><span class="sxs-lookup"><span data-stu-id="d48d8-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="d48d8-133">Appliquer la configuration</span><span class="sxs-lookup"><span data-stu-id="d48d8-133">Apply the configuration</span></span>

<span data-ttu-id="d48d8-134">Maintenant que vous disposez du fichier MOF compilé, vous pouvez appliquer la configuration au nœud cible (dans ce cas, l’ordinateur local) en appelant l’applet de commande [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="d48d8-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

<span data-ttu-id="d48d8-135">L’applet de commande `Start-DscConfiguration` indique au [LCM (Local Configuration Manager, gestionnaire de configuration local)](metaConfig.md), le moteur de DSC, d’appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="d48d8-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="d48d8-136">Le LCM est chargé d’appeler les ressources DSC pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="d48d8-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="d48d8-137">Dans une console PowerShell, accédez au dossier où vous avez enregistré votre configuration et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d48d8-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="d48d8-138">Tester la configuration</span><span class="sxs-lookup"><span data-stu-id="d48d8-138">Test the configuration</span></span>

<span data-ttu-id="d48d8-139">Vous pouvez appeler l’applet de commande [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) pour vérifier si la configuration a réussi.</span><span class="sxs-lookup"><span data-stu-id="d48d8-139">You can call the [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="d48d8-140">Vous pouvez également tester les résultats directement, dans ce cas en accédant à `http://localhost/` dans un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="d48d8-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="d48d8-141">Vous devez voir la page HTML « Hello World » que vous avez créée lors de la première étape dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d48d8-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d48d8-142">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d48d8-142">Next steps</span></span>

- <span data-ttu-id="d48d8-143">En savoir plus sur les configurations DSC sous [Configurations DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="d48d8-143">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="d48d8-144">Consultez les ressources DSC disponibles et découvrez comment créer des ressources DSC personnalisées sous [Ressources DSC](resources.md).</span><span class="sxs-lookup"><span data-stu-id="d48d8-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](resources.md).</span></span>
- <span data-ttu-id="d48d8-145">Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="d48d8-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>