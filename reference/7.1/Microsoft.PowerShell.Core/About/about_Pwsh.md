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
# <a name="about-pwsh"></a>À propos de pwsh

## <a name="short-description"></a>Description courte
Explique comment utiliser l' `pwsh` interface de ligne de commande. Affiche les paramètres de ligne de commande et décrit la syntaxe.

## <a name="long-description"></a>Description longue

## <a name="syntax"></a>Syntaxe

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

## <a name="parameters"></a>Paramètres

Tous les paramètres ne respectent pas la casse.

### <a name="-file---f"></a>-File | -f

Si la valeur de `File` est `-` , le texte de la commande est lu à partir de l’entrée standard.
L’exécution `pwsh -File -` sans une entrée standard redirigée démarre une session normale. Cela revient à ne pas spécifier le `File` paramètre du tout.

Il s’agit du paramètre par défaut si aucun paramètre n’est présent, mais que des valeurs sont présentes dans la ligne de commande. Le script spécifié s’exécute dans l’étendue locale (« point-source »), afin que les fonctions et variables créées par le script soient disponibles dans la session active. Entrez le chemin d’accès au fichier de script et les paramètres éventuels. Le fichier doit être le dernier paramètre de la commande, car tous les caractères tapés après le nom du paramètre de fichier sont interprétés comme étant le chemin du fichier de script suivi des paramètres du script.

En règle générale, les paramètres de commutateur d’un script sont inclus ou omis.
Par exemple, la commande suivante utilise le paramètre All de l' Get-Script.ps1 fichier de script : `-File .\Get-Script.ps1 -All`

Dans de rares cas, vous devrez peut-être fournir une valeur **booléenne** pour un paramètre de commutateur. Pour fournir une valeur **booléenne** pour un paramètre de commutateur dans la valeur du paramètre **file** , utilisez le paramètre normalement suivi immédiatement par un signe deux-points et la valeur booléenne, comme suit : `-File .\Get-Script.ps1 -All:$False` .

Les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel). Par exemple, si vous êtes dans `cmd.exe` et que vous souhaitez passer une valeur de variable d’environnement, vous devez utiliser la `cmd.exe` syntaxe suivante : `pwsh -File .\test.ps1 -TestParam %windir%`

En revanche, `pwsh -File .\test.ps1 -TestParam $env:windir` l’exécution de dans `cmd.exe` entraîne la réception par le script de la chaîne littérale `$env:windir` , car elle n’a aucune signification particulière pour l’interpréteur de commandes actuel `cmd.exe` . Le `$env:windir` style de référence de variable d’environnement _peut_ être utilisé dans un paramètre de **commande** , car il est interprété comme du code PowerShell.

De même, si vous souhaitez exécuter la même commande à partir d’un _script de commandes_, vous devez utiliser à la `%~dp0` place de `.\` ou `$PSScriptRoot` pour représenter le répertoire d’exécution actuel : `pwsh -File %~dp0test.ps1 -TestParam %windir%` . Si vous l’utilisez à la place `.\test.ps1` , PowerShell lèvera une erreur, car il ne peut pas trouver le chemin d’accès littéral `.\test.ps1`

Lorsque le fichier de script se termine par une `exit` commande, le code de sortie du processus est défini sur l’argument numérique utilisé avec la `exit` commande. Avec un arrêt normal, le code de sortie est toujours `0` .

Semblable à `-Command` , quand une erreur de fin de script se produit, le code de sortie est défini sur `1` . Toutefois, contrairement à `-Command` , lorsque l’exécution est interrompue avec <kbd>CTRL</kbd> - <kbd>C</kbd> , le code de sortie est `0` .

### <a name="-command---c"></a>-Commande | -c

Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell, puis se ferme, sauf si le `NoExit` paramètre est spécifié.

La valeur de **Command** peut être `-` , un bloc de script ou une chaîne. Si la valeur de **Command** est `-` , le texte de la commande est lu à partir de l’entrée standard.

Le paramètre de **commande** n’accepte qu’un bloc de script pour l’exécution lorsqu’il peut reconnaître la valeur passée à la **commande** en tant que type **scriptblock** . Cela est possible _uniquement_ lors de l’exécution `pwsh` à partir d’un autre hôte PowerShell. Le type **scriptblock** peut être contenu dans une variable existante, retournée à partir d’une expression, ou analysé par l’hôte PowerShell sous la forme d’un bloc de script littéral placé entre accolades ( `{}` ), avant d’être passé à `pwsh` .

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

Dans `cmd.exe` , il n’existe aucun bloc de script (ou type **scriptblock** ), donc la valeur transmise à la **commande** sera _toujours_ une chaîne. Si vous écrivez un bloc de script dans la chaîne, il se comportera exactement comme s’il avait été tapé dans une invite PowerShell classique, affichant le contenu du bloc de script au lieu de s’exécuter.

Une chaîne transmise à la **commande** est toujours exécutée comme code PowerShell, donc les accolades de bloc de script ne sont souvent pas requises dans le premier emplacement lors de l’exécution à partir de `cmd.exe` . Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, il est possible d’utiliser [l’opérateur d’appel](about_operators.md#special-operators) `&` :

```
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

