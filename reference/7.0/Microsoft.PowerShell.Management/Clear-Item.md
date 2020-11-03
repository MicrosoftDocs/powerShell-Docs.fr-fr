---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Item
ms.openlocfilehash: 9b7ba6637574f769b1a2c55739c9989736a08c05
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201854"
---
# <span data-ttu-id="21c1f-103">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-103">Clear-Item</span></span>

## <span data-ttu-id="21c1f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="21c1f-104">SYNOPSIS</span></span>
<span data-ttu-id="21c1f-105">Efface le contenu d’un élément, mais ne supprime pas l’élément.</span><span class="sxs-lookup"><span data-stu-id="21c1f-105">Clears the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="21c1f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="21c1f-106">SYNTAX</span></span>

### <span data-ttu-id="21c1f-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="21c1f-107">Path (Default)</span></span>

```
Clear-Item [-Path] <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="21c1f-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21c1f-108">LiteralPath</span></span>

```
Clear-Item -LiteralPath <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="21c1f-109">Description</span><span class="sxs-lookup"><span data-stu-id="21c1f-109">DESCRIPTION</span></span>

<span data-ttu-id="21c1f-110">L' `Clear-Item` applet de commande efface le contenu d’un élément, mais elle ne supprime pas l’élément.</span><span class="sxs-lookup"><span data-stu-id="21c1f-110">The `Clear-Item` cmdlet clears the content of an item, but it does not delete the item.</span></span>
<span data-ttu-id="21c1f-111">Par exemple, l' `Clear-Item` applet de commande peut supprimer la valeur d’une variable, mais elle ne supprime pas la variable.</span><span class="sxs-lookup"><span data-stu-id="21c1f-111">For example, the `Clear-Item` cmdlet can delete the value of a variable, but it does not delete the variable.</span></span> <span data-ttu-id="21c1f-112">La valeur utilisée pour représenter un élément effacé est définie par chaque fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21c1f-112">The value that used to represent a cleared item is defined by each PowerShell provider.</span></span>
<span data-ttu-id="21c1f-113">Cette applet de commande est similaire à `Clear-Content` , mais elle fonctionne sur des alias et des variables au lieu de fichiers.</span><span class="sxs-lookup"><span data-stu-id="21c1f-113">This cmdlet is similar to `Clear-Content`, but it works on aliases and variables, instead of files.</span></span>

## <span data-ttu-id="21c1f-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="21c1f-114">EXAMPLES</span></span>

### <span data-ttu-id="21c1f-115">Exemple 1 : effacer la valeur d’une variable</span><span class="sxs-lookup"><span data-stu-id="21c1f-115">Example 1: Clear the value of a variable</span></span>

<span data-ttu-id="21c1f-116">Cette commande efface la valeur de la variable nommée `TestVar1` .</span><span class="sxs-lookup"><span data-stu-id="21c1f-116">This command clears the value of the variable named `TestVar1`.</span></span>
<span data-ttu-id="21c1f-117">La variable est conservée et est valide, mais sa valeur est définie sur `$null` .</span><span class="sxs-lookup"><span data-stu-id="21c1f-117">The variable remains and is valid, but its value is set to `$null`.</span></span>
<span data-ttu-id="21c1f-118">Le nom de la variable est préfixé avec `Variable:` pour indiquer le fournisseur de la variable PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21c1f-118">The variable name is prefixed with `Variable:` to indicate the PowerShell Variable provider.</span></span>

<span data-ttu-id="21c1f-119">Les autres commandes montrent que, pour obtenir le même résultat, vous pouvez basculer vers le `Variable:` lecteur PowerShell, puis exécuter la `Clear-Item` commande.</span><span class="sxs-lookup"><span data-stu-id="21c1f-119">The alternate commands show that, to get the same result, you can switch to the PowerShell `Variable:` drive and then run the `Clear-Item` command.</span></span>

```powershell
Clear-Item Variable:TestVar1
```

```
Set-Location Variable:
PS Variable:\> Clear-Item TestVar1
```

### <span data-ttu-id="21c1f-120">Exemple 2 : effacer toutes les entrées de Registre</span><span class="sxs-lookup"><span data-stu-id="21c1f-120">Example 2: Clear all registry entries</span></span>

