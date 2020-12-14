---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: d3300e0f378139cc873ffef1e798326100644d94
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889808"
---
# <span data-ttu-id="d8e52-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d8e52-103">Find-RoleCapability</span></span>

## <span data-ttu-id="d8e52-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d8e52-104">SYNOPSIS</span></span>
<span data-ttu-id="d8e52-105">Recherche les capacités de rôle dans des modules.</span><span class="sxs-lookup"><span data-stu-id="d8e52-105">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="d8e52-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d8e52-106">SYNTAX</span></span>

### <span data-ttu-id="d8e52-107">Tous</span><span class="sxs-lookup"><span data-stu-id="d8e52-107">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="d8e52-108">Description</span><span class="sxs-lookup"><span data-stu-id="d8e52-108">DESCRIPTION</span></span>

<span data-ttu-id="d8e52-109">L' `Find-RoleCapability` applet de commande recherche les référentiels inscrits pour rechercher les modules et les capacités de rôle PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8e52-109">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="d8e52-110">Pour chaque fonctionnalité de rôle trouvée par `Find-RoleCapability` , un objet **PSGetRoleCapabilityInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="d8e52-110">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="d8e52-111">Les objets **PSGetRoleCapabilityInfo** peuvent être envoyés vers le pipeline vers les `Install-Module` applets de commande ou `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="d8e52-111">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="d8e52-112">Les fonctionnalités de rôle PowerShell définissent les commandes et les applications qui sont disponibles pour un utilisateur sur un point de terminaison d’administration (JEA) juste suffisant.</span><span class="sxs-lookup"><span data-stu-id="d8e52-112">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="d8e52-113">Les capacités de rôle sont définies par des fichiers avec une `.psrc` extension.</span><span class="sxs-lookup"><span data-stu-id="d8e52-113">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="d8e52-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d8e52-114">EXAMPLES</span></span>

### <span data-ttu-id="d8e52-115">Exemple 1 : Rechercher des fonctionnalités de rôle</span><span class="sxs-lookup"><span data-stu-id="d8e52-115">Example 1: Find role capabilities</span></span>

<span data-ttu-id="d8e52-116">`Find-RoleCapability` recherche des fonctionnalités de rôle dans chaque dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="d8e52-116">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="d8e52-117">Pour effectuer une recherche dans un référentiel spécifique, utilisez le paramètre de **référentiel** .</span><span class="sxs-lookup"><span data-stu-id="d8e52-117">To search a specific repository, use the **Repository** parameter.</span></span>

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

### <span data-ttu-id="d8e52-118">Exemple 2 : Rechercher des fonctionnalités de rôle par nom</span><span class="sxs-lookup"><span data-stu-id="d8e52-118">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="d8e52-119">`Find-RoleCapability` recherche des fonctionnalités de rôle par nom.</span><span class="sxs-lookup"><span data-stu-id="d8e52-119">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="d8e52-120">Utilisez des virgules pour séparer un tableau de noms.</span><span class="sxs-lookup"><span data-stu-id="d8e52-120">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="d8e52-121">Exemple 3 : Rechercher et enregistrer le module d’une fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="d8e52-121">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="d8e52-122">L' `Find-RoleCapability` applet de commande recherche une capacité de rôle et envoie l’objet vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d8e52-122">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="d8e52-123">`Save-Module` enregistre le module de la fonctionnalité de rôle dans un système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d8e52-123">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="d8e52-124">`Get-ChildItem` affiche le contenu du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="d8e52-124">`Get-ChildItem` displays the contents of the module's directory.</span></span>

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

<span data-ttu-id="d8e52-125">`Find-RoleCapability` utilise le paramètre **Name** pour spécifier la fonctionnalité de rôle **général-Lev1** .</span><span class="sxs-lookup"><span data-stu-id="d8e52-125">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="d8e52-126">L’objet est envoyé dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d8e52-126">The object is sent down the pipeline.</span></span> <span data-ttu-id="d8e52-127">`Save-Module` utilise le paramètre **path** pour l’emplacement du système de fichiers pour enregistrer le module.</span><span class="sxs-lookup"><span data-stu-id="d8e52-127">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="d8e52-128">Une fois le module enregistré, `Get-ChildItem` spécifie le **chemin d’accès** du module et affiche le contenu du répertoire du module **JeaExamples** .</span><span class="sxs-lookup"><span data-stu-id="d8e52-128">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="d8e52-129">Exemple 4 : Rechercher et installer le module d’une fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="d8e52-129">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="d8e52-130">`Find-RoleCapability` recherche le module et envoie l’objet vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="d8e52-130">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="d8e52-131">`Install-Module` installe le module.</span><span class="sxs-lookup"><span data-stu-id="d8e52-131">`Install-Module` installs the module.</span></span> <span data-ttu-id="d8e52-132">Après l’installation, utilisez `Get-InstalledModule` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="d8e52-132">After the installation, use `Get-InstalledModule` to see the results.</span></span>

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

<span data-ttu-id="d8e52-133">`Find-RoleCapability` utilise le paramètre **Name** pour spécifier la fonctionnalité de rôle **général-Lev1** .</span><span class="sxs-lookup"><span data-stu-id="d8e52-133">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="d8e52-134">L’objet est envoyé dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d8e52-134">The object is sent down the pipeline.</span></span> <span data-ttu-id="d8e52-135">`Install-Module` utilise le paramètre **Verbose** pour afficher les messages d’état lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="d8e52-135">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="d8e52-136">Une fois l’installation terminée, la `Get-InstalledModule` sortie confirme que le module **JeaExamples** a été installé.</span><span class="sxs-lookup"><span data-stu-id="d8e52-136">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="d8e52-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8e52-137">PARAMETERS</span></span>

