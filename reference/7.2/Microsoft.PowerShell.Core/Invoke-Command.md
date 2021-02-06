---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: d8f0a8a56792a39371a307166788f047fec99a9a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603476"
---
# <span data-ttu-id="60ac0-102">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="60ac0-102">Invoke-Command</span></span>

## <span data-ttu-id="60ac0-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="60ac0-103">SYNOPSIS</span></span>
<span data-ttu-id="60ac0-104">Exécute des commandes sur des ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-104">Runs commands on local and remote computers.</span></span>

## <span data-ttu-id="60ac0-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="60ac0-105">SYNTAX</span></span>

### <span data-ttu-id="60ac0-106">InProcess (par défaut)</span><span class="sxs-lookup"><span data-stu-id="60ac0-106">InProcess (Default)</span></span>

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="60ac0-107">FilePathRunspace</span><span class="sxs-lookup"><span data-stu-id="60ac0-107">FilePathRunspace</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="60ac0-108">Session</span><span class="sxs-lookup"><span data-stu-id="60ac0-108">Session</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="60ac0-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="60ac0-109">FilePathComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="60ac0-110">ComputerName</span><span class="sxs-lookup"><span data-stu-id="60ac0-110">ComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="60ac0-111">Uri</span><span class="sxs-lookup"><span data-stu-id="60ac0-111">Uri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="60ac0-112">FilePathUri</span><span class="sxs-lookup"><span data-stu-id="60ac0-112">FilePathUri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="60ac0-113">VMId</span><span class="sxs-lookup"><span data-stu-id="60ac0-113">VMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="60ac0-114">VMName</span><span class="sxs-lookup"><span data-stu-id="60ac0-114">VMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="60ac0-115">FilePathVMId</span><span class="sxs-lookup"><span data-stu-id="60ac0-115">FilePathVMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="60ac0-116">FilePathVMName</span><span class="sxs-lookup"><span data-stu-id="60ac0-116">FilePathVMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="60ac0-117">SSHHost</span><span class="sxs-lookup"><span data-stu-id="60ac0-117">SSHHost</span></span>

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-Subsystem <String>] [<CommonParameters>]
```

### <span data-ttu-id="60ac0-118">ContainerId</span><span class="sxs-lookup"><span data-stu-id="60ac0-118">ContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="60ac0-119">FilePathContainerId</span><span class="sxs-lookup"><span data-stu-id="60ac0-119">FilePathContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="60ac0-120">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="60ac0-120">SSHHostHashParam</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] [-JobName <String>] [-ScriptBlock] <ScriptBlock>
 -SSHConnection <Hashtable[]> [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="60ac0-121">FilePathSSHHost</span><span class="sxs-lookup"><span data-stu-id="60ac0-121">FilePathSSHHost</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="60ac0-122">FilePathSSHHostHash</span><span class="sxs-lookup"><span data-stu-id="60ac0-122">FilePathSSHHostHash</span></span>

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="60ac0-123">Description</span><span class="sxs-lookup"><span data-stu-id="60ac0-123">DESCRIPTION</span></span>

<span data-ttu-id="60ac0-124">L' `Invoke-Command` applet de commande exécute des commandes sur un ordinateur local ou distant et retourne toutes les sorties des commandes, y compris les erreurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-124">The `Invoke-Command` cmdlet runs commands on a local or remote computer and returns all output from the commands, including errors.</span></span> <span data-ttu-id="60ac0-125">À l’aide d’une seule `Invoke-Command` commande, vous pouvez exécuter des commandes sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-125">Using a single `Invoke-Command` command, you can run commands on multiple computers.</span></span>

<span data-ttu-id="60ac0-126">Pour exécuter une seule commande sur un ordinateur distant, utilisez le paramètre **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-126">To run a single command on a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="60ac0-127">Pour exécuter une série de commandes associées qui partagent des données, utilisez l' `New-PSSession` applet de commande pour créer une session **PSSession** (une connexion permanente) sur l’ordinateur distant, puis utilisez le paramètre **session** de `Invoke-Command` pour exécuter la commande dans la session **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-127">To run a series of related commands that share data, use the `New-PSSession` cmdlet to create a **PSSession** (a persistent connection) on the remote computer, and then use the **Session** parameter of `Invoke-Command` to run the command in the **PSSession**.</span></span> <span data-ttu-id="60ac0-128">Pour exécuter une commande dans une session déconnectée, utilisez le paramètre **InDisconnectedSession**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-128">To run a command in a disconnected session, use the **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="60ac0-129">Pour exécuter une commande dans une tâche en arrière-plan, utilisez le paramètre **AsJob**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-129">To run a command in a background job, use the **AsJob** parameter.</span></span>

<span data-ttu-id="60ac0-130">Vous pouvez également utiliser `Invoke-Command` sur un ordinateur local en tant que commande dans un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-130">You can also use `Invoke-Command` on a local computer to a script block as a command.</span></span> <span data-ttu-id="60ac0-131">PowerShell exécute immédiatement le bloc de script dans une étendue enfant de l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="60ac0-131">PowerShell runs the script block immediately in a child scope of the current scope.</span></span>

<span data-ttu-id="60ac0-132">Avant `Invoke-Command` d’utiliser pour exécuter des commandes sur un ordinateur distant, lisez [about_Remote](./About/about_Remote.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-132">Before using `Invoke-Command` to run commands on a remote computer, read [about_Remote](./About/about_Remote.md).</span></span>

<span data-ttu-id="60ac0-133">À compter de PowerShell 6,0, vous pouvez utiliser Secure Shell (SSH) pour établir une connexion à et appeler des commandes sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-133">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and invoke commands on remote computers.</span></span> <span data-ttu-id="60ac0-134">SSH doit être installé sur l’ordinateur local et l’ordinateur distant doit être configuré avec un point de terminaison SSH PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60ac0-134">SSH must be installed on the local computer and the remote computer must be configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="60ac0-135">L’avantage d’une session à distance PowerShell basée sur SSH est qu’elle fonctionne sur plusieurs plateformes (Windows, Linux, macOS).</span><span class="sxs-lookup"><span data-stu-id="60ac0-135">The benefit of an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="60ac0-136">Pour une session SSH, utilisez les paramètres **hostname** ou **SSHConnection** pour spécifier l’ordinateur distant et les informations de connexion appropriées.</span><span class="sxs-lookup"><span data-stu-id="60ac0-136">For SSH based session you use the **HostName** or **SSHConnection** parameters to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="60ac0-137">Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="60ac0-137">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="60ac0-138">Certains exemples de code utilisent la projection pour réduire la longueur de la ligne.</span><span class="sxs-lookup"><span data-stu-id="60ac0-138">Some code samples use splatting to reduce the line length.</span></span> <span data-ttu-id="60ac0-139">Pour plus d’informations, consultez [about_Splatting](./About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-139">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="60ac0-140">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="60ac0-140">EXAMPLES</span></span>

### <span data-ttu-id="60ac0-141">Exemple 1 : exécuter un script sur un serveur</span><span class="sxs-lookup"><span data-stu-id="60ac0-141">Example 1: Run a script on a server</span></span>

<span data-ttu-id="60ac0-142">Cet exemple exécute le `Test.ps1` script sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="60ac0-142">This example runs the `Test.ps1` script on the Server01 computer.</span></span>

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

<span data-ttu-id="60ac0-143">Le paramètre **filePath** spécifie un script qui se trouve sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-143">The **FilePath** parameter specifies a script that is located on the local computer.</span></span> <span data-ttu-id="60ac0-144">Le script s'exécute sur l'ordinateur distant et les résultats sont retournés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-144">The script runs on the remote computer and the results are returned to the local computer.</span></span>

### <span data-ttu-id="60ac0-145">Exemple 2 : exécuter une commande sur un serveur distant</span><span class="sxs-lookup"><span data-stu-id="60ac0-145">Example 2: Run a command on a remote server</span></span>

<span data-ttu-id="60ac0-146">Cet exemple exécute une `Get-Culture` commande sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="60ac0-146">This example runs a `Get-Culture` command on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

<span data-ttu-id="60ac0-147">Le paramètre **ComputerName** spécifie le nom de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-147">The **ComputerName** parameter specifies the name of the remote computer.</span></span> <span data-ttu-id="60ac0-148">Le paramètre **Credential** est utilisé pour exécuter la commande dans le contexte de sécurité de Domaine01\Utilisateur01, un utilisateur qui a l’autorisation d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="60ac0-148">The **Credential** parameter is used to run the command in the security context of Domain01\User01, a user who has permission to run commands.</span></span> <span data-ttu-id="60ac0-149">Le paramètre **scriptblock** spécifie la commande à exécuter sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-149">The **ScriptBlock** parameter specifies the command to be run on the remote computer.</span></span>

<span data-ttu-id="60ac0-150">En réponse, PowerShell demande le mot de passe et une méthode d’authentification pour le compte User01.</span><span class="sxs-lookup"><span data-stu-id="60ac0-150">In response, PowerShell requests the password and an authentication method for the User01 account.</span></span>
<span data-ttu-id="60ac0-151">Ensuite, il exécute la commande sur l'ordinateur Server01 et retourne le résultat.</span><span class="sxs-lookup"><span data-stu-id="60ac0-151">It then runs the command on the Server01 computer and returns the result.</span></span>

### <span data-ttu-id="60ac0-152">Exemple 3 : exécuter une commande dans une connexion permanente</span><span class="sxs-lookup"><span data-stu-id="60ac0-152">Example 3: Run a command in a persistent connection</span></span>

<span data-ttu-id="60ac0-153">Cet exemple exécute la même `Get-Culture` commande dans une session, à l’aide d’une connexion persistante, sur l’ordinateur distant nommé Server02.</span><span class="sxs-lookup"><span data-stu-id="60ac0-153">This example runs the same `Get-Culture` command in a session, using a persistent connection, on the remote computer named Server02.</span></span>

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="60ac0-154">L' `New-PSSession` applet de commande crée une session sur l’ordinateur distant SERVER02 et l’enregistre dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-154">The `New-PSSession` cmdlet creates a session on the Server02 remote computer and saves it in the `$s` variable.</span></span> <span data-ttu-id="60ac0-155">En règle générale, vous créez une session uniquement lorsque vous exécutez une série de commandes sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-155">Typically, you create a session only when you run a series of commands on the remote computer.</span></span>

<span data-ttu-id="60ac0-156">L' `Invoke-Command` applet `Get-Culture` de commande exécute la commande sur Server02.</span><span class="sxs-lookup"><span data-stu-id="60ac0-156">The `Invoke-Command` cmdlet runs the `Get-Culture` command on Server02.</span></span> <span data-ttu-id="60ac0-157">Le paramètre **session** spécifie la session enregistrée dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-157">The **Session** parameter specifies the session saved in the `$s` variable.</span></span>

<span data-ttu-id="60ac0-158">En réponse, PowerShell exécute la commande dans la session sur l’ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="60ac0-158">In response, PowerShell runs the command in the session on the Server02 computer.</span></span>

### <span data-ttu-id="60ac0-159">Exemple 4 : utiliser une session pour exécuter une série de commandes qui partagent des données</span><span class="sxs-lookup"><span data-stu-id="60ac0-159">Example 4: Use a session to run a series of commands that share data</span></span>

<span data-ttu-id="60ac0-160">Cet exemple compare les effets de l’utilisation de **ComputerName** et des paramètres de **session** de `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-160">This example compares the effects of using **ComputerName** and **Session** parameters of `Invoke-Command`.</span></span> <span data-ttu-id="60ac0-161">Il montre comment utiliser une session pour exécuter une série de commandes qui partagent les mêmes données.</span><span class="sxs-lookup"><span data-stu-id="60ac0-161">It shows how to use a session to run a series of commands that share the same data.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

