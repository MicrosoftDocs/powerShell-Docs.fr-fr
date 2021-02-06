---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 339afab9c817b54a79e2f1b33b7021ecb4fe6a6e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597520"
---
# <span data-ttu-id="c15c0-102">Select-String</span><span class="sxs-lookup"><span data-stu-id="c15c0-102">Select-String</span></span>

## <span data-ttu-id="c15c0-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c15c0-103">SYNOPSIS</span></span>
<span data-ttu-id="c15c0-104">Recherche du texte dans des chaînes et des fichiers.</span><span class="sxs-lookup"><span data-stu-id="c15c0-104">Finds text in strings and files.</span></span>

## <span data-ttu-id="c15c0-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c15c0-105">SYNTAX</span></span>

### <span data-ttu-id="c15c0-106">Fichier (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c15c0-106">File (Default)</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c15c0-107">ObjectRaw</span><span class="sxs-lookup"><span data-stu-id="c15c0-107">ObjectRaw</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c15c0-108">Object</span><span class="sxs-lookup"><span data-stu-id="c15c0-108">Object</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c15c0-109">FileRaw</span><span class="sxs-lookup"><span data-stu-id="c15c0-109">FileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c15c0-110">LiteralFileRaw</span><span class="sxs-lookup"><span data-stu-id="c15c0-110">LiteralFileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c15c0-111">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="c15c0-111">LiteralFile</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="c15c0-112">Description</span><span class="sxs-lookup"><span data-stu-id="c15c0-112">DESCRIPTION</span></span>

<span data-ttu-id="c15c0-113">L' `Select-String` applet de commande recherche des modèles de texte et de texte dans les chaînes et les fichiers d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-113">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="c15c0-114">Vous pouvez utiliser `Select-String` similaire à **grep** dans UNIX ou **findstr.exe** dans Windows.</span><span class="sxs-lookup"><span data-stu-id="c15c0-114">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="c15c0-115">`Select-String` est basé sur des lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="c15c0-115">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="c15c0-116">Par défaut, `Select-String` recherche la première correspondance dans chaque ligne et, pour chaque correspondance, elle affiche le nom du fichier, le numéro de ligne et tout le texte de la ligne contenant la correspondance.</span><span class="sxs-lookup"><span data-stu-id="c15c0-116">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="c15c0-117">Vous pouvez vous demander `Select-String` de Rechercher plusieurs correspondances par ligne, d’afficher du texte avant et après la correspondance, ou d’afficher une valeur booléenne (true ou false) qui indique si une correspondance est trouvée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-117">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="c15c0-118">`Select-String` utilise la correspondance d’expression régulière, mais elle peut également effectuer une correspondance qui recherche le texte que vous spécifiez dans l’entrée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-118">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="c15c0-119">`Select-String` peut afficher toutes les correspondances de texte ou les arrêter après la première correspondance dans chaque fichier d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-119">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="c15c0-120">`Select-String` peut être utilisé pour afficher tout le texte qui ne correspond pas au modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="c15c0-120">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="c15c0-121">Vous pouvez également spécifier que `Select-String` doit attendre un encodage de caractères particulier, par exemple lors de la recherche de fichiers de texte Unicode.</span><span class="sxs-lookup"><span data-stu-id="c15c0-121">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="c15c0-122">`Select-String` utilise la marque d’ordre d’octet (BOM) pour détecter le format d’encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="c15c0-122">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="c15c0-123">Si le fichier n’a pas de nomenclature, il suppose que l’encodage est UTF8.</span><span class="sxs-lookup"><span data-stu-id="c15c0-123">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="c15c0-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c15c0-124">EXAMPLES</span></span>

### <span data-ttu-id="c15c0-125">Exemple 1 : Rechercher une correspondance respectant la casse</span><span class="sxs-lookup"><span data-stu-id="c15c0-125">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="c15c0-126">Cet exemple fait une correspondance sensible à la casse du texte qui a été envoyé dans le pipeline à l’applet de commande `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-126">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="c15c0-127">Les chaînes de texte **Hello** et **Hello** sont envoyées par le pipeline à l’applet de commande `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-127">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="c15c0-128">`Select-String` utilise le paramètre **pattern** pour spécifier **Hello**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-128">`Select-String` uses the **Pattern** parameter to specify **HELLO**.</span></span> <span data-ttu-id="c15c0-129">Le paramètre **CaseSensitive** spécifie que le cas doit correspondre uniquement au modèle majuscule.</span><span class="sxs-lookup"><span data-stu-id="c15c0-129">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="c15c0-130">**SimpleMatch** est un paramètre facultatif qui spécifie que la chaîne dans le modèle n’est pas interprétée comme une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-130">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="c15c0-131">`Select-String` affiche **Hello** dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-131">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="c15c0-132">Exemple 2 : Rechercher des correspondances dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="c15c0-132">Example 2: Find matches in text files</span></span>

<span data-ttu-id="c15c0-133">Cette commande effectue une recherche dans tous les fichiers avec l' `.txt` extension de nom de fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="c15c0-133">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="c15c0-134">La sortie affiche les lignes dans les fichiers qui incluent la chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-134">The output displays the lines in those files that include the specified string.</span></span>

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

