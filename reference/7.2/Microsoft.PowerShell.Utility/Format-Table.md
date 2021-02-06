---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 2db0a8abe8fbd87b077e40655a06a1db45482ebc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598973"
---
# <span data-ttu-id="31a8b-102">Format-Table</span><span class="sxs-lookup"><span data-stu-id="31a8b-102">Format-Table</span></span>

## <span data-ttu-id="31a8b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="31a8b-103">SYNOPSIS</span></span>
<span data-ttu-id="31a8b-104">Met en forme la sortie en tant que table.</span><span class="sxs-lookup"><span data-stu-id="31a8b-104">Formats the output as a table.</span></span>

## <span data-ttu-id="31a8b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="31a8b-105">SYNTAX</span></span>

### <span data-ttu-id="31a8b-106">Tous</span><span class="sxs-lookup"><span data-stu-id="31a8b-106">All</span></span>

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="31a8b-107">Description</span><span class="sxs-lookup"><span data-stu-id="31a8b-107">DESCRIPTION</span></span>

<span data-ttu-id="31a8b-108">L' `Format-Table` applet de commande met en forme la sortie d’une commande en tant que table avec les propriétés sélectionnées de l’objet dans chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="31a8b-108">The `Format-Table` cmdlet formats the output of a command as a table with the selected properties of the object in each column.</span></span> <span data-ttu-id="31a8b-109">Le type d’objet détermine la disposition et les propriétés par défaut qui sont affichées dans chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="31a8b-109">The object type determines the default layout and properties that are displayed in each column.</span></span> <span data-ttu-id="31a8b-110">Vous pouvez utiliser le paramètre **Property** pour sélectionner les propriétés que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="31a8b-110">You can use the **Property** parameter to select the properties that you want to display.</span></span>

<span data-ttu-id="31a8b-111">PowerShell utilise des formateurs par défaut pour définir le mode d’affichage des types d’objets.</span><span class="sxs-lookup"><span data-stu-id="31a8b-111">PowerShell uses default formatters to define how object types are displayed.</span></span> <span data-ttu-id="31a8b-112">Vous pouvez utiliser `.ps1xml` des fichiers pour créer des vues personnalisées qui affichent une table de sortie avec les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="31a8b-112">You can use `.ps1xml` files to create custom views that display an output table with specified properties.</span></span> <span data-ttu-id="31a8b-113">Après avoir créé une vue personnalisée, utilisez le paramètre **View** pour afficher la table avec votre vue personnalisée.</span><span class="sxs-lookup"><span data-stu-id="31a8b-113">After a custom view is created, use the **View** parameter to display the table with your custom view.</span></span> <span data-ttu-id="31a8b-114">Pour plus d’informations sur les affichages, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="31a8b-114">For more information about views, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="31a8b-115">Vous pouvez utiliser une table de hachage pour ajouter des propriétés calculées à un objet avant de l’afficher et pour spécifier les en-têtes de colonne dans la table.</span><span class="sxs-lookup"><span data-stu-id="31a8b-115">You can use a hash table to add calculated properties to an object before displaying it and to specify the column headings in the table.</span></span> <span data-ttu-id="31a8b-116">Pour ajouter une propriété calculée, utilisez le paramètre **Property** ou **GroupBy** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-116">To add a calculated property, use the **Property** or **GroupBy** parameter.</span></span> <span data-ttu-id="31a8b-117">Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="31a8b-117">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

## <span data-ttu-id="31a8b-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="31a8b-118">EXAMPLES</span></span>

### <span data-ttu-id="31a8b-119">Exemple 1 : mettre en forme l’hôte PowerShell</span><span class="sxs-lookup"><span data-stu-id="31a8b-119">Example 1: Format PowerShell host</span></span>

<span data-ttu-id="31a8b-120">Cet exemple affiche des informations sur le programme hôte pour PowerShell dans une table.</span><span class="sxs-lookup"><span data-stu-id="31a8b-120">This example displays information about the host program for PowerShell in a table.</span></span>

```powershell
Get-Host | Format-Table -AutoSize
```

