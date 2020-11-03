---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 06f0573496f04d6790d7899afa5809ede720adee
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205989"
---
# <span data-ttu-id="56a6f-103">Format-Table</span><span class="sxs-lookup"><span data-stu-id="56a6f-103">Format-Table</span></span>

## <span data-ttu-id="56a6f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="56a6f-104">SYNOPSIS</span></span>
<span data-ttu-id="56a6f-105">Met en forme la sortie en tant que table.</span><span class="sxs-lookup"><span data-stu-id="56a6f-105">Formats the output as a table.</span></span>

## <span data-ttu-id="56a6f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56a6f-106">SYNTAX</span></span>

### <span data-ttu-id="56a6f-107">Tous</span><span class="sxs-lookup"><span data-stu-id="56a6f-107">All</span></span>

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="56a6f-108">Description</span><span class="sxs-lookup"><span data-stu-id="56a6f-108">DESCRIPTION</span></span>

<span data-ttu-id="56a6f-109">L' `Format-Table` applet de commande met en forme la sortie d’une commande en tant que table avec les propriétés sélectionnées de l’objet dans chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="56a6f-109">The `Format-Table` cmdlet formats the output of a command as a table with the selected properties of the object in each column.</span></span> <span data-ttu-id="56a6f-110">Le type d’objet détermine la disposition et les propriétés par défaut qui sont affichées dans chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="56a6f-110">The object type determines the default layout and properties that are displayed in each column.</span></span> <span data-ttu-id="56a6f-111">Vous pouvez utiliser le paramètre **Property** pour sélectionner les propriétés que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="56a6f-111">You can use the **Property** parameter to select the properties that you want to display.</span></span>

<span data-ttu-id="56a6f-112">PowerShell utilise des formateurs par défaut pour définir le mode d’affichage des types d’objets.</span><span class="sxs-lookup"><span data-stu-id="56a6f-112">PowerShell uses default formatters to define how object types are displayed.</span></span> <span data-ttu-id="56a6f-113">Vous pouvez utiliser `.ps1xml` des fichiers pour créer des vues personnalisées qui affichent une table de sortie avec les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="56a6f-113">You can use `.ps1xml` files to create custom views that display an output table with specified properties.</span></span> <span data-ttu-id="56a6f-114">Après avoir créé une vue personnalisée, utilisez le paramètre **View** pour afficher la table avec votre vue personnalisée.</span><span class="sxs-lookup"><span data-stu-id="56a6f-114">After a custom view is created, use the **View** parameter to display the table with your custom view.</span></span> <span data-ttu-id="56a6f-115">Pour plus d’informations sur les affichages, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="56a6f-115">For more information about views, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="56a6f-116">Vous pouvez utiliser une table de hachage pour ajouter des propriétés calculées à un objet avant de l’afficher et pour spécifier les en-têtes de colonne dans la table.</span><span class="sxs-lookup"><span data-stu-id="56a6f-116">You can use a hash table to add calculated properties to an object before displaying it and to specify the column headings in the table.</span></span> <span data-ttu-id="56a6f-117">Pour ajouter une propriété calculée, utilisez le paramètre **Property** ou **GroupBy** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-117">To add a calculated property, use the **Property** or **GroupBy** parameter.</span></span> <span data-ttu-id="56a6f-118">Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="56a6f-118">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

## <span data-ttu-id="56a6f-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="56a6f-119">EXAMPLES</span></span>

### <span data-ttu-id="56a6f-120">Exemple 1 : mettre en forme l’hôte PowerShell</span><span class="sxs-lookup"><span data-stu-id="56a6f-120">Example 1: Format PowerShell host</span></span>

<span data-ttu-id="56a6f-121">Cet exemple affiche des informations sur le programme hôte pour PowerShell dans une table.</span><span class="sxs-lookup"><span data-stu-id="56a6f-121">This example displays information about the host program for PowerShell in a table.</span></span>

```powershell
Get-Host | Format-Table -AutoSize
```

