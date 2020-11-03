---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: bbc5b6590dc97413350c19c91dbca0b4d08e9bce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202113"
---
# <span data-ttu-id="e7925-103">Add-History</span><span class="sxs-lookup"><span data-stu-id="e7925-103">Add-History</span></span>

## <span data-ttu-id="e7925-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e7925-104">SYNOPSIS</span></span>
<span data-ttu-id="e7925-105">Ajoute des entrées à l'historique de session.</span><span class="sxs-lookup"><span data-stu-id="e7925-105">Appends entries to the session history.</span></span>

## <span data-ttu-id="e7925-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e7925-106">SYNTAX</span></span>

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## <span data-ttu-id="e7925-107">Description</span><span class="sxs-lookup"><span data-stu-id="e7925-107">DESCRIPTION</span></span>

<span data-ttu-id="e7925-108">L' `Add-History` applet de commande ajoute des entrées à la fin de l’historique de session, autrement dit, la liste des commandes entrées pendant la session active.</span><span class="sxs-lookup"><span data-stu-id="e7925-108">The `Add-History` cmdlet adds entries to the end of the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="e7925-109">L'historique de session est une liste des commandes entrées pendant la session.</span><span class="sxs-lookup"><span data-stu-id="e7925-109">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="e7925-110">L'historique de session représente l'ordre d'exécution, l'état et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="e7925-110">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="e7925-111">Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser.</span><span class="sxs-lookup"><span data-stu-id="e7925-111">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="e7925-112">Pour plus d’informations sur l’historique de session, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="e7925-112">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="e7925-113">L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="e7925-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="e7925-114">Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé.</span><span class="sxs-lookup"><span data-stu-id="e7925-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="e7925-115">Cette applet de commande fonctionne uniquement avec l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="e7925-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="e7925-116">Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="e7925-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

<span data-ttu-id="e7925-117">Vous pouvez utiliser l' `Get-History` applet de commande pour obtenir les commandes et les passer à `Add-History` , ou vous pouvez exporter les commandes vers un fichier CSV ou XML, puis importer les commandes et transmettre le fichier importé à `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="e7925-117">You can use the `Get-History` cmdlet to get the commands and pass them to `Add-History`, or you can export the commands to a CSV or XML file, then import the commands, and pass the imported file to `Add-History`.</span></span> <span data-ttu-id="e7925-118">Vous pouvez utiliser cette applet de commande pour ajouter des commandes spécifiques à l'historique ou pour créer un fichier d'historique unique qui inclut des commandes issues de plusieurs sessions.</span><span class="sxs-lookup"><span data-stu-id="e7925-118">You can use this cmdlet to add specific commands to the history or to create a single history file that includes commands from more than one session.</span></span>

## <span data-ttu-id="e7925-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e7925-119">EXAMPLES</span></span>

### <span data-ttu-id="e7925-120">Exemple 1 : ajouter des commandes à l’historique d’une autre session</span><span class="sxs-lookup"><span data-stu-id="e7925-120">Example 1: Add commands to the history of a different session</span></span>

<span data-ttu-id="e7925-121">Cet exemple ajoute les commandes entrées dans une session PowerShell à l’historique d’une autre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7925-121">This example add the commands typed in one PowerShell session to the history of a different PowerShell session.</span></span>

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

<span data-ttu-id="e7925-122">La première commande récupère les objets qui représentent les commandes dans l’historique et les exporte dans le `History.csv` fichier.</span><span class="sxs-lookup"><span data-stu-id="e7925-122">The first command gets objects representing the commands in the history and exports them to the `History.csv` file.</span></span>

<span data-ttu-id="e7925-123">La seconde commande est entrée sur la ligne de commande d'une autre session.</span><span class="sxs-lookup"><span data-stu-id="e7925-123">The second command is typed at the command line of a different session.</span></span> <span data-ttu-id="e7925-124">Elle utilise l' `Import-Csv` applet de commande pour importer les objets dans le `History.csv` fichier.</span><span class="sxs-lookup"><span data-stu-id="e7925-124">It uses the `Import-Csv` cmdlet to import the objects in the `History.csv` file.</span></span> <span data-ttu-id="e7925-125">L’opérateur de pipeline ( `|` ) passe les objets à l' `Add-History` applet de commande, ce qui ajoute les objets représentant les commandes du `History.csv` fichier à l’historique de session actuel.</span><span class="sxs-lookup"><span data-stu-id="e7925-125">The pipeline operator (`|`) passes the objects to the `Add-History` cmdlet, which adds the objects representing the commands in the `History.csv` file to the current session history.</span></span>

