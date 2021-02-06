---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 8c0a1b7a14f5dfa071a85808f5d7dfba4d06048e
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "99598771"
---
# <span data-ttu-id="80817-102">Get-Date</span><span class="sxs-lookup"><span data-stu-id="80817-102">Get-Date</span></span>

## <span data-ttu-id="80817-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="80817-103">SYNOPSIS</span></span>
<span data-ttu-id="80817-104">Obtient les date et heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="80817-104">Gets the current date and time.</span></span>

## <span data-ttu-id="80817-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="80817-105">SYNTAX</span></span>

### <span data-ttu-id="80817-106">Date (par défaut)</span><span class="sxs-lookup"><span data-stu-id="80817-106">Date (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="80817-107">DateUFormat</span><span class="sxs-lookup"><span data-stu-id="80817-107">DateUFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### <span data-ttu-id="80817-108">UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="80817-108">UnixTimeSeconds</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="80817-109">UnixTimeSecondsUFormat</span><span class="sxs-lookup"><span data-stu-id="80817-109">UnixTimeSecondsUFormat</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## <span data-ttu-id="80817-110">Description</span><span class="sxs-lookup"><span data-stu-id="80817-110">DESCRIPTION</span></span>

<span data-ttu-id="80817-111">L' `Get-Date` applet de commande obtient un objet **DateTime** qui représente la date actuelle ou une date que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="80817-111">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="80817-112">`Get-Date` peut mettre en forme la date et l’heure dans plusieurs formats .NET et UNIX.</span><span class="sxs-lookup"><span data-stu-id="80817-112">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="80817-113">Vous pouvez utiliser `Get-Date` pour générer une chaîne de caractères de date ou d’heure, puis envoyer la chaîne à d’autres applets de commande ou programmes.</span><span class="sxs-lookup"><span data-stu-id="80817-113">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="80817-114">`Get-Date` utilise les paramètres de culture de l’ordinateur pour déterminer comment la sortie est mise en forme.</span><span class="sxs-lookup"><span data-stu-id="80817-114">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="80817-115">Pour afficher les paramètres de votre ordinateur, utilisez `(Get-Culture).DateTimeFormat` .</span><span class="sxs-lookup"><span data-stu-id="80817-115">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="80817-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="80817-116">EXAMPLES</span></span>

### <span data-ttu-id="80817-117">Exemple 1 : récupération de la date et de l’heure actuelles</span><span class="sxs-lookup"><span data-stu-id="80817-117">Example 1: Get the current date and time</span></span>

