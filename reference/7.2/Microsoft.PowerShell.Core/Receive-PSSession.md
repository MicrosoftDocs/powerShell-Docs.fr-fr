---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 4bc7ba3a8129dd332b13bee30e386dd459d92226
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595507"
---
# <span data-ttu-id="b5b46-102">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-102">Receive-PSSession</span></span>

## <span data-ttu-id="b5b46-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b5b46-103">SYNOPSIS</span></span>

<span data-ttu-id="b5b46-104">Obtient les résultats des commandes dans des sessions déconnectées</span><span class="sxs-lookup"><span data-stu-id="b5b46-104">Gets results of commands in disconnected sessions</span></span>

## <span data-ttu-id="b5b46-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b5b46-105">SYNTAX</span></span>

### <span data-ttu-id="b5b46-106">Session (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b5b46-106">Session (Default)</span></span>

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5b46-107">Id</span><span class="sxs-lookup"><span data-stu-id="b5b46-107">Id</span></span>

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="b5b46-108">ComputerSessionName</span><span class="sxs-lookup"><span data-stu-id="b5b46-108">ComputerSessionName</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5b46-109">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="b5b46-109">ComputerInstanceId</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5b46-110">ConnectionUriSessionName</span><span class="sxs-lookup"><span data-stu-id="b5b46-110">ConnectionUriSessionName</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5b46-111">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="b5b46-111">ConnectionUriInstanceId</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5b46-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b5b46-112">InstanceId</span></span>

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5b46-113">Session</span><span class="sxs-lookup"><span data-stu-id="b5b46-113">SessionName</span></span>

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="b5b46-114">Description</span><span class="sxs-lookup"><span data-stu-id="b5b46-114">DESCRIPTION</span></span>

<span data-ttu-id="b5b46-115">L' `Receive-PSSession` applet de commande obtient les résultats des commandes qui s’exécutent dans les sessions PowerShell (**PSSession**) qui ont été déconnectées.</span><span class="sxs-lookup"><span data-stu-id="b5b46-115">The `Receive-PSSession` cmdlet gets the results of commands running in PowerShell sessions (**PSSession**) that were disconnected.</span></span> <span data-ttu-id="b5b46-116">Si la session est actuellement connectée, `Receive-PSSession` obtient les résultats des commandes qui étaient en cours d’exécution lorsque la session a été déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-116">If the session is currently connected, `Receive-PSSession` gets the results of commands that were running when the session was disconnected.</span></span> <span data-ttu-id="b5b46-117">Si la session est encore déconnectée, `Receive-PSSession` se connecte à la session, reprend toutes les commandes qui ont été interrompues et obtient les résultats des commandes en cours d’exécution dans la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-117">If the session is still disconnected, `Receive-PSSession` connects to the session, resumes any commands that were suspended, and gets the results of commands running in the session.</span></span>

<span data-ttu-id="b5b46-118">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b5b46-118">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="b5b46-119">Vous pouvez utiliser une `Receive-PSSession` en plus de ou au lieu d’une `Connect-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-119">You can use a `Receive-PSSession` in addition to or instead of a `Connect-PSSession` command.</span></span>
<span data-ttu-id="b5b46-120">`Receive-PSSession` peut se connecter à une session déconnectée ou reconnectée qui a été démarrée dans d’autres sessions ou sur d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="b5b46-120">`Receive-PSSession` can connect to any disconnected or reconnected session that was started in other sessions or on other computers.</span></span>

<span data-ttu-id="b5b46-121">`Receive-PSSession` fonctionne sur les **sessions PSSession** qui ont été déconnectées intentionnellement à l’aide de l’applet de commande `Disconnect-PSSession` ou du `Invoke-Command` paramètre **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="b5b46-121">`Receive-PSSession` works on **PSSessions** that were disconnected intentionally using the `Disconnect-PSSession` cmdlet or the `Invoke-Command` **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="b5b46-122">Ou déconnectés involontairement par une interruption du réseau.</span><span class="sxs-lookup"><span data-stu-id="b5b46-122">Or disconnected unintentionally by a network interruption.</span></span>

<span data-ttu-id="b5b46-123">Si vous utilisez l' `Receive-PSSession` applet de commande pour vous connecter à une session dans laquelle aucune commande n’est en cours d’exécution ou suspendue, `Receive-PSSession` se connecte à la session, mais ne retourne aucune sortie ni erreur.</span><span class="sxs-lookup"><span data-stu-id="b5b46-123">If you use the `Receive-PSSession` cmdlet to connect to a session in which no commands are running or suspended, `Receive-PSSession` connects to the session, but returns no output or errors.</span></span>

