---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: a24d66aa1ce9e353e41cc7a686ee9f910a7106fc
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597754"
---
# <span data-ttu-id="952cf-102">Find-Command</span><span class="sxs-lookup"><span data-stu-id="952cf-102">Find-Command</span></span>

## <span data-ttu-id="952cf-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="952cf-103">SYNOPSIS</span></span>
<span data-ttu-id="952cf-104">Recherche des commandes PowerShell dans des modules.</span><span class="sxs-lookup"><span data-stu-id="952cf-104">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="952cf-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="952cf-105">SYNTAX</span></span>

### <span data-ttu-id="952cf-106">Tous</span><span class="sxs-lookup"><span data-stu-id="952cf-106">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="952cf-107">Description</span><span class="sxs-lookup"><span data-stu-id="952cf-107">DESCRIPTION</span></span>

<span data-ttu-id="952cf-108">L' `Find-Command` applet de commande recherche les commandes PowerShell, telles que les applets de commande, les alias, les fonctions et les workflows.</span><span class="sxs-lookup"><span data-stu-id="952cf-108">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="952cf-109">`Find-Command` recherche des modules dans les référentiels inscrits.</span><span class="sxs-lookup"><span data-stu-id="952cf-109">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="952cf-110">Pour chaque commande trouvée par `Find-Command` , un objet **PSGetCommandInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="952cf-110">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="952cf-111">L’objet **PSGetCommandInfo** peut être envoyé dans le pipeline à l’applet de commande `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="952cf-111">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="952cf-112">`Install-Module` installe le module qui contient la commande.</span><span class="sxs-lookup"><span data-stu-id="952cf-112">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="952cf-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="952cf-113">EXAMPLES</span></span>

### <span data-ttu-id="952cf-114">Exemple 1 : Rechercher toutes les commandes dans un dépôt spécifié</span><span class="sxs-lookup"><span data-stu-id="952cf-114">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="952cf-115">L' `Find-Command` applet de commande recherche des modules dans un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="952cf-115">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

<span data-ttu-id="952cf-116">`Find-Command` utilise le paramètre de **référentiel** pour spécifier le nom d’un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="952cf-116">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="952cf-117">Les objets sont envoyés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="952cf-117">The objects are sent down the pipeline.</span></span> <span data-ttu-id="952cf-118">`Select-Object` reçoit les objets et utilise le **premier** paramètre pour afficher les 10 premiers résultats.</span><span class="sxs-lookup"><span data-stu-id="952cf-118">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="952cf-119">Exemple 2 : Rechercher une commande par nom</span><span class="sxs-lookup"><span data-stu-id="952cf-119">Example 2: Find a command by name</span></span>

<span data-ttu-id="952cf-120">`Find-Command` peut utiliser le nom d’une commande pour localiser le module dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="952cf-120">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="952cf-121">Il est possible qu’un nom de commande existe dans plusieurs **ModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="952cf-121">It's possible that a command name exists in multiple **ModuleNames**.</span></span>

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

<span data-ttu-id="952cf-122">`Find-Command` utilise le paramètre de **référentiel** pour rechercher le **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="952cf-122">`Find-Command` uses the **Repository** parameter to search the **PSGallery**.</span></span> <span data-ttu-id="952cf-123">Le paramètre **Name** spécifie la commande **-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="952cf-123">The **Name** parameter specifies the command **Get-TargetResource**.</span></span>

### <span data-ttu-id="952cf-124">Exemple 3 : Rechercher les commandes par nom et installer le module</span><span class="sxs-lookup"><span data-stu-id="952cf-124">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="952cf-125">`Find-Command` peut localiser la commande et le module, puis envoyer l’objet à `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="952cf-125">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="952cf-126">Si une commande est incluse dans plusieurs modules, utilisez le `Find-Command` paramètre **de nom du module** applets de commande.</span><span class="sxs-lookup"><span data-stu-id="952cf-126">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="952cf-127">Dans le cas contraire, il est possible que les modules que vous ne souhaitiez pas installer soient installés.</span><span class="sxs-lookup"><span data-stu-id="952cf-127">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="952cf-128">`Find-Command` utilise le paramètre **Name** pour spécifier la commande **-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="952cf-128">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource**.</span></span> <span data-ttu-id="952cf-129">Le paramètre de **référentiel** effectue une recherche dans le **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="952cf-129">The **Repository** parameter searches the **PSGallery**.</span></span> <span data-ttu-id="952cf-130">Le paramètre **modulename** spécifie le module que vous souhaitez installer, **SystemLocaleDsc**.</span><span class="sxs-lookup"><span data-stu-id="952cf-130">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc**.</span></span> <span data-ttu-id="952cf-131">L’objet est envoyé vers le pipeline vers `Install-Module` et le module est installé.</span><span class="sxs-lookup"><span data-stu-id="952cf-131">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="952cf-132">Une fois l’installation terminée, vous pouvez utiliser `Get-InstalledModule` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="952cf-132">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="952cf-133">Exemple 4 : Rechercher une commande et enregistrer son module</span><span class="sxs-lookup"><span data-stu-id="952cf-133">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="952cf-134">`Find-Command` utilise les paramètres **Name** et **repository** pour rechercher la commande **Invoke-ScriptAnalyzer** dans le référentiel **PSGallery** .</span><span class="sxs-lookup"><span data-stu-id="952cf-134">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="952cf-135">L’objet est envoyé dans le pipeline à `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="952cf-135">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="952cf-136">Le paramètre **path** détermine l’emplacement d’enregistrement du module.</span><span class="sxs-lookup"><span data-stu-id="952cf-136">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="952cf-137">**Verbose** est un paramètre facultatif, mais affiche la sortie de l’État dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="952cf-137">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="952cf-138">La sortie détaillée est avantageuse pour la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="952cf-138">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="952cf-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="952cf-139">PARAMETERS</span></span>

