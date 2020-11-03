---
description: Décrit le chaînage des pipelines avec `&&` les `||` opérateurs et dans PowerShell.
ms.date: 09/30/2019
schema: 2.0.0
Locale: en-US
keywords: powershell,applet de commande
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: 38895ff9acda9ead031c9be58904ac132364a584
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207301"
---
# <a name="about-pipeline-chain-operators"></a><span data-ttu-id="70bb7-104">À propos des opérateurs de chaîne de pipeline</span><span class="sxs-lookup"><span data-stu-id="70bb7-104">About Pipeline Chain Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="70bb7-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="70bb7-105">Short description</span></span>

<span data-ttu-id="70bb7-106">Décrit le chaînage des pipelines avec `&&` les `||` opérateurs et dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70bb7-106">Describes chaining pipelines with the `&&` and `||` operators in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="70bb7-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="70bb7-107">Long description</span></span>

<span data-ttu-id="70bb7-108">À compter de PowerShell 7, PowerShell implémente `&&` les `||` opérateurs et pour chaîner de manière conditionnelle des pipelines.</span><span class="sxs-lookup"><span data-stu-id="70bb7-108">Beginning in PowerShell 7, PowerShell implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="70bb7-109">Ces opérateurs sont connus dans PowerShell en tant qu' *opérateurs de chaîne de pipeline* et sont similaires à des [listes et ou](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) dans des interpréteurs de commandes POSIX tels que bash, zsh et SH, ainsi qu’à des [symboles de traitement conditionnel](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) dans l’interface de commande Windows (cmd.exe).</span><span class="sxs-lookup"><span data-stu-id="70bb7-109">These operators are known in PowerShell as *pipeline chain operators* , and are similar to [AND-OR lists](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) in POSIX shells like bash, zsh and sh, as well as [conditional processing symbols](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) in the Windows Command Shell (cmd.exe).</span></span>

<span data-ttu-id="70bb7-110">L’opérateur `&&` exécute le pipeline droit si l’exécution du pipeline gauche a réussi.</span><span class="sxs-lookup"><span data-stu-id="70bb7-110">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="70bb7-111">Inversement, l’opérateur `||` exécute le pipeline droit si l’exécution du pipeline gauche a échoué.</span><span class="sxs-lookup"><span data-stu-id="70bb7-111">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

<span data-ttu-id="70bb7-112">Ces opérateurs utilisent les variables `$?` et `$LASTEXITCODE` pour déterminer si un pipeline a échoué.</span><span class="sxs-lookup"><span data-stu-id="70bb7-112">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="70bb7-113">Cela vous permet de les utiliser avec des commandes natives, et pas seulement avec des cmdlet ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="70bb7-113">This allows you to use them with native commands and not just with cmdlets or functions.</span></span> <span data-ttu-id="70bb7-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="70bb7-114">For example:</span></span>

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a><span data-ttu-id="70bb7-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="70bb7-115">Examples</span></span>

#### <a name="two-successful-commands"></a><span data-ttu-id="70bb7-116">Deux commandes réussies</span><span class="sxs-lookup"><span data-stu-id="70bb7-116">Two successful commands</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a><span data-ttu-id="70bb7-117">La première commande échoue, provoquant la non-exécution de la seconde</span><span class="sxs-lookup"><span data-stu-id="70bb7-117">First command fails, causing second not to be executed</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a><span data-ttu-id="70bb7-118">La première commande réussit, donc la deuxième commande n’est pas exécutée</span><span class="sxs-lookup"><span data-stu-id="70bb7-118">First command succeeds, so the second command is not executed</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a><span data-ttu-id="70bb7-119">La première commande échoue, donc la deuxième commande est exécutée</span><span class="sxs-lookup"><span data-stu-id="70bb7-119">First command fails, so the second command is executed</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

<span data-ttu-id="70bb7-120">La réussite du pipeline est définie par la valeur de la `$?` variable, que PowerShell définit automatiquement après l’exécution d’un pipeline en fonction de son état d’exécution.</span><span class="sxs-lookup"><span data-stu-id="70bb7-120">Pipeline success is defined by the value of the `$?` variable, which PowerShell automatically sets after executing a pipeline based on its execution status.</span></span>
<span data-ttu-id="70bb7-121">Cela signifie que les opérateurs de chaîne de pipeline ont l’équivalence suivante :</span><span class="sxs-lookup"><span data-stu-id="70bb7-121">This means that pipeline chain operators have the following equivalence:</span></span>

