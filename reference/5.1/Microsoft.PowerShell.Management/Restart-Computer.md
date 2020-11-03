---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 553b61c9669afab325e9feec101d701c2b9a7c83
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205418"
---
# <span data-ttu-id="aba35-103">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="aba35-103">Restart-Computer</span></span>

## <span data-ttu-id="aba35-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="aba35-104">SYNOPSIS</span></span>
<span data-ttu-id="aba35-105">Redémarre le système d’exploitation sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="aba35-105">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="aba35-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aba35-106">SYNTAX</span></span>

### <span data-ttu-id="aba35-107">DefaultSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="aba35-107">DefaultSet (Default)</span></span>

```
Restart-Computer [-DcomAuthentication <AuthenticationLevel>] [-Impersonation <ImpersonationLevel>]
 [-WsmanAuthentication <String>] [-Protocol <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aba35-108">AsJobSet</span><span class="sxs-lookup"><span data-stu-id="aba35-108">AsJobSet</span></span>

```
Restart-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>]
 [-Impersonation <ImpersonationLevel>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Force] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aba35-109">Description</span><span class="sxs-lookup"><span data-stu-id="aba35-109">DESCRIPTION</span></span>

<span data-ttu-id="aba35-110">L' `Restart-Computer` applet de commande redémarre le système d’exploitation sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="aba35-110">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="aba35-111">Vous pouvez utiliser les paramètres de `Restart-Computer` pour exécuter les opérations de redémarrage en tant que tâche en arrière-plan, spécifier les niveaux d’authentification et d’autres informations d’identification, pour limiter les opérations qui s’exécutent en même temps et pour forcer un redémarrage immédiat.</span><span class="sxs-lookup"><span data-stu-id="aba35-111">You can use the parameters of `Restart-Computer` to run the restart operations as a background job, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="aba35-112">À partir de Windows PowerShell 3,0, vous pouvez attendre la fin du redémarrage avant d’exécuter la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="aba35-112">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="aba35-113">Spécifiez un délai d’attente et un intervalle de requête, puis attendez que certains services soient disponibles sur l’ordinateur redémarré.</span><span class="sxs-lookup"><span data-stu-id="aba35-113">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="aba35-114">Cette fonctionnalité facilite `Restart-Computer` l’utilisation de dans les scripts et les fonctions.</span><span class="sxs-lookup"><span data-stu-id="aba35-114">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

<span data-ttu-id="aba35-115">Vous pouvez utiliser le protocole WS-Management (WSMan) pour redémarrer l’ordinateur, dans le cas où les appels DCOM (Distributed Component Object Model) sont bloqués, par exemple par un pare-feu d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="aba35-115">You can use the WS-Management (WSMan) protocol to restart the computer, in case Distributed Component Object Model (DCOM) calls are blocked, such as by an enterprise firewall.</span></span> <span data-ttu-id="aba35-116">Pour plus d’informations, consultez [protocole WS-Management](/windows/desktop/WinRM/ws-management-protocol).</span><span class="sxs-lookup"><span data-stu-id="aba35-116">For more information, see [WS-Management Protocol](/windows/desktop/WinRM/ws-management-protocol).</span></span>

<span data-ttu-id="aba35-117">Cette applet de commande requiert uniquement la communication à distance Windows PowerShell lorsque vous utilisez le paramètre **AsJob** dans une commande.</span><span class="sxs-lookup"><span data-stu-id="aba35-117">This cmdlet requires Windows PowerShell remoting only when you use the **AsJob** parameter in a command.</span></span>

## <span data-ttu-id="aba35-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="aba35-118">EXAMPLES</span></span>

### <span data-ttu-id="aba35-119">Exemple 1 : redémarrer l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="aba35-119">Example 1: Restart the local computer</span></span>

<span data-ttu-id="aba35-120">`Restart-Computer` redémarre l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="aba35-120">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="aba35-121">Exemple 2 : redémarrer plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="aba35-121">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="aba35-122">`Restart-Computer` peut redémarrer les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="aba35-122">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="aba35-123">Le paramètre **ComputerName** accepte un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="aba35-123">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="aba35-124">Exemple 3 : redémarrer les ordinateurs en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="aba35-124">Example 3: Restart computers as a background job</span></span>

