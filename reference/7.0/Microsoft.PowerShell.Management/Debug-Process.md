---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 9d2b9ce8d9aa0a1e75c0af0f2ed57aca41ec7791
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201129"
---
# <span data-ttu-id="eafb1-103">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="eafb1-103">Debug-Process</span></span>

## <span data-ttu-id="eafb1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="eafb1-104">SYNOPSIS</span></span>
<span data-ttu-id="eafb1-105">Débogue un ou plusieurs processus en cours d'exécution sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eafb1-105">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="eafb1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eafb1-106">SYNTAX</span></span>

### <span data-ttu-id="eafb1-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="eafb1-107">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="eafb1-108">Id</span><span class="sxs-lookup"><span data-stu-id="eafb1-108">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="eafb1-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="eafb1-109">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="eafb1-110">Description</span><span class="sxs-lookup"><span data-stu-id="eafb1-110">DESCRIPTION</span></span>

<span data-ttu-id="eafb1-111">L’applet de commande **Debug-Process** joint un débogueur à un ou plusieurs processus en cours d’exécution sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eafb1-111">The **Debug-Process** cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="eafb1-112">Vous pouvez spécifier les processus en fonction de leur nom de processus ou de leur ID de processus (PID), ou vous pouvez diriger les objets de processus vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eafb1-112">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="eafb1-113">Cette applet de commande attache le débogueur actuellement inscrit pour le processus.</span><span class="sxs-lookup"><span data-stu-id="eafb1-113">This cmdlet attaches the debugger that is currently registered for the process.</span></span>
<span data-ttu-id="eafb1-114">Avant d'utiliser cette applet de commande, vérifiez qu'un débogueur est téléchargé et correctement configuré.</span><span class="sxs-lookup"><span data-stu-id="eafb1-114">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="eafb1-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="eafb1-115">EXAMPLES</span></span>

### <span data-ttu-id="eafb1-116">Exemple 1 : attacher un débogueur à un processus sur l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="eafb1-116">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="eafb1-117">Cette commande joint un débogueur au processus PowerShell sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eafb1-117">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="eafb1-118">Exemple 2 : attacher un débogueur à tous les processus qui commencent par la chaîne spécifiée</span><span class="sxs-lookup"><span data-stu-id="eafb1-118">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="eafb1-119">Cette commande joint un débogueur à tous les processus dont le nom commence par SQL.</span><span class="sxs-lookup"><span data-stu-id="eafb1-119">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="eafb1-120">Exemple 3 : attacher un débogueur à plusieurs processus</span><span class="sxs-lookup"><span data-stu-id="eafb1-120">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="eafb1-121">Cette commande joint un débogueur aux processus Winlogon, Explorer et Outlook.</span><span class="sxs-lookup"><span data-stu-id="eafb1-121">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="eafb1-122">Exemple 4 : attacher un débogueur à plusieurs ID de processus</span><span class="sxs-lookup"><span data-stu-id="eafb1-122">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="eafb1-123">Cette commande joint un débogueur aux processus dont les identificateurs sont 1132 et 2028.</span><span class="sxs-lookup"><span data-stu-id="eafb1-123">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="eafb1-124">Exemple 5 : utiliser Get-Process pour obtenir un processus, puis y attacher un débogueur</span><span class="sxs-lookup"><span data-stu-id="eafb1-124">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="eafb1-125">Cette commande joint un débogueur aux processus PowerShell sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eafb1-125">This command attaches a debugger to the PowerShell processes on the computer.</span></span>
<span data-ttu-id="eafb1-126">Elle utilise l’applet de commande **obtenir-process** pour obtenir les processus PowerShell sur l’ordinateur, et elle utilise un opérateur de pipeline (|) pour envoyer les processus à l’applet de commande **Debug-Process** .</span><span class="sxs-lookup"><span data-stu-id="eafb1-126">It uses the **Get-Process** cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (|) to send the processes to the **Debug-Process** cmdlet.</span></span>

<span data-ttu-id="eafb1-127">Pour spécifier un processus PowerShell particulier, utilisez le paramètre ID de la **méthode « obtenir un processus »** .</span><span class="sxs-lookup"><span data-stu-id="eafb1-127">To specify a particular PowerShell process, use the ID parameter of **Get-Process** .</span></span>

### <span data-ttu-id="eafb1-128">Exemple 6 : attacher un débogueur à un processus en cours sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="eafb1-128">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="eafb1-129">Cette commande joint un débogueur aux processus PowerShell actifs sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eafb1-129">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="eafb1-130">La commande utilise la variable automatique $PID, qui contient l’ID du processus PowerShell en cours.</span><span class="sxs-lookup"><span data-stu-id="eafb1-130">The command uses the $PID automatic variable, which contains the process ID of the current PowerShell process.</span></span>
<span data-ttu-id="eafb1-131">Ensuite, il utilise un opérateur de pipeline (|) pour envoyer l’ID de processus à l’applet de commande **Debug-Process** .</span><span class="sxs-lookup"><span data-stu-id="eafb1-131">Then, it uses a pipeline operator (|) to send the process ID to the **Debug-Process** cmdlet.</span></span>

