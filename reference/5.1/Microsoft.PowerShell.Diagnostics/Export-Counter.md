---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/export-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Counter
ms.openlocfilehash: 54498eb504a1d13a5b96a2583b5e5d6e4c08735e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206674"
---
# <span data-ttu-id="f7b60-103">Export-Counter</span><span class="sxs-lookup"><span data-stu-id="f7b60-103">Export-Counter</span></span>

## <span data-ttu-id="f7b60-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f7b60-104">SYNOPSIS</span></span>
<span data-ttu-id="f7b60-105">Exporte les données des compteurs de performances dans les fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="f7b60-105">Exports performance counter data to log files.</span></span>

## <span data-ttu-id="f7b60-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7b60-106">SYNTAX</span></span>

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## <span data-ttu-id="f7b60-107">Description</span><span class="sxs-lookup"><span data-stu-id="f7b60-107">DESCRIPTION</span></span>

<span data-ttu-id="f7b60-108">L' `Export-Counter` applet de commande exporte les données du compteur de performance (objets PerformanceCounterSampleSet) dans les fichiers journaux au format journal de performances binaire (. BLG), de valeurs séparées par des virgules (. csv) ou de valeurs séparées par des tabulations (. TSV).</span><span class="sxs-lookup"><span data-stu-id="f7b60-108">The `Export-Counter` cmdlet exports performance counter data (PerformanceCounterSampleSet objects) to log files in binary performance log (.blg), comma-separated value (.csv), or tab-separated value (.tsv) format.</span></span> <span data-ttu-id="f7b60-109">Utilisez cette applet de commande pour consigner les données des compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="f7b60-109">You use this cmdlet to log performance counter data.</span></span>

<span data-ttu-id="f7b60-110">L' `Export-Counter` applet de commande est conçue pour exporter les données retournées par les `Get-Counter` applets de commande et `Import-Counter` .</span><span class="sxs-lookup"><span data-stu-id="f7b60-110">The `Export-Counter` cmdlet is designed to export data that is returned by the `Get-Counter` and `Import-Counter` cmdlets.</span></span>

<span data-ttu-id="f7b60-111">Cette applet de commande s’exécute uniquement sur Windows 7, Windows Server 2008 R2 et les versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="f7b60-111">This cmdlet runs only on Windows 7, Windows Server 2008 R2, and later versions of Windows.</span></span>

## <span data-ttu-id="f7b60-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f7b60-112">EXAMPLES</span></span>

### <span data-ttu-id="f7b60-113">EXEMPLE 1 : exporter des données de compteur dans un fichier</span><span class="sxs-lookup"><span data-stu-id="f7b60-113">EXAMPLE 1: Export counter data to a file</span></span>

<span data-ttu-id="f7b60-114">Cet exemple exporte des données de compteur dans un fichier BLG.</span><span class="sxs-lookup"><span data-stu-id="f7b60-114">This example exports counter data to a BLG file.</span></span>

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

<span data-ttu-id="f7b60-115">La commande utilise l' `Get-Counter` applet de commande pour collecter les données de temps processeur.</span><span class="sxs-lookup"><span data-stu-id="f7b60-115">The command uses the `Get-Counter` cmdlet to collect processor time data.</span></span> <span data-ttu-id="f7b60-116">Elle utilise un opérateur de pipeline (|) pour envoyer les données à l’applet de commande `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="f7b60-116">It uses a pipeline operator (|) to send the data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="f7b60-117">La `Export-Counter` commande utilise la variable **path** pour spécifier le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f7b60-117">The `Export-Counter` command uses the **Path** variable to specify the output file.</span></span>

<span data-ttu-id="f7b60-118">Étant donné que le jeu de données peut être très volumineux, cet exemple envoie les données vers `Export-Counter` via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="f7b60-118">Because the data set might be very large, this example sends the data to `Export-Counter` through the pipeline.</span></span> <span data-ttu-id="f7b60-119">Si les données ont été enregistrées dans une variable, vous pouvez utiliser une quantité disproportionnée de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f7b60-119">If the data were saved in a variable, you might use a disproportionate amount of memory.</span></span>

