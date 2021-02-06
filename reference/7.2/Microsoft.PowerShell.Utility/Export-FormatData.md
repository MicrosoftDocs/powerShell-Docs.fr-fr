---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: d42b108d469ed8989628a6c0b4214af4afc0db00
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597323"
---
# <span data-ttu-id="3be45-102">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="3be45-102">Export-FormatData</span></span>

## <span data-ttu-id="3be45-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3be45-103">SYNOPSIS</span></span>
<span data-ttu-id="3be45-104">Enregistre les données de mise en forme de la session active dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="3be45-104">Saves formatting data from the current session in a formatting file.</span></span>

## <span data-ttu-id="3be45-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="3be45-105">SYNTAX</span></span>

### <span data-ttu-id="3be45-106">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3be45-106">ByPath (Default)</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### <span data-ttu-id="3be45-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="3be45-107">ByLiteralPath</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## <span data-ttu-id="3be45-108">Description</span><span class="sxs-lookup"><span data-stu-id="3be45-108">DESCRIPTION</span></span>

<span data-ttu-id="3be45-109">L' `Export-FormatData` applet de commande crée des fichiers de mise en forme PowerShell (format.ps1XML) à partir des objets de mise en forme de la session active.</span><span class="sxs-lookup"><span data-stu-id="3be45-109">The `Export-FormatData` cmdlet creates PowerShell formatting files (format.ps1xml) from the formatting objects in the current session.</span></span> <span data-ttu-id="3be45-110">Elle prend les objets **ExtendedTypeDefinition** qui `Get-FormatData` sont retournées et les enregistre dans un fichier au format XML.</span><span class="sxs-lookup"><span data-stu-id="3be45-110">It takes the **ExtendedTypeDefinition** objects that `Get-FormatData` returns and saves them in a file in XML format.</span></span>

<span data-ttu-id="3be45-111">PowerShell utilise les données des fichiers de mise en forme (format.ps1XML) pour générer l’affichage par défaut des objets Microsoft .NET Framework dans la session.</span><span class="sxs-lookup"><span data-stu-id="3be45-111">PowerShell uses the data in formatting files (format.ps1xml) to generate the default display of Microsoft .NET Framework objects in the session.</span></span> <span data-ttu-id="3be45-112">Vous pouvez afficher et modifier les fichiers de mise en forme et utiliser l'applet de commande Update-FormatData pour ajouter les données de mise en forme à une session.</span><span class="sxs-lookup"><span data-stu-id="3be45-112">You can view and edit the formatting files and use the Update-FormatData cmdlet to add the formatting data to a session.</span></span>

