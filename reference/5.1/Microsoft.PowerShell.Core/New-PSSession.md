---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 1835d0bd4294161f83728a63e8da8fc64c2bf9e0
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205382"
---
# <span data-ttu-id="f1bad-103">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-103">New-PSSession</span></span>

## <span data-ttu-id="f1bad-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f1bad-104">SYNOPSIS</span></span>
<span data-ttu-id="f1bad-105">Crée une connexion persistante à un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-105">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="f1bad-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f1bad-106">SYNTAX</span></span>

### <span data-ttu-id="f1bad-107">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f1bad-107">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="f1bad-108">Uri</span><span class="sxs-lookup"><span data-stu-id="f1bad-108">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="f1bad-109">VMId</span><span class="sxs-lookup"><span data-stu-id="f1bad-109">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="f1bad-110">VMName</span><span class="sxs-lookup"><span data-stu-id="f1bad-110">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="f1bad-111">session</span><span class="sxs-lookup"><span data-stu-id="f1bad-111">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="f1bad-112">ContainerId</span><span class="sxs-lookup"><span data-stu-id="f1bad-112">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="f1bad-113">Description</span><span class="sxs-lookup"><span data-stu-id="f1bad-113">DESCRIPTION</span></span>

<span data-ttu-id="f1bad-114">L' `New-PSSession` applet de commande crée une session PowerShell ( **PSSession** ) sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-114">The `New-PSSession` cmdlet creates a PowerShell session ( **PSSession** ) on a local or remote computer.</span></span> <span data-ttu-id="f1bad-115">Lorsque vous créez une **session PSSession** , PowerShell établit une connexion permanente à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-115">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="f1bad-116">Utilisez une **session PSSession** pour exécuter plusieurs commandes qui partagent des données, telles qu’une fonction ou la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-116">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="f1bad-117">Pour exécuter des commandes dans une **session PSSession** , utilisez l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-117">To run commands in a **PSSession** , use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="f1bad-118">Pour utiliser la **session PSSession** pour interagir directement avec un ordinateur distant, utilisez l’applet de commande `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-118">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="f1bad-119">Pour plus d’informations, consultez [about_PSSessions](about/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="f1bad-119">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="f1bad-120">Vous pouvez exécuter des commandes sur un ordinateur distant sans créer de **session PSSession** à l’aide des paramètres **ComputerName** de `Enter-PSSession` ou `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-120">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="f1bad-121">Quand vous utilisez le paramètre **ComputerName** , PowerShell crée une connexion temporaire qui est utilisée pour la commande et qui est ensuite fermée.</span><span class="sxs-lookup"><span data-stu-id="f1bad-121">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

## <span data-ttu-id="f1bad-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f1bad-122">EXAMPLES</span></span>

