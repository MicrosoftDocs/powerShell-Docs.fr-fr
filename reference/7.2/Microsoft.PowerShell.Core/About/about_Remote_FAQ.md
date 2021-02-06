---
description: Contient des questions et des réponses sur l’exécution des commandes distantes dans PowerShell.
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: da3516697c58e3273538ed2ed93a7a54fcd9bb49
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598147"
---
# <a name="about-remote-faq"></a><span data-ttu-id="1d1ad-103">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1d1ad-103">About Remote FAQ</span></span>

## <a name="short-description"></a><span data-ttu-id="1d1ad-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="1d1ad-104">Short description</span></span>
<span data-ttu-id="1d1ad-105">Contient des questions et des réponses sur l’exécution des commandes distantes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-105">Contains questions and answers about running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="1d1ad-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="1d1ad-106">Long description</span></span>

<span data-ttu-id="1d1ad-107">Lorsque vous travaillez à distance, vous tapez des commandes dans PowerShell sur un ordinateur (appelé « ordinateur local »), mais les commandes s’exécutent sur un autre ordinateur (appelé « ordinateur distant »).</span><span class="sxs-lookup"><span data-stu-id="1d1ad-107">When you work remotely, you type commands in PowerShell on one computer (known as the "local computer"), but the commands run on another computer (known as the "remote computer").</span></span> <span data-ttu-id="1d1ad-108">L’expérience de travail à distance doit être aussi proche que possible de travailler directement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-108">The experience of working remotely should be as much like working directly at the remote computer as possible.</span></span>

<span data-ttu-id="1d1ad-109">Remarque : pour utiliser la communication à distance PowerShell, l’ordinateur distant doit être configuré pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-109">Note: To use PowerShell remoting, the remote computer must be configured for remoting.</span></span> <span data-ttu-id="1d1ad-110">Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d1ad-110">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="must-both-computers-have-powershell-installed"></a><span data-ttu-id="1d1ad-111">PowerShell doit-il être installé sur les deux ordinateurs ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-111">Must both computers have PowerShell installed?</span></span>

<span data-ttu-id="1d1ad-112">Oui.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-112">Yes.</span></span> <span data-ttu-id="1d1ad-113">Pour travailler à distance, les ordinateurs locaux et distants doivent avoir PowerShell, l’infrastructure Microsoft .NET et le protocole WS-Management (Web Services for Management).</span><span class="sxs-lookup"><span data-stu-id="1d1ad-113">To work remotely, the local and remote computers must have PowerShell, the Microsoft .NET Framework, and the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="1d1ad-114">Tous les fichiers et autres ressources nécessaires pour exécuter une commande particulière doivent se trouver sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-114">Any files and other resources that are needed to execute a particular command must be on the remote computer.</span></span>

<span data-ttu-id="1d1ad-115">Les ordinateurs exécutant Windows PowerShell 3,0 et les ordinateurs exécutant Windows PowerShell 2,0 peuvent se connecter les uns aux autres à distance et exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-115">Computers running Windows PowerShell 3.0 and computers running Windows PowerShell 2.0 can connect to each other remotely and run remote commands.</span></span>
<span data-ttu-id="1d1ad-116">Toutefois, certaines fonctionnalités, telles que la possibilité de se déconnecter d’une session et de se reconnecter, fonctionnent uniquement lorsque les deux ordinateurs exécutent Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-116">However, some features, such as the ability to disconnect from a session and reconnect to it, work only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="1d1ad-117">Vous devez être autorisé à vous connecter à l’ordinateur distant, à exécuter PowerShell et à accéder aux magasins de données (tels que des fichiers et des dossiers) et au registre de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-117">You must have permission to connect to the remote computer, permission to run PowerShell, and permission to access data stores (such as files and folders), and the registry on the remote computer.</span></span>

<span data-ttu-id="1d1ad-118">Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d1ad-118">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="how-does-remoting-work"></a><span data-ttu-id="1d1ad-119">Fonctionnement de la communication à distance</span><span class="sxs-lookup"><span data-stu-id="1d1ad-119">How does remoting work?</span></span>

<span data-ttu-id="1d1ad-120">Lorsque vous envoyez une commande à distance, la commande est transmise via le réseau vers le moteur PowerShell sur l’ordinateur distant, et elle s’exécute dans le client PowerShell sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-120">When you submit a remote command, the command is transmitted across the network to the PowerShell engine on the remote computer, and it runs in the PowerShell client on the remote computer.</span></span> <span data-ttu-id="1d1ad-121">Les résultats de la commande sont renvoyés à l’ordinateur local et s’affichent dans la session PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-121">The command results are sent back to the local computer and appear in the PowerShell session on the local computer.</span></span>

<span data-ttu-id="1d1ad-122">Pour transmettre les commandes et recevoir la sortie, PowerShell utilise le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-122">To transmit the commands and receive the output, PowerShell uses the WS-Management protocol.</span></span> <span data-ttu-id="1d1ad-123">Pour plus d’informations sur le protocole WS-Management, consultez [protocole WS-Management](/windows/win32/winrm/ws-management-protocol) dans la documentation de Windows.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-123">For information about the WS-Management protocol, see [WS-Management Protocol](/windows/win32/winrm/ws-management-protocol) in the Windows documentation.</span></span>

<span data-ttu-id="1d1ad-124">À compter de Windows PowerShell 3,0, les sessions à distance sont stockées sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-124">Beginning in Windows PowerShell 3.0, remote sessions are stored on the remote computer.</span></span> <span data-ttu-id="1d1ad-125">Cela vous permet de vous déconnecter de la session et de vous reconnecter à partir d’une autre session ou d’un autre ordinateur sans interrompre les commandes ou perdre l’État.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-125">This enables you to disconnect from the session and reconnect from a different session or a different computer without interrupting the commands or losing state.</span></span>

### <a name="is-powershell-remoting-secure"></a><span data-ttu-id="1d1ad-126">La communication à distance PowerShell est-elle sécurisée ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-126">Is PowerShell remoting secure?</span></span>