<span data-ttu-id="b5b46-124">Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span><span class="sxs-lookup"><span data-stu-id="b5b46-124">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="b5b46-125">Certains exemples utilisent la projection pour réduire la longueur de ligne et améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="b5b46-125">Some examples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="b5b46-126">Pour plus d’informations, consultez [about_Splatting](./About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="b5b46-126">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="b5b46-127">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b5b46-127">EXAMPLES</span></span>

### <span data-ttu-id="b5b46-128">Exemple 1 : se connecter à une session PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-128">Example 1: Connect to a PSSession</span></span>

<span data-ttu-id="b5b46-129">Cet exemple se connecte à une session sur un ordinateur distant et obtient les résultats des commandes qui s’exécutent dans une session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-129">This example connects to a session on a remote computer and gets the results of commands that are running in a session.</span></span>

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

<span data-ttu-id="b5b46-130">Le `Receive-PSSession` spécifie l’ordinateur distant avec le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="b5b46-130">The `Receive-PSSession` specifies the remote computer with the **ComputerName** parameter.</span></span> <span data-ttu-id="b5b46-131">Le paramètre **Name** identifie la session ITTask sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b5b46-131">The **Name** parameter identifies the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="b5b46-132">L’exemple obtient les résultats des commandes qui étaient en cours d’exécution dans la session ITTask.</span><span class="sxs-lookup"><span data-stu-id="b5b46-132">The example gets the results of commands that were running in the ITTask session.</span></span>

<span data-ttu-id="b5b46-133">Étant donné que la commande n’utilise pas le paramètre **distarget** , les résultats s’affichent sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-133">Because the command doesn't use the **OutTarget** parameter, the results appear on the command line.</span></span>

### <span data-ttu-id="b5b46-134">Exemple 2 : obtenir les résultats de toutes les commandes sur les sessions déconnectées</span><span class="sxs-lookup"><span data-stu-id="b5b46-134">Example 2: Get results of all commands on disconnected sessions</span></span>

<span data-ttu-id="b5b46-135">Cet exemple obtient les résultats de toutes les commandes exécutées dans toutes les sessions déconnectées sur deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="b5b46-135">This example gets the results of all commands running in all disconnected sessions on two remote computers.</span></span>

<span data-ttu-id="b5b46-136">Si une session n’a pas été déconnectée ou n’exécute pas de commandes, `Receive-PSSession` ne se connecte pas à la session et ne retourne aucune sortie ni erreur.</span><span class="sxs-lookup"><span data-stu-id="b5b46-136">If any session wasn't disconnected or isn't running commands, `Receive-PSSession` doesn't connect to the session and doesn't return any output or errors.</span></span>

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

<span data-ttu-id="b5b46-137">`Get-PSSession` utilise le paramètre **ComputerName** pour spécifier les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="b5b46-137">`Get-PSSession` uses the **ComputerName** parameter to specify the remote computers.</span></span> <span data-ttu-id="b5b46-138">Les objets sont envoyés dans le pipeline à `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b5b46-138">The objects are sent down the pipeline to `Receive-PSSession`.</span></span>

### <span data-ttu-id="b5b46-139">Exemple 3 : obtenir les résultats d’un script en cours d’exécution dans une session</span><span class="sxs-lookup"><span data-stu-id="b5b46-139">Example 3: Get the results of a script running in a session</span></span>

<span data-ttu-id="b5b46-140">Cet exemple utilise l' `Receive-PSSession` applet de commande pour obtenir les résultats d’un script qui s’exécutait dans la session d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b5b46-140">This example uses the `Receive-PSSession` cmdlet to get the results of a script that was running in a remote computer's session.</span></span>

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

<span data-ttu-id="b5b46-141">La commande utilise les paramètres **ComputerName** et **Name** pour identifier la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-141">The command uses the **ComputerName** and **Name** parameters to identify the disconnected session.</span></span>
<span data-ttu-id="b5b46-142">Elle utilise le paramètre **distarget** avec la valeur Job pour demander `Receive-PSSession` à de retourner les résultats en tant que tâche.</span><span class="sxs-lookup"><span data-stu-id="b5b46-142">It uses the **OutTarget** parameter with a value of Job to direct `Receive-PSSession` to return the results as a job.</span></span> <span data-ttu-id="b5b46-143">Le paramètre **JobName** spécifie un nom pour le travail dans la session reconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-143">The **JobName** parameter specifies a name for the job in the reconnected session.</span></span>
<span data-ttu-id="b5b46-144">Le paramètre **Credential** exécute la `Receive-PSSession` commande à l’aide des autorisations d’un administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="b5b46-144">The **Credential** parameter runs the `Receive-PSSession` command using the permissions of a domain administrator.</span></span>

<span data-ttu-id="b5b46-145">La sortie indique que `Receive-PSSession` a retourné les résultats sous la forme d’un travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b5b46-145">The output shows that `Receive-PSSession` returned the results as a job in the current session.</span></span> <span data-ttu-id="b5b46-146">Pour obtenir les résultats du travail, utilisez une `Receive-Job` commande</span><span class="sxs-lookup"><span data-stu-id="b5b46-146">To get the job results, use a `Receive-Job` command</span></span>

### <span data-ttu-id="b5b46-147">Exemple 4 : obtenir des résultats après une panne réseau</span><span class="sxs-lookup"><span data-stu-id="b5b46-147">Example 4: Get results after a network outage</span></span>

<span data-ttu-id="b5b46-148">Cet exemple utilise l' `Receive-PSSession` applet de commande pour obtenir les résultats d’un travail après qu’une panne du réseau a interrompu une connexion de session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-148">This example uses the `Receive-PSSession` cmdlet to get the results of a job after a network outage disrupts a session connection.</span></span> <span data-ttu-id="b5b46-149">PowerShell tente automatiquement de reconnecter la session une fois par seconde pendant les quatre minutes suivantes et abandonne l’effort uniquement si toutes les tentatives de l’intervalle de quatre minutes échouent.</span><span class="sxs-lookup"><span data-stu-id="b5b46-149">PowerShell automatically attempts to reconnect the session once per second for the next four minutes and abandons the effort only if all attempts in the four-minute interval fail.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

<span data-ttu-id="b5b46-150">L' `New-PSSession` applet de commande crée une session sur l’ordinateur SERVEUR01 et enregistre la session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-150">The `New-PSSession` cmdlet creates a session on the Server01 computer and saves the session in the `$s` variable.</span></span> <span data-ttu-id="b5b46-151">La `$s` variable indique que l' **État** est ouvert et que la **disponibilité** est disponible.</span><span class="sxs-lookup"><span data-stu-id="b5b46-151">The `$s` variable displays that the **State** is Opened and the **Availability** is Available.</span></span> <span data-ttu-id="b5b46-152">Ces valeurs indiquent que vous êtes connecté à la session et que vous pouvez exécuter des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-152">These values indicate that you're connected to the session and can run commands in the session.</span></span>

<span data-ttu-id="b5b46-153">L' `Invoke-Command` applet de commande exécute un script dans la session de la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-153">The `Invoke-Command` cmdlet runs a script in the session in the `$s` variable.</span></span> <span data-ttu-id="b5b46-154">Le script commence à s'exécuter et à retourner des données, mais une panne réseau se produit, qui interrompt la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-154">The script begins to run and return data, but a network outage occurs that interrupts the session.</span></span> <span data-ttu-id="b5b46-155">L'utilisateur doit quitter la session et redémarrer l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b5b46-155">The user has to exit the session and restart the local computer.</span></span>

<span data-ttu-id="b5b46-156">Lorsque l’ordinateur redémarre, l’utilisateur démarre PowerShell et exécute une `Get-PSSession` commande pour obtenir les sessions sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b5b46-156">When the computer restarts, the user starts PowerShell and runs a `Get-PSSession` command to get sessions on the Server01 computer.</span></span> <span data-ttu-id="b5b46-157">La sortie indique que la session **Active Directory** existe toujours sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b5b46-157">The output shows that the **AD** session still exists on the Server01 computer.</span></span> <span data-ttu-id="b5b46-158">L' **État** indique que la session **Active Directory** est déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-158">The **State** indicates that the **AD** session is disconnected.</span></span> <span data-ttu-id="b5b46-159">La valeur de **disponibilité** None indique que la session n’est connectée à aucune session cliente.</span><span class="sxs-lookup"><span data-stu-id="b5b46-159">The **Availability** value of None, indicates that the session isn't connected to any client sessions.</span></span>

<span data-ttu-id="b5b46-160">L' `Receive-PSSession` applet de commande se reconnecte à la session **ad** et obtient les résultats du script qui s’est exécuté dans la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-160">The `Receive-PSSession` cmdlet reconnects to the **AD** session and gets the results of the script that ran in the session.</span></span> <span data-ttu-id="b5b46-161">La commande utilise le paramètre **distarget** pour demander les résultats dans un travail nommé **ADJob**.</span><span class="sxs-lookup"><span data-stu-id="b5b46-161">The command uses the **OutTarget** parameter to request the results in a job named **ADJob**.</span></span> <span data-ttu-id="b5b46-162">La commande retourne un objet de traitement et la sortie indique que le script est toujours en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b5b46-162">The command returns a job object and the output indicates that the script is still running.</span></span>

<span data-ttu-id="b5b46-163">L' `Get-PSSession` applet de commande est utilisée pour vérifier l’état de la tâche.</span><span class="sxs-lookup"><span data-stu-id="b5b46-163">The `Get-PSSession` cmdlet is used to check the job state.</span></span> <span data-ttu-id="b5b46-164">La sortie confirme que l' `Receive-PSSession` applet de commande s’est reconnectée à la session **ad** , qui est désormais ouverte et disponible pour les commandes.</span><span class="sxs-lookup"><span data-stu-id="b5b46-164">The output confirms that the `Receive-PSSession` cmdlet reconnected to the **AD** session, which is now open and available for commands.</span></span> <span data-ttu-id="b5b46-165">Et, le script a repris l’exécution et obtient les résultats du script.</span><span class="sxs-lookup"><span data-stu-id="b5b46-165">And, the script resumed execution and is getting the script results.</span></span>

### <span data-ttu-id="b5b46-166">Exemple 5 : reconnexion à des sessions déconnectées</span><span class="sxs-lookup"><span data-stu-id="b5b46-166">Example 5: Reconnect to disconnected sessions</span></span>

<span data-ttu-id="b5b46-167">Cet exemple utilise l' `Receive-PSSession` applet de commande pour se reconnecter aux sessions qui ont été intentionnellement déconnectées et obtenir les résultats des tâches qui étaient en cours d’exécution dans les sessions.</span><span class="sxs-lookup"><span data-stu-id="b5b46-167">This example uses the `Receive-PSSession` cmdlet to reconnect to sessions that were intentionally disconnected and get the results of jobs that were running in the sessions.</span></span>

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

<span data-ttu-id="b5b46-168">L' `Invoke-Command` applet de commande exécute un script sur trois ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="b5b46-168">The `Invoke-Command` cmdlet runs a script on three remote computers.</span></span> <span data-ttu-id="b5b46-169">Étant donné que le script rassemble et synthétise les données de plusieurs bases de données, le script prend souvent une durée prolongée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-169">Because the script gathers and summarizes data from multiple databases, it often takes the script an extended time to finish.</span></span> <span data-ttu-id="b5b46-170">La commande utilise le paramètre **InDisconnectedSession** qui démarre les scripts, puis déconnecte immédiatement les sessions.</span><span class="sxs-lookup"><span data-stu-id="b5b46-170">The command uses the **InDisconnectedSession** parameter that starts the scripts and then immediately disconnects the sessions.</span></span> <span data-ttu-id="b5b46-171">Le paramètre **SessionOption** étend la valeur **IdleTimeout** de la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-171">The **SessionOption** parameter extends the **IdleTimeout** value of the disconnected session.</span></span> <span data-ttu-id="b5b46-172">Les sessions déconnectées sont considérées comme inactives à partir du moment où elles sont déconnectées.</span><span class="sxs-lookup"><span data-stu-id="b5b46-172">Disconnected sessions are considered idle from the moment they're disconnected.</span></span> <span data-ttu-id="b5b46-173">Il est important de définir le délai d’inactivité suffisamment longtemps pour que les commandes puissent se terminer et que vous puissiez vous reconnecter à la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-173">It's important to set the idle time-out for long enough so that the commands can complete and you can reconnect to the session.</span></span> <span data-ttu-id="b5b46-174">Vous pouvez définir la valeur **IdleTimeout** uniquement lorsque vous créez la **session PSSession** et la modifier uniquement lorsque vous vous déconnectez.</span><span class="sxs-lookup"><span data-stu-id="b5b46-174">You can set the **IdleTimeout** only when you create the **PSSession** and change it only when you disconnect from it.</span></span> <span data-ttu-id="b5b46-175">Vous ne pouvez pas modifier la valeur **IdleTimeout** quand vous vous connectez à une **session PSSession** ou recevez ses résultats.</span><span class="sxs-lookup"><span data-stu-id="b5b46-175">You can't change the **IdleTimeout** value when you connect to a **PSSession** or receiving its results.</span></span> <span data-ttu-id="b5b46-176">Après l’exécution de la commande, l’utilisateur quitte PowerShell et ferme l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5b46-176">After running the command, the user exits PowerShell and closes the computer.</span></span>

<span data-ttu-id="b5b46-177">Le lendemain, l’utilisateur reprend Windows, démarre PowerShell et utilise `Get-PSSession` pour recevoir les sessions dans lesquelles les scripts étaient en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b5b46-177">The next day, the user resumes Windows, starts PowerShell, and uses `Get-PSSession` to get the sessions in which the scripts were running.</span></span> <span data-ttu-id="b5b46-178">La commande identifie les sessions par le nom d’ordinateur, le nom de session et le nom de la configuration de session, et enregistre les sessions dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-178">The command identifies the sessions by the computer name, session name, and the name of the session configuration and saves the sessions in the `$s` variable.</span></span> <span data-ttu-id="b5b46-179">La valeur de la `$s` variable s’affiche et indique que les sessions sont déconnectées, mais qu’elles ne sont pas occupées.</span><span class="sxs-lookup"><span data-stu-id="b5b46-179">The value of the `$s` variable is displayed and shows that the sessions are disconnected, but aren't busy.</span></span>

<span data-ttu-id="b5b46-180">L' `Receive-PSSession` applet de commande se connecte aux sessions dans la `$s` variable et obtient les résultats.</span><span class="sxs-lookup"><span data-stu-id="b5b46-180">The `Receive-PSSession` cmdlet connects to the sessions in the `$s` variable and gets their results.</span></span>
<span data-ttu-id="b5b46-181">La commande enregistre les résultats dans la `$Results` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-181">The command saves the results in the `$Results` variable.</span></span> <span data-ttu-id="b5b46-182">La `$s` variable s’affiche et indique que les sessions sont connectées et disponibles pour les commandes.</span><span class="sxs-lookup"><span data-stu-id="b5b46-182">The `$s` variable is displayed and shows that the sessions are connected and available for commands.</span></span>

<span data-ttu-id="b5b46-183">Les résultats du script dans la `$Results` variable s’affichent dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5b46-183">The script results in the `$Results` variable are displayed in the PowerShell console.</span></span> <span data-ttu-id="b5b46-184">Si l’un des résultats est inattendu, l’utilisateur peut exécuter des commandes dans les sessions pour examiner la cause racine.</span><span class="sxs-lookup"><span data-stu-id="b5b46-184">If any of the results are unexpected, the user can run commands in the sessions to investigate the root cause.</span></span>

### <span data-ttu-id="b5b46-185">Exemple 6 : exécution d’un travail dans une session déconnectée</span><span class="sxs-lookup"><span data-stu-id="b5b46-185">Example 6: Running a job in a disconnected session</span></span>

<span data-ttu-id="b5b46-186">Cet exemple montre ce qui arrive à un travail qui s’exécute dans une session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-186">This example shows what happens to a job that's running in a disconnected session.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

<span data-ttu-id="b5b46-187">L' `New-PSSession` applet de commande crée la session de test sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b5b46-187">The `New-PSSession` cmdlet creates the Test session on the Server01 computer.</span></span> <span data-ttu-id="b5b46-188">La commande enregistre la session dans la variable `$s`.</span><span class="sxs-lookup"><span data-stu-id="b5b46-188">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="b5b46-189">L' `Invoke-Command` applet de commande exécute une commande dans la session de la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-189">The `Invoke-Command` cmdlet runs a command in the session in the `$s` variable.</span></span> <span data-ttu-id="b5b46-190">La commande utilise le paramètre **AsJob** pour exécuter la commande en tant que tâche et crée l’objet de traitement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b5b46-190">The command uses the **AsJob** parameter to run the command as a job and creates the job object in the current session.</span></span>
<span data-ttu-id="b5b46-191">La commande retourne un objet de traitement qui est enregistré dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-191">The command returns a job object that's saved in the `$j` variable.</span></span> <span data-ttu-id="b5b46-192">La `$j` variable affiche l’objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="b5b46-192">The `$j` variable displays the job object.</span></span>

<span data-ttu-id="b5b46-193">L’objet de session dans la `$s` variable est envoyé vers le pipeline vers `Disconnect-PSSession` et la session est déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-193">The session object in the `$s` variable is sent down the pipeline to `Disconnect-PSSession` and the session is disconnected.</span></span>

<span data-ttu-id="b5b46-194">La `$j` variable s’affiche et montre l’effet de la déconnexion de l’objet de traitement dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-194">The `$j` variable is displayed and shows the effect of disconnecting the job object in the `$j` variable.</span></span> <span data-ttu-id="b5b46-195">L'état de la tâche est maintenant Déconnecté.</span><span class="sxs-lookup"><span data-stu-id="b5b46-195">The job state is now Disconnected.</span></span>

<span data-ttu-id="b5b46-196">La `Receive-Job` est exécutée sur la tâche dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-196">The `Receive-Job` is run on the job in the `$j` variable.</span></span> <span data-ttu-id="b5b46-197">La sortie indique que la tâche a commencé à retourner une sortie avant la déconnexion de la session et que la tâche a été déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-197">The output shows that the job began to return output before the session and the job were disconnected.</span></span>

<span data-ttu-id="b5b46-198">L' `Connect-PSSession` applet de commande est exécutée dans la même session cliente.</span><span class="sxs-lookup"><span data-stu-id="b5b46-198">The `Connect-PSSession` cmdlet is run in the same client session.</span></span> <span data-ttu-id="b5b46-199">La commande se reconnecte à la session de test sur l’ordinateur SERVEUR01 et enregistre la session dans la `$s2` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-199">The command reconnects to the Test session on the Server01 computer and saves the session in the `$s2` variable.</span></span>

<span data-ttu-id="b5b46-200">L' `Receive-PSSession` applet de commande obtient les résultats du travail qui s’exécutait dans la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-200">The `Receive-PSSession` cmdlet gets the results of the job that was running in the session.</span></span> <span data-ttu-id="b5b46-201">Étant donné que la commande est exécutée dans la même session, `Receive-PSSession` retourne les résultats sous la forme d’un travail par défaut et réutilise le même objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="b5b46-201">Because the command is run in the same session, `Receive-PSSession` returns the results as a job by default and reuses the same job object.</span></span> <span data-ttu-id="b5b46-202">La commande enregistre la tâche dans la `$j2` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-202">The command saves the job in the `$j2` variable.</span></span> <span data-ttu-id="b5b46-203">L' `Receive-Job` applet de commande obtient les résultats de la tâche dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-203">The `Receive-Job` cmdlet gets the results of the job in the `$j` variable.</span></span>

## <span data-ttu-id="b5b46-204">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5b46-204">PARAMETERS</span></span>

### <span data-ttu-id="b5b46-205">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="b5b46-205">-AllowRedirection</span></span>

<span data-ttu-id="b5b46-206">Indique que cette applet de commande autorise la redirection de cette connexion vers un autre Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="b5b46-206">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="b5b46-207">Quand vous utilisez le paramètre **ConnectionURI**, la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="b5b46-207">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="b5b46-208">Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.</span><span class="sxs-lookup"><span data-stu-id="b5b46-208">By default, PowerShell doesn't redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="b5b46-209">Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount**.</span><span class="sxs-lookup"><span data-stu-id="b5b46-209">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="b5b46-210">Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="b5b46-210">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="b5b46-211">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="b5b46-211">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-212">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="b5b46-212">-ApplicationName</span></span>

<span data-ttu-id="b5b46-213">Spécifie une application.</span><span class="sxs-lookup"><span data-stu-id="b5b46-213">Specifies an application.</span></span> <span data-ttu-id="b5b46-214">Cette applet de commande se connecte uniquement aux sessions qui utilisent l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-214">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="b5b46-215">Entrez le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="b5b46-215">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="b5b46-216">Par exemple, dans l’URI de connexion suivant, WSMan est le nom de l’application : `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="b5b46-216">For example, in the following connection URI, WSMan is the application name: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="b5b46-217">Le nom d'application d'une session est stocké dans la propriété **Runspace.ConnectionInfo.AppName** de la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-217">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="b5b46-218">La valeur du paramètre est utilisée pour sélectionner et filtrer les sessions.</span><span class="sxs-lookup"><span data-stu-id="b5b46-218">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="b5b46-219">Elle ne modifie pas l’application utilisée par la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-219">It doesn't change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-220">-Authentification</span><span class="sxs-lookup"><span data-stu-id="b5b46-220">-Authentication</span></span>

<span data-ttu-id="b5b46-221">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur dans la commande pour se reconnecter à une session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-221">Specifies the mechanism that's used to authenticate the user credentials in the command to reconnect to a disconnected session.</span></span> <span data-ttu-id="b5b46-222">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="b5b46-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b5b46-223">Default</span><span class="sxs-lookup"><span data-stu-id="b5b46-223">Default</span></span>
- <span data-ttu-id="b5b46-224">Basic</span><span class="sxs-lookup"><span data-stu-id="b5b46-224">Basic</span></span>
- <span data-ttu-id="b5b46-225">CredSSP</span><span class="sxs-lookup"><span data-stu-id="b5b46-225">Credssp</span></span>
- <span data-ttu-id="b5b46-226">Digest</span><span class="sxs-lookup"><span data-stu-id="b5b46-226">Digest</span></span>
- <span data-ttu-id="b5b46-227">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b5b46-227">Kerberos</span></span>
- <span data-ttu-id="b5b46-228">Negotiate</span><span class="sxs-lookup"><span data-stu-id="b5b46-228">Negotiate</span></span>
- <span data-ttu-id="b5b46-229">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="b5b46-229">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="b5b46-230">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="b5b46-230">The default value is Default.</span></span>

<span data-ttu-id="b5b46-231">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="b5b46-231">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="b5b46-232">L’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="b5b46-232">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="b5b46-233">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="b5b46-233">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="b5b46-234">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="b5b46-234">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-235">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="b5b46-235">-CertificateThumbprint</span></span>

<span data-ttu-id="b5b46-236">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-236">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="b5b46-237">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="b5b46-237">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="b5b46-238">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="b5b46-238">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="b5b46-239">Les certificats peuvent être mappés uniquement aux comptes d’utilisateurs locaux et ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="b5b46-239">Certificates can be mapped only to local user accounts, and don't work with domain accounts.</span></span>

<span data-ttu-id="b5b46-240">Pour obtenir une empreinte numérique de certificat, utilisez une `Get-Item` `Get-ChildItem` commande ou dans le `Cert:` lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5b46-240">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-241">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b5b46-241">-ComputerName</span></span>

<span data-ttu-id="b5b46-242">Spécifie l'ordinateur sur lequel est stockée la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-242">Specifies the computer on which the disconnected session is stored.</span></span> <span data-ttu-id="b5b46-243">Les sessions sont stockées sur l’ordinateur qui se trouve à l’extrémité du serveur ou de la réception d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="b5b46-243">Sessions are stored on the computer that's at the server-side, or receiving end of a connection.</span></span> <span data-ttu-id="b5b46-244">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b5b46-244">The default is the local computer.</span></span>

<span data-ttu-id="b5b46-245">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet (FQDN) d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5b46-245">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of one computer.</span></span>
<span data-ttu-id="b5b46-246">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="b5b46-246">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="b5b46-247">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ), `$env:COMPUTERNAME` ou localhost.</span><span class="sxs-lookup"><span data-stu-id="b5b46-247">To specify the local computer, type the computer name, a dot (`.`), `$env:COMPUTERNAME`, or localhost.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-248">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="b5b46-248">-ConfigurationName</span></span>

