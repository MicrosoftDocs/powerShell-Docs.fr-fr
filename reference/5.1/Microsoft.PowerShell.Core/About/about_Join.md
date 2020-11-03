---
description: Décrit comment l’opérateur de jointure (-Join) combine plusieurs chaînes en une seule chaîne.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: 3e5bf4363adbded29dc58facde00f6597abeb697
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207653"
---
# <a name="about-join"></a>À propos de Join

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit comment l’opérateur de jointure (-Join) combine plusieurs chaînes en une seule chaîne.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

L’opérateur Join concatène un ensemble de chaînes en une seule chaîne. Les chaînes sont ajoutées à la chaîne résultante dans l’ordre dans lequel elles apparaissent dans la commande.

### <a name="syntax"></a>Syntaxe

Le diagramme suivant illustre la syntaxe de l’opérateur de jointure.

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a>Paramètres

String [] : spécifie une ou plusieurs chaînes à joindre.

Delimiter : spécifie un ou plusieurs caractères placés entre les chaînes concaténées. La valeur par défaut est aucun délimiteur ("").

Notes

L’opérateur de jointure unaire (-Join <String [] >) a une priorité plus élevée qu’une virgule. Par conséquent, si vous soumettez une liste de chaînes séparées par des virgules à l’opérateur de jointure unaire, seule la première chaîne (avant la première virgule) est soumise à l’opérateur de jointure.

Pour utiliser l’opérateur de jointure unaire, mettez les chaînes entre parenthèses, ou stockez les chaînes dans une variable, puis soumettez la variable à joindre.

Par exemple :

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a>Exemples

L’instruction suivante joint trois chaînes :

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

L’instruction suivante joint trois chaînes délimitées par un espace :

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

Les instructions suivantes utilisent un délimiteur de plusieurs caractères pour joindre trois chaînes :

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

L’instruction suivante joint les lignes d’une chaîne ici dans une chaîne unique. Étant donné qu’une chaîne ici est une chaîne, les lignes de la chaîne ici doivent être fractionnées avant de pouvoir être jointes. Vous pouvez utiliser cette méthode pour rattacher les chaînes dans un fichier XML qui a été enregistré dans une chaîne ici :

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a>VOIR AUSSI

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Split](about_Split.md)
