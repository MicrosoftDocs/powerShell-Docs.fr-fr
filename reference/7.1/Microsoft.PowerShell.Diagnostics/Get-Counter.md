---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: b8b78c0a2dec0c3e51c91df522cc5b026952a222
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205097"
---
# <span data-ttu-id="8cc14-103">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="8cc14-103">Get-Counter</span></span>

## <span data-ttu-id="8cc14-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8cc14-104">SYNOPSIS</span></span>
<span data-ttu-id="8cc14-105">Obtient les données de compteur de performances provenant des ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="8cc14-105">Gets performance counter data from local and remote computers.</span></span>

## <span data-ttu-id="8cc14-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8cc14-106">SYNTAX</span></span>

### <span data-ttu-id="8cc14-107">GetCounterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8cc14-107">GetCounterSet (Default)</span></span>

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8cc14-108">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="8cc14-108">ListSetSet</span></span>

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8cc14-109">Description</span><span class="sxs-lookup"><span data-stu-id="8cc14-109">DESCRIPTION</span></span>

<span data-ttu-id="8cc14-110">L' `Get-Counter` applet de commande obtient les données du compteur de performance directement à partir de l’instrumentation d’analyse des performances dans la famille de systèmes d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="8cc14-110">The `Get-Counter` cmdlet gets performance counter data directly from the performance monitoring instrumentation in the Windows family of operating systems.</span></span> <span data-ttu-id="8cc14-111">`Get-Counter` Obtient les données de performances d’un ordinateur local ou d’ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="8cc14-111">`Get-Counter` gets performance data from a local computer or remote computers.</span></span>

<span data-ttu-id="8cc14-112">Vous pouvez utiliser les `Get-Counter` paramètres pour spécifier un ou plusieurs ordinateurs, répertorier les ensembles de compteurs de performance et les instances qu’ils contiennent, définir les intervalles d’échantillonnage et spécifier le nombre maximal d’échantillons.</span><span class="sxs-lookup"><span data-stu-id="8cc14-112">You can use the `Get-Counter` parameters to specify one or more computers, list the performance counter sets and the instances they contain, set the sample intervals, and specify the maximum number of samples.</span></span> <span data-ttu-id="8cc14-113">Sans paramètres, `Get-Counter` obtient les données des compteurs de performances pour un ensemble de compteurs système.</span><span class="sxs-lookup"><span data-stu-id="8cc14-113">Without parameters, `Get-Counter` gets performance counter data for a set of system counters.</span></span>

<span data-ttu-id="8cc14-114">De nombreux ensembles de compteurs sont protégés par des listes de contrôle d’accès (ACL).</span><span class="sxs-lookup"><span data-stu-id="8cc14-114">Many counter sets are protected by access control lists (ACL).</span></span> <span data-ttu-id="8cc14-115">Pour afficher tous les ensembles de compteurs, ouvrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-115">To see all counter sets, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="8cc14-116">Cette applet de commande a été réintroduite dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="8cc14-116">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="8cc14-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8cc14-117">EXAMPLES</span></span>

### <span data-ttu-id="8cc14-118">Exemple 1 : récupération de la liste des ensembles de compteurs</span><span class="sxs-lookup"><span data-stu-id="8cc14-118">Example 1: Get the counter set list</span></span>

<span data-ttu-id="8cc14-119">Cet exemple obtient la liste des ensembles de compteurs de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-119">This example gets the local computer's list of counter sets.</span></span>

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

<span data-ttu-id="8cc14-120">`Get-Counter` utilise le paramètre **ListSet** avec un astérisque ( `*` ) pour récupérer la liste des ensembles de compteurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-120">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get the list of counter sets.</span></span>
<span data-ttu-id="8cc14-121">Le point ( `.` ) dans la colonne **MachineName** représente l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-121">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="8cc14-122">Exemple 2 : spécifier SampleInterval et MaxSamples</span><span class="sxs-lookup"><span data-stu-id="8cc14-122">Example 2: Specify the SampleInterval and MaxSamples</span></span>

<span data-ttu-id="8cc14-123">Cet exemple obtient les données de compteur pour tous les processeurs sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-123">This examples gets the counter data for all processors on the local computer.</span></span> <span data-ttu-id="8cc14-124">Les données sont collectées à intervalles de deux secondes jusqu’à ce qu’il y ait trois échantillons.</span><span class="sxs-lookup"><span data-stu-id="8cc14-124">Data is collected at two-second intervals until there are three samples.</span></span>

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

