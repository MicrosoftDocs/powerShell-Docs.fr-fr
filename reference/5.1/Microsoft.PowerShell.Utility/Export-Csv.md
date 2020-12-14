---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 17c3ef3046ba8f0cca9a85cf41aaf683212a58e9
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913339"
---
# <span data-ttu-id="78d2e-102">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="78d2e-102">Export-Csv</span></span>

## <span data-ttu-id="78d2e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="78d2e-103">SYNOPSIS</span></span>
<span data-ttu-id="78d2e-104">Convertit des objets en une série de chaînes de valeurs séparées par des virgules (CSV) et enregistre les chaînes dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-104">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="78d2e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="78d2e-105">SYNTAX</span></span>

### <span data-ttu-id="78d2e-106">Délimiteur (par défaut)</span><span class="sxs-lookup"><span data-stu-id="78d2e-106">Delimiter (Default)</span></span>

```
Export-Csv [[-Path] <string>] [[-Delimiter] <char>] -InputObject <psobject> [-LiteralPath <string>]
 [-Force] [-NoClobber] [-Encoding <string>] [-Append] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="78d2e-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="78d2e-107">UseCulture</span></span>

```
Export-Csv [[-Path] <string>] -InputObject <psobject> [-LiteralPath <string>] [-Force] [-NoClobber]
 [-Encoding <string>] [-Append] [-UseCulture] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="78d2e-108">Description</span><span class="sxs-lookup"><span data-stu-id="78d2e-108">DESCRIPTION</span></span>

