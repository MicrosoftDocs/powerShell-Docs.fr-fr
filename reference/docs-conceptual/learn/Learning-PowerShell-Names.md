---
ms.date: 08/24/2018
keywords: powershell,applet de commande
title: Apprentissage des noms de commande PowerShell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 8d50ca03f98ed4ca8f9c09c83ae57afbf0d7888d
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623719"
---
# <a name="learning-powershell-command-names"></a>Apprentissage des noms de commande PowerShell

L’apprentissage des noms de commandes et des paramètres prend beaucoup de temps avec la plupart des interfaces de ligne de commande. Le problème est qu’il y a peu de modèles. La mémorisation est le seul moyen d’assimiler les commandes et paramètres utilisés régulièrement.

Face à une nouvelle commande ou à un nouveau paramètre, on ne peut pas toujours utiliser ce qu’on connaît déjà. Il faut trouver son nom et le retenir. En règle générale, les interfaces de ligne de commande commencent par un petit éventail d’outils et évoluent par ajouts successifs. On comprend facilement pourquoi il n’existe aucune structure standard.
En effet, chaque commande constitue un outil distinct. PowerShell présente une meilleure façon de gérer les noms de commandes.

## <a name="learning-command-names-in-traditional-shells"></a>Apprendre les noms de commandes dans des interpréteurs de commandes traditionnels

La plupart des commandes sont conçues pour gérer des éléments du système d’exploitation ou des applications, telles que des services ou processus. Les commandes portent divers noms qui peuvent ou non appartenir à une famille. Par exemple, sur les systèmes Windows, les commandes `net start` et `net stop` permettent de démarrer et d’arrêter un service. **sc.exe** est un autre outil de contrôle des services pour Windows. Ce nom ne correspond pas au modèle de noms des commandes de service **net.exe**. En ce qui concerne la gestion des processus, Windows offre la commande **tasklist.exe** pour les lister et la commande **taskkill.exe** pour les tuer.

Par ailleurs, ces commandes ont des spécifications de paramètres irrégulières. On ne peut pas utiliser la commande `net start` pour démarrer un service sur un ordinateur distant. C’est la commande **sc.exe** qui permet de le faire. Mais, pour spécifier l’ordinateur distant, il faut faire précéder son nom de deux barres obliques inverses. Pour démarrer le service spouleur sur un ordinateur distant nommé DC01, vous taperez `sc.exe \\DC01 start spooler`.
Pour lister les tâches en cours d’exécution sur DC01, vous utiliserez le paramètre **/S** et le nom de l’ordinateur sans les barres obliques inverses. Par exemple, `tasklist /S DC01`.

> [!NOTE]
> Avant PowerShell v6, `sc` était un alias de la cmdlet `Set-Content`. Par conséquent, pour exécuter la commande **sc.exe** dans une version de PowerShell antérieure à v6, vous devez inclure le nom de fichier complet **sc.exe** , y compris l’extension de fichier **exe**.

Les services et les processus sont des exemples d’éléments administrables d’un ordinateur qui ont des cycles de vie bien définis. On peut les démarrer, les arrêter ou obtenir la liste de tous ceux qui sont en cours d’exécution. Malgré les différences techniques importantes qui les séparent, les actions effectuées sur les services et sur les processus sont conceptuellement identiques. En outre, les choix de personnalisation d’une action par des paramètres peuvent également être similaires sur le plan conceptuel.

PowerShell exploite ces ressemblances afin de réduire le nombre de noms distincts à connaître pour comprendre et utiliser les cmdlets.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Les cmdlets utilisent des noms de type verbe-substantif pour alléger la mémorisation des commandes

