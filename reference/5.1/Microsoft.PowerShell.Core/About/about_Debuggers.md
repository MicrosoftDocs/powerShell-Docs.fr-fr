---
description: Décrit le débogueur PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: d3353a9c684091b17f496e15f1553c860d26e973
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208057"
---
# <a name="about-debuggers"></a><span data-ttu-id="a4fd5-104">À propos des débogueurs</span><span class="sxs-lookup"><span data-stu-id="a4fd5-104">About Debuggers</span></span>

## <a name="short-description"></a><span data-ttu-id="a4fd5-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="a4fd5-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a4fd5-106">Décrit le débogueur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-106">Describes the PowerShell debugger.</span></span>

## <a name="long-description"></a><span data-ttu-id="a4fd5-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="a4fd5-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a4fd5-108">Le débogage est le processus qui consiste à examiner un script pendant qu’il est en cours d’exécution pour identifier et corriger les erreurs dans les instructions de script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-108">Debugging is the process of examining a script while it is running to identify and correct errors in the script instructions.</span></span> <span data-ttu-id="a4fd5-109">Le débogueur PowerShell peut vous aider à examiner et à identifier les erreurs et les inefficacités dans vos scripts, fonctions, commandes, workflows PowerShell, configurations DSC (Desired State Configuration) PowerShell ou expressions.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-109">The PowerShell debugger can help you examine and identify errors and inefficiencies in your scripts, functions, commands, PowerShell workflows, PowerShell Desired State Configuration (DSC) configurations, or expressions.</span></span>

<span data-ttu-id="a4fd5-110">À compter de PowerShell 5,0, le débogueur PowerShell a été mis à jour pour déboguer les scripts, les fonctions, les flux de travail, les commandes, les configurations ou les expressions qui s’exécutent dans la console ou Windows PowerShell ISE sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-110">Starting in PowerShell 5.0, the PowerShell debugger has been updated to debug scripts, functions, workflows, commands, configurations, or expressions that are running in either the console or Windows PowerShell ISE on remote computers.</span></span> <span data-ttu-id="a4fd5-111">Vous pouvez exécuter `Enter-PSSession` pour démarrer une session PowerShell à distance interactive dans laquelle vous pouvez définir des points d’arrêt et déboguer des fichiers de script et des commandes sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-111">You can run `Enter-PSSession` to start an interactive remote PowerShell session in which you can set breakpoints and debug script files and commands on the remote computer.</span></span> <span data-ttu-id="a4fd5-112">`Enter-PSSession` la fonctionnalité a été mise à jour pour vous permettre de vous reconnecter à et d’entrer dans une session déconnectée qui exécute un script ou une commande sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-112">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running a script or command on a remote computer.</span></span> <span data-ttu-id="a4fd5-113">Si le script en cours d’exécution atteint un point d’arrêt, votre session cliente démarre automatiquement le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-113">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span> <span data-ttu-id="a4fd5-114">Si la session déconnectée qui exécute un script a déjà atteint un point d’arrêt et qu’elle est arrêtée au point d’arrêt, `Enter-PSSession` démarre automatiquement le débogueur de ligne de commande après la reconnexion à la session.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-114">If the disconnected session that is running a script has already hit a breakpoint, and is stopped at the breakpoint, `Enter-PSSession` automatically starts the command-line debugger, after you reconnect to the session.</span></span>

<span data-ttu-id="a4fd5-115">Le débogueur PowerShell peut également être utilisé pour déboguer des flux de travail PowerShell, soit dans la console PowerShell, soit dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-115">The PowerShell debugger can also be used to debug PowerShell workflows, in either the PowerShell console, or in Windows PowerShell ISE.</span></span> <span data-ttu-id="a4fd5-116">À compter de PowerShell 5,0, vous pouvez effectuer un débogage dans des travaux ou processus en cours d’exécution, localement ou à distance.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-116">Starting in PowerShell 5.0, you can debug within running jobs or processes, either locally or remotely.</span></span>

<span data-ttu-id="a4fd5-117">Vous pouvez utiliser les fonctionnalités du débogueur PowerShell pour examiner un script, une fonction, une commande, un flux de travail ou une expression PowerShell pendant son exécution.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-117">You can use the features of the PowerShell debugger to examine a PowerShell script, function, command, workflow, or expression while it is running.</span></span> <span data-ttu-id="a4fd5-118">Le débogueur PowerShell comprend un ensemble d’applets de commande qui vous permettent de définir des points d’arrêt, de gérer des points d’arrêt et d’afficher la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-118">The PowerShell debugger includes a set of cmdlets that let you set breakpoints, manage breakpoints, and view the call stack.</span></span>

## <a name="debugger-cmdlets"></a><span data-ttu-id="a4fd5-119">Applets de commande du débogueur</span><span class="sxs-lookup"><span data-stu-id="a4fd5-119">Debugger Cmdlets</span></span>

<span data-ttu-id="a4fd5-120">Le débogueur PowerShell comprend l’ensemble d’applets de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-120">The PowerShell debugger includes the following set of cmdlets:</span></span>

- <span data-ttu-id="a4fd5-121">`Set-PSBreakpoint`: Définit les points d’arrêt sur les lignes, les variables et les commandes.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-121">`Set-PSBreakpoint`: Sets breakpoints on lines, variables, and commands.</span></span>
- <span data-ttu-id="a4fd5-122">`Get-PSBreakpoint`: Obtient les points d’arrêt de la session active.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-122">`Get-PSBreakpoint`: Gets breakpoints in the current session.</span></span>
- <span data-ttu-id="a4fd5-123">`Disable-PSBreakpoint`: Désactive les points d’arrêt dans la session active.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-123">`Disable-PSBreakpoint`: Turns off breakpoints in the current session.</span></span>
- <span data-ttu-id="a4fd5-124">`Enable-PSBreakpoint`: Réactive les points d’arrêt dans la session active.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-124">`Enable-PSBreakpoint`: Re-enables breakpoints in the current session.</span></span>
- <span data-ttu-id="a4fd5-125">`Remove-PSBreakpoint`: Supprime les points d’arrêt de la session active.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-125">`Remove-PSBreakpoint`: Deletes breakpoints from the current session.</span></span>
- <span data-ttu-id="a4fd5-126">`Get-PSCallStack`: Affiche la pile des appels actuelle.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-126">`Get-PSCallStack`: Displays the current call stack.</span></span>