<span data-ttu-id="c15c0-135">Dans cet exemple, `Get-Alias` et `Get-Command` sont utilisés avec l' `Out-File` applet de commande pour créer deux fichiers texte dans le répertoire actif, **Alias.txt** et **Command.txt**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-135">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt**.</span></span>

<span data-ttu-id="c15c0-136">`Select-String` utilise le paramètre **path** avec le `*` caractère générique astérisque () pour rechercher dans tous les fichiers du répertoire actif l’extension de nom de fichier `.txt` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-136">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="c15c0-137">Le paramètre **pattern** spécifie le texte à mettre en correspondance avec la fonction **obtient-**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-137">The **Pattern** parameter specifies the text to match **Get-**.</span></span> <span data-ttu-id="c15c0-138">`Select-String` affiche la sortie dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-138">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="c15c0-139">Le nom de fichier et le numéro de ligne précèdent chaque ligne de contenu qui contient une correspondance pour le paramètre de **modèle** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-139">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="c15c0-140">Exemple 3 : Rechercher une correspondance de modèle</span><span class="sxs-lookup"><span data-stu-id="c15c0-140">Example 3: Find a pattern match</span></span>

<span data-ttu-id="c15c0-141">Dans cet exemple, plusieurs fichiers sont recherchés pour trouver des correspondances pour le modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="c15c0-141">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="c15c0-142">Le modèle utilise un quantificateur d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-142">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="c15c0-143">Pour plus d’informations, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c15c0-143">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="c15c0-144">L' `Select-String` applet de commande utilise deux paramètres, **path** et **pattern**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-144">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern**.</span></span> <span data-ttu-id="c15c0-145">Le paramètre **path** utilise la variable `$PSHOME` qui spécifie le répertoire PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-145">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="c15c0-146">Le reste du chemin d’accès comprend le sous-répertoire en **-US** et spécifie chaque `*.txt` fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="c15c0-146">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="c15c0-147">Le paramètre **pattern** spécifie de faire correspondre un point d’interrogation ( `?` ) dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="c15c0-147">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="c15c0-148">Une barre oblique inverse ( `\` ) est utilisée comme caractère d’échappement et est nécessaire parce que le point d’interrogation ( `?` ) est un quantificateur d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-148">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="c15c0-149">`Select-String` affiche la sortie dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-149">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="c15c0-150">Le nom de fichier et le numéro de ligne précèdent chaque ligne de contenu qui contient une correspondance pour le paramètre de **modèle** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-150">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="c15c0-151">Exemple 4 : utiliser Select-String dans une fonction</span><span class="sxs-lookup"><span data-stu-id="c15c0-151">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="c15c0-152">Cet exemple crée une fonction pour rechercher un modèle dans les fichiers d’aide PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-152">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="c15c0-153">Pour cet exemple, la fonction existe uniquement dans la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-153">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="c15c0-154">Une fois la session PowerShell fermée, la fonction est supprimée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-154">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="c15c0-155">Pour plus d’informations, consultez [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span><span class="sxs-lookup"><span data-stu-id="c15c0-155">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

