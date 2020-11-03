---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: 7991d28e1136eb7f578cdd559f96d4c795c147a0
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "93206257"
---
# <span data-ttu-id="c3834-103">Write-Host</span><span class="sxs-lookup"><span data-stu-id="c3834-103">Write-Host</span></span>

## <span data-ttu-id="c3834-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c3834-104">SYNOPSIS</span></span>

<span data-ttu-id="c3834-105">Écrit la sortie personnalisée sur un hôte.</span><span class="sxs-lookup"><span data-stu-id="c3834-105">Writes customized output to a host.</span></span>

## <span data-ttu-id="c3834-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3834-106">SYNTAX</span></span>

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## <span data-ttu-id="c3834-107">Description</span><span class="sxs-lookup"><span data-stu-id="c3834-107">DESCRIPTION</span></span>

<span data-ttu-id="c3834-108">L' `Write-Host` objectif principal de l’applet de commande est de produire pour la sortie-(hôte)-affichage uniquement, par exemple l’impression d’un texte coloré comme lorsque vous invitez l’utilisateur à entrer des données conjointement avec l' [hôte de lecture](Read-Host.md).</span><span class="sxs-lookup"><span data-stu-id="c3834-108">The `Write-Host` cmdlet's primary purpose is to produce for-(host)-display-only output, such as printing colored text like when prompting the user for input in conjunction with [Read-Host](Read-Host.md).</span></span>
<span data-ttu-id="c3834-109">`Write-Host` utilise la méthode [ToString ()](/dotnet/api/system.object.tostring) pour écrire la sortie.</span><span class="sxs-lookup"><span data-stu-id="c3834-109">`Write-Host` uses the [ToString()](/dotnet/api/system.object.tostring) method to write the output.</span></span> <span data-ttu-id="c3834-110">En revanche, pour sortir des données dans le pipeline, utilisez la sortie [Write-Output](Write-Output.md) ou implicite.</span><span class="sxs-lookup"><span data-stu-id="c3834-110">By contrast, to output data to the pipeline, use [Write-Output](Write-Output.md) or implicit output.</span></span>

<span data-ttu-id="c3834-111">Vous pouvez spécifier la couleur du texte à l’aide du `ForegroundColor` paramètre, et vous pouvez spécifier la couleur d’arrière-plan à l’aide du `BackgroundColor` paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3834-111">You can specify the color of text by using the `ForegroundColor` parameter, and you can specify the background color by using the `BackgroundColor` parameter.</span></span> <span data-ttu-id="c3834-112">Le paramètre Separator vous permet de spécifier une chaîne à utiliser pour séparer les objets affichés.</span><span class="sxs-lookup"><span data-stu-id="c3834-112">The Separator parameter lets you specify a string to use to separate displayed objects.</span></span> <span data-ttu-id="c3834-113">Le résultat donné dépend du programme qui héberge PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3834-113">The particular result depends on the program that is hosting PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="c3834-114">À compter de Windows PowerShell 5,0, `Write-Host` est un wrapper de `Write-Information` ce qui vous permet d’utiliser `Write-Host` pour émettre une sortie vers le flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="c3834-114">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="c3834-115">Cela permet la **capture** ou la **suppression** des données écrites à l’aide de `Write-Host` tout en préservant la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="c3834-115">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span>
>
> <span data-ttu-id="c3834-116">La `$InformationPreference` variable de préférence et le `InformationAction` paramètre commun n’affectent pas les `Write-Host` messages.</span><span class="sxs-lookup"><span data-stu-id="c3834-116">The `$InformationPreference` preference variable and `InformationAction` common parameter do not affect `Write-Host` messages.</span></span> <span data-ttu-id="c3834-117">L’exception à cette règle est `-InformationAction Ignore` , qui supprime effectivement la `Write-Host` sortie.</span><span class="sxs-lookup"><span data-stu-id="c3834-117">The exception to this rule is `-InformationAction Ignore`, which effectively suppresses `Write-Host` output.</span></span> <span data-ttu-id="c3834-118">(Voir « Example 5 »)</span><span class="sxs-lookup"><span data-stu-id="c3834-118">(see "Example 5")</span></span>

## <span data-ttu-id="c3834-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c3834-119">EXAMPLES</span></span>

### <span data-ttu-id="c3834-120">Exemple 1 : écrire dans la console sans ajouter de nouvelle ligne</span><span class="sxs-lookup"><span data-stu-id="c3834-120">Example 1: Write to the console without adding a new line</span></span>

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

