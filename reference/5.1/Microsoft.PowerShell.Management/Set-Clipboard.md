---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: f3230c247296d5fd907d580e719cbbbc560183a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203521"
---
# <span data-ttu-id="e4e9a-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="e4e9a-103">Set-Clipboard</span></span>

## <span data-ttu-id="e4e9a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e4e9a-104">SYNOPSIS</span></span>
<span data-ttu-id="e4e9a-105">Définit l’entrée actuelle du presse-papiers Windows.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-105">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="e4e9a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e4e9a-106">SYNTAX</span></span>

### <span data-ttu-id="e4e9a-107">Chaîne (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="e4e9a-107">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e4e9a-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="e4e9a-108">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e4e9a-109">Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="e4e9a-109">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e4e9a-110">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e4e9a-110">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e4e9a-111">Description</span><span class="sxs-lookup"><span data-stu-id="e4e9a-111">DESCRIPTION</span></span>

<span data-ttu-id="e4e9a-112">L' `Set-Clipboard` applet de commande définit l’entrée actuelle du presse-papiers Windows.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-112">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="e4e9a-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e4e9a-113">EXAMPLES</span></span>

### <span data-ttu-id="e4e9a-114">Exemple 1 : copier du texte dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="e4e9a-114">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="e4e9a-115">Exemple 2 : copier le contenu d’un répertoire dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="e4e9a-115">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="e4e9a-116">Cette commande copie le contenu du dossier spécifié dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-116">This command copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

## <span data-ttu-id="e4e9a-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e4e9a-117">PARAMETERS</span></span>

### <span data-ttu-id="e4e9a-118">-Append</span><span class="sxs-lookup"><span data-stu-id="e4e9a-118">-Append</span></span>

<span data-ttu-id="e4e9a-119">Indique que l’applet de commande n’efface pas le presse-papiers et y ajoute du contenu.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-119">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="e4e9a-120">-AsHtml</span><span class="sxs-lookup"><span data-stu-id="e4e9a-120">-AsHtml</span></span>

<span data-ttu-id="e4e9a-121">Indique que l’applet de commande affiche le contenu au format HTML dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-121">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="e4e9a-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e4e9a-122">-LiteralPath</span></span>

<span data-ttu-id="e4e9a-123">Spécifie le chemin d’accès à l’élément copié dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-123">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="e4e9a-124">Contrairement au paramètre **Path** , la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-124">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="e4e9a-125">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e4e9a-126">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e4e9a-127">Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-127">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e4e9a-128">-Path</span><span class="sxs-lookup"><span data-stu-id="e4e9a-128">-Path</span></span>

<span data-ttu-id="e4e9a-129">Spécifie le chemin d’accès à l’élément copié dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-129">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="e4e9a-130">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-130">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e4e9a-131">-Value</span><span class="sxs-lookup"><span data-stu-id="e4e9a-131">-Value</span></span>

<span data-ttu-id="e4e9a-132">Spécifie, sous forme de tableau de chaînes, le contenu à copier dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-132">Specifies, as a string array, the content to copy to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Value
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e4e9a-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e4e9a-133">-Confirm</span></span>

<span data-ttu-id="e4e9a-134">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-134">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e4e9a-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e4e9a-135">-WhatIf</span></span>

<span data-ttu-id="e4e9a-136">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-136">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e4e9a-137">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-137">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e4e9a-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e4e9a-138">CommonParameters</span></span>

<span data-ttu-id="e4e9a-139">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e4e9a-140">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e4e9a-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e4e9a-141">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e4e9a-141">INPUTS</span></span>

### <span data-ttu-id="e4e9a-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e4e9a-142">System.String[]</span></span>

## <span data-ttu-id="e4e9a-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e4e9a-143">OUTPUTS</span></span>

## <span data-ttu-id="e4e9a-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e4e9a-144">NOTES</span></span>

<span data-ttu-id="e4e9a-145">Dans de rares cas `Set-Clipboard` , lorsque vous utilisez avec un nombre élevé de valeurs en succession rapide, comme dans une boucle, vous pouvez obtenir de manière sporadique une valeur vide à partir du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-145">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="e4e9a-146">Cela peut être résolu à l’aide `Start-Sleep -Milliseconds 1` de dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="e4e9a-146">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="e4e9a-147">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e4e9a-147">RELATED LINKS</span></span>

[<span data-ttu-id="e4e9a-148">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="e4e9a-148">Get-Clipboard</span></span>](Get-Clipboard.md)
