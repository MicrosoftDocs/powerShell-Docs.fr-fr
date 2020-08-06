---
title: Écriture d’un module Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d2398a8111a9832af2465d045be0bdefc3cf927a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779146"
---
# <a name="writing-a-windows-powershell-module"></a>Écriture d’un module Windows PowerShell

Ce document est destiné aux administrateurs, aux développeurs de scripts et aux développeurs d’applets de commande qui doivent empaqueter et distribuer leurs applets de commande Windows PowerShell. À l’aide des modules Windows PowerShell, vous pouvez empaqueter et distribuer vos solutions Windows PowerShell sans utiliser de langage compilé.

Les modules Windows PowerShell vous permettent de partitionner, d’organiser et d’abstraire votre code Windows PowerShell en unités autonomes réutilisables. Ces unités réutilisables vous permettent de partager facilement vos modules directement avec d’autres. Si vous êtes développeur de script, vous pouvez également reconditionner des modules tiers pour créer des applications basées sur des scripts personnalisés. Les modules, similaires aux modules dans d’autres langages de script tels que Perl et Python, permettent des solutions de script prêtes pour la production qui utilisent des composants redistribuables réutilisables, avec l’avantage supplémentaire de vous permettre de reconditionner et d’abstraire plusieurs composants pour créer des solutions personnalisées.

Au niveau le plus basique, Windows PowerShell traite tout code de script Windows PowerShell valide enregistré dans un fichier. psm1 en tant que module. PowerShell traitera également automatiquement tout assembly d’applet de commande binaire comme un module. Toutefois, vous pouvez également utiliser un module (ou plus spécifiquement, un manifeste de module) pour regrouper une solution entière. Les scénarios suivants décrivent les utilisations typiques des modules Windows PowerShell.

### <a name="libraries"></a>Bibliothèques

Les modules peuvent être utilisés pour empaqueter et distribuer des bibliothèques cohérentes de fonctions qui effectuent des tâches courantes. En règle générale, les noms de ces fonctions partagent un ou plusieurs noms qui reflètent la tâche courante pour laquelle ils sont utilisés. Ces fonctions peuvent également être similaires aux classes .NET Framework dans la mesure où elles peuvent avoir des membres publics et privés. Par exemple, une bibliothèque peut contenir un ensemble de fonctions pour les transferts de fichiers. Dans ce cas, le substantif qui reflète la tâche courante peut être « file ».

### <a name="configuration"></a>Configuration

Les modules peuvent être utilisés pour personnaliser votre environnement en ajoutant des applets de commande, des fournisseurs, des fonctions et des variables spécifiques.

### <a name="compiled-code-development-and-distribution"></a>Développement et distribution de code compilé

Les développeurs d’applets de commande et fournisseurs peuvent utiliser des modules pour tester et distribuer leur code compilé sans avoir besoin de créer des composants logiciels enfichables. Ils peuvent importer l’assembly qui contient le code compilé en tant que module (un module binaire) sans avoir à créer et inscrire des composants logiciels enfichables.

## <a name="see-also"></a>Voir aussi

[Présentation d’un module Windows PowerShell](./understanding-a-windows-powershell-module.md)

[Guide pratique pour écrire un module de script PowerShell](./how-to-write-a-powershell-script-module.md)

[Guide pratique pour écrire un module binaire PowerShell](./how-to-write-a-powershell-binary-module.md)

[Guide pratique pour écrire un manifeste de module PowerShell](how-to-write-a-powershell-module-manifest.md)

[Modification du chemin d’Installation de PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importation d’un module PowerShell](./importing-a-powershell-module.md)

[Installation d’un module PowerShell](./installing-a-powershell-module.md)
