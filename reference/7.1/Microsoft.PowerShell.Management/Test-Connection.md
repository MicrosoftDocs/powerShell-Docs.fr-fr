---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 6a03d5a644e3d4be515a93a702d0ef0aff23a8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202381"
---
# <span data-ttu-id="87d84-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="87d84-103">Test-Connection</span></span>

## <span data-ttu-id="87d84-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="87d84-104">SYNOPSIS</span></span>
<span data-ttu-id="87d84-105">Envoie des paquets de demande d’écho ICMP ou des pings à un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="87d84-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="87d84-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="87d84-106">SYNTAX</span></span>

### <span data-ttu-id="87d84-107">DefaultPing (par défaut)</span><span class="sxs-lookup"><span data-stu-id="87d84-107">DefaultPing (Default)</span></span>

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="87d84-108">RepeatPing</span><span class="sxs-lookup"><span data-stu-id="87d84-108">RepeatPing</span></span>

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="87d84-109">MtuSizeDetect</span><span class="sxs-lookup"><span data-stu-id="87d84-109">MtuSizeDetect</span></span>

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="87d84-110">Détermination</span><span class="sxs-lookup"><span data-stu-id="87d84-110">TraceRoute</span></span>

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="87d84-111">TcpPort</span><span class="sxs-lookup"><span data-stu-id="87d84-111">TcpPort</span></span>

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="87d84-112">Description</span><span class="sxs-lookup"><span data-stu-id="87d84-112">DESCRIPTION</span></span>

<span data-ttu-id="87d84-113">L' `Test-Connection` applet de commande envoie des paquets de demande d’écho ICMP (Internet Control Message Protocol) à un ou plusieurs ordinateurs distants, et renvoie les réponses de réponse à écho.</span><span class="sxs-lookup"><span data-stu-id="87d84-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="87d84-114">Vous pouvez utiliser cette applet de commande pour déterminer si un ordinateur particulier peut être contacté via un réseau IP.</span><span class="sxs-lookup"><span data-stu-id="87d84-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="87d84-115">Vous pouvez utiliser les paramètres de `Test-Connection` pour spécifier les ordinateurs d’envoi et de réception, exécuter la commande en tant que tâche en arrière-plan, définir un délai d’attente et un nombre de pings, et configurer la connexion et l’authentification.</span><span class="sxs-lookup"><span data-stu-id="87d84-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="87d84-116">Contrairement à la commande **ping** familière, `Test-Connection` retourne un objet **TestConnectionCommand + PingStatus** que vous pouvez examiner dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87d84-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="87d84-117">Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** pour chaque connexion testée.</span><span class="sxs-lookup"><span data-stu-id="87d84-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="87d84-118">Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="87d84-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="87d84-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="87d84-119">EXAMPLES</span></span>

### <span data-ttu-id="87d84-120">Exemple 1 : envoyer des demandes d’écho à un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="87d84-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="87d84-121">Cet exemple envoie des paquets de demande d’écho de l’ordinateur local à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="87d84-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
   Destination: Server01

Ping Source           Address                   Latency BufferSize Status
                                                   (ms)        (B)
---- ------           -------                   ------- ---------- ------
   1 ADMIN1           10.59.137.44                   24         32 Success
   2 ADMIN1           10.59.137.44                   39         32 Success
   3 ADMIN1           *                               *          * TimedOut
   4 ADMIN1           10.59.137.44                   28         32 Success
