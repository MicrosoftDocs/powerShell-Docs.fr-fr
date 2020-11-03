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
# Test-Connection

## SYNOPSIS
Envoie des paquets de demande d’écho ICMP ou des pings à un ou plusieurs ordinateurs.

## SYNTAX

### PingCount (par défaut)

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### PingContinues

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### DetectionOfMTUSize

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### Détermination

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### ConnectionByTCPPort

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## Description

L' `Test-Connection` applet de commande envoie des paquets de demande d’écho ICMP (Internet Control Message Protocol) à un ou plusieurs ordinateurs distants, et renvoie les réponses de réponse à écho. Vous pouvez utiliser cette applet de commande pour déterminer si un ordinateur particulier peut être contacté via un réseau IP.

Vous pouvez utiliser les paramètres de `Test-Connection` pour spécifier les ordinateurs d’envoi et de réception, exécuter la commande en tant que tâche en arrière-plan, définir un délai d’attente et un nombre de pings, et configurer la connexion et l’authentification.

Contrairement à la commande **ping** familière, `Test-Connection` retourne un objet **TestConnectionCommand + PingReport** que vous pouvez examiner dans PowerShell. Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** pour chaque connexion testée. Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.

## EXEMPLES

### Exemple 1 : envoyer des demandes d’écho à un ordinateur distant

Cet exemple envoie des paquets de demande d’écho de l’ordinateur local à l’ordinateur SERVEUR01.

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

`Test-Connection` utilise le paramètre **TargetName** pour spécifier l’ordinateur SERVEUR01. Le paramètre **IPv4** spécifie le protocole pour le test.

Le résultat de la commande ping est envoyé au flux d' **informations** lorsque l’objet **TestConnectionCommand + PingReport** est envoyé au flux de **réussite** . Pour plus d’informations sur les flux de sortie, consultez [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).

### Exemple 2 : envoyer des demandes d’écho à plusieurs ordinateurs

Cet exemple envoie des pings de l’ordinateur local à plusieurs ordinateurs distants.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### Exemple 3 : envoyer des demandes d’écho de plusieurs ordinateurs à un ordinateur

Cet exemple envoie des pings de différents ordinateurs sources à un ordinateur distant unique, SERVEUR01.

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

Utilisez ce format de commande pour tester la latence des connexions à partir de plusieurs points.

### Exemple 4 : utiliser des paramètres pour personnaliser la commande de test

