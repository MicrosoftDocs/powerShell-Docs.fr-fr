---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: 00f27b6b50c2c34be21e1c6f6bbef186243660aa
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204645"
---
# <span data-ttu-id="646f3-103">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="646f3-103">Get-Culture</span></span>

## <span data-ttu-id="646f3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="646f3-104">SYNOPSIS</span></span>
<span data-ttu-id="646f3-105">Obtient la culture actuelle définie dans le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="646f3-105">Gets the current culture set in the operating system.</span></span>

## <span data-ttu-id="646f3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="646f3-106">SYNTAX</span></span>

### <span data-ttu-id="646f3-107">CurrentCulture (par défaut)</span><span class="sxs-lookup"><span data-stu-id="646f3-107">CurrentCulture (Default)</span></span>

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="646f3-108">Nom</span><span class="sxs-lookup"><span data-stu-id="646f3-108">Name</span></span>

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="646f3-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="646f3-109">ListAvailable</span></span>

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="646f3-110">Description</span><span class="sxs-lookup"><span data-stu-id="646f3-110">DESCRIPTION</span></span>

<span data-ttu-id="646f3-111">L' `Get-Culture` applet de commande obtient des informations sur les paramètres de culture actuels.</span><span class="sxs-lookup"><span data-stu-id="646f3-111">The `Get-Culture` cmdlet gets information about the current culture settings.</span></span>
<span data-ttu-id="646f3-112">Ces informations incluent celles sur les paramètres de langue actuels du système, tels que la disposition du clavier et le format d'affichage d'éléments comme les nombres, les devises et les dates.</span><span class="sxs-lookup"><span data-stu-id="646f3-112">This includes information about the current language settings on the system, such as the keyboard layout, and the display format of items such as numbers, currency, and dates.</span></span>

<span data-ttu-id="646f3-113">Vous pouvez également utiliser l' `Get-UICulture` applet de commande, qui obtient la culture d’interface utilisateur actuelle sur le système, et l’applet de commande [Set-culture](/powershell/module/international/set-culture?view=win10-ps) dans le module international.</span><span class="sxs-lookup"><span data-stu-id="646f3-113">You can also use the `Get-UICulture` cmdlet, which gets the current user interface culture on the system, and the [Set-Culture](/powershell/module/international/set-culture?view=win10-ps) cmdlet in the International module.</span></span>
<span data-ttu-id="646f3-114">La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages.</span><span class="sxs-lookup"><span data-stu-id="646f3-114">The user-interface (UI) culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

## <span data-ttu-id="646f3-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="646f3-115">EXAMPLES</span></span>

### <span data-ttu-id="646f3-116">Exemple 1 : récupérer les paramètres de culture</span><span class="sxs-lookup"><span data-stu-id="646f3-116">Example 1: Get culture settings</span></span>

```
PS C:\> Get-Culture
```

<span data-ttu-id="646f3-117">Cette commande affiche des informations sur les paramètres régionaux de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="646f3-117">This command displays information about the regional settings on the computer.</span></span>

### <span data-ttu-id="646f3-118">Exemple 2 : mettre en forme les propriétés d’un objet culture</span><span class="sxs-lookup"><span data-stu-id="646f3-118">Example 2: Format the properties of a culture object</span></span>

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

<span data-ttu-id="646f3-119">Cet exemple illustre la vaste quantité de données dans l'objet de culture.</span><span class="sxs-lookup"><span data-stu-id="646f3-119">This example demonstrates the vast amount of data in the culture object.</span></span>
<span data-ttu-id="646f3-120">Il montre comment afficher les propriétés et les sous-propriétés de l'objet.</span><span class="sxs-lookup"><span data-stu-id="646f3-120">It shows how to display the properties and sub-properties of the object.</span></span>

<span data-ttu-id="646f3-121">La première commande utilise l’applet de commande **obten-culture** pour récupérer les paramètres de culture actuels sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="646f3-121">The first command uses the **Get-Culture** cmdlet to get the current culture settings on the computer.</span></span>
<span data-ttu-id="646f3-122">Elle stocke l’objet de culture résultant dans la variable $C.</span><span class="sxs-lookup"><span data-stu-id="646f3-122">It stores the resulting culture object in the $C variable.</span></span>

<span data-ttu-id="646f3-123">La deuxième commande affiche toutes les propriétés de l'objet de culture.</span><span class="sxs-lookup"><span data-stu-id="646f3-123">The second command displays all of the properties of the culture object.</span></span>
<span data-ttu-id="646f3-124">Elle utilise un opérateur de pipeline (|) pour envoyer l’objet de culture dans `$C` l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="646f3-124">It uses a pipeline operator (|) to send the culture object in `$C` to the `Format-List` cmdlet.</span></span>
<span data-ttu-id="646f3-125">Elle utilise le paramètre **Property** pour afficher toutes les \* Propriétés () de l’objet.</span><span class="sxs-lookup"><span data-stu-id="646f3-125">It uses the **Property** parameter to display all (\*) properties of the object.</span></span>
<span data-ttu-id="646f3-126">Cette commande peut être abrégée comme `$c | fl *` .</span><span class="sxs-lookup"><span data-stu-id="646f3-126">This command can be abbreviated as `$c | fl *`.</span></span>

