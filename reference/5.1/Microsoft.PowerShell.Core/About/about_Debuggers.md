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
# <a name="about-debuggers"></a>À propos des débogueurs

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit le débogueur PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le débogage est le processus qui consiste à examiner un script pendant qu’il est en cours d’exécution pour identifier et corriger les erreurs dans les instructions de script. Le débogueur PowerShell peut vous aider à examiner et à identifier les erreurs et les inefficacités dans vos scripts, fonctions, commandes, workflows PowerShell, configurations DSC (Desired State Configuration) PowerShell ou expressions.

À compter de PowerShell 5,0, le débogueur PowerShell a été mis à jour pour déboguer les scripts, les fonctions, les flux de travail, les commandes, les configurations ou les expressions qui s’exécutent dans la console ou Windows PowerShell ISE sur des ordinateurs distants. Vous pouvez exécuter `Enter-PSSession` pour démarrer une session PowerShell à distance interactive dans laquelle vous pouvez définir des points d’arrêt et déboguer des fichiers de script et des commandes sur l’ordinateur distant. `Enter-PSSession` la fonctionnalité a été mise à jour pour vous permettre de vous reconnecter à et d’entrer dans une session déconnectée qui exécute un script ou une commande sur un ordinateur distant. Si le script en cours d’exécution atteint un point d’arrêt, votre session cliente démarre automatiquement le débogueur. Si la session déconnectée qui exécute un script a déjà atteint un point d’arrêt et qu’elle est arrêtée au point d’arrêt, `Enter-PSSession` démarre automatiquement le débogueur de ligne de commande après la reconnexion à la session.

Le débogueur PowerShell peut également être utilisé pour déboguer des flux de travail PowerShell, soit dans la console PowerShell, soit dans Windows PowerShell ISE. À compter de PowerShell 5,0, vous pouvez effectuer un débogage dans des travaux ou processus en cours d’exécution, localement ou à distance.

Vous pouvez utiliser les fonctionnalités du débogueur PowerShell pour examiner un script, une fonction, une commande, un flux de travail ou une expression PowerShell pendant son exécution. Le débogueur PowerShell comprend un ensemble d’applets de commande qui vous permettent de définir des points d’arrêt, de gérer des points d’arrêt et d’afficher la pile des appels.

## <a name="debugger-cmdlets"></a>Applets de commande du débogueur

Le débogueur PowerShell comprend l’ensemble d’applets de commande suivant :

- `Set-PSBreakpoint`: Définit les points d’arrêt sur les lignes, les variables et les commandes.
- `Get-PSBreakpoint`: Obtient les points d’arrêt de la session active.
- `Disable-PSBreakpoint`: Désactive les points d’arrêt dans la session active.
- `Enable-PSBreakpoint`: Réactive les points d’arrêt dans la session active.
- `Remove-PSBreakpoint`: Supprime les points d’arrêt de la session active.
- `Get-PSCallStack`: Affiche la pile des appels actuelle.

## <a name="starting-and-stopping-the-debugger"></a>Démarrage et arrêt du débogueur

Pour démarrer le débogueur, définissez un ou plusieurs points d’arrêt. Ensuite, exécutez le script, la commande ou la fonction que vous souhaitez déboguer.

Quand vous atteignez un point d’arrêt, l’exécution s’arrête et le contrôle est réactivé sur le débogueur.

Pour arrêter le débogueur, exécutez le script, la commande ou la fonction jusqu’à ce qu’elle soit terminée. Ou, tapez `stop` ou `t` .

### <a name="debugger-commands"></a>Commandes du débogueur

Lorsque vous utilisez le débogueur dans la console PowerShell, utilisez les commandes suivantes pour contrôler l’exécution. Dans Windows PowerShell ISE, utilisez les commandes du menu Déboguer.

Remarque : pour plus d’informations sur l’utilisation du débogueur dans d’autres applications hôtes, consultez la documentation de l’application hôte.

- `s`, `StepInto` : Exécute l’instruction suivante, puis s’arrête.

- `v`, `StepOver` : Exécute l’instruction suivante, mais ignore les fonctions et les appels. Les instructions ignorées sont exécutées, mais sans pas à pas.

- `Ctrl+Break`: (Arrêter tout dans ISE) s’arrête dans un script en cours d’exécution dans la console PowerShell ou Windows PowerShell ISE. Notez que la <kbd>touche Ctrl</kbd> + <kbd>Break</kbd> dans Windows PowerShell 2,0, 3,0 et 4,0 ferme le programme. L’instruction Break All fonctionne sur les scripts locaux et distants, en cours d’exécution de manière interactive.

