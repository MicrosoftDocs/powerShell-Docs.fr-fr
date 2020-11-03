---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: 0e6dfd00da246b5632474c45d3794d796715240c
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205821"
---
# <span data-ttu-id="62535-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="62535-103">Install-Module</span></span>

## <span data-ttu-id="62535-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="62535-104">SYNOPSIS</span></span>
<span data-ttu-id="62535-105">Télécharge un ou plusieurs modules à partir d’un référentiel et les installe sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="62535-105">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

## <span data-ttu-id="62535-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="62535-106">SYNTAX</span></span>

### <span data-ttu-id="62535-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="62535-107">NameParameterSet (Default)</span></span>

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="62535-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="62535-108">InputObject</span></span>

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="62535-109">Description</span><span class="sxs-lookup"><span data-stu-id="62535-109">DESCRIPTION</span></span>

<span data-ttu-id="62535-110">L' `Install-Module` applet de commande obtient un ou plusieurs modules qui répondent aux critères spécifiés à partir d’un référentiel en ligne.</span><span class="sxs-lookup"><span data-stu-id="62535-110">The `Install-Module` cmdlet gets one or more modules that meet specified criteria from an online repository.</span></span> <span data-ttu-id="62535-111">L’applet de commande vérifie que les résultats de la recherche sont des modules valides et copie les dossiers du module vers l’emplacement d’installation.</span><span class="sxs-lookup"><span data-stu-id="62535-111">The cmdlet verifies that search results are valid modules and copies the module folders to the installation location.</span></span> <span data-ttu-id="62535-112">Les modules installés ne sont pas automatiquement importés après l’installation.</span><span class="sxs-lookup"><span data-stu-id="62535-112">Installed modules are not automatically imported after installation.</span></span>
<span data-ttu-id="62535-113">Vous pouvez filtrer le module installé en fonction des versions minimale, maximale et exacte des modules spécifiés.</span><span class="sxs-lookup"><span data-stu-id="62535-113">You can filter which module is installed based on the minimum, maximum, and exact versions of specified modules.</span></span>

<span data-ttu-id="62535-114">Si le module en cours d’installation a le même nom ou la même version, ou contient des commandes dans un module existant, des messages d’avertissement s’affichent.</span><span class="sxs-lookup"><span data-stu-id="62535-114">If the module being installed has the same name or version, or contains commands in an existing module, warning messages are displayed.</span></span> <span data-ttu-id="62535-115">Après avoir confirmé que vous voulez installer le module et remplacer les avertissements, utilisez les `-Force` `-AllowClobber` paramètres et.</span><span class="sxs-lookup"><span data-stu-id="62535-115">After you confirm that you want to install the module and override the warnings, use the `-Force` and `-AllowClobber` parameters.</span></span> <span data-ttu-id="62535-116">Selon les paramètres de votre référentiel, vous devrez peut-être répondre à une invite pour que l’installation du module se poursuive.</span><span class="sxs-lookup"><span data-stu-id="62535-116">Dependent upon your repository settings, you might need to answer a prompt for the module installation to continue.</span></span>