### <a name="-configurationname---config"></a>-ConfigurationName | -config

Spécifie un point de terminaison de configuration dans lequel PowerShell est exécuté. Il peut s’agir de n’importe quel point de terminaison enregistré sur l’ordinateur local, y compris les points de terminaison de communication à distance PowerShell par défaut ou un point de terminaison personnalisé avec des fonctionnalités de rôle d’utilisateur spécifiques.

Exemple : `pwsh -ConfigurationName AdminRoles`

### <a name="-custompipename"></a>-CustomPipeName

Spécifie le nom à utiliser pour un serveur IPC supplémentaire (canal nommé) utilisé pour le débogage et d’autres communications inter-processus. Cela offre un mécanisme prévisible pour la connexion à d’autres instances de PowerShell. Généralement utilisé avec le paramètre **CustomPipeName** sur `Enter-PSHostProcess` .

Ce paramètre a été introduit dans PowerShell 6,2.

Par exemple :

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a>-EncodedCommand | -e | -EC

Accepte une version de chaîne encodée en base64 d’une commande. Utilisez ce paramètre pour envoyer des commandes à PowerShell qui nécessitent un guillemet imbriqué complexe. La représentation base64 doit être une chaîne encodée en UTF-16LE.

Par exemple :

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a>-ExecutionPolicy | -ex | -EP

Définit la stratégie d’exécution par défaut pour la session active et l’enregistre dans la `$env:PSExecutionPolicyPreference` variable d’environnement. Ce paramètre ne modifie pas les stratégies d’exécution configurées de manière permanente.

Ce paramètre s’applique uniquement aux ordinateurs Windows. La `$env:PSExecutionPolicyPreference` variable d’environnement n’existe pas sur les plateformes non-Windows.

### <a name="-inputformat---inp---if"></a>-InputFormat | -INP | -Si

Décrit le format des données envoyées à PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

### <a name="-interactive---i"></a>-Interactif | -i

Présenter une invite interactive à l’utilisateur. Inverse pour le paramètre non interactif.

### <a name="-login---l"></a>-Connexion | -l

Sur Linux et macOS, démarre PowerShell comme un shell de connexion, en utilisant/bin/sh pour exécuter des profils de connexion tels que/etc/profile et ~/.Profile.
Sur Windows, ce commutateur ne fait rien.

> [!IMPORTANT]
> Ce paramètre doit être en premier pour démarrer PowerShell en tant qu’interpréteur de commandes.
> La transmission de ce paramètre à une autre position sera ignorée.

Pour configurer `pwsh` en tant que Shell de connexion sur les systèmes d’exploitation de type UNIX :

