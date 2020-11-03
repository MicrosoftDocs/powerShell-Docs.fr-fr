---
description: Répertorie les mots réservés qui ne peuvent pas être utilisés comme identificateurs, car ils ont une signification particulière dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: edf37ce528c8fd98ce3ca7741a1a6c9e0443173a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208253"
---
# <a name="about-reserved-words"></a><span data-ttu-id="298fc-104">À propos des mots réservés</span><span class="sxs-lookup"><span data-stu-id="298fc-104">About Reserved Words</span></span>

## <a name="short-description"></a><span data-ttu-id="298fc-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="298fc-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="298fc-106">Répertorie les mots réservés qui ne peuvent pas être utilisés comme identificateurs, car ils ont une signification particulière dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="298fc-106">Lists the reserved words that cannot be used as identifiers because they have a special meaning in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="298fc-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="298fc-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="298fc-108">Il existe certains mots qui ont une signification particulière dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="298fc-108">There are certain words that have special meaning in PowerShell.</span></span> <span data-ttu-id="298fc-109">Lorsque ces mots apparaissent sans guillemets, PowerShell tente d’appliquer leur signification spéciale plutôt que de les traiter comme des chaînes de caractères.</span><span class="sxs-lookup"><span data-stu-id="298fc-109">When these words appear without quotation marks, PowerShell attempts to apply their special meaning rather than treating them as character strings.</span></span> <span data-ttu-id="298fc-110">Pour utiliser ces mots comme arguments de paramètre dans une commande ou un script sans appeler leur signification spéciale, mettez les mots réservés entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="298fc-110">To use these words as parameter arguments in a command or script without invoking their special meaning, enclose the reserved words in quotation marks.</span></span>

<span data-ttu-id="298fc-111">Les mots réservés dans PowerShell sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="298fc-111">The following are the reserved words in PowerShell:</span></span>

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

<span data-ttu-id="298fc-112">Plusieurs mots clés de langage, y compris `Foreach` ,, `If` `For` et `While` , ont leurs propres Articles d’aide.</span><span class="sxs-lookup"><span data-stu-id="298fc-112">Several language keywords, including `Foreach`, `If`, `For`, and `While`, have their own help articles.</span></span> <span data-ttu-id="298fc-113">Pour les afficher, tapez `Get-Help about_` et ajoutez le mot clé.</span><span class="sxs-lookup"><span data-stu-id="298fc-113">To view them, type `Get-Help about_` and add the keyword.</span></span> <span data-ttu-id="298fc-114">Par exemple, pour obtenir des informations sur l' `Foreach` instruction, tapez :</span><span class="sxs-lookup"><span data-stu-id="298fc-114">For example, to get information about the `Foreach` statement, type:</span></span>

```powershell
Get-Help about_ForEach
```

<span data-ttu-id="298fc-115">Pour plus d’informations sur l' `Filter` instruction ou la syntaxe de l' `Return` instruction, tapez :</span><span class="sxs-lookup"><span data-stu-id="298fc-115">For information about the `Filter` statement or the `Return` statement syntax, type:</span></span>

```powershell
Get-Help about_Functions
```

<span data-ttu-id="298fc-116">Pour plus d’informations sur les autres mots réservés, tapez :</span><span class="sxs-lookup"><span data-stu-id="298fc-116">For information about other reserved words, type:</span></span>

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> <span data-ttu-id="298fc-117">Tous les mots réservés n’ont pas leur propre article d’aide.</span><span class="sxs-lookup"><span data-stu-id="298fc-117">Not every reserved word has its own help article.</span></span> <span data-ttu-id="298fc-118">Si `Get-Help` ne retourne pas d’article, vous pouvez rechercher des articles qui traitent du mot réservé à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="298fc-118">If `Get-Help` does not return an article, you can search for articles that talk about the reserved word using the following command:</span></span>
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a><span data-ttu-id="298fc-119">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="298fc-119">SEE ALSO</span></span>

- [<span data-ttu-id="298fc-120">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="298fc-120">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="298fc-121">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="298fc-121">about_Language_Keywords</span></span>](about_Language_Keywords.md)
- [<span data-ttu-id="298fc-122">about_Parsing</span><span class="sxs-lookup"><span data-stu-id="298fc-122">about_Parsing</span></span>](about_Parsing.md)
- [<span data-ttu-id="298fc-123">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="298fc-123">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="298fc-124">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="298fc-124">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="298fc-125">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="298fc-125">about_Special_Characters</span></span>](about_Special_Characters.md)