- `o`, `StepOut` : Pas à pas sortant de la fonction active ; un niveau vers le haut en cas d’imbrication. S’il se trouve dans le corps principal, il continue jusqu’à la fin ou jusqu’au point d’arrêt suivant. Les instructions ignorées sont exécutées, mais sans pas à pas.

- `c`, `Continue` : Continue à s’exécuter jusqu’à ce que le script soit terminé ou jusqu’à ce que le point d’arrêt suivant soit atteint. Les instructions ignorées sont exécutées, mais sans pas à pas.

- `l`, `List` : Affiche la partie du script en cours d’exécution. Par défaut, il affiche la ligne active, cinq lignes précédentes et 10 lignes suivantes.
  Pour continuer à répertorier le script, appuyez sur entrée.

- `l <m>`, `List` : Affiche 16 lignes du script en commençant par le numéro de ligne spécifié par `<m>` .

- `l <m> <n>`, `List` : Affiche les `<n>` lignes du script, en commençant par le numéro de ligne spécifié par `<m>` .

- `q`, `Stop` , `Exit` : Arrête l’exécution du script et quitte le débogueur. Si vous déboguez un travail en exécutant l' `Debug-Job` applet de commande, la `Exit` commande détache le débogueur et autorise la poursuite de l’exécution du travail.

- `k`, `Get-PsCallStack` : Affiche la pile des appels actuelle.

- `<Enter>`: Répète la dernière commande s’il s’agissait d’une ou plusieurs étapes, d’un décalage de passe (v) ou d’une liste (l). Sinon, représente une action d’envoi.

- `?`, `h` : Affiche l’aide de la commande du débogueur.

Pour quitter le débogueur, vous pouvez utiliser stop (q).

À compter de PowerShell 5,0, vous pouvez exécuter la commande exit pour quitter une session de débogage imbriquée que vous avez démarrée en exécutant `Debug-Job` ou `Debug-Runspace` .

À l’aide de ces commandes du débogueur, vous pouvez exécuter un script, l’arrêter à un point de préoccupation, examiner les valeurs des variables et l’état du système, et continuer à exécuter le script jusqu’à ce que vous ayez identifié un problème.

Remarque : Si vous exécutez pas à pas une instruction avec un opérateur de redirection, tel que « > », le débogueur PowerShell parcourt toutes les instructions restantes dans le script.

Affichage des valeurs des variables de script

Lorsque vous êtes dans le débogueur, vous pouvez également entrer des commandes, afficher la valeur des variables, utiliser des applets de commande et exécuter des scripts sur la ligne de commande.

Vous pouvez afficher la valeur actuelle de toutes les variables dans le script en cours de débogage, à l’exception des variables automatiques suivantes :

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

Si vous essayez d’afficher la valeur d’une de ces variables, vous l’obtenez pour un pipeline interne que le débogueur utilise, pas la valeur de la variable dans le script.

Pour afficher la valeur de ces variables pour le script en cours de débogage, dans le script, affectez la valeur de la variable automatique à une nouvelle variable. Vous pouvez ensuite afficher la valeur de la nouvelle variable.

Par exemple,

```powershell
$scriptArgs = $Args
$scriptArgs
```

Dans l’exemple de cette rubrique, la valeur de la `$MyInvocation` variable est réassignée comme suit :

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a>Environnement du débogueur

Quand vous atteignez un point d’arrêt, vous entrez l’environnement du débogueur. L’invite de commandes change de sorte qu’elle commence par « [DBG] : ». Si vous déboguez un flux de travail, l’invite est « [WFDBG] ». Vous pouvez personnaliser l’invite de commandes.

Pour plus d’informations sur la personnalisation de l’invite, consultez [about_Prompts](about_prompts.md).

En outre, dans certaines applications hôtes, telles que la console PowerShell (mais pas dans Environnement d’écriture de scripts intégré de Windows PowerShell [ISE]), une invite imbriquée s’ouvre pour le débogage. Vous pouvez détecter l’invite imbriquée par les caractères supérieurs à répétitifs (ASCII 62) qui s’affichent à l’invite de commandes.

Par exemple, voici l’invite de débogage par défaut dans la console PowerShell :

```
[DBG]: PS (get-location)>>>
```

Vous pouvez rechercher le niveau d’imbrication à l’aide de la `$NestedPromptLevel` variable automatique.

