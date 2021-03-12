---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: 99f9372ddd1a58b0c374e915eec436cda817bb67
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196044"
---
# <span data-ttu-id="4c1c9-102">Get-Uptime</span><span class="sxs-lookup"><span data-stu-id="4c1c9-102">Get-Uptime</span></span>

## <span data-ttu-id="4c1c9-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4c1c9-103">SYNOPSIS</span></span>
<span data-ttu-id="4c1c9-104">Obtient le **TimeSpan** depuis le dernier démarrage.</span><span class="sxs-lookup"><span data-stu-id="4c1c9-104">Get the **TimeSpan** since last boot.</span></span>

## <span data-ttu-id="4c1c9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4c1c9-105">SYNTAX</span></span>

### <span data-ttu-id="4c1c9-106">TimeSpan (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="4c1c9-106">Timespan (Default)</span></span>

```
Get-Uptime [<CommonParameters>]
```

### <span data-ttu-id="4c1c9-107">Sa</span><span class="sxs-lookup"><span data-stu-id="4c1c9-107">Since</span></span>

```
Get-Uptime [-Since] [<CommonParameters>]
```

## <span data-ttu-id="4c1c9-108">Description</span><span class="sxs-lookup"><span data-stu-id="4c1c9-108">DESCRIPTION</span></span>

<span data-ttu-id="4c1c9-109">Cette applet de commande renvoie la durée écoulée depuis le dernier démarrage du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4c1c9-109">This cmdlet returns the time elapsed since the last boot of the operating system.</span></span>

<span data-ttu-id="4c1c9-110">L' `Get-Uptime` applet de commande a été introduite dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="4c1c9-110">The `Get-Uptime` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="4c1c9-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4c1c9-111">EXAMPLES</span></span>

### <span data-ttu-id="4c1c9-112">Exemple 1 : afficher l’heure depuis le dernier démarrage</span><span class="sxs-lookup"><span data-stu-id="4c1c9-112">Example 1 - Show time since last boot</span></span>

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### <span data-ttu-id="4c1c9-113">Exemple 2 : afficher l’heure du dernier démarrage</span><span class="sxs-lookup"><span data-stu-id="4c1c9-113">Example 2 - Show the time of the last boot</span></span>

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## <span data-ttu-id="4c1c9-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4c1c9-114">PARAMETERS</span></span>

### <span data-ttu-id="4c1c9-115">-Depuis</span><span class="sxs-lookup"><span data-stu-id="4c1c9-115">-Since</span></span>

<span data-ttu-id="4c1c9-116">Force l’applet de commande à retourner un objet **DateTime** représentant l’heure du dernier démarrage du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4c1c9-116">Cause the cmdlet to return a **DateTime** object representing the last time that the operating system was booted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c1c9-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c1c9-117">CommonParameters</span></span>

<span data-ttu-id="4c1c9-118">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4c1c9-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4c1c9-119">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4c1c9-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c1c9-120">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4c1c9-120">INPUTS</span></span>

### <span data-ttu-id="4c1c9-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="4c1c9-121">None</span></span>

## <span data-ttu-id="4c1c9-122">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4c1c9-122">OUTPUTS</span></span>

### <span data-ttu-id="4c1c9-123">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="4c1c9-123">System.TimeSpan</span></span>

<span data-ttu-id="4c1c9-124">Il s’agit du type de retour par défaut quand aucun paramètre n’est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4c1c9-124">This is the default return type when no parameters are used.</span></span>

### <span data-ttu-id="4c1c9-125">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="4c1c9-125">System.DateTime</span></span>

<span data-ttu-id="4c1c9-126">Ce type est retourné lors de l’utilisation du paramètre **depuis** .</span><span class="sxs-lookup"><span data-stu-id="4c1c9-126">This type is returned when using the **Since** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="4c1c9-127">Si le démarrage rapide de Windows est activé, Windows ne met pas à jour la valeur stockée dans **LastBootUpTime**.</span><span class="sxs-lookup"><span data-stu-id="4c1c9-127">If Windows fast startup is enabled, Windows does not update the value stored in **LastBootUpTime**.</span></span> <span data-ttu-id="4c1c9-128">Pour désactiver le démarrage rapide, exécutez la commande suivante : `Powercfg -h off` .</span><span class="sxs-lookup"><span data-stu-id="4c1c9-128">To disable fast startup, run the following command: `Powercfg -h off`.</span></span>
>
> <span data-ttu-id="4c1c9-129">Pour plus d’informations sur le démarrage rapide de Windows, consultez la rubrique [distinction du démarrage rapide de la mise en veille prolongée](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).</span><span class="sxs-lookup"><span data-stu-id="4c1c9-129">For more information about Windows fast startup, see [Distinguishing Fast Startup from Wake-from-Hibernation](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).</span></span>

## <span data-ttu-id="4c1c9-130">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4c1c9-130">NOTES</span></span>

<span data-ttu-id="4c1c9-131">Sur Windows, la valeur retournée est la même que la propriété **LastBootUpTime** de la classe **Win32_OperatingSystem** dans WMI.</span><span class="sxs-lookup"><span data-stu-id="4c1c9-131">On Windows, the value returned is the same as the **LastBootUpTime** property of the **Win32_OperatingSystem** class in WMI.</span></span>

## <span data-ttu-id="4c1c9-132">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4c1c9-132">RELATED LINKS</span></span>

[<span data-ttu-id="4c1c9-133">Win32_OperatingSystem</span><span class="sxs-lookup"><span data-stu-id="4c1c9-133">Win32_OperatingSystem</span></span>](/windows/win32/cimwin32prov/win32-operatingsystem#properties)

