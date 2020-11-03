---
description: Explique comment utiliser l' `pwsh` interface de ligne de commande. Affiche les paramètres de ligne de commande et décrit la syntaxe.
keywords: powershell,applet de commande
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: 549c99fa618e2e53aed8945d95e92f97117aa6c9
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208614"
---
# <a name="about-pwsh"></a><span data-ttu-id="b222d-105">À propos de pwsh</span><span class="sxs-lookup"><span data-stu-id="b222d-105">About pwsh</span></span>

## <a name="short-description"></a><span data-ttu-id="b222d-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="b222d-106">Short Description</span></span>
<span data-ttu-id="b222d-107">Explique comment utiliser l' `pwsh` interface de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b222d-107">Explains how to use the `pwsh` command-line interface.</span></span> <span data-ttu-id="b222d-108">Affiche les paramètres de ligne de commande et décrit la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b222d-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="b222d-109">Description longue</span><span class="sxs-lookup"><span data-stu-id="b222d-109">Long Description</span></span>

## <a name="syntax"></a><span data-ttu-id="b222d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b222d-110">Syntax</span></span>

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="b222d-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b222d-111">Parameters</span></span>

<span data-ttu-id="b222d-112">Tous les paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="b222d-112">All parameters are case-insensitive.</span></span>

### <a name="-file---f"></a><span data-ttu-id="b222d-113">-File | -f</span><span class="sxs-lookup"><span data-stu-id="b222d-113">-File | -f</span></span>

<span data-ttu-id="b222d-114">Si la valeur de `File` est `-` , le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="b222d-114">If the value of `File` is `-`, the command text is read from standard input.</span></span>
<span data-ttu-id="b222d-115">L’exécution `pwsh -File -` sans une entrée standard redirigée démarre une session normale.</span><span class="sxs-lookup"><span data-stu-id="b222d-115">Running `pwsh -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="b222d-116">Cela revient à ne pas spécifier le `File` paramètre du tout.</span><span class="sxs-lookup"><span data-stu-id="b222d-116">This is the same as not specifying the `File` parameter at all.</span></span>

<span data-ttu-id="b222d-117">Il s’agit du paramètre par défaut si aucun paramètre n’est présent, mais que des valeurs sont présentes dans la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b222d-117">This is the default parameter if no parameters are present but values are present in the command line.</span></span> <span data-ttu-id="b222d-118">Le script spécifié s’exécute dans l’étendue locale (« point-source »), afin que les fonctions et variables créées par le script soient disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b222d-118">The specified script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="b222d-119">Entrez le chemin d’accès au fichier de script et les paramètres éventuels.</span><span class="sxs-lookup"><span data-stu-id="b222d-119">Enter the script file path and any parameters.</span></span> <span data-ttu-id="b222d-120">Le fichier doit être le dernier paramètre de la commande, car tous les caractères tapés après le nom du paramètre de fichier sont interprétés comme étant le chemin du fichier de script suivi des paramètres du script.</span><span class="sxs-lookup"><span data-stu-id="b222d-120">File must be the last parameter in the command, because all characters typed after the File parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="b222d-121">En règle générale, les paramètres de commutateur d’un script sont inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="b222d-121">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="b222d-122">Par exemple, la commande suivante utilise le paramètre All de l' Get-Script.ps1 fichier de script : `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="b222d-122">For example, the following command uses the All parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="b222d-123">Dans de rares cas, vous devrez peut-être fournir une valeur **booléenne** pour un paramètre de commutateur.</span><span class="sxs-lookup"><span data-stu-id="b222d-123">In rare cases, you might need to provide a **Boolean** value for a switch parameter.</span></span> <span data-ttu-id="b222d-124">Pour fournir une valeur **booléenne** pour un paramètre de commutateur dans la valeur du paramètre **file** , utilisez le paramètre normalement suivi immédiatement par un signe deux-points et la valeur booléenne, comme suit : `-File .\Get-Script.ps1 -All:$False` .</span><span class="sxs-lookup"><span data-stu-id="b222d-124">To provide a **Boolean** value for a switch parameter in the value of the **File** parameter, Use the parameter normally followed immediately by a colon and the boolean value, such as the following: `-File .\Get-Script.ps1 -All:$False`.</span></span>

