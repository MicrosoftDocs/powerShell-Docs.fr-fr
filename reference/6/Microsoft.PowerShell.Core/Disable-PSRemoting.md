---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3057f56ebb2a1d5a1c36d75cc4cb67c1e2375a1a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203818"
---
# <span data-ttu-id="56735-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="56735-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="56735-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="56735-104">SYNOPSIS</span></span>
<span data-ttu-id="56735-105">Empêche les points de terminaison PowerShell de recevoir des connexions à distance.</span><span class="sxs-lookup"><span data-stu-id="56735-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="56735-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56735-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="56735-107">Description</span><span class="sxs-lookup"><span data-stu-id="56735-107">DESCRIPTION</span></span>

<span data-ttu-id="56735-108">L' `Disable-PSRemoting` applet de commande bloque l’accès à distance à toutes les configurations de point de terminaison de session PowerShell version 6 et ultérieures sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56735-108">The `Disable-PSRemoting` cmdlet blocks remote access to all PowerShell version 6 and greater session endpoint configurations on the local computer.</span></span> <span data-ttu-id="56735-109">Elle n’affecte pas les configurations de point de terminaison Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-109">It does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="56735-110">Pour désactiver les configurations de point de terminaison de session Windows PowerShell, exécutez `Disable-PSRemoting` la commande à partir d’une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-110">To disable Windows PowerShell session endpoint configurations, run `Disable-PSRemoting` command from within a Windows PowerShell session.</span></span>

<span data-ttu-id="56735-111">Pour réactiver l’accès à distance à toutes les configurations de point de terminaison de session PowerShell version 6 et ultérieures, utilisez l’applet de commande `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="56735-111">To re-enable remote access to all PowerShell version 6 and greater session endpoint configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="56735-112">Pour réactiver l’accès à distance à toutes les configurations de point de terminaison de session Windows PowerShell, exécutez `Enable-PSRemoting` à partir d’une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-112">To re-enable remote access to all Windows PowerShell session endpoint configurations, run `Enable-PSRemoting` from within a Windows PowerShell session.</span></span>

> [!NOTE]
> <span data-ttu-id="56735-113">Si vous souhaitez désactiver tous les accès à distance PowerShell à un ordinateur Windows local, vous devez exécuter cette commande à partir d’un dans une session PowerShell version 6 ou ultérieure et à partir d’une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-113">If you want to disable all PowerShell remote access to a local Windows machine, you must run this command both from a within PowerShell version 6 or greater session and from within a Windows PowerShell session.</span></span> <span data-ttu-id="56735-114">Windows PowerShell est installé sur tous les ordinateurs Windows par défaut.</span><span class="sxs-lookup"><span data-stu-id="56735-114">Windows PowerShell is installed on all Windows machines by default.</span></span>

<span data-ttu-id="56735-115">Pour désactiver et réactiver l’accès à distance aux configurations de point de terminaison de session spécifiques, utilisez les `Enable-PSSessionConfiguration` applets de commande et `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="56735-115">To disable and re-enable remote access to specific session endpoint configurations, use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="56735-116">Pour définir des configurations d’accès spécifiques à des points de terminaison individuels, utilisez l’applet de commande `Set-PSSessionConfiguration` avec le paramètre **AccessMode** .</span><span class="sxs-lookup"><span data-stu-id="56735-116">To set specific access configurations of individual endpoints, use the `Set-PSSessionConfiguration` cmdlet along with the **AccessMode** parameter.</span></span> <span data-ttu-id="56735-117">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="56735-117">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="56735-118">Même après `Disable-PSRemoting` l’exécution, vous pouvez toujours établir des connexions de bouclage sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56735-118">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="56735-119">Une connexion de bouclage est une session PowerShell à distance qui provient de et se connecte à la même machine locale.</span><span class="sxs-lookup"><span data-stu-id="56735-119">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="56735-120">Les sessions à distance provenant de sources externes restent bloquées.</span><span class="sxs-lookup"><span data-stu-id="56735-120">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="56735-121">Pour les connexions de bouclage, vous devez utiliser des informations d’identification implicites avec le paramètre **EnableNetworkAccess** .</span><span class="sxs-lookup"><span data-stu-id="56735-121">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="56735-122">Pour plus d’informations sur les connexions de bouclage, consultez [New-PSSession](New-PSSession.md).</span><span class="sxs-lookup"><span data-stu-id="56735-122">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="56735-123">Cette applet de commande est disponible uniquement sur la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="56735-123">This cmdlet is only available on the Windows platform.</span></span> <span data-ttu-id="56735-124">Elle n’est pas disponible dans les versions Linux ou macOS de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-124">It is not available on Linux or macOS versions of PowerShell.</span></span> <span data-ttu-id="56735-125">Pour exécuter cette applet de commande, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="56735-125">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="56735-126">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="56735-126">EXAMPLES</span></span>

