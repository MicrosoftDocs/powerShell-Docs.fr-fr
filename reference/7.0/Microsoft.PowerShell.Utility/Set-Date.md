---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: a1d15dfcbafba2d3f4853b6bcc59e787a022a3ed
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390148"
---
# <span data-ttu-id="138eb-103">Set-Date</span><span class="sxs-lookup"><span data-stu-id="138eb-103">Set-Date</span></span>

## <span data-ttu-id="138eb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="138eb-104">SYNOPSIS</span></span>
<span data-ttu-id="138eb-105">Définit l'heure système sur l'ordinateur sur une heure que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="138eb-105">Changes the system time on the computer to a time that you specify.</span></span>

## <span data-ttu-id="138eb-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="138eb-106">SYNTAX</span></span>

### <span data-ttu-id="138eb-107">Date (par défaut)</span><span class="sxs-lookup"><span data-stu-id="138eb-107">Date (Default)</span></span>

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="138eb-108">Réglage</span><span class="sxs-lookup"><span data-stu-id="138eb-108">Adjust</span></span>

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="138eb-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="138eb-109">DESCRIPTION</span></span>

<span data-ttu-id="138eb-110">L' `Set-Date` applet de commande remplace la date et l’heure système de l’ordinateur par une date et une heure que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="138eb-110">The `Set-Date` cmdlet changes the system date and time on the computer to a date and time that you specify.</span></span>
<span data-ttu-id="138eb-111">Vous pouvez spécifier une nouvelle date et/ou heure en tapant une chaîne ou en passant un objet **DateTime** ou **TimeSpan** à `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="138eb-111">You can specify a new date and/or time by typing a string or by passing a **DateTime** or **TimeSpan** object to `Set-Date`.</span></span> <span data-ttu-id="138eb-112">Pour spécifier une nouvelle date ou heure, utilisez le paramètre **Date** .</span><span class="sxs-lookup"><span data-stu-id="138eb-112">To specify a new date or time, use the **Date** parameter.</span></span>
<span data-ttu-id="138eb-113">Pour spécifier un intervalle de modification, utilisez le paramètre **Adjust** .</span><span class="sxs-lookup"><span data-stu-id="138eb-113">To specify a change interval, use the **Adjust** parameter.</span></span>

## <span data-ttu-id="138eb-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="138eb-114">EXAMPLES</span></span>

### <span data-ttu-id="138eb-115">Exemple 1 : ajouter trois jours à la date système</span><span class="sxs-lookup"><span data-stu-id="138eb-115">Example 1: Add three days to the system date</span></span>

<span data-ttu-id="138eb-116">Cette commande ajoute trois jours à la date système actuelle.</span><span class="sxs-lookup"><span data-stu-id="138eb-116">This command adds three days to the current system date.</span></span>
<span data-ttu-id="138eb-117">Elle n'affecte pas l'heure.</span><span class="sxs-lookup"><span data-stu-id="138eb-117">It does not affect the time.</span></span>
<span data-ttu-id="138eb-118">La commande utilise le paramètre **Date** pour spécifier la date.</span><span class="sxs-lookup"><span data-stu-id="138eb-118">The command uses the **Date** parameter to specify the date.</span></span>

<span data-ttu-id="138eb-119">L' `Get-Date` applet de commande retourne la date actuelle sous la forme d’un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="138eb-119">The `Get-Date` cmdlet returns the current date as a **DateTime** object.</span></span> <span data-ttu-id="138eb-120">La méthode **AddDays** de l’objet **DateTime** ajoute un nombre spécifié de jours (3) à l’objet **DateTime** actuel.</span><span class="sxs-lookup"><span data-stu-id="138eb-120">The **DateTime** object's **AddDays** method adds a specified number of days (3) to the current **DateTime** object.</span></span>

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### <span data-ttu-id="138eb-121">Exemple 2 : définir l’horloge système à 10 minutes</span><span class="sxs-lookup"><span data-stu-id="138eb-121">Example 2: Set the system clock back 10 minutes</span></span>

<span data-ttu-id="138eb-122">Cet exemple rétablit l’heure système actuelle de 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="138eb-122">This example sets the current system time back by 10 minutes.</span></span>

<span data-ttu-id="138eb-123">Le paramètre de **réglage** vous permet de spécifier un intervalle de modification (moins dix minutes) au format d’heure standard pour les paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="138eb-123">The **Adjust** parameter allows you to specify an interval of change (minus ten minutes) in the standard time format for the locale.</span></span>

<span data-ttu-id="138eb-124">Le paramètre **DisplayHint** indique à PowerShell d’afficher uniquement l’heure, mais il n’affecte pas l’objet **DateTime** `Set-Date` retourné par.</span><span class="sxs-lookup"><span data-stu-id="138eb-124">The **DisplayHint** parameter tells PowerShell to display only the time, but it does not affect the **DateTime** object that `Set-Date` returns.</span></span>

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### <span data-ttu-id="138eb-125">Exemple 3 : définir la date et l’heure sur une valeur de variable</span><span class="sxs-lookup"><span data-stu-id="138eb-125">Example 3: Set the date and time to a variable value</span></span>

<span data-ttu-id="138eb-126">Ces commandes modifient la date et l’heure système sur l’ordinateur local en fonction de la date et de l’heure enregistrées dans la variable `$T` .</span><span class="sxs-lookup"><span data-stu-id="138eb-126">These commands change the system date and time on local computer to the date and time saved in the variable `$T`.</span></span> <span data-ttu-id="138eb-127">La première commande obtient la date et la stocke dans `$T` .</span><span class="sxs-lookup"><span data-stu-id="138eb-127">The first command gets the date and stores it in `$T`.</span></span>

<span data-ttu-id="138eb-128">La deuxième commande utilise le paramètre **Date** pour passer l’objet **DateTime** dans `$T` l’applet de commande `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="138eb-128">The second command uses the **Date** parameter to pass the **DateTime** object in `$T` to the `Set-Date` cmdlet.</span></span>