<span data-ttu-id="b222d-125">Les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel).</span><span class="sxs-lookup"><span data-stu-id="b222d-125">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="b222d-126">Par exemple, si vous êtes dans `cmd.exe` et que vous souhaitez passer une valeur de variable d’environnement, vous devez utiliser la `cmd.exe` syntaxe suivante : `pwsh -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="b222d-126">For example, if you are in `cmd.exe` and want to pass an environment variable value, you would use the `cmd.exe` syntax: `pwsh -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="b222d-127">En revanche, `pwsh -File .\test.ps1 -TestParam $env:windir` l’exécution de dans `cmd.exe` entraîne la réception par le script de la chaîne littérale `$env:windir` , car elle n’a aucune signification particulière pour l’interpréteur de commandes actuel `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="b222d-127">In contrast, running `pwsh -File .\test.ps1 -TestParam $env:windir` in `cmd.exe` results in the script receiving the literal string `$env:windir` because it has no special meaning to the current `cmd.exe` shell.</span></span> <span data-ttu-id="b222d-128">Le `$env:windir` style de référence de variable d’environnement _peut_ être utilisé dans un paramètre de **commande** , car il est interprété comme du code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b222d-128">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it is interpreted as PowerShell code.</span></span>

<span data-ttu-id="b222d-129">De même, si vous souhaitez exécuter la même commande à partir d’un _script de commandes_ , vous devez utiliser à la `%~dp0` place de `.\` ou `$PSScriptRoot` pour représenter le répertoire d’exécution actuel : `pwsh -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="b222d-129">Similarly, if you want to execute the same command from a _Batch script_ , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `pwsh -File %~dp0test.ps1 -TestParam %windir%`.</span></span> <span data-ttu-id="b222d-130">Si vous l’utilisez à la place `.\test.ps1` , PowerShell lèvera une erreur, car il ne peut pas trouver le chemin d’accès littéral `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="b222d-130">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="b222d-131">Lorsque le fichier de script se termine par une `exit` commande, le code de sortie du processus est défini sur l’argument numérique utilisé avec la `exit` commande.</span><span class="sxs-lookup"><span data-stu-id="b222d-131">When the script file terminates with an `exit` command, the process exit code is set to the numeric argument used with the `exit` command.</span></span> <span data-ttu-id="b222d-132">Avec un arrêt normal, le code de sortie est toujours `0` .</span><span class="sxs-lookup"><span data-stu-id="b222d-132">With normal termination, the exit code is always `0`.</span></span>

<span data-ttu-id="b222d-133">Semblable à `-Command` , quand une erreur de fin de script se produit, le code de sortie est défini sur `1` .</span><span class="sxs-lookup"><span data-stu-id="b222d-133">Similar to `-Command`, when a script-terminating error occurs, the exit code is set to `1`.</span></span> <span data-ttu-id="b222d-134">Toutefois, contrairement à `-Command` , lorsque l’exécution est interrompue avec <kbd>CTRL</kbd> - <kbd>C</kbd> , le code de sortie est `0` .</span><span class="sxs-lookup"><span data-stu-id="b222d-134">However, unlike with `-Command`, when the execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd> the exit code is `0`.</span></span>

### <a name="-command---c"></a><span data-ttu-id="b222d-135">-Commande | -c</span><span class="sxs-lookup"><span data-stu-id="b222d-135">-Command | -c</span></span>

<span data-ttu-id="b222d-136">Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell, puis se ferme, sauf si le `NoExit` paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="b222d-136">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="b222d-137">La valeur de **Command** peut être `-` , un bloc de script ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b222d-137">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="b222d-138">Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="b222d-138">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="b222d-139">Le paramètre de **commande** n’accepte qu’un bloc de script pour l’exécution lorsqu’il peut reconnaître la valeur passée à la **commande** en tant que type **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="b222d-139">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="b222d-140">Cela est possible _uniquement_ lors de l’exécution `pwsh` à partir d’un autre hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b222d-140">This is _only_ possible when running `pwsh` from another PowerShell host.</span></span> <span data-ttu-id="b222d-141">Le type **scriptblock** peut être contenu dans une variable existante, retournée à partir d’une expression, ou analysé par l’hôte PowerShell sous la forme d’un bloc de script littéral placé entre accolades ( `{}` ), avant d’être passé à `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="b222d-141">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `pwsh`.</span></span>

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="b222d-142">Dans `cmd.exe` , il n’existe aucun bloc de script (ou type **scriptblock** ), donc la valeur transmise à la **commande** sera _toujours_ une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b222d-142">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="b222d-143">Si vous écrivez un bloc de script dans la chaîne, il se comportera exactement comme s’il avait été tapé dans une invite PowerShell classique, affichant le contenu du bloc de script au lieu de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="b222d-143">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="b222d-144">Une chaîne transmise à la **commande** est toujours exécutée comme code PowerShell, donc les accolades de bloc de script ne sont souvent pas requises dans le premier emplacement lors de l’exécution à partir de `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="b222d-144">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="b222d-145">Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, il est possible d’utiliser [l’opérateur d’appel](about_operators.md#special-operators) `&` :</span><span class="sxs-lookup"><span data-stu-id="b222d-145">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="b222d-146">Si la valeur de **Command** est une chaîne, **Command** doit être le dernier paramètre de pwsh, car tous les arguments qui le suivent sont interprétés comme faisant partie de la commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="b222d-146">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="b222d-147">Quand elle est appelée à partir d’une session PowerShell existante, les résultats sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs.</span><span class="sxs-lookup"><span data-stu-id="b222d-147">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="b222d-148">Pour les autres shells, les résultats sont retournés sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="b222d-148">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="b222d-149">Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="b222d-149">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="b222d-150">Vous devez rediriger l’entrée standard lors de l’utilisation du paramètre de **commande** avec une entrée standard.</span><span class="sxs-lookup"><span data-stu-id="b222d-150">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="b222d-151">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b222d-151">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="b222d-152">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b222d-152">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="b222d-153">Le code de sortie du processus est déterminé par l’état de la dernière commande (exécutée) dans le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="b222d-153">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="b222d-154">Le code de sortie est `0` lorsque `$?` est `$true` ou `1` lorsque `$?` est `$false` .</span><span class="sxs-lookup"><span data-stu-id="b222d-154">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="b222d-155">Si la dernière commande est un programme externe ou un script PowerShell qui définit explicitement un code de sortie autre que `0` ou `1` , ce code de sortie est converti en `1` pour le code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="b222d-155">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="b222d-156">Pour conserver le code de sortie spécifique, ajoutez `exit $LASTEXITCODE` à votre chaîne de commande ou bloc de script.</span><span class="sxs-lookup"><span data-stu-id="b222d-156">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="b222d-157">De même, la valeur 1 est retournée quand une erreur de fin de script (arrêt d’exécution), telle que `throw` ou `-ErrorAction Stop` , se produit ou lorsque l’exécution est interrompue avec <kbd>CTRL</kbd> - <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b222d-157">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