### <span data-ttu-id="e7925-126">Exemple 2 : importer et exécuter des commandes</span><span class="sxs-lookup"><span data-stu-id="e7925-126">Example 2: Import and run commands</span></span>

<span data-ttu-id="e7925-127">Cet exemple importe des commandes à partir du `History.xml` fichier, les ajoute à l’historique de session actuel, puis exécute les commandes dans l’historique combiné.</span><span class="sxs-lookup"><span data-stu-id="e7925-127">This example imports commands from the `History.xml` file, adds them to the current session history, and then runs the commands in the combined history.</span></span>

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

<span data-ttu-id="e7925-128">La première commande utilise l' `Import-Clixml` applet de commande pour importer un historique de commandes qui a été exporté dans le `History.xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="e7925-128">The first command uses the `Import-Clixml` cmdlet to import a command history that was exported to the `History.xml` file.</span></span> <span data-ttu-id="e7925-129">L’opérateur de pipeline passe les commandes à l’applet de commande `Add-History` , qui ajoute les commandes à l’historique de session actuel.</span><span class="sxs-lookup"><span data-stu-id="e7925-129">The pipeline operator passes the commands to the `Add-History` cmdlet, which adds the commands to the current session history.</span></span> <span data-ttu-id="e7925-130">Le paramètre **PassThru** passe les objets représentant les commandes ajoutées dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="e7925-130">The **PassThru** parameter passes the objects representing the added commands down the pipeline.</span></span>

<span data-ttu-id="e7925-131">La commande utilise ensuite l' `ForEach-Object` applet de commande pour appliquer la `Invoke-History` commande à chacune des commandes de l’historique combiné.</span><span class="sxs-lookup"><span data-stu-id="e7925-131">The command then uses the `ForEach-Object` cmdlet to apply the `Invoke-History` command to each of the commands in the combined history.</span></span> <span data-ttu-id="e7925-132">La `Invoke-History` commande est mise en forme comme un bloc de script, placé entre accolades ( `{}` ), comme requis par le paramètre **Process** de l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="e7925-132">The `Invoke-History` command is formatted as a script block, enclosed in braces (`{}`), as required by the **Process** parameter of the `ForEach-Object` cmdlet.</span></span>

### <span data-ttu-id="e7925-133">Exemple 3 : ajouter des commandes dans l’historique à la fin de l’historique</span><span class="sxs-lookup"><span data-stu-id="e7925-133">Example 3: Add commands in the history to the end of the history</span></span>

<span data-ttu-id="e7925-134">Cet exemple ajoute les cinq premières commandes dans l’historique à la fin de la liste d’historique.</span><span class="sxs-lookup"><span data-stu-id="e7925-134">This example adds the first five commands in the history to the end of the history list.</span></span>

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

<span data-ttu-id="e7925-135">L' `Get-History` applet de commande obtient les cinq commandes se terminant par la commande 5.</span><span class="sxs-lookup"><span data-stu-id="e7925-135">The `Get-History` cmdlet gets the five commands ending in command 5.</span></span> <span data-ttu-id="e7925-136">L’opérateur de pipeline les transmet à l’applet de commande `Add-History` , qui les ajoute à l’historique actuel.</span><span class="sxs-lookup"><span data-stu-id="e7925-136">The pipeline operator passes them to the `Add-History` cmdlet, which appends them to the current history.</span></span> <span data-ttu-id="e7925-137">La `Add-History` commande n’inclut aucun paramètre, mais PowerShell associe les objets transmis via le pipeline au paramètre **InputObject** de `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="e7925-137">The `Add-History` command does not include any parameters, but PowerShell associates the objects passed through the pipeline with the **InputObject** parameter of `Add-History`.</span></span>

### <span data-ttu-id="e7925-138">Exemple 4 : ajouter des commandes dans un fichier. csv à l’historique actuel</span><span class="sxs-lookup"><span data-stu-id="e7925-138">Example 4: Add commands in a .csv file to the current history</span></span>

<span data-ttu-id="e7925-139">Cet exemple ajoute les commandes du `History.csv` fichier à l’historique de session actuel.</span><span class="sxs-lookup"><span data-stu-id="e7925-139">This example add the commands in the `History.csv` file to the current session history.</span></span>

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

<span data-ttu-id="e7925-140">L' `Import-Csv` applet de commande importe les commandes dans le `History.csv` fichier et stocke son contenu dans la variable `$a` .</span><span class="sxs-lookup"><span data-stu-id="e7925-140">The `Import-Csv` cmdlet imports the commands in the `History.csv` file and store its contents in the variable `$a`.</span></span>

