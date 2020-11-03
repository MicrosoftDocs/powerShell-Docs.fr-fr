---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: 876ce5ff32863281ba9bc1ae94ece8b0a12c9efd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201473"
---
# <span data-ttu-id="7f4f5-103">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="7f4f5-103">Get-ComputerInfo</span></span>

## <span data-ttu-id="7f4f5-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7f4f5-104">SYNOPSIS</span></span>
<span data-ttu-id="7f4f5-105">Obtient un objet consolidé des propriétés système et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7f4f5-105">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="7f4f5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f4f5-106">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7f4f5-107">Description</span><span class="sxs-lookup"><span data-stu-id="7f4f5-107">DESCRIPTION</span></span>

<span data-ttu-id="7f4f5-108">L' `Get-ComputerInfo` applet de commande obtient un objet consolidé des propriétés système et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7f4f5-108">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="7f4f5-109">Cette applet de commande a été introduite dans Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="7f4f5-109">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="7f4f5-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7f4f5-110">EXAMPLES</span></span>

### <span data-ttu-id="7f4f5-111">Exemple 1 : récupération de toutes les propriétés de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="7f4f5-111">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="7f4f5-112">Cette commande obtient toutes les propriétés système et système d’exploitation de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7f4f5-112">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="7f4f5-113">Exemple 2 : récupération de toutes les propriétés du système d’exploitation de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="7f4f5-113">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="7f4f5-114">Cette commande obtient toutes les propriétés du système d’exploitation de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7f4f5-114">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="7f4f5-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7f4f5-115">PARAMETERS</span></span>

### <span data-ttu-id="7f4f5-116">-Propriété</span><span class="sxs-lookup"><span data-stu-id="7f4f5-116">-Property</span></span>

<span data-ttu-id="7f4f5-117">Spécifie, sous forme de tableau de chaînes, les propriétés de l’ordinateur que cette applet de commande affiche.</span><span class="sxs-lookup"><span data-stu-id="7f4f5-117">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

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

### <span data-ttu-id="7f4f5-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f4f5-118">CommonParameters</span></span>

<span data-ttu-id="7f4f5-119">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f4f5-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f4f5-120">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="7f4f5-120">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7f4f5-121">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7f4f5-121">INPUTS</span></span>

### <span data-ttu-id="7f4f5-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="7f4f5-122">System.String[]</span></span>

## <span data-ttu-id="7f4f5-123">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7f4f5-123">OUTPUTS</span></span>

### <span data-ttu-id="7f4f5-124">Microsoft. PowerShell. Management. ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="7f4f5-124">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="7f4f5-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7f4f5-125">NOTES</span></span>

## <span data-ttu-id="7f4f5-126">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7f4f5-126">RELATED LINKS</span></span>
