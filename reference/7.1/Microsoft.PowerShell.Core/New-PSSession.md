---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: e5dedf3d161f2687bddfbd09740812d8c5cbaa77
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205673"
---
# <span data-ttu-id="2e58c-103">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-103">New-PSSession</span></span>

## <span data-ttu-id="2e58c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2e58c-104">SYNOPSIS</span></span>
<span data-ttu-id="2e58c-105">Crée une connexion persistante à un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-105">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="2e58c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2e58c-106">SYNTAX</span></span>

### <span data-ttu-id="2e58c-107">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2e58c-107">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="2e58c-108">Uri</span><span class="sxs-lookup"><span data-stu-id="2e58c-108">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="2e58c-109">VMId</span><span class="sxs-lookup"><span data-stu-id="2e58c-109">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="2e58c-110">VMName</span><span class="sxs-lookup"><span data-stu-id="2e58c-110">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="2e58c-111">session</span><span class="sxs-lookup"><span data-stu-id="2e58c-111">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="2e58c-112">ContainerId</span><span class="sxs-lookup"><span data-stu-id="2e58c-112">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="2e58c-113">UseWindowsPowerShellParameterSet</span><span class="sxs-lookup"><span data-stu-id="2e58c-113">UseWindowsPowerShellParameterSet</span></span>

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### <span data-ttu-id="2e58c-114">SSHHost</span><span class="sxs-lookup"><span data-stu-id="2e58c-114">SSHHost</span></span>

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### <span data-ttu-id="2e58c-115">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="2e58c-115">SSHHostHashParam</span></span>

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## <span data-ttu-id="2e58c-116">Description</span><span class="sxs-lookup"><span data-stu-id="2e58c-116">DESCRIPTION</span></span>

<span data-ttu-id="2e58c-117">L' `New-PSSession` applet de commande crée une session PowerShell ( **PSSession** ) sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-117">The `New-PSSession` cmdlet creates a PowerShell session ( **PSSession** ) on a local or remote computer.</span></span> <span data-ttu-id="2e58c-118">Lorsque vous créez une **session PSSession** , PowerShell établit une connexion permanente à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-118">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="2e58c-119">Utilisez une **session PSSession** pour exécuter plusieurs commandes qui partagent des données, telles qu’une fonction ou la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-119">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="2e58c-120">Pour exécuter des commandes dans une **session PSSession** , utilisez l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-120">To run commands in a **PSSession** , use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="2e58c-121">Pour utiliser la **session PSSession** pour interagir directement avec un ordinateur distant, utilisez l’applet de commande `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-121">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="2e58c-122">Pour plus d’informations, consultez [about_PSSessions](about/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="2e58c-122">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="2e58c-123">Vous pouvez exécuter des commandes sur un ordinateur distant sans créer de **session PSSession** à l’aide des paramètres **ComputerName** de `Enter-PSSession` ou `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-123">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="2e58c-124">Quand vous utilisez le paramètre **ComputerName** , PowerShell crée une connexion temporaire qui est utilisée pour la commande et qui est ensuite fermée.</span><span class="sxs-lookup"><span data-stu-id="2e58c-124">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

<span data-ttu-id="2e58c-125">À compter de PowerShell 6,0, vous pouvez utiliser Secure Shell (SSH) pour établir une connexion à et créer une session sur un ordinateur distant, si SSH est disponible sur l’ordinateur local et que l’ordinateur distant est configuré avec un point de terminaison SSH PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e58c-125">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and create a session on a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="2e58c-126">L’avantage d’une session à distance PowerShell basée sur SSH est qu’elle peut fonctionner sur plusieurs plateformes (Windows, Linux, macOS).</span><span class="sxs-lookup"><span data-stu-id="2e58c-126">The benefit of an SSH based PowerShell remote session is that it can work across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="2e58c-127">Pour les sessions SSH, vous utilisez le **nom d’hôte** ou le jeu de paramètres **SSHConnection** pour spécifier l’ordinateur distant et les informations de connexion appropriées.</span><span class="sxs-lookup"><span data-stu-id="2e58c-127">For SSH based sessions you use the **HostName** or **SSHConnection** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="2e58c-128">Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="2e58c-128">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="2e58c-129">Lors de l’utilisation de la communication à distance WSMan à partir d’un client Linux ou macOS avec un point de terminaison HTTPs où le certificat de serveur n’est pas approuvé (par exemple, un certificat auto-signé).</span><span class="sxs-lookup"><span data-stu-id="2e58c-129">When using WSMan remoting from a Linux or macOS client with a HTTPS endpoint where the server certificate is not trusted (e.g., a self-signed certificate).</span></span> <span data-ttu-id="2e58c-130">Vous devez fournir un `PSSessionOption` qui comprend `-SkipCACheck` et `-SkipCNCheck` pour établir correctement la connexion.</span><span class="sxs-lookup"><span data-stu-id="2e58c-130">You must provide a `PSSessionOption` that includes `-SkipCACheck` and `-SkipCNCheck` to successfully establish the connection.</span></span> <span data-ttu-id="2e58c-131">Ne le faites que si vous êtes dans un environnement dans lequel vous pouvez être certain du certificat de serveur et de la connexion réseau au système cible.</span><span class="sxs-lookup"><span data-stu-id="2e58c-131">Only do this if you are in an environment where you can be certain of the server certificate and the network connection to the target system.</span></span>

