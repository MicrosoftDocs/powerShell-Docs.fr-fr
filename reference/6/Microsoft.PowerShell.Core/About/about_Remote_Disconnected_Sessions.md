---
description: Explique comment se déconnecter et se reconnecter à une session PowerShell (PSSession).
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 2f352ab123618f1ab9617e9d300f10f7a5e5928a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206926"
---
# <a name="about-remote-disconnected-sessions"></a>À propos des sessions déconnectées distantes

## <a name="short-description"></a>Description courte

Explique comment se déconnecter et se reconnecter à une session PowerShell (PSSession).

## <a name="long-description"></a>Description longue

À compter de PowerShell 3,0, vous pouvez vous déconnecter d’une session PSSession et vous reconnecter à la session PSSession sur le même ordinateur ou sur un autre ordinateur. L’état de session est conservé et les commandes de la session PSSession continuent à s’exécuter pendant que la session est déconnectée.

La fonctionnalité sessions déconnectées n’est disponible que lorsque l’ordinateur distant exécute PowerShell 3,0 ou une version ultérieure.

La fonctionnalité sessions déconnectées vous permet de fermer la session dans laquelle une session PSSession a été créée, et même de fermer PowerShell et d’arrêter l’ordinateur, sans interrompre les commandes qui s’exécutent dans la session PSSession. Les sessions déconnectées sont utiles pour exécuter des commandes qui prennent beaucoup de temps et fournissent la flexibilité du temps et des appareils requis par les professionnels de l’informatique.

Vous ne pouvez pas vous déconnecter d’une session interactive démarrée à l’aide de l’applet de commande `Enter-PSSession` .

Vous pouvez utiliser des sessions déconnectées pour gérer des sessions PSSession qui ont été déconnectés involontairement suite à une panne de réseau ou d’ordinateur.

Dans l’utilisation réelle, la fonctionnalité sessions déconnectées vous permet de commencer à résoudre un problème, d’attirer votre attention sur un problème de priorité plus élevée, puis de reprendre le travail sur la solution, même sur un autre ordinateur situé à un autre emplacement.

## <a name="disconnected-session-cmdlets"></a>Applets de commande de session déconnectée

Les applets de commande suivantes prennent en charge la fonctionnalité sessions déconnectées :

- `Connect-PSSession`: Se connecte à une session PSSession déconnectée.
- `Disconnect-PSSession`: Déconnecte une session PSSession.
- `Get-PSSession`: Obtient sessions PSSession sur l’ordinateur local ou sur des ordinateurs distants.
- `Receive-PSSession`: Obtient les résultats des commandes exécutées dans des sessions déconnectées.
- `Invoke-Command`: Le paramètre **InDisconnectedSession** crée une session PSSession et se déconnecte immédiatement.

## <a name="how-the-disconnected-sessions-feature-works"></a>Fonctionnement de la fonctionnalité sessions déconnectées

À compter de PowerShell 3,0, les sessions PSSession sont indépendants des sessions dans lesquelles ils sont créés. Les sessions PSSession actifs sont conservés sur l’ordinateur distant ou **côté serveur** de la connexion, même si la session dans laquelle la session PSSession a été créée est fermée et que l’ordinateur d’origine est arrêté ou déconnecté du réseau.

Dans PowerShell 2,0, la session PSSession est supprimée de l’ordinateur distant lorsqu’elle est déconnectée de la session d’origine ou que la session dans laquelle elle a été créée se termine.

Lorsque vous déconnectez une session PSSession, la session PSSession reste active et est conservée sur l’ordinateur distant. L’état de session passe de **en cours d’exécution** à **déconnecté** . Vous pouvez vous reconnecter à une session PSSession déconnectée à partir de la session active ou d’une autre session sur le même ordinateur ou à partir d’un autre ordinateur. L’ordinateur distant qui gère la session doit être en cours d’exécution et être connecté au réseau.

Les commandes d’une session PSSession déconnectée continuent à s’exécuter sans interruption sur l’ordinateur distant jusqu’à ce que la commande soit terminée ou que la mémoire tampon de sortie soit remplie. Pour empêcher une mémoire tampon de sortie complète d’interrompre une commande, utilisez le paramètre **OutputBufferingMode** des `Disconnect-PSSession` applets de commande, `New-PSSessionOption` ou `New-PSTransportOption` .