### <span data-ttu-id="f1bad-123">Exemple 1 : créer une session sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="f1bad-123">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="f1bad-124">Cette commande crée une session **PSSession** sur l’ordinateur local et enregistre la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-124">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="f1bad-125">Vous pouvez maintenant utiliser cette **session PSSession** pour exécuter des commandes sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f1bad-125">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="f1bad-126">Exemple 2 : créer une session sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="f1bad-126">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="f1bad-127">Cette commande crée une **session PSSession** sur l’ordinateur SERVEUR01 et l’enregistre dans la `$Server01` variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-127">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="f1bad-128">Lorsque vous créez plusieurs objets **PSSession** , assignez-les à des variables avec des noms utiles.</span><span class="sxs-lookup"><span data-stu-id="f1bad-128">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="f1bad-129">Cela vous aidera à gérer les objets **PSSession** dans les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f1bad-129">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="f1bad-130">Exemple 3 : créer des sessions sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="f1bad-130">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="f1bad-131">Cette commande crée trois objets **PSSession** , un sur chacun des ordinateurs spécifiés par le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-131">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="f1bad-132">La commande utilise l’opérateur d’assignation (=) pour assigner les nouveaux objets **PSSession** aux variables : `$s1` , `$s2` , `$s3` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-132">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="f1bad-133">Elle attribue la **session** SERVEUR01 à `$s1` , la session **PSSession** Server02 à `$s2` et la **session PSSession** Server03 à `$s3` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-133">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="f1bad-134">Lorsque vous assignez plusieurs objets à une série de variables, PowerShell assigne respectivement chaque objet à une variable de la série.</span><span class="sxs-lookup"><span data-stu-id="f1bad-134">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="f1bad-135">S'il y a plus d'objets que de variables, tous les objets restants sont affectés à la dernière variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-135">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="f1bad-136">S'il y a plus de variables que d'objets, les autres variables sont vides (null).</span><span class="sxs-lookup"><span data-stu-id="f1bad-136">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="f1bad-137">Exemple 4 : créer une session avec un port spécifié</span><span class="sxs-lookup"><span data-stu-id="f1bad-137">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="f1bad-138">Cette commande crée une session **PSSession** sur l’ordinateur SERVEUR01 qui se connecte au port 8081 du serveur et utilise le protocole SSL.</span><span class="sxs-lookup"><span data-stu-id="f1bad-138">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="f1bad-139">La nouvelle session **PSSession** utilise une autre configuration de session appelée E12.</span><span class="sxs-lookup"><span data-stu-id="f1bad-139">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="f1bad-140">Avant de définir le port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant afin d'écouter sur le port 8081.</span><span class="sxs-lookup"><span data-stu-id="f1bad-140">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="f1bad-141">Pour plus d’informations, consultez la description du paramètre de **port** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-141">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="f1bad-142">Exemple 5 : créer une session basée sur une session existante</span><span class="sxs-lookup"><span data-stu-id="f1bad-142">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="f1bad-143">Cette commande crée une **session PSSession** avec les mêmes propriétés qu’une **session PSSession** existante.</span><span class="sxs-lookup"><span data-stu-id="f1bad-143">This command creates a **PSSession** with the same properties as an existing **PSSession** .</span></span> <span data-ttu-id="f1bad-144">Vous pouvez utiliser ce format de commande lorsque les ressources d’une **session PSSession** existante sont épuisées et qu’une nouvelle **session PSSession** est nécessaire pour décharger une partie de la demande.</span><span class="sxs-lookup"><span data-stu-id="f1bad-144">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="f1bad-145">La commande utilise le paramètre **session** de `New-PSSession` pour spécifier la session **PSSession** enregistrée dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-145">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="f1bad-146">Elle utilise les informations d'identification de l'utilisateur Domain1\Admin01 pour terminer la commande.</span><span class="sxs-lookup"><span data-stu-id="f1bad-146">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="f1bad-147">Exemple 6 : créer une session avec une étendue globale dans un autre domaine</span><span class="sxs-lookup"><span data-stu-id="f1bad-147">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="f1bad-148">Cet exemple montre comment créer une **session PSSession** avec une portée globale sur un ordinateur situé dans un autre domaine.</span><span class="sxs-lookup"><span data-stu-id="f1bad-148">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="f1bad-149">Par défaut, les objets **PSSession** créés sur la ligne de commande sont créés avec une portée locale et les objets **PSSession** créés dans un script ont une portée de script.</span><span class="sxs-lookup"><span data-stu-id="f1bad-149">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="f1bad-150">Pour créer une **session PSSession** avec une portée globale, créez une **session** PSSession, puis stockez la **session PSSession** dans une variable qui est convertie en portée globale.</span><span class="sxs-lookup"><span data-stu-id="f1bad-150">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="f1bad-151">Dans ce cas, la `$s` variable est convertie en portée globale.</span><span class="sxs-lookup"><span data-stu-id="f1bad-151">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="f1bad-152">La commande utilise le paramètre **ComputerName** pour spécifier l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-152">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="f1bad-153">Étant donné que l’ordinateur se trouve dans un domaine différent de celui du compte d’utilisateur, le nom complet de l’ordinateur est spécifié avec les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-153">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="f1bad-154">Exemple 7 : créer des sessions pour de nombreux ordinateurs</span><span class="sxs-lookup"><span data-stu-id="f1bad-154">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="f1bad-155">Cette commande crée une session **PSSession** sur chacun des ordinateurs 200 listés dans le fichier Servers.txt et stocke la **session PSSession** résultante dans la `$rs` variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-155">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="f1bad-156">Les objets **PSSession** ont une limite de limitation de 50.</span><span class="sxs-lookup"><span data-stu-id="f1bad-156">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="f1bad-157">Vous pouvez utiliser ce format de commande lorsque les noms des ordinateurs sont stockés dans une base de données, une feuille de calcul, un fichier texte ou tout autre format convertible en texte.</span><span class="sxs-lookup"><span data-stu-id="f1bad-157">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="f1bad-158">Exemple 8 : créer une session à l’aide d’un URI</span><span class="sxs-lookup"><span data-stu-id="f1bad-158">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="f1bad-159">Cette commande crée une **session PSSession** sur l’ordinateur SERVEUR01 et le stocke dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-159">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="f1bad-160">Elle utilise le paramètre **URI** pour spécifier le protocole de transport, l’ordinateur distant, le port et une autre configuration de session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-160">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="f1bad-161">Elle utilise également le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de créer une session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-161">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="f1bad-162">Exemple 9 : exécuter une tâche en arrière-plan dans un ensemble de sessions</span><span class="sxs-lookup"><span data-stu-id="f1bad-162">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="f1bad-163">Ces commandes créent un ensemble d’objets **PSSession** , puis exécutent une tâche en arrière-plan dans chacun des objets **PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-163">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="f1bad-164">La première commande crée une **session PSSession** sur chacun des ordinateurs figurant dans le fichier Servers.txt.</span><span class="sxs-lookup"><span data-stu-id="f1bad-164">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="f1bad-165">Elle utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-165">It uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span> <span data-ttu-id="f1bad-166">La valeur du paramètre **ComputerName** est une commande qui utilise l' `Get-Content` applet de commande pour obtenir la liste des noms d’ordinateur du fichier Servers.txt.</span><span class="sxs-lookup"><span data-stu-id="f1bad-166">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="f1bad-167">La commande utilise le paramètre **Credential** pour créer les objets **PSSession** qui ont l’autorisation d’un administrateur de domaine, et elle utilise le paramètre **ThrottleLimit** pour limiter la commande à 16 connexions simultanées.</span><span class="sxs-lookup"><span data-stu-id="f1bad-167">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="f1bad-168">La commande enregistre les objets **PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-168">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="f1bad-169">La deuxième commande utilise le paramètre **AsJob** de l' `Invoke-Command` applet de commande pour démarrer une tâche en arrière-plan qui exécute une `Get-Process PowerShell` commande dans chacun des objets **PSSession** dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-169">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="f1bad-170">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](About/about_Jobs.md) et [about_Remote_Jobs](About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="f1bad-170">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="f1bad-171">Exemple 10 : créer une session pour un ordinateur à l’aide de son URI</span><span class="sxs-lookup"><span data-stu-id="f1bad-171">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="f1bad-172">Cette commande crée un objet **PSSession** qui se connecte à un ordinateur spécifié par un URI au lieu d’un nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-172">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="f1bad-173">Exemple 11 : créer une option de session</span><span class="sxs-lookup"><span data-stu-id="f1bad-173">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="f1bad-174">Cet exemple montre comment créer un objet d’option de session et utiliser le paramètre **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-174">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="f1bad-175">La première commande utilise l' `New-PSSessionOption` applet de commande pour créer une option de session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-175">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="f1bad-176">Elle enregistre l’objet **SessionOption** résultant dans la `$so` variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-176">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="f1bad-177">La deuxième commande utilise l'option d'une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-177">The second command uses the option in a new session.</span></span> <span data-ttu-id="f1bad-178">La commande utilise l' `New-PSSession` applet de commande pour créer une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-178">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="f1bad-179">La valeur du paramètre SessionOption est l’objet **SessionOption** dans la `$so` variable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-179">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

