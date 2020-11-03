---
description: Explique comment utiliser l' `powershell.exe` interface de ligne de commande. Affiche les paramètres de ligne de commande et décrit la syntaxe.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_exe
ms.openlocfilehash: ef03558a6b58868b98c9da488934b0bfbbce9fe7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207953"
---
# <a name="about-powershellexe"></a><span data-ttu-id="5196f-105">À propos de PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="5196f-105">About PowerShell.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="5196f-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="5196f-106">Short Description</span></span>
<span data-ttu-id="5196f-107">Explique comment utiliser l' `powershell.exe` interface de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="5196f-107">Explains how to use the `powershell.exe` command-line interface.</span></span> <span data-ttu-id="5196f-108">Affiche les paramètres de ligne de commande et décrit la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="5196f-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="5196f-109">Description longue</span><span class="sxs-lookup"><span data-stu-id="5196f-109">Long Description</span></span>

### <a name="syntax"></a><span data-ttu-id="5196f-110">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5196f-110">SYNTAX</span></span>

```
PowerShell[.exe]
    [-PSConsoleFile <file> | -Version <version>]
    [-NoLogo]
    [-NoExit]
    [-Sta]
    [-Mta]
    [-NoProfile]
    [-NonInteractive]
    [-InputFormat {Text | XML}]
    [-OutputFormat {Text | XML}]
    [-WindowStyle <style>]
    [-EncodedCommand <Base64EncodedCommand>]
    [-ConfigurationName <string>]
    [-File - | <filePath> <args>]
    [-ExecutionPolicy <ExecutionPolicy>]
    [-Command - | { <script-block> [-args <arg-array>] }
                | { <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

### <a name="parameters"></a><span data-ttu-id="5196f-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5196f-111">Parameters</span></span>

#### <a name="-psconsolefile-filepath"></a><span data-ttu-id="5196f-112">-PSConsoleFile \<FilePath\></span><span class="sxs-lookup"><span data-stu-id="5196f-112">-PSConsoleFile \<FilePath\></span></span>

<span data-ttu-id="5196f-113">Charge le fichier de console PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="5196f-113">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="5196f-114">Entrez le chemin d’accès et le nom du fichier de console.</span><span class="sxs-lookup"><span data-stu-id="5196f-114">Enter the path and name of the console file.</span></span> <span data-ttu-id="5196f-115">Pour créer un fichier de console, utilisez l’applet de commande Export-Console dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5196f-115">To create a console file, use the Export-Console cmdlet in PowerShell.</span></span>

#### <a name="-version-powershell-version"></a><span data-ttu-id="5196f-116">-Version \<PowerShell Version\></span><span class="sxs-lookup"><span data-stu-id="5196f-116">-Version \<PowerShell Version\></span></span>

<span data-ttu-id="5196f-117">Démarre la version spécifiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5196f-117">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="5196f-118">Les valeurs valides sont 2,0 et 3,0.</span><span class="sxs-lookup"><span data-stu-id="5196f-118">Valid values are 2.0 and 3.0.</span></span> <span data-ttu-id="5196f-119">La version que vous spécifiez doit être installée sur le système.</span><span class="sxs-lookup"><span data-stu-id="5196f-119">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="5196f-120">Si Windows PowerShell 3,0 est installé sur l’ordinateur, « 3,0 » est la version par défaut.</span><span class="sxs-lookup"><span data-stu-id="5196f-120">If Windows PowerShell 3.0 is installed on the computer, "3.0" is the default version.</span></span>
<span data-ttu-id="5196f-121">Dans le cas contraire, « 2,0 » est la version par défaut.</span><span class="sxs-lookup"><span data-stu-id="5196f-121">Otherwise, "2.0" is the default version.</span></span> <span data-ttu-id="5196f-122">Pour plus d’informations, consultez [installation de PowerShell](/powershell/scripting/install/installing-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5196f-122">For more information, see [Installing PowerShell](/powershell/scripting/install/installing-windows-powershell).</span></span>

#### <a name="-nologo"></a><span data-ttu-id="5196f-123">-Nologo</span><span class="sxs-lookup"><span data-stu-id="5196f-123">-NoLogo</span></span>

<span data-ttu-id="5196f-124">Masque la bannière de copyright au démarrage.</span><span class="sxs-lookup"><span data-stu-id="5196f-124">Hides the copyright banner at startup.</span></span>

#### <a name="-noexit"></a><span data-ttu-id="5196f-125">-NoExit</span><span class="sxs-lookup"><span data-stu-id="5196f-125">-NoExit</span></span>

<span data-ttu-id="5196f-126">Ne quitte pas après l’exécution de commandes de démarrage.</span><span class="sxs-lookup"><span data-stu-id="5196f-126">Does not exit after running startup commands.</span></span>

#### <a name="-sta"></a><span data-ttu-id="5196f-127">-Sta</span><span class="sxs-lookup"><span data-stu-id="5196f-127">-Sta</span></span>

<span data-ttu-id="5196f-128">Démarre PowerShell à l’aide d’un cloisonnement monothread.</span><span class="sxs-lookup"><span data-stu-id="5196f-128">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="5196f-129">Dans Windows PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="5196f-129">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="5196f-130">Dans Windows PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="5196f-130">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-mta"></a><span data-ttu-id="5196f-131">-Mta</span><span class="sxs-lookup"><span data-stu-id="5196f-131">-Mta</span></span>

<span data-ttu-id="5196f-132">Démarre PowerShell à l’aide d’un cloisonnement multithread.</span><span class="sxs-lookup"><span data-stu-id="5196f-132">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="5196f-133">Ce paramètre est introduit dans PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="5196f-133">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="5196f-134">Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="5196f-134">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="5196f-135">Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="5196f-135">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-noprofile"></a><span data-ttu-id="5196f-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="5196f-136">-NoProfile</span></span>

<span data-ttu-id="5196f-137">Ne charge pas le profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5196f-137">Does not load the PowerShell profile.</span></span>

#### <a name="-noninteractive"></a><span data-ttu-id="5196f-138">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="5196f-138">-NonInteractive</span></span>

<span data-ttu-id="5196f-139">Ne présente pas d’invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5196f-139">Does not present an interactive prompt to the user.</span></span>

#### <a name="-inputformat-text--xml"></a><span data-ttu-id="5196f-140">-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="5196f-140">-InputFormat {Text | XML}</span></span>

<span data-ttu-id="5196f-141">Décrit le format des données envoyées à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5196f-141">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="5196f-142">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="5196f-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-outputformat-text--xml"></a><span data-ttu-id="5196f-143">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="5196f-143">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="5196f-144">Détermine la mise en forme de la sortie de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5196f-144">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="5196f-145">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="5196f-145">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-windowstyle-window-style"></a><span data-ttu-id="5196f-146">-WindowStyle \<Window style\></span><span class="sxs-lookup"><span data-stu-id="5196f-146">-WindowStyle \<Window style\></span></span>

<span data-ttu-id="5196f-147">Définit le style de fenêtre pour la session.</span><span class="sxs-lookup"><span data-stu-id="5196f-147">Sets the window style for the session.</span></span> <span data-ttu-id="5196f-148">Les valeurs valides sont Normal, Hidden, Minimized et Maximized.</span><span class="sxs-lookup"><span data-stu-id="5196f-148">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

#### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="5196f-149">-EncodedCommand \<Base64EncodedCommand\></span><span class="sxs-lookup"><span data-stu-id="5196f-149">-EncodedCommand \<Base64EncodedCommand\></span></span>

<span data-ttu-id="5196f-150">Accepte une version de chaîne codée en base 64 d’une commande.</span><span class="sxs-lookup"><span data-stu-id="5196f-150">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="5196f-151">Utilisez ce paramètre pour envoyer à PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes.</span><span class="sxs-lookup"><span data-stu-id="5196f-151">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span> <span data-ttu-id="5196f-152">La chaîne doit être mise en forme à l’aide de l’encodage de caractères UTF-16LE.</span><span class="sxs-lookup"><span data-stu-id="5196f-152">The string must be formatted using UTF-16LE character encoding.</span></span>

#### <a name="-configurationname-string"></a><span data-ttu-id="5196f-153">-ConfigurationName \<string\></span><span class="sxs-lookup"><span data-stu-id="5196f-153">-ConfigurationName \<string\></span></span>

<span data-ttu-id="5196f-154">Spécifie un point de terminaison de configuration dans lequel PowerShell est exécuté.</span><span class="sxs-lookup"><span data-stu-id="5196f-154">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="5196f-155">Il peut s’agir de n’importe quel point de terminaison enregistré sur l’ordinateur local, y compris les points de terminaison de communication à distance PowerShell par défaut ou un point de terminaison personnalisé avec des fonctionnalités de rôle d’utilisateur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="5196f-155">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

#### <a name="-file----filepath-args"></a><span data-ttu-id="5196f-156">-Fichier-| \<filePath\>\<args\></span><span class="sxs-lookup"><span data-stu-id="5196f-156">-File - | \<filePath\> \<args\></span></span>

<span data-ttu-id="5196f-157">Si la valeur du **fichier** est « - », le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="5196f-157">If the value of **File** is "-", the command text is read from standard input.</span></span>
<span data-ttu-id="5196f-158">L’exécution `powershell -File -` sans une entrée standard redirigée démarre une session normale.</span><span class="sxs-lookup"><span data-stu-id="5196f-158">Running `powershell -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="5196f-159">Cela revient au même que de ne pas spécifier le paramètre **file** .</span><span class="sxs-lookup"><span data-stu-id="5196f-159">This is the same as not specifying the **File** parameter at all.</span></span>

