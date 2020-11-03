---
description: Décrit comment résoudre les problèmes liés aux opérations distantes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: 33661392583393b69723449a914ace84f394fc94
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208929"
---
# <a name="about-remote-troubleshooting"></a><span data-ttu-id="72458-104">À propos du dépannage à distance</span><span class="sxs-lookup"><span data-stu-id="72458-104">About Remote Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="72458-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="72458-105">Short description</span></span>
<span data-ttu-id="72458-106">Décrit comment résoudre les problèmes liés aux opérations distantes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72458-106">Describes how to troubleshoot remote operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="72458-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="72458-107">Long description</span></span>

<span data-ttu-id="72458-108">Cette section décrit certains des problèmes que vous pouvez rencontrer lors de l’utilisation des fonctionnalités de communication à distance de PowerShell basées sur la technologie de WS-Management et qui suggère des solutions à ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="72458-108">This section describes some of the problems that you might encounter when using the remoting features of PowerShell that are based on WS-Management technology and it suggests solutions to these problems.</span></span>

<span data-ttu-id="72458-109">Avant d’utiliser la communication à distance PowerShell, consultez [about_Remote](about_remote.md) et [about_Remote_Requirements](about_Remote_Requirements.md) pour obtenir des conseils sur la configuration et l’utilisation de base.</span><span class="sxs-lookup"><span data-stu-id="72458-109">Before using PowerShell remoting, see [about_Remote](about_remote.md) and [about_Remote_Requirements](about_Remote_Requirements.md) for guidance on configuration and basic use.</span></span> <span data-ttu-id="72458-110">En outre, les rubriques d’aide de chacune des applets de commande de communication à distance, en particulier les descriptions des paramètres, ont des informations utiles conçues pour vous aider à éviter les problèmes.</span><span class="sxs-lookup"><span data-stu-id="72458-110">Also, the Help topics for each of the remoting cmdlets, particularly the parameter descriptions, have useful information that is designed to help you avoid problems.</span></span>

> [!NOTE]
> <span data-ttu-id="72458-111">Pour afficher ou modifier les paramètres de l’ordinateur local sur le lecteur WSMan :, y compris les modifications apportées aux configurations de session, aux hôtes approuvés, aux ports ou aux écouteurs, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="72458-111">To view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="troubleshooting-permission-and-authentication-issues"></a><span data-ttu-id="72458-112">Résolution des problèmes d’autorisation et d’authentification</span><span class="sxs-lookup"><span data-stu-id="72458-112">Troubleshooting permission and authentication issues</span></span>

<span data-ttu-id="72458-113">Cette section traite des problèmes de communication à distance liés aux autorisations de l’utilisateur et de l’ordinateur et aux exigences de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-113">This section discusses remoting problems that are related to user and computer permissions and remoting requirements.</span></span>

### <a name="how-to-run-as-administrator"></a><span data-ttu-id="72458-114">Comment exécuter en tant qu’administrateur</span><span class="sxs-lookup"><span data-stu-id="72458-114">How to run as administrator</span></span>

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

<span data-ttu-id="72458-115">Pour démarrer une session à distance sur l’ordinateur local, ou pour afficher ou modifier les paramètres de l’ordinateur local dans le lecteur WSMan :, y compris les modifications apportées aux configurations de session, aux hôtes approuvés, aux ports ou aux écouteurs, démarrez Windows PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="72458-115">To start a remote session on the local computer, or to view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start Windows PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="72458-116">Pour démarrer Windows PowerShell avec l’option **exécuter en tant qu’administrateur** :</span><span class="sxs-lookup"><span data-stu-id="72458-116">To start Windows PowerShell with the **Run as administrator** option:</span></span>

- <span data-ttu-id="72458-117">Cliquez avec le bouton droit sur une icône Windows PowerShell (ou Windows PowerShell ISE), puis cliquez sur **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="72458-117">Right-click a Windows PowerShell (or Windows PowerShell ISE) icon and then click **Run as administrator**.</span></span>

  <span data-ttu-id="72458-118">Pour démarrer Windows PowerShell avec l’option **exécuter en tant qu’administrateur** dans Windows 7 et windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="72458-118">To start Windows PowerShell with the **Run as administrator** option in Windows 7 and Windows Server 2008 R2.</span></span>

- <span data-ttu-id="72458-119">Dans la barre des tâches Windows, cliquez avec le bouton droit sur l’icône Windows PowerShell, puis cliquez sur **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="72458-119">In the Windows taskbar, right-click the Windows PowerShell icon, and then click **Run as administrator**.</span></span>

  <span data-ttu-id="72458-120">Dans Windows Server 2008 R2, l’icône Windows PowerShell est épinglée par défaut à la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="72458-120">In Windows Server 2008 R2, the Windows PowerShell icon is pinned to the taskbar by default.</span></span>

### <a name="how-to-enable-remoting"></a><span data-ttu-id="72458-121">Comment activer la communication à distance</span><span class="sxs-lookup"><span data-stu-id="72458-121">How to enable remoting</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

<span data-ttu-id="72458-122">Aucune configuration n’est requise pour permettre à un ordinateur d’envoyer des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="72458-122">No configuration is required to enable a computer to send remote commands.</span></span>
<span data-ttu-id="72458-123">Toutefois, pour recevoir des commandes à distance, la communication à distance PowerShell doit être activée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="72458-123">However, to receive remote commands, PowerShell remoting must be enabled on the computer.</span></span> <span data-ttu-id="72458-124">L’activation de comprend le démarrage du service WinRM, la définition du type de démarrage pour le service WinRM sur automatique, la création d’écouteurs pour les connexions HTTP et HTTPs et la création de configurations de session par défaut.</span><span class="sxs-lookup"><span data-stu-id="72458-124">Enabling includes starting the WinRM service, setting the startup type for the WinRM service to Automatic, creating listeners for HTTP and HTTPS connections, and creating default session configurations.</span></span>

<span data-ttu-id="72458-125">La communication à distance Windows PowerShell est activée sur Windows Server 2012 et les versions plus récentes de Windows Server par défaut.</span><span class="sxs-lookup"><span data-stu-id="72458-125">Windows PowerShell remoting is enabled on Windows Server 2012 and newer releases of Windows Server by default.</span></span> <span data-ttu-id="72458-126">Sur tous les autres systèmes, exécutez l' `Enable-PSRemoting` applet de commande pour activer la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-126">On all other systems, run the `Enable-PSRemoting` cmdlet to enable remoting.</span></span> <span data-ttu-id="72458-127">Vous pouvez également exécuter l' `Enable-PSRemoting` applet de commande pour réactiver la communication à distance sur Windows server 2012 et les versions plus récentes de Windows Server si la communication à distance est désactivée.</span><span class="sxs-lookup"><span data-stu-id="72458-127">You can also run the `Enable-PSRemoting` cmdlet to re-enable remoting on Windows Server 2012 and newer releases of Windows Server if remoting is disabled.</span></span>

<span data-ttu-id="72458-128">Pour configurer un ordinateur pour qu’il reçoive des commandes à distance, utilisez l’applet de commande `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="72458-128">To configure a computer to receive remote commands, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="72458-129">La commande suivante active tous les paramètres distants requis, active les configurations de session et redémarre le service WinRM pour que les modifications soient effectives.</span><span class="sxs-lookup"><span data-stu-id="72458-129">The following command enables all required remote settings, enables the session configurations, and restarts the WinRM service to make the changes effective.</span></span>

`Enable-PSRemoting`

<span data-ttu-id="72458-130">Pour supprimer toutes les invites utilisateur, tapez :</span><span class="sxs-lookup"><span data-stu-id="72458-130">To suppress all user prompts, type:</span></span>

`Enable-PSRemoting -Force`

<span data-ttu-id="72458-131">Pour plus d’informations, consultez [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).</span><span class="sxs-lookup"><span data-stu-id="72458-131">For more information, see [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).</span></span>

### <a name="how-to-enable-remoting-in-an-enterprise"></a><span data-ttu-id="72458-132">Comment activer la communication à distance dans une entreprise</span><span class="sxs-lookup"><span data-stu-id="72458-132">How to enable remoting in an enterprise</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="72458-133">Pour permettre à un seul ordinateur de recevoir des commandes PowerShell à distance et d’accepter des connexions, utilisez l’applet de commande `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="72458-133">To enable a single computer to receive remote PowerShell commands and accept connections, use the `Enable-PSRemoting` cmdlet.</span></span>

