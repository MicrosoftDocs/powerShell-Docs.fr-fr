---
description: Décrit comment PowerShell analyse les commandes.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: 7f68a1f29ecb6a4562ae9f9a024365a2b1744a79
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207461"
---
# <a name="about-parsing"></a><span data-ttu-id="2fb8d-104">À propos de l’analyse</span><span class="sxs-lookup"><span data-stu-id="2fb8d-104">About Parsing</span></span>

## <a name="short-description"></a><span data-ttu-id="2fb8d-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="2fb8d-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2fb8d-106">Décrit comment PowerShell analyse les commandes.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-106">Describes how PowerShell parses commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="2fb8d-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="2fb8d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="2fb8d-108">Lorsque vous entrez une commande à l’invite de commandes, PowerShell divise le texte de la commande en une série de segments appelés _jetons_ , puis détermine comment interpréter chaque jeton.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-108">When you enter a command at the command prompt, PowerShell breaks the command text into a series of segments called _tokens_ and then determines how to interpret each token.</span></span>

<span data-ttu-id="2fb8d-109">Par exemple, si vous tapez :</span><span class="sxs-lookup"><span data-stu-id="2fb8d-109">For example, if you type:</span></span>

```powershell
Write-Host book
```

<span data-ttu-id="2fb8d-110">PowerShell divise la commande en deux jetons, `Write-Host` et `book` , et interprète chaque jeton indépendamment à l’aide de l’un des deux modes d’analyse principaux : le mode expression et le mode argument.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-110">PowerShell breaks the command into two tokens, `Write-Host` and `book`, and interprets each token independently using one of two major parsing modes: expression mode and argument mode.</span></span>

