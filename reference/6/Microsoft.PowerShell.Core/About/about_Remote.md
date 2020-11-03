---
description: Décrit comment exécuter des commandes distantes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: 04c297f849a30ddabecec98a5a2250b8d9b3fbfa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206934"
---
# <a name="about-remote"></a>À propos de

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit comment exécuter des commandes distantes dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Vous pouvez exécuter des commandes à distance sur un seul ordinateur ou sur plusieurs ordinateurs à l’aide d’une connexion temporaire ou permanente. Vous pouvez également démarrer une session interactive avec un seul ordinateur distant.

Cette rubrique fournit une série d’exemples qui vous montrent comment exécuter différents types de commande à distance. Après avoir essayé ces commandes de base, lisez les rubriques d’aide qui décrivent chaque applet de commande utilisée dans ces commandes. Les rubriques fournissent des informations détaillées et expliquent comment vous pouvez modifier les commandes pour répondre à vos besoins.

Remarque : pour utiliser la communication à distance PowerShell, les ordinateurs locaux et distants doivent être configurés pour la communication à distance. Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).

## <a name="how-to-start-an-interactive-session-enter-pssession"></a>COMMENT DÉMARRER UNE SESSION INTERACTIVE (ENTER-PSSESSION)

Le moyen le plus simple d’exécuter des commandes à distance consiste à démarrer une session interactive avec un ordinateur distant.

Lorsque la session démarre, les commandes que vous tapez s’exécutent sur l’ordinateur distant, comme si vous les tapiiez directement sur l’ordinateur distant. Vous ne pouvez vous connecter qu’à un seul ordinateur dans chaque session interactive.

Pour démarrer une session interactive, utilisez l’applet de commande Enter-PSSession. La commande suivante démarre une session interactive avec l’ordinateur SERVEUR01 :

```powershell
Enter-PSSession Server01
```

L’invite de commandes change pour indiquer que vous êtes connecté à l’ordinateur SERVEUR01.

```
Server01\PS>
```

À présent, vous pouvez taper des commandes sur l’ordinateur SERVEUR01.

Pour terminer la session interactive, tapez :

```powershell
Exit-PSSession
```

Pour plus d’informations, consultez Enter-PSSession.

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a>UTILISATION D’APPLETS DE COMMANDE AVEC UN PARAMÈTRE COMPUTERNAME POUR OBTENIR DES DONNÉES DISTANTES

Plusieurs applets de commande ont un paramètre ComputerName qui vous permet d’obtenir des objets à partir d’ordinateurs distants.

Étant donné que ces applets de commande n’utilisent pas la communication à distance PowerShell basée sur WS-Management, vous pouvez utiliser le paramètre ComputerName de ces applets de commande sur n’importe quel ordinateur exécutant PowerShell. Les ordinateurs n’ont pas besoin d’être configurés pour la communication à distance PowerShell et les ordinateurs n’ont pas besoin de répondre à la configuration système requise pour la communication à distance.

Les applets de commande suivantes ont un paramètre ComputerName :

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

Par exemple, la commande suivante obtient les services sur l’ordinateur distant SERVEUR01 :

```powershell
Get-Service -ComputerName Server01
```

En règle générale, les applets de commande qui prennent en charge la communication à distance sans configuration spéciale ont un paramètre **ComputerName** et n’ont pas de paramètre de **session** . Pour trouver ces applets de commande dans votre session, tapez :

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a>COMMENT EXÉCUTER UNE COMMANDE DISTANTE

Pour exécuter d’autres commandes sur des ordinateurs distants, utilisez l’applet de commande Invoke-Command.

Pour exécuter une seule commande ou quelques commandes sans rapport, utilisez le paramètre ComputerName de Invoke-Command pour spécifier les ordinateurs distants. Utilisez le paramètre ScriptBlock pour spécifier la commande.

Par exemple, la commande suivante exécute une commande Get-Culture sur l’ordinateur SERVEUR01.

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

Le paramètre ComputerName est conçu pour la situation dans laquelle vous exécutez une commande unique ou plusieurs commandes non liées sur un ou plusieurs ordinateurs. Pour établir une connexion permanente à un ordinateur distant, utilisez le paramètre session.

## <a name="how-to-create-a-persistent-connection-pssession"></a>COMMENT CRÉER UNE CONNEXION PERMANENTE (PSSESSION)

