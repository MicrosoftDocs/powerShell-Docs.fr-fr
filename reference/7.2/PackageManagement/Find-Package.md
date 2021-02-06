---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Package
ms.openlocfilehash: c45ff8443818580dcc57cd1a945822007ae259a8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99599171"
---
# <span data-ttu-id="f528d-102">Find-Package</span><span class="sxs-lookup"><span data-stu-id="f528d-102">Find-Package</span></span>

## <span data-ttu-id="f528d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f528d-103">SYNOPSIS</span></span>
<span data-ttu-id="f528d-104">Recherche les packages de logiciels dans les sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="f528d-104">Finds software packages in available package sources.</span></span>

## <span data-ttu-id="f528d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f528d-105">SYNTAX</span></span>

### <span data-ttu-id="f528d-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="f528d-106">NuGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>]
 [-FilterOnTag <String[]>] [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="f528d-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f528d-107">PowerShellGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-AllowPrereleaseVersions] [-PackageManagementProvider <String>]
 [-PublishLocation <String>] [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>]
 [-Type <String>] [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>]
 [-DscResource <String[]>] [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense]
 [<CommonParameters>]
```

## <span data-ttu-id="f528d-108">Description</span><span class="sxs-lookup"><span data-stu-id="f528d-108">DESCRIPTION</span></span>

<span data-ttu-id="f528d-109">`Find-Package` recherche les packages de logiciels qui sont disponibles dans les sources de package.</span><span class="sxs-lookup"><span data-stu-id="f528d-109">`Find-Package` finds software packages that are available in package sources.</span></span> <span data-ttu-id="f528d-110">`Get-PackageProvider` et `Get-PackageSource` Affichez des détails sur vos fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="f528d-110">`Get-PackageProvider` and `Get-PackageSource` display details about your providers.</span></span>

## <span data-ttu-id="f528d-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f528d-111">EXAMPLES</span></span>

### <span data-ttu-id="f528d-112">Exemple 1 : Rechercher tous les packages disponibles à partir d’un fournisseur de package</span><span class="sxs-lookup"><span data-stu-id="f528d-112">Example 1: Find all available packages from a package provider</span></span>

<span data-ttu-id="f528d-113">Cette commande recherche tous les packages de modules PowerShell disponibles dans une galerie inscrite.</span><span class="sxs-lookup"><span data-stu-id="f528d-113">This command finds all available PowerShell module packages in a registered gallery.</span></span> <span data-ttu-id="f528d-114">Utilisez `Get-PackageProvider` pour récupérer le nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="f528d-114">Use `Get-PackageProvider` to get the provider name.</span></span>

```
Find-Package -ProviderName NuGet
```

```Output
Name               Version   Source     Summary
----               -------   ------     -------
NUnit              3.11.0    MyNuGet    NUnit is a unit-testing framework for all .NET langua...
Newtonsoft.Json    12.0.1    MyNuGet    Json.NET is a popular high-performance JSON framework...
EntityFramework    6.2.0     MyNuGet    Entity Framework is Microsoft's recommended data acce...
MySql.Data         8.0.15    MyNuGet    MySql.Data.MySqlClient .Net Core Class Library
bootstrap          4.3.1     MyNuGet    Bootstrap framework in CSS. Includes fonts and JavaSc...
NuGet.Core         2.14.0    MyNuGet    NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="f528d-115">`Find-Package` utilise le paramètre **Provider** pour spécifier le **NuGet** du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="f528d-115">`Find-Package` uses the **Provider** parameter to specify the provider **NuGet**.</span></span>

### <span data-ttu-id="f528d-116">Exemple 2 : Rechercher un package à partir d’une source de package</span><span class="sxs-lookup"><span data-stu-id="f528d-116">Example 2: Find a package from a package source</span></span>

