---
title: Fonctions
description: Les fonctions PowerShell vous permettent de créer des outils réutilisables dans des scripts.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 9554c0b4d3932b7371201f7b08c8b9d26a567f5e
ms.sourcegitcommit: e85e56d6614cbd30e01965a5cf03fb3f5ca78103
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94589126"
---
# <a name="chapter-9---functions"></a><span data-ttu-id="f6c46-103">Chapitre 9 : Fonctions</span><span class="sxs-lookup"><span data-stu-id="f6c46-103">Chapter 9 - Functions</span></span>

<span data-ttu-id="f6c46-104">Si vous écrivez des one-liners ou des scripts PowerShell que vous devez ensuite souvent modifier pour des scénarios différents, vous aurez probablement intérêt à les transformer en fonctions réutilisables.</span><span class="sxs-lookup"><span data-stu-id="f6c46-104">If you're writing PowerShell one-liners or scripts and find yourself often having to modify them for different scenarios, there's a good chance that it's a good candidate to be turned into a function that can be reused.</span></span>

<span data-ttu-id="f6c46-105">Dans la mesure du possible, je préfère écrire des fonctions, car elles sont davantage orientées outil.</span><span class="sxs-lookup"><span data-stu-id="f6c46-105">Whenever possible, I prefer to write functions because they are more tool oriented.</span></span> <span data-ttu-id="f6c46-106">Je peux ajouter les fonctions dans un module de script, placer ce module dans `$env:PSModulePath`et appeler les fonctions sans avoir à localiser l’emplacement physique où elles sont enregistrées.</span><span class="sxs-lookup"><span data-stu-id="f6c46-106">I can put the functions in a script module, put that module in the `$env:PSModulePath`, and call the functions without needing to physically locate where they're saved.</span></span> <span data-ttu-id="f6c46-107">Avec PowerShellGet, partager ces modules dans un dépôt NuGet est très simple.</span><span class="sxs-lookup"><span data-stu-id="f6c46-107">Using the PowerShellGet module, it's easy to share those modules in a NuGet repository.</span></span> <span data-ttu-id="f6c46-108">PowerShellGet est fourni avec PowerShell version 5.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f6c46-108">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="f6c46-109">Il est disponible en téléchargement pour PowerShell version 3.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f6c46-109">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="f6c46-110">Ne compliquez pas les choses.</span><span class="sxs-lookup"><span data-stu-id="f6c46-110">Don't over complicate things.</span></span> <span data-ttu-id="f6c46-111">Privilégiez la simplicité et choisissez le moyen le plus rapide pour effectuer une tâche.</span><span class="sxs-lookup"><span data-stu-id="f6c46-111">Keep it simple and use the most straight forward way to accomplish a task.</span></span> <span data-ttu-id="f6c46-112">N’utilisez pas d’alias ni de paramètres positionnels dans du code que vous comptez réutiliser.</span><span class="sxs-lookup"><span data-stu-id="f6c46-112">Avoid aliases and positional parameters in any code that you reuse.</span></span> <span data-ttu-id="f6c46-113">Mettez en forme votre code dans un souci d’en faciliter la lecture.</span><span class="sxs-lookup"><span data-stu-id="f6c46-113">Format your code for readability.</span></span> <span data-ttu-id="f6c46-114">Ne codez pas les valeurs en dur, utilisez des paramètres et des variables.</span><span class="sxs-lookup"><span data-stu-id="f6c46-114">Don't hardcode values; use parameters and variables.</span></span> <span data-ttu-id="f6c46-115">N’écrivez pas de code inutile, même s’il n’a aucun effet gênant.</span><span class="sxs-lookup"><span data-stu-id="f6c46-115">Don't write unnecessary code even if it doesn't hurt anything.</span></span> <span data-ttu-id="f6c46-116">Cela rend les choses plus complexes inutilement.</span><span class="sxs-lookup"><span data-stu-id="f6c46-116">It adds unnecessary complexity.</span></span> <span data-ttu-id="f6c46-117">Le souci du détail est essentiel quand vous écrivez du code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c46-117">Attention to detail goes a long way when writing any PowerShell code.</span></span>

## <a name="naming"></a><span data-ttu-id="f6c46-118">Dénomination</span><span class="sxs-lookup"><span data-stu-id="f6c46-118">Naming</span></span>

<span data-ttu-id="f6c46-119">Quand vous nommez vos fonctions dans PowerShell, utilisez un nom [casse Pascal][] avec un verbe approuvé et un nom au singulier.</span><span class="sxs-lookup"><span data-stu-id="f6c46-119">When naming your functions in PowerShell, use a [Pascal case][] name with an approved verb and a singular noun.</span></span> <span data-ttu-id="f6c46-120">Je recommande également d’ajouter un préfixe au nom.</span><span class="sxs-lookup"><span data-stu-id="f6c46-120">I also recommend prefixing the noun.</span></span> <span data-ttu-id="f6c46-121">Par exemple : `<ApprovedVerb>-<Prefix><SingularNoun>`.</span><span class="sxs-lookup"><span data-stu-id="f6c46-121">For example: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span></span>

