---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: af8a953536bb9683ba737522ad738348c5c695e2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598786"
---
# <span data-ttu-id="7a30a-102">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="7a30a-102">Test-Connection</span></span>

## <span data-ttu-id="7a30a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7a30a-103">SYNOPSIS</span></span>
<span data-ttu-id="7a30a-104">Envoie des paquets de demande d’écho ICMP ou des pings à un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="7a30a-104">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="7a30a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="7a30a-105">SYNTAX</span></span>

### <span data-ttu-id="7a30a-106">DefaultPing (par défaut)</span><span class="sxs-lookup"><span data-stu-id="7a30a-106">DefaultPing (Default)</span></span>

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="7a30a-107">RepeatPing</span><span class="sxs-lookup"><span data-stu-id="7a30a-107">RepeatPing</span></span>

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="7a30a-108">MtuSizeDetect</span><span class="sxs-lookup"><span data-stu-id="7a30a-108">MtuSizeDetect</span></span>

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="7a30a-109">Détermination</span><span class="sxs-lookup"><span data-stu-id="7a30a-109">TraceRoute</span></span>

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="7a30a-110">TcpPort</span><span class="sxs-lookup"><span data-stu-id="7a30a-110">TcpPort</span></span>

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="7a30a-111">Description</span><span class="sxs-lookup"><span data-stu-id="7a30a-111">DESCRIPTION</span></span>

<span data-ttu-id="7a30a-112">L' `Test-Connection` applet de commande envoie des paquets de demande d’écho ICMP (Internet Control Message Protocol) à un ou plusieurs ordinateurs distants, et renvoie les réponses de réponse à écho.</span><span class="sxs-lookup"><span data-stu-id="7a30a-112">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="7a30a-113">Vous pouvez utiliser cette applet de commande pour déterminer si un ordinateur particulier peut être contacté via un réseau IP.</span><span class="sxs-lookup"><span data-stu-id="7a30a-113">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="7a30a-114">Vous pouvez utiliser les paramètres de `Test-Connection` pour spécifier les ordinateurs d’envoi et de réception, exécuter la commande en tant que tâche en arrière-plan, définir un délai d’attente et un nombre de pings, et configurer la connexion et l’authentification.</span><span class="sxs-lookup"><span data-stu-id="7a30a-114">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="7a30a-115">Contrairement à la commande **ping** familière, `Test-Connection` retourne un objet **TestConnectionCommand + PingStatus** que vous pouvez examiner dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a30a-115">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="7a30a-116">Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** pour chaque connexion testée.</span><span class="sxs-lookup"><span data-stu-id="7a30a-116">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="7a30a-117">Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="7a30a-117">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="7a30a-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7a30a-118">EXAMPLES</span></span>

### <span data-ttu-id="7a30a-119">Exemple 1 : envoyer des demandes d’écho à un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="7a30a-119">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="7a30a-120">Cet exemple envoie des paquets de demande d’écho de l’ordinateur local à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="7a30a-120">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="7a30a-121">`Test-Connection` utilise le paramètre **TargetName** pour spécifier l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="7a30a-121">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="7a30a-122">Le paramètre **IPv4** spécifie le protocole pour le test.</span><span class="sxs-lookup"><span data-stu-id="7a30a-122">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="7a30a-123">Une série d’objets **TestConnectionCommand + PingStatus** sont envoyées au flux de sortie, un objet par réponse ping de l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="7a30a-123">A series of **TestConnectionCommand+PingStatus** objects are sent to the output stream, one object per ping reply from the target machine.</span></span>

### <span data-ttu-id="7a30a-124">Exemple 2 : envoyer des demandes d’écho à plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="7a30a-124">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="7a30a-125">Cet exemple envoie des pings de l’ordinateur local à plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="7a30a-125">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="7a30a-126">Exemple 3 : utiliser des paramètres pour personnaliser la commande de test</span><span class="sxs-lookup"><span data-stu-id="7a30a-126">Example 3: Use parameters to customize the test command</span></span>

