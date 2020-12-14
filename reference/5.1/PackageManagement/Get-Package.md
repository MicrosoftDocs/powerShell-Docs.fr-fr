---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: bc6ba83a6f0d585e166b1bdc419c8b9c7148e47c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892880"
---
# <span data-ttu-id="588bb-103">Get-Package</span><span class="sxs-lookup"><span data-stu-id="588bb-103">Get-Package</span></span>

## <span data-ttu-id="588bb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="588bb-104">SYNOPSIS</span></span>
<span data-ttu-id="588bb-105">Retourne une liste de tous les packages logiciels qui ont été installés avec **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="588bb-105">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

## <span data-ttu-id="588bb-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="588bb-106">SYNTAX</span></span>

### <span data-ttu-id="588bb-107">MSI</span><span class="sxs-lookup"><span data-stu-id="588bb-107">msi</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-AdditionalArguments <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="588bb-108">Programmes</span><span class="sxs-lookup"><span data-stu-id="588bb-108">Programs</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-IncludeWindowsInstaller] [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="588bb-109">NuGet</span><span class="sxs-lookup"><span data-stu-id="588bb-109">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="588bb-110">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="588bb-110">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="588bb-111">Description</span><span class="sxs-lookup"><span data-stu-id="588bb-111">DESCRIPTION</span></span>

<span data-ttu-id="588bb-112">L' `Get-Package` applet de commande renvoie la liste de tous les packages logiciels sur l’ordinateur local qui ont été installés avec **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="588bb-112">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement**.</span></span> <span data-ttu-id="588bb-113">Vous pouvez exécuter `Get-Package` sur des ordinateurs distants en l’exécutant dans le cadre d’une `Invoke-Command` commande ou d’un `Enter-PSSession` script.</span><span class="sxs-lookup"><span data-stu-id="588bb-113">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="588bb-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="588bb-114">EXAMPLES</span></span>

### <span data-ttu-id="588bb-115">Exemple 1 : récupération de tous les packages installés</span><span class="sxs-lookup"><span data-stu-id="588bb-115">Example 1: Get all installed packages</span></span>

<span data-ttu-id="588bb-116">L' `Get-Package` applet de commande obtient tous les packages qui sont installés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="588bb-116">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="588bb-117">Exemple 2 : obtenir les packages qui sont installés sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="588bb-117">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="588bb-118">Cette commande obtient la liste des packages qui ont été installés par **PackageManagement** sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="588bb-118">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="588bb-119">Cette commande vous invite à fournir le mot de passe de l’utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="588bb-119">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="588bb-120">`Invoke-Command` utilise le paramètre **ComputerName** pour spécifier un ordinateur distant, **SERVEUR01**.</span><span class="sxs-lookup"><span data-stu-id="588bb-120">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01**.</span></span> <span data-ttu-id="588bb-121">Le paramètre **Credential** spécifie un domaine et un nom d’utilisateur disposant des autorisations nécessaires pour exécuter des commandes sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="588bb-121">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="588bb-122">Le paramètre **scriptblock** exécute l' `Get-Package` applet de commande sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="588bb-122">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="588bb-123">Exemple 3 : obtenir des packages pour un fournisseur spécifié</span><span class="sxs-lookup"><span data-stu-id="588bb-123">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="588bb-124">Cette commande obtient les packages logiciels installés sur l’ordinateur local à partir d’un fournisseur spécifique.</span><span class="sxs-lookup"><span data-stu-id="588bb-124">This command gets software packages installed on the local computer from a specific provider.</span></span>

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="588bb-125">`Get-Package` utilise le paramètre **providerName** pour spécifier un fournisseur spécifique, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="588bb-125">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet**.</span></span>
<span data-ttu-id="588bb-126">Le paramètre **All-versions** affiche chaque version installée.</span><span class="sxs-lookup"><span data-stu-id="588bb-126">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="588bb-127">Exemple 4 : obtenir une version exacte d’un package spécifique</span><span class="sxs-lookup"><span data-stu-id="588bb-127">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="588bb-128">Cette commande obtient une version spécifique d’un package installé.</span><span class="sxs-lookup"><span data-stu-id="588bb-128">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="588bb-129">Il est possible d’installer plusieurs versions d’un package.</span><span class="sxs-lookup"><span data-stu-id="588bb-129">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="588bb-130">`Get-Package` utilise le paramètre **Name** pour spécifier le nom du package, **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="588bb-130">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement**.</span></span> <span data-ttu-id="588bb-131">Le paramètre **providerName** spécifie le fournisseur, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="588bb-131">The **ProviderName** parameter specifies the provider, **PowerShellGet**.</span></span> <span data-ttu-id="588bb-132">Le paramètre **Required-version** spécifie une version installée.</span><span class="sxs-lookup"><span data-stu-id="588bb-132">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="588bb-133">Exemple 5 : désinstaller un package</span><span class="sxs-lookup"><span data-stu-id="588bb-133">Example 5: Uninstall a package</span></span>

