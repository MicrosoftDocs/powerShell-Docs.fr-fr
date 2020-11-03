---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-ItemProperty
ms.openlocfilehash: 35d323b2cffe17619f6d741c296884c8f60e128b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202562"
---
# <span data-ttu-id="fc79c-103">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fc79c-103">Clear-ItemProperty</span></span>

## <span data-ttu-id="fc79c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fc79c-104">SYNOPSIS</span></span>
<span data-ttu-id="fc79c-105">Efface la valeur d’une propriété, mais ne supprime pas la propriété.</span><span class="sxs-lookup"><span data-stu-id="fc79c-105">Clears the value of a property but does not delete the property.</span></span>

## <span data-ttu-id="fc79c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fc79c-106">SYNTAX</span></span>

### <span data-ttu-id="fc79c-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="fc79c-107">Path (Default)</span></span>

```
Clear-ItemProperty [-Path] <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fc79c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fc79c-108">LiteralPath</span></span>

```
Clear-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fc79c-109">Description</span><span class="sxs-lookup"><span data-stu-id="fc79c-109">DESCRIPTION</span></span>

<span data-ttu-id="fc79c-110">L' `Clear-ItemProperty` applet de commande efface la valeur d’une propriété, mais elle ne supprime pas la propriété.</span><span class="sxs-lookup"><span data-stu-id="fc79c-110">The `Clear-ItemProperty` cmdlet clears the value of a property, but it does not delete the property.</span></span>
<span data-ttu-id="fc79c-111">Vous pouvez utiliser cette applet de commande pour supprimer les données d'une valeur du Registre.</span><span class="sxs-lookup"><span data-stu-id="fc79c-111">You can use this cmdlet to delete the data from a registry value.</span></span>

## <span data-ttu-id="fc79c-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fc79c-112">EXAMPLES</span></span>

### <span data-ttu-id="fc79c-113">Exemple 1 : effacer la valeur de la clé de Registre</span><span class="sxs-lookup"><span data-stu-id="fc79c-113">Example 1: Clear the value of registry key</span></span>

<span data-ttu-id="fc79c-114">Cette commande efface les données de la valeur de Registre « Options » dans la sous-clé « MyApp » de `HKEY_LOCAL_MACHINE\Software\MyCompany` .</span><span class="sxs-lookup"><span data-stu-id="fc79c-114">This command clears the data in the "Options" registry value in the "MyApp" subkey of `HKEY_LOCAL_MACHINE\Software\MyCompany`.</span></span>

```powershell
Clear-ItemProperty -Path "HKLM:\Software\MyCompany\MyApp" -Name "Options"
```

## <span data-ttu-id="fc79c-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fc79c-115">PARAMETERS</span></span>

### <span data-ttu-id="fc79c-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="fc79c-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="fc79c-117">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc79c-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="fc79c-118">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="fc79c-119">-Exclude</span><span class="sxs-lookup"><span data-stu-id="fc79c-119">-Exclude</span></span>

<span data-ttu-id="fc79c-120">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="fc79c-120">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="fc79c-121">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="fc79c-121">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fc79c-122">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="fc79c-122">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="fc79c-123">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc79c-123">Wildcard characters are permitted.</span></span> <span data-ttu-id="fc79c-124">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="fc79c-124">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fc79c-125">-Filter</span><span class="sxs-lookup"><span data-stu-id="fc79c-125">-Filter</span></span>

<span data-ttu-id="fc79c-126">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="fc79c-126">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="fc79c-127">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="fc79c-127">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="fc79c-128">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-128">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="fc79c-129">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="fc79c-129">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="fc79c-130">-Force</span><span class="sxs-lookup"><span data-stu-id="fc79c-130">-Force</span></span>

<span data-ttu-id="fc79c-131">Indique que cette applet de commande supprime les propriétés des éléments qui, sinon, ne sont pas accessibles par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fc79c-131">Indicates that this cmdlet deletes properties from items that cannot otherwise be accessed by the user.</span></span> <span data-ttu-id="fc79c-132">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="fc79c-132">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="fc79c-133">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-133">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="fc79c-134">-Include</span><span class="sxs-lookup"><span data-stu-id="fc79c-134">-Include</span></span>

