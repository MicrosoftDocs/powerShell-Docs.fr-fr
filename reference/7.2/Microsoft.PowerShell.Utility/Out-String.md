---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 59e5b728604ce37f27b56ebe62e1a22d6af8a966
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "99597339"
---
# Out-String

## Synopsis
Génère des objets d’entrée sous forme de chaînes.

## Syntaxe

### NoNewLineFormatting (par défaut)

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### StreamFormatting

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## Description

L' `Out-String` applet de commande convertit les objets d’entrée en chaînes. Par défaut, `Out-String` accumule les chaînes et les retourne sous la forme d’une chaîne unique, mais vous pouvez utiliser le paramètre **Stream** pour demander `Out-String` à de retourner une ligne à la fois ou créer et tableau de chaînes. Cette applet de commande vous permet de rechercher et de manipuler la sortie de chaîne comme vous le feriez dans des interpréteurs de commandes traditionnels quand la manipulation des objets est moins pratique.

## Exemples

### Exemple 1 : récupérer la culture actuelle et convertir les données en chaînes

Cet exemple obtient les paramètres régionaux de l’utilisateur actuel et convertit les données de l’objet en chaînes.

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

La `$C` variable stocke un **Selected.SysTEM. Objet Globalization. CultureInfo** . L’objet est le résultat de l' `Get-Culture` envoi de la sortie vers le pipeline vers `Select-Object` . Le paramètre **Property** utilise un `*` caractère générique astérisque () pour spécifier que toutes les propriétés sont contenues dans l’objet.

`Out-String` utilise le paramètre **InputObject** pour spécifier l’objet **CultureInfo** stocké dans la `$C` variable. Les objets dans `$C` sont convertis en une chaîne.

> [!NOTE]
> Pour afficher le `Out-String` tableau, stockez la sortie dans une variable et utilisez un index de tableau pour afficher les éléments. Pour plus d’informations sur l’index de tableau, consultez [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).
>
> `$str = Out-String -InputObject $C -Width 100`

### Exemple 2 : utilisation d’objets

Cet exemple illustre la différence entre l'utilisation d'objets et l'utilisation de chaînes. La commande affiche un alias qui comprend le texte **GCM**, l’alias de `Get-Command` .

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

`Get-Alias` Obtient les objets **System. Management. Automation. AliasInfo** , un pour chaque alias et envoie les objets dans le pipeline. `Out-String` utilise le paramètre **Stream** pour convertir chaque objet en chaîne au lieu de concaténer tous les objets en une seule chaîne. Les objets **System. String** sont envoyés dans le pipeline et `Select-String` utilisent le paramètre **pattern** pour rechercher des correspondances pour le **GCM** de texte.

> [!NOTE]
> Si vous omettez le paramètre **Stream** , la commande affiche tous les alias car `Select-String` recherche le type de texte **GCM** dans la chaîne unique qui `Out-String` retourne.

### Exemple 3 : utilisez le paramètre Width pour empêcher la troncation.

Tandis que la sortie de `Out-String` est renvoyée à la ligne suivante, il existe des scénarios dans lesquels la sortie est tronquée par le système de mise en forme avant d’être passée à `Out-String` . Vous pouvez éviter la troncation à l’aide du paramètre **Width** .

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## PARAMETERS

### -InputObject

Spécifie les objets à écrire dans une chaîne. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

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

### -NoNewline

Supprime toutes les nouvelles lignes de la sortie générée par le formateur PowerShell. Les nouvelles lignes qui font partie des objets String sont conservées.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stream

Par défaut, `Out-String` génère une chaîne unique mise en forme comme vous le verrez dans la console, y compris les en-têtes vides ou les nouvelles lignes de fin. Le paramètre **Stream** permet `Out-String` à de sortir chaque ligne un par un. La seule exception à cela est que les chaînes multilignes. Dans ce cas, `Out-String` continue à générer la chaîne sous la forme d’une chaîne unique, multiligne.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Largeur

Spécifie le nombre de caractères dans chaque ligne de la sortie. Tous les caractères supplémentaires sont renvoyés à la ligne suivante ou tronqués en fonction de l’applet de commande Formatter utilisée. Le paramètre **Width** s’applique uniquement aux objets en cours de mise en forme. Si vous omettez ce paramètre, la largeur est déterminée par les caractéristiques du programme hôte. Dans les fenêtres terminal (console), la largeur de fenêtre active est utilisée comme valeur par défaut. Les fenêtres de la console PowerShell ont par défaut une largeur de 80 caractères lors de l’installation.

```yaml
Type: System.Int32
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

### System. Management. Automation. PSObject

Vous pouvez envoyer des objets vers le dessous du pipeline `Out-String` .

## SORTIES

### System.String

`Out-String` retourne la chaîne qu’il crée à partir de l’objet d’entrée.

## REMARQUES

Les applets de commande qui contiennent le `Out` verbe ne mettent pas en forme les objets. Les `Out` applets de commande envoient des objets au formateur pour la destination d’affichage spécifiée.

## LIENS CONNEXES

[about_Formatting](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[Out-Default](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-File](Out-File.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-GridView](Out-GridView.md)

[Out-Printer](Out-Printer.md)
