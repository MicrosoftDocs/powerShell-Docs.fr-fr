---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: a8dc659d3ffdfcd296660f64f7b7cbd0bb132217
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202922"
---
# <span data-ttu-id="be6b5-103">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="be6b5-103">Set-PackageSource</span></span>

## <span data-ttu-id="be6b5-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="be6b5-104">SYNOPSIS</span></span>
<span data-ttu-id="be6b5-105">Remplace une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="be6b5-105">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="be6b5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="be6b5-106">SYNTAX</span></span>

### <span data-ttu-id="be6b5-107">SourceBySearch (par défaut)</span><span class="sxs-lookup"><span data-stu-id="be6b5-107">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="be6b5-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="be6b5-108">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="be6b5-109">NuGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="be6b5-109">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="be6b5-110">NuGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="be6b5-110">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="be6b5-111">PowerShellGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="be6b5-111">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="be6b5-112">PowerShellGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="be6b5-112">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="be6b5-113">Description</span><span class="sxs-lookup"><span data-stu-id="be6b5-113">DESCRIPTION</span></span>

<span data-ttu-id="be6b5-114">`Set-PackageSource`Remplace une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="be6b5-114">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="be6b5-115">Les sources de package sont toujours gérées par un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-115">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="be6b5-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="be6b5-116">EXAMPLES</span></span>

### <span data-ttu-id="be6b5-117">Exemple 1 : modifier une source de package</span><span class="sxs-lookup"><span data-stu-id="be6b5-117">Example 1: Change a package source</span></span>

<span data-ttu-id="be6b5-118">Cette commande modifie le nom existant d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-118">This command changes the existing name of a package source.</span></span> <span data-ttu-id="be6b5-119">La source est définie sur **approuvé** , ce qui élimine les invites de vérification de la source lors de l’installation des packages.</span><span class="sxs-lookup"><span data-stu-id="be6b5-119">The source is set to **Trusted** , which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="be6b5-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="be6b5-120">PARAMETERS</span></span>

### <span data-ttu-id="be6b5-121">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="be6b5-121">-ConfigFile</span></span>

<span data-ttu-id="be6b5-122">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="be6b5-122">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="be6b5-123">-Credential</span></span>

<span data-ttu-id="be6b5-124">Spécifie un compte d’utilisateur qui a l’autorisation d’installer des fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="be6b5-124">Specifies a user account that has permission to install package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-125">-Force</span><span class="sxs-lookup"><span data-stu-id="be6b5-125">-Force</span></span>

<span data-ttu-id="be6b5-126">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="be6b5-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="be6b5-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="be6b5-127">-ForceBootstrap</span></span>

<span data-ttu-id="be6b5-128">Indique que `Set-PackageSource` impose l’installation automatique du fournisseur de package par **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="be6b5-128">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="be6b5-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="be6b5-129">-InputObject</span></span>

<span data-ttu-id="be6b5-130">Spécifie un objet d’ID de source de package qui représente le package que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="be6b5-130">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="be6b5-131">Les ID de source de package font partie des résultats de l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="be6b5-131">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-132">-Location</span><span class="sxs-lookup"><span data-stu-id="be6b5-132">-Location</span></span>

<span data-ttu-id="be6b5-133">Spécifie l’emplacement actuel de la source du package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-133">Specifies the current package source location.</span></span> <span data-ttu-id="be6b5-134">La valeur peut être un URI, un chemin d’accès de fichier ou tout autre format de destination pris en charge par le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-134">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-135">-Name</span><span class="sxs-lookup"><span data-stu-id="be6b5-135">-Name</span></span>

<span data-ttu-id="be6b5-136">Spécifie le nom d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-136">Specifies a package source's name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: SourceName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-137">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="be6b5-137">-NewLocation</span></span>

<span data-ttu-id="be6b5-138">Spécifie le nouvel emplacement pour une source de package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-138">Specifies the new location for a package source.</span></span> <span data-ttu-id="be6b5-139">La valeur peut être un URI, un chemin d’accès de fichier ou tout autre format de destination pris en charge par le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-139">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="be6b5-140">-NewName</span></span>

<span data-ttu-id="be6b5-141">Spécifie le nouveau nom que vous attribuez à une source de package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-141">Specifies the new name you assign to a package source.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-142">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="be6b5-142">-PackageManagementProvider</span></span>

<span data-ttu-id="be6b5-143">Spécifie un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="be6b5-143">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-144">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="be6b5-144">-ProviderName</span></span>

<span data-ttu-id="be6b5-145">Spécifie un nom de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="be6b5-145">Specifies a provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-146">-Proxy</span><span class="sxs-lookup"><span data-stu-id="be6b5-146">-Proxy</span></span>

<span data-ttu-id="be6b5-147">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="be6b5-147">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-148">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="be6b5-148">-ProxyCredential</span></span>

<span data-ttu-id="be6b5-149">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="be6b5-149">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="be6b5-150">-PublishLocation</span></span>

<span data-ttu-id="be6b5-151">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="be6b5-151">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="be6b5-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="be6b5-153">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="be6b5-153">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="be6b5-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="be6b5-155">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="be6b5-155">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="be6b5-156">-SkipValidate</span></span>

<span data-ttu-id="be6b5-157">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="be6b5-157">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be6b5-158">-Approuvé</span><span class="sxs-lookup"><span data-stu-id="be6b5-158">-Trusted</span></span>

<span data-ttu-id="be6b5-159">Indique que la source est un fournisseur de package approuvé.</span><span class="sxs-lookup"><span data-stu-id="be6b5-159">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="be6b5-160">Les sources approuvées ne demandent pas de vérification pour installer les packages.</span><span class="sxs-lookup"><span data-stu-id="be6b5-160">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="be6b5-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="be6b5-161">-Confirm</span></span>

<span data-ttu-id="be6b5-162">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="be6b5-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="be6b5-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="be6b5-163">-WhatIf</span></span>

<span data-ttu-id="be6b5-164">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="be6b5-164">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="be6b5-165">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="be6b5-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="be6b5-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="be6b5-166">CommonParameters</span></span>

<span data-ttu-id="be6b5-167">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="be6b5-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="be6b5-168">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="be6b5-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="be6b5-169">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="be6b5-169">INPUTS</span></span>

### <span data-ttu-id="be6b5-170">`Set-PackageSource` n’accepte pas l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="be6b5-170">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="be6b5-171">SORTIES</span><span class="sxs-lookup"><span data-stu-id="be6b5-171">OUTPUTS</span></span>

### <span data-ttu-id="be6b5-172">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="be6b5-172">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="be6b5-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="be6b5-173">NOTES</span></span>

## <span data-ttu-id="be6b5-174">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="be6b5-174">RELATED LINKS</span></span>

[<span data-ttu-id="be6b5-175">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="be6b5-175">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="be6b5-176">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="be6b5-176">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="be6b5-177">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="be6b5-177">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="be6b5-178">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="be6b5-178">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
