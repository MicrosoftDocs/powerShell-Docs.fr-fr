---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: 947fcea58ea32e34bdd0dc0129443ac5bc39c561
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201722"
---
# <span data-ttu-id="23135-103">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="23135-103">Debug-Job</span></span>

## <span data-ttu-id="23135-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="23135-104">SYNOPSIS</span></span>
<span data-ttu-id="23135-105">Débogue un travail d’arrière-plan, distant ou PowerShell en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="23135-105">Debugs a running background, remote, or PowerShell Workflow job.</span></span>

## <span data-ttu-id="23135-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23135-106">SYNTAX</span></span>

### <span data-ttu-id="23135-107">JobParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="23135-107">JobParameterSet (Default)</span></span>

```
Debug-Job [-Job] <Job> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="23135-108">JobNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="23135-108">JobNameParameterSet</span></span>

```
Debug-Job [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="23135-109">JobIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="23135-109">JobIdParameterSet</span></span>

```
Debug-Job [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="23135-110">JobInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="23135-110">JobInstanceIdParameterSet</span></span>

```
Debug-Job [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="23135-111">Description</span><span class="sxs-lookup"><span data-stu-id="23135-111">DESCRIPTION</span></span>
<span data-ttu-id="23135-112">L’applet de commande **Debug-Job** vous permet de déboguer des scripts qui s’exécutent dans des tâches.</span><span class="sxs-lookup"><span data-stu-id="23135-112">The **Debug-Job** cmdlet lets you debug scripts that are running within jobs.</span></span>
<span data-ttu-id="23135-113">L’applet de commande est conçue pour déboguer les tâches PowerShell workflow, les travaux en arrière-plan et les travaux en cours d’exécution dans des sessions à distance.</span><span class="sxs-lookup"><span data-stu-id="23135-113">The cmdlet is designed to debug PowerShell Workflow jobs, background jobs, and jobs running in remote sessions.</span></span>
<span data-ttu-id="23135-114">**Debug-Job** accepte un objet de travail en cours d’exécution, un nom, un ID ou un ID d’instance comme entrée, et démarre une session de débogage sur le script qu’il exécute.</span><span class="sxs-lookup"><span data-stu-id="23135-114">**Debug-Job** accepts a running job object, name, ID, or instance ID as input, and starts a debugging session on the script it is running.</span></span>
<span data-ttu-id="23135-115">La commande **Quit** du débogueur arrête le travail et exécute le script.</span><span class="sxs-lookup"><span data-stu-id="23135-115">The debugger **quit** command stops the job and running script.</span></span>
<span data-ttu-id="23135-116">À compter de Windows PowerShell 5,0, la commande **Exit** détache le débogueur et permet à la tâche de continuer à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="23135-116">Starting in Windows PowerShell 5.0, the **exit** command detaches the debugger, and allows the job to continue to run.</span></span>

## <span data-ttu-id="23135-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="23135-117">EXAMPLES</span></span>

### <span data-ttu-id="23135-118">Exemple 1 : déboguer un travail par ID de travail</span><span class="sxs-lookup"><span data-stu-id="23135-118">Example 1: Debug a job by job ID</span></span>

```
PS C:\> Debug-Job -ID 3
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
3      Job3            RemoteJob       Running       True            PowerShellIx         TestWFDemo1.ps1
          Entering debug mode. Use h or ? for help.

          Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

          At C:\TestWFDemo1.ps1:8 char:5
          +     Write-Output -InputObject "Now writing output:"
          +     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          [DBG:PowerShellIx]: PS C:\> > list

              3:
              4:  workflow SampleWorkflowTest
              5:  {
              6:      param ($MyOutput)
              7:
              8:*     Write-Output -InputObject "Now writing output:"
              9:      Write-Output -Input $MyOutput
             10:
             11:      Write-Output -InputObject "Get PowerShell process:"
             12:      Get-Process -Name powershell
             13:
             14:      Write-Output -InputObject "Workflow function complete."
             15:  }
             16:
             17:  # Call workflow function
             18:  SampleWorkflowTest -MyOutput "Hello"
```

<span data-ttu-id="23135-119">Cette commande s’arrête sur un travail en cours d’exécution avec un ID de 3.</span><span class="sxs-lookup"><span data-stu-id="23135-119">This command breaks into a running job with an ID of 3.</span></span>

## <span data-ttu-id="23135-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23135-120">PARAMETERS</span></span>

### <span data-ttu-id="23135-121">-Id</span><span class="sxs-lookup"><span data-stu-id="23135-121">-Id</span></span>
<span data-ttu-id="23135-122">Spécifie le numéro d’identification d’un travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="23135-122">Specifies the ID number of a running job.</span></span>
<span data-ttu-id="23135-123">Pour obtenir le numéro d’identification d’un travail, exécutez l’applet de commande Get-Job.</span><span class="sxs-lookup"><span data-stu-id="23135-123">To get the ID number of a job, run the Get-Job cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23135-124">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="23135-124">-InstanceId</span></span>
<span data-ttu-id="23135-125">Spécifie le GUID de l’ID d’instance d’un travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="23135-125">Specifies the instance ID GUID of a running job.</span></span>
<span data-ttu-id="23135-126">Pour obtenir l' *ID* d’une tâche, exécutez l’applet de commande **obtenir-Job** , en canalisant les résultats dans une applet de commande **format-** \*, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="23135-126">To get the *InstanceId* of a job, run the **Get-Job** cmdlet, piping the results into a **Format-** \* cmdlet, as shown in the following example:</span></span>

`Get-Job | Format-List -Property Id,Name,InstanceId,State`

```yaml
Type: System.Guid
Parameter Sets: JobInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23135-127">-Travail</span><span class="sxs-lookup"><span data-stu-id="23135-127">-Job</span></span>
<span data-ttu-id="23135-128">Spécifie un objet de traitement en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="23135-128">Specifies a running job object.</span></span>
<span data-ttu-id="23135-129">La façon la plus simple d’utiliser ce paramètre consiste à enregistrer les résultats d’une commande **« obtenir-Job »** qui retourne le travail en cours d’exécution que vous souhaitez déboguer dans une variable, puis à spécifier la variable comme valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="23135-129">The simplest way to use this parameter is to save the results of a **Get-Job** command that returns the running job that you want to debug in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Management.Automation.Job
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="23135-130">-Name</span><span class="sxs-lookup"><span data-stu-id="23135-130">-Name</span></span>
<span data-ttu-id="23135-131">Spécifie un travail par le nom convivial du travail.</span><span class="sxs-lookup"><span data-stu-id="23135-131">Specifies a job by the friendly name of the job.</span></span>
<span data-ttu-id="23135-132">Lorsque vous démarrez un travail, vous pouvez spécifier un nom de travail en ajoutant le paramètre *JobName* , dans les applets de commande telles que Invoke-Command et Start-Job.</span><span class="sxs-lookup"><span data-stu-id="23135-132">When you start a job, you can specify a job name by adding the *JobName* parameter, in cmdlets such as Invoke-Command and Start-Job.</span></span>

```yaml
Type: System.String
Parameter Sets: JobNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23135-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="23135-133">-Confirm</span></span>
<span data-ttu-id="23135-134">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="23135-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="23135-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="23135-135">-WhatIf</span></span>
<span data-ttu-id="23135-136">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="23135-136">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="23135-137">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="23135-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="23135-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23135-138">CommonParameters</span></span>
<span data-ttu-id="23135-139">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23135-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23135-140">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="23135-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23135-141">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="23135-141">INPUTS</span></span>

### <span data-ttu-id="23135-142">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="23135-142">System.Management.Automation.RemotingJob</span></span>

## <span data-ttu-id="23135-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="23135-143">OUTPUTS</span></span>

## <span data-ttu-id="23135-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="23135-144">NOTES</span></span>

## <span data-ttu-id="23135-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="23135-145">RELATED LINKS</span></span>

[<span data-ttu-id="23135-146">Get-Job</span><span class="sxs-lookup"><span data-stu-id="23135-146">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="23135-147">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="23135-147">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="23135-148">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="23135-148">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="23135-149">Start-Job</span><span class="sxs-lookup"><span data-stu-id="23135-149">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="23135-150">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="23135-150">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="23135-151">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="23135-151">Wait-Job</span></span>](Wait-Job.md)