<span data-ttu-id="72458-134">Pour activer la communication à distance pour plusieurs ordinateurs dans une entreprise, vous pouvez utiliser les options mises à l’échelle suivantes.</span><span class="sxs-lookup"><span data-stu-id="72458-134">To enable remoting for multiple computers in an enterprise, you can use the following scaled options.</span></span>

- <span data-ttu-id="72458-135">Pour configurer des écouteurs pour la communication à distance, activez la stratégie **de groupe autoriser la configuration automatique des écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="72458-135">To configure listeners for remoting, enable the **Allow automatic configuration of listeners** group policy.</span></span>

- <span data-ttu-id="72458-136">Pour définir le type de démarrage du Windows Remote Management (WinRM) sur automatique sur plusieurs ordinateurs, utilisez l' `Set-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="72458-136">To set the startup type of the Windows Remote Management (WinRM) to Automatic on multiple computers, use the `Set-Service` cmdlet.</span></span>

- <span data-ttu-id="72458-137">Pour activer une exception de pare-feu, utilisez la stratégie de groupe **pare-feu Windows : autoriser les exceptions de port local** .</span><span class="sxs-lookup"><span data-stu-id="72458-137">To enable a firewall exception, use the **Windows Firewall: Allow Local Port Exceptions** group policy.</span></span>

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a><span data-ttu-id="72458-138">Comment activer des écouteurs à l’aide d’une stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="72458-138">How to enable listeners by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="72458-139">Pour configurer les écouteurs pour tous les ordinateurs d’un domaine, activez la stratégie **autoriser la configuration automatique des écouteurs** dans le chemin d’accès stratégie de groupe suivant :</span><span class="sxs-lookup"><span data-stu-id="72458-139">To configure the listeners for all computers in a domain, enable the **Allow automatic configuration of listeners** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

<span data-ttu-id="72458-140">Activez la stratégie et spécifiez les filtres IPv4 et IPv6.</span><span class="sxs-lookup"><span data-stu-id="72458-140">Enable the policy and specify the IPv4 and IPv6 filters.</span></span> <span data-ttu-id="72458-141">Les caractères génériques ( `*` ) sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="72458-141">Wildcards (`*`) are permitted.</span></span>

### <a name="how-to-enable-remoting-on-public-networks"></a><span data-ttu-id="72458-142">Comment activer la communication à distance sur des réseaux publics</span><span class="sxs-lookup"><span data-stu-id="72458-142">How to enable remoting on public networks</span></span>

```
ERROR:  Unable to check the status of the firewall
```

<span data-ttu-id="72458-143">L' `Enable-PSRemoting` applet de commande renvoie cette erreur lorsque le réseau local est public et que le paramètre **SkipNetworkProfileCheck** n’est pas utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="72458-143">The `Enable-PSRemoting` cmdlet returns this error when the local network is public and the **SkipNetworkProfileCheck** parameter is not used in the command.</span></span>

<span data-ttu-id="72458-144">Sur les versions serveur de Windows, `Enable-PSRemoting` fonctionne sur tous les types d’emplacement réseau.</span><span class="sxs-lookup"><span data-stu-id="72458-144">On server versions of Windows, `Enable-PSRemoting` succeeds on all network location types.</span></span> <span data-ttu-id="72458-145">Elle crée des règles de pare-feu qui autorisent l’accès à distance aux réseaux privés et de domaine (« personnel » et « de travail »).</span><span class="sxs-lookup"><span data-stu-id="72458-145">It creates firewall rules that allow remote access to private and domain ("Home" and "Work") networks.</span></span> <span data-ttu-id="72458-146">Pour les réseaux publics, elle crée des règles de pare-feu qui autorisent l’accès à distance à partir du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="72458-146">For public networks, it creates firewall rules that allows remote access from the same local subnet.</span></span>

<span data-ttu-id="72458-147">Sur les versions client de Windows, `Enable-PSRemoting` fonctionne sur les réseaux privés et de domaine.</span><span class="sxs-lookup"><span data-stu-id="72458-147">On client versions of Windows, `Enable-PSRemoting` succeeds on private and domain networks.</span></span> <span data-ttu-id="72458-148">Par défaut, elle échoue sur les réseaux publics, mais si vous utilisez le paramètre **SkipNetworkProfileCheck** , `Enable-PSRemoting` réussit et crée une règle de pare-feu qui autorise le trafic à partir du même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="72458-148">By default, it fails on public networks, but if you use the **SkipNetworkProfileCheck** parameter, `Enable-PSRemoting` succeeds and creates a firewall rule that allows traffic from the same local subnet.</span></span>

<span data-ttu-id="72458-149">Pour supprimer la restriction de sous-réseau local sur les réseaux publics et autoriser l’accès à distance à partir de n’importe quel emplacement, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="72458-149">To remove the local subnet restriction on public networks and allow remote access from any location, run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="72458-150">L' `Set-NetFirewallRule` applet de commande est exportée par le module netsecurity.</span><span class="sxs-lookup"><span data-stu-id="72458-150">The `Set-NetFirewallRule` cmdlet is exported by the NetSecurity module.</span></span>

> [!NOTE]
> <span data-ttu-id="72458-151">Dans Windows PowerShell 2,0, sur les ordinateurs exécutant des versions serveur de Windows, `Enable-PSRemoting` crée des règles de pare-feu qui autorisent l’accès à distance sur des réseaux privés, de domaine et publics.</span><span class="sxs-lookup"><span data-stu-id="72458-151">In Windows PowerShell 2.0, on computers running server versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access on private, domain and public networks.</span></span> <span data-ttu-id="72458-152">Sur les ordinateurs qui exécutent des versions client de Windows, `Enable-PSRemoting` crée des règles de pare-feu qui autorisent l’accès à distance uniquement sur les réseaux privés et de domaine.</span><span class="sxs-lookup"><span data-stu-id="72458-152">On computers running client versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access only on private and domain networks.</span></span>

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a><span data-ttu-id="72458-153">Comment activer une exception de pare-feu à l’aide d’une stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="72458-153">How to enable a firewall exception by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="72458-154">Pour activer une exception de pare-feu pour dans tous les ordinateurs d’un domaine, activez la stratégie **pare-feu Windows : autoriser les exceptions de port local** dans le chemin d’accès stratégie de groupe suivant :</span><span class="sxs-lookup"><span data-stu-id="72458-154">To enable a firewall exception for in all computers in a domain, enable the **Windows Firewall: Allow local port exceptions** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

<span data-ttu-id="72458-155">Cette stratégie permet aux membres du groupe Administrateurs sur l’ordinateur d’utiliser le **pare-feu Windows** dans le **panneau de configuration** pour créer une exception de pare-feu pour le service Windows Remote Management.</span><span class="sxs-lookup"><span data-stu-id="72458-155">This policy allows members of the Administrators group on the computer to use **Windows Firewall** in **Control Panel** to create a firewall exception for the Windows Remote Management service.</span></span>

<span data-ttu-id="72458-156">Si la configuration de la stratégie est incorrecte, vous pouvez recevoir l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="72458-156">If the policy configuration is incorrect you may receive the following error:</span></span>

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

