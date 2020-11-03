---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 9ae9c0e7c17a6a63da5487cce138ddce129b975b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203561"
---
# <span data-ttu-id="d3102-103">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d3102-103">Remove-ItemProperty</span></span>

## <span data-ttu-id="d3102-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d3102-104">SYNOPSIS</span></span>
<span data-ttu-id="d3102-105">Supprime la propriété et sa valeur d'un élément.</span><span class="sxs-lookup"><span data-stu-id="d3102-105">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="d3102-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d3102-106">SYNTAX</span></span>

### <span data-ttu-id="d3102-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d3102-107">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="d3102-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d3102-108">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="d3102-109">Description</span><span class="sxs-lookup"><span data-stu-id="d3102-109">DESCRIPTION</span></span>

<span data-ttu-id="d3102-110">L' `Remove-ItemProperty` applet de commande supprime une propriété et sa valeur d’un élément.</span><span class="sxs-lookup"><span data-stu-id="d3102-110">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="d3102-111">Vous pouvez l’utiliser pour supprimer des valeurs de Registre et les données qu’elles contiennent.</span><span class="sxs-lookup"><span data-stu-id="d3102-111">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="d3102-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d3102-112">EXAMPLES</span></span>

### <span data-ttu-id="d3102-113">Exemple 1 : supprimer une valeur de Registre</span><span class="sxs-lookup"><span data-stu-id="d3102-113">Example 1: Delete a registry value</span></span>

<span data-ttu-id="d3102-114">Cette commande supprime la valeur de Registre « SmpProperty » et ses données de la sous-clé « SmpApplication » de la clé de Registre « HKEY_LOCAL_MACHINE\Software ».</span><span class="sxs-lookup"><span data-stu-id="d3102-114">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the "HKEY_LOCAL_MACHINE\Software" registry key.</span></span>

<span data-ttu-id="d3102-115">Étant donné que la commande est émise à partir d’un lecteur du système de fichiers ( `PS C:\>` ), elle inclut le chemin d’accès complet de la sous-clé « SmpApplication », y compris le lecteur, `HKLM:` et la clé « logiciel ».</span><span class="sxs-lookup"><span data-stu-id="d3102-115">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

<span data-ttu-id="d3102-116">Elle utilise le paramètre **Name** pour identifier la valeur de Registre qui est supprimée.</span><span class="sxs-lookup"><span data-stu-id="d3102-116">It uses the **Name** parameter to identify the registry value that is being deleted.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

### <span data-ttu-id="d3102-117">Exemple 2 : supprimer une valeur de registre de l’emplacement HKCU</span><span class="sxs-lookup"><span data-stu-id="d3102-117">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="d3102-118">Ces commandes suppriment la valeur de Registre « Options », ainsi que ses données, de la sous-clé « MyApp » de « HKEY_CURRENT_USER\Software\MyCompany ».</span><span class="sxs-lookup"><span data-stu-id="d3102-118">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

<span data-ttu-id="d3102-119">La première commande utilise l' `Set-Location` applet de commande pour modifier l’emplacement actuel sur le **HKEY_CURRENT_USER** lecteur ( `HKCU:` ) et la sous-clé « Software\MyCompany\MyApp. ».</span><span class="sxs-lookup"><span data-stu-id="d3102-119">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the "Software\MyCompany\MyApp" subkey.</span></span>

<span data-ttu-id="d3102-120">La deuxième commande utilise `Remove-ItemProperty` pour supprimer la valeur de Registre « Options » et ses données de la sous-clé « MyApp ».</span><span class="sxs-lookup"><span data-stu-id="d3102-120">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span>
<span data-ttu-id="d3102-121">Étant donné que **path** est requis, la commande utilise un point ('. ') pour indiquer l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="d3102-121">Because **Path** is required, the command uses a dot ('.') to indicate the current location.</span></span>
<span data-ttu-id="d3102-122">Elle utilise **Name** pour spécifier la valeur de Registre à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d3102-122">It uses **Name** to specify which registry value to delete.</span></span>
<span data-ttu-id="d3102-123">Elle utilise le paramètre **Confirm** pour demander une invite utilisateur avant de supprimer la valeur.</span><span class="sxs-lookup"><span data-stu-id="d3102-123">It uses the **Confirm** parameter to request a user prompt before deleting the value.</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

### <span data-ttu-id="d3102-124">Exemple 3 : supprimer une valeur de Registre à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="d3102-124">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="d3102-125">Cette commande supprime la valeur de Registre « NoOfEmployees » et ses données de la clé de Registre « Hklm\software\mycompany. ».</span><span class="sxs-lookup"><span data-stu-id="d3102-125">This command deletes the "NoOfEmployees" registry value, and its data, from the "HKLM\Software\MyCompany" registry key.</span></span>

<span data-ttu-id="d3102-126">La commande utilise l' `Get-Item` applet de commande pour récupérer un élément qui représente la clé de registre.</span><span class="sxs-lookup"><span data-stu-id="d3102-126">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="d3102-127">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet à `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="d3102-127">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="d3102-128">Ensuite, elle utilise le paramètre **Name** de `Remove-ItemProperty` pour spécifier le nom de la valeur de registre.</span><span class="sxs-lookup"><span data-stu-id="d3102-128">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

