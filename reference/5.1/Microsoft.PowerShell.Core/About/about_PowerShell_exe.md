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
# <a name="about-powershellexe"></a>À propos de PowerShell.exe

## <a name="short-description"></a>Description courte
Explique comment utiliser l' `powershell.exe` interface de ligne de commande. Affiche les paramètres de ligne de commande et décrit la syntaxe.

## <a name="long-description"></a>Description longue

### <a name="syntax"></a>SYNTAX

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

### <a name="parameters"></a>Paramètres

#### <a name="-psconsolefile-filepath"></a>-PSConsoleFile \<FilePath\>

Charge le fichier de console PowerShell spécifié. Entrez le chemin d’accès et le nom du fichier de console. Pour créer un fichier de console, utilisez l’applet de commande Export-Console dans PowerShell.

#### <a name="-version-powershell-version"></a>-Version \<PowerShell Version\>

Démarre la version spécifiée de PowerShell. Les valeurs valides sont 2,0 et 3,0. La version que vous spécifiez doit être installée sur le système. Si Windows PowerShell 3,0 est installé sur l’ordinateur, « 3,0 » est la version par défaut.
Dans le cas contraire, « 2,0 » est la version par défaut. Pour plus d’informations, consultez [installation de PowerShell](/powershell/scripting/install/installing-windows-powershell).

#### <a name="-nologo"></a>-Nologo

Masque la bannière de copyright au démarrage.

#### <a name="-noexit"></a>-NoExit

Ne quitte pas après l’exécution de commandes de démarrage.

#### <a name="-sta"></a>-Sta

Démarre PowerShell à l’aide d’un cloisonnement monothread. Dans Windows PowerShell 2.0, le cloisonnement par défaut est multithread (MTA). Dans Windows PowerShell 3.0, le cloisonnement par défaut est monothread (STA).

#### <a name="-mta"></a>-Mta

Démarre PowerShell à l’aide d’un cloisonnement multithread. Ce paramètre est introduit dans PowerShell 3.0. Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA). Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA).

#### <a name="-noprofile"></a>-NoProfile

Ne charge pas le profil PowerShell.

#### <a name="-noninteractive"></a>-NonInteractive

Ne présente pas d’invite interactive à l’utilisateur.

#### <a name="-inputformat-text--xml"></a>-InputFormat {Text | XML}

Décrit le format des données envoyées à PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

#### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Détermine la mise en forme de la sortie de PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

#### <a name="-windowstyle-window-style"></a>-WindowStyle \<Window style\>

Définit le style de fenêtre pour la session. Les valeurs valides sont Normal, Hidden, Minimized et Maximized.

#### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand \<Base64EncodedCommand\>

Accepte une version de chaîne codée en base 64 d’une commande. Utilisez ce paramètre pour envoyer à PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes. La chaîne doit être mise en forme à l’aide de l’encodage de caractères UTF-16LE.

#### <a name="-configurationname-string"></a>-ConfigurationName \<string\>

Spécifie un point de terminaison de configuration dans lequel PowerShell est exécuté. Il peut s’agir de n’importe quel point de terminaison enregistré sur l’ordinateur local, y compris les points de terminaison de communication à distance PowerShell par défaut ou un point de terminaison personnalisé avec des fonctionnalités de rôle d’utilisateur spécifiques.

#### <a name="-file----filepath-args"></a>-Fichier-| \<filePath\>\<args\>

Si la valeur du **fichier** est « - », le texte de la commande est lu à partir de l’entrée standard.
L’exécution `powershell -File -` sans une entrée standard redirigée démarre une session normale. Cela revient au même que de ne pas spécifier le paramètre **file** .

Si la valeur de **fichier** est un chemin d’accès de fichier, le script s’exécute dans l’étendue locale (« point-source »), afin que les fonctions et variables créées par le script soient disponibles dans la session active. Entrez le chemin d’accès au fichier de script et les paramètres éventuels. **File** doit être le dernier paramètre dans la commande. Toutes les valeurs tapées après le paramètre **file** sont interprétées comme le chemin d’accès au fichier de script et les paramètres passés à ce script.

Les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel). Par exemple, si vous êtes en **cmd.exe** et que vous souhaitez passer une valeur de variable d’environnement, vous devez utiliser la syntaxe **cmd.exe** : `powershell.exe -File .\test.ps1 -TestParam %windir%`

En revanche, s’exécutant `powershell.exe -File .\test.ps1 -TestParam $env:windir` dans **cmd.exe** , le script reçoit la chaîne littérale `$env:windir` , car il n’a aucune signification particulière pour l’interpréteur de commandes **cmd.exe** actuel. Le `$env:windir` style de référence de variable d’environnement _peut_ être utilisé dans un paramètre de **commande** , dans la mesure où il sera interprété comme du code PowerShell.

