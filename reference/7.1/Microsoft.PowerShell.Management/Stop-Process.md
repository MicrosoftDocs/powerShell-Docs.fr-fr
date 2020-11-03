---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: ba1313fe0fe7fb462e1a0707c8c73f0cbfda112d
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "93206293"
---
# <span data-ttu-id="036d1-103">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="036d1-103">Stop-Process</span></span>

## <span data-ttu-id="036d1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="036d1-104">SYNOPSIS</span></span>
<span data-ttu-id="036d1-105">Arrête un ou plusieurs processus en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="036d1-105">Stops one or more running processes.</span></span>

## <span data-ttu-id="036d1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="036d1-106">SYNTAX</span></span>

### <span data-ttu-id="036d1-107">ID (par défaut)</span><span class="sxs-lookup"><span data-stu-id="036d1-107">Id (Default)</span></span>

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="036d1-108">Nom</span><span class="sxs-lookup"><span data-stu-id="036d1-108">Name</span></span>

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="036d1-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="036d1-109">InputObject</span></span>

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="036d1-110">Description</span><span class="sxs-lookup"><span data-stu-id="036d1-110">DESCRIPTION</span></span>

<span data-ttu-id="036d1-111">L’applet de commande **Stop-Process** arrête un ou plusieurs processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="036d1-111">The **Stop-Process** cmdlet stops one or more running processes.</span></span>
<span data-ttu-id="036d1-112">Vous pouvez spécifier un processus par nom de processus ou ID de processus (PID), ou passer un objet processus à **Stop-Process** .</span><span class="sxs-lookup"><span data-stu-id="036d1-112">You can specify a process by process name or process ID (PID), or pass a process object to **Stop-Process** .</span></span>
<span data-ttu-id="036d1-113">**Stop-Process** fonctionne uniquement sur les processus qui s’exécutent sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="036d1-113">**Stop-Process** works only on processes running on the local computer.</span></span>

<span data-ttu-id="036d1-114">Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, pour arrêter un processus qui n’appartient pas à l’utilisateur actuel, vous devez démarrer PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="036d1-114">On Windows Vista and later versions of the Windows operating system, to stop a process that is not owned by the current user, you must start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="036d1-115">En outre, vous n’êtes pas invité à confirmer la demande, sauf si vous spécifiez le paramètre *Confirm* .</span><span class="sxs-lookup"><span data-stu-id="036d1-115">Also, you are not prompted for confirmation unless you specify the *Confirm* parameter.</span></span>

## <span data-ttu-id="036d1-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="036d1-116">EXAMPLES</span></span>

### <span data-ttu-id="036d1-117">Exemple 1 : arrêter toutes les instances d’un processus</span><span class="sxs-lookup"><span data-stu-id="036d1-117">Example 1: Stop all instances of a process</span></span>

```
PS C:\> Stop-Process -Name "notepad"
```

<span data-ttu-id="036d1-118">Cette commande arrête toutes les instances du processus Notepad (Bloc-notes) sur l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="036d1-118">This command stops all instances of the Notepad process on the computer.</span></span>
<span data-ttu-id="036d1-119">Chaque instance du bloc-notes s’exécute dans son propre processus.</span><span class="sxs-lookup"><span data-stu-id="036d1-119">Each instance of Notepad runs in its own process.</span></span>
<span data-ttu-id="036d1-120">Elle utilise le paramètre *Name* pour spécifier les processus, qui ont tous le même nom.</span><span class="sxs-lookup"><span data-stu-id="036d1-120">It uses the *Name* parameter to specify the processes, all of which have the same name.</span></span>
<span data-ttu-id="036d1-121">Si vous utilisez le paramètre *ID* pour arrêter les mêmes processus, vous devez répertorier les ID de processus de chaque instance du bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="036d1-121">If you were to use the *Id* parameter to stop the same processes, you would have to list the process IDs of each instance of Notepad.</span></span>

### <span data-ttu-id="036d1-122">Exemple 2 : arrêter une instance spécifique d’un processus</span><span class="sxs-lookup"><span data-stu-id="036d1-122">Example 2: Stop a specific instance of a process</span></span>

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

