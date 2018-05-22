---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: d7aec1a2ba8964e877ddd7406609fe135b1eb462
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-method"></a>Appeler une méthode de classe de base

Vous pouvez substituer des méthodes existantes dans les sous-classes. Pour cela, déclarez les méthodes à l’aide des mêmes nom et signature :

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

Pour appeler des méthodes de classe de base à partir des implémentations substituées, effectuez un transtypage vers la classe de base ([baseClass]$this) lors de l’appel :

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

Toutes les méthodes PowerShell sont virtuelles. Vous pouvez masquer les méthodes .NET non virtuelles dans une sous-classe en utilisant la même syntaxe que pour une substitution : il vous suffit de déclarer des méthodes avec les mêmes nom et signature.

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