<span data-ttu-id="c15c0-156">La fonction est créée sur la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-156">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="c15c0-157">La `Function` commande utilise le nom **Search-Help**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-157">The `Function` command uses the name **Search-Help**.</span></span> <span data-ttu-id="c15c0-158">Appuyez sur **entrée** pour commencer à ajouter des instructions à la fonction.</span><span class="sxs-lookup"><span data-stu-id="c15c0-158">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="c15c0-159">À partir de l' `>>` invite, ajoutez chaque instruction et appuyez sur **entrée** comme indiqué dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="c15c0-159">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="c15c0-160">Une fois le crochet fermant ajouté, vous êtes redirigé vers une invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-160">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="c15c0-161">La fonction contient deux commandes.</span><span class="sxs-lookup"><span data-stu-id="c15c0-161">The function contains two commands.</span></span> <span data-ttu-id="c15c0-162">La `$PSHelp` variable stocke le chemin d’accès aux fichiers d’aide PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-162">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="c15c0-163">`$PSHOME` est le répertoire d’installation de PowerShell avec le sous **-répertoire en-US** qui spécifie chaque `*.txt` fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="c15c0-163">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="c15c0-164">La `Select-String` commande dans la fonction utilise les paramètres **path** et **pattern** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-164">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="c15c0-165">Le paramètre **path** utilise la `$PSHelp` variable pour récupérer le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="c15c0-165">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="c15c0-166">Le paramètre **pattern** utilise la chaîne **about_** comme critère de recherche.</span><span class="sxs-lookup"><span data-stu-id="c15c0-166">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="c15c0-167">Pour exécuter la fonction, tapez `Search-Help` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-167">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="c15c0-168">La commande de la fonction `Select-String` affiche la sortie dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-168">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="c15c0-169">Exemple 5 : Rechercher une chaîne dans un journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="c15c0-169">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="c15c0-170">Cet exemple recherche une chaîne dans un journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="c15c0-170">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="c15c0-171">La variable `$_` représente l’objet actuel dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="c15c0-171">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="c15c0-172">Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c15c0-172">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="c15c0-173">L' `Get-WinEvent` applet de commande utilise le paramètre **logname** pour spécifier le journal des applications.</span><span class="sxs-lookup"><span data-stu-id="c15c0-173">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="c15c0-174">Le paramètre **MaxEvents** obtient les événements les plus récents 50 du journal.</span><span class="sxs-lookup"><span data-stu-id="c15c0-174">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="c15c0-175">Le contenu du journal est stocké dans la variable nommée `$Events` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-175">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="c15c0-176">La `$Events` variable est envoyée dans le pipeline à l’applet de commande `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-176">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="c15c0-177">`Select-String` utilise le paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-177">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="c15c0-178">La `$_` variable représente l’objet actuel et `message` est une propriété de l’événement.</span><span class="sxs-lookup"><span data-stu-id="c15c0-178">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="c15c0-179">Le paramètre de **modèle** importe **la chaîne et** recherche des correspondances dans `$_.message` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-179">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="c15c0-180">`Select-String` affiche la sortie dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-180">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="c15c0-181">Exemple 6 : Rechercher une chaîne dans les sous-répertoires</span><span class="sxs-lookup"><span data-stu-id="c15c0-181">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="c15c0-182">Cet exemple recherche une chaîne de texte spécifique dans un répertoire et tous ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="c15c0-182">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="c15c0-183">`Get-ChildItem` utilise le paramètre **path** pour spécifier **C:\Windows\System32 \* . txt**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-183">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt**.</span></span> <span data-ttu-id="c15c0-184">Le paramètre **recurse** comprend les sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="c15c0-184">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="c15c0-185">Les objets sont envoyés dans le pipeline à `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-185">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="c15c0-186">`Select-String` utilise le paramètre **pattern** et spécifie la chaîne **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-186">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft**.</span></span> <span data-ttu-id="c15c0-187">Le paramètre **CaseSensitive** est utilisé pour faire correspondre la casse exacte de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="c15c0-187">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="c15c0-188">`Select-String` affiche la sortie dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-188">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="c15c0-189">Selon vos autorisations, vous pouvez voir des messages d' **accès refusé** dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="c15c0-189">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="c15c0-190">Exemple 7 : Rechercher des chaînes qui ne correspondent pas à un modèle</span><span class="sxs-lookup"><span data-stu-id="c15c0-190">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="c15c0-191">Cet exemple montre comment exclure des lignes de données qui ne correspondent pas à un modèle.</span><span class="sxs-lookup"><span data-stu-id="c15c0-191">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="c15c0-192">L' `Get-Command` applet de commande envoie des objets dans le pipeline au `Out-File` pour créer le fichier **Command.txt** dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="c15c0-192">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="c15c0-193">`Select-String` utilise le paramètre **path** pour spécifier le fichier **Command.txt** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-193">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="c15c0-194">Le paramètre **pattern** spécifie la **valeur** **obtenue** et définie comme modèle de recherche.</span><span class="sxs-lookup"><span data-stu-id="c15c0-194">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="c15c0-195">Le paramètre **NotMatch** exclut les résultats de l' **extraction** et de la **définition** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-195">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="c15c0-196">`Select-String` affiche la sortie dans la console PowerShell qui n’inclut pas l' **extraction** ou la **définition**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-196">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set**.</span></span>

### <span data-ttu-id="c15c0-197">Exemple 8 : Rechercher des lignes avant et après une correspondance</span><span class="sxs-lookup"><span data-stu-id="c15c0-197">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="c15c0-198">Cet exemple montre comment récupérer les lignes avant et après le modèle correspondant.</span><span class="sxs-lookup"><span data-stu-id="c15c0-198">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

<span data-ttu-id="c15c0-199">L' `Get-Command` applet de commande envoie des objets dans le pipeline au `Out-File` pour créer le fichier **Command.txt** dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="c15c0-199">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="c15c0-200">`Select-String` utilise le paramètre **path** pour spécifier le fichier **Command.txt** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-200">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="c15c0-201">Le paramètre **pattern** spécifie le modèle de recherche **« -Computer »** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-201">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="c15c0-202">Le paramètre **Context** utilise deux valeurs, avant et après, et marque les correspondances de modèle dans la sortie avec un chevron ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="c15c0-202">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="c15c0-203">Le paramètre **Context** génère les deux lignes avant le premier Matching pattern et trois lignes après le dernier modèle match.</span><span class="sxs-lookup"><span data-stu-id="c15c0-203">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="c15c0-204">Exemple 9 : Rechercher toutes les correspondances de modèle</span><span class="sxs-lookup"><span data-stu-id="c15c0-204">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="c15c0-205">Cet exemple montre comment le paramètre **AllMatches** recherche chaque correspondance de modèle dans une ligne de texte.</span><span class="sxs-lookup"><span data-stu-id="c15c0-205">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="c15c0-206">Par défaut, `Select-String` recherche uniquement la première occurrence d’un modèle dans une ligne de texte.</span><span class="sxs-lookup"><span data-stu-id="c15c0-206">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="c15c0-207">Cet exemple utilise des propriétés d’objet qui se trouvent dans l’applet de commande `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-207">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