<span data-ttu-id="036d1-123">Cette commande arrête une instance particulière du processus Notepad.</span><span class="sxs-lookup"><span data-stu-id="036d1-123">This command stops a particular instance of the Notepad process.</span></span>
<span data-ttu-id="036d1-124">Elle utilise l’ID de processus 3952 pour identifier le processus.</span><span class="sxs-lookup"><span data-stu-id="036d1-124">It uses the process ID, 3952, to identify the process.</span></span>
<span data-ttu-id="036d1-125">Le paramètre *Confirm* indique à PowerShell qu’il vous invite à arrêter le processus.</span><span class="sxs-lookup"><span data-stu-id="036d1-125">The *Confirm* parameter directs PowerShell to prompt you before it stops the process.</span></span>
<span data-ttu-id="036d1-126">Étant donné que l’invite comprend le nom du processus en plus de son ID, c’est la meilleure pratique.</span><span class="sxs-lookup"><span data-stu-id="036d1-126">Because the prompt includes the process namein addition to its ID, this is best practice.</span></span>
<span data-ttu-id="036d1-127">Le paramètre *PassThru* passe l’objet processus au formateur pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="036d1-127">The *PassThru* parameter passes the process object to the formatter for display.</span></span>
<span data-ttu-id="036d1-128">Sans ce paramètre, il n’y aurait aucun affichage après une commande **Stop-Process** .</span><span class="sxs-lookup"><span data-stu-id="036d1-128">Without this parameter, there would be no display after a **Stop-Process** command.</span></span>

### <span data-ttu-id="036d1-129">Exemple 3 : arrêter un processus et détecter qu’il s’est arrêté</span><span class="sxs-lookup"><span data-stu-id="036d1-129">Example 3: Stop a process and detect that it has stopped</span></span>

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

<span data-ttu-id="036d1-130">Cette série de commandes démarre et arrête le processus Calc, puis détecte les processus qui se sont arrêtés.</span><span class="sxs-lookup"><span data-stu-id="036d1-130">This series of commands starts and stops the Calc process, and then detects processes that have stopped.</span></span>

<span data-ttu-id="036d1-131">La première commande démarre une instance de la calculatrice.</span><span class="sxs-lookup"><span data-stu-id="036d1-131">The first command starts an instance of the calculator.</span></span>

<span data-ttu-id="036d1-132">La deuxième commande utilise la méthode d' **extraction** de données obtient un objet qui représente le processus Calc, puis le stocke dans la variable $p.</span><span class="sxs-lookup"><span data-stu-id="036d1-132">The second command uses **Get-Process** gets an object that represents the Calc process, and then stores it in the $p variable.</span></span>

<span data-ttu-id="036d1-133">La troisième commande arrête le processus Calc.</span><span class="sxs-lookup"><span data-stu-id="036d1-133">The third command stops the Calc process.</span></span>
<span data-ttu-id="036d1-134">Elle utilise le paramètre *InputObject* pour passer l’objet à **Stop-Process** .</span><span class="sxs-lookup"><span data-stu-id="036d1-134">It uses the *InputObject* parameter to pass the object to **Stop-Process** .</span></span>

