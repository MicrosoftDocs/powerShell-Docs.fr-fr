---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: d8410fbc2d3f29f0726f84ab151993a60ce95434
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597159"
---
# <span data-ttu-id="53998-102">Format-List</span><span class="sxs-lookup"><span data-stu-id="53998-102">Format-List</span></span>

## <span data-ttu-id="53998-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="53998-103">SYNOPSIS</span></span>
<span data-ttu-id="53998-104">Organise la sortie sous la forme d'une liste de propriétés dont chaque élément apparaît sur sa propre ligne.</span><span class="sxs-lookup"><span data-stu-id="53998-104">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="53998-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="53998-105">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="53998-106">Description</span><span class="sxs-lookup"><span data-stu-id="53998-106">DESCRIPTION</span></span>

<span data-ttu-id="53998-107">L' `Format-List` applet de commande met en forme la sortie d’une commande sous la forme d’une liste de propriétés dans laquelle chaque propriété est affichée sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="53998-107">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="53998-108">Vous pouvez utiliser `Format-List` pour mettre en forme et afficher toutes les propriétés ou les propriétés sélectionnées d’un objet sous forme de liste (format-list \*).</span><span class="sxs-lookup"><span data-stu-id="53998-108">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="53998-109">Étant donné que de l’espace est disponible pour chaque élément d’une liste, PowerShell affiche plus de propriétés de l’objet dans la liste, et les valeurs de propriété sont moins susceptibles d’être tronquées.</span><span class="sxs-lookup"><span data-stu-id="53998-109">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="53998-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="53998-110">EXAMPLES</span></span>

### <span data-ttu-id="53998-111">Exemple 1 : mettre en forme les services informatiques</span><span class="sxs-lookup"><span data-stu-id="53998-111">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="53998-112">Cette commande met en forme des informations sur des services sur l'ordinateur sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="53998-112">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="53998-113">Par défaut, les services sont mis en forme en tant que table.</span><span class="sxs-lookup"><span data-stu-id="53998-113">By default, the services are formatted as a table.</span></span> <span data-ttu-id="53998-114">L' `Get-Service` applet de commande obtient les objets représentant les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="53998-114">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="53998-115">L’opérateur de pipeline (|) passe les résultats dans le pipeline à `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="53998-115">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="53998-116">Ensuite, la `Format-List` commande met en forme les informations de service dans une liste et les envoie à l’applet de commande de sortie par défaut pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="53998-116">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="53998-117">Exemple 2 : mettre en forme les fichiers PS1XML</span><span class="sxs-lookup"><span data-stu-id="53998-117">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="53998-118">Ces commandes affichent des informations sur les fichiers PS1XML dans le répertoire PowerShell sous la forme d’une liste.</span><span class="sxs-lookup"><span data-stu-id="53998-118">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="53998-119">La première commande récupère les objets qui représentent les fichiers et les stocke dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="53998-119">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="53998-120">La deuxième commande utilise `Format-List` pour mettre en forme les informations sur les objets stockés dans `$A` .</span><span class="sxs-lookup"><span data-stu-id="53998-120">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="53998-121">Cette commande utilise le paramètre **InputObject** pour passer la variable à `Format-List` , qui envoie ensuite la sortie mise en forme à l’applet de commande de sortie par défaut pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="53998-121">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="53998-122">Exemple 3 : mettre en forme les propriétés de processus par nom</span><span class="sxs-lookup"><span data-stu-id="53998-122">Example 3: Format process properties by name</span></span>