## <span data-ttu-id="f1bad-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f1bad-180">PARAMETERS</span></span>

### <span data-ttu-id="f1bad-181">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="f1bad-181">-AllowRedirection</span></span>

<span data-ttu-id="f1bad-182">Indique que cette applet de commande autorise la redirection de cette connexion vers un autre Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="f1bad-182">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="f1bad-183">Quand vous utilisez le paramètre **ConnectionURI** , la destination distante peut retourner une instruction pour effectuer une redirection vers un autre URI.</span><span class="sxs-lookup"><span data-stu-id="f1bad-183">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="f1bad-184">Par défaut, PowerShell ne redirige pas les connexions, mais vous pouvez utiliser ce paramètre pour lui permettre de rediriger la connexion.</span><span class="sxs-lookup"><span data-stu-id="f1bad-184">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="f1bad-185">Vous pouvez également limiter le nombre de fois où la connexion est redirigée en modifiant la valeur de l'option de session **MaximumConnectionRedirectionCount** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-185">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="f1bad-186">Utilisez le paramètre **MaximumRedirection** de l' `New-PSSessionOption` applet de commande ou définissez la propriété **MaximumConnectionRedirectionCount** de la variable de préférence **$PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-186">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="f1bad-187">La valeur par défaut est 5.</span><span class="sxs-lookup"><span data-stu-id="f1bad-187">The default value is 5.</span></span>

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