```

<span data-ttu-id="87d84-122">`Test-Connection` utilise le paramètre **TargetName** pour spécifier l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="87d84-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="87d84-123">Le paramètre **IPv4** spécifie le protocole pour le test.</span><span class="sxs-lookup"><span data-stu-id="87d84-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="87d84-124">Une série d’objets **TestConnectionCommand + PingStatus** sont envoyées au flux de sortie, un objet par réponse ping de l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="87d84-124">A series of **TestConnectionCommand+PingStatus** objects are sent to the output stream, one object per ping reply from the target machine.</span></span>

### <span data-ttu-id="87d84-125">Exemple 2 : envoyer des demandes d’écho à plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="87d84-125">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="87d84-126">Cet exemple envoie des pings de l’ordinateur local à plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="87d84-126">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="87d84-127">Exemple 3 : utiliser des paramètres pour personnaliser la commande de test</span><span class="sxs-lookup"><span data-stu-id="87d84-127">Example 3: Use parameters to customize the test command</span></span>

<span data-ttu-id="87d84-128">Cet exemple utilise les paramètres de `Test-Connection` pour personnaliser la commande.</span><span class="sxs-lookup"><span data-stu-id="87d84-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="87d84-129">L’ordinateur local envoie un test ping à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="87d84-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="87d84-130">`Test-Connection` utilise le paramètre **TargetName** pour spécifier SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="87d84-130">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="87d84-131">Le paramètre **Count** spécifie trois pings envoyés à l’ordinateur SERVEUR01 avec un **délai** de 2 secondes.</span><span class="sxs-lookup"><span data-stu-id="87d84-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="87d84-132">Vous pouvez utiliser ces options lorsque la réponse ping est censée prendre plus de temps que d’habitude, soit en raison d’un nombre de tronçons étendu ou d’une condition de réseau à trafic élevé.</span><span class="sxs-lookup"><span data-stu-id="87d84-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="87d84-133">Exemple 4 : exécuter un test en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="87d84-133">Example 4: Run a test as a background job</span></span>

<span data-ttu-id="87d84-134">Cet exemple montre comment exécuter une `Test-Connection` commande en tant que tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87d84-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

<span data-ttu-id="87d84-135">La `Start-Job` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur de nombreux ordinateurs d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="87d84-135">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="87d84-136">La valeur du paramètre **TargetName** est une `Get-Content` commande qui lit une liste de noms d’ordinateurs à partir du `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="87d84-136">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="87d84-137">La commande utilise l' `Start-Job` applet de commande pour exécuter la commande en tant que tâche en arrière-plan et elle enregistre la tâche dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="87d84-137">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="87d84-138">La `Receive-Job` commande est invitée `-Wait` jusqu’à ce que le travail soit terminé, puis obtient les résultats et les stocke dans la `$Results` variable.</span><span class="sxs-lookup"><span data-stu-id="87d84-138">The `Receive-Job` command is instructed to `-Wait` until the job is completed, and then gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="87d84-139">Exemple 5 : créer une session uniquement si un test de connexion a échoué</span><span class="sxs-lookup"><span data-stu-id="87d84-139">Example 5: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="87d84-140">Cet exemple crée une session sur l’ordinateur SERVEUR01 uniquement si au moins l’un des pings envoyés à l’ordinateur est correctement effectué.</span><span class="sxs-lookup"><span data-stu-id="87d84-140">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

<span data-ttu-id="87d84-141">L' `Test-Connection` applet de commande exécute une commande ping sur l' `Server01` ordinateur, avec le paramètre **Quiet** fourni.</span><span class="sxs-lookup"><span data-stu-id="87d84-141">The `Test-Connection` cmdlet pings the `Server01` computer, with the **Quiet** parameter provided.</span></span>
<span data-ttu-id="87d84-142">La valeur obtenue est `$True` si l’un des quatre pings aboutit.</span><span class="sxs-lookup"><span data-stu-id="87d84-142">The resulting value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="87d84-143">Si aucune des commandes ping n’est établie, la valeur est `$False` .</span><span class="sxs-lookup"><span data-stu-id="87d84-143">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="87d84-144">Si la `Test-Connection` commande retourne la valeur `$True` , la commande utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="87d84-144">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

### <span data-ttu-id="87d84-145">Exemple 6 : utiliser le paramètre traceroute</span><span class="sxs-lookup"><span data-stu-id="87d84-145">Example 6: Use the Traceroute parameter</span></span>