<span data-ttu-id="aba35-125">Ces commandes exécutent une `Restart-Computer` commande en tant que tâche en arrière-plan sur deux ordinateurs distants, puis obtiennent les résultats.</span><span class="sxs-lookup"><span data-stu-id="aba35-125">These commands run a `Restart-Computer` command as a background job on two remote computers, and then get the results.</span></span>

<span data-ttu-id="aba35-126">Étant donné que **AsJob** crée la tâche sur l’ordinateur local et retourne automatiquement les résultats à l’ordinateur local, vous pouvez exécuter `Receive-Job` en tant que commande locale.</span><span class="sxs-lookup"><span data-stu-id="aba35-126">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

```powershell
$Job = Restart-Computer -ComputerName "Server01", "Server02" -AsJob
$Job | Receive-Job
```

<span data-ttu-id="aba35-127">`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier **SERVEUR01** et **Server02** .</span><span class="sxs-lookup"><span data-stu-id="aba35-127">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** and **Server02** .</span></span> <span data-ttu-id="aba35-128">Le paramètre **AsJob** exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="aba35-128">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="aba35-129">L’objet de traitement est stocké dans la `$Job` variable.</span><span class="sxs-lookup"><span data-stu-id="aba35-129">The job object is stored in the `$Job` variable.</span></span> <span data-ttu-id="aba35-130">`$Job` est envoyé par le pipeline à l’applet de commande `Receive-Job` qui obtient les résultats.</span><span class="sxs-lookup"><span data-stu-id="aba35-130">`$Job` is sent down the pipeline to the `Receive-Job` cmdlet that gets the results.</span></span>

### <span data-ttu-id="aba35-131">Exemple 4 : redémarrer un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="aba35-131">Example 4: Restart a remote computer</span></span>

<span data-ttu-id="aba35-132">`Restart-Computer` redémarre un ordinateur distant avec des paramètres d’authentification et d’emprunt d’identité personnalisés.</span><span class="sxs-lookup"><span data-stu-id="aba35-132">`Restart-Computer` restarts a remote computer with customized impersonation and authentication settings.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="aba35-133">`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="aba35-133">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** .</span></span> <span data-ttu-id="aba35-134">Le paramètre d' **emprunt d’identité** spécifie anonyme pour masquer l’identité du demandeur.</span><span class="sxs-lookup"><span data-stu-id="aba35-134">The **Impersonation** parameter specifies Anonymous to hide the requester's identity.</span></span> <span data-ttu-id="aba35-135">Le paramètre **DcomAuthentication** spécifie PacketIntegrity comme niveau d’authentification de la connexion.</span><span class="sxs-lookup"><span data-stu-id="aba35-135">The **DcomAuthentication** parameter specifies PacketIntegrity as the connection's authentication level.</span></span>

