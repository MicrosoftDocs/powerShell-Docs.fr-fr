---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: 9f88dc77288a0fd24efdbb486e54bc60c2658c14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203305"
---
# <span data-ttu-id="d7404-103">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="d7404-103">Export-FormatData</span></span>

## <span data-ttu-id="d7404-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d7404-104">SYNOPSIS</span></span>
<span data-ttu-id="d7404-105">Enregistre les données de mise en forme de la session active dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d7404-105">Saves formatting data from the current session in a formatting file.</span></span>

## <span data-ttu-id="d7404-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d7404-106">SYNTAX</span></span>

### <span data-ttu-id="d7404-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d7404-107">ByPath (Default)</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### <span data-ttu-id="d7404-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="d7404-108">ByLiteralPath</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## <span data-ttu-id="d7404-109">Description</span><span class="sxs-lookup"><span data-stu-id="d7404-109">DESCRIPTION</span></span>

<span data-ttu-id="d7404-110">L' `Export-FormatData` applet de commande crée des fichiers de mise en forme Windows PowerShell (format.ps1XML) à partir des objets de mise en forme de la session active.</span><span class="sxs-lookup"><span data-stu-id="d7404-110">The `Export-FormatData` cmdlet creates Windows PowerShell formatting files (format.ps1xml) from the formatting objects in the current session.</span></span> <span data-ttu-id="d7404-111">Elle prend les objets **ExtendedTypeDefinition** qui `Get-FormatData` sont retournées et les enregistre dans un fichier au format XML.</span><span class="sxs-lookup"><span data-stu-id="d7404-111">It takes the **ExtendedTypeDefinition** objects that `Get-FormatData` returns and saves them in a file in XML format.</span></span>

<span data-ttu-id="d7404-112">Windows PowerShell utilise les données des fichiers de mise en forme (format.ps1xml) pour générer l'affichage par défaut des objets Microsoft .NET Framework dans la session.</span><span class="sxs-lookup"><span data-stu-id="d7404-112">Windows PowerShell uses the data in formatting files (format.ps1xml) to generate the default display of Microsoft .NET Framework objects in the session.</span></span> <span data-ttu-id="d7404-113">Vous pouvez afficher et modifier les fichiers de mise en forme et utiliser l'applet de commande Update-FormatData pour ajouter les données de mise en forme à une session.</span><span class="sxs-lookup"><span data-stu-id="d7404-113">You can view and edit the formatting files and use the Update-FormatData cmdlet to add the formatting data to a session.</span></span>

<span data-ttu-id="d7404-114">Pour plus d’informations sur la mise en forme des fichiers dans Windows PowerShell, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="d7404-114">For more information about formatting files in Windows PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="d7404-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d7404-115">EXAMPLES</span></span>

### <span data-ttu-id="d7404-116">Exemple 1 : exporter des données au format de session</span><span class="sxs-lookup"><span data-stu-id="d7404-116">Example 1: Export session format data</span></span>

