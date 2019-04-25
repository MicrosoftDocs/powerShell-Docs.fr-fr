---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085851"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="eff29-102">Déclarer une interface implémentée</span><span class="sxs-lookup"><span data-stu-id="eff29-102">Declare Implemented Interface</span></span>

<span data-ttu-id="eff29-103">Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points (:), si aucun type de base n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="eff29-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="eff29-104">Séparez tous les noms de types par des virgules.</span><span class="sxs-lookup"><span data-stu-id="eff29-104">Separate all type names by using commas.</span></span> <span data-ttu-id="eff29-105">Cela ressemble beaucoup à la syntaxe C#.</span><span class="sxs-lookup"><span data-stu-id="eff29-105">It’s very similar to C# syntax.</span></span>

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
