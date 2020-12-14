---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: c1cf126e41a5e918afffbc41d30f957e650efdf5
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564500"
---
# <span data-ttu-id="51710-102">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="51710-102">Set-Clipboard</span></span>

## <span data-ttu-id="51710-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="51710-103">SYNOPSIS</span></span>
<span data-ttu-id="51710-104">Définit l’entrée actuelle du presse-papiers Windows.</span><span class="sxs-lookup"><span data-stu-id="51710-104">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="51710-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="51710-105">SYNTAX</span></span>

### <span data-ttu-id="51710-106">Chaîne (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="51710-106">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51710-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="51710-107">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51710-108">Path</span><span class="sxs-lookup"><span data-stu-id="51710-108">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51710-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="51710-109">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="51710-110">Description</span><span class="sxs-lookup"><span data-stu-id="51710-110">DESCRIPTION</span></span>

<span data-ttu-id="51710-111">L' `Set-Clipboard` applet de commande définit l’entrée actuelle du presse-papiers Windows.</span><span class="sxs-lookup"><span data-stu-id="51710-111">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="51710-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="51710-112">EXAMPLES</span></span>

### <span data-ttu-id="51710-113">Exemple 1 : copier du texte dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="51710-113">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="51710-114">Exemple 2 : copier le contenu d’un répertoire dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="51710-114">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="51710-115">Cet exemple copie le contenu du dossier spécifié dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="51710-115">This example copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

### <span data-ttu-id="51710-116">Exemple 3 : copier le contenu d’un fichier dans le presse-papiers</span><span class="sxs-lookup"><span data-stu-id="51710-116">Example 3: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="51710-117">Cet exemple canalise le contenu d’un fichier dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="51710-117">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="51710-118">Dans cet exemple, nous obtenons une clé SSH publique pour pouvoir la coller dans une autre application, par exemple GitHub.</span><span class="sxs-lookup"><span data-stu-id="51710-118">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="51710-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51710-119">PARAMETERS</span></span>

### <span data-ttu-id="51710-120">-Append</span><span class="sxs-lookup"><span data-stu-id="51710-120">-Append</span></span>

<span data-ttu-id="51710-121">Indique que l’applet de commande n’efface pas le presse-papiers et y ajoute du contenu.</span><span class="sxs-lookup"><span data-stu-id="51710-121">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="51710-122">-AsHtml</span><span class="sxs-lookup"><span data-stu-id="51710-122">-AsHtml</span></span>

<span data-ttu-id="51710-123">Indique que l’applet de commande affiche le contenu au format HTML dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="51710-123">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="51710-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="51710-124">-LiteralPath</span></span>

<span data-ttu-id="51710-125">Spécifie le chemin d’accès à l’élément copié dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="51710-125">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="51710-126">Contrairement au paramètre **Path**, la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="51710-126">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="51710-127">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="51710-127">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="51710-128">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="51710-128">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="51710-129">Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="51710-129">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="51710-130">-Path</span><span class="sxs-lookup"><span data-stu-id="51710-130">-Path</span></span>

<span data-ttu-id="51710-131">Spécifie le chemin d’accès à l’élément copié dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="51710-131">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="51710-132">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="51710-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="51710-133">-Value</span><span class="sxs-lookup"><span data-stu-id="51710-133">-Value</span></span>

<span data-ttu-id="51710-134">Spécifie, sous forme de tableau de chaînes, le contenu à copier dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="51710-134">Specifies, as a string array, the content to copy to the clipboard.</span></span>

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

### <span data-ttu-id="51710-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="51710-135">-Confirm</span></span>

<span data-ttu-id="51710-136">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="51710-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="51710-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="51710-137">-WhatIf</span></span>

<span data-ttu-id="51710-138">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="51710-138">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="51710-139">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="51710-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="51710-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51710-140">CommonParameters</span></span>

<span data-ttu-id="51710-141">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51710-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51710-142">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="51710-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51710-143">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="51710-143">INPUTS</span></span>

### <span data-ttu-id="51710-144">System.String[]</span><span class="sxs-lookup"><span data-stu-id="51710-144">System.String[]</span></span>

## <span data-ttu-id="51710-145">SORTIES</span><span class="sxs-lookup"><span data-stu-id="51710-145">OUTPUTS</span></span>

## <span data-ttu-id="51710-146">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="51710-146">NOTES</span></span>

<span data-ttu-id="51710-147">Dans de rares cas `Set-Clipboard` , lorsque vous utilisez avec un nombre élevé de valeurs en succession rapide, comme dans une boucle, vous pouvez obtenir de manière sporadique une valeur vide à partir du presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="51710-147">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="51710-148">Cela peut être résolu à l’aide `Start-Sleep -Milliseconds 1` de dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="51710-148">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="51710-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="51710-149">RELATED LINKS</span></span>

[<span data-ttu-id="51710-150">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="51710-150">Get-Clipboard</span></span>](Get-Clipboard.md)
