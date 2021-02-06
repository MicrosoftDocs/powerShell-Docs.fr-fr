---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 525b123d48b0f88ca3eef85a3f95cc303a981ca3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596326"
---
# <span data-ttu-id="38fdc-102">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="38fdc-102">ConvertFrom-Json</span></span>

## <span data-ttu-id="38fdc-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="38fdc-103">SYNOPSIS</span></span>
<span data-ttu-id="38fdc-104">Convertit une chaîne au format JSON en un objet personnalisé ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="38fdc-104">Converts a JSON-formatted string to a custom object or a hash table.</span></span>

## <span data-ttu-id="38fdc-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="38fdc-105">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="38fdc-106">Description</span><span class="sxs-lookup"><span data-stu-id="38fdc-106">DESCRIPTION</span></span>

<span data-ttu-id="38fdc-107">L' `ConvertFrom-Json` applet de commande convertit une chaîne au format JSON (JavaScript Object Notation) en un objet **PSCustomObject** personnalisé qui a une propriété pour chaque champ de la chaîne JSON.</span><span class="sxs-lookup"><span data-stu-id="38fdc-107">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="38fdc-108">JSON est couramment utilisé par les sites web pour fournir une représentation textuelle des objets.</span><span class="sxs-lookup"><span data-stu-id="38fdc-108">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="38fdc-109">La norme JSON n’interdit pas l’utilisation interdite avec un **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="38fdc-109">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="38fdc-110">Par exemple, si la chaîne JSON contient des clés dupliquées, seule la dernière clé est utilisée par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38fdc-110">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="38fdc-111">Consultez les autres exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="38fdc-111">See other examples below.</span></span>

<span data-ttu-id="38fdc-112">Pour générer une chaîne JSON à partir de n’importe quel objet, utilisez l’applet de commande `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="38fdc-112">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="38fdc-113">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="38fdc-113">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="38fdc-114">À partir de PowerShell 6, cette applet de commande prend en charge JSON avec des commentaires.</span><span class="sxs-lookup"><span data-stu-id="38fdc-114">Beginning with PowerShell 6, this cmdlet supports JSON with comments.</span></span> <span data-ttu-id="38fdc-115">Les commentaires acceptés sont démarrés avec deux barres obliques ( `//` ).</span><span class="sxs-lookup"><span data-stu-id="38fdc-115">Accepted comments are started with two forward slashes (`//`).</span></span> <span data-ttu-id="38fdc-116">Le commentaire n’est pas représenté dans les données et peut être écrit dans le fichier sans altérer les données ou lever une erreur comme dans PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="38fdc-116">The comment will not be represented in the data and can be written in the file without corrupting the data or throwing an error as it did in PowerShell 5.1.</span></span>

## <span data-ttu-id="38fdc-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="38fdc-117">EXAMPLES</span></span>

### <span data-ttu-id="38fdc-118">Exemple 1 : convertir un objet DateTime en objet JSON</span><span class="sxs-lookup"><span data-stu-id="38fdc-118">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="38fdc-119">Cette commande utilise les `ConvertTo-Json` applets de commande et `ConvertFrom-Json` pour convertir un objet **DateTime** de l' `Get-Date` applet de commande en un objet JSON, puis en **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="38fdc-119">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

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

