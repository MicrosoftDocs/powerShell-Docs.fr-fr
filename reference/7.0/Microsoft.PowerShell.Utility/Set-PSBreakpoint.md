---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: ee2229866bdbee530230fbd5cf04ae362722bf2f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201241"
---
# <span data-ttu-id="956f1-103">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="956f1-103">Set-PSBreakpoint</span></span>

## <span data-ttu-id="956f1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="956f1-104">SYNOPSIS</span></span>
<span data-ttu-id="956f1-105">Définit un point d'arrêt sur une ligne, une commande ou une variable.</span><span class="sxs-lookup"><span data-stu-id="956f1-105">Sets a breakpoint on a line, command, or variable.</span></span>

## <span data-ttu-id="956f1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="956f1-106">SYNTAX</span></span>

### <span data-ttu-id="956f1-107">Line (par défaut)</span><span class="sxs-lookup"><span data-stu-id="956f1-107">Line (Default)</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="956f1-108">Commande</span><span class="sxs-lookup"><span data-stu-id="956f1-108">Command</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="956f1-109">Variable</span><span class="sxs-lookup"><span data-stu-id="956f1-109">Variable</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## <span data-ttu-id="956f1-110">Description</span><span class="sxs-lookup"><span data-stu-id="956f1-110">DESCRIPTION</span></span>

<span data-ttu-id="956f1-111">L' `Set-PSBreakpoint` applet de commande définit un point d’arrêt dans un script ou une commande exécutée dans la session active.</span><span class="sxs-lookup"><span data-stu-id="956f1-111">The `Set-PSBreakpoint` cmdlet sets a breakpoint in a script or in any command run in the current session.</span></span> <span data-ttu-id="956f1-112">Vous pouvez utiliser `Set-PSBreakpoint` pour définir un point d’arrêt avant d’exécuter un script ou d’exécuter une commande, ou pendant le débogage, lorsqu’il est arrêté à un autre point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-112">You can use `Set-PSBreakpoint` to set a breakpoint before executing a script or running a command, or during debugging, when stopped at another breakpoint.</span></span>

<span data-ttu-id="956f1-113">`Set-PSBreakpoint` Impossible de définir un point d’arrêt sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="956f1-113">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="956f1-114">Pour déboguer un script sur un ordinateur distant, copiez le script sur l'ordinateur local, puis déboguez-le localement.</span><span class="sxs-lookup"><span data-stu-id="956f1-114">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>

<span data-ttu-id="956f1-115">Chaque `Set-PSBreakpoint` commande crée l’un des trois types de points d’arrêt suivants :</span><span class="sxs-lookup"><span data-stu-id="956f1-115">Each `Set-PSBreakpoint` command creates one of the following three types of breakpoints:</span></span>

- <span data-ttu-id="956f1-116">Point d’arrêt de ligne : définit les points d’arrêt à des coordonnées de ligne et de colonne particulières.</span><span class="sxs-lookup"><span data-stu-id="956f1-116">Line breakpoint - Sets breakpoints at particular line and column coordinates.</span></span>
- <span data-ttu-id="956f1-117">Point d’arrêt de commande-définit des points d’arrêt sur les commandes et les fonctions.</span><span class="sxs-lookup"><span data-stu-id="956f1-117">Command breakpoint - Sets breakpoints on commands and functions.</span></span>
- <span data-ttu-id="956f1-118">Point d’arrêt de variable-définit des points d’arrêt sur des variables.</span><span class="sxs-lookup"><span data-stu-id="956f1-118">Variable breakpoint - Sets breakpoints on variables.</span></span>

<span data-ttu-id="956f1-119">Vous pouvez définir un point d’arrêt sur plusieurs lignes, commandes ou variables dans une même `Set-PSBreakpoint` commande, mais chaque `Set-PSBreakpoint` commande ne définit qu’un seul type de point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-119">You can set a breakpoint on multiple lines, commands, or variables in a single `Set-PSBreakpoint` command, but each `Set-PSBreakpoint` command sets only one type of breakpoint.</span></span>

