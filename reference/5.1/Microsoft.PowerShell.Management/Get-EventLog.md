---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204021"
---
# <span data-ttu-id="7144d-103">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="7144d-103">Get-EventLog</span></span>

## <span data-ttu-id="7144d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7144d-104">SYNOPSIS</span></span>
<span data-ttu-id="7144d-105">Obtient les événements dans un journal des événements ou une liste des journaux des événements sur l’ordinateur local ou les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="7144d-105">Gets the events in an event log, or a list of the event logs, on the local computer or remote computers.</span></span>

## <span data-ttu-id="7144d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7144d-106">SYNTAX</span></span>

### <span data-ttu-id="7144d-107">LogName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="7144d-107">LogName (Default)</span></span>

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### <span data-ttu-id="7144d-108">List</span><span class="sxs-lookup"><span data-stu-id="7144d-108">List</span></span>

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## <span data-ttu-id="7144d-109">Description</span><span class="sxs-lookup"><span data-stu-id="7144d-109">DESCRIPTION</span></span>

<span data-ttu-id="7144d-110">L' `Get-EventLog` applet de commande obtient les événements et les journaux des événements à partir des ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="7144d-110">The `Get-EventLog` cmdlet gets events and event logs from local and remote computers.</span></span> <span data-ttu-id="7144d-111">Par défaut, `Get-EventLog` obtient les journaux à partir de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7144d-111">By default, `Get-EventLog` gets logs from the local computer.</span></span> <span data-ttu-id="7144d-112">Pour récupérer des journaux à partir d’ordinateurs distants, utilisez le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="7144d-112">To get logs from remote computers, use the **ComputerName** parameter.</span></span>

<span data-ttu-id="7144d-113">Vous pouvez utiliser les `Get-EventLog` paramètres et les valeurs de propriété pour rechercher des événements.</span><span class="sxs-lookup"><span data-stu-id="7144d-113">You can use the `Get-EventLog` parameters and property values to search for events.</span></span> <span data-ttu-id="7144d-114">L’applet de commande obtient les événements qui correspondent aux valeurs de propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7144d-114">The cmdlet gets events that match the specified property values.</span></span>

<span data-ttu-id="7144d-115">Les applets de commande PowerShell qui contiennent le `EventLog` nom fonctionnent uniquement sur les journaux des événements Windows classiques, tels que l’application, le système ou la sécurité.</span><span class="sxs-lookup"><span data-stu-id="7144d-115">PowerShell cmdlets that contain the `EventLog` noun work only on Windows classic event logs such as Application, System, or Security.</span></span> <span data-ttu-id="7144d-116">Pour récupérer les journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures de Windows, utilisez `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="7144d-116">To get logs that use the Windows Event Log technology in Windows Vista and later Windows versions, use `Get-WinEvent`.</span></span>

> [!NOTE]
> <span data-ttu-id="7144d-117">`Get-EventLog` utilise une API Win32 déconseillée.</span><span class="sxs-lookup"><span data-stu-id="7144d-117">`Get-EventLog` uses a Win32 API that is deprecated.</span></span> <span data-ttu-id="7144d-118">Les résultats peuvent ne pas être précis.</span><span class="sxs-lookup"><span data-stu-id="7144d-118">The results may not be accurate.</span></span> <span data-ttu-id="7144d-119">Utilisez plutôt l’applet de commande `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="7144d-119">Use the `Get-WinEvent` cmdlet instead.</span></span>

## <span data-ttu-id="7144d-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7144d-120">EXAMPLES</span></span>

### <span data-ttu-id="7144d-121">Exemple 1 : récupérer les journaux des événements sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="7144d-121">Example 1: Get event logs on the local computer</span></span>

<span data-ttu-id="7144d-122">Cet exemple affiche la liste des journaux des événements disponibles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7144d-122">This example displays the list of event logs that are available on the local computer.</span></span> <span data-ttu-id="7144d-123">Les noms de la colonne log sont utilisés avec le paramètre **logname** pour spécifier le journal dans lequel les événements sont recherchés.</span><span class="sxs-lookup"><span data-stu-id="7144d-123">The names in the Log column are used with the **LogName** parameter to specify which log is searched for events.</span></span>

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

<span data-ttu-id="7144d-124">L' `Get-EventLog` applet de commande utilise le paramètre **List** pour afficher les journaux disponibles.</span><span class="sxs-lookup"><span data-stu-id="7144d-124">The `Get-EventLog` cmdlet uses the **List** parameter to display the available logs.</span></span>