### <a name="-configurationname---config"></a><span data-ttu-id="b222d-158">-ConfigurationName | -config</span><span class="sxs-lookup"><span data-stu-id="b222d-158">-ConfigurationName | -config</span></span>

<span data-ttu-id="b222d-159">Spécifie un point de terminaison de configuration dans lequel PowerShell est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b222d-159">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="b222d-160">Il peut s’agir de n’importe quel point de terminaison enregistré sur l’ordinateur local, y compris les points de terminaison de communication à distance PowerShell par défaut ou un point de terminaison personnalisé avec des fonctionnalités de rôle d’utilisateur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b222d-160">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

<span data-ttu-id="b222d-161">Exemple : `pwsh -ConfigurationName AdminRoles`</span><span class="sxs-lookup"><span data-stu-id="b222d-161">Example: `pwsh -ConfigurationName AdminRoles`</span></span>

### <a name="-custompipename"></a><span data-ttu-id="b222d-162">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="b222d-162">-CustomPipeName</span></span>

<span data-ttu-id="b222d-163">Spécifie le nom à utiliser pour un serveur IPC supplémentaire (canal nommé) utilisé pour le débogage et d’autres communications inter-processus.</span><span class="sxs-lookup"><span data-stu-id="b222d-163">Specifies the name to use for an additional IPC server (named pipe) used for debugging and other cross-process communication.</span></span> <span data-ttu-id="b222d-164">Cela offre un mécanisme prévisible pour la connexion à d’autres instances de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b222d-164">This offers a predictable mechanism for connecting to other PowerShell instances.</span></span> <span data-ttu-id="b222d-165">Généralement utilisé avec le paramètre **CustomPipeName** sur `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="b222d-165">Typically used with the **CustomPipeName** parameter on `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="b222d-166">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="b222d-166">This parameter was introduced in PowerShell 6.2.</span></span>

