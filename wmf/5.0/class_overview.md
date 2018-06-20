---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: dfc171f9a3471f8fe7801283dd4a9b06860781a2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225723"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="8cac0-102">Création de types personnalisés à l’aide de classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="8cac0-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="8cac0-103">Nous avons amélioré le langage PowerShell pour la définition des classes et d’autres types définis par l’utilisateur à l’aide de la syntaxe formelle et d’une sémantique similaire aux autres langages de programmation orientés objet.</span><span class="sxs-lookup"><span data-stu-id="8cac0-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="8cac0-104">L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’utiliser PowerShell pour une plus grande variété de cas d’usage, de simplifier le développement des artefacts PowerShell (tels que les ressources DSC) et d’accélérer la couverture des surfaces de gestion.</span><span class="sxs-lookup"><span data-stu-id="8cac0-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="8cac0-105">Scénarios pris en charge dans cette version</span><span class="sxs-lookup"><span data-stu-id="8cac0-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="8cac0-106">Définition de ressources DSC et de leurs types associés à l’aide du langage PowerShell</span><span class="sxs-lookup"><span data-stu-id="8cac0-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="8cac0-107">Définition de types personnalisés dans PowerShell à l’aide de constructions de programmation orientées objet bien connues, telles que les classes, propriétés, méthodes, etc.</span><span class="sxs-lookup"><span data-stu-id="8cac0-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="8cac0-108">Prise en charge de l’héritage avec la classe dans PowerShell et ressource DSC de base de classe</span><span class="sxs-lookup"><span data-stu-id="8cac0-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="8cac0-109">Débogage de types à l’aide du langage PowerShell</span><span class="sxs-lookup"><span data-stu-id="8cac0-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="8cac0-110">Génération et gestion des exceptions à l’aide de mécanismes formels et au niveau approprié</span><span class="sxs-lookup"><span data-stu-id="8cac0-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
