---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: b839b476bb4ef7f8d73b158d61f0e8cbc1265e60
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="00285-102">Le mot clé Import-DscResource prend en charge le paramètre -ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="00285-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="00285-103">Nous avons ajouté un nouveau paramètre au mot-clé dynamique `Import-DscResource` disponible lors de la création de configurations DSC.</span><span class="sxs-lookup"><span data-stu-id="00285-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="00285-104">Les auteurs de configuration peuvent désormais spécifier exactement la version du module à partir de laquelle charger les ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="00285-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="00285-105">La nouvelle syntaxe du mot clé est la suivante :</span><span class="sxs-lookup"><span data-stu-id="00285-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="00285-106">**Name** : noms d’une ou plusieurs ressources à importer.</span><span class="sxs-lookup"><span data-stu-id="00285-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="00285-107">**ModuleName** : noms de modules ou objets ModuleSpecification d’un ou plusieurs modules à importer.</span><span class="sxs-lookup"><span data-stu-id="00285-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="00285-108">**ModuleVersion** : version du module à importer.</span><span class="sxs-lookup"><span data-stu-id="00285-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="00285-109">En cas d’utilisation, ModuleName doit représenter un seul module par nom.</span><span class="sxs-lookup"><span data-stu-id="00285-109">If used, ModuleName must represent only one module by name.</span></span> 

<span data-ttu-id="00285-110">Dans Windows PowerShell ISE, il apparaît avec IntelliSense :</span><span class="sxs-lookup"><span data-stu-id="00285-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="00285-111">**Remarque** : vous pouvez utiliser le paramètre `–ModuleVersion` uniquement avec le paramètre `–ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="00285-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="00285-112">Vous ne pouvez pas l’utiliser avec des noms de ressources utilisant uniquement le paramètre `–Name`.</span><span class="sxs-lookup"><span data-stu-id="00285-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="00285-113">Avant cela, la seule façon de spécifier la version du module lors du chargement des ressources DSC consistait à utiliser l’objet de spécification Module, par exemple : `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="00285-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>

