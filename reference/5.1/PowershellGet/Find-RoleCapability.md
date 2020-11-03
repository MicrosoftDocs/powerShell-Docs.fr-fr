---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: c7392423f4b915716ed1ef911fcfddd215337639
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202893"
---
# <span data-ttu-id="383ac-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="383ac-103">Find-RoleCapability</span></span>

## <span data-ttu-id="383ac-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="383ac-104">SYNOPSIS</span></span>
<span data-ttu-id="383ac-105">Recherche les capacités de rôle dans des modules.</span><span class="sxs-lookup"><span data-stu-id="383ac-105">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="383ac-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="383ac-106">SYNTAX</span></span>

### <span data-ttu-id="383ac-107">Tous</span><span class="sxs-lookup"><span data-stu-id="383ac-107">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="383ac-108">Description</span><span class="sxs-lookup"><span data-stu-id="383ac-108">DESCRIPTION</span></span>

<span data-ttu-id="383ac-109">L' `Find-RoleCapability` applet de commande recherche les référentiels inscrits pour rechercher les modules et les capacités de rôle PowerShell.</span><span class="sxs-lookup"><span data-stu-id="383ac-109">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="383ac-110">Pour chaque fonctionnalité de rôle trouvée par `Find-RoleCapability` , un objet **PSGetRoleCapabilityInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="383ac-110">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="383ac-111">Les objets **PSGetRoleCapabilityInfo** peuvent être envoyés vers le pipeline vers les `Install-Module` applets de commande ou `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="383ac-111">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="383ac-112">Les fonctionnalités de rôle PowerShell définissent les commandes et les applications qui sont disponibles pour un utilisateur sur un point de terminaison d’administration (JEA) juste suffisant.</span><span class="sxs-lookup"><span data-stu-id="383ac-112">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="383ac-113">Les capacités de rôle sont définies par des fichiers avec une `.psrc` extension.</span><span class="sxs-lookup"><span data-stu-id="383ac-113">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="383ac-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="383ac-114">EXAMPLES</span></span>

### <span data-ttu-id="383ac-115">Exemple 1 : Rechercher des fonctionnalités de rôle</span><span class="sxs-lookup"><span data-stu-id="383ac-115">Example 1: Find role capabilities</span></span>

<span data-ttu-id="383ac-116">`Find-RoleCapability` recherche des fonctionnalités de rôle dans chaque dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="383ac-116">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="383ac-117">Pour effectuer une recherche dans un référentiel spécifique, utilisez le paramètre de **référentiel** .</span><span class="sxs-lookup"><span data-stu-id="383ac-117">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="383ac-118">Exemple 2 : Rechercher des fonctionnalités de rôle par nom</span><span class="sxs-lookup"><span data-stu-id="383ac-118">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="383ac-119">`Find-RoleCapability` recherche des fonctionnalités de rôle par nom.</span><span class="sxs-lookup"><span data-stu-id="383ac-119">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="383ac-120">Utilisez des virgules pour séparer un tableau de noms.</span><span class="sxs-lookup"><span data-stu-id="383ac-120">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="383ac-121">Exemple 3 : Rechercher et enregistrer le module d’une fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="383ac-121">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="383ac-122">L' `Find-RoleCapability` applet de commande recherche une capacité de rôle et envoie l’objet vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="383ac-122">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="383ac-123">`Save-Module` enregistre le module de la fonctionnalité de rôle dans un système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="383ac-123">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="383ac-124">`Get-ChildItem` affiche le contenu du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="383ac-124">`Get-ChildItem` displays the contents of the module's directory.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

<span data-ttu-id="383ac-125">`Find-RoleCapability` utilise le paramètre **Name** pour spécifier la fonctionnalité de rôle **général-Lev1** .</span><span class="sxs-lookup"><span data-stu-id="383ac-125">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="383ac-126">L’objet est envoyé dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="383ac-126">The object is sent down the pipeline.</span></span> <span data-ttu-id="383ac-127">`Save-Module` utilise le paramètre **path** pour l’emplacement du système de fichiers pour enregistrer le module.</span><span class="sxs-lookup"><span data-stu-id="383ac-127">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="383ac-128">Une fois le module enregistré, `Get-ChildItem` spécifie le **chemin d’accès** du module et affiche le contenu du répertoire du module **JeaExamples** .</span><span class="sxs-lookup"><span data-stu-id="383ac-128">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="383ac-129">Exemple 4 : Rechercher et installer le module d’une fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="383ac-129">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="383ac-130">`Find-RoleCapability` recherche le module et envoie l’objet vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="383ac-130">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="383ac-131">`Install-Module` installe le module.</span><span class="sxs-lookup"><span data-stu-id="383ac-131">`Install-Module` installs the module.</span></span> <span data-ttu-id="383ac-132">Après l’installation, utilisez `Get-InstalledModule` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="383ac-132">After the installation, use `Get-InstalledModule` to see the results.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

<span data-ttu-id="383ac-133">`Find-RoleCapability` utilise le paramètre **Name** pour spécifier la fonctionnalité de rôle **général-Lev1** .</span><span class="sxs-lookup"><span data-stu-id="383ac-133">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="383ac-134">L’objet est envoyé dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="383ac-134">The object is sent down the pipeline.</span></span> <span data-ttu-id="383ac-135">`Install-Module` utilise le paramètre **Verbose** pour afficher les messages d’état lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="383ac-135">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="383ac-136">Une fois l’installation terminée, la `Get-InstalledModule` sortie confirme que le module **JeaExamples** a été installé.</span><span class="sxs-lookup"><span data-stu-id="383ac-136">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="383ac-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="383ac-137">PARAMETERS</span></span>

