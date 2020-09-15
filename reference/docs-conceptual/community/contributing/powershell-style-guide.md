---
title: Guide de style pour la documentation PowerShell
description: Cet article présente les règles de style pour l’écriture de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 32df641f7cafa2a5bfcf1bcbf94be594aa77c7d0
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837441"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="b55fa-103">Guide de style pour la documentation PowerShell</span><span class="sxs-lookup"><span data-stu-id="b55fa-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="b55fa-104">Cet article donne des conseils de style propres au contenu PowerShell-Docs,</span><span class="sxs-lookup"><span data-stu-id="b55fa-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="b55fa-105">qui s’appuient sur les informations présentées dans la [Vue d’ensemble](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="b55fa-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="b55fa-106">Terminologie des produits</span><span class="sxs-lookup"><span data-stu-id="b55fa-106">Product Terminology</span></span>

<span data-ttu-id="b55fa-107">Il existe plusieurs variantes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b55fa-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="b55fa-108">**PowerShell** : terme par défaut.</span><span class="sxs-lookup"><span data-stu-id="b55fa-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="b55fa-109">Nous considérons la version 7 et les versions ultérieures de PowerShell comme le vrai PowerShell, à ce jour et à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="b55fa-109">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>
- <span data-ttu-id="b55fa-110">**PowerShell Core** : PowerShell reposant sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b55fa-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="b55fa-111">L’utilisation du terme **Core** doit être limitée aux cas où il est nécessaire de le différencier de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b55fa-111">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="b55fa-112">**Windows PowerShell** : PowerShell reposant sur .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b55fa-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="b55fa-113">Windows PowerShell est fourni uniquement sur Windows et requiert l’infrastructure complète.</span><span class="sxs-lookup"><span data-stu-id="b55fa-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="b55fa-114">En général, les références à « Windows PowerShell » dans la documentation peuvent être remplacées par « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="b55fa-114">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
  <span data-ttu-id="b55fa-115">« Windows PowerShell » doit être utilisé lorsque l’on aborde le comportement spécifique à « Windows PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="b55fa-115">"Windows PowerShell" should be used when "Windows PowerShell"-specific behavior is being discussed.</span></span>

<span data-ttu-id="b55fa-116">Produits connexes</span><span class="sxs-lookup"><span data-stu-id="b55fa-116">Related products</span></span>

- <span data-ttu-id="b55fa-117">**Visual Studio Code (VS Code)** : il s’agit de l’éditeur open source et gratuit de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b55fa-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open source editor.</span></span> <span data-ttu-id="b55fa-118">Lors de la première mention, le nom complet doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="b55fa-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="b55fa-119">Après cela, vous pouvez utiliser **VS Code**.</span><span class="sxs-lookup"><span data-stu-id="b55fa-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="b55fa-120">N’utilisez pas « VSCode ».</span><span class="sxs-lookup"><span data-stu-id="b55fa-120">Do not use "VSCode".</span></span>
- <span data-ttu-id="b55fa-121">**Extension PowerShell pour Visual Studio Code** : l’extension active VS Code dans l’IDE préféré pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b55fa-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="b55fa-122">Lors de la première mention, le nom complet doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="b55fa-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="b55fa-123">Après cela, vous pouvez utiliser **Extension PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="b55fa-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="b55fa-124">**Azure PowerShell** : il s’agit de la collection de modules PowerShell utilisés pour gérer les services Azure.</span><span class="sxs-lookup"><span data-stu-id="b55fa-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="b55fa-125">**Azure Stack PowerShell** : il s’agit de la collection de modules PowerShell utilisés pour gérer la solution cloud hybride de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b55fa-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="b55fa-126">Spécificités de Markdown</span><span class="sxs-lookup"><span data-stu-id="b55fa-126">Markdown specifics</span></span>

<span data-ttu-id="b55fa-127">Microsoft Open Publishing System (OPS), qui nous permet de créer notre documentation, utilise [markdig][] pour traiter les documents Markdown.</span><span class="sxs-lookup"><span data-stu-id="b55fa-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="b55fa-128">Markdig analyse les documents suivant les règles de la dernière spécification [CommonMark][].</span><span class="sxs-lookup"><span data-stu-id="b55fa-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="b55fa-129">La nouvelle spécification CommonMark est plus stricte sur la construction de certains éléments Markdown.</span><span class="sxs-lookup"><span data-stu-id="b55fa-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="b55fa-130">Portez une attention particulière aux informations fournies dans ce document.</span><span class="sxs-lookup"><span data-stu-id="b55fa-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="b55fa-131">Lignes vides, espaces et tabulations</span><span class="sxs-lookup"><span data-stu-id="b55fa-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="b55fa-132">Les lignes vides signalent également la fin d’un bloc en Markdown.</span><span class="sxs-lookup"><span data-stu-id="b55fa-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="b55fa-133">Il doit y avoir un seul espace entre les blocs Markdown de différents types (par exemple, entre un paragraphe et une liste ou un en-tête).</span><span class="sxs-lookup"><span data-stu-id="b55fa-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="b55fa-134">Supprimez les lignes vides en double.</span><span class="sxs-lookup"><span data-stu-id="b55fa-134">Remove duplicate blank lines.</span></span> <span data-ttu-id="b55fa-135">S’il existe plusieurs lignes vides, elles s’affichent comme une seule ligne vide en HTML ; il n’y a donc pas d’intérêt à en insérer plusieurs.</span><span class="sxs-lookup"><span data-stu-id="b55fa-135">Multiple blank lines render as a single blank line in HTML so there is no purpose for multiple blank lines.</span></span> <span data-ttu-id="b55fa-136">Plusieurs lignes vides au sein d’un bloc de code rompent le bloc de code.</span><span class="sxs-lookup"><span data-stu-id="b55fa-136">Multiple blank lines within a code block break the code block.</span></span>

