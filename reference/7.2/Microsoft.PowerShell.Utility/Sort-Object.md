---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: fead3b3d109a79186bc82f3c9f212f11f7b0bc57
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597544"
---
# <span data-ttu-id="59fe5-102">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="59fe5-102">Sort-Object</span></span>

## <span data-ttu-id="59fe5-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="59fe5-103">SYNOPSIS</span></span>
<span data-ttu-id="59fe5-104">Trie les objets selon les valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="59fe5-104">Sorts objects by property values.</span></span>

## <span data-ttu-id="59fe5-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="59fe5-105">SYNTAX</span></span>

### <span data-ttu-id="59fe5-106">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="59fe5-106">Default (Default)</span></span>

```
Sort-Object [-Stable] [-Descending] [-Unique] [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### <span data-ttu-id="59fe5-107">Haut</span><span class="sxs-lookup"><span data-stu-id="59fe5-107">Top</span></span>

```
Sort-Object [-Descending] [-Unique] -Top <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### <span data-ttu-id="59fe5-108">Bas</span><span class="sxs-lookup"><span data-stu-id="59fe5-108">Bottom</span></span>

```
Sort-Object [-Descending] [-Unique] -Bottom <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="59fe5-109">Description</span><span class="sxs-lookup"><span data-stu-id="59fe5-109">DESCRIPTION</span></span>

<span data-ttu-id="59fe5-110">L' `Sort-Object` applet de commande trie les objets dans l’ordre croissant ou décroissant en fonction des valeurs de propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="59fe5-110">The `Sort-Object` cmdlet sorts objects in ascending or descending order based on object property values.</span></span> <span data-ttu-id="59fe5-111">Si les propriétés de tri ne sont pas incluses dans une commande, PowerShell utilise les propriétés de tri par défaut du premier objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="59fe5-111">If sort properties are not included in a command, PowerShell uses default sort properties of the first input object.</span></span> <span data-ttu-id="59fe5-112">Si le type de l’objet d’entrée n’a pas de propriétés de tri par défaut, PowerShell tente de comparer les objets eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="59fe5-112">If the type of the input object has no default sort properties, PowerShell attempts to compare the objects themselves.</span></span> <span data-ttu-id="59fe5-113">Pour plus d’informations, consultez la section [Remarques](#notes) .</span><span class="sxs-lookup"><span data-stu-id="59fe5-113">For more information, see the [Notes](#notes) section.</span></span>

<span data-ttu-id="59fe5-114">Vous pouvez trier les objets par une ou plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="59fe5-114">You can sort objects by a single property or multiple properties.</span></span> <span data-ttu-id="59fe5-115">Plusieurs propriétés utilisent des tables de hachage pour trier par ordre croissant, ordre décroissant ou combinaison d’ordres de tri.</span><span class="sxs-lookup"><span data-stu-id="59fe5-115">Multiple properties use hash tables to sort in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="59fe5-116">Les propriétés sont triées en respectant la casse ou ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="59fe5-116">Properties are sorted as case-sensitive or case-insensitive.</span></span> <span data-ttu-id="59fe5-117">Utilisez le paramètre **unique** pour éliminer les doublons de la sortie.</span><span class="sxs-lookup"><span data-stu-id="59fe5-117">Use the **Unique** parameter to eliminate duplicates from the output.</span></span>

## <span data-ttu-id="59fe5-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="59fe5-118">EXAMPLES</span></span>

### <span data-ttu-id="59fe5-119">Exemple 1 : trier le répertoire actif par nom</span><span class="sxs-lookup"><span data-stu-id="59fe5-119">Example 1: Sort the current directory by name</span></span>

<span data-ttu-id="59fe5-120">Cet exemple trie les fichiers et les sous-répertoires d’un répertoire.</span><span class="sxs-lookup"><span data-stu-id="59fe5-120">This example sorts the files and subdirectories in a directory.</span></span>

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

<span data-ttu-id="59fe5-121">L' `Get-ChildItem` applet de commande obtient les fichiers et les sous-répertoires du répertoire spécifié par le paramètre de **chemin d’accès** , **C:\test**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-121">The `Get-ChildItem` cmdlet gets the files and subdirectories from the directory specified by the **Path** parameter, **C:\Test**.</span></span> <span data-ttu-id="59fe5-122">Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-122">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="59fe5-123">`Sort-Object` ne spécifie pas de propriété, de sorte que la sortie est triée par la propriété de tri par défaut, **Name**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-123">`Sort-Object` does not specify a property so the output is sorted by the default sort property, **Name**.</span></span>

### <span data-ttu-id="59fe5-124">Exemple 2 : trier le répertoire actif par longueur de fichier</span><span class="sxs-lookup"><span data-stu-id="59fe5-124">Example 2: Sort the current directory by file length</span></span>

<span data-ttu-id="59fe5-125">Cette commande affiche les fichiers dans le répertoire actif par longueur dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-125">This command displays the files in the current directory by length in ascending order.</span></span>

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

<span data-ttu-id="59fe5-126">L' `Get-ChildItem` applet de commande obtient les fichiers du répertoire spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="59fe5-126">The `Get-ChildItem` cmdlet gets the files from the directory specified by the **Path** parameter.</span></span>
<span data-ttu-id="59fe5-127">Le paramètre **file** spécifie que `Get-ChildItem` obtient uniquement les objets de fichier.</span><span class="sxs-lookup"><span data-stu-id="59fe5-127">The **File** parameter specifies that `Get-ChildItem` only gets file objects.</span></span> <span data-ttu-id="59fe5-128">Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-128">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="59fe5-129">`Sort-Object` utilise le paramètre **Length** pour trier les fichiers par longueur dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-129">`Sort-Object` uses the **Length** parameter to sort the files by length in ascending order.</span></span>

### <span data-ttu-id="59fe5-130">Exemple 3 : trier les processus par utilisation de la mémoire</span><span class="sxs-lookup"><span data-stu-id="59fe5-130">Example 3: Sort processes by memory usage</span></span>

<span data-ttu-id="59fe5-131">Cet exemple affiche les processus avec l’utilisation de mémoire la plus élevée en fonction de leur taille de jeu de travail (WS).</span><span class="sxs-lookup"><span data-stu-id="59fe5-131">This example displays processes with the highest memory usage based on their working set (WS) size.</span></span>

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

<span data-ttu-id="59fe5-132">L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="59fe5-132">The `Get-Process` cmdlet gets the list of processes running on the computer.</span></span> <span data-ttu-id="59fe5-133">Les objets processus sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-133">The process objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="59fe5-134">`Sort-Object` utilise le paramètre **Property** pour trier les objets par **WS**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-134">`Sort-Object` uses the **Property** parameter to sort the objects by **WS**.</span></span> <span data-ttu-id="59fe5-135">Les objets sont envoyés dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-135">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="59fe5-136">`Select-Object` utilise le **dernier** paramètre pour spécifier les cinq derniers objets, qui sont les objets avec l’utilisation de **WS** la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="59fe5-136">`Select-Object` uses the **Last** parameter to specify the last five objects, which are the objects with the highest **WS** usage.</span></span>

<span data-ttu-id="59fe5-137">Dans PowerShell 6, le `Sort-Object` paramètre en **bas** est une alternative à `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-137">In PowerShell 6, the `Sort-Object` parameter **Bottom** is an alternative to `Select-Object`.</span></span> <span data-ttu-id="59fe5-138">Par exemple, `Get-Process | Sort-Object -Property WS -Bottom 5`.</span><span class="sxs-lookup"><span data-stu-id="59fe5-138">For example, `Get-Process | Sort-Object -Property WS -Bottom 5`.</span></span>

