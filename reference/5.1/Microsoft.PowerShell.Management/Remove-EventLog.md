---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203565"
---
# <span data-ttu-id="d678a-103">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="d678a-103">Remove-EventLog</span></span>

## <span data-ttu-id="d678a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d678a-104">SYNOPSIS</span></span>
<span data-ttu-id="d678a-105">Supprime un journal des événements ou annule l'inscription d'une source d'événement.</span><span class="sxs-lookup"><span data-stu-id="d678a-105">Deletes an event log or unregisters an event source.</span></span>

## <span data-ttu-id="d678a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d678a-106">SYNTAX</span></span>

### <span data-ttu-id="d678a-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d678a-107">Default (Default)</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d678a-108">Source</span><span class="sxs-lookup"><span data-stu-id="d678a-108">Source</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d678a-109">Description</span><span class="sxs-lookup"><span data-stu-id="d678a-109">DESCRIPTION</span></span>
<span data-ttu-id="d678a-110">L’applet de commande **Remove-EventLog** supprime un fichier journal des événements d’un ordinateur local ou distant et annule l’inscription de toutes ses sources d’événement pour le journal.</span><span class="sxs-lookup"><span data-stu-id="d678a-110">The **Remove-EventLog** cmdlet deletes an event log file from a local or remote computer and unregisters all its event sources for the log.</span></span>
<span data-ttu-id="d678a-111">Vous pouvez également utiliser cette applet de commande pour annuler l’inscription des sources d’événement sans supprimer de journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="d678a-111">You can also use this cmdlet to unregister event sources without deleting any event logs.</span></span>

<span data-ttu-id="d678a-112">Les applets de commande qui contiennent le nom **EventLog** , les applets de commande **EventLog** , fonctionnent uniquement sur les journaux des événements classiques.</span><span class="sxs-lookup"><span data-stu-id="d678a-112">The cmdlets that contain the **EventLog** noun, the **EventLog** cmdlets, work only on classic event logs.</span></span>
<span data-ttu-id="d678a-113">Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures du système d’exploitation Windows, utilisez la WinEvent.</span><span class="sxs-lookup"><span data-stu-id="d678a-113">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use Get-WinEvent.</span></span>

<span data-ttu-id="d678a-114">ATTENTION : cette applet de commande peut supprimer les journaux des événements du système d’exploitation, ce qui peut entraîner des échecs d’application et un comportement inattendu du système.</span><span class="sxs-lookup"><span data-stu-id="d678a-114">CAUTION: This cmdlet can delete operating system event logs, which might cause application failures and unexpected system behavior.</span></span>

## <span data-ttu-id="d678a-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d678a-115">EXAMPLES</span></span>

### <span data-ttu-id="d678a-116">Exemple 1 : supprimer un journal des événements de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="d678a-116">Example 1: Remove an event log from the local computer</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

<span data-ttu-id="d678a-117">Cette commande supprime le journal des événements MyLog de l’ordinateur local et annule l’inscription de ses sources d’événement.</span><span class="sxs-lookup"><span data-stu-id="d678a-117">This command deletes the MyLog event log from the local computer and unregisters its event sources.</span></span>

### <span data-ttu-id="d678a-118">Exemple 2 : supprimer un journal des événements de plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="d678a-118">Example 2: Remove an event log from several computers</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="d678a-119">Cette commande supprime les journaux des événements MyLog et TestLog de l’ordinateur local et des ordinateurs distants SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="d678a-119">This command deletes the MyLog and TestLog event logs from the local computer and the Server01 and Server02 remote computers.</span></span>
<span data-ttu-id="d678a-120">La commande annule également l’inscription des sources d’événement de ces journaux.</span><span class="sxs-lookup"><span data-stu-id="d678a-120">The command also unregisters the event sources for these logs.</span></span>

### <span data-ttu-id="d678a-121">Exemple 3 : supprimer une source d’événement</span><span class="sxs-lookup"><span data-stu-id="d678a-121">Example 3: Delete an event source</span></span>

```
PS C:\> Remove-EventLog -Source "MyApp"
```

<span data-ttu-id="d678a-122">Cette commande supprime la source d’événement MyApp des journaux sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d678a-122">This command deletes the MyApp event source from the logs on the local computer.</span></span>
<span data-ttu-id="d678a-123">Une fois la commande terminée, le programme MyApp ne peut pas écrire dans les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="d678a-123">When the command finishes, the MyApp program cannot write to any event logs.</span></span>

### <span data-ttu-id="d678a-124">Exemple 4 : supprimer un journal des événements et confirmer l’action</span><span class="sxs-lookup"><span data-stu-id="d678a-124">Example 4: Remove an event log and confirm the action</span></span>

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

<span data-ttu-id="d678a-125">Ces commandes montrent comment répertorier les journaux des événements sur un ordinateur et vérifier qu’une commande **Remove-EventLog** a réussi.</span><span class="sxs-lookup"><span data-stu-id="d678a-125">These commands show how to list the event logs on a computer and verify that a **Remove-EventLog** command was successful.</span></span>

### <span data-ttu-id="d678a-126">Exemple 5 : supprimer une source d’événement et confirmer l’action</span><span class="sxs-lookup"><span data-stu-id="d678a-126">Example 5: Remove an event source and confirm the action</span></span>

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

<span data-ttu-id="d678a-127">Ces commandes utilisent l’applet de commande Get-WmiObject pour répertorier les sources d’événement présentes sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d678a-127">These commands use the Get-WmiObject cmdlet to list the event sources on the local computer.</span></span>
<span data-ttu-id="d678a-128">Vous pouvez utiliser ces commandes pour vérifier la réussite d’une commande ou pour supprimer une source d’événement.</span><span class="sxs-lookup"><span data-stu-id="d678a-128">You can these commands to verify the success of a command or to delete an event source.</span></span>

