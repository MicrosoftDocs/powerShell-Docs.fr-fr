---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-MarkdownOption
ms.openlocfilehash: 0da0c869216fd2a044fe03faad25e3de6f3fb8fd
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195703"
---
# <span data-ttu-id="10db1-102">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="10db1-102">Get-MarkdownOption</span></span>

## <span data-ttu-id="10db1-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="10db1-103">SYNOPSIS</span></span>
<span data-ttu-id="10db1-104">Retourne les couleurs et les styles actuels utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="10db1-104">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="10db1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="10db1-105">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="10db1-106">Description</span><span class="sxs-lookup"><span data-stu-id="10db1-106">DESCRIPTION</span></span>

<span data-ttu-id="10db1-107">Retourne les couleurs et les styles actuels utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="10db1-107">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="10db1-108">Les chaînes affichées dans la sortie de cette applet de commande contiennent les codes d’échappement ANSI utilisés pour modifier la couleur et le style du texte de la démarque en cours de rendu.</span><span class="sxs-lookup"><span data-stu-id="10db1-108">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="10db1-109">Pour plus d’informations sur la démarque, consultez le site Web [CommonMark](https://commonmark.org/) .</span><span class="sxs-lookup"><span data-stu-id="10db1-109">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="10db1-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="10db1-110">EXAMPLES</span></span>

### <span data-ttu-id="10db1-111">Exemple 1 : récupérer les couleurs et le style actuels</span><span class="sxs-lookup"><span data-stu-id="10db1-111">Example 1 - Get the current colors and style</span></span>

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
> <span data-ttu-id="10db1-112">Les valeurs de chaîne indiquées dans la sortie sont les caractères qui suivent le caractère d' **échappement** ( `[char]0x1B` ) pour la séquence d’échappement ANSI.</span><span class="sxs-lookup"><span data-stu-id="10db1-112">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="10db1-113">Pour plus d’informations sur le fonctionnement des codes d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="10db1-113">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="10db1-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="10db1-114">PARAMETERS</span></span>

### <span data-ttu-id="10db1-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="10db1-115">CommonParameters</span></span>

<span data-ttu-id="10db1-116">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="10db1-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="10db1-117">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="10db1-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="10db1-118">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="10db1-118">INPUTS</span></span>

### <span data-ttu-id="10db1-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="10db1-119">None</span></span>

## <span data-ttu-id="10db1-120">SORTIES</span><span class="sxs-lookup"><span data-stu-id="10db1-120">OUTPUTS</span></span>

### <span data-ttu-id="10db1-121">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="10db1-121">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="10db1-122">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="10db1-122">NOTES</span></span>

## <span data-ttu-id="10db1-123">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="10db1-123">RELATED LINKS</span></span>

[<span data-ttu-id="10db1-124">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="10db1-124">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="10db1-125">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="10db1-125">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="10db1-126">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="10db1-126">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="10db1-127">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="10db1-127">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="10db1-128">CommonMark</span><span class="sxs-lookup"><span data-stu-id="10db1-128">CommonMark</span></span>](https://commonmark.org/)

