---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: fd1da10b3a64e0fe9b43dfec1289eebaf31ed739
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204217"
---
# <span data-ttu-id="3dee4-103">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="3dee4-103">Debug-Runspace</span></span>

## <span data-ttu-id="3dee4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3dee4-104">SYNOPSIS</span></span>
<span data-ttu-id="3dee4-105">Démarre une session de débogage interactive avec une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3dee4-105">Starts an interactive debugging session with a runspace.</span></span>

## <span data-ttu-id="3dee4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3dee4-106">SYNTAX</span></span>

### <span data-ttu-id="3dee4-107">RunspaceParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3dee4-107">RunspaceParameterSet (Default)</span></span>

```
Debug-Runspace [-Runspace] <Runspace> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3dee4-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="3dee4-108">NameParameterSet</span></span>

```
Debug-Runspace [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3dee4-109">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3dee4-109">IdParameterSet</span></span>

```
Debug-Runspace [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3dee4-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3dee4-110">InstanceIdParameterSet</span></span>

```
Debug-Runspace [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3dee4-111">Description</span><span class="sxs-lookup"><span data-stu-id="3dee4-111">DESCRIPTION</span></span>

<span data-ttu-id="3dee4-112">L' `Debug-Runspace` applet de commande démarre une session de débogage interactive avec une instance d’exécution active locale ou distante.</span><span class="sxs-lookup"><span data-stu-id="3dee4-112">The `Debug-Runspace` cmdlet starts an interactive debugging session with a local or remote active runspace.</span></span> <span data-ttu-id="3dee4-113">Vous pouvez trouver une instance d’exécution que vous souhaitez déboguer en exécutant en premier `Get-Process` pour rechercher les processus associés à PowerShell, puis `Enter-PSHostProcess` l’ID de processus spécifié dans le paramètre **ID** pour l’attacher au processus, puis `Get-Runspace` répertorier les instances d’exécution dans le processus hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3dee4-113">You can find a runspace that you want to debug by first running `Get-Process` to find processes associated with PowerShell, then `Enter-PSHostProcess` with the process ID specified in the **Id** parameter to attach to the process, and then `Get-Runspace` to list runspaces within the PowerShell host process.</span></span>

<span data-ttu-id="3dee4-114">Après avoir sélectionné une instance d’exécution à déboguer, si l’instance d’exécution exécute actuellement une commande ou un script, ou si le script s’est arrêté à un point d’arrêt, PowerShell ouvre une session du débogueur distant pour l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3dee4-114">After you have selected a runspace to debug, if the runspace is currently running a command or script, or if the script has stopped at a breakpoint, PowerShell opens a remote debugger session for the runspace.</span></span> <span data-ttu-id="3dee4-115">Vous pouvez déboguer le script de l’instance d’exécution de la même façon que les scripts de session à distance sont débogués.</span><span class="sxs-lookup"><span data-stu-id="3dee4-115">You can debug the runspace script in the same way remote session scripts are debugged.</span></span>

<span data-ttu-id="3dee4-116">Vous pouvez uniquement effectuer un attachement à un processus hôte PowerShell Si vous êtes un administrateur sur l’ordinateur qui exécute le processus, ou si vous exécutez le script que vous souhaitez déboguer.</span><span class="sxs-lookup"><span data-stu-id="3dee4-116">You can only attach to a PowerShell host process if you are an administrator on the computer that is running the process, or you are running the script that you want to debug.</span></span> <span data-ttu-id="3dee4-117">En outre, vous ne pouvez pas entrer dans le processus hôte qui exécute la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="3dee4-117">Also, you cannot enter the host process that is running the current PowerShell session.</span></span> <span data-ttu-id="3dee4-118">Vous pouvez uniquement entrer un processus hôte qui exécute une autre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3dee4-118">You can only enter a host process that is running a different PowerShell session.</span></span>

## <span data-ttu-id="3dee4-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3dee4-119">EXAMPLES</span></span>

### <span data-ttu-id="3dee4-120">Exemple 1 : déboguer une instance d’exécution distante</span><span class="sxs-lookup"><span data-stu-id="3dee4-120">Example 1: Debug a remote runspace</span></span>

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

<span data-ttu-id="3dee4-121">Dans cet exemple, vous déboguez une instance d’exécution qui est ouverte sur un ordinateur distant, WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="3dee4-121">In this example, you debug a runspace that is open on a remote computer, WS10TestServer.</span></span> <span data-ttu-id="3dee4-122">Sur la première ligne de la commande, vous exécutez `Get-Process` sur l’ordinateur distant et filtrez les processus de l’hôte Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3dee4-122">In the first line of the command, you run `Get-Process` on the remote computer, and filter for Windows PowerShell host processes.</span></span> <span data-ttu-id="3dee4-123">Dans cet exemple, vous souhaitez déboguer le processus ID 1152, le processus hôte Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3dee4-123">In this example, you want to debug process ID 1152, the Windows PowerShell ISE host process.</span></span>

<span data-ttu-id="3dee4-124">Dans la deuxième commande, vous exécutez `Enter-PSSession` pour ouvrir une session à distance sur WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="3dee4-124">In the second command, you run `Enter-PSSession` to open a remote session on WS10TestServer.</span></span> <span data-ttu-id="3dee4-125">Dans la troisième commande, vous attachez au processus hôte Windows PowerShell ISE s’exécutant sur le serveur distant en exécutant `Enter-PSHostProcess` et en spécifiant l’ID du processus hôte que vous avez obtenu dans la première commande, 1152.</span><span class="sxs-lookup"><span data-stu-id="3dee4-125">In the third command, you attach to the Windows PowerShell ISE host process running on the remote server by running `Enter-PSHostProcess`, and specifying the ID of the host process that you obtained in the first command, 1152.</span></span>

<span data-ttu-id="3dee4-126">Dans la quatrième commande, vous répertoriez les instances d’exécution disponibles pour l’ID de processus 1152 en exécutant `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="3dee4-126">In the fourth command, you list available runspaces for process ID 1152 by running `Get-Runspace`.</span></span>
<span data-ttu-id="3dee4-127">Vous notez le numéro d’ID de l’instance d’exécution occupée ; Il exécute un script que vous souhaitez déboguer.</span><span class="sxs-lookup"><span data-stu-id="3dee4-127">You note the ID number of the Busy runspace; it is running a script that you want to debug.</span></span>

<span data-ttu-id="3dee4-128">Dans la dernière commande, vous démarrez le débogage d’une instance d’exécution ouverte qui exécute un script, TestWFVar1.ps1, en exécutant `Debug-Runspace` et en identifiant l’instance d’exécution par son ID, 2, en ajoutant le paramètre **ID** .</span><span class="sxs-lookup"><span data-stu-id="3dee4-128">In the last command, you start debugging an opened runspace that is running a script, TestWFVar1.ps1, by running `Debug-Runspace`, and identifying the runspace by its ID, 2, by adding the **Id** parameter.</span></span> <span data-ttu-id="3dee4-129">Étant donné qu’il y a un point d’arrêt dans le script, le débogueur s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="3dee4-129">Because there's a breakpoint in the script, the debugger opens.</span></span>

## <span data-ttu-id="3dee4-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3dee4-130">PARAMETERS</span></span>

### <span data-ttu-id="3dee4-131">-Id</span><span class="sxs-lookup"><span data-stu-id="3dee4-131">-Id</span></span>

<span data-ttu-id="3dee4-132">Spécifie le numéro d’ID d’une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3dee4-132">Specifies the ID number of a runspace.</span></span> <span data-ttu-id="3dee4-133">Vous pouvez exécuter `Get-Runspace` pour afficher les ID d’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3dee4-133">You can run `Get-Runspace` to show runspace IDs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3dee4-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="3dee4-134">-InstanceId</span></span>

<span data-ttu-id="3dee4-135">Spécifie une instance d’exécution par son ID d’instance, un GUID que vous pouvez afficher en exécutant `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="3dee4-135">Specifies a runspace by its instance ID, a GUID that you can show by running `Get-Runspace`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3dee4-136">-Name</span><span class="sxs-lookup"><span data-stu-id="3dee4-136">-Name</span></span>

<span data-ttu-id="3dee4-137">Spécifie une instance d’exécution par son nom.</span><span class="sxs-lookup"><span data-stu-id="3dee4-137">Specifies a runspace by its name.</span></span> <span data-ttu-id="3dee4-138">Vous pouvez exécuter `Get-Runspace` pour afficher les noms de instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3dee4-138">You can run `Get-Runspace` to show the names of runspaces.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3dee4-139">-Instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="3dee4-139">-Runspace</span></span>

<span data-ttu-id="3dee4-140">Spécifie un objet d’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3dee4-140">Specifies a runspace object.</span></span> <span data-ttu-id="3dee4-141">La façon la plus simple de fournir une valeur pour ce paramètre consiste à spécifier une variable qui contient les résultats d’une commande filtrée `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="3dee4-141">The simplest way to provide a value for this parameter is to specify a variable that contains the results of a filtered `Get-Runspace` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3dee4-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3dee4-142">-Confirm</span></span>

<span data-ttu-id="3dee4-143">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3dee4-143">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3dee4-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3dee4-144">-WhatIf</span></span>

<span data-ttu-id="3dee4-145">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3dee4-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3dee4-146">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="3dee4-146">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3dee4-147">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="3dee4-147">-BreakAll</span></span>

<span data-ttu-id="3dee4-148">{{Renseigner la description BreakAll}}</span><span class="sxs-lookup"><span data-stu-id="3dee4-148">{{ Fill BreakAll Description }}</span></span>

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

### <span data-ttu-id="3dee4-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3dee4-149">CommonParameters</span></span>

<span data-ttu-id="3dee4-150">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3dee4-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3dee4-151">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3dee4-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3dee4-152">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3dee4-152">INPUTS</span></span>

### <span data-ttu-id="3dee4-153">System. Management. Automation. instances d’exécution. Runspace</span><span class="sxs-lookup"><span data-stu-id="3dee4-153">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="3dee4-154">Vous pouvez diriger les résultats d’une `Get-Runspace` commande vers **Debug-Runspace.**</span><span class="sxs-lookup"><span data-stu-id="3dee4-154">You can pipe the results of a `Get-Runspace` command to **Debug-Runspace.**</span></span>

## <span data-ttu-id="3dee4-155">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3dee4-155">OUTPUTS</span></span>

## <span data-ttu-id="3dee4-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3dee4-156">NOTES</span></span>

<span data-ttu-id="3dee4-157">`Debug-Runspace` fonctionne sur les instances d’exécution qui sont à l’état ouvert.</span><span class="sxs-lookup"><span data-stu-id="3dee4-157">`Debug-Runspace` works on runspaces that are in the Opened state.</span></span> <span data-ttu-id="3dee4-158">Si l’état d’une instance d’exécution passe de ouvert à un autre État, cette instance d’exécution est automatiquement supprimée de la liste en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3dee4-158">If a runspace state changes from Opened to another state, that runspace is automatically removed from the running list.</span></span> <span data-ttu-id="3dee4-159">Une instance d’exécution est ajoutée à la liste en cours d’exécution uniquement si elle répond aux critères suivants.</span><span class="sxs-lookup"><span data-stu-id="3dee4-159">A runspace is added to the running list only if it meets the following criteria.</span></span>

- <span data-ttu-id="3dee4-160">S’il provient de Invoke-Command ; autrement dit, il a un `Invoke-Command` ID de GUID.</span><span class="sxs-lookup"><span data-stu-id="3dee4-160">If it is coming from Invoke-Command; that is, it has an `Invoke-Command` GUID ID.</span></span>
- <span data-ttu-id="3dee4-161">S’il provient de `Debug-Runspace` ; autrement dit, il a un `Debug-Runspace` ID de GUID.</span><span class="sxs-lookup"><span data-stu-id="3dee4-161">If it is coming from `Debug-Runspace`; that is, it has a `Debug-Runspace` GUID ID.</span></span>
- <span data-ttu-id="3dee4-162">S’il provient d’un workflow PowerShell et que son ID de tâche de flux de travail est le même que l’ID de tâche de workflow du débogueur actif actuel.</span><span class="sxs-lookup"><span data-stu-id="3dee4-162">If it is coming from a PowerShell workflow, and its workflow job ID is the same as the current active debugger workflow job ID.</span></span>

## <span data-ttu-id="3dee4-163">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3dee4-163">RELATED LINKS</span></span>

[<span data-ttu-id="3dee4-164">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="3dee4-164">about_Debuggers</span></span>](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[<span data-ttu-id="3dee4-165">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="3dee4-165">Debug-Job</span></span>](../Microsoft.PowerShell.Core/Debug-Job.md)

[<span data-ttu-id="3dee4-166">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="3dee4-166">Get-Runspace</span></span>](Get-Runspace.md)

[<span data-ttu-id="3dee4-167">Get-Process</span><span class="sxs-lookup"><span data-stu-id="3dee4-167">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="3dee4-168">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="3dee4-168">Enter-PSHostProcess</span></span>](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[<span data-ttu-id="3dee4-169">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="3dee4-169">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

