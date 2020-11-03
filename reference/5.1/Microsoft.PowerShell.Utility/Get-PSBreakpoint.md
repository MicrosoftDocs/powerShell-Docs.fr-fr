---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 030f96cc99e42e19e78e1be2c4f913889d0567b6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203266"
---
# <span data-ttu-id="0a710-103">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a710-103">Get-PSBreakpoint</span></span>

## <span data-ttu-id="0a710-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0a710-104">SYNOPSIS</span></span>
<span data-ttu-id="0a710-105">Obtient les points d'arrêt définis dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0a710-105">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="0a710-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a710-106">SYNTAX</span></span>

### <span data-ttu-id="0a710-107">Script (par défaut)</span><span class="sxs-lookup"><span data-stu-id="0a710-107">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0a710-108">Variable</span><span class="sxs-lookup"><span data-stu-id="0a710-108">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="0a710-109">Commande</span><span class="sxs-lookup"><span data-stu-id="0a710-109">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="0a710-110">Type</span><span class="sxs-lookup"><span data-stu-id="0a710-110">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="0a710-111">Id</span><span class="sxs-lookup"><span data-stu-id="0a710-111">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="0a710-112">Description</span><span class="sxs-lookup"><span data-stu-id="0a710-112">DESCRIPTION</span></span>

<span data-ttu-id="0a710-113">L’applet de commande **obtenir-PSBreakpoint** obtient les points d’arrêt définis dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0a710-113">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="0a710-114">Vous pouvez utiliser les paramètres d'applet de commande pour obtenir des points d'arrêt spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0a710-114">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="0a710-115">Un point d'arrêt est un point dans une commande ou un script auquel l'exécution s'arrête temporairement afin que vous puissiez examiner les instructions.</span><span class="sxs-lookup"><span data-stu-id="0a710-115">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="0a710-116">L’applet de commande **PSBreakpoint** est l’une des nombreuses cmdlets conçues pour déboguer les commandes et les scripts Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0a710-116">**Get-PSBreakpoint** is one of several cmdlets designed for debugging Windows PowerShell scripts and commands.</span></span> <span data-ttu-id="0a710-117">Pour plus d'informations sur le débogueur Windows PowerShell, consultez about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="0a710-117">For more information about the Windows PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="0a710-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0a710-118">EXAMPLES</span></span>

### <span data-ttu-id="0a710-119">Exemple 1 : obtenir tous les points d’arrêt pour tous les scripts et les fonctions</span><span class="sxs-lookup"><span data-stu-id="0a710-119">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="0a710-120">Cette commande obtient tous les points d'arrêt définis sur tous les scripts et fonctions de la session active.</span><span class="sxs-lookup"><span data-stu-id="0a710-120">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="0a710-121">Exemple 2 : récupérer des points d’arrêt par ID</span><span class="sxs-lookup"><span data-stu-id="0a710-121">Example 2: Get breakpoints by ID</span></span>

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="0a710-122">Cette commande obtient le point d'arrêt associé à l'ID de point d'arrêt 2.</span><span class="sxs-lookup"><span data-stu-id="0a710-122">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="0a710-123">Exemple 3 : diriger un ID vers Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a710-123">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="0a710-124">Ces commandes montrent comment obtenir un point d’arrêt en canalisant un ID de point d’arrêt vers **PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="0a710-124">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint** .</span></span>

<span data-ttu-id="0a710-125">La première commande utilise l'applet de commande Set-PSBreakpoint pour créer un point d'arrêt sur la fonction Increment dans le script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="0a710-125">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="0a710-126">Elle enregistre l’objet de point d’arrêt dans la variable $B.</span><span class="sxs-lookup"><span data-stu-id="0a710-126">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="0a710-127">La deuxième commande utilise l’opérateur point (.) pour récupérer la propriété ID de l’objet de point d’arrêt dans la variable $B.</span><span class="sxs-lookup"><span data-stu-id="0a710-127">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="0a710-128">Elle utilise un opérateur de pipeline (|) pour envoyer l’ID à l’applet de commande **PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="0a710-128">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="0a710-129">Par conséquent, la fonction **PSBreakpoint** obtient le point d’arrêt avec l’ID spécifié.</span><span class="sxs-lookup"><span data-stu-id="0a710-129">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="0a710-130">Exemple 4 : récupérer des points d’arrêt dans les fichiers de script spécifiés</span><span class="sxs-lookup"><span data-stu-id="0a710-130">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="0a710-131">Cette commande obtient tous les points d'arrêt des fichiers Sample.ps1 et SupportScript.ps1.</span><span class="sxs-lookup"><span data-stu-id="0a710-131">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="0a710-132">Cette commande n’obtient pas d’autres points d’arrêt qui peuvent être définis dans d’autres scripts ou sur des fonctions dans la session.</span><span class="sxs-lookup"><span data-stu-id="0a710-132">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="0a710-133">Exemple 5 : récupérer des points d’arrêt dans les applets de commande spécifiées</span><span class="sxs-lookup"><span data-stu-id="0a710-133">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="0a710-134">Cette commande obtient tous les points d'arrêt de commande définis sur les commandes Read-Host ou Write-Host dans le fichier Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="0a710-134">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="0a710-135">Exemple 6 : obtenir des points d’arrêt de commande dans un fichier spécifié</span><span class="sxs-lookup"><span data-stu-id="0a710-135">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="0a710-136">Cette commande obtient tous les points d'arrêt de commande du fichier Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="0a710-136">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="0a710-137">Exemple 7 : récupérer des points d’arrêt par variable</span><span class="sxs-lookup"><span data-stu-id="0a710-137">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="0a710-138">Cette commande obtient les points d’arrêt définis sur les variables $Index et $Swap dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0a710-138">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="0a710-139">Exemple 8 : obtenir tous les points d’arrêt de ligne et de variable dans un fichier</span><span class="sxs-lookup"><span data-stu-id="0a710-139">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="0a710-140">Cette commande obtient tous points d'arrêt de ligne et de variable du script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="0a710-140">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="0a710-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a710-141">PARAMETERS</span></span>