<span data-ttu-id="38fdc-120">L’exemple utilise l' `Select-Object` applet de commande pour récupérer toutes les propriétés de l’objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="38fdc-120">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="38fdc-121">Elle utilise l' `ConvertTo-Json` applet de commande pour convertir l’objet **DateTime** en une chaîne formatée en tant qu’objet JSON et l' `ConvertFrom-Json` applet de commande pour convertir la chaîne au format JSON en objet **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="38fdc-121">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="38fdc-122">Exemple 2 : obtenir des chaînes JSON à partir d’un service Web et les convertir en objets PowerShell</span><span class="sxs-lookup"><span data-stu-id="38fdc-122">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="38fdc-123">Cette commande utilise l' `Invoke-WebRequest` applet de commande pour obtenir des chaînes JSON à partir d’un service Web, puis elle utilise l' `ConvertFrom-Json` applet de commande pour convertir le contenu JSON en objets pouvant être gérés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38fdc-123">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="38fdc-124">Vous pouvez également utiliser l' `Invoke-RestMethod` applet de commande, qui convertit automatiquement le contenu JSON en objets.</span><span class="sxs-lookup"><span data-stu-id="38fdc-124">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="38fdc-125">Exemple 3 : convertir une chaîne JSON en un objet personnalisé</span><span class="sxs-lookup"><span data-stu-id="38fdc-125">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="38fdc-126">Cet exemple montre comment utiliser l' `ConvertFrom-Json` applet de commande pour convertir un fichier JSON en un objet personnalisé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38fdc-126">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="38fdc-127">La commande utilise Get-Content applet de commande pour obtenir les chaînes dans un fichier JSON.</span><span class="sxs-lookup"><span data-stu-id="38fdc-127">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="38fdc-128">Elle utilise ensuite l’opérateur de pipeline pour envoyer la chaîne délimitée à l’applet de commande `ConvertFrom-Json` , qui la convertit en objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="38fdc-128">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

### <span data-ttu-id="38fdc-129">Exemple 4 : convertir une chaîne JSON en une table de hachage</span><span class="sxs-lookup"><span data-stu-id="38fdc-129">Example 4: Convert a JSON string to a hash table</span></span>

<span data-ttu-id="38fdc-130">Cette commande montre un exemple dans lequel le `-AsHashtable` commutateur peut surmonter les limitations de la commande.</span><span class="sxs-lookup"><span data-stu-id="38fdc-130">This command shows an example where the `-AsHashtable` switch can overcome limitations of the command.</span></span>

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

<span data-ttu-id="38fdc-131">La chaîne JSON contient deux paires clé-valeur avec des clés qui diffèrent uniquement par la casse.</span><span class="sxs-lookup"><span data-stu-id="38fdc-131">The JSON string contains two key value pairs with keys that differ only in casing.</span></span> <span data-ttu-id="38fdc-132">Sans le commutateur, la commande aurait renvoyé une erreur.</span><span class="sxs-lookup"><span data-stu-id="38fdc-132">Without the switch, the command would have thrown an error.</span></span>

### <span data-ttu-id="38fdc-133">Exemple 5 : aller-retour d’un tableau à un seul élément</span><span class="sxs-lookup"><span data-stu-id="38fdc-133">Example 5: Round-trip a single element array</span></span>

<span data-ttu-id="38fdc-134">Cette commande montre un exemple où le `-NoEnumerate` commutateur est utilisé pour effectuer un aller-retour d’un tableau JSON à élément unique.</span><span class="sxs-lookup"><span data-stu-id="38fdc-134">This command shows an example where the `-NoEnumerate` switch is used to round-trip a single element JSON array.</span></span>

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

<span data-ttu-id="38fdc-135">La chaîne JSON contient un tableau avec un seul élément.</span><span class="sxs-lookup"><span data-stu-id="38fdc-135">The JSON string contains an array with a single element.</span></span> <span data-ttu-id="38fdc-136">Sans le commutateur, la conversion de JSON en PSObject, puis sa reconversion avec la `ConvertTo-Json` commande produit un entier unique.</span><span class="sxs-lookup"><span data-stu-id="38fdc-136">Without the switch, converting the JSON to a PSObject and then converting it back with the `ConvertTo-Json` command results in a single integer.</span></span>

## <span data-ttu-id="38fdc-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38fdc-137">PARAMETERS</span></span>

### <span data-ttu-id="38fdc-138">-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="38fdc-138">-AsHashtable</span></span>

