---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 5d4a27f1a1949056ca63b9b6a2340bf1226592e0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205894"
---
# <span data-ttu-id="f44ec-103">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-103">Measure-Object</span></span>

## <span data-ttu-id="f44ec-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f44ec-104">SYNOPSIS</span></span>
<span data-ttu-id="f44ec-105">Calcule les propriétés numériques des objets et les caractères, les mots et les lignes dans les objets de chaîne, par exemple les fichiers de texte.</span><span class="sxs-lookup"><span data-stu-id="f44ec-105">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="f44ec-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f44ec-106">SYNTAX</span></span>

### <span data-ttu-id="f44ec-107">GenericMeasure (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f44ec-107">GenericMeasure (Default)</span></span>

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Sum] [-Average] [-Maximum] [-Minimum]
 [<CommonParameters>]
```

### <span data-ttu-id="f44ec-108">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="f44ec-108">TextMeasure</span></span>

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Line] [-Word] [-Character]
 [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="f44ec-109">Description</span><span class="sxs-lookup"><span data-stu-id="f44ec-109">DESCRIPTION</span></span>

<span data-ttu-id="f44ec-110">L' `Measure-Object` applet de commande calcule les valeurs de propriété de certains types d’objets.</span><span class="sxs-lookup"><span data-stu-id="f44ec-110">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="f44ec-111">`Measure-Object` effectue trois types de mesures, selon les paramètres de la commande.</span><span class="sxs-lookup"><span data-stu-id="f44ec-111">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="f44ec-112">L' `Measure-Object` applet de commande effectue des calculs sur les valeurs de propriété des objets.</span><span class="sxs-lookup"><span data-stu-id="f44ec-112">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="f44ec-113">Vous pouvez utiliser `Measure-Object` pour compter les objets ou compter les objets avec une **propriété** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f44ec-113">You can use `Measure-Object` to count objects or count objects with a specified **Property** .</span></span> <span data-ttu-id="f44ec-114">Vous pouvez également utiliser `Measure-Object` pour calculer la valeur **minimale** , la **valeur maximale** , la **somme** , la **StandardDeviation** et la **moyenne** des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="f44ec-114">You can also use `Measure-Object` to calculate the **Minimum** , **Maximum** , **Sum** , **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="f44ec-115">Pour les objets **String** , vous pouvez également utiliser `Measure-Object` pour compter le nombre de lignes, de mots et de caractères.</span><span class="sxs-lookup"><span data-stu-id="f44ec-115">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="f44ec-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f44ec-116">EXAMPLES</span></span>

### <span data-ttu-id="f44ec-117">Exemple 1 : compter les fichiers et les dossiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="f44ec-117">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="f44ec-118">Cette commande compte les fichiers et dossiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f44ec-118">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="f44ec-119">Exemple 2 : mesure des fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="f44ec-119">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="f44ec-120">Cette commande affiche la **valeur minimale** , la **valeur maximale** et la **somme** des tailles de tous les fichiers dans le répertoire actif, ainsi que la taille moyenne d’un fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="f44ec-120">This command displays the **Minimum** , **Maximum** , and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="f44ec-121">Exemple 3 : mesure du texte dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="f44ec-121">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="f44ec-122">Cette commande affiche le nombre de caractères, de mots et de lignes dans le fichier Text.txt.</span><span class="sxs-lookup"><span data-stu-id="f44ec-122">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="f44ec-123">Sans le paramètre **RAW** , `Get-Content` génère le fichier sous la forme d’un tableau de lignes.</span><span class="sxs-lookup"><span data-stu-id="f44ec-123">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="f44ec-124">La première commande utilise `Set-Content` pour ajouter du texte par défaut à un fichier.</span><span class="sxs-lookup"><span data-stu-id="f44ec-124">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="f44ec-125">Exemple 4 : mesurer des objets contenant une propriété spécifiée</span><span class="sxs-lookup"><span data-stu-id="f44ec-125">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="f44ec-126">Cet exemple compte le nombre d’objets qui ont une propriété **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="f44ec-126">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="f44ec-127">Les deux premières commandes récupèrent tous les services et processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f44ec-127">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="f44ec-128">La troisième commande compte le nombre combiné de services et de processus.</span><span class="sxs-lookup"><span data-stu-id="f44ec-128">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="f44ec-129">La dernière commande combine les deux collections et envoie le résultat à `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="f44ec-129">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="f44ec-130">L’objet **System. Diagnostics. Process** n’a pas de propriété **DisplayName** et n’est pas extrait du nombre final.</span><span class="sxs-lookup"><span data-stu-id="f44ec-130">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

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

