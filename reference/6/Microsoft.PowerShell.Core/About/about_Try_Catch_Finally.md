---
description: Décrit comment utiliser les `Try` blocs, `Catch` et `Finally` pour gérer les erreurs de fin.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: b9395fd4149e4cdaf564d252861377dfc5e17ddd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206841"
---
# <a name="about-try-catch-finally"></a><span data-ttu-id="63dcc-104">À propos de try catch finally</span><span class="sxs-lookup"><span data-stu-id="63dcc-104">About Try Catch Finally</span></span>

## <a name="short-description"></a><span data-ttu-id="63dcc-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="63dcc-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="63dcc-106">Décrit comment utiliser les `Try` blocs, `Catch` et `Finally` pour gérer les erreurs de fin.</span><span class="sxs-lookup"><span data-stu-id="63dcc-106">Describes how to use the `Try`, `Catch`, and `Finally` blocks to handle terminating errors.</span></span>

## <a name="long-description"></a><span data-ttu-id="63dcc-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="63dcc-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="63dcc-108">Utilisez `Try` des `Catch` blocs, et `Finally` pour répondre à ou gérer les erreurs de fin dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="63dcc-108">Use `Try`, `Catch`, and `Finally` blocks to respond to or handle terminating errors in scripts.</span></span> <span data-ttu-id="63dcc-109">L' `Trap` instruction peut également être utilisée pour gérer les erreurs de fin dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="63dcc-109">The `Trap` statement can also be used to handle terminating errors in scripts.</span></span> <span data-ttu-id="63dcc-110">Pour plus d’informations, consultez [about_Trap](about_Trap.md).</span><span class="sxs-lookup"><span data-stu-id="63dcc-110">For more information, see [about_Trap](about_Trap.md).</span></span>

<span data-ttu-id="63dcc-111">Une erreur d’arrêt empêche l’exécution d’une instruction.</span><span class="sxs-lookup"><span data-stu-id="63dcc-111">A terminating error stops a statement from running.</span></span> <span data-ttu-id="63dcc-112">Si PowerShell ne gère pas une erreur de fin d’une certaine façon, PowerShell arrête également l’exécution de la fonction ou du script à l’aide du pipeline actuel.</span><span class="sxs-lookup"><span data-stu-id="63dcc-112">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script using the current pipeline.</span></span> <span data-ttu-id="63dcc-113">Dans d’autres langages, tels que C \# , les erreurs de fin sont appelées exceptions.</span><span class="sxs-lookup"><span data-stu-id="63dcc-113">In other languages, such as C\#, terminating errors are referred to as exceptions.</span></span>

<span data-ttu-id="63dcc-114">Utilisez le `Try` bloc pour définir une section d’un script dans laquelle vous souhaitez que PowerShell surveille les erreurs.</span><span class="sxs-lookup"><span data-stu-id="63dcc-114">Use the `Try` block to define a section of a script in which you want PowerShell to monitor for errors.</span></span> <span data-ttu-id="63dcc-115">Lorsqu’une erreur se produit dans le `Try` bloc, l’erreur est d’abord enregistrée dans la `$Error` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="63dcc-115">When an error occurs within the `Try` block, the error is first saved to the `$Error` automatic variable.</span></span> <span data-ttu-id="63dcc-116">PowerShell recherche ensuite un `Catch` bloc pour gérer l’erreur.</span><span class="sxs-lookup"><span data-stu-id="63dcc-116">PowerShell then searches for a `Catch` block to handle the error.</span></span> <span data-ttu-id="63dcc-117">Si l' `Try` instruction n’a pas de `Catch` bloc correspondant, PowerShell continue de rechercher un `Catch` bloc ou une instruction appropriés `Trap` dans les étendues parentes.</span><span class="sxs-lookup"><span data-stu-id="63dcc-117">If the `Try` statement does not have a matching `Catch` block, PowerShell continues to search for an appropriate `Catch` block or `Trap` statement in the parent scopes.</span></span> <span data-ttu-id="63dcc-118">Une fois qu’un `Catch` bloc est terminé ou qu’aucun `Catch` bloc ou `Trap` instruction approprié n’a été trouvé, le `Finally` bloc est exécuté.</span><span class="sxs-lookup"><span data-stu-id="63dcc-118">After a `Catch` block is completed or if no appropriate `Catch` block or `Trap` statement is found, the `Finally` block is run.</span></span> <span data-ttu-id="63dcc-119">Si l’erreur ne peut pas être gérée, l’erreur est écrite dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="63dcc-119">If the error cannot be handled, the error is written to the error stream.</span></span>

