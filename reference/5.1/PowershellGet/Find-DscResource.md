---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: 39896c4f48d6cd8809d4a680e776d36deb65b0d8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889859"
---
# <span data-ttu-id="dbfeb-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="dbfeb-103">Find-DscResource</span></span>

## <span data-ttu-id="dbfeb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="dbfeb-104">SYNOPSIS</span></span>
<span data-ttu-id="dbfeb-105">Recherche les ressources de configuration d’état souhaité (DSC).</span><span class="sxs-lookup"><span data-stu-id="dbfeb-105">Finds Desired State Configuration (DSC) resources.</span></span>

## <span data-ttu-id="dbfeb-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="dbfeb-106">SYNTAX</span></span>

### <span data-ttu-id="dbfeb-107">Tous</span><span class="sxs-lookup"><span data-stu-id="dbfeb-107">All</span></span>

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="dbfeb-108">Description</span><span class="sxs-lookup"><span data-stu-id="dbfeb-108">DESCRIPTION</span></span>

<span data-ttu-id="dbfeb-109">L' `Find-DscResource` applet de commande recherche les référentiels inscrits pour trouver les ressources DSC contenues dans les modules.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-109">The `Find-DscResource` cmdlet searches registered repositories to find DSC resources contained in modules.</span></span> <span data-ttu-id="dbfeb-110">Par défaut, `Find-DscResource` recherche tous les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-110">By default `Find-DscResource` searches all registered repositories.</span></span>

<span data-ttu-id="dbfeb-111">Pour chaque module trouvé par `Find-DscResource` , un objet **PSGetDscResourceInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-111">For each module found by `Find-DscResource`, a **PSGetDscResourceInfo** object is returned.</span></span>
<span data-ttu-id="dbfeb-112">Les objets **PSGetDscResourceInfo** peuvent être envoyés vers l’applet de commande via le pipeline `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-112">**PSGetDscResourceInfo** objects can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="dbfeb-113">`Install-Module` installe le module.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-113">`Install-Module` installs the module.</span></span>

## <span data-ttu-id="dbfeb-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="dbfeb-114">EXAMPLES</span></span>

### <span data-ttu-id="dbfeb-115">Exemple 1 : Rechercher toutes les ressources DSC</span><span class="sxs-lookup"><span data-stu-id="dbfeb-115">Example 1: Find all DSC resources</span></span>

<span data-ttu-id="dbfeb-116">`Find-DscResource` retourne des ressources DSC à partir de dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-116">`Find-DscResource` returns DSC resources from registered repositories.</span></span> <span data-ttu-id="dbfeb-117">Pour effectuer une recherche dans un référentiel spécifique, utilisez le paramètre de **référentiel** .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-117">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### <span data-ttu-id="dbfeb-118">Exemple 2 : Rechercher une ressource DSC par nom</span><span class="sxs-lookup"><span data-stu-id="dbfeb-118">Example 2: Find a DSC resource by name</span></span>

<span data-ttu-id="dbfeb-119">`Find-DscResource` localise les ressources DSC par nom.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-119">`Find-DscResource` locates DSC resources by name.</span></span> <span data-ttu-id="dbfeb-120">Utilisez des virgules pour séparer un tableau de noms de ressources.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-120">Use commas to separate an array of resource names.</span></span>

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

<span data-ttu-id="dbfeb-121">`Find-DscResource` utilise le paramètre **Name** pour rechercher le tableau spécifié de ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-121">`Find-DscResource` uses the **Name** parameter to find the specified array of DSC resources.</span></span>

### <span data-ttu-id="dbfeb-122">Exemple 3 : Rechercher une ressource DSC et l’installer</span><span class="sxs-lookup"><span data-stu-id="dbfeb-122">Example 3: Find a DSC resource and install it</span></span>

<span data-ttu-id="dbfeb-123">`Find-DscResource` localise une ressource DSC et envoie l’objet dans le pipeline à installer.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-123">`Find-DscResource` locates a DSC resource and sends the object down the pipeline to be installed.</span></span>
<span data-ttu-id="dbfeb-124">Après l’installation, utilisez `Get-InstalledModule` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-124">After the installation, use `Get-InstalledModule` to view the results.</span></span>

<span data-ttu-id="dbfeb-125">Plusieurs ressources du même module peuvent être envoyées vers le pipeline vers le `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-125">Multiple resources from the same module can be sent down the pipeline to the `Install-Module`.</span></span>
<span data-ttu-id="dbfeb-126">`Install-Module` tente d’installer le module une seule fois.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-126">`Install-Module` attempts to only install the module once.</span></span>

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

