---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 5fd1ff9760cbddeb0c5c29052caf0f36d6d760d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598356"
---
# <span data-ttu-id="8c406-102">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-102">Tee-Object</span></span>

## <span data-ttu-id="8c406-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8c406-103">SYNOPSIS</span></span>
<span data-ttu-id="8c406-104">Enregistre la sortie de la commande dans un fichier ou dans une variable, puis l'envoie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8c406-104">Saves command output in a file or variable and also sends it down the pipeline.</span></span>

## <span data-ttu-id="8c406-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8c406-105">SYNTAX</span></span>

### <span data-ttu-id="8c406-106">Fichier (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8c406-106">File (Default)</span></span>

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### <span data-ttu-id="8c406-107">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="8c406-107">LiteralFile</span></span>

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### <span data-ttu-id="8c406-108">Variable</span><span class="sxs-lookup"><span data-stu-id="8c406-108">Variable</span></span>

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## <span data-ttu-id="8c406-109">Description</span><span class="sxs-lookup"><span data-stu-id="8c406-109">DESCRIPTION</span></span>

<span data-ttu-id="8c406-110">L' `Tee-Object` applet de commande redirige la sortie, autrement dit, elle envoie la sortie d’une commande dans deux directions (comme la lettre T).</span><span class="sxs-lookup"><span data-stu-id="8c406-110">The `Tee-Object` cmdlet redirects output, that is, it sends the output of a command in two directions (like the letter T).</span></span> <span data-ttu-id="8c406-111">Elle stocke la sortie dans un fichier ou dans une variable, puis l'envoie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8c406-111">It stores the output in a file or variable and also sends it down the pipeline.</span></span> <span data-ttu-id="8c406-112">Si `Tee-Object` est la dernière commande du pipeline, le résultat de la commande s’affiche à l’invite.</span><span class="sxs-lookup"><span data-stu-id="8c406-112">If `Tee-Object` is the last command in the pipeline, the command output is displayed at the prompt.</span></span>

## <span data-ttu-id="8c406-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8c406-113">EXAMPLES</span></span>

### <span data-ttu-id="8c406-114">Exemple 1 : traiter les processus dans un fichier et dans la console</span><span class="sxs-lookup"><span data-stu-id="8c406-114">Example 1: Output processes to a file and to the console</span></span>

<span data-ttu-id="8c406-115">Cet exemple obtient la liste des processus en cours d’exécution sur l’ordinateur et envoie le résultat vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="8c406-115">This example gets a list of the processes running on the computer and sends the result to a file.</span></span>
<span data-ttu-id="8c406-116">Étant donné qu'un deuxième chemin n'est pas spécifié, les processus sont également affichés dans la console.</span><span class="sxs-lookup"><span data-stu-id="8c406-116">Because a second path is not specified, the processes are also displayed in the console.</span></span>

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### <span data-ttu-id="8c406-117">Exemple 2 : traiter les processus dans une variable et `Select-Object`</span><span class="sxs-lookup"><span data-stu-id="8c406-117">Example 2: Output processes to a variable and `Select-Object`</span></span>

<span data-ttu-id="8c406-118">Cet exemple obtient la liste des processus en cours d’exécution sur l’ordinateur, les enregistre dans la `$proc` variable et les dirige vers `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8c406-118">This example gets a list of the processes running on the computer, saves them to the `$proc` variable, and pipes them to `Select-Object`.</span></span>

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

<span data-ttu-id="8c406-119">L' `Select-Object` applet de commande sélectionne les propriétés **ProcessName** et **Handles** .</span><span class="sxs-lookup"><span data-stu-id="8c406-119">The `Select-Object` cmdlet selects the **ProcessName** and **Handles** properties.</span></span> <span data-ttu-id="8c406-120">Notez que la `$proc` variable comprend les informations par défaut retournées par `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="8c406-120">Note that the `$proc` variable includes the default information returned by `Get-Process`.</span></span>

### <span data-ttu-id="8c406-121">Exemple 3 : fichiers système de sortie vers deux fichiers journaux</span><span class="sxs-lookup"><span data-stu-id="8c406-121">Example 3: Output system files to two log files</span></span>

<span data-ttu-id="8c406-122">Cet exemple enregistre une liste de fichiers système dans deux fichiers journaux, un fichier cumulatif et un fichier actif.</span><span class="sxs-lookup"><span data-stu-id="8c406-122">This example saves a list of system files in a two log files, a cumulative file and a current file.</span></span>

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

<span data-ttu-id="8c406-123">La commande utilise l' `Get-ChildItem` applet de commande pour effectuer une recherche récursive des fichiers système sur le lecteur D :.</span><span class="sxs-lookup"><span data-stu-id="8c406-123">The command uses the `Get-ChildItem` cmdlet to do a recursive search for system files on the D: drive.</span></span> <span data-ttu-id="8c406-124">Un opérateur de pipeline (|) envoie la liste à `Tee-Object` , qui ajoute la liste au fichier AllSystemFiles.txt et transmet la liste dans le pipeline à l’applet de commande, ce qui permet d' `Out-File` enregistrer la liste dans le fichier NewSystemFiles.txt.</span><span class="sxs-lookup"><span data-stu-id="8c406-124">A pipeline operator (|) sends the list to `Tee-Object`, which appends the list to the AllSystemFiles.txt file and passes the list down the pipeline to the `Out-File` cmdlet, which saves the list in the NewSystemFiles.txt file.</span></span>