```powershell
Get-FormatData -TypeName "*" | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="d7404-117">Cette commande exporte toutes les données de format de la session dans le fichier AllFormat.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="d7404-117">This command exports all of the format data in the session to the AllFormat.ps1xml file.</span></span>

<span data-ttu-id="d7404-118">La commande utilise l' `Get-FormatData` applet de commande pour récupérer les données de format dans la session.</span><span class="sxs-lookup"><span data-stu-id="d7404-118">The command uses the `Get-FormatData` cmdlet to get the format data in the session.</span></span> <span data-ttu-id="d7404-119">La valeur `*` (All) pour le paramètre **TypeName** indique à l’applet de commande d’obtenir toutes les données de la session.</span><span class="sxs-lookup"><span data-stu-id="d7404-119">A value of `*` (all) for the **TypeName** parameter directs the cmdlet to get all of the data in the session.</span></span>

<span data-ttu-id="d7404-120">La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données de format de la `Get-FormatData` commande à l’applet de commande `Export-FormatData` , qui exporte les données de format dans le fichier AllFormat.ps1.</span><span class="sxs-lookup"><span data-stu-id="d7404-120">The command uses a pipeline operator (`|`) to send the format data from the `Get-FormatData` command to the `Export-FormatData` cmdlet, which exports the format data to the AllFormat.ps1 file.</span></span>

<span data-ttu-id="d7404-121">La `Export-FormatData` commande utilise le paramètre **IncludeScriptBlock** pour inclure des blocs de script dans les données de format du fichier.</span><span class="sxs-lookup"><span data-stu-id="d7404-121">The `Export-FormatData` command uses the **IncludeScriptBlock** parameter to include script blocks in the format data in the file.</span></span>

### <span data-ttu-id="d7404-122">Exemple 2 : exporter des données de format pour un type</span><span class="sxs-lookup"><span data-stu-id="d7404-122">Example 2: Export format data for a type</span></span>

```powershell
$F = Get-FormatData -TypeName "helpinfoshort"
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="d7404-123">Ces commandes exportent les données de format pour le type **HelpInfoShort** dans le fichier XML Help.format.ps1.</span><span class="sxs-lookup"><span data-stu-id="d7404-123">These commands export the format data for the **HelpInfoShort** type to the Help.format.ps1xml file.</span></span>

<span data-ttu-id="d7404-124">La première commande utilise l' `Get-FormatData` applet de commande pour obtenir les données de format pour le type **HelpInfoShort** et l’enregistre dans la `$F` variable.</span><span class="sxs-lookup"><span data-stu-id="d7404-124">The first command uses the `Get-FormatData` cmdlet to get the format data for the **HelpInfoShort** type, and it saves it in the `$F` variable.</span></span>

<span data-ttu-id="d7404-125">La deuxième commande utilise le paramètre **InputObject** de l' `Export-FormatData` applet de commande pour entrer les données de format enregistrées dans la `$F` variable.</span><span class="sxs-lookup"><span data-stu-id="d7404-125">The second command uses the **InputObject** parameter of the `Export-FormatData` cmdlet to enter the format data saved in the `$F` variable.</span></span> <span data-ttu-id="d7404-126">Elle utilise également le paramètre **IncludeScriptBlock** pour inclure des blocs de script dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="d7404-126">It also uses the **IncludeScriptBlock** parameter to include script blocks in the output.</span></span>

### <span data-ttu-id="d7404-127">Exemple 3 : exporter des données au format sans bloc de script</span><span class="sxs-lookup"><span data-stu-id="d7404-127">Example 3: Export format data without a script block</span></span>

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

<span data-ttu-id="d7404-128">Cet exemple montre comment omettre le paramètre **IncludeScriptBlock** d’une `Export-FormatData` commande.</span><span class="sxs-lookup"><span data-stu-id="d7404-128">This example shows the effect of omitting the **IncludeScriptBlock** parameter from an `Export-FormatData` command.</span></span>

<span data-ttu-id="d7404-129">La première commande utilise l' `Get-FormatData` applet de commande pour obtenir les données de format pour l’objet **System. Diagnostics. Process** que l’applet de commande Get-Process retourne.</span><span class="sxs-lookup"><span data-stu-id="d7404-129">The first command uses the `Get-FormatData` cmdlet to get the format data for the **System.Diagnostics.Process** object that the Get-Process cmdlet returns.</span></span> <span data-ttu-id="d7404-130">La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données de mise en forme à l’applet de commande `Export-FormatData` , qui les exporte vers le fichier XML Process.format.ps1dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d7404-130">The command uses a pipeline operator (`|`) to send the formatting data to the `Export-FormatData` cmdlet, which exports it to the Process.format.ps1xml file in the current directory.</span></span>

<span data-ttu-id="d7404-131">Dans ce cas, la `Export-FormatData` commande n’utilise pas le paramètre **IncludeScriptBlock** .</span><span class="sxs-lookup"><span data-stu-id="d7404-131">In this case, the `Export-FormatData` command does not use the **IncludeScriptBlock** parameter.</span></span>