<span data-ttu-id="5196f-160">Si la valeur de **fichier** est un chemin d’accès de fichier, le script s’exécute dans l’étendue locale (« point-source »), afin que les fonctions et variables créées par le script soient disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5196f-160">If the value of **File** is a file path, the script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="5196f-161">Entrez le chemin d’accès au fichier de script et les paramètres éventuels.</span><span class="sxs-lookup"><span data-stu-id="5196f-161">Enter the script file path and any parameters.</span></span> <span data-ttu-id="5196f-162">**File** doit être le dernier paramètre dans la commande.</span><span class="sxs-lookup"><span data-stu-id="5196f-162">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="5196f-163">Toutes les valeurs tapées après le paramètre **file** sont interprétées comme le chemin d’accès au fichier de script et les paramètres passés à ce script.</span><span class="sxs-lookup"><span data-stu-id="5196f-163">All values typed after the **File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="5196f-164">Les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel).</span><span class="sxs-lookup"><span data-stu-id="5196f-164">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="5196f-165">Par exemple, si vous êtes en **cmd.exe** et que vous souhaitez passer une valeur de variable d’environnement, vous devez utiliser la syntaxe **cmd.exe** : `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="5196f-165">For example, if you are in **cmd.exe** and want to pass an environment variable value, you would use the **cmd.exe** syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="5196f-166">En revanche, s’exécutant `powershell.exe -File .\test.ps1 -TestParam $env:windir` dans **cmd.exe** , le script reçoit la chaîne littérale `$env:windir` , car il n’a aucune signification particulière pour l’interpréteur de commandes **cmd.exe** actuel.</span><span class="sxs-lookup"><span data-stu-id="5196f-166">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in **cmd.exe** results in the script receiving the literal string `$env:windir` because it has no special meaning to the current **cmd.exe** shell.</span></span> <span data-ttu-id="5196f-167">Le `$env:windir` style de référence de variable d’environnement _peut_ être utilisé dans un paramètre de **commande** , dans la mesure où il sera interprété comme du code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5196f-167">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it will be interpreted as PowerShell code.</span></span>

