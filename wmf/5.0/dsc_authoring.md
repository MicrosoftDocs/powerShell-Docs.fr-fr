---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="73124-102">Améliorations liées à la création à l’aide de PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="73124-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="73124-103">Créer des configurations DSC dans Windows PowerShell ISE est beaucoup plus facile grâce aux améliorations suivantes :</span><span class="sxs-lookup"><span data-stu-id="73124-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="73124-104">Énumération de toutes les ressources DSC dans un bloc **configuration** ou **node** en entrant **Ctrl+Espace** sur une ligne vide dans le bloc.</span><span class="sxs-lookup"><span data-stu-id="73124-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="73124-105">Saisie semi-automatique sur les propriétés de ressources de type **énumération**.</span><span class="sxs-lookup"><span data-stu-id="73124-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="73124-106">Saisie semi-automatique sur la propriété **DependsOn** des ressources DSC, basée sur d’autres instances de ressources dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="73124-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="73124-107">Meilleure saisie semi-automatique via la touche Tab pour les valeurs de propriétés de ressources.</span><span class="sxs-lookup"><span data-stu-id="73124-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="73124-108">**Remarque :** Vous devez avoir une chaîne vide pour les valeurs de propriétés de ressources pour pouvoir utiliser Ctrl+Espace pour répertorier les options.</span><span class="sxs-lookup"><span data-stu-id="73124-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="73124-109">Une pression sur la touche **Tab** permet de parcourir les options.</span><span class="sxs-lookup"><span data-stu-id="73124-109">Pressing **Tab** cycles through options.</span></span>