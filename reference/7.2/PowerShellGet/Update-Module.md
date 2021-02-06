---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: f29c208805894634960085cd3816ce7780b7602f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99599003"
---
# <span data-ttu-id="96ab8-102">Update-Module</span><span class="sxs-lookup"><span data-stu-id="96ab8-102">Update-Module</span></span>

## <span data-ttu-id="96ab8-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="96ab8-103">SYNOPSIS</span></span>
<span data-ttu-id="96ab8-104">Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="96ab8-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="96ab8-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="96ab8-105">SYNTAX</span></span>

### <span data-ttu-id="96ab8-106">Tous</span><span class="sxs-lookup"><span data-stu-id="96ab8-106">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="96ab8-107">Description</span><span class="sxs-lookup"><span data-stu-id="96ab8-107">DESCRIPTION</span></span>

<span data-ttu-id="96ab8-108">L' `Update-Module` applet de commande installe la version la plus récente d’un module à partir d’une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="96ab8-108">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="96ab8-109">Vous êtes invité à confirmer la mise à jour avant son installation.</span><span class="sxs-lookup"><span data-stu-id="96ab8-109">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="96ab8-110">Les mises à jour sont installées uniquement pour les modules qui ont été installés sur l’ordinateur local avec `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="96ab8-110">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="96ab8-111">`Update-Module` recherche `$env:PSModulePath` les modules installés.</span><span class="sxs-lookup"><span data-stu-id="96ab8-111">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="96ab8-112">`Update-Module` Si aucun paramètre n’est spécifié, tous les modules installés sont mis à jour.</span><span class="sxs-lookup"><span data-stu-id="96ab8-112">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="96ab8-113">Pour spécifier un module à mettre à jour, utilisez le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="96ab8-113">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="96ab8-114">Vous pouvez mettre à jour vers une version spécifique d’un module à l’aide du paramètre **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="96ab8-114">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="96ab8-115">Si un module installé est déjà la version la plus récente, le module n’est pas mis à jour.</span><span class="sxs-lookup"><span data-stu-id="96ab8-115">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="96ab8-116">Si le module est introuvable dans `$env:PSModulePath` , une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="96ab8-116">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="96ab8-117">Pour afficher les modules installés, utilisez `Get-InstalledModule` .</span><span class="sxs-lookup"><span data-stu-id="96ab8-117">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="96ab8-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="96ab8-118">EXAMPLES</span></span>

### <span data-ttu-id="96ab8-119">Exemple 1 : mettre à jour tous les modules</span><span class="sxs-lookup"><span data-stu-id="96ab8-119">Example 1: Update all modules</span></span>

<span data-ttu-id="96ab8-120">Cet exemple met à jour tous les modules installés vers la version la plus récente dans une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="96ab8-120">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="96ab8-121">Exemple 2 : mettre à jour un module par nom</span><span class="sxs-lookup"><span data-stu-id="96ab8-121">Example 2: Update a module by name</span></span>

<span data-ttu-id="96ab8-122">Cet exemple met à jour un module spécifique vers la version la plus récente dans une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="96ab8-122">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="96ab8-123">`Update-Module` utilise le paramètre **Name** pour mettre à jour un module spécifique, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="96ab8-123">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl**.</span></span>

### <span data-ttu-id="96ab8-124">Exemple 3 : afficher les Update-Module les exécutions</span><span class="sxs-lookup"><span data-stu-id="96ab8-124">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="96ab8-125">Cet exemple fait un scénario de simulation pour montrer ce qui se passe si `Update-Module` est exécuté.</span><span class="sxs-lookup"><span data-stu-id="96ab8-125">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="96ab8-126">La commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="96ab8-126">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="96ab8-127">`Update-Module` utilise le paramètre **WhatIf** pour afficher ce qui se passerait si `Update-Module` était exécuté.</span><span class="sxs-lookup"><span data-stu-id="96ab8-127">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="96ab8-128">Exemple 4 : mettre à jour un module vers une version spécifiée</span><span class="sxs-lookup"><span data-stu-id="96ab8-128">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="96ab8-129">Dans cet exemple, un module est mis à jour vers une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="96ab8-129">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="96ab8-130">La version doit exister dans la galerie en ligne ou une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="96ab8-130">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="96ab8-131">`Update-Module` utilise le paramètre **Name** pour spécifier le module, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="96ab8-131">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="96ab8-132">Le paramètre **RequiredVersion** spécifie la version, **1.0.14**.</span><span class="sxs-lookup"><span data-stu-id="96ab8-132">The **RequiredVersion** parameter specifies the version, **1.0.14**.</span></span>