<span data-ttu-id="62535-117">Ces exemples utilisent le [PowerShell Gallery](https://www.powershellgallery.com/) comme seul référentiel enregistré.</span><span class="sxs-lookup"><span data-stu-id="62535-117">These examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="62535-118">`Get-PSRepository` affiche les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="62535-118">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="62535-119">Si vous avez plusieurs référentiels inscrits, utilisez le `-Repository` paramètre pour spécifier le nom du référentiel.</span><span class="sxs-lookup"><span data-stu-id="62535-119">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="62535-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="62535-120">EXAMPLES</span></span>

### <span data-ttu-id="62535-121">Exemple 1 : Rechercher et installer un module</span><span class="sxs-lookup"><span data-stu-id="62535-121">Example 1: Find and install a module</span></span>

<span data-ttu-id="62535-122">Cet exemple recherche un module dans le référentiel et installe le module.</span><span class="sxs-lookup"><span data-stu-id="62535-122">This example finds a module in the repository and installs the module.</span></span>

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

<span data-ttu-id="62535-123">Le `Find-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="62535-123">The `Find-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="62535-124">Par défaut, la version la plus récente du module est téléchargée à partir du référentiel.</span><span class="sxs-lookup"><span data-stu-id="62535-124">By default, the newest version of the module is downloaded from the repository.</span></span> <span data-ttu-id="62535-125">L’objet est envoyé dans le pipeline à l’applet de commande `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="62535-125">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="62535-126">`Install-Module` installe le module pour tous les utilisateurs dans `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="62535-126">`Install-Module` installs the module for all users in `$env:ProgramFiles\PowerShell\Modules`.</span></span>

### <span data-ttu-id="62535-127">Exemple 2 : installer un module par nom</span><span class="sxs-lookup"><span data-stu-id="62535-127">Example 2: Install a module by name</span></span>

<span data-ttu-id="62535-128">Dans cet exemple, la version la plus récente du module **PowerShellGet** est installée.</span><span class="sxs-lookup"><span data-stu-id="62535-128">In this example, the newest version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet
```

<span data-ttu-id="62535-129">Le `Install-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="62535-129">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="62535-130">Par défaut, la version la plus récente du module est téléchargée à partir du référentiel et installée.</span><span class="sxs-lookup"><span data-stu-id="62535-130">By default, the newest version of the module is downloaded from the repository and installed.</span></span>

### <span data-ttu-id="62535-131">Exemple 3 : installer un module en utilisant sa version minimale</span><span class="sxs-lookup"><span data-stu-id="62535-131">Example 3: Install a module using its minimum version</span></span>

<span data-ttu-id="62535-132">Dans cet exemple, la version minimale du module **PowerShellGet** est installée.</span><span class="sxs-lookup"><span data-stu-id="62535-132">In this example, the minimum version of the **PowerShellGet** module is installed.</span></span> <span data-ttu-id="62535-133">Le paramètre **MinimumVersion** spécifie la version la plus basse du module à installer.</span><span class="sxs-lookup"><span data-stu-id="62535-133">The **MinimumVersion** parameter specifies the lowest version of the module that should be installed.</span></span> <span data-ttu-id="62535-134">Si une version plus récente du module est disponible, cette version est téléchargée et installée pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="62535-134">If a newer version of the module is available, that version is downloaded and installed for all users.</span></span>

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

<span data-ttu-id="62535-135">Le `Install-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="62535-135">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="62535-136">Le paramètre **MinimumVersion** spécifie que la version **2.0.1** est téléchargée à partir du référentiel et installée.</span><span class="sxs-lookup"><span data-stu-id="62535-136">The **MinimumVersion** parameter specifies that version **2.0.1** is downloaded from the repository and installed.</span></span> <span data-ttu-id="62535-137">Étant donné que la version **2.0.4** est disponible, cette version est téléchargée et installée pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="62535-137">Because version **2.0.4** is available, that version is downloaded and installed for all users.</span></span>

### <span data-ttu-id="62535-138">Exemple 4 : installer une version spécifique d’un module</span><span class="sxs-lookup"><span data-stu-id="62535-138">Example 4: Install a specific version of a module</span></span>

<span data-ttu-id="62535-139">Dans cet exemple, une version spécifique du module **PowerShellGet** est installée.</span><span class="sxs-lookup"><span data-stu-id="62535-139">In this example, a specific version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

<span data-ttu-id="62535-140">Le `Install-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="62535-140">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="62535-141">Le paramètre **RequiredVersion** spécifie que la version **2.0.0** est téléchargée et installée pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="62535-141">The **RequiredVersion** parameter specifies that version **2.0.0** is downloaded and installed for all users.</span></span>

### <span data-ttu-id="62535-142">Exemple 5 : installer un module uniquement pour l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="62535-142">Example 5: Install a module only for the current user</span></span>

<span data-ttu-id="62535-143">Cet exemple télécharge et installe la version la plus récente d’un module, uniquement pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="62535-143">This example downloads and installs the newest version of a module, only for the current user.</span></span>

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

<span data-ttu-id="62535-144">Le `Install-Module` utilise le paramètre **Name** pour spécifier le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="62535-144">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>
<span data-ttu-id="62535-145">`Install-Module` télécharge et installe la version la plus récente de **PowerShellGet** dans le répertoire de l’utilisateur actuel, `$home\Documents\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="62535-145">`Install-Module` downloads and installs the newest version of **PowerShellGet** into the current user's directory, `$home\Documents\PowerShell\Modules`.</span></span>

## <span data-ttu-id="62535-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="62535-146">PARAMETERS</span></span>

### <span data-ttu-id="62535-147">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="62535-147">-AcceptLicense</span></span>

<span data-ttu-id="62535-148">Pour les modules qui nécessitent une licence, **AcceptLicense** accepte automatiquement le contrat de licence lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="62535-148">For modules that require a license, **AcceptLicense** automatically accepts the license agreement during installation.</span></span> <span data-ttu-id="62535-149">Pour plus d’informations, consultez [modules nécessitant l’acceptation](/powershell/scripting/gallery/concepts/module-license-acceptance)de la licence.</span><span class="sxs-lookup"><span data-stu-id="62535-149">For more information, see [Modules Requiring License Acceptance](/powershell/scripting/gallery/concepts/module-license-acceptance).</span></span>

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

### <span data-ttu-id="62535-150">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="62535-150">-AllowClobber</span></span>

<span data-ttu-id="62535-151">Remplace les messages d’avertissement relatifs aux conflits d’installation concernant les commandes existantes sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="62535-151">Overrides warning messages about installation conflicts about existing commands on a computer.</span></span>
<span data-ttu-id="62535-152">Remplace les commandes existantes qui portent le même nom que les commandes installées par un module.</span><span class="sxs-lookup"><span data-stu-id="62535-152">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>
<span data-ttu-id="62535-153">**AllowClobber** et **force** peuvent être utilisés ensemble dans une `Install-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="62535-153">**AllowClobber** and **Force** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="62535-154">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="62535-154">-AllowPrerelease</span></span>

<span data-ttu-id="62535-155">Vous permet d’installer un module marqué en tant que version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="62535-155">Allows you to install a module marked as a pre-release.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62535-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="62535-156">-Confirm</span></span>

<span data-ttu-id="62535-157">Vous invite à confirmer l’exécution de l' `Install-Module` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="62535-157">Prompts you for confirmation before running the `Install-Module` cmdlet.</span></span>

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

### <span data-ttu-id="62535-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="62535-158">-Credential</span></span>

<span data-ttu-id="62535-159">Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour installer un module pour un fournisseur de package ou une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="62535-159">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="62535-160">-Force</span><span class="sxs-lookup"><span data-stu-id="62535-160">-Force</span></span>

<span data-ttu-id="62535-161">Installe un module et remplace les messages d’avertissement relatifs aux conflits d’installation du module.</span><span class="sxs-lookup"><span data-stu-id="62535-161">Installs a module and overrides warning messages about module installation conflicts.</span></span> <span data-ttu-id="62535-162">Si un module portant le même nom existe déjà sur l’ordinateur, **force** autorise l’installation de plusieurs versions.</span><span class="sxs-lookup"><span data-stu-id="62535-162">If a module with the same name already exists on the computer, **Force** allows for multiple versions to be installed.</span></span> <span data-ttu-id="62535-163">S’il existe un module avec le même nom et la même version, **force** remplace cette version.</span><span class="sxs-lookup"><span data-stu-id="62535-163">If there is an existing module with the same name and version, **Force** overwrites that version.</span></span> <span data-ttu-id="62535-164">**Force** et **AllowClobber** peuvent être utilisés ensemble dans une `Install-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="62535-164">**Force** and **AllowClobber** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="62535-165">-InputObject</span><span class="sxs-lookup"><span data-stu-id="62535-165">-InputObject</span></span>

<span data-ttu-id="62535-166">Utilisé pour l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="62535-166">Used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="62535-167">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="62535-167">-MaximumVersion</span></span>

<span data-ttu-id="62535-168">Spécifie la version maximale d’un module unique à installer.</span><span class="sxs-lookup"><span data-stu-id="62535-168">Specifies the maximum version of a single module to install.</span></span> <span data-ttu-id="62535-169">La version installée doit être inférieure ou égale à **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="62535-169">The version installed must be less than or equal to **MaximumVersion** .</span></span> <span data-ttu-id="62535-170">Si vous souhaitez installer plusieurs modules, vous ne pouvez pas utiliser **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="62535-170">If you want to install multiple modules, you cannot use **MaximumVersion** .</span></span> <span data-ttu-id="62535-171">**MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même `Install-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="62535-171">**MaximumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="62535-172">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="62535-172">-MinimumVersion</span></span>

<span data-ttu-id="62535-173">Spécifie la version minimale d’un module unique à installer.</span><span class="sxs-lookup"><span data-stu-id="62535-173">Specifies the minimum version of a single module to install.</span></span> <span data-ttu-id="62535-174">La version installée doit être supérieure ou égale à **MinimumVersion** .</span><span class="sxs-lookup"><span data-stu-id="62535-174">The version installed must be greater than or equal to **MinimumVersion** .</span></span> <span data-ttu-id="62535-175">Si une version plus récente du module est disponible, la version la plus récente est installée.</span><span class="sxs-lookup"><span data-stu-id="62535-175">If there is a newer version of the module available, the newer version is installed.</span></span> <span data-ttu-id="62535-176">Si vous souhaitez installer plusieurs modules, vous ne pouvez pas utiliser **MinimumVersion** .</span><span class="sxs-lookup"><span data-stu-id="62535-176">If you want to install multiple modules, you cannot use **MinimumVersion** .</span></span>
<span data-ttu-id="62535-177">**MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même `Install-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="62535-177">**MinimumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="62535-178">-Name</span><span class="sxs-lookup"><span data-stu-id="62535-178">-Name</span></span>

<span data-ttu-id="62535-179">Spécifie les noms exacts des modules à installer à partir de la galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="62535-179">Specifies the exact names of modules to install from the online gallery.</span></span> <span data-ttu-id="62535-180">Une liste séparée par des virgules de noms de modules est acceptée.</span><span class="sxs-lookup"><span data-stu-id="62535-180">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="62535-181">Le nom du module doit correspondre au nom du module dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="62535-181">The module name must match the module name in the repository.</span></span> <span data-ttu-id="62535-182">Utilisez `Find-Module` pour obtenir une liste de noms de modules.</span><span class="sxs-lookup"><span data-stu-id="62535-182">Use `Find-Module` to get a list of module names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="62535-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="62535-183">-PassThru</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62535-184">-Proxy</span><span class="sxs-lookup"><span data-stu-id="62535-184">-Proxy</span></span>

<span data-ttu-id="62535-185">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="62535-185">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="62535-186">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="62535-186">-ProxyCredential</span></span>

<span data-ttu-id="62535-187">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="62535-187">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="62535-188">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="62535-188">-Repository</span></span>

<span data-ttu-id="62535-189">Utilisez le paramètre de **dépôt** pour spécifier le référentiel utilisé pour télécharger et installer un module.</span><span class="sxs-lookup"><span data-stu-id="62535-189">Use the **Repository** parameter to specify which repository is used to download and install a module.</span></span> <span data-ttu-id="62535-190">Utilisé lorsque plusieurs dépôts sont inscrits.</span><span class="sxs-lookup"><span data-stu-id="62535-190">Used when multiple repositories are registered.</span></span> <span data-ttu-id="62535-191">Spécifie le nom d’un référentiel inscrit dans la `Install-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="62535-191">Specifies the name of a registered repository in the `Install-Module` command.</span></span> <span data-ttu-id="62535-192">Pour inscrire un dépôt, utilisez `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="62535-192">To register a repository, use `Register-PSRepository`.</span></span>
<span data-ttu-id="62535-193">Pour afficher les dépôts inscrits, utilisez `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="62535-193">To display registered repositories, use `Get-PSRepository`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62535-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="62535-194">-RequiredVersion</span></span>

<span data-ttu-id="62535-195">Spécifie la version exacte d’un module unique à installer.</span><span class="sxs-lookup"><span data-stu-id="62535-195">Specifies the exact version of a single module to install.</span></span> <span data-ttu-id="62535-196">S’il n’existe aucune correspondance dans le référentiel pour la version spécifiée, une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="62535-196">If there is no match in the repository for the specified version, an error is displayed.</span></span> <span data-ttu-id="62535-197">Si vous souhaitez installer plusieurs modules, vous ne pouvez pas utiliser **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="62535-197">If you want to install multiple modules, you cannot use **RequiredVersion** .</span></span> <span data-ttu-id="62535-198">**RequiredVersion** ne peut pas être utilisé dans la même `Install-Module` commande que **MinimumVersion** ou **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="62535-198">**RequiredVersion** cannot be used in the same `Install-Module` command as **MinimumVersion** or **MaximumVersion** .</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="62535-199">-Étendue</span><span class="sxs-lookup"><span data-stu-id="62535-199">-Scope</span></span>

<span data-ttu-id="62535-200">Spécifie l’étendue d’installation du module.</span><span class="sxs-lookup"><span data-stu-id="62535-200">Specifies the installation scope of the module.</span></span> <span data-ttu-id="62535-201">Les valeurs acceptables pour ce paramètre sont **ALLUSERS** et **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="62535-201">The acceptable values for this parameter are **AllUsers** and **CurrentUser** .</span></span>

<span data-ttu-id="62535-202">L’étendue **ALLUSERS** installe les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="62535-202">The **AllUsers** scope installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="62535-203">Le **CurrentUser** installe les modules dans un emplacement accessible uniquement à l’utilisateur actuel de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="62535-203">The **CurrentUser** installs modules in a location that is accessible only to the current user of the computer.</span></span> <span data-ttu-id="62535-204">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="62535-204">For example:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="62535-205">Si aucune **étendue** n’est définie, la valeur par défaut est définie en fonction de la version PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="62535-205">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="62535-206">Dans PowerShellGet versions 2.0.0 et ultérieures, la valeur par défaut est **CurrentUser** , ce qui ne nécessite pas d’élévation pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="62535-206">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser** , which does not require elevation for install.</span></span>
- <span data-ttu-id="62535-207">Dans les versions de PowerShellGet 1. x, la valeur par défaut est **ALLUSERS** , ce qui nécessite une élévation pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="62535-207">In PowerShellGet 1.x versions, the default is **AllUsers** , which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62535-208">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="62535-208">-SkipPublisherCheck</span></span>

<span data-ttu-id="62535-209">Vous permet d’installer une version plus récente d’un module qui existe déjà sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="62535-209">Allows you to install a newer version of a module that already exists on your computer.</span></span> <span data-ttu-id="62535-210">Par exemple, lorsqu’un module existant est signé numériquement par un éditeur approuvé, mais que la nouvelle version n’est pas signée numériquement par un éditeur approuvé.</span><span class="sxs-lookup"><span data-stu-id="62535-210">For example, when an existing module is digitally signed by a trusted publisher but the new version is not digitally signed by a trusted publisher.</span></span>

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

### <span data-ttu-id="62535-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="62535-211">-WhatIf</span></span>

<span data-ttu-id="62535-212">Montre ce qui se passe si une `Install-Module` commande a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="62535-212">Shows what would happen if an `Install-Module` command was run.</span></span> <span data-ttu-id="62535-213">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="62535-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="62535-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="62535-214">CommonParameters</span></span>

<span data-ttu-id="62535-215">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="62535-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="62535-216">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="62535-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="62535-217">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="62535-217">INPUTS</span></span>

### <span data-ttu-id="62535-218">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="62535-218">PSRepositoryItemInfo</span></span>

<span data-ttu-id="62535-219">`Find-Module` crée les objets **PSRepositoryItemInfo** qui peuvent être envoyés vers le dessous du pipeline `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="62535-219">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span>

### <span data-ttu-id="62535-220">System.String[]</span><span class="sxs-lookup"><span data-stu-id="62535-220">System.String[]</span></span>

### <span data-ttu-id="62535-221">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="62535-221">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="62535-222">System.String</span><span class="sxs-lookup"><span data-stu-id="62535-222">System.String</span></span>

### <span data-ttu-id="62535-223">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="62535-223">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="62535-224">System.Uri</span><span class="sxs-lookup"><span data-stu-id="62535-224">System.Uri</span></span>

## <span data-ttu-id="62535-225">SORTIES</span><span class="sxs-lookup"><span data-stu-id="62535-225">OUTPUTS</span></span>

### <span data-ttu-id="62535-226">Microsoft. PowerShell. Commands. PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="62535-226">Microsoft.PowerShell.Commands.PSRepositoryItemInfo</span></span>

<span data-ttu-id="62535-227">Lors de l’utilisation du paramètre **PassThru** , `Install-Module` génère un objet **PSRepositoryItemInfo** pour le module.</span><span class="sxs-lookup"><span data-stu-id="62535-227">When using the **PassThru** parameter, `Install-Module` outputs a **PSRepositoryItemInfo** object for the module.</span></span> <span data-ttu-id="62535-228">Il s’agit des mêmes informations que celles que vous obteniez de l’applet de commande `Find-Module` .</span><span class="sxs-lookup"><span data-stu-id="62535-228">This is the same information that you get from the `Find-Module` cmdlet.</span></span>

## <span data-ttu-id="62535-229">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="62535-229">NOTES</span></span>

<span data-ttu-id="62535-230">`Install-Module` s’exécute sur PowerShell 5,0 ou versions ultérieures, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="62535-230">`Install-Module` runs on PowerShell 5.0 or later releases, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="62535-231">En guise de meilleure pratique de sécurité, évaluez le code d’un module avant d’exécuter des applets de commande ou des fonctions pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="62535-231">As a security best practice, evaluate a module's code before running any cmdlets or functions for the first time.</span></span> <span data-ttu-id="62535-232">Pour empêcher l’exécution de modules contenant du code malveillant, les modules installés ne sont pas automatiquement importés après l’installation.</span><span class="sxs-lookup"><span data-stu-id="62535-232">To prevent running modules that contain malicious code, installed modules are not automatically imported after installation.</span></span>

<span data-ttu-id="62535-233">Si le nom de module spécifié par le paramètre **Name** n’existe pas dans le référentiel, `Install-Module` retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="62535-233">If the module name specified by the **Name** parameter does not exist in the repository, `Install-Module` returns an error.</span></span>

<span data-ttu-id="62535-234">Pour installer plusieurs modules, utilisez le paramètre **Name** et spécifiez un tableau de noms de module séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="62535-234">To install multiple modules, use the **Name** parameter and specify a comma-separated array of module names.</span></span> <span data-ttu-id="62535-235">Si vous spécifiez plusieurs noms de module, vous ne pouvez pas utiliser **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="62535-235">If you specify multiple module names, you cannot use **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** .</span></span> <span data-ttu-id="62535-236">`Find-Module` crée les objets **PSRepositoryItemInfo** qui peuvent être envoyés vers le dessous du pipeline `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="62535-236">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span> <span data-ttu-id="62535-237">Le pipeline est une autre façon de spécifier plusieurs modules à installer dans une seule commande.</span><span class="sxs-lookup"><span data-stu-id="62535-237">The pipeline is another way to specify multiple modules to install in a single command.</span></span>

<span data-ttu-id="62535-238">Par défaut, les modules de l’étendue de **ALLUSERS** sont installés dans `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="62535-238">By default, modules for the scope of **AllUsers** are installed in `$env:ProgramFiles\PowerShell\Modules`.</span></span> <span data-ttu-id="62535-239">La valeur par défaut empêche toute confusion quand vous installez les ressources DSC (Desired State Configuration) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62535-239">The default prevents confusion when you install PowerShell Desired State Configuration (DSC) resources.</span></span>

<span data-ttu-id="62535-240">L’installation d’un module échoue et ne peut pas être importée s’il n’a pas `.psm1` `.psd1` de, ou `.dll` du même nom dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="62535-240">A module installation fails and cannot be imported if it does not have a `.psm1`, `.psd1`, or `.dll` of the same name within the folder.</span></span> <span data-ttu-id="62535-241">Utilisez le paramètre **force** pour installer le module.</span><span class="sxs-lookup"><span data-stu-id="62535-241">Use the **Force** parameter to install the module.</span></span>

<span data-ttu-id="62535-242">Si la version d’un module existant correspond au nom spécifié par le paramètre **Name** et que le paramètre **MinimumVersion** ou **RequiredVersion** n’est pas utilisé, `Install-Module` continue sans assistance, mais n’installe pas le module.</span><span class="sxs-lookup"><span data-stu-id="62535-242">If an existing module's version matches the name specified by the **Name** parameter, and the **MinimumVersion** or **RequiredVersion** parameter are not used, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="62535-243">Si la version d’un module existant est supérieure à la valeur du paramètre **MinimumVersion** ou égale à la valeur du paramètre **RequiredVersion** , `Install-Module` continue sans assistance, mais n’installe pas le module.</span><span class="sxs-lookup"><span data-stu-id="62535-243">If an existing module's version is greater than the value of the **MinimumVersion** parameter, or equal to the value of the **RequiredVersion** parameter, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="62535-244">Si le module existant ne correspond pas aux valeurs spécifiées par les paramètres **MinimumVersion** ou **RequiredVersion** , une erreur se produit dans la `Install-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="62535-244">If the existing module does not match the values specified by the **MinimumVersion** or **RequiredVersion** parameters, an error occurs in the `Install-Module` command.</span></span> <span data-ttu-id="62535-245">Par exemple, si la version du module installé existant est inférieure à la valeur **MinimumVersion** ou différente de la valeur **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="62535-245">For example, if the version of the existing installed module is lower than the **MinimumVersion** value or not equal to the **RequiredVersion** value.</span></span>

<span data-ttu-id="62535-246">Une installation de module installe également tous les modules dépendants spécifiés comme requis par l’éditeur du module.</span><span class="sxs-lookup"><span data-stu-id="62535-246">A module installation will also install any dependent modules specified as required by the module publisher.</span></span>
<span data-ttu-id="62535-247">L’éditeur spécifie les modules requis et leurs versions dans le manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="62535-247">The publisher will specify the required modules and their versions in the module manifest.</span></span>

## <span data-ttu-id="62535-248">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="62535-248">RELATED LINKS</span></span>

[<span data-ttu-id="62535-249">Find-Module</span><span class="sxs-lookup"><span data-stu-id="62535-249">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="62535-250">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="62535-250">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="62535-251">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="62535-251">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="62535-252">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="62535-252">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="62535-253">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="62535-253">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="62535-254">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="62535-254">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="62535-255">Update-Module</span><span class="sxs-lookup"><span data-stu-id="62535-255">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="62535-256">about_Module</span><span class="sxs-lookup"><span data-stu-id="62535-256">about_Module</span></span>](../Microsoft.PowerShell.Core/About/about_Modules.md)
