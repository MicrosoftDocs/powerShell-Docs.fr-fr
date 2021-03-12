---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-MarkdownOption
ms.openlocfilehash: 5e19dc25d0b10888f6ce2f915926610f0780daf6
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195324"
---
# <span data-ttu-id="4788a-102">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="4788a-102">Set-MarkdownOption</span></span>

## <span data-ttu-id="4788a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4788a-103">SYNOPSIS</span></span>
<span data-ttu-id="4788a-104">Définit les couleurs et les styles utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="4788a-104">Sets the colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="4788a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4788a-105">SYNTAX</span></span>

### <span data-ttu-id="4788a-106">IndividualSetting (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4788a-106">IndividualSetting (Default)</span></span>

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### <span data-ttu-id="4788a-107">Thème</span><span class="sxs-lookup"><span data-stu-id="4788a-107">Theme</span></span>

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### <span data-ttu-id="4788a-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="4788a-108">InputObject</span></span>

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## <span data-ttu-id="4788a-109">Description</span><span class="sxs-lookup"><span data-stu-id="4788a-109">DESCRIPTION</span></span>

<span data-ttu-id="4788a-110">Définit les couleurs et les styles utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="4788a-110">Sets the colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="4788a-111">Ces styles sont définis à l’aide de codes d’échappement ANSI qui modifient la couleur et le style du texte de la démarque en cours de rendu.</span><span class="sxs-lookup"><span data-stu-id="4788a-111">These styles are defined using ANSI escape codes that change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="4788a-112">Pour plus d’informations sur la démarque, consultez le site Web [CommonMark](https://commonmark.org/) .</span><span class="sxs-lookup"><span data-stu-id="4788a-112">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

> [!NOTE]
> <span data-ttu-id="4788a-113">Les valeurs de chaîne utilisées dans les paramètres sont les caractères qui suivent le caractère d' **échappement** ( `[char]0x1B` ) pour la séquence d’échappement ANSI.</span><span class="sxs-lookup"><span data-stu-id="4788a-113">The string values used in the settings are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="4788a-114">N’incluez pas le caractère d' **échappement** dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="4788a-114">Do not include the **Escape** character in the string.</span></span> <span data-ttu-id="4788a-115">Pour plus d’informations sur le fonctionnement des codes d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="4788a-115">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="4788a-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4788a-116">EXAMPLES</span></span>

### <span data-ttu-id="4788a-117">Exemple 1-basculer vers le thème clair</span><span class="sxs-lookup"><span data-stu-id="4788a-117">Example 1 - Switch to the Light Theme</span></span>

<span data-ttu-id="4788a-118">Cet exemple sélectionne le thème **clair** et affiche la nouvelle configuration à l’aide du paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="4788a-118">This example selects the **Light** theme and displays the new configuration using the **PassThru** parameter.</span></span>

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### <span data-ttu-id="4788a-119">Exemple 2 : personnaliser les paramètres de couleur et de style</span><span class="sxs-lookup"><span data-stu-id="4788a-119">Example 2 - Customize the color and style settings</span></span>

<span data-ttu-id="4788a-120">Cet exemple modifie le code d’échappement pour les en-têtes de démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-120">This example changes the escape code for the Markdown headers.</span></span> <span data-ttu-id="4788a-121">La configuration par défaut des en-têtes les restitue sous forme de texte souligné de différentes couleurs.</span><span class="sxs-lookup"><span data-stu-id="4788a-121">The default configuration for headers renders them as underlined text of various colors.</span></span> <span data-ttu-id="4788a-122">Cette modification supprime le style de soulignement.</span><span class="sxs-lookup"><span data-stu-id="4788a-122">This change removes the underline style.</span></span>

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## <span data-ttu-id="4788a-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4788a-123">PARAMETERS</span></span>

### <span data-ttu-id="4788a-124">-BoldForegroundColor</span><span class="sxs-lookup"><span data-stu-id="4788a-124">-BoldForegroundColor</span></span>

<span data-ttu-id="4788a-125">Définit la couleur de premier plan pour le rendu du texte de démarque gras.</span><span class="sxs-lookup"><span data-stu-id="4788a-125">Sets the foreground color for rendering bold Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-126">-Code</span><span class="sxs-lookup"><span data-stu-id="4788a-126">-Code</span></span>

<span data-ttu-id="4788a-127">Définit la couleur de rendu des blocs de code et des étendues dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-127">Sets the color for rendering code blocks and spans in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-128">-Header1Color</span><span class="sxs-lookup"><span data-stu-id="4788a-128">-Header1Color</span></span>

<span data-ttu-id="4788a-129">Définit la couleur de rendu des blocs Header1 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-129">Sets the color for rendering Header1 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-130">-Header2Color</span><span class="sxs-lookup"><span data-stu-id="4788a-130">-Header2Color</span></span>

<span data-ttu-id="4788a-131">Définit la couleur de rendu des blocs Header2 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-131">Sets the color for rendering Header2 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-132">-Header3Color</span><span class="sxs-lookup"><span data-stu-id="4788a-132">-Header3Color</span></span>

<span data-ttu-id="4788a-133">Définit la couleur de rendu des blocs Header3 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-133">Sets the color for rendering Header3 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-134">-Header4Color</span><span class="sxs-lookup"><span data-stu-id="4788a-134">-Header4Color</span></span>

<span data-ttu-id="4788a-135">Définit la couleur de rendu des blocs Header4 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-135">Sets the color for rendering Header4 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-136">-Header5Color</span><span class="sxs-lookup"><span data-stu-id="4788a-136">-Header5Color</span></span>

<span data-ttu-id="4788a-137">Définit la couleur de rendu des blocs Header5 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-137">Sets the color for rendering Header5 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-138">-Header6Color</span><span class="sxs-lookup"><span data-stu-id="4788a-138">-Header6Color</span></span>

<span data-ttu-id="4788a-139">Définit la couleur de rendu des blocs Header6 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-139">Sets the color for rendering Header6 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-140">-ImageAltTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="4788a-140">-ImageAltTextForegroundColor</span></span>

<span data-ttu-id="4788a-141">Définit la couleur de premier plan pour le rendu du texte de remplacement d’un élément image dans le texte de démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-141">Sets the foreground color for rendering the alternate text of an image element in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4788a-142">-InputObject</span></span>

<span data-ttu-id="4788a-143">Objet **PSMarkdownOptionInfo** contenant la configuration à définir.</span><span class="sxs-lookup"><span data-stu-id="4788a-143">A **PSMarkdownOptionInfo** object containing the configuration to be set.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-144">-ItalicsForegroundColor</span><span class="sxs-lookup"><span data-stu-id="4788a-144">-ItalicsForegroundColor</span></span>

<span data-ttu-id="4788a-145">Définit la couleur de premier plan pour le rendu de l’italique dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-145">Sets the foreground color for rendering the italics in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-146">-LinkForegroundColor</span><span class="sxs-lookup"><span data-stu-id="4788a-146">-LinkForegroundColor</span></span>

<span data-ttu-id="4788a-147">Définit la couleur de premier plan pour le rendu des liens hypertexte dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="4788a-147">Sets the foreground color for rendering hyperlinks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-148">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4788a-148">-PassThru</span></span>

<span data-ttu-id="4788a-149">Fait en sorte que l’applet de commande génère un objet **PSMarkdownOptionInfo** contenant la nouvelle configuration.</span><span class="sxs-lookup"><span data-stu-id="4788a-149">Causes the cmdlet to output a **PSMarkdownOptionInfo** object containing the new configuration.</span></span>

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

### <span data-ttu-id="4788a-150">-Thème</span><span class="sxs-lookup"><span data-stu-id="4788a-150">-Theme</span></span>

<span data-ttu-id="4788a-151">Sélectionne un thème contenant des paramètres de couleur prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="4788a-151">Selects a theme containing predefined color settings.</span></span> <span data-ttu-id="4788a-152">Les valeurs possibles sont **Dark** et **Light**.</span><span class="sxs-lookup"><span data-stu-id="4788a-152">The possible values are **Dark** and **Light**.</span></span>

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4788a-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4788a-153">CommonParameters</span></span>

<span data-ttu-id="4788a-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4788a-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4788a-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4788a-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4788a-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4788a-156">INPUTS</span></span>

### <span data-ttu-id="4788a-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="4788a-157">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="4788a-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4788a-158">OUTPUTS</span></span>

### <span data-ttu-id="4788a-159">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="4788a-159">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="4788a-160">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4788a-160">NOTES</span></span>

<span data-ttu-id="4788a-161">Les valeurs de chaîne utilisées pour définir la couleur et le style doivent correspondre à l’expression régulière `^\[*[0-9;]*?m{1}` .</span><span class="sxs-lookup"><span data-stu-id="4788a-161">The string values used to define the color and style must match the regular expression `^\[*[0-9;]*?m{1}`.</span></span>

## <span data-ttu-id="4788a-162">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4788a-162">RELATED LINKS</span></span>

[<span data-ttu-id="4788a-163">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="4788a-163">Get-MarkdownOption</span></span>](Get-MarkdownOption.md)

[<span data-ttu-id="4788a-164">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="4788a-164">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="4788a-165">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="4788a-165">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="4788a-166">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="4788a-166">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="4788a-167">CommonMark</span><span class="sxs-lookup"><span data-stu-id="4788a-167">CommonMark</span></span>](https://commonmark.org/)

