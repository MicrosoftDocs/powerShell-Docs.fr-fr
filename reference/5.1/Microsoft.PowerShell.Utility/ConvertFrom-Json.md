---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: f2159a2de3432aec14fb395b93ed476f349616a8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203358"
---
# <span data-ttu-id="d8c7a-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="d8c7a-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="d8c7a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d8c7a-104">SYNOPSIS</span></span>
<span data-ttu-id="d8c7a-105">Convertit une chaîne au format JSON en objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-105">Converts a JSON-formatted string to a custom object.</span></span>

## <span data-ttu-id="d8c7a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8c7a-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="d8c7a-107">Description</span><span class="sxs-lookup"><span data-stu-id="d8c7a-107">DESCRIPTION</span></span>

<span data-ttu-id="d8c7a-108">L' `ConvertFrom-Json` applet de commande convertit une chaîne au format JSON (JavaScript Object Notation) en un objet **PSCustomObject** personnalisé qui a une propriété pour chaque champ de la chaîne JSON.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="d8c7a-109">JSON est couramment utilisé par les sites web pour fournir une représentation textuelle des objets.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="d8c7a-110">La norme JSON n’interdit pas l’utilisation interdite avec un **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="d8c7a-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject** .</span></span> <span data-ttu-id="d8c7a-111">Par exemple, si la chaîne JSON contient des clés dupliquées, seule la dernière clé est utilisée par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="d8c7a-112">Consultez les autres exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-112">See other examples below.</span></span>

<span data-ttu-id="d8c7a-113">Pour générer une chaîne JSON à partir de n’importe quel objet, utilisez l’applet de commande `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="d8c7a-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="d8c7a-114">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="d8c7a-115">Cette applet de commande ne prend pas en charge JSON avec des commentaires.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-115">This cmdlet doesn't support JSON with comments.</span></span>

## <span data-ttu-id="d8c7a-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d8c7a-116">EXAMPLES</span></span>

### <span data-ttu-id="d8c7a-117">Exemple 1 : convertir un objet DateTime en objet JSON</span><span class="sxs-lookup"><span data-stu-id="d8c7a-117">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="d8c7a-118">Cette commande utilise les `ConvertTo-Json` applets de commande et `ConvertFrom-Json` pour convertir un objet **DateTime** de l' `Get-Date` applet de commande en un objet JSON, puis en **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="d8c7a-118">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject** .</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

<span data-ttu-id="d8c7a-119">L’exemple utilise l' `Select-Object` applet de commande pour récupérer toutes les propriétés de l’objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="d8c7a-119">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="d8c7a-120">Elle utilise l' `ConvertTo-Json` applet de commande pour convertir l’objet **DateTime** en une chaîne formatée en tant qu’objet JSON et l' `ConvertFrom-Json` applet de commande pour convertir la chaîne au format JSON en objet **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="d8c7a-120">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="d8c7a-121">Exemple 2 : obtenir des chaînes JSON à partir d’un service Web et les convertir en objets PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8c7a-121">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="d8c7a-122">Cette commande utilise l' `Invoke-WebRequest` applet de commande pour obtenir des chaînes JSON à partir d’un service Web, puis elle utilise l' `ConvertFrom-Json` applet de commande pour convertir le contenu JSON en objets pouvant être gérés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-122">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="d8c7a-123">Vous pouvez également utiliser l' `Invoke-RestMethod` applet de commande, qui convertit automatiquement le contenu JSON en objets.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-123">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="d8c7a-124">Exemple 3 : convertir une chaîne JSON en un objet personnalisé</span><span class="sxs-lookup"><span data-stu-id="d8c7a-124">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="d8c7a-125">Cet exemple montre comment utiliser l' `ConvertFrom-Json` applet de commande pour convertir un fichier JSON en un objet personnalisé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-125">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="d8c7a-126">La commande utilise Get-Content applet de commande pour obtenir les chaînes dans un fichier JSON.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-126">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="d8c7a-127">Elle utilise ensuite l’opérateur de pipeline pour envoyer la chaîne délimitée à l’applet de commande `ConvertFrom-Json` , qui la convertit en objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-127">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

## <span data-ttu-id="d8c7a-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8c7a-128">PARAMETERS</span></span>

### <span data-ttu-id="d8c7a-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d8c7a-129">-InputObject</span></span>

<span data-ttu-id="d8c7a-130">Spécifie les chaînes JSON à convertir en objets JSON.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-130">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="d8c7a-131">Entrez une variable contenant la chaîne, ou tapez une commande ou une expression qui obtient la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-131">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="d8c7a-132">Vous pouvez également diriger une chaîne vers `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="d8c7a-132">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="d8c7a-133">Le paramètre **InputObject** est obligatoire, mais sa valeur peut être une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-133">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="d8c7a-134">Lorsque l’objet d’entrée est une chaîne vide, `ConvertFrom-Json` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-134">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="d8c7a-135">La valeur **InputObject** ne peut pas être `$null` .</span><span class="sxs-lookup"><span data-stu-id="d8c7a-135">The **InputObject** value cannot be `$null`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8c7a-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8c7a-136">CommonParameters</span></span>

<span data-ttu-id="d8c7a-137">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8c7a-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8c7a-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d8c7a-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8c7a-139">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d8c7a-139">INPUTS</span></span>

### <span data-ttu-id="d8c7a-140">System.String</span><span class="sxs-lookup"><span data-stu-id="d8c7a-140">System.String</span></span>

<span data-ttu-id="d8c7a-141">Vous pouvez diriger une chaîne JSON vers `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="d8c7a-141">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="d8c7a-142">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d8c7a-142">OUTPUTS</span></span>

### <span data-ttu-id="d8c7a-143">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="d8c7a-143">PSCustomObject</span></span>

## <span data-ttu-id="d8c7a-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d8c7a-144">NOTES</span></span>

<span data-ttu-id="d8c7a-145">L' `ConvertFrom-Json` applet de commande est implémentée à l’aide de la [classe JavaScriptSerializer](/dotnet/api/system.web.script.serialization.javascriptserializer).</span><span class="sxs-lookup"><span data-stu-id="d8c7a-145">The `ConvertFrom-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="d8c7a-146">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d8c7a-146">RELATED LINKS</span></span>

<span data-ttu-id="d8c7a-147">[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="d8c7a-147">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="d8c7a-148">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="d8c7a-148">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="d8c7a-149">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="d8c7a-149">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="d8c7a-150">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="d8c7a-150">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