<span data-ttu-id="63dcc-120">Un `Catch` bloc peut inclure des commandes pour le suivi de l’erreur ou pour la récupération du déroulement attendu du script.</span><span class="sxs-lookup"><span data-stu-id="63dcc-120">A `Catch` block can include commands for tracking the error or for recovering the expected flow of the script.</span></span> <span data-ttu-id="63dcc-121">Un `Catch` bloc peut spécifier les types d’erreurs qu’il intercepte.</span><span class="sxs-lookup"><span data-stu-id="63dcc-121">A `Catch` block can specify which error types it catches.</span></span> <span data-ttu-id="63dcc-122">Une `Try` instruction peut inclure plusieurs `Catch` blocs pour différents genres d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="63dcc-122">A `Try` statement can include multiple `Catch` blocks for different kinds of errors.</span></span>

<span data-ttu-id="63dcc-123">Un `Finally` bloc peut être utilisé pour libérer toutes les ressources qui ne sont plus nécessaires à votre script.</span><span class="sxs-lookup"><span data-stu-id="63dcc-123">A `Finally` block can be used to free any resources that are no longer needed by your script.</span></span>

<span data-ttu-id="63dcc-124">`Try`, et `Catch` `Finally` ressemblent aux `Try` `Catch` Mots clés, et `Finally` utilisés dans le \# langage de programmation C.</span><span class="sxs-lookup"><span data-stu-id="63dcc-124">`Try`, `Catch`, and `Finally` resemble the `Try`, `Catch`, and `Finally` keywords used in the C\# programming language.</span></span>

### <a name="syntax"></a><span data-ttu-id="63dcc-125">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63dcc-125">SYNTAX</span></span>

<span data-ttu-id="63dcc-126">Une `Try` instruction contient un `Try` bloc, zéro, un ou plusieurs `Catch` blocs, et zéro ou un `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="63dcc-126">A `Try` statement contains a `Try` block, zero or more `Catch` blocks, and zero or one `Finally` block.</span></span> <span data-ttu-id="63dcc-127">Une `Try` instruction doit avoir au moins un bloc `Catch` ou un `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="63dcc-127">A `Try` statement must have at least one `Catch` block or one `Finally` block.</span></span>

<span data-ttu-id="63dcc-128">L’exemple suivant illustre la `Try` syntaxe de bloc :</span><span class="sxs-lookup"><span data-stu-id="63dcc-128">The following shows the `Try` block syntax:</span></span>

```powershell
try {<statement list>}
```

<span data-ttu-id="63dcc-129">Le `Try` mot clé est suivi d’une liste d’instructions entre accolades.</span><span class="sxs-lookup"><span data-stu-id="63dcc-129">The `Try` keyword is followed by a statement list in braces.</span></span> <span data-ttu-id="63dcc-130">Si une erreur d’arrêt se produit pendant l’exécution des instructions de la liste d’instructions, le script passe l’objet d’erreur du `Try` bloc à un `Catch` bloc approprié.</span><span class="sxs-lookup"><span data-stu-id="63dcc-130">If a terminating error occurs while the statements in the statement list are being run, the script passes the error object from the `Try` block to an appropriate `Catch` block.</span></span>

<span data-ttu-id="63dcc-131">L’exemple suivant illustre la `Catch` syntaxe de bloc :</span><span class="sxs-lookup"><span data-stu-id="63dcc-131">The following shows the `Catch` block syntax:</span></span>

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