<span data-ttu-id="c15c0-208">L' `Get-ChildItem` applet de commande utilise le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-208">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="c15c0-209">Le paramètre **path** utilise la variable `$PSHOME` qui spécifie le répertoire PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-209">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="c15c0-210">Le reste du chemin d’accès comprend le sous-répertoire en **-US** et spécifie chaque `*.txt` fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="c15c0-210">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="c15c0-211">Les `Get-ChildItem` objets sont stockés dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="c15c0-211">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="c15c0-212">La `$A` variable est envoyée dans le pipeline à l’applet de commande `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-212">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="c15c0-213">`Select-String` utilise le paramètre **pattern** pour rechercher la chaîne **PowerShell** dans chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="c15c0-213">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell**.</span></span>

<span data-ttu-id="c15c0-214">À partir de la ligne de commande PowerShell, le contenu de la `$A` variable est affiché.</span><span class="sxs-lookup"><span data-stu-id="c15c0-214">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="c15c0-215">Il y a une ligne qui contient deux occurrences de la chaîne **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-215">There's a line that contains two occurrences of the string **PowerShell**.</span></span>

<span data-ttu-id="c15c0-216">La `$A.Matches` propriété répertorie la première occurrence du modèle **PowerShell** sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="c15c0-216">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="c15c0-217">La `$A.Matches.Length` propriété compte la première occurrence du modèle **PowerShell** sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="c15c0-217">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="c15c0-218">La `$B` variable utilise les mêmes `Get-ChildItem` applets de commande et `Select-String` , mais ajoute le paramètre **AllMatches** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-218">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="c15c0-219">**AllMatches** recherche chaque occurrence du modèle **PowerShell** sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="c15c0-219">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="c15c0-220">Les objets stockés dans les `$A` `$B` variables et sont identiques.</span><span class="sxs-lookup"><span data-stu-id="c15c0-220">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="c15c0-221">La `$B.Matches.Length` propriété augmente, car pour chaque ligne, chaque occurrence du modèle **PowerShell** est comptée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-221">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="c15c0-222">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c15c0-222">PARAMETERS</span></span>

### <span data-ttu-id="c15c0-223">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="c15c0-223">-AllMatches</span></span>

<span data-ttu-id="c15c0-224">Indique que l’applet de commande recherche plusieurs correspondances dans chaque ligne de texte.</span><span class="sxs-lookup"><span data-stu-id="c15c0-224">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="c15c0-225">Sans ce paramètre, `Select-String` recherche uniquement la première correspondance dans chaque ligne de texte.</span><span class="sxs-lookup"><span data-stu-id="c15c0-225">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="c15c0-226">Lorsque `Select-String` trouve plusieurs correspondances dans une ligne de texte, il n’émet toujours qu’un seul objet **MatchInfo** pour la ligne, mais la propriété **matches** de l’objet contient toutes les correspondances.</span><span class="sxs-lookup"><span data-stu-id="c15c0-226">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="c15c0-227">Ce paramètre est ignoré lorsqu’il est utilisé en association avec le paramètre **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-227">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="c15c0-228">Si vous souhaitez retourner toutes les correspondances et que le modèle que vous recherchez contient des caractères d’expression régulière, vous devez placer ces caractères dans une séquence d’échappement plutôt que d’utiliser **SimpleMatch**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-228">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch**.</span></span> <span data-ttu-id="c15c0-229">Pour plus d’informations sur les expressions régulières d’échappement, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) .</span><span class="sxs-lookup"><span data-stu-id="c15c0-229">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

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

### <span data-ttu-id="c15c0-230">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="c15c0-230">-CaseSensitive</span></span>

<span data-ttu-id="c15c0-231">Indique que l’applet de commande correspond à la casse.</span><span class="sxs-lookup"><span data-stu-id="c15c0-231">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="c15c0-232">Par défaut, les correspondances ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="c15c0-232">By default, matches aren't case-sensitive.</span></span>

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

### <span data-ttu-id="c15c0-233">-Context</span><span class="sxs-lookup"><span data-stu-id="c15c0-233">-Context</span></span>

<span data-ttu-id="c15c0-234">Capture le nombre spécifié de lignes avant et après la ligne qui correspond au modèle.</span><span class="sxs-lookup"><span data-stu-id="c15c0-234">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="c15c0-235">Si vous entrez un nombre comme valeur de ce paramètre, ce nombre détermine le nombre de lignes capturées avant et après la correspondance.</span><span class="sxs-lookup"><span data-stu-id="c15c0-235">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="c15c0-236">Si vous entrez deux nombres comme valeur, le premier nombre détermine le nombre de lignes avant la correspondance, et le deuxième nombre détermine le nombre de lignes après la correspondance.</span><span class="sxs-lookup"><span data-stu-id="c15c0-236">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="c15c0-237">Par exemple, `-Context 2,3`.</span><span class="sxs-lookup"><span data-stu-id="c15c0-237">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="c15c0-238">Dans l’affichage par défaut, les lignes avec une correspondance sont indiquées par un crochet angulaire à droite ( `>` ) (ASCII 62) dans la première colonne de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="c15c0-238">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="c15c0-239">Les lignes non marquées constituent le contexte.</span><span class="sxs-lookup"><span data-stu-id="c15c0-239">Unmarked lines are the context.</span></span>