## <a name="starting-and-stopping-the-debugger"></a><span data-ttu-id="a4fd5-127">Démarrage et arrêt du débogueur</span><span class="sxs-lookup"><span data-stu-id="a4fd5-127">Starting and Stopping the Debugger</span></span>

<span data-ttu-id="a4fd5-128">Pour démarrer le débogueur, définissez un ou plusieurs points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-128">To start the debugger, set one or more breakpoints.</span></span> <span data-ttu-id="a4fd5-129">Ensuite, exécutez le script, la commande ou la fonction que vous souhaitez déboguer.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-129">Then, run the script, command, or function that you want to debug.</span></span>

<span data-ttu-id="a4fd5-130">Quand vous atteignez un point d’arrêt, l’exécution s’arrête et le contrôle est réactivé sur le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-130">When you reach a breakpoint, execution stops, and control is turned over to the debugger.</span></span>

<span data-ttu-id="a4fd5-131">Pour arrêter le débogueur, exécutez le script, la commande ou la fonction jusqu’à ce qu’elle soit terminée.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-131">To stop the debugger, run the script, command, or function until it is complete.</span></span> <span data-ttu-id="a4fd5-132">Ou, tapez `stop` ou `t` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-132">Or, type `stop` or `t`.</span></span>

### <a name="debugger-commands"></a><span data-ttu-id="a4fd5-133">Commandes du débogueur</span><span class="sxs-lookup"><span data-stu-id="a4fd5-133">Debugger Commands</span></span>

<span data-ttu-id="a4fd5-134">Lorsque vous utilisez le débogueur dans la console PowerShell, utilisez les commandes suivantes pour contrôler l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-134">When you use the debugger in the PowerShell console, use the following commands to control the execution.</span></span> <span data-ttu-id="a4fd5-135">Dans Windows PowerShell ISE, utilisez les commandes du menu Déboguer.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-135">In Windows PowerShell ISE, use commands on the Debug menu.</span></span>

<span data-ttu-id="a4fd5-136">Remarque : pour plus d’informations sur l’utilisation du débogueur dans d’autres applications hôtes, consultez la documentation de l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-136">Note: For information about how to use the debugger in other host applications, see the host application documentation.</span></span>

- <span data-ttu-id="a4fd5-137">`s`, `StepInto` : Exécute l’instruction suivante, puis s’arrête.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-137">`s`, `StepInto`: Executes the next statement and then stops.</span></span>

- <span data-ttu-id="a4fd5-138">`v`, `StepOver` : Exécute l’instruction suivante, mais ignore les fonctions et les appels.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-138">`v`, `StepOver`: Executes the next statement, but skips functions and invocations.</span></span> <span data-ttu-id="a4fd5-139">Les instructions ignorées sont exécutées, mais sans pas à pas.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-139">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="a4fd5-140">`Ctrl+Break`: (Arrêter tout dans ISE) s’arrête dans un script en cours d’exécution dans la console PowerShell ou Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-140">`Ctrl+Break`: (Break All in ISE) Breaks into a running script within either the PowerShell console, or Windows PowerShell ISE.</span></span> <span data-ttu-id="a4fd5-141">Notez que la <kbd>touche Ctrl</kbd> + <kbd>Break</kbd> dans Windows PowerShell 2,0, 3,0 et 4,0 ferme le programme.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-141">Note that <kbd>Ctrl</kbd>+<kbd>Break</kbd> in Windows PowerShell 2.0, 3.0, and 4.0 closes the program.</span></span> <span data-ttu-id="a4fd5-142">L’instruction Break All fonctionne sur les scripts locaux et distants, en cours d’exécution de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-142">Break All works on both local and remote interactively-running scripts.</span></span>

- <span data-ttu-id="a4fd5-143">`o`, `StepOut` : Pas à pas sortant de la fonction active ; un niveau vers le haut en cas d’imbrication.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-143">`o`, `StepOut`: Steps out of the current function; up one level if nested.</span></span> <span data-ttu-id="a4fd5-144">S’il se trouve dans le corps principal, il continue jusqu’à la fin ou jusqu’au point d’arrêt suivant.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-144">If in the main body, it continues to the end or the next breakpoint.</span></span> <span data-ttu-id="a4fd5-145">Les instructions ignorées sont exécutées, mais sans pas à pas.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-145">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="a4fd5-146">`c`, `Continue` : Continue à s’exécuter jusqu’à ce que le script soit terminé ou jusqu’à ce que le point d’arrêt suivant soit atteint.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-146">`c`, `Continue`: Continues to run until the script is complete or until the next breakpoint is reached.</span></span> <span data-ttu-id="a4fd5-147">Les instructions ignorées sont exécutées, mais sans pas à pas.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-147">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="a4fd5-148">`l`, `List` : Affiche la partie du script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-148">`l`, `List`: Displays the part of the script that is executing.</span></span> <span data-ttu-id="a4fd5-149">Par défaut, il affiche la ligne active, cinq lignes précédentes et 10 lignes suivantes.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-149">By default, it displays the current line, five previous lines, and 10 subsequent lines.</span></span>
  <span data-ttu-id="a4fd5-150">Pour continuer à répertorier le script, appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-150">To continue listing the script, press ENTER.</span></span>

- <span data-ttu-id="a4fd5-151">`l <m>`, `List` : Affiche 16 lignes du script en commençant par le numéro de ligne spécifié par `<m>` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-151">`l <m>`, `List`: Displays 16 lines of the script beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="a4fd5-152">`l <m> <n>`, `List` : Affiche les `<n>` lignes du script, en commençant par le numéro de ligne spécifié par `<m>` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-152">`l <m> <n>`, `List`: Displays `<n>` lines of the script, beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="a4fd5-153">`q`, `Stop` , `Exit` : Arrête l’exécution du script et quitte le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-153">`q`, `Stop`, `Exit`: Stops executing the script, and exits the debugger.</span></span> <span data-ttu-id="a4fd5-154">Si vous déboguez un travail en exécutant l' `Debug-Job` applet de commande, la `Exit` commande détache le débogueur et autorise la poursuite de l’exécution du travail.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-154">If you are debugging a job by running the `Debug-Job` cmdlet, the `Exit` command detaches the debugger, and allows the job to continue running.</span></span>

