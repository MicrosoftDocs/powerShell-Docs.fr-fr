---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 8b414331bbfb7dc71d960241a6bc83b0b22641db
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="creating-custom-types-using-powershell-classes"></a>Création de types personnalisés à l’aide de classes PowerShell

Nous avons amélioré le langage PowerShell pour la définition des classes et d’autres types définis par l’utilisateur à l’aide de la syntaxe formelle et d’une sémantique similaire aux autres langages de programmation orientés objet. L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’utiliser PowerShell pour une plus grande variété de cas d’usage, de simplifier le développement des artefacts PowerShell (tels que les ressources DSC) et d’accélérer la couverture des surfaces de gestion.

## <a name="supported-scenarios-in-this-release"></a>Scénarios pris en charge dans cette version

-   Définition de ressources DSC et de leurs types associés à l’aide du langage PowerShell
-   Définition de types personnalisés dans PowerShell à l’aide de constructions de programmation orientées objet bien connues, telles que les classes, propriétés, méthodes, etc.
-   Prise en charge de l’héritage avec la classe dans PowerShell et ressource DSC de base de classe
-   Débogage de types à l’aide du langage PowerShell
-   Génération et gestion des exceptions à l’aide de mécanismes formels et au niveau approprié

