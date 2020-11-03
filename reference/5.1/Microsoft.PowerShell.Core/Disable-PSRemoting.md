---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202338"
---
# <span data-ttu-id="8a111-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="8a111-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="8a111-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8a111-104">SYNOPSIS</span></span>
<span data-ttu-id="8a111-105">Empêche les points de terminaison PowerShell de recevoir des connexions à distance.</span><span class="sxs-lookup"><span data-stu-id="8a111-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="8a111-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a111-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8a111-107">Description</span><span class="sxs-lookup"><span data-stu-id="8a111-107">DESCRIPTION</span></span>

<span data-ttu-id="8a111-108">L' `Disable-PSRemoting` applet de commande bloque l’accès à distance à toutes les configurations de point de terminaison de session Windows PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a111-108">The `Disable-PSRemoting` cmdlet blocks remote access to all Windows PowerShell session endpoint configurations on the local computer.</span></span> <span data-ttu-id="8a111-109">Cela comprend tous les points de terminaison créés par PowerShell 6 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8a111-109">This includes any endpoints created by PowerShell 6 or higher.</span></span>

<span data-ttu-id="8a111-110">Pour réactiver l’accès à distance à toutes les configurations de session, utilisez l’applet de commande `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="8a111-110">To re-enable remote access to all session configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="8a111-111">Cela comprend tous les points de terminaison créés par PowerShell 6 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8a111-111">This includes any endpoints created by PowerShell 6 or higher.</span></span> <span data-ttu-id="8a111-112">Pour activer l’accès à distance aux configurations de session sélectionnées, utilisez le paramètre **AccessMode** de l’applet de commande `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="8a111-112">To enable remote access to selected session configurations, use the **AccessMode** parameter of the `Set-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="8a111-113">Vous pouvez également utiliser les `Enable-PSSessionConfiguration` applets de commande et `Disable-PSSessionConfiguration` pour activer et désactiver les configurations de session pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8a111-113">You can also use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets to enable and disable session configurations for all users.</span></span> <span data-ttu-id="8a111-114">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="8a111-114">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8a111-115">Même après `Disable-PSRemoting` l’exécution, vous pouvez toujours établir des connexions de bouclage sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a111-115">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="8a111-116">Une connexion de bouclage est une session PowerShell à distance qui provient de et se connecte à la même machine locale.</span><span class="sxs-lookup"><span data-stu-id="8a111-116">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="8a111-117">Les sessions à distance provenant de sources externes restent bloquées.</span><span class="sxs-lookup"><span data-stu-id="8a111-117">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="8a111-118">Pour les connexions de bouclage, vous devez utiliser des informations d’identification implicites avec le paramètre **EnableNetworkAccess** .</span><span class="sxs-lookup"><span data-stu-id="8a111-118">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="8a111-119">Pour plus d’informations sur les connexions de bouclage, consultez [New-PSSession](New-PSSession.md).</span><span class="sxs-lookup"><span data-stu-id="8a111-119">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="8a111-120">Pour exécuter cette applet de commande, démarrez Windows PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="8a111-120">To run this cmdlet, start Windows PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="8a111-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8a111-121">EXAMPLES</span></span>

### <span data-ttu-id="8a111-122">Exemple 1 : empêcher l’accès à distance à toutes les configurations de session</span><span class="sxs-lookup"><span data-stu-id="8a111-122">Example 1: Prevent remote access to all session configurations</span></span>

<span data-ttu-id="8a111-123">Cet exemple empêche l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-123">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="8a111-124">Exemple 2 : empêcher l’accès à distance à toutes les configurations de session sans invite de confirmation</span><span class="sxs-lookup"><span data-stu-id="8a111-124">Example 2: Prevent remote access to all session configurations without confirmation prompt</span></span>

<span data-ttu-id="8a111-125">Cet exemple empêche l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="8a111-125">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="8a111-126">Exemple 3 : effets de l’exécution de cette applet de commande</span><span class="sxs-lookup"><span data-stu-id="8a111-126">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="8a111-127">Cet exemple montre l’effet de l’utilisation de l’applet de commande `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="8a111-127">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="8a111-128">Pour exécuter cette séquence de commandes, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="8a111-128">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="8a111-129">Après la désactivation des configurations de sessions, l' `New-PSSession` applet de commande tente de créer une session à distance sur l’ordinateur local (également appelé « bouclage »).</span><span class="sxs-lookup"><span data-stu-id="8a111-129">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="8a111-130">Étant donné que l’accès à distance est désactivé sur l’ordinateur local, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="8a111-130">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
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