<span data-ttu-id="53998-123">Cette commande affiche le nom, la priorité de base et la classe de priorité de chaque processus sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="53998-123">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="53998-124">Elle utilise l' `Get-Process` applet de commande pour récupérer un objet représentant chaque processus.</span><span class="sxs-lookup"><span data-stu-id="53998-124">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="53998-125">L’opérateur de pipeline (|) passe les objets de processus via le pipeline à `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="53998-125">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="53998-126">`Format-List` met en forme les processus en tant que liste des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="53998-126">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="53998-127">Le nom du paramètre de *propriété* est facultatif, vous pouvez donc l’omettre.</span><span class="sxs-lookup"><span data-stu-id="53998-127">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="53998-128">Exemple 4 : mettre en forme toutes les propriétés d’un processus</span><span class="sxs-lookup"><span data-stu-id="53998-128">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="53998-129">Cette commande affiche toutes les propriétés du processus Winlogon.</span><span class="sxs-lookup"><span data-stu-id="53998-129">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="53998-130">Elle utilise l'applet de commande Get-Process pour obtenir un objet représentant le processus Winlogon.</span><span class="sxs-lookup"><span data-stu-id="53998-130">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="53998-131">L’opérateur de pipeline (|) passe l’objet de processus Winlogon via le pipeline à `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="53998-131">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="53998-132">La commande utilise le paramètre *Property* pour spécifier les propriétés et \* pour indiquer toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="53998-132">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="53998-133">Étant donné que le nom du paramètre *Property* est facultatif, vous pouvez l’omettre et taper la commande comme `Format-List *` .</span><span class="sxs-lookup"><span data-stu-id="53998-133">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="53998-134">`Format-List` envoie automatiquement les résultats à l’applet de commande de sortie par défaut pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="53998-134">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="53998-135">Exemple 5 : dépannage des erreurs de format</span><span class="sxs-lookup"><span data-stu-id="53998-135">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="53998-136">Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.</span><span class="sxs-lookup"><span data-stu-id="53998-136">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="53998-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="53998-137">PARAMETERS</span></span>

### <span data-ttu-id="53998-138">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="53998-138">-DisplayError</span></span>

<span data-ttu-id="53998-139">Indique que cette applet de commande affiche les erreurs sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="53998-139">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="53998-140">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-List` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="53998-140">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="53998-141">-Développer</span><span class="sxs-lookup"><span data-stu-id="53998-141">-Expand</span></span>

<span data-ttu-id="53998-142">Spécifie l’objet de collection mis en forme, ainsi que les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="53998-142">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="53998-143">Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l'interface ICollection (System.Collections).</span><span class="sxs-lookup"><span data-stu-id="53998-143">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="53998-144">La valeur par défaut est EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="53998-144">The default value is EnumOnly.</span></span> <span data-ttu-id="53998-145">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="53998-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="53998-146">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="53998-146">EnumOnly.</span></span> <span data-ttu-id="53998-147">Affiche les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="53998-147">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="53998-148">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="53998-148">CoreOnly.</span></span> <span data-ttu-id="53998-149">Affiche les propriétés de l'objet de collection.</span><span class="sxs-lookup"><span data-stu-id="53998-149">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="53998-150">Les deux.</span><span class="sxs-lookup"><span data-stu-id="53998-150">Both.</span></span> <span data-ttu-id="53998-151">Affiche les propriétés de l'objet de collection et les propriétés des objets contenus dans la collection.</span><span class="sxs-lookup"><span data-stu-id="53998-151">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53998-152">-Force</span><span class="sxs-lookup"><span data-stu-id="53998-152">-Force</span></span>

<span data-ttu-id="53998-153">Indique que cette applet de commande affiche toutes les informations sur l’erreur.</span><span class="sxs-lookup"><span data-stu-id="53998-153">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="53998-154">Utilisez avec le paramètre **DisplayError** ou **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="53998-154">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="53998-155">Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.</span><span class="sxs-lookup"><span data-stu-id="53998-155">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="53998-156">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="53998-156">-GroupBy</span></span>

<span data-ttu-id="53998-157">Spécifie la sortie dans des groupes en fonction d’une valeur ou d’une propriété partagée.</span><span class="sxs-lookup"><span data-stu-id="53998-157">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="53998-158">Entrez une expression ou une propriété de la sortie.</span><span class="sxs-lookup"><span data-stu-id="53998-158">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="53998-159">La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="53998-159">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="53998-160">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="53998-160">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="53998-161">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="53998-161">Valid key-value pairs are:</span></span>

- <span data-ttu-id="53998-162">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="53998-162">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="53998-163">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="53998-163">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="53998-164">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="53998-164">FormatString - `<string>`</span></span>

<span data-ttu-id="53998-165">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="53998-165">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="53998-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="53998-166">-InputObject</span></span>

<span data-ttu-id="53998-167">Spécifie les objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="53998-167">Specifies the objects to be formatted.</span></span> <span data-ttu-id="53998-168">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="53998-168">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="53998-169">-Propriété</span><span class="sxs-lookup"><span data-stu-id="53998-169">-Property</span></span>

<span data-ttu-id="53998-170">Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="53998-170">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="53998-171">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="53998-171">Wildcards are permitted.</span></span>

