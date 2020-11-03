---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: 0d50fe8359f54b8aaac9482d162cc0865b1824fe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202858"
---
# <span data-ttu-id="e3b27-103">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="e3b27-103">Remove-PSBreakpoint</span></span>

## <span data-ttu-id="e3b27-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e3b27-104">SYNOPSIS</span></span>
<span data-ttu-id="e3b27-105">Supprime les points d'arrêt de la console active.</span><span class="sxs-lookup"><span data-stu-id="e3b27-105">Deletes breakpoints from the current console.</span></span>

## <span data-ttu-id="e3b27-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e3b27-106">SYNTAX</span></span>

### <span data-ttu-id="e3b27-107">Point d’arrêt (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e3b27-107">Breakpoint (Default)</span></span>

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e3b27-108">Id</span><span class="sxs-lookup"><span data-stu-id="e3b27-108">Id</span></span>

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e3b27-109">Description</span><span class="sxs-lookup"><span data-stu-id="e3b27-109">DESCRIPTION</span></span>
<span data-ttu-id="e3b27-110">L’applet de commande **Remove-PSBreakpoint** supprime un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="e3b27-110">The **Remove-PSBreakpoint** cmdlet deletes a breakpoint.</span></span>
<span data-ttu-id="e3b27-111">Entrez un objet de point d'arrêt ou un ID de point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="e3b27-111">Enter a breakpoint object or a breakpoint ID.</span></span>

<span data-ttu-id="e3b27-112">Quand vous supprimez un point d'arrêt, l'objet de point d'arrêt n'est plus disponible ou fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="e3b27-112">When you remove a breakpoint, the breakpoint object is no longer available or functional.</span></span>
<span data-ttu-id="e3b27-113">Si vous avez enregistré un objet de point d'arrêt dans une variable, la référence existe toujours, mais le point d'arrêt ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="e3b27-113">If you have saved a breakpoint object in a variable, the reference still exists, but the breakpoint does not function.</span></span>

<span data-ttu-id="e3b27-114">**Remove-PSBreakpoint** est l’une des différentes applets de commande conçues pour le débogage des scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3b27-114">**Remove-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="e3b27-115">Pour plus d’informations sur le débogueur PowerShell, consultez about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="e3b27-115">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="e3b27-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e3b27-116">EXAMPLES</span></span>

### <span data-ttu-id="e3b27-117">Exemple 1 : supprimer tous les points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="e3b27-117">Example 1: Remove all breakpoints</span></span>

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

<span data-ttu-id="e3b27-118">Cette commande supprime tous les points d'arrêt de la console active.</span><span class="sxs-lookup"><span data-stu-id="e3b27-118">This command deletes all of the breakpoints in the current console.</span></span>

### <span data-ttu-id="e3b27-119">Exemple 2 : supprimer un point d’arrêt spécifié</span><span class="sxs-lookup"><span data-stu-id="e3b27-119">Example 2: Remove a specified breakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

<span data-ttu-id="e3b27-120">Cette commande supprime un point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="e3b27-120">This command deletes a breakpoint.</span></span>

<span data-ttu-id="e3b27-121">La première commande utilise l'applet de commande Set-PSBreakpoint pour créer un point d'arrêt sur la variable Name dans le script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="e3b27-121">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Name variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="e3b27-122">Ensuite, il enregistre l’objet de point d’arrêt dans la variable $B.</span><span class="sxs-lookup"><span data-stu-id="e3b27-122">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="e3b27-123">La deuxième commande utilise l’applet de commande **Remove-PSBreakpoint** pour supprimer le nouveau point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="e3b27-123">The second command uses the **Remove-PSBreakpoint** cmdlet to delete the new breakpoint.</span></span>
<span data-ttu-id="e3b27-124">Elle utilise un opérateur de pipeline (|) pour envoyer l’objet de point d’arrêt dans la variable $B à l’applet de commande **Remove-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="e3b27-124">It uses a pipeline operator (|) to send the breakpoint object in the $B variable to the **Remove-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="e3b27-125">Si vous exécutez le script, cette commande s'exécute jusqu'à son achèvement sans interruption.</span><span class="sxs-lookup"><span data-stu-id="e3b27-125">As a result of this command, if you run the script, it runs to completion without stopping.</span></span>
<span data-ttu-id="e3b27-126">En outre, l’applet de commande **PSBreakpoint** ne retourne pas ce point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="e3b27-126">Also, the **Get-PSBreakpoint** cmdlet does not return this breakpoint.</span></span>

### <span data-ttu-id="e3b27-127">Exemple 3 : supprimer un point d’arrêt par ID</span><span class="sxs-lookup"><span data-stu-id="e3b27-127">Example 3: Remove a breakpoint by ID</span></span>

