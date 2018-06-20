---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221848"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="5db93-102">Ressources DSC basées sur une classe</span><span class="sxs-lookup"><span data-stu-id="5db93-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="5db93-103">Définition de ressources DSC avec des classes</span><span class="sxs-lookup"><span data-stu-id="5db93-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="5db93-104">Suite à vos commentaires, nous avons simplifié la création et la compréhension des ressources DSC basées sur des classes.</span><span class="sxs-lookup"><span data-stu-id="5db93-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="5db93-105">Les principales différences entre une ressource DSC basée sur une classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5db93-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="5db93-106">Aucun fichier MOF pour le schéma n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5db93-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="5db93-107">Aucun sous-dossier **DSCResource** dans le dossier de module n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5db93-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="5db93-108">Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="5db93-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="5db93-109">Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="5db93-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
