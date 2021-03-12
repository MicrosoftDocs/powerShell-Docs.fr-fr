---
description: Décrit comment l' `continue` instruction retourne immédiatement le déroulement du programme au début d’une boucle de programme, d’une `switch` instruction ou d’une `trap` instruction.
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 618ebee65d0407751e443fd957ab008d35c5375b
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195603"
---
# <a name="about-continue"></a>À propos de continue

## <a name="short-description"></a>Description courte

Décrit comment l' `continue` instruction retourne immédiatement le déroulement du programme au début d’une boucle de programme, d’une `switch` instruction ou d’une `trap` instruction.

## <a name="long-description"></a>Description longue

L' `continue` instruction fournit un moyen de quitter le bloc de contrôle actuel, mais de continuer l’exécution, au lieu de quitter complètement. L’instruction prend en charge les étiquettes.
Une étiquette est un nom que vous attribuez à une instruction dans un script.

## <a name="using-continue-in-loops"></a>Utilisation des boucles continue dans

Une `continue` instruction sans étiquette retourne immédiatement le déroulement du programme au début de la boucle la plus profonde qui est contrôlée par `for` une `foreach` instruction,, `do` ou `while` . L’itération actuelle de la boucle est terminée et la boucle se poursuit avec l’itération suivante.

Dans l’exemple suivant, le déroulement du programme revient au sommet de la `while` boucle si la `$ctr` variable est égale à 5. Par conséquent, tous les nombres compris entre 1 et 10 sont affichés, à l’exception de 5 :

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

Lors de l’utilisation d’une `for` boucle, l’exécution se poursuit au niveau de l' `<Repeat>` instruction, suivie du `<Condition>` test. Dans l’exemple ci-dessous, une boucle infinie ne se produit pas, car la décrémentation de `$i` se produit après le `continue` mot clé.

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a>Utilisation d’une étiquette continue dans une boucle

Une instruction étiquetée `continue` termine l’exécution de l’itération et transfère le contrôle à l’itération ou à l’étiquette d’instruction englobante ciblée `switch` .

Dans l’exemple suivant, le plus profond `for` se termine lorsque `$condition` a la **valeur true** et que l’itération continue avec la deuxième `for` boucle à `labelB` .

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a>Utilisation de continue dans une instruction switch

Une instruction sans étiquette `continue` dans un `switch` met fin à l’exécution de l' `switch` itération actuelle et transfère le contrôle vers le haut de `switch` pour obtenir l’élément d’entrée suivant.

Lorsqu’il existe un seul élément d’entrée `continue` , la totalité de l’instruction est fermée `switch` .
Lorsque l' `switch` entrée est une collection, le `switch` teste chaque élément de la collection. Le `continue` quitte l’itération actuelle et `switch` poursuit avec l’élément suivant.

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a>Utilisation de continue dans une instruction Trap

Si la dernière instruction exécutée dans le corps d’une `trap` instruction est `continue` , l’erreur interceptée est ignorée silencieusement et l’exécution se poursuit avec l’instruction qui suit immédiatement celle qui a entraîné l' `trap` apparition de.

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a>Ne pas utiliser continuer en dehors d’une boucle, d’un commutateur ou d’une interruption

Quand `continue` est utilisé en dehors d’une construction qui le prend directement en charge (boucles, `switch` , `trap` ), PowerShell recherche _la pile des appels_ pour une construction englobante. S’il ne trouve pas de construction englobante, l’instance d’exécution actuelle est arrêtée en mode silencieux.

Cela signifie que les fonctions et les scripts qui utilisent par inadvertance un `continue` en dehors d’une construction englobante qui la prend en charge peuvent arrêter par inadvertance leurs _appelants_.

L’utilisation `continue` de l’intérieur d’un pipeline, tel qu’un `ForEach-Object` bloc de script, non seulement quitte le pipeline, mais il peut mettre fin à la totalité de l’instance d’exécution.

## <a name="see-also"></a>Voir aussi

[about_Break](about_Break.md)

[about_For](about_For.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
