---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 7a99c4c00f809c2ec418618b2c1322d2552d1120
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204181"
---
# <span data-ttu-id="4a825-103">Install-Package</span><span class="sxs-lookup"><span data-stu-id="4a825-103">Install-Package</span></span>

## <span data-ttu-id="4a825-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4a825-104">SYNOPSIS</span></span>
<span data-ttu-id="4a825-105">Installe un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="4a825-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="4a825-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a825-106">SYNTAX</span></span>

### <span data-ttu-id="4a825-107">PackageBySearch (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4a825-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="4a825-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="4a825-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="4a825-109">NuGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="4a825-109">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="4a825-110">NuGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="4a825-110">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="4a825-111">PowerShellGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="4a825-111">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="4a825-112">PowerShellGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="4a825-112">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="4a825-113">Description</span><span class="sxs-lookup"><span data-stu-id="4a825-113">DESCRIPTION</span></span>

<span data-ttu-id="4a825-114">L' `Install-Package` applet de commande installe un ou plusieurs packages logiciels sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4a825-114">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="4a825-115">Si vous avez plusieurs sources logicielles, utilisez `Get-PackageProvider` et `Get-PackageSource` pour afficher des détails sur vos fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="4a825-115">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="4a825-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4a825-116">EXAMPLES</span></span>

### <span data-ttu-id="4a825-117">Exemple 1 : installer un package par nom de package</span><span class="sxs-lookup"><span data-stu-id="4a825-117">Example 1: Install a package by package name</span></span>

<span data-ttu-id="4a825-118">L' `Install-Package` applet de commande installe un package logiciel et ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="4a825-118">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="4a825-119">`Install-Package` utilise des paramètres pour spécifier le **nom** et la **source** des packages.</span><span class="sxs-lookup"><span data-stu-id="4a825-119">`Install-Package` uses parameters to specify the packages **Name** and **Source** .</span></span> <span data-ttu-id="4a825-120">Le paramètre **Credential** utilise un compte d’utilisateur de domaine disposant des autorisations pour installer des packages.</span><span class="sxs-lookup"><span data-stu-id="4a825-120">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="4a825-121">La commande vous invite à entrer le mot de passe du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4a825-121">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="4a825-122">Exemple 2 : utiliser Find-Package pour installer un package</span><span class="sxs-lookup"><span data-stu-id="4a825-122">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="4a825-123">Dans cet exemple, l’objet retourné par `Find-Package` est envoyé vers le pipeline et installé par `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="4a825-123">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="4a825-124">`Find-Package` utilise les paramètres **Name** et **source** pour localiser un package.</span><span class="sxs-lookup"><span data-stu-id="4a825-124">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="4a825-125">L’objet est envoyé dans le pipeline et `Install-Package` installe le package sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4a825-125">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="4a825-126">Exemple 3 : installer des packages en spécifiant une plage de versions</span><span class="sxs-lookup"><span data-stu-id="4a825-126">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="4a825-127">`Install-Package` utilise les paramètres **MinimumVersion** et **MaximumVersion** pour spécifier une plage de versions logicielles.</span><span class="sxs-lookup"><span data-stu-id="4a825-127">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="4a825-128">`Install-Package` utilise le **nom** et les paramètres de la **source** pour rechercher un package.</span><span class="sxs-lookup"><span data-stu-id="4a825-128">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="4a825-129">Les paramètres **MinimumVersion** et **MaximumVersion** spécifient une plage de versions logicielles.</span><span class="sxs-lookup"><span data-stu-id="4a825-129">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="4a825-130">La version la plus élevée de la plage est installée.</span><span class="sxs-lookup"><span data-stu-id="4a825-130">The highest version in the range is installed.</span></span>

## <span data-ttu-id="4a825-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4a825-131">PARAMETERS</span></span>

### <span data-ttu-id="4a825-132">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4a825-132">-AcceptLicense</span></span>

 <span data-ttu-id="4a825-133">**AcceptLicense** accepte automatiquement le contrat de licence lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="4a825-133">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-134">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="4a825-134">-AllowClobber</span></span>

<span data-ttu-id="4a825-135">Remplace les messages d’avertissement relatifs aux conflits avec les commandes existantes.</span><span class="sxs-lookup"><span data-stu-id="4a825-135">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="4a825-136">Remplace les commandes existantes qui portent le même nom que les commandes en cours d’installation.</span><span class="sxs-lookup"><span data-stu-id="4a825-136">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-137">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="4a825-137">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="4a825-138">Autorise l’installation de packages marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="4a825-138">Allows the installation of packages marked as prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-139">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="4a825-139">-AllVersions</span></span>

