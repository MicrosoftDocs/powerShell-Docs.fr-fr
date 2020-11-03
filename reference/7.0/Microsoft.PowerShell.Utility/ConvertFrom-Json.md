---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: bddb5b1352f0d28717bb25e6d287989aad7fcad4
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208838"
---
# <span data-ttu-id="fff41-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="fff41-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="fff41-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fff41-104">SYNOPSIS</span></span>
<span data-ttu-id="fff41-105">Convertit une chaîne au format JSON en un objet personnalisé ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="fff41-105">Converts a JSON-formatted string to a custom object or a hash table.</span></span>

## <span data-ttu-id="fff41-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fff41-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="fff41-107">Description</span><span class="sxs-lookup"><span data-stu-id="fff41-107">DESCRIPTION</span></span>

<span data-ttu-id="fff41-108">L' `ConvertFrom-Json` applet de commande convertit une chaîne au format JSON (JavaScript Object Notation) en un objet **PSCustomObject** personnalisé qui a une propriété pour chaque champ de la chaîne JSON.</span><span class="sxs-lookup"><span data-stu-id="fff41-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="fff41-109">JSON est couramment utilisé par les sites web pour fournir une représentation textuelle des objets.</span><span class="sxs-lookup"><span data-stu-id="fff41-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="fff41-110">La norme JSON n’interdit pas l’utilisation interdite avec un **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="fff41-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="fff41-111">Par exemple, si la chaîne JSON contient des clés dupliquées, seule la dernière clé est utilisée par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fff41-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="fff41-112">Consultez les autres exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="fff41-112">See other examples below.</span></span>

<span data-ttu-id="fff41-113">Pour générer une chaîne JSON à partir de n’importe quel objet, utilisez l’applet de commande `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="fff41-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="fff41-114">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fff41-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="fff41-115">À partir de PowerShell 6, cette applet de commande prend en charge JSON avec des commentaires.</span><span class="sxs-lookup"><span data-stu-id="fff41-115">Beginning with PowerShell 6, this cmdlet supports JSON with comments.</span></span> <span data-ttu-id="fff41-116">Les commentaires acceptés sont démarrés avec deux barres obliques ( `//` ).</span><span class="sxs-lookup"><span data-stu-id="fff41-116">Accepted comments are started with two forward slashes (`//`).</span></span> <span data-ttu-id="fff41-117">Le commentaire n’est pas représenté dans les données et peut être écrit dans le fichier sans altérer les données ou lever une erreur comme dans PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="fff41-117">The comment will not be represented in the data and can be written in the file without corrupting the data or throwing an error as it did in PowerShell 5.1.</span></span>

## <span data-ttu-id="fff41-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fff41-118">EXAMPLES</span></span>

### <span data-ttu-id="fff41-119">Exemple 1 : convertir un objet DateTime en objet JSON</span><span class="sxs-lookup"><span data-stu-id="fff41-119">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="fff41-120">Cette commande utilise les `ConvertTo-Json` applets de commande et `ConvertFrom-Json` pour convertir un objet **DateTime** de l' `Get-Date` applet de commande en un objet JSON, puis en **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="fff41-120">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

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

<span data-ttu-id="fff41-121">L’exemple utilise l' `Select-Object` applet de commande pour récupérer toutes les propriétés de l’objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="fff41-121">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="fff41-122">Elle utilise l' `ConvertTo-Json` applet de commande pour convertir l’objet **DateTime** en une chaîne formatée en tant qu’objet JSON et l' `ConvertFrom-Json` applet de commande pour convertir la chaîne au format JSON en objet **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="fff41-122">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="fff41-123">Exemple 2 : obtenir des chaînes JSON à partir d’un service Web et les convertir en objets PowerShell</span><span class="sxs-lookup"><span data-stu-id="fff41-123">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="fff41-124">Cette commande utilise l' `Invoke-WebRequest` applet de commande pour obtenir des chaînes JSON à partir d’un service Web, puis elle utilise l' `ConvertFrom-Json` applet de commande pour convertir le contenu JSON en objets pouvant être gérés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fff41-124">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="fff41-125">Vous pouvez également utiliser l' `Invoke-RestMethod` applet de commande, qui convertit automatiquement le contenu JSON en objets.</span><span class="sxs-lookup"><span data-stu-id="fff41-125">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="fff41-126">Exemple 3 : convertir une chaîne JSON en un objet personnalisé</span><span class="sxs-lookup"><span data-stu-id="fff41-126">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="fff41-127">Cet exemple montre comment utiliser l' `ConvertFrom-Json` applet de commande pour convertir un fichier JSON en un objet personnalisé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fff41-127">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="fff41-128">La commande utilise Get-Content applet de commande pour obtenir les chaînes dans un fichier JSON.</span><span class="sxs-lookup"><span data-stu-id="fff41-128">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="fff41-129">Elle utilise ensuite l’opérateur de pipeline pour envoyer la chaîne délimitée à l’applet de commande `ConvertFrom-Json` , qui la convertit en objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fff41-129">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

