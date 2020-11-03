---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 2c4f3526e1277c887a350cacda6641a889cae712
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201290"
---
# <span data-ttu-id="fca08-103">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="fca08-103">Uninstall-Package</span></span>

## <span data-ttu-id="fca08-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fca08-104">SYNOPSIS</span></span>
<span data-ttu-id="fca08-105">Désinstalle un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="fca08-105">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="fca08-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fca08-106">SYNTAX</span></span>

### <span data-ttu-id="fca08-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="fca08-107">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fca08-108">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="fca08-108">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="fca08-109">NuGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="fca08-109">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="fca08-110">NuGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="fca08-110">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="fca08-111">PowerShellGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="fca08-111">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="fca08-112">PowerShellGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="fca08-112">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="fca08-113">Description</span><span class="sxs-lookup"><span data-stu-id="fca08-113">DESCRIPTION</span></span>

<span data-ttu-id="fca08-114">L' `Uninstall-Package` applet de commande désinstalle un ou plusieurs packages logiciels de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fca08-114">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="fca08-115">Pour rechercher les packages installés, utilisez l’applet de commande `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="fca08-115">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="fca08-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fca08-116">EXAMPLES</span></span>

### <span data-ttu-id="fca08-117">Exemple 1 : désinstaller un package</span><span class="sxs-lookup"><span data-stu-id="fca08-117">Example 1: Uninstall a package</span></span>

<span data-ttu-id="fca08-118">L' `Uninstall-Package` applet de commande désinstalle des packages.</span><span class="sxs-lookup"><span data-stu-id="fca08-118">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="fca08-119">Le paramètre **Name** spécifie le package à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="fca08-119">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="fca08-120">Si plusieurs versions d’un package sont installées, la version la plus récente est désinstallée.</span><span class="sxs-lookup"><span data-stu-id="fca08-120">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="fca08-121">Exemple 2 : utiliser le pipeline pour désinstaller un package</span><span class="sxs-lookup"><span data-stu-id="fca08-121">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="fca08-122">`Get-Package` localise un package spécifique et envoie l’objet **SoftwareIdentity** dans le pipeline vers l’applet de commande `Uninsall-Package` .</span><span class="sxs-lookup"><span data-stu-id="fca08-122">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="fca08-123">L' `Get-Package` applet de commande utilise les paramètres **Name** et **RequiredVersion** pour spécifier un package.</span><span class="sxs-lookup"><span data-stu-id="fca08-123">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="fca08-124">Un objet **SoftwareIdentity** est envoyé vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="fca08-124">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="fca08-125">L' `Uninstall-Package` applet de commande reçoit l’objet sous la forme d’un **InputObject** et supprime le package.</span><span class="sxs-lookup"><span data-stu-id="fca08-125">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="fca08-126">L’applet de commande `Uninstall-Package` peut également spécifier une valeur pour le paramètre **InputObject** :</span><span class="sxs-lookup"><span data-stu-id="fca08-126">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="fca08-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fca08-127">PARAMETERS</span></span>

### <span data-ttu-id="fca08-128">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="fca08-128">-AllowClobber</span></span>

<span data-ttu-id="fca08-129">Remplace les messages d’avertissement relatifs aux conflits avec les commandes existantes.</span><span class="sxs-lookup"><span data-stu-id="fca08-129">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="fca08-130">Remplace les commandes existantes qui portent le même nom que les commandes en cours d’installation.</span><span class="sxs-lookup"><span data-stu-id="fca08-130">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-131">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="fca08-131">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="fca08-132">Autorise la désinstallation des packages marqués en tant que version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="fca08-132">Allows packages marked as prerelease to be uninstalled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-133">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="fca08-133">-AllVersions</span></span>

<span data-ttu-id="fca08-134">Indique que cette applet de commande désinstalle toutes les versions du package.</span><span class="sxs-lookup"><span data-stu-id="fca08-134">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="fca08-135">-Destination</span><span class="sxs-lookup"><span data-stu-id="fca08-135">-Destination</span></span>

