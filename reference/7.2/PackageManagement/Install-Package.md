---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 1518be0d34733e36217b46cbbf496e580ec7b649
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597342"
---
# <span data-ttu-id="73d3b-102">Install-Package</span><span class="sxs-lookup"><span data-stu-id="73d3b-102">Install-Package</span></span>

## <span data-ttu-id="73d3b-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="73d3b-103">SYNOPSIS</span></span>
<span data-ttu-id="73d3b-104">Installe un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="73d3b-104">Installs one or more software packages.</span></span>

## <span data-ttu-id="73d3b-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="73d3b-105">SYNTAX</span></span>

### <span data-ttu-id="73d3b-106">PackageBySearch (par défaut)</span><span class="sxs-lookup"><span data-stu-id="73d3b-106">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="73d3b-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="73d3b-107">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="73d3b-108">NuGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="73d3b-108">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="73d3b-109">NuGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="73d3b-109">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="73d3b-110">PowerShellGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="73d3b-110">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="73d3b-111">PowerShellGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="73d3b-111">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="73d3b-112">Description</span><span class="sxs-lookup"><span data-stu-id="73d3b-112">DESCRIPTION</span></span>

<span data-ttu-id="73d3b-113">L' `Install-Package` applet de commande installe un ou plusieurs packages logiciels sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="73d3b-113">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="73d3b-114">Si vous avez plusieurs sources logicielles, utilisez `Get-PackageProvider` et `Get-PackageSource` pour afficher des détails sur vos fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="73d3b-114">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="73d3b-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="73d3b-115">EXAMPLES</span></span>

### <span data-ttu-id="73d3b-116">Exemple 1 : installer un package par nom de package</span><span class="sxs-lookup"><span data-stu-id="73d3b-116">Example 1: Install a package by package name</span></span>

<span data-ttu-id="73d3b-117">L' `Install-Package` applet de commande installe un package logiciel et ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="73d3b-117">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="73d3b-118">`Install-Package` utilise des paramètres pour spécifier le **nom** et la **source** des packages.</span><span class="sxs-lookup"><span data-stu-id="73d3b-118">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="73d3b-119">Le paramètre **Credential** utilise un compte d’utilisateur de domaine disposant des autorisations pour installer des packages.</span><span class="sxs-lookup"><span data-stu-id="73d3b-119">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="73d3b-120">La commande vous invite à entrer le mot de passe du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="73d3b-120">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="73d3b-121">Exemple 2 : utiliser Find-Package pour installer un package</span><span class="sxs-lookup"><span data-stu-id="73d3b-121">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="73d3b-122">Dans cet exemple, l’objet retourné par `Find-Package` est envoyé vers le pipeline et installé par `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="73d3b-122">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="73d3b-123">`Find-Package` utilise les paramètres **Name** et **source** pour localiser un package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-123">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="73d3b-124">L’objet est envoyé dans le pipeline et `Install-Package` installe le package sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="73d3b-124">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="73d3b-125">Exemple 3 : installer des packages en spécifiant une plage de versions</span><span class="sxs-lookup"><span data-stu-id="73d3b-125">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="73d3b-126">`Install-Package` utilise les paramètres **MinimumVersion** et **MaximumVersion** pour spécifier une plage de versions logicielles.</span><span class="sxs-lookup"><span data-stu-id="73d3b-126">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="73d3b-127">`Install-Package` utilise le **nom** et les paramètres de la **source** pour rechercher un package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-127">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="73d3b-128">Les paramètres **MinimumVersion** et **MaximumVersion** spécifient une plage de versions logicielles.</span><span class="sxs-lookup"><span data-stu-id="73d3b-128">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="73d3b-129">La version la plus élevée de la plage est installée.</span><span class="sxs-lookup"><span data-stu-id="73d3b-129">The highest version in the range is installed.</span></span>

## <span data-ttu-id="73d3b-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73d3b-130">PARAMETERS</span></span>

### <span data-ttu-id="73d3b-131">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="73d3b-131">-AcceptLicense</span></span>

 <span data-ttu-id="73d3b-132">**AcceptLicense** accepte automatiquement le contrat de licence lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="73d3b-132">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

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