<span data-ttu-id="f6c46-122">Dans PowerShell, il existe une liste spécifique de verbes approuvés que vous pouvez obtenir à l’aide de la commande `Get-Verb`.</span><span class="sxs-lookup"><span data-stu-id="f6c46-122">In PowerShell, there's a specific list of approved verbs that can be obtained by running `Get-Verb`.</span></span>

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

<span data-ttu-id="f6c46-123">Dans l’exemple précédent, j’ai trié les résultats sur la colonne **Verb**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-123">In the previous example, I've sorted the results by the **Verb** column.</span></span> <span data-ttu-id="f6c46-124">La colonne **Group** vous donne une idée de la façon dont ces verbes sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="f6c46-124">The **Group** column gives you an idea of how these verbs are used.</span></span> <span data-ttu-id="f6c46-125">Il est important de choisir un verbe approuvé dans PowerShell quand des fonctions sont ajoutées à un module.</span><span class="sxs-lookup"><span data-stu-id="f6c46-125">It's important to choose an approved verb in PowerShell when functions are added to a module.</span></span> <span data-ttu-id="f6c46-126">Si vous avez choisi un verbe non approuvé, le module génère un message d’avertissement au moment du chargement.</span><span class="sxs-lookup"><span data-stu-id="f6c46-126">The module generates a warning message at load time if you choose an unapproved verb.</span></span> <span data-ttu-id="f6c46-127">Ce message d’avertissement donne une image peu professionnelle à vos fonctions.</span><span class="sxs-lookup"><span data-stu-id="f6c46-127">That warning message makes your functions look unprofessional.</span></span> <span data-ttu-id="f6c46-128">De plus, les verbes non approuvés rendent vos fonctions plus difficiles à détecter.</span><span class="sxs-lookup"><span data-stu-id="f6c46-128">Unapproved verbs also limit the discoverability of your functions.</span></span>

## <a name="a-simple-function"></a><span data-ttu-id="f6c46-129">Une fonction simple</span><span class="sxs-lookup"><span data-stu-id="f6c46-129">A simple function</span></span>

<span data-ttu-id="f6c46-130">Dans PowerShell, une fonction se déclare avec le mot clé function suivi du nom de la fonction, d’une accolade ouvrante et d’une accolade fermante.</span><span class="sxs-lookup"><span data-stu-id="f6c46-130">A function in PowerShell is declared with the function keyword followed by the function name and then an open and closing curly brace.</span></span> <span data-ttu-id="f6c46-131">Le code que la fonction exécutera est placé entre ces deux accolades.</span><span class="sxs-lookup"><span data-stu-id="f6c46-131">The code that the function will execute is contained within those curly braces.</span></span>

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="f6c46-132">Cette fonction est un exemple simple qui retourne la version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c46-132">The function shown is a simple example that returns the version of PowerShell.</span></span>

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="f6c46-133">Il y a souvent des conflits de noms entre les fonctions portant un nom comme `Get-Version` et les commandes par défaut dans PowerShell ou les commandes que d’autres utilisateurs écrivent.</span><span class="sxs-lookup"><span data-stu-id="f6c46-133">There's a good chance of name conflict with functions named something like `Get-Version` and default commands in PowerShell or commands that others may write.</span></span> <span data-ttu-id="f6c46-134">C’est la raison pour laquelle je vous recommande d’ajouter un préfixe au nom de vos fonctions, qui permet de limiter le risque de conflits de noms.</span><span class="sxs-lookup"><span data-stu-id="f6c46-134">This is why I recommend prefixing the noun portion of your functions to help prevent naming conflicts.</span></span> <span data-ttu-id="f6c46-135">Dans l’exemple suivant, je vais utiliser le préfixe « PS ».</span><span class="sxs-lookup"><span data-stu-id="f6c46-135">In the following example, I'll use the prefix "PS".</span></span>

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="f6c46-136">En dehors du nom, cette fonction est identique à la précédente.</span><span class="sxs-lookup"><span data-stu-id="f6c46-136">Other than the name, this function is identical to the previous one.</span></span>

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="f6c46-137">Même en préfixant le nom avec un élément comme PS, le risque de conflits de noms reste présent.</span><span class="sxs-lookup"><span data-stu-id="f6c46-137">Even when prefixing the noun with something like PS, there's still a good chance of having a name conflict.</span></span> <span data-ttu-id="f6c46-138">Je préfixe généralement mes noms de fonctions avec mes initiales.</span><span class="sxs-lookup"><span data-stu-id="f6c46-138">I typically prefix my function nouns with my initials.</span></span> <span data-ttu-id="f6c46-139">Établissez une convention et respectez-la.</span><span class="sxs-lookup"><span data-stu-id="f6c46-139">Develop a standard and stick to it.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="f6c46-140">Cette fonction est identique aux deux précédentes si ce n’est l’usage d’un nom plus judicieux pour éviter le plus possible les conflits de noms avec d’autres commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c46-140">This function is no different than the previous two other than using a more sensible name to try to prevent naming conflicts with other PowerShell commands.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="f6c46-141">Une fois les fonctions chargées en mémoire, vous les voyez sur le PSDrive **Function**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-141">Once loaded into memory, you can see functions on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