<span data-ttu-id="c3834-121">Cette commande affiche la chaîne « no NewLine test » avec le `NoNewline` paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3834-121">This command displays the string 'no newline test' with the `NoNewline` parameter.</span></span>

<span data-ttu-id="c3834-122">Une deuxième chaîne est écrite, mais elle finit sur la même ligne que la première en raison de l’absence de saut de ligne qui sépare les chaînes.</span><span class="sxs-lookup"><span data-stu-id="c3834-122">A second string is written, but it ends up on the same line as the first due to the absence of a newline separating the strings.</span></span>

### <span data-ttu-id="c3834-123">Exemple 2 : écrire dans la console et inclure un séparateur</span><span class="sxs-lookup"><span data-stu-id="c3834-123">Example 2: Write to the console and include a separator</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

Cette commande affiche les nombres pairs de 2 à 12. <span data-ttu-id="c3834-125">Le paramètre **separator** est utilisé pour ajouter la chaîne `, +2= ` (virgule, espace, `+` , `2` , `=` , espace).</span><span class="sxs-lookup"><span data-stu-id="c3834-125">The **Separator** parameter is used to add the string `, +2= ` (comma, space, `+`, `2`, `=`, space).</span></span>

### <span data-ttu-id="c3834-126">Exemple 3 : écrire avec des couleurs de texte et d’arrière-plan différentes</span><span class="sxs-lookup"><span data-stu-id="c3834-126">Example 3: Write with different text and background colors</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

<span data-ttu-id="c3834-127">Cette commande affiche les nombres pairs de 2 à 12.</span><span class="sxs-lookup"><span data-stu-id="c3834-127">This command displays the even numbers from two through twelve.</span></span> <span data-ttu-id="c3834-128">Elle utilise le `ForegroundColor` paramètre pour générer un texte vert foncé et le `BackgroundColor` paramètre pour afficher un arrière-plan blanc.</span><span class="sxs-lookup"><span data-stu-id="c3834-128">It uses the `ForegroundColor` parameter to output dark green text and the `BackgroundColor` parameter to display a white background.</span></span>

### <span data-ttu-id="c3834-129">Exemple 4 : écrire avec des couleurs de texte et d’arrière-plan différentes</span><span class="sxs-lookup"><span data-stu-id="c3834-129">Example 4: Write with different text and background colors</span></span>

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

<span data-ttu-id="c3834-130">Cette commande affiche la chaîne "Red on white text."</span><span class="sxs-lookup"><span data-stu-id="c3834-130">This command displays the string "Red on white text."</span></span> <span data-ttu-id="c3834-131">Le texte est rouge, comme défini par le `ForegroundColor` paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3834-131">The text is red, as defined by the `ForegroundColor` parameter.</span></span> <span data-ttu-id="c3834-132">L’arrière-plan est blanc, comme défini par le `BackgroundColor` paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3834-132">The background is white, as defined by the `BackgroundColor` parameter.</span></span>

### <span data-ttu-id="c3834-133">Exemple 5 : supprimer la sortie de Write-Host</span><span class="sxs-lookup"><span data-stu-id="c3834-133">Example 5: Suppress output from Write-Host</span></span>

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

