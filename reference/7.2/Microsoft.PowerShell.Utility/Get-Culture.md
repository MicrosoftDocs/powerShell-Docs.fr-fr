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
# <span data-ttu-id="8d5e3-102">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="8d5e3-102">Get-Culture</span></span>

## <span data-ttu-id="8d5e3-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8d5e3-103">SYNOPSIS</span></span>
<span data-ttu-id="8d5e3-104">Obtient la culture actuelle définie dans le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-104">Gets the current culture set in the operating system.</span></span>

## <span data-ttu-id="8d5e3-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8d5e3-105">SYNTAX</span></span>

### <span data-ttu-id="8d5e3-106">CurrentCulture (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8d5e3-106">CurrentCulture (Default)</span></span>

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="8d5e3-107">Nom</span><span class="sxs-lookup"><span data-stu-id="8d5e3-107">Name</span></span>

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="8d5e3-108">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="8d5e3-108">ListAvailable</span></span>

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="8d5e3-109">Description</span><span class="sxs-lookup"><span data-stu-id="8d5e3-109">DESCRIPTION</span></span>

<span data-ttu-id="8d5e3-110">L' `Get-Culture` applet de commande obtient des informations sur les paramètres de culture actuels.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-110">The `Get-Culture` cmdlet gets information about the current culture settings.</span></span> <span data-ttu-id="8d5e3-111">Ces informations incluent celles sur les paramètres de langue actuels du système, tels que la disposition du clavier et le format d'affichage d'éléments comme les nombres, les devises et les dates.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-111">This includes information about the current language settings on the system, such as the keyboard layout, and the display format of items such as numbers, currency, and dates.</span></span>

<span data-ttu-id="8d5e3-112">Vous pouvez également utiliser l' `Get-UICulture` applet de commande, qui obtient la culture d’interface utilisateur actuelle sur le système, et l’applet de commande [Set-culture](/powershell/module/international/set-culture) dans le module international.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-112">You can also use the `Get-UICulture` cmdlet, which gets the current user interface culture on the system, and the [Set-Culture](/powershell/module/international/set-culture) cmdlet in the International module.</span></span> <span data-ttu-id="8d5e3-113">La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-113">The user-interface (UI) culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

## <span data-ttu-id="8d5e3-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8d5e3-114">EXAMPLES</span></span>

### <span data-ttu-id="8d5e3-115">Exemple 1 : récupérer les paramètres de culture</span><span class="sxs-lookup"><span data-stu-id="8d5e3-115">Example 1: Get culture settings</span></span>

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="8d5e3-116">Cette commande affiche des informations sur les paramètres régionaux de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-116">This command displays information about the regional settings on the computer.</span></span>

### <span data-ttu-id="8d5e3-117">Exemple 2 : mettre en forme les propriétés d’un objet culture</span><span class="sxs-lookup"><span data-stu-id="8d5e3-117">Example 2: Format the properties of a culture object</span></span>

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

<span data-ttu-id="8d5e3-118">Cet exemple illustre la vaste quantité de données dans l'objet de culture.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-118">This example demonstrates the vast amount of data in the culture object.</span></span> <span data-ttu-id="8d5e3-119">Il montre comment afficher les propriétés et les sous-propriétés de l'objet.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-119">It shows how to display the properties and sub-properties of the object.</span></span>

<span data-ttu-id="8d5e3-120">La première commande utilise l' `Get-Culture` applet de commande pour récupérer les paramètres de culture actuels sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-120">The first command uses the `Get-Culture` cmdlet to get the current culture settings on the computer.</span></span>
<span data-ttu-id="8d5e3-121">Elle stocke l’objet de culture résultant dans la `$C` variable.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-121">It stores the resulting culture object in the `$C` variable.</span></span>

<span data-ttu-id="8d5e3-122">La deuxième commande affiche toutes les propriétés de l'objet de culture.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-122">The second command displays all of the properties of the culture object.</span></span> <span data-ttu-id="8d5e3-123">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet de culture dans `$C` l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="8d5e3-123">It uses a pipeline operator (`|`) to send the culture object in `$C` to the `Format-List` cmdlet.</span></span> <span data-ttu-id="8d5e3-124">Elle utilise le paramètre **Property** pour afficher toutes les `*` Propriétés () de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-124">It uses the **Property** parameter to display all (`*`) properties of the object.</span></span> <span data-ttu-id="8d5e3-125">Cette commande peut être abrégée comme `$c | fl *` .</span><span class="sxs-lookup"><span data-stu-id="8d5e3-125">This command can be abbreviated as `$c | fl *`.</span></span>

