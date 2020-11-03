---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: a8d3923db69a20cfada58391944b592cf999e6ef
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203454"
---
# <span data-ttu-id="b538d-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="b538d-103">Test-Connection</span></span>

## <span data-ttu-id="b538d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b538d-104">SYNOPSIS</span></span>
<span data-ttu-id="b538d-105">Envoie des paquets de demande d’écho ICMP ou des pings à un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="b538d-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="b538d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b538d-106">SYNTAX</span></span>

### <span data-ttu-id="b538d-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b538d-107">Default (Default)</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="b538d-108">Source</span><span class="sxs-lookup"><span data-stu-id="b538d-108">Source</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="b538d-109">Quiet</span><span class="sxs-lookup"><span data-stu-id="b538d-109">Quiet</span></span>

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## <span data-ttu-id="b538d-110">Description</span><span class="sxs-lookup"><span data-stu-id="b538d-110">DESCRIPTION</span></span>

<span data-ttu-id="b538d-111">L' `Test-Connection` applet de commande envoie des paquets de demande d’écho ICMP (Internet Control Message Protocol) à un ou plusieurs ordinateurs distants, et renvoie les réponses de réponse à écho.</span><span class="sxs-lookup"><span data-stu-id="b538d-111">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="b538d-112">Vous pouvez utiliser cette applet de commande pour déterminer si un ordinateur particulier peut être contacté via un réseau IP.</span><span class="sxs-lookup"><span data-stu-id="b538d-112">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="b538d-113">Vous pouvez utiliser les paramètres de `Test-Connection` pour spécifier les ordinateurs d’envoi et de réception, exécuter la commande en tant que tâche en arrière-plan, définir un délai d’attente et un nombre de pings, et configurer la connexion et l’authentification.</span><span class="sxs-lookup"><span data-stu-id="b538d-113">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="b538d-114">Contrairement à la commande **ping** familière, `Test-Connection` retourne un objet **Win32_PingStatus** que vous pouvez examiner dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b538d-114">Unlike the familiar **ping** command, `Test-Connection` returns a **Win32_PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="b538d-115">Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** pour chaque connexion testée.</span><span class="sxs-lookup"><span data-stu-id="b538d-115">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="b538d-116">Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="b538d-116">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="b538d-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b538d-117">EXAMPLES</span></span>

### <span data-ttu-id="b538d-118">Exemple 1 : envoyer des demandes d’écho à un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="b538d-118">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="b538d-119">Cet exemple envoie des paquets de demande d’écho de l’ordinateur local à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b538d-119">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

```powershell
Test-Connection -ComputerName Server01
```

```Output
Source        Destination     IPV4Address     IPV6Address  Bytes    Time(ms)
------        -----------     -----------     -----------  -----    --------
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       1
```

<span data-ttu-id="b538d-120">`Test-Connection` utilise le paramètre **ComputerName** pour spécifier l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b538d-120">`Test-Connection` uses the **ComputerName** parameter to specify the Server01 computer.</span></span>

### <span data-ttu-id="b538d-121">Exemple 2 : envoyer des demandes d’écho à plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="b538d-121">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="b538d-122">Cet exemple envoie des pings de l’ordinateur local à plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="b538d-122">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### <span data-ttu-id="b538d-123">Exemple 3 : envoyer des demandes d’écho de plusieurs ordinateurs à un ordinateur</span><span class="sxs-lookup"><span data-stu-id="b538d-123">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="b538d-124">Cet exemple envoie des pings de différents ordinateurs sources à un ordinateur distant unique, SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b538d-124">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="b538d-125">`Test-Connection` utilise le paramètre **Credential** pour spécifier les informations d’identification d’un utilisateur qui a l’autorisation d’envoyer une demande ping à partir des ordinateurs sources.</span><span class="sxs-lookup"><span data-stu-id="b538d-125">`Test-Connection` uses the **Credential** parameter to specify the credentials of a user who has permission to send a ping request from the source computers.</span></span> <span data-ttu-id="b538d-126">Utilisez ce format de commande pour tester la latence des connexions à partir de plusieurs points.</span><span class="sxs-lookup"><span data-stu-id="b538d-126">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="b538d-127">Exemple 4 : utiliser des paramètres pour personnaliser la commande de test</span><span class="sxs-lookup"><span data-stu-id="b538d-127">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="b538d-128">Cet exemple utilise les paramètres de `Test-Connection` pour personnaliser la commande.</span><span class="sxs-lookup"><span data-stu-id="b538d-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="b538d-129">L’ordinateur local envoie un test ping à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b538d-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

