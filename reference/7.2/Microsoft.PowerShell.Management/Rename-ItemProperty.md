---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 4fbd2677d6a978d4d144effe9607bceb376ad43f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598577"
---
# <span data-ttu-id="38cda-102">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38cda-102">Rename-ItemProperty</span></span>

## <span data-ttu-id="38cda-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="38cda-103">SYNOPSIS</span></span>
<span data-ttu-id="38cda-104">Renomme la propriété d'un élément.</span><span class="sxs-lookup"><span data-stu-id="38cda-104">Renames a property of an item.</span></span>

## <span data-ttu-id="38cda-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="38cda-105">SYNTAX</span></span>

### <span data-ttu-id="38cda-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="38cda-106">Path (Default)</span></span>

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="38cda-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="38cda-107">LiteralPath</span></span>

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="38cda-108">Description</span><span class="sxs-lookup"><span data-stu-id="38cda-108">DESCRIPTION</span></span>

<span data-ttu-id="38cda-109">L' `Rename-ItemProperty` applet de commande modifie le nom d’une propriété d’élément spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38cda-109">The `Rename-ItemProperty` cmdlet changes the name of a specified item property.</span></span>
<span data-ttu-id="38cda-110">La valeur de la propriété n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="38cda-110">The value of the property is not changed.</span></span>
<span data-ttu-id="38cda-111">Par exemple, vous pouvez utiliser `Rename-ItemProperty` pour modifier le nom d’une entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="38cda-111">For example, you can use `Rename-ItemProperty` to change the name of a registry entry.</span></span>

## <span data-ttu-id="38cda-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="38cda-112">EXAMPLES</span></span>

### <span data-ttu-id="38cda-113">Exemple 1 : renommer une entrée de Registre</span><span class="sxs-lookup"><span data-stu-id="38cda-113">Example 1: Rename a registry entry</span></span>

<span data-ttu-id="38cda-114">Cette commande renomme l’entrée de registre de configuration contenue dans la `HKEY_LOCAL_MACHINE\Software\SmpApplication` clé en « oldconfig »».</span><span class="sxs-lookup"><span data-stu-id="38cda-114">This command renames the config registry entry that is contained in the `HKEY_LOCAL_MACHINE\Software\SmpApplication` key to "oldconfig".</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## <span data-ttu-id="38cda-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38cda-115">PARAMETERS</span></span>

### <span data-ttu-id="38cda-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="38cda-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="38cda-117">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38cda-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="38cda-118">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="38cda-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="38cda-119">-Exclude</span><span class="sxs-lookup"><span data-stu-id="38cda-119">-Exclude</span></span>

<span data-ttu-id="38cda-120">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="38cda-120">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="38cda-121">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="38cda-121">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="38cda-122">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="38cda-122">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="38cda-123">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="38cda-123">Wildcard characters are permitted.</span></span> <span data-ttu-id="38cda-124">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="38cda-124">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="38cda-125">-Filter</span><span class="sxs-lookup"><span data-stu-id="38cda-125">-Filter</span></span>

<span data-ttu-id="38cda-126">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="38cda-126">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="38cda-127">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="38cda-127">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="38cda-128">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="38cda-128">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="38cda-129">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="38cda-129">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="38cda-130">-Force</span><span class="sxs-lookup"><span data-stu-id="38cda-130">-Force</span></span>

<span data-ttu-id="38cda-131">Force l’applet de commande à renommer une propriété d’un objet qui, sinon, n’est pas accessible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38cda-131">Forces the cmdlet to rename a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="38cda-132">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="38cda-132">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="38cda-133">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="38cda-133">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="38cda-134">-Include</span><span class="sxs-lookup"><span data-stu-id="38cda-134">-Include</span></span>

<span data-ttu-id="38cda-135">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="38cda-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="38cda-136">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="38cda-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="38cda-137">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="38cda-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="38cda-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="38cda-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="38cda-139">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="38cda-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="38cda-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="38cda-140">-LiteralPath</span></span>

<span data-ttu-id="38cda-141">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="38cda-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="38cda-142">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="38cda-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="38cda-143">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="38cda-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="38cda-144">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="38cda-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="38cda-145">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="38cda-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="38cda-146">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="38cda-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="38cda-147">-Name</span><span class="sxs-lookup"><span data-stu-id="38cda-147">-Name</span></span>

<span data-ttu-id="38cda-148">Spécifie le nom actuel de la propriété à renommer.</span><span class="sxs-lookup"><span data-stu-id="38cda-148">Specifies the current name of the property to rename.</span></span>

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

### <span data-ttu-id="38cda-149">-NewName</span><span class="sxs-lookup"><span data-stu-id="38cda-149">-NewName</span></span>

<span data-ttu-id="38cda-150">Spécifie le nouveau nom pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="38cda-150">Specifies the new name for the property.</span></span>

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

### <span data-ttu-id="38cda-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="38cda-151">-PassThru</span></span>

<span data-ttu-id="38cda-152">Retourne un objet qui représente la propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="38cda-152">Returns an object that represents the item property.</span></span>
<span data-ttu-id="38cda-153">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="38cda-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="38cda-154">-Path</span><span class="sxs-lookup"><span data-stu-id="38cda-154">-Path</span></span>

<span data-ttu-id="38cda-155">Spécifie le chemin d’accès de l’élément à renommer.</span><span class="sxs-lookup"><span data-stu-id="38cda-155">Specifies the path of the item to rename.</span></span>
<span data-ttu-id="38cda-156">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="38cda-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="38cda-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="38cda-157">-Confirm</span></span>

<span data-ttu-id="38cda-158">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38cda-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="38cda-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="38cda-159">-WhatIf</span></span>

<span data-ttu-id="38cda-160">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38cda-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="38cda-161">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="38cda-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="38cda-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38cda-162">CommonParameters</span></span>

<span data-ttu-id="38cda-163">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="38cda-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="38cda-164">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="38cda-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="38cda-165">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="38cda-165">INPUTS</span></span>

### <span data-ttu-id="38cda-166">System.String</span><span class="sxs-lookup"><span data-stu-id="38cda-166">System.String</span></span>

<span data-ttu-id="38cda-167">Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38cda-167">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="38cda-168">SORTIES</span><span class="sxs-lookup"><span data-stu-id="38cda-168">OUTPUTS</span></span>

### <span data-ttu-id="38cda-169">Aucun, System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="38cda-169">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="38cda-170">Cette applet de commande génère un **PSCustomObject** qui représente la propriété d’élément renommée, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="38cda-170">This cmdlet generates a **PSCustomObject** that represents the renamed item property, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="38cda-171">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="38cda-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="38cda-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="38cda-172">NOTES</span></span>

<span data-ttu-id="38cda-173">`Remove-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="38cda-173">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="38cda-174">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="38cda-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="38cda-175">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="38cda-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="38cda-176">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="38cda-176">RELATED LINKS</span></span>

[<span data-ttu-id="38cda-177">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38cda-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="38cda-178">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38cda-178">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="38cda-179">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38cda-179">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="38cda-180">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38cda-180">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="38cda-181">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38cda-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="38cda-182">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38cda-182">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="38cda-183">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="38cda-183">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="38cda-184">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38cda-184">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="38cda-185">about_Providers</span><span class="sxs-lookup"><span data-stu-id="38cda-185">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

