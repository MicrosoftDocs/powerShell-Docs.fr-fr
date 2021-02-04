---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 6ac35c698cc1b4f2571becdee48b1f73f21249e7
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098717"
---
# <span data-ttu-id="c644b-102">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="c644b-102">Clear-RecycleBin</span></span>

## <span data-ttu-id="c644b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c644b-103">SYNOPSIS</span></span>
<span data-ttu-id="c644b-104">Efface le contenu d’une corbeille.</span><span class="sxs-lookup"><span data-stu-id="c644b-104">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="c644b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c644b-105">SYNTAX</span></span>

### <span data-ttu-id="c644b-106">Tous</span><span class="sxs-lookup"><span data-stu-id="c644b-106">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c644b-107">Description</span><span class="sxs-lookup"><span data-stu-id="c644b-107">DESCRIPTION</span></span>

<span data-ttu-id="c644b-108">L' `Clear-RecycleBin` applet de commande supprime le contenu de la corbeille d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c644b-108">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="c644b-109">Cette action est semblable à l’utilisation de la **Corbeille vide** Windows.</span><span class="sxs-lookup"><span data-stu-id="c644b-109">This action is like using Windows **Empty Recycle Bin**.</span></span>

<span data-ttu-id="c644b-110">Cette applet de commande a été ajoutée dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c644b-110">This cmdlet was readded in PowerShell 7.</span></span>

## <span data-ttu-id="c644b-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c644b-111">EXAMPLES</span></span>

### <span data-ttu-id="c644b-112">1 : effacer toutes les corbeilles</span><span class="sxs-lookup"><span data-stu-id="c644b-112">1: Clear all recycle bins</span></span>

<span data-ttu-id="c644b-113">Dans cet exemple, toutes les corbeilles de l’ordinateur local sont effacées.</span><span class="sxs-lookup"><span data-stu-id="c644b-113">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="c644b-114">`Clear-RecycleBin` invite l’utilisateur à confirmer l’effacement de toutes les corbeilles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c644b-114">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="c644b-115">2 : effacer une corbeille spécifiée</span><span class="sxs-lookup"><span data-stu-id="c644b-115">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="c644b-116">Cet exemple efface la Corbeille pour une lettre de lecteur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c644b-116">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="c644b-117">`Clear-RecycleBin` utilise le paramètre **LettreLecteur** pour spécifier la corbeille sur le volume **C** .</span><span class="sxs-lookup"><span data-stu-id="c644b-117">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="c644b-118">L’utilisateur est invité à confirmer l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="c644b-118">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="c644b-119">3 : effacer toutes les corbeilles sans confirmation</span><span class="sxs-lookup"><span data-stu-id="c644b-119">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="c644b-120">Cet exemple ne demande pas de confirmation pour effacer les corbeilles de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c644b-120">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="c644b-121">`Clear-RecycleBin` utilise le paramètre **force** et ne demande pas à l’utilisateur de confirmer l’effacement de toutes les corbeilles sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c644b-121">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="c644b-122">Une alternative consiste à remplacer `-Force` par `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="c644b-122">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="c644b-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c644b-123">PARAMETERS</span></span>

### <span data-ttu-id="c644b-124">-LettreLecteur</span><span class="sxs-lookup"><span data-stu-id="c644b-124">-DriveLetter</span></span>

<span data-ttu-id="c644b-125">Spécifie la corbeille à effacer pour une lettre de lecteur unique ou un tableau de lettres de lecteur.</span><span class="sxs-lookup"><span data-stu-id="c644b-125">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="c644b-126">-Force</span><span class="sxs-lookup"><span data-stu-id="c644b-126">-Force</span></span>

<span data-ttu-id="c644b-127">Spécifie que l’utilisateur n’est pas invité à confirmer l’effacement d’une corbeille.</span><span class="sxs-lookup"><span data-stu-id="c644b-127">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span> <span data-ttu-id="c644b-128">Le paramètre **force** remplace également les paramètres **WhatIf** et **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="c644b-128">The **Force** parameter also overrides the **WhatIf** and **Confirm** parameters.</span></span>

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

### <span data-ttu-id="c644b-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c644b-129">-Confirm</span></span>

<span data-ttu-id="c644b-130">Demande une confirmation de l’utilisateur avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c644b-130">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="c644b-131">L’utilisateur est invité à confirmer, même si le paramètre **Confirm** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="c644b-131">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="c644b-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c644b-132">-WhatIf</span></span>

<span data-ttu-id="c644b-133">Montre ce qui se passe si `Clear-RecycleBin` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="c644b-133">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="c644b-134">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="c644b-134">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="c644b-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c644b-135">CommonParameters</span></span>

<span data-ttu-id="c644b-136">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c644b-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c644b-137">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c644b-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c644b-138">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c644b-138">INPUTS</span></span>

## <span data-ttu-id="c644b-139">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c644b-139">OUTPUTS</span></span>

### <span data-ttu-id="c644b-140">Aucun</span><span class="sxs-lookup"><span data-stu-id="c644b-140">None</span></span>

## <span data-ttu-id="c644b-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c644b-141">NOTES</span></span>

<span data-ttu-id="c644b-142">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="c644b-142">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="c644b-143">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c644b-143">RELATED LINKS</span></span>
