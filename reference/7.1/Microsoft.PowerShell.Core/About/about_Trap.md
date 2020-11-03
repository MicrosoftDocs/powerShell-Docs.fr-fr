---
description: Décrit un mot clé qui gère une erreur de fin.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: a0e852f63e37bd18e769943f98bca264ab360d3a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207714"
---
# <a name="about-trap"></a><span data-ttu-id="85801-104">À propos de l’interruption</span><span class="sxs-lookup"><span data-stu-id="85801-104">About Trap</span></span>

## <a name="short-description"></a><span data-ttu-id="85801-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="85801-105">Short description</span></span>

<span data-ttu-id="85801-106">Décrit un mot clé qui gère une erreur de fin.</span><span class="sxs-lookup"><span data-stu-id="85801-106">Describes a keyword that handles a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="85801-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="85801-107">Long description</span></span>

<span data-ttu-id="85801-108">Une erreur d’arrêt empêche l’exécution d’une instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-108">A terminating error stops a statement from running.</span></span> <span data-ttu-id="85801-109">Si PowerShell ne gère pas une erreur de fin d’une certaine façon, PowerShell arrête également l’exécution de la fonction ou du script dans le pipeline actuel.</span><span class="sxs-lookup"><span data-stu-id="85801-109">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script in the current pipeline.</span></span> <span data-ttu-id="85801-110">Dans d’autres langages, tels que C#, les erreurs de fin sont connues sous le nom d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="85801-110">In other languages, such as C#, terminating errors are known as exceptions.</span></span>

<span data-ttu-id="85801-111">Le `trap` mot clé spécifie une liste d’instructions à exécuter lorsqu’une erreur d’arrêt se produit.</span><span class="sxs-lookup"><span data-stu-id="85801-111">The `trap` keyword specifies a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="85801-112">`trap` les instructions traitent les erreurs de fin de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="85801-112">`trap` statements handle the terminating errors in the following ways:</span></span>

- <span data-ttu-id="85801-113">Affichez l’erreur après le traitement du `trap` bloc d’instructions et la poursuite de l’exécution du script ou de la fonction contenant `trap` .</span><span class="sxs-lookup"><span data-stu-id="85801-113">Display the error after processing the `trap` statement block and continuing execution of the script or function containing the `trap`.</span></span> <span data-ttu-id="85801-114">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="85801-114">This is the default behavior.</span></span>

- <span data-ttu-id="85801-115">Affichez l’erreur et annulez l’exécution du script ou de la fonction contenant le `trap` à l’aide `break` de dans l' `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-115">Display the error and abort execution of the script or function containing the `trap` using `break` in the `trap` statement.</span></span>

- <span data-ttu-id="85801-116">Interrompez l’erreur, mais poursuivez l’exécution du script ou de la fonction contenant le `trap` en utilisant `continue` dans l' `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-116">Silence the error, but continue execution of the script or function containing the `trap` by using `continue` in the `trap` statement.</span></span>

<span data-ttu-id="85801-117">La liste des instructions de `trap` peut inclure plusieurs conditions ou appels de fonction.</span><span class="sxs-lookup"><span data-stu-id="85801-117">The statement list of the `trap` can include multiple conditions or function calls.</span></span> <span data-ttu-id="85801-118">Un `trap` peut écrire des journaux, des conditions de test ou même exécuter un autre programme.</span><span class="sxs-lookup"><span data-stu-id="85801-118">A `trap` can write logs, test conditions, or even run another program.</span></span>

### <a name="syntax"></a><span data-ttu-id="85801-119">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85801-119">Syntax</span></span>

<span data-ttu-id="85801-120">L' `trap` instruction a la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="85801-120">The `trap` statement has the following syntax:</span></span>

```powershell
trap [[<error type>]] {<statement list>}
```