<span data-ttu-id="31a8b-121">L' `Get-Host` applet de commande obtient les objets **System. Management. Automation. Internal. Host. InternalHost** qui représentent l’hôte.</span><span class="sxs-lookup"><span data-stu-id="31a8b-121">The `Get-Host` cmdlet gets **System.Management.Automation.Internal.Host.InternalHost** objects that represent the host.</span></span> <span data-ttu-id="31a8b-122">Les objets sont envoyés dans le pipeline vers `Format-Table` et affichés dans une table.</span><span class="sxs-lookup"><span data-stu-id="31a8b-122">The objects are sent down the pipeline to `Format-Table` and displayed in a table.</span></span> <span data-ttu-id="31a8b-123">Le paramètre **AutoSize** ajuste les largeurs de colonne pour réduire la troncation.</span><span class="sxs-lookup"><span data-stu-id="31a8b-123">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

### <span data-ttu-id="31a8b-124">Exemple 2 : mettre en forme les processus par BasePriority</span><span class="sxs-lookup"><span data-stu-id="31a8b-124">Example 2: Format processes by BasePriority</span></span>

<span data-ttu-id="31a8b-125">Dans cet exemple, les processus sont affichés dans des groupes qui ont la même propriété **BasePriority** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-125">In this example, processes are displayed in groups that have the same **BasePriority** property.</span></span>

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

<span data-ttu-id="31a8b-126">L' `Get-Process` applet de commande obtient les objets qui représentent chaque processus sur l’ordinateur et les envoie vers le pipeline `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="31a8b-126">The `Get-Process` cmdlet gets objects that represent each process on the computer and sends them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="31a8b-127">Les objets sont triés dans l’ordre de leur propriété **BasePriority** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-127">The objects are sorted in the order of their **BasePriority** property.</span></span>

<span data-ttu-id="31a8b-128">Les objets triés sont envoyés dans le pipeline à `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="31a8b-128">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="31a8b-129">Le paramètre **GroupBy** organise les données de processus en groupes en fonction de la valeur de leur propriété **BasePriority** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-129">The **GroupBy** parameter arranges the process data into groups based on their **BasePriority** property's value.</span></span> <span data-ttu-id="31a8b-130">Le paramètre **Wrap** garantit que les données ne sont pas tronquées.</span><span class="sxs-lookup"><span data-stu-id="31a8b-130">The **Wrap** parameter ensures that data isn't truncated.</span></span>

### <span data-ttu-id="31a8b-131">Exemple 3 : mettre en forme les processus par date de début</span><span class="sxs-lookup"><span data-stu-id="31a8b-131">Example 3: Format processes by start date</span></span>

<span data-ttu-id="31a8b-132">Cet exemple affiche des informations sur les processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31a8b-132">This example displays information about the processes running on the computer.</span></span> <span data-ttu-id="31a8b-133">Les objets sont triés et `Format-Table` utilisent une vue pour regrouper les objets en fonction de leur date de début.</span><span class="sxs-lookup"><span data-stu-id="31a8b-133">The objects are sorted and `Format-Table` uses a view to group the objects by their start date.</span></span>

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

<span data-ttu-id="31a8b-134">`Get-Process` Obtient les objets **System. Diagnostics. Process** qui représentent les processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="31a8b-134">`Get-Process` gets the **System.Diagnostics.Process** objects that represent the processes running on the computer.</span></span> <span data-ttu-id="31a8b-135">Les objets sont envoyés dans le pipeline à `Sort-Object` , et sont triés en fonction de la propriété **StartTime** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-135">The objects are sent down the pipeline to `Sort-Object`, and are sorted based on the **StartTime** property.</span></span>

<span data-ttu-id="31a8b-136">Les objets triés sont envoyés dans le pipeline à `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="31a8b-136">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="31a8b-137">Le paramètre **View** spécifie la vue **StartTime** définie dans le fichier PowerShell `DotNetTypes.format.ps1xml` pour les objets **System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-137">The **View** parameter specifies the **StartTime** view that's defined in the PowerShell `DotNetTypes.format.ps1xml` file for **System.Diagnostics.Process** objects.</span></span> <span data-ttu-id="31a8b-138">La vue **StartTime** convertit l’heure de début de chaque processus en une date brève, puis regroupe les processus par date de début.</span><span class="sxs-lookup"><span data-stu-id="31a8b-138">The **StartTime** view converts each processes start time to a short date and then groups the processes by the start date.</span></span>

