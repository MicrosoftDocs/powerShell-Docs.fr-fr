---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 551646fba0523a03954295eb42380e7245ec319b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204662"
---
# <span data-ttu-id="f2f2b-103">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="f2f2b-103">Export-Csv</span></span>

## <span data-ttu-id="f2f2b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f2f2b-104">SYNOPSIS</span></span>
<span data-ttu-id="f2f2b-105">Convertit des objets en une série de chaînes de valeurs séparées par des virgules (CSV) et enregistre les chaînes dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-105">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="f2f2b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2f2b-106">SYNTAX</span></span>

### <span data-ttu-id="f2f2b-107">Délimiteur (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f2f2b-107">Delimiter (Default)</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f2f2b-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="f2f2b-108">UseCulture</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f2f2b-109">Description</span><span class="sxs-lookup"><span data-stu-id="f2f2b-109">DESCRIPTION</span></span>

<span data-ttu-id="f2f2b-110">L' `Export-CSV` applet de commande crée un fichier csv contenant les objets que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-110">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="f2f2b-111">Chaque objet est une ligne qui contient une liste séparée par des virgules des valeurs de propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-111">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="f2f2b-112">Vous pouvez utiliser l' `Export-CSV` applet de commande pour créer des feuilles de calcul et partager des données avec des programmes qui acceptent les fichiers CSV comme entrée.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-112">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="f2f2b-113">Ne mettez pas en forme les objets avant de les envoyer à l’applet de commande `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-113">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="f2f2b-114">Si `Export-CSV` reçoit des objets mis en forme, le fichier CSV contient les propriétés de format au lieu des propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-114">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="f2f2b-115">Pour exporter uniquement les propriétés sélectionnées d’un objet, utilisez l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-115">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="f2f2b-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f2f2b-116">EXAMPLES</span></span>

### <span data-ttu-id="f2f2b-117">Exemple 1 : exporter des propriétés de processus vers un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="f2f2b-117">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="f2f2b-118">Cet exemple sélectionne les objets de **processus** avec des propriétés spécifiques, exporte les objets dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-118">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

<span data-ttu-id="f2f2b-119">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-119">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="f2f2b-120">Le paramètre **Name** filtre la sortie pour inclure uniquement les objets processus WmiPrvSE.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-120">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="f2f2b-121">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-121">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="f2f2b-122">`Select-Object` utilise le paramètre **Property** pour sélectionner un sous-ensemble de propriétés de l’objet Process.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-122">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="f2f2b-123">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-123">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-124">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-124">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="f2f2b-125">Le paramètre **path** spécifie que le fichier WmiData.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-125">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2f2b-126">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-126">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2f2b-127">L' `Import-Csv` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-127">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2f2b-128">Exemple 2 : exporter des processus vers un fichier délimité par des virgules</span><span class="sxs-lookup"><span data-stu-id="f2f2b-128">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="f2f2b-129">Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-129">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="f2f2b-130">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-130">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="f2f2b-131">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-131">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-132">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-132">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="f2f2b-133">Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-133">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2f2b-134">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-134">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2f2b-135">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-135">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2f2b-136">Exemple 3 : exporter des processus vers un fichier délimité par des points-virgules</span><span class="sxs-lookup"><span data-stu-id="f2f2b-136">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="f2f2b-137">Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier avec un délimiteur de point-virgule.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-137">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="f2f2b-138">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-138">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="f2f2b-139">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-139">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-140">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-140">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="f2f2b-141">Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-141">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2f2b-142">Le paramètre **Delimiter** spécifie un point-virgule pour séparer les valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-142">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="f2f2b-143">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-143">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2f2b-144">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-144">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2f2b-145">Exemple 4 : exporter des processus à l’aide du séparateur de liste de la culture actuelle</span><span class="sxs-lookup"><span data-stu-id="f2f2b-145">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="f2f2b-146">Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-146">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="f2f2b-147">Le délimiteur est le séparateur de liste de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-147">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="f2f2b-148">L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** et affiche le séparateur de liste par défaut de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-148">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="f2f2b-149">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-149">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="f2f2b-150">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-150">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-151">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-151">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="f2f2b-152">Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-152">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2f2b-153">Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-153">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="f2f2b-154">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-154">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2f2b-155">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-155">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2f2b-156">Exemple 5 : exporter des processus avec des informations de type</span><span class="sxs-lookup"><span data-stu-id="f2f2b-156">Example 5: Export processes with type information</span></span>

