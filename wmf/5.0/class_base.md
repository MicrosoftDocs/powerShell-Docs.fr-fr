---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 188ede0c558210a746ad0f6c6cef6f571b280878
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219903"
---
# <a name="declare-base-class"></a><span data-ttu-id="3ba18-102">Déclarer une classe de base</span><span class="sxs-lookup"><span data-stu-id="3ba18-102">Declare Base Class</span></span>
<span data-ttu-id="3ba18-103">Vous pouvez déclarer une classe Windows PowerShell comme type de base pour une autre classe Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ba18-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="3ba18-104">Vous pouvez également utiliser des types .NET Framework existants comme classes de base :</span><span class="sxs-lookup"><span data-stu-id="3ba18-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
