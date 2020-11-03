---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: 33b7861f4e776b992d3483b9b0776c32a88599fc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201346"
---
# <span data-ttu-id="6a54a-103">Find-Module</span><span class="sxs-lookup"><span data-stu-id="6a54a-103">Find-Module</span></span>

## <span data-ttu-id="6a54a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6a54a-104">SYNOPSIS</span></span>
<span data-ttu-id="6a54a-105">Recherche les modules dans un référentiel qui correspondent aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6a54a-105">Finds modules in a repository that match specified criteria.</span></span>

## <span data-ttu-id="6a54a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a54a-106">SYNTAX</span></span>

### <span data-ttu-id="6a54a-107">Tous</span><span class="sxs-lookup"><span data-stu-id="6a54a-107">All</span></span>

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="6a54a-108">Description</span><span class="sxs-lookup"><span data-stu-id="6a54a-108">DESCRIPTION</span></span>

<span data-ttu-id="6a54a-109">L' `Find-Module` applet de commande recherche les modules dans un référentiel qui correspondent aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6a54a-109">The `Find-Module` cmdlet finds modules in a repository that match the specified criteria.</span></span>
<span data-ttu-id="6a54a-110">`Find-Module` retourne un objet **PSRepositoryItemInfo** pour chaque module qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="6a54a-110">`Find-Module` returns a **PSRepositoryItemInfo** object for each module it finds.</span></span> <span data-ttu-id="6a54a-111">Les objets peuvent être envoyés vers le pipeline vers des applets de commande telles que `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="6a54a-111">The objects can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

<span data-ttu-id="6a54a-112">La première fois `Find-Module` que vous tentez d’utiliser un référentiel, vous pouvez être invité à installer les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="6a54a-112">The first time `Find-Module` attempts to use a repository, you might be prompted to install updates.</span></span>
<span data-ttu-id="6a54a-113">Si la source du référentiel n’est pas inscrite auprès de l’applet de commande `Register-PSRepository` , une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="6a54a-113">If the repository source is not registered with `Register-PSRepository` cmdlet, an error is returned.</span></span>

<span data-ttu-id="6a54a-114">`Find-Module` retourne la version la plus récente d’un module si aucun paramètre n’est utilisé pour limiter la version.</span><span class="sxs-lookup"><span data-stu-id="6a54a-114">`Find-Module` returns the newest version of a module if no parameters are used that limit the version.</span></span> <span data-ttu-id="6a54a-115">Pour obtenir la liste des versions d’un module dans un référentiel, utilisez le paramètre **AllVersions** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-115">To get a repository's list of a module's versions, use the parameter **AllVersions** .</span></span>

<span data-ttu-id="6a54a-116">Si le paramètre **MinimumVersion** est spécifié, `Find-Module` retourne la version du module qui est supérieure ou égale à la valeur minimale.</span><span class="sxs-lookup"><span data-stu-id="6a54a-116">If the **MinimumVersion** parameter is specified, `Find-Module` returns the module's version that is equal to or greater than the minimum.</span></span> <span data-ttu-id="6a54a-117">Si une version plus récente est disponible dans le référentiel, la version la plus récente est retournée.</span><span class="sxs-lookup"><span data-stu-id="6a54a-117">If there is a newer version available in the repository, the newer version is returned.</span></span>

<span data-ttu-id="6a54a-118">Si le paramètre **MaximumVersion** est spécifié, `Find-Module` retourne la version la plus récente du module qui ne dépasse pas la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6a54a-118">If the **MaximumVersion** parameter is specified, `Find-Module` returns the newest version of the module that does not exceed the version specified.</span></span>

<span data-ttu-id="6a54a-119">Si le paramètre **RequiredVersion** est spécifié, `Find-Module` retourne uniquement la version du module qui correspond exactement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6a54a-119">If the **RequiredVersion** parameter is specified, `Find-Module` only returns the module version that is an exact match to the specified version.</span></span> <span data-ttu-id="6a54a-120">`Find-Module` effectue une recherche dans tous les modules disponibles, car des conflits de noms entre les sources peuvent se produire.</span><span class="sxs-lookup"><span data-stu-id="6a54a-120">`Find-Module` searches through all available modules, because name conflicts between sources can occur.</span></span>

<span data-ttu-id="6a54a-121">Les exemples suivants utilisent l' [PowerShell Gallery](https://www.powershellgallery.com/) comme seul référentiel enregistré.</span><span class="sxs-lookup"><span data-stu-id="6a54a-121">The following examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="6a54a-122">`Get-PSRepository` affiche les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="6a54a-122">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="6a54a-123">Si vous avez plusieurs référentiels inscrits, utilisez le `-Repository` paramètre pour spécifier le nom du référentiel.</span><span class="sxs-lookup"><span data-stu-id="6a54a-123">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="6a54a-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6a54a-124">EXAMPLES</span></span>

### <span data-ttu-id="6a54a-125">Exemple 1 : Rechercher un module par son nom</span><span class="sxs-lookup"><span data-stu-id="6a54a-125">Example 1: Find a module by name</span></span>

<span data-ttu-id="6a54a-126">Cet exemple recherche un module dans le référentiel par défaut.</span><span class="sxs-lookup"><span data-stu-id="6a54a-126">This example finds a module in the default repository.</span></span>

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

<span data-ttu-id="6a54a-127">L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-127">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>

### <span data-ttu-id="6a54a-128">Exemple 2 : Rechercher les modules avec des noms similaires</span><span class="sxs-lookup"><span data-stu-id="6a54a-128">Example 2: Find modules with similar names</span></span>

<span data-ttu-id="6a54a-129">Cet exemple utilise le `*` caractère générique astérisque () pour rechercher des modules avec des noms similaires.</span><span class="sxs-lookup"><span data-stu-id="6a54a-129">This example uses the asterisk (`*`) wildcard to find modules with similar names.</span></span>

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

<span data-ttu-id="6a54a-130">L' `Find-Module` applet de commande utilise le paramètre **Name** avec le `*` caractère générique astérisque () pour rechercher tous les modules qui contiennent **PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-130">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to find all modules that contain **PowerShell** .</span></span>

### <span data-ttu-id="6a54a-131">Exemple 3 : Rechercher un module par version minimale</span><span class="sxs-lookup"><span data-stu-id="6a54a-131">Example 3: Find a module by minimum version</span></span>

<span data-ttu-id="6a54a-132">Cet exemple recherche la version minimale d’un module.</span><span class="sxs-lookup"><span data-stu-id="6a54a-132">This example searches for a module's minimum version.</span></span> <span data-ttu-id="6a54a-133">Si le référentiel contient une version plus récente du module, la version la plus récente est retournée.</span><span class="sxs-lookup"><span data-stu-id="6a54a-133">If the repository contains a newer version of the module, the newer version is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="6a54a-134">L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-134">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="6a54a-135">**MinimumVersion** spécifie la version **1.6.5** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-135">The **MinimumVersion** specifies version **1.6.5** .</span></span> <span data-ttu-id="6a54a-136">`Find-Module` retourne la version PowerShellGet **2.1.0** , car elle dépasse la version minimale et est la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="6a54a-136">`Find-Module` returns PowerShellGet version **2.1.0** because it exceeds the minimum version and is the most current version.</span></span>

### <span data-ttu-id="6a54a-137">Exemple 4 : Rechercher un module par version spécifique</span><span class="sxs-lookup"><span data-stu-id="6a54a-137">Example 4: Find a module by specific version</span></span>

<span data-ttu-id="6a54a-138">Cet exemple retourne un objet qui représente la version spécifique d’un module.</span><span class="sxs-lookup"><span data-stu-id="6a54a-138">This example returns an object that represents a module's specific version.</span></span> <span data-ttu-id="6a54a-139">Si la version spécifiée est introuvable, une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="6a54a-139">If the specified version is not found, an error is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="6a54a-140">L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-140">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="6a54a-141">Le paramètre **RequiredVersion** spécifie la version **1.6.5** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-141">The **RequiredVersion** parameter specifies version **1.6.5** .</span></span>

### <span data-ttu-id="6a54a-142">Exemple 5 : Rechercher un module dans un référentiel spécifique</span><span class="sxs-lookup"><span data-stu-id="6a54a-142">Example 5: Find a module in a specific repository</span></span>

<span data-ttu-id="6a54a-143">Cet exemple utilise le paramètre **repository** pour rechercher un module dans un référentiel spécifique.</span><span class="sxs-lookup"><span data-stu-id="6a54a-143">This example uses the **Repository** parameter to find a module in a specific repository.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="6a54a-144">L' `Find-Module` applet de commande utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-144">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="6a54a-145">Le paramètre de **dépôt** spécifie la recherche dans le référentiel **PSGallery** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-145">The **Repository** parameter specifies to search the **PSGallery** repository.</span></span>

### <span data-ttu-id="6a54a-146">Exemple 6 : Rechercher un module dans plusieurs référentiels</span><span class="sxs-lookup"><span data-stu-id="6a54a-146">Example 6: Find a module in multiple repositories</span></span>

<span data-ttu-id="6a54a-147">Cet exemple utilise `Register-PSRepository` pour spécifier un référentiel.</span><span class="sxs-lookup"><span data-stu-id="6a54a-147">This example uses the `Register-PSRepository` to specify a repository.</span></span> <span data-ttu-id="6a54a-148">`Find-Module` utilise le référentiel pour rechercher un module.</span><span class="sxs-lookup"><span data-stu-id="6a54a-148">`Find-Module` uses the repository to search for a module.</span></span>

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

<span data-ttu-id="6a54a-149">L' `Register-PSRepository` applet de commande inscrit un nouveau référentiel.</span><span class="sxs-lookup"><span data-stu-id="6a54a-149">The `Register-PSRepository` cmdlet registers a new repository.</span></span> <span data-ttu-id="6a54a-150">Le paramètre **Name** attribue le nom **MySource** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-150">The **Name** parameter assigns the name **MySource** .</span></span> <span data-ttu-id="6a54a-151">Le paramètre **SourceLocation** spécifie l’adresse du dépôt.</span><span class="sxs-lookup"><span data-stu-id="6a54a-151">The **SourceLocation** parameter specifies the repository's address.</span></span>

<span data-ttu-id="6a54a-152">L' `Find-Module` applet de commande utilise le paramètre **Name** avec le `*` caractère générique astérisque () pour spécifier le module **contoso** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-152">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to specify the **Contoso** module.</span></span> <span data-ttu-id="6a54a-153">Le paramètre de **dépôt** spécifie de rechercher deux dépôts, **PSGallery** et **MySource** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-153">The **Repository** parameter specifies to search two repositories, **PSGallery** and **MySource** .</span></span>

### <span data-ttu-id="6a54a-154">Exemple 7 : Rechercher un module qui contient une ressource DSC</span><span class="sxs-lookup"><span data-stu-id="6a54a-154">Example 7: Find a module that contains a DSC resource</span></span>

<span data-ttu-id="6a54a-155">Cette commande retourne les modules qui contiennent des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="6a54a-155">This command returns modules that contain DSC resources.</span></span> <span data-ttu-id="6a54a-156">Le paramètre **includes** possède quatre fonctionnalités prédéfinies utilisées pour effectuer des recherches dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="6a54a-156">The **Includes** parameter has four predefined functionalities that are used to search the repository.</span></span> <span data-ttu-id="6a54a-157">Utilisez l’onglet terminé pour afficher les quatre fonctionnalités prises en charge par le paramètre **includes** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-157">Use tab-complete to display the four functionalities supported by the **Includes** parameter.</span></span>

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

<span data-ttu-id="6a54a-158">L' `Find-Module` applet de commande utilise le paramètre de **référentiel** pour effectuer une recherche dans le référentiel, **PSGallery** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-158">The `Find-Module` cmdlet uses the **Repository** parameter to search the repository, **PSGallery** .</span></span>
<span data-ttu-id="6a54a-159">Le paramètre **includes** spécifie **DscResource** , qui est une fonctionnalité que le paramètre peut rechercher dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="6a54a-159">The **Includes** parameter specifies **DscResource** , which is a functionality that the parameter can search for in the repository.</span></span>

### <span data-ttu-id="6a54a-160">Exemple 8 : Rechercher un module à l’aide d’un filtre</span><span class="sxs-lookup"><span data-stu-id="6a54a-160">Example 8: Find a module with a filter</span></span>

<span data-ttu-id="6a54a-161">Dans cet exemple, pour rechercher des modules, un filtre est utilisé pour effectuer une recherche dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="6a54a-161">In this example, to find modules, a filter is used to search the repository.</span></span>

<span data-ttu-id="6a54a-162">Pour un référentiel NuGet, le paramètre de **filtre** parcourt le nom, la description et les balises pour l’argument.</span><span class="sxs-lookup"><span data-stu-id="6a54a-162">For a NuGet-based repository, the **Filter** parameter searches through the name, description, and tags for the argument.</span></span>

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

<span data-ttu-id="6a54a-163">L' `Find-Module` applet de commande utilise le paramètre de **filtre** pour rechercher **AppDomain** dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="6a54a-163">The `Find-Module` cmdlet uses the **Filter** parameter to search the repository for **AppDomain** .</span></span>

## <span data-ttu-id="6a54a-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6a54a-164">PARAMETERS</span></span>

### <span data-ttu-id="6a54a-165">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="6a54a-165">-AllowPrerelease</span></span>

<span data-ttu-id="6a54a-166">Comprend dans les modules de résultats marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="6a54a-166">Includes in the results modules marked as a pre-release.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a54a-167">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="6a54a-167">-AllVersions</span></span>

<span data-ttu-id="6a54a-168">Spécifie d’inclure toutes les versions d’un module dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="6a54a-168">Specifies to include all versions of a module in the results.</span></span> <span data-ttu-id="6a54a-169">Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-169">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="6a54a-170">-Command</span><span class="sxs-lookup"><span data-stu-id="6a54a-170">-Command</span></span>

<span data-ttu-id="6a54a-171">Spécifie un tableau de commandes à rechercher dans les modules.</span><span class="sxs-lookup"><span data-stu-id="6a54a-171">Specifies an array of commands to find in modules.</span></span> <span data-ttu-id="6a54a-172">Une commande peut être une fonction ou un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="6a54a-172">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="6a54a-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="6a54a-173">-Credential</span></span>

<span data-ttu-id="6a54a-174">Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour installer un module pour un fournisseur de package ou une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6a54a-174">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="6a54a-175">-DscResource</span><span class="sxs-lookup"><span data-stu-id="6a54a-175">-DscResource</span></span>

<span data-ttu-id="6a54a-176">Spécifie le nom ou une partie du nom des modules qui contiennent des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="6a54a-176">Specifies the name, or part of the name, of modules that contain DSC resources.</span></span> <span data-ttu-id="6a54a-177">Par conventions PowerShell, effectue une recherche **ou** lorsque vous fournissez plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="6a54a-177">Per PowerShell conventions, performs an **OR** search when you provide multiple arguments.</span></span>

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

### <span data-ttu-id="6a54a-178">-Filter</span><span class="sxs-lookup"><span data-stu-id="6a54a-178">-Filter</span></span>

<span data-ttu-id="6a54a-179">Spécifie un filtre basé sur la syntaxe de recherche spécifique au fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-179">Specifies a filter based on the **PackageManagement** provider-specific search syntax.</span></span> <span data-ttu-id="6a54a-180">Pour les modules NuGet, ce paramètre est l’équivalent de la recherche à l’aide de la barre de recherche sur le site Web [PowerShell Gallery](https://www.powershellgallery.com/) .</span><span class="sxs-lookup"><span data-stu-id="6a54a-180">For NuGet modules, this parameter is the equivalent of searching by using the Search bar on the [PowerShell Gallery](https://www.powershellgallery.com/) website.</span></span>

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

### <span data-ttu-id="6a54a-181">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="6a54a-181">-IncludeDependencies</span></span>

<span data-ttu-id="6a54a-182">Indique que cette opération comprend tous les modules qui dépendent du module spécifié dans le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-182">Indicates that this operation includes all modules that are dependent upon the module specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="6a54a-183">-Comprend</span><span class="sxs-lookup"><span data-stu-id="6a54a-183">-Includes</span></span>

<span data-ttu-id="6a54a-184">Retourne uniquement les modules qui incluent des genres spécifiques de fonctionnalités PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6a54a-184">Returns only those modules that include specific kinds of PowerShell functionality.</span></span> <span data-ttu-id="6a54a-185">Par exemple, vous souhaiterez peut-être Rechercher uniquement les modules qui incluent **DSCResource** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-185">For example, you might only want to find modules that include **DSCResource** .</span></span> <span data-ttu-id="6a54a-186">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a54a-186">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="6a54a-187">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="6a54a-187">Cmdlet</span></span>
- <span data-ttu-id="6a54a-188">DscResource</span><span class="sxs-lookup"><span data-stu-id="6a54a-188">DscResource</span></span>
- <span data-ttu-id="6a54a-189">Fonction</span><span class="sxs-lookup"><span data-stu-id="6a54a-189">Function</span></span>
- <span data-ttu-id="6a54a-190">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="6a54a-190">RoleCapability</span></span>

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

### <span data-ttu-id="6a54a-191">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6a54a-191">-MaximumVersion</span></span>

<span data-ttu-id="6a54a-192">Spécifie la version maximale ou la plus récente du module à inclure dans les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="6a54a-192">Specifies the maximum, or latest, version of the module to include in the search results.</span></span>
<span data-ttu-id="6a54a-193">**MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="6a54a-193">**MaximumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

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

### <span data-ttu-id="6a54a-194">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6a54a-194">-MinimumVersion</span></span>

<span data-ttu-id="6a54a-195">Spécifie la version minimale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="6a54a-195">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="6a54a-196">**MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="6a54a-196">**MinimumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

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

### <span data-ttu-id="6a54a-197">-Name</span><span class="sxs-lookup"><span data-stu-id="6a54a-197">-Name</span></span>

<span data-ttu-id="6a54a-198">Spécifie les noms des modules à rechercher dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="6a54a-198">Specifies the names of modules to search for in the repository.</span></span> <span data-ttu-id="6a54a-199">Une liste séparée par des virgules de noms de modules est acceptée.</span><span class="sxs-lookup"><span data-stu-id="6a54a-199">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="6a54a-200">Les caractères génériques sont acceptés.</span><span class="sxs-lookup"><span data-stu-id="6a54a-200">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6a54a-201">-Proxy</span><span class="sxs-lookup"><span data-stu-id="6a54a-201">-Proxy</span></span>

<span data-ttu-id="6a54a-202">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="6a54a-202">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="6a54a-203">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="6a54a-203">-ProxyCredential</span></span>

<span data-ttu-id="6a54a-204">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-204">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="6a54a-205">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="6a54a-205">-Repository</span></span>

<span data-ttu-id="6a54a-206">Utilisez le paramètre de **dépôt** pour spécifier le référentiel dans lequel Rechercher un module.</span><span class="sxs-lookup"><span data-stu-id="6a54a-206">Use the **Repository** parameter to specify which repository to search for a module.</span></span> <span data-ttu-id="6a54a-207">Utilisé lorsque plusieurs dépôts sont inscrits.</span><span class="sxs-lookup"><span data-stu-id="6a54a-207">Used when multiple repositories are registered.</span></span> <span data-ttu-id="6a54a-208">Accepte une liste de référentiels séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="6a54a-208">Accepts a comma-separated list of repositories.</span></span> <span data-ttu-id="6a54a-209">Pour inscrire un dépôt, utilisez `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="6a54a-209">To register a repository, use `Register-PSRepository`.</span></span> <span data-ttu-id="6a54a-210">Pour afficher les dépôts inscrits, utilisez `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="6a54a-210">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="6a54a-211">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6a54a-211">-RequiredVersion</span></span>

<span data-ttu-id="6a54a-212">Spécifie le numéro de version exact du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="6a54a-212">Specifies the exact version number of the module to include in the results.</span></span> <span data-ttu-id="6a54a-213">**RequiredVersion** ne peut pas être utilisé dans la même commande que **MinimumVersion** ou **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-213">**RequiredVersion** cannot be used in the same command as **MinimumVersion** or **MaximumVersion** .</span></span>

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

### <span data-ttu-id="6a54a-214">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="6a54a-214">-RoleCapability</span></span>

<span data-ttu-id="6a54a-215">Spécifie un tableau de capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="6a54a-215">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="6a54a-216">-Tag</span><span class="sxs-lookup"><span data-stu-id="6a54a-216">-Tag</span></span>

<span data-ttu-id="6a54a-217">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="6a54a-217">Specifies an array of tags.</span></span> <span data-ttu-id="6a54a-218">Exemples de balises : **DesiredStateConfiguration** , **DSC** , **DSCResourceKit** ou **PSModule** .</span><span class="sxs-lookup"><span data-stu-id="6a54a-218">Example tags include **DesiredStateConfiguration** , **DSC** , **DSCResourceKit** , or **PSModule** .</span></span>

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

### <span data-ttu-id="6a54a-219">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a54a-219">CommonParameters</span></span>

<span data-ttu-id="6a54a-220">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a54a-220">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a54a-221">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6a54a-221">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a54a-222">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6a54a-222">INPUTS</span></span>

### <span data-ttu-id="6a54a-223">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6a54a-223">System.String[]</span></span>

### <span data-ttu-id="6a54a-224">System.String</span><span class="sxs-lookup"><span data-stu-id="6a54a-224">System.String</span></span>

### <span data-ttu-id="6a54a-225">System.Uri</span><span class="sxs-lookup"><span data-stu-id="6a54a-225">System.Uri</span></span>

### <span data-ttu-id="6a54a-226">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="6a54a-226">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="6a54a-227">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6a54a-227">OUTPUTS</span></span>

### <span data-ttu-id="6a54a-228">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="6a54a-228">PSRepositoryItemInfo</span></span>

<span data-ttu-id="6a54a-229">`Find-Module` crée des objets **PSRepositoryItemInfo** qui peuvent être envoyés vers le pipeline vers des applets de commande telles que `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="6a54a-229">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

## <span data-ttu-id="6a54a-230">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6a54a-230">NOTES</span></span>

<span data-ttu-id="6a54a-231">Cette applet de commande s’exécute sur les versions PowerShell 5,0 ou ultérieures de PowerShell, sur Windows 7, ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="6a54a-231">This cmdlet runs on PowerShell 5.0 or later releases of PowerShell, on Windows 7, or Windows 2008 R2 and later releases of Windows.</span></span>

## <span data-ttu-id="6a54a-232">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6a54a-232">RELATED LINKS</span></span>

[<span data-ttu-id="6a54a-233">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="6a54a-233">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="6a54a-234">Install-Module</span><span class="sxs-lookup"><span data-stu-id="6a54a-234">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="6a54a-235">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="6a54a-235">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="6a54a-236">Save-Module</span><span class="sxs-lookup"><span data-stu-id="6a54a-236">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="6a54a-237">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="6a54a-237">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="6a54a-238">Update-Module</span><span class="sxs-lookup"><span data-stu-id="6a54a-238">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="6a54a-239">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="6a54a-239">Register-PSRepository</span></span>](Register-PSRepository.md)
