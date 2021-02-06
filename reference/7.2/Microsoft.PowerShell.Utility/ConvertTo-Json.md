---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: d598fe2b1aefdae046b0f1a0893bf4fc407fa7a7
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "99598573"
---
# <span data-ttu-id="4d48d-102">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="4d48d-102">ConvertTo-Json</span></span>

## <span data-ttu-id="4d48d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4d48d-103">SYNOPSIS</span></span>
<span data-ttu-id="4d48d-104">Convertit un objet en une chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="4d48d-104">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="4d48d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4d48d-105">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## <span data-ttu-id="4d48d-106">Description</span><span class="sxs-lookup"><span data-stu-id="4d48d-106">DESCRIPTION</span></span>

<span data-ttu-id="4d48d-107">L' `ConvertTo-Json` applet de commande convertit n’importe quel objet .net en une chaîne au format JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="4d48d-107">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="4d48d-108">Les propriétés sont converties en noms de champs et les valeurs de champ en valeurs de propriété, tandis que les méthodes sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="4d48d-108">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="4d48d-109">Vous pouvez ensuite utiliser l' `ConvertFrom-Json` applet de commande pour convertir une chaîne au format JSON en un objet JSON, qui est facilement géré dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d48d-109">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="4d48d-110">De nombreux sites web utilisent JSON au lieu de XML pour sérialiser les données en vue de la communication entre les serveurs et les applications basées sur le web.</span><span class="sxs-lookup"><span data-stu-id="4d48d-110">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="4d48d-111">À partir de PowerShell 7,2, `ConvertTo-Json` émet un avertissement si la profondeur de l’objet d’entrée dépasse la profondeur spécifiée pour la commande.</span><span class="sxs-lookup"><span data-stu-id="4d48d-111">As of PowerShell 7.2, `ConvertTo-Json` emits a warning if the depth of the input object exceeds the depth specified for the command.</span></span> <span data-ttu-id="4d48d-112">Cela empêche la perte de données indésirables lors de la conversion d’objets.</span><span class="sxs-lookup"><span data-stu-id="4d48d-112">This prevents unwanted data loss when converting objects.</span></span>

<span data-ttu-id="4d48d-113">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="4d48d-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="4d48d-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4d48d-114">EXAMPLES</span></span>

### <span data-ttu-id="4d48d-115">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="4d48d-115">Example 1</span></span>

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

<span data-ttu-id="4d48d-116">Cette commande utilise la `ConvertTo-Json` cmdlet pour convertir un objet GregorianCalendar en chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="4d48d-116">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="4d48d-117">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="4d48d-117">Example 2</span></span>

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

<span data-ttu-id="4d48d-118">Cet exemple montre la sortie de l’applet de commande `ConvertTo-Json` avec et sans le paramètre de commutateur **AsArray** .</span><span class="sxs-lookup"><span data-stu-id="4d48d-118">This example shows the output from `ConvertTo-Json` cmdlet with and without the **AsArray** switch parameter.</span></span> <span data-ttu-id="4d48d-119">Vous pouvez voir que la deuxième partie de la sortie est incluse entre crochets de tableau.</span><span class="sxs-lookup"><span data-stu-id="4d48d-119">You can see the second portion of the output is wrapped in array brackets.</span></span>

### <span data-ttu-id="4d48d-120">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="4d48d-120">Example 3</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="4d48d-121">Cette commande montre l’effet de l’utilisation du paramètre **Compress** de `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="4d48d-121">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="4d48d-122">La compression affecte uniquement l'aspect de la chaîne, pas sa validité.</span><span class="sxs-lookup"><span data-stu-id="4d48d-122">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="4d48d-123">Exemple 4</span><span class="sxs-lookup"><span data-stu-id="4d48d-123">Example 4</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

<span data-ttu-id="4d48d-124">Cet exemple utilise l' `ConvertTo-Json` applet de commande pour convertir un objet **System. DateTime** de l' `Get-Date` applet de commande en chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="4d48d-124">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="4d48d-125">La commande utilise l' `Select-Object` applet de commande pour récupérer tout ( `*` ) des propriétés de l’objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="4d48d-125">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="4d48d-126">La sortie affiche la chaîne JSON `ConvertTo-Json` retournée.</span><span class="sxs-lookup"><span data-stu-id="4d48d-126">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="4d48d-127">Exemple 5</span><span class="sxs-lookup"><span data-stu-id="4d48d-127">Example 5</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

<span data-ttu-id="4d48d-128">Cet exemple montre comment utiliser les `ConvertTo-Json` applets de commande et `ConvertFrom-Json` pour convertir un objet en une chaîne JSON et un objet JSON.</span><span class="sxs-lookup"><span data-stu-id="4d48d-128">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="4d48d-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4d48d-129">PARAMETERS</span></span>

### <span data-ttu-id="4d48d-130">-AsArray</span><span class="sxs-lookup"><span data-stu-id="4d48d-130">-AsArray</span></span>

<span data-ttu-id="4d48d-131">Renvoie l’objet entre crochets de tableau, même si l’entrée est un objet unique.</span><span class="sxs-lookup"><span data-stu-id="4d48d-131">Outputs the object in array brackets, even if the input is a single object.</span></span>

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

### <span data-ttu-id="4d48d-132">-Compresser</span><span class="sxs-lookup"><span data-stu-id="4d48d-132">-Compress</span></span>

