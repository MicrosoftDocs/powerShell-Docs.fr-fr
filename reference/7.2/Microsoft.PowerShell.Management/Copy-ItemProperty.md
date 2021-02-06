---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-ItemProperty
ms.openlocfilehash: d6dd6d21d7c0022e8ca1ea7dbd8e1cab8a680de6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596506"
---
# <span data-ttu-id="6aa75-102">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6aa75-102">Copy-ItemProperty</span></span>

## <span data-ttu-id="6aa75-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6aa75-103">SYNOPSIS</span></span>
<span data-ttu-id="6aa75-104">Copie une propriété et une valeur d'un emplacement spécifié vers un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="6aa75-104">Copies a property and value from a specified location to another location.</span></span>

## <span data-ttu-id="6aa75-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="6aa75-105">SYNTAX</span></span>

### <span data-ttu-id="6aa75-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6aa75-106">Path (Default)</span></span>

```
Copy-ItemProperty [-Path] <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6aa75-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6aa75-107">LiteralPath</span></span>

```
Copy-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6aa75-108">Description</span><span class="sxs-lookup"><span data-stu-id="6aa75-108">DESCRIPTION</span></span>

<span data-ttu-id="6aa75-109">L' `Copy-ItemProperty` applet de commande copie une propriété et une valeur d’un emplacement spécifié vers un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="6aa75-109">The `Copy-ItemProperty` cmdlet copies a property and value from a specified location to another location.</span></span>
<span data-ttu-id="6aa75-110">Par exemple, vous pouvez utiliser cette applet de commande pour copier une ou plusieurs entrées de registre d’une clé de Registre vers une autre clé de registre.</span><span class="sxs-lookup"><span data-stu-id="6aa75-110">For instance, you can use this cmdlet to copy one or more registry entries from one registry key to another registry key.</span></span>

## <span data-ttu-id="6aa75-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6aa75-111">EXAMPLES</span></span>

### <span data-ttu-id="6aa75-112">Exemple 1 : copier une propriété d’une clé de Registre vers une autre clé de Registre</span><span class="sxs-lookup"><span data-stu-id="6aa75-112">Example 1: Copy a property from a registry key to another registry key</span></span>

<span data-ttu-id="6aa75-113">Cette commande copie la propriété nommée « MyProperty » de la clé de Registre « MyApplication » vers la clé de Registre « MyApplicationRev2 ».</span><span class="sxs-lookup"><span data-stu-id="6aa75-113">This command copies the property named "MyProperty" from the "MyApplication" registry key to the "MyApplicationRev2" registry key.</span></span>

```powershell
Copy-ItemProperty -Path "MyApplication" -Destination "HKLM:\Software\MyApplicationRev2" -Name "MyProperty"
```

## <span data-ttu-id="6aa75-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6aa75-114">PARAMETERS</span></span>

### <span data-ttu-id="6aa75-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="6aa75-115">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="6aa75-116">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6aa75-116">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="6aa75-117">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-117">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="6aa75-118">-Destination</span><span class="sxs-lookup"><span data-stu-id="6aa75-118">-Destination</span></span>

<span data-ttu-id="6aa75-119">Spécifie le chemin d'accès à l'emplacement de destination.</span><span class="sxs-lookup"><span data-stu-id="6aa75-119">Specifies the path to the destination location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6aa75-120">-Exclude</span><span class="sxs-lookup"><span data-stu-id="6aa75-120">-Exclude</span></span>

<span data-ttu-id="6aa75-121">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="6aa75-121">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="6aa75-122">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="6aa75-122">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="6aa75-123">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="6aa75-123">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="6aa75-124">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-124">Wildcard characters are permitted.</span></span> <span data-ttu-id="6aa75-125">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="6aa75-125">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="6aa75-126">-Filter</span><span class="sxs-lookup"><span data-stu-id="6aa75-126">-Filter</span></span>