<span data-ttu-id="1d1ad-127">Lorsque vous vous connectez à un ordinateur distant, le système utilise les informations d’identification du nom d’utilisateur et du mot de passe sur l’ordinateur local ou les informations d’identification que vous fournissez dans la commande pour vous connecter à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-127">When you connect to a remote computer, the system uses the username and password credentials on the local computer or the credentials that you supply in the command to log you in to the remote computer.</span></span> <span data-ttu-id="1d1ad-128">Les informations d’identification et le reste de la transmission sont chiffrés.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-128">The credentials and the rest of the transmission are encrypted.</span></span>

<span data-ttu-id="1d1ad-129">Pour ajouter une protection supplémentaire, vous pouvez configurer l’ordinateur distant pour qu’il utilise SSL (Secure Sockets Layer) (SSL) au lieu de HTTP pour écouter les demandes Windows Remote Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="1d1ad-129">To add additional protection, you can configure the remote computer to use Secure Sockets Layer (SSL) instead of HTTP to listen for Windows Remote Management (WinRM) requests.</span></span> <span data-ttu-id="1d1ad-130">Ensuite, les utilisateurs peuvent utiliser le paramètre **UseSSL** des `Invoke-Command` applets de commande, `New-PSSession` et lors de l' `Enter-PSSession` établissement d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-130">Then, users can use the **UseSSL** parameter of the `Invoke-Command`, `New-PSSession`, and `Enter-PSSession` cmdlets when establishing a connection.</span></span> <span data-ttu-id="1d1ad-131">Cette option utilise le canal HTTPs plus sécurisé au lieu du protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-131">This option uses the more secure HTTPS channel instead of HTTP.</span></span>

### <a name="do-all-remote-commands-require-powershell-remoting"></a><span data-ttu-id="1d1ad-132">Toutes les commandes distantes requièrent-elle la communication à distance PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-132">Do all remote commands require PowerShell remoting?</span></span>

<span data-ttu-id="1d1ad-133">Non.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-133">No.</span></span> <span data-ttu-id="1d1ad-134">Plusieurs applets de commande ont un paramètre **ComputerName** qui vous permet d’obtenir des objets de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-134">Several cmdlets have a **ComputerName** parameter that lets you get objects from the remote computer.</span></span>

<span data-ttu-id="1d1ad-135">Ces applets de commande n’utilisent pas la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-135">These cmdlets do not use PowerShell remoting.</span></span> <span data-ttu-id="1d1ad-136">Vous pouvez donc les utiliser sur n’importe quel ordinateur exécutant PowerShell, même si l’ordinateur n’est pas configuré pour la communication à distance PowerShell ou si l’ordinateur ne remplit pas les conditions requises pour la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-136">So, you can use them on any computer that is running PowerShell, even if the computer is not configured for PowerShell remoting or if the computer does not meet the requirements for PowerShell remoting.</span></span>

<span data-ttu-id="1d1ad-137">Ces applets de commande sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-137">These cmdlets include the following:</span></span>

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

<span data-ttu-id="1d1ad-138">Pour rechercher toutes les applets de commande avec un paramètre **ComputerName** , tapez :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-138">To find all the cmdlets with a **ComputerName** parameter, type:</span></span>

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

<span data-ttu-id="1d1ad-139">Pour déterminer si le paramètre **ComputerName** d’une applet de commande particulière requiert la communication à distance PowerShell, consultez la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-139">To determine whether the **ComputerName** parameter of a particular cmdlet requires PowerShell remoting, see the parameter description.</span></span> <span data-ttu-id="1d1ad-140">Pour afficher la description du paramètre, tapez :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-140">To display the parameter description, type:</span></span>

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

<span data-ttu-id="1d1ad-141">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-141">For example:</span></span>

```powershell
Get-Help Get-Process -Parameter ComputerName
```

<span data-ttu-id="1d1ad-142">Pour toutes les autres commandes, utilisez l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="1d1ad-142">For all other commands, use the `Invoke-Command` cmdlet.</span></span>

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a><span data-ttu-id="1d1ad-143">Comment faire exécuter une commande sur un ordinateur distant ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-143">How do I run a command on a remote computer?</span></span>

<span data-ttu-id="1d1ad-144">Pour exécuter une commande sur un ordinateur distant, utilisez l' `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-144">To run a command on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="1d1ad-145">Placez votre commande entre accolades ( `{}` ) pour en faire un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-145">Enclose your command in braces (`{}`) to make it a script block.</span></span> <span data-ttu-id="1d1ad-146">Utilisez le paramètre **scriptblock** de `Invoke-Command` pour spécifier la commande.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-146">Use the **ScriptBlock** parameter of `Invoke-Command` to specify the command.</span></span>

<span data-ttu-id="1d1ad-147">Vous pouvez utiliser le paramètre **ComputerName** de `Invoke-Command` pour spécifier un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-147">You can use the **ComputerName** parameter of `Invoke-Command` to specify a remote computer.</span></span> <span data-ttu-id="1d1ad-148">Ou bien, vous pouvez créer une connexion permanente à un ordinateur distant (une session), puis utiliser le paramètre de **session** de `Invoke-Command` pour exécuter la commande dans la session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-148">Or, you can create a persistent connection to a remote computer (a session) and then use the **Session** parameter of `Invoke-Command` to run the command in the session.</span></span>

<span data-ttu-id="1d1ad-149">Par exemple, les commandes suivantes exécutent une `Get-Process` commande à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-149">For example, the following commands run a `Get-Process` command remotely.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

<span data-ttu-id="1d1ad-150">Pour interrompre une commande distante, tapez <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-150">To interrupt a remote command, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="1d1ad-151">La demande d’interruption est transmise à l’ordinateur distant, où elle met fin à la commande à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-151">The interruption request is passed to the remote computer, where it terminates the remote command.</span></span>

<span data-ttu-id="1d1ad-152">Pour plus d’informations sur les commandes distantes, consultez about_Remote et les rubriques d’aide pour les applets de commande qui prennent en charge la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-152">For more information about remote commands, see about_Remote and the Help topics for the cmdlets that support remoting.</span></span>

