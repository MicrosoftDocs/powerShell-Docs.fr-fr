---
description: Décrit comment exécuter des commandes distantes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: d88521eeb2a5a4cd1f7d9e6303b4814b5a1c0bb6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207286"
---
# <a name="about-remote"></a><span data-ttu-id="83d83-104">À propos de</span><span class="sxs-lookup"><span data-stu-id="83d83-104">About Remote</span></span>

## <a name="short-description"></a><span data-ttu-id="83d83-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="83d83-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="83d83-106">Décrit comment exécuter des commandes distantes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83d83-106">Describes how to run remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="83d83-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="83d83-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="83d83-108">Vous pouvez exécuter des commandes à distance sur un seul ordinateur ou sur plusieurs ordinateurs à l’aide d’une connexion temporaire ou permanente.</span><span class="sxs-lookup"><span data-stu-id="83d83-108">You can run remote commands on a single computer or on multiple computers by using a temporary or persistent connection.</span></span> <span data-ttu-id="83d83-109">Vous pouvez également démarrer une session interactive avec un seul ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="83d83-109">You can also start an interactive session with a single remote computer.</span></span>

<span data-ttu-id="83d83-110">Cette rubrique fournit une série d’exemples qui vous montrent comment exécuter différents types de commande à distance.</span><span class="sxs-lookup"><span data-stu-id="83d83-110">This topic provides a series of examples to show you how to run different types of remote command.</span></span> <span data-ttu-id="83d83-111">Après avoir essayé ces commandes de base, lisez les rubriques d’aide qui décrivent chaque applet de commande utilisée dans ces commandes.</span><span class="sxs-lookup"><span data-stu-id="83d83-111">After you try these basic commands, read the Help topics that describe each cmdlet that is used in these commands.</span></span> <span data-ttu-id="83d83-112">Les rubriques fournissent des informations détaillées et expliquent comment vous pouvez modifier les commandes pour répondre à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="83d83-112">The topics provide the details and explain how you can modify the commands to meet your needs.</span></span>

<span data-ttu-id="83d83-113">Remarque : pour utiliser la communication à distance PowerShell, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="83d83-113">Note: To use PowerShell remoting, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="83d83-114">Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d83-114">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="how-to-start-an-interactive-session-enter-pssession"></a><span data-ttu-id="83d83-115">COMMENT DÉMARRER UNE SESSION INTERACTIVE (ENTER-PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="83d83-115">HOW TO START AN INTERACTIVE SESSION (ENTER-PSSESSION)</span></span>

<span data-ttu-id="83d83-116">Le moyen le plus simple d’exécuter des commandes à distance consiste à démarrer une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="83d83-116">The easiest way to run remote commands is to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="83d83-117">Lorsque la session démarre, les commandes que vous tapez s’exécutent sur l’ordinateur distant, comme si vous les tapiiez directement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="83d83-117">When the session starts, the commands that you type run on the remote computer, just as though you typed them directly on the remote computer.</span></span> <span data-ttu-id="83d83-118">Vous ne pouvez vous connecter qu’à un seul ordinateur dans chaque session interactive.</span><span class="sxs-lookup"><span data-stu-id="83d83-118">You can connect to only one computer in each interactive session.</span></span>

<span data-ttu-id="83d83-119">Pour démarrer une session interactive, utilisez l’applet de commande Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="83d83-119">To start an interactive session, use the Enter-PSSession cmdlet.</span></span> <span data-ttu-id="83d83-120">La commande suivante démarre une session interactive avec l’ordinateur SERVEUR01 :</span><span class="sxs-lookup"><span data-stu-id="83d83-120">The following command starts an interactive session with the Server01 computer:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="83d83-121">L’invite de commandes change pour indiquer que vous êtes connecté à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="83d83-121">The command prompt changes to indicate that you are connected to the Server01 computer.</span></span>

```
Server01\PS>
```

<span data-ttu-id="83d83-122">À présent, vous pouvez taper des commandes sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="83d83-122">Now, you can type commands on the Server01 computer.</span></span>

<span data-ttu-id="83d83-123">Pour terminer la session interactive, tapez :</span><span class="sxs-lookup"><span data-stu-id="83d83-123">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="83d83-124">Pour plus d’informations, consultez Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="83d83-124">For more information, see Enter-PSSession.</span></span>

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a><span data-ttu-id="83d83-125">UTILISATION D’APPLETS DE COMMANDE AVEC UN PARAMÈTRE COMPUTERNAME POUR OBTENIR DES DONNÉES DISTANTES</span><span class="sxs-lookup"><span data-stu-id="83d83-125">HOW TO USE CMDLETS THAT HAVE A COMPUTERNAME PARAMETER TO GET REMOTE DATA</span></span>

