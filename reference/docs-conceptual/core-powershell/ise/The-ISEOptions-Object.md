---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Objet ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 5e04adeebacfb9214bf39d9ec9c5f0e01f5729ee
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="1d901-103">Objet ISEOptions</span><span class="sxs-lookup"><span data-stu-id="1d901-103">The ISEOptions Object</span></span>
  <span data-ttu-id="1d901-104">L’objet **ISEOptions** représente différents paramètres pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="1d901-105">Il s’agit d’une instance de la classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="1d901-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="1d901-106">L’objet **ISEOptions** fournit les méthodes et propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="1d901-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="1d901-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1d901-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="1d901-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="1d901-108">RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="1d901-109">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-110">Restaure les valeurs par défaut des couleurs de jeton dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-110">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="1d901-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="1d901-111">RestoreDefaults\(\)</span></span>
  <span data-ttu-id="1d901-112">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-113">Restaure les valeurs par défaut de tous les paramètres d’options dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="1d901-114">Elle réinitialise également le comportement des différents messages d’avertissement qui contiennent la case à cocher standard permettant de ne plus afficher les messages.</span><span class="sxs-lookup"><span data-stu-id="1d901-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="1d901-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="1d901-115">RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="1d901-116">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-117">Restaure les valeurs par défaut des couleurs de jeton dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="1d901-117">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="1d901-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="1d901-118">RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="1d901-119">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-120">Restaure les valeurs par défaut des couleurs de jeton pour les éléments XML affichés dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="1d901-121">Consultez également [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="1d901-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="1d901-122">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1d901-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="1d901-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="1d901-123">AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="1d901-124">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-125">Spécifie le nombre de minutes entre chaque sauvegarde automatique de vos fichiers par Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="1d901-126">La valeur par défaut est deux minutes.</span><span class="sxs-lookup"><span data-stu-id="1d901-126">The default value is 2 minutes.</span></span> <span data-ttu-id="1d901-127">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="1d901-127">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="1d901-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-128">CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="1d901-129">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="1d901-130">Pour les versions ultérieures, consultez [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="1d901-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="1d901-131">Spécifie la couleur d’arrière-plan pour le volet de commandes.</span><span class="sxs-lookup"><span data-stu-id="1d901-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="1d901-132">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

### <a name="commandpaneup"></a><span data-ttu-id="1d901-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="1d901-133">CommandPaneUp</span></span>
  <span data-ttu-id="1d901-134">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="1d901-135">Spécifie si le volet de commandes se trouve au-dessus du volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="1d901-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="1d901-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-136">ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="1d901-137">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-138">Spécifie la couleur d’arrière-plan pour le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="1d901-139">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="1d901-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-140">ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="1d901-141">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-142">Spécifie la couleur de premier plan pour le texte affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-142">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="1d901-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-143">ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="1d901-144">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-145">Spécifie la couleur d’arrière-plan pour le texte affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-145">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

### <a name="consoletokencolors"></a><span data-ttu-id="1d901-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="1d901-146">ConsoleTokenColors</span></span>
  <span data-ttu-id="1d901-147">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-148">Spécifie les couleurs des jetons IntelliSense dans le volet de la console Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="1d901-149">Cette propriété est un objet dictionnaire qui contient les paires nom\/valeur des types et couleurs des jetons dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="1d901-150">Pour modifier les couleurs des jetons IntelliSense dans le volet de script, consultez [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="1d901-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="1d901-151">Pour restaurer les valeurs par défaut des couleurs, consultez [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="1d901-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="1d901-152">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="1d901-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="1d901-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-153">DebugBackgroundColor</span></span>
  <span data-ttu-id="1d901-154">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-155">Spécifie la couleur d’arrière-plan pour le texte de débogage affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="1d901-156">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="1d901-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-157">DebugForegroundColor</span></span>
  <span data-ttu-id="1d901-158">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-159">Spécifie la couleur de premier plan pour le texte de débogage affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="1d901-160">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

### <a name="defaultoptions"></a><span data-ttu-id="1d901-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="1d901-161">DefaultOptions</span></span>
  <span data-ttu-id="1d901-162">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-163">Collection de propriétés qui spécifient les valeurs par défaut à utiliser avec les méthodes Reset.</span><span class="sxs-lookup"><span data-stu-id="1d901-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="1d901-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-164">ErrorBackgroundColor</span></span>
  <span data-ttu-id="1d901-165">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-166">Spécifie la couleur d’arrière-plan pour le texte d’erreur affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="1d901-167">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="1d901-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-168">ErrorForegroundColor</span></span>
  <span data-ttu-id="1d901-169">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-170">Spécifie la couleur de premier plan pour le texte d’erreur affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="1d901-171">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

### <a name="fontname"></a><span data-ttu-id="1d901-172">FontName</span><span class="sxs-lookup"><span data-stu-id="1d901-172">FontName</span></span>
  <span data-ttu-id="1d901-173">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-174">Spécifie le nom de la police actuellement utilisée dans le volet de script et le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

### <a name="fontsize"></a><span data-ttu-id="1d901-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="1d901-175">FontSize</span></span>
  <span data-ttu-id="1d901-176">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-177">Spécifie la taille de la police sous forme de nombre entier.</span><span class="sxs-lookup"><span data-stu-id="1d901-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="1d901-178">Cette propriété s’applique au volet de script, au volet de commandes et au volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="1d901-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="1d901-179">La valeur doit être comprise entre 8 et 32.</span><span class="sxs-lookup"><span data-stu-id="1d901-179">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="1d901-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="1d901-180">IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="1d901-181">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-182">Spécifie le nombre de secondes pendant lesquelles IntelliSense tente de résoudre le texte que vous venez de taper.</span><span class="sxs-lookup"><span data-stu-id="1d901-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="1d901-183">Après ce nombre de secondes, le délai de tentative IntelliSense expire et vous pouvez continuer à taper du texte.</span><span class="sxs-lookup"><span data-stu-id="1d901-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="1d901-184">La valeur par défaut est trois secondes.</span><span class="sxs-lookup"><span data-stu-id="1d901-184">The default value is 3 seconds.</span></span> <span data-ttu-id="1d901-185">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="1d901-185">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="1d901-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="1d901-186">MruCount</span></span>
  <span data-ttu-id="1d901-187">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-188">Spécifie le nombre de fichiers récemment ouverts que Windows PowerShell ISE suit et affiche en bas du menu **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="1d901-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="1d901-189">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="1d901-189">The default value is 10.</span></span> <span data-ttu-id="1d901-190">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="1d901-190">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="1d901-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-191">OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="1d901-192">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="1d901-193">Pour les versions ultérieures, consultez [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="1d901-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="1d901-194">Propriété en lecture\/écriture qui obtient ou définit la couleur d’arrière-plan pour le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="1d901-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="1d901-195">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="1d901-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-196">OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="1d901-197">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="1d901-198">Pour les versions ultérieures, consultez [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="1d901-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

 <span data-ttu-id="1d901-199">Propriété en lecture\/écriture qui modifie la couleur de premier plan du texte affiché dans le volet de sortie de Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="1d901-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="1d901-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-200">OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="1d901-201">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="1d901-202">Pour les versions ultérieures, consultez [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="1d901-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

 <span data-ttu-id="1d901-203">Propriété en lecture/écriture qui modifie la couleur d’arrière-plan du texte affiché dans le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="1d901-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="1d901-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-204">ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="1d901-205">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-206">Propriété en lecture/écriture qui obtient ou définit la couleur d’arrière-plan pour les fichiers.</span><span class="sxs-lookup"><span data-stu-id="1d901-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="1d901-207">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'

```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="1d901-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-208">ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="1d901-209">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-210">Propriété en lecture/écriture qui obtient ou définit la couleur de premier plan pour les fichiers autres que de script dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="1d901-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="1d901-211">Pour définir la couleur de premier plan pour les fichiers de script, utilisez [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="1d901-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="1d901-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="1d901-212">SelectedScriptPaneState</span></span>
  <span data-ttu-id="1d901-213">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-214">Propriété en lecture/écriture qui obtient ou définit l’emplacement du volet de script à l’écran.</span><span class="sxs-lookup"><span data-stu-id="1d901-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="1d901-215">Les valeurs possibles sont « Maximized », « Top » ou « Right ».</span><span class="sxs-lookup"><span data-stu-id="1d901-215">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

### <a name="showdefaultsnippets"></a><span data-ttu-id="1d901-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="1d901-216">ShowDefaultSnippets</span></span>
  <span data-ttu-id="1d901-217">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-218">Spécifie si la liste **Ctrl+J** des extraits de code inclut les éléments de démarrage qui sont fournis dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d901-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="1d901-219">Si cette propriété a la valeur **$false**, la liste **Ctrl+J** contient uniquement les extraits de code définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1d901-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="1d901-220">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-220">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="1d901-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="1d901-221">ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="1d901-222">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-223">Spécifie si IntelliSense affiche des suggestions de syntaxe, de paramètre et de valeur dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="1d901-224">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-224">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="1d901-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="1d901-225">ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="1d901-226">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-227">Spécifie si IntelliSense affiche des suggestions de syntaxe, de paramètre et de valeur dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="1d901-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="1d901-228">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-228">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="1d901-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="1d901-229">ShowLineNumbers</span></span>
  <span data-ttu-id="1d901-230">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-231">Spécifie si le volet de script affiche les numéros de ligne dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="1d901-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="1d901-232">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-232">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="1d901-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="1d901-233">ShowOutlining</span></span>
  <span data-ttu-id="1d901-234">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-235">Spécifie si le volet de script affiche des crochets pouvant être développés et réduits en regard des sections de code dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="1d901-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="1d901-236">Quand les crochets sont affichés, vous pouvez cliquer sur l’icône avec le signe moins \(-\) à côté du bloc de texte à réduire ou sur l’icône avec le signe plus \(+\) pour le développer.</span><span class="sxs-lookup"><span data-stu-id="1d901-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="1d901-237">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-237">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="1d901-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="1d901-238">ShowToolBar</span></span>
  <span data-ttu-id="1d901-239">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-240">Spécifie si la barre d’outils ISE est affichée en haut de la fenêtre Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="1d901-241">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-241">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="1d901-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="1d901-242">ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="1d901-243">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-244">Spécifie si un message d’avertissement s’affiche quand un script est automatiquement enregistré avant de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="1d901-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="1d901-245">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-245">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="1d901-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="1d901-246">ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="1d901-247">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-248">Spécifie si un message d’avertissement s’affiche quand le même fichier est ouvert dans plusieurs onglets PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d901-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="1d901-249">Si cette propriété a la valeur **$true**, l’ouverture du même fichier dans plusieurs onglets entraîne l’affichage de ce message : « Une copie de ce fichier est ouverte dans un autre onglet PowerShell. Les modifications apportées à ce fichier affecteront toutes les copies ouvertes. »</span><span class="sxs-lookup"><span data-stu-id="1d901-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="1d901-250">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-250">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

### <a name="tokencolors"></a><span data-ttu-id="1d901-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="1d901-251">TokenColors</span></span>
  <span data-ttu-id="1d901-252">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-253">Spécifie les couleurs des jetons IntelliSense dans le volet de script Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="1d901-254">Cette propriété est un objet dictionnaire qui contient les paires nom/valeur des types et couleurs des jetons dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="1d901-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="1d901-255">Pour modifier les couleurs des jetons IntelliSense dans le volet de la console, consultez [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="1d901-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="1d901-256">Pour restaurer les valeurs par défaut des couleurs, consultez [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="1d901-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="1d901-257">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="1d901-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="1d901-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="1d901-258">UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="1d901-259">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-260">Spécifie si vous pouvez utiliser la touche Entrée pour sélectionner une option fournie par IntelliSense dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="1d901-261">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-261">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="1d901-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="1d901-262">UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="1d901-263">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-264">Spécifie si vous pouvez utiliser la touche Entrée pour sélectionner une option fournie par IntelliSense dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="1d901-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="1d901-265">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="1d901-265">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

### <a name="uselocalhelp"></a><span data-ttu-id="1d901-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="1d901-266">UseLocalHelp</span></span>
  <span data-ttu-id="1d901-267">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-268">Spécifie si l’aide installée localement ou l’aide en ligne de la bibliothèque TechNet s’affiche quand vous appuyez sur F1 après avoir placé le curseur dans un mot clé.</span><span class="sxs-lookup"><span data-stu-id="1d901-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="1d901-269">Si cette propriété a la valeur **$true**, une fenêtre contextuelle affiche le contenu de l’aide installée localement.</span><span class="sxs-lookup"><span data-stu-id="1d901-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="1d901-270">Vous pouvez installer les fichiers d’aide en exécutant la commande `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="1d901-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="1d901-271">Si cette propriété a la valeur **$false**, votre navigateur s’ouvre et affiche une page de la bibliothèque TechNet.</span><span class="sxs-lookup"><span data-stu-id="1d901-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="1d901-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-272">VerboseBackgroundColor</span></span>
  <span data-ttu-id="1d901-273">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-274">Spécifie la couleur d’arrière-plan pour le texte de commentaire affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="1d901-275">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-275">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="1d901-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-276">VerboseForegroundColor</span></span>
  <span data-ttu-id="1d901-277">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-278">Spécifie la couleur de premier plan pour le texte de commentaire affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="1d901-279">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-279">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor ='yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="1d901-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-280">WarningBackgroundColor</span></span>
  <span data-ttu-id="1d901-281">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-282">Spécifie la couleur d’arrière-plan pour le texte d’avertissement affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="1d901-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="1d901-283">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-283">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="1d901-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1d901-284">WarningForegroundColor</span></span>
  <span data-ttu-id="1d901-285">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1d901-286">Spécifie la couleur de premier plan pour le texte d’avertissement affiché dans le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="1d901-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="1d901-287">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="1d901-287">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor ='yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="1d901-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="1d901-288">XmlTokenColors</span></span>
  <span data-ttu-id="1d901-289">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-290">Spécifie un objet dictionnaire qui contient les paires nom/valeur des types et couleurs des jetons pour le contenu XML qui s’affiche dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1d901-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="1d901-291">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="1d901-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="1d901-292">Consultez également [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="1d901-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

### <a name="zoom"></a><span data-ttu-id="1d901-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="1d901-293">Zoom</span></span>
  <span data-ttu-id="1d901-294">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="1d901-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1d901-295">Spécifie la taille relative du texte dans les volets de la console et de script.</span><span class="sxs-lookup"><span data-stu-id="1d901-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="1d901-296">La valeur par défaut est 100.</span><span class="sxs-lookup"><span data-stu-id="1d901-296">The default value is 100.</span></span> <span data-ttu-id="1d901-297">Utilisez des valeurs plus basses pour réduire la taille du texte affiché dans Windows PowerShell ISE ou des valeurs plus élevées pour augmenter la taille du texte affiché.</span><span class="sxs-lookup"><span data-stu-id="1d901-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="1d901-298">La valeur est un nombre entier compris entre 20 et 400.</span><span class="sxs-lookup"><span data-stu-id="1d901-298">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="1d901-299">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d901-299">See Also</span></span>
- [<span data-ttu-id="1d901-300">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1d901-300">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="1d901-301">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1d901-301">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

