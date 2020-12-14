---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/register-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PackageSource
ms.openlocfilehash: dfaccf285b8a53c1701919016509fd49eeee5da7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891047"
---
# <span data-ttu-id="020d3-103">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="020d3-103">Register-PackageSource</span></span>

## <span data-ttu-id="020d3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="020d3-104">SYNOPSIS</span></span>
<span data-ttu-id="020d3-105">Ajoute une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="020d3-105">Adds a package source for a specified package provider.</span></span>

## <span data-ttu-id="020d3-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="020d3-106">SYNTAX</span></span>

### <span data-ttu-id="020d3-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="020d3-107">SourceBySearch</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="020d3-108">NuGet</span><span class="sxs-lookup"><span data-stu-id="020d3-108">NuGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="020d3-109">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="020d3-109">PowerShellGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="020d3-110">Description</span><span class="sxs-lookup"><span data-stu-id="020d3-110">DESCRIPTION</span></span>

<span data-ttu-id="020d3-111">L' `Register-PackageSource` applet de commande ajoute une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="020d3-111">The `Register-PackageSource` cmdlet adds a package source for a specified package provider.</span></span> <span data-ttu-id="020d3-112">Les sources de package sont toujours gérées par un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="020d3-112">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="020d3-113">Si le fournisseur de package ne peut pas ajouter ou remplacer une source de package, le fournisseur génère un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="020d3-113">If the package provider cannot add or replace a package source, the provider generates an error message.</span></span>

## <span data-ttu-id="020d3-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="020d3-114">EXAMPLES</span></span>

### <span data-ttu-id="020d3-115">Exemple 1 : inscrire une source de package pour le fournisseur NuGet</span><span class="sxs-lookup"><span data-stu-id="020d3-115">Example 1: Register a package source for the NuGet provider</span></span>

<span data-ttu-id="020d3-116">Cette commande inscrit une source de package, un emplacement basé sur le Web pour le fournisseur **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="020d3-116">This command registers a package source, a web-based location for the **NuGet** provider.</span></span> <span data-ttu-id="020d3-117">Par défaut, les sources ne sont pas approuvées.</span><span class="sxs-lookup"><span data-stu-id="020d3-117">By default, sources aren't trusted.</span></span> <span data-ttu-id="020d3-118">Vous êtes invité à confirmer que la source est approuvée avant l’installation des packages.</span><span class="sxs-lookup"><span data-stu-id="020d3-118">You are prompted to confirm the source is trusted before packages are installed.</span></span> <span data-ttu-id="020d3-119">Pour remplacer la valeur par défaut, utilisez le `-Trusted` paramètre.</span><span class="sxs-lookup"><span data-stu-id="020d3-119">To override the default, use the `-Trusted` parameter.</span></span>

```powershell
Register-PackageSource -Name MyNuGet -Location https://www.nuget.org/api/v2 -ProviderName NuGet
```

```Output
Name          ProviderName     IsTrusted  Location
----          ------------     ---------  --------
MyNuGet       NuGet            False      https://www.nuget.org/api/v2
```

## <span data-ttu-id="020d3-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="020d3-120">PARAMETERS</span></span>

### <span data-ttu-id="020d3-121">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="020d3-121">-ConfigFile</span></span>

<span data-ttu-id="020d3-122">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="020d3-122">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="020d3-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="020d3-123">-Credential</span></span>

<span data-ttu-id="020d3-124">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’emplacement authentifié.</span><span class="sxs-lookup"><span data-stu-id="020d3-124">Specifies a user account that has permission to access the authenticated location.</span></span>

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

### <span data-ttu-id="020d3-125">-Force</span><span class="sxs-lookup"><span data-stu-id="020d3-125">-Force</span></span>

<span data-ttu-id="020d3-126">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="020d3-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="020d3-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="020d3-127">-ForceBootstrap</span></span>

<span data-ttu-id="020d3-128">Indique que cette applet de commande installe automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="020d3-128">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="020d3-129">-Location</span><span class="sxs-lookup"><span data-stu-id="020d3-129">-Location</span></span>

<span data-ttu-id="020d3-130">Spécifie l’emplacement source du package.</span><span class="sxs-lookup"><span data-stu-id="020d3-130">Specifies the package source location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="020d3-131">-Name</span><span class="sxs-lookup"><span data-stu-id="020d3-131">-Name</span></span>

<span data-ttu-id="020d3-132">Spécifie le nom de la source du package à inscrire.</span><span class="sxs-lookup"><span data-stu-id="020d3-132">Specifies the name of the package source to register.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="020d3-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="020d3-133">-PackageManagementProvider</span></span>

<span data-ttu-id="020d3-134">Spécifie le fournisseur de Package Management.</span><span class="sxs-lookup"><span data-stu-id="020d3-134">Specifies the Package Management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="020d3-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="020d3-135">-ProviderName</span></span>

<span data-ttu-id="020d3-136">Spécifie le nom du fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="020d3-136">Specifies the package provider's name.</span></span>

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

### <span data-ttu-id="020d3-137">-Proxy</span><span class="sxs-lookup"><span data-stu-id="020d3-137">-Proxy</span></span>

<span data-ttu-id="020d3-138">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="020d3-138">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="020d3-139">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="020d3-139">-ProxyCredential</span></span>

<span data-ttu-id="020d3-140">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="020d3-140">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="020d3-141">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="020d3-141">-PublishLocation</span></span>

<span data-ttu-id="020d3-142">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="020d3-142">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="020d3-143">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="020d3-143">-ScriptPublishLocation</span></span>

<span data-ttu-id="020d3-144">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="020d3-144">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="020d3-145">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="020d3-145">-ScriptSourceLocation</span></span>

<span data-ttu-id="020d3-146">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="020d3-146">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="020d3-147">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="020d3-147">-SkipValidate</span></span>

<span data-ttu-id="020d3-148">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="020d3-148">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="020d3-149">-Approuvé</span><span class="sxs-lookup"><span data-stu-id="020d3-149">-Trusted</span></span>

<span data-ttu-id="020d3-150">Indique que la source du package est approuvée.</span><span class="sxs-lookup"><span data-stu-id="020d3-150">Indicates that the package source is trusted.</span></span>

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

### <span data-ttu-id="020d3-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="020d3-151">-Confirm</span></span>

<span data-ttu-id="020d3-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="020d3-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="020d3-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="020d3-153">-WhatIf</span></span>

<span data-ttu-id="020d3-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="020d3-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="020d3-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="020d3-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="020d3-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="020d3-156">CommonParameters</span></span>

<span data-ttu-id="020d3-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="020d3-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="020d3-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="020d3-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="020d3-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="020d3-159">INPUTS</span></span>

## <span data-ttu-id="020d3-160">SORTIES</span><span class="sxs-lookup"><span data-stu-id="020d3-160">OUTPUTS</span></span>

## <span data-ttu-id="020d3-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="020d3-161">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="020d3-162">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="020d3-162">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="020d3-163">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="020d3-163">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="020d3-164">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="020d3-164">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="020d3-165">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="020d3-165">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="020d3-166">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="020d3-166">RELATED LINKS</span></span>

[<span data-ttu-id="020d3-167">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="020d3-167">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="020d3-168">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="020d3-168">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="020d3-169">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="020d3-169">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="020d3-170">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="020d3-170">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
