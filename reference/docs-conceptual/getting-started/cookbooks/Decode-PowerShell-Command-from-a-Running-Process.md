---
ms.date: 11/13/2018
keywords: powershell,applet de commande
title: Décoder une commande PowerShell à partir d’un processus en cours d’exécution
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619195"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="51e66-103">Décoder une commande PowerShell à partir d’un processus en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="51e66-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="51e66-104">Dans certains cas, vous pouvez avoir un processus en cours d’exécution qui occupe une grande quantité de ressources de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51e66-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="51e66-105">Ce processus peut s’exécuter dans le contexte d’un [Planificateur de tâches][] travail ou un [SQL Server Agent][] travail.</span><span class="sxs-lookup"><span data-stu-id="51e66-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="51e66-106">S’il existe plusieurs processus PowerShell en cours d’exécution, il peut être difficile de savoir quel processus représente le problème.</span><span class="sxs-lookup"><span data-stu-id="51e66-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="51e66-107">Cet article explique comment décoder un bloc de script, un processus PowerShell est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="51e66-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="51e66-108">Créer un processus à long terme</span><span class="sxs-lookup"><span data-stu-id="51e66-108">Create a long running process</span></span>

<span data-ttu-id="51e66-109">Pour illustrer ce scénario, ouvrez une nouvelle fenêtre PowerShell et exécutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="51e66-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="51e66-110">Il exécute une commande PowerShell qui génère un nombre à chaque minute pendant 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="51e66-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="51e66-111">Afficher le processus</span><span class="sxs-lookup"><span data-stu-id="51e66-111">View the process</span></span>

<span data-ttu-id="51e66-112">Le corps de la commande qui est l’exécution de PowerShell est stocké dans le **CommandLine** propriété de la [Win32_Process][] classe.</span><span class="sxs-lookup"><span data-stu-id="51e66-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="51e66-113">Si la commande est un [encodé commande][], le **CommandLine** propriété contient la chaîne « EncodedCommand ».</span><span class="sxs-lookup"><span data-stu-id="51e66-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="51e66-114">À l’aide de ces informations, la commande encodée peut être dé-obfusquée via le processus suivant.</span><span class="sxs-lookup"><span data-stu-id="51e66-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="51e66-115">Démarrez PowerShell en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="51e66-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="51e66-116">Il est essentiel que PowerShell s’exécute en tant qu’administrateur, sinon aucun résultats ne sont retournés lors de l’interrogation les processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="51e66-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="51e66-117">Exécutez la commande suivante pour obtenir tous les processus PowerShell ayant une commande codée :</span><span class="sxs-lookup"><span data-stu-id="51e66-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="51e66-118">La commande suivante crée un objet PowerShell personnalisé qui contient l’ID de processus et de la commande encodée.</span><span class="sxs-lookup"><span data-stu-id="51e66-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="51e66-119">Désormais, la commande codée peut être décodée.</span><span class="sxs-lookup"><span data-stu-id="51e66-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="51e66-120">L’extrait de code suivant effectue une itération sur l’objet de détails de commande décode la commande encodée et ajoute la commande décodée à l’objet pour un examen approfondi.</span><span class="sxs-lookup"><span data-stu-id="51e66-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="51e66-121">La commande décodée peut désormais être consultée en sélectionnant la propriété command décodé.</span><span class="sxs-lookup"><span data-stu-id="51e66-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Planificateur de tâches]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[encodé commande]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
