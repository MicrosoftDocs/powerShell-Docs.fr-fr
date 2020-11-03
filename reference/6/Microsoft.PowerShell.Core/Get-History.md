---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: 773e7e8d61e0f6158b4501b9c0b23826cbb10820
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "93206369"
---
# <span data-ttu-id="8624c-103">Get-History</span><span class="sxs-lookup"><span data-stu-id="8624c-103">Get-History</span></span>

## <span data-ttu-id="8624c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8624c-104">SYNOPSIS</span></span>
<span data-ttu-id="8624c-105">Obtient une liste des commandes entrées pendant la session active.</span><span class="sxs-lookup"><span data-stu-id="8624c-105">Gets a list of the commands entered during the current session.</span></span>

## <span data-ttu-id="8624c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8624c-106">SYNTAX</span></span>

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="8624c-107">Description</span><span class="sxs-lookup"><span data-stu-id="8624c-107">DESCRIPTION</span></span>

<span data-ttu-id="8624c-108">L' `Get-History` applet de commande obtient l’historique de session, autrement dit, la liste des commandes entrées pendant la session active.</span><span class="sxs-lookup"><span data-stu-id="8624c-108">The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="8624c-109">PowerShell gère automatiquement un historique de chaque session.</span><span class="sxs-lookup"><span data-stu-id="8624c-109">PowerShell automatically maintains a history of each session.</span></span> <span data-ttu-id="8624c-110">Le nombre d’entrées dans l’historique de session est déterminé par la valeur de la `$MaximumHistoryCount` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="8624c-110">The number of entries in the session history is determined by the value of the `$MaximumHistoryCount` preference variable.</span></span> <span data-ttu-id="8624c-111">À compter de Windows PowerShell 3,0, la valeur par défaut est `4096` .</span><span class="sxs-lookup"><span data-stu-id="8624c-111">Beginning in Windows PowerShell 3.0, the default value is `4096`.</span></span> <span data-ttu-id="8624c-112">Par défaut, les fichiers d'historique sont enregistrés dans le répertoire de base, mais vous pouvez enregistrer le fichier à n'importe quel emplacement.</span><span class="sxs-lookup"><span data-stu-id="8624c-112">By default, history files are saved in the home directory, but you can save the file in any location.</span></span> <span data-ttu-id="8624c-113">Pour plus d’informations sur les fonctionnalités de l’historique dans PowerShell, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="8624c-113">For more information about the history features in PowerShell, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="8624c-114">L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="8624c-114">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="8624c-115">Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé.</span><span class="sxs-lookup"><span data-stu-id="8624c-115">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="8624c-116">Cette applet de commande fonctionne uniquement avec l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="8624c-116">This cmdlet only works with the session history.</span></span> <span data-ttu-id="8624c-117">Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="8624c-117">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="8624c-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8624c-118">EXAMPLES</span></span>

### <span data-ttu-id="8624c-119">Exemple 1 : afficher l’historique de la session</span><span class="sxs-lookup"><span data-stu-id="8624c-119">Example 1: Get the session history</span></span>

<span data-ttu-id="8624c-120">Cet exemple obtient les entrées de l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="8624c-120">This example gets the entries in the session history.</span></span> <span data-ttu-id="8624c-121">L’affichage par défaut montre chaque commande et son ID, qui indique l’ordre dans lequel elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="8624c-121">The default display shows each command and its ID, which indicates the order in which they ran.</span></span>

```powershell
Get-History
```

### <span data-ttu-id="8624c-122">Exemple 2 : obtenir des entrées qui incluent une chaîne</span><span class="sxs-lookup"><span data-stu-id="8624c-122">Example 2: Get entries that include a string</span></span>

<span data-ttu-id="8624c-123">Cet exemple obtient les entrées de l’historique de commandes qui incluent le service de chaîne.</span><span class="sxs-lookup"><span data-stu-id="8624c-123">This example gets entries in the command history that include the string service.</span></span> <span data-ttu-id="8624c-124">La première commande obtient toutes les entrées de l'historique de session.</span><span class="sxs-lookup"><span data-stu-id="8624c-124">The first command gets all entries in the session history.</span></span> <span data-ttu-id="8624c-125">L’opérateur de pipeline ( `|` ) passe les résultats à l' `Where-Object` applet de commande, qui sélectionne uniquement les commandes qui incluent le service.</span><span class="sxs-lookup"><span data-stu-id="8624c-125">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects only the commands that include service.</span></span>

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### <span data-ttu-id="8624c-126">Exemple 3 : exporter les entrées de l’historique jusqu’à un ID spécifique</span><span class="sxs-lookup"><span data-stu-id="8624c-126">Example 3: Export history entries up to a specific ID</span></span>

