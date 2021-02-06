---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 59e5b728604ce37f27b56ebe62e1a22d6af8a966
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "99597339"
---
# <span data-ttu-id="8d39a-102">Out-String</span><span class="sxs-lookup"><span data-stu-id="8d39a-102">Out-String</span></span>

## <span data-ttu-id="8d39a-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8d39a-103">Synopsis</span></span>
<span data-ttu-id="8d39a-104">Génère des objets d’entrée sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="8d39a-104">Outputs input objects as a strings.</span></span>

## <span data-ttu-id="8d39a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d39a-105">Syntax</span></span>

### <span data-ttu-id="8d39a-106">NoNewLineFormatting (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8d39a-106">NoNewLineFormatting (Default)</span></span>

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### <span data-ttu-id="8d39a-107">StreamFormatting</span><span class="sxs-lookup"><span data-stu-id="8d39a-107">StreamFormatting</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="8d39a-108">Description</span><span class="sxs-lookup"><span data-stu-id="8d39a-108">Description</span></span>

<span data-ttu-id="8d39a-109">L' `Out-String` applet de commande convertit les objets d’entrée en chaînes.</span><span class="sxs-lookup"><span data-stu-id="8d39a-109">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="8d39a-110">Par défaut, `Out-String` accumule les chaînes et les retourne sous la forme d’une chaîne unique, mais vous pouvez utiliser le paramètre **Stream** pour demander `Out-String` à de retourner une ligne à la fois ou créer et tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="8d39a-110">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create and array of strings.</span></span> <span data-ttu-id="8d39a-111">Cette applet de commande vous permet de rechercher et de manipuler la sortie de chaîne comme vous le feriez dans des interpréteurs de commandes traditionnels quand la manipulation des objets est moins pratique.</span><span class="sxs-lookup"><span data-stu-id="8d39a-111">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="8d39a-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="8d39a-112">Examples</span></span>

### <span data-ttu-id="8d39a-113">Exemple 1 : récupérer la culture actuelle et convertir les données en chaînes</span><span class="sxs-lookup"><span data-stu-id="8d39a-113">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="8d39a-114">Cet exemple obtient les paramètres régionaux de l’utilisateur actuel et convertit les données de l’objet en chaînes.</span><span class="sxs-lookup"><span data-stu-id="8d39a-114">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

<span data-ttu-id="8d39a-115">La `$C` variable stocke un **Selected.SysTEM. Objet Globalization. CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="8d39a-115">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="8d39a-116">L’objet est le résultat de l' `Get-Culture` envoi de la sortie vers le pipeline vers `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8d39a-116">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="8d39a-117">Le paramètre **Property** utilise un `*` caractère générique astérisque () pour spécifier que toutes les propriétés sont contenues dans l’objet.</span><span class="sxs-lookup"><span data-stu-id="8d39a-117">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="8d39a-118">`Out-String` utilise le paramètre **InputObject** pour spécifier l’objet **CultureInfo** stocké dans la `$C` variable.</span><span class="sxs-lookup"><span data-stu-id="8d39a-118">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="8d39a-119">Les objets dans `$C` sont convertis en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="8d39a-119">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="8d39a-120">Pour afficher le `Out-String` tableau, stockez la sortie dans une variable et utilisez un index de tableau pour afficher les éléments.</span><span class="sxs-lookup"><span data-stu-id="8d39a-120">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="8d39a-121">Pour plus d’informations sur l’index de tableau, consultez [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8d39a-121">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="8d39a-122">Exemple 2 : utilisation d’objets</span><span class="sxs-lookup"><span data-stu-id="8d39a-122">Example 2: Working with objects</span></span>

<span data-ttu-id="8d39a-123">Cet exemple illustre la différence entre l'utilisation d'objets et l'utilisation de chaînes.</span><span class="sxs-lookup"><span data-stu-id="8d39a-123">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="8d39a-124">La commande affiche un alias qui comprend le texte **GCM**, l’alias de `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="8d39a-124">The command displays an alias that includes the text **gcm**, the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="8d39a-125">`Get-Alias` Obtient les objets **System. Management. Automation. AliasInfo** , un pour chaque alias et envoie les objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8d39a-125">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="8d39a-126">`Out-String` utilise le paramètre **Stream** pour convertir chaque objet en chaîne au lieu de concaténer tous les objets en une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="8d39a-126">`Out-String` uses the **Stream** parameter to convert each object to a string rather concatenating all the objects into a single string.</span></span> <span data-ttu-id="8d39a-127">Les objets **System. String** sont envoyés dans le pipeline et `Select-String` utilisent le paramètre **pattern** pour rechercher des correspondances pour le **GCM** de texte.</span><span class="sxs-lookup"><span data-stu-id="8d39a-127">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm**.</span></span>

