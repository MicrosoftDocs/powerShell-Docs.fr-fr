---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: 0b821f96606215d5d961329ebc69a1e5d3260763
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203709"
---
# <span data-ttu-id="a80db-103">Get-Package</span><span class="sxs-lookup"><span data-stu-id="a80db-103">Get-Package</span></span>

## <span data-ttu-id="a80db-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a80db-104">SYNOPSIS</span></span>
<span data-ttu-id="a80db-105">Retourne une liste de tous les packages logiciels qui ont été installés avec **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="a80db-105">Returns a list of all software packages that were installed with **PackageManagement** .</span></span>

## <span data-ttu-id="a80db-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a80db-106">SYNTAX</span></span>

### <span data-ttu-id="a80db-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="a80db-107">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="a80db-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a80db-108">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="a80db-109">Description</span><span class="sxs-lookup"><span data-stu-id="a80db-109">DESCRIPTION</span></span>

<span data-ttu-id="a80db-110">L' `Get-Package` applet de commande renvoie la liste de tous les packages logiciels sur l’ordinateur local qui ont été installés avec **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="a80db-110">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement** .</span></span> <span data-ttu-id="a80db-111">Vous pouvez exécuter `Get-Package` sur des ordinateurs distants en l’exécutant dans le cadre d’une `Invoke-Command` commande ou d’un `Enter-PSSession` script.</span><span class="sxs-lookup"><span data-stu-id="a80db-111">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="a80db-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a80db-112">EXAMPLES</span></span>

### <span data-ttu-id="a80db-113">Exemple 1 : récupération de tous les packages installés</span><span class="sxs-lookup"><span data-stu-id="a80db-113">Example 1: Get all installed packages</span></span>

<span data-ttu-id="a80db-114">L' `Get-Package` applet de commande obtient tous les packages qui sont installés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a80db-114">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="a80db-115">Exemple 2 : obtenir les packages qui sont installés sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="a80db-115">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="a80db-116">Cette commande obtient la liste des packages qui ont été installés par **PackageManagement** sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a80db-116">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="a80db-117">Cette commande vous invite à fournir le mot de passe de l’utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="a80db-117">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="a80db-118">`Invoke-Command` utilise le paramètre **ComputerName** pour spécifier un ordinateur distant, **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="a80db-118">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01** .</span></span> <span data-ttu-id="a80db-119">Le paramètre **Credential** spécifie un domaine et un nom d’utilisateur disposant des autorisations nécessaires pour exécuter des commandes sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a80db-119">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="a80db-120">Le paramètre **scriptblock** exécute l' `Get-Package` applet de commande sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a80db-120">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="a80db-121">Exemple 3 : obtenir des packages pour un fournisseur spécifié</span><span class="sxs-lookup"><span data-stu-id="a80db-121">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="a80db-122">Cette commande obtient les packages logiciels installés sur l’ordinateur local à partir d’un fournisseur spécifique.</span><span class="sxs-lookup"><span data-stu-id="a80db-122">This command gets software packages installed on the local computer from a specific provider.</span></span>

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

<span data-ttu-id="a80db-123">`Get-Package` utilise le paramètre **providerName** pour spécifier un fournisseur spécifique, **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="a80db-123">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet** .</span></span>
<span data-ttu-id="a80db-124">Le paramètre **All-versions** affiche chaque version installée.</span><span class="sxs-lookup"><span data-stu-id="a80db-124">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="a80db-125">Exemple 4 : obtenir une version exacte d’un package spécifique</span><span class="sxs-lookup"><span data-stu-id="a80db-125">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="a80db-126">Cette commande obtient une version spécifique d’un package installé.</span><span class="sxs-lookup"><span data-stu-id="a80db-126">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="a80db-127">Il est possible d’installer plusieurs versions d’un package.</span><span class="sxs-lookup"><span data-stu-id="a80db-127">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="a80db-128">`Get-Package` utilise le paramètre **Name** pour spécifier le nom du package, **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="a80db-128">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement** .</span></span> <span data-ttu-id="a80db-129">Le paramètre **providerName** spécifie le fournisseur, **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="a80db-129">The **ProviderName** parameter specifies the provider, **PowerShellGet** .</span></span> <span data-ttu-id="a80db-130">Le paramètre **Required-version** spécifie une version installée.</span><span class="sxs-lookup"><span data-stu-id="a80db-130">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="a80db-131">Exemple 5 : désinstaller un package</span><span class="sxs-lookup"><span data-stu-id="a80db-131">Example 5: Uninstall a package</span></span>

