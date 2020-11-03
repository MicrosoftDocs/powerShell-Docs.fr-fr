---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 9314aaf7c444f9a1159b301135d4130737daa439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204062"
---
# <span data-ttu-id="24ebe-103">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="24ebe-103">Clear-RecycleBin</span></span>

## <span data-ttu-id="24ebe-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="24ebe-104">SYNOPSIS</span></span>
<span data-ttu-id="24ebe-105">Efface le contenu d’une corbeille.</span><span class="sxs-lookup"><span data-stu-id="24ebe-105">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="24ebe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="24ebe-106">SYNTAX</span></span>

### <span data-ttu-id="24ebe-107">Tous</span><span class="sxs-lookup"><span data-stu-id="24ebe-107">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="24ebe-108">Description</span><span class="sxs-lookup"><span data-stu-id="24ebe-108">DESCRIPTION</span></span>

<span data-ttu-id="24ebe-109">L' `Clear-RecycleBin` applet de commande supprime le contenu de la corbeille d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="24ebe-109">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="24ebe-110">Cette action est semblable à l’utilisation de la **Corbeille vide** Windows.</span><span class="sxs-lookup"><span data-stu-id="24ebe-110">This action is like using Windows **Empty Recycle Bin** .</span></span>

## <span data-ttu-id="24ebe-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="24ebe-111">EXAMPLES</span></span>

### <span data-ttu-id="24ebe-112">1 : effacer toutes les corbeilles</span><span class="sxs-lookup"><span data-stu-id="24ebe-112">1: Clear all recycle bins</span></span>

<span data-ttu-id="24ebe-113">Dans cet exemple, toutes les corbeilles de l’ordinateur local sont effacées.</span><span class="sxs-lookup"><span data-stu-id="24ebe-113">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="24ebe-114">`Clear-RecycleBin` invite l’utilisateur à confirmer l’effacement de toutes les corbeilles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="24ebe-114">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="24ebe-115">2 : effacer une corbeille spécifiée</span><span class="sxs-lookup"><span data-stu-id="24ebe-115">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="24ebe-116">Cet exemple efface la Corbeille pour une lettre de lecteur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="24ebe-116">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="24ebe-117">`Clear-RecycleBin` utilise le paramètre **LettreLecteur** pour spécifier la corbeille sur le volume **C** .</span><span class="sxs-lookup"><span data-stu-id="24ebe-117">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="24ebe-118">L’utilisateur est invité à confirmer l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="24ebe-118">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="24ebe-119">3 : effacer toutes les corbeilles sans confirmation</span><span class="sxs-lookup"><span data-stu-id="24ebe-119">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="24ebe-120">Cet exemple ne demande pas de confirmation pour effacer les corbeilles de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="24ebe-120">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="24ebe-121">`Clear-RecycleBin` utilise le paramètre **force** et ne demande pas à l’utilisateur de confirmer l’effacement de toutes les corbeilles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="24ebe-121">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="24ebe-122">Une alternative consiste à remplacer `-Force` par `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="24ebe-122">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="24ebe-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="24ebe-123">PARAMETERS</span></span>

### <span data-ttu-id="24ebe-124">-LettreLecteur</span><span class="sxs-lookup"><span data-stu-id="24ebe-124">-DriveLetter</span></span>

<span data-ttu-id="24ebe-125">Spécifie la corbeille à effacer pour une lettre de lecteur unique ou un tableau de lettres de lecteur.</span><span class="sxs-lookup"><span data-stu-id="24ebe-125">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="24ebe-126">-Force</span><span class="sxs-lookup"><span data-stu-id="24ebe-126">-Force</span></span>

<span data-ttu-id="24ebe-127">Spécifie que l’utilisateur n’est pas invité à confirmer l’effacement d’une corbeille.</span><span class="sxs-lookup"><span data-stu-id="24ebe-127">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span>

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

### <span data-ttu-id="24ebe-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="24ebe-128">-Confirm</span></span>

<span data-ttu-id="24ebe-129">Demande une confirmation de l’utilisateur avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="24ebe-129">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="24ebe-130">L’utilisateur est invité à confirmer, même si le paramètre **Confirm** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="24ebe-130">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="24ebe-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="24ebe-131">-WhatIf</span></span>

<span data-ttu-id="24ebe-132">Montre ce qui se passe si `Clear-RecycleBin` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="24ebe-132">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="24ebe-133">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="24ebe-133">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="24ebe-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24ebe-134">CommonParameters</span></span>

<span data-ttu-id="24ebe-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="24ebe-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="24ebe-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="24ebe-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="24ebe-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="24ebe-137">INPUTS</span></span>

## <span data-ttu-id="24ebe-138">SORTIES</span><span class="sxs-lookup"><span data-stu-id="24ebe-138">OUTPUTS</span></span>

### <span data-ttu-id="24ebe-139">Aucun</span><span class="sxs-lookup"><span data-stu-id="24ebe-139">None</span></span>

## <span data-ttu-id="24ebe-140">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="24ebe-140">NOTES</span></span>

## <span data-ttu-id="24ebe-141">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="24ebe-141">RELATED LINKS</span></span>