### <span data-ttu-id="7144d-125">Exemple 2 : récupérer les entrées récentes à partir d’un journal des événements sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="7144d-125">Example 2: Get recent entries from an event log on the local computer</span></span>

<span data-ttu-id="7144d-126">Cet exemple obtient les entrées récentes du journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="7144d-126">This example gets recent entries from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

<span data-ttu-id="7144d-127">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="7144d-127">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="7144d-128">Le paramètre le plus **récent** retourne les cinq événements les plus récents.</span><span class="sxs-lookup"><span data-stu-id="7144d-128">The **Newest** parameter returns the five most recent events.</span></span>

### <span data-ttu-id="7144d-129">Exemple 3 : Rechercher toutes les sources pour un nombre spécifique d’entrées dans un journal des événements</span><span class="sxs-lookup"><span data-stu-id="7144d-129">Example 3: Find all sources for a specific number of entries in an event log</span></span>

<span data-ttu-id="7144d-130">Cet exemple montre comment rechercher toutes les sources incluses dans les 1000 entrées les plus récentes dans le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="7144d-130">This example shows how to find all of the sources that are included in the 1000 most recent entries in the System event log.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

<span data-ttu-id="7144d-131">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système.</span><span class="sxs-lookup"><span data-stu-id="7144d-131">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="7144d-132">Le paramètre le plus **récent** sélectionne les événements les plus récents 1000.</span><span class="sxs-lookup"><span data-stu-id="7144d-132">The **Newest** parameter selects the 1000 most recent events.</span></span> <span data-ttu-id="7144d-133">Les objets d’événement sont stockés dans la `$Events` variable.</span><span class="sxs-lookup"><span data-stu-id="7144d-133">The event objects are stored in the `$Events` variable.</span></span> <span data-ttu-id="7144d-134">Les `$Events` objets sont envoyés dans le pipeline à l’applet de commande `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="7144d-134">The `$Events` objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span>
<span data-ttu-id="7144d-135">`Group-Object` utilise le paramètre **Property** pour regrouper les objets par source et compte le nombre d’objets pour chaque source.</span><span class="sxs-lookup"><span data-stu-id="7144d-135">`Group-Object` uses the **Property** parameter to group the objects by source and counts the number of objects for each source.</span></span> <span data-ttu-id="7144d-136">Le paramètre **NoElement** supprime les membres du groupe de la sortie.</span><span class="sxs-lookup"><span data-stu-id="7144d-136">The **NoElement** parameter removes the group members from the output.</span></span>
<span data-ttu-id="7144d-137">L' `Sort-Object` applet de commande utilise le paramètre **Property** pour effectuer un tri selon le nombre de chaque nom de source.</span><span class="sxs-lookup"><span data-stu-id="7144d-137">The `Sort-Object` cmdlet uses the **Property** parameter to sort by the count of each source name.</span></span>
<span data-ttu-id="7144d-138">Le paramètre **décroissant** trie la liste dans l’ordre par nombre de la plus élevée à la plus faible.</span><span class="sxs-lookup"><span data-stu-id="7144d-138">The **Descending** parameter sorts the list in order by count from highest to lowest.</span></span>

### <span data-ttu-id="7144d-139">Exemple 4 : obtenir des événements d’erreur à partir d’un journal des événements spécifique</span><span class="sxs-lookup"><span data-stu-id="7144d-139">Example 4: Get error events from a specific event log</span></span>

<span data-ttu-id="7144d-140">Cet exemple obtient les événements d’erreur du journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="7144d-140">This example gets error events from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

<span data-ttu-id="7144d-141">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système.</span><span class="sxs-lookup"><span data-stu-id="7144d-141">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="7144d-142">Le paramètre **entryType** filtre les événements pour afficher uniquement les événements d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7144d-142">The **EntryType** parameter filters the events to show only Error events.</span></span>

### <span data-ttu-id="7144d-143">Exemple 5 : récupérer des événements à partir d’un journal des événements avec un InstanceId et une valeur source</span><span class="sxs-lookup"><span data-stu-id="7144d-143">Example 5: Get events from an event log with an InstanceId and Source value</span></span>

<span data-ttu-id="7144d-144">Cet exemple obtient les événements du journal système pour un InstanceId et une source spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7144d-144">This example gets events from the System log for a specific InstanceId and Source.</span></span>

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

<span data-ttu-id="7144d-145">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système.</span><span class="sxs-lookup"><span data-stu-id="7144d-145">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="7144d-146">Le paramètre **InstanceID** sélectionne les événements avec l’ID d’instance spécifié.</span><span class="sxs-lookup"><span data-stu-id="7144d-146">The **InstanceID** parameter selects the events with the specified Instance ID.</span></span> <span data-ttu-id="7144d-147">Le paramètre **source** spécifie la propriété de l’événement.</span><span class="sxs-lookup"><span data-stu-id="7144d-147">The **Source** parameter specifies the event property.</span></span>

### <span data-ttu-id="7144d-148">Exemple 6 : récupération d’événements à partir de plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="7144d-148">Example 6: Get events from multiple computers</span></span>

<span data-ttu-id="7144d-149">Cette commande obtient les événements du journal des événements système sur trois ordinateurs : Serveur01, Server02 et Server03.</span><span class="sxs-lookup"><span data-stu-id="7144d-149">This command gets the events from the System event log on three computers: Server01, Server02, and Server03.</span></span>

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="7144d-150">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système.</span><span class="sxs-lookup"><span data-stu-id="7144d-150">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="7144d-151">Le paramètre **ComputerName** utilise une chaîne séparée par des virgules pour répertorier les ordinateurs à partir desquels vous souhaitez obtenir les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="7144d-151">The **ComputerName** parameter uses a comma-separated string to list the computers from which you want to get the event logs.</span></span>

### <span data-ttu-id="7144d-152">Exemple 7 : obtenir tous les événements qui incluent un mot spécifique dans le message</span><span class="sxs-lookup"><span data-stu-id="7144d-152">Example 7: Get all events that include a specific word in the message</span></span>

<span data-ttu-id="7144d-153">Cette commande obtient tous les événements du journal des événements système qui contiennent un mot spécifique dans le message de l’événement.</span><span class="sxs-lookup"><span data-stu-id="7144d-153">This command gets all the events in the System event log that contain a specific word in the event's message.</span></span> <span data-ttu-id="7144d-154">Il est possible que la valeur de votre paramètre de **message** spécifié soit incluse dans le contenu du message, mais ne s’affiche pas sur la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7144d-154">It's possible that your specified **Message** parameter's value is included in the message's content but isn't displayed on the PowerShell console.</span></span>

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

<span data-ttu-id="7144d-155">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="7144d-155">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="7144d-156">Le paramètre **message** spécifie un mot à rechercher dans le champ message de chaque événement.</span><span class="sxs-lookup"><span data-stu-id="7144d-156">The **Message** parameter specifies a word to search for in the message field of each event.</span></span>

### <span data-ttu-id="7144d-157">Exemple 8 : afficher les valeurs de propriété d’un événement</span><span class="sxs-lookup"><span data-stu-id="7144d-157">Example 8: Display the property values of an event</span></span>

<span data-ttu-id="7144d-158">Cet exemple montre comment afficher toutes les propriétés et valeurs d’un événement.</span><span class="sxs-lookup"><span data-stu-id="7144d-158">This example shows how to display all of an event's properties and values.</span></span>

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

<span data-ttu-id="7144d-159">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="7144d-159">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="7144d-160">Le paramètre le plus **récent** sélectionne l’objet événement le plus récent.</span><span class="sxs-lookup"><span data-stu-id="7144d-160">The **Newest** parameter selects the most recent event object.</span></span> <span data-ttu-id="7144d-161">L’objet est stocké dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="7144d-161">The object is stored in the `$A` variable.</span></span> <span data-ttu-id="7144d-162">L’objet dans la `$A` variable est envoyé dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="7144d-162">The object in the `$A` variable is sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="7144d-163">`Select-Object` utilise le paramètre **Property** avec un astérisque ( `*` ) pour sélectionner toutes les propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="7144d-163">`Select-Object` uses the **Property** parameter with an asterisk (`*`) to select all of the object's properties.</span></span>

### <span data-ttu-id="7144d-164">Exemple 9 : obtenir des événements à partir d’un journal des événements à l’aide d’un ID de source et d’événement</span><span class="sxs-lookup"><span data-stu-id="7144d-164">Example 9: Get events from an event log using a source and event ID</span></span>

<span data-ttu-id="7144d-165">Cet exemple obtient les événements d’une source et d’un ID d’événement spécifiés.</span><span class="sxs-lookup"><span data-stu-id="7144d-165">This example gets events for a specified Source and Event ID.</span></span>

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

<span data-ttu-id="7144d-166">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal des événements de l’application.</span><span class="sxs-lookup"><span data-stu-id="7144d-166">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the Application event log.</span></span> <span data-ttu-id="7144d-167">Le paramètre **source** spécifie le nom de l’application, Outlook.</span><span class="sxs-lookup"><span data-stu-id="7144d-167">The **Source** parameter specifies the application name, Outlook.</span></span> <span data-ttu-id="7144d-168">Les objets sont envoyés dans le pipeline à l’applet de commande `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="7144d-168">The objects are sent down the pipeline to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="7144d-169">Pour chaque objet dans le pipeline, l’applet de commande `Where-Object` utilise la variable `$_.EventID` pour comparer la propriété de l’ID d’événement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7144d-169">For each object in the pipeline, the `Where-Object` cmdlet uses the variable `$_.EventID` to compare the Event ID property to the specified value.</span></span> <span data-ttu-id="7144d-170">Les objets sont envoyés dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="7144d-170">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="7144d-171">`Select-Object` utilise le paramètre **Property** pour sélectionner les propriétés à afficher dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7144d-171">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="7144d-172">Exemple 10 : obtenir des événements et les regrouper par une propriété</span><span class="sxs-lookup"><span data-stu-id="7144d-172">Example 10: Get events and group by a property</span></span>

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

