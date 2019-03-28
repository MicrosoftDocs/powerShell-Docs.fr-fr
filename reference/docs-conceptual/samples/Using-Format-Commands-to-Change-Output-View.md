---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation des commandes de mise en forme pour modifier l’affichage d’une sortie
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 35ccd2525d40ffd5e3f25a1abfa38904a109bde5
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320419"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="e74b7-103">Utilisation des commandes de mise en forme pour modifier l’affichage d’une sortie</span><span class="sxs-lookup"><span data-stu-id="e74b7-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="e74b7-104">Windows PowerShell dispose d’un ensemble d’applets de commande qui vous permettent de contrôler les propriétés affichées pour des objets spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e74b7-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="e74b7-105">Les noms de toutes les applets de commande commencent par le verbe **Format**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="e74b7-106">Elles vous permettent de sélectionner une ou plusieurs propriétés à afficher.</span><span class="sxs-lookup"><span data-stu-id="e74b7-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="e74b7-107">Les applets de commande **Format** sont **Format-Wide**, **Format-List**, **Format-Table**, et **Format-Custom**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="e74b7-108">Ce guide décrit uniquement les applets de commande **Format-Wide**, **Format-List** et **Format-Table**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="e74b7-109">Chaque applet de commande Format a des propriétés par défaut qui sont utilisées si vous ne spécifiez pas de propriétés spécifiques à afficher.</span><span class="sxs-lookup"><span data-stu-id="e74b7-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="e74b7-110">Chaque applet de commande utilise également le même nom de paramètre, **Property**, pour spécifier les propriétés à afficher.</span><span class="sxs-lookup"><span data-stu-id="e74b7-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="e74b7-111">Étant donné que l’applet de commande **Format-Wide** n’affiche qu’une seule propriété, son paramètre **Property** n’accepte qu’une seule valeur, mais les paramètres de propriété des applets de commande **Format-List** et **Format-Table** acceptent une liste de noms de propriétés.</span><span class="sxs-lookup"><span data-stu-id="e74b7-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="e74b7-112">Si vous utilisez la commande **Get-Process -Name powershell** avec deux instances de Windows PowerShell en cours d’exécution, vous obtenez une sortie ressemblant à ceci :</span><span class="sxs-lookup"><span data-stu-id="e74b7-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="e74b7-113">Dans le reste de cette section, nous allons examiner comment utiliser les applets de commande **Format** pour modifier le mode d’affichage de la sortie de cette commande.</span><span class="sxs-lookup"><span data-stu-id="e74b7-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="e74b7-114">Utilisation de l’applet de commande Format-Wide pour une sortie d’élément unique</span><span class="sxs-lookup"><span data-stu-id="e74b7-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="e74b7-115">Par défaut, l’applet de commande **Format-Wide** affiche uniquement la propriété par défaut d’un objet.</span><span class="sxs-lookup"><span data-stu-id="e74b7-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="e74b7-116">Les informations associées à chaque objet s’affichent dans une seule colonne :</span><span class="sxs-lookup"><span data-stu-id="e74b7-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="e74b7-117">Vous pouvez également spécifier une propriété autre que celle par défaut :</span><span class="sxs-lookup"><span data-stu-id="e74b7-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="e74b7-118">Contrôle de l’affichage de Format-Wide avec une colonne</span><span class="sxs-lookup"><span data-stu-id="e74b7-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="e74b7-119">La cmdlet `Format-Wide` ne permet d’afficher qu’une seule propriété à la fois.</span><span class="sxs-lookup"><span data-stu-id="e74b7-119">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span>
<span data-ttu-id="e74b7-120">Cela rend utile l’affichage de listes simples qui ne présentent qu’un seul élément par ligne.</span><span class="sxs-lookup"><span data-stu-id="e74b7-120">This makes it useful for displaying simple lists that show only one element per line.</span></span>
<span data-ttu-id="e74b7-121">Pour obtenir une liste simple, définissez la valeur du paramètre **Column** sur 1 en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e74b7-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="e74b7-122">Utilisation de l’applet de commande Format-List pour un Affichage Liste</span><span class="sxs-lookup"><span data-stu-id="e74b7-122">Using Format-List for a List View</span></span>

