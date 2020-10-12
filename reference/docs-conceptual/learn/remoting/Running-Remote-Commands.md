---
ms.date: 08/21/2020
keywords: powershell,applet de commande
title: Exécution de commandes à distance
ms.openlocfilehash: f12d08b03757b24d1de50402b301faff193f27be
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91814733"
---
# <a name="running-remote-commands"></a><span data-ttu-id="55c80-103">Exécution de commandes à distance</span><span class="sxs-lookup"><span data-stu-id="55c80-103">Running Remote Commands</span></span>

<span data-ttu-id="55c80-104">Vous pouvez exécuter des commandes sur un ordinateur ou plusieurs centaines au moyen d'une seule commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55c80-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="55c80-105">Pour communiquer à distance, Windows PowerShell fait appel à différentes technologies, notamment WMI, RPC et WS-Management.</span><span class="sxs-lookup"><span data-stu-id="55c80-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="55c80-106">PowerShell Core prend en charge WMI, WS-Management et la communication à distance SSH.</span><span class="sxs-lookup"><span data-stu-id="55c80-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="55c80-107">Dans PowerShell 6, RPC n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="55c80-107">In PowerShell 6, RPC is no longer supported.</span></span> <span data-ttu-id="55c80-108">Dans PowerShell 7 et versions ultérieures, RPC est pris en charge uniquement dans Windows.</span><span class="sxs-lookup"><span data-stu-id="55c80-108">In PowerShell 7 and above, RPC is supported only in Windows.</span></span>

<span data-ttu-id="55c80-109">Pour plus d’informations sur la communication à distance dans PowerShell Core, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="55c80-109">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="55c80-110">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="55c80-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="55c80-111">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="55c80-111">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="55c80-112">Communication à distance Windows PowerShell sans configuration</span><span class="sxs-lookup"><span data-stu-id="55c80-112">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="55c80-113">De nombreuses applets de commande Windows PowerShell possèdent le paramètre ComputerName, qui vous permet de collecter des données et de modifier les paramètres sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="55c80-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="55c80-114">Ces cmdlets utilisent différents protocoles de communication et fonctionnent sur tous les systèmes d’exploitation Windows sans configuration spéciale.</span><span class="sxs-lookup"><span data-stu-id="55c80-114">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="55c80-115">Ces applets de commande sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="55c80-115">These cmdlets include:</span></span>

