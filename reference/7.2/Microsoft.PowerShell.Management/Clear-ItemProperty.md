---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-ItemProperty
ms.openlocfilehash: fc454095f9610e8712af18bfe1558e275324cefe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595725"
---
# <span data-ttu-id="a6133-102">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a6133-102">Clear-ItemProperty</span></span>

## <span data-ttu-id="a6133-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a6133-103">SYNOPSIS</span></span>
<span data-ttu-id="a6133-104">Efface la valeur d’une propriété, mais ne supprime pas la propriété.</span><span class="sxs-lookup"><span data-stu-id="a6133-104">Clears the value of a property but does not delete the property.</span></span>

## <span data-ttu-id="a6133-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a6133-105">SYNTAX</span></span>

### <span data-ttu-id="a6133-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a6133-106">Path (Default)</span></span>

```
Clear-ItemProperty [-Path] <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a6133-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a6133-107">LiteralPath</span></span>

```
Clear-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a6133-108">Description</span><span class="sxs-lookup"><span data-stu-id="a6133-108">DESCRIPTION</span></span>

<span data-ttu-id="a6133-109">L' `Clear-ItemProperty` applet de commande efface la valeur d’une propriété, mais elle ne supprime pas la propriété.</span><span class="sxs-lookup"><span data-stu-id="a6133-109">The `Clear-ItemProperty` cmdlet clears the value of a property, but it does not delete the property.</span></span>
<span data-ttu-id="a6133-110">Vous pouvez utiliser cette applet de commande pour supprimer les données d'une valeur du Registre.</span><span class="sxs-lookup"><span data-stu-id="a6133-110">You can use this cmdlet to delete the data from a registry value.</span></span>

## <span data-ttu-id="a6133-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a6133-111">EXAMPLES</span></span>

### <span data-ttu-id="a6133-112">Exemple 1 : effacer la valeur de la clé de Registre</span><span class="sxs-lookup"><span data-stu-id="a6133-112">Example 1: Clear the value of registry key</span></span>

<span data-ttu-id="a6133-113">Cette commande efface les données de la valeur de Registre « Options » dans la sous-clé « MyApp » de `HKEY_LOCAL_MACHINE\Software\MyCompany` .</span><span class="sxs-lookup"><span data-stu-id="a6133-113">This command clears the data in the "Options" registry value in the "MyApp" subkey of `HKEY_LOCAL_MACHINE\Software\MyCompany`.</span></span>

```powershell
Clear-ItemProperty -Path "HKLM:\Software\MyCompany\MyApp" -Name "Options"
```

## <span data-ttu-id="a6133-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a6133-114">PARAMETERS</span></span>

### <span data-ttu-id="a6133-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="a6133-115">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a6133-116">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6133-116">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a6133-117">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="a6133-117">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a6133-118">-Exclude</span><span class="sxs-lookup"><span data-stu-id="a6133-118">-Exclude</span></span>

<span data-ttu-id="a6133-119">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="a6133-119">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a6133-120">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="a6133-120">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a6133-121">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a6133-121">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a6133-122">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a6133-122">Wildcard characters are permitted.</span></span> <span data-ttu-id="a6133-123">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="a6133-123">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a6133-124">-Filter</span><span class="sxs-lookup"><span data-stu-id="a6133-124">-Filter</span></span>

<span data-ttu-id="a6133-125">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="a6133-125">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a6133-126">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="a6133-126">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a6133-127">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="a6133-127">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a6133-128">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="a6133-128">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a6133-129">-Force</span><span class="sxs-lookup"><span data-stu-id="a6133-129">-Force</span></span>

<span data-ttu-id="a6133-130">Indique que cette applet de commande supprime les propriétés des éléments qui, sinon, ne sont pas accessibles par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a6133-130">Indicates that this cmdlet deletes properties from items that cannot otherwise be accessed by the user.</span></span> <span data-ttu-id="a6133-131">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="a6133-131">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="a6133-132">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a6133-132">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="a6133-133">-Include</span><span class="sxs-lookup"><span data-stu-id="a6133-133">-Include</span></span>

