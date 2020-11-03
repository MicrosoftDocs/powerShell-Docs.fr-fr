---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: 29ba3907a349257f63e127739786ab6e210c0f82
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201390"
---
# <span data-ttu-id="8b89c-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="8b89c-103">Update-Module</span></span>

## <span data-ttu-id="8b89c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8b89c-104">SYNOPSIS</span></span>
<span data-ttu-id="8b89c-105">Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8b89c-105">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="8b89c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b89c-106">SYNTAX</span></span>

### <span data-ttu-id="8b89c-107">Tous</span><span class="sxs-lookup"><span data-stu-id="8b89c-107">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8b89c-108">Description</span><span class="sxs-lookup"><span data-stu-id="8b89c-108">DESCRIPTION</span></span>

<span data-ttu-id="8b89c-109">L' `Update-Module` applet de commande installe la version la plus récente d’un module à partir d’une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="8b89c-109">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="8b89c-110">Vous êtes invité à confirmer la mise à jour avant son installation.</span><span class="sxs-lookup"><span data-stu-id="8b89c-110">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="8b89c-111">Les mises à jour sont installées uniquement pour les modules qui ont été installés sur l’ordinateur local avec `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="8b89c-111">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="8b89c-112">`Update-Module` recherche `$env:PSModulePath` les modules installés.</span><span class="sxs-lookup"><span data-stu-id="8b89c-112">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="8b89c-113">`Update-Module` Si aucun paramètre n’est spécifié, tous les modules installés sont mis à jour.</span><span class="sxs-lookup"><span data-stu-id="8b89c-113">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="8b89c-114">Pour spécifier un module à mettre à jour, utilisez le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-114">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="8b89c-115">Vous pouvez mettre à jour vers une version spécifique d’un module à l’aide du paramètre **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-115">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="8b89c-116">Si un module installé est déjà la version la plus récente, le module n’est pas mis à jour.</span><span class="sxs-lookup"><span data-stu-id="8b89c-116">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="8b89c-117">Si le module est introuvable dans `$env:PSModulePath` , une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8b89c-117">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="8b89c-118">Pour afficher les modules installés, utilisez `Get-InstalledModule` .</span><span class="sxs-lookup"><span data-stu-id="8b89c-118">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="8b89c-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8b89c-119">EXAMPLES</span></span>

### <span data-ttu-id="8b89c-120">Exemple 1 : mettre à jour tous les modules</span><span class="sxs-lookup"><span data-stu-id="8b89c-120">Example 1: Update all modules</span></span>

<span data-ttu-id="8b89c-121">Cet exemple met à jour tous les modules installés vers la version la plus récente dans une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="8b89c-121">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="8b89c-122">Exemple 2 : mettre à jour un module par nom</span><span class="sxs-lookup"><span data-stu-id="8b89c-122">Example 2: Update a module by name</span></span>

<span data-ttu-id="8b89c-123">Cet exemple met à jour un module spécifique vers la version la plus récente dans une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="8b89c-123">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="8b89c-124">`Update-Module` utilise le paramètre **Name** pour mettre à jour un module spécifique, **SpeculationControl** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-124">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl** .</span></span>

### <span data-ttu-id="8b89c-125">Exemple 3 : afficher les Update-Module les exécutions</span><span class="sxs-lookup"><span data-stu-id="8b89c-125">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="8b89c-126">Cet exemple fait un scénario de simulation pour montrer ce qui se passe si `Update-Module` est exécuté.</span><span class="sxs-lookup"><span data-stu-id="8b89c-126">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="8b89c-127">La commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8b89c-127">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="8b89c-128">`Update-Module` utilise le paramètre **WhatIf** pour afficher ce qui se passerait si `Update-Module` était exécuté.</span><span class="sxs-lookup"><span data-stu-id="8b89c-128">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="8b89c-129">Exemple 4 : mettre à jour un module vers une version spécifiée</span><span class="sxs-lookup"><span data-stu-id="8b89c-129">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="8b89c-130">Dans cet exemple, un module est mis à jour vers une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="8b89c-130">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="8b89c-131">La version doit exister dans la galerie en ligne ou une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8b89c-131">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="8b89c-132">`Update-Module` utilise le paramètre **Name** pour spécifier le module, **SpeculationControl** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-132">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl** .</span></span> <span data-ttu-id="8b89c-133">Le paramètre **RequiredVersion** spécifie la version, **1.0.14** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-133">The **RequiredVersion** parameter specifies the version, **1.0.14** .</span></span>

### <span data-ttu-id="8b89c-134">Exemple 5 : mettre à jour un module sans confirmation</span><span class="sxs-lookup"><span data-stu-id="8b89c-134">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="8b89c-135">Cet exemple ne demande pas de confirmation pour mettre à jour le module vers la version la plus récente d’une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="8b89c-135">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="8b89c-136">Si le module est déjà installé, le paramètre **force** réinstalle le module.</span><span class="sxs-lookup"><span data-stu-id="8b89c-136">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="8b89c-137">`Update-Module` utilise le paramètre **Name** pour spécifier le module, **SpeculationControl** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-137">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl** .</span></span> <span data-ttu-id="8b89c-138">Le paramètre **force** met à jour le module sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8b89c-138">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="8b89c-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b89c-139">PARAMETERS</span></span>