<span data-ttu-id="31a8b-139">Le `DotNetTypes.format.ps1xml` fichier contient une vue de **priorité** pour les processus.</span><span class="sxs-lookup"><span data-stu-id="31a8b-139">The `DotNetTypes.format.ps1xml` file contains a **Priority** view for processes.</span></span> <span data-ttu-id="31a8b-140">Vous pouvez créer vos propres `format.ps1xml` fichiers avec des vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="31a8b-140">You can create your own `format.ps1xml` files with customized views.</span></span>

### <span data-ttu-id="31a8b-141">Exemple 4 : utiliser une vue personnalisée pour la sortie de table</span><span class="sxs-lookup"><span data-stu-id="31a8b-141">Example 4: Use a custom view for table output</span></span>

<span data-ttu-id="31a8b-142">Dans cet exemple, une vue personnalisée affiche le contenu d’un répertoire.</span><span class="sxs-lookup"><span data-stu-id="31a8b-142">In this example, a custom view displays a directory's contents.</span></span> <span data-ttu-id="31a8b-143">La vue personnalisée ajoute la colonne **CreationTime** à la sortie de table pour les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** créés par `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="31a8b-143">The custom view adds the **CreationTime** column to the table output for **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span>

<span data-ttu-id="31a8b-144">La vue personnalisée de cet exemple a été créée à partir de la vue définie dans le code source PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31a8b-144">The custom view in this example was created from the view defined in PowerShell source code.</span></span> <span data-ttu-id="31a8b-145">Pour plus d’informations sur les vues et le code utilisé pour créer l’affichage de cet exemple, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span><span class="sxs-lookup"><span data-stu-id="31a8b-145">For more information about views and the code used to create this example's view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span></span>

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

