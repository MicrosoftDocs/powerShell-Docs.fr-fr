---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressources DSC
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="aba99-103">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="aba99-103">DSC Resources</span></span>

><span data-ttu-id="aba99-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aba99-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="aba99-105">Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="aba99-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="aba99-106">Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="aba99-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="aba99-107">Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="aba99-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="aba99-108">Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.</span><span class="sxs-lookup"><span data-stu-id="aba99-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="aba99-109">Les rubriques suivantes décrivent les ressources DSC :</span><span class="sxs-lookup"><span data-stu-id="aba99-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="aba99-110">Ressources DSC intégrées</span><span class="sxs-lookup"><span data-stu-id="aba99-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="aba99-111">Créer des ressources DSC personnalisées</span><span class="sxs-lookup"><span data-stu-id="aba99-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="aba99-112">Ressources DSC intégrées pour Linux</span><span class="sxs-lookup"><span data-stu-id="aba99-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)