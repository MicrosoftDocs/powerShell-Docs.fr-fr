---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Comment déboguer des scripts dans Windows PowerShell ISE
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086865"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Comment déboguer des scripts dans Windows PowerShell ISE

Cet article décrit comment déboguer des scripts sur un ordinateur local à l’aide des fonctionnalités de débogage visuel de l’environnement d’écriture de scripts intégré de Windows PowerShell (Windows PowerShell ISE).

## <a name="how-to-manage-breakpoints"></a>Comment gérer les points d’arrêt

Un point d’arrêt est un endroit désigné dans un script, où vous souhaitez que l’opération s’interrompe afin que de pouvoir examiner l’état actuel des variables et de l’environnement dans lequel votre script s’exécute. Une fois votre script interrompu par un point d’arrêt, vous pouvez exécuter des commandes dans le volet Console pour examiner l’état de votre script.  Vous pouvez extraire des variables ou exécuter d’autres commandes. Vous pouvez même modifier la valeur de toutes les variables visibles dans le contexte du script en cours d’exécution. Après avoir examiné ce que vous voulez voir, vous pouvez reprendre l’exécution du script.

Dans l’environnement de débogage de Windows PowerShell, vous pouvez définir trois types de points d’arrêt :

1. **Point d’arrêt de ligne**. L’exécution du script s’interrompt quand la ligne désignée est atteinte.

2. **Point d’arrêt de variable.** L’exécution du script s’interrompt chaque fois que la valeur de la variable désignée change.

3. **Point d’arrêt de commande.** L’exécution du script s’interrompt chaque fois que la commande désignée est sur le point d’être exécutée. Il est possible d’inclure des paramètres pour filtrer davantage le point d’arrêt uniquement pour l’opération souhaitée. La commande peut également être une fonction que vous créez.

Dans l’environnement de débogage de Windows PowerShell ISE, seuls des points d’arrêt de ligne peuvent être définis à l’aide du menu ou des raccourcis clavier. Les deux autres types de points d’arrêt doivent être définis à partir du volet Console à l’aide de l’applet de commande [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8). Cette section décrit comment effectuer des tâches de débogage dans Windows PowerShell ISE en utilisant les menus disponibles, et exécuter un éventail plus large de commandes à partir du volet Console à l’aide de scripts.

### <a name="to-set-a-breakpoint"></a>Pour définir un point d’arrêt

Un point d’arrêt ne peut être défini dans un script qu’après l’enregistrement de celui-ci. Cliquez avec le bouton droit sur la ligne dans laquelle vous souhaitez définir un point d’arrêt de ligne, puis cliquez sur **Basculer le point d’arrêt**. Vous pouvez également cliquer sur la ligne dans laquelle vous souhaitez définir un point d’arrêt de ligne, puis appuyer sur **F9** ou, dans le menu **Déboguer**, cliquer sur **Basculer le point d’arrêt**.

Le script suivant montre comment définir un point d’arrêt de variable à partir du volet Console en utilisant l’applet de commande [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420).

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Liste de tous les points d’arrêt

Affiche tous les points d’arrêt dans la session Windows PowerShell actuelle.

Dans le menu **Déboguer**, cliquez sur **Lister les points d’arrêt**. Le script suivant montre comment répertorier tous les points d’arrêt à partir du volet Console en utilisant l’applet de commande [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6).

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Supprimer un point d’arrêt

La suppression d’un point d’arrêt revient à effacer celui-ci.