### <span data-ttu-id="f7b60-120">Exemple 2 : exporter un fichier vers un format de fichier de compteur</span><span class="sxs-lookup"><span data-stu-id="f7b60-120">Example 2: Export a file to a counter file format</span></span>

<span data-ttu-id="f7b60-121">Cet exemple convertit un fichier CSV en un format de données de compteur.</span><span class="sxs-lookup"><span data-stu-id="f7b60-121">This example converts a CSV file to a counter data BLG format.</span></span>

<span data-ttu-id="f7b60-122">L' `Import-Counter` applet de commande importe les données du compteur de performance à partir du `Threads.csv` fichier.</span><span class="sxs-lookup"><span data-stu-id="f7b60-122">The `Import-Counter` cmdlet imports performance counter data from the `Threads.csv` file.</span></span> <span data-ttu-id="f7b60-123">L’exemple suppose que ce fichier a été précédemment exporté à l’aide de l’applet de commande `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="f7b60-123">The example presumes that this file was previously exported by using the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="f7b60-124">Un opérateur de pipeline ( `|` ) envoie les données importées à l’applet de commande `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="f7b60-124">A pipeline operator (`|`) sends the imported data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="f7b60-125">La commande utilise le paramètre **Path** pour spécifier l'emplacement du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f7b60-125">The command uses the **Path** parameter to specify the location of the output file.</span></span> <span data-ttu-id="f7b60-126">Elle utilise les paramètres **circulaires** et **MaxSize** pour indiquer à l' `Export-Counter` applet de commande de créer un journal circulaire qui encapsule 1 Go.</span><span class="sxs-lookup"><span data-stu-id="f7b60-126">It uses the **Circular** and **MaxSize** parameters to direct the `Export-Counter` cmdlet to create a circular log that wraps at 1 GB.</span></span> <span data-ttu-id="f7b60-127">Le paramètre **MaxSize** est exprimé en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="f7b60-127">The **MaxSize** parameter is expressed in megabytes.</span></span>

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### <span data-ttu-id="f7b60-128">Exemple 3 : obtenir des données de compteur à partir d’un ordinateur distant et enregistrer les données dans un fichier</span><span class="sxs-lookup"><span data-stu-id="f7b60-128">Example 3: Get counter data from a remote computer and save the data to a file</span></span>

<span data-ttu-id="f7b60-129">Cet exemple montre comment obtenir les données de compteur de performances d'un ordinateur distant, et les enregistrer dans un fichier sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f7b60-129">This example shows how to get performance counter data from a remote computer and save the data in a file on the remote computer.</span></span>

<span data-ttu-id="f7b60-130">La première commande utilise l' `Get-Counter` applet de commande pour collecter les données de compteur de jeu de travail à partir de Serveur01, un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f7b60-130">The first command uses the `Get-Counter` cmdlet to collect working set counter data from Server01, a remote computer.</span></span> <span data-ttu-id="f7b60-131">La commande enregistre les données dans la `$C` variable.</span><span class="sxs-lookup"><span data-stu-id="f7b60-131">The command saves the data in the `$C` variable.</span></span>

<span data-ttu-id="f7b60-132">La deuxième commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données dans `$C` l’applet de commande `Export-Counter` , ce qui l’enregistre dans le `Workingset.blg` fichier du partage de performances de l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="f7b60-132">The second command uses a pipeline operator (`|`) to send the data in `$C` to the `Export-Counter` cmdlet, which saves it in the `Workingset.blg` file in the Perf share of the Server01 computer.</span></span>

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### <span data-ttu-id="f7b60-133">Exemple 4 : rejournalisation des données existantes</span><span class="sxs-lookup"><span data-stu-id="f7b60-133">Example 4: Re-log existing data</span></span>