<span data-ttu-id="8d5e3-126">Les commandes restantes explorent les propriétés de l'objet de culture à l'aide de la notation par point pour afficher les valeurs des propriétés de l'objet.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-126">The remaining commands explore the properties of the culture object by using dot notation to display the values of the object properties.</span></span> <span data-ttu-id="8d5e3-127">Vous pouvez utiliser cette notation pour afficher la valeur d'une propriété de l'objet.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-127">You can use this notation to display the value of any property of the object.</span></span>

<span data-ttu-id="8d5e3-128">La troisième commande utilise la notation par points pour afficher la valeur de la propriété **Calendar** de l’objet culture.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-128">The third command uses dot notation to display the value of the **Calendar** property of the culture object.</span></span>

<span data-ttu-id="8d5e3-129">La quatrième commande utilise la notation par points pour afficher la valeur de la propriété **DataTimeFormat** de l’objet culture.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-129">The fourth command uses dot notation to display the value of the **DataTimeFormat** property of the culture object.</span></span>

<span data-ttu-id="8d5e3-130">Plusieurs propriétés de l'objet ont des propriétés.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-130">Many object properties have properties.</span></span> <span data-ttu-id="8d5e3-131">La cinquième commande utilise la notation par points pour afficher la valeur de la propriété **FirstDayOfWeek** de la propriété **DateTimeFormat** .</span><span class="sxs-lookup"><span data-stu-id="8d5e3-131">The fifth command uses dot notation to display the value of the **FirstDayOfWeek** property of the **DateTimeFormat** property.</span></span>

### <span data-ttu-id="8d5e3-132">Exemple 3 : obtenir une culture spécifique</span><span class="sxs-lookup"><span data-stu-id="8d5e3-132">Example 3: Get a specific culture</span></span>

<span data-ttu-id="8d5e3-133">Obtenir l’objet CultureInfo pour le français en France.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-133">Get the CultureInfo object for French in France.</span></span>

```powershell
Get-Culture -Name fr-FR
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1036             fr-FR            French (France)
```

## <span data-ttu-id="8d5e3-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8d5e3-134">PARAMETERS</span></span>

### <span data-ttu-id="8d5e3-135">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="8d5e3-135">-ListAvailable</span></span>

<span data-ttu-id="8d5e3-136">Récupère toutes les cultures prises en charge par le système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-136">Retrieves all cultures supported by the current operating system.</span></span>

<span data-ttu-id="8d5e3-137">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-137">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="8d5e3-138">-Name</span><span class="sxs-lookup"><span data-stu-id="8d5e3-138">-Name</span></span>

<span data-ttu-id="8d5e3-139">Récupérez une culture spécifique en fonction du nom.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-139">Retrieve a specific culture based on the name.</span></span>

<span data-ttu-id="8d5e3-140">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-140">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="8d5e3-141">-NoUserOverrides</span><span class="sxs-lookup"><span data-stu-id="8d5e3-141">-NoUserOverrides</span></span>

<span data-ttu-id="8d5e3-142">Ignorer les modifications utilisateur pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-142">Ignore user changes for current culture.</span></span>

<span data-ttu-id="8d5e3-143">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-143">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="8d5e3-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8d5e3-144">CommonParameters</span></span>

<span data-ttu-id="8d5e3-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8d5e3-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8d5e3-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8d5e3-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8d5e3-147">INPUTS</span></span>

### <span data-ttu-id="8d5e3-148">None</span><span class="sxs-lookup"><span data-stu-id="8d5e3-148">None</span></span>

<span data-ttu-id="8d5e3-149">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-149">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="8d5e3-150">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8d5e3-150">OUTPUTS</span></span>

### <span data-ttu-id="8d5e3-151">System. Globalization. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="8d5e3-151">System.Globalization.CultureInfo</span></span>

<span data-ttu-id="8d5e3-152">`Get-Culture` retourne un objet qui représente la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-152">`Get-Culture` returns an object that represents the current culture.</span></span>

## <span data-ttu-id="8d5e3-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8d5e3-153">NOTES</span></span>

<span data-ttu-id="8d5e3-154">Vous pouvez également utiliser les `$PsCulture` `$PsUICulture` variables et.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-154">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="8d5e3-155">La `$PsCulture` variable stocke le nom de la culture actuelle et la `$PsUICulture` variable stocke le nom de la culture d’interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="8d5e3-155">The `$PsCulture` variable stores the name of the current culture and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="8d5e3-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8d5e3-156">RELATED LINKS</span></span>

[<span data-ttu-id="8d5e3-157">Définir-culture</span><span class="sxs-lookup"><span data-stu-id="8d5e3-157">Set-Culture</span></span>](/powershell/module/international/set-culture)

[<span data-ttu-id="8d5e3-158">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="8d5e3-158">Get-UICulture</span></span>](Get-UICulture.md)
