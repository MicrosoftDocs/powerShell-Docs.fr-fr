---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: dfc171f9a3471f8fe7801283dd4a9b06860781a2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="creating-custom-types-using-powershell-classes"></a>Création de types personnalisés à l’aide de classes PowerShell

Nous avons amélioré le langage PowerShell pour la définition des classes et d’autres types définis par l’utilisateur à l’aide de la syntaxe formelle et d’une sémantique similaire aux autres langages de programmation orientés objet. L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’utiliser PowerShell pour une plus grande variété de cas d’usage, de simplifier le développement des artefacts PowerShell (tels que les ressources DSC) et d’accélérer la couverture des surfaces de gestion.

## <a name="supported-scenarios-in-this-release"></a>Scénarios pris en charge dans cette version

-   Définition de ressources DSC et de leurs types associés à l’aide du langage PowerShell
-   Définition de types personnalisés dans PowerShell à l’aide de constructions de programmation orientées objet bien connues, telles que les classes, propriétés, méthodes, etc.
-   Prise en charge de l’héritage avec la classe dans PowerShell et ressource DSC de base de classe
-   Débogage de types à l’aide du langage PowerShell
-   Génération et gestion des exceptions à l’aide de mécanismes formels et au niveau approprié
