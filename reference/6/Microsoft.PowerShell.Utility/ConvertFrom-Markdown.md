---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: PowerShell, applet de commande, démarque
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: efa5e65566e3b80f12f3de5ebd1277bf68c03ff0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204705"
---
# <span data-ttu-id="608a0-103">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="608a0-103">ConvertFrom-Markdown</span></span>

## <span data-ttu-id="608a0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="608a0-104">SYNOPSIS</span></span>
<span data-ttu-id="608a0-105">Convertit le contenu d’une chaîne ou d’un fichier en objet **MarkdownInfo** .</span><span class="sxs-lookup"><span data-stu-id="608a0-105">Convert the contents of a string or a file to a **MarkdownInfo** object.</span></span>

## <span data-ttu-id="608a0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="608a0-106">SYNTAX</span></span>

### <span data-ttu-id="608a0-107">PathParamSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="608a0-107">PathParamSet (Default)</span></span>

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="608a0-108">LiteralParamSet</span><span class="sxs-lookup"><span data-stu-id="608a0-108">LiteralParamSet</span></span>

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="608a0-109">InputObjParamSet</span><span class="sxs-lookup"><span data-stu-id="608a0-109">InputObjParamSet</span></span>

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## <span data-ttu-id="608a0-110">Description</span><span class="sxs-lookup"><span data-stu-id="608a0-110">DESCRIPTION</span></span>

<span data-ttu-id="608a0-111">Cette applet de commande convertit le contenu spécifié en **MarkdownInfo** .</span><span class="sxs-lookup"><span data-stu-id="608a0-111">This cmdlet converts the specified content into a **MarkdownInfo** .</span></span> <span data-ttu-id="608a0-112">Quand un chemin d’accès de fichier est spécifié pour le paramètre **path** , le contenu du fichier est converti.</span><span class="sxs-lookup"><span data-stu-id="608a0-112">When a file path is specified for the **Path** parameter, the contents on the file are converted.</span></span> <span data-ttu-id="608a0-113">L’objet de sortie a trois propriétés :</span><span class="sxs-lookup"><span data-stu-id="608a0-113">The output object has three properties:</span></span>

- <span data-ttu-id="608a0-114">La propriété **Token** a l’arborescence de syntaxe abstraite (AST) de l’objet converti</span><span class="sxs-lookup"><span data-stu-id="608a0-114">The **Token** property has the abstract syntax tree (AST) of the the converted object</span></span>
- <span data-ttu-id="608a0-115">La propriété **HTML** contient la conversion HTML de l’entrée spécifiée</span><span class="sxs-lookup"><span data-stu-id="608a0-115">The **Html** property has the HTML conversion of the specified input</span></span>
- <span data-ttu-id="608a0-116">La propriété **VT100EncodedString** contient la chaîne convertie avec des séquences d’échappement ANSI (VT100) si le paramètre **AsVT100EncodedString** a été spécifié</span><span class="sxs-lookup"><span data-stu-id="608a0-116">The **VT100EncodedString** property has the converted string with ANSI (VT100) escape sequences if the **AsVT100EncodedString** parameter was specified</span></span>

<span data-ttu-id="608a0-117">Cette applet de commande a été introduite dans PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="608a0-117">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="608a0-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="608a0-118">EXAMPLES</span></span>

