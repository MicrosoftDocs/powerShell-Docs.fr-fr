---
ms.date: 08/14/2018
keywords: powershell,applet de commande
title: Exécution de commandes à distance
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133136"
---
# <a name="running-remote-commands"></a><span data-ttu-id="538d1-103">Exécution de commandes à distance</span><span class="sxs-lookup"><span data-stu-id="538d1-103">Running Remote Commands</span></span>

<span data-ttu-id="538d1-104">Vous pouvez exécuter des commandes sur un ordinateur ou plusieurs centaines au moyen d'une seule commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="538d1-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="538d1-105">Pour communiquer à distance, Windows PowerShell fait appel à différentes technologies, notamment WMI, RPC et WS-Management.</span><span class="sxs-lookup"><span data-stu-id="538d1-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="538d1-106">PowerShell Core prend en charge WMI, WS-Management et la communication à distance SSH.</span><span class="sxs-lookup"><span data-stu-id="538d1-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="538d1-107">RPC n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="538d1-107">RPC is no longer supported.</span></span>

<span data-ttu-id="538d1-108">Pour plus d’informations sur la communication à distance dans PowerShell Core, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="538d1-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="538d1-109">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="538d1-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="538d1-110">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="538d1-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="538d1-111">Communication à distance Windows PowerShell sans configuration</span><span class="sxs-lookup"><span data-stu-id="538d1-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="538d1-112">De nombreuses applets de commande Windows PowerShell possèdent le paramètre ComputerName, qui vous permet de collecter des données et de modifier les paramètres sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="538d1-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="538d1-113">Ces cmdlets utilisent différents protocoles de communication et fonctionnent sur tous les systèmes d’exploitation Windows sans configuration spéciale.</span><span class="sxs-lookup"><span data-stu-id="538d1-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="538d1-114">Ces applets de commande sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="538d1-114">These cmdlets include:</span></span>

