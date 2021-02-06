---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 85cbc9d012781873dddaf2a7d220a0e478dcbda2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599152"
---
# <span data-ttu-id="04e7f-102">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="04e7f-102">Enter-PSHostProcess</span></span>

## <span data-ttu-id="04e7f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="04e7f-103">SYNOPSIS</span></span>
<span data-ttu-id="04e7f-104">Se connecte à et entre dans une session interactive avec un processus local.</span><span class="sxs-lookup"><span data-stu-id="04e7f-104">Connects to and enters into an interactive session with a local process.</span></span>

## <span data-ttu-id="04e7f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="04e7f-105">SYNTAX</span></span>

### <span data-ttu-id="04e7f-106">ProcessIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="04e7f-106">ProcessIdParameterSet (Default)</span></span>

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="04e7f-107">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="04e7f-107">ProcessParameterSet</span></span>

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="04e7f-108">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="04e7f-108">ProcessNameParameterSet</span></span>

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="04e7f-109">PSHostProcessInfoParameterSet</span><span class="sxs-lookup"><span data-stu-id="04e7f-109">PSHostProcessInfoParameterSet</span></span>

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="04e7f-110">PipeNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="04e7f-110">PipeNameParameterSet</span></span>

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## <span data-ttu-id="04e7f-111">Description</span><span class="sxs-lookup"><span data-stu-id="04e7f-111">DESCRIPTION</span></span>

<span data-ttu-id="04e7f-112">L' `Enter-PSHostProcess` applet de commande se connecte à et entre dans une session interactive avec un processus local.</span><span class="sxs-lookup"><span data-stu-id="04e7f-112">The `Enter-PSHostProcess` cmdlet connects to and enters into an interactive session with a local process.</span></span> <span data-ttu-id="04e7f-113">À compter de PowerShell 6,2, cette applet de commande est prise en charge sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="04e7f-113">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

<span data-ttu-id="04e7f-114">Au lieu de créer un nouveau processus pour héberger PowerShell et exécuter une session à distance, la session distante interactive est exécutée dans un processus existant qui exécute déjà PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04e7f-114">Instead of creating a new process to host PowerShell and run a remote session, the remote, interactive session is run in an existing process that is already running PowerShell.</span></span> <span data-ttu-id="04e7f-115">Quand vous interagissez avec une session à distance sur un processus spécifié, vous pouvez énumérer les instances d’exécution en cours d’exécution, puis sélectionner une instance d’exécution à déboguer en exécutant `Debug-Runspace` ou `Enable-RunspaceDebug` .</span><span class="sxs-lookup"><span data-stu-id="04e7f-115">When you are interacting with a remote session on a specified process, you can enumerate running runspaces, and then select a runspace to debug by running either `Debug-Runspace` or `Enable-RunspaceDebug`.</span></span>

<span data-ttu-id="04e7f-116">Le processus que vous souhaitez entrer doit héberger PowerShell (System.Management.Automation.dll).</span><span class="sxs-lookup"><span data-stu-id="04e7f-116">The process that you want to enter must be hosting PowerShell (System.Management.Automation.dll).</span></span>
<span data-ttu-id="04e7f-117">Vous devez être membre du groupe Administrateurs sur l’ordinateur sur lequel le processus est trouvé, ou vous devez être l’utilisateur qui exécute le script qui a démarré le processus.</span><span class="sxs-lookup"><span data-stu-id="04e7f-117">You must be either a member of the Administrators group on the computer on which the process is found, or you must be the user who is running the script that started the process.</span></span>

<span data-ttu-id="04e7f-118">Une fois que vous avez sélectionné une instance d’exécution à déboguer, une session de débogage à distance est ouverte pour l’instance d’exécution si elle exécute actuellement une commande ou s’il est arrêté dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="04e7f-118">After you have selected a runspace to debug, a remote debug session is opened for the runspace if it is either currently running a command or is stopped in the debugger.</span></span> <span data-ttu-id="04e7f-119">Vous pouvez ensuite déboguer le script de l’instance d’exécution de la même façon que vous le feriez pour d’autres scripts de session à distance.</span><span class="sxs-lookup"><span data-stu-id="04e7f-119">You can then debug the runspace script in the same way you would debug other remote session scripts.</span></span>

<span data-ttu-id="04e7f-120">Détachez d’une session de débogage, puis la session interactive avec le processus, en exécutant deux fois exit ou arrêtez l’exécution du script en exécutant la commande du débogueur Quit existant.</span><span class="sxs-lookup"><span data-stu-id="04e7f-120">Detach from a debugging session, and then the interactive session with the process, by running exit twice, or stop script execution by running the existing debugger quit command.</span></span>