<span data-ttu-id="8cc14-125">`Get-Counter` utilise le paramètre **Counter** pour spécifier le chemin d’accès au compteur `\Processor(_Total)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-125">`Get-Counter` uses the **Counter** parameter to specify the counter path `\Processor(_Total)\% Processor Time`.</span></span> <span data-ttu-id="8cc14-126">Le paramètre **SampleInterval** définit un intervalle de deux secondes pour vérifier le compteur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-126">The **SampleInterval** parameter sets a two-second interval to check the counter.</span></span> <span data-ttu-id="8cc14-127">**MaxSamples** détermine que trois est le nombre maximal de fois que le compteur est vérifié.</span><span class="sxs-lookup"><span data-stu-id="8cc14-127">**MaxSamples** determines that three is the maximum number of times to check the counter.</span></span>

### <span data-ttu-id="8cc14-128">Exemple 3 : obtenir des échantillons continus d’un compteur</span><span class="sxs-lookup"><span data-stu-id="8cc14-128">Example 3: Get continuous samples of a counter</span></span>

<span data-ttu-id="8cc14-129">Cet exemple obtient des échantillons continus pour un compteur chaque seconde.</span><span class="sxs-lookup"><span data-stu-id="8cc14-129">This examples gets continuous samples for a counter every second.</span></span> <span data-ttu-id="8cc14-130">Pour arrêter la commande, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8cc14-130">To stop the command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="8cc14-131">Pour spécifier un intervalle plus long entre les échantillons, utilisez le paramètre **SampleInterval** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-131">To specify a longer interval between samples, use the **SampleInterval** parameter.</span></span>

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

<span data-ttu-id="8cc14-132">`Get-Counter` utilise le paramètre **Counter** pour spécifier le `\Processor\% Processor Time` compteur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-132">`Get-Counter` uses the **Counter** parameter to specify the `\Processor\% Processor Time` counter.</span></span>
<span data-ttu-id="8cc14-133">Le paramètre **Continuous** spécifie d’utiliser des échantillons chaque seconde jusqu’à ce que la commande soit arrêtée avec <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8cc14-133">The **Continuous** parameter specifies to get samples every second until the command is stopped with <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <span data-ttu-id="8cc14-134">Exemple 4 : liste alphabétique des ensembles de compteurs</span><span class="sxs-lookup"><span data-stu-id="8cc14-134">Example 4: Alphabetical list of counter sets</span></span>

<span data-ttu-id="8cc14-135">Cet exemple utilise le pipeline pour récupérer le jeu de listes de compteurs, puis trier la liste par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="8cc14-135">This example uses the pipeline to get the counter list set and then sort the list in alphabetical order.</span></span>

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

<span data-ttu-id="8cc14-136">`Get-Counter` utilise le paramètre **ListSet** avec un astérisque ( `*` ) pour obtenir la liste complète des ensembles de compteurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-136">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get a complete list of counter sets.</span></span> <span data-ttu-id="8cc14-137">Les objets **CounterSet** sont envoyés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8cc14-137">The **CounterSet** objects are sent down the pipeline.</span></span> <span data-ttu-id="8cc14-138">`Sort-Object` utilise le paramètre **Property** pour spécifier que les objets sont triés par **CounterSetName** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-138">`Sort-Object` uses the **Property** parameter to specify that the objects are sorted by **CounterSetName** .</span></span> <span data-ttu-id="8cc14-139">Les objets sont envoyés dans le pipeline à `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-139">The objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="8cc14-140">Le paramètre **AutoSize** ajuste les largeurs de colonne pour réduire la troncation.</span><span class="sxs-lookup"><span data-stu-id="8cc14-140">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

<span data-ttu-id="8cc14-141">Le point ( `.` ) dans la colonne **MachineName** représente l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-141">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="8cc14-142">Exemple 5 : exécuter une tâche en arrière-plan pour obtenir des données de compteur</span><span class="sxs-lookup"><span data-stu-id="8cc14-142">Example 5: Run a background job to get counter data</span></span>

<span data-ttu-id="8cc14-143">Dans cet exemple, `Start-Job` exécute une `Get-Counter` commande en tant que tâche en arrière-plan sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-143">In this example, `Start-Job` runs a `Get-Counter` command as a background job on the local computer.</span></span>
<span data-ttu-id="8cc14-144">Pour afficher la sortie du compteur de performance à partir du travail, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-144">To view the performance counter output from the job, use the `Receive-Job` cmdlet.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

<span data-ttu-id="8cc14-145">`Start-Job` utilise le paramètre **scriptblock** pour exécuter une `Get-Counter` commande.</span><span class="sxs-lookup"><span data-stu-id="8cc14-145">`Start-Job` uses the **ScriptBlock** parameter to run a `Get-Counter` command.</span></span> <span data-ttu-id="8cc14-146">`Get-Counter` utilise le paramètre **Counter** pour spécifier le chemin d’accès au compteur `\LogicalDisk(_Total)\% Free Space` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-146">`Get-Counter` uses the **Counter** parameter to specify the counter path `\LogicalDisk(_Total)\% Free Space`.</span></span> <span data-ttu-id="8cc14-147">Le paramètre **MaxSamples** spécifie d’utiliser les exemples 1000 du compteur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-147">The **MaxSamples** parameter specifies to get 1000 samples of the counter.</span></span>

### <span data-ttu-id="8cc14-148">Exemple 6 : récupérer des données de compteur à partir de plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="8cc14-148">Example 6: Get counter data from multiple computers</span></span>

<span data-ttu-id="8cc14-149">Cet exemple utilise une variable pour obtenir les données des compteurs de performances de deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-149">This example uses a variable to get performance counter data from two computers.</span></span>

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