### <span data-ttu-id="f1bad-188">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="f1bad-188">-ApplicationName</span></span>

<span data-ttu-id="f1bad-189">Spécifie le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="f1bad-189">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="f1bad-190">Utilisez ce paramètre pour spécifier le nom de l'application quand vous n'utilisez pas le paramètre **ConnectionURI** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="f1bad-190">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="f1bad-191">La valeur par défaut est la valeur de la `$PSSessionApplicationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f1bad-191">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="f1bad-192">Si cette variable de préférence n'est pas définie, la valeur par défaut est WSMAN.</span><span class="sxs-lookup"><span data-stu-id="f1bad-192">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="f1bad-193">Cette valeur convient pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="f1bad-193">This value is appropriate for most uses.</span></span> <span data-ttu-id="f1bad-194">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f1bad-194">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="f1bad-195">Le service WinRM utilise le nom de l'application pour sélectionner un port d'écoute et traiter la demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="f1bad-195">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="f1bad-196">La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d'un écouteur sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-196">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="f1bad-197">-Authentification</span><span class="sxs-lookup"><span data-stu-id="f1bad-197">-Authentication</span></span>

<span data-ttu-id="f1bad-198">Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-198">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="f1bad-199">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="f1bad-199">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f1bad-200">Default</span><span class="sxs-lookup"><span data-stu-id="f1bad-200">Default</span></span>
- <span data-ttu-id="f1bad-201">Basic</span><span class="sxs-lookup"><span data-stu-id="f1bad-201">Basic</span></span>
- <span data-ttu-id="f1bad-202">CredSSP</span><span class="sxs-lookup"><span data-stu-id="f1bad-202">Credssp</span></span>
- <span data-ttu-id="f1bad-203">Digest</span><span class="sxs-lookup"><span data-stu-id="f1bad-203">Digest</span></span>
- <span data-ttu-id="f1bad-204">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f1bad-204">Kerberos</span></span>
- <span data-ttu-id="f1bad-205">Negotiate</span><span class="sxs-lookup"><span data-stu-id="f1bad-205">Negotiate</span></span>
- <span data-ttu-id="f1bad-206">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="f1bad-206">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="f1bad-207">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="f1bad-207">The default value is Default.</span></span>

<span data-ttu-id="f1bad-208">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="f1bad-208">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="f1bad-209">L’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-209">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="f1bad-210">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="f1bad-210">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="f1bad-211">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="f1bad-211">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="f1bad-212">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="f1bad-212">-CertificateThumbprint</span></span>

<span data-ttu-id="f1bad-213">Spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="f1bad-213">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="f1bad-214">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="f1bad-214">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="f1bad-215">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="f1bad-215">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="f1bad-216">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="f1bad-216">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="f1bad-217">Pour obtenir un certificat, utilisez la `Get-Item` `Get-ChildItem` commande ou dans le lecteur du certificat PowerShell :</span><span class="sxs-lookup"><span data-stu-id="f1bad-217">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="f1bad-218">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f1bad-218">-ComputerName</span></span>

<span data-ttu-id="f1bad-219">Spécifie un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-219">Specifies an array of names of computers.</span></span> <span data-ttu-id="f1bad-220">Cette applet de commande crée une connexion permanente ( **PSSession** ) sur l’ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="f1bad-220">This cmdlet creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="f1bad-221">Si vous entrez plusieurs noms d’ordinateur, `New-PSSession` crée plusieurs objets **PSSession** , un pour chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-221">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="f1bad-222">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f1bad-222">The default is the local computer.</span></span>

<span data-ttu-id="f1bad-223">Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet d'un ou de plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f1bad-223">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="f1bad-224">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.).</span><span class="sxs-lookup"><span data-stu-id="f1bad-224">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="f1bad-225">Lorsque l'ordinateur distant se trouve dans un domaine différent de celui de l'utilisateur, le nom de domaine complet est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f1bad-225">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="f1bad-226">Vous pouvez également diriger un nom d’ordinateur, entre guillemets, vers `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-226">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="f1bad-227">Pour utiliser une adresse IP dans la valeur du paramètre **ComputerName** , la commande doit inclure le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-227">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="f1bad-228">En outre, l'ordinateur doit être configuré pour le transport HTTPS ou l'adresse IP de l'ordinateur distant doit être incluse dans la liste TrustedHosts pour WinRM de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f1bad-228">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="f1bad-229">Pour obtenir des instructions sur l’ajout d’un nom d’ordinateur à la liste TrustedHosts, consultez « Comment ajouter un ordinateur à la liste des hôtes approuvés » dans [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="f1bad-229">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="f1bad-230">Pour inclure l’ordinateur local dans la valeur du paramètre **ComputerName** , démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-230">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

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