<span data-ttu-id="87d84-146">Introduite dans PowerShell 6,0, le paramètre **traceroute** mappe un itinéraire entre l’ordinateur local et la destination distante que vous spécifiez avec le paramètre **TargetName** .</span><span class="sxs-lookup"><span data-stu-id="87d84-146">Introduced in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

```powershell
Test-Connection -TargetName www.google.com -Traceroute
```

```Output
   Target: google.com

Hop Hostname                  Ping Latency Status           Source       TargetAddress
                                      (ms)
--- --------                  ---- ------- ------           ------       -------------
  1 172.20.0.1                   1       4 Success          Lira         172.217.9.174
  1 172.20.0.1                   2       3 Success          Lira         172.217.9.174
  1 172.20.0.1                   3       2 Success          Lira         172.217.9.174
  2 12.108.153.193               1       3 Success          Lira         172.217.9.174
  2 12.108.153.193               2       3 Success          Lira         172.217.9.174
  2 12.108.153.193               3       2 Success          Lira         172.217.9.174
  3 12.244.85.177                1      11 Success          Lira         172.217.9.174
  3 12.244.85.177                2      12 Success          Lira         172.217.9.174
  3 12.244.85.177                3      12 Success          Lira         172.217.9.174
  4 *                            1      14 DestinationNetw… Lira         172.217.9.174
  4 *                            2       * TimedOut         Lira         172.217.9.174
  4 *                            3      20 DestinationNetw… Lira         172.217.9.174
  5 *                            1       * TimedOut         Lira         172.217.9.174
  5 *                            2      15 DestinationNetw… Lira         172.217.9.174
  5 *                            3       * TimedOut         Lira         172.217.9.174
  6 *                            1      18 DestinationNetw… Lira         172.217.9.174
  6 *                            2       * TimedOut         Lira         172.217.9.174
  6 *                            3      16 DestinationNetw… Lira         172.217.9.174
  7 *                            1       * TimedOut         Lira         172.217.9.174
  7 *                            2       * TimedOut         Lira         172.217.9.174
  7 *                            3       * TimedOut         Lira         172.217.9.174
  8 *                            1       * TimedOut         Lira         172.217.9.174
  8 *                            2       * TimedOut         Lira         172.217.9.174
  8 *                            3       * TimedOut         Lira         172.217.9.174
  9 *                            1       * TimedOut         Lira         172.217.9.174
  9 *                            2       * TimedOut         Lira         172.217.9.174
  9 *                            3       * TimedOut         Lira         172.217.9.174
 10 *                            1       * TimedOut         Lira         172.217.9.174
 10 *                            2       * TimedOut         Lira         172.217.9.174
 10 *                            3       * TimedOut         Lira         172.217.9.174
 11 172.217.9.174                1      23 Success          Lira         172.217.9.174
 11 172.217.9.174                2      21 Success          Lira         172.217.9.174
 11 172.217.9.174                3      22 Success          Lira         172.217.9.174
```

