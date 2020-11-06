---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,installation
title: Création de ressources DSC Windows PowerShell personnalisées
description: Cet article constitue une présentation du développement de ressources et fournit des liens vers des articles contenant des informations spécifiques et des exemples.
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656403"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="d7189-104">Création de ressources DSC Windows PowerShell personnalisées</span><span class="sxs-lookup"><span data-stu-id="d7189-104">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="d7189-105">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d7189-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d7189-106">La configuration de l’état souhaité (DSC) de Windows PowerShell comprend des ressources intégrées que vous pouvez utiliser pour configurer votre environnement.</span><span class="sxs-lookup"><span data-stu-id="d7189-106">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="d7189-107">Cet article constitue une présentation du développement de ressources et fournit des liens vers des articles contenant des informations spécifiques et des exemples.</span><span class="sxs-lookup"><span data-stu-id="d7189-107">This article provides an overview of developing resources and links to articles with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="d7189-108">Composants de la ressource DSC</span><span class="sxs-lookup"><span data-stu-id="d7189-108">DSC resource components</span></span>

<span data-ttu-id="d7189-109">Une ressource DSC est un module Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7189-109">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="d7189-110">Le module contient à la fois le schéma (la définition des propriétés configurables) et l’implémentation (le code qui effectue le travail spécifié par une configuration) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="d7189-110">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="d7189-111">Un schéma de ressources DSC peut être défini dans un fichier MOF et l’implémentation est effectuée par un module de script.</span><span class="sxs-lookup"><span data-stu-id="d7189-111">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="d7189-112">À partir de la version 5 des classes PowerShell, le schéma et l’implémentation peuvent être définis dans une classe.</span><span class="sxs-lookup"><span data-stu-id="d7189-112">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="d7189-113">Les articles suivants expliquent plus en détail comment créer des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="d7189-113">The following articles describe in more detail how to create DSC resources.</span></span>

- [<span data-ttu-id="d7189-114">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="d7189-114">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="d7189-115">Implementing a DSC resource in C#</span><span class="sxs-lookup"><span data-stu-id="d7189-115">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
- [<span data-ttu-id="d7189-116">Écriture d’une ressource DSC personnalisée avec les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7189-116">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="d7189-117">Ressources composites : utilisation d’une configuration DSC comme ressource</span><span class="sxs-lookup"><span data-stu-id="d7189-117">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
- [<span data-ttu-id="d7189-118">Utilisation du Concepteur de ressources</span><span class="sxs-lookup"><span data-stu-id="d7189-118">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
