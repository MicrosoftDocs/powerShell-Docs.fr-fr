---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: f94f1e3feba96aa49d44c25f2775ac9cffd0c459
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203694"
---
# <span data-ttu-id="32d5e-103">Save-Package</span><span class="sxs-lookup"><span data-stu-id="32d5e-103">Save-Package</span></span>

## <span data-ttu-id="32d5e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="32d5e-104">SYNOPSIS</span></span>
<span data-ttu-id="32d5e-105">Enregistre les packages sur l’ordinateur local sans les installer.</span><span class="sxs-lookup"><span data-stu-id="32d5e-105">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="32d5e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32d5e-106">SYNTAX</span></span>

### <span data-ttu-id="32d5e-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="32d5e-107">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="32d5e-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="32d5e-108">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="32d5e-109">NuGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="32d5e-109">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="32d5e-110">NuGet</span><span class="sxs-lookup"><span data-stu-id="32d5e-110">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="32d5e-111">PowerShellGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="32d5e-111">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="32d5e-112">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="32d5e-112">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="32d5e-113">Description</span><span class="sxs-lookup"><span data-stu-id="32d5e-113">DESCRIPTION</span></span>

<span data-ttu-id="32d5e-114">L' `Save-Package` applet de commande enregistre les packages sur l’ordinateur local, mais n’installe pas les packages.</span><span class="sxs-lookup"><span data-stu-id="32d5e-114">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="32d5e-115">Cette applet de commande enregistre la version la plus récente d’un package, sauf si vous spécifiez un **RequiredVerion** .</span><span class="sxs-lookup"><span data-stu-id="32d5e-115">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion** .</span></span> <span data-ttu-id="32d5e-116">Les paramètres **path** et **LiteralPath** s’excluent mutuellement et ne peuvent pas être ajoutés à la même commande.</span><span class="sxs-lookup"><span data-stu-id="32d5e-116">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="32d5e-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="32d5e-117">EXAMPLES</span></span>

### <span data-ttu-id="32d5e-118">Exemple 1 : enregistrer un package sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="32d5e-118">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="32d5e-119">Cet exemple enregistre la version la plus récente du package dans un répertoire sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="32d5e-119">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="32d5e-120">Les dépendances du package sont téléchargées avec le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-120">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="32d5e-121">`Save-Package` utilise le paramètre **Name** pour spécifier le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-121">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="32d5e-122">Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** .</span><span class="sxs-lookup"><span data-stu-id="32d5e-122">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="32d5e-123">Le paramètre Path détermine l’emplacement **d'** enregistrement du package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-123">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="32d5e-124">Exemple 2 : enregistrer une version de package spécifique</span><span class="sxs-lookup"><span data-stu-id="32d5e-124">Example 2: Save a specific package version</span></span>

<span data-ttu-id="32d5e-125">Cet exemple spécifie la version du package et l’enregistre dans un répertoire sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="32d5e-125">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="32d5e-126">`Save-Package` utilise le paramètre **Name** pour spécifier le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-126">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="32d5e-127">**RequiredVersion** indique une version de package spécifique.</span><span class="sxs-lookup"><span data-stu-id="32d5e-127">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="32d5e-128">Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** .</span><span class="sxs-lookup"><span data-stu-id="32d5e-128">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="32d5e-129">Le paramètre Path détermine l’emplacement **d'** enregistrement du package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-129">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="32d5e-130">Exemple 3 : utiliser Find-Package pour enregistrer un package</span><span class="sxs-lookup"><span data-stu-id="32d5e-130">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="32d5e-131">Cette commande utilise `Find-Package` pour localiser la version la plus récente du package et envoie l’objet à `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="32d5e-131">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="32d5e-132">`Find-Package` utilise le paramètre **Name** pour spécifier le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-132">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="32d5e-133">Le package est téléchargé à partir du référentiel spécifié par le paramètre **providerName** .</span><span class="sxs-lookup"><span data-stu-id="32d5e-133">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="32d5e-134">L’objet est envoyé dans le pipeline à `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="32d5e-134">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="32d5e-135">Le paramètre Path détermine l’emplacement **d'** enregistrement du package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-135">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="32d5e-136">Exemple 4 : enregistrer et installer le package</span><span class="sxs-lookup"><span data-stu-id="32d5e-136">Example 4: Save and install the package</span></span>

<span data-ttu-id="32d5e-137">La version la plus récente du package et ses dépendances sont téléchargées et installées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="32d5e-137">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="32d5e-138">`Save-Package` télécharge le fichier de package et ses dépendances sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="32d5e-138">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="32d5e-139">`Install-Package` installe le package et les dépendances à partir du répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="32d5e-139">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="32d5e-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32d5e-140">PARAMETERS</span></span>

### <span data-ttu-id="32d5e-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="32d5e-141">-AcceptLicense</span></span>

<span data-ttu-id="32d5e-142">Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="32d5e-142">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="32d5e-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="32d5e-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="32d5e-144">Autorise l’enregistrement des packages marqués comme préversion.</span><span class="sxs-lookup"><span data-stu-id="32d5e-144">Allows packages marked as Prerelease to be saved.</span></span>

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