<span data-ttu-id="21c1f-121">Cette commande efface toutes les entrées de Registre dans la sous-clé « MyKey », mais uniquement après vous être invité à confirmer votre intention.</span><span class="sxs-lookup"><span data-stu-id="21c1f-121">This command clears all registry entries in the "MyKey" subkey, but only after prompting you to confirm your intent.</span></span>
<span data-ttu-id="21c1f-122">Elle ne supprime pas la sous-clé « MyKey » ou n’affecte pas les autres clés ou entrées du Registre.</span><span class="sxs-lookup"><span data-stu-id="21c1f-122">It does not delete the "MyKey" subkey or affect any other registry keys or entries.</span></span>
<span data-ttu-id="21c1f-123">Vous pouvez utiliser les paramètres **Include** et **Exclude** pour identifier des clés de Registre spécifiques, mais non des entrées du Registre.</span><span class="sxs-lookup"><span data-stu-id="21c1f-123">You can use the **Include** and **Exclude** parameters to identify particular registry keys, but you cannot use them to identify registry entries.</span></span>

- <span data-ttu-id="21c1f-124">Pour supprimer des entrées de Registre spécifiques, utilisez l'applet de commande `Remove-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="21c1f-124">To delete particular registry entries, use the `Remove-ItemProperty` cmdlet.</span></span>
- <span data-ttu-id="21c1f-125">Pour supprimer la valeur d’une entrée de Registre, utilisez le `Clear-ItemProperty cmdlet` .</span><span class="sxs-lookup"><span data-stu-id="21c1f-125">To delete the value of a registry entry, use the `Clear-ItemProperty cmdlet`.</span></span>

```powershell
Clear-Item HKLM:\Software\MyCompany\MyKey -Confirm
```

## <span data-ttu-id="21c1f-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21c1f-126">PARAMETERS</span></span>

### <span data-ttu-id="21c1f-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="21c1f-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="21c1f-128">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21c1f-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="21c1f-129">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="21c1f-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="21c1f-130">-Exclude</span><span class="sxs-lookup"><span data-stu-id="21c1f-130">-Exclude</span></span>

<span data-ttu-id="21c1f-131">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="21c1f-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="21c1f-132">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="21c1f-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="21c1f-133">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="21c1f-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="21c1f-134">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="21c1f-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="21c1f-135">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="21c1f-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="21c1f-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="21c1f-136">-Filter</span></span>

<span data-ttu-id="21c1f-137">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="21c1f-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="21c1f-138">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="21c1f-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="21c1f-139">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="21c1f-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="21c1f-140">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="21c1f-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="21c1f-141">-Force</span><span class="sxs-lookup"><span data-stu-id="21c1f-141">-Force</span></span>

<span data-ttu-id="21c1f-142">Indique que l’applet de commande efface les éléments qui ne peuvent pas être modifiés autrement, tels que les alias en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="21c1f-142">Indicates that the cmdlet clears items that cannot otherwise be changed, such as read- only aliases.</span></span>
<span data-ttu-id="21c1f-143">L'applet de commande ne peut pas effacer des constantes.</span><span class="sxs-lookup"><span data-stu-id="21c1f-143">The cmdlet cannot clear constants.</span></span>
<span data-ttu-id="21c1f-144">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="21c1f-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="21c1f-145">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="21c1f-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="21c1f-146">L’applet de commande ne peut pas remplacer les restrictions de sécurité, même lorsque le paramètre **force** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="21c1f-146">The cmdlet cannot override security restrictions, even when the **Force** parameter is used.</span></span>

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

### <span data-ttu-id="21c1f-147">-Include</span><span class="sxs-lookup"><span data-stu-id="21c1f-147">-Include</span></span>

<span data-ttu-id="21c1f-148">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="21c1f-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="21c1f-149">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="21c1f-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="21c1f-150">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="21c1f-150">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="21c1f-151">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="21c1f-151">Wildcard characters are permitted.</span></span> <span data-ttu-id="21c1f-152">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="21c1f-152">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="21c1f-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21c1f-153">-LiteralPath</span></span>