## <span data-ttu-id="2e58c-132">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2e58c-132">EXAMPLES</span></span>

### <span data-ttu-id="2e58c-133">Exemple 1 : créer une session sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="2e58c-133">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="2e58c-134">Cette commande crée une session **PSSession** sur l’ordinateur local et enregistre la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-134">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="2e58c-135">Vous pouvez maintenant utiliser cette **session PSSession** pour exécuter des commandes sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2e58c-135">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="2e58c-136">Exemple 2 : créer une session sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="2e58c-136">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="2e58c-137">Cette commande crée une **session PSSession** sur l’ordinateur SERVEUR01 et l’enregistre dans la `$Server01` variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-137">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="2e58c-138">Lorsque vous créez plusieurs objets **PSSession** , assignez-les à des variables avec des noms utiles.</span><span class="sxs-lookup"><span data-stu-id="2e58c-138">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="2e58c-139">Cela vous aidera à gérer les objets **PSSession** dans les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="2e58c-139">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="2e58c-140">Exemple 3 : créer des sessions sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="2e58c-140">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="2e58c-141">Cette commande crée trois objets **PSSession** , un sur chacun des ordinateurs spécifiés par le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-141">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="2e58c-142">La commande utilise l’opérateur d’assignation (=) pour assigner les nouveaux objets **PSSession** aux variables : `$s1` , `$s2` , `$s3` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-142">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="2e58c-143">Elle attribue la **session** SERVEUR01 à `$s1` , la session **PSSession** Server02 à `$s2` et la **session PSSession** Server03 à `$s3` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-143">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="2e58c-144">Lorsque vous assignez plusieurs objets à une série de variables, PowerShell assigne respectivement chaque objet à une variable de la série.</span><span class="sxs-lookup"><span data-stu-id="2e58c-144">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="2e58c-145">S'il y a plus d'objets que de variables, tous les objets restants sont affectés à la dernière variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-145">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="2e58c-146">S'il y a plus de variables que d'objets, les autres variables sont vides (null).</span><span class="sxs-lookup"><span data-stu-id="2e58c-146">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="2e58c-147">Exemple 4 : créer une session avec un port spécifié</span><span class="sxs-lookup"><span data-stu-id="2e58c-147">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="2e58c-148">Cette commande crée une session **PSSession** sur l’ordinateur SERVEUR01 qui se connecte au port 8081 du serveur et utilise le protocole SSL.</span><span class="sxs-lookup"><span data-stu-id="2e58c-148">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="2e58c-149">La nouvelle session **PSSession** utilise une autre configuration de session appelée E12.</span><span class="sxs-lookup"><span data-stu-id="2e58c-149">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="2e58c-150">Avant de définir le port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant afin d'écouter sur le port 8081.</span><span class="sxs-lookup"><span data-stu-id="2e58c-150">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="2e58c-151">Pour plus d’informations, consultez la description du paramètre de **port** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-151">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="2e58c-152">Exemple 5 : créer une session basée sur une session existante</span><span class="sxs-lookup"><span data-stu-id="2e58c-152">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="2e58c-153">Cette commande crée une **session PSSession** avec les mêmes propriétés qu’une **session PSSession** existante.</span><span class="sxs-lookup"><span data-stu-id="2e58c-153">This command creates a **PSSession** with the same properties as an existing **PSSession** .</span></span> <span data-ttu-id="2e58c-154">Vous pouvez utiliser ce format de commande lorsque les ressources d’une **session PSSession** existante sont épuisées et qu’une nouvelle **session PSSession** est nécessaire pour décharger une partie de la demande.</span><span class="sxs-lookup"><span data-stu-id="2e58c-154">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="2e58c-155">La commande utilise le paramètre **session** de `New-PSSession` pour spécifier la session **PSSession** enregistrée dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-155">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="2e58c-156">Elle utilise les informations d'identification de l'utilisateur Domain1\Admin01 pour terminer la commande.</span><span class="sxs-lookup"><span data-stu-id="2e58c-156">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="2e58c-157">Exemple 6 : créer une session avec une étendue globale dans un autre domaine</span><span class="sxs-lookup"><span data-stu-id="2e58c-157">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="2e58c-158">Cet exemple montre comment créer une **session PSSession** avec une portée globale sur un ordinateur situé dans un autre domaine.</span><span class="sxs-lookup"><span data-stu-id="2e58c-158">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="2e58c-159">Par défaut, les objets **PSSession** créés sur la ligne de commande sont créés avec une portée locale et les objets **PSSession** créés dans un script ont une portée de script.</span><span class="sxs-lookup"><span data-stu-id="2e58c-159">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="2e58c-160">Pour créer une **session PSSession** avec une portée globale, créez une **session** PSSession, puis stockez la **session PSSession** dans une variable qui est convertie en portée globale.</span><span class="sxs-lookup"><span data-stu-id="2e58c-160">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="2e58c-161">Dans ce cas, la `$s` variable est convertie en portée globale.</span><span class="sxs-lookup"><span data-stu-id="2e58c-161">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="2e58c-162">La commande utilise le paramètre **ComputerName** pour spécifier l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-162">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="2e58c-163">Étant donné que l’ordinateur se trouve dans un domaine différent de celui du compte d’utilisateur, le nom complet de l’ordinateur est spécifié avec les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-163">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="2e58c-164">Exemple 7 : créer des sessions pour de nombreux ordinateurs</span><span class="sxs-lookup"><span data-stu-id="2e58c-164">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="2e58c-165">Cette commande crée une session **PSSession** sur chacun des ordinateurs 200 listés dans le fichier Servers.txt et stocke la **session PSSession** résultante dans la `$rs` variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-165">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="2e58c-166">Les objets **PSSession** ont une limite de limitation de 50.</span><span class="sxs-lookup"><span data-stu-id="2e58c-166">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="2e58c-167">Vous pouvez utiliser ce format de commande lorsque les noms des ordinateurs sont stockés dans une base de données, une feuille de calcul, un fichier texte ou tout autre format convertible en texte.</span><span class="sxs-lookup"><span data-stu-id="2e58c-167">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="2e58c-168">Exemple 8 : créer une session à l’aide d’un URI</span><span class="sxs-lookup"><span data-stu-id="2e58c-168">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="2e58c-169">Cette commande crée une **session PSSession** sur l’ordinateur SERVEUR01 et le stocke dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-169">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="2e58c-170">Elle utilise le paramètre **URI** pour spécifier le protocole de transport, l’ordinateur distant, le port et une autre configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-170">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="2e58c-171">Elle utilise également le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de créer une session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-171">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="2e58c-172">Exemple 9 : exécuter une tâche en arrière-plan dans un ensemble de sessions</span><span class="sxs-lookup"><span data-stu-id="2e58c-172">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="2e58c-173">Ces commandes créent un ensemble d’objets **PSSession** , puis exécutent une tâche en arrière-plan dans chacun des objets **PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-173">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="2e58c-174">La première commande crée une **session PSSession** sur chacun des ordinateurs figurant dans le fichier Servers.txt.</span><span class="sxs-lookup"><span data-stu-id="2e58c-174">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="2e58c-175">Elle utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-175">It uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span> <span data-ttu-id="2e58c-176">La valeur du paramètre **ComputerName** est une commande qui utilise l' `Get-Content` applet de commande pour obtenir la liste des noms d’ordinateur du fichier Servers.txt.</span><span class="sxs-lookup"><span data-stu-id="2e58c-176">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="2e58c-177">La commande utilise le paramètre **Credential** pour créer les objets **PSSession** qui ont l’autorisation d’un administrateur de domaine, et elle utilise le paramètre **ThrottleLimit** pour limiter la commande à 16 connexions simultanées.</span><span class="sxs-lookup"><span data-stu-id="2e58c-177">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="2e58c-178">La commande enregistre les objets **PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-178">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="2e58c-179">La deuxième commande utilise le paramètre **AsJob** de l' `Invoke-Command` applet de commande pour démarrer une tâche en arrière-plan qui exécute une `Get-Process PowerShell` commande dans chacun des objets **PSSession** dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-179">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="2e58c-180">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](About/about_Jobs.md) et [about_Remote_Jobs](About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2e58c-180">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="2e58c-181">Exemple 10 : créer une session pour un ordinateur à l’aide de son URI</span><span class="sxs-lookup"><span data-stu-id="2e58c-181">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="2e58c-182">Cette commande crée un objet **PSSession** qui se connecte à un ordinateur spécifié par un URI au lieu d’un nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-182">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="2e58c-183">Exemple 11 : créer une option de session</span><span class="sxs-lookup"><span data-stu-id="2e58c-183">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="2e58c-184">Cet exemple montre comment créer un objet d’option de session et utiliser le paramètre **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-184">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="2e58c-185">La première commande utilise l' `New-PSSessionOption` applet de commande pour créer une option de session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-185">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="2e58c-186">Elle enregistre l’objet **SessionOption** résultant dans la `$so` variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-186">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="2e58c-187">La deuxième commande utilise l'option d'une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-187">The second command uses the option in a new session.</span></span> <span data-ttu-id="2e58c-188">La commande utilise l' `New-PSSession` applet de commande pour créer une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-188">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="2e58c-189">La valeur du paramètre SessionOption est l’objet **SessionOption** dans la `$so` variable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-189">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

