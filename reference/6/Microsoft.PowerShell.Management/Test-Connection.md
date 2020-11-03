---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 54ba1d7db60db7b4bb64f3161bba9c1fba124219
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202385"
---
# <span data-ttu-id="9aaf3-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="9aaf3-103">Test-Connection</span></span>

## <span data-ttu-id="9aaf3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9aaf3-104">SYNOPSIS</span></span>
<span data-ttu-id="9aaf3-105">Envoie des paquets de demande d’écho ICMP ou des pings à un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="9aaf3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9aaf3-106">SYNTAX</span></span>

### <span data-ttu-id="9aaf3-107">PingCount (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9aaf3-107">PingCount (Default)</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="9aaf3-108">PingContinues</span><span class="sxs-lookup"><span data-stu-id="9aaf3-108">PingContinues</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="9aaf3-109">DetectionOfMTUSize</span><span class="sxs-lookup"><span data-stu-id="9aaf3-109">DetectionOfMTUSize</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="9aaf3-110">Détermination</span><span class="sxs-lookup"><span data-stu-id="9aaf3-110">TraceRoute</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="9aaf3-111">ConnectionByTCPPort</span><span class="sxs-lookup"><span data-stu-id="9aaf3-111">ConnectionByTCPPort</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="9aaf3-112">Description</span><span class="sxs-lookup"><span data-stu-id="9aaf3-112">DESCRIPTION</span></span>

<span data-ttu-id="9aaf3-113">L' `Test-Connection` applet de commande envoie des paquets de demande d’écho ICMP (Internet Control Message Protocol) à un ou plusieurs ordinateurs distants, et renvoie les réponses de réponse à écho.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="9aaf3-114">Vous pouvez utiliser cette applet de commande pour déterminer si un ordinateur particulier peut être contacté via un réseau IP.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="9aaf3-115">Vous pouvez utiliser les paramètres de `Test-Connection` pour spécifier les ordinateurs d’envoi et de réception, exécuter la commande en tant que tâche en arrière-plan, définir un délai d’attente et un nombre de pings, et configurer la connexion et l’authentification.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="9aaf3-116">Contrairement à la commande **ping** familière, `Test-Connection` retourne un objet **TestConnectionCommand + PingReport** que vous pouvez examiner dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingReport** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="9aaf3-117">Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** pour chaque connexion testée.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="9aaf3-118">Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="9aaf3-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9aaf3-119">EXAMPLES</span></span>

### <span data-ttu-id="9aaf3-120">Exemple 1 : envoyer des demandes d’écho à un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="9aaf3-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="9aaf3-121">Cet exemple envoie des paquets de demande d’écho de l’ordinateur local à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
Pinging Server01 [10.59.137.44] with 32 bytes of data:
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Ping complete.

