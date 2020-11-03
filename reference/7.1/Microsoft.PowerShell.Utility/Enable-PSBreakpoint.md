---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 547739d6482e86bc558245bc5c5f04eddcfe9614
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204210"
---
# <span data-ttu-id="3ad28-103">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3ad28-103">Enable-PSBreakpoint</span></span>

## <span data-ttu-id="3ad28-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3ad28-104">SYNOPSIS</span></span>
<span data-ttu-id="3ad28-105">Active les points d'arrêt dans la console active.</span><span class="sxs-lookup"><span data-stu-id="3ad28-105">Enables the breakpoints in the current console.</span></span>

## <span data-ttu-id="3ad28-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ad28-106">SYNTAX</span></span>

### <span data-ttu-id="3ad28-107">ID (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3ad28-107">Id (Default)</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3ad28-108">Point d’arrêt</span><span class="sxs-lookup"><span data-stu-id="3ad28-108">Breakpoint</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="3ad28-109">Description</span><span class="sxs-lookup"><span data-stu-id="3ad28-109">DESCRIPTION</span></span>

<span data-ttu-id="3ad28-110">L' `Enable-PSBreakpoint` applet de commande réactive les points d’arrêt désactivés.</span><span class="sxs-lookup"><span data-stu-id="3ad28-110">The `Enable-PSBreakpoint` cmdlet re-enables disabled breakpoints.</span></span> <span data-ttu-id="3ad28-111">Vous pouvez l’utiliser pour activer tous les points d’arrêt, ou des points d’arrêt spécifiques en fournissant des objets ou des ID de point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="3ad28-111">You can use it to enable all breakpoints, or specific breakpoints by providing breakpoint objects or IDs.</span></span>