### <span data-ttu-id="aba35-136">Exemple 5 : forcer le redémarrage des ordinateurs listés dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="aba35-136">Example 5: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="aba35-137">Cet exemple force un redémarrage immédiat des ordinateurs listés dans le `Domain01.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="aba35-137">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="aba35-138">Les noms d’ordinateurs du fichier texte sont stockés dans une variable.</span><span class="sxs-lookup"><span data-stu-id="aba35-138">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="aba35-139">Le paramètre **force** force un redémarrage immédiat et le paramètre **ThrottleLimit** limite le nombre de connexions simultanées.</span><span class="sxs-lookup"><span data-stu-id="aba35-139">The **Force** parameter forces an immediate restart and the **ThrottleLimit** parameter limits the number of concurrent connections.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force -ThrottleLimit 10
```

<span data-ttu-id="aba35-140">`Get-Content` utilise le paramètre **path** pour obtenir une liste de noms d’ordinateurs à partir d’un fichier texte, **Domain01.txt** .</span><span class="sxs-lookup"><span data-stu-id="aba35-140">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt** .</span></span> <span data-ttu-id="aba35-141">Les noms des ordinateurs sont stockés dans la variable `$Names` .</span><span class="sxs-lookup"><span data-stu-id="aba35-141">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="aba35-142">`Get-Credential` vous invite à entrer un nom d’utilisateur et un mot de passe, et stocke les valeurs dans la variable `$Creds` .</span><span class="sxs-lookup"><span data-stu-id="aba35-142">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="aba35-143">`Restart-Computer` utilise les paramètres **ComputerName** et **Credential** avec leurs variables.</span><span class="sxs-lookup"><span data-stu-id="aba35-143">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="aba35-144">Le paramètre **force** provoque un redémarrage immédiat de chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-144">The **Force** parameter causes an immediate restart of each computer.</span></span> <span data-ttu-id="aba35-145">Le paramètre **ThrottleLimit** limite la commande à 10 connexions simultanées.</span><span class="sxs-lookup"><span data-stu-id="aba35-145">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span>

### <span data-ttu-id="aba35-146">Exemple 6 : redémarrer un ordinateur distant et attendre PowerShell</span><span class="sxs-lookup"><span data-stu-id="aba35-146">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="aba35-147">`Restart-Computer` redémarre l’ordinateur distant, puis attend jusqu’à 5 minutes (300 secondes) que PowerShell soit disponible sur l’ordinateur redémarré avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="aba35-147">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="aba35-148">`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="aba35-148">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** .</span></span> <span data-ttu-id="aba35-149">Le paramètre **Wait** attend la fin du redémarrage.</span><span class="sxs-lookup"><span data-stu-id="aba35-149">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="aba35-150">**Pour** spécifie que PowerShell peut exécuter des commandes sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="aba35-150">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="aba35-151">Le paramètre **timeout** spécifie une attente de cinq minutes.</span><span class="sxs-lookup"><span data-stu-id="aba35-151">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="aba35-152">Le paramètre **delay** interroge l’ordinateur distant toutes les deux secondes pour déterminer s’il est redémarré.</span><span class="sxs-lookup"><span data-stu-id="aba35-152">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="aba35-153">Exemple 7 : redémarrer un ordinateur à l’aide du protocole WSMan</span><span class="sxs-lookup"><span data-stu-id="aba35-153">Example 7: Restart a computer by using the WSMan Protocol</span></span>

<span data-ttu-id="aba35-154">`Restart-Computer` redémarre l’ordinateur distant à l’aide du protocole WSMan au lieu du protocole par défaut DCOM.</span><span class="sxs-lookup"><span data-stu-id="aba35-154">`Restart-Computer` restarts the remote computer by using the WSMan protocol instead of the default, DCOM.</span></span> <span data-ttu-id="aba35-155">L’authentification Kerberos détermine si l’utilisateur actuel est autorisé à redémarrer l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="aba35-155">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span>