<span data-ttu-id="8cc14-150">La `$DiskReads` variable stocke le `\LogicalDisk(C:)\Disk Reads/sec` chemin d’accès au compteur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-150">The `$DiskReads` variable stores the `\LogicalDisk(C:)\Disk Reads/sec` counter path.</span></span> <span data-ttu-id="8cc14-151">La `$DiskReads` variable est envoyée dans le pipeline à `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-151">The `$DiskReads` variable is sent down the pipeline to `Get-Counter`.</span></span> <span data-ttu-id="8cc14-152">**Counter** est le premier paramètre de position et accepte le chemin d’accès stocké dans `$DiskReads` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-152">**Counter** is the first position parameter and accepts the path stored in `$DiskReads`.</span></span> <span data-ttu-id="8cc14-153">**ComputerName** spécifie les deux ordinateurs et **MaxSamples** spécifie d’avoir 10 échantillons sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-153">**ComputerName** specifies the two computers and **MaxSamples** specifies to get 10 samples from each computer.</span></span>

### <span data-ttu-id="8cc14-154">Exemple 7 : obtenir les valeurs d’instance d’un compteur à partir de plusieurs ordinateurs aléatoires</span><span class="sxs-lookup"><span data-stu-id="8cc14-154">Example 7: Get a counter's instance values from multiple random computers</span></span>

<span data-ttu-id="8cc14-155">Cet exemple obtient la valeur d’un compteur de performances sur les ordinateurs distants aléatoires 50 de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8cc14-155">This example gets the value of a performance counter on 50 random, remote computers in the enterprise.</span></span> <span data-ttu-id="8cc14-156">Le paramètre **ComputerName** utilise des noms d’ordinateur aléatoires stockés dans une variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-156">The **ComputerName** parameter uses random computer names stored in a variable.</span></span> <span data-ttu-id="8cc14-157">Pour mettre à jour les noms d’ordinateur dans la variable, recréez la variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-157">To update the computer names in the variable, recreate the variable.</span></span>

<span data-ttu-id="8cc14-158">Une alternative pour les noms de serveur dans le paramètre **ComputerName** consiste à utiliser un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="8cc14-158">An alternative for the server names in the **ComputerName** parameter is to use a text file.</span></span> <span data-ttu-id="8cc14-159">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8cc14-159">For example:</span></span>

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

<span data-ttu-id="8cc14-160">Le chemin d’accès du compteur comprend un astérisque ( `*` ) dans le nom de l’instance pour obtenir les données pour chaque processeur de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8cc14-160">The counter path includes an asterisk (`*`) in the instance name to get the data for each of the remote computer's processors.</span></span>

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

<span data-ttu-id="8cc14-161">L' `Get-Random` applet de commande utilise `Get-Content` pour sélectionner 50 noms d’ordinateur aléatoires dans le `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="8cc14-161">The `Get-Random` cmdlet uses `Get-Content` to select 50 random computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="8cc14-162">Les noms des ordinateurs distants sont stockés dans la `$Servers` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-162">The remote computer names are stored in the `$Servers` variable.</span></span> <span data-ttu-id="8cc14-163">Le `\Processor(*)\% Processor Time` chemin d’accès du compteur est stocké dans la `$Counter` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-163">The `\Processor(*)\% Processor Time` counter's path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="8cc14-164">`Get-Counter` utilise le paramètre **Counter** pour spécifier les compteurs dans la `$Counter` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-164">`Get-Counter` uses the **Counter** parameter to specify the counters in the `$Counter` variable.</span></span> <span data-ttu-id="8cc14-165">Le paramètre **ComputerName** spécifie les noms d’ordinateur dans la `$Servers` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-165">The **ComputerName** parameter specifies the computer names in the `$Servers` variable.</span></span>

### <span data-ttu-id="8cc14-166">Exemple 8 : utiliser la propriété Path pour récupérer les noms de chemin d’accès mis en forme</span><span class="sxs-lookup"><span data-stu-id="8cc14-166">Example 8: Use the Path property to get formatted path names</span></span>

<span data-ttu-id="8cc14-167">Cet exemple utilise la propriété **path** d’un ensemble de compteurs pour rechercher les noms de chemin d’accès mis en forme pour les compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="8cc14-167">This example uses the **Path** property of a counter set to find the formatted path names for the performance counters.</span></span>

<span data-ttu-id="8cc14-168">Le pipeline est utilisé avec l' `Where-Object` applet de commande pour rechercher un sous-ensemble des noms de chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="8cc14-168">The pipeline is used with the `Where-Object` cmdlet to find a subset of the path names.</span></span> <span data-ttu-id="8cc14-169">Pour rechercher un ensemble de compteurs liste complète des chemins de compteur, supprimez le pipeline ( `|` ) et la `Where-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="8cc14-169">To find a counter sets complete list of counter paths, remove the pipeline (`|`) and `Where-Object` command.</span></span>