### <span data-ttu-id="fff41-130">Exemple 4 : convertir une chaîne JSON en une table de hachage</span><span class="sxs-lookup"><span data-stu-id="fff41-130">Example 4: Convert a JSON string to a hash table</span></span>

<span data-ttu-id="fff41-131">Cette commande montre un exemple dans lequel le `-AsHashtable` commutateur peut surmonter les limitations de la commande.</span><span class="sxs-lookup"><span data-stu-id="fff41-131">This command shows an example where the `-AsHashtable` switch can overcome limitations of the command.</span></span>

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

<span data-ttu-id="fff41-132">La chaîne JSON contient deux paires clé-valeur avec des clés qui diffèrent uniquement par la casse.</span><span class="sxs-lookup"><span data-stu-id="fff41-132">The JSON string contains two key value pairs with keys that differ only in casing.</span></span> <span data-ttu-id="fff41-133">Sans le commutateur, la commande aurait renvoyé une erreur.</span><span class="sxs-lookup"><span data-stu-id="fff41-133">Without the switch, the command would have thrown an error.</span></span>

### <span data-ttu-id="fff41-134">Exemple 5 : aller-retour d’un tableau à un seul élément</span><span class="sxs-lookup"><span data-stu-id="fff41-134">Example 5: Round-trip a single element array</span></span>

<span data-ttu-id="fff41-135">Cette commande montre un exemple où le `-NoEnumerate` commutateur est utilisé pour effectuer un aller-retour d’un tableau JSON à élément unique.</span><span class="sxs-lookup"><span data-stu-id="fff41-135">This command shows an example where the `-NoEnumerate` switch is used to round-trip a single element JSON array.</span></span>

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

<span data-ttu-id="fff41-136">La chaîne JSON contient un tableau avec un seul élément.</span><span class="sxs-lookup"><span data-stu-id="fff41-136">The JSON string contains an array with a single element.</span></span> <span data-ttu-id="fff41-137">Sans le commutateur, la conversion de JSON en PSObject, puis sa reconversion avec la `ConvertTo-Json` commande produit un entier unique.</span><span class="sxs-lookup"><span data-stu-id="fff41-137">Without the switch, converting the JSON to a PSObject and then converting it back with the `ConvertTo-Json` command results in a single integer.</span></span>

## <span data-ttu-id="fff41-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fff41-138">PARAMETERS</span></span>

### <span data-ttu-id="fff41-139">-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="fff41-139">-AsHashtable</span></span>

<span data-ttu-id="fff41-140">Convertit le JSON en un objet de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="fff41-140">Converts the JSON to a hash table object.</span></span> <span data-ttu-id="fff41-141">Ce commutateur a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="fff41-141">This switch was introduced in PowerShell 6.0.</span></span> <span data-ttu-id="fff41-142">Il existe plusieurs scénarios dans lesquels il peut surmonter certaines limitations de l’applet de commande `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="fff41-142">There are several scenarios where it can overcome some limitations of the `ConvertFrom-Json` cmdlet.</span></span>

- <span data-ttu-id="fff41-143">Si le JSON contient une liste avec des clés qui diffèrent uniquement par la casse.</span><span class="sxs-lookup"><span data-stu-id="fff41-143">If the JSON contains a list with keys that only differ in casing.</span></span> <span data-ttu-id="fff41-144">Sans le commutateur, ces clés sont considérées comme des clés identiques et, par conséquent, seule la dernière est utilisée.</span><span class="sxs-lookup"><span data-stu-id="fff41-144">Without the switch, those keys would be seen as identical keys and therefore only the last one would get used.</span></span>
- <span data-ttu-id="fff41-145">Si le JSON contient une clé qui est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="fff41-145">If the JSON contains a key that is an empty string.</span></span> <span data-ttu-id="fff41-146">Sans le commutateur, l’applet de commande génère une erreur, car un `PSCustomObject` n’autorise pas cela, contrairement à une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="fff41-146">Without the switch, the cmdlet would throw an error since a `PSCustomObject` does not allow for that but a hash table does.</span></span> <span data-ttu-id="fff41-147">Voici un exemple de cas d’utilisation où cela peut se produire `project.lock.json` : fichiers.</span><span class="sxs-lookup"><span data-stu-id="fff41-147">An example use case where this can occurs are `project.lock.json` files.</span></span>
- <span data-ttu-id="fff41-148">Les tables de hachage peuvent être traitées plus rapidement pour certaines structures de données.</span><span class="sxs-lookup"><span data-stu-id="fff41-148">Hash tables can be processed faster for certain data structures.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fff41-149">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="fff41-149">-Depth</span></span>

<span data-ttu-id="fff41-150">Obtient ou définit la profondeur maximale autorisée par l’entrée JSON.</span><span class="sxs-lookup"><span data-stu-id="fff41-150">Gets or sets the maximum depth the JSON input is allowed to have.</span></span> <span data-ttu-id="fff41-151">Par défaut, il s’agit de 1024.</span><span class="sxs-lookup"><span data-stu-id="fff41-151">By default, it is 1024.</span></span>

<span data-ttu-id="fff41-152">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="fff41-152">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="fff41-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fff41-153">-InputObject</span></span>

<span data-ttu-id="fff41-154">Spécifie les chaînes JSON à convertir en objets JSON.</span><span class="sxs-lookup"><span data-stu-id="fff41-154">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="fff41-155">Entrez une variable contenant la chaîne, ou tapez une commande ou une expression qui obtient la chaîne.</span><span class="sxs-lookup"><span data-stu-id="fff41-155">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="fff41-156">Vous pouvez également diriger une chaîne vers `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="fff41-156">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="fff41-157">Le paramètre **InputObject** est obligatoire, mais sa valeur peut être une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="fff41-157">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="fff41-158">Lorsque l’objet d’entrée est une chaîne vide, `ConvertFrom-Json` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="fff41-158">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="fff41-159">La valeur **InputObject** ne peut pas être `$null` .</span><span class="sxs-lookup"><span data-stu-id="fff41-159">The **InputObject** value cannot be `$null`.</span></span>

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

