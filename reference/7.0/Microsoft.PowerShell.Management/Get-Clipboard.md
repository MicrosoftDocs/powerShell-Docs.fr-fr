---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 9da33bcf0bc1142859d547debedfb242819041aa
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239630"
---
# <span data-ttu-id="7e0b4-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="7e0b4-103">Get-Clipboard</span></span>

## <span data-ttu-id="7e0b4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7e0b4-104">SYNOPSIS</span></span>
<span data-ttu-id="7e0b4-105">Obtient le contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="7e0b4-105">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="7e0b4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7e0b4-106">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="7e0b4-107">Description</span><span class="sxs-lookup"><span data-stu-id="7e0b4-107">DESCRIPTION</span></span>

<span data-ttu-id="7e0b4-108">L' `Get-Clipboard` applet de commande obtient le contenu du presse-papiers sous forme de texte.</span><span class="sxs-lookup"><span data-stu-id="7e0b4-108">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="7e0b4-109">Plusieurs lignes de texte sont retournées sous la forme d’un tableau de chaînes similaire à `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="7e0b4-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="7e0b4-110">Sur Linux, cette applet de commande requiert que l' `xclip` utilitaire se trouve dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="7e0b4-110">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="7e0b4-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7e0b4-111">EXAMPLES</span></span>

### <span data-ttu-id="7e0b4-112">Exemple 1 : obtenir le contenu du presse-papiers et l’afficher sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="7e0b4-112">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="7e0b4-113">Dans cet exemple, nous avons copié le texte « Hello » dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="7e0b4-113">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="7e0b4-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7e0b4-114">PARAMETERS</span></span>

### <span data-ttu-id="7e0b4-115">-RAW</span><span class="sxs-lookup"><span data-stu-id="7e0b4-115">-Raw</span></span>

<span data-ttu-id="7e0b4-116">Obtient la totalité du contenu du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="7e0b4-116">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="7e0b4-117">Le texte multiligne est retourné sous la forme d’une chaîne multiligne unique plutôt que d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="7e0b4-117">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e0b4-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e0b4-118">CommonParameters</span></span>

<span data-ttu-id="7e0b4-119">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e0b4-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e0b4-120">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7e0b4-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e0b4-121">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7e0b4-121">INPUTS</span></span>

## <span data-ttu-id="7e0b4-122">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7e0b4-122">OUTPUTS</span></span>

### <span data-ttu-id="7e0b4-123">System.String</span><span class="sxs-lookup"><span data-stu-id="7e0b4-123">System.String</span></span>

## <span data-ttu-id="7e0b4-124">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7e0b4-124">NOTES</span></span>

## <span data-ttu-id="7e0b4-125">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7e0b4-125">RELATED LINKS</span></span>

[<span data-ttu-id="7e0b4-126">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="7e0b4-126">Set-Clipboard</span></span>](Set-Clipboard.md)

