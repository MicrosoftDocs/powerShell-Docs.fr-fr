---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: ca12f7f2118a004a6f474ae8174b04f9dbb9444d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598988"
---
# <span data-ttu-id="ed2bc-102">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="ed2bc-102">Uninstall-Package</span></span>

## <span data-ttu-id="ed2bc-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ed2bc-103">SYNOPSIS</span></span>
<span data-ttu-id="ed2bc-104">Désinstalle un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-104">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="ed2bc-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ed2bc-105">SYNTAX</span></span>

### <span data-ttu-id="ed2bc-106">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="ed2bc-106">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ed2bc-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="ed2bc-107">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ed2bc-108">NuGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="ed2bc-108">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="ed2bc-109">NuGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="ed2bc-109">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="ed2bc-110">PowerShellGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="ed2bc-110">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="ed2bc-111">PowerShellGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="ed2bc-111">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="ed2bc-112">Description</span><span class="sxs-lookup"><span data-stu-id="ed2bc-112">DESCRIPTION</span></span>

<span data-ttu-id="ed2bc-113">L' `Uninstall-Package` applet de commande désinstalle un ou plusieurs packages logiciels de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-113">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="ed2bc-114">Pour rechercher les packages installés, utilisez l’applet de commande `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-114">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="ed2bc-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ed2bc-115">EXAMPLES</span></span>

### <span data-ttu-id="ed2bc-116">Exemple 1 : désinstaller un package</span><span class="sxs-lookup"><span data-stu-id="ed2bc-116">Example 1: Uninstall a package</span></span>

<span data-ttu-id="ed2bc-117">L' `Uninstall-Package` applet de commande désinstalle des packages.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-117">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="ed2bc-118">Le paramètre **Name** spécifie le package à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-118">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="ed2bc-119">Si plusieurs versions d’un package sont installées, la version la plus récente est désinstallée.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-119">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="ed2bc-120">Exemple 2 : utiliser le pipeline pour désinstaller un package</span><span class="sxs-lookup"><span data-stu-id="ed2bc-120">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="ed2bc-121">`Get-Package` localise un package spécifique et envoie l’objet **SoftwareIdentity** dans le pipeline vers l’applet de commande `Uninsall-Package` .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-121">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="ed2bc-122">L' `Get-Package` applet de commande utilise les paramètres **Name** et **RequiredVersion** pour spécifier un package.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-122">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="ed2bc-123">Un objet **SoftwareIdentity** est envoyé vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-123">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="ed2bc-124">L' `Uninstall-Package` applet de commande reçoit l’objet sous la forme d’un **InputObject** et supprime le package.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-124">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="ed2bc-125">L’applet de commande `Uninstall-Package` peut également spécifier une valeur pour le paramètre **InputObject** :</span><span class="sxs-lookup"><span data-stu-id="ed2bc-125">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="ed2bc-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ed2bc-126">PARAMETERS</span></span>

### <span data-ttu-id="ed2bc-127">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="ed2bc-127">-AllowClobber</span></span>

<span data-ttu-id="ed2bc-128">Remplace les messages d’avertissement relatifs aux conflits avec les commandes existantes.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-128">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="ed2bc-129">Remplace les commandes existantes qui portent le même nom que les commandes en cours d’installation.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-129">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="ed2bc-130">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="ed2bc-130">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="ed2bc-131">Autorise la désinstallation des packages marqués en tant que version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-131">Allows packages marked as prerelease to be uninstalled.</span></span>

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

### <span data-ttu-id="ed2bc-132">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="ed2bc-132">-AllVersions</span></span>

<span data-ttu-id="ed2bc-133">Indique que cette applet de commande désinstalle toutes les versions du package.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-133">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="ed2bc-134">-Destination</span><span class="sxs-lookup"><span data-stu-id="ed2bc-134">-Destination</span></span>

<span data-ttu-id="ed2bc-135">Spécifie une chaîne du chemin d’accès à l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-135">Specifies a string of the path to the input object.</span></span>

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

### <span data-ttu-id="ed2bc-136">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="ed2bc-136">-ExcludeVersion</span></span>

<span data-ttu-id="ed2bc-137">Basculez pour exclure le numéro de version dans le chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-137">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="ed2bc-138">-Force</span><span class="sxs-lookup"><span data-stu-id="ed2bc-138">-Force</span></span>

<span data-ttu-id="ed2bc-139">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-139">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ed2bc-140">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="ed2bc-140">-ForceBootstrap</span></span>

<span data-ttu-id="ed2bc-141">Force **PackageManagement** à installer automatiquement le fournisseur de package pour le package spécifié.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-141">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="ed2bc-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ed2bc-142">-InputObject</span></span>

<span data-ttu-id="ed2bc-143">Accepte l’entrée de pipeline qui spécifie l’objet **SoftwareIdentity** du package à partir de l’applet de commande `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-143">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="ed2bc-144">**InputObject** accepte l’objet **SoftwareIdentity** comme une `Get-Package` valeur ou une variable qui contient l’objet.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-144">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="ed2bc-145">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="ed2bc-145">-InstallUpdate</span></span>

<span data-ttu-id="ed2bc-146">Indique que `Uninstall-Package` désinstalle les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-146">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

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

### <span data-ttu-id="ed2bc-147">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ed2bc-147">-MaximumVersion</span></span>

<span data-ttu-id="ed2bc-148">Spécifie la version de package maximale autorisée que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-148">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="ed2bc-149">Si vous ne spécifiez pas ce paramètre, `Uninstall-Package` désinstalle la version la plus récente du package.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-149">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

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

### <span data-ttu-id="ed2bc-150">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ed2bc-150">-MinimumVersion</span></span>

<span data-ttu-id="ed2bc-151">Spécifie la version de package minimale autorisée que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-151">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="ed2bc-152">Si vous n’ajoutez pas ce paramètre, `Uninstall-Package` désinstalle la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-152">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="ed2bc-153">-Name</span><span class="sxs-lookup"><span data-stu-id="ed2bc-153">-Name</span></span>

<span data-ttu-id="ed2bc-154">Spécifie un ou plusieurs noms de packages.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-154">Specifies one or more package names.</span></span> <span data-ttu-id="ed2bc-155">Plusieurs noms de packages doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-155">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="ed2bc-156">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="ed2bc-156">-NoPathUpdate</span></span>

<span data-ttu-id="ed2bc-157">**NoPathUpdate** s’applique uniquement à l’applet de commande `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-157">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="ed2bc-158">**NoPathUpdate** est un paramètre dynamique ajouté par le fournisseur et n’est pas pris en charge par `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-158">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

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

