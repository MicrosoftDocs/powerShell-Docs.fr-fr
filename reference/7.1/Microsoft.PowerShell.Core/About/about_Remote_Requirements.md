---
description: Décrit la configuration requise et la configuration requise pour l’exécution de commandes distantes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: bcaed40082c694aa7271177e6c8040a06d02772b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207725"
---
# <a name="about-remote-requirements"></a><span data-ttu-id="fdd4b-104">À propos des exigences à distance</span><span class="sxs-lookup"><span data-stu-id="fdd4b-104">About Remote Requirements</span></span>

## <a name="short-description"></a><span data-ttu-id="fdd4b-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="fdd4b-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="fdd4b-106">Décrit la configuration requise et la configuration requise pour l’exécution de commandes distantes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-106">Describes the system requirements and configuration requirements for running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="fdd4b-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="fdd4b-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="fdd4b-108">Cette rubrique décrit la configuration requise, les exigences des utilisateurs et les ressources requises pour établir des connexions à distance et exécuter des commandes distantes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-108">This topic describes the system requirements, user requirements, and resource requirements for establishing remote connections and running remote commands in PowerShell.</span></span> <span data-ttu-id="fdd4b-109">Il fournit également des instructions pour la configuration des opérations à distance.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-109">It also provides instructions for configuring remote operations.</span></span>

<span data-ttu-id="fdd4b-110">Remarque : de nombreuses cmdlets (y compris les applets de commande obtenir-service, obtenir-traiter, obtenir-WMIObject, obtenir-EventLog et Get-WinEvent) obtiennent des objets à partir d’ordinateurs distants à l’aide des méthodes de Microsoft .NET Framework pour récupérer les objets.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-110">Note: Many cmdlets (including the Get-Service, Get-Process, Get-WMIObject, Get-EventLog, and Get-WinEvent cmdlets) get objects from remote computers by using Microsoft .NET Framework methods to retrieve the objects.</span></span> <span data-ttu-id="fdd4b-111">Ils n’utilisent pas l’infrastructure de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-111">They do not use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="fdd4b-112">Les conditions requises dans ce document ne s’appliquent pas à ces applets de commande.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-112">The requirements in this document do not apply to these cmdlets.</span></span>

<span data-ttu-id="fdd4b-113">Pour rechercher les applets de commande qui ont un paramètre ComputerName, mais n’utilisez pas la communication à distance PowerShell, lisez la description du paramètre ComputerName des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-113">To find the cmdlets that have a ComputerName parameter but do not use PowerShell remoting, read the description of the ComputerName parameter of the cmdlets.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="fdd4b-114">CONFIGURATION SYSTÈME REQUISE</span><span class="sxs-lookup"><span data-stu-id="fdd4b-114">SYSTEM REQUIREMENTS</span></span>

<span data-ttu-id="fdd4b-115">Pour exécuter des sessions à distance sur Windows PowerShell 3,0, les ordinateurs locaux et distants doivent disposer des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-115">To run remote sessions on Windows PowerShell 3.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="fdd4b-116">Windows PowerShell 3,0 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="fdd4b-116">Windows PowerShell 3.0 or later</span></span>
- <span data-ttu-id="fdd4b-117">Le Microsoft .NET Framework 4 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="fdd4b-117">The Microsoft .NET Framework 4 or later</span></span>
- <span data-ttu-id="fdd4b-118">Windows Remote Management 3,0</span><span class="sxs-lookup"><span data-stu-id="fdd4b-118">Windows Remote Management 3.0</span></span>

<span data-ttu-id="fdd4b-119">Pour exécuter des sessions à distance sur Windows PowerShell 2,0, les ordinateurs locaux et distants doivent disposer des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-119">To run remote sessions on Windows PowerShell 2.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="fdd4b-120">Windows PowerShell 2,0 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="fdd4b-120">Windows PowerShell 2.0 or later</span></span>
- <span data-ttu-id="fdd4b-121">Le Microsoft .NET Framework 2,0 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="fdd4b-121">The Microsoft .NET Framework 2.0 or later</span></span>
- <span data-ttu-id="fdd4b-122">Windows Remote Management 2,0</span><span class="sxs-lookup"><span data-stu-id="fdd4b-122">Windows Remote Management 2.0</span></span>