<span data-ttu-id="f6c46-142">Si vous souhaitez supprimer ces fonctions de votre session active, vous devez les supprimer du PSDrive **Function** ou fermer et rouvrir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c46-142">If you want to remove these functions from your current session, you'll have to remove them from the **Function** PSDrive or close and reopen PowerShell.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

<span data-ttu-id="f6c46-143">Vérifiez que les fonctions ont bien été supprimées.</span><span class="sxs-lookup"><span data-stu-id="f6c46-143">Verify that the functions were indeed removed.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

<span data-ttu-id="f6c46-144">Si les fonctions ont été chargées avec un module, le module peut être déchargé pour supprimer les fonctions.</span><span class="sxs-lookup"><span data-stu-id="f6c46-144">If the functions were loaded as part of a module, the module can be unloaded to remove them.</span></span>

```powershell
Remove-Module -Name <ModuleName>
```

<span data-ttu-id="f6c46-145">L’applet de commande `Remove-Module` supprime les modules en mémoire dans votre session PowerShell active, elle ne les supprime pas de votre système ou du disque.</span><span class="sxs-lookup"><span data-stu-id="f6c46-145">The `Remove-Module` cmdlet removes modules from memory in your current PowerShell session, it doesn't remove them from your system or from disk.</span></span>

## <a name="parameters"></a><span data-ttu-id="f6c46-146">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6c46-146">Parameters</span></span>

<span data-ttu-id="f6c46-147">N’attribuez pas de valeurs de manière statique !</span><span class="sxs-lookup"><span data-stu-id="f6c46-147">Don't statically assign values!</span></span> <span data-ttu-id="f6c46-148">Utilisez des paramètres et des variables.</span><span class="sxs-lookup"><span data-stu-id="f6c46-148">Use parameters and variables.</span></span> <span data-ttu-id="f6c46-149">Pour nommer vos paramètres, utilisez les mêmes noms de paramètres que les applets de commande par défaut chaque fois que cela est possible.</span><span class="sxs-lookup"><span data-stu-id="f6c46-149">When it comes to naming your parameters, use the same name as the default cmdlets for your parameter names whenever possible.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="f6c46-150">Pourquoi ai-je utilisé **ComputerName** et non **Computer**, **ServerName** ou **Host** comme nom de paramètre ?</span><span class="sxs-lookup"><span data-stu-id="f6c46-150">Why did I use **ComputerName** and not **Computer**, **ServerName**, or **Host** for my parameter name?</span></span> <span data-ttu-id="f6c46-151">C’est parce que je voulais que ma fonction suive les conventions des applets de commande par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6c46-151">It's because I wanted my function standardized like the default cmdlets.</span></span>

<span data-ttu-id="f6c46-152">Je vais créer une fonction pour obtenir toutes les commandes sur un système et retourner le nombre d’entre elles qui ont des noms de paramètres spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f6c46-152">I'll create a function to query all of the commands on a system and return the number of them that have specific parameter names.</span></span>

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

<span data-ttu-id="f6c46-153">Comme vous pouvez le voir dans les résultats ci-dessous, 39 commandes ont un paramètre **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-153">As you can see in the results shown below, 39 commands that have a **ComputerName** parameter.</span></span> <span data-ttu-id="f6c46-154">Il n’y a pas d’applets de commande avec les paramètres **Computer**, **ServerName**, **Host** ou **Machine**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-154">There aren't any cmdlets that have parameters such as **Computer**, **ServerName**, **Host**, or **Machine**.</span></span>

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

<span data-ttu-id="f6c46-155">Je vous recommande aussi d’utiliser la même casse dans vos noms de paramètres que les applets de commande par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6c46-155">I also recommend using the same case for your parameter names as the default cmdlets.</span></span> <span data-ttu-id="f6c46-156">Par exemple, utilisez `ComputerName`, pas `computername`.</span><span class="sxs-lookup"><span data-stu-id="f6c46-156">Use `ComputerName`, not `computername`.</span></span> <span data-ttu-id="f6c46-157">Ainsi, vos fonctions auront l’apparence des applets de commande par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6c46-157">This makes your functions look and feel like the default cmdlets.</span></span> <span data-ttu-id="f6c46-158">Les personnes qui sont déjà familiarisées avec PowerShell ne seront pas dépaysées.</span><span class="sxs-lookup"><span data-stu-id="f6c46-158">People who are already familiar with PowerShell will feel right at home.</span></span>

## <a name="advanced-functions"></a><span data-ttu-id="f6c46-159">Fonctions avancées</span><span class="sxs-lookup"><span data-stu-id="f6c46-159">Advanced Functions</span></span>

<span data-ttu-id="f6c46-160">Transformer une fonction dans PowerShell en fonction avancée est une opération très simple.</span><span class="sxs-lookup"><span data-stu-id="f6c46-160">Turning a function in PowerShell into an advanced function is really simple.</span></span> <span data-ttu-id="f6c46-161">L’une des différences entre une fonction et une fonction avancée est que plusieurs paramètres courants sont automatiquement ajoutés aux fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="f6c46-161">One of the differences between a function and an advanced function is that advanced functions have a number of common parameters that are added to the function automatically.</span></span> <span data-ttu-id="f6c46-162">**Verbose** et **Debug** sont deux de ces paramètres courants.</span><span class="sxs-lookup"><span data-stu-id="f6c46-162">These common parameters include parameters such as **Verbose** and **Debug**.</span></span>