> [!NOTE]
> <span data-ttu-id="2fb8d-111">Comme PowerShell analyse l’entrée de commande, il tente de résoudre les noms de commande en applets de commande ou exécutables natifs.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-111">As PowerShell parses command input it tries to resolve the command names to cmdlets or native executables.</span></span> <span data-ttu-id="2fb8d-112">Si un nom de commande n’a pas de correspondance exacte, PowerShell ajoute `Get-` à la commande en tant que verbe par défaut.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-112">If a command name does not have an exact match, PowerShell prepends `Get-` to the command as a default verb.</span></span> <span data-ttu-id="2fb8d-113">Par exemple, PowerShell est analysé `Process` comme `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="2fb8d-113">For example, PowerShell parses `Process` as `Get-Process`.</span></span> <span data-ttu-id="2fb8d-114">Il n’est pas recommandé d’utiliser cette fonctionnalité pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="2fb8d-114">It's not recommended to use this feature for the following reasons:</span></span>
>
> - <span data-ttu-id="2fb8d-115">C’est inefficace.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-115">It's inefficient.</span></span> <span data-ttu-id="2fb8d-116">PowerShell effectue une recherche à plusieurs moments.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-116">This causes PowerShell to search multiple times.</span></span>
> - <span data-ttu-id="2fb8d-117">Les programmes externes portant le même nom sont résolus en premier, ce qui signifie que vous ne pouvez pas exécuter l’applet de commande prévue.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-117">External programs with the same name are resolved first, so you may not execute intended cmdlet.</span></span>
> - <span data-ttu-id="2fb8d-118">`Get-Help` et `Get-Command` ne reconnaissent pas les noms sans verbe.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-118">`Get-Help` and `Get-Command` don't recognize verb-less names.</span></span>

### <a name="expression-mode"></a><span data-ttu-id="2fb8d-119">Mode expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-119">Expression mode</span></span>

<span data-ttu-id="2fb8d-120">Le mode expression est conçu pour combiner des expressions, requis pour la manipulation de valeurs dans un langage de script.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-120">Expression mode is intended for combining expressions, required for value manipulation in a scripting language.</span></span> <span data-ttu-id="2fb8d-121">Les expressions sont des représentations de valeurs dans la syntaxe PowerShell et peuvent être simples ou composites, par exemple :</span><span class="sxs-lookup"><span data-stu-id="2fb8d-121">Expressions are representations of values in PowerShell syntax, and can be simple or composite, for example:</span></span>

<span data-ttu-id="2fb8d-122">Les expressions littérales sont des représentations directes de leurs valeurs :</span><span class="sxs-lookup"><span data-stu-id="2fb8d-122">Literal expressions are direct representations of their values:</span></span> 

```powershell
'hello', 32
```

<span data-ttu-id="2fb8d-123">Les expressions de variable comportent la valeur de la variable qu’elles référencent :</span><span class="sxs-lookup"><span data-stu-id="2fb8d-123">Variable expressions carry the value of the variable they reference:</span></span> 

```powershell
$x, $script:path
```
<span data-ttu-id="2fb8d-124">Les opérateurs combinent d’autres expressions à des fins d’évaluation :</span><span class="sxs-lookup"><span data-stu-id="2fb8d-124">Operators combine other expressions for evaluation:</span></span> 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- <span data-ttu-id="2fb8d-125">Les _littéraux de chaîne de caractères_ doivent être placés entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-125">_Character string literals_ must be contained in quotation marks.</span></span>
- <span data-ttu-id="2fb8d-126">Les _nombres_ sont traités comme des valeurs numériques plutôt que comme une série de caractères (à moins d’être placés dans une séquence d’échappement).</span><span class="sxs-lookup"><span data-stu-id="2fb8d-126">_Numbers_ are treated as numerical values rather than as a series of characters (unless escaped).</span></span>
- <span data-ttu-id="2fb8d-127">Les _opérateurs_ , y compris les opérateurs unaires tels que et `-` et les `-not` opérateurs binaires comme `+` et `-gt` , sont interprétés comme des opérateurs et appliquent leurs opérations respectives sur leurs arguments (opérandes).</span><span class="sxs-lookup"><span data-stu-id="2fb8d-127">_Operators_ , including unary operators like `-` and `-not` and binary operators like `+` and `-gt`, are interpreted as operators and apply their respective operations on their arguments (operands).</span></span>
- <span data-ttu-id="2fb8d-128">Les _expressions d’attribut et de conversion_ sont analysées en tant qu’expressions et appliquées à des expressions subordonnées, par exemple `[int] '7'` .</span><span class="sxs-lookup"><span data-stu-id="2fb8d-128">_Attribute and conversion expressions_ are parsed as expressions and applied to subordinate expressions, e.g. `[int] '7'`.</span></span>
- <span data-ttu-id="2fb8d-129">Les _références de variable_ sont évaluées en fonction de leurs valeurs, mais la _projection_ (c’est-à-dire le collage de jeux de paramètres préremplis) est interdite et provoque une erreur d’analyse.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-129">_Variable references_ are evaluated to their values but _splatting_ (i.e. pasting prefilled parameter sets) is forbidden and causes a parser error.</span></span>
- <span data-ttu-id="2fb8d-130">Tout autre objet sera traité comme une commande à appeler.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-130">Anything else will be treated as a command to be invoked.</span></span>

### <a name="argument-mode"></a><span data-ttu-id="2fb8d-131">Mode d’argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-131">Argument mode</span></span>

<span data-ttu-id="2fb8d-132">Lors de l’analyse, PowerShell cherche d’abord à interpréter l’entrée en tant qu’expression.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-132">When parsing, PowerShell first looks to interpret input as an expression.</span></span> <span data-ttu-id="2fb8d-133">Mais lorsqu’un appel de commande est rencontré, l’analyse continue en mode argument.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-133">But when a command invocation is encountered, parsing continues in argument mode.</span></span>

<span data-ttu-id="2fb8d-134">Le mode d’argument est conçu pour l’analyse des arguments et des paramètres pour les commandes dans un environnement de Shell.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-134">Argument mode is designed for parsing arguments and parameters for commands in a shell environment.</span></span> <span data-ttu-id="2fb8d-135">Toute entrée est traitée comme une chaîne développable, sauf si elle utilise l’une des syntaxes suivantes :</span><span class="sxs-lookup"><span data-stu-id="2fb8d-135">All input is treated as an expandable string unless it uses one of the following syntaxes:</span></span>

- <span data-ttu-id="2fb8d-136">Le signe dollar ( `$` ) commence une référence variable (uniquement si elle est suivie d’un nom de variable valide, sinon elle est interprétée comme faisant partie de la chaîne développable).</span><span class="sxs-lookup"><span data-stu-id="2fb8d-136">Dollar sign (`$`) begins a variable reference (only if it is followed by a valid variable name, otherwise it is interpreted as part of the expandable string).</span></span>
- <span data-ttu-id="2fb8d-137">Les guillemets ( `'` et `"` ) commencent les valeurs de chaîne</span><span class="sxs-lookup"><span data-stu-id="2fb8d-137">Quotation marks (`'` and `"`) begin string values</span></span>
- <span data-ttu-id="2fb8d-138">Les parenthèses (et) délimitent `(` les `)` nouvelles expressions.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-138">Parentheses (`(` and `)`) demarcate new expressions.</span></span>
- <span data-ttu-id="2fb8d-139">L’opérateur de sous-expression ( `$(` ...) délimite les `)` expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-139">Subexpression operator (`$(`…`)`) demarcates embedded expressions.</span></span>
- <span data-ttu-id="2fb8d-140">`{`Les `}` nouveaux blocs de script sont délimitées par des accolades (et).</span><span class="sxs-lookup"><span data-stu-id="2fb8d-140">Braces (`{` and `}`) demarcate new script blocks.</span></span>
- <span data-ttu-id="2fb8d-141">La fonction initiale arobase ( `@` ) commence par les syntaxes d’expressions telles que la projection ( `@args` ), les tableaux ( `@(1,2,3)` ) et les tables de hachage ( `@{a=1;b=2}` ).</span><span class="sxs-lookup"><span data-stu-id="2fb8d-141">Initial at sign (`@`) begins expression syntaxes such as splatting (`@args`), arrays (`@(1,2,3)`) and hash tables (`@{a=1;b=2}`).</span></span>
- <span data-ttu-id="2fb8d-142">Les virgules ( `,` ) présentent des listes passées en tant que tableaux, sauf lorsque la commande à appeler est une application native, auquel cas elles sont interprétées comme faisant partie de la chaîne développable.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-142">Commas (`,`) introduce lists passed as arrays, except when the command to be called is a native application, in which case they are interpreted as part of the expandable string.</span></span> <span data-ttu-id="2fb8d-143">Les virgules initiales, consécutives ou de fin ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-143">Initial, consecutive or trailing commas are not supported.</span></span>

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="2fb8d-144">Les valeurs des expressions incorporées sont converties en chaînes.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-144">Values of embedded expressions are converted to strings.</span></span>

