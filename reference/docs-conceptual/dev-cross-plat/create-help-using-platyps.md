---
title: Créer une aide XML à l’aide de PlatyPS
description: Utiliser PlatyPS est la méthode rapide et efficace pour créer une aide XML.
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972573"
---
# <a name="create-xml-based-help-using-platyps"></a><span data-ttu-id="79329-103">Créer une aide XML à l’aide de PlatyPS</span><span class="sxs-lookup"><span data-stu-id="79329-103">Create XML-based help using PlatyPS</span></span>

<span data-ttu-id="79329-104">Quand vous créez un module PowerShell, il est toujours recommandé d’inclure une aide détaillée sur les applets de commande que vous créez.</span><span class="sxs-lookup"><span data-stu-id="79329-104">When creating a PowerShell module, it is always recommended that you include detailed help for the cmdlets you create.</span></span> <span data-ttu-id="79329-105">Si vos applets de commande sont implémentées dans du code compilé, vous devez utiliser l’aide XML.</span><span class="sxs-lookup"><span data-stu-id="79329-105">If your cmdlets are implemented in compiled code, you must use the XML-based help.</span></span> <span data-ttu-id="79329-106">Ce format XML est connu sous le nom de MAML (Microsoft Assistance Markup Language).</span><span class="sxs-lookup"><span data-stu-id="79329-106">This XML format is known as the Microsoft Assistance Markup Language (MAML).</span></span>

<span data-ttu-id="79329-107">La documentation du SDK PowerShell hérité décrit en détail la création d’une aide pour des applets de commande PowerShell empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="79329-107">The legacy PowerShell SDK documentation covers the details of creating help for PowerShell cmdlets packaged into modules.</span></span> <span data-ttu-id="79329-108">En revanche, PowerShell ne fournit pas d’outils pour créer cette aide XML.</span><span class="sxs-lookup"><span data-stu-id="79329-108">However, PowerShell does not provide any tools for creating the XML-based help.</span></span> <span data-ttu-id="79329-109">La documentation du SDK explique la structure de l’aide MAML, mais vous laisse la tâche de créer manuellement le contenu MAML complexe et profondément imbriqué.</span><span class="sxs-lookup"><span data-stu-id="79329-109">The SDK documentation explains the structure of MAML help, but leaves you the task of creating the complex, and deeply nested, MAML content by hand.</span></span>

<span data-ttu-id="79329-110">C’est là que le module [PlatyPS][] peut vous aider.</span><span class="sxs-lookup"><span data-stu-id="79329-110">This is where the [PlatyPS][] module can help.</span></span>

## <a name="what-is-platyps"></a><span data-ttu-id="79329-111">Qu’est-ce que PlatyPS ?</span><span class="sxs-lookup"><span data-stu-id="79329-111">What is PlatyPS?</span></span>

<span data-ttu-id="79329-112">PlatyPS est un outil [open source][platyps-repo] qui a démarré sous la forme d’un projet _hackathon_ visant à faciliter la création et la maintenance de MAML.</span><span class="sxs-lookup"><span data-stu-id="79329-112">PlatyPS is an [open-source][platyps-repo] tool that started as a _hackathon_ project to make the creation and maintenance of MAML easier.</span></span> <span data-ttu-id="79329-113">PlatyPS documente la syntaxe des jeux de paramètres et les paramètres individuels de chaque applet de commande incluse dans votre module.</span><span class="sxs-lookup"><span data-stu-id="79329-113">PlatyPS documents the syntax of parameter sets and the individual parameters for each cmdlet in your module.</span></span> <span data-ttu-id="79329-114">PlatyPS crée des fichiers [Markdown][] structurés qui contiennent les informations sur la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="79329-114">PlatyPS creates structured [Markdown][] files that contain the syntax information.</span></span> <span data-ttu-id="79329-115">Il ne permet pas de créer des descriptions ni de fournir des exemples.</span><span class="sxs-lookup"><span data-stu-id="79329-115">It can't create descriptions or provide examples.</span></span>

