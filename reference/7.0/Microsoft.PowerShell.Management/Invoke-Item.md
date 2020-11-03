---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: bbd3ca9a3a4df8930a75ecc395765e70fc7ccf7b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201285"
---
# <span data-ttu-id="32e72-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-103">Invoke-Item</span></span>

## <span data-ttu-id="32e72-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="32e72-104">SYNOPSIS</span></span>
<span data-ttu-id="32e72-105">Exécute l'action par défaut sur l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="32e72-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="32e72-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32e72-106">SYNTAX</span></span>

### <span data-ttu-id="32e72-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="32e72-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="32e72-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32e72-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="32e72-109">Description</span><span class="sxs-lookup"><span data-stu-id="32e72-109">DESCRIPTION</span></span>

<span data-ttu-id="32e72-110">L' `Invoke-Item` applet de commande effectue l’action par défaut sur l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="32e72-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="32e72-111">Par exemple, elle exécute un fichier exécutable ou ouvre un fichier de document dans l’application associée au type de fichier de document.</span><span class="sxs-lookup"><span data-stu-id="32e72-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="32e72-112">L’action par défaut dépend du type d’élément et est déterminée par le fournisseur PowerShell qui fournit l’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="32e72-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="32e72-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="32e72-113">EXAMPLES</span></span>

### <span data-ttu-id="32e72-114">Exemple 1 : ouvrir un fichier</span><span class="sxs-lookup"><span data-stu-id="32e72-114">Example 1: Open a file</span></span>

<span data-ttu-id="32e72-115">Cette commande ouvre le fichier « aliasApr04.doc » dans Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="32e72-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="32e72-116">Dans ce cas, l’ouverture dans Word est l’action par défaut pour les fichiers « . doc ».</span><span class="sxs-lookup"><span data-stu-id="32e72-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="32e72-117">Exemple 2 : ouvrir tous les fichiers d’un type spécifique</span><span class="sxs-lookup"><span data-stu-id="32e72-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="32e72-118">Cette commande ouvre toutes les feuilles de calcul Microsoft Office Excel dans le `C:\Documents and
Settings\Lister\My Documents` dossier.</span><span class="sxs-lookup"><span data-stu-id="32e72-118">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="32e72-119">Chaque feuille de calcul est ouverte dans une nouvelle instance d’Excel.</span><span class="sxs-lookup"><span data-stu-id="32e72-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="32e72-120">Dans ce cas, l’ouverture dans Excel est l’action par défaut pour les `.xls` fichiers.</span><span class="sxs-lookup"><span data-stu-id="32e72-120">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="32e72-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32e72-121">PARAMETERS</span></span>

### <span data-ttu-id="32e72-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="32e72-122">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="32e72-123">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32e72-123">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="32e72-124">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="32e72-124">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32e72-125">-Exclude</span><span class="sxs-lookup"><span data-stu-id="32e72-125">-Exclude</span></span>

<span data-ttu-id="32e72-126">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="32e72-126">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="32e72-127">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="32e72-127">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="32e72-128">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="32e72-128">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="32e72-129">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="32e72-129">Wildcard characters are permitted.</span></span> <span data-ttu-id="32e72-130">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="32e72-130">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="32e72-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="32e72-131">-Filter</span></span>

<span data-ttu-id="32e72-132">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="32e72-132">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="32e72-133">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="32e72-133">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="32e72-134">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="32e72-134">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="32e72-135">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="32e72-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="32e72-136">-Include</span><span class="sxs-lookup"><span data-stu-id="32e72-136">-Include</span></span>

<span data-ttu-id="32e72-137">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="32e72-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="32e72-138">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="32e72-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="32e72-139">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="32e72-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="32e72-140">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="32e72-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="32e72-141">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="32e72-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="32e72-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32e72-142">-LiteralPath</span></span>

<span data-ttu-id="32e72-143">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="32e72-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="32e72-144">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="32e72-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="32e72-145">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="32e72-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="32e72-146">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="32e72-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="32e72-147">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="32e72-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="32e72-148">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="32e72-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32e72-149">-Path</span><span class="sxs-lookup"><span data-stu-id="32e72-149">-Path</span></span>

<span data-ttu-id="32e72-150">Spécifie le chemin d’accès à l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="32e72-150">Specifies the path to the selected item.</span></span>
<span data-ttu-id="32e72-151">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="32e72-151">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="32e72-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="32e72-152">-Confirm</span></span>

<span data-ttu-id="32e72-153">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32e72-153">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32e72-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="32e72-154">-WhatIf</span></span>

<span data-ttu-id="32e72-155">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32e72-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="32e72-156">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="32e72-156">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32e72-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32e72-157">CommonParameters</span></span>

<span data-ttu-id="32e72-158">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="32e72-158">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="32e72-159">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="32e72-159">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="32e72-160">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="32e72-160">INPUTS</span></span>

### <span data-ttu-id="32e72-161">System.String</span><span class="sxs-lookup"><span data-stu-id="32e72-161">System.String</span></span>

<span data-ttu-id="32e72-162">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32e72-162">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="32e72-163">SORTIES</span><span class="sxs-lookup"><span data-stu-id="32e72-163">OUTPUTS</span></span>

### <span data-ttu-id="32e72-164">Aucun</span><span class="sxs-lookup"><span data-stu-id="32e72-164">None</span></span>

<span data-ttu-id="32e72-165">La commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="32e72-165">The command does not generate any output.</span></span>
<span data-ttu-id="32e72-166">Toutefois, la sortie peut être générée par l’élément appelé.</span><span class="sxs-lookup"><span data-stu-id="32e72-166">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="32e72-167">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="32e72-167">NOTES</span></span>

<span data-ttu-id="32e72-168">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="32e72-168">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="32e72-169">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="32e72-169">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="32e72-170">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="32e72-170">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="32e72-171">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="32e72-171">RELATED LINKS</span></span>

[<span data-ttu-id="32e72-172">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-172">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="32e72-173">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-173">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="32e72-174">Get-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-174">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="32e72-175">Move-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-175">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="32e72-176">New-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-176">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="32e72-177">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-177">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="32e72-178">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-178">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="32e72-179">Set-Item</span><span class="sxs-lookup"><span data-stu-id="32e72-179">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="32e72-180">about_Providers</span><span class="sxs-lookup"><span data-stu-id="32e72-180">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