Les sessions déconnectées sont conservées dans l’état déconnecté sur l’ordinateur distant. Ils sont disponibles pour vous reconnecter, jusqu’à ce que vous supprimiez la session PSSession, par exemple à l’aide de l’applet de commande `Remove-PSSession` , ou jusqu’à ce que le délai d’inactivité de la session PSSession arrive à expiration. Vous pouvez ajuster le délai d’inactivité d’une session PSSession à l’aide des paramètres **IdleTimeoutSec** ou **IdleTimeout** des `Disconnect-PSSession` applets de commande, `New-PSSessionOption` ou `New-PSTransportOption` .

Un autre utilisateur peut se connecter à sessions PSSession que vous avez créé, mais uniquement s’il peut fournir les informations d’identification qui ont été utilisées pour créer la session, ou utiliser les `RunAs` informations d’identification de la configuration de session.

## <a name="how-to-get-pssessions"></a>Obtention de sessions PSSession

À compter de PowerShell 3,0, l' `Get-PSSession` applet de commande obtient sessions PSSession sur l’ordinateur local et les ordinateurs distants. Il peut également recevoir des sessions PSSession qui ont été créés dans la session active.

Pour accéder à sessions PSSession sur l’ordinateur local ou les ordinateurs distants, utilisez les paramètres **ComputerName** ou **ConnectionUri** . Sans paramètres, `Get-PSSession` obtient PSSession qui a été créé dans la session locale, quel que soit l’emplacement où elles se terminent.

Lorsque vous obtenez des sessions PSSession, n’oubliez pas de les Rechercher sur l’ordinateur sur lequel ils sont conservés, c’est-à-dire sur l’ordinateur distant ou **côté serveur** .

Par exemple, si vous créez une session PSSession sur l’ordinateur Serveur01, récupérez la session à partir de l’ordinateur SERVEUR01. Si vous créez une session PSSession à partir d’un autre ordinateur sur l’ordinateur local, récupérez la session à partir de l’ordinateur local.

La séquence de commandes suivante montre comment `Get-PSSession` fonctionne.

La première commande crée une session sur l’ordinateur SERVEUR01. La session se trouve sur l’ordinateur SERVEUR01.

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

Pour obtenir la session, utilisez le paramètre **ComputerName** de `Get-PSSession` avec la valeur SERVEUR01.

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

Si la valeur du paramètre **ComputerName** de `Get-PSSession` est localhost, `Get-PSSession` obtient les sessions PSSession qui se terminent à et sont conservés sur l’ordinateur local. Elle n’obtient pas de sessions PSSession sur l’ordinateur Serveur01, même si elles ont été démarrées sur l’ordinateur local.

```powershell
Get-PSSession -ComputerName localhost
```

Pour récupérer les sessions qui ont été créées dans la session active, utilisez l’applet de commande `Get-PSSession` sans paramètres. Dans cet exemple, `Get-PSSession` obtient la session PSSession créée dans la session active et se connecte à l’ordinateur SERVEUR01.

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a>Comment déconnecter des sessions

Pour déconnecter une session PSSession, utilisez l’applet de commande `Disconnect-PSSession` . Pour identifier la session PSSession, utilisez le paramètre de **session** ou le pipeline a PSSession des `New-PSSession` applets de commande ou `Get-PSSession` à `Disconnect-PSSession` .

La commande suivante déconnecte la session PSSession à l’ordinateur SERVEUR01.
Notez que la valeur de la propriété **State** est **Disconnected** et que la **disponibilité** est **None** .

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

Pour créer une session déconnectée, utilisez le paramètre **InDisconnectedSession** de l’applet de commande `Invoke-Command` . Il crée une session, démarre la commande et se déconnecte immédiatement, avant que la commande puisse retourner une sortie.

La commande suivante exécute une `Get-WinEvent` commande dans une session déconnectée sur l’ordinateur distant SERVER02.

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a>Comment se connecter à des sessions déconnectées

