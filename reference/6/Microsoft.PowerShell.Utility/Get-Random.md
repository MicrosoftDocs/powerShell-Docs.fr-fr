---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 3c1f8d136cf98a703a1eb31d73e226df5d8ef56b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204610"
---
# Get-Random

## SYNOPSIS
Obtient un nombre aléatoire ou sélectionne de façon aléatoire des objets d'une collection.

## SYNTAX

### RandomNumberParameterSet (par défaut)

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [<CommonParameters>]
```

### RandomListItemParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## Description

L' `Get-Random` applet de commande obtient un nombre sélectionné de façon aléatoire. Si vous envoyez une collection d’objets à `Get-Random` , elle obtient un ou plusieurs objets sélectionnés de façon aléatoire dans la collection.

Sans paramètres ou en entrée, une `Get-Random` commande retourne un entier non signé 32 bits sélectionné de façon aléatoire entre 0 (zéro) et **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).

Vous pouvez utiliser les paramètres de `Get-Random` pour spécifier un nombre de départ, des valeurs minimales et maximales, ainsi que le nombre d’objets retournés à partir d’une collection soumise.

## EXEMPLES

### Exemple 1 : obtenir un entier aléatoire

Cette commande obtient un entier aléatoire compris entre 0 (zéro) et **Int32. MaxValue** .

```powershell
Get-Random
```

```Output
3951433
```

### Exemple 2 : obtenir un entier aléatoire compris entre 0 et 99

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### Exemple 3 : obtenir un entier aléatoire compris entre-100 et 99

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### Exemple 4 : obtenir un nombre à virgule flottante aléatoire

Cette commande obtient un nombre à virgule flottante aléatoire supérieur ou égal à 10,7 et inférieur à 20,92.

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### Exemple 5 : obtenir un entier aléatoire à partir d’un tableau

Cette commande obtient un nombre sélectionné de façon aléatoire dans le tableau spécifié.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### Exemple 6 : récupération de plusieurs entiers aléatoires à partir d’un tableau

Cette commande obtient trois nombres sélectionnés de façon aléatoire dans un ordre aléatoire à partir d’un tableau.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### Exemple 7 : randomiser une collection entière

Cette commande retourne la collection entière dans un ordre aléatoire.

La valeur du paramètre **Count** est la propriété statique **MaxValue** des entiers.

Pour retourner une collection entière dans un ordre aléatoire, entrez un nombre qui est supérieur ou égal au nombre d'objets de la collection.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count ([int]::MaxValue)
```

```Output
2
3
5
1
8
13
```

### Exemple 8 : obtenir une valeur non numérique aléatoire

Cette commande retourne une valeur aléatoire depuis une collection non numérique.

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### Exemple 9 : utiliser le paramètre SetSeed

Cet exemple montre l'utilisation du paramètre **SetSeed** .

Comme **setseed** produit un comportement non aléatoire, il est généralement utilisé uniquement pour reproduire les résultats, par exemple lors du débogage ou de l’analyse d’un script.

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### Exemple 10 : récupération de fichiers aléatoires

Ces commandes obtiennent un exemple sélectionné de manière aléatoire de fichiers 50 à partir du `C:` lecteur de l’ordinateur local.

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### Exemple 11 : roulements de dés équitables

Cet exemple annule une matrice de 1200 fois et compte les résultats. La première commande `For-EachObject` répète l’appel à `Get-Random` à partir des numéros dirigés (1-6). Les résultats sont regroupés par valeur avec `Group-Object` et mis en forme en tant que table avec `Select-Object` .

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

## PARAMETERS

### -Nombre

Spécifie le nombre d’objets ou de nombres aléatoires à retourner. La valeur par défaut est 1.

Lorsqu' `InputObject` il est utilisé avec, si la valeur de **Count** dépasse le nombre d’objets de la collection, `Get-Random` retourne tous les objets dans l’ordre aléatoire.