<span data-ttu-id="56a6f-122">L' `Get-Host` applet de commande obtient les objets **System. Management. Automation. Internal. Host. InternalHost** qui représentent l’hôte.</span><span class="sxs-lookup"><span data-stu-id="56a6f-122">The `Get-Host` cmdlet gets **System.Management.Automation.Internal.Host.InternalHost** objects that represent the host.</span></span> <span data-ttu-id="56a6f-123">Les objets sont envoyés dans le pipeline vers `Format-Table` et affichés dans une table.</span><span class="sxs-lookup"><span data-stu-id="56a6f-123">The objects are sent down the pipeline to `Format-Table` and displayed in a table.</span></span> <span data-ttu-id="56a6f-124">Le paramètre **AutoSize** ajuste les largeurs de colonne pour réduire la troncation.</span><span class="sxs-lookup"><span data-stu-id="56a6f-124">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

### <span data-ttu-id="56a6f-125">Exemple 2 : mettre en forme les processus par BasePriority</span><span class="sxs-lookup"><span data-stu-id="56a6f-125">Example 2: Format processes by BasePriority</span></span>

<span data-ttu-id="56a6f-126">Dans cet exemple, les processus sont affichés dans des groupes qui ont la même propriété **BasePriority** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-126">In this example, processes are displayed in groups that have the same **BasePriority** property.</span></span>

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

<span data-ttu-id="56a6f-127">L' `Get-Process` applet de commande obtient les objets qui représentent chaque processus sur l’ordinateur et les envoie vers le pipeline `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="56a6f-127">The `Get-Process` cmdlet gets objects that represent each process on the computer and sends them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="56a6f-128">Les objets sont triés dans l’ordre de leur propriété **BasePriority** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-128">The objects are sorted in the order of their **BasePriority** property.</span></span>

<span data-ttu-id="56a6f-129">Les objets triés sont envoyés dans le pipeline à `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="56a6f-129">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="56a6f-130">Le paramètre **GroupBy** organise les données de processus en groupes en fonction de la valeur de leur propriété **BasePriority** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-130">The **GroupBy** parameter arranges the process data into groups based on their **BasePriority** property's value.</span></span> <span data-ttu-id="56a6f-131">Le paramètre **Wrap** garantit que les données ne sont pas tronquées.</span><span class="sxs-lookup"><span data-stu-id="56a6f-131">The **Wrap** parameter ensures that data isn't truncated.</span></span>

### <span data-ttu-id="56a6f-132">Exemple 3 : mettre en forme les processus par date de début</span><span class="sxs-lookup"><span data-stu-id="56a6f-132">Example 3: Format processes by start date</span></span>

<span data-ttu-id="56a6f-133">Cet exemple affiche des informations sur les processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56a6f-133">This example displays information about the processes running on the computer.</span></span> <span data-ttu-id="56a6f-134">Les objets sont triés et `Format-Table` utilisent une vue pour regrouper les objets en fonction de leur date de début.</span><span class="sxs-lookup"><span data-stu-id="56a6f-134">The objects are sorted and `Format-Table` uses a view to group the objects by their start date.</span></span>

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

<span data-ttu-id="56a6f-135">`Get-Process` Obtient les objets **System. Diagnostics. Process** qui représentent les processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56a6f-135">`Get-Process` gets the **System.Diagnostics.Process** objects that represent the processes running on the computer.</span></span> <span data-ttu-id="56a6f-136">Les objets sont envoyés dans le pipeline à `Sort-Object` , et sont triés en fonction de la propriété **StartTime** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-136">The objects are sent down the pipeline to `Sort-Object`, and are sorted based on the **StartTime** property.</span></span>

<span data-ttu-id="56a6f-137">Les objets triés sont envoyés dans le pipeline à `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="56a6f-137">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="56a6f-138">Le paramètre **View** spécifie la vue **StartTime** définie dans le fichier PowerShell `DotNetTypes.format.ps1xml` pour les objets **System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-138">The **View** parameter specifies the **StartTime** view that's defined in the PowerShell `DotNetTypes.format.ps1xml` file for **System.Diagnostics.Process** objects.</span></span> <span data-ttu-id="56a6f-139">La vue **StartTime** convertit l’heure de début de chaque processus en une date brève, puis regroupe les processus par date de début.</span><span class="sxs-lookup"><span data-stu-id="56a6f-139">The **StartTime** view converts each processes start time to a short date and then groups the processes by the start date.</span></span>