<span data-ttu-id="036d1-135">La dernière commande obtient tous les processus qui étaient en cours d’exécution sur l’ordinateur mais qui sont maintenant arrêtés.</span><span class="sxs-lookup"><span data-stu-id="036d1-135">The last command gets all of the processes on the computer that were running but that are now stopped.</span></span>
<span data-ttu-id="036d1-136">Elle utilise la **méthode « Process-process »** pour récupérer tous les processus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="036d1-136">It uses **Get-Process** to get all of the processes on the computer.</span></span>
<span data-ttu-id="036d1-137">L’opérateur de pipeline (|) passe les résultats à l’applet de commande Where-Object, qui sélectionne ceux pour lesquels la valeur de la propriété **HasExited** est $true.</span><span class="sxs-lookup"><span data-stu-id="036d1-137">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the ones where the value of the **HasExited** property is $True.</span></span>
<span data-ttu-id="036d1-138">**HasExited** n’est qu’une des propriétés des objets Process.</span><span class="sxs-lookup"><span data-stu-id="036d1-138">**HasExited** is just one property of process objects.</span></span>
<span data-ttu-id="036d1-139">Pour rechercher toutes les propriétés, tapez `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="036d1-139">To find all the properties, type `Get-Process | Get-Member`.</span></span>

### <span data-ttu-id="036d1-140">Exemple 4 : arrêter un processus qui n’appartient pas à l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="036d1-140">Example 4: Stop a process not owned by the current user</span></span>

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

<span data-ttu-id="036d1-141">Ces commandes montrent l’effet de l’utilisation de *force* pour arrêter un processus qui n’appartient pas à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="036d1-141">These commands show the effect of using *Force* to stop a process that is not owned by the user.</span></span>

<span data-ttu-id="036d1-142">La première commande utilise la méthode **« Process-process »** pour récupérer le processus Lsass.</span><span class="sxs-lookup"><span data-stu-id="036d1-142">The first command uses **Get-Process** to get the Lsass process.</span></span>
<span data-ttu-id="036d1-143">Un opérateur de pipeline envoie le processus à **Stop-Process** pour l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="036d1-143">A pipeline operator sends the process to **Stop-Process** to stop it.</span></span>
<span data-ttu-id="036d1-144">Comme indiqué dans l’exemple de sortie, la première commande échoue avec un message d’accès refusé, car ce processus ne peut être arrêté que par un membre du groupe Administrateurs sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="036d1-144">As shown in the sample output, the first command fails with an Access denied message, because this process can be stopped only by a member of the Administrator group on the computer.</span></span>

<span data-ttu-id="036d1-145">Lorsque PowerShell est ouvert à l’aide de l’option Exécuter en tant qu’administrateur et que la commande est répétée, PowerShell vous invite à confirmer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="036d1-145">When PowerShell is opened by using the Run as administrator option, and the command is repeated, PowerShell prompts you for confirmation.</span></span>

<span data-ttu-id="036d1-146">La deuxième commande spécifie *force* pour supprimer l’invite.</span><span class="sxs-lookup"><span data-stu-id="036d1-146">The second command specifies *Force* to suppress the prompt.</span></span>
<span data-ttu-id="036d1-147">Le processus est alors arrêté sans confirmation.</span><span class="sxs-lookup"><span data-stu-id="036d1-147">As a result, the process is stopped without confirmation.</span></span>

## <span data-ttu-id="036d1-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="036d1-148">PARAMETERS</span></span>

### <span data-ttu-id="036d1-149">-Force</span><span class="sxs-lookup"><span data-stu-id="036d1-149">-Force</span></span>

<span data-ttu-id="036d1-150">Arrête les processus spécifiés sans inviter à confirmer l’opération.</span><span class="sxs-lookup"><span data-stu-id="036d1-150">Stops the specified processes without prompting for confirmation.</span></span>
<span data-ttu-id="036d1-151">Par défaut, **Stop-Process** vous invite à confirmer l’opération avant d’arrêter tout processus qui n’appartient pas à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="036d1-151">By default, **Stop-Process** prompts for confirmation before stopping any process that is not owned by the current user.</span></span>

<span data-ttu-id="036d1-152">Pour rechercher le propriétaire d’un processus, utilisez l' `Get-CimInstance` applet de commande pour obtenir un objet **Win32_Process** qui représente le processus, puis utilisez la méthode **GetOwner** de l’objet.</span><span class="sxs-lookup"><span data-stu-id="036d1-152">To find the owner of a process, use the `Get-CimInstance` cmdlet to get a **Win32_Process** object that represents the process, and then use the **GetOwner** method of the object.</span></span>

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

### <span data-ttu-id="036d1-153">-Id</span><span class="sxs-lookup"><span data-stu-id="036d1-153">-Id</span></span>

<span data-ttu-id="036d1-154">Spécifie les ID de processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="036d1-154">Specifies the process IDs of the processes to stop.</span></span>
<span data-ttu-id="036d1-155">Lorsque vous spécifiez plusieurs identificateurs, séparez-les à l'aide de virgules.</span><span class="sxs-lookup"><span data-stu-id="036d1-155">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="036d1-156">Pour rechercher le PID d’un processus, tapez `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="036d1-156">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="036d1-157">-InputObject</span><span class="sxs-lookup"><span data-stu-id="036d1-157">-InputObject</span></span>

<span data-ttu-id="036d1-158">Spécifie les objets de processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="036d1-158">Specifies the process objects to stop.</span></span>
<span data-ttu-id="036d1-159">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="036d1-159">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="036d1-160">-Name</span><span class="sxs-lookup"><span data-stu-id="036d1-160">-Name</span></span>