<span data-ttu-id="b222d-167">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b222d-167">For example:</span></span>

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a><span data-ttu-id="b222d-168">-EncodedCommand | -e | -EC</span><span class="sxs-lookup"><span data-stu-id="b222d-168">-EncodedCommand | -e | -ec</span></span>

<span data-ttu-id="b222d-169">Accepte une version de chaîne encodée en base64 d’une commande.</span><span class="sxs-lookup"><span data-stu-id="b222d-169">Accepts a Base64-encoded string version of a command.</span></span> <span data-ttu-id="b222d-170">Utilisez ce paramètre pour envoyer des commandes à PowerShell qui nécessitent un guillemet imbriqué complexe.</span><span class="sxs-lookup"><span data-stu-id="b222d-170">Use this parameter to submit commands to PowerShell that require complex, nested quoting.</span></span> <span data-ttu-id="b222d-171">La représentation base64 doit être une chaîne encodée en UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b222d-171">The Base64 representation must be a UTF-16 encoded string.</span></span>

<span data-ttu-id="b222d-172">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b222d-172">For example:</span></span>

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a><span data-ttu-id="b222d-173">-ExecutionPolicy | -ex | -EP</span><span class="sxs-lookup"><span data-stu-id="b222d-173">-ExecutionPolicy | -ex | -ep</span></span>

<span data-ttu-id="b222d-174">Définit la stratégie d’exécution par défaut pour la session active et l’enregistre dans la `$env:PSExecutionPolicyPreference` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="b222d-174">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="b222d-175">Ce paramètre ne modifie pas les stratégies d’exécution configurées de manière permanente.</span><span class="sxs-lookup"><span data-stu-id="b222d-175">This parameter does not change the persistently configured execution policies.</span></span>

<span data-ttu-id="b222d-176">Ce paramètre s’applique uniquement aux ordinateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="b222d-176">This parameter only applies to Windows computers.</span></span> <span data-ttu-id="b222d-177">La `$env:PSExecutionPolicyPreference` variable d’environnement n’existe pas sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="b222d-177">The `$env:PSExecutionPolicyPreference` environment variable does not exist on non-Windows platforms.</span></span>

### <a name="-inputformat---in---if"></a><span data-ttu-id="b222d-178">-InputFormat | -dans | -Si</span><span class="sxs-lookup"><span data-stu-id="b222d-178">-InputFormat | -in | -if</span></span>

<span data-ttu-id="b222d-179">Décrit le format des données envoyées à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b222d-179">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="b222d-180">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="b222d-180">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-interactive---i"></a><span data-ttu-id="b222d-181">-Interactif | -i</span><span class="sxs-lookup"><span data-stu-id="b222d-181">-Interactive | -i</span></span>

<span data-ttu-id="b222d-182">Présenter une invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b222d-182">Present an interactive prompt to the user.</span></span> <span data-ttu-id="b222d-183">Inverse pour le paramètre non interactif.</span><span class="sxs-lookup"><span data-stu-id="b222d-183">Inverse for NonInteractive parameter.</span></span>

### <a name="-noexit---noe"></a><span data-ttu-id="b222d-184">-NoExit | -noe</span><span class="sxs-lookup"><span data-stu-id="b222d-184">-NoExit | -noe</span></span>