<span data-ttu-id="72458-157">Une erreur de configuration dans la stratégie génère une valeur vide pour la propriété **ListeningOn** .</span><span class="sxs-lookup"><span data-stu-id="72458-157">A configuration error in the policy results in an empty value for the **ListeningOn** property.</span></span> <span data-ttu-id="72458-158">Utilisez la commande suivante pour vérifier la valeur.</span><span class="sxs-lookup"><span data-stu-id="72458-158">Use the following command to check the value.</span></span>

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a><span data-ttu-id="72458-159">Comment définir le type de démarrage du service WinRM</span><span class="sxs-lookup"><span data-stu-id="72458-159">How to set the startup type of the WinRM service</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="72458-160">La communication à distance PowerShell dépend du service Windows Remote Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="72458-160">PowerShell remoting depends upon the Windows Remote Management (WinRM) service.</span></span>
<span data-ttu-id="72458-161">Le service doit être en cours d’exécution pour prendre en charge les commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="72458-161">The service must be running to support remote commands.</span></span>

<span data-ttu-id="72458-162">Sur les versions serveur de Windows, le type de démarrage du service Windows Remote Management (WinRM) est automatique.</span><span class="sxs-lookup"><span data-stu-id="72458-162">On server versions of Windows, the startup type of the Windows Remote Management (WinRM) service is Automatic.</span></span>

<span data-ttu-id="72458-163">Toutefois, sur les versions client de Windows, le service WinRM est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="72458-163">However, on client versions of Windows, the WinRM service is disabled by default.</span></span>

