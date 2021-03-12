---
description: Explique comment utiliser l' `pwsh` interface de ligne de commande. Affiche les paramètres de ligne de commande et décrit la syntaxe.
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: a3420af2f46c7946d6282ca639117e4104d2bd17
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195959"
---
# <a name="about-pwsh"></a><span data-ttu-id="f122b-104">À propos de pwsh</span><span class="sxs-lookup"><span data-stu-id="f122b-104">About pwsh</span></span>

## <a name="short-description"></a><span data-ttu-id="f122b-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="f122b-105">Short Description</span></span>
<span data-ttu-id="f122b-106">Explique comment utiliser l' `pwsh` interface de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f122b-106">Explains how to use the `pwsh` command-line interface.</span></span> <span data-ttu-id="f122b-107">Affiche les paramètres de ligne de commande et décrit la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="f122b-107">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="f122b-108">Description longue</span><span class="sxs-lookup"><span data-stu-id="f122b-108">Long Description</span></span>

## <a name="syntax"></a><span data-ttu-id="f122b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f122b-109">Syntax</span></span>

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
   [-Login]
   [-MTA]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-SSHServerMode]
   [-STA]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="f122b-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f122b-110">Parameters</span></span>

<span data-ttu-id="f122b-111">Tous les paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="f122b-111">All parameters are case-insensitive.</span></span>

### <a name="-file---f"></a><span data-ttu-id="f122b-112">-File | -f</span><span class="sxs-lookup"><span data-stu-id="f122b-112">-File | -f</span></span>

<span data-ttu-id="f122b-113">Si la valeur de `File` est `-` , le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="f122b-113">If the value of `File` is `-`, the command text is read from standard input.</span></span>
<span data-ttu-id="f122b-114">L’exécution `pwsh -File -` sans une entrée standard redirigée démarre une session normale.</span><span class="sxs-lookup"><span data-stu-id="f122b-114">Running `pwsh -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="f122b-115">Cela revient à ne pas spécifier le `File` paramètre du tout.</span><span class="sxs-lookup"><span data-stu-id="f122b-115">This is the same as not specifying the `File` parameter at all.</span></span>

<span data-ttu-id="f122b-116">Il s’agit du paramètre par défaut si aucun paramètre n’est présent, mais que des valeurs sont présentes dans la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f122b-116">This is the default parameter if no parameters are present but values are present in the command line.</span></span> <span data-ttu-id="f122b-117">Le script spécifié s’exécute dans l’étendue locale (« point-source »), afin que les fonctions et variables créées par le script soient disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f122b-117">The specified script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="f122b-118">Entrez le chemin d’accès au fichier de script et les paramètres éventuels.</span><span class="sxs-lookup"><span data-stu-id="f122b-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="f122b-119">Le fichier doit être le dernier paramètre de la commande, car tous les caractères tapés après le nom du paramètre de fichier sont interprétés comme étant le chemin du fichier de script suivi des paramètres du script.</span><span class="sxs-lookup"><span data-stu-id="f122b-119">File must be the last parameter in the command, because all characters typed after the File parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="f122b-120">En règle générale, les paramètres de commutateur d’un script sont inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="f122b-120">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="f122b-121">Par exemple, la commande suivante utilise le paramètre All de l' Get-Script.ps1 fichier de script : `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="f122b-121">For example, the following command uses the All parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="f122b-122">Dans de rares cas, vous devrez peut-être fournir une valeur **booléenne** pour un paramètre de commutateur.</span><span class="sxs-lookup"><span data-stu-id="f122b-122">In rare cases, you might need to provide a **Boolean** value for a switch parameter.</span></span> <span data-ttu-id="f122b-123">Pour fournir une valeur **booléenne** pour un paramètre de commutateur dans la valeur du paramètre **file** , utilisez le paramètre normalement suivi immédiatement par un signe deux-points et la valeur booléenne, comme suit : `-File .\Get-Script.ps1 -All:$False` .</span><span class="sxs-lookup"><span data-stu-id="f122b-123">To provide a **Boolean** value for a switch parameter in the value of the **File** parameter, Use the parameter normally followed immediately by a colon and the boolean value, such as the following: `-File .\Get-Script.ps1 -All:$False`.</span></span>

