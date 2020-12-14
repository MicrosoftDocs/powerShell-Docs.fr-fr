---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: cbf87c2a2d6ab0f08e514ba971a622ea9f1904aa
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514933"
---
# <span data-ttu-id="bdc12-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="bdc12-103">Get-Date</span></span>

## <span data-ttu-id="bdc12-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bdc12-104">SYNOPSIS</span></span>
<span data-ttu-id="bdc12-105">Obtient les date et heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="bdc12-105">Gets the current date and time.</span></span>

## <span data-ttu-id="bdc12-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="bdc12-106">SYNTAX</span></span>

### <span data-ttu-id="bdc12-107">NET (par défaut)</span><span class="sxs-lookup"><span data-stu-id="bdc12-107">net (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [<CommonParameters>]
```

### <span data-ttu-id="bdc12-108">UFormat</span><span class="sxs-lookup"><span data-stu-id="bdc12-108">UFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-UFormat <String>] [<CommonParameters>]
```

## <span data-ttu-id="bdc12-109">Description</span><span class="sxs-lookup"><span data-stu-id="bdc12-109">DESCRIPTION</span></span>

<span data-ttu-id="bdc12-110">L' `Get-Date` applet de commande obtient un objet **DateTime** qui représente la date actuelle ou une date que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="bdc12-110">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="bdc12-111">`Get-Date` peut mettre en forme la date et l’heure dans plusieurs formats .NET et UNIX.</span><span class="sxs-lookup"><span data-stu-id="bdc12-111">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="bdc12-112">Vous pouvez utiliser `Get-Date` pour générer une chaîne de caractères de date ou d’heure, puis envoyer la chaîne à d’autres applets de commande ou programmes.</span><span class="sxs-lookup"><span data-stu-id="bdc12-112">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="bdc12-113">`Get-Date` utilise les paramètres de culture de l’ordinateur pour déterminer comment la sortie est mise en forme.</span><span class="sxs-lookup"><span data-stu-id="bdc12-113">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="bdc12-114">Pour afficher les paramètres de votre ordinateur, utilisez `(Get-Culture).DateTimeFormat` .</span><span class="sxs-lookup"><span data-stu-id="bdc12-114">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="bdc12-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bdc12-115">EXAMPLES</span></span>

### <span data-ttu-id="bdc12-116">Exemple 1 : récupération de la date et de l’heure actuelles</span><span class="sxs-lookup"><span data-stu-id="bdc12-116">Example 1: Get the current date and time</span></span>

