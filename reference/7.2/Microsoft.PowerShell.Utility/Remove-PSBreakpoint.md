---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: a56b9041c0ae70def7df619f2a4d265cb631fe7b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595467"
---
# <span data-ttu-id="c1b0f-102">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c1b0f-102">Remove-PSBreakpoint</span></span>

## <span data-ttu-id="c1b0f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c1b0f-103">SYNOPSIS</span></span>
<span data-ttu-id="c1b0f-104">Supprime les points d'arrêt de la console active.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-104">Deletes breakpoints from the current console.</span></span>

## <span data-ttu-id="c1b0f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c1b0f-105">SYNTAX</span></span>

### <span data-ttu-id="c1b0f-106">Point d’arrêt (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c1b0f-106">Breakpoint (Default)</span></span>

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c1b0f-107">Id</span><span class="sxs-lookup"><span data-stu-id="c1b0f-107">Id</span></span>

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c1b0f-108">Description</span><span class="sxs-lookup"><span data-stu-id="c1b0f-108">DESCRIPTION</span></span>
<span data-ttu-id="c1b0f-109">L’applet de commande **Remove-PSBreakpoint** supprime un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-109">The **Remove-PSBreakpoint** cmdlet deletes a breakpoint.</span></span>
<span data-ttu-id="c1b0f-110">Entrez un objet de point d'arrêt ou un ID de point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-110">Enter a breakpoint object or a breakpoint ID.</span></span>

<span data-ttu-id="c1b0f-111">Quand vous supprimez un point d'arrêt, l'objet de point d'arrêt n'est plus disponible ou fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-111">When you remove a breakpoint, the breakpoint object is no longer available or functional.</span></span>
<span data-ttu-id="c1b0f-112">Si vous avez enregistré un objet de point d'arrêt dans une variable, la référence existe toujours, mais le point d'arrêt ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-112">If you have saved a breakpoint object in a variable, the reference still exists, but the breakpoint does not function.</span></span>

<span data-ttu-id="c1b0f-113">**Remove-PSBreakpoint** est l’une des différentes applets de commande conçues pour le débogage des scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-113">**Remove-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="c1b0f-114">Pour plus d’informations sur le débogueur PowerShell, consultez about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-114">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="c1b0f-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c1b0f-115">EXAMPLES</span></span>

### <span data-ttu-id="c1b0f-116">Exemple 1 : supprimer tous les points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="c1b0f-116">Example 1: Remove all breakpoints</span></span>

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

<span data-ttu-id="c1b0f-117">Cette commande supprime tous les points d'arrêt de la console active.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-117">This command deletes all of the breakpoints in the current console.</span></span>

### <span data-ttu-id="c1b0f-118">Exemple 2 : supprimer un point d’arrêt spécifié</span><span class="sxs-lookup"><span data-stu-id="c1b0f-118">Example 2: Remove a specified breakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

<span data-ttu-id="c1b0f-119">Cette commande supprime un point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-119">This command deletes a breakpoint.</span></span>

<span data-ttu-id="c1b0f-120">La première commande utilise l'applet de commande Set-PSBreakpoint pour créer un point d'arrêt sur la variable Name dans le script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-120">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Name variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="c1b0f-121">Ensuite, il enregistre l’objet de point d’arrêt dans la variable $B.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-121">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="c1b0f-122">La deuxième commande utilise l’applet de commande **Remove-PSBreakpoint** pour supprimer le nouveau point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-122">The second command uses the **Remove-PSBreakpoint** cmdlet to delete the new breakpoint.</span></span>
<span data-ttu-id="c1b0f-123">Elle utilise un opérateur de pipeline (|) pour envoyer l’objet de point d’arrêt dans la variable $B à l’applet de commande **Remove-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="c1b0f-123">It uses a pipeline operator (|) to send the breakpoint object in the $B variable to the **Remove-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="c1b0f-124">Si vous exécutez le script, cette commande s'exécute jusqu'à son achèvement sans interruption.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-124">As a result of this command, if you run the script, it runs to completion without stopping.</span></span>
<span data-ttu-id="c1b0f-125">En outre, l’applet de commande **PSBreakpoint** ne retourne pas ce point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-125">Also, the **Get-PSBreakpoint** cmdlet does not return this breakpoint.</span></span>

### <span data-ttu-id="c1b0f-126">Exemple 3 : supprimer un point d’arrêt par ID</span><span class="sxs-lookup"><span data-stu-id="c1b0f-126">Example 3: Remove a breakpoint by ID</span></span>

