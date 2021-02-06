---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 870d8e9797ff2cfce14034706f704c0e1c954fc2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597558"
---
# <span data-ttu-id="ceed7-102">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ceed7-102">Remove-ItemProperty</span></span>

## <span data-ttu-id="ceed7-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ceed7-103">SYNOPSIS</span></span>
<span data-ttu-id="ceed7-104">Supprime la propriété et sa valeur d'un élément.</span><span class="sxs-lookup"><span data-stu-id="ceed7-104">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="ceed7-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ceed7-105">SYNTAX</span></span>

### <span data-ttu-id="ceed7-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ceed7-106">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ceed7-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ceed7-107">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ceed7-108">Description</span><span class="sxs-lookup"><span data-stu-id="ceed7-108">DESCRIPTION</span></span>

<span data-ttu-id="ceed7-109">L' `Remove-ItemProperty` applet de commande supprime une propriété et sa valeur d’un élément.</span><span class="sxs-lookup"><span data-stu-id="ceed7-109">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="ceed7-110">Vous pouvez l’utiliser pour supprimer des valeurs de Registre et les données qu’elles contiennent.</span><span class="sxs-lookup"><span data-stu-id="ceed7-110">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="ceed7-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ceed7-111">EXAMPLES</span></span>

### <span data-ttu-id="ceed7-112">Exemple 1 : supprimer une valeur de Registre</span><span class="sxs-lookup"><span data-stu-id="ceed7-112">Example 1: Delete a registry value</span></span>

<span data-ttu-id="ceed7-113">Cette commande supprime la valeur de Registre « SmpProperty » et ses données de la sous-clé « SmpApplication » de la `HKEY_LOCAL_MACHINE\Software` clé de registre.</span><span class="sxs-lookup"><span data-stu-id="ceed7-113">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the `HKEY_LOCAL_MACHINE\Software` registry key.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

<span data-ttu-id="ceed7-114">Étant donné que la commande est émise à partir d’un lecteur du système de fichiers ( `PS C:\>` ), elle inclut le chemin d’accès complet de la sous-clé « SmpApplication », y compris le lecteur, `HKLM:` et la clé « logiciel ».</span><span class="sxs-lookup"><span data-stu-id="ceed7-114">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

### <span data-ttu-id="ceed7-115">Exemple 2 : supprimer une valeur de registre de l’emplacement HKCU</span><span class="sxs-lookup"><span data-stu-id="ceed7-115">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="ceed7-116">Ces commandes suppriment la valeur de Registre « Options », ainsi que ses données, de la sous-clé « MyApp » de « HKEY_CURRENT_USER\Software\MyCompany ».</span><span class="sxs-lookup"><span data-stu-id="ceed7-116">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

<span data-ttu-id="ceed7-117">La première commande utilise l' `Set-Location` applet de commande pour modifier l’emplacement actuel sur le lecteur **HKEY_CURRENT_USER** ( `HKCU:` ) et la `Software\MyCompany\MyApp` sous-clé.</span><span class="sxs-lookup"><span data-stu-id="ceed7-117">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the `Software\MyCompany\MyApp` subkey.</span></span>

<span data-ttu-id="ceed7-118">La deuxième commande utilise `Remove-ItemProperty` pour supprimer la valeur de Registre « Options » et ses données de la sous-clé « MyApp ».</span><span class="sxs-lookup"><span data-stu-id="ceed7-118">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span> <span data-ttu-id="ceed7-119">Étant donné que **path** est requis, la commande utilise un point ( `.` ) pour indiquer l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="ceed7-119">Because **Path** is required, the command uses a dot (`.`) to indicate the current location.</span></span> <span data-ttu-id="ceed7-120">Le paramètre **Confirm** demande une invite utilisateur avant de supprimer la valeur.</span><span class="sxs-lookup"><span data-stu-id="ceed7-120">The **Confirm** parameter requests a user prompt before deleting the value.</span></span>

### <span data-ttu-id="ceed7-121">Exemple 3 : supprimer une valeur de Registre à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="ceed7-121">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="ceed7-122">Cette commande supprime la valeur de Registre « NoOfEmployees » et ses données de la clé de `HKLM\Software\MyCompany` Registre.</span><span class="sxs-lookup"><span data-stu-id="ceed7-122">This command deletes the "NoOfEmployees" registry value, and its data, from the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

<span data-ttu-id="ceed7-123">La commande utilise l' `Get-Item` applet de commande pour récupérer un élément qui représente la clé de registre.</span><span class="sxs-lookup"><span data-stu-id="ceed7-123">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="ceed7-124">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet à `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="ceed7-124">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="ceed7-125">Ensuite, elle utilise le paramètre **Name** de `Remove-ItemProperty` pour spécifier le nom de la valeur de registre.</span><span class="sxs-lookup"><span data-stu-id="ceed7-125">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

## <span data-ttu-id="ceed7-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ceed7-126">PARAMETERS</span></span>

