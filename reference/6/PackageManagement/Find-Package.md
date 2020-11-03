---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Package
ms.openlocfilehash: 686efa1a1d0cad008c9581cc8507a4549582b2b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203733"
---
# <span data-ttu-id="e1adc-103">Find-Package</span><span class="sxs-lookup"><span data-stu-id="e1adc-103">Find-Package</span></span>

## <span data-ttu-id="e1adc-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e1adc-104">SYNOPSIS</span></span>
<span data-ttu-id="e1adc-105">Recherche les packages de logiciels dans les sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="e1adc-105">Finds software packages in available package sources.</span></span>

## <span data-ttu-id="e1adc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1adc-106">SYNTAX</span></span>

### <span data-ttu-id="e1adc-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="e1adc-107">NuGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>]
 [-FilterOnTag <String[]>] [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="e1adc-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e1adc-108">PowerShellGet</span></span>

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

## <span data-ttu-id="e1adc-109">Description</span><span class="sxs-lookup"><span data-stu-id="e1adc-109">DESCRIPTION</span></span>

<span data-ttu-id="e1adc-110">`Find-Package` recherche les packages de logiciels qui sont disponibles dans les sources de package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-110">`Find-Package` finds software packages that are available in package sources.</span></span> <span data-ttu-id="e1adc-111">`Get-PackageProvider` et `Get-PackageSource` Affichez des détails sur vos fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="e1adc-111">`Get-PackageProvider` and `Get-PackageSource` display details about your providers.</span></span>

## <span data-ttu-id="e1adc-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e1adc-112">EXAMPLES</span></span>

### <span data-ttu-id="e1adc-113">Exemple 1 : Rechercher tous les packages disponibles à partir d’un fournisseur de package</span><span class="sxs-lookup"><span data-stu-id="e1adc-113">Example 1: Find all available packages from a package provider</span></span>

<span data-ttu-id="e1adc-114">Cette commande recherche tous les packages de modules PowerShell disponibles dans une galerie inscrite.</span><span class="sxs-lookup"><span data-stu-id="e1adc-114">This command finds all available PowerShell module packages in a registered gallery.</span></span> <span data-ttu-id="e1adc-115">Utilisez `Get-PackageProvider` pour récupérer le nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e1adc-115">Use `Get-PackageProvider` to get the provider name.</span></span>

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

<span data-ttu-id="e1adc-116">`Find-Package` utilise le paramètre **Provider** pour spécifier le **NuGet** du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e1adc-116">`Find-Package` uses the **Provider** parameter to specify the provider **NuGet** .</span></span>

### <span data-ttu-id="e1adc-117">Exemple 2 : Rechercher un package à partir d’une source de package</span><span class="sxs-lookup"><span data-stu-id="e1adc-117">Example 2: Find a package from a package source</span></span>

<span data-ttu-id="e1adc-118">Cette commande recherche la version la plus récente d’un package à partir d’une source de package spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e1adc-118">This command finds the newest version of a package from a specified package source.</span></span> <span data-ttu-id="e1adc-119">Si aucune source de package n’est fournie, `Find-Package` effectue une recherche dans chaque fournisseur de package installé et ses sources de package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-119">If a package source isn't provided, `Find-Package` searches each installed package provider and its package sources.</span></span> <span data-ttu-id="e1adc-120">Utilisez `Get-PackageSource` pour récupérer le nom de la source.</span><span class="sxs-lookup"><span data-stu-id="e1adc-120">Use `Get-PackageSource` to get the source name.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet
```

```Output
Name         Version   Source    Summary
----         -------   ------    -------
NuGet.Core   2.14.0    MyNuGet   NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="e1adc-121">`Find-Package` utilise le paramètre **Name** pour spécifier le nom du package **NuGet. Core** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-121">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core** .</span></span> <span data-ttu-id="e1adc-122">Le paramètre **source** spécifie de rechercher le package dans **MyNuGet** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-122">The **Source** parameter specifies to search for the package in **MyNuGet** .</span></span>

### <span data-ttu-id="e1adc-123">Exemple 3 : Rechercher toutes les versions d’un package</span><span class="sxs-lookup"><span data-stu-id="e1adc-123">Example 3: Find all versions of a package</span></span>

<span data-ttu-id="e1adc-124">Cette commande recherche toutes les versions de package disponibles à partir d’un fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="e1adc-124">This command finds all available package versions from a specified provider.</span></span>

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

<span data-ttu-id="e1adc-125">`Find-Package` utilise le paramètre **Name** pour spécifier le package **NuGet. Core** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-125">`Find-Package` uses the **Name** parameter to specify the package **NuGet.Core** .</span></span> <span data-ttu-id="e1adc-126">Le paramètre **providerName** spécifie la recherche du package dans **MyNuGet** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-126">The **ProviderName** parameter specifies to search for the package in **MyNuGet** .</span></span> <span data-ttu-id="e1adc-127">**AllVersions** spécifie que toutes les versions disponibles sont retournées.</span><span class="sxs-lookup"><span data-stu-id="e1adc-127">**AllVersions** specifies that all available versions are returned.</span></span>

### <span data-ttu-id="e1adc-128">Exemple 4 : Rechercher un package avec un nom et une version spécifiques</span><span class="sxs-lookup"><span data-stu-id="e1adc-128">Example 4: Find a package with a specific name and version</span></span>

<span data-ttu-id="e1adc-129">Cette commande recherche une version de package spécifique à partir d’un fournisseur spécifié.</span><span class="sxs-lookup"><span data-stu-id="e1adc-129">This command finds a specific package version from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -RequiredVersion 2.9.0
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="e1adc-130">`Find-Package` utilise le paramètre **Name** pour spécifier le nom du package **NuGet. Core** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-130">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core** .</span></span> <span data-ttu-id="e1adc-131">Le paramètre **providerName** spécifie la recherche du package dans **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-131">The **ProviderName** parameter specifies to search for the package in **NuGet** .</span></span> <span data-ttu-id="e1adc-132">**RequiredVersion** spécifie que seule la version **2.9.0** est retournée.</span><span class="sxs-lookup"><span data-stu-id="e1adc-132">**RequiredVersion** specifies that only version **2.9.0** is returned.</span></span>

### <span data-ttu-id="e1adc-133">Exemple 5 : Rechercher des packages dans une plage de versions</span><span class="sxs-lookup"><span data-stu-id="e1adc-133">Example 5: Find packages within a range of versions</span></span>

<span data-ttu-id="e1adc-134">Cette commande recherche une plage de versions pour un package spécifié.</span><span class="sxs-lookup"><span data-stu-id="e1adc-134">This command finds a range of versions for a specified package.</span></span>

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

<span data-ttu-id="e1adc-135">`Find-Package` utilise le paramètre **Name** pour spécifier le nom du package **NuGet. Core** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-135">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core** .</span></span> <span data-ttu-id="e1adc-136">Le paramètre **providerName** spécifie la recherche du package dans **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-136">The **ProviderName** parameter specifies to search for the package in **NuGet** .</span></span> <span data-ttu-id="e1adc-137">**MinimumVersion** spécifie la version la plus basse **2.7.0** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-137">**MinimumVersion** specifies the lowest version **2.7.0** .</span></span> <span data-ttu-id="e1adc-138">**MaximumVersion** spécifie la version la plus récente **2.9.0** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-138">**MaximumVersion** specifies the highest version **2.9.0** .</span></span>
<span data-ttu-id="e1adc-139">**AllVersions** détermine que la plage est retournée comme spécifié par les valeurs minimale et maximale.</span><span class="sxs-lookup"><span data-stu-id="e1adc-139">**AllVersions** determines the range is returned as specified by the minimum and maximum.</span></span>

### <span data-ttu-id="e1adc-140">Exemple 6 : Rechercher un package à partir d’un système de fichiers</span><span class="sxs-lookup"><span data-stu-id="e1adc-140">Example 6: Find a package from a file system</span></span>

<span data-ttu-id="e1adc-141">Cette commande recherche les packages dont l’extension de fichier `.nupkg` est stockée sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e1adc-141">This command finds packages with the file extension `.nupkg` that are stored on the local computer.</span></span>
<span data-ttu-id="e1adc-142">Les fichiers sont des packages téléchargés à partir d’une galerie telle que **NuGet** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-142">The files are packages downloaded from a gallery such as the **NuGet** .</span></span>

```
PS> Find-Package -Source C:\LocalPkg
```

```Output
Name                 Version    Source           Summary
----                 -------    ------           -------
Microsoft.Web.Xdt    3.0.0      C:\LocalPkg\     Microsoft Xml Document Transformation (XDT)...
NuGet.Core           2.14.0     C:\LocalPkg\     NuGet.Core is the core framework assembly...
```

## <span data-ttu-id="e1adc-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1adc-143">PARAMETERS</span></span>

### <span data-ttu-id="e1adc-144">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="e1adc-144">-AcceptLicense</span></span>

<span data-ttu-id="e1adc-145">Accepte automatiquement un contrat de licence si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="e1adc-145">Automatically accepts a license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="e1adc-146">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="e1adc-146">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="e1adc-147">Comprend les packages marqués comme version préliminaire dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="e1adc-147">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="e1adc-148">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="e1adc-148">-AllVersions</span></span>

<span data-ttu-id="e1adc-149">Indique que `Find-Package` retourne toutes les versions disponibles du package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-149">Indicates that `Find-Package` returns all available versions of the package.</span></span> <span data-ttu-id="e1adc-150">Par défaut, `Find-Package` retourne uniquement la version disponible la plus récente.</span><span class="sxs-lookup"><span data-stu-id="e1adc-150">By default, `Find-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="e1adc-151">-Command</span><span class="sxs-lookup"><span data-stu-id="e1adc-151">-Command</span></span>

<span data-ttu-id="e1adc-152">Spécifie un tableau de commandes recherchées par `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="e1adc-152">Specifies an array of commands searched by `Find-Package`.</span></span>

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

### <span data-ttu-id="e1adc-153">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="e1adc-153">-ConfigFile</span></span>

<span data-ttu-id="e1adc-154">Spécifie un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e1adc-154">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="e1adc-155">-Contient</span><span class="sxs-lookup"><span data-stu-id="e1adc-155">-Contains</span></span>

<span data-ttu-id="e1adc-156">`Find-Package` obtient des objets si un élément dans les valeurs de propriété de l’objet correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e1adc-156">`Find-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

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

### <span data-ttu-id="e1adc-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="e1adc-157">-Credential</span></span>

<span data-ttu-id="e1adc-158">Spécifie un compte d’utilisateur qui a l’autorisation de rechercher des packages.</span><span class="sxs-lookup"><span data-stu-id="e1adc-158">Specifies a user account that has permission to search for packages.</span></span>

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

### <span data-ttu-id="e1adc-159">-DscResource</span><span class="sxs-lookup"><span data-stu-id="e1adc-159">-DscResource</span></span>

<span data-ttu-id="e1adc-160">Spécifie un tableau des ressources de configuration d’état souhaité (DSC) que cette applet de commande recherche.</span><span class="sxs-lookup"><span data-stu-id="e1adc-160">Specifies an array of Desired State Configuration (DSC) resources that this cmdlet searches.</span></span>

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

### <span data-ttu-id="e1adc-161">-Filter</span><span class="sxs-lookup"><span data-stu-id="e1adc-161">-Filter</span></span>

<span data-ttu-id="e1adc-162">Spécifie les termes à rechercher dans les propriétés **Name** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-162">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="e1adc-163">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="e1adc-163">-FilterOnTag</span></span>

<span data-ttu-id="e1adc-164">Spécifie la balise qui filtre les résultats.</span><span class="sxs-lookup"><span data-stu-id="e1adc-164">Specifies the tag that filters the results.</span></span> <span data-ttu-id="e1adc-165">Les résultats qui ne contiennent pas la balise spécifiée sont exclus.</span><span class="sxs-lookup"><span data-stu-id="e1adc-165">Results that don't contain the specified tag are excluded.</span></span>

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

### <span data-ttu-id="e1adc-166">-Force</span><span class="sxs-lookup"><span data-stu-id="e1adc-166">-Force</span></span>

<span data-ttu-id="e1adc-167">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e1adc-167">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e1adc-168">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="e1adc-168">-ForceBootstrap</span></span>

<span data-ttu-id="e1adc-169">Indique que `Find-Package` impose l’installation automatique du fournisseur de package par **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-169">Indicates that `Find-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="e1adc-170">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="e1adc-170">-Headers</span></span>

<span data-ttu-id="e1adc-171">Spécifie les en-têtes pour le package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-171">Specifies the headers for the package.</span></span>

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

### <span data-ttu-id="e1adc-172">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="e1adc-172">-IncludeDependencies</span></span>

<span data-ttu-id="e1adc-173">Indique que cette applet de commande comprend les dépendances de package dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="e1adc-173">Indicates that this cmdlet includes package dependencies in the results.</span></span>

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

### <span data-ttu-id="e1adc-174">-Comprend</span><span class="sxs-lookup"><span data-stu-id="e1adc-174">-Includes</span></span>

<span data-ttu-id="e1adc-175">Spécifie si `Find-Package` tous les packages doivent être détectés dans une catégorie.</span><span class="sxs-lookup"><span data-stu-id="e1adc-175">Specifies whether `Find-Package` should find all packages within a category.</span></span>

<span data-ttu-id="e1adc-176">Les valeurs acceptées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1adc-176">The accepted values are as follows:</span></span>

- <span data-ttu-id="e1adc-177">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="e1adc-177">Cmdlet</span></span>
- <span data-ttu-id="e1adc-178">DscResource</span><span class="sxs-lookup"><span data-stu-id="e1adc-178">DscResource</span></span>
- <span data-ttu-id="e1adc-179">Fonction</span><span class="sxs-lookup"><span data-stu-id="e1adc-179">Function</span></span>
- <span data-ttu-id="e1adc-180">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e1adc-180">RoleCapability</span></span>
- <span data-ttu-id="e1adc-181">Workflow</span><span class="sxs-lookup"><span data-stu-id="e1adc-181">Workflow</span></span>

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

### <span data-ttu-id="e1adc-182">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e1adc-182">-MaximumVersion</span></span>

<span data-ttu-id="e1adc-183">Spécifie la version de package maximale que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="e1adc-183">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="e1adc-184">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e1adc-184">-MinimumVersion</span></span>

<span data-ttu-id="e1adc-185">Spécifie la version minimale du package que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="e1adc-185">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="e1adc-186">Si une version plus récente est disponible, cette version est retournée.</span><span class="sxs-lookup"><span data-stu-id="e1adc-186">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="e1adc-187">-Name</span><span class="sxs-lookup"><span data-stu-id="e1adc-187">-Name</span></span>

<span data-ttu-id="e1adc-188">Spécifie un ou plusieurs noms de packages, ou des noms de package avec des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="e1adc-188">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="e1adc-189">Séparez plusieurs noms de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="e1adc-189">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="e1adc-190">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="e1adc-190">-PackageManagementProvider</span></span>

<span data-ttu-id="e1adc-191">Spécifie le nom d’un fournisseur de gestion des packages.</span><span class="sxs-lookup"><span data-stu-id="e1adc-191">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="e1adc-192">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="e1adc-192">-ProviderName</span></span>

<span data-ttu-id="e1adc-193">Spécifie un ou plusieurs noms de fournisseurs de packages.</span><span class="sxs-lookup"><span data-stu-id="e1adc-193">Specifies one or more package provider names.</span></span> <span data-ttu-id="e1adc-194">Séparez les noms de plusieurs fournisseurs de packages par des virgules.</span><span class="sxs-lookup"><span data-stu-id="e1adc-194">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="e1adc-195">Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.</span><span class="sxs-lookup"><span data-stu-id="e1adc-195">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="e1adc-196">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e1adc-196">-Proxy</span></span>

<span data-ttu-id="e1adc-197">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="e1adc-197">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="e1adc-198">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e1adc-198">-ProxyCredential</span></span>

<span data-ttu-id="e1adc-199">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-199">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="e1adc-200">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="e1adc-200">-PublishLocation</span></span>

<span data-ttu-id="e1adc-201">Spécifie un emplacement pour la publication du package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-201">Specifies a location for publishing the package.</span></span>

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

### <span data-ttu-id="e1adc-202">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e1adc-202">-RequiredVersion</span></span>

<span data-ttu-id="e1adc-203">Spécifie la version exacte du package que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="e1adc-203">Specifies an exact package version that you want to find.</span></span>

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

### <span data-ttu-id="e1adc-204">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e1adc-204">-RoleCapability</span></span>

<span data-ttu-id="e1adc-205">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="e1adc-205">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="e1adc-206">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="e1adc-206">-ScriptPublishLocation</span></span>

<span data-ttu-id="e1adc-207">Spécifie un emplacement de publication de script pour le package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-207">Specifies a script publishing location for the package.</span></span>

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

### <span data-ttu-id="e1adc-208">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="e1adc-208">-ScriptSourceLocation</span></span>

<span data-ttu-id="e1adc-209">Spécifie un emplacement source de script.</span><span class="sxs-lookup"><span data-stu-id="e1adc-209">Specifies a script source location.</span></span>

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

### <span data-ttu-id="e1adc-210">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="e1adc-210">-SkipValidate</span></span>

<span data-ttu-id="e1adc-211">Commutateur qui ignore la validation des informations d’identification du package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-211">Switch that skips package credential validation.</span></span>

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

### <span data-ttu-id="e1adc-212">-Source</span><span class="sxs-lookup"><span data-stu-id="e1adc-212">-Source</span></span>

<span data-ttu-id="e1adc-213">Spécifie une ou plusieurs sources de package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-213">Specifies one or more package sources.</span></span> <span data-ttu-id="e1adc-214">Utilisez `Get-PackageSource` pour obtenir la liste des sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="e1adc-214">Use `Get-PackageSource` to get a list of available package sources.</span></span> <span data-ttu-id="e1adc-215">Un répertoire de système de fichiers peut être utilisé comme source pour les packages de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="e1adc-215">A file system directory can be used as a source for download packages.</span></span>

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

### <span data-ttu-id="e1adc-216">-Tag</span><span class="sxs-lookup"><span data-stu-id="e1adc-216">-Tag</span></span>

<span data-ttu-id="e1adc-217">Spécifie une ou plusieurs chaînes à rechercher dans les métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="e1adc-217">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="e1adc-218">-Type</span><span class="sxs-lookup"><span data-stu-id="e1adc-218">-Type</span></span>

<span data-ttu-id="e1adc-219">Spécifie s’il faut rechercher des packages à l’aide d’un module, d’un script ou de l’un ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="e1adc-219">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="e1adc-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1adc-220">CommonParameters</span></span>

<span data-ttu-id="e1adc-221">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e1adc-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1adc-222">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e1adc-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1adc-223">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e1adc-223">INPUTS</span></span>

### <span data-ttu-id="e1adc-224">Aucun</span><span class="sxs-lookup"><span data-stu-id="e1adc-224">None</span></span>

<span data-ttu-id="e1adc-225">`Find-Package` n’accepte pas d’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="e1adc-225">`Find-Package` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="e1adc-226">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e1adc-226">OUTPUTS</span></span>

### <span data-ttu-id="e1adc-227">SoftwareIdentify[]</span><span class="sxs-lookup"><span data-stu-id="e1adc-227">SoftwareIdentify[]</span></span>

<span data-ttu-id="e1adc-228">`Find-Package` génère un objet **SoftwareIdentity** .</span><span class="sxs-lookup"><span data-stu-id="e1adc-228">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

## <span data-ttu-id="e1adc-229">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e1adc-229">NOTES</span></span>

## <span data-ttu-id="e1adc-230">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e1adc-230">RELATED LINKS</span></span>

[<span data-ttu-id="e1adc-231">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e1adc-231">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="e1adc-232">Get-Package</span><span class="sxs-lookup"><span data-stu-id="e1adc-232">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="e1adc-233">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e1adc-233">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="e1adc-234">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e1adc-234">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="e1adc-235">Install-Package</span><span class="sxs-lookup"><span data-stu-id="e1adc-235">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="e1adc-236">Save-Package</span><span class="sxs-lookup"><span data-stu-id="e1adc-236">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="e1adc-237">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="e1adc-237">Uninstall-Package</span></span>](Uninstall-Package.md)
