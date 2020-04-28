---
title: Modification des articles de référence
description: Cet article explique les conditions requises pour modifier les informations de référence sur les cmdlets et les rubriques About_ de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624769"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="bf109-103">Modification des articles de référence</span><span class="sxs-lookup"><span data-stu-id="bf109-103">Editing reference articles</span></span>

<span data-ttu-id="bf109-104">Les articles de référence sur les cmdlets présentent une structure spécifique.</span><span class="sxs-lookup"><span data-stu-id="bf109-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="bf109-105">La structure est définie par [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="bf109-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="bf109-106">PlatyPS génère l’aide des cmdlets pour les modules PowerShell en Markdown.</span><span class="sxs-lookup"><span data-stu-id="bf109-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="bf109-107">Après la modification des fichiers Markdown, PlatyPS permet de créer les fichiers d’aide MAML utilisés par la cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="bf109-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="bf109-108">PlatyPS possède un schéma codé en dur pour les informations de référence sur les cmdlets écrites dans le code.</span><span class="sxs-lookup"><span data-stu-id="bf109-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="bf109-109">Le document [platyPS.schema.md][] tente de décrire cette structure.</span><span class="sxs-lookup"><span data-stu-id="bf109-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="bf109-110">Les violations de schéma entraînent des erreurs de build que vous devez corriger pour que votre contribution puisse être acceptée.</span><span class="sxs-lookup"><span data-stu-id="bf109-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="bf109-111">Recommandations générales</span><span class="sxs-lookup"><span data-stu-id="bf109-111">General guidelines</span></span>