<span data-ttu-id="5196f-168">De même, si vous souhaitez exécuter la même commande à partir d’un **script de commandes** , vous devez utiliser à la `%~dp0` place de `.\` ou `$PSScriptRoot` pour représenter le répertoire d’exécution actuel : `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="5196f-168">Similarly, if you want to execute the same command from a **Batch script** , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%`.</span></span>
<span data-ttu-id="5196f-169">Si vous l’utilisez à la place `.\test.ps1` , PowerShell lèvera une erreur, car il ne peut pas trouver le chemin d’accès littéral `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="5196f-169">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="5196f-170">Lorsque la valeur du **fichier** est un chemin d’accès de fichier, le **fichier** _doit_ être le dernier paramètre de la commande, car tous les caractères tapés après le nom du paramètre de **fichier** sont interprétés comme étant le chemin d’accès du fichier de script suivi des paramètres du script.</span><span class="sxs-lookup"><span data-stu-id="5196f-170">When the value of **File** is a file path, **File** _must_ be the last parameter in the command because any characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="5196f-171">Vous pouvez inclure les paramètres de script et les valeurs dans la valeur du paramètre **file** .</span><span class="sxs-lookup"><span data-stu-id="5196f-171">You can include the script parameters and values in the value of the **File** parameter.</span></span> <span data-ttu-id="5196f-172">Par exemple : `-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="5196f-172">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="5196f-173">En règle générale, les paramètres de commutateur d’un script sont inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="5196f-173">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="5196f-174">Par exemple, la commande suivante utilise le paramètre **All** du `Get-Script.ps1` fichier de script : `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="5196f-174">For example, the following command uses the **All** parameter of the `Get-Script.ps1` script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="5196f-175">Dans de rares cas, vous devrez peut-être fournir une valeur **booléenne** pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="5196f-175">In rare cases, you might need to provide a **Boolean** value for a parameter.</span></span>
<span data-ttu-id="5196f-176">Il n’est pas possible de passer une valeur booléenne explicite pour un paramètre de commutateur lors de l’exécution d’un script de cette manière.</span><span class="sxs-lookup"><span data-stu-id="5196f-176">It is not possible to pass an explicit boolean value for a switch parameter when running a script in this way.</span></span> <span data-ttu-id="5196f-177">Cette limitation a été supprimée dans PowerShell 6 ( `pwsh.exe` ).</span><span class="sxs-lookup"><span data-stu-id="5196f-177">This limitation was removed in PowerShell 6 (`pwsh.exe`).</span></span>

#### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="5196f-178">-ExecutionPolicy \<ExecutionPolicy\></span><span class="sxs-lookup"><span data-stu-id="5196f-178">-ExecutionPolicy \<ExecutionPolicy\></span></span>

<span data-ttu-id="5196f-179">Définit la stratégie d’exécution par défaut pour la session active et l’enregistre dans la `$env:PSExecutionPolicyPreference` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="5196f-179">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="5196f-180">Ce paramètre ne modifie pas la stratégie d’exécution PowerShell qui est définie dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="5196f-180">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="5196f-181">Pour plus d’informations sur les stratégies d’exécution PowerShell, notamment une liste de valeurs valides, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="5196f-181">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

#### <a name="-command"></a><span data-ttu-id="5196f-182">-Command</span><span class="sxs-lookup"><span data-stu-id="5196f-182">-Command</span></span>

<span data-ttu-id="5196f-183">Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell, puis se ferme, sauf si le `NoExit` paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="5196f-183">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="5196f-184">La valeur de **Command** peut être `-` , un bloc de script ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5196f-184">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="5196f-185">Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="5196f-185">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="5196f-186">Le paramètre de **commande** n’accepte qu’un bloc de script pour l’exécution lorsqu’il peut reconnaître la valeur passée à la **commande** en tant que type **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="5196f-186">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="5196f-187">Cela est possible _uniquement_ lors de l’exécution `powershell.exe` à partir d’un autre hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5196f-187">This is _only_ possible when running `powershell.exe` from another PowerShell host.</span></span> <span data-ttu-id="5196f-188">Le type **scriptblock** peut être contenu dans une variable existante, retournée à partir d’une expression, ou analysé par l’hôte PowerShell sous la forme d’un bloc de script littéral placé entre accolades ( `{}` ), avant d’être passé à `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="5196f-188">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `powershell.exe`.</span></span>

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="5196f-189">Dans `cmd.exe` , il n’existe aucun bloc de script (ou type **scriptblock** ), donc la valeur transmise à la **commande** sera _toujours_ une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5196f-189">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="5196f-190">Si vous écrivez un bloc de script dans la chaîne, il se comportera exactement comme s’il avait été tapé dans une invite PowerShell classique, affichant le contenu du bloc de script au lieu de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="5196f-190">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="5196f-191">Une chaîne transmise à la **commande** est toujours exécutée comme code PowerShell, donc les accolades de bloc de script ne sont souvent pas requises dans le premier emplacement lors de l’exécution à partir de `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="5196f-191">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="5196f-192">Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, il est possible d’utiliser [l’opérateur d’appel](about_operators.md#special-operators) `&` :</span><span class="sxs-lookup"><span data-stu-id="5196f-192">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="5196f-193">Si la valeur de **Command** est une chaîne, **Command** doit être le dernier paramètre de pwsh, car tous les arguments qui le suivent sont interprétés comme faisant partie de la commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="5196f-193">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="5196f-194">Quand elle est appelée à partir d’une session PowerShell existante, les résultats sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs.</span><span class="sxs-lookup"><span data-stu-id="5196f-194">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="5196f-195">Pour les autres shells, les résultats sont retournés sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="5196f-195">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="5196f-196">Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="5196f-196">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="5196f-197">Vous devez rediriger l’entrée standard lors de l’utilisation du paramètre de **commande** avec une entrée standard.</span><span class="sxs-lookup"><span data-stu-id="5196f-197">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="5196f-198">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5196f-198">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="5196f-199">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5196f-199">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="5196f-200">Le code de sortie du processus est déterminé par l’état de la dernière commande (exécutée) dans le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="5196f-200">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="5196f-201">Le code de sortie est `0` lorsque `$?` est `$true` ou `1` lorsque `$?` est `$false` .</span><span class="sxs-lookup"><span data-stu-id="5196f-201">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="5196f-202">Si la dernière commande est un programme externe ou un script PowerShell qui définit explicitement un code de sortie autre que `0` ou `1` , ce code de sortie est converti en `1` pour le code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="5196f-202">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="5196f-203">Pour conserver le code de sortie spécifique, ajoutez `exit $LASTEXITCODE` à votre chaîne de commande ou bloc de script.</span><span class="sxs-lookup"><span data-stu-id="5196f-203">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="5196f-204">De même, la valeur 1 est retournée quand une erreur de fin de script (arrêt d’exécution), telle que `throw` ou `-ErrorAction Stop` , se produit ou lorsque l’exécution est interrompue avec <kbd>CTRL</kbd> - <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5196f-204">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

<span data-ttu-id="5196f-205">_uniquement_ possible lors de l’exécution de **PowerShell.exe** à partir d’un autre hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5196f-205">_only_ possible when running **PowerShell.exe** from another PowerShell host.</span></span>
<span data-ttu-id="5196f-206">Le type **scriptblock** peut être contenu dans une variable existante, retournée à partir d’une expression, ou analysé par l’hôte PowerShell sous la forme d’un bloc de script littéral placé entre accolades `{}` , avant d’être passé à **PowerShell.exe** .</span><span class="sxs-lookup"><span data-stu-id="5196f-206">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to **PowerShell.exe** .</span></span>

<span data-ttu-id="5196f-207">Dans **cmd.exe** , il n’existe pas de type de bloc de script (ou type **scriptblock** ), donc la valeur transmise à la **commande** sera _toujours_ une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5196f-207">In **cmd.exe** , there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="5196f-208">Si vous écrivez un bloc de script dans la chaîne, il se comportera exactement comme s’il avait été tapé dans une invite PowerShell classique, affichant le contenu du bloc de script au lieu de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="5196f-208">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="5196f-209">Une chaîne transmise à la **commande** est toujours exécutée en tant que PowerShell. par conséquent, les accolades de bloc de script ne sont souvent pas requises dans le premier emplacement lors de l’exécution à partir de **cmd.exe** .</span><span class="sxs-lookup"><span data-stu-id="5196f-209">A string passed to **Command** will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from **cmd.exe** .</span></span> <span data-ttu-id="5196f-210">Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, vous pouvez utiliser l' [opérateur d’appel](about_operators.md#special-operators) 
 `&` :</span><span class="sxs-lookup"><span data-stu-id="5196f-210">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators)
