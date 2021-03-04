---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: af1c808b22a812700857e756136fd570fa0acc35
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685906"
---
# <span data-ttu-id="a81ac-103">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="a81ac-103">Clear-EventLog</span></span>

## <span data-ttu-id="a81ac-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a81ac-104">SYNOPSIS</span></span>
<span data-ttu-id="a81ac-105">Efface toutes les entrées des journaux des événements spécifiés sur les ordinateurs locaux ou distants.</span><span class="sxs-lookup"><span data-stu-id="a81ac-105">Clears all entries from specified event logs on the local or remote computers.</span></span>

## <span data-ttu-id="a81ac-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a81ac-106">SYNTAX</span></span>

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a81ac-107">Description</span><span class="sxs-lookup"><span data-stu-id="a81ac-107">DESCRIPTION</span></span>

<span data-ttu-id="a81ac-108">L' `Clear-EventLog` applet de commande supprime toutes les entrées des journaux des événements spécifiés sur l’ordinateur local ou sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="a81ac-108">The `Clear-EventLog` cmdlet deletes all of the entries from the specified event logs on the local computer or on remote computers.</span></span> <span data-ttu-id="a81ac-109">Pour utiliser `Clear-EventLog` , vous devez être membre du groupe Administrateurs sur l’ordinateur concerné.</span><span class="sxs-lookup"><span data-stu-id="a81ac-109">To use `Clear-EventLog`, you must be a member of the Administrators group on the affected computer.</span></span>

<span data-ttu-id="a81ac-110">Les applets de commande qui contiennent le nom **EventLog** (les applets de commande EventLog) fonctionnent uniquement sur les journaux des événements classiques.</span><span class="sxs-lookup"><span data-stu-id="a81ac-110">The cmdlets that contain the **EventLog** noun (the EventLog cmdlets) work only on classic event logs.</span></span> <span data-ttu-id="a81ac-111">Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures de Windows, utilisez l’applet de commande Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="a81ac-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="a81ac-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a81ac-112">EXAMPLES</span></span>

### <span data-ttu-id="a81ac-113">Exemple 1 : effacer des types de journaux des événements spécifiques de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="a81ac-113">Example 1: Clear specific event log types from the local computer</span></span>

```powershell
Clear-EventLog "Windows PowerShell"
```

<span data-ttu-id="a81ac-114">Cette commande efface les entrées du journal des événements Windows PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a81ac-114">This command clears the entries from the Windows PowerShell event log on the local computer.</span></span>

### <span data-ttu-id="a81ac-115">Exemple 2 : Effacer plusieurs types de journaux spécifiques des ordinateurs locaux et distants</span><span class="sxs-lookup"><span data-stu-id="a81ac-115">Example 2: Clear specific multiple log types from the local and remote computers</span></span>

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

<span data-ttu-id="a81ac-116">Cette commande efface toutes les entrées dans les journaux Microsoft Office Diagnostics (ODiag) et Microsoft Office sessions (OSession) sur l’ordinateur local et l’ordinateur distant SERVER02.</span><span class="sxs-lookup"><span data-stu-id="a81ac-116">This command clears all of the entries in the Microsoft Office Diagnostics (ODiag) and Microsoft Office Sessions (OSession) logs on the local computer and the Server02 remote computer.</span></span>