<span data-ttu-id="f528d-117">Cette commande recherche la version la plus récente d’un package à partir d’une source de package spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f528d-117">This command finds the newest version of a package from a specified package source.</span></span> <span data-ttu-id="f528d-118">Si aucune source de package n’est fournie, `Find-Package` effectue une recherche dans chaque fournisseur de package installé et ses sources de package.</span><span class="sxs-lookup"><span data-stu-id="f528d-118">If a package source isn't provided, `Find-Package` searches each installed package provider and its package sources.</span></span> <span data-ttu-id="f528d-119">Utilisez `Get-PackageSource` pour récupérer le nom de la source.</span><span class="sxs-lookup"><span data-stu-id="f528d-119">Use `Get-PackageSource` to get the source name.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet
```

```Output
Name         Version   Source    Summary
----         -------   ------    -------
NuGet.Core   2.14.0    MyNuGet   NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="f528d-120">`Find-Package` utilise le paramètre **Name** pour spécifier le nom du package **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="f528d-120">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="f528d-121">Le paramètre **source** spécifie de rechercher le package dans **MyNuGet**.</span><span class="sxs-lookup"><span data-stu-id="f528d-121">The **Source** parameter specifies to search for the package in **MyNuGet**.</span></span>

### <span data-ttu-id="f528d-122">Exemple 3 : Rechercher toutes les versions d’un package</span><span class="sxs-lookup"><span data-stu-id="f528d-122">Example 3: Find all versions of a package</span></span>

<span data-ttu-id="f528d-123">Cette commande recherche toutes les versions de package disponibles à partir d’un fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="f528d-123">This command finds all available package versions from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.14.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.14.0-rtm-832   MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.13.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
...
NuGet.Core    1.1.229.159      MyNuGet      NuGet.Core is the core framework assembly for NuGet...
Nuget.Core    1.0.1120.104     MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="f528d-124">`Find-Package` utilise le paramètre **Name** pour spécifier le package **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="f528d-124">`Find-Package` uses the **Name** parameter to specify the package **NuGet.Core**.</span></span> <span data-ttu-id="f528d-125">Le paramètre **providerName** spécifie la recherche du package dans **MyNuGet**.</span><span class="sxs-lookup"><span data-stu-id="f528d-125">The **ProviderName** parameter specifies to search for the package in **MyNuGet**.</span></span> <span data-ttu-id="f528d-126">**AllVersions** spécifie que toutes les versions disponibles sont retournées.</span><span class="sxs-lookup"><span data-stu-id="f528d-126">**AllVersions** specifies that all available versions are returned.</span></span>

### <span data-ttu-id="f528d-127">Exemple 4 : Rechercher un package avec un nom et une version spécifiques</span><span class="sxs-lookup"><span data-stu-id="f528d-127">Example 4: Find a package with a specific name and version</span></span>

<span data-ttu-id="f528d-128">Cette commande recherche une version de package spécifique à partir d’un fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="f528d-128">This command finds a specific package version from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -RequiredVersion 2.9.0
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="f528d-129">`Find-Package` utilise le paramètre **Name** pour spécifier le nom du package **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="f528d-129">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="f528d-130">Le paramètre **providerName** spécifie la recherche du package dans **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f528d-130">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="f528d-131">**RequiredVersion** spécifie que seule la version **2.9.0** est retournée.</span><span class="sxs-lookup"><span data-stu-id="f528d-131">**RequiredVersion** specifies that only version **2.9.0** is returned.</span></span>

### <span data-ttu-id="f528d-132">Exemple 5 : Rechercher des packages dans une plage de versions</span><span class="sxs-lookup"><span data-stu-id="f528d-132">Example 5: Find packages within a range of versions</span></span>

<span data-ttu-id="f528d-133">Cette commande recherche une plage de versions pour un package spécifié.</span><span class="sxs-lookup"><span data-stu-id="f528d-133">This command finds a range of versions for a specified package.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -MinimumVersion 2.7.0 -MaximumVersion 2.9.0 -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.6            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.7.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="f528d-134">`Find-Package` utilise le paramètre **Name** pour spécifier le nom du package **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="f528d-134">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="f528d-135">Le paramètre **providerName** spécifie la recherche du package dans **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f528d-135">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="f528d-136">**MinimumVersion** spécifie la version la plus basse **2.7.0**.</span><span class="sxs-lookup"><span data-stu-id="f528d-136">**MinimumVersion** specifies the lowest version **2.7.0**.</span></span> <span data-ttu-id="f528d-137">**MaximumVersion** spécifie la version la plus récente **2.9.0**.</span><span class="sxs-lookup"><span data-stu-id="f528d-137">**MaximumVersion** specifies the highest version **2.9.0**.</span></span>
<span data-ttu-id="f528d-138">**AllVersions** détermine que la plage est retournée comme spécifié par les valeurs minimale et maximale.</span><span class="sxs-lookup"><span data-stu-id="f528d-138">**AllVersions** determines the range is returned as specified by the minimum and maximum.</span></span>

