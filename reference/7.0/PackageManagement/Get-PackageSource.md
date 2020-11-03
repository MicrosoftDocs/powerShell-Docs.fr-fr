---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 6fb64b7e95f1f8ddfff6f1be9e880045271706fc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201513"
---
# <span data-ttu-id="89240-103">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="89240-103">Get-PackageSource</span></span>

## <span data-ttu-id="89240-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="89240-104">SYNOPSIS</span></span>
<span data-ttu-id="89240-105">Obtient une liste des sources de packages qui sont inscrites pour un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="89240-105">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="89240-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="89240-106">SYNTAX</span></span>

### <span data-ttu-id="89240-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="89240-107">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="89240-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="89240-108">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="89240-109">Description</span><span class="sxs-lookup"><span data-stu-id="89240-109">DESCRIPTION</span></span>

<span data-ttu-id="89240-110">L' `Get-PackageSource` applet de commande obtient une liste des sources de packages qui sont inscrites auprès de **PackageManagement** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="89240-110">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="89240-111">Si vous spécifiez un fournisseur de packages, `Get-PackageSource` obtient uniquement les sources associées au fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="89240-111">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="89240-112">Dans le cas contraire, la commande retourne toutes les sources de package inscrites avec **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="89240-112">Otherwise, the command returns all package sources that are registered with **PackageManagement** .</span></span>

## <span data-ttu-id="89240-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="89240-113">EXAMPLES</span></span>

### <span data-ttu-id="89240-114">Exemple 1 : récupération de toutes les sources de package</span><span class="sxs-lookup"><span data-stu-id="89240-114">Example 1: Get all package sources</span></span>

<span data-ttu-id="89240-115">L' `Get-PackageSource` applet de commande obtient toutes les sources de package inscrites avec **PackageManagement** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="89240-115">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

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

### <span data-ttu-id="89240-116">Exemple 2 : obtenir toutes les sources de package pour un fournisseur spécifique</span><span class="sxs-lookup"><span data-stu-id="89240-116">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="89240-117">Cette commande obtient les sources de package inscrites pour un fournisseur spécifique.</span><span class="sxs-lookup"><span data-stu-id="89240-117">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="89240-118">`Get-PackageSource` utilise le paramètre **providerName** pour obtenir les sources de package inscrites pour le fournisseur **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="89240-118">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="89240-119">Exemple 3 : obtenir des sources à partir d’un fournisseur de packages</span><span class="sxs-lookup"><span data-stu-id="89240-119">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="89240-120">Cette commande utilise un fournisseur de package pour obtenir les sources de package.</span><span class="sxs-lookup"><span data-stu-id="89240-120">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="89240-121">`Get-PackageProvider` utilise le paramètre **Name** pour spécifier le nom du fournisseur, **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="89240-121">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet** .</span></span> <span data-ttu-id="89240-122">L’objet est envoyé dans le pipeline à `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="89240-122">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="89240-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="89240-123">PARAMETERS</span></span>

### <span data-ttu-id="89240-124">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="89240-124">-ConfigFile</span></span>

<span data-ttu-id="89240-125">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="89240-125">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="89240-126">-Force</span><span class="sxs-lookup"><span data-stu-id="89240-126">-Force</span></span>

<span data-ttu-id="89240-127">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89240-127">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="89240-128">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="89240-128">-ForceBootstrap</span></span>

<span data-ttu-id="89240-129">Indique que cette applet de commande force **PackageManagement** à installer automatiquement un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="89240-129">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="89240-130">-Location</span><span class="sxs-lookup"><span data-stu-id="89240-130">-Location</span></span>

<span data-ttu-id="89240-131">Spécifie l’emplacement d’une source ou d’un référentiel de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="89240-131">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="89240-132">-Name</span><span class="sxs-lookup"><span data-stu-id="89240-132">-Name</span></span>

<span data-ttu-id="89240-133">Spécifie le nom d’une source de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="89240-133">Specifies the name of a package management source.</span></span>

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

### <span data-ttu-id="89240-134">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="89240-134">-PackageManagementProvider</span></span>

<span data-ttu-id="89240-135">Spécifie un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="89240-135">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="89240-136">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="89240-136">-ProviderName</span></span>

<span data-ttu-id="89240-137">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="89240-137">Specifies one or more package provider names.</span></span> <span data-ttu-id="89240-138">Séparez les noms de plusieurs fournisseurs de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="89240-138">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="89240-139">Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.</span><span class="sxs-lookup"><span data-stu-id="89240-139">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="89240-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="89240-140">-PublishLocation</span></span>

<span data-ttu-id="89240-141">Spécifie l’emplacement de publication de la source du package.</span><span class="sxs-lookup"><span data-stu-id="89240-141">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="89240-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="89240-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="89240-143">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="89240-143">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="89240-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="89240-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="89240-145">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="89240-145">Specifies the script source location.</span></span>

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

### <span data-ttu-id="89240-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="89240-146">-SkipValidate</span></span>

<span data-ttu-id="89240-147">Commutateur qui ignore la validation des informations d’identification d’une source de package.</span><span class="sxs-lookup"><span data-stu-id="89240-147">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="89240-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89240-148">CommonParameters</span></span>

<span data-ttu-id="89240-149">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="89240-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="89240-150">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="89240-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="89240-151">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="89240-151">INPUTS</span></span>

## <span data-ttu-id="89240-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="89240-152">OUTPUTS</span></span>

### <span data-ttu-id="89240-153">PackageSource []</span><span class="sxs-lookup"><span data-stu-id="89240-153">PackageSource[]</span></span>

<span data-ttu-id="89240-154">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="89240-154">Specifies one or more package sources.</span></span>

## <span data-ttu-id="89240-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="89240-155">NOTES</span></span>

## <span data-ttu-id="89240-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="89240-156">RELATED LINKS</span></span>

[<span data-ttu-id="89240-157">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="89240-157">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="89240-158">Find-Package</span><span class="sxs-lookup"><span data-stu-id="89240-158">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="89240-159">Get-Package</span><span class="sxs-lookup"><span data-stu-id="89240-159">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="89240-160">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="89240-160">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="89240-161">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="89240-161">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="89240-162">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="89240-162">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="89240-163">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="89240-163">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