<span data-ttu-id="8cc14-170">`$_`Est une variable automatique pour l’objet actuel dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8cc14-170">The `$_` is an automatic variable for the current object in the pipeline.</span></span>
<span data-ttu-id="8cc14-171">Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8cc14-171">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

<span data-ttu-id="8cc14-172">`Get-Counter` utilise le paramètre **ListSet** pour spécifier le jeu de compteurs de **mémoire** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-172">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="8cc14-173">La commande est placée entre parenthèses afin que la propriété **paths** retourne chaque chemin d’accès sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="8cc14-173">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="8cc14-174">Les objets sont envoyés dans le pipeline à `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-174">The objects are sent down the pipeline to `Where-Object`.</span></span> <span data-ttu-id="8cc14-175">`Where-Object` utilise la variable `$_` pour traiter chaque objet et utilise l' `-like` opérateur pour rechercher les correspondances de la chaîne `*Cache*` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-175">`Where-Object` uses the variable `$_` to process each object and uses the `-like` operator to find matches for the string `*Cache*`.</span></span> <span data-ttu-id="8cc14-176">Les astérisques ( `*` ) sont des caractères génériques pour n’importe quel caractère.</span><span class="sxs-lookup"><span data-stu-id="8cc14-176">The asterisks (`*`) are wildcards for any characters.</span></span>

### <span data-ttu-id="8cc14-177">Exemple 9 : utiliser la propriété PathsWithInstances pour récupérer les noms de chemin d’accès mis en forme</span><span class="sxs-lookup"><span data-stu-id="8cc14-177">Example 9: Use the PathsWithInstances property to get formatted path names</span></span>

<span data-ttu-id="8cc14-178">Cet exemple obtient les noms de chemin d’accès mis en forme qui incluent les instances des compteurs de performance **PhysicalDisk** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-178">This example gets the formatted path names that include the instances for the **PhysicalDisk** performance counters.</span></span>

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

<span data-ttu-id="8cc14-179">`Get-Counter` utilise le paramètre **ListSet** pour spécifier l’ensemble de compteurs de **disque physique** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-179">`Get-Counter` uses the **ListSet** parameter to specify the **PhysicalDisk** counter set.</span></span> <span data-ttu-id="8cc14-180">La commande est placée entre parenthèses afin que la propriété **PathsWithInstances** retourne chaque instance de chemin d’accès en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="8cc14-180">The command is enclosed in parentheses so that the **PathsWithInstances** property returns each path instance as a string.</span></span>

### <span data-ttu-id="8cc14-181">Exemple 10 : obtenir une valeur unique pour chaque compteur dans un ensemble de compteurs</span><span class="sxs-lookup"><span data-stu-id="8cc14-181">Example 10: Get a single value for each counter in a counter set</span></span>

<span data-ttu-id="8cc14-182">Dans cet exemple, une valeur unique est retournée pour chaque compteur de performance dans l’ensemble de compteurs de **mémoire** de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-182">In this example, a single value is returned for each performance counter in the local computer's **Memory** counter set.</span></span>

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

<span data-ttu-id="8cc14-183">`Get-Counter` utilise le paramètre **ListSet** pour spécifier le jeu de compteurs de **mémoire** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-183">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="8cc14-184">La commande est placée entre parenthèses afin que la propriété **paths** retourne chaque chemin d’accès sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="8cc14-184">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="8cc14-185">Les chemins d’accès sont stockés dans la `$MemCounters` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-185">The paths are stored in the `$MemCounters` variable.</span></span> <span data-ttu-id="8cc14-186">`Get-Counter` utilise le paramètre **Counter** pour spécifier les chemins de compteur dans la `$MemCounters` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-186">`Get-Counter` uses the **Counter** parameter to specify the counter paths in the `$MemCounters` variable.</span></span>

### <span data-ttu-id="8cc14-187">Exemple 11 : afficher les valeurs de propriété d’un objet</span><span class="sxs-lookup"><span data-stu-id="8cc14-187">Example 11: Display an object's property values</span></span>

<span data-ttu-id="8cc14-188">Les valeurs de propriété de l’objet **PerformanceCounterSample** représentent chaque échantillon de données.</span><span class="sxs-lookup"><span data-stu-id="8cc14-188">The property values in the **PerformanceCounterSample** object represent each data sample.</span></span> <span data-ttu-id="8cc14-189">Dans cet exemple, nous utilisons les propriétés de l’objet **CounterSamples** pour examiner, sélectionner, trier et regrouper les données.</span><span class="sxs-lookup"><span data-stu-id="8cc14-189">In this example we use the properties of the **CounterSamples** object to examine, select, sort, and group the data.</span></span>

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

