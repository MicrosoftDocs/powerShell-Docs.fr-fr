---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: 08ca0ec9a45542e86ea197fc24df65430f2d0649
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205678"
---
# <span data-ttu-id="aef9f-103">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-103">Get-PSSession</span></span>

## <span data-ttu-id="aef9f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="aef9f-104">SYNOPSIS</span></span>
<span data-ttu-id="aef9f-105">Obtient les sessions PowerShell sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="aef9f-105">Gets the PowerShell sessions on local and remote computers.</span></span>

## <span data-ttu-id="aef9f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aef9f-106">SYNTAX</span></span>

### <span data-ttu-id="aef9f-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="aef9f-107">Name (Default)</span></span>

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="aef9f-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="aef9f-108">ComputerName</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="aef9f-109">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="aef9f-109">ComputerInstanceId</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="aef9f-110">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="aef9f-110">ConnectionUri</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="aef9f-111">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="aef9f-111">ConnectionUriInstanceId</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="aef9f-112">VMNameInstanceId</span><span class="sxs-lookup"><span data-stu-id="aef9f-112">VMNameInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="aef9f-113">ContainerId</span><span class="sxs-lookup"><span data-stu-id="aef9f-113">ContainerId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="aef9f-114">ContainerIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="aef9f-114">ContainerIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="aef9f-115">VMId</span><span class="sxs-lookup"><span data-stu-id="aef9f-115">VMId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="aef9f-116">VMIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="aef9f-116">VMIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="aef9f-117">VMName</span><span class="sxs-lookup"><span data-stu-id="aef9f-117">VMName</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="aef9f-118">InstanceId</span><span class="sxs-lookup"><span data-stu-id="aef9f-118">InstanceId</span></span>

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### <span data-ttu-id="aef9f-119">Id</span><span class="sxs-lookup"><span data-stu-id="aef9f-119">Id</span></span>

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="aef9f-120">Description</span><span class="sxs-lookup"><span data-stu-id="aef9f-120">DESCRIPTION</span></span>

<span data-ttu-id="aef9f-121">L' `Get-PSSession` applet de commande obtient les sessions PowerShell gérées par l’utilisateur ( **sessions PSSession** ) sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="aef9f-121">The `Get-PSSession` cmdlet gets the user-managed PowerShell sessions ( **PSSessions** ) on local and remote computers.</span></span>

<span data-ttu-id="aef9f-122">À compter de Windows PowerShell 3,0, les sessions sont stockées sur les ordinateurs à l’extrémité distante de chaque connexion.</span><span class="sxs-lookup"><span data-stu-id="aef9f-122">Starting in Windows PowerShell 3.0, sessions are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="aef9f-123">Vous pouvez utiliser les paramètres **ComputerName** ou **ConnectionUri** de `Get-PSSession` pour récupérer les sessions qui se connectent à l’ordinateur local ou aux ordinateurs distants, même s’ils n’ont pas été créés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-123">You can use the **ComputerName** or **ConnectionUri** parameters of `Get-PSSession` to get the sessions that connect to the local computer or remote computers, even if they were not created in the current session.</span></span>

<span data-ttu-id="aef9f-124">Sans paramètres, `Get-PSSession` obtient toutes les sessions qui ont été créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-124">Without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span>

<span data-ttu-id="aef9f-125">Utilisez les paramètres de filtrage, y compris **Name** , **ID** , **InstanceID** , **State** , **applicationName** et **ConfigurationName** , pour effectuer une sélection parmi les sessions `Get-PSSession` retournées par.</span><span class="sxs-lookup"><span data-stu-id="aef9f-125">Use the filtering parameters, including **Name** , **ID** , **InstanceID** , **State** , **ApplicationName** , and **ConfigurationName** to select from among the sessions that `Get-PSSession` returns.</span></span>

<span data-ttu-id="aef9f-126">Utilisez les paramètres restants pour configurer la connexion temporaire dans laquelle la `Get-PSSession` commande s’exécute lorsque vous utilisez les paramètres **ComputerName** ou **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-126">Use the remaining parameters to configure the temporary connection in which the `Get-PSSession` command runs when you use the **ComputerName** or **ConnectionUri** parameters.</span></span>

<span data-ttu-id="aef9f-127">Remarque : dans Windows PowerShell 2,0, sans paramètres, `Get-PSSession` obtient toutes les sessions qui ont été créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-127">NOTE: In Windows PowerShell 2.0, without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span> <span data-ttu-id="aef9f-128">Le paramètre **ComputerName** obtient les sessions qui ont été créées dans la session active et se connecte à l’ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="aef9f-128">The **ComputerName** parameter gets sessions that were created in the current session and connect to the specified computer.</span></span>