Vous pouvez vous connecter à n’importe quelle session PSSession déconnectée à partir de la session dans laquelle vous avez créé la session PSSession ou d’autres sessions sur l’ordinateur local ou sur d’autres ordinateurs.

Vous pouvez créer une session PSSession, exécuter des commandes dans la session PSSession, vous déconnecter de la session PSSession, fermer PowerShell et arrêter l’ordinateur. Quelques heures plus tard, vous pouvez ouvrir un autre ordinateur, obtenir la session PSSession, vous y connecter et obtenir les résultats des commandes exécutées dans la session PSSession pendant qu’elle était déconnectée. Vous pouvez ensuite exécuter d’autres commandes dans la session.

Pour connecter une session PSSession déconnectée, utilisez l’applet de commande `Connect-PSSession` . Utilisez les paramètres **ComputerName** ou **ConnectionUri** pour identifier la session PSSession ou le pipeline d’une session PSSession `Get-PSSession` `Connect-PSSession` .

La commande suivante obtient les sessions sur l’ordinateur Server02. La sortie comprend deux sessions déconnectées, qui sont toutes deux disponibles.

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

La commande suivante permet de se connecter à session2. La session PSSession est maintenant ouverte et disponible.

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a>Obtention des résultats

Pour obtenir les résultats des commandes exécutées dans une session PSSession déconnectée, utilisez l’applet de commande `Receive-PSSession` .

Vous pouvez utiliser `Receive-PSSession` plutôt que l’applet de commande `Connect-PSSession` . Si la session est déjà reconnectée, `Receive-PSSession` obtient les résultats des commandes exécutées lorsque la session a été déconnectée. Si la session PSSession est toujours déconnectée, `Receive-PSSession` se connecte à celle-ci, puis obtient les résultats des commandes qui ont été exécutées pendant qu’elle a été déconnectée.

`Receive-PSSession` peut retourner les résultats dans un travail (de façon asynchrone) ou au programme hôte (de façon synchrone). Utilisez le paramètre **distarget** pour sélectionner un **travail** ou un **hôte** . La valeur par défaut est **Host** . Toutefois, si la commande en cours de réception a été démarrée dans la session active en tant que **tâche** , elle est retournée par défaut en tant que **tâche** .

La commande suivante utilise l' `Receive-PSSession` applet de commande pour se connecter à la session PSSession sur l’ordinateur Server02 et obtenir les résultats de la `Get-WinEvent` commande exécutée dans la session session3. La commande utilise le paramètre **distarget** pour obtenir les résultats dans un **travail** .

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

Pour obtenir les résultats du travail, utilisez l' `Receive-Job` applet de commande.

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a>Propriétés d’État et de disponibilité

Les propriétés d' **État** et de **disponibilité** d’une session PSSession déconnectée vous indiquent si la session est disponible pour vous y reconnecter.

Quand une session PSSession est connectée à la session active, son état est **ouvert** et sa disponibilité est **disponible** . Lorsque vous vous déconnectez de la session PSSession, l’État PSSession est **déconnecté** et sa disponibilité est **None** .

La valeur de la propriété **State** dépend de la session active. La valeur **Disconnected** signifie que la session PSSession n’est pas connectée à la session active. Mais cela ne signifie pas que la session PSSession est déconnectée de toutes les sessions. Elle peut être connectée à une autre session.

Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session PSSession, utilisez la propriété **Availability** . La valeur **None** indique que vous pouvez vous connecter à la session. La valeur **Busy** indique que vous ne pouvez pas vous connecter à la session PSSession, car elle est connectée à une autre session.

L’exemple suivant est exécuté dans deux sessions PowerShell sur le même ordinateur.
Notez les valeurs modifiées des propriétés d' **État** et de **disponibilité** dans chaque session lorsque la session PSSession est déconnectée et reconnectée.

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

Les sessions déconnectées sont conservées sur l’ordinateur distant jusqu’à ce que vous les supprimiez, par exemple à l’aide de l’applet de commande `Remove-PSSession` ou qu’elles expirent. La propriété **IdleTimeout** d’une session PSSession détermine la durée pendant laquelle une session déconnectée est conservée avant d’être supprimée.