<span data-ttu-id="eafb1-132">Pour plus d’informations sur la variable automatique $PID, consultez about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="eafb1-132">For more information about the $PID automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="eafb1-133">Exemple 7 : attacher un débogueur à un processus qui utilise le paramètre InputObject</span><span class="sxs-lookup"><span data-stu-id="eafb1-133">Example 7: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="eafb1-134">Cette commande joint un débogueur aux processus PowerShell sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eafb1-134">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="eafb1-135">La première commande utilise l’applet de commande **« obten-process »** pour récupérer les processus PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eafb1-135">The first command uses the **Get-Process** cmdlet to get the PowerShell processes on the computer.</span></span>
<span data-ttu-id="eafb1-136">Elle enregistre l’objet processus résultant dans la variable nommée $P.</span><span class="sxs-lookup"><span data-stu-id="eafb1-136">It saves the resulting process object in the variable named $P.</span></span>

<span data-ttu-id="eafb1-137">La deuxième commande utilise le paramètre *InputObject* de l’applet de commande **Debug-Process** pour envoyer l’objet processus dans la variable $P.</span><span class="sxs-lookup"><span data-stu-id="eafb1-137">The second command uses the *InputObject* parameter of the **Debug-Process** cmdlet to submit the process object in the $P variable.</span></span>

## <span data-ttu-id="eafb1-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eafb1-138">PARAMETERS</span></span>

### <span data-ttu-id="eafb1-139">-Id</span><span class="sxs-lookup"><span data-stu-id="eafb1-139">-Id</span></span>

<span data-ttu-id="eafb1-140">Spécifie l'identificateur des processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="eafb1-140">Specifies the process IDs of the processes to be debugged.</span></span>
<span data-ttu-id="eafb1-141">Le nom du paramètre *ID* est facultatif.</span><span class="sxs-lookup"><span data-stu-id="eafb1-141">The *Id* parameter name is optional.</span></span>

<span data-ttu-id="eafb1-142">Pour Rechercher l’ID de processus d’un processus, tapez `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="eafb1-142">To find the process ID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="eafb1-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="eafb1-143">-InputObject</span></span>

<span data-ttu-id="eafb1-144">Spécifie les objets processus qui représentent les processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="eafb1-144">Specifies the process objects that represent processes to be debugged.</span></span>
<span data-ttu-id="eafb1-145">Entrez une variable qui contient les objets processus ou une commande qui obtient les objets processus, tels que l’applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="eafb1-145">Enter a variable that contains the process objects or a command that gets the process objects, such as the Get-Process cmdlet.</span></span>
<span data-ttu-id="eafb1-146">Vous pouvez également diriger les objets de processus vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eafb1-146">You can also pipe process objects to this cmdlet.</span></span>

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

### <span data-ttu-id="eafb1-147">-Name</span><span class="sxs-lookup"><span data-stu-id="eafb1-147">-Name</span></span>

<span data-ttu-id="eafb1-148">Spécifie le nom des processus à déboguer.</span><span class="sxs-lookup"><span data-stu-id="eafb1-148">Specifies the names of the processes to be debugged.</span></span>
<span data-ttu-id="eafb1-149">S’il existe plusieurs processus portant le même nom, cette applet de commande joint un débogueur à tous les processus portant ce nom.</span><span class="sxs-lookup"><span data-stu-id="eafb1-149">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span>
<span data-ttu-id="eafb1-150">Le paramètre *Name* est facultatif.</span><span class="sxs-lookup"><span data-stu-id="eafb1-150">The *Name* parameter is optional.</span></span>

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

### <span data-ttu-id="eafb1-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="eafb1-151">-Confirm</span></span>

<span data-ttu-id="eafb1-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eafb1-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="eafb1-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="eafb1-153">-WhatIf</span></span>

<span data-ttu-id="eafb1-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eafb1-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="eafb1-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="eafb1-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="eafb1-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eafb1-156">CommonParameters</span></span>

<span data-ttu-id="eafb1-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eafb1-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eafb1-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eafb1-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eafb1-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="eafb1-159">INPUTS</span></span>

### <span data-ttu-id="eafb1-160">System. Int32, System. Diagnostics. Process, System. String</span><span class="sxs-lookup"><span data-stu-id="eafb1-160">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="eafb1-161">Vous pouvez diriger un ID de processus (Int32), un objet de processus (System. Diagnostics. Process) ou un nom de processus (String) vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eafb1-161">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="eafb1-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="eafb1-162">OUTPUTS</span></span>

### <span data-ttu-id="eafb1-163">Aucun</span><span class="sxs-lookup"><span data-stu-id="eafb1-163">None</span></span>

<span data-ttu-id="eafb1-164">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="eafb1-164">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="eafb1-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="eafb1-165">NOTES</span></span>

* <span data-ttu-id="eafb1-166">Cette applet de commande utilise la méthode AttachDebugger de la classe WMI (Windows Management Instrumentation) Win32_Process.</span><span class="sxs-lookup"><span data-stu-id="eafb1-166">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="eafb1-167">Pour plus d’informations sur cette méthode, consultez la [méthode AttachDebugger](https://go.microsoft.com/fwlink/?LinkId=143640) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="eafb1-167">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="eafb1-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="eafb1-168">RELATED LINKS</span></span>

[<span data-ttu-id="eafb1-169">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="eafb1-169">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="eafb1-170">Get-Process</span><span class="sxs-lookup"><span data-stu-id="eafb1-170">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="eafb1-171">Start-Process</span><span class="sxs-lookup"><span data-stu-id="eafb1-171">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="eafb1-172">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="eafb1-172">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="eafb1-173">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="eafb1-173">Wait-Process</span></span>](Wait-Process.md)