<span data-ttu-id="3ad28-112">Un point d’arrêt est un point dans un script où l’exécution s’arrête temporairement afin que vous puissiez examiner l’état du script.</span><span class="sxs-lookup"><span data-stu-id="3ad28-112">A breakpoint is a point in a script where execution stops temporarily so that you can examine the state of the script.</span></span> <span data-ttu-id="3ad28-113">Les points d’arrêt nouvellement créés sont activés automatiquement, mais peuvent être désactivés à l’aide de `Disable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-113">Newly created breakpoints are automatically enabled, but can be disabled using `Disable-PSBreakpoint`.</span></span>

<span data-ttu-id="3ad28-114">Techniquement, cette applet de commande modifie la valeur de la propriété **Enabled** d’un objet point d’arrêt en **true** .</span><span class="sxs-lookup"><span data-stu-id="3ad28-114">Technically, this cmdlet changes the value of the **Enabled** property of a breakpoint object to **True** .</span></span>

<span data-ttu-id="3ad28-115">`Enable-PSBreakpoint` est l’une des différentes applets de commande conçues pour le débogage de scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ad28-115">`Enable-PSBreakpoint` is one of several cmdlets designed for debugging PowerShell scripts.</span></span> <span data-ttu-id="3ad28-116">Pour plus d’informations sur le débogueur PowerShell, consultez [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span><span class="sxs-lookup"><span data-stu-id="3ad28-116">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="3ad28-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3ad28-117">EXAMPLES</span></span>

### <span data-ttu-id="3ad28-118">Exemple 1 : activer tous les points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="3ad28-118">Example 1: Enable all breakpoints</span></span>

<span data-ttu-id="3ad28-119">Cet exemple active tous les points d’arrêt de la session active.</span><span class="sxs-lookup"><span data-stu-id="3ad28-119">This example enables all breakpoints in the current session.</span></span>

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

<span data-ttu-id="3ad28-120">À l’aide des alias, cet exemple peut être abrégé en `gbp | ebp` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-120">Using aliases, this example can be abbreviated as `gbp | ebp`.</span></span>

### <span data-ttu-id="3ad28-121">Exemple 2 : activer les points d’arrêt par ID</span><span class="sxs-lookup"><span data-stu-id="3ad28-121">Example 2: Enable breakpoints by ID</span></span>

<span data-ttu-id="3ad28-122">Cet exemple active plusieurs points d’arrêt à l’aide de leurs ID de point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="3ad28-122">This example enables multiple breakpoints using their breakpoint IDs.</span></span>

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### <span data-ttu-id="3ad28-123">Exemple 3 : activer un point d’arrêt désactivé</span><span class="sxs-lookup"><span data-stu-id="3ad28-123">Example 3: Enable a disabled breakpoint</span></span>

<span data-ttu-id="3ad28-124">Cet exemple réactive un point d’arrêt qui a été désactivé.</span><span class="sxs-lookup"><span data-stu-id="3ad28-124">This example re-enables a breakpoint that has been disabled.</span></span>

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="3ad28-125">`Set-PSBreakpoint` crée un point d’arrêt sur la variable **Name** dans le `Sample.ps1` script en enregistrant l’objet point d’arrêt dans la `$B` variable.</span><span class="sxs-lookup"><span data-stu-id="3ad28-125">`Set-PSBreakpoint` creates a breakpoint on the **Name** variable in the `Sample.ps1` script saving the breakpoint object in the `$B` variable.</span></span> <span data-ttu-id="3ad28-126">Le paramètre **PassThru** affiche la valeur de la propriété **Enabled** du point d’arrêt est **false** .</span><span class="sxs-lookup"><span data-stu-id="3ad28-126">The **PassThru** parameter displays the value of the **Enabled** property of the breakpoint is **False** .</span></span>

<span data-ttu-id="3ad28-127">`Enable-PSBreakpoint` réactive le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="3ad28-127">`Enable-PSBreakpoint` re-enables the breakpoint.</span></span> <span data-ttu-id="3ad28-128">Là encore, en utilisant le paramètre **PassThru** , nous voyons que la valeur de la propriété **Enabled** est **true** .</span><span class="sxs-lookup"><span data-stu-id="3ad28-128">Again, using the **PassThru** parameter we see that the value of the **Enabled** property is **True** .</span></span>

### <span data-ttu-id="3ad28-129">Exemple 4 : activer des points d’arrêt à l’aide d’une variable</span><span class="sxs-lookup"><span data-stu-id="3ad28-129">Example 4: Enable breakpoints using a variable</span></span>

<span data-ttu-id="3ad28-130">Cet exemple active un ensemble de points d’arrêt à l’aide des objets de point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="3ad28-130">This example enables a set of breakpoints using the breakpoint objects.</span></span>

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

<span data-ttu-id="3ad28-131">`Get-PSBreakpoint` Obtient les points d’arrêt et les enregistre dans la `$B` variable.</span><span class="sxs-lookup"><span data-stu-id="3ad28-131">`Get-PSBreakpoint` gets the breakpoints and saves them in the `$B` variable.</span></span> <span data-ttu-id="3ad28-132">L’utilisation du paramètre de **point d’arrêt** `Enable-PSBreakpoint` active les points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="3ad28-132">Using the **Breakpoint** parameter, `Enable-PSBreakpoint` enables the breakpoints.</span></span>

<span data-ttu-id="3ad28-133">Cet exemple est équivalent à l’exécution de `Enable-PSBreakpoint -Id 3, 5` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-133">This example is equivalent to running `Enable-PSBreakpoint -Id 3, 5`.</span></span>

## <span data-ttu-id="3ad28-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3ad28-134">PARAMETERS</span></span>

### <span data-ttu-id="3ad28-135">-Point d’arrêt</span><span class="sxs-lookup"><span data-stu-id="3ad28-135">-Breakpoint</span></span>

<span data-ttu-id="3ad28-136">Spécifie les points d'arrêt à activer.</span><span class="sxs-lookup"><span data-stu-id="3ad28-136">Specifies the breakpoints to enable.</span></span> <span data-ttu-id="3ad28-137">Fournissez une variable contenant des points d’arrêt ou une commande qui obtient des objets de point d’arrêt, tels que `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-137">Provide a variable containing breakpoints or a command that gets breakpoint objects, such as `Get-PSBreakpoint`.</span></span> <span data-ttu-id="3ad28-138">Vous pouvez également diriger les objets de point d’arrêt vers `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-138">You can also pipe breakpoint objects to `Enable-PSBreakpoint`.</span></span>

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

### <span data-ttu-id="3ad28-139">-Id</span><span class="sxs-lookup"><span data-stu-id="3ad28-139">-Id</span></span>