### <span data-ttu-id="f44ec-131">Exemple 5 : mesurer le contenu d’un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="f44ec-131">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="f44ec-132">Cette commande calcule les années de service en moyenne des employés d'une société.</span><span class="sxs-lookup"><span data-stu-id="f44ec-132">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="f44ec-133">Le `ServiceYrs.csv` fichier est un fichier CSV qui contient le numéro d’employé et les années de service de chaque employé.</span><span class="sxs-lookup"><span data-stu-id="f44ec-133">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="f44ec-134">La première ligne de la table est une ligne d’en-tête de **matemp** , **years** .</span><span class="sxs-lookup"><span data-stu-id="f44ec-134">The first row in the table is a header row of **EmpNo** , **Years** .</span></span>

<span data-ttu-id="f44ec-135">Lorsque vous utilisez `Import-Csv` pour importer le fichier, le résultat est un **PSCustomObject** avec les propriétés de note **matemp** et **years** .</span><span class="sxs-lookup"><span data-stu-id="f44ec-135">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years** .</span></span>
<span data-ttu-id="f44ec-136">Vous pouvez utiliser `Measure-Object` pour calculer les valeurs de ces propriétés, comme n’importe quelle autre propriété d’un objet.</span><span class="sxs-lookup"><span data-stu-id="f44ec-136">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="f44ec-137">Exemple 6 : mesurer des valeurs booléennes</span><span class="sxs-lookup"><span data-stu-id="f44ec-137">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="f44ec-138">Cet exemple montre comment `Measure-Object` peut mesurer des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="f44ec-138">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="f44ec-139">Dans ce cas, elle utilise la propriété **booléenne** **PSIsContainer** pour mesurer l’incidence des dossiers (par rapport aux fichiers) dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f44ec-139">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

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

### <span data-ttu-id="f44ec-140">Exemple 7 : chaînes de mesure</span><span class="sxs-lookup"><span data-stu-id="f44ec-140">Example 7: Measure strings</span></span>

