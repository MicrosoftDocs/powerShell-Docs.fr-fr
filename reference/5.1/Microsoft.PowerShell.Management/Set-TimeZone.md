---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: bfeb838ca8f67bac7c257ef3485eff9b55753933
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203497"
---
# <span data-ttu-id="70515-103">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="70515-103">Set-TimeZone</span></span>

## <span data-ttu-id="70515-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="70515-104">SYNOPSIS</span></span>
<span data-ttu-id="70515-105">Définit le fuseau horaire système sur un fuseau horaire spécifié.</span><span class="sxs-lookup"><span data-stu-id="70515-105">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="70515-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="70515-106">SYNTAX</span></span>

### <span data-ttu-id="70515-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="70515-107">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="70515-108">Id</span><span class="sxs-lookup"><span data-stu-id="70515-108">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="70515-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="70515-109">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="70515-110">Description</span><span class="sxs-lookup"><span data-stu-id="70515-110">DESCRIPTION</span></span>

<span data-ttu-id="70515-111">L' `Set-TimeZone` applet de commande définit le fuseau horaire système sur un fuseau horaire spécifié.</span><span class="sxs-lookup"><span data-stu-id="70515-111">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="70515-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="70515-112">EXAMPLES</span></span>

### <span data-ttu-id="70515-113">Exemple 1 : définir le fuseau horaire par ID</span><span class="sxs-lookup"><span data-stu-id="70515-113">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="70515-114">Cet exemple définit le fuseau horaire de l’ordinateur local à l’heure d’hiver russe.</span><span class="sxs-lookup"><span data-stu-id="70515-114">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Id "Russian Standard Time" -PassThru
```

```Output
Id                         : Russian Standard Time
DisplayName                : (UTC+03:00) Moscow, St. Petersburg
StandardName               : Russia TZ 2 Standard Time
DaylightName               : Russia TZ 2 Daylight Time
BaseUtcOffset              : 03:00:00
SupportsDaylightSavingTime : True
```

### <span data-ttu-id="70515-115">Exemple 2 : définir le fuseau horaire par nom</span><span class="sxs-lookup"><span data-stu-id="70515-115">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="70515-116">Cet exemple définit le fuseau horaire de l’ordinateur local à l’heure d’hiver russe.</span><span class="sxs-lookup"><span data-stu-id="70515-116">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="70515-117">Comme nous l’avons vu dans l’exemple précédent, l' **ID** et le **nom** du fuseau horaire ne correspondent pas toujours.</span><span class="sxs-lookup"><span data-stu-id="70515-117">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="70515-118">Le paramètre **Name** doit correspondre aux propriétés **StandardName** ou **DaylightName** de l’objet **TimeZoneInfo** .</span><span class="sxs-lookup"><span data-stu-id="70515-118">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="70515-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="70515-119">PARAMETERS</span></span>

### <span data-ttu-id="70515-120">-Id</span><span class="sxs-lookup"><span data-stu-id="70515-120">-Id</span></span>

<span data-ttu-id="70515-121">Spécifie l’ID du fuseau horaire défini par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="70515-121">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="70515-122">Vous pouvez obtenir une liste complète des ID de fuseau horaire en exécutant la commande suivante : `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="70515-122">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="70515-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="70515-123">-InputObject</span></span>

<span data-ttu-id="70515-124">Spécifie un objet **TimeZoneInfo** à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="70515-124">Specifies a **TimeZoneInfo** object to use as input.</span></span>

```yaml
Type: System.TimeZoneInfo
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="70515-125">-Name</span><span class="sxs-lookup"><span data-stu-id="70515-125">-Name</span></span>

<span data-ttu-id="70515-126">Spécifie le nom du fuseau horaire défini par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="70515-126">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="70515-127">Vous pouvez obtenir une liste complète des noms de fuseau horaire en exécutant la commande suivante : `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="70515-127">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70515-128">-PassThru</span><span class="sxs-lookup"><span data-stu-id="70515-128">-PassThru</span></span>

<span data-ttu-id="70515-129">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="70515-129">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="70515-130">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="70515-130">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70515-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="70515-131">-Confirm</span></span>

<span data-ttu-id="70515-132">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="70515-132">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70515-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="70515-133">-WhatIf</span></span>

<span data-ttu-id="70515-134">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="70515-134">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="70515-135">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="70515-135">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70515-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="70515-136">CommonParameters</span></span>

<span data-ttu-id="70515-137">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="70515-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="70515-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="70515-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="70515-139">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="70515-139">INPUTS</span></span>

### <span data-ttu-id="70515-140">System. String, System. TimeZoneInfo, System. String</span><span class="sxs-lookup"><span data-stu-id="70515-140">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="70515-141">SORTIES</span><span class="sxs-lookup"><span data-stu-id="70515-141">OUTPUTS</span></span>

## <span data-ttu-id="70515-142">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="70515-142">NOTES</span></span>

## <span data-ttu-id="70515-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="70515-143">RELATED LINKS</span></span>

[<span data-ttu-id="70515-144">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="70515-144">Get-TimeZone</span></span>](Get-TimeZone.md)
