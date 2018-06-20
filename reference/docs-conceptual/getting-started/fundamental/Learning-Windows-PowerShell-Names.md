---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Apprentissage des noms dans Windows PowerShell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 381aa619a41ccacb2ff3a4cdbc2b75b7f04282d1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953471"
---
# <a name="learning-windows-powershell-names"></a>Apprentissage des noms dans Windows PowerShell
L’apprentissage des noms et des paramètres des commandes nécessite beaucoup de temps avec la plupart des interfaces de ligne de commande. Le problème est qu’il existe très peu de modèles, de sorte que la seule façon d’apprendre consiste à mémoriser chaque commande et chaque paramètre que vous devez utiliser régulièrement.

Lorsque vous utilisez une nouvelle commande ou un nouveau paramètre, vous ne pouvez généralement pas utiliser les connaissances acquises, car vous devez apprendre un nouveau nom. Si l’on considère la manière les interfaces croissent à partir d’un petit ensemble d’outils au gré des ajouts incrémentiels de fonctionnalités, on comprend aisément pourquoi la structure n’est pas standard. Avec les noms de commande, en particulier, cela peut sembler logique, car chaque commande est un outil distinct, mais il existe un meilleur moyen de gérer les noms de commande.

La plupart des commandes sont conçues pour gérer des éléments du système d’exploitation ou des applications, telles que des services ou processus. Les commandes portent divers noms qui peuvent ou non s’intégrer dans une famille. Par exemple, sur des systèmes Windows, vous pouvez utiliser les commandes **net start** et **net stop** pour démarrer et arrêter un service. Il existe un autre outil de contrôle de service plus généralisé pour Windows, qui porte un nom complètement différent, **sc**, non conforme au modèle d’affectation de noms pour les commandes de service **net**. Pour la gestion des processus, Windows offre la commande **tasklist** pour les répertorier, et la commande **taskkill** pour les supprimer.

Les commandes qui prennent des paramètres ont des spécifications de paramètre irrégulières. Vous ne pouvez pas utiliser la commande **net start** pour démarrer un service sur un ordinateur distant. La commande **sc** démarre un service sur un ordinateur distant mais, pour spécifier celui-ci, vous devez faire précéder son nom d’une double barre oblique inverse. Par exemple, pour démarrer le service du spouleur sur un ordinateur distant nommé DC01, tapez **sc \\\\DC01 start spooler**. Pour afficher la liste des tâches en cours d’exécution sur DC01, vous devez utiliser le paramètre **/S** (pour « système ») et fournir le nom DC01 sans barre oblique inverse, comme suit : **tasklist S DC01**.

Bien qu’il existe des différences techniques importantes entre un service et un processus, il s’agit de deux exemples d’éléments faciles à gérer sur un ordinateur, dont le cycle de vie est bien défini. Il se peut que vous souhaitiez démarrer ou arrêter un service ou un processus, ou obtenir la liste de tous les services ou processus en cours d’exécution. En d’autres termes, bien qu’un service et un processus relèvent de concepts différents, les actions que nous effectuons sur un service ou un processus sont souvent conceptuellement identiques. En outre, les choix que nous pouvons opérer pour personnaliser une action en spécifiant des paramètres peuvent également être similaires sur le plan conceptuel.

Windows PowerShell exploite ces similitudes pour réduire le nombre de noms distincts que vous devez connaître pour comprendre et utiliser les applets de commande.

### <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Utilisation de noms de type verbe-substantif pour les applets de commande afin de réduire la mémorisation des commandes
Windows PowerShell utilise un système d’affectation de noms de type « verbe-substantif », où le nom de chaque applet de commande se compose d’un verbe standard associé à un nom spécifique à l’aide d’un trait d’union. Les verbes qu’utilise Windows PowerShell ne sont pas toujours des verbes anglais, mais ils désignent des actions spécifiques dans Windows PowerShell. Les noms sont très semblables à des noms communs dans n’importe quelle langue. Ils décrivent certains types d’objets qui sont importants dans l’administration du système. Il est facile de démontrer comment ces noms en deux parties contribuent à réduire l’effort d’apprentissage en examinant quelques exemples de verbes et de noms.

Les noms sont moins restreints, mais ils doivent toujours décrire l’objet de l’action d’une commande. Windows PowerShell dispose de commandes telles que **Get-Process**, **Stop-Process**, **Get-Service** et **Stop-Service**.