### <span data-ttu-id="ed2bc-159">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="ed2bc-159">-PackageManagementProvider</span></span>

<span data-ttu-id="ed2bc-160">Spécifie le fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-160">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="ed2bc-161">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="ed2bc-161">-ProviderName</span></span>

<span data-ttu-id="ed2bc-162">Spécifie un ou plusieurs noms de fournisseurs de packages dans lesquels rechercher des packages.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-162">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="ed2bc-163">Vous obtenez les noms des fournisseurs de package en exécutant l’applet de commande `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-163">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="ed2bc-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ed2bc-164">-RequiredVersion</span></span>

<span data-ttu-id="ed2bc-165">Spécifie la version exacte du package que vous souhaitez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-165">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="ed2bc-166">Si vous n’ajoutez pas ce paramètre, `Uninstall-Package` désinstalle la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-166">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="ed2bc-167">-Étendue</span><span class="sxs-lookup"><span data-stu-id="ed2bc-167">-Scope</span></span>

<span data-ttu-id="ed2bc-168">Spécifie l’étendue pour laquelle le package doit être désinstallé.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-168">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="ed2bc-169">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ed2bc-169">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="ed2bc-170">Utilisateur en cours</span><span class="sxs-lookup"><span data-stu-id="ed2bc-170">CurrentUser</span></span>
- <span data-ttu-id="ed2bc-171">AllUsers</span><span class="sxs-lookup"><span data-stu-id="ed2bc-171">AllUsers</span></span>

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

### <span data-ttu-id="ed2bc-172">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="ed2bc-172">-SkipDependencies</span></span>

<span data-ttu-id="ed2bc-173">Ignore la désinstallation des dépendances logicielles.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-173">Skips the uninstallation of software dependencies.</span></span>

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

### <span data-ttu-id="ed2bc-174">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="ed2bc-174">-SkipPublisherCheck</span></span>

<span data-ttu-id="ed2bc-175">Vous permet d’obtenir une version de package plus récente que la version installée.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-175">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="ed2bc-176">Par exemple, un package installé signé numériquement par un éditeur approuvé, mais pour lequel une nouvelle version n’est pas signée numériquement.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-176">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="ed2bc-177">-Type</span><span class="sxs-lookup"><span data-stu-id="ed2bc-177">-Type</span></span>

<span data-ttu-id="ed2bc-178">Spécifie s’il faut rechercher des packages avec un module, un script ou les deux.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-178">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="ed2bc-179">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ed2bc-179">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="ed2bc-180">Module</span><span class="sxs-lookup"><span data-stu-id="ed2bc-180">Module</span></span>
- <span data-ttu-id="ed2bc-181">Script</span><span class="sxs-lookup"><span data-stu-id="ed2bc-181">Script</span></span>
- <span data-ttu-id="ed2bc-182">Tous</span><span class="sxs-lookup"><span data-stu-id="ed2bc-182">All</span></span>

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

### <span data-ttu-id="ed2bc-183">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ed2bc-183">-Confirm</span></span>

<span data-ttu-id="ed2bc-184">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-184">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ed2bc-185">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ed2bc-185">-WhatIf</span></span>

<span data-ttu-id="ed2bc-186">Montre ce qui se passe si l' `Uninstall-Package` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-186">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="ed2bc-187">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-187">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ed2bc-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ed2bc-188">CommonParameters</span></span>

<span data-ttu-id="ed2bc-189">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ed2bc-190">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ed2bc-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ed2bc-191">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ed2bc-191">INPUTS</span></span>

### <span data-ttu-id="ed2bc-192">`Uninstall-Package` accepte les objets **SoftwareIdentity** du pipeline en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-192">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="ed2bc-193">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ed2bc-193">OUTPUTS</span></span>

### <span data-ttu-id="ed2bc-194">`Uninstall-Package` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-194">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="ed2bc-195">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ed2bc-195">NOTES</span></span>

<span data-ttu-id="ed2bc-196">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-196">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="ed2bc-197">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-197">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="ed2bc-198">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="ed2bc-198">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="ed2bc-199">Par exemple, `Uninstall-Package` a le paramètre **PowerShellGet** défini qui inclut `-NoPathUpdate` , `AllowClobber` et `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="ed2bc-199">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="ed2bc-200">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ed2bc-200">RELATED LINKS</span></span>

[<span data-ttu-id="ed2bc-201">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ed2bc-201">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="ed2bc-202">Find-Package</span><span class="sxs-lookup"><span data-stu-id="ed2bc-202">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="ed2bc-203">Get-Package</span><span class="sxs-lookup"><span data-stu-id="ed2bc-203">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="ed2bc-204">Install-Package</span><span class="sxs-lookup"><span data-stu-id="ed2bc-204">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="ed2bc-205">Save-Package</span><span class="sxs-lookup"><span data-stu-id="ed2bc-205">Save-Package</span></span>](Save-Package.md)

