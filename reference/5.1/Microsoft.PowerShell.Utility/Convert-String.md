---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203361"
---
# <span data-ttu-id="d76ef-103">Convert-String</span><span class="sxs-lookup"><span data-stu-id="d76ef-103">Convert-String</span></span>

## <span data-ttu-id="d76ef-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d76ef-104">SYNOPSIS</span></span>
<span data-ttu-id="d76ef-105">Met en forme une chaîne pour qu’elle corresponde à des exemples.</span><span class="sxs-lookup"><span data-stu-id="d76ef-105">Formats a string to match examples.</span></span>

## <span data-ttu-id="d76ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d76ef-106">SYNTAX</span></span>

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## <span data-ttu-id="d76ef-107">Description</span><span class="sxs-lookup"><span data-stu-id="d76ef-107">DESCRIPTION</span></span>

<span data-ttu-id="d76ef-108">L’applet de commande **Convert-String** met en forme une chaîne pour qu’elle corresponde au format des exemples.</span><span class="sxs-lookup"><span data-stu-id="d76ef-108">The **Convert-String** cmdlet formats a string to match the format of examples.</span></span>

## <span data-ttu-id="d76ef-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d76ef-109">EXAMPLES</span></span>

### <span data-ttu-id="d76ef-110">Exemple 1 : convertir le format d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="d76ef-110">Example 1: Convert format of a string</span></span>

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

<span data-ttu-id="d76ef-111">La première commande crée un tableau qui contient le prénom et le nom.</span><span class="sxs-lookup"><span data-stu-id="d76ef-111">The first command creates an array that contains first and last names.</span></span>

<span data-ttu-id="d76ef-112">La deuxième commande met en forme les noms en fonction de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d76ef-112">The second command formats the names according to the example.</span></span>
<span data-ttu-id="d76ef-113">Il place le nom en premier dans la sortie, suivi d’un initial.</span><span class="sxs-lookup"><span data-stu-id="d76ef-113">It puts the surname first in the output, followed by an initial.</span></span>

### <span data-ttu-id="d76ef-114">Exemple 2 : simplifier le format d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="d76ef-114">Example 2: Simplify format of a string</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

<span data-ttu-id="d76ef-115">La première commande crée un tableau qui contient les noms First, Middle et Last.</span><span class="sxs-lookup"><span data-stu-id="d76ef-115">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="d76ef-116">Notez que la dernière entrée n’a pas de deuxième prénom.</span><span class="sxs-lookup"><span data-stu-id="d76ef-116">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="d76ef-117">La deuxième commande met en forme les noms en fonction de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d76ef-117">The second command formats the names according to the example.</span></span>
<span data-ttu-id="d76ef-118">Il place le nom de famille en premier dans la sortie, suivi du prénom.</span><span class="sxs-lookup"><span data-stu-id="d76ef-118">It puts the last name first in the output, followed by the first name.</span></span>
<span data-ttu-id="d76ef-119">Tous les noms de milieu supprimés ; l’entrée sans le deuxième nom est gérée correctement.</span><span class="sxs-lookup"><span data-stu-id="d76ef-119">All middle names removed; entry without middle name is handled correctly.</span></span>

### <span data-ttu-id="d76ef-120">Exemple 3 : gestion de la sortie quand les chaînes ne correspondent pas à l’exemple</span><span class="sxs-lookup"><span data-stu-id="d76ef-120">Example 3: Output management when strings don't match example</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

<span data-ttu-id="d76ef-121">La première commande crée un tableau qui contient les noms First, Middle et Last.</span><span class="sxs-lookup"><span data-stu-id="d76ef-121">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="d76ef-122">Notez que la dernière entrée n’a pas de deuxième prénom.</span><span class="sxs-lookup"><span data-stu-id="d76ef-122">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="d76ef-123">La deuxième commande met en forme les noms en fonction de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d76ef-123">The second command formats the names according to the example.</span></span>
<span data-ttu-id="d76ef-124">Il place le **deuxième** prénom dans la sortie, suivi du prénom.</span><span class="sxs-lookup"><span data-stu-id="d76ef-124">It puts the **middle name** first in the output, followed by the first name.</span></span>
<span data-ttu-id="d76ef-125">La dernière entrée dans **$Composers** est ignorée, car elle ne correspond pas à l’exemple de modèle : elle n’a pas de deuxième prénom.</span><span class="sxs-lookup"><span data-stu-id="d76ef-125">The last entry in **$Composers** is skipped, because it doesn't match the sample pattern: it has no middle name.</span></span>

### <span data-ttu-id="d76ef-126">Exemple 4 : prudence avec les espaces de beauté</span><span class="sxs-lookup"><span data-stu-id="d76ef-126">Example 4: Caution with beauty spaces</span></span>

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

<span data-ttu-id="d76ef-127">La première commande crée un tableau de nom et prénom.</span><span class="sxs-lookup"><span data-stu-id="d76ef-127">The first command creates an array of first and last names.</span></span>
<span data-ttu-id="d76ef-128">Notez que les deuxième et quatrième éléments comportent un espace de fin supplémentaire, après le nom de famille.</span><span class="sxs-lookup"><span data-stu-id="d76ef-128">Note that second and fourth items have an extra trailing space, after the last name.</span></span>