<span data-ttu-id="f122b-124">Les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel).</span><span class="sxs-lookup"><span data-stu-id="f122b-124">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="f122b-125">Par exemple, si vous êtes dans `cmd.exe` et que vous souhaitez passer une valeur de variable d’environnement, vous devez utiliser la `cmd.exe` syntaxe suivante : `pwsh -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="f122b-125">For example, if you are in `cmd.exe` and want to pass an environment variable value, you would use the `cmd.exe` syntax: `pwsh -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="f122b-126">En revanche, `pwsh -File .\test.ps1 -TestParam $env:windir` l’exécution de dans `cmd.exe` entraîne la réception par le script de la chaîne littérale `$env:windir` , car elle n’a aucune signification particulière pour l’interpréteur de commandes actuel `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="f122b-126">In contrast, running `pwsh -File .\test.ps1 -TestParam $env:windir` in `cmd.exe` results in the script receiving the literal string `$env:windir` because it has no special meaning to the current `cmd.exe` shell.</span></span> <span data-ttu-id="f122b-127">Le `$env:windir` style de référence de variable d’environnement _peut_ être utilisé dans un paramètre de **commande** , car il est interprété comme du code PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f122b-127">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it is interpreted as PowerShell code.</span></span>

<span data-ttu-id="f122b-128">De même, si vous souhaitez exécuter la même commande à partir d’un _script de commandes_, vous devez utiliser à la `%~dp0` place de `.\` ou `$PSScriptRoot` pour représenter le répertoire d’exécution actuel : `pwsh -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="f122b-128">Similarly, if you want to execute the same command from a _Batch script_, you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `pwsh -File %~dp0test.ps1 -TestParam %windir%`.</span></span> <span data-ttu-id="f122b-129">Si vous l’utilisez à la place `.\test.ps1` , PowerShell lèvera une erreur, car il ne peut pas trouver le chemin d’accès littéral `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="f122b-129">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="f122b-130">Lorsque le fichier de script se termine par une `exit` commande, le code de sortie du processus est défini sur l’argument numérique utilisé avec la `exit` commande.</span><span class="sxs-lookup"><span data-stu-id="f122b-130">When the script file terminates with an `exit` command, the process exit code is set to the numeric argument used with the `exit` command.</span></span> <span data-ttu-id="f122b-131">Avec un arrêt normal, le code de sortie est toujours `0` .</span><span class="sxs-lookup"><span data-stu-id="f122b-131">With normal termination, the exit code is always `0`.</span></span>

<span data-ttu-id="f122b-132">Semblable à `-Command` , quand une erreur de fin de script se produit, le code de sortie est défini sur `1` .</span><span class="sxs-lookup"><span data-stu-id="f122b-132">Similar to `-Command`, when a script-terminating error occurs, the exit code is set to `1`.</span></span> <span data-ttu-id="f122b-133">Toutefois, contrairement à `-Command` , lorsque l’exécution est interrompue avec <kbd>CTRL</kbd> - <kbd>C</kbd> , le code de sortie est `0` .</span><span class="sxs-lookup"><span data-stu-id="f122b-133">However, unlike with `-Command`, when the execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd> the exit code is `0`.</span></span>

### <a name="-command---c"></a><span data-ttu-id="f122b-134">-Commande | -c</span><span class="sxs-lookup"><span data-stu-id="f122b-134">-Command | -c</span></span>

<span data-ttu-id="f122b-135">Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell, puis se ferme, sauf si le `NoExit` paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="f122b-135">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="f122b-136">La valeur de **Command** peut être `-` , un bloc de script ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f122b-136">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="f122b-137">Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="f122b-137">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="f122b-138">Le paramètre de **commande** n’accepte qu’un bloc de script pour l’exécution lorsqu’il peut reconnaître la valeur passée à la **commande** en tant que type **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="f122b-138">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="f122b-139">Cela est possible _uniquement_ lors de l’exécution `pwsh` à partir d’un autre hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f122b-139">This is _only_ possible when running `pwsh` from another PowerShell host.</span></span> <span data-ttu-id="f122b-140">Le type **scriptblock** peut être contenu dans une variable existante, retournée à partir d’une expression, ou analysé par l’hôte PowerShell sous la forme d’un bloc de script littéral placé entre accolades ( `{}` ), avant d’être passé à `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="f122b-140">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `pwsh`.</span></span>

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="f122b-141">Dans `cmd.exe` , il n’existe aucun bloc de script (ou type **scriptblock** ), donc la valeur transmise à la **commande** sera _toujours_ une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f122b-141">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="f122b-142">Si vous écrivez un bloc de script dans la chaîne, il se comportera exactement comme s’il avait été tapé dans une invite PowerShell classique, affichant le contenu du bloc de script au lieu de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="f122b-142">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="f122b-143">Une chaîne transmise à la **commande** est toujours exécutée comme code PowerShell, donc les accolades de bloc de script ne sont souvent pas requises dans le premier emplacement lors de l’exécution à partir de `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="f122b-143">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="f122b-144">Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, il est possible d’utiliser [l’opérateur d’appel](about_operators.md#special-operators) `&` :</span><span class="sxs-lookup"><span data-stu-id="f122b-144">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="f122b-145">Si la valeur de **Command** est une chaîne, **Command** doit être le dernier paramètre de pwsh, car tous les arguments qui le suivent sont interprétés comme faisant partie de la commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="f122b-145">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="f122b-146">Quand elle est appelée à partir d’une session PowerShell existante, les résultats sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs.</span><span class="sxs-lookup"><span data-stu-id="f122b-146">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="f122b-147">Pour les autres shells, les résultats sont retournés sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="f122b-147">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="f122b-148">Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="f122b-148">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="f122b-149">Vous devez rediriger l’entrée standard lors de l’utilisation du paramètre de **commande** avec une entrée standard.</span><span class="sxs-lookup"><span data-stu-id="f122b-149">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="f122b-150">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f122b-150">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="f122b-151">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f122b-151">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="f122b-152">Le code de sortie du processus est déterminé par l’état de la dernière commande (exécutée) dans le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="f122b-152">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="f122b-153">Le code de sortie est `0` lorsque `$?` est `$true` ou `1` lorsque `$?` est `$false` .</span><span class="sxs-lookup"><span data-stu-id="f122b-153">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="f122b-154">Si la dernière commande est un programme externe ou un script PowerShell qui définit explicitement un code de sortie autre que `0` ou `1` , ce code de sortie est converti en `1` pour le code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="f122b-154">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="f122b-155">Pour conserver le code de sortie spécifique, ajoutez `exit $LASTEXITCODE` à votre chaîne de commande ou bloc de script.</span><span class="sxs-lookup"><span data-stu-id="f122b-155">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="f122b-156">De même, la valeur 1 est retournée quand une erreur de fin de script (arrêt d’exécution), telle que `throw` ou `-ErrorAction Stop` , se produit ou lorsque l’exécution est interrompue avec <kbd>CTRL</kbd> - <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f122b-156">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

