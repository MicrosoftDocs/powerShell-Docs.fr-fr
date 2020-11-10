---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 98bd72901339d040748fc0d99b14bc1404ea1465
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388312"
---
# <span data-ttu-id="2450c-103">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="2450c-103">Debug-Process</span></span>

## <span data-ttu-id="2450c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2450c-104">SYNOPSIS</span></span>
<span data-ttu-id="2450c-105">Débogue un ou plusieurs processus en cours d'exécution sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2450c-105">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="2450c-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="2450c-106">SYNTAX</span></span>

### <span data-ttu-id="2450c-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2450c-107">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2450c-108">Id</span><span class="sxs-lookup"><span data-stu-id="2450c-108">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2450c-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="2450c-109">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2450c-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2450c-110">DESCRIPTION</span></span>

<span data-ttu-id="2450c-111">L' `Debug-Process` applet de commande joint un débogueur à un ou plusieurs processus en cours d’exécution sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2450c-111">The `Debug-Process` cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="2450c-112">Vous pouvez spécifier les processus en fonction de leur nom de processus ou de leur ID de processus (PID), ou vous pouvez diriger les objets de processus vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2450c-112">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="2450c-113">Cette applet de commande attache le débogueur actuellement inscrit pour le processus.</span><span class="sxs-lookup"><span data-stu-id="2450c-113">This cmdlet attaches the debugger that is currently registered for the process.</span></span> <span data-ttu-id="2450c-114">Avant d'utiliser cette applet de commande, vérifiez qu'un débogueur est téléchargé et correctement configuré.</span><span class="sxs-lookup"><span data-stu-id="2450c-114">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="2450c-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2450c-115">EXAMPLES</span></span>

### <span data-ttu-id="2450c-116">Exemple 1 : attacher un débogueur à un processus sur l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="2450c-116">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="2450c-117">Cette commande joint un débogueur au processus PowerShell sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2450c-117">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="2450c-118">Exemple 2 : attacher un débogueur à tous les processus qui commencent par la chaîne spécifiée</span><span class="sxs-lookup"><span data-stu-id="2450c-118">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="2450c-119">Cette commande joint un débogueur à tous les processus dont le nom commence par SQL.</span><span class="sxs-lookup"><span data-stu-id="2450c-119">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="2450c-120">Exemple 3 : attacher un débogueur à plusieurs processus</span><span class="sxs-lookup"><span data-stu-id="2450c-120">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="2450c-121">Cette commande joint un débogueur aux processus Winlogon, Explorer et Outlook.</span><span class="sxs-lookup"><span data-stu-id="2450c-121">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="2450c-122">Exemple 4 : attacher un débogueur à plusieurs ID de processus</span><span class="sxs-lookup"><span data-stu-id="2450c-122">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="2450c-123">Cette commande joint un débogueur aux processus dont les identificateurs sont 1132 et 2028.</span><span class="sxs-lookup"><span data-stu-id="2450c-123">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="2450c-124">Exemple 5 : utiliser Get-Process pour obtenir un processus, puis y attacher un débogueur</span><span class="sxs-lookup"><span data-stu-id="2450c-124">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="2450c-125">Cette commande joint un débogueur aux processus PowerShell sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2450c-125">This command attaches a debugger to the PowerShell processes on the computer.</span></span> <span data-ttu-id="2450c-126">Elle utilise l' `Get-Process` applet de commande pour obtenir les processus PowerShell sur l’ordinateur, et elle utilise un opérateur de pipeline ( `|` ) pour envoyer les processus à l’applet de commande `Debug-Process` .</span><span class="sxs-lookup"><span data-stu-id="2450c-126">It uses the `Get-Process` cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (`|`) to send the processes to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="2450c-127">Pour spécifier un processus PowerShell particulier, utilisez le paramètre ID de `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="2450c-127">To specify a particular PowerShell process, use the ID parameter of `Get-Process`.</span></span>

### <span data-ttu-id="2450c-128">Exemple 6 : attacher un débogueur à un processus en cours sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="2450c-128">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="2450c-129">Cette commande joint un débogueur aux processus PowerShell actifs sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2450c-129">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="2450c-130">La commande utilise la `$PID` variable automatique, qui contient l’ID de processus du processus PowerShell en cours.</span><span class="sxs-lookup"><span data-stu-id="2450c-130">The command uses the `$PID` automatic variable, which contains the process ID of the current PowerShell process.</span></span> <span data-ttu-id="2450c-131">Ensuite, il utilise un opérateur de pipeline ( `|` ) pour envoyer l’ID de processus à l’applet de commande `Debug-Process` .</span><span class="sxs-lookup"><span data-stu-id="2450c-131">Then, it uses a pipeline operator (`|`) to send the process ID to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="2450c-132">Pour plus d’informations sur la `$PID` variable automatique, consultez about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="2450c-132">For more information about the `$PID` automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="2450c-133">Exemple 7 : attacher un débogueur au processus spécifié sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="2450c-133">Example 7: Attach a debugger to the specified process on multiple computers</span></span>

```
PS C:\> Get-Process -ComputerName "Server01", "Server02" -Name "MyApp" | Debug-Process
```