<span data-ttu-id="d76ef-129">La deuxième commande convertit toutes les chaînes qui correspondent à l’exemple de modèle : _mot, espace, mot et espace de fin final_ , tout ce qui précède le signe égal.</span><span class="sxs-lookup"><span data-stu-id="d76ef-129">The second command converts all strings that match the sample pattern: _word, space, word, and final trailing space_ , all of this before the equal sign.</span></span>
<span data-ttu-id="d76ef-130">Notez également l’espace de début dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="d76ef-130">Also, note the leading space in the output.</span></span>

### <span data-ttu-id="d76ef-131">Exemple 5 : mettre en forme les informations de processus avec plusieurs modèles</span><span class="sxs-lookup"><span data-stu-id="d76ef-131">Example 5: Format process information with multiple patterns</span></span>

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

<span data-ttu-id="d76ef-132">**$ExamplePatterns** définit différents modèles attendus dans les données, par le biais d’exemples.</span><span class="sxs-lookup"><span data-stu-id="d76ef-132">**$ExamplePatterns** defines different expected patterns in the data, through examples.</span></span>

<span data-ttu-id="d76ef-133">Le premier modèle, `@{before='"Hello","World"'; after='World: Hello'}` , lit comme suit : _attend des chaînes où un mot est placé entre guillemets doubles, puis une virgule,_ puis 
 _le deuxième et le dernier mot entre guillemets._ 
 _sans espace dans la chaîne. Sur la sortie : Placez le deuxième mot en premier,_ 
 _sans guillemets, puis un espace, puis le premier mot, sans guillemets._</span><span class="sxs-lookup"><span data-stu-id="d76ef-133">The first pattern, `@{before='"Hello","World"'; after='World: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then the second, and last, word enclosed in quotes;_
_with no spaces in the string. On the output: place second word first,_
_without quotes, then a single space, and then the first word, without quotes._</span></span>

<span data-ttu-id="d76ef-134">Le deuxième modèle, `@{before='"Hello","1"'; after='1: Hello'}` , lit comme suit : _attend des chaînes où un mot est placé entre guillemets doubles, puis une virgule_ 
 _et un nombre entre guillemets._ 
 _sans espace dans la chaîne. Sur la sortie : Placez le nombre en premier,_ 
 _sans guillemets, puis un espace, puis le mot, sans guillemets._</span><span class="sxs-lookup"><span data-stu-id="d76ef-134">The second pattern, `@{before='"Hello","1"'; after='1: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then a number enclosed in quotes;_
_with no spaces in the string. On the output: place the number first,_
_without quotes, then a single space, and then the word, without quotes._</span></span>

<span data-ttu-id="d76ef-135">Le troisième modèle, `@{before='"Hello-World","22"'; after='22: Hello-World'}` , lit comme suit : _attend des chaînes où deux mots avec un trait d’Union entre parenthèses sont placés_ entre guillemets 
 _doubles, puis une virgule et un nombre entre guillemets._ 
 sans _espace entre la virgule et le troisième guillemet double._ 
 _Sur la sortie : Placez le nombre en premier, sans guillemets, puis un espace,_ 
 puis _les mots avec trait d’Union, sans guillemets._</span><span class="sxs-lookup"><span data-stu-id="d76ef-135">The third pattern, `@{before='"Hello-World","22"'; after='22: Hello-World'}`, reads as follows: _expect strings where two words with a hyphen in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the hyphenated words, without quotes._</span></span>

<span data-ttu-id="d76ef-136">Le quatrième et dernier modèle, `@{before='"hello world","333"'; after='333: hello world'}` , lit comme suit : attend des _chaînes où deux mots avec un espace entre parenthèses sont placés entre_ guillemets 
 _doubles, puis une virgule et un nombre entre guillemets._ 
 sans _espace entre la virgule et le troisième guillemet double._ 
 _Sur la sortie : Placez le nombre en premier, sans guillemets, puis un espace,_ 
 puis _les mots avec l’espace entre, sans guillemets._</span><span class="sxs-lookup"><span data-stu-id="d76ef-136">The fourth, and final, pattern, `@{before='"hello world","333"'; after='333: hello world'}`, reads as follows: _expect strings where two words with a space in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the words with the space in between, without quotes._</span></span>

<span data-ttu-id="d76ef-137">La première commande récupère tous les processus à l’aide de l’applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="d76ef-137">The first command gets all processes by using the Get-Process cmdlet.</span></span>
<span data-ttu-id="d76ef-138">La commande les transmet à l’applet de commande Select-Object, qui sélectionne le nom de processus et l’ID de processus.</span><span class="sxs-lookup"><span data-stu-id="d76ef-138">The command passes them to the Select-Object cmdlet, which selects the process name and process ID.</span></span> <span data-ttu-id="d76ef-139">À la fin du pipeline, la commande convertit la sortie en valeurs séparées par des virgules, sans informations de type, à l’aide de l’applet de commande ConvertTo-Csv.</span><span class="sxs-lookup"><span data-stu-id="d76ef-139">At the end of the pipeline, the command converts the output to comma separated values, without type information, by using the ConvertTo-Csv cmdlet.</span></span>
<span data-ttu-id="d76ef-140">La commande stocke les résultats dans la variable **$Processes** .</span><span class="sxs-lookup"><span data-stu-id="d76ef-140">The command stores the results in the **$Processes** variable.</span></span>
<span data-ttu-id="d76ef-141">**$Processes** contient maintenant des noms de processus et un PID.</span><span class="sxs-lookup"><span data-stu-id="d76ef-141">**$Processes** now contains process names and PID.</span></span>

<span data-ttu-id="d76ef-142">La deuxième commande spécifie un exemple de variable qui modifie l’ordre des éléments d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d76ef-142">The second command specifies an example variable that changes the order of the input items.</span></span>
<span data-ttu-id="d76ef-143">La commande covertit chaque chaîne dans **$Processes** .</span><span class="sxs-lookup"><span data-stu-id="d76ef-143">The command coverts each string in **$Processes** .</span></span>

><span data-ttu-id="d76ef-144">**Remarque** Le quatrième modèle dit implicitement que deux mots ou plus séparés par des espaces sont mis en correspondance.</span><span class="sxs-lookup"><span data-stu-id="d76ef-144">**Note** The fourth pattern implicitly says that two or more words separated by spaces are matched.</span></span>
>
><span data-ttu-id="d76ef-145">Sans le quatrième modèle, seul le premier mot de la chaîne placée entre guillemets doubles est mis en correspondance.</span><span class="sxs-lookup"><span data-stu-id="d76ef-145">Without the fourth pattern, only the first word of the string enclosed in double quotes is matched.</span></span>

## <span data-ttu-id="d76ef-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d76ef-146">PARAMETERS</span></span>

### <span data-ttu-id="d76ef-147">-Exemple</span><span class="sxs-lookup"><span data-stu-id="d76ef-147">-Example</span></span>

<span data-ttu-id="d76ef-148">Spécifie une liste d’exemples du format cible.</span><span class="sxs-lookup"><span data-stu-id="d76ef-148">Specifies a list of examples of the target format.</span></span>
<span data-ttu-id="d76ef-149">Spécifiez des paires séparées par le signe égal (=), avec le modèle source sur la gauche et le modèle cible à droite, comme dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="d76ef-149">Specify pairs separated by the equal (=) sign, with the source pattern on the left and the target pattern on the right, as in the following examples:</span></span>

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

><span data-ttu-id="d76ef-150">**Remarque** Le deuxième exemple utilise une liste de modèles</span><span class="sxs-lookup"><span data-stu-id="d76ef-150">**Note** The second example uses a list of patterns</span></span>

<span data-ttu-id="d76ef-151">Vous pouvez également spécifier une liste de tables de hachage qui contiennent les propriétés **Before** et **after** .</span><span class="sxs-lookup"><span data-stu-id="d76ef-151">Alternatively, specify a list of hash tables that contain **Before** and **After** properties.</span></span>

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

><span data-ttu-id="d76ef-152">**Attention** Évitez d’utiliser des espaces autour du signe égal, car ils sont traités comme faisant partie du modèle.</span><span class="sxs-lookup"><span data-stu-id="d76ef-152">**Caution** Avoid using spaces around the equal sign, as they are treated as part of the pattern.</span></span>

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d76ef-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d76ef-153">-InputObject</span></span>

<span data-ttu-id="d76ef-154">Spécifie une chaîne à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="d76ef-154">Specifies a string to format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d76ef-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d76ef-155">CommonParameters</span></span>

<span data-ttu-id="d76ef-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d76ef-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d76ef-157">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d76ef-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d76ef-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d76ef-158">INPUTS</span></span>

### <span data-ttu-id="d76ef-159">String</span><span class="sxs-lookup"><span data-stu-id="d76ef-159">String</span></span>

<span data-ttu-id="d76ef-160">Vous pouvez diriger les chaînes vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d76ef-160">You can pipe strings to this cmdlet.</span></span>

## <span data-ttu-id="d76ef-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d76ef-161">OUTPUTS</span></span>

### <span data-ttu-id="d76ef-162">String</span><span class="sxs-lookup"><span data-stu-id="d76ef-162">String</span></span>

<span data-ttu-id="d76ef-163">Cette applet de commande retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d76ef-163">This cmdlet returns a string.</span></span>

## <span data-ttu-id="d76ef-164">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d76ef-164">NOTES</span></span>

## <span data-ttu-id="d76ef-165">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d76ef-165">RELATED LINKS</span></span>

[<span data-ttu-id="d76ef-166">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="d76ef-166">ConvertFrom-String</span></span>](ConvertFrom-String.md)

[<span data-ttu-id="d76ef-167">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="d76ef-167">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="d76ef-168">Get-Process</span><span class="sxs-lookup"><span data-stu-id="d76ef-168">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="d76ef-169">Out-String</span><span class="sxs-lookup"><span data-stu-id="d76ef-169">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="d76ef-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="d76ef-170">Select-Object</span></span>](Select-Object.md)