<span data-ttu-id="7144d-173">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système.</span><span class="sxs-lookup"><span data-stu-id="7144d-173">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="7144d-174">Le paramètre **username** comprend le `*` caractère générique astérisque () pour spécifier une partie du nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7144d-174">The **UserName** parameter includes the asterisk (`*`) wildcard to specify a portion of the user name.</span></span> <span data-ttu-id="7144d-175">Les objets d’événement sont envoyés dans le pipeline à l’applet de commande `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="7144d-175">The event objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span> <span data-ttu-id="7144d-176">`Group-Object` utilise le paramètre **Property** pour spécifier que la propriété **username** est utilisée pour regrouper les objets et compter le nombre d’objets pour chaque nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7144d-176">`Group-Object` uses the **Property** parameter to specify that the **UserName** property is used to group the objects and count the number of objects for each user name.</span></span> <span data-ttu-id="7144d-177">Le paramètre **NoElement** supprime les membres du groupe de la sortie.</span><span class="sxs-lookup"><span data-stu-id="7144d-177">The **NoElement** parameter removes the group members from the output.</span></span> <span data-ttu-id="7144d-178">Les objets sont envoyés dans le pipeline à l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="7144d-178">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="7144d-179">`Select-Object` utilise le paramètre **Property** pour sélectionner les propriétés à afficher dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7144d-179">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="7144d-180">Exemple 11 : obtenir des événements qui se sont produits pendant une plage de dates et d’heures spécifique</span><span class="sxs-lookup"><span data-stu-id="7144d-180">Example 11: Get events that occurred during a specific date and time range</span></span>

