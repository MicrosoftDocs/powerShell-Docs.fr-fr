---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085879"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="44e4a-102">Appeler un constructeur de classe de base</span><span class="sxs-lookup"><span data-stu-id="44e4a-102">Call Base Class Constructor</span></span>

<span data-ttu-id="44e4a-103">Pour appeler un constructeur de classe de base à partir d’une sous-classe, utilisez le mot clé **base** :</span><span class="sxs-lookup"><span data-stu-id="44e4a-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="44e4a-104">Si une classe de base a un constructeur par défaut (sans paramètre), vous pouvez omettre un appel de constructeur explicite :</span><span class="sxs-lookup"><span data-stu-id="44e4a-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
