---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: a025432e8aed93f6668c676161c21377d0ba225c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93206022"
---
# <span data-ttu-id="dadf9-103">Format-List</span><span class="sxs-lookup"><span data-stu-id="dadf9-103">Format-List</span></span>

## <span data-ttu-id="dadf9-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="dadf9-104">SYNOPSIS</span></span>
<span data-ttu-id="dadf9-105">Organise la sortie sous la forme d'une liste de propriétés dont chaque élément apparaît sur sa propre ligne.</span><span class="sxs-lookup"><span data-stu-id="dadf9-105">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="dadf9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dadf9-106">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="dadf9-107">Description</span><span class="sxs-lookup"><span data-stu-id="dadf9-107">DESCRIPTION</span></span>

<span data-ttu-id="dadf9-108">L' `Format-List` applet de commande met en forme la sortie d’une commande sous la forme d’une liste de propriétés dans laquelle chaque propriété est affichée sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="dadf9-108">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="dadf9-109">Vous pouvez utiliser `Format-List` pour mettre en forme et afficher toutes les propriétés ou les propriétés sélectionnées d’un objet sous forme de liste (format-list \*).</span><span class="sxs-lookup"><span data-stu-id="dadf9-109">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="dadf9-110">Étant donné que de l’espace est disponible pour chaque élément d’une liste, PowerShell affiche plus de propriétés de l’objet dans la liste, et les valeurs de propriété sont moins susceptibles d’être tronquées.</span><span class="sxs-lookup"><span data-stu-id="dadf9-110">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="dadf9-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="dadf9-111">EXAMPLES</span></span>

### <span data-ttu-id="dadf9-112">Exemple 1 : mettre en forme les services informatiques</span><span class="sxs-lookup"><span data-stu-id="dadf9-112">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="dadf9-113">Cette commande met en forme des informations sur des services sur l'ordinateur sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="dadf9-113">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="dadf9-114">Par défaut, les services sont mis en forme en tant que table.</span><span class="sxs-lookup"><span data-stu-id="dadf9-114">By default, the services are formatted as a table.</span></span> <span data-ttu-id="dadf9-115">L' `Get-Service` applet de commande obtient les objets représentant les services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dadf9-115">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="dadf9-116">L’opérateur de pipeline (|) passe les résultats dans le pipeline à `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-116">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="dadf9-117">Ensuite, la `Format-List` commande met en forme les informations de service dans une liste et les envoie à l’applet de commande de sortie par défaut pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="dadf9-117">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="dadf9-118">Exemple 2 : mettre en forme les fichiers PS1XML</span><span class="sxs-lookup"><span data-stu-id="dadf9-118">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="dadf9-119">Ces commandes affichent des informations sur les fichiers PS1XML dans le répertoire PowerShell sous la forme d’une liste.</span><span class="sxs-lookup"><span data-stu-id="dadf9-119">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="dadf9-120">La première commande récupère les objets qui représentent les fichiers et les stocke dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="dadf9-120">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="dadf9-121">La deuxième commande utilise `Format-List` pour mettre en forme les informations sur les objets stockés dans `$A` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-121">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="dadf9-122">Cette commande utilise le paramètre **InputObject** pour passer la variable à `Format-List` , qui envoie ensuite la sortie mise en forme à l’applet de commande de sortie par défaut pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="dadf9-122">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="dadf9-123">Exemple 3 : mettre en forme les propriétés de processus par nom</span><span class="sxs-lookup"><span data-stu-id="dadf9-123">Example 3: Format process properties by name</span></span>

<span data-ttu-id="dadf9-124">Cette commande affiche le nom, la priorité de base et la classe de priorité de chaque processus sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dadf9-124">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="dadf9-125">Elle utilise l' `Get-Process` applet de commande pour récupérer un objet représentant chaque processus.</span><span class="sxs-lookup"><span data-stu-id="dadf9-125">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="dadf9-126">L’opérateur de pipeline (|) passe les objets de processus via le pipeline à `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-126">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="dadf9-127">`Format-List` met en forme les processus en tant que liste des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="dadf9-127">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="dadf9-128">Le nom du paramètre de *propriété* est facultatif, vous pouvez donc l’omettre.</span><span class="sxs-lookup"><span data-stu-id="dadf9-128">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="dadf9-129">Exemple 4 : mettre en forme toutes les propriétés d’un processus</span><span class="sxs-lookup"><span data-stu-id="dadf9-129">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="dadf9-130">Cette commande affiche toutes les propriétés du processus Winlogon.</span><span class="sxs-lookup"><span data-stu-id="dadf9-130">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="dadf9-131">Elle utilise l'applet de commande Get-Process pour obtenir un objet représentant le processus Winlogon.</span><span class="sxs-lookup"><span data-stu-id="dadf9-131">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="dadf9-132">L’opérateur de pipeline (|) passe l’objet de processus Winlogon via le pipeline à `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-132">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="dadf9-133">La commande utilise le paramètre *Property* pour spécifier les propriétés et \* pour indiquer toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="dadf9-133">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="dadf9-134">Étant donné que le nom du paramètre *Property* est facultatif, vous pouvez l’omettre et taper la commande comme `Format-List *` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-134">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="dadf9-135">`Format-List` envoie automatiquement les résultats à l’applet de commande de sortie par défaut pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="dadf9-135">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="dadf9-136">Exemple 5 : dépannage des erreurs de format</span><span class="sxs-lookup"><span data-stu-id="dadf9-136">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="dadf9-137">Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.</span><span class="sxs-lookup"><span data-stu-id="dadf9-137">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

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