<span data-ttu-id="8cc14-190">Le chemin d’accès au compteur est stocké dans la `$Counter` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-190">The counter path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="8cc14-191">`Get-Counter` Obtient un échantillon des valeurs de compteur et stocke les résultats dans la `$Data` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-191">`Get-Counter` gets one sample of the counter values and stores the results in the `$Data` variable.</span></span> <span data-ttu-id="8cc14-192">La `$Data` variable utilise la propriété **CounterSamples** pour récupérer les propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8cc14-192">The `$Data` variable uses the **CounterSamples** property to get the object's properties.</span></span> <span data-ttu-id="8cc14-193">L’objet est envoyé dans le pipeline à `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-193">The object is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="8cc14-194">Le paramètre **Property** utilise un `*` caractère générique astérisque () pour sélectionner toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="8cc14-194">The **Property** parameter uses an asterisk (`*`) wildcard to select all the properties.</span></span>

### <span data-ttu-id="8cc14-195">Exemple 12 : valeurs du tableau des compteurs de performances</span><span class="sxs-lookup"><span data-stu-id="8cc14-195">Example 12: Performance counter array values</span></span>

<span data-ttu-id="8cc14-196">Dans cet exemple, une variable stocke chaque compteur de performance.</span><span class="sxs-lookup"><span data-stu-id="8cc14-196">In this example, a variable stores each performance counter.</span></span> <span data-ttu-id="8cc14-197">La propriété **CounterSamples** est un tableau qui peut afficher des valeurs de compteur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8cc14-197">The **CounterSamples** property is an array that can display specific counter values.</span></span>

<span data-ttu-id="8cc14-198">Pour afficher chaque échantillon de compteur, utilisez `$Counter.CounterSamples` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-198">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

<span data-ttu-id="8cc14-199">`Get-Counter` utilise le paramètre **Counter** pour spécifier le compteur `\Processor(*)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-199">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="8cc14-200">Les valeurs sont stockées dans la `$Counter` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-200">The values are stored in the `$Counter` variable.</span></span>
<span data-ttu-id="8cc14-201">`$Counter.CounterSamples[0]` affiche la valeur de tableau pour la première valeur de compteur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-201">`$Counter.CounterSamples[0]` displays the array value for the first counter value.</span></span>

### <span data-ttu-id="8cc14-202">Exemple 13 : comparer les valeurs des compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="8cc14-202">Example 13: Compare performance counter values</span></span>

<span data-ttu-id="8cc14-203">Cet exemple recherche la quantité de temps processeur utilisée par chaque processeur sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-203">This example finds the amount of processor time used by each processor on the local computer.</span></span> <span data-ttu-id="8cc14-204">La propriété **CounterSamples** est utilisée pour comparer les données de compteur par rapport à une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8cc14-204">The **CounterSamples** property is used to compare the counter data against a specified value.</span></span>

<span data-ttu-id="8cc14-205">Pour afficher chaque échantillon de compteur, utilisez `$Counter.CounterSamples` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-205">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

<span data-ttu-id="8cc14-206">`Get-Counter` utilise le paramètre **Counter** pour spécifier le compteur `\Processor(*)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-206">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="8cc14-207">Les valeurs sont stockées dans la `$Counter` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-207">The values are stored in the `$Counter` variable.</span></span> <span data-ttu-id="8cc14-208">Les objets stockés dans `$Counter.CounterSamples` sont envoyés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8cc14-208">The objects stored in `$Counter.CounterSamples` are sent down the pipeline.</span></span> <span data-ttu-id="8cc14-209">`Where-Object` utilise un bloc de script pour comparer chaque valeur d’objet à une valeur spécifiée de 20.</span><span class="sxs-lookup"><span data-stu-id="8cc14-209">`Where-Object` uses a script block to compare each objects value against a specified value of 20.</span></span> <span data-ttu-id="8cc14-210">`$_.CookedValue`Est une variable pour l’objet actuel dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8cc14-210">The `$_.CookedValue` is a variable for the current object in the pipeline.</span></span> <span data-ttu-id="8cc14-211">Les compteurs avec un **CookedValue** inférieur à 20 s’affichent.</span><span class="sxs-lookup"><span data-stu-id="8cc14-211">Counters with a **CookedValue** that is less than 20 are displayed.</span></span>

### <span data-ttu-id="8cc14-212">Exemple 14 : trier les données des compteurs de performances</span><span class="sxs-lookup"><span data-stu-id="8cc14-212">Example 14: Sort performance counter data</span></span>

<span data-ttu-id="8cc14-213">Cet exemple montre comment trier des données de compteur de performance.</span><span class="sxs-lookup"><span data-stu-id="8cc14-213">This example shows how to sort performance counter data.</span></span> <span data-ttu-id="8cc14-214">L’exemple recherche les processus sur l’ordinateur qui utilisent le plus de temps processeur au cours de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="8cc14-214">The example finds the processes on the computer that are using the most processor time during the sample.</span></span>

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