### <span data-ttu-id="8a111-131">Exemple 4 : effets de l’exécution de cette applet de commande et Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="8a111-131">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="8a111-132">Cet exemple montre l’effet sur les configurations de session de à l’aide des `Disable-PSRemoting` applets de commande et `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="8a111-132">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="8a111-133">`Disable-PSRemoting` est utilisé pour désactiver l’accès à distance à toutes les configurations de point de terminaison de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a111-133">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="8a111-134">Le paramètre **Force** supprime toutes les invites utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-134">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="8a111-135">Les `Get-PSSessionConfiguration` applets de commande et `Format-Table` affichent les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-135">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="8a111-136">La sortie indique que l’accès aux configurations de point de terminaison est refusé à tous les utilisateurs distants distants disposant d’un jeton réseau.</span><span class="sxs-lookup"><span data-stu-id="8a111-136">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="8a111-137">Le groupe Administrateurs sur l’ordinateur local est autorisé à accéder aux configurations de point de terminaison, à condition qu’elles se connectent localement (également appelées « bouclage ») et qu’elles utilisent des informations d’identification implicites.</span><span class="sxs-lookup"><span data-stu-id="8a111-137">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="8a111-138">L' `Enable-PSRemoting` applet de commande réactive l’accès à distance à toutes les configurations de point de terminaison de session PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-138">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="8a111-139">Le paramètre **force** supprime toutes les invites utilisateur et redémarre le service WinRM sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="8a111-139">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="8a111-140">La nouvelle sortie indique que les descripteurs de sécurité **AccessDenied** ont été supprimés de toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="8a111-140">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="8a111-141">Exemple 5 : connexions de bouclage avec des configurations de point de terminaison de session désactivées</span><span class="sxs-lookup"><span data-stu-id="8a111-141">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="8a111-142">Cet exemple montre comment les configurations de point de terminaison sont désactivées et montre comment établir une connexion de bouclage à un point de terminaison désactivé.</span><span class="sxs-lookup"><span data-stu-id="8a111-142">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="8a111-143">`Disable-PSRemoting` désactive toutes les configurations de point de terminaison de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a111-143">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="8a111-144">La première utilisation des `New-PSSession` tentatives de création d’une session à distance sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a111-144">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="8a111-145">Ce type de connexion traverse la pile réseau et n’est pas un bouclage.</span><span class="sxs-lookup"><span data-stu-id="8a111-145">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="8a111-146">Par conséquent, la tentative de connexion au point de terminaison désactivé échoue avec une erreur **accès refusé** .</span><span class="sxs-lookup"><span data-stu-id="8a111-146">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="8a111-147">La deuxième utilisation de `New-PSSession` tente également de créer une session à distance sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a111-147">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="8a111-148">Dans ce cas, elle est réussie, car il s’agit d’une connexion de bouclage qui contourne la pile réseau.</span><span class="sxs-lookup"><span data-stu-id="8a111-148">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="8a111-149">Une connexion de bouclage est créée lorsque les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="8a111-149">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="8a111-150">Le nom de l’ordinateur auquel se connecter est « localhost ».</span><span class="sxs-lookup"><span data-stu-id="8a111-150">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="8a111-151">Aucune information d’identification n’est transmise.</span><span class="sxs-lookup"><span data-stu-id="8a111-151">No credentials are passed in.</span></span> <span data-ttu-id="8a111-152">L’utilisateur actuellement connecté (informations d’identification implicites) est utilisé pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="8a111-152">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="8a111-153">Le paramètre de commutateur **EnableNetworkAccess** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8a111-153">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="8a111-154">Pour plus d’informations sur les connexions de bouclage, consultez le document [New-PSSession](New-PSSession.md) .</span><span class="sxs-lookup"><span data-stu-id="8a111-154">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="8a111-155">Exemple 6 : empêcher l’accès à distance aux configurations de session qui ont des descripteurs de sécurité personnalisés</span><span class="sxs-lookup"><span data-stu-id="8a111-155">Example 6: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="8a111-156">Cet exemple montre que l' `Disable-PSRemoting` applet de commande désactive l’accès à distance à toutes les configurations de session qui incluent des configurations de session avec des descripteurs de sécurité personnalisés.</span><span class="sxs-lookup"><span data-stu-id="8a111-156">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="8a111-157">`Register-PSSessionConfiguration` crée la configuration de la session de **test** .</span><span class="sxs-lookup"><span data-stu-id="8a111-157">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="8a111-158">Le paramètre **filePath** spécifie un fichier de configuration de session qui personnalise la session.</span><span class="sxs-lookup"><span data-stu-id="8a111-158">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="8a111-159">Le paramètre **ShowSecurityDescriptorUI** affiche une boîte de dialogue qui définit les autorisations de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="8a111-159">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="8a111-160">Dans la boîte de dialogue autorisations, nous créons des autorisations d’accès complet personnalisées pour l’utilisateur indiqué.</span><span class="sxs-lookup"><span data-stu-id="8a111-160">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="8a111-161">Les `Get-PSSessionConfiguration` applets de commande et `Format-Table` affichent les configurations de session et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="8a111-161">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="8a111-162">La sortie indique que la configuration de la session de **test** autorise un accès interactif et des autorisations spéciales pour l’utilisateur indiqué.</span><span class="sxs-lookup"><span data-stu-id="8a111-162">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="8a111-163">`Disable-PSRemoting` désactive l’accès à distance à toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="8a111-163">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="8a111-164">Désormais `Get-PSSessionConfiguration` , les `Format-Table` applets de commande et indiquent qu’un descripteur de sécurité **AccessDenied** pour tous les utilisateurs du réseau est ajouté à toutes les configurations de session, y compris la configuration de la session de **test** .</span><span class="sxs-lookup"><span data-stu-id="8a111-164">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="8a111-165">Bien que les autres descripteurs de sécurité ne soient pas modifiés, le descripteur de sécurité « network_deny_all » est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="8a111-165">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="8a111-166">Cela est illustré par la tentative d’utilisation `New-PSSession` de pour se connecter à la configuration de la session de **test** .</span><span class="sxs-lookup"><span data-stu-id="8a111-166">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="8a111-167">Exemple 7 : réactiver l’accès à distance aux configurations de session sélectionnées</span><span class="sxs-lookup"><span data-stu-id="8a111-167">Example 7: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="8a111-168">Cet exemple illustre comment réactiver l'accès à distance uniquement pour les configurations de session sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="8a111-168">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="8a111-169">Après la désactivation de toutes les configurations de session, nous réactivons une session spécifique.</span><span class="sxs-lookup"><span data-stu-id="8a111-169">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="8a111-170">L' `Set-PSSessionConfiguration` applet de commande est utilisée pour modifier **Microsoft.** Configuration de session ServerManager.</span><span class="sxs-lookup"><span data-stu-id="8a111-170">The `Set-PSSessionConfiguration` cmdlet is used to change the **microsoft.ServerManager** session configuration.</span></span> <span data-ttu-id="8a111-171">Le paramètre **AccessMode** avec la valeur **Remote** Reactive l’accès à distance à la configuration.</span><span class="sxs-lookup"><span data-stu-id="8a111-171">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
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

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
```

## <span data-ttu-id="8a111-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8a111-172">PARAMETERS</span></span>

### <span data-ttu-id="8a111-173">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8a111-173">-Confirm</span></span>

<span data-ttu-id="8a111-174">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a111-174">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8a111-175">-Force</span><span class="sxs-lookup"><span data-stu-id="8a111-175">-Force</span></span>
<span data-ttu-id="8a111-176">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-176">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="8a111-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8a111-177">-WhatIf</span></span>

<span data-ttu-id="8a111-178">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a111-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8a111-179">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8a111-179">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8a111-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a111-180">CommonParameters</span></span>

<span data-ttu-id="8a111-181">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8a111-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a111-182">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8a111-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a111-183">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8a111-183">INPUTS</span></span>

### <span data-ttu-id="8a111-184">Aucun</span><span class="sxs-lookup"><span data-stu-id="8a111-184">None</span></span>

<span data-ttu-id="8a111-185">Vous ne pouvez pas diriger d’objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a111-185">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="8a111-186">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8a111-186">OUTPUTS</span></span>

### <span data-ttu-id="8a111-187">Aucun</span><span class="sxs-lookup"><span data-stu-id="8a111-187">None</span></span>

<span data-ttu-id="8a111-188">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8a111-188">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8a111-189">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8a111-189">NOTES</span></span>

- <span data-ttu-id="8a111-190">La désactivation des configurations de session n’annule pas toutes les modifications apportées par les `Enable-PSRemoting` applets de commande ou `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="8a111-190">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="8a111-191">Vous devrez peut-être annuler manuellement les modifications suivantes.</span><span class="sxs-lookup"><span data-stu-id="8a111-191">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="8a111-192">Arrêter et désactiver le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="8a111-192">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="8a111-193">Supprimer l'écouteur qui accepte les demandes sur toutes les adresses IP.</span><span class="sxs-lookup"><span data-stu-id="8a111-193">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="8a111-194">Désactiver les exceptions de pare-feu pour les communications WS-Management.</span><span class="sxs-lookup"><span data-stu-id="8a111-194">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="8a111-195">Restaurer la valeur de LocalAccountTokenFilterPolicy sur 0, ce qui restreint l'accès à distance aux membres du groupe Administrateurs sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-195">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

  <span data-ttu-id="8a111-196">Une configuration de session est un groupe de paramètres qui définissent l'environnement d'une session.</span><span class="sxs-lookup"><span data-stu-id="8a111-196">A session configuration is a group of settings that define the environment for a session.</span></span> <span data-ttu-id="8a111-197">Toutes les sessions qui se connectent à l'ordinateur doivent utiliser l'une des configurations de session enregistrées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-197">Every session that connects to the computer must use one of the session configurations that are registered on the computer.</span></span> <span data-ttu-id="8a111-198">En refusant l'accès à distance à toutes les configurations de session, vous empêchez effectivement les utilisateurs distants d'établir des sessions de connexion à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-198">By denying remote access to all session configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

  <span data-ttu-id="8a111-199">Dans Windows PowerShell 2,0, `Disable-PSRemoting` ajoute une entrée Deny_All aux descripteurs de sécurité de toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="8a111-199">In Windows PowerShell 2.0, `Disable-PSRemoting` adds a Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="8a111-200">Ce paramètre empêche tous les utilisateurs de créer des sessions gérées par l’utilisateur sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a111-200">This setting prevents all users from creating user-managed sessions to the local computer.</span></span> <span data-ttu-id="8a111-201">Dans Windows PowerShell 3,0, `Disable-PSRemoting` ajoute une entrée Network_Deny_All aux descripteurs de sécurité de toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="8a111-201">In Windows PowerShell 3.0, `Disable-PSRemoting` adds a Network_Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="8a111-202">Ce paramètre empêche les utilisateurs d’autres ordinateurs de créer des sessions gérées par l’utilisateur sur l’ordinateur local, mais permet aux utilisateurs de l’ordinateur local de créer des sessions de bouclage gérées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8a111-202">This setting prevents users on other computers from creating user-managed sessions on the local computer, but allows users of the local computer to create user-managed loopback sessions.</span></span>

  <span data-ttu-id="8a111-203">Dans Windows PowerShell 2,0, `Disable-PSRemoting` est l’équivalent de `Disable-PSSessionConfiguration -Name *` .</span><span class="sxs-lookup"><span data-stu-id="8a111-203">In Windows PowerShell 2.0, `Disable-PSRemoting` is the equivalent of `Disable-PSSessionConfiguration -Name *`.</span></span> <span data-ttu-id="8a111-204">Dans Windows PowerShell 3,0 et versions ultérieures, `Disable-PSRemoting` est l’équivalent de `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span><span class="sxs-lookup"><span data-stu-id="8a111-204">In Windows PowerShell 3.0 and later releases, `Disable-PSRemoting` is the equivalent of `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span></span>

## <span data-ttu-id="8a111-205">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8a111-205">RELATED LINKS</span></span>

[<span data-ttu-id="8a111-206">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a111-206">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="8a111-207">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="8a111-207">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="8a111-208">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a111-208">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="8a111-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8a111-209">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="8a111-210">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a111-210">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="8a111-211">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a111-211">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="8a111-212">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a111-212">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="8a111-213">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="8a111-213">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
