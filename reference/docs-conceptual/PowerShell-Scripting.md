---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Scripts PowerShell
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451028"
---
# <a name="powershell"></a>PowerShell

PowerShell est un interpréteur de ligne de commande et langage de script qui repose sur la technologie.NET.
PowerShell permet aux administrateurs système et aux utilisateurs avancés d’automatiser rapidement les tâches qui administrent les systèmes d’exploitation (Linux, macOS et Windows) et les processus.

Les commandes PowerShell vous permettent de gérer les ordinateurs à partir de la ligne de commande. Les fournisseurs PowerShell vous permettent d’accéder à des magasins de données, par exemple le Registre et le magasin de certificats, aussi facilement que si vous accédiez au système de fichiers. PowerShell inclut un analyseur d’expression avancé et un langage de script entièrement développé.

## <a name="powershell-is-open-source"></a>PowerShell est open source

Le code source de base de PowerShell est maintenant disponible dans GitHub et ouvert aux contributions de la communauté.
Consultez [Source PowerShell sur GitHub](https://github.com/powershell/powershell).

Vous pouvez commencer par les éléments nécessaires sur [Obtenir PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Vous pouvez aussi peut-être parcourir rapidement [Prise en main](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>Objectifs de conception de PowerShell

PowerShell est conçu pour améliorer l’environnement de script et de ligne de commande en éliminant des problèmes connus de longue date et en ajoutant de nouvelles fonctionnalités.

### <a name="discoverability"></a>Détectabilité

PowerShell facilite la découverte de ses fonctionnalités. Par exemple, pour obtenir la liste des applets de commande qui permettent d’afficher et de modifier les services Windows, tapez :

```powershell
Get-Command *-Service
```

Après avoir découvert l’applet de commande qui effectue une tâche, vous pouvez en apprendre davantage sur l’applet de commande à l’aide de l’applet de commande `Get-Help`. Par exemple, pour afficher l’aide concernant l’applet de commande `Get-Service`, tapez ce qui suit :

```powershell
Get-Help Get-Service
```

La plupart des cmdlets retournent des objets qui peuvent être manipulés puis rendus sous forme texte pour l’affichage. Pour bien comprendre la sortie de cette cmdlet, canalisez la sortie vers la cmdlet `Get-Member`. Par exemple, la commande suivante affiche des informations sur les membres de l’objet retourné par l’applet de commande `Get-Service`.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency

L’administration de systèmes peut être une tâche complexe. Les outils dont l’interface est cohérente facilitent le contrôle de la complexité intrinsèque. Malheureusement, ni les outils en ligne de commande, ni les objets COM pouvant contenir des scripts ne sont réputés pour leur cohérence.

La cohérence de PowerShell est l’un de ses principaux atouts. Par exemple, si vous apprenez à utiliser l’applet de commande `Sort-Object`, vous pouvez utiliser cette connaissance pour trier la sortie de toute applet de commande. Vous n’avez pas à apprendre les différentes routines de tri de chaque cmdlet.

En outre, les développeurs de cmdlets n’ont pas à concevoir de fonctionnalités de tri pour leurs cmdlets. PowerShell fournit une infrastructure avec les fonctionnalités de base qui forcent la cohérence. L’infrastructure élimine certains choix qui sont laissés au développeur. Toutefois, en retour, le développement des cmdlets est beaucoup plus simple.

### <a name="interactive-and-scripting-environments"></a>Environnements interactifs et de scripts

L’invite de commandes Windows fournit un interpréteur de commandes interactif avec accès aux outils de ligne de commande et aux scripts de base. Windows Script Host (WSH) inclut des outils de ligne de commande contenant des scripts et des objets d’automatisation COM, mais ne fournit pas d’interpréteur de commandes interactif.

PowerShell combine un interpréteur de commandes interactif et un environnement de script. PowerShell peut accéder aux outils de ligne de commande, aux objets COM et aux bibliothèques de classes .NET. Cette combinaison de fonctionnalités étend les capacités de l’utilisateur interactif, du writer de script et de l’administrateur système.

### <a name="object-orientation"></a>Orientation objet

PowerShell est basé sur l’objet, pas le texte. La sortie d’une commande est un objet. Vous pouvez envoyer l’objet de sortie, via le pipeline, à une autre commande en tant qu’entrée.

Ce pipeline fournit une interface familière aux utilisateurs familiarisés avec d’autres interpréteurs de commandes. PowerShell étend ce concept en envoyant des objets plutôt que du texte.

### <a name="easy-transition-to-scripting"></a>Transition aisée vers les scripts

La détectabilité de commande de PowerShell facilite la transition de la saisie de commandes de façon interactive vers la création et l’exécution de scripts. L’historique et les transcriptions de PowerShell facilitent la copie de commandes dans un fichier pour une utilisation en tant que script.