<span data-ttu-id="8cc14-215">`Get-Counter` utilise le paramètre **Counter** pour spécifier le `\Process(*)\% Processor Time` compteur de tous les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-215">`Get-Counter` uses the **Counter** parameter to specify the `\Process(*)\% Processor Time` counter for all the processes on the local computer.</span></span> <span data-ttu-id="8cc14-216">Le résultat est stocké dans la `$Procs` variable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-216">The result is stored in the `$Procs` variable.</span></span> <span data-ttu-id="8cc14-217">La `$Procs` variable avec la propriété **CounterSamples** envoie les objets **PerformanceCounterSample** dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8cc14-217">The `$Procs` variable with the **CounterSamples** property sends the **PerformanceCounterSample** objects down the pipeline.</span></span> <span data-ttu-id="8cc14-218">`Sort-Object` utilise le paramètre **Property** pour trier les objets par **CookedValue** dans l’ordre **décroissant** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-218">`Sort-Object` uses the **Property** parameter to sort the objects by **CookedValue** in **Descending** order.</span></span> <span data-ttu-id="8cc14-219">`Format-Table` utilise le paramètre **Property** pour sélectionner les colonnes de la sortie.</span><span class="sxs-lookup"><span data-stu-id="8cc14-219">`Format-Table` uses the **Property** parameter to select the columns for the output.</span></span> <span data-ttu-id="8cc14-220">Le paramètre **AutoSize** ajuste les largeurs de colonne pour réduire la troncation.</span><span class="sxs-lookup"><span data-stu-id="8cc14-220">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

## <span data-ttu-id="8cc14-221">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8cc14-221">PARAMETERS</span></span>

### <span data-ttu-id="8cc14-222">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8cc14-222">-ComputerName</span></span>

<span data-ttu-id="8cc14-223">Spécifie un nom d’ordinateur ou un tableau de noms d’ordinateurs **distants** séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="8cc14-223">Specifies one computer name or a comma-separated array of **remote** computer names.</span></span> <span data-ttu-id="8cc14-224">Utilisez le nom NetBIOS, une adresse IP ou le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-224">Use the NetBIOS name, an IP address, or the computer's fully qualified domain name.</span></span>

<span data-ttu-id="8cc14-225">Pour récupérer les données du compteur de performance à partir de l’ordinateur **local** , excluez le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-225">To get performance counter data from the **local** computer, exclude the **ComputerName** parameter.</span></span>
<span data-ttu-id="8cc14-226">Pour une sortie telle qu’un **ListSet** qui contient la colonne **MachineName** , un point ( `.` ) indique l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-226">For output such as a **ListSet** that contains the **MachineName** column, a dot (`.`) indicates the local computer.</span></span>

<span data-ttu-id="8cc14-227">`Get-Counter` ne repose pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8cc14-227">`Get-Counter` doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="8cc14-228">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="8cc14-228">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc14-229">-Continuous</span><span class="sxs-lookup"><span data-stu-id="8cc14-229">-Continuous</span></span>

<span data-ttu-id="8cc14-230">Lorsque la **continuation** est spécifiée, `Get-Counter` obtient des exemples jusqu’à ce que vous appuyiez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8cc14-230">When the **Continuous** is specified, `Get-Counter` gets samples until you press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="8cc14-231">Les échantillons sont obtenus chaque seconde pour chaque compteur de performance spécifié.</span><span class="sxs-lookup"><span data-stu-id="8cc14-231">Samples are obtained every second for each specified performance counter.</span></span> <span data-ttu-id="8cc14-232">Utilisez le paramètre **SampleInterval** pour augmenter l’intervalle entre les échantillons continus.</span><span class="sxs-lookup"><span data-stu-id="8cc14-232">Use the **SampleInterval** parameter to increase the interval between continuous samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc14-233">-Compteur</span><span class="sxs-lookup"><span data-stu-id="8cc14-233">-Counter</span></span>

<span data-ttu-id="8cc14-234">Spécifie le chemin d’accès à un ou plusieurs chemins de compteur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-234">Specifies the path to one or more counter paths.</span></span> <span data-ttu-id="8cc14-235">Les chemins d’accès sont des entrées sous la forme d’un tableau séparé par des virgules, d’une variable ou de valeurs d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="8cc14-235">Paths are input as a comma-separated array, a variable, or values from a text file.</span></span> <span data-ttu-id="8cc14-236">Vous pouvez envoyer des chaînes de chemin d’accès de compteur vers le pipeline `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-236">You can send counter path strings down the pipeline to `Get-Counter`.</span></span>

<span data-ttu-id="8cc14-237">Les chemins de compteur utilisent la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8cc14-237">Counter paths use the following syntax:</span></span>

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

<span data-ttu-id="8cc14-238">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8cc14-238">For example:</span></span>

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

<span data-ttu-id="8cc14-239">`\\ComputerName`Est facultatif dans un chemin d’accès de compteur de performance.</span><span class="sxs-lookup"><span data-stu-id="8cc14-239">The `\\ComputerName` is optional in a performance counter path.</span></span> <span data-ttu-id="8cc14-240">Si le chemin d’accès au compteur n’inclut pas le nom de l’ordinateur, `Get-Counter` utilise l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8cc14-240">If the counter path doesn't include the computer name, `Get-Counter` uses the local computer.</span></span>

<span data-ttu-id="8cc14-241">Un astérisque ( `*` ) dans l’instance est un caractère générique pour obtenir toutes les instances du compteur.</span><span class="sxs-lookup"><span data-stu-id="8cc14-241">An asterisk (`*`) in the instance is a wildcard character to get all instances of the counter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8cc14-242">-ListSet</span><span class="sxs-lookup"><span data-stu-id="8cc14-242">-ListSet</span></span>