<span data-ttu-id="fdd4b-123">Vous pouvez créer des sessions à distance entre des ordinateurs exécutant Windows PowerShell 2,0 et Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-123">You can create remote sessions between computers running Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span> <span data-ttu-id="fdd4b-124">Toutefois, les fonctionnalités qui s’exécutent uniquement sur Windows PowerShell 3,0, telles que la possibilité de se déconnecter et de se reconnecter aux sessions, sont disponibles uniquement lorsque les deux ordinateurs exécutent Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-124">However, features that run only on Windows PowerShell 3.0, such as the ability to disconnect and reconnect to sessions, are available only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="fdd4b-125">Pour rechercher le numéro de version d’une version installée de PowerShell, utilisez la variable automatique $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-125">To find the version number of an installed version of PowerShell, use the $PSVersionTable automatic variable.</span></span>

<span data-ttu-id="fdd4b-126">Windows Remote Management (WinRM) 3,0 et Microsoft .NET Framework 4 sont inclus dans Windows 8, Windows Server 2012 et les versions plus récentes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-126">Windows Remote Management (WinRM) 3.0 and Microsoft .NET Framework 4 are included in Windows 8, Windows Server 2012, and newer releases of the Windows operating system.</span></span> <span data-ttu-id="fdd4b-127">WinRM 3,0 est inclus dans Windows Management Framework 3,0 pour les systèmes d’exploitation plus anciens.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-127">WinRM 3.0 is included in Windows Management Framework 3.0 for older operating systems.</span></span> <span data-ttu-id="fdd4b-128">Si l’ordinateur ne dispose pas de la version requise de WinRM ou du Framework Microsoft .NET, l’installation échoue.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-128">If the computer does not have the required version of WinRM or the Microsoft .NET Framework, the installation fails.</span></span>

## <a name="user-permissions"></a><span data-ttu-id="fdd4b-129">AUTORISATIONS DE L’UTILISATEUR</span><span class="sxs-lookup"><span data-stu-id="fdd4b-129">USER PERMISSIONS</span></span>

<span data-ttu-id="fdd4b-130">Pour créer des sessions à distance et exécuter des commandes à distance, par défaut, l’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur distant ou fournir les informations d’identification d’un administrateur.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-130">To create remote sessions and run remote commands, by default, the current user must be a member of the Administrators group on the remote computer or provide the credentials of an administrator.</span></span> <span data-ttu-id="fdd4b-131">Sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-131">Otherwise, the command fails.</span></span>

<span data-ttu-id="fdd4b-132">Les autorisations requises pour créer des sessions et exécuter des commandes sur un ordinateur distant (ou dans une session à distance sur l’ordinateur local) sont établies par la configuration de session (également appelée « point de terminaison ») sur l’ordinateur distant auquel la session se connecte.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-132">The permissions required to create sessions and run commands on a remote computer (or in a remote session on the local computer) are established by the session configuration (also known as an "endpoint") on the remote computer to which the session connects.</span></span> <span data-ttu-id="fdd4b-133">Plus précisément, le descripteur de sécurité de la configuration de session détermine qui a accès à la configuration de session et qui peut l’utiliser pour se connecter.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-133">Specifically, the security descriptor on the session configuration determines who has access to the session configuration and who can use it to connect.</span></span>

<span data-ttu-id="fdd4b-134">Les descripteurs de sécurité sur les configurations de session par défaut, Microsoft. PowerShell, Microsoft. PowerShell32 et Microsoft. PowerShell. Workflow, autorisent l’accès uniquement aux membres du groupe administrateurs.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-134">The security descriptors on the default session configurations, Microsoft.PowerShell, Microsoft.PowerShell32, and Microsoft.PowerShell.Workflow, allow access only to members of the Administrators group.</span></span>

<span data-ttu-id="fdd4b-135">Si l’utilisateur actuel n’est pas autorisé à utiliser la configuration de session, la commande permettant d’exécuter une commande (qui utilise une session temporaire) ou de créer une session persistante sur l’ordinateur distant échoue.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-135">If the current user doesn't have permission to use the session configuration, the command to run a command (which uses a temporary session) or create a persistent session on the remote computer fails.</span></span> <span data-ttu-id="fdd4b-136">L’utilisateur peut utiliser le paramètre ConfigurationName des applets de commande qui créent des sessions pour sélectionner une autre configuration de session, si celle-ci est disponible.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-136">The user can use the ConfigurationName parameter of cmdlets that create sessions to select a different session configuration, if one is available.</span></span>