<span data-ttu-id="b222d-185">Ne quitte pas après l’exécution de commandes de démarrage.</span><span class="sxs-lookup"><span data-stu-id="b222d-185">Does not exit after running startup commands.</span></span>

<span data-ttu-id="b222d-186">Exemple : `pwsh -NoExit -Command Get-Date`</span><span class="sxs-lookup"><span data-stu-id="b222d-186">Example: `pwsh -NoExit -Command Get-Date`</span></span>

### <a name="-nologo---nol"></a><span data-ttu-id="b222d-187">-Nologo | -nol</span><span class="sxs-lookup"><span data-stu-id="b222d-187">-NoLogo | -nol</span></span>

<span data-ttu-id="b222d-188">Masque la bannière de Copyright au démarrage de sessions interactives.</span><span class="sxs-lookup"><span data-stu-id="b222d-188">Hides the copyright banner at startup of interactive sessions.</span></span>

### <a name="-noninteractive---noni"></a><span data-ttu-id="b222d-189">-Non interactif | -noni</span><span class="sxs-lookup"><span data-stu-id="b222d-189">-NonInteractive | -noni</span></span>

<span data-ttu-id="b222d-190">Ne présente pas d’invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b222d-190">Does not present an interactive prompt to the user.</span></span> <span data-ttu-id="b222d-191">Toute tentative d’utiliser des fonctionnalités interactives, telles que `Read-Host` ou des invites de confirmation, entraîne des erreurs de fin d’instruction.</span><span class="sxs-lookup"><span data-stu-id="b222d-191">Any attempts to use interactive features, like `Read-Host` or confirmation prompts, result in statement-terminating errors.</span></span>

### <a name="-noprofile---nop"></a><span data-ttu-id="b222d-192">-Noprofile | -NOP</span><span class="sxs-lookup"><span data-stu-id="b222d-192">-NoProfile | -nop</span></span>

<span data-ttu-id="b222d-193">Ne charge pas les profils PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b222d-193">Does not load the PowerShell profiles.</span></span>

### <a name="-outputformat---o---of"></a><span data-ttu-id="b222d-194">-OutputFormat | -o | -de</span><span class="sxs-lookup"><span data-stu-id="b222d-194">-OutputFormat | -o | -of</span></span>

<span data-ttu-id="b222d-195">Détermine la mise en forme de la sortie de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b222d-195">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="b222d-196">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="b222d-196">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

<span data-ttu-id="b222d-197">Exemple : `pwsh -o XML -c Get-Date`</span><span class="sxs-lookup"><span data-stu-id="b222d-197">Example: `pwsh -o XML -c Get-Date`</span></span>

<span data-ttu-id="b222d-198">Quand elle est appelée avec une session PowerShell, vous pouvez obtenir des objets désérialisés en tant que chaînes de sortie plutôt que des chaînes brutes.</span><span class="sxs-lookup"><span data-stu-id="b222d-198">When called withing a PowerShell session, you get deserialized objects as output rather plain strings.</span></span> <span data-ttu-id="b222d-199">En cas d’appel à partir d’autres shells, la sortie est une chaîne de données mise en forme en tant que texte CLIXML.</span><span class="sxs-lookup"><span data-stu-id="b222d-199">When called from other shells, the output is string data formatted as CLIXML text.</span></span>

### <a name="-settingsfile---settings"></a><span data-ttu-id="b222d-200">-SettingsFile | -paramètres</span><span class="sxs-lookup"><span data-stu-id="b222d-200">-SettingsFile | -settings</span></span>

<span data-ttu-id="b222d-201">Remplace le `powershell.config.json` fichier de paramètres à l’ensemble du système pour la session.</span><span class="sxs-lookup"><span data-stu-id="b222d-201">Overrides the system-wide `powershell.config.json` settings file for the session.</span></span> <span data-ttu-id="b222d-202">Par défaut, les paramètres à l’ensemble du système sont lus à partir du `powershell.config.json` dans le `$PSHOME` répertoire.</span><span class="sxs-lookup"><span data-stu-id="b222d-202">By default, system-wide settings are read from the `powershell.config.json` in the `$PSHOME` directory.</span></span>