- <span data-ttu-id="a4fd5-155">`k`, `Get-PsCallStack` : Affiche la pile des appels actuelle.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-155">`k`, `Get-PsCallStack`: Displays the current call stack.</span></span>

- <span data-ttu-id="a4fd5-156">`<Enter>`: Répète la dernière commande s’il s’agissait d’une ou plusieurs étapes, d’un décalage de passe (v) ou d’une liste (l).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-156">`<Enter>`: Repeats the last command if it was Step (s), StepOver (v), or List (l).</span></span> <span data-ttu-id="a4fd5-157">Sinon, représente une action d’envoi.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-157">Otherwise, represents a submit action.</span></span>

- <span data-ttu-id="a4fd5-158">`?`, `h` : Affiche l’aide de la commande du débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-158">`?`, `h`: Displays the debugger command Help.</span></span>

<span data-ttu-id="a4fd5-159">Pour quitter le débogueur, vous pouvez utiliser stop (q).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-159">To exit the debugger, you can use Stop (q).</span></span>

<span data-ttu-id="a4fd5-160">À compter de PowerShell 5,0, vous pouvez exécuter la commande exit pour quitter une session de débogage imbriquée que vous avez démarrée en exécutant `Debug-Job` ou `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-160">Starting in PowerShell 5.0, you can run the Exit command to exit a nested debugging session that you started by running either `Debug-Job` or `Debug-Runspace`.</span></span>

<span data-ttu-id="a4fd5-161">À l’aide de ces commandes du débogueur, vous pouvez exécuter un script, l’arrêter à un point de préoccupation, examiner les valeurs des variables et l’état du système, et continuer à exécuter le script jusqu’à ce que vous ayez identifié un problème.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-161">By using these debugger commands, you can run a script, stop on a point of concern, examine the values of variables and the state of the system, and continue running the script until you have identified a problem.</span></span>

<span data-ttu-id="a4fd5-162">Remarque : Si vous exécutez pas à pas une instruction avec un opérateur de redirection, tel que « > », le débogueur PowerShell parcourt toutes les instructions restantes dans le script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-162">NOTE: If you step into a statement with a redirection operator, such as ">", the PowerShell debugger steps over all remaining statements in the script.</span></span>

<span data-ttu-id="a4fd5-163">Affichage des valeurs des variables de script</span><span class="sxs-lookup"><span data-stu-id="a4fd5-163">Displaying the Values of script Variables</span></span>

<span data-ttu-id="a4fd5-164">Lorsque vous êtes dans le débogueur, vous pouvez également entrer des commandes, afficher la valeur des variables, utiliser des applets de commande et exécuter des scripts sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-164">While you are in the debugger, you can also enter commands, display the value of variables, use cmdlets, and run scripts at the command line.</span></span>

<span data-ttu-id="a4fd5-165">Vous pouvez afficher la valeur actuelle de toutes les variables dans le script en cours de débogage, à l’exception des variables automatiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-165">You can display the current value of all variables in the script that is being debugged, except for the following automatic variables:</span></span>

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

<span data-ttu-id="a4fd5-166">Si vous essayez d’afficher la valeur d’une de ces variables, vous l’obtenez pour un pipeline interne que le débogueur utilise, pas la valeur de la variable dans le script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-166">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span>

<span data-ttu-id="a4fd5-167">Pour afficher la valeur de ces variables pour le script en cours de débogage, dans le script, affectez la valeur de la variable automatique à une nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-167">To display the value these variables for the script that is being debugged, in the script, assign the value of the automatic variable to a new variable.</span></span> <span data-ttu-id="a4fd5-168">Vous pouvez ensuite afficher la valeur de la nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-168">Then you can display the value of the new variable.</span></span>

<span data-ttu-id="a4fd5-169">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="a4fd5-169">For example,</span></span>

```powershell
$scriptArgs = $Args
$scriptArgs
```

<span data-ttu-id="a4fd5-170">Dans l’exemple de cette rubrique, la valeur de la `$MyInvocation` variable est réassignée comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-170">In the example in this topic, the value of the `$MyInvocation` variable is reassigned as follows:</span></span>

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a><span data-ttu-id="a4fd5-171">Environnement du débogueur</span><span class="sxs-lookup"><span data-stu-id="a4fd5-171">The Debugger Environment</span></span>

<span data-ttu-id="a4fd5-172">Quand vous atteignez un point d’arrêt, vous entrez l’environnement du débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-172">When you reach a breakpoint, you enter the debugger environment.</span></span> <span data-ttu-id="a4fd5-173">L’invite de commandes change de sorte qu’elle commence par « [DBG] : ».</span><span class="sxs-lookup"><span data-stu-id="a4fd5-173">The command prompt changes so that it begins with "[DBG]:".</span></span> <span data-ttu-id="a4fd5-174">Si vous déboguez un flux de travail, l’invite est « [WFDBG] ».</span><span class="sxs-lookup"><span data-stu-id="a4fd5-174">If you are debugging a workflow, the prompt is "[WFDBG]".</span></span> <span data-ttu-id="a4fd5-175">Vous pouvez personnaliser l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-175">You can customize the prompt.</span></span>

<span data-ttu-id="a4fd5-176">Pour plus d’informations sur la personnalisation de l’invite, consultez [about_Prompts](about_prompts.md).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-176">For more information about customizing the prompt, see [about_Prompts](about_prompts.md).</span></span>

<span data-ttu-id="a4fd5-177">En outre, dans certaines applications hôtes, telles que la console PowerShell (mais pas dans Environnement d’écriture de scripts intégré de Windows PowerShell [ISE]), une invite imbriquée s’ouvre pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-177">Also, in some host applications, such as the PowerShell console, (but not in Windows PowerShell Integrated Scripting Environment [ISE]), a nested prompt opens for debugging.</span></span> <span data-ttu-id="a4fd5-178">Vous pouvez détecter l’invite imbriquée par les caractères supérieurs à répétitifs (ASCII 62) qui s’affichent à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-178">You can detect the nested prompt by the repeating greater-than characters (ASCII 62) that appear at the command prompt.</span></span>

<span data-ttu-id="a4fd5-179">Par exemple, voici l’invite de débogage par défaut dans la console PowerShell :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-179">For example, the following is the default debugging prompt in the PowerShell console:</span></span>

```
[DBG]: PS (get-location)>>>
```

<span data-ttu-id="a4fd5-180">Vous pouvez rechercher le niveau d’imbrication à l’aide de la `$NestedPromptLevel` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-180">You can find the nesting level by using the `$NestedPromptLevel` automatic variable.</span></span>

<span data-ttu-id="a4fd5-181">En outre, une variable automatique, `$PSDebugContext` , est définie dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-181">Additionally, an automatic variable, `$PSDebugContext`, is defined in the local scope.</span></span> <span data-ttu-id="a4fd5-182">Vous pouvez utiliser la présence de la `$PsDebugContext` variable pour déterminer si vous êtes dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-182">You can use the presence of the `$PsDebugContext` variable to determine whether you are in the debugger.</span></span>

<span data-ttu-id="a4fd5-183">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-183">For example:</span></span>

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

<span data-ttu-id="a4fd5-184">Vous pouvez utiliser la valeur de la `$PSDebugContext` variable dans votre débogage.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-184">You can use the value of the `$PSDebugContext` variable in your debugging.</span></span>

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a><span data-ttu-id="a4fd5-185">Débogage et portée</span><span class="sxs-lookup"><span data-stu-id="a4fd5-185">Debugging and Scope</span></span>

<span data-ttu-id="a4fd5-186">L’arrêt dans le débogueur ne modifie pas l’étendue dans laquelle vous travaillez, mais quand vous atteignez un point d’arrêt dans un script, vous passez dans la portée du script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-186">Breaking into the debugger does not change the scope in which you are operating, but when you reach a breakpoint in a script, you move into the script scope.</span></span> <span data-ttu-id="a4fd5-187">La portée du script est un enfant de l’étendue dans laquelle vous avez exécuté le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-187">The script scope is a child of the scope in which you ran the debugger.</span></span>

<span data-ttu-id="a4fd5-188">Pour rechercher les variables et les alias définis dans la portée du script, utilisez le paramètre scope des `Get-Alias` applets de commande ou `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-188">To find the variables and aliases that are defined in the script scope, use the Scope parameter of the `Get-Alias` or `Get-Variable` cmdlets.</span></span>