<span data-ttu-id="b5b46-249">Spécifie le nom d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-249">Specifies the name of a session configuration.</span></span> <span data-ttu-id="b5b46-250">Cette applet de commande se connecte uniquement aux sessions qui utilisent la configuration de session spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-250">This cmdlet connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="b5b46-251">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-251">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="b5b46-252">Si vous spécifiez uniquement le nom de la configuration, l'URI de schéma suivant est ajouté :</span><span class="sxs-lookup"><span data-stu-id="b5b46-252">If you specify only the configuration name, the following schema URI is prepended:</span></span>

<span data-ttu-id="b5b46-253">`http://schemas.microsoft.com/powershell`.</span><span class="sxs-lookup"><span data-stu-id="b5b46-253">`http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="b5b46-254">Le nom de configuration d'une session est stocké dans la propriété **ConfigurationName** de la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-254">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="b5b46-255">La valeur du paramètre est utilisée pour sélectionner et filtrer les sessions.</span><span class="sxs-lookup"><span data-stu-id="b5b46-255">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="b5b46-256">Elle ne modifie pas la configuration de session utilisée par la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-256">It doesn't change the session configuration that the session uses.</span></span>

<span data-ttu-id="b5b46-257">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](./About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b5b46-257">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-258">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="b5b46-258">-ConnectionUri</span></span>

<span data-ttu-id="b5b46-259">Spécifie un URI qui définit le point de terminaison de connexion utilisé pour se reconnecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-259">Specifies a URI that defines the connection endpoint that is used to reconnect to the disconnected session.</span></span>

<span data-ttu-id="b5b46-260">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="b5b46-260">The URI must be fully qualified.</span></span> <span data-ttu-id="b5b46-261">Le format de la chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="b5b46-261">The string's format is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="b5b46-262">La valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b5b46-262">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="b5b46-263">Si vous ne spécifiez pas d’URI de connexion, vous pouvez utiliser les paramètres **UseSSL**, **ComputerName**, **port** et **applicationName** pour spécifier les valeurs d’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="b5b46-263">If you don't specify a connection URI, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="b5b46-264">Les valeurs valides du segment **Transport** de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b5b46-264">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="b5b46-265">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="b5b46-265">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with standard ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="b5b46-266">Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="b5b46-266">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="b5b46-267">Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-267">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-268">-Credential</span><span class="sxs-lookup"><span data-stu-id="b5b46-268">-Credential</span></span>

<span data-ttu-id="b5b46-269">Spécifie un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-269">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="b5b46-270">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="b5b46-270">The default is the current user.</span></span>

<span data-ttu-id="b5b46-271">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="b5b46-271">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="b5b46-272">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b5b46-272">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="b5b46-273">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="b5b46-273">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="b5b46-274">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="b5b46-274">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-275">-Id</span><span class="sxs-lookup"><span data-stu-id="b5b46-275">-Id</span></span>

<span data-ttu-id="b5b46-276">Spécifie l’ID d’une session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-276">Specifies the ID of a disconnected session.</span></span> <span data-ttu-id="b5b46-277">Le paramètre **ID** fonctionne uniquement lorsque la session déconnectée a déjà été connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="b5b46-277">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="b5b46-278">Ce paramètre est valide, mais il n’est pas effectif, lorsque la session est stockée sur l’ordinateur local, mais n’a pas été connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="b5b46-278">This parameter is valid, but not effective, when the session is stored on the local computer, but wasn't connected to the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-279">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="b5b46-279">-InstanceId</span></span>

<span data-ttu-id="b5b46-280">Spécifie l'ID d'instance de la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-280">Specifies the instance ID of the disconnected session.</span></span> <span data-ttu-id="b5b46-281">L’ID d’instance est un GUID qui identifie de façon unique une **session PSSession** sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="b5b46-281">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span> <span data-ttu-id="b5b46-282">L’ID d’instance est stocké dans la propriété **InstanceID** de la **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="b5b46-282">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-283">-JobName</span><span class="sxs-lookup"><span data-stu-id="b5b46-283">-JobName</span></span>

<span data-ttu-id="b5b46-284">Spécifie un nom convivial pour le travail `Receive-PSSession` retourné par.</span><span class="sxs-lookup"><span data-stu-id="b5b46-284">Specifies a friendly name for the job that `Receive-PSSession` returns.</span></span>

<span data-ttu-id="b5b46-285">`Receive-PSSession` retourne un travail lorsque la valeur du paramètre de l’objet de la **cible** est Job ou que le travail en cours d’exécution dans la session déconnectée a été démarré dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b5b46-285">`Receive-PSSession` returns a job when the value of the **OutTarget** parameter is Job or the job that's running in the disconnected session was started in the current session.</span></span>

<span data-ttu-id="b5b46-286">Si le travail en cours d’exécution dans la session déconnectée a démarré dans la session active, PowerShell réutilise l’objet de traitement d’origine dans la session et ignore la valeur du paramètre **JobName** .</span><span class="sxs-lookup"><span data-stu-id="b5b46-286">If the job that's running in the disconnected session was started in the current session, PowerShell reuses the original job object in the session and ignores the value of the **JobName** parameter.</span></span>

<span data-ttu-id="b5b46-287">Si le travail en cours d’exécution dans la session déconnectée a été démarré dans une autre session, PowerShell crée un nouvel objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="b5b46-287">If the job that's running in the disconnected session was started in a different session, PowerShell creates a new job object.</span></span> <span data-ttu-id="b5b46-288">Il utilise un nom par défaut, mais vous pouvez utiliser ce paramètre pour modifier le nom.</span><span class="sxs-lookup"><span data-stu-id="b5b46-288">It uses a default name, but you can use this parameter to change the name.</span></span>

<span data-ttu-id="b5b46-289">Si la valeur par défaut ou la valeur explicite du paramètre **untarget** n’est pas Job, la commande est réussie, mais le paramètre **JobName** n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="b5b46-289">If the default value or explicit value of the **OutTarget** parameter isn't Job, the command succeeds, but the **JobName** parameter has no effect.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-290">-Name</span><span class="sxs-lookup"><span data-stu-id="b5b46-290">-Name</span></span>

<span data-ttu-id="b5b46-291">Spécifie le nom convivial de la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-291">Specifies the friendly name of the disconnected session.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-292">-En-dessous</span><span class="sxs-lookup"><span data-stu-id="b5b46-292">-OutTarget</span></span>

<span data-ttu-id="b5b46-293">Détermine la façon dont les résultats de la session sont retournés.</span><span class="sxs-lookup"><span data-stu-id="b5b46-293">Determines how the session results are returned.</span></span> <span data-ttu-id="b5b46-294">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="b5b46-294">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b5b46-295">**Travail**.</span><span class="sxs-lookup"><span data-stu-id="b5b46-295">**Job**.</span></span> <span data-ttu-id="b5b46-296">retourne les résultats de façon asynchrone dans un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="b5b46-296">Returns the results asynchronously in a job object.</span></span> <span data-ttu-id="b5b46-297">Vous pouvez utiliser le paramètre **JobName** pour spécifier un nom ou un nouveau nom pour la tâche.</span><span class="sxs-lookup"><span data-stu-id="b5b46-297">You can use the **JobName** parameter to specify a name or new name for the job.</span></span>
- <span data-ttu-id="b5b46-298">**Hôte**.</span><span class="sxs-lookup"><span data-stu-id="b5b46-298">**Host**.</span></span> <span data-ttu-id="b5b46-299">retourne les résultats dans la ligne de commande (synchrone).</span><span class="sxs-lookup"><span data-stu-id="b5b46-299">Returns the results to the command line (synchronously).</span></span> <span data-ttu-id="b5b46-300">Si la commande est reprise ou si les résultats se composent d'un grand nombre d'objets, la réponse peut être retardée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-300">If the command is being resumed or the results consist of a large number of objects, the response might be delayed.</span></span>

<span data-ttu-id="b5b46-301">La valeur par défaut du paramètre de **précible** est host.</span><span class="sxs-lookup"><span data-stu-id="b5b46-301">The default value of the **OutTarget** parameter is Host.</span></span> <span data-ttu-id="b5b46-302">Si la commande qui est reçue dans une session déconnectée a été démarrée dans la session active, la valeur par défaut du paramètre de la **cible** est le formulaire dans lequel la commande a été démarrée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-302">If the command that's being received in a disconnected session was started in the current session, the default value of the **OutTarget** parameter is the form in which the command was started.</span></span> <span data-ttu-id="b5b46-303">Si la commande a été démarrée en tant que tâche, elle est retournée par défaut en tant que tâche.</span><span class="sxs-lookup"><span data-stu-id="b5b46-303">If the command was started as a job, by default, it's returned as a job.</span></span> <span data-ttu-id="b5b46-304">Dans le cas contraire, elle est retournée au programme hôte par défaut.</span><span class="sxs-lookup"><span data-stu-id="b5b46-304">Otherwise, it's returned to the host program by default.</span></span>

<span data-ttu-id="b5b46-305">En général, le programme hôte affiche sans retard les objets retournés dans la ligne de commande, mais ce comportement peut varier.</span><span class="sxs-lookup"><span data-stu-id="b5b46-305">Typically, the host program displays returned objects at the command line without delay, but this behavior can vary.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-306">-Port</span><span class="sxs-lookup"><span data-stu-id="b5b46-306">-Port</span></span>

<span data-ttu-id="b5b46-307">Spécifie le port réseau de l’ordinateur distant qui est utilisé pour se reconnecter à la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-307">Specifies the remote computer's network port that's used to reconnect to the session.</span></span> <span data-ttu-id="b5b46-308">Pour vous connecter à un ordinateur distant, celui-ci doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="b5b46-308">To connect to a remote computer, it must be listening on the port that the connection uses.</span></span> <span data-ttu-id="b5b46-309">Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="b5b46-309">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="b5b46-310">Avant d’utiliser un autre port, vous devez configurer l’écouteur WinRM sur l’ordinateur distant pour qu’il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="b5b46-310">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen on that port.</span></span> <span data-ttu-id="b5b46-311">Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="b5b46-311">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="b5b46-312">N’utilisez pas le paramètre **port** à moins qu’il soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b5b46-312">Don't use the **Port** parameter unless it's necessary.</span></span> <span data-ttu-id="b5b46-313">Le port défini dans la commande s’applique à tous les ordinateurs ou sessions sur lesquels la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b5b46-313">The port that's set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="b5b46-314">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="b5b46-314">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-315">-Session</span><span class="sxs-lookup"><span data-stu-id="b5b46-315">-Session</span></span>

<span data-ttu-id="b5b46-316">Spécifie la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-316">Specifies the disconnected session.</span></span> <span data-ttu-id="b5b46-317">Entrez une variable qui contient la **session PSSession** ou une commande qui crée ou obtient la **session PSSession**, telle qu’une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-317">Enter a variable that contains the **PSSession** or a command that creates or gets the **PSSession**, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-318">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="b5b46-318">-SessionOption</span></span>

<span data-ttu-id="b5b46-319">Spécifie les options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-319">Specifies advanced options for the session.</span></span> <span data-ttu-id="b5b46-320">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-320">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="b5b46-321">Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="b5b46-321">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="b5b46-322">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-322">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="b5b46-323">Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-323">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="b5b46-324">Toutefois, elles ne sont pas prioritaires sur les valeurs maximales, les quotas ou les limites définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-324">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="b5b46-325">Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="b5b46-325">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="b5b46-326">Pour plus d’informations sur la variable de préférence **$PSSessionOption** , consultez [about_Preference_Variables](./About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="b5b46-326">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span> <span data-ttu-id="b5b46-327">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](./About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b5b46-327">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-328">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="b5b46-328">-UseSSL</span></span>

<span data-ttu-id="b5b46-329">Indique que cette applet de commande utilise le protocole SSL (Secure Sockets Layer) (SSL) pour se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-329">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="b5b46-330">Par défaut, SSL n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="b5b46-330">By default, SSL isn't used.</span></span>

<span data-ttu-id="b5b46-331">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="b5b46-331">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="b5b46-332">**UseSSL** est une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d'une connexion HTTP.</span><span class="sxs-lookup"><span data-stu-id="b5b46-332">**UseSSL** is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="b5b46-333">Si vous utilisez ce paramètre et que le protocole SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="b5b46-333">If you use this parameter and SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5b46-334">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b5b46-334">-Confirm</span></span>

<span data-ttu-id="b5b46-335">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-335">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b5b46-336">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b5b46-336">-WhatIf</span></span>

<span data-ttu-id="b5b46-337">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-337">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b5b46-338">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-338">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b5b46-339">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5b46-339">CommonParameters</span></span>

<span data-ttu-id="b5b46-340">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b5b46-340">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5b46-341">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b5b46-341">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5b46-342">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b5b46-342">INPUTS</span></span>

### <span data-ttu-id="b5b46-343">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-343">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="b5b46-344">Vous pouvez diriger les objets de session vers cette applet de commande, tels que les objets retournés par l’applet de commande `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b5b46-344">You can pipe session objects to this cmdlet, such as objects returned by the `Get-PSSession` cmdlet.</span></span>