### <span data-ttu-id="56735-127">Exemple 1 : empêcher l’accès à distance à toutes les configurations de session PowerShell</span><span class="sxs-lookup"><span data-stu-id="56735-127">Example 1: Prevent remote access to all PowerShell session configurations</span></span>

<span data-ttu-id="56735-128">Cet exemple empêche l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56735-128">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="56735-129">Exemple 2 : empêcher l’accès à distance à toutes les configurations de session PowerShell sans invite de confirmation</span><span class="sxs-lookup"><span data-stu-id="56735-129">Example 2: Prevent remote access to all PowerShell session configurations without confirmation prompt</span></span>

<span data-ttu-id="56735-130">Cet exemple empêche l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="56735-130">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="56735-131">Exemple 3 : effets de l’exécution de cette applet de commande</span><span class="sxs-lookup"><span data-stu-id="56735-131">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="56735-132">Cet exemple montre l’effet de l’utilisation de l’applet de commande `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="56735-132">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="56735-133">Pour exécuter cette séquence de commandes, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="56735-133">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="56735-134">Après la désactivation des configurations de sessions, l' `New-PSSession` applet de commande tente de créer une session à distance sur l’ordinateur local (également appelé « bouclage »).</span><span class="sxs-lookup"><span data-stu-id="56735-134">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="56735-135">Étant donné que l’accès à distance est désactivé sur l’ordinateur local, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="56735-135">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### <span data-ttu-id="56735-136">Exemple 4 : effets de l’exécution de cette applet de commande et Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="56735-136">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="56735-137">Cet exemple montre l’effet sur les configurations de session de à l’aide des `Disable-PSRemoting` applets de commande et `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="56735-137">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="56735-138">`Disable-PSRemoting` est utilisé pour désactiver l’accès à distance à toutes les configurations de point de terminaison de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-138">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="56735-139">Le paramètre **Force** supprime toutes les invites utilisateur.</span><span class="sxs-lookup"><span data-stu-id="56735-139">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="56735-140">Les `Get-PSSessionConfiguration` applets de commande et `Format-Table` affichent les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56735-140">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="56735-141">La sortie indique que l’accès aux configurations de point de terminaison est refusé à tous les utilisateurs distants distants disposant d’un jeton réseau.</span><span class="sxs-lookup"><span data-stu-id="56735-141">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="56735-142">Le groupe Administrateurs sur l’ordinateur local est autorisé à accéder aux configurations de point de terminaison, à condition qu’elles se connectent localement (également appelées « bouclage ») et qu’elles utilisent des informations d’identification implicites.</span><span class="sxs-lookup"><span data-stu-id="56735-142">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

<span data-ttu-id="56735-143">L' `Enable-PSRemoting` applet de commande réactive l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56735-143">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="56735-144">Le paramètre **force** supprime toutes les invites utilisateur et redémarre le service WinRM sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="56735-144">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="56735-145">La nouvelle sortie indique que les descripteurs de sécurité **AccessDenied** ont été supprimés de toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="56735-145">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="56735-146">Exemple 5 : connexions de bouclage avec des configurations de point de terminaison de session désactivées</span><span class="sxs-lookup"><span data-stu-id="56735-146">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="56735-147">Cet exemple montre comment les configurations de point de terminaison sont désactivées et montre comment établir une connexion de bouclage à un point de terminaison désactivé.</span><span class="sxs-lookup"><span data-stu-id="56735-147">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="56735-148">`Disable-PSRemoting` désactive toutes les configurations de point de terminaison de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-148">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="56735-149">La première utilisation des `New-PSSession` tentatives de création d’une session à distance sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56735-149">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="56735-150">Le paramètre **ConfigurationName** est utilisé pour spécifier un point de terminaison PowerShell désactivé.</span><span class="sxs-lookup"><span data-stu-id="56735-150">The **ConfigurationName** parameter is used to specify a disabled PowerShell endpoint.</span></span> <span data-ttu-id="56735-151">Les informations d’identification sont passées explicitement à la commande via le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="56735-151">Credentials are explicitly passed to the command through the **Credential** parameter.</span></span> <span data-ttu-id="56735-152">Ce type de connexion traverse la pile réseau et n’est pas un bouclage.</span><span class="sxs-lookup"><span data-stu-id="56735-152">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="56735-153">Par conséquent, la tentative de connexion au point de terminaison désactivé échoue avec une erreur **accès refusé** .</span><span class="sxs-lookup"><span data-stu-id="56735-153">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="56735-154">La deuxième utilisation de `New-PSSession` tente également de créer une session à distance sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56735-154">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="56735-155">Dans ce cas, elle est réussie, car il s’agit d’une connexion de bouclage qui contourne la pile réseau.</span><span class="sxs-lookup"><span data-stu-id="56735-155">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="56735-156">Une connexion de bouclage est créée lorsque les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="56735-156">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="56735-157">Le nom de l’ordinateur auquel se connecter est « localhost ».</span><span class="sxs-lookup"><span data-stu-id="56735-157">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="56735-158">Aucune information d’identification n’est transmise.</span><span class="sxs-lookup"><span data-stu-id="56735-158">No credentials are passed in.</span></span> <span data-ttu-id="56735-159">L’utilisateur actuellement connecté (informations d’identification implicites) est utilisé pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="56735-159">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="56735-160">Le paramètre de commutateur **EnableNetworkAccess** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="56735-160">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="56735-161">Pour plus d’informations sur les connexions de bouclage, consultez le document [New-PSSession](New-PSSession.md) .</span><span class="sxs-lookup"><span data-stu-id="56735-161">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="56735-162">Exemple 6 : désactivation de toutes les configurations de point de terminaison de communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="56735-162">Example 6: Disabling all PowerShell remoting endpoint configurations</span></span>