Les sessions PSSession sont inactifs lorsque le **thread de pulsation** ne reçoit pas de réponse.
La déconnexion d’une session rend celle-ci inactive et démarre l’horloge **IdleTimeout** , même si les commandes sont toujours en cours d’exécution dans la session déconnectée. PowerShell considère que les sessions déconnectées sont actives, mais inactives.

Lors de la création et de la déconnexion des sessions, vérifiez que le délai d’inactivité dans la session PSSession est suffisamment long pour maintenir la session en fonction de vos besoins, mais pas si longtemps qu’elle consomme des ressources inutiles sur l’ordinateur distant.

La propriété **IdleTimeoutMs** de la configuration de session détermine le délai d’inactivité par défaut des sessions qui utilisent la configuration de session. Vous pouvez remplacer la valeur par défaut, mais la valeur que vous utilisez ne peut pas dépasser la propriété **MaxIdleTimeoutMs** de la configuration de session.

Pour rechercher la valeur des valeurs **IdleTimeoutMs** et **MaxIdleTimeoutMs** d’une configuration de session, utilisez le format de commande suivant.

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

Vous pouvez remplacer la valeur par défaut dans la configuration de session et définir le délai d’inactivité d’une session PSSession lorsque vous créez une session PSSession et lorsque vous vous déconnectez.

Si vous êtes membre du groupe Administrateurs sur l’ordinateur distant, vous pouvez créer et modifier les propriétés **IdleTimeoutMs** et **MaxIdleTimeoutMs** des configurations de session.

## <a name="idle-timeout-values"></a>Valeurs du délai d’inactivité

La valeur du délai d’inactivité des configurations de session et des options de session est exprimée en millisecondes. La valeur du délai d’inactivité des sessions et des options de configuration de session est en secondes.

Vous pouvez définir le délai d’inactivité d’une session PSSession quand vous créez la session PSSession ( `New-PSSession` , `Invoke-Command` ) et lorsque vous vous déconnectez de celle-ci ( `Disconnect-PSSession` ). Toutefois, vous ne pouvez pas modifier la valeur **IdleTimeout** lorsque vous vous connectez à la session PSSession ( `Connect-PSSession` ) ou obtenir les résultats ( `Receive-PSSession` ).

Les `Connect-PSSession` applets de commande et `Receive-PSSession` ont un paramètre **SessionOption** qui prend un objet **SessionOption** , tel que celui retourné par l’applet de commande `New-PSSessionOption` . La valeur **IdleTimeout** de l’objet **SessionOption** et la valeur **IdleTimeout** de la `$PSSessionOption` variable preference ne modifient pas la valeur de l’option **IdleTimeout** de la session PSSession dans une `Connect-PSSession` commande ou `Receive-PSSession` .

Pour créer une session PSSession avec une valeur de délai d’inactivité particulière, créez une `$PSSessionOption` variable de préférence. Définissez la valeur de la propriété **IdleTimeout** sur la valeur souhaitée (en millisecondes).

Lorsque vous créez des sessions PSSession, les valeurs de `$PSSessionOption` variables sont prioritaires sur les valeurs de la configuration de session.

Par exemple, la commande suivante définit un délai d’inactivité de 48 heures :

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

Pour créer une session PSSession avec une valeur de délai d’inactivité particulière, utilisez le paramètre **IdleTimeoutMSec** de l’applet de commande `New-PSSessionOption` . Utilisez ensuite l’option de session dans la valeur du paramètre **SessionOption** des `New-PSSession` applets de commande ou `Invoke-Command` .

Les valeurs définies lors de la création de la session sont prioritaires par rapport aux valeurs définies dans la `$PSSessionOption` variable de préférence et la configuration de session.

Par exemple :

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

Pour modifier le délai d’inactivité d’une session PSSession lors de la déconnexion, utilisez le paramètre **IdleTimeoutSec** de l’applet de commande `Disconnect-PSSession` .

Par exemple :

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

Pour créer une configuration de session avec un délai d’inactivité particulier et un délai d’inactivité maximal, utilisez les paramètres **IdleTimeoutSec** et **MaxIdleTimeoutSec** de l’applet de commande `New-PSTransportOption` . Ensuite, utilisez l’option de transport dans la valeur du paramètre **TransportOption** de `Register-PSSessionConfiguration` .

