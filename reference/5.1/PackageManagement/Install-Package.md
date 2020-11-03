---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 058ed7f90e63bd7ca7a29cf6c89864a30255662a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202933"
---
# <span data-ttu-id="71101-103">Install-Package</span><span class="sxs-lookup"><span data-stu-id="71101-103">Install-Package</span></span>

## <span data-ttu-id="71101-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="71101-104">SYNOPSIS</span></span>
<span data-ttu-id="71101-105">Installe un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="71101-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="71101-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="71101-106">SYNTAX</span></span>

### <span data-ttu-id="71101-107">PackageBySearch (par défaut)</span><span class="sxs-lookup"><span data-stu-id="71101-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="71101-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="71101-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="71101-109">Programmes : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="71101-109">Programs:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="71101-110">Programmes : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="71101-110">Programs:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="71101-111">MSI : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="71101-111">msi:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="71101-112">MSI : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="71101-112">msi:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="71101-113">NuGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="71101-113">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="71101-114">NuGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="71101-114">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="71101-115">PowerShellGet : PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="71101-115">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="71101-116">PowerShellGet : PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="71101-116">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="71101-117">Description</span><span class="sxs-lookup"><span data-stu-id="71101-117">DESCRIPTION</span></span>

<span data-ttu-id="71101-118">L' `Install-Package` applet de commande installe un ou plusieurs packages logiciels sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="71101-118">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="71101-119">Si vous avez plusieurs sources logicielles, utilisez `Get-PackageProvider` et `Get-PackageSource` pour afficher des détails sur vos fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="71101-119">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="71101-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="71101-120">EXAMPLES</span></span>

### <span data-ttu-id="71101-121">Exemple 1 : installer un package par nom de package</span><span class="sxs-lookup"><span data-stu-id="71101-121">Example 1: Install a package by package name</span></span>

<span data-ttu-id="71101-122">L' `Install-Package` applet de commande installe un package logiciel et ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="71101-122">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="71101-123">`Install-Package` utilise des paramètres pour spécifier le **nom** et la **source** des packages.</span><span class="sxs-lookup"><span data-stu-id="71101-123">`Install-Package` uses parameters to specify the packages **Name** and **Source** .</span></span> <span data-ttu-id="71101-124">Le paramètre **Credential** utilise un compte d’utilisateur de domaine disposant des autorisations pour installer des packages.</span><span class="sxs-lookup"><span data-stu-id="71101-124">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="71101-125">La commande vous invite à entrer le mot de passe du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="71101-125">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="71101-126">Exemple 2 : utiliser Find-Package pour installer un package</span><span class="sxs-lookup"><span data-stu-id="71101-126">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="71101-127">Dans cet exemple, l’objet retourné par `Find-Package` est envoyé vers le pipeline et installé par `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="71101-127">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="71101-128">`Find-Package` utilise les paramètres **Name** et **source** pour localiser un package.</span><span class="sxs-lookup"><span data-stu-id="71101-128">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="71101-129">L’objet est envoyé dans le pipeline et `Install-Package` installe le package sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="71101-129">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="71101-130">Exemple 3 : installer des packages en spécifiant une plage de versions</span><span class="sxs-lookup"><span data-stu-id="71101-130">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="71101-131">`Install-Package` utilise les paramètres **MinimumVersion** et **MaximumVersion** pour spécifier une plage de versions logicielles.</span><span class="sxs-lookup"><span data-stu-id="71101-131">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="71101-132">`Install-Package` utilise le **nom** et les paramètres de la **source** pour rechercher un package.</span><span class="sxs-lookup"><span data-stu-id="71101-132">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="71101-133">Les paramètres **MinimumVersion** et **MaximumVersion** spécifient une plage de versions logicielles.</span><span class="sxs-lookup"><span data-stu-id="71101-133">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="71101-134">La version la plus élevée de la plage est installée.</span><span class="sxs-lookup"><span data-stu-id="71101-134">The highest version in the range is installed.</span></span>

## <span data-ttu-id="71101-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="71101-135">PARAMETERS</span></span>

