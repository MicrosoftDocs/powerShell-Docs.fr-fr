---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 9638577ef63a6f5d81fa1f84aee355c080ab6538
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913374"
---
# <span data-ttu-id="60f62-102">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="60f62-102">ConvertTo-Csv</span></span>

## <span data-ttu-id="60f62-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="60f62-103">SYNOPSIS</span></span>
<span data-ttu-id="60f62-104">Convertit des objets .NET en une série de chaînes de valeurs séparées par des caractères (CSV).</span><span class="sxs-lookup"><span data-stu-id="60f62-104">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="60f62-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="60f62-105">SYNTAX</span></span>

### <span data-ttu-id="60f62-106">Délimiteur (par défaut)</span><span class="sxs-lookup"><span data-stu-id="60f62-106">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### <span data-ttu-id="60f62-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="60f62-107">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## <span data-ttu-id="60f62-108">Description</span><span class="sxs-lookup"><span data-stu-id="60f62-108">DESCRIPTION</span></span>

<span data-ttu-id="60f62-109">L' `ConvertTo-CSV` applet de commande retourne une série de chaînes de valeurs séparées par des virgules (CSV) qui représentent les objets que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="60f62-109">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="60f62-110">Vous pouvez ensuite utiliser l' `ConvertFrom-Csv` applet de commande pour recréer des objets à partir des chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-110">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="60f62-111">Les objets convertis à partir de CSV sont des valeurs de chaîne des objets d’origine qui contiennent des valeurs de propriété et aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="60f62-111">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="60f62-112">Vous pouvez utiliser l' `Export-Csv` applet de commande pour convertir des objets en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-112">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="60f62-113">`Export-CSV` est semblable à `ConvertTo-CSV` , à ceci près qu’elle enregistre les chaînes CSV dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="60f62-113">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="60f62-114">L' `ConvertTo-CSV` applet de commande possède des paramètres pour spécifier un délimiteur autre qu’une virgule ou utiliser la culture actuelle comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="60f62-114">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="60f62-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="60f62-115">EXAMPLES</span></span>

### <span data-ttu-id="60f62-116">Exemple 1 : convertir un objet au format CSV</span><span class="sxs-lookup"><span data-stu-id="60f62-116">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="60f62-117">Cet exemple convertit un objet **processus** en une chaîne CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-117">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="60f62-118">L' `Get-Process` applet de commande obtient l’objet **processus** et utilise le paramètre **Name** pour spécifier le processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60f62-118">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="60f62-119">L’objet processus est envoyé dans le pipeline à l’applet de commande `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="60f62-119">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="60f62-120">L' `ConvertTo-CSV` applet de commande convertit l’objet en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-120">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="60f62-121">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="60f62-121">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="60f62-122">Exemple 2 : convertir un objet DateTime en CSV</span><span class="sxs-lookup"><span data-stu-id="60f62-122">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="60f62-123">Cet exemple convertit un objet **DateTime** en une chaîne CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-123">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="60f62-124">L' `Get-Date` applet de commande obtient l’objet **DateTime** et l’enregistre dans la `$Date` variable.</span><span class="sxs-lookup"><span data-stu-id="60f62-124">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="60f62-125">L' `ConvertTo-Csv` applet de commande convertit l’objet **DateTime** en chaînes.</span><span class="sxs-lookup"><span data-stu-id="60f62-125">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="60f62-126">Le paramètre **InputObject** utilise l’objet **DateTime** stocké dans la `$Date` variable.</span><span class="sxs-lookup"><span data-stu-id="60f62-126">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="60f62-127">Le paramètre **Delimiter** spécifie un point-virgule pour séparer les valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="60f62-127">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="60f62-128">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="60f62-128">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="60f62-129">Exemple 3 : convertir le journal des événements PowerShell au format CSV</span><span class="sxs-lookup"><span data-stu-id="60f62-129">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="60f62-130">Cet exemple convertit le journal des événements Windows pour PowerShell en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-130">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="60f62-131">L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** et affiche le séparateur de liste par défaut de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="60f62-131">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="60f62-132">L' `Get-WinEvent` applet de commande obtient les objets du journal des événements et utilise le paramètre **logname** pour spécifier le nom du fichier journal.</span><span class="sxs-lookup"><span data-stu-id="60f62-132">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="60f62-133">Les objets du journal des événements sont envoyés vers l’applet de commande via le pipeline `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="60f62-133">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="60f62-134">L' `ConvertTo-Csv` applet de commande convertit les objets du journal des événements en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-134">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="60f62-135">Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="60f62-135">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="60f62-136">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="60f62-136">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="60f62-137">Exemple 4 : convertir en CSV avec des guillemets autour de deux colonnes</span><span class="sxs-lookup"><span data-stu-id="60f62-137">Example 4: Convert to CSV with quotes around two columns</span></span>

