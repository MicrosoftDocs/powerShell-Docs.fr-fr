---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: f39add03a3b0250172cbb117a4233bb01958d9d3
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205262"
---
# <span data-ttu-id="bec89-101">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="bec89-101">Get-MarkdownOption</span></span>

## <span data-ttu-id="bec89-102">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bec89-102">SYNOPSIS</span></span>
<span data-ttu-id="bec89-103">Retourne les couleurs et les styles actuels utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="bec89-103">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="bec89-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bec89-104">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="bec89-105">Description</span><span class="sxs-lookup"><span data-stu-id="bec89-105">DESCRIPTION</span></span>

<span data-ttu-id="bec89-106">Retourne les couleurs et les styles actuels utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="bec89-106">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="bec89-107">Les chaînes affichées dans la sortie de cette applet de commande contiennent les codes d’échappement ANSI utilisés pour modifier la couleur et le style du texte de la démarque en cours de rendu.</span><span class="sxs-lookup"><span data-stu-id="bec89-107">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="bec89-108">Pour plus d’informations sur la démarque, consultez le site Web [CommonMark](https://commonmark.org/) .</span><span class="sxs-lookup"><span data-stu-id="bec89-108">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="bec89-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bec89-109">EXAMPLES</span></span>

### <span data-ttu-id="bec89-110">Exemple 1 : récupérer les couleurs et le style actuels</span><span class="sxs-lookup"><span data-stu-id="bec89-110">Example 1 - Get the current colors and style</span></span>

```powershell
Get-MarkdownOption
```

```Output
Header1         : [7m
Header2         : [4;93m
Header3         : [4;94m
Header4         : [4;95m
Header5         : [4;96m
Header6         : [4;97m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

> [!NOTE]
> <span data-ttu-id="bec89-111">Les valeurs de chaîne indiquées dans la sortie sont les caractères qui suivent le caractère d' **échappement** ( `[char]0x1B` ) pour la séquence d’échappement ANSI.</span><span class="sxs-lookup"><span data-stu-id="bec89-111">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="bec89-112">Pour plus d’informations sur le fonctionnement des codes d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="bec89-112">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="bec89-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bec89-113">PARAMETERS</span></span>

### <span data-ttu-id="bec89-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bec89-114">CommonParameters</span></span>

<span data-ttu-id="bec89-115">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bec89-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bec89-116">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bec89-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bec89-117">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bec89-117">INPUTS</span></span>

### <span data-ttu-id="bec89-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="bec89-118">None</span></span>

## <span data-ttu-id="bec89-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bec89-119">OUTPUTS</span></span>

### <span data-ttu-id="bec89-120">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="bec89-120">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="bec89-121">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bec89-121">NOTES</span></span>

## <span data-ttu-id="bec89-122">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bec89-122">RELATED LINKS</span></span>

[<span data-ttu-id="bec89-123">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="bec89-123">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="bec89-124">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="bec89-124">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="bec89-125">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="bec89-125">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="bec89-126">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="bec89-126">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="bec89-127">CommonMark</span><span class="sxs-lookup"><span data-stu-id="bec89-127">CommonMark</span></span>](https://commonmark.org/)