<span data-ttu-id="7a30a-127">Cet exemple utilise les paramètres de `Test-Connection` pour personnaliser la commande.</span><span class="sxs-lookup"><span data-stu-id="7a30a-127">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="7a30a-128">L’ordinateur local envoie un test ping à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7a30a-128">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="7a30a-129">`Test-Connection` utilise le paramètre **TargetName** pour spécifier SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="7a30a-129">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="7a30a-130">Le paramètre **Count** spécifie trois pings envoyés à l’ordinateur SERVEUR01 avec un **délai** de 2 secondes.</span><span class="sxs-lookup"><span data-stu-id="7a30a-130">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="7a30a-131">Vous pouvez utiliser ces options lorsque la réponse ping est censée prendre plus de temps que d’habitude, soit en raison d’un nombre de tronçons étendu ou d’une condition de réseau à trafic élevé.</span><span class="sxs-lookup"><span data-stu-id="7a30a-131">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="7a30a-132">Exemple 4 : exécuter un test en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7a30a-132">Example 4: Run a test as a background job</span></span>

<span data-ttu-id="7a30a-133">Cet exemple montre comment exécuter une `Test-Connection` commande en tant que tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a30a-133">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

<span data-ttu-id="7a30a-134">La `Start-Job` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur de nombreux ordinateurs d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="7a30a-134">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="7a30a-135">La valeur du paramètre **TargetName** est une `Get-Content` commande qui lit une liste de noms d’ordinateurs à partir du `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="7a30a-135">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="7a30a-136">La commande utilise l' `Start-Job` applet de commande pour exécuter la commande en tant que tâche en arrière-plan et elle enregistre la tâche dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="7a30a-136">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="7a30a-137">La `Receive-Job` commande est invitée `-Wait` jusqu’à ce que le travail soit terminé, puis obtient les résultats et les stocke dans la `$Results` variable.</span><span class="sxs-lookup"><span data-stu-id="7a30a-137">The `Receive-Job` command is instructed to `-Wait` until the job is completed, and then gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="7a30a-138">Exemple 5 : créer une session uniquement si un test de connexion a échoué</span><span class="sxs-lookup"><span data-stu-id="7a30a-138">Example 5: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="7a30a-139">Cet exemple crée une session sur l’ordinateur SERVEUR01 uniquement si au moins l’un des pings envoyés à l’ordinateur est correctement effectué.</span><span class="sxs-lookup"><span data-stu-id="7a30a-139">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

<span data-ttu-id="7a30a-140">L' `Test-Connection` applet de commande exécute une commande ping sur l' `Server01` ordinateur, avec le paramètre **Quiet** fourni.</span><span class="sxs-lookup"><span data-stu-id="7a30a-140">The `Test-Connection` cmdlet pings the `Server01` computer, with the **Quiet** parameter provided.</span></span>
<span data-ttu-id="7a30a-141">La valeur obtenue est `$True` si l’un des quatre pings aboutit.</span><span class="sxs-lookup"><span data-stu-id="7a30a-141">The resulting value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="7a30a-142">Si aucune des commandes ping n’est établie, la valeur est `$False` .</span><span class="sxs-lookup"><span data-stu-id="7a30a-142">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="7a30a-143">Si la `Test-Connection` commande retourne la valeur `$True` , la commande utilise l' `New-PSSession` applet de commande pour créer la **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="7a30a-143">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

### <span data-ttu-id="7a30a-144">Exemple 6 : utiliser le paramètre traceroute</span><span class="sxs-lookup"><span data-stu-id="7a30a-144">Example 6: Use the Traceroute parameter</span></span>

<span data-ttu-id="7a30a-145">Introduite dans PowerShell 6,0, le paramètre **traceroute** mappe un itinéraire entre l’ordinateur local et la destination distante que vous spécifiez avec le paramètre **TargetName** .</span><span class="sxs-lookup"><span data-stu-id="7a30a-145">Introduced in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

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

<span data-ttu-id="7a30a-146">La `Test-Connection` commande est appelée avec le paramètre **traceroute** .</span><span class="sxs-lookup"><span data-stu-id="7a30a-146">The `Test-Connection` command is called with the **Traceroute** parameter.</span></span> <span data-ttu-id="7a30a-147">Les résultats, qui sont des `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objets, sont générés dans le flux de sortie de **réussite** .</span><span class="sxs-lookup"><span data-stu-id="7a30a-147">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objects, are output to the **Success** output stream.</span></span>

## <span data-ttu-id="7a30a-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a30a-148">PARAMETERS</span></span>

