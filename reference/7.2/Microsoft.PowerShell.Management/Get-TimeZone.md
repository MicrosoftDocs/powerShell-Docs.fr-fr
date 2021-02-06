---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 22034eeac6988478a5f2ff87b2582cc5e1acc1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599151"
---
# <span data-ttu-id="ef877-102">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="ef877-102">Get-TimeZone</span></span>

## <span data-ttu-id="ef877-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ef877-103">SYNOPSIS</span></span>
<span data-ttu-id="ef877-104">Obtient le fuseau horaire actuel ou une liste de fuseaux horaires disponibles.</span><span class="sxs-lookup"><span data-stu-id="ef877-104">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="ef877-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ef877-105">SYNTAX</span></span>

### <span data-ttu-id="ef877-106">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ef877-106">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ef877-107">Id</span><span class="sxs-lookup"><span data-stu-id="ef877-107">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="ef877-108">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="ef877-108">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="ef877-109">Description</span><span class="sxs-lookup"><span data-stu-id="ef877-109">DESCRIPTION</span></span>

<span data-ttu-id="ef877-110">L’applet de commande **« obtenir-TimeZone »** obtient le fuseau horaire actuel ou une liste des fuseaux horaires disponibles.</span><span class="sxs-lookup"><span data-stu-id="ef877-110">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="ef877-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ef877-111">EXAMPLES</span></span>

### <span data-ttu-id="ef877-112">Exemple 1 : récupération du fuseau horaire actuel</span><span class="sxs-lookup"><span data-stu-id="ef877-112">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="ef877-113">Cette commande obtient le fuseau horaire actuel.</span><span class="sxs-lookup"><span data-stu-id="ef877-113">This command gets the current time zone.</span></span>

### <span data-ttu-id="ef877-114">Exemple 2 : obtenir les fuseaux horaires qui correspondent à une chaîne spécifiée</span><span class="sxs-lookup"><span data-stu-id="ef877-114">Example 2: Get time zones that match a specified string</span></span>

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

<span data-ttu-id="ef877-115">Cette commande obtient tous les fuseaux horaires qui correspondent au caractère générique spécifié.</span><span class="sxs-lookup"><span data-stu-id="ef877-115">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="ef877-116">Exemple 3 : récupération de tous les fuseaux horaires disponibles</span><span class="sxs-lookup"><span data-stu-id="ef877-116">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="ef877-117">Cette commande obtient tous les fuseaux horaires disponibles.</span><span class="sxs-lookup"><span data-stu-id="ef877-117">This command gets all available time zones.</span></span>

## <span data-ttu-id="ef877-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef877-118">PARAMETERS</span></span>

### <span data-ttu-id="ef877-119">-Id</span><span class="sxs-lookup"><span data-stu-id="ef877-119">-Id</span></span>

<span data-ttu-id="ef877-120">Spécifie, sous la forme d’un tableau de chaînes, l’ID ou les ID des fuseaux horaires que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="ef877-120">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="ef877-121">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="ef877-121">-ListAvailable</span></span>

<span data-ttu-id="ef877-122">Indique que cette applet de commande obtient tous les fuseaux horaires disponibles.</span><span class="sxs-lookup"><span data-stu-id="ef877-122">Indicates that this cmdlet gets all available time zones.</span></span>

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

### <span data-ttu-id="ef877-123">-Name</span><span class="sxs-lookup"><span data-stu-id="ef877-123">-Name</span></span>

<span data-ttu-id="ef877-124">Spécifie, sous forme de tableau de chaînes, le nom ou les noms des fuseaux horaires que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="ef877-124">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="ef877-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef877-125">CommonParameters</span></span>

<span data-ttu-id="ef877-126">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef877-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef877-127">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ef877-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef877-128">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ef877-128">INPUTS</span></span>

### <span data-ttu-id="ef877-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ef877-129">System.String[]</span></span>

## <span data-ttu-id="ef877-130">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ef877-130">OUTPUTS</span></span>

### <span data-ttu-id="ef877-131">System. TimeZoneInfo []</span><span class="sxs-lookup"><span data-stu-id="ef877-131">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="ef877-132">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ef877-132">NOTES</span></span>

<span data-ttu-id="ef877-133">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="ef877-133">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="ef877-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ef877-134">RELATED LINKS</span></span>

[<span data-ttu-id="ef877-135">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="ef877-135">Set-TimeZone</span></span>](Set-TimeZone.md)
