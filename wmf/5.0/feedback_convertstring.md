---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219264"
---
# <a name="convert-string"></a><span data-ttu-id="f698a-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="f698a-102">Convert-String</span></span>
<span data-ttu-id="f698a-103">**Convert-String** expose une fonctionnalité de « remplacement par magie ».</span><span class="sxs-lookup"><span data-stu-id="f698a-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="f698a-104">Fournissez des exemples indiquant l’aspect souhaité du texte avant et après l’opération, et l’applet de commande **Convert-String** met automatiquement en forme le texte.</span><span class="sxs-lookup"><span data-stu-id="f698a-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="f698a-105">Voici un exemple qui prend un prénom et un nom, et les remplace par le nom, une virgule, l’initiale du prénom, puis un point.</span><span class="sxs-lookup"><span data-stu-id="f698a-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="f698a-106">Essayez avec une expression régulière et regardez combien de temps cela vous prend.</span><span class="sxs-lookup"><span data-stu-id="f698a-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