### <span data-ttu-id="96ab8-133">Exemple 5 : mettre à jour un module sans confirmation</span><span class="sxs-lookup"><span data-stu-id="96ab8-133">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="96ab8-134">Cet exemple ne demande pas de confirmation pour mettre à jour le module vers la version la plus récente d’une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="96ab8-134">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="96ab8-135">Si le module est déjà installé, le paramètre **force** réinstalle le module.</span><span class="sxs-lookup"><span data-stu-id="96ab8-135">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="96ab8-136">`Update-Module` utilise le paramètre **Name** pour spécifier le module, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="96ab8-136">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="96ab8-137">Le paramètre **force** met à jour le module sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="96ab8-137">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="96ab8-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="96ab8-138">PARAMETERS</span></span>

### <span data-ttu-id="96ab8-139">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="96ab8-139">-AcceptLicense</span></span>

<span data-ttu-id="96ab8-140">Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="96ab8-140">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="96ab8-141">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="96ab8-141">-AllowPrerelease</span></span>

<span data-ttu-id="96ab8-142">Vous permet de mettre à jour un module avec le module le plus récent marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="96ab8-142">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="96ab8-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="96ab8-143">-Confirm</span></span>

<span data-ttu-id="96ab8-144">Vous invite à confirmer l’exécution `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="96ab8-144">Prompts you for confirmation before running `Update-Module`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ab8-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="96ab8-145">-Credential</span></span>

<span data-ttu-id="96ab8-146">Spécifie un compte d’utilisateur qui a l’autorisation de mettre à jour un module.</span><span class="sxs-lookup"><span data-stu-id="96ab8-146">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="96ab8-147">-Force</span><span class="sxs-lookup"><span data-stu-id="96ab8-147">-Force</span></span>

<span data-ttu-id="96ab8-148">Force une mise à jour de chaque module spécifié sans demander de confirmation.</span><span class="sxs-lookup"><span data-stu-id="96ab8-148">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="96ab8-149">Si le module est déjà installé, **force** réinstalle le module.</span><span class="sxs-lookup"><span data-stu-id="96ab8-149">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="96ab8-150">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="96ab8-150">-MaximumVersion</span></span>

<span data-ttu-id="96ab8-151">Spécifie la version maximale d’un module unique à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="96ab8-151">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="96ab8-152">Vous ne pouvez pas ajouter ce paramètre si vous tentez de mettre à jour plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="96ab8-152">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="96ab8-153">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="96ab8-153">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="96ab8-154">-Name</span><span class="sxs-lookup"><span data-stu-id="96ab8-154">-Name</span></span>

<span data-ttu-id="96ab8-155">Spécifie les noms d’un ou plusieurs modules à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="96ab8-155">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="96ab8-156">`Update-Module` recherche `$env:PSModulePath` les modules à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="96ab8-156">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="96ab8-157">Si aucune correspondance n’est trouvée dans `$env:PSModulePath` pour le nom de module spécifié, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="96ab8-157">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="96ab8-158">Les caractères génériques sont acceptés dans les noms de module.</span><span class="sxs-lookup"><span data-stu-id="96ab8-158">Wildcards are accepted in module names.</span></span> <span data-ttu-id="96ab8-159">Si vous ajoutez des caractères génériques au nom spécifié et qu’aucune correspondance n’est trouvée, aucune erreur ne se produit.</span><span class="sxs-lookup"><span data-stu-id="96ab8-159">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

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

### <span data-ttu-id="96ab8-160">-PassThru</span><span class="sxs-lookup"><span data-stu-id="96ab8-160">-PassThru</span></span>

<span data-ttu-id="96ab8-161">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="96ab8-161">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="96ab8-162">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="96ab8-162">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="96ab8-163">-Proxy</span><span class="sxs-lookup"><span data-stu-id="96ab8-163">-Proxy</span></span>

<span data-ttu-id="96ab8-164">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="96ab8-164">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="96ab8-165">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="96ab8-165">-ProxyCredential</span></span>

<span data-ttu-id="96ab8-166">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="96ab8-166">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="96ab8-167">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="96ab8-167">-RequiredVersion</span></span>

<span data-ttu-id="96ab8-168">Spécifie la version exacte à laquelle le module installé existant sera mis à jour.</span><span class="sxs-lookup"><span data-stu-id="96ab8-168">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="96ab8-169">La version spécifiée par **RequiredVersion** doit exister dans la galerie en ligne ou une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="96ab8-169">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="96ab8-170">Si plusieurs modules sont mis à jour dans une même commande, vous ne pouvez pas utiliser **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="96ab8-170">If more than one module is updated in a single command, you can't use **RequiredVersion**.</span></span>

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

### <span data-ttu-id="96ab8-171">-Étendue</span><span class="sxs-lookup"><span data-stu-id="96ab8-171">-Scope</span></span>

<span data-ttu-id="96ab8-172">Spécifie l’étendue d’installation du module.</span><span class="sxs-lookup"><span data-stu-id="96ab8-172">Specifies the installation scope of the module.</span></span> <span data-ttu-id="96ab8-173">Les valeurs acceptables pour ce paramètre sont **ALLUSERS** et **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="96ab8-173">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span> <span data-ttu-id="96ab8-174">Si **scope** n’est pas spécifié, la mise à jour est installée dans l’étendue **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="96ab8-174">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="96ab8-175">L’étendue **ALLUSERS** nécessite des autorisations élevées et installe les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="96ab8-175">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="96ab8-176">Le **CurrentUser** ne requiert pas d’autorisations élevées et installe les modules dans un emplacement accessible uniquement à l’utilisateur actuel de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="96ab8-176">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="96ab8-177">Si aucune **étendue** n’est définie, la valeur par défaut est définie en fonction de la version PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="96ab8-177">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="96ab8-178">Dans PowerShellGet versions 2.0.0 et ultérieures, la valeur par défaut est **CurrentUser**, ce qui ne nécessite pas d’élévation pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="96ab8-178">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser**, which does not require elevation for install.</span></span>
- <span data-ttu-id="96ab8-179">Dans les versions de PowerShellGet 1. x, la valeur par défaut est **ALLUSERS**, ce qui nécessite une élévation pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="96ab8-179">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ab8-180">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="96ab8-180">-WhatIf</span></span>

<span data-ttu-id="96ab8-181">Montre ce qui se passe si `Update-Module` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="96ab8-181">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="96ab8-182">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="96ab8-182">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96ab8-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96ab8-183">CommonParameters</span></span>

<span data-ttu-id="96ab8-184">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="96ab8-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="96ab8-185">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="96ab8-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="96ab8-186">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="96ab8-186">INPUTS</span></span>

### <span data-ttu-id="96ab8-187">System.String[]</span><span class="sxs-lookup"><span data-stu-id="96ab8-187">System.String[]</span></span>

### <span data-ttu-id="96ab8-188">System.String</span><span class="sxs-lookup"><span data-stu-id="96ab8-188">System.String</span></span>

### <span data-ttu-id="96ab8-189">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="96ab8-189">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="96ab8-190">System.Uri</span><span class="sxs-lookup"><span data-stu-id="96ab8-190">System.Uri</span></span>

## <span data-ttu-id="96ab8-191">SORTIES</span><span class="sxs-lookup"><span data-stu-id="96ab8-191">OUTPUTS</span></span>

### <span data-ttu-id="96ab8-192">System.Object</span><span class="sxs-lookup"><span data-stu-id="96ab8-192">System.Object</span></span>

## <span data-ttu-id="96ab8-193">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="96ab8-193">NOTES</span></span>

<span data-ttu-id="96ab8-194">Pour PowerShell version 6,0 et versions ultérieures, l’étendue d’installation par défaut est toujours **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="96ab8-194">For PowerShell version 6.0 and above, the default installation scope is always **CurrentUser**.</span></span>
<span data-ttu-id="96ab8-195">Les mises à jour de module pour **CurrentUser**, `$home\Documents\PowerShell\Modules` , n’ont pas besoin d’autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="96ab8-195">Module updates for **CurrentUser**, `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span> <span data-ttu-id="96ab8-196">Les mises à jour de module pour **ALLUSERS**, `$env:ProgramFiles\PowerShell\Modules` , ont besoin d’autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="96ab8-196">Module updates for **AllUsers**, `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96ab8-197">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="96ab8-197">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="96ab8-198">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="96ab8-198">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="96ab8-199">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="96ab8-199">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="96ab8-200">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96ab8-200">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="96ab8-201">`Update-Module` s’exécute sur les versions PowerShell 3,0 ou ultérieures de PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="96ab8-201">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="96ab8-202">Si le module que vous spécifiez avec le paramètre **Name** n’a pas été installé à l’aide de `Install-Module` , une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="96ab8-202">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="96ab8-203">Vous ne pouvez exécuter que `Update-Module` sur les modules que vous avez installés à partir de la galerie en ligne en exécutant `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="96ab8-203">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="96ab8-204">Si `Update-Module` tente de mettre à jour les fichiers binaires qui sont en cours d’utilisation, `Update-Module` retourne une erreur qui identifie les processus posant problème.</span><span class="sxs-lookup"><span data-stu-id="96ab8-204">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="96ab8-205">L’utilisateur est informé de nouvelles tentatives `Update-Module` une fois les processus arrêtés.</span><span class="sxs-lookup"><span data-stu-id="96ab8-205">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="96ab8-206">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="96ab8-206">RELATED LINKS</span></span>

[<span data-ttu-id="96ab8-207">Find-Module</span><span class="sxs-lookup"><span data-stu-id="96ab8-207">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="96ab8-208">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="96ab8-208">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="96ab8-209">Install-Module</span><span class="sxs-lookup"><span data-stu-id="96ab8-209">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="96ab8-210">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="96ab8-210">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="96ab8-211">Module Uninstall</span><span class="sxs-lookup"><span data-stu-id="96ab8-211">Uninstall-Module</span></span>](Uninstall-Module.md)
