---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="65301-102">Déclarer une interface implémentée</span><span class="sxs-lookup"><span data-stu-id="65301-102">Declare Implemented Interface</span></span>

<span data-ttu-id="65301-103">Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points (:), si aucun type de base n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="65301-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="65301-104">Séparez tous les noms de types par des virgules.</span><span class="sxs-lookup"><span data-stu-id="65301-104">Separate all type names by using commas.</span></span> <span data-ttu-id="65301-105">Cela ressemble beaucoup à la syntaxe C#.</span><span class="sxs-lookup"><span data-stu-id="65301-105">It’s very similar to C# syntax.</span></span>

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