Quand vous utilisez le paramètre ComputerName de l’applet de commande Invoke-Command, Windows PowerShell établit une connexion uniquement pour la commande. Ensuite, il ferme la connexion quand la commande est terminée. Toutes les variables ou fonctions définies dans la commande sont perdues.

Pour créer une connexion permanente à un ordinateur distant, utilisez l’applet de commande New-PSSession. Par exemple, la commande suivante crée sessions PSSession sur les ordinateurs SERVEUR01 et Server02, puis enregistre le sessions PSSession dans la variable $s.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a>COMMENT EXÉCUTER DES COMMANDES DANS UNE SESSION PSSESSION

Avec PSSession, vous pouvez exécuter une série de commandes distantes qui partagent des données, comme des fonctions, des alias et des valeurs de variables. Pour exécuter des commandes dans une session PSSession, utilisez le paramètre session de l’applet de commande Invoke-Command.

Par exemple, la commande suivante utilise l’applet de commande Invoke-Command pour exécuter une commande Get-Process dans le sessions PSSession sur les ordinateurs SERVEUR01 et Server02.
La commande enregistre les processus dans une variable $p dans chaque session PSSession.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

Étant donné que la session PSSession utilise une connexion permanente, vous pouvez exécuter une autre commande dans la même session PSSession qui utilise la variable $p. La commande suivante compte le nombre de processus enregistrés dans $p.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a>COMMENT EXÉCUTER UNE COMMANDE À DISTANCE SUR PLUSIEURS ORDINATEURS

Pour exécuter une commande à distance sur plusieurs ordinateurs, tapez tous les noms d’ordinateur dans la valeur du paramètre ComputerName de Invoke-Command. Séparez les noms par des virgules.

Par exemple, la commande suivante exécute une commande Get-Culture sur trois ordinateurs :

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

Vous pouvez également exécuter une commande dans plusieurs sessions PSSession. Les commandes suivantes créent des sessions PSSession sur les ordinateurs Serveur01, Server02 et Server03, puis exécutent une commande Get-Culture dans chacun des sessions PSSession.

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

Pour inclure la liste des ordinateurs locaux, tapez le nom de l’ordinateur local, tapez un point (.) ou tapez « localhost ».

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a>COMMENT EXÉCUTER UN SCRIPT SUR DES ORDINATEURS DISTANTS

Pour exécuter un script local sur des ordinateurs distants, utilisez le paramètre FilePath de Invoke-Command.

Par exemple, la commande suivante exécute le script Sample.ps1 sur les ordinateurs S1 et S2 :

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

Les résultats du script sont retournés à l’ordinateur local. Vous n’avez pas besoin de copier des fichiers.

## <a name="how-to-stop-a-remote-command"></a>COMMENT ARRÊTER UNE COMMANDE À DISTANCE

Pour interrompre une commande, appuyez sur CTRL + C. La demande d’interruption est transmise à l’ordinateur distant où elle met fin à la commande distante.

## <a name="for-more-information"></a>POUR PLUS D’INFORMATIONS

- Pour plus d’informations sur la configuration système requise pour la communication à distance, consultez [about_Remote_Requirements](about_Remote_Requirements.md).

- Pour obtenir de l’aide sur la mise en forme de la sortie à distance, consultez [about_Remote_Output](about_Remote_Output.md).

- Pour plus d’informations sur le fonctionnement de la communication à distance, la gestion des données distantes, les configurations spéciales, les problèmes de sécurité et d’autres questions fréquemment posées, consultez [about_Remote_FAQ](about_Remote_FAQ.md).

- Pour obtenir de l’aide sur la résolution des erreurs de communication à distance, consultez about_Remote_Troubleshooting.

- Pour plus d’informations sur les sessions PSSession et les connexions persistantes, consultez [about_PSSessions](about_PSSessions.md).

- Pour plus d’informations sur les travaux en arrière-plan PowerShell, voir [about_Jobs](about_Jobs.md).

## <a name="keywords"></a>MOT

about_Remoting

## <a name="see-also"></a>VOIR AUSSI

[about_PSSessions](about_PSSessions.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_FAQ](about_Remote_FAQ.md)

[about_Remote_TroubleShooting](about_Remote_TroubleShooting.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
