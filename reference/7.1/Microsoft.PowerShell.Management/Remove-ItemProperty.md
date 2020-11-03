---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 335f1f5b3e40eaf39cee7213b7bb02dbfa69ee3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202054"
---
# <span data-ttu-id="4d71b-103">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4d71b-103">Remove-ItemProperty</span></span>

## <span data-ttu-id="4d71b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4d71b-104">SYNOPSIS</span></span>
<span data-ttu-id="4d71b-105">Supprime la propriété et sa valeur d'un élément.</span><span class="sxs-lookup"><span data-stu-id="4d71b-105">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="4d71b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4d71b-106">SYNTAX</span></span>

### <span data-ttu-id="4d71b-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4d71b-107">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d71b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4d71b-108">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4d71b-109">Description</span><span class="sxs-lookup"><span data-stu-id="4d71b-109">DESCRIPTION</span></span>

<span data-ttu-id="4d71b-110">L' `Remove-ItemProperty` applet de commande supprime une propriété et sa valeur d’un élément.</span><span class="sxs-lookup"><span data-stu-id="4d71b-110">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="4d71b-111">Vous pouvez l’utiliser pour supprimer des valeurs de Registre et les données qu’elles contiennent.</span><span class="sxs-lookup"><span data-stu-id="4d71b-111">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="4d71b-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4d71b-112">EXAMPLES</span></span>

### <span data-ttu-id="4d71b-113">Exemple 1 : supprimer une valeur de Registre</span><span class="sxs-lookup"><span data-stu-id="4d71b-113">Example 1: Delete a registry value</span></span>

<span data-ttu-id="4d71b-114">Cette commande supprime la valeur de Registre « SmpProperty » et ses données de la sous-clé « SmpApplication » de la `HKEY_LOCAL_MACHINE\Software` clé de registre.</span><span class="sxs-lookup"><span data-stu-id="4d71b-114">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the `HKEY_LOCAL_MACHINE\Software` registry key.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

<span data-ttu-id="4d71b-115">Étant donné que la commande est émise à partir d’un lecteur du système de fichiers ( `PS C:\>` ), elle inclut le chemin d’accès complet de la sous-clé « SmpApplication », y compris le lecteur, `HKLM:` et la clé « logiciel ».</span><span class="sxs-lookup"><span data-stu-id="4d71b-115">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

### <span data-ttu-id="4d71b-116">Exemple 2 : supprimer une valeur de registre de l’emplacement HKCU</span><span class="sxs-lookup"><span data-stu-id="4d71b-116">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="4d71b-117">Ces commandes suppriment la valeur de Registre « Options », ainsi que ses données, de la sous-clé « MyApp » de « HKEY_CURRENT_USER\Software\MyCompany ».</span><span class="sxs-lookup"><span data-stu-id="4d71b-117">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

<span data-ttu-id="4d71b-118">La première commande utilise l' `Set-Location` applet de commande pour modifier l’emplacement actuel sur le lecteur **HKEY_CURRENT_USER** ( `HKCU:` ) et la `Software\MyCompany\MyApp` sous-clé.</span><span class="sxs-lookup"><span data-stu-id="4d71b-118">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the `Software\MyCompany\MyApp` subkey.</span></span>

<span data-ttu-id="4d71b-119">La deuxième commande utilise `Remove-ItemProperty` pour supprimer la valeur de Registre « Options » et ses données de la sous-clé « MyApp ».</span><span class="sxs-lookup"><span data-stu-id="4d71b-119">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span> <span data-ttu-id="4d71b-120">Étant donné que **path** est requis, la commande utilise un point ( `.` ) pour indiquer l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="4d71b-120">Because **Path** is required, the command uses a dot (`.`) to indicate the current location.</span></span> <span data-ttu-id="4d71b-121">Le paramètre **Confirm** demande une invite utilisateur avant de supprimer la valeur.</span><span class="sxs-lookup"><span data-stu-id="4d71b-121">The **Confirm** parameter requests a user prompt before deleting the value.</span></span>

### <span data-ttu-id="4d71b-122">Exemple 3 : supprimer une valeur de Registre à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="4d71b-122">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="4d71b-123">Cette commande supprime la valeur de Registre « NoOfEmployees » et ses données de la clé de `HKLM\Software\MyCompany` Registre.</span><span class="sxs-lookup"><span data-stu-id="4d71b-123">This command deletes the "NoOfEmployees" registry value, and its data, from the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

<span data-ttu-id="4d71b-124">La commande utilise l' `Get-Item` applet de commande pour récupérer un élément qui représente la clé de registre.</span><span class="sxs-lookup"><span data-stu-id="4d71b-124">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="4d71b-125">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet à `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="4d71b-125">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="4d71b-126">Ensuite, elle utilise le paramètre **Name** de `Remove-ItemProperty` pour spécifier le nom de la valeur de registre.</span><span class="sxs-lookup"><span data-stu-id="4d71b-126">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

## <span data-ttu-id="4d71b-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4d71b-127">PARAMETERS</span></span>