<span data-ttu-id="c15c0-240">Le paramètre de **contexte** ne change pas le nombre d’objets générés par `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-240">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="c15c0-241">`Select-String` génère un objet [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) pour chaque correspondance.</span><span class="sxs-lookup"><span data-stu-id="c15c0-241">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="c15c0-242">Le contexte est stocké sous la forme d’un tableau de chaînes dans la propriété de **contexte** de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c15c0-242">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="c15c0-243">Quand la sortie d’une `Select-String` commande est envoyée au pipeline vers une autre `Select-String` commande, la commande réceptrice recherche uniquement le texte dans la ligne correspondante.</span><span class="sxs-lookup"><span data-stu-id="c15c0-243">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="c15c0-244">La ligne mise en correspondance correspond à la valeur de la propriété **line** de l’objet **MatchInfo** , et non au texte des lignes de contexte.</span><span class="sxs-lookup"><span data-stu-id="c15c0-244">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="c15c0-245">Par conséquent, le paramètre de **contexte** n’est pas valide dans la commande de réception `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-245">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="c15c0-246">Lorsque le contexte comprend une correspondance, l’objet **MatchInfo** pour chaque correspondance comprend toutes les lignes de contexte, mais les lignes qui se chevauchent n’apparaissent qu’une seule fois dans l’affichage.</span><span class="sxs-lookup"><span data-stu-id="c15c0-246">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c15c0-247">-Culture</span><span class="sxs-lookup"><span data-stu-id="c15c0-247">-Culture</span></span>

<span data-ttu-id="c15c0-248">Spécifie un nom de culture qui correspond au modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="c15c0-248">Specifies a culture name to match the specified pattern.</span></span> <span data-ttu-id="c15c0-249">Le paramètre **culture** doit être utilisé avec le paramètre **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-249">The **Culture** parameter must be used with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="c15c0-250">Le comportement par défaut utilise la culture de l’instance d’exécution PowerShell actuelle (session).</span><span class="sxs-lookup"><span data-stu-id="c15c0-250">The default behavior uses the culture of the current PowerShell runspace (session).</span></span>

<span data-ttu-id="c15c0-251">Pour obtenir la liste de toutes les cultures prises en charge, utilisez la `Get-Culture -ListAvailable` commande.</span><span class="sxs-lookup"><span data-stu-id="c15c0-251">To get a list of all supported cultures, use `Get-Culture -ListAvailable` command.</span></span>

<span data-ttu-id="c15c0-252">En outre, ce paramètre accepte les arguments suivants :</span><span class="sxs-lookup"><span data-stu-id="c15c0-252">In addition, this parameter accepts the following arguments:</span></span>

- <span data-ttu-id="c15c0-253">CurrentCulture, qui est la valeur par défaut ;</span><span class="sxs-lookup"><span data-stu-id="c15c0-253">CurrentCulture, that is default;</span></span>
- <span data-ttu-id="c15c0-254">Ordinal, autrement dit une comparaison binaire non linguistique ;</span><span class="sxs-lookup"><span data-stu-id="c15c0-254">Ordinal, that is non-linguistic binary comparison;</span></span>
- <span data-ttu-id="c15c0-255">Invariant, qui est une comparaison indépendante de la culture.</span><span class="sxs-lookup"><span data-stu-id="c15c0-255">Invariant, that is culture independent comparison.</span></span>

<span data-ttu-id="c15c0-256">Avec la `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` commande, vous allez obtenir une comparaison binaire plus rapide.</span><span class="sxs-lookup"><span data-stu-id="c15c0-256">With `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` command you gets fastest binary comparison.</span></span>

<span data-ttu-id="c15c0-257">Le paramètre **culture** utilise la saisie semi-automatique via la touche Tab pour faire défiler la liste des arguments qui spécifient les cultures disponibles.</span><span class="sxs-lookup"><span data-stu-id="c15c0-257">The **Culture** parameter uses tab completion to scroll through the list of arguments that specify the available cultures.</span></span> <span data-ttu-id="c15c0-258">Pour répertorier tous les arguments disponibles, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c15c0-258">To list all available arguments, use the following command:</span></span>

`(Get-Command Select-String).Parameters.Culture.Attributes.ValidValues`

<span data-ttu-id="c15c0-259">Pour plus d’informations sur la propriété .NET CultureInfo.Name, consultez [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name).</span><span class="sxs-lookup"><span data-stu-id="c15c0-259">For more information about .NET CultureInfo.Name property, see [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name).</span></span>

<span data-ttu-id="c15c0-260">Le paramètre **culture** a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c15c0-260">The **Culture** parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Culture of the current PowerShell session
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c15c0-261">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c15c0-261">-Encoding</span></span>