PowerShell utilise un système de noms de type « verbe-substantif ». Chaque nom de cmdlet se compose d’un verbe standard suivi d’un trait d’union et d’un substantif spécifique. Les verbes qu’utilise PowerShell ne sont pas toujours des verbes anglais, mais ils désignent des actions particulières dans PowerShell. Les substantifs ressemblent aux noms communs que l’on trouve dans n’importe quelle langue. Ils décrivent des types d’objets importants dans l’administration du système. Il est facile de démontrer, en prenant quelques exemples, comment ces noms en deux parties contribuent à réduire l’effort d’apprentissage.

PowerShell comporte un jeu de verbes standard recommandé. Les noms, moins restreints, doivent toujours décrire ce sur quoi porte un verbe. PowerShell offre des commandes comme `Get-Process`, `Stop-Process`, `Get-Service` et `Stop-Service`.

Dans cet exemple composé de deux noms et deux verbes, la cohérence ne simplifie pas tellement l’apprentissage. Étendons cette liste à un ensemble standardisé de 10 verbes et 10 noms. Il n’y a que 20 mots à comprendre,
mais ils peuvent être combinés pour former 100 noms de commandes distincts.

On comprend facilement ce que fait une commande PowerShell en lisant son nom. La commande permettant d’arrêter un ordinateur est `Stop-Computer`. Celle qui liste tous les ordinateurs sur un réseau est `Get-Computer`. Pour obtenir la date du système, la commande est `Get-Date`.

Vous pouvez lister toutes les commandes comportant un verbe donné en ajoutant le paramètre **Verb** à `Get-Command`. Par exemple, pour afficher toutes les cmdlets qui utilisent le verbe `Get`, tapez :

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Utilisez le paramètre **Noun** pour voir une famille de commandes qui affectent le même type d’objet. Par exemple, exécutez la commande suivante afin de voir les commandes disponibles pour la gestion des services :

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Les cmdlets utilisent des paramètres standard

Comme nous l’avons mentionné, les commandes utilisées dans les interfaces de ligne de commande traditionnelles n’ont pas toujours des noms de paramètres cohérents. Il s’agit souvent d’un caractère unique ou de mots abrégés, faciles à taper mais difficilement compréhensibles pour des néophytes.

Contrairement à la plupart des interfaces de ligne de commande classiques, PowerShell traite directement les paramètres et utilise cet accès direct aux paramètres ainsi qu’une aide aux développeurs pour normaliser les noms de paramètres. Ces instructions encouragent à respecter le standard pour les différentes cmdlets, sans pour autant le garantir.

PowerShell normalise également le séparateur de paramètre. Les noms de paramètres sont toujours précédés d’un « - » avec une commande PowerShell. Prenons l’exemple suivant :

```powershell
Get-Command -Name Clear-Host
```

Le nom du paramètre est **Name**, mais il est noté `-Name` lorsqu’il est utilisé comme paramètre dans la ligne de commande.

Voici quelques-unes des caractéristiques générales des noms et utilisations des paramètres standard.

### <a name="the-help-parameter-"></a>Le paramètre Help (?)

Lorsque vous spécifiez le paramètre `-?` dans une applet de commande, PowerShell affiche l’aide de cette applet.
La cmdlet n’est pas exécutée.

### <a name="common-parameters"></a>Paramètres communs

PowerShell comporte plusieurs *paramètres communs*. Ils sont contrôlés par le moteur PowerShell. Ils se comportent toujours de la même façon. Les paramètres communs sont **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** et **OutBuffer**.

### <a name="recommended-parameter-names"></a>Noms de paramètres recommandés

Les principales cmdlet PowerShell utilisent des noms standard pour des paramètres similaires. Bien que leur utilisation ne soit pas imposée, des instructions explicites encouragent la normalisation.

Par exemple, le nom recommandé pour un paramètre faisant référence à un ordinateur est **ComputerName**, plutôt que Server, Host, System, Node ou tout autre nom courant. Voici d’autres noms de paramètres recommandés parmi les plus importants : **Force**, **Exclude**, **Include**, **PassThru**, **Path** et **CaseSensitive**.