<span data-ttu-id="fca08-136">Spécifie une chaîne du chemin d’accès à l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="fca08-136">Specifies a string of the path to the input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-137">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="fca08-137">-ExcludeVersion</span></span>

<span data-ttu-id="fca08-138">Basculez pour exclure le numéro de version dans le chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="fca08-138">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-139">-Force</span><span class="sxs-lookup"><span data-stu-id="fca08-139">-Force</span></span>

<span data-ttu-id="fca08-140">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fca08-140">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="fca08-141">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="fca08-141">-ForceBootstrap</span></span>

<span data-ttu-id="fca08-142">Force **PackageManagement** à installer automatiquement le fournisseur de package pour le package spécifié.</span><span class="sxs-lookup"><span data-stu-id="fca08-142">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="fca08-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fca08-143">-InputObject</span></span>

<span data-ttu-id="fca08-144">Accepte l’entrée de pipeline qui spécifie l’objet **SoftwareIdentity** du package à partir de l’applet de commande `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="fca08-144">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="fca08-145">**InputObject** accepte l’objet **SoftwareIdentity** comme une `Get-Package` valeur ou une variable qui contient l’objet.</span><span class="sxs-lookup"><span data-stu-id="fca08-145">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-146">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="fca08-146">-InstallUpdate</span></span>

<span data-ttu-id="fca08-147">Indique que `Uninstall-Package` désinstalle les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="fca08-147">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="fca08-148">-MaximumVersion</span></span>

<span data-ttu-id="fca08-149">Spécifie la version de package maximale autorisée que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="fca08-149">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="fca08-150">Si vous ne spécifiez pas ce paramètre, `Uninstall-Package` désinstalle la version la plus récente du package.</span><span class="sxs-lookup"><span data-stu-id="fca08-150">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

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

### <span data-ttu-id="fca08-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="fca08-151">-MinimumVersion</span></span>

<span data-ttu-id="fca08-152">Spécifie la version de package minimale autorisée que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="fca08-152">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="fca08-153">Si vous n’ajoutez pas ce paramètre, `Uninstall-Package` désinstalle la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="fca08-153">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="fca08-154">-Name</span><span class="sxs-lookup"><span data-stu-id="fca08-154">-Name</span></span>

<span data-ttu-id="fca08-155">Spécifie un ou plusieurs noms de packages.</span><span class="sxs-lookup"><span data-stu-id="fca08-155">Specifies one or more package names.</span></span> <span data-ttu-id="fca08-156">Plusieurs noms de packages doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="fca08-156">Multiple package names must be separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-157">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="fca08-157">-NoPathUpdate</span></span>

<span data-ttu-id="fca08-158">**NoPathUpdate** s’applique uniquement à l’applet de commande `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="fca08-158">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="fca08-159">**NoPathUpdate** est un paramètre dynamique ajouté par le fournisseur et n’est pas pris en charge par `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="fca08-159">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-160">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="fca08-160">-PackageManagementProvider</span></span>

<span data-ttu-id="fca08-161">Spécifie le fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="fca08-161">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-162">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="fca08-162">-ProviderName</span></span>

<span data-ttu-id="fca08-163">Spécifie un ou plusieurs noms de fournisseurs de packages dans lesquels rechercher des packages.</span><span class="sxs-lookup"><span data-stu-id="fca08-163">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="fca08-164">Vous obtenez les noms des fournisseurs de package en exécutant l’applet de commande `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="fca08-164">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="fca08-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="fca08-165">-RequiredVersion</span></span>

<span data-ttu-id="fca08-166">Spécifie la version exacte du package que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="fca08-166">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="fca08-167">Si vous n’ajoutez pas ce paramètre, `Uninstall-Package` désinstalle la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="fca08-167">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="fca08-168">-Étendue</span><span class="sxs-lookup"><span data-stu-id="fca08-168">-Scope</span></span>

