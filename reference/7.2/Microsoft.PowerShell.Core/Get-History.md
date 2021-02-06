---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: be47925211c57760ddbd0bd4c8e985e161d24593
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597326"
---
# <span data-ttu-id="e51f9-102">Get-History</span><span class="sxs-lookup"><span data-stu-id="e51f9-102">Get-History</span></span>

## <span data-ttu-id="e51f9-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e51f9-103">SYNOPSIS</span></span>
<span data-ttu-id="e51f9-104">Obtient une liste des commandes entrées pendant la session active.</span><span class="sxs-lookup"><span data-stu-id="e51f9-104">Gets a list of the commands entered during the current session.</span></span>

## <span data-ttu-id="e51f9-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="e51f9-105">SYNTAX</span></span>

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="e51f9-106">Description</span><span class="sxs-lookup"><span data-stu-id="e51f9-106">DESCRIPTION</span></span>

<span data-ttu-id="e51f9-107">L' `Get-History` applet de commande obtient l’historique de session, autrement dit, la liste des commandes entrées pendant la session active.</span><span class="sxs-lookup"><span data-stu-id="e51f9-107">The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="e51f9-108">PowerShell gère automatiquement un historique de chaque session.</span><span class="sxs-lookup"><span data-stu-id="e51f9-108">PowerShell automatically maintains a history of each session.</span></span> <span data-ttu-id="e51f9-109">Le nombre d’entrées dans l’historique de session est déterminé par la valeur de la `$MaximumHistoryCount` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="e51f9-109">The number of entries in the session history is determined by the value of the `$MaximumHistoryCount` preference variable.</span></span> <span data-ttu-id="e51f9-110">À compter de Windows PowerShell 3,0, la valeur par défaut est `4096` .</span><span class="sxs-lookup"><span data-stu-id="e51f9-110">Beginning in Windows PowerShell 3.0, the default value is `4096`.</span></span> <span data-ttu-id="e51f9-111">Par défaut, les fichiers d'historique sont enregistrés dans le répertoire de base, mais vous pouvez enregistrer le fichier à n'importe quel emplacement.</span><span class="sxs-lookup"><span data-stu-id="e51f9-111">By default, history files are saved in the home directory, but you can save the file in any location.</span></span> <span data-ttu-id="e51f9-112">Pour plus d’informations sur les fonctionnalités de l’historique dans PowerShell, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="e51f9-112">For more information about the history features in PowerShell, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="e51f9-113">L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="e51f9-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="e51f9-114">Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé.</span><span class="sxs-lookup"><span data-stu-id="e51f9-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="e51f9-115">Cette applet de commande fonctionne uniquement avec l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="e51f9-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="e51f9-116">Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="e51f9-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="e51f9-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e51f9-117">EXAMPLES</span></span>

### <span data-ttu-id="e51f9-118">Exemple 1 : afficher l’historique de la session</span><span class="sxs-lookup"><span data-stu-id="e51f9-118">Example 1: Get the session history</span></span>

<span data-ttu-id="e51f9-119">Cet exemple obtient les entrées de l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="e51f9-119">This example gets the entries in the session history.</span></span> <span data-ttu-id="e51f9-120">L’affichage par défaut montre chaque commande et son ID, qui indique l’ordre dans lequel elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="e51f9-120">The default display shows each command and its ID, which indicates the order in which they ran.</span></span>

```powershell
Get-History
```

### <span data-ttu-id="e51f9-121">Exemple 2 : obtenir des entrées qui incluent une chaîne</span><span class="sxs-lookup"><span data-stu-id="e51f9-121">Example 2: Get entries that include a string</span></span>

<span data-ttu-id="e51f9-122">Cet exemple obtient les entrées de l’historique de commandes qui incluent le service de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e51f9-122">This example gets entries in the command history that include the string service.</span></span> <span data-ttu-id="e51f9-123">La première commande obtient toutes les entrées de l'historique de session.</span><span class="sxs-lookup"><span data-stu-id="e51f9-123">The first command gets all entries in the session history.</span></span> <span data-ttu-id="e51f9-124">L’opérateur de pipeline ( `|` ) passe les résultats à l' `Where-Object` applet de commande, qui sélectionne uniquement les commandes qui incluent le service.</span><span class="sxs-lookup"><span data-stu-id="e51f9-124">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects only the commands that include service.</span></span>

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### <span data-ttu-id="e51f9-125">Exemple 3 : exporter les entrées de l’historique jusqu’à un ID spécifique</span><span class="sxs-lookup"><span data-stu-id="e51f9-125">Example 3: Export history entries up to a specific ID</span></span>