<span data-ttu-id="aba35-156">Ces paramètres sont conçus pour les entreprises dans lesquelles les redémarrages basés sur DCOM échouent, car DCOM est bloqué.</span><span class="sxs-lookup"><span data-stu-id="aba35-156">These settings are designed for enterprises in which DCOM-based restarts fail because DCOM is blocked.</span></span> <span data-ttu-id="aba35-157">Par exemple, par un pare-feu.</span><span class="sxs-lookup"><span data-stu-id="aba35-157">For example, by a firewall.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Protocol WSMan -WsmanAuthentication Kerberos
```

<span data-ttu-id="aba35-158">`Restart-Computer` utilise le paramètre **ComputerName** pour spécifier l’ordinateur distant **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="aba35-158">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01** .</span></span>
<span data-ttu-id="aba35-159">Le paramètre **Protocol** spécifie d’utiliser le protocole WSMan.</span><span class="sxs-lookup"><span data-stu-id="aba35-159">The **Protocol** parameter specifies to use the WSMan protocol.</span></span> <span data-ttu-id="aba35-160">Le paramètre **WsmanAuthentication** spécifie la méthode d’authentification comme **Kerberos** .</span><span class="sxs-lookup"><span data-stu-id="aba35-160">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos** .</span></span>

## <span data-ttu-id="aba35-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aba35-161">PARAMETERS</span></span>

### <span data-ttu-id="aba35-162">-AsJob</span><span class="sxs-lookup"><span data-stu-id="aba35-162">-AsJob</span></span>

<span data-ttu-id="aba35-163">Indique que `Restart-Computer` s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="aba35-163">Indicates that `Restart-Computer` runs as a background job.</span></span>

<span data-ttu-id="aba35-164">Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="aba35-164">To use this parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="aba35-165">Sur Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="aba35-165">On Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as Administrator** option.</span></span> <span data-ttu-id="aba35-166">Pour plus d'informations, consultez [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aba35-166">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="aba35-167">Lorsque vous spécifiez le paramètre **AsJob** , la commande retourne immédiatement un objet qui représente la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="aba35-167">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="aba35-168">Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="aba35-168">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="aba35-169">La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="aba35-169">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="aba35-170">Pour gérer le travail, utilisez les applets de commande **Job** .</span><span class="sxs-lookup"><span data-stu-id="aba35-170">To manage the job, use the **Job** cmdlets.</span></span> <span data-ttu-id="aba35-171">Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="aba35-171">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="aba35-172">Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="aba35-172">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-173">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="aba35-173">-ComputerName</span></span>

<span data-ttu-id="aba35-174">Spécifie un nom d’ordinateur ou un tableau de noms d’ordinateurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="aba35-174">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="aba35-175">`Restart-Computer` accepte les objets **ComputerName** du ou des variables.</span><span class="sxs-lookup"><span data-stu-id="aba35-175">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="aba35-176">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="aba35-176">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="aba35-177">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point `.` ou localhost.</span><span class="sxs-lookup"><span data-stu-id="aba35-177">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="aba35-178">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aba35-178">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="aba35-179">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="aba35-179">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="aba35-180">Si le paramètre **ComputerName** n’est pas spécifié, `Restart-Computer` redémarre l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="aba35-180">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="aba35-181">-Credential</span></span>

<span data-ttu-id="aba35-182">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="aba35-182">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="aba35-183">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="aba35-183">The default is the current user.</span></span>

<span data-ttu-id="aba35-184">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="aba35-184">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="aba35-185">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="aba35-185">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="aba35-186">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="aba35-186">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="aba35-187">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="aba35-187">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-188">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="aba35-188">-DcomAuthentication</span></span>

<span data-ttu-id="aba35-189">Spécifie le niveau d’authentification utilisé pour la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="aba35-189">Specifies the authentication level that is used for the WMI connection.</span></span> <span data-ttu-id="aba35-190">`Restart-Computer` utilise WMI.</span><span class="sxs-lookup"><span data-stu-id="aba35-190">`Restart-Computer` uses WMI.</span></span>

<span data-ttu-id="aba35-191">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="aba35-191">Valid values are:</span></span>

- <span data-ttu-id="aba35-192">**Appel** : authentification com au niveau de l’appel</span><span class="sxs-lookup"><span data-stu-id="aba35-192">**Call** :            Call-level COM authentication</span></span>
- <span data-ttu-id="aba35-193">**Connect** : authentification com au niveau de la connexion</span><span class="sxs-lookup"><span data-stu-id="aba35-193">**Connect** :         Connect-level COM authentication</span></span>
- <span data-ttu-id="aba35-194">**Par défaut** : authentification Windows</span><span class="sxs-lookup"><span data-stu-id="aba35-194">**Default** :         Windows Authentication</span></span>
- <span data-ttu-id="aba35-195">**None** : aucune authentification com</span><span class="sxs-lookup"><span data-stu-id="aba35-195">**None** :            No COM authentication</span></span>
- <span data-ttu-id="aba35-196">**Paquet** : authentification com au niveau du paquet.</span><span class="sxs-lookup"><span data-stu-id="aba35-196">**Packet** :          Packet-level COM authentication.</span></span>
- <span data-ttu-id="aba35-197">**PacketIntegrity** : authentification com au niveau de l’intégrité du paquet</span><span class="sxs-lookup"><span data-stu-id="aba35-197">**PacketIntegrity** : Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="aba35-198">**PacketPrivacy** : authentification com au niveau de la confidentialité des paquets.</span><span class="sxs-lookup"><span data-stu-id="aba35-198">**PacketPrivacy** :   Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="aba35-199">**Inchangé** : le niveau d’authentification est le même que la commande précédente.</span><span class="sxs-lookup"><span data-stu-id="aba35-199">**Unchanged** :       The authentication level is the same as the previous command.</span></span>

<span data-ttu-id="aba35-200">Pour plus d’informations, consultez [énumération AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).</span><span class="sxs-lookup"><span data-stu-id="aba35-200">For more information, see [AuthenticationLevel Enumeration](/dotnet/api/system.management.authenticationlevel).</span></span>

<span data-ttu-id="aba35-201">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aba35-201">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-202">-Délai</span><span class="sxs-lookup"><span data-stu-id="aba35-202">-Delay</span></span>

<span data-ttu-id="aba35-203">Spécifie la fréquence des requêtes, en secondes.</span><span class="sxs-lookup"><span data-stu-id="aba35-203">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="aba35-204">PowerShell interroge le service spécifié par le paramètre **for** pour déterminer si le service est disponible après le redémarrage de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-204">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="aba35-205">Ce paramètre est valide uniquement avec les paramètres **Wait** et **for** .</span><span class="sxs-lookup"><span data-stu-id="aba35-205">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="aba35-206">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aba35-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="aba35-207">Si le paramètre **delay** n’est pas spécifié, `Restart-Computer` utilise un délai de cinq secondes.</span><span class="sxs-lookup"><span data-stu-id="aba35-207">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-208">-Pour</span><span class="sxs-lookup"><span data-stu-id="aba35-208">-For</span></span>

<span data-ttu-id="aba35-209">Spécifie le comportement de PowerShell, car il attend que le service ou la fonctionnalité spécifié soit disponible après le redémarrage de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-209">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="aba35-210">Ce paramètre est valide uniquement avec le paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="aba35-210">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="aba35-211">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="aba35-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="aba35-212">**Default** : attend le redémarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aba35-212">**Default** : Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="aba35-213">**PowerShell** : peut exécuter des commandes dans une session à distance PowerShell sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-213">**PowerShell** : Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="aba35-214">**WMI** : reçoit une réponse à une requête de Win32_ComputerSystem pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-214">**WMI** : Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="aba35-215">**WinRM** : peut établir une session à distance sur l’ordinateur à l’aide de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="aba35-215">**WinRM** : Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="aba35-216">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aba35-216">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: DefaultSet
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-217">-Force</span><span class="sxs-lookup"><span data-stu-id="aba35-217">-Force</span></span>

<span data-ttu-id="aba35-218">Force un redémarrage immédiat de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-218">Forces an immediate restart of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-219">-Emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="aba35-219">-Impersonation</span></span>

<span data-ttu-id="aba35-220">Spécifie le niveau d’emprunt d’identité utilisé par cette applet de commande pour appeler WMI.</span><span class="sxs-lookup"><span data-stu-id="aba35-220">Specifies the impersonation level that this cmdlet uses to call WMI.</span></span> <span data-ttu-id="aba35-221">`Restart-Computer` utilise WMI.</span><span class="sxs-lookup"><span data-stu-id="aba35-221">`Restart-Computer` uses WMI.</span></span>
<span data-ttu-id="aba35-222">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="aba35-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="aba35-223">**Default** : emprunt d’identité par défaut.</span><span class="sxs-lookup"><span data-stu-id="aba35-223">**Default** : Default impersonation.</span></span> <span data-ttu-id="aba35-224">En dépit du nom, il ne s’agit pas de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="aba35-224">Despite the name, this isn't the default value.</span></span>
- <span data-ttu-id="aba35-225">**Anonymous** : masque l’identité de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="aba35-225">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="aba35-226">**Identify** : permet aux objets d’interroger les informations d’identification de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="aba35-226">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="aba35-227">**Impersonate** : permet aux objets d’utiliser les informations d’identification de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="aba35-227">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-228">-Protocol</span><span class="sxs-lookup"><span data-stu-id="aba35-228">-Protocol</span></span>

<span data-ttu-id="aba35-229">Spécifie le protocole à utiliser pour redémarrer les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="aba35-229">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="aba35-230">Les valeurs valides sont **WSMan** et **DCOM** .</span><span class="sxs-lookup"><span data-stu-id="aba35-230">The valid values are **WSMan** and **DCOM** .</span></span>

<span data-ttu-id="aba35-231">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aba35-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-232">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="aba35-232">-ThrottleLimit</span></span>

<span data-ttu-id="aba35-233">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="aba35-233">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="aba35-234">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-234">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="aba35-235">Si le paramètre **ThrottleLimit** n’est pas spécifié ou si la valeur 0 est utilisée, `Restart-Computer` utilise un maximum de 32 connexions simultanées.</span><span class="sxs-lookup"><span data-stu-id="aba35-235">If the **ThrottleLimit** parameter isn't specified or a value of 0 is used, `Restart-Computer` uses a maximum of 32 concurrent connections.</span></span>

```yaml
Type: System.Int32
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-236">-Timeout</span><span class="sxs-lookup"><span data-stu-id="aba35-236">-Timeout</span></span>