<span data-ttu-id="f44ec-141">L’exemple suivant mesure le nombre de lignes, d’abord une chaîne unique, puis entre plusieurs chaînes.</span><span class="sxs-lookup"><span data-stu-id="f44ec-141">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="f44ec-142">Le caractère de saut de ligne <code>\`n</code> sépare les chaînes en plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="f44ec-142">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

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

## <span data-ttu-id="f44ec-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f44ec-143">PARAMETERS</span></span>

### <span data-ttu-id="f44ec-144">-Moyenne</span><span class="sxs-lookup"><span data-stu-id="f44ec-144">-Average</span></span>

<span data-ttu-id="f44ec-145">Indique que l’applet de commande affiche la valeur moyenne des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="f44ec-145">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

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

### <span data-ttu-id="f44ec-146">-Caractère</span><span class="sxs-lookup"><span data-stu-id="f44ec-146">-Character</span></span>

<span data-ttu-id="f44ec-147">Indique que l’applet de commande compte le nombre de caractères dans les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f44ec-147">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="f44ec-148">Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f44ec-148">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="f44ec-149">Voir l’exemple 7.</span><span class="sxs-lookup"><span data-stu-id="f44ec-149">See Example 7.</span></span>

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

### <span data-ttu-id="f44ec-150">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="f44ec-150">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="f44ec-151">Indique que l’applet de commande ignore les espaces blancs dans le nombre de caractères.</span><span class="sxs-lookup"><span data-stu-id="f44ec-151">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="f44ec-152">Par défaut, les espaces ne sont pas ignorés.</span><span class="sxs-lookup"><span data-stu-id="f44ec-152">By default, white space is not ignored.</span></span>

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

### <span data-ttu-id="f44ec-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f44ec-153">-InputObject</span></span>

<span data-ttu-id="f44ec-154">Spécifie les objets à mesurer.</span><span class="sxs-lookup"><span data-stu-id="f44ec-154">Specifies the objects to be measured.</span></span>
<span data-ttu-id="f44ec-155">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="f44ec-155">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="f44ec-156">Quand vous utilisez le paramètre **InputObject** avec `Measure-Object` , au lieu de rediriger les résultats de la commande vers `Measure-Object` , la valeur **InputObject** est traitée comme un objet unique.</span><span class="sxs-lookup"><span data-stu-id="f44ec-156">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="f44ec-157">Il est recommandé `Measure-Object` d’utiliser dans le pipeline si vous souhaitez mesurer une collection d’objets selon que les objets ont des valeurs spécifiques dans les propriétés définies.</span><span class="sxs-lookup"><span data-stu-id="f44ec-157">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

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

### <span data-ttu-id="f44ec-158">-Ligne</span><span class="sxs-lookup"><span data-stu-id="f44ec-158">-Line</span></span>

<span data-ttu-id="f44ec-159">Indique que l’applet de commande compte le nombre de lignes dans les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f44ec-159">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="f44ec-160">Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f44ec-160">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="f44ec-161">Voir l’exemple 7.</span><span class="sxs-lookup"><span data-stu-id="f44ec-161">See Example 7.</span></span>

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

### <span data-ttu-id="f44ec-162">-Maximum</span><span class="sxs-lookup"><span data-stu-id="f44ec-162">-Maximum</span></span>

<span data-ttu-id="f44ec-163">Indique que l’applet de commande affiche la valeur maximale des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="f44ec-163">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

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

### <span data-ttu-id="f44ec-164">-Minimum</span><span class="sxs-lookup"><span data-stu-id="f44ec-164">-Minimum</span></span>

<span data-ttu-id="f44ec-165">Indique que l’applet de commande affiche la valeur minimale des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="f44ec-165">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

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

### <span data-ttu-id="f44ec-166">-Propriété</span><span class="sxs-lookup"><span data-stu-id="f44ec-166">-Property</span></span>

<span data-ttu-id="f44ec-167">Spécifie une ou plusieurs propriétés à mesurer.</span><span class="sxs-lookup"><span data-stu-id="f44ec-167">Specifies one or more properties to measure.</span></span> <span data-ttu-id="f44ec-168">Si vous ne spécifiez aucune autre mesure, `Measure-Object` compte les objets qui ont les propriétés que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="f44ec-168">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f44ec-169">-Sum</span><span class="sxs-lookup"><span data-stu-id="f44ec-169">-Sum</span></span>

<span data-ttu-id="f44ec-170">Indique que l’applet de commande affiche la somme des valeurs des propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="f44ec-170">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

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

### <span data-ttu-id="f44ec-171">-Word</span><span class="sxs-lookup"><span data-stu-id="f44ec-171">-Word</span></span>

<span data-ttu-id="f44ec-172">Indique que l’applet de commande compte le nombre de mots dans les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f44ec-172">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="f44ec-173">Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f44ec-173">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="f44ec-174">Voir l’exemple 7.</span><span class="sxs-lookup"><span data-stu-id="f44ec-174">See Example 7.</span></span>

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

### <span data-ttu-id="f44ec-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f44ec-175">CommonParameters</span></span>

<span data-ttu-id="f44ec-176">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f44ec-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f44ec-177">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f44ec-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f44ec-178">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f44ec-178">INPUTS</span></span>

### <span data-ttu-id="f44ec-179">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f44ec-179">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f44ec-180">Vous pouvez diriger les objets vers `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="f44ec-180">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="f44ec-181">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f44ec-181">OUTPUTS</span></span>

### <span data-ttu-id="f44ec-182">Microsoft. PowerShell. Commands. GenericMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="f44ec-182">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="f44ec-183">Microsoft. PowerShell. Commands. TextMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="f44ec-183">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="f44ec-184">Si vous utilisez le paramètre **Word** , `Measure-Object` retourne un objet **TextMeasureInfo** .</span><span class="sxs-lookup"><span data-stu-id="f44ec-184">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="f44ec-185">Sinon, elle retourne un objet **GenericMeasureInfo** .</span><span class="sxs-lookup"><span data-stu-id="f44ec-185">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="f44ec-186">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f44ec-186">NOTES</span></span>

## <span data-ttu-id="f44ec-187">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f44ec-187">RELATED LINKS</span></span>

[<span data-ttu-id="f44ec-188">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-188">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="f44ec-189">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-189">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="f44ec-190">Group-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-190">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="f44ec-191">New-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-191">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="f44ec-192">Select-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-192">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="f44ec-193">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-193">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="f44ec-194">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-194">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="f44ec-195">Where-Object</span><span class="sxs-lookup"><span data-stu-id="f44ec-195">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