<span data-ttu-id="87d84-147">La `Test-Connection` commande est appelée avec le paramètre **traceroute** .</span><span class="sxs-lookup"><span data-stu-id="87d84-147">The `Test-Connection` command is called with the **Traceroute** parameter.</span></span> <span data-ttu-id="87d84-148">Les résultats, qui sont des `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objets, sont générés dans le flux de sortie de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="87d84-148">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objects, are output to the **Success** output stream.</span></span>

## <span data-ttu-id="87d84-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="87d84-149">PARAMETERS</span></span>

### <span data-ttu-id="87d84-150">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="87d84-150">-BufferSize</span></span>

<span data-ttu-id="87d84-151">Spécifie la taille (en octets) de la mémoire tampon envoyée avec cette commande.</span><span class="sxs-lookup"><span data-stu-id="87d84-151">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="87d84-152">La valeur par défaut est 32.</span><span class="sxs-lookup"><span data-stu-id="87d84-152">The default value is 32.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-153">-Répéter</span><span class="sxs-lookup"><span data-stu-id="87d84-153">-Repeat</span></span>

<span data-ttu-id="87d84-154">Fait en sorte que l’applet de commande envoie continuellement des demandes ping.</span><span class="sxs-lookup"><span data-stu-id="87d84-154">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="87d84-155">Ce paramètre ne peut pas être utilisé avec le paramètre **Count** .</span><span class="sxs-lookup"><span data-stu-id="87d84-155">This parameter can't be used with the **Count** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RepeatPing
Aliases: Continuous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-156">-Nombre</span><span class="sxs-lookup"><span data-stu-id="87d84-156">-Count</span></span>

<span data-ttu-id="87d84-157">Spécifie le nombre de demandes d’écho à envoyer.</span><span class="sxs-lookup"><span data-stu-id="87d84-157">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="87d84-158">La valeur par défaut est 4.</span><span class="sxs-lookup"><span data-stu-id="87d84-158">The default value is 4.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-159">-Délai</span><span class="sxs-lookup"><span data-stu-id="87d84-159">-Delay</span></span>

<span data-ttu-id="87d84-160">Spécifie l’intervalle entre les pings (en secondes).</span><span class="sxs-lookup"><span data-stu-id="87d84-160">Specifies the interval between pings, in seconds.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-161">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="87d84-161">-DontFragment</span></span>

<span data-ttu-id="87d84-162">Ce paramètre définit l’indicateur de non **fragmentation** dans l’en-tête IP.</span><span class="sxs-lookup"><span data-stu-id="87d84-162">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="87d84-163">Vous pouvez utiliser ce paramètre avec le paramètre **bufferSize** pour tester la taille de la MTU du chemin.</span><span class="sxs-lookup"><span data-stu-id="87d84-163">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="87d84-164">Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="87d84-164">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-165">-IPv4</span><span class="sxs-lookup"><span data-stu-id="87d84-165">-IPv4</span></span>

<span data-ttu-id="87d84-166">Force l’applet de commande à utiliser le protocole IPv4 pour le test.</span><span class="sxs-lookup"><span data-stu-id="87d84-166">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="87d84-167">-IPv6</span><span class="sxs-lookup"><span data-stu-id="87d84-167">-IPv6</span></span>

<span data-ttu-id="87d84-168">Force l’applet de commande à utiliser le protocole IPv6 pour le test.</span><span class="sxs-lookup"><span data-stu-id="87d84-168">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="87d84-169">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="87d84-169">-MaxHops</span></span>

<span data-ttu-id="87d84-170">Définit le nombre maximal de tronçons qu’un message de demande ICMP peut envoyer.</span><span class="sxs-lookup"><span data-stu-id="87d84-170">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="87d84-171">La valeur par défaut est contrôlée par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="87d84-171">The default value is controlled by the operating system.</span></span> <span data-ttu-id="87d84-172">La valeur par défaut pour Windows 10 est 128 tronçons.</span><span class="sxs-lookup"><span data-stu-id="87d84-172">The default value for Windows 10 is 128 hops.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-173">-Ping</span><span class="sxs-lookup"><span data-stu-id="87d84-173">-Ping</span></span>

<span data-ttu-id="87d84-174">Fait en sorte que l’applet de commande effectue un test ping.</span><span class="sxs-lookup"><span data-stu-id="87d84-174">Causes the cmdlet to do a ping test.</span></span> <span data-ttu-id="87d84-175">Il s’agit du mode par défaut de l’applet de commande `Test-Connection` .</span><span class="sxs-lookup"><span data-stu-id="87d84-175">This is the default mode for the `Test-Connection` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-176">-Quiet</span><span class="sxs-lookup"><span data-stu-id="87d84-176">-Quiet</span></span>

<span data-ttu-id="87d84-177">Le paramètre **Quiet** retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="87d84-177">The **Quiet** parameter returns a **Boolean** value.</span></span> <span data-ttu-id="87d84-178">L’utilisation de ce paramètre supprime toutes les erreurs.</span><span class="sxs-lookup"><span data-stu-id="87d84-178">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="87d84-179">Chaque connexion testée retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="87d84-179">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="87d84-180">Si le paramètre **TargetName** spécifie plusieurs ordinateurs, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="87d84-180">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="87d84-181">Si **une** commande ping vers une cible donnée est réussie, `$True` est retourné.</span><span class="sxs-lookup"><span data-stu-id="87d84-181">If **any** ping to a given target succeeds, `$True` is returned.</span></span>

<span data-ttu-id="87d84-182">Si **tous les** pings vers une cible donnée échouent, `$False` est retourné.</span><span class="sxs-lookup"><span data-stu-id="87d84-182">If **all** pings to a given target fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="87d84-183">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="87d84-183">-ResolveDestination</span></span>

<span data-ttu-id="87d84-184">Force l’applet de commande à tenter de résoudre le nom DNS de la cible.</span><span class="sxs-lookup"><span data-stu-id="87d84-184">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span> <span data-ttu-id="87d84-185">Lorsqu’ils sont utilisés conjointement avec le paramètre **traceroute** , les noms DNS de tous les hôtes intermédiaires sont également récupérés, si possible.</span><span class="sxs-lookup"><span data-stu-id="87d84-185">When used in conjunction with the **Traceroute** parameter, the DNS names of all intermediate hosts will also be retrieved, if possible.</span></span>

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

### <span data-ttu-id="87d84-186">-Source</span><span class="sxs-lookup"><span data-stu-id="87d84-186">-Source</span></span>

<span data-ttu-id="87d84-187">Spécifie le nom des ordinateurs d’où le ping provient.</span><span class="sxs-lookup"><span data-stu-id="87d84-187">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="87d84-188">Entrez une liste de noms d’ordinateurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="87d84-188">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="87d84-189">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="87d84-189">The default is the local computer.</span></span>

<span data-ttu-id="87d84-190">**Remarque :** Ce paramètre ne fonctionne pas dans les versions 6 et ultérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87d84-190">**NOTE:** This parameter is not functional in PowerShell versions 6 and up.</span></span>
<span data-ttu-id="87d84-191">La spécification de ce paramètre n’aura aucun effet sur la commande.</span><span class="sxs-lookup"><span data-stu-id="87d84-191">Supplying this parameter will have no effect on the command.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultPing, RepeatPing, TraceRoute, TcpPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-192">-TargetName</span><span class="sxs-lookup"><span data-stu-id="87d84-192">-TargetName</span></span>

<span data-ttu-id="87d84-193">Spécifie le ou les ordinateurs à tester.</span><span class="sxs-lookup"><span data-stu-id="87d84-193">Specifies the computer(s) to test.</span></span> <span data-ttu-id="87d84-194">Tapez le nom des ordinateurs ou les adresses IP au format IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="87d84-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span>

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

### <span data-ttu-id="87d84-195">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="87d84-195">-TimeoutSeconds</span></span>

<span data-ttu-id="87d84-196">Définit la valeur du délai d’attente pour le test.</span><span class="sxs-lookup"><span data-stu-id="87d84-196">Sets the timeout value for the test.</span></span> <span data-ttu-id="87d84-197">Le test échoue si aucune réponse n’est reçue avant l’expiration du délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="87d84-197">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="87d84-198">La valeur par défaut est cinq secondes.</span><span class="sxs-lookup"><span data-stu-id="87d84-198">The default is five seconds.</span></span>

<span data-ttu-id="87d84-199">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="87d84-199">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="87d84-200">-Traceroute</span><span class="sxs-lookup"><span data-stu-id="87d84-200">-Traceroute</span></span>

<span data-ttu-id="87d84-201">Fait en sorte que l’applet de commande effectue un test traceroute.</span><span class="sxs-lookup"><span data-stu-id="87d84-201">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="87d84-202">Lorsque ce paramètre est utilisé, l’applet de commande retourne un `TestConnectionCommand+TraceStatus` objet.</span><span class="sxs-lookup"><span data-stu-id="87d84-202">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceStatus` object.</span></span>

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