<span data-ttu-id="63dcc-132">Les types d’erreurs apparaissent entre crochets.</span><span class="sxs-lookup"><span data-stu-id="63dcc-132">Error types appear in brackets.</span></span> <span data-ttu-id="63dcc-133">Les crochets les plus éloignés indiquent que l’élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="63dcc-133">The outermost brackets indicate the element is optional.</span></span>

<span data-ttu-id="63dcc-134">Le `Catch` mot clé est suivi d’une liste facultative de spécifications de type d’erreur et d’une liste d’instructions.</span><span class="sxs-lookup"><span data-stu-id="63dcc-134">The `Catch` keyword is followed by an optional list of error type specifications and a statement list.</span></span> <span data-ttu-id="63dcc-135">Si une erreur se termine dans le `Try` bloc, PowerShell recherche un bloc approprié `Catch` .</span><span class="sxs-lookup"><span data-stu-id="63dcc-135">If a terminating error occurs in the `Try` block, PowerShell searches for an appropriate `Catch` block.</span></span> <span data-ttu-id="63dcc-136">Si un est trouvé, les instructions du `Catch` bloc sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="63dcc-136">If one is found, the statements in the `Catch` block are executed.</span></span>

<span data-ttu-id="63dcc-137">Le `Catch` bloc peut spécifier un ou plusieurs types d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="63dcc-137">The `Catch` block can specify one or more error types.</span></span> <span data-ttu-id="63dcc-138">Un type d’erreur est une exception Microsoft .NET Framework ou une exception dérivée d’une exception .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63dcc-138">An error type is a Microsoft .NET Framework exception or an exception that is derived from a .NET Framework exception.</span></span> <span data-ttu-id="63dcc-139">Un `Catch` bloc gère les erreurs de la classe d’exception .NET Framework spécifiée ou de toute classe qui dérive de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="63dcc-139">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span>

<span data-ttu-id="63dcc-140">Si un `Catch` bloc spécifie un type d’erreur, ce `Catch` bloc gère ce type d’erreur.</span><span class="sxs-lookup"><span data-stu-id="63dcc-140">If a `Catch` block specifies an error type, that `Catch` block handles that type of error.</span></span> <span data-ttu-id="63dcc-141">Si un `Catch` bloc ne spécifie pas de type d’erreur, ce `Catch` bloc gère toutes les erreurs rencontrées dans le `Try` bloc.</span><span class="sxs-lookup"><span data-stu-id="63dcc-141">If a `Catch` block does not specify an error type, that `Catch` block handles any error encountered in the `Try` block.</span></span> <span data-ttu-id="63dcc-142">Une `Try` instruction peut inclure plusieurs `Catch` blocs pour les différents types d’erreur spécifiés.</span><span class="sxs-lookup"><span data-stu-id="63dcc-142">A `Try` statement can include multiple `Catch` blocks for the different specified error types.</span></span>

<span data-ttu-id="63dcc-143">L’exemple suivant illustre la `Finally` syntaxe de bloc :</span><span class="sxs-lookup"><span data-stu-id="63dcc-143">The following shows the `Finally` block syntax:</span></span>

```powershell
finally {<statement list>}
```

<span data-ttu-id="63dcc-144">Le `Finally` mot clé est suivi d’une liste d’instructions qui s’exécute chaque fois que le script est exécuté, même si l' `Try` instruction a été exécutée sans erreur ou si une erreur a été interceptée dans une `Catch` instruction.</span><span class="sxs-lookup"><span data-stu-id="63dcc-144">The `Finally` keyword is followed by a statement list that runs every time the script is run, even if the `Try` statement ran without error or an error was caught in a `Catch` statement.</span></span>