<span data-ttu-id="83d83-126">Plusieurs applets de commande ont un paramètre ComputerName qui vous permet d’obtenir des objets à partir d’ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="83d83-126">Several cmdlets have a ComputerName parameter that lets you get objects from remote computers.</span></span>

<span data-ttu-id="83d83-127">Étant donné que ces applets de commande n’utilisent pas la communication à distance PowerShell basée sur WS-Management, vous pouvez utiliser le paramètre ComputerName de ces applets de commande sur n’importe quel ordinateur exécutant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83d83-127">Because these cmdlets do not use WS-Management-based PowerShell remoting, you can use the ComputerName parameter of these cmdlets on any computer that is running PowerShell.</span></span> <span data-ttu-id="83d83-128">Les ordinateurs n’ont pas besoin d’être configurés pour la communication à distance PowerShell et les ordinateurs n’ont pas besoin de répondre à la configuration système requise pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="83d83-128">The computers do not have to be configured for PowerShell remoting, and the computers do not have to meet the system requirements for remoting.</span></span>

<span data-ttu-id="83d83-129">Les applets de commande suivantes ont un paramètre ComputerName :</span><span class="sxs-lookup"><span data-stu-id="83d83-129">The following cmdlets have a ComputerName parameter:</span></span>

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

<span data-ttu-id="83d83-130">Par exemple, la commande suivante obtient les services sur l’ordinateur distant SERVEUR01 :</span><span class="sxs-lookup"><span data-stu-id="83d83-130">For example, the following command gets the services on the Server01 remote computer:</span></span>

```powershell
Get-Service -ComputerName Server01
```

<span data-ttu-id="83d83-131">En règle générale, les applets de commande qui prennent en charge la communication à distance sans configuration spéciale ont un paramètre **ComputerName** et n’ont pas de paramètre de **session** .</span><span class="sxs-lookup"><span data-stu-id="83d83-131">Typically, cmdlets that support remoting without special configuration have a **ComputerName** parameter and do not have a **Session** parameter.</span></span> <span data-ttu-id="83d83-132">Pour trouver ces applets de commande dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="83d83-132">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a><span data-ttu-id="83d83-133">COMMENT EXÉCUTER UNE COMMANDE DISTANTE</span><span class="sxs-lookup"><span data-stu-id="83d83-133">HOW TO RUN A REMOTE COMMAND</span></span>

<span data-ttu-id="83d83-134">Pour exécuter d’autres commandes sur des ordinateurs distants, utilisez l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="83d83-134">To run other commands on remote computers, use the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="83d83-135">Pour exécuter une seule commande ou quelques commandes sans rapport, utilisez le paramètre ComputerName de Invoke-Command pour spécifier les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="83d83-135">To run a single command or a few unrelated commands, use the ComputerName parameter of Invoke-Command to specify the remote computers.</span></span> <span data-ttu-id="83d83-136">Utilisez le paramètre ScriptBlock pour spécifier la commande.</span><span class="sxs-lookup"><span data-stu-id="83d83-136">Use the ScriptBlock parameter to specify the command.</span></span>

<span data-ttu-id="83d83-137">Par exemple, la commande suivante exécute une commande Get-Culture sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="83d83-137">For example, the following command runs a Get-Culture command on the Server01 computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="83d83-138">Le paramètre ComputerName est conçu pour la situation dans laquelle vous exécutez une commande unique ou plusieurs commandes non liées sur un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="83d83-138">The ComputerName parameter is designed for situation in which you run a single command or several unrelated commands on one or many computers.</span></span> <span data-ttu-id="83d83-139">Pour établir une connexion permanente à un ordinateur distant, utilisez le paramètre session.</span><span class="sxs-lookup"><span data-stu-id="83d83-139">To establish a persistent connection to a remote computer, use the Session parameter.</span></span>

## <a name="how-to-create-a-persistent-connection-pssession"></a><span data-ttu-id="83d83-140">COMMENT CRÉER UNE CONNEXION PERMANENTE (PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="83d83-140">HOW TO CREATE A PERSISTENT CONNECTION (PSSESSION)</span></span>

<span data-ttu-id="83d83-141">Quand vous utilisez le paramètre ComputerName de l’applet de commande Invoke-Command, Windows PowerShell établit une connexion uniquement pour la commande.</span><span class="sxs-lookup"><span data-stu-id="83d83-141">When you use the ComputerName parameter of the Invoke-Command cmdlet, Windows PowerShell establishes a connection just for the command.</span></span> <span data-ttu-id="83d83-142">Ensuite, il ferme la connexion quand la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="83d83-142">Then, it closes the connection when the command is complete.</span></span> <span data-ttu-id="83d83-143">Toutes les variables ou fonctions définies dans la commande sont perdues.</span><span class="sxs-lookup"><span data-stu-id="83d83-143">Any variables or functions that are defined in the command are lost.</span></span>

