---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: ddce638972aabb1afc1c8fe500df380dd01dff14
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596337"
---
# <span data-ttu-id="9b1ce-102">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="9b1ce-102">Set-TimeZone</span></span>

## <span data-ttu-id="9b1ce-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9b1ce-103">SYNOPSIS</span></span>
<span data-ttu-id="9b1ce-104">Définit le fuseau horaire système sur un fuseau horaire spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-104">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="9b1ce-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="9b1ce-105">SYNTAX</span></span>

### <span data-ttu-id="9b1ce-106">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9b1ce-106">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9b1ce-107">Id</span><span class="sxs-lookup"><span data-stu-id="9b1ce-107">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9b1ce-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="9b1ce-108">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9b1ce-109">Description</span><span class="sxs-lookup"><span data-stu-id="9b1ce-109">DESCRIPTION</span></span>

<span data-ttu-id="9b1ce-110">L' `Set-TimeZone` applet de commande définit le fuseau horaire système sur un fuseau horaire spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-110">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="9b1ce-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9b1ce-111">EXAMPLES</span></span>

### <span data-ttu-id="9b1ce-112">Exemple 1 : définir le fuseau horaire par ID</span><span class="sxs-lookup"><span data-stu-id="9b1ce-112">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="9b1ce-113">Cet exemple définit le fuseau horaire de l’ordinateur local à l’heure d’hiver russe.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-113">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

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

### <span data-ttu-id="9b1ce-114">Exemple 2 : définir le fuseau horaire par nom</span><span class="sxs-lookup"><span data-stu-id="9b1ce-114">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="9b1ce-115">Cet exemple définit le fuseau horaire de l’ordinateur local à l’heure d’hiver russe.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-115">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="9b1ce-116">Comme nous l’avons vu dans l’exemple précédent, l' **ID** et le **nom** du fuseau horaire ne correspondent pas toujours.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-116">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="9b1ce-117">Le paramètre **Name** doit correspondre aux propriétés **StandardName** ou **DaylightName** de l’objet **TimeZoneInfo** .</span><span class="sxs-lookup"><span data-stu-id="9b1ce-117">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="9b1ce-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9b1ce-118">PARAMETERS</span></span>

### <span data-ttu-id="9b1ce-119">-Id</span><span class="sxs-lookup"><span data-stu-id="9b1ce-119">-Id</span></span>

<span data-ttu-id="9b1ce-120">Spécifie l’ID du fuseau horaire défini par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-120">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="9b1ce-121">Vous pouvez obtenir une liste complète des ID de fuseau horaire en exécutant la commande suivante : `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="9b1ce-121">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

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

### <span data-ttu-id="9b1ce-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9b1ce-122">-InputObject</span></span>

<span data-ttu-id="9b1ce-123">Spécifie un objet **TimeZoneInfo** à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-123">Specifies a **TimeZoneInfo** object to use as input.</span></span>

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

### <span data-ttu-id="9b1ce-124">-Name</span><span class="sxs-lookup"><span data-stu-id="9b1ce-124">-Name</span></span>

<span data-ttu-id="9b1ce-125">Spécifie le nom du fuseau horaire défini par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-125">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="9b1ce-126">Vous pouvez obtenir une liste complète des noms de fuseau horaire en exécutant la commande suivante : `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="9b1ce-126">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

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

### <span data-ttu-id="9b1ce-127">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9b1ce-127">-PassThru</span></span>

<span data-ttu-id="9b1ce-128">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-128">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="9b1ce-129">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-129">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9b1ce-130">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9b1ce-130">-Confirm</span></span>

<span data-ttu-id="9b1ce-131">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-131">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9b1ce-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9b1ce-132">-WhatIf</span></span>

<span data-ttu-id="9b1ce-133">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-133">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9b1ce-134">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-134">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9b1ce-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b1ce-135">CommonParameters</span></span>

<span data-ttu-id="9b1ce-136">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b1ce-137">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9b1ce-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b1ce-138">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9b1ce-138">INPUTS</span></span>

### <span data-ttu-id="9b1ce-139">System. String, System. TimeZoneInfo, System. String</span><span class="sxs-lookup"><span data-stu-id="9b1ce-139">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="9b1ce-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9b1ce-140">OUTPUTS</span></span>

## <span data-ttu-id="9b1ce-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9b1ce-141">NOTES</span></span>

<span data-ttu-id="9b1ce-142">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="9b1ce-142">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="9b1ce-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9b1ce-143">RELATED LINKS</span></span>

[<span data-ttu-id="9b1ce-144">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="9b1ce-144">Get-TimeZone</span></span>](Get-TimeZone.md)
