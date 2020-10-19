---
ms.date: 10/15/2020
title: Utilisation des fonctionnalités expérimentales dans PowerShell
description: Répertorie les fonctionnalités expérimentales actuellement disponibles et leur mode d’utilisation.
ms.openlocfilehash: e98b1222755f3d4ffbd432af6b01d56f63307bb2
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156573"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="2ae73-103">Utilisation des fonctionnalités expérimentales dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ae73-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="2ae73-104">La prise en charge des Fonctionnalités expérimentales dans PowerShell fournit un mécanisme permettant aux fonctionnalités expérimentales de coexister avec les fonctionnalités stables existantes dans PowerShell ou les modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ae73-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="2ae73-105">Une fonctionnalité expérimentale est une fonctionnalité dans laquelle la conception n’est pas finalisée.</span><span class="sxs-lookup"><span data-stu-id="2ae73-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="2ae73-106">Les utilisateurs peuvent tester la fonctionnalité et fournir des commentaires.</span><span class="sxs-lookup"><span data-stu-id="2ae73-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="2ae73-107">Lorsqu’une fonctionnalité expérimentale est finalisée, les modifications apportées à la conception deviennent des changements cassants.</span><span class="sxs-lookup"><span data-stu-id="2ae73-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="2ae73-108">Les fonctionnalités expérimentales ne sont pas destinées à être utilisées en production, car les changements peuvent être cassants.</span><span class="sxs-lookup"><span data-stu-id="2ae73-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="2ae73-109">Les fonctionnalités expérimentales ne sont pas officiellement prises en charge.</span><span class="sxs-lookup"><span data-stu-id="2ae73-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="2ae73-110">Toutefois, nous apprécions de recevoir des commentaires et des rapports de bogues.</span><span class="sxs-lookup"><span data-stu-id="2ae73-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="2ae73-111">Vous pouvez consigner les problèmes dans le [référentiel source GitHub](https://github.com/PowerShell/PowerShell/issues/new/choose).</span><span class="sxs-lookup"><span data-stu-id="2ae73-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="2ae73-112">Pour plus d’informations sur l’activation ou la désactivation de ces fonctionnalités, consultez [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span><span class="sxs-lookup"><span data-stu-id="2ae73-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="2ae73-113">Fonctionnalités disponibles</span><span class="sxs-lookup"><span data-stu-id="2ae73-113">Available features</span></span>

<span data-ttu-id="2ae73-114">Cet article décrit les fonctionnalités expérimentales disponibles et leur mode d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="2ae73-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="2ae73-115">Nom</span><span class="sxs-lookup"><span data-stu-id="2ae73-115">Name</span></span>                            |   <span data-ttu-id="2ae73-116">6.2</span><span class="sxs-lookup"><span data-stu-id="2ae73-116">6.2</span></span>   |   <span data-ttu-id="2ae73-117">7.0</span><span class="sxs-lookup"><span data-stu-id="2ae73-117">7.0</span></span>   |   <span data-ttu-id="2ae73-118">7.1</span><span class="sxs-lookup"><span data-stu-id="2ae73-118">7.1</span></span>   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: |
| <span data-ttu-id="2ae73-119">PSTempDrive (standard dans PS 7.0+)</span><span class="sxs-lookup"><span data-stu-id="2ae73-119">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |         |
| <span data-ttu-id="2ae73-120">PSUseAbbreviationExpansion (standard dans PS 7.0+)</span><span class="sxs-lookup"><span data-stu-id="2ae73-120">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |         |
| <span data-ttu-id="2ae73-121">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="2ae73-121">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; | &check; |
| <span data-ttu-id="2ae73-122">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="2ae73-122">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; | &check; |
| <span data-ttu-id="2ae73-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="2ae73-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; | &check; |
| <span data-ttu-id="2ae73-124">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="2ae73-124">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; | &check; |
| <span data-ttu-id="2ae73-125">PSNullConditionalOperators (standard dans PS 7.1+)</span><span class="sxs-lookup"><span data-stu-id="2ae73-125">PSNullConditionalOperators (mainstream in PS 7.1+)</span></span>         |         | &check; |         |
| <span data-ttu-id="2ae73-126">PSUnixFileStat (non-Windows uniquement)</span><span class="sxs-lookup"><span data-stu-id="2ae73-126">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; | &check; |
| <span data-ttu-id="2ae73-127">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="2ae73-127">PSNativePSPathResolution</span></span>                                   |         |         | &check; |
| <span data-ttu-id="2ae73-128">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="2ae73-128">PSCultureInvariantReplaceOperator</span></span>                          |         |         | &check; |
| <span data-ttu-id="2ae73-129">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="2ae73-129">PSNotApplyErrorActionToStderr</span></span>                              |         |         | &check; |
| <span data-ttu-id="2ae73-130">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="2ae73-130">PSSubsystemPluginModel</span></span>                                     |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="2ae73-131">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="2ae73-131">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="2ae73-132">Dans PowerShell 7.0, l’expérience active le paramètre **BreakAll** sur les cmdlets `Debug-Runspace` et `Debug-Job` pour permettre aux utilisateurs de décider s’ils veulent que PowerShell s’arrête immédiatement à l’emplacement actuel lorsqu’ils attachent un débogueur.</span><span class="sxs-lookup"><span data-stu-id="2ae73-132">In PowerShell 7.0, the experiment enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

<span data-ttu-id="2ae73-133">Dans PowerShell 7.1, cette expérimentation ajoute également le paramètre **Runspace** aux applets de commande `*-PSBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-133">In PowerShell 7.1, this experiment also adds the **Runspace** parameter to the `*-PSBreakpoint` cmdlets.</span></span>

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

<span data-ttu-id="2ae73-134">Le paramètre **Runspace** spécifie un objet **Runspace** pour interagir avec des points d’arrêt dans l’instance d’exécution spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ae73-134">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

<span data-ttu-id="2ae73-135">Dans cet exemple, un travail est démarré et un point d’arrêt est défini pour s’arrêter lors de l’exécution du `Set-PSBreakPoint`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-135">In this example, a job is started and a breakpoint is set to break when the `Set-PSBreakPoint` is run.</span></span> <span data-ttu-id="2ae73-136">L’instance d’exécution est stockée dans une variable et passée à la commande `Get-PSBreakPoint` avec le paramètre **Runspace**.</span><span class="sxs-lookup"><span data-stu-id="2ae73-136">The runspace is stored in a variable and passed to the `Get-PSBreakPoint` command with the **Runspace** parameter.</span></span> <span data-ttu-id="2ae73-137">Vous pouvez ensuite inspecter le point d’arrêt dans la variable `$breakpoint`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-137">You can then inspect the breakpoint in the `$breakpoint` variable.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="2ae73-138">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="2ae73-138">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="2ae73-139">Recommande des commandes potentielles en fonction de la recherche de correspondance approximative après **CommandNotFoundException**.</span><span class="sxs-lookup"><span data-stu-id="2ae73-139">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="2ae73-140">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="2ae73-140">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="2ae73-141">Lorsque l’opérande gauche dans une instruction opérateur `-replace` n’est pas une chaîne, cet opérande est converti en chaîne.</span><span class="sxs-lookup"><span data-stu-id="2ae73-141">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="2ae73-142">Lorsque cette fonctionnalité est désactivée, l’opérateur `-replace` effectue une conversion de chaîne dépendante de la culture.</span><span class="sxs-lookup"><span data-stu-id="2ae73-142">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="2ae73-143">Par exemple, si votre culture est définie sur Français (fr), la valeur `1.2` est convertie en chaîne `1,2`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-143">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="2ae73-144">Avec la fonctionnalité activée :</span><span class="sxs-lookup"><span data-stu-id="2ae73-144">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="2ae73-145">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="2ae73-145">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="2ae73-146">Active la compilation en MOF sur les systèmes non-Windows et permet l’utilisation de `Invoke-DSCResource` sans LCM.</span><span class="sxs-lookup"><span data-stu-id="2ae73-146">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="2ae73-147">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="2ae73-147">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="2ae73-148">Cette fonctionnalité examine la commande tapée dans l’interpréteur de commandes, et si toutes les commandes sont des commandes proxy de communication à distance implicites qui forment un pipeline simple, les commandes sont regroupées et appelées en tant que pipeline à distance unique.</span><span class="sxs-lookup"><span data-stu-id="2ae73-148">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="2ae73-149">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ae73-149">Example:</span></span>

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

<span data-ttu-id="2ae73-150">Comme indiqué ci-dessus, avec la fonctionnalité de traitement par lot activée, les trois commandes proxy de communication à distance implicite, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, s’exécutent dans la session à distance et le résultat du pipeline est les seules données retournées au client.</span><span class="sxs-lookup"><span data-stu-id="2ae73-150">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="2ae73-151">Cela réduit la quantité de données qui circulent entre le client et la session à distance, et réduit également la quantité de sérialisation et de désérialisation d’objets.</span><span class="sxs-lookup"><span data-stu-id="2ae73-151">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="2ae73-152">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="2ae73-152">PSNativePSPathResolution</span></span>

<span data-ttu-id="2ae73-153">Si un chemin PSDrive qui utilise le fournisseur FileSystem est passé à une commande native, le chemin du fichier résolu est passé à la commande native.</span><span class="sxs-lookup"><span data-stu-id="2ae73-153">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="2ae73-154">Cela signifie qu’une commande comme `code temp:/test.txt` fonctionne à présent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="2ae73-154">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="2ae73-155">En outre, sur Windows, si le chemin commence par `~`, il est résolu en chemin d’accès complet et transmis à la commande native.</span><span class="sxs-lookup"><span data-stu-id="2ae73-155">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="2ae73-156">Dans les deux cas, le chemin est normalisé aux séparateurs de répertoire pour le système d’exploitation approprié.</span><span class="sxs-lookup"><span data-stu-id="2ae73-156">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="2ae73-157">Si le chemin n’est pas PSDrive ou `~` (sur Windows), la normalisation de chemin d’accès ne se produit pas</span><span class="sxs-lookup"><span data-stu-id="2ae73-157">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="2ae73-158">Si le chemin est placé entre guillemets simples, il n’est pas résolu et traité comme littéral</span><span class="sxs-lookup"><span data-stu-id="2ae73-158">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnotapplyerroractiontostderr"></a><span data-ttu-id="2ae73-159">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="2ae73-159">PSNotApplyErrorActionToStderr</span></span>

<span data-ttu-id="2ae73-160">Lorsque cette fonctionnalité expérimentale est activée, les enregistrements d’erreurs redirigés à partir de commandes natives, par exemple lors de l’utilisation d’opérateurs de redirection (`2>&1`), ne sont pas écrits dans la variable `$Error` et la variable de préférence `$ErrorActionPreference` n’affecte pas la sortie redirigée.</span><span class="sxs-lookup"><span data-stu-id="2ae73-160">When this experimental feature is enabled, error records redirected from native commands, like when using redirection operators (`2>&1`), are not written to the `$Error` variable and the preference variable `$ErrorActionPreference` does not affect the redirected output.</span></span>

<span data-ttu-id="2ae73-161">De nombreuses commandes natives écrivent dans `stderr` en tant que flux de remplacement pour obtenir des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2ae73-161">Many native commands write to `stderr` as an alternative stream for additional information.</span></span> <span data-ttu-id="2ae73-162">Ce comportement peut entraîner une confusion lors de l’examen des erreurs, ou les informations de sortie supplémentaires peuvent être perdues pour l’utilisateur si `$ErrorActionPreference` est défini sur un état qui désactive la sortie.</span><span class="sxs-lookup"><span data-stu-id="2ae73-162">This behavior can cause confusion when looking through errors or the additional output information can be lost to the user if `$ErrorActionPreference` is set to a state that mutes the output.</span></span>

<span data-ttu-id="2ae73-163">Quand une commande native a un code de sortie différent de zéro, `$?` a la valeur `$false`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-163">When a native command has a non-zero exit code, `$?` is set to `$false`.</span></span> <span data-ttu-id="2ae73-164">Si le code de sortie est égal à zéro, `$?` a la valeur `$true`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-164">If the exit code is zero, `$?` is set to `$true`.</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="2ae73-165">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="2ae73-165">PSNullConditionalOperators</span></span>

<span data-ttu-id="2ae73-166">Introduit de nouveaux opérateurs pour les opérateurs d’accès de membre conditionnel Null, `?.` et `?[]`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-166">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="2ae73-167">Les opérateurs d’accès de membre Null peuvent être utilisés sur des types scalaires et des types tableau.</span><span class="sxs-lookup"><span data-stu-id="2ae73-167">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="2ae73-168">Retourne la valeur du membre ayant fait l’objet d’un accès si la variable n’est pas Null.</span><span class="sxs-lookup"><span data-stu-id="2ae73-168">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="2ae73-169">Si la valeur de la variable est Null, retourne la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="2ae73-169">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="2ae73-170">La propriété `propname` fait l’objet d’un accès et sa valeur est retournée uniquement si `$x` n’est pas Null.</span><span class="sxs-lookup"><span data-stu-id="2ae73-170">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="2ae73-171">De même, l’indexeur est utilisé uniquement si `$x` n’a pas la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="2ae73-171">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="2ae73-172">Si `$x` est Null, alors Null est retourné.</span><span class="sxs-lookup"><span data-stu-id="2ae73-172">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="2ae73-173">Les opérateurs `?.` et `?[]` sont des opérateurs d’accès de membre et n’autorisent pas d’espace entre le nom de la variable et l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="2ae73-173">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="2ae73-174">Étant donné que PowerShell autorise `?` dans le cadre du nom de la variable, toute suppression d’ambiguïté est nécessaire lorsque les opérateurs sont utilisés sans espace entre le nom de la variable et l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="2ae73-174">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="2ae73-175">Pour lever l’ambiguïté, les variables doivent utiliser `{}` autour du nom de la variable, par exemple : `${x?}?.propertyName` ou `${y}?[0]`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-175">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

> [!NOTE]
> <span data-ttu-id="2ae73-176">Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2ae73-176">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="2ae73-177">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="2ae73-177">PSTempDrive</span></span>

<span data-ttu-id="2ae73-178">Crée le PSDrive `TEMP:` mappé au chemin du répertoire temporaire de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2ae73-178">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="2ae73-179">Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2ae73-179">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="2ae73-180">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="2ae73-180">PSUnixFileStat</span></span>

<span data-ttu-id="2ae73-181">Cette fonctionnalité offre un nouveau comportement permettant d’inclure des données de l’API **stat** Unix dans la sortie du fournisseur de système de fichiers pour faciliter l’affichage des fichiers plus similaire à Unix.</span><span class="sxs-lookup"><span data-stu-id="2ae73-181">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="2ae73-182">Elle ajoute une nouvelle propriété de note dans le fournisseur du système de fichiers nommé **UnixStat** qui inclut une expression commune de l’API `stat(2)` à partir du système de type Unix sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="2ae73-182">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="2ae73-183">La sortie de `Get-ChildItem` suivant doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2ae73-183">The output from `Get-ChildItem` should look something like this:</span></span>

```powershell
dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="2ae73-184">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="2ae73-184">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="2ae73-185">Cette fonctionnalité permet la saisie semi-automatique par tabulation des cmdlets et des fonctions abrégées :</span><span class="sxs-lookup"><span data-stu-id="2ae73-185">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="2ae73-186">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2ae73-186">For example:</span></span>

- <span data-ttu-id="2ae73-187">`i-psdf<tab>` retourne `Import-PowerShellDataFile`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-187">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="2ae73-188">`u-akvmssdr<tab>` retourne `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="2ae73-188">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="2ae73-189">Cela ne fonctionne que pour la saisie semi-automatique par tabulation (utilisation interactive), donc `i-psdf` n’est pas un nom de cmdlet valide dans un script.</span><span class="sxs-lookup"><span data-stu-id="2ae73-189">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="2ae73-190">Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2ae73-190">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="pssubsystempluginmodel"></a><span data-ttu-id="2ae73-191">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="2ae73-191">PSSubsystemPluginModel</span></span>

<span data-ttu-id="2ae73-192">Cette fonctionnalité active le modèle de plug-in de sous-système dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ae73-192">This feature enables the subsystem plugin model in PowerShell.</span></span> <span data-ttu-id="2ae73-193">La fonctionnalité permet de diviser les composants de `System.Management.Automation.dll` en sous-systèmes individuels qui résident dans leur propre assembly.</span><span class="sxs-lookup"><span data-stu-id="2ae73-193">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="2ae73-194">Cette division réduit l’encombrement de disque du moteur PowerShell principal et permet à ces composants de devenir des fonctionnalités facultatives pour une installation PowerShell minimale.</span><span class="sxs-lookup"><span data-stu-id="2ae73-194">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="2ae73-195">Actuellement, seul le sous-système **CommandPredictor** est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2ae73-195">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="2ae73-196">Ce sous-système est utilisé avec le module PSReadLine pour fournir des plug-ins de prédiction personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2ae73-196">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="2ae73-197">À l’avenir, **Job**, **CommandCompleter**, **Remoting** et d’autres composants pourraient être divisés en assemblys de sous-système en dehors de `System.Management.Automation.dll`.</span><span class="sxs-lookup"><span data-stu-id="2ae73-197">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

<span data-ttu-id="2ae73-198">La fonctionnalité expérimentale comprend une nouvelle applet de commande, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem).</span><span class="sxs-lookup"><span data-stu-id="2ae73-198">The experimental feature includes a new cmdlet, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem).</span></span> <span data-ttu-id="2ae73-199">Cette applet de commande est disponible uniquement lorsque la fonctionnalité est activée.</span><span class="sxs-lookup"><span data-stu-id="2ae73-199">This cmdlet is only available when the feature is enabled.</span></span> <span data-ttu-id="2ae73-200">Cette applet de commande retourne des informations sur les sous-systèmes disponibles sur le système.</span><span class="sxs-lookup"><span data-stu-id="2ae73-200">This cmdlet returns information about the subsystems that are available on the system.</span></span>