### <a name="-configurationname---config"></a><span data-ttu-id="f122b-157">-ConfigurationName | -config</span><span class="sxs-lookup"><span data-stu-id="f122b-157">-ConfigurationName | -config</span></span>

<span data-ttu-id="f122b-158">Spécifie un point de terminaison de configuration dans lequel PowerShell est exécuté.</span><span class="sxs-lookup"><span data-stu-id="f122b-158">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="f122b-159">Il peut s’agir de n’importe quel point de terminaison enregistré sur l’ordinateur local, y compris les points de terminaison de communication à distance PowerShell par défaut ou un point de terminaison personnalisé avec des fonctionnalités de rôle d’utilisateur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f122b-159">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

<span data-ttu-id="f122b-160">Exemple : `pwsh -ConfigurationName AdminRoles`</span><span class="sxs-lookup"><span data-stu-id="f122b-160">Example: `pwsh -ConfigurationName AdminRoles`</span></span>

### <a name="-custompipename"></a><span data-ttu-id="f122b-161">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="f122b-161">-CustomPipeName</span></span>

<span data-ttu-id="f122b-162">Spécifie le nom à utiliser pour un serveur IPC supplémentaire (canal nommé) utilisé pour le débogage et d’autres communications inter-processus.</span><span class="sxs-lookup"><span data-stu-id="f122b-162">Specifies the name to use for an additional IPC server (named pipe) used for debugging and other cross-process communication.</span></span> <span data-ttu-id="f122b-163">Cela offre un mécanisme prévisible pour la connexion à d’autres instances de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f122b-163">This offers a predictable mechanism for connecting to other PowerShell instances.</span></span> <span data-ttu-id="f122b-164">Généralement utilisé avec le paramètre **CustomPipeName** sur `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="f122b-164">Typically used with the **CustomPipeName** parameter on `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="f122b-165">Ce paramètre a été introduit dans PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="f122b-165">This parameter was introduced in PowerShell 6.2.</span></span>