### <span data-ttu-id="ceed7-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="ceed7-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="ceed7-128">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceed7-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="ceed7-129">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="ceed7-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="ceed7-130">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ceed7-130">-Exclude</span></span>

<span data-ttu-id="ceed7-131">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="ceed7-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="ceed7-132">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="ceed7-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="ceed7-133">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="ceed7-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="ceed7-134">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ceed7-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="ceed7-135">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="ceed7-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="ceed7-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="ceed7-136">-Filter</span></span>

<span data-ttu-id="ceed7-137">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="ceed7-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="ceed7-138">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="ceed7-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="ceed7-139">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="ceed7-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="ceed7-140">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="ceed7-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="ceed7-141">-Force</span><span class="sxs-lookup"><span data-stu-id="ceed7-141">-Force</span></span>

<span data-ttu-id="ceed7-142">Force l’applet de commande à supprimer une propriété d’un objet qui, sinon, n’est pas accessible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ceed7-142">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="ceed7-143">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="ceed7-143">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="ceed7-144">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="ceed7-144">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="ceed7-145">-Include</span><span class="sxs-lookup"><span data-stu-id="ceed7-145">-Include</span></span>

<span data-ttu-id="ceed7-146">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="ceed7-146">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="ceed7-147">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="ceed7-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="ceed7-148">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="ceed7-148">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="ceed7-149">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ceed7-149">Wildcard characters are permitted.</span></span> <span data-ttu-id="ceed7-150">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="ceed7-150">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="ceed7-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ceed7-151">-LiteralPath</span></span>

<span data-ttu-id="ceed7-152">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="ceed7-152">Specifies a path to one or more locations.</span></span> <span data-ttu-id="ceed7-153">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="ceed7-153">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="ceed7-154">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="ceed7-154">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ceed7-155">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="ceed7-155">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ceed7-156">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="ceed7-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="ceed7-157">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="ceed7-157">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="ceed7-158">-Name</span><span class="sxs-lookup"><span data-stu-id="ceed7-158">-Name</span></span>

<span data-ttu-id="ceed7-159">Spécifie les noms des propriétés à supprimer.</span><span class="sxs-lookup"><span data-stu-id="ceed7-159">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="ceed7-160">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ceed7-160">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ceed7-161">-Path</span><span class="sxs-lookup"><span data-stu-id="ceed7-161">-Path</span></span>

<span data-ttu-id="ceed7-162">Spécifie le chemin d’accès de l’élément dont les propriétés sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="ceed7-162">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="ceed7-163">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ceed7-163">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ceed7-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ceed7-164">-Confirm</span></span>

<span data-ttu-id="ceed7-165">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ceed7-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ceed7-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ceed7-166">-WhatIf</span></span>

<span data-ttu-id="ceed7-167">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ceed7-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ceed7-168">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ceed7-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ceed7-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ceed7-169">CommonParameters</span></span>

<span data-ttu-id="ceed7-170">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="ceed7-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="ceed7-171">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ceed7-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ceed7-172">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ceed7-172">INPUTS</span></span>

### <span data-ttu-id="ceed7-173">System.String</span><span class="sxs-lookup"><span data-stu-id="ceed7-173">System.String</span></span>

<span data-ttu-id="ceed7-174">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ceed7-174">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="ceed7-175">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ceed7-175">OUTPUTS</span></span>

### <span data-ttu-id="ceed7-176">None</span><span class="sxs-lookup"><span data-stu-id="ceed7-176">None</span></span>

<span data-ttu-id="ceed7-177">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ceed7-177">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="ceed7-178">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ceed7-178">NOTES</span></span>

- <span data-ttu-id="ceed7-179">Dans le fournisseur de Registre PowerShell, les valeurs de Registre sont considérées comme des propriétés d’une clé de registre ou d’une sous-clé.</span><span class="sxs-lookup"><span data-stu-id="ceed7-179">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="ceed7-180">Vous pouvez utiliser les applets de commande **ItemProperty** pour gérer ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="ceed7-180">You can use the **ItemProperty** cmdlets to manage these values.</span></span>
- <span data-ttu-id="ceed7-181">`Remove-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="ceed7-181">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ceed7-182">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="ceed7-182">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="ceed7-183">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="ceed7-183">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="ceed7-184">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ceed7-184">RELATED LINKS</span></span>

[<span data-ttu-id="ceed7-185">Get-Item</span><span class="sxs-lookup"><span data-stu-id="ceed7-185">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="ceed7-186">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ceed7-186">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="ceed7-187">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ceed7-187">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="ceed7-188">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ceed7-188">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="ceed7-189">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ceed7-189">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="ceed7-190">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ceed7-190">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="ceed7-191">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="ceed7-191">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="ceed7-192">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ceed7-192">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="ceed7-193">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ceed7-193">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="ceed7-194">Set-Location</span><span class="sxs-lookup"><span data-stu-id="ceed7-194">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="ceed7-195">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ceed7-195">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

