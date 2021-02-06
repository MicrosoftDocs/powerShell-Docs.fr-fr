---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 2cd8b51e1d4ef11a0a5f9e3542ff89e094854d8c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595923"
---
# <span data-ttu-id="ab14a-102">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="ab14a-102">Uninstall-Script</span></span>

## <span data-ttu-id="ab14a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ab14a-103">SYNOPSIS</span></span>
<span data-ttu-id="ab14a-104">Désinstalle un script.</span><span class="sxs-lookup"><span data-stu-id="ab14a-104">Uninstalls a script.</span></span>

## <span data-ttu-id="ab14a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ab14a-105">SYNTAX</span></span>

### <span data-ttu-id="ab14a-106">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ab14a-106">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ab14a-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="ab14a-107">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ab14a-108">Description</span><span class="sxs-lookup"><span data-stu-id="ab14a-108">DESCRIPTION</span></span>

<span data-ttu-id="ab14a-109">L' `Uninstall-Script` applet de commande désinstalle un script spécifié de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ab14a-109">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="ab14a-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ab14a-110">EXAMPLES</span></span>

### <span data-ttu-id="ab14a-111">Exemple 1 : désinstaller un script</span><span class="sxs-lookup"><span data-stu-id="ab14a-111">Example 1: Uninstall a script</span></span>

<span data-ttu-id="ab14a-112">Cet exemple désinstalle un script.</span><span class="sxs-lookup"><span data-stu-id="ab14a-112">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="ab14a-113">`Uninstall-Script` utilise le paramètre **Name** pour spécifier le script à désinstaller à partir de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ab14a-113">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="ab14a-114">Exemple 2 : utiliser le pipeline pour désinstaller un script</span><span class="sxs-lookup"><span data-stu-id="ab14a-114">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="ab14a-115">Dans cet exemple, le pipeline est utilisé pour désinstaller un script.</span><span class="sxs-lookup"><span data-stu-id="ab14a-115">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="ab14a-116">`Get-InstalledScript` utilise le paramètre **Name** pour spécifier le script.</span><span class="sxs-lookup"><span data-stu-id="ab14a-116">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="ab14a-117">L’objet est envoyé vers le pipeline vers `Uninstall-Script` et le script est désinstallé.</span><span class="sxs-lookup"><span data-stu-id="ab14a-117">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="ab14a-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab14a-118">PARAMETERS</span></span>

### <span data-ttu-id="ab14a-119">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="ab14a-119">-AllowPrerelease</span></span>

<span data-ttu-id="ab14a-120">Vous permet de désinstaller un script marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="ab14a-120">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="ab14a-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab14a-121">-Confirm</span></span>

<span data-ttu-id="ab14a-122">Vous invite à confirmer l’exécution `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="ab14a-122">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="ab14a-123">-Force</span><span class="sxs-lookup"><span data-stu-id="ab14a-123">-Force</span></span>

<span data-ttu-id="ab14a-124">Force l' `Uninstall-Script` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ab14a-124">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ab14a-125">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ab14a-125">-InputObject</span></span>

<span data-ttu-id="ab14a-126">Accepte un objet **PSRepositoryItemInfo** .</span><span class="sxs-lookup"><span data-stu-id="ab14a-126">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="ab14a-127">Par exemple, `Get-InstalledScript` la sortie vers une variable et l’utilisation de cette variable en tant qu’argument **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="ab14a-127">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="ab14a-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ab14a-128">-MaximumVersion</span></span>

<span data-ttu-id="ab14a-129">Spécifie la version maximale ou la plus récente du script à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ab14a-129">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="ab14a-130">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="ab14a-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="ab14a-131">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ab14a-131">-MinimumVersion</span></span>

<span data-ttu-id="ab14a-132">Spécifie la version minimale du script à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ab14a-132">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="ab14a-133">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="ab14a-133">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="ab14a-134">-Name</span><span class="sxs-lookup"><span data-stu-id="ab14a-134">-Name</span></span>

<span data-ttu-id="ab14a-135">Spécifie un tableau de noms de script à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ab14a-135">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="ab14a-136">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ab14a-136">-RequiredVersion</span></span>

<span data-ttu-id="ab14a-137">Spécifie le numéro de version exact du script à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ab14a-137">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="ab14a-138">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab14a-138">-WhatIf</span></span>

<span data-ttu-id="ab14a-139">Montre ce qui se passe si `Uninstall-Script` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ab14a-139">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="ab14a-140">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ab14a-140">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ab14a-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab14a-141">CommonParameters</span></span>

<span data-ttu-id="ab14a-142">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab14a-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab14a-143">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ab14a-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab14a-144">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ab14a-144">INPUTS</span></span>

### <span data-ttu-id="ab14a-145">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ab14a-145">System.String[]</span></span>

### <span data-ttu-id="ab14a-146">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="ab14a-146">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="ab14a-147">System.String</span><span class="sxs-lookup"><span data-stu-id="ab14a-147">System.String</span></span>

## <span data-ttu-id="ab14a-148">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ab14a-148">OUTPUTS</span></span>

### <span data-ttu-id="ab14a-149">System.Object</span><span class="sxs-lookup"><span data-stu-id="ab14a-149">System.Object</span></span>

## <span data-ttu-id="ab14a-150">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ab14a-150">NOTES</span></span>

## <span data-ttu-id="ab14a-151">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ab14a-151">RELATED LINKS</span></span>

[<span data-ttu-id="ab14a-152">Find-Script</span><span class="sxs-lookup"><span data-stu-id="ab14a-152">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="ab14a-153">Install-Script</span><span class="sxs-lookup"><span data-stu-id="ab14a-153">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="ab14a-154">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="ab14a-154">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="ab14a-155">Save-Script</span><span class="sxs-lookup"><span data-stu-id="ab14a-155">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="ab14a-156">Update-Script</span><span class="sxs-lookup"><span data-stu-id="ab14a-156">Update-Script</span></span>](Update-Script.md)