<span data-ttu-id="e7925-141">La deuxième commande utilise l' `Add-History` applet de commande pour ajouter les commandes de `History.csv` à l’historique de session actuel.</span><span class="sxs-lookup"><span data-stu-id="e7925-141">The second command uses the `Add-History` cmdlet to add the commands from `History.csv` to the current session history.</span></span> <span data-ttu-id="e7925-142">Elle utilise le paramètre **InputObject** pour spécifier la `$a` variable et le paramètre **PassThru** pour générer un objet à afficher sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e7925-142">It uses the **InputObject** parameter to specify the `$a` variable and the **PassThru** parameter to generate an object to display at the command line.</span></span> <span data-ttu-id="e7925-143">Sans le paramètre **PassThru** , l' `Add-History` applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="e7925-143">Without the **PassThru** parameter, the `Add-History` cmdlet does not generate any output.</span></span>

### <span data-ttu-id="e7925-144">Exemple 5 : ajouter des commandes dans un fichier. XML à l’historique actuel</span><span class="sxs-lookup"><span data-stu-id="e7925-144">Example 5: Add commands in an .xml file to the current history</span></span>

<span data-ttu-id="e7925-145">Cet exemple ajoute les commandes du `history.xml` fichier à l’historique de session actuel.</span><span class="sxs-lookup"><span data-stu-id="e7925-145">This example adds the commands in the `history.xml` file to the current session history.</span></span>

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

<span data-ttu-id="e7925-146">Le paramètre **InputObject** passe les résultats de la commande entre parenthèses à l' `Add-History` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e7925-146">The **InputObject** parameter passes the results of the command in parentheses to the `Add-History` cmdlet.</span></span> <span data-ttu-id="e7925-147">La commande entre parenthèses, qui est exécutée en premier, importe le `history.xml` fichier dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7925-147">The command in parentheses, which is executed first, imports the `history.xml` file into PowerShell.</span></span> <span data-ttu-id="e7925-148">L' `Add-History` applet de commande ajoute ensuite les commandes du fichier à l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="e7925-148">The `Add-History` cmdlet then adds the commands in the file to the session history.</span></span>

## <span data-ttu-id="e7925-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e7925-149">PARAMETERS</span></span>

### <span data-ttu-id="e7925-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e7925-150">-InputObject</span></span>

