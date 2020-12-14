---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: ee94ba7808cb364306826325cfbc3df2cf9834a5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892584"
---
# <span data-ttu-id="44b68-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="44b68-103">Update-Module</span></span>

## <span data-ttu-id="44b68-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="44b68-104">SYNOPSIS</span></span>
<span data-ttu-id="44b68-105">Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="44b68-105">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="44b68-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="44b68-106">SYNTAX</span></span>

### <span data-ttu-id="44b68-107">Tous</span><span class="sxs-lookup"><span data-stu-id="44b68-107">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="44b68-108">Description</span><span class="sxs-lookup"><span data-stu-id="44b68-108">DESCRIPTION</span></span>

<span data-ttu-id="44b68-109">L' `Update-Module` applet de commande installe la version la plus récente d’un module à partir d’une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="44b68-109">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="44b68-110">Vous êtes invité à confirmer la mise à jour avant son installation.</span><span class="sxs-lookup"><span data-stu-id="44b68-110">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="44b68-111">Les mises à jour sont installées uniquement pour les modules qui ont été installés sur l’ordinateur local avec `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="44b68-111">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="44b68-112">`Update-Module` recherche `$env:PSModulePath` les modules installés.</span><span class="sxs-lookup"><span data-stu-id="44b68-112">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="44b68-113">`Update-Module` Si aucun paramètre n’est spécifié, tous les modules installés sont mis à jour.</span><span class="sxs-lookup"><span data-stu-id="44b68-113">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="44b68-114">Pour spécifier un module à mettre à jour, utilisez le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="44b68-114">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="44b68-115">Vous pouvez mettre à jour vers une version spécifique d’un module à l’aide du paramètre **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="44b68-115">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="44b68-116">Si un module installé est déjà la version la plus récente, le module n’est pas mis à jour.</span><span class="sxs-lookup"><span data-stu-id="44b68-116">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="44b68-117">Si le module est introuvable dans `$env:PSModulePath` , une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="44b68-117">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="44b68-118">Pour afficher les modules installés, utilisez `Get-InstalledModule` .</span><span class="sxs-lookup"><span data-stu-id="44b68-118">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="44b68-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="44b68-119">EXAMPLES</span></span>

### <span data-ttu-id="44b68-120">Exemple 1 : mettre à jour tous les modules</span><span class="sxs-lookup"><span data-stu-id="44b68-120">Example 1: Update all modules</span></span>

<span data-ttu-id="44b68-121">Cet exemple met à jour tous les modules installés vers la version la plus récente dans une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="44b68-121">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="44b68-122">Exemple 2 : mettre à jour un module par nom</span><span class="sxs-lookup"><span data-stu-id="44b68-122">Example 2: Update a module by name</span></span>

<span data-ttu-id="44b68-123">Cet exemple met à jour un module spécifique vers la version la plus récente dans une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="44b68-123">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="44b68-124">`Update-Module` utilise le paramètre **Name** pour mettre à jour un module spécifique, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="44b68-124">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl**.</span></span>

### <span data-ttu-id="44b68-125">Exemple 3 : afficher les Update-Module les exécutions</span><span class="sxs-lookup"><span data-stu-id="44b68-125">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="44b68-126">Cet exemple fait un scénario de simulation pour montrer ce qui se passe si `Update-Module` est exécuté.</span><span class="sxs-lookup"><span data-stu-id="44b68-126">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="44b68-127">La commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="44b68-127">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="44b68-128">`Update-Module` utilise le paramètre **WhatIf** pour afficher ce qui se passerait si `Update-Module` était exécuté.</span><span class="sxs-lookup"><span data-stu-id="44b68-128">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="44b68-129">Exemple 4 : mettre à jour un module vers une version spécifiée</span><span class="sxs-lookup"><span data-stu-id="44b68-129">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="44b68-130">Dans cet exemple, un module est mis à jour vers une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="44b68-130">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="44b68-131">La version doit exister dans la galerie en ligne ou une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="44b68-131">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="44b68-132">`Update-Module` utilise le paramètre **Name** pour spécifier le module, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="44b68-132">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="44b68-133">Le paramètre **RequiredVersion** spécifie la version, **1.0.14**.</span><span class="sxs-lookup"><span data-stu-id="44b68-133">The **RequiredVersion** parameter specifies the version, **1.0.14**.</span></span>

### <span data-ttu-id="44b68-134">Exemple 5 : mettre à jour un module sans confirmation</span><span class="sxs-lookup"><span data-stu-id="44b68-134">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="44b68-135">Cet exemple ne demande pas de confirmation pour mettre à jour le module vers la version la plus récente d’une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="44b68-135">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="44b68-136">Si le module est déjà installé, le paramètre **force** réinstalle le module.</span><span class="sxs-lookup"><span data-stu-id="44b68-136">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="44b68-137">`Update-Module` utilise le paramètre **Name** pour spécifier le module, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="44b68-137">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="44b68-138">Le paramètre **force** met à jour le module sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44b68-138">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="44b68-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="44b68-139">PARAMETERS</span></span>