<span data-ttu-id="56735-163">Cet exemple montre comment l’exécution de la `Disable-PSRemoting` commande n’affecte pas les configurations de point de terminaison Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-163">This example demonstrates how running the `Disable-PSRemoting` command does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="56735-164">`Get-PSSessionConfiguration` exécuter dans Windows PowerShell affiche toutes les configurations de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56735-164">`Get-PSSessionConfiguration` run within Windows PowerShell shows all endpoint configurations.</span></span> <span data-ttu-id="56735-165">Nous voyons que les configurations de point de terminaison Windows PowerShell ne sont pas désactivées.</span><span class="sxs-lookup"><span data-stu-id="56735-165">We see that the Windows PowerShell endpoint configurations are not disabled.</span></span>

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

<span data-ttu-id="56735-166">Pour désactiver ces configurations de point de terminaison, la `Disable-PSRemoting` commande doit être exécutée à partir d’une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56735-166">To disable these endpoint configurations, the `Disable-PSRemoting` command must be run from within a Windows PowerShell session.</span></span> <span data-ttu-id="56735-167">À présent, `Get-PSSessionConfiguration` exécuter à partir de Windows PowerShell montre que toutes les configurations de point de terminaison sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="56735-167">Now, `Get-PSSessionConfiguration` run from within Windows PowerShell shows that all endpoint configurations are disabled.</span></span>

### <span data-ttu-id="56735-168">Exemple 7 : empêcher l’accès à distance aux configurations de session qui ont des descripteurs de sécurité personnalisés</span><span class="sxs-lookup"><span data-stu-id="56735-168">Example 7: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="56735-169">Cet exemple montre que l' `Disable-PSRemoting` applet de commande désactive l’accès à distance à toutes les configurations de session qui incluent des configurations de session avec des descripteurs de sécurité personnalisés.</span><span class="sxs-lookup"><span data-stu-id="56735-169">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="56735-170">`Register-PSSessionConfiguration` crée la configuration de la session de **test** .</span><span class="sxs-lookup"><span data-stu-id="56735-170">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="56735-171">Le paramètre **filePath** spécifie un fichier de configuration de session qui personnalise la session.</span><span class="sxs-lookup"><span data-stu-id="56735-171">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="56735-172">Le paramètre **ShowSecurityDescriptorUI** affiche une boîte de dialogue qui définit les autorisations de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="56735-172">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="56735-173">Dans la boîte de dialogue autorisations, nous créons des autorisations d’accès complet personnalisées pour l’utilisateur indiqué.</span><span class="sxs-lookup"><span data-stu-id="56735-173">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="56735-174">Les `Get-PSSessionConfiguration` applets de commande et `Format-Table` affichent les configurations de session et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="56735-174">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="56735-175">La sortie indique que la configuration de la session de **test** autorise un accès interactif et des autorisations spéciales pour l’utilisateur indiqué.</span><span class="sxs-lookup"><span data-stu-id="56735-175">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="56735-176">`Disable-PSRemoting` désactive l’accès à distance à toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="56735-176">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

