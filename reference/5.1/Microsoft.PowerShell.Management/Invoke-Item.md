---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 6aac74b9b084996377b97997ab78972cb28b0959
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203978"
---
# <span data-ttu-id="8d303-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-103">Invoke-Item</span></span>

## <span data-ttu-id="8d303-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8d303-104">SYNOPSIS</span></span>
<span data-ttu-id="8d303-105">Exécute l'action par défaut sur l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="8d303-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="8d303-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8d303-106">SYNTAX</span></span>

### <span data-ttu-id="8d303-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8d303-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="8d303-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8d303-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="8d303-109">Description</span><span class="sxs-lookup"><span data-stu-id="8d303-109">DESCRIPTION</span></span>

<span data-ttu-id="8d303-110">L' `Invoke-Item` applet de commande effectue l’action par défaut sur l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="8d303-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="8d303-111">Par exemple, elle exécute un fichier exécutable ou ouvre un fichier de document dans l’application associée au type de fichier de document.</span><span class="sxs-lookup"><span data-stu-id="8d303-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="8d303-112">L’action par défaut dépend du type d’élément et est déterminée par le fournisseur PowerShell qui fournit l’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="8d303-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="8d303-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8d303-113">EXAMPLES</span></span>

### <span data-ttu-id="8d303-114">Exemple 1 : ouvrir un fichier</span><span class="sxs-lookup"><span data-stu-id="8d303-114">Example 1: Open a file</span></span>

<span data-ttu-id="8d303-115">Cette commande ouvre le fichier « aliasApr04.doc » dans Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="8d303-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="8d303-116">Dans ce cas, l’ouverture dans Word est l’action par défaut pour les fichiers « . doc ».</span><span class="sxs-lookup"><span data-stu-id="8d303-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="8d303-117">Exemple 2 : ouvrir tous les fichiers d’un type spécifique</span><span class="sxs-lookup"><span data-stu-id="8d303-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="8d303-118">Cette commande ouvre toutes les feuilles de calcul Microsoft Office Excel dans le dossier « C:\Documents and Settings\Lister\My documents ».</span><span class="sxs-lookup"><span data-stu-id="8d303-118">This command opens all of the Microsoft Office Excel spreadsheets in the "C:\Documents and Settings\Lister\My Documents" folder.</span></span>
<span data-ttu-id="8d303-119">Chaque feuille de calcul est ouverte dans une nouvelle instance d’Excel.</span><span class="sxs-lookup"><span data-stu-id="8d303-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="8d303-120">Dans ce cas, l’ouverture dans Excel est l’action par défaut pour les fichiers « . xls ».</span><span class="sxs-lookup"><span data-stu-id="8d303-120">In this case, opening in Excel is the default action for ".xls" files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="8d303-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8d303-121">PARAMETERS</span></span>

### <span data-ttu-id="8d303-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="8d303-122">-Credential</span></span>

<span data-ttu-id="8d303-123">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="8d303-123">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="8d303-124">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="8d303-124">The default is the current user.</span></span>

<span data-ttu-id="8d303-125">Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="8d303-125">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="8d303-126">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8d303-126">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="8d303-127">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d303-127">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="8d303-128">-Exclude</span><span class="sxs-lookup"><span data-stu-id="8d303-128">-Exclude</span></span>

<span data-ttu-id="8d303-129">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="8d303-129">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="8d303-130">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="8d303-130">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="8d303-131">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="8d303-131">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="8d303-132">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8d303-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8d303-133">-Filter</span><span class="sxs-lookup"><span data-stu-id="8d303-133">-Filter</span></span>

<span data-ttu-id="8d303-134">Spécifie un filtre dans le format ou la langue du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="8d303-134">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="8d303-135">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="8d303-135">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="8d303-136">La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="8d303-136">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="8d303-137">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="8d303-137">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="8d303-138">-Include</span><span class="sxs-lookup"><span data-stu-id="8d303-138">-Include</span></span>

<span data-ttu-id="8d303-139">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="8d303-139">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="8d303-140">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="8d303-140">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="8d303-141">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="8d303-141">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="8d303-142">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8d303-142">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d303-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8d303-143">-LiteralPath</span></span>

<span data-ttu-id="8d303-144">Spécifie un chemin d’accès à l’élément.</span><span class="sxs-lookup"><span data-stu-id="8d303-144">Specifies a path to the item.</span></span>
<span data-ttu-id="8d303-145">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="8d303-145">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="8d303-146">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="8d303-146">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="8d303-147">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="8d303-147">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="8d303-148">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="8d303-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8d303-149">-Path</span><span class="sxs-lookup"><span data-stu-id="8d303-149">-Path</span></span>

<span data-ttu-id="8d303-150">Spécifie le chemin d’accès à l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8d303-150">Specifies the path to the selected item.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8d303-151">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="8d303-151">-UseTransaction</span></span>

<span data-ttu-id="8d303-152">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="8d303-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="8d303-153">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="8d303-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="8d303-154">Pour plus d’informations, consultez about_transactions.</span><span class="sxs-lookup"><span data-stu-id="8d303-154">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d303-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8d303-155">-Confirm</span></span>
<span data-ttu-id="8d303-156">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8d303-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8d303-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8d303-157">-WhatIf</span></span>

<span data-ttu-id="8d303-158">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8d303-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8d303-159">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8d303-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8d303-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8d303-160">CommonParameters</span></span>

<span data-ttu-id="8d303-161">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="8d303-161">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8d303-162">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="8d303-162">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8d303-163">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8d303-163">INPUTS</span></span>

### <span data-ttu-id="8d303-164">System.String</span><span class="sxs-lookup"><span data-stu-id="8d303-164">System.String</span></span>

<span data-ttu-id="8d303-165">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8d303-165">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="8d303-166">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8d303-166">OUTPUTS</span></span>

### <span data-ttu-id="8d303-167">Aucun</span><span class="sxs-lookup"><span data-stu-id="8d303-167">None</span></span>

<span data-ttu-id="8d303-168">La commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="8d303-168">The command does not generate any output.</span></span>
<span data-ttu-id="8d303-169">Toutefois, la sortie peut être générée par l’élément appelé.</span><span class="sxs-lookup"><span data-stu-id="8d303-169">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="8d303-170">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8d303-170">NOTES</span></span>

<span data-ttu-id="8d303-171">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="8d303-171">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8d303-172">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="8d303-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="8d303-173">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="8d303-173">For more information, see about_Providers.</span></span>

## <span data-ttu-id="8d303-174">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8d303-174">RELATED LINKS</span></span>

[<span data-ttu-id="8d303-175">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-175">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="8d303-176">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-176">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="8d303-177">Get-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-177">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="8d303-178">Move-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-178">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="8d303-179">New-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-179">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="8d303-180">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-180">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="8d303-181">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-181">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="8d303-182">Set-Item</span><span class="sxs-lookup"><span data-stu-id="8d303-182">Set-Item</span></span>](Set-Item.md)