### <span data-ttu-id="7a30a-149">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="7a30a-149">-BufferSize</span></span>

<span data-ttu-id="7a30a-150">Spécifie la taille (en octets) de la mémoire tampon envoyée avec cette commande.</span><span class="sxs-lookup"><span data-stu-id="7a30a-150">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="7a30a-151">La valeur par défaut est 32.</span><span class="sxs-lookup"><span data-stu-id="7a30a-151">The default value is 32.</span></span>

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

### <span data-ttu-id="7a30a-152">-Répéter</span><span class="sxs-lookup"><span data-stu-id="7a30a-152">-Repeat</span></span>

<span data-ttu-id="7a30a-153">Fait en sorte que l’applet de commande envoie continuellement des demandes ping.</span><span class="sxs-lookup"><span data-stu-id="7a30a-153">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="7a30a-154">Ce paramètre ne peut pas être utilisé avec le paramètre **Count** .</span><span class="sxs-lookup"><span data-stu-id="7a30a-154">This parameter can't be used with the **Count** parameter.</span></span>

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

### <span data-ttu-id="7a30a-155">-Nombre</span><span class="sxs-lookup"><span data-stu-id="7a30a-155">-Count</span></span>

<span data-ttu-id="7a30a-156">Spécifie le nombre de demandes d’écho à envoyer.</span><span class="sxs-lookup"><span data-stu-id="7a30a-156">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="7a30a-157">La valeur par défaut est 4.</span><span class="sxs-lookup"><span data-stu-id="7a30a-157">The default value is 4.</span></span>

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

### <span data-ttu-id="7a30a-158">-Délai</span><span class="sxs-lookup"><span data-stu-id="7a30a-158">-Delay</span></span>

<span data-ttu-id="7a30a-159">Spécifie l’intervalle entre les pings (en secondes).</span><span class="sxs-lookup"><span data-stu-id="7a30a-159">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="7a30a-160">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="7a30a-160">-DontFragment</span></span>

<span data-ttu-id="7a30a-161">Ce paramètre définit l’indicateur de non **fragmentation** dans l’en-tête IP.</span><span class="sxs-lookup"><span data-stu-id="7a30a-161">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="7a30a-162">Vous pouvez utiliser ce paramètre avec le paramètre **bufferSize** pour tester la taille de la MTU du chemin.</span><span class="sxs-lookup"><span data-stu-id="7a30a-162">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="7a30a-163">Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="7a30a-163">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="7a30a-164">-IPv4</span><span class="sxs-lookup"><span data-stu-id="7a30a-164">-IPv4</span></span>

<span data-ttu-id="7a30a-165">Force l’applet de commande à utiliser le protocole IPv4 pour le test.</span><span class="sxs-lookup"><span data-stu-id="7a30a-165">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="7a30a-166">-IPv6</span><span class="sxs-lookup"><span data-stu-id="7a30a-166">-IPv6</span></span>

<span data-ttu-id="7a30a-167">Force l’applet de commande à utiliser le protocole IPv6 pour le test.</span><span class="sxs-lookup"><span data-stu-id="7a30a-167">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="7a30a-168">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="7a30a-168">-MaxHops</span></span>

<span data-ttu-id="7a30a-169">Définit le nombre maximal de tronçons qu’un message de demande ICMP peut envoyer.</span><span class="sxs-lookup"><span data-stu-id="7a30a-169">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="7a30a-170">La valeur par défaut est contrôlée par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7a30a-170">The default value is controlled by the operating system.</span></span> <span data-ttu-id="7a30a-171">La valeur par défaut pour Windows 10 est 128 tronçons.</span><span class="sxs-lookup"><span data-stu-id="7a30a-171">The default value for Windows 10 is 128 hops.</span></span>

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

### <span data-ttu-id="7a30a-172">-Ping</span><span class="sxs-lookup"><span data-stu-id="7a30a-172">-Ping</span></span>

<span data-ttu-id="7a30a-173">Fait en sorte que l’applet de commande effectue un test ping.</span><span class="sxs-lookup"><span data-stu-id="7a30a-173">Causes the cmdlet to do a ping test.</span></span> <span data-ttu-id="7a30a-174">Il s’agit du mode par défaut de l’applet de commande `Test-Connection` .</span><span class="sxs-lookup"><span data-stu-id="7a30a-174">This is the default mode for the `Test-Connection` cmdlet.</span></span>

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