<span data-ttu-id="72458-164">Pour définir le type de démarrage d’un service sur un ordinateur distant, utilisez l’applet de commande `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="72458-164">To set the startup type of a service on a remote computer, use the `Set-Service` cmdlet.</span></span>

<span data-ttu-id="72458-165">Pour exécuter la commande sur plusieurs ordinateurs, vous pouvez créer un fichier texte ou un fichier CSV portant le nom de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="72458-165">To run the command on multiple computers, you can create a text file or CSV file of the computer names.</span></span>

<span data-ttu-id="72458-166">Par exemple, les commandes suivantes obtiennent une liste de noms d’ordinateurs à partir du `Servers.txt` fichier, puis définit le type de démarrage du service WinRM sur tous les ordinateurs sur **automatique**.</span><span class="sxs-lookup"><span data-stu-id="72458-166">For example, the following commands get a list of computer names from the `Servers.txt` file and then sets the startup type of the WinRM service on all of the computers to **Automatic**.</span></span>

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

<span data-ttu-id="72458-167">Pour afficher les résultats, utilisez l' `Get-WMIObject` applet de commande avec l’objet **Win32_Service** .</span><span class="sxs-lookup"><span data-stu-id="72458-167">To see the results use the `Get-WMIObject` cmdlet with the **Win32_Service** object.</span></span> <span data-ttu-id="72458-168">Pour plus d’informations, consultez [set-service](xref:Microsoft.PowerShell.Management.Set-Service).</span><span class="sxs-lookup"><span data-stu-id="72458-168">For more information, see [Set-Service](xref:Microsoft.PowerShell.Management.Set-Service).</span></span>

### <a name="how-to-recreate-the-default-session-configurations"></a><span data-ttu-id="72458-169">Comment recréer les configurations de session par défaut</span><span class="sxs-lookup"><span data-stu-id="72458-169">How to recreate the default session configurations</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="72458-170">Pour vous connecter à l’ordinateur local et exécuter des commandes à distance, l’ordinateur local doit inclure des configurations de session pour les commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="72458-170">To connect to the local computer and run commands remotely, the local computer must include session configurations for remote commands.</span></span>

<span data-ttu-id="72458-171">Lorsque vous utilisez `Enable-PSRemoting` , il crée des configurations de session par défaut sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="72458-171">When you use `Enable-PSRemoting`, it creates default session configurations on the local computer.</span></span> <span data-ttu-id="72458-172">Les utilisateurs distants utilisent ces configurations de session chaque fois qu’une commande à distance n’inclut pas le paramètre **ConfigurationName** .</span><span class="sxs-lookup"><span data-stu-id="72458-172">Remote users use these session configurations whenever a remote command does not include the **ConfigurationName** parameter.</span></span>

<span data-ttu-id="72458-173">Si les configurations par défaut sur un ordinateur ne sont pas inscrites ou supprimées, utilisez l' `Enable-PSRemoting` applet de commande pour les recréer.</span><span class="sxs-lookup"><span data-stu-id="72458-173">If the default configurations on a computer are unregistered or deleted, use the `Enable-PSRemoting` cmdlet to recreate them.</span></span> <span data-ttu-id="72458-174">Vous pouvez utiliser cette applet de commande à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="72458-174">You can use this cmdlet repeatedly.</span></span> <span data-ttu-id="72458-175">Elle ne génère pas d’erreurs si une fonctionnalité est déjà configurée.</span><span class="sxs-lookup"><span data-stu-id="72458-175">It does not generate errors if a feature is already configured.</span></span>

<span data-ttu-id="72458-176">Si vous modifiez les configurations de session par défaut et souhaitez restaurer les configurations de session par défaut d’origine, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer les configurations de session modifiées, puis utilisez l' `Enable-PSRemoting` applet de commande pour les restaurer.</span><span class="sxs-lookup"><span data-stu-id="72458-176">If you change the default session configurations and want to restore the original default session configurations, use the `Unregister-PSSessionConfiguration` cmdlet to delete the changed session configurations and then use the `Enable-PSRemoting` cmdlet to restore them.</span></span>
<span data-ttu-id="72458-177">`Enable-PSRemoting` ne modifie pas les configurations de session existantes.</span><span class="sxs-lookup"><span data-stu-id="72458-177">`Enable-PSRemoting` does not change existing session configurations.</span></span>

> [!NOTE]
> <span data-ttu-id="72458-178">Lorsque `Enable-PSRemoting` restaure la configuration de session par défaut, elle ne crée pas de descripteurs de sécurité explicites pour les configurations.</span><span class="sxs-lookup"><span data-stu-id="72458-178">When `Enable-PSRemoting` restores the default session configuration, it does not create explicit security descriptors for the configurations.</span></span> <span data-ttu-id="72458-179">Au lieu de cela, les configurations héritent du descripteur de sécurité de RootSDDL, qui est sécurisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="72458-179">Instead, the configurations inherit the security descriptor of the RootSDDL, which is secure by default.</span></span>

<span data-ttu-id="72458-180">Pour afficher le descripteur de sécurité RootSDDL, tapez :</span><span class="sxs-lookup"><span data-stu-id="72458-180">To see the RootSDDL security descriptor, type:</span></span>

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

<span data-ttu-id="72458-181">Pour modifier le RootSDDL, utilisez l' `Set-Item` applet de commande dans le lecteur WSMan :.</span><span class="sxs-lookup"><span data-stu-id="72458-181">To change the RootSDDL, use the `Set-Item` cmdlet in the WSMan: drive.</span></span> <span data-ttu-id="72458-182">Pour modifier le descripteur de sécurité d’une configuration de session, utilisez l’applet de commande `Set-PSSessionConfiguration` avec les paramètres **SecurityDescriptorSDDL** ou **ShowSecurityDescriptorUI** .</span><span class="sxs-lookup"><span data-stu-id="72458-182">To change the security descriptor of a session configuration, use the `Set-PSSessionConfiguration` cmdlet with the **SecurityDescriptorSDDL** or **ShowSecurityDescriptorUI** parameters.</span></span>

<span data-ttu-id="72458-183">Pour plus d’informations sur le lecteur WSMan :, consultez la rubrique d’aide pour le fournisseur WSMan (« obtenir-Help WSMan »).</span><span class="sxs-lookup"><span data-stu-id="72458-183">For more information about the WSMan: drive, see the Help topic for the WSMan provider ("Get-Help wsman").</span></span>

### <a name="how-to-provide-administrator-credentials"></a><span data-ttu-id="72458-184">Comment fournir des informations d’identification d’administrateur</span><span class="sxs-lookup"><span data-stu-id="72458-184">How to provide administrator credentials</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="72458-185">Pour créer une session PSSession ou exécuter des commandes sur un ordinateur distant, par défaut, l’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="72458-185">To create a PSSession or run commands on a remote computer, by default, the current user must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="72458-186">Les informations d’identification sont parfois nécessaires même lorsque l’utilisateur actuel est connecté à un compte membre du groupe administrateurs.</span><span class="sxs-lookup"><span data-stu-id="72458-186">Credentials are sometimes required even when the current user is logged on to an account that is a member of the Administrators group.</span></span>

<span data-ttu-id="72458-187">Si l’utilisateur actuel est membre du groupe Administrateurs sur l’ordinateur distant, ou peut fournir les informations d’identification d’un membre du groupe administrateurs, utilisez le paramètre **Credential** des `New-PSSession` `Enter-PSSession` `Invoke-Command` applets de commande ou pour vous connecter à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-187">If the current user is a member of the Administrators group on the remote computer, or can provide the credentials of a member of the Administrators group, use the **Credential** parameter of the `New-PSSession`, `Enter-PSSession` or `Invoke-Command` cmdlets to connect remotely.</span></span>

<span data-ttu-id="72458-188">Par exemple, la commande suivante fournit les informations d’identification d’un administrateur.</span><span class="sxs-lookup"><span data-stu-id="72458-188">For example, the following command provides the credentials of an Administrator.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="72458-189">Pour plus d’informations sur le paramètre **Credential** , consultez [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) ou [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).</span><span class="sxs-lookup"><span data-stu-id="72458-189">For more information about the **Credential** parameter, see [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).</span></span>

### <a name="how-to-enable-remoting-for-non-administrative-users"></a><span data-ttu-id="72458-190">Comment activer la communication à distance pour les utilisateurs non-administrateurs</span><span class="sxs-lookup"><span data-stu-id="72458-190">How to enable remoting for non-administrative users</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="72458-191">Pour établir une session PSSession ou exécuter une commande sur un ordinateur distant, l’utilisateur doit avoir l’autorisation d’utiliser les configurations de session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="72458-191">To establish a PSSession or run a command on a remote computer, the user must have permission to use the session configurations on the remote computer.</span></span>

<span data-ttu-id="72458-192">Par défaut, seuls les membres du groupe Administrateurs sur un ordinateur sont autorisés à utiliser les configurations de session par défaut.</span><span class="sxs-lookup"><span data-stu-id="72458-192">By default, only members of the Administrators group on a computer have permission to use the default session configurations.</span></span> <span data-ttu-id="72458-193">Par conséquent, seuls les membres du groupe administrateurs peuvent se connecter à l’ordinateur à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-193">Therefore, only members of the Administrators group can connect to the computer remotely.</span></span>

<span data-ttu-id="72458-194">Pour permettre à d’autres utilisateurs de se connecter à l’ordinateur local, accordez à l’utilisateur des autorisations d’exécution sur les configurations de session par défaut sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="72458-194">To allow other users to connect to the local computer, give the user Execute permissions to the default session configurations on the local computer.</span></span>

<span data-ttu-id="72458-195">La commande suivante ouvre une feuille de propriétés qui vous permet de modifier le descripteur de sécurité de la configuration de session Microsoft. PowerShell par défaut sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="72458-195">The following command opens a property sheet that lets you change the security descriptor of the default Microsoft.PowerShell session configuration on the local computer.</span></span>

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

<span data-ttu-id="72458-196">Pour plus d’informations, consultez [about_session_configurations](about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="72458-196">For more information, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a><span data-ttu-id="72458-197">Comment activer la communication à distance pour les administrateurs dans d’autres domaines</span><span class="sxs-lookup"><span data-stu-id="72458-197">How to enable remoting for administrators in other domains</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="72458-198">Lorsqu’un utilisateur d’un autre domaine est membre du groupe Administrateurs sur l’ordinateur local, l’utilisateur ne peut pas se connecter à distance à l’ordinateur local avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="72458-198">When a user in another domain is a member of the Administrators group on the local computer, the user cannot connect to the local computer remotely with Administrator privileges.</span></span> <span data-ttu-id="72458-199">Par défaut, les connexions à distance à partir d’autres domaines s’exécutent avec uniquement des jetons de privilège d’utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="72458-199">By default, remote connections from other domains run with only standard user privilege tokens.</span></span>

<span data-ttu-id="72458-200">Toutefois, vous pouvez utiliser l’entrée de Registre **LocalAccountTokenFilterPolicy** pour modifier le comportement par défaut et autoriser les utilisateurs distants qui sont membres du groupe administrateurs à s’exécuter avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="72458-200">However, you can use the **LocalAccountTokenFilterPolicy** registry entry to change the default behavior and allow remote users who are members of the Administrators group to run with Administrator privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="72458-201">L’entrée **LocalAccountTokenFilterPolicy** désactive les restrictions distantes du contrôle de compte d’utilisateur pour tous les utilisateurs de tous les ordinateurs concernés.</span><span class="sxs-lookup"><span data-stu-id="72458-201">The **LocalAccountTokenFilterPolicy** entry disables user account control (UAC) remote restrictions for all users of all affected computers.</span></span> <span data-ttu-id="72458-202">Examinez attentivement les implications de ce paramètre avant de modifier la stratégie.</span><span class="sxs-lookup"><span data-stu-id="72458-202">Consider the implications of this setting carefully before changing the policy.</span></span>

<span data-ttu-id="72458-203">Pour modifier la stratégie, utilisez la commande suivante pour définir la valeur de l’entrée de Registre **LocalAccountTokenFilterPolicy** sur 1.</span><span class="sxs-lookup"><span data-stu-id="72458-203">To change the policy, use the following command to set the value of the **LocalAccountTokenFilterPolicy** registry entry to 1.</span></span>

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a><span data-ttu-id="72458-204">Utilisation d’une adresse IP dans une commande à distance</span><span class="sxs-lookup"><span data-stu-id="72458-204">How to use an ip address in a remote command</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="72458-205">Le paramètre **ComputerName** des `New-PSSession` applets de commande, `Enter-PSSession` et `Invoke-Command` accepte une adresse IP en tant que valeur valide.</span><span class="sxs-lookup"><span data-stu-id="72458-205">The **ComputerName** parameter of the `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets accepts an IP address as a valid value.</span></span> <span data-ttu-id="72458-206">Toutefois, étant donné que l’authentification Kerberos ne prend pas en charge les adresses IP, l’authentification NTLM est utilisée par défaut chaque fois que vous spécifiez une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="72458-206">However, because Kerberos authentication does not support IP addresses, NTLM authentication is used by default whenever you specify an IP address.</span></span>

