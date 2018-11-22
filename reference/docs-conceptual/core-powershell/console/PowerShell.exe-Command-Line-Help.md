---
ms.date: 08/14/2018
keywords: powershell,applet de commande
title: Aide sur la ligne de commande PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691828"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="e8c0a-103">Aide sur la ligne de commande PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="e8c0a-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="e8c0a-104">Vous pouvez utiliser PowerShell.exe pour démarrer une session PowerShell à partir de la ligne de commande d’un autre outil, tel que Cmd.exe, ou l’utiliser dans la ligne de commande PowerShell pour démarrer une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="e8c0a-105">Utilisez les paramètres pour personnaliser la session.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8c0a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8c0a-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="e8c0a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8c0a-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="e8c0a-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="e8c0a-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="e8c0a-109">Accepte une version de chaîne codée en base 64 d’une commande.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="e8c0a-110">Utilisez ce paramètre pour envoyer à PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="e8c0a-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="e8c0a-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="e8c0a-112">Définit la stratégie d’exécution par défaut pour la session actuelle et l’enregistre dans la variable d’environnement $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="e8c0a-113">Ce paramètre ne modifie pas la stratégie d’exécution PowerShell qui est définie dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="e8c0a-114">Pour plus d’informations sur les stratégies d’exécution PowerShell, notamment une liste de valeurs valides, consultez [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="e8c0a-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="e8c0a-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="e8c0a-116">Exécute le script spécifié dans l’étendue locale (avec « dot-sourcing »), afin que les fonctions et variables créées par le script soient disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="e8c0a-117">Entrez le chemin d’accès au fichier de script et les paramètres éventuels.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="e8c0a-118">**File** doit être le dernier paramètre dans la commande.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="e8c0a-119">Toutes les valeurs saisies après le paramètre **-File** sont interprétées comme les paramètres et le chemin d’accès au fichier de script passés à ce script.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="e8c0a-120">Les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="e8c0a-121">Par exemple, si vous êtes dans cmd.exe et que vous souhaitez passer une valeur de variable d’environnement, vous utiliseriez la syntaxe de cmd.exe : `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="e8c0a-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="e8c0a-122">En revanche, en cours d’exécution `powershell.exe -File .\test.ps1 -TestParam $env:windir` dans les résultats de cmd.exe dans le script reçoit la chaîne littérale `$env:windir` , car il n’a aucune signification spéciale à l’interpréteur de commandes cmd.exe actuel.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="e8c0a-123">Le `$env:windir` style de référence de variable d’environnement _pouvez_ utilisables dans un `-Command` paramètre, dans la mesure où il elle sera interprétée en tant que code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="e8c0a-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="e8c0a-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="e8c0a-125">Décrit le format des données envoyées à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="e8c0a-126">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="e8c0a-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="e8c0a-127">-Mta</span></span>

<span data-ttu-id="e8c0a-128">Démarre PowerShell à l’aide d’un cloisonnement multithread.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="e8c0a-129">Ce paramètre est introduit dans PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="e8c0a-130">Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="e8c0a-131">Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="e8c0a-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="e8c0a-132">-NoExit</span></span>

<span data-ttu-id="e8c0a-133">Ne quitte pas après l’exécution de commandes de démarrage.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="e8c0a-134">-Nologo</span><span class="sxs-lookup"><span data-stu-id="e8c0a-134">-NoLogo</span></span>

<span data-ttu-id="e8c0a-135">Masque la bannière de copyright au démarrage.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="e8c0a-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="e8c0a-136">-NonInteractive</span></span>

<span data-ttu-id="e8c0a-137">Ne présente pas d’invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="e8c0a-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="e8c0a-138">-NoProfile</span></span>

<span data-ttu-id="e8c0a-139">Ne charge pas le profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="e8c0a-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="e8c0a-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="e8c0a-141">Détermine la mise en forme de la sortie de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="e8c0a-142">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="e8c0a-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="e8c0a-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="e8c0a-144">Charge le fichier de console PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="e8c0a-145">Entrez le chemin d’accès et le nom du fichier de console.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="e8c0a-146">Pour créer un fichier de console, utilisez la cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="e8c0a-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="e8c0a-147">-Sta</span></span>