Par exemple :

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

Pour modifier le délai d’inactivité par défaut et le délai d’inactivité maximal pour une configuration de session, utilisez les paramètres **IdleTimeoutSec** et **MaxIdleTimeoutSec** de l’applet de commande `New-PSTransportOption` . Ensuite, utilisez l’option de transport dans la valeur du paramètre **TransportOption** de `Set-PSSessionConfiguration` .

Par exemple :

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a>Mode de mise en mémoire tampon de sortie

Le mode de mise en mémoire tampon de sortie d’une session PSSession détermine comment la sortie de la commande est gérée lorsque la mémoire tampon de sortie de la session PSSession est pleine.

Dans une session déconnectée, le mode de mise en mémoire tampon de sortie détermine en réalité si la commande continue de s’exécuter pendant que la session est déconnectée.

Les valeurs valides sont les suivantes :

- **Bloquer** . Quand la mémoire tampon de sortie est pleine, l'exécution est suspendue jusqu'à ce que la mémoire tampon soit effacée. Valeur par défaut.
- **Supprimer** . Quand la mémoire tampon de sortie est pleine, l'exécution se poursuit. À mesure que de nouvelles sorties sont générées, la sortie la plus ancienne est ignorée.

**Block** conserve les données, mais peut interrompre la commande. La valeur **Drop** permet l'exécution de la commande, même si des données peuvent être perdues. Quand vous utilisez la valeur **Drop** , redirigez la sortie de la commande vers un fichier sur disque. Cette valeur est recommandée pour les sessions déconnectées.

La propriété **OutputBufferingMode** de la configuration de session détermine le mode de mise en mémoire tampon de sortie par défaut des sessions qui utilisent la configuration de session.

Pour trouver la valeur de la configuration de session **OutputBufferingMode** , vous pouvez utiliser l’un des formats de commande suivants :

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

Vous pouvez remplacer la valeur par défaut dans la configuration de session et définir le mode de mise en mémoire tampon de sortie d’une session PSSession quand vous créez une session PSSession, lorsque vous vous déconnectez, et lorsque vous vous reconnectez.

Si vous êtes membre du groupe Administrateurs sur l’ordinateur distant, vous pouvez créer et modifier le mode de mise en mémoire tampon de sortie des configurations de session.

Pour créer une session PSSession avec le mode de **suppression** de la mise en mémoire tampon de sortie, créez une `$PSSessionOption` variable de préférence dans laquelle la valeur de la propriété **OutputBufferingMode** est **Drop** .

Lorsque vous créez des sessions PSSession, les valeurs de `$PSSessionOption` variables sont prioritaires sur les valeurs de la configuration de session.

Par exemple :

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

Pour créer une session PSSession avec le mode de mise en mémoire tampon de sortie **Drop** , utilisez le paramètre **OutputBufferingMode** de l' `New-PSSessionOption` applet de commande pour créer une option de session avec la valeur **Drop** . Utilisez ensuite l’option de session dans la valeur du paramètre **SessionOption** des `New-PSSession` applets de commande ou `Invoke-Command` .

Les valeurs définies lors de la création de la session sont prioritaires par rapport aux valeurs définies dans la `$PSSessionOption` variable de préférence et la configuration de session.

Par exemple :

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

Pour modifier le mode de mise en mémoire tampon de sortie d’une session PSSession lors de la déconnexion, utilisez le paramètre **OutputBufferingMode** de l’applet de commande `Disconnect-PSSession` .

Par exemple :

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

Pour modifier le mode de mise en mémoire tampon de sortie d’une session PSSession lors de la reconnexion, utilisez le paramètre **OutputBufferingMode** de l' `New-PSSessionOption` applet de commande pour créer une option de session avec la valeur **Drop** . Ensuite, utilisez l’option de session dans la valeur du paramètre **SessionOption** de `Connect-PSSession` ou `Receive-PSSession` .

Par exemple :

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

Pour créer une configuration de session avec le mode de **suppression** de la mise en mémoire tampon de sortie par défaut, utilisez le paramètre **OutputBufferingMode** de l' `New-PSTransportOption` applet de commande pour créer un objet d’option de transport avec la valeur **Drop** . Ensuite, utilisez l’option de transport dans la valeur du paramètre **TransportOption** de `Register-PSSessionConfiguration` .

