---
title: Liste de contrôle éditoriale
description: Il s’agit d’une liste résumée des règles de modification de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060334"
---
# <a name="editors-checklist"></a><span data-ttu-id="8ec36-103">Liste de contrôle de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="8ec36-103">Editor's checklist</span></span>

<span data-ttu-id="8ec36-104">Il s’agit d’un résumé des règles à appliquer lors de l’écriture de nouveaux articles ou de la mise à jour d’articles existants.</span><span class="sxs-lookup"><span data-stu-id="8ec36-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="8ec36-105">Pour des explications détaillées et des exemples de ces règles, consultez les autres articles du Guide du contributeur.</span><span class="sxs-lookup"><span data-stu-id="8ec36-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="8ec36-106">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="8ec36-106">Metadata</span></span>

- <span data-ttu-id="8ec36-107">`ms.date` : doit être au format **MM/JJ/AAAA**.</span><span class="sxs-lookup"><span data-stu-id="8ec36-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="8ec36-108">Modifier la date en cas de mise à jour importante ou factuelle :</span><span class="sxs-lookup"><span data-stu-id="8ec36-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="8ec36-109">réorganisation de l’article ;</span><span class="sxs-lookup"><span data-stu-id="8ec36-109">Reorganizing the article</span></span>
    - <span data-ttu-id="8ec36-110">correction d’erreurs factuelles ;</span><span class="sxs-lookup"><span data-stu-id="8ec36-110">Fixing factual errors</span></span>
    - <span data-ttu-id="8ec36-111">ajout de nouvelles informations.</span><span class="sxs-lookup"><span data-stu-id="8ec36-111">Adding new information</span></span>
  - <span data-ttu-id="8ec36-112">Ne pas modifier la date si la mise à jour n’est pas significative :</span><span class="sxs-lookup"><span data-stu-id="8ec36-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="8ec36-113">correction de fautes de frappe et de la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="8ec36-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="8ec36-114">`title` : chaîne unique de 43-59 caractères, espaces compris.</span><span class="sxs-lookup"><span data-stu-id="8ec36-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="8ec36-115">Ne pas inclure l’identificateur de site (il est généré automatiquement).</span><span class="sxs-lookup"><span data-stu-id="8ec36-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="8ec36-116">Utiliser une majuscule pour le premier mot et les noms propres uniquement.</span><span class="sxs-lookup"><span data-stu-id="8ec36-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="8ec36-117">`description`: 115-145 caractères espaces compris. Ce résumé s’affiche dans le résultat de la recherche.</span><span class="sxs-lookup"><span data-stu-id="8ec36-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="8ec36-118">Mise en forme</span><span class="sxs-lookup"><span data-stu-id="8ec36-118">Formatting</span></span>

- <span data-ttu-id="8ec36-119">Éléments de syntaxe avec accent grave qui s’affichent en ligne dans un paragraphe :</span><span class="sxs-lookup"><span data-stu-id="8ec36-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="8ec36-120">nom des cmdlets `Verb-Noun` ;</span><span class="sxs-lookup"><span data-stu-id="8ec36-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="8ec36-121">variable `$counter` ;</span><span class="sxs-lookup"><span data-stu-id="8ec36-121">Variable `$counter`</span></span>
  - <span data-ttu-id="8ec36-122">exemples syntaxiques `Verb-Noun -Parameter` ;</span><span class="sxs-lookup"><span data-stu-id="8ec36-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="8ec36-123">chemins de fichiers `C:\Program Files\PowerShell`, `/usr/bin/pwsh` ;</span><span class="sxs-lookup"><span data-stu-id="8ec36-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="8ec36-124">URL qui ne sont pas censées être cliquables dans le document.</span><span class="sxs-lookup"><span data-stu-id="8ec36-124">URLs that are not meant to be clickable in the document</span></span>