<span data-ttu-id="78d2e-109">L' `Export-CSV` applet de commande crée un fichier csv contenant les objets que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="78d2e-109">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="78d2e-110">Chaque objet est une ligne qui contient une liste séparée par des virgules des valeurs de propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="78d2e-110">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="78d2e-111">Vous pouvez utiliser l' `Export-CSV` applet de commande pour créer des feuilles de calcul et partager des données avec des programmes qui acceptent les fichiers CSV comme entrée.</span><span class="sxs-lookup"><span data-stu-id="78d2e-111">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="78d2e-112">Ne mettez pas en forme les objets avant de les envoyer à l’applet de commande `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-112">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="78d2e-113">Si `Export-CSV` reçoit des objets mis en forme, le fichier CSV contient les propriétés de format au lieu des propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="78d2e-113">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="78d2e-114">Pour exporter uniquement les propriétés sélectionnées d’un objet, utilisez l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-114">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="78d2e-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="78d2e-115">EXAMPLES</span></span>

### <span data-ttu-id="78d2e-116">Exemple 1 : exporter des propriétés de processus vers un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="78d2e-116">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="78d2e-117">Cet exemple sélectionne les objets de **processus** avec des propriétés spécifiques, exporte les objets dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-117">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

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

<span data-ttu-id="78d2e-118">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-118">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="78d2e-119">Le paramètre **Name** filtre la sortie pour inclure uniquement les objets processus WmiPrvSE.</span><span class="sxs-lookup"><span data-stu-id="78d2e-119">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="78d2e-120">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-120">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="78d2e-121">`Select-Object` utilise le paramètre **Property** pour sélectionner un sous-ensemble de propriétés de l’objet Process.</span><span class="sxs-lookup"><span data-stu-id="78d2e-121">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="78d2e-122">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-122">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-123">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-123">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="78d2e-124">Le paramètre **path** spécifie que le fichier WmiData.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-124">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="78d2e-125">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="78d2e-125">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="78d2e-126">L' `Import-Csv` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-126">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="78d2e-127">Exemple 2 : exporter des processus vers un fichier délimité par des virgules</span><span class="sxs-lookup"><span data-stu-id="78d2e-127">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="78d2e-128">Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-128">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="78d2e-129">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-129">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="78d2e-130">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-130">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-131">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-131">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="78d2e-132">Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-132">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="78d2e-133">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="78d2e-133">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="78d2e-134">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-134">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="78d2e-135">Exemple 3 : exporter des processus vers un fichier délimité par des points-virgules</span><span class="sxs-lookup"><span data-stu-id="78d2e-135">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="78d2e-136">Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier avec un délimiteur de point-virgule.</span><span class="sxs-lookup"><span data-stu-id="78d2e-136">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="78d2e-137">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-137">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="78d2e-138">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-138">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-139">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-139">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="78d2e-140">Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-140">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="78d2e-141">Le paramètre **Delimiter** spécifie un point-virgule pour séparer les valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="78d2e-141">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="78d2e-142">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="78d2e-142">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="78d2e-143">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-143">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="78d2e-144">Exemple 4 : exporter des processus à l’aide du séparateur de liste de la culture actuelle</span><span class="sxs-lookup"><span data-stu-id="78d2e-144">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="78d2e-145">Cet exemple obtient les objets de **processus** et exporte les objets dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-145">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="78d2e-146">Le délimiteur est le séparateur de liste de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="78d2e-146">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="78d2e-147">L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** et affiche le séparateur de liste par défaut de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="78d2e-147">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="78d2e-148">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-148">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="78d2e-149">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-149">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-150">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-150">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="78d2e-151">Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-151">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="78d2e-152">Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="78d2e-152">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="78d2e-153">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="78d2e-153">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="78d2e-154">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-154">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="78d2e-155">Exemple 5 : exporter des processus avec des informations de type</span><span class="sxs-lookup"><span data-stu-id="78d2e-155">Example 5: Export processes with type information</span></span>

<span data-ttu-id="78d2e-156">Cet exemple explique comment inclure les informations d’en-tête **#TYPE** dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-156">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="78d2e-157">L’en-tête **#TYPE** est la valeur par défaut dans les versions antérieures à PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="78d2e-157">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="78d2e-158">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-158">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="78d2e-159">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-159">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-160">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-160">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="78d2e-161">Le paramètre **path** spécifie que le fichier Processes.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-161">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="78d2e-162">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-162">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="78d2e-163">Exemple 6 : exporter et ajouter des objets dans un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="78d2e-163">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="78d2e-164">Cet exemple décrit comment exporter des objets dans un fichier CSV et utiliser le paramètre **Append** pour ajouter des objets à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="78d2e-164">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

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

<span data-ttu-id="78d2e-165">L' `Get-Service` applet de commande obtient les objets de service.</span><span class="sxs-lookup"><span data-stu-id="78d2e-165">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="78d2e-166">Le paramètre **DisplayName** retourne les services qui contiennent l’application Word.</span><span class="sxs-lookup"><span data-stu-id="78d2e-166">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="78d2e-167">Les objets de service sont envoyés dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-167">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="78d2e-168">`Select-Object` utilise le paramètre **Property** pour spécifier les propriétés **DisplayName** et **Status** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-168">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="78d2e-169">La `$AppService` variable stocke les objets.</span><span class="sxs-lookup"><span data-stu-id="78d2e-169">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="78d2e-170">Les `$AppService` objets sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-170">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-171">`Export-Csv` convertit les objets de service en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-171">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="78d2e-172">Le paramètre **path** spécifie que le fichier Services.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-172">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="78d2e-173">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="78d2e-173">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="78d2e-174">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-174">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="78d2e-175">Les `Get-Service` applets de commande et `Select-Object` sont répétées pour les services qui contiennent le mot Windows.</span><span class="sxs-lookup"><span data-stu-id="78d2e-175">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="78d2e-176">La `$WinService` variable stocke les objets de service.</span><span class="sxs-lookup"><span data-stu-id="78d2e-176">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="78d2e-177">L' `Export-Csv` applet de commande utilise le paramètre **Append** pour spécifier que les `$WinService` objets sont ajoutés au fichier de Services.csv existant.</span><span class="sxs-lookup"><span data-stu-id="78d2e-177">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="78d2e-178">L' `Get-Content` applet de commande est répétée pour afficher le fichier mis à jour qui comprend les données ajoutées.</span><span class="sxs-lookup"><span data-stu-id="78d2e-178">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="78d2e-179">Exemple 7 : l’applet de commande format au sein d’un pipeline crée des résultats inattendus</span><span class="sxs-lookup"><span data-stu-id="78d2e-179">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="78d2e-180">Cet exemple montre pourquoi il est important de ne pas utiliser une applet de commande format dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="78d2e-180">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="78d2e-181">Lors de la réception d’une sortie inattendue, corrigez la syntaxe du pipeline.</span><span class="sxs-lookup"><span data-stu-id="78d2e-181">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

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

<span data-ttu-id="78d2e-182">L' `Get-Date` applet de commande obtient l’objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-182">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="78d2e-183">L’objet est envoyé dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-183">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="78d2e-184">`Select-Object` utilise le paramètre **Property** pour sélectionner un sous-ensemble de propriétés d’objet.</span><span class="sxs-lookup"><span data-stu-id="78d2e-184">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="78d2e-185">L’objet est envoyé dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-185">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-186">`Export-Csv` Convertit l’objet au format CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-186">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="78d2e-187">Le paramètre **path** spécifie que le fichier DateTime.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-187">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="78d2e-188">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="78d2e-188">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="78d2e-189">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier CSV situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-189">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="78d2e-190">Lorsque l' `Format-Table` applet de commande est utilisée dans le pipeline pour sélectionner des propriétés, des résultats inattendus sont reçus.</span><span class="sxs-lookup"><span data-stu-id="78d2e-190">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="78d2e-191">`Format-Table` envoie des objets de format de table vers l’applet de commande au lieu de l' `Export-Csv` objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-191">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="78d2e-192">`Export-Csv` convertit les objets de format de table en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-192">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="78d2e-193">L' `Get-Content` applet de commande affiche le fichier CSV qui contient les objets de format de table.</span><span class="sxs-lookup"><span data-stu-id="78d2e-193">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="78d2e-194">Exemple 8 : utilisation du paramètre force pour remplacer les fichiers en lecture seule</span><span class="sxs-lookup"><span data-stu-id="78d2e-194">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="78d2e-195">Cet exemple crée un fichier vide en lecture seule et utilise le paramètre **force** pour mettre à jour le fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-195">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

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

<span data-ttu-id="78d2e-196">L' `New-Item` applet de commande utilise les paramètres **path** et **ItemType** pour créer le fichier ReadOnly.csv dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-196">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="78d2e-197">L' `Set-ItemProperty` applet de commande utilise les paramètres **Name** et **value** pour affecter la valeur true à la propriété **IsReadOnly** du fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-197">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="78d2e-198">L' `Get-Process` applet de commande obtient les objets de **processus** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-198">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="78d2e-199">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-199">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-200">`Export-Csv` convertit les objets processus en une série de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-200">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="78d2e-201">Le paramètre **path** spécifie que le fichier ReadOnly.csv est enregistré dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-201">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="78d2e-202">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="78d2e-202">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="78d2e-203">La sortie indique que le fichier n’est pas écrit parce que l’accès est refusé.</span><span class="sxs-lookup"><span data-stu-id="78d2e-203">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="78d2e-204">Le paramètre **force** est ajouté à l' `Export-Csv` applet de commande pour forcer l’exportation à écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-204">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="78d2e-205">L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-205">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="78d2e-206">Exemple 9 : utilisation du paramètre force avec Append</span><span class="sxs-lookup"><span data-stu-id="78d2e-206">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="78d2e-207">Cet exemple montre comment utiliser les paramètres **force** et **Append** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-207">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="78d2e-208">Lorsque ces paramètres sont combinés, les propriétés d’objets non appariées peuvent être écrites dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-208">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

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

<span data-ttu-id="78d2e-209">Une expression crée le **PSCustomObject** avec les propriétés **Name** et **version** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-209">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="78d2e-210">Les valeurs sont stockées dans la `$Content` variable.</span><span class="sxs-lookup"><span data-stu-id="78d2e-210">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="78d2e-211">La `$Content` variable est envoyée dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-211">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-212">`Export-Csv` utilise le paramètre **path** et enregistre le fichier ParmFile.csv dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-212">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="78d2e-213">Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV et n’est pas requis dans PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="78d2e-213">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="78d2e-214">Une autre expression crée un **PSCustomObject** avec le **nom** et les propriétés de l' **édition** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-214">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="78d2e-215">Les valeurs sont stockées dans la `$AdditionalContent` variable.</span><span class="sxs-lookup"><span data-stu-id="78d2e-215">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="78d2e-216">La `$AdditionalContent` variable est envoyée dans le pipeline à l’applet de commande `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-216">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="78d2e-217">Le paramètre **Append** est utilisé pour ajouter les données au fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-217">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="78d2e-218">L’ajout échoue en raison d’une incompatibilité de nom de propriété entre la **version** et l' **édition**.</span><span class="sxs-lookup"><span data-stu-id="78d2e-218">The append fails because there is a property name mismatch between **Version** and **Edition**.</span></span>