<span data-ttu-id="c15c0-262">Spécifie le type de codage du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="c15c0-262">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="c15c0-263">La valeur par défaut est `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="c15c0-263">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="c15c0-264">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c15c0-264">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c15c0-265">`ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="c15c0-265">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c15c0-266">`bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="c15c0-266">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c15c0-267">`bigendianutf32`: Encode au format UTF-32 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="c15c0-267">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c15c0-268">`oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.</span><span class="sxs-lookup"><span data-stu-id="c15c0-268">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="c15c0-269">`unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="c15c0-269">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="c15c0-270">`utf7`: Encode au format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="c15c0-270">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="c15c0-271">`utf8`: Encode au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c15c0-271">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="c15c0-272">`utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="c15c0-272">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c15c0-273">`utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)</span><span class="sxs-lookup"><span data-stu-id="c15c0-273">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c15c0-274">`utf32`: Encode au format UTF-32.</span><span class="sxs-lookup"><span data-stu-id="c15c0-274">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="c15c0-275">À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="c15c0-275">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="c15c0-276">Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="c15c0-276">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="c15c0-277">**UTF-7** _ n’est plus recommandé pour l’utilisation de.</span><span class="sxs-lookup"><span data-stu-id="c15c0-277">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="c15c0-278">Dans PowerShell 7,1, un avertissement est écrit si vous spécifiez `utf7` pour le paramètre _ \*Encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="c15c0-278">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c15c0-279">-Exclude</span><span class="sxs-lookup"><span data-stu-id="c15c0-279">-Exclude</span></span>

<span data-ttu-id="c15c0-280">Exclure les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c15c0-280">Exclude the specified items.</span></span> <span data-ttu-id="c15c0-281">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-281">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c15c0-282">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-282">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c15c0-283">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c15c0-283">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c15c0-284">-Include</span><span class="sxs-lookup"><span data-stu-id="c15c0-284">-Include</span></span>

<span data-ttu-id="c15c0-285">Inclut les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c15c0-285">Includes the specified items.</span></span> <span data-ttu-id="c15c0-286">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-286">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c15c0-287">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-287">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c15c0-288">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c15c0-288">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c15c0-289">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c15c0-289">-InputObject</span></span>

