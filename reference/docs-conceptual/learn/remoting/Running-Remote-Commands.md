---
ms.date: 08/21/2020
keywords: powershell,applet de commande
title: Exécution de commandes à distance
description: Explique les méthodes permettant d’exécuter des commandes sur des systèmes distants à l’aide de PowerShell.
ms.openlocfilehash: cff18a4f51c3ed8e3ed2c1f35862a88911e7ceb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391406"
---
# <a name="running-remote-commands"></a><span data-ttu-id="db410-104">Exécution de commandes à distance</span><span class="sxs-lookup"><span data-stu-id="db410-104">Running Remote Commands</span></span>

<span data-ttu-id="db410-105">Vous pouvez exécuter des commandes sur un ordinateur ou plusieurs centaines au moyen d'une seule commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db410-105">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="db410-106">Pour communiquer à distance, Windows PowerShell fait appel à différentes technologies, notamment WMI, RPC et WS-Management.</span><span class="sxs-lookup"><span data-stu-id="db410-106">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="db410-107">PowerShell Core prend en charge WMI, WS-Management et la communication à distance SSH.</span><span class="sxs-lookup"><span data-stu-id="db410-107">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="db410-108">Dans PowerShell 6, RPC n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="db410-108">In PowerShell 6, RPC is no longer supported.</span></span> <span data-ttu-id="db410-109">Dans PowerShell 7 et versions ultérieures, RPC est pris en charge uniquement dans Windows.</span><span class="sxs-lookup"><span data-stu-id="db410-109">In PowerShell 7 and above, RPC is supported only in Windows.</span></span>

<span data-ttu-id="db410-110">Pour plus d’informations sur la communication à distance dans PowerShell Core, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="db410-110">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="db410-111">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="db410-111">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="db410-112">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="db410-112">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="db410-113">Communication à distance Windows PowerShell sans configuration</span><span class="sxs-lookup"><span data-stu-id="db410-113">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="db410-114">De nombreuses applets de commande Windows PowerShell possèdent le paramètre ComputerName, qui vous permet de collecter des données et de modifier les paramètres sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="db410-114">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="db410-115">Ces cmdlets utilisent différents protocoles de communication et fonctionnent sur tous les systèmes d’exploitation Windows sans configuration spéciale.</span><span class="sxs-lookup"><span data-stu-id="db410-115">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="db410-116">Ces applets de commande sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="db410-116">These cmdlets include:</span></span>