<span data-ttu-id="60f62-138">Cet exemple convertit un objet **DateTime** en une chaîne CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-138">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="60f62-139">Exemple 4 : convertir en CSV avec des guillemets uniquement lorsque cela est nécessaire</span><span class="sxs-lookup"><span data-stu-id="60f62-139">Example 4: Convert to CSV with quotes only when needed</span></span>

<span data-ttu-id="60f62-140">Cet exemple convertit un objet **DateTime** en une chaîne CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-140">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="60f62-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="60f62-141">PARAMETERS</span></span>

### <span data-ttu-id="60f62-142">-Délimiteur</span><span class="sxs-lookup"><span data-stu-id="60f62-142">-Delimiter</span></span>

<span data-ttu-id="60f62-143">Spécifie le délimiteur pour séparer les valeurs de propriété dans les chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-143">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="60f62-144">La valeur par défaut est une virgule ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="60f62-144">The default is a comma (`,`).</span></span> <span data-ttu-id="60f62-145">Entrez un caractère, tel qu’un signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="60f62-145">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="60f62-146">Pour spécifier un point-virgule ( `;` ), placez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="60f62-146">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

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

### <span data-ttu-id="60f62-147">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="60f62-147">-IncludeTypeInformation</span></span>

<span data-ttu-id="60f62-148">Lorsque ce paramètre est utilisé, la première ligne de la sortie contient **#TYPE** suivie du nom qualifié complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="60f62-148">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="60f62-149">Par exemple, **#TYPE System. Diagnostics. Process**.</span><span class="sxs-lookup"><span data-stu-id="60f62-149">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="60f62-150">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="60f62-150">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f62-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="60f62-151">-InputObject</span></span>

<span data-ttu-id="60f62-152">Spécifie les objets qui sont convertis en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-152">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="60f62-153">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="60f62-153">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="60f62-154">Vous pouvez également diriger les objets vers `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="60f62-154">You can also pipe objects to `ConvertTo-CSV`.</span></span>

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

### <span data-ttu-id="60f62-155">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="60f62-155">-NoTypeInformation</span></span>

<span data-ttu-id="60f62-156">Supprime l’en-tête d’informations **#TYPE** de la sortie.</span><span class="sxs-lookup"><span data-stu-id="60f62-156">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="60f62-157">Ce paramètre est devenu la valeur par défaut dans PowerShell 6,0 et est inclus à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="60f62-157">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="60f62-158">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="60f62-158">-UseCulture</span></span>

<span data-ttu-id="60f62-159">Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément.</span><span class="sxs-lookup"><span data-stu-id="60f62-159">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="60f62-160">Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="60f62-160">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="60f62-161">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="60f62-161">-QuoteFields</span></span>

<span data-ttu-id="60f62-162">Spécifie les noms des colonnes qui doivent être entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="60f62-162">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="60f62-163">Lorsque ce paramètre est utilisé, seules les colonnes spécifiées sont placées entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="60f62-163">When this parameter is used only the specified columns are quoted.</span></span> <span data-ttu-id="60f62-164">Ce paramètre a été ajouté dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="60f62-164">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f62-165">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="60f62-165">-UseQuotes</span></span>

<span data-ttu-id="60f62-166">Spécifie quand les guillemets sont utilisés dans les fichiers CSV.</span><span class="sxs-lookup"><span data-stu-id="60f62-166">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="60f62-167">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="60f62-167">Possible values are:</span></span>