<span data-ttu-id="d7404-132">La deuxième commande utilise l' `Update-FormatData` applet de commande pour ajouter le Process.format.ps1fichier XML à la session active.</span><span class="sxs-lookup"><span data-stu-id="d7404-132">The second command uses the `Update-FormatData` cmdlet to add the Process.format.ps1xml file to the current session.</span></span> <span data-ttu-id="d7404-133">La commande utilise le paramètre **prependpath** pour garantir que les données de mise en forme pour les objets de processus dans le fichier XML Process.format.ps1se trouvent avant les données de mise en forme standard pour les objets de processus.</span><span class="sxs-lookup"><span data-stu-id="d7404-133">The command uses the **PrependPath** parameter to ensure that the formatting data for process objects in the Process.format.ps1xml file is found before the standard formatting data for process objects.</span></span>

<span data-ttu-id="d7404-134">La troisième commande montre les effets de cette modification.</span><span class="sxs-lookup"><span data-stu-id="d7404-134">The third command shows the effects of this change.</span></span> <span data-ttu-id="d7404-135">La commande utilise l' `Get-Process` applet de commande pour obtenir les processus dont le nom commence par P. La sortie montre que les valeurs de propriété qui sont calculées à l’aide de blocs de script sont manquantes dans l’affichage.</span><span class="sxs-lookup"><span data-stu-id="d7404-135">The command uses the `Get-Process` cmdlet to get processes that have names that begin with P. The output shows that property values that are calculated by using script blocks are missing from the display.</span></span>

## <span data-ttu-id="d7404-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d7404-136">PARAMETERS</span></span>

### <span data-ttu-id="d7404-137">-Force</span><span class="sxs-lookup"><span data-stu-id="d7404-137">-Force</span></span>

<span data-ttu-id="d7404-138">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d7404-138">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d7404-139">-IncludeScriptBlock</span><span class="sxs-lookup"><span data-stu-id="d7404-139">-IncludeScriptBlock</span></span>

<span data-ttu-id="d7404-140">Indique si les blocs de script dans les données de format sont exportés.</span><span class="sxs-lookup"><span data-stu-id="d7404-140">Indicates whether script blocks in the format data are exported.</span></span>

<span data-ttu-id="d7404-141">Comme les blocs de script contiennent du code et peuvent être utilisés à des fins malveillantes, par défaut, ils ne sont pas exportés.</span><span class="sxs-lookup"><span data-stu-id="d7404-141">Because script blocks contain code and can be used maliciously, they are not exported by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d7404-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d7404-142">-InputObject</span></span>