<span data-ttu-id="21c1f-154">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="21c1f-154">Specifies a path to one or more locations.</span></span> <span data-ttu-id="21c1f-155">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="21c1f-155">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="21c1f-156">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="21c1f-156">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="21c1f-157">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="21c1f-157">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="21c1f-158">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="21c1f-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="21c1f-159">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="21c1f-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="21c1f-160">-Path</span><span class="sxs-lookup"><span data-stu-id="21c1f-160">-Path</span></span>

<span data-ttu-id="21c1f-161">Spécifie le chemin d'accès aux éléments qui sont effacés.</span><span class="sxs-lookup"><span data-stu-id="21c1f-161">Specifies the path to the items being cleared.</span></span>
<span data-ttu-id="21c1f-162">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="21c1f-162">Wildcard characters are permitted.</span></span>
<span data-ttu-id="21c1f-163">Ce paramètre est obligatoire, mais le **chemin d’accès** au nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="21c1f-163">This parameter is required, but the parameter name **Path** is optional.</span></span>

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

### <span data-ttu-id="21c1f-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="21c1f-164">-Confirm</span></span>

<span data-ttu-id="21c1f-165">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="21c1f-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="21c1f-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="21c1f-166">-WhatIf</span></span>

<span data-ttu-id="21c1f-167">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="21c1f-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="21c1f-168">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="21c1f-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="21c1f-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21c1f-169">CommonParameters</span></span>

<span data-ttu-id="21c1f-170">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="21c1f-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="21c1f-171">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="21c1f-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="21c1f-172">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="21c1f-172">INPUTS</span></span>

### <span data-ttu-id="21c1f-173">System.String</span><span class="sxs-lookup"><span data-stu-id="21c1f-173">System.String</span></span>

<span data-ttu-id="21c1f-174">Vous pouvez diriger une chaîne de chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="21c1f-174">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="21c1f-175">SORTIES</span><span class="sxs-lookup"><span data-stu-id="21c1f-175">OUTPUTS</span></span>

### <span data-ttu-id="21c1f-176">Aucun</span><span class="sxs-lookup"><span data-stu-id="21c1f-176">None</span></span>

<span data-ttu-id="21c1f-177">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="21c1f-177">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="21c1f-178">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="21c1f-178">NOTES</span></span>

- <span data-ttu-id="21c1f-179">L' `Clear-Item` applet de commande est uniquement prise en charge par plusieurs fournisseurs PowerShell, y compris l' **alias** , l' **environnement** , la **fonction** , le **Registre** et les fournisseurs de **variables** .</span><span class="sxs-lookup"><span data-stu-id="21c1f-179">The `Clear-Item` cmdlet is supported only by several PowerShell providers, including the **Alias** , **Environment** , **Function** , **Registry** , and **Variable** providers.</span></span> <span data-ttu-id="21c1f-180">Ainsi, vous pouvez utiliser `Clear-Item` pour supprimer le contenu des éléments dans les espaces de noms du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="21c1f-180">As such, you can use `Clear-Item` to delete the content of items in the provider namespaces.</span></span> <span data-ttu-id="21c1f-181">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="21c1f-181">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="21c1f-182">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="21c1f-182">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
- <span data-ttu-id="21c1f-183">Vous ne pouvez pas utiliser `Clear-Item` pour supprimer le contenu d’un fichier, car le fournisseur de système de fichiers PowerShell ne prend pas en charge cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="21c1f-183">You cannot use `Clear-Item` to delete the contents of a file, because the PowerShell FileSystem provider does not support this cmdlet.</span></span> <span data-ttu-id="21c1f-184">Pour effacer des fichiers, utilisez le `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="21c1f-184">To clear files, use the `Clear-Content`.</span></span>

## <span data-ttu-id="21c1f-185">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="21c1f-185">RELATED LINKS</span></span>

[<span data-ttu-id="21c1f-186">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-186">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="21c1f-187">Get-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-187">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="21c1f-188">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-188">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="21c1f-189">Move-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-189">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="21c1f-190">New-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-190">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="21c1f-191">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-191">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="21c1f-192">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-192">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="21c1f-193">Set-Item</span><span class="sxs-lookup"><span data-stu-id="21c1f-193">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="21c1f-194">about_Providers</span><span class="sxs-lookup"><span data-stu-id="21c1f-194">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