### <span data-ttu-id="32d5e-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="32d5e-145">-AllVersions</span></span>

<span data-ttu-id="32d5e-146">Indique que cette applet de commande enregistre toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-146">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="32d5e-147">-Command</span><span class="sxs-lookup"><span data-stu-id="32d5e-147">-Command</span></span>

<span data-ttu-id="32d5e-148">Spécifie une ou plusieurs commandes incluses dans le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-148">Specifies one or more commands included in the package.</span></span>

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

### <span data-ttu-id="32d5e-149">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="32d5e-149">-ConfigFile</span></span>

<span data-ttu-id="32d5e-150">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="32d5e-150">Specifies a configuration File.</span></span>

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

### <span data-ttu-id="32d5e-151">-Contient</span><span class="sxs-lookup"><span data-stu-id="32d5e-151">-Contains</span></span>

<span data-ttu-id="32d5e-152">`Save-Package` obtient des objets si un élément dans les valeurs de propriété de l’objet correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="32d5e-152">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

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

### <span data-ttu-id="32d5e-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="32d5e-153">-Credential</span></span>

<span data-ttu-id="32d5e-154">Spécifie un compte d’utilisateur qui a l’autorisation d’enregistrer un package à partir d’un fournisseur de package ou d’une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="32d5e-154">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

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

### <span data-ttu-id="32d5e-155">-DscResource</span><span class="sxs-lookup"><span data-stu-id="32d5e-155">-DscResource</span></span>

<span data-ttu-id="32d5e-156">Spécifie une ou plusieurs ressources de configuration d’état souhaité (DSC) pour le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-156">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

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

### <span data-ttu-id="32d5e-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="32d5e-157">-Filter</span></span>

<span data-ttu-id="32d5e-158">Spécifie un filtre pour le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-158">Specifies a filter for the package.</span></span>

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

### <span data-ttu-id="32d5e-159">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="32d5e-159">-FilterOnTag</span></span>

<span data-ttu-id="32d5e-160">Spécifie la balise qui filtre les résultats.</span><span class="sxs-lookup"><span data-stu-id="32d5e-160">Specifies the tag that filters the results.</span></span> <span data-ttu-id="32d5e-161">Les résultats qui ne contiennent pas la balise spécifiée sont exclus.</span><span class="sxs-lookup"><span data-stu-id="32d5e-161">Results that don't contain the specified tag are excluded.</span></span>

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

### <span data-ttu-id="32d5e-162">-Force</span><span class="sxs-lookup"><span data-stu-id="32d5e-162">-Force</span></span>

<span data-ttu-id="32d5e-163">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="32d5e-163">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="32d5e-164">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="32d5e-164">-ForceBootstrap</span></span>

<span data-ttu-id="32d5e-165">Indique que `Save-Package` force **PackageManagement** à installer automatiquement le fournisseur de package pour le package spécifié.</span><span class="sxs-lookup"><span data-stu-id="32d5e-165">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="32d5e-166">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="32d5e-166">-Headers</span></span>

<span data-ttu-id="32d5e-167">Spécifie les en-têtes pour le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-167">Specifies the headers for the package.</span></span>

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

### <span data-ttu-id="32d5e-168">-Comprend</span><span class="sxs-lookup"><span data-stu-id="32d5e-168">-Includes</span></span>

<span data-ttu-id="32d5e-169">Indique les ressources incluses dans le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-169">Indicates the resources that the package includes.</span></span>

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

### <span data-ttu-id="32d5e-170">-InputObject</span><span class="sxs-lookup"><span data-stu-id="32d5e-170">-InputObject</span></span>