```
PS C:\> Remove-PSBreakpoint -Id 2
```

<span data-ttu-id="c1b0f-127">Cette commande supprime le point d'arrêt ayant l'ID de point d'arrêt 2.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-127">This command deletes the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="c1b0f-128">Exemple 4 : utiliser une fonction pour supprimer tous les points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="c1b0f-128">Example 4: Use a function to remove all breakpoints</span></span>

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

<span data-ttu-id="c1b0f-129">Cette simple fonction supprime tous les points d'arrêt de la console active.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-129">This simple function deletes all of the breakpoints in the current console.</span></span>
<span data-ttu-id="c1b0f-130">Elle utilise l'applet de commande Get-PSBreakpoint pour obtenir les points d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-130">It uses the Get-PSBreakpoint cmdlet to get the breakpoints.</span></span>
<span data-ttu-id="c1b0f-131">Ensuite, il utilise un opérateur de pipeline (|) pour envoyer les points d’arrêt à l’applet de commande **Remove-PSBreakpoint** , qui les supprime.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-131">Then, it uses a pipeline operator (|) to send the breakpoints to the **Remove-PSBreakpoint** cmdlet, which deletes them.</span></span>

<span data-ttu-id="c1b0f-132">Par conséquent, vous pouvez taper à `del-psb` la place de la commande la plus longue.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-132">As a result, you can type `del-psb` instead of the longer command.</span></span>

<span data-ttu-id="c1b0f-133">Pour enregistrer la fonction, ajoutez-la à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-133">To save the function, add it to your PowerShell profile.</span></span>

## <span data-ttu-id="c1b0f-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c1b0f-134">PARAMETERS</span></span>

### <span data-ttu-id="c1b0f-135">-Point d’arrêt</span><span class="sxs-lookup"><span data-stu-id="c1b0f-135">-Breakpoint</span></span>
<span data-ttu-id="c1b0f-136">Spécifie les points d'arrêt à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-136">Specifies the breakpoints to delete.</span></span>
<span data-ttu-id="c1b0f-137">Entrez une variable qui contient des objets de point d’arrêt ou une commande qui obtient des objets de point d’arrêt, comme une commande **PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="c1b0f-137">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a **Get-PSBreakpoint** command.</span></span>
<span data-ttu-id="c1b0f-138">Vous pouvez également diriger les objets point d’arrêt vers **Remove-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-138">You can also pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="c1b0f-139">-Id</span><span class="sxs-lookup"><span data-stu-id="c1b0f-139">-Id</span></span>
<span data-ttu-id="c1b0f-140">Spécifie les ID de point d’arrêt pour lesquels cette applet de commande supprime les points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-140">Specifies breakpoint IDs for which this cmdlet deletes breakpoints.</span></span>

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

### <span data-ttu-id="c1b0f-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c1b0f-141">-Confirm</span></span>
<span data-ttu-id="c1b0f-142">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c1b0f-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c1b0f-143">-WhatIf</span></span>
<span data-ttu-id="c1b0f-144">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c1b0f-145">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c1b0f-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c1b0f-146">CommonParameters</span></span>
<span data-ttu-id="c1b0f-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c1b0f-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c1b0f-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c1b0f-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c1b0f-149">INPUTS</span></span>

### <span data-ttu-id="c1b0f-150">System. Management. Automation. Breakpoint</span><span class="sxs-lookup"><span data-stu-id="c1b0f-150">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="c1b0f-151">Vous pouvez diriger les objets point d’arrêt vers **Remove-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-151">You can pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

## <span data-ttu-id="c1b0f-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c1b0f-152">OUTPUTS</span></span>

### <span data-ttu-id="c1b0f-153">None</span><span class="sxs-lookup"><span data-stu-id="c1b0f-153">None</span></span>
<span data-ttu-id="c1b0f-154">L'applet de commande ne génère pas de résultat.</span><span class="sxs-lookup"><span data-stu-id="c1b0f-154">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c1b0f-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c1b0f-155">NOTES</span></span>

## <span data-ttu-id="c1b0f-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c1b0f-156">RELATED LINKS</span></span>

[<span data-ttu-id="c1b0f-157">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c1b0f-157">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="c1b0f-158">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c1b0f-158">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="c1b0f-159">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c1b0f-159">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="c1b0f-160">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="c1b0f-160">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="c1b0f-161">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c1b0f-161">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