<span data-ttu-id="04e7f-121">Si vous spécifiez un processus à l’aide du paramètre **Name** et qu’un seul processus est trouvé avec le nom spécifié, le processus est entré.</span><span class="sxs-lookup"><span data-stu-id="04e7f-121">If you specify a process by using the **Name** parameter, and there is only one process found with the specified name, the process is entered.</span></span> <span data-ttu-id="04e7f-122">Si plusieurs processus portant le nom spécifié sont trouvés, PowerShell retourne une erreur et répertorie tous les processus trouvés avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="04e7f-122">If more than one process with the specified name is found, PowerShell returns an error, and lists all processes found with the specified name.</span></span>

<span data-ttu-id="04e7f-123">Pour prendre en charge l’attachement à des processus sur des ordinateurs distants, l' `Enter-PSHostProcess` applet de commande est activée sur un ordinateur distant spécifié, ce qui vous permet d’attacher un processus local dans une session PowerShell distante.</span><span class="sxs-lookup"><span data-stu-id="04e7f-123">To support attaching to processes on remote computers, the `Enter-PSHostProcess` cmdlet is enabled in a specified remote computer, so that you can attach to a local process within a remote PowerShell session.</span></span>

## <span data-ttu-id="04e7f-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="04e7f-124">EXAMPLES</span></span>

### <span data-ttu-id="04e7f-125">Exemple 1 : démarrer le débogage d’une instance d’exécution dans le processus PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="04e7f-125">Example 1: Start debugging a runspace within the PowerShell ISE process</span></span>

<span data-ttu-id="04e7f-126">Dans cet exemple, vous exécutez `Enter-PSHostProcess` à partir de la console PowerShell pour entrer dans le processus PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="04e7f-126">In this example, you run `Enter-PSHostProcess` from within the PowerShell console to enter the PowerShell ISE process.</span></span> <span data-ttu-id="04e7f-127">Dans la session interactive obtenue, vous pouvez trouver une instance d’exécution que vous souhaitez déboguer en exécutant `Get-Runspace` , puis déboguer l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="04e7f-127">In the resulting interactive session, you can find a runspace that you want to debug by running `Get-Runspace`, and then debug the runspace.</span></span>

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## <span data-ttu-id="04e7f-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="04e7f-128">PARAMETERS</span></span>

### <span data-ttu-id="04e7f-129">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="04e7f-129">-AppDomainName</span></span>

<span data-ttu-id="04e7f-130">Spécifie un nom de domaine d’application auquel se connecter en cas d’omission, utilise **DefaultAppDomain**.</span><span class="sxs-lookup"><span data-stu-id="04e7f-130">Specifies an application domain name to connect to if omitted, uses **DefaultAppDomain**.</span></span> <span data-ttu-id="04e7f-131">Utilisez `Get-PSHostProcessInfo` pour afficher les noms de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="04e7f-131">Use `Get-PSHostProcessInfo` to display the application domain names.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04e7f-132">-HostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="04e7f-132">-HostProcessInfo</span></span>

<span data-ttu-id="04e7f-133">Spécifie un objet **PSHostProcessInfo** qui peut être connecté à avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04e7f-133">Specifies a **PSHostProcessInfo** object that can be connected to with PowerShell.</span></span> <span data-ttu-id="04e7f-134">Utilisez `Get-PSHostProcessInfo` pour récupérer l’objet.</span><span class="sxs-lookup"><span data-stu-id="04e7f-134">Use `Get-PSHostProcessInfo` to get the object.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="04e7f-135">-Id</span><span class="sxs-lookup"><span data-stu-id="04e7f-135">-Id</span></span>

<span data-ttu-id="04e7f-136">Spécifie un processus par l’ID de processus.</span><span class="sxs-lookup"><span data-stu-id="04e7f-136">Specifies a process by the process ID.</span></span> <span data-ttu-id="04e7f-137">Pour obtenir un ID de processus, exécutez l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="04e7f-137">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04e7f-138">-Name</span><span class="sxs-lookup"><span data-stu-id="04e7f-138">-Name</span></span>