<span data-ttu-id="78d2e-219">Le `Export-Csv` paramètre **force** de l’applet de commande est utilisé pour forcer l’exportation à écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-219">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="78d2e-220">La propriété **Edition** est ignorée.</span><span class="sxs-lookup"><span data-stu-id="78d2e-220">The **Edition** property is discarded.</span></span> <span data-ttu-id="78d2e-221">L' `Import-Csv` applet de commande utilise le paramètre **path** pour afficher le fichier situé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="78d2e-221">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

## <span data-ttu-id="78d2e-222">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="78d2e-222">PARAMETERS</span></span>

### <span data-ttu-id="78d2e-223">-Append</span><span class="sxs-lookup"><span data-stu-id="78d2e-223">-Append</span></span>

<span data-ttu-id="78d2e-224">Utilisez ce paramètre pour `Export-CSV` Ajouter la sortie CSV à la fin du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="78d2e-224">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="78d2e-225">Sans ce paramètre, `Export-CSV` remplace le contenu du fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="78d2e-225">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="78d2e-226">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="78d2e-226">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="78d2e-227">-Délimiteur</span><span class="sxs-lookup"><span data-stu-id="78d2e-227">-Delimiter</span></span>

<span data-ttu-id="78d2e-228">Spécifie un délimiteur pour séparer les valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="78d2e-228">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="78d2e-229">La valeur par défaut est une virgule ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="78d2e-229">The default is a comma (`,`).</span></span> <span data-ttu-id="78d2e-230">Entrez un caractère, tel qu’un signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="78d2e-230">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="78d2e-231">Pour spécifier un point-virgule ( `;` ), mettez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="78d2e-231">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="78d2e-232">-Encoding</span><span class="sxs-lookup"><span data-stu-id="78d2e-232">-Encoding</span></span>