<span data-ttu-id="2fb8d-145">Le tableau suivant fournit plusieurs exemples de valeurs traitées en mode expression et en mode argument, ainsi que l’évaluation de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-145">The following table provides several examples of values processed in expression mode and argument mode and the evaluation of those values.</span></span> <span data-ttu-id="2fb8d-146">Nous supposons que la valeur de la variable `a` est `4` .</span><span class="sxs-lookup"><span data-stu-id="2fb8d-146">We assume that the value of the variable `a` is `4`.</span></span>

|       <span data-ttu-id="2fb8d-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="2fb8d-147">Example</span></span>        |    <span data-ttu-id="2fb8d-148">Mode</span><span class="sxs-lookup"><span data-stu-id="2fb8d-148">Mode</span></span>    |      <span data-ttu-id="2fb8d-149">Résultats</span><span class="sxs-lookup"><span data-stu-id="2fb8d-149">Result</span></span>       |
| -------------------- | ---------- | ----------------- |
| `2`                  | <span data-ttu-id="2fb8d-150">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-150">Expression</span></span> | <span data-ttu-id="2fb8d-151">2 (entier)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-151">2 (integer)</span></span>       |
| `` `2``              | <span data-ttu-id="2fb8d-152">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-152">Expression</span></span> | <span data-ttu-id="2fb8d-153">"2" (commande)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-153">"2" (command)</span></span>     |
| `echo 2`             | <span data-ttu-id="2fb8d-154">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-154">Expression</span></span> | <span data-ttu-id="2fb8d-155">2 (entier)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-155">2 (integer)</span></span>       |
| `2+2`                | <span data-ttu-id="2fb8d-156">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-156">Expression</span></span> | <span data-ttu-id="2fb8d-157">4 (entier)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-157">4 (integer)</span></span>       |
| `echo 2+2`           | <span data-ttu-id="2fb8d-158">Argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-158">Argument</span></span>   | <span data-ttu-id="2fb8d-159">"2 + 2" (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-159">"2+2" (string)</span></span>    |
| `echo(2+2)`          | <span data-ttu-id="2fb8d-160">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-160">Expression</span></span> | <span data-ttu-id="2fb8d-161">4 (entier)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-161">4 (integer)</span></span>       |
| `$a`                 | <span data-ttu-id="2fb8d-162">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-162">Expression</span></span> | <span data-ttu-id="2fb8d-163">4 (entier)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-163">4 (integer)</span></span>       |
| `echo $a`            | <span data-ttu-id="2fb8d-164">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-164">Expression</span></span> | <span data-ttu-id="2fb8d-165">4 (entier)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-165">4 (integer)</span></span>       |
| `$a+2`               | <span data-ttu-id="2fb8d-166">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-166">Expression</span></span> | <span data-ttu-id="2fb8d-167">6 (entier)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-167">6 (integer)</span></span>       |
| `echo $a+2`          | <span data-ttu-id="2fb8d-168">Argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-168">Argument</span></span>   | <span data-ttu-id="2fb8d-169">4 + 2 (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-169">4+2 (string)</span></span>      |
| `$-`                 | <span data-ttu-id="2fb8d-170">Argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-170">Argument</span></span>   | <span data-ttu-id="2fb8d-171">"$-" (commande)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-171">"$-" (command)</span></span>    |
| `echo $-`            | <span data-ttu-id="2fb8d-172">Argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-172">Argument</span></span>   | <span data-ttu-id="2fb8d-173">"$-" (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-173">"$-" (string)</span></span>     |
| `a$a`                | <span data-ttu-id="2fb8d-174">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-174">Expression</span></span> | <span data-ttu-id="2fb8d-175">« a $ a » (commande)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-175">"a$a" (command)</span></span>   |
| `echo a$a`           | <span data-ttu-id="2fb8d-176">Argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-176">Argument</span></span>   | <span data-ttu-id="2fb8d-177">« A4 » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-177">"a4" (string)</span></span>     |
| `a'$a'`              | <span data-ttu-id="2fb8d-178">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-178">Expression</span></span> | <span data-ttu-id="2fb8d-179">« a $ a » (commande)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-179">"a$a" (command)</span></span>   |
| `echo a'$a'`         | <span data-ttu-id="2fb8d-180">Argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-180">Argument</span></span>   | <span data-ttu-id="2fb8d-181">« a $ a » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-181">"a$a" (string)</span></span>    |
| `a"$a"`              | <span data-ttu-id="2fb8d-182">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-182">Expression</span></span> | <span data-ttu-id="2fb8d-183">« a $ a » (commande)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-183">"a$a" (command)</span></span>   |
| `echo a"$a"`         | <span data-ttu-id="2fb8d-184">Argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-184">Argument</span></span>   | <span data-ttu-id="2fb8d-185">« A4 » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-185">"a4" (string)</span></span>     |
| `a$(2)`              | <span data-ttu-id="2fb8d-186">Expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-186">Expression</span></span> | <span data-ttu-id="2fb8d-187">« a $ (2) » (commande)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-187">"a$(2)" (command)</span></span> |
| `echo a$(2)`         | <span data-ttu-id="2fb8d-188">Argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-188">Argument</span></span>   | <span data-ttu-id="2fb8d-189">« a2 » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-189">"a2" (string)</span></span>     |

<span data-ttu-id="2fb8d-190">Chaque jeton peut être interprété comme un type d’objet, tel qu’une valeur booléenne ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-190">Every token can be interpreted as some kind of object type, such as Boolean or string.</span></span> <span data-ttu-id="2fb8d-191">PowerShell tente de déterminer le type de l’objet à partir de l’expression.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-191">PowerShell attempts to determine the object type from the expression.</span></span>
<span data-ttu-id="2fb8d-192">Le type d’objet dépend du type de paramètre attendu par une commande et de la manière dont PowerShell sait comment convertir l’argument en type correct.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-192">The object type depends on the type of parameter a command expects and on whether PowerShell knows how to convert the argument to the correct type.</span></span> <span data-ttu-id="2fb8d-193">Le tableau suivant présente plusieurs exemples des types affectés aux valeurs retournées par les expressions.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-193">The following table shows several examples of the types assigned to values returned by the expressions.</span></span>

|       <span data-ttu-id="2fb8d-194">Exemple</span><span class="sxs-lookup"><span data-stu-id="2fb8d-194">Example</span></span>          |    <span data-ttu-id="2fb8d-195">Mode</span><span class="sxs-lookup"><span data-stu-id="2fb8d-195">Mode</span></span>    |     <span data-ttu-id="2fb8d-196">Résultats</span><span class="sxs-lookup"><span data-stu-id="2fb8d-196">Result</span></span>      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | <span data-ttu-id="2fb8d-197">argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-197">argument</span></span>   | <span data-ttu-id="2fb8d-198">«  ! 1 » (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-198">"!1" (string)</span></span>   |
| `Write-Output (!1)`    | <span data-ttu-id="2fb8d-199">expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-199">expression</span></span> | <span data-ttu-id="2fb8d-200">False (booléen)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-200">False (Boolean)</span></span> |
| `Write-Output (2)`     | <span data-ttu-id="2fb8d-201">expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-201">expression</span></span> | <span data-ttu-id="2fb8d-202">2 (entier)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-202">2 (integer)</span></span>     |
| `Set-Variable AB A,B`  | <span data-ttu-id="2fb8d-203">argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-203">argument</span></span>   | <span data-ttu-id="2fb8d-204">'A', 'B' (tableau)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-204">'A','B' (array)</span></span> |
| `CMD /CECHO A,B`       | <span data-ttu-id="2fb8d-205">argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-205">argument</span></span>   | <span data-ttu-id="2fb8d-206">'A, B' (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-206">'A,B' (string)</span></span>  |
| `CMD /CECHO $AB`       | <span data-ttu-id="2fb8d-207">expression</span><span class="sxs-lookup"><span data-stu-id="2fb8d-207">expression</span></span> | <span data-ttu-id="2fb8d-208">'A', 'B' (tableau)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-208">'A','B' (array)</span></span> |
| `CMD /CECHO :$AB`      | <span data-ttu-id="2fb8d-209">argument</span><span class="sxs-lookup"><span data-stu-id="2fb8d-209">argument</span></span>   | <span data-ttu-id="2fb8d-210">' : A B' (chaîne)</span><span class="sxs-lookup"><span data-stu-id="2fb8d-210">':A B' (string)</span></span> |

<span data-ttu-id="2fb8d-211">Le symbole d’analyse d’arrêt ( `--%` ), introduit dans powershell 3,0, indique à PowerShell de s’abstenir d’interpréter l’entrée comme des commandes ou des expressions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-211">The stop-parsing symbol (`--%`), introduced in PowerShell 3.0, directs PowerShell to refrain from interpreting input as PowerShell commands or expressions.</span></span>

<span data-ttu-id="2fb8d-212">Quand vous appelez un programme exécutable dans PowerShell, placez le symbole d’analyse des arrêts avant les arguments du programme.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-212">When calling an executable program in PowerShell, place the stop-parsing symbol before the program arguments.</span></span> <span data-ttu-id="2fb8d-213">Cette technique est beaucoup plus facile que d’utiliser des caractères d’échappement pour éviter une mauvaise interprétation.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-213">This technique is much easier than using escape characters to prevent misinterpretation.</span></span>

<span data-ttu-id="2fb8d-214">Lorsqu’il rencontre un symbole d’analyse d’arrêt, PowerShell traite les caractères restants de la ligne comme un littéral.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-214">When it encounters a stop-parsing symbol, PowerShell treats the remaining characters in the line as a literal.</span></span> <span data-ttu-id="2fb8d-215">La seule interprétation qu’il effectue est la substitution de valeurs pour les variables d’environnement qui utilisent la notation Windows standard, telle que `%USERPROFILE%` .</span><span class="sxs-lookup"><span data-stu-id="2fb8d-215">The only interpretation it performs is to substitute values for environment variables that use standard Windows notation, such as `%USERPROFILE%`.</span></span>

<span data-ttu-id="2fb8d-216">Le symbole d’analyse Stop est effectif uniquement jusqu’au saut de ligne ou au caractère de pipeline suivant.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-216">The stop-parsing symbol is effective only until the next newline or pipeline character.</span></span> <span data-ttu-id="2fb8d-217">Vous ne pouvez pas utiliser un caractère de continuation ( `` ` `` ) pour étendre son effet ou utiliser un délimiteur de commande ( `;` ) pour terminer son effet.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-217">You cannot use a continuation character (`` ` ``) to extend its effect or use a command delimiter (`;`) to terminate its effect.</span></span>

