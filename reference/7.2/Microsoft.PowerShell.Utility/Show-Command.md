---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: 87bdd5a9610267b8fce9e391431d24872a77e2de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595728"
---
# <span data-ttu-id="da207-102">Show-Command</span><span class="sxs-lookup"><span data-stu-id="da207-102">Show-Command</span></span>

## <span data-ttu-id="da207-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="da207-103">SYNOPSIS</span></span>
<span data-ttu-id="da207-104">Affiche des informations de commande PowerShell dans une fenêtre graphique.</span><span class="sxs-lookup"><span data-stu-id="da207-104">Displays PowerShell command information in a graphical window.</span></span>

## <span data-ttu-id="da207-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="da207-105">SYNTAX</span></span>

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="da207-106">Description</span><span class="sxs-lookup"><span data-stu-id="da207-106">DESCRIPTION</span></span>

<span data-ttu-id="da207-107">L' `Show-Command` applet de commande vous permet de créer une commande PowerShell dans une fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="da207-107">The `Show-Command` cmdlet lets you create a PowerShell command in a command window.</span></span> <span data-ttu-id="da207-108">Vous pouvez utiliser les fonctionnalités de la fenêtre de commandes pour qu'elle exécute la commande, ou pour qu'elle vous la retourne.</span><span class="sxs-lookup"><span data-stu-id="da207-108">You can use the features of the command window to run the command or have it return the command to you.</span></span>

<span data-ttu-id="da207-109">`Show-Command` est un outil d’apprentissage et d’apprentissage très utile.</span><span class="sxs-lookup"><span data-stu-id="da207-109">`Show-Command` is a very useful teaching and learning tool.</span></span> <span data-ttu-id="da207-110">`Show-Command` fonctionne sur tous les types de commandes, y compris les applets de commande, les fonctions, les flux de travail et les commandes CIM.</span><span class="sxs-lookup"><span data-stu-id="da207-110">`Show-Command` works on all command types, including cmdlets, functions, workflows and CIM commands.</span></span>

<span data-ttu-id="da207-111">Sans paramètres, `Show-Command` affiche une fenêtre de commande qui répertorie toutes les commandes disponibles dans tous les modules installés.</span><span class="sxs-lookup"><span data-stu-id="da207-111">Without parameters, `Show-Command` displays a command window that lists all available commands in all installed modules.</span></span> <span data-ttu-id="da207-112">Pour trouver les commandes d'un module, sélectionnez le module dans la liste déroulante Modules.</span><span class="sxs-lookup"><span data-stu-id="da207-112">To find the commands in a module, select the module from the Modules drop-down list.</span></span> <span data-ttu-id="da207-113">Pour sélectionner une commande, cliquez sur son nom.</span><span class="sxs-lookup"><span data-stu-id="da207-113">To select a command, click the command name.</span></span>

<span data-ttu-id="da207-114">Pour utiliser la fenêtre commande, sélectionnez une commande, en utilisant le nom ou en cliquant sur le nom de la commande dans la liste **commandes** .</span><span class="sxs-lookup"><span data-stu-id="da207-114">To use the command window, select a command, either by using the Name or by clicking the command name in the **Commands** list.</span></span> <span data-ttu-id="da207-115">Chaque jeu de paramètres s’affiche sous un onglet distinct. Les astérisques indiquent les paramètres obligatoires.</span><span class="sxs-lookup"><span data-stu-id="da207-115">Each parameter set is displayed on a separate tab. Asterisks indicate the mandatory parameters.</span></span> <span data-ttu-id="da207-116">Pour entrer des valeurs pour un paramètre, tapez la valeur dans la zone de texte ou sélectionnez la valeur dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="da207-116">To enter values for a parameter, type the value in the text box or select the value from the drop-down box.</span></span> <span data-ttu-id="da207-117">Pour ajouter un paramètre de commutateur, cliquez et cochez la case du paramètre.</span><span class="sxs-lookup"><span data-stu-id="da207-117">To add a switch parameter, click to select the parameter check box.</span></span>