<span data-ttu-id="e7925-151">Spécifie un tableau d’entrées à ajouter à l’historique en tant qu’objet **HistoryInfo** dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="e7925-151">Specifies an array of entries to add to the history as **HistoryInfo** object to the session history.</span></span>
<span data-ttu-id="e7925-152">Vous pouvez utiliser ce paramètre pour envoyer un objet **HistoryInfo** , tel que ceux qui sont retournés par `Get-History` les `Import-Clixml` `Import-Csv` applets de commande, ou, à `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="e7925-152">You can use this parameter to submit a **HistoryInfo** object, such as the ones that are returned by the `Get-History`, `Import-Clixml`, or `Import-Csv` cmdlets, to `Add-History`.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e7925-153">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e7925-153">-Passthru</span></span>

<span data-ttu-id="e7925-154">Indique que cette applet de commande retourne un objet **HistoryInfo** pour chaque entrée d’historique.</span><span class="sxs-lookup"><span data-stu-id="e7925-154">Indicates that this cmdlet returns a **HistoryInfo** object for each history entry.</span></span> <span data-ttu-id="e7925-155">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="e7925-155">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e7925-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7925-156">CommonParameters</span></span>

<span data-ttu-id="e7925-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e7925-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7925-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e7925-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e7925-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e7925-159">INPUTS</span></span>

### <span data-ttu-id="e7925-160">Microsoft. PowerShell. Commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="e7925-160">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="e7925-161">Vous pouvez diriger un objet **HistoryInfo** vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e7925-161">You can pipe a **HistoryInfo** object to this cmdlet.</span></span>

## <span data-ttu-id="e7925-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e7925-162">OUTPUTS</span></span>

### <span data-ttu-id="e7925-163">None ou Microsoft. PowerShell. Commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="e7925-163">None or Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="e7925-164">Cette applet de commande retourne un objet **HistoryInfo** si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="e7925-164">This cmdlet returns a **HistoryInfo** object if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="e7925-165">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="e7925-165">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e7925-166">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e7925-166">NOTES</span></span>

<span data-ttu-id="e7925-167">L’historique de session est une liste des commandes entrées pendant la session avec l’ID.</span><span class="sxs-lookup"><span data-stu-id="e7925-167">The session history is a list of the commands entered during the session together with the ID.</span></span> <span data-ttu-id="e7925-168">L'historique de session représente l'ordre d'exécution, l'état et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="e7925-168">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="e7925-169">Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser.</span><span class="sxs-lookup"><span data-stu-id="e7925-169">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="e7925-170">Pour plus d’informations sur l’historique de session, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="e7925-170">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="e7925-171">Pour spécifier les commandes à ajouter à l'historique, utilisez le paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="e7925-171">To specify the commands to add to the history, use the **InputObject** parameter.</span></span> <span data-ttu-id="e7925-172">La `Add-History` commande accepte uniquement les objets **HistoryInfo** , tels que ceux retournés pour chaque commande par l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="e7925-172">The `Add-History` command accepts only **HistoryInfo** objects, such as those returned for each command by the `Get-History` cmdlet.</span></span> <span data-ttu-id="e7925-173">Vous ne pouvez pas lui passer un chemin d'accès et un nom de fichier, ni une liste de commandes.</span><span class="sxs-lookup"><span data-stu-id="e7925-173">You cannot pass it a path and file name or a list of commands.</span></span>

<span data-ttu-id="e7925-174">Vous pouvez utiliser le paramètre **InputObject** pour passer un fichier d’objets **HistoryInfo** à `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="e7925-174">You can use the **InputObject** parameter to pass a file of **HistoryInfo** objects to `Add-History`.</span></span> <span data-ttu-id="e7925-175">Pour ce faire, exportez les résultats d’une `Get-History` commande dans un fichier à l’aide de l’applet de commande `Export-Csv` ou `Export-Clixml` , puis importez le fichier à l’aide des `Import-Csv` applets de commande ou `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="e7925-175">To do so, export the results of a `Get-History` command to a file by using the `Export-Csv` or `Export-Clixml` cmdlet and then import the file by using the `Import-Csv` or `Import-Clixml` cmdlets.</span></span> <span data-ttu-id="e7925-176">Vous pouvez ensuite passer le fichier d’objets **HistoryInfo** importés à `Add-History` via un pipeline ou dans une variable.</span><span class="sxs-lookup"><span data-stu-id="e7925-176">You can then pass the file of imported **HistoryInfo** objects to `Add-History` through a pipeline or in a variable.</span></span> <span data-ttu-id="e7925-177">Pour plus d'informations, consultez les exemples.</span><span class="sxs-lookup"><span data-stu-id="e7925-177">For more information, see the examples.</span></span>

<span data-ttu-id="e7925-178">Le fichier d’objets **HistoryInfo** que vous transmettez à l’applet de commande `Add-History` doit inclure les informations de type, les en-têtes de colonne et toutes les propriétés des objets **HistoryInfo** .</span><span class="sxs-lookup"><span data-stu-id="e7925-178">The file of **HistoryInfo** objects that you pass to the `Add-History` cmdlet must include the type information, column headings, and all of the properties of the **HistoryInfo** objects.</span></span> <span data-ttu-id="e7925-179">Si vous envisagez de renvoyer les objets à `Add-History` , n’utilisez pas le paramètre **NoTypeInformation** de l’applet de commande `Export-Csv` et ne supprimez pas les informations de type, les en-têtes de colonne ni les champs dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="e7925-179">If you intend to pass the objects back to `Add-History`, do not use the **NoTypeInformation** parameter of the `Export-Csv` cmdlet and do not delete the type information, column headings, or any fields in the file.</span></span>

<span data-ttu-id="e7925-180">Pour modifier l’historique de session, exportez la session dans un fichier CSV ou XML, modifiez le fichier, importez le fichier et utilisez `Add-History` pour l’ajouter à l’historique de session actuel.</span><span class="sxs-lookup"><span data-stu-id="e7925-180">To modify the session history, export the session to a CSV or XML file, modify the file, import the file, and use `Add-History` to append it to the current session history.</span></span>

## <span data-ttu-id="e7925-181">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e7925-181">RELATED LINKS</span></span>

[<span data-ttu-id="e7925-182">Clear-History</span><span class="sxs-lookup"><span data-stu-id="e7925-182">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="e7925-183">Get-History</span><span class="sxs-lookup"><span data-stu-id="e7925-183">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="e7925-184">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="e7925-184">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="e7925-185">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="e7925-185">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="e7925-186">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="e7925-186">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="e7925-187">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="e7925-187">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)

