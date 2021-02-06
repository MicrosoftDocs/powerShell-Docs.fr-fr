---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 0df911ad8b1f7b4516eef4a1c2b0180893013e3e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596345"
---
# <span data-ttu-id="bdcdc-102">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="bdcdc-102">Uninstall-Module</span></span>

## <span data-ttu-id="bdcdc-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bdcdc-103">SYNOPSIS</span></span>
<span data-ttu-id="bdcdc-104">Désinstalle un module.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-104">Uninstalls a module.</span></span>

## <span data-ttu-id="bdcdc-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="bdcdc-105">SYNTAX</span></span>

### <span data-ttu-id="bdcdc-106">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="bdcdc-106">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="bdcdc-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="bdcdc-107">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bdcdc-108">Description</span><span class="sxs-lookup"><span data-stu-id="bdcdc-108">DESCRIPTION</span></span>

<span data-ttu-id="bdcdc-109">L' `Uninstall-Module` applet de commande désinstalle un module spécifié de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-109">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="bdcdc-110">Vous ne pouvez pas désinstaller un module s’il contient d’autres modules en tant que dépendances.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-110">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="bdcdc-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bdcdc-111">EXAMPLES</span></span>

### <span data-ttu-id="bdcdc-112">Exemple 1 : désinstaller un module</span><span class="sxs-lookup"><span data-stu-id="bdcdc-112">Example 1: Uninstall a module</span></span>

<span data-ttu-id="bdcdc-113">Cet exemple désinstalle un module.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-113">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="bdcdc-114">`Uninstall-Module` utilise le paramètre **Name** pour spécifier le module à désinstaller à partir de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-114">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="bdcdc-115">Exemple 2 : utiliser le pipeline pour désinstaller un module</span><span class="sxs-lookup"><span data-stu-id="bdcdc-115">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="bdcdc-116">Dans cet exemple, le pipeline est utilisé pour désinstaller un module.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-116">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="bdcdc-117">`Get-InstalledModule` utilise le paramètre **Name** pour spécifier le module.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-117">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="bdcdc-118">L’objet est envoyé dans le pipeline à `Uninstall-Module` et est désinstallé.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-118">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="bdcdc-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bdcdc-119">PARAMETERS</span></span>

### <span data-ttu-id="bdcdc-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="bdcdc-120">-AllowPrerelease</span></span>

<span data-ttu-id="bdcdc-121">Vous permet de désinstaller un module marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-121">Allows you to uninstall a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="bdcdc-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="bdcdc-122">-AllVersions</span></span>

<span data-ttu-id="bdcdc-123">Spécifie que vous souhaitez inclure toutes les versions disponibles d’un module.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-123">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="bdcdc-124">Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion**, **MaximumVersion** ou **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="bdcdc-124">You can't use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="bdcdc-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bdcdc-125">-Confirm</span></span>

<span data-ttu-id="bdcdc-126">Vous invite à confirmer l’exécution de l' `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="bdcdc-126">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="bdcdc-127">-Force</span><span class="sxs-lookup"><span data-stu-id="bdcdc-127">-Force</span></span>

<span data-ttu-id="bdcdc-128">Force l' `Uninstall-Module` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-128">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="bdcdc-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bdcdc-129">-InputObject</span></span>

<span data-ttu-id="bdcdc-130">Accepte un objet **PSRepositoryItemInfo** .</span><span class="sxs-lookup"><span data-stu-id="bdcdc-130">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="bdcdc-131">Par exemple, `Get-InstalledModule` la sortie vers une variable et l’utilisation de cette variable en tant qu’argument **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="bdcdc-131">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="bdcdc-132">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="bdcdc-132">-MaximumVersion</span></span>

<span data-ttu-id="bdcdc-133">Spécifie la version maximale ou la plus récente du module à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-133">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="bdcdc-134">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-134">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="bdcdc-135">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="bdcdc-135">-MinimumVersion</span></span>

<span data-ttu-id="bdcdc-136">Spécifie la version minimale du module à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-136">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="bdcdc-137">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-137">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="bdcdc-138">-Name</span><span class="sxs-lookup"><span data-stu-id="bdcdc-138">-Name</span></span>

<span data-ttu-id="bdcdc-139">Spécifie un tableau de noms de modules à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-139">Specifies an array of module names to uninstall.</span></span>

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

### <span data-ttu-id="bdcdc-140">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="bdcdc-140">-RequiredVersion</span></span>

<span data-ttu-id="bdcdc-141">Spécifie le numéro de version exact du module à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-141">Specifies the exact version number of the module to uninstall.</span></span>

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

### <span data-ttu-id="bdcdc-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bdcdc-142">-WhatIf</span></span>

<span data-ttu-id="bdcdc-143">Montre ce qui se passe si `Uninstall-Module` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-143">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="bdcdc-144">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-144">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="bdcdc-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bdcdc-145">CommonParameters</span></span>

<span data-ttu-id="bdcdc-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bdcdc-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bdcdc-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bdcdc-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bdcdc-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bdcdc-148">INPUTS</span></span>

### <span data-ttu-id="bdcdc-149">System.String[]</span><span class="sxs-lookup"><span data-stu-id="bdcdc-149">System.String[]</span></span>

### <span data-ttu-id="bdcdc-150">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="bdcdc-150">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="bdcdc-151">System.String</span><span class="sxs-lookup"><span data-stu-id="bdcdc-151">System.String</span></span>

## <span data-ttu-id="bdcdc-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bdcdc-152">OUTPUTS</span></span>

### <span data-ttu-id="bdcdc-153">System.Object</span><span class="sxs-lookup"><span data-stu-id="bdcdc-153">System.Object</span></span>

## <span data-ttu-id="bdcdc-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bdcdc-154">NOTES</span></span>

## <span data-ttu-id="bdcdc-155">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bdcdc-155">RELATED LINKS</span></span>

[<span data-ttu-id="bdcdc-156">Find-Module</span><span class="sxs-lookup"><span data-stu-id="bdcdc-156">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="bdcdc-157">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="bdcdc-157">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="bdcdc-158">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="bdcdc-158">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="bdcdc-159">Save-Module</span><span class="sxs-lookup"><span data-stu-id="bdcdc-159">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="bdcdc-160">Update-Module</span><span class="sxs-lookup"><span data-stu-id="bdcdc-160">Update-Module</span></span>](Update-Module.md)