<span data-ttu-id="aef9f-129">Pour plus d’informations sur les sessions PowerShell, consultez [about_PSSessions](about/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="aef9f-129">For more information about PowerShell sessions, see [about_PSSessions](about/about_PSSessions.md).</span></span>

## <span data-ttu-id="aef9f-130">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="aef9f-130">EXAMPLES</span></span>

### <span data-ttu-id="aef9f-131">Exemple 1 : accéder aux sessions créées dans la session active</span><span class="sxs-lookup"><span data-stu-id="aef9f-131">Example 1: Get sessions created in the current session</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="aef9f-132">Cette commande obtient toutes les **sessions PSSession** qui ont été créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-132">This command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="aef9f-133">Il n’obtient pas les **sessions PSSession** qui ont été créés dans d’autres sessions ou sur d’autres ordinateurs, même s’ils se connectent à cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aef9f-133">It does not get **PSSessions** that were created in other sessions or on other computers, even if they connect to this computer.</span></span>

### <span data-ttu-id="aef9f-134">Exemple 2 : accéder aux sessions connectées à l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="aef9f-134">Example 2: Get sessions connected to the local computer</span></span>

```powershell
Get-PSSession -ComputerName "localhost"
```

<span data-ttu-id="aef9f-135">Cette commande obtient les **sessions PSSession** qui sont connectés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="aef9f-135">This command gets the **PSSessions** that are connected to the local computer.</span></span> <span data-ttu-id="aef9f-136">Pour indiquer l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.)</span><span class="sxs-lookup"><span data-stu-id="aef9f-136">To indicate the local computer, type the computer name, localhost, or a dot (.)</span></span>

<span data-ttu-id="aef9f-137">La commande retourne toutes les sessions sur l'ordinateur local, même si elles ont été créées dans différentes sessions ou sur des ordinateurs différents.</span><span class="sxs-lookup"><span data-stu-id="aef9f-137">The command returns all of the sessions on the local computer, even if they were created in different sessions or on different computers.</span></span>

### <span data-ttu-id="aef9f-138">Exemple 3 : obtenir des sessions connectées à un ordinateur</span><span class="sxs-lookup"><span data-stu-id="aef9f-138">Example 3: Get sessions connected to a computer</span></span>

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

<span data-ttu-id="aef9f-139">Cette commande obtient les **sessions PSSession** qui sont connectés à l’ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="aef9f-139">This command gets the **PSSessions** that are connected to the Server02 computer.</span></span>

<span data-ttu-id="aef9f-140">La commande retourne toutes les sessions sur Server02, même si elles ont été créées dans différentes sessions ou sur des ordinateurs différents.</span><span class="sxs-lookup"><span data-stu-id="aef9f-140">The command returns all of the sessions on Server02, even if they were created in different sessions or on different computers.</span></span>

<span data-ttu-id="aef9f-141">La sortie montre que deux sessions ont l'état Disconnected et la disponibilité Busy.</span><span class="sxs-lookup"><span data-stu-id="aef9f-141">The output shows that two of the sessions have a Disconnected state and a Busy availability.</span></span> <span data-ttu-id="aef9f-142">Elles ont été créées dans différentes sessions et sont en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="aef9f-142">They were created in different sessions and are currently in use.</span></span> <span data-ttu-id="aef9f-143">La session ScheduledJobs, qui est ouverte et disponible, a été créée dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-143">The ScheduledJobs session, which is Opened and Available, was created in the current session.</span></span>

### <span data-ttu-id="aef9f-144">Exemple 4 : enregistrer les résultats de cette commande</span><span class="sxs-lookup"><span data-stu-id="aef9f-144">Example 4: Save results of this command</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

<span data-ttu-id="aef9f-145">Cet exemple montre comment enregistrer les résultats d’une `Get-PSSession` commande dans plusieurs variables.</span><span class="sxs-lookup"><span data-stu-id="aef9f-145">This example shows how to save the results of a `Get-PSSession` command in multiple variables.</span></span>

<span data-ttu-id="aef9f-146">La première commande utilise l' `New-PSSession` applet de commande pour créer des **sessions PSSession** sur trois ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="aef9f-146">The first command uses the `New-PSSession` cmdlet to create **PSSessions** on three remote computers.</span></span>

<span data-ttu-id="aef9f-147">La deuxième commande utilise une `Get-PSSession` applet de commande pour obtenir les trois **sessions PSSession** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-147">The second command uses a `Get-PSSession` cmdlet to get the three **PSSessions** .</span></span> <span data-ttu-id="aef9f-148">Il enregistre ensuite chaque **sessions PSSession** dans une variable distincte.</span><span class="sxs-lookup"><span data-stu-id="aef9f-148">It then saves each of the **PSSessions** in a separate variable.</span></span>

<span data-ttu-id="aef9f-149">Quand PowerShell assigne un tableau d’objets à un tableau de variables, il assigne le premier objet à la première variable, le deuxième à la deuxième variable, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="aef9f-149">When PowerShell assigns an array of objects to an array of variables, it assigns the first object to the first variable, the second object to the second variable, and so on.</span></span> <span data-ttu-id="aef9f-150">S'il y a plus d'objets que de variables, il affecte tous les autres objets à la dernière variable dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="aef9f-150">If there are more objects than variables, it assigns all remaining objects to the last variable in the array.</span></span> <span data-ttu-id="aef9f-151">S'il y a plus de variables que d'objets, les variables supplémentaires ne sont pas utilisées.</span><span class="sxs-lookup"><span data-stu-id="aef9f-151">If there are more variables than objects, the extra variables are not used.</span></span>

### <span data-ttu-id="aef9f-152">Exemple 5 : supprimer une session à l’aide d’un ID d’instance</span><span class="sxs-lookup"><span data-stu-id="aef9f-152">Example 5: Delete a session by using an instance ID</span></span>

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

<span data-ttu-id="aef9f-153">Cet exemple montre comment obtenir une **session PSSession** à l’aide de son ID d’instance, puis comment supprimer la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-153">This example shows how to get a **PSSession** by using its instance ID, and then to delete the **PSSession** .</span></span>

