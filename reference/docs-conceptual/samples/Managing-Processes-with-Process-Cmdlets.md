---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Gestion des processus avec les applets de commande Process
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 741a3464bce6284c4933384398c4e9ddcca2572c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401197"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="850e6-103">Gestion des processus avec les applets de commande Process</span><span class="sxs-lookup"><span data-stu-id="850e6-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="850e6-104">Les applets de commande Process de Windows PowerShell permettent de gérer des processus locaux et distants dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="850e6-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="850e6-105">Obtention de processus (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="850e6-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="850e6-106">Pour obtenir les processus en cours d’exécution sur l’ordinateur local, exécutez l’applet de commande **Get-Process** sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="850e6-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="850e6-107">Vous pouvez obtenir des processus particuliers en spécifiant leur nom ou leur ID.</span><span class="sxs-lookup"><span data-stu-id="850e6-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="850e6-108">La commande suivante obtient le processus Idle :</span><span class="sxs-lookup"><span data-stu-id="850e6-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="850e6-109">S’il est normal que des applets de commande ne retournent aucune donnée dans certaines situations, lorsque vous spécifiez un processus par son ID, l’applet de commande **Get-Process** génère une erreur si elle ne trouve aucune correspondance, car l’objectif consiste généralement à récupérer un processus en cours d’exécution connu.</span><span class="sxs-lookup"><span data-stu-id="850e6-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="850e6-110">Si aucun processus ne correspond à cet ID, il est probable que celui-ci est incorrect ou que son exécution est déjà terminée :</span><span class="sxs-lookup"><span data-stu-id="850e6-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="850e6-111">Vous pouvez utiliser le paramètre Name de l’applet de commande Get-Process pour spécifier une partie des processus en se basant sur le nom des processus.</span><span class="sxs-lookup"><span data-stu-id="850e6-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="850e6-112">Le paramètre Name peut prendre plusieurs noms dans une liste de valeurs séparées par des virgules. Comme il prend en charge l’utilisation de caractères génériques, vous pouvez entrer des modèles de noms.</span><span class="sxs-lookup"><span data-stu-id="850e6-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="850e6-113">Par exemple, la commande suivante obtient les processus dont les noms commencent par « ex ».</span><span class="sxs-lookup"><span data-stu-id="850e6-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="850e6-114">Étant donné que la classe System.Diagnostics.Process de .NET constitue la base des processus Windows PowerShell, elle suit certaines des conventions utilisées par System.Diagnostics.Process.</span><span class="sxs-lookup"><span data-stu-id="850e6-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="850e6-115">L’une de ces conventions est que le nom de processus d’un exécutable n’inclut jamais « .exe » à la fin du nom.</span><span class="sxs-lookup"><span data-stu-id="850e6-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="850e6-116">L’applet de commande **Get-Process** accepte également plusieurs valeurs pour le paramètre Name.</span><span class="sxs-lookup"><span data-stu-id="850e6-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="850e6-117">Vous pouvez utiliser le paramètre ComputerName de l’applet de commande Get-Process pour obtenir des processus sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="850e6-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="850e6-118">Par exemple, la commande suivante obtient les processus PowerShell sur l’ordinateur local (représenté par « localhost ») et sur deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="850e6-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="850e6-119">Les noms d’ordinateurs ne sont pas évidents dans cet affichage, mais ils sont stockés dans la propriété MachineName des objets de processus que l’applet de commande Get-Process retourne.</span><span class="sxs-lookup"><span data-stu-id="850e6-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="850e6-120">La commande suivante utilise l’applet de commande Format-Table pour afficher les propriétés d’ID de processus, ProcessName et MachineName (ComputerName) des objets de processus.</span><span class="sxs-lookup"><span data-stu-id="850e6-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="850e6-121">Cette commande plus complexe ajoute la propriété MachineName à l’affichage standard de l’applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="850e6-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="850e6-122">Arrêt des processus (Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="850e6-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="850e6-123">Windows PowerShell offre une flexibilité certaine pour l’affichage des processus, mais qu’en est-il de l’arrêt d’un processus ?</span><span class="sxs-lookup"><span data-stu-id="850e6-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="850e6-124">L’applet de commande **Stop-Process** prend un nom ou un ID pour spécifier un processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="850e6-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="850e6-125">Votre capacité à arrêter des processus dépend des autorisations dont vous disposez.</span><span class="sxs-lookup"><span data-stu-id="850e6-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="850e6-126">Certains processus ne peuvent pas être arrêtés.</span><span class="sxs-lookup"><span data-stu-id="850e6-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="850e6-127">Par exemple, si vous essayez d’arrêter le processus inactif, vous obtenez une erreur :</span><span class="sxs-lookup"><span data-stu-id="850e6-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="850e6-128">Vous pouvez également forcer l’affichage d’une invite avec le paramètre **Confirm**.</span><span class="sxs-lookup"><span data-stu-id="850e6-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="850e6-129">Ce paramètre est particulièrement utile si vous utilisez un caractère générique quand vous spécifiez le nom du processus, car vous pouvez accidentellement établir une correspondance avec des processus que vous ne souhaitez pas arrêter :</span><span class="sxs-lookup"><span data-stu-id="850e6-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="850e6-130">Une manipulation de processus complexes est possible en utilisant certaines applets de commande de filtrage d’objet.</span><span class="sxs-lookup"><span data-stu-id="850e6-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="850e6-131">Étant donné qu’un objet Process a une propriété Responding dont la valeur est true quand il ne répond plus, vous pouvez arrêter toutes les applications qui ne répondent pas avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="850e6-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="850e6-132">Vous pouvez utiliser la même approche dans d’autres situations.</span><span class="sxs-lookup"><span data-stu-id="850e6-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="850e6-133">Par exemple, supposons qu’une application de zone de notification secondaire s’exécute automatiquement quand des utilisateurs démarrent une autre application.</span><span class="sxs-lookup"><span data-stu-id="850e6-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="850e6-134">Il est possible que vous constatiez que cela ne fonctionne pas correctement dans les sessions des services Terminal Server, mais que vous souhaitiez conserver cette approche dans les sessions qui s’exécutent sur la console de l’ordinateur physique.</span><span class="sxs-lookup"><span data-stu-id="850e6-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="850e6-135">Les sessions connectées au bureau de l’ordinateur physique ayant toujours un ID de session 0, vous pouvez arrêter toutes les instances du processus figurant dans d’autres sessions à l’aide de l’applet de commande **Where-Object** et du processus **SessionId** :</span><span class="sxs-lookup"><span data-stu-id="850e6-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="850e6-136">L’applet de commande Stop-Process ne prend pas de paramètre ComputerName.</span><span class="sxs-lookup"><span data-stu-id="850e6-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="850e6-137">Par conséquent, pour exécuter une commande d’arrêt de processus sur un ordinateur distant, vous devez utiliser l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="850e6-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="850e6-138">Par exemple, pour arrêter le processus PowerShell sur l’ordinateur distant Serveur01, tapez :</span><span class="sxs-lookup"><span data-stu-id="850e6-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="850e6-139">Arrêt de toutes les autres sessions Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="850e6-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="850e6-140">Il est parfois utile de pouvoir arrêter toutes les sessions Windows PowerShell en cours d’exécution autres que la session active.</span><span class="sxs-lookup"><span data-stu-id="850e6-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="850e6-141">Si une session utilise trop de ressources ou n’est pas accessible (par exemple, si elle s’exécute à distance ou dans une autre session de bureau), il se peut que vous ne puissiez pas l’arrêter directement.</span><span class="sxs-lookup"><span data-stu-id="850e6-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="850e6-142">Toutefois, si vous essayez d’arrêter toutes les sessions en cours d’exécution, il se peut que la session active s’arrête à la place.</span><span class="sxs-lookup"><span data-stu-id="850e6-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="850e6-143">Chaque session Windows PowerShell a un PID de variable d’environnement qui contient l’ID du processus Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="850e6-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="850e6-144">Vous pouvez contrôler la valeur de $PID par rapport à l’ID de chaque session, et arrêter uniquement les sessions Windows PowerShell dont l’ID diffère. La commande de pipeline suivante effectue cette opération et retourne la liste des sessions terminées (en raison de l’utilisation du paramètre **PassThru**) :</span><span class="sxs-lookup"><span data-stu-id="850e6-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="850e6-145">Démarrage, débogage et attente de processus</span><span class="sxs-lookup"><span data-stu-id="850e6-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="850e6-146">Windows PowerShell comprend également des applets de commande permettant de démarrer (ou redémarrer) un processus, de déboguer un processus, et d’attendre qu’un processus s’achève avant d’exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="850e6-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="850e6-147">Pour plus d’informations sur ces applets de commande, voir la rubrique d’aide sur chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="850e6-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="850e6-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="850e6-148">See Also</span></span>

- <span data-ttu-id="850e6-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="850e6-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="850e6-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="850e6-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="850e6-151">Start-Process</span><span class="sxs-lookup"><span data-stu-id="850e6-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="850e6-152">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="850e6-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="850e6-153">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="850e6-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="850e6-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="850e6-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