<span data-ttu-id="d678a-129">La première commande obtient les sources d’événement du journal des événements TestLog présent sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d678a-129">The first command gets the event sources of the TestLog event log on the local computer.</span></span>
<span data-ttu-id="d678a-130">MyApp fait partie de ces sources.</span><span class="sxs-lookup"><span data-stu-id="d678a-130">MyApp is one of the sources.</span></span>

<span data-ttu-id="d678a-131">La deuxième commande utilise le paramètre *source* de **Remove-EventLog** pour supprimer la source d’événement MyApp.</span><span class="sxs-lookup"><span data-stu-id="d678a-131">The second command uses the *Source* parameter of **Remove-EventLog** to delete the MyApp event source.</span></span>

<span data-ttu-id="d678a-132">La troisième commande est identique à la première.</span><span class="sxs-lookup"><span data-stu-id="d678a-132">The third command is identical to the first.</span></span>
<span data-ttu-id="d678a-133">Elle indique que la source d’événement MyApp a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="d678a-133">It shows that the MyApp event source was deleted.</span></span>

## <span data-ttu-id="d678a-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d678a-134">PARAMETERS</span></span>

### <span data-ttu-id="d678a-135">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d678a-135">-ComputerName</span></span>
<span data-ttu-id="d678a-136">Spécifie un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d678a-136">Specifies a remote computer.</span></span>
<span data-ttu-id="d678a-137">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d678a-137">The default is the local computer.</span></span>

<span data-ttu-id="d678a-138">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d678a-138">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="d678a-139">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="d678a-139">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="d678a-140">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d678a-140">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="d678a-141">Vous pouvez utiliser le paramètre *ComputerName* de **Remove-EventLog** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="d678a-141">You can use the *ComputerName* parameter of **Remove-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d678a-142">-LogName</span><span class="sxs-lookup"><span data-stu-id="d678a-142">-LogName</span></span>
<span data-ttu-id="d678a-143">Spécifie les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="d678a-143">Specifies the event logs.</span></span>
<span data-ttu-id="d678a-144">Entrez le nom du journal d’un ou plusieurs journaux des événements, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="d678a-144">Enter the log name of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="d678a-145">Le nom du journal est la valeur de la propriété **log** , et non *et non LogDisplayName* , les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="d678a-145">The log name is the value of the **Log** property, not the *LogDisplayName* , Wildcard characters are not permitted.</span></span>
<span data-ttu-id="d678a-146">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d678a-146">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d678a-147">-Source</span><span class="sxs-lookup"><span data-stu-id="d678a-147">-Source</span></span>
<span data-ttu-id="d678a-148">Spécifie les sources d’événements que cette applet de commande annule.</span><span class="sxs-lookup"><span data-stu-id="d678a-148">Specifies the event sources that this cmdlet unregisters.</span></span>
<span data-ttu-id="d678a-149">Entrez les noms des sources, et non le nom de l’exécutable, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="d678a-149">Enter the source names, not the executable name, separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d678a-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d678a-150">-Confirm</span></span>
<span data-ttu-id="d678a-151">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d678a-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d678a-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d678a-152">-WhatIf</span></span>
<span data-ttu-id="d678a-153">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d678a-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d678a-154">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d678a-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d678a-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d678a-155">CommonParameters</span></span>
<span data-ttu-id="d678a-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d678a-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d678a-157">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d678a-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d678a-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d678a-158">INPUTS</span></span>

### <span data-ttu-id="d678a-159">Aucun</span><span class="sxs-lookup"><span data-stu-id="d678a-159">None</span></span>
<span data-ttu-id="d678a-160">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d678a-160">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d678a-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d678a-161">OUTPUTS</span></span>

### <span data-ttu-id="d678a-162">Aucun</span><span class="sxs-lookup"><span data-stu-id="d678a-162">None</span></span>
<span data-ttu-id="d678a-163">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d678a-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="d678a-164">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d678a-164">NOTES</span></span>

* <span data-ttu-id="d678a-165">Pour utiliser **Remove-EventLog** sur Windows Vista et les versions ultérieures du système d’exploitation Windows, démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="d678a-165">To use **Remove-EventLog** on Windows Vista and later versions of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

  <span data-ttu-id="d678a-166">Si vous supprimez un journal des événements et que vous recréez le journal par la suite, vous ne pourrez pas inscrire les mêmes sources d’événement.</span><span class="sxs-lookup"><span data-stu-id="d678a-166">If you remove an event log and then re-create the log, you will not be able to register the same event sources.</span></span>
<span data-ttu-id="d678a-167">Les applications qui ont utilisé les sources d’événement pour écrire des entrées dans le journal d’origine ne pourront rien écrire dans le nouveau journal.</span><span class="sxs-lookup"><span data-stu-id="d678a-167">Applications that used the events sources to write entries to the original log will not be able to write to the new log.</span></span>

* <span data-ttu-id="d678a-168">Lorsque vous annulez l’inscription d’une source d’événement d’un journal particulier, vous pouvez empêcher la source d’événement d’écrire des entrées dans d’autres journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="d678a-168">When you unregister an event source for a particular log, the event source might be prevented from writing entries in other event logs.</span></span>

## <span data-ttu-id="d678a-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d678a-169">RELATED LINKS</span></span>

[<span data-ttu-id="d678a-170">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="d678a-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="d678a-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="d678a-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="d678a-172">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="d678a-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="d678a-173">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="d678a-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="d678a-174">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="d678a-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="d678a-175">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="d678a-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="d678a-176">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="d678a-176">Write-EventLog</span></span>](Write-EventLog.md)