<span data-ttu-id="83d83-144">Pour créer une connexion permanente à un ordinateur distant, utilisez l’applet de commande New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="83d83-144">To create a persistent connection to a remote computer, use the New-PSSession cmdlet.</span></span> <span data-ttu-id="83d83-145">Par exemple, la commande suivante crée sessions PSSession sur les ordinateurs SERVEUR01 et Server02, puis enregistre le sessions PSSession dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="83d83-145">For example, the following command creates PSSessions on the Server01 and Server02 computers and then saves the PSSessions in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="83d83-146">COMMENT EXÉCUTER DES COMMANDES DANS UNE SESSION PSSESSION</span><span class="sxs-lookup"><span data-stu-id="83d83-146">HOW TO RUN COMMANDS IN A PSSESSION</span></span>

<span data-ttu-id="83d83-147">Avec PSSession, vous pouvez exécuter une série de commandes distantes qui partagent des données, comme des fonctions, des alias et des valeurs de variables.</span><span class="sxs-lookup"><span data-stu-id="83d83-147">With a PSSession, you can run a series of remote commands that share data, like functions, aliases, and the values of variables.</span></span> <span data-ttu-id="83d83-148">Pour exécuter des commandes dans une session PSSession, utilisez le paramètre session de l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="83d83-148">To run commands in a PSSession, use the Session parameter of the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="83d83-149">Par exemple, la commande suivante utilise l’applet de commande Invoke-Command pour exécuter une commande Get-Process dans le sessions PSSession sur les ordinateurs SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="83d83-149">For example, the following command uses the Invoke-Command cmdlet to run a Get-Process command in the PSSessions on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="83d83-150">La commande enregistre les processus dans une variable $p dans chaque session PSSession.</span><span class="sxs-lookup"><span data-stu-id="83d83-150">The command saves the processes in a $p variable in each PSSession.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

<span data-ttu-id="83d83-151">Étant donné que la session PSSession utilise une connexion permanente, vous pouvez exécuter une autre commande dans la même session PSSession qui utilise la variable $p.</span><span class="sxs-lookup"><span data-stu-id="83d83-151">Because the PSSession uses a persistent connection, you can run another command in the same PSSession that uses the $p variable.</span></span> <span data-ttu-id="83d83-152">La commande suivante compte le nombre de processus enregistrés dans $p.</span><span class="sxs-lookup"><span data-stu-id="83d83-152">The following command counts the number of processes saved in $p.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a><span data-ttu-id="83d83-153">COMMENT EXÉCUTER UNE COMMANDE À DISTANCE SUR PLUSIEURS ORDINATEURS</span><span class="sxs-lookup"><span data-stu-id="83d83-153">HOW TO RUN A REMOTE COMMAND ON MULTIPLE COMPUTERS</span></span>

<span data-ttu-id="83d83-154">Pour exécuter une commande à distance sur plusieurs ordinateurs, tapez tous les noms d’ordinateur dans la valeur du paramètre ComputerName de Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="83d83-154">To run a remote command on multiple computers, type all of the computer names in the value of the ComputerName parameter of Invoke-Command.</span></span> <span data-ttu-id="83d83-155">Séparez les noms par des virgules.</span><span class="sxs-lookup"><span data-stu-id="83d83-155">Separate the names with commas.</span></span>

<span data-ttu-id="83d83-156">Par exemple, la commande suivante exécute une commande Get-Culture sur trois ordinateurs :</span><span class="sxs-lookup"><span data-stu-id="83d83-156">For example, the following command runs a Get-Culture command on three computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="83d83-157">Vous pouvez également exécuter une commande dans plusieurs sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="83d83-157">You can also run a command in multiple PSSessions.</span></span> <span data-ttu-id="83d83-158">Les commandes suivantes créent des sessions PSSession sur les ordinateurs Serveur01, Server02 et Server03, puis exécutent une commande Get-Culture dans chacun des sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="83d83-158">The following commands create PSSessions on the Server01, Server02, and Server03 computers and then run a Get-Culture command in each of the PSSessions.</span></span>

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="83d83-159">Pour inclure la liste des ordinateurs locaux, tapez le nom de l’ordinateur local, tapez un point (.) ou tapez « localhost ».</span><span class="sxs-lookup"><span data-stu-id="83d83-159">To include the local computer list of computers, type the name of the local computer, type a dot (.), or type  "localhost".</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a><span data-ttu-id="83d83-160">COMMENT EXÉCUTER UN SCRIPT SUR DES ORDINATEURS DISTANTS</span><span class="sxs-lookup"><span data-stu-id="83d83-160">HOW TO RUN A SCRIPT ON REMOTE COMPUTERS</span></span>