### <span data-ttu-id="73d3b-133">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="73d3b-133">-AllowClobber</span></span>

<span data-ttu-id="73d3b-134">Remplace les messages d’avertissement relatifs aux conflits avec les commandes existantes.</span><span class="sxs-lookup"><span data-stu-id="73d3b-134">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="73d3b-135">Remplace les commandes existantes qui portent le même nom que les commandes en cours d’installation.</span><span class="sxs-lookup"><span data-stu-id="73d3b-135">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="73d3b-136">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="73d3b-136">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="73d3b-137">Autorise l’installation de packages marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="73d3b-137">Allows the installation of packages marked as prerelease.</span></span>

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

### <span data-ttu-id="73d3b-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="73d3b-138">-AllVersions</span></span>

<span data-ttu-id="73d3b-139">`Install-Package` installe toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-139">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="73d3b-140">Par défaut, seule la version la plus récente est installée.</span><span class="sxs-lookup"><span data-stu-id="73d3b-140">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="73d3b-141">-Command</span><span class="sxs-lookup"><span data-stu-id="73d3b-141">-Command</span></span>

<span data-ttu-id="73d3b-142">Spécifie une ou plusieurs commandes qui `Install-Package` effectuent des recherches.</span><span class="sxs-lookup"><span data-stu-id="73d3b-142">Specifies one or more commands that `Install-Package` searches.</span></span>

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

### <span data-ttu-id="73d3b-143">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="73d3b-143">-ConfigFile</span></span>

<span data-ttu-id="73d3b-144">Spécifie un chemin d’accès qui contient un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="73d3b-144">Specifies a path that contains a configuration file.</span></span>

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

### <span data-ttu-id="73d3b-145">-Contient</span><span class="sxs-lookup"><span data-stu-id="73d3b-145">-Contains</span></span>

<span data-ttu-id="73d3b-146">`Install-Package` obtient des objets si le paramètre **Contains** spécifie une valeur qui correspond à l’une des valeurs de propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="73d3b-146">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

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

### <span data-ttu-id="73d3b-147">-Credential</span><span class="sxs-lookup"><span data-stu-id="73d3b-147">-Credential</span></span>

<span data-ttu-id="73d3b-148">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’ordinateur et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="73d3b-148">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="73d3b-149">Tapez un nom d’utilisateur, tel que **User01**, **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** , généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="73d3b-149">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="73d3b-150">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="73d3b-150">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="73d3b-151">Lorsque le paramètre **Credential** n’est pas spécifié, `Install-Package` utilise l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="73d3b-151">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="73d3b-152">-Destination</span><span class="sxs-lookup"><span data-stu-id="73d3b-152">-Destination</span></span>

<span data-ttu-id="73d3b-153">Spécifie le chemin d’accès à un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="73d3b-153">Specifies a path to an input object.</span></span>

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

### <span data-ttu-id="73d3b-154">-DscResource</span><span class="sxs-lookup"><span data-stu-id="73d3b-154">-DscResource</span></span>

