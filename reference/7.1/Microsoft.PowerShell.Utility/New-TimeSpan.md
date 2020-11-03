---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 135b4441490bbee7d8c8e0088080f97a7128af53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204977"
---
# <span data-ttu-id="632cf-103">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="632cf-103">New-TimeSpan</span></span>

## <span data-ttu-id="632cf-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="632cf-104">SYNOPSIS</span></span>
<span data-ttu-id="632cf-105">Crée un objet TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="632cf-105">Creates a TimeSpan object.</span></span>

## <span data-ttu-id="632cf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="632cf-106">SYNTAX</span></span>

### <span data-ttu-id="632cf-107">Date (par défaut)</span><span class="sxs-lookup"><span data-stu-id="632cf-107">Date (Default)</span></span>

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="632cf-108">Heure</span><span class="sxs-lookup"><span data-stu-id="632cf-108">Time</span></span>

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="632cf-109">Description</span><span class="sxs-lookup"><span data-stu-id="632cf-109">DESCRIPTION</span></span>

<span data-ttu-id="632cf-110">L' `New-TimeSpan` applet de commande crée un objet **TimeSpan** qui représente un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="632cf-110">The `New-TimeSpan` cmdlet creates a **TimeSpan** object that represents a time interval.</span></span>
<span data-ttu-id="632cf-111">Vous pouvez utiliser un objet **TimeSpan** pour ajouter ou soustraire du temps à des objets **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="632cf-111">You can use a **TimeSpan** object to add or subtract time from **DateTime** objects.</span></span>

<span data-ttu-id="632cf-112">Sans paramètres, une `New-TimeSpan` commande retourne un objet **TimeSpan** qui représente un intervalle de temps égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="632cf-112">Without parameters, a `New-TimeSpan` command returns a **TimeSpan** object that represents a time interval of zero.</span></span>

## <span data-ttu-id="632cf-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="632cf-113">EXAMPLES</span></span>

### <span data-ttu-id="632cf-114">Exemple 1 : créer un objet TimeSpan pour une durée spécifiée</span><span class="sxs-lookup"><span data-stu-id="632cf-114">Example 1: Create a TimeSpan object for a specified duration</span></span>

