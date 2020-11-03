---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: ae937a7e72b2b1f2d5f455358a0034717e3e4634
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203985"
---
# <span data-ttu-id="f0244-103">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="f0244-103">Get-TimeZone</span></span>

## <span data-ttu-id="f0244-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f0244-104">SYNOPSIS</span></span>
<span data-ttu-id="f0244-105">Obtient le fuseau horaire actuel ou une liste de fuseaux horaires disponibles.</span><span class="sxs-lookup"><span data-stu-id="f0244-105">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="f0244-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0244-106">SYNTAX</span></span>

### <span data-ttu-id="f0244-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f0244-107">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f0244-108">Id</span><span class="sxs-lookup"><span data-stu-id="f0244-108">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f0244-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="f0244-109">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="f0244-110">Description</span><span class="sxs-lookup"><span data-stu-id="f0244-110">DESCRIPTION</span></span>

<span data-ttu-id="f0244-111">L’applet de commande **« obtenir-TimeZone »** obtient le fuseau horaire actuel ou une liste des fuseaux horaires disponibles.</span><span class="sxs-lookup"><span data-stu-id="f0244-111">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="f0244-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f0244-112">EXAMPLES</span></span>

### <span data-ttu-id="f0244-113">Exemple 1 : récupération du fuseau horaire actuel</span><span class="sxs-lookup"><span data-stu-id="f0244-113">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="f0244-114">Cette commande obtient le fuseau horaire actuel.</span><span class="sxs-lookup"><span data-stu-id="f0244-114">This command gets the current time zone.</span></span>

### <span data-ttu-id="f0244-115">Exemple 2 : obtenir les fuseaux horaires qui correspondent à une chaîne spécifiée</span><span class="sxs-lookup"><span data-stu-id="f0244-115">Example 2: Get time zones that match a specified string</span></span>

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

<span data-ttu-id="f0244-116">Cette commande obtient tous les fuseaux horaires qui correspondent au caractère générique spécifié.</span><span class="sxs-lookup"><span data-stu-id="f0244-116">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="f0244-117">Exemple 3 : récupération de tous les fuseaux horaires disponibles</span><span class="sxs-lookup"><span data-stu-id="f0244-117">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="f0244-118">Cette commande obtient tous les fuseaux horaires disponibles.</span><span class="sxs-lookup"><span data-stu-id="f0244-118">This command gets all available time zones.</span></span>

## <span data-ttu-id="f0244-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0244-119">PARAMETERS</span></span>

### <span data-ttu-id="f0244-120">-Id</span><span class="sxs-lookup"><span data-stu-id="f0244-120">-Id</span></span>

<span data-ttu-id="f0244-121">Spécifie, sous la forme d’un tableau de chaînes, l’ID ou les ID des fuseaux horaires que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="f0244-121">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0244-122">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="f0244-122">-ListAvailable</span></span>

<span data-ttu-id="f0244-123">Indique que cette applet de commande obtient tous les fuseaux horaires disponibles.</span><span class="sxs-lookup"><span data-stu-id="f0244-123">Indicates that this cmdlet gets all available time zones.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0244-124">-Name</span><span class="sxs-lookup"><span data-stu-id="f0244-124">-Name</span></span>

<span data-ttu-id="f0244-125">Spécifie, sous forme de tableau de chaînes, le nom ou les noms des fuseaux horaires que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="f0244-125">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f0244-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0244-126">CommonParameters</span></span>

<span data-ttu-id="f0244-127">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0244-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0244-128">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0244-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0244-129">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f0244-129">INPUTS</span></span>

### <span data-ttu-id="f0244-130">System.String[]</span><span class="sxs-lookup"><span data-stu-id="f0244-130">System.String[]</span></span>

## <span data-ttu-id="f0244-131">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f0244-131">OUTPUTS</span></span>

### <span data-ttu-id="f0244-132">System. TimeZoneInfo []</span><span class="sxs-lookup"><span data-stu-id="f0244-132">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="f0244-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f0244-133">NOTES</span></span>

## <span data-ttu-id="f0244-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f0244-134">RELATED LINKS</span></span>

[<span data-ttu-id="f0244-135">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="f0244-135">Set-TimeZone</span></span>](Set-TimeZone.md)
