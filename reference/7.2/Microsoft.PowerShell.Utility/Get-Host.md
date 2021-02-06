---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: 0775940f210cb028d7a0919bb8e5ca9f256b70d8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597748"
---
# <span data-ttu-id="1f303-102">Get-Host</span><span class="sxs-lookup"><span data-stu-id="1f303-102">Get-Host</span></span>

## <span data-ttu-id="1f303-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1f303-103">SYNOPSIS</span></span>
<span data-ttu-id="1f303-104">Obtient un objet qui représente le programme hôte actuel.</span><span class="sxs-lookup"><span data-stu-id="1f303-104">Gets an object that represents the current host program.</span></span>

## <span data-ttu-id="1f303-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="1f303-105">SYNTAX</span></span>

```
Get-Host [<CommonParameters>]
```

## <span data-ttu-id="1f303-106">Description</span><span class="sxs-lookup"><span data-stu-id="1f303-106">DESCRIPTION</span></span>

<span data-ttu-id="1f303-107">L' `Get-Host` applet de commande obtient un objet qui représente le programme qui héberge Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f303-107">The `Get-Host` cmdlet gets an object that represents the program that is hosting Windows PowerShell.</span></span>

<span data-ttu-id="1f303-108">L'affichage par défaut inclut le numéro de version de Windows PowerShell, ainsi que les paramètres de région et de langue actuels que l'hôte utilise. Toutefois, l'objet hôte contient une mine d'informations, dont notamment des informations détaillées sur la version de Windows PowerShell en cours d'exécution, ainsi que la culture actuelle et la culture d'interface utilisateur de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f303-108">The default display includes the Windows PowerShell version number and the current region and language settings that the host is using, but the host object contains a wealth of information, including detailed information about the version of Windows PowerShell that is currently running and the current culture and UI culture of Windows PowerShell.</span></span> <span data-ttu-id="1f303-109">Vous pouvez également utiliser cette applet de commande pour personnaliser les fonctionnalités de l’interface utilisateur du programme hôte, telles que les couleurs de texte et d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1f303-109">You can also use this cmdlet to customize features of the host program user interface, such as the text and background colors.</span></span>

## <span data-ttu-id="1f303-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1f303-110">EXAMPLES</span></span>

### <span data-ttu-id="1f303-111">Exemple 1 : obtenir des informations sur l’hôte de la console PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f303-111">Example 1: Get information about the PowerShell console host</span></span>

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

<span data-ttu-id="1f303-112">Cette commande affiche des informations sur la console Windows PowerShell, qui est le programme hôte actuel pour Windows PowerShell dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="1f303-112">This command displays information about the Windows PowerShell console, which is the current host program for Windows PowerShell in this example.</span></span> <span data-ttu-id="1f303-113">Elle inclut le nom de l'hôte, la version de Windows PowerShell qui s'exécute sur l'hôte, ainsi que la culture actuelle et la culture d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1f303-113">It includes the name of the host, the version of Windows PowerShell that is running in the host, and current culture and UI culture.</span></span>

<span data-ttu-id="1f303-114">Les propriétés Version, UI, CurrentCulture, CurrentUICulture, PrivateData, et Runspace contiennent toutes un objet doté de propriétés très utiles.</span><span class="sxs-lookup"><span data-stu-id="1f303-114">The Version, UI, CurrentCulture, CurrentUICulture, PrivateData, and Runspace properties each contain an object with very useful properties.</span></span> <span data-ttu-id="1f303-115">Les exemples suivants illustrent ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="1f303-115">Later examples examine these properties.</span></span>

### <span data-ttu-id="1f303-116">Exemple 2 : redimensionner la fenêtre PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f303-116">Example 2: Resize the PowerShell window</span></span>

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

<span data-ttu-id="1f303-117">Cette commande redimensionne la fenêtre Windows PowerShell à 10 x 10 pixels.</span><span class="sxs-lookup"><span data-stu-id="1f303-117">This command resizes the Windows PowerShell window to 10 pixels by 10 pixels.</span></span>

### <span data-ttu-id="1f303-118">Exemple 3 : obtenir la version de PowerShell pour l’hôte</span><span class="sxs-lookup"><span data-stu-id="1f303-118">Example 3: Get the PowerShell version for the host</span></span>

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

<span data-ttu-id="1f303-119">Cette commande obtient des informations détaillées sur la version de Windows PowerShell en cours d'exécution sur l'hôte.</span><span class="sxs-lookup"><span data-stu-id="1f303-119">This command gets detailed information about the version of Windows PowerShell running in the host.</span></span>
<span data-ttu-id="1f303-120">Vous pouvez afficher, mais pas modifier, ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="1f303-120">You can view, but not change, these values.</span></span>