<span data-ttu-id="646f3-127">Les commandes restantes explorent les propriétés de l'objet de culture à l'aide de la notation par point pour afficher les valeurs des propriétés de l'objet.</span><span class="sxs-lookup"><span data-stu-id="646f3-127">The remaining commands explore the properties of the culture object by using dot notation to display the values of the object properties.</span></span>
<span data-ttu-id="646f3-128">Vous pouvez utiliser cette notation pour afficher la valeur d'une propriété de l'objet.</span><span class="sxs-lookup"><span data-stu-id="646f3-128">You can use this notation to display the value of any property of the object.</span></span>

<span data-ttu-id="646f3-129">La troisième commande utilise la notation par points pour afficher la valeur de la propriété **Calendar** de l’objet culture.</span><span class="sxs-lookup"><span data-stu-id="646f3-129">The third command uses dot notation to display the value of the **Calendar** property of the culture object.</span></span>

<span data-ttu-id="646f3-130">La quatrième commande utilise la notation par points pour afficher la valeur de la propriété **DataTimeFormat** de l’objet culture.</span><span class="sxs-lookup"><span data-stu-id="646f3-130">The fourth command uses dot notation to display the value of the **DataTimeFormat** property of the culture object.</span></span>

<span data-ttu-id="646f3-131">Plusieurs propriétés de l'objet ont des propriétés.</span><span class="sxs-lookup"><span data-stu-id="646f3-131">Many object properties have properties.</span></span>
<span data-ttu-id="646f3-132">La cinquième commande utilise la notation par points pour afficher la valeur de la propriété **FirstDayOfWeek** de la propriété **DateTimeFormat** .</span><span class="sxs-lookup"><span data-stu-id="646f3-132">The fifth command uses dot notation to display the value of the **FirstDayOfWeek** property of the **DateTimeFormat** property.</span></span>

### <span data-ttu-id="646f3-133">Exemple 3 : obtenir une culture spécifique</span><span class="sxs-lookup"><span data-stu-id="646f3-133">Example 3: Get a specific culture</span></span>

<span data-ttu-id="646f3-134">Obtient l’objet CultureInfo pour l’anglais dans le États-Unis.</span><span class="sxs-lookup"><span data-stu-id="646f3-134">Get the CultureInfo object for English in the United States.</span></span>

```powershell
Get-Culture -Name en-US
```

```output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

## <span data-ttu-id="646f3-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="646f3-135">PARAMETERS</span></span>

### <span data-ttu-id="646f3-136">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="646f3-136">-ListAvailable</span></span>

<span data-ttu-id="646f3-137">Récupère toutes les cultures prises en charge par le système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="646f3-137">Retrieves all cultures supported by the current operating system.</span></span>

<span data-ttu-id="646f3-138">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="646f3-138">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="646f3-139">-Name</span><span class="sxs-lookup"><span data-stu-id="646f3-139">-Name</span></span>

<span data-ttu-id="646f3-140">Récupérez une culture spécifique en fonction du nom.</span><span class="sxs-lookup"><span data-stu-id="646f3-140">Retrieve a specific culture based on the name.</span></span>

<span data-ttu-id="646f3-141">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="646f3-141">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="646f3-142">-NoUserOverrides</span><span class="sxs-lookup"><span data-stu-id="646f3-142">-NoUserOverrides</span></span>

<span data-ttu-id="646f3-143">Ignorer les modifications utilisateur pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="646f3-143">Ignore user changes for current culture.</span></span>

<span data-ttu-id="646f3-144">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="646f3-144">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="646f3-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="646f3-145">CommonParameters</span></span>

<span data-ttu-id="646f3-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="646f3-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="646f3-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="646f3-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="646f3-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="646f3-148">INPUTS</span></span>

### <span data-ttu-id="646f3-149">Aucun</span><span class="sxs-lookup"><span data-stu-id="646f3-149">None</span></span>

<span data-ttu-id="646f3-150">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="646f3-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="646f3-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="646f3-151">OUTPUTS</span></span>

### <span data-ttu-id="646f3-152">System. Globalization. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="646f3-152">System.Globalization.CultureInfo</span></span>

<span data-ttu-id="646f3-153">`Get-Culture` retourne un objet qui représente la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="646f3-153">`Get-Culture` returns an object that represents the current culture.</span></span>

## <span data-ttu-id="646f3-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="646f3-154">NOTES</span></span>

<span data-ttu-id="646f3-155">Vous pouvez également utiliser les `$PsCulture` `$PsUICulture` variables et.</span><span class="sxs-lookup"><span data-stu-id="646f3-155">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="646f3-156">La `$PsCulture` variable stocke le nom de la culture actuelle et la `$PsUICulture` variable stocke le nom de la culture d’interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="646f3-156">The `$PsCulture` variable stores the name of the current culture and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="646f3-157">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="646f3-157">RELATED LINKS</span></span>

[<span data-ttu-id="646f3-158">Définir-culture</span><span class="sxs-lookup"><span data-stu-id="646f3-158">Set-Culture</span></span>](/powershell/module/international/set-culture?view=win10-ps)

[<span data-ttu-id="646f3-159">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="646f3-159">Get-UICulture</span></span>](Get-UICulture.md)
