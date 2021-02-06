---
description: Variables qui personnalisent le comportement de PowerShell.
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: d8eadf88d486de4758b56738089f27e8adc3bc91
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595899"
---
# <a name="about-preference-variables"></a><span data-ttu-id="e6601-103">À propos des variables de préférence</span><span class="sxs-lookup"><span data-stu-id="e6601-103">About Preference Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="e6601-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="e6601-104">Short description</span></span>

<span data-ttu-id="e6601-105">Variables qui personnalisent le comportement de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6601-105">Variables that customize the behavior of PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e6601-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="e6601-106">Long description</span></span>

<span data-ttu-id="e6601-107">PowerShell comprend un ensemble de variables qui vous permettent de personnaliser son comportement.</span><span class="sxs-lookup"><span data-stu-id="e6601-107">PowerShell includes a set of variables that enable you to customize its behavior.</span></span> <span data-ttu-id="e6601-108">Ces variables de préférence fonctionnent comme les options des systèmes basés sur l’interface graphique.</span><span class="sxs-lookup"><span data-stu-id="e6601-108">These preference variables work like the options in GUI-based systems.</span></span>

<span data-ttu-id="e6601-109">Les variables de préférence affectent l’environnement d’exploitation PowerShell et toutes les commandes exécutées dans l’environnement.</span><span class="sxs-lookup"><span data-stu-id="e6601-109">The preference variables affect the PowerShell operating environment and all commands run in the environment.</span></span> <span data-ttu-id="e6601-110">Dans de nombreux cas, les applets de commande ont des paramètres que vous pouvez utiliser pour remplacer le comportement de préférence pour une commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="e6601-110">In many cases, the cmdlets have parameters that you can use to override the preference behavior for a specific command.</span></span>

<span data-ttu-id="e6601-111">Le tableau suivant répertorie les variables de préférence et leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6601-111">The following table lists the preference variables and their default values.</span></span>

