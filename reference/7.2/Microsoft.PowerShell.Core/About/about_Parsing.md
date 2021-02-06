---
description: Décrit comment PowerShell analyse les commandes.
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: a5ce30b2ad9aff7dd8b54e7a62937013a61cd278
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603494"
---
# <a name="about-parsing"></a><span data-ttu-id="7edd0-103">À propos de l’analyse</span><span class="sxs-lookup"><span data-stu-id="7edd0-103">About Parsing</span></span>

## <a name="short-description"></a><span data-ttu-id="7edd0-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="7edd0-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="7edd0-105">Décrit comment PowerShell analyse les commandes.</span><span class="sxs-lookup"><span data-stu-id="7edd0-105">Describes how PowerShell parses commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="7edd0-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="7edd0-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="7edd0-107">Lorsque vous entrez une commande à l’invite de commandes, PowerShell divise le texte de la commande en une série de segments appelés _jetons_ , puis détermine comment interpréter chaque jeton.</span><span class="sxs-lookup"><span data-stu-id="7edd0-107">When you enter a command at the command prompt, PowerShell breaks the command text into a series of segments called _tokens_ and then determines how to interpret each token.</span></span>

<span data-ttu-id="7edd0-108">Par exemple, si vous tapez :</span><span class="sxs-lookup"><span data-stu-id="7edd0-108">For example, if you type:</span></span>

```powershell
Write-Host book
```

<span data-ttu-id="7edd0-109">PowerShell divise la commande en deux jetons, `Write-Host` et `book` , et interprète chaque jeton indépendamment à l’aide de l’un des deux modes d’analyse principaux : le mode expression et le mode argument.</span><span class="sxs-lookup"><span data-stu-id="7edd0-109">PowerShell breaks the command into two tokens, `Write-Host` and `book`, and interprets each token independently using one of two major parsing modes: expression mode and argument mode.</span></span>

