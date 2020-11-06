---
ms.date: 06/05/2017
title: Objet PowerShellTab
description: L’objet PowerShellTab représente un environnement d’exécution Windows PowerShell.
ms.openlocfilehash: ac89875e408a41a92d7e3d1a83a849466296c3c6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663390"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="bc8a6-103">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="bc8a6-103">The PowerShellTab Object</span></span>

<span data-ttu-id="bc8a6-104">L’objet **PowerShellTab** représente un environnement d’exécution Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="bc8a6-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bc8a6-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="bc8a6-106">Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="bc8a6-106">Invoke\( Script \)</span></span>

<span data-ttu-id="bc8a6-107">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bc8a6-108">Exécute le script spécifié dans l’onglet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="bc8a6-109">Cette méthode effectue cette action uniquement dans les onglets PowerShell autres que l’onglet PowerShell à partir duquel elle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="bc8a6-110">Elle ne renvoie pas d’objet ou de valeur.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-110">It does not return any object or value.</span></span> <span data-ttu-id="bc8a6-111">Si le code modifie une variable, ces modifications s’appliquent à l’onglet pour lequel la commande a été appelée.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="bc8a6-112">**Script** \- System.Management.Automation.ScriptBlock ou chaîne. Bloc de script à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="bc8a6-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="bc8a6-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="bc8a6-114">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bc8a6-115">Exécute le script spécifié dans l’onglet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="bc8a6-116">Cette méthode effectue cette action uniquement dans les onglets PowerShell autres que l’onglet PowerShell à partir duquel elle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="bc8a6-117">Le bloc de script est exécuté. Les valeurs renvoyées par le script sont renvoyées à l’environnement d’exécution à partir duquel vous avez appelé la commande.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="bc8a6-118">Si la durée d’exécution de la commande dépasse la valeur **millesecondsTimeout** spécifiée, la commande échoue avec une exception : « Le délai de l’opération a expiré. »</span><span class="sxs-lookup"><span data-stu-id="bc8a6-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="bc8a6-119">**Script** \- System.Management.Automation.ScriptBlock ou chaîne. Bloc de script à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="bc8a6-120">**\[useNewScope\]**  : valeur booléenne facultative qui a la valeur `$true`. Si la valeur est `$true`, une nouvelle étendue est créée pour y exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-120">**\[useNewScope\]** -  Optional Boolean that defaults to `$true` If set to `$true`, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="bc8a6-121">Cela ne modifie pas l’environnement d’exécution de l’onglet PowerShell qui est spécifié par la commande.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="bc8a6-122">**\[millisecondsTimeout\]** - Entier facultatif qui a la valeur **500** par défaut.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="bc8a6-123">Si la commande ne se termine pas dans le délai spécifié, la commande génère une exception **TimeoutException** avec le message « Le délai de l’opération a expiré. »</span><span class="sxs-lookup"><span data-stu-id="bc8a6-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="bc8a6-124">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bc8a6-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="bc8a6-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="bc8a6-125">AddOnsMenu</span></span>

<span data-ttu-id="bc8a6-126">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bc8a6-127">Propriété en lecture seule qui obtient le menu complémentaire de l’onglet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="bc8a6-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="bc8a6-128">CanInvoke</span></span>

<span data-ttu-id="bc8a6-129">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bc8a6-130">La propriété booléenne en lecture seule qui renvoie une valeur `$true` si un script peut être appelé avec la méthode [Invoke( Script )](#invoke-script-).</span><span class="sxs-lookup"><span data-stu-id="bc8a6-130">The read-only Boolean property that returns a `$true` value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="bc8a6-131">ConsolePane</span><span class="sxs-lookup"><span data-stu-id="bc8a6-131">ConsolePane</span></span>

<span data-ttu-id="bc8a6-132">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> <span data-ttu-id="bc8a6-133">Dans Windows PowerShell ISE 2.0, cette propriété s’appelait **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="bc8a6-134">Propriété en lecture seule qui obtient l’objet [editor](The-ISEEditor-Object.md) du volet de la console.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="bc8a6-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bc8a6-135">DisplayName</span></span>

<span data-ttu-id="bc8a6-136">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bc8a6-137">Propriété en lecture seule qui obtient ou définit le texte affiché dans l’onglet PowerShell. Par défaut, les onglets sont nommés « PowerShell # », où # est un nombre.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="bc8a6-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="bc8a6-138">ExpandedScript</span></span>

<span data-ttu-id="bc8a6-139">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bc8a6-140">Propriété booléenne en lecture\-écriture qui détermine si le volet de script est développé ou masqué.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="bc8a6-141">Fichiers</span><span class="sxs-lookup"><span data-stu-id="bc8a6-141">Files</span></span>

<span data-ttu-id="bc8a6-142">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bc8a6-143">Propriété en lecture seule qui obtient la [collection des fichiers de script](The-ISEFileCollection-Object.md) qui sont ouverts dans l’onglet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="bc8a6-144">Output</span><span class="sxs-lookup"><span data-stu-id="bc8a6-144">Output</span></span>

<span data-ttu-id="bc8a6-145">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="bc8a6-146">Dans les versions ultérieures de Windows PowerShell ISE, vous pouvez utiliser l’objet **ConsolePane** à la place.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="bc8a6-147">Propriété en lecture seule qui obtient le volet de sortie de l’objet [editor](The-ISEEditor-Object.md) actuel.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="bc8a6-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="bc8a6-148">Prompt</span></span>

<span data-ttu-id="bc8a6-149">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bc8a6-150">Propriété en lecture seule qui obtient le texte d’invite actuel.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="bc8a6-151">Remarque : la fonction **Prompt** peut être remplacée par le profil utilisateur &trade;.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-151">Note: the **Prompt** function can be overridden by the user'&trade;s profile.</span></span> <span data-ttu-id="bc8a6-152">Si le résultat n’est pas une chaîne simple, cette propriété ne renvoie rien.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="bc8a6-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="bc8a6-153">ShowCommands</span></span>

<span data-ttu-id="bc8a6-154">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bc8a6-155">Propriété en lecture\-écriture qui indique si le volet de commandes est actuellement affiché.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="bc8a6-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="bc8a6-156">StatusText</span></span>

<span data-ttu-id="bc8a6-157">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bc8a6-158">Propriété en lecture seule qui obtient le texte d’état **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="bc8a6-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="bc8a6-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="bc8a6-160">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bc8a6-161">Propriété en lecture seule qui indique si le volet des outils complémentaires horizontal est actuellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="bc8a6-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="bc8a6-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="bc8a6-163">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bc8a6-164">Propriété en lecture seule qui indique si le volet des outils complémentaires vertical est actuellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="bc8a6-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="bc8a6-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc8a6-165">See Also</span></span>

- [<span data-ttu-id="bc8a6-166">Objet PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="bc8a6-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="bc8a6-167">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bc8a6-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="bc8a6-168">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="bc8a6-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