<span data-ttu-id="78d2e-233">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="78d2e-233">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="78d2e-234">La valeur par défaut est `ASCII`.</span><span class="sxs-lookup"><span data-stu-id="78d2e-234">The default value is `ASCII`.</span></span>

<span data-ttu-id="78d2e-235">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="78d2e-235">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="78d2e-236">`ASCII` Utilise le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="78d2e-236">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="78d2e-237">`BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="78d2e-237">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="78d2e-238">`Default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).</span><span class="sxs-lookup"><span data-stu-id="78d2e-238">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="78d2e-239">`OEM` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="78d2e-239">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="78d2e-240">`Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="78d2e-240">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="78d2e-241">`UTF7` Utilise UTF-7.</span><span class="sxs-lookup"><span data-stu-id="78d2e-241">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="78d2e-242">`UTF8` Utilise UTF-8.</span><span class="sxs-lookup"><span data-stu-id="78d2e-242">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="78d2e-243">`UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="78d2e-243">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78d2e-244">-Force</span><span class="sxs-lookup"><span data-stu-id="78d2e-244">-Force</span></span>

<span data-ttu-id="78d2e-245">Ce paramètre permet `Export-Csv` de remplacer les fichiers avec l’attribut de **lecture seule** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-245">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="78d2e-246">Lorsque les paramètres **force** et **Append** sont combinés, les objets qui contiennent des propriétés incompatibles peuvent être écrits dans un fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-246">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="78d2e-247">Seules les propriétés correspondantes sont écrites dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-247">Only the properties that match are written to the file.</span></span> <span data-ttu-id="78d2e-248">Les propriétés non appariées sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="78d2e-248">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="78d2e-249">-InputObject</span><span class="sxs-lookup"><span data-stu-id="78d2e-249">-InputObject</span></span>