<span data-ttu-id="4a825-140">`Install-Package` installe toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="4a825-140">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="4a825-141">Par défaut, seule la version la plus récente est installée.</span><span class="sxs-lookup"><span data-stu-id="4a825-141">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="4a825-142">-Command</span><span class="sxs-lookup"><span data-stu-id="4a825-142">-Command</span></span>

<span data-ttu-id="4a825-143">Spécifie une ou plusieurs commandes qui `Install-Package` effectuent des recherches.</span><span class="sxs-lookup"><span data-stu-id="4a825-143">Specifies one or more commands that `Install-Package` searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-144">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="4a825-144">-ConfigFile</span></span>

<span data-ttu-id="4a825-145">Spécifie un chemin d’accès qui contient un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="4a825-145">Specifies a path that contains a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-146">-Contient</span><span class="sxs-lookup"><span data-stu-id="4a825-146">-Contains</span></span>

<span data-ttu-id="4a825-147">`Install-Package` obtient des objets si le paramètre **Contains** spécifie une valeur qui correspond à l’une des valeurs de propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4a825-147">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="4a825-148">-Credential</span></span>

<span data-ttu-id="4a825-149">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’ordinateur et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="4a825-149">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="4a825-150">Tapez un nom d’utilisateur, tel que **User01** , **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="4a825-150">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="4a825-151">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="4a825-151">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="4a825-152">Lorsque le paramètre **Credential** n’est pas spécifié, `Install-Package` utilise l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="4a825-152">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="4a825-153">-Destination</span><span class="sxs-lookup"><span data-stu-id="4a825-153">-Destination</span></span>

<span data-ttu-id="4a825-154">Spécifie le chemin d’accès à un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4a825-154">Specifies a path to an input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-155">-DscResource</span><span class="sxs-lookup"><span data-stu-id="4a825-155">-DscResource</span></span>