<span data-ttu-id="f122b-166">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f122b-166">For example:</span></span>

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a><span data-ttu-id="f122b-167">-EncodedCommand | -e | -EC</span><span class="sxs-lookup"><span data-stu-id="f122b-167">-EncodedCommand | -e | -ec</span></span>

<span data-ttu-id="f122b-168">Accepte une version de chaîne encodée en base64 d’une commande.</span><span class="sxs-lookup"><span data-stu-id="f122b-168">Accepts a Base64-encoded string version of a command.</span></span> <span data-ttu-id="f122b-169">Utilisez ce paramètre pour envoyer des commandes à PowerShell qui nécessitent un guillemet imbriqué complexe.</span><span class="sxs-lookup"><span data-stu-id="f122b-169">Use this parameter to submit commands to PowerShell that require complex, nested quoting.</span></span> <span data-ttu-id="f122b-170">La représentation base64 doit être une chaîne encodée en UTF-16LE.</span><span class="sxs-lookup"><span data-stu-id="f122b-170">The Base64 representation must be a UTF-16LE encoded string.</span></span>

<span data-ttu-id="f122b-171">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f122b-171">For example:</span></span>

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a><span data-ttu-id="f122b-172">-ExecutionPolicy | -ex | -EP</span><span class="sxs-lookup"><span data-stu-id="f122b-172">-ExecutionPolicy | -ex | -ep</span></span>

<span data-ttu-id="f122b-173">Définit la stratégie d’exécution par défaut pour la session active et l’enregistre dans la `$env:PSExecutionPolicyPreference` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f122b-173">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="f122b-174">Ce paramètre ne modifie pas les stratégies d’exécution configurées de manière permanente.</span><span class="sxs-lookup"><span data-stu-id="f122b-174">This parameter does not change the persistently configured execution policies.</span></span>

<span data-ttu-id="f122b-175">Ce paramètre s’applique uniquement aux ordinateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="f122b-175">This parameter only applies to Windows computers.</span></span> <span data-ttu-id="f122b-176">La `$env:PSExecutionPolicyPreference` variable d’environnement n’existe pas sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="f122b-176">The `$env:PSExecutionPolicyPreference` environment variable does not exist on non-Windows platforms.</span></span>

### <a name="-inputformat---inp---if"></a><span data-ttu-id="f122b-177">-InputFormat | -INP | -Si</span><span class="sxs-lookup"><span data-stu-id="f122b-177">-InputFormat | -inp | -if</span></span>

<span data-ttu-id="f122b-178">Décrit le format des données envoyées à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f122b-178">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="f122b-179">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="f122b-179">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-interactive---i"></a><span data-ttu-id="f122b-180">-Interactif | -i</span><span class="sxs-lookup"><span data-stu-id="f122b-180">-Interactive | -i</span></span>

<span data-ttu-id="f122b-181">Présenter une invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f122b-181">Present an interactive prompt to the user.</span></span> <span data-ttu-id="f122b-182">Inverse pour le paramètre non interactif.</span><span class="sxs-lookup"><span data-stu-id="f122b-182">Inverse for NonInteractive parameter.</span></span>

### <a name="-login---l"></a><span data-ttu-id="f122b-183">-Connexion | -l</span><span class="sxs-lookup"><span data-stu-id="f122b-183">-Login | -l</span></span>