### <span data-ttu-id="2e58c-190">Exemple 12 : créer une session à l’aide de SSH</span><span class="sxs-lookup"><span data-stu-id="2e58c-190">Example 12: Create a session using SSH</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="2e58c-191">Cet exemple montre comment créer une **session PSSession** à l’aide de Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="2e58c-191">This example shows how to create a new **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="2e58c-192">Si SSH est configuré sur l’ordinateur distant pour demander des mots de passe, vous recevrez une invite de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2e58c-192">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span> <span data-ttu-id="2e58c-193">Dans le cas contraire, vous devrez utiliser l’authentification utilisateur basée sur une clé SSH.</span><span class="sxs-lookup"><span data-stu-id="2e58c-193">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="2e58c-194">Exemple 13 : créer une session à l’aide de SSH et spécifier le port et la clé d’authentification utilisateur</span><span class="sxs-lookup"><span data-stu-id="2e58c-194">Example 13: Create a session using SSH and specify the port and user authentication key</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="2e58c-195">Cet exemple montre comment créer une **session PSSession** à l’aide de Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="2e58c-195">This example shows how to create a **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="2e58c-196">Elle utilise le paramètre **port** pour spécifier le port à utiliser et le paramètre **keyFilePath** pour spécifier une clé RSA utilisée pour identifier et authentifier l’utilisateur sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-196">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to identify and authenticate the user on the remote computer.</span></span>