<span data-ttu-id="85801-121">L' `trap` instruction contient une liste d’instructions à exécuter lorsqu’une erreur se termine.</span><span class="sxs-lookup"><span data-stu-id="85801-121">The `trap` statement includes a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="85801-122">Une `trap` instruction se compose du `trap` mot clé, éventuellement suivi d’une expression de type et du bloc d’instructions contenant la liste des instructions à exécuter lorsqu’une erreur est interceptée.</span><span class="sxs-lookup"><span data-stu-id="85801-122">A `trap` statement consists of the `trap` keyword, optionally followed by a type expression, and the statement block containing the list of statements to run when an error is trapped.</span></span> <span data-ttu-id="85801-123">L’expression de type affine les types d’erreurs `trap` interceptés.</span><span class="sxs-lookup"><span data-stu-id="85801-123">The type expression refines the types of errors the `trap` catches.</span></span>

<span data-ttu-id="85801-124">Un script ou une commande peut avoir plusieurs `trap` instructions.</span><span class="sxs-lookup"><span data-stu-id="85801-124">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="85801-125">`trap` les instructions peuvent apparaître n’importe où dans le script ou la commande.</span><span class="sxs-lookup"><span data-stu-id="85801-125">`trap` statements can appear anywhere in the script or command.</span></span>

### <a name="trapping-all-terminating-errors"></a><span data-ttu-id="85801-126">Récupération de toutes les erreurs de fin</span><span class="sxs-lookup"><span data-stu-id="85801-126">Trapping all terminating errors</span></span>

<span data-ttu-id="85801-127">Lorsqu’une erreur d’arrêt se produit qui n’est pas gérée d’une autre façon dans un script ou une commande, PowerShell recherche une `trap` instruction qui gère l’erreur.</span><span class="sxs-lookup"><span data-stu-id="85801-127">When a terminating error occurs that is not handled in another way in a script or command, PowerShell checks for a `trap` statement that handles the error.</span></span> <span data-ttu-id="85801-128">Si une `trap` instruction est présente, PowerShell continue à exécuter le script ou la commande dans l' `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-128">If a `trap` statement is present, PowerShell continues running the script or command in the `trap` statement.</span></span>

<span data-ttu-id="85801-129">L’exemple suivant est une instruction très simple `trap` :</span><span class="sxs-lookup"><span data-stu-id="85801-129">The following example is a very simple `trap` statement:</span></span>

```powershell
trap {"Error found."}
```

<span data-ttu-id="85801-130">Cette `trap` instruction intercepte toute erreur qui se termine.</span><span class="sxs-lookup"><span data-stu-id="85801-130">This `trap` statement traps any terminating error.</span></span>

<span data-ttu-id="85801-131">Dans l’exemple suivant, la fonction contient une chaîne incompréhensible qui provoque une erreur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="85801-131">In the following example, the function includes a nonsense string that causes a runtime error.</span></span>

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="85801-132">L’exécution de cette fonction retourne ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="85801-132">Running this function returns the following:</span></span>

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="85801-133">L’exemple suivant comprend une `trap` instruction qui affiche l’erreur à l’aide de la `$_` variable automatique :</span><span class="sxs-lookup"><span data-stu-id="85801-133">The following example includes a `trap` statement that displays the error by using the `$_` automatic variable:</span></span>

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="85801-134">L’exécution de cette version de la fonction retourne ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="85801-134">Running this version of the function returns the following:</span></span>

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> <span data-ttu-id="85801-135">`trap` les instructions peuvent être définies n’importe où dans une étendue donnée, mais s’appliquent toujours à toutes les instructions de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="85801-135">`trap` statements may be defined anywhere within a given scope, but always apply to all statements in that scope.</span></span> <span data-ttu-id="85801-136">Lors de l’exécution, `trap` les instructions d’un bloc sont définies avant l’exécution de toute autre instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-136">At runtime, `trap` statements in a block are defined before any other statements are executed.</span></span> <span data-ttu-id="85801-137">En JavaScript, c’est ce qu’on appelle le « [levage](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)».</span><span class="sxs-lookup"><span data-stu-id="85801-137">In JavaScript, this is known as [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting).</span></span> <span data-ttu-id="85801-138">Cela signifie que `trap` les instructions s’appliquent à toutes les instructions de ce bloc, même si l’exécution n’a pas avancé au-delà du point auquel elles sont définies.</span><span class="sxs-lookup"><span data-stu-id="85801-138">This means that `trap` statements apply to all statements in that block even if execution has not advanced past the point at which they are defined.</span></span> <span data-ttu-id="85801-139">Par exemple, la définition d’un `trap` à la fin d’un script et la génération d’une erreur dans la première instruction déclenche toujours cela `trap` .</span><span class="sxs-lookup"><span data-stu-id="85801-139">For example, defining a `trap` at the end of a script and throwing an error in the first statement still triggers that `trap`.</span></span>