<span data-ttu-id="78d2e-250">Spécifie les objets à exporter en tant que chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-250">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="78d2e-251">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="78d2e-251">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="78d2e-252">Vous pouvez également diriger les objets vers `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-252">You can also pipe objects to `Export-CSV`.</span></span>

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

### <span data-ttu-id="78d2e-253">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="78d2e-253">-LiteralPath</span></span>

<span data-ttu-id="78d2e-254">Spécifie le chemin d'accès au fichier de sortie CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-254">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="78d2e-255">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="78d2e-255">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="78d2e-256">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="78d2e-256">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="78d2e-257">Si le chemin d’accès comprend des caractères d’échappement, utilisez des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="78d2e-257">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="78d2e-258">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="78d2e-258">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78d2e-259">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="78d2e-259">-NoClobber</span></span>

<span data-ttu-id="78d2e-260">Utilisez ce paramètre pour `Export-CSV` ne pas remplacer un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="78d2e-260">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="78d2e-261">Par défaut, si le fichier existe dans le chemin d’accès spécifié, `Export-CSV` remplace le fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="78d2e-261">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="78d2e-262">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="78d2e-262">-NoTypeInformation</span></span>

<span data-ttu-id="78d2e-263">Supprime l’en-tête d’informations **#TYPE** de la sortie.</span><span class="sxs-lookup"><span data-stu-id="78d2e-263">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="78d2e-264">Ce paramètre est devenu la valeur par défaut dans PowerShell 6,0 et est inclus à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="78d2e-264">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="78d2e-265">-Path</span><span class="sxs-lookup"><span data-stu-id="78d2e-265">-Path</span></span>

<span data-ttu-id="78d2e-266">Paramètre obligatoire qui spécifie l’emplacement d’enregistrement du fichier de sortie CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-266">A required parameter that specifies the location to save the CSV output file.</span></span>

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

### <span data-ttu-id="78d2e-267">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="78d2e-267">-UseCulture</span></span>

<span data-ttu-id="78d2e-268">Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément.</span><span class="sxs-lookup"><span data-stu-id="78d2e-268">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="78d2e-269">Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-269">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="78d2e-270">-Confirm</span><span class="sxs-lookup"><span data-stu-id="78d2e-270">-Confirm</span></span>

<span data-ttu-id="78d2e-271">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="78d2e-271">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="78d2e-272">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="78d2e-272">-WhatIf</span></span>

<span data-ttu-id="78d2e-273">Empêche le traitement de l’applet de commande ou l’apport de modifications.</span><span class="sxs-lookup"><span data-stu-id="78d2e-273">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="78d2e-274">La sortie indique ce qui se produirait si l’applet de commande était exécutée.</span><span class="sxs-lookup"><span data-stu-id="78d2e-274">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="78d2e-275">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="78d2e-275">CommonParameters</span></span>

<span data-ttu-id="78d2e-276">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="78d2e-276">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="78d2e-277">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="78d2e-277">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="78d2e-278">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="78d2e-278">INPUTS</span></span>

### <span data-ttu-id="78d2e-279">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="78d2e-279">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="78d2e-280">Vous pouvez diriger n’importe quel objet avec un adaptateur de système de type étendu (ETS) vers `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="78d2e-280">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="78d2e-281">SORTIES</span><span class="sxs-lookup"><span data-stu-id="78d2e-281">OUTPUTS</span></span>

### <span data-ttu-id="78d2e-282">System.String</span><span class="sxs-lookup"><span data-stu-id="78d2e-282">System.String</span></span>

<span data-ttu-id="78d2e-283">La liste CSV est envoyée au fichier désigné dans le paramètre Path.</span><span class="sxs-lookup"><span data-stu-id="78d2e-283">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="78d2e-284">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="78d2e-284">NOTES</span></span>

