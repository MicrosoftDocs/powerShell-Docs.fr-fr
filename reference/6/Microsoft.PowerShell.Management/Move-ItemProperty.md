---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 235991da33ae49f8d1dd9b379432963a8930ebc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202878"
---
# <span data-ttu-id="2463b-103">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2463b-103">Move-ItemProperty</span></span>

## <span data-ttu-id="2463b-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="2463b-104">Synopsis</span></span>
<span data-ttu-id="2463b-105">Déplace une propriété d'un emplacement à un autre.</span><span class="sxs-lookup"><span data-stu-id="2463b-105">Moves a property from one location to another.</span></span>

## <span data-ttu-id="2463b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2463b-106">SYNTAX</span></span>

### <span data-ttu-id="2463b-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="2463b-107">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2463b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2463b-108">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2463b-109">Description</span><span class="sxs-lookup"><span data-stu-id="2463b-109">Description</span></span>

<span data-ttu-id="2463b-110">L' `Move-ItemProperty` applet de commande déplace une propriété d’un élément d’un élément à un autre.</span><span class="sxs-lookup"><span data-stu-id="2463b-110">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="2463b-111">Par exemple, il peut déplacer une entrée de registre d’une clé de Registre vers une autre clé de registre.</span><span class="sxs-lookup"><span data-stu-id="2463b-111">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="2463b-112">Lors du déplacement d’une propriété d’élément, celle-ci est ajoutée au nouvel emplacement et supprimée de l’emplacement d’origine.</span><span class="sxs-lookup"><span data-stu-id="2463b-112">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="2463b-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2463b-113">EXAMPLES</span></span>

### <span data-ttu-id="2463b-114">Exemple 1 : déplacer une valeur de Registre et ses données vers une autre clé</span><span class="sxs-lookup"><span data-stu-id="2463b-114">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="2463b-115">Cette commande déplace la valeur de registre de la version, ainsi que ses données, de la sous-clé « MyApp » vers la sous-clé NewApp de la `HKLM\Software\MyCompany` clé de registre.</span><span class="sxs-lookup"><span data-stu-id="2463b-115">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="2463b-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2463b-116">PARAMETERS</span></span>

### <span data-ttu-id="2463b-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="2463b-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2463b-118">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2463b-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="2463b-119">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="2463b-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="2463b-120">-Destination</span><span class="sxs-lookup"><span data-stu-id="2463b-120">-Destination</span></span>

<span data-ttu-id="2463b-121">Spécifie le chemin d'accès à l'emplacement de destination.</span><span class="sxs-lookup"><span data-stu-id="2463b-121">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="2463b-122">-Exclude</span><span class="sxs-lookup"><span data-stu-id="2463b-122">-Exclude</span></span>

<span data-ttu-id="2463b-123">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="2463b-123">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="2463b-124">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="2463b-124">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2463b-125">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="2463b-125">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="2463b-126">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2463b-126">Wildcard characters are permitted.</span></span> <span data-ttu-id="2463b-127">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="2463b-127">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2463b-128">-Filter</span><span class="sxs-lookup"><span data-stu-id="2463b-128">-Filter</span></span>

<span data-ttu-id="2463b-129">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="2463b-129">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="2463b-130">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="2463b-130">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="2463b-131">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="2463b-131">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="2463b-132">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="2463b-132">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="2463b-133">-Force</span><span class="sxs-lookup"><span data-stu-id="2463b-133">-Force</span></span>

<span data-ttu-id="2463b-134">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2463b-134">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="2463b-135">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="2463b-135">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="2463b-136">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2463b-136">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="2463b-137">-Include</span><span class="sxs-lookup"><span data-stu-id="2463b-137">-Include</span></span>

<span data-ttu-id="2463b-138">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="2463b-138">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="2463b-139">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="2463b-139">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2463b-140">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="2463b-140">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="2463b-141">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2463b-141">Wildcard characters are permitted.</span></span> <span data-ttu-id="2463b-142">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="2463b-142">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2463b-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2463b-143">-LiteralPath</span></span>

<span data-ttu-id="2463b-144">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="2463b-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="2463b-145">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="2463b-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="2463b-146">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="2463b-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2463b-147">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="2463b-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2463b-148">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="2463b-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="2463b-149">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="2463b-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="2463b-150">-Name</span><span class="sxs-lookup"><span data-stu-id="2463b-150">-Name</span></span>

<span data-ttu-id="2463b-151">Spécifie le nom de la propriété à déplacer.</span><span class="sxs-lookup"><span data-stu-id="2463b-151">Specifies the name of the property to be moved.</span></span>

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

### <span data-ttu-id="2463b-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2463b-152">-PassThru</span></span>

<span data-ttu-id="2463b-153">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="2463b-153">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="2463b-154">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="2463b-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="2463b-155">-Path</span><span class="sxs-lookup"><span data-stu-id="2463b-155">-Path</span></span>

<span data-ttu-id="2463b-156">Spécifie le chemin d’accès à l’emplacement actuel de la propriété.</span><span class="sxs-lookup"><span data-stu-id="2463b-156">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="2463b-157">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="2463b-157">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="2463b-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2463b-158">-Confirm</span></span>

<span data-ttu-id="2463b-159">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2463b-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2463b-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2463b-160">-WhatIf</span></span>

<span data-ttu-id="2463b-161">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2463b-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2463b-162">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="2463b-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2463b-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2463b-163">CommonParameters</span></span>

<span data-ttu-id="2463b-164">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="2463b-164">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2463b-165">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="2463b-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2463b-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2463b-166">INPUTS</span></span>

### <span data-ttu-id="2463b-167">System.String</span><span class="sxs-lookup"><span data-stu-id="2463b-167">System.String</span></span>

<span data-ttu-id="2463b-168">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2463b-168">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="2463b-169">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2463b-169">OUTPUTS</span></span>

### <span data-ttu-id="2463b-170">None ou System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="2463b-170">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="2463b-171">Quand vous utilisez le paramètre **PassThru** , cette applet de commande génère un **PSCustomObject** représentant la propriété d’élément déplacée.</span><span class="sxs-lookup"><span data-stu-id="2463b-171">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span> <span data-ttu-id="2463b-172">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="2463b-172">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2463b-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2463b-173">NOTES</span></span>

<span data-ttu-id="2463b-174">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="2463b-174">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2463b-175">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="2463b-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="2463b-176">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2463b-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2463b-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2463b-177">RELATED LINKS</span></span>

[<span data-ttu-id="2463b-178">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2463b-178">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="2463b-179">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2463b-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="2463b-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2463b-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="2463b-181">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2463b-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="2463b-182">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2463b-182">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="2463b-183">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2463b-183">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="2463b-184">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2463b-184">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="2463b-185">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2463b-185">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