- [<span data-ttu-id="55c80-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="55c80-116">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="55c80-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="55c80-117">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="55c80-118">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="55c80-118">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="55c80-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="55c80-119">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="55c80-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="55c80-120">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="55c80-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="55c80-121">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="55c80-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="55c80-122">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="55c80-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="55c80-123">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="55c80-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="55c80-124">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="55c80-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="55c80-125">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="55c80-126">En général, les cmdlets qui prennent en charge la communication à distance sans configuration particulière possèdent le paramètre ComputerName. En revanche, elles ne possèdent pas le paramètre Session.</span><span class="sxs-lookup"><span data-stu-id="55c80-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="55c80-127">Pour trouver ces applets de commande dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="55c80-127">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="55c80-128">Communication à distance Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="55c80-128">Windows PowerShell Remoting</span></span>

<span data-ttu-id="55c80-129">La communication à distance Windows PowerShell, qui utilise le protocole WS-Management, vous permet d'exécuter n'importe quelle commande Windows PowerShell sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="55c80-129">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="55c80-130">Vous pouvez établir des connexions persistantes, démarrer des sessions interactives et exécuter des scripts sur ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="55c80-130">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="55c80-131">Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="55c80-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="55c80-132">Pour obtenir plus d’informations, notamment des instructions, voir [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="55c80-132">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="55c80-133">Après avoir configuré la communication à distance Windows PowerShell, vous avez le choix entre plusieurs stratégies de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="55c80-133">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="55c80-134">Cet article en répertorie quelques-unes.</span><span class="sxs-lookup"><span data-stu-id="55c80-134">This article lists just a few of them.</span></span> <span data-ttu-id="55c80-135">Pour plus d’informations, consultez [À propos de la communication à distance](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="55c80-135">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="55c80-136">Démarrer une session interactive</span><span class="sxs-lookup"><span data-stu-id="55c80-136">Start an Interactive Session</span></span>

<span data-ttu-id="55c80-137">Pour démarrer une session interactive avec un seul ordinateur distant, utilisez l'applet de commande [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="55c80-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span> <span data-ttu-id="55c80-138">Par exemple, pour démarrer une session interactive avec l'ordinateur distant Server01, tapez :</span><span class="sxs-lookup"><span data-stu-id="55c80-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="55c80-139">L'invite de commandes affiche alors le nom de l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="55c80-139">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="55c80-140">Toutes les commandes que vous tapez à l'invite sont exécutées sur l'ordinateur distant et les résultats sont affichés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="55c80-140">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="55c80-141">Pour terminer la session interactive, tapez :</span><span class="sxs-lookup"><span data-stu-id="55c80-141">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="55c80-142">Pour plus d’informations sur les cmdlets Enter-PSSession et Exit-PSSession, consultez :</span><span class="sxs-lookup"><span data-stu-id="55c80-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="55c80-143">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="55c80-143">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="55c80-144">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="55c80-144">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="55c80-145">Exécuter une commande à distance</span><span class="sxs-lookup"><span data-stu-id="55c80-145">Run a Remote Command</span></span>

<span data-ttu-id="55c80-146">Pour exécuter une commande sur un ou plusieurs ordinateurs, utilisez la cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="55c80-146">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="55c80-147">Par exemple, pour exécuter une commande [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) sur les ordinateurs distants Server01 et Server02, tapez :</span><span class="sxs-lookup"><span data-stu-id="55c80-147">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="55c80-148">La sortie est retournée à votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55c80-148">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="55c80-149">Exécuter un script</span><span class="sxs-lookup"><span data-stu-id="55c80-149">Run a Script</span></span>

<span data-ttu-id="55c80-150">Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre FilePath de la cmdlet `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="55c80-150">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="55c80-151">Le script doit être accessible à votre ordinateur local ou se trouver sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="55c80-151">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="55c80-152">Les résultats sont retournés à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="55c80-152">The results are returned to your local computer.</span></span>

<span data-ttu-id="55c80-153">Par exemple, la commande suivante exécute le script DiskCollect.ps1 sur les ordinateurs distants Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="55c80-153">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="55c80-154">Établir une connexion persistante</span><span class="sxs-lookup"><span data-stu-id="55c80-154">Establish a Persistent Connection</span></span>

<span data-ttu-id="55c80-155">Utilisez la cmdlet `New-PSSession` pour créer une session persistante sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="55c80-155">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="55c80-156">L’exemple suivant crée des sessions distantes sur Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="55c80-156">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="55c80-157">Les objets de session sont stockés dans la variable `$s`.</span><span class="sxs-lookup"><span data-stu-id="55c80-157">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="55c80-158">Une fois les sessions établies, vous pouvez exécuter n'importe quelle commande dans celles-ci.</span><span class="sxs-lookup"><span data-stu-id="55c80-158">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="55c80-159">Les sessions étant persistantes, vous pouvez collecter des données à partir d’une seule commande et les utiliser dans une autre commande.</span><span class="sxs-lookup"><span data-stu-id="55c80-159">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="55c80-160">Par exemple, la commande suivante exécute une commande Get-Hotfix dans les sessions dans la variable $s et enregistre les résultats dans la variable $h.</span><span class="sxs-lookup"><span data-stu-id="55c80-160">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="55c80-161">La variable $h est créée dans chacune des sessions dans $s, mais elle n'existe pas dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="55c80-161">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="55c80-162">Vous pouvez désormais utiliser les données dans la variable `$h` avec d’autres commandes dans la même session.</span><span class="sxs-lookup"><span data-stu-id="55c80-162">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="55c80-163">Les résultats sont affichés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="55c80-163">The results are displayed on the local computer.</span></span> <span data-ttu-id="55c80-164">Exemple :</span><span class="sxs-lookup"><span data-stu-id="55c80-164">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="55c80-165">Communication à distance avancée</span><span class="sxs-lookup"><span data-stu-id="55c80-165">Advanced Remoting</span></span>

<span data-ttu-id="55c80-166">Dans Windows PowerShell, la gestion à distance n'est qu'un début.</span><span class="sxs-lookup"><span data-stu-id="55c80-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="55c80-167">Grâce aux applets de commande installées avec Windows PowerShell, vous pouvez établir et configurer des sessions à distance à partir des extrémités locales et distantes, créer des sessions personnalisées et restreintes, permettre aux utilisateurs d'importer à partir d'une session à distance des commandes qui s'exécutent de manière implicite sur la session à distance, configurer la sécurité d'une session à distance, etc.</span><span class="sxs-lookup"><span data-stu-id="55c80-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="55c80-168">Windows PowerShell inclut un fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="55c80-168">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="55c80-169">Le fournisseur crée un lecteur `WSMAN:` qui vous permet de parcourir une hiérarchie de paramètres de configuration sur l'ordinateur local et les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="55c80-169">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="55c80-170">Pour plus d’informations sur le fournisseur WSMan, consultez [Fournisseur WSMan](https://technet.microsoft.com/library/dd819476.aspx) et [À propos des cmdlets WS-Management](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets) ou tapez `Get-Help wsman` dans la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55c80-170">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="55c80-171">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="55c80-171">For more information, see:</span></span>

- [<span data-ttu-id="55c80-172">about_Remote</span><span class="sxs-lookup"><span data-stu-id="55c80-172">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="55c80-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="55c80-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="55c80-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="55c80-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="55c80-175">Pour obtenir de l'aide sur les erreurs de communication à distance, consultez [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="55c80-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="55c80-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55c80-176">See Also</span></span>

- [<span data-ttu-id="55c80-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="55c80-177">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="55c80-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="55c80-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="55c80-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="55c80-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="55c80-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="55c80-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="55c80-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="55c80-181">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="55c80-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="55c80-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="55c80-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="55c80-183">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="55c80-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="55c80-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="55c80-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="55c80-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="55c80-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="55c80-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="55c80-187">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="55c80-187">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
