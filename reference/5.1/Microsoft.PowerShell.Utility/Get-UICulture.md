---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 098e98dec6733af036795e4decb633f59d40c633
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200810"
---
# <span data-ttu-id="a58a0-103">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="a58a0-103">Get-UICulture</span></span>

## <span data-ttu-id="a58a0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a58a0-104">SYNOPSIS</span></span>
<span data-ttu-id="a58a0-105">Obtient les paramètres de culture d’interface utilisateur actuels dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="a58a0-105">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="a58a0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a58a0-106">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="a58a0-107">Description</span><span class="sxs-lookup"><span data-stu-id="a58a0-107">DESCRIPTION</span></span>
<span data-ttu-id="a58a0-108">L’applet de commande **obten-UICulture** obtient des informations sur les paramètres de culture de l’interface utilisateur (IU) actuels pour Windows.</span><span class="sxs-lookup"><span data-stu-id="a58a0-108">The **Get-UICulture** cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="a58a0-109">La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages.</span><span class="sxs-lookup"><span data-stu-id="a58a0-109">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="a58a0-110">Vous pouvez également utiliser l'applet de commande Get-Culture, qui obtient la culture actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="a58a0-110">You can also use the Get-Culture cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="a58a0-111">La culture détermine le format d'affichage d'éléments tels que nombres, devises et dates.</span><span class="sxs-lookup"><span data-stu-id="a58a0-111">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="a58a0-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a58a0-112">EXAMPLES</span></span>

### <span data-ttu-id="a58a0-113">Exemple 1 : récupération de la culture de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="a58a0-113">Example 1: Get the UI culture</span></span>

```
PS C:\> Get-UICulture
```

<span data-ttu-id="a58a0-114">Cette commande obtient les informations sur la culture d'interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="a58a0-114">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="a58a0-115">Exemple 2 : obtenir la culture de l’interface utilisateur et mettre en forme les résultats</span><span class="sxs-lookup"><span data-stu-id="a58a0-115">Example 2: Get the UI culture and format the results</span></span>

```
PS C:\> Get-UICulture | Format-List *
```

<span data-ttu-id="a58a0-116">Cette commande affiche les valeurs de toutes les propriétés de la culture d'interface utilisateur actuelle dans une liste.</span><span class="sxs-lookup"><span data-stu-id="a58a0-116">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="a58a0-117">Exemple 3 : récupération de la valeur de la propriété Calendar</span><span class="sxs-lookup"><span data-stu-id="a58a0-117">Example 3: Get the value of the Calendar property</span></span>

```
PS C:\> (Get-UICulture).Calendar
```

<span data-ttu-id="a58a0-118">Cette commande affiche les valeurs actuelles de la propriété Calendar de la culture d'interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="a58a0-118">This command displays the current values for the Calendar property of the current UI culture.</span></span>
<span data-ttu-id="a58a0-119">Calendar n'est qu'une des propriétés de la culture d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a58a0-119">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="a58a0-120">Pour afficher toutes les propriétés, tapez `Get-UICulture | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="a58a0-120">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="a58a0-121">Exemple 4 : récupération du modèle de date abrégée</span><span class="sxs-lookup"><span data-stu-id="a58a0-121">Example 4: Get the short date pattern</span></span>

```
PS C:\> (Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="a58a0-122">Cette commande affiche le modèle de date courte de la culture d'interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="a58a0-122">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="a58a0-123">Pour afficher toutes les sous-propriétés de la propriété DateTimeFormat de la culture d’interface utilisateur, tapez `(Get-UICulture).DateTimeFormat | gm` .</span><span class="sxs-lookup"><span data-stu-id="a58a0-123">To see all of the subproperties of the DateTimeFormat property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="a58a0-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a58a0-124">PARAMETERS</span></span>

### <span data-ttu-id="a58a0-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a58a0-125">CommonParameters</span></span>
<span data-ttu-id="a58a0-126">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a58a0-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a58a0-127">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a58a0-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a58a0-128">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a58a0-128">INPUTS</span></span>

### <span data-ttu-id="a58a0-129">Aucun</span><span class="sxs-lookup"><span data-stu-id="a58a0-129">None</span></span>
<span data-ttu-id="a58a0-130">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a58a0-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a58a0-131">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a58a0-131">OUTPUTS</span></span>

### <span data-ttu-id="a58a0-132">System. Globalization. CultureInfo, Microsoft. PowerShell. VistaCultureInfo</span><span class="sxs-lookup"><span data-stu-id="a58a0-132">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>
<span data-ttu-id="a58a0-133">La méthode **obten-UICulture** retourne un objet qui représente la culture d’interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="a58a0-133">**Get-UICulture** returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="a58a0-134">Dans Windows PowerShell 3,0, elle retourne un objet **CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="a58a0-134">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="a58a0-135">Dans Windows PowerShell 2,0, elle retourne un objet **VistaCultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="a58a0-135">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="a58a0-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a58a0-136">NOTES</span></span>

* <span data-ttu-id="a58a0-137">Vous pouvez également utiliser les variables $PsCulture et $PsUICulture.</span><span class="sxs-lookup"><span data-stu-id="a58a0-137">You can also use the $PsCulture and $PsUICulture variables.</span></span> <span data-ttu-id="a58a0-138">La variable $PsCulture stocke le nom de la culture actuelle et la variable $PsUICulture le nom de la culture d'interface utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="a58a0-138">The $PsCulture variable stores the name of the current culture, and the $PsUICulture variable stores the name of the current UI culture.</span></span>

*

## <span data-ttu-id="a58a0-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a58a0-139">RELATED LINKS</span></span>

## <span data-ttu-id="a58a0-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a58a0-140">RELATED LINKS</span></span>