<span data-ttu-id="38fdc-139">Convertit le JSON en un objet de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="38fdc-139">Converts the JSON to a hash table object.</span></span> <span data-ttu-id="38fdc-140">Ce commutateur a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="38fdc-140">This switch was introduced in PowerShell 6.0.</span></span> <span data-ttu-id="38fdc-141">Il existe plusieurs scénarios dans lesquels il peut surmonter certaines limitations de l’applet de commande `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="38fdc-141">There are several scenarios where it can overcome some limitations of the `ConvertFrom-Json` cmdlet.</span></span>

- <span data-ttu-id="38fdc-142">Si le JSON contient une liste avec des clés qui diffèrent uniquement par la casse.</span><span class="sxs-lookup"><span data-stu-id="38fdc-142">If the JSON contains a list with keys that only differ in casing.</span></span> <span data-ttu-id="38fdc-143">Sans le commutateur, ces clés sont considérées comme des clés identiques et, par conséquent, seule la dernière est utilisée.</span><span class="sxs-lookup"><span data-stu-id="38fdc-143">Without the switch, those keys would be seen as identical keys and therefore only the last one would get used.</span></span>
- <span data-ttu-id="38fdc-144">Si le JSON contient une clé qui est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="38fdc-144">If the JSON contains a key that is an empty string.</span></span> <span data-ttu-id="38fdc-145">Sans le commutateur, l’applet de commande génère une erreur, car un `PSCustomObject` n’autorise pas cela, contrairement à une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="38fdc-145">Without the switch, the cmdlet would throw an error since a `PSCustomObject` does not allow for that but a hash table does.</span></span> <span data-ttu-id="38fdc-146">Voici un exemple de cas d’utilisation où cela peut se produire `project.lock.json` : fichiers.</span><span class="sxs-lookup"><span data-stu-id="38fdc-146">An example use case where this can occurs are `project.lock.json` files.</span></span>
- <span data-ttu-id="38fdc-147">Les tables de hachage peuvent être traitées plus rapidement pour certaines structures de données.</span><span class="sxs-lookup"><span data-stu-id="38fdc-147">Hash tables can be processed faster for certain data structures.</span></span>

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

### <span data-ttu-id="38fdc-148">-Profondeur</span><span class="sxs-lookup"><span data-stu-id="38fdc-148">-Depth</span></span>

<span data-ttu-id="38fdc-149">Obtient ou définit la profondeur maximale autorisée par l’entrée JSON.</span><span class="sxs-lookup"><span data-stu-id="38fdc-149">Gets or sets the maximum depth the JSON input is allowed to have.</span></span> <span data-ttu-id="38fdc-150">Par défaut, il s’agit de 1024.</span><span class="sxs-lookup"><span data-stu-id="38fdc-150">By default, it is 1024.</span></span>

<span data-ttu-id="38fdc-151">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="38fdc-151">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="38fdc-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="38fdc-152">-InputObject</span></span>

<span data-ttu-id="38fdc-153">Spécifie les chaînes JSON à convertir en objets JSON.</span><span class="sxs-lookup"><span data-stu-id="38fdc-153">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="38fdc-154">Entrez une variable contenant la chaîne, ou tapez une commande ou une expression qui obtient la chaîne.</span><span class="sxs-lookup"><span data-stu-id="38fdc-154">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="38fdc-155">Vous pouvez également diriger une chaîne vers `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="38fdc-155">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="38fdc-156">Le paramètre **InputObject** est obligatoire, mais sa valeur peut être une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="38fdc-156">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="38fdc-157">Lorsque l’objet d’entrée est une chaîne vide, `ConvertFrom-Json` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="38fdc-157">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="38fdc-158">La valeur **InputObject** ne peut pas être `$null` .</span><span class="sxs-lookup"><span data-stu-id="38fdc-158">The **InputObject** value cannot be `$null`.</span></span>

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

### <span data-ttu-id="38fdc-159">-Noenumerate</span><span class="sxs-lookup"><span data-stu-id="38fdc-159">-NoEnumerate</span></span>

<span data-ttu-id="38fdc-160">Spécifie que la sortie n’est pas énumérée.</span><span class="sxs-lookup"><span data-stu-id="38fdc-160">Specifies that output is not enumerated.</span></span>

