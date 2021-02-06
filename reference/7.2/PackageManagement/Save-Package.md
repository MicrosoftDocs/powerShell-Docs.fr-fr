---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: 93ec8264bad588e38554daddcdf5dc9befce053e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598579"
---
# <span data-ttu-id="38067-102">Save-Package</span><span class="sxs-lookup"><span data-stu-id="38067-102">Save-Package</span></span>

## <span data-ttu-id="38067-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="38067-103">SYNOPSIS</span></span>
<span data-ttu-id="38067-104">Enregistre les packages sur l’ordinateur local sans les installer.</span><span class="sxs-lookup"><span data-stu-id="38067-104">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="38067-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="38067-105">SYNTAX</span></span>

### <span data-ttu-id="38067-106">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="38067-106">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="38067-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="38067-107">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="38067-108">NuGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="38067-108">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="38067-109">NuGet</span><span class="sxs-lookup"><span data-stu-id="38067-109">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="38067-110">PowerShellGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="38067-110">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="38067-111">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="38067-111">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="38067-112">Description</span><span class="sxs-lookup"><span data-stu-id="38067-112">DESCRIPTION</span></span>

<span data-ttu-id="38067-113">L' `Save-Package` applet de commande enregistre les packages sur l’ordinateur local, mais n’installe pas les packages.</span><span class="sxs-lookup"><span data-stu-id="38067-113">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="38067-114">Cette applet de commande enregistre la version la plus récente d’un package, sauf si vous spécifiez un **RequiredVerion**.</span><span class="sxs-lookup"><span data-stu-id="38067-114">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="38067-115">Les paramètres **path** et **LiteralPath** s’excluent mutuellement et ne peuvent pas être ajoutés à la même commande.</span><span class="sxs-lookup"><span data-stu-id="38067-115">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="38067-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="38067-116">EXAMPLES</span></span>

### <span data-ttu-id="38067-117">Exemple 1 : enregistrer un package sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="38067-117">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="38067-118">Cet exemple enregistre la version la plus récente du package dans un répertoire sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="38067-118">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="38067-119">Les dépendances du package sont téléchargées avec le package.</span><span class="sxs-lookup"><span data-stu-id="38067-119">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="38067-120">`Save-Package` utilise le paramètre **Name** pour spécifier le package.</span><span class="sxs-lookup"><span data-stu-id="38067-120">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="38067-121">Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** .</span><span class="sxs-lookup"><span data-stu-id="38067-121">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="38067-122">Le paramètre Path détermine l’emplacement **d'** enregistrement du package.</span><span class="sxs-lookup"><span data-stu-id="38067-122">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="38067-123">Exemple 2 : enregistrer une version de package spécifique</span><span class="sxs-lookup"><span data-stu-id="38067-123">Example 2: Save a specific package version</span></span>

<span data-ttu-id="38067-124">Cet exemple spécifie la version du package et l’enregistre dans un répertoire sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="38067-124">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="38067-125">`Save-Package` utilise le paramètre **Name** pour spécifier le package.</span><span class="sxs-lookup"><span data-stu-id="38067-125">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="38067-126">**RequiredVersion** indique une version de package spécifique.</span><span class="sxs-lookup"><span data-stu-id="38067-126">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="38067-127">Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** .</span><span class="sxs-lookup"><span data-stu-id="38067-127">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="38067-128">Le paramètre Path détermine l’emplacement **d'** enregistrement du package.</span><span class="sxs-lookup"><span data-stu-id="38067-128">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="38067-129">Exemple 3 : utiliser Find-Package pour enregistrer un package</span><span class="sxs-lookup"><span data-stu-id="38067-129">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="38067-130">Cette commande utilise `Find-Package` pour localiser la version la plus récente du package et envoie l’objet à `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="38067-130">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="38067-131">`Find-Package` utilise le paramètre **Name** pour spécifier le package.</span><span class="sxs-lookup"><span data-stu-id="38067-131">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="38067-132">Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** .</span><span class="sxs-lookup"><span data-stu-id="38067-132">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="38067-133">L’objet est envoyé dans le pipeline à `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="38067-133">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="38067-134">Le paramètre Path détermine l’emplacement **d'** enregistrement du package.</span><span class="sxs-lookup"><span data-stu-id="38067-134">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="38067-135">Exemple 4 : enregistrer et installer le package</span><span class="sxs-lookup"><span data-stu-id="38067-135">Example 4: Save and install the package</span></span>

<span data-ttu-id="38067-136">La version la plus récente du package et ses dépendances sont téléchargées et installées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="38067-136">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="38067-137">`Save-Package` télécharge le fichier de package et ses dépendances sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="38067-137">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="38067-138">`Install-Package` installe le package et les dépendances à partir du répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="38067-138">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="38067-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38067-139">PARAMETERS</span></span>