<span data-ttu-id="56a6f-140">Le `DotNetTypes.format.ps1xml` fichier contient une vue de **priorité** pour les processus.</span><span class="sxs-lookup"><span data-stu-id="56a6f-140">The `DotNetTypes.format.ps1xml` file contains a **Priority** view for processes.</span></span> <span data-ttu-id="56a6f-141">Vous pouvez créer vos propres `format.ps1xml` fichiers avec des vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="56a6f-141">You can create your own `format.ps1xml` files with customized views.</span></span>

### <span data-ttu-id="56a6f-142">Exemple 4 : utiliser une vue personnalisée pour la sortie de table</span><span class="sxs-lookup"><span data-stu-id="56a6f-142">Example 4: Use a custom view for table output</span></span>

<span data-ttu-id="56a6f-143">Dans cet exemple, une vue personnalisée affiche le contenu d’un répertoire.</span><span class="sxs-lookup"><span data-stu-id="56a6f-143">In this example, a custom view displays a directory's contents.</span></span> <span data-ttu-id="56a6f-144">La vue personnalisée ajoute la colonne **CreationTime** à la sortie de table pour les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** créés par `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="56a6f-144">The custom view adds the **CreationTime** column to the table output for **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span>

<span data-ttu-id="56a6f-145">La vue personnalisée de cet exemple a été créée à partir de la vue définie dans le code source PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56a6f-145">The custom view in this example was created from the view defined in PowerShell source code.</span></span> <span data-ttu-id="56a6f-146">Pour plus d’informations sur les vues et le code utilisé pour créer l’affichage de cet exemple, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span><span class="sxs-lookup"><span data-stu-id="56a6f-146">For more information about views and the code used to create this example's view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span></span>

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

