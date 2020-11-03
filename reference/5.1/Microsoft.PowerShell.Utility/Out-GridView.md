---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 473571aa73d9b9331545b80cb5949e7a83c26eff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203178"
---
# <span data-ttu-id="0f3c2-103">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="0f3c2-103">Out-GridView</span></span>

## <span data-ttu-id="0f3c2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0f3c2-104">SYNOPSIS</span></span>
<span data-ttu-id="0f3c2-105">Envoie la sortie vers un tableau interactif dans une fenêtre distincte.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-105">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="0f3c2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0f3c2-106">SYNTAX</span></span>

### <span data-ttu-id="0f3c2-107">PassThru (par défaut)</span><span class="sxs-lookup"><span data-stu-id="0f3c2-107">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="0f3c2-108">Wait</span><span class="sxs-lookup"><span data-stu-id="0f3c2-108">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="0f3c2-109">OutputMode</span><span class="sxs-lookup"><span data-stu-id="0f3c2-109">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="0f3c2-110">Description</span><span class="sxs-lookup"><span data-stu-id="0f3c2-110">DESCRIPTION</span></span>

<span data-ttu-id="0f3c2-111">L' `Out-GridView` applet de commande envoie la sortie d’une commande à une fenêtre d’affichage de grille dans laquelle la sortie est affichée dans un tableau interactif.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-111">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="0f3c2-112">Étant donné que cette applet de commande nécessite une interface utilisateur, elle ne fonctionne pas sur Windows Server Core ou Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-112">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="0f3c2-113">Vous pouvez utiliser les fonctionnalités suivantes du tableau pour examiner vos données :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-113">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="0f3c2-114">Masquer, afficher et réorganiser les colonnes</span><span class="sxs-lookup"><span data-stu-id="0f3c2-114">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="0f3c2-115">Trier les lignes</span><span class="sxs-lookup"><span data-stu-id="0f3c2-115">Sort rows</span></span>
- <span data-ttu-id="0f3c2-116">Filtre rapide</span><span class="sxs-lookup"><span data-stu-id="0f3c2-116">Quick Filter</span></span>
- <span data-ttu-id="0f3c2-117">Filtre ajouter des critères</span><span class="sxs-lookup"><span data-stu-id="0f3c2-117">Add Criteria Filter</span></span>
- <span data-ttu-id="0f3c2-118">Copier et coller</span><span class="sxs-lookup"><span data-stu-id="0f3c2-118">Copy and paste</span></span>