<span data-ttu-id="da207-118">Quand vous êtes prêt, cliquez sur **Copy** pour copier la commande que vous avez créée dans le Presse-papiers, ou cliquez sur **Run** pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="da207-118">When you're ready, you can click **Copy** to copy the command that you've created to the clipboard or click **Run** to run the command.</span></span> <span data-ttu-id="da207-119">Vous pouvez également utiliser le paramètre **PassThru** pour retourner la commande au programme hôte, tel que la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da207-119">You can also use the **PassThru** parameter to return the command to the host program, such as the PowerShell console.</span></span> <span data-ttu-id="da207-120">Pour annuler la sélection de la commande et revenir à la vue qui affiche toutes les commandes, appuyez sur Ctrl et cliquez sur la commande sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="da207-120">To cancel the command selection and return to the view that displays all commands, press Ctrl and click the selected command.</span></span>

<span data-ttu-id="da207-121">Dans l’environnement d’écriture de scripts intégré (ISE) de PowerShell, une variante de la `Show-Command` fenêtre s’affiche par défaut.</span><span class="sxs-lookup"><span data-stu-id="da207-121">In the PowerShell Integrated Scripting Environment (ISE), a variation of the `Show-Command` window is displayed by default.</span></span> <span data-ttu-id="da207-122">Pour plus d’informations sur l’utilisation de cette fenêtre de commande, consultez les rubriques d’aide de PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="da207-122">For information about using this command window, see the PowerShell ISE Help topics.</span></span>

<span data-ttu-id="da207-123">Cette applet de commande a été réintroduite dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="da207-123">This cmdlet was reintroduced in PowerShell 7.</span></span>

<span data-ttu-id="da207-124">Étant donné que cette applet de commande nécessite une interface utilisateur, elle ne fonctionne pas sur Windows Server Core ou Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="da207-124">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="da207-125">Cette applet de commande est uniquement disponible sur les systèmes Windows qui prennent en charge le bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="da207-125">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="da207-126">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="da207-126">EXAMPLES</span></span>

### <span data-ttu-id="da207-127">Exemple 1 : ouvrir la fenêtre commandes</span><span class="sxs-lookup"><span data-stu-id="da207-127">Example 1: Open the Commands window</span></span>

<span data-ttu-id="da207-128">Cet exemple affiche la vue par défaut de la `Show-Command` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="da207-128">This example displays the default view of the `Show-Command` window.</span></span> <span data-ttu-id="da207-129">La fenêtre **commandes** affiche une liste de toutes les commandes de tous les modules installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="da207-129">The **Commands** window displays a list of all commands in all modules that are installed on the computer.</span></span>

```powershell
Show-Command
```

### <span data-ttu-id="da207-130">Exemple 2 : ouvrir une applet de commande dans la fenêtre commandes</span><span class="sxs-lookup"><span data-stu-id="da207-130">Example 2: Open a cmdlet in the Commands window</span></span>

<span data-ttu-id="da207-131">Cet exemple affiche l' `Invoke-Command` applet de commande dans la fenêtre **commande** .</span><span class="sxs-lookup"><span data-stu-id="da207-131">This example display the `Invoke-Command` cmdlet in the **Command** window.</span></span> <span data-ttu-id="da207-132">Vous pouvez utiliser cet affichage pour exécuter des `Invoke-Command` commandes.</span><span class="sxs-lookup"><span data-stu-id="da207-132">You can use this display to run `Invoke-Command` commands.</span></span>

```powershell
Show-Command -Name "Invoke-Command"
```

### <span data-ttu-id="da207-133">Exemple 3 : ouvrir une applet de commande avec les paramètres spécifiés</span><span class="sxs-lookup"><span data-stu-id="da207-133">Example 3: Open a cmdlet with specified parameters</span></span>

<span data-ttu-id="da207-134">Cette commande ouvre une `Show-Command` fenêtre pour l' `Connect-PSSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="da207-134">This command opens a `Show-Command` window for the`Connect-PSSession`cmdlet.</span></span>

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

