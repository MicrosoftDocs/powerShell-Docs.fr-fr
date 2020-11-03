---
description: Exécute une ou plusieurs fois une liste d’instructions, sous réserve d’une condition while ou until.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 9c5a7c561fde4d96401771870cf4e85d78591593
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208053"
---
# <a name="about-do"></a>À propos de

## <a name="short-description"></a>DESCRIPTION COURTE

Exécute une ou plusieurs fois une liste d’instructions, sous réserve d’une condition while ou until.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le mot clé do fonctionne avec le mot clé While ou le mot clé Until pour exécuter les instructions dans un bloc de script, sous réserve d’une condition. Contrairement à la boucle while associée, le bloc de script dans une boucle do s’exécute toujours au moins une fois.

Une boucle **do-while** est une variété de la boucle while. Dans une boucle **do-while** , la condition est évaluée après l’exécution du bloc de script. Comme dans une boucle while, le bloc de script est répété tant que la condition prend la valeur true.

À l’instar d’une boucle **do-while** , une boucle **Do-Until** s’exécute toujours au moins une fois avant que la condition soit évaluée. Toutefois, le bloc de script s’exécute uniquement lorsque la condition a la valeur false.

Les mots clés de contrôle de *continuation continue* et *break* peuvent être utilisés dans une boucle **do-while** ou dans une boucle **Do-Until** .

### <a name="syntax"></a>Syntaxe

L’exemple suivant illustre la syntaxe de l’instruction **do-while** :

```powershell
do {<statement list>} while (<condition>)
```

L’exemple suivant illustre la syntaxe de l’instruction **Do-Until** :

```powershell
do {<statement list>} until (<condition>)
```

La liste d’instructions contient une ou plusieurs instructions qui s’exécutent chaque fois que la boucle est entrée ou répétée.

La partie condition de l’instruction correspond à true ou false.

### <a name="example"></a>Exemple

L’exemple suivant d’une instruction do compte les éléments d’un tableau jusqu’à ce qu’il atteigne un élément avec une valeur de 0.

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

L’exemple suivant utilise le mot clé until. Notez que l’opérateur différent de ( `-ne` ) est remplacé par l’opérateur égal à ( `-eq` ).

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

L’exemple suivant écrit toutes les valeurs d’un tableau, en ignorant toute valeur inférieure à zéro.

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a>VOIR AUSSI

[about_While](about_While.md)

[about_Operators](about_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)
