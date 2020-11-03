---
description: Décrit les sessions PowerShell (sessions PSSession) et explique comment établir une connexion permanente à un ordinateur distant.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: ae7f5d06773253328c58f770595dd041c5ff6367
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207005"
---
# <a name="about-pssessions"></a>À propos de sessions PSSession

## <a name="short-description"></a>Description courte
Décrit les sessions PowerShell (sessions PSSession) et explique comment établir une connexion permanente à un ordinateur distant.

## <a name="long-description"></a>Description longue

Pour exécuter des commandes PowerShell sur un ordinateur distant, vous pouvez utiliser le paramètre **ComputerName** d’une applet de commande, ou vous pouvez créer une session PowerShell (PSSession) et exécuter des commandes dans la session PSSession.

Lorsque vous créez une session PSSession, PowerShell établit une connexion permanente à l’ordinateur distant. Utilisez une session PSSession pour exécuter une série de commandes associées sur un ordinateur distant. Les commandes qui s’exécutent dans la même session PSSession peuvent partager des données, telles que les valeurs des variables, des alias et des fonctions.

Vous pouvez également créer une session PSSession sur l’ordinateur local et y exécuter des commandes.
Une session PSSession locale utilise l’infrastructure de communication à distance PowerShell pour créer et maintenir la session PSSession.

À compter de Windows PowerShell 3,0, les sessions PSSession sont indépendants des sessions dans lesquelles ils sont créés. Les sessions PSSession actifs sont conservés sur l’ordinateur distant (ou l’ordinateur situé à l’extrémité distante ou côté serveur de la connexion). Par conséquent, vous pouvez vous déconnecter de la session PSSession et vous y reconnecter ultérieurement à partir du même ordinateur ou d’un autre ordinateur.

Cette rubrique explique comment créer, utiliser, récupérer et supprimer des sessions PSSession. Pour plus d’informations, consultez [about_PSSession_Details](about_PSSession_Details.md).

Remarque : sessions PSSession utilise l’infrastructure de communication à distance PowerShell. Pour utiliser sessions PSSession, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.
Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).

Dans Windows Vista et les versions ultérieures de Windows, vous devez démarrer PowerShell avec l’option « Exécuter en tant qu’administrateur » pour créer une session PSSession sur un ordinateur local.

## <a name="what-is-a-session"></a>Qu’est-ce qu’une session ?

Une session est un environnement dans lequel PowerShell s’exécute.

Chaque fois que vous démarrez PowerShell, une session est créée pour vous et vous pouvez exécuter des commandes dans la session. Vous pouvez également ajouter des éléments à votre session, tels que des modules et des composants logiciels enfichables, et vous pouvez créer des éléments, tels que des variables, des fonctions et des alias. Ces éléments existent uniquement dans la session et sont supprimés à la fin de la session.

Vous pouvez également créer des sessions gérées par l’utilisateur, appelées « sessions PowerShell » ou « sessions PSSession », sur l’ordinateur local ou sur un ordinateur distant. Comme pour la session par défaut, vous pouvez exécuter des commandes dans une session PSSession et ajouter et créer des éléments. Toutefois, contrairement à la session qui démarre automatiquement, vous pouvez contrôler le sessions PSSession que vous créez. Vous pouvez les récupérer, les créer, les configurer et les supprimer, vous déconnecter et vous y reconnecter, et exécuter plusieurs commandes dans la même session PSSession. La session PSSession reste disponible jusqu’à ce que vous la supprimiez ou expire.

En général, vous créez une session PSSession pour exécuter une série de commandes associées sur un ordinateur distant. Lorsque vous créez une session PSSession sur un ordinateur distant, PowerShell établit une connexion permanente à l’ordinateur distant pour prendre en charge la session.

Si vous utilisez le paramètre **ComputerName** de l' `Invoke-Command` applet de `Enter-PSSession` commande ou pour exécuter une commande à distance ou démarrer une session interactive, PowerShell crée une session temporaire sur l’ordinateur distant et ferme la session dès que la commande est terminée ou dès la fin de la session interactive. Vous ne pouvez pas contrôler ces sessions temporaires et vous ne pouvez pas les utiliser pour plusieurs commandes ou une seule session interactive.

Dans PowerShell, la « session active » correspond à la session dans laquelle vous travaillez. La « session active » peut faire référence à n’importe quelle session, y compris une session temporaire ou une session PSSession.

## <a name="why-use-a-pssession"></a>Pourquoi utiliser une session PSSession ?

Utilisez une session PSSession lorsque vous avez besoin d’une connexion permanente à un ordinateur distant.
Avec PSSession, vous pouvez exécuter une série de commandes qui partagent des données, telles que la valeur des variables, le contenu d’une fonction ou la définition d’un alias.

Vous pouvez exécuter des commandes distantes sans créer de session PSSession. Utilisez le paramètre **ComputerName** des cmdlets distantes pour exécuter une seule commande ou une série de commandes non liées sur un ou plusieurs ordinateurs.

Quand vous utilisez le paramètre **ComputerName** de `Invoke-Command` ou `Enter-PSSession` , PowerShell établit une connexion temporaire à l’ordinateur distant, puis ferme la connexion dès que la commande est terminée. Tout élément de données que vous créez est perdu lorsque la connexion est fermée.

D’autres applets de commande ayant un paramètre **ComputerName** , telles que `Get-Eventlog` et `Get-WmiObject` , utilisent différentes technologies de communication à distance pour collecter des données. Aucun crée une connexion persistante comme une session PSSession.

## <a name="how-to-create-a-pssession"></a>Comment créer une session PSSession

