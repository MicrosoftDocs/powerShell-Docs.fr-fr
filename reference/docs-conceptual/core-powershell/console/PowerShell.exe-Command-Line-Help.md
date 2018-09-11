---
ms.date: 08/14/2018
keywords: powershell,applet de commande
title: Aide sur la ligne de commande PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133101"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="9fc11-103">Aide sur la ligne de commande PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="9fc11-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="9fc11-104">Vous pouvez utiliser PowerShell.exe pour démarrer une session PowerShell à partir de la ligne de commande d’un autre outil, tel que Cmd.exe, ou l’utiliser dans la ligne de commande PowerShell pour démarrer une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="9fc11-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="9fc11-105">Utilisez les paramètres pour personnaliser la session.</span><span class="sxs-lookup"><span data-stu-id="9fc11-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="9fc11-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fc11-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="9fc11-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fc11-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="9fc11-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="9fc11-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="9fc11-109">Accepte une version de chaîne codée en base 64 d’une commande.</span><span class="sxs-lookup"><span data-stu-id="9fc11-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="9fc11-110">Utilisez ce paramètre pour envoyer à PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes.</span><span class="sxs-lookup"><span data-stu-id="9fc11-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="9fc11-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="9fc11-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="9fc11-112">Définit la stratégie d’exécution par défaut pour la session actuelle et l’enregistre dans la variable d’environnement $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="9fc11-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="9fc11-113">Ce paramètre ne modifie pas la stratégie d’exécution PowerShell qui est définie dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="9fc11-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="9fc11-114">Pour plus d’informations sur les stratégies d’exécution PowerShell, notamment une liste de valeurs valides, consultez [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="9fc11-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="9fc11-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="9fc11-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="9fc11-116">Exécute le script spécifié dans l’étendue locale (avec « dot-sourcing »), afin que les fonctions et variables créées par le script soient disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="9fc11-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="9fc11-117">Entrez le chemin d’accès au fichier de script et les paramètres éventuels.</span><span class="sxs-lookup"><span data-stu-id="9fc11-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="9fc11-118">**File** doit être le dernier paramètre dans la commande.</span><span class="sxs-lookup"><span data-stu-id="9fc11-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="9fc11-119">Toutes les valeurs saisies après le paramètre **-File** sont interprétées comme les paramètres et le chemin d’accès au fichier de script passés à ce script.</span><span class="sxs-lookup"><span data-stu-id="9fc11-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="9fc11-120">Les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel).</span><span class="sxs-lookup"><span data-stu-id="9fc11-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="9fc11-121">Par exemple, si vous êtes dans cmd.exe et que vous souhaitez passer une valeur de variable d’environnement, vous utilisez la syntaxe de cmd.exe : `powershell -File .\test.ps1 -Sample %windir%` Dans cet exemple, votre script reçoit la chaîne littérale `$env:windir`, et non la valeur de cette variable d’environnement : `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="9fc11-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="9fc11-122">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="9fc11-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="9fc11-123">Décrit le format des données envoyées à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fc11-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="9fc11-124">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="9fc11-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="9fc11-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="9fc11-125">-Mta</span></span>

<span data-ttu-id="9fc11-126">Démarre PowerShell à l’aide d’un cloisonnement multithread.</span><span class="sxs-lookup"><span data-stu-id="9fc11-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="9fc11-127">Ce paramètre est introduit dans PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9fc11-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="9fc11-128">Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="9fc11-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9fc11-129">Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="9fc11-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="9fc11-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="9fc11-130">-NoExit</span></span>

<span data-ttu-id="9fc11-131">Ne quitte pas après l’exécution de commandes de démarrage.</span><span class="sxs-lookup"><span data-stu-id="9fc11-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="9fc11-132">-Nologo</span><span class="sxs-lookup"><span data-stu-id="9fc11-132">-NoLogo</span></span>

<span data-ttu-id="9fc11-133">Masque la bannière de copyright au démarrage.</span><span class="sxs-lookup"><span data-stu-id="9fc11-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="9fc11-134">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="9fc11-134">-NonInteractive</span></span>

<span data-ttu-id="9fc11-135">Ne présente pas d’invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9fc11-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="9fc11-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="9fc11-136">-NoProfile</span></span>

<span data-ttu-id="9fc11-137">Ne charge pas le profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fc11-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="9fc11-138">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="9fc11-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="9fc11-139">Détermine la mise en forme de la sortie de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fc11-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="9fc11-140">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="9fc11-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="9fc11-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="9fc11-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="9fc11-142">Charge le fichier de console PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="9fc11-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="9fc11-143">Entrez le chemin d’accès et le nom du fichier de console.</span><span class="sxs-lookup"><span data-stu-id="9fc11-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="9fc11-144">Pour créer un fichier de console, utilisez la cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fc11-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="9fc11-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="9fc11-145">-Sta</span></span>

<span data-ttu-id="9fc11-146">Démarre PowerShell à l’aide d’un cloisonnement monothread.</span><span class="sxs-lookup"><span data-stu-id="9fc11-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="9fc11-147">Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="9fc11-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9fc11-148">Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="9fc11-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="9fc11-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="9fc11-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="9fc11-150">Démarre la version spécifiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fc11-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="9fc11-151">La version que vous spécifiez doit être installée sur le système.</span><span class="sxs-lookup"><span data-stu-id="9fc11-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="9fc11-152">Si PowerShell 3.0 est installé sur l’ordinateur, les valeurs valides sont « 2.0 » et « 3.0 ».</span><span class="sxs-lookup"><span data-stu-id="9fc11-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="9fc11-153">La valeur par défaut est « 3.0 ».</span><span class="sxs-lookup"><span data-stu-id="9fc11-153">The default value is "3.0".</span></span>

<span data-ttu-id="9fc11-154">Si PowerShell 3.0 n’est pas installé, la seule valeur valide est « 2.0 ».</span><span class="sxs-lookup"><span data-stu-id="9fc11-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="9fc11-155">Les autres valeurs sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="9fc11-155">Other values are ignored.</span></span>

<span data-ttu-id="9fc11-156">Pour plus d’informations, voir [Installation de Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9fc11-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="9fc11-157">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="9fc11-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="9fc11-158">Définit le style de fenêtre pour la session.</span><span class="sxs-lookup"><span data-stu-id="9fc11-158">Sets the window style for the session.</span></span> <span data-ttu-id="9fc11-159">Les valeurs valides sont Normal, Hidden, Minimized et Maximized.</span><span class="sxs-lookup"><span data-stu-id="9fc11-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="9fc11-160">-Command</span><span class="sxs-lookup"><span data-stu-id="9fc11-160">-Command</span></span>

<span data-ttu-id="9fc11-161">Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fc11-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="9fc11-162">Après l’exécution, PowerShell s’arrête, sauf si le paramètre `-NoExit` est précisé.</span><span class="sxs-lookup"><span data-stu-id="9fc11-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="9fc11-163">Tout texte qui suit `-Command` est envoyé en tant qu’une seule ligne de commande à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fc11-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="9fc11-164">Cela diffère de la façon dont `-File` gère les paramètres envoyés à un script.</span><span class="sxs-lookup"><span data-stu-id="9fc11-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="9fc11-165">La valeur de Command peut être « - », une chaîne</span><span class="sxs-lookup"><span data-stu-id="9fc11-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="9fc11-166">ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="9fc11-166">or a script block.</span></span> <span data-ttu-id="9fc11-167">Si la valeur de Command est « - », le texte de commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="9fc11-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="9fc11-168">Les blocs de script doivent être entourés d’accolades ({}).</span><span class="sxs-lookup"><span data-stu-id="9fc11-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="9fc11-169">Vous pouvez spécifier un bloc de script uniquement lors de l’exécution de PowerShell.exe dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fc11-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="9fc11-170">Les résultats du script sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs.</span><span class="sxs-lookup"><span data-stu-id="9fc11-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="9fc11-171">Si la valeur de Command est une chaîne, **Command** doit être le dernier paramètre de la commande, car les caractères tapés après la commande sont interprétés comme étant des arguments de la commande.</span><span class="sxs-lookup"><span data-stu-id="9fc11-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="9fc11-172">Pour écrire une chaîne exécutant une commande PowerShell, utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="9fc11-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="9fc11-173">Les guillemets indiquent une chaîne et l’opérateur d’appel (&) déclenche l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="9fc11-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="9fc11-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="9fc11-174">-Help, -?, /?</span></span>

<span data-ttu-id="9fc11-175">Illustre la syntaxe de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="9fc11-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="9fc11-176">Si vous tapez une commande PowerShell.exe dans PowerShell, faites précéder les paramètres de commande d’un trait d’union (-), et non d’une barre oblique (/).</span><span class="sxs-lookup"><span data-stu-id="9fc11-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="9fc11-177">Vous pouvez utiliser un trait d’union ou une barre oblique dans Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9fc11-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="9fc11-178">Remarque sur la résolution de problèmes : dans PowerShell 2.0, le démarrage de certains programmes dans la console Windows PowerShell échoue en signalant un LastExitCode de 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="9fc11-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="9fc11-179">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9fc11-179">EXAMPLES</span></span>

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
