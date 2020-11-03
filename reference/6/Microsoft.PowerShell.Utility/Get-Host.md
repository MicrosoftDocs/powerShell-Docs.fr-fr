---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: 15305de9512a45a92242c283f60f6fd36b80fbe3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200786"
---
# Get-Host

## SYNOPSIS
Obtient un objet qui représente le programme hôte actuel.

## SYNTAX

```
Get-Host [<CommonParameters>]
```

## Description

L' `Get-Host` applet de commande obtient un objet qui représente le programme qui héberge Windows PowerShell.

L'affichage par défaut inclut le numéro de version de Windows PowerShell, ainsi que les paramètres de région et de langue actuels que l'hôte utilise. Toutefois, l'objet hôte contient une mine d'informations, dont notamment des informations détaillées sur la version de Windows PowerShell en cours d'exécution, ainsi que la culture actuelle et la culture d'interface utilisateur de Windows PowerShell. Vous pouvez également utiliser cette applet de commande pour personnaliser les fonctionnalités de l’interface utilisateur du programme hôte, telles que les couleurs de texte et d’arrière-plan.

## EXEMPLES

### Exemple 1 : obtenir des informations sur l’hôte de la console PowerShell

```
PS C:\> Get-Host
Name             : ConsoleHost
Version          : 2.0
InstanceId       : e4e0ab54-cc5e-4261-9117-4081f20ce7a2
UI               : System.Management.Automation.Internal.Host.InternalHostUserInterface
CurrentCulture   : en-US
CurrentUICulture : en-US
PrivateData      : Microsoft.PowerShell.ConsoleHost+ConsoleColorProxy
IsRunspacePushed : False
Runspace         : System.Management.Automation.Runspaces.LocalRunspace
```

Cette commande affiche des informations sur la console Windows PowerShell, qui est le programme hôte actuel pour Windows PowerShell dans cet exemple. Elle inclut le nom de l'hôte, la version de Windows PowerShell qui s'exécute sur l'hôte, ainsi que la culture actuelle et la culture d'interface utilisateur.

Les propriétés Version, UI, CurrentCulture, CurrentUICulture, PrivateData, et Runspace contiennent toutes un objet doté de propriétés très utiles. Les exemples suivants illustrent ces propriétés.

### Exemple 2 : redimensionner la fenêtre PowerShell

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

Cette commande redimensionne la fenêtre Windows PowerShell à 10 x 10 pixels.

### Exemple 3 : obtenir la version de PowerShell pour l’hôte

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

Cette commande obtient des informations détaillées sur la version de Windows PowerShell en cours d'exécution sur l'hôte.
Vous pouvez afficher, mais pas modifier, ces valeurs.

La propriété version de `Get-Host` contient un objet **System. version** . Cette commande utilise un opérateur de pipeline (|) pour envoyer l’objet de version à l’applet de commande `Format-List` . La `Format-List` commande utilise le paramètre *Property* avec la valeur All (*) pour afficher toutes les propriétés et les valeurs de propriété de l’objet version.

### Exemple 4 : obtenir la culture actuelle pour l’hôte

```powershell
PS C:\> (Get-Host).CurrentCulture | Format-List -Property *
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
```

Cette commande obtient des informations détaillées sur la culture actuelle définie pour Windows PowerShell et en cours d'exécution sur l'hôte. Il s’agit des mêmes informations que celles retournées par l’applet de commande `Get-Culture` .

De même, la propriété **CurrentUICulture** retourne le même objet que celui `Get-UICulture` retourné par.

La propriété **CurrentCulture** de l’objet hôte contient un objet **System. Globalization. CultureInfo** . Cette commande utilise un opérateur de pipeline (|) pour envoyer l’objet **CultureInfo** à l’applet de commande `Format-List` . La `Format-List` commande utilise le paramètre *Property* avec la valeur All (*) pour afficher toutes les propriétés et les valeurs de propriété de l’objet **CultureInfo** .

### Exemple 5 : obtenir DateTimeFormat pour la culture actuelle

```powershell
PS C:\> (Get-Host).CurrentCulture.DateTimeFormat | Format-List -Property *
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
```

Cette commande retourne des informations détaillées sur le DateTimeFormat de la culture actuelle, en cours d'utilisation pour Windows PowerShell.

La propriété **CurrentCulture** de l’objet hôte contient un objet **CultureInfo** qui, à son tour, a de nombreuses propriétés utiles. Parmi celles-ci, la propriété **DateTimeFormat** contient un objet **DateTimeFormatInfo** avec de nombreuses propriétés utiles.

Pour rechercher le type d’un objet stocké dans une propriété d’objet, utilisez l' `Get-Member` applet de commande. Pour afficher les valeurs de propriété de l’objet, utilisez l’applet de commande `Format-List` .

### Exemple 6 : obtenir la propriété RawUI pour l’hôte

```
PS C:\> (Get-Host).UI.RawUI | Format-List -Property *
ForegroundColor       : DarkYellow
BackgroundColor       : DarkBlue
CursorPosition        : 0,390
WindowPosition        : 0,341
CursorSize            : 25
BufferSize            : 120,3000
WindowSize            : 120,50
MaxWindowSize         : 120,81
MaxPhysicalWindowSize : 182,81
KeyAvailable          : False
WindowTitle           : Windows PowerShell 2.0 (04/11/2008 00:08:14)
```

Cette commande affiche les propriétés de la propriété **rawui** de l’objet hôte. En modifiant ces valeurs, vous pouvez modifier l'apparence du programme hôte.

### Exemple 7 : définir la couleur d’arrière-plan de la console PowerShell

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

Ces commandes définissent en noir la couleur d'arrière-plan de la console Windows PowerShell. La commande **CLS** est un alias pour la `Clear-Host` fonction, ce qui efface l’écran et remplace l’écran entier par la nouvelle couleur.

Cette modification est effective uniquement dans la session active. Pour modifier la couleur d'arrière-plan de la console pour toutes les sessions, ajoutez la commande à votre profil Windows PowerShell.

### Exemple 8 : définir la couleur d’arrière-plan des messages d’erreur

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

Cette commande définit en blanc la couleur d'arrière-plan des messages d'erreur.

Cette commande utilise la `$Host` variable automatique, qui contient l’objet hôte du programme hôte actuel. `Get-Host` retourne le même objet que celui qui `$Host` contient, de sorte que vous pouvez les utiliser de manière interchangeable.

Cette commande utilise la propriété **PrivateData** de `$Host` comme propriété ErrorBackgroundColor. Pour afficher toutes les propriétés de l’objet dans le `$Host` . Propriété PrivateData, tapez `$host.privatedata | format-list *` .

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. Internal. Host. InternalHost

`Get-Host` retourne un objet **System. Management. Automation. Internal. Host. InternalHost** .

## REMARQUES

La `$Host` variable automatique contient le même objet que celui `Get-Host` retourné par, et vous pouvez l’utiliser de la même façon. De même, les `$PSCulture` `$PSUICulture` variables automatiques et contiennent les mêmes objets que les propriétés CurrentCulture et CurrentUICulture de l’objet hôte. Vous pouvez utiliser ces fonctionnalités de manière interchangeable.

Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

## LIENS CONNEXES

[Clear-Host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Read-Host](Read-Host.md)

[Write-Host](Write-Host.md)