```powershell
$T = Get-Date
Set-Date -Date $T
```

### <span data-ttu-id="138eb-129">Exemple 4 : ajouter 90 minutes à l’horloge système</span><span class="sxs-lookup"><span data-stu-id="138eb-129">Example 4: Add 90 minutes to the system clock</span></span>

<span data-ttu-id="138eb-130">Ces commandes avancent de 90 minutes l'heure système sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="138eb-130">These commands advance the system time on the local computer by 90 minutes.</span></span>

<span data-ttu-id="138eb-131">La première commande utilise l' `New-TimeSpan` applet de commande pour créer un objet **TimeSpan** avec un intervalle de 90 minutes, puis l’enregistre dans la `$90mins` variable.</span><span class="sxs-lookup"><span data-stu-id="138eb-131">The first command uses the `New-TimeSpan` cmdlet to create a **TimeSpan** object with a 90-minute interval, and saves it in the `$90mins` variable.</span></span>

<span data-ttu-id="138eb-132">La deuxième commande utilise le paramètre **Adjust** de `Set-Date` pour ajuster la date en utilisant la valeur de l’objet **TimeSpan** dans la `$90mins` variable.</span><span class="sxs-lookup"><span data-stu-id="138eb-132">The second command uses the **Adjust** parameter of `Set-Date` to adjust the date by the value of the **TimeSpan** object in the `$90mins` variable.</span></span>

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## <span data-ttu-id="138eb-133">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="138eb-133">PARAMETERS</span></span>

### <span data-ttu-id="138eb-134">-Ajuster</span><span class="sxs-lookup"><span data-stu-id="138eb-134">-Adjust</span></span>

<span data-ttu-id="138eb-135">Spécifie la valeur que cette applet de commande ajoute ou soustrait de la date et de l’heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="138eb-135">Specifies the value for which this cmdlet adds or subtracts from the current date and time.</span></span>
<span data-ttu-id="138eb-136">peut taper un ajustement au format de date et d’heure standard pour vos paramètres régionaux ou utiliser le paramètre **Adjust** pour passer un objet **TimeSpan** de `New-TimeSpan` à `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="138eb-136">can type an adjustment in standard date and time format for your locale or use the **Adjust** parameter to pass a **TimeSpan** object from `New-TimeSpan` to `Set-Date`.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="138eb-137">-Date</span><span class="sxs-lookup"><span data-stu-id="138eb-137">-Date</span></span>

<span data-ttu-id="138eb-138">Modifie la date et l'heure en leur affectant les valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="138eb-138">Changes the date and time to the specified values.</span></span>
<span data-ttu-id="138eb-139">Vous pouvez taper une nouvelle date au format de date courte et une heure au format d'heure standard correspondant aux paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="138eb-139">You can type a new date in the short date format and a time in the standard time format for your locale.</span></span> <span data-ttu-id="138eb-140">Ou, vous pouvez passer un objet **DateTime** à partir de `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="138eb-140">Or, you can pass a **DateTime** object from `Get-Date`.</span></span>

<span data-ttu-id="138eb-141">Si vous spécifiez une date, mais pas une heure, `Set-Date` remplace l’heure par minuit à la date spécifiée.</span><span class="sxs-lookup"><span data-stu-id="138eb-141">If you specify a date, but not a time, `Set-Date` changes the time to midnight on the specified date.</span></span> <span data-ttu-id="138eb-142">Si vous spécifiez uniquement une heure, la date n'est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="138eb-142">If you specify only a time, it does not change the date.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="138eb-143">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="138eb-143">-DisplayHint</span></span>