<span data-ttu-id="f122b-184">Sur Linux et macOS, démarre PowerShell comme un shell de connexion, en utilisant/bin/sh pour exécuter des profils de connexion tels que/etc/profile et ~/.Profile.</span><span class="sxs-lookup"><span data-stu-id="f122b-184">On Linux and macOS, starts PowerShell as a login shell, using /bin/sh to execute login profiles such as /etc/profile and ~/.profile.</span></span>
<span data-ttu-id="f122b-185">Sur Windows, ce commutateur ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="f122b-185">On Windows, this switch does nothing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f122b-186">Ce paramètre doit être en premier pour démarrer PowerShell en tant qu’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="f122b-186">This parameter must come first to start PowerShell as a login shell.</span></span>
> <span data-ttu-id="f122b-187">La transmission de ce paramètre à une autre position sera ignorée.</span><span class="sxs-lookup"><span data-stu-id="f122b-187">Passing this parameter in another position will be ignored.</span></span>

<span data-ttu-id="f122b-188">Pour configurer `pwsh` en tant que Shell de connexion sur les systèmes d’exploitation de type UNIX :</span><span class="sxs-lookup"><span data-stu-id="f122b-188">To set up `pwsh` as the login shell on UNIX-like operating systems:</span></span>

- <span data-ttu-id="f122b-189">Vérifiez que le chemin d’accès absolu complet à `pwsh` est indiqué sous `/etc/shells`</span><span class="sxs-lookup"><span data-stu-id="f122b-189">Verify that the full absolute path to `pwsh` is listed under `/etc/shells`</span></span>
  - <span data-ttu-id="f122b-190">Ce chemin d’accès est généralement similaire `/usr/bin/pwsh` sur Linux ou `/usr/local/bin/pwsh` MacOS</span><span class="sxs-lookup"><span data-stu-id="f122b-190">This path is usually something like `/usr/bin/pwsh` on Linux or `/usr/local/bin/pwsh` on macOS</span></span>
  - <span data-ttu-id="f122b-191">Avec certaines méthodes d’installation, cette entrée sera ajoutée automatiquement au moment de l’installation</span><span class="sxs-lookup"><span data-stu-id="f122b-191">With some installation methods, this entry will be added automatically at installation time</span></span>
  - <span data-ttu-id="f122b-192">Si `pwsh` n’est pas présent dans `/etc/shells` , utilisez un éditeur pour ajouter le chemin d’accès à `pwsh` la dernière ligne.</span><span class="sxs-lookup"><span data-stu-id="f122b-192">If `pwsh` is not present in `/etc/shells`, use an editor to append the path to `pwsh` on the last line.</span></span> <span data-ttu-id="f122b-193">Cela nécessite des privilèges élevés pour la modification.</span><span class="sxs-lookup"><span data-stu-id="f122b-193">This requires elevated privileges to edit.</span></span>