<span data-ttu-id="dbfeb-127">`Find-DscResource` utilise le paramètre **Name** pour rechercher la ressource nommée **xWebsite**.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-127">`Find-DscResource` uses the **Name** parameter to find the resource named **xWebsite**.</span></span> <span data-ttu-id="dbfeb-128">L’objet est envoyé dans le pipeline à l’applet de commande `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-128">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="dbfeb-129">`Install-Module` installe le module **xWebAdministration** pour la ressource.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-129">`Install-Module` installs the **xWebAdministration** module for the resource.</span></span>

### <span data-ttu-id="dbfeb-130">Exemple 4 : Rechercher toutes les ressources DSC dans un module</span><span class="sxs-lookup"><span data-stu-id="dbfeb-130">Example 4: Find all DSC resources in a module</span></span>

<span data-ttu-id="dbfeb-131">`Find-DscResource` recherche toutes les ressources DSC contenues dans un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-131">`Find-DscResource` finds all the DSC resources contained in a specified module.</span></span> <span data-ttu-id="dbfeb-132">Par défaut, la version actuelle est affichée.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-132">By default, the current version is displayed.</span></span> <span data-ttu-id="dbfeb-133">Pour afficher d’autres versions, utilisez les paramètres **AllVersions** ou **RequiredVersions** .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-133">To display other versions, use the **AllVersions** or **RequiredVersions** parameters.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

<span data-ttu-id="dbfeb-134">`Find-DscResource` utilise le paramètre **modulename** pour spécifier le **xWebAdministration** et rechercher les ressources DSC contenues dans le module.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-134">`Find-DscResource` uses the **ModuleName** parameter to specify the **xWebAdministration** and find the DSC resources contained in the module.</span></span> <span data-ttu-id="dbfeb-135">La version actuelle de chaque ressource est affichée.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-135">The current version of each resource is displayed.</span></span>

### <span data-ttu-id="dbfeb-136">Exemple 5 : Rechercher une ressource DSC par balise et version requise</span><span class="sxs-lookup"><span data-stu-id="dbfeb-136">Example 5: Find a DSC resource by tag and required version</span></span>

<span data-ttu-id="dbfeb-137">Les ressources DSC peuvent être localisées à l’aide des paramètres **tag** et **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-137">DSC resources can be located using the parameters **Tag** and **RequiredVersion**.</span></span> <span data-ttu-id="dbfeb-138">**Tag** affiche la version actuelle de chaque ressource contenant la balise spécifiée dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-138">**Tag** displays the current version of every resource that contains the specified tag in the repository.</span></span>
<span data-ttu-id="dbfeb-139">**RequiredVersion** a besoin du paramètre **modulename** et le paramètre **Name** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-139">**RequiredVersion** needs the **ModuleName** parameter and the **Name** parameter is optional.</span></span> <span data-ttu-id="dbfeb-140">Les paramètres **Name** et **modulename** limitent la sortie.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-140">The **Name** and **ModuleName** parameters limit the output.</span></span> <span data-ttu-id="dbfeb-141">Utilisez le paramètre **AllVersions** pour afficher les versions disponibles d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-141">Use the **AllVersions** parameter to display a DSC resource's available versions.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### <span data-ttu-id="dbfeb-142">Exemple 6 : Rechercher une ressource à l’aide d’un filtre</span><span class="sxs-lookup"><span data-stu-id="dbfeb-142">Example 6: Find a resource by using a filter</span></span>

<span data-ttu-id="dbfeb-143">`Find-DscResource` recherche toutes les ressources et utilise le paramètre **Filter** pour spécifier les résultats par **domaine**.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-143">`Find-DscResource` finds all resources and uses the **Filter** parameter to specify the results by **Domain**.</span></span> <span data-ttu-id="dbfeb-144">Le paramètre de **filtre** recherche la valeur de filtre dans la description ou le nom de module de l’objet.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-144">The **Filter** parameter finds the filter value in the object's description or module name.</span></span> <span data-ttu-id="dbfeb-145">Utilisez l' `Select-Object` applet de commande pour afficher les propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-145">Use the `Select-Object` cmdlet to view an object's properties.</span></span>

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## <span data-ttu-id="dbfeb-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dbfeb-146">PARAMETERS</span></span>

### <span data-ttu-id="dbfeb-147">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="dbfeb-147">-AllowPrerelease</span></span>

<span data-ttu-id="dbfeb-148">Comprend les ressources marquées comme préversion dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-148">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="dbfeb-149">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="dbfeb-149">-AllVersions</span></span>

<span data-ttu-id="dbfeb-150">Le paramètre **AllVersions** affiche chacune des versions disponibles d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-150">The **AllVersions** parameter displays each of a DSC resource's available versions.</span></span> <span data-ttu-id="dbfeb-151">Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion**, **MaximumVersion** ou **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-151">You can't use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="dbfeb-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="dbfeb-152">-Filter</span></span>