<span data-ttu-id="7144d-181">Cet exemple obtient les événements d’erreur du journal des événements système pour une plage de dates et d’heures spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7144d-181">This example gets Error events from the System event log for a specified date and time range.</span></span> <span data-ttu-id="7144d-182">Les paramètres **Before** et **after** définissent la plage de dates et d’heures, mais sont exclus de la sortie.</span><span class="sxs-lookup"><span data-stu-id="7144d-182">The **Before** and **After** parameters set the date and time range but are excluded from the output.</span></span>

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

<span data-ttu-id="7144d-183">L' `Get-Date` applet de commande utilise le paramètre **Date** pour spécifier une date et une heure.</span><span class="sxs-lookup"><span data-stu-id="7144d-183">The `Get-Date` cmdlet uses the **Date** parameter to specify a date and time.</span></span> <span data-ttu-id="7144d-184">Les objets **DateTime** sont stockés dans les `$Begin` `$End` variables et.</span><span class="sxs-lookup"><span data-stu-id="7144d-184">The **DateTime** objects are stored in the `$Begin` and `$End` variables.</span></span> <span data-ttu-id="7144d-185">L' `Get-EventLog` applet de commande utilise le paramètre **logname** pour spécifier le journal système.</span><span class="sxs-lookup"><span data-stu-id="7144d-185">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="7144d-186">Le paramètre **entryType** spécifie le type d’événement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7144d-186">The **EntryType** parameter specifies the Error event type.</span></span> <span data-ttu-id="7144d-187">La plage de dates et d’heures est définie par le paramètre **after** et `$Begin` la variable, ainsi que par la variable et le paramètre **Before** `$End` .</span><span class="sxs-lookup"><span data-stu-id="7144d-187">The date and time range is set by the **After** parameter and `$Begin` variable and the **Before** parameter and `$End` variable.</span></span>

