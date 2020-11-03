---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: e8e50bb42d71aa69626e52a9bb2a8bd3cc77af64
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203333"
---
# <span data-ttu-id="a7373-103">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a7373-103">Disable-PSBreakpoint</span></span>

## <span data-ttu-id="a7373-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a7373-104">SYNOPSIS</span></span>
<span data-ttu-id="a7373-105">Désactive les points d'arrêt dans la console active.</span><span class="sxs-lookup"><span data-stu-id="a7373-105">Disables the breakpoints in the current console.</span></span>

## <span data-ttu-id="a7373-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a7373-106">SYNTAX</span></span>

### <span data-ttu-id="a7373-107">Point d’arrêt (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a7373-107">Breakpoint (Default)</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a7373-108">Id</span><span class="sxs-lookup"><span data-stu-id="a7373-108">Id</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a7373-109">Description</span><span class="sxs-lookup"><span data-stu-id="a7373-109">DESCRIPTION</span></span>
<span data-ttu-id="a7373-110">L’applet de commande **Disable-PSBreakpoint** désactive les points d’arrêt, ce qui garantit qu’ils ne sont pas atteints lors de l’exécution du script.</span><span class="sxs-lookup"><span data-stu-id="a7373-110">The **Disable-PSBreakpoint** cmdlet disables breakpoints, which assures that they are not hit when the script runs.</span></span>
<span data-ttu-id="a7373-111">Vous pouvez l'utiliser pour désactiver tous les points d'arrêt, ou vous pouvez spécifier des points d'arrêt en envoyant des objets de point d'arrêt ou des ID de point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="a7373-111">You can use it to disable all breakpoints, or you can specify breakpoints by submitting breakpoint objects or breakpoint IDs.</span></span>

<span data-ttu-id="a7373-112">Techniquement, cette applet de commande affecte la valeur False à la propriété Enabled d'un objet de point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="a7373-112">Technically, this cmdlet changes the value of the Enabled property of a breakpoint object to False.</span></span>
<span data-ttu-id="a7373-113">Pour réactiver un point d'arrêt, utilisez l'applet de commande Enable-PSBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="a7373-113">To re-enable a breakpoint, use the Enable-PSBreakpoint cmdlet.</span></span>
<span data-ttu-id="a7373-114">Les points d'arrêt sont activés par défaut quand vous les créez à l'aide de l'applet de commande Set-PSBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="a7373-114">Breakpoints are enabled by default when you create them by using the Set-PSBreakpoint cmdlet.</span></span>

<span data-ttu-id="a7373-115">Un point d'arrêt est un point dans un script auquel l'exécution s'arrête temporairement afin que vous puissiez examiner les instructions comprises dans le script.</span><span class="sxs-lookup"><span data-stu-id="a7373-115">A breakpoint is a point in a script where execution stops temporarily so that you can examine the instructions in the script.</span></span>
<span data-ttu-id="a7373-116">**Disable-PSBreakpoint** est l’une des différentes applets de commande conçues pour le débogage des scripts Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7373-116">**Disable-PSBreakpoint** is one of several cmdlets designed for debugging Windows PowerShell scripts.</span></span>
<span data-ttu-id="a7373-117">Pour plus d'informations sur le débogueur Windows PowerShell, consultez about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="a7373-117">For more information about the Windows PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="a7373-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a7373-118">EXAMPLES</span></span>

### <span data-ttu-id="a7373-119">Exemple 1 : définir un point d’arrêt et le désactiver</span><span class="sxs-lookup"><span data-stu-id="a7373-119">Example 1: Set a breakpoint and disable it</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

<span data-ttu-id="a7373-120">Ces commandes désactivent un point d'arrêt nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="a7373-120">These commands disable a newly-created breakpoint.</span></span>

