---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 812ff0b9ea57e2aa3ccb1f24656a94d4de9c641b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204546"
---
# <span data-ttu-id="6d763-103">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="6d763-103">Uninstall-Script</span></span>

## <span data-ttu-id="6d763-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6d763-104">SYNOPSIS</span></span>
<span data-ttu-id="6d763-105">Désinstalle un script.</span><span class="sxs-lookup"><span data-stu-id="6d763-105">Uninstalls a script.</span></span>

## <span data-ttu-id="6d763-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6d763-106">SYNTAX</span></span>

### <span data-ttu-id="6d763-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6d763-107">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6d763-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="6d763-108">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6d763-109">Description</span><span class="sxs-lookup"><span data-stu-id="6d763-109">DESCRIPTION</span></span>

<span data-ttu-id="6d763-110">L' `Uninstall-Script` applet de commande désinstalle un script spécifié de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6d763-110">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="6d763-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6d763-111">EXAMPLES</span></span>

### <span data-ttu-id="6d763-112">Exemple 1 : désinstaller un script</span><span class="sxs-lookup"><span data-stu-id="6d763-112">Example 1: Uninstall a script</span></span>

<span data-ttu-id="6d763-113">Cet exemple désinstalle un script.</span><span class="sxs-lookup"><span data-stu-id="6d763-113">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="6d763-114">`Uninstall-Script` utilise le paramètre **Name** pour spécifier le script à désinstaller à partir de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6d763-114">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="6d763-115">Exemple 2 : utiliser le pipeline pour désinstaller un script</span><span class="sxs-lookup"><span data-stu-id="6d763-115">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="6d763-116">Dans cet exemple, le pipeline est utilisé pour désinstaller un script.</span><span class="sxs-lookup"><span data-stu-id="6d763-116">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="6d763-117">`Get-InstalledScript` utilise le paramètre **Name** pour spécifier le script.</span><span class="sxs-lookup"><span data-stu-id="6d763-117">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="6d763-118">L’objet est envoyé vers le pipeline vers `Uninstall-Script` et le script est désinstallé.</span><span class="sxs-lookup"><span data-stu-id="6d763-118">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="6d763-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6d763-119">PARAMETERS</span></span>

### <span data-ttu-id="6d763-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="6d763-120">-AllowPrerelease</span></span>

<span data-ttu-id="6d763-121">Vous permet de désinstaller un script marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="6d763-121">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="6d763-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6d763-122">-Confirm</span></span>

<span data-ttu-id="6d763-123">Vous invite à confirmer l’exécution `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="6d763-123">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="6d763-124">-Force</span><span class="sxs-lookup"><span data-stu-id="6d763-124">-Force</span></span>

<span data-ttu-id="6d763-125">Force l' `Uninstall-Script` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6d763-125">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="6d763-126">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6d763-126">-InputObject</span></span>

<span data-ttu-id="6d763-127">Accepte un objet **PSRepositoryItemInfo** .</span><span class="sxs-lookup"><span data-stu-id="6d763-127">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="6d763-128">Par exemple, `Get-InstalledScript` la sortie vers une variable et l’utilisation de cette variable en tant qu’argument **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="6d763-128">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="6d763-129">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6d763-129">-MaximumVersion</span></span>

<span data-ttu-id="6d763-130">Spécifie la version maximale ou la plus récente du script à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="6d763-130">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="6d763-131">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="6d763-131">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="6d763-132">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6d763-132">-MinimumVersion</span></span>

<span data-ttu-id="6d763-133">Spécifie la version minimale du script à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="6d763-133">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="6d763-134">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="6d763-134">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="6d763-135">-Name</span><span class="sxs-lookup"><span data-stu-id="6d763-135">-Name</span></span>

<span data-ttu-id="6d763-136">Spécifie un tableau de noms de script à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="6d763-136">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="6d763-137">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6d763-137">-RequiredVersion</span></span>

<span data-ttu-id="6d763-138">Spécifie le numéro de version exact du script à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="6d763-138">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="6d763-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6d763-139">-WhatIf</span></span>

<span data-ttu-id="6d763-140">Montre ce qui se passe si `Uninstall-Script` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="6d763-140">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="6d763-141">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6d763-141">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="6d763-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6d763-142">CommonParameters</span></span>

<span data-ttu-id="6d763-143">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6d763-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6d763-144">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6d763-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6d763-145">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6d763-145">INPUTS</span></span>

### <span data-ttu-id="6d763-146">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6d763-146">System.String[]</span></span>

### <span data-ttu-id="6d763-147">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="6d763-147">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="6d763-148">System.String</span><span class="sxs-lookup"><span data-stu-id="6d763-148">System.String</span></span>

## <span data-ttu-id="6d763-149">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6d763-149">OUTPUTS</span></span>

### <span data-ttu-id="6d763-150">System.Object</span><span class="sxs-lookup"><span data-stu-id="6d763-150">System.Object</span></span>

## <span data-ttu-id="6d763-151">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6d763-151">NOTES</span></span>

## <span data-ttu-id="6d763-152">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6d763-152">RELATED LINKS</span></span>

[<span data-ttu-id="6d763-153">Find-Script</span><span class="sxs-lookup"><span data-stu-id="6d763-153">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="6d763-154">Install-Script</span><span class="sxs-lookup"><span data-stu-id="6d763-154">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="6d763-155">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="6d763-155">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="6d763-156">Save-Script</span><span class="sxs-lookup"><span data-stu-id="6d763-156">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="6d763-157">Update-Script</span><span class="sxs-lookup"><span data-stu-id="6d763-157">Update-Script</span></span>](Update-Script.md)
