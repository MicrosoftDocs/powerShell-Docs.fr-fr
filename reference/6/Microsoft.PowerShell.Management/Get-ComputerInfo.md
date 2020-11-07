---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: d0bf17b4bdc169661cf4cde878739287d8be668b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343981"
---
# <span data-ttu-id="6f334-103">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="6f334-103">Get-ComputerInfo</span></span>

## <span data-ttu-id="6f334-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6f334-104">SYNOPSIS</span></span>
<span data-ttu-id="6f334-105">Obtient un objet consolidé des propriétés système et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6f334-105">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="6f334-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="6f334-106">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="6f334-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6f334-107">DESCRIPTION</span></span>

<span data-ttu-id="6f334-108">L' `Get-ComputerInfo` applet de commande obtient un objet consolidé des propriétés système et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6f334-108">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="6f334-109">Cette applet de commande a été introduite dans Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="6f334-109">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="6f334-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6f334-110">EXAMPLES</span></span>

### <span data-ttu-id="6f334-111">Exemple 1 : récupération de toutes les propriétés de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="6f334-111">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="6f334-112">Cette commande obtient toutes les propriétés système et système d’exploitation de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6f334-112">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="6f334-113">Exemple 2 : récupération de toutes les propriétés du système d’exploitation de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="6f334-113">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="6f334-114">Cette commande obtient toutes les propriétés du système d’exploitation de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6f334-114">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="6f334-115">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="6f334-115">PARAMETERS</span></span>

### <span data-ttu-id="6f334-116">-Propriété</span><span class="sxs-lookup"><span data-stu-id="6f334-116">-Property</span></span>

<span data-ttu-id="6f334-117">Spécifie, sous forme de tableau de chaînes, les propriétés de l’ordinateur que cette applet de commande affiche.</span><span class="sxs-lookup"><span data-stu-id="6f334-117">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="6f334-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6f334-118">CommonParameters</span></span>

<span data-ttu-id="6f334-119">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6f334-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6f334-120">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6f334-120">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6f334-121">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6f334-121">INPUTS</span></span>

### <span data-ttu-id="6f334-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6f334-122">System.String[]</span></span>

## <span data-ttu-id="6f334-123">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6f334-123">OUTPUTS</span></span>

### <span data-ttu-id="6f334-124">Microsoft. PowerShell. Management. ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="6f334-124">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="6f334-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6f334-125">NOTES</span></span>

<span data-ttu-id="6f334-126">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="6f334-126">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="6f334-127">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6f334-127">RELATED LINKS</span></span>
