---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: d7e9ebd56db3ad9de2bfbcec62f73f1f8c0e2eaa
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200818"
---
# Get-Culture

## SYNOPSIS
Obtient la culture actuelle définie dans le système d'exploitation.

## SYNTAX

```
Get-Culture [<CommonParameters>]
```

## Description
L’applet **de commande obtenir-culture** obtient des informations sur les paramètres de culture actuels.
Ces informations incluent celles sur les paramètres de langue actuels du système, tels que la disposition du clavier et le format d'affichage d'éléments comme les nombres, les devises et les dates.

Vous pouvez également utiliser l’applet de commande Get-UICulture, qui obtient la culture d’interface utilisateur actuelle sur le système, et l’applet de commande [Set-culture](https://go.microsoft.com/fwlink/?LinkID=242258) dans le module international.
La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages.

## EXEMPLES

### Exemple 1 : récupérer les paramètres de culture

```
PS C:\> Get-Culture
```

Cette commande affiche des informations sur les paramètres régionaux de l'ordinateur.

### Exemple 2 : mettre en forme les propriétés d’un objet culture

```
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
IsReadOnly                     : False PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False PS C:\> $C.DateTimeFormat
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
MonthGenitiveNames               : {January, February, March, April...} PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

Cet exemple illustre la vaste quantité de données dans l'objet de culture.
Il montre comment afficher les propriétés et les sous-propriétés de l'objet.

La première commande utilise l’applet de commande **obten-culture** pour récupérer les paramètres de culture actuels sur l’ordinateur.
Elle stocke l’objet de culture résultant dans la variable $C.

La deuxième commande affiche toutes les propriétés de l'objet de culture.
Elle utilise un opérateur de pipeline (|) pour envoyer l’objet de culture dans $C à l’applet de commande Format-List.
Elle utilise le paramètre *Property* pour afficher toutes les propriétés (*) de l’objet.
Cette commande peut être abrégée comme `$c | fl *` .

Les commandes restantes explorent les propriétés de l'objet de culture à l'aide de la notation par point pour afficher les valeurs des propriétés de l'objet.
Vous pouvez utiliser cette notation pour afficher la valeur d'une propriété de l'objet.

La troisième commande utilise la notation par point pour afficher la valeur de la propriété Calendar de l'objet de culture.

La troisième commande utilise la notation par point pour afficher la valeur de la propriété DataTimeFormat de l'objet de culture.

Plusieurs propriétés de l'objet ont des propriétés.
La cinquième commande utilise la notation par point pour afficher la valeur de la propriété FirstDayOfWeek de la propriété DateTimeFormat.

## PARAMETERS

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Globalization. CultureInfo
L’expression **obtient-culture** retourne un objet qui représente la culture actuelle.

## REMARQUES

* Vous pouvez également utiliser les variables $PsCulture et $PsUICulture. La variable $PsCulture stocke le nom de la culture actuelle et la variable $PsUICulture le nom de la culture d'interface utilisateur actuelle.

*

## LIENS CONNEXES

[Définir-culture](/powershell/module/internationalcmdlets/set-culture)

[Get-UICulture](Get-UICulture.md)