### <span data-ttu-id="b5b46-345">System.Int32</span><span class="sxs-lookup"><span data-stu-id="b5b46-345">System.Int32</span></span>

<span data-ttu-id="b5b46-346">Vous pouvez diriger les ID de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-346">You can pipe session Ids to this cmdlet.</span></span>

### <span data-ttu-id="b5b46-347">System.Guid</span><span class="sxs-lookup"><span data-stu-id="b5b46-347">System.Guid</span></span>

<span data-ttu-id="b5b46-348">Vous pouvez diriger les ID d’instance des sessions de cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-348">You can pipe the instance Ids of sessions this cmdlet.</span></span>

### <span data-ttu-id="b5b46-349">System.String</span><span class="sxs-lookup"><span data-stu-id="b5b46-349">System.String</span></span>

<span data-ttu-id="b5b46-350">Vous pouvez diriger les noms de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-350">You can pipe session names to this cmdlet.</span></span>

## <span data-ttu-id="b5b46-351">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b5b46-351">OUTPUTS</span></span>

### <span data-ttu-id="b5b46-352">System. Management. Automation. job ou PSObject</span><span class="sxs-lookup"><span data-stu-id="b5b46-352">System.Management.Automation.Job or PSObject</span></span>

<span data-ttu-id="b5b46-353">Cette applet de commande retourne les résultats des commandes exécutées dans la session déconnectée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="b5b46-353">This cmdlet returns the results of commands that ran in the disconnected session, if any.</span></span> <span data-ttu-id="b5b46-354">Si la valeur ou la valeur par défaut du paramètre de **précible** est Job, `Receive-PSSession` retourne un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="b5b46-354">If the value or default value of the **OutTarget** parameter is Job, `Receive-PSSession` returns a job object.</span></span> <span data-ttu-id="b5b46-355">Sinon, elle retourne des objets qui représentent les résultats de cette commande.</span><span class="sxs-lookup"><span data-stu-id="b5b46-355">Otherwise, it returns objects that represent that command results.</span></span>