### <span data-ttu-id="f1bad-231">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="f1bad-231">-ConfigurationName</span></span>

<span data-ttu-id="f1bad-232">Spécifie la configuration de session utilisée pour la nouvelle session **PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-232">Specifies the session configuration that is used for the new **PSSession** .</span></span>

<span data-ttu-id="f1bad-233">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-233">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="f1bad-234">Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-234">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="f1bad-235">La configuration d'une session se trouve sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-235">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="f1bad-236">Si la configuration de session spécifiée n'existe pas sur l'ordinateur distant, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="f1bad-236">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="f1bad-237">La valeur par défaut est la valeur de la `$PSSessionConfigurationName` variable de préférence sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f1bad-237">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="f1bad-238">Si cette variable de préférence n'est pas définie, la valeur par défaut est Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1bad-238">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="f1bad-239">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f1bad-239">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="f1bad-240">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="f1bad-240">-ConnectionUri</span></span>

<span data-ttu-id="f1bad-241">Spécifie un URI qui définit le point de terminaison de connexion pour la session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-241">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="f1bad-242">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="f1bad-242">The URI must be fully qualified.</span></span> <span data-ttu-id="f1bad-243">Le format de cette chaîne est le suivant :</span><span class="sxs-lookup"><span data-stu-id="f1bad-243">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="f1bad-244">La valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f1bad-244">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="f1bad-245">Si vous ne spécifiez pas un **ConnectionURI** , vous pouvez utiliser les paramètres **UseSSL** , **ComputerName** , **Port** et **ApplicationName** pour spécifier les valeurs **ConnectionURI** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-245">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="f1bad-246">Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f1bad-246">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="f1bad-247">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-247">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="f1bad-248">Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-248">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="f1bad-249">Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="f1bad-249">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="f1bad-250">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="f1bad-250">-ContainerId</span></span>

<span data-ttu-id="f1bad-251">Spécifie un tableau d’ID de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-251">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="f1bad-252">Cette applet de commande démarre une session interactive avec chacun des conteneurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f1bad-252">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="f1bad-253">Utilisez la `docker ps` commande pour obtenir la liste des ID de conteneur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-253">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="f1bad-254">Pour plus d’informations, consultez l’aide de la commande [dockr PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="f1bad-254">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

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

### <span data-ttu-id="f1bad-255">-Credential</span><span class="sxs-lookup"><span data-stu-id="f1bad-255">-Credential</span></span>

<span data-ttu-id="f1bad-256">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="f1bad-256">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="f1bad-257">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="f1bad-257">The default is the current user.</span></span>

<span data-ttu-id="f1bad-258">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-258">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f1bad-259">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f1bad-259">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="f1bad-260">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f1bad-260">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f1bad-261">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="f1bad-261">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="f1bad-262">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="f1bad-262">-EnableNetworkAccess</span></span>

