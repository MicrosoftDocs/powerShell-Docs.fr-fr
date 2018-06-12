---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Exécution de commandes à distance
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: d21d1def1e25895f65b3578bf2892d56f14cc150
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482877"
---
# <a name="running-remote-commands"></a><span data-ttu-id="ca2b4-103">Exécution de commandes à distance</span><span class="sxs-lookup"><span data-stu-id="ca2b4-103">Running Remote Commands</span></span>

<span data-ttu-id="ca2b4-104">Vous pouvez exécuter des commandes sur un ordinateur ou plusieurs centaines au moyen d'une seule commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="ca2b4-105">Pour communiquer à distance, Windows PowerShell fait appel à différentes technologies, notamment WMI, RPC et WS-Management.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="ca2b4-106">Accès distant dans PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="ca2b4-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="ca2b4-107">PowerShell Core, l’édition la plus récente de PowerShell sur Windows, macOS et Linux, prend en charge WMI, WS-Management et l’accès distant SSH.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="ca2b4-108">(RPC n’est plus pris en charge.)</span><span class="sxs-lookup"><span data-stu-id="ca2b4-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="ca2b4-109">Pour plus d’informations sur la configuration de ceci, consultez :</span><span class="sxs-lookup"><span data-stu-id="ca2b4-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="ca2b4-110">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="ca2b4-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="ca2b4-111">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="ca2b4-111">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="ca2b4-112">Communication à distance sans configuration</span><span class="sxs-lookup"><span data-stu-id="ca2b4-112">Remoting Without Configuration</span></span>

<span data-ttu-id="ca2b4-113">De nombreuses applets de commande Windows PowerShell possèdent le paramètre ComputerName, qui vous permet de collecter des données et de modifier les paramètres sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="ca2b4-114">Elles utilisent diverses technologies de communication et bon nombre d'entre elles fonctionnent sur tous les systèmes d'exploitation Windows pris en charge par Windows PowerShell, et ce sans configuration particulière.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="ca2b4-115">Ces applets de commande sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ca2b4-115">These cmdlets include:</span></span>

