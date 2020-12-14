---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: 67a5a97c4e29556c9b93a17d25576d4bd6eaea0c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892703"
---
# <span data-ttu-id="22994-103">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="22994-103">Set-PackageSource</span></span>

## <span data-ttu-id="22994-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="22994-104">SYNOPSIS</span></span>
<span data-ttu-id="22994-105">Remplace une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="22994-105">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="22994-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="22994-106">SYNTAX</span></span>

### <span data-ttu-id="22994-107">SourceBySearch (par défaut)</span><span class="sxs-lookup"><span data-stu-id="22994-107">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="22994-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="22994-108">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="22994-109">NuGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="22994-109">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="22994-110">NuGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="22994-110">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="22994-111">PowerShellGet : SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="22994-111">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="22994-112">PowerShellGet : SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="22994-112">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="22994-113">Description</span><span class="sxs-lookup"><span data-stu-id="22994-113">DESCRIPTION</span></span>

<span data-ttu-id="22994-114">`Set-PackageSource`Remplace une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="22994-114">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="22994-115">Les sources de package sont toujours gérées par un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="22994-115">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="22994-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="22994-116">EXAMPLES</span></span>

### <span data-ttu-id="22994-117">Exemple 1 : modifier une source de package</span><span class="sxs-lookup"><span data-stu-id="22994-117">Example 1: Change a package source</span></span>

<span data-ttu-id="22994-118">Cette commande modifie le nom existant d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="22994-118">This command changes the existing name of a package source.</span></span> <span data-ttu-id="22994-119">La source est définie sur **approuvé**, ce qui élimine les invites de vérification de la source lors de l’installation des packages.</span><span class="sxs-lookup"><span data-stu-id="22994-119">The source is set to **Trusted**, which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="22994-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="22994-120">PARAMETERS</span></span>

### <span data-ttu-id="22994-121">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="22994-121">-ConfigFile</span></span>

<span data-ttu-id="22994-122">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="22994-122">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="22994-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="22994-123">-Credential</span></span>

<span data-ttu-id="22994-124">Spécifie un compte d’utilisateur qui a l’autorisation d’installer des fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="22994-124">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="22994-125">-Force</span><span class="sxs-lookup"><span data-stu-id="22994-125">-Force</span></span>

<span data-ttu-id="22994-126">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="22994-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="22994-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="22994-127">-ForceBootstrap</span></span>

<span data-ttu-id="22994-128">Indique que `Set-PackageSource` impose l’installation automatique du fournisseur de package par **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="22994-128">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="22994-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="22994-129">-InputObject</span></span>

<span data-ttu-id="22994-130">Spécifie un objet d’ID de source de package qui représente le package que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="22994-130">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="22994-131">Les ID de source de package font partie des résultats de l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="22994-131">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="22994-132">-Location</span><span class="sxs-lookup"><span data-stu-id="22994-132">-Location</span></span>

<span data-ttu-id="22994-133">Spécifie l’emplacement actuel de la source du package.</span><span class="sxs-lookup"><span data-stu-id="22994-133">Specifies the current package source location.</span></span> <span data-ttu-id="22994-134">La valeur peut être un URI, un chemin d’accès de fichier ou tout autre format de destination pris en charge par le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="22994-134">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="22994-135">-Name</span><span class="sxs-lookup"><span data-stu-id="22994-135">-Name</span></span>

<span data-ttu-id="22994-136">Spécifie le nom d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="22994-136">Specifies a package source's name.</span></span>

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

### <span data-ttu-id="22994-137">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="22994-137">-NewLocation</span></span>

<span data-ttu-id="22994-138">Spécifie le nouvel emplacement pour une source de package.</span><span class="sxs-lookup"><span data-stu-id="22994-138">Specifies the new location for a package source.</span></span> <span data-ttu-id="22994-139">La valeur peut être un URI, un chemin d’accès de fichier ou tout autre format de destination pris en charge par le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="22994-139">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="22994-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="22994-140">-NewName</span></span>

<span data-ttu-id="22994-141">Spécifie le nouveau nom que vous attribuez à une source de package.</span><span class="sxs-lookup"><span data-stu-id="22994-141">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="22994-142">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="22994-142">-PackageManagementProvider</span></span>

<span data-ttu-id="22994-143">Spécifie un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="22994-143">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="22994-144">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="22994-144">-ProviderName</span></span>

<span data-ttu-id="22994-145">Spécifie un nom de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="22994-145">Specifies a provider name.</span></span>

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

### <span data-ttu-id="22994-146">-Proxy</span><span class="sxs-lookup"><span data-stu-id="22994-146">-Proxy</span></span>

<span data-ttu-id="22994-147">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="22994-147">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="22994-148">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="22994-148">-ProxyCredential</span></span>

<span data-ttu-id="22994-149">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="22994-149">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="22994-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="22994-150">-PublishLocation</span></span>

<span data-ttu-id="22994-151">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="22994-151">Specifies the publish location.</span></span>

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

### <span data-ttu-id="22994-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="22994-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="22994-153">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="22994-153">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="22994-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="22994-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="22994-155">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="22994-155">Specifies the script source location.</span></span>

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

### <span data-ttu-id="22994-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="22994-156">-SkipValidate</span></span>

<span data-ttu-id="22994-157">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="22994-157">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="22994-158">-Approuvé</span><span class="sxs-lookup"><span data-stu-id="22994-158">-Trusted</span></span>

<span data-ttu-id="22994-159">Indique que la source est un fournisseur de package approuvé.</span><span class="sxs-lookup"><span data-stu-id="22994-159">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="22994-160">Les sources approuvées ne demandent pas de vérification pour installer les packages.</span><span class="sxs-lookup"><span data-stu-id="22994-160">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="22994-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="22994-161">-Confirm</span></span>

<span data-ttu-id="22994-162">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="22994-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="22994-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="22994-163">-WhatIf</span></span>

<span data-ttu-id="22994-164">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="22994-164">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="22994-165">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="22994-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="22994-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="22994-166">CommonParameters</span></span>

<span data-ttu-id="22994-167">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="22994-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="22994-168">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="22994-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="22994-169">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="22994-169">INPUTS</span></span>

### <span data-ttu-id="22994-170">`Set-PackageSource` n’accepte pas l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="22994-170">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="22994-171">SORTIES</span><span class="sxs-lookup"><span data-stu-id="22994-171">OUTPUTS</span></span>

### <span data-ttu-id="22994-172">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="22994-172">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="22994-173">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="22994-173">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22994-174">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="22994-174">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="22994-175">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="22994-175">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="22994-176">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="22994-176">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="22994-177">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22994-177">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="22994-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="22994-178">RELATED LINKS</span></span>

[<span data-ttu-id="22994-179">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="22994-179">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="22994-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="22994-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="22994-181">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="22994-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="22994-182">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="22994-182">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