### <span data-ttu-id="38067-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="38067-140">-AcceptLicense</span></span>

<span data-ttu-id="38067-141">Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="38067-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-142">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="38067-142">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="38067-143">Autorise l’enregistrement des packages marqués comme préversion.</span><span class="sxs-lookup"><span data-stu-id="38067-143">Allows packages marked as Prerelease to be saved.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet, PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-144">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="38067-144">-AllVersions</span></span>

<span data-ttu-id="38067-145">Indique que cette applet de commande enregistre toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="38067-145">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="38067-146">-Command</span><span class="sxs-lookup"><span data-stu-id="38067-146">-Command</span></span>

<span data-ttu-id="38067-147">Spécifie une ou plusieurs commandes incluses dans le package.</span><span class="sxs-lookup"><span data-stu-id="38067-147">Specifies one or more commands included in the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-148">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="38067-148">-ConfigFile</span></span>

<span data-ttu-id="38067-149">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="38067-149">Specifies a configuration File.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-150">-Contient</span><span class="sxs-lookup"><span data-stu-id="38067-150">-Contains</span></span>

<span data-ttu-id="38067-151">`Save-Package` obtient des objets si un élément dans les valeurs de propriété de l’objet correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38067-151">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="38067-152">-Credential</span></span>

<span data-ttu-id="38067-153">Spécifie un compte d’utilisateur qui a l’autorisation d’enregistrer un package à partir d’un fournisseur de package ou d’une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="38067-153">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

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

### <span data-ttu-id="38067-154">-DscResource</span><span class="sxs-lookup"><span data-stu-id="38067-154">-DscResource</span></span>

<span data-ttu-id="38067-155">Spécifie une ou plusieurs ressources de configuration d’état souhaité (DSC) pour le package.</span><span class="sxs-lookup"><span data-stu-id="38067-155">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-156">-Filter</span><span class="sxs-lookup"><span data-stu-id="38067-156">-Filter</span></span>

<span data-ttu-id="38067-157">Spécifie un filtre pour le package.</span><span class="sxs-lookup"><span data-stu-id="38067-157">Specifies a filter for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-158">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="38067-158">-FilterOnTag</span></span>

<span data-ttu-id="38067-159">Spécifie la balise qui filtre les résultats.</span><span class="sxs-lookup"><span data-stu-id="38067-159">Specifies the tag that filters the results.</span></span> <span data-ttu-id="38067-160">Les résultats qui ne contiennent pas la balise spécifiée sont exclus.</span><span class="sxs-lookup"><span data-stu-id="38067-160">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-161">-Force</span><span class="sxs-lookup"><span data-stu-id="38067-161">-Force</span></span>

<span data-ttu-id="38067-162">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38067-162">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="38067-163">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="38067-163">-ForceBootstrap</span></span>

<span data-ttu-id="38067-164">Indique que `Save-Package` force **PackageManagement** à installer automatiquement le fournisseur de package pour le package spécifié.</span><span class="sxs-lookup"><span data-stu-id="38067-164">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="38067-165">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="38067-165">-Headers</span></span>

<span data-ttu-id="38067-166">Spécifie les en-têtes pour le package.</span><span class="sxs-lookup"><span data-stu-id="38067-166">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-167">-Comprend</span><span class="sxs-lookup"><span data-stu-id="38067-167">-Includes</span></span>

<span data-ttu-id="38067-168">Indique les ressources incluses dans le package.</span><span class="sxs-lookup"><span data-stu-id="38067-168">Indicates the resources that the package includes.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: DscResource, Cmdlet, Function, Workflow, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-169">-InputObject</span><span class="sxs-lookup"><span data-stu-id="38067-169">-InputObject</span></span>