<span data-ttu-id="fdd4b-137">Les membres du groupe Administrateurs sur un ordinateur peuvent déterminer qui est autorisé à se connecter à distance à l’ordinateur en modifiant les descripteurs de sécurité sur les configurations de session par défaut et en créant de nouvelles configurations de session avec des descripteurs de sécurité différents.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-137">Members of the Administrators group on a computer can determine who has permission to connect to the computer remotely by changing the security descriptors on the default session configurations and by creating new session configurations with different security descriptors.</span></span>

<span data-ttu-id="fdd4b-138">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="fdd4b-138">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="windows-network-locations"></a><span data-ttu-id="fdd4b-139">EMPLACEMENTS RÉSEAU WINDOWS</span><span class="sxs-lookup"><span data-stu-id="fdd4b-139">WINDOWS NETWORK LOCATIONS</span></span>

<span data-ttu-id="fdd4b-140">À compter de Windows PowerShell 3,0, l’applet de commande Enable-PSRemoting peut activer la communication à distance sur les versions client et serveur de Windows sur des réseaux privés, de domaine et publics.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-140">Beginning in Windows PowerShell 3.0, the Enable-PSRemoting cmdlet can enable remoting on client and server versions of Windows on private, domain, and public networks.</span></span>

<span data-ttu-id="fdd4b-141">Sur les versions serveur de Windows avec des réseaux privés et de domaine, l’applet de commande Enable-PSRemoting crée des règles de pare-feu qui autorisent l’accès à distance illimité.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-141">On server versions of Windows with private and domain networks, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span> <span data-ttu-id="fdd4b-142">Il crée également une règle de pare-feu pour les réseaux publics qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-142">It also creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="fdd4b-143">Cette règle de pare-feu de sous-réseau local est activée par défaut sur les versions serveur de Windows sur les réseaux publics, mais Enable-PSRemoting réapplique la règle en cas de modification ou de suppression.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-143">This local subnet firewall rule is enabled by default on server versions of Windows on public networks, but Enable-PSRemoting reapplies the rule in case it was changed or deleted.</span></span>

<span data-ttu-id="fdd4b-144">Sur les versions client de Windows avec des réseaux privés et de domaine, par défaut, l’applet de commande Enable-PSRemoting crée des règles de pare-feu qui autorisent l’accès à distance illimité.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-144">On client versions of Windows with private and domain networks, by default, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span>

<span data-ttu-id="fdd4b-145">Pour activer la communication à distance sur les versions client de Windows avec des réseaux publics, utilisez le paramètre SkipNetworkProfileCheck de l’applet de commande Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-145">To enable remoting on client versions of Windows with public networks, use the SkipNetworkProfileCheck parameter of the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="fdd4b-146">Il crée une règle de pare-feu qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-146">It creates a firewall rule that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="fdd4b-147">Pour supprimer la restriction de sous-réseau local sur les réseaux publics et autoriser l’accès à distance à partir de tous les emplacements sur les versions client et serveur de Windows, utilisez l’applet de commande Set-NetFirewallRule dans le module netsecurity.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-147">To remove the local subnet restriction on public networks and allow remote access from all locations on client and server versions of Windows, use the Set-NetFirewallRule cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="fdd4b-148">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-148">Run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="fdd4b-149">Dans Windows PowerShell 2,0, sur les versions serveur de Windows, Enable-PSRemoting crée des règles de pare-feu qui autorisent l’accès à distance sur tous les réseaux.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-149">In Windows PowerShell 2.0, on server versions of Windows, Enable-PSRemoting creates firewall rules that permit remote access on all networks.</span></span>

<span data-ttu-id="fdd4b-150">Dans Windows PowerShell 2,0, sur les versions client de Windows, Enable-PSRemoting ne crée des règles de pare-feu que sur les réseaux privés et de domaine.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-150">In Windows PowerShell 2.0, on client versions of Windows, Enable-PSRemoting creates firewall rules only on private and domain networks.</span></span> <span data-ttu-id="fdd4b-151">Si l’emplacement réseau est public, Enable-PSRemoting échoue.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-151">If the network location is public, Enable-PSRemoting fails.</span></span>

## <a name="run-as-administrator"></a><span data-ttu-id="fdd4b-152">EXÉCUTER EN TANT QU’ADMINISTRATEUR</span><span class="sxs-lookup"><span data-stu-id="fdd4b-152">RUN AS ADMINISTRATOR</span></span>

