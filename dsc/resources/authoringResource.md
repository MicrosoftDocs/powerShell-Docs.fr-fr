---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Création de ressources DSC Windows PowerShell personnalisées
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401221"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="3c611-103">Création de ressources DSC Windows PowerShell personnalisées</span><span class="sxs-lookup"><span data-stu-id="3c611-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="3c611-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3c611-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3c611-105">La configuration de l’état souhaité (DSC) de Windows PowerShell comprend des ressources intégrées que vous pouvez utiliser pour configurer votre environnement.</span><span class="sxs-lookup"><span data-stu-id="3c611-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="3c611-106">Cette rubrique constitue une présentation du développement de ressources et fournit des liens vers des rubriques contenant des informations spécifiques et des exemples.</span><span class="sxs-lookup"><span data-stu-id="3c611-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="3c611-107">Composants de la ressource DSC</span><span class="sxs-lookup"><span data-stu-id="3c611-107">DSC resource components</span></span>

<span data-ttu-id="3c611-108">Une ressource DSC est un module Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c611-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="3c611-109">Le module contient à la fois le schéma (la définition des propriétés configurables) et l’implémentation (le code qui effectue le travail spécifié par une configuration) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="3c611-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="3c611-110">Un schéma de ressources DSC peut être défini dans un fichier MOF et l’implémentation est effectuée par un module de script.</span><span class="sxs-lookup"><span data-stu-id="3c611-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="3c611-111">À partir de la version 5 des classes PowerShell, le schéma et l’implémentation peuvent être définis dans une classe.</span><span class="sxs-lookup"><span data-stu-id="3c611-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="3c611-112">Les rubriques suivantes expliquent plus en détail comment créer des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="3c611-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="3c611-113">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="3c611-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="3c611-114">Implementing a DSC resource in C#</span><span class="sxs-lookup"><span data-stu-id="3c611-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="3c611-115">Écriture d’une ressource DSC personnalisée avec les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c611-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="3c611-116">Ressources composites : utilisation d’une configuration DSC comme ressource</span><span class="sxs-lookup"><span data-stu-id="3c611-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="3c611-117">Utilisation du Concepteur de ressources</span><span class="sxs-lookup"><span data-stu-id="3c611-117">Using the Resource Designer tool</span></span>](../authoringResourceMofDesigner.md)