### <span data-ttu-id="44b68-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="44b68-140">-AcceptLicense</span></span>

<span data-ttu-id="44b68-141">Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="44b68-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="44b68-142">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="44b68-142">-AllowPrerelease</span></span>

<span data-ttu-id="44b68-143">Vous permet de mettre à jour un module avec le module le plus récent marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="44b68-143">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="44b68-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="44b68-144">-Confirm</span></span>

<span data-ttu-id="44b68-145">Vous invite à confirmer l’exécution `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="44b68-145">Prompts you for confirmation before running `Update-Module`.</span></span>

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

### <span data-ttu-id="44b68-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="44b68-146">-Credential</span></span>

<span data-ttu-id="44b68-147">Spécifie un compte d’utilisateur qui a l’autorisation de mettre à jour un module.</span><span class="sxs-lookup"><span data-stu-id="44b68-147">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="44b68-148">-Force</span><span class="sxs-lookup"><span data-stu-id="44b68-148">-Force</span></span>

<span data-ttu-id="44b68-149">Force une mise à jour de chaque module spécifié sans demander de confirmation.</span><span class="sxs-lookup"><span data-stu-id="44b68-149">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="44b68-150">Si le module est déjà installé, **force** réinstalle le module.</span><span class="sxs-lookup"><span data-stu-id="44b68-150">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="44b68-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="44b68-151">-MaximumVersion</span></span>

<span data-ttu-id="44b68-152">Spécifie la version maximale d’un module unique à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="44b68-152">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="44b68-153">Vous ne pouvez pas ajouter ce paramètre si vous tentez de mettre à jour plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="44b68-153">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="44b68-154">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="44b68-154">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="44b68-155">-Name</span><span class="sxs-lookup"><span data-stu-id="44b68-155">-Name</span></span>

<span data-ttu-id="44b68-156">Spécifie les noms d’un ou plusieurs modules à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="44b68-156">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="44b68-157">`Update-Module` recherche `$env:PSModulePath` les modules à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="44b68-157">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="44b68-158">Si aucune correspondance n’est trouvée dans `$env:PSModulePath` pour le nom de module spécifié, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="44b68-158">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="44b68-159">Les caractères génériques sont acceptés dans les noms de module.</span><span class="sxs-lookup"><span data-stu-id="44b68-159">Wildcards are accepted in module names.</span></span> <span data-ttu-id="44b68-160">Si vous ajoutez des caractères génériques au nom spécifié et qu’aucune correspondance n’est trouvée, aucune erreur ne se produit.</span><span class="sxs-lookup"><span data-stu-id="44b68-160">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

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

### <span data-ttu-id="44b68-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="44b68-161">-PassThru</span></span>

<span data-ttu-id="44b68-162">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="44b68-162">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="44b68-163">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="44b68-163">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="44b68-164">La prise en charge du paramètre **PassThru** a été ajoutée à **PowerShellGet** 2.0.0</span><span class="sxs-lookup"><span data-stu-id="44b68-164">The **PassThru** parameter support was added in **PowerShellGet** 2.0.0</span></span>

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

### <span data-ttu-id="44b68-165">-Proxy</span><span class="sxs-lookup"><span data-stu-id="44b68-165">-Proxy</span></span>

<span data-ttu-id="44b68-166">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="44b68-166">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="44b68-167">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="44b68-167">-ProxyCredential</span></span>

<span data-ttu-id="44b68-168">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="44b68-168">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="44b68-169">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="44b68-169">-RequiredVersion</span></span>

<span data-ttu-id="44b68-170">Spécifie la version exacte à laquelle le module installé existant sera mis à jour.</span><span class="sxs-lookup"><span data-stu-id="44b68-170">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="44b68-171">La version spécifiée par **RequiredVersion** doit exister dans la galerie en ligne ou une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="44b68-171">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="44b68-172">Si plusieurs modules sont mis à jour dans une même commande, vous ne pouvez pas utiliser **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="44b68-172">If more than one module is updated in a single command, you can't use **RequiredVersion**.</span></span>

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

### <span data-ttu-id="44b68-173">-Étendue</span><span class="sxs-lookup"><span data-stu-id="44b68-173">-Scope</span></span>

<span data-ttu-id="44b68-174">Spécifie l’étendue d’installation du module.</span><span class="sxs-lookup"><span data-stu-id="44b68-174">Specifies the installation scope of the module.</span></span> <span data-ttu-id="44b68-175">Les valeurs acceptables pour ce paramètre sont **ALLUSERS** et **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="44b68-175">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span> <span data-ttu-id="44b68-176">Si **scope** n’est pas spécifié, la mise à jour est installée dans l’étendue **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="44b68-176">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="44b68-177">L’étendue **ALLUSERS** nécessite des autorisations élevées et installe les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="44b68-177">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="44b68-178">Le **CurrentUser** ne requiert pas d’autorisations élevées et installe les modules dans un emplacement accessible uniquement à l’utilisateur actuel de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="44b68-178">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="44b68-179">Si aucune **étendue** n’est définie, la valeur par défaut est définie en fonction de la version PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="44b68-179">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="44b68-180">Dans PowerShellGet versions 2.0.0 et ultérieures, la valeur par défaut est **ALLUSERS** lors de l’exécution d’une session avec élévation de privilèges et **CurrentUser** pour tous les autres.</span><span class="sxs-lookup"><span data-stu-id="44b68-180">In PowerShellGet versions 2.0.0 and above, the default is **AllUsers** when running an elevated session and **CurrentUser** for all others.</span></span>
- <span data-ttu-id="44b68-181">Dans les versions de PowerShellGet 1. x, la valeur par défaut est **ALLUSERS**, ce qui nécessite une élévation pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="44b68-181">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

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

### <span data-ttu-id="44b68-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="44b68-182">-WhatIf</span></span>

<span data-ttu-id="44b68-183">Montre ce qui se passe si `Update-Module` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="44b68-183">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="44b68-184">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="44b68-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="44b68-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44b68-185">CommonParameters</span></span>

<span data-ttu-id="44b68-186">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="44b68-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44b68-187">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="44b68-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44b68-188">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="44b68-188">INPUTS</span></span>

### <span data-ttu-id="44b68-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="44b68-189">System.String[]</span></span>

### <span data-ttu-id="44b68-190">System.String</span><span class="sxs-lookup"><span data-stu-id="44b68-190">System.String</span></span>

### <span data-ttu-id="44b68-191">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="44b68-191">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="44b68-192">System.Uri</span><span class="sxs-lookup"><span data-stu-id="44b68-192">System.Uri</span></span>

## <span data-ttu-id="44b68-193">SORTIES</span><span class="sxs-lookup"><span data-stu-id="44b68-193">OUTPUTS</span></span>

### <span data-ttu-id="44b68-194">System.Object</span><span class="sxs-lookup"><span data-stu-id="44b68-194">System.Object</span></span>

## <span data-ttu-id="44b68-195">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="44b68-195">NOTES</span></span>

<span data-ttu-id="44b68-196">Pour PowerShell 5,1 ou les versions antérieures, l’étendue par défaut dans une session avec élévation de privilèges est **ALLUSERS**, et dans une session non élevée, **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="44b68-196">For PowerShell 5.1 or below, the default scope in an elevated session is **AllUsers**, and in a non-elevated session, **CurrentUser**.</span></span> <span data-ttu-id="44b68-197">Les mises à jour de module pour **ALLUSERS**, `$env:ProgramFiles\PowerShell\Modules` , ont besoin d’autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="44b68-197">Module updates for **AllUsers**, `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span> <span data-ttu-id="44b68-198">Les mises à jour de module pour **CurrentUser**, `$home\Documents\PowerShell\Modules` , n’ont pas besoin d’autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="44b68-198">Module updates for **CurrentUser**, `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44b68-199">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="44b68-199">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="44b68-200">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="44b68-200">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="44b68-201">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="44b68-201">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="44b68-202">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44b68-202">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="44b68-203">`Update-Module` s’exécute sur les versions PowerShell 3,0 ou ultérieures de PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="44b68-203">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="44b68-204">Si le module que vous spécifiez avec le paramètre **Name** n’a pas été installé à l’aide de `Install-Module` , une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="44b68-204">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="44b68-205">Vous ne pouvez exécuter que `Update-Module` sur les modules que vous avez installés à partir de la galerie en ligne en exécutant `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="44b68-205">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="44b68-206">Si `Update-Module` tente de mettre à jour les fichiers binaires qui sont en cours d’utilisation, `Update-Module` retourne une erreur qui identifie les processus posant problème.</span><span class="sxs-lookup"><span data-stu-id="44b68-206">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="44b68-207">L’utilisateur est informé de nouvelles tentatives `Update-Module` une fois les processus arrêtés.</span><span class="sxs-lookup"><span data-stu-id="44b68-207">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="44b68-208">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="44b68-208">RELATED LINKS</span></span>

[<span data-ttu-id="44b68-209">Find-Module</span><span class="sxs-lookup"><span data-stu-id="44b68-209">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="44b68-210">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="44b68-210">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="44b68-211">Install-Module</span><span class="sxs-lookup"><span data-stu-id="44b68-211">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="44b68-212">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="44b68-212">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="44b68-213">Module Uninstall</span><span class="sxs-lookup"><span data-stu-id="44b68-213">Uninstall-Module</span></span>](Uninstall-Module.md)