<span data-ttu-id="4a825-156">Spécifie une ou plusieurs ressources de configuration d’état souhaité (DSC) sur lesquelles porte la recherche `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="4a825-156">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="4a825-157">Utilisez l' `Find-DscResource` applet de commande pour rechercher des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="4a825-157">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-158">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="4a825-158">-ExcludeVersion</span></span>

<span data-ttu-id="4a825-159">Basculez pour exclure le numéro de version dans le chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="4a825-159">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-160">-Filter</span><span class="sxs-lookup"><span data-stu-id="4a825-160">-Filter</span></span>

<span data-ttu-id="4a825-161">Spécifie les termes à rechercher dans les propriétés **Name** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="4a825-161">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-162">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="4a825-162">-FilterOnTag</span></span>

<span data-ttu-id="4a825-163">Spécifie une balise qui filtre les résultats et exclut les résultats qui ne contiennent pas la balise spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4a825-163">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-164">-Force</span><span class="sxs-lookup"><span data-stu-id="4a825-164">-Force</span></span>

<span data-ttu-id="4a825-165">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4a825-165">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="4a825-166">Remplace les restrictions qui empêchent `Install-Package` la réussie, à l’exception de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="4a825-166">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="4a825-167">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="4a825-167">-ForceBootstrap</span></span>

<span data-ttu-id="4a825-168">Force **PackageManagement** à installer automatiquement le fournisseur de package pour le package spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a825-168">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="4a825-169">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="4a825-169">-Headers</span></span>

<span data-ttu-id="4a825-170">Spécifie les en-têtes de package.</span><span class="sxs-lookup"><span data-stu-id="4a825-170">Specifies the package headers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-171">-Comprend</span><span class="sxs-lookup"><span data-stu-id="4a825-171">-Includes</span></span>

<span data-ttu-id="4a825-172">Spécifie si `Install-Package` tous les types de packages doivent être recherchés.</span><span class="sxs-lookup"><span data-stu-id="4a825-172">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="4a825-173">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a825-173">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4a825-174">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="4a825-174">Cmdlet</span></span>
- <span data-ttu-id="4a825-175">DscResource</span><span class="sxs-lookup"><span data-stu-id="4a825-175">DscResource</span></span>
- <span data-ttu-id="4a825-176">Fonction</span><span class="sxs-lookup"><span data-stu-id="4a825-176">Function</span></span>
- <span data-ttu-id="4a825-177">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="4a825-177">RoleCapability</span></span>
- <span data-ttu-id="4a825-178">Workflow</span><span class="sxs-lookup"><span data-stu-id="4a825-178">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-179">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4a825-179">-InputObject</span></span>

<span data-ttu-id="4a825-180">Accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="4a825-180">Accepts pipeline input.</span></span> <span data-ttu-id="4a825-181">Spécifie un package à l’aide du type **SoftwareIdentity** du package.</span><span class="sxs-lookup"><span data-stu-id="4a825-181">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="4a825-182">`Find-Package` génère un objet **SoftwareIdentity** .</span><span class="sxs-lookup"><span data-stu-id="4a825-182">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="4a825-183">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="4a825-183">-InstallUpdate</span></span>

<span data-ttu-id="4a825-184">Indique que `Install-Package` installe les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="4a825-184">Indicates that `Install-Package` installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-185">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="4a825-185">-MaximumVersion</span></span>

<span data-ttu-id="4a825-186">Spécifie la version de package maximale autorisée que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="4a825-186">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="4a825-187">Si vous ne spécifiez pas ce paramètre, `Install-Package` installe la version la plus récente du package.</span><span class="sxs-lookup"><span data-stu-id="4a825-187">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="4a825-188">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="4a825-188">-MinimumVersion</span></span>

<span data-ttu-id="4a825-189">Spécifie la version de package minimale autorisée que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="4a825-189">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="4a825-190">Si vous n’ajoutez pas ce paramètre, `Install-Package` installe la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="4a825-190">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="4a825-191">-Name</span><span class="sxs-lookup"><span data-stu-id="4a825-191">-Name</span></span>

<span data-ttu-id="4a825-192">Spécifie un ou plusieurs noms de packages.</span><span class="sxs-lookup"><span data-stu-id="4a825-192">Specifies one or more package names.</span></span> <span data-ttu-id="4a825-193">Plusieurs noms de packages doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4a825-193">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="4a825-194">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="4a825-194">-NoPathUpdate</span></span>

<span data-ttu-id="4a825-195">**NoPathUpdate** s’applique uniquement à l’applet de commande `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="4a825-195">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="4a825-196">**NoPathUpdate** est un paramètre dynamique ajouté par le fournisseur et n’est pas pris en charge par `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="4a825-196">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-197">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="4a825-197">-PackageManagementProvider</span></span>

<span data-ttu-id="4a825-198">Spécifie le nom du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="4a825-198">Specifies the name of the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-199">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="4a825-199">-ProviderName</span></span>

<span data-ttu-id="4a825-200">Spécifie un ou plusieurs noms de fournisseurs de packages dans lesquels étendre votre recherche de package.</span><span class="sxs-lookup"><span data-stu-id="4a825-200">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="4a825-201">Vous obtenez les noms des fournisseurs de package en exécutant l’applet de commande `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="4a825-201">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="4a825-202">-Proxy</span><span class="sxs-lookup"><span data-stu-id="4a825-202">-Proxy</span></span>

<span data-ttu-id="4a825-203">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="4a825-203">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="4a825-204">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4a825-204">-ProxyCredential</span></span>

<span data-ttu-id="4a825-205">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="4a825-205">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="4a825-206">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="4a825-206">-PublishLocation</span></span>

<span data-ttu-id="4a825-207">Spécifie le chemin d’accès à l’emplacement publié d’un package.</span><span class="sxs-lookup"><span data-stu-id="4a825-207">Specifies the path to a package's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-208">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="4a825-208">-RequiredVersion</span></span>

<span data-ttu-id="4a825-209">Spécifie la version exacte du package que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="4a825-209">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="4a825-210">Si vous n’ajoutez pas ce paramètre, `Install-Package` installe la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="4a825-210">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="4a825-211">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="4a825-211">-RoleCapability</span></span>

<span data-ttu-id="4a825-212">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="4a825-212">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-213">-Étendue</span><span class="sxs-lookup"><span data-stu-id="4a825-213">-Scope</span></span>

<span data-ttu-id="4a825-214">Spécifie l’étendue pour laquelle installer le package.</span><span class="sxs-lookup"><span data-stu-id="4a825-214">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="4a825-215">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a825-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4a825-216">Utilisateur en cours</span><span class="sxs-lookup"><span data-stu-id="4a825-216">CurrentUser</span></span>
- <span data-ttu-id="4a825-217">AllUsers</span><span class="sxs-lookup"><span data-stu-id="4a825-217">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-218">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="4a825-218">-ScriptPublishLocation</span></span>