<span data-ttu-id="72458-207">Lorsque vous utilisez l’authentification NTLM, la procédure suivante est requise pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-207">When using NTLM authentication, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="72458-208">Configurez l’ordinateur pour le transport HTTPs ou ajoutez les adresses IP des ordinateurs distants à la liste TrustedHosts sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="72458-208">Configure the computer for HTTPS transport or add the IP addresses of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="72458-209">Utilisez le paramètre **Credential** dans toutes les commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="72458-209">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="72458-210">Cela est nécessaire même lorsque vous soumettez les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="72458-210">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a><span data-ttu-id="72458-211">Connexion à distance à partir d’un ordinateur basé sur un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="72458-211">How to connect remotely from a workgroup-based computer</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="72458-212">Lorsque l’ordinateur local n’est pas dans un domaine, la procédure suivante est requise pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-212">When the local computer is not in a domain, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="72458-213">Configurez l’ordinateur pour le transport HTTPs ou ajoutez les noms des ordinateurs distants à la liste TrustedHosts sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="72458-213">Configure the computer for HTTPS transport or add the names of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="72458-214">Vérifiez qu’un mot de passe est défini sur l’ordinateur basé sur un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="72458-214">Verify that a password is set on the workgroup-based computer.</span></span> <span data-ttu-id="72458-215">Si un mot de passe n’est pas défini ou si la valeur du mot de passe est vide, vous ne pouvez pas exécuter de commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="72458-215">If a password is not set or the password value is empty, you cannot run remote commands.</span></span>

   <span data-ttu-id="72458-216">Pour définir le mot de passe de votre compte d’utilisateur, utilisez comptes d’utilisateur dans le panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="72458-216">To set password for your user account, use User Accounts in Control Panel.</span></span>

1. <span data-ttu-id="72458-217">Utilisez le paramètre **Credential** dans toutes les commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="72458-217">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="72458-218">Cela est nécessaire même lorsque vous soumettez les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="72458-218">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a><span data-ttu-id="72458-219">Comment ajouter un ordinateur à la liste des hôtes approuvés</span><span class="sxs-lookup"><span data-stu-id="72458-219">How to add a computer to the trusted hosts list</span></span>

<span data-ttu-id="72458-220">L’élément TrustedHosts peut contenir une liste séparée par des virgules de noms d’ordinateur, d’adresses IP et de noms de domaine complets.</span><span class="sxs-lookup"><span data-stu-id="72458-220">The TrustedHosts item can contain a comma-separated list of computer names, IP addresses, and fully-qualified domain names.</span></span> <span data-ttu-id="72458-221">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="72458-221">Wildcards are permitted.</span></span>

<span data-ttu-id="72458-222">Pour afficher ou modifier la liste des hôtes approuvés, utilisez le lecteur WSMan :.</span><span class="sxs-lookup"><span data-stu-id="72458-222">To view or change the trusted host list, use the WSMan: drive.</span></span> <span data-ttu-id="72458-223">L’élément TrustedHost est dans le `WSMan:\localhost\Client` nœud.</span><span class="sxs-lookup"><span data-stu-id="72458-223">The TrustedHost item is in the `WSMan:\localhost\Client` node.</span></span>

<span data-ttu-id="72458-224">Seuls les membres du groupe Administrateurs sur l’ordinateur sont autorisés à modifier la liste des hôtes approuvés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="72458-224">Only members of the Administrators group on the computer have permission to change the list of trusted hosts on the computer.</span></span>

<span data-ttu-id="72458-225">ATTENTION : la valeur que vous définissez pour l’élément TrustedHosts affecte tous les utilisateurs de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="72458-225">Caution: The value that you set for the TrustedHosts item affects all users of the computer.</span></span>

<span data-ttu-id="72458-226">Pour afficher la liste des hôtes approuvés, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="72458-226">To view the list of trusted hosts, use the following command:</span></span>

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

<span data-ttu-id="72458-227">Vous pouvez également utiliser l' `Set-Location` applet de commande (alias = CD) pour naviguer dans le lecteur WSMan : vers l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="72458-227">You can also use the `Set-Location` cmdlet (alias = cd) to navigate though the WSMan: drive to the location.</span></span> <span data-ttu-id="72458-228">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="72458-228">For example:</span></span>

```powershell
cd WSMan:\localhost\Client; dir
```

<span data-ttu-id="72458-229">Pour ajouter tous les ordinateurs à la liste des hôtes approuvés, utilisez la commande suivante, qui place la valeur \* (tout) dans le nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="72458-229">To add all computers to the list of trusted hosts, use the following command, which places a value of \* (all) in the ComputerName</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

<span data-ttu-id="72458-230">Vous pouvez également utiliser un caractère générique ( `*` ) pour ajouter tous les ordinateurs d’un domaine particulier à la liste des hôtes approuvés.</span><span class="sxs-lookup"><span data-stu-id="72458-230">You can also use a wildcard character (`*`) to add all computers in a particular domain to the list of trusted hosts.</span></span> <span data-ttu-id="72458-231">Par exemple, la commande suivante ajoute tous les ordinateurs du domaine fabrikam à la liste des hôtes approuvés.</span><span class="sxs-lookup"><span data-stu-id="72458-231">For example, the following command adds all of the computers in the Fabrikam domain to the list of trusted hosts.</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

<span data-ttu-id="72458-232">Pour ajouter les noms de certains ordinateurs à la liste des hôtes approuvés, utilisez le format de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="72458-232">To add the names of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

<span data-ttu-id="72458-233">où chaque valeur `<ComputerName>` doit avoir le format suivant :</span><span class="sxs-lookup"><span data-stu-id="72458-233">where each value `<ComputerName>` must have the following format:</span></span>

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

<span data-ttu-id="72458-234">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="72458-234">For example:</span></span>

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

<span data-ttu-id="72458-235">Pour ajouter un nom d'ordinateur à une liste existante d'hôtes approuvés, enregistrez d'abord la valeur actuelle dans une variable, puis affectez-lui une liste séparée par des virgules qui inclut les valeurs actuelles et nouvelles.</span><span class="sxs-lookup"><span data-stu-id="72458-235">To add a computer name to an existing list of trusted hosts, first save the current value in a variable, and then set the value to a comma-separated list that includes the current and new values.</span></span>

<span data-ttu-id="72458-236">Par exemple, pour ajouter l'ordinateur Serveur01 à une liste existante d'hôtes approuvés, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="72458-236">For example, to add the Server01 computer to an existing list of trusted hosts, use the following command</span></span>

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

<span data-ttu-id="72458-237">Pour ajouter les adresses IP d’ordinateurs particuliers à la liste des hôtes approuvés, utilisez le format de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="72458-237">To add the IP addresses of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

<span data-ttu-id="72458-238">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="72458-238">For example:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

<span data-ttu-id="72458-239">Pour ajouter un ordinateur à la liste TrustedHosts d’un ordinateur distant, utilisez l' `Connect-WSMan` applet de commande pour ajouter un nœud pour l’ordinateur distant au lecteur WSMan : sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="72458-239">To add a computer to the TrustedHosts list of a remote computer, use the `Connect-WSMan` cmdlet to add a node for the remote computer to the WSMan: drive on the local computer.</span></span> <span data-ttu-id="72458-240">Utilisez ensuite une `Set-Item` commande pour ajouter l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="72458-240">Then use a `Set-Item` command to add the computer.</span></span>