<span data-ttu-id="56a6f-147">`Get-ChildItem` Obtient le contenu du répertoire actif, `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="56a6f-147">`Get-ChildItem` gets the contents of the current directory, `C:\Test`.</span></span> <span data-ttu-id="56a6f-148">Les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** sont envoyés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="56a6f-148">The **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects are sent down the pipeline.</span></span>
<span data-ttu-id="56a6f-149">`Format-Table` utilise le paramètre **View** pour spécifier la vue personnalisée **mygciview** qui comprend la colonne **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-149">`Format-Table` uses the **View** parameter to specify the custom view **mygciview** that includes the **CreationTime** column.</span></span>

<span data-ttu-id="56a6f-150">La sortie par défaut `Format-Table` pour `Get-ChildItem` n’inclut pas la colonne **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-150">The default `Format-Table` output for `Get-ChildItem` doesn't include the **CreationTime** column.</span></span>

### <span data-ttu-id="56a6f-151">Exemple 5 : utiliser les propriétés de la sortie de table</span><span class="sxs-lookup"><span data-stu-id="56a6f-151">Example 5: Use properties for table output</span></span>

<span data-ttu-id="56a6f-152">Cet exemple utilise le paramètre **Property** pour afficher tous les services de l’ordinateur dans une table à deux colonnes qui affiche les propriétés **Name** et **DependentServices** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-152">This example uses the **Property** parameter to display all the computer's services in a two-column table that shows the properties **Name** and **DependentServices** .</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="56a6f-153">`Get-Service` Obtient tous les services sur l’ordinateur et envoie les objets **System. ServiceProcess. ServiceController** dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="56a6f-153">`Get-Service` gets all the services on the computer and sends the **System.ServiceProcess.ServiceController** objects down the pipeline.</span></span> <span data-ttu-id="56a6f-154">`Format-Table` utilise le paramètre **Property** pour spécifier que les propriétés **Name** et **DependentServices** sont affichées dans la table.</span><span class="sxs-lookup"><span data-stu-id="56a6f-154">`Format-Table` uses the **Property** parameter to specify that the **Name** and **DependentServices** properties are displayed in the table.</span></span>

<span data-ttu-id="56a6f-155">**Name** et **DependentServices** sont deux des propriétés du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="56a6f-155">**Name** and **DependentServices** are two of the object type's properties.</span></span> <span data-ttu-id="56a6f-156">Pour afficher toutes les propriétés : `Get-Service | Get-Member -MemberType Properties` .</span><span class="sxs-lookup"><span data-stu-id="56a6f-156">To view all the properties: `Get-Service | Get-Member -MemberType Properties`.</span></span>

### <span data-ttu-id="56a6f-157">Exemple 6 : mettre en forme un processus et calculer son temps d’exécution</span><span class="sxs-lookup"><span data-stu-id="56a6f-157">Example 6: Format a process and calculate its running time</span></span>

<span data-ttu-id="56a6f-158">Cet exemple affiche une table avec le nom du processus et la durée d’exécution totale pour les processus du **bloc-notes** de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56a6f-158">This example displays a table with the process name and total running time for the local computer's **notepad** processes.</span></span> <span data-ttu-id="56a6f-159">La durée d'exécution totale est calculée en soustrayant l'heure de début de chaque processus de l'heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="56a6f-159">The total running time is calculated by subtracting the start time of each process from the current time.</span></span>

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

<span data-ttu-id="56a6f-160">`Get-Process` Obtient tous les processus du **bloc-notes** de l’ordinateur local et les envoie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="56a6f-160">`Get-Process` gets all the local computer's **notepad** processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="56a6f-161">`Format-Table` affiche une table avec deux colonnes : **ProcessName** , `Get-Process` Property et **TotalRunningTime** , une propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="56a6f-161">`Format-Table` displays a table with two columns: **ProcessName** , a `Get-Process` property, and **TotalRunningTime** , a calculated property.</span></span>

<span data-ttu-id="56a6f-162">La propriété **TotalRunningTime** est spécifiée par une table de hachage avec deux clés, **label** et **expression** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-162">The **TotalRunningTime** property is specified by a hash table with two keys, **Label** and **Expression** .</span></span> <span data-ttu-id="56a6f-163">La clé de l' **étiquette** spécifie le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="56a6f-163">The **Label** key specifies the property name.</span></span> <span data-ttu-id="56a6f-164">La clé d' **expression** spécifie le calcul.</span><span class="sxs-lookup"><span data-stu-id="56a6f-164">The **Expression** key specifies the calculation.</span></span> <span data-ttu-id="56a6f-165">L’expression obtient la propriété **StartTime** de chaque objet processus et la soustrait du résultat d’une `Get-Date` commande, qui obtient la date et l’heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="56a6f-165">The expression gets the **StartTime** property of each process object and subtracts it from the result of a `Get-Date` command, which gets the current date and time.</span></span>

### <span data-ttu-id="56a6f-166">Exemple 7 : mettre en forme les processus Notepad</span><span class="sxs-lookup"><span data-stu-id="56a6f-166">Example 7: Format Notepad processes</span></span>

<span data-ttu-id="56a6f-167">Cet exemple utilise `Get-CimInstance` pour obtenir le temps d’exécution de tous les processus du **bloc-notes** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56a6f-167">This example uses `Get-CimInstance` to get the running time for all **notepad** processes on the local computer.</span></span> <span data-ttu-id="56a6f-168">Vous pouvez utiliser `Get-CimInstance` avec le paramètre **ComputerName** pour récupérer des informations à partir d’ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="56a6f-168">You can use `Get-CimInstance` with the **ComputerName** parameter to get information from remote computers.</span></span>

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

<span data-ttu-id="56a6f-169">`Get-CimInstance` obtient des instances de la classe de **WIN32_PROCESS** WMI qui décrit tous les processus de l’ordinateur local nommés **notepad.exe** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-169">`Get-CimInstance` gets instances of the WMI **Win32_Process** class that describes all the local computer's processes named **notepad.exe** .</span></span> <span data-ttu-id="56a6f-170">Les objets processus sont stockés dans la `$Processes` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6f-170">The process objects are stored in the `$Processes` variable.</span></span>

<span data-ttu-id="56a6f-171">Les objets processus de la `$Processes` variable sont envoyés dans le pipeline à `Format-Table` , qui affiche la propriété **ProcessName** et une nouvelle propriété calculée, **durée totale d’exécution** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-171">The process objects in the `$Processes` variable are sent down the pipeline to `Format-Table`, which displays the **ProcessName** property and a new calculated property, **Total Running Time** .</span></span>

<span data-ttu-id="56a6f-172">La commande attribue le nom de la nouvelle propriété calculée, **durée totale d’exécution** , à la clé de l' **étiquette** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-172">The command assigns the name of the new calculated property, **Total Running Time** , to the **Label** key.</span></span> <span data-ttu-id="56a6f-173">Le bloc de script de la clé d' **expression** calcule la durée d’exécution du processus en soustrayant la date de création du processus de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="56a6f-173">The **Expression** key's script block calculates how long the process has been running by subtracting the processes creation date from the current date.</span></span> <span data-ttu-id="56a6f-174">L' `Get-Date` applet de commande obtient la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="56a6f-174">The `Get-Date` cmdlet gets the current date.</span></span> <span data-ttu-id="56a6f-175">La date de création est soustraite de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="56a6f-175">The creation date is subtracted from the current date.</span></span> <span data-ttu-id="56a6f-176">Le résultat est la valeur de la **durée d’exécution totale** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-176">The result is the value of **Total Running Time** .</span></span>

### <span data-ttu-id="56a6f-177">Exemple 8 : dépannage des erreurs de format</span><span class="sxs-lookup"><span data-stu-id="56a6f-177">Example 8: Troubleshooting format errors</span></span>

<span data-ttu-id="56a6f-178">Les exemples suivants montrent les résultats de l’ajout des paramètres **DisplayError** ou **ShowError** avec une expression.</span><span class="sxs-lookup"><span data-stu-id="56a6f-178">The following examples show the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

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
Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (11/27/2019 12:52:38:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="56a6f-179">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56a6f-179">PARAMETERS</span></span>

### <span data-ttu-id="56a6f-180">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="56a6f-180">-AutoSize</span></span>

<span data-ttu-id="56a6f-181">Indique que l’applet de commande ajuste la taille de la colonne et le nombre de colonnes en fonction de la largeur des données.</span><span class="sxs-lookup"><span data-stu-id="56a6f-181">Indicates that the cmdlet adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="56a6f-182">Par défaut, la vue détermine la taille et le nombre de colonnes.</span><span class="sxs-lookup"><span data-stu-id="56a6f-182">By default, the column size and number are determined by the view.</span></span>

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

### <span data-ttu-id="56a6f-183">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="56a6f-183">-DisplayError</span></span>

<span data-ttu-id="56a6f-184">Indique que l’applet de commande affiche les erreurs sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="56a6f-184">Indicates that the cmdlet displays errors on the command line.</span></span> <span data-ttu-id="56a6f-185">Ce paramètre peut être utilisé comme une aide au débogage lorsque vous mettez en forme des expressions dans une `Format-Table` commande et que vous devez dépanner les expressions.</span><span class="sxs-lookup"><span data-stu-id="56a6f-185">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

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

### <span data-ttu-id="56a6f-186">-Développer</span><span class="sxs-lookup"><span data-stu-id="56a6f-186">-Expand</span></span>

<span data-ttu-id="56a6f-187">Spécifie le format de l’objet de collection et les objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="56a6f-187">Specifies the format of the collection object and the objects in the collection.</span></span> <span data-ttu-id="56a6f-188">Ce paramètre est conçu pour mettre en forme les objets qui prennent en charge l’interface [ICollection](/dotnet/api/system.collections.icollection) ([System. Collections](/dotnet/api/system.collections)).</span><span class="sxs-lookup"><span data-stu-id="56a6f-188">This parameter is designed to format objects that support the [ICollection](/dotnet/api/system.collections.icollection) ([System.Collections](/dotnet/api/system.collections)) interface.</span></span> <span data-ttu-id="56a6f-189">La valeur par défaut est **EnumOnly** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-189">The default value is **EnumOnly** .</span></span>
<span data-ttu-id="56a6f-190">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="56a6f-190">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="56a6f-191">**EnumOnly** : affiche les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="56a6f-191">**EnumOnly** : Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="56a6f-192">**CoreOnly** : affiche les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="56a6f-192">**CoreOnly** : Displays the properties of the collection object.</span></span>
- <span data-ttu-id="56a6f-193">**Both** : affiche les propriétés de l’objet de collection et les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="56a6f-193">**Both** : Displays the properties of the collection object and the properties of objects in the collection.</span></span>

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

### <span data-ttu-id="56a6f-194">-Force</span><span class="sxs-lookup"><span data-stu-id="56a6f-194">-Force</span></span>

<span data-ttu-id="56a6f-195">Indique que l’applet de commande ordonne à l’applet de commande d’afficher toutes les informations sur l’erreur.</span><span class="sxs-lookup"><span data-stu-id="56a6f-195">Indicates that the cmdlet directs the cmdlet to display all the error information.</span></span> <span data-ttu-id="56a6f-196">Utilisez avec le paramètre **DisplayError** ou **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="56a6f-196">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="56a6f-197">Par défaut, quand un objet d'erreur est écrit dans les flux d'erreur ou d'affichage, seules certaines informations sur l'erreur s'affichent.</span><span class="sxs-lookup"><span data-stu-id="56a6f-197">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="56a6f-198">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="56a6f-198">-GroupBy</span></span>

<span data-ttu-id="56a6f-199">Spécifie la sortie triée dans des tables distinctes en fonction d’une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="56a6f-199">Specifies sorted output in separate tables based on a property value.</span></span> <span data-ttu-id="56a6f-200">Par exemple, vous pouvez utiliser **GroupBy** pour répertorier les services dans des tables distinctes en fonction de leur état.</span><span class="sxs-lookup"><span data-stu-id="56a6f-200">For example, you can use **GroupBy** to list services in separate tables based on their status.</span></span>

<span data-ttu-id="56a6f-201">Entrez une expression ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="56a6f-201">Enter an expression or a property.</span></span> <span data-ttu-id="56a6f-202">Le paramètre **GroupBy** s’attend à ce que les objets soient triés.</span><span class="sxs-lookup"><span data-stu-id="56a6f-202">The **GroupBy** parameter expects that the objects are sorted.</span></span>
<span data-ttu-id="56a6f-203">Utilisez l' `Sort-Object` applet de commande avant `Format-Table` d’utiliser pour regrouper les objets.</span><span class="sxs-lookup"><span data-stu-id="56a6f-203">Use the `Sort-Object` cmdlet before using `Format-Table` to group the objects.</span></span>

<span data-ttu-id="56a6f-204">La valeur du paramètre **GroupBy** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="56a6f-204">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="56a6f-205">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="56a6f-205">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="56a6f-206">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="56a6f-206">Valid key-value pairs are:</span></span>

- <span data-ttu-id="56a6f-207">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="56a6f-207">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="56a6f-208">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="56a6f-208">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="56a6f-209">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="56a6f-209">FormatString - `<string>`</span></span>

<span data-ttu-id="56a6f-210">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="56a6f-210">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="56a6f-211">-HideTableHeaders</span><span class="sxs-lookup"><span data-stu-id="56a6f-211">-HideTableHeaders</span></span>

<span data-ttu-id="56a6f-212">Omet les en-têtes de colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="56a6f-212">Omits the column headings from the table.</span></span>

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

### <span data-ttu-id="56a6f-213">-InputObject</span><span class="sxs-lookup"><span data-stu-id="56a6f-213">-InputObject</span></span>

<span data-ttu-id="56a6f-214">Spécifie les objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="56a6f-214">Specifies the objects to format.</span></span> <span data-ttu-id="56a6f-215">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="56a6f-215">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="56a6f-216">-Propriété</span><span class="sxs-lookup"><span data-stu-id="56a6f-216">-Property</span></span>

<span data-ttu-id="56a6f-217">Spécifie les propriétés d'objet qui apparaissent dans l''affichage et l'ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="56a6f-217">Specifies the object properties that appear in the display and the order in which they appear.</span></span> <span data-ttu-id="56a6f-218">Tapez un ou plusieurs noms de propriété, en les séparant par des virgules, ou utilisez une table de hachage pour afficher une propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="56a6f-218">Type one or more property names, separated by commas, or use a hash table to display a calculated property.</span></span> <span data-ttu-id="56a6f-219">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="56a6f-219">Wildcards are permitted.</span></span>

<span data-ttu-id="56a6f-220">Si vous omettez ce paramètre, les propriétés qui s’affichent dans l’affichage dépendent des propriétés du premier objet.</span><span class="sxs-lookup"><span data-stu-id="56a6f-220">If you omit this parameter, the properties that appear in the display depend on the first object's properties.</span></span> <span data-ttu-id="56a6f-221">Par exemple, si le premier objet a **PropertyA** et **PropertyB** , mais que les objets suivants possèdent **PropertyA** , **PropertyB** et **PropertyC** , seuls les en-têtes **PropertyA** et **PropertyB** s’afficheront.</span><span class="sxs-lookup"><span data-stu-id="56a6f-221">For example, if the first object has **PropertyA** and **PropertyB** but subsequent objects have **PropertyA** , **PropertyB** , and **PropertyC** , then only the **PropertyA** and **PropertyB** headers will display.</span></span>

<span data-ttu-id="56a6f-222">Le paramètre **Property** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="56a6f-222">The **Property** parameter is optional.</span></span> <span data-ttu-id="56a6f-223">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="56a6f-223">You can't use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="56a6f-224">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="56a6f-224">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="56a6f-225">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="56a6f-225">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="56a6f-226">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="56a6f-226">Valid key-value pairs are:</span></span>

- <span data-ttu-id="56a6f-227">Nom (ou étiquette) `<string>`</span><span class="sxs-lookup"><span data-stu-id="56a6f-227">Name (or Label) `<string>`</span></span>
- <span data-ttu-id="56a6f-228">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="56a6f-228">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="56a6f-229">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="56a6f-229">FormatString - `<string>`</span></span>
- <span data-ttu-id="56a6f-230">Largeur- `<int32>` -doit être supérieur à `0`</span><span class="sxs-lookup"><span data-stu-id="56a6f-230">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="56a6f-231">Alignment : la valeur peut être `Left` , `Center` ou `Right`</span><span class="sxs-lookup"><span data-stu-id="56a6f-231">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="56a6f-232">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="56a6f-232">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="56a6f-233">-RepeatHeader</span><span class="sxs-lookup"><span data-stu-id="56a6f-233">-RepeatHeader</span></span>

<span data-ttu-id="56a6f-234">Répète l’affichage de l’en-tête d’un tableau après chaque écran complet.</span><span class="sxs-lookup"><span data-stu-id="56a6f-234">Repeats displaying the header of a table after every screen full.</span></span> <span data-ttu-id="56a6f-235">L’en-tête répété est utile lorsque la sortie est dirigée vers un récepteur de radiomessagerie tel que `less` ou, `more` ou en utilisant un lecteur d’écran.</span><span class="sxs-lookup"><span data-stu-id="56a6f-235">The repeated header is useful when the output is piped to a pager such as `less` or `more` or paging with a screen reader.</span></span>

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

### <span data-ttu-id="56a6f-236">-ShowError</span><span class="sxs-lookup"><span data-stu-id="56a6f-236">-ShowError</span></span>

<span data-ttu-id="56a6f-237">Ce paramètre envoie des erreurs via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="56a6f-237">This parameter sends errors through the pipeline.</span></span> <span data-ttu-id="56a6f-238">Ce paramètre peut être utilisé comme une aide au débogage lorsque vous mettez en forme des expressions dans une `Format-Table` commande et que vous devez dépanner les expressions.</span><span class="sxs-lookup"><span data-stu-id="56a6f-238">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

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

### <span data-ttu-id="56a6f-239">-Afficher</span><span class="sxs-lookup"><span data-stu-id="56a6f-239">-View</span></span>

<span data-ttu-id="56a6f-240">À compter de PowerShell 6, les vues par défaut sont définies dans le `C#` code source PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56a6f-240">Beginning in PowerShell 6, the default views are defined in PowerShell `C#` source code.</span></span> <span data-ttu-id="56a6f-241">Les `*.format.ps1xml` fichiers de powershell 5,1 et versions antérieures n’existent pas dans PowerShell 6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="56a6f-241">The `*.format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="56a6f-242">Le paramètre **View** vous permet de spécifier un autre format ou une autre vue personnalisée pour la table.</span><span class="sxs-lookup"><span data-stu-id="56a6f-242">The **View** parameter lets you specify an alternate format or custom view for the table.</span></span> <span data-ttu-id="56a6f-243">Vous pouvez utiliser les vues PowerShell par défaut ou créer des vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="56a6f-243">You can use the default PowerShell views or create custom views.</span></span> <span data-ttu-id="56a6f-244">Pour plus d’informations sur la création d’un affichage personnalisé, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="56a6f-244">For more information about how to create a custom view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="56a6f-245">Les vues alternatives et personnalisées pour le paramètre **View** doivent utiliser le format de table ; sinon, `Format-Table` échoue.</span><span class="sxs-lookup"><span data-stu-id="56a6f-245">The alternate and custom views for the **View** parameter must use the table format, otherwise, `Format-Table` fails.</span></span> <span data-ttu-id="56a6f-246">Si l’autre vue est une liste, utilisez l' `Format-List` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="56a6f-246">If the alternate view is a list, use the `Format-List` cmdlet.</span></span> <span data-ttu-id="56a6f-247">Si l’autre vue n’est ni une liste ni une table, utilisez l’applet de commande `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="56a6f-247">If the alternate view isn't a list or a table, use the `Format-Custom` cmdlet.</span></span>