<span data-ttu-id="956f1-120">À un point d’arrêt, PowerShell arrête temporairement l’exécution et donne le contrôle au débogueur.</span><span class="sxs-lookup"><span data-stu-id="956f1-120">At a breakpoint, PowerShell temporarily stops executing and gives control to the debugger.</span></span> <span data-ttu-id="956f1-121">L’invite de commandes devient `DBG\>` , et un ensemble de commandes du débogueur peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="956f1-121">The command prompt changes to `DBG\>`, and a set of debugger commands become available for use.</span></span> <span data-ttu-id="956f1-122">Toutefois, vous pouvez utiliser le paramètre **action** pour spécifier une autre réponse, telle que les conditions pour le point d’arrêt ou les instructions pour effectuer des tâches supplémentaires telles que la journalisation ou les Diagnostics.</span><span class="sxs-lookup"><span data-stu-id="956f1-122">However, you can use the **Action** parameter to specify an alternate response, such as conditions for the breakpoint or instructions to perform additional tasks such as logging or diagnostics.</span></span>

<span data-ttu-id="956f1-123">L' `Set-PSBreakpoint` applet de commande est l’une des différentes applets de commande conçues pour le débogage des scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="956f1-123">The `Set-PSBreakpoint` cmdlet is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="956f1-124">Pour plus d’informations sur le débogueur PowerShell, consultez [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span><span class="sxs-lookup"><span data-stu-id="956f1-124">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="956f1-125">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="956f1-125">EXAMPLES</span></span>

### <span data-ttu-id="956f1-126">Exemple 1 : définir un point d’arrêt sur une ligne</span><span class="sxs-lookup"><span data-stu-id="956f1-126">Example 1: Set a breakpoint on a line</span></span>

<span data-ttu-id="956f1-127">Cet exemple définit un point d’arrêt à la ligne 5 dans le script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="956f1-127">This example sets a breakpoint at line 5 in the Sample.ps1 script.</span></span> <span data-ttu-id="956f1-128">Lorsque le script s’exécute, l’exécution s’arrête immédiatement avant l’exécution de la ligne 5.</span><span class="sxs-lookup"><span data-stu-id="956f1-128">When the script runs, execution stops immediately before line 5 would execute.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="956f1-129">Lorsque vous définissez un nouveau point d’arrêt par numéro de ligne, l’applet de commande `Set-PSBreakpoint` génère un objet de point d’arrêt de ligne ( **System. Management. Automation. LineBreakpoint** ) qui comprend l’ID du point d’arrêt et le nombre d’accès.</span><span class="sxs-lookup"><span data-stu-id="956f1-129">When you set a new breakpoint by line number, the `Set-PSBreakpoint` cmdlet generates a line breakpoint object ( **System.Management.Automation.LineBreakpoint** ) that includes the breakpoint ID and hit count.</span></span>

### <span data-ttu-id="956f1-130">Exemple 2 : définir un point d’arrêt sur une fonction</span><span class="sxs-lookup"><span data-stu-id="956f1-130">Example 2: Set a breakpoint on a function</span></span>

<span data-ttu-id="956f1-131">Cet exemple crée un point d’arrêt de commande sur la `Increment` fonction dans l’applet de commande Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="956f1-131">This example creates a command breakpoint on the `Increment` function in the Sample.ps1 cmdlet.</span></span> <span data-ttu-id="956f1-132">Le script arrête l'exécution juste avant chaque appel à la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="956f1-132">The script stops executing immediately before each call to the specified function.</span></span>

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="956f1-133">Le résultat est un objet point d'arrêt de commande.</span><span class="sxs-lookup"><span data-stu-id="956f1-133">The result is a command breakpoint object.</span></span> <span data-ttu-id="956f1-134">Avant l’exécution du script, la valeur de la propriété **HitCount** est 0.</span><span class="sxs-lookup"><span data-stu-id="956f1-134">Before the script runs, the value of the **HitCount** property is 0.</span></span>