### <span data-ttu-id="608a0-119">Exemple 1 : convertir un fichier contenant le contenu de la démarque en HTML</span><span class="sxs-lookup"><span data-stu-id="608a0-119">Example 1: Convert a file containing Markdown content to HTML</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md
```

<span data-ttu-id="608a0-120">L’objet **MarkdownInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="608a0-120">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="608a0-121">La propriété **tokens** contient l’AST du contenu converti du `README.md` fichier.</span><span class="sxs-lookup"><span data-stu-id="608a0-121">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="608a0-122">La propriété **HTML** contient le contenu HTML converti du `README.md` fichier.</span><span class="sxs-lookup"><span data-stu-id="608a0-122">The **Html** property has the HTML converted content of the `README.md` file.</span></span>

### <span data-ttu-id="608a0-123">Exemple 2 : convertir un fichier contenant le contenu de la démarque en une chaîne encodée en VT100</span><span class="sxs-lookup"><span data-stu-id="608a0-123">Example 2: Convert a file containing Markdown content to a VT100-encoded string</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

<span data-ttu-id="608a0-124">L’objet **MarkdownInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="608a0-124">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="608a0-125">La propriété **tokens** contient l’AST du contenu converti du `README.md` fichier.</span><span class="sxs-lookup"><span data-stu-id="608a0-125">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="608a0-126">La valeur de la propriété **VT100EncodedString** de la chaîne encodée en VT100 du fichier est convertie `README.md` .</span><span class="sxs-lookup"><span data-stu-id="608a0-126">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="608a0-127">Exemple 3 : convertir un objet d’entrée contenant le contenu de la démarque en une chaîne encodée en VT100</span><span class="sxs-lookup"><span data-stu-id="608a0-127">Example 3: Convert input object containing Markdown content to a VT100-encoded string</span></span>

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="608a0-128">L’objet **MarkdownInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="608a0-128">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="608a0-129">L’objet **FileInfo** de `Get-Item` est converti en une chaîne encodée en VT100.</span><span class="sxs-lookup"><span data-stu-id="608a0-129">The **FileInfo** object from `Get-Item` is converted to a VT100-encoded string.</span></span> <span data-ttu-id="608a0-130">La propriété **tokens** contient l’AST du contenu converti du `README.md` fichier.</span><span class="sxs-lookup"><span data-stu-id="608a0-130">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="608a0-131">La valeur de la propriété **VT100EncodedString** de la chaîne encodée en VT100 du fichier est convertie `README.md` .</span><span class="sxs-lookup"><span data-stu-id="608a0-131">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="608a0-132">Exemple 4 : convertir une chaîne contenant le contenu de la démarque en une chaîne encodée en VT100</span><span class="sxs-lookup"><span data-stu-id="608a0-132">Example 4: Convert a string containing Markdown content to a VT100-encoded string</span></span>

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="608a0-133">L’objet **MarkdownInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="608a0-133">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="608a0-134">La chaîne spécifiée `**Bold text**` est convertie en une chaîne encodée en VT100 et disponible dans la propriété **VT100EncodedString** .</span><span class="sxs-lookup"><span data-stu-id="608a0-134">The specified string `**Bold text**` is converted to a VT100-encoded string and available in **VT100EncodedString** property.</span></span>

## <span data-ttu-id="608a0-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="608a0-135">PARAMETERS</span></span>

### <span data-ttu-id="608a0-136">-AsVT100EncodedString</span><span class="sxs-lookup"><span data-stu-id="608a0-136">-AsVT100EncodedString</span></span>

<span data-ttu-id="608a0-137">Spécifie si la sortie doit être encodée sous la forme d’une chaîne avec des codes d’échappement VT100.</span><span class="sxs-lookup"><span data-stu-id="608a0-137">Specifies if the output should be encoded as a string with VT100 escape codes.</span></span>

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

### <span data-ttu-id="608a0-138">-InputObject</span><span class="sxs-lookup"><span data-stu-id="608a0-138">-InputObject</span></span>

<span data-ttu-id="608a0-139">Spécifie l'objet à convertir.</span><span class="sxs-lookup"><span data-stu-id="608a0-139">Specifies the object to be converted.</span></span> <span data-ttu-id="608a0-140">Lorsqu’un objet de type **System. String** est spécifié, la chaîne est convertie.</span><span class="sxs-lookup"><span data-stu-id="608a0-140">When an object of type **System.String** is specified, the string is converted.</span></span> <span data-ttu-id="608a0-141">Lorsqu’un objet de type **System. IO. FileInfo** est spécifié, le contenu du fichier spécifié par l’objet est converti.</span><span class="sxs-lookup"><span data-stu-id="608a0-141">When an object of type **System.IO.FileInfo** is specified, the contents of the file specified by the object are converted.</span></span> <span data-ttu-id="608a0-142">Les objets de tout autre type provoquent une erreur.</span><span class="sxs-lookup"><span data-stu-id="608a0-142">Objects of any other type result in an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="608a0-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="608a0-143">-LiteralPath</span></span>

<span data-ttu-id="608a0-144">Spécifie un chemin d’accès au fichier à convertir.</span><span class="sxs-lookup"><span data-stu-id="608a0-144">Specifies a path to the file to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="608a0-145">-Path</span><span class="sxs-lookup"><span data-stu-id="608a0-145">-Path</span></span>

<span data-ttu-id="608a0-146">Spécifie un chemin d’accès au fichier à convertir.</span><span class="sxs-lookup"><span data-stu-id="608a0-146">Specifies a path to the file to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="608a0-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="608a0-147">CommonParameters</span></span>

<span data-ttu-id="608a0-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="608a0-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="608a0-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="608a0-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="608a0-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="608a0-150">INPUTS</span></span>

### <span data-ttu-id="608a0-151">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="608a0-151">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="608a0-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="608a0-152">OUTPUTS</span></span>

### <span data-ttu-id="608a0-153">Microsoft. PowerShell. MarkdownRender. MarkdownInfo</span><span class="sxs-lookup"><span data-stu-id="608a0-153">Microsoft.PowerShell.MarkdownRender.MarkdownInfo</span></span>

## <span data-ttu-id="608a0-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="608a0-154">NOTES</span></span>

## <span data-ttu-id="608a0-155">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="608a0-155">RELATED LINKS</span></span>

[<span data-ttu-id="608a0-156">Analyseur de démarque</span><span class="sxs-lookup"><span data-stu-id="608a0-156">Markdown Parser</span></span>](https://github.com/lunet-io/markdig)

[<span data-ttu-id="608a0-157">Code d’échappement ANSI</span><span class="sxs-lookup"><span data-stu-id="608a0-157">ANSI escape code</span></span>](https://wikipedia.org/wiki/ANSI_escape_code)
