---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: ebb79f16447aef2dd194505d805a34353f710e69
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598992"
---
# <span data-ttu-id="b9260-102">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-102">Invoke-Item</span></span>

## <span data-ttu-id="b9260-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b9260-103">SYNOPSIS</span></span>
<span data-ttu-id="b9260-104">Exécute l'action par défaut sur l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="b9260-104">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="b9260-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b9260-105">SYNTAX</span></span>

### <span data-ttu-id="b9260-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b9260-106">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b9260-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b9260-107">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b9260-108">Description</span><span class="sxs-lookup"><span data-stu-id="b9260-108">DESCRIPTION</span></span>

<span data-ttu-id="b9260-109">L' `Invoke-Item` applet de commande effectue l’action par défaut sur l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="b9260-109">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="b9260-110">Par exemple, elle exécute un fichier exécutable ou ouvre un fichier de document dans l’application associée au type de fichier de document.</span><span class="sxs-lookup"><span data-stu-id="b9260-110">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="b9260-111">L’action par défaut dépend du type d’élément et est déterminée par le fournisseur PowerShell qui fournit l’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="b9260-111">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="b9260-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b9260-112">EXAMPLES</span></span>

### <span data-ttu-id="b9260-113">Exemple 1 : ouvrir un fichier</span><span class="sxs-lookup"><span data-stu-id="b9260-113">Example 1: Open a file</span></span>

<span data-ttu-id="b9260-114">Cette commande ouvre le fichier « aliasApr04.doc » dans Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="b9260-114">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="b9260-115">Dans ce cas, l’ouverture dans Word est l’action par défaut pour les fichiers « . doc ».</span><span class="sxs-lookup"><span data-stu-id="b9260-115">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="b9260-116">Exemple 2 : ouvrir tous les fichiers d’un type spécifique</span><span class="sxs-lookup"><span data-stu-id="b9260-116">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="b9260-117">Cette commande ouvre toutes les feuilles de calcul Microsoft Office Excel dans le `C:\Documents and
Settings\Lister\My Documents` dossier.</span><span class="sxs-lookup"><span data-stu-id="b9260-117">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="b9260-118">Chaque feuille de calcul est ouverte dans une nouvelle instance d’Excel.</span><span class="sxs-lookup"><span data-stu-id="b9260-118">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="b9260-119">Dans ce cas, l’ouverture dans Excel est l’action par défaut pour les `.xls` fichiers.</span><span class="sxs-lookup"><span data-stu-id="b9260-119">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="b9260-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b9260-120">PARAMETERS</span></span>

### <span data-ttu-id="b9260-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="b9260-121">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b9260-122">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9260-122">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="b9260-123">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="b9260-123">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="b9260-124">-Exclude</span><span class="sxs-lookup"><span data-stu-id="b9260-124">-Exclude</span></span>

<span data-ttu-id="b9260-125">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="b9260-125">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="b9260-126">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="b9260-126">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b9260-127">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="b9260-127">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="b9260-128">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b9260-128">Wildcard characters are permitted.</span></span> <span data-ttu-id="b9260-129">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="b9260-129">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b9260-130">-Filter</span><span class="sxs-lookup"><span data-stu-id="b9260-130">-Filter</span></span>

<span data-ttu-id="b9260-131">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="b9260-131">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="b9260-132">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="b9260-132">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="b9260-133">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="b9260-133">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="b9260-134">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="b9260-134">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="b9260-135">-Include</span><span class="sxs-lookup"><span data-stu-id="b9260-135">-Include</span></span>

<span data-ttu-id="b9260-136">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="b9260-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="b9260-137">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="b9260-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b9260-138">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="b9260-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="b9260-139">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b9260-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="b9260-140">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="b9260-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b9260-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b9260-141">-LiteralPath</span></span>

<span data-ttu-id="b9260-142">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="b9260-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b9260-143">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="b9260-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="b9260-144">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="b9260-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b9260-145">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="b9260-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b9260-146">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="b9260-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="b9260-147">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="b9260-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="b9260-148">-Path</span><span class="sxs-lookup"><span data-stu-id="b9260-148">-Path</span></span>

<span data-ttu-id="b9260-149">Spécifie le chemin d’accès à l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="b9260-149">Specifies the path to the selected item.</span></span>
<span data-ttu-id="b9260-150">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b9260-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b9260-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b9260-151">-Confirm</span></span>

<span data-ttu-id="b9260-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b9260-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b9260-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b9260-153">-WhatIf</span></span>

<span data-ttu-id="b9260-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b9260-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b9260-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b9260-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b9260-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9260-156">CommonParameters</span></span>

<span data-ttu-id="b9260-157">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="b9260-157">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b9260-158">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b9260-158">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b9260-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b9260-159">INPUTS</span></span>

### <span data-ttu-id="b9260-160">System.String</span><span class="sxs-lookup"><span data-stu-id="b9260-160">System.String</span></span>

<span data-ttu-id="b9260-161">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b9260-161">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="b9260-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b9260-162">OUTPUTS</span></span>

### <span data-ttu-id="b9260-163">None</span><span class="sxs-lookup"><span data-stu-id="b9260-163">None</span></span>

<span data-ttu-id="b9260-164">La commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="b9260-164">The command does not generate any output.</span></span>
<span data-ttu-id="b9260-165">Toutefois, la sortie peut être générée par l’élément appelé.</span><span class="sxs-lookup"><span data-stu-id="b9260-165">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="b9260-166">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b9260-166">NOTES</span></span>

<span data-ttu-id="b9260-167">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="b9260-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b9260-168">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="b9260-168">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="b9260-169">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="b9260-169">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b9260-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b9260-170">RELATED LINKS</span></span>

[<span data-ttu-id="b9260-171">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-171">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="b9260-172">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-172">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="b9260-173">Get-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-173">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="b9260-174">Move-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-174">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="b9260-175">New-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-175">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="b9260-176">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-176">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="b9260-177">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-177">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="b9260-178">Set-Item</span><span class="sxs-lookup"><span data-stu-id="b9260-178">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="b9260-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b9260-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