<span data-ttu-id="a7373-121">La première commande utilise l’applet de commande Set-PSBreakpoint pour créer un point d’arrêt sur la variable *Name* dans le script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="a7373-121">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the *Name* variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="a7373-122">Ensuite, il enregistre l’objet de point d’arrêt dans la variable $B.</span><span class="sxs-lookup"><span data-stu-id="a7373-122">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="a7373-123">La deuxième commande utilise l’applet de commande **Disable-PSBreakpoint** pour désactiver le nouveau point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="a7373-123">The second command uses the **Disable-PSBreakpoint** cmdlet to disable the new breakpoint.</span></span>
<span data-ttu-id="a7373-124">Elle utilise un opérateur de pipeline (|) pour envoyer l’objet de point d’arrêt dans $B à l’applet de commande **Disable-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="a7373-124">It uses a pipeline operator (|) to send the breakpoint object in $B to the **Disable-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="a7373-125">En raison de cette commande, la valeur de la propriété Enabled de l’objet Breakpoint dans $B est false.</span><span class="sxs-lookup"><span data-stu-id="a7373-125">As a result of this command, the value of the Enabled property of the breakpoint object in $B is False.</span></span>

### <span data-ttu-id="a7373-126">Exemple 2 : désactiver un point d’arrêt</span><span class="sxs-lookup"><span data-stu-id="a7373-126">Example 2: Disable a breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Id 0
```

<span data-ttu-id="a7373-127">Cette commande désactive le point d'arrêt avec l'ID de point d'arrêt 0.</span><span class="sxs-lookup"><span data-stu-id="a7373-127">This command disables the breakpoint with breakpoint ID 0.</span></span>

### <span data-ttu-id="a7373-128">Exemple 3 : créer un point d’arrêt désactivé</span><span class="sxs-lookup"><span data-stu-id="a7373-128">Example 3: Create a disabled breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

<span data-ttu-id="a7373-129">Cette commande crée un nouveau point d'arrêt qui est désactivé jusqu'à ce que vous l'activiez.</span><span class="sxs-lookup"><span data-stu-id="a7373-129">This command creates a new breakpoint that is disabled until you enable it.</span></span>

<span data-ttu-id="a7373-130">Elle utilise l’applet de commande **Disable-PSBreakpoint** pour désactiver le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="a7373-130">It uses the **Disable-PSBreakpoint** cmdlet to disable the breakpoint.</span></span>
<span data-ttu-id="a7373-131">La valeur du paramètre de *point d’arrêt* est une commande Set-PSBreakpoint qui définit un nouveau point d’arrêt, génère un objet de point d’arrêt et enregistre l’objet dans la variable $B.</span><span class="sxs-lookup"><span data-stu-id="a7373-131">The value of the *Breakpoint* parameter is a Set-PSBreakpoint command that sets a new breakpoint, generates a breakpoint object, and saves the object in the $B variable.</span></span>

<span data-ttu-id="a7373-132">Les paramètres d'applet de commande qui acceptent des objets comme valeurs peuvent accepter une variable qui contient l'objet, ou une commande qui obtient ou génère l'objet.</span><span class="sxs-lookup"><span data-stu-id="a7373-132">Cmdlet parameters that take objects as their values can accept a variable that contains the object or a command that gets or generates the object.</span></span>
<span data-ttu-id="a7373-133">Dans ce cas, étant donné que **Set-PSBreakpoint** génère un objet de point d’arrêt, il peut être utilisé comme valeur du paramètre de *point d’arrêt* .</span><span class="sxs-lookup"><span data-stu-id="a7373-133">In this case, because **Set-PSBreakpoint** generates a breakpoint object, it can be used as the value of the *Breakpoint* parameter.</span></span>

<span data-ttu-id="a7373-134">La deuxième commande affiche l’objet de point d’arrêt dans la valeur de la variable $B.</span><span class="sxs-lookup"><span data-stu-id="a7373-134">The second command displays the breakpoint object in the value of the $B variable.</span></span>

### <span data-ttu-id="a7373-135">Exemple 4 : désactiver tous les points d’arrêt dans la console actuelle</span><span class="sxs-lookup"><span data-stu-id="a7373-135">Example 4: Disable all breakpoints in the current console</span></span>

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

<span data-ttu-id="a7373-136">Cette commande désactive tous les points d'arrêt dans la console active.</span><span class="sxs-lookup"><span data-stu-id="a7373-136">This command disables all breakpoints in the current console.</span></span>
<span data-ttu-id="a7373-137">Vous pouvez abréger cette commande comme suit : «GBP | DBP ".</span><span class="sxs-lookup"><span data-stu-id="a7373-137">You can abbreviate this command as: "gbp | dbp".</span></span>

## <span data-ttu-id="a7373-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a7373-138">PARAMETERS</span></span>

### <span data-ttu-id="a7373-139">-Point d’arrêt</span><span class="sxs-lookup"><span data-stu-id="a7373-139">-Breakpoint</span></span>
<span data-ttu-id="a7373-140">Spécifie les points d'arrêt à désactiver.</span><span class="sxs-lookup"><span data-stu-id="a7373-140">Specifies the breakpoints to disable.</span></span>
<span data-ttu-id="a7373-141">Entrez une variable qui contient des objets point d'arrêt ou une commande qui obtient des objets point d'arrêt (commande Get-PSBreakpoint, par exemple).</span><span class="sxs-lookup"><span data-stu-id="a7373-141">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a Get-PSBreakpoint command.</span></span>
<span data-ttu-id="a7373-142">Vous pouvez également diriger les objets de point d’arrêt vers l’applet de commande **Disable-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="a7373-142">You can also pipe breakpoint objects to the **Disable-PSBreakpoint** cmdlet.</span></span>

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

### <span data-ttu-id="a7373-143">-Id</span><span class="sxs-lookup"><span data-stu-id="a7373-143">-Id</span></span>
<span data-ttu-id="a7373-144">Désactive les points d'arrêt avec l'ID de point d'arrêt spécifié.</span><span class="sxs-lookup"><span data-stu-id="a7373-144">Disables the breakpoints with the specified breakpoint IDs.</span></span>
<span data-ttu-id="a7373-145">Entrez les ID ou une variable qui contient les ID.</span><span class="sxs-lookup"><span data-stu-id="a7373-145">Enter the IDs or a variable that contains the IDs.</span></span>
<span data-ttu-id="a7373-146">Vous ne pouvez pas diriger d’ID vers **Disable-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="a7373-146">You cannot pipe IDs to **Disable-PSBreakpoint** .</span></span>

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

### <span data-ttu-id="a7373-147">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a7373-147">-PassThru</span></span>
<span data-ttu-id="a7373-148">Retourne un objet qui représente les points d'arrêt activés.</span><span class="sxs-lookup"><span data-stu-id="a7373-148">Returns an object representing the enabled breakpoints.</span></span>
<span data-ttu-id="a7373-149">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="a7373-149">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a7373-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a7373-150">-Confirm</span></span>
<span data-ttu-id="a7373-151">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a7373-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a7373-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a7373-152">-WhatIf</span></span>
<span data-ttu-id="a7373-153">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a7373-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a7373-154">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a7373-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a7373-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7373-155">CommonParameters</span></span>
<span data-ttu-id="a7373-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a7373-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7373-157">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a7373-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7373-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a7373-158">INPUTS</span></span>

### <span data-ttu-id="a7373-159">System. Management. Automation. Breakpoint</span><span class="sxs-lookup"><span data-stu-id="a7373-159">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="a7373-160">Vous pouvez diriger un objet point d’arrêt vers **Disable-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="a7373-160">You can pipe a breakpoint object to **Disable-PSBreakpoint** .</span></span>

## <span data-ttu-id="a7373-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a7373-161">OUTPUTS</span></span>

### <span data-ttu-id="a7373-162">Aucun ou System. Management. Automation. Breakpoint</span><span class="sxs-lookup"><span data-stu-id="a7373-162">None or System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="a7373-163">Quand vous utilisez le paramètre *PassThru* , **Disable-PSBreakpoint** retourne un objet qui représente le point d’arrêt désactivé.</span><span class="sxs-lookup"><span data-stu-id="a7373-163">When you use the *PassThru* parameter, **Disable-PSBreakpoint** returns an object that represents the disabled breakpoint.</span></span>
<span data-ttu-id="a7373-164">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a7373-164">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a7373-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a7373-165">NOTES</span></span>

## <span data-ttu-id="a7373-166">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a7373-166">RELATED LINKS</span></span>

[<span data-ttu-id="a7373-167">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a7373-167">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="a7373-168">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a7373-168">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="a7373-169">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="a7373-169">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="a7373-170">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a7373-170">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="a7373-171">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a7373-171">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