```
PS C:\> Remove-PSBreakpoint -Id 2
```

<span data-ttu-id="e3b27-128">Cette commande supprime le point d'arrêt ayant l'ID de point d'arrêt 2.</span><span class="sxs-lookup"><span data-stu-id="e3b27-128">This command deletes the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="e3b27-129">Exemple 4 : utiliser une fonction pour supprimer tous les points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="e3b27-129">Example 4: Use a function to remove all breakpoints</span></span>

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

<span data-ttu-id="e3b27-130">Cette simple fonction supprime tous les points d'arrêt de la console active.</span><span class="sxs-lookup"><span data-stu-id="e3b27-130">This simple function deletes all of the breakpoints in the current console.</span></span>
<span data-ttu-id="e3b27-131">Elle utilise l'applet de commande Get-PSBreakpoint pour obtenir les points d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="e3b27-131">It uses the Get-PSBreakpoint cmdlet to get the breakpoints.</span></span>
<span data-ttu-id="e3b27-132">Ensuite, il utilise un opérateur de pipeline (|) pour envoyer les points d’arrêt à l’applet de commande **Remove-PSBreakpoint** , qui les supprime.</span><span class="sxs-lookup"><span data-stu-id="e3b27-132">Then, it uses a pipeline operator (|) to send the breakpoints to the **Remove-PSBreakpoint** cmdlet, which deletes them.</span></span>

<span data-ttu-id="e3b27-133">Par conséquent, vous pouvez taper à `del-psb` la place de la commande la plus longue.</span><span class="sxs-lookup"><span data-stu-id="e3b27-133">As a result, you can type `del-psb` instead of the longer command.</span></span>

<span data-ttu-id="e3b27-134">Pour enregistrer la fonction, ajoutez-la à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3b27-134">To save the function, add it to your PowerShell profile.</span></span>

## <span data-ttu-id="e3b27-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e3b27-135">PARAMETERS</span></span>

### <span data-ttu-id="e3b27-136">-Point d’arrêt</span><span class="sxs-lookup"><span data-stu-id="e3b27-136">-Breakpoint</span></span>
<span data-ttu-id="e3b27-137">Spécifie les points d'arrêt à supprimer.</span><span class="sxs-lookup"><span data-stu-id="e3b27-137">Specifies the breakpoints to delete.</span></span>
<span data-ttu-id="e3b27-138">Entrez une variable qui contient des objets de point d’arrêt ou une commande qui obtient des objets de point d’arrêt, comme une commande **PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="e3b27-138">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a **Get-PSBreakpoint** command.</span></span>
<span data-ttu-id="e3b27-139">Vous pouvez également diriger les objets point d’arrêt vers **Remove-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="e3b27-139">You can also pipe breakpoint objects to **Remove-PSBreakpoint** .</span></span>

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e3b27-140">-Id</span><span class="sxs-lookup"><span data-stu-id="e3b27-140">-Id</span></span>
<span data-ttu-id="e3b27-141">Spécifie les ID de point d’arrêt pour lesquels cette applet de commande supprime les points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="e3b27-141">Specifies breakpoint IDs for which this cmdlet deletes breakpoints.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e3b27-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e3b27-142">-Confirm</span></span>
<span data-ttu-id="e3b27-143">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e3b27-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e3b27-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e3b27-144">-WhatIf</span></span>
<span data-ttu-id="e3b27-145">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e3b27-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e3b27-146">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e3b27-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e3b27-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3b27-147">CommonParameters</span></span>
<span data-ttu-id="e3b27-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e3b27-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3b27-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e3b27-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e3b27-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e3b27-150">INPUTS</span></span>

### <span data-ttu-id="e3b27-151">System. Management. Automation. Breakpoint</span><span class="sxs-lookup"><span data-stu-id="e3b27-151">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="e3b27-152">Vous pouvez diriger les objets point d’arrêt vers **Remove-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="e3b27-152">You can pipe breakpoint objects to **Remove-PSBreakpoint** .</span></span>

## <span data-ttu-id="e3b27-153">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e3b27-153">OUTPUTS</span></span>

### <span data-ttu-id="e3b27-154">Aucun</span><span class="sxs-lookup"><span data-stu-id="e3b27-154">None</span></span>
<span data-ttu-id="e3b27-155">L'applet de commande ne génère pas de résultat.</span><span class="sxs-lookup"><span data-stu-id="e3b27-155">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e3b27-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e3b27-156">NOTES</span></span>

## <span data-ttu-id="e3b27-157">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e3b27-157">RELATED LINKS</span></span>

[<span data-ttu-id="e3b27-158">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="e3b27-158">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="e3b27-159">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="e3b27-159">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="e3b27-160">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="e3b27-160">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="e3b27-161">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="e3b27-161">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="e3b27-162">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="e3b27-162">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