<span data-ttu-id="31a8b-146">`Get-ChildItem` Obtient le contenu du répertoire actif, `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="31a8b-146">`Get-ChildItem` gets the contents of the current directory, `C:\Test`.</span></span> <span data-ttu-id="31a8b-147">Les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** sont envoyés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="31a8b-147">The **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects are sent down the pipeline.</span></span>
<span data-ttu-id="31a8b-148">`Format-Table` utilise le paramètre **View** pour spécifier la vue personnalisée **mygciview** qui comprend la colonne **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-148">`Format-Table` uses the **View** parameter to specify the custom view **mygciview** that includes the **CreationTime** column.</span></span>

<span data-ttu-id="31a8b-149">La sortie par défaut `Format-Table` pour `Get-ChildItem` n’inclut pas la colonne **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-149">The default `Format-Table` output for `Get-ChildItem` doesn't include the **CreationTime** column.</span></span>

### <span data-ttu-id="31a8b-150">Exemple 5 : utiliser les propriétés de la sortie de table</span><span class="sxs-lookup"><span data-stu-id="31a8b-150">Example 5: Use properties for table output</span></span>

<span data-ttu-id="31a8b-151">Cet exemple utilise le paramètre **Property** pour afficher tous les services de l’ordinateur dans une table à deux colonnes qui affiche les propriétés **Name** et **DependentServices**.</span><span class="sxs-lookup"><span data-stu-id="31a8b-151">This example uses the **Property** parameter to display all the computer's services in a two-column table that shows the properties **Name** and **DependentServices**.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="31a8b-152">`Get-Service` Obtient tous les services sur l’ordinateur et envoie les objets **System. ServiceProcess. ServiceController** dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="31a8b-152">`Get-Service` gets all the services on the computer and sends the **System.ServiceProcess.ServiceController** objects down the pipeline.</span></span> <span data-ttu-id="31a8b-153">`Format-Table` utilise le paramètre **Property** pour spécifier que les propriétés **Name** et **DependentServices** sont affichées dans la table.</span><span class="sxs-lookup"><span data-stu-id="31a8b-153">`Format-Table` uses the **Property** parameter to specify that the **Name** and **DependentServices** properties are displayed in the table.</span></span>

<span data-ttu-id="31a8b-154">**Name** et **DependentServices** sont deux des propriétés du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="31a8b-154">**Name** and **DependentServices** are two of the object type's properties.</span></span> <span data-ttu-id="31a8b-155">Pour afficher toutes les propriétés : `Get-Service | Get-Member -MemberType Properties` .</span><span class="sxs-lookup"><span data-stu-id="31a8b-155">To view all the properties: `Get-Service | Get-Member -MemberType Properties`.</span></span>

### <span data-ttu-id="31a8b-156">Exemple 6 : mettre en forme un processus et calculer son temps d’exécution</span><span class="sxs-lookup"><span data-stu-id="31a8b-156">Example 6: Format a process and calculate its running time</span></span>

<span data-ttu-id="31a8b-157">Cet exemple affiche une table avec le nom du processus et la durée d’exécution totale pour les processus du **bloc-notes** de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="31a8b-157">This example displays a table with the process name and total running time for the local computer's **notepad** processes.</span></span> <span data-ttu-id="31a8b-158">La durée d'exécution totale est calculée en soustrayant l'heure de début de chaque processus de l'heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="31a8b-158">The total running time is calculated by subtracting the start time of each process from the current time.</span></span>

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

<span data-ttu-id="31a8b-159">`Get-Process` Obtient tous les processus du **bloc-notes** de l’ordinateur local et les envoie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="31a8b-159">`Get-Process` gets all the local computer's **notepad** processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="31a8b-160">`Format-Table` affiche une table avec deux colonnes : **ProcessName**, `Get-Process` Property et **TotalRunningTime**, une propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="31a8b-160">`Format-Table` displays a table with two columns: **ProcessName**, a `Get-Process` property, and **TotalRunningTime**, a calculated property.</span></span>

<span data-ttu-id="31a8b-161">La propriété **TotalRunningTime** est spécifiée par une table de hachage avec deux clés, **label** et **expression**.</span><span class="sxs-lookup"><span data-stu-id="31a8b-161">The **TotalRunningTime** property is specified by a hash table with two keys, **Label** and **Expression**.</span></span> <span data-ttu-id="31a8b-162">La clé de l' **étiquette** spécifie le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="31a8b-162">The **Label** key specifies the property name.</span></span> <span data-ttu-id="31a8b-163">La clé d' **expression** spécifie le calcul.</span><span class="sxs-lookup"><span data-stu-id="31a8b-163">The **Expression** key specifies the calculation.</span></span> <span data-ttu-id="31a8b-164">L’expression obtient la propriété **StartTime** de chaque objet processus et la soustrait du résultat d’une `Get-Date` commande, qui obtient la date et l’heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="31a8b-164">The expression gets the **StartTime** property of each process object and subtracts it from the result of a `Get-Date` command, which gets the current date and time.</span></span>

### <span data-ttu-id="31a8b-165">Exemple 7 : mettre en forme les processus Notepad</span><span class="sxs-lookup"><span data-stu-id="31a8b-165">Example 7: Format Notepad processes</span></span>

<span data-ttu-id="31a8b-166">Cet exemple utilise `Get-CimInstance` pour obtenir le temps d’exécution de tous les processus du **bloc-notes** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="31a8b-166">This example uses `Get-CimInstance` to get the running time for all **notepad** processes on the local computer.</span></span> <span data-ttu-id="31a8b-167">Vous pouvez utiliser `Get-CimInstance` avec le paramètre **ComputerName** pour récupérer des informations à partir d’ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="31a8b-167">You can use `Get-CimInstance` with the **ComputerName** parameter to get information from remote computers.</span></span>

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

<span data-ttu-id="31a8b-168">`Get-CimInstance` obtient des instances de la classe de **WIN32_PROCESS** WMI qui décrit tous les processus de l’ordinateur local nommés **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="31a8b-168">`Get-CimInstance` gets instances of the WMI **Win32_Process** class that describes all the local computer's processes named **notepad.exe**.</span></span> <span data-ttu-id="31a8b-169">Les objets processus sont stockés dans la `$Processes` variable.</span><span class="sxs-lookup"><span data-stu-id="31a8b-169">The process objects are stored in the `$Processes` variable.</span></span>

<span data-ttu-id="31a8b-170">Les objets processus de la `$Processes` variable sont envoyés dans le pipeline à `Format-Table` , qui affiche la propriété **ProcessName** et une nouvelle propriété calculée, **durée totale d’exécution**.</span><span class="sxs-lookup"><span data-stu-id="31a8b-170">The process objects in the `$Processes` variable are sent down the pipeline to `Format-Table`, which displays the **ProcessName** property and a new calculated property, **Total Running Time**.</span></span>

<span data-ttu-id="31a8b-171">La commande attribue le nom de la nouvelle propriété calculée, **durée totale d’exécution**, à la clé de l' **étiquette** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-171">The command assigns the name of the new calculated property, **Total Running Time**, to the **Label** key.</span></span> <span data-ttu-id="31a8b-172">Le bloc de script de la clé d' **expression** calcule la durée d’exécution du processus en soustrayant la date de création du processus de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="31a8b-172">The **Expression** key's script block calculates how long the process has been running by subtracting the processes creation date from the current date.</span></span> <span data-ttu-id="31a8b-173">L' `Get-Date` applet de commande obtient la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="31a8b-173">The `Get-Date` cmdlet gets the current date.</span></span> <span data-ttu-id="31a8b-174">La date de création est soustraite de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="31a8b-174">The creation date is subtracted from the current date.</span></span> <span data-ttu-id="31a8b-175">Le résultat est la valeur de la **durée d’exécution totale**.</span><span class="sxs-lookup"><span data-stu-id="31a8b-175">The result is the value of **Total Running Time**.</span></span>

### <span data-ttu-id="31a8b-176">Exemple 8 : dépannage des erreurs de format</span><span class="sxs-lookup"><span data-stu-id="31a8b-176">Example 8: Troubleshooting format errors</span></span>

<span data-ttu-id="31a8b-177">Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.</span><span class="sxs-lookup"><span data-stu-id="31a8b-177">The following examples show the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday

InvalidArgument: Failed to evaluate expression " $_ / $null ".
```