Si vous pensez que vous pouvez être amené à le réutiliser ultérieurement, envisagez plutôt de [désactiver un point d’arrêt](#disable-a-breakpoint).
Cliquez avec le bouton droit sur la ligne dans laquelle vous souhaitez supprimer un point d’arrêt, puis cliquez sur **Basculer le point d’arrêt**.
Vous pouvez également cliquer sur la ligne dans laquelle vous souhaitez supprimer un point d’arrêt, puis, dans le menu **Déboguer**, cliquer sur **Basculer le point d’arrêt**.
Le script suivant montre comment supprimer un point d’arrêt avec un ID spécifié à partir du volet Console en utilisant l’applet de commande [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6).

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Supprimer tous les points d’arrêt

Pour supprimer tous les points d’arrêt définis dans la session active, dans le menu **Déboguer**, cliquez sur **Supprimer tous les points d’arrêt**.

Le script suivant montre comment supprimer tous les points d’arrêt à partir du volet Console en utilisant l’applet de commande [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6).

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Désactiver un point d’arrêt

La désactivation d’un point d’arrêt n’a pas pour effet de supprimer celui-ci, mais uniquement de le mettre hors service jusqu’à sa réactivation éventuelle.  Pour désactiver un point d’arrêt de ligne spécifique, cliquez avec le bouton droit sur la ligne dans laquelle vous souhaitez désactiver ce point d’arrêt, puis cliquez sur **Désactiver le point d’arrêt**. Vous pouvez également cliquer sur la ligne dans laquelle vous souhaitez désactiver un point d’arrêt, puis appuyer sur **F9** ou, dans le menu **Déboguer**, cliquer sur **Désactiver le point d’arrêt**. Le script suivant montre comment supprimer un point d’arrêt avec un ID spécifié à partir du volet Console en utilisant l’applet de commande [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8).

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Désactiver tous les points d’arrêt

La désactivation d’un point d’arrêt n’a pas pour effet de supprimer celui-ci, mais uniquement de le mettre hors service jusqu’à sa réactivation éventuelle.  Pour désactiver tous les points d’arrêt dans la session active, dans le menu **Déboguer**, cliquez sur **Désactiver tous les points d’arrêt**. Le script suivant montre comment désactiver tous les points d’arrêt à partir du volet Console en utilisant l’applet de commande [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8).

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Activer un point d’arrêt

Pour activer un point d’arrêt spécifique, cliquez avec le bouton droit sur la ligne dans laquelle vous souhaitez activer ce point d’arrêt, puis cliquez sur **Activer le point d’arrêt**. Vous pouvez également cliquer sur la ligne dans laquelle vous souhaitez activer un point d’arrêt, puis appuyer sur **F9** ou, dans le menu **Déboguer**, cliquer sur **Activer le point d’arrêt**. Le script suivant montre comment activer des points d’arrêt spécifiques à partir du volet Console en utilisant l’applet de commande [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0).

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Activer tous les points d’arrêt

Pour activer tous les points d’arrêt définis dans la session active, dans le menu **Déboguer**, cliquez sur **Activer tous les points d’arrêt**. Le script suivant montre comment activer tous les points d’arrêt à partir du volet Console en utilisant l’applet de commande [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0).

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Comment gérer une session de débogage

Avant de commencer le débogage, vous devez définir un ou plusieurs points d’arrêt. Vous ne pouvez définir un point d’arrêt que si le script que vous souhaitez déboguer est enregistré. Pour des instructions sur la définition d’un point d’arrêt, voir [Comment gérer les points d’arrêt](#how-to-manage-breakpoints) ou [Set-PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Une fois le débogage démarré, vous ne pouvez modifier un script qu’après avoir arrêté le débogage. Un script dans lequel un ou plusieurs points d’arrêt sont définis est automatiquement enregistré avant son exécution.

### <a name="to-start-debugging"></a>Pour commencer le débogage

Appuyez sur **F5** ou, dans la barre d’outils, cliquez sur l’icône **Exécuter le script**. Ou encore, dans le menu **Déboguer**, cliquez sur **Exécuter/Continuer**. Le script s’exécute jusqu’à ce qu’il rencontre le premier point d’arrêt. Il suspend alors l’opération et met en surbrillance la ligne sur laquelle il s’est arrêté.

### <a name="to-continue-debugging"></a>Pour continuer le débogage

Appuyez sur **F5** ou, dans la barre d’outils, cliquez sur l’icône **Exécuter le script**. Ou bien, dans le menu **Déboguer**, cliquez sur **Exécuter/Continuer**. Ou encore, dans le volet Console, tapez sur **C** puis appuyez sur **Entrée**. Le script poursuit alors son exécution jusqu’au point d’arrêt suivant ou jusqu’à la fin s’il ne rencontre plus d’autre point d’arrêt.

### <a name="to-view-the-call-stack"></a>Pour afficher la pile des appels

La pile des appels affiche l’emplacement d’exécution actuel dans le script. Si le script s’exécute dans une fonction appelée par une autre fonction, cela est indiqué dans l’affichage par des lignes supplémentaires dans la sortie. La ligne inférieure affiche le script d’origine et la ligne de celui-ci dans laquelle une fonction a été appelée. La ligne juste au-dessus affiche cette fonction et la ligne dans laquelle une autre fonction pourrait avoir été appelée.  La dernière supérieure affiche le contexte actuel de la ligne active sur laquelle le point d’arrêt est défini.

Pendant la suspension, pour afficher la pile des appels active, appuyez sur **Ctrl+Maj+D** ou, dans le menu **Déboguer**, cliquez sur **Afficher la pile des appels**. Ou encore, dans le volet Console, tapez **K**, puis appuyez sur **Entrée**.

### <a name="to-stop-debugging"></a>Pour arrêter le débogage

Appuyez sur **Maj-F5** ou, dans le menu **Déboguer**, cliquez sur **Arrêter le débogueur**. Ou encore, dans le volet Console, tapez **Q**, puis appuyez sur **Entrée**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Comment effectuer une opération de pas à pas principal, de pas à pas détaillé et de pas à pas sortant lors d’un débogage

Un pas à pas est le processus consistant à exécuter une instruction à la fois. Vous pouvez arrêter l’exécution sur une ligne de code, puis examiner les valeurs des variables et l’état du système. Le tableau suivant décrit des tâches de débogage courantes, telles que l’exécution d’une opération de pas à pas principal, de pas à pas détaillé et de pas à pas sortant.

| Tâche de débogage | Description | Comment l’accomplir dans PowerShell ISE |
| --- | --- | --- |
| **Pas à pas détaillé** | Exécute l’instruction en cours, puis s’arrête à l’instruction suivante. Si l’instruction en cours est une fonction ou appel de script, le débogueur effectue un pas à pas détaillé de cette fonction ou de ce script ; sinon, il s’arrête à l’instruction suivante. | Appuyez sur **F11** ou, dans le menu **Déboguer**, cliquez sur **Pas à pas détaillé**. Ou encore, dans le volet Console, tapez **S**, puis appuyez sur **Entrée**. |
| **Pas à pas principal** | Exécute l’instruction en cours, puis s’arrête à l’instruction suivante. Si l’instruction en cours est un appel de fonction ou un script, le débogueur exécute entièrement la fonction ou le script, puis s’arrête à l’instruction suivante après l’appel de fonction. | Appuyez sur **F10** ou, dans le menu **Déboguer**, cliquez sur **Pas à pas principal**. Ou encore, dans le volet Console, tapez **V**, puis appuyez sur **Entrée**. |
| **Pas à pas sortant** | Sort de la fonction en cours et passe au niveau supérieur si la fonction est imbriquée. Dans le corps principal, le script est exécuté jusqu’à la fin ou jusqu’au point d’arrêt suivant. Les instructions ignorées sont exécutées, mais sans pas à pas. | Appuyez sur **Maj+F11** ou, dans le menu **Déboguer**, cliquez sur **Pas à pas sortant**. Ou encore, dans le volet Console, tapez **O**, puis appuyez sur **Entrée**. |
| **Continuer** | Continue l’exécution jusqu’à la fin ou jusqu’au point d’arrêt suivant. Les fonctions et appels ignorés sont exécutés, mais sans pas à pas. | Appuyez sur **F5** ou, dans le menu **Déboguer**, cliquez sur **Exécuter/Continuer**. Ou encore, dans le volet Console, tapez **C**, puis appuyez sur **Entrée**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Comment afficher les valeurs de variables lors d’un débogage

À mesure que vous exécutez le code pas à pas, vous pouvez afficher les valeurs actuelles des variables dans le script.

### <a name="to-display-the-values-of-standard-variables"></a>Pour afficher les valeurs des variables standards

Appliquez l'une des méthodes suivantes :

- Dans le volet Script, placez le curseur sur la variable pour afficher sa valeur dans une info-bulle.

- Dans le volet Console, tapez le nom de la variable, puis appuyez sur **Entrée**.

Dans ISE, tous les volets sont toujours dans la même étendue. Par conséquent, lorsque vous déboguez un script, les commandes que vous tapez dans le volet Console s’exécutent dans l’étendue du script. Cela permet d’utiliser le volet Console pour rechercher les valeurs des variables et d’appeler des fonctions qui sont définies uniquement dans le script.

### <a name="to-display-the-values-of-automatic-variables"></a>Pour afficher les valeurs de variables automatiques

Vous pouvez utiliser la méthode précédente pour afficher la valeur de presque toutes les variables pendant que vous déboguez un script. En revanche, ces méthodes ne fonctionnent pas pour les variables automatiques suivantes.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Si vous essayez d’afficher la valeur d’une de ces variables, vous l’obtenez pour un pipeline interne que le débogueur utilise, pas la valeur de la variable dans le script. Vous pouvez contourner ce comportement pour quelques variables ($_, $Input, $MyInvocation, $PSBoundParameters et $Args) en utilisant la méthode suivante :

1. Dans le script, affectez la valeur de la variable automatique à une nouvelle variable.

2. Affichez la valeur de la nouvelle variable, soit en pointant sur celle-ci dans le volet Script, ou en la tapant dans le volet Console.

Par exemple, pour afficher la valeur de la variable $MyInvocation, dans le script, affectez la valeur à une nouvelle variable, par exemple $scriptname, puis pointez sur la variable $scriptname ou tapez-la pour afficher sa valeur.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path
```

```output
# In the Console Pane:
PS> .\MyScript.ps1
PS> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Voir aussi

- [Exploration de Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)