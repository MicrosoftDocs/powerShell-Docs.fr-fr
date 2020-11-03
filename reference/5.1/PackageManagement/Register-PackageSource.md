---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/register-packagesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PackageSource
ms.openlocfilehash: 01c5130091b0028fb3cd4cc40a1e838156168ae5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202926"
---
# <span data-ttu-id="62560-103">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="62560-103">Register-PackageSource</span></span>

## <span data-ttu-id="62560-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="62560-104">SYNOPSIS</span></span>
<span data-ttu-id="62560-105">Ajoute une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="62560-105">Adds a package source for a specified package provider.</span></span>

## <span data-ttu-id="62560-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="62560-106">SYNTAX</span></span>

### <span data-ttu-id="62560-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="62560-107">SourceBySearch</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="62560-108">NuGet</span><span class="sxs-lookup"><span data-stu-id="62560-108">NuGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="62560-109">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="62560-109">PowerShellGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="62560-110">Description</span><span class="sxs-lookup"><span data-stu-id="62560-110">DESCRIPTION</span></span>

<span data-ttu-id="62560-111">L' `Register-PackageSource` applet de commande ajoute une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="62560-111">The `Register-PackageSource` cmdlet adds a package source for a specified package provider.</span></span> <span data-ttu-id="62560-112">Les sources de package sont toujours gérées par un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="62560-112">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="62560-113">Si le fournisseur de package ne peut pas ajouter ou remplacer une source de package, le fournisseur génère un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="62560-113">If the package provider cannot add or replace a package source, the provider generates an error message.</span></span>

## <span data-ttu-id="62560-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="62560-114">EXAMPLES</span></span>

### <span data-ttu-id="62560-115">Exemple 1 : inscrire une source de package pour le fournisseur NuGet</span><span class="sxs-lookup"><span data-stu-id="62560-115">Example 1: Register a package source for the NuGet provider</span></span>

<span data-ttu-id="62560-116">Cette commande inscrit une source de package, un emplacement basé sur le Web pour le fournisseur **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="62560-116">This command registers a package source, a web-based location for the **NuGet** provider.</span></span> <span data-ttu-id="62560-117">Par défaut, les sources ne sont pas approuvées.</span><span class="sxs-lookup"><span data-stu-id="62560-117">By default, sources aren't trusted.</span></span> <span data-ttu-id="62560-118">Vous êtes invité à confirmer que la source est approuvée avant l’installation des packages.</span><span class="sxs-lookup"><span data-stu-id="62560-118">You are prompted to confirm the source is trusted before packages are installed.</span></span> <span data-ttu-id="62560-119">Pour remplacer la valeur par défaut, utilisez le `-Trusted` paramètre.</span><span class="sxs-lookup"><span data-stu-id="62560-119">To override the default, use the `-Trusted` parameter.</span></span>

```powershell
Register-PackageSource -Name MyNuGet -Location https://www.nuget.org/api/v2 -ProviderName NuGet
```

```Output
Name          ProviderName     IsTrusted  Location
----          ------------     ---------  --------
MyNuGet       NuGet            False      https://www.nuget.org/api/v2
```

## <span data-ttu-id="62560-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="62560-120">PARAMETERS</span></span>

### <span data-ttu-id="62560-121">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="62560-121">-ConfigFile</span></span>

<span data-ttu-id="62560-122">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="62560-122">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="62560-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="62560-123">-Credential</span></span>

<span data-ttu-id="62560-124">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’emplacement authentifié.</span><span class="sxs-lookup"><span data-stu-id="62560-124">Specifies a user account that has permission to access the authenticated location.</span></span>

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

### <span data-ttu-id="62560-125">-Force</span><span class="sxs-lookup"><span data-stu-id="62560-125">-Force</span></span>

<span data-ttu-id="62560-126">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="62560-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="62560-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="62560-127">-ForceBootstrap</span></span>

<span data-ttu-id="62560-128">Indique que cette applet de commande installe automatiquement le fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="62560-128">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="62560-129">-Location</span><span class="sxs-lookup"><span data-stu-id="62560-129">-Location</span></span>

<span data-ttu-id="62560-130">Spécifie l’emplacement source du package.</span><span class="sxs-lookup"><span data-stu-id="62560-130">Specifies the package source location.</span></span>

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

### <span data-ttu-id="62560-131">-Name</span><span class="sxs-lookup"><span data-stu-id="62560-131">-Name</span></span>

<span data-ttu-id="62560-132">Spécifie le nom de la source du package à inscrire.</span><span class="sxs-lookup"><span data-stu-id="62560-132">Specifies the name of the package source to register.</span></span>

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

### <span data-ttu-id="62560-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="62560-133">-PackageManagementProvider</span></span>

<span data-ttu-id="62560-134">Spécifie le fournisseur de Package Management.</span><span class="sxs-lookup"><span data-stu-id="62560-134">Specifies the Package Management provider.</span></span>

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

### <span data-ttu-id="62560-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="62560-135">-ProviderName</span></span>

<span data-ttu-id="62560-136">Spécifie le nom du fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="62560-136">Specifies the package provider's name.</span></span>

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

### <span data-ttu-id="62560-137">-Proxy</span><span class="sxs-lookup"><span data-stu-id="62560-137">-Proxy</span></span>

<span data-ttu-id="62560-138">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="62560-138">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="62560-139">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="62560-139">-ProxyCredential</span></span>

<span data-ttu-id="62560-140">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="62560-140">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="62560-141">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="62560-141">-PublishLocation</span></span>

<span data-ttu-id="62560-142">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="62560-142">Specifies the publish location.</span></span>

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

### <span data-ttu-id="62560-143">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="62560-143">-ScriptPublishLocation</span></span>

<span data-ttu-id="62560-144">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="62560-144">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="62560-145">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="62560-145">-ScriptSourceLocation</span></span>

<span data-ttu-id="62560-146">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="62560-146">Specifies the script source location.</span></span>

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

### <span data-ttu-id="62560-147">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="62560-147">-SkipValidate</span></span>

<span data-ttu-id="62560-148">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="62560-148">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="62560-149">-Approuvé</span><span class="sxs-lookup"><span data-stu-id="62560-149">-Trusted</span></span>

<span data-ttu-id="62560-150">Indique que la source du package est approuvée.</span><span class="sxs-lookup"><span data-stu-id="62560-150">Indicates that the package source is trusted.</span></span>

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

### <span data-ttu-id="62560-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="62560-151">-Confirm</span></span>

<span data-ttu-id="62560-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="62560-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="62560-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="62560-153">-WhatIf</span></span>

<span data-ttu-id="62560-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="62560-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="62560-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="62560-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="62560-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="62560-156">CommonParameters</span></span>

<span data-ttu-id="62560-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="62560-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="62560-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="62560-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="62560-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="62560-159">INPUTS</span></span>

## <span data-ttu-id="62560-160">SORTIES</span><span class="sxs-lookup"><span data-stu-id="62560-160">OUTPUTS</span></span>

## <span data-ttu-id="62560-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="62560-161">NOTES</span></span>

## <span data-ttu-id="62560-162">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="62560-162">RELATED LINKS</span></span>

[<span data-ttu-id="62560-163">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="62560-163">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="62560-164">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="62560-164">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="62560-165">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="62560-165">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="62560-166">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="62560-166">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