<span data-ttu-id="c15c0-290">Spécifie le texte à rechercher.</span><span class="sxs-lookup"><span data-stu-id="c15c0-290">Specifies the text to be searched.</span></span> <span data-ttu-id="c15c0-291">Entrez une variable contenant le texte, ou tapez une commande ou une expression qui obtient le texte.</span><span class="sxs-lookup"><span data-stu-id="c15c0-291">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="c15c0-292">L’utilisation du paramètre **InputObject** n’est pas identique à l’envoi de chaînes vers le pipeline dans le pipeline `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-292">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="c15c0-293">Lorsque vous dirigez plusieurs chaînes vers l’applet de commande `Select-String` , celle-ci recherche le texte spécifié dans chaque chaîne et retourne chaque chaîne qui contient le texte recherché.</span><span class="sxs-lookup"><span data-stu-id="c15c0-293">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="c15c0-294">Quand vous utilisez le paramètre **InputObject** pour envoyer une collection de chaînes, `Select-String` traite la collection comme une chaîne combinée unique.</span><span class="sxs-lookup"><span data-stu-id="c15c0-294">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="c15c0-295">`Select-String` retourne les chaînes en tant qu’unité si le texte recherché est trouvé dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c15c0-295">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object, ObjectRaw
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c15c0-296">-List</span><span class="sxs-lookup"><span data-stu-id="c15c0-296">-List</span></span>

<span data-ttu-id="c15c0-297">Seule la première instance du texte correspondant est retournée à partir de chaque fichier d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-297">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="c15c0-298">Il s’agit de la méthode la plus efficace pour récupérer une liste de fichiers dont le contenu correspond à l’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-298">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="c15c0-299">Par défaut, `Select-String` retourne un objet **MatchInfo** pour chaque correspondance trouvée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-299">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

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

### <span data-ttu-id="c15c0-300">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c15c0-300">-LiteralPath</span></span>

<span data-ttu-id="c15c0-301">Spécifie le chemin d'accès aux fichiers où effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="c15c0-301">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="c15c0-302">La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-302">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="c15c0-303">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="c15c0-303">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c15c0-304">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="c15c0-304">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c15c0-305">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="c15c0-305">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="c15c0-306">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="c15c0-306">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFileRaw, LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c15c0-307">-Importance</span><span class="sxs-lookup"><span data-stu-id="c15c0-307">-NoEmphasis</span></span>

<span data-ttu-id="c15c0-308">Par défaut, `Select-String` met en surbrillance la chaîne qui correspond au modèle que vous avez recherché avec le paramètre **pattern** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-308">By default, `Select-String` highlights the string that matches the pattern you searched for with the **Pattern** parameter.</span></span> <span data-ttu-id="c15c0-309">Le paramètre **norelief** désactive la mise en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="c15c0-309">The **NoEmphasis** parameter disables the highlighting.</span></span>

<span data-ttu-id="c15c0-310">L’accentuation utilise des couleurs négatives en fonction de vos couleurs d’arrière-plan et de texte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c15c0-310">The emphasis uses negative colors based on your PowerShell background and text colors.</span></span> <span data-ttu-id="c15c0-311">Par exemple, si vos couleurs PowerShell sont un arrière-plan noir avec du texte blanc.</span><span class="sxs-lookup"><span data-stu-id="c15c0-311">For example, if your PowerShell colors are a black background with white text.</span></span> <span data-ttu-id="c15c0-312">L’accent est un arrière-plan blanc avec du texte noir.</span><span class="sxs-lookup"><span data-stu-id="c15c0-312">The emphasis is a white background with black text.</span></span>

<span data-ttu-id="c15c0-313">Ce paramètre a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c15c0-313">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="c15c0-314">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="c15c0-314">-NotMatch</span></span>

<span data-ttu-id="c15c0-315">Le paramètre **NotMatch** recherche le texte qui ne correspond pas au modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="c15c0-315">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

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

### <span data-ttu-id="c15c0-316">-Path</span><span class="sxs-lookup"><span data-stu-id="c15c0-316">-Path</span></span>

<span data-ttu-id="c15c0-317">Spécifie le chemin d’accès aux fichiers à rechercher.</span><span class="sxs-lookup"><span data-stu-id="c15c0-317">Specifies the path to the files to search.</span></span> <span data-ttu-id="c15c0-318">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c15c0-318">Wildcards are permitted.</span></span> <span data-ttu-id="c15c0-319">L'emplacement par défaut est le répertoire local.</span><span class="sxs-lookup"><span data-stu-id="c15c0-319">The default location is the local directory.</span></span>

<span data-ttu-id="c15c0-320">Spécifiez les fichiers dans le répertoire, tels que `log1.txt` , `*.doc` ou `*.*` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-320">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="c15c0-321">Si vous spécifiez seulement un répertoire, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="c15c0-321">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File, FileRaw
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c15c0-322">-Modèle</span><span class="sxs-lookup"><span data-stu-id="c15c0-322">-Pattern</span></span>

<span data-ttu-id="c15c0-323">Spécifie le texte à rechercher sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="c15c0-323">Specifies the text to find on each line.</span></span> <span data-ttu-id="c15c0-324">La valeur de modèle est traitée comme une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-324">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="c15c0-325">Pour en savoir plus sur les expressions régulières, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c15c0-325">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c15c0-326">-Quiet</span><span class="sxs-lookup"><span data-stu-id="c15c0-326">-Quiet</span></span>

<span data-ttu-id="c15c0-327">Indique que l’applet de commande retourne une valeur booléenne (true ou false) au lieu d’un objet **MatchInfo** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-327">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="c15c0-328">La valeur est true si le modèle est trouvé ; Sinon, la valeur est false.</span><span class="sxs-lookup"><span data-stu-id="c15c0-328">The value is True if the pattern is found; otherwise the value is False.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File, Object, LiteralFile
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c15c0-329">-RAW</span><span class="sxs-lookup"><span data-stu-id="c15c0-329">-Raw</span></span>

<span data-ttu-id="c15c0-330">Fait en sorte que l’applet de commande génère uniquement les chaînes correspondantes, plutôt que les objets **MatchInfo** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-330">Causes the cmdlet to output only the matching strings, rather than **MatchInfo** objects.</span></span> <span data-ttu-id="c15c0-331">Il s’agit du comportement qui est le plus semblable aux commandes d’UNIX **grep** ou Windows **findstr.exe** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-331">This is the results in behavior that's the most similar to the Unix **grep** or Windows **findstr.exe** commands.</span></span>

<span data-ttu-id="c15c0-332">Ce paramètre a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c15c0-332">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ObjectRaw, FileRaw, LiteralFileRaw
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c15c0-333">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="c15c0-333">-SimpleMatch</span></span>

<span data-ttu-id="c15c0-334">Indique que l’applet de commande utilise une correspondance simple plutôt qu’une correspondance d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-334">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="c15c0-335">Dans une correspondance simple, `Select-String` recherche l’entrée pour le texte dans le paramètre **pattern** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-335">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="c15c0-336">Elle n’interprète pas la valeur du paramètre **pattern** comme une instruction d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-336">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="c15c0-337">En outre, quand **SimpleMatch** est utilisé, la propriété **matches** de l’objet **MatchInfo** retourné est vide.</span><span class="sxs-lookup"><span data-stu-id="c15c0-337">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="c15c0-338">Lorsque ce paramètre est utilisé avec le paramètre **AllMatches** , le **AllMatches** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="c15c0-338">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

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

### <span data-ttu-id="c15c0-339">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c15c0-339">CommonParameters</span></span>

<span data-ttu-id="c15c0-340">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c15c0-340">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c15c0-341">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c15c0-341">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c15c0-342">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c15c0-342">INPUTS</span></span>

### <span data-ttu-id="c15c0-343">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="c15c0-343">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c15c0-344">Vous pouvez diriger n’importe quel objet ayant une méthode **ToString** vers `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-344">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="c15c0-345">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c15c0-345">OUTPUTS</span></span>

### <span data-ttu-id="c15c0-346">Microsoft. PowerShell. Commands. MatchInfo, System. Boolean, System. String</span><span class="sxs-lookup"><span data-stu-id="c15c0-346">Microsoft.PowerShell.Commands.MatchInfo, System.Boolean, System.String</span></span>

