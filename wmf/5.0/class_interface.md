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
# <a name="declare-implemented-interface"></a>Déclarer une interface implémentée

Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points (:), si aucun type de base n’est spécifié. Séparez tous les noms de types par des virgules. Cela ressemble beaucoup à la syntaxe C#.

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
