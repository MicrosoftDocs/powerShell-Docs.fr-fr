---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 5de6a3bd28b850d3fc1632e26998986f302b78f8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204701"
---
# <span data-ttu-id="a5a0c-103">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="a5a0c-103">ConvertTo-Csv</span></span>

## <span data-ttu-id="a5a0c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a5a0c-104">SYNOPSIS</span></span>
<span data-ttu-id="a5a0c-105">Convertit des objets .NET en une série de chaînes de valeurs séparées par des caractères (CSV).</span><span class="sxs-lookup"><span data-stu-id="a5a0c-105">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="a5a0c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a5a0c-106">SYNTAX</span></span>

### <span data-ttu-id="a5a0c-107">DelimiterPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a5a0c-107">DelimiterPath (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-IncludeTypeInformation] [-NoTypeInformation]
 [<CommonParameters>]
```

### <span data-ttu-id="a5a0c-108">Délimiteur</span><span class="sxs-lookup"><span data-stu-id="a5a0c-108">Delimiter</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [<CommonParameters>]
```

### <span data-ttu-id="a5a0c-109">UseCulture</span><span class="sxs-lookup"><span data-stu-id="a5a0c-109">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [<CommonParameters>]
```

## <span data-ttu-id="a5a0c-110">Description</span><span class="sxs-lookup"><span data-stu-id="a5a0c-110">DESCRIPTION</span></span>

<span data-ttu-id="a5a0c-111">L' `ConvertTo-CSV` applet de commande retourne une série de chaînes de valeurs séparées par des virgules (CSV) qui représentent les objets que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-111">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="a5a0c-112">Vous pouvez ensuite utiliser l' `ConvertFrom-Csv` applet de commande pour recréer des objets à partir des chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-112">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="a5a0c-113">Les objets convertis à partir de CSV sont des valeurs de chaîne des objets d’origine qui contiennent des valeurs de propriété et aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-113">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="a5a0c-114">Vous pouvez utiliser l' `Export-Csv` applet de commande pour convertir des objets en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-114">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="a5a0c-115">`Export-CSV` est semblable à `ConvertTo-CSV` , à ceci près qu’elle enregistre les chaînes CSV dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-115">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="a5a0c-116">L' `ConvertTo-CSV` applet de commande possède des paramètres pour spécifier un délimiteur autre qu’une virgule ou utiliser la culture actuelle comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-116">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="a5a0c-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a5a0c-117">EXAMPLES</span></span>

### <span data-ttu-id="a5a0c-118">Exemple 1 : convertir un objet au format CSV</span><span class="sxs-lookup"><span data-stu-id="a5a0c-118">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="a5a0c-119">Cet exemple convertit un objet **processus** en une chaîne CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-119">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="a5a0c-120">L' `Get-Process` applet de commande obtient l’objet **processus** et utilise le paramètre **Name** pour spécifier le processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-120">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="a5a0c-121">L’objet processus est envoyé dans le pipeline à l’applet de commande `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="a5a0c-121">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="a5a0c-122">L' `ConvertTo-CSV` applet de commande convertit l’objet en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-122">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="a5a0c-123">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-123">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="a5a0c-124">Exemple 2 : convertir un objet DateTime en CSV</span><span class="sxs-lookup"><span data-stu-id="a5a0c-124">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="a5a0c-125">Cet exemple convertit un objet **DateTime** en une chaîne CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-125">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="a5a0c-126">L' `Get-Date` applet de commande obtient l’objet **DateTime** et l’enregistre dans la `$Date` variable.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-126">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="a5a0c-127">L' `ConvertTo-Csv` applet de commande convertit l’objet **DateTime** en chaînes.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-127">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="a5a0c-128">Le paramètre **InputObject** utilise l’objet **DateTime** stocké dans la `$Date` variable.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-128">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="a5a0c-129">Le paramètre **Delimiter** spécifie un point-virgule pour séparer les valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-129">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="a5a0c-130">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-130">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="a5a0c-131">Exemple 3 : convertir le journal des événements PowerShell au format CSV</span><span class="sxs-lookup"><span data-stu-id="a5a0c-131">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="a5a0c-132">Cet exemple convertit le journal des événements Windows pour PowerShell en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-132">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="a5a0c-133">L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** et affiche le séparateur de liste par défaut de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-133">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="a5a0c-134">L' `Get-WinEvent` applet de commande obtient les objets du journal des événements et utilise le paramètre **logname** pour spécifier le nom du fichier journal.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-134">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="a5a0c-135">Les objets du journal des événements sont envoyés vers l’applet de commande via le pipeline `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="a5a0c-135">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="a5a0c-136">L' `ConvertTo-Csv` applet de commande convertit les objets du journal des événements en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-136">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="a5a0c-137">Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-137">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="a5a0c-138">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-138">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

## <span data-ttu-id="a5a0c-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a5a0c-139">PARAMETERS</span></span>

### <span data-ttu-id="a5a0c-140">-Délimiteur</span><span class="sxs-lookup"><span data-stu-id="a5a0c-140">-Delimiter</span></span>

<span data-ttu-id="a5a0c-141">Spécifie le délimiteur pour séparer les valeurs de propriété dans les chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-141">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="a5a0c-142">La valeur par défaut est une virgule ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="a5a0c-142">The default is a comma (`,`).</span></span> <span data-ttu-id="a5a0c-143">Entrez un caractère, tel qu’un signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="a5a0c-143">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="a5a0c-144">Pour spécifier un point-virgule ( `;` ), placez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-144">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

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

### <span data-ttu-id="a5a0c-145">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="a5a0c-145">-IncludeTypeInformation</span></span>

<span data-ttu-id="a5a0c-146">Lorsque ce paramètre est utilisé, la première ligne de la sortie contient **#TYPE** suivie du nom qualifié complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-146">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="a5a0c-147">Par exemple, **#TYPE System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="a5a0c-147">For example, **#TYPE System.Diagnostics.Process** .</span></span>

<span data-ttu-id="a5a0c-148">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-148">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="a5a0c-149">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a5a0c-149">-InputObject</span></span>

<span data-ttu-id="a5a0c-150">Spécifie les objets qui sont convertis en chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-150">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="a5a0c-151">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-151">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="a5a0c-152">Vous pouvez également diriger les objets vers `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="a5a0c-152">You can also pipe objects to `ConvertTo-CSV`.</span></span>

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