<span data-ttu-id="f2f2b-157">Cet exemple explique comment inclure les informations d’en-tête **#TYPE** dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-157">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="f2f2b-158">L’en-tête **#TYPE** est la valeur par défaut dans les versions antérieures à PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-158">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="f2f2b-159">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-159">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="f2f2b-160">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-160">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-161">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-161">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="f2f2b-162">Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-162">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2f2b-163">**IncludeTypeInformation** comprend l’en-tête d’informations **#TYPE** dans la sortie CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-163">The **IncludeTypeInformation** includes the **#TYPE** information header in the CSV output.</span></span> <span data-ttu-id="f2f2b-164">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-164">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2f2b-165">Exemple 6 : exporter et ajouter des objets dans un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="f2f2b-165">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="f2f2b-166">Cet exemple décrit comment exporter des objets dans un fichier CSV et utiliser le paramètre **Append** pour ajouter des objets à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-166">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

<span data-ttu-id="f2f2b-167">L' `Get-Service` applet de commande obtient les objets de service.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-167">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="f2f2b-168">Le paramètre **DisplayName** retourne les services qui contiennent l’application Word.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-168">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="f2f2b-169">Les objets de service sont envoyés dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-169">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="f2f2b-170">`Select-Object` utilise le paramètre **Property** pour spécifier les propriétés **DisplayName** et **Status** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-170">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="f2f2b-171">La `$AppService` variable stocke les objets.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-171">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="f2f2b-172">Les `$AppService` objets sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-172">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-173">`Export-Csv` convertit les objets de service en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-173">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="f2f2b-174">Le paramètre **path** spécifie que le fichier Services.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-174">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2f2b-175">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-175">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2f2b-176">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-176">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="f2f2b-177">Les `Get-Service` applets de commande et `Select-Object` sont répétées pour les services qui contiennent le mot Windows.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-177">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="f2f2b-178">La `$WinService` variable stocke les objets de service.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-178">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="f2f2b-179">L' `Export-Csv` applet de commande utilise le paramètre **Append** pour spécifier que les `$WinService` objets sont ajoutés au fichier de Services.csv existant.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-179">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="f2f2b-180">L' `Get-Content` applet de commande est répétée pour afficher le fichier mis à jour qui comprend les données ajoutées.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-180">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="f2f2b-181">Exemple 7 : l’applet de commande format au sein d’un pipeline crée des résultats inattendus</span><span class="sxs-lookup"><span data-stu-id="f2f2b-181">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="f2f2b-182">Cet exemple montre pourquoi il est important de ne pas utiliser une applet de commande format dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-182">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="f2f2b-183">Lors de la réception d’une sortie inattendue, corrigez la syntaxe du pipeline.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-183">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

<span data-ttu-id="f2f2b-184">L' `Get-Date` applet de commande obtient l’objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-184">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="f2f2b-185">L’objet est envoyé dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-185">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="f2f2b-186">`Select-Object` utilise le paramètre **Property** pour sélectionner un sous-ensemble de propriétés d’objet.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-186">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="f2f2b-187">L’objet est envoyé dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-187">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-188">`Export-Csv` Convertit l’objet au format CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-188">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="f2f2b-189">Le paramètre **path** spécifie que le fichier DateTime.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-189">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2f2b-190">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-190">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2f2b-191">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier CSV situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-191">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="f2f2b-192">Lorsque l' `Format-Table` applet de commande est utilisée dans le pipeline pour sélectionner des propriétés, des résultats inattendus sont reçus.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-192">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="f2f2b-193">`Format-Table` envoie des objets de format de table vers l’applet de commande au lieu de l' `Export-Csv` objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-193">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="f2f2b-194">`Export-Csv` convertit les objets de format de table en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-194">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="f2f2b-195">L' `Get-Content` applet de commande affiche le fichier CSV qui contient les objets de format de table.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-195">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="f2f2b-196">Exemple 8 : utilisation du paramètre force pour remplacer les fichiers en lecture seule</span><span class="sxs-lookup"><span data-stu-id="f2f2b-196">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="f2f2b-197">Cet exemple crée un fichier vide en lecture seule et utilise le paramètre **force** pour mettre à jour le fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-197">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="f2f2b-198">L' `New-Item` applet de commande utilise les paramètres **path** et **ItemType** pour créer le fichier ReadOnly.csv dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-198">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="f2f2b-199">L' `Set-ItemProperty` applet de commande utilise les paramètres **Name** et **value** pour affecter la valeur true à la propriété **IsReadOnly** du fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-199">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="f2f2b-200">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-200">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="f2f2b-201">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-201">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-202">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-202">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="f2f2b-203">Le paramètre **path** spécifie que le fichier ReadOnly.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-203">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="f2f2b-204">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-204">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="f2f2b-205">La sortie indique que le fichier n’est pas écrit parce que l’accès est refusé.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-205">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="f2f2b-206">Le paramètre **force** est ajouté à l' `Export-Csv` applet de commande pour forcer l’exportation à écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-206">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="f2f2b-207">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-207">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="f2f2b-208">Exemple 9 : utilisation du paramètre force avec Append</span><span class="sxs-lookup"><span data-stu-id="f2f2b-208">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="f2f2b-209">Cet exemple montre comment utiliser les paramètres **force** et **Append** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-209">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="f2f2b-210">Lorsque ces paramètres sont combinés, les propriétés d’objets non appariées peuvent être écrites dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-210">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