```yaml
Type: System.Int32
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie une collection d'objets. `Get-Random` obtient des objets sélectionnés aléatoirement dans l’ordre aléatoire à partir de la collection jusqu’au nombre spécifié par **Count** . Entrez les objets, une variable contenant les objets, ou bien tapez une commande ou une expression qui obtient les objets. Vous pouvez également diriger une collection d’objets vers `Get-Random` .

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Maximum

Spécifie une valeur maximale pour le nombre aléatoire. `Get-Random` retourne une valeur inférieure à la valeur maximale (non égal à). Entrez un entier, un nombre à virgule flottante double précision ou un objet qui peut être converti en entier ou double, par exemple une chaîne numérique (« 100 »).

La valeur de **Maximum** doit être supérieure à (différente de) la valeur de **Minimum** . Si la valeur de **maximum** ou **minimum** est un nombre à virgule flottante, `Get-Random` retourne un nombre à virgule flottante sélectionné de façon aléatoire.

Sur un ordinateur 64 bits, si la valeur **minimale** est un entier 32 bits, la valeur par défaut de **maximum** est **Int32. MaxValue** .

Si la valeur de **minimum** est un double (un nombre à virgule flottante), la valeur par défaut de **maximum** est **double. MaxValue** . Dans le cas contraire, la valeur par défaut est **Int32. MaxValue** .

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum

Spécifie une valeur minimale pour le nombre aléatoire. Entrez un entier, un nombre à virgule flottante double précision ou un objet qui peut être converti en entier ou double, par exemple une chaîne numérique (« 100 »). La valeur par défaut est 0 (zéro).

La valeur de **Minimum** doit être inférieure à (différente de) la valeur de **Maximum** . Si la valeur de **maximum** ou **minimum** est un nombre à virgule flottante, `Get-Random` retourne un nombre à virgule flottante sélectionné de façon aléatoire.

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SetSeed

Spécifie une valeur de départ pour le générateur de nombres aléatoires. Cette valeur de départ est utilisée pour la commande actuelle et pour toutes les `Get-Random` commandes suivantes dans la session active jusqu’à ce que vous réutilisiez **setseed** ou fermiez la session. Vous ne pouvez pas réinitialiser la valeur de départ à sa valeur par défaut.

Le paramètre **setseed** n’est pas obligatoire. Par défaut, `Get-Random` utilise la méthode [RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator) pour générer une valeur de départ. Comme **setseed** entraîne un comportement non aléatoire, il est généralement utilisé uniquement lors de la tentative de reproduction du comportement, par exemple lors du débogage ou de l’analyse d’un script qui comprend des `Get-Random` commandes.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
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

### System.Object

Vous pouvez diriger un ou plusieurs objets. `Get-Random` sélectionne les valeurs de façon aléatoire à partir des objets dirigés.

## SORTIES

### System. Int32, System. Int64, System. double

`Get-Random` retourne un entier ou un nombre à virgule flottante, ou un objet sélectionné de façon aléatoire à partir d’une collection soumise.

## REMARQUES

`Get-Random` définit une valeur de départ par défaut pour chaque session en fonction de l’horloge système au démarrage de la session.

`Get-Random` ne retourne pas toujours le même type de données que la valeur d’entrée. Le tableau suivant indique le type de sortie pour chacun des types d’entrée numériques.

| Type d’entrée | Type de sortie |
| :--------: | :---------: |
|   SByte    |   Double    |
|    Byte    |   Double    |
|   Int16    |   Double    |
|   UInt16   |   Double    |
|   Int32    |    Int32    |
|   UInt32   |   Double    |
|   Int64    |    Int64    |
|   UInt64   |   Double    |
|   Double   |   Double    |
|   Single   |   Double    |

À compter de Windows PowerShell 3,0, `Get-Random` prend en charge les entiers 64 bits. Dans Windows PowerShell 2,0, toutes les valeurs sont converties en **System. Int32** .

## LIENS CONNEXES