<span data-ttu-id="53998-172">Si vous omettez ce paramètre, les propriétés qui apparaissent dans l'affichage dépendent de l'objet affiché.</span><span class="sxs-lookup"><span data-stu-id="53998-172">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="53998-173">Le nom de paramètre « Property » est facultatif.</span><span class="sxs-lookup"><span data-stu-id="53998-173">The parameter name "Property" is optional.</span></span> <span data-ttu-id="53998-174">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="53998-174">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="53998-175">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="53998-175">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="53998-176">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="53998-176">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="53998-177">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="53998-177">Valid key-value pairs are:</span></span>

- <span data-ttu-id="53998-178">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="53998-178">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="53998-179">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="53998-179">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="53998-180">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="53998-180">FormatString - `<string>`</span></span>

<span data-ttu-id="53998-181">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="53998-181">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="53998-182">-ShowError</span><span class="sxs-lookup"><span data-stu-id="53998-182">-ShowError</span></span>

<span data-ttu-id="53998-183">Indique que l’applet de commande envoie des erreurs par le biais du pipeline.</span><span class="sxs-lookup"><span data-stu-id="53998-183">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="53998-184">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-List` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="53998-184">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="53998-185">-Afficher</span><span class="sxs-lookup"><span data-stu-id="53998-185">-View</span></span>

<span data-ttu-id="53998-186">Spécifie le nom d’une vue ou d’un format de liste secondaire.</span><span class="sxs-lookup"><span data-stu-id="53998-186">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="53998-187">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="53998-187">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="53998-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53998-188">CommonParameters</span></span>

<span data-ttu-id="53998-189">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="53998-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53998-190">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="53998-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53998-191">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="53998-191">INPUTS</span></span>

### <span data-ttu-id="53998-192">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="53998-192">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="53998-193">Vous pouvez diriger n’importe quel objet vers `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="53998-193">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="53998-194">SORTIES</span><span class="sxs-lookup"><span data-stu-id="53998-194">OUTPUTS</span></span>

### <span data-ttu-id="53998-195">Microsoft. PowerShell. Commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="53998-195">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="53998-196">`Format-List` retourne les objets de format qui représentent la liste.</span><span class="sxs-lookup"><span data-stu-id="53998-196">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="53998-197">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="53998-197">NOTES</span></span>

<span data-ttu-id="53998-198">Vous pouvez également faire référence à Format-List par son alias intégré, FL.</span><span class="sxs-lookup"><span data-stu-id="53998-198">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="53998-199">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="53998-199">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="53998-200">Les applets de commande format, telles que `Format-List` , organisent les données à afficher, mais ne les affichent pas.</span><span class="sxs-lookup"><span data-stu-id="53998-200">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="53998-201">Les données sont affichées par les fonctionnalités de sortie de PowerShell et par les applets de commande qui contiennent le verbe out (applets de commande Out), telles que `Out-Host` ou `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="53998-201">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="53998-202">Si vous n’utilisez pas d’applet de commande format, PowerShell applique ce format par défaut pour chaque objet qu’il affiche.</span><span class="sxs-lookup"><span data-stu-id="53998-202">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="53998-203">Le paramètre **GroupBy** suppose que les objets sont triés.</span><span class="sxs-lookup"><span data-stu-id="53998-203">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="53998-204">Utilisez Sort-Object avant `Format-List` d’utiliser pour regrouper les objets.</span><span class="sxs-lookup"><span data-stu-id="53998-204">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="53998-205">Le paramètre **View** vous permet de spécifier un autre format pour la table.</span><span class="sxs-lookup"><span data-stu-id="53998-205">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="53998-206">Vous pouvez utiliser les affichages définis dans les `*.format.PS1XML` fichiers dans le répertoire PowerShell, ou vous pouvez créer vos propres affichages dans de nouveaux fichiers ps1xml et utiliser l’applet de commande Update-FormatData pour les inclure dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53998-206">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="53998-207">L’autre vue pour le paramètre **View** doit utiliser le format de liste ; sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="53998-207">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="53998-208">Si l’autre vue est une table, utilisez `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="53998-208">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="53998-209">Si l’autre vue n’est ni une liste ni une table, utilisez `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="53998-209">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="53998-210">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="53998-210">RELATED LINKS</span></span>

[<span data-ttu-id="53998-211">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="53998-211">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="53998-212">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="53998-212">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="53998-213">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="53998-213">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="53998-214">Format-Table</span><span class="sxs-lookup"><span data-stu-id="53998-214">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="53998-215">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="53998-215">Format-Wide</span></span>](Format-Wide.md)