## <span data-ttu-id="8c406-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8c406-125">PARAMETERS</span></span>

### <span data-ttu-id="8c406-126">-Append</span><span class="sxs-lookup"><span data-stu-id="8c406-126">-Append</span></span>

<span data-ttu-id="8c406-127">Indique que l’applet de commande ajoute la sortie au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c406-127">Indicates that the cmdlet appends the output to the specified file.</span></span> <span data-ttu-id="8c406-128">Sans ce paramètre, le nouveau contenu remplace tout contenu existant dans le fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="8c406-128">Without this parameter, the new content replaces any existing content in the file without warning.</span></span>

<span data-ttu-id="8c406-129">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c406-129">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c406-130">-FilePath</span><span class="sxs-lookup"><span data-stu-id="8c406-130">-FilePath</span></span>

<span data-ttu-id="8c406-131">Spécifie un fichier dont cette applet de commande enregistre l’objet dans les caractères génériques, mais qui doit être résolu en un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="8c406-131">Specifies a file that this cmdlet saves the object to Wildcard characters are permitted, but must resolve to a single file.</span></span>

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8c406-132">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8c406-132">-InputObject</span></span>

<span data-ttu-id="8c406-133">Spécifie l'objet à enregistrer et à afficher.</span><span class="sxs-lookup"><span data-stu-id="8c406-133">Specifies the object to be saved and displayed.</span></span> <span data-ttu-id="8c406-134">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="8c406-134">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="8c406-135">Vous pouvez également diriger un objet vers `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="8c406-135">You can also pipe an object to `Tee-Object`.</span></span>

<span data-ttu-id="8c406-136">Quand vous utilisez le paramètre **InputObject** avec `Tee-Object` , au lieu de rediriger les résultats de la commande vers `Tee-Object` , la valeur **InputObject** est traitée comme un objet unique, même si la valeur est une collection.</span><span class="sxs-lookup"><span data-stu-id="8c406-136">When you use the **InputObject** parameter with `Tee-Object`, instead of piping command results to `Tee-Object`, the **InputObject** value is treated as a single object even if the value is a collection.</span></span>

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

### <span data-ttu-id="8c406-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8c406-137">-LiteralPath</span></span>

<span data-ttu-id="8c406-138">Spécifie un fichier dans lequel cette applet de commande enregistre l’objet.</span><span class="sxs-lookup"><span data-stu-id="8c406-138">Specifies a file that this cmdlet saves the object to.</span></span> <span data-ttu-id="8c406-139">Contrairement à **FilePath**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="8c406-139">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="8c406-140">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="8c406-140">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8c406-141">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="8c406-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="8c406-142">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="8c406-142">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c406-143">-Variable</span><span class="sxs-lookup"><span data-stu-id="8c406-143">-Variable</span></span>

<span data-ttu-id="8c406-144">Spécifie une variable dans laquelle l’applet de commande enregistre l’objet.</span><span class="sxs-lookup"><span data-stu-id="8c406-144">Specifies a variable that the cmdlet saves the object to.</span></span> <span data-ttu-id="8c406-145">Entrez un nom de variable sans le signe dollar précédent ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="8c406-145">Enter a variable name without the preceding dollar sign (`$`).</span></span>

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c406-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c406-146">CommonParameters</span></span>

<span data-ttu-id="8c406-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c406-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c406-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8c406-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8c406-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8c406-149">INPUTS</span></span>

### <span data-ttu-id="8c406-150">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8c406-150">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8c406-151">Vous pouvez diriger les objets vers `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="8c406-151">You can pipe objects to `Tee-Object`.</span></span>

## <span data-ttu-id="8c406-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8c406-152">OUTPUTS</span></span>

### <span data-ttu-id="8c406-153">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8c406-153">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8c406-154">`Tee-Object` retourne l’objet qu’il redirige.</span><span class="sxs-lookup"><span data-stu-id="8c406-154">`Tee-Object` returns the object that it redirects.</span></span>

## <span data-ttu-id="8c406-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8c406-155">NOTES</span></span>

<span data-ttu-id="8c406-156">Vous pouvez également utiliser l' `Out-File` applet de commande ou l’opérateur de redirection, qui enregistrent la sortie dans un fichier, mais ne l’envoient pas dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8c406-156">You can also use the `Out-File` cmdlet or the redirection operator, both of which save the output in a file but do not send it down the pipeline.</span></span>

<span data-ttu-id="8c406-157">À compter de PowerShell 6, `Tee-Object` utilise l’encodage UTF-8 sans nomenclature lorsqu’il écrit dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="8c406-157">Beginning in PowerShell 6, `Tee-Object` uses BOM-less UTF-8 encoding when it writes to files.</span></span> <span data-ttu-id="8c406-158">Si vous avez besoin d’un encodage différent, utilisez l' `Out-File` applet de commande avec le paramètre **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="8c406-158">If you need a different encoding, use the `Out-File` cmdlet with the **Encoding** parameter.</span></span>

## <span data-ttu-id="8c406-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8c406-159">RELATED LINKS</span></span>

[<span data-ttu-id="8c406-160">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-160">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="8c406-161">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-161">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="8c406-162">Group-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-162">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="8c406-163">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-163">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="8c406-164">New-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-164">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="8c406-165">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-165">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="8c406-166">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-166">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="8c406-167">Where-Object</span><span class="sxs-lookup"><span data-stu-id="8c406-167">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="8c406-168">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="8c406-168">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