<span data-ttu-id="da207-135">Les paramètres de **hauteur** et de **largeur** spécifient la dimension de la fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="da207-135">The **Height** and **Width** parameters specify the dimension of the command window.</span></span> <span data-ttu-id="da207-136">Le paramètre **ErrorPopup** affiche la fenêtre d’erreur de la commande.</span><span class="sxs-lookup"><span data-stu-id="da207-136">The **ErrorPopup** parameter displays the error command window.</span></span>

<span data-ttu-id="da207-137">Lorsque vous cliquez sur **exécuter**, la `Connect-PSSession` commande s’exécute, comme si vous tapiiez la `Connect-PSSession` commande sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="da207-137">When you click **Run**, the `Connect-PSSession` command runs, just as would if you typed the `Connect-PSSession` command at the command line.</span></span>

### <span data-ttu-id="da207-138">Exemple 4 : spécifier les nouvelles valeurs de paramètre par défaut pour une applet de commande</span><span class="sxs-lookup"><span data-stu-id="da207-138">Example 4: Specify new default parameter values for a cmdlet</span></span>

<span data-ttu-id="da207-139">Cet exemple utilise la `$PSDefaultParameterValues` variable Automatic pour définir de nouvelles valeurs par défaut pour les paramètres de **hauteur**, de **largeur** et de **ErrorPopup** de l’applet de commande `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="da207-139">This example uses the `$PSDefaultParameterValues` automatic variable to set new default values for the **Height**, **Width**, and **ErrorPopup** parameters of the `Show-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

<span data-ttu-id="da207-140">Désormais, lorsque vous exécutez une `Show-Command` commande, les nouvelles valeurs par défaut sont appliquées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="da207-140">Now when you run a `Show-Command` command, the new defaults are applied automatically.</span></span> <span data-ttu-id="da207-141">Pour utiliser ces valeurs par défaut dans chaque session PowerShell, ajoutez la `$PSDefaultParameterValues` variable à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da207-141">To use these default values in every PowerShell session, add the `$PSDefaultParameterValues` variable to your PowerShell profile.</span></span> <span data-ttu-id="da207-142">Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) et [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).</span><span class="sxs-lookup"><span data-stu-id="da207-142">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) and [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).</span></span>

### <span data-ttu-id="da207-143">Exemple 5 : envoyer une sortie vers une vue grille</span><span class="sxs-lookup"><span data-stu-id="da207-143">Example 5: Send output to a grid view</span></span>

<span data-ttu-id="da207-144">Cette commande montre comment utiliser les `Show-Command` `Out-GridView` cmdlets et ensemble.</span><span class="sxs-lookup"><span data-stu-id="da207-144">This command shows how to use the `Show-Command` and `Out-GridView` cmdlets together.</span></span>

```powershell
Show-Command Get-ChildItem | Out-GridView
```

<span data-ttu-id="da207-145">La commande utilise l' `Show-Command` applet de commande pour ouvrir une fenêtre de commande pour l’applet de commande `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="da207-145">The command uses the `Show-Command` cmdlet to open a command window for the`Get-ChildItem`cmdlet.</span></span>
<span data-ttu-id="da207-146">Lorsque vous cliquez sur le bouton **exécuter** , la `Get-ChildItem` commande s’exécute et génère une sortie.</span><span class="sxs-lookup"><span data-stu-id="da207-146">When you click the **Run** button, the `Get-ChildItem` command runs and generates output.</span></span> <span data-ttu-id="da207-147">L’opérateur de pipeline (|) envoie la sortie de la `Get-ChildItem` commande à l’applet de commande `Out-GridView` , qui affiche la `Get-ChildItem` sortie dans une fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="da207-147">The pipeline operator ( | ) sends the output of the `Get-ChildItem` command to the `Out-GridView` cmdlet, which displays the `Get-ChildItem` output in an interactive window.</span></span>