- <span data-ttu-id="f122b-194">Utilisez l’utilitaire [CHSH](https://linux.die.net/man/1/chsh) pour définir le shell de l’utilisateur actuel sur `pwsh` :</span><span class="sxs-lookup"><span data-stu-id="f122b-194">Use the [chsh](https://linux.die.net/man/1/chsh) utility to set your current user's shell to `pwsh`:</span></span>

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> <span data-ttu-id="f122b-195">La définition de `pwsh` l’environnement de connexion n’est pas prise en charge actuellement sur le sous-système Windows pour Linux (WSL) et la tentative de définition `pwsh` en tant que Shell de connexion peut entraîner l’impossibilité de démarrer WSL de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="f122b-195">Setting `pwsh` as the login shell is currently not supported on Windows Subsystem for Linux (WSL), and attempting to set `pwsh` as the login shell there may lead to being unable to start WSL interactively.</span></span>

### <a name="-mta"></a><span data-ttu-id="f122b-196">-MTA</span><span class="sxs-lookup"><span data-stu-id="f122b-196">-MTA</span></span>

<span data-ttu-id="f122b-197">Démarrez PowerShell à l’aide d’un cloisonnement multithread.</span><span class="sxs-lookup"><span data-stu-id="f122b-197">Start PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="f122b-198">Ce commutateur est disponible uniquement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="f122b-198">This switch is only available on Windows.</span></span>

### <a name="-noexit---noe"></a><span data-ttu-id="f122b-199">-NoExit | -noe</span><span class="sxs-lookup"><span data-stu-id="f122b-199">-NoExit | -noe</span></span>

<span data-ttu-id="f122b-200">Ne quitte pas après l’exécution de commandes de démarrage.</span><span class="sxs-lookup"><span data-stu-id="f122b-200">Does not exit after running startup commands.</span></span>

<span data-ttu-id="f122b-201">Exemple : `pwsh -NoExit -Command Get-Date`</span><span class="sxs-lookup"><span data-stu-id="f122b-201">Example: `pwsh -NoExit -Command Get-Date`</span></span>

### <a name="-nologo---nol"></a><span data-ttu-id="f122b-202">-Nologo | -nol</span><span class="sxs-lookup"><span data-stu-id="f122b-202">-NoLogo | -nol</span></span>

<span data-ttu-id="f122b-203">Masque la bannière de Copyright au démarrage de sessions interactives.</span><span class="sxs-lookup"><span data-stu-id="f122b-203">Hides the copyright banner at startup of interactive sessions.</span></span>

### <a name="-noninteractive---noni"></a><span data-ttu-id="f122b-204">-Non interactif | -noni</span><span class="sxs-lookup"><span data-stu-id="f122b-204">-NonInteractive | -noni</span></span>

<span data-ttu-id="f122b-205">Ne présente pas d’invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f122b-205">Does not present an interactive prompt to the user.</span></span> <span data-ttu-id="f122b-206">Toute tentative d’utiliser des fonctionnalités interactives, telles que `Read-Host` ou des invites de confirmation, entraîne des erreurs de fin d’instruction.</span><span class="sxs-lookup"><span data-stu-id="f122b-206">Any attempts to use interactive features, like `Read-Host` or confirmation prompts, result in statement-terminating errors.</span></span>

### <a name="-noprofile---nop"></a><span data-ttu-id="f122b-207">-Noprofile | -NOP</span><span class="sxs-lookup"><span data-stu-id="f122b-207">-NoProfile | -nop</span></span>

<span data-ttu-id="f122b-208">Ne charge pas les profils PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f122b-208">Does not load the PowerShell profiles.</span></span>

### <a name="-outputformat---o---of"></a><span data-ttu-id="f122b-209">-OutputFormat | -o | -de</span><span class="sxs-lookup"><span data-stu-id="f122b-209">-OutputFormat | -o | -of</span></span>

<span data-ttu-id="f122b-210">Détermine la mise en forme de la sortie de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f122b-210">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="f122b-211">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="f122b-211">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

<span data-ttu-id="f122b-212">Exemple : `pwsh -o XML -c Get-Date`</span><span class="sxs-lookup"><span data-stu-id="f122b-212">Example: `pwsh -o XML -c Get-Date`</span></span>

<span data-ttu-id="f122b-213">Quand elle est appelée avec une session PowerShell, vous pouvez obtenir des objets désérialisés en tant que chaînes de sortie plutôt que des chaînes brutes.</span><span class="sxs-lookup"><span data-stu-id="f122b-213">When called withing a PowerShell session, you get deserialized objects as output rather plain strings.</span></span> <span data-ttu-id="f122b-214">En cas d’appel à partir d’autres shells, la sortie est une chaîne de données mise en forme en tant que texte CLIXML.</span><span class="sxs-lookup"><span data-stu-id="f122b-214">When called from other shells, the output is string data formatted as CLIXML text.</span></span>

### <a name="-settingsfile---settings"></a><span data-ttu-id="f122b-215">-SettingsFile | -paramètres</span><span class="sxs-lookup"><span data-stu-id="f122b-215">-SettingsFile | -settings</span></span>

<span data-ttu-id="f122b-216">Remplace le `powershell.config.json` fichier de paramètres à l’ensemble du système pour la session.</span><span class="sxs-lookup"><span data-stu-id="f122b-216">Overrides the system-wide `powershell.config.json` settings file for the session.</span></span> <span data-ttu-id="f122b-217">Par défaut, les paramètres à l’ensemble du système sont lus à partir du `powershell.config.json` dans le `$PSHOME` répertoire.</span><span class="sxs-lookup"><span data-stu-id="f122b-217">By default, system-wide settings are read from the `powershell.config.json` in the `$PSHOME` directory.</span></span>

<span data-ttu-id="f122b-218">Notez que ces paramètres ne sont pas utilisés par le point de terminaison spécifié par l' `-ConfigurationName` argument.</span><span class="sxs-lookup"><span data-stu-id="f122b-218">Note that these settings are not used by the endpoint specified by the `-ConfigurationName` argument.</span></span>

<span data-ttu-id="f122b-219">Exemple : `pwsh -SettingsFile c:\myproject\powershell.config.json`</span><span class="sxs-lookup"><span data-stu-id="f122b-219">Example: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span></span>

### <a name="-sshservermode---sshs"></a><span data-ttu-id="f122b-220">-SSHServerMode | -sshs</span><span class="sxs-lookup"><span data-stu-id="f122b-220">-SSHServerMode | -sshs</span></span>

<span data-ttu-id="f122b-221">Utilisé dans sshd_config pour l’exécution de PowerShell en tant que sous-système SSH.</span><span class="sxs-lookup"><span data-stu-id="f122b-221">Used in sshd_config for running PowerShell as an SSH subsystem.</span></span> <span data-ttu-id="f122b-222">Elle n’est pas prévue ou prise en charge pour toute autre utilisation.</span><span class="sxs-lookup"><span data-stu-id="f122b-222">It is not intended or supported for any other use.</span></span>

### <a name="-sta"></a><span data-ttu-id="f122b-223">-STA</span><span class="sxs-lookup"><span data-stu-id="f122b-223">-STA</span></span>

<span data-ttu-id="f122b-224">Démarrez PowerShell à l’aide d’un cloisonnement à thread unique.</span><span class="sxs-lookup"><span data-stu-id="f122b-224">Start PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="f122b-225">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f122b-225">This is the default.</span></span> <span data-ttu-id="f122b-226">Ce commutateur est disponible uniquement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="f122b-226">This switch is only available on Windows.</span></span>

### <a name="-version---v"></a><span data-ttu-id="f122b-227">-Version | -v</span><span class="sxs-lookup"><span data-stu-id="f122b-227">-Version | -v</span></span>

<span data-ttu-id="f122b-228">Affiche la version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f122b-228">Displays the version of PowerShell.</span></span> <span data-ttu-id="f122b-229">Les paramètres supplémentaires sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="f122b-229">Additional parameters are ignored.</span></span>

### <a name="-windowstyle---w"></a><span data-ttu-id="f122b-230">-WindowStyle | -w</span><span class="sxs-lookup"><span data-stu-id="f122b-230">-WindowStyle | -w</span></span>

<span data-ttu-id="f122b-231">Définit le style de fenêtre pour la session.</span><span class="sxs-lookup"><span data-stu-id="f122b-231">Sets the window style for the session.</span></span> <span data-ttu-id="f122b-232">Les valeurs valides sont Normal, Hidden, Minimized et Maximized.</span><span class="sxs-lookup"><span data-stu-id="f122b-232">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-workingdirectory---wd"></a><span data-ttu-id="f122b-233">-WorkingDirectory | -WD</span><span class="sxs-lookup"><span data-stu-id="f122b-233">-WorkingDirectory | -wd</span></span>

<span data-ttu-id="f122b-234">Définit le répertoire de travail initial en exécutant au démarrage.</span><span class="sxs-lookup"><span data-stu-id="f122b-234">Sets the initial working directory by executing at startup.</span></span> <span data-ttu-id="f122b-235">Tout chemin d’accès de fichier PowerShell valide est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f122b-235">Any valid PowerShell file path is supported.</span></span>

<span data-ttu-id="f122b-236">Pour démarrer PowerShell dans votre répertoire de départ, utilisez : `pwsh -WorkingDirectory ~`</span><span class="sxs-lookup"><span data-stu-id="f122b-236">To start PowerShell in your home directory, use: `pwsh -WorkingDirectory ~`</span></span>

### <a name="-help---"></a><span data-ttu-id="f122b-237">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="f122b-237">-Help, -?, /?</span></span>

<span data-ttu-id="f122b-238">Affiche l’aide pour `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="f122b-238">Displays help for `pwsh`.</span></span> <span data-ttu-id="f122b-239">Si vous tapez une commande pwsh dans PowerShell, faites précéder les paramètres de commande d’un trait d’Union ( `-` ), et non d’une barre oblique ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="f122b-239">If you are typing a pwsh command in PowerShell, prepend the command parameters with a hyphen (`-`), not a forward slash (`/`).</span></span>