<span data-ttu-id="38fdc-161">La définition de ce paramètre entraîne l’envoi de tableaux sous la forme d’un objet unique au lieu d’envoyer chaque élément séparément.</span><span class="sxs-lookup"><span data-stu-id="38fdc-161">Setting this parameter causes arrays to be sent as a single object instead of sending every element separately.</span></span> <span data-ttu-id="38fdc-162">Cela garantit que JSON peut être un aller-retour via `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="38fdc-162">This guarantees that JSON can be round-tripped via `ConvertTo-Json`.</span></span>

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

### <span data-ttu-id="38fdc-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38fdc-163">CommonParameters</span></span>

<span data-ttu-id="38fdc-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38fdc-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38fdc-165">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="38fdc-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="38fdc-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="38fdc-166">INPUTS</span></span>

### <span data-ttu-id="38fdc-167">System.String</span><span class="sxs-lookup"><span data-stu-id="38fdc-167">System.String</span></span>

<span data-ttu-id="38fdc-168">Vous pouvez diriger une chaîne JSON vers `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="38fdc-168">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="38fdc-169">SORTIES</span><span class="sxs-lookup"><span data-stu-id="38fdc-169">OUTPUTS</span></span>

### <span data-ttu-id="38fdc-170">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="38fdc-170">PSCustomObject</span></span>

### <span data-ttu-id="38fdc-171">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="38fdc-171">System.Collections.Hashtable</span></span>

## <span data-ttu-id="38fdc-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="38fdc-172">NOTES</span></span>

<span data-ttu-id="38fdc-173">Cette applet de commande est implémentée à l’aide de [Newtonsoft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="38fdc-173">This cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

<span data-ttu-id="38fdc-174">À compter de PowerShell 6, `ConvertTo-Json` tente de convertir les chaînes mises en forme en horodateur en valeurs **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="38fdc-174">Beginning in PowerShell 6, `ConvertTo-Json` attempts to convert strings formatted as timestamps to **DateTime** values.</span></span> <span data-ttu-id="38fdc-175">La valeur convertie est une `[datetime]` instance avec une `Kind` propriété définie comme suit :</span><span class="sxs-lookup"><span data-stu-id="38fdc-175">The converted value is a `[datetime]` instance with a `Kind` property set as follows:</span></span>

- <span data-ttu-id="38fdc-176">`Unspecified`, s’il n’y a pas d’informations de fuseau horaire dans la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="38fdc-176">`Unspecified`, if there is no time zone information in the input string.</span></span>
- <span data-ttu-id="38fdc-177">`Utc`, si les informations de fuseau horaire sont à la fin `Z` .</span><span class="sxs-lookup"><span data-stu-id="38fdc-177">`Utc`, if the time zone information is a trailing `Z`.</span></span>
- <span data-ttu-id="38fdc-178">`Local`, si les informations de fuseau horaire sont fournies sous la forme d’un _offset_ UTC de fin comme `+02:00` .</span><span class="sxs-lookup"><span data-stu-id="38fdc-178">`Local`, if the time zone information is given as a trailing UTC _offset_ like `+02:00`.</span></span> <span data-ttu-id="38fdc-179">Le décalage est correctement converti dans le fuseau horaire configuré de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="38fdc-179">The offset is properly converted to the caller's configured time zone.</span></span> <span data-ttu-id="38fdc-180">La mise en forme de sortie par défaut n’indique pas le décalage de fuseau horaire d’origine.</span><span class="sxs-lookup"><span data-stu-id="38fdc-180">The default output formatting does not indicate the original time zone offset.</span></span>

## <span data-ttu-id="38fdc-181">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="38fdc-181">RELATED LINKS</span></span>

<span data-ttu-id="38fdc-182">[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="38fdc-182">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="38fdc-183">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="38fdc-183">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="38fdc-184">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="38fdc-184">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="38fdc-185">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="38fdc-185">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