## <span data-ttu-id="7144d-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7144d-188">PARAMETERS</span></span>

### <span data-ttu-id="7144d-189">-Après</span><span class="sxs-lookup"><span data-stu-id="7144d-189">-After</span></span>

<span data-ttu-id="7144d-190">Obtient les événements qui se sont produits après une date et une heure spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7144d-190">Gets events that occurred after a specified date and time.</span></span> <span data-ttu-id="7144d-191">La date et l’heure du paramètre **after** sont exclues de la sortie.</span><span class="sxs-lookup"><span data-stu-id="7144d-191">The **After** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="7144d-192">Entrez un objet **DateTime** , tel que la valeur retournée par l’applet de commande `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="7144d-192">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-193">-AsBaseObject</span><span class="sxs-lookup"><span data-stu-id="7144d-193">-AsBaseObject</span></span>

<span data-ttu-id="7144d-194">Indique que cette applet de commande retourne un objet **System. Diagnostics. EventLogEntry** standard pour chaque événement.</span><span class="sxs-lookup"><span data-stu-id="7144d-194">Indicates that this cmdlet returns a standard **System.Diagnostics.EventLogEntry** object for each event.</span></span> <span data-ttu-id="7144d-195">Sans ce paramètre, `Get-EventLog` retourne un objet **PSObject** étendu avec des propriétés **EventLogName** , **source** et **InstanceID** supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="7144d-195">Without this parameter, `Get-EventLog` returns an extended **PSObject** object with additional **EventLogName** , **Source** , and **InstanceId** properties.</span></span>

<span data-ttu-id="7144d-196">Pour voir l’effet de ce paramètre, dirigez les événements vers l’applet de commande `Get-Member` et examinez la valeur **TypeName** dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="7144d-196">To see the effect of this parameter, pipe the events to the `Get-Member` cmdlet and examine the **TypeName** value in the result.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-197">-AsString</span><span class="sxs-lookup"><span data-stu-id="7144d-197">-AsString</span></span>

<span data-ttu-id="7144d-198">Indique que cette applet de commande retourne la sortie sous forme de chaînes, au lieu d’objets.</span><span class="sxs-lookup"><span data-stu-id="7144d-198">Indicates that this cmdlet returns the output as strings, instead of objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-199">-Avant</span><span class="sxs-lookup"><span data-stu-id="7144d-199">-Before</span></span>

<span data-ttu-id="7144d-200">Obtient les événements qui se sont produits avant une date et une heure spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7144d-200">Gets events that occurred before a specified date and time.</span></span> <span data-ttu-id="7144d-201">La date et l’heure du paramètre **Before** sont exclues de la sortie.</span><span class="sxs-lookup"><span data-stu-id="7144d-201">The **Before** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="7144d-202">Entrez un objet **DateTime** , tel que la valeur retournée par l’applet de commande `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="7144d-202">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-203">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7144d-203">-ComputerName</span></span>

<span data-ttu-id="7144d-204">Ce paramètre spécifie le nom NetBIOS de l’ordinateur distant, l’adresse IP (Internet Protocol) ou un nom de domaine complet (FQDN).</span><span class="sxs-lookup"><span data-stu-id="7144d-204">This parameter specifies a remote computer's NetBIOS name, Internet Protocol (IP) address, or a fully qualified domain name (FQDN).</span></span>

<span data-ttu-id="7144d-205">Si le paramètre **ComputerName** n’est pas spécifié, `Get-EventLog` l’ordinateur local est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="7144d-205">If the **ComputerName** parameter isn't specified, `Get-EventLog` defaults to the local computer.</span></span> <span data-ttu-id="7144d-206">Le paramètre accepte également un point ( `.` ) pour spécifier l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7144d-206">The parameter also accepts a dot (`.`) to specify the local computer.</span></span>