### <span data-ttu-id="71101-136">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="71101-136">-AcceptLicense</span></span>

 <span data-ttu-id="71101-137">**AcceptLicense** accepte automatiquement le contrat de licence lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="71101-137">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

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

### <span data-ttu-id="71101-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="71101-138">-AllowClobber</span></span>

<span data-ttu-id="71101-139">Remplace les messages d’avertissement relatifs aux conflits avec les commandes existantes.</span><span class="sxs-lookup"><span data-stu-id="71101-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="71101-140">Remplace les commandes existantes qui portent le même nom que les commandes en cours d’installation.</span><span class="sxs-lookup"><span data-stu-id="71101-140">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="71101-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="71101-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="71101-142">Autorise l’installation de packages marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="71101-142">Allows the installation of packages marked as prerelease.</span></span>

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

### <span data-ttu-id="71101-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="71101-143">-AllVersions</span></span>

<span data-ttu-id="71101-144">`Install-Package` installe toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="71101-144">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="71101-145">Par défaut, seule la version la plus récente est installée.</span><span class="sxs-lookup"><span data-stu-id="71101-145">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="71101-146">-Command</span><span class="sxs-lookup"><span data-stu-id="71101-146">-Command</span></span>

<span data-ttu-id="71101-147">Spécifie une ou plusieurs commandes qui `Install-Package` effectuent des recherches.</span><span class="sxs-lookup"><span data-stu-id="71101-147">Specifies one or more commands that `Install-Package` searches.</span></span>

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

### <span data-ttu-id="71101-148">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="71101-148">-ConfigFile</span></span>

<span data-ttu-id="71101-149">Spécifie un chemin d’accès qui contient un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="71101-149">Specifies a path that contains a configuration file.</span></span>

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

### <span data-ttu-id="71101-150">-Contient</span><span class="sxs-lookup"><span data-stu-id="71101-150">-Contains</span></span>

<span data-ttu-id="71101-151">`Install-Package` obtient des objets si le paramètre **Contains** spécifie une valeur qui correspond à l’une des valeurs de propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="71101-151">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

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

### <span data-ttu-id="71101-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="71101-152">-Credential</span></span>

<span data-ttu-id="71101-153">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’ordinateur et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="71101-153">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="71101-154">Tapez un nom d’utilisateur, tel que **User01** , **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="71101-154">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="71101-155">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="71101-155">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="71101-156">Lorsque le paramètre **Credential** n’est pas spécifié, `Install-Package` utilise l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="71101-156">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="71101-157">-Destination</span><span class="sxs-lookup"><span data-stu-id="71101-157">-Destination</span></span>

<span data-ttu-id="71101-158">Spécifie le chemin d’accès à un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="71101-158">Specifies a path to an input object.</span></span>

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

### <span data-ttu-id="71101-159">-DscResource</span><span class="sxs-lookup"><span data-stu-id="71101-159">-DscResource</span></span>

