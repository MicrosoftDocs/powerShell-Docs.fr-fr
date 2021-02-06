---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 4bd912db3f86ffa8b495faf3e62259f207340938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603669"
---
# <span data-ttu-id="58035-102">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="58035-102">Get-UICulture</span></span>

## <span data-ttu-id="58035-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="58035-103">SYNOPSIS</span></span>
<span data-ttu-id="58035-104">Obtient les paramètres de culture d’interface utilisateur actuels dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="58035-104">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="58035-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="58035-105">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="58035-106">Description</span><span class="sxs-lookup"><span data-stu-id="58035-106">DESCRIPTION</span></span>

<span data-ttu-id="58035-107">L' `Get-UICulture` applet de commande obtient des informations sur les paramètres de culture de l’interface utilisateur (IU) actuelle pour Windows.</span><span class="sxs-lookup"><span data-stu-id="58035-107">The `Get-UICulture` cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="58035-108">La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages.</span><span class="sxs-lookup"><span data-stu-id="58035-108">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="58035-109">Vous pouvez également utiliser l' `Get-Culture` applet de commande, qui obtient la culture actuelle sur le système.</span><span class="sxs-lookup"><span data-stu-id="58035-109">You can also use the `Get-Culture` cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="58035-110">La culture détermine le format d'affichage d'éléments tels que nombres, devises et dates.</span><span class="sxs-lookup"><span data-stu-id="58035-110">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="58035-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="58035-111">EXAMPLES</span></span>

### <span data-ttu-id="58035-112">Exemple 1 : récupération de la culture de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="58035-112">Example 1: Get the UI culture</span></span>

```powershell
Get-UICulture
```

<span data-ttu-id="58035-113">Cette commande obtient les informations sur la culture d'interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="58035-113">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="58035-114">Exemple 2 : obtenir la culture de l’interface utilisateur et mettre en forme les résultats</span><span class="sxs-lookup"><span data-stu-id="58035-114">Example 2: Get the UI culture and format the results</span></span>

```powershell
Get-UICulture | Format-List *
```

<span data-ttu-id="58035-115">Cette commande affiche les valeurs de toutes les propriétés de la culture d'interface utilisateur actuelle dans une liste.</span><span class="sxs-lookup"><span data-stu-id="58035-115">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="58035-116">Exemple 3 : récupération de la valeur de la propriété Calendar</span><span class="sxs-lookup"><span data-stu-id="58035-116">Example 3: Get the value of the Calendar property</span></span>

```powershell
(Get-UICulture).Calendar
```

<span data-ttu-id="58035-117">Cette commande affiche les valeurs actuelles de la propriété **Calendar** de la culture d’interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="58035-117">This command displays the current values for the **Calendar** property of the current UI culture.</span></span>
<span data-ttu-id="58035-118">Calendar n'est qu'une des propriétés de la culture d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="58035-118">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="58035-119">Pour afficher toutes les propriétés, tapez `Get-UICulture | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="58035-119">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="58035-120">Exemple 4 : récupération du modèle de date abrégée</span><span class="sxs-lookup"><span data-stu-id="58035-120">Example 4: Get the short date pattern</span></span>

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="58035-121">Cette commande affiche le modèle de date courte de la culture d'interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="58035-121">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="58035-122">Pour afficher toutes les sous-propriétés de la propriété **DateTimeFormat** de la culture d’interface utilisateur, tapez `(Get-UICulture).DateTimeFormat | gm` .</span><span class="sxs-lookup"><span data-stu-id="58035-122">To see all of the subproperties of the **DateTimeFormat** property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="58035-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="58035-123">PARAMETERS</span></span>

### <span data-ttu-id="58035-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="58035-124">CommonParameters</span></span>

<span data-ttu-id="58035-125">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="58035-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="58035-126">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="58035-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="58035-127">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="58035-127">INPUTS</span></span>

### <span data-ttu-id="58035-128">None</span><span class="sxs-lookup"><span data-stu-id="58035-128">None</span></span>

<span data-ttu-id="58035-129">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58035-129">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="58035-130">SORTIES</span><span class="sxs-lookup"><span data-stu-id="58035-130">OUTPUTS</span></span>

### <span data-ttu-id="58035-131">System. Globalization. CultureInfo, Microsoft. PowerShell. VistaCultureInfo</span><span class="sxs-lookup"><span data-stu-id="58035-131">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>

<span data-ttu-id="58035-132">`Get-UICulture` retourne un objet qui représente la culture d’interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="58035-132">`Get-UICulture` returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="58035-133">Dans Windows PowerShell 3,0, elle retourne un objet **CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="58035-133">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="58035-134">Dans Windows PowerShell 2,0, elle retourne un objet **VistaCultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="58035-134">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="58035-135">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="58035-135">NOTES</span></span>

- <span data-ttu-id="58035-136">Vous pouvez également utiliser les `$PsCulture` `$PsUICulture` variables et.</span><span class="sxs-lookup"><span data-stu-id="58035-136">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="58035-137">La `$PsCulture` variable stocke le nom de la culture actuelle et la `$PsUICulture` variable stocke le nom de la culture d’interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="58035-137">The `$PsCulture` variable stores the name of the current culture, and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="58035-138">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="58035-138">RELATED LINKS</span></span>