<span data-ttu-id="e51f9-126">Cet exemple obtient les cinq entrées d’historique les plus récentes se terminant par l’entrée 7.</span><span class="sxs-lookup"><span data-stu-id="e51f9-126">This example gets the five most recent history entries ending with entry 7.</span></span> <span data-ttu-id="e51f9-127">L’opérateur de pipeline passe le résultat à l’applet de commande `Export-Csv` , qui met en forme l’historique sous forme de texte séparé par des virgules et l’enregistre dans le fichier History.csv.</span><span class="sxs-lookup"><span data-stu-id="e51f9-127">The pipeline operator passes the result to the `Export-Csv` cmdlet, which formats the history as comma-separated text and saves it in the History.csv file.</span></span> <span data-ttu-id="e51f9-128">Le fichier comprend les données qui s’affichent lorsque vous mettez en forme l’historique sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="e51f9-128">The file includes the data that is displayed when you format the history as a list.</span></span> <span data-ttu-id="e51f9-129">Cela comprend l’État et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="e51f9-129">This includes the status and start and end times of the command.</span></span>

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### <span data-ttu-id="e51f9-130">Exemple 4 : afficher la commande la plus récente</span><span class="sxs-lookup"><span data-stu-id="e51f9-130">Example 4: Display the most recent command</span></span>

<span data-ttu-id="e51f9-131">Cet exemple obtient la dernière commande de l’historique de commande.</span><span class="sxs-lookup"><span data-stu-id="e51f9-131">This example gets the last command in the command history.</span></span> <span data-ttu-id="e51f9-132">La dernière commande est la dernière commande entrée.</span><span class="sxs-lookup"><span data-stu-id="e51f9-132">The last command is the most recently entered command.</span></span> <span data-ttu-id="e51f9-133">Cette commande utilise le paramètre **Count** pour afficher une seule commande.</span><span class="sxs-lookup"><span data-stu-id="e51f9-133">This command uses the **Count** parameter to display just one command.</span></span> <span data-ttu-id="e51f9-134">Par défaut, `Get-History` obtient les commandes les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="e51f9-134">By default, `Get-History` gets the most recent commands.</span></span> <span data-ttu-id="e51f9-135">Cette commande peut être abrégée en « h -c 1 » et équivaut à appuyer sur la touche flèche vers le haut.</span><span class="sxs-lookup"><span data-stu-id="e51f9-135">This command can be abbreviated to "h -c 1" and is equivalent to pressing the up-arrow key.</span></span>

```powershell
Get-History -Count 1
```

### <span data-ttu-id="e51f9-136">Exemple 5 : afficher toutes les propriétés des entrées de l’historique</span><span class="sxs-lookup"><span data-stu-id="e51f9-136">Example 5: Display all the properties of the entries in the history</span></span>

<span data-ttu-id="e51f9-137">Cet exemple affiche toutes les propriétés des entrées de l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="e51f9-137">This example displays all of the properties of entries in the session history.</span></span> <span data-ttu-id="e51f9-138">L’opérateur de pipeline passe les résultats d’une `Get-History` commande à l’applet de commande `Format-List` , qui affiche toutes les propriétés de chaque entrée d’historique.</span><span class="sxs-lookup"><span data-stu-id="e51f9-138">The pipeline operator passes the results of a `Get-History` command to the `Format-List` cmdlet, which displays all of the properties of each history entry.</span></span> <span data-ttu-id="e51f9-139">Cela comprend l’ID, l’État et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="e51f9-139">This includes the ID, status, and start and end times of the command.</span></span>

```powershell
Get-History | Format-List -Property *
```

## <span data-ttu-id="e51f9-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e51f9-140">PARAMETERS</span></span>

### <span data-ttu-id="e51f9-141">-Nombre</span><span class="sxs-lookup"><span data-stu-id="e51f9-141">-Count</span></span>

<span data-ttu-id="e51f9-142">Spécifie le nombre d’entrées d’historique les plus récentes que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="e51f9-142">Specifies the number of the most recent history entries that this cmdlet gets.</span></span> <span data-ttu-id="e51f9-143">Par défaut, `Get-History` obtient toutes les entrées dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="e51f9-143">By, default, `Get-History` gets all entries in the session history.</span></span> <span data-ttu-id="e51f9-144">Si vous utilisez à la fois les paramètres **Count** et **Id** dans une commande, l'affichage se termine par la commande spécifiée par le paramètre **Id**.</span><span class="sxs-lookup"><span data-stu-id="e51f9-144">If you use both the **Count** and **Id** parameters in a command, the display ends with the command that is specified by the **Id** parameter.</span></span>