### <a name="can-i-just-telnet-into-a-remote-computer"></a><span data-ttu-id="1d1ad-153">Puis-je simplement faire appel à Telnet sur un ordinateur distant ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-153">Can I just telnet into a remote computer?</span></span>

<span data-ttu-id="1d1ad-154">Vous pouvez utiliser l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-154">You can use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="1d1ad-155">À l’invite PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-155">At the PowerShell prompt, type:</span></span>

```powershell
Enter-PSSession <ComputerName>
```

<span data-ttu-id="1d1ad-156">L’invite de commandes change pour indiquer que vous êtes connecté à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-156">The command prompt changes to show that you are connected to the remote computer.</span></span>

```
<ComputerName>\C:>
```

<span data-ttu-id="1d1ad-157">À présent, les commandes que vous tapez s’exécutent sur l’ordinateur distant comme si vous les tapiez directement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-157">Now, the commands that you type run on the remote computer just as though you typed them directly on the remote computer.</span></span>

<span data-ttu-id="1d1ad-158">Pour terminer la session interactive, tapez :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-158">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="1d1ad-159">Une session interactive est une session persistante qui utilise le protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-159">An interactive session is a persistent session that uses the WS-Management protocol.</span></span> <span data-ttu-id="1d1ad-160">Elle n’est pas identique à l’utilisation de Telnet, mais elle offre une expérience similaire.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-160">It is not the same as using Telnet, but it provides a similar experience.</span></span>

<span data-ttu-id="1d1ad-161">Pour plus d’informations, consultez `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-161">For more information, see `Enter-PSSession`.</span></span>

### <a name="can-i-create-a-persistent-connection"></a><span data-ttu-id="1d1ad-162">Puis-je créer une connexion permanente ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-162">Can I create a persistent connection?</span></span>

<span data-ttu-id="1d1ad-163">Oui.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-163">Yes.</span></span> <span data-ttu-id="1d1ad-164">Vous pouvez exécuter des commandes distantes en spécifiant le nom de l’ordinateur distant, son nom NetBIOS ou son adresse IP.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-164">You can run remote commands by specifying the name of the remote computer, its NetBIOS name, or its IP address.</span></span> <span data-ttu-id="1d1ad-165">Ou bien, vous pouvez exécuter des commandes distantes en spécifiant une session PowerShell (PSSession) qui est connectée à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-165">Or, you can run remote commands by specifying a PowerShell session (PSSession) that is connected to the remote computer.</span></span>

<span data-ttu-id="1d1ad-166">Quand vous utilisez le paramètre **ComputerName** de `Invoke-Command` ou `Enter-PSSession` , PowerShell établit une connexion temporaire.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-166">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection.</span></span> <span data-ttu-id="1d1ad-167">PowerShell utilise la connexion pour exécuter uniquement la commande actuelle, puis ferme la connexion.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-167">PowerShell uses the connection to run only the current command, and then it closes the connection.</span></span> <span data-ttu-id="1d1ad-168">Il s’agit d’une méthode très efficace pour exécuter une seule commande ou plusieurs commandes sans rapport, même sur de nombreux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-168">This is a very efficient method for running a single command or several unrelated commands, even on many remote computers.</span></span>

<span data-ttu-id="1d1ad-169">Lorsque vous utilisez l' `New-PSSession` applet de commande pour créer une session PSSession, PowerShell établit une connexion permanente pour la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-169">When you use the `New-PSSession` cmdlet to create a PSSession, PowerShell establishes a persistent connection for the PSSession.</span></span> <span data-ttu-id="1d1ad-170">Ensuite, vous pouvez exécuter plusieurs commandes dans la session PSSession, y compris les commandes qui partagent des données.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-170">Then, you can run multiple commands in the PSSession, including commands that share data.</span></span>

<span data-ttu-id="1d1ad-171">En général, vous créez une session PSSession pour exécuter une série de commandes associées qui partagent des données.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-171">Typically, you create a PSSession to run a series of related commands that share data.</span></span> <span data-ttu-id="1d1ad-172">Dans le cas contraire, la connexion temporaire créée par le paramètre **ComputerName** est suffisante pour la plupart des commandes.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-172">Otherwise, the temporary connection created by the **ComputerName** parameter is sufficient for most commands.</span></span>

<span data-ttu-id="1d1ad-173">Pour plus d’informations sur les sessions, consultez about_PSSessions.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-173">For more information about sessions, see about_PSSessions.</span></span>

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a><span data-ttu-id="1d1ad-174">Puis-je exécuter des commandes sur plusieurs ordinateurs à la fois ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-174">Can I run commands on more than one computer at a time?</span></span>

<span data-ttu-id="1d1ad-175">Oui.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-175">Yes.</span></span> <span data-ttu-id="1d1ad-176">Le paramètre **ComputerName** de l' `Invoke-Command` applet de commande accepte plusieurs noms d’ordinateur, et le paramètre de **session** accepte plusieurs sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-176">The **ComputerName** parameter of the `Invoke-Command` cmdlet accepts multiple computer names, and the **Session** parameter accepts multiple PSSessions.</span></span>

<span data-ttu-id="1d1ad-177">Quand vous exécutez une `Invoke-Command` commande, PowerShell exécute les commandes sur tous les ordinateurs spécifiés ou dans tous les sessions PSSession spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-177">When you run an `Invoke-Command` command, PowerShell runs the commands on all of the specified computers or in all of the specified PSSessions.</span></span>

<span data-ttu-id="1d1ad-178">PowerShell peut gérer des centaines de connexions à distance simultanées.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-178">PowerShell can manage hundreds of concurrent remote connections.</span></span> <span data-ttu-id="1d1ad-179">Toutefois, le nombre de commandes distantes que vous pouvez envoyer peut être limité par les ressources de votre ordinateur et sa capacité à établir et à gérer plusieurs connexions réseau.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-179">However, the number of remote commands that you can send might be limited by the resources of your computer and its capacity to establish and maintain multiple network connections.</span></span>

<span data-ttu-id="1d1ad-180">Pour plus d’informations, consultez l’exemple de la `Invoke-Command` rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-180">For more information, see the example in the `Invoke-Command` Help topic.</span></span>

### <a name="where-are-my-profiles"></a><span data-ttu-id="1d1ad-181">Où sont mes profils ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-181">Where are my profiles?</span></span>

<span data-ttu-id="1d1ad-182">Les profils PowerShell ne sont pas exécutés automatiquement dans les sessions à distance. par conséquent, les commandes ajoutées par le profil ne sont pas présentes dans la session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-182">PowerShell profiles are not run automatically in remote sessions, so the commands that the profile adds are not present in the session.</span></span> <span data-ttu-id="1d1ad-183">En outre, la `$profile` variable automatique n’est pas remplie dans les sessions à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-183">In addition, the `$profile` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="1d1ad-184">Pour exécuter un profil dans une session, utilisez l' `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-184">To run a profile in a session, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="1d1ad-185">Par exemple, la commande suivante exécute le profil CurrentUserCurrentHost à partir de l’ordinateur local dans la session dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="1d1ad-185">For example, the following command runs the CurrentUserCurrentHost profile from the local computer in the session in `$s`.</span></span>