### <span data-ttu-id="fff41-160">-Noenumerate</span><span class="sxs-lookup"><span data-stu-id="fff41-160">-NoEnumerate</span></span>

<span data-ttu-id="fff41-161">Spécifie que la sortie n’est pas énumérée.</span><span class="sxs-lookup"><span data-stu-id="fff41-161">Specifies that output is not enumerated.</span></span>

<span data-ttu-id="fff41-162">La définition de ce paramètre entraîne l’envoi de tableaux sous la forme d’un objet unique au lieu d’envoyer chaque élément séparément.</span><span class="sxs-lookup"><span data-stu-id="fff41-162">Setting this parameter causes arrays to be sent as a single object instead of sending every element separately.</span></span> <span data-ttu-id="fff41-163">Cela garantit que JSON peut être un aller-retour via `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="fff41-163">This guarantees that JSON can be round-tripped via `ConvertTo-Json`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fff41-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fff41-164">CommonParameters</span></span>

<span data-ttu-id="fff41-165">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fff41-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fff41-166">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fff41-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fff41-167">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fff41-167">INPUTS</span></span>

### <span data-ttu-id="fff41-168">System.String</span><span class="sxs-lookup"><span data-stu-id="fff41-168">System.String</span></span>

<span data-ttu-id="fff41-169">Vous pouvez diriger une chaîne JSON vers `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="fff41-169">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="fff41-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fff41-170">OUTPUTS</span></span>

### <span data-ttu-id="fff41-171">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="fff41-171">PSCustomObject</span></span>

### <span data-ttu-id="fff41-172">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="fff41-172">System.Collections.Hashtable</span></span>

## <span data-ttu-id="fff41-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fff41-173">NOTES</span></span>

<span data-ttu-id="fff41-174">Cette applet de commande est implémentée à l’aide de [Newtonsoft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="fff41-174">This cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

<span data-ttu-id="fff41-175">À compter de PowerShell 6, `ConvertTo-Json` tente de convertir les chaînes mises en forme en horodateur en valeurs **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="fff41-175">Beginning in PowerShell 6, `ConvertTo-Json` attempts to convert strings formatted as timestamps to **DateTime** values.</span></span> <span data-ttu-id="fff41-176">La valeur convertie est une `[datetime]` instance avec une `Kind` propriété définie comme suit :</span><span class="sxs-lookup"><span data-stu-id="fff41-176">The converted value is a `[datetime]` instance with a `Kind` property set as follows:</span></span>

- <span data-ttu-id="fff41-177">`Unspecified`, s’il n’y a pas d’informations de fuseau horaire dans la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="fff41-177">`Unspecified`, if there is no time zone information in the input string.</span></span>
- <span data-ttu-id="fff41-178">`Utc`, si les informations de fuseau horaire sont à la fin `Z` .</span><span class="sxs-lookup"><span data-stu-id="fff41-178">`Utc`, if the time zone information is a trailing `Z`.</span></span>
- <span data-ttu-id="fff41-179">`Local`, si les informations de fuseau horaire sont fournies sous la forme d’un _offset_ UTC de fin comme `+02:00` .</span><span class="sxs-lookup"><span data-stu-id="fff41-179">`Local`, if the time zone information is given as a trailing UTC _offset_ like `+02:00`.</span></span> <span data-ttu-id="fff41-180">Le décalage est correctement converti dans le fuseau horaire configuré de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="fff41-180">The offset is properly converted to the caller's configured time zone.</span></span> <span data-ttu-id="fff41-181">La mise en forme de sortie par défaut n’indique pas le décalage de fuseau horaire d’origine.</span><span class="sxs-lookup"><span data-stu-id="fff41-181">The default output formatting does not indicate the original time zone offset.</span></span>

## <span data-ttu-id="fff41-182">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fff41-182">RELATED LINKS</span></span>

<span data-ttu-id="fff41-183">[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="fff41-183">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="fff41-184">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="fff41-184">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="fff41-185">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="fff41-185">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="fff41-186">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="fff41-186">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
