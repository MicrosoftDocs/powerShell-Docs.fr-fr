---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 840aa38ff17ceaf7dc65ca838da020c3d8c27952
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344386"
---
# <span data-ttu-id="d04e3-103">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="d04e3-103">Out-GridView</span></span>

## <span data-ttu-id="d04e3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d04e3-104">SYNOPSIS</span></span>
<span data-ttu-id="d04e3-105">Envoie la sortie vers un tableau interactif dans une fenêtre distincte.</span><span class="sxs-lookup"><span data-stu-id="d04e3-105">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="d04e3-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d04e3-106">SYNTAX</span></span>

### <span data-ttu-id="d04e3-107">PassThru (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d04e3-107">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="d04e3-108">Wait</span><span class="sxs-lookup"><span data-stu-id="d04e3-108">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="d04e3-109">OutputMode</span><span class="sxs-lookup"><span data-stu-id="d04e3-109">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="d04e3-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d04e3-110">DESCRIPTION</span></span>

<span data-ttu-id="d04e3-111">L' `Out-GridView` applet de commande envoie la sortie d’une commande à une fenêtre d’affichage de grille dans laquelle la sortie est affichée dans un tableau interactif.</span><span class="sxs-lookup"><span data-stu-id="d04e3-111">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="d04e3-112">Étant donné que cette applet de commande nécessite une interface utilisateur, elle ne fonctionne pas sur Windows Server Core ou Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="d04e3-112">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="d04e3-113">Vous pouvez utiliser les fonctionnalités suivantes du tableau pour examiner vos données :</span><span class="sxs-lookup"><span data-stu-id="d04e3-113">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="d04e3-114">Masquer, afficher et réorganiser les colonnes</span><span class="sxs-lookup"><span data-stu-id="d04e3-114">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="d04e3-115">Trier les lignes</span><span class="sxs-lookup"><span data-stu-id="d04e3-115">Sort rows</span></span>
- <span data-ttu-id="d04e3-116">Filtre rapide</span><span class="sxs-lookup"><span data-stu-id="d04e3-116">Quick Filter</span></span>
- <span data-ttu-id="d04e3-117">Filtre ajouter des critères</span><span class="sxs-lookup"><span data-stu-id="d04e3-117">Add Criteria Filter</span></span>
- <span data-ttu-id="d04e3-118">Copier et coller</span><span class="sxs-lookup"><span data-stu-id="d04e3-118">Copy and paste</span></span>

