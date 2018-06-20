---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Gestion des processus avec les applets de commande Process
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: d6d7daa810dce2d476566e4d30f03cc95bf730e6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952492"
---
# <a name="managing-processes-with-process-cmdlets"></a>Gestion des processus avec les applets de commande Process

Les applets de commande Process de Windows PowerShell permettent de gérer des processus locaux et distants dans Windows PowerShell.

## <a name="getting-processes-get-process"></a>Obtention de processus (Get-Process)

Pour obtenir les processus en cours d’exécution sur l’ordinateur local, exécutez l’applet de commande **Get-Process** sans paramètres.

Vous pouvez obtenir des processus particuliers en spécifiant leur nom ou leur ID. La commande suivante obtient le processus Idle :

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

S’il est normal que des applets de commande ne retournent aucune donnée dans certaines situations, lorsque vous spécifiez un processus par son ID, l’applet de commande **Get-Process** génère une erreur si elle ne trouve aucune correspondance, car l’objectif consiste généralement à récupérer un processus en cours d’exécution connu. Si aucun processus ne correspond à cet ID, il est probable que celui-ci est incorrect ou que son exécution est déjà terminée :

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Vous pouvez utiliser le paramètre Name de l’applet de commande Get-Process pour spécifier une partie des processus en se basant sur le nom des processus. Le paramètre Name peut prendre plusieurs noms dans une liste de valeurs séparées par des virgules. Comme il prend en charge l’utilisation de caractères génériques, vous pouvez entrer des modèles de noms.

Par exemple, la commande suivante obtient les processus dont les noms commencent par « ex ».

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Étant donné que la classe System.Diagnostics.Process de .NET constitue la base des processus Windows PowerShell, elle suit certaines des conventions utilisées par System.Diagnostics.Process. L’une de ces conventions est que le nom de processus d’un exécutable n’inclut jamais « .exe » à la fin du nom.

L’applet de commande **Get-Process** accepte également plusieurs valeurs pour le paramètre Name.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Vous pouvez utiliser le paramètre ComputerName de l’applet de commande Get-Process pour obtenir des processus sur des ordinateurs distants. Par exemple, la commande suivante obtient les processus PowerShell sur l’ordinateur local (représenté par « localhost ») et sur deux ordinateurs distants.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Les noms d’ordinateurs ne sont pas évidents dans cet affichage, mais ils sont stockés dans la propriété MachineName des objets de processus que l’applet de commande Get-Process retourne. La commande suivante utilise l’applet de commande Format-Table pour afficher les propriétés d’ID de processus, ProcessName et MachineName (ComputerName) des objets de processus.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Cette commande plus complexe ajoute la propriété MachineName à l’affichage standard de l’applet de commande Get-Process.

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $() {$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Arrêt des processus (Stop-Process)

Windows PowerShell offre une flexibilité certaine pour l’affichage des processus, mais qu’en est-il de l’arrêt d’un processus ?

L’applet de commande **Stop-Process** prend un nom ou un ID pour spécifier un processus à arrêter. Votre capacité à arrêter des processus dépend des autorisations dont vous disposez. Certains processus ne peuvent pas être arrêtés. Par exemple, si vous essayez d’arrêter le processus inactif, vous obtenez une erreur :

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

Vous pouvez également forcer l’affichage d’une invite avec le paramètre **Confirm**. Ce paramètre est particulièrement utile si vous utilisez un caractère générique quand vous spécifiez le nom du processus, car vous pouvez accidentellement établir une correspondance avec des processus que vous ne souhaitez pas arrêter :

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

Une manipulation de processus complexes est possible en utilisant certaines applets de commande de filtrage d’objet. Étant donné qu’un objet Process a une propriété Responding dont la valeur est true quand il ne répond plus, vous pouvez arrêter toutes les applications qui ne répondent pas avec la commande suivante :

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Vous pouvez utiliser la même approche dans d’autres situations. Par exemple, supposons qu’une application de zone de notification secondaire s’exécute automatiquement quand des utilisateurs démarrent une autre application. Il est possible que vous constatiez que cela ne fonctionne pas correctement dans les sessions des services Terminal Server, mais que vous souhaitiez conserver cette approche dans les sessions qui s’exécutent sur la console de l’ordinateur physique. Les sessions connectées au bureau de l’ordinateur physique ayant toujours un ID de session 0, vous pouvez arrêter toutes les instances du processus figurant dans d’autres sessions à l’aide de l’applet de commande **Where-Object** et du processus **SessionId** :

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

L’applet de commande Stop-Process ne prend pas de paramètre ComputerName. Par conséquent, pour exécuter une commande d’arrêt de processus sur un ordinateur distant, vous devez utiliser l’applet de commande Invoke-Command. Par exemple, pour arrêter le processus PowerShell sur l’ordinateur distant Serveur01, tapez :

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Arrêt de toutes les autres sessions Windows PowerShell

Il est parfois utile de pouvoir arrêter toutes les sessions Windows PowerShell en cours d’exécution autres que la session active. Si une session utilise trop de ressources ou n’est pas accessible (par exemple, si elle s’exécute à distance ou dans une autre session de bureau), il se peut que vous ne puissiez pas l’arrêter directement. Toutefois, si vous essayez d’arrêter toutes les sessions en cours d’exécution, il se peut que la session active s’arrête à la place.

Chaque session Windows PowerShell a un PID de variable d’environnement qui contient l’ID du processus Windows PowerShell. Vous pouvez contrôler la valeur de $PID par rapport à l’ID de chaque session, et arrêter uniquement les sessions Windows PowerShell dont l’ID diffère. La commande de pipeline suivante effectue cette opération et retourne la liste des sessions terminées (en raison de l’utilisation du paramètre **PassThru**) :

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

## <a name="starting-debugging-and-waiting-for-processes"></a>Démarrage, débogage et attente de processus

Windows PowerShell comprend également des applets de commande permettant de démarrer (ou redémarrer) un processus, de déboguer un processus, et d’attendre qu’un processus s’achève avant d’exécuter une commande. Pour plus d’informations sur ces applets de commande, voir la rubrique d’aide sur chacune d’elles.

## <a name="see-also"></a>Voir aussi

- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Start-Process](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Wait-Process](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Debug-Process](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)