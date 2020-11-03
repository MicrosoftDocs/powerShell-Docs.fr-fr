---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 4ce6bce60a3f1e87a8512b32166fb3e22f7d737e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202053"
---
# <span data-ttu-id="044fc-103">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="044fc-103">Rename-ItemProperty</span></span>

## <span data-ttu-id="044fc-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="044fc-104">SYNOPSIS</span></span>
<span data-ttu-id="044fc-105">Renomme la propriété d'un élément.</span><span class="sxs-lookup"><span data-stu-id="044fc-105">Renames a property of an item.</span></span>

## <span data-ttu-id="044fc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="044fc-106">SYNTAX</span></span>

### <span data-ttu-id="044fc-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="044fc-107">Path (Default)</span></span>

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="044fc-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="044fc-108">LiteralPath</span></span>

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="044fc-109">Description</span><span class="sxs-lookup"><span data-stu-id="044fc-109">DESCRIPTION</span></span>

<span data-ttu-id="044fc-110">L' `Rename-ItemProperty` applet de commande modifie le nom d’une propriété d’élément spécifiée.</span><span class="sxs-lookup"><span data-stu-id="044fc-110">The `Rename-ItemProperty` cmdlet changes the name of a specified item property.</span></span>
<span data-ttu-id="044fc-111">La valeur de la propriété n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="044fc-111">The value of the property is not changed.</span></span>
<span data-ttu-id="044fc-112">Par exemple, vous pouvez utiliser `Rename-ItemProperty` pour modifier le nom d’une entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="044fc-112">For example, you can use `Rename-ItemProperty` to change the name of a registry entry.</span></span>

## <span data-ttu-id="044fc-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="044fc-113">EXAMPLES</span></span>

### <span data-ttu-id="044fc-114">Exemple 1 : renommer une entrée de Registre</span><span class="sxs-lookup"><span data-stu-id="044fc-114">Example 1: Rename a registry entry</span></span>

<span data-ttu-id="044fc-115">Cette commande renomme l’entrée de registre de configuration contenue dans la `HKEY_LOCAL_MACHINE\Software\SmpApplication` clé en « oldconfig »».</span><span class="sxs-lookup"><span data-stu-id="044fc-115">This command renames the config registry entry that is contained in the `HKEY_LOCAL_MACHINE\Software\SmpApplication` key to "oldconfig".</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## <span data-ttu-id="044fc-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="044fc-116">PARAMETERS</span></span>

### <span data-ttu-id="044fc-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="044fc-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="044fc-118">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="044fc-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="044fc-119">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="044fc-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="044fc-120">-Exclude</span><span class="sxs-lookup"><span data-stu-id="044fc-120">-Exclude</span></span>

<span data-ttu-id="044fc-121">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="044fc-121">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="044fc-122">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="044fc-122">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="044fc-123">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="044fc-123">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="044fc-124">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="044fc-124">Wildcard characters are permitted.</span></span> <span data-ttu-id="044fc-125">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="044fc-125">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="044fc-126">-Filter</span><span class="sxs-lookup"><span data-stu-id="044fc-126">-Filter</span></span>

<span data-ttu-id="044fc-127">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="044fc-127">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="044fc-128">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="044fc-128">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="044fc-129">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="044fc-129">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="044fc-130">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="044fc-130">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="044fc-131">-Force</span><span class="sxs-lookup"><span data-stu-id="044fc-131">-Force</span></span>

<span data-ttu-id="044fc-132">Force l’applet de commande à renommer une propriété d’un objet qui, sinon, n’est pas accessible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="044fc-132">Forces the cmdlet to rename a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="044fc-133">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="044fc-133">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="044fc-134">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="044fc-134">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="044fc-135">-Include</span><span class="sxs-lookup"><span data-stu-id="044fc-135">-Include</span></span>

<span data-ttu-id="044fc-136">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="044fc-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="044fc-137">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="044fc-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="044fc-138">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="044fc-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="044fc-139">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="044fc-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="044fc-140">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="044fc-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="044fc-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="044fc-141">-LiteralPath</span></span>

<span data-ttu-id="044fc-142">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="044fc-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="044fc-143">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="044fc-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="044fc-144">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="044fc-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="044fc-145">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="044fc-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="044fc-146">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="044fc-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="044fc-147">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="044fc-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="044fc-148">-Name</span><span class="sxs-lookup"><span data-stu-id="044fc-148">-Name</span></span>

<span data-ttu-id="044fc-149">Spécifie le nom actuel de la propriété à renommer.</span><span class="sxs-lookup"><span data-stu-id="044fc-149">Specifies the current name of the property to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="044fc-150">-NewName</span><span class="sxs-lookup"><span data-stu-id="044fc-150">-NewName</span></span>

<span data-ttu-id="044fc-151">Spécifie le nouveau nom pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="044fc-151">Specifies the new name for the property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="044fc-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="044fc-152">-PassThru</span></span>

<span data-ttu-id="044fc-153">Retourne un objet qui représente la propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="044fc-153">Returns an object that represents the item property.</span></span>
<span data-ttu-id="044fc-154">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="044fc-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="044fc-155">-Path</span><span class="sxs-lookup"><span data-stu-id="044fc-155">-Path</span></span>

<span data-ttu-id="044fc-156">Spécifie le chemin d’accès de l’élément à renommer.</span><span class="sxs-lookup"><span data-stu-id="044fc-156">Specifies the path of the item to rename.</span></span>
<span data-ttu-id="044fc-157">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="044fc-157">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="044fc-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="044fc-158">-Confirm</span></span>

<span data-ttu-id="044fc-159">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="044fc-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="044fc-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="044fc-160">-WhatIf</span></span>

<span data-ttu-id="044fc-161">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="044fc-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="044fc-162">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="044fc-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="044fc-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="044fc-163">CommonParameters</span></span>

<span data-ttu-id="044fc-164">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="044fc-164">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="044fc-165">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="044fc-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="044fc-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="044fc-166">INPUTS</span></span>

### <span data-ttu-id="044fc-167">System.String</span><span class="sxs-lookup"><span data-stu-id="044fc-167">System.String</span></span>

<span data-ttu-id="044fc-168">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="044fc-168">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="044fc-169">SORTIES</span><span class="sxs-lookup"><span data-stu-id="044fc-169">OUTPUTS</span></span>

### <span data-ttu-id="044fc-170">Aucun, System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="044fc-170">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="044fc-171">Cette applet de commande génère un **PSCustomObject** qui représente la propriété d’élément renommée, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="044fc-171">This cmdlet generates a **PSCustomObject** that represents the renamed item property, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="044fc-172">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="044fc-172">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="044fc-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="044fc-173">NOTES</span></span>

<span data-ttu-id="044fc-174">`Remove-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="044fc-174">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="044fc-175">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="044fc-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="044fc-176">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="044fc-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="044fc-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="044fc-177">RELATED LINKS</span></span>

[<span data-ttu-id="044fc-178">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="044fc-178">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="044fc-179">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="044fc-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="044fc-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="044fc-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="044fc-181">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="044fc-181">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="044fc-182">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="044fc-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="044fc-183">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="044fc-183">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="044fc-184">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="044fc-184">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="044fc-185">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="044fc-185">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="044fc-186">about_Providers</span><span class="sxs-lookup"><span data-stu-id="044fc-186">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