<span data-ttu-id="a4fd5-189">Par exemple, la commande suivante obtient les variables dans l’étendue locale (script) :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-189">For example, the following command gets the variables in the local (script) scope:</span></span>

```powershell
Get-Variable -scope 0
```

<span data-ttu-id="a4fd5-190">Vous pouvez abréger la commande comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-190">You can abbreviate the command as:</span></span>

```powershell
gv -s 0
```

<span data-ttu-id="a4fd5-191">Il s’agit d’une méthode utile pour afficher uniquement les variables que vous avez définies dans le script et que vous avez définies pendant le débogage.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-191">This is a useful way to see only the variables that you defined in the script and that you defined while debugging.</span></span>

<span data-ttu-id="a4fd5-192">Débogage à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a4fd5-192">Debugging at the Command Line</span></span>

<span data-ttu-id="a4fd5-193">Quand vous définissez un point d’arrêt sur variable ou un point d’arrêt de commande, vous pouvez définir le point d’arrêt uniquement dans un fichier de script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-193">When you set a variable breakpoint or a command breakpoint, you can set the breakpoint only in a script file.</span></span> <span data-ttu-id="a4fd5-194">Toutefois, par défaut, le point d’arrêt est défini sur tout ce qui s’exécute dans la session active.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-194">However, by default, the breakpoint is set on anything that runs in the current session.</span></span>

<span data-ttu-id="a4fd5-195">Par exemple, si vous définissez un point d’arrêt sur la `$name` variable, le débogueur s’arrête sur toute `$name` variable d’un script, d’une commande, d’une fonction, d’une applet de commande de script ou d’une expression que vous exécutez jusqu’à ce que vous désactiviez ou supprimiez le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-195">For example, if you set a breakpoint on the `$name` variable, the debugger breaks on any `$name` variable in any script, command, function, script cmdlet or expression that you run until you disable or remove the breakpoint.</span></span>

<span data-ttu-id="a4fd5-196">Cela vous permet de déboguer vos scripts dans un contexte plus réaliste dans lequel ils peuvent être affectés par des fonctions, des variables et d’autres scripts dans la session et dans le profil de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-196">This allows you to debug your scripts in a more realistic context in which they might be affected by functions, variables, and other scripts in the session and in the user's profile.</span></span>

<span data-ttu-id="a4fd5-197">Les points d’arrêt de ligne étant spécifiques aux fichiers de script, ils sont définis uniquement dans les fichiers de script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-197">Line breakpoints are specific to script files, so they are set only in script files.</span></span>

## <a name="debugging-workflows"></a><span data-ttu-id="a4fd5-198">Débogage de workflows</span><span class="sxs-lookup"><span data-stu-id="a4fd5-198">Debugging Workflows</span></span>

<span data-ttu-id="a4fd5-199">Le débogueur PowerShell 4,0 peut être utilisé pour déboguer des flux de travail PowerShell, soit dans la console PowerShell, soit dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-199">The PowerShell 4.0 debugger can be used to debug PowerShell workflows, either in the PowerShell console, or in Windows PowerShell ISE.</span></span> <span data-ttu-id="a4fd5-200">L’utilisation du débogueur PowerShell pour déboguer des flux de travail présente certaines limites.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-200">There are some limitations with using the PowerShell debugger to debug workflows.</span></span>

- <span data-ttu-id="a4fd5-201">Vous pouvez afficher les variables de flux de travail lorsque vous êtes dans le débogueur, mais la définition de variables de workflow à partir du débogueur n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-201">You can view workflow variables while you are in the debugger, but setting workflow variables from within the debugger is not supported.</span></span>
- <span data-ttu-id="a4fd5-202">La saisie semi-automatique via la touche Tab lorsqu’elle est arrêtée dans le débogueur de workflow n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-202">Tab completion when stopped in the workflow debugger is not available.</span></span>
- <span data-ttu-id="a4fd5-203">Le débogage de workflow fonctionne uniquement avec l’exécution synchrone de flux de travail à partir d’un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-203">Workflow debugging works only with synchronous running of workflows from a PowerShell script.</span></span> <span data-ttu-id="a4fd5-204">Vous ne pouvez pas déboguer des workflows s’ils s’exécutent en tant que travail (avec le paramètre **AsJob** ).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-204">You cannot debug workflows if they are running as a job (with the **AsJob** parameter).</span></span>
- <span data-ttu-id="a4fd5-205">D’autres scénarios de débogage imbriqués, tels qu’un workflow appelant un autre Workflow ou un workflow appelant un script, ne sont pas implémentés.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-205">Other nested debugging scenarios, such as a workflow calling another workflow or a workflow calling a script, are not implemented.</span></span>