<span data-ttu-id="f2f2b-211">Une expression crée le **PSCustomObject** avec les propriétés **Name** et **version** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-211">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="f2f2b-212">Les valeurs sont stockées dans la `$Content` variable.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-212">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="f2f2b-213">La `$Content` variable est envoyée dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-213">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-214">`Export-Csv` utilise le paramètre **path** et enregistre le fichier ParmFile.csv dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-214">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="f2f2b-215">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-215">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="f2f2b-216">Une autre expression crée un **PSCustomObject** avec le **nom** et les propriétés de l' **édition** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-216">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="f2f2b-217">Les valeurs sont stockées dans la `$AdditionalContent` variable.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-217">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="f2f2b-218">La `$AdditionalContent` variable est envoyée dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-218">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="f2f2b-219">Le paramètre **Append** est utilisé pour ajouter les données au fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-219">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="f2f2b-220">L’ajout échoue en raison d’une incompatibilité de nom de propriété entre la **version** et l' **édition** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-220">The append fails because there is a property name mismatch between **Version** and **Edition** .</span></span>

<span data-ttu-id="f2f2b-221">Le `Export-Csv` paramètre **force** de l’applet de commande est utilisé pour forcer l’exportation à écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-221">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="f2f2b-222">La propriété **Edition** est ignorée.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-222">The **Edition** property is discarded.</span></span> <span data-ttu-id="f2f2b-223">L' `Import-Csv` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-223">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

## <span data-ttu-id="f2f2b-224">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2f2b-224">PARAMETERS</span></span>

### <span data-ttu-id="f2f2b-225">-Append</span><span class="sxs-lookup"><span data-stu-id="f2f2b-225">-Append</span></span>

<span data-ttu-id="f2f2b-226">Utilisez ce paramètre pour `Export-CSV` Ajouter la sortie CSV à la fin du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-226">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="f2f2b-227">Sans ce paramètre, `Export-CSV` remplace le contenu du fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-227">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="f2f2b-228">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f2f2b-229">-Délimiteur</span><span class="sxs-lookup"><span data-stu-id="f2f2b-229">-Delimiter</span></span>

<span data-ttu-id="f2f2b-230">Spécifie un délimiteur pour séparer les valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-230">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="f2f2b-231">La valeur par défaut est une virgule ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-231">The default is a comma (`,`).</span></span> <span data-ttu-id="f2f2b-232">Entrez un caractère, tel qu’un signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-232">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="f2f2b-233">Pour spécifier un point-virgule ( `;` ), mettez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-233">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-234">-Encoding</span><span class="sxs-lookup"><span data-stu-id="f2f2b-234">-Encoding</span></span>

<span data-ttu-id="f2f2b-235">Spécifie l'encodage pour le fichier CSV exporté.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-235">Specifies the encoding for the exported CSV file.</span></span> <span data-ttu-id="f2f2b-236">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-236">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="f2f2b-237">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2f2b-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f2f2b-238">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-238">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="f2f2b-239">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-239">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="f2f2b-240">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-240">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="f2f2b-241">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-241">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="f2f2b-242">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-242">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="f2f2b-243">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-243">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="f2f2b-244">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="f2f2b-244">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="f2f2b-245">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="f2f2b-245">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="f2f2b-246">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-246">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="f2f2b-247">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-247">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="f2f2b-248">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-248">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-249">-Force</span><span class="sxs-lookup"><span data-stu-id="f2f2b-249">-Force</span></span>