### <span data-ttu-id="952cf-140">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="952cf-140">-AllowPrerelease</span></span>

<span data-ttu-id="952cf-141">Comprend les modules marqués comme version préliminaire dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="952cf-141">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="952cf-142">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="952cf-142">-AllVersions</span></span>

<span data-ttu-id="952cf-143">Indique que cette applet de commande obtient toutes les versions d’un module.</span><span class="sxs-lookup"><span data-stu-id="952cf-143">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="952cf-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="952cf-144">-Filter</span></span>

<span data-ttu-id="952cf-145">Recherche des modules en fonction de la syntaxe de recherche du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="952cf-145">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="952cf-146">Par exemple, spécifiez les mots à rechercher dans les propriétés **modulename** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="952cf-146">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="952cf-147">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="952cf-147">-MaximumVersion</span></span>

<span data-ttu-id="952cf-148">Spécifie la version maximale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="952cf-148">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="952cf-149">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="952cf-149">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="952cf-150">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="952cf-150">-MinimumVersion</span></span>

<span data-ttu-id="952cf-151">Spécifie la version minimale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="952cf-151">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="952cf-152">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="952cf-152">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="952cf-153">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="952cf-153">-ModuleName</span></span>

<span data-ttu-id="952cf-154">Spécifie le nom d’un module dans lequel Rechercher des commandes.</span><span class="sxs-lookup"><span data-stu-id="952cf-154">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="952cf-155">La valeur par défaut est tous les modules.</span><span class="sxs-lookup"><span data-stu-id="952cf-155">The default is all modules.</span></span>

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

### <span data-ttu-id="952cf-156">-Name</span><span class="sxs-lookup"><span data-stu-id="952cf-156">-Name</span></span>

<span data-ttu-id="952cf-157">Spécifie le nom de la commande à rechercher dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="952cf-157">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="952cf-158">Utilisez des virgules pour séparer un tableau de noms de commandes.</span><span class="sxs-lookup"><span data-stu-id="952cf-158">Use commas to separate an array of command names.</span></span>

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

### <span data-ttu-id="952cf-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="952cf-159">-Proxy</span></span>

<span data-ttu-id="952cf-160">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="952cf-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="952cf-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="952cf-161">-ProxyCredential</span></span>

<span data-ttu-id="952cf-162">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="952cf-162">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="952cf-163">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="952cf-163">-Repository</span></span>

<span data-ttu-id="952cf-164">Spécifie le référentiel dans lequel Rechercher des commandes.</span><span class="sxs-lookup"><span data-stu-id="952cf-164">Specifies the repository to search for commands.</span></span> <span data-ttu-id="952cf-165">Utilisez des virgules pour séparer un tableau de noms de référentiel.</span><span class="sxs-lookup"><span data-stu-id="952cf-165">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="952cf-166">La valeur par défaut est tous les dépôts.</span><span class="sxs-lookup"><span data-stu-id="952cf-166">The default is all repositories.</span></span>

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

### <span data-ttu-id="952cf-167">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="952cf-167">-RequiredVersion</span></span>

<span data-ttu-id="952cf-168">Spécifie la version du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="952cf-168">Specifies the version of the module to include in the results.</span></span>

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

### <span data-ttu-id="952cf-169">-Tag</span><span class="sxs-lookup"><span data-stu-id="952cf-169">-Tag</span></span>

<span data-ttu-id="952cf-170">Spécifie les balises qui classent les modules dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="952cf-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="952cf-171">Utilisez des virgules pour séparer un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="952cf-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="952cf-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="952cf-172">CommonParameters</span></span>

<span data-ttu-id="952cf-173">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="952cf-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="952cf-174">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="952cf-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="952cf-175">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="952cf-175">INPUTS</span></span>

## <span data-ttu-id="952cf-176">SORTIES</span><span class="sxs-lookup"><span data-stu-id="952cf-176">OUTPUTS</span></span>

### <span data-ttu-id="952cf-177">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="952cf-177">PSGetCommandInfo</span></span>

<span data-ttu-id="952cf-178">`Find-Command` génère un objet **PSGetCommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="952cf-178">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="952cf-179">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="952cf-179">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="952cf-180">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="952cf-180">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="952cf-181">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="952cf-181">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="952cf-182">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="952cf-182">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="952cf-183">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="952cf-183">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="952cf-184">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="952cf-184">RELATED LINKS</span></span>

[<span data-ttu-id="952cf-185">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="952cf-185">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="952cf-186">Install-Module</span><span class="sxs-lookup"><span data-stu-id="952cf-186">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="952cf-187">Save-Module</span><span class="sxs-lookup"><span data-stu-id="952cf-187">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="952cf-188">Select-Object</span><span class="sxs-lookup"><span data-stu-id="952cf-188">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="952cf-189">Module Uninstall</span><span class="sxs-lookup"><span data-stu-id="952cf-189">Uninstall-Module</span></span>](Uninstall-Module.md)