<span data-ttu-id="83d83-161">Pour exécuter un script local sur des ordinateurs distants, utilisez le paramètre FilePath de Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="83d83-161">To run a local script on remote computers, use the FilePath parameter of Invoke-Command.</span></span>

<span data-ttu-id="83d83-162">Par exemple, la commande suivante exécute le script Sample.ps1 sur les ordinateurs S1 et S2 :</span><span class="sxs-lookup"><span data-stu-id="83d83-162">For example, the following command runs the Sample.ps1 script on the S1 and S2 computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

<span data-ttu-id="83d83-163">Les résultats du script sont retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="83d83-163">The results of the script are returned to the local computer.</span></span> <span data-ttu-id="83d83-164">Vous n’avez pas besoin de copier des fichiers.</span><span class="sxs-lookup"><span data-stu-id="83d83-164">You do not need to copy any files.</span></span>

## <a name="how-to-stop-a-remote-command"></a><span data-ttu-id="83d83-165">COMMENT ARRÊTER UNE COMMANDE À DISTANCE</span><span class="sxs-lookup"><span data-stu-id="83d83-165">HOW TO STOP A REMOTE COMMAND</span></span>

<span data-ttu-id="83d83-166">Pour interrompre une commande, appuyez sur CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="83d83-166">To interrupt a command, press CTRL+C.</span></span> <span data-ttu-id="83d83-167">La demande d’interruption est transmise à l’ordinateur distant où elle met fin à la commande distante.</span><span class="sxs-lookup"><span data-stu-id="83d83-167">The interrupt request is passed to the remote computer where it terminates the remote command.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="83d83-168">POUR PLUS D’INFORMATIONS</span><span class="sxs-lookup"><span data-stu-id="83d83-168">FOR MORE INFORMATION</span></span>

- <span data-ttu-id="83d83-169">Pour plus d’informations sur la configuration système requise pour la communication à distance, consultez [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d83-169">For information about the system requirements for remoting, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

- <span data-ttu-id="83d83-170">Pour obtenir de l’aide sur la mise en forme de la sortie à distance, consultez [about_Remote_Output](about_Remote_Output.md).</span><span class="sxs-lookup"><span data-stu-id="83d83-170">For help in formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

- <span data-ttu-id="83d83-171">Pour plus d’informations sur le fonctionnement de la communication à distance, la gestion des données distantes, les configurations spéciales, les problèmes de sécurité et d’autres questions fréquemment posées, consultez [about_Remote_FAQ](about_Remote_FAQ.md).</span><span class="sxs-lookup"><span data-stu-id="83d83-171">For information about how remoting works, how to manage remote data, special configurations, security issues, and other frequently asked questions, see [about_Remote_FAQ](about_Remote_FAQ.md).</span></span>

- <span data-ttu-id="83d83-172">Pour obtenir de l’aide sur la résolution des erreurs de communication à distance, consultez about_Remote_Troubleshooting.</span><span class="sxs-lookup"><span data-stu-id="83d83-172">For help in resolving remoting errors, see about_Remote_Troubleshooting.</span></span>

- <span data-ttu-id="83d83-173">Pour plus d’informations sur les sessions PSSession et les connexions persistantes, consultez [about_PSSessions](about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="83d83-173">For information about PSSessions and persistent connections, see [about_PSSessions](about_PSSessions.md).</span></span>

- <span data-ttu-id="83d83-174">Pour plus d’informations sur les travaux en arrière-plan PowerShell, voir [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="83d83-174">For information about PowerShell background jobs, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="83d83-175">MOT</span><span class="sxs-lookup"><span data-stu-id="83d83-175">KEYWORDS</span></span>

<span data-ttu-id="83d83-176">about_Remoting</span><span class="sxs-lookup"><span data-stu-id="83d83-176">about_Remoting</span></span>

## <a name="see-also"></a><span data-ttu-id="83d83-177">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="83d83-177">SEE ALSO</span></span>

[<span data-ttu-id="83d83-178">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="83d83-178">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="83d83-179">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="83d83-179">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="83d83-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="83d83-180">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="83d83-181">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="83d83-181">about_Remote_FAQ</span></span>](about_Remote_FAQ.md)

[<span data-ttu-id="83d83-182">about_Remote_TroubleShooting</span><span class="sxs-lookup"><span data-stu-id="83d83-182">about_Remote_TroubleShooting</span></span>](about_Remote_TroubleShooting.md)

[<span data-ttu-id="83d83-183">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="83d83-183">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="83d83-184">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="83d83-184">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="83d83-185">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="83d83-185">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="83d83-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="83d83-186">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