<span data-ttu-id="38067-170">Objet d’ID de logiciel qui représente le package que vous souhaitez enregistrer.</span><span class="sxs-lookup"><span data-stu-id="38067-170">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="38067-171">Les ID de logiciel font partie des résultats de l’applet de commande `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="38067-171">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="38067-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="38067-172">-LiteralPath</span></span>

<span data-ttu-id="38067-173">Spécifie le chemin d’accès littéral dans lequel vous souhaitez enregistrer le package.</span><span class="sxs-lookup"><span data-stu-id="38067-173">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="38067-174">Vous ne pouvez pas ajouter à la fois ce paramètre et le paramètre **path** à la même commande.</span><span class="sxs-lookup"><span data-stu-id="38067-174">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="38067-175">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="38067-175">-MaximumVersion</span></span>

<span data-ttu-id="38067-176">Spécifie la version maximale du package que vous souhaitez enregistrer.</span><span class="sxs-lookup"><span data-stu-id="38067-176">Specifies the maximum version of the package that you want to save.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-177">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="38067-177">-MinimumVersion</span></span>

<span data-ttu-id="38067-178">Spécifie la version minimale du package que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="38067-178">Specifies the minimum version of the package that you want to find.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-179">-Name</span><span class="sxs-lookup"><span data-stu-id="38067-179">-Name</span></span>

<span data-ttu-id="38067-180">Spécifie un ou plusieurs noms de packages.</span><span class="sxs-lookup"><span data-stu-id="38067-180">Specifies one or more package names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="38067-181">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="38067-181">-PackageManagementProvider</span></span>

<span data-ttu-id="38067-182">Spécifie un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="38067-182">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-183">-Path</span><span class="sxs-lookup"><span data-stu-id="38067-183">-Path</span></span>

<span data-ttu-id="38067-184">Spécifie l’emplacement sur l’ordinateur local où stocker le package.</span><span class="sxs-lookup"><span data-stu-id="38067-184">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="38067-185">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="38067-185">-ProviderName</span></span>

<span data-ttu-id="38067-186">Spécifie un ou plusieurs noms de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="38067-186">Specifies one or more provider names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="38067-187">-Proxy</span><span class="sxs-lookup"><span data-stu-id="38067-187">-Proxy</span></span>

<span data-ttu-id="38067-188">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="38067-188">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="38067-189">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="38067-189">-ProxyCredential</span></span>

<span data-ttu-id="38067-190">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="38067-190">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="38067-191">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="38067-191">-PublishLocation</span></span>

<span data-ttu-id="38067-192">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="38067-192">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-193">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="38067-193">-RequiredVersion</span></span>

<span data-ttu-id="38067-194">Spécifie la version exacte du package à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="38067-194">Specifies the exact version of the package to save.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-195">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="38067-195">-RoleCapability</span></span>

<span data-ttu-id="38067-196">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="38067-196">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-197">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="38067-197">-ScriptPublishLocation</span></span>

<span data-ttu-id="38067-198">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="38067-198">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-199">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="38067-199">-ScriptSourceLocation</span></span>

<span data-ttu-id="38067-200">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="38067-200">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-201">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="38067-201">-SkipValidate</span></span>

<span data-ttu-id="38067-202">Commutateur qui ignore la validation des informations d’identification d’un package.</span><span class="sxs-lookup"><span data-stu-id="38067-202">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-203">-Source</span><span class="sxs-lookup"><span data-stu-id="38067-203">-Source</span></span>

<span data-ttu-id="38067-204">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="38067-204">Specifies one or more package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="38067-205">-Tag</span><span class="sxs-lookup"><span data-stu-id="38067-205">-Tag</span></span>

<span data-ttu-id="38067-206">Spécifie une balise à rechercher dans les métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="38067-206">Specifies a tag to search for within the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-207">-Type</span><span class="sxs-lookup"><span data-stu-id="38067-207">-Type</span></span>

<span data-ttu-id="38067-208">Spécifie s’il faut rechercher des packages à l’aide d’un module, d’un script ou de l’un ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="38067-208">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38067-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="38067-209">-Confirm</span></span>

<span data-ttu-id="38067-210">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38067-210">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="38067-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="38067-211">-WhatIf</span></span>

<span data-ttu-id="38067-212">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38067-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="38067-213">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="38067-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="38067-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38067-214">CommonParameters</span></span>

<span data-ttu-id="38067-215">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38067-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38067-216">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="38067-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="38067-217">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="38067-217">INPUTS</span></span>

### <span data-ttu-id="38067-218">`Save-Package` accepte les objets du pipeline.</span><span class="sxs-lookup"><span data-stu-id="38067-218">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="38067-219">SORTIES</span><span class="sxs-lookup"><span data-stu-id="38067-219">OUTPUTS</span></span>

### <span data-ttu-id="38067-220">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="38067-220">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="38067-221">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="38067-221">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38067-222">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="38067-222">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="38067-223">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="38067-223">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="38067-224">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="38067-224">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="38067-225">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38067-225">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="38067-226">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="38067-226">RELATED LINKS</span></span>

[<span data-ttu-id="38067-227">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="38067-227">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="38067-228">Get-Package</span><span class="sxs-lookup"><span data-stu-id="38067-228">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="38067-229">Install-Package</span><span class="sxs-lookup"><span data-stu-id="38067-229">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="38067-230">Save-Package</span><span class="sxs-lookup"><span data-stu-id="38067-230">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="38067-231">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="38067-231">Uninstall-Package</span></span>](Uninstall-Package.md)