<span data-ttu-id="588bb-134">Cet exemple obtient des informations sur le package, puis désinstalle le package.</span><span class="sxs-lookup"><span data-stu-id="588bb-134">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="588bb-135">`Get-Package` utilise le paramètre **Name** pour spécifier le nom du package, **Posh-git**.</span><span class="sxs-lookup"><span data-stu-id="588bb-135">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git**.</span></span> <span data-ttu-id="588bb-136">Le paramètre **RequiredVersion** est une version spécifique du package.</span><span class="sxs-lookup"><span data-stu-id="588bb-136">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="588bb-137">L’objet est envoyé dans le pipeline à l’applet de commande `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="588bb-137">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="588bb-138">`Uninstall-Package` supprime le package.</span><span class="sxs-lookup"><span data-stu-id="588bb-138">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="588bb-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="588bb-139">PARAMETERS</span></span>

### <span data-ttu-id="588bb-140">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="588bb-140">-AllowClobber</span></span>

<span data-ttu-id="588bb-141">Remplace les messages d’avertissement relatifs aux conflits avec les commandes existantes.</span><span class="sxs-lookup"><span data-stu-id="588bb-141">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="588bb-142">Remplace les commandes existantes qui portent le même nom que les commandes installées par un module.</span><span class="sxs-lookup"><span data-stu-id="588bb-142">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="588bb-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="588bb-144">Comprend les packages marqués comme version préliminaire dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="588bb-144">Includes packages marked as a prerelease in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="588bb-145">-AllVersions</span></span>

<span data-ttu-id="588bb-146">Indique que `Get-Package` retourne toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="588bb-146">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="588bb-147">Par défaut, `Get-Package` retourne uniquement la version disponible la plus récente.</span><span class="sxs-lookup"><span data-stu-id="588bb-147">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="588bb-148">-Destination</span><span class="sxs-lookup"><span data-stu-id="588bb-148">-Destination</span></span>

<span data-ttu-id="588bb-149">Spécifie le chemin d’accès à un répertoire qui contient des fichiers de package extraits.</span><span class="sxs-lookup"><span data-stu-id="588bb-149">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="588bb-150">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="588bb-150">-ExcludeVersion</span></span>

<span data-ttu-id="588bb-151">Basculez pour exclure le numéro de version dans le chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="588bb-151">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="588bb-152">-Force</span><span class="sxs-lookup"><span data-stu-id="588bb-152">-Force</span></span>

<span data-ttu-id="588bb-153">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="588bb-153">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="588bb-154">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="588bb-154">-ForceBootstrap</span></span>

<span data-ttu-id="588bb-155">Indique que `Get-Package` impose l’installation automatique du fournisseur de package par **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="588bb-155">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="588bb-156">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="588bb-156">-InstallUpdate</span></span>

<span data-ttu-id="588bb-157">Indique que cette applet de commande installe les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="588bb-157">Indicates that this cmdlet installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-158">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="588bb-158">-MaximumVersion</span></span>

<span data-ttu-id="588bb-159">Spécifie la version de package maximale que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="588bb-159">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="588bb-160">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="588bb-160">-MinimumVersion</span></span>

<span data-ttu-id="588bb-161">Spécifie la version minimale du package que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="588bb-161">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="588bb-162">Si une version plus récente est disponible, cette version est retournée.</span><span class="sxs-lookup"><span data-stu-id="588bb-162">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="588bb-163">-Name</span><span class="sxs-lookup"><span data-stu-id="588bb-163">-Name</span></span>

<span data-ttu-id="588bb-164">Spécifie un ou plusieurs noms de packages, ou des noms de package avec des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="588bb-164">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="588bb-165">Séparez plusieurs noms de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="588bb-165">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="588bb-166">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="588bb-166">-NoPathUpdate</span></span>

<span data-ttu-id="588bb-167">**NoPathUpdate** s’applique uniquement à l’applet de commande `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="588bb-167">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="588bb-168">**NoPathUpdate** est un paramètre dynamique ajouté par le fournisseur et n’est pas pris en charge par `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="588bb-168">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-169">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="588bb-169">-PackageManagementProvider</span></span>

<span data-ttu-id="588bb-170">Spécifie le nom d’un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="588bb-170">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="588bb-171">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="588bb-171">-ProviderName</span></span>

<span data-ttu-id="588bb-172">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="588bb-172">Specifies one or more package provider names.</span></span> <span data-ttu-id="588bb-173">Séparez les noms de plusieurs fournisseurs de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="588bb-173">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="588bb-174">Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.</span><span class="sxs-lookup"><span data-stu-id="588bb-174">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="588bb-175">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="588bb-175">-RequiredVersion</span></span>

<span data-ttu-id="588bb-176">Spécifie la version exacte du package à rechercher.</span><span class="sxs-lookup"><span data-stu-id="588bb-176">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="588bb-177">-Étendue</span><span class="sxs-lookup"><span data-stu-id="588bb-177">-Scope</span></span>

<span data-ttu-id="588bb-178">Spécifie l’étendue de recherche pour le package.</span><span class="sxs-lookup"><span data-stu-id="588bb-178">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet, PowerShellGet
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-179">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="588bb-179">-SkipDependencies</span></span>

<span data-ttu-id="588bb-180">Commutateur qui spécifie d’ignorer la recherche de dépendances de package.</span><span class="sxs-lookup"><span data-stu-id="588bb-180">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="588bb-181">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="588bb-181">-SkipPublisherCheck</span></span>

<span data-ttu-id="588bb-182">Vous permet d’obtenir une version de package plus récente que la version installée.</span><span class="sxs-lookup"><span data-stu-id="588bb-182">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="588bb-183">Par exemple, un package installé signé numériquement par un éditeur approuvé, mais pour lequel une nouvelle version n’est pas signée numériquement.</span><span class="sxs-lookup"><span data-stu-id="588bb-183">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-184">-Type</span><span class="sxs-lookup"><span data-stu-id="588bb-184">-Type</span></span>

<span data-ttu-id="588bb-185">Spécifie s’il faut rechercher des packages à l’aide d’un module, d’un script ou de l’un ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="588bb-185">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-186">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="588bb-186">-AdditionalArguments</span></span>

<span data-ttu-id="588bb-187">Spécifie des arguments supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="588bb-187">Specifies additional arguments.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-188">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="588bb-188">-IncludeSystemComponent</span></span>

<span data-ttu-id="588bb-189">Indique que cette applet de commande comprend des composants système dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="588bb-189">Indicates that this cmdlet includes system components in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-190">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="588bb-190">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="588bb-191">Indique que cette applet de commande comprend les Windows Installer dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="588bb-191">Indicates that this cmdlet includes the Windows Installer in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="588bb-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="588bb-192">CommonParameters</span></span>

<span data-ttu-id="588bb-193">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="588bb-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="588bb-194">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="588bb-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="588bb-195">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="588bb-195">INPUTS</span></span>

## <span data-ttu-id="588bb-196">SORTIES</span><span class="sxs-lookup"><span data-stu-id="588bb-196">OUTPUTS</span></span>

### <span data-ttu-id="588bb-197">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="588bb-197">SoftwareIdentity[]</span></span>

## <span data-ttu-id="588bb-198">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="588bb-198">NOTES</span></span>

<span data-ttu-id="588bb-199">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="588bb-199">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="588bb-200">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="588bb-200">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="588bb-201">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="588bb-201">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="588bb-202">Par exemple, `Get-Package` a le paramètre **PowerShellGet** défini qui inclut `-NoPathUpdate` , `AllowClobber` et `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="588bb-202">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="588bb-203">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="588bb-203">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="588bb-204">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="588bb-204">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="588bb-205">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="588bb-205">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="588bb-206">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="588bb-206">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="588bb-207">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="588bb-207">RELATED LINKS</span></span>

[<span data-ttu-id="588bb-208">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="588bb-208">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="588bb-209">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="588bb-209">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="588bb-210">Find-Package</span><span class="sxs-lookup"><span data-stu-id="588bb-210">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="588bb-211">Get-Help</span><span class="sxs-lookup"><span data-stu-id="588bb-211">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="588bb-212">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="588bb-212">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="588bb-213">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="588bb-213">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="588bb-214">Install-Package</span><span class="sxs-lookup"><span data-stu-id="588bb-214">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="588bb-215">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="588bb-215">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="588bb-216">Save-Package</span><span class="sxs-lookup"><span data-stu-id="588bb-216">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="588bb-217">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="588bb-217">Uninstall-Package</span></span>](Uninstall-Package.md)