<span data-ttu-id="fca08-169">Spécifie l’étendue pour laquelle le package doit être désinstallé.</span><span class="sxs-lookup"><span data-stu-id="fca08-169">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="fca08-170">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fca08-170">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="fca08-171">Utilisateur en cours</span><span class="sxs-lookup"><span data-stu-id="fca08-171">CurrentUser</span></span>
- <span data-ttu-id="fca08-172">AllUsers</span><span class="sxs-lookup"><span data-stu-id="fca08-172">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-173">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="fca08-173">-SkipDependencies</span></span>

<span data-ttu-id="fca08-174">Ignore la désinstallation des dépendances logicielles.</span><span class="sxs-lookup"><span data-stu-id="fca08-174">Skips the uninstallation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-175">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="fca08-175">-SkipPublisherCheck</span></span>

<span data-ttu-id="fca08-176">Vous permet d’obtenir une version de package plus récente que la version installée.</span><span class="sxs-lookup"><span data-stu-id="fca08-176">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="fca08-177">Par exemple, un package installé signé numériquement par un éditeur approuvé, mais pour lequel une nouvelle version n’est pas signée numériquement.</span><span class="sxs-lookup"><span data-stu-id="fca08-177">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-178">-Type</span><span class="sxs-lookup"><span data-stu-id="fca08-178">-Type</span></span>

<span data-ttu-id="fca08-179">Spécifie s’il faut rechercher des packages avec un module, un script ou les deux.</span><span class="sxs-lookup"><span data-stu-id="fca08-179">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="fca08-180">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fca08-180">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="fca08-181">Module</span><span class="sxs-lookup"><span data-stu-id="fca08-181">Module</span></span>
- <span data-ttu-id="fca08-182">Script</span><span class="sxs-lookup"><span data-stu-id="fca08-182">Script</span></span>
- <span data-ttu-id="fca08-183">Tous</span><span class="sxs-lookup"><span data-stu-id="fca08-183">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fca08-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fca08-184">-Confirm</span></span>

<span data-ttu-id="fca08-185">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fca08-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fca08-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fca08-186">-WhatIf</span></span>

<span data-ttu-id="fca08-187">Montre ce qui se passe si l' `Uninstall-Package` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="fca08-187">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="fca08-188">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="fca08-188">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="fca08-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fca08-189">CommonParameters</span></span>

<span data-ttu-id="fca08-190">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fca08-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fca08-191">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fca08-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fca08-192">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fca08-192">INPUTS</span></span>

### <span data-ttu-id="fca08-193">`Uninstall-Package` accepte les objets **SoftwareIdentity** du pipeline en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="fca08-193">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="fca08-194">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fca08-194">OUTPUTS</span></span>

### <span data-ttu-id="fca08-195">`Uninstall-Package` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="fca08-195">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="fca08-196">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fca08-196">NOTES</span></span>

<span data-ttu-id="fca08-197">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fca08-197">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="fca08-198">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="fca08-198">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="fca08-199">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="fca08-199">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="fca08-200">Par exemple, `Uninstall-Package` a le paramètre **PowerShellGet** défini qui inclut `-NoPathUpdate` , `AllowClobber` et `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="fca08-200">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="fca08-201">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fca08-201">RELATED LINKS</span></span>

[<span data-ttu-id="fca08-202">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="fca08-202">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="fca08-203">Find-Package</span><span class="sxs-lookup"><span data-stu-id="fca08-203">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="fca08-204">Get-Package</span><span class="sxs-lookup"><span data-stu-id="fca08-204">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="fca08-205">Install-Package</span><span class="sxs-lookup"><span data-stu-id="fca08-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="fca08-206">Save-Package</span><span class="sxs-lookup"><span data-stu-id="fca08-206">Save-Package</span></span>](Save-Package.md)
