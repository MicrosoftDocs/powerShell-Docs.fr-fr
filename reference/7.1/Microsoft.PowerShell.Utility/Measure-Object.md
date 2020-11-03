---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 88b18a929a1debc85eb7ce65dbdf2d14fc4b89cd
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205922"
---
# <span data-ttu-id="7c302-103">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-103">Measure-Object</span></span>

## <span data-ttu-id="7c302-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7c302-104">SYNOPSIS</span></span>
<span data-ttu-id="7c302-105">Calcule les propriétés numériques des objets et les caractères, les mots et les lignes dans les objets de chaîne, par exemple les fichiers de texte.</span><span class="sxs-lookup"><span data-stu-id="7c302-105">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="7c302-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7c302-106">SYNTAX</span></span>

### <span data-ttu-id="7c302-107">GenericMeasure (par défaut)</span><span class="sxs-lookup"><span data-stu-id="7c302-107">GenericMeasure (Default)</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### <span data-ttu-id="7c302-108">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="7c302-108">TextMeasure</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="7c302-109">Description</span><span class="sxs-lookup"><span data-stu-id="7c302-109">DESCRIPTION</span></span>

<span data-ttu-id="7c302-110">L' `Measure-Object` applet de commande calcule les valeurs de propriété de certains types d’objets.</span><span class="sxs-lookup"><span data-stu-id="7c302-110">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="7c302-111">`Measure-Object` effectue trois types de mesures, selon les paramètres de la commande.</span><span class="sxs-lookup"><span data-stu-id="7c302-111">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="7c302-112">L' `Measure-Object` applet de commande effectue des calculs sur les valeurs de propriété des objets.</span><span class="sxs-lookup"><span data-stu-id="7c302-112">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="7c302-113">Vous pouvez utiliser `Measure-Object` pour compter les objets ou compter les objets avec une **propriété** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7c302-113">You can use `Measure-Object` to count objects or count objects with a specified **Property** .</span></span> <span data-ttu-id="7c302-114">Vous pouvez également utiliser `Measure-Object` pour calculer la valeur **minimale** , la **valeur maximale** , la **somme** , la **StandardDeviation** et la **moyenne** des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="7c302-114">You can also use `Measure-Object` to calculate the **Minimum** , **Maximum** , **Sum** , **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="7c302-115">Pour les objets **String** , vous pouvez également utiliser `Measure-Object` pour compter le nombre de lignes, de mots et de caractères.</span><span class="sxs-lookup"><span data-stu-id="7c302-115">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="7c302-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7c302-116">EXAMPLES</span></span>

### <span data-ttu-id="7c302-117">Exemple 1 : compter les fichiers et les dossiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="7c302-117">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="7c302-118">Cette commande compte les fichiers et dossiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="7c302-118">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="7c302-119">Exemple 2 : mesure des fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="7c302-119">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="7c302-120">Cette commande affiche la **valeur minimale** , la **valeur maximale** et la **somme** des tailles de tous les fichiers dans le répertoire actif, ainsi que la taille moyenne d’un fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="7c302-120">This command displays the **Minimum** , **Maximum** , and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="7c302-121">Exemple 3 : mesure du texte dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="7c302-121">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="7c302-122">Cette commande affiche le nombre de caractères, de mots et de lignes dans le fichier Text.txt.</span><span class="sxs-lookup"><span data-stu-id="7c302-122">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="7c302-123">Sans le paramètre **RAW** , `Get-Content` génère le fichier sous la forme d’un tableau de lignes.</span><span class="sxs-lookup"><span data-stu-id="7c302-123">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="7c302-124">La première commande utilise `Set-Content` pour ajouter du texte par défaut à un fichier.</span><span class="sxs-lookup"><span data-stu-id="7c302-124">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="7c302-125">Exemple 4 : mesurer des objets contenant une propriété spécifiée</span><span class="sxs-lookup"><span data-stu-id="7c302-125">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="7c302-126">Cet exemple compte le nombre d’objets qui ont une propriété **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="7c302-126">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="7c302-127">Les deux premières commandes récupèrent tous les services et processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7c302-127">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="7c302-128">La troisième commande compte le nombre combiné de services et de processus.</span><span class="sxs-lookup"><span data-stu-id="7c302-128">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="7c302-129">La dernière commande combine les deux collections et envoie le résultat à `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="7c302-129">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="7c302-130">L’objet **System. Diagnostics. Process** n’a pas de propriété **DisplayName** et n’est pas extrait du nombre final.</span><span class="sxs-lookup"><span data-stu-id="7c302-130">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### <span data-ttu-id="7c302-131">Exemple 5 : mesurer le contenu d’un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="7c302-131">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="7c302-132">Cette commande calcule les années de service en moyenne des employés d'une société.</span><span class="sxs-lookup"><span data-stu-id="7c302-132">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="7c302-133">Le `ServiceYrs.csv` fichier est un fichier CSV qui contient le numéro d’employé et les années de service de chaque employé.</span><span class="sxs-lookup"><span data-stu-id="7c302-133">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="7c302-134">La première ligne de la table est une ligne d’en-tête de **matemp** , **years** .</span><span class="sxs-lookup"><span data-stu-id="7c302-134">The first row in the table is a header row of **EmpNo** , **Years** .</span></span>

