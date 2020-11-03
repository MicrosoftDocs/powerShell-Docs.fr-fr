---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 04e9e47055610ef8120b44f2418a0843e5901062
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201581"
---
# Test-Connection

## SYNOPSIS
Envoie des paquets de demande d’écho ICMP ou des pings à un ou plusieurs ordinateurs.

## SYNTAX

### DefaultPing (par défaut)

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### RepeatPing

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### MtuSizeDetect

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### Détermination

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TcpPort

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## Description

L' `Test-Connection` applet de commande envoie des paquets de demande d’écho ICMP (Internet Control Message Protocol) à un ou plusieurs ordinateurs distants, et renvoie les réponses de réponse à écho. Vous pouvez utiliser cette applet de commande pour déterminer si un ordinateur particulier peut être contacté via un réseau IP.

Vous pouvez utiliser les paramètres de `Test-Connection` pour spécifier les ordinateurs d’envoi et de réception, exécuter la commande en tant que tâche en arrière-plan, définir un délai d’attente et un nombre de pings, et configurer la connexion et l’authentification.

Contrairement à la commande **ping** familière, `Test-Connection` retourne un objet **TestConnectionCommand + PingStatus** que vous pouvez examiner dans PowerShell. Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** pour chaque connexion testée. Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.

## EXEMPLES

### Exemple 1 : envoyer des demandes d’écho à un ordinateur distant

Cet exemple envoie des paquets de demande d’écho de l’ordinateur local à l’ordinateur SERVEUR01.

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

`Test-Connection` utilise le paramètre **TargetName** pour spécifier l’ordinateur SERVEUR01. Le paramètre **IPv4** spécifie le protocole pour le test.

Une série d’objets **TestConnectionCommand + PingStatus** sont envoyées au flux de sortie, un objet par réponse ping de l’ordinateur cible.

### Exemple 2 : envoyer des demandes d’écho à plusieurs ordinateurs

Cet exemple envoie des pings de l’ordinateur local à plusieurs ordinateurs distants.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### Exemple 3 : utiliser des paramètres pour personnaliser la commande de test

Cet exemple utilise les paramètres de `Test-Connection` pour personnaliser la commande. L’ordinateur local envoie un test ping à un ordinateur distant.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` utilise le paramètre **TargetName** pour spécifier SERVEUR01. Le paramètre **Count** spécifie trois pings envoyés à l’ordinateur SERVEUR01 avec un **délai** de 2 secondes.

Vous pouvez utiliser ces options lorsque la réponse ping est censée prendre plus de temps que d’habitude, soit en raison d’un nombre de tronçons étendu ou d’une condition de réseau à trafic élevé.

### Exemple 4 : exécuter un test en tant que tâche en arrière-plan

Cet exemple montre comment exécuter une `Test-Connection` commande en tant que tâche en arrière-plan PowerShell.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

La `Start-Job` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur de nombreux ordinateurs d’une entreprise.
La valeur du paramètre **TargetName** est une `Get-Content` commande qui lit une liste de noms d’ordinateurs à partir du `Servers.txt` fichier. La commande utilise l' `Start-Job` applet de commande pour exécuter la commande en tant que tâche en arrière-plan et elle enregistre la tâche dans la `$job` variable.

La `Receive-Job` commande est invitée `-Wait` jusqu’à ce que le travail soit terminé, puis obtient les résultats et les stocke dans la `$Results` variable.

### Exemple 5 : créer une session uniquement si un test de connexion a échoué

Cet exemple crée une session sur l’ordinateur SERVEUR01 uniquement si au moins l’un des pings envoyés à l’ordinateur est correctement effectué.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

L' `Test-Connection` applet de commande exécute une commande ping sur l' `Server01` ordinateur, avec le paramètre **Quiet** fourni.
La valeur obtenue est `$True` si l’un des quatre pings aboutit. Si aucune des commandes ping n’est établie, la valeur est `$False` .

Si la `Test-Connection` commande retourne la valeur `$True` , la commande utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** .

### Exemple 6 : utiliser le paramètre traceroute

Introduite dans PowerShell 6,0, le paramètre **traceroute** mappe un itinéraire entre l’ordinateur local et la destination distante que vous spécifiez avec le paramètre **TargetName** .

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

La `Test-Connection` commande est appelée avec le paramètre **traceroute** . Les résultats, qui sont des `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objets, sont générés dans le flux de sortie de **réussite** .