<span data-ttu-id="63dcc-145">Notez que la <kbd>combinaison de touches Ctrl</kbd> + <kbd>+</kbd> arrête le pipeline.</span><span class="sxs-lookup"><span data-stu-id="63dcc-145">Note that pressing <kbd>CTRL</kbd>+<kbd>C</kbd> stops the pipeline.</span></span> <span data-ttu-id="63dcc-146">Les objets qui sont envoyés au pipeline ne seront pas affichés en tant que sortie.</span><span class="sxs-lookup"><span data-stu-id="63dcc-146">Objects that are sent to the pipeline will not be displayed as output.</span></span> <span data-ttu-id="63dcc-147">Par conséquent, si vous incluez une instruction à afficher, par exemple « le bloc finally a été exécuté », elle ne s’affichera pas une fois que vous aurez appuyé sur <kbd>CTRL</kbd> + <kbd>C</kbd>, même si le `Finally` bloc s’exécutait.</span><span class="sxs-lookup"><span data-stu-id="63dcc-147">Therefore, if you include a statement to be displayed, such as "Finally block has run", it will not be displayed after you press <kbd>CTRL</kbd>+<kbd>C</kbd>, even if the `Finally` block ran.</span></span>

### <a name="catching-errors"></a><span data-ttu-id="63dcc-148">INTERCEPTION DES ERREURS</span><span class="sxs-lookup"><span data-stu-id="63dcc-148">CATCHING ERRORS</span></span>

<span data-ttu-id="63dcc-149">L’exemple de script suivant illustre un `Try` bloc avec un `Catch` bloc :</span><span class="sxs-lookup"><span data-stu-id="63dcc-149">The following sample script shows a `Try` block with a `Catch` block:</span></span>

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