### <span data-ttu-id="d8e52-138">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="d8e52-138">-AllowPrerelease</span></span>

<span data-ttu-id="d8e52-139">Comprend les ressources marquées comme préversion dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="d8e52-139">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="d8e52-140">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="d8e52-140">-AllVersions</span></span>

<span data-ttu-id="d8e52-141">Indique que cette applet de commande obtient toutes les versions d’un module.</span><span class="sxs-lookup"><span data-stu-id="d8e52-141">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="d8e52-142">Le paramètre **AllVersions** affiche chacune des versions disponibles d’un module.</span><span class="sxs-lookup"><span data-stu-id="d8e52-142">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="d8e52-143">-Filter</span><span class="sxs-lookup"><span data-stu-id="d8e52-143">-Filter</span></span>

<span data-ttu-id="d8e52-144">Recherche des ressources en fonction de la syntaxe de recherche du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="d8e52-144">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="d8e52-145">Par exemple, spécifiez les mots à rechercher dans les propriétés **modulename** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="d8e52-145">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="d8e52-146">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d8e52-146">-MaximumVersion</span></span>

<span data-ttu-id="d8e52-147">Spécifie la version maximale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="d8e52-147">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="d8e52-148">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="d8e52-148">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="d8e52-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d8e52-149">-MinimumVersion</span></span>

<span data-ttu-id="d8e52-150">Spécifie la version minimale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="d8e52-150">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="d8e52-151">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="d8e52-151">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="d8e52-152">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="d8e52-152">-ModuleName</span></span>

<span data-ttu-id="d8e52-153">Spécifie le nom du module dans lequel rechercher les fonctionnalités de rôle.</span><span class="sxs-lookup"><span data-stu-id="d8e52-153">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="d8e52-154">La valeur par défaut est tous les modules.</span><span class="sxs-lookup"><span data-stu-id="d8e52-154">The default is all modules.</span></span>

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

### <span data-ttu-id="d8e52-155">-Name</span><span class="sxs-lookup"><span data-stu-id="d8e52-155">-Name</span></span>

<span data-ttu-id="d8e52-156">Spécifie le nom d’une capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="d8e52-156">Specifies the name of a role capability.</span></span> <span data-ttu-id="d8e52-157">La valeur par défaut est toutes les capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="d8e52-157">The default is all role capabilities.</span></span> <span data-ttu-id="d8e52-158">Utilisez des virgules pour séparer un tableau de noms de ressources.</span><span class="sxs-lookup"><span data-stu-id="d8e52-158">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="d8e52-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="d8e52-159">-Proxy</span></span>

<span data-ttu-id="d8e52-160">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="d8e52-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="d8e52-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d8e52-161">-ProxyCredential</span></span>

<span data-ttu-id="d8e52-162">Spécifie un compte d’utilisateur disposant de l’autorisation d’utiliser le serveur proxy spécifié dans le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="d8e52-162">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="d8e52-163">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="d8e52-163">-Repository</span></span>

<span data-ttu-id="d8e52-164">Spécifie un référentiel dans lequel Rechercher des fonctionnalités de rôle.</span><span class="sxs-lookup"><span data-stu-id="d8e52-164">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="d8e52-165">Utilisez des virgules pour séparer un tableau de noms de référentiel.</span><span class="sxs-lookup"><span data-stu-id="d8e52-165">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="d8e52-166">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d8e52-166">-RequiredVersion</span></span>

<span data-ttu-id="d8e52-167">Spécifie le numéro de version exact du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="d8e52-167">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="d8e52-168">Les paramètres **RequiredVersion** et **MinimumVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="d8e52-168">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="d8e52-169">-Tag</span><span class="sxs-lookup"><span data-stu-id="d8e52-169">-Tag</span></span>

<span data-ttu-id="d8e52-170">Spécifie les balises qui classent les modules dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="d8e52-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="d8e52-171">Utilisez des virgules pour séparer un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="d8e52-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="d8e52-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8e52-172">CommonParameters</span></span>

<span data-ttu-id="d8e52-173">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8e52-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8e52-174">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d8e52-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8e52-175">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d8e52-175">INPUTS</span></span>

## <span data-ttu-id="d8e52-176">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d8e52-176">OUTPUTS</span></span>

### <span data-ttu-id="d8e52-177">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="d8e52-177">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="d8e52-178">L' `Find-RoleCapability` applet de commande retourne un objet **PSGetRoleCapabilityInfo** .</span><span class="sxs-lookup"><span data-stu-id="d8e52-178">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="d8e52-179">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d8e52-179">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8e52-180">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="d8e52-180">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d8e52-181">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d8e52-181">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d8e52-182">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="d8e52-182">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d8e52-183">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8e52-183">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d8e52-184">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d8e52-184">RELATED LINKS</span></span>

[<span data-ttu-id="d8e52-185">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="d8e52-185">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="d8e52-186">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="d8e52-186">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="d8e52-187">Install-Module</span><span class="sxs-lookup"><span data-stu-id="d8e52-187">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="d8e52-188">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="d8e52-188">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="d8e52-189">Save-Module</span><span class="sxs-lookup"><span data-stu-id="d8e52-189">Save-Module</span></span>](Save-Module.md)
