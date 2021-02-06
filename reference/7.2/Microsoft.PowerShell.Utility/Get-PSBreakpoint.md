---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 78691b806fe68aaa8d9e502d28e6f3967867f95b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595475"
---
# <span data-ttu-id="51638-102">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="51638-102">Get-PSBreakpoint</span></span>

## <span data-ttu-id="51638-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="51638-103">SYNOPSIS</span></span>
<span data-ttu-id="51638-104">Obtient les points d'arrêt définis dans la session active.</span><span class="sxs-lookup"><span data-stu-id="51638-104">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="51638-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="51638-105">SYNTAX</span></span>

### <span data-ttu-id="51638-106">Script (par défaut)</span><span class="sxs-lookup"><span data-stu-id="51638-106">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="51638-107">Variable</span><span class="sxs-lookup"><span data-stu-id="51638-107">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="51638-108">Commande</span><span class="sxs-lookup"><span data-stu-id="51638-108">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="51638-109">Type</span><span class="sxs-lookup"><span data-stu-id="51638-109">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="51638-110">Id</span><span class="sxs-lookup"><span data-stu-id="51638-110">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="51638-111">Description</span><span class="sxs-lookup"><span data-stu-id="51638-111">DESCRIPTION</span></span>

<span data-ttu-id="51638-112">L’applet de commande **obtenir-PSBreakpoint** obtient les points d’arrêt définis dans la session active.</span><span class="sxs-lookup"><span data-stu-id="51638-112">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="51638-113">Vous pouvez utiliser les paramètres d'applet de commande pour obtenir des points d'arrêt spécifiques.</span><span class="sxs-lookup"><span data-stu-id="51638-113">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="51638-114">Un point d'arrêt est un point dans une commande ou un script auquel l'exécution s'arrête temporairement afin que vous puissiez examiner les instructions.</span><span class="sxs-lookup"><span data-stu-id="51638-114">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="51638-115">La commande **PSBreakpoint** est l’une des différentes applets de commande conçues pour déboguer les scripts et les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51638-115">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="51638-116">Pour plus d’informations sur le débogueur PowerShell, consultez about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="51638-116">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="51638-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="51638-117">EXAMPLES</span></span>

### <span data-ttu-id="51638-118">Exemple 1 : obtenir tous les points d’arrêt pour tous les scripts et les fonctions</span><span class="sxs-lookup"><span data-stu-id="51638-118">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="51638-119">Cette commande obtient tous les points d'arrêt définis sur tous les scripts et fonctions de la session active.</span><span class="sxs-lookup"><span data-stu-id="51638-119">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="51638-120">Exemple 2 : récupérer des points d’arrêt par ID</span><span class="sxs-lookup"><span data-stu-id="51638-120">Example 2: Get breakpoints by ID</span></span>

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

<span data-ttu-id="51638-121">Cette commande obtient le point d'arrêt associé à l'ID de point d'arrêt 2.</span><span class="sxs-lookup"><span data-stu-id="51638-121">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="51638-122">Exemple 3 : diriger un ID vers Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="51638-122">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="51638-123">Ces commandes montrent comment obtenir un point d’arrêt en canalisant un ID de point d’arrêt vers **PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="51638-123">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint**.</span></span>

<span data-ttu-id="51638-124">La première commande utilise l'applet de commande Set-PSBreakpoint pour créer un point d'arrêt sur la fonction Increment dans le script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="51638-124">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="51638-125">Elle enregistre l’objet de point d’arrêt dans la variable $B.</span><span class="sxs-lookup"><span data-stu-id="51638-125">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="51638-126">La deuxième commande utilise l’opérateur point (.) pour récupérer la propriété ID de l’objet de point d’arrêt dans la variable $B.</span><span class="sxs-lookup"><span data-stu-id="51638-126">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="51638-127">Elle utilise un opérateur de pipeline (|) pour envoyer l’ID à l’applet de commande **PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="51638-127">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="51638-128">Par conséquent, la fonction **PSBreakpoint** obtient le point d’arrêt avec l’ID spécifié.</span><span class="sxs-lookup"><span data-stu-id="51638-128">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="51638-129">Exemple 4 : récupérer des points d’arrêt dans les fichiers de script spécifiés</span><span class="sxs-lookup"><span data-stu-id="51638-129">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="51638-130">Cette commande obtient tous les points d'arrêt des fichiers Sample.ps1 et SupportScript.ps1.</span><span class="sxs-lookup"><span data-stu-id="51638-130">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="51638-131">Cette commande n’obtient pas d’autres points d’arrêt qui peuvent être définis dans d’autres scripts ou sur des fonctions dans la session.</span><span class="sxs-lookup"><span data-stu-id="51638-131">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="51638-132">Exemple 5 : récupérer des points d’arrêt dans les applets de commande spécifiées</span><span class="sxs-lookup"><span data-stu-id="51638-132">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="51638-133">Cette commande obtient tous les points d'arrêt de commande définis sur les commandes Read-Host ou Write-Host dans le fichier Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="51638-133">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="51638-134">Exemple 6 : obtenir des points d’arrêt de commande dans un fichier spécifié</span><span class="sxs-lookup"><span data-stu-id="51638-134">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="51638-135">Cette commande obtient tous les points d'arrêt de commande du fichier Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="51638-135">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="51638-136">Exemple 7 : récupérer des points d’arrêt par variable</span><span class="sxs-lookup"><span data-stu-id="51638-136">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="51638-137">Cette commande obtient les points d’arrêt définis sur les variables $Index et $Swap dans la session active.</span><span class="sxs-lookup"><span data-stu-id="51638-137">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="51638-138">Exemple 8 : obtenir tous les points d’arrêt de ligne et de variable dans un fichier</span><span class="sxs-lookup"><span data-stu-id="51638-138">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="51638-139">Cette commande obtient tous points d'arrêt de ligne et de variable du script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="51638-139">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="51638-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51638-140">PARAMETERS</span></span>

