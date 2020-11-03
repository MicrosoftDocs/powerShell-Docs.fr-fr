---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: 28914b86c86d5c16f09c81a5dc70ed1e05123b3e
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205913"
---
# <span data-ttu-id="c8e66-103">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="c8e66-103">Format-Custom</span></span>

## <span data-ttu-id="c8e66-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c8e66-104">SYNOPSIS</span></span>
<span data-ttu-id="c8e66-105">Utilise un affichage personnalisé pour mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="c8e66-105">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="c8e66-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c8e66-106">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="c8e66-107">Description</span><span class="sxs-lookup"><span data-stu-id="c8e66-107">DESCRIPTION</span></span>

<span data-ttu-id="c8e66-108">L' `Format-Custom` applet de commande met en forme la sortie d’une commande telle qu’elle est définie dans une autre vue.</span><span class="sxs-lookup"><span data-stu-id="c8e66-108">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="c8e66-109">`Format-Custom` est conçu pour afficher des vues qui ne sont pas simplement des tables ou des listes.</span><span class="sxs-lookup"><span data-stu-id="c8e66-109">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="c8e66-110">Vous pouvez utiliser les affichages définis dans PowerShell, ou vous pouvez créer vos propres vues dans un nouveau `format.ps1xml` fichier et utiliser l' `Update-FormatData` applet de commande pour les ajouter à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8e66-110">You can use the views defined in PowerShell, or you can create your own views in a new `format.ps1xml` file and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="c8e66-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c8e66-111">EXAMPLES</span></span>

### <span data-ttu-id="c8e66-112">Exemple 1 : mettre en forme la sortie avec une vue personnalisée</span><span class="sxs-lookup"><span data-stu-id="c8e66-112">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="c8e66-113">Cette commande met en forme les informations sur l' `Start-Transcript` applet de commande dans le format défini par la vue MyView, un affichage personnalisé créé par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c8e66-113">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="c8e66-114">Pour exécuter cette commande avec succès, vous devez d’abord créer un nouveau fichier PS1XML, définir la vue **MyView** , puis utiliser la `Update-FormatData` commande pour ajouter le fichier ps1xml à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8e66-114">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="c8e66-115">Exemple 2 : mettre en forme la sortie avec la vue par défaut</span><span class="sxs-lookup"><span data-stu-id="c8e66-115">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="c8e66-116">Cette commande met en forme des informations sur le processus **Winlogon** dans un autre affichage personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c8e66-116">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="c8e66-117">Étant donné que la commande n’utilise pas le paramètre **View** , `Format-Custom` utilise une vue personnalisée par défaut pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="c8e66-117">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="c8e66-118">Exemple 3 : dépannage des erreurs de format</span><span class="sxs-lookup"><span data-stu-id="c8e66-118">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="c8e66-119">Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.</span><span class="sxs-lookup"><span data-stu-id="c8e66-119">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="c8e66-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c8e66-120">PARAMETERS</span></span>

### <span data-ttu-id="c8e66-121">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="c8e66-121">-Depth</span></span>

<span data-ttu-id="c8e66-122">Spécifie le nombre de colonnes dans l'affichage.</span><span class="sxs-lookup"><span data-stu-id="c8e66-122">Specifies the number of columns in the display.</span></span>

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

### <span data-ttu-id="c8e66-123">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="c8e66-123">-DisplayError</span></span>

<span data-ttu-id="c8e66-124">Affiche les erreurs sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c8e66-124">Displays errors at the command line.</span></span> <span data-ttu-id="c8e66-125">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Custom` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="c8e66-125">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="c8e66-126">-Développer</span><span class="sxs-lookup"><span data-stu-id="c8e66-126">-Expand</span></span>

<span data-ttu-id="c8e66-127">Met en forme l'objet de collection, ainsi que les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="c8e66-127">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="c8e66-128">Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l’interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="c8e66-128">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="c8e66-129">La valeur par défaut est **EnumOnly** .</span><span class="sxs-lookup"><span data-stu-id="c8e66-129">The default value is **EnumOnly** .</span></span>

<span data-ttu-id="c8e66-130">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="c8e66-130">Valid values are:</span></span>

- <span data-ttu-id="c8e66-131">EnumOnly : affiche les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="c8e66-131">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="c8e66-132">CoreOnly : affiche les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="c8e66-132">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="c8e66-133">Both : affiche les propriétés de l’objet de collection et les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="c8e66-133">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8e66-134">-Force</span><span class="sxs-lookup"><span data-stu-id="c8e66-134">-Force</span></span>

<span data-ttu-id="c8e66-135">Indique à l'applet de commande d'afficher toutes les informations sur l'erreur.</span><span class="sxs-lookup"><span data-stu-id="c8e66-135">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="c8e66-136">Utilisez avec les paramètres **DisplayError** ou **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="c8e66-136">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="c8e66-137">Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.</span><span class="sxs-lookup"><span data-stu-id="c8e66-137">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="c8e66-138">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="c8e66-138">-GroupBy</span></span>

