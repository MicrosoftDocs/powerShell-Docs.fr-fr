---
title: Comment créer un fournisseur Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.openlocfilehash: 5e7424c035d22d0f5eb154b369427a6da80b1c49
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787102"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Guide pratique pour créer un fournisseur Windows PowerShell

Cette section décrit comment créer un fournisseur Windows PowerShell. Un fournisseur Windows PowerShell peut être considéré de deux manières. Pour l’utilisateur, le fournisseur représente un ensemble de données stockées. Par exemple, les données stockées peuvent être la métabase Internet Information Services (IIS), le Registre Microsoft Windows, le système de fichiers Windows, Active Directory et la variable et les données d’alias stockées par Windows PowerShell.

Pour le développeur, le fournisseur Windows PowerShell est l’interface entre l’utilisateur et les données auxquelles l’utilisateur doit accéder. À partir de cette perspective, chaque type de fournisseur décrit dans cette section prend en charge un ensemble de classes de base et d’interfaces spécifiques qui permettent au runtime Windows PowerShell d’exposer certaines applets de commande à l’utilisateur de manière courante.

## <a name="providers-provided-by-windows-powershell"></a>Fournisseurs fournis par Windows PowerShell

Windows PowerShell fournit plusieurs fournisseurs (tels que le fournisseur de système de fichiers, le fournisseur de Registre et le fournisseur d’alias) qui sont utilisés pour accéder aux magasins de données connus. Pour plus d’informations sur les fournisseurs fournis par Windows PowerShell, utilisez la commande suivante pour accéder à l’aide en ligne :

**Bloc de>PS-Help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Accès aux données stockées à l’aide des chemins d’accès Windows PowerShell

Les fournisseurs Windows PowerShell sont accessibles par le biais du runtime Windows PowerShell et des commandes par programme via l’utilisation de chemins d’accès Windows PowerShell. La plupart du temps, ces chemins d’accès sont utilisés pour accéder directement aux données via le fournisseur. Toutefois, certains chemins d’accès peuvent être résolus en chemins d’accès internes du fournisseur qui permettent à une applet de commande d’utiliser des interfaces de programmation d’applications (API) non-Windows PowerShell pour accéder aux données. Pour plus d’informations sur le fonctionnement des fournisseurs Windows PowerShell dans Windows PowerShell, consultez fonctionnement de [Windows PowerShell](/previous-versions/ms714658(v=vs.85)).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Exposition des applets de commande de fournisseur à l’aide de lecteurs Windows PowerShell

Un fournisseur Windows PowerShell expose ses applets de commande prises en charge à l’aide de lecteurs Windows PowerShell virtuels.
Windows PowerShell applique les règles suivantes pour un lecteur Windows PowerShell :

- Le nom d’un lecteur peut être une séquence alphanumérique.
- Un lecteur peut être spécifié à n’importe quel point valide sur un chemin d’accès, appelé « racine ».
- Un lecteur peut être implémenté pour toutes les données stockées, et pas seulement pour le système de fichiers.
- Chaque lecteur conserve son propre emplacement de travail actuel, ce qui permet à l’utilisateur de conserver le contexte lors du déplacement entre les lecteurs.

## <a name="in-this-section"></a>Dans cette section

Le tableau suivant répertorie les rubriques qui contiennent des exemples de code qui s’appuient les uns sur les autres. À partir de la deuxième rubrique, le fournisseur Windows PowerShell de base peut être initialisé et non initialisé par le runtime Windows PowerShell, la rubrique suivante ajoute des fonctionnalités pour accéder aux données, la rubrique suivante ajoute des fonctionnalités pour manipuler les données (les éléments dans les données stockées), et ainsi de suite.

|                                                    Rubrique                                                    |                                                                                         Définition                                                                                          |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)               | Cette rubrique décrit les éléments à prendre en compte avant d’implémenter un fournisseur Windows PowerShell. Il résume les interfaces et les classes de base du fournisseur Windows PowerShell qui sont utilisées. |
| [Création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md)           | Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet au runtime Windows PowerShell d’initialiser et d’initialiser le fournisseur.                                        |
| [Création d’un fournisseur de lecteur Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)           | Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur d’accéder à un magasin de données via un lecteur Windows PowerShell.                                                |
| [Création d’un fournisseur d’élément Windows PowerShell](./creating-a-windows-powershell-item-provider.md)             | Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de manipuler les éléments d’un magasin de données.                                                                  |
| [Création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md)   | Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de travailler sur des magasins de données multicouches.                                                                        |
| [Création d’un fournisseur de navigation Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md) | Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de parcourir les éléments d’un magasin de données de manière hiérarchique.                                           |
| [Création d’un fournisseur de contenu Windows PowerShell](./creating-a-windows-powershell-content-provider.md)       | Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de manipuler le contenu des éléments d’un magasin de données.                                                       |
| [Création d’un fournisseur de propriété Windows PowerShell](./creating-a-windows-powershell-property-provider.md)     | Cette rubrique montre comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de manipuler les propriétés des éléments d’un magasin de données.                                                    |

## <a name="see-also"></a>Voir aussi

[Fonctionnement de Windows PowerShell](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)