<span data-ttu-id="60ac0-162">Les deux premières commandes utilisent le paramètre **ComputerName** de `Invoke-Command` pour exécuter des commandes sur l’ordinateur distant SERVER02.</span><span class="sxs-lookup"><span data-stu-id="60ac0-162">The first two commands use the **ComputerName** parameter of `Invoke-Command` to run commands on the Server02 remote computer.</span></span> <span data-ttu-id="60ac0-163">La première commande utilise l' `Get-Process` applet de commande pour récupérer le processus PowerShell sur l’ordinateur distant et l’enregistrer dans la `$p` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-163">The first command uses the `Get-Process` cmdlet to get the PowerShell process on the remote computer and to save it in the `$p` variable.</span></span> <span data-ttu-id="60ac0-164">La deuxième commande obtient la valeur de la propriété **VirtualMemorySize** du processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60ac0-164">The second command gets the value of the **VirtualMemorySize** property of the PowerShell process.</span></span>

<span data-ttu-id="60ac0-165">Quand vous utilisez le paramètre **ComputerName** , PowerShell crée une nouvelle session pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-165">When you use the **ComputerName** parameter, PowerShell creates a new session to run the command.</span></span>
<span data-ttu-id="60ac0-166">La session est fermée à la fin de l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-166">The session is closed when the command completes.</span></span> <span data-ttu-id="60ac0-167">La `$p` variable a été créée dans une connexion, mais elle n’existe pas dans la connexion créée pour la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-167">The `$p` variable was created in one connection, but it doesn't exist in the connection created for the second command.</span></span>

<span data-ttu-id="60ac0-168">Le problème est résolu en créant une session persistante sur l’ordinateur distant, puis en exécutant les deux commandes de la même session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-168">The problem is solved by creating a persistent session on the remote computer, then running both of the commands in the same session.</span></span>

<span data-ttu-id="60ac0-169">L' `New-PSSession` applet de commande crée une session persistante sur l’ordinateur Server02 et enregistre la session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-169">The `New-PSSession` cmdlet creates a persistent session on the computer Server02 and saves the session in the `$s` variable.</span></span> <span data-ttu-id="60ac0-170">Les `Invoke-Command` lignes qui suivent utilisent le paramètre **session** pour exécuter les deux commandes de la même session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-170">The `Invoke-Command` lines that follow use the **Session** parameter to run both of the commands in the same session.</span></span> <span data-ttu-id="60ac0-171">Étant donné que les deux commandes s’exécutent dans la même session, la `$p` valeur reste active.</span><span class="sxs-lookup"><span data-stu-id="60ac0-171">Since both commands run in the same session, the `$p` value remains active.</span></span>

### <span data-ttu-id="60ac0-172">Exemple 5 : entrer une commande stockée dans une variable locale</span><span class="sxs-lookup"><span data-stu-id="60ac0-172">Example 5: Enter a command stored in a local variable</span></span>

<span data-ttu-id="60ac0-173">Cet exemple montre comment créer une commande stockée en tant que bloc de script dans une variable locale.</span><span class="sxs-lookup"><span data-stu-id="60ac0-173">This example shows how to create a command that is stored as a script block in a local variable.</span></span>
<span data-ttu-id="60ac0-174">Lorsque le bloc de script est enregistré dans une variable locale, vous pouvez spécifier la variable comme valeur du paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-174">When the script block is saved in a local variable, you can specify the variable as the value of the **ScriptBlock** parameter.</span></span>

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

<span data-ttu-id="60ac0-175">La `$command` variable stocke la `Get-WinEvent` commande mise en forme comme un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-175">The `$command` variable stores the `Get-WinEvent` command that's formatted as a script block.</span></span> <span data-ttu-id="60ac0-176">Le `Invoke-Command` exécute la commande stockée dans `$command` sur les ordinateurs distants S1 et S2.</span><span class="sxs-lookup"><span data-stu-id="60ac0-176">The `Invoke-Command` runs the command stored in `$command` on the S1 and S2 remote computers.</span></span>

### <span data-ttu-id="60ac0-177">Exemple 6 : exécuter une seule commande sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="60ac0-177">Example 6: Run a single command on several computers</span></span>

<span data-ttu-id="60ac0-178">Cet exemple montre comment utiliser `Invoke-Command` pour exécuter une seule commande sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-178">This example demonstrates how to use `Invoke-Command` to run a single command on multiple computers.</span></span>

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

<span data-ttu-id="60ac0-179">Le paramètre **ComputerName** spécifie une liste de noms d’ordinateurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="60ac0-179">The **ComputerName** parameter specifies a comma-separated list of computer names.</span></span> <span data-ttu-id="60ac0-180">La liste des ordinateurs comprend la valeur localhost, qui représente l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-180">The list of computers includes the localhost value, which represents the local computer.</span></span> <span data-ttu-id="60ac0-181">Le paramètre **ConfigurationName** spécifie une autre configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-181">The **ConfigurationName** parameter specifies an alternate session configuration.</span></span> <span data-ttu-id="60ac0-182">Le paramètre **scriptblock** s’exécute `Get-WinEvent` pour récupérer les journaux des événements PowerShellCore/Operations de chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-182">The **ScriptBlock** parameter runs `Get-WinEvent` to get the PowerShellCore/Operational event logs from each computer.</span></span>

### <span data-ttu-id="60ac0-183">Exemple 7 : récupération de la version du programme hôte sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="60ac0-183">Example 7: Get the version of the host program on multiple computers</span></span>

<span data-ttu-id="60ac0-184">Cet exemple obtient la version du programme hôte PowerShell en cours d’exécution sur les ordinateurs distants 200.</span><span class="sxs-lookup"><span data-stu-id="60ac0-184">This example gets the version of the PowerShell host program running on 200 remote computers.</span></span>

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

<span data-ttu-id="60ac0-185">Comme une seule commande est exécutée, vous n’êtes pas obligé de créer des connexions persistantes à chacun des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-185">Because only one command is run, you don't have to create persistent connections to each of the computers.</span></span> <span data-ttu-id="60ac0-186">À la place, la commande utilise le paramètre **ComputerName** pour indiquer les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-186">Instead, the command uses the **ComputerName** parameter to indicate the computers.</span></span> <span data-ttu-id="60ac0-187">Pour spécifier les ordinateurs, il utilise l' `Get-Content` applet de commande pour obtenir le contenu du fichier Machine.txt, un fichier de noms d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-187">To specify the computers, it uses the `Get-Content` cmdlet to get the contents of the Machine.txt file, a file of computer names.</span></span>

<span data-ttu-id="60ac0-188">L' `Invoke-Command` applet de commande exécute une `Get-Host` commande sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-188">The `Invoke-Command` cmdlet runs a `Get-Host` command on the remote computers.</span></span> <span data-ttu-id="60ac0-189">Elle utilise la notation par points pour récupérer la propriété de **version** de l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60ac0-189">It uses dot notation to get the **Version** property of the PowerShell host.</span></span>

<span data-ttu-id="60ac0-190">Ces commandes s’exécutent l’une après l’autre.</span><span class="sxs-lookup"><span data-stu-id="60ac0-190">These commands run one at a time.</span></span> <span data-ttu-id="60ac0-191">Lorsque les commandes sont terminées, la sortie des commandes de tous les ordinateurs est enregistrée dans la `$version` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-191">When the commands complete, the output of the commands from all of the computers is saved in the `$version` variable.</span></span> <span data-ttu-id="60ac0-192">La sortie inclut le nom de l'ordinateur d'où proviennent les données.</span><span class="sxs-lookup"><span data-stu-id="60ac0-192">The output includes the name of the computer from which the data originated.</span></span>

### <span data-ttu-id="60ac0-193">Exemple 8 : exécuter une tâche en arrière-plan sur plusieurs ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="60ac0-193">Example 8: Run a background job on several remote computers</span></span>

<span data-ttu-id="60ac0-194">Cet exemple exécute une commande sur deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-194">This example runs a command on two remote computers.</span></span> <span data-ttu-id="60ac0-195">La `Invoke-Command` commande utilise le paramètre **AsJob** afin que la commande s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="60ac0-195">The `Invoke-Command` command uses the **AsJob** parameter so that the command runs as a background job.</span></span> <span data-ttu-id="60ac0-196">Les commandes s’exécutent sur les ordinateurs distants, mais la tâche existe sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-196">The commands run on the remote computers, but the job exists on the local computer.</span></span> <span data-ttu-id="60ac0-197">Les résultats sont transmis à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-197">The results are transmitted to the local computer.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

<span data-ttu-id="60ac0-198">L' `New-PSSession` applet de commande crée des sessions sur les ordinateurs distants SERVEUR01 et Server02.</span><span class="sxs-lookup"><span data-stu-id="60ac0-198">The `New-PSSession` cmdlet creates sessions on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="60ac0-199">L' `Invoke-Command` applet de commande exécute une tâche en arrière-plan dans chacune des sessions.</span><span class="sxs-lookup"><span data-stu-id="60ac0-199">The `Invoke-Command` cmdlet runs a background job in each of the sessions.</span></span> <span data-ttu-id="60ac0-200">La commande utilise le paramètre **AsJob** pour exécuter la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="60ac0-200">The command uses the **AsJob** parameter to run the command as a background job.</span></span> <span data-ttu-id="60ac0-201">Cette commande retourne un objet de tâche qui contient deux objets de tâche enfants, un pour chacune des tâches exécutées sur les deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-201">This command returns a job object that contains two child job objects, one for each of the jobs run on the two remote computers.</span></span>

<span data-ttu-id="60ac0-202">La `Get-Job` commande enregistre l’objet de traitement dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-202">The `Get-Job` command saves the job object in the `$j` variable.</span></span> <span data-ttu-id="60ac0-203">La `$j` variable est ensuite redirigée vers l' `Format-List` applet de commande pour afficher toutes les propriétés de l’objet de traitement dans une liste.</span><span class="sxs-lookup"><span data-stu-id="60ac0-203">The `$j` variable is then piped to the `Format-List` cmdlet to display all properties of the job object in a list.</span></span> <span data-ttu-id="60ac0-204">La dernière commande obtient les résultats des tâches.</span><span class="sxs-lookup"><span data-stu-id="60ac0-204">The last command gets the results of the jobs.</span></span> <span data-ttu-id="60ac0-205">Elle dirige l’objet de traitement dans `$j` vers l’applet de commande `Receive-Job` et stocke les résultats dans la `$results` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-205">It pipes the job object in `$j` to the `Receive-Job` cmdlet and stores the results in the `$results` variable.</span></span>

### <span data-ttu-id="60ac0-206">Exemple 9 : inclure des variables locales dans une commande exécutée sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="60ac0-206">Example 9: Include local variables in a command run on a remote computer</span></span>