<span data-ttu-id="f7b60-134">Cet exemple montre comment utiliser les `Import-Counter` applets de commande et `Export-Counter` pour rejournaliser les données existantes.</span><span class="sxs-lookup"><span data-stu-id="f7b60-134">This example shows how to use the `Import-Counter` and `Export-Counter` cmdlets to re-log existing data.</span></span>

<span data-ttu-id="f7b60-135">La première commande utilise l' `Import-Counter` applet de commande pour importer des données de compteur de performance à partir du journal de l’enregistrement de fichier. BLG.</span><span class="sxs-lookup"><span data-stu-id="f7b60-135">The first command uses the `Import-Counter` cmdlet to import performance counter data from the DiskSpace.blg log.</span></span> <span data-ttu-id="f7b60-136">Elle enregistre les données dans la `$All` variable.</span><span class="sxs-lookup"><span data-stu-id="f7b60-136">It saves the data in the `$All` variable.</span></span> <span data-ttu-id="f7b60-137">Ce fichier contient des exemples du compteur « \% espace libre du disque logique » sur plus de 200 ordinateurs distants dans l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f7b60-137">This file contains samples of the "LogicalDisk\% Free Space" counter on more than 200 remote computers in the enterprise.</span></span>

<span data-ttu-id="f7b60-138">La deuxième commande utilise l' `Where-Object` applet de commande pour sélectionner des objets dont le **CookedValue** est inférieur à 15 (en pourcentage).</span><span class="sxs-lookup"><span data-stu-id="f7b60-138">The second command uses the `Where-Object` cmdlet to select objects with **CookedValue** of less than 15 (percent).</span></span> <span data-ttu-id="f7b60-139">La commande enregistre les résultats dans la `$LowSpace` variable.</span><span class="sxs-lookup"><span data-stu-id="f7b60-139">The command saves the results in the `$LowSpace` variable.</span></span>

<span data-ttu-id="f7b60-140">La troisième commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données de la `$LowSpace` variable à l’applet de commande `Export-Counter` .</span><span class="sxs-lookup"><span data-stu-id="f7b60-140">The third command uses a pipeline operator (`|`) to send the data in the `$LowSpace` variable to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="f7b60-141">La commande utilise le paramètre **Path** pour indiquer que les données sélectionnées doivent être journalisées dans le fichier LowDiskSpace.blg.</span><span class="sxs-lookup"><span data-stu-id="f7b60-141">The command uses the **Path** parameter to indicate that the selected data should be logged in the LowDiskSpace.blg file.</span></span>

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## <span data-ttu-id="f7b60-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7b60-142">PARAMETERS</span></span>

### <span data-ttu-id="f7b60-143">-Circulaire</span><span class="sxs-lookup"><span data-stu-id="f7b60-143">-Circular</span></span>

<span data-ttu-id="f7b60-144">Indique que le fichier de sortie est un journal circulaire avec le format premier entré, premier sorti (FIFO).</span><span class="sxs-lookup"><span data-stu-id="f7b60-144">Indicates that the output file is a circular log with first in, first out (FIFO) format.</span></span>
<span data-ttu-id="f7b60-145">Quand vous incluez ce paramètre, le paramètre **MaxSize** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f7b60-145">When you include this parameter, the **MaxSize** parameter is required.</span></span>

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

### <span data-ttu-id="f7b60-146">-FileFormat</span><span class="sxs-lookup"><span data-stu-id="f7b60-146">-FileFormat</span></span>

<span data-ttu-id="f7b60-147">Spécifie le format de sortie du fichier journal de sortie.</span><span class="sxs-lookup"><span data-stu-id="f7b60-147">Specifies the output format of the output log file.</span></span>