<span data-ttu-id="8624c-127">Cet exemple obtient les cinq entrées d’historique les plus récentes se terminant par l’entrée 7.</span><span class="sxs-lookup"><span data-stu-id="8624c-127">This example gets the five most recent history entries ending with entry 7.</span></span> <span data-ttu-id="8624c-128">L’opérateur de pipeline passe le résultat à l’applet de commande `Export-Csv` , qui met en forme l’historique sous forme de texte séparé par des virgules et l’enregistre dans le fichier History.csv.</span><span class="sxs-lookup"><span data-stu-id="8624c-128">The pipeline operator passes the result to the `Export-Csv` cmdlet, which formats the history as comma-separated text and saves it in the History.csv file.</span></span> <span data-ttu-id="8624c-129">Le fichier comprend les données qui s’affichent lorsque vous mettez en forme l’historique sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="8624c-129">The file includes the data that is displayed when you format the history as a list.</span></span> <span data-ttu-id="8624c-130">Cela comprend l’État et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="8624c-130">This includes the status and start and end times of the command.</span></span>

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### <span data-ttu-id="8624c-131">Exemple 4 : afficher la commande la plus récente</span><span class="sxs-lookup"><span data-stu-id="8624c-131">Example 4: Display the most recent command</span></span>

<span data-ttu-id="8624c-132">Cet exemple obtient la dernière commande de l’historique de commande.</span><span class="sxs-lookup"><span data-stu-id="8624c-132">This example gets the last command in the command history.</span></span> <span data-ttu-id="8624c-133">La dernière commande est la dernière commande entrée.</span><span class="sxs-lookup"><span data-stu-id="8624c-133">The last command is the most recently entered command.</span></span> <span data-ttu-id="8624c-134">Cette commande utilise le paramètre **Count** pour afficher une seule commande.</span><span class="sxs-lookup"><span data-stu-id="8624c-134">This command uses the **Count** parameter to display just one command.</span></span> <span data-ttu-id="8624c-135">Par défaut, `Get-History` obtient les commandes les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="8624c-135">By default, `Get-History` gets the most recent commands.</span></span> <span data-ttu-id="8624c-136">Cette commande peut être abrégée en « h -c 1 » et équivaut à appuyer sur la touche flèche vers le haut.</span><span class="sxs-lookup"><span data-stu-id="8624c-136">This command can be abbreviated to "h -c 1" and is equivalent to pressing the up-arrow key.</span></span>

```powershell
Get-History -Count 1
```

### <span data-ttu-id="8624c-137">Exemple 5 : afficher toutes les propriétés des entrées de l’historique</span><span class="sxs-lookup"><span data-stu-id="8624c-137">Example 5: Display all the properties of the entries in the history</span></span>

<span data-ttu-id="8624c-138">Cet exemple affiche toutes les propriétés des entrées de l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="8624c-138">This example displays all of the properties of entries in the session history.</span></span> <span data-ttu-id="8624c-139">L’opérateur de pipeline passe les résultats d’une `Get-History` commande à l’applet de commande `Format-List` , qui affiche toutes les propriétés de chaque entrée d’historique.</span><span class="sxs-lookup"><span data-stu-id="8624c-139">The pipeline operator passes the results of a `Get-History` command to the `Format-List` cmdlet, which displays all of the properties of each history entry.</span></span> <span data-ttu-id="8624c-140">Cela comprend l’ID, l’État et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="8624c-140">This includes the ID, status, and start and end times of the command.</span></span>

```powershell
Get-History | Format-List -Property *
```

## <span data-ttu-id="8624c-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8624c-141">PARAMETERS</span></span>

### <span data-ttu-id="8624c-142">-Nombre</span><span class="sxs-lookup"><span data-stu-id="8624c-142">-Count</span></span>

<span data-ttu-id="8624c-143">Spécifie le nombre d’entrées d’historique les plus récentes que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="8624c-143">Specifies the number of the most recent history entries that this cmdlet gets.</span></span> <span data-ttu-id="8624c-144">Par défaut, `Get-History` obtient toutes les entrées dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="8624c-144">By, default, `Get-History` gets all entries in the session history.</span></span> <span data-ttu-id="8624c-145">Si vous utilisez à la fois les paramètres **Count** et **Id** dans une commande, l'affichage se termine par la commande spécifiée par le paramètre **Id** .</span><span class="sxs-lookup"><span data-stu-id="8624c-145">If you use both the **Count** and **Id** parameters in a command, the display ends with the command that is specified by the **Id** parameter.</span></span>