<span data-ttu-id="a4fd5-206">L’exemple suivant illustre le débogage d’un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-206">The following example demonstrates debugging a workflow.</span></span> <span data-ttu-id="a4fd5-207">Quand le débogueur parcourt la fonction de flux de travail, l’invite du débogueur passe à « [WFDBG] ».</span><span class="sxs-lookup"><span data-stu-id="a4fd5-207">When the debugger steps into the workflow function, the debugger prompt changes to "[WFDBG]".</span></span>

```powershell
PS C:> Set-PSBreakpoint -Script C:\TestWFDemo1.ps1 -Line 8

ID Script           Line Command    Variable     Action
-- ------           ---- -------    --------     ------
0 TestWFDemo1.ps1   8

PS C:> C:\TestWFDemo1.ps1
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

At C:\TestWFDemo1.ps1:8 char:5
+     Write-Output -InputObject "Now writing output:"
# +!INCLUDE[]~~~~~

[WFDBG:localhost]: PS C:>> list

# 3:

4:  workflow SampleWorkflowTest
5:  {
6:      param ($MyOutput)
# 7:

8:*     Write-Output -InputObject "Now writing output:"
9:      Write-Output -Input $MyOutput
# 10:

11:      Write-Output -InputObject "Get PowerShell process:"
12:      Get-Process -Name powershell
# 13:

14:      Write-Output -InputObject "Workflow function complete."
15:  }
# 16:

17:  # Call workflow function
18:  SampleWorkflowTest -MyOutput "Hello"

[WFDBG:localhost]: PS C:>> $MyOutput
Hello
[WFDBG:localhost]: PS C:>> stepOver
Now writing output:
At C:\TestWFDemo1.ps1:9 char:5
+     Write-Output -Input $MyOutput
# +!INCLUDE[]~

[WFDBG:localhost]: PS C:>> list

4:  workflow SampleWorkflowTest
5:  {
6:      param ($MyOutput)
# 7:

8:      Write-Output -InputObject "Now writing output:"
9:*     Write-Output -Input $MyOutput
# 10:

11:      Write-Output -InputObject "Get PowerShell process:"
12:      Get-Process -Name powershell
# 13:

14:      Write-Output -InputObject "Workflow function complete."
15:  }
# 16:

17:  # Call workflow function
18:  SampleWorkflowTest -MyOutput "Hello"
# 19:


[WFDBG:localhost]: PS C:>> stepOver
Hello
At C:\TestWFDemo1.ps1:11 char:5
+     Write-Output -InputObject "Get PowerShell process:"
# +!INCLUDE[]~~~~~~~~~

[WFDBG:localhost]: PS C:>> stepOut
Get PowerShell process:

Handles  NPM(K)    PM(K)    WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----    ----- -----   ------     -- -----------
    433      35   106688   128392   726     2.67   7124 powershell
    499      44   134244   172096   787     2.79   7452 powershell

Workflow function complete.
```

## <a name="debugging-functions"></a><span data-ttu-id="a4fd5-208">Fonctions de débogage</span><span class="sxs-lookup"><span data-stu-id="a4fd5-208">Debugging Functions</span></span>

<span data-ttu-id="a4fd5-209">Quand vous définissez un point d’arrêt sur une fonction qui a des `Begin` `Process` sections, et `End` , le débogueur s’arrête à la première ligne de chaque section.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-209">When you set a breakpoint on a function that has `Begin`, `Process`, and `End` sections, the debugger breaks at the first line of each section.</span></span>

<span data-ttu-id="a4fd5-210">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-210">For example:</span></span>

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a><span data-ttu-id="a4fd5-211">Débogage de scripts distants</span><span class="sxs-lookup"><span data-stu-id="a4fd5-211">Debugging Remote Scripts</span></span>

<span data-ttu-id="a4fd5-212">À compter de PowerShell 5,0, vous pouvez exécuter le débogueur PowerShell dans une session à distance, soit dans la console, soit Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-212">Starting in PowerShell 5.0, you can run the PowerShell debugger in a remote session, in either the console, or Windows PowerShell ISE.</span></span>
<span data-ttu-id="a4fd5-213">`Enter-PSSession` la fonctionnalité a été mise à jour pour vous permettre de vous reconnecter à et d’entrer dans une session déconnectée qui s’exécute sur un ordinateur distant, et d’exécuter un script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-213">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running on a remote computer, and currently running a script.</span></span> <span data-ttu-id="a4fd5-214">Si le script en cours d’exécution atteint un point d’arrêt, votre session cliente démarre automatiquement le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-214">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span>

<span data-ttu-id="a4fd5-215">Voici un exemple qui montre comment cela fonctionne, avec les points d’arrêt définis dans un script aux lignes 6, 11, 22 et 25.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-215">The following is an example that shows how this works, with breakpoints set in a script at lines 6, 11, 22, and 25.</span></span> <span data-ttu-id="a4fd5-216">Notez que dans l’exemple, quand le débogueur démarre, il existe deux invites d’identification : le nom de l’ordinateur sur lequel la session s’exécute et l’invite DBG qui vous indique que vous êtes en mode de débogage.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-216">Note that in the example, when the debugger starts, there are two identifying prompts: the name of the computer on which the session is running, and the DBG prompt that lets you know you are in debugging mode.</span></span>

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a><span data-ttu-id="a4fd5-217">Exemples</span><span class="sxs-lookup"><span data-stu-id="a4fd5-217">Examples</span></span>

<span data-ttu-id="a4fd5-218">Ce script de test détecte la version du système d’exploitation et affiche un message propre au système.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-218">This test script detects the version of the operating system and displays a system-appropriate message.</span></span> <span data-ttu-id="a4fd5-219">Il comprend une fonction, un appel de fonction et une variable.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-219">It includes a function, a function call, and a variable.</span></span>

<span data-ttu-id="a4fd5-220">La commande suivante affiche le contenu du fichier de script de test :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-220">The following command displays the contents of the test script file:</span></span>

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