<span data-ttu-id="f1bad-263">Indique que cette applet de commande ajoute un jeton de sécurité interactif aux sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="f1bad-263">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="f1bad-264">Le jeton interactif vous permet d'exécuter des commandes dans la session de bouclage qui obtiennent des données à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-264">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="f1bad-265">Par exemple, vous pouvez exécuter une commande dans la session qui copie les fichiers XML d'un ordinateur distant vers l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f1bad-265">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="f1bad-266">Une session de bouclage est une session **PSSession** qui provient et se termine sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-266">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="f1bad-267">Pour créer une session de bouclage, omettez le paramètre **ComputerName** ou définissez sa valeur sur point (.), localhost ou le nom de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f1bad-267">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="f1bad-268">Par défaut, cette applet de commande crée des sessions de bouclage à l’aide d’un jeton réseau, qui peut ne pas fournir les autorisations suffisantes pour s’authentifier auprès des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f1bad-268">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="f1bad-269">Le paramètre **EnableNetworkAccess** n'est effectif que dans les sessions de bouclage.</span><span class="sxs-lookup"><span data-stu-id="f1bad-269">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="f1bad-270">Si vous utilisez **EnableNetworkAccess** quand vous créez une session sur un ordinateur distant, la commande s’exécute correctement, mais le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="f1bad-270">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="f1bad-271">Vous pouvez également activer l’accès à distance dans une session de bouclage en utilisant la valeur CredSSP du paramètre **Authentication** , qui délègue les informations d’identification de session à d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-271">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="f1bad-272">Pour protéger l’ordinateur contre les accès malveillants, les sessions de bouclage déconnectées qui ont des jetons interactifs, qui sont créés à l’aide du paramètre **EnableNetworkAccess** , peuvent être reconnectées uniquement à partir de l’ordinateur sur lequel la session a été créée.</span><span class="sxs-lookup"><span data-stu-id="f1bad-272">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="f1bad-273">Les sessions déconnectées qui utilisent l'authentification CredSSP peuvent être reconnectées à partir d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-273">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="f1bad-274">Pour plus d'informations, consultez `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="f1bad-274">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="f1bad-275">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f1bad-275">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f1bad-276">-Name</span><span class="sxs-lookup"><span data-stu-id="f1bad-276">-Name</span></span>

<span data-ttu-id="f1bad-277">Spécifie un nom convivial pour la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-277">Specifies a friendly name for the **PSSession** .</span></span>

<span data-ttu-id="f1bad-278">Vous pouvez utiliser le nom pour faire référence à la **session PSSession** quand vous utilisez d’autres applets de commande, telles que `Get-PSSession` et `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-278">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="f1bad-279">Le nom n'a pas obligatoirement à être unique sur l'ordinateur ou dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f1bad-279">The name is not required to be unique to the computer or the current session.</span></span>

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

### <span data-ttu-id="f1bad-280">-Port</span><span class="sxs-lookup"><span data-stu-id="f1bad-280">-Port</span></span>

<span data-ttu-id="f1bad-281">Spécifie le port réseau sur l’ordinateur distant utilisé pour cette connexion.</span><span class="sxs-lookup"><span data-stu-id="f1bad-281">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="f1bad-282">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="f1bad-282">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="f1bad-283">Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-283">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="f1bad-284">Avant d’utiliser un autre port, vous devez configurer l’écouteur WinRM sur l’ordinateur distant pour qu’il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="f1bad-284">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="f1bad-285">Utilisez les commandes suivantes pour configurer l'écouteur :</span><span class="sxs-lookup"><span data-stu-id="f1bad-285">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="f1bad-286">N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="f1bad-286">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="f1bad-287">Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="f1bad-287">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="f1bad-288">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f1bad-288">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1bad-289">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="f1bad-289">-RunAsAdministrator</span></span>

<span data-ttu-id="f1bad-290">Indique que la **session PSSession** s’exécute en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-290">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="f1bad-291">-Session</span><span class="sxs-lookup"><span data-stu-id="f1bad-291">-Session</span></span>

<span data-ttu-id="f1bad-292">Spécifie un tableau d’objets **PSSession** que cette applet de commande utilise comme modèle pour la nouvelle **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="f1bad-292">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession** .</span></span> <span data-ttu-id="f1bad-293">Ce paramètre crée de nouveaux objets **PSSession** qui ont les mêmes propriétés que les objets **PSSession** spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f1bad-293">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="f1bad-294">Entrez une variable qui contient les objets **PSSession** ou une commande qui crée ou obtient les objets **PSSession** , tels qu’une `New-PSSession` commande ou `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-294">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="f1bad-295">Les objets **PSSession** qui en résultent ont les mêmes nom d’ordinateur, nom d’application, URI de connexion, port, nom de configuration, limite de limitation et valeur de protocole SSL (SSL) que les originaux, mais ils ont un nom complet, un ID et un ID d’instance (Guid) différents.</span><span class="sxs-lookup"><span data-stu-id="f1bad-295">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

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

### <span data-ttu-id="f1bad-296">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="f1bad-296">-SessionOption</span></span>