### <span data-ttu-id="f528d-139">Exemple 6 : Rechercher un package à partir d’un système de fichiers</span><span class="sxs-lookup"><span data-stu-id="f528d-139">Example 6: Find a package from a file system</span></span>

<span data-ttu-id="f528d-140">Cette commande recherche les packages dont l’extension de fichier `.nupkg` est stockée sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f528d-140">This command finds packages with the file extension `.nupkg` that are stored on the local computer.</span></span>
<span data-ttu-id="f528d-141">Les fichiers sont des packages téléchargés à partir d’une galerie telle que **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f528d-141">The files are packages downloaded from a gallery such as the **NuGet**.</span></span>

```
PS> Find-Package -Source C:\LocalPkg
```

```Output
Name                 Version    Source           Summary
----                 -------    ------           -------
Microsoft.Web.Xdt    3.0.0      C:\LocalPkg\     Microsoft Xml Document Transformation (XDT)...
NuGet.Core           2.14.0     C:\LocalPkg\     NuGet.Core is the core framework assembly...
```

## <span data-ttu-id="f528d-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f528d-142">PARAMETERS</span></span>

### <span data-ttu-id="f528d-143">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="f528d-143">-AcceptLicense</span></span>

<span data-ttu-id="f528d-144">Accepte automatiquement un contrat de licence si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="f528d-144">Automatically accepts a license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="f528d-145">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="f528d-145">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="f528d-146">Comprend les packages marqués comme version préliminaire dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="f528d-146">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="f528d-147">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="f528d-147">-AllVersions</span></span>

<span data-ttu-id="f528d-148">Indique que `Find-Package` retourne toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="f528d-148">Indicates that `Find-Package` returns all available versions of the package.</span></span> <span data-ttu-id="f528d-149">Par défaut, `Find-Package` retourne uniquement la version disponible la plus récente.</span><span class="sxs-lookup"><span data-stu-id="f528d-149">By default, `Find-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="f528d-150">-Command</span><span class="sxs-lookup"><span data-stu-id="f528d-150">-Command</span></span>

<span data-ttu-id="f528d-151">Spécifie un tableau de commandes recherchées par `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="f528d-151">Specifies an array of commands searched by `Find-Package`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f528d-152">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="f528d-152">-ConfigFile</span></span>

<span data-ttu-id="f528d-153">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f528d-153">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="f528d-154">-Contient</span><span class="sxs-lookup"><span data-stu-id="f528d-154">-Contains</span></span>

<span data-ttu-id="f528d-155">`Find-Package` obtient des objets si un élément dans les valeurs de propriété de l’objet correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f528d-155">`Find-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

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

### <span data-ttu-id="f528d-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="f528d-156">-Credential</span></span>

<span data-ttu-id="f528d-157">Spécifie un compte d’utilisateur qui a l’autorisation de rechercher des packages.</span><span class="sxs-lookup"><span data-stu-id="f528d-157">Specifies a user account that has permission to search for packages.</span></span>

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

### <span data-ttu-id="f528d-158">-DscResource</span><span class="sxs-lookup"><span data-stu-id="f528d-158">-DscResource</span></span>

<span data-ttu-id="f528d-159">Spécifie un tableau des ressources de configuration d’état souhaité (DSC) que cette applet de commande recherche.</span><span class="sxs-lookup"><span data-stu-id="f528d-159">Specifies an array of Desired State Configuration (DSC) resources that this cmdlet searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f528d-160">-Filter</span><span class="sxs-lookup"><span data-stu-id="f528d-160">-Filter</span></span>

<span data-ttu-id="f528d-161">Spécifie les termes à rechercher dans les propriétés **Name** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="f528d-161">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="f528d-162">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="f528d-162">-FilterOnTag</span></span>