### <span data-ttu-id="4d71b-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="4d71b-128">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="4d71b-129">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d71b-129">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="4d71b-130">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="4d71b-130">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="4d71b-131">-Exclude</span><span class="sxs-lookup"><span data-stu-id="4d71b-131">-Exclude</span></span>

<span data-ttu-id="4d71b-132">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="4d71b-132">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="4d71b-133">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="4d71b-133">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4d71b-134">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="4d71b-134">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="4d71b-135">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4d71b-135">Wildcard characters are permitted.</span></span> <span data-ttu-id="4d71b-136">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="4d71b-136">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="4d71b-137">-Filter</span><span class="sxs-lookup"><span data-stu-id="4d71b-137">-Filter</span></span>

<span data-ttu-id="4d71b-138">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="4d71b-138">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="4d71b-139">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="4d71b-139">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="4d71b-140">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="4d71b-140">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="4d71b-141">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="4d71b-141">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="4d71b-142">-Force</span><span class="sxs-lookup"><span data-stu-id="4d71b-142">-Force</span></span>

<span data-ttu-id="4d71b-143">Force l’applet de commande à supprimer une propriété d’un objet qui, sinon, n’est pas accessible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d71b-143">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="4d71b-144">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="4d71b-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="4d71b-145">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="4d71b-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="4d71b-146">-Include</span><span class="sxs-lookup"><span data-stu-id="4d71b-146">-Include</span></span>

<span data-ttu-id="4d71b-147">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="4d71b-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="4d71b-148">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="4d71b-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4d71b-149">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="4d71b-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="4d71b-150">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4d71b-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="4d71b-151">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="4d71b-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="4d71b-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4d71b-152">-LiteralPath</span></span>

<span data-ttu-id="4d71b-153">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="4d71b-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="4d71b-154">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="4d71b-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="4d71b-155">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="4d71b-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4d71b-156">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="4d71b-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4d71b-157">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4d71b-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="4d71b-158">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="4d71b-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="4d71b-159">-Name</span><span class="sxs-lookup"><span data-stu-id="4d71b-159">-Name</span></span>

<span data-ttu-id="4d71b-160">Spécifie les noms des propriétés à supprimer.</span><span class="sxs-lookup"><span data-stu-id="4d71b-160">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="4d71b-161">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4d71b-161">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="4d71b-162">-Path</span><span class="sxs-lookup"><span data-stu-id="4d71b-162">-Path</span></span>

<span data-ttu-id="4d71b-163">Spécifie le chemin d’accès de l’élément dont les propriétés sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="4d71b-163">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="4d71b-164">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4d71b-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="4d71b-165">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4d71b-165">-Confirm</span></span>

<span data-ttu-id="4d71b-166">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4d71b-166">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4d71b-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4d71b-167">-WhatIf</span></span>

<span data-ttu-id="4d71b-168">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4d71b-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4d71b-169">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4d71b-169">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4d71b-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4d71b-170">CommonParameters</span></span>

<span data-ttu-id="4d71b-171">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="4d71b-171">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="4d71b-172">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4d71b-172">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4d71b-173">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4d71b-173">INPUTS</span></span>

### <span data-ttu-id="4d71b-174">System.String</span><span class="sxs-lookup"><span data-stu-id="4d71b-174">System.String</span></span>

<span data-ttu-id="4d71b-175">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4d71b-175">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="4d71b-176">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4d71b-176">OUTPUTS</span></span>

### <span data-ttu-id="4d71b-177">Aucun</span><span class="sxs-lookup"><span data-stu-id="4d71b-177">None</span></span>

<span data-ttu-id="4d71b-178">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="4d71b-178">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="4d71b-179">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4d71b-179">NOTES</span></span>

- <span data-ttu-id="4d71b-180">Dans le fournisseur de Registre PowerShell, les valeurs de Registre sont considérées comme des propriétés d’une clé de registre ou d’une sous-clé.</span><span class="sxs-lookup"><span data-stu-id="4d71b-180">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="4d71b-181">Vous pouvez utiliser les applets de commande **ItemProperty** pour gérer ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="4d71b-181">You can use the **ItemProperty** cmdlets to manage these values.</span></span>
- <span data-ttu-id="4d71b-182">`Remove-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4d71b-182">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4d71b-183">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="4d71b-183">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="4d71b-184">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="4d71b-184">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="4d71b-185">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4d71b-185">RELATED LINKS</span></span>

[<span data-ttu-id="4d71b-186">Get-Item</span><span class="sxs-lookup"><span data-stu-id="4d71b-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="4d71b-187">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4d71b-187">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="4d71b-188">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4d71b-188">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="4d71b-189">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4d71b-189">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="4d71b-190">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4d71b-190">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="4d71b-191">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4d71b-191">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="4d71b-192">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="4d71b-192">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="4d71b-193">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4d71b-193">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="4d71b-194">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4d71b-194">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="4d71b-195">Set-Location</span><span class="sxs-lookup"><span data-stu-id="4d71b-195">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="4d71b-196">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4d71b-196">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