<span data-ttu-id="71101-160">Spécifie une ou plusieurs ressources de configuration d’état souhaité (DSC) sur lesquelles porte la recherche `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="71101-160">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="71101-161">Utilisez l' `Find-DscResource` applet de commande pour rechercher des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="71101-161">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

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

### <span data-ttu-id="71101-162">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="71101-162">-ExcludeVersion</span></span>

<span data-ttu-id="71101-163">Basculez pour exclure le numéro de version dans le chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="71101-163">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="71101-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="71101-164">-Filter</span></span>

<span data-ttu-id="71101-165">Spécifie les termes à rechercher dans les propriétés **Name** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="71101-165">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="71101-166">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="71101-166">-FilterOnTag</span></span>

<span data-ttu-id="71101-167">Spécifie une balise qui filtre les résultats et exclut les résultats qui ne contiennent pas la balise spécifiée.</span><span class="sxs-lookup"><span data-stu-id="71101-167">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

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

### <span data-ttu-id="71101-168">-Force</span><span class="sxs-lookup"><span data-stu-id="71101-168">-Force</span></span>

<span data-ttu-id="71101-169">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="71101-169">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="71101-170">Remplace les restrictions qui empêchent `Install-Package` la réussie, à l’exception de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="71101-170">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="71101-171">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="71101-171">-ForceBootstrap</span></span>

<span data-ttu-id="71101-172">Force **PackageManagement** à installer automatiquement le fournisseur de package pour le package spécifié.</span><span class="sxs-lookup"><span data-stu-id="71101-172">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="71101-173">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="71101-173">-Headers</span></span>

<span data-ttu-id="71101-174">Spécifie les en-têtes de package.</span><span class="sxs-lookup"><span data-stu-id="71101-174">Specifies the package headers.</span></span>

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

### <span data-ttu-id="71101-175">-Comprend</span><span class="sxs-lookup"><span data-stu-id="71101-175">-Includes</span></span>

<span data-ttu-id="71101-176">Spécifie si `Install-Package` tous les types de packages doivent être recherchés.</span><span class="sxs-lookup"><span data-stu-id="71101-176">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="71101-177">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="71101-177">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="71101-178">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="71101-178">Cmdlet</span></span>
- <span data-ttu-id="71101-179">DscResource</span><span class="sxs-lookup"><span data-stu-id="71101-179">DscResource</span></span>
- <span data-ttu-id="71101-180">Fonction</span><span class="sxs-lookup"><span data-stu-id="71101-180">Function</span></span>
- <span data-ttu-id="71101-181">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="71101-181">RoleCapability</span></span>
- <span data-ttu-id="71101-182">Workflow</span><span class="sxs-lookup"><span data-stu-id="71101-182">Workflow</span></span>

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

### <span data-ttu-id="71101-183">-InputObject</span><span class="sxs-lookup"><span data-stu-id="71101-183">-InputObject</span></span>

<span data-ttu-id="71101-184">Accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="71101-184">Accepts pipeline input.</span></span> <span data-ttu-id="71101-185">Spécifie un package à l’aide du type **SoftwareIdentity** du package.</span><span class="sxs-lookup"><span data-stu-id="71101-185">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="71101-186">`Find-Package` génère un objet **SoftwareIdentity** .</span><span class="sxs-lookup"><span data-stu-id="71101-186">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="71101-187">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="71101-187">-InstallUpdate</span></span>

<span data-ttu-id="71101-188">Indique que `Install-Package` installe les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="71101-188">Indicates that `Install-Package` installs updates.</span></span>

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

### <span data-ttu-id="71101-189">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="71101-189">-MaximumVersion</span></span>

<span data-ttu-id="71101-190">Spécifie la version de package maximale autorisée que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="71101-190">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="71101-191">Si vous ne spécifiez pas ce paramètre, `Install-Package` installe la version la plus récente du package.</span><span class="sxs-lookup"><span data-stu-id="71101-191">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="71101-192">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="71101-192">-MinimumVersion</span></span>

<span data-ttu-id="71101-193">Spécifie la version de package minimale autorisée que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="71101-193">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="71101-194">Si vous n’ajoutez pas ce paramètre, `Install-Package` installe la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="71101-194">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="71101-195">-Name</span><span class="sxs-lookup"><span data-stu-id="71101-195">-Name</span></span>

<span data-ttu-id="71101-196">Spécifie un ou plusieurs noms de packages.</span><span class="sxs-lookup"><span data-stu-id="71101-196">Specifies one or more package names.</span></span> <span data-ttu-id="71101-197">Plusieurs noms de packages doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="71101-197">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="71101-198">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="71101-198">-NoPathUpdate</span></span>

<span data-ttu-id="71101-199">**NoPathUpdate** s’applique uniquement à l’applet de commande `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="71101-199">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="71101-200">**NoPathUpdate** est un paramètre dynamique ajouté par le fournisseur et n’est pas pris en charge par `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="71101-200">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

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

### <span data-ttu-id="71101-201">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="71101-201">-PackageManagementProvider</span></span>

<span data-ttu-id="71101-202">Spécifie le nom du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="71101-202">Specifies the name of the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="71101-203">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="71101-203">-ProviderName</span></span>

<span data-ttu-id="71101-204">Spécifie un ou plusieurs noms de fournisseurs de packages dans lesquels étendre votre recherche de package.</span><span class="sxs-lookup"><span data-stu-id="71101-204">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="71101-205">Vous obtenez les noms des fournisseurs de package en exécutant l’applet de commande `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="71101-205">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="71101-206">-Proxy</span><span class="sxs-lookup"><span data-stu-id="71101-206">-Proxy</span></span>