### <span data-ttu-id="2e58c-197">Exemple 14 : créer plusieurs sessions à l’aide de SSH</span><span class="sxs-lookup"><span data-stu-id="2e58c-197">Example 14: Create multiple sessions using SSH</span></span>

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

<span data-ttu-id="2e58c-198">Cet exemple montre comment créer plusieurs sessions à l’aide de Secure Shell (SSH) et du jeu de paramètres **SSHConnection** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-198">This example shows how to create multiple sessions using Secure Shell (SSH) and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="2e58c-199">Le paramètre **SSHConnection** prend un tableau de tables de hachage qui contiennent des informations de connexion pour chaque session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-199">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each session.</span></span> <span data-ttu-id="2e58c-200">Notez que cet exemple requiert que SSH soit configuré sur les ordinateurs distants cibles pour prendre en charge l’authentification des utilisateurs basée sur les clés.</span><span class="sxs-lookup"><span data-stu-id="2e58c-200">Note that this example requires that the target remote computers have SSH configured to support key based user authentication.</span></span>

## <span data-ttu-id="2e58c-201">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e58c-201">PARAMETERS</span></span>

### <span data-ttu-id="2e58c-202">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="2e58c-202">-AllowRedirection</span></span>

<span data-ttu-id="2e58c-203">Indique que cette applet de commande autorise la redirection de cette connexion vers un autre Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="2e58c-203">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="2e58c-204">Quand vous utilisez le paramètre **ConnectionURI** , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="2e58c-204">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="2e58c-205">Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.</span><span class="sxs-lookup"><span data-stu-id="2e58c-205">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="2e58c-206">Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-206">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="2e58c-207">Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la variable de préférence **$PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-207">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="2e58c-208">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="2e58c-208">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-209">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="2e58c-209">-ApplicationName</span></span>

<span data-ttu-id="2e58c-210">Spécifie le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="2e58c-210">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="2e58c-211">Utilisez ce paramètre pour spécifier le nom de l'application quand vous n'utilisez pas le paramètre **ConnectionURI** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="2e58c-211">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="2e58c-212">La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2e58c-212">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="2e58c-213">Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN.</span><span class="sxs-lookup"><span data-stu-id="2e58c-213">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="2e58c-214">Cette valeur convient pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="2e58c-214">This value is appropriate for most uses.</span></span> <span data-ttu-id="2e58c-215">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="2e58c-215">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="2e58c-216">Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="2e58c-216">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="2e58c-217">La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-217">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-218">-Authentification</span><span class="sxs-lookup"><span data-stu-id="2e58c-218">-Authentication</span></span>

<span data-ttu-id="2e58c-219">Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-219">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="2e58c-220">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="2e58c-220">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2e58c-221">Default</span><span class="sxs-lookup"><span data-stu-id="2e58c-221">Default</span></span>
- <span data-ttu-id="2e58c-222">Basic</span><span class="sxs-lookup"><span data-stu-id="2e58c-222">Basic</span></span>
- <span data-ttu-id="2e58c-223">CredSSP</span><span class="sxs-lookup"><span data-stu-id="2e58c-223">Credssp</span></span>
- <span data-ttu-id="2e58c-224">Digest</span><span class="sxs-lookup"><span data-stu-id="2e58c-224">Digest</span></span>
- <span data-ttu-id="2e58c-225">Kerberos</span><span class="sxs-lookup"><span data-stu-id="2e58c-225">Kerberos</span></span>
- <span data-ttu-id="2e58c-226">Negotiate</span><span class="sxs-lookup"><span data-stu-id="2e58c-226">Negotiate</span></span>
- <span data-ttu-id="2e58c-227">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="2e58c-227">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="2e58c-228">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="2e58c-228">The default value is Default.</span></span>