<span data-ttu-id="f2f2b-250">Ce paramètre permet `Export-Csv` de remplacer les fichiers avec l’attribut de **lecture seule** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-250">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="f2f2b-251">Lorsque les paramètres **force** et **Append** sont combinés, les objets qui contiennent des propriétés incompatibles peuvent être écrits dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-251">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="f2f2b-252">Seules les propriétés correspondantes sont écrites dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-252">Only the properties that match are written to the file.</span></span> <span data-ttu-id="f2f2b-253">Les propriétés non appariées sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-253">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="f2f2b-254">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="f2f2b-254">-IncludeTypeInformation</span></span>

<span data-ttu-id="f2f2b-255">Lorsque ce paramètre est utilisé, la première ligne de la sortie CSV contient **#TYPE** suivie du nom qualifié complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-255">When this parameter is used the first line of the CSV output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="f2f2b-256">Par exemple, **#TYPE System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-256">For example, **#TYPE System.Diagnostics.Process** .</span></span>

<span data-ttu-id="f2f2b-257">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-257">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-258">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f2f2b-258">-InputObject</span></span>

<span data-ttu-id="f2f2b-259">Spécifie les objets à exporter en tant que chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-259">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="f2f2b-260">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-260">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="f2f2b-261">Vous pouvez également diriger les objets vers `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-261">You can also pipe objects to `Export-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-262">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f2f2b-262">-LiteralPath</span></span>

<span data-ttu-id="f2f2b-263">Spécifie le chemin d'accès au fichier de sortie CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-263">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="f2f2b-264">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-264">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="f2f2b-265">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-265">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f2f2b-266">Si le chemin d’accès comprend des caractères d’échappement, utilisez des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-266">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="f2f2b-267">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-267">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-268">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="f2f2b-268">-NoClobber</span></span>

<span data-ttu-id="f2f2b-269">Utilisez ce paramètre pour `Export-CSV` ne pas remplacer un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-269">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="f2f2b-270">Par défaut, si le fichier existe dans le chemin d’accès spécifié, `Export-CSV` remplace le fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-270">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-271">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="f2f2b-271">-NoTypeInformation</span></span>

<span data-ttu-id="f2f2b-272">Supprime l’en-tête d’informations **#TYPE** de la sortie.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-272">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="f2f2b-273">Ce paramètre est devenu la valeur par défaut dans PowerShell 6,0 et est inclus à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-273">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-274">-Path</span><span class="sxs-lookup"><span data-stu-id="f2f2b-274">-Path</span></span>

<span data-ttu-id="f2f2b-275">Paramètre obligatoire qui spécifie l’emplacement d’enregistrement du fichier de sortie CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-275">A required parameter that specifies the location to save the CSV output file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-276">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="f2f2b-276">-UseCulture</span></span>

<span data-ttu-id="f2f2b-277">Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-277">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="f2f2b-278">Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-278">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2f2b-279">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f2f2b-279">-Confirm</span></span>

<span data-ttu-id="f2f2b-280">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-280">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f2f2b-281">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f2f2b-281">-WhatIf</span></span>

<span data-ttu-id="f2f2b-282">Empêche le traitement de l’applet de commande ou l’apport de modifications.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-282">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="f2f2b-283">La sortie indique ce qui se produirait si l’applet de commande était exécutée.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-283">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="f2f2b-284">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2f2b-284">CommonParameters</span></span>

<span data-ttu-id="f2f2b-285">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-285">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2f2b-286">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-286">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2f2b-287">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f2f2b-287">INPUTS</span></span>

### <span data-ttu-id="f2f2b-288">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f2f2b-288">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f2f2b-289">Vous pouvez diriger n’importe quel objet avec un adaptateur de système de type étendu (ETS) vers `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-289">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="f2f2b-290">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f2f2b-290">OUTPUTS</span></span>

### <span data-ttu-id="f2f2b-291">System.String</span><span class="sxs-lookup"><span data-stu-id="f2f2b-291">System.String</span></span>

<span data-ttu-id="f2f2b-292">La liste CSV est envoyée au fichier désigné dans le paramètre Path.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-292">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="f2f2b-293">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f2f2b-293">NOTES</span></span>

