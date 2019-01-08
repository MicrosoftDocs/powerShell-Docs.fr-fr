---
ms.date: 11/13/2018
keywords: powershell,applet de commande
title: Décoder une commande PowerShell à partir d’un processus en cours d’exécution
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401234"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Décoder une commande PowerShell à partir d’un processus en cours d’exécution

Dans certains cas, vous pouvez avoir un processus en cours d’exécution qui occupe une grande quantité de ressources de PowerShell.
Ce processus peut s’exécuter dans le contexte d’un [Planificateur de tâches][] travail ou un [SQL Server Agent][] travail. S’il existe plusieurs processus PowerShell en cours d’exécution, il peut être difficile de savoir quel processus représente le problème. Cet article explique comment décoder un bloc de script, un processus PowerShell est en cours d’exécution.

## <a name="create-a-long-running-process"></a>Créer un processus à long terme

Pour illustrer ce scénario, ouvrez une nouvelle fenêtre PowerShell et exécutez le code suivant. Il exécute une commande PowerShell qui génère un nombre à chaque minute pendant 10 minutes.

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

## <a name="view-the-process"></a>Afficher le processus

Le corps de la commande qui est l’exécution de PowerShell est stocké dans le **CommandLine** propriété de la [Win32_Process][] classe. Si la commande est un [encodé commande][], le **CommandLine** propriété contient la chaîne « EncodedCommand ». À l’aide de ces informations, la commande encodée peut être dé-obfusquée via le processus suivant.

Démarrez PowerShell en tant qu’administrateur. Il est essentiel que PowerShell s’exécute en tant qu’administrateur, sinon aucun résultats ne sont retournés lors de l’interrogation les processus en cours d’exécution.

Exécutez la commande suivante pour obtenir tous les processus PowerShell ayant une commande codée :

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

La commande suivante crée un objet PowerShell personnalisé qui contient l’ID de processus et de la commande encodée.

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

Désormais, la commande codée peut être décodée. L’extrait de code suivant effectue une itération sur l’objet de détails de commande décode la commande encodée et ajoute la commande décodée à l’objet pour un examen approfondi.

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

La commande décodée peut désormais être consultée en sélectionnant la propriété command décodé.

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
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[encodé commande]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
