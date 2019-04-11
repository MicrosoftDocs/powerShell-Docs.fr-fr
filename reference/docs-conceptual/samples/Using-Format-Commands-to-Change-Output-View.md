---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation des commandes de mise en forme pour modifier l’affichage d’une sortie
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: fba37b1d0479bf605d8f2171da27cd1bceb9976e
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293042"
---
# <a name="using-format-commands-to-change-output-view"></a>Utilisation des commandes de mise en forme pour modifier l’affichage d’une sortie

Windows PowerShell dispose d’un ensemble d’applets de commande qui vous permettent de contrôler les propriétés affichées pour des objets spécifiques. Les noms de toutes les applets de commande commencent par le verbe **Format**. Elles vous permettent de sélectionner une ou plusieurs propriétés à afficher.

Les applets de commande **Format** sont **Format-Wide**, **Format-List**, **Format-Table**, et **Format-Custom**. Ce guide décrit uniquement les applets de commande **Format-Wide**, **Format-List** et **Format-Table**.

Chaque applet de commande Format a des propriétés par défaut qui sont utilisées si vous ne spécifiez pas de propriétés spécifiques à afficher. Chaque applet de commande utilise également le même nom de paramètre, **Property**, pour spécifier les propriétés à afficher. Étant donné que l’applet de commande **Format-Wide** n’affiche qu’une seule propriété, son paramètre **Property** n’accepte qu’une seule valeur, mais les paramètres de propriété des applets de commande **Format-List** et **Format-Table** acceptent une liste de noms de propriétés.

Si vous utilisez la commande **Get-Process -Name powershell** avec deux instances de Windows PowerShell en cours d’exécution, vous obtenez une sortie ressemblant à ceci :

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

Dans le reste de cette section, nous allons examiner comment utiliser les applets de commande **Format** pour modifier le mode d’affichage de la sortie de cette commande.

## <a name="using-format-wide-for-single-item-output"></a>Utilisation de l’applet de commande Format-Wide pour une sortie d’élément unique

Par défaut, l’applet de commande `Format-Wide` affiche uniquement la propriété par défaut d’un objet.
Les informations associées à chaque objet s’affichent dans une seule colonne :

```powershell
Get-Command -Verb Format | Format-Wide
```

```output
Format-Custom                          Format-Hex
Format-List                            Format-Table
Format-Wide
```

