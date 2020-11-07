---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: 3acf02b567c1fecd8089b12fac7c32b42abfec77
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343179"
---
# <span data-ttu-id="ec7f7-103">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="ec7f7-103">Set-TimeZone</span></span>

## <span data-ttu-id="ec7f7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ec7f7-104">SYNOPSIS</span></span>
<span data-ttu-id="ec7f7-105">Définit le fuseau horaire système sur un fuseau horaire spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-105">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="ec7f7-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ec7f7-106">SYNTAX</span></span>

### <span data-ttu-id="ec7f7-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ec7f7-107">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ec7f7-108">Id</span><span class="sxs-lookup"><span data-stu-id="ec7f7-108">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ec7f7-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="ec7f7-109">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ec7f7-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ec7f7-110">DESCRIPTION</span></span>

<span data-ttu-id="ec7f7-111">L' `Set-TimeZone` applet de commande définit le fuseau horaire système sur un fuseau horaire spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-111">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="ec7f7-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ec7f7-112">EXAMPLES</span></span>

### <span data-ttu-id="ec7f7-113">Exemple 1 : définir le fuseau horaire par ID</span><span class="sxs-lookup"><span data-stu-id="ec7f7-113">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="ec7f7-114">Cet exemple définit le fuseau horaire de l’ordinateur local à l’heure d’hiver russe.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-114">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

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

### <span data-ttu-id="ec7f7-115">Exemple 2 : définir le fuseau horaire par nom</span><span class="sxs-lookup"><span data-stu-id="ec7f7-115">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="ec7f7-116">Cet exemple définit le fuseau horaire de l’ordinateur local à l’heure d’hiver russe.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-116">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="ec7f7-117">Comme nous l’avons vu dans l’exemple précédent, l' **ID** et le **nom** du fuseau horaire ne correspondent pas toujours.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-117">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="ec7f7-118">Le paramètre **Name** doit correspondre aux propriétés **StandardName** ou **DaylightName** de l’objet **TimeZoneInfo** .</span><span class="sxs-lookup"><span data-stu-id="ec7f7-118">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="ec7f7-119">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="ec7f7-119">PARAMETERS</span></span>

### <span data-ttu-id="ec7f7-120">-Id</span><span class="sxs-lookup"><span data-stu-id="ec7f7-120">-Id</span></span>

<span data-ttu-id="ec7f7-121">Spécifie l’ID du fuseau horaire défini par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-121">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="ec7f7-122">Vous pouvez obtenir une liste complète des ID de fuseau horaire en exécutant la commande suivante : `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="ec7f7-122">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

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

### <span data-ttu-id="ec7f7-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ec7f7-123">-InputObject</span></span>

<span data-ttu-id="ec7f7-124">Spécifie un objet **TimeZoneInfo** à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-124">Specifies a **TimeZoneInfo** object to use as input.</span></span>

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

### <span data-ttu-id="ec7f7-125">-Name</span><span class="sxs-lookup"><span data-stu-id="ec7f7-125">-Name</span></span>

<span data-ttu-id="ec7f7-126">Spécifie le nom du fuseau horaire défini par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-126">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="ec7f7-127">Vous pouvez obtenir une liste complète des noms de fuseau horaire en exécutant la commande suivante : `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="ec7f7-127">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

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

### <span data-ttu-id="ec7f7-128">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ec7f7-128">-PassThru</span></span>

<span data-ttu-id="ec7f7-129">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-129">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="ec7f7-130">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-130">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ec7f7-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ec7f7-131">-Confirm</span></span>

<span data-ttu-id="ec7f7-132">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-132">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ec7f7-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ec7f7-133">-WhatIf</span></span>

<span data-ttu-id="ec7f7-134">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-134">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ec7f7-135">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-135">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ec7f7-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ec7f7-136">CommonParameters</span></span>

<span data-ttu-id="ec7f7-137">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ec7f7-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ec7f7-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ec7f7-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ec7f7-139">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ec7f7-139">INPUTS</span></span>

### <span data-ttu-id="ec7f7-140">System. String, System. TimeZoneInfo, System. String</span><span class="sxs-lookup"><span data-stu-id="ec7f7-140">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="ec7f7-141">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ec7f7-141">OUTPUTS</span></span>

## <span data-ttu-id="ec7f7-142">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ec7f7-142">NOTES</span></span>

## <span data-ttu-id="ec7f7-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ec7f7-143">RELATED LINKS</span></span>

[<span data-ttu-id="ec7f7-144">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="ec7f7-144">Get-TimeZone</span></span>](Get-TimeZone.md)