## <span data-ttu-id="b5b46-356">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b5b46-356">NOTES</span></span>

<span data-ttu-id="b5b46-357">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="b5b46-357">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="b5b46-358">`Receive-PSSession` Obtient les résultats uniquement à partir des sessions qui ont été déconnectées.</span><span class="sxs-lookup"><span data-stu-id="b5b46-358">`Receive-PSSession` gets results only from sessions that were disconnected.</span></span> <span data-ttu-id="b5b46-359">Seules les sessions connectées à, ou qui se terminent à, les ordinateurs qui exécutent PowerShell 3,0 ou des versions ultérieures peuvent être déconnectés et reconnectés.</span><span class="sxs-lookup"><span data-stu-id="b5b46-359">Only sessions that are connected to, or terminate at, computers that run PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

<span data-ttu-id="b5b46-360">Si les commandes qui étaient en cours d’exécution dans la session déconnectée n’ont pas généré de résultats ou si les résultats ont déjà été retournés à une autre session, `Receive-PSSession` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="b5b46-360">If the commands that were running in the disconnected session didn't generate results or if the results were already returned to another session, `Receive-PSSession` doesn't generate any output.</span></span>

<span data-ttu-id="b5b46-361">Le mode de mise en mémoire tampon de sortie d’une session détermine la manière dont les commandes dans la session gèrent la sortie lorsque la session est déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-361">A session's output buffering mode determines how commands in the session manage output when the session is disconnected.</span></span> <span data-ttu-id="b5b46-362">Lorsque la valeur de l’option **OutputBufferingMode** de la session est Drop et que la mémoire tampon de sortie est Full, la commande commence à supprimer output.</span><span class="sxs-lookup"><span data-stu-id="b5b46-362">When the value of the **OutputBufferingMode** option of the session is Drop and the output buffer is full, the command starts to delete output.</span></span> <span data-ttu-id="b5b46-363">`Receive-PSSession` Impossible de récupérer cette sortie.</span><span class="sxs-lookup"><span data-stu-id="b5b46-363">`Receive-PSSession` can't recover this output.</span></span> <span data-ttu-id="b5b46-364">Pour plus d’informations sur l’option mode de mise en mémoire tampon de sortie, consultez les articles d’aide pour les applets de commande [New-PSSessionOption](New-PSSessionOption.md) et [New-PSTransportOption](New-PSTransportOption.md) .</span><span class="sxs-lookup"><span data-stu-id="b5b46-364">For more information about the output buffering mode option, see the help articles for the [New-PSSessionOption](New-PSSessionOption.md) and [New-PSTransportOption](New-PSTransportOption.md) cmdlets.</span></span>