<span data-ttu-id="71101-207">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="71101-207">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="71101-208">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="71101-208">-ProxyCredential</span></span>

<span data-ttu-id="71101-209">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="71101-209">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="71101-210">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="71101-210">-PublishLocation</span></span>

<span data-ttu-id="71101-211">Spécifie le chemin d’accès à l’emplacement publié d’un package.</span><span class="sxs-lookup"><span data-stu-id="71101-211">Specifies the path to a package's published location.</span></span>

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

### <span data-ttu-id="71101-212">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="71101-212">-RequiredVersion</span></span>

<span data-ttu-id="71101-213">Spécifie la version exacte du package que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="71101-213">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="71101-214">Si vous n’ajoutez pas ce paramètre, `Install-Package` installe la version la plus récente du package qui satisfait à toute version spécifiée par le paramètre **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="71101-214">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="71101-215">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="71101-215">-RoleCapability</span></span>

<span data-ttu-id="71101-216">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="71101-216">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="71101-217">-Étendue</span><span class="sxs-lookup"><span data-stu-id="71101-217">-Scope</span></span>

<span data-ttu-id="71101-218">Spécifie l’étendue pour laquelle installer le package.</span><span class="sxs-lookup"><span data-stu-id="71101-218">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="71101-219">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="71101-219">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="71101-220">Utilisateur en cours</span><span class="sxs-lookup"><span data-stu-id="71101-220">CurrentUser</span></span>
- <span data-ttu-id="71101-221">AllUsers</span><span class="sxs-lookup"><span data-stu-id="71101-221">AllUsers</span></span>

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

### <span data-ttu-id="71101-222">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="71101-222">-ScriptPublishLocation</span></span>

<span data-ttu-id="71101-223">Spécifie le chemin d’accès à l’emplacement de publication d’un script.</span><span class="sxs-lookup"><span data-stu-id="71101-223">Specifies the path to a script's published location.</span></span>

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

### <span data-ttu-id="71101-224">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="71101-224">-ScriptSourceLocation</span></span>

<span data-ttu-id="71101-225">Spécifie l’emplacement source du script.</span><span class="sxs-lookup"><span data-stu-id="71101-225">Specifies the script source location.</span></span>

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

### <span data-ttu-id="71101-226">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="71101-226">-SkipDependencies</span></span>

<span data-ttu-id="71101-227">Ignore l’installation des dépendances logicielles.</span><span class="sxs-lookup"><span data-stu-id="71101-227">Skips the installation of software dependencies.</span></span>

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

### <span data-ttu-id="71101-228">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="71101-228">-SkipPublisherCheck</span></span>

<span data-ttu-id="71101-229">Vous permet d’obtenir une version de package plus récente que la version installée.</span><span class="sxs-lookup"><span data-stu-id="71101-229">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="71101-230">Par exemple, un package installé signé numériquement par un éditeur approuvé, mais pour lequel une nouvelle version n’est pas signée numériquement.</span><span class="sxs-lookup"><span data-stu-id="71101-230">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="71101-231">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="71101-231">-SkipValidate</span></span>

<span data-ttu-id="71101-232">Commutateur qui ignore la validation des informations d’identification d’un package.</span><span class="sxs-lookup"><span data-stu-id="71101-232">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="71101-233">-Source</span><span class="sxs-lookup"><span data-stu-id="71101-233">-Source</span></span>