<span data-ttu-id="79329-116">PlatyPS crée des espaces réservés pour vous permettre de renseigner des descriptions et des exemples.</span><span class="sxs-lookup"><span data-stu-id="79329-116">PlatyPS creates placeholders for you to fill in descriptions and examples.</span></span> <span data-ttu-id="79329-117">Après avoir ajouté les informations nécessaires, PlatyPS compile les fichiers Markdown dans des fichiers MAML.</span><span class="sxs-lookup"><span data-stu-id="79329-117">After adding the required information, PlatyPS compiles the Markdown files into MAML files.</span></span> <span data-ttu-id="79329-118">Le système d’aide de PowerShell autorise aussi les fichiers d’aide conceptuelle en texte brut (rubriques À propos de).</span><span class="sxs-lookup"><span data-stu-id="79329-118">PowerShell's help system also allows for plain-text conceptual help files (about topics).</span></span> <span data-ttu-id="79329-119">PlatyPS dispose d’une applet de commande pour créer un modèle Markdown structuré pour un nouveau fichier _À propos de_, mais ces fichiers `about_*.help.txt` doivent être gérés manuellement.</span><span class="sxs-lookup"><span data-stu-id="79329-119">PlatyPS has a cmdlet to create a structured Markdown template for a new _about_ file, but these `about_*.help.txt` files must be maintained manually.</span></span>

<span data-ttu-id="79329-120">Vous pouvez inclure les fichiers d’aide MAML et texte dans votre module.</span><span class="sxs-lookup"><span data-stu-id="79329-120">You can include the MAML and Text help files with your module.</span></span> <span data-ttu-id="79329-121">Vous pouvez également utiliser PlatyPS pour compiler les fichiers d’aide dans un package CAB que vous pouvez héberger pour une aide modifiable.</span><span class="sxs-lookup"><span data-stu-id="79329-121">You can also use PlatyPS to compile the help files into a CAB package that can be hosted for updateable help.</span></span>

## <a name="get-started-using-platyps"></a><span data-ttu-id="79329-122">Démarrer avec PlatyPS</span><span class="sxs-lookup"><span data-stu-id="79329-122">Get started using PlatyPS</span></span>

<span data-ttu-id="79329-123">Tout d’abord, vous devez installer PlatyPS à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="79329-123">First you must install PlatyPS from the PowerShell Gallery.</span></span>

```powershell
Install-Module platyps -Force
Import-Module platyps
```

<span data-ttu-id="79329-124">L’organigramme suivant décrit le processus de création ou de mise à jour du contenu de référence PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79329-124">The following flowchart outlines the process for creating or updating PowerShell reference content.</span></span>

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="Workflow de la création d’une aide XML à l’aide de PlatyPS":::

##  <a name="create-markdown-content-for-a-powershell-module"></a><span data-ttu-id="79329-126">Créer du contenu Markdown pour un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="79329-126">Create Markdown content for a PowerShell module</span></span>