<span data-ttu-id="f6c46-163">Je vais d’abord parler de la fonction `Test-MrParameter` qui a été utilisée dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="f6c46-163">I'll start out with the `Test-MrParameter` function that was used in the previous section.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="f6c46-164">Ce que je veux vous montrer, c’est que la fonction `Test-MrParameter` n’a pas de paramètres courants.</span><span class="sxs-lookup"><span data-stu-id="f6c46-164">What I want you to notice is that the `Test-MrParameter` function doesn't have any common parameters.</span></span> <span data-ttu-id="f6c46-165">Il existe plusieurs façons de voir les paramètres courants.</span><span class="sxs-lookup"><span data-stu-id="f6c46-165">There are a couple of different ways to see the common parameters.</span></span> <span data-ttu-id="f6c46-166">La première consiste à afficher la syntaxe à l’aide de `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="f6c46-166">One is by viewing the syntax using `Get-Command`.</span></span>

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

<span data-ttu-id="f6c46-167">Une autre consiste à parcourir les paramètres avec `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="f6c46-167">Another is to drill down into the parameters with `Get-Command`.</span></span>

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

<span data-ttu-id="f6c46-168">Vous ajoutez ensuite `CmdletBinding` pour transformer la fonction en fonction avancée.</span><span class="sxs-lookup"><span data-stu-id="f6c46-168">Add `CmdletBinding` to turn the function into an advanced function.</span></span>

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="f6c46-169">L’ajout de `CmdletBinding` entraîne l’ajout automatique des paramètres courants.</span><span class="sxs-lookup"><span data-stu-id="f6c46-169">Adding `CmdletBinding` adds the common parameters automatically.</span></span> <span data-ttu-id="f6c46-170">`CmdletBinding` requiert un bloc `param`, mais le bloc `param` peut être vide.</span><span class="sxs-lookup"><span data-stu-id="f6c46-170">`CmdletBinding` requires a `param` block, but the `param` block can be empty.</span></span>

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

<span data-ttu-id="f6c46-171">L’exploration des paramètres avec `Get-Command` affiche les noms de paramètres réels, y compris des paramètres courants.</span><span class="sxs-lookup"><span data-stu-id="f6c46-171">Drilling down into the parameters with `Get-Command` shows the actual parameter names including the common ones.</span></span>

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="f6c46-172">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="f6c46-172">SupportsShouldProcess</span></span>

<span data-ttu-id="f6c46-173">`SupportsShouldProcess` ajoute les paramètres **WhatIf** et **Confirm**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-173">`SupportsShouldProcess` adds **WhatIf** and **Confirm** parameters.</span></span> <span data-ttu-id="f6c46-174">Ces paramètres sont nécessaires uniquement pour les commandes de modification.</span><span class="sxs-lookup"><span data-stu-id="f6c46-174">These are only needed for commands that make changes.</span></span>

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="f6c46-175">Vous voyez maintenant les paramètres **WhatIf** et **Confirm**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-175">Notice that there are now **WhatIf** and **Confirm** parameters.</span></span>

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="f6c46-176">Ici encore, vous pouvez utiliser `Get-Command` pour retourner une liste des noms de paramètres réels, avec ceux des paramètres courants plus WhatIf et Confirm.</span><span class="sxs-lookup"><span data-stu-id="f6c46-176">Once again, you can also use `Get-Command` to return a list of the actual parameter names including the common ones along with WhatIf and Confirm.</span></span>

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a><span data-ttu-id="f6c46-177">Validation des paramètres</span><span class="sxs-lookup"><span data-stu-id="f6c46-177">Parameter Validation</span></span>

<span data-ttu-id="f6c46-178">La validation de l’entrée doit se faire très tôt.</span><span class="sxs-lookup"><span data-stu-id="f6c46-178">Validate input early on.</span></span> <span data-ttu-id="f6c46-179">Quel intérêt y aurait-il à laisser votre code s’exécuter s’il ne trouve pas l’entrée valide dont il a besoin ?</span><span class="sxs-lookup"><span data-stu-id="f6c46-179">Why allow your code to continue on a path when it's not possible to run without valid input?</span></span>

<span data-ttu-id="f6c46-180">Définissez toujours le type des variables utilisées pour vos paramètres (en clair, spécifiez un type de données).</span><span class="sxs-lookup"><span data-stu-id="f6c46-180">Always type the variables that are being used for your parameters (specify a datatype).</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="f6c46-181">Dans l’exemple précédent, j’ai spécifié **String** comme type de données pour le paramètre **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-181">In the previous example, I've specified **String** as the datatype for the **ComputerName** parameter.</span></span> <span data-ttu-id="f6c46-182">Un seul nom d’ordinateur peut donc être spécifié.</span><span class="sxs-lookup"><span data-stu-id="f6c46-182">This causes it to allow only a single computer name to be specified.</span></span> <span data-ttu-id="f6c46-183">Si plusieurs noms d’ordinateur sont spécifiés sous forme d’une liste séparée par des virgules, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="f6c46-183">If more than one computer name is specified via a comma-separated list, an error is generated.</span></span>

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