<span data-ttu-id="c15c0-347">Par défaut, la sortie est un ensemble d’objets **MatchInfo** avec un objet pour chaque correspondance trouvée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-347">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="c15c0-348">Si vous utilisez le paramètre **Quiet** , la sortie est une valeur **booléenne** indiquant si le modèle a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="c15c0-348">If you use the **Quiet** parameter, the output is a **Boolean** value indicating whether the pattern was found.</span></span>
<span data-ttu-id="c15c0-349">Si vous utilisez le paramètre **RAW** , la sortie est un ensemble d’objets **String** qui correspondent au modèle.</span><span class="sxs-lookup"><span data-stu-id="c15c0-349">If you use the **Raw** parameter, the output is a set of **String** objects that match the pattern.</span></span>

## <span data-ttu-id="c15c0-350">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c15c0-350">NOTES</span></span>

<span data-ttu-id="c15c0-351">`Select-String` est similaire à **grep** dans UNIX ou **findstr.exe** dans Windows.</span><span class="sxs-lookup"><span data-stu-id="c15c0-351">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="c15c0-352">L’alias **SLS** pour l' `Select-String` applet de commande a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c15c0-352">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="c15c0-353">Selon les [verbes approuvés pour les commandes PowerShell](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), le préfixe d’alias officiel pour les `Select-*` applets de commande est `sc` , et non `sl` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-353">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="c15c0-354">Par conséquent, l’alias approprié pour `Select-String` doit être `scs` , et non `sls` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-354">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="c15c0-355">Il s’agit d’une exception à cette règle.</span><span class="sxs-lookup"><span data-stu-id="c15c0-355">This is an exception to this rule.</span></span>

<span data-ttu-id="c15c0-356">Pour utiliser `Select-String` , tapez le texte que vous souhaitez rechercher comme valeur du paramètre **pattern** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-356">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="c15c0-357">Pour spécifier le texte à rechercher, utilisez les critères suivants :</span><span class="sxs-lookup"><span data-stu-id="c15c0-357">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="c15c0-358">Tapez le texte dans une chaîne entre guillemets, puis dirigez-le vers `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="c15c0-358">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="c15c0-359">Stockez une chaîne de texte dans une variable, puis spécifiez la variable comme valeur du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-359">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="c15c0-360">Si le texte est stocké dans des fichiers, utilisez le paramètre **path** pour spécifier le chemin d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="c15c0-360">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="c15c0-361">Par défaut, `Select-String` interprète la valeur du paramètre **pattern** comme une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-361">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="c15c0-362">Pour plus d’informations, consultez [about_regular_expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c15c0-362">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="c15c0-363">Vous pouvez utiliser le paramètre **SimpleMatch** pour remplacer la correspondance d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="c15c0-363">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="c15c0-364">Le paramètre **SimpleMatch** recherche des instances de la valeur du paramètre **pattern** dans l’entrée.</span><span class="sxs-lookup"><span data-stu-id="c15c0-364">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="c15c0-365">La sortie par défaut de `Select-String` est un objet **MatchInfo** , qui contient des informations détaillées sur les correspondances.</span><span class="sxs-lookup"><span data-stu-id="c15c0-365">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="c15c0-366">Les informations contenues dans l’objet sont utiles quand vous recherchez du texte dans des fichiers, car les objets **MatchInfo** ont des propriétés telles que **filename** et **line**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-366">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line**.</span></span> <span data-ttu-id="c15c0-367">Lorsque l’entrée ne provient pas du fichier, la valeur de ces paramètres est **InputStream**.</span><span class="sxs-lookup"><span data-stu-id="c15c0-367">When the input isn't from the file, the value of these parameters is **InputStream**.</span></span>

<span data-ttu-id="c15c0-368">Si vous n’avez pas besoin des informations contenues dans l’objet **MatchInfo** , utilisez le paramètre **Quiet** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-368">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="c15c0-369">Le paramètre **Quiet** retourne une valeur booléenne (true ou false) pour indiquer s’il a trouvé une correspondance, au lieu d’un objet **MatchInfo** .</span><span class="sxs-lookup"><span data-stu-id="c15c0-369">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="c15c0-370">Lors `Select-String` de la correspondance d’expressions, utilise la culture actuelle définie pour le système.</span><span class="sxs-lookup"><span data-stu-id="c15c0-370">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="c15c0-371">Pour trouver la culture actuelle, utilisez l' `Get-Culture` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c15c0-371">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="c15c0-372">Pour rechercher les propriétés d’un objet **MatchInfo** , tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c15c0-372">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="c15c0-373">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c15c0-373">RELATED LINKS</span></span>

[<span data-ttu-id="c15c0-374">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="c15c0-374">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="c15c0-375">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="c15c0-375">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="c15c0-376">about_Functions</span><span class="sxs-lookup"><span data-stu-id="c15c0-376">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="c15c0-377">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c15c0-377">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="c15c0-378">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="c15c0-378">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="c15c0-379">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="c15c0-379">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="c15c0-380">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="c15c0-380">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="c15c0-381">Get-Command</span><span class="sxs-lookup"><span data-stu-id="c15c0-381">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="c15c0-382">Get-Member</span><span class="sxs-lookup"><span data-stu-id="c15c0-382">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="c15c0-383">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="c15c0-383">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="c15c0-384">Out-File</span><span class="sxs-lookup"><span data-stu-id="c15c0-384">Out-File</span></span>](Out-File.md)