### <span data-ttu-id="383ac-138">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="383ac-138">-AllowPrerelease</span></span>

<span data-ttu-id="383ac-139">Comprend les ressources marquées comme préversion dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="383ac-139">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="383ac-140">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="383ac-140">-AllVersions</span></span>

<span data-ttu-id="383ac-141">Indique que cette applet de commande obtient toutes les versions d’un module.</span><span class="sxs-lookup"><span data-stu-id="383ac-141">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="383ac-142">Le paramètre **AllVersions** affiche chacune des versions disponibles d’un module.</span><span class="sxs-lookup"><span data-stu-id="383ac-142">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="383ac-143">-Filter</span><span class="sxs-lookup"><span data-stu-id="383ac-143">-Filter</span></span>

<span data-ttu-id="383ac-144">Recherche des ressources en fonction de la syntaxe de recherche du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="383ac-144">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="383ac-145">Par exemple, spécifiez les mots à rechercher dans les propriétés **modulename** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="383ac-145">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="383ac-146">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="383ac-146">-MaximumVersion</span></span>

<span data-ttu-id="383ac-147">Spécifie la version maximale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="383ac-147">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="383ac-148">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="383ac-148">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="383ac-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="383ac-149">-MinimumVersion</span></span>

<span data-ttu-id="383ac-150">Spécifie la version minimale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="383ac-150">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="383ac-151">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="383ac-151">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="383ac-152">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="383ac-152">-ModuleName</span></span>

<span data-ttu-id="383ac-153">Spécifie le nom du module dans lequel rechercher les fonctionnalités de rôle.</span><span class="sxs-lookup"><span data-stu-id="383ac-153">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="383ac-154">La valeur par défaut est tous les modules.</span><span class="sxs-lookup"><span data-stu-id="383ac-154">The default is all modules.</span></span>

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

### <span data-ttu-id="383ac-155">-Name</span><span class="sxs-lookup"><span data-stu-id="383ac-155">-Name</span></span>

<span data-ttu-id="383ac-156">Spécifie le nom d’une capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="383ac-156">Specifies the name of a role capability.</span></span> <span data-ttu-id="383ac-157">La valeur par défaut est toutes les capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="383ac-157">The default is all role capabilities.</span></span> <span data-ttu-id="383ac-158">Utilisez des virgules pour séparer un tableau de noms de ressources.</span><span class="sxs-lookup"><span data-stu-id="383ac-158">Use commas to separate an array of resource names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="383ac-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="383ac-159">-Proxy</span></span>

<span data-ttu-id="383ac-160">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="383ac-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="383ac-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="383ac-161">-ProxyCredential</span></span>

<span data-ttu-id="383ac-162">Spécifie un compte d’utilisateur disposant de l’autorisation d’utiliser le serveur proxy spécifié dans le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="383ac-162">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="383ac-163">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="383ac-163">-Repository</span></span>

<span data-ttu-id="383ac-164">Spécifie un référentiel dans lequel Rechercher des fonctionnalités de rôle.</span><span class="sxs-lookup"><span data-stu-id="383ac-164">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="383ac-165">Utilisez des virgules pour séparer un tableau de noms de référentiel.</span><span class="sxs-lookup"><span data-stu-id="383ac-165">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="383ac-166">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="383ac-166">-RequiredVersion</span></span>

<span data-ttu-id="383ac-167">Spécifie le numéro de version exact du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="383ac-167">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="383ac-168">Les paramètres **RequiredVersion** et **MinimumVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="383ac-168">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="383ac-169">-Tag</span><span class="sxs-lookup"><span data-stu-id="383ac-169">-Tag</span></span>

<span data-ttu-id="383ac-170">Spécifie les balises qui classent les modules dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="383ac-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="383ac-171">Utilisez des virgules pour séparer un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="383ac-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="383ac-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="383ac-172">CommonParameters</span></span>

<span data-ttu-id="383ac-173">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="383ac-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="383ac-174">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="383ac-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="383ac-175">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="383ac-175">INPUTS</span></span>

## <span data-ttu-id="383ac-176">SORTIES</span><span class="sxs-lookup"><span data-stu-id="383ac-176">OUTPUTS</span></span>

### <span data-ttu-id="383ac-177">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="383ac-177">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="383ac-178">L' `Find-RoleCapability` applet de commande retourne un objet **PSGetRoleCapabilityInfo** .</span><span class="sxs-lookup"><span data-stu-id="383ac-178">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="383ac-179">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="383ac-179">NOTES</span></span>

## <span data-ttu-id="383ac-180">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="383ac-180">RELATED LINKS</span></span>

[<span data-ttu-id="383ac-181">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="383ac-181">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="383ac-182">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="383ac-182">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="383ac-183">Install-Module</span><span class="sxs-lookup"><span data-stu-id="383ac-183">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="383ac-184">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="383ac-184">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="383ac-185">Save-Module</span><span class="sxs-lookup"><span data-stu-id="383ac-185">Save-Module</span></span>](Save-Module.md)