<span data-ttu-id="f6c46-184">Le problème avec la définition actuelle est qu’il est possible d’omettre la valeur du paramètre **ComputerName**, alors qu’une valeur est attendue pour que la fonction puisse s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="f6c46-184">The problem with the current definition is that it's valid to omit the value of the **ComputerName** parameter, but a value is required for the function to complete successfully.</span></span> <span data-ttu-id="f6c46-185">C’est là où l’attribut de paramètre `Mandatory` est utile.</span><span class="sxs-lookup"><span data-stu-id="f6c46-185">This is where the `Mandatory` parameter attribute comes in handy.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="f6c46-186">La syntaxe utilisée dans l’exemple précédent est compatible avec PowerShell 3.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f6c46-186">The syntax used in the previous example is PowerShell version 3.0 and higher compatible.</span></span>
<span data-ttu-id="f6c46-187">La syntaxe `[Parameter(Mandatory=$true)]` doit être utilisée à la place pour rendre la fonction compatible avec PowerShell version 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f6c46-187">`[Parameter(Mandatory=$true)]` could be specified instead to make the function compatible with PowerShell version 2.0 and higher.</span></span> <span data-ttu-id="f6c46-188">Maintenant que le paramètre **ComputerName** est rendu obligatoire, si aucun n’est spécifié, la fonction demandera d’en spécifier un.</span><span class="sxs-lookup"><span data-stu-id="f6c46-188">Now that the **ComputerName** is required, if one isn't specified, the function will prompt for one.</span></span>

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

<span data-ttu-id="f6c46-189">Si vous voulez autoriser plusieurs valeurs pour le paramètre **ComputerName**, choisissez le type de données **String** et spécifiez-le entre deux crochets ouvert et fermé pour autoriser un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="f6c46-189">If you want to allow for more than one value for the **ComputerName** parameter, use the **String** datatype but add open and closed square brackets to the datatype to allow for an array of strings.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="f6c46-190">Vous voudrez peut-être spécifier une valeur par défaut à utiliser pour le paramètre **ComputerName** quand aucune valeur n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f6c46-190">Maybe you want to specify a default value for the **ComputerName** parameter if one isn't specified.</span></span>
<span data-ttu-id="f6c46-191">Le problème est que l’utilisation de valeurs par défaut n’est pas possible avec des paramètres obligatoires.</span><span class="sxs-lookup"><span data-stu-id="f6c46-191">The problem is that default values can't be used with mandatory parameters.</span></span> <span data-ttu-id="f6c46-192">À la place, vous devrez utiliser l’attribut de validation de paramètre `ValidateNotNullOrEmpty` avec une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6c46-192">Instead, you'll need to use the `ValidateNotNullOrEmpty` parameter validation attribute with a default value.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="f6c46-193">Même si vous définissez une valeur par défaut, évitez d’utiliser des valeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="f6c46-193">Even when setting a default value, try not to use static values.</span></span> <span data-ttu-id="f6c46-194">Dans l’exemple précédent, `$env:COMPUTERNAME` est utilisé comme valeur par défaut, qui est automatiquement remplacée par le nom de l’ordinateur local si aucune valeur n’est fournie.</span><span class="sxs-lookup"><span data-stu-id="f6c46-194">In the previous example, `$env:COMPUTERNAME` is used as the default value, which is automatically translated into the local computer name if a value is not provided.</span></span>

## <a name="verbose-output"></a><span data-ttu-id="f6c46-195">Sortie détaillée</span><span class="sxs-lookup"><span data-stu-id="f6c46-195">Verbose Output</span></span>

<span data-ttu-id="f6c46-196">Bien que les commentaires inline soient utiles, en particulier si vous écrivez du code complexe, ils ne sont jamais vus par les utilisateurs, sauf par ceux qui examinent le code de près.</span><span class="sxs-lookup"><span data-stu-id="f6c46-196">While inline comments are useful, especially if you're writing some complex code, they never get seen by users unless they look into the code itself.</span></span>

<span data-ttu-id="f6c46-197">La fonction illustrée dans l’exemple suivant contient un commentaire inline dans la boucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="f6c46-197">The function shown in the following example has an inline comment in the `foreach` loop.</span></span> <span data-ttu-id="f6c46-198">Ce commentaire particulier n’est pas difficile à localiser, mais imaginez ce que cela serait si la fonction incluait des centaines de lignes de code.</span><span class="sxs-lookup"><span data-stu-id="f6c46-198">While this particular comment may not be that difficult to locate, imagine if the function included hundreds of lines of code.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

<span data-ttu-id="f6c46-199">Il est préférable d’utiliser la fonction `Write-Verbose` au lieu de commentaires inline.</span><span class="sxs-lookup"><span data-stu-id="f6c46-199">A better option is to use `Write-Verbose` instead of inline comments.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

<span data-ttu-id="f6c46-200">Quand la fonction est appelée sans le paramètre **Verbose**, la sortie détaillée ne s’affiche pas.</span><span class="sxs-lookup"><span data-stu-id="f6c46-200">When the function is called without the **Verbose** parameter, the verbose output won't be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