En outre, une variable automatique, `$PSDebugContext` , est définie dans l’étendue locale. Vous pouvez utiliser la présence de la `$PsDebugContext` variable pour déterminer si vous êtes dans le débogueur.

Par exemple :

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

Vous pouvez utiliser la valeur de la `$PSDebugContext` variable dans votre débogage.

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a>Débogage et portée

L’arrêt dans le débogueur ne modifie pas l’étendue dans laquelle vous travaillez, mais quand vous atteignez un point d’arrêt dans un script, vous passez dans la portée du script. La portée du script est un enfant de l’étendue dans laquelle vous avez exécuté le débogueur.

Pour rechercher les variables et les alias définis dans la portée du script, utilisez le paramètre scope des `Get-Alias` applets de commande ou `Get-Variable` .

Par exemple, la commande suivante obtient les variables dans l’étendue locale (script) :

```powershell
Get-Variable -scope 0
```

Vous pouvez abréger la commande comme suit :

```powershell
gv -s 0
```

Il s’agit d’une méthode utile pour afficher uniquement les variables que vous avez définies dans le script et que vous avez définies pendant le débogage.

Débogage à partir de la ligne de commande

Quand vous définissez un point d’arrêt sur variable ou un point d’arrêt de commande, vous pouvez définir le point d’arrêt uniquement dans un fichier de script. Toutefois, par défaut, le point d’arrêt est défini sur tout ce qui s’exécute dans la session active.

Par exemple, si vous définissez un point d’arrêt sur la `$name` variable, le débogueur s’arrête sur toute `$name` variable d’un script, d’une commande, d’une fonction, d’une applet de commande de script ou d’une expression que vous exécutez jusqu’à ce que vous désactiviez ou supprimiez le point d’arrêt.

Cela vous permet de déboguer vos scripts dans un contexte plus réaliste dans lequel ils peuvent être affectés par des fonctions, des variables et d’autres scripts dans la session et dans le profil de l’utilisateur.

Les points d’arrêt de ligne étant spécifiques aux fichiers de script, ils sont définis uniquement dans les fichiers de script.

## <a name="debugging-workflows"></a>Débogage de workflows

Le débogueur PowerShell 4,0 peut être utilisé pour déboguer des flux de travail PowerShell, soit dans la console PowerShell, soit dans Windows PowerShell ISE. L’utilisation du débogueur PowerShell pour déboguer des flux de travail présente certaines limites.

- Vous pouvez afficher les variables de flux de travail lorsque vous êtes dans le débogueur, mais la définition de variables de workflow à partir du débogueur n’est pas prise en charge.
- La saisie semi-automatique via la touche Tab lorsqu’elle est arrêtée dans le débogueur de workflow n’est pas disponible.
- Le débogage de workflow fonctionne uniquement avec l’exécution synchrone de flux de travail à partir d’un script PowerShell. Vous ne pouvez pas déboguer des workflows s’ils s’exécutent en tant que travail (avec le paramètre **AsJob** ).
- D’autres scénarios de débogage imbriqués, tels qu’un workflow appelant un autre Workflow ou un workflow appelant un script, ne sont pas implémentés.

L’exemple suivant illustre le débogage d’un flux de travail. Quand le débogueur parcourt la fonction de flux de travail, l’invite du débogueur passe à « [WFDBG] ».

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

## <a name="debugging-functions"></a>Fonctions de débogage

Quand vous définissez un point d’arrêt sur une fonction qui a des `Begin` `Process` sections, et `End` , le débogueur s’arrête à la première ligne de chaque section.

Par exemple :

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

## <a name="debugging-remote-scripts"></a>Débogage de scripts distants

À compter de PowerShell 5,0, vous pouvez exécuter le débogueur PowerShell dans une session à distance, soit dans la console, soit Windows PowerShell ISE.
`Enter-PSSession` la fonctionnalité a été mise à jour pour vous permettre de vous reconnecter à et d’entrer dans une session déconnectée qui s’exécute sur un ordinateur distant, et d’exécuter un script. Si le script en cours d’exécution atteint un point d’arrêt, votre session cliente démarre automatiquement le débogueur.

Voici un exemple qui montre comment cela fonctionne, avec les points d’arrêt définis dans un script aux lignes 6, 11, 22 et 25. Notez que dans l’exemple, quand le débogueur démarre, il existe deux invites d’identification : le nom de l’ordinateur sur lequel la session s’exécute et l’invite DBG qui vous indique que vous êtes en mode de débogage.

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

## <a name="examples"></a>Exemples

