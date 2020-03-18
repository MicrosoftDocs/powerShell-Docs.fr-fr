---
title: Guide de style pour la documentation PowerShell
description: Cet article présente les règles de style pour l’écriture de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 964536c5195c3bb8abd98b5996a96fc7b9362489
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402576"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="e4ecc-103">Guide de style pour la documentation PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4ecc-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="e4ecc-104">Cet article donne des conseils de style propres au contenu PowerShell-Docs,</span><span class="sxs-lookup"><span data-stu-id="e4ecc-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="e4ecc-105">qui s’appuient sur les informations présentées dans la [Vue d’ensemble](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="e4ecc-106">Terminologie des produits</span><span class="sxs-lookup"><span data-stu-id="e4ecc-106">Product Terminology</span></span>

<span data-ttu-id="e4ecc-107">Il existe plusieurs variantes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-107">There are several variants of PowerShell.</span></span>
<span data-ttu-id="e4ecc-108">Ce tableau définit certains des termes utilisés pour parler de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-108">This table defines some of the different terms used to discuss PowerShell.</span></span>

- <span data-ttu-id="e4ecc-109">**PowerShell** : terme par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-109">**PowerShell** - This is the default.</span></span> <span data-ttu-id="e4ecc-110">Nous considérons la version 7 et les versions ultérieures de PowerShell comme le vrai PowerShell, à ce jour et à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-110">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>

- <span data-ttu-id="e4ecc-111">**PowerShell Core** : PowerShell reposant sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-111">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="e4ecc-112">L’utilisation du terme **Core** doit être limitée aux cas où il est nécessaire de le différencier de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-112">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>

- <span data-ttu-id="e4ecc-113">**Windows PowerShell** : PowerShell reposant sur .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-113">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="e4ecc-114">Windows PowerShell est fourni uniquement sur Windows et requiert l’infrastructure complète.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-114">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

<span data-ttu-id="e4ecc-115">En général, les références à « Windows PowerShell » dans la documentation peuvent être remplacées par « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="e4ecc-115">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
<span data-ttu-id="e4ecc-116">« Windows PowerShell » ne doit **pas** être modifié lorsque l’on aborde les technologies propres à Windows.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-116">"Windows PowerShell" should **not** be changed when Windows-specific technology is being discussed.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="e4ecc-117">Spécificités de Markdown</span><span class="sxs-lookup"><span data-stu-id="e4ecc-117">Markdown specifics</span></span>

<span data-ttu-id="e4ecc-118">Microsoft Open Publishing System (OPS), qui nous permet de créer notre documentation, utilise [markdig][] pour traiter les documents Markdown.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-118">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="e4ecc-119">Markdig analyse les documents suivant les règles de la dernière spécification [CommonMark][].</span><span class="sxs-lookup"><span data-stu-id="e4ecc-119">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="e4ecc-120">La nouvelle spécification CommonMark est plus stricte sur la construction de certains éléments Markdown.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-120">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="e4ecc-121">Portez une attention particulière aux informations fournies dans ce document.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-121">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="e4ecc-122">Lignes vides, espaces et tabulations</span><span class="sxs-lookup"><span data-stu-id="e4ecc-122">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="e4ecc-123">Supprimez les lignes vides en double.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-123">Remove duplicate blank lines.</span></span> <span data-ttu-id="e4ecc-124">S’il existe plusieurs lignes vides, elles s’affichent comme une seule ligne vide en HTML ; il n’y a donc pas d’intérêt à en insérer plusieurs.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-124">Multiple blank lines render as a single blank line in HTML so there is not purpose for multiple blank lines.</span></span>

<span data-ttu-id="e4ecc-125">Les lignes vides signalent également la fin d’un bloc en Markdown.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-125">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="e4ecc-126">Il doit y avoir un seul espace entre les blocs Markdown de différents types (par exemple, entre un paragraphe et une liste ou un en-tête).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-126">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

> [!NOTE]
> <span data-ttu-id="e4ecc-127">L’espacement est significatif en Markdown.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-127">Spacing is significant in Markdown.</span></span> <span data-ttu-id="e4ecc-128">Utilisez toujours des espaces plutôt que des tabulations fixes.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-128">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="e4ecc-129">Supprimez les espaces supplémentaires à la fin des lignes.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-129">Remove extra spaces at the end of lines.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="e4ecc-130">Titres et en-têtes</span><span class="sxs-lookup"><span data-stu-id="e4ecc-130">Titles and headings</span></span>

<span data-ttu-id="e4ecc-131">Utilisez uniquement des [en-têtes ATX][atx] (de style #, par opposition aux en-têtes de style `=` ou `-`).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-131">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="e4ecc-132">Seule la première lettre des phrases, des noms propres, des titres et des en-têtes doit être en majuscule.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-132">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="e4ecc-133">Il doit y avoir un seul espace entre le `#` et la première lettre du titre.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-133">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="e4ecc-134">Les en-têtes doivent être délimités par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-134">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="e4ecc-135">Un document ne peut contenir qu’un seul titre H1.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-135">Only one H1 per document</span></span>
- <span data-ttu-id="e4ecc-136">Les niveaux d’en-têtes doivent se suivre par incréments de un,</span><span class="sxs-lookup"><span data-stu-id="e4ecc-136">Header levels should increment by one.</span></span> <span data-ttu-id="e4ecc-137">sans qu’un niveau soit ignoré.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-137">Do not skip levels</span></span>
- <span data-ttu-id="e4ecc-138">N’utilisez pas de balises de type gras ou autre dans les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-138">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="e4ecc-139">Limiter la longueur de ligne à 100 caractères</span><span class="sxs-lookup"><span data-stu-id="e4ecc-139">Limit line length to 100 characters</span></span>

<span data-ttu-id="e4ecc-140">Cette règle s’applique aux articles conceptuels et aux informations de référence sur les cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-140">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="e4ecc-141">Les rubriques About_ sont limitées à 80 caractères.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-141">About_topics are limited to 80 characters.</span></span>
<span data-ttu-id="e4ecc-142">Le fait de limiter la longueur de ligne améliore la lisibilité des différences et de l’historique de Git.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-142">Limiting the line length improves the readability git diffs and history.</span></span> <span data-ttu-id="e4ecc-143">Elle permet également aux autres rédacteurs d’apporter plus facilement leur contribution.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-143">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="e4ecc-144">Utilisez l’extension [Reflow Markdown][reflow] dans Visual Studio Code pour ajuster dynamiquement les paragraphes en fonction de la longueur de ligne prescrite.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-144">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

### <a name="lists"></a><span data-ttu-id="e4ecc-145">Listes</span><span class="sxs-lookup"><span data-stu-id="e4ecc-145">Lists</span></span>

<span data-ttu-id="e4ecc-146">Si votre liste contient plusieurs phrases ou paragraphes, utilisez de préférence un en-tête de sous-niveau plutôt qu’une liste.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-146">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="e4ecc-147">Les listes doivent être délimitées par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-147">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="e4ecc-148">Listes non triées</span><span class="sxs-lookup"><span data-stu-id="e4ecc-148">Unordered lists</span></span>

<span data-ttu-id="e4ecc-149">Les éléments de liste ne doivent pas se terminer par un point, sauf s’ils contiennent plusieurs phrases.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-149">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="e4ecc-150">Utilisez le caractère de trait d’union (`-`) comme puce pour les éléments de liste</span><span class="sxs-lookup"><span data-stu-id="e4ecc-150">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="e4ecc-151">afin d’éviter toute confusion avec les balises de type gras ou en italique qui utilisent l’astérisque [`*`].</span><span class="sxs-lookup"><span data-stu-id="e4ecc-151">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="e4ecc-152">Pour inclure un paragraphe ou d’autres éléments sous un élément de puce, insérez un saut de ligne et alignez le retrait avec le premier caractère après la puce.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-152">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="e4ecc-153">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-153">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="e4ecc-154">Voici une liste qui contient des sous-éléments sous un élément de puce.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-154">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="e4ecc-155">Premier élément de puce</span><span class="sxs-lookup"><span data-stu-id="e4ecc-155">First bullet item</span></span>

  <span data-ttu-id="e4ecc-156">Phrase expliquant la première puce.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-156">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="e4ecc-157">Élément de puce de niveau inférieur</span><span class="sxs-lookup"><span data-stu-id="e4ecc-157">Sub-bullet item</span></span>

    <span data-ttu-id="e4ecc-158">Phrase expliquant la puce de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-158">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="e4ecc-159">Deuxième élément de puce</span><span class="sxs-lookup"><span data-stu-id="e4ecc-159">Second bullet item</span></span>
- <span data-ttu-id="e4ecc-160">Troisième élément de puce</span><span class="sxs-lookup"><span data-stu-id="e4ecc-160">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="e4ecc-161">Listes triées</span><span class="sxs-lookup"><span data-stu-id="e4ecc-161">Ordered lists</span></span>

<span data-ttu-id="e4ecc-162">Pour inclure un paragraphe ou d’autres éléments sous un élément numéroté, alignez le retrait avec le premier caractère après le numéro d’élément.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-162">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="e4ecc-163">Tous les éléments d’une liste numérotée doivent utiliser le numéro `1.` sans incrémentation.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-163">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="e4ecc-164">Le rendu Markdown incrémente automatiquement la valeur,</span><span class="sxs-lookup"><span data-stu-id="e4ecc-164">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="e4ecc-165">ce qui permet de réorganiser plus facilement les éléments et standardise la mise en retrait du contenu subordonné.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-165">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="e4ecc-166">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-166">For example:</span></span>

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

<span data-ttu-id="e4ecc-167">Le Markdown résultant est rendu de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-167">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="e4ecc-168">Pour le premier élément, insérez un seul espace après le 1.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-168">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="e4ecc-169">Les phrases longues doivent comporter un retour automatique à la ligne et être alignées avec le premier caractère après le marqueur de liste numérotée.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-169">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="e4ecc-170">Pour inclure un deuxième élément (comme celui-ci), insérez un saut de ligne après le premier et alignez les mises en retrait.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-170">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="e4ecc-171">Le retrait du deuxième élément doit être aligné avec le premier caractère après le marqueur de liste numérotée.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-171">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="e4ecc-172">Pour les éléments à un seul chiffre, comme celui-ci, la mise en retrait s’effectue vers la colonne 4.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-172">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="e4ecc-173">Pour les éléments à deux chiffres, par exemple le numéro d’élément 10, elle s’effectue vers la colonne 5.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-173">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="e4ecc-174">L’élément numéroté suivant commence ici.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-174">The next numbered item starts here.</span></span>

### <a name="formatting-command-syntax-elements"></a><span data-ttu-id="e4ecc-175">Mise en forme des éléments de syntaxe de commande</span><span class="sxs-lookup"><span data-stu-id="e4ecc-175">Formatting command syntax elements</span></span>

- <span data-ttu-id="e4ecc-176">Utilisez toujours le nom complet pour les cmdlets et les paramètres.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-176">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="e4ecc-177">Évitez d’utiliser des alias à moins qu’il ne s’agisse spécifiquement d’une démonstration des alias.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-177">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="e4ecc-178">Dans un paragraphe, les mots clés de langage, les noms de cmdlets, les variables et les chemins de fichiers doivent être placés entre accents graves (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-178">Within a paragraph, language keywords, cmdlet names, variables, and file paths should be wrapped in backtick (`` ` ``) characters.</span></span> <span data-ttu-id="e4ecc-179">Les noms de propriétés, de paramètres et de classes doivent être en **gras**.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-179">Property, parameter, and class names should be **bold**.</span></span>

  <span data-ttu-id="e4ecc-180">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-180">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- <span data-ttu-id="e4ecc-181">En cas de référence à un paramètre par son nom, ce nom doit être en **gras**.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-181">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="e4ecc-182">Pour illustrer l’utilisation d’un paramètre avec le préfixe de trait d’union, ce paramètre doit être placé entre accents graves.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-182">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="e4ecc-183">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-183">For example:</span></span>

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- <span data-ttu-id="e4ecc-184">En cas de référence à des commandes externes (exe, scripts, etc.), le nom de la commande doit être en gras, tout en minuscules (ou avec une majuscule s’il se trouve au début d’une phrase) et avec l’extension de fichier correspondante.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-184">When referring to external commands (EXEs, scripts, etc.), the command name should be bold, all lowercase (or capitalized if at the beginning of a sentence), and include the appropriate file extension.</span></span> <span data-ttu-id="e4ecc-185">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-185">For example:</span></span>

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- <span data-ttu-id="e4ecc-186">Pour montrer l’utilisation d’une commande externe, l’exemple doit être placé entre accents graves.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-186">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
  <span data-ttu-id="e4ecc-187">En cas de conflit de noms avec un alias, vous devez inclure l’extension de fichier dans l’exemple de commande.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-187">When there is a name collisions with an alias you must include the file extension in the command example.</span></span> <span data-ttu-id="e4ecc-188">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-188">For example:</span></span>

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- <span data-ttu-id="e4ecc-189">Lorsque vous écrivez un article conceptuel (par opposition à du contenu de référence), la première instance du nom d’une cmdlet doit comporter un lien hypertexte vers la documentation de la cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-189">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="e4ecc-190">N’utilisez pas d’accents graves ou de balises de type gras ou autre à l’intérieur des crochets d’un lien hypertexte.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-190">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="e4ecc-191">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-191">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="e4ecc-192">Pour plus d’informations, consultez la section [Liens hypertextes](#hyperlinks) de cet article.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-192">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

### <a name="images"></a><span data-ttu-id="e4ecc-193">Images</span><span class="sxs-lookup"><span data-stu-id="e4ecc-193">Images</span></span>

<span data-ttu-id="e4ecc-194">Voici la syntaxe permettant d’inclure une image :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-194">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="e4ecc-195">Où `alt text` est une brève description de l’image et `<folder path>` le chemin relatif de l’image.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-195">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="e4ecc-196">Le texte de remplacement est nécessaire pour les lecteurs d’écran des personnes déficientes visuelles.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-196">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="e4ecc-197">Il est également utile en cas de bogue du site empêchant le rendu de l’image.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-197">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="e4ecc-198">Les images doivent être stockées dans un dossier `media/<article-name>` à l’intérieur du dossier contenant l’article.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-198">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="e4ecc-199">Elles ne doivent pas être partagées entre les articles.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-199">Images should not be shared between articles.</span></span> <span data-ttu-id="e4ecc-200">Créez un dossier correspondant au nom de fichier de votre article dans le dossier `media`.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-200">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="e4ecc-201">Copiez les images de cet article dans ce nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-201">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="e4ecc-202">Si une image est utilisée par plusieurs articles, chaque dossier d’image doit comporter une copie de ce fichier image.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-202">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="e4ecc-203">Cette pratique permet d’éviter que la modification d’une image dans un article n’affecte un autre article.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-203">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="e4ecc-204">Sont pris en charge les types de fichiers images suivants : `*.png`, `*.gif`, `*.jpeg`, `*.jpg` et `*.svg`.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-204">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="e4ecc-205">Extensions Markdown prises en charge par Open Publishing</span><span class="sxs-lookup"><span data-stu-id="e4ecc-205">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="e4ecc-206">[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contient des outils qui gèrent des fonctionnalités propres à notre système de publication.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-206">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="e4ecc-207">Les alertes sont une extension Markdown permettant de créer des citations qui s’affichent sur docs.microsoft.com avec des couleurs et des icônes différentes selon l’importance du contenu.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-207">Alerts are a Markdown extension to create block quotes that render on docs.microsoft.com with colors and icons that indicate the significance of the content.</span></span> <span data-ttu-id="e4ecc-208">Sont pris en charge les types d’alertes suivants :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-208">The following alert types are supported:</span></span>

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

<span data-ttu-id="e4ecc-209">Ces alertes se présentent ainsi sur docs.microsoft.com :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-209">These alerts look like this on docs.microsoft.com:</span></span>

> [!NOTE]
> <span data-ttu-id="e4ecc-210">Informations que l’utilisateur devrait remarquer même en parcourant rapidement le document.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-210">Information the user should notice even if skimming.</span></span>

> [!TIP]
> <span data-ttu-id="e4ecc-211">Informations facultatives visant à aider l’utilisateur à gagner en efficacité.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-211">Optional information to help a user be more successful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4ecc-212">Informations essentielles nécessaires à la réussite de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-212">Essential information required for user success.</span></span>

> [!CAUTION]
> <span data-ttu-id="e4ecc-213">Conséquences négatives potentielles d’une action.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-213">Negative potential consequences of an action.</span></span>

> [!WARNING]
> <span data-ttu-id="e4ecc-214">Conséquences dangereuses certaines d’une action.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-214">Dangerous certain consequences of an action.</span></span>

## <a name="hyperlinks"></a><span data-ttu-id="e4ecc-215">Liens hypertexte</span><span class="sxs-lookup"><span data-stu-id="e4ecc-215">Hyperlinks</span></span>

- <span data-ttu-id="e4ecc-216">Évitez d’utiliser des URL nues.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-216">Avoid using bare URLs.</span></span> <span data-ttu-id="e4ecc-217">Les liens doivent suivre la syntaxe Markdown `[friendlyname](url-or-path)`.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-217">Links should use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="e4ecc-218">Des URL nues peuvent être utilisées si nécessaire, mais à condition d’être placées entre accents graves.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-218">Bare URLs may be used when necessary, but should be enclosed in backticks.</span></span> <span data-ttu-id="e4ecc-219">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-219">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- <span data-ttu-id="e4ecc-220">Les liens URL doivent utiliser le protocole HTTPS dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-220">URL links should be HTTPS when possible.</span></span>
- <span data-ttu-id="e4ecc-221">Les liens doivent avoir un nom convivial, généralement le titre de la rubrique liée.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-221">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="e4ecc-222">Tous les éléments de la section « liens connexes » en bas de la page doivent contenir des liens hypertexte.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-222">All items in the "related links" section at the bottom should be hyperlinked.</span></span>
- <span data-ttu-id="e4ecc-223">N’utilisez pas d’accents graves ou de balises de type gras ou autre à l’intérieur des crochets d’un lien hypertexte.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-223">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

### <a name="linking-to-other-content"></a><span data-ttu-id="e4ecc-224">Liens vers d’autres contenus</span><span class="sxs-lookup"><span data-stu-id="e4ecc-224">Linking to other content</span></span>

<span data-ttu-id="e4ecc-225">Il existe deux types de liens hypertextes pris en charge par le système de publication : les URL et les liens de fichiers.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-225">There are two types of hyperlinks supported by the publishing system: URLs and file links.</span></span>

<span data-ttu-id="e4ecc-226">Un lien URL peut être un chemin d’URL relatif à la racine de docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="e4ecc-226">A URL link can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="e4ecc-227">ou une URL absolue comportant la syntaxe complète de l’URL</span><span class="sxs-lookup"><span data-stu-id="e4ecc-227">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="e4ecc-228">(par exemple, `https:/github.com/MicrosoftDocs/PowerShell-Docs`).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-228">(For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span></span>

- <span data-ttu-id="e4ecc-229">Utilisez des liens URL pour établir un lien vers du contenu extérieur à PowerShell-Docs ou entre des informations de référence sur les cmdlets et des articles conceptuels dans PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-229">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs.</span></span>
- <span data-ttu-id="e4ecc-230">Le moyen le plus simple de créer un lien relatif consiste à copier l’URL dans votre navigateur, puis à supprimer `https://docs.microsoft.com/en-us` de la valeur que vous collez dans Markdown.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-230">The simplest way to link create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
   - <span data-ttu-id="e4ecc-231">Ne pas inclure de paramètres régionaux dans les URL sur les propriétés Microsoft (par exemple,</span><span class="sxs-lookup"><span data-stu-id="e4ecc-231">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="e4ecc-232">supprimez « /en-us » de l’URL).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-232">remove "/en-us" from URL).</span></span>
- <span data-ttu-id="e4ecc-233">Toutes les URL de sites web externes doivent utiliser le protocole HTTPS, sauf si ce n’est pas valide pour le site cible.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-233">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="e4ecc-234">Un lien de fichier est utilisé pour établir un lien d’un article de référence à un autre, ou d’un article conceptuel à un autre.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-234">A file link is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="e4ecc-235">Si vous avez besoin de créer un lien vers un article de référence pour une version spécifique de PowerShell, vous devez utiliser un lien URL.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-235">If you need to link to a reference article for a specific version of PowerShell, then you need to use a URL link.</span></span>

- <span data-ttu-id="e4ecc-236">Les liens de fichiers contiennent un chemin de fichier relatif (par exemple, `../folder/file.md`).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-236">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="e4ecc-237">Tous les chemins de fichiers utilisent des barres obliques (`/`).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-237">All file paths use forward-slash (`/`) characters</span></span>

## <a name="formatting-code-samples"></a><span data-ttu-id="e4ecc-238">Mise en forme d’exemples de code</span><span class="sxs-lookup"><span data-stu-id="e4ecc-238">Formatting code samples</span></span>

<span data-ttu-id="e4ecc-239">Markdown prend en charge deux styles de code différents :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-239">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="e4ecc-240">Le code inline, marqué par un seul caractère accent grave (`` ` ``)</span><span class="sxs-lookup"><span data-stu-id="e4ecc-240">Code spans (inline) - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="e4ecc-241">et utilisé au sein d’un paragraphe plutôt que comme bloc autonome ;</span><span class="sxs-lookup"><span data-stu-id="e4ecc-241">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="e4ecc-242">les blocs de code, blocs de plusieurs lignes délimités par des chaînes constituées de trois accents graves (`` ``` ``)</span><span class="sxs-lookup"><span data-stu-id="e4ecc-242">Code blocks - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="e4ecc-243">éventuellement suivis d’une étiquette de langage</span><span class="sxs-lookup"><span data-stu-id="e4ecc-243">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="e4ecc-244">qui permet la coloration syntaxique du contenu du bloc de code.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-244">The language label enables syntax highlighting for the contents of the code block.</span></span>

### <a name="using-code-blocks"></a><span data-ttu-id="e4ecc-245">Usage des blocs de code</span><span class="sxs-lookup"><span data-stu-id="e4ecc-245">Using code blocks</span></span>

<span data-ttu-id="e4ecc-246">Markdown permet de définir un bloc de code par la mise en retrait, mais ce modèle peut être problématique et doit être évité.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-246">Markdown allows for indentation to signify a code block, but this pattern can be problematic and should be avoided.</span></span> <span data-ttu-id="e4ecc-247">Tous les blocs de code doivent être délimités</span><span class="sxs-lookup"><span data-stu-id="e4ecc-247">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="e4ecc-248">par des chaînes constituées de trois accents graves (`` ``` ``).</span><span class="sxs-lookup"><span data-stu-id="e4ecc-248">A code fence is a block of code surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="e4ecc-249">Les délimiteurs de code doivent se trouver sur leur propre ligne avant et après l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-249">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="e4ecc-250">Le marqueur de début du bloc de code peut éventuellement comporter une étiquette de langage.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-250">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="e4ecc-251">Microsoft Open Publishing System (OPS) utilise l’étiquette de langage pour gérer la fonctionnalité de coloration syntaxique.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-251">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="e4ecc-252">OPS ajoute également un bouton **Copier** qui permet de copier le contenu du bloc de code dans le Presse-papiers,</span><span class="sxs-lookup"><span data-stu-id="e4ecc-252">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="e4ecc-253">et ainsi de coller rapidement le code dans un script pour tester l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-253">This allows you to quickly paste the code into a script for testing the code example.</span></span> <span data-ttu-id="e4ecc-254">Toutefois, les exemples de notre documentation ne sont pas tous destinés à être exécutés.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-254">However, not all examples in our documentation are intended to be run.</span></span> <span data-ttu-id="e4ecc-255">Certains blocs de code sont de simples illustrations d’un concept de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-255">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="e4ecc-256">Deux types de blocs de code sont utilisés dans notre documentation :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-256">There are two types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="e4ecc-257">Exemples servant d’illustration</span><span class="sxs-lookup"><span data-stu-id="e4ecc-257">Illustrative examples</span></span>
2. <span data-ttu-id="e4ecc-258">Exemples exécutables</span><span class="sxs-lookup"><span data-stu-id="e4ecc-258">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="e4ecc-259">Blocs de code syntaxiques</span><span class="sxs-lookup"><span data-stu-id="e4ecc-259">Syntax code blocks</span></span>

<span data-ttu-id="e4ecc-260">Cet exemple illustre tous les paramètres possibles de la cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-260">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="e4ecc-261">Cet exemple décrit l’instruction `for` en termes généralisés :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-261">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="e4ecc-262">Exemples servant d’illustration</span><span class="sxs-lookup"><span data-stu-id="e4ecc-262">Illustrative examples</span></span>

<span data-ttu-id="e4ecc-263">Certains exemples servent d’illustration pour expliquer un concept de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-263">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="e4ecc-264">Ils ne sont pas destinés à être copiés dans le Presse-papiers pour être exécutés.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-264">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="e4ecc-265">Ils sont couramment utilisés pour des exemples simples et faciles à taper,</span><span class="sxs-lookup"><span data-stu-id="e4ecc-265">These are most commonly used for simple examples that are easy to type.</span></span>
<span data-ttu-id="e4ecc-266">ou pour des exemples illustrant la syntaxe d’une commande.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-266">They are also used for syntax examples where you are illustrating the syntax of a command.</span></span> <span data-ttu-id="e4ecc-267">Le bloc de code peut contenir l’exemple de sortie de la commande illustrée.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-267">The code block may contain example output from the command being illustrated.</span></span>

<span data-ttu-id="e4ecc-268">Voici un exemple simple illustrant des opérateurs de comparaison de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-268">Here is a simple example illustrating a PowerShell comparison operators:</span></span>

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

<span data-ttu-id="e4ecc-269">Comme on peut le constater, cet exemple présente l’invite PowerShell simplifiée et affiche la sortie obtenue.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-269">Note that this example has the simplified PowerShell prompt and shows the resulting output.</span></span> <span data-ttu-id="e4ecc-270">Il n’est pas attendu du lecteur qu’il copie et exécute cet exemple.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-270">In this case, we don't intend the reader to copy and run this example.</span></span>

### <a name="executable-examples"></a><span data-ttu-id="e4ecc-271">Exemples exécutables</span><span class="sxs-lookup"><span data-stu-id="e4ecc-271">Executable examples</span></span>

<span data-ttu-id="e4ecc-272">Les exemples plus complexes ou destinés à être copiés et exécutés doivent utiliser le balisage de style bloc suivant :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-272">More complex examples or examples that are intended to be useful to copy and execute should use the following block-style markup:</span></span>

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

<span data-ttu-id="e4ecc-273">La sortie affichée par les commandes PowerShell doit être placée dans un bloc de code **Output** pour empêcher la coloration syntaxique.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-273">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="e4ecc-274">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e4ecc-274">For example:</span></span>

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

<span data-ttu-id="e4ecc-275">L’étiquette de code **Output** n’est pas un « langage » officiel pris en charge par le système de coloration syntaxique.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-275">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="e4ecc-276">Elle est toutefois utile, car OPS ajoute l’étiquette « Output » (« Sortie ») au cadre de la zone de code sur la page web.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-276">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="e4ecc-277">La zone de code « Output » ne présente pas de coloration syntaxique.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-277">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="e4ecc-278">Règles de style de codage</span><span class="sxs-lookup"><span data-stu-id="e4ecc-278">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="e4ecc-279">Éviter la continuation de ligne dans les exemples de code</span><span class="sxs-lookup"><span data-stu-id="e4ecc-279">Avoid line continuation in code samples</span></span>

<span data-ttu-id="e4ecc-280">Évitez d’utiliser des caractères de continuation de ligne (`` ` ``) dans les exemples de code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-280">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="e4ecc-281">Ils sont difficiles à voir et peuvent poser problème en présence d’espaces supplémentaires à la fin de la ligne.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-281">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="e4ecc-282">Utilisez la projection PowerShell pour réduire la longueur de ligne des cmdlets comportant de nombreux paramètres.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-282">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="e4ecc-283">Tirez parti des possibilités naturelles de saut de ligne de PowerShell, comme après les caractères barre verticale (`|`), les accolades ouvrantes, les parenthèses et les crochets.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-283">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="e4ecc-284">Éviter d’utiliser les invites PowerShell dans les exemples</span><span class="sxs-lookup"><span data-stu-id="e4ecc-284">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="e4ecc-285">Il est déconseillé d’utiliser la chaîne d’invite, qui doit être limitée aux scénarios destinés à illustrer l’usage de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-285">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="e4ecc-286">Pour la plupart de ces exemples, la chaîne d’invite doit être `PS>`.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-286">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="e4ecc-287">Cette invite est indépendante des indicateurs propres au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-287">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="e4ecc-288">Les invites sont requises pour les exemples illustrant des commandes qui modifient l’invite ou lorsque le chemin affiché est significatif pour le scénario illustré.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-288">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="e4ecc-289">L’exemple suivant montre comment l’invite change lorsque le fournisseur de registre est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-289">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="e4ecc-290">Ne pas utiliser d’alias dans les exemples</span><span class="sxs-lookup"><span data-stu-id="e4ecc-290">Do not use aliases in examples</span></span>

<span data-ttu-id="e4ecc-291">Utilisez toujours le nom complet de toutes les cmdlets et de tous les paramètres, sauf si vous parlez spécifiquement de l’alias.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-291">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="e4ecc-292">Le noms des cmdlets et des paramètres doit suivre l’orthographe correcte définie dans le code.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-292">Cmdlet and parameter names must use the proper spelling defined in the code.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="e4ecc-293">Utiliser des paramètres dans les exemples</span><span class="sxs-lookup"><span data-stu-id="e4ecc-293">Using parameters in examples</span></span>

<span data-ttu-id="e4ecc-294">Évitez d’utiliser des paramètres positionnels.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-294">Avoid using positional parameters.</span></span> <span data-ttu-id="e4ecc-295">En général, vous devez toujours inclure le nom du paramètre dans l’exemple, même s’il s’agit d’un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-295">In general, you should use always include the parameter name in an example, even if the parameter positional.</span></span> <span data-ttu-id="e4ecc-296">Cela réduit le risque de confusion dans les exemples.</span><span class="sxs-lookup"><span data-stu-id="e4ecc-296">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e4ecc-297">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e4ecc-297">Next steps</span></span>

[<span data-ttu-id="e4ecc-298">Modification des informations de référence sur les cmdlets</span><span class="sxs-lookup"><span data-stu-id="e4ecc-298">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