<span data-ttu-id="7144d-207">Le paramètre **ComputerName** ne repose pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7144d-207">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="7144d-208">Vous pouvez utiliser `Get-EventLog` avec le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="7144d-208">You can use `Get-EventLog` with the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="7144d-209">-EntryType</span><span class="sxs-lookup"><span data-stu-id="7144d-209">-EntryType</span></span>

<span data-ttu-id="7144d-210">Spécifie, sous forme de tableau de chaînes, le type d’entrée des événements que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="7144d-210">Specifies, as a string array, the entry type of the events that this cmdlet gets.</span></span>

<span data-ttu-id="7144d-211">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="7144d-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7144d-212">Erreur</span><span class="sxs-lookup"><span data-stu-id="7144d-212">Error</span></span>
- <span data-ttu-id="7144d-213">Information</span><span class="sxs-lookup"><span data-stu-id="7144d-213">Information</span></span>
- <span data-ttu-id="7144d-214">FailureAudit</span><span class="sxs-lookup"><span data-stu-id="7144d-214">FailureAudit</span></span>
- <span data-ttu-id="7144d-215">SuccessAudit</span><span class="sxs-lookup"><span data-stu-id="7144d-215">SuccessAudit</span></span>
- <span data-ttu-id="7144d-216">Avertissement</span><span class="sxs-lookup"><span data-stu-id="7144d-216">Warning</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-217">-Index</span><span class="sxs-lookup"><span data-stu-id="7144d-217">-Index</span></span>

<span data-ttu-id="7144d-218">Spécifie les valeurs d’index à extraire du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="7144d-218">Specifies the index values to get from the event log.</span></span> <span data-ttu-id="7144d-219">Le paramètre accepte une chaîne de valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7144d-219">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-220">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="7144d-220">-InstanceId</span></span>

<span data-ttu-id="7144d-221">Spécifie les ID d’instance à récupérer à partir du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="7144d-221">Specifies the Instance IDs to get from the event log.</span></span> <span data-ttu-id="7144d-222">Le paramètre accepte une chaîne de valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7144d-222">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-223">-List</span><span class="sxs-lookup"><span data-stu-id="7144d-223">-List</span></span>

<span data-ttu-id="7144d-224">Affiche la liste des journaux des événements sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7144d-224">Displays the list of event logs on the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-225">-LogName</span><span class="sxs-lookup"><span data-stu-id="7144d-225">-LogName</span></span>

<span data-ttu-id="7144d-226">Spécifie le nom d’un journal des événements.</span><span class="sxs-lookup"><span data-stu-id="7144d-226">Specifies the name of one event log.</span></span> <span data-ttu-id="7144d-227">Pour rechercher les noms de journaux `Get-EventLog -List` , utilisez.</span><span class="sxs-lookup"><span data-stu-id="7144d-227">To find the log names use `Get-EventLog -List`.</span></span> <span data-ttu-id="7144d-228">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7144d-228">Wildcard characters are permitted.</span></span> <span data-ttu-id="7144d-229">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7144d-229">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7144d-230">-Message</span><span class="sxs-lookup"><span data-stu-id="7144d-230">-Message</span></span>

<span data-ttu-id="7144d-231">Spécifie une chaîne dans le message de l’événement.</span><span class="sxs-lookup"><span data-stu-id="7144d-231">Specifies a string in the event message.</span></span> <span data-ttu-id="7144d-232">Vous pouvez utiliser ce paramètre pour rechercher des messages qui contiennent certains mots ou certaines expressions.</span><span class="sxs-lookup"><span data-stu-id="7144d-232">You can use this parameter to search for messages that contain certain words or phrases.</span></span> <span data-ttu-id="7144d-233">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7144d-233">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7144d-234">-Plus récent</span><span class="sxs-lookup"><span data-stu-id="7144d-234">-Newest</span></span>

<span data-ttu-id="7144d-235">Commence par les événements les plus récents et obtient le nombre d’événements spécifié.</span><span class="sxs-lookup"><span data-stu-id="7144d-235">Begins with the newest events and gets the specified number of events.</span></span> <span data-ttu-id="7144d-236">Le nombre d’événements est requis, par exemple `-Newest 100` .</span><span class="sxs-lookup"><span data-stu-id="7144d-236">The number of events is required, for example `-Newest 100`.</span></span> <span data-ttu-id="7144d-237">Spécifie le nombre maximal d’événements qui sont retournés.</span><span class="sxs-lookup"><span data-stu-id="7144d-237">Specifies the maximum number of events that are returned.</span></span>

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7144d-238">-Source</span><span class="sxs-lookup"><span data-stu-id="7144d-238">-Source</span></span>

