---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 19a53b5b14d2dfdb513fbbda4c55ba0df37ab1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595913"
---
# <span data-ttu-id="e3e74-102">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="e3e74-102">Out-GridView</span></span>

## <span data-ttu-id="e3e74-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e3e74-103">SYNOPSIS</span></span>
<span data-ttu-id="e3e74-104">Envoie la sortie vers un tableau interactif dans une fenêtre distincte.</span><span class="sxs-lookup"><span data-stu-id="e3e74-104">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="e3e74-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="e3e74-105">SYNTAX</span></span>

### <span data-ttu-id="e3e74-106">PassThru (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e3e74-106">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="e3e74-107">Wait</span><span class="sxs-lookup"><span data-stu-id="e3e74-107">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="e3e74-108">OutputMode</span><span class="sxs-lookup"><span data-stu-id="e3e74-108">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="e3e74-109">Description</span><span class="sxs-lookup"><span data-stu-id="e3e74-109">DESCRIPTION</span></span>

<span data-ttu-id="e3e74-110">L' `Out-GridView` applet de commande envoie la sortie d’une commande à une fenêtre d’affichage de grille dans laquelle la sortie est affichée dans un tableau interactif.</span><span class="sxs-lookup"><span data-stu-id="e3e74-110">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="e3e74-111">Étant donné que cette applet de commande nécessite une interface utilisateur, elle ne fonctionne pas sur Windows Server Core ou Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="e3e74-111">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="e3e74-112">Vous pouvez utiliser les fonctionnalités suivantes du tableau pour examiner vos données :</span><span class="sxs-lookup"><span data-stu-id="e3e74-112">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="e3e74-113">Masquer, afficher et réorganiser les colonnes</span><span class="sxs-lookup"><span data-stu-id="e3e74-113">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="e3e74-114">Trier les lignes</span><span class="sxs-lookup"><span data-stu-id="e3e74-114">Sort rows</span></span>
- <span data-ttu-id="e3e74-115">Filtre rapide</span><span class="sxs-lookup"><span data-stu-id="e3e74-115">Quick Filter</span></span>
- <span data-ttu-id="e3e74-116">Filtre ajouter des critères</span><span class="sxs-lookup"><span data-stu-id="e3e74-116">Add Criteria Filter</span></span>
- <span data-ttu-id="e3e74-117">Copier et coller</span><span class="sxs-lookup"><span data-stu-id="e3e74-117">Copy and paste</span></span>