### <span data-ttu-id="8b89c-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="8b89c-140">-AcceptLicense</span></span>

<span data-ttu-id="8b89c-141">Accepter automatiquement le contrat de licence au cours de l’installation si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="8b89c-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="8b89c-142">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="8b89c-142">-AllowPrerelease</span></span>

<span data-ttu-id="8b89c-143">Vous permet de mettre à jour un module avec le module le plus récent marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="8b89c-143">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="8b89c-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8b89c-144">-Confirm</span></span>

<span data-ttu-id="8b89c-145">Vous invite à confirmer l’exécution `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="8b89c-145">Prompts you for confirmation before running `Update-Module`.</span></span>

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

### <span data-ttu-id="8b89c-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="8b89c-146">-Credential</span></span>

<span data-ttu-id="8b89c-147">Spécifie un compte d’utilisateur qui a l’autorisation de mettre à jour un module.</span><span class="sxs-lookup"><span data-stu-id="8b89c-147">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="8b89c-148">-Force</span><span class="sxs-lookup"><span data-stu-id="8b89c-148">-Force</span></span>

<span data-ttu-id="8b89c-149">Force une mise à jour de chaque module spécifié sans demander de confirmation.</span><span class="sxs-lookup"><span data-stu-id="8b89c-149">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="8b89c-150">Si le module est déjà installé, **force** réinstalle le module.</span><span class="sxs-lookup"><span data-stu-id="8b89c-150">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="8b89c-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="8b89c-151">-MaximumVersion</span></span>

<span data-ttu-id="8b89c-152">Spécifie la version maximale d’un module unique à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="8b89c-152">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="8b89c-153">Vous ne pouvez pas ajouter ce paramètre si vous tentez de mettre à jour plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="8b89c-153">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="8b89c-154">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="8b89c-154">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="8b89c-155">-Name</span><span class="sxs-lookup"><span data-stu-id="8b89c-155">-Name</span></span>

<span data-ttu-id="8b89c-156">Spécifie les noms d’un ou plusieurs modules à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="8b89c-156">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="8b89c-157">`Update-Module` recherche `$env:PSModulePath` les modules à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="8b89c-157">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="8b89c-158">Si aucune correspondance n’est trouvée dans `$env:PSModulePath` pour le nom de module spécifié, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="8b89c-158">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="8b89c-159">Les caractères génériques sont acceptés dans les noms de module.</span><span class="sxs-lookup"><span data-stu-id="8b89c-159">Wildcards are accepted in module names.</span></span> <span data-ttu-id="8b89c-160">Si vous ajoutez des caractères génériques au nom spécifié et qu’aucune correspondance n’est trouvée, aucune erreur ne se produit.</span><span class="sxs-lookup"><span data-stu-id="8b89c-160">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

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

### <span data-ttu-id="8b89c-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8b89c-161">-PassThru</span></span>

<span data-ttu-id="8b89c-162">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="8b89c-162">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="8b89c-163">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="8b89c-163">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8b89c-164">-Proxy</span><span class="sxs-lookup"><span data-stu-id="8b89c-164">-Proxy</span></span>

<span data-ttu-id="8b89c-165">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="8b89c-165">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="8b89c-166">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="8b89c-166">-ProxyCredential</span></span>

<span data-ttu-id="8b89c-167">Spécifie un compte d’utilisateur qui a l’autorisation d’utiliser le serveur proxy spécifié par le paramètre **proxy** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-167">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="8b89c-168">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="8b89c-168">-RequiredVersion</span></span>

<span data-ttu-id="8b89c-169">Spécifie la version exacte à laquelle le module installé existant sera mis à jour.</span><span class="sxs-lookup"><span data-stu-id="8b89c-169">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="8b89c-170">La version spécifiée par **RequiredVersion** doit exister dans la galerie en ligne ou une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8b89c-170">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="8b89c-171">Si plusieurs modules sont mis à jour dans une même commande, vous ne pouvez pas utiliser **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-171">If more than one module is updated in a single command, you can't use **RequiredVersion** .</span></span>

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

### <span data-ttu-id="8b89c-172">-Étendue</span><span class="sxs-lookup"><span data-stu-id="8b89c-172">-Scope</span></span>

<span data-ttu-id="8b89c-173">Spécifie l’étendue d’installation du module.</span><span class="sxs-lookup"><span data-stu-id="8b89c-173">Specifies the installation scope of the module.</span></span> <span data-ttu-id="8b89c-174">Les valeurs acceptables pour ce paramètre sont **ALLUSERS** et **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-174">The acceptable values for this parameter are **AllUsers** and **CurrentUser** .</span></span> <span data-ttu-id="8b89c-175">Si **scope** n’est pas spécifié, la mise à jour est installée dans l’étendue **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-175">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="8b89c-176">L’étendue **ALLUSERS** nécessite des autorisations élevées et installe les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="8b89c-176">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="8b89c-177">Le **CurrentUser** ne requiert pas d’autorisations élevées et installe les modules dans un emplacement accessible uniquement à l’utilisateur actuel de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="8b89c-177">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="8b89c-178">Si aucune **étendue** n’est définie, la valeur par défaut est définie en fonction de la version PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8b89c-178">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="8b89c-179">Dans PowerShellGet versions 2.1.0 et ultérieures, la valeur par défaut est **CurrentUser** , ce qui ne nécessite pas d’élévation pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="8b89c-179">In PowerShellGet versions 2.1.0 and above, the default is **CurrentUser** , which does not require elevation for install.</span></span>
- <span data-ttu-id="8b89c-180">Dans les versions PowerShellGet 1. x-2.0. x, le paramètre d' **étendue** n’est pas disponible et la valeur par défaut est **ALLUSERS** , ce qui nécessite une élévation pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="8b89c-180">In PowerShellGet 1.x - 2.0.x versions, the **Scope** parameter is not available and the default is **AllUsers** , which requires elevation for install.</span></span>

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

### <span data-ttu-id="8b89c-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8b89c-181">-WhatIf</span></span>

<span data-ttu-id="8b89c-182">Montre ce qui se passe si `Update-Module` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8b89c-182">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="8b89c-183">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8b89c-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="8b89c-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b89c-184">CommonParameters</span></span>

<span data-ttu-id="8b89c-185">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b89c-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b89c-186">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8b89c-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b89c-187">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8b89c-187">INPUTS</span></span>

### <span data-ttu-id="8b89c-188">System.String[]</span><span class="sxs-lookup"><span data-stu-id="8b89c-188">System.String[]</span></span>

### <span data-ttu-id="8b89c-189">System.String</span><span class="sxs-lookup"><span data-stu-id="8b89c-189">System.String</span></span>

### <span data-ttu-id="8b89c-190">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="8b89c-190">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="8b89c-191">System.Uri</span><span class="sxs-lookup"><span data-stu-id="8b89c-191">System.Uri</span></span>

## <span data-ttu-id="8b89c-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8b89c-192">OUTPUTS</span></span>

### <span data-ttu-id="8b89c-193">System.Object</span><span class="sxs-lookup"><span data-stu-id="8b89c-193">System.Object</span></span>

## <span data-ttu-id="8b89c-194">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8b89c-194">NOTES</span></span>

<span data-ttu-id="8b89c-195">Pour PowerShell version 6,0 et versions ultérieures, l’étendue d’installation par défaut est toujours **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="8b89c-195">For PowerShell version 6.0 and above, the default installation scope is always **CurrentUser** .</span></span>
<span data-ttu-id="8b89c-196">Les mises à jour de module pour **CurrentUser** , `$home\Documents\PowerShell\Modules` , n’ont pas besoin d’autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="8b89c-196">Module updates for **CurrentUser** , `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span> <span data-ttu-id="8b89c-197">Les mises à jour de module pour **ALLUSERS** , `$env:ProgramFiles\PowerShell\Modules` , ont besoin d’autorisations élevées.</span><span class="sxs-lookup"><span data-stu-id="8b89c-197">Module updates for **AllUsers** , `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span>

<span data-ttu-id="8b89c-198">`Update-Module` s’exécute sur les versions PowerShell 3,0 ou ultérieures de PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="8b89c-198">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="8b89c-199">Si le module que vous spécifiez avec le paramètre **Name** n’a pas été installé à l’aide de `Install-Module` , une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="8b89c-199">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="8b89c-200">Vous ne pouvez exécuter que `Update-Module` sur les modules que vous avez installés à partir de la galerie en ligne en exécutant `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="8b89c-200">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="8b89c-201">Si `Update-Module` tente de mettre à jour les fichiers binaires qui sont en cours d’utilisation, `Update-Module` retourne une erreur qui identifie les processus posant problème.</span><span class="sxs-lookup"><span data-stu-id="8b89c-201">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="8b89c-202">L’utilisateur est informé de nouvelles tentatives `Update-Module` une fois les processus arrêtés.</span><span class="sxs-lookup"><span data-stu-id="8b89c-202">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="8b89c-203">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8b89c-203">RELATED LINKS</span></span>

[<span data-ttu-id="8b89c-204">Find-Module</span><span class="sxs-lookup"><span data-stu-id="8b89c-204">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="8b89c-205">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="8b89c-205">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="8b89c-206">Install-Module</span><span class="sxs-lookup"><span data-stu-id="8b89c-206">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="8b89c-207">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="8b89c-207">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="8b89c-208">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="8b89c-208">Uninstall-Module</span></span>](Uninstall-Module.md)
