---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: 2d88b24519f472f0c167dc5138450ab542a8b7cf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204397"
---
# <span data-ttu-id="db16b-103">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="db16b-103">Show-Markdown</span></span>

## <span data-ttu-id="db16b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="db16b-104">SYNOPSIS</span></span>
<span data-ttu-id="db16b-105">Affiche un fichier de démarque ou une chaîne dans la console d’une manière conviviale à l’aide de séquences d’échappement VT100 ou dans un navigateur à l’aide de HTML.</span><span class="sxs-lookup"><span data-stu-id="db16b-105">Shows a Markdown file or string in the console in a friendly way using VT100 escape sequences or in a browser using HTML.</span></span>

## <span data-ttu-id="db16b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="db16b-106">SYNTAX</span></span>

### <span data-ttu-id="db16b-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="db16b-107">Path (Default)</span></span>

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="db16b-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="db16b-108">InputObject</span></span>

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="db16b-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="db16b-109">LiteralPath</span></span>

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## <span data-ttu-id="db16b-110">Description</span><span class="sxs-lookup"><span data-stu-id="db16b-110">DESCRIPTION</span></span>

<span data-ttu-id="db16b-111">L' `Show-Markdown` applet de commande est utilisée pour restituer la démarque dans un format lisible par l’utilisateur dans un terminal ou dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="db16b-111">The `Show-Markdown` cmdlet is used to render Markdown in a human readable format either in a terminal or in a browser.</span></span>

<span data-ttu-id="db16b-112">`Show-Markdown` peut retourner une chaîne qui comprend les séquences d’échappement VT100 que le terminal restitue (s’il prend en charge les séquences d’échappement VT100).</span><span class="sxs-lookup"><span data-stu-id="db16b-112">`Show-Markdown` can return a string that includes the VT100 escape sequences which the terminal renders (if it supports VT100 escape sequences).</span></span> <span data-ttu-id="db16b-113">Il est principalement utilisé pour afficher les fichiers de démarque dans un terminal.</span><span class="sxs-lookup"><span data-stu-id="db16b-113">This is primarily used for viewing Markdown files in a terminal.</span></span> <span data-ttu-id="db16b-114">Vous pouvez également récupérer cette chaîne via la `ConvertFrom-Markdown` en spécifiant le paramètre **AsVT100EncodedString** .</span><span class="sxs-lookup"><span data-stu-id="db16b-114">You can also get this string via the `ConvertFrom-Markdown` by specifying the **AsVT100EncodedString** parameter.</span></span>

<span data-ttu-id="db16b-115">`Show-Markdown` a également la possibilité d’ouvrir un navigateur et d’afficher une version rendue de la démarque.</span><span class="sxs-lookup"><span data-stu-id="db16b-115">`Show-Markdown` also has the ability to open a browser and show you a rendered version of the Markdown.</span></span> <span data-ttu-id="db16b-116">Il affiche la démarque en le convertissant en HTML et en ouvrant le fichier HTML dans votre navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="db16b-116">It renders the Markdown by turning it into HTML and opening the HTML file in your default browser.</span></span>

<span data-ttu-id="db16b-117">Vous pouvez modifier le `Show-Markdown` rendu du démarque dans un terminal à l’aide de `Set-MarkdownOption` .</span><span class="sxs-lookup"><span data-stu-id="db16b-117">You can change how `Show-Markdown` renders Markdown in a terminal by using `Set-MarkdownOption`.</span></span>

<span data-ttu-id="db16b-118">Cette applet de commande a été introduite dans PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="db16b-118">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="db16b-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="db16b-119">EXAMPLES</span></span>

### <span data-ttu-id="db16b-120">Exemple 1 : exemple simple spécifiant un chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="db16b-120">Example 1: Simple example specifying a path</span></span>

```powershell
Show-Markdown -Path ./README.md
```

### <span data-ttu-id="db16b-121">Exemple 2 : exemple simple spécifiant une chaîne</span><span class="sxs-lookup"><span data-stu-id="db16b-121">Example 2: Simple example specifying a string</span></span>

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### <span data-ttu-id="db16b-122">Exemple 2 : ouverture d’une démarque dans un navigateur</span><span class="sxs-lookup"><span data-stu-id="db16b-122">Example 2: Opening Markdown in a browser</span></span>

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## <span data-ttu-id="db16b-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db16b-123">PARAMETERS</span></span>

### <span data-ttu-id="db16b-124">-InputObject</span><span class="sxs-lookup"><span data-stu-id="db16b-124">-InputObject</span></span>

<span data-ttu-id="db16b-125">Chaîne de démarque qui s’affiche dans le terminal.</span><span class="sxs-lookup"><span data-stu-id="db16b-125">A Markdown string that will be shown in the terminal.</span></span> <span data-ttu-id="db16b-126">Si vous ne transmettez pas un format pris en charge, `Show-Markdown` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="db16b-126">If you do not pass in a supported format, `Show-Markdown` will emit an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="db16b-127">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="db16b-127">-LiteralPath</span></span>

<span data-ttu-id="db16b-128">Spécifie le chemin d’accès à un fichier de démarque.</span><span class="sxs-lookup"><span data-stu-id="db16b-128">Specifies the path to a Markdown file.</span></span> <span data-ttu-id="db16b-129">Contrairement au paramètre Path, la valeur du paramètre LiteralPath est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="db16b-129">Unlike the Path parameter, the value of LiteralPath is used exactly as it is typed.</span></span> <span data-ttu-id="db16b-130">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="db16b-130">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="db16b-131">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="db16b-131">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="db16b-132">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="db16b-132">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="db16b-133">-Path</span><span class="sxs-lookup"><span data-stu-id="db16b-133">-Path</span></span>

<span data-ttu-id="db16b-134">Spécifie le chemin d’accès à un fichier de démarques à rendre.</span><span class="sxs-lookup"><span data-stu-id="db16b-134">Specifies the path to a Markdown file to be rendered.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="db16b-135">-UseBrowser</span><span class="sxs-lookup"><span data-stu-id="db16b-135">-UseBrowser</span></span>

<span data-ttu-id="db16b-136">Compile l’entrée de la démarque en HTML et l’ouvre dans votre navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="db16b-136">Compiles the Markdown input as HTML and opens it in your default browser.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db16b-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db16b-137">CommonParameters</span></span>

<span data-ttu-id="db16b-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="db16b-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db16b-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="db16b-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="db16b-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="db16b-140">INPUTS</span></span>

### <span data-ttu-id="db16b-141">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="db16b-141">System.Management.Automation.PSObject</span></span>

### <span data-ttu-id="db16b-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="db16b-142">System.String[]</span></span>

## <span data-ttu-id="db16b-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="db16b-143">OUTPUTS</span></span>

### <span data-ttu-id="db16b-144">System.String</span><span class="sxs-lookup"><span data-stu-id="db16b-144">System.String</span></span>

## <span data-ttu-id="db16b-145">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="db16b-145">NOTES</span></span>

## <span data-ttu-id="db16b-146">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="db16b-146">RELATED LINKS</span></span>

[<span data-ttu-id="db16b-147">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="db16b-147">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)