<span data-ttu-id="56735-177">Désormais `Get-PSSessionConfiguration` , les `Format-Table` applets de commande et indiquent qu’un descripteur de sécurité **AccessDenied** pour tous les utilisateurs du réseau est ajouté à toutes les configurations de session, y compris la configuration de la session de **test** .</span><span class="sxs-lookup"><span data-stu-id="56735-177">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="56735-178">Bien que les autres descripteurs de sécurité ne soient pas modifiés, le descripteur de sécurité « network_deny_all » est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="56735-178">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="56735-179">Cela est illustré par la tentative d’utilisation `New-PSSession` de pour se connecter à la configuration de la session de **test** .</span><span class="sxs-lookup"><span data-stu-id="56735-179">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="56735-180">Exemple 8 : réactiver l’accès à distance aux configurations de session sélectionnées</span><span class="sxs-lookup"><span data-stu-id="56735-180">Example 8: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="56735-181">Cet exemple illustre comment réactiver l'accès à distance uniquement pour les configurations de session sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="56735-181">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="56735-182">Après la désactivation de toutes les configurations de session, nous réactivons une session spécifique.</span><span class="sxs-lookup"><span data-stu-id="56735-182">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="56735-183">L' `Set-PSSessionConfiguration` applet de commande est utilisée pour modifier la configuration de session **PowerShell. 6** .</span><span class="sxs-lookup"><span data-stu-id="56735-183">The `Set-PSSessionConfiguration` cmdlet is used to change the **PowerShell.6** session configuration.</span></span> <span data-ttu-id="56735-184">Le paramètre **AccessMode** avec la valeur **Remote** Reactive l’accès à distance à la configuration.</span><span class="sxs-lookup"><span data-stu-id="56735-184">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

## <span data-ttu-id="56735-185">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56735-185">PARAMETERS</span></span>

### <span data-ttu-id="56735-186">-Confirm</span><span class="sxs-lookup"><span data-stu-id="56735-186">-Confirm</span></span>

<span data-ttu-id="56735-187">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="56735-187">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56735-188">-Force</span><span class="sxs-lookup"><span data-stu-id="56735-188">-Force</span></span>

<span data-ttu-id="56735-189">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="56735-189">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56735-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="56735-190">-WhatIf</span></span>

<span data-ttu-id="56735-191">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="56735-191">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="56735-192">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="56735-192">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56735-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56735-193">CommonParameters</span></span>

<span data-ttu-id="56735-194">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="56735-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56735-195">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="56735-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56735-196">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="56735-196">INPUTS</span></span>

### <span data-ttu-id="56735-197">Aucun</span><span class="sxs-lookup"><span data-stu-id="56735-197">None</span></span>

<span data-ttu-id="56735-198">Vous ne pouvez pas diriger d’objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="56735-198">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="56735-199">SORTIES</span><span class="sxs-lookup"><span data-stu-id="56735-199">OUTPUTS</span></span>

### <span data-ttu-id="56735-200">Aucun</span><span class="sxs-lookup"><span data-stu-id="56735-200">None</span></span>

<span data-ttu-id="56735-201">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="56735-201">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="56735-202">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="56735-202">NOTES</span></span>

- <span data-ttu-id="56735-203">La désactivation des configurations de session n’annule pas toutes les modifications apportées par les `Enable-PSRemoting` applets de commande ou `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="56735-203">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="56735-204">Vous devrez peut-être annuler manuellement les modifications suivantes.</span><span class="sxs-lookup"><span data-stu-id="56735-204">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="56735-205">Arrêter et désactiver le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="56735-205">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="56735-206">Supprimer l'écouteur qui accepte les demandes sur toutes les adresses IP.</span><span class="sxs-lookup"><span data-stu-id="56735-206">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="56735-207">Désactiver les exceptions de pare-feu pour les communications WS-Management.</span><span class="sxs-lookup"><span data-stu-id="56735-207">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="56735-208">Restaurer la valeur de LocalAccountTokenFilterPolicy sur 0, ce qui restreint l'accès à distance aux membres du groupe Administrateurs sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56735-208">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

- <span data-ttu-id="56735-209">Une configuration de point de terminaison de session est un groupe de paramètres qui définissent l’environnement d’une session.</span><span class="sxs-lookup"><span data-stu-id="56735-209">A session endpoint configuration is a group of settings that define the environment for a session.</span></span>
  <span data-ttu-id="56735-210">Chaque session qui se connecte à l’ordinateur doit utiliser l’une des configurations de point de terminaison de session inscrites sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56735-210">Every session that connects to the computer must use one of the session endpoint configurations that are registered on the computer.</span></span> <span data-ttu-id="56735-211">En refusant l’accès à distance à toutes les configurations de point de terminaison de session, vous empêchez efficacement les utilisateurs distants d’établir des sessions qui se connectent à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56735-211">By denying remote access to all session endpoint configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

## <span data-ttu-id="56735-212">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="56735-212">RELATED LINKS</span></span>

[<span data-ttu-id="56735-213">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="56735-213">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="56735-214">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="56735-214">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="56735-215">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="56735-215">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="56735-216">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="56735-216">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="56735-217">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="56735-217">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="56735-218">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="56735-218">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="56735-219">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="56735-219">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="56735-220">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="56735-220">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