<span data-ttu-id="aef9f-154">La première commande obtient toutes les **sessions PSSession** qui ont été créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-154">The first command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="aef9f-155">Elle envoie le **sessions PSSession** à l’applet de commande Format-Table, qui affiche les propriétés **ComputerName** et **InstanceID** de chaque **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-155">It sends the **PSSessions** to the Format-Table cmdlet, which displays the **ComputerName** and **InstanceID** properties of each **PSSession** .</span></span>

<span data-ttu-id="aef9f-156">La deuxième commande utilise l' `Get-PSSession` applet de commande pour obtenir une **session PSSession** particulière et l’enregistrer dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="aef9f-156">The second command uses the `Get-PSSession` cmdlet to get a particular **PSSession** and to save it in the `$s` variable.</span></span> <span data-ttu-id="aef9f-157">La commande utilise le paramètre **InstanceID** pour identifier la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-157">The command uses the **InstanceID** parameter to identify the **PSSession** .</span></span>

<span data-ttu-id="aef9f-158">La troisième commande utilise l’applet de commande Remove-PSSession pour supprimer la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="aef9f-158">The third command uses the Remove-PSSession cmdlet to delete the **PSSession** in the `$s` variable.</span></span>

### <span data-ttu-id="aef9f-159">Exemple 6 : obtenir une session portant un nom particulier</span><span class="sxs-lookup"><span data-stu-id="aef9f-159">Example 6: Get a session that has a particular name</span></span>

<span data-ttu-id="aef9f-160">Les commandes de cet exemple montrent comment rechercher une session qui a un format de nom particulier et qui utilise une configuration de session particulière, puis comment se connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-160">The commands in this example find a session that has a particular name format and uses a particular session configuration and then connect to the session.</span></span> <span data-ttu-id="aef9f-161">Vous pouvez utiliser une commande similaire à celle-ci pour rechercher une session dans laquelle un collègue a démarré une tâche et vous connecter pour terminer la tâche.</span><span class="sxs-lookup"><span data-stu-id="aef9f-161">You can use a command like this one to find a session in which a colleague started a task and connect to finish the task.</span></span>

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

<span data-ttu-id="aef9f-162">La première commande obtient les sessions sur les ordinateurs distants Server02 et Server12 dont les noms commencent par BackupJob et utilisent la configuration de session ITTasks. La commande utilise le paramètre **Name** pour spécifier le modèle de nom et le paramètre **ConfigurationName** pour spécifier la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-162">The first command gets sessions on the Server02 and Server12 remote computers that have names that begin with BackupJob and use the ITTasks session configuration.The command uses the **Name** parameter to specify the name pattern and the **ConfigurationName** parameter to specify the session configuration.</span></span> <span data-ttu-id="aef9f-163">La valeur du paramètre **SessionOption** est une table de hachage qui définit la valeur d' **OperationTimeout** sur 240 000 millisecondes (4 minutes).</span><span class="sxs-lookup"><span data-stu-id="aef9f-163">The value of the **SessionOption** parameter is a hash table that sets the value of the **OperationTimeout** to 240000 milliseconds (4 minutes).</span></span> <span data-ttu-id="aef9f-164">Ce paramètre donne plus de temps à la commande. Les paramètres **ConfigurationName** et **SessionOption** sont utilisés pour configurer les sessions temporaires dans lesquelles l’applet de commande `Get-PSSession` s’exécute sur chaque ordinateur. La sortie indique que la commande retourne la session BackupJob04.</span><span class="sxs-lookup"><span data-stu-id="aef9f-164">This setting gives the command more time to complete.The **ConfigurationName** and **SessionOption** parameters are used to configure the temporary sessions in which the `Get-PSSession` cmdlet runs on each computer.The output shows that the command returns the BackupJob04 session.</span></span> <span data-ttu-id="aef9f-165">La session est déconnectée et la **disponibilité** est None, ce qui indique qu’elle n’est pas en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="aef9f-165">The session is disconnected and the **Availability** is None, which indicates that it is not in use.</span></span>

<span data-ttu-id="aef9f-166">La deuxième commande utilise l' `Get-PSSession` applet de commande pour accéder à la session BackupJob04 et l’applet de commande Connect-PSSession pour se connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-166">The second command uses the `Get-PSSession` cmdlet to get to the BackupJob04 session and the Connect-PSSession cmdlet to connect to the session.</span></span> <span data-ttu-id="aef9f-167">La commande enregistre la session dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="aef9f-167">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="aef9f-168">La troisième commande obtient la session stockée dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="aef9f-168">The third command gets the session in the $s variable.</span></span> <span data-ttu-id="aef9f-169">La sortie indique que la `Connect-PSSession` commande a réussi.</span><span class="sxs-lookup"><span data-stu-id="aef9f-169">The output shows that the `Connect-PSSession` command was successful.</span></span> <span data-ttu-id="aef9f-170">La session est dans l'état **Opened** et est utilisable.</span><span class="sxs-lookup"><span data-stu-id="aef9f-170">The session is in the **Opened** state and is available for use.</span></span>

### <span data-ttu-id="aef9f-171">Exemple 7 : obtenir une session à l’aide de son ID</span><span class="sxs-lookup"><span data-stu-id="aef9f-171">Example 7: Get a session by using its ID</span></span>

```powershell
Get-PSSession -Id 2
```