### <span data-ttu-id="da207-148">Exemple 6 : afficher une commande que vous créez dans la fenêtre commandes</span><span class="sxs-lookup"><span data-stu-id="da207-148">Example 6: Display a command that you create in the Commands window</span></span>

<span data-ttu-id="da207-149">Cet exemple montre la commande que vous avez créée dans la `Show-Command` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="da207-149">This example shows the command that you created in the `Show-Command` window.</span></span> <span data-ttu-id="da207-150">La commande utilise le paramètre **PassThru** , qui retourne les `Show-Command` résultats dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="da207-150">The command uses the **PassThru** parameter, which returns the `Show-Command` results in a string.</span></span>

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

<span data-ttu-id="da207-151">Par exemple, si vous utilisez la `Show-Command` fenêtre pour créer une `Get-EventLog` commande qui obtient les cinq événements les plus récents dans le journal des événements Windows PowerShell, puis cliquez sur **OK**, la commande renvoie la sortie indiquée ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="da207-151">For example, if you use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log, and then click **OK**, the command returns the output shown above.</span></span> <span data-ttu-id="da207-152">L’affichage de la chaîne de commande vous aide à découvrir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da207-152">Viewing the command string helps you learn PowerShell.</span></span>

### <span data-ttu-id="da207-153">Exemple 7 : enregistrer une commande dans une variable</span><span class="sxs-lookup"><span data-stu-id="da207-153">Example 7: Save a command to a variable</span></span>

<span data-ttu-id="da207-154">Cet exemple montre comment exécuter la chaîne de commande que vous recevez quand vous utilisez le paramètre **PassThru** de l' `Show-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="da207-154">This example shows how to run the command string that you get when you use the **PassThru** parameter of the `Show-Command` cmdlet.</span></span> <span data-ttu-id="da207-155">Cette stratégie vous permet de voir la commande et de l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="da207-155">This strategy lets you see the command and use it.</span></span>

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

<span data-ttu-id="da207-156">La première commande utilise le paramètre **PassThru** de l' `Show-Command` applet de commande et enregistre les résultats de la commande dans la `$C` variable.</span><span class="sxs-lookup"><span data-stu-id="da207-156">The first command uses the **PassThru** parameter of the `Show-Command` cmdlet and saves the results of the command in the `$C` variable.</span></span> <span data-ttu-id="da207-157">Dans ce cas, nous utilisons la `Show-Command` fenêtre pour créer une `Get-EventLog` commande qui obtient les cinq événements les plus récents dans le journal des événements Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da207-157">In this case, we use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log.</span></span> <span data-ttu-id="da207-158">Lorsque vous cliquez sur **OK**, `Show-Command` retourne la chaîne de commande, qui est enregistrée dans la `$C` variable.</span><span class="sxs-lookup"><span data-stu-id="da207-158">When you click **OK**, `Show-Command` returns the command string, which is saved in the `$C` variable.</span></span>

### <span data-ttu-id="da207-159">Exemple 8 : enregistrer la sortie d’une commande dans une variable</span><span class="sxs-lookup"><span data-stu-id="da207-159">Example 8: Save the output of a command to a variable</span></span>

<span data-ttu-id="da207-160">Cet exemple utilise le paramètre **ErrorPopup** pour enregistrer la sortie d’une commande dans une variable.</span><span class="sxs-lookup"><span data-stu-id="da207-160">This example uses the **ErrorPopup** parameter to save the output of a command in a variable.</span></span>

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

<span data-ttu-id="da207-161">Outre l'affichage des erreurs dans une fenêtre, **ErrorPopup** retourne la sortie de commande dans la commande actuelle, au lieu de créer une commande.</span><span class="sxs-lookup"><span data-stu-id="da207-161">In addition to displaying errors in a window, **ErrorPopup** returns command output to the current command, instead of creating a new command.</span></span> <span data-ttu-id="da207-162">Lorsque vous exécutez cette commande, la `Show-Command` fenêtre s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="da207-162">When you run this command, the `Show-Command` window opens.</span></span> <span data-ttu-id="da207-163">Vous pouvez utiliser les fonctionnalités de la fenêtre pour définir les valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="da207-163">You can use the window features to set parameter values.</span></span> <span data-ttu-id="da207-164">Pour exécuter la commande, cliquez sur le bouton **exécuter** dans la `Show-Command` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="da207-164">To run the command, click the **Run** button in the `Show-Command` window.</span></span>