<span data-ttu-id="fc79c-135">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="fc79c-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="fc79c-136">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="fc79c-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fc79c-137">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="fc79c-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="fc79c-138">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc79c-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="fc79c-139">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="fc79c-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fc79c-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fc79c-140">-LiteralPath</span></span>

<span data-ttu-id="fc79c-141">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="fc79c-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="fc79c-142">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="fc79c-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="fc79c-143">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="fc79c-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="fc79c-144">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="fc79c-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="fc79c-145">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="fc79c-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="fc79c-146">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="fc79c-147">-Name</span><span class="sxs-lookup"><span data-stu-id="fc79c-147">-Name</span></span>

<span data-ttu-id="fc79c-148">Spécifie le nom de la propriété à effacer, tel que le nom d'une valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="fc79c-148">Specifies the name of the property to be cleared, such as the name of a registry value.</span></span>
<span data-ttu-id="fc79c-149">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc79c-149">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="fc79c-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fc79c-150">-PassThru</span></span>

<span data-ttu-id="fc79c-151">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fc79c-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="fc79c-152">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="fc79c-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="fc79c-153">-Path</span><span class="sxs-lookup"><span data-stu-id="fc79c-153">-Path</span></span>

<span data-ttu-id="fc79c-154">Spécifie le chemin d'accès à la propriété à effacer.</span><span class="sxs-lookup"><span data-stu-id="fc79c-154">Specifies the path to the property being cleared.</span></span>
<span data-ttu-id="fc79c-155">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc79c-155">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="fc79c-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fc79c-156">-Confirm</span></span>

<span data-ttu-id="fc79c-157">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fc79c-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fc79c-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fc79c-158">-WhatIf</span></span>

<span data-ttu-id="fc79c-159">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fc79c-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fc79c-160">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="fc79c-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fc79c-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc79c-161">CommonParameters</span></span>

<span data-ttu-id="fc79c-162">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="fc79c-162">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="fc79c-163">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-163">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fc79c-164">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fc79c-164">INPUTS</span></span>

### <span data-ttu-id="fc79c-165">System.String</span><span class="sxs-lookup"><span data-stu-id="fc79c-165">System.String</span></span>

<span data-ttu-id="fc79c-166">Vous pouvez diriger une chaîne de chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fc79c-166">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="fc79c-167">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fc79c-167">OUTPUTS</span></span>

### <span data-ttu-id="fc79c-168">None ou System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="fc79c-168">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="fc79c-169">Quand vous utilisez le paramètre **PassThru** , `Clear-ItemProperty` génère un objet **PSCustomObject** qui représente la propriété d’élément effacée.</span><span class="sxs-lookup"><span data-stu-id="fc79c-169">When you use the **PassThru** parameter, `Clear-ItemProperty` generates a **PSCustomObject** object that represents the cleared item property.</span></span> <span data-ttu-id="fc79c-170">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="fc79c-170">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fc79c-171">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fc79c-171">NOTES</span></span>

- <span data-ttu-id="fc79c-172">Vous pouvez utiliser `Clear-ItemProperty` pour supprimer les données dans les valeurs de registre sans supprimer la valeur.</span><span class="sxs-lookup"><span data-stu-id="fc79c-172">You can use `Clear-ItemProperty` to delete the data in registry values without deleting the value.</span></span>
  <span data-ttu-id="fc79c-173">Si les données de la valeur sont de type Binaire ou DWORD, l'effacement des données rend la valeur égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="fc79c-173">If the data type of the value is Binary or DWORD, clearing the data sets the value to zero.</span></span>
  <span data-ttu-id="fc79c-174">Sinon, la valeur est vide.</span><span class="sxs-lookup"><span data-stu-id="fc79c-174">Otherwise, the value is empty.</span></span>
- <span data-ttu-id="fc79c-175">L' `Clear-ItemProperty` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="fc79c-175">The `Clear-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="fc79c-176">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="fc79c-176">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="fc79c-177">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="fc79c-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fc79c-178">RELATED LINKS</span></span>

[<span data-ttu-id="fc79c-179">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fc79c-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="fc79c-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fc79c-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="fc79c-181">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fc79c-181">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="fc79c-182">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fc79c-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="fc79c-183">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fc79c-183">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="fc79c-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="fc79c-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