## <span data-ttu-id="dadf9-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dadf9-138">PARAMETERS</span></span>

### <span data-ttu-id="dadf9-139">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="dadf9-139">-DisplayError</span></span>

<span data-ttu-id="dadf9-140">Indique que cette applet de commande affiche les erreurs sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="dadf9-140">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="dadf9-141">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-List` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="dadf9-141">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="dadf9-142">-Développer</span><span class="sxs-lookup"><span data-stu-id="dadf9-142">-Expand</span></span>

<span data-ttu-id="dadf9-143">Spécifie l’objet de collection mis en forme, ainsi que les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="dadf9-143">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="dadf9-144">Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l'interface ICollection (System.Collections).</span><span class="sxs-lookup"><span data-stu-id="dadf9-144">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="dadf9-145">La valeur par défaut est EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="dadf9-145">The default value is EnumOnly.</span></span> <span data-ttu-id="dadf9-146">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="dadf9-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dadf9-147">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="dadf9-147">EnumOnly.</span></span> <span data-ttu-id="dadf9-148">Affiche les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="dadf9-148">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="dadf9-149">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="dadf9-149">CoreOnly.</span></span> <span data-ttu-id="dadf9-150">Affiche les propriétés de l'objet de collection.</span><span class="sxs-lookup"><span data-stu-id="dadf9-150">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="dadf9-151">Les deux.</span><span class="sxs-lookup"><span data-stu-id="dadf9-151">Both.</span></span> <span data-ttu-id="dadf9-152">Affiche les propriétés de l'objet de collection et les propriétés des objets contenus dans la collection.</span><span class="sxs-lookup"><span data-stu-id="dadf9-152">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

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

### <span data-ttu-id="dadf9-153">-Force</span><span class="sxs-lookup"><span data-stu-id="dadf9-153">-Force</span></span>

<span data-ttu-id="dadf9-154">Indique que cette applet de commande affiche toutes les informations sur l’erreur.</span><span class="sxs-lookup"><span data-stu-id="dadf9-154">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="dadf9-155">Utilisez avec le paramètre **DisplayError** ou **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="dadf9-155">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="dadf9-156">Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.</span><span class="sxs-lookup"><span data-stu-id="dadf9-156">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="dadf9-157">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="dadf9-157">-GroupBy</span></span>

<span data-ttu-id="dadf9-158">Spécifie la sortie dans des groupes en fonction d’une valeur ou d’une propriété partagée.</span><span class="sxs-lookup"><span data-stu-id="dadf9-158">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="dadf9-159">Entrez une expression ou une propriété de la sortie.</span><span class="sxs-lookup"><span data-stu-id="dadf9-159">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="dadf9-160">La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="dadf9-160">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="dadf9-161">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="dadf9-161">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="dadf9-162">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="dadf9-162">Valid key-value pairs are:</span></span>

- <span data-ttu-id="dadf9-163">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="dadf9-163">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="dadf9-164">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="dadf9-164">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="dadf9-165">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="dadf9-165">FormatString - `<string>`</span></span>

<span data-ttu-id="dadf9-166">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="dadf9-166">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="dadf9-167">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dadf9-167">-InputObject</span></span>

<span data-ttu-id="dadf9-168">Spécifie les objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="dadf9-168">Specifies the objects to be formatted.</span></span> <span data-ttu-id="dadf9-169">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="dadf9-169">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="dadf9-170">-Propriété</span><span class="sxs-lookup"><span data-stu-id="dadf9-170">-Property</span></span>

<span data-ttu-id="dadf9-171">Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="dadf9-171">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="dadf9-172">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="dadf9-172">Wildcards are permitted.</span></span>

<span data-ttu-id="dadf9-173">Si vous omettez ce paramètre, les propriétés qui apparaissent dans l'affichage dépendent de l'objet affiché.</span><span class="sxs-lookup"><span data-stu-id="dadf9-173">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="dadf9-174">Le nom de paramètre « Property » est facultatif.</span><span class="sxs-lookup"><span data-stu-id="dadf9-174">The parameter name "Property" is optional.</span></span> <span data-ttu-id="dadf9-175">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="dadf9-175">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="dadf9-176">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="dadf9-176">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="dadf9-177">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="dadf9-177">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="dadf9-178">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="dadf9-178">Valid key-value pairs are:</span></span>

- <span data-ttu-id="dadf9-179">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="dadf9-179">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="dadf9-180">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="dadf9-180">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="dadf9-181">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="dadf9-181">FormatString - `<string>`</span></span>

<span data-ttu-id="dadf9-182">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="dadf9-182">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="dadf9-183">-ShowError</span><span class="sxs-lookup"><span data-stu-id="dadf9-183">-ShowError</span></span>

<span data-ttu-id="dadf9-184">Indique que l’applet de commande envoie des erreurs par le biais du pipeline.</span><span class="sxs-lookup"><span data-stu-id="dadf9-184">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="dadf9-185">Ce paramètre est rarement utilisé, mais il peut être utilisé comme une aide au débogage quand vous formatez des expressions dans une `Format-List` commande et que les expressions ne semblent pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="dadf9-185">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="dadf9-186">-Afficher</span><span class="sxs-lookup"><span data-stu-id="dadf9-186">-View</span></span>

<span data-ttu-id="dadf9-187">Spécifie le nom d’une vue ou d’un format de liste secondaire.</span><span class="sxs-lookup"><span data-stu-id="dadf9-187">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="dadf9-188">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="dadf9-188">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="dadf9-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dadf9-189">CommonParameters</span></span>

<span data-ttu-id="dadf9-190">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dadf9-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dadf9-191">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dadf9-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dadf9-192">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="dadf9-192">INPUTS</span></span>

### <span data-ttu-id="dadf9-193">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="dadf9-193">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="dadf9-194">Vous pouvez diriger n’importe quel objet vers `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-194">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="dadf9-195">SORTIES</span><span class="sxs-lookup"><span data-stu-id="dadf9-195">OUTPUTS</span></span>