<span data-ttu-id="04e7f-139">Spécifie un processus par le nom du processus.</span><span class="sxs-lookup"><span data-stu-id="04e7f-139">Specifies a process by the process name.</span></span> <span data-ttu-id="04e7f-140">Pour obtenir un nom de processus, exécutez l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="04e7f-140">To get a process name, run the `Get-Process` cmdlet.</span></span> <span data-ttu-id="04e7f-141">Vous pouvez également obtenir des noms de processus à partir de la boîte de dialogue Propriétés d’un processus dans le gestionnaire des tâches.</span><span class="sxs-lookup"><span data-stu-id="04e7f-141">You can also get process names from the Properties dialog box of a process in Task Manager.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04e7f-142">-Processus</span><span class="sxs-lookup"><span data-stu-id="04e7f-142">-Process</span></span>

<span data-ttu-id="04e7f-143">Spécifie un processus par l’objet processus.</span><span class="sxs-lookup"><span data-stu-id="04e7f-143">Specifies a process by the process object.</span></span> <span data-ttu-id="04e7f-144">La façon la plus simple d’utiliser ce paramètre consiste à enregistrer les résultats d’une `Get-Process` commande qui retourne le processus que vous souhaitez entrer dans une variable, puis à spécifier la variable comme valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="04e7f-144">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="04e7f-145">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="04e7f-145">-CustomPipeName</span></span>

<span data-ttu-id="04e7f-146">Obtient ou définit le nom de canal nommé personnalisé auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="04e7f-146">Gets or sets the custom named pipe name to connect to.</span></span> <span data-ttu-id="04e7f-147">Cela est généralement utilisé conjointement avec `pwsh -CustomPipeName` .</span><span class="sxs-lookup"><span data-stu-id="04e7f-147">This is usually used in conjunction with `pwsh -CustomPipeName`.</span></span>

<span data-ttu-id="04e7f-148">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="04e7f-148">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04e7f-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="04e7f-149">CommonParameters</span></span>

<span data-ttu-id="04e7f-150">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="04e7f-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="04e7f-151">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="04e7f-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="04e7f-152">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="04e7f-152">INPUTS</span></span>

### <span data-ttu-id="04e7f-153">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="04e7f-153">System.Diagnostics.Process</span></span>

## <span data-ttu-id="04e7f-154">SORTIES</span><span class="sxs-lookup"><span data-stu-id="04e7f-154">OUTPUTS</span></span>

## <span data-ttu-id="04e7f-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="04e7f-155">NOTES</span></span>

<span data-ttu-id="04e7f-156">`Enter-PSHostProcess` Impossible d’entrer dans le processus de la session PowerShell dans laquelle vous exécutez la commande.</span><span class="sxs-lookup"><span data-stu-id="04e7f-156">`Enter-PSHostProcess` cannot enter the process of the PowerShell session in which you are running the command.</span></span> <span data-ttu-id="04e7f-157">Toutefois, vous pouvez entrer le processus d’une autre session PowerShell ou une session PowerShell ISE qui s’exécute en même temps que la session dans laquelle vous exécutez `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="04e7f-157">You can, however, enter the process of another PowerShell session, or a PowerShell ISE session that is running at the same time as the session in which you are running `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="04e7f-158">`Enter-PSHostProcess` peut entrer uniquement les processus qui hébergent PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04e7f-158">`Enter-PSHostProcess` can enter only those processes that are hosting PowerShell.</span></span> <span data-ttu-id="04e7f-159">Autrement dit, ils ont chargé le moteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04e7f-159">That is, they have loaded the PowerShell engine.</span></span>

<span data-ttu-id="04e7f-160">Pour quitter un processus au sein du processus, tapez **Exit**, puis appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="04e7f-160">To exit a process from within the process, type **exit**, and then press <kbd>Enter</kbd>.</span></span>

<span data-ttu-id="04e7f-161">Avant PowerShell 7.1, la communication à distance via SSH ne prenait pas en charge les sessions à distance de deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="04e7f-161">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="04e7f-162">Cette fonctionnalité était limitée aux sessions qui utilisaient WinRM.</span><span class="sxs-lookup"><span data-stu-id="04e7f-162">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="04e7f-163">PowerShell 7.1 permet à `Enter-PSSession` et `Enter-PSHostProcess` de fonctionner dans n’importe quelle session à distance interactive.</span><span class="sxs-lookup"><span data-stu-id="04e7f-163">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="04e7f-164">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="04e7f-164">RELATED LINKS</span></span>

[<span data-ttu-id="04e7f-165">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="04e7f-165">Exit-PSHostProcess</span></span>](Exit-PSHostProcess.md)

[<span data-ttu-id="04e7f-166">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="04e7f-166">Get-PSHostProcessInfo</span></span>](Get-PSHostProcessInfo.md)