### <span data-ttu-id="87d84-203">-MtuSize</span><span class="sxs-lookup"><span data-stu-id="87d84-203">-MtuSize</span></span>

<span data-ttu-id="87d84-204">Ce paramètre permet de découvrir la taille de la MTU du chemin.</span><span class="sxs-lookup"><span data-stu-id="87d84-204">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="87d84-205">L’applet de commande retourne un objet **PingReply # MTUSize** qui contient la taille du chemin d’accès MTU à la cible.</span><span class="sxs-lookup"><span data-stu-id="87d84-205">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="87d84-206">Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="87d84-206">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MtuSizeDetect
Aliases: MtuSizeDetect

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-207">-TcpPort</span><span class="sxs-lookup"><span data-stu-id="87d84-207">-TcpPort</span></span>

<span data-ttu-id="87d84-208">Spécifie le numéro de port TCP sur la cible à utiliser dans le test de connexion TCP.</span><span class="sxs-lookup"><span data-stu-id="87d84-208">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="87d84-209">L’applet de commande tente d’établir une connexion TCP au port spécifié sur la cible.</span><span class="sxs-lookup"><span data-stu-id="87d84-209">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

<span data-ttu-id="87d84-210">Si une connexion peut être établie, `$True` est retourné.</span><span class="sxs-lookup"><span data-stu-id="87d84-210">If a connection can be made, `$True` will be returned.</span></span>