## <span data-ttu-id="31a8b-178">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31a8b-178">PARAMETERS</span></span>

### <span data-ttu-id="31a8b-179">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="31a8b-179">-AutoSize</span></span>

<span data-ttu-id="31a8b-180">Indique que l’applet de commande ajuste la taille de la colonne et le nombre de colonnes en fonction de la largeur des données.</span><span class="sxs-lookup"><span data-stu-id="31a8b-180">Indicates that the cmdlet adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="31a8b-181">Par défaut, la vue détermine la taille et le nombre de colonnes.</span><span class="sxs-lookup"><span data-stu-id="31a8b-181">By default, the column size and number are determined by the view.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-182">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="31a8b-182">-DisplayError</span></span>

<span data-ttu-id="31a8b-183">Indique que l’applet de commande affiche les erreurs sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="31a8b-183">Indicates that the cmdlet displays errors on the command line.</span></span> <span data-ttu-id="31a8b-184">Ce paramètre peut être utilisé comme une aide au débogage lorsque vous mettez en forme des expressions dans une `Format-Table` commande et que vous devez dépanner les expressions.</span><span class="sxs-lookup"><span data-stu-id="31a8b-184">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-185">-Développer</span><span class="sxs-lookup"><span data-stu-id="31a8b-185">-Expand</span></span>

