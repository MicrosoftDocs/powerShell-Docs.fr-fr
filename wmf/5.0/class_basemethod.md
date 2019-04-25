---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 0e79127faf3f9bf6fe7d525db5bb946daf3b93e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058622"
---
# <a name="call-base-class-method"></a><span data-ttu-id="b316e-102">Appeler une méthode de classe de base</span><span class="sxs-lookup"><span data-stu-id="b316e-102">Call Base Class Method</span></span>

<span data-ttu-id="b316e-103">Vous pouvez substituer des méthodes existantes dans les sous-classes.</span><span class="sxs-lookup"><span data-stu-id="b316e-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="b316e-104">Pour cela, déclarez les méthodes à l’aide des mêmes nom et signature :</span><span class="sxs-lookup"><span data-stu-id="b316e-104">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="b316e-105">Pour appeler des méthodes de classe de base à partir des implémentations substituées, effectuez un transtypage vers la classe de base ([baseClass]$this) lors de l’appel :</span><span class="sxs-lookup"><span data-stu-id="b316e-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="b316e-106">Toutes les méthodes PowerShell sont virtuelles.</span><span class="sxs-lookup"><span data-stu-id="b316e-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="b316e-107">Vous pouvez masquer les méthodes .NET non virtuelles dans une sous-classe en utilisant la même syntaxe que pour une substitution : il vous suffit de déclarer des méthodes avec les mêmes nom et signature.</span><span class="sxs-lookup"><span data-stu-id="b316e-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```