<span data-ttu-id="aba35-237">Spécifie la durée de l'attente, en secondes.</span><span class="sxs-lookup"><span data-stu-id="aba35-237">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="aba35-238">Lorsque le délai d’attente est écoulé, `Restart-Computer` retourne à l’invite de commandes, même si les ordinateurs ne sont pas redémarrés.</span><span class="sxs-lookup"><span data-stu-id="aba35-238">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="aba35-239">Le paramètre **timeout** est valide uniquement avec le paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="aba35-239">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="aba35-240">Le **délai d'** attente remplace la période d’attente indéfinie du paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="aba35-240">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="aba35-241">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aba35-241">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultSet
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-242">-Wait</span><span class="sxs-lookup"><span data-stu-id="aba35-242">-Wait</span></span>

<span data-ttu-id="aba35-243">`Restart-Computer` supprime l’invite PowerShell et bloque le pipeline jusqu’à ce que les ordinateurs aient redémarré.</span><span class="sxs-lookup"><span data-stu-id="aba35-243">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="aba35-244">Vous pouvez utiliser ce paramètre dans un script pour redémarrer les ordinateurs, puis continuer le traitement une fois le redémarrage terminé.</span><span class="sxs-lookup"><span data-stu-id="aba35-244">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="aba35-245">Le paramètre **Wait** attend indéfiniment que les ordinateurs redémarrent.</span><span class="sxs-lookup"><span data-stu-id="aba35-245">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="aba35-246">Vous pouvez utiliser le **délai d’expiration** pour ajuster le minutage et les paramètres **de** **délai** et pour attendre que des services particuliers soient disponibles sur les ordinateurs redémarrés.</span><span class="sxs-lookup"><span data-stu-id="aba35-246">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="aba35-247">Le paramètre **Wait** n’est pas valide lorsque vous redémarrez l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="aba35-247">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="aba35-248">Si la valeur du paramètre **ComputerName** contient les noms des ordinateurs distants et de l’ordinateur local, `Restart-Computer` génère une erreur sans fin d' **attente** sur l’ordinateur local, mais attend que les ordinateurs distants redémarrent.</span><span class="sxs-lookup"><span data-stu-id="aba35-248">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="aba35-249">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aba35-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-250">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="aba35-250">-WsmanAuthentication</span></span>