<span data-ttu-id="2fb8d-218">Par exemple, la commande suivante appelle le programme **icacls** .</span><span class="sxs-lookup"><span data-stu-id="2fb8d-218">For example, the following command calls the **Icacls** program.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="2fb8d-219">Pour exécuter cette commande dans PowerShell 2,0, vous devez utiliser des caractères d’échappement pour empêcher PowerShell d’interpréter les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-219">To run this command in PowerShell 2.0, you must use escape characters to prevent PowerShell from misinterpreting the parentheses.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

<span data-ttu-id="2fb8d-220">À compter de PowerShell 3,0, vous pouvez utiliser le symbole d’analyse stop.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-220">Beginning in PowerShell 3.0, you can use the stop-parsing symbol.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="2fb8d-221">PowerShell envoie la chaîne de commande suivante au programme **icacls** :</span><span class="sxs-lookup"><span data-stu-id="2fb8d-221">PowerShell sends the following command string to the **Icacls** program:</span></span>

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> <span data-ttu-id="2fb8d-222">Symbole d’analyse Stop uniquement destiné à être utilisé sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="2fb8d-222">The stop-parsing symbol only intended for use on Windows platforms.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fb8d-223">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="2fb8d-223">SEE ALSO</span></span>

[<span data-ttu-id="2fb8d-224">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="2fb8d-224">about_Command_Syntax</span></span>](about_Command_Syntax.md)