### <span data-ttu-id="51638-141">-Command</span><span class="sxs-lookup"><span data-stu-id="51638-141">-Command</span></span>

<span data-ttu-id="51638-142">Spécifie un tableau de points d’arrêt de commande définis sur les noms de commande spécifiés.</span><span class="sxs-lookup"><span data-stu-id="51638-142">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="51638-143">Entrez les noms de commande, par exemple, le nom d'une applet de commande ou d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="51638-143">Enter the command names, such as the name of a cmdlet or function.</span></span>

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

### <span data-ttu-id="51638-144">-Id</span><span class="sxs-lookup"><span data-stu-id="51638-144">-Id</span></span>

<span data-ttu-id="51638-145">Spécifie les ID de point d’arrêt que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="51638-145">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="51638-146">Entrez les ID dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="51638-146">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="51638-147">Vous pouvez également diriger les ID de point d’arrêt vers **PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="51638-147">You can also pipe breakpoint IDs to **Get-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="51638-148">-Script</span><span class="sxs-lookup"><span data-stu-id="51638-148">-Script</span></span>

<span data-ttu-id="51638-149">Spécifie un tableau de scripts qui contiennent les points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="51638-149">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="51638-150">Entrez le chemin d’accès (facultatif) et les noms d’un ou de plusieurs fichiers de script.</span><span class="sxs-lookup"><span data-stu-id="51638-150">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="51638-151">Si vous omettez le chemin d'accès, l'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="51638-151">If you omit the path, the default location is the current directory.</span></span>

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

### <span data-ttu-id="51638-152">-Type</span><span class="sxs-lookup"><span data-stu-id="51638-152">-Type</span></span>

<span data-ttu-id="51638-153">Spécifie un tableau de types de points d’arrêt que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="51638-153">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="51638-154">Entrez un ou plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="51638-154">Enter one or more types.</span></span>
<span data-ttu-id="51638-155">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="51638-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="51638-156">Lignes</span><span class="sxs-lookup"><span data-stu-id="51638-156">Line</span></span>
- <span data-ttu-id="51638-157">Commande</span><span class="sxs-lookup"><span data-stu-id="51638-157">Command</span></span>
- <span data-ttu-id="51638-158">Variable</span><span class="sxs-lookup"><span data-stu-id="51638-158">Variable</span></span>

<span data-ttu-id="51638-159">Vous pouvez également diriger les types de point d’arrêt vers **PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="51638-159">You can also pipe breakpoint types to **Get-PSBreakPoint**.</span></span>

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

### <span data-ttu-id="51638-160">-Variable</span><span class="sxs-lookup"><span data-stu-id="51638-160">-Variable</span></span>

<span data-ttu-id="51638-161">Spécifie un tableau de points d’arrêt de variable définis sur les noms de variable spécifiés.</span><span class="sxs-lookup"><span data-stu-id="51638-161">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="51638-162">Entrez les noms de variable sans le signe dollar.</span><span class="sxs-lookup"><span data-stu-id="51638-162">Enter the variable names without dollar signs.</span></span>

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

### <span data-ttu-id="51638-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51638-163">CommonParameters</span></span>

<span data-ttu-id="51638-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51638-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51638-165">Pour plus d’informations, consultez about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="51638-165">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51638-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="51638-166">INPUTS</span></span>

### <span data-ttu-id="51638-167">System. Int32, Microsoft. PowerShell. Commands. BreakpointType</span><span class="sxs-lookup"><span data-stu-id="51638-167">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="51638-168">Vous pouvez diriger les ID de point d’arrêt et les types de point d’arrêt vers **PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="51638-168">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint**.</span></span>

## <span data-ttu-id="51638-169">SORTIES</span><span class="sxs-lookup"><span data-stu-id="51638-169">OUTPUTS</span></span>

### <span data-ttu-id="51638-170">System. Management. Automation. Breakpoint</span><span class="sxs-lookup"><span data-stu-id="51638-170">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="51638-171">La méthode **PSBreakpoint retourne des** objets qui représentent les points d’arrêt de la session.</span><span class="sxs-lookup"><span data-stu-id="51638-171">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="51638-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="51638-172">NOTES</span></span>

* <span data-ttu-id="51638-173">Vous pouvez utiliser **PSBreakpoint** ou son alias, « GBP ».</span><span class="sxs-lookup"><span data-stu-id="51638-173">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="51638-174">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="51638-174">RELATED LINKS</span></span>

[<span data-ttu-id="51638-175">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="51638-175">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="51638-176">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="51638-176">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="51638-177">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="51638-177">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="51638-178">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="51638-178">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="51638-179">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="51638-179">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

