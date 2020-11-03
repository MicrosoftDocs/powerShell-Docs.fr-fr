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
# Test-Connection

## SYNOPSIS
Envoie des paquets de demande d’écho ICMP ou des pings à un ou plusieurs ordinateurs.

## SYNTAX

### Valeur par défaut (par défaut)

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### Source

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### Quiet

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## Description

L' `Test-Connection` applet de commande envoie des paquets de demande d’écho ICMP (Internet Control Message Protocol) à un ou plusieurs ordinateurs distants, et renvoie les réponses de réponse à écho. Vous pouvez utiliser cette applet de commande pour déterminer si un ordinateur particulier peut être contacté via un réseau IP.

Vous pouvez utiliser les paramètres de `Test-Connection` pour spécifier les ordinateurs d’envoi et de réception, exécuter la commande en tant que tâche en arrière-plan, définir un délai d’attente et un nombre de pings, et configurer la connexion et l’authentification.

Contrairement à la commande **ping** familière, `Test-Connection` retourne un objet **Win32_PingStatus** que vous pouvez examiner dans PowerShell. Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** pour chaque connexion testée. Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné.

## EXEMPLES

### Exemple 1 : envoyer des demandes d’écho à un ordinateur distant

Cet exemple envoie des paquets de demande d’écho de l’ordinateur local à l’ordinateur SERVEUR01.

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

`Test-Connection` utilise le paramètre **ComputerName** pour spécifier l’ordinateur SERVEUR01.

### Exemple 2 : envoyer des demandes d’écho à plusieurs ordinateurs

Cet exemple envoie des pings de l’ordinateur local à plusieurs ordinateurs distants.

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### Exemple 3 : envoyer des demandes d’écho de plusieurs ordinateurs à un ordinateur

Cet exemple envoie des pings de différents ordinateurs sources à un ordinateur distant unique, SERVEUR01.

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

`Test-Connection` utilise le paramètre **Credential** pour spécifier les informations d’identification d’un utilisateur qui a l’autorisation d’envoyer une demande ping à partir des ordinateurs sources. Utilisez ce format de commande pour tester la latence des connexions à partir de plusieurs points.

### Exemple 4 : utiliser des paramètres pour personnaliser la commande de test

Cet exemple utilise les paramètres de `Test-Connection` pour personnaliser la commande. L’ordinateur local envoie un test ping à un ordinateur distant.

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

`Test-Connection` utilise le paramètre **ComputerName** pour spécifier SERVEUR01. Le paramètre **Count** spécifie trois pings envoyés à l’ordinateur SERVEUR01 avec un **délai** de 2 secondes.

Vous pouvez utiliser ces options lorsque la réponse ping est censée prendre plus de temps que d’habitude, soit en raison d’un nombre de tronçons étendu ou d’une condition de réseau à trafic élevé.

### Exemple 5 : exécuter un test en tant que tâche en arrière-plan

Cet exemple montre comment exécuter une `Test-Connection` commande en tant que tâche en arrière-plan PowerShell.

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

La `Test-Connection` commande exécute une commande ping sur de nombreux ordinateurs d’une entreprise. La valeur du paramètre **ComputerName** est une `Get-Content` commande qui lit une liste de noms d’ordinateurs à partir du `Servers.txt file` . La commande utilise le paramètre **AsJob** pour exécuter la commande en tant que tâche en arrière-plan et elle enregistre la tâche dans la `$job` variable.

La `if` commande vérifie que le travail n’est pas encore en cours d’exécution. Si le travail n’est pas en cours d’exécution, `Receive-Job` obtient les résultats et les stocke dans la `$Results` variable.

### Exemple 6 : exécuter une commande ping sur un ordinateur distant avec des informations d’identification

Cette commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur un ordinateur distant.

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

La commande utilise le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation d’exécuter une commande ping sur l’ordinateur distant et le paramètre d' **emprunt d’identité** pour modifier le niveau d’emprunt d’identité à **identifier** .

### Exemple 7 : créer une session uniquement si un test de connexion a échoué

Cet exemple crée une session sur l’ordinateur SERVEUR01 uniquement si au moins l’un des pings envoyés à l’ordinateur est correctement effectué.

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

La `if` commande utilise l' `Test-Connection` applet de commande pour effectuer un test ping sur l’ordinateur SERVEUR01. La commande utilise le paramètre **Quiet** , qui retourne une valeur **booléenne** au lieu d’un objet **Win32_PingStatus** . La valeur est `$True` si l’un des quatre pings s’effectue correctement et est, sinon, `$False` .

Si la `Test-Connection` commande retourne la valeur `$True` , la commande utilise l' `New-PSSession` applet de commande pour créer la **session PSSession** .

## PARAMETERS

### -AsJob

Indique que cette applet de commande s’exécute en tant que tâche en arrière-plan.

Pour utiliser ce paramètre, les ordinateurs locaux et distants doivent être configurés pour la communication à distance et, sous Windows Vista et les versions ultérieures du système d’exploitation Windows, vous devez ouvrir PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** . Pour plus d'informations, consultez [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).

