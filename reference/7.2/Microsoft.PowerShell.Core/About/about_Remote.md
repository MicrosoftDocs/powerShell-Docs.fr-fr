---
description: Décrit comment exécuter des commandes distantes dans PowerShell.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: b47efbaaebdd75be5f15be449e194113a0d6ebd7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603881"
---
# <a name="about-remote"></a><span data-ttu-id="066f0-103">À propos de</span><span class="sxs-lookup"><span data-stu-id="066f0-103">About Remote</span></span>

## <a name="short-description"></a><span data-ttu-id="066f0-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="066f0-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="066f0-105">Décrit comment exécuter des commandes distantes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="066f0-105">Describes how to run remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="066f0-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="066f0-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="066f0-107">Vous pouvez exécuter des commandes à distance sur un seul ordinateur ou sur plusieurs ordinateurs à l’aide d’une connexion temporaire ou permanente.</span><span class="sxs-lookup"><span data-stu-id="066f0-107">You can run remote commands on a single computer or on multiple computers by using a temporary or persistent connection.</span></span> <span data-ttu-id="066f0-108">Vous pouvez également démarrer une session interactive avec un seul ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="066f0-108">You can also start an interactive session with a single remote computer.</span></span>

<span data-ttu-id="066f0-109">Cette rubrique fournit une série d’exemples qui vous montrent comment exécuter différents types de commande à distance.</span><span class="sxs-lookup"><span data-stu-id="066f0-109">This topic provides a series of examples to show you how to run different types of remote command.</span></span> <span data-ttu-id="066f0-110">Après avoir essayé ces commandes de base, lisez les rubriques d’aide qui décrivent chaque applet de commande utilisée dans ces commandes.</span><span class="sxs-lookup"><span data-stu-id="066f0-110">After you try these basic commands, read the Help topics that describe each cmdlet that is used in these commands.</span></span> <span data-ttu-id="066f0-111">Les rubriques fournissent des informations détaillées et expliquent comment vous pouvez modifier les commandes pour répondre à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="066f0-111">The topics provide the details and explain how you can modify the commands to meet your needs.</span></span>