<span data-ttu-id="f1bad-297">Spécifie les options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-297">Specifies advanced options for the session.</span></span> <span data-ttu-id="f1bad-298">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l' `New-PSSessionOption` applet de commande, ou une table de hachage dans laquelle les clés sont des noms d’option de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-298">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="f1bad-299">Les valeurs par défaut des options sont déterminées par la valeur de la `$PSSessionOption` variable de préférence, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="f1bad-299">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="f1bad-300">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-300">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="f1bad-301">Les valeurs d’option de session ont priorité sur les valeurs par défaut des sessions définies dans la `$PSSessionOption` variable de préférence et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-301">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="f1bad-302">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="f1bad-302">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="f1bad-303">Pour obtenir une description des options de session qui incluent les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="f1bad-303">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="f1bad-304">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f1bad-304">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="f1bad-305">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="f1bad-305">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="f1bad-306">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="f1bad-306">-ThrottleLimit</span></span>

<span data-ttu-id="f1bad-307">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="f1bad-307">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="f1bad-308">Si vous omettez ce paramètre ou entrez la valeur 0 (zéro), la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f1bad-308">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="f1bad-309">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-309">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1bad-310">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="f1bad-310">-UseSSL</span></span>

<span data-ttu-id="f1bad-311">Indique que cette applet de commande utilise le protocole SSL pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f1bad-311">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="f1bad-312">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="f1bad-312">By default, SSL is not used.</span></span>

<span data-ttu-id="f1bad-313">WS-Management chiffre tout le contenu PowerShell transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="f1bad-313">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="f1bad-314">Le paramètre **UseSSL** offre une protection supplémentaire qui envoie les données via une connexion HTTPS au lieu d’une connexion http.</span><span class="sxs-lookup"><span data-stu-id="f1bad-314">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="f1bad-315">Si vous utilisez ce paramètre, mais que SSL n’est pas disponible sur le port utilisé pour la commande, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="f1bad-315">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="f1bad-316">-VMId</span><span class="sxs-lookup"><span data-stu-id="f1bad-316">-VMId</span></span>

<span data-ttu-id="f1bad-317">Spécifie un tableau d’ID de machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="f1bad-317">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="f1bad-318">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f1bad-318">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="f1bad-319">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f1bad-319">To see the virtual machines that are available to you, use the following command:</span></span>

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

### <span data-ttu-id="f1bad-320">-VMName</span><span class="sxs-lookup"><span data-stu-id="f1bad-320">-VMName</span></span>

<span data-ttu-id="f1bad-321">Spécifie un tableau de noms d'ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="f1bad-321">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="f1bad-322">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f1bad-322">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="f1bad-323">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez l' `Get-VM` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f1bad-323">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

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

### <span data-ttu-id="f1bad-324">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f1bad-324">CommonParameters</span></span>

<span data-ttu-id="f1bad-325">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f1bad-325">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f1bad-326">Pour plus d’informations, consultez about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f1bad-326">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f1bad-327">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f1bad-327">INPUTS</span></span>

### <span data-ttu-id="f1bad-328">System. String, System. URI, System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-328">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="f1bad-329">Vous pouvez diriger une chaîne, un URI ou un objet de session vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f1bad-329">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="f1bad-330">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f1bad-330">OUTPUTS</span></span>

### <span data-ttu-id="f1bad-331">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-331">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="f1bad-332">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f1bad-332">NOTES</span></span>

- <span data-ttu-id="f1bad-333">Cette applet de commande utilise l’infrastructure de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1bad-333">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="f1bad-334">Pour utiliser cette applet de commande, l’ordinateur local et les ordinateurs distants doivent être configurés pour la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1bad-334">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="f1bad-335">Pour plus d'informations, consultez [about_Remote_Requirements](About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1bad-335">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="f1bad-336">Pour créer une **session PSSession** sur l’ordinateur local, démarrez PowerShell avec l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f1bad-336">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="f1bad-337">Lorsque vous avez terminé avec la **session PSSession** , utilisez l' `Remove-PSSession` applet de commande pour supprimer la **session PSSession** et libérer ses ressources.</span><span class="sxs-lookup"><span data-stu-id="f1bad-337">When you are finished with the **PSSession** , use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>

## <span data-ttu-id="f1bad-338">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f1bad-338">RELATED LINKS</span></span>

[<span data-ttu-id="f1bad-339">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-339">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="f1bad-340">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-340">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="f1bad-341">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-341">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="f1bad-342">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-342">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="f1bad-343">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-343">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="f1bad-344">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f1bad-344">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="f1bad-345">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-345">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="f1bad-346">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="f1bad-346">Remove-PSSession</span></span>](Remove-PSSession.md)