<span data-ttu-id="80817-118">Dans cet exemple, `Get-Date` affiche la date et l’heure système actuelles.</span><span class="sxs-lookup"><span data-stu-id="80817-118">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="80817-119">La sortie est dans les formats de date longue et d’heure longue.</span><span class="sxs-lookup"><span data-stu-id="80817-119">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="80817-120">Exemple 2 : obtient les éléments de la date et de l’heure actuelles</span><span class="sxs-lookup"><span data-stu-id="80817-120">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="80817-121">Cet exemple montre comment utiliser `Get-Date` pour récupérer l’élément de date ou d’heure.</span><span class="sxs-lookup"><span data-stu-id="80817-121">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="80817-122">Le paramètre utilise les arguments **Date**, **Time** ou **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="80817-122">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="80817-123">`Get-Date` utilise le paramètre **DisplayHint** avec l’argument **Date** pour récupérer uniquement la date.</span><span class="sxs-lookup"><span data-stu-id="80817-123">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="80817-124">Exemple 3 : obtenir la date et l’heure avec un spécificateur de format .NET</span><span class="sxs-lookup"><span data-stu-id="80817-124">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="80817-125">Dans cet exemple, un spécificateur de format .NET est utilisé pour personnaliser le format de la sortie.</span><span class="sxs-lookup"><span data-stu-id="80817-125">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="80817-126">La sortie est un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="80817-126">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="80817-127">`Get-Date` utilise le paramètre **format** pour spécifier plusieurs spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="80817-127">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="80817-128">Les spécificateurs de format .NET utilisés dans cet exemple sont définis comme suit :</span><span class="sxs-lookup"><span data-stu-id="80817-128">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="80817-129">Spécificateur</span><span class="sxs-lookup"><span data-stu-id="80817-129">Specifier</span></span> |                      <span data-ttu-id="80817-130">Définition</span><span class="sxs-lookup"><span data-stu-id="80817-130">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | <span data-ttu-id="80817-131">Jour de la semaine-Nom complet</span><span class="sxs-lookup"><span data-stu-id="80817-131">Day of the week - full name</span></span>                           |
| `MM`      | <span data-ttu-id="80817-132">Numéro du mois</span><span class="sxs-lookup"><span data-stu-id="80817-132">Month number</span></span>                                          |
| `dd`      | <span data-ttu-id="80817-133">Jour du mois-2 chiffres</span><span class="sxs-lookup"><span data-stu-id="80817-133">Day of the month - 2 digits</span></span>                           |
| `yyyy`    | <span data-ttu-id="80817-134">Année au format à 4 chiffres</span><span class="sxs-lookup"><span data-stu-id="80817-134">Year in 4-digit format</span></span>                                |
| `HH:mm`   | <span data-ttu-id="80817-135">Heure au format 24 heures-pas de secondes</span><span class="sxs-lookup"><span data-stu-id="80817-135">Time in 24-hour format - no seconds</span></span>                    |
| `K`       | <span data-ttu-id="80817-136">Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate)</span><span class="sxs-lookup"><span data-stu-id="80817-136">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="80817-137">Pour plus d’informations sur les spécificateurs de format .NET, consultez [chaînes de format de date et d’heure personnalisées](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="80817-137">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="80817-138">Exemple 4 : obtenir la date et l’heure avec un spécificateur UFormat</span><span class="sxs-lookup"><span data-stu-id="80817-138">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="80817-139">Dans cet exemple, plusieurs spécificateurs de format **UFormat** sont utilisés pour personnaliser le format de la sortie.</span><span class="sxs-lookup"><span data-stu-id="80817-139">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="80817-140">La sortie est un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="80817-140">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="80817-141">`Get-Date` utilise le paramètre **UFormat** pour spécifier plusieurs spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="80817-141">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="80817-142">Les spécificateurs de format **UFormat** utilisés dans cet exemple sont définis comme suit :</span><span class="sxs-lookup"><span data-stu-id="80817-142">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="80817-143">Spécificateur</span><span class="sxs-lookup"><span data-stu-id="80817-143">Specifier</span></span> |                      <span data-ttu-id="80817-144">Définition</span><span class="sxs-lookup"><span data-stu-id="80817-144">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `%A`      | <span data-ttu-id="80817-145">Jour de la semaine-Nom complet</span><span class="sxs-lookup"><span data-stu-id="80817-145">Day of the week - full name</span></span>                           |
| `%m`      | <span data-ttu-id="80817-146">Numéro du mois</span><span class="sxs-lookup"><span data-stu-id="80817-146">Month number</span></span>                                          |
| `%d`      | <span data-ttu-id="80817-147">Jour du mois-2 chiffres</span><span class="sxs-lookup"><span data-stu-id="80817-147">Day of the month - 2 digits</span></span>                           |
| `%Y`      | <span data-ttu-id="80817-148">Année au format à 4 chiffres</span><span class="sxs-lookup"><span data-stu-id="80817-148">Year in 4-digit format</span></span>                                |
| `%R`      | <span data-ttu-id="80817-149">Heure au format 24 heures-pas de secondes</span><span class="sxs-lookup"><span data-stu-id="80817-149">Time in 24-hour format - no seconds</span></span>                    |
| `%Z`      | <span data-ttu-id="80817-150">Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate)</span><span class="sxs-lookup"><span data-stu-id="80817-150">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="80817-151">Pour obtenir la liste des spécificateurs de format **UFormat** valides, consultez la section [Remarques](#notes) .</span><span class="sxs-lookup"><span data-stu-id="80817-151">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="80817-152">Exemple 5 : obtenir le jour d’une date de l’année</span><span class="sxs-lookup"><span data-stu-id="80817-152">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="80817-153">Dans cet exemple, une propriété est utilisée pour obtenir le nombre de jours de l’année.</span><span class="sxs-lookup"><span data-stu-id="80817-153">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="80817-154">Le calendrier grégorien contient 365 jours, à l’exception des années bissextiles qui comportent 366 jours.</span><span class="sxs-lookup"><span data-stu-id="80817-154">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="80817-155">Par exemple, le 31 décembre 2020 est le jour 366.</span><span class="sxs-lookup"><span data-stu-id="80817-155">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="80817-156">`Get-Date` utilise trois paramètres pour spécifier la date : **année**, **mois** et **jour**.</span><span class="sxs-lookup"><span data-stu-id="80817-156">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="80817-157">La commande est entourée de parenthèses afin que le résultat soit évalué par la propriété **DayofYear** .</span><span class="sxs-lookup"><span data-stu-id="80817-157">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="80817-158">Exemple 6 : vérifier si une date est ajustée pour l’heure d’été</span><span class="sxs-lookup"><span data-stu-id="80817-158">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="80817-159">Cet exemple utilise une méthode booléenne pour vérifier si une date est ajustée par l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="80817-159">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="80817-160">Une variable, `$DST` stocke le résultat de `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="80817-160">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="80817-161">`$DST` utilise la méthode **IsDaylightSavingTime** pour tester si la date est ajustée pour l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="80817-161">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="80817-162">Exemple 7 : convertir l’heure actuelle en heure UTC</span><span class="sxs-lookup"><span data-stu-id="80817-162">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="80817-163">Dans cet exemple, l’heure actuelle est convertie en heure UTC.</span><span class="sxs-lookup"><span data-stu-id="80817-163">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="80817-164">L’offset UTC pour les paramètres régionaux du système est utilisé pour convertir l’heure.</span><span class="sxs-lookup"><span data-stu-id="80817-164">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="80817-165">Un tableau de la section [Remarques](#notes) répertorie les spécificateurs de format **UFormat** valides.</span><span class="sxs-lookup"><span data-stu-id="80817-165">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="80817-166">`Get-Date` utilise le paramètre **UFormat** avec des spécificateurs de format pour afficher la date et l’heure système actuelles.</span><span class="sxs-lookup"><span data-stu-id="80817-166">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="80817-167">Le spécificateur de format **% Z** représente l’offset UTC de **-07**.</span><span class="sxs-lookup"><span data-stu-id="80817-167">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="80817-168">La `$Time` variable stocke la date et l’heure système actuelles.</span><span class="sxs-lookup"><span data-stu-id="80817-168">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="80817-169">`$Time` utilise la méthode **ToUniversalTime ()** pour convertir l’heure en fonction du décalage UTC de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="80817-169">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="80817-170">Exemple 8 : créer un horodateur</span><span class="sxs-lookup"><span data-stu-id="80817-170">Example 8: Create a timestamp</span></span>

<span data-ttu-id="80817-171">Dans cet exemple, un spécificateur de format crée un objet de **chaîne** d’horodatage pour un nom de répertoire.</span><span class="sxs-lookup"><span data-stu-id="80817-171">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="80817-172">L’horodateur contient la date, l’heure et le décalage UTC.</span><span class="sxs-lookup"><span data-stu-id="80817-172">The timestamp includes the date, time, and UTC offset.</span></span>

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

<span data-ttu-id="80817-173">La `$timestamp` variable stocke les résultats d’une `Get-Date` commande.</span><span class="sxs-lookup"><span data-stu-id="80817-173">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="80817-174">`Get-Date` utilise le paramètre de **format** avec le spécificateur de format en minuscules `o` pour créer un objet de **chaîne** d’horodatage.</span><span class="sxs-lookup"><span data-stu-id="80817-174">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="80817-175">L’objet est envoyé dans le pipeline à `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="80817-175">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="80817-176">Un **scriptblock** contient la `$_` variable qui représente l’objet de pipeline actuel.</span><span class="sxs-lookup"><span data-stu-id="80817-176">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="80817-177">La chaîne d’horodatage est délimitée par des signes deux-points qui sont remplacés par des points.</span><span class="sxs-lookup"><span data-stu-id="80817-177">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="80817-178">`New-Item` utilise le paramètre **path** pour spécifier l’emplacement d’un nouveau répertoire.</span><span class="sxs-lookup"><span data-stu-id="80817-178">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="80817-179">Le chemin d’accès comprend la `$timestamp` variable en tant que nom de répertoire.</span><span class="sxs-lookup"><span data-stu-id="80817-179">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="80817-180">Le paramètre de **type** spécifie qu’un répertoire est créé.</span><span class="sxs-lookup"><span data-stu-id="80817-180">The **Type** parameter specifies that a directory is created.</span></span>

### <span data-ttu-id="80817-181">Exemple 9 : convertir un horodateur UNIX</span><span class="sxs-lookup"><span data-stu-id="80817-181">Example 9: Convert a Unix timestamp</span></span>

<span data-ttu-id="80817-182">Cet exemple convertit une heure UNIX (représentée par le nombre de secondes depuis 1970-01-01 0:00:00) en DateTime.</span><span class="sxs-lookup"><span data-stu-id="80817-182">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### <span data-ttu-id="80817-183">Exemple 10 : retourner une valeur de date interprétée comme UTC</span><span class="sxs-lookup"><span data-stu-id="80817-183">Example 10: Return a date value interpreted as UTC</span></span>

<span data-ttu-id="80817-184">Cet exemple montre comment interpréter une valeur de date comme son équivalent UTC.</span><span class="sxs-lookup"><span data-stu-id="80817-184">This example shows how to interpret a date value as its UTC equivalent.</span></span> <span data-ttu-id="80817-185">Pour l’exemple, cet ordinateur est défini à l' **heure standard du Pacifique**.</span><span class="sxs-lookup"><span data-stu-id="80817-185">For the example, this machine is set to **Pacific Standard Time**.</span></span> <span data-ttu-id="80817-186">Par défaut, `Get-Date` retourne des valeurs pour ce fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="80817-186">By default, `Get-Date` returns values for that timezone.</span></span> <span data-ttu-id="80817-187">Utilisez le paramètre **AsUTC** pour convertir la valeur en heure UTC équivalente.</span><span class="sxs-lookup"><span data-stu-id="80817-187">Use the **AsUTC** parameter to convert the value to the UTC equivalent time.</span></span>

```powershell
PS> Get-TimeZone

Id                         : Pacific Standard Time
DisplayName                : (UTC-08:00) Pacific Time (US & Canada)
StandardName               : Pacific Standard Time
DaylightName               : Pacific Daylight Time
BaseUtcOffset              : -08:00:00
SupportsDaylightSavingTime : True

PS> (Get-Date -Date "2020-01-01T00:00:00").Kind
Unspecified

PS> Get-Date -Date "2020-01-01T00:00:00"

Wednesday, January 1, 2020 12:00:00 AM

PS> (Get-Date -Date "2020-01-01T00:00:00" -AsUTC).Kind
Utc

PS> Get-Date -Date "2020-01-01T00:00:00" -AsUTC

Wednesday, January 1, 2020 8:00:00 AM
```

## <span data-ttu-id="80817-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="80817-188">PARAMETERS</span></span>

### <span data-ttu-id="80817-189">-AsUTC</span><span class="sxs-lookup"><span data-stu-id="80817-189">-AsUTC</span></span>

<span data-ttu-id="80817-190">Convertit la valeur de date en heure équivalente en heure UTC.</span><span class="sxs-lookup"><span data-stu-id="80817-190">Converts the date value to the equivalent time in UTC.</span></span>

<span data-ttu-id="80817-191">Ce paramètre a été introduit dans PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="80817-191">This parameter was introduced in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="80817-192">-Date</span><span class="sxs-lookup"><span data-stu-id="80817-192">-Date</span></span>

<span data-ttu-id="80817-193">Spécifie une date et une heure.</span><span class="sxs-lookup"><span data-stu-id="80817-193">Specifies a date and time.</span></span> <span data-ttu-id="80817-194">L’heure est facultative et, si elle n’est pas spécifiée, retourne 00:00:00.</span><span class="sxs-lookup"><span data-stu-id="80817-194">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="80817-195">Entrez la date et l’heure dans un format standard pour les paramètres régionaux système.</span><span class="sxs-lookup"><span data-stu-id="80817-195">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="80817-196">Par exemple, en anglais (États-Unis) :</span><span class="sxs-lookup"><span data-stu-id="80817-196">For example, in US English:</span></span>

<span data-ttu-id="80817-197">`Get-Date -Date "6/25/2019 12:30:22"` retourne mardi 25 juin, 2019 12:30:22</span><span class="sxs-lookup"><span data-stu-id="80817-197">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: DateAndFormat, DateAndUFormat
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="80817-198">-Jour</span><span class="sxs-lookup"><span data-stu-id="80817-198">-Day</span></span>

<span data-ttu-id="80817-199">Spécifie le jour du mois qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="80817-199">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="80817-200">Entrez une valeur comprise entre 1 et 31.</span><span class="sxs-lookup"><span data-stu-id="80817-200">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="80817-201">Si la valeur spécifiée est supérieure au nombre de jours d’un mois, PowerShell ajoute le nombre de jours au mois.</span><span class="sxs-lookup"><span data-stu-id="80817-201">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="80817-202">Par exemple, `Get-Date -Month 2 -Day 31` affiche le **3 mars**, et non le **31 février**.</span><span class="sxs-lookup"><span data-stu-id="80817-202">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="80817-203">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="80817-203">-DisplayHint</span></span>

<span data-ttu-id="80817-204">Détermine les éléments de date et d'heure à afficher.</span><span class="sxs-lookup"><span data-stu-id="80817-204">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="80817-205">Les valeurs acceptées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="80817-205">The accepted values are as follows:</span></span>

- <span data-ttu-id="80817-206">**Date**: affiche uniquement la date</span><span class="sxs-lookup"><span data-stu-id="80817-206">**Date**: displays only the date</span></span>
- <span data-ttu-id="80817-207">**Heure**: affiche uniquement l’heure</span><span class="sxs-lookup"><span data-stu-id="80817-207">**Time**: displays only the time</span></span>
- <span data-ttu-id="80817-208">**DateTime**: affiche la date et l’heure</span><span class="sxs-lookup"><span data-stu-id="80817-208">**DateTime**: displays the date and time</span></span>

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

### <span data-ttu-id="80817-209">-Format</span><span class="sxs-lookup"><span data-stu-id="80817-209">-Format</span></span>

<span data-ttu-id="80817-210">Affiche la date et l'heure dans le format Microsoft .NET Framework indiqué par le spécificateur de format.</span><span class="sxs-lookup"><span data-stu-id="80817-210">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="80817-211">Le paramètre **format** génère un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="80817-211">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="80817-212">Pour obtenir la liste des spécificateurs de format .NET disponibles, consultez [chaînes de format de date et d’heure personnalisées](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="80817-212">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="80817-213">Lorsque le paramètre **format** est utilisé, `Get-Date` obtient uniquement les propriétés de l’objet **DateTime** nécessaires à l’affichage de la date.</span><span class="sxs-lookup"><span data-stu-id="80817-213">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="80817-214">Ainsi, certaines propriétés et méthodes des objets **DateTime** ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="80817-214">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="80817-215">À compter de PowerShell 5,0, vous pouvez utiliser les formats supplémentaires suivants comme valeurs pour le paramètre **format** .</span><span class="sxs-lookup"><span data-stu-id="80817-215">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="80817-216">**Archivé**.</span><span class="sxs-lookup"><span data-stu-id="80817-216">**FileDate**.</span></span> <span data-ttu-id="80817-217">Représentation conviviale d’un fichier ou d’un chemin d’accès de la date actuelle en heure locale.</span><span class="sxs-lookup"><span data-stu-id="80817-217">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="80817-218">Le format est `yyyyMMdd` (respecte la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres et un jour à 2 chiffres).</span><span class="sxs-lookup"><span data-stu-id="80817-218">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="80817-219">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="80817-219">For example:</span></span>
  20190627.

- <span data-ttu-id="80817-220">**FileDateUniversal**.</span><span class="sxs-lookup"><span data-stu-id="80817-220">**FileDateUniversal**.</span></span> <span data-ttu-id="80817-221">Représentation conviviale d’un fichier ou d’un chemin d’accès de la date actuelle en temps universel (UTC).</span><span class="sxs-lookup"><span data-stu-id="80817-221">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="80817-222">Le format est `yyyyMMddZ` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres et la lettre `Z` comme indicateur UTC).</span><span class="sxs-lookup"><span data-stu-id="80817-222">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="80817-223">Par exemple : 20190627Z.</span><span class="sxs-lookup"><span data-stu-id="80817-223">For example: 20190627Z.</span></span>

- <span data-ttu-id="80817-224">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="80817-224">**FileDateTime**.</span></span> <span data-ttu-id="80817-225">Représentation conviviale de fichier ou de chemin d’accès de la date et de l’heure en heure locale, au format 24 heures.</span><span class="sxs-lookup"><span data-stu-id="80817-225">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="80817-226">Le format est `yyyyMMddTHHmmssffff` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres, la lettre `T` comme séparateur horaire, l’heure à 2 chiffres, la minute à 2 chiffres, la seconde à 2 chiffres et la milliseconde sur 4 chiffres).</span><span class="sxs-lookup"><span data-stu-id="80817-226">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="80817-227">Par exemple : 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="80817-227">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="80817-228">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="80817-228">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="80817-229">Représentation conviviale d’un fichier ou d’un chemin d’accès de la date et de l’heure en temps universel (UTC), au format 24 heures.</span><span class="sxs-lookup"><span data-stu-id="80817-229">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="80817-230">Le format est `yyyyMMddTHHmmssffffZ` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres, la lettre `T` comme séparateur d’heure, une heure à 2 chiffres, une minute à 2 chiffres, une seconde à 2 chiffres, une milliseconde à 4 chiffres et la lettre `Z` comme indicateur UTC).</span><span class="sxs-lookup"><span data-stu-id="80817-230">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="80817-231">Par exemple : 20190627T1540500718Z.</span><span class="sxs-lookup"><span data-stu-id="80817-231">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: DateAndFormat, UnixTimeSecondsAndFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80817-232">-Heure</span><span class="sxs-lookup"><span data-stu-id="80817-232">-Hour</span></span>

<span data-ttu-id="80817-233">Spécifie l'heure qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="80817-233">Specifies the hour that is displayed.</span></span> <span data-ttu-id="80817-234">Entrez une valeur comprise entre 0 et 23.</span><span class="sxs-lookup"><span data-stu-id="80817-234">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="80817-235">-Milliseconde</span><span class="sxs-lookup"><span data-stu-id="80817-235">-Millisecond</span></span>

<span data-ttu-id="80817-236">Spécifie le nombre de millisecondes dans la date.</span><span class="sxs-lookup"><span data-stu-id="80817-236">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="80817-237">Entrez une valeur comprise entre 0 et 999.</span><span class="sxs-lookup"><span data-stu-id="80817-237">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="80817-238">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="80817-238">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="80817-239">-Minute</span><span class="sxs-lookup"><span data-stu-id="80817-239">-Minute</span></span>

<span data-ttu-id="80817-240">Spécifie le nombre de minutes qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="80817-240">Specifies the minute that is displayed.</span></span> <span data-ttu-id="80817-241">Entrez une valeur comprise entre 0 et 59.</span><span class="sxs-lookup"><span data-stu-id="80817-241">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="80817-242">-Mois</span><span class="sxs-lookup"><span data-stu-id="80817-242">-Month</span></span>

<span data-ttu-id="80817-243">Spécifie le mois qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="80817-243">Specifies the month that is displayed.</span></span> <span data-ttu-id="80817-244">Entrez une valeur comprise entre 1 et 12.</span><span class="sxs-lookup"><span data-stu-id="80817-244">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="80817-245">-Seconde</span><span class="sxs-lookup"><span data-stu-id="80817-245">-Second</span></span>

<span data-ttu-id="80817-246">Spécifie le nombre de secondes qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="80817-246">Specifies the second that is displayed.</span></span> <span data-ttu-id="80817-247">Entrez une valeur comprise entre 0 et 59.</span><span class="sxs-lookup"><span data-stu-id="80817-247">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="80817-248">-UFormat</span><span class="sxs-lookup"><span data-stu-id="80817-248">-UFormat</span></span>

<span data-ttu-id="80817-249">Affiche la date et l'heure au format UNIX.</span><span class="sxs-lookup"><span data-stu-id="80817-249">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="80817-250">Le paramètre **UFormat** génère un objet String.</span><span class="sxs-lookup"><span data-stu-id="80817-250">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="80817-251">Les spécificateurs **UFormat** sont précédés d’un signe `%` de pourcentage (), par exemple,, `%m` `%d` et `%Y` .</span><span class="sxs-lookup"><span data-stu-id="80817-251">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="80817-252">La section [Remarques](#notes) contient un tableau de **spécificateurs UFormat** valides.</span><span class="sxs-lookup"><span data-stu-id="80817-252">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="80817-253">Lorsque le paramètre **UFormat** est utilisé, `Get-Date` obtient uniquement les propriétés de l’objet **DateTime** nécessaires à l’affichage de la date.</span><span class="sxs-lookup"><span data-stu-id="80817-253">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="80817-254">Ainsi, certaines propriétés et méthodes des objets **DateTime** ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="80817-254">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: DateAndUFormat, UnixTimeSecondsAndUFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80817-255">-UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="80817-255">-UnixTimeSeconds</span></span>

<span data-ttu-id="80817-256">Date et heure représentées en secondes depuis le 1er janvier 1970, 0:00:00.</span><span class="sxs-lookup"><span data-stu-id="80817-256">Date and time represented in seconds since January 1, 1970, 0:00:00.</span></span>

<span data-ttu-id="80817-257">Ce paramètre a été introduit dans PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="80817-257">This parameter was introduced in PowerShell 7.1.</span></span>

```yaml
Type: System.Int64
Parameter Sets: UnixTimeSecondsAndFormat, UnixTimeSecondsAndUFormat
Aliases: UnixTime

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80817-258">-Année</span><span class="sxs-lookup"><span data-stu-id="80817-258">-Year</span></span>

<span data-ttu-id="80817-259">Spécifie l'année qui s'affiche.</span><span class="sxs-lookup"><span data-stu-id="80817-259">Specifies the year that is displayed.</span></span> <span data-ttu-id="80817-260">Entrez une valeur comprise entre 1 et 9999.</span><span class="sxs-lookup"><span data-stu-id="80817-260">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="80817-261">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="80817-261">CommonParameters</span></span>

<span data-ttu-id="80817-262">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="80817-262">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="80817-263">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="80817-263">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="80817-264">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="80817-264">INPUTS</span></span>

### <span data-ttu-id="80817-265">Entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="80817-265">Pipeline input</span></span>

<span data-ttu-id="80817-266">`Get-Date` accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="80817-266">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="80817-267">Par exemple, `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="80817-267">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="80817-268">SORTIES</span><span class="sxs-lookup"><span data-stu-id="80817-268">OUTPUTS</span></span>

### <span data-ttu-id="80817-269">System. DateTime ou System. String</span><span class="sxs-lookup"><span data-stu-id="80817-269">System.DateTime or System.String</span></span>

<span data-ttu-id="80817-270">`Get-Date` retourne un objet **DateTime** sauf lorsque les paramètres **format** et **UFormat** sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="80817-270">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="80817-271">Les paramètres **format** ou **UFormat** retournent des objets de **chaîne** .</span><span class="sxs-lookup"><span data-stu-id="80817-271">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="80817-272">Lorsqu’un objet **DateTime** est envoyé vers le pipeline à une applet de commande, comme `Add-Content` qui attend une entrée de chaîne, PowerShell convertit l’objet en un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="80817-272">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="80817-273">La méthode `(Get-Date).ToString()` convertit un objet **DateTime** en objet **String** .</span><span class="sxs-lookup"><span data-stu-id="80817-273">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="80817-274">Pour afficher les propriétés et les méthodes d’un objet, envoyez l’objet vers le dessous du pipeline `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="80817-274">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="80817-275">Par exemple, `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="80817-275">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="80817-276">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="80817-276">NOTES</span></span>

<span data-ttu-id="80817-277">Les objets **DateTime** sont dans des formats de date longue et d’heure longue pour les paramètres régionaux système.</span><span class="sxs-lookup"><span data-stu-id="80817-277">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="80817-278">Les **spécificateurs UFormat** valides sont affichés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="80817-278">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="80817-279">Spécificateur de format</span><span class="sxs-lookup"><span data-stu-id="80817-279">Format specifier</span></span> |                                 <span data-ttu-id="80817-280">Signification</span><span class="sxs-lookup"><span data-stu-id="80817-280">Meaning</span></span>                     |         <span data-ttu-id="80817-281">Exemple</span><span class="sxs-lookup"><span data-stu-id="80817-281">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="80817-282">Jour de la semaine-Nom complet</span><span class="sxs-lookup"><span data-stu-id="80817-282">Day of the week - full name</span></span>                                             | <span data-ttu-id="80817-283">Lundi</span><span class="sxs-lookup"><span data-stu-id="80817-283">Monday</span></span>                   |
| `%a` | <span data-ttu-id="80817-284">Jour de la semaine-Nom abrégé</span><span class="sxs-lookup"><span data-stu-id="80817-284">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="80817-285">Lun</span><span class="sxs-lookup"><span data-stu-id="80817-285">Mon</span></span>                      |
| `%B` | <span data-ttu-id="80817-286">Nom du mois-complet</span><span class="sxs-lookup"><span data-stu-id="80817-286">Month name - full</span></span>                                                       | <span data-ttu-id="80817-287">Janvier</span><span class="sxs-lookup"><span data-stu-id="80817-287">January</span></span>                  |
| `%b` | <span data-ttu-id="80817-288">Nom du mois-abrégé</span><span class="sxs-lookup"><span data-stu-id="80817-288">Month name - abbreviated</span></span>                                                | <span data-ttu-id="80817-289">Jan</span><span class="sxs-lookup"><span data-stu-id="80817-289">Jan</span></span>                      |
| `%C` | <span data-ttu-id="80817-290">Siècle</span><span class="sxs-lookup"><span data-stu-id="80817-290">Century</span></span>                                                                 | <span data-ttu-id="80817-291">20 pour 2019</span><span class="sxs-lookup"><span data-stu-id="80817-291">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="80817-292">Date et heure-abrégé</span><span class="sxs-lookup"><span data-stu-id="80817-292">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="80817-293">Jeudi Juin 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="80817-293">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="80817-294">Date au format mm/jj/aa</span><span class="sxs-lookup"><span data-stu-id="80817-294">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="80817-295">06/27/19</span><span class="sxs-lookup"><span data-stu-id="80817-295">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="80817-296">Jour du mois-2 chiffres</span><span class="sxs-lookup"><span data-stu-id="80817-296">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="80817-297">05</span><span class="sxs-lookup"><span data-stu-id="80817-297">05</span></span>                       |
| `%e` | <span data-ttu-id="80817-298">Jour du mois-précédé d’un espace si seul un chiffre</span><span class="sxs-lookup"><span data-stu-id="80817-298">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="80817-299">\<space\>5,5</span><span class="sxs-lookup"><span data-stu-id="80817-299">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="80817-300">Date au format aaaa-mm-jj, égale à% Y-% m-% d (le format de date ISO 8601)</span><span class="sxs-lookup"><span data-stu-id="80817-300">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="80817-301">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="80817-301">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="80817-302">Identique à « Y »</span><span class="sxs-lookup"><span data-stu-id="80817-302">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="80817-303">Identique à « y »</span><span class="sxs-lookup"><span data-stu-id="80817-303">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="80817-304">Heure au format 24 heures</span><span class="sxs-lookup"><span data-stu-id="80817-304">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="80817-305">17</span><span class="sxs-lookup"><span data-stu-id="80817-305">17</span></span>                       |
| `%h` | <span data-ttu-id="80817-306">Identique à « b »</span><span class="sxs-lookup"><span data-stu-id="80817-306">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="80817-307">Heure au format 12 heures</span><span class="sxs-lookup"><span data-stu-id="80817-307">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="80817-308">05</span><span class="sxs-lookup"><span data-stu-id="80817-308">05</span></span>                       |
| `%j` | <span data-ttu-id="80817-309">Jour de l’année</span><span class="sxs-lookup"><span data-stu-id="80817-309">Day of the year</span></span>                                                         | <span data-ttu-id="80817-310">1-366</span><span class="sxs-lookup"><span data-stu-id="80817-310">1-366</span></span>                    |
| `%k` | <span data-ttu-id="80817-311">Identique à « H »</span><span class="sxs-lookup"><span data-stu-id="80817-311">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="80817-312">Identique à « I » (I majuscule)</span><span class="sxs-lookup"><span data-stu-id="80817-312">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="80817-313">05</span><span class="sxs-lookup"><span data-stu-id="80817-313">05</span></span>                       |
| `%M` | <span data-ttu-id="80817-314">Minutes</span><span class="sxs-lookup"><span data-stu-id="80817-314">Minutes</span></span>                                                                 | <span data-ttu-id="80817-315">35</span><span class="sxs-lookup"><span data-stu-id="80817-315">35</span></span>                       |
| `%m` | <span data-ttu-id="80817-316">Numéro du mois</span><span class="sxs-lookup"><span data-stu-id="80817-316">Month number</span></span>                                                            | <span data-ttu-id="80817-317">06</span><span class="sxs-lookup"><span data-stu-id="80817-317">06</span></span>                       |
| `%n` | <span data-ttu-id="80817-318">caractère de saut de ligne</span><span class="sxs-lookup"><span data-stu-id="80817-318">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="80817-319">AM ou PM</span><span class="sxs-lookup"><span data-stu-id="80817-319">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="80817-320">Heure au format 24 heures-pas de secondes</span><span class="sxs-lookup"><span data-stu-id="80817-320">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="80817-321">17:45</span><span class="sxs-lookup"><span data-stu-id="80817-321">17:45</span></span>                    |
| `%r` | <span data-ttu-id="80817-322">Heure au format 12 heures</span><span class="sxs-lookup"><span data-stu-id="80817-322">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="80817-323">09:15:36</span><span class="sxs-lookup"><span data-stu-id="80817-323">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="80817-324">Secondes</span><span class="sxs-lookup"><span data-stu-id="80817-324">Seconds</span></span>                                                                 | <span data-ttu-id="80817-325">05</span><span class="sxs-lookup"><span data-stu-id="80817-325">05</span></span>                       |
| `%s` | <span data-ttu-id="80817-326">Secondes écoulées depuis le 1er janvier 1970 00:00:00</span><span class="sxs-lookup"><span data-stu-id="80817-326">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="80817-327">1150451174</span><span class="sxs-lookup"><span data-stu-id="80817-327">1150451174</span></span>               |
| `%t` | <span data-ttu-id="80817-328">Caractère de tabulation horizontale</span><span class="sxs-lookup"><span data-stu-id="80817-328">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="80817-329">Heure au format 24 heures</span><span class="sxs-lookup"><span data-stu-id="80817-329">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="80817-330">17:45:52</span><span class="sxs-lookup"><span data-stu-id="80817-330">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="80817-331">Identique à « W »</span><span class="sxs-lookup"><span data-stu-id="80817-331">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="80817-332">Jour de la semaine-numéro</span><span class="sxs-lookup"><span data-stu-id="80817-332">Day of the week - number</span></span>                                                | <span data-ttu-id="80817-333">Dimanche = 0</span><span class="sxs-lookup"><span data-stu-id="80817-333">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="80817-334">Semaine de l’année</span><span class="sxs-lookup"><span data-stu-id="80817-334">Week of the year</span></span>                                                        | <span data-ttu-id="80817-335">01-53</span><span class="sxs-lookup"><span data-stu-id="80817-335">01-53</span></span>                    |
| `%w` | <span data-ttu-id="80817-336">Identique à « u »</span><span class="sxs-lookup"><span data-stu-id="80817-336">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="80817-337">Semaine de l’année</span><span class="sxs-lookup"><span data-stu-id="80817-337">Week of the year</span></span>                                                        | <span data-ttu-id="80817-338">00-52</span><span class="sxs-lookup"><span data-stu-id="80817-338">00-52</span></span>                    |
| `%X` | <span data-ttu-id="80817-339">Identique à « t »</span><span class="sxs-lookup"><span data-stu-id="80817-339">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="80817-340">Date au format standard pour les paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="80817-340">Date in standard format for locale</span></span>                                      | <span data-ttu-id="80817-341">06/27/19 pour l’anglais (États-Unis)</span><span class="sxs-lookup"><span data-stu-id="80817-341">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="80817-342">Année au format à 4 chiffres</span><span class="sxs-lookup"><span data-stu-id="80817-342">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="80817-343">2019</span><span class="sxs-lookup"><span data-stu-id="80817-343">2019</span></span>                     |
| `%y` | <span data-ttu-id="80817-344">Année au format à 2 chiffres</span><span class="sxs-lookup"><span data-stu-id="80817-344">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="80817-345">19</span><span class="sxs-lookup"><span data-stu-id="80817-345">19</span></span>                       |
| `%Z` | <span data-ttu-id="80817-346">Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate)</span><span class="sxs-lookup"><span data-stu-id="80817-346">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="80817-347">-07</span><span class="sxs-lookup"><span data-stu-id="80817-347">-07</span></span>                      |

## <span data-ttu-id="80817-348">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="80817-348">RELATED LINKS</span></span>

[<span data-ttu-id="80817-349">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="80817-349">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="80817-350">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="80817-350">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="80817-351">Get-Member</span><span class="sxs-lookup"><span data-stu-id="80817-351">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="80817-352">New-Item</span><span class="sxs-lookup"><span data-stu-id="80817-352">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="80817-353">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="80817-353">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="80817-354">Set-Date</span><span class="sxs-lookup"><span data-stu-id="80817-354">Set-Date</span></span>](Set-Date.md)
