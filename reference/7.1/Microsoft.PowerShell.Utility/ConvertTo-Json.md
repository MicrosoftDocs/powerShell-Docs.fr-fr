---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: acfeae4025b3a32d2a04307609597cf30332d708
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389451"
---
# <span data-ttu-id="b9aa8-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="b9aa8-103">ConvertTo-Json</span></span>

## <span data-ttu-id="b9aa8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b9aa8-104">SYNOPSIS</span></span>
<span data-ttu-id="b9aa8-105">Convertit un objet en une chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="b9aa8-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b9aa8-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## <span data-ttu-id="b9aa8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b9aa8-107">DESCRIPTION</span></span>

<span data-ttu-id="b9aa8-108">L' `ConvertTo-Json` applet de commande convertit n’importe quel objet .net en une chaîne au format JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="b9aa8-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="b9aa8-109">Les propriétés sont converties en noms de champs et les valeurs de champ en valeurs de propriété, tandis que les méthodes sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="b9aa8-110">Vous pouvez ensuite utiliser l' `ConvertFrom-Json` applet de commande pour convertir une chaîne au format JSON en un objet JSON, qui est facilement géré dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="b9aa8-111">De nombreux sites web utilisent JSON au lieu de XML pour sérialiser les données en vue de la communication entre les serveurs et les applications basées sur le web.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="b9aa8-112">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b9aa8-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b9aa8-113">EXAMPLES</span></span>

### <span data-ttu-id="b9aa8-114">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="b9aa8-114">Example 1</span></span>

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

<span data-ttu-id="b9aa8-115">Cette commande utilise la `ConvertTo-Json` cmdlet pour convertir un objet GregorianCalendar en chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="b9aa8-116">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="b9aa8-116">Example 2</span></span>

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

<span data-ttu-id="b9aa8-117">Cet exemple montre la sortie de l’applet de commande `ConvertTo-Json` avec et sans le paramètre de commutateur **AsArray** .</span><span class="sxs-lookup"><span data-stu-id="b9aa8-117">This example shows the output from `ConvertTo-Json` cmdlet with and without the **AsArray** switch parameter.</span></span> <span data-ttu-id="b9aa8-118">Vous pouvez voir que la deuxième partie de la sortie est incluse entre crochets de tableau.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-118">You can see the second portion of the output is wrapped in array brackets.</span></span>

### <span data-ttu-id="b9aa8-119">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="b9aa8-119">Example 3</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="b9aa8-120">Cette commande montre l’effet de l’utilisation du paramètre **Compress** de `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="b9aa8-120">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="b9aa8-121">La compression affecte uniquement l'aspect de la chaîne, pas sa validité.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-121">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="b9aa8-122">Exemple 4</span><span class="sxs-lookup"><span data-stu-id="b9aa8-122">Example 4</span></span>

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

<span data-ttu-id="b9aa8-123">Cet exemple utilise l' `ConvertTo-Json` applet de commande pour convertir un objet **System. DateTime** de l' `Get-Date` applet de commande en chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-123">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="b9aa8-124">La commande utilise l' `Select-Object` applet de commande pour récupérer tout ( `*` ) des propriétés de l’objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="b9aa8-124">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="b9aa8-125">La sortie affiche la chaîne JSON `ConvertTo-Json` retournée.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-125">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="b9aa8-126">Exemple 5</span><span class="sxs-lookup"><span data-stu-id="b9aa8-126">Example 5</span></span>

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

<span data-ttu-id="b9aa8-127">Cet exemple montre comment utiliser les `ConvertTo-Json` applets de commande et `ConvertFrom-Json` pour convertir un objet en une chaîne JSON et un objet JSON.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-127">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="b9aa8-128">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="b9aa8-128">PARAMETERS</span></span>

### <span data-ttu-id="b9aa8-129">-AsArray</span><span class="sxs-lookup"><span data-stu-id="b9aa8-129">-AsArray</span></span>

<span data-ttu-id="b9aa8-130">Renvoie l’objet entre crochets de tableau, même si l’entrée est un objet unique.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-130">Outputs the object in array brackets, even if the input is a single object.</span></span>

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

### <span data-ttu-id="b9aa8-131">-Compresser</span><span class="sxs-lookup"><span data-stu-id="b9aa8-131">-Compress</span></span>

<span data-ttu-id="b9aa8-132">Omet les espaces blancs et la mise en forme en retrait dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-132">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="b9aa8-133">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="b9aa8-133">-Depth</span></span>