1. <span data-ttu-id="79329-127">Importez votre nouveau module dans la session.</span><span class="sxs-lookup"><span data-stu-id="79329-127">Import your new module into the session.</span></span> <span data-ttu-id="79329-128">Répétez cette étape pour chaque module à documenter.</span><span class="sxs-lookup"><span data-stu-id="79329-128">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="79329-129">Exécutez la commande suivante pour importer vos modules :</span><span class="sxs-lookup"><span data-stu-id="79329-129">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="79329-130">Utilisez PlatyPS pour générer des fichiers Markdown pour votre page de module et toutes les applets de commande associées dans le module.</span><span class="sxs-lookup"><span data-stu-id="79329-130">Use PlatyPS to generate Markdown files for your module page and all associated cmdlets within the module.</span></span> <span data-ttu-id="79329-131">Répétez cette étape pour chaque module à documenter.</span><span class="sxs-lookup"><span data-stu-id="79329-131">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   <span data-ttu-id="79329-132">Si le dossier de sortie n’existe pas, `New-MarkdownHelp` le crée.</span><span class="sxs-lookup"><span data-stu-id="79329-132">If the output folder does not exist, `New-MarkdownHelp` creates it.</span></span> <span data-ttu-id="79329-133">Dans cet exemple, `New-MarkdownHelp` crée un fichier Markdown pour chaque applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="79329-133">In this example, `New-MarkdownHelp` creates a Markdown file for each cmdlet in the module.</span></span> <span data-ttu-id="79329-134">La _page de module_ est également créée dans un fichier nommé `<ModuleName>.md`.</span><span class="sxs-lookup"><span data-stu-id="79329-134">It also creates the _module page_ in a file named `<ModuleName>.md`.</span></span> <span data-ttu-id="79329-135">Cette page de module contient la liste des applets de commande contenues dans le module et des espaces réservés pour la description de **Synopsis**.</span><span class="sxs-lookup"><span data-stu-id="79329-135">This module page contains a list of the cmdlets contained in the module and placeholders for the **Synopsis** description.</span></span> <span data-ttu-id="79329-136">Les métadonnées de la page de module proviennent du manifeste du module. PlatyPS les utilise pour créer le fichier XML HelpInfo (comme expliqué [ci-dessous](#creating-an-updateable-help-package)).</span><span class="sxs-lookup"><span data-stu-id="79329-136">The metadata in the module page comes from the module manifest and is used by PlatyPS to create the HelpInfo XML file (as explained [below](#creating-an-updateable-help-package)).</span></span>

   <span data-ttu-id="79329-137">`New-MarkdownAboutHelp` crée un fichier _about_ nommé `about_topic_name.md`.</span><span class="sxs-lookup"><span data-stu-id="79329-137">`New-MarkdownAboutHelp` creates a new _about_ file named `about_topic_name.md`.</span></span>

   <span data-ttu-id="79329-138">Pour plus d’informations, consultez [New-MarkdownHelp][] et [New-MarkdownAboutHelp][].</span><span class="sxs-lookup"><span data-stu-id="79329-138">For more information, see [New-MarkdownHelp][] and [New-MarkdownAboutHelp][].</span></span>

### <a name="update-existing-markdown-content-when-the-module-changes"></a><span data-ttu-id="79329-139">Mettre à jour le contenu Markdown existant quand le module change</span><span class="sxs-lookup"><span data-stu-id="79329-139">Update existing Markdown content when the module changes</span></span>

<span data-ttu-id="79329-140">PlatyPS peut également mettre à jour les fichiers Markdown existants pour un module.</span><span class="sxs-lookup"><span data-stu-id="79329-140">PlatyPS can also update existing Markdown files for a module.</span></span> <span data-ttu-id="79329-141">Utilisez cette étape pour mettre à jour des modules existants qui incluent de nouvelles applets de commande, de nouveaux paramètres ou des paramètres modifiés.</span><span class="sxs-lookup"><span data-stu-id="79329-141">Use this step to update existing modules that have new cmdlets, new parameters, or parameters that have changed.</span></span>

1. <span data-ttu-id="79329-142">Importez votre nouveau module dans la session.</span><span class="sxs-lookup"><span data-stu-id="79329-142">Import your new module into the session.</span></span> <span data-ttu-id="79329-143">Répétez cette étape pour chaque module à documenter.</span><span class="sxs-lookup"><span data-stu-id="79329-143">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="79329-144">Exécutez la commande suivante pour importer vos modules :</span><span class="sxs-lookup"><span data-stu-id="79329-144">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="79329-145">Utilisez PlatyPS pour mettre à jour les fichiers Markdown de la page d’arrivée de votre module et toutes les applets de commande associées dans le module.</span><span class="sxs-lookup"><span data-stu-id="79329-145">Use PlatyPS to update Markdown files for your module landing page and all associated cmdlets within the module.</span></span> <span data-ttu-id="79329-146">Répétez cette étape pour chaque module à documenter.</span><span class="sxs-lookup"><span data-stu-id="79329-146">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   <span data-ttu-id="79329-147">`Update-MarkdownHelpModule` met à jour l’applet de commande et les fichiers Markdown du module dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="79329-147">`Update-MarkdownHelpModule` updates the cmdlet and module Markdown files in the specified folder.</span></span>
   <span data-ttu-id="79329-148">Cette commande ne met pas à jour les fichiers `about_*.md`.</span><span class="sxs-lookup"><span data-stu-id="79329-148">It does not update the `about_*.md` files.</span></span> <span data-ttu-id="79329-149">Le fichier du module (`ModuleName.md`) reçoit tout nouveau texte **Synopsis** ajouté aux fichiers d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="79329-149">The module file (`ModuleName.md`) receives any new **Synopsis** text that has been added to the cmdlet files.</span></span> <span data-ttu-id="79329-150">Les mises à jour apportées aux fichiers d’applet de commande incluent les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="79329-150">Updates to cmdlet files include the following change:</span></span>

   - <span data-ttu-id="79329-151">Nouveaux jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="79329-151">New parameter sets</span></span>
   - <span data-ttu-id="79329-152">Nouveaux paramètres</span><span class="sxs-lookup"><span data-stu-id="79329-152">New parameters</span></span>
   - <span data-ttu-id="79329-153">Métadonnées de paramètre mises à jour</span><span class="sxs-lookup"><span data-stu-id="79329-153">Updated parameter metadata</span></span>
   - <span data-ttu-id="79329-154">Informations de type d’entrée et de sortie mises à jour</span><span class="sxs-lookup"><span data-stu-id="79329-154">Updated input and output type information</span></span>

   <span data-ttu-id="79329-155">Pour plus d’informations, consultez [Update-MarkdownHelpModule][].</span><span class="sxs-lookup"><span data-stu-id="79329-155">For more information, see [Update-MarkdownHelpModule][].</span></span>

## <a name="edit-the-new-or-updated-markdown-files"></a><span data-ttu-id="79329-156">Modifier les fichiers Markdown nouveaux ou mis à jour</span><span class="sxs-lookup"><span data-stu-id="79329-156">Edit the new or updated Markdown files</span></span>

<span data-ttu-id="79329-157">PlatyPS documente la syntaxe des jeux de paramètres et les paramètres individuels.</span><span class="sxs-lookup"><span data-stu-id="79329-157">PlatyPS documents the syntax of the parameter sets and the individual parameters.</span></span> <span data-ttu-id="79329-158">L’outil ne permet pas de créer des descriptions ni de fournir des exemples.</span><span class="sxs-lookup"><span data-stu-id="79329-158">It can't create descriptions or provide examples.</span></span> <span data-ttu-id="79329-159">Les zones spécifiques dans lesquelles du contenu est nécessaire sont indiquées entre accolades.</span><span class="sxs-lookup"><span data-stu-id="79329-159">The specific areas where content is needed are contained in curly braces.</span></span> <span data-ttu-id="79329-160">Par exemple : `{{ Fill in the Description }}`</span><span class="sxs-lookup"><span data-stu-id="79329-160">For example: `{{ Fill in the Description }}`</span></span>

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="Modèle Markdown présentant des espaces réservés dans VS Code":::

<span data-ttu-id="79329-162">Vous avez besoin d’ajouter un synopsis, une description de l’applet de commande, des descriptions pour chaque paramètre et au moins un exemple.</span><span class="sxs-lookup"><span data-stu-id="79329-162">You need to add a synopsis, a description of the cmdlet, descriptions for each parameter, and at least one example.</span></span>

<span data-ttu-id="79329-163">Pour plus d’informations sur l’écriture de contenu PowerShell, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="79329-163">For detailed information about writing PowerShell content, see the following articles:</span></span>

- [<span data-ttu-id="79329-164">Guide de style PowerShell</span><span class="sxs-lookup"><span data-stu-id="79329-164">PowerShell style guide</span></span>](/powershell/scripting/community/contributing/powershell-style-guide)
- [<span data-ttu-id="79329-165">Modification des articles de référence</span><span class="sxs-lookup"><span data-stu-id="79329-165">Editing reference articles</span></span>](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> <span data-ttu-id="79329-166">PlatyPS inclut un schéma spécifique utilisé pour les informations de référence des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="79329-166">PlatyPS has a specific schema that is uses for cmdlet reference.</span></span> <span data-ttu-id="79329-167">Ce schéma autorise uniquement certains blocs Markdown dans des sections spécifiques du document.</span><span class="sxs-lookup"><span data-stu-id="79329-167">That schema only allows certain Markdown blocks in specific sections of the document.</span></span> <span data-ttu-id="79329-168">Si vous placez du contenu au mauvais endroit, l’étape de génération PlatyPS échoue.</span><span class="sxs-lookup"><span data-stu-id="79329-168">If you put content in the wrong location, the PlatyPS build step fails.</span></span> <span data-ttu-id="79329-169">Pour plus d’informations, consultez la documentation sur le [schéma][] dans le référentiel PlatyPS.</span><span class="sxs-lookup"><span data-stu-id="79329-169">For more information, see the [schema][] documentation in the PlatyPS repository.</span></span> <span data-ttu-id="79329-170">Pour obtenir un exemple complet d’informations de référence sur une applet de commande bien formée, consultez [Get-Item][].</span><span class="sxs-lookup"><span data-stu-id="79329-170">For a complete example of well-formed cmdlet reference, see [Get-Item][].</span></span>

<span data-ttu-id="79329-171">Une fois que vous avez fourni le contenu nécessaire pour chacune de vos applets de commande, vous devez veiller à mettre à jour la page d’arrivée du module.</span><span class="sxs-lookup"><span data-stu-id="79329-171">After providing the required content for each of your cmdlets, you need to make sure that you update the module landing page.</span></span> <span data-ttu-id="79329-172">Vérifiez que votre module a les valeurs `Module Guid` et `Download Help Link` appropriées dans les métadonnées YAML du fichier `<module-name>.md`.</span><span class="sxs-lookup"><span data-stu-id="79329-172">Verify your module has the correct `Module Guid` and `Download Help Link` values in the YAML metadata of the `<module-name>.md` file.</span></span> <span data-ttu-id="79329-173">Ajoutez toutes les métadonnées manquantes.</span><span class="sxs-lookup"><span data-stu-id="79329-173">Add any missing metadata.</span></span>

<span data-ttu-id="79329-174">De plus, vous pouvez remarquer que certaines applets de commande n’ont pas de **Synopsis** (_description brève_).</span><span class="sxs-lookup"><span data-stu-id="79329-174">Also, you may notice that some cmdlets may be missing a **Synopsis** (_short description_).</span></span> <span data-ttu-id="79329-175">La commande suivante met à jour la page d’arrivée du module avec votre texte de description **Synopsis**.</span><span class="sxs-lookup"><span data-stu-id="79329-175">The following command updates the module landing page with your **Synopsis** description text.</span></span> <span data-ttu-id="79329-176">Ouvrez la page d’arrivée du module pour vérifier les descriptions.</span><span class="sxs-lookup"><span data-stu-id="79329-176">Open the module landing page to verify the descriptions.</span></span>

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

<span data-ttu-id="79329-177">Maintenant que vous avez entré tout le contenu, vous pouvez créer les fichiers d’aide MAML que `Get-Help` va permettre d’afficher dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79329-177">Now that you have entered all the content, you can create the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

## <a name="create-the-external-help-files"></a><span data-ttu-id="79329-178">Créer les fichiers d’aide externes</span><span class="sxs-lookup"><span data-stu-id="79329-178">Create the external help files</span></span>

<span data-ttu-id="79329-179">Cette étape crée les fichiers d’aide MAML affichés par `Get-Help` dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79329-179">This step creates the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

<span data-ttu-id="79329-180">Pour générer les fichiers MAML, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="79329-180">To build the MAML files, run the following command:</span></span>

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

<span data-ttu-id="79329-181">`New-ExternalHelp` convertit tous les fichiers Markdown d’applet de commande en un ou plusieurs fichiers MAML.</span><span class="sxs-lookup"><span data-stu-id="79329-181">`New-ExternalHelp` converts all of the cmdlet Markdown files into one (or more) MAML files.</span></span> <span data-ttu-id="79329-182">Les fichiers À propos de sont convertis en fichiers texte brut avec le format de nom suivant : `about_topic_name.help.txt`.</span><span class="sxs-lookup"><span data-stu-id="79329-182">About files are converted to plain-text files with the following name format: `about_topic_name.help.txt`.</span></span>
<span data-ttu-id="79329-183">Le contenu Markdown doit satisfaire aux exigences du schéma PlatyPS.</span><span class="sxs-lookup"><span data-stu-id="79329-183">The Markdown content must meet the requirement of the PlatyPS schema.</span></span> <span data-ttu-id="79329-184">`New-ExternalHelp` se termine avec des erreurs quand le contenu ne suit pas le schéma.</span><span class="sxs-lookup"><span data-stu-id="79329-184">`New-ExternalHelp` will exits with errors when the content does not follow the schema.</span></span> <span data-ttu-id="79329-185">Vous devez modifier les fichiers pour corriger les violations de schéma.</span><span class="sxs-lookup"><span data-stu-id="79329-185">You must edit the files to fix the schema violations.</span></span>

> [!CAUTION]
> <span data-ttu-id="79329-186">PlatyPS ne parvient pas à convertir correctement les fichiers `about_*.md` en texte brut.</span><span class="sxs-lookup"><span data-stu-id="79329-186">PlatyPS does a poor job converting the `about_*.md` files to plain text.</span></span> <span data-ttu-id="79329-187">Pour obtenir des résultats acceptables, vous devez utiliser un langage Markdown très simple.</span><span class="sxs-lookup"><span data-stu-id="79329-187">You must use very simple Markdown to get acceptable results.</span></span> <span data-ttu-id="79329-188">Envisagez éventuellement de garder les fichiers au format texte brut `about_topic_name.help.txt`, plutôt que d’autoriser PlatyPS à les convertir.</span><span class="sxs-lookup"><span data-stu-id="79329-188">You may want to maintain the files in plain-text `about_topic_name.help.txt` format, rather than allowing PlatyPS to convert them.</span></span>

<span data-ttu-id="79329-189">Une fois cette étape terminée, les fichiers `*-help.xml` et `about_*.help.txt` apparaissent dans le dossier de sortie cible.</span><span class="sxs-lookup"><span data-stu-id="79329-189">Once this step is complete, you will see `*-help.xml` and `about_*.help.txt` files in the target output folder.</span></span>

<span data-ttu-id="79329-190">Pour plus d’informations, consultez [New-ExternalHelp][].</span><span class="sxs-lookup"><span data-stu-id="79329-190">For more information, see [New-ExternalHelp][]</span></span>

### <a name="test-the-compiled-help-files"></a><span data-ttu-id="79329-191">Tester les fichiers d’aide compilés</span><span class="sxs-lookup"><span data-stu-id="79329-191">Test the compiled help files</span></span>

<span data-ttu-id="79329-192">Vous pouvez vérifier le contenu à l’aide de l’applet de commande [Get-HelpPreview][] :</span><span class="sxs-lookup"><span data-stu-id="79329-192">You can verify the content with the [Get-HelpPreview][] cmdlet:</span></span>

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

<span data-ttu-id="79329-193">L’applet de commande lit le fichier MAML compilé et génère le contenu dans le même format que celui que vous recevez de `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="79329-193">The cmdlet reads the compiled MAML file and outputs the content in the same format you would receive from `Get-Help`.</span></span> <span data-ttu-id="79329-194">Ainsi, vous pouvez inspecter les résultats pour vérifier que les fichiers Markdown ont été compilés correctement et qu’ils produisent les résultats voulus.</span><span class="sxs-lookup"><span data-stu-id="79329-194">This allows you to inspect the results to verify that the Markdown files compiled correctly and produce the desired results.</span></span> <span data-ttu-id="79329-195">Si vous trouvez une erreur, remodifiez les fichiers Markdown et recompilez le MAML.</span><span class="sxs-lookup"><span data-stu-id="79329-195">If you find an error, re-edit the Markdown files and recompile the MAML.</span></span>

<span data-ttu-id="79329-196">Vous pouvez à présent publier vos fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="79329-196">Now you are ready to publish your help files.</span></span>

## <a name="publishing-your-help"></a><span data-ttu-id="79329-197">Publication de votre aide</span><span class="sxs-lookup"><span data-stu-id="79329-197">Publishing your help</span></span>

<span data-ttu-id="79329-198">Maintenant que vous avez compilé les fichiers Markdown dans des fichiers d’aide PowerShell, vous êtes prêt à les mettre à la disposition des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="79329-198">Now that you have compiled the Markdown files into PowerShell help files, you are ready to make the files available to users.</span></span> <span data-ttu-id="79329-199">Deux possibilités s’offrent à vous pour fournir de l’aide dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79329-199">There are two options for providing help in the PowerShell console.</span></span>

- <span data-ttu-id="79329-200">Empaqueter les fichiers d’aide avec le module</span><span class="sxs-lookup"><span data-stu-id="79329-200">Package the help files with the module</span></span>
- <span data-ttu-id="79329-201">Créer un package d’aide modifiable que les utilisateurs installent avec l’applet de commande `Update-Help`</span><span class="sxs-lookup"><span data-stu-id="79329-201">Create an updateable help package that users install with the `Update-Help` cmdlet</span></span>

### <a name="packaging-help-with-the-module"></a><span data-ttu-id="79329-202">Empaquetage de l’aide avec le module</span><span class="sxs-lookup"><span data-stu-id="79329-202">Packaging help with the module</span></span>

<span data-ttu-id="79329-203">Les fichiers d’aide peuvent être empaquetés avec votre module.</span><span class="sxs-lookup"><span data-stu-id="79329-203">The help files can be packaged with your module.</span></span> <span data-ttu-id="79329-204">Pour plus d’informations sur la structure des dossiers, consultez [Écriture d’aide pour les modules][].</span><span class="sxs-lookup"><span data-stu-id="79329-204">See [Writing Help for Modules][] for details of the folder structure.</span></span> <span data-ttu-id="79329-205">Vous devez inclure la liste des fichiers d’aide dans la valeur de la clé **FileList** qui se trouve dans le manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="79329-205">You should include the list of Help files in the value of the **FileList** key in the module manifest.</span></span>

### <a name="creating-an-updateable-help-package"></a><span data-ttu-id="79329-206">Création d’un package d’aide modifiable</span><span class="sxs-lookup"><span data-stu-id="79329-206">Creating an updateable help package</span></span>

<span data-ttu-id="79329-207">En règle générale, les étapes permettant de créer une aide modifiable sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="79329-207">At a high level, the steps to create updateable help include:</span></span>

1. <span data-ttu-id="79329-208">Trouver un site Internet pour héberger vos fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="79329-208">Find an internet site to host your help files</span></span>
1. <span data-ttu-id="79329-209">Ajouter une clé **HelpInfoURI** au manifeste de votre module</span><span class="sxs-lookup"><span data-stu-id="79329-209">Add a **HelpInfoURI** key to your module manifest</span></span>
1. <span data-ttu-id="79329-210">Créer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="79329-210">Create a HelpInfo XML file</span></span>
1. <span data-ttu-id="79329-211">Créer des fichiers CAB</span><span class="sxs-lookup"><span data-stu-id="79329-211">Create CAB files</span></span>
1. <span data-ttu-id="79329-212">Charger vos fichiers</span><span class="sxs-lookup"><span data-stu-id="79329-212">Upload your files</span></span>

<span data-ttu-id="79329-213">Pour plus d’informations, consultez [Prise en charge de l’aide modifiable : procédure pas à pas][step-by-step].</span><span class="sxs-lookup"><span data-stu-id="79329-213">For more information, see [Supporting Updateable Help: Step-by-step][step-by-step].</span></span>

<span data-ttu-id="79329-214">PlatyPS vous accompagne tout au long d’une partie de ces étapes.</span><span class="sxs-lookup"><span data-stu-id="79329-214">PlatyPS assists you with  some of these steps.</span></span>

<span data-ttu-id="79329-215">**HelpInfoURI** correspond à une URL qui pointe vers l’emplacement où vos fichiers d’aide sont hébergés sur Internet.</span><span class="sxs-lookup"><span data-stu-id="79329-215">The **HelpInfoURI** is a URL that points to location where your help files are hosted on the internet.</span></span> <span data-ttu-id="79329-216">Cette valeur est configurée dans le manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="79329-216">This value is configured in the module manifest.</span></span> <span data-ttu-id="79329-217">`Update-Help` lit le manifeste du module pour obtenir cette URL et télécharger le contenu de l’aide modifiable.</span><span class="sxs-lookup"><span data-stu-id="79329-217">`Update-Help` reads the module manifest to get this URL and download the updateable help content.</span></span> <span data-ttu-id="79329-218">Cette URL doit uniquement pointer vers l’emplacement du dossier et non celui de fichiers individuels.</span><span class="sxs-lookup"><span data-stu-id="79329-218">This URL should only point to the folder location and not to individual files.</span></span> <span data-ttu-id="79329-219">`Update-Help` construit les noms de fichiers à télécharger en fonction d’autres informations issues du manifeste du module et du fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="79329-219">`Update-Help` constructs the filenames to download based on other information from the module manifest and the HelpInfo XML file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79329-220">**HelpInfoURI** doit se terminer par une barre oblique (`/`).</span><span class="sxs-lookup"><span data-stu-id="79329-220">The **HelpInfoURI** must end with a forward-slash character (`/`).</span></span> <span data-ttu-id="79329-221">Sans ce caractère, `Update-Help` ne peut pas construire les chemins de fichier corrects pour télécharger le contenu.</span><span class="sxs-lookup"><span data-stu-id="79329-221">Without that character, `Update-Help` cannot construct the correct file paths to download the content.</span></span> <span data-ttu-id="79329-222">De plus, la plupart des services de fichiers HTTP sont sensibles à la casse.</span><span class="sxs-lookup"><span data-stu-id="79329-222">Also, most HTTP-based file services are case-sensitive.</span></span> <span data-ttu-id="79329-223">Il est important que les métadonnées du module dans le fichier XML HelpInfo contiennent la bonne casse.</span><span class="sxs-lookup"><span data-stu-id="79329-223">It is important that the module metadata in the HelpInfo XML file contains the proper letter case.</span></span>

<span data-ttu-id="79329-224">L’applet de commande `New-ExternalHelp` crée le fichier XML HelpInfo dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="79329-224">The `New-ExternalHelp` cmdlet creates the HelpInfo XML file in the output folder.</span></span> <span data-ttu-id="79329-225">Le fichier XML HelpInfo est généré à l’aide des métadonnées YAML contenues dans les fichiers Markdown du module (`ModuleName.md`).</span><span class="sxs-lookup"><span data-stu-id="79329-225">The HelpInfo XML file is built using YAML metadata contained in the module Markdown files (`ModuleName.md`).</span></span>

<span data-ttu-id="79329-226">L’applet de commande `New-ExternalHelpCab` crée des fichiers ZIP et CAB qui contiennent les fichiers MAML et `about_*.help.txt` que vous avez compilés.</span><span class="sxs-lookup"><span data-stu-id="79329-226">The `New-ExternalHelpCab` cmdlet creates ZIP and CAB files containing the MAML and `about_*.help.txt` files you compiled.</span></span> <span data-ttu-id="79329-227">Les fichiers CAB sont compatibles avec toutes les versions de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79329-227">CAB files are compatible with all versions of PowerShell.</span></span>
<span data-ttu-id="79329-228">PowerShell 6 et ses versions ultérieures peuvent utiliser des fichiers ZIP.</span><span class="sxs-lookup"><span data-stu-id="79329-228">PowerShell 6 and higher can use ZIP files.</span></span>

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

<span data-ttu-id="79329-229">Après avoir créé les fichiers ZIP et CAB, chargez les fichiers ZIP, CAB et XML HelpInfo sur votre serveur de fichiers HTTP.</span><span class="sxs-lookup"><span data-stu-id="79329-229">After creating the ZIP and CAB files, upload the ZIP, CAB, and HelpInfo XML files to your HTTP file server.</span></span> <span data-ttu-id="79329-230">Placez les fichiers à l’emplacement indiqué par **HelpInfoURI**.</span><span class="sxs-lookup"><span data-stu-id="79329-230">Put the files in the location indicated by the **HelpInfoURI**.</span></span>

<span data-ttu-id="79329-231">Pour plus d’informations, consultez [New-ExternalHelpCab][].</span><span class="sxs-lookup"><span data-stu-id="79329-231">For more information, see [New-ExternalHelpCab][].</span></span>

### <a name="other-publishing-options"></a><span data-ttu-id="79329-232">Autres options de publication</span><span class="sxs-lookup"><span data-stu-id="79329-232">Other publishing options</span></span>

<span data-ttu-id="79329-233">Markdown est un format polyvalent facile à transformer en d’autres formats à des fins de publication.</span><span class="sxs-lookup"><span data-stu-id="79329-233">Markdown is a versatile format that is easy to transform to other formats for publishing.</span></span> <span data-ttu-id="79329-234">À l’aide d’un outil comme [Pandoc][], vous pouvez convertir vos fichiers d’aide Markdown en de nombreux autres formats de document, notamment les formats texte brut, HTML, PDF et Office.</span><span class="sxs-lookup"><span data-stu-id="79329-234">Using a tool like [Pandoc][], you can convert your Markdown help files to many different document formats, including plain text, HTML, PDF, and Office document formats.</span></span>

<span data-ttu-id="79329-235">De plus, les applets de commande [ConvertFrom-Markdown][] et [Show-Markdown][] dans PowerShell 6 et ses versions ultérieures peuvent être utilisées pour convertir le format Markdown au format HTML ou créer un affichage en couleurs dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79329-235">Also, the cmdlets [ConvertFrom-Markdown][] and [Show-Markdown][] in PowerShell 6 and higher can be used to convert Markdown to HTML or create a colorful display in the PowerShell console.</span></span>

## <a name="known-issues"></a><span data-ttu-id="79329-236">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="79329-236">Known issues</span></span>

<span data-ttu-id="79329-237">PlatyPS est très sensible au [schéma][] pour la structure des fichiers Markdown qu’il crée et compile.</span><span class="sxs-lookup"><span data-stu-id="79329-237">PlatyPS is very sensitive to the [schema][] for the structure of the Markdown files it creates and compiles.</span></span> <span data-ttu-id="79329-238">Il est très facile d’écrire du langage Markdown valide qui enfreint ce schéma.</span><span class="sxs-lookup"><span data-stu-id="79329-238">It is very easy write valid Markdown that violates this schema.</span></span> <span data-ttu-id="79329-239">Pour plus d’informations, consultez [Guide de style PowerShell][] et [Modification des articles de référence][].</span><span class="sxs-lookup"><span data-stu-id="79329-239">For more information, consult the [PowerShell style guide][] and [Editing reference articles][].</span></span>

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Get-Item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[Guide de style PowerShell]: /powershell/scripting/community/contributing/powershell-style-guide
[PowerShell style guide]: /powershell/scripting/community/contributing/powershell-style-guide
[Modification des articles de référence]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Editing reference articles]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Écriture d’aide pour les modules]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[Writing Help for Modules]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom-Markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Show-Markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