<span data-ttu-id="87d84-211">Si une connexion ne peut pas être établie, `$False` est retourné.</span><span class="sxs-lookup"><span data-stu-id="87d84-211">If a connection cannot be made, `$False` will be returned.</span></span>

```yaml
Type: System.Int32
Parameter Sets: TcpPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87d84-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="87d84-212">CommonParameters</span></span>

<span data-ttu-id="87d84-213">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="87d84-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="87d84-214">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="87d84-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="87d84-215">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="87d84-215">INPUTS</span></span>

### <span data-ttu-id="87d84-216">Aucun</span><span class="sxs-lookup"><span data-stu-id="87d84-216">None</span></span>

<span data-ttu-id="87d84-217">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="87d84-217">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="87d84-218">SORTIES</span><span class="sxs-lookup"><span data-stu-id="87d84-218">OUTPUTS</span></span>

### <span data-ttu-id="87d84-219">TestConnectionCommand + PingStatus, TestConnectionCommand + TraceStatus, Boolean, TestConnectionCommand + PingMtuStatus</span><span class="sxs-lookup"><span data-stu-id="87d84-219">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span></span>

<span data-ttu-id="87d84-220">Par défaut, `Test-Connection` retourne un objet **TestConnectionCommand + PingStatus** pour chaque réponse ping.</span><span class="sxs-lookup"><span data-stu-id="87d84-220">By default, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object for each ping reply.</span></span>

<span data-ttu-id="87d84-221">Si vous spécifiez le paramètre **traceroute** , l’applet de commande renverra un objet **TestConnectionCommand + TraceStatus** pour chaque réponse ping sur l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="87d84-221">If you specify the **Traceroute** parameter, the cmdlet will return a **TestConnectionCommand+TraceStatus** object for each ping reply along the route.</span></span>

<span data-ttu-id="87d84-222">Si vous spécifiez les paramètres **Quiet** ou **TCPPort** , elle retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="87d84-222">If you specify the **Quiet** or **TcpPort** parameters, it returns a **Boolean** value.</span></span> <span data-ttu-id="87d84-223">Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="87d84-223">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="87d84-224">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="87d84-224">NOTES</span></span>

## <span data-ttu-id="87d84-225">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="87d84-225">RELATED LINKS</span></span>

[<span data-ttu-id="87d84-226">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="87d84-226">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="87d84-227">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="87d84-227">Stop-Computer</span></span>](Stop-Computer.md)

