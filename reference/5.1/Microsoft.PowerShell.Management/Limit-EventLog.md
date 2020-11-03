---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203618"
---
# <span data-ttu-id="7fa6b-103">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa6b-103">Limit-EventLog</span></span>

## <span data-ttu-id="7fa6b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7fa6b-104">SYNOPSIS</span></span>
<span data-ttu-id="7fa6b-105">Définit les propriétés de journal des événements qui limitent la taille du journal des événements et l'ancienneté de ses entrées.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-105">Sets the event log properties that limit the size of the event log and the age of its entries.</span></span>

## <span data-ttu-id="7fa6b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7fa6b-106">SYNTAX</span></span>

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7fa6b-107">Description</span><span class="sxs-lookup"><span data-stu-id="7fa6b-107">DESCRIPTION</span></span>
<span data-ttu-id="7fa6b-108">L’applet de commande **Limit-EventLog** définit la taille maximale d’un journal des événements classique, la durée pendant laquelle chaque événement doit être conservé et ce qui se produit lorsque le journal atteint sa taille maximale.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-108">The **Limit-EventLog** cmdlet sets the maximum size of a classic event log, how long each event must be retained, and what happens when the log reaches its maximum size.</span></span>
<span data-ttu-id="7fa6b-109">Vous pouvez l'utiliser pour limiter les journaux des événements sur les ordinateurs locaux ou distants.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-109">You can use it to limit the event logs on local or remote computers.</span></span>

<span data-ttu-id="7fa6b-110">Les applets de commande contenant le nom EventLog (les applets de commande EventLog) fonctionnent uniquement sur les journaux des événements classiques.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-110">The cmdlets that contain the EventLog noun (the EventLog cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="7fa6b-111">Pour obtenir des événements à partir des journaux qui utilisent la technologie Journal des événements Windows sous Windows Vista et les versions ultérieures de Windows, utilisez Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use Get-WinEvent.</span></span>

## <span data-ttu-id="7fa6b-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7fa6b-112">EXAMPLES</span></span>

### <span data-ttu-id="7fa6b-113">Exemple 1 : augmenter la taille d’un journal des événements</span><span class="sxs-lookup"><span data-stu-id="7fa6b-113">Example 1: Increase the size of an event log</span></span>

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

<span data-ttu-id="7fa6b-114">Cette commande augmente la taille maximale du journal des événements Windows PowerShell sur l'ordinateur local jusqu'à 20 480 octets (20 Ko).</span><span class="sxs-lookup"><span data-stu-id="7fa6b-114">This command increases the maximum size of the Windows PowerShell event log on the local computer to 20480 bytes (20 KB).</span></span>

### <span data-ttu-id="7fa6b-115">Exemple 2 : conserver un journal des événements pour une durée spécifiée</span><span class="sxs-lookup"><span data-stu-id="7fa6b-115">Example 2: Retain an event log for a specified duration</span></span>

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

<span data-ttu-id="7fa6b-116">Grâce à cette commande, les événements qui figurent dans le journal de sécurité des ordinateurs Server01 et Server02 sont assurés d'être conservés pendant au moins 7 jours.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-116">This command ensures that events in the Security log on the Server01 and Server02 computers are retained for at least 7 days.</span></span>

### <span data-ttu-id="7fa6b-117">Exemple 3 : modifier l’action de dépassement de capacité de tous les journaux des événements</span><span class="sxs-lookup"><span data-stu-id="7fa6b-117">Example 3: Change the overflow action of all event logs</span></span>

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

<span data-ttu-id="7fa6b-118">Cet exemple modifie l’action de dépassement de capacité de tous les journaux des événements sur l’ordinateur local en OverwriteOlder.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-118">This example changes the overflow action of all event logs on the local computer to OverwriteOlder.</span></span>

<span data-ttu-id="7fa6b-119">La première commande obtient le nom de tous les journaux présents sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-119">The first command gets the log names of all of the logs on the local computer.</span></span>
<span data-ttu-id="7fa6b-120">La deuxième commande définit l'action de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-120">The second command sets the overflow action.</span></span>
<span data-ttu-id="7fa6b-121">La troisième commande affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-121">The third command displays the results.</span></span>

## <span data-ttu-id="7fa6b-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7fa6b-122">PARAMETERS</span></span>

### <span data-ttu-id="7fa6b-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7fa6b-123">-ComputerName</span></span>
<span data-ttu-id="7fa6b-124">Spécifie les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-124">Specifies remote computers.</span></span>
<span data-ttu-id="7fa6b-125">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-125">The default is the local computer.</span></span>

<span data-ttu-id="7fa6b-126">Tapez le nom NetBIOS, une adresse IP (Internet Protocol) ou un nom de domaine complet (FQDN) d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="7fa6b-127">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-127">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="7fa6b-128">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-128">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="7fa6b-129">Vous pouvez utiliser le paramètre *ComputerName* de **Limit-EventLog** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-129">You can use the *ComputerName* parameter of **Limit-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa6b-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="7fa6b-130">-LogName</span></span>
<span data-ttu-id="7fa6b-131">Spécifie les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-131">Specifies the event logs.</span></span>
<span data-ttu-id="7fa6b-132">Entrez le nom du journal (la valeur de la propriété log et non le et non LogDisplayName) d’un ou plusieurs journaux des événements, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-132">Enter the log name (the value of the Log property; not the LogDisplayName) of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="7fa6b-133">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-133">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="7fa6b-134">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-134">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa6b-135">-MaximumSize</span><span class="sxs-lookup"><span data-stu-id="7fa6b-135">-MaximumSize</span></span>
<span data-ttu-id="7fa6b-136">Spécifie la taille maximale des journaux des événements (en octets).</span><span class="sxs-lookup"><span data-stu-id="7fa6b-136">Specifies the maximum size of the event logs in bytes.</span></span>
<span data-ttu-id="7fa6b-137">Entrez une valeur comprise entre 64 kilo-octets (Ko) et 4 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="7fa6b-137">Enter a value between 64 kilobytes (KB) and 4 gigabytes (GB).</span></span>
<span data-ttu-id="7fa6b-138">La valeur doit être divisible par 64 Ko (65 536).</span><span class="sxs-lookup"><span data-stu-id="7fa6b-138">The value must be divisible by 64 KB (65536).</span></span>