```
Invoke-Command -Session $s -FilePath $profile
```

<span data-ttu-id="1d1ad-186">La commande suivante exécute le profil CurrentUserCurrentHost à partir de l’ordinateur distant dans la session dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="1d1ad-186">The following command runs the CurrentUserCurrentHost profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="1d1ad-187">Étant donné que la `$profile` variable n’est pas remplie, la commande utilise le chemin d’accès explicite au profil.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-187">Because the `$profile` variable is not populated, the command uses the explicit path to the profile.</span></span>

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="1d1ad-188">Après l’exécution de cette commande, les commandes ajoutées par le profil à la session sont disponibles dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="1d1ad-188">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

<span data-ttu-id="1d1ad-189">Vous pouvez également utiliser un script de démarrage dans une configuration de session pour exécuter un profil dans chaque session à distance qui utilise la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-189">You can also use a startup script in a session configuration to run a profile in every remote session that uses the session configuration.</span></span>

<span data-ttu-id="1d1ad-190">Pour plus d’informations sur les profils PowerShell, voir about_Profiles.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-190">For more information about PowerShell profiles, see about_Profiles.</span></span>
<span data-ttu-id="1d1ad-191">Pour plus d’informations sur les configurations de session, consultez `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1d1ad-191">For more information about session configurations, see `Register-PSSessionConfiguration`.</span></span>

### <a name="how-does-throttling-work-on-remote-commands"></a><span data-ttu-id="1d1ad-192">Comment la limitation fonctionne-t-elle sur les commandes distantes ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-192">How does throttling work on remote commands?</span></span>

<span data-ttu-id="1d1ad-193">Pour vous aider à gérer les ressources sur votre ordinateur local, PowerShell intègre une fonctionnalité de limitation par commande qui vous permet de limiter le nombre de connexions à distance simultanées établies pour chaque commande.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-193">To help you manage the resources on your local computer, PowerShell includes a per-command throttling feature that lets you limit the number of concurrent remote connections that are established for each command.</span></span>

<span data-ttu-id="1d1ad-194">La valeur par défaut est 32 connexions simultanées, mais vous pouvez utiliser le paramètre **ThrottleLimit** des applets de commande pour définir une limite de limitation personnalisée pour des commandes particulières.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-194">The default is 32 concurrent connections, but you can use the **ThrottleLimit** parameter of the cmdlets to set a custom throttle limit for particular commands.</span></span>

<span data-ttu-id="1d1ad-195">Lorsque vous utilisez la fonctionnalité de limitation, n’oubliez pas qu’elle est appliquée à chaque commande, et non à l’ensemble de la session ou à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-195">When you use the throttling feature, remember that it is applied to each command, not to the entire session or to the computer.</span></span> <span data-ttu-id="1d1ad-196">Si vous exécutez des commandes simultanément dans plusieurs sessions ou sessions PSSession, le nombre de connexions simultanées est la somme des connexions simultanées dans toutes les sessions.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-196">If you are running commands concurrently in several sessions or PSSessions, the number of concurrent connections is the sum of the concurrent connections in all the sessions.</span></span>

<span data-ttu-id="1d1ad-197">Pour rechercher des applets de commande avec un paramètre **ThrottleLimit** , tapez :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-197">To find cmdlets with a **ThrottleLimit** parameter, type:</span></span>

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a><span data-ttu-id="1d1ad-198">La sortie des commandes à distance est-elle différente de la sortie locale ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-198">Is the output of remote commands different from local output?</span></span>

<span data-ttu-id="1d1ad-199">Lorsque vous utilisez PowerShell localement, vous envoyez et recevez des objets « Live » .NET Framework. les objets « actifs » sont des objets qui sont associés à des programmes ou des composants système réels.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-199">When you use PowerShell locally, you send and receive "live" .NET Framework objects; "live" objects are objects that are associated with actual programs or system components.</span></span> <span data-ttu-id="1d1ad-200">Lorsque vous appelez les méthodes ou modifiez les propriétés d’objets actifs, les modifications affectent le programme ou le composant réel.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-200">When you invoke the methods or change the properties of live objects, the changes affect the actual program or component.</span></span> <span data-ttu-id="1d1ad-201">Et, lorsque les propriétés d’un programme ou d’un composant changent, les propriétés de l’objet qui les représentent sont également modifiées.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-201">And, when the properties of a program or component change, the properties of the object that represent them also change.</span></span>

<span data-ttu-id="1d1ad-202">Toutefois, étant donné que la plupart des objets en ligne ne peuvent pas être transmis sur le réseau, PowerShell « sérialise » la plupart des objets envoyés dans les commandes distantes, autrement dit, il convertit chaque objet en une série de éléments de données XML (contrainte Language dans XML [CLiXML]) pour la transmission.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-202">However, because most live objects cannot be transmitted over the network, PowerShell "serializes" most of the objects sent in remote commands, that is, it converts each object into a series of XML (Constraint Language in XML [CLiXML]) data elements for transmission.</span></span>

<span data-ttu-id="1d1ad-203">Lorsque PowerShell reçoit un objet sérialisé, il convertit le XML en un type d’objet désérialisé.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-203">When PowerShell receives a serialized object, it converts the XML into a deserialized object type.</span></span> <span data-ttu-id="1d1ad-204">L’objet désérialisé est un enregistrement précis des propriétés du programme ou du composant à un moment précédent, mais il n’est plus « en temps réel », c’est-à-dire qu’il n’est plus directement associé au composant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-204">The deserialized object is an accurate record of the properties of the program or component at a previous time, but it is no longer "live", that is, it is no longer directly associated with the component.</span></span> <span data-ttu-id="1d1ad-205">Et, les méthodes sont supprimées, car elles ne sont plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-205">And, the methods are removed because they are no longer effective.</span></span>

<span data-ttu-id="1d1ad-206">En règle générale, vous pouvez utiliser des objets désérialisés de la même façon que vous utilisez des objets actifs, mais vous devez être conscient de leurs limitations.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-206">Typically, you can use deserialized objects just as you would use live objects, but you must be aware of their limitations.</span></span> <span data-ttu-id="1d1ad-207">En outre, les objets retournés par l' `Invoke-Command` applet de commande ont des propriétés supplémentaires qui vous aident à déterminer l’origine de la commande.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-207">Also, the objects that are returned by the `Invoke-Command` cmdlet have additional properties that help you to determine the origin of the command.</span></span>

<span data-ttu-id="1d1ad-208">Certains types d’objets, tels que les objets DirectoryInfo et les GUID, sont reconvertis en objets dynamiques lorsqu’ils sont reçus.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-208">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="1d1ad-209">Ces objets n’ont pas besoin d’une gestion ou d’une mise en forme spéciale.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-209">These objects do not need any special handling or formatting.</span></span>

<span data-ttu-id="1d1ad-210">Pour plus d’informations sur l’interprétation et la mise en forme de la sortie à distance, consultez [about_Remote_Output](about_Remote_Output.md).</span><span class="sxs-lookup"><span data-stu-id="1d1ad-210">For information about interpreting and formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

### <a name="can-i-run-background-jobs-remotely"></a><span data-ttu-id="1d1ad-211">Puis-je exécuter des tâches en arrière-plan à distance ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-211">Can I run background jobs remotely?</span></span>

<span data-ttu-id="1d1ad-212">Oui.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-212">Yes.</span></span> <span data-ttu-id="1d1ad-213">Une tâche en arrière-plan PowerShell est une commande PowerShell qui s’exécute de façon asynchrone sans interagir avec la session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-213">A PowerShell background job is a PowerShell command that runs asynchronously without interacting with the session.</span></span> <span data-ttu-id="1d1ad-214">Lorsque vous démarrez une tâche en arrière-plan, l’invite de commandes est immédiatement retournée, et vous pouvez continuer à travailler dans la session pendant l’exécution de la tâche, même si elle s’exécute pendant une période prolongée.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-214">When you start a background job, the command prompt returns immediately, and you can continue to work in the session while the job runs even if it runs for an extended period of time.</span></span>

<span data-ttu-id="1d1ad-215">Vous pouvez démarrer un travail en arrière-plan même si d’autres commandes sont en cours d’exécution, car les travaux en arrière-plan s’exécutent toujours de façon asynchrone dans une session temporaire.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-215">You can start a background job even while other commands are running because background jobs always run asynchronously in a temporary session.</span></span>

<span data-ttu-id="1d1ad-216">Vous pouvez exécuter des tâches en arrière-plan sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-216">You can run background jobs on a local or remote computer.</span></span> <span data-ttu-id="1d1ad-217">Par défaut, une tâche en arrière-plan s’exécute sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-217">By default, a background job runs on the local computer.</span></span> <span data-ttu-id="1d1ad-218">Toutefois, vous pouvez utiliser le paramètre **AsJob** de l' `Invoke-Command` applet de commande pour exécuter une commande à distance en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-218">However, you can use the **AsJob** parameter of the `Invoke-Command` cmdlet to run any remote command as a background job.</span></span> <span data-ttu-id="1d1ad-219">Et, vous pouvez utiliser `Invoke-Command` pour exécuter une `Start-Job` commande à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-219">And, you can use `Invoke-Command` to run a `Start-Job` command remotely.</span></span>

<span data-ttu-id="1d1ad-220">Pour plus d’informations sur les tâches en arrière-plan dans PowerShell, consultez [about_Jobs (about_Jobs. MD)] et [about_Remote_Jobs (about_Remote_Jobs. MD)].</span><span class="sxs-lookup"><span data-stu-id="1d1ad-220">For more information about background jobs in PowerShell , see [about_Jobs(about_Jobs.md)] and [about_Remote_Jobs(about_Remote_Jobs.md)].</span></span>

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a><span data-ttu-id="1d1ad-221">Puis-je exécuter des programmes Windows sur un ordinateur distant ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-221">Can I run windows programs on a remote computer?</span></span>

<span data-ttu-id="1d1ad-222">Vous pouvez utiliser les commandes à distance PowerShell pour exécuter des programmes Windows sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-222">You can use PowerShell remote commands to run Windows-based programs on remote computers.</span></span> <span data-ttu-id="1d1ad-223">Par exemple, vous pouvez exécuter `Shutdown.exe` ou `Ipconfig.exe` sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-223">For example, you can run `Shutdown.exe` or `Ipconfig.exe` on a remote computer.</span></span>

<span data-ttu-id="1d1ad-224">Toutefois, vous ne pouvez pas utiliser de commandes PowerShell pour ouvrir l’interface utilisateur d’un programme sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-224">However, you cannot use PowerShell commands to open the user interface for any program on a remote computer.</span></span>

<span data-ttu-id="1d1ad-225">Lorsque vous démarrez un programme Windows sur un ordinateur distant, la commande n’est pas terminée et l’invite de commandes PowerShell ne retourne pas, jusqu’à ce que le programme soit terminé ou que vous appuyiez sur <kbd>CTRL</kbd> + <kbd>C</kbd> pour interrompre la commande.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-225">When you start a Windows program on a remote computer, the command is not completed, and the PowerShell command prompt does not return, until the program is finished or until you press <kbd>CTRL</kbd>+<kbd>C</kbd> to interrupt the command.</span></span> <span data-ttu-id="1d1ad-226">Par exemple, si vous exécutez le `Ipconfig.exe` programme sur un ordinateur distant, l’invite de commandes n’est pas renvoyée tant que `Ipconfig.exe` n’est pas terminé.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-226">For example, if you run the `Ipconfig.exe` program on a remote computer, the command prompt does not return until `Ipconfig.exe` is completed.</span></span>

<span data-ttu-id="1d1ad-227">Si vous utilisez des commandes à distance pour démarrer un programme avec une interface utilisateur, le processus de programme démarre, mais l’interface utilisateur n’apparaît pas.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-227">If you use remote commands to start a program that has a user interface, the program process starts, but the user interface does not appear.</span></span> <span data-ttu-id="1d1ad-228">La commande PowerShell n’est pas terminée, et l’invite de commandes ne retourne pas tant que vous n’arrêtez pas le processus du programme ou que vous n’appuyez pas sur <kbd>CTRL</kbd> + <kbd>C</kbd>, ce qui interrompt la commande et arrête le processus.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-228">The PowerShell command is not completed, and the command prompt does not return until you stop the program process or until you press <kbd>CTRL</kbd>+<kbd>C</kbd>, which interrupts the command and stops the process.</span></span>

<span data-ttu-id="1d1ad-229">Par exemple, si vous utilisez une commande PowerShell pour l’exécuter `Notepad` sur un ordinateur distant, le processus du bloc-notes démarre sur l’ordinateur distant, mais l’interface utilisateur du bloc-notes n’apparaît pas.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-229">For example, if you use a PowerShell command to run `Notepad` on a remote computer, the Notepad process starts on the remote computer, but the Notepad user interface does not appear.</span></span> <span data-ttu-id="1d1ad-230">Pour interrompre la commande et restaurer l’invite de commandes, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-230">To interrupt the command and restore the command prompt, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a><span data-ttu-id="1d1ad-231">Puis-je limiter les commandes que les utilisateurs peuvent exécuter à distance sur mon ordinateur ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-231">Can I limit the commands that users can run remotely on my computer?</span></span>

<span data-ttu-id="1d1ad-232">Oui.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-232">Yes.</span></span> <span data-ttu-id="1d1ad-233">Chaque session à distance doit utiliser l’une des configurations de session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-233">Every remote session must use one of the session configurations on the remote computer.</span></span> <span data-ttu-id="1d1ad-234">Vous pouvez gérer les configurations de session sur votre ordinateur (et les autorisations sur ces configurations de session) pour déterminer qui peut exécuter des commandes à distance sur votre ordinateur et les commandes qu’ils peuvent exécuter.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-234">You can manage the session configurations on your computer (and the permissions to those session configurations) to determine who can run commands remotely on your computer and which commands they can run.</span></span>

<span data-ttu-id="1d1ad-235">Une configuration de session configure l’environnement pour la session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-235">A session configuration configures the environment for the session.</span></span> <span data-ttu-id="1d1ad-236">Vous pouvez définir la configuration à l’aide d’un assembly qui implémente une nouvelle classe de configuration ou à l’aide d’un script qui s’exécute dans la session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-236">You can define the configuration by using an assembly that implements a new configuration class or by using a script that runs in the session.</span></span> <span data-ttu-id="1d1ad-237">La configuration peut déterminer les commandes qui sont disponibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-237">The configuration can determine the commands that are available in the session.</span></span>
<span data-ttu-id="1d1ad-238">De plus, la configuration peut inclure des paramètres qui protègent l’ordinateur, tels que des paramètres qui limitent la quantité de données que la session peut recevoir à distance dans un objet ou une commande unique.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-238">And, the configuration can include settings that protect the computer, such as settings that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="1d1ad-239">Vous pouvez également spécifier un descripteur de sécurité qui détermine les autorisations requises pour utiliser la configuration.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-239">You can also specify a security descriptor that determines the permissions that are required to use the configuration.</span></span>

<span data-ttu-id="1d1ad-240">L' `Enable-PSRemoting` applet de commande crée les configurations de session par défaut sur votre ordinateur : Microsoft. PowerShell, Microsoft. PowerShell. Workflow et Microsoft. powershell32 (systèmes d’exploitation 64 bits uniquement).</span><span class="sxs-lookup"><span data-stu-id="1d1ad-240">The `Enable-PSRemoting` cmdlet creates the default session configurations on your computer: Microsoft.PowerShell, Microsoft.PowerShell.Workflow, and Microsoft.PowerShell32 (64-bit operating systems only).</span></span> <span data-ttu-id="1d1ad-241">`Enable-PSRemoting` définit le descripteur de sécurité pour la configuration afin d’autoriser uniquement les membres du groupe Administrateurs sur votre ordinateur à les utiliser.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-241">`Enable-PSRemoting` sets the security descriptor for the configuration to allow only members of the Administrators group on your computer to use them.</span></span>

<span data-ttu-id="1d1ad-242">Vous pouvez utiliser les applets de commande de configuration de session pour modifier les configurations de session par défaut, pour créer de nouvelles configurations de session et pour modifier les descripteurs de sécurité de toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-242">You can use the session configuration cmdlets to edit the default session configurations, to create new session configurations, and to change the security descriptors of all the session configurations.</span></span>

<span data-ttu-id="1d1ad-243">À compter de Windows PowerShell 3,0, l’applet de commande `New-PSSessionConfigurationFile` vous permet de créer des configurations de session personnalisées à l’aide d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-243">Beginning in Windows PowerShell 3.0, the `New-PSSessionConfigurationFile` cmdlet lets you create custom session configurations by using a text file.</span></span> <span data-ttu-id="1d1ad-244">Le fichier comprend des options permettant de définir le mode de langage et de spécifier les applets de commande et les modules disponibles dans les sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-244">The file includes options for setting the language mode and for specifying the cmdlets and modules that are available in sessions that use the session configuration.</span></span>

<span data-ttu-id="1d1ad-245">Quand les utilisateurs utilisent `Invoke-Command` les `New-PSSession` applets de commande, ou, `Enter-PSSession` ils peuvent utiliser le paramètre **ConfigurationName** pour indiquer la configuration de session utilisée pour la session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-245">When users use the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets, they can use the **ConfigurationName** parameter to indicate the session configuration that is used for the session.</span></span> <span data-ttu-id="1d1ad-246">Ils peuvent modifier la configuration par défaut utilisée par leurs sessions en modifiant la valeur de la `$PSSessionConfigurationName` variable de préférence dans la session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-246">And, they can change the default configuration that their sessions use by changing the value of the `$PSSessionConfigurationName` preference variable in the session.</span></span>

<span data-ttu-id="1d1ad-247">Pour plus d’informations sur les configurations de session, consultez l’aide sur les applets de commande de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-247">For more information about session configurations, see the Help for the session configuration cmdlets.</span></span> <span data-ttu-id="1d1ad-248">Pour rechercher les applets de commande de configuration de session, tapez :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-248">To find the session configuration cmdlets, type:</span></span>

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a><span data-ttu-id="1d1ad-249">Que sont les configurations de ventilateur et de ventilateur ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-249">What are fan in and fan out configurations?</span></span>

<span data-ttu-id="1d1ad-250">Le scénario de communication à distance PowerShell le plus courant impliquant plusieurs ordinateurs est la configuration un-à-plusieurs, dans laquelle un ordinateur local (l’ordinateur de l’administrateur) exécute des commandes PowerShell sur de nombreux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-250">The most common PowerShell remoting scenario involving multiple computers is the one-to-many configuration, in which one local computer (the administrator's computer) runs PowerShell commands on numerous remote computers.</span></span> <span data-ttu-id="1d1ad-251">C’est ce que l’on appelle le scénario de « Fanout ».</span><span class="sxs-lookup"><span data-stu-id="1d1ad-251">This is known as the "fan-out" scenario.</span></span>

<span data-ttu-id="1d1ad-252">Toutefois, dans certaines entreprises, la configuration est de type plusieurs-à-un, où de nombreux ordinateurs clients se connectent à un ordinateur distant unique exécutant PowerShell, tel qu’un serveur de fichiers ou une borne.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-252">However, in some enterprises, the configuration is many-to-one, where many client computers connect to a single remote computer that is running PowerShell, such as a file server or a kiosk.</span></span> <span data-ttu-id="1d1ad-253">C’est ce que l’on appelle la configuration « fan-in ».</span><span class="sxs-lookup"><span data-stu-id="1d1ad-253">This is known as the "fan-in" configuration.</span></span>

<span data-ttu-id="1d1ad-254">La communication à distance PowerShell prend en charge les configurations de ventilateur et de ventilateur.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-254">PowerShell remoting supports both fan-out and fan-in configurations.</span></span>

<span data-ttu-id="1d1ad-255">Pour la configuration de Fanout, PowerShell utilise le protocole WS-Management (Web Services for Management) et le service WinRM qui prend en charge l’implémentation Microsoft de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-255">For the fan-out configuration, PowerShell uses the Web Services for Management (WS-Management) protocol and the WinRM service that supports the Microsoft implementation of WS-Management.</span></span> <span data-ttu-id="1d1ad-256">Lorsqu’un ordinateur local se connecte à un ordinateur distant, WS-Management établit une connexion et utilise un plug-in pour PowerShell pour démarrer le processus hôte PowerShell (Wsmprovhost.exe) sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-256">When a local computer connects to a remote computer, WS-Management establishes a connection and uses a plug-in for PowerShell to start the PowerShell host process (Wsmprovhost.exe) on the remote computer.</span></span> <span data-ttu-id="1d1ad-257">L’utilisateur peut spécifier un autre port, une autre configuration de session et d’autres fonctionnalités pour personnaliser la connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-257">The user can specify an alternate port, an alternate session configuration, and other features to customize the remote connection.</span></span>

<span data-ttu-id="1d1ad-258">Pour prendre en charge la configuration « fan-in », PowerShell utilise Internet Information Services (IIS) pour héberger WS-Management, charger le plug-in PowerShell et Démarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-258">To support the "fan-in" configuration, PowerShell uses internet Information Services (IIS) to host WS-Management, to load the PowerShell plug-in, and to start PowerShell.</span></span> <span data-ttu-id="1d1ad-259">Dans ce scénario, au lieu de démarrer chaque session PowerShell dans un processus distinct, toutes les sessions PowerShell s’exécutent dans le même processus hôte.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-259">In this scenario, instead of starting each PowerShell session in a separate process, all PowerShell sessions run in the same host process.</span></span>

<span data-ttu-id="1d1ad-260">L’hébergement IIS et la gestion à distance du fan-in ne sont pas pris en charge dans Windows XP ou Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-260">IIS hosting and fan-in remote management is not supported in Windows XP or in Windows Server 2003.</span></span>

<span data-ttu-id="1d1ad-261">Dans une configuration de fan-in, l’utilisateur peut spécifier un URI de connexion et un point de terminaison HTTP, y compris le transport, le nom de l’ordinateur, le port et le nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-261">In a fan-in configuration, the user can specify a connection URI and an HTTP endpoint, including the transport, computer name, port, and application name.</span></span>
<span data-ttu-id="1d1ad-262">IIS transfère toutes les demandes avec un nom d’application spécifié à l’application.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-262">IIS forwards all the requests with a specified application name to the application.</span></span> <span data-ttu-id="1d1ad-263">La valeur par défaut est WS-Management, qui peut héberger PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-263">The default is WS-Management, which can host PowerShell.</span></span>

<span data-ttu-id="1d1ad-264">Vous pouvez également spécifier un mécanisme d’authentification et interdire ou autoriser la redirection à partir de points de terminaison HTTP et HTTPs.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-264">You can also specify an authentication mechanism and prohibit or allow redirection from HTTP and HTTPS endpoints.</span></span>

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a><span data-ttu-id="1d1ad-265">Puis-je tester la communication à distance sur un seul ordinateur qui n’est pas dans un domaine ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-265">Can I test remoting on a single computer not in a domain?</span></span>

<span data-ttu-id="1d1ad-266">Oui.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-266">Yes.</span></span> <span data-ttu-id="1d1ad-267">La communication à distance PowerShell est disponible même lorsque l’ordinateur local n’est pas dans un domaine.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-267">PowerShell remoting is available even when the local computer is not in a domain.</span></span> <span data-ttu-id="1d1ad-268">Vous pouvez utiliser les fonctionnalités de communication à distance pour vous connecter à des sessions et créer des sessions sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-268">You can use the remoting features to connect to sessions and to create sessions on the same computer.</span></span> <span data-ttu-id="1d1ad-269">Les fonctionnalités fonctionnent de la même façon que lorsque vous vous connectez à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-269">The features work the same as they do when you connect to a remote computer.</span></span>

<span data-ttu-id="1d1ad-270">Pour exécuter des commandes à distance sur un ordinateur dans un groupe de travail, modifiez les paramètres Windows suivants sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-270">To run remote commands on a computer in a workgroup, change the following Windows settings on the computer.</span></span>

<span data-ttu-id="1d1ad-271">ATTENTION : ces paramètres affectent tous les utilisateurs du système et peuvent rendre le système plus vulnérable à une attaque malveillante.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-271">Caution: These settings affect all users on the system and they can make the system more vulnerable to a malicious attack.</span></span> <span data-ttu-id="1d1ad-272">Soyez prudent lorsque vous apportez ces modifications.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-272">Use caution when making these changes.</span></span>

- <span data-ttu-id="1d1ad-273">Windows Vista, Windows 7, Windows 8 :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-273">Windows Vista, Windows 7, Windows 8:</span></span>

  <span data-ttu-id="1d1ad-274">Créez l’entrée de Registre suivante, puis définissez sa valeur sur 1 : LocalAccountTokenFilterPolicy dans ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span><span class="sxs-lookup"><span data-stu-id="1d1ad-274">Create the following registry entry, and then set its value to 1: LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span></span>

  <span data-ttu-id="1d1ad-275">Vous pouvez utiliser la commande PowerShell suivante pour ajouter cette entrée :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-275">You can use the following PowerShell command to add this entry:</span></span>

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- <span data-ttu-id="1d1ad-276">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2 :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-276">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:</span></span>

  <span data-ttu-id="1d1ad-277">Aucune modification n’est nécessaire, car le paramètre par défaut de la stratégie « accès réseau : modèle de partage et de sécurité pour les comptes locaux » est « classique ».</span><span class="sxs-lookup"><span data-stu-id="1d1ad-277">No changes are needed because the default setting of the "Network Access: Sharing and security model for local accounts" policy is "Classic".</span></span> <span data-ttu-id="1d1ad-278">Vérifiez le paramètre en cas de modification de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-278">Verify the setting in case it has changed.</span></span>

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a><span data-ttu-id="1d1ad-279">Puis-je exécuter des commandes à distance sur un ordinateur dans un autre domaine ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-279">Can I run remote commands on a computer in another domain?</span></span>

<span data-ttu-id="1d1ad-280">Oui.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-280">Yes.</span></span> <span data-ttu-id="1d1ad-281">En règle générale, les commandes s’exécutent sans erreur, même si vous devrez peut-être utiliser le paramètre **Credential** des `Invoke-Command` applets de commande, `New-PSSession` ou `Enter-PSSession` pour fournir les informations d’identification d’un membre du groupe Administrateurs sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-281">Typically, the commands run without error, although you might need to use the **Credential** parameter of the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets to provide the credentials of a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="1d1ad-282">Cela est parfois nécessaire même lorsque l’utilisateur actuel est membre du groupe Administrateurs sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-282">This is sometimes required even when the current user is a member of the Administrators group on the local and remote computers.</span></span>

<span data-ttu-id="1d1ad-283">Toutefois, si l’ordinateur distant n’est pas dans un domaine approuvé par l’ordinateur local, l’ordinateur distant peut ne pas être en mesure d’authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-283">However, if the remote computer is not in a domain that the local computer trusts, the remote computer might not be able to authenticate the user's credentials.</span></span>

<span data-ttu-id="1d1ad-284">Pour activer l’authentification, utilisez la commande suivante pour ajouter l’ordinateur distant à la liste des hôtes approuvés pour l’ordinateur local dans WinRM.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-284">To enable authentication, use the following command to add the remote computer to the list of trusted hosts for the local computer in WinRM.</span></span> <span data-ttu-id="1d1ad-285">Tapez la commande à l’invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-285">Type the command at the PowerShell prompt.</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

<span data-ttu-id="1d1ad-286">Par exemple, pour ajouter l’ordinateur SERVEUR01 à la liste des hôtes approuvés sur l’ordinateur local, tapez la commande suivante à l’invite de commandes PowerShell :</span><span class="sxs-lookup"><span data-stu-id="1d1ad-286">For example, to add the Server01 computer to the list of trusted hosts on the local computer, type the following command at the PowerShell prompt:</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```

### <a name="does-powershell-support-remoting-over-ssh"></a><span data-ttu-id="1d1ad-287">PowerShell prend-il en charge la communication à distance via SSH ?</span><span class="sxs-lookup"><span data-stu-id="1d1ad-287">Does PowerShell support remoting over SSH?</span></span>

<span data-ttu-id="1d1ad-288">Oui.</span><span class="sxs-lookup"><span data-stu-id="1d1ad-288">Yes.</span></span> <span data-ttu-id="1d1ad-289">Pour plus d’informations, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="1d1ad-289">For more information, see [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d1ad-290">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d1ad-290">See also</span></span>

[<span data-ttu-id="1d1ad-291">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1d1ad-291">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="1d1ad-292">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1d1ad-292">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="1d1ad-293">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="1d1ad-293">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="1d1ad-294">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="1d1ad-294">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)

[<span data-ttu-id="1d1ad-295">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="1d1ad-295">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="1d1ad-296">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1d1ad-296">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="1d1ad-297">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="1d1ad-297">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
