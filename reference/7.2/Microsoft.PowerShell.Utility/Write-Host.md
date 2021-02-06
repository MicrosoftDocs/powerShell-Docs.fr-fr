---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: 01d045a6254b40161462bf36976fdbf57f205705
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597766"
---
# <span data-ttu-id="1d12d-102">Write-Host</span><span class="sxs-lookup"><span data-stu-id="1d12d-102">Write-Host</span></span>

## <span data-ttu-id="1d12d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1d12d-103">SYNOPSIS</span></span>

<span data-ttu-id="1d12d-104">Écrit la sortie personnalisée sur un hôte.</span><span class="sxs-lookup"><span data-stu-id="1d12d-104">Writes customized output to a host.</span></span>

## <span data-ttu-id="1d12d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="1d12d-105">SYNTAX</span></span>

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## <span data-ttu-id="1d12d-106">Description</span><span class="sxs-lookup"><span data-stu-id="1d12d-106">DESCRIPTION</span></span>

<span data-ttu-id="1d12d-107">L' `Write-Host` objectif principal de l’applet de commande est de produire pour la sortie-(hôte)-affichage uniquement, par exemple l’impression d’un texte coloré comme lorsque vous invitez l’utilisateur à entrer des données conjointement avec l' [hôte de lecture](Read-Host.md).</span><span class="sxs-lookup"><span data-stu-id="1d12d-107">The `Write-Host` cmdlet's primary purpose is to produce for-(host)-display-only output, such as printing colored text like when prompting the user for input in conjunction with [Read-Host](Read-Host.md).</span></span>
<span data-ttu-id="1d12d-108">`Write-Host` utilise la méthode [ToString ()](/dotnet/api/system.object.tostring) pour écrire la sortie.</span><span class="sxs-lookup"><span data-stu-id="1d12d-108">`Write-Host` uses the [ToString()](/dotnet/api/system.object.tostring) method to write the output.</span></span> <span data-ttu-id="1d12d-109">En revanche, pour sortir des données dans le pipeline, utilisez la sortie [Write-Output](Write-Output.md) ou implicite.</span><span class="sxs-lookup"><span data-stu-id="1d12d-109">By contrast, to output data to the pipeline, use [Write-Output](Write-Output.md) or implicit output.</span></span>

<span data-ttu-id="1d12d-110">Vous pouvez spécifier la couleur du texte à l’aide du `ForegroundColor` paramètre, et vous pouvez spécifier la couleur d’arrière-plan à l’aide du `BackgroundColor` paramètre.</span><span class="sxs-lookup"><span data-stu-id="1d12d-110">You can specify the color of text by using the `ForegroundColor` parameter, and you can specify the background color by using the `BackgroundColor` parameter.</span></span> <span data-ttu-id="1d12d-111">Le paramètre Separator vous permet de spécifier une chaîne à utiliser pour séparer les objets affichés.</span><span class="sxs-lookup"><span data-stu-id="1d12d-111">The Separator parameter lets you specify a string to use to separate displayed objects.</span></span> <span data-ttu-id="1d12d-112">Le résultat donné dépend du programme qui héberge PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d12d-112">The particular result depends on the program that is hosting PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="1d12d-113">À compter de Windows PowerShell 5,0, `Write-Host` est un wrapper de `Write-Information` ce qui vous permet d’utiliser `Write-Host` pour émettre une sortie vers le flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="1d12d-113">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="1d12d-114">Cela permet la **capture** ou la **suppression** des données écrites à l’aide de `Write-Host` tout en préservant la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="1d12d-114">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span>
>
> <span data-ttu-id="1d12d-115">La `$InformationPreference` variable de préférence et le `InformationAction` paramètre commun n’affectent pas les `Write-Host` messages.</span><span class="sxs-lookup"><span data-stu-id="1d12d-115">The `$InformationPreference` preference variable and `InformationAction` common parameter do not affect `Write-Host` messages.</span></span> <span data-ttu-id="1d12d-116">L’exception à cette règle est `-InformationAction Ignore` , qui supprime effectivement la `Write-Host` sortie.</span><span class="sxs-lookup"><span data-stu-id="1d12d-116">The exception to this rule is `-InformationAction Ignore`, which effectively suppresses `Write-Host` output.</span></span> <span data-ttu-id="1d12d-117">(Voir « Example 5 »)</span><span class="sxs-lookup"><span data-stu-id="1d12d-117">(see "Example 5")</span></span>

## <span data-ttu-id="1d12d-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1d12d-118">EXAMPLES</span></span>

### <span data-ttu-id="1d12d-119">Exemple 1 : écrire dans la console sans ajouter de nouvelle ligne</span><span class="sxs-lookup"><span data-stu-id="1d12d-119">Example 1: Write to the console without adding a new line</span></span>

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