<span data-ttu-id="56a6f-248">Vous ne pouvez pas utiliser les paramètres **Property** et **View** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="56a6f-248">You can't use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="56a6f-249">-Wrap</span><span class="sxs-lookup"><span data-stu-id="56a6f-249">-Wrap</span></span>

<span data-ttu-id="56a6f-250">Affiche le texte qui dépasse de la largeur de colonne sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="56a6f-250">Displays text that exceeds the column width on the next line.</span></span> <span data-ttu-id="56a6f-251">Par défaut, le texte qui dépasse de la largeur de colonne est tronqué.</span><span class="sxs-lookup"><span data-stu-id="56a6f-251">By default, text that exceeds the column width is truncated.</span></span>

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

### <span data-ttu-id="56a6f-252">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56a6f-252">CommonParameters</span></span>

<span data-ttu-id="56a6f-253">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="56a6f-253">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56a6f-254">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="56a6f-254">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56a6f-255">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="56a6f-255">INPUTS</span></span>

### <span data-ttu-id="56a6f-256">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="56a6f-256">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="56a6f-257">Vous pouvez envoyer n’importe quel objet dans le pipeline à `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="56a6f-257">You can send any object down the pipeline to `Format-Table`.</span></span>

## <span data-ttu-id="56a6f-258">SORTIES</span><span class="sxs-lookup"><span data-stu-id="56a6f-258">OUTPUTS</span></span>