<span data-ttu-id="32d5e-171">Objet d’ID de logiciel qui représente le package que vous souhaitez enregistrer.</span><span class="sxs-lookup"><span data-stu-id="32d5e-171">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="32d5e-172">Les ID de logiciel font partie des résultats de l’applet de commande `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="32d5e-172">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

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

### <span data-ttu-id="32d5e-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32d5e-173">-LiteralPath</span></span>

<span data-ttu-id="32d5e-174">Spécifie le chemin d’accès littéral dans lequel vous souhaitez enregistrer le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-174">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="32d5e-175">Vous ne pouvez pas ajouter à la fois ce paramètre et le paramètre **path** à la même commande.</span><span class="sxs-lookup"><span data-stu-id="32d5e-175">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="32d5e-176">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="32d5e-176">-MaximumVersion</span></span>

<span data-ttu-id="32d5e-177">Spécifie la version maximale du package que vous souhaitez enregistrer.</span><span class="sxs-lookup"><span data-stu-id="32d5e-177">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="32d5e-178">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="32d5e-178">-MinimumVersion</span></span>

<span data-ttu-id="32d5e-179">Spécifie la version minimale du package que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="32d5e-179">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="32d5e-180">-Name</span><span class="sxs-lookup"><span data-stu-id="32d5e-180">-Name</span></span>

<span data-ttu-id="32d5e-181">Spécifie un ou plusieurs noms de packages.</span><span class="sxs-lookup"><span data-stu-id="32d5e-181">Specifies one or more package names.</span></span>

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

### <span data-ttu-id="32d5e-182">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="32d5e-182">-PackageManagementProvider</span></span>

<span data-ttu-id="32d5e-183">Spécifie un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="32d5e-183">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="32d5e-184">-Path</span><span class="sxs-lookup"><span data-stu-id="32d5e-184">-Path</span></span>

<span data-ttu-id="32d5e-185">Spécifie l’emplacement sur l’ordinateur local où stocker le package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-185">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="32d5e-186">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="32d5e-186">-ProviderName</span></span>

<span data-ttu-id="32d5e-187">Spécifie un ou plusieurs noms de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="32d5e-187">Specifies one or more provider names.</span></span>

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

### <span data-ttu-id="32d5e-188">-Proxy</span><span class="sxs-lookup"><span data-stu-id="32d5e-188">-Proxy</span></span>

<span data-ttu-id="32d5e-189">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="32d5e-189">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="32d5e-190">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="32d5e-190">-ProxyCredential</span></span>

<span data-ttu-id="32d5e-191">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="32d5e-191">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="32d5e-192">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="32d5e-192">-PublishLocation</span></span>

<span data-ttu-id="32d5e-193">Spécifie l’emplacement de publication.</span><span class="sxs-lookup"><span data-stu-id="32d5e-193">Specifies the publish location.</span></span>

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

### <span data-ttu-id="32d5e-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="32d5e-194">-RequiredVersion</span></span>

<span data-ttu-id="32d5e-195">Spécifie la version exacte du package à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="32d5e-195">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="32d5e-196">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="32d5e-196">-RoleCapability</span></span>

<span data-ttu-id="32d5e-197">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="32d5e-197">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="32d5e-198">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="32d5e-198">-ScriptPublishLocation</span></span>

<span data-ttu-id="32d5e-199">Spécifie l’emplacement de publication du script.</span><span class="sxs-lookup"><span data-stu-id="32d5e-199">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="32d5e-200">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="32d5e-200">-ScriptSourceLocation</span></span>

<span data-ttu-id="32d5e-201">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="32d5e-201">Specifies the script source location.</span></span>

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

### <span data-ttu-id="32d5e-202">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="32d5e-202">-SkipValidate</span></span>

<span data-ttu-id="32d5e-203">Commutateur qui ignore la validation des informations d’identification d’un package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-203">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="32d5e-204">-Source</span><span class="sxs-lookup"><span data-stu-id="32d5e-204">-Source</span></span>

<span data-ttu-id="32d5e-205">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-205">Specifies one or more package sources.</span></span>

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

### <span data-ttu-id="32d5e-206">-Tag</span><span class="sxs-lookup"><span data-stu-id="32d5e-206">-Tag</span></span>

<span data-ttu-id="32d5e-207">Spécifie une balise à rechercher dans les métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="32d5e-207">Specifies a tag to search for within the package metadata.</span></span>

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

### <span data-ttu-id="32d5e-208">-Type</span><span class="sxs-lookup"><span data-stu-id="32d5e-208">-Type</span></span>

<span data-ttu-id="32d5e-209">Spécifie s’il faut rechercher des packages à l’aide d’un module, d’un script ou de l’un ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="32d5e-209">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="32d5e-210">-Confirm</span><span class="sxs-lookup"><span data-stu-id="32d5e-210">-Confirm</span></span>

<span data-ttu-id="32d5e-211">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32d5e-211">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="32d5e-212">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="32d5e-212">-WhatIf</span></span>

<span data-ttu-id="32d5e-213">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32d5e-213">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="32d5e-214">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="32d5e-214">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="32d5e-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32d5e-215">CommonParameters</span></span>

<span data-ttu-id="32d5e-216">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32d5e-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32d5e-217">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="32d5e-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="32d5e-218">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="32d5e-218">INPUTS</span></span>

### <span data-ttu-id="32d5e-219">`Save-Package` accepte les objets du pipeline.</span><span class="sxs-lookup"><span data-stu-id="32d5e-219">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="32d5e-220">SORTIES</span><span class="sxs-lookup"><span data-stu-id="32d5e-220">OUTPUTS</span></span>

### <span data-ttu-id="32d5e-221">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="32d5e-221">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="32d5e-222">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="32d5e-222">NOTES</span></span>

## <span data-ttu-id="32d5e-223">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="32d5e-223">RELATED LINKS</span></span>

[<span data-ttu-id="32d5e-224">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="32d5e-224">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="32d5e-225">Get-Package</span><span class="sxs-lookup"><span data-stu-id="32d5e-225">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="32d5e-226">Install-Package</span><span class="sxs-lookup"><span data-stu-id="32d5e-226">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="32d5e-227">Save-Package</span><span class="sxs-lookup"><span data-stu-id="32d5e-227">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="32d5e-228">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="32d5e-228">Uninstall-Package</span></span>](Uninstall-Package.md)
