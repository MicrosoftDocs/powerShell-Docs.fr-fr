---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet PowerShellTab
ms.openlocfilehash: 55e3678a8285f0ec7e8131d98c87478216c26f37
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402516"
---
# <a name="the-powershelltab-object"></a>Objet PowerShellTab

L’objet **PowerShellTab** représente un environnement d’exécution Windows PowerShell.

## <a name="methods"></a>Méthodes

### <a name="invoke-script-"></a>Invoke\( Script \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Exécute le script spécifié dans l’onglet PowerShell.

> [!NOTE]
> Cette méthode effectue cette action uniquement dans les onglets PowerShell autres que l’onglet PowerShell à partir duquel elle est exécutée. Elle ne renvoie pas d’objet ou de valeur. Si le code modifie une variable, ces modifications s’appliquent à l’onglet pour lequel la commande a été appelée.

**Script** \- System.Management.Automation.ScriptBlock ou chaîne. Bloc de script à utiliser.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Exécute le script spécifié dans l’onglet PowerShell.

> [!NOTE]
> Cette méthode effectue cette action uniquement dans les onglets PowerShell autres que l’onglet PowerShell à partir duquel elle est exécutée. Le bloc de script est exécuté. Les valeurs renvoyées par le script sont renvoyées à l’environnement d’exécution à partir duquel vous avez appelé la commande. Si la durée d’exécution de la commande dépasse la valeur **millesecondsTimeout** spécifiée, la commande échoue avec une exception : « Le délai de l’opération a expiré. »

**Script** \- System.Management.Automation.ScriptBlock ou chaîne. Bloc de script à utiliser.

**\[useNewScope\]**  : valeur booléenne facultative qui a la valeur `$true`. Si la valeur est `$true`, une nouvelle étendue est créée pour y exécuter la commande. Cela ne modifie pas l’environnement d’exécution de l’onglet PowerShell qui est spécifié par la commande.

**\[millisecondsTimeout\]** - Entier facultatif qui a la valeur **500** par défaut.
Si la commande ne se termine pas dans le délai spécifié, la commande génère une exception **TimeoutException** avec le message « Le délai de l’opération a expiré. »

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a>Propriétés

### <a name="addonsmenu"></a>AddOnsMenu

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le menu complémentaire de l’onglet PowerShell.

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

La propriété booléenne en lecture seule qui renvoie une valeur `$true` si un script peut être appelé avec la méthode [Invoke( Script )](#invoke-script-).

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a>ConsolePane

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures. Dans Windows PowerShell ISE 2.0, cette propriété s’appelait **CommandPane**.

Propriété en lecture seule qui obtient l’objet [editor](The-ISEEditor-Object.md) du volet de la console.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient ou définit le texte affiché dans l’onglet PowerShell. Par défaut, les onglets sont nommés « PowerShell # », où # est un nombre.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété booléenne en lecture\-écriture qui détermine si le volet de script est développé ou masqué.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Fichiers

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient la [collection des fichiers de script](The-ISEFileCollection-Object.md) qui sont ouverts dans l’onglet PowerShell.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Output

Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE. Dans les versions ultérieures de Windows PowerShell ISE, vous pouvez utiliser l’objet **ConsolePane** à la place.

Propriété en lecture seule qui obtient le volet de sortie de l’objet [editor](The-ISEEditor-Object.md) actuel.

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Prompt

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le texte d’invite actuel. Remarque : La fonction **Prompt** peut être remplacée par le profil utilisateur. Si le résultat n’est pas une chaîne simple, cette propriété ne renvoie rien.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture\-écriture qui indique si le volet de commandes est actuellement affiché.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le texte d’état **PowerShellTab**.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture seule qui indique si le volet des outils complémentaires horizontal est actuellement ouvert.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Propriété en lecture seule qui indique si le volet des outils complémentaires vertical est actuellement ouvert.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Voir aussi

- [Objet PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