<span data-ttu-id="31a8b-186">Spécifie le format de l’objet de collection et les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="31a8b-186">Specifies the format of the collection object and the objects in the collection.</span></span> <span data-ttu-id="31a8b-187">Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l’interface [ICollection](/dotnet/api/system.collections.icollection) ([System. Collections](/dotnet/api/system.collections)).</span><span class="sxs-lookup"><span data-stu-id="31a8b-187">This parameter is designed to format objects that support the [ICollection](/dotnet/api/system.collections.icollection) ([System.Collections](/dotnet/api/system.collections)) interface.</span></span> <span data-ttu-id="31a8b-188">La valeur par défaut est **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="31a8b-188">The default value is **EnumOnly**.</span></span>
<span data-ttu-id="31a8b-189">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="31a8b-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="31a8b-190">**EnumOnly**: affiche les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="31a8b-190">**EnumOnly**: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="31a8b-191">**CoreOnly**: affiche les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="31a8b-191">**CoreOnly**: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="31a8b-192">**Both**: affiche les propriétés de l’objet de collection et les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="31a8b-192">**Both**: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-193">-Force</span><span class="sxs-lookup"><span data-stu-id="31a8b-193">-Force</span></span>

<span data-ttu-id="31a8b-194">Indique que l’applet de commande ordonne à l’applet de commande d’afficher toutes les informations sur l’erreur.</span><span class="sxs-lookup"><span data-stu-id="31a8b-194">Indicates that the cmdlet directs the cmdlet to display all the error information.</span></span> <span data-ttu-id="31a8b-195">Utilisez avec le paramètre **DisplayError** ou **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="31a8b-195">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="31a8b-196">Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.</span><span class="sxs-lookup"><span data-stu-id="31a8b-196">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-197">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="31a8b-197">-GroupBy</span></span>

<span data-ttu-id="31a8b-198">Spécifie la sortie triée dans des tables distinctes en fonction d’une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="31a8b-198">Specifies sorted output in separate tables based on a property value.</span></span> <span data-ttu-id="31a8b-199">Par exemple, vous pouvez utiliser **GroupBy** pour répertorier les services dans des tables distinctes en fonction de leur état.</span><span class="sxs-lookup"><span data-stu-id="31a8b-199">For example, you can use **GroupBy** to list services in separate tables based on their status.</span></span>

<span data-ttu-id="31a8b-200">Entrez une expression ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="31a8b-200">Enter an expression or a property.</span></span> <span data-ttu-id="31a8b-201">Le paramètre **GroupBy** s’attend à ce que les objets soient triés.</span><span class="sxs-lookup"><span data-stu-id="31a8b-201">The **GroupBy** parameter expects that the objects are sorted.</span></span>
<span data-ttu-id="31a8b-202">Utilisez l' `Sort-Object` applet de commande avant `Format-Table` d’utiliser pour regrouper les objets.</span><span class="sxs-lookup"><span data-stu-id="31a8b-202">Use the `Sort-Object` cmdlet before using `Format-Table` to group the objects.</span></span>

<span data-ttu-id="31a8b-203">La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="31a8b-203">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="31a8b-204">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="31a8b-204">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="31a8b-205">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="31a8b-205">Valid key-value pairs are:</span></span>

- <span data-ttu-id="31a8b-206">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="31a8b-206">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="31a8b-207">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="31a8b-207">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="31a8b-208">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="31a8b-208">FormatString - `<string>`</span></span>

<span data-ttu-id="31a8b-209">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="31a8b-209">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-210">-HideTableHeaders</span><span class="sxs-lookup"><span data-stu-id="31a8b-210">-HideTableHeaders</span></span>

<span data-ttu-id="31a8b-211">Omet les en-têtes de colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="31a8b-211">Omits the column headings from the table.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-212">-InputObject</span><span class="sxs-lookup"><span data-stu-id="31a8b-212">-InputObject</span></span>

<span data-ttu-id="31a8b-213">Spécifie les objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="31a8b-213">Specifies the objects to format.</span></span> <span data-ttu-id="31a8b-214">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="31a8b-214">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-215">-Propriété</span><span class="sxs-lookup"><span data-stu-id="31a8b-215">-Property</span></span>

<span data-ttu-id="31a8b-216">Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="31a8b-216">Specifies the object properties that appear in the display and the order in which they appear.</span></span> <span data-ttu-id="31a8b-217">Tapez un ou plusieurs noms de propriété, en les séparant par des virgules, ou utilisez une table de hachage pour afficher une propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="31a8b-217">Type one or more property names, separated by commas, or use a hash table to display a calculated property.</span></span> <span data-ttu-id="31a8b-218">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="31a8b-218">Wildcards are permitted.</span></span>