> [!NOTE]
> <span data-ttu-id="8d39a-128">Si vous omettez le paramètre **Stream** , la commande affiche tous les alias car `Select-String` recherche le type de texte **GCM** dans la chaîne unique qui `Out-String` retourne.</span><span class="sxs-lookup"><span data-stu-id="8d39a-128">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="8d39a-129">Exemple 3 : utilisez le paramètre Width pour empêcher la troncation.</span><span class="sxs-lookup"><span data-stu-id="8d39a-129">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="8d39a-130">Tandis que la sortie de `Out-String` est renvoyée à la ligne suivante, il existe des scénarios dans lesquels la sortie est tronquée par le système de mise en forme avant d’être passée à `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="8d39a-130">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="8d39a-131">Vous pouvez éviter la troncation à l’aide du paramètre **Width** .</span><span class="sxs-lookup"><span data-stu-id="8d39a-131">You can avoid truncation using the **Width** parameter.</span></span>

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## <span data-ttu-id="8d39a-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8d39a-132">PARAMETERS</span></span>

### <span data-ttu-id="8d39a-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8d39a-133">-InputObject</span></span>

<span data-ttu-id="8d39a-134">Spécifie les objets à écrire dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="8d39a-134">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="8d39a-135">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="8d39a-135">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8d39a-136">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="8d39a-136">-NoNewline</span></span>

<span data-ttu-id="8d39a-137">Supprime toutes les nouvelles lignes de la sortie générée par le formateur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d39a-137">Removes all newlines from output generated by the PowerShell formatter.</span></span> <span data-ttu-id="8d39a-138">Les nouvelles lignes qui font partie des objets String sont conservées.</span><span class="sxs-lookup"><span data-stu-id="8d39a-138">Newlines that are part of the string objects are preserved.</span></span>

<span data-ttu-id="8d39a-139">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="8d39a-139">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d39a-140">-Stream</span><span class="sxs-lookup"><span data-stu-id="8d39a-140">-Stream</span></span>

<span data-ttu-id="8d39a-141">Par défaut, `Out-String` génère une chaîne unique mise en forme comme vous le verrez dans la console, y compris les en-têtes vides ou les nouvelles lignes de fin.</span><span class="sxs-lookup"><span data-stu-id="8d39a-141">By default, `Out-String` outputs a single string formatted as you would see it in the console including any blank headers or trailing newlines.</span></span> <span data-ttu-id="8d39a-142">Le paramètre **Stream** permet `Out-String` à de sortir chaque ligne un par un.</span><span class="sxs-lookup"><span data-stu-id="8d39a-142">The **Stream** parameter enables `Out-String` to output each line one by one.</span></span> <span data-ttu-id="8d39a-143">La seule exception à cela est que les chaînes multilignes.</span><span class="sxs-lookup"><span data-stu-id="8d39a-143">The only exception to this are multiline strings.</span></span> <span data-ttu-id="8d39a-144">Dans ce cas, `Out-String` continue à générer la chaîne sous la forme d’une chaîne unique, multiligne.</span><span class="sxs-lookup"><span data-stu-id="8d39a-144">In that case, `Out-String` will still output the string as a single, multiline string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d39a-145">-Largeur</span><span class="sxs-lookup"><span data-stu-id="8d39a-145">-Width</span></span>

<span data-ttu-id="8d39a-146">Spécifie le nombre de caractères dans chaque ligne de la sortie.</span><span class="sxs-lookup"><span data-stu-id="8d39a-146">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="8d39a-147">Tous les caractères supplémentaires sont renvoyés à la ligne suivante ou tronqués en fonction de l’applet de commande Formatter utilisée.</span><span class="sxs-lookup"><span data-stu-id="8d39a-147">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="8d39a-148">Le paramètre **Width** s’applique uniquement aux objets en cours de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="8d39a-148">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="8d39a-149">Si vous omettez ce paramètre, la largeur est déterminée par les caractéristiques du programme hôte.</span><span class="sxs-lookup"><span data-stu-id="8d39a-149">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="8d39a-150">Dans les fenêtres terminal (console), la largeur de fenêtre active est utilisée comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8d39a-150">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="8d39a-151">Les fenêtres de la console PowerShell ont par défaut une largeur de 80 caractères lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="8d39a-151">PowerShell console windows default to a width of 80 characters on installation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d39a-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8d39a-152">CommonParameters</span></span>

<span data-ttu-id="8d39a-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8d39a-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8d39a-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8d39a-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8d39a-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8d39a-155">INPUTS</span></span>

### <span data-ttu-id="8d39a-156">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8d39a-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8d39a-157">Vous pouvez envoyer des objets vers le dessous du pipeline `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="8d39a-157">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="8d39a-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8d39a-158">OUTPUTS</span></span>

### <span data-ttu-id="8d39a-159">System.String</span><span class="sxs-lookup"><span data-stu-id="8d39a-159">System.String</span></span>

<span data-ttu-id="8d39a-160">`Out-String` retourne la chaîne qu’il crée à partir de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8d39a-160">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="8d39a-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8d39a-161">NOTES</span></span>

<span data-ttu-id="8d39a-162">Les applets de commande qui contiennent le `Out` verbe ne mettent pas en forme les objets.</span><span class="sxs-lookup"><span data-stu-id="8d39a-162">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="8d39a-163">Les `Out` applets de commande envoient des objets au formateur pour la destination d’affichage spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8d39a-163">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="8d39a-164">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8d39a-164">RELATED LINKS</span></span>

[<span data-ttu-id="8d39a-165">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="8d39a-165">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="8d39a-166">Out-Default</span><span class="sxs-lookup"><span data-stu-id="8d39a-166">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="8d39a-167">Out-File</span><span class="sxs-lookup"><span data-stu-id="8d39a-167">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="8d39a-168">Out-Host</span><span class="sxs-lookup"><span data-stu-id="8d39a-168">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="8d39a-169">Out-Null</span><span class="sxs-lookup"><span data-stu-id="8d39a-169">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="8d39a-170">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="8d39a-170">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="8d39a-171">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="8d39a-171">Out-Printer</span></span>](Out-Printer.md)