Cet exemple utilise les paramètres de `Test-Connection` pour personnaliser la commande. L’ordinateur local envoie un test ping à un ordinateur distant.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` utilise le paramètre **TargetName** pour spécifier SERVEUR01. Le paramètre **Count** spécifie trois pings envoyés à l’ordinateur SERVEUR01 avec un **délai** de 2 secondes.

Vous pouvez utiliser ces options lorsque la réponse ping est censée prendre plus de temps que d’habitude, soit en raison d’un nombre de tronçons étendu ou d’une condition de réseau à trafic élevé.

### Exemple 5 : exécuter un test en tant que tâche en arrière-plan

Cet exemple montre comment exécuter une `Test-Connection` commande en tant que tâche en arrière-plan PowerShell.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

La `Start-Job` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur de nombreux ordinateurs d’une entreprise.
La valeur du paramètre **TargetName** est une `Get-Content` commande qui lit une liste de noms d’ordinateurs à partir du `Servers.txt` fichier. La commande utilise l' `Start-Job` applet de commande pour exécuter la commande en tant que tâche en arrière-plan et elle enregistre la tâche dans la `$job` variable.

La `if` commande vérifie que le travail n’est pas encore en cours d’exécution. Si le travail n’est pas en cours d’exécution, `Receive-Job` obtient les résultats et les stocke dans la `$Results` variable.

### Exemple 6 : créer une session uniquement si un test de connexion a échoué

Cet exemple crée une session sur l’ordinateur SERVEUR01 uniquement si au moins l’un des pings envoyés à l’ordinateur est correctement effectué.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

La `if` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur l’ordinateur SERVEUR01. La commande utilise le paramètre **Quiet** , qui retourne une valeur **booléenne** au lieu d’un objet **TestConnectionCommand + PingReport** .

La valeur est `$True` si l’un des quatre pings s’effectue correctement. Si aucune des commandes ping n’est établie, la valeur est `$False` .

Si la `Test-Connection` commande retourne la valeur `$True` , la commande utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** .

### Exemple 7 : utiliser le paramètre traceroute

À compter de PowerShell 6,0, le paramètre **traceroute** mappe un itinéraire entre l’ordinateur local et la destination distante que vous spécifiez avec le paramètre **TargetName** .

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

La `Test-Connection` commande utilise le paramètre **traceroute** . Les résultats, qui sont des `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objets, sont dirigés vers l’applet de commande `ForEach-Object` . `ForEach-Object` crée une sortie structurée des `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objets contenus et des `[System.Net.NetworkInformation.PingReply]` objets suivants.

## PARAMETERS

### -BufferSize

Spécifie la taille (en octets) de la mémoire tampon envoyée avec cette commande. La valeur par défaut est 32.

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

### -Nombre

Spécifie le nombre de demandes d’écho à envoyer. La valeur par défaut est 4.

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

### -Délai

Spécifie l’intervalle entre les pings (en secondes).

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

### -DontFragment

Ce paramètre définit l’indicateur de non **fragmentation** dans l’en-tête IP. Vous pouvez utiliser ce paramètre avec le paramètre **bufferSize** pour tester la taille de la MTU du chemin. Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.

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

### -IPv4

Force l’applet de commande à utiliser le protocole IPv4 pour le test.

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

### -IPv6

Force l’applet de commande à utiliser le protocole IPv6 pour le test.

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

### -MaxHops

Définit le nombre maximal de tronçons qu’un message de demande ICMP peut envoyer. La valeur par défaut est contrôlée par le système d’exploitation. La valeur par défaut pour Windows 10 est 128 tronçons.

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

### -Ping

Fait en sorte que l’applet de commande effectue un test ping, qui est l’action par défaut.

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

### -Quiet

Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** . L’utilisation de ce paramètre supprime toutes les erreurs.

Chaque connexion testée retourne une valeur **booléenne** . Si le paramètre **TargetName** spécifie plusieurs ordinateurs, un tableau de valeurs **booléennes** est retourné.

Si **une** commande ping est réussie, `$True` est retourné.

Si **tous les** pings échouent, `$False` est retourné.

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

### -ResolveDestination

Force l’applet de commande à tenter de résoudre le nom DNS de la cible.

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

### -Source

Spécifie le nom des ordinateurs d’où le ping provient. Entrez une liste de noms d’ordinateurs séparés par des virgules. La valeur par défaut est l'ordinateur local.

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

### -TargetName

Spécifie les ordinateurs à tester. Tapez le nom des ordinateurs ou les adresses IP au format IPv4 ou IPv6. Les caractères génériques ne sont pas autorisés. Ce paramètre est obligatoire. **ComputerName** est un alias pour ce paramètre.

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

### -TCPPort

Spécifie le numéro de port TCP sur la cible à utiliser dans le test de connexion TCP. L’applet de commande tente d’établir une connexion TCP au port spécifié sur la cible.

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

### -TimeoutSeconds

Définit la valeur du délai d’attente pour le test. Le test échoue si aucune réponse n’est reçue avant l’expiration du délai d’attente. La valeur par défaut est cinq secondes.

Ce paramètre a été introduit dans PowerShell 6,0.

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

### -Traceroute

Fait en sorte que l’applet de commande effectue un test traceroute. Lorsque ce paramètre est utilisé, l’applet de commande retourne un `TestConnectionCommand+TraceRouteResult` objet.

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

### -Continue

Fait en sorte que l’applet de commande envoie continuellement des demandes ping. Ce paramètre ne peut pas être utilisé avec le paramètre **Count** .

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

### -MTUSizeDetect

Ce paramètre permet de découvrir la taille de la MTU du chemin. L’applet de commande retourne un objet **PingReply # MTUSize** qui contient la taille du chemin d’accès MTU à la cible. Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’entrée vers cette applet de commande.

## SORTIES

### TestConnectionCommand + PingReport, TestConnectionCommand + TraceRouteResult, Boolean, PingReply # MTUSize

Si vous spécifiez le paramètre **Quiet** , elle retourne une valeur **booléenne** . Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné. Sinon, `Test-Connection` retourne un objet **TestConnectionCommand + PingReport** pour chaque test ping.

## REMARQUES

## LIENS CONNEXES

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
