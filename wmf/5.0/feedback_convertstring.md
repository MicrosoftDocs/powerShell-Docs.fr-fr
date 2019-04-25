---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057789"
---
# <a name="convert-string"></a><span data-ttu-id="0d429-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="0d429-102">Convert-String</span></span>
<span data-ttu-id="0d429-103">**Convert-String** expose une fonctionnalité de « remplacement par magie ».</span><span class="sxs-lookup"><span data-stu-id="0d429-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="0d429-104">Fournissez des exemples indiquant l’aspect souhaité du texte avant et après l’opération, et l’applet de commande **Convert-String** met automatiquement en forme le texte.</span><span class="sxs-lookup"><span data-stu-id="0d429-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="0d429-105">Voici un exemple qui prend un prénom et un nom, et les remplace par le nom, une virgule, l’initiale du prénom, puis un point.</span><span class="sxs-lookup"><span data-stu-id="0d429-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="0d429-106">Essayez avec une expression régulière et regardez combien de temps cela vous prend.</span><span class="sxs-lookup"><span data-stu-id="0d429-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