<span data-ttu-id="6aa75-127">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="6aa75-127">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="6aa75-128">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="6aa75-128">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="6aa75-129">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-129">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="6aa75-130">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-130">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="6aa75-131">-Force</span><span class="sxs-lookup"><span data-stu-id="6aa75-131">-Force</span></span>

<span data-ttu-id="6aa75-132">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6aa75-132">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="6aa75-133">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="6aa75-133">Implementation varies from provider to provider.</span></span>

<span data-ttu-id="6aa75-134">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-134">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="6aa75-135">-Include</span><span class="sxs-lookup"><span data-stu-id="6aa75-135">-Include</span></span>

<span data-ttu-id="6aa75-136">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="6aa75-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="6aa75-137">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="6aa75-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="6aa75-138">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="6aa75-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="6aa75-139">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="6aa75-140">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="6aa75-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="6aa75-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6aa75-141">-LiteralPath</span></span>

<span data-ttu-id="6aa75-142">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="6aa75-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="6aa75-143">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="6aa75-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="6aa75-144">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="6aa75-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6aa75-145">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="6aa75-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6aa75-146">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="6aa75-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="6aa75-147">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="6aa75-148">-Name</span><span class="sxs-lookup"><span data-stu-id="6aa75-148">-Name</span></span>

<span data-ttu-id="6aa75-149">Spécifie le nom de la propriété à copier.</span><span class="sxs-lookup"><span data-stu-id="6aa75-149">Specifies the name of the property to be copied.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6aa75-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="6aa75-150">-PassThru</span></span>

<span data-ttu-id="6aa75-151">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="6aa75-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="6aa75-152">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="6aa75-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="6aa75-153">-Path</span><span class="sxs-lookup"><span data-stu-id="6aa75-153">-Path</span></span>

<span data-ttu-id="6aa75-154">Spécifie, sous forme de tableau de chaînes, le chemin d’accès à la propriété à copier.</span><span class="sxs-lookup"><span data-stu-id="6aa75-154">Specifies, as a string array, the path to the property to be copied.</span></span>
<span data-ttu-id="6aa75-155">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="6aa75-155">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="6aa75-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6aa75-156">-Confirm</span></span>

<span data-ttu-id="6aa75-157">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6aa75-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6aa75-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6aa75-158">-WhatIf</span></span>

<span data-ttu-id="6aa75-159">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6aa75-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6aa75-160">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6aa75-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6aa75-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6aa75-161">CommonParameters</span></span>

<span data-ttu-id="6aa75-162">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="6aa75-162">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="6aa75-163">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-163">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6aa75-164">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6aa75-164">INPUTS</span></span>

### <span data-ttu-id="6aa75-165">System.String</span><span class="sxs-lookup"><span data-stu-id="6aa75-165">System.String</span></span>

<span data-ttu-id="6aa75-166">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6aa75-166">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="6aa75-167">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6aa75-167">OUTPUTS</span></span>

### <span data-ttu-id="6aa75-168">None ou System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="6aa75-168">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="6aa75-169">Quand vous utilisez le paramètre **PassThru** , cette applet de commande génère un **PSCustomObject** représentant la propriété d’élément copiée.</span><span class="sxs-lookup"><span data-stu-id="6aa75-169">When you use the **Passthru** parameter, this cmdlet generates a **PsCustomObject** representing the copied item property.</span></span> <span data-ttu-id="6aa75-170">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="6aa75-170">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6aa75-171">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6aa75-171">NOTES</span></span>

<span data-ttu-id="6aa75-172">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="6aa75-172">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="6aa75-173">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="6aa75-173">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="6aa75-174">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-174">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="6aa75-175">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6aa75-175">RELATED LINKS</span></span>

[<span data-ttu-id="6aa75-176">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6aa75-176">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="6aa75-177">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6aa75-177">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="6aa75-178">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6aa75-178">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="6aa75-179">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6aa75-179">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="6aa75-180">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6aa75-180">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="6aa75-181">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6aa75-181">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="6aa75-182">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="6aa75-182">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="6aa75-183">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6aa75-183">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