<span data-ttu-id="2e58c-229">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="2e58c-229">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="2e58c-230">L’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-230">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="2e58c-231">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="2e58c-231">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="2e58c-232">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="2e58c-232">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-233">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="2e58c-233">-CertificateThumbprint</span></span>

<span data-ttu-id="2e58c-234">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="2e58c-234">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="2e58c-235">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="2e58c-235">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="2e58c-236">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="2e58c-236">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="2e58c-237">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="2e58c-237">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="2e58c-238">Pour obtenir un certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur du certificat PowerShell :</span><span class="sxs-lookup"><span data-stu-id="2e58c-238">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="2e58c-239">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="2e58c-239">-ComputerName</span></span>

<span data-ttu-id="2e58c-240">Spécifie un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-240">Specifies an array of names of computers.</span></span> <span data-ttu-id="2e58c-241">Cette applet de commande crée une connexion permanente ( **PSSession** ) sur l’ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="2e58c-241">This cmdlet creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="2e58c-242">Si vous entrez plusieurs noms d’ordinateur, `New-PSSession` crée plusieurs objets **PSSession** , un pour chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-242">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="2e58c-243">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2e58c-243">The default is the local computer.</span></span>

<span data-ttu-id="2e58c-244">Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="2e58c-244">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="2e58c-245">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.).</span><span class="sxs-lookup"><span data-stu-id="2e58c-245">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="2e58c-246">Lorsque l'ordinateur distant se trouve dans un domaine différent de celui de l'utilisateur, le nom de domaine complet est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2e58c-246">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="2e58c-247">Vous pouvez également diriger un nom d’ordinateur, entre guillemets, vers `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-247">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="2e58c-248">Pour utiliser une adresse IP dans la valeur du paramètre **ComputerName** , la commande doit inclure le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-248">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="2e58c-249">En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2e58c-249">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="2e58c-250">Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="2e58c-250">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="2e58c-251">Pour inclure l’ordinateur local dans la valeur du paramètre **ComputerName** , démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-251">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-252">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="2e58c-252">-ConfigurationName</span></span>

<span data-ttu-id="2e58c-253">Spécifie la configuration de session utilisée pour la nouvelle session **PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-253">Specifies the session configuration that is used for the new **PSSession** .</span></span>

<span data-ttu-id="2e58c-254">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-254">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="2e58c-255">Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-255">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="2e58c-256">La configuration d'une session se trouve sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-256">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="2e58c-257">Si la configuration de session spécifiée n'existe pas sur l'ordinateur distant, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="2e58c-257">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="2e58c-258">La valeur par défaut est la valeur de la `$PSSessionConfigurationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2e58c-258">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="2e58c-259">Si cette variable de préférence n'est pas définie, la valeur par défaut est Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e58c-259">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="2e58c-260">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="2e58c-260">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-261">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="2e58c-261">-ConnectionUri</span></span>

<span data-ttu-id="2e58c-262">Spécifie un URI qui définit le point de terminaison de connexion pour la session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-262">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="2e58c-263">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="2e58c-263">The URI must be fully qualified.</span></span> <span data-ttu-id="2e58c-264">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="2e58c-264">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="2e58c-265">La valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2e58c-265">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="2e58c-266">Si vous ne spécifiez pas un **ConnectionURI** , vous pouvez utiliser les paramètres **UseSSL** , **ComputerName** , **Port** et **ApplicationName** pour spécifier les valeurs **ConnectionURI** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-266">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="2e58c-267">Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e58c-267">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="2e58c-268">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-268">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="2e58c-269">Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-269">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="2e58c-270">Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="2e58c-270">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-271">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="2e58c-271">-ContainerId</span></span>

<span data-ttu-id="2e58c-272">Spécifie un tableau d’ID de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-272">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="2e58c-273">Cette applet de commande démarre une session interactive avec chacun des conteneurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2e58c-273">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="2e58c-274">Utilisez la `docker ps` commande pour obtenir la liste des ID de conteneur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-274">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="2e58c-275">Pour plus d’informations, consultez l’aide de la commande [dockr PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="2e58c-275">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-276">-Credential</span><span class="sxs-lookup"><span data-stu-id="2e58c-276">-Credential</span></span>

<span data-ttu-id="2e58c-277">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="2e58c-277">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="2e58c-278">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="2e58c-278">The default is the current user.</span></span>

<span data-ttu-id="2e58c-279">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-279">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2e58c-280">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2e58c-280">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="2e58c-281">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="2e58c-281">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2e58c-282">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="2e58c-282">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-283">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="2e58c-283">-EnableNetworkAccess</span></span>

