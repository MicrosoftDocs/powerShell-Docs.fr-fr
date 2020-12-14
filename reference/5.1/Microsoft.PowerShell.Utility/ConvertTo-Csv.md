---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: be590368539f396f0aac694e9565674393543f2c
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913200"
---
# <span data-ttu-id="c2d31-102">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="c2d31-102">ConvertTo-Csv</span></span>

## <span data-ttu-id="c2d31-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c2d31-103">SYNOPSIS</span></span>
<span data-ttu-id="c2d31-104">Convertit des objets .NET en une série de chaînes de valeurs séparées par des virgules (CSV).</span><span class="sxs-lookup"><span data-stu-id="c2d31-104">Converts .NET objects into a series of comma-separated value (CSV) strings.</span></span>

## <span data-ttu-id="c2d31-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c2d31-105">SYNTAX</span></span>

### <span data-ttu-id="c2d31-106">Délimiteur (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c2d31-106">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### <span data-ttu-id="c2d31-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="c2d31-107">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## <span data-ttu-id="c2d31-108">Description</span><span class="sxs-lookup"><span data-stu-id="c2d31-108">DESCRIPTION</span></span>

<span data-ttu-id="c2d31-109">L' `ConvertTo-CSV` applet de commande retourne une série de chaînes de valeurs séparées par des virgules (CSV) qui représentent les objets que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="c2d31-109">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="c2d31-110">Vous pouvez ensuite utiliser l' `ConvertFrom-Csv` applet de commande pour recréer des objets à partir des chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-110">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="c2d31-111">Les objets convertis à partir de CSV sont des valeurs de chaîne des objets d’origine qui contiennent des valeurs de propriété et aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="c2d31-111">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="c2d31-112">Vous pouvez utiliser l' `Export-Csv` applet de commande pour convertir des objets en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-112">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="c2d31-113">`Export-CSV` est semblable à `ConvertTo-CSV` , à ceci près qu’elle enregistre les chaînes CSV dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="c2d31-113">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="c2d31-114">L' `ConvertTo-CSV` applet de commande possède des paramètres pour spécifier un délimiteur autre qu’une virgule ou utiliser la culture actuelle comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="c2d31-114">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="c2d31-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c2d31-115">EXAMPLES</span></span>

### <span data-ttu-id="c2d31-116">Exemple 1 : convertir un objet au format CSV</span><span class="sxs-lookup"><span data-stu-id="c2d31-116">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="c2d31-117">Cet exemple convertit un objet **processus** en une chaîne CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-117">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

<span data-ttu-id="c2d31-118">L' `Get-Process` applet de commande obtient l’objet **processus** et utilise le paramètre **Name** pour spécifier le processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2d31-118">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="c2d31-119">L’objet processus est envoyé dans le pipeline à l’applet de commande `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="c2d31-119">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="c2d31-120">L' `ConvertTo-CSV` applet de commande convertit l’objet en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-120">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="c2d31-121">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-121">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

### <span data-ttu-id="c2d31-122">Exemple 2 : convertir un objet DateTime en CSV</span><span class="sxs-lookup"><span data-stu-id="c2d31-122">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="c2d31-123">Cet exemple convertit un objet **DateTime** en une chaîne CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-123">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="c2d31-124">L' `Get-Date` applet de commande obtient l’objet **DateTime** et l’enregistre dans la `$Date` variable.</span><span class="sxs-lookup"><span data-stu-id="c2d31-124">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="c2d31-125">L' `ConvertTo-Csv` applet de commande convertit l’objet **DateTime** en chaînes.</span><span class="sxs-lookup"><span data-stu-id="c2d31-125">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="c2d31-126">Le paramètre **InputObject** utilise l’objet **DateTime** stocké dans la `$Date` variable.</span><span class="sxs-lookup"><span data-stu-id="c2d31-126">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="c2d31-127">Le paramètre **Delimiter** spécifie un point-virgule pour séparer les valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c2d31-127">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="c2d31-128">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-128">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

### <span data-ttu-id="c2d31-129">Exemple 3 : convertir le journal des événements PowerShell au format CSV</span><span class="sxs-lookup"><span data-stu-id="c2d31-129">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="c2d31-130">Cet exemple convertit le journal des événements Windows pour PowerShell en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-130">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

<span data-ttu-id="c2d31-131">L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** et affiche le séparateur de liste par défaut de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="c2d31-131">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="c2d31-132">L' `Get-WinEvent` applet de commande obtient les objets du journal des événements et utilise le paramètre **logname** pour spécifier le nom du fichier journal.</span><span class="sxs-lookup"><span data-stu-id="c2d31-132">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="c2d31-133">Les objets du journal des événements sont envoyés vers l’applet de commande via le pipeline `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="c2d31-133">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="c2d31-134">L' `ConvertTo-Csv` applet de commande convertit les objets du journal des événements en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-134">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="c2d31-135">Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="c2d31-135">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="c2d31-136">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-136">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