<span data-ttu-id="d7404-143">Spécifie les objets de données de mise en forme à exporter.</span><span class="sxs-lookup"><span data-stu-id="d7404-143">Specifies the format data objects to be exported.</span></span> <span data-ttu-id="d7404-144">Entrez une variable qui contient les objets ou une commande qui obtient les objets, par exemple une `Get-FormatData` commande.</span><span class="sxs-lookup"><span data-stu-id="d7404-144">Enter a variable that contains the objects or a command that gets the objects, such as a `Get-FormatData` command.</span></span> <span data-ttu-id="d7404-145">Vous pouvez également diriger les objets de `Get-FormatData` vers `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="d7404-145">You can also pipe the objects from `Get-FormatData` to `Export-FormatData`.</span></span>

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d7404-146">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d7404-146">-LiteralPath</span></span>

<span data-ttu-id="d7404-147">Spécifie l'emplacement du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d7404-147">Specifies a location for the output file.</span></span> <span data-ttu-id="d7404-148">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="d7404-148">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="d7404-149">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="d7404-149">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d7404-150">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="d7404-150">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="d7404-151">Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d7404-151">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d7404-152">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="d7404-152">-NoClobber</span></span>

<span data-ttu-id="d7404-153">Indique que l’applet de commande ne remplace pas les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="d7404-153">Indicates that the cmdlet does not overwrite existing files.</span></span> <span data-ttu-id="d7404-154">Par défaut, `Export-FormatData` remplace les fichiers sans avertissement, sauf si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d7404-154">By default, `Export-FormatData` overwrites files without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="d7404-155">Pour indiquer au `Export-FormatData` remplacement des fichiers en lecture seule, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="d7404-155">To direct `Export-FormatData` to overwrite read-only files, use the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d7404-156">-Path</span><span class="sxs-lookup"><span data-stu-id="d7404-156">-Path</span></span>

<span data-ttu-id="d7404-157">Spécifie l'emplacement du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d7404-157">Specifies a location for the output file.</span></span>
<span data-ttu-id="d7404-158">Entrez un chemin d'accès (facultatif) et un nom de fichier avec une extension de nom de fichier format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="d7404-158">Enter a path (optional) and file name with a format.ps1xml file name extension.</span></span>
<span data-ttu-id="d7404-159">Si vous omettez le chemin d’accès, `Export-FormatData` crée le fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="d7404-159">If you omit the path, `Export-FormatData` creates the file in the current directory.</span></span>

<span data-ttu-id="d7404-160">Si vous utilisez une extension de nom de fichier autre que. ps1xml, l' `Update-FormatData` applet de commande ne reconnaît pas le fichier.</span><span class="sxs-lookup"><span data-stu-id="d7404-160">If you use a file name extension other than .ps1xml, the `Update-FormatData` cmdlet will not recognize the file.</span></span>

<span data-ttu-id="d7404-161">Si vous spécifiez un fichier existant, `Export-FormatData` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d7404-161">If you specify an existing file, `Export-FormatData` overwrites the file without warning, unless the file has the read-only attribute.</span></span> <span data-ttu-id="d7404-162">Pour remplacer un fichier en lecture seule, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="d7404-162">To overwrite a read-only file, use the **Force** parameter.</span></span> <span data-ttu-id="d7404-163">Pour empêcher le remplacement des fichiers, utilisez le paramètre **NoClobber** .</span><span class="sxs-lookup"><span data-stu-id="d7404-163">To prevent files from being overwritten, use the **NoClobber** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d7404-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d7404-164">CommonParameters</span></span>

<span data-ttu-id="d7404-165">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d7404-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d7404-166">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d7404-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d7404-167">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d7404-167">INPUTS</span></span>

### <span data-ttu-id="d7404-168">System. Management. Automation. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="d7404-168">System.Management.Automation.ExtendedTypeDefinition</span></span>

<span data-ttu-id="d7404-169">Vous pouvez diriger les objets **ExtendedTypeDefinition** de `Get-FormatData` vers `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="d7404-169">You can pipe **ExtendedTypeDefinition** objects from `Get-FormatData` to `Export-FormatData`.</span></span>

## <span data-ttu-id="d7404-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d7404-170">OUTPUTS</span></span>

### <span data-ttu-id="d7404-171">Aucun</span><span class="sxs-lookup"><span data-stu-id="d7404-171">None</span></span>

<span data-ttu-id="d7404-172">`Export-FormatData` ne retourne aucun objet.</span><span class="sxs-lookup"><span data-stu-id="d7404-172">`Export-FormatData` does not return any objects.</span></span>
<span data-ttu-id="d7404-173">Il génère un fichier et l'enregistre dans le chemin d'accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="d7404-173">It generates a file and saves it in the specified path.</span></span>

## <span data-ttu-id="d7404-174">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d7404-174">NOTES</span></span>

- <span data-ttu-id="d7404-175">Pour utiliser un fichier de mise en forme, y compris un fichier de mise en forme exporté, la stratégie d'exécution de la session doit autoriser l'exécution des scripts et des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="d7404-175">To use any formatting file, including an exported formatting file, the execution policy for the session must allow scripts and configuration files to run.</span></span> <span data-ttu-id="d7404-176">Pour plus d’informations, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="d7404-176">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="d7404-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d7404-177">RELATED LINKS</span></span>

[<span data-ttu-id="d7404-178">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="d7404-178">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="d7404-179">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="d7404-179">Update-FormatData</span></span>](Update-FormatData.md)