<span data-ttu-id="aba35-251">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-251">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="aba35-252">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="aba35-252">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="aba35-253">Les valeurs acceptables pour ce paramètre sont les suivantes : de **base** , **CredSSP** , **par défaut** , **Digest** , **Kerberos** et **Negotiate** .</span><span class="sxs-lookup"><span data-stu-id="aba35-253">The acceptable values for this parameter are: **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** , and **Negotiate** .</span></span>

<span data-ttu-id="aba35-254">Pour plus d’informations, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="aba35-254">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="aba35-255">L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="aba35-255">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="aba35-256">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="aba35-256">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="aba35-257">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="aba35-257">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aba35-258">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aba35-258">-Confirm</span></span>

<span data-ttu-id="aba35-259">Vous invite à confirmer l’exécution `Restart-Computer` .</span><span class="sxs-lookup"><span data-stu-id="aba35-259">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="aba35-260">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aba35-260">-WhatIf</span></span>

<span data-ttu-id="aba35-261">Montre ce qui se passerait si le `Restart-Computer` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="aba35-261">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="aba35-262">L' `Restart-Computer` applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="aba35-262">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="aba35-263">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aba35-263">CommonParameters</span></span>

<span data-ttu-id="aba35-264">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aba35-264">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aba35-265">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aba35-265">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aba35-266">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="aba35-266">INPUTS</span></span>