<span data-ttu-id="7c302-135">Lorsque vous utilisez `Import-Csv` pour importer le fichier, le résultat est un **PSCustomObject** avec les propriétés de note **matemp** et **years** .</span><span class="sxs-lookup"><span data-stu-id="7c302-135">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years** .</span></span>
<span data-ttu-id="7c302-136">Vous pouvez utiliser `Measure-Object` pour calculer les valeurs de ces propriétés, comme n’importe quelle autre propriété d’un objet.</span><span class="sxs-lookup"><span data-stu-id="7c302-136">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="7c302-137">Exemple 6 : mesurer des valeurs booléennes</span><span class="sxs-lookup"><span data-stu-id="7c302-137">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="7c302-138">Cet exemple montre comment `Measure-Object` peut mesurer des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="7c302-138">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="7c302-139">Dans ce cas, elle utilise la propriété **booléenne** **PSIsContainer** pour mesurer l’incidence des dossiers (par rapport aux fichiers) dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="7c302-139">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### <span data-ttu-id="7c302-140">Exemple 7 : chaînes de mesure</span><span class="sxs-lookup"><span data-stu-id="7c302-140">Example 7: Measure strings</span></span>

<span data-ttu-id="7c302-141">L’exemple suivant mesure le nombre de lignes, d’abord une chaîne unique, puis entre plusieurs chaînes.</span><span class="sxs-lookup"><span data-stu-id="7c302-141">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="7c302-142">Le caractère de saut de ligne <code>\`n</code> sépare les chaînes en plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="7c302-142">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### <span data-ttu-id="7c302-143">Exemple 8 : mesurer toutes les valeurs</span><span class="sxs-lookup"><span data-stu-id="7c302-143">Example 8: Measure all the values</span></span>

<span data-ttu-id="7c302-144">À compter de PowerShell 6, le paramètre **AllStats** de `Measure-Object` vous permet de mesurer toutes les statistiques ensemble.</span><span class="sxs-lookup"><span data-stu-id="7c302-144">Beginning in PowerShell 6, the **AllStats** parameter of `Measure-Object` allows you to measure all the statistics together.</span></span>

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### <span data-ttu-id="7c302-145">Exemple 9 : mesurer à l’aide des propriétés scriptblock</span><span class="sxs-lookup"><span data-stu-id="7c302-145">Example 9: Measure using scriptblock properties</span></span>

<span data-ttu-id="7c302-146">À compter de PowerShell 6, `Measure-Object` prend en charge les propriétés **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="7c302-146">Beginning in PowerShell 6, `Measure-Object` supports **ScriptBlock** properties.</span></span> <span data-ttu-id="7c302-147">L’exemple suivant montre comment utiliser une propriété **scriptblock** pour déterminer la taille, en mégaoctets, de tous les fichiers d’un répertoire.</span><span class="sxs-lookup"><span data-stu-id="7c302-147">The following example demonstrates how to use a **ScriptBlock** property to determine the size, in MegaBytes, of all the files in a directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### <span data-ttu-id="7c302-148">Exemple 10 : opérations de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="7c302-148">Example 10: Measure hashtables</span></span>

<span data-ttu-id="7c302-149">À compter de PowerShell 6, `Measure-Object` prend en charge la mesure de l’entrée de la **Hashtable** .</span><span class="sxs-lookup"><span data-stu-id="7c302-149">Beginning in PowerShell 6, `Measure-Object` supports measurement of **hashtable** input.</span></span> <span data-ttu-id="7c302-150">L’exemple suivant détermine la plus grande valeur pour la `num` clé de 3 objets **Hashtable** .</span><span class="sxs-lookup"><span data-stu-id="7c302-150">The following example determines the largest value for the `num` key of 3 **hashtable** objects.</span></span>

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### <span data-ttu-id="7c302-151">Exemple 11 : mesurer l’écart type</span><span class="sxs-lookup"><span data-stu-id="7c302-151">Example 11: Measure the Standard Deviation</span></span>

<span data-ttu-id="7c302-152">À compter de PowerShell 6, `Measure-Object` prend en charge le `-StandardDeviation` paramètre.</span><span class="sxs-lookup"><span data-stu-id="7c302-152">Beginning in PowerShell 6, `Measure-Object` supports the `-StandardDeviation` parameter.</span></span> <span data-ttu-id="7c302-153">L’exemple suivant détermine l' *écart type* pour le processeur utilisé par tous les processus.</span><span class="sxs-lookup"><span data-stu-id="7c302-153">The following example determines the *standard deviation* for the CPU used by all processes.</span></span> <span data-ttu-id="7c302-154">Un écart important indique un petit nombre de processus consommant le plus d’UC.</span><span class="sxs-lookup"><span data-stu-id="7c302-154">A large deviation would indicate a small number of processes consuming the most CPU.</span></span>

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### <span data-ttu-id="7c302-155">Exemple 12 : mesurer à l’aide de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="7c302-155">Example 12: Measure using wildcards</span></span>

<span data-ttu-id="7c302-156">À compter de PowerShell 6, `Measure-Object` prend en charge la mesure des objets à l’aide de caractères génériques dans les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="7c302-156">Beginning in PowerShell 6, `Measure-Object` supports measurement of objects by using wildcards in property names.</span></span> <span data-ttu-id="7c302-157">L’exemple suivant détermine la valeur maximale de tout type d’utilisation de la mémoire paginée parmi un ensemble de processus.</span><span class="sxs-lookup"><span data-stu-id="7c302-157">The following example determines the maximum of any type of paged memory usage among a set of processes.</span></span>

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## <span data-ttu-id="7c302-158">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7c302-158">PARAMETERS</span></span>

### <span data-ttu-id="7c302-159">-Moyenne</span><span class="sxs-lookup"><span data-stu-id="7c302-159">-Average</span></span>

<span data-ttu-id="7c302-160">Indique que l’applet de commande affiche la valeur moyenne des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7c302-160">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-161">-Caractère</span><span class="sxs-lookup"><span data-stu-id="7c302-161">-Character</span></span>

<span data-ttu-id="7c302-162">Indique que l’applet de commande compte le nombre de caractères dans les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7c302-162">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="7c302-163">Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7c302-163">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="7c302-164">Voir l’exemple 7.</span><span class="sxs-lookup"><span data-stu-id="7c302-164">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-165">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="7c302-165">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="7c302-166">Indique que l’applet de commande ignore les espaces blancs dans le nombre de caractères.</span><span class="sxs-lookup"><span data-stu-id="7c302-166">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="7c302-167">Par défaut, les espaces ne sont pas ignorés.</span><span class="sxs-lookup"><span data-stu-id="7c302-167">By default, white space is not ignored.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-168">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7c302-168">-InputObject</span></span>

<span data-ttu-id="7c302-169">Spécifie les objets à mesurer.</span><span class="sxs-lookup"><span data-stu-id="7c302-169">Specifies the objects to be measured.</span></span>
<span data-ttu-id="7c302-170">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="7c302-170">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="7c302-171">Quand vous utilisez le paramètre **InputObject** avec `Measure-Object` , au lieu de rediriger les résultats de la commande vers `Measure-Object` , la valeur **InputObject** est traitée comme un objet unique.</span><span class="sxs-lookup"><span data-stu-id="7c302-171">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="7c302-172">Il est recommandé `Measure-Object` d’utiliser dans le pipeline si vous souhaitez mesurer une collection d’objets selon que les objets ont des valeurs spécifiques dans les propriétés définies.</span><span class="sxs-lookup"><span data-stu-id="7c302-172">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

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

### <span data-ttu-id="7c302-173">-Ligne</span><span class="sxs-lookup"><span data-stu-id="7c302-173">-Line</span></span>

<span data-ttu-id="7c302-174">Indique que l’applet de commande compte le nombre de lignes dans les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7c302-174">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="7c302-175">Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7c302-175">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="7c302-176">Voir l’exemple 7.</span><span class="sxs-lookup"><span data-stu-id="7c302-176">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-177">-Maximum</span><span class="sxs-lookup"><span data-stu-id="7c302-177">-Maximum</span></span>

<span data-ttu-id="7c302-178">Indique que l’applet de commande affiche la valeur maximale des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7c302-178">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-179">-Minimum</span><span class="sxs-lookup"><span data-stu-id="7c302-179">-Minimum</span></span>

<span data-ttu-id="7c302-180">Indique que l’applet de commande affiche la valeur minimale des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7c302-180">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-181">-Propriété</span><span class="sxs-lookup"><span data-stu-id="7c302-181">-Property</span></span>

<span data-ttu-id="7c302-182">Spécifie une ou plusieurs propriétés à mesurer.</span><span class="sxs-lookup"><span data-stu-id="7c302-182">Specifies one or more properties to measure.</span></span> <span data-ttu-id="7c302-183">Si vous ne spécifiez aucune autre mesure, `Measure-Object` compte les objets qui ont les propriétés que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="7c302-183">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

<span data-ttu-id="7c302-184">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="7c302-184">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="7c302-185">La propriété calculée doit être un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="7c302-185">The calculated property must be a script block.</span></span> <span data-ttu-id="7c302-186">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="7c302-186">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7c302-187">-StandardDeviation</span><span class="sxs-lookup"><span data-stu-id="7c302-187">-StandardDeviation</span></span>

<span data-ttu-id="7c302-188">Indique que l’applet de commande affiche l’écart type des valeurs des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7c302-188">Indicates that the cmdlet displays the standard deviation of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-189">-Sum</span><span class="sxs-lookup"><span data-stu-id="7c302-189">-Sum</span></span>

<span data-ttu-id="7c302-190">Indique que l’applet de commande affiche la somme des valeurs des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7c302-190">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-191">-AllStats</span><span class="sxs-lookup"><span data-stu-id="7c302-191">-AllStats</span></span>

<span data-ttu-id="7c302-192">Indique que l’applet de commande affiche toutes les statistiques des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7c302-192">Indicates that the cmdlet displays all the statistics of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-193">-Word</span><span class="sxs-lookup"><span data-stu-id="7c302-193">-Word</span></span>

<span data-ttu-id="7c302-194">Indique que l’applet de commande compte le nombre de mots dans les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7c302-194">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="7c302-195">Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7c302-195">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="7c302-196">Voir l’exemple 7.</span><span class="sxs-lookup"><span data-stu-id="7c302-196">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c302-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c302-197">CommonParameters</span></span>

<span data-ttu-id="7c302-198">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c302-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c302-199">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7c302-199">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c302-200">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7c302-200">INPUTS</span></span>

### <span data-ttu-id="7c302-201">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7c302-201">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7c302-202">Vous pouvez diriger les objets vers `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="7c302-202">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="7c302-203">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7c302-203">OUTPUTS</span></span>

### <span data-ttu-id="7c302-204">Microsoft. PowerShell. Commands. GenericMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="7c302-204">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="7c302-205">Microsoft. PowerShell. Commands. TextMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="7c302-205">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="7c302-206">Si vous utilisez le paramètre **Word** , `Measure-Object` retourne un objet **TextMeasureInfo** .</span><span class="sxs-lookup"><span data-stu-id="7c302-206">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="7c302-207">Sinon, elle retourne un objet **GenericMeasureInfo** .</span><span class="sxs-lookup"><span data-stu-id="7c302-207">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="7c302-208">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7c302-208">NOTES</span></span>

## <span data-ttu-id="7c302-209">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7c302-209">RELATED LINKS</span></span>

[<span data-ttu-id="7c302-210">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="7c302-210">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="7c302-211">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-211">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="7c302-212">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-212">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="7c302-213">Group-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-213">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="7c302-214">New-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-214">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="7c302-215">Select-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-215">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="7c302-216">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-216">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="7c302-217">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-217">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="7c302-218">Where-Object</span><span class="sxs-lookup"><span data-stu-id="7c302-218">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