<span data-ttu-id="1f303-121">La propriété version de `Get-Host` contient un objet **System. version** .</span><span class="sxs-lookup"><span data-stu-id="1f303-121">The Version property of `Get-Host` contains a **System.Version** object.</span></span> <span data-ttu-id="1f303-122">Cette commande utilise un opérateur de pipeline (|) pour envoyer l’objet de version à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="1f303-122">This command uses a pipeline operator (|) to send the version object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1f303-123">La `Format-List` commande utilise le paramètre *Property* avec la valeur All (\*) pour afficher toutes les propriétés et les valeurs de propriété de l’objet version.</span><span class="sxs-lookup"><span data-stu-id="1f303-123">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the version object.</span></span>

### <span data-ttu-id="1f303-124">Exemple 4 : obtenir la culture actuelle pour l’hôte</span><span class="sxs-lookup"><span data-stu-id="1f303-124">Example 4: Get the current culture for the host</span></span>

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

<span data-ttu-id="1f303-125">Cette commande obtient des informations détaillées sur la culture actuelle définie pour Windows PowerShell et en cours d'exécution sur l'hôte.</span><span class="sxs-lookup"><span data-stu-id="1f303-125">This command gets detailed information about the current culture set for Windows PowerShell running in the host.</span></span> <span data-ttu-id="1f303-126">Il s’agit des mêmes informations que celles retournées par l’applet de commande `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="1f303-126">This is the same information that is returned by the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="1f303-127">De même, la propriété **CurrentUICulture** retourne le même objet que celui `Get-UICulture` retourné par.</span><span class="sxs-lookup"><span data-stu-id="1f303-127">Similarly, the **CurrentUICulture** property returns the same object that `Get-UICulture` returns.</span></span>

<span data-ttu-id="1f303-128">La propriété **CurrentCulture** de l’objet hôte contient un objet **System. Globalization. CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="1f303-128">The **CurrentCulture** property of the host object contains a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="1f303-129">Cette commande utilise un opérateur de pipeline (|) pour envoyer l’objet **CultureInfo** à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="1f303-129">This command uses a pipeline operator (|) to send the **CultureInfo** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1f303-130">La `Format-List` commande utilise le paramètre *Property* avec la valeur All (\*) pour afficher toutes les propriétés et les valeurs de propriété de l’objet **CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="1f303-130">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the **CultureInfo** object.</span></span>

### <span data-ttu-id="1f303-131">Exemple 5 : obtenir DateTimeFormat pour la culture actuelle</span><span class="sxs-lookup"><span data-stu-id="1f303-131">Example 5: Get the DateTimeFormat for the current culture</span></span>

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

<span data-ttu-id="1f303-132">Cette commande retourne des informations détaillées sur le DateTimeFormat de la culture actuelle, en cours d'utilisation pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f303-132">This command returns detailed information about the DateTimeFormat of the current culture that is being used for Windows PowerShell.</span></span>

<span data-ttu-id="1f303-133">La propriété **CurrentCulture** de l’objet hôte contient un objet **CultureInfo** qui, à son tour, a de nombreuses propriétés utiles.</span><span class="sxs-lookup"><span data-stu-id="1f303-133">The **CurrentCulture** property of the host object contains a **CultureInfo** object that, in turn, has many useful properties.</span></span> <span data-ttu-id="1f303-134">Parmi celles-ci, la propriété **DateTimeFormat** contient un objet **DateTimeFormatInfo** avec de nombreuses propriétés utiles.</span><span class="sxs-lookup"><span data-stu-id="1f303-134">Among them, the **DateTimeFormat** property contains a **DateTimeFormatInfo** object with many useful properties.</span></span>

<span data-ttu-id="1f303-135">Pour rechercher le type d’un objet stocké dans une propriété d’objet, utilisez l' `Get-Member` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1f303-135">To find the type of an object that is stored in an object property, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="1f303-136">Pour afficher les valeurs de propriété de l’objet, utilisez l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="1f303-136">To display the property values of the object, use the `Format-List` cmdlet.</span></span>

### <span data-ttu-id="1f303-137">Exemple 6 : obtenir la propriété RawUI pour l’hôte</span><span class="sxs-lookup"><span data-stu-id="1f303-137">Example 6: Get the RawUI property for the host</span></span>

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

<span data-ttu-id="1f303-138">Cette commande affiche les propriétés de la propriété **rawui** de l’objet hôte.</span><span class="sxs-lookup"><span data-stu-id="1f303-138">This command displays the properties of the **RawUI** property of the host object.</span></span> <span data-ttu-id="1f303-139">En modifiant ces valeurs, vous pouvez modifier l'apparence du programme hôte.</span><span class="sxs-lookup"><span data-stu-id="1f303-139">By changing these values, you can change the appearance of the host program.</span></span>

### <span data-ttu-id="1f303-140">Exemple 7 : définir la couleur d’arrière-plan de la console PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f303-140">Example 7: Set the background color for the PowerShell console</span></span>

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

<span data-ttu-id="1f303-141">Ces commandes définissent en noir la couleur d'arrière-plan de la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f303-141">These commands change the background color of the Windows PowerShell console to black.</span></span> <span data-ttu-id="1f303-142">La commande **CLS** est un alias pour la `Clear-Host` fonction, ce qui efface l’écran et remplace l’écran entier par la nouvelle couleur.</span><span class="sxs-lookup"><span data-stu-id="1f303-142">The **cls** command is an alias for the `Clear-Host` function, which clears the screen and changes the whole screen to the new color.</span></span>

<span data-ttu-id="1f303-143">Cette modification est effective uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="1f303-143">This change is effective only in the current session.</span></span> <span data-ttu-id="1f303-144">Pour modifier la couleur d'arrière-plan de la console pour toutes les sessions, ajoutez la commande à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f303-144">To change the background color of the console for all sessions, add the command to your Windows PowerShell profile.</span></span>

### <span data-ttu-id="1f303-145">Exemple 8 : définir la couleur d’arrière-plan des messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="1f303-145">Example 8: Set the background color for error messages</span></span>

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

<span data-ttu-id="1f303-146">Cette commande définit en blanc la couleur d'arrière-plan des messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="1f303-146">This command changes the background color of error messages to white.</span></span>

<span data-ttu-id="1f303-147">Cette commande utilise la `$Host` variable automatique, qui contient l’objet hôte du programme hôte actuel.</span><span class="sxs-lookup"><span data-stu-id="1f303-147">This command uses the `$Host` automatic variable, which contains the host object for the current host program.</span></span> <span data-ttu-id="1f303-148">`Get-Host` retourne le même objet que celui qui `$Host` contient, de sorte que vous pouvez les utiliser de manière interchangeable.</span><span class="sxs-lookup"><span data-stu-id="1f303-148">`Get-Host` returns the same object that `$Host` contains, so you can use them interchangeably.</span></span>

<span data-ttu-id="1f303-149">Cette commande utilise la propriété **PrivateData** de `$Host` comme propriété ErrorBackgroundColor.</span><span class="sxs-lookup"><span data-stu-id="1f303-149">This command uses the **PrivateData** property of `$Host` as its ErrorBackgroundColor property.</span></span> <span data-ttu-id="1f303-150">Pour afficher toutes les propriétés de l’objet dans le `$Host` . Propriété PrivateData, tapez `$host.privatedata | format-list *` .</span><span class="sxs-lookup"><span data-stu-id="1f303-150">To see all of the properties of the object in the `$Host`.PrivateData property, type `$host.privatedata | format-list *`.</span></span>

## <span data-ttu-id="1f303-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1f303-151">PARAMETERS</span></span>

### <span data-ttu-id="1f303-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1f303-152">CommonParameters</span></span>

<span data-ttu-id="1f303-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1f303-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1f303-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1f303-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1f303-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1f303-155">INPUTS</span></span>

### <span data-ttu-id="1f303-156">None</span><span class="sxs-lookup"><span data-stu-id="1f303-156">None</span></span>
<span data-ttu-id="1f303-157">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1f303-157">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1f303-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1f303-158">OUTPUTS</span></span>

### <span data-ttu-id="1f303-159">System. Management. Automation. Internal. Host. InternalHost</span><span class="sxs-lookup"><span data-stu-id="1f303-159">System.Management.Automation.Internal.Host.InternalHost</span></span>

<span data-ttu-id="1f303-160">`Get-Host` retourne un objet **System. Management. Automation. Internal. Host. InternalHost** .</span><span class="sxs-lookup"><span data-stu-id="1f303-160">`Get-Host` returns a **System.Management.Automation.Internal.Host.InternalHost** object.</span></span>

## <span data-ttu-id="1f303-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1f303-161">NOTES</span></span>

<span data-ttu-id="1f303-162">La `$Host` variable automatique contient le même objet que celui `Get-Host` retourné par, et vous pouvez l’utiliser de la même façon.</span><span class="sxs-lookup"><span data-stu-id="1f303-162">The `$Host` automatic variable contains the same object that `Get-Host` returns, and you can use it in the same way.</span></span> <span data-ttu-id="1f303-163">De même, les `$PSCulture` `$PSUICulture` variables automatiques et contiennent les mêmes objets que les propriétés CurrentCulture et CurrentUICulture de l’objet hôte.</span><span class="sxs-lookup"><span data-stu-id="1f303-163">Similarly, the `$PSCulture` and `$PSUICulture` automatic variables contain the same objects that the CurrentCulture and CurrentUICulture properties of the host object contain.</span></span> <span data-ttu-id="1f303-164">Vous pouvez utiliser ces fonctionnalités de manière interchangeable.</span><span class="sxs-lookup"><span data-stu-id="1f303-164">You can use these features interchangeably.</span></span>

<span data-ttu-id="1f303-165">Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1f303-165">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="1f303-166">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1f303-166">RELATED LINKS</span></span>

[<span data-ttu-id="1f303-167">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="1f303-167">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="1f303-168">Read-Host</span><span class="sxs-lookup"><span data-stu-id="1f303-168">Read-Host</span></span>](Read-Host.md)

[<span data-ttu-id="1f303-169">Write-Host</span><span class="sxs-lookup"><span data-stu-id="1f303-169">Write-Host</span></span>](Write-Host.md)