<span data-ttu-id="c8e66-139">Formate la sortie dans des groupes basés sur une valeur ou propriété partagée.</span><span class="sxs-lookup"><span data-stu-id="c8e66-139">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="c8e66-140">Entrez une expression ou une propriété de la sortie.</span><span class="sxs-lookup"><span data-stu-id="c8e66-140">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="c8e66-141">La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="c8e66-141">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="c8e66-142">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="c8e66-142">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="c8e66-143">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="c8e66-143">Valid key-value pairs are:</span></span>

- <span data-ttu-id="c8e66-144">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="c8e66-144">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="c8e66-145">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="c8e66-145">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="c8e66-146">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="c8e66-146">FormatString - `<string>`</span></span>

<span data-ttu-id="c8e66-147">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="c8e66-147">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="c8e66-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c8e66-148">-InputObject</span></span>

<span data-ttu-id="c8e66-149">Spécifie les objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="c8e66-149">Specifies the objects to be formatted.</span></span> <span data-ttu-id="c8e66-150">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="c8e66-150">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="c8e66-151">-Propriété</span><span class="sxs-lookup"><span data-stu-id="c8e66-151">-Property</span></span>

<span data-ttu-id="c8e66-152">Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="c8e66-152">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="c8e66-153">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c8e66-153">Wildcards are permitted.</span></span>

<span data-ttu-id="c8e66-154">Si vous omettez ce paramètre, les propriétés qui apparaissent dans l'affichage dépendent de l'objet affiché.</span><span class="sxs-lookup"><span data-stu-id="c8e66-154">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="c8e66-155">La **propriété** nom du paramètre est facultative.</span><span class="sxs-lookup"><span data-stu-id="c8e66-155">The parameter name **Property** is optional.</span></span> <span data-ttu-id="c8e66-156">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="c8e66-156">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="c8e66-157">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="c8e66-157">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="c8e66-158">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="c8e66-158">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="c8e66-159">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="c8e66-159">Valid key-value pairs are:</span></span>

- <span data-ttu-id="c8e66-160">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="c8e66-160">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="c8e66-161">Profondeur `<int32>`</span><span class="sxs-lookup"><span data-stu-id="c8e66-161">Depth - `<int32>`</span></span>

<span data-ttu-id="c8e66-162">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="c8e66-162">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c8e66-163">-ShowError</span><span class="sxs-lookup"><span data-stu-id="c8e66-163">-ShowError</span></span>

<span data-ttu-id="c8e66-164">Envoie les erreurs via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="c8e66-164">Sends errors through the pipeline.</span></span> <span data-ttu-id="c8e66-165">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Custom` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="c8e66-165">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="c8e66-166">-Afficher</span><span class="sxs-lookup"><span data-stu-id="c8e66-166">-View</span></span>

<span data-ttu-id="c8e66-167">Spécifie le nom d’un autre format ou d’une autre vue.</span><span class="sxs-lookup"><span data-stu-id="c8e66-167">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="c8e66-168">Si vous omettez ce paramètre, `Format-Custom` utilise une vue personnalisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c8e66-168">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="c8e66-169">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="c8e66-169">You cannot use the **Property** and **View** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8e66-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8e66-170">CommonParameters</span></span>

<span data-ttu-id="c8e66-171">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c8e66-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8e66-172">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c8e66-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c8e66-173">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c8e66-173">INPUTS</span></span>

### <span data-ttu-id="c8e66-174">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="c8e66-174">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c8e66-175">Vous pouvez diriger n’importe quel objet vers `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="c8e66-175">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="c8e66-176">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c8e66-176">OUTPUTS</span></span>

### <span data-ttu-id="c8e66-177">Microsoft. PowerShell. Commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="c8e66-177">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="c8e66-178">`Format-Custom` retourne les objets de format qui représentent l’affichage.</span><span class="sxs-lookup"><span data-stu-id="c8e66-178">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="c8e66-179">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c8e66-179">NOTES</span></span>

<span data-ttu-id="c8e66-180">`Format-Custom` est conçu pour afficher des vues qui ne sont pas simplement des tables ou des listes.</span><span class="sxs-lookup"><span data-stu-id="c8e66-180">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="c8e66-181">Pour afficher une autre vue de table, utilisez `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="c8e66-181">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="c8e66-182">Pour afficher un autre affichage de liste, utilisez `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="c8e66-182">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="c8e66-183">Vous pouvez également faire référence à `Format-Custom` par son alias intégré, `fc` .</span><span class="sxs-lookup"><span data-stu-id="c8e66-183">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="c8e66-184">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="c8e66-184">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="c8e66-185">Le paramètre **GroupBy** suppose que les objets sont triés.</span><span class="sxs-lookup"><span data-stu-id="c8e66-185">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="c8e66-186">Avant `Format-Custom` d’utiliser pour regrouper les objets, utilisez `Sort-Object` pour les trier.</span><span class="sxs-lookup"><span data-stu-id="c8e66-186">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="c8e66-187">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c8e66-187">RELATED LINKS</span></span>

[<span data-ttu-id="c8e66-188">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="c8e66-188">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="c8e66-189">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="c8e66-189">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="c8e66-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="c8e66-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="c8e66-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="c8e66-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="c8e66-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="c8e66-192">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="c8e66-193">Get-Process</span><span class="sxs-lookup"><span data-stu-id="c8e66-193">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