<span data-ttu-id="b5b46-365">Vous ne pouvez pas modifier la valeur du délai d’inactivité d’une **session PSSession** quand vous vous connectez à la **session PSSession** ou recevez des résultats.</span><span class="sxs-lookup"><span data-stu-id="b5b46-365">You can't change the idle time-out value of a **PSSession** when you connect to the **PSSession** or receive results.</span></span> <span data-ttu-id="b5b46-366">Le paramètre **SessionOption** de `Receive-PSSession` prend un objet **SessionOption** qui a une valeur **IdleTimeout** .</span><span class="sxs-lookup"><span data-stu-id="b5b46-366">The **SessionOption** parameter of `Receive-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="b5b46-367">Toutefois, la valeur **IdleTimeout** de l’objet **SessionOption** et la valeur **IdleTimeout** de la `$PSSessionOption` variable sont ignorées lorsqu’il se connecte à une **session PSSession** ou reçoit des résultats.</span><span class="sxs-lookup"><span data-stu-id="b5b46-367">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when it connects to a **PSSession** or receiving results.</span></span>

- <span data-ttu-id="b5b46-368">Vous pouvez définir et modifier le délai d’inactivité d’une **session PSSession** quand vous créez la **session PSSession**, à l’aide des `New-PSSession` applets de commande ou `Invoke-Command` , et lorsque vous vous déconnectez de la **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="b5b46-368">You can set and change the idle time-out of a **PSSession** when you create the **PSSession**, by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>
- <span data-ttu-id="b5b46-369">La propriété **IdleTimeout** d’une session **PSSession** est critique pour les sessions déconnectées, car elle détermine la durée pendant laquelle une session déconnectée est conservée sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b5b46-369">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="b5b46-370">Une session déconnectée est considérée comme inactive dès qu'elle est déconnectée, même si elle comprend des commandes en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="b5b46-370">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="b5b46-371">Si vous démarrez un travail démarrer un travail dans une session à distance à l’aide du paramètre **AsJob** de l’applet de commande `Invoke-Command` , l’objet de traitement est créé dans la session active, même si la tâche est exécutée dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="b5b46-371">If you start a start a job in a remote session by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is created in the current session, even though the job runs in the remote session.</span></span> <span data-ttu-id="b5b46-372">Si vous déconnectez la session à distance, l’objet de traitement de la session active est déconnecté du travail.</span><span class="sxs-lookup"><span data-stu-id="b5b46-372">If you disconnect the remote session, the job object in the current session is disconnected from the job.</span></span> <span data-ttu-id="b5b46-373">L’objet de traitement contient tous les résultats qui lui ont été retournés, mais ne reçoit pas les nouveaux résultats de la tâche dans la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-373">The job object contains any results that were returned to it, but doesn't receive new results from the job in the disconnected session.</span></span>

