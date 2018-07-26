---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Scripts PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094049"
---
# <a name="powershell"></a>PowerShell

Reposant sur le .NET Framework, PowerShell est un interpréteur de commandes en ligne de commande basé sur des tâches et un langage de script. Il est spécialement conçu pour les administrateurs système et les utilisateurs avancés afin d’automatiser rapidement l’administration de plusieurs systèmes d’exploitation (Linux, macOS, Unix et Windows) et les processus liés aux applications qui s’exécutent sur ces systèmes d’exploitation.

## <a name="powershell-is-open-source"></a>PowerShell est open source

Le code source de base de PowerShell est maintenant disponible dans GitHub et ouvert aux contributions de la communauté.
Consultez [Source PowerShell sur GitHub](https://github.com/powershell/powershell).

Vous pouvez commencer par les éléments nécessaires sur [Obtenir PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Vous pouvez aussi peut-être parcourir rapidement [Prise en main](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>Objectifs de conception de PowerShell
PowerShell est conçu pour améliorer l’environnement de script et de ligne de commande en éliminant des problèmes connus de longue date et en ajoutant de nouvelles fonctionnalités.

### <a name="discoverability"></a>Détectabilité
PowerShell facilite la découverte de ses fonctionnalités. Par exemple, pour obtenir la liste des applets de commande qui permettent d’afficher et de modifier les services Windows, tapez :

```powershell
Get-Command *-Service
```

Après avoir découvert l’applet de commande qui effectue une tâche, vous pouvez en apprendre davantage sur l’applet de commande à l’aide de l’applet de commande `Get-Help`.
Par exemple, pour afficher l’aide concernant l’applet de commande `Get-Service`, tapez ce qui suit :

```powershell
Get-Help Get-Service
```
La plupart des applets de commande émettent des objets qui peuvent être manipulés puis rendus sous forme texte pour l’affichage.
Pour bien comprendre la sortie de cette applet de commande, canalisez-la vers l’applet de commande `Get-Member`.
Par exemple, la commande suivante affiche des informations sur les membres de l’objet retourné par l’applet de commande `Get-Service`.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency
La gestion de systèmes pouvant être complexe, disposer d’outils dont l’interface est cohérente facilite le contrôle de la complexité intrinsèque.
Malheureusement, ni les outils en ligne de commande, ni les objets COM pouvant contenir des scripts ne sont réputés pour leur cohérence.

La cohérence de PowerShell est l’un de ses principaux atouts.
Par exemple, si vous apprenez à utiliser l’applet de commande `Sort-Object`, vous pouvez utiliser cette connaissance pour trier la sortie de toute applet de commande.
Vous n’avez pas à apprendre les différentes routines de tri de chaque applet de commande.

En outre, les développeurs d’applets de commande n’ont pas à concevoir de fonctionnalités de tri pour leur applets de commande.
PowerShell leur offre une infrastructure qui intègre les fonctionnalités de base et les force à être cohérents pour de nombreux aspects de l’interface.
L’infrastructure élimine certains choix généralement laissés à l’appréciation des développeurs mais, en retour, elle simplifie le développement d’applets de commande robustes et simples d’utilisation.

### <a name="interactive-and-scripting-environments"></a>Environnements interactifs et de scripts
PowerShell est un environnement combiné interactif et de script qui donne accès à des outils en ligne de commande et à des objets COM et permet d’exploiter la puissance de la bibliothèque de classes .NET Framework.

Cet environnement améliore l’invite de commandes Windows, pour offrir un environnement interactif avec plusieurs outils en ligne de commande.
Il améliore également les scripts Windows Script Host (WSH) qui permettent d’utiliser plusieurs outils en ligne de commande et objets Automation COM, mais ne fournissent pas d’environnement interactif.

En combinant l’accès à toutes ces fonctionnalités, PowerShell étend la capacité de l’utilisateur interactif et du writer de script, et facilite l’administration du système.

### <a name="object-orientation"></a>Orientation objet
Même si vous interagissez avec PowerShell en tapant des commandes sous forme de texte, PowerShell est basé sur des objets, pas sur du texte.
La sortie d’une commande est un objet.
Vous pouvez envoyer l’objet de sortie à une autre commande en tant qu’entrée.
Par conséquent, PowerShell fournit une interface familière aux personnes ayant l’expérience d’autres interpréteurs de commandes, tout en introduisant un paradigme de ligne de commande nouveau et puissant.
Il étend le concept d’échange de données entre commandes en vous permettant d’envoyer des objets, plutôt que du texte.

### <a name="easy-transition-to-scripting"></a>Transition aisée vers les scripts
PowerShell facilite la transition de la saisie de commandes de façon interactive vers la création et l’exécution de scripts.
Vous pouvez taper des commandes à l’invite de commandes PowerShell pour découvrir les commandes qui effectuent une tâche.
Ensuite, vous pouvez enregistrer ces commandes dans une transcription ou un historique avant de les copier dans un fichier afin de les utiliser en tant que script.
