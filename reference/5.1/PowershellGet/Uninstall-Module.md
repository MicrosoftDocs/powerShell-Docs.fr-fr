---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 72cdbd26a909e4be33fa32f67019e4c1f02ce3de
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203874"
---
# <span data-ttu-id="4ddc1-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="4ddc1-103">Uninstall-Module</span></span>

## <span data-ttu-id="4ddc1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4ddc1-104">SYNOPSIS</span></span>
<span data-ttu-id="4ddc1-105">Désinstalle un module.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-105">Uninstalls a module.</span></span>

## <span data-ttu-id="4ddc1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4ddc1-106">SYNTAX</span></span>

### <span data-ttu-id="4ddc1-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4ddc1-107">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="4ddc1-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="4ddc1-108">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4ddc1-109">Description</span><span class="sxs-lookup"><span data-stu-id="4ddc1-109">DESCRIPTION</span></span>

<span data-ttu-id="4ddc1-110">L' `Uninstall-Module` applet de commande désinstalle un module spécifié de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-110">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="4ddc1-111">Vous ne pouvez pas désinstaller un module s’il contient d’autres modules en tant que dépendances.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-111">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="4ddc1-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4ddc1-112">EXAMPLES</span></span>

### <span data-ttu-id="4ddc1-113">Exemple 1 : désinstaller un module</span><span class="sxs-lookup"><span data-stu-id="4ddc1-113">Example 1: Uninstall a module</span></span>

<span data-ttu-id="4ddc1-114">Cet exemple désinstalle un module.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-114">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="4ddc1-115">`Uninstall-Module` utilise le paramètre **Name** pour spécifier le module à désinstaller à partir de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-115">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="4ddc1-116">Exemple 2 : utiliser le pipeline pour désinstaller un module</span><span class="sxs-lookup"><span data-stu-id="4ddc1-116">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="4ddc1-117">Dans cet exemple, le pipeline est utilisé pour désinstaller un module.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-117">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="4ddc1-118">`Get-InstalledModule` utilise le paramètre **Name** pour spécifier le module.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-118">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="4ddc1-119">L’objet est envoyé dans le pipeline à `Uninstall-Module` et est désinstallé.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-119">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="4ddc1-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4ddc1-120">PARAMETERS</span></span>

### <span data-ttu-id="4ddc1-121">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="4ddc1-121">-AllowPrerelease</span></span>

<span data-ttu-id="4ddc1-122">Vous permet de désinstaller un module marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-122">Allows you to uninstall a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4ddc1-123">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="4ddc1-123">-AllVersions</span></span>

<span data-ttu-id="4ddc1-124">Spécifie que vous souhaitez inclure toutes les versions disponibles d’un module.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-124">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="4ddc1-125">Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="4ddc1-125">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4ddc1-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4ddc1-126">-Confirm</span></span>

<span data-ttu-id="4ddc1-127">Vous invite à confirmer l’exécution de l' `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="4ddc1-127">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="4ddc1-128">-Force</span><span class="sxs-lookup"><span data-stu-id="4ddc1-128">-Force</span></span>

<span data-ttu-id="4ddc1-129">Force l' `Uninstall-Module` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-129">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4ddc1-130">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4ddc1-130">-InputObject</span></span>

<span data-ttu-id="4ddc1-131">Accepte un objet **PSRepositoryItemInfo** .</span><span class="sxs-lookup"><span data-stu-id="4ddc1-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="4ddc1-132">Par exemple, `Get-InstalledModule` la sortie vers une variable et l’utilisation de cette variable en tant qu’argument **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="4ddc1-132">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4ddc1-133">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="4ddc1-133">-MaximumVersion</span></span>

<span data-ttu-id="4ddc1-134">Spécifie la version maximale ou la plus récente du module à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-134">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="4ddc1-135">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-135">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4ddc1-136">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="4ddc1-136">-MinimumVersion</span></span>

<span data-ttu-id="4ddc1-137">Spécifie la version minimale du module à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-137">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="4ddc1-138">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-138">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4ddc1-139">-Name</span><span class="sxs-lookup"><span data-stu-id="4ddc1-139">-Name</span></span>

<span data-ttu-id="4ddc1-140">Spécifie un tableau de noms de modules à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-140">Specifies an array of module names to uninstall.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4ddc1-141">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="4ddc1-141">-RequiredVersion</span></span>

<span data-ttu-id="4ddc1-142">Spécifie le numéro de version exact du module à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-142">Specifies the exact version number of the module to uninstall.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4ddc1-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4ddc1-143">-WhatIf</span></span>

<span data-ttu-id="4ddc1-144">Montre ce qui se passe si `Uninstall-Module` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-144">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="4ddc1-145">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="4ddc1-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4ddc1-146">CommonParameters</span></span>

<span data-ttu-id="4ddc1-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4ddc1-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4ddc1-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4ddc1-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4ddc1-149">INPUTS</span></span>

### <span data-ttu-id="4ddc1-150">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="4ddc1-150">PSRepositoryItemInfo</span></span>

<span data-ttu-id="4ddc1-151">`Uninstall-Module` accepte les objets **PSRepositoryItemInfo** à partir du pipeline.</span><span class="sxs-lookup"><span data-stu-id="4ddc1-151">`Uninstall-Module` accepts **PSRepositoryItemInfo** objects from the pipeline.</span></span>

## <span data-ttu-id="4ddc1-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4ddc1-152">OUTPUTS</span></span>

## <span data-ttu-id="4ddc1-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4ddc1-153">NOTES</span></span>

## <span data-ttu-id="4ddc1-154">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4ddc1-154">RELATED LINKS</span></span>

[<span data-ttu-id="4ddc1-155">Find-Module</span><span class="sxs-lookup"><span data-stu-id="4ddc1-155">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="4ddc1-156">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="4ddc1-156">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="4ddc1-157">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="4ddc1-157">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="4ddc1-158">Save-Module</span><span class="sxs-lookup"><span data-stu-id="4ddc1-158">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="4ddc1-159">Update-Module</span><span class="sxs-lookup"><span data-stu-id="4ddc1-159">Update-Module</span></span>](Update-Module.md)