En cas d’utilisation de deux noms et deux verbes, la cohérence ne simplifie pas tellement l’apprentissage. En revanche, si l’on considère un jeu standard de 10 verbes et 10 noms, il n’y a que 20 mots à comprendre, mais ils permettent de former 100 noms de commande distincts.

Souvent, vous pouvez comprendre l’action d’une commande en lisant son nom, et le nom à utiliser pour une nouvelle commande est généralement évident. Par exemple, une commande d’arrêt d’ordinateur peut être **Stop-Computer**. Une commande permettant de répertorier tous les ordinateurs d’un réseau peut être **Get-Computer**. La commande permettant d’obtenir la date système est **Get-Date**.

Vous pouvez répertorier toutes les commandes incluant un verbe particulier avec le paramètre **-Verb** pour l’applet de commande **Get-Command** (l’applet de commande **Get-Command** est décrite en détail dans la section suivante). Par exemple, pour afficher toutes les applets de commande qui utilisent le verbe **Get**, tapez :

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

Le paramètre **-Noun** est encore plus utile, car il permet de voir une famille de commandes qui affectent le même type d’objet. Par exemple, si vous souhaitez afficher les commandes disponibles pour la gestion des services, tapez la commande suivante :

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

Le simple fait que le schéma d’affectation de noms des commandes soit de type verbe-substantif ne signifie pas qu’une commande soit pas nécessairement une applet de commande. Un exemple de commande Windows PowerShell native qui n’est pas une applet de commande, mais a un nom de type verbe-substantif, est la commande d’effacement d’une fenêtre de console, Clear-Host. La commande Clear-Host est en fait une fonction interne, comme vous pouvez voir si vous exécutez dessus l’applet de commande Get-Command :

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### <a name="cmdlets-use-standard-parameters"></a>Utilisation de paramètres standard par les applets de commande
Comme mentionné précédemment, les commandes utilisées dans les interfaces de ligne de commande traditionnelles n’ont généralement pas de noms de paramètre cohérents. Parfois, les paramètres n’ont pas de nom du tout. Quand ils en ont un, il s’agit souvent d’un caractère unique ou de mots abrégés pouvant être tapés rapidement, mais qui ne sont pas facilement compréhensibles pour des néophytes.

Contrairement à la plupart des autres interfaces de ligne de commande traditionnelles, Windows PowerShell traite les paramètres directement et utilise cet accès direct aux paramètres en même temps que des instructions à l’adresse des développeurs afin de normaliser les noms de paramètre. Si cette solution ne garantit pas que chaque applet de commande soit toujours conforme aux normes, elle y contribue.

> [!NOTE]
> Lorsque vous utilisez des noms des paramètres, ceux-ci sont toujours précédés du signe « - » afin de permettre à Windows PowerShell de les identifier clairement en tant que paramètres. Dans l’exemple **Get-Command -Name Clear-Host**, le nom du paramètre est **Name**, mais il est entré sous la forme -**Name**.

Voici quelques-unes des caractéristiques générales des noms et utilisations des paramètres standard.

#### <a name="the-help-parameter-"></a>Paramètre Help (?)
Si vous spécifiez le paramètre **-?** pour une applet de commande, celle-ci n’est pas exécutée. Au lieu de cela, Windows PowerShell affiche l’aide sur l’applet de commande.

#### <a name="common-parameters"></a>Paramètres communs
Windows PowerShell dispose de plusieurs paramètres appelés *paramètres communs*. Étant donné que ces paramètres sont contrôlés par le moteur Windows PowerShell, chaque fois qu’une applet de commande les implémente, ils se comportent de la même façon. Les paramètres communs sont **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** et **OutBuffer**.

#### <a name="suggested-parameters"></a>Paramètres suggérés
Les principales applets de commande Windows PowerShell utilisent des noms standard pour des paramètres similaires. Bien que le mode d’utilisation des noms de paramètre ne soit pas imposé, il existe des instructions d’utilisation explicites visant à encourager la normalisation.

Par exemple, les instructions recommandent d’attribuer à un paramètre faisant référence à un ordinateur un nom de type **ComputerName**, plutôt que Serveur, Hôte, Système, Nœud ou un autre nom commun. Parmi les noms de paramètres importants suggérés figurent **Force**, **Exclude**, **Include**, **PassThru**, **Path** et **CaseSensitive**.