<span data-ttu-id="0f3c2-119">Pour obtenir des instructions complètes, consultez la section [Remarques](#notes) de cet article.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-119">For full instructions, see the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="0f3c2-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0f3c2-120">EXAMPLES</span></span>

### <span data-ttu-id="0f3c2-121">Exemple 1 : processus de sortie vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="0f3c2-121">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="0f3c2-122">Cet exemple obtient les processus en cours d’exécution sur l’ordinateur local et les envoie à une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-122">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="0f3c2-123">Exemple 2 : utiliser une variable pour sortir des processus dans un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="0f3c2-123">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="0f3c2-124">Cet exemple obtient également les processus en cours d’exécution sur l’ordinateur local et les envoie à une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-124">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="0f3c2-125">La sortie de l' `Get-Process` applet de commande est enregistrée dans la `$P` variable.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-125">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="0f3c2-126">Ensuite, `$P` est dirigé vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-126">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="0f3c2-127">Exemple 3 : afficher les propriétés sélectionnées dans un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="0f3c2-127">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="0f3c2-128">Cet exemple affiche les propriétés sélectionnées des processus en cours d’exécution dans un affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-128">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="0f3c2-129">La sortie de `Get-Process` est redirigée vers `Select-Object` pour sélectionner les propriétés **Name** , de la **plage** de **PeakWorkingSet** et de la propriété.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-129">The output of `Get-Process` is piped to `Select-Object` to select the **Name** , **WorkingSet** , and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="0f3c2-130">Un autre opérateur de pipeline envoie les objets filtrés à l' `Sort-Object` applet de commande pour les trier dans l’ordre décroissant selon la valeur de la propriété de la **plage** de recherche.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-130">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="0f3c2-131">Ensuite, les résultats triés sont dirigés vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-131">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="0f3c2-132">Vous pouvez maintenant utiliser les fonctionnalités de l'affichage de grille pour rechercher, trier ou filtrer les données.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-132">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="0f3c2-133">Exemple 4 : enregistrer la sortie dans une variable, puis générer une vue grille</span><span class="sxs-lookup"><span data-stu-id="0f3c2-133">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="0f3c2-134">Cet exemple enregistre la sortie de l’applet de commande dans une variable, puis l’envoie à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-134">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="0f3c2-135">`Get-ChildItem` Obtient tous les fichiers dans le répertoire d’installation de PowerShell et ses sous-répertoires à l’aide de la `$PSHOME` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-135">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="0f3c2-136">Les parenthèses de la commande établissent l'ordre des opérations.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-136">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="0f3c2-137">En conséquence, la sortie de la `Get-ChildItem` commande est enregistrée dans la `$A` variable avant d’être envoyée à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-137">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="0f3c2-138">Exemple 5 : processus de sortie pour un ordinateur spécifié vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="0f3c2-138">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="0f3c2-139">Cet exemple affiche les processus en cours d’exécution sur l’ordinateur SERVEUR01 dans une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-139">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="0f3c2-140">Exemple utilise `ogv` , qui est l’alias de l’applet de commande `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-140">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="0f3c2-141">Le paramètre **title** spécifie le titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-141">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="0f3c2-142">Exemple 6 : sortie des données des ordinateurs distants vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="0f3c2-142">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="0f3c2-143">Cet exemple montre comment envoyer des données collectées à partir d’ordinateurs distants vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-143">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="0f3c2-144">`Invoke-Command` s’exécute `Get-Culture` sur trois ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-144">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="0f3c2-145">Les données résultantes sont redirigées vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-145">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="0f3c2-146">Notez que le bloc de script qui s’exécute sur l’ordinateur distant n’inclut pas la `Out-GridView` commande.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-146">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="0f3c2-147">Si tel était le cas, la commande échouerait quand elle essaierait d'ouvrir une fenêtre d'affichage de grille sur chacun des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-147">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="0f3c2-148">Exemple 7 : passer plusieurs éléments à `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="0f3c2-148">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="0f3c2-149">Cet exemple vous permet de sélectionner plusieurs processus dans la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-149">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="0f3c2-150">Les processus que vous sélectionnez sont passés à la `Export-Csv` commande et écrits dans le `ProcessLog.csv` fichier.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-150">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="0f3c2-151">Le paramètre **PassThru** de `Out-GridView` vous permet d’envoyer plusieurs éléments vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-151">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="0f3c2-152">Le paramètre **PassThru** équivaut à l'utilisation de la valeur **Multiple** du paramètre **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-152">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="0f3c2-153">Exemple 8 : créer un raccourci Windows vers `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="0f3c2-153">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="0f3c2-154">Cet exemple montre comment utiliser le paramètre **Wait** de `Out-GridView` pour créer un raccourci Windows dans la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-154">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="0f3c2-155">Cette ligne de commande peut être utilisée dans un raccourci Windows.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-155">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="0f3c2-156">Sans le paramètre **Wait** , PowerShell s’arrête dès que la fenêtre s’est `Out-GridView` ouverte, ce qui ferme la `Out-GridView` fenêtre presque immédiatement.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-156">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="0f3c2-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0f3c2-157">PARAMETERS</span></span>

### <span data-ttu-id="0f3c2-158">-InputObject</span><span class="sxs-lookup"><span data-stu-id="0f3c2-158">-InputObject</span></span>

<span data-ttu-id="0f3c2-159">Spécifie l’objet que l’applet de commande accepte comme entrée pour `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-159">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="0f3c2-160">Quand vous utilisez le paramètre **InputObject** pour envoyer une collection d’objets à `Out-GridView` , `Out-GridView` traite la collection comme un objet de collection et affiche une ligne qui représente la collection.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-160">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="0f3c2-161">Pour afficher chaque objet de la collection, utilisez un opérateur de pipeline (|) pour envoyer des objets à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-161">To display the each object in the collection, use a pipeline operator (|) to send objects to `Out-GridView`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0f3c2-162">-Du outputmode</span><span class="sxs-lookup"><span data-stu-id="0f3c2-162">-OutputMode</span></span>

<span data-ttu-id="0f3c2-163">Spécifie les éléments que la fenêtre interactive envoie au pipeline en tant qu’entrée d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-163">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="0f3c2-164">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-164">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="0f3c2-165">Pour envoyer des éléments depuis la fenêtre interactive dans le pipeline, cliquez pour sélectionner les éléments, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-165">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="0f3c2-166">Les valeurs de ce paramètre déterminent le nombre d'éléments que vous pouvez envoyer dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-166">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="0f3c2-167">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-167">None.</span></span>  <span data-ttu-id="0f3c2-168">aucun élément.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-168">No items.</span></span> <span data-ttu-id="0f3c2-169">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-169">This is the default value.</span></span>
- <span data-ttu-id="0f3c2-170">Unique.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-170">Single.</span></span> <span data-ttu-id="0f3c2-171">zéro ou un élément.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-171">Zero items or one item.</span></span> <span data-ttu-id="0f3c2-172">Utilisez cette valeur lorsque la commande suivante ne peut prendre qu'un seul objet en entrée.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-172">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="0f3c2-173">Plusieurs.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-173">Multiple.</span></span> <span data-ttu-id="0f3c2-174">zéro, un ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-174">Zero, one, or many items.</span></span> <span data-ttu-id="0f3c2-175">Utilisez cette valeur lorsque la commande suivante peut prendre plusieurs objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-175">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="0f3c2-176">Cette valeur est équivalente au paramètre **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-176">This value is equivalent to the **Passthru** parameter.</span></span>

<span data-ttu-id="0f3c2-177">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-177">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f3c2-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0f3c2-178">-PassThru</span></span>

<span data-ttu-id="0f3c2-179">Indique que l’applet de commande envoie les éléments à partir de la fenêtre interactive dans le pipeline en tant qu’entrée d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-179">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="0f3c2-180">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-180">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="0f3c2-181">Ce paramètre est équivalent à l'utilisation de la valeur **Multiple** du paramètre **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-181">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="0f3c2-182">Pour envoyer des éléments depuis la fenêtre interactive dans le pipeline, cliquez pour sélectionner les éléments, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-182">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="0f3c2-183">MAJ+clic et Ctrl+clic sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-183">Shift-click and Ctrl-click are supported.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f3c2-184">-Title</span><span class="sxs-lookup"><span data-stu-id="0f3c2-184">-Title</span></span>

<span data-ttu-id="0f3c2-185">Spécifie le texte qui apparaît dans la barre de titre de la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-185">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="0f3c2-186">Par défaut, la barre de titre affiche la commande qui appelle `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-186">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f3c2-187">-Wait</span><span class="sxs-lookup"><span data-stu-id="0f3c2-187">-Wait</span></span>

<span data-ttu-id="0f3c2-188">Indique que l’applet de commande supprime l’invite de commandes et empêche Windows PowerShell de se fermer jusqu’à la fermeture de la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-188">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="0f3c2-189">Par défaut, l’invite de commandes retourne quand la `Out-GridView` fenêtre s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-189">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="0f3c2-190">Cette fonctionnalité vous permet d’utiliser les `Out-GridView` applets de commande dans les raccourcis Windows.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-190">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="0f3c2-191">Quand `Out-GridView` est utilisé dans un raccourci sans le paramètre **Wait** , la `Out-GridView` fenêtre s’affiche uniquement momentanément avant la fermeture de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-191">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f3c2-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0f3c2-192">CommonParameters</span></span>

<span data-ttu-id="0f3c2-193">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0f3c2-194">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0f3c2-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0f3c2-195">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0f3c2-195">INPUTS</span></span>

### <span data-ttu-id="0f3c2-196">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="0f3c2-196">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="0f3c2-197">Vous pouvez envoyer n’importe quel objet à cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-197">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="0f3c2-198">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0f3c2-198">OUTPUTS</span></span>

### <span data-ttu-id="0f3c2-199">Aucun</span><span class="sxs-lookup"><span data-stu-id="0f3c2-199">None</span></span>

<span data-ttu-id="0f3c2-200">Normalement, `Out-GridView` ne retourne pas d’objets.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-200">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="0f3c2-201">Lors de l’utilisation du paramètre **PassThru** , les objets représentant les lignes sélectionnées sont retournés au pipeline.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-201">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="0f3c2-202">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0f3c2-202">NOTES</span></span>

<span data-ttu-id="0f3c2-203">Vous ne pouvez pas utiliser une commande distante pour ouvrir une fenêtre d'affichage de grille sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-203">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="0f3c2-204">La sortie de commande que vous envoyez à `Out-GridView` ne peut pas être mise en forme à l’aide des `Format` applets de commande, telles que `Format-Table` ou `Format-Wide` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-204">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="0f3c2-205">Pour sélectionner des propriétés, utilisez l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-205">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="0f3c2-206">La sortie désérialisée à partir des commandes distantes ne peut pas être correctement mise en forme dans la fenêtre d'affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-206">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="0f3c2-207">**Raccourcis clavier pour**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="0f3c2-207">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="0f3c2-208">Utilisez cette clé :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-208">Use this key:</span></span>              |                                   <span data-ttu-id="0f3c2-209">Pour exécuter cette action :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-209">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="0f3c2-210"><kbd>Onglet</kbd></span><span class="sxs-lookup"><span data-stu-id="0f3c2-210"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="0f3c2-211">Déplace le curseur de la zone **filtre** vers le menu **Ajouter des critères** vers la table et inversement.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-211">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="0f3c2-212"><kbd>Haut</kbd></span><span class="sxs-lookup"><span data-stu-id="0f3c2-212"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="0f3c2-213">Remonter d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-213">Move up one row.</span></span> <span data-ttu-id="0f3c2-214">Se déplace vers les en-têtes de colonne à partir de la première ligne de données.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-214">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="0f3c2-215"><kbd>Flèche</kbd></span><span class="sxs-lookup"><span data-stu-id="0f3c2-215"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="0f3c2-216">Descendre d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-216">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="0f3c2-217"><kbd>Flèche gauche</kbd></span><span class="sxs-lookup"><span data-stu-id="0f3c2-217"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="0f3c2-218">Dans ligne d’en-tête de colonne, déplacer d’une colonne vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-218">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="0f3c2-219"><kbd>Flèche droite</kbd></span><span class="sxs-lookup"><span data-stu-id="0f3c2-219"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="0f3c2-220">Dans ligne d’en-tête de colonne, déplacer vers la droite d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-220">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="0f3c2-221"><kbd>ContextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="0f3c2-221"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="0f3c2-222">Dans ligne d’en-tête de colonne, affiche l’option Sélectionner les colonnes.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-222">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="0f3c2-223"><kbd>Entrée</kbd> ou <kbd>barre d’espace</kbd></span><span class="sxs-lookup"><span data-stu-id="0f3c2-223"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="0f3c2-224">Dans la ligne d’en-tête de colonne, triez les données de la colonne (basculez A-Z, Z-A).</span><span class="sxs-lookup"><span data-stu-id="0f3c2-224">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="0f3c2-225">**Comment utiliser les fonctionnalités de la fenêtre d’affichage de grille**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-225">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="0f3c2-226">**Pour masquer ou afficher une colonne :**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-226">**To hide or show a column:**</span></span>

1. <span data-ttu-id="0f3c2-227">Cliquez avec le bouton droit sur un en-tête de colonne et cliquez sur **Sélectionner les colonnes** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-227">Right-click any column header and click **Select Columns** .</span></span>
2. <span data-ttu-id="0f3c2-228">Dans la boîte de dialogue **Sélectionner les colonnes** , utilisez les touches de direction pour déplacer les colonnes entre les colonnes sélectionnées dans les zones colonnes disponibles.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-228">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="0f3c2-229">Seules les colonnes de la zone **Sélectionner les colonnes** s’affichent dans la fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-229">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="0f3c2-230">**Pour réorganiser les colonnes :**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-230">**To reorder columns:**</span></span>

<span data-ttu-id="0f3c2-231">Vous pouvez faire glisser et déposer des colonnes à l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-231">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="0f3c2-232">Ou procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-232">Or use the following steps:</span></span>

1. <span data-ttu-id="0f3c2-233">Cliquez avec le bouton droit sur un en-tête de colonne et cliquez sur **Sélectionner les colonnes** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-233">Right-click any column header and click **Select Columns** .</span></span>
2. <span data-ttu-id="0f3c2-234">Dans la boîte de dialogue **Sélectionner les colonnes** , utilisez les boutons **monter** **et descendre pour** réorganiser les colonnes.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-234">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="0f3c2-235">Les colonnes en haut de la liste apparaissent à gauche des colonnes au bas de la liste dans la fenêtre d'affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-235">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="0f3c2-236">**Comment trier les données de tableau**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-236">**How to Sort Table Data**</span></span>

- <span data-ttu-id="0f3c2-237">Pour trier les données, cliquez sur un en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-237">To sort the data, click a column header.</span></span>
- <span data-ttu-id="0f3c2-238">Pour modifier l’ordre de tri, cliquez de nouveau sur l’en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-238">To change the sort order, click the column header again.</span></span> <span data-ttu-id="0f3c2-239">Chaque fois que vous cliquez sur le même en-tête, l'ordre de tri bascule de croissant à décroissant (ou inversement).</span><span class="sxs-lookup"><span data-stu-id="0f3c2-239">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="0f3c2-240">L'ordre actif est indiqué par un triangle dans l'en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-240">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="0f3c2-241">**Comment sélectionner les données de tableau**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-241">**How to Select Table Data**</span></span>

- <span data-ttu-id="0f3c2-242">Pour sélectionner une ligne, sélectionnez la ligne ou utilisez la flèche haut ou bas pour accéder à la ligne.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-242">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="0f3c2-243">Pour sélectionner toutes les lignes (à l’exception de la ligne d’en-tête), appuyez sur <kbd>CTRL</kbd> + <kbd>A</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-243">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="0f3c2-244">Pour sélectionner des lignes consécutives, maintenez la touche <kbd>MAJ</kbd> enfoncée tout en cliquant sur les lignes ou en utilisant les touches de direction.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-244">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="0f3c2-245">Pour sélectionner des lignes non consécutives, appuyez sur la touche <kbd>CTRL</kbd> et cliquez pour ajouter une ligne à la sélection.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-245">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="0f3c2-246">Vous ne pouvez pas sélectionner des colonnes et vous ne pouvez pas sélectionner la ligne d'en-tête d'une colonne entière.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-246">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="0f3c2-247">**Comment copier des lignes**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-247">**How to Copy Rows**</span></span>

- <span data-ttu-id="0f3c2-248">Pour copier une ou plusieurs lignes de la table, sélectionnez les lignes, puis appuyez sur CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-248">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="0f3c2-249">Vous pouvez coller les données dans n'importe quel tableur ou traitement de texte.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-249">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="0f3c2-250">Vous ne pouvez pas copier des colonnes ou des parties de ligne et vous ne pouvez pas copier la ligne d'en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-250">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="0f3c2-251">**Comment effectuer une recherche dans le tableau (filtre rapide)**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-251">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="0f3c2-252">Utilisez la zone de filtre pour rechercher des données dans la table.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-252">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="0f3c2-253">Lorsque vous entrez une valeur dans la zone, seuls les éléments qui incluent le texte entré apparaissent dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-253">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="0f3c2-254">Recherchez du texte.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-254">Search for text.</span></span> <span data-ttu-id="0f3c2-255">Pour rechercher du texte dans le tableau, dans la zone de filtre, tapez le texte à rechercher.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-255">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="0f3c2-256">Rechercher plusieurs mots.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-256">Search for multiple words.</span></span> <span data-ttu-id="0f3c2-257">Pour rechercher plusieurs mots dans le tableau, tapez les mots séparés par un espace.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-257">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="0f3c2-258">`Out-GridView` affiche les lignes qui incluent tous les mots (AND logique).</span><span class="sxs-lookup"><span data-stu-id="0f3c2-258">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="0f3c2-259">Recherchez des expressions littérales.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-259">Search for literal phrases.</span></span> <span data-ttu-id="0f3c2-260">Pour rechercher une expression qui comporte des espaces ou des caractères spéciaux, placez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-260">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="0f3c2-261">`Out-GridView` affiche les lignes qui incluent une correspondance exacte pour l’expression.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-261">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="0f3c2-262">Rechercher dans les colonnes.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-262">Search in columns.</span></span> <span data-ttu-id="0f3c2-263">Pour rechercher un texte dans une ou plusieurs colonnes, utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-263">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="0f3c2-264">Par exemple, pour rechercher « net » dans la colonne **DisplayName** , dans la zone de **filtre** , tapez :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-264">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="0f3c2-265">Pour rechercher des lignes avec « net » dans les colonnes **DisplayName** et **Name** , dans la zone de **filtre** , tapez :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-265">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="0f3c2-266">Désactiver la recherche.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-266">Turn off search.</span></span> <span data-ttu-id="0f3c2-267">Pour afficher à nouveau la totalité du tableau, cliquez sur le bouton X rouge dans le coin supérieur droit de la zone de **filtre** ou supprimez le texte de la zone de **filtre** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-267">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="0f3c2-268">**Utiliser des critères pour filtrer le tableau**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-268">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="0f3c2-269">Vous pouvez utiliser des règles ou des critères pour déterminer les éléments qui sont affichés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-269">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="0f3c2-270">Les éléments s’affichent uniquement lorsqu’ils répondent à tous les critères que vous établissez.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-270">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="0f3c2-271">Les critères disponibles sont déterminés par les propriétés des objets affichés dans la fenêtre d'affichage de grille et les types .NET Framework de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-271">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="0f3c2-272">Chaque critère a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-272">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="0f3c2-273">Les critères des différentes propriétés sont connectés par **et** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-273">Criteria for different properties are connected by **AND** .</span></span> <span data-ttu-id="0f3c2-274">Les critères de la même propriété sont connectés par **ou** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-274">Criteria for the same property are connected by **OR** .</span></span> <span data-ttu-id="0f3c2-275">Vous ne pouvez pas modifier les connecteurs logiques.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-275">You cannot change the logical connectors.</span></span>

<span data-ttu-id="0f3c2-276">Les critères affectent uniquement l'affichage.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-276">The criteria only affects the display.</span></span> <span data-ttu-id="0f3c2-277">Ils ne suppriment pas des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-277">It does not delete items from the table.</span></span>

<span data-ttu-id="0f3c2-278">**Comment ajouter des critères**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-278">**How to Add Criteria**</span></span>

1. <span data-ttu-id="0f3c2-279">Pour afficher le bouton de menu **Ajouter des critères** , dans le coin supérieur droit de la fenêtre, cliquez sur la flèche de développement.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-279">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="0f3c2-280">Cliquez sur le bouton de menu **Ajouter des critères** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-280">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="0f3c2-281">Cliquez pour sélectionner les colonnes (propriétés).</span><span class="sxs-lookup"><span data-stu-id="0f3c2-281">Click to select columns (properties).</span></span> <span data-ttu-id="0f3c2-282">Vous pouvez sélectionner une ou plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-282">You can select one or many properties.</span></span>
4. <span data-ttu-id="0f3c2-283">Lorsque vous avez fini de sélectionner les propriétés, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-283">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="0f3c2-284">Pour annuler les ajouts, cliquez sur **Annuler** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-284">To cancel the additions, click **Cancel** .</span></span>
6. <span data-ttu-id="0f3c2-285">Pour ajouter d’autres critères, cliquez de nouveau sur le bouton **Ajouter des critères** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-285">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="0f3c2-286">**Comment modifier un critère**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-286">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="0f3c2-287">Pour modifier un opérateur, cliquez sur la valeur de l’opérateur bleu, puis sélectionnez un autre opérateur dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-287">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="0f3c2-288">Pour entrer ou modifier une valeur, tapez une valeur dans la zone valeur.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-288">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="0f3c2-289">Si vous entrez une valeur qui n'est pas valide, une icône en forme de X s'affiche.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-289">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="0f3c2-290">Pour supprimer la valeur, modifiez-la.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-290">To remove it, change the value.</span></span>
- <span data-ttu-id="0f3c2-291">Pour créer une instruction **ou** , ajoutez un critère avec la même propriété.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-291">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="0f3c2-292">**Comment supprimer des critères**</span><span class="sxs-lookup"><span data-stu-id="0f3c2-292">**How to Delete Criteria**</span></span>

- <span data-ttu-id="0f3c2-293">Pour supprimer les critères sélectionnés, cliquez sur la Croix Rouge en regard de chaque critère.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-293">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="0f3c2-294">Pour supprimer tous les critères, cliquez sur le bouton **Effacer tout** .</span><span class="sxs-lookup"><span data-stu-id="0f3c2-294">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="0f3c2-295">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0f3c2-295">RELATED LINKS</span></span>

[<span data-ttu-id="0f3c2-296">Out-File</span><span class="sxs-lookup"><span data-stu-id="0f3c2-296">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="0f3c2-297">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="0f3c2-297">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="0f3c2-298">Out-String</span><span class="sxs-lookup"><span data-stu-id="0f3c2-298">Out-String</span></span>](Out-String.md)