## <span data-ttu-id="d3102-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d3102-129">PARAMETERS</span></span>

### <span data-ttu-id="d3102-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="d3102-130">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="d3102-131">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3102-131">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="d3102-132">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="d3102-132">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="d3102-133">-Exclude</span><span class="sxs-lookup"><span data-stu-id="d3102-133">-Exclude</span></span>

<span data-ttu-id="d3102-134">Spécifie les éléments que cette applet de commande omet.</span><span class="sxs-lookup"><span data-stu-id="d3102-134">Specifies items that this cmdlet omits.</span></span>
<span data-ttu-id="d3102-135">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="d3102-135">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="d3102-136">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="d3102-136">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="d3102-137">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d3102-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d3102-138">-Filter</span><span class="sxs-lookup"><span data-stu-id="d3102-138">-Filter</span></span>

<span data-ttu-id="d3102-139">Spécifie un filtre dans le format ou la langue du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d3102-139">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="d3102-140">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="d3102-140">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="d3102-141">La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d3102-141">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="d3102-142">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="d3102-142">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="d3102-143">-Force</span><span class="sxs-lookup"><span data-stu-id="d3102-143">-Force</span></span>

<span data-ttu-id="d3102-144">Force l’applet de commande à supprimer une propriété d’un objet qui, sinon, n’est pas accessible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3102-144">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="d3102-145">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="d3102-145">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="d3102-146">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d3102-146">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="d3102-147">-Include</span><span class="sxs-lookup"><span data-stu-id="d3102-147">-Include</span></span>

<span data-ttu-id="d3102-148">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="d3102-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="d3102-149">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="d3102-149">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="d3102-150">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="d3102-150">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="d3102-151">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d3102-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d3102-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d3102-152">-LiteralPath</span></span>

<span data-ttu-id="d3102-153">Spécifie le chemin d’accès à l’emplacement actuel de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d3102-153">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="d3102-154">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="d3102-154">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="d3102-155">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="d3102-155">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="d3102-156">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="d3102-156">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="d3102-157">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d3102-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="d3102-158">-Name</span><span class="sxs-lookup"><span data-stu-id="d3102-158">-Name</span></span>

<span data-ttu-id="d3102-159">Spécifie les noms des propriétés à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d3102-159">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="d3102-160">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d3102-160">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="d3102-161">-Path</span><span class="sxs-lookup"><span data-stu-id="d3102-161">-Path</span></span>

<span data-ttu-id="d3102-162">Spécifie le chemin d’accès de l’élément dont les propriétés sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="d3102-162">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="d3102-163">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d3102-163">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d3102-164">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="d3102-164">-UseTransaction</span></span>

<span data-ttu-id="d3102-165">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="d3102-165">Includes the command in the active transaction.</span></span>
<span data-ttu-id="d3102-166">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="d3102-166">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="d3102-167">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="d3102-167">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="d3102-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d3102-168">-Confirm</span></span>

<span data-ttu-id="d3102-169">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d3102-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d3102-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d3102-170">-WhatIf</span></span>

<span data-ttu-id="d3102-171">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d3102-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d3102-172">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d3102-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d3102-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d3102-173">CommonParameters</span></span>

<span data-ttu-id="d3102-174">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="d3102-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="d3102-175">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="d3102-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d3102-176">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d3102-176">INPUTS</span></span>

### <span data-ttu-id="d3102-177">System.String</span><span class="sxs-lookup"><span data-stu-id="d3102-177">System.String</span></span>

<span data-ttu-id="d3102-178">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d3102-178">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="d3102-179">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d3102-179">OUTPUTS</span></span>

### <span data-ttu-id="d3102-180">Aucun</span><span class="sxs-lookup"><span data-stu-id="d3102-180">None</span></span>

<span data-ttu-id="d3102-181">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d3102-181">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="d3102-182">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d3102-182">NOTES</span></span>

<span data-ttu-id="d3102-183">Dans le fournisseur de Registre PowerShell, les valeurs de Registre sont considérées comme des propriétés d’une clé de registre ou d’une sous-clé.</span><span class="sxs-lookup"><span data-stu-id="d3102-183">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="d3102-184">Vous pouvez utiliser les applets de commande **ItemProperty** pour gérer ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="d3102-184">You can use the **ItemProperty** cmdlets to manage these values.</span></span>

<span data-ttu-id="d3102-185">`Remove-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d3102-185">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d3102-186">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="d3102-186">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="d3102-187">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="d3102-187">For more information, see about_Providers.</span></span>

## <span data-ttu-id="d3102-188">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d3102-188">RELATED LINKS</span></span>

[<span data-ttu-id="d3102-189">Get-Item</span><span class="sxs-lookup"><span data-stu-id="d3102-189">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="d3102-190">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d3102-190">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="d3102-191">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d3102-191">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="d3102-192">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d3102-192">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="d3102-193">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d3102-193">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="d3102-194">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d3102-194">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="d3102-195">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="d3102-195">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="d3102-196">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d3102-196">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="d3102-197">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d3102-197">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="d3102-198">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d3102-198">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