```powershell
Test-Command '1' && Test-Command '2'
```

<span data-ttu-id="70bb7-122">fonctionne de la même façon que</span><span class="sxs-lookup"><span data-stu-id="70bb7-122">works the same as</span></span>

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

<span data-ttu-id="70bb7-123">et</span><span class="sxs-lookup"><span data-stu-id="70bb7-123">and</span></span>

```powershell
Test-Command '1' || Test-Command '2'
```

<span data-ttu-id="70bb7-124">fonctionne de la même façon que</span><span class="sxs-lookup"><span data-stu-id="70bb7-124">works the same as</span></span>

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a><span data-ttu-id="70bb7-125">Assignation à partir de chaînes de pipeline</span><span class="sxs-lookup"><span data-stu-id="70bb7-125">Assignment from pipeline chains</span></span>

<span data-ttu-id="70bb7-126">L’affectation d’une variable à partir d’une chaîne de pipeline prend la concaténation de tous les pipelines de la chaîne :</span><span class="sxs-lookup"><span data-stu-id="70bb7-126">Assigning a variable from a pipeline chain takes the concatenation of all the pipelines in the chain:</span></span>

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

<span data-ttu-id="70bb7-127">Si une erreur de fin de script se produit pendant l’assignation à partir d’une chaîne de pipeline, l’affectation échoue :</span><span class="sxs-lookup"><span data-stu-id="70bb7-127">If a script-terminating error occurs during assignment from a pipeline chain, the assignment does not succeed:</span></span>

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a><span data-ttu-id="70bb7-128">Syntaxe et priorité des opérateurs</span><span class="sxs-lookup"><span data-stu-id="70bb7-128">Operator syntax and precedence</span></span>

<span data-ttu-id="70bb7-129">Contrairement à d’autres opérateurs, `&&` et `||` fonctionnent sur des pipelines, plutôt que sur des expressions telles que `+` ou `-and` , par exemple.</span><span class="sxs-lookup"><span data-stu-id="70bb7-129">Unlike other operators, `&&` and `||` operate on pipelines, rather than on expressions like `+` or `-and`, for example.</span></span>

<span data-ttu-id="70bb7-130">`&&` et `||` ont une priorité plus faible que le canalisation ( `|` ) ou la redirection ( `>` ), mais une priorité plus élevée que les opérateurs de travail ( `&` ), l’assignation ( `=` ) ou les points-virgules ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="70bb7-130">`&&` and `||` have a lower precedence than piping (`|`) or redirection (`>`), but a higher precedence than job operators (`&`), assignment (`=`) or semicolons (`;`).</span></span> <span data-ttu-id="70bb7-131">Cela signifie que les pipelines d’une chaîne de pipeline peuvent être redirigés individuellement, et que toutes les chaînes de pipeline peuvent être en arrière-plan, affectées à des variables ou être séparées en tant qu’instructions.</span><span class="sxs-lookup"><span data-stu-id="70bb7-131">This means that pipelines within a pipeline chain can be individually redirected, and that entire pipeline chains can be backgrounded, assigned to variables, or separated as statements.</span></span>

<span data-ttu-id="70bb7-132">Pour utiliser une syntaxe de précédence inférieure dans une chaîne de pipeline, envisagez l’utilisation de parenthèses `(...)` .</span><span class="sxs-lookup"><span data-stu-id="70bb7-132">To use lower precedence syntax within a pipeline chain, consider the use of parentheses `(...)`.</span></span>
<span data-ttu-id="70bb7-133">De même, pour incorporer une instruction dans une chaîne de pipeline, une sous-expression `$(...)` peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="70bb7-133">Similarly, to embed a statement within a pipeline chain, a subexpression `$(...)` can be used.</span></span>
<span data-ttu-id="70bb7-134">Cela peut être utile pour combiner des commandes natives avec un workflow de contrôle :</span><span class="sxs-lookup"><span data-stu-id="70bb7-134">This can be useful for combining native commands with control flow:</span></span>

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