<span data-ttu-id="7144d-239">Spécifie, sous forme de tableau de chaînes, les sources qui ont été écrites dans le journal que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="7144d-239">Specifies, as a string array, sources that were written to the log that this cmdlet gets.</span></span> <span data-ttu-id="7144d-240">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7144d-240">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7144d-241">-UserName</span><span class="sxs-lookup"><span data-stu-id="7144d-241">-UserName</span></span>

<span data-ttu-id="7144d-242">Spécifie, sous forme de tableau de chaînes, les noms d’utilisateur associés à des événements.</span><span class="sxs-lookup"><span data-stu-id="7144d-242">Specifies, as a string array, user names that are associated with events.</span></span> <span data-ttu-id="7144d-243">Entrez des noms ou des modèles de nom, tels que `User01` , `User*` ou `Domain01\User*` .</span><span class="sxs-lookup"><span data-stu-id="7144d-243">Enter names or name patterns, such as `User01`, `User*`, or `Domain01\User*`.</span></span> <span data-ttu-id="7144d-244">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7144d-244">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7144d-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7144d-245">CommonParameters</span></span>

<span data-ttu-id="7144d-246">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7144d-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7144d-247">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7144d-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7144d-248">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7144d-248">INPUTS</span></span>

### <span data-ttu-id="7144d-249">Aucun</span><span class="sxs-lookup"><span data-stu-id="7144d-249">None</span></span>

<span data-ttu-id="7144d-250">Vous ne pouvez pas diriger d’entrée vers `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="7144d-250">You cannot pipe input to `Get-EventLog`.</span></span>

## <span data-ttu-id="7144d-251">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7144d-251">OUTPUTS</span></span>

### <span data-ttu-id="7144d-252">System. Diagnostics. EventLogEntry.</span><span class="sxs-lookup"><span data-stu-id="7144d-252">System.Diagnostics.EventLogEntry.</span></span> <span data-ttu-id="7144d-253">System. Diagnostics. EventLog.</span><span class="sxs-lookup"><span data-stu-id="7144d-253">System.Diagnostics.EventLog.</span></span> <span data-ttu-id="7144d-254">System.String</span><span class="sxs-lookup"><span data-stu-id="7144d-254">System.String</span></span>

<span data-ttu-id="7144d-255">Si le paramètre **logname** est spécifié, la sortie est une collection d’objets **System. Diagnostics. EventLogEntry** .</span><span class="sxs-lookup"><span data-stu-id="7144d-255">If the **LogName** parameter is specified, the output is a collection of **System.Diagnostics.EventLogEntry** objects.</span></span>

<span data-ttu-id="7144d-256">Si seul le paramètre **List** est spécifié, la sortie est une collection d’objets **System. Diagnostics. EventLog** .</span><span class="sxs-lookup"><span data-stu-id="7144d-256">If only the **List** parameter is specified, the output is a collection of **System.Diagnostics.EventLog** objects.</span></span>

<span data-ttu-id="7144d-257">Si les paramètres **List** et **AsString** sont tous les deux spécifiés, la sortie est une collection d’objets **System. String** .</span><span class="sxs-lookup"><span data-stu-id="7144d-257">If both the **List** and **AsString** parameters are specified, the output is a collection of **System.String** objects.</span></span>

## <span data-ttu-id="7144d-258">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7144d-258">NOTES</span></span>

<span data-ttu-id="7144d-259">Les applets de commande `Get-EventLog` et ne `Get-WinEvent` sont pas prises en charge dans le environnement de préinstallation Windows (WinPE) (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="7144d-259">The cmdlets `Get-EventLog` and `Get-WinEvent` are not supported in the Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="7144d-260">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7144d-260">RELATED LINKS</span></span>

[<span data-ttu-id="7144d-261">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="7144d-261">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="7144d-262">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="7144d-262">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="7144d-263">Group-Object</span><span class="sxs-lookup"><span data-stu-id="7144d-263">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="7144d-264">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="7144d-264">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="7144d-265">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="7144d-265">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="7144d-266">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="7144d-266">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="7144d-267">Select-Object</span><span class="sxs-lookup"><span data-stu-id="7144d-267">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="7144d-268">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="7144d-268">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="7144d-269">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="7144d-269">Write-EventLog</span></span>](Write-EventLog.md)