### <a name="trapping-specific-errors"></a><span data-ttu-id="85801-140">Interception des erreurs spécifiques</span><span class="sxs-lookup"><span data-stu-id="85801-140">Trapping specific errors</span></span>

<span data-ttu-id="85801-141">Un script ou une commande peut avoir plusieurs `trap` instructions.</span><span class="sxs-lookup"><span data-stu-id="85801-141">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="85801-142">Une `trap` peut être définie pour gérer des erreurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="85801-142">A `trap` can be defined to handle specific errors.</span></span>

<span data-ttu-id="85801-143">L’exemple suivant est une `trap` instruction qui intercepte l’erreur spécifique **CommandNotFoundException** :</span><span class="sxs-lookup"><span data-stu-id="85801-143">The following example is a `trap` statement that traps the specific error **CommandNotFoundException** :</span></span>

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

<span data-ttu-id="85801-144">Lorsqu’une fonction ou un script rencontre une chaîne qui ne correspond pas à une commande connue, cette `trap` instruction affiche la chaîne « erreur de commande interceptée ».</span><span class="sxs-lookup"><span data-stu-id="85801-144">When a function or script encounters a string that does not match a known command, this `trap` statement displays the "Command error trapped" string.</span></span>
<span data-ttu-id="85801-145">Après l’exécution de la `trap` liste d’instructions, PowerShell écrit l’objet d’erreur dans le flux d’erreurs, puis continue le script.</span><span class="sxs-lookup"><span data-stu-id="85801-145">After running the `trap` statement list, PowerShell writes the error object to the error stream and then continues the script.</span></span>

<span data-ttu-id="85801-146">PowerShell utilise les types d’exceptions .NET.</span><span class="sxs-lookup"><span data-stu-id="85801-146">PowerShell uses .NET exception types.</span></span> <span data-ttu-id="85801-147">L’exemple suivant spécifie le type d’erreur **System. exception** :</span><span class="sxs-lookup"><span data-stu-id="85801-147">The following example specifies the **System.Exception** error type:</span></span>

```powershell
trap [System.Exception] {"An error trapped"}
```

<span data-ttu-id="85801-148">Le type d’erreur **CommandNotFoundException** hérite du type **System. exception** .</span><span class="sxs-lookup"><span data-stu-id="85801-148">The **CommandNotFoundException** error type inherits from the **System.Exception** type.</span></span> <span data-ttu-id="85801-149">Cette instruction intercepte une erreur créée par une commande inconnue.</span><span class="sxs-lookup"><span data-stu-id="85801-149">This statement traps an error that is created by an unknown command.</span></span> <span data-ttu-id="85801-150">Il intercepte également d’autres types d’erreur.</span><span class="sxs-lookup"><span data-stu-id="85801-150">It also traps other error types.</span></span>