<span data-ttu-id="3be45-113">Pour plus d’informations sur la mise en forme des fichiers dans PowerShell, consultez [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="3be45-113">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="3be45-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3be45-114">EXAMPLES</span></span>

### <span data-ttu-id="3be45-115">Exemple 1 : exporter des données au format de session</span><span class="sxs-lookup"><span data-stu-id="3be45-115">Example 1: Export session format data</span></span>

```powershell
Get-FormatData -TypeName "*" | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="3be45-116">Cette commande exporte toutes les données de format de la session dans le fichier AllFormat.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="3be45-116">This command exports all of the format data in the session to the AllFormat.ps1xml file.</span></span>

<span data-ttu-id="3be45-117">La commande utilise l' `Get-FormatData` applet de commande pour récupérer les données de format dans la session.</span><span class="sxs-lookup"><span data-stu-id="3be45-117">The command uses the `Get-FormatData` cmdlet to get the format data in the session.</span></span> <span data-ttu-id="3be45-118">La valeur `*` (All) pour le paramètre **TypeName** indique à l’applet de commande d’obtenir toutes les données de la session.</span><span class="sxs-lookup"><span data-stu-id="3be45-118">A value of `*` (all) for the **TypeName** parameter directs the cmdlet to get all of the data in the session.</span></span>

<span data-ttu-id="3be45-119">La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données de format de la `Get-FormatData` commande à l’applet de commande `Export-FormatData` , qui exporte les données de format dans le fichier AllFormat.ps1.</span><span class="sxs-lookup"><span data-stu-id="3be45-119">The command uses a pipeline operator (`|`) to send the format data from the `Get-FormatData` command to the `Export-FormatData` cmdlet, which exports the format data to the AllFormat.ps1 file.</span></span>

<span data-ttu-id="3be45-120">La `Export-FormatData` commande utilise le paramètre **IncludeScriptBlock** pour inclure des blocs de script dans les données de format du fichier.</span><span class="sxs-lookup"><span data-stu-id="3be45-120">The `Export-FormatData` command uses the **IncludeScriptBlock** parameter to include script blocks in the format data in the file.</span></span>

### <span data-ttu-id="3be45-121">Exemple 2 : exporter des données de format pour un type</span><span class="sxs-lookup"><span data-stu-id="3be45-121">Example 2: Export format data for a type</span></span>

```powershell
$F = Get-FormatData -TypeName "helpinfoshort"
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="3be45-122">Ces commandes exportent les données de format pour le type **HelpInfoShort** dans le fichier XML Help.format.ps1.</span><span class="sxs-lookup"><span data-stu-id="3be45-122">These commands export the format data for the **HelpInfoShort** type to the Help.format.ps1xml file.</span></span>

<span data-ttu-id="3be45-123">La première commande utilise l' `Get-FormatData` applet de commande pour obtenir les données de format pour le type **HelpInfoShort** et l’enregistre dans la `$F` variable.</span><span class="sxs-lookup"><span data-stu-id="3be45-123">The first command uses the `Get-FormatData` cmdlet to get the format data for the **HelpInfoShort** type, and it saves it in the `$F` variable.</span></span>

<span data-ttu-id="3be45-124">La deuxième commande utilise le paramètre **InputObject** de l' `Export-FormatData` applet de commande pour entrer les données de format enregistrées dans la `$F` variable.</span><span class="sxs-lookup"><span data-stu-id="3be45-124">The second command uses the **InputObject** parameter of the `Export-FormatData` cmdlet to enter the format data saved in the `$F` variable.</span></span> <span data-ttu-id="3be45-125">Elle utilise également le paramètre **IncludeScriptBlock** pour inclure des blocs de script dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="3be45-125">It also uses the **IncludeScriptBlock** parameter to include script blocks in the output.</span></span>

### <span data-ttu-id="3be45-126">Exemple 3 : exporter des données au format sans bloc de script</span><span class="sxs-lookup"><span data-stu-id="3be45-126">Example 3: Export format data without a script block</span></span>

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

<span data-ttu-id="3be45-127">Cet exemple montre comment omettre le paramètre **IncludeScriptBlock** d’une `Export-FormatData` commande.</span><span class="sxs-lookup"><span data-stu-id="3be45-127">This example shows the effect of omitting the **IncludeScriptBlock** parameter from an `Export-FormatData` command.</span></span>

<span data-ttu-id="3be45-128">La première commande utilise l' `Get-FormatData` applet de commande pour obtenir les données de format pour l’objet **System. Diagnostics. Process** que l’applet de commande Get-Process retourne.</span><span class="sxs-lookup"><span data-stu-id="3be45-128">The first command uses the `Get-FormatData` cmdlet to get the format data for the **System.Diagnostics.Process** object that the Get-Process cmdlet returns.</span></span> <span data-ttu-id="3be45-129">La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données de mise en forme à l’applet de commande `Export-FormatData` , qui les exporte vers le fichier XML Process.format.ps1dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3be45-129">The command uses a pipeline operator (`|`) to send the formatting data to the `Export-FormatData` cmdlet, which exports it to the Process.format.ps1xml file in the current directory.</span></span>

<span data-ttu-id="3be45-130">Dans ce cas, la `Export-FormatData` commande n’utilise pas le paramètre **IncludeScriptBlock** .</span><span class="sxs-lookup"><span data-stu-id="3be45-130">In this case, the `Export-FormatData` command does not use the **IncludeScriptBlock** parameter.</span></span>

<span data-ttu-id="3be45-131">La deuxième commande utilise l' `Update-FormatData` applet de commande pour ajouter le Process.format.ps1fichier XML à la session active.</span><span class="sxs-lookup"><span data-stu-id="3be45-131">The second command uses the `Update-FormatData` cmdlet to add the Process.format.ps1xml file to the current session.</span></span> <span data-ttu-id="3be45-132">La commande utilise le paramètre **prependpath** pour garantir que les données de mise en forme pour les objets de processus dans le fichier XML Process.format.ps1se trouvent avant les données de mise en forme standard pour les objets de processus.</span><span class="sxs-lookup"><span data-stu-id="3be45-132">The command uses the **PrependPath** parameter to ensure that the formatting data for process objects in the Process.format.ps1xml file is found before the standard formatting data for process objects.</span></span>

<span data-ttu-id="3be45-133">La troisième commande montre les effets de cette modification.</span><span class="sxs-lookup"><span data-stu-id="3be45-133">The third command shows the effects of this change.</span></span> <span data-ttu-id="3be45-134">La commande utilise l' `Get-Process` applet de commande pour obtenir les processus dont le nom commence par P. La sortie montre que les valeurs de propriété qui sont calculées à l’aide de blocs de script sont manquantes dans l’affichage.</span><span class="sxs-lookup"><span data-stu-id="3be45-134">The command uses the `Get-Process` cmdlet to get processes that have names that begin with P. The output shows that property values that are calculated by using script blocks are missing from the display.</span></span>

## <span data-ttu-id="3be45-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3be45-135">PARAMETERS</span></span>

### <span data-ttu-id="3be45-136">-Force</span><span class="sxs-lookup"><span data-stu-id="3be45-136">-Force</span></span>

<span data-ttu-id="3be45-137">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3be45-137">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="3be45-138">-IncludeScriptBlock</span><span class="sxs-lookup"><span data-stu-id="3be45-138">-IncludeScriptBlock</span></span>

<span data-ttu-id="3be45-139">Indique si les blocs de script dans les données de format sont exportés.</span><span class="sxs-lookup"><span data-stu-id="3be45-139">Indicates whether script blocks in the format data are exported.</span></span>

<span data-ttu-id="3be45-140">Comme les blocs de script contiennent du code et peuvent être utilisés à des fins malveillantes, par défaut, ils ne sont pas exportés.</span><span class="sxs-lookup"><span data-stu-id="3be45-140">Because script blocks contain code and can be used maliciously, they are not exported by default.</span></span>

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

### <span data-ttu-id="3be45-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3be45-141">-InputObject</span></span>

<span data-ttu-id="3be45-142">Spécifie les objets de données de mise en forme à exporter.</span><span class="sxs-lookup"><span data-stu-id="3be45-142">Specifies the format data objects to be exported.</span></span> <span data-ttu-id="3be45-143">Entrez une variable qui contient les objets ou une commande qui obtient les objets, par exemple une `Get-FormatData` commande.</span><span class="sxs-lookup"><span data-stu-id="3be45-143">Enter a variable that contains the objects or a command that gets the objects, such as a `Get-FormatData` command.</span></span> <span data-ttu-id="3be45-144">Vous pouvez également diriger les objets de `Get-FormatData` vers `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="3be45-144">You can also pipe the objects from `Get-FormatData` to `Export-FormatData`.</span></span>

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

### <span data-ttu-id="3be45-145">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3be45-145">-LiteralPath</span></span>

<span data-ttu-id="3be45-146">Spécifie l'emplacement du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="3be45-146">Specifies a location for the output file.</span></span> <span data-ttu-id="3be45-147">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="3be45-147">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="3be45-148">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="3be45-148">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="3be45-149">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="3be45-149">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="3be45-150">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="3be45-150">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3be45-151">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="3be45-151">-NoClobber</span></span>

<span data-ttu-id="3be45-152">Indique que l’applet de commande ne remplace pas les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="3be45-152">Indicates that the cmdlet does not overwrite existing files.</span></span> <span data-ttu-id="3be45-153">Par défaut, `Export-FormatData` remplace les fichiers sans avertissement, sauf si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="3be45-153">By default, `Export-FormatData` overwrites files without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="3be45-154">Pour indiquer au `Export-FormatData` remplacement des fichiers en lecture seule, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="3be45-154">To direct `Export-FormatData` to overwrite read-only files, use the **Force** parameter.</span></span>

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

### <span data-ttu-id="3be45-155">-Path</span><span class="sxs-lookup"><span data-stu-id="3be45-155">-Path</span></span>

<span data-ttu-id="3be45-156">Spécifie l'emplacement du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="3be45-156">Specifies a location for the output file.</span></span>
<span data-ttu-id="3be45-157">Entrez un chemin d'accès (facultatif) et un nom de fichier avec une extension de nom de fichier format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="3be45-157">Enter a path (optional) and file name with a format.ps1xml file name extension.</span></span>
<span data-ttu-id="3be45-158">Si vous omettez le chemin d’accès, `Export-FormatData` crée le fichier dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3be45-158">If you omit the path, `Export-FormatData` creates the file in the current directory.</span></span>

<span data-ttu-id="3be45-159">Si vous utilisez une extension de nom de fichier autre que. ps1xml, l' `Update-FormatData` applet de commande ne reconnaît pas le fichier.</span><span class="sxs-lookup"><span data-stu-id="3be45-159">If you use a file name extension other than .ps1xml, the `Update-FormatData` cmdlet will not recognize the file.</span></span>

<span data-ttu-id="3be45-160">Si vous spécifiez un fichier existant, `Export-FormatData` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="3be45-160">If you specify an existing file, `Export-FormatData` overwrites the file without warning, unless the file has the read-only attribute.</span></span> <span data-ttu-id="3be45-161">Pour remplacer un fichier en lecture seule, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="3be45-161">To overwrite a read-only file, use the **Force** parameter.</span></span> <span data-ttu-id="3be45-162">Pour empêcher le remplacement des fichiers, utilisez le paramètre **NoClobber** .</span><span class="sxs-lookup"><span data-stu-id="3be45-162">To prevent files from being overwritten, use the **NoClobber** parameter.</span></span>

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

### <span data-ttu-id="3be45-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3be45-163">CommonParameters</span></span>

<span data-ttu-id="3be45-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3be45-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3be45-165">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3be45-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3be45-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3be45-166">INPUTS</span></span>

### <span data-ttu-id="3be45-167">System. Management. Automation. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="3be45-167">System.Management.Automation.ExtendedTypeDefinition</span></span>

<span data-ttu-id="3be45-168">Vous pouvez diriger les objets **ExtendedTypeDefinition** de `Get-FormatData` vers `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="3be45-168">You can pipe **ExtendedTypeDefinition** objects from `Get-FormatData` to `Export-FormatData`.</span></span>

## <span data-ttu-id="3be45-169">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3be45-169">OUTPUTS</span></span>

### <span data-ttu-id="3be45-170">None</span><span class="sxs-lookup"><span data-stu-id="3be45-170">None</span></span>

<span data-ttu-id="3be45-171">`Export-FormatData` ne retourne aucun objet.</span><span class="sxs-lookup"><span data-stu-id="3be45-171">`Export-FormatData` does not return any objects.</span></span>
<span data-ttu-id="3be45-172">Il génère un fichier et l'enregistre dans le chemin d'accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="3be45-172">It generates a file and saves it in the specified path.</span></span>

## <span data-ttu-id="3be45-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3be45-173">NOTES</span></span>

- <span data-ttu-id="3be45-174">Pour utiliser un fichier de mise en forme, y compris un fichier de mise en forme exporté, la stratégie d'exécution de la session doit autoriser l'exécution des scripts et des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="3be45-174">To use any formatting file, including an exported formatting file, the execution policy for the session must allow scripts and configuration files to run.</span></span> <span data-ttu-id="3be45-175">Pour plus d’informations, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="3be45-175">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="3be45-176">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3be45-176">RELATED LINKS</span></span>

[<span data-ttu-id="3be45-177">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="3be45-177">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="3be45-178">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="3be45-178">Update-FormatData</span></span>](Update-FormatData.md)