De même, si vous souhaitez exécuter la même commande à partir d’un **script de commandes** , vous devez utiliser à la `%~dp0` place de `.\` ou `$PSScriptRoot` pour représenter le répertoire d’exécution actuel : `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` .
Si vous l’utilisez à la place `.\test.ps1` , PowerShell lèvera une erreur, car il ne peut pas trouver le chemin d’accès littéral `.\test.ps1`

Lorsque la valeur du **fichier** est un chemin d’accès de fichier, le **fichier** _doit_ être le dernier paramètre de la commande, car tous les caractères tapés après le nom du paramètre de **fichier** sont interprétés comme étant le chemin d’accès du fichier de script suivi des paramètres du script.

Vous pouvez inclure les paramètres de script et les valeurs dans la valeur du paramètre **file** . Par exemple : `-File .\Get-Script.ps1 -Domain Central`

En règle générale, les paramètres de commutateur d’un script sont inclus ou omis.
Par exemple, la commande suivante utilise le paramètre **All** du `Get-Script.ps1` fichier de script : `-File .\Get-Script.ps1 -All`

Dans de rares cas, vous devrez peut-être fournir une valeur **booléenne** pour un paramètre.
Il n’est pas possible de passer une valeur booléenne explicite pour un paramètre de commutateur lors de l’exécution d’un script de cette manière. Cette limitation a été supprimée dans PowerShell 6 ( `pwsh.exe` ).

#### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy \<ExecutionPolicy\>

Définit la stratégie d’exécution par défaut pour la session active et l’enregistre dans la `$env:PSExecutionPolicyPreference` variable d’environnement. Ce paramètre ne modifie pas la stratégie d’exécution PowerShell qui est définie dans le Registre. Pour plus d’informations sur les stratégies d’exécution PowerShell, notamment une liste de valeurs valides, consultez [about_Execution_Policies](about_Execution_Policies.md).

#### <a name="-command"></a>-Command

Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell, puis se ferme, sauf si le `NoExit` paramètre est spécifié.

La valeur de **Command** peut être `-` , un bloc de script ou une chaîne. Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard.

Le paramètre de **commande** n’accepte qu’un bloc de script pour l’exécution lorsqu’il peut reconnaître la valeur passée à la **commande** en tant que type **scriptblock** . Cela est possible _uniquement_ lors de l’exécution `powershell.exe` à partir d’un autre hôte PowerShell. Le type **scriptblock** peut être contenu dans une variable existante, retournée à partir d’une expression, ou analysé par l’hôte PowerShell sous la forme d’un bloc de script littéral placé entre accolades ( `{}` ), avant d’être passé à `powershell.exe` .

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

Dans `cmd.exe` , il n’existe aucun bloc de script (ou type **scriptblock** ), donc la valeur transmise à la **commande** sera _toujours_ une chaîne. Si vous écrivez un bloc de script dans la chaîne, il se comportera exactement comme s’il avait été tapé dans une invite PowerShell classique, affichant le contenu du bloc de script au lieu de s’exécuter.

Une chaîne transmise à la **commande** est toujours exécutée comme code PowerShell, donc les accolades de bloc de script ne sont souvent pas requises dans le premier emplacement lors de l’exécution à partir de `cmd.exe` . Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, il est possible d’utiliser [l’opérateur d’appel](about_operators.md#special-operators) `&` :

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

Si la valeur de **Command** est une chaîne, **Command** doit être le dernier paramètre de pwsh, car tous les arguments qui le suivent sont interprétés comme faisant partie de la commande à exécuter.

Quand elle est appelée à partir d’une session PowerShell existante, les résultats sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs. Pour les autres shells, les résultats sont retournés sous forme de chaînes.

Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard. Vous devez rediriger l’entrée standard lors de l’utilisation du paramètre de **commande** avec une entrée standard. Par exemple :

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

Cet exemple produit la sortie suivante :

```Output
in
hi there
out
```

Le code de sortie du processus est déterminé par l’état de la dernière commande (exécutée) dans le bloc de script. Le code de sortie est `0` lorsque `$?` est `$true` ou `1` lorsque `$?` est `$false` . Si la dernière commande est un programme externe ou un script PowerShell qui définit explicitement un code de sortie autre que `0` ou `1` , ce code de sortie est converti en `1` pour le code de sortie du processus. Pour conserver le code de sortie spécifique, ajoutez `exit $LASTEXITCODE` à votre chaîne de commande ou bloc de script.

De même, la valeur 1 est retournée quand une erreur de fin de script (arrêt d’exécution), telle que `throw` ou `-ErrorAction Stop` , se produit ou lorsque l’exécution est interrompue avec <kbd>CTRL</kbd> - <kbd>C</kbd>.

_uniquement_ possible lors de l’exécution de **PowerShell.exe** à partir d’un autre hôte PowerShell.
Le type **scriptblock** peut être contenu dans une variable existante, retournée à partir d’une expression, ou analysé par l’hôte PowerShell sous la forme d’un bloc de script littéral placé entre accolades `{}` , avant d’être passé à **PowerShell.exe** .

Dans **cmd.exe** , il n’existe pas de type de bloc de script (ou type **scriptblock** ), donc la valeur transmise à la **commande** sera _toujours_ une chaîne. Si vous écrivez un bloc de script dans la chaîne, il se comportera exactement comme s’il avait été tapé dans une invite PowerShell classique, affichant le contenu du bloc de script au lieu de s’exécuter.

Une chaîne transmise à la **commande** est toujours exécutée en tant que PowerShell. par conséquent, les accolades de bloc de script ne sont souvent pas requises dans le premier emplacement lors de l’exécution à partir de **cmd.exe** . Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, vous pouvez utiliser l' [opérateur d’appel](about_operators.md#special-operators) 
 `&` :

```console
"& {<command>}"
```

#### <a name="-help---"></a>-Help, -?, /?

Affiche l’aide pour **PowerShell.exe** . Si vous tapez une commande **PowerShell.exe** dans une session PowerShell, faites précéder les paramètres de commande d’un trait d’Union (-), et non d’une barre oblique (/). Vous pouvez utiliser un trait d’Union ou une barre oblique dans **cmd.exe** .

### <a name="remarks"></a>Remarques

Remarque sur la résolution des problèmes : dans PowerShell 2,0, le démarrage de certains programmes à partir de la console PowerShell échoue avec un **LastExitCode** de 0xc0000142.

### <a name="examples"></a>EXEMPLES

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