<span data-ttu-id="f2f2b-294">L' `Export-CSV` applet de commande convertit les objets que vous envoyez en une série de chaînes CSV et les enregistre dans le fichier texte spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-294">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="f2f2b-295">Vous pouvez utiliser `Export-CSV -IncludeTypeInformation` pour enregistrer des objets dans un fichier CSV, puis utiliser l' `Import-Csv` applet de commande pour créer des objets à partir du texte du fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-295">You can use `Export-CSV -IncludeTypeInformation` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the text in the CSV file.</span></span>

<span data-ttu-id="f2f2b-296">Dans le fichier CSV, chaque objet est représenté par une liste séparée par des virgules des valeurs de propriété de l'objet.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-296">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="f2f2b-297">Les valeurs de propriété sont converties en chaînes à l’aide de la méthode **ToString ()** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-297">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="f2f2b-298">Les chaînes sont représentées par le nom de la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-298">The strings are represented by the property value name.</span></span> <span data-ttu-id="f2f2b-299">`Export-CSV -IncludeTypeInformation` n’exporte pas les méthodes de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-299">`Export-CSV -IncludeTypeInformation` does not export the methods of the object.</span></span>

<span data-ttu-id="f2f2b-300">Les chaînes CSV sont générées comme suit :</span><span class="sxs-lookup"><span data-stu-id="f2f2b-300">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="f2f2b-301">Si **IncludeTypeInformation** est utilisé, la première chaîne contient l’en-tête d’informations **#TYPE** , suivi du nom qualifié complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-301">If **IncludeTypeInformation** is used, the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span>
  <span data-ttu-id="f2f2b-302">Par exemple, **#TYPE System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="f2f2b-302">For example, **#TYPE System.Diagnostics.Process** .</span></span>
- <span data-ttu-id="f2f2b-303">Si **IncludeTypeInformation** n’est pas utilisé, la première chaîne comprend les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-303">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="f2f2b-304">Les en-têtes contiennent les noms de propriété du premier objet sous la forme d’une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-304">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="f2f2b-305">Les chaînes restantes contiennent des listes séparées par des virgules des valeurs de propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-305">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="f2f2b-306">À compter de PowerShell 6,0, le comportement par défaut de `Export-CSV` est de ne pas inclure les informations de **#TYPE** dans le csv et **NoTypeInformation** est implicite.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-306">Beginning with PowerShell 6.0 the default behavior of `Export-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="f2f2b-307">**IncludeTypeInformation** peut être utilisé pour inclure les informations **#TYPE** et émuler le comportement par défaut de `Export-CSV` avant PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-307">**IncludeTypeInformation** can be used to include the **#TYPE** Information and emulate the default behavior of `Export-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="f2f2b-308">Lorsque vous envoyez plusieurs objets à `Export-CSV` , `Export-CSV` organise le fichier en fonction des propriétés du premier objet que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-308">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="f2f2b-309">Si les objets restants n'ont pas l'une des propriétés spécifiées, la valeur de propriété de cet objet est null (représentation sous forme de deux virgules consécutives).</span><span class="sxs-lookup"><span data-stu-id="f2f2b-309">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="f2f2b-310">Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété ne sont pas incluses dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-310">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="f2f2b-311">Vous pouvez utiliser la `Import-Csv` cmdlet pour recréer des objets à partir des chaînes CSV dans les fichiers.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-311">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="f2f2b-312">Les objets résultants sont les versions CSV des objets d'origine qui se composent des représentations de chaînes des valeurs de propriété et d'aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-312">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="f2f2b-313">Les `ConvertTo-Csv` applets de commande et `ConvertFrom-Csv` convertissent des objets en chaînes CSV et à partir de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-313">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="f2f2b-314">`Export-CSV` est identique à `ConvertTo-CSV` , à ceci près qu’il enregistre les chaînes CSV dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-314">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="f2f2b-315">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f2f2b-315">RELATED LINKS</span></span>

[<span data-ttu-id="f2f2b-316">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="f2f2b-316">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="f2f2b-317">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="f2f2b-317">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="f2f2b-318">Format-Table</span><span class="sxs-lookup"><span data-stu-id="f2f2b-318">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="f2f2b-319">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="f2f2b-319">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="f2f2b-320">Select-Object</span><span class="sxs-lookup"><span data-stu-id="f2f2b-320">Select-Object</span></span>](Select-Object.md)
