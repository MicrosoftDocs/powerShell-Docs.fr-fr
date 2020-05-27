---
ms.date: 12/31/2019
keywords: powershell,applet de commande
title: Objet ISEOptions
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808625"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="f1f82-103">Objet ISEOptions</span><span class="sxs-lookup"><span data-stu-id="f1f82-103">The ISEOptions Object</span></span>

<span data-ttu-id="f1f82-104">L’objet **ISEOptions** représente différents paramètres pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="f1f82-105">Il s’agit d’une instance de la classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="f1f82-106">L’objet **ISEOptions** fournit les méthodes et propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="f1f82-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="f1f82-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f1f82-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="f1f82-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="f1f82-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="f1f82-109">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-110">Restaure les valeurs par défaut des couleurs de jeton dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="f1f82-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="f1f82-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="f1f82-112">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-113">Restaure les valeurs par défaut de tous les paramètres d’options dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="f1f82-114">Elle réinitialise également le comportement des différents messages d’avertissement qui contiennent la case à cocher standard permettant de ne plus afficher les messages.</span><span class="sxs-lookup"><span data-stu-id="f1f82-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="f1f82-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="f1f82-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="f1f82-116">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-117">Restaure les valeurs par défaut des couleurs de jeton dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="f1f82-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="f1f82-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="f1f82-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="f1f82-119">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-120">Restaure les valeurs par défaut des couleurs de jeton pour les éléments XML affichés dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="f1f82-121">Consultez également [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="f1f82-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="f1f82-122">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f1f82-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="f1f82-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="f1f82-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="f1f82-124">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-125">Spécifie le nombre de minutes entre chaque sauvegarde automatique de vos fichiers par Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="f1f82-126">La valeur par défaut est deux minutes.</span><span class="sxs-lookup"><span data-stu-id="f1f82-126">The default value is 2 minutes.</span></span> <span data-ttu-id="f1f82-127">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="f1f82-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="f1f82-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="f1f82-129">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f1f82-130">Pour les versions ultérieures, consultez [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="f1f82-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="f1f82-131">Spécifie la couleur d’arrière-plan pour le volet de commandes.</span><span class="sxs-lookup"><span data-stu-id="f1f82-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="f1f82-132">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="f1f82-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="f1f82-133">CommandPaneUp</span></span>

<span data-ttu-id="f1f82-134">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="f1f82-135">Spécifie si le volet de commandes se trouve au-dessus du volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1f82-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="f1f82-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="f1f82-137">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-138">Spécifie la couleur d’arrière-plan pour le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="f1f82-139">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="f1f82-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="f1f82-141">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-142">Spécifie la couleur de premier plan pour le texte affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="f1f82-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="f1f82-144">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-145">Spécifie la couleur d’arrière-plan pour le texte affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="f1f82-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="f1f82-146">ConsoleTokenColors</span></span>

<span data-ttu-id="f1f82-147">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-148">Spécifie les couleurs des jetons IntelliSense dans le volet de la console Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="f1f82-149">Cette propriété est un objet dictionnaire qui contient les paires nom\/valeur des types et couleurs des jetons dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="f1f82-150">Pour modifier les couleurs des jetons IntelliSense dans le volet de script, consultez [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="f1f82-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span>
<span data-ttu-id="f1f82-151">Pour restaurer les valeurs par défaut des couleurs, consultez [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="f1f82-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span>
<span data-ttu-id="f1f82-152">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="f1f82-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="f1f82-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-153">DebugBackgroundColor</span></span>

<span data-ttu-id="f1f82-154">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-155">Spécifie la couleur d’arrière-plan pour le texte de débogage affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="f1f82-156">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="f1f82-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-157">DebugForegroundColor</span></span>

<span data-ttu-id="f1f82-158">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-159">Spécifie la couleur de premier plan pour le texte de débogage affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="f1f82-160">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="f1f82-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="f1f82-161">DefaultOptions</span></span>

<span data-ttu-id="f1f82-162">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-163">Collection de propriétés qui spécifient les valeurs par défaut à utiliser avec les méthodes Reset.</span><span class="sxs-lookup"><span data-stu-id="f1f82-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions
```

```Output
SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a><span data-ttu-id="f1f82-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="f1f82-165">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-166">Spécifie la couleur d’arrière-plan pour le texte d’erreur affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="f1f82-167">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="f1f82-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-168">ErrorForegroundColor</span></span>

<span data-ttu-id="f1f82-169">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-170">Spécifie la couleur de premier plan pour le texte d’erreur affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="f1f82-171">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="f1f82-172">FontName</span><span class="sxs-lookup"><span data-stu-id="f1f82-172">FontName</span></span>

<span data-ttu-id="f1f82-173">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-174">Spécifie le nom de la police actuellement utilisée dans le volet de script et le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="f1f82-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="f1f82-175">FontSize</span></span>

<span data-ttu-id="f1f82-176">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-177">Spécifie la taille de la police sous forme de nombre entier.</span><span class="sxs-lookup"><span data-stu-id="f1f82-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="f1f82-178">Cette propriété s’applique au volet de script, au volet de commandes et au volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1f82-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="f1f82-179">La valeur doit être comprise entre 8 et 32.</span><span class="sxs-lookup"><span data-stu-id="f1f82-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="f1f82-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="f1f82-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="f1f82-181">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-182">Spécifie le nombre de secondes pendant lesquelles IntelliSense tente de résoudre le texte que vous venez de taper.</span><span class="sxs-lookup"><span data-stu-id="f1f82-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span>
<span data-ttu-id="f1f82-183">Après ce nombre de secondes, le délai de tentative IntelliSense expire et vous pouvez continuer à taper du texte.</span><span class="sxs-lookup"><span data-stu-id="f1f82-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="f1f82-184">La valeur par défaut est trois secondes.</span><span class="sxs-lookup"><span data-stu-id="f1f82-184">The default value is 3 seconds.</span></span> <span data-ttu-id="f1f82-185">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="f1f82-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="f1f82-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="f1f82-186">MruCount</span></span>

<span data-ttu-id="f1f82-187">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-188">Spécifie le nombre de fichiers récemment ouverts que Windows PowerShell ISE suit et affiche en bas du menu **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="f1f82-189">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="f1f82-189">The default value is 10.</span></span> <span data-ttu-id="f1f82-190">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="f1f82-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="f1f82-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="f1f82-192">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f1f82-193">Pour les versions ultérieures, consultez [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="f1f82-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="f1f82-194">Propriété en lecture\/écriture qui obtient ou définit la couleur d’arrière-plan pour le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1f82-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="f1f82-195">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="f1f82-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="f1f82-197">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f1f82-198">Pour les versions ultérieures, consultez [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="f1f82-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="f1f82-199">Propriété en lecture\/écriture qui modifie la couleur de premier plan du texte affiché dans le volet de sortie de Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="f1f82-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="f1f82-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="f1f82-201">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f1f82-202">Pour les versions ultérieures, consultez [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="f1f82-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="f1f82-203">Propriété en lecture/écriture qui modifie la couleur d’arrière-plan du texte affiché dans le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1f82-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="f1f82-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="f1f82-205">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-206">Propriété en lecture/écriture qui obtient ou définit la couleur d’arrière-plan pour les fichiers.</span><span class="sxs-lookup"><span data-stu-id="f1f82-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="f1f82-207">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="f1f82-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="f1f82-209">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-210">Propriété en lecture/écriture qui obtient ou définit la couleur de premier plan pour les fichiers autres que de script dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="f1f82-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="f1f82-211">Pour définir la couleur de premier plan pour les fichiers de script, utilisez [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="f1f82-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="f1f82-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="f1f82-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="f1f82-213">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-214">Propriété en lecture/écriture qui obtient ou définit l’emplacement du volet de script à l’écran.</span><span class="sxs-lookup"><span data-stu-id="f1f82-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="f1f82-215">Les valeurs possibles sont « Maximized », « Top » ou « Right ».</span><span class="sxs-lookup"><span data-stu-id="f1f82-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="f1f82-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="f1f82-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="f1f82-217">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-218">Spécifie si la liste <kbd>CTRL</kbd>+<kbd>J</kbd> des extraits de code inclut les éléments de démarrage qui sont fournis dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1f82-218">Specifies whether the <kbd>CTRL</kbd>+<kbd>J</kbd> list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="f1f82-219">Si cette propriété est défini e sur `$false`, seuls les extraits de code définis par l’utilisateur sont affichés dans la liste <kbd>CTRL</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f1f82-219">When set to `$false`, only user-defined snippets appear in the <kbd>CTRL</kbd>+<kbd>J</kbd> list.</span></span>
<span data-ttu-id="f1f82-220">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-220">The default value is `$true`.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="f1f82-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="f1f82-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="f1f82-222">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-223">Spécifie si IntelliSense affiche des suggestions de syntaxe, de paramètre et de valeur dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span>
<span data-ttu-id="f1f82-224">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-224">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="f1f82-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="f1f82-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="f1f82-226">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-227">Spécifie si IntelliSense affiche des suggestions de syntaxe, de paramètre et de valeur dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="f1f82-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span>
<span data-ttu-id="f1f82-228">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-228">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="f1f82-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="f1f82-229">ShowLineNumbers</span></span>

<span data-ttu-id="f1f82-230">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-231">Spécifie si le volet de script affiche les numéros de ligne dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="f1f82-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="f1f82-232">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-232">The default value is `$true`.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="f1f82-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="f1f82-233">ShowOutlining</span></span>

<span data-ttu-id="f1f82-234">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-235">Spécifie si le volet de script affiche des crochets pouvant être développés et réduits en regard des sections de code dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="f1f82-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="f1f82-236">Quand les crochets sont affichés, vous pouvez cliquer sur l’icône avec le signe moins `-` à côté du bloc de texte à réduire ou sur l’icône avec le signe plus `+` pour le développer.</span><span class="sxs-lookup"><span data-stu-id="f1f82-236">When they are displayed, you can click the minus `-` icons next to a block of text to collapse it or click the plus `+` icon to expand a block of text.</span></span> <span data-ttu-id="f1f82-237">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-237">The default value is `$true`.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="f1f82-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="f1f82-238">ShowToolBar</span></span>

<span data-ttu-id="f1f82-239">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-240">Spécifie si la barre d’outils ISE est affichée en haut de la fenêtre Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="f1f82-241">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-241">The default value is `$true`.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="f1f82-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="f1f82-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="f1f82-243">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-244">Spécifie si un message d’avertissement s’affiche quand un script est automatiquement enregistré avant de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="f1f82-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span>
<span data-ttu-id="f1f82-245">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-245">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="f1f82-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="f1f82-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="f1f82-247">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-248">Spécifie si un message d’avertissement s’affiche quand le même fichier est ouvert dans plusieurs onglets PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1f82-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="f1f82-249">Si cette propriété est définie sur `$true`, l’ouverture du même fichier dans plusieurs onglets entraîne l’affichage de ce message : « Une copie de ce fichier est ouverte dans un autre onglet PowerShell. Les modifications apportées à ce fichier affecteront toutes les copies ouvertes. »</span><span class="sxs-lookup"><span data-stu-id="f1f82-249">If set to `$true`, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="f1f82-250">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-250">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="f1f82-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="f1f82-251">TokenColors</span></span>

<span data-ttu-id="f1f82-252">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-253">Spécifie les couleurs des jetons IntelliSense dans le volet de script Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="f1f82-254">Cette propriété est un objet dictionnaire qui contient les paires nom/valeur des types et couleurs des jetons dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="f1f82-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="f1f82-255">Pour modifier les couleurs des jetons IntelliSense dans le volet de la console, consultez [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="f1f82-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span>
<span data-ttu-id="f1f82-256">Pour restaurer les valeurs par défaut des couleurs, consultez [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="f1f82-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span>
<span data-ttu-id="f1f82-257">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="f1f82-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="f1f82-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="f1f82-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="f1f82-259">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-260">Spécifie si vous pouvez utiliser la touche Entrée pour sélectionner une option fournie par IntelliSense dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="f1f82-261">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-261">The default value is `$true`.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="f1f82-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="f1f82-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="f1f82-263">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-264">Spécifie si vous pouvez utiliser la touche Entrée pour sélectionner une option fournie par IntelliSense dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="f1f82-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="f1f82-265">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-265">The default value is `$true`.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="f1f82-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="f1f82-266">UseLocalHelp</span></span>

<span data-ttu-id="f1f82-267">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-268">Spécifie si l’aide installée localement ou l’aide en ligne de la bibliothèque TechNet s’affiche quand vous appuyez sur <kbd>F1</kbd> après avoir placé le curseur dans un mot clé.</span><span class="sxs-lookup"><span data-stu-id="f1f82-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press <kbd>F1</kbd> with the cursor positioned in a keyword.</span></span> <span data-ttu-id="f1f82-269">Si cette propriété est définie sur `$true`, une fenêtre contextuelle affiche le contenu de l’aide installée localement.</span><span class="sxs-lookup"><span data-stu-id="f1f82-269">If set to `$true`, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="f1f82-270">Vous pouvez installer les fichiers d’aide en exécutant la commande `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="f1f82-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="f1f82-271">Si cette propriété est définie sur `$false`, votre navigateur s’ouvre et affiche une page de la bibliothèque TechNet.</span><span class="sxs-lookup"><span data-stu-id="f1f82-271">If set to `$false`, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="f1f82-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="f1f82-273">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-274">Spécifie la couleur d’arrière-plan pour le texte de commentaire affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="f1f82-275">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="f1f82-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-276">VerboseForegroundColor</span></span>

<span data-ttu-id="f1f82-277">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-278">Spécifie la couleur de premier plan pour le texte de commentaire affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="f1f82-279">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="f1f82-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-280">WarningBackgroundColor</span></span>

<span data-ttu-id="f1f82-281">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-282">Spécifie la couleur d’arrière-plan pour le texte d’avertissement affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="f1f82-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="f1f82-283">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="f1f82-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f1f82-284">WarningForegroundColor</span></span>

<span data-ttu-id="f1f82-285">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f1f82-286">Spécifie la couleur de premier plan pour le texte d’avertissement affiché dans le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1f82-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="f1f82-287">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f1f82-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="f1f82-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="f1f82-288">XmlTokenColors</span></span>

<span data-ttu-id="f1f82-289">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-290">Spécifie un objet dictionnaire qui contient les paires nom/valeur des types et couleurs des jetons pour le contenu XML qui s’affiche dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f82-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="f1f82-291">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="f1f82-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="f1f82-292">Consultez également [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="f1f82-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="f1f82-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="f1f82-293">Zoom</span></span>

<span data-ttu-id="f1f82-294">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f1f82-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f1f82-295">Spécifie la taille relative du texte dans les volets de la console et de script.</span><span class="sxs-lookup"><span data-stu-id="f1f82-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="f1f82-296">La valeur par défaut est 100.</span><span class="sxs-lookup"><span data-stu-id="f1f82-296">The default value is 100.</span></span>
<span data-ttu-id="f1f82-297">Utilisez des valeurs plus basses pour réduire la taille du texte affiché dans Windows PowerShell ISE ou des valeurs plus élevées pour augmenter la taille du texte affiché.</span><span class="sxs-lookup"><span data-stu-id="f1f82-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="f1f82-298">La valeur est un nombre entier compris entre 20 et 400.</span><span class="sxs-lookup"><span data-stu-id="f1f82-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="f1f82-299">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1f82-299">See Also</span></span>

- [<span data-ttu-id="f1f82-300">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f1f82-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f1f82-301">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="f1f82-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