<span data-ttu-id="a4fd5-221">Pour commencer, définissez un point d’arrêt à un point d’intérêt dans le script, tel qu’une ligne, une commande, une variable ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-221">To start, set a breakpoint at a point of interest in the script, such as a line, command, variable, or function.</span></span>

<span data-ttu-id="a4fd5-222">Commencez par créer un point d’arrêt de ligne sur la première ligne du Test.ps1 script dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-222">Start by creating a line breakpoint on the first line of the Test.ps1 script in the current directory.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

<span data-ttu-id="a4fd5-223">Vous pouvez abréger cette commande :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-223">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

<span data-ttu-id="a4fd5-224">La commande retourne un objet de point d’arrêt de ligne ( **System. Management. Automation. LineBreakpoint** ).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-224">The command returns a line-breakpoint object ( **System.Management.Automation.LineBreakpoint** ).</span></span>

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

<span data-ttu-id="a4fd5-225">À présent, démarrez le script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-225">Now, start the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
```

<span data-ttu-id="a4fd5-226">Lorsque le script atteint le premier point d’arrêt, le message de point d’arrêt indique que le débogueur est actif.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-226">When the script reaches the first breakpoint, the breakpoint message indicates that the debugger is active.</span></span> <span data-ttu-id="a4fd5-227">Il décrit le point d’arrêt et affiche un aperçu de la première ligne du script, qui est une déclaration de fonction.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-227">It describes the breakpoint and previews the first line of the script, which is a function declaration.</span></span> <span data-ttu-id="a4fd5-228">L’invite de commandes change également pour indiquer que le débogueur a le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-228">The command prompt also changes to indicate that the debugger has control.</span></span>

<span data-ttu-id="a4fd5-229">La ligne d’aperçu comprend le nom du script et le numéro de ligne de la commande prévisualisée.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-229">The preview line includes the script name and the line number of the previewed command.</span></span>

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

<span data-ttu-id="a4fd5-230">Utilisez la ou les commandes Step pour exécuter la première instruction dans le script et pour afficher un aperçu de l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-230">Use the Step command (s) to execute the first statement in the script and to preview the next statement.</span></span> <span data-ttu-id="a4fd5-231">L’instruction suivante utilise la `$MyInvocation` variable Automatic pour définir la valeur de la `$scriptName` variable sur le chemin d’accès et le nom de fichier du fichier de script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-231">The next statement uses the `$MyInvocation` automatic variable to set the value of the `$scriptName` variable to the path and file name of the script file.</span></span>

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

<span data-ttu-id="a4fd5-232">À ce stade, la `$scriptName` variable n’est pas remplie, mais vous pouvez vérifier la valeur de la variable en affichant sa valeur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-232">At this point, the `$scriptName` variable is not populated, but you can verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="a4fd5-233">Dans ce cas, la valeur est `$null`.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-233">In this case, the value is `$null`.</span></span>

```powershell
DBG> $scriptname
# DBG>
```

<span data-ttu-id="a4fd5-234">Utilisez une ou plusieurs autres commandes d’étape pour exécuter l’instruction en cours et pour afficher un aperçu de l’instruction suivante dans le script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-234">Use another Step command (s) to execute the current statement and to preview the next statement in the script.</span></span> <span data-ttu-id="a4fd5-235">L’instruction suivante appelle la fonction PsVersion.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-235">The next statement calls the PsVersion function.</span></span>

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="a4fd5-236">À ce stade, la `$scriptName` variable est remplie, mais vous vérifiez la valeur de la variable en affichant sa valeur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-236">At this point, the `$scriptName` variable is populated, but you verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="a4fd5-237">Dans ce cas, la valeur est définie sur le chemin d’accès du script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-237">In this case, the value is set to the script path.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

<span data-ttu-id="a4fd5-238">Utilisez une autre commande Step pour exécuter l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-238">Use another Step command to execute the function call.</span></span> <span data-ttu-id="a4fd5-239">Appuyez sur entrée ou tapez « s » pour l’étape.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-239">Press ENTER, or type "s" for Step.</span></span>

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

<span data-ttu-id="a4fd5-240">Le message de débogage comprend un aperçu de l’instruction dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-240">The debug message includes a preview of the statement in the function.</span></span> <span data-ttu-id="a4fd5-241">Pour exécuter cette instruction et pour afficher un aperçu de l’instruction suivante dans la fonction, vous pouvez utiliser une `Step` commande.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-241">To execute this statement and to preview the next statement in the function, you can use a `Step` command.</span></span> <span data-ttu-id="a4fd5-242">Toutefois, dans ce cas, utilisez une commande StepOut, (o).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-242">But, in this case, use a StepOut command (o).</span></span> <span data-ttu-id="a4fd5-243">Elle termine l’exécution de la fonction (sauf si elle atteint un point d’arrêt) et passe à l’instruction suivante dans le script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-243">It completes the execution of the function (unless it reaches a breakpoint) and steps to the next statement in the script.</span></span>

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="a4fd5-244">Étant donné que nous sommes dans la dernière instruction du script, les commandes Step, StepOut, et continue ont le même effet.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-244">Because we are on the last statement in the script, the Step, StepOut, and Continue commands have the same effect.</span></span> <span data-ttu-id="a4fd5-245">Dans ce cas, utilisez StepOut, (o).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-245">In this case, use StepOut (o).</span></span>

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

<span data-ttu-id="a4fd5-246">La commande StepOut, exécute la dernière commande.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-246">The StepOut command executes the last command.</span></span> <span data-ttu-id="a4fd5-247">L’invite de commandes standard indique que le débogueur s’est arrêté et a retourné le contrôle au processeur de commandes.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-247">The standard command prompt indicates that the debugger has exited and returned control to the command processor.</span></span>

<span data-ttu-id="a4fd5-248">À présent, réexécutez le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-248">Now, run the debugger again.</span></span> <span data-ttu-id="a4fd5-249">Tout d’abord, pour supprimer le point d’arrêt actuel, utilisez les `Get-PsBreakpoint` applets de commande et `Remove-PsBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-249">First, to delete the current breakpoint, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span> <span data-ttu-id="a4fd5-250">(Si vous pensez que vous pouvez réutiliser le point d’arrêt, utilisez l' `Disable-PsBreakpoint` applet de commande au lieu de `Remove-PsBreakpoint` .)</span><span class="sxs-lookup"><span data-stu-id="a4fd5-250">(If you think you might reuse the breakpoint, use the `Disable-PsBreakpoint` cmdlet instead of `Remove-PsBreakpoint`.)</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="a4fd5-251">Vous pouvez abréger cette commande :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-251">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> gbp | rbp
```

<span data-ttu-id="a4fd5-252">Ou exécutez la commande en écrivant une fonction, telle que la fonction suivante :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-252">Or, run the command by writing a function, such as the following function:</span></span>

```powershell
function delbr { gbp | rbp }
```

<span data-ttu-id="a4fd5-253">À présent, créez un point d’arrêt sur la `$scriptname` variable.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-253">Now, create a breakpoint on the `$scriptname` variable.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

<span data-ttu-id="a4fd5-254">Vous pouvez abréger la commande comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-254">You can abbreviate the command as:</span></span>

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

<span data-ttu-id="a4fd5-255">À présent, démarrez le script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-255">Now, start the script.</span></span> <span data-ttu-id="a4fd5-256">Le script atteint le point d’arrêt de la variable.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-256">The script reaches the variable breakpoint.</span></span> <span data-ttu-id="a4fd5-257">Le mode par défaut est Write, ce qui signifie que l’exécution s’arrête juste avant l’instruction qui modifie la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-257">The default mode is Write, so execution stops just before the statement that changes the value of the variable.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

<span data-ttu-id="a4fd5-258">Affichez la valeur actuelle de la `$scriptName` variable, qui est `$null` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-258">Display the current value of the `$scriptName` variable, which is `$null`.</span></span>

```powershell
DBG> $scriptName
# DBG>
```

<span data-ttu-id="a4fd5-259">Utilisez une ou plusieurs commandes d’étape pour exécuter l’instruction qui remplit la variable.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-259">Use a Step command (s) to execute the statement that populates the variable.</span></span>
<span data-ttu-id="a4fd5-260">Ensuite, affichez la nouvelle valeur de la `$scriptName` variable.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-260">Then, display the new value of the `$scriptName` variable.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="a4fd5-261">L’instruction suivante est un appel à la fonction PsVersion.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-261">The next statement is a call to the PsVersion function.</span></span> <span data-ttu-id="a4fd5-262">Pour ignorer la fonction tout en l’exécutant, utilisez une commande de décalage automatique (v).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-262">To skip the function but still execute it, use a StepOver command (v).</span></span> <span data-ttu-id="a4fd5-263">Si vous êtes déjà dans la fonction lorsque vous utilisez le décalage de passe, il n’est pas effectif.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-263">If you are already in the function when you use StepOver, it is not effective.</span></span> <span data-ttu-id="a4fd5-264">L’appel de fonction est affiché, mais il n’est pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-264">The function call is displayed, but it is not executed.</span></span>

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="a4fd5-265">La commande de décalage automatique exécute la fonction et affiche l’instruction suivante dans le script, qui imprime la dernière ligne.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-265">The StepOver command executes the function, and it previews the next statement in the script, which prints the final line.</span></span>

<span data-ttu-id="a4fd5-266">Utilisez une commande Stop (t) pour quitter le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-266">Use a Stop command (t) to exit the debugger.</span></span> <span data-ttu-id="a4fd5-267">L’invite de commandes revient à l’invite de commandes standard.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-267">The command prompt reverts to the standard command prompt.</span></span>

```powershell
C:\ps-test>
```

<span data-ttu-id="a4fd5-268">Pour supprimer les points d’arrêt, utilisez les `Get-PsBreakpoint` applets de commande et `Remove-PsBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-268">To delete the breakpoints, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="a4fd5-269">Créez un point d’arrêt de commande sur la fonction PsVersion.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-269">Create a new command breakpoint on the PsVersion function.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

