---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 9831249a9f1ffcc65fc275e44da04fde9348ae71
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388057"
---
# <span data-ttu-id="7d83c-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="7d83c-103">ConvertTo-Json</span></span>

## <span data-ttu-id="7d83c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7d83c-104">SYNOPSIS</span></span>
<span data-ttu-id="7d83c-105">Convertit un objet en une chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="7d83c-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="7d83c-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="7d83c-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
 [<CommonParameters>]
```

## <span data-ttu-id="7d83c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7d83c-107">DESCRIPTION</span></span>

<span data-ttu-id="7d83c-108">L' `ConvertTo-Json` applet de commande convertit n’importe quel objet .net en une chaîne au format JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="7d83c-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="7d83c-109">Les propriétés sont converties en noms de champs et les valeurs de champ en valeurs de propriété, tandis que les méthodes sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="7d83c-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="7d83c-110">Vous pouvez ensuite utiliser l' `ConvertFrom-Json` applet de commande pour convertir une chaîne au format JSON en un objet JSON, qui est facilement géré dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d83c-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="7d83c-111">De nombreux sites web utilisent JSON au lieu de XML pour sérialiser les données en vue de la communication entre les serveurs et les applications basées sur le web.</span><span class="sxs-lookup"><span data-stu-id="7d83c-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="7d83c-112">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="7d83c-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="7d83c-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7d83c-113">EXAMPLES</span></span>

### <span data-ttu-id="7d83c-114">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="7d83c-114">Example 1</span></span>

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
    "MinSupportedDateTime":  "\/Date(-62135596800000)\/",
    "MaxSupportedDateTime":  "\/Date(253402300799999)\/",
    "AlgorithmType":  1,
    "CalendarType":  1,
    "Eras":  [
                 1
             ],
    "TwoDigitYearMax":  2029,
    "IsReadOnly":  false
}
```

<span data-ttu-id="7d83c-115">Cette commande utilise la `ConvertTo-Json` cmdlet pour convertir un objet GregorianCalendar en chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="7d83c-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="7d83c-116">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="7d83c-116">Example 2</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="7d83c-117">Cette commande montre l’effet de l’utilisation du paramètre **Compress** de `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="7d83c-117">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="7d83c-118">La compression affecte uniquement l'aspect de la chaîne, pas sa validité.</span><span class="sxs-lookup"><span data-stu-id="7d83c-118">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="7d83c-119">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="7d83c-119">Example 3</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
    "DisplayHint":  2,
    "DateTime":  "Friday, January 13, 2012 8:06:16 PM",
    "Date":  "\/Date(1326441600000)\/",
    "Day":  13,
    "DayOfWeek":  5,
    "DayOfYear":  13,
    "Hour":  20,
    "Kind":  2,
    "Millisecond":  221,
    "Minute":  6,
    "Month":  1,
    "Second":  16,
    "Ticks":  634620819762218083,
    "TimeOfDay":  {
                      "Ticks":  723762218083,
                      "Days":  0,
                      "Hours":  20,
                      "Milliseconds":  221,
                      "Minutes":  6,
                      "Seconds":  16,
                      "TotalDays":  0.83768775241087956,
                      "TotalHours":  20.104506057861109,
                      "TotalMilliseconds":  72376221.8083,
                      "TotalMinutes":  1206.2703634716668,
                      "TotalSeconds":  72376.22180829999
                  },
    "Year":  2012
}
```

<span data-ttu-id="7d83c-120">Cet exemple utilise l' `ConvertTo-Json` applet de commande pour convertir un objet **System. DateTime** de l' `Get-Date` applet de commande en chaîne au format JSON.</span><span class="sxs-lookup"><span data-stu-id="7d83c-120">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="7d83c-121">La commande utilise l' `Select-Object` applet de commande pour récupérer tout ( `*` ) des propriétés de l’objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="7d83c-121">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="7d83c-122">La sortie affiche la chaîne JSON `ConvertTo-Json` retournée.</span><span class="sxs-lookup"><span data-stu-id="7d83c-122">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="7d83c-123">Exemple 4</span><span class="sxs-lookup"><span data-stu-id="7d83c-123">Example 4</span></span>

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

<span data-ttu-id="7d83c-124">Cet exemple montre comment utiliser les `ConvertTo-Json` applets de commande et `ConvertFrom-Json` pour convertir un objet en une chaîne JSON et un objet JSON.</span><span class="sxs-lookup"><span data-stu-id="7d83c-124">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="7d83c-125">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="7d83c-125">PARAMETERS</span></span>

### <span data-ttu-id="7d83c-126">-Compresser</span><span class="sxs-lookup"><span data-stu-id="7d83c-126">-Compress</span></span>

<span data-ttu-id="7d83c-127">Omet les espaces blancs et la mise en forme en retrait dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="7d83c-127">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="7d83c-128">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="7d83c-128">-Depth</span></span>

<span data-ttu-id="7d83c-129">Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation JSON.</span><span class="sxs-lookup"><span data-stu-id="7d83c-129">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="7d83c-130">La valeur par défaut est 2.</span><span class="sxs-lookup"><span data-stu-id="7d83c-130">The default value is 2.</span></span>

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

### <span data-ttu-id="7d83c-131">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7d83c-131">-InputObject</span></span>

<span data-ttu-id="7d83c-132">Spécifie les objets à convertir au format JSON.</span><span class="sxs-lookup"><span data-stu-id="7d83c-132">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="7d83c-133">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="7d83c-133">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="7d83c-134">Vous pouvez également diriger un objet vers `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="7d83c-134">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="7d83c-135">Le paramètre **InputObject** est obligatoire, mais sa valeur peut être null ( `$null` ) ou une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="7d83c-135">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="7d83c-136">Lorsque l’objet d’entrée est `$null` , `ConvertTo-Json` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="7d83c-136">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="7d83c-137">Lorsque l’objet d’entrée est une chaîne vide, `ConvertTo-Json` retourne une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="7d83c-137">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="7d83c-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7d83c-138">CommonParameters</span></span>

<span data-ttu-id="7d83c-139">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7d83c-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7d83c-140">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="7d83c-140">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7d83c-141">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7d83c-141">INPUTS</span></span>

### <span data-ttu-id="7d83c-142">System.Object</span><span class="sxs-lookup"><span data-stu-id="7d83c-142">System.Object</span></span>

<span data-ttu-id="7d83c-143">Vous pouvez diriger n’importe quel objet vers `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="7d83c-143">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="7d83c-144">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7d83c-144">OUTPUTS</span></span>

### <span data-ttu-id="7d83c-145">System.String</span><span class="sxs-lookup"><span data-stu-id="7d83c-145">System.String</span></span>

## <span data-ttu-id="7d83c-146">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7d83c-146">NOTES</span></span>

<span data-ttu-id="7d83c-147">L' `ConvertTo-Json` applet de commande est implémentée à l’aide de la [classe JavaScriptSerializer](/dotnet/api/system.web.script.serialization.javascriptserializer).</span><span class="sxs-lookup"><span data-stu-id="7d83c-147">The `ConvertTo-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="7d83c-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7d83c-148">RELATED LINKS</span></span>

<span data-ttu-id="7d83c-149">[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="7d83c-149">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="7d83c-150">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="7d83c-150">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="7d83c-151">Get-Content</span><span class="sxs-lookup"><span data-stu-id="7d83c-151">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="7d83c-152">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="7d83c-152">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="7d83c-153">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="7d83c-153">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="7d83c-154">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="7d83c-154">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