<span data-ttu-id="b5b46-374">Si un autre client se connecte à la session qui contient le travail en cours d’exécution, les résultats qui ont été remis à l’objet de traitement d’origine dans la session d’origine ne sont pas disponibles dans la session qui vient d’être connectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-374">If a different client connects to the session that contains the running job, the results that were delivered to the original job object in the original session aren't available in the newly connected session.</span></span> <span data-ttu-id="b5b46-375">Seuls les résultats qui n'ont pas été remis à l'objet de traitement d'origine sont disponibles dans la session reconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-375">Only results that were not delivered to the original job object are available in the reconnected session.</span></span>

<span data-ttu-id="b5b46-376">De même, si vous démarrez un script dans une session, puis vous déconnectez de la session, les résultats que le script remet à la session avant la déconnexion ne sont pas disponibles pour un autre client qui se connecte à la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-376">Similarly, if you start a script in a session and then disconnect from the session, any results that the script delivers to the session before disconnecting aren't available to another client that connects to the session.</span></span>

<span data-ttu-id="b5b46-377">Pour éviter la perte de données dans les sessions que vous souhaitez déconnecter, utilisez le paramètre **InDisconnectedSession** de l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="b5b46-377">To prevent data loss in sessions that you intend to disconnect, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="b5b46-378">Comme ce paramètre empêche le renvoi des résultats à la session active, tous les résultats sont disponibles quand la session est reconnectée.</span><span class="sxs-lookup"><span data-stu-id="b5b46-378">Because this parameter prevents results from being returned to the current session, all results are available when the session is reconnected.</span></span>