### <span data-ttu-id="7a30a-175">-Quiet</span><span class="sxs-lookup"><span data-stu-id="7a30a-175">-Quiet</span></span>

<span data-ttu-id="7a30a-176">Le paramètre **Quiet** retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="7a30a-176">The **Quiet** parameter returns a **Boolean** value.</span></span> <span data-ttu-id="7a30a-177">L’utilisation de ce paramètre supprime toutes les erreurs.</span><span class="sxs-lookup"><span data-stu-id="7a30a-177">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="7a30a-178">Chaque connexion testée retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="7a30a-178">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="7a30a-179">Si le paramètre **TargetName** spécifie plusieurs ordinateurs, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="7a30a-179">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="7a30a-180">Si **une** commande ping vers une cible donnée est réussie, `$True` est retourné.</span><span class="sxs-lookup"><span data-stu-id="7a30a-180">If **any** ping to a given target succeeds, `$True` is returned.</span></span>

<span data-ttu-id="7a30a-181">Si **tous les** pings vers une cible donnée échouent, `$False` est retourné.</span><span class="sxs-lookup"><span data-stu-id="7a30a-181">If **all** pings to a given target fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="7a30a-182">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="7a30a-182">-ResolveDestination</span></span>

<span data-ttu-id="7a30a-183">Force l’applet de commande à tenter de résoudre le nom DNS de la cible.</span><span class="sxs-lookup"><span data-stu-id="7a30a-183">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span> <span data-ttu-id="7a30a-184">Lorsqu’ils sont utilisés conjointement avec le paramètre **traceroute** , les noms DNS de tous les hôtes intermédiaires sont également récupérés, si possible.</span><span class="sxs-lookup"><span data-stu-id="7a30a-184">When used in conjunction with the **Traceroute** parameter, the DNS names of all intermediate hosts will also be retrieved, if possible.</span></span>

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

### <span data-ttu-id="7a30a-185">-Source</span><span class="sxs-lookup"><span data-stu-id="7a30a-185">-Source</span></span>

<span data-ttu-id="7a30a-186">Spécifie le nom des ordinateurs d’où le ping provient.</span><span class="sxs-lookup"><span data-stu-id="7a30a-186">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="7a30a-187">Entrez une liste de noms d’ordinateurs séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7a30a-187">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="7a30a-188">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7a30a-188">The default is the local computer.</span></span>

<span data-ttu-id="7a30a-189">**Remarque :** Ce paramètre ne fonctionne pas dans les versions 6 et ultérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a30a-189">**NOTE:** This parameter is not functional in PowerShell versions 6 and up.</span></span>
<span data-ttu-id="7a30a-190">La spécification de ce paramètre n’aura aucun effet sur la commande.</span><span class="sxs-lookup"><span data-stu-id="7a30a-190">Supplying this parameter will have no effect on the command.</span></span>

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

### <span data-ttu-id="7a30a-191">-TargetName</span><span class="sxs-lookup"><span data-stu-id="7a30a-191">-TargetName</span></span>

<span data-ttu-id="7a30a-192">Spécifie le ou les ordinateurs à tester.</span><span class="sxs-lookup"><span data-stu-id="7a30a-192">Specifies the computer(s) to test.</span></span> <span data-ttu-id="7a30a-193">Tapez le nom des ordinateurs ou les adresses IP au format IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="7a30a-193">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span>

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

### <span data-ttu-id="7a30a-194">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="7a30a-194">-TimeoutSeconds</span></span>

<span data-ttu-id="7a30a-195">Définit la valeur du délai d’attente pour le test.</span><span class="sxs-lookup"><span data-stu-id="7a30a-195">Sets the timeout value for the test.</span></span> <span data-ttu-id="7a30a-196">Le test échoue si aucune réponse n’est reçue avant l’expiration du délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="7a30a-196">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="7a30a-197">La valeur par défaut est cinq secondes.</span><span class="sxs-lookup"><span data-stu-id="7a30a-197">The default is five seconds.</span></span>

<span data-ttu-id="7a30a-198">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="7a30a-198">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="7a30a-199">-Traceroute</span><span class="sxs-lookup"><span data-stu-id="7a30a-199">-Traceroute</span></span>

