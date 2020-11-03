---
description: Quitte l'étendue active (fonction, script ou bloc de script).
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: c0c5b60163870e9352f0c3aa750d5603f29a81b1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208242"
---
# <a name="about-return"></a>À propos du retour

## <a name="short-description"></a>Description courte

Quitte l'étendue active (fonction, script ou bloc de script).

## <a name="long-description"></a>Description longue

Le `return` mot clé quitte une fonction, un script ou un bloc de script. Il peut être utilisé pour quitter une étendue à un point spécifique, pour retourner une valeur ou pour indiquer que la fin de l’étendue a été atteinte.

Les utilisateurs qui sont familiarisés avec les langages tels que C ou C \# peuvent souhaiter utiliser le `return` mot clé pour rendre une portée explicite.

Dans PowerShell, les résultats de chaque instruction sont retournés en tant que sortie, même si aucune instruction ne contient le mot clé return. Les langages tels que C ou C \# retournent uniquement la valeur ou les valeurs spécifiées par le `return` mot clé.

> [!NOTE]
> À compter de PowerShell 5,0, PowerShell a ajouté le langage pour la définition des classes, à l’aide de la syntaxe formelle.  Dans le contexte d’une classe PowerShell, rien n’est généré à partir d’une méthode, à l’exception de ce que vous spécifiez à l’aide d’une `return` instruction. Vous pouvez en savoir plus sur les classes PowerShell dans [about_Classes](about_Classes.md).

### <a name="syntax"></a>Syntaxe

La syntaxe du `return` mot clé est la suivante :

```
return [<expression>]
```

Le `return` mot clé peut apparaître seul, ou il peut être suivi d’une valeur ou d’une expression, comme suit :

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a>Exemples

L’exemple suivant utilise le `return` mot clé pour quitter une fonction à un point spécifique si une condition est remplie. Les nombres impairs ne sont pas multipliés, car l’instruction return se termine avant que cette instruction puisse s’exécuter.

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

Dans PowerShell, les valeurs peuvent être retournées même si le `return` mot clé n’est pas utilisé.
Les résultats de chaque instruction sont retournés. Par exemple, les instructions suivantes retournent la valeur de la `$a` variable :

```powershell
$a
return
```

L’instruction suivante retourne également la valeur de `$a` :

```powershell
return $a
```

L’exemple suivant comprend une instruction destinée à permettre à l’utilisateur de savoir que la fonction effectue un calcul :

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

«Veuillez patienter. Utilisation du calcul...» la chaîne n’est pas affichée. Au lieu de cela, elle est assignée à la `$a` variable, comme dans l’exemple suivant :

```
PS> $a
Please wait. Working on calculation...
87
```

La chaîne d’information et le résultat du calcul sont retournés par la fonction et assignés à la `$a` variable.

Si vous souhaitez afficher un message dans votre fonction, à compter de PowerShell 5,0, vous pouvez utiliser le `Information` flux. Le code ci-dessous corrige l’exemple ci-dessus à l’aide de l' `Write-Information` applet de commande avec un `InformationAction` de **continue** .

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a>Valeurs de retour et pipeline

Lorsque vous retournez une collection à partir d’un bloc de script ou d’une fonction, PowerShell dérouler automatiquement les membres et les transmet un par un à un autre via le pipeline. Cela est dû au traitement « un à la fois » de PowerShell. Pour plus d’informations, consultez [about_Pipelines](about_pipelines.md).

Ce concept est illustré par l’exemple de fonction suivant qui retourne un tableau de nombres. La sortie de la fonction est dirigée vers l' `Measure-Object` applet de commande qui compte le nombre d’objets dans le pipeline.

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

Pour forcer un bloc de script ou une fonction à retourner une collection en tant qu’objet unique au pipeline, utilisez l’une des deux méthodes suivantes :

- Expression de tableau unaire

  À l’aide d’une expression unaire, vous pouvez envoyer votre valeur de retour dans le pipeline en tant qu’objet unique, comme illustré dans l’exemple suivant.

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- `Write-Output` avec le paramètre **noenumerate** .

  Vous pouvez également utiliser l' `Write-Output` applet de commande avec le paramètre **noenum** . L’exemple ci-dessous utilise l' `Measure-Object` applet de commande pour compter les objets envoyés au pipeline à partir de l’exemple de fonction par le `return` mot clé.

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a>Voir aussi

[about_Language_Keywords](about_Language_Keywords.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[À propos des classes](about_Classes.md)

[Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)

[about_Script_Blocks](about_Script_Blocks.md)