<span data-ttu-id="a6133-134">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="a6133-134">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a6133-135">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="a6133-135">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a6133-136">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="a6133-136">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a6133-137">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a6133-137">Wildcard characters are permitted.</span></span> <span data-ttu-id="a6133-138">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="a6133-138">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a6133-139">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a6133-139">-LiteralPath</span></span>

<span data-ttu-id="a6133-140">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="a6133-140">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a6133-141">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="a6133-141">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a6133-142">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a6133-142">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a6133-143">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a6133-143">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a6133-144">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a6133-144">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a6133-145">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="a6133-145">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="a6133-146">-Name</span><span class="sxs-lookup"><span data-stu-id="a6133-146">-Name</span></span>

<span data-ttu-id="a6133-147">Spécifie le nom de la propriété à effacer, tel que le nom d'une valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="a6133-147">Specifies the name of the property to be cleared, such as the name of a registry value.</span></span>
<span data-ttu-id="a6133-148">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a6133-148">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a6133-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a6133-149">-PassThru</span></span>

<span data-ttu-id="a6133-150">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="a6133-150">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="a6133-151">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="a6133-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a6133-152">-Path</span><span class="sxs-lookup"><span data-stu-id="a6133-152">-Path</span></span>

<span data-ttu-id="a6133-153">Spécifie le chemin d'accès à la propriété à effacer.</span><span class="sxs-lookup"><span data-stu-id="a6133-153">Specifies the path to the property being cleared.</span></span>
<span data-ttu-id="a6133-154">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a6133-154">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a6133-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a6133-155">-Confirm</span></span>

<span data-ttu-id="a6133-156">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a6133-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a6133-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a6133-157">-WhatIf</span></span>

<span data-ttu-id="a6133-158">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a6133-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a6133-159">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a6133-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a6133-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6133-160">CommonParameters</span></span>

<span data-ttu-id="a6133-161">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a6133-161">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a6133-162">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a6133-162">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a6133-163">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a6133-163">INPUTS</span></span>

### <span data-ttu-id="a6133-164">System.String</span><span class="sxs-lookup"><span data-stu-id="a6133-164">System.String</span></span>

<span data-ttu-id="a6133-165">Vous pouvez diriger une chaîne de chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a6133-165">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="a6133-166">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a6133-166">OUTPUTS</span></span>

### <span data-ttu-id="a6133-167">None ou System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a6133-167">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="a6133-168">Quand vous utilisez le paramètre **PassThru** , `Clear-ItemProperty` génère un objet **PSCustomObject** qui représente la propriété d’élément effacée.</span><span class="sxs-lookup"><span data-stu-id="a6133-168">When you use the **PassThru** parameter, `Clear-ItemProperty` generates a **PSCustomObject** object that represents the cleared item property.</span></span> <span data-ttu-id="a6133-169">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a6133-169">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a6133-170">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a6133-170">NOTES</span></span>

- <span data-ttu-id="a6133-171">Vous pouvez utiliser `Clear-ItemProperty` pour supprimer les données dans les valeurs de registre sans supprimer la valeur.</span><span class="sxs-lookup"><span data-stu-id="a6133-171">You can use `Clear-ItemProperty` to delete the data in registry values without deleting the value.</span></span>
  <span data-ttu-id="a6133-172">Si les données de la valeur sont de type Binaire ou DWORD, l'effacement des données rend la valeur égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="a6133-172">If the data type of the value is Binary or DWORD, clearing the data sets the value to zero.</span></span>
  <span data-ttu-id="a6133-173">Sinon, la valeur est vide.</span><span class="sxs-lookup"><span data-stu-id="a6133-173">Otherwise, the value is empty.</span></span>
- <span data-ttu-id="a6133-174">L' `Clear-ItemProperty` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a6133-174">The `Clear-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a6133-175">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a6133-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a6133-176">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a6133-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a6133-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a6133-177">RELATED LINKS</span></span>

[<span data-ttu-id="a6133-178">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a6133-178">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="a6133-179">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a6133-179">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="a6133-180">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a6133-180">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="a6133-181">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a6133-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="a6133-182">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a6133-182">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="a6133-183">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a6133-183">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

