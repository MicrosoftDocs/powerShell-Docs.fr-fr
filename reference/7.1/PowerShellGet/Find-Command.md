---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: 1cd86a1c9abe6c8a4af9f68ed17ea1876ff1bd20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204166"
---
# <span data-ttu-id="fea5a-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="fea5a-103">Find-Command</span></span>

## <span data-ttu-id="fea5a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fea5a-104">SYNOPSIS</span></span>
<span data-ttu-id="fea5a-105">Recherche des commandes PowerShell dans des modules.</span><span class="sxs-lookup"><span data-stu-id="fea5a-105">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="fea5a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fea5a-106">SYNTAX</span></span>

### <span data-ttu-id="fea5a-107">Tous</span><span class="sxs-lookup"><span data-stu-id="fea5a-107">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="fea5a-108">Description</span><span class="sxs-lookup"><span data-stu-id="fea5a-108">DESCRIPTION</span></span>

<span data-ttu-id="fea5a-109">L' `Find-Command` applet de commande recherche les commandes PowerShell, telles que les applets de commande, les alias, les fonctions et les workflows.</span><span class="sxs-lookup"><span data-stu-id="fea5a-109">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="fea5a-110">`Find-Command` recherche des modules dans les référentiels inscrits.</span><span class="sxs-lookup"><span data-stu-id="fea5a-110">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="fea5a-111">Pour chaque commande trouvée par `Find-Command` , un objet **PSGetCommandInfo** est retourné.</span><span class="sxs-lookup"><span data-stu-id="fea5a-111">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="fea5a-112">L’objet **PSGetCommandInfo** peut être envoyé dans le pipeline à l’applet de commande `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="fea5a-112">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="fea5a-113">`Install-Module` installe le module qui contient la commande.</span><span class="sxs-lookup"><span data-stu-id="fea5a-113">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="fea5a-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fea5a-114">EXAMPLES</span></span>

### <span data-ttu-id="fea5a-115">Exemple 1 : Rechercher toutes les commandes dans un dépôt spécifié</span><span class="sxs-lookup"><span data-stu-id="fea5a-115">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="fea5a-116">L' `Find-Command` applet de commande recherche des modules dans un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="fea5a-116">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

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

<span data-ttu-id="fea5a-117">`Find-Command` utilise le paramètre de **référentiel** pour spécifier le nom d’un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="fea5a-117">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="fea5a-118">Les objets sont envoyés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="fea5a-118">The objects are sent down the pipeline.</span></span> <span data-ttu-id="fea5a-119">`Select-Object` reçoit les objets et utilise le **premier** paramètre pour afficher les 10 premiers résultats.</span><span class="sxs-lookup"><span data-stu-id="fea5a-119">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="fea5a-120">Exemple 2 : Rechercher une commande par nom</span><span class="sxs-lookup"><span data-stu-id="fea5a-120">Example 2: Find a command by name</span></span>

<span data-ttu-id="fea5a-121">`Find-Command` peut utiliser le nom d’une commande pour localiser le module dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="fea5a-121">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="fea5a-122">Il est possible qu’un nom de commande existe dans plusieurs **ModuleNames** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-122">It's possible that a command name exists in multiple **ModuleNames** .</span></span>

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

<span data-ttu-id="fea5a-123">`Find-Command` utilise le paramètre de **référentiel** pour rechercher le **PSGallery** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-123">`Find-Command` uses the **Repository** parameter to search the **PSGallery** .</span></span> <span data-ttu-id="fea5a-124">Le paramètre **Name** spécifie la commande **-TargetResource** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-124">The **Name** parameter specifies the command **Get-TargetResource** .</span></span>

### <span data-ttu-id="fea5a-125">Exemple 3 : Rechercher les commandes par nom et installer le module</span><span class="sxs-lookup"><span data-stu-id="fea5a-125">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="fea5a-126">`Find-Command` peut localiser la commande et le module, puis envoyer l’objet à `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="fea5a-126">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="fea5a-127">Si une commande est incluse dans plusieurs modules, utilisez le `Find-Command` paramètre **de nom du module** applets de commande.</span><span class="sxs-lookup"><span data-stu-id="fea5a-127">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="fea5a-128">Dans le cas contraire, il est possible que les modules que vous ne souhaitiez pas installer soient installés.</span><span class="sxs-lookup"><span data-stu-id="fea5a-128">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="fea5a-129">`Find-Command` utilise le paramètre **Name** pour spécifier la commande **-TargetResource** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-129">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource** .</span></span> <span data-ttu-id="fea5a-130">Le paramètre de **référentiel** effectue une recherche dans le **PSGallery** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-130">The **Repository** parameter searches the **PSGallery** .</span></span> <span data-ttu-id="fea5a-131">Le paramètre **modulename** spécifie le module que vous souhaitez installer, **SystemLocaleDsc** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-131">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc** .</span></span> <span data-ttu-id="fea5a-132">L’objet est envoyé vers le pipeline vers `Install-Module` et le module est installé.</span><span class="sxs-lookup"><span data-stu-id="fea5a-132">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="fea5a-133">Une fois l’installation terminée, vous pouvez utiliser `Get-InstalledModule` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="fea5a-133">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="fea5a-134">Exemple 4 : Rechercher une commande et enregistrer son module</span><span class="sxs-lookup"><span data-stu-id="fea5a-134">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="fea5a-135">`Find-Command` utilise les paramètres **Name** et **repository** pour rechercher la commande **Invoke-ScriptAnalyzer** dans le référentiel **PSGallery** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-135">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="fea5a-136">L’objet est envoyé dans le pipeline à `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="fea5a-136">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="fea5a-137">Le paramètre **path** détermine l’emplacement d’enregistrement du module.</span><span class="sxs-lookup"><span data-stu-id="fea5a-137">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="fea5a-138">**Verbose** est un paramètre facultatif, mais affiche la sortie de l’État dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fea5a-138">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="fea5a-139">La sortie détaillée est avantageuse pour la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="fea5a-139">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="fea5a-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fea5a-140">PARAMETERS</span></span>

