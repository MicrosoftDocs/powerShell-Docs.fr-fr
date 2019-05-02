---
ms.date: 11/13/2018
keywords: powershell,applet de commande
title: Décoder une commande PowerShell à partir d’un processus en cours d’exécution
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086236"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="4ee18-103">Décoder une commande PowerShell à partir d’un processus en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="4ee18-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="4ee18-104">Il peut arriver qu’un processus PowerShell en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="4ee18-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="4ee18-105">dans le contexte d’un travail [Planificateur de tâches][] ou [SQL Server Agent][] demande une grande quantité de ressources.</span><span class="sxs-lookup"><span data-stu-id="4ee18-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="4ee18-106">Si plusieurs processus PowerShell sont en cours d’exécution, il peut être difficile de savoir lequel pose problème.</span><span class="sxs-lookup"><span data-stu-id="4ee18-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="4ee18-107">Cet article explique comment décoder un bloc de script exécuté par un processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ee18-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="4ee18-108">Créer un processus long</span><span class="sxs-lookup"><span data-stu-id="4ee18-108">Create a long running process</span></span>

<span data-ttu-id="4ee18-109">Pour illustrer ce scénario, ouvrez une nouvelle fenêtre PowerShell et exécutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4ee18-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="4ee18-110">Il exécute une commande PowerShell qui génère un nombre par minute pendant 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="4ee18-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

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

## <a name="view-the-process"></a><span data-ttu-id="4ee18-111">Afficher le processus</span><span class="sxs-lookup"><span data-stu-id="4ee18-111">View the process</span></span>

<span data-ttu-id="4ee18-112">Le corps de la commande exécuté par PowerShell est stocké dans la propriété **CommandLine** de la classe [Win32_Process][].</span><span class="sxs-lookup"><span data-stu-id="4ee18-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="4ee18-113">S’il s’agit d’une [commande encodée][], la propriété **CommandLine** contient la chaîne « EncodedCommand ».</span><span class="sxs-lookup"><span data-stu-id="4ee18-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="4ee18-114">Ces informations permettent de révéler la commande encodée suivant le processus ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="4ee18-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="4ee18-115">Lancez PowerShell en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="4ee18-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="4ee18-116">Il est essentiel que PowerShell s’exécute en mode administrateur ; sinon, aucun résultat ne sera retourné dans la liste des processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4ee18-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="4ee18-117">Exécutez la commande suivante pour obtenir tous les processus PowerShell comportant une commande encodée :</span><span class="sxs-lookup"><span data-stu-id="4ee18-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="4ee18-118">La commande suivante crée un objet PowerShell personnalisé contenant l’identificateur de processus et la commande encodée.</span><span class="sxs-lookup"><span data-stu-id="4ee18-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

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

<span data-ttu-id="4ee18-119">Il est maintenant possible de décoder la commande encodée.</span><span class="sxs-lookup"><span data-stu-id="4ee18-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="4ee18-120">L’extrait de code suivant effectue une itération sur l’objet de détails de la commande, décode la commande encodée et rajoute la commande décodée à l’objet en vue d’un examen approfondi.</span><span class="sxs-lookup"><span data-stu-id="4ee18-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

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

<span data-ttu-id="4ee18-121">Il est maintenant possible de consulter la commande décodée en sélectionnant la propriété DecodedCommand.</span><span class="sxs-lookup"><span data-stu-id="4ee18-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

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
[Commande encodée]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