<span data-ttu-id="72458-241">Pour plus d’informations sur l’applet de commande `Connect-WSMan` , consultez [connect-wsman](xref:Microsoft.WSMan.Management.Connect-WSMan).</span><span class="sxs-lookup"><span data-stu-id="72458-241">For more information about the `Connect-WSMan` cmdlet, see [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span>

## <a name="troubleshooting-computer-configuration-issues"></a><span data-ttu-id="72458-242">Résolution des problèmes de configuration de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="72458-242">Troubleshooting computer configuration issues</span></span>

<span data-ttu-id="72458-243">Cette section traite des problèmes de communication à distance liés à des configurations particulières d’un ordinateur, d’un domaine ou d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="72458-243">This section discusses remoting problems that are related to particular configurations of a computer, domain, or enterprise.</span></span>

### <a name="how-to-configure-remoting-on-alternate-ports"></a><span data-ttu-id="72458-244">Comment configurer la communication à distance sur d’autres ports</span><span class="sxs-lookup"><span data-stu-id="72458-244">How to configure remoting on alternate ports</span></span>

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="72458-245">La communication à distance PowerShell utilise le port 80 pour le transport HTTP par défaut.</span><span class="sxs-lookup"><span data-stu-id="72458-245">PowerShell remoting uses port 80 for HTTP transport by default.</span></span> <span data-ttu-id="72458-246">Le port par défaut est utilisé chaque fois que l’utilisateur ne spécifie pas les paramètres **ConnectionUri** ou **port** dans une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-246">The default port is used whenever the user does not specify the **ConnectionURI** or **Port** parameters in a remote command.</span></span>

<span data-ttu-id="72458-247">Pour modifier le port par défaut utilisé par PowerShell, utilisez `Set-Item` l’applet de commande du lecteur WSMan : pour modifier la valeur du port dans le nœud terminal de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="72458-247">To change the default port that PowerShell uses, use `Set-Item` cmdlet in the WSMan: drive to change the Port value in the listener leaf node.</span></span>

<span data-ttu-id="72458-248">Par exemple, la commande suivante change le port par défaut en 8080.</span><span class="sxs-lookup"><span data-stu-id="72458-248">For example, the following command changes the default port to 8080.</span></span>

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a><span data-ttu-id="72458-249">Comment configurer la communication à distance avec un serveur proxy</span><span class="sxs-lookup"><span data-stu-id="72458-249">How to configure remoting with a proxy server</span></span>

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

<span data-ttu-id="72458-250">Étant donné que la communication à distance PowerShell utilise le protocole HTTP, elle est affectée par les paramètres du proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="72458-250">Because PowerShell remoting uses the HTTP protocol, it is affected by HTTP proxy settings.</span></span> <span data-ttu-id="72458-251">Dans les entreprises qui ont des serveurs proxy, les utilisateurs ne peuvent pas accéder directement à un ordinateur distant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72458-251">In enterprises that have proxy servers, users cannot access a PowerShell remote computer directly.</span></span>

<span data-ttu-id="72458-252">Pour résoudre ce problème, utilisez les options de paramètre de proxy dans votre commande à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-252">To resolve this problem, use proxy setting options in your remote command.</span></span> <span data-ttu-id="72458-253">Les options suivantes sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="72458-253">The following settings are available:</span></span>

- <span data-ttu-id="72458-254">ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="72458-254">ProxyAccessType</span></span>
- <span data-ttu-id="72458-255">ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="72458-255">ProxyAuthentication</span></span>
- <span data-ttu-id="72458-256">ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="72458-256">ProxyCredential</span></span>

<span data-ttu-id="72458-257">Pour définir ces options pour une commande particulière, utilisez la procédure suivante :</span><span class="sxs-lookup"><span data-stu-id="72458-257">To set these options for a particular command, use the following procedure:</span></span>

1. <span data-ttu-id="72458-258">Utilisez les paramètres **ProxyAccessType** , **ProxyAuthentication** et **ProxyCredential** de l' `New-PSSessionOption` applet de commande pour créer un objet d’option de session avec les paramètres de proxy de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="72458-258">Use the **ProxyAccessType** , **ProxyAuthentication** , and **ProxyCredential** parameters of the `New-PSSessionOption` cmdlet to create a session option object with the proxy settings for your enterprise.</span></span> <span data-ttu-id="72458-259">Enregistrer l’objet option est une variable.</span><span class="sxs-lookup"><span data-stu-id="72458-259">Save the option object is a variable.</span></span>

1. <span data-ttu-id="72458-260">Utilisez la variable qui contient l’objet option comme valeur du paramètre **SessionOption** d’une `New-PSSession` `Enter-PSSession` commande, ou `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="72458-260">Use the variable that contains the option object as the value of the **SessionOption** parameter of a `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` command.</span></span>

<span data-ttu-id="72458-261">Par exemple, la commande suivante crée un objet d’option de session avec des options de session proxy, puis utilise l’objet pour créer une session à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-261">For example, the following command creates a session option object with proxy session options and then uses the object to create a remote session.</span></span>

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

<span data-ttu-id="72458-262">Pour plus d’informations sur l’applet de commande `New-PSSessionOption` , consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="72458-262">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="72458-263">Pour définir ces options pour toutes les commandes distantes dans la session active, utilisez l’objet option qui `New-PSSessionOption` crée dans la valeur de la `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="72458-263">To set these options for all remote commands in the current session, use the option object that `New-PSSessionOption` creates in the value of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="72458-264">Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="72458-264">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="72458-265">Pour définir ces options pour toutes les commandes à distance, toutes les sessions PowerShell sur l’ordinateur local, ajoutez la `$PSSessionOption` variable de préférence à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72458-265">To set these options for all remote commands all PowerShell sessions on the local computer, add the `$PSSessionOption` preference variable to your PowerShell profile.</span></span> <span data-ttu-id="72458-266">Pour plus d’informations sur les profils PowerShell, voir [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="72458-266">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a><span data-ttu-id="72458-267">Comment détecter une session 32 bits sur un ordinateur 64 bits</span><span class="sxs-lookup"><span data-stu-id="72458-267">How to detect a 32-bit session on a 64-bit computer</span></span>

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="72458-268">Si l’ordinateur distant exécute une version 64 bits de Windows et que la commande à distance utilise une configuration de session 32 bits, telle que Microsoft. PowerShell32, Windows Remote Management (WinRM) charge un processus WOW64 et Windows redirige automatiquement toutes les références à l' `$env:Windir\System32` annuaire vers le `$env:Windir\SysWOW64` répertoire.</span><span class="sxs-lookup"><span data-stu-id="72458-268">If the remote computer is running a 64-bit version of Windows, and the remote command is using a 32-bit session configuration, such as Microsoft.PowerShell32, Windows Remote Management (WinRM) loads a WOW64 process and Windows automatically redirects all references to the `$env:Windir\System32` directory to the `$env:Windir\SysWOW64` directory.</span></span>

<span data-ttu-id="72458-269">Par conséquent, si vous essayez d’utiliser les outils du répertoire system32 qui n’ont pas d’équivalent dans le répertoire SysWow64, par exemple `Defrag.exe` , les outils sont introuvables dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="72458-269">As a result, if you try to use tools in the System32 directory that do not have counterparts in the SysWow64 directory, such as `Defrag.exe`, the tools cannot be found in the directory.</span></span>

<span data-ttu-id="72458-270">Pour Rechercher l’architecture de processeur utilisée dans la session, utilisez la valeur de la variable d’environnement **PROCESSOR_ARCHITECTURE** .</span><span class="sxs-lookup"><span data-stu-id="72458-270">To find the processor architecture that is being used in the session, use the value of the **PROCESSOR_ARCHITECTURE** environment variable.</span></span> <span data-ttu-id="72458-271">La commande suivante recherche l’architecture de processeur de la session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="72458-271">The following command finds the processor architecture of the session in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

<span data-ttu-id="72458-272">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="72458-272">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="troubleshooting-policy-and-preference-issues"></a><span data-ttu-id="72458-273">Résolution des problèmes de stratégie et de préférence</span><span class="sxs-lookup"><span data-stu-id="72458-273">Troubleshooting policy and preference issues</span></span>

<span data-ttu-id="72458-274">Cette section traite des problèmes de communication à distance liés aux stratégies et aux préférences définies sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="72458-274">This section discusses remoting problems that are related to policies and preferences set on the local and remote computers.</span></span>

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a><span data-ttu-id="72458-275">Comment modifier la stratégie d’exécution pour Import-PSSession et Import-Module</span><span class="sxs-lookup"><span data-stu-id="72458-275">How to change the execution policy for Import-PSSession and Import-Module</span></span>

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

<span data-ttu-id="72458-276">Les `Import-PSSession` applets de commande et `Export-PSSession` créent des modules qui contiennent des fichiers de script non signés et des fichiers de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="72458-276">The `Import-PSSession` and `Export-PSSession` cmdlets create modules that contains unsigned script files and formatting files.</span></span>

<span data-ttu-id="72458-277">Pour importer les modules créés par ces applets de commande, à l’aide de `Import-PSSession` ou de `Import-Module` , la stratégie d’exécution dans la session active ne peut pas être restreinte ou AllSigned.</span><span class="sxs-lookup"><span data-stu-id="72458-277">To import the modules that are created by these cmdlets, either by using `Import-PSSession` or `Import-Module`, the execution policy in the current session cannot be Restricted or AllSigned.</span></span> <span data-ttu-id="72458-278">Pour plus d’informations sur les stratégies d’exécution de PowerShell, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="72458-278">For information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="72458-279">Pour importer les modules sans modifier la stratégie d’exécution de l’ordinateur local qui est définie dans le registre, utilisez le paramètre **scope** de `Set-ExecutionPolicy` pour définir une stratégie d’exécution moins restrictive pour un processus unique.</span><span class="sxs-lookup"><span data-stu-id="72458-279">To import the modules without changing the execution policy for the local computer that is set in the registry, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>

<span data-ttu-id="72458-280">Par exemple, la commande suivante démarre un processus avec la `RemoteSigned` stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="72458-280">For example, the following command starts a process with the `RemoteSigned` execution policy.</span></span> <span data-ttu-id="72458-281">La modification de la stratégie d’exécution affecte uniquement le processus en cours et ne modifie pas le paramètre de Registre **ExecutionPolicy** PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72458-281">The execution policy change affects only the current process and does not change the PowerShell **ExecutionPolicy** registry setting.</span></span>

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="72458-282">Vous pouvez également utiliser le paramètre **ExecutionPolicy** de `PowerShell.exe` pour démarrer une seule session avec une stratégie d’exécution moins restrictive.</span><span class="sxs-lookup"><span data-stu-id="72458-282">You can also use the **ExecutionPolicy** parameter of `PowerShell.exe` to start a single session with a less restrictive execution policy.</span></span>

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="72458-283">Pour plus d’informations sur les stratégies d’exécution, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="72458-283">For more information about execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span> <span data-ttu-id="72458-284">Pour plus d'informations, voir `PowerShell.exe -?`.</span><span class="sxs-lookup"><span data-stu-id="72458-284">For more information, type `PowerShell.exe -?`.</span></span>

### <a name="how-to-set-and-change-quotas"></a><span data-ttu-id="72458-285">Définition et modification des quotas</span><span class="sxs-lookup"><span data-stu-id="72458-285">How to set and change quotas</span></span>

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

<span data-ttu-id="72458-286">Vous pouvez utiliser des quotas pour protéger l’ordinateur local et l’ordinateur distant contre une utilisation excessive des ressources, à la fois accidentelle et malveillante.</span><span class="sxs-lookup"><span data-stu-id="72458-286">You can use quotas to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span>

<span data-ttu-id="72458-287">Les quotas suivants sont disponibles dans la configuration de base.</span><span class="sxs-lookup"><span data-stu-id="72458-287">The following quotas are available in the basic configuration.</span></span>

- <span data-ttu-id="72458-288">Le fournisseur WSMan (WSMan :) fournit plusieurs paramètres de quota, tels que les paramètres **MaxEnvelopeSizekb** et **MaxProviderRequests** dans le `WSMan:<ComputerName>` nœud, ainsi que les paramètres **MaxConcurrentOperations** , **Propriétés MaxConcurrentOperationsPerUser** et **MaxConnections** dans le `WSMan:<ComputerName>\Service` nœud.</span><span class="sxs-lookup"><span data-stu-id="72458-288">The WSMan provider (WSMan:) provides several quota settings, such as the **MaxEnvelopeSizeKB** and **MaxProviderRequests** settings in the `WSMan:<ComputerName>` node and the **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** , and **MaxConnections** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="72458-289">Vous pouvez protéger l’ordinateur local à l’aide des paramètres **MaximumReceivedDataSizePerCommand** et **MaximumReceivedObjectSize** de l’applet de commande `New-PSSessionOption` et de la variable de `$PSSessionOption` préférence.</span><span class="sxs-lookup"><span data-stu-id="72458-289">You can protect the local computer by using the **MaximumReceivedDataSizePerCommand** and **MaximumReceivedObjectSize** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="72458-290">Vous pouvez protéger l’ordinateur distant en ajoutant des restrictions aux configurations de session, par exemple en utilisant les paramètres **MaximumReceivedDataSizePerCommandMB** et **MaximumReceivedObjectSizeMB** de l' `Register-PSSessionConfiguration` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="72458-290">You can protect the remote computer by adding restrictions to the session configurations, such as by using the **MaximumReceivedDataSizePerCommandMB** and **MaximumReceivedObjectSizeMB** parameters of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="72458-291">Lorsque les quotas sont en conflit avec une commande, PowerShell génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="72458-291">When quotas conflict with a command, PowerShell generates an error.</span></span>

<span data-ttu-id="72458-292">Pour résoudre l’erreur, modifiez la commande distante pour qu’elle soit conforme au quota.</span><span class="sxs-lookup"><span data-stu-id="72458-292">To resolve the error, change the remote command to comply with the quota.</span></span> <span data-ttu-id="72458-293">Ou bien, déterminez la source du quota, puis augmentez le quota pour permettre l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="72458-293">Or, determine the source of the quota, and then increase the quota to allow the command to complete.</span></span>

<span data-ttu-id="72458-294">Par exemple, la commande suivante augmente le quota de taille d’objet dans la configuration de session Microsoft. PowerShell sur l’ordinateur distant de 10 Mo (valeur par défaut) à 11 Mo.</span><span class="sxs-lookup"><span data-stu-id="72458-294">For example, the following command increases the object size quota in the Microsoft.PowerShell session configuration on the remote computer from 10 MB (the default value) to 11 MB.</span></span>

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

<span data-ttu-id="72458-295">Pour plus d’informations sur l’applet de commande `New-PSSessionOption` , consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="72458-295">For more information about the `New-PSSessionOption` cmdlet, see `New-PSSessionOption`.</span></span>

<span data-ttu-id="72458-296">Pour plus d’informations sur les quotas de WS-Management, consultez [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="72458-296">For more information about the WS-Management quotas, see [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).</span></span>

### <a name="how-to-resolve-timeout-errors"></a><span data-ttu-id="72458-297">Comment résoudre les erreurs de délai d’attente</span><span class="sxs-lookup"><span data-stu-id="72458-297">How to resolve timeout errors</span></span>

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

<span data-ttu-id="72458-298">Vous pouvez utiliser des délais d’attente pour protéger l’ordinateur local et l’ordinateur distant contre une utilisation excessive des ressources, à la fois accidentelle et malveillante.</span><span class="sxs-lookup"><span data-stu-id="72458-298">You can use timeouts to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span> <span data-ttu-id="72458-299">Lorsque des délais d’attente sont définis à la fois sur l’ordinateur local et sur l’ordinateur distant, PowerShell utilise les paramètres de délai d’expiration les plus courts.</span><span class="sxs-lookup"><span data-stu-id="72458-299">When timeouts are set on both the local and remote computer, PowerShell uses the shortest timeout settings.</span></span>

<span data-ttu-id="72458-300">Les délais d’attente suivants sont disponibles dans la configuration de base.</span><span class="sxs-lookup"><span data-stu-id="72458-300">The following timeouts are available in the basic configuration.</span></span>

- <span data-ttu-id="72458-301">Le fournisseur WSMan (WSMan :) fournit plusieurs paramètres de délai d’attente côté client et côté service, tels que le paramètre **MaxTimeoutms** dans le `WSMan:<ComputerName>` nœud et les paramètres **EnumerationTimeoutms** et **MaxPacketRetrievalTimeSeconds** dans le `WSMan:<ComputerName>\Service` nœud.</span><span class="sxs-lookup"><span data-stu-id="72458-301">The WSMan provider (WSMan:) provides several client-side and service-side timeout settings, such as the **MaxTimeoutms** setting in the `WSMan:<ComputerName>` node and the **EnumerationTimeoutms** and **MaxPacketRetrievalTimeSeconds** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="72458-302">Vous pouvez protéger l’ordinateur local à l’aide des paramètres **CancelTimeout** , **IdleTimeout** , **OpenTimeout** et **OperationTimeout** de l’applet de commande `New-PSSessionOption` et de la variable de `$PSSessionOption` préférence.</span><span class="sxs-lookup"><span data-stu-id="72458-302">You can protect the local computer by using the **CancelTimeout** , **IdleTimeout** , **OpenTimeout** , and **OperationTimeout** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="72458-303">Vous pouvez également protéger l’ordinateur distant en définissant les valeurs de délai d’attente par programmation dans la configuration de session de la session.</span><span class="sxs-lookup"><span data-stu-id="72458-303">You can also protect the remote computer by setting timeout values programmatically in the session configuration for the session.</span></span>

<span data-ttu-id="72458-304">Lorsqu’une valeur de délai d’attente n’autorise pas l’exécution d’une opération, PowerShell met fin à l’opération et génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="72458-304">When a timeout value does not permit a operation to complete, PowerShell terminates the operation and generates an error.</span></span>

<span data-ttu-id="72458-305">Pour résoudre l’erreur, modifiez la commande pour qu’elle se termine dans l’intervalle de délai d’attente ou déterminez la source de la limite du délai d’attente, puis augmentez l’intervalle de délai d’attente pour permettre l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="72458-305">To resolve the error, change the command to complete within the timeout interval or determine the source of the timeout limit and increase the timeout interval to allow the command to complete.</span></span>

<span data-ttu-id="72458-306">Par exemple, les commandes suivantes utilisent l' `New-PSSessionOption` applet de commande pour créer un objet d’option de session avec une valeur **OperationTimeout** de 4 minutes (en ms), puis utiliser l’objet d’option de session pour créer une session à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-306">For example, the following commands use the `New-PSSessionOption` cmdlet to create a session option object with an **OperationTimeout** value of 4 minutes (in MS) and then use the session option object to create a remote session.</span></span>

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

<span data-ttu-id="72458-307">Pour plus d’informations sur les délais d’expiration WS-Management, consultez la rubrique d’aide pour le fournisseur WSMan (type `Get-Help WSMan` ).</span><span class="sxs-lookup"><span data-stu-id="72458-307">For more information about the WS-Management timeouts, see the Help topic for the WSMan provider (type `Get-Help WSMan`).</span></span>

<span data-ttu-id="72458-308">Pour plus d’informations sur l’applet de commande `New-PSSessionOption` , consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="72458-308">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="troubleshooting-unresponsive-behavior"></a><span data-ttu-id="72458-309">Résolution des problèmes de comportement qui ne répond pas</span><span class="sxs-lookup"><span data-stu-id="72458-309">Troubleshooting unresponsive behavior</span></span>

<span data-ttu-id="72458-310">Cette section traite des problèmes de communication à distance qui empêchent une commande de se terminer et d’empêcher ou de retarder le retour de l’invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72458-310">This section discusses remoting problems that prevent a command from completing and prevent or delay the return of the PowerShell prompt.</span></span>

### <a name="how-to-interrupt-a-command"></a><span data-ttu-id="72458-311">Interruption d’une commande</span><span class="sxs-lookup"><span data-stu-id="72458-311">How to interrupt a command</span></span>

<span data-ttu-id="72458-312">Certains programmes Windows natifs, tels que les programmes avec une interface utilisateur, les applications console qui demandent une entrée et les applications console qui utilisent l’API de console Win32, ne fonctionnent pas correctement dans l’hôte distant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72458-312">Some native Windows programs, such as programs with a user interface, console applications that prompt for input, and console applications that use the Win32 console API, do not work correctly in the PowerShell remote host.</span></span>

<span data-ttu-id="72458-313">Lorsque vous utilisez ces programmes, vous pouvez constater un comportement inattendu, tel qu’aucune sortie, sortie partielle ou commande distante qui ne se termine pas.</span><span class="sxs-lookup"><span data-stu-id="72458-313">When you use these programs, you might see unexpected behavior, such as no output, partial output, or a remote command that does not complete.</span></span>

<span data-ttu-id="72458-314">Pour mettre fin à un programme qui ne répond pas, tapez <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="72458-314">To end an unresponsive program, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="72458-315">Pour afficher les erreurs qui ont pu être signalées, tapez `$error` dans l’hôte local et la session à distance.</span><span class="sxs-lookup"><span data-stu-id="72458-315">To view any errors that might have been reported, type `$error` in the local host and the remote session.</span></span>

## <a name="how-to-recover-from-an-operation-failure"></a><span data-ttu-id="72458-316">Récupération suite à un échec d’opération</span><span class="sxs-lookup"><span data-stu-id="72458-316">How to recover from an operation failure</span></span>

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

<span data-ttu-id="72458-317">Cette erreur est retournée lorsqu’une opération est terminée avant qu’elle ne se termine.</span><span class="sxs-lookup"><span data-stu-id="72458-317">This error is returned when an operation is terminated before it completes.</span></span>
<span data-ttu-id="72458-318">En général, il se produit lorsque le service WinRM s’arrête ou redémarre alors que d’autres opérations WinRM sont en cours.</span><span class="sxs-lookup"><span data-stu-id="72458-318">Typically, it occurs when the WinRM service stops or restarts while other WinRM operations are in progress.</span></span>

<span data-ttu-id="72458-319">Pour résoudre ce problème, vérifiez que le service WinRM est en cours d’exécution et réessayez d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="72458-319">To resolve this issue, verify that the WinRM service is running and try the command again.</span></span>

1. <span data-ttu-id="72458-320">Démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="72458-320">Start PowerShell with the **Run as administrator** option.</span></span>
1. <span data-ttu-id="72458-321">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="72458-321">Run the following command:</span></span>

   `Start-Service WinRM`

1. <span data-ttu-id="72458-322">Réexécutez la commande qui a généré l’erreur.</span><span class="sxs-lookup"><span data-stu-id="72458-322">Re-run the command that generated the error.</span></span>

## <a name="linux-and-macos-limitations"></a><span data-ttu-id="72458-323">Limitations de Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="72458-323">Linux and macOS limitations</span></span>

### <a name="authentication"></a><span data-ttu-id="72458-324">Authentification</span><span class="sxs-lookup"><span data-stu-id="72458-324">Authentication</span></span>

<span data-ttu-id="72458-325">Seule l’authentification de base fonctionne sur macOS et toute tentative d’utilisation d’autres schémas d’authentification peut entraîner un blocage du processus.</span><span class="sxs-lookup"><span data-stu-id="72458-325">Only basic authentication works on macOS and attempting to use other authentication schemes may result in the process crashing.</span></span>

<span data-ttu-id="72458-326">Veuillez consulter les instructions [d’authentification OMI](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) .</span><span class="sxs-lookup"><span data-stu-id="72458-326">Please see the [OMI authentication](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="72458-327">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="72458-327">SEE ALSO</span></span>

[<span data-ttu-id="72458-328">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="72458-328">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[<span data-ttu-id="72458-329">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="72458-329">Export-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[<span data-ttu-id="72458-330">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="72458-330">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="72458-331">about_Remote</span><span class="sxs-lookup"><span data-stu-id="72458-331">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="72458-332">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="72458-332">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="72458-333">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="72458-333">about_Remote_Variables</span></span>](about_Remote_Variables.md)
