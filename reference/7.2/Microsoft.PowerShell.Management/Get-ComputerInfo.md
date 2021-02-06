---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: abc820bd6f8f5c8cd8c6301aacee268c82161d7e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597350"
---
# <span data-ttu-id="bd21c-102">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="bd21c-102">Get-ComputerInfo</span></span>

## <span data-ttu-id="bd21c-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bd21c-103">SYNOPSIS</span></span>
<span data-ttu-id="bd21c-104">Obtient un objet consolidé des propriétés système et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="bd21c-104">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="bd21c-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="bd21c-105">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="bd21c-106">Description</span><span class="sxs-lookup"><span data-stu-id="bd21c-106">DESCRIPTION</span></span>

<span data-ttu-id="bd21c-107">L' `Get-ComputerInfo` applet de commande obtient un objet consolidé des propriétés système et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="bd21c-107">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="bd21c-108">Cette applet de commande a été introduite dans Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="bd21c-108">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="bd21c-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bd21c-109">EXAMPLES</span></span>

### <span data-ttu-id="bd21c-110">Exemple 1 : récupération de toutes les propriétés de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="bd21c-110">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="bd21c-111">Cette commande obtient toutes les propriétés système et système d’exploitation de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bd21c-111">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="bd21c-112">Exemple 2 : récupération de toutes les propriétés du système d’exploitation de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="bd21c-112">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="bd21c-113">Cette commande obtient toutes les propriétés du système d’exploitation de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bd21c-113">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="bd21c-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd21c-114">PARAMETERS</span></span>

### <span data-ttu-id="bd21c-115">-Propriété</span><span class="sxs-lookup"><span data-stu-id="bd21c-115">-Property</span></span>

<span data-ttu-id="bd21c-116">Spécifie, sous forme de tableau de chaînes, les propriétés de l’ordinateur que cette applet de commande affiche.</span><span class="sxs-lookup"><span data-stu-id="bd21c-116">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

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

### <span data-ttu-id="bd21c-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd21c-117">CommonParameters</span></span>

<span data-ttu-id="bd21c-118">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd21c-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd21c-119">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="bd21c-119">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bd21c-120">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bd21c-120">INPUTS</span></span>

### <span data-ttu-id="bd21c-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="bd21c-121">System.String[]</span></span>

## <span data-ttu-id="bd21c-122">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bd21c-122">OUTPUTS</span></span>

### <span data-ttu-id="bd21c-123">Microsoft. PowerShell. Management. ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="bd21c-123">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="bd21c-124">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bd21c-124">NOTES</span></span>

<span data-ttu-id="bd21c-125">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="bd21c-125">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="bd21c-126">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bd21c-126">RELATED LINKS</span></span>
