---
title: Écrire un Module PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229348"
---
# <a name="writing-a-windows-powershell-module"></a>Écriture d’un module Windows PowerShell

Ce document est destiné aux administrateurs, développeurs de script et les développeurs d’applet de commande qui doivent empaqueter et distribuer leurs applets de commande Windows PowerShell. À l’aide de modules Windows PowerShell, vous pouvez empaqueter et distribuer vos solutions de Windows PowerShell sans utiliser un langage compilé.

Modules Windows PowerShell vous permettent de partition, organiser et d’abstraire votre code Windows PowerShell en unités autonomes réutilisables. Avec ces unités réutilisables, vous pouvez facilement partager vos modules directement avec d’autres utilisateurs. Si vous êtes un développeur de script, vous pouvez également réorganiser des modules tiers pour créer des applications personnalisées en fonction de script. Modules, similaires aux modules dans d’autres langages de script tels que Perl et Python, activer des solutions de script prêt pour la production qui utilisent des composants réutilisables et redistribuables, avec l’avantage supplémentaire de ce qui vous permet de réorganiser et d’abstraire plusieurs composants à créer des solutions personnalisées.

À leur plus simple, Windows PowerShell traite tout code de script Windows PowerShell valide enregistré dans un fichier .psm1 en tant que module. En tant que module traite également automatiquement n’importe quel assembly binaire applet de commande PowerShell. Toutefois, vous pouvez également utiliser un module (ou plus précisément, un manifeste de module) pour regrouper un ensemble de la solution. Les scénarios suivants décrivent les utilisations courantes pour les modules Windows PowerShell.

### <a name="libraries"></a>Bibliothèques

Modules peuvent être utilisés pour empaqueter et distribuer des bibliothèques cohérente de fonctions qui effectuent des tâches courantes. En règle générale, les noms de ces fonctions partagent un ou plusieurs noms qui reflètent la tâche courante qui elles sont utilisées. Ces fonctions peuvent également être semblables aux classes du .NET Framework dans la mesure où ils peuvent avoir des membres publics et privés. Par exemple, une bibliothèque peut contenir un ensemble de fonctions pour les transferts de fichiers. Dans ce cas, le substantif reflétant la tâche courante peut être « fichier ».

### <a name="configuration"></a>Configuration

Modules peuvent être utilisés pour personnaliser votre environnement en ajoutant les variables, les fournisseurs, les fonctions et les applets de commande spécifique.

### <a name="compiled-code-development-and-distribution"></a>Développement de Code compilé et la Distribution

Les développeurs d’applet de commande et le fournisseur peuvent utiliser des modules pour tester et distribuer leur code compilé sans avoir à créer des composants logiciel enfichables. Ils peuvent importer l’assembly qui contient le code compilé en tant que module (un module binaire) sans avoir à créer et inscrire les composants logiciel enfichables.

## <a name="see-also"></a>Voir aussi

[Comprendre un Module PowerShell de Windows](./understanding-a-windows-powershell-module.md)

[Comment écrire un Module de Script PowerShell](./how-to-write-a-powershell-script-module.md)

[Comment écrire un Module PowerShell binaire](./how-to-write-a-powershell-binary-module.md)

[Comment écrire un manifeste de Module PowerShell](how-to-write-a-powershell-module-manifest.md)

[Modifier le chemin d’Installation de PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importation d’un Module PowerShell](./importing-a-powershell-module.md)

[Installation d’un Module PowerShell](./installing-a-powershell-module.md)
