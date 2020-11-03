---
description: Décrit les variables qui stockent des informations d’État pour PowerShell. Ces variables sont créées et gérées par PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: e7525ad8acd6dd5aa2dc65a8d49d03c1c6260bea
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206669"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="3e210-105">À propos des variables automatiques</span><span class="sxs-lookup"><span data-stu-id="3e210-105">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="3e210-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="3e210-106">Short description</span></span>

<span data-ttu-id="3e210-107">Décrit les variables qui stockent des informations d’État pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e210-107">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="3e210-108">Ces variables sont créées et gérées par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e210-108">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="3e210-109">Description longue</span><span class="sxs-lookup"><span data-stu-id="3e210-109">Long description</span></span>

<span data-ttu-id="3e210-110">Conceptuellement, ces variables sont considérées comme étant en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="3e210-110">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="3e210-111">Même s’ils **peuvent** être écrits dans, pour des raisons de compatibilité descendante, ils ne **doivent pas** être écrits.</span><span class="sxs-lookup"><span data-stu-id="3e210-111">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="3e210-112">Voici une liste des variables automatiques dans PowerShell :</span><span class="sxs-lookup"><span data-stu-id="3e210-112">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="3e210-113">Contient le dernier jeton de la dernière ligne reçue par la session.</span><span class="sxs-lookup"><span data-stu-id="3e210-113">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="3e210-114">$?</span><span class="sxs-lookup"><span data-stu-id="3e210-114">$?</span></span>

<span data-ttu-id="3e210-115">Contient l’état d’exécution de la dernière commande.</span><span class="sxs-lookup"><span data-stu-id="3e210-115">Contains the execution status of the last command.</span></span> <span data-ttu-id="3e210-116">Elle contient la **valeur true** si la dernière commande a réussi et **false** si elle a échoué.</span><span class="sxs-lookup"><span data-stu-id="3e210-116">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="3e210-117">Pour les applets de commande et les fonctions avancées qui sont exécutées à plusieurs étapes dans un pipeline, par exemple dans les `process` `end` blocs et, l’appel de `this.WriteError()` ou, respectivement, `$PSCmdlet.WriteError()` à n’importe quel point, est défini `$?` sur **false** , comme c’est le cas `this.ThrowTerminatingError()` et `$PSCmdlet.ThrowTerminatingError()` .</span><span class="sxs-lookup"><span data-stu-id="3e210-117">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False** , as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="3e210-118">L' `Write-Error` applet de commande affecte toujours la `$?` **valeur false** immédiatement après son exécution, mais elle n’a pas la valeur `$?` **false** pour une fonction qui l’appelle :</span><span class="sxs-lookup"><span data-stu-id="3e210-118">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="3e210-119">Dans ce dernier cas, `$PSCmdlet.WriteError()` doit être utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="3e210-119">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="3e210-120">Pour les commandes natives (exécutables), a la valeur `$?` **true** lorsque a la valeur `$LASTEXITCODE` 0, et la valeur **false** lorsque `$LASTEXITCODE` est une autre valeur.</span><span class="sxs-lookup"><span data-stu-id="3e210-120">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="3e210-121">Jusqu’à PowerShell 7, contenant une instruction dans les parenthèses, la syntaxe de sous-expression `(...)` ou l’expression de tableau est `$(...)` `@(...)` toujours réinitialisée `$?` à **true** , de sorte que `(Write-Error)` affiche la `$?` **valeur true** .</span><span class="sxs-lookup"><span data-stu-id="3e210-121">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True** , so that `(Write-Error)` shows `$?` as **True** .</span></span>
> <span data-ttu-id="3e210-122">Cela a été modifié dans PowerShell 7, afin de `$?` refléter toujours la réussite réelle de la dernière commande exécutée dans ces expressions.</span><span class="sxs-lookup"><span data-stu-id="3e210-122">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="3e210-123">Contient le premier jeton de la dernière ligne reçue par la session.</span><span class="sxs-lookup"><span data-stu-id="3e210-123">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="3e210-124">$_</span><span class="sxs-lookup"><span data-stu-id="3e210-124">$_</span></span>

<span data-ttu-id="3e210-125">Comme pour `$PSItem`.</span><span class="sxs-lookup"><span data-stu-id="3e210-125">Same as `$PSItem`.</span></span> <span data-ttu-id="3e210-126">Contient l’objet actuel dans l’objet de pipeline.</span><span class="sxs-lookup"><span data-stu-id="3e210-126">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="3e210-127">Vous pouvez utiliser cette variable dans les commandes qui exécutent une action sur chaque objet ou sur les objets sélectionnés dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="3e210-127">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="3e210-128">$args</span><span class="sxs-lookup"><span data-stu-id="3e210-128">$args</span></span>

<span data-ttu-id="3e210-129">Contient un tableau de valeurs pour les paramètres non déclarés passés à une fonction, à un script ou à un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="3e210-129">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="3e210-130">Lorsque vous créez une fonction, vous pouvez déclarer les paramètres à l’aide du `param` mot clé ou en ajoutant une liste de paramètres séparés par des virgules entre parenthèses après le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3e210-130">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="3e210-131">Dans une action d’événement, la `$Args` variable contient des objets qui représentent les arguments d’événement de l’événement en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="3e210-131">In an event action, the `$Args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="3e210-132">Cette variable est remplie uniquement dans le `Action` bloc d’une commande d’inscription d’événement.</span><span class="sxs-lookup"><span data-stu-id="3e210-132">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="3e210-133">La valeur de cette variable peut également être trouvée dans la propriété **SourceArgs** de l’objet **PSEventArgs** `Get-Event` retourné par.</span><span class="sxs-lookup"><span data-stu-id="3e210-133">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="3e210-134">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="3e210-134">$ConsoleFileName</span></span>

<span data-ttu-id="3e210-135">Contient le chemin d’accès du fichier de console ( `.psc1` ) qui a été le plus récemment utilisé dans la session.</span><span class="sxs-lookup"><span data-stu-id="3e210-135">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="3e210-136">Cette variable est remplie lorsque vous démarrez PowerShell à l’aide du paramètre **PSConsoleFile** ou lorsque vous utilisez l' `Export-Console` applet de commande pour exporter des noms de composant logiciel enfichable vers un fichier de console.</span><span class="sxs-lookup"><span data-stu-id="3e210-136">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="3e210-137">Lorsque vous utilisez l' `Export-Console` applet de commande sans paramètres, elle met à jour automatiquement le fichier de console qui a été utilisé le plus récemment dans la session.</span><span class="sxs-lookup"><span data-stu-id="3e210-137">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="3e210-138">Vous pouvez utiliser cette variable automatique pour déterminer le fichier qui sera mis à jour.</span><span class="sxs-lookup"><span data-stu-id="3e210-138">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="3e210-139">$Error</span><span class="sxs-lookup"><span data-stu-id="3e210-139">$Error</span></span>