## PARAMETERS

### -BufferSize

Spécifie la taille (en octets) de la mémoire tampon envoyée avec cette commande. La valeur par défaut est 32.

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

### -Répéter

Fait en sorte que l’applet de commande envoie continuellement des demandes ping. Ce paramètre ne peut pas être utilisé avec le paramètre **Count** .

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

### -Nombre

Spécifie le nombre de demandes d’écho à envoyer. La valeur par défaut est 4.

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

### -Délai

Spécifie l’intervalle entre les pings (en secondes).

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

### -DontFragment

Ce paramètre définit l’indicateur de non **fragmentation** dans l’en-tête IP. Vous pouvez utiliser ce paramètre avec le paramètre **bufferSize** pour tester la taille de la MTU du chemin. Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.

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
Parameter Sets: DefaultPing, RepeatPing, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

Fait en sorte que l’applet de commande effectue un test ping. Il s’agit du mode par défaut de l’applet de commande `Test-Connection` .

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

### -Quiet

Le paramètre **Quiet** retourne une valeur **booléenne** . L’utilisation de ce paramètre supprime toutes les erreurs.

Chaque connexion testée retourne une valeur **booléenne** . Si le paramètre **TargetName** spécifie plusieurs ordinateurs, un tableau de valeurs **booléennes** est retourné.

Si **une** commande ping vers une cible donnée est réussie, `$True` est retourné.

Si **tous les** pings vers une cible donnée échouent, `$False` est retourné.

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

Force l’applet de commande à tenter de résoudre le nom DNS de la cible. Lorsqu’ils sont utilisés conjointement avec le paramètre **traceroute** , les noms DNS de tous les hôtes intermédiaires sont également récupérés, si possible.

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

**Remarque :** Ce paramètre ne fonctionne pas dans les versions 6 et ultérieures de PowerShell.
La spécification de ce paramètre n’aura aucun effet sur la commande.

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

### -TargetName

Spécifie le ou les ordinateurs à tester. Tapez le nom des ordinateurs ou les adresses IP au format IPv4 ou IPv6.

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

Fait en sorte que l’applet de commande effectue un test traceroute. Lorsque ce paramètre est utilisé, l’applet de commande retourne un `TestConnectionCommand+TraceStatus` objet.

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

### -MtuSize

Ce paramètre permet de découvrir la taille de la MTU du chemin. L’applet de commande retourne un objet **PingReply # MTUSize** qui contient la taille du chemin d’accès MTU à la cible. Pour plus d’informations sur Path MTU, consultez l’article relatif à la [détection MTU Path](https://wikipedia.org/wiki/Path_MTU_Discovery) dans Wikipédia.

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

### -TcpPort

Spécifie le numéro de port TCP sur la cible à utiliser dans le test de connexion TCP. L’applet de commande tente d’établir une connexion TCP au port spécifié sur la cible.

Si une connexion peut être établie, `$True` est retourné.

Si une connexion ne peut pas être établie, `$False` est retourné.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’entrée vers cette applet de commande.

## SORTIES

### TestConnectionCommand + PingStatus, TestConnectionCommand + TraceStatus, Boolean, TestConnectionCommand + PingMtuStatus

Par défaut, `Test-Connection` retourne un objet **TestConnectionCommand + PingStatus** pour chaque réponse ping.

Si vous spécifiez le paramètre **traceroute** , l’applet de commande renverra un objet **TestConnectionCommand + TraceStatus** pour chaque réponse ping sur l’itinéraire.

Si vous spécifiez les paramètres **Quiet** ou **TCPPort** , elle retourne une valeur **booléenne** . Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.

## REMARQUES

## LIENS CONNEXES

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