- [<span data-ttu-id="538d1-115">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="538d1-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="538d1-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="538d1-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="538d1-117">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="538d1-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="538d1-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="538d1-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="538d1-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="538d1-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="538d1-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="538d1-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="538d1-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="538d1-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="538d1-122">Set-Service</span><span class="sxs-lookup"><span data-stu-id="538d1-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="538d1-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="538d1-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="538d1-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="538d1-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="538d1-125">En général, les cmdlets qui prennent en charge la communication à distance sans configuration particulière possèdent le paramètre ComputerName. En revanche, elles ne possèdent pas le paramètre Session.</span><span class="sxs-lookup"><span data-stu-id="538d1-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="538d1-126">Pour trouver ces applets de commande dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="538d1-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="538d1-127">Communication à distance Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="538d1-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="538d1-128">La communication à distance Windows PowerShell, qui utilise le protocole WS-Management, vous permet d'exécuter n'importe quelle commande Windows PowerShell sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="538d1-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="538d1-129">Vous pouvez établir des connexions persistantes, démarrer des sessions interactives et exécuter des scripts sur ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="538d1-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="538d1-130">Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="538d1-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="538d1-131">Pour obtenir plus d’informations, notamment des instructions, voir [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="538d1-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="538d1-132">Après avoir configuré la communication à distance Windows PowerShell, vous avez le choix entre plusieurs stratégies de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="538d1-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="538d1-133">Cet article en répertorie quelques-unes.</span><span class="sxs-lookup"><span data-stu-id="538d1-133">This article lists just a few of them.</span></span> <span data-ttu-id="538d1-134">Pour plus d’informations, consultez [À propos de la communication à distance](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="538d1-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="538d1-135">Démarrer une session interactive</span><span class="sxs-lookup"><span data-stu-id="538d1-135">Start an Interactive Session</span></span>

<span data-ttu-id="538d1-136">Pour démarrer une session interactive avec un seul ordinateur distant, utilisez l’applet de commande [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="538d1-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="538d1-137">Par exemple, pour démarrer une session interactive avec l'ordinateur distant Server01, tapez :</span><span class="sxs-lookup"><span data-stu-id="538d1-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="538d1-138">L'invite de commandes affiche alors le nom de l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="538d1-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="538d1-139">Toutes les commandes que vous tapez à l'invite sont exécutées sur l'ordinateur distant et les résultats sont affichés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="538d1-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="538d1-140">Pour terminer la session interactive, tapez :</span><span class="sxs-lookup"><span data-stu-id="538d1-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="538d1-141">Pour plus d’informations sur les cmdlets Enter-PSSession et Exit-PSSession, consultez :</span><span class="sxs-lookup"><span data-stu-id="538d1-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="538d1-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="538d1-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="538d1-143">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="538d1-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="538d1-144">Exécuter une commande à distance</span><span class="sxs-lookup"><span data-stu-id="538d1-144">Run a Remote Command</span></span>

<span data-ttu-id="538d1-145">Pour exécuter une commande sur un ou plusieurs ordinateurs, utilisez la cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="538d1-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="538d1-146">Par exemple, pour exécuter une commande [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) sur les ordinateurs distants Serveur01 et Serveur02, tapez :</span><span class="sxs-lookup"><span data-stu-id="538d1-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="538d1-147">La sortie est retournée à votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="538d1-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="538d1-148">Exécuter un script</span><span class="sxs-lookup"><span data-stu-id="538d1-148">Run a Script</span></span>

<span data-ttu-id="538d1-149">Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre FilePath de la cmdlet `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="538d1-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="538d1-150">Le script doit être accessible à votre ordinateur local ou se trouver sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="538d1-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="538d1-151">Les résultats sont retournés à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="538d1-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="538d1-152">Par exemple, la commande suivante exécute le script DiskCollect.ps1 sur les ordinateurs distants Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="538d1-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="538d1-153">Établir une connexion persistante</span><span class="sxs-lookup"><span data-stu-id="538d1-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="538d1-154">Utilisez la cmdlet `New-PSSession` pour créer une session persistante sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="538d1-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="538d1-155">L’exemple suivant crée des sessions distantes sur Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="538d1-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="538d1-156">Les objets de session sont stockés dans la variable `$s`.</span><span class="sxs-lookup"><span data-stu-id="538d1-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="538d1-157">Une fois les sessions établies, vous pouvez exécuter n'importe quelle commande dans celles-ci.</span><span class="sxs-lookup"><span data-stu-id="538d1-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="538d1-158">Les sessions étant persistantes, vous pouvez collecter des données à partir d’une seule commande et les utiliser dans une autre commande.</span><span class="sxs-lookup"><span data-stu-id="538d1-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="538d1-159">Par exemple, la commande suivante exécute une commande Get-Hotfix dans les sessions dans la variable $s et enregistre les résultats dans la variable $h.</span><span class="sxs-lookup"><span data-stu-id="538d1-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="538d1-160">La variable $h est créée dans chacune des sessions dans $s, mais elle n'existe pas dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="538d1-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="538d1-161">Vous pouvez désormais utiliser les données dans la variable `$h` avec d’autres commandes dans la même session.</span><span class="sxs-lookup"><span data-stu-id="538d1-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="538d1-162">Les résultats sont affichés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="538d1-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="538d1-163">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="538d1-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="538d1-164">Communication à distance avancée</span><span class="sxs-lookup"><span data-stu-id="538d1-164">Advanced Remoting</span></span>

<span data-ttu-id="538d1-165">Dans Windows PowerShell, la gestion à distance n'est qu'un début.</span><span class="sxs-lookup"><span data-stu-id="538d1-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="538d1-166">Grâce aux applets de commande installées avec Windows PowerShell, vous pouvez établir et configurer des sessions à distance à partir des extrémités locales et distantes, créer des sessions personnalisées et restreintes, permettre aux utilisateurs d'importer à partir d'une session à distance des commandes qui s'exécutent de manière implicite sur la session à distance, configurer la sécurité d'une session à distance, etc.</span><span class="sxs-lookup"><span data-stu-id="538d1-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="538d1-167">Windows PowerShell inclut un fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="538d1-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="538d1-168">Le fournisseur crée un lecteur `WSMAN:` qui vous permet de parcourir une hiérarchie de paramètres de configuration sur l'ordinateur local et les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="538d1-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="538d1-169">Pour plus d’informations sur le fournisseur WSMan, consultez [Fournisseur WSMan](https://technet.microsoft.com/library/dd819476.aspx) et [À propos des cmdlets WS-Management](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets) ou tapez `Get-Help wsman` dans la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="538d1-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="538d1-170">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="538d1-170">For more information, see:</span></span>

- [<span data-ttu-id="538d1-171">About_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="538d1-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="538d1-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="538d1-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="538d1-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="538d1-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="538d1-174">Pour obtenir de l’aide sur les erreurs de communication à distance, voir [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="538d1-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="538d1-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="538d1-175">See Also</span></span>

- [<span data-ttu-id="538d1-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="538d1-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="538d1-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="538d1-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="538d1-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="538d1-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="538d1-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="538d1-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="538d1-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="538d1-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="538d1-181">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="538d1-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="538d1-182">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="538d1-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="538d1-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="538d1-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="538d1-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="538d1-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="538d1-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="538d1-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="538d1-186">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="538d1-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md