## <span data-ttu-id="da207-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="da207-165">PARAMETERS</span></span>

### <span data-ttu-id="da207-166">-ErrorPopup</span><span class="sxs-lookup"><span data-stu-id="da207-166">-ErrorPopup</span></span>

<span data-ttu-id="da207-167">Indique que l’applet de commande affiche les erreurs dans une fenêtre indépendante, en plus de les afficher sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="da207-167">Indicates that the cmdlet displays errors in a pop-up window, in addition to displaying them at the command line.</span></span> <span data-ttu-id="da207-168">Par défaut, lorsqu’une commande exécutée dans une `Show-Command` fenêtre génère une erreur, l’erreur s’affiche uniquement sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="da207-168">By default, when a command that is run in a `Show-Command` window generates an error, the error is displayed only at the command line.</span></span>

<span data-ttu-id="da207-169">En outre, lorsque vous exécutez la commande (à l’aide du bouton **exécuter** dans la `Show-Command` fenêtre), le paramètre **ErrorPopup** retourne les résultats de la commande à la commande actuelle, au lieu d’exécuter la commande et de retourner sa sortie à une nouvelle commande.</span><span class="sxs-lookup"><span data-stu-id="da207-169">Also, when you run the command (by using the **Run** button in the `Show-Command` window), the **ErrorPopup** parameter returns the command results to the current command, instead of running the command and returning its output to a new command.</span></span> <span data-ttu-id="da207-170">Vous pouvez utiliser cette fonctionnalité pour enregistrer les résultats de la commande dans une variable.</span><span class="sxs-lookup"><span data-stu-id="da207-170">You can use this feature to save the command results in a variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da207-171">-Hauteur</span><span class="sxs-lookup"><span data-stu-id="da207-171">-Height</span></span>

<span data-ttu-id="da207-172">Spécifie la hauteur de la `Show-Command` fenêtre en pixels.</span><span class="sxs-lookup"><span data-stu-id="da207-172">Specifies the height of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="da207-173">Entrez une valeur comprise entre 300 et le nombre de pixels de la résolution d'écran.</span><span class="sxs-lookup"><span data-stu-id="da207-173">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="da207-174">Si la valeur est trop grande pour afficher la fenêtre commande à l’écran, `Show-Command` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="da207-174">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="da207-175">La hauteur par défaut est de 600 pixels.</span><span class="sxs-lookup"><span data-stu-id="da207-175">The default height is 600 pixels.</span></span> <span data-ttu-id="da207-176">Pour une `Show-Command` commande qui comprend le paramètre **Name** , la hauteur par défaut est de 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="da207-176">For a `Show-Command` command that includes the **Name** parameter, the default height is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da207-177">-Name</span><span class="sxs-lookup"><span data-stu-id="da207-177">-Name</span></span>

<span data-ttu-id="da207-178">Affiche une fenêtre de commandes pour la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="da207-178">Displays a command window for the specified command.</span></span> <span data-ttu-id="da207-179">Entrez le nom d’une commande, par exemple le nom d’une applet de commande, d’une fonction ou d’une commande CIM.</span><span class="sxs-lookup"><span data-stu-id="da207-179">Enter the name of one command, such as the name of a cmdlet, function, or CIM command.</span></span> <span data-ttu-id="da207-180">Si vous omettez ce paramètre, `Show-Command` affiche une fenêtre de commande qui répertorie toutes les commandes PowerShell de tous les modules installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="da207-180">If you omit this parameter, `Show-Command` displays a command window that lists all of the PowerShell commands in all modules installed on the computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da207-181">-NoCommonParameter</span><span class="sxs-lookup"><span data-stu-id="da207-181">-NoCommonParameter</span></span>