<span data-ttu-id="70bb7-135">Depuis PowerShell 7, le comportement de ces syntaxes a été modifié afin de `$?` définir comme prévu quand une commande réussit ou échoue entre parenthèses ou sous-expression.</span><span class="sxs-lookup"><span data-stu-id="70bb7-135">As of PowerShell 7, the behaviour of these syntaxes has been changed so that `$?` is set as expected when a command succeeds or fails within parentheses or a subexpression.</span></span>

<span data-ttu-id="70bb7-136">Comme la plupart des autres opérateurs dans PowerShell, `&&` et `||` sont également *associatifs à gauche* , ce qui signifie qu’ils sont regroupés à partir de la gauche.</span><span class="sxs-lookup"><span data-stu-id="70bb7-136">Like most other operators in PowerShell, `&&` and `||` are also *left-associative* , meaning they group from the left.</span></span> <span data-ttu-id="70bb7-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="70bb7-137">For example:</span></span>

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

<span data-ttu-id="70bb7-138">regroupera en tant que :</span><span class="sxs-lookup"><span data-stu-id="70bb7-138">will group as:</span></span>

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

<span data-ttu-id="70bb7-139">équivalent à :</span><span class="sxs-lookup"><span data-stu-id="70bb7-139">being equivalent to:</span></span>

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a><span data-ttu-id="70bb7-140">Interaction d’erreur</span><span class="sxs-lookup"><span data-stu-id="70bb7-140">Error interaction</span></span>

<span data-ttu-id="70bb7-141">Les opérateurs de chaîne de pipeline n’absorbent pas les erreurs.</span><span class="sxs-lookup"><span data-stu-id="70bb7-141">Pipeline chain operators do not absorb errors.</span></span> <span data-ttu-id="70bb7-142">Lorsqu’une instruction dans une chaîne de pipeline lève une erreur de fin de script, la chaîne de pipeline est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="70bb7-142">When a statement in a pipeline chain throws a script-terminating error, the pipeline chain is terminated.</span></span>

<span data-ttu-id="70bb7-143">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="70bb7-143">For example:</span></span>

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

<span data-ttu-id="70bb7-144">Même lorsque l’erreur est interceptée, la chaîne de pipeline est toujours terminée :</span><span class="sxs-lookup"><span data-stu-id="70bb7-144">Even when the error is caught, the pipeline chain is still terminated:</span></span>

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

<span data-ttu-id="70bb7-145">Si une erreur ne se termine pas ou ne termine qu’un pipeline, la chaîne de pipeline continue, en respectant la valeur de `$?` :</span><span class="sxs-lookup"><span data-stu-id="70bb7-145">If an error is non-terminating, or only terminates a pipeline, the pipeline chain continues, respecting the value of `$?`:</span></span>

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a><span data-ttu-id="70bb7-146">Chaînage des pipelines plutôt que des commandes</span><span class="sxs-lookup"><span data-stu-id="70bb7-146">Chaining pipelines rather than commands</span></span>

<span data-ttu-id="70bb7-147">Les opérateurs de chaîne de pipeline, par leur nom, peuvent être utilisés pour chaîner des pipelines, plutôt que simplement des commandes.</span><span class="sxs-lookup"><span data-stu-id="70bb7-147">Pipeline chain operators, by their name, can be used to chain pipelines, rather than just commands.</span></span> <span data-ttu-id="70bb7-148">Cela correspond au comportement d’autres shells, mais peut rendre la *réussite* plus difficile à déterminer :</span><span class="sxs-lookup"><span data-stu-id="70bb7-148">This matches the behavior of other shells, but can make *success* harder to determine:</span></span>

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

<span data-ttu-id="70bb7-149">Notez que n' `Write-Output 'All done!'` est pas exécuté, car `Test-NotTwo` est considéré comme ayant échoué après la génération de l’erreur sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="70bb7-149">Note that `Write-Output 'All done!'` is not executed, since `Test-NotTwo` is deemed to have failed after generating the non-terminating error.</span></span>

## <a name="see-also"></a><span data-ttu-id="70bb7-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70bb7-150">See also</span></span>

- [<span data-ttu-id="70bb7-151">about_Operators</span><span class="sxs-lookup"><span data-stu-id="70bb7-151">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="70bb7-152">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="70bb7-152">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="70bb7-153">about_pipelines</span><span class="sxs-lookup"><span data-stu-id="70bb7-153">about_pipelines</span></span>](about_pipelines.md)