<span data-ttu-id="63dcc-150">Le `Catch` mot clé doit suivre immédiatement le `Try` bloc ou un autre `Catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="63dcc-150">The `Catch` keyword must immediately follow the `Try` block or another `Catch` block.</span></span>

<span data-ttu-id="63dcc-151">PowerShell ne reconnaît pas « NonsenseString » comme une applet de commande ou un autre élément.</span><span class="sxs-lookup"><span data-stu-id="63dcc-151">PowerShell does not recognize "NonsenseString" as a cmdlet or other item.</span></span>
<span data-ttu-id="63dcc-152">L’exécution de ce script renvoie le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="63dcc-152">Running this script returns the following result:</span></span>

```powershell
An error occurred.
```

<span data-ttu-id="63dcc-153">Quand le script rencontre « NonsenseString », il provoque une erreur de fin.</span><span class="sxs-lookup"><span data-stu-id="63dcc-153">When the script encounters "NonsenseString", it causes a terminating error.</span></span> <span data-ttu-id="63dcc-154">Le `Catch` bloc gère l’erreur en exécutant la liste d’instructions à l’intérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="63dcc-154">The `Catch` block handles the error by running the statement list inside the block.</span></span>

### <a name="using-multiple-catch-statements"></a><span data-ttu-id="63dcc-155">UTILISATION DE PLUSIEURS INSTRUCTIONS CATCH</span><span class="sxs-lookup"><span data-stu-id="63dcc-155">USING MULTIPLE CATCH STATEMENTS</span></span>

<span data-ttu-id="63dcc-156">Une `Try` instruction peut comporter un nombre quelconque de `Catch` blocs.</span><span class="sxs-lookup"><span data-stu-id="63dcc-156">A `Try` statement can have any number of `Catch` blocks.</span></span> <span data-ttu-id="63dcc-157">Par exemple, le script suivant contient un `Try` bloc qui est téléchargé `MyDoc.doc` et contient deux `Catch` blocs :</span><span class="sxs-lookup"><span data-stu-id="63dcc-157">For example, the following script has a `Try` block that downloads `MyDoc.doc`, and it contains two `Catch` blocks:</span></span>

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

<span data-ttu-id="63dcc-158">Le premier `Catch` bloc gère les erreurs des types **System .net. WebException** et **System. IO. IOException** .</span><span class="sxs-lookup"><span data-stu-id="63dcc-158">The first `Catch` block handles errors of the **System.Net.WebException** and **System.IO.IOException** types.</span></span> <span data-ttu-id="63dcc-159">Le deuxième `Catch` bloc ne spécifie pas de type d’erreur.</span><span class="sxs-lookup"><span data-stu-id="63dcc-159">The second `Catch` block does not specify an error type.</span></span> <span data-ttu-id="63dcc-160">Le deuxième `Catch` bloc gère toutes les autres erreurs de fin qui se produisent.</span><span class="sxs-lookup"><span data-stu-id="63dcc-160">The second `Catch` block handles any other terminating errors that occur.</span></span>

<span data-ttu-id="63dcc-161">PowerShell met en correspondance les types d’erreurs par héritage.</span><span class="sxs-lookup"><span data-stu-id="63dcc-161">PowerShell matches error types by inheritance.</span></span> <span data-ttu-id="63dcc-162">Un `Catch` bloc gère les erreurs de la classe d’exception .NET Framework spécifiée ou de toute classe qui dérive de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="63dcc-162">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span> <span data-ttu-id="63dcc-163">L’exemple suivant contient un `Catch` bloc qui intercepte une erreur « commande introuvable » :</span><span class="sxs-lookup"><span data-stu-id="63dcc-163">The following example contains a `Catch` block that catches a "Command Not Found" error:</span></span>

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

<span data-ttu-id="63dcc-164">Le type d’erreur spécifié, **CommandNotFoundException** , hérite du type de **temExceptionSystem.Sys** .</span><span class="sxs-lookup"><span data-stu-id="63dcc-164">The specified error type, **CommandNotFoundException** , inherits from the **System.SystemException** type.</span></span> <span data-ttu-id="63dcc-165">L’exemple suivant intercepte également une erreur de commande introuvable :</span><span class="sxs-lookup"><span data-stu-id="63dcc-165">The following example also catches a Command Not Found error:</span></span>

```powershell
catch [System.SystemException] {"Base Exception" }
```

<span data-ttu-id="63dcc-166">Ce `Catch` bloc gère l’erreur « commande introuvable » et les autres erreurs qui héritent du type **SystemException** .</span><span class="sxs-lookup"><span data-stu-id="63dcc-166">This `Catch` block handles the "Command Not Found" error and other errors that inherit from the **SystemException** type.</span></span>

<span data-ttu-id="63dcc-167">Si vous spécifiez une classe d’erreur et l’une de ses classes dérivées, placez le `Catch` bloc de la classe dérivée avant le `Catch` bloc de la classe générale.</span><span class="sxs-lookup"><span data-stu-id="63dcc-167">If you specify an error class and one of its derived classes, place the `Catch` block for the derived class before the `Catch` block for the general class.</span></span>

### <a name="using-traps-in-a-try-catch"></a><span data-ttu-id="63dcc-168">Utilisation d’interruptions dans une tentative catch</span><span class="sxs-lookup"><span data-stu-id="63dcc-168">Using Traps in a Try Catch</span></span>

<span data-ttu-id="63dcc-169">Lorsqu’une erreur d’arrêt se produit dans un `Try` bloc avec un `Trap` défini dans le `Try` bloc, même s’il existe un `Catch` bloc correspondant, l' `Trap` instruction prend le contrôle.</span><span class="sxs-lookup"><span data-stu-id="63dcc-169">When a terminating error occurs in a `Try` block with a `Trap` defined within the `Try` block, even if there is a matching `Catch` block, the `Trap` statement takes control.</span></span>

<span data-ttu-id="63dcc-170">Si un `Trap` existe dans un bloc supérieur à `Try` , et qu’il n’existe pas de `Catch` bloc correspondant dans la portée actuelle, le prend le `Trap` contrôle, même si une portée parente a un `Catch` bloc correspondant.</span><span class="sxs-lookup"><span data-stu-id="63dcc-170">If a `Trap` exists at a higher block than the `Try`, and there is no matching `Catch` block within the current scope, the `Trap` will take control, even if any parent scope has a matching `Catch` block.</span></span>

### <a name="accessing-exception-information"></a><span data-ttu-id="63dcc-171">ACCÈS AUX INFORMATIONS SUR LES EXCEPTIONS</span><span class="sxs-lookup"><span data-stu-id="63dcc-171">ACCESSING EXCEPTION INFORMATION</span></span>

<span data-ttu-id="63dcc-172">Dans un `Catch` bloc, l’erreur actuelle est accessible à l’aide de `$_` , qui est également connu sous le nom de `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="63dcc-172">Within a `Catch` block, the current error can be accessed using `$_`, which is also known as `$PSItem`.</span></span> <span data-ttu-id="63dcc-173">L’objet est de type **ErrorRecord** .</span><span class="sxs-lookup"><span data-stu-id="63dcc-173">The object is of type **ErrorRecord** .</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