|             <span data-ttu-id="e6601-112">Variable</span><span class="sxs-lookup"><span data-stu-id="e6601-112">Variable</span></span>             |       <span data-ttu-id="e6601-113">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e6601-113">Default Value</span></span>       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | <span data-ttu-id="e6601-114">Importante</span><span class="sxs-lookup"><span data-stu-id="e6601-114">High</span></span>                      |
| `$DebugPreference`               | <span data-ttu-id="e6601-115">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="e6601-115">SilentlyContinue</span></span>          |
| `$ErrorActionPreference`         | <span data-ttu-id="e6601-116">Continue</span><span class="sxs-lookup"><span data-stu-id="e6601-116">Continue</span></span>                  |
| `$ErrorView`                     | <span data-ttu-id="e6601-117">ConciseView</span><span class="sxs-lookup"><span data-stu-id="e6601-117">ConciseView</span></span>               |
| `$FormatEnumerationLimit`        | <span data-ttu-id="e6601-118">4</span><span class="sxs-lookup"><span data-stu-id="e6601-118">4</span></span>                         |
| `$InformationPreference`         | <span data-ttu-id="e6601-119">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="e6601-119">SilentlyContinue</span></span>          |
| `$LogCommandHealthEvent`         | <span data-ttu-id="e6601-120">False (non enregistré)</span><span class="sxs-lookup"><span data-stu-id="e6601-120">False (not logged)</span></span>        |
| `$LogCommandLifecycleEvent`      | <span data-ttu-id="e6601-121">False (non enregistré)</span><span class="sxs-lookup"><span data-stu-id="e6601-121">False (not logged)</span></span>        |
| `$LogEngineHealthEvent`          | <span data-ttu-id="e6601-122">True (consigné)</span><span class="sxs-lookup"><span data-stu-id="e6601-122">True (logged)</span></span>             |
| `$LogEngineLifecycleEvent`       | <span data-ttu-id="e6601-123">True (consigné)</span><span class="sxs-lookup"><span data-stu-id="e6601-123">True (logged)</span></span>             |
| `$LogProviderLifecycleEvent`     | <span data-ttu-id="e6601-124">True (consigné)</span><span class="sxs-lookup"><span data-stu-id="e6601-124">True (logged)</span></span>             |
| `$LogProviderHealthEvent`        | <span data-ttu-id="e6601-125">True (consigné)</span><span class="sxs-lookup"><span data-stu-id="e6601-125">True (logged)</span></span>             |
| `$MaximumHistoryCount`           | <span data-ttu-id="e6601-126">4096</span><span class="sxs-lookup"><span data-stu-id="e6601-126">4096</span></span>                      |
| `$OFS`                           | <span data-ttu-id="e6601-127">(Espace ( `" "` ))</span><span class="sxs-lookup"><span data-stu-id="e6601-127">(Space character (`" "`))</span></span> |
| `$OutputEncoding`                | <span data-ttu-id="e6601-128">UTF8Encoding, objet</span><span class="sxs-lookup"><span data-stu-id="e6601-128">UTF8Encoding object</span></span>       |
| `$ProgressPreference`            | <span data-ttu-id="e6601-129">Continuer</span><span class="sxs-lookup"><span data-stu-id="e6601-129">Continue</span></span>                  |
| `$PSDefaultParameterValues`      | <span data-ttu-id="e6601-130">(Aucune-table de hachage vide)</span><span class="sxs-lookup"><span data-stu-id="e6601-130">(None - empty hash table)</span></span> |
| `$PSEmailServer`                 | <span data-ttu-id="e6601-131">(aucune)</span><span class="sxs-lookup"><span data-stu-id="e6601-131">(None)</span></span>                    |
| `$PSModuleAutoLoadingPreference` | <span data-ttu-id="e6601-132">Tous</span><span class="sxs-lookup"><span data-stu-id="e6601-132">All</span></span>                       |
| `$PSSessionApplicationName`      | <span data-ttu-id="e6601-133">wsman</span><span class="sxs-lookup"><span data-stu-id="e6601-133">wsman</span></span>                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | <span data-ttu-id="e6601-134">Voir [$PSSessionOption](#pssessionoption)</span><span class="sxs-lookup"><span data-stu-id="e6601-134">See [$PSSessionOption](#pssessionoption)</span></span> |
| `$Transcript`                    | <span data-ttu-id="e6601-135">(aucun)</span><span class="sxs-lookup"><span data-stu-id="e6601-135">(none)</span></span>                    |
| `$VerbosePreference`             | <span data-ttu-id="e6601-136">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="e6601-136">SilentlyContinue</span></span>          |
| `$WarningPreference`             | <span data-ttu-id="e6601-137">Continue</span><span class="sxs-lookup"><span data-stu-id="e6601-137">Continue</span></span>                  |
| `$WhatIfPreference`              | <span data-ttu-id="e6601-138">Faux</span><span class="sxs-lookup"><span data-stu-id="e6601-138">False</span></span>                     |

<span data-ttu-id="e6601-139">PowerShell comprend les variables d’environnement suivantes qui stockent les préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6601-139">PowerShell includes the following environment variables that store user preferences.</span></span> <span data-ttu-id="e6601-140">Pour plus d’informations sur ces variables d’environnement, consultez [about_Environment_Variables](about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-140">For more information about these environment variables, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> <span data-ttu-id="e6601-141">Les modifications apportées à la variable de préférence prennent effet uniquement dans les scripts et les fonctions si ces scripts ou fonctions sont définis dans la même portée que l’étendue dans laquelle la préférence a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="e6601-141">Changes to preference variable only take effect in scripts and functions if those scripts or functions are defined in the same scope as the scope in which preference was used.</span></span> <span data-ttu-id="e6601-142">Pour plus d’informations, consultez [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-142">For more information, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="working-with-preference-variables"></a><span data-ttu-id="e6601-143">Utilisation des variables de préférence</span><span class="sxs-lookup"><span data-stu-id="e6601-143">Working with preference variables</span></span>

<span data-ttu-id="e6601-144">Ce document décrit chacune des variables de préférence.</span><span class="sxs-lookup"><span data-stu-id="e6601-144">This document describes each of the preference variables.</span></span>

<span data-ttu-id="e6601-145">Pour afficher la valeur actuelle d’une variable de préférence spécifique, tapez le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-145">To display the current value of a specific preference variable, type the variable's name.</span></span> <span data-ttu-id="e6601-146">Par exemple, la commande suivante affiche la `$ConfirmPreference` valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-146">For example, the following command displays the `$ConfirmPreference` variable's value.</span></span>

```powershell
 $ConfirmPreference
```

```Output
High
```

<span data-ttu-id="e6601-147">Pour modifier la valeur d’une variable, utilisez une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="e6601-147">To change a variable's value, use an assignment statement.</span></span> <span data-ttu-id="e6601-148">Par exemple, l’instruction suivante modifie la `$ConfirmPreference` valeur du paramètre en **moyenne**.</span><span class="sxs-lookup"><span data-stu-id="e6601-148">For example, the following statement changes the `$ConfirmPreference` parameter's value to **Medium**.</span></span>

```powershell
$ConfirmPreference = "Medium"
```

<span data-ttu-id="e6601-149">Les valeurs que vous définissez sont spécifiques à la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="e6601-149">The values that you set are specific to the current PowerShell session.</span></span> <span data-ttu-id="e6601-150">Pour rendre les variables effectives dans toutes les sessions PowerShell, ajoutez-les à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6601-150">To make variables effective in all PowerShell sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="e6601-151">Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-151">For more information, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="working-remotely"></a><span data-ttu-id="e6601-152">Travailler à distance</span><span class="sxs-lookup"><span data-stu-id="e6601-152">Working remotely</span></span>

<span data-ttu-id="e6601-153">Lorsque vous exécutez des commandes sur un ordinateur distant, les commandes à distance sont soumises uniquement aux préférences définies dans le client PowerShell de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e6601-153">When you run commands on a remote computer, the remote commands are only subject to the preferences set in the remote computer's PowerShell client.</span></span> <span data-ttu-id="e6601-154">Par exemple, lorsque vous exécutez une commande distante, la valeur de la variable de l’ordinateur distant `$DebugPreference` détermine la manière dont PowerShell répond aux messages de débogage.</span><span class="sxs-lookup"><span data-stu-id="e6601-154">For example, when you run a remote command, the value of the remote computer's `$DebugPreference` variable determines how PowerShell responds to debugging messages.</span></span>

<span data-ttu-id="e6601-155">Pour plus d’informations sur les commandes distantes, consultez [about_Remote](about_Remote.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-155">For more information about remote commands, see [about_Remote](about_Remote.md).</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="e6601-156">\$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="e6601-156">\$ConfirmPreference</span></span>

<span data-ttu-id="e6601-157">Détermine si PowerShell vous invite automatiquement à confirmer l’exécution d’une applet de commande ou d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="e6601-157">Determines whether PowerShell automatically prompts you for confirmation before running a cmdlet or function.</span></span>

<span data-ttu-id="e6601-158">Les `$ConfirmPreference` valeurs valides de la variable sont **haute**, **moyenne** ou **faible**.</span><span class="sxs-lookup"><span data-stu-id="e6601-158">The `$ConfirmPreference` variable's valid values are **High**, **Medium**, or **Low**.</span></span> <span data-ttu-id="e6601-159">Les applets de commande et les fonctions se voient attribuer un risque de **haute**, **moyenne** ou **faible**.</span><span class="sxs-lookup"><span data-stu-id="e6601-159">Cmdlets and functions are assigned a risk of **High**, **Medium**, or **Low**.</span></span> <span data-ttu-id="e6601-160">Lorsque la valeur de la `$ConfirmPreference` variable est inférieure ou égale au risque affecté à une applet de commande ou à une fonction, PowerShell vous invite automatiquement à confirmer l’exécution de l’applet de commande ou de la fonction.</span><span class="sxs-lookup"><span data-stu-id="e6601-160">When the value of the `$ConfirmPreference` variable is less than or equal to the risk assigned to a cmdlet or function, PowerShell automatically prompts you for confirmation before running the cmdlet or function.</span></span>

<span data-ttu-id="e6601-161">Si la valeur de la `$ConfirmPreference` variable est **None**, PowerShell ne vous invite jamais automatiquement à exécuter une applet de commande ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="e6601-161">If the value of the `$ConfirmPreference` variable is **None**, PowerShell never automatically prompts you before running a cmdlet or function.</span></span>

<span data-ttu-id="e6601-162">Pour modifier le comportement de confirmation pour toutes les applets de commande et fonctions de la session, modifiez la `$ConfirmPreference` valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-162">To change the confirming behavior for all cmdlets and functions in the session, change `$ConfirmPreference` variable's value.</span></span>

<span data-ttu-id="e6601-163">Pour remplacer le `$ConfirmPreference` pour une seule commande, utilisez le paramètre **Confirm** d’une applet de commande ou d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="e6601-163">To override the `$ConfirmPreference` for a single command, use a cmdlet's or function's **Confirm** parameter.</span></span> <span data-ttu-id="e6601-164">Pour demander une confirmation, utilisez `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="e6601-164">To request confirmation, use `-Confirm`.</span></span> <span data-ttu-id="e6601-165">Pour supprimer la confirmation, utilisez `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="e6601-165">To suppress confirmation, use `-Confirm:$false`.</span></span>

<span data-ttu-id="e6601-166">Valeurs valides `$ConfirmPreference` :</span><span class="sxs-lookup"><span data-stu-id="e6601-166">Valid values of `$ConfirmPreference`:</span></span>

- <span data-ttu-id="e6601-167">**None**: PowerShell n’affiche pas d’invite automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e6601-167">**None**: PowerShell doesn't prompt automatically.</span></span> <span data-ttu-id="e6601-168">Pour demander la confirmation d’une commande particulière, utilisez le paramètre **Confirm** de l’applet de commande ou de la fonction.</span><span class="sxs-lookup"><span data-stu-id="e6601-168">To request confirmation of a particular command, use the **Confirm** parameter of the cmdlet or function.</span></span>
- <span data-ttu-id="e6601-169">**Faible**: PowerShell vous invite à confirmer l’exécution des applets de commande ou des fonctions avec un risque faible, moyen ou élevé.</span><span class="sxs-lookup"><span data-stu-id="e6601-169">**Low**: PowerShell prompts for confirmation before running cmdlets or functions with a low, medium, or high risk.</span></span>
- <span data-ttu-id="e6601-170">**Moyenne**: PowerShell vous invite à confirmer l’exécution des applets de commande ou des fonctions avec un risque moyen ou élevé.</span><span class="sxs-lookup"><span data-stu-id="e6601-170">**Medium**: PowerShell prompts for confirmation before running cmdlets or functions with a medium, or high risk.</span></span>
- <span data-ttu-id="e6601-171">**Élevé**: PowerShell vous invite à confirmer l’exécution des applets de commande ou des fonctions présentant un risque élevé.</span><span class="sxs-lookup"><span data-stu-id="e6601-171">**High**: PowerShell prompts for confirmation before running cmdlets or functions with a high risk.</span></span>

#### <a name="detailed-explanation"></a><span data-ttu-id="e6601-172">Explication détaillée</span><span class="sxs-lookup"><span data-stu-id="e6601-172">Detailed explanation</span></span>

<span data-ttu-id="e6601-173">PowerShell peut vous inviter automatiquement à confirmer l’opération avant d’exécuter une action.</span><span class="sxs-lookup"><span data-stu-id="e6601-173">PowerShell can automatically prompt you for confirmation before doing an action.</span></span> <span data-ttu-id="e6601-174">Par exemple, quand une applet de commande ou une fonction affecte de manière significative le système pour supprimer des données ou utiliser une quantité importante de ressources système.</span><span class="sxs-lookup"><span data-stu-id="e6601-174">For example, when cmdlet or function significantly affects the system to delete data or use a significant amount of system resources.</span></span>

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

<span data-ttu-id="e6601-175">L’estimation du risque est un attribut de l’applet de commande ou de la fonction appelée **ConfirmImpact**.</span><span class="sxs-lookup"><span data-stu-id="e6601-175">The estimate of the risk is an attribute of the cmdlet or function known as its **ConfirmImpact**.</span></span> <span data-ttu-id="e6601-176">Les utilisateurs ne peuvent pas le changer.</span><span class="sxs-lookup"><span data-stu-id="e6601-176">Users can't change it.</span></span>

<span data-ttu-id="e6601-177">Les applets de commande et les fonctions qui peuvent présenter un risque pour le système disposent d’un paramètre **Confirm** que vous pouvez utiliser pour demander ou supprimer la confirmation pour une seule commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-177">Cmdlets and functions that might pose a risk to the system have a **Confirm** parameter that you can use to request or suppress confirmation for a single command.</span></span>

<span data-ttu-id="e6601-178">Étant donné que la plupart des applets de commande et des fonctions utilisent la valeur de risque par défaut, **ConfirmImpact**, de **Medium** et que la valeur par défaut de `$ConfirmPreference` est **High**, la confirmation automatique se produit rarement.</span><span class="sxs-lookup"><span data-stu-id="e6601-178">Because most cmdlets and functions use the default risk value, **ConfirmImpact**, of **Medium**, and the default value of `$ConfirmPreference` is **High**, automatic confirmation rarely occurs.</span></span> <span data-ttu-id="e6601-179">Toutefois, vous pouvez activer la confirmation automatique en remplaçant la valeur de par `$ConfirmPreference` **moyenne** ou **faible**.</span><span class="sxs-lookup"><span data-stu-id="e6601-179">However, you can activate automatic confirmation by changing the value of `$ConfirmPreference` to **Medium** or **Low**.</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-180">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-180">Examples</span></span>

<span data-ttu-id="e6601-181">Cet exemple montre l’effet de la `$ConfirmPreference` valeur par défaut de la variable **High**.</span><span class="sxs-lookup"><span data-stu-id="e6601-181">This example shows the effect of the `$ConfirmPreference` variable's default value, **High**.</span></span> <span data-ttu-id="e6601-182">La valeur **élevée** confirme uniquement les applets de commande et les fonctions à haut risque.</span><span class="sxs-lookup"><span data-stu-id="e6601-182">The **High** value only confirms high-risk cmdlets and functions.</span></span> <span data-ttu-id="e6601-183">Étant donné que la plupart des applets de commande et des fonctions sont à risque moyen, elles ne sont pas confirmées automatiquement et `Remove-Item` suppriment le fichier.</span><span class="sxs-lookup"><span data-stu-id="e6601-183">Since most cmdlets and functions are medium risk, they aren't automatically confirmed and `Remove-Item` deletes the file.</span></span> <span data-ttu-id="e6601-184">`-Confirm`L’ajout de à la commande invite l’utilisateur à confirmer.</span><span class="sxs-lookup"><span data-stu-id="e6601-184">Adding `-Confirm` to the command prompts the user for confirmation.</span></span>

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

<span data-ttu-id="e6601-185">Utilisez `-Confirm` pour demander une confirmation.</span><span class="sxs-lookup"><span data-stu-id="e6601-185">Use `-Confirm` to request confirmation.</span></span>

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

<span data-ttu-id="e6601-186">L’exemple suivant montre l’effet de la modification de la valeur de `$ConfirmPreference` en **moyenne**.</span><span class="sxs-lookup"><span data-stu-id="e6601-186">The following example shows the effect of changing the value of `$ConfirmPreference` to **Medium**.</span></span> <span data-ttu-id="e6601-187">Étant donné que la plupart des applets de commande et des fonctions sont à risque moyen, elles sont confirmées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e6601-187">Because most cmdlets and function are medium risk, they're automatically confirmed.</span></span> <span data-ttu-id="e6601-188">Pour supprimer l’invite de confirmation pour une seule commande, utilisez le paramètre **Confirm** avec la valeur `$false` .</span><span class="sxs-lookup"><span data-stu-id="e6601-188">To suppress the confirmation prompt for a single command, use the **Confirm** parameter with a value of `$false`.</span></span>

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a><span data-ttu-id="e6601-189">\$Variable DebugPreference</span><span class="sxs-lookup"><span data-stu-id="e6601-189">\$DebugPreference</span></span>

<span data-ttu-id="e6601-190">Détermine la manière dont PowerShell répond aux messages de débogage générés par un script, une applet de commande ou un fournisseur, ou par une `Write-Debug` commande sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-190">Determines how PowerShell responds to debugging messages generated by a script, cmdlet or provider, or by a `Write-Debug` command at the command line.</span></span>

<span data-ttu-id="e6601-191">Certaines applets de commande affichent des messages de débogage, qui sont généralement des messages techniques destinés aux programmeurs et aux professionnels du support technique.</span><span class="sxs-lookup"><span data-stu-id="e6601-191">Some cmdlets display debugging messages, which are typically technical messages designed for programmers and technical support professionals.</span></span> <span data-ttu-id="e6601-192">Par défaut, les messages de débogage ne sont pas affichés, mais vous pouvez afficher les messages de débogage en modifiant la valeur de `$DebugPreference` .</span><span class="sxs-lookup"><span data-stu-id="e6601-192">By default, debugging messages aren't displayed, but you can display debugging messages by changing the value of `$DebugPreference`.</span></span>

<span data-ttu-id="e6601-193">Vous pouvez utiliser le paramètre Common de **débogage** d’une applet de commande pour afficher ou masquer les messages de débogage d’une commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="e6601-193">You can use the **Debug** common parameter of a cmdlet to display or hide the debugging messages for a specific command.</span></span> <span data-ttu-id="e6601-194">Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-194">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="e6601-195">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-195">The valid values are as follows:</span></span>

- <span data-ttu-id="e6601-196">**Arrêter**: affiche le message de débogage et arrête l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-196">**Stop**: Displays the debug message and stops executing.</span></span> <span data-ttu-id="e6601-197">Écrit une erreur dans la console.</span><span class="sxs-lookup"><span data-stu-id="e6601-197">Writes an error to the console.</span></span>
- <span data-ttu-id="e6601-198">**Rechercher**: affiche le message de débogage et vous demande si vous souhaitez continuer.</span><span class="sxs-lookup"><span data-stu-id="e6601-198">**Inquire**: Displays the debug message and asks you whether you want to continue.</span></span> <span data-ttu-id="e6601-199">L’ajout du paramètre common **Debug** à une commande, lorsque la commande est configurée pour générer un message de débogage, remplace la valeur de la `$DebugPreference` variable par **inquire**.</span><span class="sxs-lookup"><span data-stu-id="e6601-199">Adding the **Debug** common parameter to a command, when the command is configured to generate a debugging message, changes the value of the `$DebugPreference` variable to **Inquire**.</span></span>
- <span data-ttu-id="e6601-200">**Continuer**: affiche le message de débogage et poursuit l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-200">**Continue**: Displays the debug message and continues with execution.</span></span>
- <span data-ttu-id="e6601-201">**SilentlyContinue**: (valeur par défaut) aucun effet.</span><span class="sxs-lookup"><span data-stu-id="e6601-201">**SilentlyContinue**: (Default) No effect.</span></span> <span data-ttu-id="e6601-202">Le message de débogage n’est pas affiché et l’exécution se poursuit sans interruption.</span><span class="sxs-lookup"><span data-stu-id="e6601-202">The debug message isn't displayed and execution continues without interruption.</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-203">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-203">Examples</span></span>

<span data-ttu-id="e6601-204">Les exemples suivants illustrent l’effet de la modification des valeurs de `$DebugPreference` lorsqu’une `Write-Debug` commande est entrée sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-204">The following examples show the effect of changing the values of `$DebugPreference` when a `Write-Debug` command is entered at the command line.</span></span>
<span data-ttu-id="e6601-205">La modification affecte tous les messages de débogage, y compris les messages générés par les applets de commande et les scripts.</span><span class="sxs-lookup"><span data-stu-id="e6601-205">The change affects all debugging messages, including messages generated by cmdlets and scripts.</span></span> <span data-ttu-id="e6601-206">Les exemples montrent le paramètre de **débogage** , qui affiche ou masque les messages de débogage associés à une commande unique.</span><span class="sxs-lookup"><span data-stu-id="e6601-206">The examples show the **Debug** parameter, which displays or hides the debugging messages related to a single command.</span></span>

<span data-ttu-id="e6601-207">Cet exemple montre l’effet de la `$DebugPreference` valeur par défaut de la variable, **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="e6601-207">This example shows the effect of the `$DebugPreference` variable's default value, **SilentlyContinue**.</span></span> <span data-ttu-id="e6601-208">Par défaut, le `Write-Debug` message de débogage de l’applet de commande n’est pas affiché et le traitement continue.</span><span class="sxs-lookup"><span data-stu-id="e6601-208">By default, the `Write-Debug` cmdlet's debug message isn't displayed and processing continues.</span></span> <span data-ttu-id="e6601-209">Lorsque le paramètre de **débogage** est utilisé, il se substitue à la préférence pour une seule commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-209">When the **Debug** parameter is used, it overrides the preference for a single command.</span></span> <span data-ttu-id="e6601-210">Le message de débogage s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e6601-210">The debug message is displayed.</span></span>

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="e6601-211">Cet exemple montre l’effet de `$DebugPreference` avec la valeur **continue** .</span><span class="sxs-lookup"><span data-stu-id="e6601-211">This example shows the effect of `$DebugPreference` with the **Continue** value.</span></span> <span data-ttu-id="e6601-212">Le message de débogage s’affiche et la commande continue à traiter.</span><span class="sxs-lookup"><span data-stu-id="e6601-212">The debug message is displayed and the command continues to process.</span></span>

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="e6601-213">Cet exemple utilise le paramètre **Debug** avec la valeur `$false` pour supprimer le message d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-213">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="e6601-214">Le message de débogage n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="e6601-214">The debug message isn't displayed.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="e6601-215">Cet exemple montre l’effet de la `$DebugPreference` définition de la valeur d' **arrêt** .</span><span class="sxs-lookup"><span data-stu-id="e6601-215">This example shows the effect of `$DebugPreference` being set to the **Stop** value.</span></span> <span data-ttu-id="e6601-216">Le message de débogage s’affiche et la commande est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="e6601-216">The debug message is displayed and the command is stopped.</span></span>

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

<span data-ttu-id="e6601-217">Cet exemple utilise le paramètre **Debug** avec la valeur `$false` pour supprimer le message d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-217">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="e6601-218">Le message de débogage n’est pas affiché et le traitement n’est pas arrêté.</span><span class="sxs-lookup"><span data-stu-id="e6601-218">The debug message isn't displayed and processing isn't stopped.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="e6601-219">Cet exemple montre l’effet de la `$DebugPreference` définition de la valeur de **recherche** .</span><span class="sxs-lookup"><span data-stu-id="e6601-219">This example shows the effect of `$DebugPreference` being set to the **Inquire** value.</span></span> <span data-ttu-id="e6601-220">Le message de débogage s’affiche et l’utilisateur est invité à confirmer l’intervention.</span><span class="sxs-lookup"><span data-stu-id="e6601-220">The debug message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="e6601-221">Cet exemple utilise le paramètre **Debug** avec la valeur `$false` pour supprimer le message d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-221">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="e6601-222">Le message de débogage n’est pas affiché et le traitement continue.</span><span class="sxs-lookup"><span data-stu-id="e6601-222">The debug message isn't displayed and processing continues.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a><span data-ttu-id="e6601-223">\$ErrorActionPreference</span><span class="sxs-lookup"><span data-stu-id="e6601-223">\$ErrorActionPreference</span></span>

<span data-ttu-id="e6601-224">Détermine la manière dont PowerShell répond à une erreur sans fin d’exécution, une erreur qui n’arrête pas le traitement de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-224">Determines how PowerShell responds to a non-terminating error, an error that doesn't stop the cmdlet processing.</span></span> <span data-ttu-id="e6601-225">Par exemple, sur la ligne de commande ou dans un script, une applet de commande ou un fournisseur, comme les erreurs générées par l’applet de commande `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="e6601-225">For example, at the command line or in a script, cmdlet, or provider, such as the errors generated by the `Write-Error` cmdlet.</span></span>

<span data-ttu-id="e6601-226">Vous pouvez utiliser le paramètre commun **ErrorAction** d’une applet de commande pour remplacer la préférence pour une commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="e6601-226">You can use a cmdlet's **ErrorAction** common parameter to override the preference for a specific command.</span></span>

<span data-ttu-id="e6601-227">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-227">The valid values are as follows:</span></span>

- <span data-ttu-id="e6601-228">**Arrêter** : entrez le débogueur lorsqu’une erreur se produit ou lorsqu’une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="e6601-228">**Break** - Enter the debugger when an error occurs or when an exception is raised.</span></span>
- <span data-ttu-id="e6601-229">**Continuer**: (valeur par défaut) affiche le message d’erreur et poursuit l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-229">**Continue**: (Default) Displays the error message and continues executing.</span></span>
- <span data-ttu-id="e6601-230">**Ignorer**: supprime le message d’erreur et poursuit l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-230">**Ignore**: Suppresses the error message and continues to execute the command.</span></span> <span data-ttu-id="e6601-231">La valeur **Ignorer** est destinée à une utilisation par commande, et non à une utilisation en tant que préférence enregistrée.</span><span class="sxs-lookup"><span data-stu-id="e6601-231">The **Ignore** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="e6601-232">L’option **ignore** n’est pas une valeur valide pour la `$ErrorActionPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-232">**Ignore** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>
- <span data-ttu-id="e6601-233">**Rechercher**: affiche le message d’erreur et vous demande si vous souhaitez continuer.</span><span class="sxs-lookup"><span data-stu-id="e6601-233">**Inquire**: Displays the error message and asks you whether you want to continue.</span></span>
- <span data-ttu-id="e6601-234">**SilentlyContinue**: aucun effet.</span><span class="sxs-lookup"><span data-stu-id="e6601-234">**SilentlyContinue**: No effect.</span></span> <span data-ttu-id="e6601-235">Le message d’erreur ne s’affiche pas et l’exécution se poursuit sans interruption.</span><span class="sxs-lookup"><span data-stu-id="e6601-235">The error message isn't displayed and execution continues without interruption.</span></span>
- <span data-ttu-id="e6601-236">**Arrêter**: affiche le message d’erreur et arrête l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-236">**Stop**: Displays the error message and stops executing.</span></span> <span data-ttu-id="e6601-237">En plus de l’erreur générée, la valeur d' **arrêt** génère un objet ActionPreferenceStopException dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="e6601-237">In addition to the error generated, the **Stop** value generates an ActionPreferenceStopException object to the error stream.</span></span>
  <span data-ttu-id="e6601-238">flux</span><span class="sxs-lookup"><span data-stu-id="e6601-238">stream</span></span>
- <span data-ttu-id="e6601-239">**Suspend**: suspend automatiquement une tâche de workflow pour permettre une investigation plus poussée.</span><span class="sxs-lookup"><span data-stu-id="e6601-239">**Suspend**: Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="e6601-240">Après l’examen, le flux de travail peut être repris.</span><span class="sxs-lookup"><span data-stu-id="e6601-240">After investigation, the workflow can be resumed.</span></span> <span data-ttu-id="e6601-241">La valeur de **suspension** est destinée à une utilisation par commande, et non à une utilisation en tant que préférence enregistrée.</span><span class="sxs-lookup"><span data-stu-id="e6601-241">The **Suspend** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="e6601-242">**Suspend** n’est pas une valeur valide pour la `$ErrorActionPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-242">**Suspend** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="e6601-243">`$ErrorActionPreference` et le paramètre **ErrorAction** n’affectent pas la manière dont PowerShell répond aux erreurs de fin qui arrêtent le traitement des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-243">`$ErrorActionPreference` and the **ErrorAction** parameter don't affect how PowerShell responds to terminating errors that stop cmdlet processing.</span></span> <span data-ttu-id="e6601-244">Pour plus d’informations sur le paramètre commun **ErrorAction** , consultez [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-244">For more information about the **ErrorAction** common parameter, see [about_CommonParameters](about_CommonParameters.md).</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-245">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-245">Examples</span></span>

<span data-ttu-id="e6601-246">Ces exemples illustrent l’effet des différentes valeurs de la `$ErrorActionPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-246">These examples show the effect of the different values of the `$ErrorActionPreference` variable.</span></span> <span data-ttu-id="e6601-247">Le paramètre **ErrorAction** est utilisé pour remplacer la `$ErrorActionPreference` valeur.</span><span class="sxs-lookup"><span data-stu-id="e6601-247">The **ErrorAction** parameter is used to override the `$ErrorActionPreference` value.</span></span>

<span data-ttu-id="e6601-248">Cet exemple montre la `$ErrorActionPreference` valeur par défaut, **continue**.</span><span class="sxs-lookup"><span data-stu-id="e6601-248">This example shows the `$ErrorActionPreference` default value, **Continue**.</span></span> <span data-ttu-id="e6601-249">Une erreur sans fin d’achèvement est générée.</span><span class="sxs-lookup"><span data-stu-id="e6601-249">A non-terminating error is generated.</span></span> <span data-ttu-id="e6601-250">Le message s’affiche et le traitement continue.</span><span class="sxs-lookup"><span data-stu-id="e6601-250">The message is displayed and processing continues.</span></span>

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error: Test Error
Hello World
```

<span data-ttu-id="e6601-251">Cet exemple montre la `$ErrorActionPreference` valeur par défaut, **inquire**.</span><span class="sxs-lookup"><span data-stu-id="e6601-251">This example shows the `$ErrorActionPreference` default value, **Inquire**.</span></span> <span data-ttu-id="e6601-252">Une erreur est générée et une invite d’action s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e6601-252">An error is generated and a prompt for action is shown.</span></span>

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="e6601-253">Cet exemple montre l' `$ErrorActionPreference` ensemble de **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="e6601-253">This example shows the `$ErrorActionPreference` set to **SilentlyContinue**.</span></span>
<span data-ttu-id="e6601-254">Le message d’erreur est supprimé.</span><span class="sxs-lookup"><span data-stu-id="e6601-254">The error message is suppressed.</span></span>

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

<span data-ttu-id="e6601-255">Cet exemple montre le `$ErrorActionPreference` jeu à **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="e6601-255">This example shows the `$ErrorActionPreference` set to **Stop**.</span></span> <span data-ttu-id="e6601-256">Il montre également l’objet supplémentaire généré pour la `$Error` variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-256">It also shows the extra object generated to the `$Error` variable.</span></span>

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error: Test Error

ErrorRecord                 : Test Error
WasThrownFromThrowStatement : False
TargetSite                  : System.Collections.ObjectModel.Collection`1[System.Management.Automation.PSObject]
                              Invoke(System.Collections.IEnumerable)
StackTrace                  :    at System.Management.Automation.Runspaces.PipelineBase.Invoke(IEnumerable input)
                                 at Microsoft.PowerShell.Executor.ExecuteCommandHelper(Pipeline tempPipeline,
                              Exception& exceptionThrown, ExecutionOptions options)
Message                     : The running command stopped because the preference variable "ErrorActionPreference" or
                              common parameter is set to Stop: Test Error
Data                        : {System.Management.Automation.Interpreter.InterpretedFrameInfo}
InnerException              :
HelpLink                    :
Source                      : System.Management.Automation
HResult                     : -2146233087

Write-Error: Test Error
```

### <a name="errorview"></a><span data-ttu-id="e6601-257">\$ErrorView</span><span class="sxs-lookup"><span data-stu-id="e6601-257">\$ErrorView</span></span>

<span data-ttu-id="e6601-258">Détermine le format d’affichage des messages d’erreur dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6601-258">Determines the display format of error messages in PowerShell.</span></span>

<span data-ttu-id="e6601-259">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-259">The valid values are as follows:</span></span>

- <span data-ttu-id="e6601-260">**ConciseView**: (par défaut) fournit un message d’erreur concis et une vue refactorle pour les générateurs de modules avancés.</span><span class="sxs-lookup"><span data-stu-id="e6601-260">**ConciseView**: (Default) Provides a concise error message and a refactored view for advanced module builders.</span></span> <span data-ttu-id="e6601-261">Si l’erreur provient de la ligne de commande, il s’agit d’un message d’erreur de ligne unique.</span><span class="sxs-lookup"><span data-stu-id="e6601-261">If the error is from command line it's a single line error message.</span></span> <span data-ttu-id="e6601-262">Dans le cas contraire, vous recevez un message d’erreur multiligne contenant l’erreur et un pointeur vers l’erreur indiquant où elle se produit sur cette ligne.</span><span class="sxs-lookup"><span data-stu-id="e6601-262">Otherwise, you receive a multiline error message that contains the error and a pointer to the error showing where it occurs in that line.</span></span> <span data-ttu-id="e6601-263">Si le terminal prend en charge le terminal virtuel, les codes de couleur ANSI sont utilisés pour fournir un accent sur les couleurs.</span><span class="sxs-lookup"><span data-stu-id="e6601-263">If the terminal supports Virtual Terminal, then ANSI color codes are used to provide color accent.</span></span> <span data-ttu-id="e6601-264">La couleur d’accentuation peut être modifiée à `$Host.PrivateData.ErrorAccentColor` .</span><span class="sxs-lookup"><span data-stu-id="e6601-264">The Accent color can be changed at `$Host.PrivateData.ErrorAccentColor`.</span></span> <span data-ttu-id="e6601-265">Utilisez `Get-Error` l’applet de commande pour obtenir une vue détaillée détaillée de l’erreur complète, y compris les exceptions internes.</span><span class="sxs-lookup"><span data-stu-id="e6601-265">Use `Get-Error` cmdlet for a comprehensive detailed view of the fully qualified error, including inner exceptions.</span></span>

  <span data-ttu-id="e6601-266">**ConciseView** a été ajouté dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="e6601-266">**ConciseView** was added in PowerShell 7.</span></span>

- <span data-ttu-id="e6601-267">**NormalView**: vue détaillée conçue pour la plupart des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e6601-267">**NormalView**: A detailed view designed for most users.</span></span> <span data-ttu-id="e6601-268">Se compose d’une description de l’erreur et du nom de l’objet impliqué dans l’erreur.</span><span class="sxs-lookup"><span data-stu-id="e6601-268">Consists of a description of the error and the name of the object involved in the error.</span></span>

- <span data-ttu-id="e6601-269">**CategoryView**: vue succincte structurée conçue pour les environnements de production.</span><span class="sxs-lookup"><span data-stu-id="e6601-269">**CategoryView**: A succinct, structured view designed for production environments.</span></span> <span data-ttu-id="e6601-270">au format suivant :</span><span class="sxs-lookup"><span data-stu-id="e6601-270">The format is as follows:</span></span>

  <span data-ttu-id="e6601-271">{Category} : ({NomCible} : {TargetType}) : [{Activity}], {Reason}</span><span class="sxs-lookup"><span data-stu-id="e6601-271">{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}</span></span>

<span data-ttu-id="e6601-272">Pour plus d’informations sur les champs dans **CategoryView**, consultez classe [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) .</span><span class="sxs-lookup"><span data-stu-id="e6601-272">For more information about the fields in **CategoryView**, see [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) class.</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-273">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-273">Examples</span></span>

<span data-ttu-id="e6601-274">Cet exemple montre comment une erreur s’affiche lorsque la valeur de `$ErrorView` est la valeur par défaut, **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="e6601-274">This example shows how an error appears when the value of `$ErrorView` is the default, **ConciseView**.</span></span> <span data-ttu-id="e6601-275">`Get-ChildItem` est utilisé pour rechercher un répertoire inexistant.</span><span class="sxs-lookup"><span data-stu-id="e6601-275">`Get-ChildItem` is used to find a non-existent directory.</span></span>

```powershell
Get-ChildItem -path 'C:\NoRealDirectory'
```

```Output
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.
```

<span data-ttu-id="e6601-276">Cet exemple montre comment une erreur s’affiche lorsque la valeur de `$ErrorView` est la valeur par défaut, **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="e6601-276">This example shows how an error appears when the value of `$ErrorView` is the default, **ConciseView**.</span></span> <span data-ttu-id="e6601-277">`Script.ps1` est exécutée et génère une erreur à partir de l' `Get-Item` instruction.</span><span class="sxs-lookup"><span data-stu-id="e6601-277">`Script.ps1` is run and throws an error from `Get-Item` statement.</span></span>

```powershell
./Script.ps1
```

```Output
Get-Item: C:\Script.ps1
Line |
  11 | Get-Item -Path .\stuff
     | ^ Cannot find path 'C:\demo\stuff' because it does not exist.
```

<span data-ttu-id="e6601-278">Cet exemple montre comment une erreur s’affiche lorsque la valeur de `$ErrorView` est remplacée par **NormalView**.</span><span class="sxs-lookup"><span data-stu-id="e6601-278">This example shows how an error appears when the value of `$ErrorView` is changed to **NormalView**.</span></span> <span data-ttu-id="e6601-279">`Get-ChildItem` est utilisé pour rechercher un fichier inexistant.</span><span class="sxs-lookup"><span data-stu-id="e6601-279">`Get-ChildItem` is used to find a non-existent file.</span></span>

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

<span data-ttu-id="e6601-280">Cet exemple montre comment la même erreur s’affiche lorsque la valeur de `$ErrorView` est remplacée par **CategoryView**.</span><span class="sxs-lookup"><span data-stu-id="e6601-280">This example shows how the same error appears when the value of `$ErrorView` is changed to **CategoryView**.</span></span>

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

<span data-ttu-id="e6601-281">Cet exemple montre que la valeur de `$ErrorView` affecte uniquement l’affichage des erreurs.</span><span class="sxs-lookup"><span data-stu-id="e6601-281">This example demonstrates that the value of `$ErrorView` only affects the error display.</span></span> <span data-ttu-id="e6601-282">Elle ne modifie pas la structure de l’objet d’erreur stocké dans la `$Error` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="e6601-282">It doesn't change the structure of the error object that is stored in the `$Error` automatic variable.</span></span> <span data-ttu-id="e6601-283">Pour plus d’informations sur la `$Error` variable automatique, consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-283">For information about the `$Error` automatic variable, see [about_automatic_variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="e6601-284">La commande suivante prend l’objet **ErrorRecord** associé à l’erreur la plus récente dans le tableau d’erreurs, **élément 0**, et met en forme toutes les propriétés de l’objet d’erreur dans une liste.</span><span class="sxs-lookup"><span data-stu-id="e6601-284">The following command takes the **ErrorRecord** object associated with the most recent error in the error array, **element 0**, and formats all the error object's properties in a list.</span></span>

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a><span data-ttu-id="e6601-285">\$FormatEnumerationLimit</span><span class="sxs-lookup"><span data-stu-id="e6601-285">\$FormatEnumerationLimit</span></span>

<span data-ttu-id="e6601-286">Détermine le nombre d’éléments énumérés inclus dans un affichage.</span><span class="sxs-lookup"><span data-stu-id="e6601-286">Determines how many enumerated items are included in a display.</span></span> <span data-ttu-id="e6601-287">Cette variable n’affecte pas les objets sous-jacents, mais uniquement l’affichage.</span><span class="sxs-lookup"><span data-stu-id="e6601-287">This variable doesn't affect the underlying objects, only the display.</span></span> <span data-ttu-id="e6601-288">Lorsque la valeur de `$FormatEnumerationLimit` est inférieure au nombre d’éléments énumérés, PowerShell ajoute des points de suspension ( `...` ) pour indiquer les éléments qui ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="e6601-288">When the value of `$FormatEnumerationLimit` is fewer than the number of enumerated items, PowerShell adds an ellipsis (`...`) to indicate items not shown.</span></span>

<span data-ttu-id="e6601-289">**Valeurs valides**: entiers ( `Int32` )</span><span class="sxs-lookup"><span data-stu-id="e6601-289">**Valid values**: Integers (`Int32`)</span></span>

<span data-ttu-id="e6601-290">**Valeur par défaut**: 4</span><span class="sxs-lookup"><span data-stu-id="e6601-290">**Default value**: 4</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-291">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-291">Examples</span></span>

<span data-ttu-id="e6601-292">Cet exemple montre comment utiliser la `$FormatEnumerationLimit` variable pour améliorer l’affichage des éléments énumérés.</span><span class="sxs-lookup"><span data-stu-id="e6601-292">This example shows how to use the `$FormatEnumerationLimit` variable to improve the display of enumerated items.</span></span>

<span data-ttu-id="e6601-293">Dans cet exemple, la commande génère une table qui répertorie tous les services en cours d’exécution sur l’ordinateur en deux groupes : un pour les services **en cours d’exécution** et un pour les services **arrêtés** .</span><span class="sxs-lookup"><span data-stu-id="e6601-293">The command in this example generates a table that lists all the services running on the computer in two groups: one for **running** services and one for **stopped** services.</span></span> <span data-ttu-id="e6601-294">Elle utilise une `Get-Service` commande pour obtenir tous les services, puis envoie les résultats via le pipeline à l' `Group-Object` applet de commande, qui regroupe les résultats selon l’état du service.</span><span class="sxs-lookup"><span data-stu-id="e6601-294">It uses a `Get-Service` command to get all the services, and then sends the results through the pipeline to the `Group-Object` cmdlet, which groups the results by the service status.</span></span>

<span data-ttu-id="e6601-295">Le résultat est une table qui répertorie l’État dans la colonne **nom** et les processus dans la colonne **groupe** .</span><span class="sxs-lookup"><span data-stu-id="e6601-295">The result is a table that lists the status in the **Name** column, and the processes in the **Group** column.</span></span> <span data-ttu-id="e6601-296">Pour modifier les étiquettes de colonne, utilisez une table de hachage, consultez [about_Hash_Tables](about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-296">To change the column labels, use a hash table, see [about_Hash_Tables](about_Hash_Tables.md).</span></span> <span data-ttu-id="e6601-297">Pour plus d’informations, consultez les exemples dans [format-table](xref:Microsoft.PowerShell.Utility.Format-Table).</span><span class="sxs-lookup"><span data-stu-id="e6601-297">For more information, see the examples in [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

<span data-ttu-id="e6601-298">Recherchez la valeur actuelle de `$FormatEnumerationLimit` .</span><span class="sxs-lookup"><span data-stu-id="e6601-298">Find the current value of `$FormatEnumerationLimit`.</span></span>

```powershell
$FormatEnumerationLimit
```

```Output
4
```

<span data-ttu-id="e6601-299">Répertorie tous les services regroupés par **État**.</span><span class="sxs-lookup"><span data-stu-id="e6601-299">List all services grouped by **Status**.</span></span> <span data-ttu-id="e6601-300">Il existe un maximum de quatre services répertoriés dans la colonne **groupe** pour chaque État, car `$FormatEnumerationLimit` a la valeur **4**.</span><span class="sxs-lookup"><span data-stu-id="e6601-300">There are a maximum of four services listed in the **Group** column for each status because `$FormatEnumerationLimit` has a value of **4**.</span></span>

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

<span data-ttu-id="e6601-301">Pour augmenter le nombre d’éléments figurant dans la liste, augmentez la valeur de `$FormatEnumerationLimit` à **1000**.</span><span class="sxs-lookup"><span data-stu-id="e6601-301">To increase the number of items listed, increase the value of `$FormatEnumerationLimit` to **1000**.</span></span> <span data-ttu-id="e6601-302">Utilisez `Get-Service` et `Group-Object` pour afficher les services.</span><span class="sxs-lookup"><span data-stu-id="e6601-302">Use `Get-Service` and `Group-Object` to display the services.</span></span>

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

<span data-ttu-id="e6601-303">Utilisez `Format-Table` avec le paramètre **Wrap** pour afficher la liste des services.</span><span class="sxs-lookup"><span data-stu-id="e6601-303">Use `Format-Table` with the **Wrap** parameter to display the list of services.</span></span>

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a><span data-ttu-id="e6601-304">\$InformationPreference</span><span class="sxs-lookup"><span data-stu-id="e6601-304">\$InformationPreference</span></span>

<span data-ttu-id="e6601-305">La `$InformationPreference` variable vous permet de définir les préférences de flux d’informations que vous souhaitez afficher aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e6601-305">The `$InformationPreference` variable lets you set information stream preferences that you want displayed to users.</span></span> <span data-ttu-id="e6601-306">Plus précisément, les messages d’information que vous avez ajoutés aux commandes ou aux scripts en ajoutant l’applet de commande [Write-information](xref:Microsoft.PowerShell.Utility.Write-Information) .</span><span class="sxs-lookup"><span data-stu-id="e6601-306">Specifically, informational messages that you added to commands or scripts by adding the [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) cmdlet.</span></span> <span data-ttu-id="e6601-307">Si le paramètre **InformationAction** est utilisé, sa valeur remplace la valeur de la `$InformationPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-307">If the **InformationAction** parameter is used, its value overrides the value of the `$InformationPreference` variable.</span></span> <span data-ttu-id="e6601-308">`Write-Information` a été introduit dans PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="e6601-308">`Write-Information` was introduced in PowerShell 5.0.</span></span>

<span data-ttu-id="e6601-309">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-309">The valid values are as follows:</span></span>

- <span data-ttu-id="e6601-310">**Arrêter**: arrête une commande ou un script à une occurrence de la `Write-Information` commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-310">**Stop**: Stops a command or script at an occurrence of the `Write-Information` command.</span></span>
- <span data-ttu-id="e6601-311">**Rechercher**: affiche le message d’information que vous spécifiez dans une `Write-Information` commande, puis vous demande si vous souhaitez continuer.</span><span class="sxs-lookup"><span data-stu-id="e6601-311">**Inquire**: Displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>
- <span data-ttu-id="e6601-312">**Continuer**: affiche le message d’information et poursuit son exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-312">**Continue**: Displays the informational message, and continues running.</span></span>
- <span data-ttu-id="e6601-313">L' **interruption** n’est disponible que pour les flux de travail qui ne sont pas pris en charge dans PowerShell 6 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e6601-313">**Suspend** is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>
- <span data-ttu-id="e6601-314">**SilentlyContinue**: (valeur par défaut) aucun effet.</span><span class="sxs-lookup"><span data-stu-id="e6601-314">**SilentlyContinue**: (Default) No effect.</span></span> <span data-ttu-id="e6601-315">Les messages d’information ne sont pas affichés et le script se poursuit sans interruption.</span><span class="sxs-lookup"><span data-stu-id="e6601-315">The informational messages aren't displayed, and the script continues without interruption.</span></span>

### <a name="logevent"></a><span data-ttu-id="e6601-316">\$Log \* (événement)</span><span class="sxs-lookup"><span data-stu-id="e6601-316">\$Log\*Event</span></span>

<span data-ttu-id="e6601-317">Les variables de préférence d' \*\*événement log \*\*\* déterminent les types d’événements qui sont écrits dans le journal des événements PowerShell dans observateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="e6601-317">The **Log\*Event** preference variables determine which types of events are written to the PowerShell event log in Event Viewer.</span></span> <span data-ttu-id="e6601-318">Par défaut, seuls les événements du moteur et du fournisseur sont journalisés.</span><span class="sxs-lookup"><span data-stu-id="e6601-318">By default, only engine and provider events are logged.</span></span> <span data-ttu-id="e6601-319">Toutefois, vous pouvez utiliser les variables de préférence d' \*\*événement log \*\*\* pour personnaliser votre journal, comme la journalisation des événements sur les commandes.</span><span class="sxs-lookup"><span data-stu-id="e6601-319">But, you can use the **Log\*Event** preference variables to customize your log, such as logging events about commands.</span></span>

<span data-ttu-id="e6601-320">Les variables de préférence d' \*\*événement log \*\*\* sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-320">The **Log\*Event** preference variables are as follows:</span></span>

- <span data-ttu-id="e6601-321">`$LogCommandHealthEvent`: Journalise les erreurs et les exceptions dans l’initialisation et le traitement des commandes.</span><span class="sxs-lookup"><span data-stu-id="e6601-321">`$LogCommandHealthEvent`: Logs errors and exceptions in command initialization and processing.</span></span> <span data-ttu-id="e6601-322">La valeur par défaut est `$false` (non enregistré).</span><span class="sxs-lookup"><span data-stu-id="e6601-322">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="e6601-323">`$LogCommandLifecycleEvent`: Journalise le démarrage et l’arrêt des commandes et des pipelines de commande et des exceptions de sécurité dans la découverte des commandes.</span><span class="sxs-lookup"><span data-stu-id="e6601-323">`$LogCommandLifecycleEvent`: Logs the starting and stopping of commands and command pipelines and security exceptions in command discovery.</span></span> <span data-ttu-id="e6601-324">La valeur par défaut est `$false` (non enregistré).</span><span class="sxs-lookup"><span data-stu-id="e6601-324">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="e6601-325">`$LogEngineHealthEvent`: Journalise les erreurs et les échecs des sessions.</span><span class="sxs-lookup"><span data-stu-id="e6601-325">`$LogEngineHealthEvent`: Logs errors and failures of sessions.</span></span> <span data-ttu-id="e6601-326">La valeur par défaut est `$true` (journalisée).</span><span class="sxs-lookup"><span data-stu-id="e6601-326">The default is `$true` (logged).</span></span>
- <span data-ttu-id="e6601-327">`$LogEngineLifecycleEvent`: Journalise l’ouverture et la fermeture des sessions.</span><span class="sxs-lookup"><span data-stu-id="e6601-327">`$LogEngineLifecycleEvent`: Logs the opening and closing of sessions.</span></span> <span data-ttu-id="e6601-328">La valeur par défaut est `$true` (journalisée).</span><span class="sxs-lookup"><span data-stu-id="e6601-328">The default is `$true` (logged).</span></span>
- <span data-ttu-id="e6601-329">`$LogProviderHealthEvent`: Journalise des erreurs de fournisseur, telles que des erreurs de lecture et d’écriture, des erreurs de recherche et des erreurs d’appel.</span><span class="sxs-lookup"><span data-stu-id="e6601-329">`$LogProviderHealthEvent`: Logs provider errors, such as read and write errors, lookup errors, and invocation errors.</span></span> <span data-ttu-id="e6601-330">La valeur par défaut est `$true` (journalisée).</span><span class="sxs-lookup"><span data-stu-id="e6601-330">The default is `$true` (logged).</span></span>
- <span data-ttu-id="e6601-331">`$LogProviderLifecycleEvent`: Enregistre l’ajout et la suppression des fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6601-331">`$LogProviderLifecycleEvent`: Logs adding and removing of PowerShell providers.</span></span> <span data-ttu-id="e6601-332">La valeur par défaut est `$true` (journalisée).</span><span class="sxs-lookup"><span data-stu-id="e6601-332">The default is `$true` (logged).</span></span> <span data-ttu-id="e6601-333">Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-333">For information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

<span data-ttu-id="e6601-334">Pour activer un \*\*événement log \*\*\*, tapez la variable avec la valeur `$true` , par exemple :</span><span class="sxs-lookup"><span data-stu-id="e6601-334">To enable a **Log\*Event**, type the variable with a value of `$true`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="e6601-335">Pour désactiver un type d’événement, tapez la variable avec la valeur `$false` , par exemple :</span><span class="sxs-lookup"><span data-stu-id="e6601-335">To disable an event type, type the variable with a value of `$false`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $false
```

<span data-ttu-id="e6601-336">Les événements que vous activez sont effectifs uniquement pour la console PowerShell actuelle.</span><span class="sxs-lookup"><span data-stu-id="e6601-336">The events that you enable are effective only for the current PowerShell console.</span></span> <span data-ttu-id="e6601-337">Pour appliquer la configuration à toutes les consoles, enregistrez les paramètres de la variable dans votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6601-337">To apply the configuration to all consoles, save the variable settings in your PowerShell profile.</span></span> <span data-ttu-id="e6601-338">Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-338">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="e6601-339">\$MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="e6601-339">\$MaximumHistoryCount</span></span>

<span data-ttu-id="e6601-340">Détermine le nombre de commandes enregistrées dans l’historique des commandes pour la session active.</span><span class="sxs-lookup"><span data-stu-id="e6601-340">Determines how many commands are saved in the command history for the current session.</span></span>

<span data-ttu-id="e6601-341">**Valeurs valides**: 1-32768 ( `Int32` )</span><span class="sxs-lookup"><span data-stu-id="e6601-341">**Valid values**: 1 - 32768 (`Int32`)</span></span>

<span data-ttu-id="e6601-342">**Valeur par défaut**: 4096</span><span class="sxs-lookup"><span data-stu-id="e6601-342">**Default**: 4096</span></span>

<span data-ttu-id="e6601-343">Pour déterminer le nombre de commandes actuellement enregistrées dans l’historique de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="e6601-343">To determine the number of commands current saved in the command history, type:</span></span>

```powershell
(Get-History).Count
```

<span data-ttu-id="e6601-344">Pour afficher les commandes enregistrées dans votre historique de session, utilisez l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="e6601-344">To see the commands saved in your session history, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="e6601-345">Pour plus d’informations, consultez [about_History](about_History.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-345">For more information, see [about_History](about_History.md).</span></span>

### <a name="ofs"></a><span data-ttu-id="e6601-346">\$OFS</span><span class="sxs-lookup"><span data-stu-id="e6601-346">\$OFS</span></span>

<span data-ttu-id="e6601-347">Le séparateur de champ de sortie (OFS) spécifie le caractère qui sépare les éléments d’un tableau qui est converti en chaîne.</span><span class="sxs-lookup"><span data-stu-id="e6601-347">The Output Field Separator (OFS) specifies the character that separates the elements of an array that is converted to a string.</span></span>

<span data-ttu-id="e6601-348">**Valeurs valides**: n’importe quelle chaîne.</span><span class="sxs-lookup"><span data-stu-id="e6601-348">**Valid values**: Any string.</span></span>

<span data-ttu-id="e6601-349">**Valeur par défaut**: espace</span><span class="sxs-lookup"><span data-stu-id="e6601-349">**Default**: Space</span></span>

<span data-ttu-id="e6601-350">Par défaut, la `$OFS` variable n’existe pas et le séparateur de fichier de sortie est un espace, mais vous pouvez ajouter cette variable et la définir sur n’importe quelle chaîne.</span><span class="sxs-lookup"><span data-stu-id="e6601-350">By default, the `$OFS` variable doesn't exist and the output file separator is a space, but you can add this variable and set it to any string.</span></span> <span data-ttu-id="e6601-351">Vous pouvez modifier la valeur de `$OFS` dans votre session, en tapant `$OFS="<value>"` .</span><span class="sxs-lookup"><span data-stu-id="e6601-351">You can change the value of `$OFS` in your session, by typing `$OFS="<value>"`.</span></span>

> [!NOTE]
> <span data-ttu-id="e6601-352">Si vous prévoyez la valeur par défaut d’un espace ( `" "` ) dans votre script, module ou sortie de configuration, veillez à ce que la `$OFS` valeur par défaut n’ait pas été modifiée ailleurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="e6601-352">If you're expecting the default value of a space (`" "`) in your script, module, or configuration output, be careful that the `$OFS` default value hasn't been changed elsewhere in your code.</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-353">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-353">Examples</span></span>

<span data-ttu-id="e6601-354">Cet exemple montre qu’un espace est utilisé pour séparer les valeurs lorsqu’un tableau est converti en chaîne.</span><span class="sxs-lookup"><span data-stu-id="e6601-354">This example shows that a space is used to separate the values when an array is converted to a string.</span></span> <span data-ttu-id="e6601-355">Dans ce cas, un tableau d’entiers est stocké dans une variable, puis la variable est convertie en chaîne.</span><span class="sxs-lookup"><span data-stu-id="e6601-355">In this case, an array of integers is stored in a variable and then the variable is cast as a string.</span></span>

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

<span data-ttu-id="e6601-356">Pour modifier le séparateur, ajoutez la `$OFS` variable en lui assignant une valeur.</span><span class="sxs-lookup"><span data-stu-id="e6601-356">To change the separator, add the `$OFS` variable by assigning a value to it.</span></span>
<span data-ttu-id="e6601-357">La variable doit être nommée `$OFS` .</span><span class="sxs-lookup"><span data-stu-id="e6601-357">The variable must be named `$OFS`.</span></span>

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

<span data-ttu-id="e6601-358">Pour restaurer le comportement par défaut, vous pouvez assigner un espace ( `" "` ) à la valeur de `$OFS` ou supprimer la variable.</span><span class="sxs-lookup"><span data-stu-id="e6601-358">To restore the default behavior, you can assign a space (`" "`) to the value of `$OFS` or delete the variable.</span></span> <span data-ttu-id="e6601-359">Les commandes suivantes suppriment la variable, puis vérifient que le séparateur est un espace.</span><span class="sxs-lookup"><span data-stu-id="e6601-359">The following commands delete the variable and then verify that the separator is a space.</span></span>

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a><span data-ttu-id="e6601-360">\$OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="e6601-360">\$OutputEncoding</span></span>

<span data-ttu-id="e6601-361">Détermine la méthode d’encodage de caractères que PowerShell utilise lorsqu’il envoie du texte à d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="e6601-361">Determines the character encoding method that PowerShell uses when it sends text to other applications.</span></span>

<span data-ttu-id="e6601-362">Par exemple, si une application retourne des chaînes Unicode à PowerShell, vous devrez peut-être modifier la valeur en **UnicodeEncoding** pour envoyer correctement les caractères.</span><span class="sxs-lookup"><span data-stu-id="e6601-362">For example, if an application returns Unicode strings to PowerShell, you might need to change the value to **UnicodeEncoding** to send the characters correctly.</span></span>

<span data-ttu-id="e6601-363">Les valeurs valides sont les suivantes : objets dérivés d’une classe d’encodage, tels que **ASCIIEncoding**, **SBCSCodePageEncoding**, **UTF7Encoding**, **UTF8Encoding**, **UTF32Encoding** et **UnicodeEncoding**.</span><span class="sxs-lookup"><span data-stu-id="e6601-363">The valid values are as follows: Objects derived from an Encoding class, such as **ASCIIEncoding**, **SBCSCodePageEncoding**, **UTF7Encoding**, **UTF8Encoding**, **UTF32Encoding**, and **UnicodeEncoding**.</span></span>

<span data-ttu-id="e6601-364">**Default**: objet UTF8Encoding (System. Text. UTF8Encoding)</span><span class="sxs-lookup"><span data-stu-id="e6601-364">**Default**: UTF8Encoding object (System.Text.UTF8Encoding)</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-365">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-365">Examples</span></span>

<span data-ttu-id="e6601-366">Cet exemple montre comment rendre la commande Windows **findstr.exe** fonctionner dans PowerShell sur un ordinateur localisé pour une langue qui utilise des caractères Unicode, tels que le chinois.</span><span class="sxs-lookup"><span data-stu-id="e6601-366">This example shows how to make the Windows **findstr.exe** command work in PowerShell on a computer that is localized for a language that uses Unicode characters, such as Chinese.</span></span>

<span data-ttu-id="e6601-367">La première commande recherche la valeur de `$OutputEncoding` .</span><span class="sxs-lookup"><span data-stu-id="e6601-367">The first command finds the value of `$OutputEncoding`.</span></span> <span data-ttu-id="e6601-368">Étant donné que la valeur est un objet d’encodage, Affichez uniquement sa propriété **EncodingName** .</span><span class="sxs-lookup"><span data-stu-id="e6601-368">Because the value is an encoding object, display only its **EncodingName** property.</span></span>

```powershell
$OutputEncoding.EncodingName
```

<span data-ttu-id="e6601-369">Dans cet exemple, une commande **findstr.exe** est utilisée pour rechercher deux caractères chinois présents dans le `Test.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="e6601-369">In this example, a **findstr.exe** command is used to search for two Chinese characters that are present in the `Test.txt` file.</span></span> <span data-ttu-id="e6601-370">Quand cette commande **findstr.exe** est exécutée dans l’invite de commandes Windows (**cmd.exe**), **findstr.exe** recherche les caractères dans le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e6601-370">When this **findstr.exe** command is run in the Windows Command Prompt (**cmd.exe**), **findstr.exe** finds the characters in the text file.</span></span> <span data-ttu-id="e6601-371">Toutefois, lorsque vous exécutez la même commande **findstr.exe** dans PowerShell, les caractères ne sont pas trouvés, car PowerShell les envoie à **findstr.exe** en texte ASCII, et non en texte Unicode.</span><span class="sxs-lookup"><span data-stu-id="e6601-371">However, when you run the same **findstr.exe** command in PowerShell, the characters aren't found because the PowerShell sends them to **findstr.exe** in ASCII text, instead of in Unicode text.</span></span>

```powershell
findstr <Unicode-characters>
```

<span data-ttu-id="e6601-372">Pour que la commande fonctionne dans PowerShell, définissez la valeur de la `$OutputEncoding` propriété **OutputEncoding** de la console, en fonction des paramètres régionaux sélectionnés pour Windows.</span><span class="sxs-lookup"><span data-stu-id="e6601-372">To make the command work in PowerShell, set the value of `$OutputEncoding` to the value of the **OutputEncoding** property of the console, that is based on the locale selected for Windows.</span></span> <span data-ttu-id="e6601-373">Étant donné que **OutputEncoding** est une propriété statique de la console, utilisez le double signe deux-points ( `::` ) dans la commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-373">Because **OutputEncoding** is a static property of the console, use double-colons (`::`) in the command.</span></span>

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

<span data-ttu-id="e6601-374">Après la modification de l’encodage, la commande **findstr.exe** recherche les caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="e6601-374">After the encoding change, the **findstr.exe** command finds the Unicode characters.</span></span>

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a><span data-ttu-id="e6601-375">\$ProgressPreference</span><span class="sxs-lookup"><span data-stu-id="e6601-375">\$ProgressPreference</span></span>

<span data-ttu-id="e6601-376">Détermine la manière dont PowerShell répond aux mises à jour de progression générées par un script, une applet de commande ou un fournisseur, comme les barres de progression générées par l’applet [de commande Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) .</span><span class="sxs-lookup"><span data-stu-id="e6601-376">Determines how PowerShell responds to progress updates generated by a script, cmdlet, or provider, such as the progress bars generated by the [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) cmdlet.</span></span>
<span data-ttu-id="e6601-377">L' `Write-Progress` applet de commande crée des barres de progression qui indiquent l’état d’une commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-377">The `Write-Progress` cmdlet creates progress bars that show a command's status.</span></span>

<span data-ttu-id="e6601-378">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-378">The valid values are as follows:</span></span>

- <span data-ttu-id="e6601-379">**Stop**: n’affiche pas la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="e6601-379">**Stop**: Doesn't display the progress bar.</span></span> <span data-ttu-id="e6601-380">Au lieu de cela, il affiche un message d’erreur et arrête l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-380">Instead, it displays an error message and stops executing.</span></span>
- <span data-ttu-id="e6601-381">**Rechercher**: n’affiche pas la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="e6601-381">**Inquire**: Doesn't display the progress bar.</span></span> <span data-ttu-id="e6601-382">Demande l’autorisation de continuer.</span><span class="sxs-lookup"><span data-stu-id="e6601-382">Prompts for permission to continue.</span></span> <span data-ttu-id="e6601-383">Si vous répondez avec `Y` ou `A` , la barre de progression s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e6601-383">If you reply with `Y` or `A`, it displays the progress bar.</span></span>
- <span data-ttu-id="e6601-384">**Continuer**: (valeur par défaut) affiche la barre de progression et poursuit l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-384">**Continue**: (Default) Displays the progress bar and continues with execution.</span></span>
- <span data-ttu-id="e6601-385">**SilentlyContinue**: exécute la commande, mais n’affiche pas la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="e6601-385">**SilentlyContinue**: Executes the command, but doesn't display the progress bar.</span></span>

### <a name="psemailserver"></a><span data-ttu-id="e6601-386">\$PSEmailServer</span><span class="sxs-lookup"><span data-stu-id="e6601-386">\$PSEmailServer</span></span>

<span data-ttu-id="e6601-387">Spécifie le serveur de messagerie par défaut qui est utilisé pour envoyer des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="e6601-387">Specifies the default e-mail server that is used to send email messages.</span></span> <span data-ttu-id="e6601-388">Cette variable de préférence est utilisée par les cmdlets qui envoient des messages électroniques, tels que l’applet de commande [Send-MailMessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) .</span><span class="sxs-lookup"><span data-stu-id="e6601-388">This preference variable is used by cmdlets that send email, such as the [Send-MailMessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) cmdlet.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="e6601-389">\$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="e6601-389">\$PSDefaultParameterValues</span></span>

<span data-ttu-id="e6601-390">Spécifie les valeurs par défaut des paramètres des applets de commande et des fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="e6601-390">Specifies default values for the parameters of cmdlets and advanced functions.</span></span>
<span data-ttu-id="e6601-391">La valeur de `$PSDefaultParameterValues` est une table de hachage où la clé se compose du nom de l’applet de commande et du nom du paramètre séparés par un signe deux-points ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="e6601-391">The value of `$PSDefaultParameterValues` is a hash table where the key consists of the cmdlet name and parameter name separated by a colon (`:`).</span></span> <span data-ttu-id="e6601-392">La valeur est une valeur par défaut personnalisée que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="e6601-392">The value is a custom default value that you specify.</span></span>

<span data-ttu-id="e6601-393">`$PSDefaultParameterValues` a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e6601-393">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="e6601-394">Pour plus d’informations sur cette variable de préférence, consultez [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-394">For more information about this preference variable, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="psmoduleautoloadingpreference"></a><span data-ttu-id="e6601-395">\$PSModuleAutoloadingPreference</span><span class="sxs-lookup"><span data-stu-id="e6601-395">\$PSModuleAutoloadingPreference</span></span>

<span data-ttu-id="e6601-396">Active et désactive l’importation automatique de modules dans la session.</span><span class="sxs-lookup"><span data-stu-id="e6601-396">Enables and disables automatic importing of modules in the session.</span></span> <span data-ttu-id="e6601-397">**All** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6601-397">**All** is the default.</span></span> <span data-ttu-id="e6601-398">Quelle que soit la valeur de la variable, vous pouvez utiliser [import-module](xref:Microsoft.PowerShell.Core.Import-Module) pour importer un module.</span><span class="sxs-lookup"><span data-stu-id="e6601-398">Regardless of the variable's value, you can use [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) to import a module.</span></span>

<span data-ttu-id="e6601-399">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="e6601-399">Valid values are:</span></span>

- <span data-ttu-id="e6601-400">**Tous : les** modules sont importés automatiquement à la première utilisation.</span><span class="sxs-lookup"><span data-stu-id="e6601-400">**All**: Modules are imported automatically on first-use.</span></span> <span data-ttu-id="e6601-401">Pour importer un module, récupérez ou utilisez une commande quelconque dans le module.</span><span class="sxs-lookup"><span data-stu-id="e6601-401">To import a module, get or use any command in the module.</span></span> <span data-ttu-id="e6601-402">Par exemple, utilisez `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="e6601-402">For example, use `Get-Command`.</span></span>
- <span data-ttu-id="e6601-403">**ModuleQualified**: les modules sont importés automatiquement uniquement lorsqu’un utilisateur utilise le nom qualifié du module d’une commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="e6601-403">**ModuleQualified**: Modules are imported automatically only when a user uses the module-qualified name of a command in the module.</span></span> <span data-ttu-id="e6601-404">Par exemple, si l’utilisateur tape `MyModule\MyCommand` , PowerShell importe le module **MyModule** .</span><span class="sxs-lookup"><span data-stu-id="e6601-404">For example, if the user types `MyModule\MyCommand`, PowerShell imports the **MyModule** module.</span></span>
- <span data-ttu-id="e6601-405">**Aucun**: l’importation automatique des modules est désactivée dans la session.</span><span class="sxs-lookup"><span data-stu-id="e6601-405">**None**: Automatic importing of modules is disabled in the session.</span></span> <span data-ttu-id="e6601-406">Pour importer un module, utilisez l' `Import-Module` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-406">To import a module, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="e6601-407">Pour plus d’informations sur l’importation automatique de modules, consultez [about_Modules](about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-407">For more information about automatic importing of modules, see [about_Modules](about_Modules.md).</span></span>

### <a name="pssessionapplicationname"></a><span data-ttu-id="e6601-408">\$PSSessionApplicationName</span><span class="sxs-lookup"><span data-stu-id="e6601-408">\$PSSessionApplicationName</span></span>

<span data-ttu-id="e6601-409">Spécifie le nom d’application par défaut pour une commande à distance qui utilise la technologie Web Services for Management (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="e6601-409">Specifies the default application name for a remote command that uses Web Services for Management (WS-Management) technology.</span></span> <span data-ttu-id="e6601-410">Pour plus d’informations, consultez [à propos de Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).</span><span class="sxs-lookup"><span data-stu-id="e6601-410">For more information, see [About Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).</span></span>

<span data-ttu-id="e6601-411">Le nom d’application par défaut du système est `WSMAN` , mais vous pouvez utiliser cette variable de préférence pour modifier la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6601-411">The system default application name is `WSMAN`, but you can use this preference variable to change the default.</span></span>

<span data-ttu-id="e6601-412">Le nom de l’application est le dernier nœud d’un URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="e6601-412">The application name is the last node in a connection URI.</span></span> <span data-ttu-id="e6601-413">Par exemple, le nom de l’application dans l’exemple d’URI suivant est `WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="e6601-413">For example, the application name in the following sample URI is `WSMAN`.</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="e6601-414">Le nom de l’application par défaut est utilisé lorsque la commande distante ne spécifie pas un URI de connexion ou un nom d’application.</span><span class="sxs-lookup"><span data-stu-id="e6601-414">The default application name is used when the remote command doesn't specify a connection URI or an application name.</span></span>

<span data-ttu-id="e6601-415">Le service **WinRM** utilise le nom de l’application pour sélectionner un écouteur afin de traiter la demande de connexion.</span><span class="sxs-lookup"><span data-stu-id="e6601-415">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="e6601-416">La valeur du paramètre doit correspondre à la valeur de la propriété **URLPrefix** d’un écouteur sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e6601-416">The parameter's value should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

<span data-ttu-id="e6601-417">Pour remplacer la valeur système par défaut et la valeur de cette variable, et sélectionner un autre nom d’application pour une session particulière, utilisez les paramètres **ConnectionUri** ou **applicationName** des applets de commande [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)ou [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .</span><span class="sxs-lookup"><span data-stu-id="e6601-417">To override the system default and the value of this variable, and select a different application name for a particular session, use the **ConnectionURI** or **ApplicationName** parameters of the [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession), or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlets.</span></span>

<span data-ttu-id="e6601-418">La `$PSSessionApplicationName` variable de préférence est définie sur l’ordinateur local, mais elle spécifie un écouteur sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e6601-418">The `$PSSessionApplicationName` preference variable is set on the local computer, but it specifies a listener on the remote computer.</span></span> <span data-ttu-id="e6601-419">Si le nom d’application que vous spécifiez n’existe pas sur l’ordinateur distant, la commande d’établissement de la session échoue.</span><span class="sxs-lookup"><span data-stu-id="e6601-419">If the application name that you specify doesn't exist on the remote computer, the command to establish the session fails.</span></span>

### <a name="pssessionconfigurationname"></a><span data-ttu-id="e6601-420">\$PSSessionConfigurationName</span><span class="sxs-lookup"><span data-stu-id="e6601-420">\$PSSessionConfigurationName</span></span>

<span data-ttu-id="e6601-421">Spécifie la configuration de session par défaut utilisée pour les **sessions PSSession** créés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e6601-421">Specifies the default session configuration that is used for **PSSessions** created in the current session.</span></span>

<span data-ttu-id="e6601-422">Cette variable de préférence est définie sur l’ordinateur local, mais elle spécifie une configuration de session qui se trouve sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e6601-422">This preference variable is set on the local computer, but it specifies a session configuration that's located on the remote computer.</span></span>

<span data-ttu-id="e6601-423">La valeur de la `$PSSessionConfigurationName` variable est un URI de ressource complet.</span><span class="sxs-lookup"><span data-stu-id="e6601-423">The value of the `$PSSessionConfigurationName` variable is a fully qualified resource URI.</span></span>

<span data-ttu-id="e6601-424">La valeur par défaut `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` indique la configuration de session **Microsoft. PowerShell** sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e6601-424">The default value `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` indicates the **Microsoft.PowerShell** session configuration on the remote computer.</span></span>

<span data-ttu-id="e6601-425">Si vous spécifiez uniquement un nom de configuration, l’URI de schéma suivant est ajouté :</span><span class="sxs-lookup"><span data-stu-id="e6601-425">If you specify only a configuration name, the following schema URI is prepended:</span></span>

`http://schemas.microsoft.com/PowerShell/`

<span data-ttu-id="e6601-426">Vous pouvez remplacer la valeur par défaut et sélectionner une autre configuration de session pour une session particulière à l’aide du paramètre **ConfigurationName** des `New-PSSession` applets de commande, `Enter-PSSession` ou `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e6601-426">You can override the default and select a different session configuration for a particular session by using the **ConfigurationName** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="e6601-427">Vous pouvez modifier la valeur de cette variable à tout moment.</span><span class="sxs-lookup"><span data-stu-id="e6601-427">You can change the value of this variable at any time.</span></span> <span data-ttu-id="e6601-428">Dans ce cas, n’oubliez pas que la configuration de session que vous sélectionnez doit exister sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e6601-428">When you do, remember that the session configuration that you select must exist on the remote computer.</span></span> <span data-ttu-id="e6601-429">Si ce n’est pas le cas, la commande permettant de créer une session qui utilise la configuration de session échoue.</span><span class="sxs-lookup"><span data-stu-id="e6601-429">If it doesn't, the command to create a session that uses the session configuration fails.</span></span>

<span data-ttu-id="e6601-430">Cette variable de préférence ne détermine pas les configurations de sessions locales utilisées lorsque les utilisateurs distants créent une session qui se connecte à cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e6601-430">This preference variable doesn't determine which local session configurations are used when remote users create a session that connects to this computer.</span></span>
<span data-ttu-id="e6601-431">Toutefois, vous pouvez utiliser les autorisations pour les configurations de session locale pour déterminer les utilisateurs qui peuvent les utiliser.</span><span class="sxs-lookup"><span data-stu-id="e6601-431">However, you can use the permissions for the local session configurations to determine which users may use them.</span></span>

### <a name="pssessionoption"></a><span data-ttu-id="e6601-432">\$PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="e6601-432">\$PSSessionOption</span></span>

<span data-ttu-id="e6601-433">Établit les valeurs par défaut pour les options utilisateur avancées dans une session à distance.</span><span class="sxs-lookup"><span data-stu-id="e6601-433">Establishes the default values for advanced user options in a remote session.</span></span>
<span data-ttu-id="e6601-434">Ces préférences de l’option remplacent les valeurs par défaut du système pour les options de session.</span><span class="sxs-lookup"><span data-stu-id="e6601-434">These option preferences override the system default values for session options.</span></span>

<span data-ttu-id="e6601-435">La `$PSSessionOption` variable contient un objet **PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="e6601-435">The `$PSSessionOption` variable contains a **PSSessionOption** object.</span></span> <span data-ttu-id="e6601-436">Pour plus d’informations, consultez [System. Management. Automation. Remoting. PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).</span><span class="sxs-lookup"><span data-stu-id="e6601-436">For more information, see [System.Management.Automation.Remoting.PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).</span></span>
<span data-ttu-id="e6601-437">Chaque propriété de l’objet représente une option de session.</span><span class="sxs-lookup"><span data-stu-id="e6601-437">Each property of the object represents a session option.</span></span> <span data-ttu-id="e6601-438">Par exemple, la propriété **NoCompression** active la compression des données pendant la session.</span><span class="sxs-lookup"><span data-stu-id="e6601-438">For example, the **NoCompression** property turns of data compression during the session.</span></span>

<span data-ttu-id="e6601-439">Par défaut, la `$PSSessionOption` variable contient un objet **PSSessionOption** avec les valeurs par défaut pour toutes les options, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e6601-439">By default, the `$PSSessionOption` variable contains a **PSSessionOption** object with the default values for all options, as shown below.</span></span>

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

<span data-ttu-id="e6601-440">Pour obtenir une description de ces options et des informations supplémentaires, consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="e6601-440">For descriptions of these options and more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span> <span data-ttu-id="e6601-441">Pour plus d’informations sur les commandes et les sessions à distance, consultez [about_Remote](about_Remote.md) et [about_PSSessions](about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-441">For more information about remote commands and sessions, see [about_Remote](about_Remote.md) and [about_PSSessions](about_PSSessions.md).</span></span>

<span data-ttu-id="e6601-442">Pour modifier la valeur de la `$PSSessionOption` variable de préférence, utilisez l' `New-PSSessionOption` applet de commande pour créer un objet **PSSessionOption** avec les valeurs d’option que vous préférez.</span><span class="sxs-lookup"><span data-stu-id="e6601-442">To change the value of the `$PSSessionOption` preference variable, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object with the option values you prefer.</span></span> <span data-ttu-id="e6601-443">Enregistrez la sortie dans une variable appelée `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="e6601-443">Save the output in a variable called `$PSSessionOption`.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

<span data-ttu-id="e6601-444">Pour utiliser la `$PSSessionOption` variable de préférence dans chaque session PowerShell, ajoutez une `New-PSSessionOption` commande qui crée la `$PSSessionOption` variable à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6601-444">To use the `$PSSessionOption` preference variable in every PowerShell session, add a `New-PSSessionOption` command that creates the `$PSSessionOption` variable to your PowerShell profile.</span></span> <span data-ttu-id="e6601-445">Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-445">For more information, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="e6601-446">Vous pouvez définir des options personnalisées pour une session à distance particulière.</span><span class="sxs-lookup"><span data-stu-id="e6601-446">You can set custom options for a particular remote session.</span></span> <span data-ttu-id="e6601-447">Les options que vous définissez prévalent sur les valeurs par défaut du système et sur la valeur de la `$PSSessionOption` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="e6601-447">The options that you set take precedence over the system defaults and the value of the `$PSSessionOption` preference variable.</span></span>

<span data-ttu-id="e6601-448">Pour définir des options de session personnalisées, utilisez l' `New-PSSessionOption` applet de commande pour créer un objet **PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="e6601-448">To set custom session options, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object.</span></span> <span data-ttu-id="e6601-449">Ensuite, utilisez l’objet **PSSessionOption** comme valeur du paramètre **SessionOption** dans les applets de commande qui créent une session, telles que `New-PSSession` , `Enter-PSSession` et `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e6601-449">Then, use the **PSSessionOption** object as the value of the **SessionOption** parameter in cmdlets that create a session, such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

### <a name="transcript"></a><span data-ttu-id="e6601-450">$Transcript</span><span class="sxs-lookup"><span data-stu-id="e6601-450">$Transcript</span></span>

<span data-ttu-id="e6601-451">Utilisé par `Start-Transcript` pour spécifier le nom et l’emplacement du fichier de transcription.</span><span class="sxs-lookup"><span data-stu-id="e6601-451">Used by `Start-Transcript` to specify the name and location of the transcript file.</span></span> <span data-ttu-id="e6601-452">Si vous ne spécifiez pas de valeur pour le paramètre **path** , `Start-Transcript` utilise le chemin d’accès dans la valeur de la `$Transcript` variable globale.</span><span class="sxs-lookup"><span data-stu-id="e6601-452">If you do not specify a value for the **Path** parameter, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="e6601-453">Si vous n’avez pas créé cette variable, `Start-Transcript` stocke les transcriptions dans le `$Home\My Documents` répertoire sous forme de `\PowerShell_transcript.<time-stamp>.txt` fichiers.</span><span class="sxs-lookup"><span data-stu-id="e6601-453">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents` directory as `\PowerShell_transcript.<time-stamp>.txt` files.</span></span>

### <a name="verbosepreference"></a><span data-ttu-id="e6601-454">\$VerbosePreference</span><span class="sxs-lookup"><span data-stu-id="e6601-454">\$VerbosePreference</span></span>

<span data-ttu-id="e6601-455">Détermine la manière dont PowerShell répond aux messages détaillés générés par un script, une applet de commande ou un fournisseur, tels que les messages générés par l’applet de commande [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) .</span><span class="sxs-lookup"><span data-stu-id="e6601-455">Determines how PowerShell responds to verbose messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdlet.</span></span>
<span data-ttu-id="e6601-456">Les messages détaillés décrivent les actions effectuées pour exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-456">Verbose messages describe the actions performed to execute a command.</span></span>

<span data-ttu-id="e6601-457">Par défaut, les messages détaillés ne sont pas affichés, mais vous pouvez modifier ce comportement en modifiant la valeur de `$VerbosePreference` .</span><span class="sxs-lookup"><span data-stu-id="e6601-457">By default, verbose messages aren't displayed, but you can change this behavior by changing the value of `$VerbosePreference`.</span></span>

<span data-ttu-id="e6601-458">Vous pouvez utiliser le paramètre commun **Verbose** d’une applet de commande pour afficher ou masquer les messages détaillés pour une commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="e6601-458">You can use the **Verbose** common parameter of a cmdlet to display or hide the verbose messages for a specific command.</span></span> <span data-ttu-id="e6601-459">Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-459">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="e6601-460">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-460">The valid values are as follows:</span></span>

- <span data-ttu-id="e6601-461">**Arrêter**: affiche le message détaillé et un message d’erreur, puis arrête l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-461">**Stop**: Displays the verbose message and an error message and then stops executing.</span></span>
- <span data-ttu-id="e6601-462">**Rechercher**: affiche le message détaillé, puis affiche une invite vous demandant si vous souhaitez continuer.</span><span class="sxs-lookup"><span data-stu-id="e6601-462">**Inquire**: Displays the verbose message and then displays a prompt that asks you whether you want to continue.</span></span>
- <span data-ttu-id="e6601-463">**Continuer**: affiche le message détaillé, puis poursuit l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-463">**Continue**: Displays the verbose message and then continues with execution.</span></span>
- <span data-ttu-id="e6601-464">**SilentlyContinue**: (par défaut) n’affiche pas le message détaillé.</span><span class="sxs-lookup"><span data-stu-id="e6601-464">**SilentlyContinue**: (Default) Doesn't display the verbose message.</span></span> <span data-ttu-id="e6601-465">Continue l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-465">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-466">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-466">Examples</span></span>

<span data-ttu-id="e6601-467">Ces exemples illustrent l’effet des différentes valeurs de `$VerbosePreference` et le paramètre **Verbose** pour remplacer la valeur de préférence.</span><span class="sxs-lookup"><span data-stu-id="e6601-467">These examples show the effect of the different values of `$VerbosePreference` and the **Verbose** parameter to override the preference value.</span></span>

<span data-ttu-id="e6601-468">Cet exemple montre l’effet de la valeur **SilentlyContinue** , qui est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6601-468">This example shows the effect of the **SilentlyContinue** value, that is the default.</span></span> <span data-ttu-id="e6601-469">La commande utilise le paramètre **message** , mais n’écrit pas de message dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6601-469">The command uses the **Message** parameter, but doesn't write a message to the PowerShell console.</span></span>

```powershell
Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="e6601-470">Lorsque le paramètre **Verbose** est utilisé, le message est écrit.</span><span class="sxs-lookup"><span data-stu-id="e6601-470">When the **Verbose** parameter is used, the message is written.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="e6601-471">Cet exemple montre l’effet de la valeur **continue** .</span><span class="sxs-lookup"><span data-stu-id="e6601-471">This example shows the effect of the **Continue** value.</span></span> <span data-ttu-id="e6601-472">La `$VerbosePreference` variable est définie pour **Continuer** et le message s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e6601-472">The `$VerbosePreference` variable is set to **Continue** and the message is displayed.</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="e6601-473">Cet exemple utilise le paramètre **Verbose** avec une valeur de `$false` qui remplace la valeur **continue** .</span><span class="sxs-lookup"><span data-stu-id="e6601-473">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Continue** value.</span></span> <span data-ttu-id="e6601-474">Le message n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="e6601-474">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="e6601-475">Cet exemple montre l’effet de la valeur d' **arrêt** .</span><span class="sxs-lookup"><span data-stu-id="e6601-475">This example shows the effect of the **Stop** value.</span></span> <span data-ttu-id="e6601-476">La `$VerbosePreference` variable est définie sur **Stop** et le message s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e6601-476">The `$VerbosePreference` variable is set to **Stop** and the message is displayed.</span></span> <span data-ttu-id="e6601-477">La commande est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="e6601-477">The command is stopped.</span></span>

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="e6601-478">Cet exemple utilise le paramètre **Verbose** avec une valeur de `$false` qui remplace la valeur d' **arrêt** .</span><span class="sxs-lookup"><span data-stu-id="e6601-478">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Stop** value.</span></span> <span data-ttu-id="e6601-479">Le message n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="e6601-479">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="e6601-480">Cet exemple montre l’effet de la valeur de **recherche** .</span><span class="sxs-lookup"><span data-stu-id="e6601-480">This example shows the effect of the **Inquire** value.</span></span> <span data-ttu-id="e6601-481">La `$VerbosePreference` variable est définie sur **inquire**.</span><span class="sxs-lookup"><span data-stu-id="e6601-481">The `$VerbosePreference` variable is set to **Inquire**.</span></span> <span data-ttu-id="e6601-482">Le message s’affiche et l’utilisateur est invité à confirmer l’intervention.</span><span class="sxs-lookup"><span data-stu-id="e6601-482">The message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="e6601-483">Cet exemple utilise le paramètre **Verbose** avec une valeur de `$false` qui remplace la valeur de **recherche** .</span><span class="sxs-lookup"><span data-stu-id="e6601-483">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Inquire** value.</span></span> <span data-ttu-id="e6601-484">L’utilisateur n’est pas invité et le message n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="e6601-484">The user isn't prompted and the message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a><span data-ttu-id="e6601-485">\$WarningPreference</span><span class="sxs-lookup"><span data-stu-id="e6601-485">\$WarningPreference</span></span>

<span data-ttu-id="e6601-486">Détermine la manière dont PowerShell répond aux messages d’avertissement générés par un script, une applet de commande ou un fournisseur, tels que les messages générés par l’applet de commande [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) .</span><span class="sxs-lookup"><span data-stu-id="e6601-486">Determines how PowerShell responds to warning messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) cmdlet.</span></span>

<span data-ttu-id="e6601-487">Par défaut, les messages d’avertissement s’affichent et l’exécution se poursuit, mais vous pouvez modifier ce comportement en modifiant la valeur de `$WarningPreference` .</span><span class="sxs-lookup"><span data-stu-id="e6601-487">By default, warning messages are displayed and execution continues, but you can change this behavior by changing the value of `$WarningPreference`.</span></span>

<span data-ttu-id="e6601-488">Vous pouvez utiliser le paramètre commun **WarningAction** d’une applet de commande pour déterminer comment PowerShell répond aux avertissements d’une commande particulière.</span><span class="sxs-lookup"><span data-stu-id="e6601-488">You can use the **WarningAction** common parameter of a cmdlet to determine how PowerShell responds to warnings from a particular command.</span></span> <span data-ttu-id="e6601-489">Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="e6601-489">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="e6601-490">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-490">The valid values are as follows:</span></span>

- <span data-ttu-id="e6601-491">**Arrêter**: affiche le message d’avertissement et un message d’erreur, puis arrête l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-491">**Stop**: Displays the warning message and an error message and then stops executing.</span></span>
- <span data-ttu-id="e6601-492">**Rechercher**: affiche le message d’avertissement, puis demande l’autorisation de continuer.</span><span class="sxs-lookup"><span data-stu-id="e6601-492">**Inquire**: Displays the warning message and then prompts for permission to continue.</span></span>
- <span data-ttu-id="e6601-493">**Continuer**: (valeur par défaut) affiche le message d’avertissement, puis continue l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-493">**Continue**: (Default) Displays the warning message and then continues executing.</span></span>
- <span data-ttu-id="e6601-494">**SilentlyContinue**: n’affiche pas le message d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="e6601-494">**SilentlyContinue**: Doesn't display the warning message.</span></span> <span data-ttu-id="e6601-495">Continue l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6601-495">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-496">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-496">Examples</span></span>

<span data-ttu-id="e6601-497">Ces exemples illustrent l’effet des différentes valeurs de `$WarningPreference` .</span><span class="sxs-lookup"><span data-stu-id="e6601-497">These examples show the effect of the different values of `$WarningPreference`.</span></span>
<span data-ttu-id="e6601-498">Le paramètre **WarningAction** remplace la valeur de préférence.</span><span class="sxs-lookup"><span data-stu-id="e6601-498">The **WarningAction** parameter overrides the preference value.</span></span>

<span data-ttu-id="e6601-499">Cet exemple montre l’effet de la valeur par défaut, **continue**.</span><span class="sxs-lookup"><span data-stu-id="e6601-499">This example shows the effect of the default value, **Continue**.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

<span data-ttu-id="e6601-500">Cet exemple utilise le paramètre **WarningAction** avec la valeur **SilentlyContinue** pour supprimer l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="e6601-500">This example uses the **WarningAction** parameter with the value **SilentlyContinue** to suppress the warning.</span></span> <span data-ttu-id="e6601-501">Le message n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="e6601-501">The message isn't displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="e6601-502">Cet exemple remplace la `$WarningPreference` variable par la valeur **SilentlyContinue** .</span><span class="sxs-lookup"><span data-stu-id="e6601-502">This example changes the `$WarningPreference` variable to the **SilentlyContinue** value.</span></span> <span data-ttu-id="e6601-503">Le message n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="e6601-503">The message isn't displayed.</span></span>

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

<span data-ttu-id="e6601-504">Cet exemple utilise le paramètre **WarningAction** pour s’arrêter lorsqu’un avertissement est généré.</span><span class="sxs-lookup"><span data-stu-id="e6601-504">This example uses the **WarningAction** parameter to stop when a warning is generated.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

<span data-ttu-id="e6601-505">Cet exemple remplace la `$WarningPreference` variable par la valeur de **recherche** .</span><span class="sxs-lookup"><span data-stu-id="e6601-505">This example changes the `$WarningPreference` variable to the **Inquire** value.</span></span> <span data-ttu-id="e6601-506">L’utilisateur est invité à confirmer l’intervention.</span><span class="sxs-lookup"><span data-stu-id="e6601-506">The user is prompted for confirmation.</span></span>

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="e6601-507">Cet exemple utilise le paramètre **WarningAction** avec la valeur **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="e6601-507">This example uses the **WarningAction** parameter with the value **SilentlyContinue**.</span></span> <span data-ttu-id="e6601-508">La commande continue de s’exécuter et aucun message n’est affiché.</span><span class="sxs-lookup"><span data-stu-id="e6601-508">The command continues to execute and no message is displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="e6601-509">Cet exemple modifie la `$WarningPreference` valeur en **Stop**.</span><span class="sxs-lookup"><span data-stu-id="e6601-509">This example changes the `$WarningPreference` value to **Stop**.</span></span>

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

<span data-ttu-id="e6601-510">Cet exemple utilise **WarningAction** avec la valeur **Inquiry** .</span><span class="sxs-lookup"><span data-stu-id="e6601-510">This example uses the **WarningAction** with the **Inquire** value.</span></span> <span data-ttu-id="e6601-511">Lorsqu’un avertissement se produit, l’utilisateur est invité à entrer un message.</span><span class="sxs-lookup"><span data-stu-id="e6601-511">The user is prompted when a warning occurs.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a><span data-ttu-id="e6601-512">\$WhatIfPreference quand vous</span><span class="sxs-lookup"><span data-stu-id="e6601-512">\$WhatIfPreference</span></span>

<span data-ttu-id="e6601-513">Détermine si **WhatIf** est activé automatiquement pour chaque commande qui le prend en charge.</span><span class="sxs-lookup"><span data-stu-id="e6601-513">Determines whether **WhatIf** is automatically enabled for every command that supports it.</span></span> <span data-ttu-id="e6601-514">Lorsque **WhatIf** est activé, l’applet de commande signale l’effet attendu de la commande, mais n’exécute pas la commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-514">When **WhatIf** is enabled, the cmdlet reports the expected effect of the command, but doesn't execute the command.</span></span>

<span data-ttu-id="e6601-515">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6601-515">The valid values are as follows:</span></span>

- <span data-ttu-id="e6601-516">**False** (**0**, non activé) : (valeur par défaut) **WhatIf** n’est pas activé automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e6601-516">**False** (**0**, not enabled): (Default) **WhatIf** isn't automatically enabled.</span></span> <span data-ttu-id="e6601-517">Pour l’activer manuellement, utilisez le paramètre **WhatIf** de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e6601-517">To enable it manually, use the cmdlet's **WhatIf** parameter.</span></span>
- <span data-ttu-id="e6601-518">**True** (**1**, activé) : **WhatIf** est activé automatiquement sur toute commande qui le prend en charge.</span><span class="sxs-lookup"><span data-stu-id="e6601-518">**True** (**1**, enabled): **WhatIf** is automatically enabled on any command that supports it.</span></span> <span data-ttu-id="e6601-519">Les utilisateurs peuvent utiliser le paramètre **WhatIf** avec la valeur **false** pour le désactiver manuellement, par exemple `-WhatIf:$false` .</span><span class="sxs-lookup"><span data-stu-id="e6601-519">Users can use the **WhatIf** parameter with a value of **False** to disable it manually, such as `-WhatIf:$false`.</span></span>

#### <a name="examples"></a><span data-ttu-id="e6601-520">Exemples</span><span class="sxs-lookup"><span data-stu-id="e6601-520">Examples</span></span>

<span data-ttu-id="e6601-521">Ces exemples illustrent l’effet des différentes valeurs de `$WhatIfPreference` .</span><span class="sxs-lookup"><span data-stu-id="e6601-521">These examples show the effect of the different values of `$WhatIfPreference`.</span></span>
<span data-ttu-id="e6601-522">Ils montrent comment utiliser le paramètre **WhatIf** pour remplacer la valeur de préférence pour une commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="e6601-522">They show how to use the **WhatIf** parameter to override the preference value for a specific command.</span></span>

<span data-ttu-id="e6601-523">Cet exemple montre l’effet de la `$WhatIfPreference` variable définie sur la valeur par défaut, **false**.</span><span class="sxs-lookup"><span data-stu-id="e6601-523">This example shows the effect of the `$WhatIfPreference` variable set to the default value, **False**.</span></span> <span data-ttu-id="e6601-524">Utilisez `Get-ChildItem` pour vérifier que le fichier existe.</span><span class="sxs-lookup"><span data-stu-id="e6601-524">Use `Get-ChildItem` to verify that the file exists.</span></span>
<span data-ttu-id="e6601-525">`Remove-Item` supprime le fichier.</span><span class="sxs-lookup"><span data-stu-id="e6601-525">`Remove-Item` deletes the file.</span></span> <span data-ttu-id="e6601-526">Une fois le fichier supprimé, vous pouvez vérifier la suppression avec `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="e6601-526">After the file is deleted, you can verify the deletion with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

<span data-ttu-id="e6601-527">Cet exemple montre l’effet de l’utilisation du paramètre **WhatIf** lorsque la valeur de `$WhatIfPreference` est **false**.</span><span class="sxs-lookup"><span data-stu-id="e6601-527">This example shows the effect of using the **WhatIf** parameter when the value of `$WhatIfPreference` is **False**.</span></span>

<span data-ttu-id="e6601-528">Vérifiez que le fichier existe.</span><span class="sxs-lookup"><span data-stu-id="e6601-528">Verify that the file exists.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="e6601-529">Utilisez le paramètre **WhatIf** pour déterminer le résultat de la tentative de suppression du fichier.</span><span class="sxs-lookup"><span data-stu-id="e6601-529">Use the **WhatIf** parameter to determine the result of attempting to delete the file.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

<span data-ttu-id="e6601-530">Vérifiez que le fichier n’a pas été supprimé.</span><span class="sxs-lookup"><span data-stu-id="e6601-530">Verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="e6601-531">Cet exemple montre l’effet de la `$WhatIfPreference` variable définie sur la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="e6601-531">This example shows the effect of the `$WhatIfPreference` variable set to the value, **True**.</span></span> <span data-ttu-id="e6601-532">Lorsque vous utilisez `Remove-Item` pour supprimer un fichier, le chemin d’accès du fichier est affiché, mais le fichier n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="e6601-532">When you use `Remove-Item` to delete a file, the file's path is displayed, but the file isn't deleted.</span></span>

<span data-ttu-id="e6601-533">Tentative de suppression d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="e6601-533">Attempt to delete a file.</span></span> <span data-ttu-id="e6601-534">Un message s’affiche à propos de ce qui se passe si `Remove-Item` a été exécuté, mais le fichier n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="e6601-534">A message is displayed about what would happen if `Remove-Item` was run, but the file isn't deleted.</span></span>

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

<span data-ttu-id="e6601-535">Utilisez `Get-ChildItem` pour vérifier que le fichier n’a pas été supprimé.</span><span class="sxs-lookup"><span data-stu-id="e6601-535">Use `Get-ChildItem` to verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="e6601-536">Cet exemple montre comment supprimer un fichier lorsque la valeur de `$WhatIfPreference` est **true**.</span><span class="sxs-lookup"><span data-stu-id="e6601-536">This example shows how to delete a file when the value of `$WhatIfPreference` is **True**.</span></span> <span data-ttu-id="e6601-537">Elle utilise le paramètre **WhatIf** avec la valeur `$false` .</span><span class="sxs-lookup"><span data-stu-id="e6601-537">It uses the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="e6601-538">Utilisez `Get-ChildItem` pour vérifier que le fichier a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="e6601-538">Use `Get-ChildItem` to verify the file was deleted.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

<span data-ttu-id="e6601-539">Voici quelques exemples de l’applet de commande `Get-Process` qui ne prend pas en charge **WhatIf** et `Stop-Process` qui prend en charge **WhatIf**.</span><span class="sxs-lookup"><span data-stu-id="e6601-539">The following are examples of the `Get-Process` cmdlet that doesn't support **WhatIf** and `Stop-Process` that does support **WhatIf**.</span></span> <span data-ttu-id="e6601-540">La `$WhatIfPreference` valeur de la variable est **true**.</span><span class="sxs-lookup"><span data-stu-id="e6601-540">The `$WhatIfPreference` variable's value is **True**.</span></span>

<span data-ttu-id="e6601-541">`Get-Process` ne prend pas en charge **WhatIf**.</span><span class="sxs-lookup"><span data-stu-id="e6601-541">`Get-Process` doesn't support **WhatIf**.</span></span> <span data-ttu-id="e6601-542">Lorsque la commande est exécutée, elle affiche le processus **WINWORD** .</span><span class="sxs-lookup"><span data-stu-id="e6601-542">When the command is executed, it displays the **Winword** process.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

<span data-ttu-id="e6601-543">`Stop-Process` prend en charge **WhatIf**.</span><span class="sxs-lookup"><span data-stu-id="e6601-543">`Stop-Process` does support **WhatIf**.</span></span> <span data-ttu-id="e6601-544">Le processus **WINWORD** n’est pas arrêté.</span><span class="sxs-lookup"><span data-stu-id="e6601-544">The **Winword** process isn't stopped.</span></span>

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

<span data-ttu-id="e6601-545">Vous pouvez remplacer le comportement `Stop-Process` **WhatIf** en utilisant le paramètre **WhatIf** avec la valeur `$false` .</span><span class="sxs-lookup"><span data-stu-id="e6601-545">You can override the `Stop-Process` **WhatIf** behavior by using the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="e6601-546">Le processus **WINWORD** est arrêté.</span><span class="sxs-lookup"><span data-stu-id="e6601-546">The **Winword** process is stopped.</span></span>

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

<span data-ttu-id="e6601-547">Pour vérifier que le processus **WINWORD** a été arrêté, utilisez `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="e6601-547">To verify that the **Winword** process was stopped, use `Get-Process`.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a><span data-ttu-id="e6601-548">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6601-548">See also</span></span>

[<span data-ttu-id="e6601-549">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="e6601-549">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="e6601-550">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e6601-550">about_CommonParameters</span></span>](about_CommonParameters.md)

[<span data-ttu-id="e6601-551">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="e6601-551">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="e6601-552">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="e6601-552">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="e6601-553">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e6601-553">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="e6601-554">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="e6601-554">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="e6601-555">about_Variables</span><span class="sxs-lookup"><span data-stu-id="e6601-555">about_Variables</span></span>](about_Variables.md)

