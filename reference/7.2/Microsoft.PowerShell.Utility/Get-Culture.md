---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: dc49f153adc22b7c2c943a4cc529ac155561228a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595922"
---
# Get-Culture

## SYNOPSIS
Obtient la culture actuelle définie dans le système d'exploitation.

## SYNTAXE

### CurrentCulture (par défaut)

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### Nom

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### ListAvailable

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## Description

L' `Get-Culture` applet de commande obtient des informations sur les paramètres de culture actuels. Ces informations incluent celles sur les paramètres de langue actuels du système, tels que la disposition du clavier et le format d'affichage d'éléments comme les nombres, les devises et les dates.

Vous pouvez également utiliser l' `Get-UICulture` applet de commande, qui obtient la culture d’interface utilisateur actuelle sur le système, et l’applet de commande [Set-culture](/powershell/module/international/set-culture) dans le module international. La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages.

## EXEMPLES

### Exemple 1 : récupérer les paramètres de culture

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

Cette commande affiche des informations sur les paramètres régionaux de l'ordinateur.

### Exemple 2 : mettre en forme les propriétés d’un objet culture

```powershell
PS C:\> $C = Get-Culture
PS C:\> $C | Format-List -Property *
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
CompareInfo                    : CompareInfo - 1033
TextInfo                       : TextInfo - 1033
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar, System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False

PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False

PS C:\> $C.DateTimeFormat
AMDesignator                     : AM
Calendar                         : System.Globalization.GregorianCalendar
DateSeparator                    : /
FirstDayOfWeek                   : Sunday
CalendarWeekRule                 : FirstDay
FullDateTimePattern              : dddd, MMMM dd, yyyy h:mm:ss tt
LongDatePattern                  : dddd, MMMM dd, yyyy
LongTimePattern                  : h:mm:ss tt
MonthDayPattern                  : MMMM dd
PMDesignator                     : PM
RFC1123Pattern                   : ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
ShortDatePattern                 : M/d/yyyy
ShortTimePattern                 : h:mm tt
SortableDateTimePattern          : yyyy'-'MM'-'dd'T'HH':'mm':'ss
TimeSeparator                    : :
UniversalSortableDateTimePattern : yyyy'-'MM'-'dd HH':'mm':'ss'Z'
YearMonthPattern                 : MMMM, yyyy
AbbreviatedDayNames              : {Sun, Mon, Tue, Wed...}
ShortestDayNames                 : {Su, Mo, Tu, We...}
DayNames                         : {Sunday, Monday, Tuesday, Wednesday...}
AbbreviatedMonthNames            : {Jan, Feb, Mar, Apr...}
MonthNames                       : {January, February, March, April...}
IsReadOnly                       : False
NativeCalendarName               : Gregorian Calendar
AbbreviatedMonthGenitiveNames    : {Jan, Feb, Mar, Apr...}
MonthGenitiveNames               : {January, February, March, April...}

PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

Cet exemple illustre la vaste quantité de données dans l'objet de culture. Il montre comment afficher les propriétés et les sous-propriétés de l'objet.

La première commande utilise l' `Get-Culture` applet de commande pour récupérer les paramètres de culture actuels sur l’ordinateur.
Elle stocke l’objet de culture résultant dans la `$C` variable.

La deuxième commande affiche toutes les propriétés de l'objet de culture. Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet de culture dans `$C` l’applet de commande `Format-List` . Elle utilise le paramètre **Property** pour afficher toutes les `*` Propriétés () de l’objet. Cette commande peut être abrégée comme `$c | fl *` .

Les commandes restantes explorent les propriétés de l'objet de culture à l'aide de la notation par point pour afficher les valeurs des propriétés de l'objet. Vous pouvez utiliser cette notation pour afficher la valeur d'une propriété de l'objet.

La troisième commande utilise la notation par points pour afficher la valeur de la propriété **Calendar** de l’objet culture.

La quatrième commande utilise la notation par points pour afficher la valeur de la propriété **DataTimeFormat** de l’objet culture.

Plusieurs propriétés de l'objet ont des propriétés. La cinquième commande utilise la notation par points pour afficher la valeur de la propriété **FirstDayOfWeek** de la propriété **DateTimeFormat** .

### Exemple 3 : obtenir une culture spécifique

Obtenir l’objet CultureInfo pour le français en France.

```powershell
Get-Culture -Name fr-FR
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1036             fr-FR            French (France)
```

## PARAMETERS

### -ListAvailable

Récupère toutes les cultures prises en charge par le système d’exploitation actuel.

Ce paramètre a été introduit dans PowerShell 6,2.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Récupérez une culture spécifique en fonction du nom.

Ce paramètre a été introduit dans PowerShell 6,2.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoUserOverrides

Ignorer les modifications utilisateur pour la culture actuelle.

Ce paramètre a été introduit dans PowerShell 6,2.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CurrentCulture, Name
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

### None

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Globalization. CultureInfo

`Get-Culture` retourne un objet qui représente la culture actuelle.

## REMARQUES

Vous pouvez également utiliser les `$PsCulture` `$PsUICulture` variables et. La `$PsCulture` variable stocke le nom de la culture actuelle et la `$PsUICulture` variable stocke le nom de la culture d’interface utilisateur actuelle.

## LIENS CONNEXES

[Définir-culture](/powershell/module/international/set-culture)

[Get-UICulture](Get-UICulture.md)