<span data-ttu-id="31a8b-219">Si vous omettez ce paramètre, les propriétés qui s’affichent dans l’affichage dépendent des propriétés du premier objet.</span><span class="sxs-lookup"><span data-stu-id="31a8b-219">If you omit this parameter, the properties that appear in the display depend on the first object's properties.</span></span> <span data-ttu-id="31a8b-220">Par exemple, si le premier objet a **PropertyA** et **PropertyB** , mais que les objets suivants possèdent **PropertyA**, **PropertyB** et **PropertyC**, seuls les en-têtes **PropertyA** et **PropertyB** s’afficheront.</span><span class="sxs-lookup"><span data-stu-id="31a8b-220">For example, if the first object has **PropertyA** and **PropertyB** but subsequent objects have **PropertyA**, **PropertyB**, and **PropertyC**, then only the **PropertyA** and **PropertyB** headers will display.</span></span>

<span data-ttu-id="31a8b-221">Le paramètre **Property** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="31a8b-221">The **Property** parameter is optional.</span></span> <span data-ttu-id="31a8b-222">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="31a8b-222">You can't use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="31a8b-223">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="31a8b-223">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="31a8b-224">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="31a8b-224">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="31a8b-225">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="31a8b-225">Valid key-value pairs are:</span></span>

- <span data-ttu-id="31a8b-226">Nom (ou étiquette) `<string>`</span><span class="sxs-lookup"><span data-stu-id="31a8b-226">Name (or Label) `<string>`</span></span>
- <span data-ttu-id="31a8b-227">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="31a8b-227">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="31a8b-228">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="31a8b-228">FormatString - `<string>`</span></span>
- <span data-ttu-id="31a8b-229">Largeur- `<int32>` -doit être supérieur à `0`</span><span class="sxs-lookup"><span data-stu-id="31a8b-229">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="31a8b-230">Alignment : la valeur peut être `Left` , `Center` ou `Right`</span><span class="sxs-lookup"><span data-stu-id="31a8b-230">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="31a8b-231">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="31a8b-231">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="31a8b-232">-RepeatHeader</span><span class="sxs-lookup"><span data-stu-id="31a8b-232">-RepeatHeader</span></span>

<span data-ttu-id="31a8b-233">Répète l’affichage de l’en-tête d’un tableau après chaque écran complet.</span><span class="sxs-lookup"><span data-stu-id="31a8b-233">Repeats displaying the header of a table after every screen full.</span></span> <span data-ttu-id="31a8b-234">L’en-tête répété est utile lorsque la sortie est dirigée vers un récepteur de radiomessagerie tel que `less` ou, `more` ou en utilisant un lecteur d’écran.</span><span class="sxs-lookup"><span data-stu-id="31a8b-234">The repeated header is useful when the output is piped to a pager such as `less` or `more` or paging with a screen reader.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-235">-ShowError</span><span class="sxs-lookup"><span data-stu-id="31a8b-235">-ShowError</span></span>

<span data-ttu-id="31a8b-236">Ce paramètre envoie des erreurs via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="31a8b-236">This parameter sends errors through the pipeline.</span></span> <span data-ttu-id="31a8b-237">Ce paramètre peut être utilisé comme une aide au débogage lorsque vous mettez en forme des expressions dans une `Format-Table` commande et que vous devez dépanner les expressions.</span><span class="sxs-lookup"><span data-stu-id="31a8b-237">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-238">-Afficher</span><span class="sxs-lookup"><span data-stu-id="31a8b-238">-View</span></span>