Source     Destination Replies
------     ----------- -------
Server01   Server01    {System.Net.NetworkInformation.PingReply, System.Net.NetworkInformation ...
```

<span data-ttu-id="9aaf3-122">`Test-Connection` utilise le paramètre **TargetName** pour spécifier l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="9aaf3-123">Le paramètre **IPv4** spécifie le protocole pour le test.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="9aaf3-124">Le résultat de la commande ping est envoyé au flux d' **informations** lorsque l’objet **TestConnectionCommand + PingReport** est envoyé au flux de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-124">The ping output is sent to the **Information** stream while the **TestConnectionCommand+PingReport** object sent to the **Success** stream.</span></span> <span data-ttu-id="9aaf3-125">Pour plus d’informations sur les flux de sortie, consultez [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).</span><span class="sxs-lookup"><span data-stu-id="9aaf3-125">For more information about the output streams, see [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).</span></span>

### <span data-ttu-id="9aaf3-126">Exemple 2 : envoyer des demandes d’écho à plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="9aaf3-126">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="9aaf3-127">Cet exemple envoie des pings de l’ordinateur local à plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-127">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="9aaf3-128">Exemple 3 : envoyer des demandes d’écho de plusieurs ordinateurs à un ordinateur</span><span class="sxs-lookup"><span data-stu-id="9aaf3-128">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="9aaf3-129">Cet exemple envoie des pings de différents ordinateurs sources à un ordinateur distant unique, SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-129">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

<span data-ttu-id="9aaf3-130">Utilisez ce format de commande pour tester la latence des connexions à partir de plusieurs points.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-130">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="9aaf3-131">Exemple 4 : utiliser des paramètres pour personnaliser la commande de test</span><span class="sxs-lookup"><span data-stu-id="9aaf3-131">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="9aaf3-132">Cet exemple utilise les paramètres de `Test-Connection` pour personnaliser la commande.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-132">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="9aaf3-133">L’ordinateur local envoie un test ping à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-133">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="9aaf3-134">`Test-Connection` utilise le paramètre **TargetName** pour spécifier SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-134">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="9aaf3-135">Le paramètre **Count** spécifie trois pings envoyés à l’ordinateur SERVEUR01 avec un **délai** de 2 secondes.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-135">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="9aaf3-136">Vous pouvez utiliser ces options lorsque la réponse ping est censée prendre plus de temps que d’habitude, soit en raison d’un nombre de tronçons étendu ou d’une condition de réseau à trafic élevé.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-136">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="9aaf3-137">Exemple 5 : exécuter un test en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="9aaf3-137">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="9aaf3-138">Cet exemple montre comment exécuter une `Test-Connection` commande en tant que tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-138">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

<span data-ttu-id="9aaf3-139">La `Start-Job` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur de nombreux ordinateurs d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-139">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="9aaf3-140">La valeur du paramètre **TargetName** est une `Get-Content` commande qui lit une liste de noms d’ordinateurs à partir du `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-140">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="9aaf3-141">La commande utilise l' `Start-Job` applet de commande pour exécuter la commande en tant que tâche en arrière-plan et elle enregistre la tâche dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-141">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="9aaf3-142">La `if` commande vérifie que le travail n’est pas encore en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-142">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="9aaf3-143">Si le travail n’est pas en cours d’exécution, `Receive-Job` obtient les résultats et les stocke dans la `$Results` variable.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-143">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="9aaf3-144">Exemple 6 : créer une session uniquement si un test de connexion a échoué</span><span class="sxs-lookup"><span data-stu-id="9aaf3-144">Example 6: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="9aaf3-145">Cet exemple crée une session sur l’ordinateur SERVEUR01 uniquement si au moins l’un des pings envoyés à l’ordinateur est correctement effectué.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-145">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="9aaf3-146">La `if` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-146">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="9aaf3-147">La commande utilise le paramètre **Quiet** , qui retourne une valeur **booléenne** au lieu d’un objet **TestConnectionCommand + PingReport** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-147">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **TestConnectionCommand+PingReport** object.</span></span>

<span data-ttu-id="9aaf3-148">La valeur est `$True` si l’un des quatre pings s’effectue correctement.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-148">The value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="9aaf3-149">Si aucune des commandes ping n’est établie, la valeur est `$False` .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-149">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="9aaf3-150">Si la `Test-Connection` commande retourne la valeur `$True` , la commande utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-150">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

### <span data-ttu-id="9aaf3-151">Exemple 7 : utiliser le paramètre traceroute</span><span class="sxs-lookup"><span data-stu-id="9aaf3-151">Example 7: Use the Traceroute parameter</span></span>

<span data-ttu-id="9aaf3-152">À compter de PowerShell 6,0, le paramètre **traceroute** mappe un itinéraire entre l’ordinateur local et la destination distante que vous spécifiez avec le paramètre **TargetName** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-152">Beginning in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

```powershell
Test-Connection -TargetName www.microsoft.com -Traceroute | ForEach-Object {
  $_ | Format-Table Source, DestinationAddress, DestinationHost
  $_.Replies | ForEach-Object {
      $_ | Format-Table Hop, ReplyRouterAddress
      $_.PingReplies | Format-Table
  }
}
```

```Output
Tracing route to www.microsoft.com [96.6.27.90] over a maximum of 128 hops:
  1   0 ms   0 ms   0 ms   192.168.0.3 [192.168.0.3]
  2   0 ms   0 ms   0 ms   192.168.1.1 [192.168.1.1]
  3   3 ms   29 ms   4 ms   96.6.27.90 [96.6.27.90]
Trace complete.

Source      DestinationAddress DestinationHost   Replies
------      ------------------ ---------------   -------
SERVER01    96.6.27.90         www.microsoft.com {, , }

Hop ReplyRouterAddress
--- ------------------
  1 192.168.0.3

    Status Address      RoundtripTime Options Buffer
    ------ -------      ------------- ------- ------
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  2 192.168.1.1

    Status Address     RoundtripTime Options Buffer
    ------ -------     ------------- ------- ------
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  3 96.6.27.90

 Status Address    RoundtripTime Options                                   Buffer
 ------ -------    ------------- -------                                   ------
Success 96.6.27.90             3 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             2 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             4 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
```

<span data-ttu-id="9aaf3-153">La `Test-Connection` commande utilise le paramètre **traceroute** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-153">The `Test-Connection` command uses the **Traceroute** parameter.</span></span> <span data-ttu-id="9aaf3-154">Les résultats, qui sont des `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objets, sont dirigés vers l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-154">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objects, are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="9aaf3-155">`ForEach-Object` crée une sortie structurée des `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objets contenus et des `[System.Net.NetworkInformation.PingReply]` objets suivants.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-155">`ForEach-Object` creates a structured output of the contained `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objects and subsequent `[System.Net.NetworkInformation.PingReply]` objects.</span></span>

## <span data-ttu-id="9aaf3-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9aaf3-156">PARAMETERS</span></span>

### <span data-ttu-id="9aaf3-157">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="9aaf3-157">-BufferSize</span></span>

<span data-ttu-id="9aaf3-158">Spécifie la taille (en octets) de la mémoire tampon envoyée avec cette commande.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-158">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="9aaf3-159">La valeur par défaut est 32.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-159">The default value is 32.</span></span>

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-160">-Nombre</span><span class="sxs-lookup"><span data-stu-id="9aaf3-160">-Count</span></span>

<span data-ttu-id="9aaf3-161">Spécifie le nombre de demandes d’écho à envoyer.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-161">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="9aaf3-162">La valeur par défaut est 4.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-162">The default value is 4.</span></span>

```yaml
Type: System.Int32
Parameter Sets: PingCount
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-163">-Délai</span><span class="sxs-lookup"><span data-stu-id="9aaf3-163">-Delay</span></span>

<span data-ttu-id="9aaf3-164">Spécifie l’intervalle entre les pings (en secondes).</span><span class="sxs-lookup"><span data-stu-id="9aaf3-164">Specifies the interval between pings, in seconds.</span></span>

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-165">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="9aaf3-165">-DontFragment</span></span>

<span data-ttu-id="9aaf3-166">Ce paramètre définit l’indicateur de non **fragmentation** dans l’en-tête IP.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-166">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="9aaf3-167">Vous pouvez utiliser ce paramètre avec le paramètre **bufferSize** pour tester la taille de la MTU du chemin.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-167">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="9aaf3-168">Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-168">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-169">-IPv4</span><span class="sxs-lookup"><span data-stu-id="9aaf3-169">-IPv4</span></span>

<span data-ttu-id="9aaf3-170">Force l’applet de commande à utiliser le protocole IPv4 pour le test.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-170">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-171">-IPv6</span><span class="sxs-lookup"><span data-stu-id="9aaf3-171">-IPv6</span></span>

<span data-ttu-id="9aaf3-172">Force l’applet de commande à utiliser le protocole IPv6 pour le test.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-172">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-173">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="9aaf3-173">-MaxHops</span></span>

<span data-ttu-id="9aaf3-174">Définit le nombre maximal de tronçons qu’un message de demande ICMP peut envoyer.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-174">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="9aaf3-175">La valeur par défaut est contrôlée par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-175">The default value is controlled by the operating system.</span></span> <span data-ttu-id="9aaf3-176">La valeur par défaut pour Windows 10 est 128 tronçons.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-176">The default value for Windows 10 is 128 hops.</span></span>

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-177">-Ping</span><span class="sxs-lookup"><span data-stu-id="9aaf3-177">-Ping</span></span>

<span data-ttu-id="9aaf3-178">Fait en sorte que l’applet de commande effectue un test ping, qui est l’action par défaut.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-178">Causes the cmdlet to do a ping test, which is the default action.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: Ping test
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-179">-Quiet</span><span class="sxs-lookup"><span data-stu-id="9aaf3-179">-Quiet</span></span>

<span data-ttu-id="9aaf3-180">Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-180">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="9aaf3-181">L’utilisation de ce paramètre supprime toutes les erreurs.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-181">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="9aaf3-182">Chaque connexion testée retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-182">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="9aaf3-183">Si le paramètre **TargetName** spécifie plusieurs ordinateurs, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-183">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="9aaf3-184">Si **une** commande ping est réussie, `$True` est retourné.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-184">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="9aaf3-185">Si **tous les** pings échouent, `$False` est retourné.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-185">If **all** pings fail, `$False` is returned.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-186">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="9aaf3-186">-ResolveDestination</span></span>

<span data-ttu-id="9aaf3-187">Force l’applet de commande à tenter de résoudre le nom DNS de la cible.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-187">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-188">-Source</span><span class="sxs-lookup"><span data-stu-id="9aaf3-188">-Source</span></span>

<span data-ttu-id="9aaf3-189">Spécifie le nom des ordinateurs d’où le ping provient.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-189">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="9aaf3-190">Entrez une liste de noms d’ordinateurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-190">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="9aaf3-191">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-191">The default is the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: PingCount, PingContinues, TraceRoute, ConnectionByTCPPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-192">-TargetName</span><span class="sxs-lookup"><span data-stu-id="9aaf3-192">-TargetName</span></span>

<span data-ttu-id="9aaf3-193">Spécifie les ordinateurs à tester.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-193">Specifies the computers to test.</span></span> <span data-ttu-id="9aaf3-194">Tapez le nom des ordinateurs ou les adresses IP au format IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="9aaf3-195">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-195">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="9aaf3-196">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-196">This parameter is required.</span></span> <span data-ttu-id="9aaf3-197">**ComputerName** est un alias pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-197">**ComputerName** is an alias for this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ComputerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-198">-TCPPort</span><span class="sxs-lookup"><span data-stu-id="9aaf3-198">-TCPPort</span></span>

<span data-ttu-id="9aaf3-199">Spécifie le numéro de port TCP sur la cible à utiliser dans le test de connexion TCP.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-199">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="9aaf3-200">L’applet de commande tente d’établir une connexion TCP au port spécifié sur la cible.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-200">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ConnectionByTCPPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-201">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="9aaf3-201">-TimeoutSeconds</span></span>

<span data-ttu-id="9aaf3-202">Définit la valeur du délai d’attente pour le test.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-202">Sets the timeout value for the test.</span></span> <span data-ttu-id="9aaf3-203">Le test échoue si aucune réponse n’est reçue avant l’expiration du délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-203">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="9aaf3-204">La valeur par défaut est cinq secondes.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-204">The default is five seconds.</span></span>

<span data-ttu-id="9aaf3-205">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-205">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5 seconds
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-206">-Traceroute</span><span class="sxs-lookup"><span data-stu-id="9aaf3-206">-Traceroute</span></span>

<span data-ttu-id="9aaf3-207">Fait en sorte que l’applet de commande effectue un test traceroute.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-207">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="9aaf3-208">Lorsque ce paramètre est utilisé, l’applet de commande retourne un `TestConnectionCommand+TraceRouteResult` objet.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-208">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceRouteResult` object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TraceRoute
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-209">-Continue</span><span class="sxs-lookup"><span data-stu-id="9aaf3-209">-Continues</span></span>

<span data-ttu-id="9aaf3-210">Fait en sorte que l’applet de commande envoie continuellement des demandes ping.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-210">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="9aaf3-211">Ce paramètre ne peut pas être utilisé avec le paramètre **Count** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-211">This parameter can't be used with the **Count** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-212">-MTUSizeDetect</span><span class="sxs-lookup"><span data-stu-id="9aaf3-212">-MTUSizeDetect</span></span>

<span data-ttu-id="9aaf3-213">Ce paramètre permet de découvrir la taille de la MTU du chemin.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-213">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="9aaf3-214">L’applet de commande retourne un objet **PingReply # MTUSize** qui contient la taille du chemin d’accès MTU à la cible.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-214">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="9aaf3-215">Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-215">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetectionOfMTUSize
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aaf3-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9aaf3-216">CommonParameters</span></span>

<span data-ttu-id="9aaf3-217">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9aaf3-218">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9aaf3-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9aaf3-219">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9aaf3-219">INPUTS</span></span>

### <span data-ttu-id="9aaf3-220">Aucun</span><span class="sxs-lookup"><span data-stu-id="9aaf3-220">None</span></span>

<span data-ttu-id="9aaf3-221">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-221">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9aaf3-222">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9aaf3-222">OUTPUTS</span></span>

### <span data-ttu-id="9aaf3-223">TestConnectionCommand + PingReport, TestConnectionCommand + TraceRouteResult, Boolean, PingReply # MTUSize</span><span class="sxs-lookup"><span data-stu-id="9aaf3-223">TestConnectionCommand+PingReport, TestConnectionCommand+TraceRouteResult, Boolean, PingReply#MTUSize</span></span>

<span data-ttu-id="9aaf3-224">Si vous spécifiez le paramètre **Quiet** , elle retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="9aaf3-224">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="9aaf3-225">Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-225">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="9aaf3-226">Sinon, `Test-Connection` retourne un objet **TestConnectionCommand + PingReport** pour chaque test ping.</span><span class="sxs-lookup"><span data-stu-id="9aaf3-226">Otherwise, `Test-Connection` returns a **TestConnectionCommand+PingReport** object for each ping.</span></span>

## <span data-ttu-id="9aaf3-227">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9aaf3-227">NOTES</span></span>

## <span data-ttu-id="9aaf3-228">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9aaf3-228">RELATED LINKS</span></span>

[<span data-ttu-id="9aaf3-229">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="9aaf3-229">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="9aaf3-230">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="9aaf3-230">Stop-Computer</span></span>](Stop-Computer.md)