<span data-ttu-id="73d3b-155">Spécifie une ou plusieurs ressources de configuration d’état souhaité (DSC) sur lesquelles porte la recherche `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="73d3b-155">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="73d3b-156">Utilisez l' `Find-DscResource` applet de commande pour rechercher des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="73d3b-156">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

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

### <span data-ttu-id="73d3b-157">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="73d3b-157">-ExcludeVersion</span></span>

<span data-ttu-id="73d3b-158">Basculez pour exclure le numéro de version dans le chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="73d3b-158">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="73d3b-159">-Filter</span><span class="sxs-lookup"><span data-stu-id="73d3b-159">-Filter</span></span>

<span data-ttu-id="73d3b-160">Spécifie les termes à rechercher dans les propriétés **Name** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="73d3b-160">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="73d3b-161">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="73d3b-161">-FilterOnTag</span></span>

<span data-ttu-id="73d3b-162">Spécifie une balise qui filtre les résultats et exclut les résultats qui ne contiennent pas la balise spécifiée.</span><span class="sxs-lookup"><span data-stu-id="73d3b-162">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

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

### <span data-ttu-id="73d3b-163">-Force</span><span class="sxs-lookup"><span data-stu-id="73d3b-163">-Force</span></span>

<span data-ttu-id="73d3b-164">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="73d3b-164">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="73d3b-165">Remplace les restrictions qui empêchent `Install-Package` la réussie, à l’exception de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="73d3b-165">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="73d3b-166">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="73d3b-166">-ForceBootstrap</span></span>

<span data-ttu-id="73d3b-167">Force **PackageManagement** à installer automatiquement le fournisseur de package pour le package spécifié.</span><span class="sxs-lookup"><span data-stu-id="73d3b-167">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="73d3b-168">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="73d3b-168">-Headers</span></span>

<span data-ttu-id="73d3b-169">Spécifie les en-têtes de package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-169">Specifies the package headers.</span></span>

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

### <span data-ttu-id="73d3b-170">-Comprend</span><span class="sxs-lookup"><span data-stu-id="73d3b-170">-Includes</span></span>

<span data-ttu-id="73d3b-171">Spécifie si `Install-Package` tous les types de packages doivent être recherchés.</span><span class="sxs-lookup"><span data-stu-id="73d3b-171">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="73d3b-172">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="73d3b-172">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="73d3b-173">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="73d3b-173">Cmdlet</span></span>
- <span data-ttu-id="73d3b-174">DscResource</span><span class="sxs-lookup"><span data-stu-id="73d3b-174">DscResource</span></span>
- <span data-ttu-id="73d3b-175">Fonction</span><span class="sxs-lookup"><span data-stu-id="73d3b-175">Function</span></span>
- <span data-ttu-id="73d3b-176">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="73d3b-176">RoleCapability</span></span>
- <span data-ttu-id="73d3b-177">Workflow</span><span class="sxs-lookup"><span data-stu-id="73d3b-177">Workflow</span></span>

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

### <span data-ttu-id="73d3b-178">-InputObject</span><span class="sxs-lookup"><span data-stu-id="73d3b-178">-InputObject</span></span>

<span data-ttu-id="73d3b-179">Accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="73d3b-179">Accepts pipeline input.</span></span> <span data-ttu-id="73d3b-180">Spécifie un package à l’aide du type **SoftwareIdentity** du package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-180">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="73d3b-181">`Find-Package` génère un objet **SoftwareIdentity** .</span><span class="sxs-lookup"><span data-stu-id="73d3b-181">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="73d3b-182">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="73d3b-182">-InstallUpdate</span></span>

<span data-ttu-id="73d3b-183">Indique que `Install-Package` installe les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="73d3b-183">Indicates that `Install-Package` installs updates.</span></span>

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

### <span data-ttu-id="73d3b-184">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="73d3b-184">-MaximumVersion</span></span>

<span data-ttu-id="73d3b-185">Spécifie la version de package maximale autorisée que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="73d3b-185">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="73d3b-186">Si vous ne spécifiez pas ce paramètre, `Install-Package` installe la version la plus récente du package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-186">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="73d3b-187">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="73d3b-187">-MinimumVersion</span></span>

<span data-ttu-id="73d3b-188">Spécifie la version de package minimale autorisée que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="73d3b-188">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="73d3b-189">Si vous n’ajoutez pas ce paramètre, `Install-Package` installe la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="73d3b-189">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="73d3b-190">-Name</span><span class="sxs-lookup"><span data-stu-id="73d3b-190">-Name</span></span>

<span data-ttu-id="73d3b-191">Spécifie un ou plusieurs noms de packages.</span><span class="sxs-lookup"><span data-stu-id="73d3b-191">Specifies one or more package names.</span></span> <span data-ttu-id="73d3b-192">Plusieurs noms de packages doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="73d3b-192">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="73d3b-193">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="73d3b-193">-NoPathUpdate</span></span>

<span data-ttu-id="73d3b-194">**NoPathUpdate** s’applique uniquement à l’applet de commande `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="73d3b-194">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="73d3b-195">**NoPathUpdate** est un paramètre dynamique ajouté par le fournisseur et n’est pas pris en charge par `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="73d3b-195">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

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

### <span data-ttu-id="73d3b-196">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="73d3b-196">-PackageManagementProvider</span></span>

<span data-ttu-id="73d3b-197">Spécifie le nom du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="73d3b-197">Specifies the name of the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="73d3b-198">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="73d3b-198">-ProviderName</span></span>

<span data-ttu-id="73d3b-199">Spécifie un ou plusieurs noms de fournisseurs de packages dans lesquels étendre votre recherche de package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-199">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="73d3b-200">Vous obtenez les noms des fournisseurs de package en exécutant l’applet de commande `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="73d3b-200">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="73d3b-201">-Proxy</span><span class="sxs-lookup"><span data-stu-id="73d3b-201">-Proxy</span></span>