<span data-ttu-id="8cc14-243">Répertorie les ensembles de compteurs de performances sur les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-243">Lists the performance counter sets on the computers.</span></span> <span data-ttu-id="8cc14-244">Utilisez un astérisque ( `*` ) pour spécifier tous les ensembles de compteurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-244">Use an asterisk (`*`) to specify all counter sets.</span></span> <span data-ttu-id="8cc14-245">Entrez un nom ou une chaîne séparée par des virgules de noms d’ensembles de compteurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-245">Enter one name or a comma-separated string of counter set names.</span></span> <span data-ttu-id="8cc14-246">Vous pouvez envoyer des noms d’ensemble de compteurs vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8cc14-246">You can send counter set names down the pipeline.</span></span>

<span data-ttu-id="8cc14-247">Pour obtenir un ensemble de compteurs avec des chemins de compteur mis en forme, utilisez le paramètre **ListSet** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-247">To get a counter sets formatted counter paths, use the **ListSet** parameter.</span></span> <span data-ttu-id="8cc14-248">Les propriétés **paths** et **PathsWithInstances** de chaque ensemble de compteurs contiennent les chemins de compteur individuels mis en forme en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="8cc14-248">The **Paths** and **PathsWithInstances** properties of each counter set contain the individual counter paths formatted as a string.</span></span>

<span data-ttu-id="8cc14-249">Vous pouvez enregistrer les chaînes de chemin de compteur dans une variable ou utiliser le pipeline pour envoyer la chaîne à une autre `Get-Counter` commande.</span><span class="sxs-lookup"><span data-stu-id="8cc14-249">You can save the counter path strings in a variable or use the pipeline to send the string to another `Get-Counter` command.</span></span>

<span data-ttu-id="8cc14-250">Par exemple, pour envoyer chaque chemin de compteur de **processeur** à `Get-Counter` :</span><span class="sxs-lookup"><span data-stu-id="8cc14-250">For example to send each **Processor** counter path to `Get-Counter`:</span></span>

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> <span data-ttu-id="8cc14-251">Dans PowerShell 7, `Get-Counter` Impossible de récupérer la propriété **Description** de l’ensemble de compteurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-251">In PowerShell 7, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="8cc14-252">La **Description** a la valeur `$null` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-252">The **Description** is set to `$null`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8cc14-253">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="8cc14-253">-MaxSamples</span></span>

<span data-ttu-id="8cc14-254">Spécifie le nombre d’échantillons à récupérer à partir de chaque compteur de performance spécifié.</span><span class="sxs-lookup"><span data-stu-id="8cc14-254">Specifies the number of samples to get from each specified performance counter.</span></span> <span data-ttu-id="8cc14-255">Pour obtenir un flux constant d’exemples, utilisez le paramètre **Continuous** .</span><span class="sxs-lookup"><span data-stu-id="8cc14-255">To get a constant stream of samples, use the **Continuous** parameter.</span></span>

<span data-ttu-id="8cc14-256">Si le paramètre **MaxSamples** n’est pas spécifié, `Get-Counter` obtient uniquement un échantillon pour chaque compteur spécifié.</span><span class="sxs-lookup"><span data-stu-id="8cc14-256">If the **MaxSamples** parameter isn't specified, `Get-Counter` only gets one sample for each specified counter.</span></span>

<span data-ttu-id="8cc14-257">Pour collecter un jeu de données volumineux, exécutez `Get-Counter` en tant que tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8cc14-257">To collect a large data set, run `Get-Counter` as a PowerShell background job.</span></span> <span data-ttu-id="8cc14-258">Pour plus d’informations, consultez [à propos des_tâches](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="8cc14-258">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc14-259">-SampleInterval</span><span class="sxs-lookup"><span data-stu-id="8cc14-259">-SampleInterval</span></span>

<span data-ttu-id="8cc14-260">Spécifie le nombre de secondes entre les échantillons pour chaque compteur de performance spécifié.</span><span class="sxs-lookup"><span data-stu-id="8cc14-260">Specifies the number of seconds between samples for each specified performance counter.</span></span> <span data-ttu-id="8cc14-261">Si le paramètre **SampleInterval** n’est pas spécifié, `Get-Counter` utilise un intervalle d’une seconde.</span><span class="sxs-lookup"><span data-stu-id="8cc14-261">If the **SampleInterval** parameter isn't specified, `Get-Counter` uses a one-second interval.</span></span>

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc14-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8cc14-262">CommonParameters</span></span>

<span data-ttu-id="8cc14-263">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8cc14-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8cc14-264">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8cc14-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8cc14-265">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8cc14-265">INPUTS</span></span>

### <span data-ttu-id="8cc14-266">System.String[]</span><span class="sxs-lookup"><span data-stu-id="8cc14-266">System.String[]</span></span>