### <span data-ttu-id="fea5a-141">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="fea5a-141">-AllowPrerelease</span></span>

<span data-ttu-id="fea5a-142">Comprend les modules marqués comme version préliminaire dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="fea5a-142">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="fea5a-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="fea5a-143">-AllVersions</span></span>

<span data-ttu-id="fea5a-144">Indique que cette applet de commande obtient toutes les versions d’un module.</span><span class="sxs-lookup"><span data-stu-id="fea5a-144">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="fea5a-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="fea5a-145">-Filter</span></span>

<span data-ttu-id="fea5a-146">Recherche des modules en fonction de la syntaxe de recherche du fournisseur **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-146">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="fea5a-147">Par exemple, spécifiez les mots à rechercher dans les propriétés **modulename** et **Description** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-147">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="fea5a-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="fea5a-148">-MaximumVersion</span></span>

<span data-ttu-id="fea5a-149">Spécifie la version maximale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="fea5a-149">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="fea5a-150">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="fea5a-150">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="fea5a-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="fea5a-151">-MinimumVersion</span></span>

<span data-ttu-id="fea5a-152">Spécifie la version minimale du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="fea5a-152">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="fea5a-153">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="fea5a-153">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="fea5a-154">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="fea5a-154">-ModuleName</span></span>

<span data-ttu-id="fea5a-155">Spécifie le nom d’un module dans lequel Rechercher des commandes.</span><span class="sxs-lookup"><span data-stu-id="fea5a-155">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="fea5a-156">La valeur par défaut est tous les modules.</span><span class="sxs-lookup"><span data-stu-id="fea5a-156">The default is all modules.</span></span>

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

### <span data-ttu-id="fea5a-157">-Name</span><span class="sxs-lookup"><span data-stu-id="fea5a-157">-Name</span></span>

<span data-ttu-id="fea5a-158">Spécifie le nom de la commande à rechercher dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="fea5a-158">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="fea5a-159">Utilisez des virgules pour séparer un tableau de noms de commandes.</span><span class="sxs-lookup"><span data-stu-id="fea5a-159">Use commas to separate an array of command names.</span></span>

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

### <span data-ttu-id="fea5a-160">-Proxy</span><span class="sxs-lookup"><span data-stu-id="fea5a-160">-Proxy</span></span>

<span data-ttu-id="fea5a-161">Spécifie un serveur proxy pour la demande, plutôt qu’une connexion directe à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="fea5a-161">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="fea5a-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="fea5a-162">-ProxyCredential</span></span>

<span data-ttu-id="fea5a-163">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-163">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="fea5a-164">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="fea5a-164">-Repository</span></span>

<span data-ttu-id="fea5a-165">Spécifie le référentiel dans lequel Rechercher des commandes.</span><span class="sxs-lookup"><span data-stu-id="fea5a-165">Specifies the repository to search for commands.</span></span> <span data-ttu-id="fea5a-166">Utilisez des virgules pour séparer un tableau de noms de référentiel.</span><span class="sxs-lookup"><span data-stu-id="fea5a-166">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="fea5a-167">La valeur par défaut est tous les dépôts.</span><span class="sxs-lookup"><span data-stu-id="fea5a-167">The default is all repositories.</span></span>

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

### <span data-ttu-id="fea5a-168">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="fea5a-168">-RequiredVersion</span></span>

<span data-ttu-id="fea5a-169">Spécifie la version du module à inclure dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="fea5a-169">Specifies the version of the module to include in the results.</span></span>

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

### <span data-ttu-id="fea5a-170">-Tag</span><span class="sxs-lookup"><span data-stu-id="fea5a-170">-Tag</span></span>

<span data-ttu-id="fea5a-171">Spécifie les balises qui classent les modules dans un référentiel.</span><span class="sxs-lookup"><span data-stu-id="fea5a-171">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="fea5a-172">Utilisez des virgules pour séparer un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="fea5a-172">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="fea5a-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fea5a-173">CommonParameters</span></span>

<span data-ttu-id="fea5a-174">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fea5a-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fea5a-175">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fea5a-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fea5a-176">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fea5a-176">INPUTS</span></span>

## <span data-ttu-id="fea5a-177">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fea5a-177">OUTPUTS</span></span>

### <span data-ttu-id="fea5a-178">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="fea5a-178">PSGetCommandInfo</span></span>

<span data-ttu-id="fea5a-179">`Find-Command` génère un objet **PSGetCommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="fea5a-179">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="fea5a-180">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fea5a-180">NOTES</span></span>

## <span data-ttu-id="fea5a-181">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fea5a-181">RELATED LINKS</span></span>

[<span data-ttu-id="fea5a-182">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="fea5a-182">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="fea5a-183">Install-Module</span><span class="sxs-lookup"><span data-stu-id="fea5a-183">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="fea5a-184">Save-Module</span><span class="sxs-lookup"><span data-stu-id="fea5a-184">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="fea5a-185">Select-Object</span><span class="sxs-lookup"><span data-stu-id="fea5a-185">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="fea5a-186">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="fea5a-186">Uninstall-Module</span></span>](Uninstall-Module.md)