<span data-ttu-id="1d12d-120">Cette commande affiche la chaîne « no NewLine test » avec le `NoNewline` paramètre.</span><span class="sxs-lookup"><span data-stu-id="1d12d-120">This command displays the string 'no newline test' with the `NoNewline` parameter.</span></span>

<span data-ttu-id="1d12d-121">Une deuxième chaîne est écrite, mais elle finit sur la même ligne que la première en raison de l’absence de saut de ligne qui sépare les chaînes.</span><span class="sxs-lookup"><span data-stu-id="1d12d-121">A second string is written, but it ends up on the same line as the first due to the absence of a newline separating the strings.</span></span>

### <span data-ttu-id="1d12d-122">Exemple 2 : écrire dans la console et inclure un séparateur</span><span class="sxs-lookup"><span data-stu-id="1d12d-122">Example 2: Write to the console and include a separator</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

Cette commande affiche les nombres pairs de 2 à 12. <span data-ttu-id="1d12d-124">Le paramètre **separator** est utilisé pour ajouter la chaîne `, +2= ` (virgule, espace, `+` , `2` , `=` , espace).</span><span class="sxs-lookup"><span data-stu-id="1d12d-124">The **Separator** parameter is used to add the string `, +2= ` (comma, space, `+`, `2`, `=`, space).</span></span>

### <span data-ttu-id="1d12d-125">Exemple 3 : écrire avec des couleurs de texte et d’arrière-plan différentes</span><span class="sxs-lookup"><span data-stu-id="1d12d-125">Example 3: Write with different text and background colors</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

<span data-ttu-id="1d12d-126">Cette commande affiche les nombres pairs de 2 à 12.</span><span class="sxs-lookup"><span data-stu-id="1d12d-126">This command displays the even numbers from two through twelve.</span></span> <span data-ttu-id="1d12d-127">Elle utilise le `ForegroundColor` paramètre pour générer un texte vert foncé et le `BackgroundColor` paramètre pour afficher un arrière-plan blanc.</span><span class="sxs-lookup"><span data-stu-id="1d12d-127">It uses the `ForegroundColor` parameter to output dark green text and the `BackgroundColor` parameter to display a white background.</span></span>

### <span data-ttu-id="1d12d-128">Exemple 4 : écrire avec des couleurs de texte et d’arrière-plan différentes</span><span class="sxs-lookup"><span data-stu-id="1d12d-128">Example 4: Write with different text and background colors</span></span>

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

<span data-ttu-id="1d12d-129">Cette commande affiche la chaîne "Red on white text."</span><span class="sxs-lookup"><span data-stu-id="1d12d-129">This command displays the string "Red on white text."</span></span> <span data-ttu-id="1d12d-130">Le texte est rouge, comme défini par le `ForegroundColor` paramètre.</span><span class="sxs-lookup"><span data-stu-id="1d12d-130">The text is red, as defined by the `ForegroundColor` parameter.</span></span> <span data-ttu-id="1d12d-131">L’arrière-plan est blanc, comme défini par le `BackgroundColor` paramètre.</span><span class="sxs-lookup"><span data-stu-id="1d12d-131">The background is white, as defined by the `BackgroundColor` parameter.</span></span>

### <span data-ttu-id="1d12d-132">Exemple 5 : supprimer la sortie de Write-Host</span><span class="sxs-lookup"><span data-stu-id="1d12d-132">Example 5: Suppress output from Write-Host</span></span>

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