<span data-ttu-id="85801-151">Vous pouvez avoir plusieurs `trap` instructions dans un script.</span><span class="sxs-lookup"><span data-stu-id="85801-151">You can have more than one `trap` statement in a script.</span></span> <span data-ttu-id="85801-152">Chaque type d’erreur peut être intercepté par une seule `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-152">Each error type can be trapped by only one `trap` statement.</span></span> <span data-ttu-id="85801-153">Lorsqu’une erreur se termine, PowerShell recherche le `trap` avec la correspondance la plus spécifique, en commençant par la portée d’exécution actuelle.</span><span class="sxs-lookup"><span data-stu-id="85801-153">When a terminating error occurs, PowerShell searches for the `trap` with the most specific match, starting in the current scope of execution.</span></span>

<span data-ttu-id="85801-154">L’exemple de script suivant contient une erreur.</span><span class="sxs-lookup"><span data-stu-id="85801-154">The following script example contains an error.</span></span> <span data-ttu-id="85801-155">Le script contient une `trap` instruction générale qui intercepte toutes les erreurs de fin et une `trap` instruction spécifique qui spécifie le type **CommandNotFoundException** .</span><span class="sxs-lookup"><span data-stu-id="85801-155">The script includes a general `trap` statement that traps any terminating error and a specific `trap` statement that specifies the **CommandNotFoundException** type.</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

<span data-ttu-id="85801-156">L’exécution de ce script produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="85801-156">Running this script produces the following result:</span></span>

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="85801-157">Étant donné que PowerShell ne reconnaît pas « nonsenseString » comme une applet de commande ou un autre élément, il renvoie une erreur **CommandNotFoundException** .</span><span class="sxs-lookup"><span data-stu-id="85801-157">Because PowerShell does not recognize "nonsenseString" as a cmdlet or other item, it returns a **CommandNotFoundException** error.</span></span> <span data-ttu-id="85801-158">Cette erreur de fin est interceptée par l' `trap` instruction spécifique.</span><span class="sxs-lookup"><span data-stu-id="85801-158">This terminating error is trapped by the specific `trap` statement.</span></span>

<span data-ttu-id="85801-159">L’exemple de script suivant contient les mêmes `trap` instructions avec une erreur différente :</span><span class="sxs-lookup"><span data-stu-id="85801-159">The following script example contains the same `trap` statements with a different error:</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

<span data-ttu-id="85801-160">L’exécution de ce script produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="85801-160">Running this script produces the following result:</span></span>

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

<span data-ttu-id="85801-161">La tentative de division par zéro ne crée pas d’erreur **CommandNotFoundException** .</span><span class="sxs-lookup"><span data-stu-id="85801-161">The attempt to divide by zero does not create a **CommandNotFoundException** error.</span></span> <span data-ttu-id="85801-162">Au lieu de cela, cette erreur est interceptée par l’autre `trap` instruction, qui intercepte toutes les erreurs qui se terminent.</span><span class="sxs-lookup"><span data-stu-id="85801-162">Instead, that error is trapped by the other `trap` statement, which traps any terminating error.</span></span>

### <a name="trapping-errors-and-scope"></a><span data-ttu-id="85801-163">Interception des erreurs et de la portée</span><span class="sxs-lookup"><span data-stu-id="85801-163">Trapping errors and scope</span></span>

<span data-ttu-id="85801-164">Si une erreur d’arrêt se produit dans la même portée que l' `trap` instruction, PowerShell exécute la liste des instructions définies par le `trap` .</span><span class="sxs-lookup"><span data-stu-id="85801-164">If a terminating error occurs in the same scope as the `trap` statement, PowerShell runs the list of statements defined by the `trap`.</span></span> <span data-ttu-id="85801-165">L’exécution se poursuit à l’instruction qui suit l’erreur.</span><span class="sxs-lookup"><span data-stu-id="85801-165">Execution continues at the statement after the error.</span></span> <span data-ttu-id="85801-166">Si l' `trap` instruction se trouve dans une étendue différente de celle de l’erreur, l’exécution se poursuit à l’instruction suivante qui se trouve dans la même portée que l' `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-166">If the `trap` statement is in a different scope from the error, execution continues at the next statement that is in the same scope as the `trap` statement.</span></span>

<span data-ttu-id="85801-167">Par exemple, si une erreur se produit dans une fonction et que l' `trap` instruction se trouve dans la fonction, le script se poursuit à l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="85801-167">For example, if an error occurs in a function, and the `trap` statement is in the function, the script continues at the next statement.</span></span> <span data-ttu-id="85801-168">Le script suivant contient une erreur et une `trap` instruction :</span><span class="sxs-lookup"><span data-stu-id="85801-168">The following script contains an error and a `trap` statement:</span></span>

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