<span data-ttu-id="f528d-163">Spécifie la balise qui filtre les résultats.</span><span class="sxs-lookup"><span data-stu-id="f528d-163">Specifies the tag that filters the results.</span></span> <span data-ttu-id="f528d-164">Les résultats qui ne contiennent pas la balise spécifiée sont exclus.</span><span class="sxs-lookup"><span data-stu-id="f528d-164">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f528d-165">-Force</span><span class="sxs-lookup"><span data-stu-id="f528d-165">-Force</span></span>

<span data-ttu-id="f528d-166">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f528d-166">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f528d-167">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="f528d-167">-ForceBootstrap</span></span>

<span data-ttu-id="f528d-168">Indique que `Find-Package` impose l’installation automatique du fournisseur de package par **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="f528d-168">Indicates that `Find-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="f528d-169">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="f528d-169">-Headers</span></span>

<span data-ttu-id="f528d-170">Spécifie les en-têtes pour le package.</span><span class="sxs-lookup"><span data-stu-id="f528d-170">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f528d-171">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="f528d-171">-IncludeDependencies</span></span>

<span data-ttu-id="f528d-172">Indique que cette applet de commande comprend les dépendances de package dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="f528d-172">Indicates that this cmdlet includes package dependencies in the results.</span></span>

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

### <span data-ttu-id="f528d-173">-Comprend</span><span class="sxs-lookup"><span data-stu-id="f528d-173">-Includes</span></span>

<span data-ttu-id="f528d-174">Spécifie si `Find-Package` tous les packages doivent être détectés dans une catégorie.</span><span class="sxs-lookup"><span data-stu-id="f528d-174">Specifies whether `Find-Package` should find all packages within a category.</span></span>

<span data-ttu-id="f528d-175">Les valeurs acceptées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f528d-175">The accepted values are as follows:</span></span>

- <span data-ttu-id="f528d-176">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="f528d-176">Cmdlet</span></span>
- <span data-ttu-id="f528d-177">DscResource</span><span class="sxs-lookup"><span data-stu-id="f528d-177">DscResource</span></span>
- <span data-ttu-id="f528d-178">Fonction</span><span class="sxs-lookup"><span data-stu-id="f528d-178">Function</span></span>
- <span data-ttu-id="f528d-179">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="f528d-179">RoleCapability</span></span>
- <span data-ttu-id="f528d-180">Workflow</span><span class="sxs-lookup"><span data-stu-id="f528d-180">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f528d-181">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f528d-181">-MaximumVersion</span></span>

<span data-ttu-id="f528d-182">Spécifie la version de package maximale que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="f528d-182">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="f528d-183">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f528d-183">-MinimumVersion</span></span>

<span data-ttu-id="f528d-184">Spécifie la version minimale du package que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="f528d-184">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="f528d-185">Si une version plus récente est disponible, cette version est retournée.</span><span class="sxs-lookup"><span data-stu-id="f528d-185">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="f528d-186">-Name</span><span class="sxs-lookup"><span data-stu-id="f528d-186">-Name</span></span>

<span data-ttu-id="f528d-187">Spécifie un ou plusieurs noms de packages, ou des noms de package avec des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="f528d-187">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="f528d-188">Séparez plusieurs noms de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f528d-188">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="f528d-189">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="f528d-189">-PackageManagementProvider</span></span>

<span data-ttu-id="f528d-190">Spécifie le nom d’un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="f528d-190">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="f528d-191">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="f528d-191">-ProviderName</span></span>

<span data-ttu-id="f528d-192">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="f528d-192">Specifies one or more package provider names.</span></span> <span data-ttu-id="f528d-193">Séparez les noms de plusieurs fournisseurs de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f528d-193">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="f528d-194">Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.</span><span class="sxs-lookup"><span data-stu-id="f528d-194">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="f528d-195">-Proxy</span><span class="sxs-lookup"><span data-stu-id="f528d-195">-Proxy</span></span>

<span data-ttu-id="f528d-196">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="f528d-196">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="f528d-197">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="f528d-197">-ProxyCredential</span></span>

<span data-ttu-id="f528d-198">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="f528d-198">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="f528d-199">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="f528d-199">-PublishLocation</span></span>

<span data-ttu-id="f528d-200">Spécifie un emplacement pour la publication du package.</span><span class="sxs-lookup"><span data-stu-id="f528d-200">Specifies a location for publishing the package.</span></span>

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

### <span data-ttu-id="f528d-201">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f528d-201">-RequiredVersion</span></span>

<span data-ttu-id="f528d-202">Spécifie la version exacte du package que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="f528d-202">Specifies an exact package version that you want to find.</span></span>

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

### <span data-ttu-id="f528d-203">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="f528d-203">-RoleCapability</span></span>

<span data-ttu-id="f528d-204">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="f528d-204">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f528d-205">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="f528d-205">-ScriptPublishLocation</span></span>

<span data-ttu-id="f528d-206">Spécifie un emplacement de publication de script pour le package.</span><span class="sxs-lookup"><span data-stu-id="f528d-206">Specifies a script publishing location for the package.</span></span>

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

### <span data-ttu-id="f528d-207">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="f528d-207">-ScriptSourceLocation</span></span>

<span data-ttu-id="f528d-208">Spécifie un emplacement source de script.</span><span class="sxs-lookup"><span data-stu-id="f528d-208">Specifies a script source location.</span></span>

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

### <span data-ttu-id="f528d-209">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="f528d-209">-SkipValidate</span></span>

<span data-ttu-id="f528d-210">Commutateur qui ignore la validation des informations d’identification du package.</span><span class="sxs-lookup"><span data-stu-id="f528d-210">Switch that skips package credential validation.</span></span>

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

### <span data-ttu-id="f528d-211">-Source</span><span class="sxs-lookup"><span data-stu-id="f528d-211">-Source</span></span>

<span data-ttu-id="f528d-212">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="f528d-212">Specifies one or more package sources.</span></span> <span data-ttu-id="f528d-213">Utilisez `Get-PackageSource` pour obtenir la liste des sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="f528d-213">Use `Get-PackageSource` to get a list of available package sources.</span></span> <span data-ttu-id="f528d-214">Un répertoire de système de fichiers peut être utilisé comme source pour les packages de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="f528d-214">A file system directory can be used as a source for download packages.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f528d-215">-Tag</span><span class="sxs-lookup"><span data-stu-id="f528d-215">-Tag</span></span>

<span data-ttu-id="f528d-216">Spécifie une ou plusieurs chaînes à rechercher dans les métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="f528d-216">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f528d-217">-Type</span><span class="sxs-lookup"><span data-stu-id="f528d-217">-Type</span></span>

<span data-ttu-id="f528d-218">Spécifie s’il faut rechercher des packages à l’aide d’un module, d’un script ou de l’un ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="f528d-218">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="f528d-219">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f528d-219">CommonParameters</span></span>

<span data-ttu-id="f528d-220">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f528d-220">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f528d-221">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f528d-221">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f528d-222">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f528d-222">INPUTS</span></span>

### <span data-ttu-id="f528d-223">None</span><span class="sxs-lookup"><span data-stu-id="f528d-223">None</span></span>

<span data-ttu-id="f528d-224">`Find-Package` n’accepte pas d’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="f528d-224">`Find-Package` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="f528d-225">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f528d-225">OUTPUTS</span></span>

### <span data-ttu-id="f528d-226">SoftwareIdentify[]</span><span class="sxs-lookup"><span data-stu-id="f528d-226">SoftwareIdentify[]</span></span>

<span data-ttu-id="f528d-227">`Find-Package` génère un objet **SoftwareIdentity** .</span><span class="sxs-lookup"><span data-stu-id="f528d-227">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

## <span data-ttu-id="f528d-228">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f528d-228">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f528d-229">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="f528d-229">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="f528d-230">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="f528d-230">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="f528d-231">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="f528d-231">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="f528d-232">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f528d-232">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="f528d-233">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f528d-233">RELATED LINKS</span></span>

[<span data-ttu-id="f528d-234">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="f528d-234">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="f528d-235">Get-Package</span><span class="sxs-lookup"><span data-stu-id="f528d-235">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="f528d-236">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="f528d-236">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="f528d-237">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f528d-237">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="f528d-238">Install-Package</span><span class="sxs-lookup"><span data-stu-id="f528d-238">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="f528d-239">Save-Package</span><span class="sxs-lookup"><span data-stu-id="f528d-239">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="f528d-240">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="f528d-240">Uninstall-Package</span></span>](Uninstall-Package.md)
