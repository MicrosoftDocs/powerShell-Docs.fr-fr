---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 4131232e7afb2e0a213bbe11f5da7ee3a0071a59
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344301"
---
# <span data-ttu-id="d02d3-103">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="d02d3-103">Clear-RecycleBin</span></span>

## <span data-ttu-id="d02d3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d02d3-104">SYNOPSIS</span></span>
<span data-ttu-id="d02d3-105">Efface le contenu d’une corbeille.</span><span class="sxs-lookup"><span data-stu-id="d02d3-105">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="d02d3-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d02d3-106">SYNTAX</span></span>

### <span data-ttu-id="d02d3-107">Tous</span><span class="sxs-lookup"><span data-stu-id="d02d3-107">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d02d3-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d02d3-108">DESCRIPTION</span></span>

<span data-ttu-id="d02d3-109">L' `Clear-RecycleBin` applet de commande supprime le contenu de la corbeille d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d02d3-109">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="d02d3-110">Cette action est semblable à l’utilisation de la **Corbeille vide** Windows.</span><span class="sxs-lookup"><span data-stu-id="d02d3-110">This action is like using Windows **Empty Recycle Bin**.</span></span>

<span data-ttu-id="d02d3-111">Cette applet de commande a été ajoutée dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="d02d3-111">This cmdlet was readded in PowerShell 7.</span></span>

## <span data-ttu-id="d02d3-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d02d3-112">EXAMPLES</span></span>

### <span data-ttu-id="d02d3-113">1 : effacer toutes les corbeilles</span><span class="sxs-lookup"><span data-stu-id="d02d3-113">1: Clear all recycle bins</span></span>

<span data-ttu-id="d02d3-114">Dans cet exemple, toutes les corbeilles de l’ordinateur local sont effacées.</span><span class="sxs-lookup"><span data-stu-id="d02d3-114">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="d02d3-115">`Clear-RecycleBin` invite l’utilisateur à confirmer l’effacement de toutes les corbeilles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d02d3-115">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="d02d3-116">2 : effacer une corbeille spécifiée</span><span class="sxs-lookup"><span data-stu-id="d02d3-116">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="d02d3-117">Cet exemple efface la Corbeille pour une lettre de lecteur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d02d3-117">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="d02d3-118">`Clear-RecycleBin` utilise le paramètre **LettreLecteur** pour spécifier la corbeille sur le volume **C** .</span><span class="sxs-lookup"><span data-stu-id="d02d3-118">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="d02d3-119">L’utilisateur est invité à confirmer l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="d02d3-119">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="d02d3-120">3 : effacer toutes les corbeilles sans confirmation</span><span class="sxs-lookup"><span data-stu-id="d02d3-120">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="d02d3-121">Cet exemple ne demande pas de confirmation pour effacer les corbeilles de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d02d3-121">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="d02d3-122">`Clear-RecycleBin` utilise le paramètre **force** et ne demande pas à l’utilisateur de confirmer l’effacement de toutes les corbeilles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d02d3-122">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="d02d3-123">Une alternative consiste à remplacer `-Force` par `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="d02d3-123">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="d02d3-124">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="d02d3-124">PARAMETERS</span></span>

### <span data-ttu-id="d02d3-125">-LettreLecteur</span><span class="sxs-lookup"><span data-stu-id="d02d3-125">-DriveLetter</span></span>

<span data-ttu-id="d02d3-126">Spécifie la corbeille à effacer pour une lettre de lecteur unique ou un tableau de lettres de lecteur.</span><span class="sxs-lookup"><span data-stu-id="d02d3-126">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="d02d3-127">-Force</span><span class="sxs-lookup"><span data-stu-id="d02d3-127">-Force</span></span>

<span data-ttu-id="d02d3-128">Spécifie que l’utilisateur n’est pas invité à confirmer l’effacement d’une corbeille.</span><span class="sxs-lookup"><span data-stu-id="d02d3-128">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span>

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

### <span data-ttu-id="d02d3-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d02d3-129">-Confirm</span></span>

<span data-ttu-id="d02d3-130">Demande une confirmation de l’utilisateur avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d02d3-130">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="d02d3-131">L’utilisateur est invité à confirmer, même si le paramètre **Confirm** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="d02d3-131">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="d02d3-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d02d3-132">-WhatIf</span></span>

<span data-ttu-id="d02d3-133">Montre ce qui se passe si `Clear-RecycleBin` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d02d3-133">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="d02d3-134">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d02d3-134">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="d02d3-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d02d3-135">CommonParameters</span></span>

<span data-ttu-id="d02d3-136">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d02d3-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d02d3-137">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d02d3-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d02d3-138">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d02d3-138">INPUTS</span></span>

## <span data-ttu-id="d02d3-139">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d02d3-139">OUTPUTS</span></span>

### <span data-ttu-id="d02d3-140">Aucun</span><span class="sxs-lookup"><span data-stu-id="d02d3-140">None</span></span>

## <span data-ttu-id="d02d3-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d02d3-141">NOTES</span></span>

<span data-ttu-id="d02d3-142">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="d02d3-142">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="d02d3-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d02d3-143">RELATED LINKS</span></span>
