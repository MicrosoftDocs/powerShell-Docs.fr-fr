---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225604"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="935f6-102">Appeler un constructeur de classe de base</span><span class="sxs-lookup"><span data-stu-id="935f6-102">Call Base Class Constructor</span></span>

<span data-ttu-id="935f6-103">Pour appeler un constructeur de classe de base à partir d’une sous-classe, utilisez le mot clé **base** :</span><span class="sxs-lookup"><span data-stu-id="935f6-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="935f6-104">Si une classe de base a un constructeur par défaut (sans paramètre), vous pouvez omettre un appel de constructeur explicite :</span><span class="sxs-lookup"><span data-stu-id="935f6-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