Lorsque vous spécifiez le paramètre **AsJob** , la commande retourne immédiatement un objet qui représente la tâche en arrière-plan. Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche. La tâche est créée sur l'ordinateur local et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local. Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.

Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) et [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).

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

### -BufferSize

Spécifie la taille (en octets) de la mémoire tampon envoyée avec cette commande. La valeur par défaut est 32.

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

### -ComputerName

Spécifie les ordinateurs sur lesquels effectuer un test ping. Tapez le nom des ordinateurs ou les adresses IP au format IPv4 ou IPv6. Les caractères génériques ne sont pas autorisés. Ce paramètre est obligatoire.

Ce paramètre ne s’appuie pas sur la communication à distance PowerShell. Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

> [!NOTE]
> Le paramètre **ComputerName** est renommé en **TargetName** dans PowerShell 6,0 et versions ultérieures.

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

### -Nombre

Spécifie le nombre de demandes d’écho à envoyer. La valeur par défaut est 4.

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

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’envoyer une demande Ping à partir de l’ordinateur source. Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui de l’applet de commande `Get-Credential` .

Le paramètre **Credential** est valide uniquement lorsque le paramètre **Source** est utilisé dans la commande. Les informations d’identification n’affectent pas l’ordinateur de destination.

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

### -DcomAuthentication

Spécifie le niveau d’authentification que cette applet de commande utilise avec WMI.
`Test-Connection` utilise WMI.
Les valeurs valides pour ce paramètre sont :

- **Par défaut** . Authentification Windows
- **Aucun** . aucune authentification COM.
- **Connectez-vous** . authentification COM au niveau de la connexion
- **Appelez** . authentification COM au niveau de l'appel.
- **Paquet** . Authentification COM au niveau du paquet
- **PacketIntegrity** . authentification COM au niveau de l'intégrité du paquet.
- **PacketPrivacy** . Authentification COM au niveau de la confidentialité du paquet
- **Inchangé** . Identique à la commande précédente

La valeur par défaut est **Packet** qui a une valeur énumérée de **4** . Pour plus d’informations sur les valeurs de ce paramètre, consultez énumération [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) .

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

### -Délai

Spécifie l’intervalle entre les pings (en secondes).

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

### -Emprunt d’identité

Spécifie le niveau d’emprunt d’identité à utiliser lorsque cette applet de commande appelle WMI. `Test-Connection` utilise WMI.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- **Par défaut** . Emprunt d'identité par défaut.
- **Anonyme** . masque l'identité de l'appelant.
- **Identifiez** . Permet aux objets d'interroger les informations d'identification de l'appelant.
- **Emprunter l’identité** . Permet aux objets d'utiliser les informations d'identification de l'appelant.

La valeur par défaut est **Impersonate** .

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

### -Protocol

Spécifie un protocole. Les valeurs acceptables pour ce paramètre sont DCOM et WSMan.

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

### -Quiet

Le paramètre **Quiet** retourne une valeur **booléenne** dans un objet **System. Boolean** . L’utilisation de ce paramètre supprime toutes les erreurs.

Chaque connexion testée retourne une valeur **booléenne** . Si le paramètre **ComputerName** spécifie plusieurs ordinateurs, un tableau de valeurs **booléennes** est retourné.

Si **une** commande ping est réussie, `$True` est retourné.

Si **tous les** pings échouent, `$False` est retourné.

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

### -Source

Spécifie le nom des ordinateurs d’où le ping provient. Entrez une liste de noms d’ordinateurs séparés par des virgules. La valeur par défaut est l'ordinateur local.

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

### -ThrottleLimit

Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.
Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.

La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

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

### -TimeToLive

Spécifie la durée maximale pendant laquelle un paquet peut être transféré. Pour chaque tronçon dans les passerelles, les routeurs, etc., la valeur de **TimeToLive** est diminuée d’une unité. À zéro, le paquet est rejeté et une erreur est retournée.
Dans **Windows** , la valeur par défaut est **128** . L’alias du paramètre **TimeToLive** est **TTL** .

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

### -WsmanAuthentication

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan.
Les valeurs valides pour ce paramètre sont :

- Basic
- CredSSP
- Default
- Digest
- Kerberos
- Negotiate.

La valeur par défaut est Default.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).

ATTENTION : l’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.
Ce mécanisme augmente le risque de sécurité lié à l'opération distante.
Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’entrée vers cette applet de commande.

## SORTIES

### System. Management. ManagementObject # root\cimv2\ Win32_PingStatus, System. Management. Automation. RemotingJob, System. Boolean

Cette applet de commande retourne un objet de traitement, si vous spécifiez le paramètre **AsJob** .

Si vous spécifiez le paramètre **Quiet** , elle retourne une valeur **booléenne** . Si plusieurs connexions sont testées, un tableau de valeurs **booléennes** est retourné. Sinon, `Test-Connection` retourne un objet **Win32_PingStatus** pour chaque test ping.

## REMARQUES

Cette applet de commande utilise la classe **Win32_PingStatus** . Une `Get-WMIObject Win32_PingStatus` commande est équivalente à une `Test-Connection` commande.

Le jeu de paramètres **source** a été introduit dans PowerShell 3,0.

## LIENS CONNEXES

[Add-Computer](Add-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