### <span data-ttu-id="956f1-135">Exemple 3 : définir un point d’arrêt sur une variable</span><span class="sxs-lookup"><span data-stu-id="956f1-135">Example 3: Set a breakpoint on a variable</span></span>

<span data-ttu-id="956f1-136">Cet exemple définit un point d’arrêt sur la variable **serveur** dans le script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="956f1-136">This example sets a breakpoint on the **Server** variable in the Sample.ps1 script.</span></span> <span data-ttu-id="956f1-137">Elle utilise le paramètre **mode** avec la valeur **ReadWrite** pour arrêter l’exécution lorsque la valeur de la variable est lue et juste avant que la valeur ne change.</span><span class="sxs-lookup"><span data-stu-id="956f1-137">It uses the **Mode** parameter with a value of **ReadWrite** to stop execution when the value of the variable is read and just before the value changes.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### <span data-ttu-id="956f1-138">Exemple 4 : définir un point d’arrêt pour chaque commande qui commence par le texte spécifié</span><span class="sxs-lookup"><span data-stu-id="956f1-138">Example 4: Set a breakpoint on every command that begins with specified text</span></span>

<span data-ttu-id="956f1-139">Cet exemple définit un point d’arrêt sur chaque commande dans le script Sample.ps1 qui commence par « Write », comme `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="956f1-139">This example sets a breakpoint on every command in the Sample.ps1 script that begins with "write", such as `Write-Host`.</span></span>

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### <span data-ttu-id="956f1-140">Exemple 5 : définir un point d’arrêt en fonction de la valeur d’une variable</span><span class="sxs-lookup"><span data-stu-id="956f1-140">Example 5: Set a breakpoint depending on the value of a variable</span></span>

<span data-ttu-id="956f1-141">Cet exemple arrête l’exécution au niveau de la `DiskTest` fonction dans le script Test.ps1 uniquement lorsque la valeur de la `$Disk` variable est supérieure à 2.</span><span class="sxs-lookup"><span data-stu-id="956f1-141">This example stops execution at the `DiskTest` function in the Test.ps1 script only when the value of the `$Disk` variable is greater than 2.</span></span>

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

<span data-ttu-id="956f1-142">La valeur de l' **action** est un bloc de script qui teste la valeur de la `$Disk` variable dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="956f1-142">The value of the **Action** is a script block that tests the value of the `$Disk` variable in the function.</span></span>

<span data-ttu-id="956f1-143">L’action utilise le `break` mot clé pour arrêter l’exécution si la condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="956f1-143">The action uses the `break` keyword to stop execution if the condition is met.</span></span> <span data-ttu-id="956f1-144">L’alternative (et la valeur par défaut) est **Continuer** .</span><span class="sxs-lookup"><span data-stu-id="956f1-144">The alternative (and the default) is **Continue** .</span></span>

### <span data-ttu-id="956f1-145">Exemple 6 : définir un point d’arrêt sur une fonction</span><span class="sxs-lookup"><span data-stu-id="956f1-145">Example 6: Set a breakpoint on a function</span></span>

<span data-ttu-id="956f1-146">Cet exemple définit un point d’arrêt sur la `CheckLog` fonction.</span><span class="sxs-lookup"><span data-stu-id="956f1-146">This example sets a breakpoint on the `CheckLog` function.</span></span> <span data-ttu-id="956f1-147">Comme la commande ne spécifie pas de script, le point d'arrêt est défini sur n'importe quel élément qui s'exécute dans la session active.</span><span class="sxs-lookup"><span data-stu-id="956f1-147">Because the command does not specify a script, the breakpoint is set on anything that runs in the current session.</span></span> <span data-ttu-id="956f1-148">Le débogueur s'arrête quand la fonction est appelée, et non quand elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="956f1-148">The debugger breaks when the function is called, not when it is declared.</span></span>

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### <span data-ttu-id="956f1-149">Exemple 7 : définir des points d’arrêt sur plusieurs lignes</span><span class="sxs-lookup"><span data-stu-id="956f1-149">Example 7: Set breakpoints on multiple lines</span></span>

<span data-ttu-id="956f1-150">Cet exemple définit trois points d’arrêt de ligne dans le script Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="956f1-150">This example sets three line breakpoints in the Sample.ps1 script.</span></span> <span data-ttu-id="956f1-151">Elle définit un point d'arrêt sur la colonne 2 de chacune des lignes spécifiées dans le script.</span><span class="sxs-lookup"><span data-stu-id="956f1-151">It sets one breakpoint at column 2 on each of the lines specified in the script.</span></span> <span data-ttu-id="956f1-152">L’action spécifiée dans le paramètre **action** s’applique à tous les points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-152">The action specified in the **Action** parameter applies to all breakpoints.</span></span>

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## <span data-ttu-id="956f1-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="956f1-153">PARAMETERS</span></span>

### <span data-ttu-id="956f1-154">-Action</span><span class="sxs-lookup"><span data-stu-id="956f1-154">-Action</span></span>

<span data-ttu-id="956f1-155">Spécifie les commandes qui s'exécutent à chaque point d'arrêt au lieu de s'arrêter.</span><span class="sxs-lookup"><span data-stu-id="956f1-155">Specifies commands that run at each breakpoint instead of breaking.</span></span> <span data-ttu-id="956f1-156">Entrez un bloc de script qui contient les commandes.</span><span class="sxs-lookup"><span data-stu-id="956f1-156">Enter a script block that contains the commands.</span></span> <span data-ttu-id="956f1-157">Vous pouvez utiliser ce paramètre pour définir des points d'arrêt conditionnels ou exécuter d'autres tâches, comme les tests ou la journalisation.</span><span class="sxs-lookup"><span data-stu-id="956f1-157">You can use this parameter to set conditional breakpoints or to perform other tasks, such as testing or logging.</span></span>

<span data-ttu-id="956f1-158">Si ce paramètre est omis ou qu'aucune action n'est spécifiées, l'exécution s'arrête au point d'arrêt et le débogueur démarre.</span><span class="sxs-lookup"><span data-stu-id="956f1-158">If this parameter is omitted, or no action is specified, execution stops at the breakpoint, and the debugger starts.</span></span>

<span data-ttu-id="956f1-159">Lorsque le paramètre d' **action** est utilisé, le bloc de script d’action s’exécute à chaque point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-159">When the **Action** parameter is used, the Action script block runs at each breakpoint.</span></span> <span data-ttu-id="956f1-160">L'exécution ne s'interrompt pas, à moins que le bloc de script ne comporte le mot clé Break.</span><span class="sxs-lookup"><span data-stu-id="956f1-160">Execution does not stop unless the script block includes the Break keyword.</span></span> <span data-ttu-id="956f1-161">Si vous utilisez le mot clé Continue dans le bloc de script, l'exécution reprend jusqu'au point d'arrêt suivant.</span><span class="sxs-lookup"><span data-stu-id="956f1-161">If you use the Continue keyword in the script block, execution resumes until the next breakpoint.</span></span>

<span data-ttu-id="956f1-162">Pour plus d’informations, consultez [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)et [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span><span class="sxs-lookup"><span data-stu-id="956f1-162">For more information, see [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md), and [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="956f1-163">-Colonne</span><span class="sxs-lookup"><span data-stu-id="956f1-163">-Column</span></span>

<span data-ttu-id="956f1-164">Spécifie le numéro de colonne du fichier de script sur lequel l'exécution s'arrête.</span><span class="sxs-lookup"><span data-stu-id="956f1-164">Specifies the column number of the column in the script file on which execution stops.</span></span> <span data-ttu-id="956f1-165">Entrez un seul numéro de colonne.</span><span class="sxs-lookup"><span data-stu-id="956f1-165">Enter only one column number.</span></span> <span data-ttu-id="956f1-166">La valeur par défaut est la colonne 1.</span><span class="sxs-lookup"><span data-stu-id="956f1-166">The default is column 1.</span></span>

<span data-ttu-id="956f1-167">La valeur de la colonne est utilisée avec la valeur du paramètre **line** pour spécifier le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-167">The Column value is used with the value of the **Line** parameter to specify the breakpoint.</span></span> <span data-ttu-id="956f1-168">Si le paramètre **line** spécifie plusieurs lignes, le paramètre **Column** définit un point d’arrêt au niveau de la colonne spécifiée sur chacune des lignes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="956f1-168">If the **Line** parameter specifies multiple lines, the **Column** parameter sets a breakpoint at the specified column on each of the specified lines.</span></span> <span data-ttu-id="956f1-169">PowerShell arrête l’exécution avant l’instruction ou l’expression qui contient le caractère à la position de ligne et de colonne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="956f1-169">PowerShell stops executing before the statement or expression that includes the character at the specified line and column position.</span></span>

<span data-ttu-id="956f1-170">Les colonnes sont numérotées à partir de la marge gauche en commençant par le numéro 1 (pas 0).</span><span class="sxs-lookup"><span data-stu-id="956f1-170">Columns are counted from the top left margin beginning with column number 1 (not 0).</span></span> <span data-ttu-id="956f1-171">Si vous spécifiez une colonne qui n'existe pas dans le script, aucune erreur n'est déclarée, mais le point d'arrêt n'est jamais exécuté.</span><span class="sxs-lookup"><span data-stu-id="956f1-171">If you specify a column that does not exist in the script, an error is not declared, but the breakpoint is never executed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="956f1-172">-Command</span><span class="sxs-lookup"><span data-stu-id="956f1-172">-Command</span></span>

<span data-ttu-id="956f1-173">Définit un point d'arrêt de commande.</span><span class="sxs-lookup"><span data-stu-id="956f1-173">Sets a command breakpoint.</span></span> <span data-ttu-id="956f1-174">Entrez des noms d’applet de commande, tels que `Get-Process` , ou des noms de fonction.</span><span class="sxs-lookup"><span data-stu-id="956f1-174">Enter cmdlet names, such as `Get-Process`, or function names.</span></span> <span data-ttu-id="956f1-175">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="956f1-175">Wildcards are permitted.</span></span>

<span data-ttu-id="956f1-176">L'exécution s'arrête juste avant l'exécution de chaque instance de chaque commande.</span><span class="sxs-lookup"><span data-stu-id="956f1-176">Execution stops just before each instance of each command is executed.</span></span> <span data-ttu-id="956f1-177">Si la commande est une fonction, l'exécution s'arrête chaque fois que la fonction est appelée, ainsi que sur chaque section BEGIN, PROCESS et END.</span><span class="sxs-lookup"><span data-stu-id="956f1-177">If the command is a function, execution stops each time the function is called and at each BEGIN, PROCESS, and END section.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="956f1-178">-Ligne</span><span class="sxs-lookup"><span data-stu-id="956f1-178">-Line</span></span>

<span data-ttu-id="956f1-179">Définit un point d'arrêt de ligne dans un script.</span><span class="sxs-lookup"><span data-stu-id="956f1-179">Sets a line breakpoint in a script.</span></span> <span data-ttu-id="956f1-180">Entrez un ou plusieurs numéros de ligne, séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="956f1-180">Enter one or more line numbers, separated by commas.</span></span> <span data-ttu-id="956f1-181">PowerShell s’arrête immédiatement avant l’exécution de l’instruction qui commence sur chacune des lignes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="956f1-181">PowerShell stops immediately before executing the statement that begins on each of the specified lines.</span></span>

<span data-ttu-id="956f1-182">Les lignes sont numérotées à partir de la marge gauche du fichier de script en commençant par le numéro 1 (pas 0).</span><span class="sxs-lookup"><span data-stu-id="956f1-182">Lines are counted from the top left margin of the script file beginning with line number 1 (not 0).</span></span>
<span data-ttu-id="956f1-183">Si vous spécifiez une ligne vierge, l'exécution s'arrête avant la prochaine ligne non vide.</span><span class="sxs-lookup"><span data-stu-id="956f1-183">If you specify a blank line, execution stops before the next non-blank line.</span></span> <span data-ttu-id="956f1-184">Si la ligne est en dehors de la plage, le point d'arrêt n'est jamais atteint.</span><span class="sxs-lookup"><span data-stu-id="956f1-184">If the line is out of range, the breakpoint is never hit.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="956f1-185">-Mode</span><span class="sxs-lookup"><span data-stu-id="956f1-185">-Mode</span></span>

<span data-ttu-id="956f1-186">Spécifie le mode d’accès qui déclenche les points d’arrêt de variable.</span><span class="sxs-lookup"><span data-stu-id="956f1-186">Specifies the mode of access that triggers variable breakpoints.</span></span> <span data-ttu-id="956f1-187">La valeur par défaut est **Write** .</span><span class="sxs-lookup"><span data-stu-id="956f1-187">The default is **Write** .</span></span>

<span data-ttu-id="956f1-188">Ce paramètre n’est valide que lorsque le paramètre **variable** est utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="956f1-188">This parameter is valid only when the **Variable** parameter is used in the command.</span></span> <span data-ttu-id="956f1-189">Le mode s'applique à tous les points d'arrêt définis dans la commande.</span><span class="sxs-lookup"><span data-stu-id="956f1-189">The mode applies to all breakpoints set in the command.</span></span> <span data-ttu-id="956f1-190">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="956f1-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="956f1-191">**Write** : arrête l’exécution immédiatement avant qu’une nouvelle valeur ne soit écrite dans la variable.</span><span class="sxs-lookup"><span data-stu-id="956f1-191">**Write** - Stops execution immediately before a new value is written to the variable.</span></span>
- <span data-ttu-id="956f1-192">**Lecture** : arrête l’exécution lorsque la variable est lue, c’est-à-dire lorsque sa valeur est accédée, affichée ou utilisée.</span><span class="sxs-lookup"><span data-stu-id="956f1-192">**Read** - Stops execution when the variable is read, that is, when its value is accessed, either to be assigned, displayed, or used.</span></span> <span data-ttu-id="956f1-193">En mode lecture, l'exécution ne s'arrête pas lorsque la valeur de la variable change.</span><span class="sxs-lookup"><span data-stu-id="956f1-193">In read mode, execution does not stop when the value of the variable changes.</span></span>
- <span data-ttu-id="956f1-194">**ReadWrite** : arrête l’exécution lorsque la variable est lue ou écrite.</span><span class="sxs-lookup"><span data-stu-id="956f1-194">**ReadWrite** - Stops execution when the variable is read or written.</span></span>

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="956f1-195">-Script</span><span class="sxs-lookup"><span data-stu-id="956f1-195">-Script</span></span>

<span data-ttu-id="956f1-196">Spécifie un tableau de fichiers de script dans lequel cette applet de commande définit un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-196">Specifies an array of script files that this cmdlet sets a breakpoint in.</span></span> <span data-ttu-id="956f1-197">Entrez les chemins d'accès et les noms de fichiers d'un ou de plusieurs fichiers de script.</span><span class="sxs-lookup"><span data-stu-id="956f1-197">Enter the paths and file names of one or more script files.</span></span> <span data-ttu-id="956f1-198">Si les fichiers se trouvent dans le répertoire actif, vous pouvez ignorer le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="956f1-198">If the files are in the current directory, you can omit the path.</span></span>
<span data-ttu-id="956f1-199">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="956f1-199">Wildcards are permitted.</span></span>

<span data-ttu-id="956f1-200">Par défaut, les points d'arrêt de variable ou de commande sont définis sur une commande qui s'exécute dans la session active.</span><span class="sxs-lookup"><span data-stu-id="956f1-200">By default, variable breakpoints and command breakpoints are set on any command that runs in the current session.</span></span> <span data-ttu-id="956f1-201">Ce paramètre n'est obligatoire que lors de la définition d'un point d'arrêt de ligne.</span><span class="sxs-lookup"><span data-stu-id="956f1-201">This parameter is required only when setting a line breakpoint.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="956f1-202">-Variable</span><span class="sxs-lookup"><span data-stu-id="956f1-202">-Variable</span></span>

<span data-ttu-id="956f1-203">Spécifie un tableau de variables sur lesquelles cette cmdlet définit des points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-203">Specifies an array of variables that this cmdlet sets breakpoints on.</span></span> <span data-ttu-id="956f1-204">Entrez une liste de variables séparées par des virgules sans signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="956f1-204">Enter a comma-separated list of variables without dollar signs (`$`).</span></span>

<span data-ttu-id="956f1-205">Utilisez le paramètre **mode** pour déterminer le mode d’accès qui déclenche les points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="956f1-205">Use the **Mode** parameter to determine the mode of access that triggers the breakpoints.</span></span> <span data-ttu-id="956f1-206">Le mode par défaut, Write, arrête l'exécution avant qu'une nouvelle valeur ne soit écrite dans la variable.</span><span class="sxs-lookup"><span data-stu-id="956f1-206">The default mode, Write, stops execution just before a new value is written to the variable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="956f1-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="956f1-207">CommonParameters</span></span>

<span data-ttu-id="956f1-208">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="956f1-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="956f1-209">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="956f1-209">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="956f1-210">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="956f1-210">INPUTS</span></span>

### <span data-ttu-id="956f1-211">Aucun</span><span class="sxs-lookup"><span data-stu-id="956f1-211">None</span></span>
<span data-ttu-id="956f1-212">Vous ne pouvez pas diriger d’entrée vers `Set-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="956f1-212">You cannot pipe input to `Set-PSBreakpoint`.</span></span>