<span data-ttu-id="a4fd5-270">Vous pouvez abréger cette commande pour :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-270">You can abbreviate this command to:</span></span>

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

<span data-ttu-id="a4fd5-271">À présent, exécutez le script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-271">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

<span data-ttu-id="a4fd5-272">Le script atteint le point d’arrêt au niveau de l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-272">The script reaches the breakpoint at the function call.</span></span> <span data-ttu-id="a4fd5-273">À ce stade, la fonction n’a pas encore été appelée.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-273">At this point, the function has not yet been called.</span></span> <span data-ttu-id="a4fd5-274">Cela vous donne la possibilité d’utiliser le paramètre action de `Set-PSBreakpoint` pour définir des conditions pour l’exécution du point d’arrêt ou pour effectuer des tâches préparatoires ou de diagnostic, telles que le démarrage d’un journal ou l’appel d’un diagnostic ou d’un script de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-274">This gives you the opportunity to use the Action parameter of `Set-PSBreakpoint` to set conditions for the execution of the breakpoint or to perform preparatory or diagnostic tasks, such as starting a log or invoking a diagnostic or security script.</span></span>

<span data-ttu-id="a4fd5-275">Pour définir une action, utilisez une commande continue (c) pour quitter le script et une `Remove-PsBreakpoint` commande pour supprimer le point d’arrêt actuel.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-275">To set an action, use a Continue command (c) to exit the script, and a `Remove-PsBreakpoint` command to delete the current breakpoint.</span></span> <span data-ttu-id="a4fd5-276">(Les points d’arrêt sont en lecture seule, vous ne pouvez donc pas ajouter une action au point d’arrêt actuel.)</span><span class="sxs-lookup"><span data-stu-id="a4fd5-276">(Breakpoints are read-only, so you cannot add an action to the current breakpoint.)</span></span>

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

<span data-ttu-id="a4fd5-277">À présent, créez un point d’arrêt de commande avec une action.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-277">Now, create a new command breakpoint with an action.</span></span> <span data-ttu-id="a4fd5-278">La commande suivante définit un point d’arrêt de commande avec une action qui journalise la valeur de la `$scriptName` variable lorsque la fonction est appelée.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-278">The following command sets a command breakpoint with an action that logs the value of the `$scriptName` variable when the function is called.</span></span> <span data-ttu-id="a4fd5-279">Étant donné que le mot clé Break n’est pas utilisé dans l’action, l’exécution ne s’arrête pas.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-279">Because the Break keyword is not used in the action, execution does not stop.</span></span> <span data-ttu-id="a4fd5-280">(L’accent grave (') est le caractère de continuation de ligne.)</span><span class="sxs-lookup"><span data-stu-id="a4fd5-280">(The backtick (\`) is the line-continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