Pour créer une session PSSession, utilisez l’applet de commande `New-PSSession` . Pour créer la session PSSession sur un ordinateur distant, utilisez le paramètre **ComputerName** de l’applet de commande `New-PSSession` .

Par exemple, la commande suivante crée une session PSSession sur l’ordinateur SERVEUR01.

```powershell
New-PSSession -ComputerName Server01
```

Lorsque vous envoyez la commande, `New-PSSession` crée la session PSSession et retourne un objet qui représente la session PSSession. Vous pouvez enregistrer l’objet dans une variable lorsque vous créez la session PSSession, ou vous pouvez utiliser une `Get-PSSession` commande pour obtenir la session PSSession ultérieurement.

Par exemple, la commande suivante crée une session PSSession sur l’ordinateur SERVEUR01 et enregistre l’objet résultant dans la variable $ps.

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a>Comment créer des sessions PSSession sur plusieurs ordinateurs

Pour créer des sessions PSSession sur plusieurs ordinateurs, utilisez le paramètre **ComputerName** de l’applet de commande `New-PSSession` . Tapez les noms des ordinateurs distants dans une liste séparée par des virgules.

Par exemple, pour créer des sessions PSSession sur les ordinateurs Serveur01, Server02 et Server03, tapez :

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

`New-PSSession` crée une session PSSession sur chacun des ordinateurs distants.

## <a name="how-to-get-pssessions"></a>Obtention de sessions PSSession

Pour récupérer les sessions PSSession qui ont été créés dans votre session active, utilisez l’applet de commande `Get-PSSession` sans le paramètre **ComputerName** . `Get-PSSession` retourne le même type d’objet que celui `New-PSSession` retourné par.

La commande suivante obtient toutes les sessions PSSession qui ont été créées dans la session active.

```powershell
Get-PSSession
```

L’affichage par défaut de l’sessions PSSession affiche son ID et un nom d’affichage par défaut. Vous pouvez attribuer un autre nom d’affichage lorsque vous créez la session.

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

Vous pouvez également enregistrer le sessions PSSession dans une variable. La commande suivante obtient le sessions PSSession et les enregistre dans la \$ variable ps123.

```powershell
$ps123 = Get-PSSession
```

Lorsque vous utilisez les applets de commande PSSession, vous pouvez faire référence à une session PSSession par son ID, son nom ou son ID d’instance (GUID). La commande suivante obtient une session PSSession par son ID et l’enregistre dans la \$ variable PS01.

```powershell
$ps01 = Get-PSSession -Id 1
```

À compter de Windows PowerShell 3,0, les sessions PSSession sont conservés sur l’ordinateur distant. Pour accéder à des sessions PSSession que vous avez créés sur des ordinateurs distants particuliers, utilisez le paramètre **ComputerName** de l’applet de commande `Get-PSSession` . La commande suivante obtient les sessions PSSession que vous avez créés sur l’ordinateur distant SERVEUR01. Cela comprend les sessions PSSession créés dans la session active et dans d’autres sessions sur l’ordinateur local ou d’autres ordinateurs.

```powershell
Get-PSSession -ComputerName Server01
```

Dans Windows PowerShell 2,0, `Get-PSSession` obtient uniquement les sessions PSSession qui ont été créés dans la session active. Il n’obtient pas les sessions PSSession qui ont été créés dans d’autres sessions ou sur d’autres ordinateurs, même si les sessions sont connectées à et exécutent des commandes sur l’ordinateur local.

## <a name="how-to-run-commands-in-a-pssession"></a>Comment exécuter des commandes dans une session PSSession

Pour exécuter une commande dans un ou plusieurs sessions PSSession, utilisez l' `Invoke-Command` applet de commande.
Utilisez le paramètre session pour spécifier sessions PSSession et le paramètre **scriptblock** pour spécifier la commande.

Par exemple, pour exécuter une `Get-ChildItem` commande (« dir ») dans chacun des trois sessions PSSession enregistrés dans la variable $ps 123, tapez :

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a>Comment supprimer des sessions PSSession

Lorsque vous avez terminé avec la session PSSession, utilisez l' `Remove-PSSession` applet de commande pour supprimer la session PSSession et libérer les ressources qu’elle utilisait.

```powershell
Remove-PSSession -Session $ps
```

ou

```powershell
Remove-PSSession -Id 1
```

Pour supprimer une session PSSession d’un ordinateur distant, utilisez le paramètre **ComputerName** de l’applet de commande `Remove-PSSession` .

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

Si vous ne supprimez pas la session PSSession, la session PSSession reste disponible pour être utilisée jusqu’à expiration.

Vous pouvez également utiliser le paramètre **IdleTimeout** de l' `New-PSSessionOption` applet de commande pour définir une heure d’expiration pour une session PSSession inactive. Pour plus d’informations, consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

## <a name="the-pssession-cmdlets"></a>Applets de commande PSSession

Pour obtenir la liste des applets de commande PSSession, tapez :

```powershell
Get-Help *-PSSession
```

- Connect-PSSession : connecte une session PSSession à la session active
- Disconnect-PSSession : déconnecte une session PSSession de la session active
- Enter-PSSession : démarre une session interactive
- Exit-PSSession : met fin à une session interactive
- Obtenir-PSSession : obtient le sessions PSSession dans la session active
- New-PSSession : crée une session PSSession sur un ordinateur local ou distant
- Receive-PSSession : obtient les résultats des commandes exécutées dans une session déconnectée
- Remove-PSSession : supprime le sessions PSSession dans la session active

## <a name="for-more-information"></a>Pour plus d'informations

Pour plus d’informations sur sessions PSSession, consultez [about_PSSession_Details](about_PSSession_Details.md).

## <a name="see-also"></a>Voir aussi

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Disconnect-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)
