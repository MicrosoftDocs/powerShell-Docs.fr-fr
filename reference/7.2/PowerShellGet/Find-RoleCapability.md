---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: a84dee14872ad5a7d0f7bac8e0057dc527855074
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597533"
---
# <span data-ttu-id="2a387-102">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="2a387-102">Find-RoleCapability</span></span>

## <span data-ttu-id="2a387-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2a387-103">SYNOPSIS</span></span>
<span data-ttu-id="2a387-104">Recherche les capacités de rôle dans des modules.</span><span class="sxs-lookup"><span data-stu-id="2a387-104">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="2a387-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="2a387-105">SYNTAX</span></span>

### <span data-ttu-id="2a387-106">Tous</span><span class="sxs-lookup"><span data-stu-id="2a387-106">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2a387-107">Description</span><span class="sxs-lookup"><span data-stu-id="2a387-107">DESCRIPTION</span></span>

<span data-ttu-id="2a387-108">L' `Find-RoleCapability` applet de commande recherche les référentiels inscrits pour rechercher les modules et les capacités de rôle PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a387-108">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="2a387-109">Pour chaque fonctionnalité de rôle trouvée par `Find-RoleCapability` , un objet **PSGetRoleCapabilityInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="2a387-109">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="2a387-110">Les objets **PSGetRoleCapabilityInfo** peuvent être envoyés vers le pipeline vers les `Install-Module` applets de commande ou `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="2a387-110">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="2a387-111">Les fonctionnalités de rôle PowerShell définissent les commandes et les applications qui sont disponibles pour un utilisateur sur un point de terminaison d’administration (JEA) juste suffisant.</span><span class="sxs-lookup"><span data-stu-id="2a387-111">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="2a387-112">Les capacités de rôle sont définies par des fichiers avec une `.psrc` extension.</span><span class="sxs-lookup"><span data-stu-id="2a387-112">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="2a387-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2a387-113">EXAMPLES</span></span>

### <span data-ttu-id="2a387-114">Exemple 1 : Rechercher des fonctionnalités de rôle</span><span class="sxs-lookup"><span data-stu-id="2a387-114">Example 1: Find role capabilities</span></span>

<span data-ttu-id="2a387-115">`Find-RoleCapability` recherche des fonctionnalités de rôle dans chaque dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="2a387-115">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="2a387-116">Pour effectuer une recherche dans un référentiel spécifique, utilisez le paramètre de **référentiel** .</span><span class="sxs-lookup"><span data-stu-id="2a387-116">To search a specific repository, use the **Repository** parameter.</span></span>

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

### <span data-ttu-id="2a387-117">Exemple 2 : Rechercher des fonctionnalités de rôle par nom</span><span class="sxs-lookup"><span data-stu-id="2a387-117">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="2a387-118">`Find-RoleCapability` recherche des fonctionnalités de rôle par nom.</span><span class="sxs-lookup"><span data-stu-id="2a387-118">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="2a387-119">Utilisez des virgules pour séparer un tableau de noms.</span><span class="sxs-lookup"><span data-stu-id="2a387-119">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="2a387-120">Exemple 3 : Rechercher et enregistrer le module d’une fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="2a387-120">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="2a387-121">L' `Find-RoleCapability` applet de commande recherche une capacité de rôle et envoie l’objet vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="2a387-121">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="2a387-122">`Save-Module` enregistre le module de la fonctionnalité de rôle dans un système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="2a387-122">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="2a387-123">`Get-ChildItem` affiche le contenu du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="2a387-123">`Get-ChildItem` displays the contents of the module's directory.</span></span>

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

<span data-ttu-id="2a387-124">`Find-RoleCapability` utilise le paramètre **Name** pour spécifier la fonctionnalité de rôle **général-Lev1** .</span><span class="sxs-lookup"><span data-stu-id="2a387-124">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="2a387-125">L’objet est envoyé dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="2a387-125">The object is sent down the pipeline.</span></span> <span data-ttu-id="2a387-126">`Save-Module` utilise le paramètre **path** pour l’emplacement du système de fichiers pour enregistrer le module.</span><span class="sxs-lookup"><span data-stu-id="2a387-126">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="2a387-127">Une fois le module enregistré, `Get-ChildItem` spécifie le **chemin d’accès** du module et affiche le contenu du répertoire du module **JeaExamples** .</span><span class="sxs-lookup"><span data-stu-id="2a387-127">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="2a387-128">Exemple 4 : Rechercher et installer le module d’une fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="2a387-128">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="2a387-129">`Find-RoleCapability` recherche le module et envoie l’objet vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="2a387-129">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="2a387-130">`Install-Module` installe le module.</span><span class="sxs-lookup"><span data-stu-id="2a387-130">`Install-Module` installs the module.</span></span> <span data-ttu-id="2a387-131">Après l’installation, utilisez `Get-InstalledModule` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="2a387-131">After the installation, use `Get-InstalledModule` to see the results.</span></span>

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

<span data-ttu-id="2a387-132">`Find-RoleCapability` utilise le paramètre **Name** pour spécifier la fonctionnalité de rôle **général-Lev1** .</span><span class="sxs-lookup"><span data-stu-id="2a387-132">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="2a387-133">L’objet est envoyé dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="2a387-133">The object is sent down the pipeline.</span></span> <span data-ttu-id="2a387-134">`Install-Module` utilise le paramètre **Verbose** pour afficher les messages d’état lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="2a387-134">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="2a387-135">Une fois l’installation terminée, la `Get-InstalledModule` sortie confirme que le module **JeaExamples** a été installé.</span><span class="sxs-lookup"><span data-stu-id="2a387-135">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="2a387-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a387-136">PARAMETERS</span></span>