- <span data-ttu-id="8ec36-125">Mettre en gras les noms de propriétés, les valeurs de paramètres, les noms de paramètres, les noms de classes, les noms de modules, les noms d’entités, les noms d’objets et les noms de types.</span><span class="sxs-lookup"><span data-stu-id="8ec36-125">Use bold for property names, parameter values, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="8ec36-126">Les caractères gras servent au balisage sémantique et non à l’accentuation.</span><span class="sxs-lookup"><span data-stu-id="8ec36-126">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="8ec36-127">Gras : utiliser des astérisques `**`.</span><span class="sxs-lookup"><span data-stu-id="8ec36-127">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="8ec36-128">Italique : utiliser le trait de soulignement `_`.</span><span class="sxs-lookup"><span data-stu-id="8ec36-128">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="8ec36-129">L’italique sert uniquement à l’accentuation et non au balisage sémantique.</span><span class="sxs-lookup"><span data-stu-id="8ec36-129">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="8ec36-130">Sauts de ligne à 100 colonnes (ou 80 pour **about_Topics**).</span><span class="sxs-lookup"><span data-stu-id="8ec36-130">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="8ec36-131">Pas d’onglets en dur : utiliser uniquement des espaces.</span><span class="sxs-lookup"><span data-stu-id="8ec36-131">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="8ec36-132">Pas d’espace de fin sur les lignes.</span><span class="sxs-lookup"><span data-stu-id="8ec36-132">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="8ec36-133">headers</span><span class="sxs-lookup"><span data-stu-id="8ec36-133">Headers</span></span>