<span data-ttu-id="aef9f-172">Cette commande obtient la **session PSSession** avec l’ID 2.</span><span class="sxs-lookup"><span data-stu-id="aef9f-172">This command gets the **PSSession** with ID 2.</span></span> <span data-ttu-id="aef9f-173">Étant donné que la valeur de la propriété **ID** n’est unique que dans la session active, le paramètre **ID** n’est valide que pour les commandes locales.</span><span class="sxs-lookup"><span data-stu-id="aef9f-173">Because the value of the **ID** property is unique only in the current session, the **Id** parameter is valid only for local commands.</span></span>

## <span data-ttu-id="aef9f-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aef9f-174">PARAMETERS</span></span>

### <span data-ttu-id="aef9f-175">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="aef9f-175">-AllowRedirection</span></span>

<span data-ttu-id="aef9f-176">Indique que cette applet de commande autorise la redirection de cette connexion vers un autre Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="aef9f-176">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="aef9f-177">Par défaut, PowerShell ne redirige pas les connexions.</span><span class="sxs-lookup"><span data-stu-id="aef9f-177">By default, PowerShell does not redirect connections.</span></span>

<span data-ttu-id="aef9f-178">Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-178">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="aef9f-179">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-179">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-180">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="aef9f-180">-ApplicationName</span></span>

<span data-ttu-id="aef9f-181">Spécifie le nom d'une application.</span><span class="sxs-lookup"><span data-stu-id="aef9f-181">Specifies the name of an application.</span></span> <span data-ttu-id="aef9f-182">Cette applet de commande se connecte uniquement aux sessions qui utilisent l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aef9f-182">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="aef9f-183">Entrez le segment de nom d'application de l'URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="aef9f-183">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="aef9f-184">Par exemple, dans l’URI de connexion suivant, le nom de l’application est WSMan : `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="aef9f-184">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="aef9f-185">Le nom d'application d'une session est stocké dans la propriété **Runspace.ConnectionInfo.AppName** de la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-185">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="aef9f-186">La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions.</span><span class="sxs-lookup"><span data-stu-id="aef9f-186">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="aef9f-187">Elle ne modifie pas l'application utilisée par la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-187">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-188">-Authentification</span><span class="sxs-lookup"><span data-stu-id="aef9f-188">-Authentication</span></span>

<span data-ttu-id="aef9f-189">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de la session dans laquelle la `Get-PSSession` commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="aef9f-189">Specifies the mechanism that is used to authenticate credentials for the session in which the `Get-PSSession` command runs.</span></span>

<span data-ttu-id="aef9f-190">Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** ou **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-190">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="aef9f-191">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="aef9f-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="aef9f-192">Default</span><span class="sxs-lookup"><span data-stu-id="aef9f-192">Default</span></span>
- <span data-ttu-id="aef9f-193">Basic</span><span class="sxs-lookup"><span data-stu-id="aef9f-193">Basic</span></span>
- <span data-ttu-id="aef9f-194">CredSSP</span><span class="sxs-lookup"><span data-stu-id="aef9f-194">Credssp</span></span>
- <span data-ttu-id="aef9f-195">Digest</span><span class="sxs-lookup"><span data-stu-id="aef9f-195">Digest</span></span>
- <span data-ttu-id="aef9f-196">Kerberos</span><span class="sxs-lookup"><span data-stu-id="aef9f-196">Kerberos</span></span>
- <span data-ttu-id="aef9f-197">Negotiate</span><span class="sxs-lookup"><span data-stu-id="aef9f-197">Negotiate</span></span>
- <span data-ttu-id="aef9f-198">NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="aef9f-198">NegotiateWithImplicitCredential.</span></span>

<span data-ttu-id="aef9f-199">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="aef9f-199">The default value is Default.</span></span>