> [!NOTE]
> <span data-ttu-id="7edd0-110">Comme PowerShell analyse l’entrée de commande, il tente de résoudre les noms de commande en applets de commande ou exécutables natifs.</span><span class="sxs-lookup"><span data-stu-id="7edd0-110">As PowerShell parses command input it tries to resolve the command names to cmdlets or native executables.</span></span> <span data-ttu-id="7edd0-111">Si un nom de commande n’a pas de correspondance exacte, PowerShell ajoute `Get-` à la commande en tant que verbe par défaut.</span><span class="sxs-lookup"><span data-stu-id="7edd0-111">If a command name does not have an exact match, PowerShell prepends `Get-` to the command as a default verb.</span></span> <span data-ttu-id="7edd0-112">Par exemple, PowerShell est analysé `Process` comme `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="7edd0-112">For example, PowerShell parses `Process` as `Get-Process`.</span></span> <span data-ttu-id="7edd0-113">Il n’est pas recommandé d’utiliser cette fonctionnalité pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="7edd0-113">It's not recommended to use this feature for the following reasons:</span></span>
>
> - <span data-ttu-id="7edd0-114">C’est inefficace.</span><span class="sxs-lookup"><span data-stu-id="7edd0-114">It's inefficient.</span></span> <span data-ttu-id="7edd0-115">PowerShell effectue une recherche à plusieurs moments.</span><span class="sxs-lookup"><span data-stu-id="7edd0-115">This causes PowerShell to search multiple times.</span></span>
> - <span data-ttu-id="7edd0-116">Les programmes externes portant le même nom sont résolus en premier, ce qui signifie que vous ne pouvez pas exécuter l’applet de commande prévue.</span><span class="sxs-lookup"><span data-stu-id="7edd0-116">External programs with the same name are resolved first, so you may not execute intended cmdlet.</span></span>
> - <span data-ttu-id="7edd0-117">`Get-Help` et `Get-Command` ne reconnaissent pas les noms sans verbe.</span><span class="sxs-lookup"><span data-stu-id="7edd0-117">`Get-Help` and `Get-Command` don't recognize verb-less names.</span></span>

### <a name="expression-mode"></a><span data-ttu-id="7edd0-118">Mode expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-118">Expression mode</span></span>

<span data-ttu-id="7edd0-119">Le mode expression est conçu pour combiner des expressions, requis pour la manipulation de valeurs dans un langage de script.</span><span class="sxs-lookup"><span data-stu-id="7edd0-119">Expression mode is intended for combining expressions, required for value manipulation in a scripting language.</span></span> <span data-ttu-id="7edd0-120">Les expressions sont des représentations de valeurs dans la syntaxe PowerShell et peuvent être simples ou composites, par exemple :</span><span class="sxs-lookup"><span data-stu-id="7edd0-120">Expressions are representations of values in PowerShell syntax, and can be simple or composite, for example:</span></span>

<span data-ttu-id="7edd0-121">Les expressions littérales sont des représentations directes de leurs valeurs :</span><span class="sxs-lookup"><span data-stu-id="7edd0-121">Literal expressions are direct representations of their values:</span></span> 

```powershell
'hello', 32
```

<span data-ttu-id="7edd0-122">Les expressions de variable comportent la valeur de la variable qu’elles référencent :</span><span class="sxs-lookup"><span data-stu-id="7edd0-122">Variable expressions carry the value of the variable they reference:</span></span> 

```powershell
$x, $script:path
```
<span data-ttu-id="7edd0-123">Les opérateurs combinent d’autres expressions à des fins d’évaluation :</span><span class="sxs-lookup"><span data-stu-id="7edd0-123">Operators combine other expressions for evaluation:</span></span> 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- <span data-ttu-id="7edd0-124">Les _littéraux de chaîne de caractères_ doivent être placés entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="7edd0-124">_Character string literals_ must be contained in quotation marks.</span></span>
- <span data-ttu-id="7edd0-125">Les _nombres_ sont traités comme des valeurs numériques plutôt que comme une série de caractères (à moins d’être placés dans une séquence d’échappement).</span><span class="sxs-lookup"><span data-stu-id="7edd0-125">_Numbers_ are treated as numerical values rather than as a series of characters (unless escaped).</span></span>
- <span data-ttu-id="7edd0-126">Les _opérateurs_, y compris les opérateurs unaires tels que et `-` et les `-not` opérateurs binaires comme `+` et `-gt` , sont interprétés comme des opérateurs et appliquent leurs opérations respectives sur leurs arguments (opérandes).</span><span class="sxs-lookup"><span data-stu-id="7edd0-126">_Operators_, including unary operators like `-` and `-not` and binary operators like `+` and `-gt`, are interpreted as operators and apply their respective operations on their arguments (operands).</span></span>
- <span data-ttu-id="7edd0-127">Les _expressions d’attribut et de conversion_ sont analysées en tant qu’expressions et appliquées à des expressions subordonnées, par exemple `[int] '7'` .</span><span class="sxs-lookup"><span data-stu-id="7edd0-127">_Attribute and conversion expressions_ are parsed as expressions and applied to subordinate expressions, e.g. `[int] '7'`.</span></span>
- <span data-ttu-id="7edd0-128">Les _références de variable_ sont évaluées en fonction de leurs valeurs, mais la _projection_ (c’est-à-dire le collage de jeux de paramètres préremplis) est interdite et provoque une erreur d’analyse.</span><span class="sxs-lookup"><span data-stu-id="7edd0-128">_Variable references_ are evaluated to their values but _splatting_ (i.e. pasting prefilled parameter sets) is forbidden and causes a parser error.</span></span>
- <span data-ttu-id="7edd0-129">Tout autre objet sera traité comme une commande à appeler.</span><span class="sxs-lookup"><span data-stu-id="7edd0-129">Anything else will be treated as a command to be invoked.</span></span>

### <a name="argument-mode"></a><span data-ttu-id="7edd0-130">Mode d’argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-130">Argument mode</span></span>

<span data-ttu-id="7edd0-131">Lors de l’analyse, PowerShell cherche d’abord à interpréter l’entrée en tant qu’expression.</span><span class="sxs-lookup"><span data-stu-id="7edd0-131">When parsing, PowerShell first looks to interpret input as an expression.</span></span> <span data-ttu-id="7edd0-132">Mais lorsqu’un appel de commande est rencontré, l’analyse continue en mode argument.</span><span class="sxs-lookup"><span data-stu-id="7edd0-132">But when a command invocation is encountered, parsing continues in argument mode.</span></span>

<span data-ttu-id="7edd0-133">Le mode d’argument est conçu pour l’analyse des arguments et des paramètres pour les commandes dans un environnement de Shell.</span><span class="sxs-lookup"><span data-stu-id="7edd0-133">Argument mode is designed for parsing arguments and parameters for commands in a shell environment.</span></span> <span data-ttu-id="7edd0-134">Toute entrée est traitée comme une chaîne développable, sauf si elle utilise l’une des syntaxes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7edd0-134">All input is treated as an expandable string unless it uses one of the following syntaxes:</span></span>

- <span data-ttu-id="7edd0-135">Le signe dollar ( `$` ) commence une référence variable (uniquement si elle est suivie d’un nom de variable valide, sinon elle est interprétée comme faisant partie de la chaîne développable).</span><span class="sxs-lookup"><span data-stu-id="7edd0-135">Dollar sign (`$`) begins a variable reference (only if it is followed by a valid variable name, otherwise it is interpreted as part of the expandable string).</span></span>
- <span data-ttu-id="7edd0-136">Les guillemets ( `'` et `"` ) commencent les valeurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="7edd0-136">Quotation marks (`'` and `"`) begin string values</span></span>
- <span data-ttu-id="7edd0-137">Les parenthèses (et) délimitent `(` les `)` nouvelles expressions.</span><span class="sxs-lookup"><span data-stu-id="7edd0-137">Parentheses (`(` and `)`) demarcate new expressions.</span></span>
- <span data-ttu-id="7edd0-138">L’opérateur de sous-expression ( `$(` ...) délimite les `)` expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="7edd0-138">Subexpression operator (`$(`…`)`) demarcates embedded expressions.</span></span>
- <span data-ttu-id="7edd0-139">`{`Les `}` nouveaux blocs de script sont délimitées par des accolades (et).</span><span class="sxs-lookup"><span data-stu-id="7edd0-139">Braces (`{` and `}`) demarcate new script blocks.</span></span>
- <span data-ttu-id="7edd0-140">La fonction initiale arobase ( `@` ) commence par les syntaxes d’expressions telles que la projection ( `@args` ), les tableaux ( `@(1,2,3)` ) et les tables de hachage ( `@{a=1;b=2}` ).</span><span class="sxs-lookup"><span data-stu-id="7edd0-140">Initial at sign (`@`) begins expression syntaxes such as splatting (`@args`), arrays (`@(1,2,3)`) and hash tables (`@{a=1;b=2}`).</span></span>
- <span data-ttu-id="7edd0-141">Les virgules ( `,` ) présentent des listes passées en tant que tableaux, sauf lorsque la commande à appeler est une application native, auquel cas elles sont interprétées comme faisant partie de la chaîne développable.</span><span class="sxs-lookup"><span data-stu-id="7edd0-141">Commas (`,`) introduce lists passed as arrays, except when the command to be called is a native application, in which case they are interpreted as part of the expandable string.</span></span> <span data-ttu-id="7edd0-142">Les virgules initiales, consécutives ou de fin ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="7edd0-142">Initial, consecutive or trailing commas are not supported.</span></span>

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="7edd0-143">Les valeurs des expressions incorporées sont converties en chaînes.</span><span class="sxs-lookup"><span data-stu-id="7edd0-143">Values of embedded expressions are converted to strings.</span></span>