### <span data-ttu-id="0a710-142">-Command</span><span class="sxs-lookup"><span data-stu-id="0a710-142">-Command</span></span>

<span data-ttu-id="0a710-143">Spécifie un tableau de points d’arrêt de commande définis sur les noms de commande spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0a710-143">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="0a710-144">Entrez les noms de commande, par exemple, le nom d'une applet de commande ou d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="0a710-144">Enter the command names, such as the name of a cmdlet or function.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0a710-145">-Id</span><span class="sxs-lookup"><span data-stu-id="0a710-145">-Id</span></span>

<span data-ttu-id="0a710-146">Spécifie les ID de point d’arrêt que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="0a710-146">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="0a710-147">Entrez les ID dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="0a710-147">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="0a710-148">Vous pouvez également diriger les ID de point d’arrêt vers **PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="0a710-148">You can also pipe breakpoint IDs to **Get-PSBreakpoint** .</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0a710-149">-Script</span><span class="sxs-lookup"><span data-stu-id="0a710-149">-Script</span></span>

<span data-ttu-id="0a710-150">Spécifie un tableau de scripts qui contiennent les points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="0a710-150">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="0a710-151">Entrez le chemin d’accès (facultatif) et les noms d’un ou de plusieurs fichiers de script.</span><span class="sxs-lookup"><span data-stu-id="0a710-151">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="0a710-152">Si vous omettez le chemin d'accès, l'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="0a710-152">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0a710-153">-Type</span><span class="sxs-lookup"><span data-stu-id="0a710-153">-Type</span></span>

<span data-ttu-id="0a710-154">Spécifie un tableau de types de points d’arrêt que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="0a710-154">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="0a710-155">Entrez un ou plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="0a710-155">Enter one or more types.</span></span>
<span data-ttu-id="0a710-156">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="0a710-156">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0a710-157">Ligne</span><span class="sxs-lookup"><span data-stu-id="0a710-157">Line</span></span>
- <span data-ttu-id="0a710-158">Commande</span><span class="sxs-lookup"><span data-stu-id="0a710-158">Command</span></span>
- <span data-ttu-id="0a710-159">Variable</span><span class="sxs-lookup"><span data-stu-id="0a710-159">Variable</span></span>

<span data-ttu-id="0a710-160">Vous pouvez également diriger les types de point d’arrêt vers **PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="0a710-160">You can also pipe breakpoint types to **Get-PSBreakPoint** .</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0a710-161">-Variable</span><span class="sxs-lookup"><span data-stu-id="0a710-161">-Variable</span></span>

<span data-ttu-id="0a710-162">Spécifie un tableau de points d’arrêt de variable définis sur les noms de variable spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0a710-162">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="0a710-163">Entrez les noms de variable sans le signe dollar.</span><span class="sxs-lookup"><span data-stu-id="0a710-163">Enter the variable names without dollar signs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0a710-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a710-164">CommonParameters</span></span>

<span data-ttu-id="0a710-165">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0a710-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0a710-166">Pour plus d’informations, consultez about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0a710-166">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0a710-167">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0a710-167">INPUTS</span></span>

### <span data-ttu-id="0a710-168">System. Int32, Microsoft. PowerShell. Commands. BreakpointType</span><span class="sxs-lookup"><span data-stu-id="0a710-168">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="0a710-169">Vous pouvez diriger les ID de point d’arrêt et les types de point d’arrêt vers **PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="0a710-169">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint** .</span></span>

## <span data-ttu-id="0a710-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0a710-170">OUTPUTS</span></span>

### <span data-ttu-id="0a710-171">System. Management. Automation. Breakpoint</span><span class="sxs-lookup"><span data-stu-id="0a710-171">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="0a710-172">La méthode **PSBreakpoint retourne des** objets qui représentent les points d’arrêt de la session.</span><span class="sxs-lookup"><span data-stu-id="0a710-172">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="0a710-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0a710-173">NOTES</span></span>

* <span data-ttu-id="0a710-174">Vous pouvez utiliser **PSBreakpoint** ou son alias, « GBP ».</span><span class="sxs-lookup"><span data-stu-id="0a710-174">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="0a710-175">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0a710-175">RELATED LINKS</span></span>

[<span data-ttu-id="0a710-176">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a710-176">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="0a710-177">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a710-177">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="0a710-178">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="0a710-178">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="0a710-179">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a710-179">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="0a710-180">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a710-180">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