## <span data-ttu-id="956f1-213">SORTIES</span><span class="sxs-lookup"><span data-stu-id="956f1-213">OUTPUTS</span></span>

### <span data-ttu-id="956f1-214">Objet point d’arrêt (System. Management. Automation. LineBreakpoint, System. Management. Automation. VariableBreakpoint, System. Management. Automation. CommandBreakpoint)</span><span class="sxs-lookup"><span data-stu-id="956f1-214">Breakpoint object (System.Management.Automation.LineBreakpoint, System.Management.Automation.VariableBreakpoint, System.Management.Automation.CommandBreakpoint)</span></span>

<span data-ttu-id="956f1-215">`Set-PSBreakpoint` retourne un objet qui représente chaque point d’arrêt qu’il définit.</span><span class="sxs-lookup"><span data-stu-id="956f1-215">`Set-PSBreakpoint` returns an object that represents each breakpoint that it sets.</span></span>

## <span data-ttu-id="956f1-216">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="956f1-216">NOTES</span></span>

- <span data-ttu-id="956f1-217">`Set-PSBreakpoint` Impossible de définir un point d’arrêt sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="956f1-217">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="956f1-218">Pour déboguer un script sur un ordinateur distant, copiez le script sur l'ordinateur local, puis déboguez-le localement.</span><span class="sxs-lookup"><span data-stu-id="956f1-218">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>
- <span data-ttu-id="956f1-219">Lorsque vous définissez un point d’arrêt sur plusieurs lignes, commandes ou variables, `Set-PSBreakpoint` génère un objet de point d’arrêt pour chaque entrée.</span><span class="sxs-lookup"><span data-stu-id="956f1-219">When you set a breakpoint on more than one line, command, or variable, `Set-PSBreakpoint` generates a breakpoint object for each entry.</span></span>
- <span data-ttu-id="956f1-220">Lors de la définition d'un point d'arrêt sur une fonction ou une variable à l'invite de commandes, vous pouvez définir le point d'arrêt avant ou après la création de la fonction ou variable.</span><span class="sxs-lookup"><span data-stu-id="956f1-220">When setting a breakpoint on a function or variable at the command prompt, you can set the breakpoint before or after you create the function or variable.</span></span>

## <span data-ttu-id="956f1-221">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="956f1-221">RELATED LINKS</span></span>

[<span data-ttu-id="956f1-222">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="956f1-222">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="956f1-223">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="956f1-223">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="956f1-224">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="956f1-224">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="956f1-225">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="956f1-225">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="956f1-226">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="956f1-226">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)