<span data-ttu-id="60ac0-207">Cet exemple montre comment inclure les valeurs des variables locales dans une commande exécutée sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-207">This example shows how to include the values of local variables in a command run on a remote computer.</span></span> <span data-ttu-id="60ac0-208">La commande utilise le `Using` modificateur de portée pour identifier une variable locale dans une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="60ac0-208">The command uses the `Using` scope modifier to identify a local variable in a remote command.</span></span> <span data-ttu-id="60ac0-209">Par défaut, toutes les variables sont supposées être définies dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="60ac0-209">By default, all variables are assumed to be defined in the remote session.</span></span> <span data-ttu-id="60ac0-210">Le `Using` modificateur de portée a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-210">The `Using` scope modifier was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="60ac0-211">Pour plus d’informations sur le `Using` modificateur d’étendue, consultez [about_Remote_Variables](./About/about_Remote_Variables.md) et [about_Scopes](./about/about_scopes.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-211">For more information about the `Using` scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md) and [about_Scopes](./about/about_scopes.md).</span></span>

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

<span data-ttu-id="60ac0-212">La `$Log` variable stocke le nom du journal des événements, PowerShellCore/Operational.</span><span class="sxs-lookup"><span data-stu-id="60ac0-212">The `$Log` variable stores the name of the event log, PowerShellCore/Operational.</span></span> <span data-ttu-id="60ac0-213">L' `Invoke-Command` applet de commande s’exécute `Get-WinEvent` sur SERVEUR01 pour recevoir les dix événements les plus récents du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="60ac0-213">The `Invoke-Command` cmdlet runs `Get-WinEvent` on Server01 to get the ten newest events from the event log.</span></span> <span data-ttu-id="60ac0-214">La valeur du paramètre **logname** est la `$Log` variable qui est préfixée par le `Using` modificateur de portée pour indiquer qu’elle a été créée dans la session locale, et non dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="60ac0-214">The value of the **LogName** parameter is the `$Log` variable that is prefixed by the `Using` scope modifier to indicate that it was created in the local session, not in the remote session.</span></span>

### <span data-ttu-id="60ac0-215">Exemple 10 : masquer le nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="60ac0-215">Example 10: Hide the computer name</span></span>

<span data-ttu-id="60ac0-216">Cet exemple montre l’effet de l’utilisation du paramètre **HideComputerName** de `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-216">This example shows the effect of using the **HideComputerName** parameter of `Invoke-Command`.</span></span>
<span data-ttu-id="60ac0-217">**HideComputerName** ne modifie pas l’objet retourné par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-217">**HideComputerName** doesn't change the object that this cmdlet returns.</span></span> <span data-ttu-id="60ac0-218">Il modifie uniquement l’affichage.</span><span class="sxs-lookup"><span data-stu-id="60ac0-218">It changes only the display.</span></span> <span data-ttu-id="60ac0-219">Vous pouvez toujours utiliser les applets de commande **format** pour afficher la propriété **PSComputerName** de l’un des objets affectés.</span><span class="sxs-lookup"><span data-stu-id="60ac0-219">You can still use the **Format** cmdlets to display the **PsComputerName** property of any of the affected objects.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

<span data-ttu-id="60ac0-220">Les deux premières commandes utilisent `Invoke-Command` pour exécuter une `Get-Process` commande pour le processus PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60ac0-220">The first two commands use `Invoke-Command` to run a `Get-Process` command for the PowerShell process.</span></span> <span data-ttu-id="60ac0-221">La sortie de la première commande inclut la propriété **PsComputerName**, qui contient le nom de l'ordinateur sur lequel la commande a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-221">The output of the first command includes the **PsComputerName** property, which contains the name of the computer on which the command ran.</span></span> <span data-ttu-id="60ac0-222">La sortie de la deuxième commande, qui utilise **HideComputerName**, n’inclut pas la colonne **PSComputerName** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-222">The output of the second command, which uses **HideComputerName**, doesn't include the **PsComputerName** column.</span></span>

### <span data-ttu-id="60ac0-223">Exemple 11 : utiliser le mot clé param dans un bloc de script</span><span class="sxs-lookup"><span data-stu-id="60ac0-223">Example 11: Use the Param keyword in a script block</span></span>

<span data-ttu-id="60ac0-224">Le `Param` mot clé et le paramètre **argumentlist** sont utilisés pour passer des valeurs de variable à des paramètres nommés dans un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-224">The `Param` keyword and the **ArgumentList** parameter are used to pass variable values to named parameters in a script block.</span></span> <span data-ttu-id="60ac0-225">Cet exemple affiche les noms de fichiers qui commencent par la lettre `a` et ont l' `.pdf` extension.</span><span class="sxs-lookup"><span data-stu-id="60ac0-225">This example displays filenames that begin with the letter `a` and have the `.pdf` extension.</span></span>

<span data-ttu-id="60ac0-226">Pour plus d’informations sur le `Param` mot clé, consultez [about_Language_Keywords](./about/about_language_keywords.md#param).</span><span class="sxs-lookup"><span data-stu-id="60ac0-226">For more information about the `Param` keyword, see [about_Language_Keywords](./about/about_language_keywords.md#param).</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

<span data-ttu-id="60ac0-227">`Invoke-Command` utilise le paramètre **scriptblock** qui définit deux variables, `$param1` et `$param2` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-227">`Invoke-Command` uses the **ScriptBlock** parameter that defines two variables, `$param1` and `$param2`.</span></span> <span data-ttu-id="60ac0-228">`Get-ChildItem` utilise les paramètres nommés, **Name** et **include** avec les noms de variables.</span><span class="sxs-lookup"><span data-stu-id="60ac0-228">`Get-ChildItem` uses the named parameters, **Name** and **Include** with the variable names.</span></span> <span data-ttu-id="60ac0-229">Le **argumentlist** transmet les valeurs aux variables.</span><span class="sxs-lookup"><span data-stu-id="60ac0-229">The **ArgumentList** passes the values to the variables.</span></span>

### <span data-ttu-id="60ac0-230">Exemple 12 : utiliser la variable automatique $args dans un bloc de script</span><span class="sxs-lookup"><span data-stu-id="60ac0-230">Example 12: Use the $args automatic variable in a script block</span></span>

<span data-ttu-id="60ac0-231">La `$args` variable automatique et le paramètre **argumentlist** sont utilisés pour passer des valeurs de tableau aux positions de paramètre dans un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-231">The `$args` automatic variable and the **ArgumentList** parameter are used to pass array values to parameter positions in a script block.</span></span> <span data-ttu-id="60ac0-232">Cet exemple affiche le contenu du répertoire d’un serveur de `.txt` fichiers.</span><span class="sxs-lookup"><span data-stu-id="60ac0-232">This example displays a server's directory contents of `.txt` files.</span></span> <span data-ttu-id="60ac0-233">Le `Get-ChildItem` paramètre **path** a la position 0 et le paramètre **Filter** est position</span><span class="sxs-lookup"><span data-stu-id="60ac0-233">The `Get-ChildItem` **Path** parameter is position 0 and the **Filter** parameter is position</span></span>
1.

<span data-ttu-id="60ac0-234">Pour plus d’informations sur la `$args` variable, consultez [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span><span class="sxs-lookup"><span data-stu-id="60ac0-234">For more information about the `$args` variable, see [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

<span data-ttu-id="60ac0-235">`Invoke-Command` utilise un paramètre **scriptblock** et `Get-ChildItem` spécifie `$args[0]` les `$args[1]` valeurs de tableau et.</span><span class="sxs-lookup"><span data-stu-id="60ac0-235">`Invoke-Command` uses a **ScriptBlock** parameter and `Get-ChildItem` specifies the `$args[0]` and `$args[1]` array values.</span></span> <span data-ttu-id="60ac0-236">Le **argumentlist** passe les `$args` valeurs de tableau aux `Get-ChildItem` positions de paramètre pour le **chemin d’accès** et le **filtre**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-236">The **ArgumentList** passes the `$args` array values to the `Get-ChildItem` parameter positions for **Path** and **Filter**.</span></span>

### <span data-ttu-id="60ac0-237">Exemple 13 : exécuter un script sur tous les ordinateurs listés dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="60ac0-237">Example 13: Run a script on all the computers listed in a text file</span></span>

<span data-ttu-id="60ac0-238">Cet exemple utilise l' `Invoke-Command` applet de commande pour exécuter le `Sample.ps1` script sur tous les ordinateurs figurant dans le `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="60ac0-238">This example uses the `Invoke-Command` cmdlet to run the `Sample.ps1` script on all the computers listed in the `Servers.txt` file.</span></span> <span data-ttu-id="60ac0-239">La commande utilise le paramètre **FilePath** pour spécifier le fichier de script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-239">The command uses the **FilePath** parameter to specify the script file.</span></span> <span data-ttu-id="60ac0-240">Cette commande vous permet d’exécuter le script sur les ordinateurs distants, même si le fichier de script n’est pas accessible aux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-240">This command lets you run the script on the remote computers, even if the script file isn't accessible to the remote computers.</span></span>

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

<span data-ttu-id="60ac0-241">Lorsque vous envoyez la commande, le contenu du `Sample.ps1` fichier est copié dans un bloc de script et le bloc de script est exécuté sur chacun des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-241">When you submit the command, the content of the `Sample.ps1` file is copied into a script block and the script block is run on each of the remote computers.</span></span> <span data-ttu-id="60ac0-242">Cette procédure est équivalente à l'utilisation du paramètre **ScriptBlock** pour envoyer le contenu du script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-242">This procedure is equivalent to using the **ScriptBlock** parameter to submit the contents of the script.</span></span>

### <span data-ttu-id="60ac0-243">Exemple 14 : exécuter une commande sur un ordinateur distant à l’aide d’un URI</span><span class="sxs-lookup"><span data-stu-id="60ac0-243">Example 14: Run a command on a remote computer using a URI</span></span>

<span data-ttu-id="60ac0-244">Cet exemple montre comment exécuter une commande sur un ordinateur distant identifié par un Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="60ac0-244">This example shows how to run a command on a remote computer that's identified by a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="60ac0-245">Cet exemple particulier exécute une `Set-Mailbox` commande sur un serveur Exchange distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-245">This particular example runs a `Set-Mailbox` command on a remote Exchange server.</span></span>

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

<span data-ttu-id="60ac0-246">La première ligne utilise l' `Get-Credential` applet de commande pour stocker les informations d’identification Windows Live ID dans la `$LiveCred` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-246">The first line uses the `Get-Credential` cmdlet to store Windows Live ID credentials in the `$LiveCred` variable.</span></span> <span data-ttu-id="60ac0-247">PowerShell invite l’utilisateur à entrer des informations d’identification Windows Live ID.</span><span class="sxs-lookup"><span data-stu-id="60ac0-247">PowerShell prompts the user to enter Windows Live ID credentials.</span></span>

<span data-ttu-id="60ac0-248">La `$parameters` variable est une table de hachage contenant les paramètres à passer à l' `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-248">The `$parameters` variable is a hash table containing the parameters to be passed to the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="60ac0-249">L' `Invoke-Command` applet de commande exécute une `Set-Mailbox` commande à l’aide de la configuration de session **Microsoft. Exchange** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-249">The `Invoke-Command` cmdlet runs a `Set-Mailbox` command using the **Microsoft.Exchange** session configuration.</span></span> <span data-ttu-id="60ac0-250">Le paramètre **ConnectionURI** spécifie l'URL du point de terminaison de serveur Exchange.</span><span class="sxs-lookup"><span data-stu-id="60ac0-250">The **ConnectionURI** parameter specifies the URL of the Exchange server endpoint.</span></span> <span data-ttu-id="60ac0-251">Le paramètre **Credential** spécifie les informations d’identification stockées dans la `$LiveCred` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-251">The **Credential** parameter specifies the credentials stored in the `$LiveCred` variable.</span></span> <span data-ttu-id="60ac0-252">Le paramètre **AuthenticationMechanism** spécifie l'utilisation de l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="60ac0-252">The **AuthenticationMechanism** parameter specifies the use of basic authentication.</span></span> <span data-ttu-id="60ac0-253">Le paramètre **ScriptBlock** spécifie un bloc de script qui contient la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-253">The **ScriptBlock** parameter specifies a script block that contains the command.</span></span>

### <span data-ttu-id="60ac0-254">Exemple 15 : utiliser une option de session</span><span class="sxs-lookup"><span data-stu-id="60ac0-254">Example 15: Use a session option</span></span>

<span data-ttu-id="60ac0-255">Cet exemple montre comment créer et utiliser un paramètre **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-255">This example shows how to create and use a **SessionOption** parameter.</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

<span data-ttu-id="60ac0-256">L' `New-PSSessionOption` applet de commande crée un objet d’option de session qui oblige l’extrémité distante à ne pas vérifier l’autorité de certification, le nom canonique et les listes de révocation lors de l’évaluation de la connexion HTTPS entrante.</span><span class="sxs-lookup"><span data-stu-id="60ac0-256">The `New-PSSessionOption` cmdlet creates a session option object that causes the remote end not to verify the Certificate Authority, Canonical Name, and Revocation Lists while evaluating the incoming HTTPS connection.</span></span> <span data-ttu-id="60ac0-257">L’objet **SessionOption** est enregistré dans la `$so` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-257">The **SessionOption** object is saved in the `$so` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="60ac0-258">La désactivation de ces contrôles est pratique pour la résolution des problèmes, mais évidemment non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-258">Disabling these checks is convenient for troubleshooting, but obviously not secure.</span></span>

<span data-ttu-id="60ac0-259">L' `Invoke-Command` applet de commande exécute une `Get-HotFix` commande à distance.</span><span class="sxs-lookup"><span data-stu-id="60ac0-259">The `Invoke-Command` cmdlet runs a `Get-HotFix` command remotely.</span></span> <span data-ttu-id="60ac0-260">La variable est attribuée au paramètre **SessionOption** `$so` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-260">The **SessionOption** parameter is given the `$so` variable.</span></span>

### <span data-ttu-id="60ac0-261">Exemple 16 : gérer la redirection d’URI dans une commande distante</span><span class="sxs-lookup"><span data-stu-id="60ac0-261">Example 16: Manage URI redirection in a remote command</span></span>

<span data-ttu-id="60ac0-262">Cet exemple montre comment utiliser les paramètres **AllowRedirection** et **SessionOption** pour gérer la redirection d’URI dans une commande distante.</span><span class="sxs-lookup"><span data-stu-id="60ac0-262">This example shows how to use the **AllowRedirection** and **SessionOption** parameters to manage URI redirection in a remote command.</span></span>

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

<span data-ttu-id="60ac0-263">L' `New-PSSessionOption` applet de commande crée un objet **PSSessionOption** qui est enregistré dans la `$max` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-263">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object that is saved in the `$max` variable.</span></span> <span data-ttu-id="60ac0-264">La commande utilise le paramètre **MaximumRedirection** pour définir la propriété **MaximumConnectionRedirectionCount** de l'objet **PSSessionOption** sur 1.</span><span class="sxs-lookup"><span data-stu-id="60ac0-264">The command uses the **MaximumRedirection** parameter to set the **MaximumConnectionRedirectionCount** property of the **PSSessionOption** object to 1.</span></span>

<span data-ttu-id="60ac0-265">L' `Invoke-Command` applet de commande exécute une `Get-Mailbox` commande sur un serveur Microsoft Exchange distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-265">The `Invoke-Command` cmdlet runs a `Get-Mailbox` command on a remote Microsoft Exchange Server.</span></span> <span data-ttu-id="60ac0-266">Le paramètre **AllowRedirection** fournit une autorisation explicite pour rediriger la connexion vers un autre point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="60ac0-266">The **AllowRedirection** parameter provides explicit permission to redirect the connection to an alternate endpoint.</span></span> <span data-ttu-id="60ac0-267">Le paramètre **SessionOption** utilise l’objet de session stocké dans la `$max` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-267">The **SessionOption** parameter uses the session object stored in the `$max` variable.</span></span>

<span data-ttu-id="60ac0-268">Par conséquent, si l’ordinateur distant spécifié par **ConnectionUri** retourne un message de redirection, PowerShell redirige la connexion, mais si la nouvelle destination retourne un autre message de redirection, la valeur du nombre de redirections de 1 est dépassée et `Invoke-Command` retourne une erreur sans fin d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="60ac0-268">As a result, if the remote computer specified by **ConnectionURI** returns a redirection message, PowerShell redirects the connection, but if the new destination returns another redirection message, the redirection count value of 1 is exceeded, and `Invoke-Command` returns a non-terminating error.</span></span>

### <span data-ttu-id="60ac0-269">Exemple 17 : accéder à un partage réseau dans une session à distance</span><span class="sxs-lookup"><span data-stu-id="60ac0-269">Example 17: Access a network share in a remote session</span></span>

<span data-ttu-id="60ac0-270">Cet exemple montre comment accéder à un partage réseau à partir d’une session à distance.</span><span class="sxs-lookup"><span data-stu-id="60ac0-270">This example shows how to access a network share from a remote session.</span></span> <span data-ttu-id="60ac0-271">Trois ordinateurs sont utilisés pour illustrer l’exemple.</span><span class="sxs-lookup"><span data-stu-id="60ac0-271">Three computers are used to demonstrate the example.</span></span> <span data-ttu-id="60ac0-272">SERVEUR01 est l’ordinateur local, Server02 est l’ordinateur distant et Net03 contient le partage réseau.</span><span class="sxs-lookup"><span data-stu-id="60ac0-272">Server01 is the local computer, Server02 is the remote computer, and Net03 contains the network share.</span></span> <span data-ttu-id="60ac0-273">SERVEUR01 se connecte à Server02, puis Server02 effectue un deuxième tronçon vers Net03 pour accéder au partage réseau.</span><span class="sxs-lookup"><span data-stu-id="60ac0-273">Server01 connects to Server02, and then Server02 does a second hop to Net03 to access the network share.</span></span> <span data-ttu-id="60ac0-274">Pour plus d’informations sur la façon dont la communication à distance PowerShell prend en charge les tronçons entre ordinateurs, consultez [création du deuxième tronçon dans la communication à distance PowerShell](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span><span class="sxs-lookup"><span data-stu-id="60ac0-274">For more information about how PowerShell Remoting supports hops between computers, see [Making the second hop in PowerShell Remoting](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span></span>

<span data-ttu-id="60ac0-275">La délégation CredSSP (Credential Security Support Provider) requise est activée dans les paramètres du client sur l’ordinateur local et dans les paramètres de service sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-275">The required Credential Security Support Provider (CredSSP) delegation is enabled in the client settings on the local computer, and in the service settings on the remote computer.</span></span> <span data-ttu-id="60ac0-276">Pour exécuter les commandes dans cet exemple, vous devez être membre du groupe **administrateurs** sur l’ordinateur local et l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-276">To run the commands in this example, you must be a member of the **Administrators** group on the local computer and the remote computer.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

<span data-ttu-id="60ac0-277">L' `Enable-WSManCredSSP` applet de commande active la délégation CredSSP à partir de l’ordinateur local SERVEUR01 sur l’ordinateur distant SERVER02.</span><span class="sxs-lookup"><span data-stu-id="60ac0-277">The `Enable-WSManCredSSP` cmdlet enables CredSSP delegation from the Server01 local computer to the Server02 remote computer.</span></span> <span data-ttu-id="60ac0-278">Le paramètre **role** spécifie au **client** de configurer le paramètre client CredSSP sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-278">The **Role** parameter specifies **Client** to configure the CredSSP client setting on the local computer.</span></span>

<span data-ttu-id="60ac0-279">`New-PSSession` crée un objet **PSSession** pour Server02 et stocke l’objet dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-279">`New-PSSession` creates a **PSSession** object for Server02 and stores the object in the `$s` variable.</span></span>

<span data-ttu-id="60ac0-280">L' `Invoke-Command` applet `$s` de commande utilise la variable pour se connecter à l’ordinateur distant, Server02.</span><span class="sxs-lookup"><span data-stu-id="60ac0-280">The `Invoke-Command` cmdlet uses the `$s` variable to connect to the remote computer, Server02.</span></span> <span data-ttu-id="60ac0-281">Le paramètre **scriptblock** s’exécute `Enable-WSManCredSSP` sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-281">The **ScriptBlock** parameter runs `Enable-WSManCredSSP` on the remote computer.</span></span> <span data-ttu-id="60ac0-282">Le paramètre **role** spécifie le **serveur** pour configurer le paramètre de serveur CredSSP sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-282">The **Role** parameter specifies **Server** to configure the CredSSP server setting on the remote computer.</span></span>

<span data-ttu-id="60ac0-283">La `$parameters` variable contient les valeurs des paramètres pour se connecter au partage réseau.</span><span class="sxs-lookup"><span data-stu-id="60ac0-283">The `$parameters` variable contains the parameter values to connect to the network share.</span></span> <span data-ttu-id="60ac0-284">L' `Invoke-Command` applet de commande exécute une `Get-Item` commande dans la session dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-284">The `Invoke-Command` cmdlet runs a `Get-Item` command in the session in `$s`.</span></span> <span data-ttu-id="60ac0-285">Cette commande obtient un script à partir du `\\Net03\Scripts` partage réseau.</span><span class="sxs-lookup"><span data-stu-id="60ac0-285">This command gets a script from the `\\Net03\Scripts` network share.</span></span> <span data-ttu-id="60ac0-286">La commande utilise le paramètre **Authentication** avec la valeur **CredSSP** et le paramètre **Credential** avec la valeur **domain01\admin01**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-286">The command uses the **Authentication** parameter with a value of **CredSSP** and the **Credential** parameter with a value of **Domain01\Admin01**.</span></span>

### <span data-ttu-id="60ac0-287">Exemple 18 : démarrer des scripts sur de nombreux ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="60ac0-287">Example 18: Start scripts on many remote computers</span></span>

<span data-ttu-id="60ac0-288">Cet exemple exécute un script sur plus de cent ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-288">This example runs a script on more than a hundred computers.</span></span> <span data-ttu-id="60ac0-289">Pour réduire au minimum l'impact sur l'ordinateur local, elle se connecte à chaque ordinateur, lance le script, puis se déconnecte de chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-289">To minimize the impact on the local computer, it connects to each computer, starts the script, and then disconnects from each computer.</span></span>
<span data-ttu-id="60ac0-290">Le script continue de s'exécuter dans les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="60ac0-290">The script continues to run in the disconnected sessions.</span></span>

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

<span data-ttu-id="60ac0-291">La commande utilise `Invoke-Command` pour exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-291">The command uses `Invoke-Command` to run the script.</span></span> <span data-ttu-id="60ac0-292">La valeur du paramètre **ComputerName** est une `Get-Content` commande qui obtient les noms des ordinateurs distants à partir d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="60ac0-292">The value of the **ComputerName** parameter is a `Get-Content` command that gets the names of the remote computers from a text file.</span></span> <span data-ttu-id="60ac0-293">Le paramètre **InDisconnectedSession** déconnecte les sessions dès qu'il démarre la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-293">The **InDisconnectedSession** parameter disconnects the sessions as soon as it starts the command.</span></span> <span data-ttu-id="60ac0-294">La valeur du paramètre **filePath** est le script qui `Invoke-Command` s’exécute sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-294">The value of the **FilePath** parameter is the script that `Invoke-Command` runs on each computer.</span></span>

<span data-ttu-id="60ac0-295">La valeur de **SessionOption** est une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="60ac0-295">The value of **SessionOption** is a hash table.</span></span> <span data-ttu-id="60ac0-296">La valeur **OutputBufferingMode** est définie sur **Drop** et la valeur **IdleTimeout** est définie sur **43,2 millions** millisecondes (12 heures).</span><span class="sxs-lookup"><span data-stu-id="60ac0-296">The **OutputBufferingMode** value is set to **Drop** and the **IdleTimeout** value is set to **43200000** milliseconds (12 hours).</span></span>

<span data-ttu-id="60ac0-297">Pour obtenir les résultats des commandes et des scripts qui s’exécutent dans les sessions déconnectées, utilisez l’applet de commande `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-297">To get the results of commands and scripts that run in disconnected sessions, use the `Receive-PSSession` cmdlet.</span></span>

### <span data-ttu-id="60ac0-298">Exemple 19 : exécuter une commande sur un ordinateur distant à l’aide de SSH</span><span class="sxs-lookup"><span data-stu-id="60ac0-298">Example 19: Run a command on a remote computer using SSH</span></span>

<span data-ttu-id="60ac0-299">Cet exemple montre comment exécuter une commande sur un ordinateur distant à l’aide d’Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="60ac0-299">This example shows how to run a command on a remote computer using Secure Shell (SSH).</span></span> <span data-ttu-id="60ac0-300">Si SSH est configuré sur l’ordinateur distant pour demander des mots de passe, vous obtenez une invite de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="60ac0-300">If SSH is configured on the remote computer to prompt for passwords, then you'll get a password prompt.</span></span>
<span data-ttu-id="60ac0-301">Dans le cas contraire, vous devrez utiliser l’authentification utilisateur basée sur les clés SSH.</span><span class="sxs-lookup"><span data-stu-id="60ac0-301">Otherwise, you'll have to use SSH key-based user authentication.</span></span>

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### <span data-ttu-id="60ac0-302">Exemple 20 : exécuter une commande sur un ordinateur distant à l’aide de SSH et spécifier une clé d’authentification utilisateur</span><span class="sxs-lookup"><span data-stu-id="60ac0-302">Example 20: Run a command on a remote computer using SSH and specify a user authentication key</span></span>

<span data-ttu-id="60ac0-303">Cet exemple montre comment exécuter une commande sur un ordinateur distant à l’aide de SSH et spécifier un fichier de clé pour l’authentification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-303">This example shows how to run a command on a remote computer using SSH and specifying a key file for user authentication.</span></span> <span data-ttu-id="60ac0-304">Vous ne serez pas invité à entrer un mot de passe, sauf si l’authentification par clé échoue et que l’ordinateur distant est configuré pour autoriser l’authentification de mot de passe de base.</span><span class="sxs-lookup"><span data-stu-id="60ac0-304">You won't be prompted for a password unless the key authentication fails and the remote computer is configured to allow basic password authentication.</span></span>

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### <span data-ttu-id="60ac0-305">Exemple 21 : exécuter un fichier de script sur plusieurs ordinateurs distants à l’aide de SSH en tant que tâche</span><span class="sxs-lookup"><span data-stu-id="60ac0-305">Example 21: Run a script file on multiple remote computers using SSH as a job</span></span>

<span data-ttu-id="60ac0-306">Cet exemple montre comment exécuter un fichier de script sur plusieurs ordinateurs distants à l’aide de SSH et du jeu de paramètres **SSHConnection** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-306">This example shows how to run a script file on multiple remote computers using SSH and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="60ac0-307">Le paramètre **SSHConnection** prend un tableau de tables de hachage qui contiennent des informations de connexion pour chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-307">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each computer.</span></span> <span data-ttu-id="60ac0-308">Cet exemple exige que le protocole SSH soit configuré sur les ordinateurs distants cibles pour prendre en charge l’authentification des utilisateurs basée sur les clés.</span><span class="sxs-lookup"><span data-stu-id="60ac0-308">This example requires that the target remote computers have SSH configured to support key-based user authentication.</span></span>

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## <span data-ttu-id="60ac0-309">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="60ac0-309">PARAMETERS</span></span>

### <span data-ttu-id="60ac0-310">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="60ac0-310">-AllowRedirection</span></span>

<span data-ttu-id="60ac0-311">Autorise la redirection de cette connexion vers un autre URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="60ac0-311">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="60ac0-312">Quand vous utilisez le paramètre **ConnectionURI**, la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="60ac0-312">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="60ac0-313">Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.</span><span class="sxs-lookup"><span data-stu-id="60ac0-313">By default, PowerShell doesn't redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="60ac0-314">Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-314">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="60ac0-315">Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="60ac0-315">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="60ac0-316">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="60ac0-316">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-317">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="60ac0-317">-ApplicationName</span></span>

<span data-ttu-id="60ac0-318">Spécifie le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="60ac0-318">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="60ac0-319">Utilisez ce paramètre pour spécifier le nom de l’application lorsque vous n’utilisez pas le paramètre **ConnectionUri** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-319">Use this parameter to specify the application name when you aren't using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="60ac0-320">La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-320">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="60ac0-321">Si cette variable de préférence n’est pas définie, la valeur par défaut est WSMAN.</span><span class="sxs-lookup"><span data-stu-id="60ac0-321">If this preference variable isn't defined, the default value is WSMAN.</span></span> <span data-ttu-id="60ac0-322">Cette valeur convient pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="60ac0-322">This value is appropriate for most uses.</span></span> <span data-ttu-id="60ac0-323">Pour plus d’informations, consultez [about_Preference_Variables](./About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-323">For more information, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="60ac0-324">Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="60ac0-324">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="60ac0-325">La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-325">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-326">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="60ac0-326">-ArgumentList</span></span>

<span data-ttu-id="60ac0-327">Fournit les valeurs des variables locales dans la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-327">Supplies the values of local variables in the command.</span></span> <span data-ttu-id="60ac0-328">Les variables dans la commande sont remplacées par ces valeurs avant l'exécution de la commande sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-328">The variables in the command are replaced by these values before the command is run on the remote computer.</span></span> <span data-ttu-id="60ac0-329">Entrez les valeurs dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="60ac0-329">Enter the values in a comma-separated list.</span></span> <span data-ttu-id="60ac0-330">Les valeurs sont associées à des variables dans l’ordre dans lequel elles sont répertoriées.</span><span class="sxs-lookup"><span data-stu-id="60ac0-330">Values are associated with variables in the order that they're listed.</span></span> <span data-ttu-id="60ac0-331">L’alias pour **argumentlist** est args.</span><span class="sxs-lookup"><span data-stu-id="60ac0-331">The alias for **ArgumentList** is Args.</span></span>

<span data-ttu-id="60ac0-332">Les valeurs du paramètre **argumentlist** peuvent être des valeurs réelles, telles que 1024, ou elles peuvent être des références à des variables locales, telles que `$max` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-332">The values in the **ArgumentList** parameter can be actual values, such as 1024, or they can be references to local variables, such as `$max`.</span></span>

<span data-ttu-id="60ac0-333">Pour utiliser des variables locales dans une commande, utilisez le format de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="60ac0-333">To use local variables in a command, use the following command format:</span></span>

<span data-ttu-id="60ac0-334">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` ou `<local-variable>`</span><span class="sxs-lookup"><span data-stu-id="60ac0-334">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`</span></span>

<span data-ttu-id="60ac0-335">Le mot clé **param** répertorie les variables locales utilisées dans la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-335">The **param** keyword lists the local variables that are used in the command.</span></span> <span data-ttu-id="60ac0-336">**Argumentlist** fournit les valeurs des variables, dans l’ordre dans lequel elles sont listées.</span><span class="sxs-lookup"><span data-stu-id="60ac0-336">**ArgumentList** supplies the values of the variables, in the order that they're listed.</span></span> <span data-ttu-id="60ac0-337">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="60ac0-337">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-338">-AsJob</span><span class="sxs-lookup"><span data-stu-id="60ac0-338">-AsJob</span></span>

<span data-ttu-id="60ac0-339">Indique que cette applet de commande exécute la commande en tant que tâche en arrière-plan sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-339">Indicates that this cmdlet runs the command as a background job on a remote computer.</span></span> <span data-ttu-id="60ac0-340">Utilisez ce paramètre pour exécuter des commandes qui prennent beaucoup de temps pour se terminer.</span><span class="sxs-lookup"><span data-stu-id="60ac0-340">Use this parameter to run commands that take an extensive time to finish.</span></span>

<span data-ttu-id="60ac0-341">Quand vous utilisez le paramètre **AsJob** , la commande retourne un objet qui représente le travail, puis affiche l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="60ac0-341">When you use the **AsJob** parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span> <span data-ttu-id="60ac0-342">Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="60ac0-342">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="60ac0-343">Pour gérer le travail, utilisez les `*-Job` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-343">To manage the job, use the `*-Job` cmdlets.</span></span> <span data-ttu-id="60ac0-344">Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="60ac0-344">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="60ac0-345">Le paramètre **AsJob** ressemble à l’utilisation de l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` applet de commande à distance.</span><span class="sxs-lookup"><span data-stu-id="60ac0-345">The **AsJob** parameter resembles using the `Invoke-Command` cmdlet to run a `Start-Job` cmdlet remotely.</span></span> <span data-ttu-id="60ac0-346">Toutefois, avec **AsJob**, la tâche est créée sur l’ordinateur local, même si le travail s’exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-346">However, with **AsJob**, the job is created on the local computer, even though the job runs on a remote computer.</span></span> <span data-ttu-id="60ac0-347">Les résultats de la tâche à distance sont automatiquement retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-347">The results of the remote job are automatically returned to the local computer.</span></span>

<span data-ttu-id="60ac0-348">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](About/about_Jobs.md) et [about_Remote_Jobs](About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-348">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-349">-Authentification</span><span class="sxs-lookup"><span data-stu-id="60ac0-349">-Authentication</span></span>

<span data-ttu-id="60ac0-350">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-350">Specifies the mechanism that's used to authenticate the user's credentials.</span></span> <span data-ttu-id="60ac0-351">L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="60ac0-351">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="60ac0-352">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="60ac0-352">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="60ac0-353">Default</span><span class="sxs-lookup"><span data-stu-id="60ac0-353">Default</span></span>
- <span data-ttu-id="60ac0-354">Basic</span><span class="sxs-lookup"><span data-stu-id="60ac0-354">Basic</span></span>
- <span data-ttu-id="60ac0-355">CredSSP</span><span class="sxs-lookup"><span data-stu-id="60ac0-355">Credssp</span></span>
- <span data-ttu-id="60ac0-356">Digest</span><span class="sxs-lookup"><span data-stu-id="60ac0-356">Digest</span></span>
- <span data-ttu-id="60ac0-357">Kerberos</span><span class="sxs-lookup"><span data-stu-id="60ac0-357">Kerberos</span></span>
- <span data-ttu-id="60ac0-358">Negotiate</span><span class="sxs-lookup"><span data-stu-id="60ac0-358">Negotiate</span></span>
- <span data-ttu-id="60ac0-359">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="60ac0-359">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="60ac0-360">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="60ac0-360">The default value is Default.</span></span>

<span data-ttu-id="60ac0-361">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="60ac0-361">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="60ac0-362">l'authentification CredSSP (Credential Security Support Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui nécessitent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-362">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="60ac0-363">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="60ac0-363">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="60ac0-364">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="60ac0-364">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span> <span data-ttu-id="60ac0-365">Pour plus d’informations, consultez [informations d’identification Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span><span class="sxs-lookup"><span data-stu-id="60ac0-365">For more information, see [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:
Accepted values: Basic, Default, Credssp, Digest, Kerberos, Negotiate, NegotiateWithImplicitCredential

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-366">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="60ac0-366">-CertificateThumbprint</span></span>

<span data-ttu-id="60ac0-367">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation de se connecter à la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-367">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="60ac0-368">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="60ac0-368">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="60ac0-369">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="60ac0-369">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="60ac0-370">Ils peuvent être mappés uniquement aux comptes d’utilisateurs locaux et ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="60ac0-370">They can be mapped only to local user accounts and they don't work with domain accounts.</span></span>

<span data-ttu-id="60ac0-371">Pour obtenir une empreinte numérique de certificat, utilisez une `Get-Item` `Get-ChildItem` commande ou dans le lecteur de certificat PowerShell :.</span><span class="sxs-lookup"><span data-stu-id="60ac0-371">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-372">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="60ac0-372">-ComputerName</span></span>

<span data-ttu-id="60ac0-373">Spécifie les ordinateurs sur lesquels la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="60ac0-373">Specifies the computers on which the command runs.</span></span> <span data-ttu-id="60ac0-374">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-374">The default is the local computer.</span></span>

<span data-ttu-id="60ac0-375">Quand vous utilisez le paramètre **ComputerName** , PowerShell crée une connexion temporaire qui est utilisée uniquement pour exécuter la commande spécifiée, puis elle est fermée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-375">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that's used only to run the specified command and is then closed.</span></span> <span data-ttu-id="60ac0-376">Si vous avez besoin d’une connexion permanente, utilisez le paramètre **session** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-376">If you need a persistent connection, use the **Session** parameter.</span></span>

<span data-ttu-id="60ac0-377">Tapez le nom NETBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="60ac0-377">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="60ac0-378">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="60ac0-378">To specify the local computer, type the computer name, localhost, or a dot (`.`).</span></span>

<span data-ttu-id="60ac0-379">Pour utiliser une adresse IP dans la valeur **ComputerName**, la commande doit inclure le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-379">To use an IP address in the value of **ComputerName**, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="60ac0-380">L’ordinateur doit être configuré pour le transport HTTPs ou l’adresse IP de l’ordinateur distant doit être incluse dans la liste **TrustedHosts** de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-380">The computer must be configured for the HTTPS transport or the IP address of the remote computer must be included in the local computer's WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="60ac0-381">Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste **TrustedHosts** , consultez [comment ajouter un ordinateur à la liste des hôtes approuvés](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span><span class="sxs-lookup"><span data-stu-id="60ac0-381">For instructions to add a computer name to the **TrustedHosts** list, see [How to Add a Computer to the Trusted Host List](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span></span>

<span data-ttu-id="60ac0-382">Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, pour inclure l’ordinateur local dans la valeur **ComputerName**, vous devez exécuter PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-382">On Windows Vista and later versions of the Windows operating system, to include the local computer in the value of **ComputerName**, you must run PowerShell using the **Run as administrator** option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-383">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="60ac0-383">-ConfigurationName</span></span>

<span data-ttu-id="60ac0-384">Spécifie la configuration de session utilisée pour la nouvelle session **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-384">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="60ac0-385">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-385">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="60ac0-386">Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-386">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="60ac0-387">Lorsqu’il est utilisé avec SSH, ce paramètre spécifie le sous-système à utiliser sur la cible, comme défini dans `sshd_config` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-387">When used with SSH, this parameter specifies the subsystem to use on the target as defined in `sshd_config`.</span></span> <span data-ttu-id="60ac0-388">La valeur par défaut pour SSH est le `powershell` sous-système.</span><span class="sxs-lookup"><span data-stu-id="60ac0-388">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="60ac0-389">La configuration d'une session se trouve sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-389">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="60ac0-390">Si la configuration de session spécifiée n’existe pas sur l’ordinateur distant, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="60ac0-390">If the specified session configuration doesn't exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="60ac0-391">La valeur par défaut est la valeur de la `$PSSessionConfigurationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-391">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="60ac0-392">Si cette variable de préférence n’est pas définie, la valeur par défaut est **Microsoft. PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-392">If this preference variable isn't set, the default is **Microsoft.PowerShell**.</span></span> <span data-ttu-id="60ac0-393">Pour plus d’informations, consultez [about_Preference_Variables](about/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-393">For more information, see [about_Preference_Variables](about/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-394">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="60ac0-394">-ConnectionUri</span></span>

<span data-ttu-id="60ac0-395">Spécifie un URI (Uniform Resource Identifier) qui définit le point de terminaison de connexion de la session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-395">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint of the session.</span></span>
<span data-ttu-id="60ac0-396">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="60ac0-396">The URI must be fully qualified.</span></span>

<span data-ttu-id="60ac0-397">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="60ac0-397">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="60ac0-398">La valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="60ac0-398">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="60ac0-399">Si vous ne spécifiez pas d’URI de connexion, vous pouvez utiliser les paramètres **UseSSL** et **port** pour spécifier les valeurs d’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="60ac0-399">If you don't specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="60ac0-400">Les valeurs valides du segment **Transport** de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="60ac0-400">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="60ac0-401">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-401">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with the standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="60ac0-402">Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-402">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="60ac0-403">Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-403">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-404">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="60ac0-404">-ContainerId</span></span>

<span data-ttu-id="60ac0-405">Spécifie un tableau d’ID de conteneur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-405">Specifies an array of container IDs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-406">-Credential</span><span class="sxs-lookup"><span data-stu-id="60ac0-406">-Credential</span></span>

<span data-ttu-id="60ac0-407">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="60ac0-407">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="60ac0-408">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="60ac0-408">The default is the current user.</span></span>

<span data-ttu-id="60ac0-409">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-409">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="60ac0-410">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="60ac0-410">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="60ac0-411">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="60ac0-411">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="60ac0-412">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="60ac0-412">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-413">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="60ac0-413">-EnableNetworkAccess</span></span>

<span data-ttu-id="60ac0-414">Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="60ac0-414">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="60ac0-415">Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-415">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="60ac0-416">Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-416">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="60ac0-417">Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-417">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="60ac0-418">Pour créer une session de bouclage, omettez le paramètre **ComputerName** ou affectez-lui la valeur dot ( `.` ), localhost ou le nom de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60ac0-418">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (`.`), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="60ac0-419">Par défaut, les sessions de bouclage sont créées à l’aide d’un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-419">By default, loopback sessions are created using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="60ac0-420">Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="60ac0-420">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="60ac0-421">Si vous utilisez **EnableNetworkAccess** quand vous créez une session sur un ordinateur distant, la commande s’exécute correctement, mais le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="60ac0-421">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="60ac0-422">Vous pouvez autoriser l’accès à distance dans une session de bouclage à l’aide de la valeur **CredSSP** du paramètre **Authentication** , qui délègue les informations d’identification de session à d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-422">You can allow remote access in a loopback session using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="60ac0-423">Pour protéger l’ordinateur contre les accès malveillants, les sessions de bouclage déconnectées qui ont des jetons interactifs, qui sont créés à l’aide de **EnableNetworkAccess**, peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-423">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created using **EnableNetworkAccess**, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="60ac0-424">Les sessions déconnectées qui utilisent l'authentification CredSSP peuvent être reconnectées à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-424">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="60ac0-425">Pour plus d’informations, consultez `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="60ac0-425">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="60ac0-426">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-426">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-427">-FilePath</span><span class="sxs-lookup"><span data-stu-id="60ac0-427">-FilePath</span></span>

<span data-ttu-id="60ac0-428">Spécifie un script local que cette applet de commande exécute sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60ac0-428">Specifies a local script that this cmdlet runs on one or more remote computers.</span></span> <span data-ttu-id="60ac0-429">Entrez le chemin d’accès et le nom de fichier du script, ou dirigez un chemin d’accès de script vers `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-429">Enter the path and filename of the script, or pipe a script path to `Invoke-Command`.</span></span> <span data-ttu-id="60ac0-430">Le script doit exister sur l’ordinateur local ou dans un répertoire auquel l’ordinateur local peut accéder.</span><span class="sxs-lookup"><span data-stu-id="60ac0-430">The script must exist on the local computer or in a directory that the local computer can access.</span></span> <span data-ttu-id="60ac0-431">Utilisez **argumentlist** pour spécifier les valeurs des paramètres dans le script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-431">Use **ArgumentList** to specify the values of parameters in the script.</span></span>

<span data-ttu-id="60ac0-432">Lorsque vous utilisez ce paramètre, PowerShell convertit le contenu du fichier de script spécifié en un bloc de script, transmet le bloc de script à l’ordinateur distant et l’exécute sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-432">When you use this parameter, PowerShell converts the contents of the specified script file to a script block, transmits the script block to the remote computer, and runs it on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId, FilePathSSHHost, FilePathSSHHostHash
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-433">-HideComputerName</span><span class="sxs-lookup"><span data-stu-id="60ac0-433">-HideComputerName</span></span>

<span data-ttu-id="60ac0-434">Indique que cette applet de commande omet le nom d’ordinateur de chaque objet dans l’affichage de sortie.</span><span class="sxs-lookup"><span data-stu-id="60ac0-434">Indicates that this cmdlet omits the computer name of each object from the output display.</span></span> <span data-ttu-id="60ac0-435">Par défaut, le nom de l'ordinateur qui a généré l'objet apparaît dans l'affichage.</span><span class="sxs-lookup"><span data-stu-id="60ac0-435">By default, the name of the computer that generated the object appears in the display.</span></span>

<span data-ttu-id="60ac0-436">Ce paramètre affecte uniquement l'affichage de la sortie.</span><span class="sxs-lookup"><span data-stu-id="60ac0-436">This parameter affects only the output display.</span></span> <span data-ttu-id="60ac0-437">Elle ne modifie pas l’objet.</span><span class="sxs-lookup"><span data-stu-id="60ac0-437">It doesn't change the object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases: HCN

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-438">-HostName</span><span class="sxs-lookup"><span data-stu-id="60ac0-438">-HostName</span></span>

<span data-ttu-id="60ac0-439">Spécifie un tableau de noms d’ordinateurs pour une connexion Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="60ac0-439">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="60ac0-440">Cela est similaire au paramètre **ComputerName** , à ceci près que la connexion à l’ordinateur distant s’effectue à l’aide de SSH plutôt que de Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="60ac0-440">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="60ac0-441">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-441">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-442">-InDisconnectedSession</span><span class="sxs-lookup"><span data-stu-id="60ac0-442">-InDisconnectedSession</span></span>

<span data-ttu-id="60ac0-443">Indique que cette applet de commande exécute une commande ou un script dans une session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-443">Indicates that this cmdlet runs a command or script in a disconnected session.</span></span>

<span data-ttu-id="60ac0-444">Quand vous utilisez le paramètre **InDisconnectedSession** , `Invoke-Command` crée une session persistante sur chaque ordinateur distant, démarre la commande spécifiée par le paramètre **scriptblock** ou **filePath** , puis se déconnecte de la session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-444">When you use the **InDisconnectedSession** parameter, `Invoke-Command` creates a persistent session on each remote computer, starts the command specified by the **ScriptBlock** or **FilePath** parameter, and then disconnects from the session.</span></span> <span data-ttu-id="60ac0-445">Les commandes continuent à s’exécuter dans les sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="60ac0-445">The commands continue to run in the disconnected sessions.</span></span> <span data-ttu-id="60ac0-446">**InDisconnectedSession** vous permet d’exécuter des commandes sans maintenir une connexion aux sessions à distance.</span><span class="sxs-lookup"><span data-stu-id="60ac0-446">**InDisconnectedSession** enables you to run commands without maintaining a connection to the remote sessions.</span></span> <span data-ttu-id="60ac0-447">Et, étant donné que la session est déconnectée avant le renvoi des résultats, **InDisconnectedSession** garantit que tous les résultats de la commande sont retournés à la session reconnectée, au lieu d’être fractionnés entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="60ac0-447">And, because the session is disconnected before any results are returned, **InDisconnectedSession** makes sure that all command results are returned to the reconnected session, instead of being split between sessions.</span></span>

<span data-ttu-id="60ac0-448">Vous ne pouvez pas utiliser **InDisconnectedSession** avec le paramètre de **session** ou le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-448">You can't use **InDisconnectedSession** with the **Session** parameter or the **AsJob** parameter.</span></span>

<span data-ttu-id="60ac0-449">Les commandes qui utilisent **InDisconnectedSession** retournent un objet **PSSession** qui représente la session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-449">Commands that use **InDisconnectedSession** return a **PSSession** object that represents the disconnected session.</span></span> <span data-ttu-id="60ac0-450">Ils ne retournent pas la sortie de commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-450">They don't return the command output.</span></span> <span data-ttu-id="60ac0-451">Pour vous connecter à la session déconnectée, utilisez les `Connect-PSSession` applets de commande ou `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-451">To connect to the disconnected session, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span> <span data-ttu-id="60ac0-452">Pour obtenir les résultats des commandes exécutées dans la session, utilisez l' `Receive-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-452">To get the results of commands that ran in the session, use the `Receive-PSSession` cmdlet.</span></span> <span data-ttu-id="60ac0-453">Pour exécuter des commandes qui génèrent une sortie dans une session déconnectée, définissez la valeur de l’option de session **OutputBufferingMode** sur **Drop**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-453">To run commands that generate output in a disconnected session, set the value of the **OutputBufferingMode** session option to **Drop**.</span></span> <span data-ttu-id="60ac0-454">Si vous envisagez de vous connecter à la session déconnectée, définissez le délai d’inactivité dans la session afin qu’elle fournisse suffisamment de temps pour vous connecter avant de supprimer la session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-454">If you intend to connect to the disconnected session, set the idle time-out in the session so that it provides sufficient time for you to connect before deleting the session.</span></span>

<span data-ttu-id="60ac0-455">Vous pouvez définir le mode de mise en mémoire tampon de sortie et le délai d’inactivité dans le paramètre **SessionOption** ou dans la `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="60ac0-455">You can set the output buffering mode and idle time-out in the **SessionOption** parameter or in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="60ac0-456">Pour plus d’informations sur les options de session, consultez `New-PSSessionOption` et [about_Preference_Variables](./about/about_preference_variables.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-456">For more information about session options, see `New-PSSessionOption` and [about_Preference_Variables](./about/about_preference_variables.md).</span></span>

<span data-ttu-id="60ac0-457">Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-457">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="60ac0-458">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-458">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-459">-InputObject</span><span class="sxs-lookup"><span data-stu-id="60ac0-459">-InputObject</span></span>

<span data-ttu-id="60ac0-460">Spécifie l'entrée de la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-460">Specifies input to the command.</span></span> <span data-ttu-id="60ac0-461">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="60ac0-461">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="60ac0-462">Quand vous utilisez le paramètre **InputObject** , utilisez la `$Input` variable Automatic dans la valeur du paramètre **scriptblock** pour représenter les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-462">When using the **InputObject** parameter, use the `$Input` automatic variable in the value of the **ScriptBlock** parameter to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-463">-JobName</span><span class="sxs-lookup"><span data-stu-id="60ac0-463">-JobName</span></span>

<span data-ttu-id="60ac0-464">Spécifie un nom convivial pour la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="60ac0-464">Specifies a friendly name for the background job.</span></span> <span data-ttu-id="60ac0-465">Par défaut, les tâches sont nommées `Job<n>` , où `<n>` est un nombre ordinal.</span><span class="sxs-lookup"><span data-stu-id="60ac0-465">By default, jobs are named `Job<n>`, where `<n>` is an ordinal number.</span></span>

<span data-ttu-id="60ac0-466">Si vous utilisez le paramètre **JobName** dans une commande, la commande est exécutée en tant que tâche et `Invoke-Command` retourne un objet de traitement, même si vous n’incluez pas **AsJob** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-466">If you use the **JobName** parameter in a command, the command is run as a job, and `Invoke-Command` returns a job object, even if you don't include **AsJob** in the command.</span></span>

<span data-ttu-id="60ac0-467">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-467">For more information about PowerShell background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-468">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="60ac0-468">-KeyFilePath</span></span>

<span data-ttu-id="60ac0-469">Spécifie un chemin de fichier de clé utilisé par Secure Shell (SSH) pour authentifier un utilisateur sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-469">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="60ac0-470">SSH permet d’effectuer l’authentification des utilisateurs via des clés privées et publiques comme alternative à l’authentification de base par mot de passe.</span><span class="sxs-lookup"><span data-stu-id="60ac0-470">SSH allows user authentication to be performed via private and public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="60ac0-471">Si l’ordinateur distant est configuré pour l’authentification de clé, ce paramètre peut être utilisé pour fournir la clé qui identifie l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-471">If the remote computer is configured for key authentication, then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="60ac0-472">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-472">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-473">-NoNewScope</span><span class="sxs-lookup"><span data-stu-id="60ac0-473">-NoNewScope</span></span>

<span data-ttu-id="60ac0-474">Indique que cette applet de commande exécute la commande spécifiée dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="60ac0-474">Indicates that this cmdlet runs the specified command in the current scope.</span></span> <span data-ttu-id="60ac0-475">Par défaut, `Invoke-Command` exécute des commandes dans leur propre étendue.</span><span class="sxs-lookup"><span data-stu-id="60ac0-475">By default, `Invoke-Command` runs commands in their own scope.</span></span>

<span data-ttu-id="60ac0-476">Ce paramètre est valide uniquement dans les commandes qui sont exécutées dans la session active, autrement dit, dans les commandes qui omettent les deux paramètres **ComputerName** et **Session**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-476">This parameter is valid only in commands that are run in the current session, that is, commands that omit both the **ComputerName** and **Session** parameters.</span></span>

<span data-ttu-id="60ac0-477">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-477">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-478">-Port</span><span class="sxs-lookup"><span data-stu-id="60ac0-478">-Port</span></span>

<span data-ttu-id="60ac0-479">Spécifie le port réseau sur l’ordinateur distant utilisé pour cette commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-479">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="60ac0-480">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="60ac0-480">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="60ac0-481">Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPs).</span><span class="sxs-lookup"><span data-stu-id="60ac0-481">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="60ac0-482">Avant d'utiliser un autre port, configurez l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="60ac0-482">Before using an alternate port, configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="60ac0-483">Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="60ac0-483">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="60ac0-484">N’utilisez pas le paramètre **port** , sauf si vous devez le faire.</span><span class="sxs-lookup"><span data-stu-id="60ac0-484">Don't use the **Port** parameter unless you must.</span></span> <span data-ttu-id="60ac0-485">Le port défini dans la commande s'applique à tous les ordinateurs ou toutes les sessions sur lesquelles la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="60ac0-485">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="60ac0-486">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="60ac0-486">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, FilePathComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-487">-RemoteDebug</span><span class="sxs-lookup"><span data-stu-id="60ac0-487">-RemoteDebug</span></span>

<span data-ttu-id="60ac0-488">Utilisé pour exécuter la commande appelée en mode débogage dans la session PowerShell distante.</span><span class="sxs-lookup"><span data-stu-id="60ac0-488">Used to run the invoked command in debug mode in the remote PowerShell session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-489">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="60ac0-489">-RunAsAdministrator</span></span>

<span data-ttu-id="60ac0-490">Indique que cette applet de commande appelle une commande en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-490">Indicates that this cmdlet invokes a command as an Administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-491">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="60ac0-491">-ScriptBlock</span></span>

<span data-ttu-id="60ac0-492">Spécifie les commandes à exécuter.</span><span class="sxs-lookup"><span data-stu-id="60ac0-492">Specifies the commands to run.</span></span> <span data-ttu-id="60ac0-493">Placez les commandes entre accolades `{ }` pour créer un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="60ac0-493">Enclose the commands in curly braces `{ }` to create a script block.</span></span>
<span data-ttu-id="60ac0-494">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="60ac0-494">This parameter is required.</span></span>

<span data-ttu-id="60ac0-495">Par défaut, les variables de la commande sont évaluées sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-495">By default, any variables in the command are evaluated on the remote computer.</span></span> <span data-ttu-id="60ac0-496">Pour inclure des variables locales dans la commande, utilisez **argumentlist**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-496">To include local variables in the command, use **ArgumentList**.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, SSHHost, ContainerId, SSHHostHashParam
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-497">-Session</span><span class="sxs-lookup"><span data-stu-id="60ac0-497">-Session</span></span>

<span data-ttu-id="60ac0-498">Spécifie un tableau de sessions dans lequel cette applet de commande exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-498">Specifies an array of sessions in which this cmdlet runs the command.</span></span> <span data-ttu-id="60ac0-499">Entrez une variable qui contient des objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu' `New-PSSession` une `Get-PSSession` commande ou.</span><span class="sxs-lookup"><span data-stu-id="60ac0-499">Enter a variable that contains **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="60ac0-500">Lorsque vous créez une **session PSSession**, PowerShell établit une connexion permanente à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-500">When you create a **PSSession**, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="60ac0-501">Utilisez une **session PSSession** pour exécuter une série de commandes associées qui partagent des données.</span><span class="sxs-lookup"><span data-stu-id="60ac0-501">Use a **PSSession** to run a series of related commands that share data.</span></span> <span data-ttu-id="60ac0-502">Pour exécuter une seule commande ou une série de commandes sans rapport, utilisez le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-502">To run a single command or a series of unrelated commands, use the **ComputerName** parameter.</span></span> <span data-ttu-id="60ac0-503">Pour plus d’informations, consultez [about_PSSessions](./About/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-503">For more information, see [about_PSSessions](./About/about_PSSessions.md).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: FilePathRunspace, Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-504">-Nom_session</span><span class="sxs-lookup"><span data-stu-id="60ac0-504">-SessionName</span></span>

<span data-ttu-id="60ac0-505">Spécifie un nom convivial pour une session déconnectée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-505">Specifies a friendly name for a disconnected session.</span></span> <span data-ttu-id="60ac0-506">Vous pouvez utiliser le nom pour faire référence à la session dans les commandes suivantes, par exemple une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-506">You can use the name to refer to the session in subsequent commands, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="60ac0-507">Ce paramètre est valide uniquement avec le paramètre **InDisconnectedSession**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-507">This parameter is valid only with the **InDisconnectedSession** parameter.</span></span>

<span data-ttu-id="60ac0-508">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-508">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-509">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="60ac0-509">-SessionOption</span></span>

<span data-ttu-id="60ac0-510">Spécifie les options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-510">Specifies advanced options for the session.</span></span> <span data-ttu-id="60ac0-511">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-511">Enter a **SessionOption** object, such as one that you create using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="60ac0-512">Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="60ac0-512">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="60ac0-513">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-513">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="60ac0-514">Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-514">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="60ac0-515">Toutefois, elles ne sont pas prioritaires sur les valeurs maximales, les quotas ou les limites définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-515">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="60ac0-516">Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-516">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="60ac0-517">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-517">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="60ac0-518">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="60ac0-518">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-519">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="60ac0-519">-SSHConnection</span></span>

<span data-ttu-id="60ac0-520">Ce paramètre prend un tableau de tables de hachage dans lequel chaque table de hachage contient un ou plusieurs paramètres de connexion nécessaires pour établir une connexion Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="60ac0-520">This parameter takes an array of hash tables where each hash table contains one or more connection parameters needed to establish a Secure Shell (SSH) connection.</span></span> <span data-ttu-id="60ac0-521">Le paramètre **SSHConnection** est utile pour créer plusieurs sessions où chaque session requiert des informations de connexion différentes.</span><span class="sxs-lookup"><span data-stu-id="60ac0-521">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="60ac0-522">La Hashtable contient les membres suivants :</span><span class="sxs-lookup"><span data-stu-id="60ac0-522">The hashtable has the following members:</span></span>

- <span data-ttu-id="60ac0-523">**ComputerName** (ou **hostname**)</span><span class="sxs-lookup"><span data-stu-id="60ac0-523">**ComputerName** (or **HostName**)</span></span>
- <span data-ttu-id="60ac0-524">**Port**</span><span class="sxs-lookup"><span data-stu-id="60ac0-524">**Port**</span></span>
- <span data-ttu-id="60ac0-525">**UserName**</span><span class="sxs-lookup"><span data-stu-id="60ac0-525">**UserName**</span></span>
- <span data-ttu-id="60ac0-526">**KeyFilePath** (ou **IdentityFilePath**)</span><span class="sxs-lookup"><span data-stu-id="60ac0-526">**KeyFilePath** (or **IdentityFilePath**)</span></span>

<span data-ttu-id="60ac0-527">**ComputerName** (ou **hostname**) est la seule paire clé-valeur requise.</span><span class="sxs-lookup"><span data-stu-id="60ac0-527">**ComputerName** (or **HostName**) is the only key-value pair that is required.</span></span>

<span data-ttu-id="60ac0-528">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-528">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam, FilePathSSHHostHash
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-529">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="60ac0-529">-SSHTransport</span></span>

<span data-ttu-id="60ac0-530">Indique que la connexion à distance est établie à l’aide d’Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="60ac0-530">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="60ac0-531">Par défaut, PowerShell utilise Windows WinRM pour se connecter à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-531">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="60ac0-532">Ce commutateur force PowerShell à utiliser le paramètre **hostname** pour établir une connexion à distance basée sur SSH.</span><span class="sxs-lookup"><span data-stu-id="60ac0-532">This switch forces PowerShell to use the **HostName** parameter for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="60ac0-533">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-533">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-534">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="60ac0-534">-ThrottleLimit</span></span>

<span data-ttu-id="60ac0-535">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-535">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="60ac0-536">Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-536">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="60ac0-537">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-537">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-538">-UserName</span><span class="sxs-lookup"><span data-stu-id="60ac0-538">-UserName</span></span>

<span data-ttu-id="60ac0-539">Spécifie le nom d’utilisateur du compte utilisé pour exécuter une commande sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-539">Specifies the username for the account used to run a command on the remote computer.</span></span> <span data-ttu-id="60ac0-540">La méthode d’authentification de l’utilisateur dépend de la configuration de Secure Shell (SSH) sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-540">The user authentication method depends on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="60ac0-541">Si SSH est configuré pour l’authentification de mot de passe de base, vous êtes invité à entrer le mot de passe de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-541">If SSH is configured for basic password authentication, then you'll be prompted for the user password.</span></span>

<span data-ttu-id="60ac0-542">Si SSH est configuré pour l’authentification utilisateur basée sur les clés, un chemin d’accès de fichier de clé peut être fourni via le paramètre **keyFilePath** et aucune invite de mot de passe n’est générée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-542">If SSH is configured for key-based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt occurs.</span></span> <span data-ttu-id="60ac0-543">Si le fichier de clé de l’utilisateur client se trouve dans un emplacement connu SSH, le paramètre **keyFilePath** n’est pas nécessaire pour l’authentification basée sur les clés et l’authentification de l’utilisateur se produit automatiquement en fonction du nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-543">If the client user key file is located in an SSH known location, then the **KeyFilePath** parameter isn't needed for key-based authentication, and user authentication occurs automatically based on the username.</span></span> <span data-ttu-id="60ac0-544">Pour plus d’informations, consultez la documentation SSH de votre plateforme relative à l’authentification des utilisateurs basée sur les clés.</span><span class="sxs-lookup"><span data-stu-id="60ac0-544">For more information, see your platform's SSH documentation about key-based user authentication.</span></span>

<span data-ttu-id="60ac0-545">Ce paramètre n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="60ac0-545">This isn't a required parameter.</span></span> <span data-ttu-id="60ac0-546">Si le paramètre **username** n’est pas spécifié, le nom d’utilisateur actuellement connecté est utilisé pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="60ac0-546">If the **UserName** parameter isn't specified, then the current logged on username is used for the connection.</span></span>

<span data-ttu-id="60ac0-547">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-547">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-548">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="60ac0-548">-UseSSL</span></span>

<span data-ttu-id="60ac0-549">Indique que cette applet de commande utilise le protocole SSL (Secure Sockets Layer) (SSL) pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60ac0-549">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="60ac0-550">Par défaut, SSL n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="60ac0-550">By default, SSL isn't used.</span></span>

<span data-ttu-id="60ac0-551">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="60ac0-551">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="60ac0-552">Le paramètre **UseSSL** est une protection supplémentaire qui envoie les données via HTTPS au lieu de http.</span><span class="sxs-lookup"><span data-stu-id="60ac0-552">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span>

<span data-ttu-id="60ac0-553">Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="60ac0-553">If you use this parameter, but SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-554">-VMId</span><span class="sxs-lookup"><span data-stu-id="60ac0-554">-VMId</span></span>

<span data-ttu-id="60ac0-555">Spécifie un tableau d’ID de machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="60ac0-555">Specifies an array of IDs of virtual machines.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-556">-VMName</span><span class="sxs-lookup"><span data-stu-id="60ac0-556">-VMName</span></span>

<span data-ttu-id="60ac0-557">Spécifie un tableau de noms d'ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="60ac0-557">Specifies an array of names of virtual machines.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-558">-Sous-système</span><span class="sxs-lookup"><span data-stu-id="60ac0-558">-Subsystem</span></span>

<span data-ttu-id="60ac0-559">Spécifie le sous-système SSH utilisé pour la nouvelle **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-559">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="60ac0-560">Cela spécifie le sous-système à utiliser sur la cible, tel que défini dans sshd_config.</span><span class="sxs-lookup"><span data-stu-id="60ac0-560">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="60ac0-561">Le sous-système démarre une version spécifique de PowerShell avec des paramètres prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="60ac0-561">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="60ac0-562">Si le sous-système spécifié n’existe pas sur l’ordinateur distant, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="60ac0-562">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="60ac0-563">Si ce paramètre n’est pas utilisé, la valeur par défaut est le sous-système « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="60ac0-563">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="60ac0-564">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="60ac0-564">CommonParameters</span></span>

<span data-ttu-id="60ac0-565">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="60ac0-565">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="60ac0-566">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="60ac0-566">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="60ac0-567">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="60ac0-567">INPUTS</span></span>

### <span data-ttu-id="60ac0-568">System. Management. Automation. ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="60ac0-568">System.Management.Automation.ScriptBlock</span></span>

<span data-ttu-id="60ac0-569">Vous pouvez diriger une commande dans un bloc de script vers `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="60ac0-569">You can pipe a command in a script block to `Invoke-Command`.</span></span> <span data-ttu-id="60ac0-570">Utilisez la `$Input` variable Automatic pour représenter les objets d’entrée de la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-570">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="60ac0-571">SORTIES</span><span class="sxs-lookup"><span data-stu-id="60ac0-571">OUTPUTS</span></span>

### <span data-ttu-id="60ac0-572">System. Management. Automation. PSRemotingJob, System. Management. Automation. instances d’exécution. PSSession ou la sortie de la commande appelée</span><span class="sxs-lookup"><span data-stu-id="60ac0-572">System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession, or the output of the invoked command</span></span>

<span data-ttu-id="60ac0-573">Cette applet de commande retourne un objet de traitement, si vous utilisez le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-573">This cmdlet returns a job object, if you use the **AsJob** parameter.</span></span> <span data-ttu-id="60ac0-574">Si vous spécifiez le paramètre **InDisconnectedSession** , `Invoke-Command` retourne un objet **PSSession** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-574">If you specify the **InDisconnectedSession** parameter, `Invoke-Command` returns a **PSSession** object.</span></span> <span data-ttu-id="60ac0-575">Dans le cas contraire, elle retourne la sortie de la commande appelée, qui est la valeur du paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-575">Otherwise, it returns the output of the invoked command, which is the value of the **ScriptBlock** parameter.</span></span>

## <span data-ttu-id="60ac0-576">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="60ac0-576">NOTES</span></span>

<span data-ttu-id="60ac0-577">Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, pour utiliser le paramètre **ComputerName** de `Invoke-Command` pour exécuter une commande sur l’ordinateur local, vous devez exécuter PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="60ac0-577">On Windows Vista, and later versions of the Windows operating system, to use the **ComputerName** parameter of `Invoke-Command` to run a command on the local computer, you must run PowerShell using the **Run as administrator** option.</span></span>

<span data-ttu-id="60ac0-578">Lorsque vous exécutez des commandes sur plusieurs ordinateurs, PowerShell se connecte aux ordinateurs dans l’ordre dans lequel ils apparaissent dans la liste.</span><span class="sxs-lookup"><span data-stu-id="60ac0-578">When you run commands on multiple computers, PowerShell connects to the computers in the order in which they appear in the list.</span></span> <span data-ttu-id="60ac0-579">Toutefois, la sortie de la commande s’affiche dans l’ordre dans lequel elle est reçue des ordinateurs distants, ce qui peut être différent.</span><span class="sxs-lookup"><span data-stu-id="60ac0-579">However, the command output is displayed in the order that it's received from the remote computers, which might be different.</span></span>

<span data-ttu-id="60ac0-580">Les erreurs qui résultent de la commande qui `Invoke-Command` s’exécute sont incluses dans les résultats de la commande.</span><span class="sxs-lookup"><span data-stu-id="60ac0-580">Errors that result from the command that `Invoke-Command` runs are included in the command results.</span></span>
<span data-ttu-id="60ac0-581">Les erreurs qui seraient des erreurs avec fin d'exécution dans une commande locale sont traitées comme des erreurs sans fin d'exécution dans une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="60ac0-581">Errors that would be terminating errors in a local command are treated as non-terminating errors in a remote command.</span></span> <span data-ttu-id="60ac0-582">Cette stratégie permet de s’assurer que les erreurs d’arrêt sur un ordinateur ne ferment pas la commande sur tous les ordinateurs sur lesquels elle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="60ac0-582">This strategy makes sure that terminating errors on one computer don't close the command on all computers on which it's run.</span></span> <span data-ttu-id="60ac0-583">Cette pratique est utilisée même quand une commande à distance est exécutée sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-583">This practice is used even when a remote command is run on a single computer.</span></span>

<span data-ttu-id="60ac0-584">Si l’ordinateur distant n’est pas dans un domaine approuvé par l’ordinateur local, il se peut que l’ordinateur ne soit pas en mesure d’authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60ac0-584">If the remote computer isn't in a domain that the local computer trusts, the computer might not be able to authenticate the user's credentials.</span></span> <span data-ttu-id="60ac0-585">Pour ajouter l’ordinateur distant à la liste des hôtes approuvés dans WS-Management, utilisez la commande suivante dans le `WSMAN` fournisseur, où `<Remote-Computer-Name>` est le nom de l’ordinateur distant :</span><span class="sxs-lookup"><span data-stu-id="60ac0-585">To add the remote computer to the list of trusted hosts in WS-Management, use the following command in the `WSMAN` provider, where `<Remote-Computer-Name>` is the name of the remote computer:</span></span>

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

<span data-ttu-id="60ac0-586">Lorsque vous déconnectez une session **PSSession** à l’aide du paramètre **InDisconnectedSession** , l’état de session est **Disconnected** et la disponibilité est **None**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-586">When you disconnect a **PSSession** using the **InDisconnectedSession** parameter, the session state is **Disconnected** and the availability is **None**.</span></span> <span data-ttu-id="60ac0-587">La valeur de la propriété **State** dépend de la session active.</span><span class="sxs-lookup"><span data-stu-id="60ac0-587">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="60ac0-588">La valeur **Disconnected** signifie que la session **PSSession** n’est pas connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="60ac0-588">A value of **Disconnected** means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="60ac0-589">Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions.</span><span class="sxs-lookup"><span data-stu-id="60ac0-589">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="60ac0-590">Elle peut être connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-590">It might be connected to a different session.</span></span> <span data-ttu-id="60ac0-591">Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability**.</span><span class="sxs-lookup"><span data-stu-id="60ac0-591">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

<span data-ttu-id="60ac0-592">Une propriété **Availability** avec la valeur **None** signifie que vous pouvez vous connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-592">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="60ac0-593">La valeur **Busy** indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="60ac0-593">A value of **Busy** indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span> <span data-ttu-id="60ac0-594">Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="60ac0-594">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span> <span data-ttu-id="60ac0-595">Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="60ac0-595">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

<span data-ttu-id="60ac0-596">Les paramètres **hostname** et **SSHConnection** ont été inclus à partir de PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="60ac0-596">The **HostName** and **SSHConnection** parameters were included starting with PowerShell 6.0.</span></span> <span data-ttu-id="60ac0-597">Elles ont été ajoutées pour fournir une communication à distance PowerShell basée sur Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="60ac0-597">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="60ac0-598">PowerShell et SSH sont pris en charge sur plusieurs plateformes (Windows, Linux, macOS) et la communication à distance PowerShell fonctionne sur ces plateformes où PowerShell et SSH sont installés et configurés.</span><span class="sxs-lookup"><span data-stu-id="60ac0-598">PowerShell and SSH are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting works over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="60ac0-599">Cela est différent de la version précédente de Windows uniquement qui est basée sur WinRM et la plupart des fonctionnalités et limitations spécifiques à WinRM ne s’appliquent pas.</span><span class="sxs-lookup"><span data-stu-id="60ac0-599">This is separate from the previous Windows only remoting that is based on WinRM and many of the WinRM specific features and limitations don't apply.</span></span> <span data-ttu-id="60ac0-600">Par exemple, les quotas basés sur WinRM, les options de session, la configuration de point de terminaison personnalisée et les fonctionnalités de déconnexion/reconnexion ne sont actuellement pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="60ac0-600">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="60ac0-601">Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="60ac0-601">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="60ac0-602">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="60ac0-602">RELATED LINKS</span></span>

[<span data-ttu-id="60ac0-603">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="60ac0-603">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="60ac0-604">about_Remote</span><span class="sxs-lookup"><span data-stu-id="60ac0-604">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="60ac0-605">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="60ac0-605">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="60ac0-606">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="60ac0-606">about_Remote_Troubleshooting</span></span>](./About/about_remote_troubleshooting.md)

[<span data-ttu-id="60ac0-607">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="60ac0-607">about_Remote_Variables</span></span>](./About/about_Remote_Variables.md)

[<span data-ttu-id="60ac0-608">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="60ac0-608">about_Scopes</span></span>](./About/about_scopes.md)

[<span data-ttu-id="60ac0-609">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="60ac0-609">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="60ac0-610">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="60ac0-610">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="60ac0-611">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="60ac0-611">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="60ac0-612">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="60ac0-612">Invoke-Item</span></span>](../Microsoft.PowerShell.Management/Invoke-Item.md)

[<span data-ttu-id="60ac0-613">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="60ac0-613">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="60ac0-614">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="60ac0-614">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="60ac0-615">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="60ac0-615">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