<span data-ttu-id="4d48d-133">Omet les espaces blancs et la mise en forme en retrait dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="4d48d-133">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="4d48d-134">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="4d48d-134">-Depth</span></span>

<span data-ttu-id="4d48d-135">Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation JSON.</span><span class="sxs-lookup"><span data-stu-id="4d48d-135">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="4d48d-136">La valeur par défaut est 2.</span><span class="sxs-lookup"><span data-stu-id="4d48d-136">The default value is 2.</span></span> <span data-ttu-id="4d48d-137">À partir de PowerShell 7,2, `ConvertTo-Json` émet un avertissement si le nombre de niveaux dans un objet d’entrée dépasse ce nombre.</span><span class="sxs-lookup"><span data-stu-id="4d48d-137">As of PowerShell 7.2, `ConvertTo-Json` emits a warning if the number of levels in an input object exceeds this number.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4d48d-138">-EnumsAsStrings</span><span class="sxs-lookup"><span data-stu-id="4d48d-138">-EnumsAsStrings</span></span>

<span data-ttu-id="4d48d-139">Fournit une autre option de sérialisation qui convertit toutes les énumérations en leur représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="4d48d-139">Provides an alternative serialization option that converts all enumerations to their string representation.</span></span>

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

### <span data-ttu-id="4d48d-140">-EscapeHandling</span><span class="sxs-lookup"><span data-stu-id="4d48d-140">-EscapeHandling</span></span>

<span data-ttu-id="4d48d-141">Contrôle la façon dont certains caractères sont placés dans une séquence d’échappement dans la sortie JSON résultante.</span><span class="sxs-lookup"><span data-stu-id="4d48d-141">Controls how certain characters are escaped in the resulting JSON output.</span></span> <span data-ttu-id="4d48d-142">Par défaut, seuls les caractères de contrôle (tels que les sauts de ligne) sont placés dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4d48d-142">By default, only control characters (like newline) are escaped.</span></span>

<span data-ttu-id="4d48d-143">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="4d48d-143">Acceptable values are:</span></span>

- <span data-ttu-id="4d48d-144">Les caractères de contrôle par défaut uniquement sont placés dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4d48d-144">Default - Only control characters are escaped.</span></span>
- <span data-ttu-id="4d48d-145">EscapeNonAscii-tous les caractères de contrôle et non-ASCII sont placés dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4d48d-145">EscapeNonAscii - All non-ASCII and control characters are escaped.</span></span>
- <span data-ttu-id="4d48d-146">EscapeHtml-html ( `<` , `>` , `&` , `'` , `"` ) et les caractères de contrôle sont placés dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4d48d-146">EscapeHtml - HTML (`<`, `>`, `&`, `'`, `"`) and control characters are escaped.</span></span>

<span data-ttu-id="4d48d-147">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="4d48d-147">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4d48d-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4d48d-148">-InputObject</span></span>

<span data-ttu-id="4d48d-149">Spécifie les objets à convertir au format JSON.</span><span class="sxs-lookup"><span data-stu-id="4d48d-149">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="4d48d-150">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="4d48d-150">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="4d48d-151">Vous pouvez également diriger un objet vers `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="4d48d-151">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="4d48d-152">Le paramètre **InputObject** est obligatoire, mais sa valeur peut être null ( `$null` ) ou une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="4d48d-152">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="4d48d-153">Lorsque l’objet d’entrée est `$null` , `ConvertTo-Json` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="4d48d-153">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="4d48d-154">Lorsque l’objet d’entrée est une chaîne vide, `ConvertTo-Json` retourne une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="4d48d-154">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4d48d-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4d48d-155">CommonParameters</span></span>

<span data-ttu-id="4d48d-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4d48d-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4d48d-157">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4d48d-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4d48d-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4d48d-158">INPUTS</span></span>

### <span data-ttu-id="4d48d-159">System.Object</span><span class="sxs-lookup"><span data-stu-id="4d48d-159">System.Object</span></span>

<span data-ttu-id="4d48d-160">Vous pouvez diriger n’importe quel objet vers `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="4d48d-160">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="4d48d-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4d48d-161">OUTPUTS</span></span>

### <span data-ttu-id="4d48d-162">System.String</span><span class="sxs-lookup"><span data-stu-id="4d48d-162">System.String</span></span>

## <span data-ttu-id="4d48d-163">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4d48d-163">NOTES</span></span>

<span data-ttu-id="4d48d-164">L' `ConvertTo-Json` applet de commande est implémentée à l’aide de [Newtonsoft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="4d48d-164">The `ConvertTo-Json` cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

## <span data-ttu-id="4d48d-165">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4d48d-165">RELATED LINKS</span></span>

<span data-ttu-id="4d48d-166">[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="4d48d-166">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="4d48d-167">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="4d48d-167">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="4d48d-168">Get-Content</span><span class="sxs-lookup"><span data-stu-id="4d48d-168">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="4d48d-169">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="4d48d-169">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="4d48d-170">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="4d48d-170">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="4d48d-171">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="4d48d-171">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="4d48d-172">NewtonSoft.Js. StringEscapeHandling</span><span class="sxs-lookup"><span data-stu-id="4d48d-172">NewtonSoft.Json.StringEscapeHandling</span></span>](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