<span data-ttu-id="2e58c-284">Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="2e58c-284">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="2e58c-285">Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-285">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="2e58c-286">Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2e58c-286">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="2e58c-287">Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-287">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="2e58c-288">Pour créer une session de bouclage, omettez le paramètre **ComputerName** ou définissez sa valeur sur point (.), localhost ou le nom de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2e58c-288">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="2e58c-289">Par défaut, cette applet de commande crée des sessions de bouclage à l’aide d’un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="2e58c-289">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="2e58c-290">Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="2e58c-290">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="2e58c-291">Si vous utilisez **EnableNetworkAccess** quand vous créez une session sur un ordinateur distant, la commande s’exécute correctement, mais le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="2e58c-291">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="2e58c-292">Vous pouvez également activer l’accès à distance dans une session de bouclage en utilisant la valeur CredSSP du paramètre **Authentication** , qui délègue les informations d’identification de session à d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-292">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="2e58c-293">Pour protéger l’ordinateur contre les accès malveillants, les sessions de bouclage déconnectées qui ont des jetons interactifs, qui sont créés à l’aide du paramètre **EnableNetworkAccess** , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée.</span><span class="sxs-lookup"><span data-stu-id="2e58c-293">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="2e58c-294">Les sessions déconnectées qui utilisent l'authentification CredSSP peuvent être reconnectées à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-294">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="2e58c-295">Pour plus d'informations, consultez `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="2e58c-295">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="2e58c-296">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2e58c-296">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-297">-HostName</span><span class="sxs-lookup"><span data-stu-id="2e58c-297">-HostName</span></span>

<span data-ttu-id="2e58c-298">Spécifie un tableau de noms d’ordinateurs pour une connexion Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="2e58c-298">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="2e58c-299">Cela est similaire au paramètre ComputerName, à ceci près que la connexion à l’ordinateur distant s’effectue à l’aide de SSH plutôt que de Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="2e58c-299">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="2e58c-300">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2e58c-300">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-301">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="2e58c-301">-KeyFilePath</span></span>

<span data-ttu-id="2e58c-302">Spécifie un chemin de fichier de clé utilisé par Secure Shell (SSH) pour authentifier un utilisateur sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-302">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="2e58c-303">SSH permet d’effectuer l’authentification des utilisateurs via des clés privées/publiques comme alternative à l’authentification de base par mot de passe.</span><span class="sxs-lookup"><span data-stu-id="2e58c-303">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="2e58c-304">Si l’ordinateur distant est configuré pour l’authentification de clé, ce paramètre peut être utilisé pour fournir la clé qui identifie l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-304">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="2e58c-305">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2e58c-305">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-306">-Name</span><span class="sxs-lookup"><span data-stu-id="2e58c-306">-Name</span></span>

<span data-ttu-id="2e58c-307">Spécifie un nom convivial pour la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-307">Specifies a friendly name for the **PSSession** .</span></span>

<span data-ttu-id="2e58c-308">Vous pouvez utiliser le nom pour faire référence à la **session PSSession** quand vous utilisez d’autres applets de commande, telles que `Get-PSSession` et `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-308">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="2e58c-309">Le nom n'a pas obligatoirement à être unique sur l'ordinateur ou dans la session active.</span><span class="sxs-lookup"><span data-stu-id="2e58c-309">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-310">-Port</span><span class="sxs-lookup"><span data-stu-id="2e58c-310">-Port</span></span>

<span data-ttu-id="2e58c-311">Spécifie le port réseau sur l’ordinateur distant utilisé pour cette connexion.</span><span class="sxs-lookup"><span data-stu-id="2e58c-311">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="2e58c-312">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="2e58c-312">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="2e58c-313">Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-313">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="2e58c-314">Avant d’utiliser un autre port, vous devez configurer l’écouteur WinRM sur l’ordinateur distant pour qu’il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="2e58c-314">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="2e58c-315">Utilisez les commandes suivantes pour configurer l'écouteur :</span><span class="sxs-lookup"><span data-stu-id="2e58c-315">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="2e58c-316">N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="2e58c-316">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="2e58c-317">Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="2e58c-317">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="2e58c-318">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2e58c-318">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-319">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="2e58c-319">-RunAsAdministrator</span></span>

<span data-ttu-id="2e58c-320">Indique que la **session PSSession** s’exécute en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-320">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-321">-Session</span><span class="sxs-lookup"><span data-stu-id="2e58c-321">-Session</span></span>

<span data-ttu-id="2e58c-322">Spécifie un tableau d’objets **PSSession** que cette applet de commande utilise comme modèle pour la nouvelle **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-322">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession** .</span></span> <span data-ttu-id="2e58c-323">Ce paramètre crée de nouveaux objets **PSSession** qui ont les mêmes propriétés que les objets **PSSession** spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2e58c-323">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="2e58c-324">Entrez une variable qui contient les objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu’une `New-PSSession` commande ou `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-324">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="2e58c-325">Les objets **PSSession** qui en résultent ont les mêmes nom d’ordinateur, nom d’application, URI de connexion, port, nom de configuration, limite de limitation et valeur de protocole SSL (SSL) que les originaux, mais ils ont un nom complet, un ID et un ID d’instance (Guid) différents.</span><span class="sxs-lookup"><span data-stu-id="2e58c-325">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-326">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="2e58c-326">-SessionOption</span></span>