<span data-ttu-id="e74b7-123">L’applet de commende **Format-List** affiche un objet sous la forme d’une liste, chaque propriété étant étiquetée et affichée sur une ligne distincte :</span><span class="sxs-lookup"><span data-stu-id="e74b7-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="e74b7-124">Vous pouvez spécifier autant de propriétés que vous le souhaitez :</span><span class="sxs-lookup"><span data-stu-id="e74b7-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="e74b7-125">Obtention d’informations détaillées en utilisant l’applet de commande Format-List avec des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="e74b7-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="e74b7-126">L’applet de commande **Format-List** permet d’utiliser un caractère générique en tant que la valeur pour son paramètre **Property**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="e74b7-127">Cela permet d’afficher des informations détaillées.</span><span class="sxs-lookup"><span data-stu-id="e74b7-127">This lets you display detailed information.</span></span> <span data-ttu-id="e74b7-128">Souvent, des objets incluent plus d’informations que nécessaire. C’est pourquoi, par défaut, Windows PowerShell n’affiche pas les valeurs de toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="e74b7-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="e74b7-129">Pour afficher toutes les propriétés d’un objet, utilisez la commande **Format-List -Property \&#42;**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="e74b7-130">La commande suivante génère plus de 60 lignes de sortie pour un seul processus :</span><span class="sxs-lookup"><span data-stu-id="e74b7-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="e74b7-131">Bien que la commande **Format-List** soit utile pour afficher des détails, si vous souhaitez une vue d’ensemble de la sortie incluant de nombreux d’éléments, une simple vue tabulaire est souvent plus utile.</span><span class="sxs-lookup"><span data-stu-id="e74b7-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="e74b7-132">Utilisation de l’applet de commande Format-Table pour une sortie tabulaire</span><span class="sxs-lookup"><span data-stu-id="e74b7-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="e74b7-133">Si vous utilisez l’applet de commande **Format-Table** sans nom de propriété spécifié pour mettre en forme la sortie de la commande **Get-Process**, vous obtenez exactement la même sortie que sans effectuer de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e74b7-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="e74b7-134">La raison en est que les processus sont généralement affichés dans un format tabulaire, tout comme la plupart des objets Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e74b7-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="e74b7-135">Amélioration de la sortie de l’applet de commande Format-Table (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="e74b7-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="e74b7-136">Bien qu’une vue tabulaire soit utile pour afficher de nombreuses informations comparables, elle peut être difficile à interpréter si l’affichage est trop étroit pour les données.</span><span class="sxs-lookup"><span data-stu-id="e74b7-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="e74b7-137">Par exemple, si vous essayez d’afficher le chemin d’accès au processus, l’ID, le nom et la société, vous obtenez une sortie tronquée pour les colonnes du chemin d’accès et de la société :</span><span class="sxs-lookup"><span data-stu-id="e74b7-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="e74b7-138">Si vous spécifiez le paramètre **AutoSize** lorsque vous exécutez la commande **Format-Table**, Windows PowerShell calcule les largeurs de colonne en fonction des données réelles à afficher.</span><span class="sxs-lookup"><span data-stu-id="e74b7-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="e74b7-139">Cela rend la colonne du **chemin d’accès** lisible, mais la colonne de la société reste tronquée :</span><span class="sxs-lookup"><span data-stu-id="e74b7-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="e74b7-140">L’applet de commande **Format-Table** peut toujours tronquer des données, mais elle ne le fait qu’à la fin de l’écran.</span><span class="sxs-lookup"><span data-stu-id="e74b7-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="e74b7-141">Les propriétés, à l’exception de la dernière affichée, disposent de la taille nécessaire pour que leur élément de données le plus long s’affiche correctement.</span><span class="sxs-lookup"><span data-stu-id="e74b7-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="e74b7-142">Vous pouvez constater que nom de la société est visible, mais que le chemin d’accès est tronqué si vous permutez les emplacements de **Path** et de **Company** dans la liste de valeurs **Property** :</span><span class="sxs-lookup"><span data-stu-id="e74b7-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="e74b7-143">La commande **Format-Table** suppose que, plus une propriété est proche du début de la liste de propriétés, plus elle est importante.</span><span class="sxs-lookup"><span data-stu-id="e74b7-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="e74b7-144">Elle tente donc d’afficher entièrement les propriétés les plus proches du début.</span><span class="sxs-lookup"><span data-stu-id="e74b7-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="e74b7-145">Si la commande **Format-Table** ne peut pas afficher toutes les propriétés, elle supprime certaines colonnes de l’affichage et génère un avertissement.</span><span class="sxs-lookup"><span data-stu-id="e74b7-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="e74b7-146">Vous pouvez observer ce comportement si vous faites de **Name** la dernière propriété de la liste :</span><span class="sxs-lookup"><span data-stu-id="e74b7-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="e74b7-147">Dans la sortie ci-dessus, la colonne ID est tronquée pour qu’elle tienne dans la liste, et les en-têtes de colonne sont empilés.</span><span class="sxs-lookup"><span data-stu-id="e74b7-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="e74b7-148">Une redimensionnement automatique les colonnes ne produit pas toujours le résultat souhaité.</span><span class="sxs-lookup"><span data-stu-id="e74b7-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="e74b7-149">Retour automatique à la ligne de la sortie de l’applet de commande Format-Table dans les colonnes (Wrap)</span><span class="sxs-lookup"><span data-stu-id="e74b7-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="e74b7-150">Vous pouvez forcer le retour automatique à la ligne des données longues retournées par l’applet de commande **Format-Table** dans la colonne d’affichage en utilisant le paramètre **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="e74b7-151">L’utilisation du paramètre **Wrap** isolément ne produit pas nécessairement le résultat attendu car, si vous ne spécifiez pas **AutoSize**, les paramètres par défaut sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="e74b7-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="e74b7-152">Un avantage de l’utilisation du paramètre **Wrap** isolément est qu’il ne ralentit pas beaucoup le traitement.</span><span class="sxs-lookup"><span data-stu-id="e74b7-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="e74b7-153">Si vous générez une liste récursive des fichiers d’un système d’annuaire volumineux, l’affichage des premiers éléments de sortie peut prendre beaucoup de temps et monopoliser beaucoup de mémoire si vous utilisez **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="e74b7-154">Si vous n’êtes pas inquiet de la charge du système, **AutoSize** fonctionne bien avec le paramètre **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="e74b7-155">Les colonnes initiales disposent toujours de la largeur nécessaire pour afficher les éléments sur une seule ligne, comme lorsque vous spécifiez **AutoSize** sans le paramètre **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="e74b7-156">La seule différence est que la dernière colonne contient des retours à la ligne automatiques si nécessaire :</span><span class="sxs-lookup"><span data-stu-id="e74b7-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="e74b7-157">Il se peut que certaines colonnes ne s’affichent pas si vous spécifiez d’abord les colonnes plus larges. Il est donc plus sûr de spécifier en premier les éléments de données les plus petits.</span><span class="sxs-lookup"><span data-stu-id="e74b7-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="e74b7-158">Dans l’exemple suivant, nous spécifions d’abord l’élément de chemin d’accès très large et, même avec un retour automatique à la ligne, nous perdons la dernière colonne **Name** :</span><span class="sxs-lookup"><span data-stu-id="e74b7-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="e74b7-159">Organisation de la sortie de table (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="e74b7-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="e74b7-160">Un autre paramètre utile pour le contrôle de la sortie tabulaire est **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="e74b7-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="e74b7-161">Des listes tabulaires plus longues en particulier peuvent être difficiles à comparer.</span><span class="sxs-lookup"><span data-stu-id="e74b7-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="e74b7-162">Le paramètre **GroupBy** groupe la sortie en fonction d’une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="e74b7-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="e74b7-163">Par exemple, nous pouvons grouper des processus par société pour faciliter l’inspection, en omettant la valeur de la société de la liste des propriétés :</span><span class="sxs-lookup"><span data-stu-id="e74b7-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```