Ce script de test détecte la version du système d’exploitation et affiche un message propre au système. Il comprend une fonction, un appel de fonction et une variable.

La commande suivante affiche le contenu du fichier de script de test :

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

Pour commencer, définissez un point d’arrêt à un point d’intérêt dans le script, tel qu’une ligne, une commande, une variable ou une fonction.

Commencez par créer un point d’arrêt de ligne sur la première ligne du Test.ps1 script dans le répertoire actif.

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

Vous pouvez abréger cette commande :

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

La commande retourne un objet de point d’arrêt de ligne ( **System. Management. Automation. LineBreakpoint** ).

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

À présent, démarrez le script.

```powershell
PS C:\ps-test> .\test.ps1
```

Lorsque le script atteint le premier point d’arrêt, le message de point d’arrêt indique que le débogueur est actif. Il décrit le point d’arrêt et affiche un aperçu de la première ligne du script, qui est une déclaration de fonction. L’invite de commandes change également pour indiquer que le débogueur a le contrôle.

La ligne d’aperçu comprend le nom du script et le numéro de ligne de la commande prévisualisée.

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

Utilisez la ou les commandes Step pour exécuter la première instruction dans le script et pour afficher un aperçu de l’instruction suivante. L’instruction suivante utilise la `$MyInvocation` variable Automatic pour définir la valeur de la `$scriptName` variable sur le chemin d’accès et le nom de fichier du fichier de script.

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

À ce stade, la `$scriptName` variable n’est pas remplie, mais vous pouvez vérifier la valeur de la variable en affichant sa valeur. Dans ce cas, la valeur est `$null`.

```powershell
DBG> $scriptname
# DBG>
```

Utilisez une ou plusieurs autres commandes d’étape pour exécuter l’instruction en cours et pour afficher un aperçu de l’instruction suivante dans le script. L’instruction suivante appelle la fonction PsVersion.

```powershell
DBG> s
test.ps1:12  psversion
```

À ce stade, la `$scriptName` variable est remplie, mais vous vérifiez la valeur de la variable en affichant sa valeur. Dans ce cas, la valeur est définie sur le chemin d’accès du script.

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

Utilisez une autre commande Step pour exécuter l’appel de fonction. Appuyez sur entrée ou tapez « s » pour l’étape.

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

Le message de débogage comprend un aperçu de l’instruction dans la fonction. Pour exécuter cette instruction et pour afficher un aperçu de l’instruction suivante dans la fonction, vous pouvez utiliser une `Step` commande. Toutefois, dans ce cas, utilisez une commande StepOut, (o). Elle termine l’exécution de la fonction (sauf si elle atteint un point d’arrêt) et passe à l’instruction suivante dans le script.

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

Étant donné que nous sommes dans la dernière instruction du script, les commandes Step, StepOut, et continue ont le même effet. Dans ce cas, utilisez StepOut, (o).

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

La commande StepOut, exécute la dernière commande. L’invite de commandes standard indique que le débogueur s’est arrêté et a retourné le contrôle au processeur de commandes.