<span data-ttu-id="2e58c-327">Spécifie les options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-327">Specifies advanced options for the session.</span></span> <span data-ttu-id="2e58c-328">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-328">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="2e58c-329">Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="2e58c-329">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="2e58c-330">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-330">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="2e58c-331">Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-331">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="2e58c-332">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="2e58c-332">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="2e58c-333">Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="2e58c-333">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="2e58c-334">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="2e58c-334">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="2e58c-335">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="2e58c-335">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-336">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="2e58c-336">-SSHConnection</span></span>

<span data-ttu-id="2e58c-337">Ce paramètre prend un tableau de tables de hachage dans lequel chaque table de hachage contient un ou plusieurs paramètres de connexion nécessaires pour établir une connexion Secure Shell (SSH) (nom d’hôte, port, nom d’utilisateur, KeyFilePath).</span><span class="sxs-lookup"><span data-stu-id="2e58c-337">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath).</span></span>

<span data-ttu-id="2e58c-338">Les paramètres de connexion Hashtable sont les mêmes que ceux définis pour le jeu de paramètres **hostname** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-338">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>

<span data-ttu-id="2e58c-339">Le paramètre **SSHConnection** est utile pour créer plusieurs sessions où chaque session requiert des informations de connexion différentes.</span><span class="sxs-lookup"><span data-stu-id="2e58c-339">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="2e58c-340">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2e58c-340">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-341">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="2e58c-341">-SSHTransport</span></span>

<span data-ttu-id="2e58c-342">Indique que la connexion à distance est établie à l’aide d’Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="2e58c-342">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="2e58c-343">Par défaut, PowerShell utilise Windows WinRM pour se connecter à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-343">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="2e58c-344">Ce commutateur force PowerShell à utiliser le jeu de paramètres HostName pour établir une connexion à distance basée sur SSH.</span><span class="sxs-lookup"><span data-stu-id="2e58c-344">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="2e58c-345">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2e58c-345">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-346">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2e58c-346">-ThrottleLimit</span></span>

<span data-ttu-id="2e58c-347">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="2e58c-347">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="2e58c-348">Si vous omettez ce paramètre ou entrez la valeur 0 (zéro), la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2e58c-348">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="2e58c-349">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-349">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-350">-UserName</span><span class="sxs-lookup"><span data-stu-id="2e58c-350">-UserName</span></span>

<span data-ttu-id="2e58c-351">Spécifie le nom d’utilisateur du compte utilisé pour créer une session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-351">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="2e58c-352">La méthode d’authentification de l’utilisateur dépend de la configuration de Secure Shell (SSH) sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-352">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="2e58c-353">Si SSH est configuré pour l’authentification de base par mot de passe, vous êtes invité à entrer le mot de passe de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-353">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="2e58c-354">Si SSH est configuré pour l’authentification utilisateur basée sur une clé, un chemin d’accès de fichier de clé peut être fourni via le paramètre KeyFilePath et aucune invite de mot de passe n’est générée.</span><span class="sxs-lookup"><span data-stu-id="2e58c-354">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="2e58c-355">Notez que si le fichier de clé de l’utilisateur client se trouve dans un emplacement connu SSH, le paramètre KeyFilePath n’est pas nécessaire pour l’authentification basée sur les clés et l’authentification de l’utilisateur aura lieu automatiquement en fonction du nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-355">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="2e58c-356">Pour plus d’informations, consultez la documentation SSH sur l’authentification des utilisateurs basée sur les clés.</span><span class="sxs-lookup"><span data-stu-id="2e58c-356">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="2e58c-357">Ce paramètre n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2e58c-357">This is not a required parameter.</span></span> <span data-ttu-id="2e58c-358">Si aucun paramètre de nom d’utilisateur n’est spécifié, le nom d’utilisateur actuellement connecté est utilisé pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="2e58c-358">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="2e58c-359">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2e58c-359">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-360">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="2e58c-360">-UseSSL</span></span>

<span data-ttu-id="2e58c-361">Indique que cette applet de commande utilise le protocole SSL pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2e58c-361">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="2e58c-362">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="2e58c-362">By default, SSL is not used.</span></span>

<span data-ttu-id="2e58c-363">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="2e58c-363">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="2e58c-364">Le paramètre **UseSSL** offre une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.</span><span class="sxs-lookup"><span data-stu-id="2e58c-364">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="2e58c-365">Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="2e58c-365">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-366">-VMId</span><span class="sxs-lookup"><span data-stu-id="2e58c-366">-VMId</span></span>