### <span data-ttu-id="59fe5-139">Exemple 4 : trier les objets HistoryInfo par ID</span><span class="sxs-lookup"><span data-stu-id="59fe5-139">Example 4: Sort HistoryInfo objects by Id</span></span>

<span data-ttu-id="59fe5-140">Cette commande trie les objets **HistoryInfo** de la session PowerShell à l’aide de la propriété **ID** .</span><span class="sxs-lookup"><span data-stu-id="59fe5-140">This command sorts the PowerShell session's **HistoryInfo** objects using the **Id** property.</span></span> <span data-ttu-id="59fe5-141">Chaque session PowerShell a son propre historique de commande.</span><span class="sxs-lookup"><span data-stu-id="59fe5-141">Each PowerShell session has its own command history.</span></span>

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

<span data-ttu-id="59fe5-142">L' `Get-History` applet de commande obtient les objets d’historique de la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="59fe5-142">The `Get-History` cmdlet gets the history objects from the current PowerShell session.</span></span> <span data-ttu-id="59fe5-143">Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-143">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="59fe5-144">`Sort-Object` utilise le paramètre **Property** pour trier les objets par **ID**. Le paramètre **décroissant** trie l’historique des commandes du plus récent au plus ancien.</span><span class="sxs-lookup"><span data-stu-id="59fe5-144">`Sort-Object` uses the **Property** parameter to sort the objects by **Id**. The **Descending** parameter sorts the command history from newest to oldest.</span></span>

