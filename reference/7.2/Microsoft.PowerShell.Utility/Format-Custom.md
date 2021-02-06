---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: ff4b2dda3f12fa34fc518c6a180f3213ba873d90
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598556"
---
# <span data-ttu-id="a3a47-102">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="a3a47-102">Format-Custom</span></span>

## <span data-ttu-id="a3a47-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a3a47-103">SYNOPSIS</span></span>
<span data-ttu-id="a3a47-104">Utilise un affichage personnalisé pour mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="a3a47-104">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="a3a47-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a3a47-105">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="a3a47-106">Description</span><span class="sxs-lookup"><span data-stu-id="a3a47-106">DESCRIPTION</span></span>

<span data-ttu-id="a3a47-107">L' `Format-Custom` applet de commande met en forme la sortie d’une commande telle qu’elle est définie dans une autre vue.</span><span class="sxs-lookup"><span data-stu-id="a3a47-107">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="a3a47-108">`Format-Custom` est conçu pour afficher des vues qui ne sont pas simplement des tables ou des listes.</span><span class="sxs-lookup"><span data-stu-id="a3a47-108">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="a3a47-109">Vous pouvez utiliser les affichages définis dans PowerShell, ou vous pouvez créer vos propres vues dans un nouveau `format.ps1xml` fichier et utiliser l' `Update-FormatData` applet de commande pour les ajouter à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3a47-109">You can use the views defined in PowerShell, or you can create your own views in a new `format.ps1xml` file and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="a3a47-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a3a47-110">EXAMPLES</span></span>

### <span data-ttu-id="a3a47-111">Exemple 1 : mettre en forme la sortie avec une vue personnalisée</span><span class="sxs-lookup"><span data-stu-id="a3a47-111">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="a3a47-112">Cette commande met en forme les informations sur l' `Start-Transcript` applet de commande dans le format défini par la vue MyView, un affichage personnalisé créé par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a3a47-112">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="a3a47-113">Pour exécuter cette commande avec succès, vous devez d’abord créer un nouveau fichier PS1XML, définir la vue **MyView** , puis utiliser la `Update-FormatData` commande pour ajouter le fichier ps1xml à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3a47-113">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="a3a47-114">Exemple 2 : mettre en forme la sortie avec la vue par défaut</span><span class="sxs-lookup"><span data-stu-id="a3a47-114">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="a3a47-115">Cette commande met en forme des informations sur le processus **Winlogon** dans un autre affichage personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a3a47-115">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="a3a47-116">Étant donné que la commande n’utilise pas le paramètre **View** , `Format-Custom` utilise une vue personnalisée par défaut pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="a3a47-116">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="a3a47-117">Exemple 3 : dépannage des erreurs de format</span><span class="sxs-lookup"><span data-stu-id="a3a47-117">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="a3a47-118">Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.</span><span class="sxs-lookup"><span data-stu-id="a3a47-118">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

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

## <span data-ttu-id="a3a47-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a3a47-119">PARAMETERS</span></span>

### <span data-ttu-id="a3a47-120">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="a3a47-120">-Depth</span></span>

<span data-ttu-id="a3a47-121">Spécifie le nombre de colonnes dans l'affichage.</span><span class="sxs-lookup"><span data-stu-id="a3a47-121">Specifies the number of columns in the display.</span></span>

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

### <span data-ttu-id="a3a47-122">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="a3a47-122">-DisplayError</span></span>

<span data-ttu-id="a3a47-123">Affiche les erreurs sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a3a47-123">Displays errors at the command line.</span></span> <span data-ttu-id="a3a47-124">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Custom` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="a3a47-124">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="a3a47-125">-Développer</span><span class="sxs-lookup"><span data-stu-id="a3a47-125">-Expand</span></span>

<span data-ttu-id="a3a47-126">Met en forme l'objet de collection, ainsi que les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="a3a47-126">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="a3a47-127">Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l’interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="a3a47-127">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="a3a47-128">La valeur par défaut est **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="a3a47-128">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="a3a47-129">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="a3a47-129">Valid values are:</span></span>

- <span data-ttu-id="a3a47-130">EnumOnly : affiche les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="a3a47-130">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="a3a47-131">CoreOnly : affiche les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="a3a47-131">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="a3a47-132">Both : affiche les propriétés de l’objet de collection et les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="a3a47-132">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

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

### <span data-ttu-id="a3a47-133">-Force</span><span class="sxs-lookup"><span data-stu-id="a3a47-133">-Force</span></span>

<span data-ttu-id="a3a47-134">Indique à l'applet de commande d'afficher toutes les informations sur l'erreur.</span><span class="sxs-lookup"><span data-stu-id="a3a47-134">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="a3a47-135">Utilisez avec les paramètres **DisplayError** ou **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="a3a47-135">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="a3a47-136">Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.</span><span class="sxs-lookup"><span data-stu-id="a3a47-136">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="a3a47-137">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="a3a47-137">-GroupBy</span></span>

<span data-ttu-id="a3a47-138">Formate la sortie dans des groupes basés sur une valeur ou propriété partagée.</span><span class="sxs-lookup"><span data-stu-id="a3a47-138">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="a3a47-139">Entrez une expression ou une propriété de la sortie.</span><span class="sxs-lookup"><span data-stu-id="a3a47-139">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="a3a47-140">La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="a3a47-140">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="a3a47-141">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="a3a47-141">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="a3a47-142">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="a3a47-142">Valid key-value pairs are:</span></span>