- <span data-ttu-id="8ec36-134">H1 arrive en premier : un seul H1 par article.</span><span class="sxs-lookup"><span data-stu-id="8ec36-134">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="8ec36-135">Utiliser uniquement des [en-têtes ATX](https://github.github.com/gfm/#atx-headings).</span><span class="sxs-lookup"><span data-stu-id="8ec36-135">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="8ec36-136">Mettre la première lettre des phrases en majuscule pour les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="8ec36-136">Use sentence case for all headers</span></span>
- <span data-ttu-id="8ec36-137">N’ignorer aucun niveau : pas de H3 sans H2.</span><span class="sxs-lookup"><span data-stu-id="8ec36-137">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="8ec36-138">Profondeur maximale : H3 ou H4.</span><span class="sxs-lookup"><span data-stu-id="8ec36-138">Max depth of H3 or H4</span></span>
- <span data-ttu-id="8ec36-139">Ligne vide avant et après.</span><span class="sxs-lookup"><span data-stu-id="8ec36-139">Blank line before and after</span></span>
- <span data-ttu-id="8ec36-140">PlatyPS applique des en-têtes spécifiques dans son schéma : n’ajouter ni ne supprimer aucun en-tête.</span><span class="sxs-lookup"><span data-stu-id="8ec36-140">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="8ec36-141">Blocs de code</span><span class="sxs-lookup"><span data-stu-id="8ec36-141">Code blocks</span></span>

- <span data-ttu-id="8ec36-142">Ligne vide avant et après.</span><span class="sxs-lookup"><span data-stu-id="8ec36-142">Blank line before and after</span></span>
- <span data-ttu-id="8ec36-143">Utiliser des limites de code balisées : **powershell**, **Output** ou tout autre ID de langage adapté.</span><span class="sxs-lookup"><span data-stu-id="8ec36-143">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="8ec36-144">Limite non balisée : blocs syntaxiques ou autres shells.</span><span class="sxs-lookup"><span data-stu-id="8ec36-144">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="8ec36-145">Placer **Output** dans un bloc de code distinct, sauf pour les exemples simples où le lecteur n’est pas censé utiliser le bouton **Copier**.</span><span class="sxs-lookup"><span data-stu-id="8ec36-145">Put **Output** in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="8ec36-146">Voir la liste des [langages pris en charge](/contribute/code-in-docs#supported-languages).</span><span class="sxs-lookup"><span data-stu-id="8ec36-146">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="8ec36-147">Listes</span><span class="sxs-lookup"><span data-stu-id="8ec36-147">Lists</span></span>

- <span data-ttu-id="8ec36-148">Mise en retrait correcte.</span><span class="sxs-lookup"><span data-stu-id="8ec36-148">Indented properly</span></span>
- <span data-ttu-id="8ec36-149">Ligne vide avant le premier élément et après le dernier.</span><span class="sxs-lookup"><span data-stu-id="8ec36-149">Blank line before first item and after last item</span></span>
- <span data-ttu-id="8ec36-150">Puce : utiliser le trait d’union (`-`) et non l’astérisque (`*`), trop facile à confondre avec l’accentuation.</span><span class="sxs-lookup"><span data-stu-id="8ec36-150">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="8ec36-151">Pour les listes numérotées, tous les nombres sont « 1 ».</span><span class="sxs-lookup"><span data-stu-id="8ec36-151">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="8ec36-152">Terminologie</span><span class="sxs-lookup"><span data-stu-id="8ec36-152">Terminology</span></span>

- <span data-ttu-id="8ec36-153">PowerShell, Windows PowerShell ou PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8ec36-153">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="8ec36-154">Voir [Terminologie des produits](powershell-style-guide.md#product-terminology).</span><span class="sxs-lookup"><span data-stu-id="8ec36-154">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="8ec36-155">Exemples d’informations de référence sur les cmdlets</span><span class="sxs-lookup"><span data-stu-id="8ec36-155">Cmdlet reference examples</span></span>

- <span data-ttu-id="8ec36-156">Les informations de référence sur les cmdlets doivent comporter au moins un exemple.</span><span class="sxs-lookup"><span data-stu-id="8ec36-156">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="8ec36-157">Les exemples doivent contenir juste assez de code pour illustrer leur usage.</span><span class="sxs-lookup"><span data-stu-id="8ec36-157">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="8ec36-158">Syntaxe PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8ec36-158">PowerShell syntax</span></span>
  - <span data-ttu-id="8ec36-159">Utiliser le nom complet des cmdlets et des paramètres, sans alias.</span><span class="sxs-lookup"><span data-stu-id="8ec36-159">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="8ec36-160">Utiliser la projection pour les paramètres lorsque la ligne de commande est trop longue.</span><span class="sxs-lookup"><span data-stu-id="8ec36-160">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="8ec36-161">Éviter autant que possible d’utiliser des accents graves de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="8ec36-161">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="8ec36-162">Supprimer ou simplifier l’invite PowerShell (`PS>`), sauf si l’exemple l’exige.</span><span class="sxs-lookup"><span data-stu-id="8ec36-162">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="8ec36-163">L’exemple d’informations de référence sur les cmdlets doit suivre le schéma PlatyPS suivant :</span><span class="sxs-lookup"><span data-stu-id="8ec36-163">Cmdlet reference example must follow the following PlatyPS schema</span></span>

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- <span data-ttu-id="8ec36-164">Ne pas placer de paragraphes entre les blocs de code.</span><span class="sxs-lookup"><span data-stu-id="8ec36-164">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="8ec36-165">Tout le contenu descriptif doit venir avant ou après les blocs de code.</span><span class="sxs-lookup"><span data-stu-id="8ec36-165">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="8ec36-166">Lien vers d’autres documents</span><span class="sxs-lookup"><span data-stu-id="8ec36-166">Linking to other documents</span></span>

- <span data-ttu-id="8ec36-167">Les liens extérieurs à l’ensemble de documents ou entre informations de référence sur les cmdlets sont conceptuels :</span><span class="sxs-lookup"><span data-stu-id="8ec36-167">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="8ec36-168">Utiliser des URL relatives pour les liens vers docs.microsoft.com (supprimer `https://docs.microsoft.com/en-us`).</span><span class="sxs-lookup"><span data-stu-id="8ec36-168">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="8ec36-169">Ne pas inclure de paramètres régionaux dans les URL sur les propriétés Microsoft (par exemple,</span><span class="sxs-lookup"><span data-stu-id="8ec36-169">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="8ec36-170">supprimer `/en-us` dans l’URL).</span><span class="sxs-lookup"><span data-stu-id="8ec36-170">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="8ec36-171">Toutes les URL de sites web externes doivent utiliser le protocole HTTPS, sauf si ce n’est pas valide pour le site cible.</span><span class="sxs-lookup"><span data-stu-id="8ec36-171">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="8ec36-172">Au sein de l’ensemble de documents :</span><span class="sxs-lookup"><span data-stu-id="8ec36-172">Within docset</span></span>
  - <span data-ttu-id="8ec36-173">Lien vers le chemin d’un fichier (par exemple, `../folder/file.md`).</span><span class="sxs-lookup"><span data-stu-id="8ec36-173">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="8ec36-174">Tous les chemins de fichiers utilisent des barres obliques (`/`).</span><span class="sxs-lookup"><span data-stu-id="8ec36-174">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="8ec36-175">Les liens d’images doivent comporter un texte de remplacement unique.</span><span class="sxs-lookup"><span data-stu-id="8ec36-175">Image links should have unique alt text</span></span>