- <span data-ttu-id="bf109-112">Ne supprimez aucune des structures d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="bf109-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="bf109-113">PlatyPS attend un ensemble spécifique d’en-têtes.</span><span class="sxs-lookup"><span data-stu-id="bf109-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="bf109-114">Les en-têtes **Type d’entrée** et **Type de sortie** doivent avoir un type.</span><span class="sxs-lookup"><span data-stu-id="bf109-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="bf109-115">Si la cmdlet ne prend pas d’entrée ou ne retourne pas de valeur, utilisez la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="bf109-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="bf109-116">Les blocs de code délimités ne sont autorisés que dans la section [Exemples](#structuring-examples).</span><span class="sxs-lookup"><span data-stu-id="bf109-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="bf109-117">Les morceaux de code inline peuvent être utilisés dans n’importe quel paragraphe.</span><span class="sxs-lookup"><span data-stu-id="bf109-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="bf109-118">Mise en forme des fichiers About_</span><span class="sxs-lookup"><span data-stu-id="bf109-118">Formatting About_ files</span></span>

<span data-ttu-id="bf109-119">Les fichiers `About_*` sont écrits dans Markdown mais sont fournis en tant que fichiers texte bruts.</span><span class="sxs-lookup"><span data-stu-id="bf109-119">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="bf109-120">Nous utilisons [Pandoc][] pour convertir Markdown en texte brut.</span><span class="sxs-lookup"><span data-stu-id="bf109-120">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="bf109-121">Leur mise en forme répond à l’objectif de maximiser la compatibilité dans toutes les versions de PowerShell et avec les outils de publication.</span><span class="sxs-lookup"><span data-stu-id="bf109-121">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="bf109-122">Instructions de mise en forme de base :</span><span class="sxs-lookup"><span data-stu-id="bf109-122">Basic formatting guidelines:</span></span>

- <span data-ttu-id="bf109-123">Limitez les lignes à 80 caractères.</span><span class="sxs-lookup"><span data-stu-id="bf109-123">Limit lines to 80 characters.</span></span> <span data-ttu-id="bf109-124">Pandoc met en retrait certains blocs Markdown, de sorte que ces blocs doivent être ajustés.</span><span class="sxs-lookup"><span data-stu-id="bf109-124">Pandoc indents some Markdown blocks so those block must be adjusted.</span></span>
  - <span data-ttu-id="bf109-125">Les blocs de code sont limités à 76 caractères</span><span class="sxs-lookup"><span data-stu-id="bf109-125">Code blocks are limited to 76 characters</span></span>
  - <span data-ttu-id="bf109-126">Les tables sont limitées à 76 caractères</span><span class="sxs-lookup"><span data-stu-id="bf109-126">Tables are limited 76 characters</span></span>
  - <span data-ttu-id="bf109-127">Les citations (et les alertes) sont limitées à 78 caractères</span><span class="sxs-lookup"><span data-stu-id="bf109-127">Blockquotes (and Alerts) are limited 78 characters</span></span>

- <span data-ttu-id="bf109-128">Si vous utilisez les méta-caractères spéciaux Pandoc `\`, `$` et `<`</span><span class="sxs-lookup"><span data-stu-id="bf109-128">Using Pandoc's special meta-characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="bf109-129">Dans un en-tête : ils doivent être placés dans une séquence d’échappement précédée d’un caractère `\` ou dans des morceaux de code entre accents graves (`` ` ``)</span><span class="sxs-lookup"><span data-stu-id="bf109-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="bf109-130">Dans un paragraphe : ils doivent être placés dans un morceau de code.</span><span class="sxs-lookup"><span data-stu-id="bf109-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="bf109-131">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bf109-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="bf109-132">Les tables doivent tenir dans 76 caractères.</span><span class="sxs-lookup"><span data-stu-id="bf109-132">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="bf109-133">Ajoutez manuellement des retours à la ligne au contenu des cellules.</span><span class="sxs-lookup"><span data-stu-id="bf109-133">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="bf109-134">Utilisez des caractères `|` ouvrants et fermants sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="bf109-134">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="bf109-135">L’exemple suivant montre comment construire correctement une table qui contient des informations qui s’encapsulent sur plusieurs lignes dans une cellule.</span><span class="sxs-lookup"><span data-stu-id="bf109-135">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

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
    > <span data-ttu-id="bf109-136">La limite de 76 colonnes s’applique uniquement aux rubriques `About_*`.</span><span class="sxs-lookup"><span data-stu-id="bf109-136">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="bf109-137">Vous pouvez utiliser des colonnes larges dans les articles de référence sur les cmdlets ou conceptuelles.</span><span class="sxs-lookup"><span data-stu-id="bf109-137">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="structuring-examples"></a><span data-ttu-id="bf109-138">Structuration des exemples</span><span class="sxs-lookup"><span data-stu-id="bf109-138">Structuring examples</span></span>

<span data-ttu-id="bf109-139">Dans le schéma PlatyPS, l’en-tête **EXEMPLES** est un en-tête H2 et chaque exemple est un en-tête H3.</span><span class="sxs-lookup"><span data-stu-id="bf109-139">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="bf109-140">Le schéma ne permet pas de séparer les blocs de code par des paragraphes dans un exemple.</span><span class="sxs-lookup"><span data-stu-id="bf109-140">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="bf109-141">Voici le schéma pris en charge :</span><span class="sxs-lookup"><span data-stu-id="bf109-141">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="bf109-142">Numérotez chaque exemple et ajoutez un titre court.</span><span class="sxs-lookup"><span data-stu-id="bf109-142">Number each example and add a brief title.</span></span>

<span data-ttu-id="bf109-143">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bf109-143">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="bf109-144">Exemple 1 : Récupérer les cmdlets, les fonctions et les alias</span><span class="sxs-lookup"><span data-stu-id="bf109-144">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="bf109-145">Cette commande permet d’obtenir les cmdlets, fonctions et alias PowerShell installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bf109-145">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="bf109-146">Exemple 2 : Récupérer les commandes de la session active</span><span class="sxs-lookup"><span data-stu-id="bf109-146">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="bf109-147">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="bf109-147">Next steps</span></span>

[<span data-ttu-id="bf109-148">Liste de contrôle éditoriale</span><span class="sxs-lookup"><span data-stu-id="bf109-148">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