<span data-ttu-id="da207-182">Indique que cette applet de commande omet la section paramètres communs de l’affichage de la commande.</span><span class="sxs-lookup"><span data-stu-id="da207-182">Indicates that this cmdlet omits the Common Parameters section of the command display.</span></span> <span data-ttu-id="da207-183">Par défaut, les paramètres communs apparaissent dans une section extensible en bas de la fenêtre de commandes.</span><span class="sxs-lookup"><span data-stu-id="da207-183">By default, the Common Parameters appear in an expandable section at the bottom of the command window.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da207-184">-PassThru</span><span class="sxs-lookup"><span data-stu-id="da207-184">-PassThru</span></span>

<span data-ttu-id="da207-185">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="da207-185">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="da207-186">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="da207-186">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="da207-187">Pour exécuter la chaîne de commande, copiez et collez-la à l’invite de commandes, ou enregistrez-la dans une variable et utilisez l' `Invoke-Expression` applet de commande pour exécuter la chaîne dans la variable.</span><span class="sxs-lookup"><span data-stu-id="da207-187">To run the command string, copy and paste it at the command prompt or save it in a variable and use the `Invoke-Expression` cmdlet to run the string in the variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da207-188">-Largeur</span><span class="sxs-lookup"><span data-stu-id="da207-188">-Width</span></span>

<span data-ttu-id="da207-189">Spécifie la largeur de la `Show-Command` fenêtre en pixels.</span><span class="sxs-lookup"><span data-stu-id="da207-189">Specifies the width of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="da207-190">Entrez une valeur comprise entre 300 et le nombre de pixels de la résolution d'écran.</span><span class="sxs-lookup"><span data-stu-id="da207-190">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="da207-191">Si la valeur est trop grande pour afficher la fenêtre commande à l’écran, `Show-Command` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="da207-191">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="da207-192">La largeur par défaut est de 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="da207-192">The default width is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da207-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="da207-193">CommonParameters</span></span>

<span data-ttu-id="da207-194">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="da207-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="da207-195">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="da207-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="da207-196">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="da207-196">INPUTS</span></span>

### <span data-ttu-id="da207-197">None</span><span class="sxs-lookup"><span data-stu-id="da207-197">None</span></span>

<span data-ttu-id="da207-198">Vous ne pouvez pas diriger d’entrée vers `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="da207-198">You cannot pipe input to `Show-Command`.</span></span>

## <span data-ttu-id="da207-199">SORTIES</span><span class="sxs-lookup"><span data-stu-id="da207-199">OUTPUTS</span></span>

### <span data-ttu-id="da207-200">None, System. String, System. Object</span><span class="sxs-lookup"><span data-stu-id="da207-200">None, System.String, System.Object</span></span>

<span data-ttu-id="da207-201">Quand vous utilisez le paramètre **PassThru** , `Show-Command` retourne une chaîne de commande.</span><span class="sxs-lookup"><span data-stu-id="da207-201">When you use the **PassThru** parameter, `Show-Command` returns a command string.</span></span> <span data-ttu-id="da207-202">Quand vous utilisez le paramètre **ErrorPopup** , `Show-Command` retourne la sortie de commande (n’importe quel objet).</span><span class="sxs-lookup"><span data-stu-id="da207-202">When you use the **ErrorPopup** parameter, `Show-Command` returns the command output (any object).</span></span> <span data-ttu-id="da207-203">Dans le cas contraire, `Show-Command` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="da207-203">Otherwise, `Show-Command` does not generate any output.</span></span>

## <span data-ttu-id="da207-204">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="da207-204">NOTES</span></span>

<span data-ttu-id="da207-205">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="da207-205">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="da207-206">`Show-Command` ne fonctionne pas dans les sessions à distance.</span><span class="sxs-lookup"><span data-stu-id="da207-206">`Show-Command` does not work in remote sessions.</span></span>

## <span data-ttu-id="da207-207">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="da207-207">RELATED LINKS</span></span>