### <span data-ttu-id="aba35-267">System.String</span><span class="sxs-lookup"><span data-stu-id="aba35-267">System.String</span></span>

<span data-ttu-id="aba35-268">`Restart-Computer` accepte les noms d’ordinateur à partir du ou des variables.</span><span class="sxs-lookup"><span data-stu-id="aba35-268">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

<span data-ttu-id="aba35-269">Dans Windows PowerShell 2.0, le paramètre **ComputerName** accepte l'entrée provenant du pipeline uniquement par nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="aba35-269">In Windows PowerShell 2.0, the **ComputerName** parameter takes input from the pipeline only by property name.</span></span> <span data-ttu-id="aba35-270">Dans Windows PowerShell 3,0 et versions ultérieures, le paramètre **ComputerName** prend en entrée le pipeline par valeur.</span><span class="sxs-lookup"><span data-stu-id="aba35-270">In Windows PowerShell 3.0, and later, the **ComputerName** parameter takes input from the pipeline by value.</span></span>

## <span data-ttu-id="aba35-271">SORTIES</span><span class="sxs-lookup"><span data-stu-id="aba35-271">OUTPUTS</span></span>

### <span data-ttu-id="aba35-272">Aucun, System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="aba35-272">None, System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="aba35-273">Si vous spécifiez le paramètre **AsJob** , `Restart-Computer` retourne un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="aba35-273">If you specify the **AsJob** parameter, `Restart-Computer` returns a job object.</span></span> <span data-ttu-id="aba35-274">Sinon, aucune sortie n’est générée.</span><span class="sxs-lookup"><span data-stu-id="aba35-274">Otherwise, no output is generated.</span></span>

## <span data-ttu-id="aba35-275">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="aba35-275">NOTES</span></span>

- <span data-ttu-id="aba35-276">`Restart-Computer` fonctionne uniquement sur les ordinateurs exécutant Windows et requiert WinRM et WMI pour arrêter un système, y compris le système local.</span><span class="sxs-lookup"><span data-stu-id="aba35-276">`Restart-Computer` only work on computers running Windows and requires WinRM and WMI to shutdown a system, including the local system.</span></span>
- <span data-ttu-id="aba35-277">`Restart-Computer` utilise la [méthode Win32Shutdown](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) de la classe [WIN32_OPERATINGSYSTEM](/windows/desktop/CIMWin32Prov/win32-operatingsystem) Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="aba35-277">`Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span>  <span data-ttu-id="aba35-278">Cette méthode requiert l’activation du privilège **SeShutdownPrivilege** pour le compte d’utilisateur utilisé pour redémarrer l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aba35-278">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="aba35-279">Dans Windows PowerShell 2,0, le paramètre **AsJob** ne fonctionne pas de façon fiable lorsque vous redémarrez ou arrêtez des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="aba35-279">In Windows PowerShell 2.0, the **AsJob** parameter doesn't work reliably when you are restarting or stopping remote computers.</span></span> <span data-ttu-id="aba35-280">Dans Windows PowerShell 3.0, l'implémentation est modifiée pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="aba35-280">In Windows PowerShell 3.0, the implementation is changed to resolve this problem.</span></span>

## <span data-ttu-id="aba35-281">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="aba35-281">RELATED LINKS</span></span>

[<span data-ttu-id="aba35-282">À propos de Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="aba35-282">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="aba35-283">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="aba35-283">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="aba35-284">Protocole Gestion des services web</span><span class="sxs-lookup"><span data-stu-id="aba35-284">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