### <span data-ttu-id="a81ac-117">Exemple 3 : effacer tous les journaux sur les ordinateurs spécifiés, puis afficher la liste des journaux des événements</span><span class="sxs-lookup"><span data-stu-id="a81ac-117">Example 3: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
Clear-EventLog -LogName application, system -confirm
```

<span data-ttu-id="a81ac-118">Cette commande vous invite à confirmer la suppression des entrées dans les journaux des événements spécifiés.</span><span class="sxs-lookup"><span data-stu-id="a81ac-118">This command prompts you for confirmation before deleting the entries in the specified event logs.</span></span>

### <span data-ttu-id="a81ac-119">Exemple 4 : effacer tous les journaux sur les ordinateurs spécifiés, puis afficher la liste des journaux des événements</span><span class="sxs-lookup"><span data-stu-id="a81ac-119">Example 4: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

<span data-ttu-id="a81ac-120">Cette fonction efface tous les journaux des événements sur les ordinateurs spécifiés, puis affiche la liste des journaux des événements résultante.</span><span class="sxs-lookup"><span data-stu-id="a81ac-120">This function clears all event logs on the specified computers and then displays the resulting event log list.</span></span>

<span data-ttu-id="a81ac-121">Notez que quelques entrées ont été ajoutées au journal système et au journal de sécurité après l’effacement des journaux mais avant leur affichage.</span><span class="sxs-lookup"><span data-stu-id="a81ac-121">Notice that a few entries were added to the System and Security logs after the logs were cleared but before they were displayed.</span></span>

## <span data-ttu-id="a81ac-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a81ac-122">PARAMETERS</span></span>

### <span data-ttu-id="a81ac-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a81ac-123">-ComputerName</span></span>

<span data-ttu-id="a81ac-124">Spécifie un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a81ac-124">Specifies a remote computer.</span></span> <span data-ttu-id="a81ac-125">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a81ac-125">The default is the local computer.</span></span>

<span data-ttu-id="a81ac-126">Tapez le nom NetBIOS, une adresse IP ou le nom de domaine complet d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a81ac-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="a81ac-127">Pour spécifier l'ordinateur local, tapez le nom de l'ordinateur, un point (.) ou « localhost ».</span><span class="sxs-lookup"><span data-stu-id="a81ac-127">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="a81ac-128">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a81ac-128">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="a81ac-129">Vous pouvez utiliser le paramètre **ComputerName** de `Get-EventLog` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="a81ac-129">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a81ac-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="a81ac-130">-LogName</span></span>

<span data-ttu-id="a81ac-131">Spécifie les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="a81ac-131">Specifies the event logs.</span></span> <span data-ttu-id="a81ac-132">Entrez le nom du journal (la valeur de la propriété **log** n’est pas **et non LogDisplayName**) d’un ou plusieurs journaux des événements, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="a81ac-132">Enter the log name (the value of the **Log** property not the **LogDisplayName**) of one or more event logs, separated by commas.</span></span> <span data-ttu-id="a81ac-133">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="a81ac-133">Wildcard characters are not permitted.</span></span> <span data-ttu-id="a81ac-134">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="a81ac-134">This parameter is required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a81ac-135">Ce paramètre est supposé accepter les valeurs du pipeline par nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="a81ac-135">This parameter is supposed to accept values from the pipeline by property name.</span></span> <span data-ttu-id="a81ac-136">Toutefois, il existe un bogue qui empêche cela de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="a81ac-136">However, there is a bug that prevents this from working.</span></span> <span data-ttu-id="a81ac-137">Vous devez passer une valeur directement à l’aide du paramètre.</span><span class="sxs-lookup"><span data-stu-id="a81ac-137">You must pass a value using the parameter directly.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a81ac-138">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a81ac-138">-Confirm</span></span>

<span data-ttu-id="a81ac-139">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a81ac-139">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a81ac-140">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a81ac-140">-WhatIf</span></span>

<span data-ttu-id="a81ac-141">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a81ac-141">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a81ac-142">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a81ac-142">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a81ac-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a81ac-143">CommonParameters</span></span>

<span data-ttu-id="a81ac-144">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a81ac-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a81ac-145">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a81ac-145">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a81ac-146">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a81ac-146">INPUTS</span></span>

### <span data-ttu-id="a81ac-147">Aucun</span><span class="sxs-lookup"><span data-stu-id="a81ac-147">None</span></span>

<span data-ttu-id="a81ac-148">Vous ne pouvez pas diriger d’objets vers `Clear-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="a81ac-148">You cannot pipe objects to `Clear-EventLog`.</span></span>

## <span data-ttu-id="a81ac-149">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a81ac-149">OUTPUTS</span></span>

### <span data-ttu-id="a81ac-150">Aucun</span><span class="sxs-lookup"><span data-stu-id="a81ac-150">None</span></span>

<span data-ttu-id="a81ac-151">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a81ac-151">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a81ac-152">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a81ac-152">NOTES</span></span>

- <span data-ttu-id="a81ac-153">Pour utiliser `Clear-EventLog` sur Windows Vista et les versions ultérieures de Windows, démarrez Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="a81ac-153">To use `Clear-EventLog` on Windows Vista and later versions of Windows, start Windows PowerShell with the "Run as administrator" option.</span></span>

## <span data-ttu-id="a81ac-154">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a81ac-154">RELATED LINKS</span></span>

[<span data-ttu-id="a81ac-155">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="a81ac-155">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="a81ac-156">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="a81ac-156">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="a81ac-157">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="a81ac-157">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="a81ac-158">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="a81ac-158">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="a81ac-159">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="a81ac-159">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="a81ac-160">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="a81ac-160">Write-EventLog</span></span>](Write-EventLog.md)