<span data-ttu-id="fdd4b-153">Des privilèges d’administrateur sont requis pour les opérations de communication à distance suivantes :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-153">Administrator privileges are required for the following remoting operations:</span></span>

- <span data-ttu-id="fdd4b-154">Établissement d’une connexion à distance à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-154">Establishing a remote connection to the local computer.</span></span> <span data-ttu-id="fdd4b-155">Ce scénario est communément appelé « bouclage ».</span><span class="sxs-lookup"><span data-stu-id="fdd4b-155">This is commonly known as a "loopback" scenario.</span></span>

- <span data-ttu-id="fdd4b-156">Gestion des configurations de session sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-156">Managing session configurations on the local computer.</span></span>

- <span data-ttu-id="fdd4b-157">Affichage et modification des paramètres de WS-Management sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-157">Viewing and changing WS-Management settings on the local computer.</span></span> <span data-ttu-id="fdd4b-158">Il s’agit des paramètres du nœud LocalHost du lecteur WSMAN :.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-158">These are the settings in the LocalHost node of the WSMAN: drive.</span></span>

<span data-ttu-id="fdd4b-159">Pour effectuer ces tâches, vous devez démarrer PowerShell avec l’option « Exécuter en tant qu’administrateur », même si vous êtes membre du groupe Administrateurs sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-159">To perform these tasks, you must start PowerShell with the "Run as administrator" option even if you are a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="fdd4b-160">Dans Windows 7 et Windows Server 2008 R2, pour démarrer Windows PowerShell avec l’option « Exécuter en tant qu’administrateur » :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-160">In Windows 7 and in Windows Server 2008 R2, to start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="fdd4b-161">Cliquez sur Démarrer, sur tous les programmes, sur accessoires, puis sur le dossier Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-161">Click Start, click All Programs, click Accessories, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="fdd4b-162">Cliquez avec le bouton droit sur Windows PowerShell, puis cliquez sur Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-162">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="fdd4b-163">Pour démarrer Windows PowerShell avec l’option « Exécuter en tant qu’administrateur » :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-163">To start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="fdd4b-164">Cliquez sur Démarrer, sur tous les programmes, puis sur le dossier Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-164">Click Start, click All Programs, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="fdd4b-165">Cliquez avec le bouton droit sur Windows PowerShell, puis cliquez sur Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-165">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="fdd4b-166">L’option « Exécuter en tant qu’administrateur » est également disponible dans d’autres entrées de l’Explorateur Windows pour Windows PowerShell, y compris les raccourcis.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-166">The "Run as administrator" option is also available in other Windows Explorer entries for Windows PowerShell, including shortcuts.</span></span> <span data-ttu-id="fdd4b-167">Il vous suffit de cliquer avec le bouton droit sur l’élément, puis de cliquer sur « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="fdd4b-167">Just right-click the item, and then click "Run as administrator".</span></span>

<span data-ttu-id="fdd4b-168">Quand vous démarrez Windows PowerShell à partir d’un autre programme, tel que Cmd.exe, utilisez l’option « Exécuter en tant qu’administrateur » pour démarrer le programme.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-168">When you start Windows PowerShell from another program such as Cmd.exe, use the "Run as administrator" option to start the program.</span></span>

## <a name="how-to-configure-your-computer-for-remoting"></a><span data-ttu-id="fdd4b-169">COMMENT CONFIGURER VOTRE ORDINATEUR POUR LA COMMUNICATION À DISTANCE</span><span class="sxs-lookup"><span data-stu-id="fdd4b-169">HOW TO CONFIGURE YOUR COMPUTER FOR REMOTING</span></span>

<span data-ttu-id="fdd4b-170">Les ordinateurs exécutant toutes les versions de Windows prises en charge peuvent établir des connexions à distance à et exécuter des commandes distantes dans PowerShell sans aucune configuration.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-170">Computers running all supported versions of Windows can establish remote connections to and run remote commands in PowerShell without any configuration.</span></span> <span data-ttu-id="fdd4b-171">Toutefois, pour recevoir des connexions et autoriser les utilisateurs à créer des sessions PowerShell locales et distantes gérées par l’utilisateur (« sessions PSSession ») et à exécuter des commandes sur l’ordinateur local, vous devez activer la communication à distance PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-171">However, to receive connections, and allow users to create local and remote user-managed PowerShell sessions ("PSSessions") and run commands on the local computer, you must enable PowerShell remoting on the computer.</span></span>