<span data-ttu-id="066f0-112">Remarque : pour utiliser la communication à distance PowerShell, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="066f0-112">Note: To use PowerShell remoting, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="066f0-113">Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="066f0-113">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="how-to-start-an-interactive-session-enter-pssession"></a><span data-ttu-id="066f0-114">COMMENT DÉMARRER UNE SESSION INTERACTIVE (ENTER-PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="066f0-114">HOW TO START AN INTERACTIVE SESSION (ENTER-PSSESSION)</span></span>

<span data-ttu-id="066f0-115">Le moyen le plus simple d’exécuter des commandes à distance consiste à démarrer une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="066f0-115">The easiest way to run remote commands is to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="066f0-116">Lorsque la session démarre, les commandes que vous tapez s’exécutent sur l’ordinateur distant, comme si vous les tapiiez directement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="066f0-116">When the session starts, the commands that you type run on the remote computer, just as though you typed them directly on the remote computer.</span></span> <span data-ttu-id="066f0-117">Vous ne pouvez vous connecter qu’à un seul ordinateur dans chaque session interactive.</span><span class="sxs-lookup"><span data-stu-id="066f0-117">You can connect to only one computer in each interactive session.</span></span>

<span data-ttu-id="066f0-118">Pour démarrer une session interactive, utilisez l’applet de commande Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="066f0-118">To start an interactive session, use the Enter-PSSession cmdlet.</span></span> <span data-ttu-id="066f0-119">La commande suivante démarre une session interactive avec l’ordinateur SERVEUR01 :</span><span class="sxs-lookup"><span data-stu-id="066f0-119">The following command starts an interactive session with the Server01 computer:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="066f0-120">L’invite de commandes change pour indiquer que vous êtes connecté à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="066f0-120">The command prompt changes to indicate that you are connected to the Server01 computer.</span></span>

```
Server01\PS>
```

<span data-ttu-id="066f0-121">À présent, vous pouvez taper des commandes sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="066f0-121">Now, you can type commands on the Server01 computer.</span></span>

<span data-ttu-id="066f0-122">Pour terminer la session interactive, tapez :</span><span class="sxs-lookup"><span data-stu-id="066f0-122">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="066f0-123">Pour plus d’informations, consultez Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="066f0-123">For more information, see Enter-PSSession.</span></span>

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a><span data-ttu-id="066f0-124">UTILISATION D’APPLETS DE COMMANDE AVEC UN PARAMÈTRE COMPUTERNAME POUR OBTENIR DES DONNÉES DISTANTES</span><span class="sxs-lookup"><span data-stu-id="066f0-124">HOW TO USE CMDLETS THAT HAVE A COMPUTERNAME PARAMETER TO GET REMOTE DATA</span></span>

<span data-ttu-id="066f0-125">Plusieurs applets de commande ont un paramètre ComputerName qui vous permet d’obtenir des objets à partir d’ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="066f0-125">Several cmdlets have a ComputerName parameter that lets you get objects from remote computers.</span></span>

<span data-ttu-id="066f0-126">Étant donné que ces applets de commande n’utilisent pas la communication à distance PowerShell basée sur WS-Management, vous pouvez utiliser le paramètre ComputerName de ces applets de commande sur n’importe quel ordinateur exécutant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="066f0-126">Because these cmdlets do not use WS-Management-based PowerShell remoting, you can use the ComputerName parameter of these cmdlets on any computer that is running PowerShell.</span></span> <span data-ttu-id="066f0-127">Les ordinateurs n’ont pas besoin d’être configurés pour la communication à distance PowerShell et les ordinateurs n’ont pas besoin de répondre à la configuration système requise pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="066f0-127">The computers do not have to be configured for PowerShell remoting, and the computers do not have to meet the system requirements for remoting.</span></span>

<span data-ttu-id="066f0-128">Les applets de commande suivantes ont un paramètre ComputerName :</span><span class="sxs-lookup"><span data-stu-id="066f0-128">The following cmdlets have a ComputerName parameter:</span></span>

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

<span data-ttu-id="066f0-129">Par exemple, la commande suivante obtient les services sur l’ordinateur distant SERVEUR01 :</span><span class="sxs-lookup"><span data-stu-id="066f0-129">For example, the following command gets the services on the Server01 remote computer:</span></span>

```powershell
Get-Service -ComputerName Server01
```

<span data-ttu-id="066f0-130">En règle générale, les applets de commande qui prennent en charge la communication à distance sans configuration spéciale ont un paramètre **ComputerName** et n’ont pas de paramètre de **session** .</span><span class="sxs-lookup"><span data-stu-id="066f0-130">Typically, cmdlets that support remoting without special configuration have a **ComputerName** parameter and do not have a **Session** parameter.</span></span> <span data-ttu-id="066f0-131">Pour trouver ces applets de commande dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="066f0-131">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a><span data-ttu-id="066f0-132">COMMENT EXÉCUTER UNE COMMANDE DISTANTE</span><span class="sxs-lookup"><span data-stu-id="066f0-132">HOW TO RUN A REMOTE COMMAND</span></span>

<span data-ttu-id="066f0-133">Pour exécuter d’autres commandes sur des ordinateurs distants, utilisez l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="066f0-133">To run other commands on remote computers, use the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="066f0-134">Pour exécuter une seule commande ou quelques commandes sans rapport, utilisez le paramètre ComputerName de Invoke-Command pour spécifier les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="066f0-134">To run a single command or a few unrelated commands, use the ComputerName parameter of Invoke-Command to specify the remote computers.</span></span> <span data-ttu-id="066f0-135">Utilisez le paramètre ScriptBlock pour spécifier la commande.</span><span class="sxs-lookup"><span data-stu-id="066f0-135">Use the ScriptBlock parameter to specify the command.</span></span>

<span data-ttu-id="066f0-136">Par exemple, la commande suivante exécute une commande Get-Culture sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="066f0-136">For example, the following command runs a Get-Culture command on the Server01 computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="066f0-137">Le paramètre ComputerName est conçu pour la situation dans laquelle vous exécutez une commande unique ou plusieurs commandes non liées sur un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="066f0-137">The ComputerName parameter is designed for situation in which you run a single command or several unrelated commands on one or many computers.</span></span> <span data-ttu-id="066f0-138">Pour établir une connexion permanente à un ordinateur distant, utilisez le paramètre session.</span><span class="sxs-lookup"><span data-stu-id="066f0-138">To establish a persistent connection to a remote computer, use the Session parameter.</span></span>

## <a name="how-to-create-a-persistent-connection-pssession"></a><span data-ttu-id="066f0-139">COMMENT CRÉER UNE CONNEXION PERMANENTE (PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="066f0-139">HOW TO CREATE A PERSISTENT CONNECTION (PSSESSION)</span></span>

<span data-ttu-id="066f0-140">Quand vous utilisez le paramètre ComputerName de l’applet de commande Invoke-Command, Windows PowerShell établit une connexion uniquement pour la commande.</span><span class="sxs-lookup"><span data-stu-id="066f0-140">When you use the ComputerName parameter of the Invoke-Command cmdlet, Windows PowerShell establishes a connection just for the command.</span></span> <span data-ttu-id="066f0-141">Ensuite, il ferme la connexion quand la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="066f0-141">Then, it closes the connection when the command is complete.</span></span> <span data-ttu-id="066f0-142">Toutes les variables ou fonctions définies dans la commande sont perdues.</span><span class="sxs-lookup"><span data-stu-id="066f0-142">Any variables or functions that are defined in the command are lost.</span></span>

<span data-ttu-id="066f0-143">Pour créer une connexion permanente à un ordinateur distant, utilisez l’applet de commande New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="066f0-143">To create a persistent connection to a remote computer, use the New-PSSession cmdlet.</span></span> <span data-ttu-id="066f0-144">Par exemple, la commande suivante crée sessions PSSession sur les ordinateurs SERVEUR01 et Server02, puis enregistre le sessions PSSession dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="066f0-144">For example, the following command creates PSSessions on the Server01 and Server02 computers and then saves the PSSessions in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="066f0-145">COMMENT EXÉCUTER DES COMMANDES DANS UNE SESSION PSSESSION</span><span class="sxs-lookup"><span data-stu-id="066f0-145">HOW TO RUN COMMANDS IN A PSSESSION</span></span>

<span data-ttu-id="066f0-146">Avec PSSession, vous pouvez exécuter une série de commandes distantes qui partagent des données, comme des fonctions, des alias et des valeurs de variables.</span><span class="sxs-lookup"><span data-stu-id="066f0-146">With a PSSession, you can run a series of remote commands that share data, like functions, aliases, and the values of variables.</span></span> <span data-ttu-id="066f0-147">Pour exécuter des commandes dans une session PSSession, utilisez le paramètre session de l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="066f0-147">To run commands in a PSSession, use the Session parameter of the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="066f0-148">Par exemple, la commande suivante utilise l’applet de commande Invoke-Command pour exécuter une commande Get-Process dans le sessions PSSession sur les ordinateurs SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="066f0-148">For example, the following command uses the Invoke-Command cmdlet to run a Get-Process command in the PSSessions on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="066f0-149">La commande enregistre les processus dans une variable $p dans chaque session PSSession.</span><span class="sxs-lookup"><span data-stu-id="066f0-149">The command saves the processes in a $p variable in each PSSession.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

<span data-ttu-id="066f0-150">Étant donné que la session PSSession utilise une connexion permanente, vous pouvez exécuter une autre commande dans la même session PSSession qui utilise la variable $p.</span><span class="sxs-lookup"><span data-stu-id="066f0-150">Because the PSSession uses a persistent connection, you can run another command in the same PSSession that uses the $p variable.</span></span> <span data-ttu-id="066f0-151">La commande suivante compte le nombre de processus enregistrés dans $p.</span><span class="sxs-lookup"><span data-stu-id="066f0-151">The following command counts the number of processes saved in $p.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a><span data-ttu-id="066f0-152">COMMENT EXÉCUTER UNE COMMANDE À DISTANCE SUR PLUSIEURS ORDINATEURS</span><span class="sxs-lookup"><span data-stu-id="066f0-152">HOW TO RUN A REMOTE COMMAND ON MULTIPLE COMPUTERS</span></span>

<span data-ttu-id="066f0-153">Pour exécuter une commande à distance sur plusieurs ordinateurs, tapez tous les noms d’ordinateur dans la valeur du paramètre ComputerName de Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="066f0-153">To run a remote command on multiple computers, type all of the computer names in the value of the ComputerName parameter of Invoke-Command.</span></span> <span data-ttu-id="066f0-154">Séparez les noms par des virgules.</span><span class="sxs-lookup"><span data-stu-id="066f0-154">Separate the names with commas.</span></span>

<span data-ttu-id="066f0-155">Par exemple, la commande suivante exécute une commande Get-Culture sur trois ordinateurs :</span><span class="sxs-lookup"><span data-stu-id="066f0-155">For example, the following command runs a Get-Culture command on three computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="066f0-156">Vous pouvez également exécuter une commande dans plusieurs sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="066f0-156">You can also run a command in multiple PSSessions.</span></span> <span data-ttu-id="066f0-157">Les commandes suivantes créent des sessions PSSession sur les ordinateurs Serveur01, Server02 et Server03, puis exécutent une commande Get-Culture dans chacun des sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="066f0-157">The following commands create PSSessions on the Server01, Server02, and Server03 computers and then run a Get-Culture command in each of the PSSessions.</span></span>

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="066f0-158">Pour inclure la liste des ordinateurs locaux, tapez le nom de l’ordinateur local, tapez un point (.) ou tapez « localhost ».</span><span class="sxs-lookup"><span data-stu-id="066f0-158">To include the local computer list of computers, type the name of the local computer, type a dot (.), or type  "localhost".</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a><span data-ttu-id="066f0-159">COMMENT EXÉCUTER UN SCRIPT SUR DES ORDINATEURS DISTANTS</span><span class="sxs-lookup"><span data-stu-id="066f0-159">HOW TO RUN A SCRIPT ON REMOTE COMPUTERS</span></span>

<span data-ttu-id="066f0-160">Pour exécuter un script local sur des ordinateurs distants, utilisez le paramètre FilePath de Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="066f0-160">To run a local script on remote computers, use the FilePath parameter of Invoke-Command.</span></span>

<span data-ttu-id="066f0-161">Par exemple, la commande suivante exécute le script Sample.ps1 sur les ordinateurs S1 et S2 :</span><span class="sxs-lookup"><span data-stu-id="066f0-161">For example, the following command runs the Sample.ps1 script on the S1 and S2 computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

<span data-ttu-id="066f0-162">Les résultats du script sont retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="066f0-162">The results of the script are returned to the local computer.</span></span> <span data-ttu-id="066f0-163">Vous n’avez pas besoin de copier des fichiers.</span><span class="sxs-lookup"><span data-stu-id="066f0-163">You do not need to copy any files.</span></span>

## <a name="how-to-stop-a-remote-command"></a><span data-ttu-id="066f0-164">COMMENT ARRÊTER UNE COMMANDE À DISTANCE</span><span class="sxs-lookup"><span data-stu-id="066f0-164">HOW TO STOP A REMOTE COMMAND</span></span>

<span data-ttu-id="066f0-165">Pour interrompre une commande, appuyez sur CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="066f0-165">To interrupt a command, press CTRL+C.</span></span> <span data-ttu-id="066f0-166">La demande d’interruption est transmise à l’ordinateur distant où elle met fin à la commande distante.</span><span class="sxs-lookup"><span data-stu-id="066f0-166">The interrupt request is passed to the remote computer where it terminates the remote command.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="066f0-167">POUR PLUS D’INFORMATIONS</span><span class="sxs-lookup"><span data-stu-id="066f0-167">FOR MORE INFORMATION</span></span>

- <span data-ttu-id="066f0-168">Pour plus d’informations sur la configuration système requise pour la communication à distance, consultez [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="066f0-168">For information about the system requirements for remoting, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

- <span data-ttu-id="066f0-169">Pour obtenir de l’aide sur la mise en forme de la sortie à distance, consultez [about_Remote_Output](about_Remote_Output.md).</span><span class="sxs-lookup"><span data-stu-id="066f0-169">For help in formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

- <span data-ttu-id="066f0-170">Pour plus d’informations sur le fonctionnement de la communication à distance, la gestion des données distantes, les configurations spéciales, les problèmes de sécurité et d’autres questions fréquemment posées, consultez [about_Remote_FAQ](about_Remote_FAQ.md).</span><span class="sxs-lookup"><span data-stu-id="066f0-170">For information about how remoting works, how to manage remote data, special configurations, security issues, and other frequently asked questions, see [about_Remote_FAQ](about_Remote_FAQ.md).</span></span>

- <span data-ttu-id="066f0-171">Pour obtenir de l’aide sur la résolution des erreurs de communication à distance, consultez about_Remote_Troubleshooting.</span><span class="sxs-lookup"><span data-stu-id="066f0-171">For help in resolving remoting errors, see about_Remote_Troubleshooting.</span></span>

- <span data-ttu-id="066f0-172">Pour plus d’informations sur les sessions PSSession et les connexions persistantes, consultez [about_PSSessions](about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="066f0-172">For information about PSSessions and persistent connections, see [about_PSSessions](about_PSSessions.md).</span></span>

- <span data-ttu-id="066f0-173">Pour plus d’informations sur les travaux en arrière-plan PowerShell, voir [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="066f0-173">For information about PowerShell background jobs, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="066f0-174">MOT</span><span class="sxs-lookup"><span data-stu-id="066f0-174">KEYWORDS</span></span>

<span data-ttu-id="066f0-175">about_Remoting</span><span class="sxs-lookup"><span data-stu-id="066f0-175">about_Remoting</span></span>

## <a name="see-also"></a><span data-ttu-id="066f0-176">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="066f0-176">SEE ALSO</span></span>

[<span data-ttu-id="066f0-177">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="066f0-177">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="066f0-178">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="066f0-178">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="066f0-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="066f0-179">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="066f0-180">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="066f0-180">about_Remote_FAQ</span></span>](about_Remote_FAQ.md)

[<span data-ttu-id="066f0-181">about_Remote_TroubleShooting</span><span class="sxs-lookup"><span data-stu-id="066f0-181">about_Remote_TroubleShooting</span></span>](about_Remote_TroubleShooting.md)

[<span data-ttu-id="066f0-182">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="066f0-182">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="066f0-183">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="066f0-183">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="066f0-184">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="066f0-184">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="066f0-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="066f0-185">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