<span data-ttu-id="b538d-130">`Test-Connection` utilise le paramètre **ComputerName** pour spécifier SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b538d-130">`Test-Connection` uses the **ComputerName** parameter to specify Server01.</span></span> <span data-ttu-id="b538d-131">Le paramètre **Count** spécifie trois pings envoyés à l’ordinateur SERVEUR01 avec un **délai** de 2 secondes.</span><span class="sxs-lookup"><span data-stu-id="b538d-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="b538d-132">Vous pouvez utiliser ces options lorsque la réponse ping est censée prendre plus de temps que d’habitude, soit en raison d’un nombre de tronçons étendu ou d’une condition de réseau à trafic élevé.</span><span class="sxs-lookup"><span data-stu-id="b538d-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="b538d-133">Exemple 5 : exécuter un test en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="b538d-133">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="b538d-134">Cet exemple montre comment exécuter une `Test-Connection` commande en tant que tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b538d-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

<span data-ttu-id="b538d-135">La `Test-Connection` commande exécute une commande ping sur de nombreux ordinateurs d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="b538d-135">The `Test-Connection` command pings many computers in an enterprise.</span></span> <span data-ttu-id="b538d-136">La valeur du paramètre **ComputerName** est une `Get-Content` commande qui lit une liste de noms d’ordinateurs à partir du `Servers.txt file` .</span><span class="sxs-lookup"><span data-stu-id="b538d-136">The value of the **ComputerName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt file`.</span></span> <span data-ttu-id="b538d-137">La commande utilise le paramètre **AsJob** pour exécuter la commande en tant que tâche en arrière-plan et elle enregistre la tâche dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="b538d-137">The command uses the **AsJob** parameter to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="b538d-138">La `if` commande vérifie que le travail n’est pas encore en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b538d-138">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="b538d-139">Si le travail n’est pas en cours d’exécution, `Receive-Job` obtient les résultats et les stocke dans la `$Results` variable.</span><span class="sxs-lookup"><span data-stu-id="b538d-139">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="b538d-140">Exemple 6 : exécuter une commande ping sur un ordinateur distant avec des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="b538d-140">Example 6: Ping a remote computer with credentials</span></span>

<span data-ttu-id="b538d-141">Cette commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b538d-141">This command uses the `Test-Connection` cmdlet to ping a remote computer.</span></span>

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

<span data-ttu-id="b538d-142">La commande utilise le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation d’exécuter une commande ping sur l’ordinateur distant et le paramètre d' **emprunt d’identité** pour modifier le niveau d’emprunt d’identité à **identifier** .</span><span class="sxs-lookup"><span data-stu-id="b538d-142">The command uses the **Credential** parameter to specify a user account that has permission to ping the remote computer and the **Impersonation** parameter to change the impersonation level to **Identify** .</span></span>

### <span data-ttu-id="b538d-143">Exemple 7 : créer une session uniquement si un test de connexion a échoué</span><span class="sxs-lookup"><span data-stu-id="b538d-143">Example 7: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="b538d-144">Cet exemple crée une session sur l’ordinateur SERVEUR01 uniquement si au moins l’un des pings envoyés à l’ordinateur est correctement effectué.</span><span class="sxs-lookup"><span data-stu-id="b538d-144">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="b538d-145">La `if` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b538d-145">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="b538d-146">La commande utilise le paramètre **Quiet** , qui retourne une valeur **booléenne** au lieu d’un objet **Win32_PingStatus** .</span><span class="sxs-lookup"><span data-stu-id="b538d-146">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **Win32_PingStatus** object.</span></span> <span data-ttu-id="b538d-147">La valeur est `$True` si l’un des quatre pings s’effectue correctement et est, sinon, `$False` .</span><span class="sxs-lookup"><span data-stu-id="b538d-147">The value is `$True` if any of the four pings succeed and is, otherwise, `$False`.</span></span>

<span data-ttu-id="b538d-148">Si la `Test-Connection` commande retourne la valeur `$True` , la commande utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="b538d-148">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

## <span data-ttu-id="b538d-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b538d-149">PARAMETERS</span></span>

### <span data-ttu-id="b538d-150">-AsJob</span><span class="sxs-lookup"><span data-stu-id="b538d-150">-AsJob</span></span>

<span data-ttu-id="b538d-151">Indique que cette applet de commande s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b538d-151">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="b538d-152">Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance et, sous Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="b538d-152">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="b538d-153">Pour plus d'informations, consultez [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b538d-153">For more information, see [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="b538d-154">Lorsque vous spécifiez le paramètre **AsJob** , la commande retourne immédiatement un objet qui représente la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b538d-154">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="b538d-155">Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="b538d-155">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="b538d-156">La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b538d-156">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="b538d-157">Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="b538d-157">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="b538d-158">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).</span><span class="sxs-lookup"><span data-stu-id="b538d-158">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-159">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="b538d-159">-BufferSize</span></span>

<span data-ttu-id="b538d-160">Spécifie la taille (en octets) de la mémoire tampon envoyée avec cette commande.</span><span class="sxs-lookup"><span data-stu-id="b538d-160">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="b538d-161">La valeur par défaut est 32.</span><span class="sxs-lookup"><span data-stu-id="b538d-161">The default value is 32.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b538d-162">-ComputerName</span></span>

<span data-ttu-id="b538d-163">Spécifie les ordinateurs sur lesquels effectuer un test ping.</span><span class="sxs-lookup"><span data-stu-id="b538d-163">Specifies the computers to ping.</span></span> <span data-ttu-id="b538d-164">Tapez le nom des ordinateurs ou les adresses IP au format IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="b538d-164">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="b538d-165">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="b538d-165">Wildcard characters are not permitted.</span></span> <span data-ttu-id="b538d-166">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b538d-166">This parameter is required.</span></span>

<span data-ttu-id="b538d-167">Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b538d-167">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="b538d-168">Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="b538d-168">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

> [!NOTE]
> <span data-ttu-id="b538d-169">Le paramètre **ComputerName** est renommé en **TargetName** dans PowerShell 6,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="b538d-169">The **ComputerName** parameter is renamed to **TargetName** in PowerShell 6.0 and above.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, IPAddress, __SERVER, Server, Destination

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-170">-Nombre</span><span class="sxs-lookup"><span data-stu-id="b538d-170">-Count</span></span>

<span data-ttu-id="b538d-171">Spécifie le nombre de demandes d’écho à envoyer.</span><span class="sxs-lookup"><span data-stu-id="b538d-171">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="b538d-172">La valeur par défaut est 4.</span><span class="sxs-lookup"><span data-stu-id="b538d-172">The default value is 4.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="b538d-173">-Credential</span></span>

<span data-ttu-id="b538d-174">Spécifie un compte d’utilisateur qui a l’autorisation d’envoyer une demande Ping à partir de l’ordinateur source.</span><span class="sxs-lookup"><span data-stu-id="b538d-174">Specifies a user account that has permission to send a ping request from the source computer.</span></span> <span data-ttu-id="b538d-175">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="b538d-175">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="b538d-176">Le paramètre **Credential** est valide uniquement lorsque le paramètre **Source** est utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="b538d-176">The **Credential** parameter is valid only when the **Source** parameter is used in the command.</span></span> <span data-ttu-id="b538d-177">Les informations d’identification n’affectent pas l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="b538d-177">The credentials don't affect the destination computer.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Source
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-178">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="b538d-178">-DcomAuthentication</span></span>

<span data-ttu-id="b538d-179">Spécifie le niveau d’authentification que cette applet de commande utilise avec WMI.</span><span class="sxs-lookup"><span data-stu-id="b538d-179">Specifies the authentication level that this cmdlet uses with WMI.</span></span>
<span data-ttu-id="b538d-180">`Test-Connection` utilise WMI.</span><span class="sxs-lookup"><span data-stu-id="b538d-180">`Test-Connection` uses WMI.</span></span>
<span data-ttu-id="b538d-181">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="b538d-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b538d-182">**Par défaut** .</span><span class="sxs-lookup"><span data-stu-id="b538d-182">**Default** .</span></span> <span data-ttu-id="b538d-183">Authentification Windows</span><span class="sxs-lookup"><span data-stu-id="b538d-183">Windows Authentication</span></span>
- <span data-ttu-id="b538d-184">**Aucun** .</span><span class="sxs-lookup"><span data-stu-id="b538d-184">**None** .</span></span> <span data-ttu-id="b538d-185">aucune authentification COM.</span><span class="sxs-lookup"><span data-stu-id="b538d-185">No COM authentication</span></span>
- <span data-ttu-id="b538d-186">**Connectez-vous** .</span><span class="sxs-lookup"><span data-stu-id="b538d-186">**Connect** .</span></span> <span data-ttu-id="b538d-187">authentification COM au niveau de la connexion</span><span class="sxs-lookup"><span data-stu-id="b538d-187">Connect-level COM authentication</span></span>
- <span data-ttu-id="b538d-188">**Appelez** .</span><span class="sxs-lookup"><span data-stu-id="b538d-188">**Call** .</span></span> <span data-ttu-id="b538d-189">authentification COM au niveau de l'appel.</span><span class="sxs-lookup"><span data-stu-id="b538d-189">Call-level COM authentication</span></span>
- <span data-ttu-id="b538d-190">**Paquet** .</span><span class="sxs-lookup"><span data-stu-id="b538d-190">**Packet** .</span></span> <span data-ttu-id="b538d-191">Authentification COM au niveau du paquet</span><span class="sxs-lookup"><span data-stu-id="b538d-191">Packet-level COM authentication</span></span>
- <span data-ttu-id="b538d-192">**PacketIntegrity** .</span><span class="sxs-lookup"><span data-stu-id="b538d-192">**PacketIntegrity** .</span></span> <span data-ttu-id="b538d-193">authentification COM au niveau de l'intégrité du paquet.</span><span class="sxs-lookup"><span data-stu-id="b538d-193">Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="b538d-194">**PacketPrivacy** .</span><span class="sxs-lookup"><span data-stu-id="b538d-194">**PacketPrivacy** .</span></span> <span data-ttu-id="b538d-195">Authentification COM au niveau de la confidentialité du paquet</span><span class="sxs-lookup"><span data-stu-id="b538d-195">Packet Privacy-level COM authentication</span></span>
- <span data-ttu-id="b538d-196">**Inchangé** .</span><span class="sxs-lookup"><span data-stu-id="b538d-196">**Unchanged** .</span></span> <span data-ttu-id="b538d-197">Identique à la commande précédente</span><span class="sxs-lookup"><span data-stu-id="b538d-197">Same as the previous command</span></span>

<span data-ttu-id="b538d-198">La valeur par défaut est **Packet** qui a une valeur énumérée de **4** .</span><span class="sxs-lookup"><span data-stu-id="b538d-198">The default value is **Packet** that has an enumerated value of **4** .</span></span> <span data-ttu-id="b538d-199">Pour plus d’informations sur les valeurs de ce paramètre, consultez énumération [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) .</span><span class="sxs-lookup"><span data-stu-id="b538d-199">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) enumeration.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet (enumerated value of 4)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-200">-Délai</span><span class="sxs-lookup"><span data-stu-id="b538d-200">-Delay</span></span>

<span data-ttu-id="b538d-201">Spécifie l’intervalle entre les pings (en secondes).</span><span class="sxs-lookup"><span data-stu-id="b538d-201">Specifies the interval between pings, in seconds.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1 (second)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-202">-Emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="b538d-202">-Impersonation</span></span>

<span data-ttu-id="b538d-203">Spécifie le niveau d’emprunt d’identité à utiliser lorsque cette applet de commande appelle WMI.</span><span class="sxs-lookup"><span data-stu-id="b538d-203">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="b538d-204">`Test-Connection` utilise WMI.</span><span class="sxs-lookup"><span data-stu-id="b538d-204">`Test-Connection` uses WMI.</span></span>

<span data-ttu-id="b538d-205">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b538d-205">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b538d-206">**Par défaut** .</span><span class="sxs-lookup"><span data-stu-id="b538d-206">**Default** .</span></span> <span data-ttu-id="b538d-207">Emprunt d'identité par défaut.</span><span class="sxs-lookup"><span data-stu-id="b538d-207">Default impersonation.</span></span>
- <span data-ttu-id="b538d-208">**Anonyme** .</span><span class="sxs-lookup"><span data-stu-id="b538d-208">**Anonymous** .</span></span> <span data-ttu-id="b538d-209">masque l'identité de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="b538d-209">Hides the identity of the caller.</span></span>
- <span data-ttu-id="b538d-210">**Identifiez** .</span><span class="sxs-lookup"><span data-stu-id="b538d-210">**Identify** .</span></span> <span data-ttu-id="b538d-211">Permet aux objets d'interroger les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="b538d-211">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="b538d-212">**Emprunter l’identité** .</span><span class="sxs-lookup"><span data-stu-id="b538d-212">**Impersonate** .</span></span> <span data-ttu-id="b538d-213">Permet aux objets d'utiliser les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="b538d-213">Allows objects to use the credentials of the caller.</span></span>

<span data-ttu-id="b538d-214">La valeur par défaut est **Impersonate** .</span><span class="sxs-lookup"><span data-stu-id="b538d-214">The default value is **Impersonate** .</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-215">-Protocol</span><span class="sxs-lookup"><span data-stu-id="b538d-215">-Protocol</span></span>

<span data-ttu-id="b538d-216">Spécifie un protocole.</span><span class="sxs-lookup"><span data-stu-id="b538d-216">Specifies a protocol.</span></span> <span data-ttu-id="b538d-217">Les valeurs acceptables pour ce paramètre sont DCOM et WSMan.</span><span class="sxs-lookup"><span data-stu-id="b538d-217">The acceptable values for this parameter are DCOM and WSMan.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-218">-Quiet</span><span class="sxs-lookup"><span data-stu-id="b538d-218">-Quiet</span></span>

<span data-ttu-id="b538d-219">Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** .</span><span class="sxs-lookup"><span data-stu-id="b538d-219">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="b538d-220">L’utilisation de ce paramètre supprime toutes les erreurs.</span><span class="sxs-lookup"><span data-stu-id="b538d-220">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="b538d-221">Chaque connexion testée retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="b538d-221">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="b538d-222">Si le paramètre **ComputerName** spécifie plusieurs ordinateurs, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="b538d-222">If the **ComputerName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="b538d-223">Si **une** commande ping est réussie, `$True` est retourné.</span><span class="sxs-lookup"><span data-stu-id="b538d-223">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="b538d-224">Si **tous les** pings échouent, `$False` est retourné.</span><span class="sxs-lookup"><span data-stu-id="b538d-224">If **all** pings fail, `$False` is returned.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Quiet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-225">-Source</span><span class="sxs-lookup"><span data-stu-id="b538d-225">-Source</span></span>

<span data-ttu-id="b538d-226">Spécifie le nom des ordinateurs d’où le ping provient.</span><span class="sxs-lookup"><span data-stu-id="b538d-226">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="b538d-227">Entrez une liste de noms d’ordinateurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="b538d-227">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="b538d-228">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b538d-228">The default is the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: FCN, SRC

Required: True
Position: 1
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-229">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b538d-229">-ThrottleLimit</span></span>

<span data-ttu-id="b538d-230">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="b538d-230">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="b538d-231">Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b538d-231">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="b538d-232">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b538d-232">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-233">-TimeToLive</span><span class="sxs-lookup"><span data-stu-id="b538d-233">-TimeToLive</span></span>

<span data-ttu-id="b538d-234">Spécifie la durée maximale pendant laquelle un paquet peut être transféré.</span><span class="sxs-lookup"><span data-stu-id="b538d-234">Specifies the maximum times a packet can be forwarded.</span></span> <span data-ttu-id="b538d-235">Pour chaque tronçon dans les passerelles, les routeurs, etc., la valeur de **TimeToLive** est diminuée d’une unité.</span><span class="sxs-lookup"><span data-stu-id="b538d-235">For every hop in gateways, routers etc. the **TimeToLive** value is decreased by one.</span></span> <span data-ttu-id="b538d-236">À zéro, le paquet est rejeté et une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="b538d-236">At zero the packet is discarded and an error is returned.</span></span>
<span data-ttu-id="b538d-237">Dans **Windows** , la valeur par défaut est **128** .</span><span class="sxs-lookup"><span data-stu-id="b538d-237">In **Windows** , The default value is **128** .</span></span> <span data-ttu-id="b538d-238">L’alias du paramètre **TimeToLive** est **TTL** .</span><span class="sxs-lookup"><span data-stu-id="b538d-238">The alias of the **TimeToLive** parameter is **TTL** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TTL

Required: False
Position: Named
Default value: 128 in Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-239">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="b538d-239">-WsmanAuthentication</span></span>

<span data-ttu-id="b538d-240">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan.</span><span class="sxs-lookup"><span data-stu-id="b538d-240">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span>
<span data-ttu-id="b538d-241">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="b538d-241">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b538d-242">Basic</span><span class="sxs-lookup"><span data-stu-id="b538d-242">Basic</span></span>
- <span data-ttu-id="b538d-243">CredSSP</span><span class="sxs-lookup"><span data-stu-id="b538d-243">CredSSP</span></span>
- <span data-ttu-id="b538d-244">Default</span><span class="sxs-lookup"><span data-stu-id="b538d-244">Default</span></span>
- <span data-ttu-id="b538d-245">Digest</span><span class="sxs-lookup"><span data-stu-id="b538d-245">Digest</span></span>
- <span data-ttu-id="b538d-246">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b538d-246">Kerberos</span></span>
- <span data-ttu-id="b538d-247">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="b538d-247">Negotiate.</span></span>

<span data-ttu-id="b538d-248">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="b538d-248">The default value is Default.</span></span>

<span data-ttu-id="b538d-249">Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="b538d-249">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).</span></span>

<span data-ttu-id="b538d-250">ATTENTION : l’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="b538d-250">Caution: Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="b538d-251">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="b538d-251">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="b538d-252">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="b538d-252">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="b538d-253">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="b538d-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b538d-254">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b538d-254">CommonParameters</span></span>

<span data-ttu-id="b538d-255">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b538d-255">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b538d-256">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b538d-256">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b538d-257">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b538d-257">INPUTS</span></span>

### <span data-ttu-id="b538d-258">Aucun</span><span class="sxs-lookup"><span data-stu-id="b538d-258">None</span></span>

<span data-ttu-id="b538d-259">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b538d-259">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b538d-260">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b538d-260">OUTPUTS</span></span>

### <span data-ttu-id="b538d-261">System. Management. ManagementObject # root\cimv2\ Win32_PingStatus, System. Management. Automation. RemotingJob, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="b538d-261">System.Management.ManagementObject#root\cimv2\Win32_PingStatus, System.Management.Automation.RemotingJob, System.Boolean</span></span>

<span data-ttu-id="b538d-262">Cette applet de commande retourne un objet de traitement, si vous spécifiez le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="b538d-262">This cmdlet returns a job object, if you specify the **AsJob** parameter.</span></span>

<span data-ttu-id="b538d-263">Si vous spécifiez le paramètre **Quiet** , elle retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="b538d-263">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="b538d-264">Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="b538d-264">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="b538d-265">Sinon, `Test-Connection` retourne un objet **Win32_PingStatus** pour chaque test ping.</span><span class="sxs-lookup"><span data-stu-id="b538d-265">Otherwise, `Test-Connection` returns a **Win32_PingStatus** object for each ping.</span></span>

## <span data-ttu-id="b538d-266">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b538d-266">NOTES</span></span>

<span data-ttu-id="b538d-267">Cette applet de commande utilise la classe **Win32_PingStatus** .</span><span class="sxs-lookup"><span data-stu-id="b538d-267">This cmdlet uses the **Win32_PingStatus** class.</span></span> <span data-ttu-id="b538d-268">Une `Get-WMIObject Win32_PingStatus` commande est équivalente à une `Test-Connection` commande.</span><span class="sxs-lookup"><span data-stu-id="b538d-268">A `Get-WMIObject Win32_PingStatus` command is equivalent to a `Test-Connection` command.</span></span>

<span data-ttu-id="b538d-269">Le jeu de paramètres **source** a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b538d-269">The **Source** parameter set was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="b538d-270">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b538d-270">RELATED LINKS</span></span>

[<span data-ttu-id="b538d-271">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="b538d-271">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="b538d-272">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="b538d-272">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="b538d-273">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="b538d-273">Stop-Computer</span></span>](Stop-Computer.md)