<span data-ttu-id="63dcc-174">L’exécution de ce script renvoie le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="63dcc-174">Running this script returns the following result:</span></span>

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

<span data-ttu-id="63dcc-175">Des propriétés supplémentaires sont accessibles, telles que **ScriptStackTrace** , **exception** et **ErrorDetails** .</span><span class="sxs-lookup"><span data-stu-id="63dcc-175">There are additional properties that can be accessed, such as **ScriptStackTrace** , **Exception** , and **ErrorDetails** .</span></span>  <span data-ttu-id="63dcc-176">Par exemple, si nous modifions le script comme suit :</span><span class="sxs-lookup"><span data-stu-id="63dcc-176">For example, if we change the script to the following:</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

<span data-ttu-id="63dcc-177">Le résultat sera semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="63dcc-177">The result will be similar to:</span></span>

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a><span data-ttu-id="63dcc-178">LIBÉRATION DE RESSOURCES À L’AIDE DE FINALLY</span><span class="sxs-lookup"><span data-stu-id="63dcc-178">FREEING RESOURCES BY USING FINALLY</span></span>

<span data-ttu-id="63dcc-179">Pour libérer les ressources utilisées par un script, ajoutez un `Finally` bloc après `Try` les `Catch` blocs et.</span><span class="sxs-lookup"><span data-stu-id="63dcc-179">To free resources used by a script, add a `Finally` block after the `Try` and `Catch` blocks.</span></span> <span data-ttu-id="63dcc-180">Les `Finally` instructions de bloc s’exécutent indépendamment du fait que le `Try` bloc rencontre une erreur de fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="63dcc-180">The `Finally` block statements run regardless of whether the `Try` block encounters a terminating error.</span></span> <span data-ttu-id="63dcc-181">PowerShell exécute le `Finally` bloc avant que le script ne se termine ou avant que le bloc actuel ne soit hors de portée.</span><span class="sxs-lookup"><span data-stu-id="63dcc-181">PowerShell runs the `Finally` block before the script terminates or before the current block goes out of scope.</span></span>

<span data-ttu-id="63dcc-182">Un `Finally` bloc s’exécute même si vous utilisez <kbd>CTRL</kbd> + <kbd>C</kbd> pour arrêter le script.</span><span class="sxs-lookup"><span data-stu-id="63dcc-182">A `Finally` block runs even if you use <kbd>CTRL</kbd>+<kbd>C</kbd> to stop the script.</span></span> <span data-ttu-id="63dcc-183">Un `Finally` bloc s’exécute également si un mot clé Exit arrête le script dans un `Catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="63dcc-183">A `Finally` block also runs if an Exit keyword stops the script from within a `Catch` block.</span></span>

### <a name="see-also"></a><span data-ttu-id="63dcc-184">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="63dcc-184">SEE ALSO</span></span>

[<span data-ttu-id="63dcc-185">about_Break</span><span class="sxs-lookup"><span data-stu-id="63dcc-185">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="63dcc-186">about_Continue</span><span class="sxs-lookup"><span data-stu-id="63dcc-186">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="63dcc-187">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="63dcc-187">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="63dcc-188">about_Throw</span><span class="sxs-lookup"><span data-stu-id="63dcc-188">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="63dcc-189">about_Trap</span><span class="sxs-lookup"><span data-stu-id="63dcc-189">about_Trap</span></span>](about_Trap.md)