<span data-ttu-id="b55fa-137">Supprimez les espaces supplémentaires à la fin des lignes.</span><span class="sxs-lookup"><span data-stu-id="b55fa-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="b55fa-138">L’espacement est significatif en Markdown.</span><span class="sxs-lookup"><span data-stu-id="b55fa-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="b55fa-139">Utilisez toujours des espaces plutôt que des tabulations fixes.</span><span class="sxs-lookup"><span data-stu-id="b55fa-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="b55fa-140">Les espaces de fin peuvent modifier le rendu Markdown.</span><span class="sxs-lookup"><span data-stu-id="b55fa-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="b55fa-141">Titres et en-têtes</span><span class="sxs-lookup"><span data-stu-id="b55fa-141">Titles and headings</span></span>

<span data-ttu-id="b55fa-142">Utilisez uniquement des [en-têtes ATX][atx] (de style #, par opposition aux en-têtes de style `=` ou `-`).</span><span class="sxs-lookup"><span data-stu-id="b55fa-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="b55fa-143">Seule la première lettre des phrases, des noms propres, des titres et des en-têtes doit être en majuscule.</span><span class="sxs-lookup"><span data-stu-id="b55fa-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="b55fa-144">Il doit y avoir un seul espace entre le `#` et la première lettre du titre.</span><span class="sxs-lookup"><span data-stu-id="b55fa-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="b55fa-145">Les en-têtes doivent être délimités par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="b55fa-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="b55fa-146">Un document ne peut contenir qu’un seul titre H1.</span><span class="sxs-lookup"><span data-stu-id="b55fa-146">Only one H1 per document</span></span>
- <span data-ttu-id="b55fa-147">Les niveaux d’en-têtes doivent se suivre par incréments de un,</span><span class="sxs-lookup"><span data-stu-id="b55fa-147">Header levels should increment by one.</span></span> <span data-ttu-id="b55fa-148">sans qu’un niveau soit ignoré.</span><span class="sxs-lookup"><span data-stu-id="b55fa-148">Do not skip levels</span></span>
- <span data-ttu-id="b55fa-149">N’utilisez pas de balises de type gras ou autre dans les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="b55fa-149">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="b55fa-150">Limiter la longueur de ligne à 100 caractères</span><span class="sxs-lookup"><span data-stu-id="b55fa-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="b55fa-151">Cette règle s’applique aux articles conceptuels et aux informations de référence sur les cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b55fa-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="b55fa-152">Le fait de limiter la longueur de ligne améliore la lisibilité des différences et de l’historique de Git.</span><span class="sxs-lookup"><span data-stu-id="b55fa-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="b55fa-153">Elle permet également aux autres rédacteurs d’apporter plus facilement leur contribution.</span><span class="sxs-lookup"><span data-stu-id="b55fa-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="b55fa-154">Utilisez l’extension [Reflow Markdown][reflow] dans Visual Studio Code pour ajuster dynamiquement les paragraphes en fonction de la longueur de ligne prescrite.</span><span class="sxs-lookup"><span data-stu-id="b55fa-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="b55fa-155">Les rubriques About_ sont limitées à 80 caractères.</span><span class="sxs-lookup"><span data-stu-id="b55fa-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="b55fa-156">Pour plus d’informations, consultez [Modification des articles de référence](./editing-cmdlet-ref.md#formatting-about_-files).</span><span class="sxs-lookup"><span data-stu-id="b55fa-156">For more specific information, see [Editing reference articles](./editing-cmdlet-ref.md#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="b55fa-157">Listes</span><span class="sxs-lookup"><span data-stu-id="b55fa-157">Lists</span></span>

<span data-ttu-id="b55fa-158">Si votre liste contient plusieurs phrases ou paragraphes, utilisez de préférence un en-tête de sous-niveau plutôt qu’une liste.</span><span class="sxs-lookup"><span data-stu-id="b55fa-158">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="b55fa-159">Les listes doivent être délimitées par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="b55fa-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="b55fa-160">Listes non triées</span><span class="sxs-lookup"><span data-stu-id="b55fa-160">Unordered lists</span></span>

<span data-ttu-id="b55fa-161">Les éléments de liste ne doivent pas se terminer par un point, sauf s’ils contiennent plusieurs phrases.</span><span class="sxs-lookup"><span data-stu-id="b55fa-161">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="b55fa-162">Utilisez le caractère de trait d’union (`-`) comme puce pour les éléments de liste</span><span class="sxs-lookup"><span data-stu-id="b55fa-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="b55fa-163">afin d’éviter toute confusion avec les balises de type gras ou en italique qui utilisent l’astérisque [`*`].</span><span class="sxs-lookup"><span data-stu-id="b55fa-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="b55fa-164">Pour inclure un paragraphe ou d’autres éléments sous un élément de puce, insérez un saut de ligne et alignez le retrait avec le premier caractère après la puce.</span><span class="sxs-lookup"><span data-stu-id="b55fa-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="b55fa-165">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-165">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="b55fa-166">Voici une liste qui contient des sous-éléments sous un élément de puce.</span><span class="sxs-lookup"><span data-stu-id="b55fa-166">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="b55fa-167">Premier élément de puce</span><span class="sxs-lookup"><span data-stu-id="b55fa-167">First bullet item</span></span>

  <span data-ttu-id="b55fa-168">Phrase expliquant la première puce.</span><span class="sxs-lookup"><span data-stu-id="b55fa-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="b55fa-169">Élément de puce de niveau inférieur</span><span class="sxs-lookup"><span data-stu-id="b55fa-169">Sub-bullet item</span></span>

    <span data-ttu-id="b55fa-170">Phrase expliquant la puce de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="b55fa-170">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="b55fa-171">Deuxième élément de puce</span><span class="sxs-lookup"><span data-stu-id="b55fa-171">Second bullet item</span></span>
- <span data-ttu-id="b55fa-172">Troisième élément de puce</span><span class="sxs-lookup"><span data-stu-id="b55fa-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="b55fa-173">Listes triées</span><span class="sxs-lookup"><span data-stu-id="b55fa-173">Ordered lists</span></span>

<span data-ttu-id="b55fa-174">Pour inclure un paragraphe ou d’autres éléments sous un élément numéroté, alignez le retrait avec le premier caractère après le numéro d’élément.</span><span class="sxs-lookup"><span data-stu-id="b55fa-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="b55fa-175">Tous les éléments d’une liste numérotée doivent utiliser le numéro `1.` sans incrémentation.</span><span class="sxs-lookup"><span data-stu-id="b55fa-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="b55fa-176">Le rendu Markdown incrémente automatiquement la valeur,</span><span class="sxs-lookup"><span data-stu-id="b55fa-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="b55fa-177">ce qui permet de réorganiser plus facilement les éléments et standardise la mise en retrait du contenu subordonné.</span><span class="sxs-lookup"><span data-stu-id="b55fa-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="b55fa-178">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-178">For example:</span></span>

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

<span data-ttu-id="b55fa-179">Le Markdown résultant est rendu de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="b55fa-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="b55fa-180">Pour le premier élément, insérez un seul espace après le 1.</span><span class="sxs-lookup"><span data-stu-id="b55fa-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="b55fa-181">Les phrases longues doivent comporter un retour automatique à la ligne et être alignées avec le premier caractère après le marqueur de liste numérotée.</span><span class="sxs-lookup"><span data-stu-id="b55fa-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="b55fa-182">Pour inclure un deuxième élément (comme celui-ci), insérez un saut de ligne après le premier et alignez les mises en retrait.</span><span class="sxs-lookup"><span data-stu-id="b55fa-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="b55fa-183">Le retrait du deuxième élément doit être aligné avec le premier caractère après le marqueur de liste numérotée.</span><span class="sxs-lookup"><span data-stu-id="b55fa-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="b55fa-184">Pour les éléments à un seul chiffre, comme celui-ci, la mise en retrait s’effectue vers la colonne 4.</span><span class="sxs-lookup"><span data-stu-id="b55fa-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="b55fa-185">Pour les éléments à deux chiffres, par exemple le numéro d’élément 10, elle s’effectue vers la colonne 5.</span><span class="sxs-lookup"><span data-stu-id="b55fa-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="b55fa-186">L’élément numéroté suivant commence ici.</span><span class="sxs-lookup"><span data-stu-id="b55fa-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="b55fa-187">Images</span><span class="sxs-lookup"><span data-stu-id="b55fa-187">Images</span></span>

<span data-ttu-id="b55fa-188">Voici la syntaxe permettant d’inclure une image :</span><span class="sxs-lookup"><span data-stu-id="b55fa-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="b55fa-189">Où `alt text` est une brève description de l’image et `<folder path>` le chemin relatif de l’image.</span><span class="sxs-lookup"><span data-stu-id="b55fa-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="b55fa-190">Le texte de remplacement est nécessaire pour les lecteurs d’écran des personnes déficientes visuelles.</span><span class="sxs-lookup"><span data-stu-id="b55fa-190">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="b55fa-191">Il est également utile en cas de bogue du site empêchant le rendu de l’image.</span><span class="sxs-lookup"><span data-stu-id="b55fa-191">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="b55fa-192">Les images doivent être stockées dans un dossier `media/<article-name>` à l’intérieur du dossier contenant l’article.</span><span class="sxs-lookup"><span data-stu-id="b55fa-192">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="b55fa-193">Elles ne doivent pas être partagées entre les articles.</span><span class="sxs-lookup"><span data-stu-id="b55fa-193">Images should not be shared between articles.</span></span> <span data-ttu-id="b55fa-194">Créez un dossier correspondant au nom de fichier de votre article dans le dossier `media`.</span><span class="sxs-lookup"><span data-stu-id="b55fa-194">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="b55fa-195">Copiez les images de cet article dans ce nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="b55fa-195">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="b55fa-196">Si une image est utilisée par plusieurs articles, chaque dossier d’image doit comporter une copie de ce fichier image.</span><span class="sxs-lookup"><span data-stu-id="b55fa-196">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="b55fa-197">Cette pratique permet d’éviter que la modification d’une image dans un article n’affecte un autre article.</span><span class="sxs-lookup"><span data-stu-id="b55fa-197">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="b55fa-198">Sont pris en charge les types de fichiers images suivants : `*.png`, `*.gif`, `*.jpeg`, `*.jpg` et `*.svg`.</span><span class="sxs-lookup"><span data-stu-id="b55fa-198">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="b55fa-199">Extensions Markdown prises en charge par Open Publishing</span><span class="sxs-lookup"><span data-stu-id="b55fa-199">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="b55fa-200">[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contient des outils qui gèrent des fonctionnalités propres à notre système de publication.</span><span class="sxs-lookup"><span data-stu-id="b55fa-200">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="b55fa-201">Les alertes sont une extension Markdown permettant de créer des citations qui s’affichent sur docs.microsoft.com avec des couleurs et des icônes différentes selon l’importance du contenu.</span><span class="sxs-lookup"><span data-stu-id="b55fa-201">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="b55fa-202">Sont pris en charge les types d’alertes suivants :</span><span class="sxs-lookup"><span data-stu-id="b55fa-202">The following alert types are supported:</span></span>

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

<span data-ttu-id="b55fa-203">Ces alertes se présentent ainsi sur docs.microsoft.com :</span><span class="sxs-lookup"><span data-stu-id="b55fa-203">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="b55fa-204">Bloc Note</span><span class="sxs-lookup"><span data-stu-id="b55fa-204">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="b55fa-205">Informations que l’utilisateur devrait remarquer même en parcourant rapidement le document.</span><span class="sxs-lookup"><span data-stu-id="b55fa-205">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="b55fa-206">Bloc Conseil</span><span class="sxs-lookup"><span data-stu-id="b55fa-206">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="b55fa-207">Informations facultatives visant à aider l’utilisateur à gagner en efficacité.</span><span class="sxs-lookup"><span data-stu-id="b55fa-207">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="b55fa-208">Bloc Important</span><span class="sxs-lookup"><span data-stu-id="b55fa-208">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b55fa-209">Informations essentielles nécessaires à la réussite de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b55fa-209">Essential information required for user success.</span></span>

<span data-ttu-id="b55fa-210">Bloc Attention</span><span class="sxs-lookup"><span data-stu-id="b55fa-210">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="b55fa-211">Conséquences négatives potentielles d’une action.</span><span class="sxs-lookup"><span data-stu-id="b55fa-211">Negative potential consequences of an action.</span></span>

<span data-ttu-id="b55fa-212">Bloc Avertissement</span><span class="sxs-lookup"><span data-stu-id="b55fa-212">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="b55fa-213">Conséquences dangereuses certaines d’une action.</span><span class="sxs-lookup"><span data-stu-id="b55fa-213">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="b55fa-214">Liens hypertexte</span><span class="sxs-lookup"><span data-stu-id="b55fa-214">Hyperlinks</span></span>

- <span data-ttu-id="b55fa-215">Les liens hypertexte doivent utiliser la syntaxe Markdown `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="b55fa-215">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="b55fa-216">Les liens doivent utiliser le protocole HTTPS dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="b55fa-216">Links should be HTTPS when possible.</span></span>
- <span data-ttu-id="b55fa-217">Les liens doivent avoir un nom convivial, généralement le titre de la rubrique liée.</span><span class="sxs-lookup"><span data-stu-id="b55fa-217">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="b55fa-218">Tous les éléments de la section « liens connexes » en bas de la page doivent contenir des liens hypertexte.</span><span class="sxs-lookup"><span data-stu-id="b55fa-218">All items in the "related links" section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="b55fa-219">N’utilisez pas d’accents graves ou de balises de type gras ou autre à l’intérieur des crochets d’un lien hypertexte.</span><span class="sxs-lookup"><span data-stu-id="b55fa-219">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="b55fa-220">Les URL brutes peuvent être utilisées lorsque vous parlez d’un URI spécifique.</span><span class="sxs-lookup"><span data-stu-id="b55fa-220">Bare URLs may be used when you are talking about a specific URI.</span></span> <span data-ttu-id="b55fa-221">L’URI doit être placé entre des accents graves.</span><span class="sxs-lookup"><span data-stu-id="b55fa-221">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="b55fa-222">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-222">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a><span data-ttu-id="b55fa-223">Liens vers d’autres contenus</span><span class="sxs-lookup"><span data-stu-id="b55fa-223">Linking to other content</span></span>

<span data-ttu-id="b55fa-224">Il existe deux types de liens hypertextes pris en charge par le système de publication :</span><span class="sxs-lookup"><span data-stu-id="b55fa-224">There are two types of hyperlinks supported by the publishing system:</span></span>

<span data-ttu-id="b55fa-225">Un **lien URL** peut être un chemin d’URL relatif à la racine de docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="b55fa-225">A **URL link** can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="b55fa-226">ou une URL absolue comportant la syntaxe complète de l’URL</span><span class="sxs-lookup"><span data-stu-id="b55fa-226">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="b55fa-227">Par exemple : `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span><span class="sxs-lookup"><span data-stu-id="b55fa-227">For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span></span>

- <span data-ttu-id="b55fa-228">Utilisez des liens URL pour établir un lien vers du contenu extérieur à PowerShell-Docs ou entre des informations de référence sur les cmdlets et des articles conceptuels dans PowerShell-Docs. Le moyen le plus simple de créer un lien relatif consiste à copier l’URL dans votre navigateur, puis à supprimer `https://docs.microsoft.com/en-us` de la valeur que vous collez dans Markdown.</span><span class="sxs-lookup"><span data-stu-id="b55fa-228">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs. The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
- <span data-ttu-id="b55fa-229">Ne pas inclure de paramètres régionaux dans les URL sur les propriétés Microsoft (par exemple,</span><span class="sxs-lookup"><span data-stu-id="b55fa-229">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="b55fa-230">supprimer `/en-us` dans l’URL).</span><span class="sxs-lookup"><span data-stu-id="b55fa-230">remove `/en-us` from URL).</span></span>
- <span data-ttu-id="b55fa-231">Supprimez les paramètres de requête inutiles de l’URL, sauf si vous avez besoin de créer un lien vers une version spécifique d’un article.</span><span class="sxs-lookup"><span data-stu-id="b55fa-231">Remove any unnecessary query parameters from the URL unless you need to link to a specific version of an article.</span></span> <span data-ttu-id="b55fa-232">Exemples :</span><span class="sxs-lookup"><span data-stu-id="b55fa-232">Examples:</span></span>
  - <span data-ttu-id="b55fa-233">`?view=powershell-5.1` : utilisé pour établir un lien vers une version spécifique de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b55fa-233">`?view=powershell-5.1` - this is used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="b55fa-234">`?redirectedfrom=MSDN` : ajouté à l’URL lorsque vous êtes redirigé depuis un ancien article vers son nouvel emplacement</span><span class="sxs-lookup"><span data-stu-id="b55fa-234">`?redirectedfrom=MSDN` - this is added to the URL when you get redirected from an old article to its new location</span></span>
- <span data-ttu-id="b55fa-235">Toutes les URL de sites web externes doivent utiliser le protocole HTTPS, sauf si ce n’est pas valide pour le site cible.</span><span class="sxs-lookup"><span data-stu-id="b55fa-235">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="b55fa-236">Un **lien de fichier** est utilisé pour établir un lien d’un article de référence à un autre, ou d’un article conceptuel à un autre.</span><span class="sxs-lookup"><span data-stu-id="b55fa-236">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="b55fa-237">Si vous avez besoin de créer un lien vers un article de référence pour une version spécifique de PowerShell, vous devez utiliser un lien URL.</span><span class="sxs-lookup"><span data-stu-id="b55fa-237">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

- <span data-ttu-id="b55fa-238">Les liens de fichiers contiennent un chemin de fichier relatif (par exemple, `../folder/file.md`).</span><span class="sxs-lookup"><span data-stu-id="b55fa-238">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="b55fa-239">Tous les chemins de fichiers utilisent des barres obliques (`/`).</span><span class="sxs-lookup"><span data-stu-id="b55fa-239">All file paths use forward-slash (`/`) characters</span></span>

<span data-ttu-id="b55fa-240">La liaison profonde est autorisée à la fois sur les liens d’URL et de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b55fa-240">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="b55fa-241">Ajoutez l’ancre à la fin du chemin d’accès cible.</span><span class="sxs-lookup"><span data-stu-id="b55fa-241">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="b55fa-242">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-242">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="b55fa-243">Pour plus d’informations, consultez [Utiliser des liens dans la documentation](/contribute/how-to-write-links).</span><span class="sxs-lookup"><span data-stu-id="b55fa-243">For more information, see [Use links in documentation](/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="b55fa-244">Mise en forme des éléments de syntaxe de commande</span><span class="sxs-lookup"><span data-stu-id="b55fa-244">Formatting command syntax elements</span></span>

- <span data-ttu-id="b55fa-245">Utilisez toujours le nom complet pour les cmdlets et les paramètres.</span><span class="sxs-lookup"><span data-stu-id="b55fa-245">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="b55fa-246">Évitez d’utiliser des alias à moins qu’il ne s’agisse spécifiquement d’une démonstration des alias.</span><span class="sxs-lookup"><span data-stu-id="b55fa-246">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="b55fa-247">Les noms de propriété, de paramètre, d’objet, de type, les noms de classes, les méthodes de classe doivent être en **gras**.</span><span class="sxs-lookup"><span data-stu-id="b55fa-247">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="b55fa-248">Les valeurs des propriétés et des paramètres doivent être encapsulées entre des accents graves (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="b55fa-248">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="b55fa-249">Quand vous faites référence à des types à l’aide du style entre crochets, utilisez des accents graves.</span><span class="sxs-lookup"><span data-stu-id="b55fa-249">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="b55fa-250">Par exemple : `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="b55fa-250">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="b55fa-251">Les mots clés de langage, les noms d’applet de commande, les fonctions, les variables, les fichiers EXE natifs, les chemins de fichiers et les exemples de syntaxe Inline doivent être encapsulés entre des accents graves (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="b55fa-251">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="b55fa-252">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-252">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="b55fa-253">En cas de référence à un paramètre par son nom, ce nom doit être en **gras**.</span><span class="sxs-lookup"><span data-stu-id="b55fa-253">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="b55fa-254">Pour illustrer l’utilisation d’un paramètre avec le préfixe de trait d’union, ce paramètre doit être placé entre accents graves.</span><span class="sxs-lookup"><span data-stu-id="b55fa-254">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="b55fa-255">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-255">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="b55fa-256">Pour montrer l’utilisation d’une commande externe, l’exemple doit être placé entre accents graves.</span><span class="sxs-lookup"><span data-stu-id="b55fa-256">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="b55fa-257">Incluez toujours l’extension de fichier dans la commande native.</span><span class="sxs-lookup"><span data-stu-id="b55fa-257">Always include the file extension in the native command.</span></span> <span data-ttu-id="b55fa-258">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-258">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="b55fa-259">L’inclusion de l’extension de fichier garantit que la commande correcte est exécutée conformément à la priorité des commandes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b55fa-259">Including the file extension ensures that the correct command is executed according PowerShell's command precedence.</span></span>

- <span data-ttu-id="b55fa-260">Lorsque vous écrivez un article conceptuel (par opposition à du contenu de référence), la première instance du nom d’une cmdlet doit comporter un lien hypertexte vers la documentation de la cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b55fa-260">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="b55fa-261">N’utilisez pas d’accents graves ou de balises de type gras ou autre à l’intérieur des crochets d’un lien hypertexte.</span><span class="sxs-lookup"><span data-stu-id="b55fa-261">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="b55fa-262">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-262">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="b55fa-263">Pour plus d’informations, consultez la section [Liens hypertextes](#hyperlinks) de cet article.</span><span class="sxs-lookup"><span data-stu-id="b55fa-263">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="b55fa-264">Markdown pour les exemples de code</span><span class="sxs-lookup"><span data-stu-id="b55fa-264">Markdown for code samples</span></span>

<span data-ttu-id="b55fa-265">Markdown prend en charge deux styles de code différents :</span><span class="sxs-lookup"><span data-stu-id="b55fa-265">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="b55fa-266">Le **code inline**, marqué par un seul caractère accent grave (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="b55fa-266">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="b55fa-267">et utilisé au sein d’un paragraphe plutôt que comme bloc autonome ;</span><span class="sxs-lookup"><span data-stu-id="b55fa-267">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="b55fa-268">les **blocs de code**, blocs de plusieurs lignes délimités par des chaînes constituées de trois accents graves (`` ``` ``)</span><span class="sxs-lookup"><span data-stu-id="b55fa-268">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="b55fa-269">éventuellement suivis d’une étiquette de langage</span><span class="sxs-lookup"><span data-stu-id="b55fa-269">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="b55fa-270">qui permet la coloration syntaxique du contenu du bloc de code.</span><span class="sxs-lookup"><span data-stu-id="b55fa-270">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="b55fa-271">Tous les blocs de code doivent être délimités</span><span class="sxs-lookup"><span data-stu-id="b55fa-271">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="b55fa-272">N’utilisez jamais la mise en retrait pour les blocs de code.</span><span class="sxs-lookup"><span data-stu-id="b55fa-272">Never use indentation for code blocks.</span></span> <span data-ttu-id="b55fa-273">Markdown autorise ce modèle, mais il peut être problématique et doit être évité.</span><span class="sxs-lookup"><span data-stu-id="b55fa-273">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="b55fa-274">Un bloc de code est une ou plusieurs lignes de code entourées d’une limite de code de trois caractères accent grave (`` ``` ``).</span><span class="sxs-lookup"><span data-stu-id="b55fa-274">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="b55fa-275">Les délimiteurs de code doivent se trouver sur leur propre ligne avant et après l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="b55fa-275">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="b55fa-276">Le marqueur de début du bloc de code peut éventuellement comporter une étiquette de langage.</span><span class="sxs-lookup"><span data-stu-id="b55fa-276">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="b55fa-277">Microsoft Open Publishing System (OPS) utilise l’étiquette de langage pour gérer la fonctionnalité de coloration syntaxique.</span><span class="sxs-lookup"><span data-stu-id="b55fa-277">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="b55fa-278">Pour obtenir la liste complète des balises de langage prises en charge, consultez [Blocs de code délimités](/contribute/code-in-docs#fenced-code-blocks) dans le Guide du contributeur centralisé.</span><span class="sxs-lookup"><span data-stu-id="b55fa-278">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="b55fa-279">OPS ajoute également un bouton **Copier** qui permet de copier le contenu du bloc de code dans le Presse-papiers,</span><span class="sxs-lookup"><span data-stu-id="b55fa-279">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="b55fa-280">et ainsi de coller rapidement le code dans un script pour tester l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="b55fa-280">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="b55fa-281">Toutefois, les exemples de notre documentation ne sont pas tous destinés à être exécutés tels quels.</span><span class="sxs-lookup"><span data-stu-id="b55fa-281">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="b55fa-282">Certains blocs de code sont de simples illustrations d’un concept de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b55fa-282">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="b55fa-283">Trois types de blocs de code sont utilisés dans notre documentation :</span><span class="sxs-lookup"><span data-stu-id="b55fa-283">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="b55fa-284">Blocs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="b55fa-284">Syntax blocks</span></span>
1. <span data-ttu-id="b55fa-285">Exemples servant d’illustration</span><span class="sxs-lookup"><span data-stu-id="b55fa-285">Illustrative examples</span></span>
1. <span data-ttu-id="b55fa-286">Exemples exécutables</span><span class="sxs-lookup"><span data-stu-id="b55fa-286">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="b55fa-287">Blocs de code syntaxiques</span><span class="sxs-lookup"><span data-stu-id="b55fa-287">Syntax code blocks</span></span>

<span data-ttu-id="b55fa-288">Les blocs de code de syntaxe sont utilisés pour décrire la structure syntaxique d’une commande.</span><span class="sxs-lookup"><span data-stu-id="b55fa-288">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="b55fa-289">N’utilisez pas de balise de langage sur la limite du code.</span><span class="sxs-lookup"><span data-stu-id="b55fa-289">Do not use a language tag on the code fence.</span></span> <span data-ttu-id="b55fa-290">Cet exemple illustre tous les paramètres possibles de la cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="b55fa-290">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="b55fa-291">Cet exemple décrit l’instruction `for` en termes généralisés :</span><span class="sxs-lookup"><span data-stu-id="b55fa-291">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="b55fa-292">Exemples servant d’illustration</span><span class="sxs-lookup"><span data-stu-id="b55fa-292">Illustrative examples</span></span>

<span data-ttu-id="b55fa-293">Certains exemples servent d’illustration pour expliquer un concept de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b55fa-293">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="b55fa-294">Ils ne sont pas destinés à être copiés dans le Presse-papiers pour être exécutés.</span><span class="sxs-lookup"><span data-stu-id="b55fa-294">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="b55fa-295">Ils sont couramment utilisés pour des exemples simples et faciles à taper et à comprendre.</span><span class="sxs-lookup"><span data-stu-id="b55fa-295">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="b55fa-296">Le bloc de code peut inclure l’invite PowerShell et l’exemple de sortie.</span><span class="sxs-lookup"><span data-stu-id="b55fa-296">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="b55fa-297">Voici un exemple simple illustrant les opérateurs de comparaison de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b55fa-297">Here is a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="b55fa-298">Il n’est pas attendu du lecteur qu’il copie et exécute cet exemple.</span><span class="sxs-lookup"><span data-stu-id="b55fa-298">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="b55fa-299">Exemples exécutables</span><span class="sxs-lookup"><span data-stu-id="b55fa-299">Executable examples</span></span>

<span data-ttu-id="b55fa-300">Les exemples complexes ou destinés à être copiés et exécutés doivent utiliser le balisage de style bloc suivant :</span><span class="sxs-lookup"><span data-stu-id="b55fa-300">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="b55fa-301">La sortie affichée par les commandes PowerShell doit être placée dans un bloc de code **Output** pour empêcher la coloration syntaxique.</span><span class="sxs-lookup"><span data-stu-id="b55fa-301">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="b55fa-302">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b55fa-302">For example:</span></span>

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

<span data-ttu-id="b55fa-303">L’étiquette de code **Output** n’est pas un « langage » officiel pris en charge par le système de coloration syntaxique.</span><span class="sxs-lookup"><span data-stu-id="b55fa-303">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="b55fa-304">Elle est toutefois utile, car OPS ajoute l’étiquette « Output » (« Sortie ») au cadre de la zone de code sur la page web.</span><span class="sxs-lookup"><span data-stu-id="b55fa-304">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="b55fa-305">La zone de code « Output » ne présente pas de coloration syntaxique.</span><span class="sxs-lookup"><span data-stu-id="b55fa-305">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="b55fa-306">Règles de style de codage</span><span class="sxs-lookup"><span data-stu-id="b55fa-306">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="b55fa-307">Éviter la continuation de ligne dans les exemples de code</span><span class="sxs-lookup"><span data-stu-id="b55fa-307">Avoid line continuation in code samples</span></span>

<span data-ttu-id="b55fa-308">Évitez d’utiliser des caractères de continuation de ligne (`` ` ``) dans les exemples de code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b55fa-308">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="b55fa-309">Ils sont difficiles à voir et peuvent poser problème en présence d’espaces supplémentaires à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b55fa-309">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="b55fa-310">Utilisez la projection PowerShell pour réduire la longueur de ligne des cmdlets comportant de nombreux paramètres.</span><span class="sxs-lookup"><span data-stu-id="b55fa-310">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="b55fa-311">Tirez parti des possibilités naturelles de saut de ligne de PowerShell, comme après les caractères barre verticale (`|`), les accolades ouvrantes, les parenthèses et les crochets.</span><span class="sxs-lookup"><span data-stu-id="b55fa-311">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="b55fa-312">Éviter d’utiliser les invites PowerShell dans les exemples</span><span class="sxs-lookup"><span data-stu-id="b55fa-312">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="b55fa-313">Il est déconseillé d’utiliser la chaîne d’invite, qui doit être limitée aux scénarios destinés à illustrer l’usage de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b55fa-313">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="b55fa-314">Pour la plupart de ces exemples, la chaîne d’invite doit être `PS>`.</span><span class="sxs-lookup"><span data-stu-id="b55fa-314">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="b55fa-315">Cette invite est indépendante des indicateurs propres au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b55fa-315">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="b55fa-316">Les invites sont requises pour les exemples illustrant des commandes qui modifient l’invite ou lorsque le chemin affiché est significatif pour le scénario illustré.</span><span class="sxs-lookup"><span data-stu-id="b55fa-316">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="b55fa-317">L’exemple suivant montre comment l’invite change lorsque le fournisseur de registre est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b55fa-317">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="b55fa-318">Ne pas utiliser d’alias dans les exemples</span><span class="sxs-lookup"><span data-stu-id="b55fa-318">Do not use aliases in examples</span></span>

<span data-ttu-id="b55fa-319">Utilisez toujours le nom complet de toutes les cmdlets et de tous les paramètres, sauf si vous parlez spécifiquement de l’alias.</span><span class="sxs-lookup"><span data-stu-id="b55fa-319">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="b55fa-320">Les noms des cmdlets et des paramètres doivent être des noms utilisant la casse Pascal correcte.</span><span class="sxs-lookup"><span data-stu-id="b55fa-320">Cmdlet and parameter names must use the proper Pascal-cased names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="b55fa-321">Utiliser des paramètres dans les exemples</span><span class="sxs-lookup"><span data-stu-id="b55fa-321">Using parameters in examples</span></span>

<span data-ttu-id="b55fa-322">Évitez d’utiliser des paramètres positionnels.</span><span class="sxs-lookup"><span data-stu-id="b55fa-322">Avoid using positional parameters.</span></span> <span data-ttu-id="b55fa-323">En général, vous devez toujours inclure le nom du paramètre dans l’exemple, même s’il s’agit d’un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="b55fa-323">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="b55fa-324">Cela réduit le risque de confusion dans les exemples.</span><span class="sxs-lookup"><span data-stu-id="b55fa-324">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b55fa-325">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b55fa-325">Next steps</span></span>

[<span data-ttu-id="b55fa-326">Modification des informations de référence sur les cmdlets</span><span class="sxs-lookup"><span data-stu-id="b55fa-326">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