<span data-ttu-id="f7b60-148">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="f7b60-148">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f7b60-149">CSV</span><span class="sxs-lookup"><span data-stu-id="f7b60-149">CSV</span></span>
- <span data-ttu-id="f7b60-150">TSV</span><span class="sxs-lookup"><span data-stu-id="f7b60-150">TSV</span></span>
- <span data-ttu-id="f7b60-151">BLG</span><span class="sxs-lookup"><span data-stu-id="f7b60-151">BLG</span></span>

<span data-ttu-id="f7b60-152">La valeur par défaut est BLG.</span><span class="sxs-lookup"><span data-stu-id="f7b60-152">The default value is BLG.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7b60-153">-Force</span><span class="sxs-lookup"><span data-stu-id="f7b60-153">-Force</span></span>

<span data-ttu-id="f7b60-154">Remplace et remplace un fichier existant s’il existe dans l’emplacement spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="f7b60-154">Overwrites and replaces an existing file if one exists in the location specified by the **Path** parameter.</span></span>

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

### <span data-ttu-id="f7b60-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f7b60-155">-InputObject</span></span>

<span data-ttu-id="f7b60-156">Spécifie, sous forme de tableau, les données de compteur à exporter.</span><span class="sxs-lookup"><span data-stu-id="f7b60-156">Specifies, as an array, the counter data to export.</span></span> <span data-ttu-id="f7b60-157">Entrez une variable qui contient les données ou une commande qui obtient les données, telles que l' `Get-Counter` applet de commande ou `Import-Counter` .</span><span class="sxs-lookup"><span data-stu-id="f7b60-157">Enter a variable that contains the data or a command that gets the data, such as the `Get-Counter` or `Import-Counter` cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f7b60-158">-MaxSize</span><span class="sxs-lookup"><span data-stu-id="f7b60-158">-MaxSize</span></span>

<span data-ttu-id="f7b60-159">Spécifie la taille maximale du fichier de sortie en mégaoctets (Mo).</span><span class="sxs-lookup"><span data-stu-id="f7b60-159">Specifies the maximum size of the output file in megabytes (MB).</span></span>

<span data-ttu-id="f7b60-160">Si le paramètre **circulaire** est spécifié, quand le fichier journal atteint la taille maximale spécifiée, les entrées les plus anciennes sont supprimées, car les plus récentes sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="f7b60-160">If the **Circular** parameter is specified, then when the log file reaches the specified maximum size, the oldest entries are deleted as newer ones are added.</span></span> <span data-ttu-id="f7b60-161">Si le paramètre **circulaire** n’est pas spécifié, quand le fichier journal atteint la taille maximale spécifiée, aucune nouvelle donnée n’est ajoutée et l’applet de commande génère une erreur sans fin d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="f7b60-161">If the **Circular** parameter is not specified, then when the log file reaches the specified maximum size, no new data is added and the cmdlet generates a non-terminating error.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7b60-162">-Path</span><span class="sxs-lookup"><span data-stu-id="f7b60-162">-Path</span></span>

<span data-ttu-id="f7b60-163">Spécifie le chemin d'accès et le nom de fichier du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f7b60-163">Specifies the path and file name of the output file.</span></span> <span data-ttu-id="f7b60-164">Entrez un chemin d’accès relatif ou absolu sur l’ordinateur local, ou un chemin d’accès UNC (Uniform Naming Convention) à un ordinateur distant, tel que `\\Computer\Share\file.blg` .</span><span class="sxs-lookup"><span data-stu-id="f7b60-164">Enter a relative or absolute path on the local computer, or a Uniform Naming Convention (UNC) path to a remote computer, such as `\\Computer\Share\file.blg`.</span></span> <span data-ttu-id="f7b60-165">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f7b60-165">This parameter is required.</span></span>

<span data-ttu-id="f7b60-166">Le format de fichier est déterminé par la valeur du paramètre **FileFormat** , et non par l’extension de nom de fichier dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="f7b60-166">The file format is determined by the value of the **FileFormat** parameter, not by the file name extension in the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f7b60-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7b60-167">CommonParameters</span></span>