<span data-ttu-id="e3e74-118">Pour obtenir des instructions complètes, consultez la section [Remarques](#notes) de cet article.</span><span class="sxs-lookup"><span data-stu-id="e3e74-118">For full instructions, see the [Notes](#notes) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="e3e74-119">Cette applet de commande a été réintroduite dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="e3e74-119">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="e3e74-120">Cette applet de commande est uniquement disponible sur les systèmes Windows qui prennent en charge le bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="e3e74-120">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span> <span data-ttu-id="e3e74-121">Pour une version multiplateforme de cette applet de commande, consultez le module [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) dans le PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e3e74-121">For a cross-platform version of this cmdlet, see the [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) module in the PowerShell Gallery.</span></span>

## <span data-ttu-id="e3e74-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e3e74-122">EXAMPLES</span></span>

### <span data-ttu-id="e3e74-123">Exemple 1 : processus de sortie vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="e3e74-123">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="e3e74-124">Cet exemple obtient les processus en cours d’exécution sur l’ordinateur local et les envoie à une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="e3e74-124">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="e3e74-125">Exemple 2 : utiliser une variable pour sortir des processus dans un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="e3e74-125">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="e3e74-126">Cet exemple obtient également les processus en cours d’exécution sur l’ordinateur local et les envoie à une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="e3e74-126">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="e3e74-127">La sortie de l' `Get-Process` applet de commande est enregistrée dans la `$P` variable.</span><span class="sxs-lookup"><span data-stu-id="e3e74-127">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="e3e74-128">Ensuite, `$P` est dirigé vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-128">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="e3e74-129">Exemple 3 : afficher les propriétés sélectionnées dans un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="e3e74-129">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="e3e74-130">Cet exemple affiche les propriétés sélectionnées des processus en cours d’exécution dans un affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="e3e74-130">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="e3e74-131">La sortie de `Get-Process` est redirigée vers `Select-Object` pour sélectionner les propriétés **Name**, de la **plage** de **PeakWorkingSet** et de la propriété.</span><span class="sxs-lookup"><span data-stu-id="e3e74-131">The output of `Get-Process` is piped to `Select-Object` to select the **Name**, **WorkingSet**, and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="e3e74-132">Un autre opérateur de pipeline envoie les objets filtrés à l' `Sort-Object` applet de commande pour les trier dans l’ordre décroissant selon la valeur de la propriété de la **plage** de recherche.</span><span class="sxs-lookup"><span data-stu-id="e3e74-132">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="e3e74-133">Ensuite, les résultats triés sont dirigés vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-133">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="e3e74-134">Vous pouvez maintenant utiliser les fonctionnalités de l'affichage de grille pour rechercher, trier ou filtrer les données.</span><span class="sxs-lookup"><span data-stu-id="e3e74-134">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="e3e74-135">Exemple 4 : enregistrer la sortie dans une variable, puis générer une vue grille</span><span class="sxs-lookup"><span data-stu-id="e3e74-135">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="e3e74-136">Cet exemple enregistre la sortie de l’applet de commande dans une variable, puis l’envoie à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-136">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="e3e74-137">`Get-ChildItem` Obtient tous les fichiers dans le répertoire d’installation de PowerShell et ses sous-répertoires à l’aide de la `$PSHOME` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="e3e74-137">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="e3e74-138">Les parenthèses de la commande établissent l'ordre des opérations.</span><span class="sxs-lookup"><span data-stu-id="e3e74-138">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="e3e74-139">En conséquence, la sortie de la `Get-ChildItem` commande est enregistrée dans la `$A` variable avant d’être envoyée à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-139">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="e3e74-140">Exemple 5 : processus de sortie pour un ordinateur spécifié vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="e3e74-140">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="e3e74-141">Cet exemple affiche les processus en cours d’exécution sur l’ordinateur SERVEUR01 dans une fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="e3e74-141">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="e3e74-142">Exemple utilise `ogv` , qui est l’alias de l’applet de commande `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-142">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="e3e74-143">Le paramètre **title** spécifie le titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e3e74-143">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="e3e74-144">Exemple 6 : sortie des données des ordinateurs distants vers un affichage de grille</span><span class="sxs-lookup"><span data-stu-id="e3e74-144">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="e3e74-145">Cet exemple montre comment envoyer des données collectées à partir d’ordinateurs distants vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-145">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="e3e74-146">`Invoke-Command` s’exécute `Get-Culture` sur trois ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="e3e74-146">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="e3e74-147">Les données résultantes sont redirigées vers `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-147">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="e3e74-148">Notez que le bloc de script qui s’exécute sur l’ordinateur distant n’inclut pas la `Out-GridView` commande.</span><span class="sxs-lookup"><span data-stu-id="e3e74-148">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="e3e74-149">Si tel était le cas, la commande échouerait quand elle essaierait d'ouvrir une fenêtre d'affichage de grille sur chacun des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="e3e74-149">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="e3e74-150">Exemple 7 : passer plusieurs éléments à `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="e3e74-150">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="e3e74-151">Cet exemple vous permet de sélectionner plusieurs processus dans la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e3e74-151">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="e3e74-152">Les processus que vous sélectionnez sont passés à la `Export-Csv` commande et écrits dans le `ProcessLog.csv` fichier.</span><span class="sxs-lookup"><span data-stu-id="e3e74-152">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="e3e74-153">Le paramètre **PassThru** de `Out-GridView` vous permet d’envoyer plusieurs éléments vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="e3e74-153">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="e3e74-154">Le paramètre **PassThru** équivaut à l'utilisation de la valeur **Multiple** du paramètre **OutputMode**.</span><span class="sxs-lookup"><span data-stu-id="e3e74-154">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="e3e74-155">Exemple 8 : créer un raccourci Windows vers `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="e3e74-155">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="e3e74-156">Cet exemple montre comment utiliser le paramètre **Wait** de `Out-GridView` pour créer un raccourci Windows dans la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e3e74-156">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="e3e74-157">Cette ligne de commande peut être utilisée dans un raccourci Windows.</span><span class="sxs-lookup"><span data-stu-id="e3e74-157">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="e3e74-158">Sans le paramètre **Wait** , PowerShell s’arrête dès que la fenêtre s’est `Out-GridView` ouverte, ce qui ferme la `Out-GridView` fenêtre presque immédiatement.</span><span class="sxs-lookup"><span data-stu-id="e3e74-158">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="e3e74-159">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e3e74-159">PARAMETERS</span></span>

### <span data-ttu-id="e3e74-160">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e3e74-160">-InputObject</span></span>

<span data-ttu-id="e3e74-161">Spécifie l’objet que l’applet de commande accepte comme entrée pour `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-161">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="e3e74-162">Quand vous utilisez le paramètre **InputObject** pour envoyer une collection d’objets à `Out-GridView` , `Out-GridView` traite la collection comme un objet de collection et affiche une ligne qui représente la collection.</span><span class="sxs-lookup"><span data-stu-id="e3e74-162">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="e3e74-163">Pour afficher chaque objet de la collection, utilisez un opérateur de pipeline ( `|` ) pour envoyer des objets à `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-163">To display the each object in the collection, use a pipeline operator (`|`) to send objects to `Out-GridView`.</span></span>

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

### <span data-ttu-id="e3e74-164">-Du outputmode</span><span class="sxs-lookup"><span data-stu-id="e3e74-164">-OutputMode</span></span>

<span data-ttu-id="e3e74-165">Spécifie les éléments que la fenêtre interactive envoie au pipeline en tant qu’entrée d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="e3e74-165">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="e3e74-166">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="e3e74-166">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="e3e74-167">Pour envoyer des éléments depuis la fenêtre interactive dans le pipeline, cliquez pour sélectionner les éléments, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="e3e74-167">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="e3e74-168">Les valeurs de ce paramètre déterminent le nombre d'éléments que vous pouvez envoyer dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="e3e74-168">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="e3e74-169">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e3e74-169">None.</span></span>  <span data-ttu-id="e3e74-170">aucun élément.</span><span class="sxs-lookup"><span data-stu-id="e3e74-170">No items.</span></span> <span data-ttu-id="e3e74-171">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e3e74-171">This is the default value.</span></span>
- <span data-ttu-id="e3e74-172">Unique.</span><span class="sxs-lookup"><span data-stu-id="e3e74-172">Single.</span></span> <span data-ttu-id="e3e74-173">zéro ou un élément.</span><span class="sxs-lookup"><span data-stu-id="e3e74-173">Zero items or one item.</span></span> <span data-ttu-id="e3e74-174">Utilisez cette valeur lorsque la commande suivante ne peut prendre qu'un seul objet en entrée.</span><span class="sxs-lookup"><span data-stu-id="e3e74-174">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="e3e74-175">Plusieurs.</span><span class="sxs-lookup"><span data-stu-id="e3e74-175">Multiple.</span></span> <span data-ttu-id="e3e74-176">zéro, un ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="e3e74-176">Zero, one, or many items.</span></span> <span data-ttu-id="e3e74-177">Utilisez cette valeur lorsque la commande suivante peut prendre plusieurs objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="e3e74-177">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="e3e74-178">Cette valeur est équivalente au paramètre **Passthru**.</span><span class="sxs-lookup"><span data-stu-id="e3e74-178">This value is equivalent to the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="e3e74-179">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e3e74-179">-PassThru</span></span>

<span data-ttu-id="e3e74-180">Indique que l’applet de commande envoie les éléments à partir de la fenêtre interactive dans le pipeline en tant qu’entrée d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="e3e74-180">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="e3e74-181">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="e3e74-181">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="e3e74-182">Ce paramètre est équivalent à l'utilisation de la valeur **Multiple** du paramètre **OutputMode**.</span><span class="sxs-lookup"><span data-stu-id="e3e74-182">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="e3e74-183">Pour envoyer des éléments depuis la fenêtre interactive dans le pipeline, cliquez pour sélectionner les éléments, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="e3e74-183">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="e3e74-184">MAJ+clic et Ctrl+clic sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e3e74-184">Shift-click and Ctrl-click are supported.</span></span>

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

### <span data-ttu-id="e3e74-185">-Title</span><span class="sxs-lookup"><span data-stu-id="e3e74-185">-Title</span></span>

<span data-ttu-id="e3e74-186">Spécifie le texte qui apparaît dans la barre de titre de la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e3e74-186">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="e3e74-187">Par défaut, la barre de titre affiche la commande qui appelle `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-187">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

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

### <span data-ttu-id="e3e74-188">-Wait</span><span class="sxs-lookup"><span data-stu-id="e3e74-188">-Wait</span></span>

<span data-ttu-id="e3e74-189">Indique que l’applet de commande supprime l’invite de commandes et empêche Windows PowerShell de se fermer jusqu’à la fermeture de la `Out-GridView` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e3e74-189">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="e3e74-190">Par défaut, l’invite de commandes retourne quand la `Out-GridView` fenêtre s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="e3e74-190">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="e3e74-191">Cette fonctionnalité vous permet d’utiliser les `Out-GridView` applets de commande dans les raccourcis Windows.</span><span class="sxs-lookup"><span data-stu-id="e3e74-191">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="e3e74-192">Quand `Out-GridView` est utilisé dans un raccourci sans le paramètre **Wait** , la `Out-GridView` fenêtre s’affiche uniquement momentanément avant la fermeture de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3e74-192">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

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

### <span data-ttu-id="e3e74-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3e74-193">CommonParameters</span></span>

<span data-ttu-id="e3e74-194">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e3e74-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3e74-195">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e3e74-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e3e74-196">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e3e74-196">INPUTS</span></span>

### <span data-ttu-id="e3e74-197">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="e3e74-197">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e3e74-198">Vous pouvez envoyer n’importe quel objet à cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e3e74-198">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="e3e74-199">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e3e74-199">OUTPUTS</span></span>

### <span data-ttu-id="e3e74-200">None</span><span class="sxs-lookup"><span data-stu-id="e3e74-200">None</span></span>

<span data-ttu-id="e3e74-201">Normalement, `Out-GridView` ne retourne pas d’objets.</span><span class="sxs-lookup"><span data-stu-id="e3e74-201">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="e3e74-202">Lors de l’utilisation du paramètre **PassThru** , les objets représentant les lignes sélectionnées sont retournés au pipeline.</span><span class="sxs-lookup"><span data-stu-id="e3e74-202">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="e3e74-203">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e3e74-203">NOTES</span></span>

<span data-ttu-id="e3e74-204">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="e3e74-204">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="e3e74-205">Vous ne pouvez pas utiliser une commande distante pour ouvrir une fenêtre d'affichage de grille sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e3e74-205">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="e3e74-206">La sortie de commande que vous envoyez à `Out-GridView` ne peut pas être mise en forme à l’aide des `Format` applets de commande, telles que `Format-Table` ou `Format-Wide` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e3e74-206">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="e3e74-207">Pour sélectionner des propriétés, utilisez l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="e3e74-207">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="e3e74-208">La sortie désérialisée à partir des commandes distantes ne peut pas être correctement mise en forme dans la fenêtre d'affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="e3e74-208">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="e3e74-209">**Raccourcis clavier pour**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="e3e74-209">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="e3e74-210">Utilisez cette clé :</span><span class="sxs-lookup"><span data-stu-id="e3e74-210">Use this key:</span></span>              |                                   <span data-ttu-id="e3e74-211">Pour exécuter cette action :</span><span class="sxs-lookup"><span data-stu-id="e3e74-211">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e3e74-212"><kbd>Tab</kbd></span><span class="sxs-lookup"><span data-stu-id="e3e74-212"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="e3e74-213">Déplace le curseur de la zone **filtre** vers le menu **Ajouter des critères** vers la table et inversement.</span><span class="sxs-lookup"><span data-stu-id="e3e74-213">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="e3e74-214"><kbd>Haut</kbd></span><span class="sxs-lookup"><span data-stu-id="e3e74-214"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="e3e74-215">Remonter d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="e3e74-215">Move up one row.</span></span> <span data-ttu-id="e3e74-216">Se déplace vers les en-têtes de colonne à partir de la première ligne de données.</span><span class="sxs-lookup"><span data-stu-id="e3e74-216">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="e3e74-217"><kbd>Flèche</kbd></span><span class="sxs-lookup"><span data-stu-id="e3e74-217"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="e3e74-218">Descendre d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="e3e74-218">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="e3e74-219"><kbd>Flèche gauche</kbd></span><span class="sxs-lookup"><span data-stu-id="e3e74-219"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="e3e74-220">Dans ligne d’en-tête de colonne, déplacer d’une colonne vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="e3e74-220">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="e3e74-221"><kbd>Flèche droite</kbd></span><span class="sxs-lookup"><span data-stu-id="e3e74-221"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="e3e74-222">Dans ligne d’en-tête de colonne, déplacer vers la droite d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="e3e74-222">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="e3e74-223"><kbd>ContextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="e3e74-223"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="e3e74-224">Dans ligne d’en-tête de colonne, affiche l’option Sélectionner les colonnes.</span><span class="sxs-lookup"><span data-stu-id="e3e74-224">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="e3e74-225"><kbd>Entrée</kbd> ou <kbd>barre d’espace</kbd></span><span class="sxs-lookup"><span data-stu-id="e3e74-225"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="e3e74-226">Dans la ligne d’en-tête de colonne, triez les données de la colonne (basculez A-Z, Z-A).</span><span class="sxs-lookup"><span data-stu-id="e3e74-226">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="e3e74-227">**Comment utiliser les fonctionnalités de la fenêtre d’affichage de grille**</span><span class="sxs-lookup"><span data-stu-id="e3e74-227">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="e3e74-228">**Pour masquer ou afficher une colonne :**</span><span class="sxs-lookup"><span data-stu-id="e3e74-228">**To hide or show a column:**</span></span>

1. <span data-ttu-id="e3e74-229">Cliquez avec le bouton droit sur un en-tête de colonne et cliquez sur **Sélectionner les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="e3e74-229">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="e3e74-230">Dans la boîte de dialogue **Sélectionner les colonnes** , utilisez les touches de direction pour déplacer les colonnes entre les colonnes sélectionnées dans les zones colonnes disponibles.</span><span class="sxs-lookup"><span data-stu-id="e3e74-230">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="e3e74-231">Seules les colonnes de la zone **Sélectionner les colonnes** s’affichent dans la fenêtre d’affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="e3e74-231">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="e3e74-232">**Pour réorganiser les colonnes :**</span><span class="sxs-lookup"><span data-stu-id="e3e74-232">**To reorder columns:**</span></span>

<span data-ttu-id="e3e74-233">Vous pouvez faire glisser et déposer des colonnes à l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="e3e74-233">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="e3e74-234">Ou procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e3e74-234">Or use the following steps:</span></span>

1. <span data-ttu-id="e3e74-235">Cliquez avec le bouton droit sur un en-tête de colonne et cliquez sur **Sélectionner les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="e3e74-235">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="e3e74-236">Dans la boîte de dialogue **Sélectionner les colonnes** , utilisez les boutons **monter** **et descendre pour** réorganiser les colonnes.</span><span class="sxs-lookup"><span data-stu-id="e3e74-236">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="e3e74-237">Les colonnes en haut de la liste apparaissent à gauche des colonnes au bas de la liste dans la fenêtre d'affichage de grille.</span><span class="sxs-lookup"><span data-stu-id="e3e74-237">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="e3e74-238">**Comment trier les données de tableau**</span><span class="sxs-lookup"><span data-stu-id="e3e74-238">**How to Sort Table Data**</span></span>

- <span data-ttu-id="e3e74-239">Pour trier les données, cliquez sur un en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="e3e74-239">To sort the data, click a column header.</span></span>
- <span data-ttu-id="e3e74-240">Pour modifier l’ordre de tri, cliquez de nouveau sur l’en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="e3e74-240">To change the sort order, click the column header again.</span></span> <span data-ttu-id="e3e74-241">Chaque fois que vous cliquez sur le même en-tête, l'ordre de tri bascule de croissant à décroissant (ou inversement).</span><span class="sxs-lookup"><span data-stu-id="e3e74-241">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="e3e74-242">L'ordre actif est indiqué par un triangle dans l'en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="e3e74-242">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="e3e74-243">**Comment sélectionner les données de tableau**</span><span class="sxs-lookup"><span data-stu-id="e3e74-243">**How to Select Table Data**</span></span>

- <span data-ttu-id="e3e74-244">Pour sélectionner une ligne, sélectionnez la ligne ou utilisez la flèche haut ou bas pour accéder à la ligne.</span><span class="sxs-lookup"><span data-stu-id="e3e74-244">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="e3e74-245">Pour sélectionner toutes les lignes (à l’exception de la ligne d’en-tête), appuyez sur <kbd>CTRL</kbd> + <kbd>A</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e3e74-245">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="e3e74-246">Pour sélectionner des lignes consécutives, maintenez la touche <kbd>MAJ</kbd> enfoncée tout en cliquant sur les lignes ou en utilisant les touches de direction.</span><span class="sxs-lookup"><span data-stu-id="e3e74-246">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="e3e74-247">Pour sélectionner des lignes non consécutives, appuyez sur la touche <kbd>CTRL</kbd> et cliquez pour ajouter une ligne à la sélection.</span><span class="sxs-lookup"><span data-stu-id="e3e74-247">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="e3e74-248">Vous ne pouvez pas sélectionner des colonnes et vous ne pouvez pas sélectionner la ligne d'en-tête d'une colonne entière.</span><span class="sxs-lookup"><span data-stu-id="e3e74-248">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="e3e74-249">**Comment copier des lignes**</span><span class="sxs-lookup"><span data-stu-id="e3e74-249">**How to Copy Rows**</span></span>

- <span data-ttu-id="e3e74-250">Pour copier une ou plusieurs lignes de la table, sélectionnez les lignes, puis appuyez sur CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="e3e74-250">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="e3e74-251">Vous pouvez coller les données dans n'importe quel tableur ou traitement de texte.</span><span class="sxs-lookup"><span data-stu-id="e3e74-251">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="e3e74-252">Vous ne pouvez pas copier des colonnes ou des parties de ligne et vous ne pouvez pas copier la ligne d'en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="e3e74-252">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="e3e74-253">**Comment effectuer une recherche dans le tableau (filtre rapide)**</span><span class="sxs-lookup"><span data-stu-id="e3e74-253">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="e3e74-254">Utilisez la zone de filtre pour rechercher des données dans la table.</span><span class="sxs-lookup"><span data-stu-id="e3e74-254">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="e3e74-255">Lorsque vous entrez une valeur dans la zone, seuls les éléments qui incluent le texte entré apparaissent dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="e3e74-255">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="e3e74-256">Recherchez du texte.</span><span class="sxs-lookup"><span data-stu-id="e3e74-256">Search for text.</span></span> <span data-ttu-id="e3e74-257">Pour rechercher du texte dans le tableau, dans la zone de filtre, tapez le texte à rechercher.</span><span class="sxs-lookup"><span data-stu-id="e3e74-257">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="e3e74-258">Rechercher plusieurs mots.</span><span class="sxs-lookup"><span data-stu-id="e3e74-258">Search for multiple words.</span></span> <span data-ttu-id="e3e74-259">Pour rechercher plusieurs mots dans le tableau, tapez les mots séparés par un espace.</span><span class="sxs-lookup"><span data-stu-id="e3e74-259">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="e3e74-260">`Out-GridView` affiche les lignes qui incluent tous les mots (AND logique).</span><span class="sxs-lookup"><span data-stu-id="e3e74-260">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="e3e74-261">Recherchez des expressions littérales.</span><span class="sxs-lookup"><span data-stu-id="e3e74-261">Search for literal phrases.</span></span> <span data-ttu-id="e3e74-262">Pour rechercher une expression qui comporte des espaces ou des caractères spéciaux, placez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="e3e74-262">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="e3e74-263">`Out-GridView` affiche les lignes qui incluent une correspondance exacte pour l’expression.</span><span class="sxs-lookup"><span data-stu-id="e3e74-263">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="e3e74-264">Rechercher dans les colonnes.</span><span class="sxs-lookup"><span data-stu-id="e3e74-264">Search in columns.</span></span> <span data-ttu-id="e3e74-265">Pour rechercher un texte dans une ou plusieurs colonnes, utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="e3e74-265">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="e3e74-266">Par exemple, pour rechercher « net » dans la colonne **DisplayName** , dans la zone de **filtre** , tapez :</span><span class="sxs-lookup"><span data-stu-id="e3e74-266">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="e3e74-267">Pour rechercher des lignes avec « net » dans les colonnes **DisplayName** et **Name** , dans la zone de **filtre** , tapez :</span><span class="sxs-lookup"><span data-stu-id="e3e74-267">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="e3e74-268">Désactiver la recherche.</span><span class="sxs-lookup"><span data-stu-id="e3e74-268">Turn off search.</span></span> <span data-ttu-id="e3e74-269">Pour afficher à nouveau la totalité du tableau, cliquez sur le bouton X rouge dans le coin supérieur droit de la zone de **filtre** ou supprimez le texte de la zone de **filtre** .</span><span class="sxs-lookup"><span data-stu-id="e3e74-269">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="e3e74-270">**Utiliser des critères pour filtrer le tableau**</span><span class="sxs-lookup"><span data-stu-id="e3e74-270">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="e3e74-271">Vous pouvez utiliser des règles ou des critères pour déterminer les éléments qui sont affichés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="e3e74-271">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="e3e74-272">Les éléments s’affichent uniquement lorsqu’ils répondent à tous les critères que vous établissez.</span><span class="sxs-lookup"><span data-stu-id="e3e74-272">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="e3e74-273">Les critères disponibles sont déterminés par les propriétés des objets affichés dans la fenêtre d'affichage de grille et les types .NET Framework de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="e3e74-273">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="e3e74-274">Chaque critère a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="e3e74-274">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="e3e74-275">Les critères des différentes propriétés sont connectés par **et**.</span><span class="sxs-lookup"><span data-stu-id="e3e74-275">Criteria for different properties are connected by **AND**.</span></span> <span data-ttu-id="e3e74-276">Les critères de la même propriété sont connectés par **ou**.</span><span class="sxs-lookup"><span data-stu-id="e3e74-276">Criteria for the same property are connected by **OR**.</span></span> <span data-ttu-id="e3e74-277">Vous ne pouvez pas modifier les connecteurs logiques.</span><span class="sxs-lookup"><span data-stu-id="e3e74-277">You cannot change the logical connectors.</span></span>

<span data-ttu-id="e3e74-278">Les critères affectent uniquement l'affichage.</span><span class="sxs-lookup"><span data-stu-id="e3e74-278">The criteria only affects the display.</span></span> <span data-ttu-id="e3e74-279">Ils ne suppriment pas des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="e3e74-279">It does not delete items from the table.</span></span>

<span data-ttu-id="e3e74-280">**Comment ajouter des critères**</span><span class="sxs-lookup"><span data-stu-id="e3e74-280">**How to Add Criteria**</span></span>

1. <span data-ttu-id="e3e74-281">Pour afficher le bouton de menu **Ajouter des critères** , dans le coin supérieur droit de la fenêtre, cliquez sur la flèche de développement.</span><span class="sxs-lookup"><span data-stu-id="e3e74-281">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="e3e74-282">Cliquez sur le bouton de menu **Ajouter des critères** .</span><span class="sxs-lookup"><span data-stu-id="e3e74-282">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="e3e74-283">Cliquez pour sélectionner les colonnes (propriétés).</span><span class="sxs-lookup"><span data-stu-id="e3e74-283">Click to select columns (properties).</span></span> <span data-ttu-id="e3e74-284">Vous pouvez sélectionner une ou plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="e3e74-284">You can select one or many properties.</span></span>
4. <span data-ttu-id="e3e74-285">Lorsque vous avez fini de sélectionner les propriétés, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="e3e74-285">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="e3e74-286">Pour annuler les ajouts, cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="e3e74-286">To cancel the additions, click **Cancel**.</span></span>
6. <span data-ttu-id="e3e74-287">Pour ajouter d’autres critères, cliquez de nouveau sur le bouton **Ajouter des critères** .</span><span class="sxs-lookup"><span data-stu-id="e3e74-287">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="e3e74-288">**Comment modifier un critère**</span><span class="sxs-lookup"><span data-stu-id="e3e74-288">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="e3e74-289">Pour modifier un opérateur, cliquez sur la valeur de l’opérateur bleu, puis sélectionnez un autre opérateur dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e3e74-289">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="e3e74-290">Pour entrer ou modifier une valeur, tapez une valeur dans la zone valeur.</span><span class="sxs-lookup"><span data-stu-id="e3e74-290">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="e3e74-291">Si vous entrez une valeur qui n'est pas valide, une icône en forme de X s'affiche.</span><span class="sxs-lookup"><span data-stu-id="e3e74-291">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="e3e74-292">Pour supprimer la valeur, modifiez-la.</span><span class="sxs-lookup"><span data-stu-id="e3e74-292">To remove it, change the value.</span></span>
- <span data-ttu-id="e3e74-293">Pour créer une instruction **ou** , ajoutez un critère avec la même propriété.</span><span class="sxs-lookup"><span data-stu-id="e3e74-293">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="e3e74-294">**Comment supprimer des critères**</span><span class="sxs-lookup"><span data-stu-id="e3e74-294">**How to Delete Criteria**</span></span>

- <span data-ttu-id="e3e74-295">Pour supprimer les critères sélectionnés, cliquez sur la Croix Rouge en regard de chaque critère.</span><span class="sxs-lookup"><span data-stu-id="e3e74-295">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="e3e74-296">Pour supprimer tous les critères, cliquez sur le bouton **Effacer tout** .</span><span class="sxs-lookup"><span data-stu-id="e3e74-296">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="e3e74-297">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e3e74-297">RELATED LINKS</span></span>

[<span data-ttu-id="e3e74-298">Out-File</span><span class="sxs-lookup"><span data-stu-id="e3e74-298">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="e3e74-299">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="e3e74-299">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="e3e74-300">Out-String</span><span class="sxs-lookup"><span data-stu-id="e3e74-300">Out-String</span></span>](Out-String.md)