<span data-ttu-id="78d2e-285">L' `Export-CSV` applet de commande convertit les objets que vous envoyez en une série de chaînes CSV et les enregistre dans le fichier texte spécifié.</span><span class="sxs-lookup"><span data-stu-id="78d2e-285">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="78d2e-286">Vous pouvez utiliser `Export-CSV` pour enregistrer des objets dans un fichier CSV, puis utiliser l' `Import-Csv` applet de commande pour créer des objets à partir du fichier CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-286">You can use `Export-CSV` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the CSV file.</span></span>

<span data-ttu-id="78d2e-287">Dans le fichier CSV, chaque objet est représenté par une liste séparée par des virgules des valeurs de propriété de l'objet.</span><span class="sxs-lookup"><span data-stu-id="78d2e-287">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="78d2e-288">Les valeurs de propriété sont converties en chaînes à l’aide de la méthode **ToString ()** .</span><span class="sxs-lookup"><span data-stu-id="78d2e-288">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="78d2e-289">Les chaînes sont représentées par le nom de la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="78d2e-289">The strings are represented by the property value name.</span></span> <span data-ttu-id="78d2e-290">'Export-CSV n’exporte pas les méthodes de l’objet.</span><span class="sxs-lookup"><span data-stu-id="78d2e-290">\`Export-CSV does not export the methods of the object.</span></span>

<span data-ttu-id="78d2e-291">Les chaînes CSV sont générées comme suit :</span><span class="sxs-lookup"><span data-stu-id="78d2e-291">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="78d2e-292">Par défaut, la première chaîne contient l’en-tête d’informations **#TYPE** , suivi du nom qualifié complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="78d2e-292">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="78d2e-293">Par exemple, **#TYPE System. Diagnostics. Process**.</span><span class="sxs-lookup"><span data-stu-id="78d2e-293">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="78d2e-294">Si **NoTypeInformation** est utilisé, la première chaîne comprend les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="78d2e-294">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="78d2e-295">Les en-têtes contiennent les noms de propriété du premier objet sous la forme d’une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="78d2e-295">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="78d2e-296">Les chaînes restantes contiennent des listes séparées par des virgules des valeurs de propriété de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="78d2e-296">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="78d2e-297">Lorsque vous envoyez plusieurs objets à `Export-CSV` , `Export-CSV` organise le fichier en fonction des propriétés du premier objet que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="78d2e-297">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="78d2e-298">Si les objets restants n'ont pas l'une des propriétés spécifiées, la valeur de propriété de cet objet est null (représentation sous forme de deux virgules consécutives).</span><span class="sxs-lookup"><span data-stu-id="78d2e-298">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="78d2e-299">Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété ne sont pas incluses dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-299">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="78d2e-300">Vous pouvez utiliser la `Import-Csv` cmdlet pour recréer des objets à partir des chaînes CSV dans les fichiers.</span><span class="sxs-lookup"><span data-stu-id="78d2e-300">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="78d2e-301">Les objets résultants sont les versions CSV des objets d'origine qui se composent des représentations de chaînes des valeurs de propriété et d'aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="78d2e-301">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="78d2e-302">Les `ConvertTo-Csv` applets de commande et `ConvertFrom-Csv` convertissent des objets en chaînes CSV et à partir de chaînes CSV.</span><span class="sxs-lookup"><span data-stu-id="78d2e-302">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="78d2e-303">`Export-CSV` est identique à `ConvertTo-CSV` , à ceci près qu’il enregistre les chaînes CSV dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="78d2e-303">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="78d2e-304">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="78d2e-304">RELATED LINKS</span></span>

[<span data-ttu-id="78d2e-305">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="78d2e-305">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="78d2e-306">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="78d2e-306">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="78d2e-307">Format-Table</span><span class="sxs-lookup"><span data-stu-id="78d2e-307">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="78d2e-308">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="78d2e-308">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="78d2e-309">Select-Object</span><span class="sxs-lookup"><span data-stu-id="78d2e-309">Select-Object</span></span>](Select-Object.md)