- <span data-ttu-id="a3a47-143">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="a3a47-143">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="a3a47-144">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="a3a47-144">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="a3a47-145">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="a3a47-145">FormatString - `<string>`</span></span>

<span data-ttu-id="a3a47-146">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="a3a47-146">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="a3a47-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a3a47-147">-InputObject</span></span>

<span data-ttu-id="a3a47-148">Spécifie les objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="a3a47-148">Specifies the objects to be formatted.</span></span> <span data-ttu-id="a3a47-149">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="a3a47-149">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="a3a47-150">-Propriété</span><span class="sxs-lookup"><span data-stu-id="a3a47-150">-Property</span></span>

<span data-ttu-id="a3a47-151">Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="a3a47-151">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="a3a47-152">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a3a47-152">Wildcards are permitted.</span></span>

<span data-ttu-id="a3a47-153">Si vous omettez ce paramètre, les propriétés qui apparaissent dans l'affichage dépendent de l'objet affiché.</span><span class="sxs-lookup"><span data-stu-id="a3a47-153">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="a3a47-154">La **propriété** nom du paramètre est facultative.</span><span class="sxs-lookup"><span data-stu-id="a3a47-154">The parameter name **Property** is optional.</span></span> <span data-ttu-id="a3a47-155">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="a3a47-155">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="a3a47-156">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="a3a47-156">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="a3a47-157">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="a3a47-157">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="a3a47-158">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="a3a47-158">Valid key-value pairs are:</span></span>

- <span data-ttu-id="a3a47-159">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="a3a47-159">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="a3a47-160">Profondeur `<int32>`</span><span class="sxs-lookup"><span data-stu-id="a3a47-160">Depth - `<int32>`</span></span>

<span data-ttu-id="a3a47-161">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="a3a47-161">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="a3a47-162">-ShowError</span><span class="sxs-lookup"><span data-stu-id="a3a47-162">-ShowError</span></span>

<span data-ttu-id="a3a47-163">Envoie les erreurs via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a3a47-163">Sends errors through the pipeline.</span></span> <span data-ttu-id="a3a47-164">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-Custom` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="a3a47-164">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="a3a47-165">-Afficher</span><span class="sxs-lookup"><span data-stu-id="a3a47-165">-View</span></span>

<span data-ttu-id="a3a47-166">Spécifie le nom d’un autre format ou d’une autre vue.</span><span class="sxs-lookup"><span data-stu-id="a3a47-166">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="a3a47-167">Si vous omettez ce paramètre, `Format-Custom` utilise une vue personnalisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="a3a47-167">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="a3a47-168">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="a3a47-168">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="a3a47-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3a47-169">CommonParameters</span></span>

<span data-ttu-id="a3a47-170">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a3a47-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3a47-171">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a3a47-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a3a47-172">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a3a47-172">INPUTS</span></span>

### <span data-ttu-id="a3a47-173">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="a3a47-173">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a3a47-174">Vous pouvez diriger n’importe quel objet vers `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="a3a47-174">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="a3a47-175">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a3a47-175">OUTPUTS</span></span>

### <span data-ttu-id="a3a47-176">Microsoft. PowerShell. Commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="a3a47-176">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="a3a47-177">`Format-Custom` retourne les objets de format qui représentent l’affichage.</span><span class="sxs-lookup"><span data-stu-id="a3a47-177">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="a3a47-178">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a3a47-178">NOTES</span></span>

<span data-ttu-id="a3a47-179">`Format-Custom` est conçu pour afficher des vues qui ne sont pas simplement des tables ou des listes.</span><span class="sxs-lookup"><span data-stu-id="a3a47-179">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="a3a47-180">Pour afficher une autre vue de table, utilisez `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="a3a47-180">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="a3a47-181">Pour afficher un autre affichage de liste, utilisez `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="a3a47-181">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="a3a47-182">Vous pouvez également faire référence à `Format-Custom` par son alias intégré, `fc` .</span><span class="sxs-lookup"><span data-stu-id="a3a47-182">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="a3a47-183">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="a3a47-183">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="a3a47-184">Le paramètre **GroupBy** suppose que les objets sont triés.</span><span class="sxs-lookup"><span data-stu-id="a3a47-184">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="a3a47-185">Avant `Format-Custom` d’utiliser pour regrouper les objets, utilisez `Sort-Object` pour les trier.</span><span class="sxs-lookup"><span data-stu-id="a3a47-185">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="a3a47-186">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a3a47-186">RELATED LINKS</span></span>

[<span data-ttu-id="a3a47-187">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="a3a47-187">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="a3a47-188">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="a3a47-188">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="a3a47-189">Format-List</span><span class="sxs-lookup"><span data-stu-id="a3a47-189">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="a3a47-190">Format-Table</span><span class="sxs-lookup"><span data-stu-id="a3a47-190">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="a3a47-191">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="a3a47-191">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="a3a47-192">Get-Process</span><span class="sxs-lookup"><span data-stu-id="a3a47-192">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