Vous pouvez également spécifier une propriété autre que celle par défaut :

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```output
Custom                                 Hex
List                                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Contrôle de l’affichage de Format-Wide avec une colonne

La cmdlet `Format-Wide` ne permet d’afficher qu’une seule propriété à la fois.
Cela rend utile l’affichage de listes simples qui ne présentent qu’un seul élément par ligne.
Pour obtenir une liste simple, définissez la valeur du paramètre **Column** sur 1 en tapant ce qui suit :

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

## <a name="using-format-list-for-a-list-view"></a>Utilisation de l’applet de commande Format-List pour un Affichage Liste

L’applet de commende **Format-List** affiche un objet sous la forme d’une liste, chaque propriété étant étiquetée et affichée sur une ligne distincte :

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

Vous pouvez spécifier autant de propriétés que vous le souhaitez :

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Obtention d’informations détaillées en utilisant l’applet de commande Format-List avec des caractères génériques

L’applet de commande **Format-List** permet d’utiliser un caractère générique en tant que la valeur pour son paramètre **Property**. Cela permet d’afficher des informations détaillées. Souvent, des objets incluent plus d’informations que nécessaire. C’est pourquoi, par défaut, Windows PowerShell n’affiche pas les valeurs de toutes les propriétés. Pour afficher toutes les propriétés d’un objet, utilisez la commande **Format-List -Property \&#42;**. La commande suivante génère plus de 60 lignes de sortie pour un seul processus :

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Bien que la commande **Format-List** soit utile pour afficher des détails, si vous souhaitez une vue d’ensemble de la sortie incluant de nombreux d’éléments, une simple vue tabulaire est souvent plus utile.

## <a name="using-format-table-for-tabular-output"></a>Utilisation de l’applet de commande Format-Table pour une sortie tabulaire

Si vous utilisez l’applet de commande **Format-Table** sans nom de propriété spécifié pour mettre en forme la sortie de la commande **Get-Process**, vous obtenez exactement la même sortie que sans effectuer de mise en forme. La raison en est que les processus sont généralement affichés dans un format tabulaire, tout comme la plupart des objets Windows PowerShell.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

### <a name="improving-format-table-output-autosize"></a>Amélioration de la sortie de l’applet de commande Format-Table (AutoSize)

Bien qu’une vue tabulaire soit utile pour afficher de nombreuses informations comparables, elle peut être difficile à interpréter si l’affichage est trop étroit pour les données. Par exemple, si vous essayez d’afficher le chemin d’accès au processus, l’ID, le nom et la société, vous obtenez une sortie tronquée pour les colonnes du chemin d’accès et de la société :

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Si vous spécifiez le paramètre **AutoSize** lorsque vous exécutez la commande **Format-Table**, Windows PowerShell calcule les largeurs de colonne en fonction des données réelles à afficher. Cela rend la colonne du **chemin d’accès** lisible, mais la colonne de la société reste tronquée :

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

L’applet de commande **Format-Table** peut toujours tronquer des données, mais elle ne le fait qu’à la fin de l’écran. Les propriétés, à l’exception de la dernière affichée, disposent de la taille nécessaire pour que leur élément de données le plus long s’affiche correctement. Vous pouvez constater que nom de la société est visible, mais que le chemin d’accès est tronqué si vous permutez les emplacements de **Path** et de **Company** dans la liste de valeurs **Property** :

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

La commande **Format-Table** suppose que, plus une propriété est proche du début de la liste de propriétés, plus elle est importante. Elle tente donc d’afficher entièrement les propriétés les plus proches du début. Si la commande **Format-Table** ne peut pas afficher toutes les propriétés, elle supprime certaines colonnes de l’affichage et génère un avertissement. Vous pouvez observer ce comportement si vous faites de **Name** la dernière propriété de la liste :

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

Dans la sortie ci-dessus, la colonne ID est tronquée pour qu’elle tienne dans la liste, et les en-têtes de colonne sont empilés. Une redimensionnement automatique les colonnes ne produit pas toujours le résultat souhaité.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Retour automatique à la ligne de la sortie de l’applet de commande Format-Table dans les colonnes (Wrap)

Vous pouvez forcer le retour automatique à la ligne des données longues retournées par l’applet de commande **Format-Table** dans la colonne d’affichage en utilisant le paramètre **Wrap**. L’utilisation du paramètre **Wrap** isolément ne produit pas nécessairement le résultat attendu car, si vous ne spécifiez pas **AutoSize**, les paramètres par défaut sont utilisés :

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Un avantage de l’utilisation du paramètre **Wrap** isolément est qu’il ne ralentit pas beaucoup le traitement. Si vous générez une liste récursive des fichiers d’un système d’annuaire volumineux, l’affichage des premiers éléments de sortie peut prendre beaucoup de temps et monopoliser beaucoup de mémoire si vous utilisez **AutoSize**.

Si vous n’êtes pas inquiet de la charge du système, **AutoSize** fonctionne bien avec le paramètre **Wrap**. Les colonnes initiales disposent toujours de la largeur nécessaire pour afficher les éléments sur une seule ligne, comme lorsque vous spécifiez **AutoSize** sans le paramètre **Wrap**. La seule différence est que la dernière colonne contient des retours à la ligne automatiques si nécessaire :

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Il se peut que certaines colonnes ne s’affichent pas si vous spécifiez d’abord les colonnes plus larges. Il est donc plus sûr de spécifier en premier les éléments de données les plus petits. Dans l’exemple suivant, nous spécifions d’abord l’élément de chemin d’accès très large et, même avec un retour automatique à la ligne, nous perdons la dernière colonne **Name** :

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

### <a name="organizing-table-output--groupby"></a>Organisation de la sortie de table (-GroupBy)

Un autre paramètre utile pour le contrôle de la sortie tabulaire est **GroupBy**. Des listes tabulaires plus longues en particulier peuvent être difficiles à comparer. Le paramètre **GroupBy** groupe la sortie en fonction d’une valeur de propriété. Par exemple, nous pouvons grouper des processus par société pour faciliter l’inspection, en omettant la valeur de la société de la liste des propriétés :

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```