<span data-ttu-id="b9aa8-134">Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation JSON.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-134">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="b9aa8-135">La valeur par défaut est 2.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-135">The default value is 2.</span></span>

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

### <span data-ttu-id="b9aa8-136">-EnumsAsStrings</span><span class="sxs-lookup"><span data-stu-id="b9aa8-136">-EnumsAsStrings</span></span>

<span data-ttu-id="b9aa8-137">Fournit une autre option de sérialisation qui convertit toutes les énumérations en leur représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-137">Provides an alternative serialization option that converts all enumerations to their string representation.</span></span>

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

### <span data-ttu-id="b9aa8-138">-EscapeHandling</span><span class="sxs-lookup"><span data-stu-id="b9aa8-138">-EscapeHandling</span></span>

<span data-ttu-id="b9aa8-139">Contrôle la façon dont certains caractères sont placés dans une séquence d’échappement dans la sortie JSON résultante.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-139">Controls how certain characters are escaped in the resulting JSON output.</span></span> <span data-ttu-id="b9aa8-140">Par défaut, seuls les caractères de contrôle (tels que les sauts de ligne) sont placés dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-140">By default, only control characters (like newline) are escaped.</span></span>

<span data-ttu-id="b9aa8-141">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="b9aa8-141">Acceptable values are:</span></span>

- <span data-ttu-id="b9aa8-142">Les caractères de contrôle par défaut uniquement sont placés dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-142">Default - Only control characters are escaped.</span></span>
- <span data-ttu-id="b9aa8-143">EscapeNonAscii-tous les caractères de contrôle et non-ASCII sont placés dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-143">EscapeNonAscii - All non-ASCII and control characters are escaped.</span></span>
- <span data-ttu-id="b9aa8-144">EscapeHtml-html ( `<` , `>` , `&` , `'` , `"` ) et les caractères de contrôle sont placés dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-144">EscapeHtml - HTML (`<`, `>`, `&`, `'`, `"`) and control characters are escaped.</span></span>

<span data-ttu-id="b9aa8-145">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-145">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="b9aa8-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b9aa8-146">-InputObject</span></span>

<span data-ttu-id="b9aa8-147">Spécifie les objets à convertir au format JSON.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-147">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="b9aa8-148">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="b9aa8-149">Vous pouvez également diriger un objet vers `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="b9aa8-149">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="b9aa8-150">Le paramètre **InputObject** est obligatoire, mais sa valeur peut être null ( `$null` ) ou une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-150">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="b9aa8-151">Lorsque l’objet d’entrée est `$null` , `ConvertTo-Json` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-151">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="b9aa8-152">Lorsque l’objet d’entrée est une chaîne vide, `ConvertTo-Json` retourne une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-152">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="b9aa8-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9aa8-153">CommonParameters</span></span>

<span data-ttu-id="b9aa8-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b9aa8-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b9aa8-155">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b9aa8-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b9aa8-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b9aa8-156">INPUTS</span></span>

### <span data-ttu-id="b9aa8-157">System.Object</span><span class="sxs-lookup"><span data-stu-id="b9aa8-157">System.Object</span></span>

<span data-ttu-id="b9aa8-158">Vous pouvez diriger n’importe quel objet vers `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="b9aa8-158">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="b9aa8-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b9aa8-159">OUTPUTS</span></span>

### <span data-ttu-id="b9aa8-160">System.String</span><span class="sxs-lookup"><span data-stu-id="b9aa8-160">System.String</span></span>

## <span data-ttu-id="b9aa8-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b9aa8-161">NOTES</span></span>

<span data-ttu-id="b9aa8-162">L' `ConvertTo-Json` applet de commande est implémentée à l’aide de [Newtonsoft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="b9aa8-162">The `ConvertTo-Json` cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

## <span data-ttu-id="b9aa8-163">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b9aa8-163">RELATED LINKS</span></span>

<span data-ttu-id="b9aa8-164">[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="b9aa8-164">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="b9aa8-165">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="b9aa8-165">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="b9aa8-166">Get-Content</span><span class="sxs-lookup"><span data-stu-id="b9aa8-166">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="b9aa8-167">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="b9aa8-167">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="b9aa8-168">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="b9aa8-168">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="b9aa8-169">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="b9aa8-169">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="b9aa8-170">NewtonSoft.Js. StringEscapeHandling</span><span class="sxs-lookup"><span data-stu-id="b9aa8-170">NewtonSoft.Json.StringEscapeHandling</span></span>](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