<span data-ttu-id="036d1-161">Spécifie les noms des processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="036d1-161">Specifies the process names of the processes to stop.</span></span>
<span data-ttu-id="036d1-162">Vous pouvez taper plusieurs noms de processus, en les séparant par des virgules, ou utiliser des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="036d1-162">You can type multiple process names, separated by commas, or use wildcard characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="036d1-163">-PassThru</span><span class="sxs-lookup"><span data-stu-id="036d1-163">-PassThru</span></span>

<span data-ttu-id="036d1-164">Retourne un objet qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="036d1-164">Returns an object that represents the process.</span></span>
<span data-ttu-id="036d1-165">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="036d1-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="036d1-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="036d1-166">-Confirm</span></span>

<span data-ttu-id="036d1-167">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="036d1-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="036d1-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="036d1-168">-WhatIf</span></span>

<span data-ttu-id="036d1-169">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="036d1-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="036d1-170">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="036d1-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="036d1-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="036d1-171">CommonParameters</span></span>
<span data-ttu-id="036d1-172">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="036d1-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="036d1-173">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="036d1-173">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="036d1-174">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="036d1-174">INPUTS</span></span>

### <span data-ttu-id="036d1-175">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="036d1-175">System.Diagnostics.Process</span></span>

<span data-ttu-id="036d1-176">Vous pouvez diriger un objet processus vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="036d1-176">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="036d1-177">SORTIES</span><span class="sxs-lookup"><span data-stu-id="036d1-177">OUTPUTS</span></span>

### <span data-ttu-id="036d1-178">Aucun, System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="036d1-178">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="036d1-179">Cette applet de commande retourne un objet **System. Diagnostics. Process** qui représente le processus arrêté, si vous spécifiez le paramètre *PassThru* .</span><span class="sxs-lookup"><span data-stu-id="036d1-179">This cmdlet returns a **System.Diagnostics.Process** object that represents the stopped process, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="036d1-180">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="036d1-180">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="036d1-181">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="036d1-181">NOTES</span></span>

* <span data-ttu-id="036d1-182">Vous pouvez également faire référence à **Stop-Process** par ses alias intégrés, **Kill** et **SPPS** .</span><span class="sxs-lookup"><span data-stu-id="036d1-182">You can also refer to **Stop-Process** by its built-in aliases, **kill** and **spps** .</span></span> <span data-ttu-id="036d1-183">Pour plus d'informations, consultez about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="036d1-183">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="036d1-184">Vous pouvez également utiliser les propriétés et les méthodes de l’objet **Win32_Process** Windows Management Instrumentation (WMI) dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="036d1-184">You can also use the properties and methods of the Windows Management Instrumentation (WMI) **Win32_Process** object in Windows PowerShell.</span></span>
<span data-ttu-id="036d1-185">Pour plus d’informations, consultez `Get-CimInstance` et le kit de développement logiciel (SDK) WMI.</span><span class="sxs-lookup"><span data-stu-id="036d1-185">For more information, see `Get-CimInstance` and the WMI SDK.</span></span>

* <span data-ttu-id="036d1-186">Lorsque vous arrêtez des processus, sachez que l’arrêt d’un processus peut arrêter les processus et les services qui dépendent du processus.</span><span class="sxs-lookup"><span data-stu-id="036d1-186">When stopping processes, realize that stopping a process can stop process and services that depend on the process.</span></span>
<span data-ttu-id="036d1-187">Dans certains cas extrêmes, l’arrêt d’un processus peut entraîner l’arrêt de Windows.</span><span class="sxs-lookup"><span data-stu-id="036d1-187">In an extreme case, stopping a process can stop Windows.</span></span>

## <span data-ttu-id="036d1-188">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="036d1-188">RELATED LINKS</span></span>

[<span data-ttu-id="036d1-189">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="036d1-189">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="036d1-190">Get-Process</span><span class="sxs-lookup"><span data-stu-id="036d1-190">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="036d1-191">Start-Process</span><span class="sxs-lookup"><span data-stu-id="036d1-191">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="036d1-192">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="036d1-192">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="036d1-193">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="036d1-193">Wait-Process</span></span>](Wait-Process.md)