<span data-ttu-id="2450c-134">Cette commande joint un débogueur aux processus MyApp sur les ordinateurs Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="2450c-134">This command attaches a debugger to the MyApp processes on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="2450c-135">La commande utilise l' `Get-Process` applet de commande pour récupérer les processus MyApp sur les ordinateurs SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="2450c-135">The command uses the `Get-Process` cmdlet to get the MyApp processes on the Server01 and Server02 computers.</span></span> <span data-ttu-id="2450c-136">Elle utilise un opérateur de pipeline pour envoyer les processus à l’applet de commande `Debug-Process` , qui attache les débogueurs.</span><span class="sxs-lookup"><span data-stu-id="2450c-136">It uses a pipeline operator to send the processes to the `Debug-Process` cmdlet, which attaches the debuggers.</span></span>

### <span data-ttu-id="2450c-137">Exemple 8 : attacher un débogueur à un processus qui utilise le paramètre InputObject</span><span class="sxs-lookup"><span data-stu-id="2450c-137">Example 8: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="2450c-138">Cette commande joint un débogueur aux processus PowerShell sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2450c-138">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="2450c-139">La première commande utilise l' `Get-Process` applet de commande pour récupérer les processus PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2450c-139">The first command uses the `Get-Process` cmdlet to get the PowerShell processes on the computer.</span></span> <span data-ttu-id="2450c-140">Elle enregistre l’objet processus résultant dans la variable nommée `$P` .</span><span class="sxs-lookup"><span data-stu-id="2450c-140">It saves the resulting process object in the variable named `$P`.</span></span>

<span data-ttu-id="2450c-141">La deuxième commande utilise le paramètre **InputObject** de l' `Debug-Process` applet de commande pour envoyer l’objet processus dans la `$P` variable.</span><span class="sxs-lookup"><span data-stu-id="2450c-141">The second command uses the **InputObject** parameter of the `Debug-Process` cmdlet to submit the process object in the `$P` variable.</span></span>

## <span data-ttu-id="2450c-142">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="2450c-142">PARAMETERS</span></span>

### <span data-ttu-id="2450c-143">-Id</span><span class="sxs-lookup"><span data-stu-id="2450c-143">-Id</span></span>

<span data-ttu-id="2450c-144">Spécifie l'identificateur des processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="2450c-144">Specifies the process IDs of the processes to be debugged.</span></span> <span data-ttu-id="2450c-145">Le nom du paramètre **ID** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="2450c-145">The **Id** parameter name is optional.</span></span>

<span data-ttu-id="2450c-146">Pour Rechercher l’ID de processus d’un processus, tapez `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="2450c-146">To find the process ID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2450c-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2450c-147">-InputObject</span></span>

<span data-ttu-id="2450c-148">Spécifie les objets processus qui représentent les processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="2450c-148">Specifies the process objects that represent processes to be debugged.</span></span> <span data-ttu-id="2450c-149">Entrez une variable qui contient les objets processus ou une commande qui obtient les objets processus, tels que l' `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2450c-149">Enter a variable that contains the process objects or a command that gets the process objects, such as the `Get-Process` cmdlet.</span></span> <span data-ttu-id="2450c-150">Vous pouvez également diriger les objets de processus vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2450c-150">You can also pipe process objects to this cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2450c-151">-Name</span><span class="sxs-lookup"><span data-stu-id="2450c-151">-Name</span></span>

<span data-ttu-id="2450c-152">Spécifie le nom des processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="2450c-152">Specifies the names of the processes to be debugged.</span></span> <span data-ttu-id="2450c-153">S’il existe plusieurs processus portant le même nom, cette applet de commande joint un débogueur à tous les processus portant ce nom.</span><span class="sxs-lookup"><span data-stu-id="2450c-153">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span> <span data-ttu-id="2450c-154">Le paramètre **Name** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="2450c-154">The **Name** parameter is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2450c-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2450c-155">-Confirm</span></span>

<span data-ttu-id="2450c-156">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2450c-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2450c-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2450c-157">-WhatIf</span></span>

<span data-ttu-id="2450c-158">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2450c-158">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2450c-159">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2450c-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2450c-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2450c-160">CommonParameters</span></span>

<span data-ttu-id="2450c-161">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2450c-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2450c-162">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2450c-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2450c-163">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2450c-163">INPUTS</span></span>

### <span data-ttu-id="2450c-164">System. Int32, System. Diagnostics. Process, System. String</span><span class="sxs-lookup"><span data-stu-id="2450c-164">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="2450c-165">Vous pouvez diriger un ID de processus (Int32), un objet de processus (System. Diagnostics. Process) ou un nom de processus (String) vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2450c-165">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="2450c-166">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2450c-166">OUTPUTS</span></span>

### <span data-ttu-id="2450c-167">Aucun</span><span class="sxs-lookup"><span data-stu-id="2450c-167">None</span></span>

<span data-ttu-id="2450c-168">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="2450c-168">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2450c-169">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2450c-169">NOTES</span></span>

<span data-ttu-id="2450c-170">Cette applet de commande utilise la méthode AttachDebugger de la classe WMI (Windows Management Instrumentation) Win32_Process.</span><span class="sxs-lookup"><span data-stu-id="2450c-170">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="2450c-171">Pour plus d’informations sur cette méthode, consultez la [méthode AttachDebugger](https://go.microsoft.com/fwlink/?LinkId=143640) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="2450c-171">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="2450c-172">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2450c-172">RELATED LINKS</span></span>

[<span data-ttu-id="2450c-173">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="2450c-173">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="2450c-174">Get-Process</span><span class="sxs-lookup"><span data-stu-id="2450c-174">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="2450c-175">Start-Process</span><span class="sxs-lookup"><span data-stu-id="2450c-175">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="2450c-176">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="2450c-176">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="2450c-177">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="2450c-177">Wait-Process</span></span>](Wait-Process.md)