- Vérifiez que le chemin d’accès absolu complet à `pwsh` est indiqué sous `/etc/shells`
  - Ce chemin d’accès est généralement similaire `/usr/bin/pwsh` sur Linux ou `/usr/local/bin/pwsh` MacOS
  - Avec certaines méthodes d’installation, cette entrée sera ajoutée automatiquement au moment de l’installation
  - Si `pwsh` n’est pas présent dans `/etc/shells` , utilisez un éditeur pour ajouter le chemin d’accès à `pwsh` la dernière ligne. Cela nécessite des privilèges élevés pour la modification.
- Utilisez l’utilitaire [CHSH](https://linux.die.net/man/1/chsh) pour définir le shell de l’utilisateur actuel sur `pwsh` :

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> La définition de `pwsh` l’environnement de connexion n’est pas prise en charge actuellement sur le sous-système Windows pour Linux (WSL) et la tentative de définition `pwsh` en tant que Shell de connexion peut entraîner l’impossibilité de démarrer WSL de manière interactive.

### <a name="-mta"></a>-MTA

Démarrez PowerShell à l’aide d’un cloisonnement multithread. Ce commutateur est disponible uniquement sur Windows.

### <a name="-noexit---noe"></a>-NoExit | -noe

Ne quitte pas après l’exécution de commandes de démarrage.

Exemple : `pwsh -NoExit -Command Get-Date`

### <a name="-nologo---nol"></a>-Nologo | -nol

Masque la bannière de Copyright au démarrage de sessions interactives.

### <a name="-noninteractive---noni"></a>-Non interactif | -noni

Ne présente pas d’invite interactive à l’utilisateur. Toute tentative d’utiliser des fonctionnalités interactives, telles que `Read-Host` ou des invites de confirmation, entraîne des erreurs de fin d’instruction.

### <a name="-noprofile---nop"></a>-Noprofile | -NOP

Ne charge pas les profils PowerShell.

### <a name="-outputformat---o---of"></a>-OutputFormat | -o | -de

Détermine la mise en forme de la sortie de PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

Exemple : `pwsh -o XML -c Get-Date`

Quand elle est appelée avec une session PowerShell, vous pouvez obtenir des objets désérialisés en tant que chaînes de sortie plutôt que des chaînes brutes. En cas d’appel à partir d’autres shells, la sortie est une chaîne de données mise en forme en tant que texte CLIXML.

### <a name="-settingsfile---settings"></a>-SettingsFile | -paramètres

Remplace le `powershell.config.json` fichier de paramètres à l’ensemble du système pour la session. Par défaut, les paramètres à l’ensemble du système sont lus à partir du `powershell.config.json` dans le `$PSHOME` répertoire.

Notez que ces paramètres ne sont pas utilisés par le point de terminaison spécifié par l' `-ConfigurationName` argument.

Exemple : `pwsh -SettingsFile c:\myproject\powershell.config.json`

### <a name="-sshservermode---sshs"></a>-SSHServerMode | -sshs

Utilisé dans sshd_config pour l’exécution de PowerShell en tant que sous-système SSH. Elle n’est pas prévue ou prise en charge pour toute autre utilisation.

### <a name="-sta"></a>-STA

Démarrez PowerShell à l’aide d’un cloisonnement à thread unique. Il s’agit de la valeur par défaut. Ce commutateur est disponible uniquement sur Windows.

### <a name="-version---v"></a>-Version | -v

Affiche la version de PowerShell. Les paramètres supplémentaires sont ignorés.

### <a name="-windowstyle---w"></a>-WindowStyle | -w

Définit le style de fenêtre pour la session. Les valeurs valides sont Normal, Hidden, Minimized et Maximized.

### <a name="-workingdirectory---wd"></a>-WorkingDirectory | -WD

Définit le répertoire de travail initial en exécutant au démarrage. Tout chemin d’accès de fichier PowerShell valide est pris en charge.

Pour démarrer PowerShell dans votre répertoire de départ, utilisez : `pwsh -WorkingDirectory ~`

### <a name="-help---"></a>-Help, -?, /?

Affiche l’aide pour `pwsh` . Si vous tapez une commande pwsh dans PowerShell, faites précéder les paramètres de commande d’un trait d’Union ( `-` ), et non d’une barre oblique ( `/` ).
