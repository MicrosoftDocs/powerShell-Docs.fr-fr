---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: de827d956e6e813e84d87bb1578ee7d596fe2f15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603902"
---
# Get-Unique

## SYNOPSIS
Retourne les éléments uniques d'une liste triée.

## SYNTAXE

### AsString (par défaut)

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### UniqueByType

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## Description

L' `Get-Unique` applet de commande compare chaque élément d’une liste triée à l’élément suivant, élimine les doublons et ne retourne qu’une seule instance de chaque élément. La liste doit être triée pour que l'applet de commande fonctionne correctement.

`Get-Unique` respecte la casse. Par conséquent, les chaînes qui diffèrent uniquement par la casse sont considérées comme uniques.

## EXEMPLES

### Exemple 1 : obtenir des mots uniques dans un fichier texte

Ces commandes recherchent le nombre de mots uniques dans un fichier texte.

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

La première commande obtient le contenu du fichier Fichier.txt. Elle convertit chaque ligne de texte en lettres minuscules, puis répartit chaque mot sur une ligne distincte au niveau de l'espace (« »). Ensuite, elle trie la liste résultante par ordre alphabétique (valeur par défaut) et utilise l' `Get-Unique` applet de commande pour éliminer les mots en double. Les résultats sont stockés dans la `$A` variable.

La deuxième commande utilise la propriété **Count** de la collection de chaînes dans `$A` pour déterminer le nombre d’éléments dans `$A` .

### Exemple 2 : récupérer des entiers uniques dans un tableau

Cette commande recherche les membres uniques de l'ensemble d'entiers.

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

La première commande utilise un tableau d’entiers tapés sur la ligne de commande, les dirige vers l' `Sort-Object` applet de commande à trier, puis les transfère vers `Get-Unique` , ce qui élimine les entrées en double.

### Exemple 3 : obtenir les types d’objets uniques dans un répertoire

Cette commande utilise l' `Get-ChildItem` applet de commande pour récupérer le contenu du répertoire local, qui comprend les fichiers et les répertoires.

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

L’opérateur de pipeline (|) envoie les résultats à l’applet de commande `Sort-Object` . L' `$_.GetType()` instruction applique la méthode **GetType** à chaque fichier ou répertoire. Trie ensuite `Sort-Object` les éléments par type. Un autre opérateur de pipeline envoie les résultats à `Get-Unique` . Le paramètre **OnType** indique `Get-Unique` à de ne retourner qu’un seul objet de chaque type.

### Exemple 4 : récupération d’un processus unique

Cette commande obtient les noms des processus qui s'exécutent sur l'ordinateur sans doublon.

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

La `Get-Process` commande obtient tous les processus sur l’ordinateur. L’opérateur de pipeline (|) passe le résultat à `Sort-Object` , qui, par défaut, trie les processus par ordre alphabétique par ProcessName. Les résultats sont dirigés vers l’applet de commande `Select-Object` , qui sélectionne uniquement les valeurs de la propriété ProcessName de chaque objet. Les résultats sont ensuite redirigés vers `Get-Unique` pour éliminer les doublons.

Le paramètre **AsString** indique `Get-Unique` à de traiter les valeurs **ProcessName** en tant que chaînes.
Sans ce paramètre, `Get-Unique` traite les valeurs **ProcessName** en tant qu’objets et ne retourne qu’une seule instance de l’objet, autrement dit, le premier nom de processus de la liste.

## PARAMETERS

### -AsString

Indique que cette applet de commande utilise les données en tant que chaîne. Sans ce paramètre, les données sont traitées comme un objet. par conséquent, lorsque vous envoyez une collection d’objets du même type à `Get-Unique` , par exemple une collection de fichiers, elle ne retourne qu’un seul (le premier). Vous pouvez utiliser ce paramètre pour rechercher les valeurs uniques des propriétés de l'objet, telles que les noms de fichier uniques.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie l’entrée pour `Get-Unique` . Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.

Cette applet de commande traite l’entrée envoyée en utilisant **InputObject** comme collection. Il n’énumère pas les éléments individuels dans la collection. Étant donné que la collection est un élément unique, l’entrée envoyée à l’aide d' **InputObject** est toujours retournée inchangée.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OnType

Indique que cette applet de commande ne retourne qu’un seul objet de chaque type.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger tout type d’objet vers `Get-Unique` .

## SORTIES

### System. Management. Automation. PSObject

Le type d’objet `Get-Unique` retourné est déterminé par l’entrée.

## REMARQUES

Vous pouvez également faire référence à `Get-Unique` par son alias intégré, `gu` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Pour trier une liste, utilisez Sort-Object. Vous pouvez également utiliser le paramètre **unique** de `Sort-Object` pour rechercher les éléments uniques dans une liste.

## LIENS CONNEXES

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

