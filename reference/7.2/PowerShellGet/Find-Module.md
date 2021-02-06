---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: f9cba90ffa69d04df196f4062c8f190d545b9bc3
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598978"
---
# <span data-ttu-id="27b2d-102">Find-Module</span><span class="sxs-lookup"><span data-stu-id="27b2d-102">Find-Module</span></span>

## <span data-ttu-id="27b2d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="27b2d-103">SYNOPSIS</span></span>
<span data-ttu-id="27b2d-104">Recherche les modules dans un référentiel qui correspondent aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="27b2d-104">Finds modules in a repository that match specified criteria.</span></span>

## <span data-ttu-id="27b2d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="27b2d-105">SYNTAX</span></span>

### <span data-ttu-id="27b2d-106">Tous</span><span class="sxs-lookup"><span data-stu-id="27b2d-106">All</span></span>

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="27b2d-107">Description</span><span class="sxs-lookup"><span data-stu-id="27b2d-107">DESCRIPTION</span></span>

<span data-ttu-id="27b2d-108">L' `Find-Module` applet de commande recherche les modules dans un référentiel qui correspondent aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="27b2d-108">The `Find-Module` cmdlet finds modules in a repository that match the specified criteria.</span></span>
<span data-ttu-id="27b2d-109">`Find-Module` retourne un objet **PSRepositoryItemInfo** pour chaque module qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="27b2d-109">`Find-Module` returns a **PSRepositoryItemInfo** object for each module it finds.</span></span> <span data-ttu-id="27b2d-110">Les objets peuvent être envoyés vers le pipeline vers des applets de commande telles que `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="27b2d-110">The objects can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

<span data-ttu-id="27b2d-111">La première fois `Find-Module` que vous tentez d’utiliser un référentiel, vous pouvez être invité à installer les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="27b2d-111">The first time `Find-Module` attempts to use a repository, you might be prompted to install updates.</span></span>
<span data-ttu-id="27b2d-112">Si la source du référentiel n’est pas inscrite auprès de l’applet de commande `Register-PSRepository` , une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="27b2d-112">If the repository source is not registered with `Register-PSRepository` cmdlet, an error is returned.</span></span>

<span data-ttu-id="27b2d-113">`Find-Module` retourne la version la plus récente d’un module si aucun paramètre n’est utilisé pour limiter la version.</span><span class="sxs-lookup"><span data-stu-id="27b2d-113">`Find-Module` returns the newest version of a module if no parameters are used that limit the version.</span></span> <span data-ttu-id="27b2d-114">Pour obtenir la liste des versions d’un module dans un référentiel, utilisez le paramètre **AllVersions**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-114">To get a repository's list of a module's versions, use the parameter **AllVersions**.</span></span>

<span data-ttu-id="27b2d-115">Si le paramètre **MinimumVersion** est spécifié, `Find-Module` retourne la version du module qui est supérieure ou égale à la valeur minimale.</span><span class="sxs-lookup"><span data-stu-id="27b2d-115">If the **MinimumVersion** parameter is specified, `Find-Module` returns the module's version that is equal to or greater than the minimum.</span></span> <span data-ttu-id="27b2d-116">Si une version plus récente est disponible dans le référentiel, la version la plus récente est retournée.</span><span class="sxs-lookup"><span data-stu-id="27b2d-116">If there is a newer version available in the repository, the newer version is returned.</span></span>

<span data-ttu-id="27b2d-117">Si le paramètre **MaximumVersion** est spécifié, `Find-Module` retourne la version la plus récente du module qui ne dépasse pas la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="27b2d-117">If the **MaximumVersion** parameter is specified, `Find-Module` returns the newest version of the module that does not exceed the version specified.</span></span>

<span data-ttu-id="27b2d-118">Si le paramètre **RequiredVersion** est spécifié, `Find-Module` retourne uniquement la version du module qui correspond exactement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="27b2d-118">If the **RequiredVersion** parameter is specified, `Find-Module` only returns the module version that is an exact match to the specified version.</span></span> <span data-ttu-id="27b2d-119">`Find-Module` effectue une recherche dans tous les modules disponibles, car des conflits de noms entre les sources peuvent se produire.</span><span class="sxs-lookup"><span data-stu-id="27b2d-119">`Find-Module` searches through all available modules, because name conflicts between sources can occur.</span></span>

<span data-ttu-id="27b2d-120">Les exemples suivants utilisent l' [PowerShell Gallery](https://www.powershellgallery.com/) comme seul référentiel enregistré.</span><span class="sxs-lookup"><span data-stu-id="27b2d-120">The following examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="27b2d-121">`Get-PSRepository` affiche les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="27b2d-121">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="27b2d-122">Si vous avez plusieurs référentiels inscrits, utilisez le `-Repository` paramètre pour spécifier le nom du référentiel.</span><span class="sxs-lookup"><span data-stu-id="27b2d-122">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="27b2d-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="27b2d-123">EXAMPLES</span></span>

### <span data-ttu-id="27b2d-124">Exemple 1 : Rechercher un module par son nom</span><span class="sxs-lookup"><span data-stu-id="27b2d-124">Example 1: Find a module by name</span></span>

<span data-ttu-id="27b2d-125">Cet exemple recherche un module dans le référentiel par défaut.</span><span class="sxs-lookup"><span data-stu-id="27b2d-125">This example finds a module in the default repository.</span></span>

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

<span data-ttu-id="27b2d-126">L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-126">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>

### <span data-ttu-id="27b2d-127">Exemple 2 : Rechercher les modules avec des noms similaires</span><span class="sxs-lookup"><span data-stu-id="27b2d-127">Example 2: Find modules with similar names</span></span>

<span data-ttu-id="27b2d-128">Cet exemple utilise le `*` caractère générique astérisque () pour rechercher des modules avec des noms similaires.</span><span class="sxs-lookup"><span data-stu-id="27b2d-128">This example uses the asterisk (`*`) wildcard to find modules with similar names.</span></span>

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

<span data-ttu-id="27b2d-129">L' `Find-Module` applet de commande utilise le paramètre **Name** avec le `*` caractère générique astérisque () pour rechercher tous les modules qui contiennent **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-129">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to find all modules that contain **PowerShell**.</span></span>

### <span data-ttu-id="27b2d-130">Exemple 3 : Rechercher un module par version minimale</span><span class="sxs-lookup"><span data-stu-id="27b2d-130">Example 3: Find a module by minimum version</span></span>

<span data-ttu-id="27b2d-131">Cet exemple recherche la version minimale d’un module.</span><span class="sxs-lookup"><span data-stu-id="27b2d-131">This example searches for a module's minimum version.</span></span> <span data-ttu-id="27b2d-132">Si le référentiel contient une version plus récente du module, la version la plus récente est retournée.</span><span class="sxs-lookup"><span data-stu-id="27b2d-132">If the repository contains a newer version of the module, the newer version is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="27b2d-133">L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-133">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="27b2d-134">**MinimumVersion** spécifie la version **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-134">The **MinimumVersion** specifies version **1.6.5**.</span></span> <span data-ttu-id="27b2d-135">`Find-Module` retourne la version PowerShellGet **2.1.0** , car elle dépasse la version minimale et est la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="27b2d-135">`Find-Module` returns PowerShellGet version **2.1.0** because it exceeds the minimum version and is the most current version.</span></span>

### <span data-ttu-id="27b2d-136">Exemple 4 : Rechercher un module par version spécifique</span><span class="sxs-lookup"><span data-stu-id="27b2d-136">Example 4: Find a module by specific version</span></span>

<span data-ttu-id="27b2d-137">Cet exemple retourne un objet qui représente la version spécifique d’un module.</span><span class="sxs-lookup"><span data-stu-id="27b2d-137">This example returns an object that represents a module's specific version.</span></span> <span data-ttu-id="27b2d-138">Si la version spécifiée est introuvable, une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="27b2d-138">If the specified version is not found, an error is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="27b2d-139">L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-139">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="27b2d-140">Le paramètre **RequiredVersion** spécifie la version **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-140">The **RequiredVersion** parameter specifies version **1.6.5**.</span></span>

### <span data-ttu-id="27b2d-141">Exemple 5 : Rechercher un module dans un référentiel spécifique</span><span class="sxs-lookup"><span data-stu-id="27b2d-141">Example 5: Find a module in a specific repository</span></span>

<span data-ttu-id="27b2d-142">Cet exemple utilise le paramètre **repository** pour rechercher un module dans un référentiel spécifique.</span><span class="sxs-lookup"><span data-stu-id="27b2d-142">This example uses the **Repository** parameter to find a module in a specific repository.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="27b2d-143">L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-143">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="27b2d-144">Le paramètre de **dépôt** spécifie la recherche dans le référentiel **PSGallery** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-144">The **Repository** parameter specifies to search the **PSGallery** repository.</span></span>

### <span data-ttu-id="27b2d-145">Exemple 6 : Rechercher un module dans plusieurs référentiels</span><span class="sxs-lookup"><span data-stu-id="27b2d-145">Example 6: Find a module in multiple repositories</span></span>

<span data-ttu-id="27b2d-146">Cet exemple utilise `Register-PSRepository` pour spécifier un référentiel.</span><span class="sxs-lookup"><span data-stu-id="27b2d-146">This example uses the `Register-PSRepository` to specify a repository.</span></span> <span data-ttu-id="27b2d-147">`Find-Module` utilise le référentiel pour rechercher un module.</span><span class="sxs-lookup"><span data-stu-id="27b2d-147">`Find-Module` uses the repository to search for a module.</span></span>

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

<span data-ttu-id="27b2d-148">L' `Register-PSRepository` applet de commande inscrit un nouveau référentiel.</span><span class="sxs-lookup"><span data-stu-id="27b2d-148">The `Register-PSRepository` cmdlet registers a new repository.</span></span> <span data-ttu-id="27b2d-149">Le paramètre **Name** attribue le nom **MySource**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-149">The **Name** parameter assigns the name **MySource**.</span></span> <span data-ttu-id="27b2d-150">Le paramètre **SourceLocation** spécifie l’adresse du dépôt.</span><span class="sxs-lookup"><span data-stu-id="27b2d-150">The **SourceLocation** parameter specifies the repository's address.</span></span>

<span data-ttu-id="27b2d-151">L' `Find-Module` applet de commande utilise le paramètre **Name** avec le `*` caractère générique astérisque () pour spécifier le module **contoso** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-151">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to specify the **Contoso** module.</span></span> <span data-ttu-id="27b2d-152">Le paramètre de **dépôt** spécifie de rechercher deux dépôts, **PSGallery** et **MySource**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-152">The **Repository** parameter specifies to search two repositories, **PSGallery** and **MySource**.</span></span>

### <span data-ttu-id="27b2d-153">Exemple 7 : Rechercher un module qui contient une ressource DSC</span><span class="sxs-lookup"><span data-stu-id="27b2d-153">Example 7: Find a module that contains a DSC resource</span></span>

<span data-ttu-id="27b2d-154">Cette commande retourne les modules qui contiennent des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="27b2d-154">This command returns modules that contain DSC resources.</span></span> <span data-ttu-id="27b2d-155">Le paramètre **includes** possède quatre fonctionnalités prédéfinies utilisées pour effectuer des recherches dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="27b2d-155">The **Includes** parameter has four predefined functionalities that are used to search the repository.</span></span> <span data-ttu-id="27b2d-156">Utilisez l’onglet terminé pour afficher les quatre fonctionnalités prises en charge par le paramètre **includes** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-156">Use tab-complete to display the four functionalities supported by the **Includes** parameter.</span></span>

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

<span data-ttu-id="27b2d-157">L' `Find-Module` applet de commande utilise le paramètre de **référentiel** pour effectuer une recherche dans le référentiel, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-157">The `Find-Module` cmdlet uses the **Repository** parameter to search the repository, **PSGallery**.</span></span>
<span data-ttu-id="27b2d-158">Le paramètre **includes** spécifie **DscResource**, qui est une fonctionnalité que le paramètre peut rechercher dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="27b2d-158">The **Includes** parameter specifies **DscResource**, which is a functionality that the parameter can search for in the repository.</span></span>

### <span data-ttu-id="27b2d-159">Exemple 8 : Rechercher un module à l’aide d’un filtre</span><span class="sxs-lookup"><span data-stu-id="27b2d-159">Example 8: Find a module with a filter</span></span>

<span data-ttu-id="27b2d-160">Dans cet exemple, pour rechercher des modules, un filtre est utilisé pour effectuer une recherche dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="27b2d-160">In this example, to find modules, a filter is used to search the repository.</span></span>

<span data-ttu-id="27b2d-161">Pour un référentiel NuGet, le paramètre de **filtre** parcourt le nom, la description et les balises pour l’argument.</span><span class="sxs-lookup"><span data-stu-id="27b2d-161">For a NuGet-based repository, the **Filter** parameter searches through the name, description, and tags for the argument.</span></span>

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

<span data-ttu-id="27b2d-162">L' `Find-Module` applet de commande utilise le paramètre de **filtre** pour rechercher **AppDomain** dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="27b2d-162">The `Find-Module` cmdlet uses the **Filter** parameter to search the repository for **AppDomain**.</span></span>

## <span data-ttu-id="27b2d-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="27b2d-163">PARAMETERS</span></span>

### <span data-ttu-id="27b2d-164">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="27b2d-164">-AllowPrerelease</span></span>

<span data-ttu-id="27b2d-165">Comprend dans les modules de résultats marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="27b2d-165">Includes in the results modules marked as a pre-release.</span></span>

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

### <span data-ttu-id="27b2d-166">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="27b2d-166">-AllVersions</span></span>

<span data-ttu-id="27b2d-167">Spécifie d’inclure toutes les versions d’un module dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="27b2d-167">Specifies to include all versions of a module in the results.</span></span> <span data-ttu-id="27b2d-168">Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion**, **MaximumVersion** ou **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-168">You cannot use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="27b2d-169">-Command</span><span class="sxs-lookup"><span data-stu-id="27b2d-169">-Command</span></span>

<span data-ttu-id="27b2d-170">Spécifie un tableau de commandes à rechercher dans les modules.</span><span class="sxs-lookup"><span data-stu-id="27b2d-170">Specifies an array of commands to find in modules.</span></span> <span data-ttu-id="27b2d-171">Une commande peut être une fonction ou un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="27b2d-171">A command can be a function or workflow.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="27b2d-172">-Credential</span></span>

<span data-ttu-id="27b2d-173">Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour installer un module pour un fournisseur de package ou une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="27b2d-173">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-174">-DscResource</span><span class="sxs-lookup"><span data-stu-id="27b2d-174">-DscResource</span></span>

<span data-ttu-id="27b2d-175">Spécifie le nom ou une partie du nom des modules qui contiennent des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="27b2d-175">Specifies the name, or part of the name, of modules that contain DSC resources.</span></span> <span data-ttu-id="27b2d-176">Par conventions PowerShell, effectue une recherche **ou** lorsque vous fournissez plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="27b2d-176">Per PowerShell conventions, performs an **OR** search when you provide multiple arguments.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-177">-Filter</span><span class="sxs-lookup"><span data-stu-id="27b2d-177">-Filter</span></span>

<span data-ttu-id="27b2d-178">Spécifie un filtre basé sur la syntaxe de recherche spécifique au fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-178">Specifies a filter based on the **PackageManagement** provider-specific search syntax.</span></span> <span data-ttu-id="27b2d-179">Pour les modules NuGet, ce paramètre est l’équivalent de la recherche à l’aide de la barre de recherche sur le site Web [PowerShell Gallery](https://www.powershellgallery.com/) .</span><span class="sxs-lookup"><span data-stu-id="27b2d-179">For NuGet modules, this parameter is the equivalent of searching by using the Search bar on the [PowerShell Gallery](https://www.powershellgallery.com/) website.</span></span>

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

### <span data-ttu-id="27b2d-180">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="27b2d-180">-IncludeDependencies</span></span>

<span data-ttu-id="27b2d-181">Indique que cette opération comprend tous les modules qui dépendent du module spécifié dans le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="27b2d-181">Indicates that this operation includes all modules that are dependent upon the module specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="27b2d-182">-Comprend</span><span class="sxs-lookup"><span data-stu-id="27b2d-182">-Includes</span></span>

<span data-ttu-id="27b2d-183">Retourne uniquement les modules qui incluent des genres spécifiques de fonctionnalités PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27b2d-183">Returns only those modules that include specific kinds of PowerShell functionality.</span></span> <span data-ttu-id="27b2d-184">Par exemple, vous souhaiterez peut-être Rechercher uniquement les modules qui incluent **DSCResource**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-184">For example, you might only want to find modules that include **DSCResource**.</span></span> <span data-ttu-id="27b2d-185">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="27b2d-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="27b2d-186">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="27b2d-186">Cmdlet</span></span>
- <span data-ttu-id="27b2d-187">DscResource</span><span class="sxs-lookup"><span data-stu-id="27b2d-187">DscResource</span></span>
- <span data-ttu-id="27b2d-188">Fonction</span><span class="sxs-lookup"><span data-stu-id="27b2d-188">Function</span></span>
- <span data-ttu-id="27b2d-189">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="27b2d-189">RoleCapability</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-190">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="27b2d-190">-MaximumVersion</span></span>

<span data-ttu-id="27b2d-191">Spécifie la version maximale ou la plus récente du module à inclure dans les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="27b2d-191">Specifies the maximum, or latest, version of the module to include in the search results.</span></span>
<span data-ttu-id="27b2d-192">**MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="27b2d-192">**MaximumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-193">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="27b2d-193">-MinimumVersion</span></span>

<span data-ttu-id="27b2d-194">Spécifie la version minimale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="27b2d-194">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="27b2d-195">**MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="27b2d-195">**MinimumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-196">-Name</span><span class="sxs-lookup"><span data-stu-id="27b2d-196">-Name</span></span>

<span data-ttu-id="27b2d-197">Spécifie les noms des modules à rechercher dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="27b2d-197">Specifies the names of modules to search for in the repository.</span></span> <span data-ttu-id="27b2d-198">Une liste séparée par des virgules de noms de modules est acceptée.</span><span class="sxs-lookup"><span data-stu-id="27b2d-198">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="27b2d-199">Les caractères génériques sont acceptés.</span><span class="sxs-lookup"><span data-stu-id="27b2d-199">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-200">-Proxy</span><span class="sxs-lookup"><span data-stu-id="27b2d-200">-Proxy</span></span>

<span data-ttu-id="27b2d-201">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="27b2d-201">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-202">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="27b2d-202">-ProxyCredential</span></span>

<span data-ttu-id="27b2d-203">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-203">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-204">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="27b2d-204">-Repository</span></span>

<span data-ttu-id="27b2d-205">Utilisez le paramètre de **dépôt** pour spécifier le référentiel dans lequel Rechercher un module.</span><span class="sxs-lookup"><span data-stu-id="27b2d-205">Use the **Repository** parameter to specify which repository to search for a module.</span></span> <span data-ttu-id="27b2d-206">Utilisé lorsque plusieurs dépôts sont inscrits.</span><span class="sxs-lookup"><span data-stu-id="27b2d-206">Used when multiple repositories are registered.</span></span> <span data-ttu-id="27b2d-207">Accepte une liste de référentiels séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="27b2d-207">Accepts a comma-separated list of repositories.</span></span> <span data-ttu-id="27b2d-208">Pour inscrire un dépôt, utilisez `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="27b2d-208">To register a repository, use `Register-PSRepository`.</span></span> <span data-ttu-id="27b2d-209">Pour afficher les dépôts inscrits, utilisez `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="27b2d-209">To display registered repositories, use `Get-PSRepository`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-210">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="27b2d-210">-RequiredVersion</span></span>

<span data-ttu-id="27b2d-211">Spécifie le numéro de version exact du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="27b2d-211">Specifies the exact version number of the module to include in the results.</span></span> <span data-ttu-id="27b2d-212">**RequiredVersion** ne peut pas être utilisé dans la même commande que **MinimumVersion** ou **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-212">**RequiredVersion** cannot be used in the same command as **MinimumVersion** or **MaximumVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-213">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="27b2d-213">-RoleCapability</span></span>

<span data-ttu-id="27b2d-214">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="27b2d-214">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-215">-Tag</span><span class="sxs-lookup"><span data-stu-id="27b2d-215">-Tag</span></span>

<span data-ttu-id="27b2d-216">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="27b2d-216">Specifies an array of tags.</span></span> <span data-ttu-id="27b2d-217">Exemples de balises : **DesiredStateConfiguration**, **DSC**, **DSCResourceKit** ou **PSModule**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-217">Example tags include **DesiredStateConfiguration**, **DSC**, **DSCResourceKit**, or **PSModule**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27b2d-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27b2d-218">CommonParameters</span></span>

<span data-ttu-id="27b2d-219">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27b2d-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27b2d-220">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="27b2d-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27b2d-221">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="27b2d-221">INPUTS</span></span>

### <span data-ttu-id="27b2d-222">System.String[]</span><span class="sxs-lookup"><span data-stu-id="27b2d-222">System.String[]</span></span>

### <span data-ttu-id="27b2d-223">System.String</span><span class="sxs-lookup"><span data-stu-id="27b2d-223">System.String</span></span>

### <span data-ttu-id="27b2d-224">System.Uri</span><span class="sxs-lookup"><span data-stu-id="27b2d-224">System.Uri</span></span>

### <span data-ttu-id="27b2d-225">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="27b2d-225">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="27b2d-226">SORTIES</span><span class="sxs-lookup"><span data-stu-id="27b2d-226">OUTPUTS</span></span>

### <span data-ttu-id="27b2d-227">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="27b2d-227">PSRepositoryItemInfo</span></span>

<span data-ttu-id="27b2d-228">`Find-Module` crée des objets **PSRepositoryItemInfo** qui peuvent être envoyés vers le pipeline vers des applets de commande telles que `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="27b2d-228">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

## <span data-ttu-id="27b2d-229">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="27b2d-229">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27b2d-230">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="27b2d-230">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="27b2d-231">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="27b2d-231">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="27b2d-232">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="27b2d-232">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="27b2d-233">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27b2d-233">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="27b2d-234">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="27b2d-234">RELATED LINKS</span></span>

[<span data-ttu-id="27b2d-235">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="27b2d-235">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="27b2d-236">Install-Module</span><span class="sxs-lookup"><span data-stu-id="27b2d-236">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="27b2d-237">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="27b2d-237">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="27b2d-238">Save-Module</span><span class="sxs-lookup"><span data-stu-id="27b2d-238">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="27b2d-239">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="27b2d-239">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="27b2d-240">Update-Module</span><span class="sxs-lookup"><span data-stu-id="27b2d-240">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="27b2d-241">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="27b2d-241">Register-PSRepository</span></span>](Register-PSRepository.md)
