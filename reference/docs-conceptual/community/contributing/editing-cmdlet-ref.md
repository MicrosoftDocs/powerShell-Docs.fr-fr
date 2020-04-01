---
title: Modification des articles de référence
description: Cet article explique les conditions requises pour modifier les informations de référence sur les cmdlets et les rubriques About_ de la documentation de PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3aed1c14429310c57681397d4877a3a6f48400fd
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500972"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="ba1e6-103">Modification des articles de référence</span><span class="sxs-lookup"><span data-stu-id="ba1e6-103">Editing reference articles</span></span>

<span data-ttu-id="ba1e6-104">Les articles de référence sur les cmdlets présentent une structure spécifique.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="ba1e6-105">La structure est définie par [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="ba1e6-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="ba1e6-106">PlatyPS génère l’aide des cmdlets pour les modules PowerShell en Markdown.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="ba1e6-107">Après la modification des fichiers Markdown, PlatyPS permet de créer les fichiers d’aide MAML utilisés par la cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="ba1e6-108">PlatyPS possède un schéma codé en dur pour les informations de référence sur les cmdlets écrites dans le code.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="ba1e6-109">Le document [platyPS.schema.md][] tente de décrire cette structure.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="ba1e6-110">Les violations de schéma entraînent des erreurs de build que vous devez corriger pour que votre contribution puisse être acceptée.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="ba1e6-111">Recommandations générales</span><span class="sxs-lookup"><span data-stu-id="ba1e6-111">General guidelines</span></span>

- <span data-ttu-id="ba1e6-112">Ne supprimez aucune des structures d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="ba1e6-113">PlatyPS attend un ensemble spécifique d’en-têtes.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="ba1e6-114">Les en-têtes **Type d’entrée** et **Type de sortie** doivent avoir un type.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="ba1e6-115">Si la cmdlet ne prend pas d’entrée ou ne retourne pas de valeur, utilisez la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="ba1e6-116">Les blocs de code délimités ne sont autorisés que dans la section [Exemples](#structuring-examples).</span><span class="sxs-lookup"><span data-stu-id="ba1e6-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="ba1e6-117">Les morceaux de code inline peuvent être utilisés dans n’importe quel paragraphe.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="ba1e6-118">Mise en forme des fichiers About_</span><span class="sxs-lookup"><span data-stu-id="ba1e6-118">Formatting About_ files</span></span>

<span data-ttu-id="ba1e6-119">Les fichiers `About_*` sont maintenant traités par [Pandoc][] et non plus par PlatyPS.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-119">`About_*` files are now processed by [Pandoc][], instead of PlatyPS.</span></span> <span data-ttu-id="ba1e6-120">Leur mise en forme répond à l’objectif de maximiser la compatibilité dans toutes les versions de PowerShell et avec les outils de publication.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-120">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="ba1e6-121">Instructions de mise en forme de base :</span><span class="sxs-lookup"><span data-stu-id="ba1e6-121">Basic formatting guidelines:</span></span>

- <span data-ttu-id="ba1e6-122">Limitez les lignes à 80 caractères.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-122">Limit lines to 80 characters</span></span>
- <span data-ttu-id="ba1e6-123">Les blocs de code et les tables sont limités à 76 caractères, car Pandoc ajoute un retrait de quatre espaces lors de la conversion en texte brut.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-123">Code blocks and tables are limited to 76 characters because Pandoc indents these by four spaces during conversion to plain text</span></span>
- <span data-ttu-id="ba1e6-124">Les tables doivent tenir dans 76 caractères.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-124">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="ba1e6-125">Ajoutez manuellement des retours à la ligne au contenu des cellules.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-125">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="ba1e6-126">Utilisez des caractères `|` ouvrants et fermants sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-126">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="ba1e6-127">Vous trouverez un exemple fonctionnel dans [about_Comparison_Operators][about-example].</span><span class="sxs-lookup"><span data-stu-id="ba1e6-127">See a working example in [about_Comparison_Operators][about-example]</span></span>
- <span data-ttu-id="ba1e6-128">Si vous utilisez les caractères spéciaux Pandoc `\`, `$` et `<` :</span><span class="sxs-lookup"><span data-stu-id="ba1e6-128">Using Pandoc special characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="ba1e6-129">Dans un en-tête : ils doivent être placés dans une séquence d’échappement précédée d’un caractère `\` ou entre accents graves (`` ` ``)</span><span class="sxs-lookup"><span data-stu-id="ba1e6-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in backticks (`` ` ``)</span></span>
  - <span data-ttu-id="ba1e6-130">Dans un paragraphe : ils doivent être placés dans un morceau de code.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="ba1e6-131">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ba1e6-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a><span data-ttu-id="ba1e6-132">Structuration des exemples</span><span class="sxs-lookup"><span data-stu-id="ba1e6-132">Structuring examples</span></span>

<span data-ttu-id="ba1e6-133">Dans le schéma PlatyPS, l’en-tête **EXEMPLES** est un en-tête H2 et chaque exemple est un en-tête H3.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-133">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="ba1e6-134">Le schéma ne permet pas de séparer les blocs de code par des paragraphes dans un exemple.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-134">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="ba1e6-135">Voici le schéma pris en charge :</span><span class="sxs-lookup"><span data-stu-id="ba1e6-135">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="ba1e6-136">Numérotez chaque exemple et ajoutez un titre court.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-136">Number each example and add a brief title.</span></span>

<span data-ttu-id="ba1e6-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ba1e6-137">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="ba1e6-138">Exemple 1 : Récupérer les cmdlets, les fonctions et les alias</span><span class="sxs-lookup"><span data-stu-id="ba1e6-138">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="ba1e6-139">Cette commande permet d’obtenir les cmdlets, fonctions et alias PowerShell installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba1e6-139">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="ba1e6-140">Exemple 2 : Récupérer les commandes de la session active</span><span class="sxs-lookup"><span data-stu-id="ba1e6-140">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="ba1e6-141">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ba1e6-141">Next steps</span></span>

[<span data-ttu-id="ba1e6-142">Liste de contrôle éditoriale</span><span class="sxs-lookup"><span data-stu-id="ba1e6-142">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
