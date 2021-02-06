---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: 9f258c3b02064aafdaf272141f2613ff5cbaf5b5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597537"
---
# <span data-ttu-id="0150f-102">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0150f-102">Set-PackageSource</span></span>

## <span data-ttu-id="0150f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0150f-103">SYNOPSIS</span></span>
<span data-ttu-id="0150f-104">Remplace une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="0150f-104">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="0150f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="0150f-105">SYNTAX</span></span>

### <span data-ttu-id="0150f-106">SourceBySearch (par défaut)</span><span class="sxs-lookup"><span data-stu-id="0150f-106">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="0150f-107">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="0150f-107">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0150f-108">NuGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="0150f-108">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="0150f-109">NuGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="0150f-109">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="0150f-110">PowerShellGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="0150f-110">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="0150f-111">PowerShellGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="0150f-111">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="0150f-112">Description</span><span class="sxs-lookup"><span data-stu-id="0150f-112">DESCRIPTION</span></span>

<span data-ttu-id="0150f-113">`Set-PackageSource`Remplace une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="0150f-113">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="0150f-114">Les sources de package sont toujours gérées par un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="0150f-114">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="0150f-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0150f-115">EXAMPLES</span></span>

### <span data-ttu-id="0150f-116">Exemple 1 : modifier une source de package</span><span class="sxs-lookup"><span data-stu-id="0150f-116">Example 1: Change a package source</span></span>

<span data-ttu-id="0150f-117">Cette commande modifie le nom existant d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="0150f-117">This command changes the existing name of a package source.</span></span> <span data-ttu-id="0150f-118">La source est définie sur **approuvé**, ce qui élimine les invites de vérification de la source lors de l’installation des packages.</span><span class="sxs-lookup"><span data-stu-id="0150f-118">The source is set to **Trusted**, which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="0150f-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0150f-119">PARAMETERS</span></span>

### <span data-ttu-id="0150f-120">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="0150f-120">-ConfigFile</span></span>

<span data-ttu-id="0150f-121">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0150f-121">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="0150f-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="0150f-122">-Credential</span></span>

<span data-ttu-id="0150f-123">Spécifie un compte d’utilisateur qui a l’autorisation d’installer des fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="0150f-123">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="0150f-124">-Force</span><span class="sxs-lookup"><span data-stu-id="0150f-124">-Force</span></span>

<span data-ttu-id="0150f-125">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0150f-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0150f-126">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="0150f-126">-ForceBootstrap</span></span>

<span data-ttu-id="0150f-127">Indique que `Set-PackageSource` impose l’installation automatique du fournisseur de package par **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="0150f-127">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="0150f-128">-InputObject</span><span class="sxs-lookup"><span data-stu-id="0150f-128">-InputObject</span></span>

<span data-ttu-id="0150f-129">Spécifie un objet d’ID de source de package qui représente le package que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="0150f-129">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="0150f-130">Les ID de source de package font partie des résultats de l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="0150f-130">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="0150f-131">-Location</span><span class="sxs-lookup"><span data-stu-id="0150f-131">-Location</span></span>

<span data-ttu-id="0150f-132">Spécifie l’emplacement actuel de la source du package.</span><span class="sxs-lookup"><span data-stu-id="0150f-132">Specifies the current package source location.</span></span> <span data-ttu-id="0150f-133">La valeur peut être un URI, un chemin d’accès de fichier ou tout autre format de destination pris en charge par le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="0150f-133">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="0150f-134">-Name</span><span class="sxs-lookup"><span data-stu-id="0150f-134">-Name</span></span>

<span data-ttu-id="0150f-135">Spécifie le nom d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="0150f-135">Specifies a package source's name.</span></span>

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

### <span data-ttu-id="0150f-136">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="0150f-136">-NewLocation</span></span>

<span data-ttu-id="0150f-137">Spécifie le nouvel emplacement pour une source de package.</span><span class="sxs-lookup"><span data-stu-id="0150f-137">Specifies the new location for a package source.</span></span> <span data-ttu-id="0150f-138">La valeur peut être un URI, un chemin d’accès de fichier ou tout autre format de destination pris en charge par le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="0150f-138">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="0150f-139">-NewName</span><span class="sxs-lookup"><span data-stu-id="0150f-139">-NewName</span></span>

<span data-ttu-id="0150f-140">Spécifie le nouveau nom que vous attribuez à une source de package.</span><span class="sxs-lookup"><span data-stu-id="0150f-140">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="0150f-141">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="0150f-141">-PackageManagementProvider</span></span>

<span data-ttu-id="0150f-142">Spécifie un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="0150f-142">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="0150f-143">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="0150f-143">-ProviderName</span></span>

<span data-ttu-id="0150f-144">Spécifie un nom de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0150f-144">Specifies a provider name.</span></span>

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

### <span data-ttu-id="0150f-145">-Proxy</span><span class="sxs-lookup"><span data-stu-id="0150f-145">-Proxy</span></span>

<span data-ttu-id="0150f-146">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="0150f-146">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="0150f-147">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="0150f-147">-ProxyCredential</span></span>

<span data-ttu-id="0150f-148">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="0150f-148">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="0150f-149">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="0150f-149">-PublishLocation</span></span>

<span data-ttu-id="0150f-150">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="0150f-150">Specifies the publish location.</span></span>

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

### <span data-ttu-id="0150f-151">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="0150f-151">-ScriptPublishLocation</span></span>

<span data-ttu-id="0150f-152">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="0150f-152">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="0150f-153">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="0150f-153">-ScriptSourceLocation</span></span>

<span data-ttu-id="0150f-154">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="0150f-154">Specifies the script source location.</span></span>

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

### <span data-ttu-id="0150f-155">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="0150f-155">-SkipValidate</span></span>

<span data-ttu-id="0150f-156">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="0150f-156">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="0150f-157">-Approuvé</span><span class="sxs-lookup"><span data-stu-id="0150f-157">-Trusted</span></span>

<span data-ttu-id="0150f-158">Indique que la source est un fournisseur de package approuvé.</span><span class="sxs-lookup"><span data-stu-id="0150f-158">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="0150f-159">Les sources approuvées ne demandent pas de vérification pour installer les packages.</span><span class="sxs-lookup"><span data-stu-id="0150f-159">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="0150f-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0150f-160">-Confirm</span></span>

<span data-ttu-id="0150f-161">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0150f-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0150f-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0150f-162">-WhatIf</span></span>

<span data-ttu-id="0150f-163">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0150f-163">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0150f-164">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="0150f-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0150f-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0150f-165">CommonParameters</span></span>

<span data-ttu-id="0150f-166">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0150f-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0150f-167">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0150f-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0150f-168">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0150f-168">INPUTS</span></span>

### <span data-ttu-id="0150f-169">`Set-PackageSource` n’accepte pas l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="0150f-169">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="0150f-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0150f-170">OUTPUTS</span></span>

### <span data-ttu-id="0150f-171">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="0150f-171">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0150f-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0150f-172">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0150f-173">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="0150f-173">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="0150f-174">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0150f-174">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="0150f-175">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="0150f-175">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="0150f-176">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0150f-176">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="0150f-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0150f-177">RELATED LINKS</span></span>

[<span data-ttu-id="0150f-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="0150f-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="0150f-179">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0150f-179">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="0150f-180">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0150f-180">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="0150f-181">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0150f-181">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
