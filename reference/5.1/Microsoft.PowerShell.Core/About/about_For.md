---
description: Décrit une commande de langage que vous pouvez utiliser pour exécuter des instructions basées sur un test conditionnel.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 28d901c62ccc17febb74412a773710f4d5b5a4be
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207673"
---
# <a name="about-for"></a>À propos de pour

## <a name="short-description"></a>Description courte
Décrit une commande de langage que vous pouvez utiliser pour exécuter des instructions basées sur un test conditionnel.

## <a name="long-description"></a>Description longue

L' `For` instruction (également appelée `For` boucle) est une construction de langage que vous pouvez utiliser pour créer une boucle qui exécute des commandes dans un bloc de commande alors qu’une condition spécifiée a la valeur `$true` .

Une utilisation courante de la `For` boucle consiste à itérer un tableau de valeurs et à opérer sur un sous-ensemble de ces valeurs. Dans la plupart des cas, si vous souhaitez itérer toutes les valeurs d’un tableau, envisagez d’utiliser une `Foreach` instruction.

### <a name="syntax"></a>Syntaxe

L’exemple suivant illustre la syntaxe de l' `For` instruction.

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

L’espace réservé **init** représente une ou plusieurs commandes qui sont exécutées avant le début de la boucle. En général, vous utilisez la partie **init** de l’instruction pour créer et initialiser une variable avec une valeur de départ.

Cette variable sera ensuite la base de la condition à tester dans la partie suivante de l' `For` instruction.

L’espace réservé de **condition** représente la partie de l' `For` instruction qui correspond à une `$true` valeur `$false` **booléenne** ou. PowerShell évalue la condition chaque fois que la `For` boucle s’exécute. Si l’instruction est `$true` , les commandes du bloc de commande s’exécutent et l’instruction est de nouveau évaluée. Si la condition est toujours `$true` , les commandes de la **liste d’instructions** s’exécutent à nouveau. La boucle est répétée jusqu’à ce que la condition devienne `$false` .

L’espace réservé **REPEAT** représente une ou plusieurs commandes, séparées par des virgules, qui sont exécutées chaque fois que la boucle se répète. En général, il est utilisé pour modifier une variable qui est testée à l’intérieur de la partie **condition** de l’instruction.

L’espace réservé de la **liste d’instructions** représente un ensemble d’une ou plusieurs commandes qui sont exécutées chaque fois que la boucle est entrée ou répétée. Le contenu de la **liste d’instructions** est entouré d’accolades.

### <a name="support-for-multiple-operations"></a>Prise en charge de plusieurs opérations

Les syntaxes suivantes sont prises en charge pour les opérations d’assignation multiples dans l’instruction **init** :

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

Les syntaxes suivantes sont prises en charge pour les opérations d’assignation multiples dans l’instruction **REPEAT** :

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> Les opérations autres que pre ou after Increment peuvent ne pas fonctionner avec toutes les syntaxes.

Pour plusieurs **conditions** , utilisez des opérateurs logiques, comme illustré dans l’exemple suivant.

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

Pour plus d’informations, consultez [about_Logical_Operators](about_Logical_Operators.md).

### <a name="examples"></a>Exemples

Au minimum, une `For` instruction requiert la parenthèse entourant les éléments **init** , **condition** et **REPEAT** de l’instruction et une commande placée entre accolades dans la partie de la **liste d’instructions** de l’instruction.

Notez que les exemples à venir montrent intentionnellement du code en dehors de l' `For` instruction. Dans des exemples ultérieurs, le code est intégré à l' `For` instruction.

Par exemple, l' `For` instruction suivante affiche continuellement la valeur de la `$i` variable jusqu’à ce que vous sautiez manuellement de la commande en appuyant sur Ctrl + C.

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

Vous pouvez ajouter des commandes supplémentaires à la liste d’instructions afin que la valeur de `$i` soit incrémentée de 1 chaque fois que la boucle est exécutée, comme le montre l’exemple suivant.

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

Jusqu’à sortir de la commande en appuyant sur CTRL + C, cette instruction affiche continuellement la valeur de la `$i` variable, car elle est incrémentée de 1 chaque fois que la boucle est exécutée.

Au lieu de modifier la valeur de la variable dans la partie de la liste d’instructions de l' `For` instruction, vous pouvez utiliser la portion **REPEAT** de l' `For` instruction à la place, comme suit.

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

Cette instruction se répète toujours indéfiniment jusqu’à sortir de la commande en appuyant sur CTRL + C.

Vous pouvez arrêter la `For` boucle à l’aide d’une *condition* . Vous pouvez placer une condition à l’aide de la partie **condition** de l' `For` instruction. La `For` boucle se termine lorsque la condition prend la valeur `$false` .

Dans l’exemple suivant, la `For` boucle s’exécute tandis que la valeur de `$i` est inférieure ou égale à 10.

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

Au lieu de créer et d’initialiser la variable en dehors de l' `For` instruction, vous pouvez effectuer cette tâche à l’intérieur de la boucle à l' `For` aide de la partie **init** de l' `For` instruction.

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

Vous pouvez utiliser des retours chariot plutôt que des points-virgules pour délimiter les portions **init** , **condition** et **REPEAT** de l' `For` instruction. L’exemple suivant montre un `For` qui utilise cette syntaxe alternative.

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

Cette autre forme de l' `For` instruction fonctionne dans les fichiers de script PowerShell et à l’invite de commandes PowerShell. Toutefois, il est plus facile d’utiliser la `For` syntaxe de l’instruction avec des points-virgules lorsque vous entrez des commandes interactives à l’invite de commandes.

La `For` boucle est plus flexible que la `Foreach` boucle, car elle vous permet d’incrémenter des valeurs dans un tableau ou une collection à l’aide de modèles. Dans l’exemple suivant, la `$i` variable est incrémentée de 2 dans la partie **REPEAT** de l' `For` instruction.

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

La `For` boucle peut également être écrite sur une ligne comme dans l’exemple suivant.

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a>VOIR AUSSI

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Foreach](about_Foreach.md)