* [<span data-ttu-id="ca2b4-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="ca2b4-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="ca2b4-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="ca2b4-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="ca2b4-118">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="ca2b4-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="ca2b4-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="ca2b4-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="ca2b4-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="ca2b4-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="ca2b4-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="ca2b4-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="ca2b4-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="ca2b4-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="ca2b4-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="ca2b4-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="ca2b4-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="ca2b4-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="ca2b4-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="ca2b4-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="ca2b4-126">En général, les applets de commande qui prennent en charge la communication à distance sans configuration particulière possèdent le paramètre ComputerName. En revanche, elles ne possèdent pas le paramètre Session.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="ca2b4-127">Pour trouver ces applets de commande dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="ca2b4-127">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="ca2b4-128">Communication à distance Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca2b4-128">Windows PowerShell Remoting</span></span>

<span data-ttu-id="ca2b4-129">La communication à distance Windows PowerShell, qui utilise le protocole WS-Management, vous permet d'exécuter n'importe quelle commande Windows PowerShell sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="ca2b4-130">Vous pouvez ainsi établir des connexions persistantes, démarrer des sessions interactives 1:1 et exécuter des scripts sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="ca2b4-131">Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="ca2b4-132">Pour obtenir plus d’informations, notamment des instructions, voir [about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="ca2b4-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/library/dd315349.aspx).</span></span>

<span data-ttu-id="ca2b4-133">Après avoir configuré la communication à distance Windows PowerShell, vous avez le choix entre plusieurs stratégies de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="ca2b4-134">Le reste de ce document répertorie quelques-unes d'entre elles.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="ca2b4-135">Pour plus d’informations, voir [À propos de la connexion à distance](https://technet.microsoft.com/library/dd347744.aspx) et [FAQ de la connexion à distance](https://technet.microsoft.com/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="ca2b4-135">For more information, see [About Remote](https://technet.microsoft.com/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="ca2b4-136">Démarrer une session interactive</span><span class="sxs-lookup"><span data-stu-id="ca2b4-136">Start an Interactive Session</span></span>

<span data-ttu-id="ca2b4-137">Pour démarrer une session interactive avec un seul ordinateur distant, utilisez l’applet de commande [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).</span><span class="sxs-lookup"><span data-stu-id="ca2b4-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="ca2b4-138">Par exemple, pour démarrer une session interactive avec l'ordinateur distant Server01, tapez :</span><span class="sxs-lookup"><span data-stu-id="ca2b4-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="ca2b4-139">L'invite de commandes affiche alors le nom de l'ordinateur auquel vous êtes connecté.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="ca2b4-140">À partir de là, toutes les commandes que vous tapez à l'invite sont exécutées sur l'ordinateur distant et les résultats sont affichés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="ca2b4-141">Pour terminer la session interactive, tapez :</span><span class="sxs-lookup"><span data-stu-id="ca2b4-141">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="ca2b4-142">Pour plus d’informations sur les applets de commande Enter-PSSession et Exit-PSSession, voir [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) et [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="ca2b4-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="ca2b4-143">Exécuter une commande à distance</span><span class="sxs-lookup"><span data-stu-id="ca2b4-143">Run a Remote Command</span></span>

<span data-ttu-id="ca2b4-144">Pour exécuter une commande sur un ou plusieurs ordinateurs distants, utilisez l’applet de commande [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="ca2b4-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="ca2b4-145">Par exemple, pour exécuter une commande [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) sur les ordinateurs distants Serveur01 et Serveur02, tapez :</span><span class="sxs-lookup"><span data-stu-id="ca2b4-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="ca2b4-146">La sortie est retournée à votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-146">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

<span data-ttu-id="ca2b4-147">Pour plus d’informations sur l’applet de commande Invoke-Command, voir [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="ca2b4-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="ca2b4-148">Exécuter un script</span><span class="sxs-lookup"><span data-stu-id="ca2b4-148">Run a Script</span></span>

<span data-ttu-id="ca2b4-149">Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre FilePath de l'applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="ca2b4-150">Le script doit être accessible à votre ordinateur local ou se trouver sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="ca2b4-151">Les résultats sont retournés à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="ca2b4-152">Par exemple, la commande suivante exécute le script DiskCollect.ps1 sur les ordinateurs distants Server01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="ca2b4-153">Pour plus d’informations sur l’applet de commande Invoke-Command, voir [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="ca2b4-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="ca2b4-154">Établir une connexion persistante</span><span class="sxs-lookup"><span data-stu-id="ca2b4-154">Establish a Persistent Connection</span></span>

<span data-ttu-id="ca2b4-155">Pour exécuter une série de commandes associées qui partagent des données, créez une session sur l'ordinateur distant, puis utilisez l'applet de commande Invoke-Command pour exécuter des commandes dans la session créée.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="ca2b4-156">Pour créer une session à distance, utilisez l'applet de commande New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="ca2b4-157">Par exemple, la commande suivante crée une session à distance sur l'ordinateur Server01 et une autre session à distance sur l'ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="ca2b4-158">Elle enregistre les objets de session dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-158">It saves the session objects in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="ca2b4-159">Une fois les sessions établies, vous pouvez exécuter n'importe quelle commande dans celles-ci.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="ca2b4-160">Les sessions étant persistantes, vous pouvez collecter des données en une seule commande et les utiliser dans une commande ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="ca2b4-161">Par exemple, la commande suivante exécute une commande Get-Hotfix dans les sessions dans la variable $s et enregistre les résultats dans la variable $h.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="ca2b4-162">La variable $h est créée dans chacune des sessions dans $s, mais elle n'existe pas dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="ca2b4-163">Vous pouvez désormais utiliser les données dans la variable $h dans des commandes ultérieures, comme celle qui suit.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="ca2b4-164">Les résultats sont affichés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-164">The results are displayed on the local computer.</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="ca2b4-165">Communication à distance avancée</span><span class="sxs-lookup"><span data-stu-id="ca2b4-165">Advanced Remoting</span></span>

<span data-ttu-id="ca2b4-166">Dans Windows PowerShell, la gestion à distance n'est qu'un début.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="ca2b4-167">Grâce aux applets de commande installées avec Windows PowerShell, vous pouvez établir et configurer des sessions à distance à partir des extrémités locales et distantes, créer des sessions personnalisées et restreintes, permettre aux utilisateurs d'importer à partir d'une session à distance des commandes qui s'exécutent de manière implicite sur la session à distance, configurer la sécurité d'une session à distance, etc.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="ca2b4-168">Pour faciliter la configuration à distance, Windows PowerShell comprend un fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="ca2b4-169">Le lecteur WSMAN: créé par le fournisseur vous permet de parcourir une hiérarchie de paramètres de configuration sur l'ordinateur local et les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="ca2b4-170">Pour plus d’informations sur le fournisseur WSMan, voir [Fournisseur WSMan](https://technet.microsoft.com/library/dd819476.aspx) et [À propos des applets de commande WSMan](https://technet.microsoft.com/library/dd819481.aspx) ou tapez « Get-Help wsman » dans la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca2b4-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="ca2b4-171">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="ca2b4-171">For more information, see:</span></span>

- [<span data-ttu-id="ca2b4-172">About_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="ca2b4-172">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="ca2b4-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca2b4-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="ca2b4-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="ca2b4-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="ca2b4-175">Pour obtenir de l’aide sur les erreurs de communication à distance, voir [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="ca2b4-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca2b4-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca2b4-176">See Also</span></span>

- [<span data-ttu-id="ca2b4-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ca2b4-177">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="ca2b4-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="ca2b4-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="ca2b4-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="ca2b4-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="ca2b4-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="ca2b4-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="ca2b4-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="ca2b4-181">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="ca2b4-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="ca2b4-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="ca2b4-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="ca2b4-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="ca2b4-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="ca2b4-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="ca2b4-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ca2b4-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="ca2b4-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca2b4-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="ca2b4-187">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="ca2b4-187">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md