<span data-ttu-id="bdc12-117">Dans cet exemple, `Get-Date` affiche la date et l’heure système actuelles.</span><span class="sxs-lookup"><span data-stu-id="bdc12-117">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="bdc12-118">La sortie est dans les formats de date longue et d’heure longue.</span><span class="sxs-lookup"><span data-stu-id="bdc12-118">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="bdc12-119">Exemple 2 : obtient les éléments de la date et de l’heure actuelles</span><span class="sxs-lookup"><span data-stu-id="bdc12-119">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="bdc12-120">Cet exemple montre comment utiliser `Get-Date` pour récupérer l’élément de date ou d’heure.</span><span class="sxs-lookup"><span data-stu-id="bdc12-120">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="bdc12-121">Le paramètre utilise les arguments **Date**, **Time** ou **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="bdc12-121">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="bdc12-122">`Get-Date` utilise le paramètre **DisplayHint** avec l’argument **Date** pour récupérer uniquement la date.</span><span class="sxs-lookup"><span data-stu-id="bdc12-122">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="bdc12-123">Exemple 3 : obtenir la date et l’heure avec un spécificateur de format .NET</span><span class="sxs-lookup"><span data-stu-id="bdc12-123">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="bdc12-124">Dans cet exemple, un spécificateur de format .NET est utilisé pour personnaliser le format de la sortie.</span><span class="sxs-lookup"><span data-stu-id="bdc12-124">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="bdc12-125">La sortie est un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="bdc12-125">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="bdc12-126">`Get-Date` utilise le paramètre **format** pour spécifier plusieurs spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="bdc12-126">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="bdc12-127">Les spécificateurs de format .NET utilisés dans cet exemple sont définis comme suit :</span><span class="sxs-lookup"><span data-stu-id="bdc12-127">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="bdc12-128">Spécificateur</span><span class="sxs-lookup"><span data-stu-id="bdc12-128">Specifier</span></span> | <span data-ttu-id="bdc12-129">Définition</span><span class="sxs-lookup"><span data-stu-id="bdc12-129">Definition</span></span> |
| --- | --- |
| `dddd` | <span data-ttu-id="bdc12-130">Jour de la semaine-Nom complet</span><span class="sxs-lookup"><span data-stu-id="bdc12-130">Day of the week - full name</span></span> |
| `MM` | <span data-ttu-id="bdc12-131">Numéro du mois</span><span class="sxs-lookup"><span data-stu-id="bdc12-131">Month number</span></span> |
| `dd` | <span data-ttu-id="bdc12-132">Jour du mois-2 chiffres</span><span class="sxs-lookup"><span data-stu-id="bdc12-132">Day of the month - 2 digits</span></span> |
| `yyyy` | <span data-ttu-id="bdc12-133">Année au format à 4 chiffres</span><span class="sxs-lookup"><span data-stu-id="bdc12-133">Year in 4-digit format</span></span> |
| `HH:mm` | <span data-ttu-id="bdc12-134">Heure au format 24 heures-pas de secondes</span><span class="sxs-lookup"><span data-stu-id="bdc12-134">Time in 24-hour format -no seconds</span></span> |
| `K` | <span data-ttu-id="bdc12-135">Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate)</span><span class="sxs-lookup"><span data-stu-id="bdc12-135">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="bdc12-136">Pour plus d’informations sur les spécificateurs de format .NET, consultez [chaînes de format de date et d’heure personnalisées](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="bdc12-136">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="bdc12-137">Exemple 4 : obtenir la date et l’heure avec un spécificateur UFormat</span><span class="sxs-lookup"><span data-stu-id="bdc12-137">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="bdc12-138">Dans cet exemple, plusieurs spécificateurs de format **UFormat** sont utilisés pour personnaliser le format de la sortie.</span><span class="sxs-lookup"><span data-stu-id="bdc12-138">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="bdc12-139">La sortie est un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="bdc12-139">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="bdc12-140">`Get-Date` utilise le paramètre **UFormat** pour spécifier plusieurs spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="bdc12-140">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="bdc12-141">Les spécificateurs de format **UFormat** utilisés dans cet exemple sont définis comme suit :</span><span class="sxs-lookup"><span data-stu-id="bdc12-141">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="bdc12-142">Spécificateur</span><span class="sxs-lookup"><span data-stu-id="bdc12-142">Specifier</span></span> | <span data-ttu-id="bdc12-143">Définition</span><span class="sxs-lookup"><span data-stu-id="bdc12-143">Definition</span></span> |
| --- | --- |
| `%A` | <span data-ttu-id="bdc12-144">Jour de la semaine-Nom complet</span><span class="sxs-lookup"><span data-stu-id="bdc12-144">Day of the week - full name</span></span> |
| `%m` | <span data-ttu-id="bdc12-145">Numéro du mois</span><span class="sxs-lookup"><span data-stu-id="bdc12-145">Month number</span></span> |
| `%d` | <span data-ttu-id="bdc12-146">Jour du mois-2 chiffres</span><span class="sxs-lookup"><span data-stu-id="bdc12-146">Day of the month - 2 digits</span></span> |
| `%Y` | <span data-ttu-id="bdc12-147">Année au format à 4 chiffres</span><span class="sxs-lookup"><span data-stu-id="bdc12-147">Year in 4-digit format</span></span> |
| `%R` | <span data-ttu-id="bdc12-148">Heure au format 24 heures-pas de secondes</span><span class="sxs-lookup"><span data-stu-id="bdc12-148">Time in 24-hour format -no seconds</span></span> |
| `%Z` | <span data-ttu-id="bdc12-149">Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate)</span><span class="sxs-lookup"><span data-stu-id="bdc12-149">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="bdc12-150">Pour obtenir la liste des spécificateurs de format **UFormat** valides, consultez la section [Remarques](#notes) .</span><span class="sxs-lookup"><span data-stu-id="bdc12-150">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="bdc12-151">Exemple 5 : obtenir le jour d’une date de l’année</span><span class="sxs-lookup"><span data-stu-id="bdc12-151">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="bdc12-152">Dans cet exemple, une propriété est utilisée pour obtenir le nombre de jours de l’année.</span><span class="sxs-lookup"><span data-stu-id="bdc12-152">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="bdc12-153">Le calendrier grégorien contient 365 jours, à l’exception des années bissextiles qui comportent 366 jours.</span><span class="sxs-lookup"><span data-stu-id="bdc12-153">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="bdc12-154">Par exemple, le 31 décembre 2020 est le jour 366.</span><span class="sxs-lookup"><span data-stu-id="bdc12-154">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="bdc12-155">`Get-Date` utilise trois paramètres pour spécifier la date : **année**, **mois** et **jour**.</span><span class="sxs-lookup"><span data-stu-id="bdc12-155">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="bdc12-156">La commande est entourée de parenthèses afin que le résultat soit évalué par la propriété **DayofYear** .</span><span class="sxs-lookup"><span data-stu-id="bdc12-156">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="bdc12-157">Exemple 6 : vérifier si une date est ajustée pour l’heure d’été</span><span class="sxs-lookup"><span data-stu-id="bdc12-157">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="bdc12-158">Cet exemple utilise une méthode booléenne pour vérifier si une date est ajustée par l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="bdc12-158">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="bdc12-159">Une variable, `$DST` stocke le résultat de `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="bdc12-159">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="bdc12-160">`$DST` utilise la méthode **IsDaylightSavingTime** pour tester si la date est ajustée pour l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="bdc12-160">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="bdc12-161">Exemple 7 : convertir l’heure actuelle en heure UTC</span><span class="sxs-lookup"><span data-stu-id="bdc12-161">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="bdc12-162">Dans cet exemple, l’heure actuelle est convertie en heure UTC.</span><span class="sxs-lookup"><span data-stu-id="bdc12-162">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="bdc12-163">L’offset UTC pour les paramètres régionaux du système est utilisé pour convertir l’heure.</span><span class="sxs-lookup"><span data-stu-id="bdc12-163">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="bdc12-164">Un tableau de la section [Remarques](#notes) répertorie les spécificateurs de format **UFormat** valides.</span><span class="sxs-lookup"><span data-stu-id="bdc12-164">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="bdc12-165">`Get-Date` utilise le paramètre **UFormat** avec des spécificateurs de format pour afficher la date et l’heure système actuelles.</span><span class="sxs-lookup"><span data-stu-id="bdc12-165">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="bdc12-166">Le spécificateur de format **% Z** représente l’offset UTC de **-07**.</span><span class="sxs-lookup"><span data-stu-id="bdc12-166">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="bdc12-167">La `$Time` variable stocke la date et l’heure système actuelles.</span><span class="sxs-lookup"><span data-stu-id="bdc12-167">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="bdc12-168">`$Time` utilise la méthode **ToUniversalTime ()** pour convertir l’heure en fonction du décalage UTC de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bdc12-168">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="bdc12-169">Exemple 8 : créer un horodateur</span><span class="sxs-lookup"><span data-stu-id="bdc12-169">Example 8: Create a timestamp</span></span>

<span data-ttu-id="bdc12-170">Dans cet exemple, un spécificateur de format crée un objet de **chaîne** d’horodatage pour un nom de répertoire.</span><span class="sxs-lookup"><span data-stu-id="bdc12-170">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="bdc12-171">L’horodateur contient la date, l’heure et le décalage UTC.</span><span class="sxs-lookup"><span data-stu-id="bdc12-171">The timestamp includes the date, time, and UTC offset.</span></span>

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

<span data-ttu-id="bdc12-172">La `$timestamp` variable stocke les résultats d’une `Get-Date` commande.</span><span class="sxs-lookup"><span data-stu-id="bdc12-172">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="bdc12-173">`Get-Date` utilise le paramètre de **format** avec le spécificateur de format en minuscules `o` pour créer un objet de **chaîne** d’horodatage.</span><span class="sxs-lookup"><span data-stu-id="bdc12-173">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="bdc12-174">L’objet est envoyé dans le pipeline à `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="bdc12-174">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="bdc12-175">Un **scriptblock** contient la `$_` variable qui représente l’objet de pipeline actuel.</span><span class="sxs-lookup"><span data-stu-id="bdc12-175">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="bdc12-176">La chaîne d’horodatage est délimitée par des signes deux-points qui sont remplacés par des points.</span><span class="sxs-lookup"><span data-stu-id="bdc12-176">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="bdc12-177">`New-Item` utilise le paramètre **path** pour spécifier l’emplacement d’un nouveau répertoire.</span><span class="sxs-lookup"><span data-stu-id="bdc12-177">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="bdc12-178">Le chemin d’accès comprend la `$timestamp` variable en tant que nom de répertoire.</span><span class="sxs-lookup"><span data-stu-id="bdc12-178">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="bdc12-179">Le paramètre de **type** spécifie qu’un répertoire est créé.</span><span class="sxs-lookup"><span data-stu-id="bdc12-179">The **Type** parameter specifies that a directory is created.</span></span>

## <span data-ttu-id="bdc12-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bdc12-180">PARAMETERS</span></span>

### <span data-ttu-id="bdc12-181">-Date</span><span class="sxs-lookup"><span data-stu-id="bdc12-181">-Date</span></span>

<span data-ttu-id="bdc12-182">Spécifie une date et une heure.</span><span class="sxs-lookup"><span data-stu-id="bdc12-182">Specifies a date and time.</span></span> <span data-ttu-id="bdc12-183">L’heure est facultative et, si elle n’est pas spécifiée, retourne 00:00:00.</span><span class="sxs-lookup"><span data-stu-id="bdc12-183">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="bdc12-184">Entrez la date et l’heure dans un format standard pour les paramètres régionaux système.</span><span class="sxs-lookup"><span data-stu-id="bdc12-184">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="bdc12-185">Par exemple, en anglais (États-Unis) :</span><span class="sxs-lookup"><span data-stu-id="bdc12-185">For example, in US English:</span></span>

<span data-ttu-id="bdc12-186">`Get-Date -Date "6/25/2019 12:30:22"` retourne mardi 25 juin, 2019 12:30:22</span><span class="sxs-lookup"><span data-stu-id="bdc12-186">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bdc12-187">-Jour</span><span class="sxs-lookup"><span data-stu-id="bdc12-187">-Day</span></span>

<span data-ttu-id="bdc12-188">Spécifie le jour du mois qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="bdc12-188">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="bdc12-189">Entrez une valeur comprise entre 1 et 31.</span><span class="sxs-lookup"><span data-stu-id="bdc12-189">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="bdc12-190">Si la valeur spécifiée est supérieure au nombre de jours d’un mois, PowerShell ajoute le nombre de jours au mois.</span><span class="sxs-lookup"><span data-stu-id="bdc12-190">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="bdc12-191">Par exemple, `Get-Date -Month 2 -Day 31` affiche le **3 mars**, et non le **31 février**.</span><span class="sxs-lookup"><span data-stu-id="bdc12-191">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="bdc12-192">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="bdc12-192">-DisplayHint</span></span>

<span data-ttu-id="bdc12-193">Détermine les éléments de date et d'heure à afficher.</span><span class="sxs-lookup"><span data-stu-id="bdc12-193">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="bdc12-194">Les valeurs acceptées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdc12-194">The accepted values are as follows:</span></span>

- <span data-ttu-id="bdc12-195">**Date**: affiche uniquement la date</span><span class="sxs-lookup"><span data-stu-id="bdc12-195">**Date**: displays only the date</span></span>
- <span data-ttu-id="bdc12-196">**Heure**: affiche uniquement l’heure</span><span class="sxs-lookup"><span data-stu-id="bdc12-196">**Time**: displays only the time</span></span>
- <span data-ttu-id="bdc12-197">**DateTime**: affiche la date et l’heure</span><span class="sxs-lookup"><span data-stu-id="bdc12-197">**DateTime**: displays the date and time</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bdc12-198">-Format</span><span class="sxs-lookup"><span data-stu-id="bdc12-198">-Format</span></span>

<span data-ttu-id="bdc12-199">Affiche la date et l'heure dans le format Microsoft .NET Framework indiqué par le spécificateur de format.</span><span class="sxs-lookup"><span data-stu-id="bdc12-199">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="bdc12-200">Le paramètre **format** génère un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="bdc12-200">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="bdc12-201">Pour obtenir la liste des spécificateurs de format .NET disponibles, consultez [chaînes de format de date et d’heure personnalisées](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="bdc12-201">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="bdc12-202">Lorsque le paramètre **format** est utilisé, `Get-Date` obtient uniquement les propriétés de l’objet **DateTime** nécessaires à l’affichage de la date.</span><span class="sxs-lookup"><span data-stu-id="bdc12-202">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="bdc12-203">Ainsi, certaines propriétés et méthodes des objets **DateTime** ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="bdc12-203">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="bdc12-204">À compter de PowerShell 5,0, vous pouvez utiliser les formats supplémentaires suivants comme valeurs pour le paramètre **format** .</span><span class="sxs-lookup"><span data-stu-id="bdc12-204">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="bdc12-205">**Archivé**.</span><span class="sxs-lookup"><span data-stu-id="bdc12-205">**FileDate**.</span></span> <span data-ttu-id="bdc12-206">Représentation conviviale d’un fichier ou d’un chemin d’accès de la date actuelle en heure locale.</span><span class="sxs-lookup"><span data-stu-id="bdc12-206">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="bdc12-207">Le format est `yyyyMMdd` (respecte la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres et un jour à 2 chiffres).</span><span class="sxs-lookup"><span data-stu-id="bdc12-207">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="bdc12-208">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bdc12-208">For example:</span></span>
  20190627.

- <span data-ttu-id="bdc12-209">**FileDateUniversal**.</span><span class="sxs-lookup"><span data-stu-id="bdc12-209">**FileDateUniversal**.</span></span> <span data-ttu-id="bdc12-210">Représentation conviviale d’un fichier ou d’un chemin d’accès de la date actuelle en temps universel (UTC).</span><span class="sxs-lookup"><span data-stu-id="bdc12-210">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="bdc12-211">Le format est `yyyyMMddZ` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres et la lettre `Z` comme indicateur UTC).</span><span class="sxs-lookup"><span data-stu-id="bdc12-211">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="bdc12-212">Par exemple : 20190627Z.</span><span class="sxs-lookup"><span data-stu-id="bdc12-212">For example: 20190627Z.</span></span>

- <span data-ttu-id="bdc12-213">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="bdc12-213">**FileDateTime**.</span></span> <span data-ttu-id="bdc12-214">Représentation conviviale de fichier ou de chemin d’accès de la date et de l’heure en heure locale, au format 24 heures.</span><span class="sxs-lookup"><span data-stu-id="bdc12-214">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="bdc12-215">Le format est `yyyyMMddTHHmmssffff` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres, la lettre `T` comme séparateur horaire, l’heure à 2 chiffres, la minute à 2 chiffres, la seconde à 2 chiffres et la milliseconde sur 4 chiffres).</span><span class="sxs-lookup"><span data-stu-id="bdc12-215">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="bdc12-216">Par exemple : 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="bdc12-216">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="bdc12-217">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="bdc12-217">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="bdc12-218">Représentation conviviale d’un fichier ou d’un chemin d’accès de la date et de l’heure en temps universel (UTC), au format 24 heures.</span><span class="sxs-lookup"><span data-stu-id="bdc12-218">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="bdc12-219">Le format est `yyyyMMddTHHmmssffffZ` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres, la lettre `T` comme séparateur d’heure, une heure à 2 chiffres, une minute à 2 chiffres, une seconde à 2 chiffres, une milliseconde à 4 chiffres et la lettre `Z` comme indicateur UTC).</span><span class="sxs-lookup"><span data-stu-id="bdc12-219">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="bdc12-220">Par exemple : 20190627T1540500718Z.</span><span class="sxs-lookup"><span data-stu-id="bdc12-220">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: net
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bdc12-221">-Heure</span><span class="sxs-lookup"><span data-stu-id="bdc12-221">-Hour</span></span>

<span data-ttu-id="bdc12-222">Spécifie l'heure qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="bdc12-222">Specifies the hour that is displayed.</span></span> <span data-ttu-id="bdc12-223">Entrez une valeur comprise entre 0 et 23.</span><span class="sxs-lookup"><span data-stu-id="bdc12-223">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="bdc12-224">-Milliseconde</span><span class="sxs-lookup"><span data-stu-id="bdc12-224">-Millisecond</span></span>

<span data-ttu-id="bdc12-225">Spécifie le nombre de millisecondes dans la date.</span><span class="sxs-lookup"><span data-stu-id="bdc12-225">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="bdc12-226">Entrez une valeur comprise entre 0 et 999.</span><span class="sxs-lookup"><span data-stu-id="bdc12-226">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="bdc12-227">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bdc12-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bdc12-228">-Minute</span><span class="sxs-lookup"><span data-stu-id="bdc12-228">-Minute</span></span>

<span data-ttu-id="bdc12-229">Spécifie le nombre de minutes qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="bdc12-229">Specifies the minute that is displayed.</span></span> <span data-ttu-id="bdc12-230">Entrez une valeur comprise entre 0 et 59.</span><span class="sxs-lookup"><span data-stu-id="bdc12-230">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="bdc12-231">-Mois</span><span class="sxs-lookup"><span data-stu-id="bdc12-231">-Month</span></span>

<span data-ttu-id="bdc12-232">Spécifie le mois qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="bdc12-232">Specifies the month that is displayed.</span></span> <span data-ttu-id="bdc12-233">Entrez une valeur comprise entre 1 et 12.</span><span class="sxs-lookup"><span data-stu-id="bdc12-233">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="bdc12-234">-Seconde</span><span class="sxs-lookup"><span data-stu-id="bdc12-234">-Second</span></span>

<span data-ttu-id="bdc12-235">Spécifie le nombre de secondes qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="bdc12-235">Specifies the second that is displayed.</span></span> <span data-ttu-id="bdc12-236">Entrez une valeur comprise entre 0 et 59.</span><span class="sxs-lookup"><span data-stu-id="bdc12-236">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="bdc12-237">-UFormat</span><span class="sxs-lookup"><span data-stu-id="bdc12-237">-UFormat</span></span>

<span data-ttu-id="bdc12-238">Affiche la date et l'heure au format UNIX.</span><span class="sxs-lookup"><span data-stu-id="bdc12-238">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="bdc12-239">Le paramètre **UFormat** génère un objet String.</span><span class="sxs-lookup"><span data-stu-id="bdc12-239">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="bdc12-240">Les spécificateurs **UFormat** sont précédés d’un signe `%` de pourcentage (), par exemple,, `%m` `%d` et `%Y` .</span><span class="sxs-lookup"><span data-stu-id="bdc12-240">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="bdc12-241">La section [Remarques](#notes) contient un tableau de **spécificateurs UFormat** valides.</span><span class="sxs-lookup"><span data-stu-id="bdc12-241">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="bdc12-242">Lorsque le paramètre **UFormat** est utilisé, `Get-Date` obtient uniquement les propriétés de l’objet **DateTime** nécessaires à l’affichage de la date.</span><span class="sxs-lookup"><span data-stu-id="bdc12-242">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="bdc12-243">Ainsi, certaines propriétés et méthodes des objets **DateTime** ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="bdc12-243">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: UFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bdc12-244">-Année</span><span class="sxs-lookup"><span data-stu-id="bdc12-244">-Year</span></span>

<span data-ttu-id="bdc12-245">Spécifie l'année qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="bdc12-245">Specifies the year that is displayed.</span></span> <span data-ttu-id="bdc12-246">Entrez une valeur comprise entre 1 et 9999.</span><span class="sxs-lookup"><span data-stu-id="bdc12-246">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="bdc12-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bdc12-247">CommonParameters</span></span>

<span data-ttu-id="bdc12-248">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bdc12-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bdc12-249">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bdc12-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bdc12-250">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bdc12-250">INPUTS</span></span>

### <span data-ttu-id="bdc12-251">Entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="bdc12-251">Pipeline input</span></span>

<span data-ttu-id="bdc12-252">`Get-Date` accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bdc12-252">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="bdc12-253">Par exemple, `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="bdc12-253">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="bdc12-254">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bdc12-254">OUTPUTS</span></span>

### <span data-ttu-id="bdc12-255">System. DateTime ou System. String</span><span class="sxs-lookup"><span data-stu-id="bdc12-255">System.DateTime or System.String</span></span>

<span data-ttu-id="bdc12-256">`Get-Date` retourne un objet **DateTime** sauf lorsque les paramètres **format** et **UFormat** sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="bdc12-256">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="bdc12-257">Les paramètres **format** ou **UFormat** retournent des objets de **chaîne** .</span><span class="sxs-lookup"><span data-stu-id="bdc12-257">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="bdc12-258">Lorsqu’un objet **DateTime** est envoyé vers le pipeline à une applet de commande, comme `Add-Content` qui attend une entrée de chaîne, PowerShell convertit l’objet en un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="bdc12-258">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="bdc12-259">La méthode `(Get-Date).ToString()` convertit un objet **DateTime** en objet **String** .</span><span class="sxs-lookup"><span data-stu-id="bdc12-259">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="bdc12-260">Pour afficher les propriétés et les méthodes d’un objet, envoyez l’objet vers le dessous du pipeline `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="bdc12-260">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="bdc12-261">Par exemple, `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="bdc12-261">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="bdc12-262">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bdc12-262">NOTES</span></span>

<span data-ttu-id="bdc12-263">Les objets **DateTime** sont dans des formats de date longue et d’heure longue pour les paramètres régionaux système.</span><span class="sxs-lookup"><span data-stu-id="bdc12-263">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="bdc12-264">Les **spécificateurs UFormat** valides sont affichés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="bdc12-264">The valid **UFormat specifiers** are displayed in the following table:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdc12-265">Des spécificateurs **UFormat** supplémentaires sont ajoutés dans les versions plus récentes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bdc12-265">Additional **UFormat** specifiers are added in newer versions of PowerShell.</span></span> <span data-ttu-id="bdc12-266">Par exemple, `%F` a été ajouté dans powershell 6,2, il n’est donc pas disponible dans Windows powershell 5,1 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="bdc12-266">For example, `%F` was added in PowerShell 6.2, so it isn't available in Windows PowerShell 5.1 or older.</span></span> <span data-ttu-id="bdc12-267">Gardez cela à l’esprit lors de l’utilisation de spécificateurs **UFormat** dans des scripts conçus pour être exécutés sur plusieurs versions de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bdc12-267">Keep this in mind when using **UFormat** specifiers in scripts designed to be run on multiple versions of PowerShell.</span></span>

| <span data-ttu-id="bdc12-268">Spécificateur de format</span><span class="sxs-lookup"><span data-stu-id="bdc12-268">Format specifier</span></span> |                                 <span data-ttu-id="bdc12-269">Signification</span><span class="sxs-lookup"><span data-stu-id="bdc12-269">Meaning</span></span>                     |         <span data-ttu-id="bdc12-270">Exemple</span><span class="sxs-lookup"><span data-stu-id="bdc12-270">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="bdc12-271">Jour de la semaine-Nom complet</span><span class="sxs-lookup"><span data-stu-id="bdc12-271">Day of the week - full name</span></span>                                             | <span data-ttu-id="bdc12-272">Lundi</span><span class="sxs-lookup"><span data-stu-id="bdc12-272">Monday</span></span>                   |
| `%a` | <span data-ttu-id="bdc12-273">Jour de la semaine-Nom abrégé</span><span class="sxs-lookup"><span data-stu-id="bdc12-273">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="bdc12-274">Lun</span><span class="sxs-lookup"><span data-stu-id="bdc12-274">Mon</span></span>                      |
| `%B` | <span data-ttu-id="bdc12-275">Nom du mois-complet</span><span class="sxs-lookup"><span data-stu-id="bdc12-275">Month name - full</span></span>                                                       | <span data-ttu-id="bdc12-276">Janvier</span><span class="sxs-lookup"><span data-stu-id="bdc12-276">January</span></span>                  |
| `%b` | <span data-ttu-id="bdc12-277">Nom du mois-abrégé</span><span class="sxs-lookup"><span data-stu-id="bdc12-277">Month name - abbreviated</span></span>                                                | <span data-ttu-id="bdc12-278">Jan</span><span class="sxs-lookup"><span data-stu-id="bdc12-278">Jan</span></span>                      |
| `%C` | <span data-ttu-id="bdc12-279">Siècle</span><span class="sxs-lookup"><span data-stu-id="bdc12-279">Century</span></span>                                                                 | <span data-ttu-id="bdc12-280">20 pour 2019</span><span class="sxs-lookup"><span data-stu-id="bdc12-280">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="bdc12-281">Date et heure-abrégé</span><span class="sxs-lookup"><span data-stu-id="bdc12-281">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="bdc12-282">Jeudi Juin 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="bdc12-282">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="bdc12-283">Date au format mm/jj/aa</span><span class="sxs-lookup"><span data-stu-id="bdc12-283">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="bdc12-284">06/27/19</span><span class="sxs-lookup"><span data-stu-id="bdc12-284">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="bdc12-285">Jour du mois-2 chiffres</span><span class="sxs-lookup"><span data-stu-id="bdc12-285">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="bdc12-286">05</span><span class="sxs-lookup"><span data-stu-id="bdc12-286">05</span></span>                       |
| `%e` | <span data-ttu-id="bdc12-287">Jour du mois-précédé d’un espace si seul un chiffre</span><span class="sxs-lookup"><span data-stu-id="bdc12-287">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="bdc12-288">\<space\>5,5</span><span class="sxs-lookup"><span data-stu-id="bdc12-288">\<space\>5</span></span>               |
| `%G` | <span data-ttu-id="bdc12-289">Identique à « Y »</span><span class="sxs-lookup"><span data-stu-id="bdc12-289">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="bdc12-290">Identique à « y »</span><span class="sxs-lookup"><span data-stu-id="bdc12-290">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="bdc12-291">Heure au format 24 heures</span><span class="sxs-lookup"><span data-stu-id="bdc12-291">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="bdc12-292">17</span><span class="sxs-lookup"><span data-stu-id="bdc12-292">17</span></span>                       |
| `%h` | <span data-ttu-id="bdc12-293">Identique à « b »</span><span class="sxs-lookup"><span data-stu-id="bdc12-293">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="bdc12-294">Heure au format 12 heures</span><span class="sxs-lookup"><span data-stu-id="bdc12-294">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="bdc12-295">05</span><span class="sxs-lookup"><span data-stu-id="bdc12-295">05</span></span>                       |
| `%j` | <span data-ttu-id="bdc12-296">Jour de l’année</span><span class="sxs-lookup"><span data-stu-id="bdc12-296">Day of the year</span></span>                                                         | <span data-ttu-id="bdc12-297">1-366</span><span class="sxs-lookup"><span data-stu-id="bdc12-297">1-366</span></span>                    |
| `%k` | <span data-ttu-id="bdc12-298">Identique à « H »</span><span class="sxs-lookup"><span data-stu-id="bdc12-298">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="bdc12-299">Identique à « I » (I majuscule)</span><span class="sxs-lookup"><span data-stu-id="bdc12-299">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="bdc12-300">05</span><span class="sxs-lookup"><span data-stu-id="bdc12-300">05</span></span>                       |
| `%M` | <span data-ttu-id="bdc12-301">Minutes</span><span class="sxs-lookup"><span data-stu-id="bdc12-301">Minutes</span></span>                                                                 | <span data-ttu-id="bdc12-302">35</span><span class="sxs-lookup"><span data-stu-id="bdc12-302">35</span></span>                       |
| `%m` | <span data-ttu-id="bdc12-303">Numéro du mois</span><span class="sxs-lookup"><span data-stu-id="bdc12-303">Month number</span></span>                                                            | <span data-ttu-id="bdc12-304">06</span><span class="sxs-lookup"><span data-stu-id="bdc12-304">06</span></span>                       |
| `%n` | <span data-ttu-id="bdc12-305">caractère de saut de ligne</span><span class="sxs-lookup"><span data-stu-id="bdc12-305">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="bdc12-306">AM ou PM</span><span class="sxs-lookup"><span data-stu-id="bdc12-306">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="bdc12-307">Heure au format 24 heures-pas de secondes</span><span class="sxs-lookup"><span data-stu-id="bdc12-307">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="bdc12-308">17:45</span><span class="sxs-lookup"><span data-stu-id="bdc12-308">17:45</span></span>                    |
| `%r` | <span data-ttu-id="bdc12-309">Heure au format 12 heures</span><span class="sxs-lookup"><span data-stu-id="bdc12-309">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="bdc12-310">09:15:36</span><span class="sxs-lookup"><span data-stu-id="bdc12-310">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="bdc12-311">Secondes</span><span class="sxs-lookup"><span data-stu-id="bdc12-311">Seconds</span></span>                                                                 | <span data-ttu-id="bdc12-312">05</span><span class="sxs-lookup"><span data-stu-id="bdc12-312">05</span></span>                       |
| `%s` | <span data-ttu-id="bdc12-313">Secondes écoulées depuis le 1er janvier 1970 00:00:00</span><span class="sxs-lookup"><span data-stu-id="bdc12-313">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="bdc12-314">1150451174,95705</span><span class="sxs-lookup"><span data-stu-id="bdc12-314">1150451174.95705</span></span>         |
| `%t` | <span data-ttu-id="bdc12-315">Caractère de tabulation horizontale</span><span class="sxs-lookup"><span data-stu-id="bdc12-315">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="bdc12-316">Heure au format 24 heures</span><span class="sxs-lookup"><span data-stu-id="bdc12-316">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="bdc12-317">17:45:52</span><span class="sxs-lookup"><span data-stu-id="bdc12-317">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="bdc12-318">Identique à « W »</span><span class="sxs-lookup"><span data-stu-id="bdc12-318">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="bdc12-319">Jour de la semaine-numéro</span><span class="sxs-lookup"><span data-stu-id="bdc12-319">Day of the week - number</span></span>                                                | <span data-ttu-id="bdc12-320">Dimanche = 0</span><span class="sxs-lookup"><span data-stu-id="bdc12-320">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="bdc12-321">Semaine de l’année</span><span class="sxs-lookup"><span data-stu-id="bdc12-321">Week of the year</span></span>                                                        | <span data-ttu-id="bdc12-322">01-53</span><span class="sxs-lookup"><span data-stu-id="bdc12-322">01-53</span></span>                    |
| `%w` | <span data-ttu-id="bdc12-323">Identique à « u »</span><span class="sxs-lookup"><span data-stu-id="bdc12-323">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="bdc12-324">Semaine de l’année</span><span class="sxs-lookup"><span data-stu-id="bdc12-324">Week of the year</span></span>                                                        | <span data-ttu-id="bdc12-325">00-52</span><span class="sxs-lookup"><span data-stu-id="bdc12-325">00-52</span></span>                    |
| `%X` | <span data-ttu-id="bdc12-326">Identique à « t »</span><span class="sxs-lookup"><span data-stu-id="bdc12-326">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="bdc12-327">Date au format standard pour les paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="bdc12-327">Date in standard format for locale</span></span>                                      | <span data-ttu-id="bdc12-328">06/27/19 pour l’anglais (États-Unis)</span><span class="sxs-lookup"><span data-stu-id="bdc12-328">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="bdc12-329">Année au format à 4 chiffres</span><span class="sxs-lookup"><span data-stu-id="bdc12-329">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="bdc12-330">2019</span><span class="sxs-lookup"><span data-stu-id="bdc12-330">2019</span></span>                     |
| `%y` | <span data-ttu-id="bdc12-331">Année au format à 2 chiffres</span><span class="sxs-lookup"><span data-stu-id="bdc12-331">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="bdc12-332">19</span><span class="sxs-lookup"><span data-stu-id="bdc12-332">19</span></span>                       |
| `%Z` | <span data-ttu-id="bdc12-333">Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate)</span><span class="sxs-lookup"><span data-stu-id="bdc12-333">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="bdc12-334">-07</span><span class="sxs-lookup"><span data-stu-id="bdc12-334">-07</span></span>                      |

## <span data-ttu-id="bdc12-335">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bdc12-335">RELATED LINKS</span></span>

[<span data-ttu-id="bdc12-336">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="bdc12-336">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="bdc12-337">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="bdc12-337">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="bdc12-338">Get-Member</span><span class="sxs-lookup"><span data-stu-id="bdc12-338">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="bdc12-339">New-Item</span><span class="sxs-lookup"><span data-stu-id="bdc12-339">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="bdc12-340">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="bdc12-340">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="bdc12-341">Set-Date</span><span class="sxs-lookup"><span data-stu-id="bdc12-341">Set-Date</span></span>](Set-Date.md)