- <span data-ttu-id="60f62-168">N’effectuez jamais aucune citation</span><span class="sxs-lookup"><span data-stu-id="60f62-168">Never - don't quote anything</span></span>
- <span data-ttu-id="60f62-169">Always-tout (comportement par défaut)</span><span class="sxs-lookup"><span data-stu-id="60f62-169">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="60f62-170">AsNeeded uniquement les champs de guillemets contenant un caractère délimiteur</span><span class="sxs-lookup"><span data-stu-id="60f62-170">AsNeeded - only quote fields that contain a delimiter character</span></span>

<span data-ttu-id="60f62-171">Ce paramètre a été ajouté dans PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="60f62-171">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60f62-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="60f62-172">CommonParameters</span></span>

<span data-ttu-id="60f62-173">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="60f62-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="60f62-174">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="60f62-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="60f62-175">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="60f62-175">INPUTS</span></span>

### <span data-ttu-id="60f62-176">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="60f62-176">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="60f62-177">Vous pouvez diriger n’importe quel objet ayant un adaptateur de système de type étendu (ETS) vers `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="60f62-177">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="60f62-178">SORTIES</span><span class="sxs-lookup"><span data-stu-id="60f62-178">OUTPUTS</span></span>

### <span data-ttu-id="60f62-179">System.String</span><span class="sxs-lookup"><span data-stu-id="60f62-179">System.String</span></span>

<span data-ttu-id="60f62-180">La sortie CSV est renvoyée sous forme d'une collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="60f62-180">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="60f62-181">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="60f62-181">NOTES</span></span>

<span data-ttu-id="60f62-182">Au format CSV, chaque objet est représenté par une liste séparée par des virgules de sa valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="60f62-182">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="60f62-183">Les valeurs de propriété sont converties en chaînes à l’aide de la méthode **ToString ()** de l’objet.</span><span class="sxs-lookup"><span data-stu-id="60f62-183">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="60f62-184">Les chaînes sont représentées par le nom de la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="60f62-184">The strings are represented by the property value name.</span></span> <span data-ttu-id="60f62-185">`ConvertTo-CSV` n’exporte pas les méthodes de l’objet.</span><span class="sxs-lookup"><span data-stu-id="60f62-185">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="60f62-186">Les chaînes CSV sont générées comme suit :</span><span class="sxs-lookup"><span data-stu-id="60f62-186">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="60f62-187">Si **IncludeTypeInformation** est utilisé, la première chaîne se compose de **#TYPE** suivie du nom qualifié complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="60f62-187">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="60f62-188">Par exemple, **#TYPE System. Diagnostics. Process**.</span><span class="sxs-lookup"><span data-stu-id="60f62-188">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="60f62-189">Si **IncludeTypeInformation** n’est pas utilisé, la première chaîne comprend les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="60f62-189">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="60f62-190">Les en-têtes contiennent les noms de propriété du premier objet sous la forme d’une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="60f62-190">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="60f62-191">Les chaînes restantes contiennent des listes séparées par des virgules des valeurs de propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="60f62-191">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="60f62-192">À compter de PowerShell 6,0, le comportement par défaut de `ConvertTo-CSV` est de ne pas inclure les informations de **#TYPE** dans le csv et **NoTypeInformation** est implicite.</span><span class="sxs-lookup"><span data-stu-id="60f62-192">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="60f62-193">**IncludeTypeInformation** peut être utilisé pour inclure les informations **#TYPE** et émuler le comportement par défaut de `ConvertTo-CSV` avant PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="60f62-193">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="60f62-194">Lorsque vous envoyez plusieurs objets à `ConvertTo-CSV` , `ConvertTo-CSV` trie les chaînes en fonction des propriétés du premier objet que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="60f62-194">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="60f62-195">Si les objets restants n’ont pas l’une des propriétés spécifiées, la valeur de propriété de cet objet est null, comme représenté par deux virgules consécutives.</span><span class="sxs-lookup"><span data-stu-id="60f62-195">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="60f62-196">Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="60f62-196">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="60f62-197">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="60f62-197">RELATED LINKS</span></span>

[<span data-ttu-id="60f62-198">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="60f62-198">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="60f62-199">Export-CSV</span><span class="sxs-lookup"><span data-stu-id="60f62-199">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="60f62-200">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="60f62-200">Import-Csv</span></span>](Import-Csv.md)