<span data-ttu-id="2e58c-367">Spécifie un tableau d’ID de machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="2e58c-367">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="2e58c-368">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2e58c-368">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="2e58c-369">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="2e58c-369">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-370">-VMName</span><span class="sxs-lookup"><span data-stu-id="2e58c-370">-VMName</span></span>

<span data-ttu-id="2e58c-371">Spécifie un tableau de noms d'ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="2e58c-371">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="2e58c-372">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2e58c-372">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="2e58c-373">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez l' `Get-VM` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2e58c-373">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-374">-Sous-système</span><span class="sxs-lookup"><span data-stu-id="2e58c-374">-Subsystem</span></span>

<span data-ttu-id="2e58c-375">Spécifie le sous-système SSH utilisé pour la nouvelle **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="2e58c-375">Specifies the SSH subsystem used for the new **PSSession** .</span></span>

<span data-ttu-id="2e58c-376">Cela spécifie le sous-système à utiliser sur la cible, tel que défini dans sshd_config.</span><span class="sxs-lookup"><span data-stu-id="2e58c-376">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="2e58c-377">Le sous-système démarre une version spécifique de PowerShell avec des paramètres prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="2e58c-377">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="2e58c-378">Si le sous-système spécifié n’existe pas sur l’ordinateur distant, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="2e58c-378">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="2e58c-379">Si ce paramètre n’est pas utilisé, la valeur par défaut est le sous-système « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="2e58c-379">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

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

### <span data-ttu-id="2e58c-380">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="2e58c-380">-UseWindowsPowerShell</span></span>

<span data-ttu-id="2e58c-381">{{Renseigner la description UseWindowsPowerShell}}</span><span class="sxs-lookup"><span data-stu-id="2e58c-381">{{ Fill UseWindowsPowerShell Description }}</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e58c-382">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e58c-382">CommonParameters</span></span>

<span data-ttu-id="2e58c-383">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2e58c-383">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e58c-384">Pour plus d’informations, consultez about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2e58c-384">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e58c-385">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2e58c-385">INPUTS</span></span>

### <span data-ttu-id="2e58c-386">System. String, System. URI, System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-386">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="2e58c-387">Vous pouvez diriger une chaîne, un URI ou un objet de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2e58c-387">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="2e58c-388">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2e58c-388">OUTPUTS</span></span>

### <span data-ttu-id="2e58c-389">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-389">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="2e58c-390">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2e58c-390">NOTES</span></span>

- <span data-ttu-id="2e58c-391">Cette applet de commande utilise l’infrastructure de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e58c-391">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="2e58c-392">Pour utiliser cette applet de commande, l’ordinateur local et les ordinateurs distants doivent être configurés pour la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e58c-392">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="2e58c-393">Pour plus d'informations, consultez [about_Remote_Requirements](About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e58c-393">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="2e58c-394">Pour créer une **session PSSession** sur l’ordinateur local, démarrez PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="2e58c-394">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="2e58c-395">Lorsque vous avez terminé avec la **session PSSession** , utilisez l' `Remove-PSSession` applet de commande pour supprimer la **session PSSession** et libérer ses ressources.</span><span class="sxs-lookup"><span data-stu-id="2e58c-395">When you are finished with the **PSSession** , use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>
- <span data-ttu-id="2e58c-396">Les jeux de paramètres **hostname** et **SSHConnection** ont été inclus à partir de PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2e58c-396">The **HostName** and **SSHConnection** parameter sets were included starting with PowerShell 6.0.</span></span>
  <span data-ttu-id="2e58c-397">Elles ont été ajoutées pour fournir une communication à distance PowerShell basée sur Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="2e58c-397">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="2e58c-398">SSH et PowerShell sont tous deux pris en charge sur plusieurs plateformes (Windows, Linux, macOS) et la communication à distance PowerShell fonctionne sur ces plateformes où PowerShell et SSH sont installés et configurés.</span><span class="sxs-lookup"><span data-stu-id="2e58c-398">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="2e58c-399">Cela est différent de la version précédente de Windows uniquement qui est basée sur WinRM, et la plupart des fonctionnalités et limitations spécifiques à WinRM ne s’appliquent pas.</span><span class="sxs-lookup"><span data-stu-id="2e58c-399">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="2e58c-400">Par exemple, les quotas basés sur WinRM, les options de session, la configuration de point de terminaison personnalisée et les fonctionnalités de déconnexion/reconnexion ne sont actuellement pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2e58c-400">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="2e58c-401">Pour plus d’informations sur la configuration de la communication à distance SSH de PowerShell, consultez [communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="2e58c-401">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="2e58c-402">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2e58c-402">RELATED LINKS</span></span>

[<span data-ttu-id="2e58c-403">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-403">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="2e58c-404">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-404">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="2e58c-405">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-405">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="2e58c-406">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-406">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="2e58c-407">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-407">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="2e58c-408">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="2e58c-408">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="2e58c-409">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-409">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="2e58c-410">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="2e58c-410">Remove-PSSession</span></span>](Remove-PSSession.md)