### <span data-ttu-id="56a6f-259">Microsoft. PowerShell. Commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="56a6f-259">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="56a6f-260">`Format-Table` retourne les objets de format représentant la table.</span><span class="sxs-lookup"><span data-stu-id="56a6f-260">`Format-Table` returns format objects that represent the table.</span></span>

## <span data-ttu-id="56a6f-261">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="56a6f-261">NOTES</span></span>

## <span data-ttu-id="56a6f-262">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="56a6f-262">RELATED LINKS</span></span>

[<span data-ttu-id="56a6f-263">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="56a6f-263">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="56a6f-264">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="56a6f-264">about_Format.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="56a6f-265">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="56a6f-265">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="56a6f-266">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="56a6f-266">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="56a6f-267">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="56a6f-267">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="56a6f-268">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="56a6f-268">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="56a6f-269">Format-List</span><span class="sxs-lookup"><span data-stu-id="56a6f-269">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="56a6f-270">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="56a6f-270">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="56a6f-271">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="56a6f-271">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="56a6f-272">Get-Member</span><span class="sxs-lookup"><span data-stu-id="56a6f-272">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="56a6f-273">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="56a6f-273">Get-CimInstance</span></span>](../CimCmdlets/Get-CimInstance.md)

[<span data-ttu-id="56a6f-274">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="56a6f-274">Update-FormatData</span></span>](Update-FormatData.md)