<span data-ttu-id="3ad28-140">Spécifie les numéros d' **identification** des points d’arrêt à activer.</span><span class="sxs-lookup"><span data-stu-id="3ad28-140">Specifies the **Id** numbers of the breakpoints to enable.</span></span> <span data-ttu-id="3ad28-141">La valeur par défaut est tous les points d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="3ad28-141">The default value is all breakpoints.</span></span>
<span data-ttu-id="3ad28-142">Fournissez l' **ID** par numéro ou dans une variable.</span><span class="sxs-lookup"><span data-stu-id="3ad28-142">Provide the **Id** by number or in a variable.</span></span> <span data-ttu-id="3ad28-143">Vous ne pouvez pas diriger les numéros d' **identification** vers `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-143">You can't pipe **Id** numbers to `Enable-PSBreakpoint`.</span></span> <span data-ttu-id="3ad28-144">Pour Rechercher l' **ID** d’un point d’arrêt, utilisez l’applet de commande `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-144">To find the **Id** of a breakpoint, use the `Get-PSBreakpoint` cmdlet.</span></span>

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

### <span data-ttu-id="3ad28-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="3ad28-145">-PassThru</span></span>

<span data-ttu-id="3ad28-146">Retourne un objet représentant le point d’arrêt en cours d’activation.</span><span class="sxs-lookup"><span data-stu-id="3ad28-146">Returns an object representing the breakpoint being enabled.</span></span> <span data-ttu-id="3ad28-147">Par défaut, cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="3ad28-147">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="3ad28-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3ad28-148">-Confirm</span></span>

<span data-ttu-id="3ad28-149">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3ad28-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3ad28-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3ad28-150">-WhatIf</span></span>

<span data-ttu-id="3ad28-151">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3ad28-151">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3ad28-152">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="3ad28-152">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="3ad28-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ad28-153">CommonParameters</span></span>

<span data-ttu-id="3ad28-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3ad28-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ad28-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3ad28-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3ad28-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3ad28-156">INPUTS</span></span>

### <span data-ttu-id="3ad28-157">System. Management. Automation. Breakpoint</span><span class="sxs-lookup"><span data-stu-id="3ad28-157">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="3ad28-158">Vous pouvez diriger un objet point d’arrêt vers `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-158">You can pipe a breakpoint object to `Enable-PSBreakpoint`.</span></span>

## <span data-ttu-id="3ad28-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3ad28-159">OUTPUTS</span></span>

### <span data-ttu-id="3ad28-160">Aucun ou System. Management. Automation. Breakpoint</span><span class="sxs-lookup"><span data-stu-id="3ad28-160">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="3ad28-161">Quand vous utilisez le paramètre **PassThru** , `Enable-PSBreakpoint` retourne un objet de point d’arrêt qui représente ce point d’arrêt qui a été activé.</span><span class="sxs-lookup"><span data-stu-id="3ad28-161">When you use the **PassThru** parameter, `Enable-PSBreakpoint` returns a breakpoint object that represents that breakpoint that was enabled.</span></span> <span data-ttu-id="3ad28-162">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="3ad28-162">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="3ad28-163">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3ad28-163">NOTES</span></span>

- <span data-ttu-id="3ad28-164">L' `Enable-PSBreakpoint` applet de commande ne génère pas d’erreur si vous essayez d’activer un point d’arrêt déjà activé.</span><span class="sxs-lookup"><span data-stu-id="3ad28-164">The `Enable-PSBreakpoint` cmdlet doesn't generate an error if you try to enable a breakpoint that is already enabled.</span></span> <span data-ttu-id="3ad28-165">Par conséquent, vous pouvez activer tous les points d'arrêt sans erreur, même si seuls quelques-uns sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="3ad28-165">As such, you can enable all breakpoints without error, even when only a few are disabled.</span></span>

- <span data-ttu-id="3ad28-166">Les points d’arrêt sont activés lorsque vous les créez à l’aide de l’applet de commande `Set-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="3ad28-166">Breakpoints are enabled when you create them by using the `Set-PSBreakpoint` cmdlet.</span></span> <span data-ttu-id="3ad28-167">Vous n’avez pas besoin d’activer les points d’arrêt nouvellement créés.</span><span class="sxs-lookup"><span data-stu-id="3ad28-167">You don't need to enable newly created breakpoints.</span></span>

## <span data-ttu-id="3ad28-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3ad28-168">RELATED LINKS</span></span>

[<span data-ttu-id="3ad28-169">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3ad28-169">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="3ad28-170">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3ad28-170">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="3ad28-171">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="3ad28-171">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="3ad28-172">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3ad28-172">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="3ad28-173">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3ad28-173">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