Par exemple :

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

Pour modifier le mode de mise en mémoire tampon de sortie par défaut d’une configuration de session, utilisez le paramètre **OutputBufferingMode** de l' `New-PSTransportOption` applet de commande pour créer une option de transport avec la valeur **Drop** . Ensuite, utilisez l’option de transport dans la valeur du paramètre **SessionOption** de `Set-PSSessionConfiguration` .

Par exemple :

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a>Déconnexion de sessions de bouclage

Les sessions de bouclage, ou sessions locales, sont des sessions PSSession qui proviennent et se terminent sur le même ordinateur. Comme les autres sessions PSSession, les sessions de bouclage actives sont conservées sur l’ordinateur à l’extrémité distante de la connexion (ordinateur local), ce qui vous permet de vous déconnecter et de vous reconnecter aux sessions de bouclage.

Par défaut, les sessions de bouclage sont créées avec un jeton de sécurité réseau qui n’autorise pas les commandes exécutées dans la session à accéder à d’autres ordinateurs. Vous pouvez vous reconnecter aux sessions de bouclage qui ont un jeton de sécurité réseau à partir de n’importe quelle session sur l’ordinateur local ou sur un ordinateur distant.

Toutefois, si vous utilisez le paramètre **EnableNetworkAccess** de l’applet de commande, `New-PSSession` `Enter-PSSession` ou `Invoke-Command` , la session de bouclage est créée avec un jeton de sécurité interactif. Le jeton interactif active les commandes qui s’exécutent dans la session de bouclage pour récupérer des données à partir d’autres ordinateurs.

Vous pouvez déconnecter des sessions de bouclage avec des jetons interactifs, puis vous y reconnecter à partir de la même session ou d’une autre session sur le même ordinateur.
Toutefois, pour empêcher les accès malveillants, vous pouvez vous reconnecter aux sessions de bouclage avec des jetons interactifs uniquement à partir de l’ordinateur sur lequel ils ont été créés.

## <a name="waiting-for-jobs-in-disconnected-sessions"></a>En attente de travaux dans les sessions déconnectées

L' `Wait-Job` applet de commande attend qu’une tâche se termine, puis retourne à l’invite de commandes ou à la commande suivante. Par défaut, `Wait-Job` retourne si la session dans laquelle un travail est en cours d’exécution est déconnectée. Pour demander `Wait-Job` à l’applet de commande d’attendre que la session soit reconnectée, à l’état **ouvert** , utilisez le paramètre **force** . Pour plus d’informations, consultez [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).

## <a name="robust-sessions-and-unintentional-disconnection"></a>Sessions fiables et déconnexion non intentionnelle

Une session PSSession peut être déconnectée de manière involontaire en raison d’une panne de l’ordinateur ou d’un réseau. PowerShell tente de récupérer la session PSSession, mais son succès dépend de la gravité et de la durée de la cause.

L’état d’une session PSSession déconnectée de manière involontaire peut être **interrompu** ou **fermé** , mais il peut également être **déconnecté** . Si la valeur de l' **État** est **Disconnected** , vous pouvez utiliser les mêmes techniques pour gérer la session PSSession que si la session était déconnectée intentionnellement. Par exemple, vous pouvez utiliser la `Connect-PSSession` cmdlet pour vous reconnecter à la session et l' `Receive-PSSession` applet de commande pour obtenir les résultats des commandes exécutées pendant la déconnexion de la session.

Si vous fermez (quittez) la session dans laquelle une session PSSession a été créée alors que les commandes s’exécutent dans la session PSSession, PowerShell maintient la session PSSession à l’état **déconnecté** sur l’ordinateur distant. Si vous fermez (quittez) la session dans laquelle une session PSSession a été créée, mais qu’aucune commande n’est en cours d’exécution dans la session PSSession, PowerShell ne tente pas de maintenir la session PSSession.

## <a name="see-also"></a>Voir aussi

[about_Jobs](about_Jobs.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Session_Configurations](about_Session_Configurations.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Disconnect-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Receive-PSSession](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