<span data-ttu-id="d04e3-119">Pour obtenir des instructions complètes, consultez la section [Remarques](#notes) de cet article.</span><span class="sxs-lookup"><span data-stu-id="d04e3-119">For full instructions, see the [Notes](#notes) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="d04e3-120">Cette applet de commande a été réintroduite dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="d04e3-120">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="d04e3-121">Cette applet de commande est uniquement disponible sur les systèmes Windows qui prennent en charge le bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="d04e3-121">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span> <span data-ttu-id="d04e3-122">Pour une version multiplateforme de cette applet de commande, consultez le module [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) dans le PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d04e3-122">For a cross-platform version of this cmdlet, see the [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) module in the PowerShell Gallery.</span></span>

## <span data-ttu-id="d04e3-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d04e3-123">EXAMPLES</span></span>

### <span data-ttu-id="d04e3-124">Exemple 1 : processus de sortie vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="d04e3-124">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="d04e3-125">Cet exemple obtient les processus en cours d’exécution sur l’ordinateur local et les envoie à une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="d04e3-125">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="d04e3-126">Exemple 2 : utiliser une variable pour sortir des processus dans un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="d04e3-126">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="d04e3-127">Cet exemple obtient également les processus en cours d’exécution sur l’ordinateur local et les envoie à une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="d04e3-127">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="d04e3-128">La sortie de l' `Get-Process` applet de commande est enregistrée dans la `$P` variable.</span><span class="sxs-lookup"><span data-stu-id="d04e3-128">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="d04e3-129">Ensuite, `$P` est dirigé vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-129">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="d04e3-130">Exemple 3 : afficher les propriétés sélectionnées dans un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="d04e3-130">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="d04e3-131">Cet exemple affiche les propriétés sélectionnées des processus en cours d’exécution dans un affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="d04e3-131">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="d04e3-132">La sortie de `Get-Process` est redirigée vers `Select-Object` pour sélectionner les propriétés **Name** , de la **plage** de **PeakWorkingSet** et de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d04e3-132">The output of `Get-Process` is piped to `Select-Object` to select the **Name** , **WorkingSet** , and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="d04e3-133">Un autre opérateur de pipeline envoie les objets filtrés à l' `Sort-Object` applet de commande pour les trier dans l’ordre décroissant selon la valeur de la propriété de la **plage** de recherche.</span><span class="sxs-lookup"><span data-stu-id="d04e3-133">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="d04e3-134">Ensuite, les résultats triés sont dirigés vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-134">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="d04e3-135">Vous pouvez maintenant utiliser les fonctionnalités de l'affichage de grille pour rechercher, trier ou filtrer les données.</span><span class="sxs-lookup"><span data-stu-id="d04e3-135">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="d04e3-136">Exemple 4 : enregistrer la sortie dans une variable, puis générer une vue grille</span><span class="sxs-lookup"><span data-stu-id="d04e3-136">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="d04e3-137">Cet exemple enregistre la sortie de l’applet de commande dans une variable, puis l’envoie à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-137">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="d04e3-138">`Get-ChildItem` Obtient tous les fichiers dans le répertoire d’installation de PowerShell et ses sous-répertoires à l’aide de la `$PSHOME` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="d04e3-138">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="d04e3-139">Les parenthèses de la commande établissent l'ordre des opérations.</span><span class="sxs-lookup"><span data-stu-id="d04e3-139">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="d04e3-140">En conséquence, la sortie de la `Get-ChildItem` commande est enregistrée dans la `$A` variable avant d’être envoyée à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-140">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="d04e3-141">Exemple 5 : processus de sortie pour un ordinateur spécifié vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="d04e3-141">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="d04e3-142">Cet exemple affiche les processus en cours d’exécution sur l’ordinateur SERVEUR01 dans une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="d04e3-142">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="d04e3-143">Exemple utilise `ogv` , qui est l’alias de l’applet de commande `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-143">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="d04e3-144">Le paramètre **title** spécifie le titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d04e3-144">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="d04e3-145">Exemple 6 : sortie des données des ordinateurs distants vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="d04e3-145">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="d04e3-146">Cet exemple montre comment envoyer des données collectées à partir d’ordinateurs distants vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-146">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="d04e3-147">`Invoke-Command` s’exécute `Get-Culture` sur trois ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="d04e3-147">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="d04e3-148">Les données résultantes sont redirigées vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-148">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="d04e3-149">Notez que le bloc de script qui s’exécute sur l’ordinateur distant n’inclut pas la `Out-GridView` commande.</span><span class="sxs-lookup"><span data-stu-id="d04e3-149">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="d04e3-150">Si tel était le cas, la commande échouerait quand elle essaierait d'ouvrir une fenêtre d'affichage de grille sur chacun des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="d04e3-150">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="d04e3-151">Exemple 7 : passer plusieurs éléments à `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="d04e3-151">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="d04e3-152">Cet exemple vous permet de sélectionner plusieurs processus dans la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d04e3-152">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="d04e3-153">Les processus que vous sélectionnez sont passés à la `Export-Csv` commande et écrits dans le `ProcessLog.csv` fichier.</span><span class="sxs-lookup"><span data-stu-id="d04e3-153">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="d04e3-154">Le paramètre **PassThru** de `Out-GridView` vous permet d’envoyer plusieurs éléments vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="d04e3-154">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="d04e3-155">Le paramètre **PassThru** équivaut à l'utilisation de la valeur **Multiple** du paramètre **OutputMode**.</span><span class="sxs-lookup"><span data-stu-id="d04e3-155">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="d04e3-156">Exemple 8 : créer un raccourci Windows vers `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="d04e3-156">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="d04e3-157">Cet exemple montre comment utiliser le paramètre **Wait** de `Out-GridView` pour créer un raccourci Windows dans la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d04e3-157">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="d04e3-158">Cette ligne de commande peut être utilisée dans un raccourci Windows.</span><span class="sxs-lookup"><span data-stu-id="d04e3-158">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="d04e3-159">Sans le paramètre **Wait** , PowerShell s’arrête dès que la fenêtre s’est `Out-GridView` ouverte, ce qui ferme la `Out-GridView` fenêtre presque immédiatement.</span><span class="sxs-lookup"><span data-stu-id="d04e3-159">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="d04e3-160">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="d04e3-160">PARAMETERS</span></span>

### <span data-ttu-id="d04e3-161">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d04e3-161">-InputObject</span></span>

<span data-ttu-id="d04e3-162">Spécifie l’objet que l’applet de commande accepte comme entrée pour `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-162">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="d04e3-163">Quand vous utilisez le paramètre **InputObject** pour envoyer une collection d’objets à `Out-GridView` , `Out-GridView` traite la collection comme un objet de collection et affiche une ligne qui représente la collection.</span><span class="sxs-lookup"><span data-stu-id="d04e3-163">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="d04e3-164">Pour afficher chaque objet de la collection, utilisez un opérateur de pipeline ( `|` ) pour envoyer des objets à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-164">To display the each object in the collection, use a pipeline operator (`|`) to send objects to `Out-GridView`.</span></span>

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

### <span data-ttu-id="d04e3-165">-Du outputmode</span><span class="sxs-lookup"><span data-stu-id="d04e3-165">-OutputMode</span></span>

<span data-ttu-id="d04e3-166">Spécifie les éléments que la fenêtre interactive envoie au pipeline en tant qu’entrée d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="d04e3-166">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="d04e3-167">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="d04e3-167">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="d04e3-168">Pour envoyer des éléments depuis la fenêtre interactive dans le pipeline, cliquez pour sélectionner les éléments, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="d04e3-168">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="d04e3-169">Les valeurs de ce paramètre déterminent le nombre d'éléments que vous pouvez envoyer dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d04e3-169">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="d04e3-170">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d04e3-170">None.</span></span>  <span data-ttu-id="d04e3-171">aucun élément.</span><span class="sxs-lookup"><span data-stu-id="d04e3-171">No items.</span></span> <span data-ttu-id="d04e3-172">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d04e3-172">This is the default value.</span></span>
- <span data-ttu-id="d04e3-173">Unique.</span><span class="sxs-lookup"><span data-stu-id="d04e3-173">Single.</span></span> <span data-ttu-id="d04e3-174">zéro ou un élément.</span><span class="sxs-lookup"><span data-stu-id="d04e3-174">Zero items or one item.</span></span> <span data-ttu-id="d04e3-175">Utilisez cette valeur lorsque la commande suivante ne peut prendre qu'un seul objet en entrée.</span><span class="sxs-lookup"><span data-stu-id="d04e3-175">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="d04e3-176">Plusieurs.</span><span class="sxs-lookup"><span data-stu-id="d04e3-176">Multiple.</span></span> <span data-ttu-id="d04e3-177">zéro, un ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="d04e3-177">Zero, one, or many items.</span></span> <span data-ttu-id="d04e3-178">Utilisez cette valeur lorsque la commande suivante peut prendre plusieurs objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="d04e3-178">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="d04e3-179">Cette valeur est équivalente au paramètre **Passthru**.</span><span class="sxs-lookup"><span data-stu-id="d04e3-179">This value is equivalent to the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="d04e3-180">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d04e3-180">-PassThru</span></span>

<span data-ttu-id="d04e3-181">Indique que l’applet de commande envoie les éléments à partir de la fenêtre interactive dans le pipeline en tant qu’entrée d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="d04e3-181">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="d04e3-182">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="d04e3-182">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="d04e3-183">Ce paramètre est équivalent à l'utilisation de la valeur **Multiple** du paramètre **OutputMode**.</span><span class="sxs-lookup"><span data-stu-id="d04e3-183">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="d04e3-184">Pour envoyer des éléments depuis la fenêtre interactive dans le pipeline, cliquez pour sélectionner les éléments, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="d04e3-184">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="d04e3-185">MAJ+clic et Ctrl+clic sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d04e3-185">Shift-click and Ctrl-click are supported.</span></span>

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

### <span data-ttu-id="d04e3-186">-Title</span><span class="sxs-lookup"><span data-stu-id="d04e3-186">-Title</span></span>

<span data-ttu-id="d04e3-187">Spécifie le texte qui apparaît dans la barre de titre de la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d04e3-187">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="d04e3-188">Par défaut, la barre de titre affiche la commande qui appelle `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-188">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

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

### <span data-ttu-id="d04e3-189">-Wait</span><span class="sxs-lookup"><span data-stu-id="d04e3-189">-Wait</span></span>

<span data-ttu-id="d04e3-190">Indique que l’applet de commande supprime l’invite de commandes et empêche Windows PowerShell de se fermer jusqu’à la fermeture de la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d04e3-190">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="d04e3-191">Par défaut, l’invite de commandes retourne quand la `Out-GridView` fenêtre s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="d04e3-191">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="d04e3-192">Cette fonctionnalité vous permet d’utiliser les `Out-GridView` applets de commande dans les raccourcis Windows.</span><span class="sxs-lookup"><span data-stu-id="d04e3-192">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="d04e3-193">Quand `Out-GridView` est utilisé dans un raccourci sans le paramètre **Wait** , la `Out-GridView` fenêtre s’affiche uniquement momentanément avant la fermeture de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d04e3-193">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

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

### <span data-ttu-id="d04e3-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d04e3-194">CommonParameters</span></span>

<span data-ttu-id="d04e3-195">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d04e3-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d04e3-196">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d04e3-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d04e3-197">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d04e3-197">INPUTS</span></span>

### <span data-ttu-id="d04e3-198">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="d04e3-198">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="d04e3-199">Vous pouvez envoyer n’importe quel objet à cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d04e3-199">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="d04e3-200">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d04e3-200">OUTPUTS</span></span>

### <span data-ttu-id="d04e3-201">Aucun</span><span class="sxs-lookup"><span data-stu-id="d04e3-201">None</span></span>

<span data-ttu-id="d04e3-202">Normalement, `Out-GridView` ne retourne pas d’objets.</span><span class="sxs-lookup"><span data-stu-id="d04e3-202">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="d04e3-203">Lors de l’utilisation du paramètre **PassThru** , les objets représentant les lignes sélectionnées sont retournés au pipeline.</span><span class="sxs-lookup"><span data-stu-id="d04e3-203">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="d04e3-204">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d04e3-204">NOTES</span></span>

<span data-ttu-id="d04e3-205">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="d04e3-205">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="d04e3-206">Vous ne pouvez pas utiliser une commande distante pour ouvrir une fenêtre d'affichage de grille sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d04e3-206">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="d04e3-207">La sortie de commande que vous envoyez à `Out-GridView` ne peut pas être mise en forme à l’aide des `Format` applets de commande, telles que `Format-Table` ou `Format-Wide` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d04e3-207">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="d04e3-208">Pour sélectionner des propriétés, utilisez l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="d04e3-208">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="d04e3-209">La sortie désérialisée à partir des commandes distantes ne peut pas être correctement mise en forme dans la fenêtre d'affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="d04e3-209">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="d04e3-210">**Raccourcis clavier pour**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="d04e3-210">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="d04e3-211">Utilisez cette clé :</span><span class="sxs-lookup"><span data-stu-id="d04e3-211">Use this key:</span></span>              |                                   <span data-ttu-id="d04e3-212">Pour exécuter cette action :</span><span class="sxs-lookup"><span data-stu-id="d04e3-212">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="d04e3-213"><kbd>Onglet</kbd></span><span class="sxs-lookup"><span data-stu-id="d04e3-213"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="d04e3-214">Déplace le curseur de la zone **filtre** vers le menu **Ajouter des critères** vers la table et inversement.</span><span class="sxs-lookup"><span data-stu-id="d04e3-214">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="d04e3-215"><kbd>Haut</kbd></span><span class="sxs-lookup"><span data-stu-id="d04e3-215"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="d04e3-216">Remonter d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="d04e3-216">Move up one row.</span></span> <span data-ttu-id="d04e3-217">Se déplace vers les en-têtes de colonne à partir de la première ligne de données.</span><span class="sxs-lookup"><span data-stu-id="d04e3-217">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="d04e3-218"><kbd>Flèche</kbd></span><span class="sxs-lookup"><span data-stu-id="d04e3-218"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="d04e3-219">Descendre d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="d04e3-219">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="d04e3-220"><kbd>Flèche gauche</kbd></span><span class="sxs-lookup"><span data-stu-id="d04e3-220"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="d04e3-221">Dans ligne d’en-tête de colonne, déplacer d’une colonne vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="d04e3-221">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="d04e3-222"><kbd>Flèche droite</kbd></span><span class="sxs-lookup"><span data-stu-id="d04e3-222"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="d04e3-223">Dans ligne d’en-tête de colonne, déplacer vers la droite d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="d04e3-223">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="d04e3-224"><kbd>ContextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="d04e3-224"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="d04e3-225">Dans ligne d’en-tête de colonne, affiche l’option Sélectionner les colonnes.</span><span class="sxs-lookup"><span data-stu-id="d04e3-225">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="d04e3-226"><kbd>Entrée</kbd> ou <kbd>barre d’espace</kbd></span><span class="sxs-lookup"><span data-stu-id="d04e3-226"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="d04e3-227">Dans la ligne d’en-tête de colonne, triez les données de la colonne (basculez A-Z, Z-A).</span><span class="sxs-lookup"><span data-stu-id="d04e3-227">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="d04e3-228">**Comment utiliser les fonctionnalités de la fenêtre d’affichage de grille**</span><span class="sxs-lookup"><span data-stu-id="d04e3-228">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="d04e3-229">**Pour masquer ou afficher une colonne :**</span><span class="sxs-lookup"><span data-stu-id="d04e3-229">**To hide or show a column:**</span></span>

1. <span data-ttu-id="d04e3-230">Cliquez avec le bouton droit sur un en-tête de colonne et cliquez sur **Sélectionner les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="d04e3-230">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="d04e3-231">Dans la boîte de dialogue **Sélectionner les colonnes** , utilisez les touches de direction pour déplacer les colonnes entre les colonnes sélectionnées dans les zones colonnes disponibles.</span><span class="sxs-lookup"><span data-stu-id="d04e3-231">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="d04e3-232">Seules les colonnes de la zone **Sélectionner les colonnes** s’affichent dans la fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="d04e3-232">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="d04e3-233">**Pour réorganiser les colonnes :**</span><span class="sxs-lookup"><span data-stu-id="d04e3-233">**To reorder columns:**</span></span>

<span data-ttu-id="d04e3-234">Vous pouvez faire glisser et déposer des colonnes à l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="d04e3-234">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="d04e3-235">Ou procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d04e3-235">Or use the following steps:</span></span>

1. <span data-ttu-id="d04e3-236">Cliquez avec le bouton droit sur un en-tête de colonne et cliquez sur **Sélectionner les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="d04e3-236">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="d04e3-237">Dans la boîte de dialogue **Sélectionner les colonnes** , utilisez les boutons **monter** **et descendre pour** réorganiser les colonnes.</span><span class="sxs-lookup"><span data-stu-id="d04e3-237">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="d04e3-238">Les colonnes en haut de la liste apparaissent à gauche des colonnes au bas de la liste dans la fenêtre d'affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="d04e3-238">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="d04e3-239">**Comment trier les données de tableau**</span><span class="sxs-lookup"><span data-stu-id="d04e3-239">**How to Sort Table Data**</span></span>

- <span data-ttu-id="d04e3-240">Pour trier les données, cliquez sur un en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="d04e3-240">To sort the data, click a column header.</span></span>
- <span data-ttu-id="d04e3-241">Pour modifier l’ordre de tri, cliquez de nouveau sur l’en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="d04e3-241">To change the sort order, click the column header again.</span></span> <span data-ttu-id="d04e3-242">Chaque fois que vous cliquez sur le même en-tête, l'ordre de tri bascule de croissant à décroissant (ou inversement).</span><span class="sxs-lookup"><span data-stu-id="d04e3-242">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="d04e3-243">L'ordre actif est indiqué par un triangle dans l'en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="d04e3-243">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="d04e3-244">**Comment sélectionner les données de tableau**</span><span class="sxs-lookup"><span data-stu-id="d04e3-244">**How to Select Table Data**</span></span>

- <span data-ttu-id="d04e3-245">Pour sélectionner une ligne, sélectionnez la ligne ou utilisez la flèche haut ou bas pour accéder à la ligne.</span><span class="sxs-lookup"><span data-stu-id="d04e3-245">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="d04e3-246">Pour sélectionner toutes les lignes (à l’exception de la ligne d’en-tête), appuyez sur <kbd>CTRL</kbd> + <kbd>A</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d04e3-246">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="d04e3-247">Pour sélectionner des lignes consécutives, maintenez la touche <kbd>MAJ</kbd> enfoncée tout en cliquant sur les lignes ou en utilisant les touches de direction.</span><span class="sxs-lookup"><span data-stu-id="d04e3-247">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="d04e3-248">Pour sélectionner des lignes non consécutives, appuyez sur la touche <kbd>CTRL</kbd> et cliquez pour ajouter une ligne à la sélection.</span><span class="sxs-lookup"><span data-stu-id="d04e3-248">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="d04e3-249">Vous ne pouvez pas sélectionner des colonnes et vous ne pouvez pas sélectionner la ligne d'en-tête d'une colonne entière.</span><span class="sxs-lookup"><span data-stu-id="d04e3-249">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="d04e3-250">**Comment copier des lignes**</span><span class="sxs-lookup"><span data-stu-id="d04e3-250">**How to Copy Rows**</span></span>

- <span data-ttu-id="d04e3-251">Pour copier une ou plusieurs lignes de la table, sélectionnez les lignes, puis appuyez sur CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="d04e3-251">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="d04e3-252">Vous pouvez coller les données dans n'importe quel tableur ou traitement de texte.</span><span class="sxs-lookup"><span data-stu-id="d04e3-252">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="d04e3-253">Vous ne pouvez pas copier des colonnes ou des parties de ligne et vous ne pouvez pas copier la ligne d'en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="d04e3-253">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="d04e3-254">**Comment effectuer une recherche dans le tableau (filtre rapide)**</span><span class="sxs-lookup"><span data-stu-id="d04e3-254">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="d04e3-255">Utilisez la zone de filtre pour rechercher des données dans la table.</span><span class="sxs-lookup"><span data-stu-id="d04e3-255">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="d04e3-256">Lorsque vous entrez une valeur dans la zone, seuls les éléments qui incluent le texte entré apparaissent dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="d04e3-256">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="d04e3-257">Recherchez du texte.</span><span class="sxs-lookup"><span data-stu-id="d04e3-257">Search for text.</span></span> <span data-ttu-id="d04e3-258">Pour rechercher du texte dans le tableau, dans la zone de filtre, tapez le texte à rechercher.</span><span class="sxs-lookup"><span data-stu-id="d04e3-258">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="d04e3-259">Rechercher plusieurs mots.</span><span class="sxs-lookup"><span data-stu-id="d04e3-259">Search for multiple words.</span></span> <span data-ttu-id="d04e3-260">Pour rechercher plusieurs mots dans le tableau, tapez les mots séparés par un espace.</span><span class="sxs-lookup"><span data-stu-id="d04e3-260">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="d04e3-261">`Out-GridView` affiche les lignes qui incluent tous les mots (AND logique).</span><span class="sxs-lookup"><span data-stu-id="d04e3-261">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="d04e3-262">Recherchez des expressions littérales.</span><span class="sxs-lookup"><span data-stu-id="d04e3-262">Search for literal phrases.</span></span> <span data-ttu-id="d04e3-263">Pour rechercher une expression qui comporte des espaces ou des caractères spéciaux, placez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="d04e3-263">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="d04e3-264">`Out-GridView` affiche les lignes qui incluent une correspondance exacte pour l’expression.</span><span class="sxs-lookup"><span data-stu-id="d04e3-264">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="d04e3-265">Rechercher dans les colonnes.</span><span class="sxs-lookup"><span data-stu-id="d04e3-265">Search in columns.</span></span> <span data-ttu-id="d04e3-266">Pour rechercher un texte dans une ou plusieurs colonnes, utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="d04e3-266">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="d04e3-267">Par exemple, pour rechercher « net » dans la colonne **DisplayName** , dans la zone de **filtre** , tapez :</span><span class="sxs-lookup"><span data-stu-id="d04e3-267">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="d04e3-268">Pour rechercher des lignes avec « net » dans les colonnes **DisplayName** et **Name** , dans la zone de **filtre** , tapez :</span><span class="sxs-lookup"><span data-stu-id="d04e3-268">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="d04e3-269">Désactiver la recherche.</span><span class="sxs-lookup"><span data-stu-id="d04e3-269">Turn off search.</span></span> <span data-ttu-id="d04e3-270">Pour afficher à nouveau la totalité du tableau, cliquez sur le bouton X rouge dans le coin supérieur droit de la zone de **filtre** ou supprimez le texte de la zone de **filtre** .</span><span class="sxs-lookup"><span data-stu-id="d04e3-270">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="d04e3-271">**Utiliser des critères pour filtrer le tableau**</span><span class="sxs-lookup"><span data-stu-id="d04e3-271">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="d04e3-272">Vous pouvez utiliser des règles ou des critères pour déterminer les éléments qui sont affichés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="d04e3-272">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="d04e3-273">Les éléments s’affichent uniquement lorsqu’ils répondent à tous les critères que vous établissez.</span><span class="sxs-lookup"><span data-stu-id="d04e3-273">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="d04e3-274">Les critères disponibles sont déterminés par les propriétés des objets affichés dans la fenêtre d'affichage de grille et les types .NET Framework de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="d04e3-274">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="d04e3-275">Chaque critère a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="d04e3-275">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="d04e3-276">Les critères des différentes propriétés sont connectés par **et**.</span><span class="sxs-lookup"><span data-stu-id="d04e3-276">Criteria for different properties are connected by **AND**.</span></span> <span data-ttu-id="d04e3-277">Les critères de la même propriété sont connectés par **ou**.</span><span class="sxs-lookup"><span data-stu-id="d04e3-277">Criteria for the same property are connected by **OR**.</span></span> <span data-ttu-id="d04e3-278">Vous ne pouvez pas modifier les connecteurs logiques.</span><span class="sxs-lookup"><span data-stu-id="d04e3-278">You cannot change the logical connectors.</span></span>

<span data-ttu-id="d04e3-279">Les critères affectent uniquement l'affichage.</span><span class="sxs-lookup"><span data-stu-id="d04e3-279">The criteria only affects the display.</span></span> <span data-ttu-id="d04e3-280">Ils ne suppriment pas des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="d04e3-280">It does not delete items from the table.</span></span>

<span data-ttu-id="d04e3-281">**Comment ajouter des critères**</span><span class="sxs-lookup"><span data-stu-id="d04e3-281">**How to Add Criteria**</span></span>

1. <span data-ttu-id="d04e3-282">Pour afficher le bouton de menu **Ajouter des critères** , dans le coin supérieur droit de la fenêtre, cliquez sur la flèche de développement.</span><span class="sxs-lookup"><span data-stu-id="d04e3-282">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="d04e3-283">Cliquez sur le bouton de menu **Ajouter des critères** .</span><span class="sxs-lookup"><span data-stu-id="d04e3-283">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="d04e3-284">Cliquez pour sélectionner les colonnes (propriétés).</span><span class="sxs-lookup"><span data-stu-id="d04e3-284">Click to select columns (properties).</span></span> <span data-ttu-id="d04e3-285">Vous pouvez sélectionner une ou plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="d04e3-285">You can select one or many properties.</span></span>
4. <span data-ttu-id="d04e3-286">Lorsque vous avez fini de sélectionner les propriétés, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="d04e3-286">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="d04e3-287">Pour annuler les ajouts, cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="d04e3-287">To cancel the additions, click **Cancel**.</span></span>
6. <span data-ttu-id="d04e3-288">Pour ajouter d’autres critères, cliquez de nouveau sur le bouton **Ajouter des critères** .</span><span class="sxs-lookup"><span data-stu-id="d04e3-288">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="d04e3-289">**Comment modifier un critère**</span><span class="sxs-lookup"><span data-stu-id="d04e3-289">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="d04e3-290">Pour modifier un opérateur, cliquez sur la valeur de l’opérateur bleu, puis sélectionnez un autre opérateur dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="d04e3-290">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="d04e3-291">Pour entrer ou modifier une valeur, tapez une valeur dans la zone valeur.</span><span class="sxs-lookup"><span data-stu-id="d04e3-291">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="d04e3-292">Si vous entrez une valeur qui n'est pas valide, une icône en forme de X s'affiche.</span><span class="sxs-lookup"><span data-stu-id="d04e3-292">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="d04e3-293">Pour supprimer la valeur, modifiez-la.</span><span class="sxs-lookup"><span data-stu-id="d04e3-293">To remove it, change the value.</span></span>
- <span data-ttu-id="d04e3-294">Pour créer une instruction **ou** , ajoutez un critère avec la même propriété.</span><span class="sxs-lookup"><span data-stu-id="d04e3-294">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="d04e3-295">**Comment supprimer des critères**</span><span class="sxs-lookup"><span data-stu-id="d04e3-295">**How to Delete Criteria**</span></span>

- <span data-ttu-id="d04e3-296">Pour supprimer les critères sélectionnés, cliquez sur la Croix Rouge en regard de chaque critère.</span><span class="sxs-lookup"><span data-stu-id="d04e3-296">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="d04e3-297">Pour supprimer tous les critères, cliquez sur le bouton **Effacer tout** .</span><span class="sxs-lookup"><span data-stu-id="d04e3-297">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="d04e3-298">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d04e3-298">RELATED LINKS</span></span>

[<span data-ttu-id="d04e3-299">Out-File</span><span class="sxs-lookup"><span data-stu-id="d04e3-299">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="d04e3-300">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="d04e3-300">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="d04e3-301">Out-String</span><span class="sxs-lookup"><span data-stu-id="d04e3-301">Out-String</span></span>](Out-String.md)