### <span data-ttu-id="59fe5-145">Exemple 5 : utiliser une table de hachage pour trier les propriétés dans l’ordre croissant et décroissant</span><span class="sxs-lookup"><span data-stu-id="59fe5-145">Example 5: Use a hash table to sort properties in ascending and descending order</span></span>

<span data-ttu-id="59fe5-146">Cet exemple utilise deux propriétés pour trier les objets, **Status** et **DisplayName**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-146">This example uses two properties to sort the objects, **Status** and **DisplayName**.</span></span> <span data-ttu-id="59fe5-147">L' **État** est trié par ordre décroissant et **DisplayName** est trié dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-147">**Status** is sorted in descending order and **DisplayName** is sorted in ascending order.</span></span>

<span data-ttu-id="59fe5-148">Une table de hachage est utilisée pour spécifier la valeur du paramètre de **propriété** .</span><span class="sxs-lookup"><span data-stu-id="59fe5-148">A hash table is used to specify the **Property** parameter's value.</span></span> <span data-ttu-id="59fe5-149">La table de hachage utilise une expression pour spécifier les noms de propriétés et les ordres de tri.</span><span class="sxs-lookup"><span data-stu-id="59fe5-149">The hash table uses an expression to specify the property names and sort orders.</span></span> <span data-ttu-id="59fe5-150">Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="59fe5-150">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="59fe5-151">La propriété **Status** utilisée dans la table de hachage est une propriété énumérée.</span><span class="sxs-lookup"><span data-stu-id="59fe5-151">The **Status** property used in the hash table is an enumerated property.</span></span>
<span data-ttu-id="59fe5-152">Pour plus d’informations, consultez [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="59fe5-152">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

<span data-ttu-id="59fe5-153">L' `Get-Service` applet de commande obtient la liste des services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="59fe5-153">The `Get-Service` cmdlet gets the list of services on the computer.</span></span> <span data-ttu-id="59fe5-154">Les objets de service sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-154">The service objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="59fe5-155">`Sort-Object` utilise le paramètre **Property** avec une table de hachage pour spécifier les noms de propriétés et les ordres de tri.</span><span class="sxs-lookup"><span data-stu-id="59fe5-155">`Sort-Object` uses the **Property** parameter with a hash table to specify the property names and sort orders.</span></span> <span data-ttu-id="59fe5-156">Le paramètre **Property** est trié par deux propriétés, **Status** dans l’ordre décroissant et **DisplayName** dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-156">The **Property** parameter is sorted by two properties, **Status** in descending order and **DisplayName** in ascending order.</span></span>

<span data-ttu-id="59fe5-157">**Status** est une propriété énumérée.</span><span class="sxs-lookup"><span data-stu-id="59fe5-157">**Status** is an enumerated property.</span></span> <span data-ttu-id="59fe5-158">**Stopped** a la valeur **1** et **Running** a la valeur **4**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-158">**Stopped** has a value of **1** and **Running** has a value of **4**.</span></span> <span data-ttu-id="59fe5-159">Le paramètre **décroissant** est défini sur `$True` afin que les processus **en cours d’exécution** soient affichés avant les processus **arrêtés** .</span><span class="sxs-lookup"><span data-stu-id="59fe5-159">The **Descending** parameter is set to `$True` so that **Running** processes are displayed before **Stopped** processes.</span></span> <span data-ttu-id="59fe5-160">**DisplayName** définit le paramètre **décroissant** sur `$False` pour trier les noms d’affichage par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="59fe5-160">**DisplayName** sets the **Descending** parameter to `$False` to sort the display names in alphabetical order.</span></span>

### <span data-ttu-id="59fe5-161">Exemple 6 : trier des fichiers texte par intervalle de temps</span><span class="sxs-lookup"><span data-stu-id="59fe5-161">Example 6: Sort text files by time span</span></span>

<span data-ttu-id="59fe5-162">Cette commande trie les fichiers texte par ordre décroissant selon l’intervalle de temps entre **CreationTime** et **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-162">This command sorts text files in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt
```

<span data-ttu-id="59fe5-163">L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire **C:\test** et tous les `*.txt` fichiers.</span><span class="sxs-lookup"><span data-stu-id="59fe5-163">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** and all of the `*.txt` files.</span></span> <span data-ttu-id="59fe5-164">Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-164">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="59fe5-165">`Sort-Object` utilise le paramètre **Property** avec une table de hachage pour déterminer l’intervalle de temps entre les fichiers **CreationTime** et **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-165">`Sort-Object` uses the **Property** parameter with a hash table to determine each files time span between **CreationTime** and **LastWriteTime**.</span></span> <span data-ttu-id="59fe5-166">Le paramètre **décroissant** est défini sur `$False` pour trier dans l’ordre de l’intervalle de temps le plus long au plus bref.</span><span class="sxs-lookup"><span data-stu-id="59fe5-166">The **Descending** parameter is set to `$False` to sort in the order of longest to shortest time span.</span></span>

### <span data-ttu-id="59fe5-167">Exemple 7 : trier les noms dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="59fe5-167">Example 7: Sort names in a text file</span></span>

<span data-ttu-id="59fe5-168">Cet exemple montre comment trier une liste à partir d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="59fe5-168">This example shows how to sort a list from a text file.</span></span> <span data-ttu-id="59fe5-169">Le fichier d’origine s’affiche sous la forme d’une liste non triée.</span><span class="sxs-lookup"><span data-stu-id="59fe5-169">The original file is displayed as an unsorted list.</span></span> <span data-ttu-id="59fe5-170">`Sort-Object` trie le contenu, puis trie le contenu avec le paramètre **unique** qui supprime les doublons.</span><span class="sxs-lookup"><span data-stu-id="59fe5-170">`Sort-Object` sorts the contents and then sorts the contents with the **Unique** parameter that removes duplicates.</span></span>

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

<span data-ttu-id="59fe5-171">L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le répertoire et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="59fe5-171">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="59fe5-172">Le **ServerNames.txt** de fichier contient une liste non triée de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="59fe5-172">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span>

<span data-ttu-id="59fe5-173">L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le répertoire et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="59fe5-173">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="59fe5-174">Le **ServerNames.txt** de fichier contient une liste non triée de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="59fe5-174">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="59fe5-175">Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-175">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="59fe5-176">`Sort-Object` trie la liste dans l’ordre par défaut, en ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-176">`Sort-Object` sorts the list in the default order, ascending.</span></span>

<span data-ttu-id="59fe5-177">L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le répertoire et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="59fe5-177">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="59fe5-178">Le **ServerNames.txt** de fichier contient une liste non triée de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="59fe5-178">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="59fe5-179">Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-179">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="59fe5-180">`Sort-Object` utilise le paramètre **unique** pour supprimer les noms d’ordinateur en double.</span><span class="sxs-lookup"><span data-stu-id="59fe5-180">`Sort-Object` uses the **Unique** parameter to remove duplicate computer names.</span></span> <span data-ttu-id="59fe5-181">La liste est triée dans l’ordre par défaut, en ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-181">The list is sorted in the default order, ascending.</span></span>

### <span data-ttu-id="59fe5-182">Exemple 8 : trier une chaîne comme un entier</span><span class="sxs-lookup"><span data-stu-id="59fe5-182">Example 8: Sort a string as an integer</span></span>

<span data-ttu-id="59fe5-183">Cet exemple montre comment trier un fichier texte qui contient des objets String en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="59fe5-183">This example shows how to sort a text file that contains string objects as integers.</span></span> <span data-ttu-id="59fe5-184">Vous pouvez envoyer chaque commande dans le pipeline à `Get-Member` et vérifier que les objets sont des chaînes et non des entiers.</span><span class="sxs-lookup"><span data-stu-id="59fe5-184">You can send each command down the pipeline to `Get-Member` and verify that the objects are strings instead of integers.</span></span> <span data-ttu-id="59fe5-185">Pour ces exemples, le `ProductId.txt` fichier contient une liste non triée de numéros de produits.</span><span class="sxs-lookup"><span data-stu-id="59fe5-185">For these examples, the `ProductId.txt` file contains an unsorted list of product numbers.</span></span>

<span data-ttu-id="59fe5-186">Dans le premier exemple, `Get-Content` obtient le contenu du fichier et canalise les lignes vers l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-186">In the first example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="59fe5-187">`Sort-Object` trie les objets String dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-187">`Sort-Object` sorts the string objects in ascending order.</span></span>

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

<span data-ttu-id="59fe5-188">Dans le deuxième exemple, `Get-Content` obtient le contenu du fichier et canalise les lignes vers l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-188">In the second example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="59fe5-189">`Sort-Object` utilise un bloc de script pour convertir les chaînes en entiers.</span><span class="sxs-lookup"><span data-stu-id="59fe5-189">`Sort-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="59fe5-190">Dans l’exemple de code, `[int]` convertit la chaîne en un entier et `$_` représente chaque chaîne au fur et à mesure qu’elle apparaît dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="59fe5-190">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="59fe5-191">Les objets entiers sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-191">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="59fe5-192">`Sort-Object` trie les objets entiers dans l’ordre numérique.</span><span class="sxs-lookup"><span data-stu-id="59fe5-192">`Sort-Object` sorts the integer objects in numeric order.</span></span>

### <span data-ttu-id="59fe5-193">Exemple 9 : utilisation de tris stables</span><span class="sxs-lookup"><span data-stu-id="59fe5-193">Example 9: Using stable sorts</span></span>

<span data-ttu-id="59fe5-194">Lorsque vous utilisez les paramètres **supérieur**, **inférieur** ou **stable** , les objets triés sont remis dans l’ordre dans lequel ils ont été reçus `Sort-Object` lorsque les critères de tri sont égaux.</span><span class="sxs-lookup"><span data-stu-id="59fe5-194">When you use the **Top**, **Bottom**, or **Stable** parameters, the sorted objects are delivered in the order they were received by `Sort-Object` when the sort criteria are equal.</span></span> <span data-ttu-id="59fe5-195">Dans cet exemple, nous triant les nombres 1 à 20 par leur valeur « modulo 3 ».</span><span class="sxs-lookup"><span data-stu-id="59fe5-195">In this example, we are sorting the numbers one through 20 by the their value 'modulo 3'.</span></span> <span data-ttu-id="59fe5-196">La valeur modulo est comprise entre zéro et deux.</span><span class="sxs-lookup"><span data-stu-id="59fe5-196">The modulo value ranges from zero to two.</span></span>

```powershell
PS> 1..20 |Sort-Object {$_ % 3}
18
3
15
6
12
9
1
16
13
10
7
4
19
11
8
14
5
17
2
20

PS> 1..20 |Sort-Object {$_ % 3} -Stable
3
6
9
12
15
18
1
4
7
10
13
16
19
2
5
8
11
14
17
20
```

<span data-ttu-id="59fe5-197">La sortie du premier tri est correctement regroupée selon la valeur du modulo, mais les éléments individuels ne sont pas triés dans la plage du modulo.</span><span class="sxs-lookup"><span data-stu-id="59fe5-197">The output from the first sort is correctly grouped by the modulus value but the individual items are not sorted within the modulus range.</span></span> <span data-ttu-id="59fe5-198">Le deuxième tri utilise l’option **stable** pour retourner un tri stable.</span><span class="sxs-lookup"><span data-stu-id="59fe5-198">The second sort uses the **Stable** option to return a stable sort.</span></span>

## <span data-ttu-id="59fe5-199">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="59fe5-199">PARAMETERS</span></span>

### <span data-ttu-id="59fe5-200">-Bas</span><span class="sxs-lookup"><span data-stu-id="59fe5-200">-Bottom</span></span>

<span data-ttu-id="59fe5-201">Spécifie le nombre d’objets à obtenir à partir de la fin d’un tableau d’objets trié.</span><span class="sxs-lookup"><span data-stu-id="59fe5-201">Specifies the number of objects to get from the end of a sorted object array.</span></span> <span data-ttu-id="59fe5-202">Cela entraîne un tri stable.</span><span class="sxs-lookup"><span data-stu-id="59fe5-202">This results in a stable sort.</span></span>

<span data-ttu-id="59fe5-203">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="59fe5-203">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Bottom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="59fe5-204">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="59fe5-204">-CaseSensitive</span></span>

<span data-ttu-id="59fe5-205">Indique que le tri respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="59fe5-205">Indicates that the sort is case-sensitive.</span></span> <span data-ttu-id="59fe5-206">Par défaut, les tris ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="59fe5-206">By default, sorts are not case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="59fe5-207">-Culture</span><span class="sxs-lookup"><span data-stu-id="59fe5-207">-Culture</span></span>

<span data-ttu-id="59fe5-208">Spécifie la configuration culturelle à utiliser pour les tris.</span><span class="sxs-lookup"><span data-stu-id="59fe5-208">Specifies the cultural configuration to use for sorts.</span></span> <span data-ttu-id="59fe5-209">Utilisez `Get-Culture` pour afficher la configuration de la culture du système.</span><span class="sxs-lookup"><span data-stu-id="59fe5-209">Use `Get-Culture` to display the system's culture configuration.</span></span>

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

### <span data-ttu-id="59fe5-210">-Décroissant</span><span class="sxs-lookup"><span data-stu-id="59fe5-210">-Descending</span></span>

<span data-ttu-id="59fe5-211">Indique que `Sort-Object` trie les objets dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-211">Indicates that `Sort-Object` sorts the objects in descending order.</span></span> <span data-ttu-id="59fe5-212">La valeur par défaut est l'ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-212">The default is ascending order.</span></span>

<span data-ttu-id="59fe5-213">Pour trier plusieurs propriétés avec différents ordres de tri, utilisez une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="59fe5-213">To sort multiple properties with different sort orders, use a hash table.</span></span> <span data-ttu-id="59fe5-214">Par exemple, avec une table de hachage, vous pouvez trier une propriété par ordre croissant et une autre propriété dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="59fe5-214">For example, with a hash table you can sort one property in ascending order and another property in descending order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="59fe5-215">-InputObject</span><span class="sxs-lookup"><span data-stu-id="59fe5-215">-InputObject</span></span>

<span data-ttu-id="59fe5-216">Pour trier les objets, envoyez-les dans le pipeline à `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-216">To sort objects, send them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="59fe5-217">Si vous utilisez le paramètre **InputObject** pour envoyer une collection d’éléments, `Sort-Object` reçoit un objet qui représente la collection.</span><span class="sxs-lookup"><span data-stu-id="59fe5-217">If you use the **InputObject** parameter to submit a collection of items, `Sort-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="59fe5-218">Étant donné qu’un objet ne peut pas être trié, `Sort-Object` retourne la collection entière inchangée.</span><span class="sxs-lookup"><span data-stu-id="59fe5-218">Because one object cannot be sorted, `Sort-Object` returns the entire collection unchanged.</span></span>

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

### <span data-ttu-id="59fe5-219">-Propriété</span><span class="sxs-lookup"><span data-stu-id="59fe5-219">-Property</span></span>

<span data-ttu-id="59fe5-220">Spécifie les noms de propriété que `Sort-Object` utilise pour trier les objets.</span><span class="sxs-lookup"><span data-stu-id="59fe5-220">Specifies the property names that `Sort-Object` uses to sort the objects.</span></span> <span data-ttu-id="59fe5-221">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="59fe5-221">Wildcards are permitted.</span></span>
<span data-ttu-id="59fe5-222">Les objets sont triés en fonction des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="59fe5-222">Objects are sorted based on the property values.</span></span> <span data-ttu-id="59fe5-223">Si vous ne spécifiez pas de propriété, effectue un `Sort-Object` Tri en fonction des propriétés par défaut du type d’objet ou des objets eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="59fe5-223">If you do not specify a property, `Sort-Object` sorts based on default properties for the object type or the objects themselves.</span></span>

<span data-ttu-id="59fe5-224">Plusieurs propriétés peuvent être triées par ordre croissant, ordre décroissant ou combinaison d’ordres de tri.</span><span class="sxs-lookup"><span data-stu-id="59fe5-224">Multiple properties can be sorted in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="59fe5-225">Lorsque vous spécifiez plusieurs propriétés, les objets sont triés par la première propriété.</span><span class="sxs-lookup"><span data-stu-id="59fe5-225">When you specify multiple properties, the objects are sorted by the first property.</span></span> <span data-ttu-id="59fe5-226">Si plusieurs objets ont la même valeur pour la première propriété, ces objets sont triés par la deuxième propriété.</span><span class="sxs-lookup"><span data-stu-id="59fe5-226">If multiple objects have the same value for the first property, those objects are sorted by the second property.</span></span> <span data-ttu-id="59fe5-227">Ce processus se poursuit jusqu'à ce qu'il ne reste plus aucune propriété spécifiée ou aucun groupe d'objets.</span><span class="sxs-lookup"><span data-stu-id="59fe5-227">This process continues until there are no more specified properties or no groups of objects.</span></span>

<span data-ttu-id="59fe5-228">La valeur du paramètre **Property** peut être une propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="59fe5-228">The **Property** parameter's value can be a calculated property.</span></span> <span data-ttu-id="59fe5-229">Pour créer une propriété calculée, utilisez une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="59fe5-229">To create a calculated property, use a hash table.</span></span>

<span data-ttu-id="59fe5-230">Les clés valides pour une table de hachage sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="59fe5-230">Valid keys for a hash table are as follows:</span></span>

- <span data-ttu-id="59fe5-231">`expression` - `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="59fe5-231">`expression` - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="59fe5-232">`ascending` ni `descending` - `<boolean>`</span><span class="sxs-lookup"><span data-stu-id="59fe5-232">`ascending` or `descending` - `<boolean>`</span></span>

<span data-ttu-id="59fe5-233">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="59fe5-233">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="59fe5-234">-Haut</span><span class="sxs-lookup"><span data-stu-id="59fe5-234">-Top</span></span>

<span data-ttu-id="59fe5-235">Spécifie le nombre d’objets à obtenir à partir du début d’un tableau d’objets trié.</span><span class="sxs-lookup"><span data-stu-id="59fe5-235">Specifies the number of objects to get from the start of a sorted object array.</span></span> <span data-ttu-id="59fe5-236">Cela entraîne un tri stable.</span><span class="sxs-lookup"><span data-stu-id="59fe5-236">This results in a stable sort.</span></span>

<span data-ttu-id="59fe5-237">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="59fe5-237">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Top
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="59fe5-238">-Unique</span><span class="sxs-lookup"><span data-stu-id="59fe5-238">-Unique</span></span>

<span data-ttu-id="59fe5-239">Indique que `Sort-Object` élimine les doublons et ne retourne que les membres uniques de la collection.</span><span class="sxs-lookup"><span data-stu-id="59fe5-239">Indicates that `Sort-Object` eliminates duplicates and returns only the unique members of the collection.</span></span> <span data-ttu-id="59fe5-240">La première instance d’une valeur unique est incluse dans la sortie triée.</span><span class="sxs-lookup"><span data-stu-id="59fe5-240">The first instance of a unique value is included in the sorted output.</span></span>

<span data-ttu-id="59fe5-241">**Unique** ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="59fe5-241">**Unique** is case-insensitive.</span></span> <span data-ttu-id="59fe5-242">Les chaînes qui diffèrent uniquement par la casse des caractères sont considérées comme identiques.</span><span class="sxs-lookup"><span data-stu-id="59fe5-242">Strings that only differ by character case are considered the same.</span></span>
<span data-ttu-id="59fe5-243">Par exemple, caractère et caractère.</span><span class="sxs-lookup"><span data-stu-id="59fe5-243">For example, character and CHARACTER.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="59fe5-244">-Stable</span><span class="sxs-lookup"><span data-stu-id="59fe5-244">-Stable</span></span>

<span data-ttu-id="59fe5-245">Les objets triés sont remis dans l’ordre dans lequel ils ont été reçus lorsque les critères de tri sont égaux.</span><span class="sxs-lookup"><span data-stu-id="59fe5-245">The sorted objects are delivered in the order they were received when the sort criteria are equal.</span></span>

<span data-ttu-id="59fe5-246">Ce paramètre a été ajouté dans PowerShell v 6.2.0.</span><span class="sxs-lookup"><span data-stu-id="59fe5-246">This parameter was added in PowerShell v6.2.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="59fe5-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="59fe5-247">CommonParameters</span></span>

<span data-ttu-id="59fe5-248">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="59fe5-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="59fe5-249">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="59fe5-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="59fe5-250">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="59fe5-250">INPUTS</span></span>

### <span data-ttu-id="59fe5-251">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="59fe5-251">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="59fe5-252">Vous pouvez diriger les objets à trier vers `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="59fe5-252">You can pipe the objects to be sorted to `Sort-Object`.</span></span>

## <span data-ttu-id="59fe5-253">SORTIES</span><span class="sxs-lookup"><span data-stu-id="59fe5-253">OUTPUTS</span></span>

### <span data-ttu-id="59fe5-254">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="59fe5-254">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="59fe5-255">`Sort-Object` retourne les objets triés.</span><span class="sxs-lookup"><span data-stu-id="59fe5-255">`Sort-Object` returns the sorted objects.</span></span>

## <span data-ttu-id="59fe5-256">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="59fe5-256">NOTES</span></span>

<span data-ttu-id="59fe5-257">L' `Sort-Object` applet de commande trie les objets en fonction des propriétés spécifiées dans la commande ou des propriétés de tri par défaut du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="59fe5-257">The `Sort-Object` cmdlet sorts objects based on properties specified in the command or the default sort properties for the object type.</span></span> <span data-ttu-id="59fe5-258">Les propriétés de tri par défaut sont définies à l’aide du `PropertySet` nommé `DefaultKeyPropertySet` dans un `types.ps1xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="59fe5-258">Default sort properties are defined using the `PropertySet` named `DefaultKeyPropertySet` in a `types.ps1xml` file.</span></span> <span data-ttu-id="59fe5-259">Pour plus d’informations, consultez [about_Types.ps1XML](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="59fe5-259">For more information, see [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span></span>

<span data-ttu-id="59fe5-260">Si un objet n’a pas l’une des propriétés spécifiées, la valeur de la propriété de cet objet est interprétée par `Sort-Object` comme **null** et placée à la fin de l’ordre de tri.</span><span class="sxs-lookup"><span data-stu-id="59fe5-260">If an object does not have one of the specified properties, the property value for that object is interpreted by `Sort-Object` as **Null** and placed at the end of the sort order.</span></span>

<span data-ttu-id="59fe5-261">Lorsqu’aucune propriété de tri n’est disponible, PowerShell tente de comparer les objets eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="59fe5-261">When no sort properties are available, PowerShell attempts to compare the objects themselves.</span></span>
<span data-ttu-id="59fe5-262">`Sort-Object` utilise la méthode **compare** pour chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="59fe5-262">`Sort-Object` uses the **Compare** method for each property.</span></span> <span data-ttu-id="59fe5-263">Si une propriété n’implémente pas **IComparable**, l’applet de commande convertit la valeur de la propriété en une chaîne et utilise la méthode **compare** pour **System. String**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-263">If a property does not implement **IComparable**, the cmdlet converts the property value to a string and uses the **Compare** method for **System.String**.</span></span> <span data-ttu-id="59fe5-264">Pour plus d’informations, consultez la [méthode PSObject. CompareTo (Object)](/dotnet/api/system.management.automation.psobject.compareto).</span><span class="sxs-lookup"><span data-stu-id="59fe5-264">For more information, see [PSObject.CompareTo(Object) Method](/dotnet/api/system.management.automation.psobject.compareto).</span></span>

<span data-ttu-id="59fe5-265">Si vous triez sur une propriété énumérée telle que **Status**, `Sort-Object` trie par valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="59fe5-265">If you sort on an enumerated property such as **Status**, `Sort-Object` sorts by the enumeration values.</span></span> <span data-ttu-id="59fe5-266">Pour les services Windows, l’état **arrêté** a la valeur **1** et l' **exécution** a la valeur **4**.</span><span class="sxs-lookup"><span data-stu-id="59fe5-266">For Windows services, **Stopped** has a value of **1** and **Running** has a value of **4**.</span></span>
<span data-ttu-id="59fe5-267">L’état **arrêté** est trié avant l' **exécution en** raison des valeurs énumérées.</span><span class="sxs-lookup"><span data-stu-id="59fe5-267">**Stopped** is sorted before **Running** because of the enumerated values.</span></span> <span data-ttu-id="59fe5-268">Pour plus d’informations, consultez [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="59fe5-268">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="59fe5-269">Les performances de l’algorithme de tri sont plus lentes lorsque vous procédez à un tri stable.</span><span class="sxs-lookup"><span data-stu-id="59fe5-269">The performance of the sorting algorithm is slower when doing a stable sort.</span></span>

## <span data-ttu-id="59fe5-270">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="59fe5-270">RELATED LINKS</span></span>

[<span data-ttu-id="59fe5-271">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="59fe5-271">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="59fe5-272">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="59fe5-272">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="59fe5-273">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="59fe5-273">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="59fe5-274">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="59fe5-274">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="59fe5-275">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="59fe5-275">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="59fe5-276">Group-Object</span><span class="sxs-lookup"><span data-stu-id="59fe5-276">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="59fe5-277">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="59fe5-277">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="59fe5-278">New-Object</span><span class="sxs-lookup"><span data-stu-id="59fe5-278">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="59fe5-279">Select-Object</span><span class="sxs-lookup"><span data-stu-id="59fe5-279">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="59fe5-280">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="59fe5-280">Tee-Object</span></span>](Tee-Object.md)