<span data-ttu-id="f6c46-201">Si elle est appelée avec le paramètre **Verbose**, la sortie détaillée s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f6c46-201">When it's called with the **Verbose** parameter, the verbose output will be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a><span data-ttu-id="f6c46-202">Entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="f6c46-202">Pipeline Input</span></span>

<span data-ttu-id="f6c46-203">Si vous souhaitez que votre fonction accepte l’entrée de pipeline, vous devez ajouter du code supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="f6c46-203">When you want your function to accept pipeline input, some additional coding is necessary.</span></span> <span data-ttu-id="f6c46-204">Comme mentionné plus haut dans ce livre, les commandes peuvent accepter l’entrée de pipeline **par valeur** (par type) ou **par nom de propriété**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-204">As mentioned earlier in this book, commands can accept pipeline input **by value** (by type) or **by property name**.</span></span> <span data-ttu-id="f6c46-205">Vous pouvez écrire vos fonctions comme des commandes natives pour qu’elles acceptent l’un de ces types d’entrée ou les deux.</span><span class="sxs-lookup"><span data-stu-id="f6c46-205">You can write your functions just like the native commands so that they accept either one or both of these types of input.</span></span>

<span data-ttu-id="f6c46-206">Pour accepter l’entrée de pipeline **par valeur**, spécifiez l’attribut `ValueFromPipeline` pour ce paramètre particulier.</span><span class="sxs-lookup"><span data-stu-id="f6c46-206">To accept pipeline input **by value**, specified the `ValueFromPipeline` parameter attribute for that particular parameter.</span></span> <span data-ttu-id="f6c46-207">Gardez à l’esprit que l’entrée de pipeline **par valeur** peut être acceptée uniquement par un seul paramètre de chaque type de données.</span><span class="sxs-lookup"><span data-stu-id="f6c46-207">Keep in mind that you can only accept pipeline input **by value** from one of each datatype.</span></span> <span data-ttu-id="f6c46-208">Par exemple, si vous avez deux paramètres qui acceptent une entrée de type chaîne, un seul d’entre eux peut accepter l’entrée de pipeline **par valeur**. Si vous la spécifiez pour les deux paramètres chaîne, l’entrée de pipeline ne saura pas à quel paramètre elle doit être liée.</span><span class="sxs-lookup"><span data-stu-id="f6c46-208">For example, if you have two parameters that accept string input, only one of those can accept pipeline input **by value** because if you specified it for both of the string parameters, the pipeline input wouldn't know which one to bind to.</span></span> <span data-ttu-id="f6c46-209">C’est une autre raison pour laquelle je préfère appeler ce type d’entrée de pipeline _par type_ au lieu de **par valeur**.</span><span class="sxs-lookup"><span data-stu-id="f6c46-209">This is another reason I call this type of pipeline input _by type_ instead of **by value**.</span></span>

<span data-ttu-id="f6c46-210">L’entrée de pipeline fournit un seul élément à la fois, de la même façon que les éléments sont traités dans une boucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="f6c46-210">Pipeline input comes in one item at a time similar to the way items are handled in a `foreach` loop.</span></span>
<span data-ttu-id="f6c46-211">Au minimum, un bloc `process` est requis pour traiter chacun de ces éléments si vous acceptez un tableau en entrée.</span><span class="sxs-lookup"><span data-stu-id="f6c46-211">At a minimum, a `process` block is required to process each of these items if you're accepting an array as input.</span></span> <span data-ttu-id="f6c46-212">Si vous acceptez une seule valeur en entrée, un bloc `process` n’est pas nécessaire, mais je vous conseille quand même de le spécifier par souci de cohérence.</span><span class="sxs-lookup"><span data-stu-id="f6c46-212">If you're only accepting a single value as input, a `process` block isn't necessary, but I still recommend specifying it for consistency.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

<span data-ttu-id="f6c46-213">L’acceptation de l’entrée de pipeline **par nom de propriété** est similaire, à ceci près qu’elle est spécifiée avec l’attribut de paramètre `ValueFromPipelineByPropertyName` et qu’elle peut être spécifiée pour n’importe quel nombre de paramètres quel que soit le type de données.</span><span class="sxs-lookup"><span data-stu-id="f6c46-213">Accepting pipeline input **by property name** is similar except it's specified with the `ValueFromPipelineByPropertyName` parameter attribute and it can be specified for any number of parameters regardless of datatype.</span></span> <span data-ttu-id="f6c46-214">Ce qu’il faut retenir est que la sortie de la commande fournie en entrée doit avoir un nom de propriété qui correspond au nom du paramètre ou un alias de paramètre de votre fonction.</span><span class="sxs-lookup"><span data-stu-id="f6c46-214">The key is that the output of the command that's being piped in has to have a property name that matches the name of the parameter or a parameter alias of your function.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

