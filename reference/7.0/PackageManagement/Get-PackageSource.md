---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: e1e4814d0128cc1f170bee26425c540c007dbdd4
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890489"
---
# <span data-ttu-id="00f7e-103">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="00f7e-103">Get-PackageSource</span></span>

## <span data-ttu-id="00f7e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="00f7e-104">SYNOPSIS</span></span>
<span data-ttu-id="00f7e-105">Obtient une liste des sources de packages qui sont inscrites pour un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="00f7e-105">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="00f7e-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="00f7e-106">SYNTAX</span></span>

### <span data-ttu-id="00f7e-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="00f7e-107">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="00f7e-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="00f7e-108">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="00f7e-109">Description</span><span class="sxs-lookup"><span data-stu-id="00f7e-109">DESCRIPTION</span></span>

<span data-ttu-id="00f7e-110">L' `Get-PackageSource` applet de commande obtient une liste des sources de packages qui sont inscrites auprès de **PackageManagement** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="00f7e-110">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="00f7e-111">Si vous spécifiez un fournisseur de packages, `Get-PackageSource` obtient uniquement les sources associées au fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="00f7e-111">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="00f7e-112">Dans le cas contraire, la commande retourne toutes les sources de package inscrites avec **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="00f7e-112">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="00f7e-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="00f7e-113">EXAMPLES</span></span>

### <span data-ttu-id="00f7e-114">Exemple 1 : récupération de toutes les sources de package</span><span class="sxs-lookup"><span data-stu-id="00f7e-114">Example 1: Get all package sources</span></span>

<span data-ttu-id="00f7e-115">L' `Get-PackageSource` applet de commande obtient toutes les sources de package inscrites avec **PackageManagement** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="00f7e-115">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

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

### <span data-ttu-id="00f7e-116">Exemple 2 : obtenir toutes les sources de package pour un fournisseur spécifique</span><span class="sxs-lookup"><span data-stu-id="00f7e-116">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="00f7e-117">Cette commande obtient les sources de package inscrites pour un fournisseur spécifique.</span><span class="sxs-lookup"><span data-stu-id="00f7e-117">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="00f7e-118">`Get-PackageSource` utilise le paramètre **providerName** pour obtenir les sources de package inscrites pour le fournisseur **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="00f7e-118">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="00f7e-119">Exemple 3 : obtenir des sources à partir d’un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="00f7e-119">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="00f7e-120">Cette commande utilise un fournisseur de package pour obtenir les sources de package.</span><span class="sxs-lookup"><span data-stu-id="00f7e-120">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="00f7e-121">`Get-PackageProvider` utilise le paramètre **Name** pour spécifier le nom du fournisseur, **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="00f7e-121">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="00f7e-122">L’objet est envoyé dans le pipeline à `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="00f7e-122">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="00f7e-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="00f7e-123">PARAMETERS</span></span>

### <span data-ttu-id="00f7e-124">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="00f7e-124">-ConfigFile</span></span>

<span data-ttu-id="00f7e-125">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="00f7e-125">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="00f7e-126">-Force</span><span class="sxs-lookup"><span data-stu-id="00f7e-126">-Force</span></span>

<span data-ttu-id="00f7e-127">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="00f7e-127">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="00f7e-128">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="00f7e-128">-ForceBootstrap</span></span>

<span data-ttu-id="00f7e-129">Indique que cette applet de commande force **PackageManagement** à installer automatiquement un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="00f7e-129">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="00f7e-130">-Location</span><span class="sxs-lookup"><span data-stu-id="00f7e-130">-Location</span></span>

<span data-ttu-id="00f7e-131">Spécifie l’emplacement d’une source ou d’un référentiel de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="00f7e-131">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="00f7e-132">-Name</span><span class="sxs-lookup"><span data-stu-id="00f7e-132">-Name</span></span>

<span data-ttu-id="00f7e-133">Spécifie le nom d’une source de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="00f7e-133">Specifies the name of a package management source.</span></span>

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

### <span data-ttu-id="00f7e-134">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="00f7e-134">-PackageManagementProvider</span></span>

<span data-ttu-id="00f7e-135">Spécifie un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="00f7e-135">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="00f7e-136">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="00f7e-136">-ProviderName</span></span>

<span data-ttu-id="00f7e-137">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="00f7e-137">Specifies one or more package provider names.</span></span> <span data-ttu-id="00f7e-138">Séparez les noms de plusieurs fournisseurs de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="00f7e-138">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="00f7e-139">Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.</span><span class="sxs-lookup"><span data-stu-id="00f7e-139">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="00f7e-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="00f7e-140">-PublishLocation</span></span>

<span data-ttu-id="00f7e-141">Spécifie l’emplacement de publication de la source du package.</span><span class="sxs-lookup"><span data-stu-id="00f7e-141">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="00f7e-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="00f7e-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="00f7e-143">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="00f7e-143">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="00f7e-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="00f7e-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="00f7e-145">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="00f7e-145">Specifies the script source location.</span></span>

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

### <span data-ttu-id="00f7e-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="00f7e-146">-SkipValidate</span></span>

<span data-ttu-id="00f7e-147">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="00f7e-147">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="00f7e-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="00f7e-148">CommonParameters</span></span>

<span data-ttu-id="00f7e-149">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="00f7e-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="00f7e-150">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="00f7e-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="00f7e-151">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="00f7e-151">INPUTS</span></span>

## <span data-ttu-id="00f7e-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="00f7e-152">OUTPUTS</span></span>

### <span data-ttu-id="00f7e-153">PackageSource []</span><span class="sxs-lookup"><span data-stu-id="00f7e-153">PackageSource[]</span></span>

<span data-ttu-id="00f7e-154">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="00f7e-154">Specifies one or more package sources.</span></span>

## <span data-ttu-id="00f7e-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="00f7e-155">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00f7e-156">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="00f7e-156">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="00f7e-157">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="00f7e-157">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="00f7e-158">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="00f7e-158">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="00f7e-159">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00f7e-159">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="00f7e-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="00f7e-160">RELATED LINKS</span></span>

[<span data-ttu-id="00f7e-161">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="00f7e-161">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="00f7e-162">Find-Package</span><span class="sxs-lookup"><span data-stu-id="00f7e-162">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="00f7e-163">Get-Package</span><span class="sxs-lookup"><span data-stu-id="00f7e-163">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="00f7e-164">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="00f7e-164">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="00f7e-165">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="00f7e-165">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="00f7e-166">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="00f7e-166">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="00f7e-167">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="00f7e-167">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