<span data-ttu-id="138eb-144">Spécifie les éléments de la date et de l’heure affichés. Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="138eb-144">Specifies which elements of the date and time are displayed.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="138eb-145">**Date** : affiche uniquement la date.</span><span class="sxs-lookup"><span data-stu-id="138eb-145">**Date** - displays only the date.</span></span>
- <span data-ttu-id="138eb-146">**Time** : affiche uniquement l’heure.</span><span class="sxs-lookup"><span data-stu-id="138eb-146">**Time** - displays only the time.</span></span>
- <span data-ttu-id="138eb-147">**DateTime** : affiche la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="138eb-147">**DateTime** - displays the date and time.</span></span>

<span data-ttu-id="138eb-148">Ce paramètre affecte uniquement l'affichage.</span><span class="sxs-lookup"><span data-stu-id="138eb-148">This parameter affects only the display.</span></span>
<span data-ttu-id="138eb-149">Elle n’affecte pas l’objet **DateTime** que `Get-Date` récupère.</span><span class="sxs-lookup"><span data-stu-id="138eb-149">It does not affect the **DateTime** object that `Get-Date` retrieves.</span></span>

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

### <span data-ttu-id="138eb-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="138eb-150">-Confirm</span></span>

<span data-ttu-id="138eb-151">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="138eb-151">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="138eb-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="138eb-152">-WhatIf</span></span>

<span data-ttu-id="138eb-153">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="138eb-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="138eb-154">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="138eb-154">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="138eb-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="138eb-155">CommonParameters</span></span>

<span data-ttu-id="138eb-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="138eb-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="138eb-157">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="138eb-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="138eb-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="138eb-158">INPUTS</span></span>

### <span data-ttu-id="138eb-159">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="138eb-159">System.DateTime</span></span>

<span data-ttu-id="138eb-160">Vous pouvez diriger une date vers `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="138eb-160">You can pipe a date to `Set-Date`.</span></span>

## <span data-ttu-id="138eb-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="138eb-161">OUTPUTS</span></span>

### <span data-ttu-id="138eb-162">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="138eb-162">System.DateTime</span></span>

<span data-ttu-id="138eb-163">`Set-Date` retourne un objet qui représente la date à laquelle il est défini.</span><span class="sxs-lookup"><span data-stu-id="138eb-163">`Set-Date` returns an object that represents the date that it set.</span></span>

## <span data-ttu-id="138eb-164">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="138eb-164">NOTES</span></span>

- <span data-ttu-id="138eb-165">Utilisez cette applet de commande avec précaution lors de la modification de la date et de l’heure sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="138eb-165">Use this cmdlet cautiously when changing the date and time on the computer.</span></span> <span data-ttu-id="138eb-166">la modification peut empêcher l'ordinateur de recevoir des mises à jour et des événements système qui sont déclenchés par une date ou une heure.</span><span class="sxs-lookup"><span data-stu-id="138eb-166">The change might prevent the computer from receiving system-wide events and updates that are triggered by a date or time.</span></span> <span data-ttu-id="138eb-167">Utilisez les paramètres **WhatIf** et **Confirm** pour éviter les erreurs.</span><span class="sxs-lookup"><span data-stu-id="138eb-167">Use the **WhatIf** and **Confirm** parameters to avoid errors.</span></span>
- <span data-ttu-id="138eb-168">Vous pouvez utiliser des méthodes .NET standard avec les objets **DateTime** et **TimeSpan** utilisés avec `Set-Date` , tels que **AddDays** , **AddMonths** et **FromFileTime**.</span><span class="sxs-lookup"><span data-stu-id="138eb-168">You can use standard .NET methods with the **DateTime** and **TimeSpan** objects used with `Set-Date`, such as **AddDays** , **AddMonths** , and **FromFileTime**.</span></span> <span data-ttu-id="138eb-169">Pour plus d’informations, consultez [DateTime, méthodes](/dotnet/api/system.datetime) et</span><span class="sxs-lookup"><span data-stu-id="138eb-169">For more information, see [DateTime Methods](/dotnet/api/system.datetime) and</span></span>

  <span data-ttu-id="138eb-170">Les [méthodes TimeSpan](/dotnet/api/system.timespan) dans le kit de développement logiciel (SDK) .net.</span><span class="sxs-lookup"><span data-stu-id="138eb-170">[TimeSpan Methods](/dotnet/api/system.timespan) in the .NET SDK.</span></span>

## <span data-ttu-id="138eb-171">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="138eb-171">RELATED LINKS</span></span>

[<span data-ttu-id="138eb-172">Obtient la date</span><span class="sxs-lookup"><span data-stu-id="138eb-172">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="138eb-173">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="138eb-173">New-TimeSpan</span></span>](New-TimeSpan.md)
