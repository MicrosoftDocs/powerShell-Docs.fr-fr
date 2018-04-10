---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Création de ressources DSC Windows PowerShell personnalisées
ms.openlocfilehash: 7da4741a773d40da75c6ef667c35f86e1bae74bf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="da0bf-103">Création de ressources DSC Windows PowerShell personnalisées</span><span class="sxs-lookup"><span data-stu-id="da0bf-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="da0bf-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="da0bf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="da0bf-105">La configuration de l’état souhaité (DSC) de Windows PowerShell comprend des ressources intégrées que vous pouvez utiliser pour configurer votre environnement.</span><span class="sxs-lookup"><span data-stu-id="da0bf-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="da0bf-106">Pour plus d’informations, consultez [Ressources DSC Windows PowerShell intégrées](builtInResource.md). Cette rubrique constitue une présentation du développement de ressources et fournit des liens vers des rubriques contenant des informations spécifiques et des exemples.</span><span class="sxs-lookup"><span data-stu-id="da0bf-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="da0bf-107">Composants de la ressource DSC</span><span class="sxs-lookup"><span data-stu-id="da0bf-107">DSC resource components</span></span>

<span data-ttu-id="da0bf-108">Une ressource DSC est un module Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da0bf-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="da0bf-109">Le module contient à la fois le schéma (la définition des propriétés configurables) et l’implémentation (le code qui effectue le travail spécifié par une configuration) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="da0bf-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="da0bf-110">Un schéma de ressources DSC peut être défini dans un fichier MOF et l’implémentation est effectuée par un module de script.</span><span class="sxs-lookup"><span data-stu-id="da0bf-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="da0bf-111">À partir de la version 5 des classes PowerShell, le schéma et l’implémentation peuvent être définis dans une classe.</span><span class="sxs-lookup"><span data-stu-id="da0bf-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="da0bf-112">Les rubriques suivantes expliquent plus en détail comment créer des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="da0bf-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="da0bf-113">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="da0bf-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="da0bf-114">Implementing a DSC resource in C#</span><span class="sxs-lookup"><span data-stu-id="da0bf-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="da0bf-115">Écriture d’une ressource DSC personnalisée avec les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="da0bf-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="da0bf-116">Ressources composites : utilisation d’une configuration DSC comme ressource</span><span class="sxs-lookup"><span data-stu-id="da0bf-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="da0bf-117">Utilisation du Concepteur de ressources</span><span class="sxs-lookup"><span data-stu-id="da0bf-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)