<span data-ttu-id="71101-234">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="71101-234">Specifies one or more package sources.</span></span> <span data-ttu-id="71101-235">Plusieurs noms de sources de packages doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="71101-235">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="71101-236">Vous pouvez récupérer les noms des sources du package en exécutant l’applet de commande `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="71101-236">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="71101-237">-Tag</span><span class="sxs-lookup"><span data-stu-id="71101-237">-Tag</span></span>

<span data-ttu-id="71101-238">Spécifie une ou plusieurs chaînes à rechercher dans les métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="71101-238">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="71101-239">-Type</span><span class="sxs-lookup"><span data-stu-id="71101-239">-Type</span></span>

<span data-ttu-id="71101-240">Spécifie s’il faut rechercher des packages avec un module, un script ou les deux.</span><span class="sxs-lookup"><span data-stu-id="71101-240">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="71101-241">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="71101-241">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="71101-242">Module</span><span class="sxs-lookup"><span data-stu-id="71101-242">Module</span></span>
- <span data-ttu-id="71101-243">Script</span><span class="sxs-lookup"><span data-stu-id="71101-243">Script</span></span>
- <span data-ttu-id="71101-244">Tous</span><span class="sxs-lookup"><span data-stu-id="71101-244">All</span></span>

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

### <span data-ttu-id="71101-245">-Confirm</span><span class="sxs-lookup"><span data-stu-id="71101-245">-Confirm</span></span>

<span data-ttu-id="71101-246">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71101-246">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="71101-247">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="71101-247">-WhatIf</span></span>

<span data-ttu-id="71101-248">Montre ce qui se passe si l' `Install-Package` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="71101-248">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="71101-249">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="71101-249">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="71101-250">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="71101-250">-AdditionalArguments</span></span>

<span data-ttu-id="71101-251">Spécifie un ou plusieurs arguments supplémentaires pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="71101-251">Specifies one or more additional arguments for installation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi:PackageBySearch, msi:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71101-252">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="71101-252">-IncludeSystemComponent</span></span>

<span data-ttu-id="71101-253">Indique que cette applet de commande comprend des composants système dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="71101-253">Indicates that this cmdlet includes system components in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71101-254">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="71101-254">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="71101-255">Indique que cette applet de commande comprend le programme d’installation Windows dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="71101-255">Indicates that this cmdlet includes the Windows installer in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71101-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71101-256">CommonParameters</span></span>

<span data-ttu-id="71101-257">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="71101-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71101-258">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="71101-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71101-259">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="71101-259">INPUTS</span></span>

### <span data-ttu-id="71101-260">`Install-Package` accepte l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="71101-260">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="71101-261">SORTIES</span><span class="sxs-lookup"><span data-stu-id="71101-261">OUTPUTS</span></span>

### <span data-ttu-id="71101-262">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="71101-262">SoftwareIdentity[]</span></span>

## <span data-ttu-id="71101-263">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="71101-263">NOTES</span></span>

<span data-ttu-id="71101-264">L’inclusion d’un fournisseur de package dans une commande peut rendre des paramètres dynamiques disponibles pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71101-264">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="71101-265">Les paramètres dynamiques sont spécifiques à un fournisseur de packages.</span><span class="sxs-lookup"><span data-stu-id="71101-265">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="71101-266">L' `Get-Help` applet de commande répertorie les jeux de paramètres d’une applet de commande et comprend le jeu de paramètres du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="71101-266">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="71101-267">Par exemple, `Install-Package` a le paramètre **PowerShellGet** défini qui inclut `-NoPathUpdate` , `AllowClobber` et `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="71101-267">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="71101-268">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="71101-268">RELATED LINKS</span></span>

[<span data-ttu-id="71101-269">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="71101-269">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="71101-270">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="71101-270">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="71101-271">Get-Help</span><span class="sxs-lookup"><span data-stu-id="71101-271">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="71101-272">Get-Package</span><span class="sxs-lookup"><span data-stu-id="71101-272">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="71101-273">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="71101-273">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="71101-274">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="71101-274">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="71101-275">Find-Package</span><span class="sxs-lookup"><span data-stu-id="71101-275">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="71101-276">Save-Package</span><span class="sxs-lookup"><span data-stu-id="71101-276">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="71101-277">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="71101-277">Uninstall-Package</span></span>](Uninstall-Package.md)