<span data-ttu-id="7a30a-200">Fait en sorte que l’applet de commande effectue un test traceroute.</span><span class="sxs-lookup"><span data-stu-id="7a30a-200">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="7a30a-201">Lorsque ce paramètre est utilisé, l’applet de commande retourne un `TestConnectionCommand+TraceStatus` objet.</span><span class="sxs-lookup"><span data-stu-id="7a30a-201">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceStatus` object.</span></span>

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

### <span data-ttu-id="7a30a-202">-MtuSize</span><span class="sxs-lookup"><span data-stu-id="7a30a-202">-MtuSize</span></span>

<span data-ttu-id="7a30a-203">Ce paramètre permet de découvrir la taille de la MTU du chemin.</span><span class="sxs-lookup"><span data-stu-id="7a30a-203">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="7a30a-204">L’applet de commande retourne un objet **PingReply # MTUSize** qui contient la taille du chemin d’accès MTU à la cible.</span><span class="sxs-lookup"><span data-stu-id="7a30a-204">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="7a30a-205">Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="7a30a-205">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="7a30a-206">-TcpPort</span><span class="sxs-lookup"><span data-stu-id="7a30a-206">-TcpPort</span></span>

<span data-ttu-id="7a30a-207">Spécifie le numéro de port TCP sur la cible à utiliser dans le test de connexion TCP.</span><span class="sxs-lookup"><span data-stu-id="7a30a-207">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="7a30a-208">L’applet de commande tente d’établir une connexion TCP au port spécifié sur la cible.</span><span class="sxs-lookup"><span data-stu-id="7a30a-208">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

<span data-ttu-id="7a30a-209">Si une connexion peut être établie, `$True` est retourné.</span><span class="sxs-lookup"><span data-stu-id="7a30a-209">If a connection can be made, `$True` will be returned.</span></span>

<span data-ttu-id="7a30a-210">Si une connexion ne peut pas être établie, `$False` est retourné.</span><span class="sxs-lookup"><span data-stu-id="7a30a-210">If a connection cannot be made, `$False` will be returned.</span></span>

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

### <span data-ttu-id="7a30a-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a30a-211">CommonParameters</span></span>

<span data-ttu-id="7a30a-212">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a30a-212">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a30a-213">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7a30a-213">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a30a-214">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7a30a-214">INPUTS</span></span>

### <span data-ttu-id="7a30a-215">None</span><span class="sxs-lookup"><span data-stu-id="7a30a-215">None</span></span>

<span data-ttu-id="7a30a-216">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7a30a-216">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="7a30a-217">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7a30a-217">OUTPUTS</span></span>

### <span data-ttu-id="7a30a-218">TestConnectionCommand + PingStatus, TestConnectionCommand + TraceStatus, Boolean, TestConnectionCommand + PingMtuStatus</span><span class="sxs-lookup"><span data-stu-id="7a30a-218">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span></span>

<span data-ttu-id="7a30a-219">Par défaut, `Test-Connection` retourne un objet **TestConnectionCommand + PingStatus** pour chaque réponse ping.</span><span class="sxs-lookup"><span data-stu-id="7a30a-219">By default, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object for each ping reply.</span></span>

<span data-ttu-id="7a30a-220">Si vous spécifiez le paramètre **traceroute** , l’applet de commande renverra un objet **TestConnectionCommand + TraceStatus** pour chaque réponse ping sur l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="7a30a-220">If you specify the **Traceroute** parameter, the cmdlet will return a **TestConnectionCommand+TraceStatus** object for each ping reply along the route.</span></span>

<span data-ttu-id="7a30a-221">Si vous spécifiez les paramètres **Quiet** ou **TCPPort** , elle retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="7a30a-221">If you specify the **Quiet** or **TcpPort** parameters, it returns a **Boolean** value.</span></span> <span data-ttu-id="7a30a-222">Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.</span><span class="sxs-lookup"><span data-stu-id="7a30a-222">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="7a30a-223">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7a30a-223">NOTES</span></span>

## <span data-ttu-id="7a30a-224">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7a30a-224">RELATED LINKS</span></span>

[<span data-ttu-id="7a30a-225">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="7a30a-225">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="7a30a-226">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="7a30a-226">Stop-Computer</span></span>](Stop-Computer.md)