- [<span data-ttu-id="db410-117">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="db410-117">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="db410-118">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="db410-118">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="db410-119">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="db410-119">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="db410-120">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="db410-120">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="db410-121">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="db410-121">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="db410-122">Get-Process</span><span class="sxs-lookup"><span data-stu-id="db410-122">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="db410-123">Get-Service</span><span class="sxs-lookup"><span data-stu-id="db410-123">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="db410-124">Set-Service</span><span class="sxs-lookup"><span data-stu-id="db410-124">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="db410-125">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="db410-125">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="db410-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="db410-126">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="db410-127">En général, les cmdlets qui prennent en charge la communication à distance sans configuration particulière possèdent le paramètre ComputerName. En revanche, elles ne possèdent pas le paramètre Session.</span><span class="sxs-lookup"><span data-stu-id="db410-127">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="db410-128">Pour trouver ces applets de commande dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="db410-128">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="db410-129">Communication à distance Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="db410-129">Windows PowerShell Remoting</span></span>

<span data-ttu-id="db410-130">La communication à distance Windows PowerShell, qui utilise le protocole WS-Management, vous permet d'exécuter n'importe quelle commande Windows PowerShell sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="db410-130">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="db410-131">Vous pouvez établir des connexions persistantes, démarrer des sessions interactives et exécuter des scripts sur ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="db410-131">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="db410-132">Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="db410-132">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="db410-133">Pour obtenir plus d’informations, notamment des instructions, voir [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="db410-133">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="db410-134">Après avoir configuré la communication à distance Windows PowerShell, vous avez le choix entre plusieurs stratégies de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="db410-134">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="db410-135">Cet article en répertorie quelques-unes.</span><span class="sxs-lookup"><span data-stu-id="db410-135">This article lists just a few of them.</span></span> <span data-ttu-id="db410-136">Pour plus d’informations, consultez [À propos de la communication à distance](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="db410-136">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="db410-137">Démarrer une session interactive</span><span class="sxs-lookup"><span data-stu-id="db410-137">Start an Interactive Session</span></span>

<span data-ttu-id="db410-138">Pour démarrer une session interactive avec un seul ordinateur distant, utilisez l'applet de commande [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="db410-138">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span> <span data-ttu-id="db410-139">Par exemple, pour démarrer une session interactive avec l'ordinateur distant Server01, tapez :</span><span class="sxs-lookup"><span data-stu-id="db410-139">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="db410-140">L'invite de commandes affiche alors le nom de l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="db410-140">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="db410-141">Toutes les commandes que vous tapez à l'invite sont exécutées sur l'ordinateur distant et les résultats sont affichés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="db410-141">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="db410-142">Pour terminer la session interactive, tapez :</span><span class="sxs-lookup"><span data-stu-id="db410-142">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="db410-143">Pour plus d’informations sur les cmdlets Enter-PSSession et Exit-PSSession, consultez :</span><span class="sxs-lookup"><span data-stu-id="db410-143">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="db410-144">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="db410-144">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="db410-145">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="db410-145">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="db410-146">Exécuter une commande à distance</span><span class="sxs-lookup"><span data-stu-id="db410-146">Run a Remote Command</span></span>

<span data-ttu-id="db410-147">Pour exécuter une commande sur un ou plusieurs ordinateurs, utilisez la cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="db410-147">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="db410-148">Par exemple, pour exécuter une commande [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) sur les ordinateurs distants Server01 et Server02, tapez :</span><span class="sxs-lookup"><span data-stu-id="db410-148">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="db410-149">La sortie est retournée à votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="db410-149">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="db410-150">Exécuter un script</span><span class="sxs-lookup"><span data-stu-id="db410-150">Run a Script</span></span>

<span data-ttu-id="db410-151">Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre FilePath de la cmdlet `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="db410-151">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="db410-152">Le script doit être accessible à votre ordinateur local ou se trouver sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="db410-152">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="db410-153">Les résultats sont retournés à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="db410-153">The results are returned to your local computer.</span></span>

<span data-ttu-id="db410-154">Par exemple, la commande suivante exécute le script DiskCollect.ps1 sur les ordinateurs distants Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="db410-154">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="db410-155">Établir une connexion persistante</span><span class="sxs-lookup"><span data-stu-id="db410-155">Establish a Persistent Connection</span></span>

<span data-ttu-id="db410-156">Utilisez la cmdlet `New-PSSession` pour créer une session persistante sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="db410-156">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="db410-157">L’exemple suivant crée des sessions distantes sur Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="db410-157">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="db410-158">Les objets de session sont stockés dans la variable `$s`.</span><span class="sxs-lookup"><span data-stu-id="db410-158">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="db410-159">Une fois les sessions établies, vous pouvez exécuter n'importe quelle commande dans celles-ci.</span><span class="sxs-lookup"><span data-stu-id="db410-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="db410-160">Les sessions étant persistantes, vous pouvez collecter des données à partir d’une seule commande et les utiliser dans une autre commande.</span><span class="sxs-lookup"><span data-stu-id="db410-160">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="db410-161">Par exemple, la commande suivante exécute une commande Get-Hotfix dans les sessions dans la variable $s et enregistre les résultats dans la variable $h.</span><span class="sxs-lookup"><span data-stu-id="db410-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="db410-162">La variable $h est créée dans chacune des sessions dans $s, mais elle n'existe pas dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="db410-162">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="db410-163">Vous pouvez désormais utiliser les données dans la variable `$h` avec d’autres commandes dans la même session.</span><span class="sxs-lookup"><span data-stu-id="db410-163">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="db410-164">Les résultats sont affichés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="db410-164">The results are displayed on the local computer.</span></span> <span data-ttu-id="db410-165">Exemple :</span><span class="sxs-lookup"><span data-stu-id="db410-165">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="db410-166">Communication à distance avancée</span><span class="sxs-lookup"><span data-stu-id="db410-166">Advanced Remoting</span></span>

<span data-ttu-id="db410-167">Dans Windows PowerShell, la gestion à distance n'est qu'un début.</span><span class="sxs-lookup"><span data-stu-id="db410-167">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="db410-168">Grâce aux applets de commande installées avec Windows PowerShell, vous pouvez établir et configurer des sessions à distance à partir des extrémités locales et distantes, créer des sessions personnalisées et restreintes, permettre aux utilisateurs d'importer à partir d'une session à distance des commandes qui s'exécutent de manière implicite sur la session à distance, configurer la sécurité d'une session à distance, etc.</span><span class="sxs-lookup"><span data-stu-id="db410-168">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="db410-169">Windows PowerShell inclut un fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="db410-169">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="db410-170">Le fournisseur crée un lecteur `WSMAN:` qui vous permet de parcourir une hiérarchie de paramètres de configuration sur l'ordinateur local et les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="db410-170">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="db410-171">Pour plus d’informations sur le fournisseur WSMan, consultez [Fournisseur WSMan](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) et [À propos des cmdlets WS-Management](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets) ou tapez `Get-Help wsman` dans la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db410-171">For more information about the WSMan provider, see [WSMan Provider](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) and [About WS-Management Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="db410-172">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="db410-172">For more information, see:</span></span>

- [<span data-ttu-id="db410-173">about_Remote</span><span class="sxs-lookup"><span data-stu-id="db410-173">About Remote FAQ</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="db410-174">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="db410-174">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [<span data-ttu-id="db410-175">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="db410-175">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

<span data-ttu-id="db410-176">Pour obtenir de l'aide sur les erreurs de communication à distance, consultez [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting).</span><span class="sxs-lookup"><span data-stu-id="db410-176">For help with remoting errors, see [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting).</span></span>

## <a name="see-also"></a><span data-ttu-id="db410-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db410-177">See Also</span></span>

- [<span data-ttu-id="db410-178">about_Remote</span><span class="sxs-lookup"><span data-stu-id="db410-178">about_Remote</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="db410-179">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="db410-179">about_Remote_FAQ</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="db410-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="db410-180">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
- [<span data-ttu-id="db410-181">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="db410-181">about_Remote_Troubleshooting</span></span>](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting)
- [<span data-ttu-id="db410-182">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="db410-182">about_PSSessions</span></span>](/powershell/module/microsoft.powershell.core/about/about_PSSessions)
- [<span data-ttu-id="db410-183">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="db410-183">about_WS-Management_Cmdlets</span></span>](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets)
- [<span data-ttu-id="db410-184">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="db410-184">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="db410-185">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="db410-185">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)
- [<span data-ttu-id="db410-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="db410-186">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="db410-187">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="db410-187">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [<span data-ttu-id="db410-188">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="db410-188">WSMan Provider</span></span>](/powershell/module/microsoft.wsman.management/about/about_wsman_provider)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