<span data-ttu-id="4a825-219">Spécifie le chemin d’accès à l’emplacement de publication d’un script.</span><span class="sxs-lookup"><span data-stu-id="4a825-219">Specifies the path to a script's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-220">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="4a825-220">-ScriptSourceLocation</span></span>

<span data-ttu-id="4a825-221">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="4a825-221">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-222">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="4a825-222">-SkipDependencies</span></span>

<span data-ttu-id="4a825-223">Ignore l’installation des dépendances logicielles.</span><span class="sxs-lookup"><span data-stu-id="4a825-223">Skips the installation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-224">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="4a825-224">-SkipPublisherCheck</span></span>

<span data-ttu-id="4a825-225">Vous permet d’obtenir une version de package plus récente que la version installée.</span><span class="sxs-lookup"><span data-stu-id="4a825-225">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="4a825-226">Par exemple, un package installé signé numériquement par un éditeur approuvé, mais pour lequel une nouvelle version n’est pas signée numériquement.</span><span class="sxs-lookup"><span data-stu-id="4a825-226">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-227">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="4a825-227">-SkipValidate</span></span>

<span data-ttu-id="4a825-228">Commutateur qui ignore la validation des informations d’identification d’un package.</span><span class="sxs-lookup"><span data-stu-id="4a825-228">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-229">-Source</span><span class="sxs-lookup"><span data-stu-id="4a825-229">-Source</span></span>

<span data-ttu-id="4a825-230">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="4a825-230">Specifies one or more package sources.</span></span> <span data-ttu-id="4a825-231">Plusieurs noms de sources de packages doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4a825-231">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="4a825-232">Vous pouvez récupérer les noms des sources du package en exécutant l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="4a825-232">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="4a825-233">-Tag</span><span class="sxs-lookup"><span data-stu-id="4a825-233">-Tag</span></span>

<span data-ttu-id="4a825-234">Spécifie une ou plusieurs chaînes à rechercher dans les métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="4a825-234">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-235">-Type</span><span class="sxs-lookup"><span data-stu-id="4a825-235">-Type</span></span>

<span data-ttu-id="4a825-236">Spécifie s’il faut rechercher des packages avec un module, un script ou les deux.</span><span class="sxs-lookup"><span data-stu-id="4a825-236">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="4a825-237">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a825-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4a825-238">Module</span><span class="sxs-lookup"><span data-stu-id="4a825-238">Module</span></span>
- <span data-ttu-id="4a825-239">Script</span><span class="sxs-lookup"><span data-stu-id="4a825-239">Script</span></span>
- <span data-ttu-id="4a825-240">Tous</span><span class="sxs-lookup"><span data-stu-id="4a825-240">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a825-241">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4a825-241">-Confirm</span></span>

<span data-ttu-id="4a825-242">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4a825-242">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4a825-243">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4a825-243">-WhatIf</span></span>

<span data-ttu-id="4a825-244">Montre ce qui se passe si l' `Install-Package` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="4a825-244">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="4a825-245">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4a825-245">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4a825-246">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a825-246">CommonParameters</span></span>

<span data-ttu-id="4a825-247">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4a825-247">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a825-248">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4a825-248">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a825-249">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4a825-249">INPUTS</span></span>

### <span data-ttu-id="4a825-250">`Install-Package` accepte l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="4a825-250">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="4a825-251">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4a825-251">OUTPUTS</span></span>

### <span data-ttu-id="4a825-252">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="4a825-252">SoftwareIdentity[]</span></span>

## <span data-ttu-id="4a825-253">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4a825-253">NOTES</span></span>

<span data-ttu-id="4a825-254">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4a825-254">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="4a825-255">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="4a825-255">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="4a825-256">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4a825-256">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="4a825-257">Par exemple, `Install-Package` a le paramètre **PowerShellGet** défini qui inclut `-NoPathUpdate` , `AllowClobber` et `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="4a825-257">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="4a825-258">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4a825-258">RELATED LINKS</span></span>

[<span data-ttu-id="4a825-259">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="4a825-259">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="4a825-260">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="4a825-260">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="4a825-261">Get-Help</span><span class="sxs-lookup"><span data-stu-id="4a825-261">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="4a825-262">Get-Package</span><span class="sxs-lookup"><span data-stu-id="4a825-262">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="4a825-263">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4a825-263">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="4a825-264">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4a825-264">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="4a825-265">Find-Package</span><span class="sxs-lookup"><span data-stu-id="4a825-265">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="4a825-266">Save-Package</span><span class="sxs-lookup"><span data-stu-id="4a825-266">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="4a825-267">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="4a825-267">Uninstall-Package</span></span>](Uninstall-Package.md)