<span data-ttu-id="1d12d-133">Ces commandes suppriment efficacement la sortie de l’applet de commande `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="1d12d-133">These commands effectively suppress output of the `Write-Host` cmdlet.</span></span> <span data-ttu-id="1d12d-134">La première utilise le `InformationAction` paramètre avec la `Ignore` valeur pour supprimer la sortie du flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="1d12d-134">The first one uses the `InformationAction` parameter with the `Ignore` Value to suppress output to the information stream.</span></span>
<span data-ttu-id="1d12d-135">Le deuxième exemple redirige le flux d’informations de la commande vers la `$null` variable et le supprime par conséquent.</span><span class="sxs-lookup"><span data-stu-id="1d12d-135">The second example redirects the information stream of the command to the `$null` variable and thereby suppresses it.</span></span>

## <span data-ttu-id="1d12d-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1d12d-136">PARAMETERS</span></span>

### <span data-ttu-id="1d12d-137">-BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d12d-137">-BackgroundColor</span></span>

<span data-ttu-id="1d12d-138">Spécifie la couleur d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d12d-138">Specifies the background color.</span></span> <span data-ttu-id="1d12d-139">Il n'y a pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1d12d-139">There is no default.</span></span> <span data-ttu-id="1d12d-140">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="1d12d-140">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1d12d-141">Noir</span><span class="sxs-lookup"><span data-stu-id="1d12d-141">Black</span></span>
- <span data-ttu-id="1d12d-142">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="1d12d-142">DarkBlue</span></span>
- <span data-ttu-id="1d12d-143">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="1d12d-143">DarkGreen</span></span>
- <span data-ttu-id="1d12d-144">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="1d12d-144">DarkCyan</span></span>
- <span data-ttu-id="1d12d-145">DarkRed</span><span class="sxs-lookup"><span data-stu-id="1d12d-145">DarkRed</span></span>
- <span data-ttu-id="1d12d-146">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="1d12d-146">DarkMagenta</span></span>
- <span data-ttu-id="1d12d-147">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="1d12d-147">DarkYellow</span></span>
- <span data-ttu-id="1d12d-148">Gris</span><span class="sxs-lookup"><span data-stu-id="1d12d-148">Gray</span></span>
- <span data-ttu-id="1d12d-149">DarkGray</span><span class="sxs-lookup"><span data-stu-id="1d12d-149">DarkGray</span></span>
- <span data-ttu-id="1d12d-150">Blue</span><span class="sxs-lookup"><span data-stu-id="1d12d-150">Blue</span></span>
- <span data-ttu-id="1d12d-151">Vert</span><span class="sxs-lookup"><span data-stu-id="1d12d-151">Green</span></span>
- <span data-ttu-id="1d12d-152">Cyan</span><span class="sxs-lookup"><span data-stu-id="1d12d-152">Cyan</span></span>
- <span data-ttu-id="1d12d-153">Rouge</span><span class="sxs-lookup"><span data-stu-id="1d12d-153">Red</span></span>
- <span data-ttu-id="1d12d-154">Magenta</span><span class="sxs-lookup"><span data-stu-id="1d12d-154">Magenta</span></span>
- <span data-ttu-id="1d12d-155">Yellow</span><span class="sxs-lookup"><span data-stu-id="1d12d-155">Yellow</span></span>
- <span data-ttu-id="1d12d-156">White</span><span class="sxs-lookup"><span data-stu-id="1d12d-156">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d12d-157">-ForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1d12d-157">-ForegroundColor</span></span>

<span data-ttu-id="1d12d-158">Spécifie la couleur du texte.</span><span class="sxs-lookup"><span data-stu-id="1d12d-158">Specifies the text color.</span></span> <span data-ttu-id="1d12d-159">Il n'y a pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1d12d-159">There is no default.</span></span> <span data-ttu-id="1d12d-160">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="1d12d-160">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1d12d-161">Noir</span><span class="sxs-lookup"><span data-stu-id="1d12d-161">Black</span></span>
- <span data-ttu-id="1d12d-162">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="1d12d-162">DarkBlue</span></span>
- <span data-ttu-id="1d12d-163">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="1d12d-163">DarkGreen</span></span>
- <span data-ttu-id="1d12d-164">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="1d12d-164">DarkCyan</span></span>
- <span data-ttu-id="1d12d-165">DarkRed</span><span class="sxs-lookup"><span data-stu-id="1d12d-165">DarkRed</span></span>
- <span data-ttu-id="1d12d-166">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="1d12d-166">DarkMagenta</span></span>
- <span data-ttu-id="1d12d-167">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="1d12d-167">DarkYellow</span></span>
- <span data-ttu-id="1d12d-168">Gris</span><span class="sxs-lookup"><span data-stu-id="1d12d-168">Gray</span></span>
- <span data-ttu-id="1d12d-169">DarkGray</span><span class="sxs-lookup"><span data-stu-id="1d12d-169">DarkGray</span></span>
- <span data-ttu-id="1d12d-170">Blue</span><span class="sxs-lookup"><span data-stu-id="1d12d-170">Blue</span></span>
- <span data-ttu-id="1d12d-171">Vert</span><span class="sxs-lookup"><span data-stu-id="1d12d-171">Green</span></span>
- <span data-ttu-id="1d12d-172">Cyan</span><span class="sxs-lookup"><span data-stu-id="1d12d-172">Cyan</span></span>
- <span data-ttu-id="1d12d-173">Rouge</span><span class="sxs-lookup"><span data-stu-id="1d12d-173">Red</span></span>
- <span data-ttu-id="1d12d-174">Magenta</span><span class="sxs-lookup"><span data-stu-id="1d12d-174">Magenta</span></span>
- <span data-ttu-id="1d12d-175">Yellow</span><span class="sxs-lookup"><span data-stu-id="1d12d-175">Yellow</span></span>
- <span data-ttu-id="1d12d-176">White</span><span class="sxs-lookup"><span data-stu-id="1d12d-176">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d12d-177">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="1d12d-177">-NoNewline</span></span>

<span data-ttu-id="1d12d-178">Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie.</span><span class="sxs-lookup"><span data-stu-id="1d12d-178">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="1d12d-179">Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="1d12d-179">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="1d12d-180">Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="1d12d-180">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="1d12d-181">-Object</span><span class="sxs-lookup"><span data-stu-id="1d12d-181">-Object</span></span>

<span data-ttu-id="1d12d-182">Objets à afficher dans l’hôte.</span><span class="sxs-lookup"><span data-stu-id="1d12d-182">Objects to display in the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1d12d-183">-Séparateur</span><span class="sxs-lookup"><span data-stu-id="1d12d-183">-Separator</span></span>

<span data-ttu-id="1d12d-184">Spécifie une chaîne de séparation à insérer entre les objets affichés par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="1d12d-184">Specifies a separator string to insert between objects displayed by the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d12d-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1d12d-185">CommonParameters</span></span>
<span data-ttu-id="1d12d-186">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1d12d-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1d12d-187">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1d12d-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1d12d-188">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1d12d-188">INPUTS</span></span>

### <span data-ttu-id="1d12d-189">System.Object</span><span class="sxs-lookup"><span data-stu-id="1d12d-189">System.Object</span></span>

<span data-ttu-id="1d12d-190">Vous pouvez diriger les objets à écrire vers l'hôte.</span><span class="sxs-lookup"><span data-stu-id="1d12d-190">You can pipe objects to be written to the host.</span></span>

## <span data-ttu-id="1d12d-191">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1d12d-191">OUTPUTS</span></span>

### <span data-ttu-id="1d12d-192">None</span><span class="sxs-lookup"><span data-stu-id="1d12d-192">None</span></span>

<span data-ttu-id="1d12d-193">`Write-Host` envoie les objets à l’hôte.</span><span class="sxs-lookup"><span data-stu-id="1d12d-193">`Write-Host` sends the objects to the host.</span></span> <span data-ttu-id="1d12d-194">Aucun objet n'est retourné.</span><span class="sxs-lookup"><span data-stu-id="1d12d-194">It does not return any objects.</span></span> <span data-ttu-id="1d12d-195">Toutefois, l’hôte affiche les objets qui `Write-Host` lui sont envoyés.</span><span class="sxs-lookup"><span data-stu-id="1d12d-195">However, the host displays the objects that `Write-Host` sends to it.</span></span>

## <span data-ttu-id="1d12d-196">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1d12d-196">NOTES</span></span>

- <span data-ttu-id="1d12d-197">Lors de l’écriture d’une collection sur l’hôte, les éléments de la collection sont imprimés sur la même ligne, séparés par un espace.</span><span class="sxs-lookup"><span data-stu-id="1d12d-197">When writing a collection to the host, elements of the collection are printed on the same line separated by a single space.</span></span> <span data-ttu-id="1d12d-198">Vous pouvez le remplacer par le paramètre **separator** .</span><span class="sxs-lookup"><span data-stu-id="1d12d-198">This can be overridden with the **Separator** parameter.</span></span>

- <span data-ttu-id="1d12d-199">Les types de données non primitifs, tels que les objets avec des propriétés, peuvent entraîner des résultats inattendus et ne pas fournir une sortie significative.</span><span class="sxs-lookup"><span data-stu-id="1d12d-199">Non-primitive data types such as objects with properties can cause unexpected results and not provide meaningful output.</span></span> <span data-ttu-id="1d12d-200">Par exemple, `Write-Host @{a = 1; b = 2}` s’imprimera `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` sur l’hôte.</span><span class="sxs-lookup"><span data-stu-id="1d12d-200">For example, `Write-Host @{a = 1; b = 2}` will print `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` to the host.</span></span>

## <span data-ttu-id="1d12d-201">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1d12d-201">RELATED LINKS</span></span>

[<span data-ttu-id="1d12d-202">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="1d12d-202">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="1d12d-203">Out-Host</span><span class="sxs-lookup"><span data-stu-id="1d12d-203">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="1d12d-204">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="1d12d-204">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="1d12d-205">Write-Error</span><span class="sxs-lookup"><span data-stu-id="1d12d-205">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="1d12d-206">Write-Output</span><span class="sxs-lookup"><span data-stu-id="1d12d-206">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="1d12d-207">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="1d12d-207">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="1d12d-208">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="1d12d-208">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="1d12d-209">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="1d12d-209">Write-Warning</span></span>](Write-Warning.md)