<span data-ttu-id="85801-169">L’exécution de ce script produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="85801-169">Running this script produces the following result:</span></span>

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

<span data-ttu-id="85801-170">L' `trap` instruction dans la fonction intercepte l’erreur.</span><span class="sxs-lookup"><span data-stu-id="85801-170">The `trap` statement in the function traps the error.</span></span> <span data-ttu-id="85801-171">Après l’affichage du message, PowerShell reprend l’exécution de la fonction.</span><span class="sxs-lookup"><span data-stu-id="85801-171">After displaying the message, PowerShell resumes running the function.</span></span> <span data-ttu-id="85801-172">Notez que `Function1` a été terminé.</span><span class="sxs-lookup"><span data-stu-id="85801-172">Note that `Function1` was completed.</span></span>

<span data-ttu-id="85801-173">Comparez ceci avec l’exemple suivant, qui a la même erreur et la même `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-173">Compare this with the following example, which has the same error and `trap` statement.</span></span> <span data-ttu-id="85801-174">Dans cet exemple, l' `trap` instruction se trouve en dehors de la fonction :</span><span class="sxs-lookup"><span data-stu-id="85801-174">In this example, the `trap` statement occurs outside the function:</span></span>

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

<span data-ttu-id="85801-175">L’exécution de la `Function2` fonction produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="85801-175">Running the `Function2` function produces the following result:</span></span>

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="85801-176">Dans cet exemple, la commande « fonction2 is Completed » n’a pas été exécutée.</span><span class="sxs-lookup"><span data-stu-id="85801-176">In this example, the "function2 was completed" command was not run.</span></span> <span data-ttu-id="85801-177">Dans les deux exemples, l’erreur d’arrêt se produit dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="85801-177">In both examples, the terminating error occurs within the function.</span></span> <span data-ttu-id="85801-178">Dans cet exemple, cependant, l' `trap` instruction est en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="85801-178">In this example, however, the `trap` statement is outside the function.</span></span> <span data-ttu-id="85801-179">PowerShell ne revient pas à la fonction après l’exécution de l' `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="85801-179">PowerShell does not go back into the function after the `trap` statement runs.</span></span>

> [!CAUTION]
> <span data-ttu-id="85801-180">Lorsque plusieurs interruptions sont définies pour la même condition d’erreur, la première `trap` définie lexicalement (la plus élevée dans l’étendue) est utilisée.</span><span class="sxs-lookup"><span data-stu-id="85801-180">When multiple traps are defined for the same error condition, the first `trap` defined lexically (highest in the scope) is used.</span></span>

<span data-ttu-id="85801-181">Dans l’exemple suivant, seul le `trap` avec « whoops 1 » est exécuté.</span><span class="sxs-lookup"><span data-stu-id="85801-181">In the following example, only the `trap` with "whoops 1" is run.</span></span>

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> <span data-ttu-id="85801-182">Une instruction Trap est limitée à l’emplacement où elle est compilée.</span><span class="sxs-lookup"><span data-stu-id="85801-182">A Trap statement is scoped to where it compiles.</span></span> <span data-ttu-id="85801-183">Si vous avez une `trap` instruction à l’intérieur d’une fonction ou d’un script de code source point, lorsque le script de la fonction ou du point s’arrête, toutes les `trap` instructions à l’intérieur de sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="85801-183">If you have a `trap` statement inside a function or dot sourced script, when the function or dot sourced script exits, all `trap` statements inside are removed.</span></span>

### <a name="using-the-break-and-continue-keywords"></a><span data-ttu-id="85801-184">Utilisation des mots clés Break et continue</span><span class="sxs-lookup"><span data-stu-id="85801-184">Using the break and continue keywords</span></span>

<span data-ttu-id="85801-185">Vous pouvez utiliser les `break` `continue` Mots clés et dans une `trap` instruction pour déterminer si un script ou une commande continue à s’exécuter après une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="85801-185">You can use the `break` and `continue` keywords in a `trap` statement to determine whether a script or command continues to run after a terminating error.</span></span>