<span data-ttu-id="b5b46-379">Vous pouvez également empêcher la perte de données à l’aide de l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="b5b46-379">You can also prevent data loss by using the `Invoke-Command` cmdlet to run a `Start-Job` command in the remote session.</span></span> <span data-ttu-id="b5b46-380">Dans ce cas, l'objet de traitement est créé dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="b5b46-380">In this case, the job object is created in the remote session.</span></span> <span data-ttu-id="b5b46-381">Vous ne pouvez pas utiliser l' `Receive-PSSession` applet de commande pour obtenir les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="b5b46-381">You can't use the `Receive-PSSession` cmdlet to get the job results.</span></span> <span data-ttu-id="b5b46-382">Utilisez plutôt l' `Connect-PSSession` applet de commande pour vous connecter à la session, puis utilisez l' `Invoke-Command` applet de commande pour exécuter une `Receive-Job` commande dans la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-382">Instead, use the `Connect-PSSession` cmdlet to connect to the session and then use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session.</span></span>

<span data-ttu-id="b5b46-383">Quand une session qui contient un travail en cours d’exécution est déconnectée puis reconnectée, l’objet de travail d’origine est réutilisé uniquement si le travail est déconnecté et reconnecté à la même session, et si la commande de reconnexion ne spécifie pas un nouveau nom de travail.</span><span class="sxs-lookup"><span data-stu-id="b5b46-383">When a session that contains a running job is disconnected and then reconnected, the original job object is reused only if the job is disconnected and reconnected to the same session, and the command to reconnect doesn't specify a new job name.</span></span> <span data-ttu-id="b5b46-384">Si la session est reconnectée à une autre session client ou si un nouveau nom de tâche est spécifié, PowerShell crée un nouvel objet de traitement pour la nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-384">If the session is reconnected to a different client session or a new job name is specified, PowerShell creates a new job object for the new session.</span></span>

<span data-ttu-id="b5b46-385">Lorsque vous déconnectez une session **PSSession**, l’état de session est disconnected et la disponibilité est None.</span><span class="sxs-lookup"><span data-stu-id="b5b46-385">When you disconnect a **PSSession**, the session state is Disconnected and the availability is None.</span></span>

- <span data-ttu-id="b5b46-386">La valeur de la propriété **State** dépend de la session active.</span><span class="sxs-lookup"><span data-stu-id="b5b46-386">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="b5b46-387">La valeur Disconnected signifie que la session **PSSession** n’est pas connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="b5b46-387">A value of Disconnected means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="b5b46-388">Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions.</span><span class="sxs-lookup"><span data-stu-id="b5b46-388">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="b5b46-389">Elle peut être connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-389">It might be connected to a different session.</span></span>
  <span data-ttu-id="b5b46-390">Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability**.</span><span class="sxs-lookup"><span data-stu-id="b5b46-390">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>
- <span data-ttu-id="b5b46-391">Une propriété **Availability** avec la valeur None signifie que vous pouvez vous connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-391">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="b5b46-392">La valeur Busy indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="b5b46-392">A value of Busy indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span>
- <span data-ttu-id="b5b46-393">Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="b5b46-393">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>
- <span data-ttu-id="b5b46-394">Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="b5b46-394">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="b5b46-395">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b5b46-395">RELATED LINKS</span></span>

[<span data-ttu-id="b5b46-396">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="b5b46-396">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="b5b46-397">about_Remote</span><span class="sxs-lookup"><span data-stu-id="b5b46-397">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="b5b46-398">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="b5b46-398">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="b5b46-399">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="b5b46-399">about_Session_Configurations</span></span>](./About/about_Session_Configurations.md)

[<span data-ttu-id="b5b46-400">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-400">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="b5b46-401">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-401">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="b5b46-402">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-402">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="b5b46-403">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-403">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="b5b46-404">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="b5b46-404">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="b5b46-405">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-405">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="b5b46-406">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="b5b46-406">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="b5b46-407">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="b5b46-407">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="b5b46-408">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="b5b46-408">Remove-PSSession</span></span>](Remove-PSSession.md)