<span data-ttu-id="73d3b-202">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="73d3b-202">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="73d3b-203">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="73d3b-203">-ProxyCredential</span></span>

<span data-ttu-id="73d3b-204">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="73d3b-204">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="73d3b-205">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="73d3b-205">-PublishLocation</span></span>

<span data-ttu-id="73d3b-206">Spécifie le chemin d’accès à l’emplacement publié d’un package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-206">Specifies the path to a package's published location.</span></span>

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

### <span data-ttu-id="73d3b-207">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="73d3b-207">-RequiredVersion</span></span>

<span data-ttu-id="73d3b-208">Spécifie la version exacte du package que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="73d3b-208">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="73d3b-209">Si vous n’ajoutez pas ce paramètre, `Install-Package` installe la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="73d3b-209">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="73d3b-210">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="73d3b-210">-RoleCapability</span></span>

<span data-ttu-id="73d3b-211">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="73d3b-211">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="73d3b-212">-Étendue</span><span class="sxs-lookup"><span data-stu-id="73d3b-212">-Scope</span></span>

<span data-ttu-id="73d3b-213">Spécifie l’étendue pour laquelle installer le package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-213">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="73d3b-214">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="73d3b-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="73d3b-215">Utilisateur en cours</span><span class="sxs-lookup"><span data-stu-id="73d3b-215">CurrentUser</span></span>
- <span data-ttu-id="73d3b-216">AllUsers</span><span class="sxs-lookup"><span data-stu-id="73d3b-216">AllUsers</span></span>

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

### <span data-ttu-id="73d3b-217">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="73d3b-217">-ScriptPublishLocation</span></span>

<span data-ttu-id="73d3b-218">Spécifie le chemin d’accès à l’emplacement de publication d’un script.</span><span class="sxs-lookup"><span data-stu-id="73d3b-218">Specifies the path to a script's published location.</span></span>

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

### <span data-ttu-id="73d3b-219">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="73d3b-219">-ScriptSourceLocation</span></span>

<span data-ttu-id="73d3b-220">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="73d3b-220">Specifies the script source location.</span></span>

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

### <span data-ttu-id="73d3b-221">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="73d3b-221">-SkipDependencies</span></span>

<span data-ttu-id="73d3b-222">Ignore l’installation des dépendances logicielles.</span><span class="sxs-lookup"><span data-stu-id="73d3b-222">Skips the installation of software dependencies.</span></span>

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

### <span data-ttu-id="73d3b-223">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="73d3b-223">-SkipPublisherCheck</span></span>

<span data-ttu-id="73d3b-224">Vous permet d’obtenir une version de package plus récente que la version installée.</span><span class="sxs-lookup"><span data-stu-id="73d3b-224">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="73d3b-225">Par exemple, un package installé signé numériquement par un éditeur approuvé, mais pour lequel une nouvelle version n’est pas signée numériquement.</span><span class="sxs-lookup"><span data-stu-id="73d3b-225">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="73d3b-226">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="73d3b-226">-SkipValidate</span></span>