<span data-ttu-id="b222d-203">Notez que ces paramètres ne sont pas utilisés par le point de terminaison spécifié par l' `-ConfigurationName` argument.</span><span class="sxs-lookup"><span data-stu-id="b222d-203">Note that these settings are not used by the endpoint specified by the `-ConfigurationName` argument.</span></span>

<span data-ttu-id="b222d-204">Exemple : `pwsh -SettingsFile c:\myproject\powershell.config.json`</span><span class="sxs-lookup"><span data-stu-id="b222d-204">Example: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span></span>

### <a name="-sshservermode---sshs"></a><span data-ttu-id="b222d-205">-SSHServerMode | -sshs</span><span class="sxs-lookup"><span data-stu-id="b222d-205">-SSHServerMode | -sshs</span></span>

<span data-ttu-id="b222d-206">Utilisé dans sshd_config pour l’exécution de PowerShell en tant que sous-système SSH.</span><span class="sxs-lookup"><span data-stu-id="b222d-206">Used in sshd_config for running PowerShell as an SSH subsystem.</span></span> <span data-ttu-id="b222d-207">Elle n’est pas prévue ou prise en charge pour toute autre utilisation.</span><span class="sxs-lookup"><span data-stu-id="b222d-207">It is not intended or supported for any other use.</span></span>

### <a name="-version---v"></a><span data-ttu-id="b222d-208">-Version | -v</span><span class="sxs-lookup"><span data-stu-id="b222d-208">-Version | -v</span></span>

<span data-ttu-id="b222d-209">Affiche la version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b222d-209">Displays the version of PowerShell.</span></span> <span data-ttu-id="b222d-210">Les paramètres supplémentaires sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="b222d-210">Additional parameters are ignored.</span></span>

### <a name="-windowstyle---w"></a><span data-ttu-id="b222d-211">-WindowStyle | -w</span><span class="sxs-lookup"><span data-stu-id="b222d-211">-WindowStyle | -w</span></span>

<span data-ttu-id="b222d-212">Définit le style de fenêtre pour la session.</span><span class="sxs-lookup"><span data-stu-id="b222d-212">Sets the window style for the session.</span></span> <span data-ttu-id="b222d-213">Les valeurs valides sont Normal, Hidden, Minimized et Maximized.</span><span class="sxs-lookup"><span data-stu-id="b222d-213">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-workingdirectory---wd"></a><span data-ttu-id="b222d-214">-WorkingDirectory | -WD</span><span class="sxs-lookup"><span data-stu-id="b222d-214">-WorkingDirectory | -wd</span></span>

<span data-ttu-id="b222d-215">Définit le répertoire de travail initial en exécutant au démarrage.</span><span class="sxs-lookup"><span data-stu-id="b222d-215">Sets the initial working directory by executing at startup.</span></span> <span data-ttu-id="b222d-216">Tout chemin d’accès de fichier PowerShell valide est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b222d-216">Any valid PowerShell file path is supported.</span></span>

<span data-ttu-id="b222d-217">Pour démarrer PowerShell dans votre répertoire de départ, utilisez : `pwsh -WorkingDirectory ~`</span><span class="sxs-lookup"><span data-stu-id="b222d-217">To start PowerShell in your home directory, use: `pwsh -WorkingDirectory ~`</span></span>

### <a name="-help---"></a><span data-ttu-id="b222d-218">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="b222d-218">-Help, -?, /?</span></span>

<span data-ttu-id="b222d-219">Affiche l’aide pour `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="b222d-219">Displays help for `pwsh`.</span></span> <span data-ttu-id="b222d-220">Si vous tapez une commande pwsh dans PowerShell, faites précéder les paramètres de commande d’un trait d’Union ( `-` ), et non d’une barre oblique ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="b222d-220">If you are typing a pwsh command in PowerShell, prepend the command parameters with a hyphen (`-`), not a forward slash (`/`).</span></span>