<span data-ttu-id="e51f9-145">Dans Windows PowerShell 2,0, par défaut, `Get-History` obtient les inscriptions les plus récentes de 32.</span><span class="sxs-lookup"><span data-stu-id="e51f9-145">In Windows PowerShell 2.0, by default, `Get-History` gets the 32 most recent entries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e51f9-146">-Id</span><span class="sxs-lookup"><span data-stu-id="e51f9-146">-Id</span></span>

<span data-ttu-id="e51f9-147">Spécifie un tableau des ID d’entrées dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="e51f9-147">Specifies an array of the IDs of entries in the session history.</span></span> <span data-ttu-id="e51f9-148">`Get-History` Obtient uniquement les entrées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="e51f9-148">`Get-History` gets only specified entries.</span></span> <span data-ttu-id="e51f9-149">Si vous utilisez à la fois les paramètres **ID** et **Count** dans une commande, `Get-History` obtient les entrées les plus récentes se terminant par l’entrée spécifiée par le paramètre **ID** .</span><span class="sxs-lookup"><span data-stu-id="e51f9-149">If you use both the **Id** and **Count** parameters in a command, `Get-History` gets the most recent entries ending with the entry specified by the **Id** parameter.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e51f9-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e51f9-150">CommonParameters</span></span>

<span data-ttu-id="e51f9-151">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e51f9-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e51f9-152">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e51f9-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e51f9-153">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e51f9-153">INPUTS</span></span>

### <span data-ttu-id="e51f9-154">System.Int64</span><span class="sxs-lookup"><span data-stu-id="e51f9-154">System.Int64</span></span>

<span data-ttu-id="e51f9-155">Vous pouvez diriger un ID d’historique vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e51f9-155">You can pipe a history ID to this cmdlet.</span></span>

## <span data-ttu-id="e51f9-156">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e51f9-156">OUTPUTS</span></span>

### <span data-ttu-id="e51f9-157">Microsoft. PowerShell. Commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="e51f9-157">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="e51f9-158">Cette applet de commande retourne un objet d’historique pour chaque élément de l’historique qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="e51f9-158">This cmdlet returns a history object for each history item that it gets.</span></span>

## <span data-ttu-id="e51f9-159">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e51f9-159">NOTES</span></span>

<span data-ttu-id="e51f9-160">L'historique de session est une liste des commandes entrées pendant la session.</span><span class="sxs-lookup"><span data-stu-id="e51f9-160">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="e51f9-161">L’historique de session représente l’ordre d’exécution, l’État et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="e51f9-161">The session history represents the run order, the status, and the start and end times of the command.</span></span> <span data-ttu-id="e51f9-162">Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser.</span><span class="sxs-lookup"><span data-stu-id="e51f9-162">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="e51f9-163">Pour plus d’informations sur l’historique des commandes, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="e51f9-163">For more information about the command history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="e51f9-164">À compter de Windows PowerShell 3,0, la valeur par défaut de la `$MaximumHistoryCount` variable de préférence est `4096` .</span><span class="sxs-lookup"><span data-stu-id="e51f9-164">Starting in Windows PowerShell 3.0, the default value of the `$MaximumHistoryCount` preference variable is `4096`.</span></span> <span data-ttu-id="e51f9-165">Dans Windows PowerShell 2,0, la valeur par défaut est `64` .</span><span class="sxs-lookup"><span data-stu-id="e51f9-165">In Windows PowerShell 2.0, the default value is `64`.</span></span> <span data-ttu-id="e51f9-166">Pour plus d’informations sur la `$MaximumHistoryCount` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e51f9-166">For more information about the `$MaximumHistoryCount` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="e51f9-167">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e51f9-167">RELATED LINKS</span></span>

[<span data-ttu-id="e51f9-168">Add-History</span><span class="sxs-lookup"><span data-stu-id="e51f9-168">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="e51f9-169">Clear-History</span><span class="sxs-lookup"><span data-stu-id="e51f9-169">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="e51f9-170">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="e51f9-170">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="e51f9-171">about_History</span><span class="sxs-lookup"><span data-stu-id="e51f9-171">about_History</span></span>](About/about_History.md)
