---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="825ed-102">Déclarer une interface implémentée</span><span class="sxs-lookup"><span data-stu-id="825ed-102">Declare Implemented Interface</span></span>

<span data-ttu-id="825ed-103">Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points (:), si aucun type de base n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="825ed-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="825ed-104">Séparez tous les noms de types par des virgules.</span><span class="sxs-lookup"><span data-stu-id="825ed-104">Separate all type names by using commas.</span></span> <span data-ttu-id="825ed-105">Cela ressemble beaucoup à la syntaxe C#.</span><span class="sxs-lookup"><span data-stu-id="825ed-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```