<span data-ttu-id="f7b60-168">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7b60-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7b60-169">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f7b60-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7b60-170">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f7b60-170">INPUTS</span></span>

### <span data-ttu-id="f7b60-171">Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet</span><span class="sxs-lookup"><span data-stu-id="f7b60-171">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet</span></span>

<span data-ttu-id="f7b60-172">Vous pouvez diriger les données du compteur de performance à partir de `Get-Counter` ou `Import-Counter` vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f7b60-172">You can pipe performance counter data from `Get-Counter` or `Import-Counter` to this cmdlet.</span></span>

## <span data-ttu-id="f7b60-173">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f7b60-173">OUTPUTS</span></span>

### <span data-ttu-id="f7b60-174">Aucun</span><span class="sxs-lookup"><span data-stu-id="f7b60-174">None</span></span>

## <span data-ttu-id="f7b60-175">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f7b60-175">NOTES</span></span>

<span data-ttu-id="f7b60-176">Le générateur de fichier journal s'attend à ce que tous les objets d'entrée aient le même chemin d'accès de compteur, et que ces objets soient regroupés par ordre chronologie croissant.</span><span class="sxs-lookup"><span data-stu-id="f7b60-176">The log file generator expects that all input objects have the same counter path and that the objects are arranged in ascending time order.</span></span>

<span data-ttu-id="f7b60-177">Le type et le chemin d'accès de compteur du premier objet d'entrée déterminent les propriétés enregistrées dans le fichier journal.</span><span class="sxs-lookup"><span data-stu-id="f7b60-177">The counter type and path of the first input object determines the properties recorded in the log file.</span></span> <span data-ttu-id="f7b60-178">Si d'autres objets d'entrée n'ont pas de valeur pour une propriété enregistrée, le champ de propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="f7b60-178">If other input objects do not have a value for a recorded property, the property field is empty.</span></span> <span data-ttu-id="f7b60-179">Si les objets ont des valeurs de propriété qui n'étaient pas enregistrées, les valeurs de propriété supplémentaires sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="f7b60-179">If the objects have property values that were not recorded, the extra property values are ignored.</span></span>

<span data-ttu-id="f7b60-180">L’analyseur de performances risque de ne pas pouvoir lire tous les journaux `Export-Counter` générés par.</span><span class="sxs-lookup"><span data-stu-id="f7b60-180">Performance Monitor might not be able to read all logs that `Export-Counter` generates.</span></span> <span data-ttu-id="f7b60-181">Par exemple, l’analyseur de performances nécessite que tous les objets aient le même chemin et que tous les objets soient séparés par le même intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="f7b60-181">For instance, Performance Monitor requires that all objects have the same path and that all objects are separated by the same time interval.</span></span>

<span data-ttu-id="f7b60-182">L' `Import-Counter` applet de commande n’a pas de paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="f7b60-182">The `Import-Counter` cmdlet does not have a **ComputerName** parameter.</span></span> <span data-ttu-id="f7b60-183">Toutefois, si l’ordinateur est configuré pour Windows PowerShell Windows PowerShell à distance, vous pouvez utiliser la `Invoke-Command` cmdlet pour exécuter une `Import-Counter` commande sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f7b60-183">However, if the computer is configured for remote Windows PowerShell Windows PowerShell, you can use the `Invoke-Command` cmdlet to run an `Import-Counter` command on a remote computer.</span></span>

## <span data-ttu-id="f7b60-184">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f7b60-184">RELATED LINKS</span></span>

[<span data-ttu-id="f7b60-185">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="f7b60-185">Get-Counter</span></span>](Get-Counter.md)

[<span data-ttu-id="f7b60-186">Import-Counter</span><span class="sxs-lookup"><span data-stu-id="f7b60-186">Import-Counter</span></span>](Import-Counter.md)