<span data-ttu-id="31a8b-239">À compter de PowerShell 6, les vues par défaut sont définies dans le `C#` code source PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31a8b-239">Beginning in PowerShell 6, the default views are defined in PowerShell `C#` source code.</span></span> <span data-ttu-id="31a8b-240">Les `*.format.ps1xml` fichiers de powershell 5,1 et versions antérieures n’existent pas dans PowerShell 6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="31a8b-240">The `*.format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="31a8b-241">Le paramètre **View** vous permet de spécifier un autre format ou une autre vue personnalisée pour la table.</span><span class="sxs-lookup"><span data-stu-id="31a8b-241">The **View** parameter lets you specify an alternate format or custom view for the table.</span></span> <span data-ttu-id="31a8b-242">Vous pouvez utiliser les vues PowerShell par défaut ou créer des vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="31a8b-242">You can use the default PowerShell views or create custom views.</span></span> <span data-ttu-id="31a8b-243">Pour plus d’informations sur la création d’un affichage personnalisé, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="31a8b-243">For more information about how to create a custom view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="31a8b-244">Les vues alternatives et personnalisées pour le paramètre **View** doivent utiliser le format de table ; sinon, `Format-Table` échoue.</span><span class="sxs-lookup"><span data-stu-id="31a8b-244">The alternate and custom views for the **View** parameter must use the table format, otherwise, `Format-Table` fails.</span></span> <span data-ttu-id="31a8b-245">Si l’autre vue est une liste, utilisez l' `Format-List` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31a8b-245">If the alternate view is a list, use the `Format-List` cmdlet.</span></span> <span data-ttu-id="31a8b-246">Si l’autre vue n’est ni une liste ni une table, utilisez l’applet de commande `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="31a8b-246">If the alternate view isn't a list or a table, use the `Format-Custom` cmdlet.</span></span>

<span data-ttu-id="31a8b-247">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="31a8b-247">You can't use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="31a8b-248">-Wrap</span><span class="sxs-lookup"><span data-stu-id="31a8b-248">-Wrap</span></span>

<span data-ttu-id="31a8b-249">Affiche le texte qui dépasse de la largeur de colonne sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="31a8b-249">Displays text that exceeds the column width on the next line.</span></span> <span data-ttu-id="31a8b-250">Par défaut, le texte qui dépasse de la largeur de colonne est tronqué.</span><span class="sxs-lookup"><span data-stu-id="31a8b-250">By default, text that exceeds the column width is truncated.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31a8b-251">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31a8b-251">CommonParameters</span></span>

<span data-ttu-id="31a8b-252">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="31a8b-252">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="31a8b-253">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="31a8b-253">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="31a8b-254">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="31a8b-254">INPUTS</span></span>

### <span data-ttu-id="31a8b-255">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="31a8b-255">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="31a8b-256">Vous pouvez envoyer n’importe quel objet dans le pipeline à `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="31a8b-256">You can send any object down the pipeline to `Format-Table`.</span></span>

## <span data-ttu-id="31a8b-257">SORTIES</span><span class="sxs-lookup"><span data-stu-id="31a8b-257">OUTPUTS</span></span>

### <span data-ttu-id="31a8b-258">Microsoft. PowerShell. Commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="31a8b-258">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="31a8b-259">`Format-Table` retourne les objets de format représentant la table.</span><span class="sxs-lookup"><span data-stu-id="31a8b-259">`Format-Table` returns format objects that represent the table.</span></span>

## <span data-ttu-id="31a8b-260">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="31a8b-260">NOTES</span></span>

## <span data-ttu-id="31a8b-261">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="31a8b-261">RELATED LINKS</span></span>

[<span data-ttu-id="31a8b-262">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="31a8b-262">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="31a8b-263">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="31a8b-263">about_Format.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="31a8b-264">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="31a8b-264">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="31a8b-265">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="31a8b-265">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="31a8b-266">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="31a8b-266">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="31a8b-267">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="31a8b-267">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="31a8b-268">Format-List</span><span class="sxs-lookup"><span data-stu-id="31a8b-268">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="31a8b-269">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="31a8b-269">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="31a8b-270">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="31a8b-270">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="31a8b-271">Get-Member</span><span class="sxs-lookup"><span data-stu-id="31a8b-271">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="31a8b-272">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="31a8b-272">Get-CimInstance</span></span>](../CimCmdlets/Get-CimInstance.md)

[<span data-ttu-id="31a8b-273">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="31a8b-273">Update-FormatData</span></span>](Update-FormatData.md)