<span data-ttu-id="8cc14-267">`Get-Counter` accepte l’entrée de pipeline pour les chemins de compteurs et les noms des ensembles de compteurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-267">`Get-Counter` accepts pipeline input for counter paths and counter set names.</span></span>

## <span data-ttu-id="8cc14-268">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8cc14-268">OUTPUTS</span></span>

### <span data-ttu-id="8cc14-269">Microsoft. PowerShell. Commands. GetCounter. CounterSet, Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet, Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSample</span><span class="sxs-lookup"><span data-stu-id="8cc14-269">Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample</span></span>

<span data-ttu-id="8cc14-270">Pour afficher les propriétés d’un objet, envoyez la sortie vers le pipeline dans le pipeline `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-270">To view an object's properties, send the output down the pipeline to `Get-Member`.</span></span> <span data-ttu-id="8cc14-271">Les types d’objets qui sont générés sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="8cc14-271">The object types that are output are as follows:</span></span>

<span data-ttu-id="8cc14-272">Paramètre **ListSet** : **Microsoft. PowerShell. Commands. GetCounter. CounterSet**</span><span class="sxs-lookup"><span data-stu-id="8cc14-272">**ListSet** parameter: **Microsoft.PowerShell.Commands.GetCounter.CounterSet**</span></span>

<span data-ttu-id="8cc14-273">Paramètre de **compteur** : **Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet**</span><span class="sxs-lookup"><span data-stu-id="8cc14-273">**Counter** parameter: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet**</span></span>

<span data-ttu-id="8cc14-274">Propriété **CounterSamples** : **Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSample**</span><span class="sxs-lookup"><span data-stu-id="8cc14-274">**CounterSamples** property: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample**</span></span>

## <span data-ttu-id="8cc14-275">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8cc14-275">NOTES</span></span>

<span data-ttu-id="8cc14-276">Si aucun paramètre n’est spécifié, `Get-Counter` obtient un échantillon pour chaque compteur de performance spécifié.</span><span class="sxs-lookup"><span data-stu-id="8cc14-276">If no parameters are specified, `Get-Counter` gets one sample for each specified performance counter.</span></span> <span data-ttu-id="8cc14-277">Utilisez les paramètres **MaxSamples** et **Continuous** pour obtenir d’autres exemples.</span><span class="sxs-lookup"><span data-stu-id="8cc14-277">Use the **MaxSamples** and **Continuous** parameters to get more samples.</span></span>

<span data-ttu-id="8cc14-278">`Get-Counter` utilise un intervalle d’une seconde entre les échantillons.</span><span class="sxs-lookup"><span data-stu-id="8cc14-278">`Get-Counter` uses a one-second interval between samples.</span></span> <span data-ttu-id="8cc14-279">Utilisez le paramètre **SampleInterval** pour augmenter l’intervalle.</span><span class="sxs-lookup"><span data-stu-id="8cc14-279">Use the **SampleInterval** parameter to increase the interval.</span></span>

<span data-ttu-id="8cc14-280">Les valeurs **MaxSamples** et **SampleInterval** s’appliquent à tous les compteurs de chaque ordinateur dans la commande.</span><span class="sxs-lookup"><span data-stu-id="8cc14-280">The **MaxSamples** and **SampleInterval** values apply to all the counters on each computer in the command.</span></span> <span data-ttu-id="8cc14-281">Pour définir des valeurs différentes pour différents compteurs, entrez des `Get-Counter` commandes distinctes.</span><span class="sxs-lookup"><span data-stu-id="8cc14-281">To set different values for different counters, enter separate `Get-Counter` commands.</span></span>

<span data-ttu-id="8cc14-282">Dans PowerShell 7, quand vous utilisez le paramètre **ListSet** , vous `Get-Counter` ne pouvez pas récupérer la propriété **Description** de l’ensemble de compteurs.</span><span class="sxs-lookup"><span data-stu-id="8cc14-282">In PowerShell 7, when using the **ListSet** parameter, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="8cc14-283">La **Description** a la valeur `$null` .</span><span class="sxs-lookup"><span data-stu-id="8cc14-283">The **Description** is set to `$null`.</span></span>

## <span data-ttu-id="8cc14-284">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8cc14-284">RELATED LINKS</span></span>

[<span data-ttu-id="8cc14-285">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="8cc14-285">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="8cc14-286">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="8cc14-286">about_Jobs</span></span>](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[<span data-ttu-id="8cc14-287">Format-List</span><span class="sxs-lookup"><span data-stu-id="8cc14-287">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="8cc14-288">Format-Table</span><span class="sxs-lookup"><span data-stu-id="8cc14-288">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="8cc14-289">Get-Member</span><span class="sxs-lookup"><span data-stu-id="8cc14-289">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="8cc14-290">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="8cc14-290">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)

[<span data-ttu-id="8cc14-291">Start-Job</span><span class="sxs-lookup"><span data-stu-id="8cc14-291">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="8cc14-292">Where-Object</span><span class="sxs-lookup"><span data-stu-id="8cc14-292">Where-Object</span></span>](..//Microsoft.PowerShell.Core/Where-Object.md)