<span data-ttu-id="c3834-134">Ces commandes suppriment efficacement la sortie de l’applet de commande `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="c3834-134">These commands effectively suppress output of the `Write-Host` cmdlet.</span></span> <span data-ttu-id="c3834-135">La première utilise le `InformationAction` paramètre avec la `Ignore` valeur pour supprimer la sortie du flux d’informations.</span><span class="sxs-lookup"><span data-stu-id="c3834-135">The first one uses the `InformationAction` parameter with the `Ignore` Value to suppress output to the information stream.</span></span>
<span data-ttu-id="c3834-136">Le deuxième exemple redirige le flux d’informations de la commande vers la `$null` variable et le supprime par conséquent.</span><span class="sxs-lookup"><span data-stu-id="c3834-136">The second example redirects the information stream of the command to the `$null` variable and thereby suppresses it.</span></span>

## <span data-ttu-id="c3834-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3834-137">PARAMETERS</span></span>

### <span data-ttu-id="c3834-138">-BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c3834-138">-BackgroundColor</span></span>

<span data-ttu-id="c3834-139">Spécifie la couleur d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c3834-139">Specifies the background color.</span></span> <span data-ttu-id="c3834-140">Il n'y a pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3834-140">There is no default.</span></span> <span data-ttu-id="c3834-141">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c3834-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c3834-142">Noir</span><span class="sxs-lookup"><span data-stu-id="c3834-142">Black</span></span>
- <span data-ttu-id="c3834-143">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="c3834-143">DarkBlue</span></span>
- <span data-ttu-id="c3834-144">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="c3834-144">DarkGreen</span></span>
- <span data-ttu-id="c3834-145">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="c3834-145">DarkCyan</span></span>
- <span data-ttu-id="c3834-146">DarkRed</span><span class="sxs-lookup"><span data-stu-id="c3834-146">DarkRed</span></span>
- <span data-ttu-id="c3834-147">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="c3834-147">DarkMagenta</span></span>
- <span data-ttu-id="c3834-148">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="c3834-148">DarkYellow</span></span>
- <span data-ttu-id="c3834-149">Gris</span><span class="sxs-lookup"><span data-stu-id="c3834-149">Gray</span></span>
- <span data-ttu-id="c3834-150">DarkGray</span><span class="sxs-lookup"><span data-stu-id="c3834-150">DarkGray</span></span>
- <span data-ttu-id="c3834-151">Bleu</span><span class="sxs-lookup"><span data-stu-id="c3834-151">Blue</span></span>
- <span data-ttu-id="c3834-152">Vert</span><span class="sxs-lookup"><span data-stu-id="c3834-152">Green</span></span>
- <span data-ttu-id="c3834-153">Cyan</span><span class="sxs-lookup"><span data-stu-id="c3834-153">Cyan</span></span>
- <span data-ttu-id="c3834-154">Rouge</span><span class="sxs-lookup"><span data-stu-id="c3834-154">Red</span></span>
- <span data-ttu-id="c3834-155">Magenta</span><span class="sxs-lookup"><span data-stu-id="c3834-155">Magenta</span></span>
- <span data-ttu-id="c3834-156">Jaune</span><span class="sxs-lookup"><span data-stu-id="c3834-156">Yellow</span></span>
- <span data-ttu-id="c3834-157">White</span><span class="sxs-lookup"><span data-stu-id="c3834-157">White</span></span>

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

### <span data-ttu-id="c3834-158">-ForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c3834-158">-ForegroundColor</span></span>

<span data-ttu-id="c3834-159">Spécifie la couleur du texte.</span><span class="sxs-lookup"><span data-stu-id="c3834-159">Specifies the text color.</span></span> <span data-ttu-id="c3834-160">Il n'y a pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3834-160">There is no default.</span></span> <span data-ttu-id="c3834-161">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c3834-161">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c3834-162">Noir</span><span class="sxs-lookup"><span data-stu-id="c3834-162">Black</span></span>
- <span data-ttu-id="c3834-163">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="c3834-163">DarkBlue</span></span>
- <span data-ttu-id="c3834-164">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="c3834-164">DarkGreen</span></span>
- <span data-ttu-id="c3834-165">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="c3834-165">DarkCyan</span></span>
- <span data-ttu-id="c3834-166">DarkRed</span><span class="sxs-lookup"><span data-stu-id="c3834-166">DarkRed</span></span>
- <span data-ttu-id="c3834-167">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="c3834-167">DarkMagenta</span></span>
- <span data-ttu-id="c3834-168">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="c3834-168">DarkYellow</span></span>
- <span data-ttu-id="c3834-169">Gris</span><span class="sxs-lookup"><span data-stu-id="c3834-169">Gray</span></span>
- <span data-ttu-id="c3834-170">DarkGray</span><span class="sxs-lookup"><span data-stu-id="c3834-170">DarkGray</span></span>
- <span data-ttu-id="c3834-171">Bleu</span><span class="sxs-lookup"><span data-stu-id="c3834-171">Blue</span></span>
- <span data-ttu-id="c3834-172">Vert</span><span class="sxs-lookup"><span data-stu-id="c3834-172">Green</span></span>
- <span data-ttu-id="c3834-173">Cyan</span><span class="sxs-lookup"><span data-stu-id="c3834-173">Cyan</span></span>
- <span data-ttu-id="c3834-174">Rouge</span><span class="sxs-lookup"><span data-stu-id="c3834-174">Red</span></span>
- <span data-ttu-id="c3834-175">Magenta</span><span class="sxs-lookup"><span data-stu-id="c3834-175">Magenta</span></span>
- <span data-ttu-id="c3834-176">Jaune</span><span class="sxs-lookup"><span data-stu-id="c3834-176">Yellow</span></span>
- <span data-ttu-id="c3834-177">White</span><span class="sxs-lookup"><span data-stu-id="c3834-177">White</span></span>

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

### <span data-ttu-id="c3834-178">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="c3834-178">-NoNewline</span></span>

<span data-ttu-id="c3834-179">Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie.</span><span class="sxs-lookup"><span data-stu-id="c3834-179">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="c3834-180">Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie.</span><span class="sxs-lookup"><span data-stu-id="c3834-180">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="c3834-181">Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="c3834-181">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="c3834-182">-Object</span><span class="sxs-lookup"><span data-stu-id="c3834-182">-Object</span></span>

<span data-ttu-id="c3834-183">Objets à afficher dans l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c3834-183">Objects to display in the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c3834-184">-Séparateur</span><span class="sxs-lookup"><span data-stu-id="c3834-184">-Separator</span></span>

<span data-ttu-id="c3834-185">Spécifie une chaîne de séparation à insérer entre les objets affichés par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c3834-185">Specifies a separator string to insert between objects displayed by the host.</span></span>

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

### <span data-ttu-id="c3834-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3834-186">CommonParameters</span></span>
<span data-ttu-id="c3834-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c3834-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3834-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c3834-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c3834-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c3834-189">INPUTS</span></span>

### <span data-ttu-id="c3834-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="c3834-190">System.Object</span></span>

<span data-ttu-id="c3834-191">Vous pouvez diriger les objets à écrire vers l'hôte.</span><span class="sxs-lookup"><span data-stu-id="c3834-191">You can pipe objects to be written to the host.</span></span>

## <span data-ttu-id="c3834-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c3834-192">OUTPUTS</span></span>

### <span data-ttu-id="c3834-193">Aucun</span><span class="sxs-lookup"><span data-stu-id="c3834-193">None</span></span>

<span data-ttu-id="c3834-194">`Write-Host` envoie les objets à l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c3834-194">`Write-Host` sends the objects to the host.</span></span> <span data-ttu-id="c3834-195">Aucun objet n'est retourné.</span><span class="sxs-lookup"><span data-stu-id="c3834-195">It does not return any objects.</span></span> <span data-ttu-id="c3834-196">Toutefois, l’hôte affiche les objets qui `Write-Host` lui sont envoyés.</span><span class="sxs-lookup"><span data-stu-id="c3834-196">However, the host displays the objects that `Write-Host` sends to it.</span></span>

## <span data-ttu-id="c3834-197">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c3834-197">NOTES</span></span>

- <span data-ttu-id="c3834-198">Lors de l’écriture d’une collection sur l’hôte, les éléments de la collection sont imprimés sur la même ligne, séparés par un espace.</span><span class="sxs-lookup"><span data-stu-id="c3834-198">When writing a collection to the host, elements of the collection are printed on the same line separated by a single space.</span></span> <span data-ttu-id="c3834-199">Vous pouvez le remplacer par le paramètre **separator** .</span><span class="sxs-lookup"><span data-stu-id="c3834-199">This can be overridden with the **Separator** parameter.</span></span>

- <span data-ttu-id="c3834-200">Les types de données non primitifs, tels que les objets avec des propriétés, peuvent entraîner des résultats inattendus et ne pas fournir une sortie significative.</span><span class="sxs-lookup"><span data-stu-id="c3834-200">Non-primitive data types such as objects with properties can cause unexpected results and not provide meaningful output.</span></span> <span data-ttu-id="c3834-201">Par exemple, `Write-Host @{a = 1; b = 2}` s’imprimera `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` sur l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c3834-201">For example, `Write-Host @{a = 1; b = 2}` will print `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` to the host.</span></span>

## <span data-ttu-id="c3834-202">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c3834-202">RELATED LINKS</span></span>

[<span data-ttu-id="c3834-203">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="c3834-203">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="c3834-204">Out-Host</span><span class="sxs-lookup"><span data-stu-id="c3834-204">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="c3834-205">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="c3834-205">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="c3834-206">Écriture-erreur</span><span class="sxs-lookup"><span data-stu-id="c3834-206">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="c3834-207">Write-Output</span><span class="sxs-lookup"><span data-stu-id="c3834-207">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="c3834-208">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="c3834-208">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="c3834-209">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="c3834-209">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="c3834-210">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="c3834-210">Write-Warning</span></span>](Write-Warning.md)
