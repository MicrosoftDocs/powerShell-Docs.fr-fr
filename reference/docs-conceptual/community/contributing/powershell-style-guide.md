---
title: Guide de style pour la documentation PowerShell
description: Cet article présente les règles de style pour l’écriture de la documentation de PowerShell.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99598548"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="7f763-103">Guide de style pour la documentation PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f763-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="7f763-104">Cet article donne des conseils de style propres au contenu PowerShell-Docs,</span><span class="sxs-lookup"><span data-stu-id="7f763-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="7f763-105">Il s’appuie sur les informations présentées dans la [vue d’ensemble](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="7f763-105">It builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="7f763-106">Terminologie des produits</span><span class="sxs-lookup"><span data-stu-id="7f763-106">Product Terminology</span></span>

<span data-ttu-id="7f763-107">Il existe plusieurs variantes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="7f763-108">**PowerShell** : terme par défaut.</span><span class="sxs-lookup"><span data-stu-id="7f763-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="7f763-109">Nous considérons PowerShell 7 et les versions ultérieures comme un véritable PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-109">We consider PowerShell 7 and beyond to be the one, true PowerShell.</span></span>
- <span data-ttu-id="7f763-110">**PowerShell Core** : PowerShell reposant sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f763-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="7f763-111">L’utilisation du terme **Core** doit être limitée aux cas où il est nécessaire de le différencier de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-111">Usage of the term **Core** should be limited to cases where it's necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="7f763-112">**Windows PowerShell** : PowerShell reposant sur .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7f763-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="7f763-113">Windows PowerShell est fourni uniquement sur Windows et requiert l’infrastructure complète.</span><span class="sxs-lookup"><span data-stu-id="7f763-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="7f763-114">En général, les références à « Windows PowerShell » dans la documentation peuvent être remplacées par _PowerShell_.</span><span class="sxs-lookup"><span data-stu-id="7f763-114">In general, references to "Windows PowerShell" in documentation can be changed to _PowerShell_.</span></span>
  <span data-ttu-id="7f763-115">« Windows PowerShell » doit être utilisé lorsque le comportement spécifique à _Windows PowerShell_ est abordé.</span><span class="sxs-lookup"><span data-stu-id="7f763-115">"Windows PowerShell" should be used when _Windows PowerShell_-specific behavior is being discussed.</span></span>

<span data-ttu-id="7f763-116">Produits connexes</span><span class="sxs-lookup"><span data-stu-id="7f763-116">Related products</span></span>

- <span data-ttu-id="7f763-117">**Visual Studio code (vs code)** : il s’agit de l’éditeur libre et open source de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7f763-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open-source editor.</span></span> <span data-ttu-id="7f763-118">Lors de la première mention, le nom complet doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="7f763-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="7f763-119">Après cela, vous pouvez utiliser **VS Code**.</span><span class="sxs-lookup"><span data-stu-id="7f763-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="7f763-120">N’utilisez pas « VSCode ».</span><span class="sxs-lookup"><span data-stu-id="7f763-120">Don't use "VSCode".</span></span>
- <span data-ttu-id="7f763-121">**Extension PowerShell pour Visual Studio Code** : l’extension active VS Code dans l’IDE préféré pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="7f763-122">Lors de la première mention, le nom complet doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="7f763-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="7f763-123">Après cela, vous pouvez utiliser **Extension PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="7f763-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="7f763-124">**Azure PowerShell** : il s’agit de la collection de modules PowerShell utilisés pour gérer les services Azure.</span><span class="sxs-lookup"><span data-stu-id="7f763-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="7f763-125">**Azure Stack PowerShell** : il s’agit de la collection de modules PowerShell utilisés pour gérer la solution cloud hybride de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7f763-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="7f763-126">Spécificités de Markdown</span><span class="sxs-lookup"><span data-stu-id="7f763-126">Markdown specifics</span></span>

<span data-ttu-id="7f763-127">Microsoft Open Publishing System (OPS), qui nous permet de créer notre documentation, utilise [markdig][] pour traiter les documents Markdown.</span><span class="sxs-lookup"><span data-stu-id="7f763-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="7f763-128">Markdig analyse les documents suivant les règles de la dernière spécification [CommonMark][].</span><span class="sxs-lookup"><span data-stu-id="7f763-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="7f763-129">La nouvelle spécification CommonMark est plus stricte sur la construction de certains éléments Markdown.</span><span class="sxs-lookup"><span data-stu-id="7f763-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="7f763-130">Portez une attention particulière aux informations fournies dans ce document.</span><span class="sxs-lookup"><span data-stu-id="7f763-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="7f763-131">Lignes vides, espaces et tabulations</span><span class="sxs-lookup"><span data-stu-id="7f763-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="7f763-132">Les lignes vides signalent également la fin d’un bloc en Markdown.</span><span class="sxs-lookup"><span data-stu-id="7f763-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="7f763-133">Il doit y avoir un seul espace entre les blocs Markdown de différents types (par exemple, entre un paragraphe et une liste ou un en-tête).</span><span class="sxs-lookup"><span data-stu-id="7f763-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="7f763-134">Plusieurs lignes vides consécutives sont rendues sous la forme d’une seule ligne vide en HTML.</span><span class="sxs-lookup"><span data-stu-id="7f763-134">Multiple consecutive blank lines render as a single blank line in HTML.</span></span> <span data-ttu-id="7f763-135">Ils n’ont aucun effet.</span><span class="sxs-lookup"><span data-stu-id="7f763-135">They serve no purpose.</span></span>
<span data-ttu-id="7f763-136">Dans un bloc de code, les lignes vides consécutives rompent le bloc de code.</span><span class="sxs-lookup"><span data-stu-id="7f763-136">Within a code block, consecutive blank lines break the code block.</span></span>

<span data-ttu-id="7f763-137">Supprimez les espaces supplémentaires à la fin des lignes.</span><span class="sxs-lookup"><span data-stu-id="7f763-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="7f763-138">L’espacement est significatif en Markdown.</span><span class="sxs-lookup"><span data-stu-id="7f763-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="7f763-139">Utilisez toujours des espaces plutôt que des tabulations fixes.</span><span class="sxs-lookup"><span data-stu-id="7f763-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="7f763-140">Les espaces de fin peuvent modifier le rendu Markdown.</span><span class="sxs-lookup"><span data-stu-id="7f763-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="7f763-141">Titres et en-têtes</span><span class="sxs-lookup"><span data-stu-id="7f763-141">Titles and headings</span></span>

<span data-ttu-id="7f763-142">Utilisez uniquement des [en-têtes ATX][atx] (de style #, par opposition aux en-têtes de style `=` ou `-`).</span><span class="sxs-lookup"><span data-stu-id="7f763-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="7f763-143">Seule la première lettre des phrases, des noms propres, des titres et des en-têtes doit être en majuscule.</span><span class="sxs-lookup"><span data-stu-id="7f763-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="7f763-144">Il doit y avoir un seul espace entre le `#` et la première lettre du titre.</span><span class="sxs-lookup"><span data-stu-id="7f763-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="7f763-145">Les en-têtes doivent être délimités par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="7f763-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="7f763-146">Un document ne peut contenir qu’un seul titre H1.</span><span class="sxs-lookup"><span data-stu-id="7f763-146">Only one H1 per document</span></span>
- <span data-ttu-id="7f763-147">Les niveaux d’en-têtes doivent se suivre par incréments de un,</span><span class="sxs-lookup"><span data-stu-id="7f763-147">Header levels should increment by one.</span></span> <span data-ttu-id="7f763-148">Ne pas ignorer les niveaux</span><span class="sxs-lookup"><span data-stu-id="7f763-148">Don't skip levels</span></span>
- <span data-ttu-id="7f763-149">N’utilisez pas le balisage gras ou autre dans les en-têtes</span><span class="sxs-lookup"><span data-stu-id="7f763-149">Don't use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="7f763-150">Limiter la longueur de ligne à 100 caractères</span><span class="sxs-lookup"><span data-stu-id="7f763-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="7f763-151">Cette règle s’applique aux articles conceptuels et aux informations de référence sur les cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7f763-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="7f763-152">Le fait de limiter la longueur de ligne améliore la lisibilité des différences et de l’historique de Git.</span><span class="sxs-lookup"><span data-stu-id="7f763-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="7f763-153">Elle permet également aux autres rédacteurs d’apporter plus facilement leur contribution.</span><span class="sxs-lookup"><span data-stu-id="7f763-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="7f763-154">Utilisez l’extension [Reflow Markdown][reflow] dans Visual Studio Code pour ajuster dynamiquement les paragraphes en fonction de la longueur de ligne prescrite.</span><span class="sxs-lookup"><span data-stu-id="7f763-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="7f763-155">Les rubriques About_ sont limitées à 80 caractères.</span><span class="sxs-lookup"><span data-stu-id="7f763-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="7f763-156">Pour plus d’informations, consultez [mise en forme des fichiers de about_](#formatting-about_-files).</span><span class="sxs-lookup"><span data-stu-id="7f763-156">For more specific information, see [Formatting About_ files](#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="7f763-157">Listes</span><span class="sxs-lookup"><span data-stu-id="7f763-157">Lists</span></span>

<span data-ttu-id="7f763-158">Si votre liste contient plusieurs phrases ou paragraphes, envisagez d’utiliser un en-tête de sous-niveau plutôt qu’une liste.</span><span class="sxs-lookup"><span data-stu-id="7f763-158">If your list contains multiple sentences or paragraphs, consider using a sublevel header rather than a list.</span></span>

<span data-ttu-id="7f763-159">Les listes doivent être délimitées par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="7f763-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="7f763-160">Listes non triées</span><span class="sxs-lookup"><span data-stu-id="7f763-160">Unordered lists</span></span>

<span data-ttu-id="7f763-161">Ne terminez pas les éléments de liste par un point, sauf s’ils contiennent plusieurs phrases.</span><span class="sxs-lookup"><span data-stu-id="7f763-161">Don't end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="7f763-162">Utilisez le caractère de trait d’union (`-`) comme puce pour les éléments de liste</span><span class="sxs-lookup"><span data-stu-id="7f763-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="7f763-163">afin d’éviter toute confusion avec les balises de type gras ou en italique qui utilisent l’astérisque [`*`].</span><span class="sxs-lookup"><span data-stu-id="7f763-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="7f763-164">Pour inclure un paragraphe ou d’autres éléments sous un élément de puce, insérez un saut de ligne et alignez le retrait avec le premier caractère après la puce.</span><span class="sxs-lookup"><span data-stu-id="7f763-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="7f763-165">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-165">For example:</span></span>

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="7f763-166">Il s’agit d’une liste qui contient des éléments enfants sous un élément de puce.</span><span class="sxs-lookup"><span data-stu-id="7f763-166">This is a list that contains child elements under a bullet item.</span></span>

- <span data-ttu-id="7f763-167">Premier élément de puce</span><span class="sxs-lookup"><span data-stu-id="7f763-167">First bullet item</span></span>

  <span data-ttu-id="7f763-168">Phrase expliquant la première puce.</span><span class="sxs-lookup"><span data-stu-id="7f763-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="7f763-169">Élément de puce enfant</span><span class="sxs-lookup"><span data-stu-id="7f763-169">Child bullet item</span></span>

    <span data-ttu-id="7f763-170">Phrase expliquant la puce enfant.</span><span class="sxs-lookup"><span data-stu-id="7f763-170">Sentence explaining the child bullet.</span></span>

- <span data-ttu-id="7f763-171">Deuxième élément de puce</span><span class="sxs-lookup"><span data-stu-id="7f763-171">Second bullet item</span></span>
- <span data-ttu-id="7f763-172">Troisième élément de puce</span><span class="sxs-lookup"><span data-stu-id="7f763-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="7f763-173">Listes triées</span><span class="sxs-lookup"><span data-stu-id="7f763-173">Ordered lists</span></span>

<span data-ttu-id="7f763-174">Pour inclure un paragraphe ou d’autres éléments sous un élément numéroté, alignez le retrait avec le premier caractère après le numéro d’élément.</span><span class="sxs-lookup"><span data-stu-id="7f763-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="7f763-175">Tous les éléments d’une liste numérotée doivent utiliser le numéro `1.` sans incrémentation.</span><span class="sxs-lookup"><span data-stu-id="7f763-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="7f763-176">Le rendu Markdown incrémente automatiquement la valeur,</span><span class="sxs-lookup"><span data-stu-id="7f763-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="7f763-177">ce qui permet de réorganiser plus facilement les éléments et standardise la mise en retrait du contenu subordonné.</span><span class="sxs-lookup"><span data-stu-id="7f763-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="7f763-178">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-178">For example:</span></span>

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

<span data-ttu-id="7f763-179">Le Markdown résultant est rendu de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="7f763-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="7f763-180">Pour le premier élément, insérez un seul espace après le 1.</span><span class="sxs-lookup"><span data-stu-id="7f763-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="7f763-181">Les phrases longues doivent comporter un retour automatique à la ligne et être alignées avec le premier caractère après le marqueur de liste numérotée.</span><span class="sxs-lookup"><span data-stu-id="7f763-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="7f763-182">Pour inclure un deuxième élément (comme celui-ci), insérez un saut de ligne après le premier et alignez les mises en retrait.</span><span class="sxs-lookup"><span data-stu-id="7f763-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="7f763-183">Le retrait du deuxième élément doit être aligné avec le premier caractère après le marqueur de liste numérotée.</span><span class="sxs-lookup"><span data-stu-id="7f763-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="7f763-184">Pour les éléments à un seul chiffre, comme celui-ci, la mise en retrait s’effectue vers la colonne 4.</span><span class="sxs-lookup"><span data-stu-id="7f763-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="7f763-185">Pour les éléments à deux chiffres, par exemple le numéro d’élément 10, elle s’effectue vers la colonne 5.</span><span class="sxs-lookup"><span data-stu-id="7f763-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="7f763-186">L’élément numéroté suivant commence ici.</span><span class="sxs-lookup"><span data-stu-id="7f763-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="7f763-187">Images</span><span class="sxs-lookup"><span data-stu-id="7f763-187">Images</span></span>

<span data-ttu-id="7f763-188">Voici la syntaxe permettant d’inclure une image :</span><span class="sxs-lookup"><span data-stu-id="7f763-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="7f763-189">Où `alt text` est une brève description de l’image et `<folder path>` le chemin relatif de l’image.</span><span class="sxs-lookup"><span data-stu-id="7f763-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="7f763-190">Le texte de remplacement est nécessaire pour les lecteurs d’écran des personnes déficientes visuelles.</span><span class="sxs-lookup"><span data-stu-id="7f763-190">Alternate text is required for screen readers for the visually impaired.</span></span>

<span data-ttu-id="7f763-191">Les images doivent être stockées dans un `media/<article-name>` dossier dans le dossier contenant l’article.</span><span class="sxs-lookup"><span data-stu-id="7f763-191">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="7f763-192">Ne partagez pas d’images entre des articles.</span><span class="sxs-lookup"><span data-stu-id="7f763-192">Don't share images between articles.</span></span> <span data-ttu-id="7f763-193">Créez un dossier qui correspond au nom de fichier de votre article sous le dossier `media`.</span><span class="sxs-lookup"><span data-stu-id="7f763-193">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="7f763-194">Copiez les images pour cet article dans ce nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="7f763-194">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="7f763-195">Si une image est utilisée par plusieurs articles, chaque dossier d’images doit avoir une copie de ce fichier d’image.</span><span class="sxs-lookup"><span data-stu-id="7f763-195">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="7f763-196">Cette pratique permet d’éviter que la modification d’une image dans un article affecte un autre article.</span><span class="sxs-lookup"><span data-stu-id="7f763-196">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="7f763-197">Les types de fichiers image suivants sont pris en charge : `*.png` , `*.gif` , `*.jpeg` , `*.jpg` , `*.svg`</span><span class="sxs-lookup"><span data-stu-id="7f763-197">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="7f763-198">Extensions Markdown prises en charge par Open Publishing</span><span class="sxs-lookup"><span data-stu-id="7f763-198">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="7f763-199">Le [Pack de création Microsoft docs](/contribute/how-to-write-docs-auth-pack) contient des outils qui prennent en charge des fonctionnalités propres à notre système de publication.</span><span class="sxs-lookup"><span data-stu-id="7f763-199">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="7f763-200">Les alertes sont une extension de démarque pour créer des citations qui s’affichent sur docs.microsoft.com avec des couleurs et des icônes qui mettent en évidence l’importance du contenu.</span><span class="sxs-lookup"><span data-stu-id="7f763-200">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="7f763-201">Les types d’alerte suivants sont pris en charge :</span><span class="sxs-lookup"><span data-stu-id="7f763-201">The following alert types are supported:</span></span>

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

<span data-ttu-id="7f763-202">Ces alertes ressemblent à ceci sur docs.microsoft.com :</span><span class="sxs-lookup"><span data-stu-id="7f763-202">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="7f763-203">Bloc de note</span><span class="sxs-lookup"><span data-stu-id="7f763-203">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="7f763-204">Information the user should notice even if skimming.</span><span class="sxs-lookup"><span data-stu-id="7f763-204">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="7f763-205">Bloc Tip</span><span class="sxs-lookup"><span data-stu-id="7f763-205">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="7f763-206">Optional information to help a user be more successful.</span><span class="sxs-lookup"><span data-stu-id="7f763-206">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="7f763-207">Bloc important</span><span class="sxs-lookup"><span data-stu-id="7f763-207">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f763-208">Essential information required for user success.</span><span class="sxs-lookup"><span data-stu-id="7f763-208">Essential information required for user success.</span></span>

<span data-ttu-id="7f763-209">AVERTISSEMENT-bloc</span><span class="sxs-lookup"><span data-stu-id="7f763-209">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="7f763-210">Negative potential consequences of an action.</span><span class="sxs-lookup"><span data-stu-id="7f763-210">Negative potential consequences of an action.</span></span>

<span data-ttu-id="7f763-211">Bloc d’avertissement</span><span class="sxs-lookup"><span data-stu-id="7f763-211">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="7f763-212">Certaines conséquences dangereuses d’une action.</span><span class="sxs-lookup"><span data-stu-id="7f763-212">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="7f763-213">Liens hypertexte</span><span class="sxs-lookup"><span data-stu-id="7f763-213">Hyperlinks</span></span>

- <span data-ttu-id="7f763-214">Les liens hypertexte doivent utiliser la syntaxe de la démarque `[friendlyname](url-or-path)` .</span><span class="sxs-lookup"><span data-stu-id="7f763-214">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`.</span></span> <span data-ttu-id="7f763-215">Les [références de liens][linkref] sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="7f763-215">[Link references][linkref] are supported.</span></span>
- <span data-ttu-id="7f763-216">Le système de publication prend en charge trois types de liens :</span><span class="sxs-lookup"><span data-stu-id="7f763-216">The publishing system supports three types of links:</span></span>
  - <span data-ttu-id="7f763-217">Liens URL</span><span class="sxs-lookup"><span data-stu-id="7f763-217">URL links</span></span>
  - <span data-ttu-id="7f763-218">Liens de fichiers</span><span class="sxs-lookup"><span data-stu-id="7f763-218">File links</span></span>
  - <span data-ttu-id="7f763-219">Liens de références croisées</span><span class="sxs-lookup"><span data-stu-id="7f763-219">Cross-reference links</span></span>
- <span data-ttu-id="7f763-220">Les liens vers d’autres articles sur docs.microsoft.com doivent être des chemins d’accès relatifs au site</span><span class="sxs-lookup"><span data-stu-id="7f763-220">Links to other articles on docs.microsoft.com must be site-relative paths</span></span>
- <span data-ttu-id="7f763-221">Toutes les URL vers des sites Web externes doivent utiliser le protocole HTTPs, sauf si elles ne sont pas valides pour le site cible.</span><span class="sxs-lookup"><span data-stu-id="7f763-221">All URLs to external websites should use HTTPS unless that isn't valid for the target site.</span></span>
- <span data-ttu-id="7f763-222">Les liens doivent avoir un nom convivial, généralement le titre de l’article lié</span><span class="sxs-lookup"><span data-stu-id="7f763-222">Links must have a friendly name, usually the title of the linked article</span></span>
- <span data-ttu-id="7f763-223">Tous les éléments de la section _liens connexes_ en bas doivent être liés par un lien hypertexte</span><span class="sxs-lookup"><span data-stu-id="7f763-223">All items in the _Related links_ section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="7f763-224">N’utilisez pas les surcycles, le gras ou tout autre balisage à l’intérieur des crochets d’un lien hypertexte.</span><span class="sxs-lookup"><span data-stu-id="7f763-224">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="7f763-225">Les URL complètes peuvent être utilisées lorsque vous documentez un URI spécifique.</span><span class="sxs-lookup"><span data-stu-id="7f763-225">Bare URLs may be used when you're documenting a specific URI.</span></span> <span data-ttu-id="7f763-226">L’URI doit être placé entre les battements.</span><span class="sxs-lookup"><span data-stu-id="7f763-226">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="7f763-227">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-227">For example:</span></span>

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a><span data-ttu-id="7f763-228">Liaison à d’autres contenus sur docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="7f763-228">Linking to other content on docs.microsoft.com</span></span>

- <span data-ttu-id="7f763-229">Les **liens URL** vers d’autres articles sur docs.Microsoft.com doivent être des chemins d’accès relatifs au site.</span><span class="sxs-lookup"><span data-stu-id="7f763-229">**URL links** to other articles on docs.microsoft.com must be site-relative paths.</span></span> <span data-ttu-id="7f763-230">La façon la plus simple de créer un lien relatif consiste à copier l’URL à partir de votre navigateur, puis `https://docs.microsoft.com/en-us` à supprimer de la valeur que vous collez dans démarque.</span><span class="sxs-lookup"><span data-stu-id="7f763-230">The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span> <span data-ttu-id="7f763-231">N’incluez pas de paramètres régionaux dans les URL sur les propriétés Microsoft (supprimer `/en-us` de l’URL).</span><span class="sxs-lookup"><span data-stu-id="7f763-231">Don't include locales in URLs on Microsoft properties (remove `/en-us` from URL).</span></span> <span data-ttu-id="7f763-232">Supprimez les paramètres de requête inutiles de l’URL.</span><span class="sxs-lookup"><span data-stu-id="7f763-232">Remove any unnecessary query parameters from the URL.</span></span> <span data-ttu-id="7f763-233">Exemples à supprimer :</span><span class="sxs-lookup"><span data-stu-id="7f763-233">Examples that should be removed:</span></span>

  - <span data-ttu-id="7f763-234">`?view=powershell-5.1` -utilisé pour établir une liaison à une version spécifique de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f763-234">`?view=powershell-5.1` - used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="7f763-235">`?redirectedfrom=MSDN` -ajouté à l’URL lorsque vous êtes Redirigé depuis un ancien article vers son nouvel emplacement</span><span class="sxs-lookup"><span data-stu-id="7f763-235">`?redirectedfrom=MSDN` - added to the URL when you get redirected from an old article to its new location</span></span>

  <span data-ttu-id="7f763-236">Si vous avez besoin de créer un lien vers une version spécifique d’un document, vous devez ajouter le `&preserve_view=true` paramètre à la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="7f763-236">If you need to link to a specific version of a document, then you need to add the `&preserve_view=true` parameter to the query string.</span></span> <span data-ttu-id="7f763-237">Par exemple : `?view=powershell-5.1&preserve_view=true`</span><span class="sxs-lookup"><span data-stu-id="7f763-237">For example: `?view=powershell-5.1&preserve_view=true`</span></span>

- <span data-ttu-id="7f763-238">Un **lien de fichier** est utilisé pour lier un article de référence à un autre, ou d’un article conceptuel à un autre.</span><span class="sxs-lookup"><span data-stu-id="7f763-238">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="7f763-239">Si vous avez besoin de créer un lien vers un article de référence pour une version spécifique de PowerShell, vous devez utiliser un lien URL.</span><span class="sxs-lookup"><span data-stu-id="7f763-239">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

  - <span data-ttu-id="7f763-240">Les liens de fichiers contiennent un chemin de fichier relatif (par exemple : `../folder/file.md` )</span><span class="sxs-lookup"><span data-stu-id="7f763-240">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
  - <span data-ttu-id="7f763-241">Tous les chemins d’accès aux fichiers utilisent des barres obliques ( `/` )</span><span class="sxs-lookup"><span data-stu-id="7f763-241">All file paths use forward-slash (`/`) characters</span></span>

- <span data-ttu-id="7f763-242">Les **liens de références croisées** sont une fonctionnalité spéciale prise en charge par le système de publication.</span><span class="sxs-lookup"><span data-stu-id="7f763-242">**Cross-reference links** are a special feature supported by the publishing system.</span></span> <span data-ttu-id="7f763-243">Vous pouvez utiliser des liens de référence croisée dans des articles conceptuels pour établir un lien vers l’API .NET ou une référence d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7f763-243">You can use cross-reference links in conceptual articles to link to .NET API or cmdlet reference.</span></span>

  <span data-ttu-id="7f763-244">Pour obtenir des liens vers des informations de référence sur les API .NET, consultez [utiliser les liens dans la documentation](/contribute/how-to-write-links#xref-cross-reference-links) du Guide du contributeur central.</span><span class="sxs-lookup"><span data-stu-id="7f763-244">For links to .NET API reference, see [Use links in documentation](/contribute/how-to-write-links#xref-cross-reference-links) in the central Contributor Guide.</span></span>

  <span data-ttu-id="7f763-245">Le format des liens vers la référence d’applet de commande est le suivant : `xref:<module-name>.<cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="7f763-245">Links to cmdlet reference have the following format: `xref:<module-name>.<cmdlet-name>`.</span></span> <span data-ttu-id="7f763-246">Par exemple, pour établir un lien vers l' `Get-Content` applet de commande dans le module **Microsoft. PowerShell. Management** .</span><span class="sxs-lookup"><span data-stu-id="7f763-246">For example, to link to the `Get-Content` cmdlet in the **Microsoft.PowerShell.Management** module.</span></span>

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

<span data-ttu-id="7f763-247">La liaison profonde est autorisée à la fois sur les liens d’URL et de fichiers.</span><span class="sxs-lookup"><span data-stu-id="7f763-247">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="7f763-248">Ajoutez l’ancre à la fin du chemin d’accès cible.</span><span class="sxs-lookup"><span data-stu-id="7f763-248">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="7f763-249">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-249">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="7f763-250">Pour plus d’informations, consultez [utiliser des liens dans la documentation](/contribute/how-to-write-links).</span><span class="sxs-lookup"><span data-stu-id="7f763-250">For more information, see [Use links in documentation](/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="7f763-251">Mise en forme des éléments de la syntaxe des commandes</span><span class="sxs-lookup"><span data-stu-id="7f763-251">Formatting command syntax elements</span></span>

- <span data-ttu-id="7f763-252">Utilisez toujours le nom complet pour les applets de commande et les paramètres.</span><span class="sxs-lookup"><span data-stu-id="7f763-252">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="7f763-253">Évitez d’utiliser des alias à moins que vous ne démontrant spécifiquement l’alias.</span><span class="sxs-lookup"><span data-stu-id="7f763-253">Avoid using aliases unless you're specifically demonstrating the alias.</span></span>

- <span data-ttu-id="7f763-254">La propriété, le paramètre, l’objet, les noms de types, les noms de classes, les méthodes de classe doivent être en **gras**.</span><span class="sxs-lookup"><span data-stu-id="7f763-254">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="7f763-255">Les valeurs des propriétés et des paramètres doivent être encapsulées dans les battements ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="7f763-255">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="7f763-256">Quand vous faites référence à des types à l’aide du style entre crochets, utilisez des battements.</span><span class="sxs-lookup"><span data-stu-id="7f763-256">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="7f763-257">Par exemple : `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="7f763-257">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="7f763-258">Les mots clés de langage, les noms d’applet de commande, les fonctions, les variables, les fichiers exe natifs, les chemins de fichiers et les exemples de syntaxe Inline doivent être encapsulés dans les caractères de soulignement ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="7f763-258">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="7f763-259">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-259">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="7f763-260">Quand vous faites référence à un paramètre par son nom, le nom doit être en **gras**.</span><span class="sxs-lookup"><span data-stu-id="7f763-260">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="7f763-261">Lors de l’illustration de l’utilisation d’un paramètre avec le préfixe de trait d’union, le paramètre doit être entouré d’accents graves.</span><span class="sxs-lookup"><span data-stu-id="7f763-261">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="7f763-262">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-262">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="7f763-263">Quand vous montrez un exemple d’utilisation d’une commande externe, l’exemple doit être entouré d’accents graves.</span><span class="sxs-lookup"><span data-stu-id="7f763-263">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="7f763-264">Incluez toujours l’extension de fichier dans la commande native.</span><span class="sxs-lookup"><span data-stu-id="7f763-264">Always include the file extension in the native command.</span></span> <span data-ttu-id="7f763-265">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-265">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="7f763-266">L’inclusion de l’extension de fichier garantit que la commande correcte est exécutée en fonction de la priorité des commandes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-266">Including the file extension ensures that the correct command is executed according to PowerShell's command precedence.</span></span>

- <span data-ttu-id="7f763-267">Lors de l’écriture d’un article conceptuel (par opposition au contenu des informations de référence), la première occurrence du nom d’une applet de commande doit avoir un lien hypertexte vers la documentation de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7f763-267">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="7f763-268">N’utilisez pas les surcycles, le gras ou tout autre balisage à l’intérieur des crochets d’un lien hypertexte.</span><span class="sxs-lookup"><span data-stu-id="7f763-268">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="7f763-269">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-269">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="7f763-270">Pour plus d’informations, consultez la section [liens hypertexte](#hyperlinks) de cet article.</span><span class="sxs-lookup"><span data-stu-id="7f763-270">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="7f763-271">Démarque pour les exemples de code</span><span class="sxs-lookup"><span data-stu-id="7f763-271">Markdown for code samples</span></span>

<span data-ttu-id="7f763-272">Markdown prend en charge deux styles de code différents :</span><span class="sxs-lookup"><span data-stu-id="7f763-272">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="7f763-273">**Étendues de code (Inline)** -marquées d’un seul caractère de soulignement ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="7f763-273">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="7f763-274">Utilisé dans un paragraphe plutôt qu’en tant que bloc autonome.</span><span class="sxs-lookup"><span data-stu-id="7f763-274">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="7f763-275">**Blocs de code** : bloc à plusieurs lignes entouré de chaînes triple-Tick ( `` ``` `` ).</span><span class="sxs-lookup"><span data-stu-id="7f763-275">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="7f763-276">Les blocs de code peuvent également avoir une étiquette de langue après les battements.</span><span class="sxs-lookup"><span data-stu-id="7f763-276">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="7f763-277">L’étiquette de langage active la mise en surbrillance de la syntaxe pour le contenu du bloc de code.</span><span class="sxs-lookup"><span data-stu-id="7f763-277">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="7f763-278">Tous les blocs de code doivent être entourés d’une délimitation de code.</span><span class="sxs-lookup"><span data-stu-id="7f763-278">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="7f763-279">N’utilisez jamais la mise en retrait pour les blocs de code.</span><span class="sxs-lookup"><span data-stu-id="7f763-279">Never use indentation for code blocks.</span></span> <span data-ttu-id="7f763-280">La démarque autorise ce modèle, mais elle peut être problématique et doit être évitée.</span><span class="sxs-lookup"><span data-stu-id="7f763-280">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="7f763-281">Un bloc de code est une ou plusieurs lignes de code entourées d’une délimitation de code triple-Tick ( `` ``` `` ).</span><span class="sxs-lookup"><span data-stu-id="7f763-281">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="7f763-282">Les marqueurs de délimitation de code doivent se trouver sur leur propre ligne avant et après l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="7f763-282">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="7f763-283">Le marqueur au début du bloc de code peut avoir une étiquette de langage facultative.</span><span class="sxs-lookup"><span data-stu-id="7f763-283">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="7f763-284">Le système de publication OPS de Microsoft utilise l’étiquette de langage pour prendre en charge la fonctionnalité de mise en surbrillance de la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7f763-284">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="7f763-285">Pour obtenir la liste complète des balises de langue prises en charge, consultez [blocs de code](/contribute/code-in-docs#fenced-code-blocks) délimités dans le Guide du contributeur centralisé.</span><span class="sxs-lookup"><span data-stu-id="7f763-285">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="7f763-286">OPS ajoute également un bouton de **Copie** qui copie le contenu du bloc de code dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="7f763-286">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="7f763-287">Cela vous permet de coller rapidement le code dans un script pour tester l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="7f763-287">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="7f763-288">Toutefois, tous les exemples de notre documentation ne sont pas destinés à être exécutés en l’absence.</span><span class="sxs-lookup"><span data-stu-id="7f763-288">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="7f763-289">Certains blocs de code sont des illustrations simples d’un concept PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-289">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="7f763-290">Il existe trois types de blocs de code utilisés dans notre documentation :</span><span class="sxs-lookup"><span data-stu-id="7f763-290">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="7f763-291">Blocs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f763-291">Syntax blocks</span></span>
1. <span data-ttu-id="7f763-292">Exemples servant d’illustration</span><span class="sxs-lookup"><span data-stu-id="7f763-292">Illustrative examples</span></span>
1. <span data-ttu-id="7f763-293">Exemples exécutables</span><span class="sxs-lookup"><span data-stu-id="7f763-293">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="7f763-294">Blocs de code de syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f763-294">Syntax code blocks</span></span>

<span data-ttu-id="7f763-295">Les blocs de code de syntaxe sont utilisés pour décrire la structure syntaxique d’une commande.</span><span class="sxs-lookup"><span data-stu-id="7f763-295">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="7f763-296">N’utilisez pas de balise de langue sur la clôture du code.</span><span class="sxs-lookup"><span data-stu-id="7f763-296">Don't use a language tag on the code fence.</span></span> <span data-ttu-id="7f763-297">Cet exemple illustre tous les paramètres possibles de l’applet de commande `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="7f763-297">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="7f763-298">Cet exemple décrit l’instruction `for` en termes généralisés :</span><span class="sxs-lookup"><span data-stu-id="7f763-298">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="7f763-299">Exemples illustratifs</span><span class="sxs-lookup"><span data-stu-id="7f763-299">Illustrative examples</span></span>

<span data-ttu-id="7f763-300">Des exemples illustratifs sont utilisés pour expliquer un concept PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-300">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="7f763-301">Elles ne sont pas destinées à être copiées dans le presse-papiers pour être exécutées.</span><span class="sxs-lookup"><span data-stu-id="7f763-301">They aren't meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="7f763-302">Celles-ci sont le plus souvent utilisées pour des exemples simples faciles à saisir et faciles à comprendre.</span><span class="sxs-lookup"><span data-stu-id="7f763-302">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="7f763-303">Le bloc de code peut inclure l’invite PowerShell et l’exemple de sortie.</span><span class="sxs-lookup"><span data-stu-id="7f763-303">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="7f763-304">Voici un exemple simple illustrant les opérateurs de comparaison PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-304">Here's a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="7f763-305">Dans ce cas, nous ne prévoyons pas que le lecteur copie cet exemple et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="7f763-305">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="7f763-306">Exemples exécutables</span><span class="sxs-lookup"><span data-stu-id="7f763-306">Executable examples</span></span>

<span data-ttu-id="7f763-307">Les exemples complexes, ou des exemples destinés à être copiés et exécutés, doivent utiliser le balisage de style bloc suivant :</span><span class="sxs-lookup"><span data-stu-id="7f763-307">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="7f763-308">La sortie affichée par les commandes PowerShell doit être placée dans un bloc de code **Output** (Sortie) pour empêcher la mise en surbrillance de la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7f763-308">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="7f763-309">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-309">For example:</span></span>

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

<span data-ttu-id="7f763-310">L’étiquette du code de **sortie** n’est pas une « langue » officielle prise en charge par le système de mise en surbrillance de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7f763-310">The **Output** code label isn't an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="7f763-311">Toutefois, cette étiquette est utile, car OPS ajoute l’étiquette « sortie » au cadre de la zone de code sur la page Web.</span><span class="sxs-lookup"><span data-stu-id="7f763-311">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="7f763-312">La zone de code « sortie » n’a pas de mise en surbrillance syntaxique.</span><span class="sxs-lookup"><span data-stu-id="7f763-312">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="7f763-313">Règles de style pour le code</span><span class="sxs-lookup"><span data-stu-id="7f763-313">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="7f763-314">Éviter les continuations de ligne dans les exemples de code</span><span class="sxs-lookup"><span data-stu-id="7f763-314">Avoid line continuation in code samples</span></span>

<span data-ttu-id="7f763-315">Évitez d’utiliser les caractères de continuation de ligne (`` ` ``) dans les exemples de code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f763-315">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="7f763-316">Ils sont difficiles à voir et peuvent provoquer des problèmes s’il existe des espaces supplémentaires à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="7f763-316">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="7f763-317">Utilisez la projection PowerShell pour réduire la longueur de ligne des applets de commande qui ont plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="7f763-317">Use PowerShell splatting to reduce line length for cmdlets that have several parameters.</span></span>
- <span data-ttu-id="7f763-318">Tirez parti des opportunités de saut de ligne naturel de PowerShell, comme après les caractères de barre verticale () `|` , les accolades ouvrantes ( `{` ), les parenthèses ( `(` ) et les crochets ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="7f763-318">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces (`{`), parentheses (`(`), and brackets (`[`).</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="7f763-319">Évitez d’utiliser les invites PowerShell dans les exemples.</span><span class="sxs-lookup"><span data-stu-id="7f763-319">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="7f763-320">L’utilisation de la chaîne d’invite est déconseillée et doit être limitée aux scénarios qui sont destinés à illustrer l’utilisation de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="7f763-320">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command-line usage.</span></span> <span data-ttu-id="7f763-321">Pour la plupart de ces exemples, la chaîne d’invite doit être `PS>` .</span><span class="sxs-lookup"><span data-stu-id="7f763-321">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="7f763-322">Cette invite est indépendante des indicateurs spécifiques au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7f763-322">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="7f763-323">Les invites sont requises dans des exemples pour illustrer les commandes qui modifient l’invite ou lorsque le chemin d’accès affiché est significatif pour le scénario.</span><span class="sxs-lookup"><span data-stu-id="7f763-323">Prompts are required in examples to illustrate commands that alter the prompt or when the path displayed is significant to the scenario.</span></span> <span data-ttu-id="7f763-324">L’exemple suivant montre comment l’invite change lors de l’utilisation du fournisseur de Registre.</span><span class="sxs-lookup"><span data-stu-id="7f763-324">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="dont-use-aliases-in-examples"></a><span data-ttu-id="7f763-325">N’utilisez pas d’alias dans des exemples</span><span class="sxs-lookup"><span data-stu-id="7f763-325">Don't use aliases in examples</span></span>

<span data-ttu-id="7f763-326">Utilisez le nom complet de l’ensemble des applets de commande et des paramètres, sauf si vous documentez spécifiquement l’alias.</span><span class="sxs-lookup"><span data-stu-id="7f763-326">Use the full name of all cmdlets and parameters unless you're specifically documenting the alias.</span></span>
<span data-ttu-id="7f763-327">Les noms des applets de commande et des paramètres doivent utiliser les noms appropriés [en respectant la casse][] .</span><span class="sxs-lookup"><span data-stu-id="7f763-327">Cmdlet and parameter names must use the proper [Pascal-cased][] names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="7f763-328">Utilisation de paramètres dans les exemples</span><span class="sxs-lookup"><span data-stu-id="7f763-328">Using parameters in examples</span></span>

<span data-ttu-id="7f763-329">Évitez d’utiliser des paramètres positionnels</span><span class="sxs-lookup"><span data-stu-id="7f763-329">Avoid using positional parameters.</span></span> <span data-ttu-id="7f763-330">En général, vous devez toujours inclure le nom du paramètre dans un exemple, même si le paramètre est positionnel.</span><span class="sxs-lookup"><span data-stu-id="7f763-330">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="7f763-331">Ceci réduit le risque de confusion dans vos exemples.</span><span class="sxs-lookup"><span data-stu-id="7f763-331">This reduces the chance of confusion in your examples.</span></span>

## <a name="formatting-cmdlet-reference-articles"></a><span data-ttu-id="7f763-332">Articles de référence sur les applets de commande mise en forme</span><span class="sxs-lookup"><span data-stu-id="7f763-332">Formatting cmdlet reference articles</span></span>

<span data-ttu-id="7f763-333">Les articles de référence sur les applets de commande ont une structure spécifique.</span><span class="sxs-lookup"><span data-stu-id="7f763-333">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="7f763-334">Cette structure est définie par [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="7f763-334">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="7f763-335">PlatyPS génère l’aide de l’applet de commande pour les modules PowerShell dans la démarque.</span><span class="sxs-lookup"><span data-stu-id="7f763-335">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="7f763-336">Une fois les fichiers Markdown modifiés, PlatyPS est utilisé pour créer les fichiers d’aide MAML utilisés par l’applet de commande `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="7f763-336">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="7f763-337">PlatyPS un schéma codé en dur pour les informations de référence des applets de commande qui sont écrites dans le code.</span><span class="sxs-lookup"><span data-stu-id="7f763-337">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="7f763-338">Le document [platyPS.schema.md][] décrit cette structure.</span><span class="sxs-lookup"><span data-stu-id="7f763-338">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="7f763-339">Les violations du schéma entraînent des erreurs de génération, qui doivent être corrigées avant que nous puissions accepter votre contribution.</span><span class="sxs-lookup"><span data-stu-id="7f763-339">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

- <span data-ttu-id="7f763-340">Ne supprimez pas les structures d’en-tête ATX.</span><span class="sxs-lookup"><span data-stu-id="7f763-340">Don't remove any of the ATX header structures.</span></span> <span data-ttu-id="7f763-341">PlatyPS attend un ensemble spécifique d’en-têtes.</span><span class="sxs-lookup"><span data-stu-id="7f763-341">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="7f763-342">Les en-têtes **Input type** et **Output type** doivent avoir un type.</span><span class="sxs-lookup"><span data-stu-id="7f763-342">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="7f763-343">Si l’applet de commande ne prend pas d’entrée ou ne retourne pas de valeur, utilisez la valeur `None` .</span><span class="sxs-lookup"><span data-stu-id="7f763-343">If the cmdlet doesn't take input or return a value, then use the value `None`.</span></span>
- <span data-ttu-id="7f763-344">Les étendues de code inline peuvent être utilisées dans n’importe quel paragraphe.</span><span class="sxs-lookup"><span data-stu-id="7f763-344">Inline code spans can be used in any paragraph.</span></span>
- <span data-ttu-id="7f763-345">Les blocs de code délimités sont autorisés uniquement dans la section **exemples** .</span><span class="sxs-lookup"><span data-stu-id="7f763-345">Fenced code blocks are only allowed in the **EXAMPLES** section.</span></span>

<span data-ttu-id="7f763-346">Dans le schéma PlatyPS, des **exemples** sont un en-tête H2.</span><span class="sxs-lookup"><span data-stu-id="7f763-346">In the PlatyPS schema, **EXAMPLES** is an H2 header.</span></span> <span data-ttu-id="7f763-347">Chaque exemple est un en-tête H3.</span><span class="sxs-lookup"><span data-stu-id="7f763-347">Each example is an H3 header.</span></span> <span data-ttu-id="7f763-348">Dans un exemple, le schéma n’autorise pas la séparation des blocs de code par des paragraphes.</span><span class="sxs-lookup"><span data-stu-id="7f763-348">Within an example, the schema doesn't allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="7f763-349">Le schéma autorise la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="7f763-349">The schema allows the following structure:</span></span>

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="7f763-350">Numérotez chaque exemple et ajoutez un titre court.</span><span class="sxs-lookup"><span data-stu-id="7f763-350">Number each example and add a brief title.</span></span>

<span data-ttu-id="7f763-351">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-351">For example:</span></span>

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a><span data-ttu-id="7f763-352">Mise en forme des fichiers About_</span><span class="sxs-lookup"><span data-stu-id="7f763-352">Formatting About_ files</span></span>

<span data-ttu-id="7f763-353">`About_*` les fichiers sont écrits dans la démarque mais sont fournis en tant que fichiers texte bruts.</span><span class="sxs-lookup"><span data-stu-id="7f763-353">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="7f763-354">Nous utilisons [pandoc][] pour convertir la démarque en texte brut.</span><span class="sxs-lookup"><span data-stu-id="7f763-354">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="7f763-355">`About_*` les fichiers sont mis en forme pour une meilleure compatibilité dans toutes les versions de PowerShell et avec les outils de publication.</span><span class="sxs-lookup"><span data-stu-id="7f763-355">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="7f763-356">Instructions de mise en forme de base :</span><span class="sxs-lookup"><span data-stu-id="7f763-356">Basic formatting guidelines:</span></span>

- <span data-ttu-id="7f763-357">Limiter les lignes normales à 80 caractères</span><span class="sxs-lookup"><span data-stu-id="7f763-357">Limit normal lines to 80 characters</span></span>
- <span data-ttu-id="7f763-358">Les blocs de code sont limités à 76 caractères</span><span class="sxs-lookup"><span data-stu-id="7f763-358">Code blocks are limited to 76 characters</span></span>
- <span data-ttu-id="7f763-359">Citations (et les alertes) sont des 78 caractères limités</span><span class="sxs-lookup"><span data-stu-id="7f763-359">Blockquotes (and Alerts) are limited 78 characters</span></span>
- <span data-ttu-id="7f763-360">Quand vous utilisez ces méta-caractères spéciaux `\` , `$` , et `<` :</span><span class="sxs-lookup"><span data-stu-id="7f763-360">When using these special meta-characters `\`,`$`, and `<`:</span></span>
  - <span data-ttu-id="7f763-361">Dans un en-tête, ces caractères doivent être placés dans une séquence d’échappement à l’aide d’un `\` caractère de début ou placés entre des étendues de code à l’aide des battements ( `` ` `` )</span><span class="sxs-lookup"><span data-stu-id="7f763-361">Within a header, these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="7f763-362">Dans un paragraphe, ces caractères doivent être placés dans des étendues de code.</span><span class="sxs-lookup"><span data-stu-id="7f763-362">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="7f763-363">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7f763-363">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="7f763-364">Les tables doivent tenir dans 76 caractères</span><span class="sxs-lookup"><span data-stu-id="7f763-364">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="7f763-365">Renvoyez manuellement à la ligne le contenu des cellules sur plusieurs lignes</span><span class="sxs-lookup"><span data-stu-id="7f763-365">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="7f763-366">Utilisez des caractères `|` d’ouverture et de fermeture sur chaque ligne</span><span class="sxs-lookup"><span data-stu-id="7f763-366">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="7f763-367">L’exemple suivant montre comment construire correctement une table qui contient des informations qui s’encapsulent sur plusieurs lignes dans une cellule.</span><span class="sxs-lookup"><span data-stu-id="7f763-367">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > <span data-ttu-id="7f763-368">La limitation de 76 colonnes s’applique uniquement aux `About_*` rubriques.</span><span class="sxs-lookup"><span data-stu-id="7f763-368">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="7f763-369">Vous pouvez utiliser des colonnes larges dans des Articles de référence conceptuelles ou d’applets de commande.</span><span class="sxs-lookup"><span data-stu-id="7f763-369">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7f763-370">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7f763-370">Next steps</span></span>

[<span data-ttu-id="7f763-371">Liste de contrôle éditoriale</span><span class="sxs-lookup"><span data-stu-id="7f763-371">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[Casse Pascal]: https://en.wikipedia.org/wiki/PascalCase
[Pascal-cased]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