<span data-ttu-id="f6c46-215">Les blocs `BEGIN` et `END` sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="f6c46-215">`BEGIN` and `END` blocks are optional.</span></span> <span data-ttu-id="f6c46-216">`BEGIN` est spécifié avant le bloc `PROCESS` et est utilisé pour effectuer tout travail initial avant que les éléments ne soient reçus du pipeline.</span><span class="sxs-lookup"><span data-stu-id="f6c46-216">`BEGIN` would be specified before the `PROCESS` block and is used to perform any initial work prior to the items being received from the pipeline.</span></span> <span data-ttu-id="f6c46-217">Il est important de comprendre ce point.</span><span class="sxs-lookup"><span data-stu-id="f6c46-217">This is important to understand.</span></span> <span data-ttu-id="f6c46-218">Les valeurs reçues ne sont pas accessibles dans le bloc `BEGIN`.</span><span class="sxs-lookup"><span data-stu-id="f6c46-218">Values that are piped in are not accessible in the `BEGIN` block.</span></span> <span data-ttu-id="f6c46-219">Le bloc `END` est spécifié après le bloc `PROCESS` et est utilisé pour le nettoyage une fois que tous les éléments reçus ont été traités.</span><span class="sxs-lookup"><span data-stu-id="f6c46-219">The `END` block would be specified after the `PROCESS` block and is used for cleanup once all of the items that are piped in have been processed.</span></span>

## <a name="error-handling"></a><span data-ttu-id="f6c46-220">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="f6c46-220">Error Handling</span></span>

<span data-ttu-id="f6c46-221">La fonction illustrée dans l’exemple suivant génère une exception non prise en charge quand un ordinateur ne peut pas être contacté.</span><span class="sxs-lookup"><span data-stu-id="f6c46-221">The function shown in the following example generates an unhandled exception when a computer can't be contacted.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

<span data-ttu-id="f6c46-222">Il y a plusieurs manières de gérer les erreurs dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c46-222">There are a couple of different ways to handle errors in PowerShell.</span></span> <span data-ttu-id="f6c46-223">L’utilisation de `Try/Catch` est le moyen le plus moderne.</span><span class="sxs-lookup"><span data-stu-id="f6c46-223">`Try/Catch` is the more modern way to handle errors.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="f6c46-224">Bien que la fonction illustrée dans l’exemple précédent utilise la gestion des erreurs, elle génère également une exception non prise en charge, car la commande ne génère pas d’erreur avec fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6c46-224">Although the function shown in the previous example uses error handling, it also generates an unhandled exception because the command doesn't generate a terminating error.</span></span> <span data-ttu-id="f6c46-225">Il est important de comprendre aussi ce point.</span><span class="sxs-lookup"><span data-stu-id="f6c46-225">This is also important to understand.</span></span> <span data-ttu-id="f6c46-226">Seules les erreurs avec fin d’exécution sont interceptées.</span><span class="sxs-lookup"><span data-stu-id="f6c46-226">Only terminating errors are caught.</span></span> <span data-ttu-id="f6c46-227">Spécifiez le paramètre **ErrorAction** avec la valeur **Stop** pour transformer une erreur sans fin d’exécution en erreur avec fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6c46-227">Specify the **ErrorAction** parameter with **Stop** as the value to turn a non-terminating error into a terminating one.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="f6c46-228">Ne modifiez pas la variable `$ErrorActionPreference` globale sauf si cela est absolument nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f6c46-228">Don't modify the global `$ErrorActionPreference` variable unless absolutely necessary.</span></span> <span data-ttu-id="f6c46-229">Si vous utilisez du code comme .NET directement dans votre fonction PowerShell, vous ne pouvez pas spécifier le paramètre **ErrorAction** dans la commande elle-même.</span><span class="sxs-lookup"><span data-stu-id="f6c46-229">If you're using something like .NET directly from within your PowerShell function, you can't specify the **ErrorAction** on the command itself.</span></span> <span data-ttu-id="f6c46-230">Dans ce scénario, vous devrez peut-être modifier temporairement la variable `$ErrorActionPreference` globale ; si vous le faites, n’oubliez pas de rétablir la variable initiale tout de suite après avoir essayé la commande.</span><span class="sxs-lookup"><span data-stu-id="f6c46-230">In that scenario, you might need to change the global `$ErrorActionPreference` variable, but if you do change it, change it back immediately after trying the command.</span></span>

## <a name="comment-based-help"></a><span data-ttu-id="f6c46-231">Aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="f6c46-231">Comment-Based Help</span></span>

<span data-ttu-id="f6c46-232">Une bonne pratique reconnue est d’ajouter une aide basée sur les commentaires à vos fonctions afin que les personnes avec lesquelles vous partagez les fonctions sachent comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="f6c46-232">It's considered to be a best practice to add comment based help to your functions so the people you're sharing them with will know how to use them.</span></span>

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

<span data-ttu-id="f6c46-233">Quand vous ajoutez une aide basée sur les commentaires à vos fonctions, l’aide associée peut être obtenue de la même façon que les commandes intégrées par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6c46-233">When you add comment based help to your functions, help can be retrieved for them just like the default built-in commands.</span></span>

