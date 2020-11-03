---
description: Décrit une commande de langage que vous pouvez utiliser pour exécuter des listes d’instructions basées sur les résultats d’un ou plusieurs tests conditionnels.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 7f63b6f12743390608e0da72adb4098ce0583751
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207066"
---
# <a name="about-if"></a>À propos de si

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit une commande de langage que vous pouvez utiliser pour exécuter des listes d’instructions basées sur les résultats d’un ou plusieurs tests conditionnels.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Vous pouvez utiliser l' `If` instruction pour exécuter des blocs de code si un test conditionnel spécifié prend la valeur true. Vous pouvez également spécifier un ou plusieurs tests conditionnels supplémentaires à exécuter si tous les tests précédents ont la valeur false. Enfin, vous pouvez spécifier un bloc de code supplémentaire qui est exécuté si aucun autre test conditionnel antérieur ne prend la valeur true.

### <a name="syntax"></a>Syntaxe

L’exemple suivant illustre la `If` syntaxe de l’instruction :

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

Lorsque vous exécutez une `If` instruction, PowerShell évalue l' `<test1>` expression conditionnelle comme true ou false. Si `<test1>` a la valeur true, `<statement list 1>` s’exécute et PowerShell quitte l' `If` instruction. Si `<test1>` a la valeur false, PowerShell évalue la condition spécifiée par l' `<test2>` instruction conditionnelle.

Si `<test2>` a la valeur true, `<statement list 2>` s’exécute et PowerShell quitte l' `If` instruction. Si `<test1>` et ont tous deux `<test2>` la valeur false, le `<statement list 3` bloc de code> s’exécute et PowerShell quitte l’instruction if.

Vous pouvez utiliser plusieurs instructions ElseIf pour chaîner une série de tests conditionnels. Par conséquent, chaque test est exécuté uniquement si tous les tests précédents ont la valeur false.
Si vous avez besoin de créer une `If` instruction qui contient de nombreuses instructions ElseIf, envisagez d’utiliser une instruction switch à la place.

Exemples :

L’instruction la plus simple `If` contient une seule commande et ne contient aucune instruction ElseIf, ni aucune instruction Else. L’exemple suivant montre la forme la plus simple de l' `If` instruction :

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

Dans cet exemple, si la variable $a est supérieure à 2, la condition prend la valeur true et la liste d’instructions est exécutée. Toutefois, si $a est inférieur ou égal à 2 ou qu’il ne s’agit pas d’une variable existante, l' `If` instruction n’affiche pas de message.

En ajoutant une instruction Else, un message s’affiche lorsque $a est inférieur ou égal à 2. Comme le montre l’exemple suivant :

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

Pour affiner cet exemple, vous pouvez utiliser l’instruction ElseIf pour afficher un message lorsque la valeur de $a est égale à 2. Comme le montre l’exemple suivant :

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

## <a name="see-also"></a>VOIR AUSSI

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Switch](about_Switch.md)