<span data-ttu-id="a80db-132">Cet exemple obtient des informations sur le package, puis désinstalle le package.</span><span class="sxs-lookup"><span data-stu-id="a80db-132">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="a80db-133">`Get-Package` utilise le paramètre **Name** pour spécifier le nom du package, **Posh-git** .</span><span class="sxs-lookup"><span data-stu-id="a80db-133">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git** .</span></span> <span data-ttu-id="a80db-134">Le paramètre **RequiredVersion** est une version spécifique du package.</span><span class="sxs-lookup"><span data-stu-id="a80db-134">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="a80db-135">L’objet est envoyé dans le pipeline à l’applet de commande `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="a80db-135">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="a80db-136">`Uninstall-Package` supprime le package.</span><span class="sxs-lookup"><span data-stu-id="a80db-136">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="a80db-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a80db-137">PARAMETERS</span></span>

### <span data-ttu-id="a80db-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="a80db-138">-AllowClobber</span></span>

<span data-ttu-id="a80db-139">Remplace les messages d’avertissement relatifs aux conflits avec les commandes existantes.</span><span class="sxs-lookup"><span data-stu-id="a80db-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="a80db-140">Remplace les commandes existantes qui portent le même nom que les commandes installées par un module.</span><span class="sxs-lookup"><span data-stu-id="a80db-140">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

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

### <span data-ttu-id="a80db-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="a80db-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="a80db-142">Comprend les packages marqués comme version préliminaire dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="a80db-142">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="a80db-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="a80db-143">-AllVersions</span></span>

<span data-ttu-id="a80db-144">Indique que `Get-Package` retourne toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="a80db-144">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="a80db-145">Par défaut, `Get-Package` retourne uniquement la version disponible la plus récente.</span><span class="sxs-lookup"><span data-stu-id="a80db-145">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="a80db-146">-Destination</span><span class="sxs-lookup"><span data-stu-id="a80db-146">-Destination</span></span>

<span data-ttu-id="a80db-147">Spécifie le chemin d’accès à un répertoire qui contient des fichiers de package extraits.</span><span class="sxs-lookup"><span data-stu-id="a80db-147">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="a80db-148">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="a80db-148">-ExcludeVersion</span></span>

<span data-ttu-id="a80db-149">Basculez pour exclure le numéro de version dans le chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="a80db-149">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="a80db-150">-Force</span><span class="sxs-lookup"><span data-stu-id="a80db-150">-Force</span></span>

<span data-ttu-id="a80db-151">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a80db-151">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a80db-152">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="a80db-152">-ForceBootstrap</span></span>

<span data-ttu-id="a80db-153">Indique que `Get-Package` impose l’installation automatique du fournisseur de package par **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="a80db-153">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="a80db-154">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="a80db-154">-InstallUpdate</span></span>

<span data-ttu-id="a80db-155">Indique que cette applet de commande installe les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a80db-155">Indicates that this cmdlet installs updates.</span></span>

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

### <span data-ttu-id="a80db-156">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a80db-156">-MaximumVersion</span></span>

<span data-ttu-id="a80db-157">Spécifie la version de package maximale que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="a80db-157">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="a80db-158">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a80db-158">-MinimumVersion</span></span>

<span data-ttu-id="a80db-159">Spécifie la version minimale du package que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="a80db-159">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="a80db-160">Si une version plus récente est disponible, cette version est retournée.</span><span class="sxs-lookup"><span data-stu-id="a80db-160">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="a80db-161">-Name</span><span class="sxs-lookup"><span data-stu-id="a80db-161">-Name</span></span>

<span data-ttu-id="a80db-162">Spécifie un ou plusieurs noms de packages, ou des noms de package avec des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="a80db-162">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="a80db-163">Séparez plusieurs noms de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="a80db-163">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="a80db-164">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="a80db-164">-NoPathUpdate</span></span>

<span data-ttu-id="a80db-165">**NoPathUpdate** s’applique uniquement à l’applet de commande `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="a80db-165">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="a80db-166">**NoPathUpdate** est un paramètre dynamique ajouté par le fournisseur et n’est pas pris en charge par `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="a80db-166">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

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

### <span data-ttu-id="a80db-167">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="a80db-167">-PackageManagementProvider</span></span>

<span data-ttu-id="a80db-168">Spécifie le nom d’un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="a80db-168">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="a80db-169">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="a80db-169">-ProviderName</span></span>

<span data-ttu-id="a80db-170">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="a80db-170">Specifies one or more package provider names.</span></span> <span data-ttu-id="a80db-171">Séparez les noms de plusieurs fournisseurs de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="a80db-171">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="a80db-172">Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.</span><span class="sxs-lookup"><span data-stu-id="a80db-172">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="a80db-173">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a80db-173">-RequiredVersion</span></span>

<span data-ttu-id="a80db-174">Spécifie la version exacte du package à rechercher.</span><span class="sxs-lookup"><span data-stu-id="a80db-174">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="a80db-175">-Étendue</span><span class="sxs-lookup"><span data-stu-id="a80db-175">-Scope</span></span>

<span data-ttu-id="a80db-176">Spécifie l’étendue de recherche pour le package.</span><span class="sxs-lookup"><span data-stu-id="a80db-176">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a80db-177">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="a80db-177">-SkipDependencies</span></span>

<span data-ttu-id="a80db-178">Commutateur qui spécifie d’ignorer la recherche de dépendances de package.</span><span class="sxs-lookup"><span data-stu-id="a80db-178">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="a80db-179">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="a80db-179">-SkipPublisherCheck</span></span>

<span data-ttu-id="a80db-180">Vous permet d’obtenir une version de package plus récente que la version installée.</span><span class="sxs-lookup"><span data-stu-id="a80db-180">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="a80db-181">Par exemple, un package installé signé numériquement par un éditeur approuvé, mais pour lequel une nouvelle version n’est pas signée numériquement.</span><span class="sxs-lookup"><span data-stu-id="a80db-181">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="a80db-182">-Type</span><span class="sxs-lookup"><span data-stu-id="a80db-182">-Type</span></span>

<span data-ttu-id="a80db-183">Spécifie s’il faut rechercher des packages à l’aide d’un module, d’un script ou de l’un ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="a80db-183">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="a80db-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a80db-184">CommonParameters</span></span>

<span data-ttu-id="a80db-185">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a80db-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a80db-186">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a80db-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a80db-187">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a80db-187">INPUTS</span></span>

## <span data-ttu-id="a80db-188">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a80db-188">OUTPUTS</span></span>

### <span data-ttu-id="a80db-189">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="a80db-189">SoftwareIdentity[]</span></span>

## <span data-ttu-id="a80db-190">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a80db-190">NOTES</span></span>

<span data-ttu-id="a80db-191">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a80db-191">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="a80db-192">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="a80db-192">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="a80db-193">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a80db-193">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="a80db-194">Par exemple, `Get-Package` a le paramètre **PowerShellGet** défini qui inclut `-NoPathUpdate` , `AllowClobber` et `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="a80db-194">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="a80db-195">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a80db-195">RELATED LINKS</span></span>

[<span data-ttu-id="a80db-196">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="a80db-196">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="a80db-197">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="a80db-197">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="a80db-198">Find-Package</span><span class="sxs-lookup"><span data-stu-id="a80db-198">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="a80db-199">Get-Help</span><span class="sxs-lookup"><span data-stu-id="a80db-199">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="a80db-200">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a80db-200">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="a80db-201">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a80db-201">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="a80db-202">Install-Package</span><span class="sxs-lookup"><span data-stu-id="a80db-202">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="a80db-203">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a80db-203">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="a80db-204">Save-Package</span><span class="sxs-lookup"><span data-stu-id="a80db-204">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="a80db-205">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="a80db-205">Uninstall-Package</span></span>](Uninstall-Package.md)