### <span data-ttu-id="dadf9-196">Microsoft. PowerShell. Commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="dadf9-196">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="dadf9-197">`Format-List` retourne les objets de format qui représentent la liste.</span><span class="sxs-lookup"><span data-stu-id="dadf9-197">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="dadf9-198">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="dadf9-198">NOTES</span></span>

<span data-ttu-id="dadf9-199">Vous pouvez également faire référence à Format-List par son alias intégré, FL.</span><span class="sxs-lookup"><span data-stu-id="dadf9-199">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="dadf9-200">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="dadf9-200">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="dadf9-201">Les applets de commande format, telles que `Format-List` , organisent les données à afficher, mais ne les affichent pas.</span><span class="sxs-lookup"><span data-stu-id="dadf9-201">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="dadf9-202">Les données sont affichées par les fonctionnalités de sortie de PowerShell et par les applets de commande qui contiennent le verbe out (applets de commande Out), telles que `Out-Host` ou `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-202">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="dadf9-203">Si vous n’utilisez pas d’applet de commande format, PowerShell applique ce format par défaut pour chaque objet qu’il affiche.</span><span class="sxs-lookup"><span data-stu-id="dadf9-203">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="dadf9-204">Le paramètre **GroupBy** suppose que les objets sont triés.</span><span class="sxs-lookup"><span data-stu-id="dadf9-204">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="dadf9-205">Utilisez Sort-Object avant `Format-List` d’utiliser pour regrouper les objets.</span><span class="sxs-lookup"><span data-stu-id="dadf9-205">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="dadf9-206">Le paramètre **View** vous permet de spécifier un autre format pour la table.</span><span class="sxs-lookup"><span data-stu-id="dadf9-206">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="dadf9-207">Vous pouvez utiliser les affichages définis dans les `*.format.PS1XML` fichiers dans le répertoire PowerShell, ou vous pouvez créer vos propres affichages dans de nouveaux fichiers ps1xml et utiliser l’applet de commande Update-FormatData pour les inclure dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dadf9-207">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="dadf9-208">L’autre vue pour le paramètre **View** doit utiliser le format de liste ; sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="dadf9-208">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="dadf9-209">Si l’autre vue est une table, utilisez `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-209">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="dadf9-210">Si l’autre vue n’est ni une liste ni une table, utilisez `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="dadf9-210">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="dadf9-211">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="dadf9-211">RELATED LINKS</span></span>

[<span data-ttu-id="dadf9-212">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="dadf9-212">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="dadf9-213">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="dadf9-213">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="dadf9-214">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="dadf9-214">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="dadf9-215">Format-Table</span><span class="sxs-lookup"><span data-stu-id="dadf9-215">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="dadf9-216">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="dadf9-216">Format-Wide</span></span>](Format-Wide.md)