### <span data-ttu-id="2a387-137">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="2a387-137">-AllowPrerelease</span></span>

<span data-ttu-id="2a387-138">Comprend les ressources marquées comme préversion dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="2a387-138">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="2a387-139">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="2a387-139">-AllVersions</span></span>

<span data-ttu-id="2a387-140">Indique que cette applet de commande obtient toutes les versions d’un module.</span><span class="sxs-lookup"><span data-stu-id="2a387-140">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="2a387-141">Le paramètre **AllVersions** affiche chacune des versions disponibles d’un module.</span><span class="sxs-lookup"><span data-stu-id="2a387-141">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="2a387-142">-Filter</span><span class="sxs-lookup"><span data-stu-id="2a387-142">-Filter</span></span>

<span data-ttu-id="2a387-143">Recherche des ressources en fonction de la syntaxe de recherche du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="2a387-143">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="2a387-144">Par exemple, spécifiez les mots à rechercher dans les propriétés **modulename** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="2a387-144">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="2a387-145">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2a387-145">-MaximumVersion</span></span>

<span data-ttu-id="2a387-146">Spécifie la version maximale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="2a387-146">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="2a387-147">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="2a387-147">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="2a387-148">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="2a387-148">-MinimumVersion</span></span>

<span data-ttu-id="2a387-149">Spécifie la version minimale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="2a387-149">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="2a387-150">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="2a387-150">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="2a387-151">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="2a387-151">-ModuleName</span></span>

<span data-ttu-id="2a387-152">Spécifie le nom du module dans lequel rechercher les fonctionnalités de rôle.</span><span class="sxs-lookup"><span data-stu-id="2a387-152">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="2a387-153">La valeur par défaut est tous les modules.</span><span class="sxs-lookup"><span data-stu-id="2a387-153">The default is all modules.</span></span>

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

### <span data-ttu-id="2a387-154">-Name</span><span class="sxs-lookup"><span data-stu-id="2a387-154">-Name</span></span>

<span data-ttu-id="2a387-155">Spécifie le nom d’une capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="2a387-155">Specifies the name of a role capability.</span></span> <span data-ttu-id="2a387-156">La valeur par défaut est toutes les capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="2a387-156">The default is all role capabilities.</span></span> <span data-ttu-id="2a387-157">Utilisez des virgules pour séparer un tableau de noms de ressources.</span><span class="sxs-lookup"><span data-stu-id="2a387-157">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="2a387-158">-Proxy</span><span class="sxs-lookup"><span data-stu-id="2a387-158">-Proxy</span></span>

<span data-ttu-id="2a387-159">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="2a387-159">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="2a387-160">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="2a387-160">-ProxyCredential</span></span>

<span data-ttu-id="2a387-161">Spécifie un compte d’utilisateur disposant de l’autorisation d’utiliser le serveur proxy spécifié dans le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="2a387-161">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="2a387-162">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="2a387-162">-Repository</span></span>

<span data-ttu-id="2a387-163">Spécifie un référentiel dans lequel Rechercher des fonctionnalités de rôle.</span><span class="sxs-lookup"><span data-stu-id="2a387-163">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="2a387-164">Utilisez des virgules pour séparer un tableau de noms de référentiel.</span><span class="sxs-lookup"><span data-stu-id="2a387-164">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="2a387-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2a387-165">-RequiredVersion</span></span>

<span data-ttu-id="2a387-166">Spécifie le numéro de version exact du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="2a387-166">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="2a387-167">Les paramètres **RequiredVersion** et **MinimumVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="2a387-167">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="2a387-168">-Tag</span><span class="sxs-lookup"><span data-stu-id="2a387-168">-Tag</span></span>

<span data-ttu-id="2a387-169">Spécifie les balises qui classent les modules dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="2a387-169">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="2a387-170">Utilisez des virgules pour séparer un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="2a387-170">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="2a387-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a387-171">CommonParameters</span></span>

<span data-ttu-id="2a387-172">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2a387-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a387-173">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2a387-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a387-174">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="2a387-174">INPUTS</span></span>

### <span data-ttu-id="2a387-175">System.Uri</span><span class="sxs-lookup"><span data-stu-id="2a387-175">System.Uri</span></span>

### <span data-ttu-id="2a387-176">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="2a387-176">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="2a387-177">SORTIES</span><span class="sxs-lookup"><span data-stu-id="2a387-177">OUTPUTS</span></span>

### <span data-ttu-id="2a387-178">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="2a387-178">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="2a387-179">L' `Find-RoleCapability` applet de commande retourne un objet **PSGetRoleCapabilityInfo** .</span><span class="sxs-lookup"><span data-stu-id="2a387-179">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="2a387-180">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="2a387-180">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a387-181">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="2a387-181">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="2a387-182">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="2a387-182">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="2a387-183">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="2a387-183">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="2a387-184">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a387-184">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="2a387-185">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="2a387-185">RELATED LINKS</span></span>

[<span data-ttu-id="2a387-186">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2a387-186">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="2a387-187">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="2a387-187">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="2a387-188">Install-Module</span><span class="sxs-lookup"><span data-stu-id="2a387-188">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="2a387-189">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="2a387-189">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="2a387-190">Save-Module</span><span class="sxs-lookup"><span data-stu-id="2a387-190">Save-Module</span></span>](Save-Module.md)