<span data-ttu-id="3e210-140">Contient un tableau d’objets d’erreur qui représentent les erreurs les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="3e210-140">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="3e210-141">L’erreur la plus récente est le premier objet d’erreur dans le tableau `$Error[0]` .</span><span class="sxs-lookup"><span data-stu-id="3e210-141">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="3e210-142">Pour éviter qu’une erreur ne soit ajoutée au `$Error` tableau, utilisez le paramètre commun **ErrorAction** avec la valeur **ignore** .</span><span class="sxs-lookup"><span data-stu-id="3e210-142">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore** .</span></span> <span data-ttu-id="3e210-143">Pour plus d’informations, consultez [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="3e210-143">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="3e210-144">$Event</span><span class="sxs-lookup"><span data-stu-id="3e210-144">$Event</span></span>

<span data-ttu-id="3e210-145">Contient un objet **PSEventArgs** qui représente l’événement en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="3e210-145">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="3e210-146">Cette variable est remplie uniquement dans le `Action` bloc d’une commande d’inscription d’événement, telle que `Register-ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="3e210-146">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="3e210-147">La valeur de cette variable est le même que celui retourné par l’applet de commande `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="3e210-147">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="3e210-148">Par conséquent, vous pouvez utiliser les propriétés de la `Event` variable, telles que `$Event.TimeGenerated` , dans un `Action` bloc de script.</span><span class="sxs-lookup"><span data-stu-id="3e210-148">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="3e210-149">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="3e210-149">$EventArgs</span></span>

<span data-ttu-id="3e210-150">Contient un objet qui représente le premier argument d’événement qui dérive de **EventArgs** de l’événement en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="3e210-150">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="3e210-151">Cette variable est remplie uniquement dans le `Action` bloc d’une commande d’inscription d’événement.</span><span class="sxs-lookup"><span data-stu-id="3e210-151">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="3e210-152">La valeur de cette variable peut également être trouvée dans la propriété **SourceEventArgs** de l’objet **PSEventArgs** `Get-Event` retourné par.</span><span class="sxs-lookup"><span data-stu-id="3e210-152">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="3e210-153">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="3e210-153">$EventSubscriber</span></span>

<span data-ttu-id="3e210-154">Contient un objet **PSEventSubscriber** qui représente l’abonné aux événements de l’événement en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="3e210-154">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="3e210-155">Cette variable est remplie uniquement dans le `Action` bloc d’une commande d’inscription d’événement.</span><span class="sxs-lookup"><span data-stu-id="3e210-155">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="3e210-156">La valeur de cette variable est le même que celui retourné par l’applet de commande `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="3e210-156">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="3e210-157">$ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="3e210-157">$ExecutionContext</span></span>

<span data-ttu-id="3e210-158">Contient un objet **EngineIntrinsics** qui représente le contexte d’exécution de l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e210-158">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="3e210-159">Vous pouvez utiliser cette variable pour rechercher les objets d’exécution qui sont disponibles pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="3e210-159">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="3e210-160">$false</span><span class="sxs-lookup"><span data-stu-id="3e210-160">$false</span></span>

<span data-ttu-id="3e210-161">Contient la **valeur false** .</span><span class="sxs-lookup"><span data-stu-id="3e210-161">Contains **False** .</span></span> <span data-ttu-id="3e210-162">Vous pouvez utiliser cette variable pour représenter la **valeur false** dans les commandes et les scripts au lieu d’utiliser la chaîne « false ».</span><span class="sxs-lookup"><span data-stu-id="3e210-162">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="3e210-163">La chaîne peut être interprétée comme **true** si elle est convertie en une chaîne non vide ou en un entier différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="3e210-163">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="3e210-164">$foreach</span><span class="sxs-lookup"><span data-stu-id="3e210-164">$foreach</span></span>

<span data-ttu-id="3e210-165">Contient l’énumérateur (pas les valeurs résultantes) d’une boucle [foreach](about_ForEach.md) .</span><span class="sxs-lookup"><span data-stu-id="3e210-165">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="3e210-166">La `$ForEach` variable existe uniquement pendant l' `ForEach` exécution de la boucle ; elle est supprimée une fois la boucle terminée.</span><span class="sxs-lookup"><span data-stu-id="3e210-166">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="3e210-167">Les énumérateurs contiennent des propriétés et des méthodes que vous pouvez utiliser pour récupérer des valeurs de boucle et modifier l’itération de boucle actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-167">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="3e210-168">Pour plus d’informations, consultez [utilisation d’énumérateurs](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="3e210-168">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="3e210-169">$HOME</span><span class="sxs-lookup"><span data-stu-id="3e210-169">$HOME</span></span>

<span data-ttu-id="3e210-170">Contient le chemin d’accès complet du répertoire de destination de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3e210-170">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="3e210-171">Cette variable est l’équivalent des `"$env:homedrive$env:homepath"` variables d’environnement Windows, en général `C:\Users\<UserName>` .</span><span class="sxs-lookup"><span data-stu-id="3e210-171">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="3e210-172">$Host</span><span class="sxs-lookup"><span data-stu-id="3e210-172">$Host</span></span>

<span data-ttu-id="3e210-173">Contient un objet qui représente l’application hôte actuelle pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e210-173">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="3e210-174">Vous pouvez utiliser cette variable pour représenter l’hôte actuel dans les commandes ou pour afficher ou modifier les propriétés de l’hôte, telles que `$Host.version` ou `$Host.CurrentCulture` , ou `$host.ui.rawui.setbackgroundcolor("Red")` .</span><span class="sxs-lookup"><span data-stu-id="3e210-174">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="3e210-175">$input</span><span class="sxs-lookup"><span data-stu-id="3e210-175">$input</span></span>

<span data-ttu-id="3e210-176">Contient un énumérateur qui énumère toutes les entrées passées à une fonction.</span><span class="sxs-lookup"><span data-stu-id="3e210-176">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="3e210-177">La `$input` variable est disponible uniquement pour les fonctions et les blocs de script (qui sont des fonctions sans nom).</span><span class="sxs-lookup"><span data-stu-id="3e210-177">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="3e210-178">Dans une fonction sans `Begin` bloc, `Process` ou `End` , la `$input` variable énumère la collection de toutes les entrées de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3e210-178">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="3e210-179">Dans le `Begin` bloc, la `$input` variable ne contient aucune donnée.</span><span class="sxs-lookup"><span data-stu-id="3e210-179">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="3e210-180">Dans le `Process` bloc, la `$input` variable contient l’objet qui se trouve actuellement dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="3e210-180">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="3e210-181">Dans le `End` bloc, la `$input` variable énumère la collection de toutes les entrées de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3e210-181">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3e210-182">Vous ne pouvez pas utiliser la `$input` variable à la fois dans le bloc de processus et dans le bloc de fin dans la même fonction ou le même bloc de script.</span><span class="sxs-lookup"><span data-stu-id="3e210-182">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="3e210-183">Étant donné que `$input` est un énumérateur, l’accès à l’une de ses propriétés `$input` n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="3e210-183">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="3e210-184">Vous pouvez stocker `$input` dans une autre variable pour réutiliser les `$input` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="3e210-184">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="3e210-185">Les énumérateurs contiennent des propriétés et des méthodes que vous pouvez utiliser pour récupérer des valeurs de boucle et modifier l’itération de boucle actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-185">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="3e210-186">Pour plus d’informations, consultez [utilisation d’énumérateurs](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="3e210-186">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="iscoreclr"></a><span data-ttu-id="3e210-187">$IsCoreCLR</span><span class="sxs-lookup"><span data-stu-id="3e210-187">$IsCoreCLR</span></span>

<span data-ttu-id="3e210-188">Contient `$True` si la session active est en cours d’exécution sur le Runtime .net Core (CoreCLR).</span><span class="sxs-lookup"><span data-stu-id="3e210-188">Contains `$True` if the current session is running on the .NET Core Runtime (CoreCLR).</span></span> <span data-ttu-id="3e210-189">Sinon, contient `$False` .</span><span class="sxs-lookup"><span data-stu-id="3e210-189">Otherwise contains `$False`.</span></span>

### <a name="islinux"></a><span data-ttu-id="3e210-190">$IsLinux</span><span class="sxs-lookup"><span data-stu-id="3e210-190">$IsLinux</span></span>

<span data-ttu-id="3e210-191">Contient `$True` si la session active est exécutée sur un système d’exploitation Linux.</span><span class="sxs-lookup"><span data-stu-id="3e210-191">Contains `$True` if the current session is running on a Linux operating system.</span></span>
<span data-ttu-id="3e210-192">Sinon, contient `$False` .</span><span class="sxs-lookup"><span data-stu-id="3e210-192">Otherwise contains `$False`.</span></span>

### <a name="ismacos"></a><span data-ttu-id="3e210-193">$IsMacOS</span><span class="sxs-lookup"><span data-stu-id="3e210-193">$IsMacOS</span></span>

<span data-ttu-id="3e210-194">Contient `$True` si la session active est exécutée sur un système d’exploitation MacOS.</span><span class="sxs-lookup"><span data-stu-id="3e210-194">Contains `$True` if the current session is running on a MacOS operating system.</span></span>
<span data-ttu-id="3e210-195">Sinon, contient `$False` .</span><span class="sxs-lookup"><span data-stu-id="3e210-195">Otherwise contains `$False`.</span></span>

### <a name="iswindows"></a><span data-ttu-id="3e210-196">$IsWindows</span><span class="sxs-lookup"><span data-stu-id="3e210-196">$IsWindows</span></span>

<span data-ttu-id="3e210-197">Contient `$TRUE` si la session active est exécutée sur un système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="3e210-197">Contains `$TRUE` if the current session is running on a Windows operating system.</span></span> <span data-ttu-id="3e210-198">Sinon, contient `$FALSE` .</span><span class="sxs-lookup"><span data-stu-id="3e210-198">Otherwise contains `$FALSE`.</span></span>

### <a name="lastexitcode"></a><span data-ttu-id="3e210-199">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="3e210-199">$LastExitCode</span></span>

<span data-ttu-id="3e210-200">Contient le code de sortie du dernier programme Windows exécuté.</span><span class="sxs-lookup"><span data-stu-id="3e210-200">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="3e210-201">$Matches</span><span class="sxs-lookup"><span data-stu-id="3e210-201">$Matches</span></span>

<span data-ttu-id="3e210-202">La `Matches` variable fonctionne avec les `-match` `-notmatch` opérateurs et.</span><span class="sxs-lookup"><span data-stu-id="3e210-202">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="3e210-203">Lorsque vous envoyez une entrée scalaire à l' `-match` opérateur or et que l’une d’elles `-notmatch` détecte une correspondance, elle retourne une valeur booléenne et remplit la `$Matches` variable automatique avec une table de hachage de toutes les valeurs de chaîne qui ont été mises en correspondance.</span><span class="sxs-lookup"><span data-stu-id="3e210-203">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="3e210-204">La `$Matches` table de hachage peut également être remplie avec des captures lorsque vous utilisez des expressions régulières avec l' `-match` opérateur.</span><span class="sxs-lookup"><span data-stu-id="3e210-204">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="3e210-205">Pour plus d’informations sur l' `-match` opérateur, consultez [about_Comparison_Operators](about_comparison_operators.md).</span><span class="sxs-lookup"><span data-stu-id="3e210-205">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="3e210-206">Pour plus d’informations sur les expressions régulières, consultez [about_regular_expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3e210-206">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="3e210-207">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="3e210-207">$MyInvocation</span></span>

<span data-ttu-id="3e210-208">Contient des informations sur la commande actuelle, telles que le nom, les paramètres, les valeurs de paramètre et les informations sur la façon dont la commande a été démarrée, appelée ou appelée, comme le nom du script qui a appelé la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-208">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="3e210-209">`$MyInvocation` est renseigné uniquement pour les scripts, les fonctions et les blocs de script.</span><span class="sxs-lookup"><span data-stu-id="3e210-209">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="3e210-210">Vous pouvez utiliser les informations de l’objet **System. Management. Automation. InvocationInfo** qui `$MyInvocation` retourne dans le script actuel, comme le chemin d’accès et le nom de fichier du script ( `$MyInvocation.MyCommand.Path` ) ou le nom d’une fonction ( `$MyInvocation.MyCommand.Name` ) pour identifier la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-210">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="3e210-211">Cela s’avère particulièrement utile pour rechercher le nom du script actuel.</span><span class="sxs-lookup"><span data-stu-id="3e210-211">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="3e210-212">À compter de PowerShell 3,0, `MyInvocation` possède les nouvelles propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="3e210-212">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

| <span data-ttu-id="3e210-213">Propriété</span><span class="sxs-lookup"><span data-stu-id="3e210-213">Property</span></span>      | <span data-ttu-id="3e210-214">Description</span><span class="sxs-lookup"><span data-stu-id="3e210-214">Description</span></span>                                         |
| ------------- | --------------------------------------------------- |
| <span data-ttu-id="3e210-215">**PSScriptRoot**</span><span class="sxs-lookup"><span data-stu-id="3e210-215">**PSScriptRoot**</span></span>  | <span data-ttu-id="3e210-216">Contient le chemin d’accès complet au script qui a appelé</span><span class="sxs-lookup"><span data-stu-id="3e210-216">Contains the full path to the script that invoked</span></span>   |
|               | <span data-ttu-id="3e210-217">commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-217">the current command.</span></span> <span data-ttu-id="3e210-218">La valeur de cette propriété est</span><span class="sxs-lookup"><span data-stu-id="3e210-218">The value of this property is</span></span>  |
|               | <span data-ttu-id="3e210-219">renseigné uniquement lorsque l’appelant est un script.</span><span class="sxs-lookup"><span data-stu-id="3e210-219">populated only when the caller is a script.</span></span>         |
| <span data-ttu-id="3e210-220">**PSCommandPath**</span><span class="sxs-lookup"><span data-stu-id="3e210-220">**PSCommandPath**</span></span> | <span data-ttu-id="3e210-221">Contient le chemin d’accès complet et le nom de fichier du script</span><span class="sxs-lookup"><span data-stu-id="3e210-221">Contains the full path and file name of the script</span></span>  |
|               | <span data-ttu-id="3e210-222">qui a appelé la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-222">that invoked the current command.</span></span> <span data-ttu-id="3e210-223">Valeur de ce</span><span class="sxs-lookup"><span data-stu-id="3e210-223">The value of this</span></span> |
|               | <span data-ttu-id="3e210-224">la propriété est remplie uniquement lorsque l’appelant est un</span><span class="sxs-lookup"><span data-stu-id="3e210-224">property is populated only when the caller is a</span></span>     |
|               | <span data-ttu-id="3e210-225">« Hello world! ».</span><span class="sxs-lookup"><span data-stu-id="3e210-225">script.</span></span>                                             |

<span data-ttu-id="3e210-226">Contrairement aux `$PSScriptRoot` `$PSCommandPath` variables automatiques et, les propriétés **PSScriptRoot** et **PSCommandPath** de la `$MyInvocation` variable automatique contiennent des informations sur le demandeur ou le script appelant, et non sur le script en cours.</span><span class="sxs-lookup"><span data-stu-id="3e210-226">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="3e210-227">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="3e210-227">$NestedPromptLevel</span></span>

<span data-ttu-id="3e210-228">Contient le niveau d’invite actuel.</span><span class="sxs-lookup"><span data-stu-id="3e210-228">Contains the current prompt level.</span></span> <span data-ttu-id="3e210-229">La valeur 0 indique le niveau d’invite d’origine.</span><span class="sxs-lookup"><span data-stu-id="3e210-229">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="3e210-230">La valeur est incrémentée lorsque vous entrez un niveau imbriqué et décrémenté lorsque vous la quittez.</span><span class="sxs-lookup"><span data-stu-id="3e210-230">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="3e210-231">Par exemple, PowerShell présente une invite de commandes imbriquée lorsque vous utilisez la `$Host.EnterNestedPrompt` méthode.</span><span class="sxs-lookup"><span data-stu-id="3e210-231">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="3e210-232">PowerShell présente également une invite de commandes imbriquée lorsque vous atteignez un point d’arrêt dans le débogueur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e210-232">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="3e210-233">Lorsque vous entrez une invite imbriquée, PowerShell suspend la commande active, enregistre le contexte d’exécution et incrémente la valeur de la `$NestedPromptLevel` variable.</span><span class="sxs-lookup"><span data-stu-id="3e210-233">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="3e210-234">Pour créer des invites de commandes imbriquées supplémentaires (jusqu’à 128 niveaux) ou pour revenir à l’invite de commandes d’origine, exécutez la commande ou tapez `exit` .</span><span class="sxs-lookup"><span data-stu-id="3e210-234">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="3e210-235">La `$NestedPromptLevel` variable vous aide à suivre le niveau d’invite.</span><span class="sxs-lookup"><span data-stu-id="3e210-235">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="3e210-236">Vous pouvez créer une autre invite de commandes PowerShell incluant cette valeur afin qu’elle soit toujours visible.</span><span class="sxs-lookup"><span data-stu-id="3e210-236">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="3e210-237">$null</span><span class="sxs-lookup"><span data-stu-id="3e210-237">$null</span></span>

<span data-ttu-id="3e210-238">`$null` variable automatique qui contient une valeur **null** ou vide.</span><span class="sxs-lookup"><span data-stu-id="3e210-238">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="3e210-239">Vous pouvez utiliser cette variable pour représenter une valeur absente ou non définie dans les commandes et les scripts.</span><span class="sxs-lookup"><span data-stu-id="3e210-239">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="3e210-240">PowerShell traite `$null` comme un objet avec une valeur, autrement dit comme un espace réservé explicite, afin que vous puissiez utiliser `$null` pour représenter une valeur vide dans une série de valeurs.</span><span class="sxs-lookup"><span data-stu-id="3e210-240">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="3e210-241">Par exemple, lorsque `$null` est inclus dans une collection, il est compté comme l’un des objets.</span><span class="sxs-lookup"><span data-stu-id="3e210-241">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="3e210-242">Si vous dirigez la `$null` variable vers l’applet de commande `ForEach-Object` , elle génère une valeur pour `$null` , comme c’est le cas pour les autres objets</span><span class="sxs-lookup"><span data-stu-id="3e210-242">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="3e210-243">Par conséquent, vous ne pouvez pas utiliser `$null` pour signifier qu' **aucune valeur de paramètre n'** est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3e210-243">As a result, you can't use `$null` to mean **no parameter value** .</span></span> <span data-ttu-id="3e210-244">Une valeur de paramètre de `$null` remplace la valeur de paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="3e210-244">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="3e210-245">Toutefois, étant donné que PowerShell traite la `$null` variable comme un espace réservé, vous pouvez l’utiliser dans des scripts comme celui qui suit, ce qui ne fonctionnerait `$null` pas si a été ignoré.</span><span class="sxs-lookup"><span data-stu-id="3e210-245">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a><span data-ttu-id="3e210-246">$PID</span><span class="sxs-lookup"><span data-stu-id="3e210-246">$PID</span></span>

<span data-ttu-id="3e210-247">Contient l’identificateur de processus (PID) du processus qui héberge la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="3e210-247">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="3e210-248">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="3e210-248">$PROFILE</span></span>

<span data-ttu-id="3e210-249">Contient le chemin d’accès complet du profil PowerShell pour l’utilisateur actuel et l’application hôte actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-249">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="3e210-250">Vous pouvez utiliser cette variable pour représenter le profil dans les commandes.</span><span class="sxs-lookup"><span data-stu-id="3e210-250">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="3e210-251">Par exemple, vous pouvez l’utiliser dans une commande pour déterminer si un profil a été créé :</span><span class="sxs-lookup"><span data-stu-id="3e210-251">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="3e210-252">Ou vous pouvez l’utiliser dans une commande pour créer un profil :</span><span class="sxs-lookup"><span data-stu-id="3e210-252">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="3e210-253">Vous pouvez l’utiliser dans une commande pour ouvrir le profil dans **notepad.exe** :</span><span class="sxs-lookup"><span data-stu-id="3e210-253">You can use it in a command to open the profile in **notepad.exe** :</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="3e210-254">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="3e210-254">$PSBoundParameters</span></span>

<span data-ttu-id="3e210-255">Contient un dictionnaire des paramètres qui sont passés à un script ou une fonction et leurs valeurs actuelles.</span><span class="sxs-lookup"><span data-stu-id="3e210-255">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="3e210-256">Cette variable a une valeur uniquement dans une portée où les paramètres sont déclarés, comme un script ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="3e210-256">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="3e210-257">Vous pouvez l’utiliser pour afficher ou modifier les valeurs actuelles des paramètres ou pour passer des valeurs de paramètres à un autre script ou à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="3e210-257">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="3e210-258">Dans cet exemple, la fonction **Test2** passe `$PSBoundParameters` à la fonction **Test1** .</span><span class="sxs-lookup"><span data-stu-id="3e210-258">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="3e210-259">Les `$PSBoundParameters` sont affichés dans le format de la **clé** et de la **valeur** .</span><span class="sxs-lookup"><span data-stu-id="3e210-259">The `$PSBoundParameters` are displayed in the format of **Key** and **Value** .</span></span>

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a><span data-ttu-id="3e210-260">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="3e210-260">$PSCmdlet</span></span>

<span data-ttu-id="3e210-261">Contient un objet qui représente l’applet de commande ou la fonction avancée en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3e210-261">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="3e210-262">Vous pouvez utiliser les propriétés et les méthodes de l’objet dans votre applet de commande ou code de fonction pour répondre aux conditions d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="3e210-262">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="3e210-263">Par exemple, la propriété **ParameterSetName** contient le nom du jeu de paramètres en cours d’utilisation, et la méthode **ShouldProcess** ajoute les paramètres **WhatIf** et **Confirm** à l’applet de commande de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="3e210-263">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="3e210-264">Pour plus d’informations sur la `$PSCmdlet` variable automatique, consultez [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) et [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="3e210-264">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="3e210-265">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="3e210-265">$PSCommandPath</span></span>

<span data-ttu-id="3e210-266">Contient le chemin d’accès complet et le nom de fichier du script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3e210-266">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="3e210-267">Cette variable est valide dans tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="3e210-267">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="3e210-268">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="3e210-268">$PSCulture</span></span>

<span data-ttu-id="3e210-269">À compter de PowerShell 7, `$PSCulture` reflète la culture de l’instance d’exécution PowerShell actuelle (session).</span><span class="sxs-lookup"><span data-stu-id="3e210-269">Beginning in PowerShell 7, `$PSCulture` reflects the culture of the current PowerShell runspace (session).</span></span> <span data-ttu-id="3e210-270">Si la culture est modifiée dans une instance d’exécution PowerShell, la `$PSCulture` valeur de cette instance d’exécution est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="3e210-270">If the culture is changed in a PowerShell runspace, the `$PSCulture` value for that runspace is updated.</span></span>

<span data-ttu-id="3e210-271">La culture détermine le format d’affichage des éléments, tels que les nombres, les devises et les dates, et est stocké dans un objet **System. Globalization. CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="3e210-271">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="3e210-272">Utilisez `Get-Culture` pour afficher la culture de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3e210-272">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="3e210-273">`$PSCulture` contient la valeur de la propriété **Name** .</span><span class="sxs-lookup"><span data-stu-id="3e210-273">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="3e210-274">$PSDebugContext</span><span class="sxs-lookup"><span data-stu-id="3e210-274">$PSDebugContext</span></span>

<span data-ttu-id="3e210-275">Lors du débogage, cette variable contient des informations sur l’environnement de débogage.</span><span class="sxs-lookup"><span data-stu-id="3e210-275">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="3e210-276">Dans le cas contraire, elle contient une valeur **null** .</span><span class="sxs-lookup"><span data-stu-id="3e210-276">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="3e210-277">Par conséquent, vous pouvez l’utiliser pour indiquer si le débogueur contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e210-277">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="3e210-278">Lorsqu’il est rempli, il contient un objet **PSDebugContext** qui a des **points d’arrêt** et des propriétés **InvocationInfo** .</span><span class="sxs-lookup"><span data-stu-id="3e210-278">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="3e210-279">La propriété **InvocationInfo** possède plusieurs propriétés utiles, notamment la propriété **location** .</span><span class="sxs-lookup"><span data-stu-id="3e210-279">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="3e210-280">La propriété **location** indique le chemin d’accès du script en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="3e210-280">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="3e210-281">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="3e210-281">$PSHOME</span></span>

<span data-ttu-id="3e210-282">Contient le chemin d’accès complet du répertoire d’installation de PowerShell, en général, `$env:windir\System32\PowerShell\v1.0` dans les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="3e210-282">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="3e210-283">Vous pouvez utiliser cette variable dans les chemins d’accès des fichiers PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e210-283">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="3e210-284">Par exemple, la commande suivante recherche dans les rubriques d’aide conceptuelle le mot **variable** :</span><span class="sxs-lookup"><span data-stu-id="3e210-284">For example, the following command searches the conceptual Help topics for the word **variable** :</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="3e210-285">$PSItem</span><span class="sxs-lookup"><span data-stu-id="3e210-285">$PSItem</span></span>

<span data-ttu-id="3e210-286">Comme pour `$_`.</span><span class="sxs-lookup"><span data-stu-id="3e210-286">Same as `$_`.</span></span> <span data-ttu-id="3e210-287">Contient l’objet actuel dans l’objet de pipeline.</span><span class="sxs-lookup"><span data-stu-id="3e210-287">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="3e210-288">Vous pouvez utiliser cette variable dans les commandes qui exécutent une action sur chaque objet ou sur les objets sélectionnés dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="3e210-288">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="3e210-289">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="3e210-289">$PSScriptRoot</span></span>

<span data-ttu-id="3e210-290">Contient le répertoire à partir duquel un script est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3e210-290">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="3e210-291">Dans PowerShell 2,0, cette variable est valide uniquement dans les modules de script ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="3e210-291">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="3e210-292">À compter de PowerShell 3,0, il est valide dans tous les scripts.</span><span class="sxs-lookup"><span data-stu-id="3e210-292">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="3e210-293">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="3e210-293">$PSSenderInfo</span></span>

<span data-ttu-id="3e210-294">Contient des informations sur l’utilisateur qui a démarré la session PSSession, y compris l’identité de l’utilisateur et le fuseau horaire de l’ordinateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="3e210-294">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="3e210-295">Cette variable est disponible uniquement dans sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="3e210-295">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="3e210-296">La `$PSSenderInfo` variable inclut une propriété configurable par l’utilisateur, **ApplicationArguments** , qui, par défaut, contient uniquement le `$PSVersionTable` de la session d’origine.</span><span class="sxs-lookup"><span data-stu-id="3e210-296">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments** , that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="3e210-297">Pour ajouter des données à la propriété **ApplicationArguments** , utilisez le paramètre **ApplicationArguments** de l’applet de commande `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="3e210-297">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="3e210-298">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="3e210-298">$PSUICulture</span></span>

<span data-ttu-id="3e210-299">Contient le nom de la culture de l’interface utilisateur qui est actuellement utilisée dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3e210-299">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="3e210-300">La culture d'interface utilisateur détermine les chaînes de texte utilisées pour les éléments d'interface utilisateur, tels que les menus et les messages.</span><span class="sxs-lookup"><span data-stu-id="3e210-300">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="3e210-301">Il s’agit de la valeur de la propriété **System.Globalization.CultureInfo.CurrentUICulture.Name** du système.</span><span class="sxs-lookup"><span data-stu-id="3e210-301">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="3e210-302">Pour obtenir l’objet **System. Globalization. CultureInfo** du système, utilisez l' `Get-UICulture` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3e210-302">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="3e210-303">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="3e210-303">$PSVersionTable</span></span>

<span data-ttu-id="3e210-304">Contient une table de hachage en lecture seule qui affiche des détails sur la version de PowerShell en cours d’exécution dans la session active.</span><span class="sxs-lookup"><span data-stu-id="3e210-304">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="3e210-305">Le tableau comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3e210-305">The table includes the following items:</span></span>

| <span data-ttu-id="3e210-306">Propriété</span><span class="sxs-lookup"><span data-stu-id="3e210-306">Property</span></span>                  | <span data-ttu-id="3e210-307">Description</span><span class="sxs-lookup"><span data-stu-id="3e210-307">Description</span></span>                                   |
| ------------------------- | --------------------------------------------- |
| <span data-ttu-id="3e210-308">**PSVersion**</span><span class="sxs-lookup"><span data-stu-id="3e210-308">**PSVersion**</span></span>             | <span data-ttu-id="3e210-309">Numéro de version de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e210-309">The PowerShell version number</span></span>                 |
| <span data-ttu-id="3e210-310">**PSEdition**</span><span class="sxs-lookup"><span data-stu-id="3e210-310">**PSEdition**</span></span>             | <span data-ttu-id="3e210-311">Cette propriété a la valeur « Desktop » pour</span><span class="sxs-lookup"><span data-stu-id="3e210-311">This property has the value of 'Desktop' for</span></span>  |
|                           | <span data-ttu-id="3e210-312">PowerShell 4 et versions antérieures, ainsi que PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e210-312">PowerShell 4 and below as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="3e210-313">5,1 sur les éditions Windows complètes.</span><span class="sxs-lookup"><span data-stu-id="3e210-313">5.1 on full-featured Windows editions.</span></span>        |
|                           | <span data-ttu-id="3e210-314">Cette propriété a la valeur « Core » pour</span><span class="sxs-lookup"><span data-stu-id="3e210-314">This property has the value of 'Core' for</span></span>     |
|                           | <span data-ttu-id="3e210-315">PowerShell 6 et versions ultérieures, ainsi que PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e210-315">PowerShell 6 and above as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="3e210-316">PowerShell 5,1 sur les éditions à encombrement réduit</span><span class="sxs-lookup"><span data-stu-id="3e210-316">PowerShell 5.1 on reduced-footprint editions</span></span>  |
|                           | <span data-ttu-id="3e210-317">comme Windows nano Server ou Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="3e210-317">like Windows Nano Server or Windows IoT.</span></span>      |
| <span data-ttu-id="3e210-318">**GitCommitId**</span><span class="sxs-lookup"><span data-stu-id="3e210-318">**GitCommitId**</span></span>           | <span data-ttu-id="3e210-319">ID de validation des fichiers sources, dans GitHub,</span><span class="sxs-lookup"><span data-stu-id="3e210-319">The commit Id of the source files, in GitHub,</span></span> |
| <span data-ttu-id="3e210-320">**SE**</span><span class="sxs-lookup"><span data-stu-id="3e210-320">**OS**</span></span>                    | <span data-ttu-id="3e210-321">Description du système d’exploitation qui</span><span class="sxs-lookup"><span data-stu-id="3e210-321">Description of the operating system that</span></span>      |
|                           | <span data-ttu-id="3e210-322">PowerShell est en cours d’exécution sur.</span><span class="sxs-lookup"><span data-stu-id="3e210-322">PowerShell is running on.</span></span>                     |
| <span data-ttu-id="3e210-323">**Plateforme**</span><span class="sxs-lookup"><span data-stu-id="3e210-323">**Platform**</span></span>              | <span data-ttu-id="3e210-324">Plateforme exécutée par le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="3e210-324">Platform that the operating system is running</span></span> |
|                           | <span data-ttu-id="3e210-325">Activé.</span><span class="sxs-lookup"><span data-stu-id="3e210-325">on.</span></span> <span data-ttu-id="3e210-326">La valeur sur Linux et macOS est **UNIX** .</span><span class="sxs-lookup"><span data-stu-id="3e210-326">The value on Linux and macOS is **Unix** .</span></span> |
|                           | <span data-ttu-id="3e210-327">Localisez `$IsMacOs` et `$IsLinux`.</span><span class="sxs-lookup"><span data-stu-id="3e210-327">See `$IsMacOs` and `$IsLinux`.</span></span>                |
| <span data-ttu-id="3e210-328">**PSCompatibleVersions**</span><span class="sxs-lookup"><span data-stu-id="3e210-328">**PSCompatibleVersions**</span></span>  | <span data-ttu-id="3e210-329">Versions de PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="3e210-329">Versions of PowerShell that are compatible</span></span>    |
|                           | <span data-ttu-id="3e210-330">avec la version actuelle</span><span class="sxs-lookup"><span data-stu-id="3e210-330">with the current version</span></span>                      |
| <span data-ttu-id="3e210-331">**PSRemotingProtocolVersion**</span><span class="sxs-lookup"><span data-stu-id="3e210-331">**PSRemotingProtocolVersion**</span></span> | <span data-ttu-id="3e210-332">Version de PowerShell à distance</span><span class="sxs-lookup"><span data-stu-id="3e210-332">The version of the PowerShell remote</span></span>      |
|                           | <span data-ttu-id="3e210-333">Protocole de gestion.</span><span class="sxs-lookup"><span data-stu-id="3e210-333">management protocol.</span></span>                          |
| <span data-ttu-id="3e210-334">**SerializationVersion**</span><span class="sxs-lookup"><span data-stu-id="3e210-334">**SerializationVersion**</span></span>  | <span data-ttu-id="3e210-335">Version de la méthode de sérialisation</span><span class="sxs-lookup"><span data-stu-id="3e210-335">The version of the serialization method</span></span>       |
| <span data-ttu-id="3e210-336">**WSManStackVersion**</span><span class="sxs-lookup"><span data-stu-id="3e210-336">**WSManStackVersion**</span></span>     | <span data-ttu-id="3e210-337">Numéro de version de la pile de WS-Management</span><span class="sxs-lookup"><span data-stu-id="3e210-337">The version number of the WS-Management stack</span></span> |

### <a name="pwd"></a><span data-ttu-id="3e210-338">$PWD</span><span class="sxs-lookup"><span data-stu-id="3e210-338">$PWD</span></span>

<span data-ttu-id="3e210-339">Contient un objet de chemin d’accès qui représente le chemin d’accès complet du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3e210-339">Contains a path object that represents the full path of the current directory.</span></span>

### <a name="sender"></a><span data-ttu-id="3e210-340">$Sender</span><span class="sxs-lookup"><span data-stu-id="3e210-340">$Sender</span></span>

<span data-ttu-id="3e210-341">Contient l’objet qui a généré cet événement.</span><span class="sxs-lookup"><span data-stu-id="3e210-341">Contains the object that generated this event.</span></span> <span data-ttu-id="3e210-342">Cette variable est remplie uniquement dans le bloc d’action d’une commande d’inscription d’événement.</span><span class="sxs-lookup"><span data-stu-id="3e210-342">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="3e210-343">La valeur de cette variable peut également se trouver dans la propriété sender de l’objet **PSEventArgs** qui `Get-Event` retourne.</span><span class="sxs-lookup"><span data-stu-id="3e210-343">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="3e210-344">$ShellId</span><span class="sxs-lookup"><span data-stu-id="3e210-344">$ShellId</span></span>

<span data-ttu-id="3e210-345">Contient l’identificateur de l’interpréteur de commandes actuel.</span><span class="sxs-lookup"><span data-stu-id="3e210-345">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="3e210-346">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="3e210-346">$StackTrace</span></span>

<span data-ttu-id="3e210-347">Contient une trace de la pile de l’erreur la plus récente.</span><span class="sxs-lookup"><span data-stu-id="3e210-347">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="3e210-348">$switch</span><span class="sxs-lookup"><span data-stu-id="3e210-348">$switch</span></span>

<span data-ttu-id="3e210-349">Contient l’énumérateur qui ne correspond pas aux valeurs résultantes d’une `Switch` instruction.</span><span class="sxs-lookup"><span data-stu-id="3e210-349">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="3e210-350">La `$switch` variable existe uniquement lorsque l' `Switch` instruction est en cours d’exécution ; elle est supprimée à la fin de l’exécution de l' `switch` instruction.</span><span class="sxs-lookup"><span data-stu-id="3e210-350">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="3e210-351">Pour plus d’informations, consultez [about_Switch](about_Switch.md).</span><span class="sxs-lookup"><span data-stu-id="3e210-351">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="3e210-352">Les énumérateurs contiennent des propriétés et des méthodes que vous pouvez utiliser pour récupérer des valeurs de boucle et modifier l’itération de boucle actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-352">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="3e210-353">Pour plus d’informations, consultez [utilisation d’énumérateurs](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="3e210-353">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="3e210-354">$this</span><span class="sxs-lookup"><span data-stu-id="3e210-354">$this</span></span>

<span data-ttu-id="3e210-355">Dans un bloc de script qui définit une propriété de script ou une méthode de script, la `$this` variable fait référence à l’objet qui est étendu.</span><span class="sxs-lookup"><span data-stu-id="3e210-355">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="3e210-356">Dans une classe personnalisée, la `$this` variable fait référence à l’objet de classe lui-même autorisant l’accès aux propriétés et méthodes définies dans la classe.</span><span class="sxs-lookup"><span data-stu-id="3e210-356">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="3e210-357">$true</span><span class="sxs-lookup"><span data-stu-id="3e210-357">$true</span></span>

<span data-ttu-id="3e210-358">Contient la **valeur true** .</span><span class="sxs-lookup"><span data-stu-id="3e210-358">Contains **True** .</span></span> <span data-ttu-id="3e210-359">Vous pouvez utiliser cette variable pour représenter la **valeur true** dans les commandes et les scripts.</span><span class="sxs-lookup"><span data-stu-id="3e210-359">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="3e210-360">Utilisation d’énumérateurs</span><span class="sxs-lookup"><span data-stu-id="3e210-360">Using Enumerators</span></span>

<span data-ttu-id="3e210-361">Les `$input` `$foreach` variables, et `$switch` sont tous des énumérateurs utilisés pour itérer au sein des valeurs traitées par leur bloc de code conteneur.</span><span class="sxs-lookup"><span data-stu-id="3e210-361">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="3e210-362">Un énumérateur contient des propriétés et des méthodes que vous pouvez utiliser pour avancer ou réinitialiser une itération, ou pour récupérer des valeurs d’itération.</span><span class="sxs-lookup"><span data-stu-id="3e210-362">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="3e210-363">La manipulation directe d’énumérateurs n’est pas considérée comme meilleure pratique.</span><span class="sxs-lookup"><span data-stu-id="3e210-363">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="3e210-364">Dans les boucles, les mots clés de contrôle de workflow [break](about_Break.md) et [continue](about_Continue.md) doivent être préférés.</span><span class="sxs-lookup"><span data-stu-id="3e210-364">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="3e210-365">Dans les fonctions qui acceptent l’entrée de pipeline, il est recommandé d’utiliser des paramètres avec les attributs **ValueFromPipeline** ou **ValueFromPipelineByPropertyName** .</span><span class="sxs-lookup"><span data-stu-id="3e210-365">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="3e210-366">Pour plus d’informations, consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3e210-366">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="3e210-367">MoveNext</span><span class="sxs-lookup"><span data-stu-id="3e210-367">MoveNext</span></span>

<span data-ttu-id="3e210-368">La méthode [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) avance l’énumérateur à l’élément suivant de la collection.</span><span class="sxs-lookup"><span data-stu-id="3e210-368">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="3e210-369">**MoveNext** retourne **true** si l’énumérateur a été avancé avec succès, **false** si l’énumérateur a dépassé la fin de la collection.</span><span class="sxs-lookup"><span data-stu-id="3e210-369">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="3e210-370">La valeur **booléenne** retournée par mon **MoveNext** est envoyée au flux de sortie.</span><span class="sxs-lookup"><span data-stu-id="3e210-370">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="3e210-371">Vous pouvez supprimer la sortie en la cast ou en la `[void]` canalisant vers [out-NULL](xref:Microsoft.PowerShell.Core.Out-Null).</span><span class="sxs-lookup"><span data-stu-id="3e210-371">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="3e210-372">Réinitialiser</span><span class="sxs-lookup"><span data-stu-id="3e210-372">Reset</span></span>

<span data-ttu-id="3e210-373">La méthode [Reset](/dotnet/api/system.collections.ienumerator.reset) affecte à l’énumérateur sa position initiale, qui **précède** le premier élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="3e210-373">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="3e210-374">Actuel</span><span class="sxs-lookup"><span data-stu-id="3e210-374">Current</span></span>

<span data-ttu-id="3e210-375">La propriété [actuelle](/dotnet/api/system.collections.ienumerator.current) obtient l’élément dans la collection, ou le pipeline, à la position actuelle de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="3e210-375">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="3e210-376">La propriété **actuelle** continue à retourner la même propriété jusqu’à ce que **MoveNext** soit appelé.</span><span class="sxs-lookup"><span data-stu-id="3e210-376">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="3e210-377">Exemples</span><span class="sxs-lookup"><span data-stu-id="3e210-377">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="3e210-378">Exemple 1 : utilisation de la variable $input</span><span class="sxs-lookup"><span data-stu-id="3e210-378">Example 1: Using the $input variable</span></span>

<span data-ttu-id="3e210-379">Dans l’exemple suivant, l’accès à la `$input` variable efface la variable jusqu’à la prochaine exécution du bloc de processus.</span><span class="sxs-lookup"><span data-stu-id="3e210-379">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="3e210-380">L’utilisation de la méthode **Reset** réinitialise la `$input` variable à la valeur de pipeline actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e210-380">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

<span data-ttu-id="3e210-381">Le bloc de processus avance automatiquement la `$input` variable même si vous n’y accédez pas.</span><span class="sxs-lookup"><span data-stu-id="3e210-381">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="3e210-382">Exemple 2 : utilisation de $input en dehors du bloc Process</span><span class="sxs-lookup"><span data-stu-id="3e210-382">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="3e210-383">En dehors du bloc de processus `$input` , la variable représente toutes les valeurs redirigées dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="3e210-383">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="3e210-384">L’accès à la `$input` variable efface toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="3e210-384">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="3e210-385">La méthode **Reset** réinitialise l’ensemble de la collection.</span><span class="sxs-lookup"><span data-stu-id="3e210-385">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="3e210-386">La propriété **actuelle** n’est jamais remplie.</span><span class="sxs-lookup"><span data-stu-id="3e210-386">The **Current** property is never populated.</span></span>
- <span data-ttu-id="3e210-387">La méthode **MoveNext** retourne la valeur false, car la collection ne peut pas être avancée.</span><span class="sxs-lookup"><span data-stu-id="3e210-387">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="3e210-388">L’appel de **MoveNext** efface la `$input` variable.</span><span class="sxs-lookup"><span data-stu-id="3e210-388">Calling **MoveNext** clears out the `$input` variable.</span></span>

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="3e210-389">Exemple 3 : utilisation de l' $input. Propriété actuelle</span><span class="sxs-lookup"><span data-stu-id="3e210-389">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="3e210-390">À l’aide de la propriété **Current** , la valeur de pipeline actuelle est accessible plusieurs fois sans utiliser la méthode **Reset** .</span><span class="sxs-lookup"><span data-stu-id="3e210-390">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="3e210-391">Le bloc Process n’appelle pas automatiquement la méthode **MoveNext** .</span><span class="sxs-lookup"><span data-stu-id="3e210-391">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="3e210-392">La propriété **actuelle** ne sera jamais remplie, sauf si vous appelez explicitement **MoveNext** .</span><span class="sxs-lookup"><span data-stu-id="3e210-392">The **Current** property will never be populated unless you explicitly call **MoveNext** .</span></span> <span data-ttu-id="3e210-393">La propriété **actuelle** est accessible plusieurs fois dans le bloc de processus sans effacer sa valeur.</span><span class="sxs-lookup"><span data-stu-id="3e210-393">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="3e210-394">Exemple 4 : utilisation de la variable $foreach</span><span class="sxs-lookup"><span data-stu-id="3e210-394">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="3e210-395">Contrairement `$input` à la variable, la `$foreach` variable représente toujours tous les éléments de la collection lorsque vous y accédez directement.</span><span class="sxs-lookup"><span data-stu-id="3e210-395">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="3e210-396">Utilisez la propriété **Current** pour accéder à l’élément de collection actuel, et les méthodes **Reset** et **MoveNext** pour modifier sa valeur.</span><span class="sxs-lookup"><span data-stu-id="3e210-396">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="3e210-397">Chaque itération de la `foreach` boucle appellera automatiquement la méthode **MoveNext** .</span><span class="sxs-lookup"><span data-stu-id="3e210-397">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="3e210-398">La boucle suivante s’exécute deux fois seulement.</span><span class="sxs-lookup"><span data-stu-id="3e210-398">The following loop only executes twice.</span></span> <span data-ttu-id="3e210-399">Dans la deuxième itération, la collection est déplacée vers le troisième élément avant la fin de l’itération.</span><span class="sxs-lookup"><span data-stu-id="3e210-399">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="3e210-400">Après la deuxième itération, il n’y a plus aucune valeur à itérer, et la boucle se termine.</span><span class="sxs-lookup"><span data-stu-id="3e210-400">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="3e210-401">La propriété **MoveNext** n’affecte pas la variable choisie pour itérer au sein de la collection ( `$Num` ).</span><span class="sxs-lookup"><span data-stu-id="3e210-401">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

<span data-ttu-id="3e210-402">L’utilisation de la méthode **Reset** réinitialise l’élément actuel dans la collection.</span><span class="sxs-lookup"><span data-stu-id="3e210-402">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="3e210-403">L’exemple suivant effectue une boucle à deux **reprises** sur les deux premiers éléments, car la méthode de **réinitialisation** est appelée.</span><span class="sxs-lookup"><span data-stu-id="3e210-403">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="3e210-404">Après les deux premières boucles, l' `if` instruction échoue et la boucle itère les trois éléments normalement.</span><span class="sxs-lookup"><span data-stu-id="3e210-404">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e210-405">Cela peut entraîner une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="3e210-405">This could result in an infinite loop.</span></span>

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="3e210-406">Exemple 5 : utilisation de la variable $switch</span><span class="sxs-lookup"><span data-stu-id="3e210-406">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="3e210-407">La `$switch` variable a exactement les mêmes règles que la `$foreach` variable.</span><span class="sxs-lookup"><span data-stu-id="3e210-407">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="3e210-408">L’exemple suivant illustre tous les concepts de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="3e210-408">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="3e210-409">Notez que le cas **NotEvaluated** n’est jamais exécuté, même s’il n’y a pas d' `break` instruction après la méthode **MoveNext** .</span><span class="sxs-lookup"><span data-stu-id="3e210-409">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a><span data-ttu-id="3e210-410">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e210-410">See also</span></span>

[<span data-ttu-id="3e210-411">about_Functions</span><span class="sxs-lookup"><span data-stu-id="3e210-411">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="3e210-412">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="3e210-412">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="3e210-413">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="3e210-413">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="3e210-414">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="3e210-414">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="3e210-415">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="3e210-415">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="3e210-416">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="3e210-416">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="3e210-417">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="3e210-417">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="3e210-418">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="3e210-418">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="3e210-419">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="3e210-419">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="3e210-420">about_Variables</span><span class="sxs-lookup"><span data-stu-id="3e210-420">about_Variables</span></span>](about_Variables.md)