<span data-ttu-id="aef9f-200">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism, énumération](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="aef9f-200">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in the MSDN library.</span></span>

<span data-ttu-id="aef9f-201">ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="aef9f-201">CAUTION: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="aef9f-202">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="aef9f-202">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="aef9f-203">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="aef9f-203">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="aef9f-204">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="aef9f-205">-CertificateThumbprint</span></span>

<span data-ttu-id="aef9f-206">Spécifie le certificat de clé publique numérique (x509) d’un compte d’utilisateur qui a l’autorisation de créer la session dans laquelle la `Get-PSSession` commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="aef9f-206">Specifies the digital public key certificate (X509) of a user account that has permission to create the session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="aef9f-207">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="aef9f-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="aef9f-208">Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** ou **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-208">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="aef9f-209">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="aef9f-209">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="aef9f-210">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="aef9f-210">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="aef9f-211">Pour obtenir une empreinte numérique de certificat, utilisez une commande Get-Item ou Get-ChildItem dans le lecteur Cert : PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aef9f-211">To get a certificate thumbprint, use a Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

<span data-ttu-id="aef9f-212">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-212">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-213">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="aef9f-213">-ComputerName</span></span>

<span data-ttu-id="aef9f-214">Spécifie un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="aef9f-214">Specifies an array of names of computers.</span></span> <span data-ttu-id="aef9f-215">Obtient les sessions qui se connectent aux ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-215">Gets the sessions that connect to the specified computers.</span></span>
<span data-ttu-id="aef9f-216">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-216">Wildcard characters are not permitted.</span></span> <span data-ttu-id="aef9f-217">Il n’y a pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="aef9f-217">There is no default value.</span></span>

<span data-ttu-id="aef9f-218">À compter de Windows PowerShell 3,0, les objets **PSSession** sont stockés sur les ordinateurs à l’extrémité distante de chaque connexion.</span><span class="sxs-lookup"><span data-stu-id="aef9f-218">Beginning in Windows PowerShell 3.0, **PSSession** objects are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="aef9f-219">Pour obtenir les sessions sur les ordinateurs spécifiés, PowerShell crée une connexion temporaire à chaque ordinateur et exécute une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="aef9f-219">To get the sessions on the specified computers, PowerShell creates a temporary connection to each computer and runs a `Get-PSSession` command.</span></span>

<span data-ttu-id="aef9f-220">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ou de plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="aef9f-220">Type the NetBIOS name, an IP address, or a fully-qualified domain name of one or more computers.</span></span> <span data-ttu-id="aef9f-221">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, localhost ou un point (.).</span><span class="sxs-lookup"><span data-stu-id="aef9f-221">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

<span data-ttu-id="aef9f-222">Remarque : ce paramètre obtient les sessions uniquement à partir d’ordinateurs qui exécutent Windows PowerShell 3,0 ou des versions ultérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aef9f-222">Note: This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of PowerShell.</span></span> <span data-ttu-id="aef9f-223">Les versions antérieures ne stockent pas de sessions.</span><span class="sxs-lookup"><span data-stu-id="aef9f-223">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-224">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="aef9f-224">-ConfigurationName</span></span>

<span data-ttu-id="aef9f-225">Spécifie le nom d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="aef9f-225">Specifies the name of a configuration.</span></span> <span data-ttu-id="aef9f-226">Cette applet de commande obtient uniquement les sessions qui utilisent la configuration de session spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aef9f-226">This cmdlet gets only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="aef9f-227">Entrez un nom de configuration ou l'URI de ressource complet d'une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-227">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="aef9f-228">Si vous spécifiez uniquement le nom de la configuration, l’URI de schéma suivant est ajouté : `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="aef9f-228">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="aef9f-229">Le nom de configuration d'une session est stocké dans la propriété **ConfigurationName** de la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-229">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="aef9f-230">La valeur de ce paramètre est utilisée pour sélectionner et filtrer les sessions.</span><span class="sxs-lookup"><span data-stu-id="aef9f-230">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="aef9f-231">Elle ne modifie pas la configuration de session utilisée par la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-231">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="aef9f-232">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="aef9f-232">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-233">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="aef9f-233">-ConnectionUri</span></span>

<span data-ttu-id="aef9f-234">Spécifie un URI qui définit le point de terminaison de connexion pour la session temporaire dans laquelle la `Get-PSSession` commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="aef9f-234">Specifies a URI that defines the connection endpoint for the temporary session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="aef9f-235">L’URI doit être complet.</span><span class="sxs-lookup"><span data-stu-id="aef9f-235">The URI must be fully qualified.</span></span>

<span data-ttu-id="aef9f-236">Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-236">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="aef9f-237">Le format de cette chaîne est :</span><span class="sxs-lookup"><span data-stu-id="aef9f-237">The format of this string is:</span></span>

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

<span data-ttu-id="aef9f-238">La valeur par défaut est `http://localhost:5985/WSMAN`.</span><span class="sxs-lookup"><span data-stu-id="aef9f-238">The default value is: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="aef9f-239">Si vous ne spécifiez pas de **ConnectionUri** , vous pouvez utiliser les paramètres **UseSSL** , **ComputerName** , **port** et **applicationName** pour spécifier les valeurs **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-239">If you do not specify a **ConnectionUri** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span> <span data-ttu-id="aef9f-240">Les valeurs valides du segment Transport de l'URI sont HTTP et HTTPS.</span><span class="sxs-lookup"><span data-stu-id="aef9f-240">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="aef9f-241">Si vous spécifiez un URI de connexion avec un segment de transport, mais que vous ne spécifiez pas de port, la session est créée avec les ports standard : 80 pour HTTP et 443 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="aef9f-241">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="aef9f-242">Pour utiliser les ports par défaut pour la communication à distance PowerShell, spécifiez le port 5985 pour HTTP ou 5986 pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="aef9f-242">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="aef9f-243">Si l’ordinateur de destination redirige la connexion vers un autre URI, PowerShell empêche la redirection, sauf si vous utilisez le paramètre **AllowRedirection** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="aef9f-243">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

<span data-ttu-id="aef9f-244">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="aef9f-245">Ce paramètre obtient les sessions uniquement à partir d’ordinateurs qui exécutent Windows PowerShell 3,0 ou des versions ultérieures de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aef9f-245">This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of Windows PowerShell.</span></span> <span data-ttu-id="aef9f-246">Les versions antérieures ne stockent pas de sessions.</span><span class="sxs-lookup"><span data-stu-id="aef9f-246">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-247">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="aef9f-247">-ContainerId</span></span>

<span data-ttu-id="aef9f-248">Spécifie un tableau d’ID de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="aef9f-248">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="aef9f-249">Cette applet de commande démarre une session interactive avec chacun des conteneurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-249">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="aef9f-250">Utilisez la `docker ps` commande pour obtenir la liste des ID de conteneur.</span><span class="sxs-lookup"><span data-stu-id="aef9f-250">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="aef9f-251">Pour plus d’informations, consultez l’aide de la commande [dockr PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="aef9f-251">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-252">-Credential</span><span class="sxs-lookup"><span data-stu-id="aef9f-252">-Credential</span></span>

<span data-ttu-id="aef9f-253">Spécifie les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aef9f-253">Specifies a user credential.</span></span> <span data-ttu-id="aef9f-254">Cette applet de commande exécute la commande avec les autorisations de l’utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="aef9f-254">This cmdlet runs the command with the permissions of the specified user.</span></span> <span data-ttu-id="aef9f-255">Spécifiez un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur distant et d’exécuter une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="aef9f-255">Specify a user account that has permission to connect to the remote computer and run a `Get-PSSession` command.</span></span> <span data-ttu-id="aef9f-256">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="aef9f-256">The default is the current user.</span></span>

<span data-ttu-id="aef9f-257">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="aef9f-257">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="aef9f-258">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="aef9f-258">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="aef9f-259">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="aef9f-259">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="aef9f-260">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="aef9f-260">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="aef9f-261">Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** ou **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-261">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="aef9f-262">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-263">-Id</span><span class="sxs-lookup"><span data-stu-id="aef9f-263">-Id</span></span>

<span data-ttu-id="aef9f-264">Spécifie un tableau d’ID de session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-264">Specifies an array of session IDs.</span></span> <span data-ttu-id="aef9f-265">Cette applet de commande obtient uniquement les sessions avec les ID spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-265">This cmdlet gets only the sessions with the specified IDs.</span></span> <span data-ttu-id="aef9f-266">Tapez un ou plusieurs ID, en les séparant par des virgules, ou utilisez l’opérateur de plage (..) pour spécifier une plage d’ID.</span><span class="sxs-lookup"><span data-stu-id="aef9f-266">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span> <span data-ttu-id="aef9f-267">Vous ne pouvez pas utiliser le paramètre ID avec le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-267">You cannot use the ID parameter together with the **ComputerName** parameter.</span></span>

<span data-ttu-id="aef9f-268">Un ID est un entier qui identifie de façon unique les sessions gérées par l’utilisateur dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-268">An ID is an integer that uniquely identifies the user-managed sessions in the current session.</span></span> <span data-ttu-id="aef9f-269">Il est plus facile à mémoriser et à taper que **InstanceID** , mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-269">It is easier to remember and type than the **InstanceId** , but it is unique only within the current session.</span></span> <span data-ttu-id="aef9f-270">L'ID d'une session est stocké dans la propriété ID de la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-270">The ID of a session is stored in the ID property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-271">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="aef9f-271">-InstanceId</span></span>

<span data-ttu-id="aef9f-272">Spécifie un tableau d’ID d’instance de sessions.</span><span class="sxs-lookup"><span data-stu-id="aef9f-272">Specifies an array of instance IDs of sessions.</span></span> <span data-ttu-id="aef9f-273">Cette applet de commande obtient uniquement les sessions avec les ID d’instance spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-273">This cmdlet gets only the sessions with the specified instance IDs.</span></span>

<span data-ttu-id="aef9f-274">L'ID d'instance est un GUID qui identifie une session sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="aef9f-274">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="aef9f-275">L' **InstanceID** est unique, même si plusieurs sessions sont en cours d’exécution dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aef9f-275">The **InstanceID** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="aef9f-276">L'ID d'instance d'une session est stocké dans la propriété **InstanceID** de la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-276">The instance ID of a session is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId, InstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-277">-Name</span><span class="sxs-lookup"><span data-stu-id="aef9f-277">-Name</span></span>

<span data-ttu-id="aef9f-278">Spécifie un tableau de noms de sessions.</span><span class="sxs-lookup"><span data-stu-id="aef9f-278">Specifies an array of session names.</span></span> <span data-ttu-id="aef9f-279">Cette applet de commande obtient uniquement les sessions qui ont les noms conviviaux spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-279">This cmdlet gets only the sessions that have the specified friendly names.</span></span> <span data-ttu-id="aef9f-280">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-280">Wildcard characters are permitted.</span></span>

<span data-ttu-id="aef9f-281">Le nom convivial d'une session est stocké dans la propriété **Name** de la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-281">The friendly name of a session is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="aef9f-282">-Port</span><span class="sxs-lookup"><span data-stu-id="aef9f-282">-Port</span></span>

<span data-ttu-id="aef9f-283">Spécifie le port réseau spécifié qui est utilisé pour la connexion temporaire dans laquelle la `Get-PSSession` commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="aef9f-283">Specifies the specified network port that is used for the temporary connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="aef9f-284">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="aef9f-284">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="aef9f-285">Les ports par défaut sont 5985, qui est le port WinRM pour HTTP et 5986, qui est le port WinRM pour HTTPs.</span><span class="sxs-lookup"><span data-stu-id="aef9f-285">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="aef9f-286">Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="aef9f-286">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="aef9f-287">Pour configurer l’écouteur, tapez les deux commandes suivantes à l’invite de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="aef9f-287">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="aef9f-288">Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** ou **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-288">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="aef9f-289">N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="aef9f-289">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="aef9f-290">Le **port** défini dans la commande s’applique à tous les ordinateurs ou sessions sur lesquels la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="aef9f-290">The **Port** set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="aef9f-291">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="aef9f-291">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="aef9f-292">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-293">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="aef9f-293">-SessionOption</span></span>

<span data-ttu-id="aef9f-294">Spécifie les options avancées pour la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-294">Specifies advanced options for the session.</span></span> <span data-ttu-id="aef9f-295">Entrez un objet **SessionOption** , tel que celui que vous créez à l’aide de l’applet de commande New-PSSessionOption, ou une table de hachage dans laquelle les clés sont des noms d’options de session et les valeurs sont des valeurs d’option de session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-295">Enter a **SessionOption** object, such as one that you create by using the New-PSSessionOption cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="aef9f-296">Les valeurs par défaut des options sont déterminées par la valeur de la variable de préférence PSSessionOption, si elle est définie.</span><span class="sxs-lookup"><span data-stu-id="aef9f-296">The default values for the options are determined by the value of the $PSSessionOption preference variable, if it is set.</span></span> <span data-ttu-id="aef9f-297">Sinon, les valeurs par défaut sont établies par les options définies dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-297">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="aef9f-298">Les valeurs des options de la session sont prioritaires sur les valeurs par défaut des sessions définies dans la variable de préférence $PSSessionOption et dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-298">The session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="aef9f-299">Elles ne sont cependant pas prioritaires sur les valeurs maximales, les quotas ou les limites définis dans la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-299">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="aef9f-300">Pour obtenir une description des options de session, y compris les valeurs par défaut, consultez `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="aef9f-300">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="aef9f-301">Pour plus d’informations sur la `$PSSessionOption` variable de préférence, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="aef9f-301">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="aef9f-302">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="aef9f-302">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-303">-État</span><span class="sxs-lookup"><span data-stu-id="aef9f-303">-State</span></span>

<span data-ttu-id="aef9f-304">Spécifie un état de session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-304">Specifies a session state.</span></span> <span data-ttu-id="aef9f-305">Cette applet de commande obtient uniquement les sessions dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="aef9f-305">This cmdlet gets only sessions in the specified state.</span></span> <span data-ttu-id="aef9f-306">Les valeurs acceptables pour ce paramètre sont : All, Opened, Disconnected, Closed et Broken.</span><span class="sxs-lookup"><span data-stu-id="aef9f-306">The acceptable values for this parameter are: All, Opened, Disconnected, Closed, and Broken.</span></span> <span data-ttu-id="aef9f-307">La valeur par défaut est All.</span><span class="sxs-lookup"><span data-stu-id="aef9f-307">The default value is All.</span></span>

<span data-ttu-id="aef9f-308">La valeur d'état de session dépend des sessions actives.</span><span class="sxs-lookup"><span data-stu-id="aef9f-308">The session state value is relative to the current sessions.</span></span> <span data-ttu-id="aef9f-309">Les sessions qui n'ont pas été créées dans les sessions actives et qui ne sont pas connectées à la session active ont l'état Disconnected même si elles sont connectées à une autre session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-309">Sessions that were not created in the current sessions and are not connected to the current session have a state of Disconnected even when they are connected to a different session.</span></span>

<span data-ttu-id="aef9f-310">L'état d'une session est stocké dans la propriété **State** de la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-310">The state of a session is stored in the **State** property of the session.</span></span>

<span data-ttu-id="aef9f-311">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-311">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-312">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="aef9f-312">-ThrottleLimit</span></span>

<span data-ttu-id="aef9f-313">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter la `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="aef9f-313">Specifies the maximum number of concurrent connections that can be established to run the `Get-PSSession` command.</span></span> <span data-ttu-id="aef9f-314">Si vous omettez ce paramètre ou entrez la valeur 0 (zéro), la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="aef9f-314">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span> <span data-ttu-id="aef9f-315">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aef9f-315">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="aef9f-316">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-316">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-317">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="aef9f-317">-UseSSL</span></span>

<span data-ttu-id="aef9f-318">Indique que cette applet de commande utilise le protocole protocole SSL (SSL) pour établir la connexion dans laquelle la `Get-PSSession` commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="aef9f-318">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish the connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="aef9f-319">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="aef9f-319">By default, SSL is not used.</span></span> <span data-ttu-id="aef9f-320">Si vous utilisez ce paramètre, mais que SSL n'est pas disponible sur le port utilisé pour la commande, celle-ci échoue.</span><span class="sxs-lookup"><span data-stu-id="aef9f-320">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

<span data-ttu-id="aef9f-321">Ce paramètre configure la connexion temporaire qui est créée pour exécuter une `Get-PSSession` commande avec le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-321">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** parameter.</span></span>

<span data-ttu-id="aef9f-322">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aef9f-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-323">-VMId</span><span class="sxs-lookup"><span data-stu-id="aef9f-323">-VMId</span></span>

<span data-ttu-id="aef9f-324">Spécifie un tableau d’ID de machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="aef9f-324">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="aef9f-325">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-325">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="aef9f-326">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="aef9f-326">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-327">-VMName</span><span class="sxs-lookup"><span data-stu-id="aef9f-327">-VMName</span></span>

<span data-ttu-id="aef9f-328">Spécifie un tableau de noms d'ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="aef9f-328">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="aef9f-329">Cette applet de commande démarre une session interactive avec chacun des ordinateurs virtuels spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aef9f-329">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="aef9f-330">Pour afficher les ordinateurs virtuels qui sont à votre disposition, utilisez l' `Get-VM` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aef9f-330">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, VMNameInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aef9f-331">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aef9f-331">CommonParameters</span></span>

<span data-ttu-id="aef9f-332">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aef9f-332">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aef9f-333">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aef9f-333">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aef9f-334">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="aef9f-334">INPUTS</span></span>

### <span data-ttu-id="aef9f-335">Aucun</span><span class="sxs-lookup"><span data-stu-id="aef9f-335">None</span></span>

<span data-ttu-id="aef9f-336">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="aef9f-336">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="aef9f-337">SORTIES</span><span class="sxs-lookup"><span data-stu-id="aef9f-337">OUTPUTS</span></span>

### <span data-ttu-id="aef9f-338">System. Management. Automation. instances d’exécution. PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-338">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="aef9f-339">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="aef9f-339">NOTES</span></span>

- <span data-ttu-id="aef9f-340">Cette applet de commande obtient les objets **PSSession** des sessions gérées par l’utilisateur, telles que celles qui sont créées à l’aide des applets de commande New-PSSession, `Enter-PSSession` et Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="aef9f-340">This cmdlet gets user-managed sessions **PSSession** objects" such as those that are created by using the New-PSSession, `Enter-PSSession`, and Invoke-Command cmdlets.</span></span> <span data-ttu-id="aef9f-341">Elle n’obtient pas la session gérée par le système qui est créée lorsque vous démarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aef9f-341">It does not get the system-managed session that is created when you start PowerShell.</span></span>
- <span data-ttu-id="aef9f-342">À compter de Windows PowerShell 3,0, les objets **PSSession** sont stockés sur l’ordinateur qui se trouve sur le côté serveur ou reçoit la fin d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="aef9f-342">Starting in Windows PowerShell 3.0, **PSSession** objects are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="aef9f-343">Pour obtenir les sessions qui sont stockées sur l’ordinateur local ou sur un ordinateur distant, PowerShell établit une session temporaire sur l’ordinateur spécifié et exécute des commandes de requête dans la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-343">To get the sessions that are stored on the local computer or a remote computer, PowerShell establishes a temporary session to the specified computer and runs query commands in the session.</span></span>
- <span data-ttu-id="aef9f-344">Pour obtenir les sessions qui se connectent à un ordinateur distant, utilisez les paramètres **ComputerName** ou **ConnectionUri** pour spécifier l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="aef9f-344">To get sessions that connect to a remote computer, use the **ComputerName** or **ConnectionUri** parameters to specify the remote computer.</span></span> <span data-ttu-id="aef9f-345">Pour filtrer les sessions que `Get-PSSession` obtient, utilisez les paramètres **Name** , **ID** , **InstanceID** et **State** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-345">To filter the sessions that `Get-PSSession` gets, use the **Name** , **ID** , **InstanceID** , and **State** parameters.</span></span> <span data-ttu-id="aef9f-346">Utilisez les paramètres restants pour configurer la session temporaire qui `Get-PSSession` utilise.</span><span class="sxs-lookup"><span data-stu-id="aef9f-346">Use the remaining parameters to configure the temporary session that `Get-PSSession` uses.</span></span>
- <span data-ttu-id="aef9f-347">Lorsque vous utilisez les paramètres **ComputerName** ou **ConnectionUri** , `Get-PSSession` obtient uniquement les sessions d’ordinateurs exécutant Windows PowerShell 3,0 et les versions ultérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aef9f-347">When you use the **ComputerName** or **ConnectionUri** parameters, `Get-PSSession` gets only sessions from computers running Windows PowerShell 3.0 and later versions of PowerShell.</span></span>
- <span data-ttu-id="aef9f-348">La valeur de la propriété **State** d’une session **PSSession** est relative à la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-348">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="aef9f-349">Par conséquent, la valeur **Disconnected** signifie que la session **PSSession** n’est pas connectée à la session active.</span><span class="sxs-lookup"><span data-stu-id="aef9f-349">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="aef9f-350">Toutefois, cela ne signifie pas que la **session PSSession** est déconnectée de toutes les sessions.</span><span class="sxs-lookup"><span data-stu-id="aef9f-350">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="aef9f-351">Elle peut être connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-351">It might be connected to a different session.</span></span> <span data-ttu-id="aef9f-352">Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session **PSSession** à partir de la session active, utilisez la propriété **Availability** .</span><span class="sxs-lookup"><span data-stu-id="aef9f-352">To determine whether you can connect or reconnect to the **PSSession** from the current session, use the **Availability** property.</span></span>

<span data-ttu-id="aef9f-353">Une propriété **Availability** avec la valeur **None** signifie que vous pouvez vous connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-353">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="aef9f-354">La valeur **Busy** indique que vous ne pouvez pas vous connecter à la session **PSSession** , car elle est connectée à une autre session.</span><span class="sxs-lookup"><span data-stu-id="aef9f-354">A value of **Busy** indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

<span data-ttu-id="aef9f-355">Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [énumération RunspaceState](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="aef9f-355">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate).</span></span>

<span data-ttu-id="aef9f-356">Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [énumération RunspaceAvailability](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="aef9f-356">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="aef9f-357">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="aef9f-357">RELATED LINKS</span></span>

[<span data-ttu-id="aef9f-358">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-358">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="aef9f-359">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-359">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="aef9f-360">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-360">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="aef9f-361">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-361">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="aef9f-362">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-362">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="aef9f-363">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="aef9f-363">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="aef9f-364">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-364">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="aef9f-365">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="aef9f-365">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="aef9f-366">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="aef9f-366">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="aef9f-367">about_Remote</span><span class="sxs-lookup"><span data-stu-id="aef9f-367">about_Remote</span></span>](About/about_Remote.md)

