---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: d6707a9f5c54b736d0b917d453416ccdb0850baa
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "93206258"
---
# Write-Host

## SYNOPSIS

Écrit la sortie personnalisée sur un hôte.

## SYNTAX

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## Description

L' `Write-Host` objectif principal de l’applet de commande est de produire pour la sortie-(hôte)-affichage uniquement, par exemple l’impression d’un texte coloré comme lorsque vous invitez l’utilisateur à entrer des données conjointement avec l' [hôte de lecture](Read-Host.md).
`Write-Host` utilise la méthode [ToString ()](/dotnet/api/system.object.tostring) pour écrire la sortie. En revanche, pour sortir des données dans le pipeline, utilisez la sortie [Write-Output](Write-Output.md) ou implicite.

Vous pouvez spécifier la couleur du texte à l’aide du `ForegroundColor` paramètre, et vous pouvez spécifier la couleur d’arrière-plan à l’aide du `BackgroundColor` paramètre. Le paramètre Separator vous permet de spécifier une chaîne à utiliser pour séparer les objets affichés. Le résultat donné dépend du programme qui héberge PowerShell.

> [!NOTE]
> À compter de Windows PowerShell 5,0, `Write-Host` est un wrapper de `Write-Information` ce qui vous permet d’utiliser `Write-Host` pour émettre une sortie vers le flux d’informations. Cela permet la **capture** ou la **suppression** des données écrites à l’aide de `Write-Host` tout en préservant la compatibilité descendante.
>
> La `$InformationPreference` variable de préférence et le `InformationAction` paramètre commun n’affectent pas les `Write-Host` messages. L’exception à cette règle est `-InformationAction Ignore` , qui supprime effectivement la `Write-Host` sortie. (Voir « Example 5 »)

## EXEMPLES

### Exemple 1 : écrire dans la console sans ajouter de nouvelle ligne

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

Cette commande affiche la chaîne « no NewLine test » avec le `NoNewline` paramètre.

Une deuxième chaîne est écrite, mais elle finit sur la même ligne que la première en raison de l’absence de saut de ligne qui sépare les chaînes.

### Exemple 2 : écrire dans la console et inclure un séparateur

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

Cette commande affiche les nombres pairs de 2 à 12. Le paramètre **separator** est utilisé pour ajouter la chaîne `, +2= ` (virgule, espace, `+` , `2` , `=` , espace).

### Exemple 3 : écrire avec des couleurs de texte et d’arrière-plan différentes

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

Cette commande affiche les nombres pairs de 2 à 12. Elle utilise le `ForegroundColor` paramètre pour générer un texte vert foncé et le `BackgroundColor` paramètre pour afficher un arrière-plan blanc.

### Exemple 4 : écrire avec des couleurs de texte et d’arrière-plan différentes

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

Cette commande affiche la chaîne "Red on white text." Le texte est rouge, comme défini par le `ForegroundColor` paramètre. L’arrière-plan est blanc, comme défini par le `BackgroundColor` paramètre.

### Exemple 5 : supprimer la sortie de Write-Host

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

Ces commandes suppriment efficacement la sortie de l’applet de commande `Write-Host` . La première utilise le `InformationAction` paramètre avec la `Ignore` valeur pour supprimer la sortie du flux d’informations.
Le deuxième exemple redirige le flux d’informations de la commande vers la `$null` variable et le supprime par conséquent.

## PARAMETERS

### -BackgroundColor

Spécifie la couleur d'arrière-plan. Il n'y a pas de valeur par défaut. Les valeurs valides pour ce paramètre sont :

- Noir
- DarkBlue
- DarkGreen
- DarkCyan
- DarkRed
- DarkMagenta
- DarkYellow
- Gris
- DarkGray
- Bleu
- Vert
- Cyan
- Rouge
- Magenta
- Jaune
- White

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForegroundColor

Spécifie la couleur du texte. Il n'y a pas de valeur par défaut. Les valeurs valides pour ce paramètre sont :

- Noir
- DarkBlue
- DarkGreen
- DarkCyan
- DarkRed
- DarkMagenta
- DarkYellow
- Gris
- DarkGray
- Bleu
- Vert
- Cyan
- Rouge
- Magenta
- Jaune
- White

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewline

Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie. Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie. Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Object

Objets à afficher dans l’hôte.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Séparateur

Spécifie une chaîne de séparation à insérer entre les objets affichés par l’hôte.

```yaml
Type: System.Object
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

Vous pouvez diriger les objets à écrire vers l'hôte.

## SORTIES

### Aucun

`Write-Host` envoie les objets à l’hôte. Aucun objet n'est retourné. Toutefois, l’hôte affiche les objets qui `Write-Host` lui sont envoyés.

## REMARQUES

- Lors de l’écriture d’une collection sur l’hôte, les éléments de la collection sont imprimés sur la même ligne, séparés par un espace. Vous pouvez le remplacer par le paramètre **separator** .

- Les types de données non primitifs, tels que les objets avec des propriétés, peuvent entraîner des résultats inattendus et ne pas fournir une sortie significative. Par exemple, `Write-Host @{a = 1; b = 2}` s’imprimera `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` sur l’hôte.

## LIENS CONNEXES

[Clear-Host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Write-Debug](Write-Debug.md)

[Écriture-erreur](Write-Error.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