<span data-ttu-id="fdd4b-172">Windows Server 2012 et les versions plus récentes de Windows Server sont activés par défaut pour la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-172">Windows Server 2012 and newer releases of Windows Server are enabled for PowerShell remoting by default.</span></span> <span data-ttu-id="fdd4b-173">Si les paramètres sont modifiés, vous pouvez restaurer les paramètres par défaut en exécutant l’applet de commande Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-173">If the settings are changed, you can restore the default settings by running the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="fdd4b-174">Sur toutes les autres versions prises en charge de Windows, vous devez exécuter l’applet de commande Enable-PSRemoting pour activer la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-174">On all other supported versions of Windows, you need to run the Enable-PSRemoting cmdlet to enable PowerShell remoting.</span></span>

<span data-ttu-id="fdd4b-175">Les fonctionnalités de communication à distance de PowerShell sont prises en charge par le service WinRM, qui est l’implémentation Microsoft du protocole WS-Management (Web Services for Management).</span><span class="sxs-lookup"><span data-stu-id="fdd4b-175">The remoting features of PowerShell are supported by the WinRM service, which is the Microsoft implementation of the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="fdd4b-176">Lorsque vous activez la communication à distance PowerShell, vous modifiez la configuration par défaut de WS-Management et ajoutez la configuration du système qui permet aux utilisateurs de se connecter à WS-Management.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-176">When you enable PowerShell remoting, you change the default configuration of WS-Management and add system configuration that allow users to connect to WS-Management.</span></span>

<span data-ttu-id="fdd4b-177">Pour configurer PowerShell pour recevoir des commandes à distance :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-177">To configure PowerShell to receive remote commands:</span></span>

1. <span data-ttu-id="fdd4b-178">Démarrez PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="fdd4b-178">Start PowerShell with the "Run as administrator" option.</span></span>
2. <span data-ttu-id="fdd4b-179">À l’invite de commandes, tapez : `Enable-PSRemoting`</span><span class="sxs-lookup"><span data-stu-id="fdd4b-179">At the command prompt, type: `Enable-PSRemoting`</span></span>

<span data-ttu-id="fdd4b-180">Pour vérifier que la communication à distance est correctement configurée, exécutez une commande de test telle que la commande suivante, qui crée une session à distance sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-180">To verify that remoting is configured correctly, run a test command such as the following command, which creates a remote session on the local computer.</span></span>

```powershell
New-PSSession
```

<span data-ttu-id="fdd4b-181">Si la communication à distance est correctement configurée, la commande crée une session sur l’ordinateur local et retourne un objet qui représente la session.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-181">If remoting is configured correctly, the command will create a session on the local computer and return an object that represents the session.</span></span> <span data-ttu-id="fdd4b-182">La sortie doit ressembler à l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-182">The output should resemble the following sample output:</span></span>

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