<span data-ttu-id="e8c0a-148">Démarre PowerShell à l’aide d’un cloisonnement monothread.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="e8c0a-149">Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="e8c0a-150">Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="e8c0a-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="e8c0a-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="e8c0a-152">Démarre la version spécifiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="e8c0a-153">La version que vous spécifiez doit être installée sur le système.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="e8c0a-154">Si PowerShell 3.0 est installé sur l’ordinateur, les valeurs valides sont « 2.0 » et « 3.0 ».</span><span class="sxs-lookup"><span data-stu-id="e8c0a-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="e8c0a-155">La valeur par défaut est « 3.0 ».</span><span class="sxs-lookup"><span data-stu-id="e8c0a-155">The default value is "3.0".</span></span>

<span data-ttu-id="e8c0a-156">Si PowerShell 3.0 n’est pas installé, la seule valeur valide est « 2.0 ».</span><span class="sxs-lookup"><span data-stu-id="e8c0a-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="e8c0a-157">Les autres valeurs sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-157">Other values are ignored.</span></span>

<span data-ttu-id="e8c0a-158">Pour plus d’informations, voir [Installation de Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="e8c0a-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="e8c0a-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="e8c0a-160">Définit le style de fenêtre pour la session.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-160">Sets the window style for the session.</span></span> <span data-ttu-id="e8c0a-161">Les valeurs valides sont Normal, Hidden, Minimized et Maximized.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="e8c0a-162">-Command</span><span class="sxs-lookup"><span data-stu-id="e8c0a-162">-Command</span></span>

<span data-ttu-id="e8c0a-163">Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="e8c0a-164">Après l’exécution, PowerShell s’arrête, sauf si le **NoExit** est précisé.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="e8c0a-165">Tout texte qui suit `-Command` est envoyé en tant qu’une seule ligne de commande à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="e8c0a-166">Cela diffère de la façon dont `-File` gère les paramètres envoyés à un script.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="e8c0a-167">La valeur de `-Command` peut être «- », une chaîne ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="e8c0a-168">Les résultats de la commande sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, objets pas actifs.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="e8c0a-169">Si la valeur de `-Command` est «- », le texte de commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="e8c0a-170">Lorsque la valeur de `-Command` est une chaîne, **commande** _doit_ être le dernier paramètre spécifié, car les caractères tapés après la commande sont interprétés comme des arguments de commande.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="e8c0a-171">Le **commande** paramètre accepte uniquement un bloc de script pour l’exécution lorsqu’il peut reconnaître la valeur passée à `-Command` comme un type de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="e8c0a-172">Il s’agit de _uniquement_ possible lors de l’exécution de PowerShell.exe à partir d’un autre hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="e8c0a-173">Un bloc de script littérale entre accolades d’héberger le ScriptBlock type peut être contenu dans une variable, retourné par une expression ou analysé par la commande PowerShell existante `{}`, avant passés aux fonctions PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="e8c0a-174">Dans cmd.exe, il n’existe pas comme un bloc de script (ou le type de bloc de script), par conséquent, la valeur passée à **commande** sera _toujours_ être une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="e8c0a-175">Vous pouvez écrire un bloc de script à l’intérieur de la chaîne, mais au lieu d’en cours d’exécution qu’il se comporte exactement comme si vous avez tapé à l’invite de PowerShell classique, affichant le contenu du script bloquer arrière pour vous.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="e8c0a-176">Une chaîne passée à `-Command` seront toujours exécutées en tant que PowerShell, par conséquent, les accolades de bloc de script ne sont généralement pas requis en premier lieu lors de l’exécution à partir de cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="e8c0a-177">Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, le [opérateur d’appel](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` peut être utilisé :</span><span class="sxs-lookup"><span data-stu-id="e8c0a-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="e8c0a-178">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="e8c0a-178">-Help, -?, /?</span></span>

<span data-ttu-id="e8c0a-179">Illustre la syntaxe de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="e8c0a-180">Si vous tapez une commande PowerShell.exe dans PowerShell, faites précéder les paramètres de commande d’un trait d’union (-), et non d’une barre oblique (/).</span><span class="sxs-lookup"><span data-stu-id="e8c0a-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="e8c0a-181">Vous pouvez utiliser un trait d’union ou une barre oblique dans Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="e8c0a-182">Remarque sur la résolution de problèmes : dans PowerShell 2.0, le démarrage de certains programmes dans la console Windows PowerShell échoue en signalant un LastExitCode de 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="e8c0a-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="e8c0a-183">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e8c0a-183">EXAMPLES</span></span>

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