À présent, réexécutez le débogueur. Tout d’abord, pour supprimer le point d’arrêt actuel, utilisez les `Get-PsBreakpoint` applets de commande et `Remove-PsBreakpoint` . (Si vous pensez que vous pouvez réutiliser le point d’arrêt, utilisez l' `Disable-PsBreakpoint` applet de commande au lieu de `Remove-PsBreakpoint` .)

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

Vous pouvez abréger cette commande :

```powershell
PS C:\ps-test> gbp | rbp
```

Ou exécutez la commande en écrivant une fonction, telle que la fonction suivante :

```powershell
function delbr { gbp | rbp }
```

À présent, créez un point d’arrêt sur la `$scriptname` variable.

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

Vous pouvez abréger la commande comme suit :

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

À présent, démarrez le script. Le script atteint le point d’arrêt de la variable. Le mode par défaut est Write, ce qui signifie que l’exécution s’arrête juste avant l’instruction qui modifie la valeur de la variable.

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

Affichez la valeur actuelle de la `$scriptName` variable, qui est `$null` .

```powershell
DBG> $scriptName
# DBG>
```

Utilisez une ou plusieurs commandes d’étape pour exécuter l’instruction qui remplit la variable.
Ensuite, affichez la nouvelle valeur de la `$scriptName` variable.

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

L’instruction suivante est un appel à la fonction PsVersion. Pour ignorer la fonction tout en l’exécutant, utilisez une commande de décalage automatique (v). Si vous êtes déjà dans la fonction lorsque vous utilisez le décalage de passe, il n’est pas effectif. L’appel de fonction est affiché, mais il n’est pas exécuté.

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

La commande de décalage automatique exécute la fonction et affiche l’instruction suivante dans le script, qui imprime la dernière ligne.

Utilisez une commande Stop (t) pour quitter le débogueur. L’invite de commandes revient à l’invite de commandes standard.

```powershell
C:\ps-test>
```

Pour supprimer les points d’arrêt, utilisez les `Get-PsBreakpoint` applets de commande et `Remove-PsBreakpoint` .

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

Créez un point d’arrêt de commande sur la fonction PsVersion.

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

Vous pouvez abréger cette commande pour :

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

À présent, exécutez le script.

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

Le script atteint le point d’arrêt au niveau de l’appel de fonction. À ce stade, la fonction n’a pas encore été appelée. Cela vous donne la possibilité d’utiliser le paramètre action de `Set-PSBreakpoint` pour définir des conditions pour l’exécution du point d’arrêt ou pour effectuer des tâches préparatoires ou de diagnostic, telles que le démarrage d’un journal ou l’appel d’un diagnostic ou d’un script de sécurité.

Pour définir une action, utilisez une commande continue (c) pour quitter le script et une `Remove-PsBreakpoint` commande pour supprimer le point d’arrêt actuel. (Les points d’arrêt sont en lecture seule, vous ne pouvez donc pas ajouter une action au point d’arrêt actuel.)

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

À présent, créez un point d’arrêt de commande avec une action. La commande suivante définit un point d’arrêt de commande avec une action qui journalise la valeur de la `$scriptName` variable lorsque la fonction est appelée. Étant donné que le mot clé Break n’est pas utilisé dans l’action, l’exécution ne s’arrête pas. (L’accent grave (') est le caractère de continuation de ligne.)

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

Vous pouvez également ajouter des actions qui définissent des conditions pour le point d’arrêt. Dans la commande suivante, le point d’arrêt de commande est exécuté uniquement si la stratégie d’exécution est définie sur RemoteSigned, la stratégie la plus restrictive qui vous permet toujours d’exécuter des scripts. (L’accent grave (') est le caractère de continuation.)

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

Le mot clé Break dans l’action indique au débogueur d’exécuter le point d’arrêt.
Vous pouvez également utiliser le mot clé continue pour demander au débogueur de s’exécuter sans interruption. Étant donné que le mot clé Default est continue, vous devez spécifier Break pour arrêter l’exécution.

À présent, exécutez le script.

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

Étant donné que la stratégie d’exécution est définie sur **RemoteSigned** , l’exécution s’arrête au niveau de l’appel de fonction.

À ce stade, vous souhaiterez peut-être vérifier la pile des appels. Utilisez l' `Get-PsCallStack` applet de commande ou la `Get-PsCallStack` commande du débogueur (k). La commande suivante obtient la pile des appels actuelle.

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

Cet exemple montre quelques-unes des nombreuses façons d’utiliser le débogueur PowerShell.

Pour plus d’informations sur les applets de commande du débogueur, tapez la commande suivante :

```powershell
help <cmdlet-name> -full
```

Par exemple, entrez :

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a>Autres fonctionnalités de débogage dans PowerShell

En plus du débogueur PowerShell, PowerShell comprend plusieurs autres fonctionnalités que vous pouvez utiliser pour déboguer des scripts et des fonctions.

- Windows PowerShell ISE comprend un débogueur graphique interactif. Pour plus d’informations, démarrez Windows PowerShell ISE et appuyez sur F1.

- L' `Set-PSDebug` applet de commande offre des fonctionnalités de débogage de script très basiques, y compris l’exécution pas à pas et le suivi.

- Utilisez l' `Set-StrictMode` applet de commande pour détecter les références à des variables non initialisées, aux références à des propriétés inexistantes d’un objet et à une syntaxe de fonction non valide.

- Ajoutez des instructions de diagnostic à un script, telles que des instructions qui affichent la valeur des variables, des instructions qui lisent l’entrée à partir de la ligne de commande ou des instructions qui signalent l’instruction en cours. Utilisez les applets de commande qui contiennent le verbe Write pour cette tâche, telles que `Write-Host` ,, `Write-Debug` `Write-Warning` et `Write-Verbose` .

## <a name="see-also"></a>VOIR AUSSI

- [Disable-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [Enable-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [Get-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [Get-PSCallStack](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [Remove-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [Set-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