<span data-ttu-id="8624c-146">Dans Windows PowerShell 2,0, par défaut, `Get-History` obtient les inscriptions les plus récentes de 32.</span><span class="sxs-lookup"><span data-stu-id="8624c-146">In Windows PowerShell 2.0, by default, `Get-History` gets the 32 most recent entries.</span></span>

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

### <span data-ttu-id="8624c-147">-Id</span><span class="sxs-lookup"><span data-stu-id="8624c-147">-Id</span></span>

<span data-ttu-id="8624c-148">Spécifie un tableau des ID d’entrées dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="8624c-148">Specifies an array of the IDs of entries in the session history.</span></span> <span data-ttu-id="8624c-149">`Get-History` Obtient uniquement les entrées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="8624c-149">`Get-History` gets only specified entries.</span></span> <span data-ttu-id="8624c-150">Si vous utilisez à la fois les paramètres **ID** et **Count** dans une commande, `Get-History` obtient les entrées les plus récentes se terminant par l’entrée spécifiée par le paramètre **ID** .</span><span class="sxs-lookup"><span data-stu-id="8624c-150">If you use both the **Id** and **Count** parameters in a command, `Get-History` gets the most recent entries ending with the entry specified by the **Id** parameter.</span></span>

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

### <span data-ttu-id="8624c-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8624c-151">CommonParameters</span></span>

<span data-ttu-id="8624c-152">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8624c-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8624c-153">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8624c-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8624c-154">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8624c-154">INPUTS</span></span>

### <span data-ttu-id="8624c-155">System.Int64</span><span class="sxs-lookup"><span data-stu-id="8624c-155">System.Int64</span></span>

<span data-ttu-id="8624c-156">Vous pouvez diriger un ID d’historique vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8624c-156">You can pipe a history ID to this cmdlet.</span></span>

## <span data-ttu-id="8624c-157">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8624c-157">OUTPUTS</span></span>

### <span data-ttu-id="8624c-158">Microsoft. PowerShell. Commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="8624c-158">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="8624c-159">Cette applet de commande retourne un objet d’historique pour chaque élément de l’historique qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="8624c-159">This cmdlet returns a history object for each history item that it gets.</span></span>

## <span data-ttu-id="8624c-160">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8624c-160">NOTES</span></span>

<span data-ttu-id="8624c-161">L'historique de session est une liste des commandes entrées pendant la session.</span><span class="sxs-lookup"><span data-stu-id="8624c-161">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="8624c-162">L’historique de session représente l’ordre d’exécution, l’État et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="8624c-162">The session history represents the run order, the status, and the start and end times of the command.</span></span> <span data-ttu-id="8624c-163">Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser.</span><span class="sxs-lookup"><span data-stu-id="8624c-163">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="8624c-164">Pour plus d’informations sur l’historique des commandes, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="8624c-164">For more information about the command history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="8624c-165">À compter de Windows PowerShell 3,0, la valeur par défaut de la `$MaximumHistoryCount` variable de préférence est `4096` .</span><span class="sxs-lookup"><span data-stu-id="8624c-165">Starting in Windows PowerShell 3.0, the default value of the `$MaximumHistoryCount` preference variable is `4096`.</span></span> <span data-ttu-id="8624c-166">Dans Windows PowerShell 2,0, la valeur par défaut est `64` .</span><span class="sxs-lookup"><span data-stu-id="8624c-166">In Windows PowerShell 2.0, the default value is `64`.</span></span> <span data-ttu-id="8624c-167">Pour plus d’informations sur la `$MaximumHistoryCount` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8624c-167">For more information about the `$MaximumHistoryCount` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="8624c-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8624c-168">RELATED LINKS</span></span>

[<span data-ttu-id="8624c-169">Add-History</span><span class="sxs-lookup"><span data-stu-id="8624c-169">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="8624c-170">Clear-History</span><span class="sxs-lookup"><span data-stu-id="8624c-170">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="8624c-171">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="8624c-171">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="8624c-172">about_History</span><span class="sxs-lookup"><span data-stu-id="8624c-172">about_History</span></span>](About/about_History.md)
