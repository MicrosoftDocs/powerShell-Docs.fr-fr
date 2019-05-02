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
# <a name="decode-a-powershell-command-from-a-running-process"></a>Décoder une commande PowerShell à partir d’un processus en cours d’exécution

Il peut arriver qu’un processus PowerShell en cours d’exécution
dans le contexte d’un travail [Planificateur de tâches][] ou [SQL Server Agent][] demande une grande quantité de ressources. Si plusieurs processus PowerShell sont en cours d’exécution, il peut être difficile de savoir lequel pose problème. Cet article explique comment décoder un bloc de script exécuté par un processus PowerShell.

## <a name="create-a-long-running-process"></a>Créer un processus long

Pour illustrer ce scénario, ouvrez une nouvelle fenêtre PowerShell et exécutez le code suivant. Il exécute une commande PowerShell qui génère un nombre par minute pendant 10 minutes.

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

Le corps de la commande exécuté par PowerShell est stocké dans la propriété **CommandLine** de la classe [Win32_Process][]. S’il s’agit d’une [commande encodée][], la propriété **CommandLine** contient la chaîne « EncodedCommand ». Ces informations permettent de révéler la commande encodée suivant le processus ci-dessous.

Lancez PowerShell en tant qu’administrateur. Il est essentiel que PowerShell s’exécute en mode administrateur ; sinon, aucun résultat ne sera retourné dans la liste des processus en cours d’exécution.

Exécutez la commande suivante pour obtenir tous les processus PowerShell comportant une commande encodée :

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

La commande suivante crée un objet PowerShell personnalisé contenant l’identificateur de processus et la commande encodée.

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

Il est maintenant possible de décoder la commande encodée. L’extrait de code suivant effectue une itération sur l’objet de détails de la commande, décode la commande encodée et rajoute la commande décodée à l’objet en vue d’un examen approfondi.

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

Il est maintenant possible de consulter la commande décodée en sélectionnant la propriété DecodedCommand.

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
[Commande encodée]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