<span data-ttu-id="a4fd5-281">Vous pouvez également ajouter des actions qui définissent des conditions pour le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-281">You can also add actions that set conditions for the breakpoint.</span></span> <span data-ttu-id="a4fd5-282">Dans la commande suivante, le point d’arrêt de commande est exécuté uniquement si la stratégie d’exécution est définie sur RemoteSigned, la stratégie la plus restrictive qui vous permet toujours d’exécuter des scripts.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-282">In the following command, the command breakpoint is executed only if the execution policy is set to RemoteSigned, the most restrictive policy that still permits you to run scripts.</span></span> <span data-ttu-id="a4fd5-283">(L’accent grave (') est le caractère de continuation.)</span><span class="sxs-lookup"><span data-stu-id="a4fd5-283">(The backtick (\`) is the continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

<span data-ttu-id="a4fd5-284">Le mot clé Break dans l’action indique au débogueur d’exécuter le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-284">The Break keyword in the action directs the debugger to execute the breakpoint.</span></span>
<span data-ttu-id="a4fd5-285">Vous pouvez également utiliser le mot clé continue pour demander au débogueur de s’exécuter sans interruption.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-285">You can also use the Continue keyword to direct the debugger to execute without breaking.</span></span> <span data-ttu-id="a4fd5-286">Étant donné que le mot clé Default est continue, vous devez spécifier Break pour arrêter l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-286">Because the default keyword is Continue, you must specify Break to stop execution.</span></span>

<span data-ttu-id="a4fd5-287">À présent, exécutez le script.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-287">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

<span data-ttu-id="a4fd5-288">Étant donné que la stratégie d’exécution est définie sur **RemoteSigned** , l’exécution s’arrête au niveau de l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-288">Because the execution policy is set to **RemoteSigned** , execution stops at the function call.</span></span>

<span data-ttu-id="a4fd5-289">À ce stade, vous souhaiterez peut-être vérifier la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-289">At this point, you might want to check the call stack.</span></span> <span data-ttu-id="a4fd5-290">Utilisez l' `Get-PsCallStack` applet de commande ou la `Get-PsCallStack` commande du débogueur (k).</span><span class="sxs-lookup"><span data-stu-id="a4fd5-290">Use the `Get-PsCallStack` cmdlet or the `Get-PsCallStack` debugger command (k).</span></span> <span data-ttu-id="a4fd5-291">La commande suivante obtient la pile des appels actuelle.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-291">The following command gets the current call stack.</span></span>

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

<span data-ttu-id="a4fd5-292">Cet exemple montre quelques-unes des nombreuses façons d’utiliser le débogueur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-292">This example demonstrates just a few of the many ways to use the PowerShell debugger.</span></span>

<span data-ttu-id="a4fd5-293">Pour plus d’informations sur les applets de commande du débogueur, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-293">For more information about the debugger cmdlets, type the following command:</span></span>

```powershell
help <cmdlet-name> -full
```

<span data-ttu-id="a4fd5-294">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="a4fd5-294">For example, type:</span></span>

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a><span data-ttu-id="a4fd5-295">Autres fonctionnalités de débogage dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4fd5-295">Other Debugging Features in PowerShell</span></span>

<span data-ttu-id="a4fd5-296">En plus du débogueur PowerShell, PowerShell comprend plusieurs autres fonctionnalités que vous pouvez utiliser pour déboguer des scripts et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-296">In addition to the PowerShell debugger, PowerShell includes several other features that you can use to debug scripts and functions.</span></span>

- <span data-ttu-id="a4fd5-297">Windows PowerShell ISE comprend un débogueur graphique interactif.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-297">Windows PowerShell ISE includes an interactive graphical debugger.</span></span> <span data-ttu-id="a4fd5-298">Pour plus d’informations, démarrez Windows PowerShell ISE et appuyez sur F1.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-298">For more information, start Windows PowerShell ISE and press F1.</span></span>

- <span data-ttu-id="a4fd5-299">L' `Set-PSDebug` applet de commande offre des fonctionnalités de débogage de script très basiques, y compris l’exécution pas à pas et le suivi.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-299">The `Set-PSDebug` cmdlet offers very basic script debugging features, including stepping and tracing.</span></span>

- <span data-ttu-id="a4fd5-300">Utilisez l' `Set-StrictMode` applet de commande pour détecter les références à des variables non initialisées, aux références à des propriétés inexistantes d’un objet et à une syntaxe de fonction non valide.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-300">Use the `Set-StrictMode` cmdlet to detect references to uninitialized variables, to references to non-existent properties of an object, and to function syntax that is not valid.</span></span>

- <span data-ttu-id="a4fd5-301">Ajoutez des instructions de diagnostic à un script, telles que des instructions qui affichent la valeur des variables, des instructions qui lisent l’entrée à partir de la ligne de commande ou des instructions qui signalent l’instruction en cours.</span><span class="sxs-lookup"><span data-stu-id="a4fd5-301">Add diagnostic statements to a script, such as statements that display the value of variables, statements that read input from the command line, or statements that report the current instruction.</span></span> <span data-ttu-id="a4fd5-302">Utilisez les applets de commande qui contiennent le verbe Write pour cette tâche, telles que `Write-Host` ,, `Write-Debug` `Write-Warning` et `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="a4fd5-302">Use the cmdlets that contain the Write verb for this task, such as `Write-Host`, `Write-Debug`, `Write-Warning`, and `Write-Verbose`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4fd5-303">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="a4fd5-303">SEE ALSO</span></span>

- [<span data-ttu-id="a4fd5-304">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a4fd5-304">Disable-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [<span data-ttu-id="a4fd5-305">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a4fd5-305">Enable-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [<span data-ttu-id="a4fd5-306">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a4fd5-306">Get-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [<span data-ttu-id="a4fd5-307">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="a4fd5-307">Get-PSCallStack</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [<span data-ttu-id="a4fd5-308">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a4fd5-308">Remove-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [<span data-ttu-id="a4fd5-309">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a4fd5-309">Set-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [<span data-ttu-id="a4fd5-310">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="a4fd5-310">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="a4fd5-311">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="a4fd5-311">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)