## <span data-ttu-id="c2d31-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2d31-137">PARAMETERS</span></span>

### <span data-ttu-id="c2d31-138">-Délimiteur</span><span class="sxs-lookup"><span data-stu-id="c2d31-138">-Delimiter</span></span>

<span data-ttu-id="c2d31-139">Spécifie le délimiteur pour séparer les valeurs de propriété dans les chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-139">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="c2d31-140">La valeur par défaut est une virgule ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="c2d31-140">The default is a comma (`,`).</span></span> <span data-ttu-id="c2d31-141">Entrez un caractère, tel qu’un signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="c2d31-141">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="c2d31-142">Pour spécifier un point-virgule ( `;` ), placez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="c2d31-142">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c2d31-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c2d31-143">-InputObject</span></span>

<span data-ttu-id="c2d31-144">Spécifie les objets qui sont convertis en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="c2d31-144">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="c2d31-145">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="c2d31-145">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="c2d31-146">Vous pouvez également diriger les objets vers `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="c2d31-146">You can also pipe objects to `ConvertTo-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c2d31-147">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="c2d31-147">-NoTypeInformation</span></span>

<span data-ttu-id="c2d31-148">Supprime l’en-tête d’informations **#TYPE** de la sortie.</span><span class="sxs-lookup"><span data-stu-id="c2d31-148">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="c2d31-149">Ce paramètre est devenu la valeur par défaut dans PowerShell 6,0 et est inclus à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="c2d31-149">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c2d31-150">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="c2d31-150">-UseCulture</span></span>

<span data-ttu-id="c2d31-151">Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément.</span><span class="sxs-lookup"><span data-stu-id="c2d31-151">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="c2d31-152">Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="c2d31-152">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c2d31-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2d31-153">CommonParameters</span></span>

<span data-ttu-id="c2d31-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c2d31-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c2d31-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c2d31-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c2d31-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c2d31-156">INPUTS</span></span>

### <span data-ttu-id="c2d31-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="c2d31-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c2d31-158">Vous pouvez diriger n’importe quel objet ayant un adaptateur de système de type étendu (ETS) vers `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="c2d31-158">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="c2d31-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c2d31-159">OUTPUTS</span></span>

### <span data-ttu-id="c2d31-160">System.String</span><span class="sxs-lookup"><span data-stu-id="c2d31-160">System.String</span></span>

<span data-ttu-id="c2d31-161">La sortie CSV est renvoyée sous forme d'une collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="c2d31-161">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="c2d31-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c2d31-162">NOTES</span></span>

<span data-ttu-id="c2d31-163">Au format CSV, chaque objet est représenté par une liste séparée par des virgules de sa valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="c2d31-163">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="c2d31-164">Les valeurs de propriété sont converties en chaînes à l’aide de la méthode **ToString ()** de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c2d31-164">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="c2d31-165">Les chaînes sont représentées par le nom de la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="c2d31-165">The strings are represented by the property value name.</span></span> <span data-ttu-id="c2d31-166">`ConvertTo-CSV` n’exporte pas les méthodes de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c2d31-166">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="c2d31-167">Les chaînes CSV sont générées comme suit :</span><span class="sxs-lookup"><span data-stu-id="c2d31-167">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="c2d31-168">Par défaut, la première chaîne contient l’en-tête d’informations **#TYPE** , suivi du nom qualifié complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="c2d31-168">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="c2d31-169">Par exemple, **#TYPE System. Diagnostics. Process**.</span><span class="sxs-lookup"><span data-stu-id="c2d31-169">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="c2d31-170">Si **NoTypeInformation** est utilisé, la première chaîne comprend les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="c2d31-170">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="c2d31-171">Les en-têtes contiennent les noms de propriété du premier objet sous la forme d’une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c2d31-171">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="c2d31-172">Les chaînes restantes contiennent des listes séparées par des virgules des valeurs de propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="c2d31-172">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="c2d31-173">Lorsque vous envoyez plusieurs objets à `ConvertTo-CSV` , `ConvertTo-CSV` trie les chaînes en fonction des propriétés du premier objet que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="c2d31-173">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="c2d31-174">Si les objets restants n’ont pas l’une des propriétés spécifiées, la valeur de propriété de cet objet est null, comme représenté par deux virgules consécutives.</span><span class="sxs-lookup"><span data-stu-id="c2d31-174">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="c2d31-175">Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="c2d31-175">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="c2d31-176">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c2d31-176">RELATED LINKS</span></span>

[<span data-ttu-id="c2d31-177">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="c2d31-177">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="c2d31-178">Export-CSV</span><span class="sxs-lookup"><span data-stu-id="c2d31-178">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="c2d31-179">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="c2d31-179">Import-Csv</span></span>](Import-Csv.md)
