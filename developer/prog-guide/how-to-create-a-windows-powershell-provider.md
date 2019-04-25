---
title: Comment créer un fournisseur de PowerShell Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081748"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Guide pratique pour créer un fournisseur Windows PowerShell

Cette section décrit comment créer un fournisseur Windows PowerShell. Un fournisseur Windows PowerShell peut être considéré comme de deux manières. À l’utilisateur, le fournisseur représente un jeu de données stockées. Par exemple, les données stockées peuvent être la métabase Internet Information Services (IIS), le Registre Windows de Microsoft, le système de fichiers Windows, Active Directory et les données de variable et alias stockées par Windows PowerShell.

Pour le développeur, le fournisseur Windows PowerShell est l’interface entre l’utilisateur et les données auxquelles l’utilisateur doit accéder. À partir de cette perspective, chaque type de fournisseur décrite dans cette section prend en charge un ensemble de classes de base spécifiques et des interfaces qui permettent l’exécution de Windows PowerShell pour exposer certaines applets de commande à l’utilisateur de manière commune.

## <a name="providers-provided-by-windows-powershell"></a>Fournisseurs fournis par Windows PowerShell

Windows PowerShell propose plusieurs fournisseurs (par exemple, le fournisseur FileSystem, le fournisseur de Registre et le fournisseur d’Alias) qui sont utilisés pour accéder à des magasins de données connues. Pour plus d’informations sur les fournisseurs fournis par Windows PowerShell, utilisez la commande suivante pour accéder à l’aide en ligne :

**PS > get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>L’accès aux données stockées à l’aide de chemins d’accès de Windows PowerShell

Les fournisseurs Windows PowerShell sont accessibles à l’exécution de Windows PowerShell et aux commandes par programmation via l’utilisation de chemins d’accès Windows PowerShell. La plupart du temps, ces chemins d’accès sont utilisés pour accéder directement aux données via le fournisseur. Toutefois, certains chemins d’accès peuvent être résolues en interne au fournisseur de chemins d’accès qui permettent une applet de commande à utiliser les interfaces de programmation d’applications (API) non - Windows PowerShell pour accéder aux données. Pour plus d’informations sur le fonctionnement des fournisseurs Windows PowerShell dans Windows PowerShell, consultez [Windows PowerShell fonctionnement](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Exposer les applets de commande fournisseur à l’aide de Windows PowerShell de lecteurs

Un fournisseur Windows PowerShell expose ses applets de commande pris en charge à l’aide de disques virtuels de Windows PowerShell. Windows PowerShell applique les règles suivantes pour un lecteur Windows PowerShell :

- Le nom d’un lecteur peut être n’importe quelle séquence d’alphanumériques.

- Un lecteur peut être spécifié en tout point valide sur un chemin d’accès, appelé un « root ».

- Un lecteur peut être implémenté pour toutes les données stockées, pas seulement le système de fichiers.

- Chaque lecteur conserve son propre emplacement de travail actif, permettant à l’utilisateur conserver le contexte lors du déplacement entre des lecteurs.

## <a name="in-this-section"></a>Dans cette section

Le tableau suivant répertorie les rubriques qui contiennent des exemples de code qui s’appuient sur eux. À compter de la deuxième rubrique, le fournisseur de base de Windows PowerShell peut être initialisé et non initialisé par le runtime de Windows PowerShell, la rubrique suivante ajoute des fonctionnalités pour accéder aux données, la rubrique suivante ajoute des fonctionnalités permettant de manipuler le (des données les éléments dans les données stockées), et ainsi de suite.

|Rubrique|Définition|
|-----------|----------------|
|[Conception de votre fournisseur de PowerShell Windows](./designing-your-windows-powershell-provider.md)|Cette rubrique traite des choses que vous devez prendre en compte avant d’implémenter un fournisseur Windows PowerShell. Il récapitule les classes de base de fournisseur Windows PowerShell et les interfaces qui sont utilisées.|
|[Création d’un fournisseur PowerShell de base Windows](./creating-a-basic-windows-powershell-provider.md)|Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet au runtime de Windows PowerShell initialiser et annuler l’initialisation du fournisseur.|
|[Création d’un fournisseur de lecteur PowerShell Windows](./creating-a-windows-powershell-drive-provider.md)|Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur pour accéder à un magasin de données via un lecteur Windows PowerShell.|
|[Création d’un fournisseur d’éléments de PowerShell Windows](./creating-a-windows-powershell-item-provider.md)|Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de manipuler les éléments dans un magasin de données.|
|[Création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md)|Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de travailler sur des magasins de données multicouche.|
|[Création d’un fournisseur de Navigation de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)|Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur à parcourir les éléments d’un magasin de données de façon hiérarchique.|
|[Création d’un fournisseur de contenu PowerShell Windows](./creating-a-windows-powershell-content-provider.md)|Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de manipuler le contenu d’éléments dans un magasin de données.|
|[Création d’un fournisseur de propriété PowerShell Windows](./creating-a-windows-powershell-property-provider.md)|Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de manipuler les propriétés des éléments dans un magasin de données.|

## <a name="see-also"></a>Voir aussi

[Fonctionnement de Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)
