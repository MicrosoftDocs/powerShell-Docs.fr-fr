---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 8b91c5b950e0e16c4ce0821ee2f96b830dab1fc2
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596927"
---
# <span data-ttu-id="73ced-102">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="73ced-102">Get-PackageSource</span></span>

## <span data-ttu-id="73ced-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="73ced-103">SYNOPSIS</span></span>
<span data-ttu-id="73ced-104">Obtient une liste des sources de packages qui sont inscrites pour un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="73ced-104">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="73ced-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="73ced-105">SYNTAX</span></span>

### <span data-ttu-id="73ced-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="73ced-106">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="73ced-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="73ced-107">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="73ced-108">Description</span><span class="sxs-lookup"><span data-stu-id="73ced-108">DESCRIPTION</span></span>

<span data-ttu-id="73ced-109">L' `Get-PackageSource` applet de commande obtient une liste des sources de packages qui sont inscrites auprès de **PackageManagement** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="73ced-109">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="73ced-110">Si vous spécifiez un fournisseur de packages, `Get-PackageSource` obtient uniquement les sources associées au fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="73ced-110">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="73ced-111">Dans le cas contraire, la commande retourne toutes les sources de package inscrites avec **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="73ced-111">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="73ced-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="73ced-112">EXAMPLES</span></span>

### <span data-ttu-id="73ced-113">Exemple 1 : récupération de toutes les sources de package</span><span class="sxs-lookup"><span data-stu-id="73ced-113">Example 1: Get all package sources</span></span>

<span data-ttu-id="73ced-114">L' `Get-PackageSource` applet de commande obtient toutes les sources de package inscrites avec **PackageManagement** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="73ced-114">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

```powershell
Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
PSGallery            PowerShellGet    False      https://www.powershellgallery.com/api/v2
```

### <span data-ttu-id="73ced-115">Exemple 2 : obtenir toutes les sources de package pour un fournisseur spécifique</span><span class="sxs-lookup"><span data-stu-id="73ced-115">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="73ced-116">Cette commande obtient les sources de package inscrites pour un fournisseur spécifique.</span><span class="sxs-lookup"><span data-stu-id="73ced-116">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="73ced-117">`Get-PackageSource` utilise le paramètre **providerName** pour obtenir les sources de package inscrites pour le fournisseur **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="73ced-117">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="73ced-118">Exemple 3 : obtenir des sources à partir d’un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="73ced-118">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="73ced-119">Cette commande utilise un fournisseur de package pour obtenir les sources de package.</span><span class="sxs-lookup"><span data-stu-id="73ced-119">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="73ced-120">`Get-PackageProvider` utilise le paramètre **Name** pour spécifier le nom du fournisseur, **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="73ced-120">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="73ced-121">L’objet est envoyé dans le pipeline à `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="73ced-121">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="73ced-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73ced-122">PARAMETERS</span></span>

### <span data-ttu-id="73ced-123">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="73ced-123">-ConfigFile</span></span>

<span data-ttu-id="73ced-124">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="73ced-124">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="73ced-125">-Force</span><span class="sxs-lookup"><span data-stu-id="73ced-125">-Force</span></span>

<span data-ttu-id="73ced-126">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="73ced-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="73ced-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="73ced-127">-ForceBootstrap</span></span>

<span data-ttu-id="73ced-128">Indique que cette applet de commande force **PackageManagement** à installer automatiquement un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="73ced-128">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="73ced-129">-Location</span><span class="sxs-lookup"><span data-stu-id="73ced-129">-Location</span></span>

<span data-ttu-id="73ced-130">Spécifie l’emplacement d’une source ou d’un référentiel de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="73ced-130">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="73ced-131">-Name</span><span class="sxs-lookup"><span data-stu-id="73ced-131">-Name</span></span>

<span data-ttu-id="73ced-132">Spécifie le nom d’une source de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="73ced-132">Specifies the name of a package management source.</span></span>

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

### <span data-ttu-id="73ced-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="73ced-133">-PackageManagementProvider</span></span>

<span data-ttu-id="73ced-134">Spécifie un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="73ced-134">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="73ced-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="73ced-135">-ProviderName</span></span>

<span data-ttu-id="73ced-136">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="73ced-136">Specifies one or more package provider names.</span></span> <span data-ttu-id="73ced-137">Séparez les noms de plusieurs fournisseurs de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="73ced-137">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="73ced-138">Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.</span><span class="sxs-lookup"><span data-stu-id="73ced-138">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="73ced-139">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="73ced-139">-PublishLocation</span></span>

<span data-ttu-id="73ced-140">Spécifie l’emplacement de publication de la source du package.</span><span class="sxs-lookup"><span data-stu-id="73ced-140">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="73ced-141">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="73ced-141">-ScriptPublishLocation</span></span>

<span data-ttu-id="73ced-142">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="73ced-142">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="73ced-143">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="73ced-143">-ScriptSourceLocation</span></span>

<span data-ttu-id="73ced-144">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="73ced-144">Specifies the script source location.</span></span>

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

### <span data-ttu-id="73ced-145">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="73ced-145">-SkipValidate</span></span>

<span data-ttu-id="73ced-146">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="73ced-146">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="73ced-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73ced-147">CommonParameters</span></span>

<span data-ttu-id="73ced-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73ced-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73ced-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="73ced-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73ced-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="73ced-150">INPUTS</span></span>

## <span data-ttu-id="73ced-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="73ced-151">OUTPUTS</span></span>

### <span data-ttu-id="73ced-152">PackageSource []</span><span class="sxs-lookup"><span data-stu-id="73ced-152">PackageSource[]</span></span>

<span data-ttu-id="73ced-153">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="73ced-153">Specifies one or more package sources.</span></span>

## <span data-ttu-id="73ced-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="73ced-154">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73ced-155">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="73ced-155">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="73ced-156">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="73ced-156">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="73ced-157">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="73ced-157">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="73ced-158">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73ced-158">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="73ced-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="73ced-159">RELATED LINKS</span></span>

[<span data-ttu-id="73ced-160">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="73ced-160">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="73ced-161">Find-Package</span><span class="sxs-lookup"><span data-stu-id="73ced-161">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="73ced-162">Get-Package</span><span class="sxs-lookup"><span data-stu-id="73ced-162">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="73ced-163">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="73ced-163">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="73ced-164">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="73ced-164">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="73ced-165">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="73ced-165">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="73ced-166">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="73ced-166">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
