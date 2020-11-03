---
description: Décrit une instruction de langage que vous pouvez utiliser pour exécuter un bloc de commande en fonction des résultats d’un test conditionnel.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 0adc435eeba6b07e1f16aec5dd1328ddd80c4612
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206809"
---
# <a name="about-while"></a>À propos de while

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit une instruction de langage que vous pouvez utiliser pour exécuter un bloc de commande en fonction des résultats d’un test conditionnel.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

L’instruction while (également appelée « boucle while ») est une construction de langage permettant de créer une boucle qui exécute des commandes dans un bloc de commande tant qu’un test conditionnel prend la valeur true. L’instruction while est plus facile à construire qu’une instruction for, car sa syntaxe est moins compliquée. En outre, il est plus souple que l’instruction foreach, car vous spécifiez un test conditionnel dans l’instruction while pour contrôler le nombre de fois que la boucle s’exécute.

L’exemple suivant illustre la syntaxe de l’instruction while :

```powershell
while (<condition>){<statement list>}
```

Quand vous exécutez une instruction while, PowerShell évalue la `<condition>` section de l’instruction avant d’entrer dans la `<statement list>` section. La partie condition de l’instruction correspond à true ou false. Tant que la condition reste vraie, PowerShell réexécute la `<statement list>` section.

La `<statement list>` section de l’instruction contient une ou plusieurs commandes qui sont exécutées chaque fois que la boucle est entrée ou répétée.

Par exemple, l’instruction while suivante affiche les nombres 1 à 3 Si la variable $val n’a pas été créée ou si la $val variable a été créée et initialisée à 0.

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

Dans cet exemple, la condition ($val n’est pas égale à 3) est vraie alors que $val \= 0, 1, 2. Chaque fois que la boucle est utilisée, $val est incrémenté de 1 à l’aide de l' \+ \+ opérateur d’incrémentation unaire ($Val \+ \+ ). La dernière fois dans la boucle, $val \= 3. Lorsque $val est égal à 3, l’instruction de condition prend la valeur false et la boucle se termine.

Pour écrire facilement cette commande à l’invite de commandes PowerShell, vous pouvez l’entrer de la façon suivante :

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

Notez que le point-virgule sépare la première commande qui ajoute 1 à $val de la deuxième commande qui écrit la valeur de $val dans la console.

## <a name="see-also"></a>VOIR AUSSI

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Do](about_Do.md)

[about_Foreach](about_Foreach.md)

[about_For](about_For.md)

[about_Language_Keywords](about_Language_Keywords.md)
