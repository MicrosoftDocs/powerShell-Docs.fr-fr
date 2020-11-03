---
description: Décrit une instruction que vous pouvez utiliser pour quitter immédiatement les instructions,,,, `foreach` `for` `while` `do` `switch` ou `trap` .
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: 8716f81163cfd34684c3ef7071f7827f2e9b5bcf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207178"
---
# <a name="about-break"></a>À propos des arrêts

## <a name="short-description"></a>Description courte

Décrit une instruction que vous pouvez utiliser pour quitter immédiatement les instructions,,,, `foreach` `for` `while` `do` `switch` ou `trap` .

## <a name="long-description"></a>Description longue

L' `break` instruction fournit un moyen de quitter le bloc de contrôle actuel.
L’exécution se poursuit à l’instruction suivante après le bloc de contrôle. L’instruction prend en charge les étiquettes. Une étiquette est un nom que vous attribuez à une instruction dans un script.

## <a name="using-break-in-loops"></a>Utilisation de boucles Break in

Lorsqu’une `break` instruction apparaît dans une boucle, telle qu’une `foreach` boucle,, `for` `do` ou `while` , PowerShell quitte immédiatement la boucle.

Une `break` instruction peut inclure une étiquette qui vous permet de quitter des boucles incorporées. Une étiquette peut spécifier n’importe quel mot clé de boucle, tel que `foreach` , `for` ou `while` , dans un script.

L’exemple suivant montre comment utiliser une `break` instruction pour quitter une `for` instruction :

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

Dans cet exemple, l' `break` instruction quitte la `for` boucle lorsque la `$i` variable est égale à 1. Même si l' `for` instruction prend la **valeur true** jusqu’à ce que `$i` soit supérieur à 10, PowerShell atteint l’instruction Break la première fois que la `for` boucle est exécutée.

Il est plus courant d’utiliser l' `break` instruction dans une boucle où une condition interne doit être remplie. Prenons l’exemple de l' `foreach` instruction suivante :

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

Dans cet exemple, l' `foreach` instruction itère le `$varB` tableau. L' `if` instruction prend la valeur false les deux premières fois que la boucle est exécutée et la variable `$i` est incrémentée de 1. La troisième fois que la boucle est exécutée, est `$i` égal à 2 et la `$val` variable est égale à 30. À ce stade, l' `break` instruction s’exécute et la `foreach` boucle se termine.

### <a name="using-a-labeled-break-in-a-loop"></a>Utilisation d’un saut de chaîne étiqueté dans une boucle

Une `break` instruction peut inclure une étiquette. Si vous utilisez le `break` mot clé avec une étiquette, PowerShell quitte la boucle étiquetée au lieu de quitter la boucle en cours.
L’étiquette est un signe deux-points suivi d’un nom que vous attribuez. L’étiquette doit être le premier jeton d’une instruction, et elle doit être suivie par le mot clé de bouclage, par exemple `while` .

`break` déplace l’exécution en dehors de la boucle étiquetée. Dans les boucles incorporées, le résultat est différent de celui du `break` mot clé lorsqu’il est utilisé par lui-même. Cet exemple contient une `while` instruction avec une `for` instruction :

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

Si la condition 2 prend la **valeur true** , l’exécution du script passe à l’instruction qui suit la boucle étiquetée. Dans l’exemple, l’exécution recommence avec l’instruction `$a = $c` .

Vous pouvez imbriquer de nombreuses boucles étiquetées, comme illustré dans l’exemple suivant.

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

Si la `$b` variable prend la valeur true, l’exécution du script reprend après la boucle étiquetée « Red ». Si la `$c` variable prend la valeur true, l’exécution du contrôle de script reprend après la boucle étiquetée « Yellow ».

Si la `$a` variable prend la valeur true, l’exécution reprend après la boucle la plus profonde. Aucune étiquette n’est nécessaire.

PowerShell ne limite pas la manière dont les étiquettes peuvent reprendre l’exécution. L’étiquette peut même passer le contrôle entre les limites d’appel de script et de fonction.

## <a name="using-break-in-a-switch-statement"></a>Utilisation de Break dans une instruction switch

Dans une `switch` construction, `break` fait en sorte que PowerShell quitte le `switch` bloc de code.

Le `break` mot clé est utilisé pour conserver la `switch` construction. Par exemple, l' `switch` instruction suivante utilise des `break` instructions pour tester la condition la plus spécifique :

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

Dans cet exemple, la `$var` variable est créée et initialisée avec une valeur de chaîne de `word2` . L' `switch` instruction utilise la classe **Regex** pour faire correspondre d’abord la valeur de la variable au terme `word2` . Étant donné que la valeur de la variable et le premier test de l' `switch` instruction correspondent, le premier bloc de code de l' `switch` instruction s’exécute.

Lorsque PowerShell atteint la première `break` instruction, l' `switch` instruction se termine. Si les quatre `break` instructions sont supprimées de l’exemple, les quatre conditions sont remplies. L’exemple suivant utilise l' `break` instruction pour afficher les résultats lorsque la condition la plus spécifique est remplie.

## <a name="using-break-in-a-trap-statement"></a>Utilisation de Break dans une instruction Trap

Si la dernière instruction exécutée dans le corps d’une `trap` instruction est `break` , l’objet d’erreur est supprimé et l’exception est de nouveau levée.

L’exemple suivant crée une exception **DivideByZeroException** qui est interceptée à l’aide de l' `trap` instruction.

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

Notez que l’exécution s’arrête à l’exception. `After loop`N’est jamais atteint.
L’exception est à nouveau levée après l' `trap` exécution de.

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
Attempted to divide by zero.
At line:10 char:6
+      "1 / $i = " + (1 / $i--)
+      ~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RuntimeException
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a>N’utilisez pas de saut en dehors d’une boucle, d’un commutateur ou d’une interruption

Quand `break` est utilisé en dehors d’une construction qui le prend directement en charge (boucles, `switch` , `trap` ), PowerShell recherche _la pile des appels_ pour une construction englobante. S’il ne trouve pas de construction englobante, l’instance d’exécution actuelle est arrêtée en mode silencieux.

Cela signifie que les fonctions et les scripts qui utilisent par inadvertance un `break` en dehors d’une construction englobante qui la prend en charge peuvent mettre fin par inadvertance à leurs _appelants_ .

L’utilisation `break` de l’intérieur d’un pipeline `break` , tel qu’un `ForEach-Object` bloc de script, non seulement quitte le pipeline, mais il peut mettre fin à la totalité de l’instance d’exécution.

## <a name="see-also"></a>Voir aussi

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Continue](about_Continue.md)

[about_For](about_For.md)

[about_Foreach](about_Foreach.md)

[about_Switch](about_Switch.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)

[about_While](about_While.md)