<span data-ttu-id="dbfeb-153">Recherche des ressources en fonction de la syntaxe de recherche du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-153">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="dbfeb-154">Par exemple, spécifiez les mots à rechercher dans les propriétés **modulename** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-154">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="dbfeb-155">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="dbfeb-155">-MaximumVersion</span></span>

<span data-ttu-id="dbfeb-156">Spécifie la version maximale de la ressource à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-156">Specifies the maximum version of the resource to include in results.</span></span> <span data-ttu-id="dbfeb-157">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-157">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="dbfeb-158">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="dbfeb-158">-MinimumVersion</span></span>

<span data-ttu-id="dbfeb-159">Spécifie la version minimale de la ressource à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-159">Specifies the minimum version of the resource to include in results.</span></span> <span data-ttu-id="dbfeb-160">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-160">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="dbfeb-161">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="dbfeb-161">-ModuleName</span></span>

<span data-ttu-id="dbfeb-162">Spécifie un module qui contient la ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-162">Specifies a module that contains the DSC resource.</span></span>

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

### <span data-ttu-id="dbfeb-163">-Name</span><span class="sxs-lookup"><span data-stu-id="dbfeb-163">-Name</span></span>

<span data-ttu-id="dbfeb-164">Spécifie le nom d'une ressource.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-164">Specifies the name of a resource.</span></span> <span data-ttu-id="dbfeb-165">La valeur par défaut est toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-165">The default is all resources.</span></span> <span data-ttu-id="dbfeb-166">Utilisez des virgules pour séparer un tableau de noms de ressources.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-166">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="dbfeb-167">-Proxy</span><span class="sxs-lookup"><span data-stu-id="dbfeb-167">-Proxy</span></span>

<span data-ttu-id="dbfeb-168">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-168">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="dbfeb-169">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="dbfeb-169">-ProxyCredential</span></span>

<span data-ttu-id="dbfeb-170">Spécifie un compte d’utilisateur disposant de l’autorisation d’utiliser le serveur proxy spécifié dans le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-170">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="dbfeb-171">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="dbfeb-171">-Repository</span></span>

<span data-ttu-id="dbfeb-172">Spécifie un référentiel dans lequel Rechercher des ressources.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-172">Specifies a repository to search for resources.</span></span> <span data-ttu-id="dbfeb-173">Utilisez des virgules pour séparer un tableau de noms de référentiel.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-173">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="dbfeb-174">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="dbfeb-174">-RequiredVersion</span></span>

<span data-ttu-id="dbfeb-175">Spécifie le numéro de version exact du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-175">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="dbfeb-176">Les paramètres **RequiredVersion** et **MinimumVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-176">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="dbfeb-177">-Tag</span><span class="sxs-lookup"><span data-stu-id="dbfeb-177">-Tag</span></span>

<span data-ttu-id="dbfeb-178">Spécifie les balises qui classent les modules dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-178">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="dbfeb-179">Utilisez des virgules pour séparer un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-179">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="dbfeb-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dbfeb-180">CommonParameters</span></span>

<span data-ttu-id="dbfeb-181">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dbfeb-182">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dbfeb-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dbfeb-183">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="dbfeb-183">INPUTS</span></span>

## <span data-ttu-id="dbfeb-184">SORTIES</span><span class="sxs-lookup"><span data-stu-id="dbfeb-184">OUTPUTS</span></span>

### <span data-ttu-id="dbfeb-185">PSGetDscResourceInfo</span><span class="sxs-lookup"><span data-stu-id="dbfeb-185">PSGetDscResourceInfo</span></span>

<span data-ttu-id="dbfeb-186">`Find-DscResource` retourne un objet **PSGetDscResourceInfo** .</span><span class="sxs-lookup"><span data-stu-id="dbfeb-186">`Find-DscResource` returns a **PSGetDscResourceInfo** object.</span></span>

## <span data-ttu-id="dbfeb-187">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="dbfeb-187">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dbfeb-188">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="dbfeb-188">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="dbfeb-189">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-189">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="dbfeb-190">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="dbfeb-190">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="dbfeb-191">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-191">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="dbfeb-192">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="dbfeb-192">RELATED LINKS</span></span>

[<span data-ttu-id="dbfeb-193">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="dbfeb-193">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="dbfeb-194">Install-Module</span><span class="sxs-lookup"><span data-stu-id="dbfeb-194">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="dbfeb-195">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="dbfeb-195">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="dbfeb-196">Select-Object</span><span class="sxs-lookup"><span data-stu-id="dbfeb-196">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="dbfeb-197">Module Uninstall</span><span class="sxs-lookup"><span data-stu-id="dbfeb-197">Uninstall-Module</span></span>](Uninstall-Module.md)