### <span data-ttu-id="a5a0c-153">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="a5a0c-153">-NoTypeInformation</span></span>

<span data-ttu-id="a5a0c-154">Supprime l’en-tête d’informations **#TYPE** de la sortie.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-154">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="a5a0c-155">Ce paramètre est devenu la valeur par défaut dans PowerShell 6,0 et est inclus à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-155">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="a5a0c-156">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="a5a0c-156">-UseCulture</span></span>

<span data-ttu-id="a5a0c-157">Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-157">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="a5a0c-158">Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="a5a0c-158">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="a5a0c-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a5a0c-159">CommonParameters</span></span>

<span data-ttu-id="a5a0c-160">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a5a0c-161">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a5a0c-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a5a0c-162">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a5a0c-162">INPUTS</span></span>

### <span data-ttu-id="a5a0c-163">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="a5a0c-163">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a5a0c-164">Vous pouvez diriger n’importe quel objet ayant un adaptateur de système de type étendu (ETS) vers `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="a5a0c-164">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="a5a0c-165">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a5a0c-165">OUTPUTS</span></span>

### <span data-ttu-id="a5a0c-166">System.String</span><span class="sxs-lookup"><span data-stu-id="a5a0c-166">System.String</span></span>

<span data-ttu-id="a5a0c-167">La sortie CSV est renvoyée sous forme d'une collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-167">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="a5a0c-168">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a5a0c-168">NOTES</span></span>

<span data-ttu-id="a5a0c-169">Au format CSV, chaque objet est représenté par une liste séparée par des virgules de sa valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-169">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="a5a0c-170">Les valeurs de propriété sont converties en chaînes à l’aide de la méthode **ToString ()** de l’objet.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-170">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="a5a0c-171">Les chaînes sont représentées par le nom de la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-171">The strings are represented by the property value name.</span></span> <span data-ttu-id="a5a0c-172">`ConvertTo-CSV` n’exporte pas les méthodes de l’objet.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-172">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="a5a0c-173">Les chaînes CSV sont générées comme suit :</span><span class="sxs-lookup"><span data-stu-id="a5a0c-173">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="a5a0c-174">Si **IncludeTypeInformation** est utilisé, la première chaîne se compose de **#TYPE** suivie du nom qualifié complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-174">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="a5a0c-175">Par exemple, **#TYPE System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="a5a0c-175">For example, **#TYPE System.Diagnostics.Process** .</span></span>
- <span data-ttu-id="a5a0c-176">Si **IncludeTypeInformation** n’est pas utilisé, la première chaîne comprend les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-176">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="a5a0c-177">Les en-têtes contiennent les noms de propriété du premier objet sous la forme d’une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-177">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="a5a0c-178">Les chaînes restantes contiennent des listes séparées par des virgules des valeurs de propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-178">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="a5a0c-179">À compter de PowerShell 6,0, le comportement par défaut de `ConvertTo-CSV` est de ne pas inclure les informations de **#TYPE** dans le csv et **NoTypeInformation** est implicite.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-179">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="a5a0c-180">**IncludeTypeInformation** peut être utilisé pour inclure les informations **#TYPE** et émuler le comportement par défaut de `ConvertTo-CSV` avant PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-180">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="a5a0c-181">Lorsque vous envoyez plusieurs objets à `ConvertTo-CSV` , `ConvertTo-CSV` trie les chaînes en fonction des propriétés du premier objet que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-181">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="a5a0c-182">Si les objets restants n’ont pas l’une des propriétés spécifiées, la valeur de propriété de cet objet est null, comme représenté par deux virgules consécutives.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-182">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="a5a0c-183">Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-183">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="a5a0c-184">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a5a0c-184">RELATED LINKS</span></span>

[<span data-ttu-id="a5a0c-185">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="a5a0c-185">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="a5a0c-186">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="a5a0c-186">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="a5a0c-187">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="a5a0c-187">Import-Csv</span></span>](Import-Csv.md)