<span data-ttu-id="85801-186">Si vous incluez une `break` instruction dans une `trap` liste d’instructions, PowerShell arrête la fonction ou le script.</span><span class="sxs-lookup"><span data-stu-id="85801-186">If you include a `break` statement in a `trap` statement list, PowerShell stops the function or script.</span></span> <span data-ttu-id="85801-187">L’exemple de fonction suivant utilise le `break` mot clé dans une `trap` instruction :</span><span class="sxs-lookup"><span data-stu-id="85801-187">The following sample function uses the `break` keyword in a `trap` statement:</span></span>

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

<span data-ttu-id="85801-188">Étant donné que l' `trap` instruction incluait le `break` mot clé, la fonction ne continue pas de s’exécuter et la ligne « fonction terminée » n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="85801-188">Because the `trap` statement included the `break` keyword, the function does not continue to run, and the "Function completed" line is not run.</span></span>

<span data-ttu-id="85801-189">Si vous incluez un `continue` mot clé dans une `trap` instruction, PowerShell reprend après l’instruction qui a provoqué l’erreur, comme c’est le cas sans `break` ou `continue` .</span><span class="sxs-lookup"><span data-stu-id="85801-189">If you include a `continue` keyword in a `trap` statement, PowerShell resumes after the statement that caused the error, just as it would without `break` or `continue`.</span></span> <span data-ttu-id="85801-190">`continue`Toutefois, avec le mot clé, PowerShell n’écrit pas d’erreur dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="85801-190">With the `continue` keyword, however, PowerShell does not write an error to the error stream.</span></span>

<span data-ttu-id="85801-191">L’exemple de fonction suivant utilise le `continue` mot clé dans une `trap` instruction :</span><span class="sxs-lookup"><span data-stu-id="85801-191">The following sample function uses the `continue` keyword in a `trap` statement:</span></span>

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

<span data-ttu-id="85801-192">La fonction reprend après que l’erreur a été interceptée et l’instruction « Function Completed » s’exécute.</span><span class="sxs-lookup"><span data-stu-id="85801-192">The function resumes after the error is trapped, and the "Function completed" statement runs.</span></span> <span data-ttu-id="85801-193">Aucune erreur n’est écrite dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="85801-193">No error is written to the error stream.</span></span>

## <a name="notes"></a><span data-ttu-id="85801-194">Notes</span><span class="sxs-lookup"><span data-stu-id="85801-194">Notes</span></span>

<span data-ttu-id="85801-195">`trap` les instructions offrent un moyen simple de s’assurer que toutes les erreurs de fin au sein d’une étendue sont gérées.</span><span class="sxs-lookup"><span data-stu-id="85801-195">`trap` statements provide a simple way to broadly ensure all terminating errors within a scope are handled.</span></span> <span data-ttu-id="85801-196">Pour une gestion des erreurs plus fine, utilisez des `try` / `catch` blocs où les interruptions sont définies à l’aide d' `catch` instructions.</span><span class="sxs-lookup"><span data-stu-id="85801-196">For more finer-grained error handling, use `try`/`catch` blocks where traps are defined using `catch` statements.</span></span> <span data-ttu-id="85801-197">Les `catch` instructions s’appliquent uniquement au code à l’intérieur de l' `try` instruction associée.</span><span class="sxs-lookup"><span data-stu-id="85801-197">The `catch` statements only apply to the code inside the associated `try` statement.</span></span> <span data-ttu-id="85801-198">Pour plus d’informations, consultez [about_Try_Catch_Finally](about_Try_Catch_Finally.md).</span><span class="sxs-lookup"><span data-stu-id="85801-198">For more information, see [about_Try_Catch_Finally](about_Try_Catch_Finally.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85801-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85801-199">See also</span></span>

[<span data-ttu-id="85801-200">about_Break</span><span class="sxs-lookup"><span data-stu-id="85801-200">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="85801-201">about_Continue</span><span class="sxs-lookup"><span data-stu-id="85801-201">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="85801-202">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="85801-202">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="85801-203">about_Throw</span><span class="sxs-lookup"><span data-stu-id="85801-203">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="85801-204">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="85801-204">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
