---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
schema: 2.0.0
ms.openlocfilehash: 775b11db79b9ca8290864b757e5cd1a0615f89e4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598756"
---
# <span data-ttu-id="5e157-101">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="5e157-101">Get-MarkdownOption</span></span>

## <span data-ttu-id="5e157-102">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5e157-102">SYNOPSIS</span></span>
<span data-ttu-id="5e157-103">Retourne les couleurs et les styles actuels utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="5e157-103">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="5e157-104">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="5e157-104">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="5e157-105">Description</span><span class="sxs-lookup"><span data-stu-id="5e157-105">DESCRIPTION</span></span>

<span data-ttu-id="5e157-106">Retourne les couleurs et les styles actuels utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="5e157-106">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="5e157-107">Les chaînes affichées dans la sortie de cette applet de commande contiennent les codes d’échappement ANSI utilisés pour modifier la couleur et le style du texte de la démarque en cours de rendu.</span><span class="sxs-lookup"><span data-stu-id="5e157-107">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="5e157-108">Pour plus d’informations sur la démarque, consultez le site Web [CommonMark](https://commonmark.org/) .</span><span class="sxs-lookup"><span data-stu-id="5e157-108">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="5e157-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5e157-109">EXAMPLES</span></span>

### <span data-ttu-id="5e157-110">Exemple 1 : récupérer les couleurs et le style actuels</span><span class="sxs-lookup"><span data-stu-id="5e157-110">Example 1 - Get the current colors and style</span></span>

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
> <span data-ttu-id="5e157-111">Les valeurs de chaîne indiquées dans la sortie sont les caractères qui suivent le caractère d' **échappement** ( `[char]0x1B` ) pour la séquence d’échappement ANSI.</span><span class="sxs-lookup"><span data-stu-id="5e157-111">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="5e157-112">Pour plus d’informations sur le fonctionnement des codes d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="5e157-112">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="5e157-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5e157-113">PARAMETERS</span></span>

### <span data-ttu-id="5e157-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e157-114">CommonParameters</span></span>

<span data-ttu-id="5e157-115">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5e157-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e157-116">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5e157-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e157-117">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5e157-117">INPUTS</span></span>

### <span data-ttu-id="5e157-118">None</span><span class="sxs-lookup"><span data-stu-id="5e157-118">None</span></span>

## <span data-ttu-id="5e157-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5e157-119">OUTPUTS</span></span>

### <span data-ttu-id="5e157-120">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="5e157-120">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="5e157-121">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5e157-121">NOTES</span></span>

## <span data-ttu-id="5e157-122">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5e157-122">RELATED LINKS</span></span>

[<span data-ttu-id="5e157-123">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="5e157-123">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="5e157-124">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="5e157-124">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="5e157-125">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="5e157-125">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="5e157-126">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="5e157-126">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="5e157-127">CommonMark</span><span class="sxs-lookup"><span data-stu-id="5e157-127">CommonMark</span></span>](https://commonmark.org/)