<span data-ttu-id="f6c46-234">Toute la syntaxe à respecter pour écrire une fonction dans PowerShell peut paraître très compliquée, surtout pour les développeurs débutants.</span><span class="sxs-lookup"><span data-stu-id="f6c46-234">All of the syntax for writing a function in PowerShell can seem overwhelming especially for someone who is just getting started.</span></span> <span data-ttu-id="f6c46-235">Souvent, quand je ne me souviens pas de la syntaxe d’un élément, j’ouvre une deuxième copie de l’environnement ISE sur un autre moniteur pour voir l’extrait de code « Cmdlet (advanced function) - Complete » pendant que je tape le code de ma fonction.</span><span class="sxs-lookup"><span data-stu-id="f6c46-235">Often times if I can't remember the syntax for something, I'll open a second copy of the ISE on a separate monitor and view the "Cmdlet (advanced function) - Complete" snippet while typing in the code for my function.</span></span> <span data-ttu-id="f6c46-236">Vous pouvez accéder aux extraits de code dans PowerShell ISE en appuyant sur les touches <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f6c46-236">Snippets can be accessed in the PowerShell ISE using the <kbd>Ctrl</kbd>+<kbd>J</kbd> key combination.</span></span>

## <a name="summary"></a><span data-ttu-id="f6c46-237">Résumé</span><span class="sxs-lookup"><span data-stu-id="f6c46-237">Summary</span></span>

<span data-ttu-id="f6c46-238">Dans ce chapitre, vous avez appris les bases de l’écriture de fonctions dans PowerShell. Vous avez appris comment transformer une fonction en fonction avancée, et vous avez vu certains des points les plus importants à connaître pour écrire des fonctions PowerShell, comme la validation de paramètres, la sortie détaillée, l’entrée de pipeline, la gestion des erreurs et l’aide basée sur les commentaires.</span><span class="sxs-lookup"><span data-stu-id="f6c46-238">In this chapter you've learned the basics of writing functions in PowerShell to include how to turn a function into an advanced function and some of the more important elements that you should consider when writing PowerShell functions such as parameter validation, verbose output, pipeline input, error handling, and comment based help.</span></span>

## <a name="review"></a><span data-ttu-id="f6c46-239">Révision</span><span class="sxs-lookup"><span data-stu-id="f6c46-239">Review</span></span>

1. <span data-ttu-id="f6c46-240">Comment pouvez-vous obtenir une liste des verbes approuvés dans PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="f6c46-240">How do you obtain a list of approved verbs in PowerShell?</span></span>
1. <span data-ttu-id="f6c46-241">Comment pouvez-vous transformer une fonction PowerShell en fonction avancée ?</span><span class="sxs-lookup"><span data-stu-id="f6c46-241">How do you turn a PowerShell function into an advanced function?</span></span>
1. <span data-ttu-id="f6c46-242">Quand devez-vous ajouter les paramètres **WhatIf** et **Confirm** à vos fonctions PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="f6c46-242">When should **WhatIf** and **Confirm** parameters be added to your PowerShell functions?</span></span>
1. <span data-ttu-id="f6c46-243">Comment faites-vous pour transformer une erreur sans fin d’exécution en erreur avec fin d’exécution ?</span><span class="sxs-lookup"><span data-stu-id="f6c46-243">How do you turn a non-terminating error into a terminating one?</span></span>
1. <span data-ttu-id="f6c46-244">Pourquoi devez-vous ajouter une aide basée sur les commentaires à vos fonctions ?</span><span class="sxs-lookup"><span data-stu-id="f6c46-244">Why should you add comment based help to your functions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="f6c46-245">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="f6c46-245">Recommended Reading</span></span>

- <span data-ttu-id="f6c46-246">[about_Functions][]</span><span class="sxs-lookup"><span data-stu-id="f6c46-246">[about_Functions][]</span></span>
- <span data-ttu-id="f6c46-247">[about_Functions_Advanced_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="f6c46-247">[about_Functions_Advanced_Parameters][]</span></span>
- <span data-ttu-id="f6c46-248">[about_CommonParameters][]</span><span class="sxs-lookup"><span data-stu-id="f6c46-248">[about_CommonParameters][]</span></span>
- <span data-ttu-id="f6c46-249">[about_Functions_CmdletBindingAttribute][]</span><span class="sxs-lookup"><span data-stu-id="f6c46-249">[about_Functions_CmdletBindingAttribute][]</span></span>
- <span data-ttu-id="f6c46-250">[about_Functions_Advanced][]</span><span class="sxs-lookup"><span data-stu-id="f6c46-250">[about_Functions_Advanced][]</span></span>
- <span data-ttu-id="f6c46-251">[about_Try_Catch_Finally][]</span><span class="sxs-lookup"><span data-stu-id="f6c46-251">[about_Try_Catch_Finally][]</span></span>
- <span data-ttu-id="f6c46-252">[about_Comment_Based_Help][]</span><span class="sxs-lookup"><span data-stu-id="f6c46-252">[about_Comment_Based_Help][]</span></span>
- <span data-ttu-id="f6c46-253">[Vidéo : PowerShell Toolmaking with Advanced Functions and Script Modules][]</span><span class="sxs-lookup"><span data-stu-id="f6c46-253">[Video: PowerShell Toolmaking with Advanced Functions and Script Modules][]</span></span>

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[Vidéo : PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Video: PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Casse Pascal]: /dotnet/standard/design-guidelines/capitalization-conventions
[Pascal case]: /dotnet/standard/design-guidelines/capitalization-conventions