<span data-ttu-id="73d3b-227">Commutateur qui ignore la validation des informations d’identification d’un package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-227">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="73d3b-228">-Source</span><span class="sxs-lookup"><span data-stu-id="73d3b-228">-Source</span></span>

<span data-ttu-id="73d3b-229">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-229">Specifies one or more package sources.</span></span> <span data-ttu-id="73d3b-230">Plusieurs noms de sources de packages doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="73d3b-230">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="73d3b-231">Vous pouvez récupérer les noms des sources du package en exécutant l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="73d3b-231">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="73d3b-232">-Tag</span><span class="sxs-lookup"><span data-stu-id="73d3b-232">-Tag</span></span>

<span data-ttu-id="73d3b-233">Spécifie une ou plusieurs chaînes à rechercher dans les métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="73d3b-233">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="73d3b-234">-Type</span><span class="sxs-lookup"><span data-stu-id="73d3b-234">-Type</span></span>

<span data-ttu-id="73d3b-235">Spécifie s’il faut rechercher des packages avec un module, un script ou les deux.</span><span class="sxs-lookup"><span data-stu-id="73d3b-235">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="73d3b-236">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="73d3b-236">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="73d3b-237">Module</span><span class="sxs-lookup"><span data-stu-id="73d3b-237">Module</span></span>
- <span data-ttu-id="73d3b-238">Script</span><span class="sxs-lookup"><span data-stu-id="73d3b-238">Script</span></span>
- <span data-ttu-id="73d3b-239">Tous</span><span class="sxs-lookup"><span data-stu-id="73d3b-239">All</span></span>

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

### <span data-ttu-id="73d3b-240">-Confirm</span><span class="sxs-lookup"><span data-stu-id="73d3b-240">-Confirm</span></span>

<span data-ttu-id="73d3b-241">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73d3b-241">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="73d3b-242">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="73d3b-242">-WhatIf</span></span>

<span data-ttu-id="73d3b-243">Montre ce qui se passe si l' `Install-Package` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="73d3b-243">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="73d3b-244">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="73d3b-244">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="73d3b-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73d3b-245">CommonParameters</span></span>

<span data-ttu-id="73d3b-246">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73d3b-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73d3b-247">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="73d3b-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73d3b-248">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="73d3b-248">INPUTS</span></span>

### <span data-ttu-id="73d3b-249">`Install-Package` accepte l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="73d3b-249">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="73d3b-250">SORTIES</span><span class="sxs-lookup"><span data-stu-id="73d3b-250">OUTPUTS</span></span>

### <span data-ttu-id="73d3b-251">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="73d3b-251">SoftwareIdentity[]</span></span>

## <span data-ttu-id="73d3b-252">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="73d3b-252">NOTES</span></span>

<span data-ttu-id="73d3b-253">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73d3b-253">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="73d3b-254">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="73d3b-254">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="73d3b-255">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="73d3b-255">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="73d3b-256">Par exemple, `Install-Package` a le paramètre **PowerShellGet** défini qui inclut `-NoPathUpdate` , `AllowClobber` et `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="73d3b-256">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73d3b-257">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="73d3b-257">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="73d3b-258">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="73d3b-258">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="73d3b-259">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="73d3b-259">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="73d3b-260">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73d3b-260">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="73d3b-261">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="73d3b-261">RELATED LINKS</span></span>

[<span data-ttu-id="73d3b-262">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="73d3b-262">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="73d3b-263">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="73d3b-263">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="73d3b-264">Get-Help</span><span class="sxs-lookup"><span data-stu-id="73d3b-264">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="73d3b-265">Get-Package</span><span class="sxs-lookup"><span data-stu-id="73d3b-265">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="73d3b-266">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="73d3b-266">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="73d3b-267">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="73d3b-267">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="73d3b-268">Find-Package</span><span class="sxs-lookup"><span data-stu-id="73d3b-268">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="73d3b-269">Save-Package</span><span class="sxs-lookup"><span data-stu-id="73d3b-269">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="73d3b-270">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="73d3b-270">Uninstall-Package</span></span>](Uninstall-Package.md)
