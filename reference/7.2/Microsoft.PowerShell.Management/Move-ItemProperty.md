---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 92a14e4bd165efd4721e3802cade827744c9c056
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597163"
---
# <span data-ttu-id="609a0-102">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="609a0-102">Move-ItemProperty</span></span>

## <span data-ttu-id="609a0-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="609a0-103">Synopsis</span></span>
<span data-ttu-id="609a0-104">Déplace une propriété d'un emplacement à un autre.</span><span class="sxs-lookup"><span data-stu-id="609a0-104">Moves a property from one location to another.</span></span>

## <span data-ttu-id="609a0-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="609a0-105">SYNTAX</span></span>

### <span data-ttu-id="609a0-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="609a0-106">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="609a0-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="609a0-107">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="609a0-108">Description</span><span class="sxs-lookup"><span data-stu-id="609a0-108">Description</span></span>

<span data-ttu-id="609a0-109">L' `Move-ItemProperty` applet de commande déplace une propriété d’un élément d’un élément à un autre.</span><span class="sxs-lookup"><span data-stu-id="609a0-109">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="609a0-110">Par exemple, il peut déplacer une entrée de registre d’une clé de Registre vers une autre clé de registre.</span><span class="sxs-lookup"><span data-stu-id="609a0-110">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="609a0-111">Lors du déplacement d’une propriété d’élément, celle-ci est ajoutée au nouvel emplacement et supprimée de l’emplacement d’origine.</span><span class="sxs-lookup"><span data-stu-id="609a0-111">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="609a0-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="609a0-112">EXAMPLES</span></span>

### <span data-ttu-id="609a0-113">Exemple 1 : déplacer une valeur de Registre et ses données vers une autre clé</span><span class="sxs-lookup"><span data-stu-id="609a0-113">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="609a0-114">Cette commande déplace la valeur de registre de la version, ainsi que ses données, de la sous-clé « MyApp » vers la sous-clé NewApp de la `HKLM\Software\MyCompany` clé de registre.</span><span class="sxs-lookup"><span data-stu-id="609a0-114">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="609a0-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="609a0-115">PARAMETERS</span></span>

### <span data-ttu-id="609a0-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="609a0-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="609a0-117">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="609a0-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="609a0-118">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="609a0-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="609a0-119">-Destination</span><span class="sxs-lookup"><span data-stu-id="609a0-119">-Destination</span></span>

<span data-ttu-id="609a0-120">Spécifie le chemin d'accès à l'emplacement de destination.</span><span class="sxs-lookup"><span data-stu-id="609a0-120">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="609a0-121">-Exclude</span><span class="sxs-lookup"><span data-stu-id="609a0-121">-Exclude</span></span>

<span data-ttu-id="609a0-122">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="609a0-122">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="609a0-123">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="609a0-123">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="609a0-124">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="609a0-124">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="609a0-125">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="609a0-125">Wildcard characters are permitted.</span></span> <span data-ttu-id="609a0-126">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="609a0-126">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="609a0-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="609a0-127">-Filter</span></span>

<span data-ttu-id="609a0-128">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="609a0-128">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="609a0-129">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="609a0-129">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="609a0-130">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="609a0-130">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="609a0-131">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="609a0-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="609a0-132">-Force</span><span class="sxs-lookup"><span data-stu-id="609a0-132">-Force</span></span>

<span data-ttu-id="609a0-133">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="609a0-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="609a0-134">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="609a0-134">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="609a0-135">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="609a0-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="609a0-136">-Include</span><span class="sxs-lookup"><span data-stu-id="609a0-136">-Include</span></span>

<span data-ttu-id="609a0-137">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="609a0-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="609a0-138">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="609a0-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="609a0-139">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="609a0-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="609a0-140">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="609a0-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="609a0-141">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="609a0-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="609a0-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="609a0-142">-LiteralPath</span></span>

<span data-ttu-id="609a0-143">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="609a0-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="609a0-144">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="609a0-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="609a0-145">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="609a0-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="609a0-146">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="609a0-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="609a0-147">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="609a0-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="609a0-148">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="609a0-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="609a0-149">-Name</span><span class="sxs-lookup"><span data-stu-id="609a0-149">-Name</span></span>

<span data-ttu-id="609a0-150">Spécifie le nom de la propriété à déplacer.</span><span class="sxs-lookup"><span data-stu-id="609a0-150">Specifies the name of the property to be moved.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="609a0-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="609a0-151">-PassThru</span></span>

<span data-ttu-id="609a0-152">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="609a0-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="609a0-153">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="609a0-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="609a0-154">-Path</span><span class="sxs-lookup"><span data-stu-id="609a0-154">-Path</span></span>

<span data-ttu-id="609a0-155">Spécifie le chemin d’accès à l’emplacement actuel de la propriété.</span><span class="sxs-lookup"><span data-stu-id="609a0-155">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="609a0-156">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="609a0-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="609a0-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="609a0-157">-Confirm</span></span>

<span data-ttu-id="609a0-158">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="609a0-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="609a0-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="609a0-159">-WhatIf</span></span>

<span data-ttu-id="609a0-160">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="609a0-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="609a0-161">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="609a0-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="609a0-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="609a0-162">CommonParameters</span></span>

<span data-ttu-id="609a0-163">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="609a0-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="609a0-164">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="609a0-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="609a0-165">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="609a0-165">INPUTS</span></span>

### <span data-ttu-id="609a0-166">System.String</span><span class="sxs-lookup"><span data-stu-id="609a0-166">System.String</span></span>

<span data-ttu-id="609a0-167">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="609a0-167">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="609a0-168">SORTIES</span><span class="sxs-lookup"><span data-stu-id="609a0-168">OUTPUTS</span></span>

### <span data-ttu-id="609a0-169">None ou System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="609a0-169">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="609a0-170">Quand vous utilisez le paramètre **PassThru** , cette applet de commande génère un **PSCustomObject** représentant la propriété d’élément déplacée.</span><span class="sxs-lookup"><span data-stu-id="609a0-170">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span> <span data-ttu-id="609a0-171">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="609a0-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="609a0-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="609a0-172">NOTES</span></span>

<span data-ttu-id="609a0-173">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="609a0-173">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="609a0-174">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="609a0-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="609a0-175">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="609a0-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="609a0-176">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="609a0-176">RELATED LINKS</span></span>

[<span data-ttu-id="609a0-177">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="609a0-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="609a0-178">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="609a0-178">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="609a0-179">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="609a0-179">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="609a0-180">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="609a0-180">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="609a0-181">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="609a0-181">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="609a0-182">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="609a0-182">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="609a0-183">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="609a0-183">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="609a0-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="609a0-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