<span data-ttu-id="632cf-115">Cette commande crée un objet **TimeSpan** avec une durée de 1 heure et 25 minutes et le stocke dans une variable nommée `$TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="632cf-115">This command creates a **TimeSpan** object with a duration of 1 hour and 25 minutes and stores it in a variable named `$TimeSpan`.</span></span> <span data-ttu-id="632cf-116">Elle affiche une représentation de l’objet **TimeSpan** .</span><span class="sxs-lookup"><span data-stu-id="632cf-116">It displays a representation of the **TimeSpan** object.</span></span>

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### <span data-ttu-id="632cf-117">Exemple 2 : créer un objet TimeSpan pour un intervalle de temps</span><span class="sxs-lookup"><span data-stu-id="632cf-117">Example 2: Create a TimeSpan object for a time interval</span></span>

<span data-ttu-id="632cf-118">Cet exemple crée un nouvel objet **TimeSpan** qui représente l’intervalle entre l’exécution de la commande et le 1er janvier 2010.</span><span class="sxs-lookup"><span data-stu-id="632cf-118">This example creates a new **TimeSpan** object that represents the interval between the time that the command is run and January 1, 2010.</span></span>

<span data-ttu-id="632cf-119">Cette commande ne nécessite pas le paramètre **Start** , car la valeur par défaut du paramètre **Start** correspond à la date et à l’heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="632cf-119">This command does not require the **Start** parameter, because the default value of the **Start** parameter is the current date and time.</span></span>

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### <span data-ttu-id="632cf-120">Exemple 3 : récupérer la date 90 jours à partir de la date actuelle</span><span class="sxs-lookup"><span data-stu-id="632cf-120">Example 3: Get the date 90 days from the current date</span></span>

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

<span data-ttu-id="632cf-121">Ces commandes retournent la date située 90 jours après la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="632cf-121">These commands return the date that is 90 days after the current date.</span></span>

### <span data-ttu-id="632cf-122">Exemple 4 : découvrir la période depuis la mise à jour d’un fichier</span><span class="sxs-lookup"><span data-stu-id="632cf-122">Example 4: Discover the TimeSpan since a file was updated</span></span>

<span data-ttu-id="632cf-123">Cette commande vous indique le temps écoulé depuis la dernière mise à jour du fichier d’aide [about_Remote](../Microsoft.PowerShell.Core/About/about_Remote.md) .</span><span class="sxs-lookup"><span data-stu-id="632cf-123">This command tells you how long it has been since the [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) help file was last updated.</span></span>
<span data-ttu-id="632cf-124">Vous pouvez utiliser ce format de commande sur n’importe quel fichier ou tout autre objet qui possède une propriété **LastWriteTime** .</span><span class="sxs-lookup"><span data-stu-id="632cf-124">You can use this command format on any file, or any other object that has a **LastWriteTime** property.</span></span>

<span data-ttu-id="632cf-125">Cette commande fonctionne parce que le paramètre de **démarrage** de `New-TimeSpan` a un alias **LastWriteTime** .</span><span class="sxs-lookup"><span data-stu-id="632cf-125">This command works because the **Start** parameter of `New-TimeSpan` has an alias of **LastWriteTime** .</span></span> <span data-ttu-id="632cf-126">Quand vous dirigez un objet qui a une propriété **LastWriteTime** vers `New-TimeSpan` , PowerShell utilise la valeur de la propriété **LastWriteTime** comme valeur du paramètre **Start** .</span><span class="sxs-lookup"><span data-stu-id="632cf-126">When you pipe an object that has a **LastWriteTime** property to `New-TimeSpan`, PowerShell uses the value of the **LastWriteTime** property as the value of the **Start** parameter.</span></span>

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## <span data-ttu-id="632cf-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="632cf-127">PARAMETERS</span></span>

### <span data-ttu-id="632cf-128">-Days</span><span class="sxs-lookup"><span data-stu-id="632cf-128">-Days</span></span>

<span data-ttu-id="632cf-129">Spécifie les jours dans l’intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="632cf-129">Specifies the days in the time span.</span></span>
<span data-ttu-id="632cf-130">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="632cf-130">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="632cf-131">-Fin</span><span class="sxs-lookup"><span data-stu-id="632cf-131">-End</span></span>

<span data-ttu-id="632cf-132">Spécifie la fin d’un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="632cf-132">Specifies the end of a time span.</span></span>
<span data-ttu-id="632cf-133">La valeur par défaut est l'horodatage actuel.</span><span class="sxs-lookup"><span data-stu-id="632cf-133">The default value is the current date and time.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="632cf-134">Heures d’ouverture</span><span class="sxs-lookup"><span data-stu-id="632cf-134">-Hours</span></span>

<span data-ttu-id="632cf-135">Spécifie les heures dans l’intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="632cf-135">Specifies the hours in the time span.</span></span>
<span data-ttu-id="632cf-136">La valeur par défaut est zéro.</span><span class="sxs-lookup"><span data-stu-id="632cf-136">The default value is zero.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="632cf-137">-Minutes</span><span class="sxs-lookup"><span data-stu-id="632cf-137">-Minutes</span></span>

<span data-ttu-id="632cf-138">Spécifie les minutes dans l’intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="632cf-138">Specifies the minutes in the time span.</span></span>
<span data-ttu-id="632cf-139">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="632cf-139">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="632cf-140">-Secondes</span><span class="sxs-lookup"><span data-stu-id="632cf-140">-Seconds</span></span>

<span data-ttu-id="632cf-141">Spécifie la longueur de l’intervalle de temps en secondes.</span><span class="sxs-lookup"><span data-stu-id="632cf-141">Specifies the length of the time span in seconds.</span></span>
<span data-ttu-id="632cf-142">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="632cf-142">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="632cf-143">-Start</span><span class="sxs-lookup"><span data-stu-id="632cf-143">-Start</span></span>

<span data-ttu-id="632cf-144">Spécifie le début d’un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="632cf-144">Specifies the start of a time span.</span></span>
<span data-ttu-id="632cf-145">Entrez une chaîne qui représente la date et l’heure, par exemple « 3/15/09 » ou un objet **DateTime** , tel que celui d’une `Get-Date` commande.</span><span class="sxs-lookup"><span data-stu-id="632cf-145">Enter a string that represents the date and time, such as "3/15/09" or a **DateTime** object, such as one from a `Get-Date` command.</span></span> <span data-ttu-id="632cf-146">La valeur par défaut est l'horodatage actuel.</span><span class="sxs-lookup"><span data-stu-id="632cf-146">The default value is the current date and time.</span></span>

<span data-ttu-id="632cf-147">Vous pouvez utiliser **Start** ou son alias, **LastWriteTime** .</span><span class="sxs-lookup"><span data-stu-id="632cf-147">You can use **Start** or its alias, **LastWriteTime** .</span></span>
<span data-ttu-id="632cf-148">L’alias **LastWriteTime** vous permet de diriger des objets qui ont une propriété **LastWriteTime** , tels que des fichiers dans le système de fichiers `[System.Io.FileIO]` , vers le paramètre de **démarrage** de `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="632cf-148">The **LastWriteTime** alias lets you pipe objects that have a **LastWriteTime** property, such as files in the file system `[System.Io.FileIO]`, to the **Start** parameter of `New-TimeSpan`.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="632cf-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="632cf-149">CommonParameters</span></span>

<span data-ttu-id="632cf-150">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="632cf-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="632cf-151">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="632cf-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="632cf-152">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="632cf-152">INPUTS</span></span>

### <span data-ttu-id="632cf-153">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="632cf-153">System.DateTime</span></span>

<span data-ttu-id="632cf-154">Vous pouvez diriger un objet **DateTime** qui représente cette heure de début vers `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="632cf-154">You can pipe a **DateTime** object that represents that start time to `New-TimeSpan`.</span></span>

## <span data-ttu-id="632cf-155">SORTIES</span><span class="sxs-lookup"><span data-stu-id="632cf-155">OUTPUTS</span></span>

### <span data-ttu-id="632cf-156">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="632cf-156">System.TimeSpan</span></span>

<span data-ttu-id="632cf-157">`New-TimeSpan` retourne un objet qui représente l’intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="632cf-157">`New-TimeSpan` returns an object that represents the time span.</span></span>

## <span data-ttu-id="632cf-158">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="632cf-158">NOTES</span></span>

## <span data-ttu-id="632cf-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="632cf-159">RELATED LINKS</span></span>

[<span data-ttu-id="632cf-160">Obtient la date</span><span class="sxs-lookup"><span data-stu-id="632cf-160">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="632cf-161">Set-Date</span><span class="sxs-lookup"><span data-stu-id="632cf-161">Set-Date</span></span>](Set-Date.md)