`&` can be used:</span></span>

```console
"& {<command>}"
```

#### <a name="-help---"></a><span data-ttu-id="5196f-211">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="5196f-211">-Help, -?, /?</span></span>

<span data-ttu-id="5196f-212">Affiche l’aide pour **PowerShell.exe** .</span><span class="sxs-lookup"><span data-stu-id="5196f-212">Displays help for **PowerShell.exe** .</span></span> <span data-ttu-id="5196f-213">Si vous tapez une commande **PowerShell.exe** dans une session PowerShell, faites précéder les paramètres de commande d’un trait d’Union (-), et non d’une barre oblique (/).</span><span class="sxs-lookup"><span data-stu-id="5196f-213">If you are typing a **PowerShell.exe** command in a PowerShell session, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="5196f-214">Vous pouvez utiliser un trait d’Union ou une barre oblique dans **cmd.exe** .</span><span class="sxs-lookup"><span data-stu-id="5196f-214">You can use either a hyphen or forward slash in **cmd.exe** .</span></span>

### <a name="remarks"></a><span data-ttu-id="5196f-215">Remarques</span><span class="sxs-lookup"><span data-stu-id="5196f-215">REMARKS</span></span>

<span data-ttu-id="5196f-216">Remarque sur la résolution des problèmes : dans PowerShell 2,0, le démarrage de certains programmes à partir de la console PowerShell échoue avec un **LastExitCode** de 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="5196f-216">Troubleshooting note: In PowerShell 2.0, starting some programs from the PowerShell console fails with a **LastExitCode** of 0xc0000142.</span></span>

### <a name="examples"></a><span data-ttu-id="5196f-217">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5196f-217">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
