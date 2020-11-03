---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: e7e70637afcf53f84c719b489575f5267f9048b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202194"
---
# <span data-ttu-id="a8f19-101">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="a8f19-101">Set-MarkdownOption</span></span>

## <span data-ttu-id="a8f19-102">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a8f19-102">SYNOPSIS</span></span>
<span data-ttu-id="a8f19-103">Définit les couleurs et les styles utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="a8f19-103">Sets the colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="a8f19-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a8f19-104">SYNTAX</span></span>

### <span data-ttu-id="a8f19-105">IndividualSetting (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a8f19-105">IndividualSetting (Default)</span></span>

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### <span data-ttu-id="a8f19-106">Thème</span><span class="sxs-lookup"><span data-stu-id="a8f19-106">Theme</span></span>

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### <span data-ttu-id="a8f19-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="a8f19-107">InputObject</span></span>

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## <span data-ttu-id="a8f19-108">Description</span><span class="sxs-lookup"><span data-stu-id="a8f19-108">DESCRIPTION</span></span>

<span data-ttu-id="a8f19-109">Définit les couleurs et les styles utilisés pour le rendu du contenu de la démarque dans la console.</span><span class="sxs-lookup"><span data-stu-id="a8f19-109">Sets the colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="a8f19-110">Ces styles sont définis à l’aide de codes d’échappement ANSI qui modifient la couleur et le style du texte de la démarque en cours de rendu.</span><span class="sxs-lookup"><span data-stu-id="a8f19-110">These styles are defined using ANSI escape codes that change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="a8f19-111">Pour plus d’informations sur la démarque, consultez le site Web [CommonMark](https://commonmark.org/) .</span><span class="sxs-lookup"><span data-stu-id="a8f19-111">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

> [!NOTE]
> <span data-ttu-id="a8f19-112">Les valeurs de chaîne utilisées dans les paramètres sont les caractères qui suivent le caractère d' **échappement** ( `[char]0x1B` ) pour la séquence d’échappement ANSI.</span><span class="sxs-lookup"><span data-stu-id="a8f19-112">The string values used in the settings are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="a8f19-113">N’incluez pas le caractère d' **échappement** dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="a8f19-113">Do not include the **Escape** character in the string.</span></span> <span data-ttu-id="a8f19-114">Pour plus d’informations sur le fonctionnement des codes d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="a8f19-114">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="a8f19-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a8f19-115">EXAMPLES</span></span>

### <span data-ttu-id="a8f19-116">Exemple 1-basculer vers le thème clair</span><span class="sxs-lookup"><span data-stu-id="a8f19-116">Example 1 - Switch to the Light Theme</span></span>

<span data-ttu-id="a8f19-117">Cet exemple sélectionne le thème **clair** et affiche la nouvelle configuration à l’aide du paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="a8f19-117">This example selects the **Light** theme and displays the new configuration using the **PassThru** parameter.</span></span>

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

### <span data-ttu-id="a8f19-118">Exemple 2 : personnaliser les paramètres de couleur et de style</span><span class="sxs-lookup"><span data-stu-id="a8f19-118">Example 2 - Customize the color and style settings</span></span>

<span data-ttu-id="a8f19-119">Cet exemple modifie le code d’échappement pour les en-têtes de démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-119">This example changes the escape code for the Markdown headers.</span></span> <span data-ttu-id="a8f19-120">La configuration par défaut des en-têtes les restitue sous forme de texte souligné de différentes couleurs.</span><span class="sxs-lookup"><span data-stu-id="a8f19-120">The default configuration for headers renders them as underlined text of various colors.</span></span> <span data-ttu-id="a8f19-121">Cette modification supprime le style de soulignement.</span><span class="sxs-lookup"><span data-stu-id="a8f19-121">This change removes the underline style.</span></span>

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

## <span data-ttu-id="a8f19-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8f19-122">PARAMETERS</span></span>

### <span data-ttu-id="a8f19-123">-BoldForegroundColor</span><span class="sxs-lookup"><span data-stu-id="a8f19-123">-BoldForegroundColor</span></span>

<span data-ttu-id="a8f19-124">Définit la couleur de premier plan pour le rendu du texte de démarque gras.</span><span class="sxs-lookup"><span data-stu-id="a8f19-124">Sets the foreground color for rendering bold Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-125">-Code</span><span class="sxs-lookup"><span data-stu-id="a8f19-125">-Code</span></span>

<span data-ttu-id="a8f19-126">Définit la couleur de rendu des blocs de code et des étendues dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-126">Sets the color for rendering code blocks and spans in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-127">-Header1Color</span><span class="sxs-lookup"><span data-stu-id="a8f19-127">-Header1Color</span></span>

<span data-ttu-id="a8f19-128">Définit la couleur de rendu des blocs Header1 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-128">Sets the color for rendering Header1 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-129">-Header2Color</span><span class="sxs-lookup"><span data-stu-id="a8f19-129">-Header2Color</span></span>

<span data-ttu-id="a8f19-130">Définit la couleur de rendu des blocs Header2 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-130">Sets the color for rendering Header2 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-131">-Header3Color</span><span class="sxs-lookup"><span data-stu-id="a8f19-131">-Header3Color</span></span>

<span data-ttu-id="a8f19-132">Définit la couleur de rendu des blocs Header3 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-132">Sets the color for rendering Header3 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-133">-Header4Color</span><span class="sxs-lookup"><span data-stu-id="a8f19-133">-Header4Color</span></span>

<span data-ttu-id="a8f19-134">Définit la couleur de rendu des blocs Header4 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-134">Sets the color for rendering Header4 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-135">-Header5Color</span><span class="sxs-lookup"><span data-stu-id="a8f19-135">-Header5Color</span></span>

<span data-ttu-id="a8f19-136">Définit la couleur de rendu des blocs Header5 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-136">Sets the color for rendering Header5 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-137">-Header6Color</span><span class="sxs-lookup"><span data-stu-id="a8f19-137">-Header6Color</span></span>

<span data-ttu-id="a8f19-138">Définit la couleur de rendu des blocs Header6 dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-138">Sets the color for rendering Header6 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-139">-ImageAltTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="a8f19-139">-ImageAltTextForegroundColor</span></span>

<span data-ttu-id="a8f19-140">Définit la couleur de premier plan pour le rendu du texte de remplacement d’un élément image dans le texte de démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-140">Sets the foreground color for rendering the alternate text of an image element in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a8f19-141">-InputObject</span></span>

<span data-ttu-id="a8f19-142">Objet **PSMarkdownOptionInfo** contenant la configuration à définir.</span><span class="sxs-lookup"><span data-stu-id="a8f19-142">A **PSMarkdownOptionInfo** object containing the configuration to be set.</span></span>

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

### <span data-ttu-id="a8f19-143">-ItalicsForegroundColor</span><span class="sxs-lookup"><span data-stu-id="a8f19-143">-ItalicsForegroundColor</span></span>

<span data-ttu-id="a8f19-144">Définit la couleur de premier plan pour le rendu de l’italique dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-144">Sets the foreground color for rendering the italics in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-145">-LinkForegroundColor</span><span class="sxs-lookup"><span data-stu-id="a8f19-145">-LinkForegroundColor</span></span>

<span data-ttu-id="a8f19-146">Définit la couleur de premier plan pour le rendu des liens hypertexte dans le texte de la démarque.</span><span class="sxs-lookup"><span data-stu-id="a8f19-146">Sets the foreground color for rendering hyperlinks in Markdown text.</span></span>

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

### <span data-ttu-id="a8f19-147">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a8f19-147">-PassThru</span></span>

<span data-ttu-id="a8f19-148">Fait en sorte que l’applet de commande génère un objet **PSMarkdownOptionInfo** contenant la nouvelle configuration.</span><span class="sxs-lookup"><span data-stu-id="a8f19-148">Causes the cmdlet to output a **PSMarkdownOptionInfo** object containing the new configuration.</span></span>

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

### <span data-ttu-id="a8f19-149">-Thème</span><span class="sxs-lookup"><span data-stu-id="a8f19-149">-Theme</span></span>

<span data-ttu-id="a8f19-150">Sélectionne un thème contenant des paramètres de couleur prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="a8f19-150">Selects a theme containing predefined color settings.</span></span> <span data-ttu-id="a8f19-151">Les valeurs possibles sont **Dark** et **Light** .</span><span class="sxs-lookup"><span data-stu-id="a8f19-151">The possible values are **Dark** and **Light** .</span></span>

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

### <span data-ttu-id="a8f19-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8f19-152">CommonParameters</span></span>

<span data-ttu-id="a8f19-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a8f19-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a8f19-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a8f19-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a8f19-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a8f19-155">INPUTS</span></span>

### <span data-ttu-id="a8f19-156">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="a8f19-156">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="a8f19-157">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a8f19-157">OUTPUTS</span></span>

### <span data-ttu-id="a8f19-158">Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="a8f19-158">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="a8f19-159">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a8f19-159">NOTES</span></span>

<span data-ttu-id="a8f19-160">Les valeurs de chaîne utilisées pour définir la couleur et le style doivent correspondre à l’expression régulière `^\[*[0-9;]*?m{1}` .</span><span class="sxs-lookup"><span data-stu-id="a8f19-160">The string values used to define the color and style must match the regular expression `^\[*[0-9;]*?m{1}`.</span></span>

## <span data-ttu-id="a8f19-161">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a8f19-161">RELATED LINKS</span></span>

[<span data-ttu-id="a8f19-162">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="a8f19-162">Get-MarkdownOption</span></span>](Get-MarkdownOption.md)

[<span data-ttu-id="a8f19-163">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="a8f19-163">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="a8f19-164">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="a8f19-164">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="a8f19-165">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="a8f19-165">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="a8f19-166">CommonMark</span><span class="sxs-lookup"><span data-stu-id="a8f19-166">CommonMark</span></span>](https://commonmark.org/)