<span data-ttu-id="7edd0-144">Le tableau suivant fournit plusieurs exemples de valeurs traitées en mode expression et en mode argument, ainsi que l’évaluation de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="7edd0-144">The following table provides several examples of values processed in expression mode and argument mode and the evaluation of those values.</span></span> <span data-ttu-id="7edd0-145">Nous supposons que la valeur de la variable `a` est `4` .</span><span class="sxs-lookup"><span data-stu-id="7edd0-145">We assume that the value of the variable `a` is `4`.</span></span>

|       <span data-ttu-id="7edd0-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="7edd0-146">Example</span></span>        |    <span data-ttu-id="7edd0-147">Mode</span><span class="sxs-lookup"><span data-stu-id="7edd0-147">Mode</span></span>    |      <span data-ttu-id="7edd0-148">Résultats</span><span class="sxs-lookup"><span data-stu-id="7edd0-148">Result</span></span>       |
| -------------------- | ---------- | ----------------- |
| `2`                  | <span data-ttu-id="7edd0-149">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-149">Expression</span></span> | <span data-ttu-id="7edd0-150">2 (entier)</span><span class="sxs-lookup"><span data-stu-id="7edd0-150">2 (integer)</span></span>       |
| `` `2``              | <span data-ttu-id="7edd0-151">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-151">Expression</span></span> | <span data-ttu-id="7edd0-152">"2" (commande)</span><span class="sxs-lookup"><span data-stu-id="7edd0-152">"2" (command)</span></span>     |
| `echo 2`             | <span data-ttu-id="7edd0-153">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-153">Expression</span></span> | <span data-ttu-id="7edd0-154">2 (entier)</span><span class="sxs-lookup"><span data-stu-id="7edd0-154">2 (integer)</span></span>       |
| `2+2`                | <span data-ttu-id="7edd0-155">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-155">Expression</span></span> | <span data-ttu-id="7edd0-156">4 (entier)</span><span class="sxs-lookup"><span data-stu-id="7edd0-156">4 (integer)</span></span>       |
| `echo 2+2`           | <span data-ttu-id="7edd0-157">Argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-157">Argument</span></span>   | <span data-ttu-id="7edd0-158">"2 + 2" (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-158">"2+2" (string)</span></span>    |
| `echo(2+2)`          | <span data-ttu-id="7edd0-159">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-159">Expression</span></span> | <span data-ttu-id="7edd0-160">4 (entier)</span><span class="sxs-lookup"><span data-stu-id="7edd0-160">4 (integer)</span></span>       |
| `$a`                 | <span data-ttu-id="7edd0-161">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-161">Expression</span></span> | <span data-ttu-id="7edd0-162">4 (entier)</span><span class="sxs-lookup"><span data-stu-id="7edd0-162">4 (integer)</span></span>       |
| `echo $a`            | <span data-ttu-id="7edd0-163">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-163">Expression</span></span> | <span data-ttu-id="7edd0-164">4 (entier)</span><span class="sxs-lookup"><span data-stu-id="7edd0-164">4 (integer)</span></span>       |
| `$a+2`               | <span data-ttu-id="7edd0-165">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-165">Expression</span></span> | <span data-ttu-id="7edd0-166">6 (entier)</span><span class="sxs-lookup"><span data-stu-id="7edd0-166">6 (integer)</span></span>       |
| `echo $a+2`          | <span data-ttu-id="7edd0-167">Argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-167">Argument</span></span>   | <span data-ttu-id="7edd0-168">4 + 2 (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-168">4+2 (string)</span></span>      |
| `$-`                 | <span data-ttu-id="7edd0-169">Argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-169">Argument</span></span>   | <span data-ttu-id="7edd0-170">"$-" (commande)</span><span class="sxs-lookup"><span data-stu-id="7edd0-170">"$-" (command)</span></span>    |
| `echo $-`            | <span data-ttu-id="7edd0-171">Argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-171">Argument</span></span>   | <span data-ttu-id="7edd0-172">"$-" (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-172">"$-" (string)</span></span>     |
| `a$a`                | <span data-ttu-id="7edd0-173">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-173">Expression</span></span> | <span data-ttu-id="7edd0-174">« a $ a » (commande)</span><span class="sxs-lookup"><span data-stu-id="7edd0-174">"a$a" (command)</span></span>   |
| `echo a$a`           | <span data-ttu-id="7edd0-175">Argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-175">Argument</span></span>   | <span data-ttu-id="7edd0-176">« A4 » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-176">"a4" (string)</span></span>     |
| `a'$a'`              | <span data-ttu-id="7edd0-177">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-177">Expression</span></span> | <span data-ttu-id="7edd0-178">« a $ a » (commande)</span><span class="sxs-lookup"><span data-stu-id="7edd0-178">"a$a" (command)</span></span>   |
| `echo a'$a'`         | <span data-ttu-id="7edd0-179">Argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-179">Argument</span></span>   | <span data-ttu-id="7edd0-180">« a $ a » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-180">"a$a" (string)</span></span>    |
| `a"$a"`              | <span data-ttu-id="7edd0-181">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-181">Expression</span></span> | <span data-ttu-id="7edd0-182">« a $ a » (commande)</span><span class="sxs-lookup"><span data-stu-id="7edd0-182">"a$a" (command)</span></span>   |
| `echo a"$a"`         | <span data-ttu-id="7edd0-183">Argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-183">Argument</span></span>   | <span data-ttu-id="7edd0-184">« A4 » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-184">"a4" (string)</span></span>     |
| `a$(2)`              | <span data-ttu-id="7edd0-185">Expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-185">Expression</span></span> | <span data-ttu-id="7edd0-186">« a $ (2) » (commande)</span><span class="sxs-lookup"><span data-stu-id="7edd0-186">"a$(2)" (command)</span></span> |
| `echo a$(2)`         | <span data-ttu-id="7edd0-187">Argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-187">Argument</span></span>   | <span data-ttu-id="7edd0-188">« a2 » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-188">"a2" (string)</span></span>     |

<span data-ttu-id="7edd0-189">Chaque jeton peut être interprété comme un type d’objet, tel qu’une valeur booléenne ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="7edd0-189">Every token can be interpreted as some kind of object type, such as Boolean or string.</span></span> <span data-ttu-id="7edd0-190">PowerShell tente de déterminer le type de l’objet à partir de l’expression.</span><span class="sxs-lookup"><span data-stu-id="7edd0-190">PowerShell attempts to determine the object type from the expression.</span></span>
<span data-ttu-id="7edd0-191">Le type d’objet dépend du type de paramètre attendu par une commande et de la manière dont PowerShell sait comment convertir l’argument en type correct.</span><span class="sxs-lookup"><span data-stu-id="7edd0-191">The object type depends on the type of parameter a command expects and on whether PowerShell knows how to convert the argument to the correct type.</span></span> <span data-ttu-id="7edd0-192">Le tableau suivant présente plusieurs exemples des types affectés aux valeurs retournées par les expressions.</span><span class="sxs-lookup"><span data-stu-id="7edd0-192">The following table shows several examples of the types assigned to values returned by the expressions.</span></span>

|       <span data-ttu-id="7edd0-193">Exemple</span><span class="sxs-lookup"><span data-stu-id="7edd0-193">Example</span></span>          |    <span data-ttu-id="7edd0-194">Mode</span><span class="sxs-lookup"><span data-stu-id="7edd0-194">Mode</span></span>    |     <span data-ttu-id="7edd0-195">Résultats</span><span class="sxs-lookup"><span data-stu-id="7edd0-195">Result</span></span>      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | <span data-ttu-id="7edd0-196">argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-196">argument</span></span>   | <span data-ttu-id="7edd0-197">«  ! 1 » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-197">"!1" (string)</span></span>   |
| `Write-Output (!1)`    | <span data-ttu-id="7edd0-198">expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-198">expression</span></span> | <span data-ttu-id="7edd0-199">False (booléen)</span><span class="sxs-lookup"><span data-stu-id="7edd0-199">False (Boolean)</span></span> |
| `Write-Output (2)`     | <span data-ttu-id="7edd0-200">expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-200">expression</span></span> | <span data-ttu-id="7edd0-201">2 (entier)</span><span class="sxs-lookup"><span data-stu-id="7edd0-201">2 (integer)</span></span>     |
| `Set-Variable AB A,B`  | <span data-ttu-id="7edd0-202">argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-202">argument</span></span>   | <span data-ttu-id="7edd0-203">'A', 'B' (tableau)</span><span class="sxs-lookup"><span data-stu-id="7edd0-203">'A','B' (array)</span></span> |
| `CMD /CECHO A,B`       | <span data-ttu-id="7edd0-204">argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-204">argument</span></span>   | <span data-ttu-id="7edd0-205">'A, B' (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-205">'A,B' (string)</span></span>  |
| `CMD /CECHO $AB`       | <span data-ttu-id="7edd0-206">expression</span><span class="sxs-lookup"><span data-stu-id="7edd0-206">expression</span></span> | <span data-ttu-id="7edd0-207">'A', 'B' (tableau)</span><span class="sxs-lookup"><span data-stu-id="7edd0-207">'A','B' (array)</span></span> |
| `CMD /CECHO :$AB`      | <span data-ttu-id="7edd0-208">argument</span><span class="sxs-lookup"><span data-stu-id="7edd0-208">argument</span></span>   | <span data-ttu-id="7edd0-209">' : A B' (chaîne)</span><span class="sxs-lookup"><span data-stu-id="7edd0-209">':A B' (string)</span></span> |

<span data-ttu-id="7edd0-210">Le symbole d’analyse d’arrêt ( `--%` ), introduit dans powershell 3,0, indique à PowerShell de s’abstenir d’interpréter l’entrée comme des commandes ou des expressions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7edd0-210">The stop-parsing symbol (`--%`), introduced in PowerShell 3.0, directs PowerShell to refrain from interpreting input as PowerShell commands or expressions.</span></span>

<span data-ttu-id="7edd0-211">Quand vous appelez un programme exécutable dans PowerShell, placez le symbole d’analyse des arrêts avant les arguments du programme.</span><span class="sxs-lookup"><span data-stu-id="7edd0-211">When calling an executable program in PowerShell, place the stop-parsing symbol before the program arguments.</span></span> <span data-ttu-id="7edd0-212">Cette technique est beaucoup plus facile que d’utiliser des caractères d’échappement pour éviter une mauvaise interprétation.</span><span class="sxs-lookup"><span data-stu-id="7edd0-212">This technique is much easier than using escape characters to prevent misinterpretation.</span></span>

<span data-ttu-id="7edd0-213">Lorsqu’il rencontre un symbole d’analyse d’arrêt, PowerShell traite les caractères restants de la ligne comme un littéral.</span><span class="sxs-lookup"><span data-stu-id="7edd0-213">When it encounters a stop-parsing symbol, PowerShell treats the remaining characters in the line as a literal.</span></span> <span data-ttu-id="7edd0-214">La seule interprétation qu’il effectue est la substitution de valeurs pour les variables d’environnement qui utilisent la notation Windows standard, telle que `%USERPROFILE%` .</span><span class="sxs-lookup"><span data-stu-id="7edd0-214">The only interpretation it performs is to substitute values for environment variables that use standard Windows notation, such as `%USERPROFILE%`.</span></span>

<span data-ttu-id="7edd0-215">Le symbole d’analyse Stop est effectif uniquement jusqu’au saut de ligne ou au caractère de pipeline suivant.</span><span class="sxs-lookup"><span data-stu-id="7edd0-215">The stop-parsing symbol is effective only until the next newline or pipeline character.</span></span> <span data-ttu-id="7edd0-216">Vous ne pouvez pas utiliser un caractère de continuation ( `` ` `` ) pour étendre son effet ou utiliser un délimiteur de commande ( `;` ) pour terminer son effet.</span><span class="sxs-lookup"><span data-stu-id="7edd0-216">You cannot use a continuation character (`` ` ``) to extend its effect or use a command delimiter (`;`) to terminate its effect.</span></span>

<span data-ttu-id="7edd0-217">Par exemple, la commande suivante appelle le programme **icacls** .</span><span class="sxs-lookup"><span data-stu-id="7edd0-217">For example, the following command calls the **Icacls** program.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="7edd0-218">Pour exécuter cette commande dans PowerShell 2,0, vous devez utiliser des caractères d’échappement pour empêcher PowerShell d’interpréter les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7edd0-218">To run this command in PowerShell 2.0, you must use escape characters to prevent PowerShell from misinterpreting the parentheses.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

<span data-ttu-id="7edd0-219">À compter de PowerShell 3,0, vous pouvez utiliser le symbole d’analyse stop.</span><span class="sxs-lookup"><span data-stu-id="7edd0-219">Beginning in PowerShell 3.0, you can use the stop-parsing symbol.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="7edd0-220">PowerShell envoie la chaîne de commande suivante au programme **icacls** :</span><span class="sxs-lookup"><span data-stu-id="7edd0-220">PowerShell sends the following command string to the **Icacls** program:</span></span>

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> <span data-ttu-id="7edd0-221">Symbole d’analyse Stop uniquement destiné à être utilisé sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="7edd0-221">The stop-parsing symbol only intended for use on Windows platforms.</span></span>

## <a name="see-also"></a><span data-ttu-id="7edd0-222">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="7edd0-222">SEE ALSO</span></span>

[<span data-ttu-id="7edd0-223">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="7edd0-223">about_Command_Syntax</span></span>](about_Command_Syntax.md)