<span data-ttu-id="fdd4b-183">Si la commande échoue, pour obtenir de l’aide, consultez [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="fdd4b-183">If the command fails, for assistance, see [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).</span></span>

## <a name="understand-policies"></a><span data-ttu-id="fdd4b-184">COMPRENDRE LES STRATÉGIES</span><span class="sxs-lookup"><span data-stu-id="fdd4b-184">UNDERSTAND POLICIES</span></span>

<span data-ttu-id="fdd4b-185">Lorsque vous travaillez à distance, vous utilisez deux instances de PowerShell, l’une sur l’ordinateur local et l’autre sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-185">When you work remotely, you use two instances of PowerShell, one on the local computer and one on the remote computer.</span></span> <span data-ttu-id="fdd4b-186">Par conséquent, votre travail est affecté par les stratégies Windows et les stratégies PowerShell sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-186">As a result, your work is affected by the Windows policies and the PowerShell policies on the local and remote computers.</span></span>

<span data-ttu-id="fdd4b-187">En général, avant de vous connecter et lorsque vous établissez la connexion, les stratégies sur l’ordinateur local sont activées.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-187">In general, before you connect and as you are establishing the connection, the policies on the local computer are in effect.</span></span> <span data-ttu-id="fdd4b-188">Lorsque vous utilisez la connexion, les stratégies sur l’ordinateur distant sont en vigueur.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-188">When you are using the connection, the policies on the remote computer are in effect.</span></span>

## <a name="basic-authentication-limitations-on-linux-and-macos"></a><span data-ttu-id="fdd4b-189">Limitations de l’authentification de base sur Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="fdd4b-189">Basic Authentication Limitations on Linux and macOS</span></span>

<span data-ttu-id="fdd4b-190">Lors de la connexion d’un système Linux ou macOS à Windows, l’authentification de base sur HTTP n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-190">When connecting from a Linux or macOS system to Windows, Basic Authentication over HTTP is not supported.</span></span> <span data-ttu-id="fdd4b-191">L’authentification de base peut être utilisée sur HTTPs en installant un certificat sur le serveur cible.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-191">Basic Authentication can be used over HTTPS by installing a certificate on the target server.</span></span> <span data-ttu-id="fdd4b-192">Le certificat doit avoir un nom CN qui correspond au nom d’hôte, n’a pas expiré ou n’a pas été révoqué.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-192">The certificate must have a CN name that matches the hostname, is not expired or revoked.</span></span> <span data-ttu-id="fdd4b-193">Un certificat auto-signé peut être utilisé à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-193">A self-signed certificate may be used for testing purposes.</span></span>

<span data-ttu-id="fdd4b-194">Pour plus d’informations, consultez [procédure : configurer WINRM pour HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) .</span><span class="sxs-lookup"><span data-stu-id="fdd4b-194">See [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) for additional details.</span></span>

<span data-ttu-id="fdd4b-195">La commande suivante, exécutée à partir d’une invite de commandes avec élévation de privilèges, configure l’écouteur HTTPs sur Windows avec le certificat installé.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-195">The following command, run from an elevated command prompt, will configure the HTTPS listener on Windows with the installed certificate.</span></span>

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

<span data-ttu-id="fdd4b-196">Sur le côté Linux ou macOS, sélectionnez de base pour authentification et-UseSSl.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-196">On the Linux or macOS side, select Basic for authentication and -UseSSl.</span></span>

> <span data-ttu-id="fdd4b-197">Remarque : l’authentification de base ne peut pas être utilisée avec les comptes de domaine ; un compte local est requis et le compte doit se trouver dans le groupe administrateurs.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-197">NOTE: Basic authentication cannot be used with domain accounts; a local account is required and the account must be in the Administrators group.</span></span>

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

<span data-ttu-id="fdd4b-198">Une alternative à l’authentification de base sur HTTPs est Negotiate.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-198">An alternative to Basic Authentication over HTTPS is Negotiate.</span></span> <span data-ttu-id="fdd4b-199">Cela entraîne l’authentification NTLM entre le client et le serveur, et la charge utile est chiffrée via HTTP.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-199">This results in NTLM authentication between the client and server and payload is encrypted over HTTP.</span></span>

<span data-ttu-id="fdd4b-200">L’exemple suivant illustre l’utilisation de Negotiate avec New-PSSession :</span><span class="sxs-lookup"><span data-stu-id="fdd4b-200">The following illustrates using Negotiate with New-PSSession:</span></span>

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> <span data-ttu-id="fdd4b-201">Windows Server nécessite un paramètre de Registre supplémentaire pour permettre aux administrateurs, autres que l’administrateur intégré, de se connecter à l’aide de NTLM.</span><span class="sxs-lookup"><span data-stu-id="fdd4b-201">Windows Server requires an additional registry setting to enable administrators, other than the built in administrator, to connect using NTLM.</span></span>
> <span data-ttu-id="fdd4b-202">Reportez-vous au paramètre de Registre LocalAccountTokenFilterPolicy sous négocier l’authentification dans [l’authentification pour les connexions à distance](/windows/win32/winrm/authentication-for-remote-connections)</span><span class="sxs-lookup"><span data-stu-id="fdd4b-202">Refer to the LocalAccountTokenFilterPolicy registry setting under Negotiate Authentication in [Authentication for Remote Connections](/windows/win32/winrm/authentication-for-remote-connections)</span></span>

## <a name="see-also"></a><span data-ttu-id="fdd4b-203">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="fdd4b-203">SEE ALSO</span></span>

[<span data-ttu-id="fdd4b-204">about_Remote</span><span class="sxs-lookup"><span data-stu-id="fdd4b-204">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="fdd4b-205">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="fdd4b-205">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="fdd4b-206">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="fdd4b-206">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="fdd4b-207">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="fdd4b-207">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="fdd4b-208">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="fdd4b-208">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="fdd4b-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="fdd4b-209">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