<span data-ttu-id="7fa6b-139">Ce paramètre spécifie la valeur de la propriété **MaximumKilobytes** de l’objet **System. Diagnostics. EventLog** qui représente un journal des événements classique.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-139">This parameter specifies the value of the **MaximumKilobytes** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa6b-140">-OverflowAction</span><span class="sxs-lookup"><span data-stu-id="7fa6b-140">-OverflowAction</span></span>
<span data-ttu-id="7fa6b-141">Spécifie l'action prévue lorsque le journal des événements atteint sa taille maximale.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-141">Specifies what happens when the event log reaches its maximum size.</span></span>

<span data-ttu-id="7fa6b-142">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="7fa6b-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7fa6b-143">DoNotOverwrite : les entrées existantes sont conservées et les nouvelles entrées sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-143">DoNotOverwrite:  Existing entries are retained and new entries are discarded.</span></span>
- <span data-ttu-id="7fa6b-144">OverwriteAsNeeded : chaque nouvelle entrée remplace l’entrée la plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-144">OverwriteAsNeeded:  Each new entry overwrites the oldest entry.</span></span>
- <span data-ttu-id="7fa6b-145">OverwriteOlder : les nouveaux événements remplacent les événements antérieurs à la valeur spécifiée par la propriété **MinimumRetentionDays** .</span><span class="sxs-lookup"><span data-stu-id="7fa6b-145">OverwriteOlder:  New events overwrite events older than the value specified by the **MinimumRetentionDays** property.</span></span> <span data-ttu-id="7fa6b-146">S’il n’y a pas d’événements antérieurs à spécifié par la valeur de la propriété **MinimumRetentionDays** , les nouveaux événements sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-146">If there are no events older than specified by the **MinimumRetentionDays** property value, new events are discarded.</span></span>

<span data-ttu-id="7fa6b-147">Ce paramètre spécifie la valeur de la propriété **OverflowAction** de l’objet **System. Diagnostics. EventLog** qui représente un journal des événements classique.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-147">This parameter specifies the value of the **OverflowAction** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa6b-148">-RetentionDays</span><span class="sxs-lookup"><span data-stu-id="7fa6b-148">-RetentionDays</span></span>
<span data-ttu-id="7fa6b-149">Spécifie le nombre minimal de jours pendant lesquels un événement doit rester dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-149">Specifies the minimum number of days that an event must remain in the event log.</span></span>

<span data-ttu-id="7fa6b-150">Ce paramètre spécifie la valeur de la propriété **MinimumRetentionDays** de l’objet **System. Diagnostics. EventLog** qui représente un journal des événements classique.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-150">This parameter specifies the value of the **MinimumRetentionDays** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa6b-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7fa6b-151">-Confirm</span></span>
<span data-ttu-id="7fa6b-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7fa6b-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7fa6b-153">-WhatIf</span></span>
<span data-ttu-id="7fa6b-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7fa6b-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7fa6b-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7fa6b-156">CommonParameters</span></span>
<span data-ttu-id="7fa6b-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7fa6b-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7fa6b-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7fa6b-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7fa6b-159">INPUTS</span></span>

### <span data-ttu-id="7fa6b-160">Aucun</span><span class="sxs-lookup"><span data-stu-id="7fa6b-160">None</span></span>
<span data-ttu-id="7fa6b-161">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-161">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="7fa6b-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7fa6b-162">OUTPUTS</span></span>

### <span data-ttu-id="7fa6b-163">Aucun</span><span class="sxs-lookup"><span data-stu-id="7fa6b-163">None</span></span>
<span data-ttu-id="7fa6b-164">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-164">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7fa6b-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7fa6b-165">NOTES</span></span>

* <span data-ttu-id="7fa6b-166">Pour utiliser cette applet de commande sur Windows Vista et les versions ultérieures de Windows, ouvrez Windows PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-166">To use this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="7fa6b-167">Cette applet de commande modifie les propriétés de l’objet **System. Diagnostics. EventLog** qui représente un journal des événements classique.</span><span class="sxs-lookup"><span data-stu-id="7fa6b-167">This cmdlet changes the properties of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>
<span data-ttu-id="7fa6b-168">Pour afficher les paramètres actuels des propriétés du journal des événements, tapez `Get-EventLog -List` .</span><span class="sxs-lookup"><span data-stu-id="7fa6b-168">To see the current settings of the event log properties, type `Get-EventLog -List`.</span></span>

*

## <span data-ttu-id="7fa6b-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7fa6b-169">RELATED LINKS</span></span>

[<span data-ttu-id="7fa6b-170">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa6b-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="7fa6b-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa6b-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="7fa6b-172">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa6b-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="7fa6b-173">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa6b-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="7fa6b-174">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa6b-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="7fa6b-175">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa6b-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="7fa6b-176">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa6b-176">Write-EventLog</span></span>](Write-EventLog.md)
