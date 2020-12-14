---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 9aff0ff794bea42da7690a77357c1d76f747a004
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892155"
---
# <span data-ttu-id="a122e-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="a122e-103">Save-Module</span></span>

## <span data-ttu-id="a122e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a122e-104">SYNOPSIS</span></span>
<span data-ttu-id="a122e-105">Enregistre un module et ses dépendances sur l’ordinateur local, mais n’installe pas le module.</span><span class="sxs-lookup"><span data-stu-id="a122e-105">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="a122e-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a122e-106">SYNTAX</span></span>

### <span data-ttu-id="a122e-107">NameAndPathParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a122e-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a122e-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="a122e-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a122e-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="a122e-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a122e-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="a122e-110">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a122e-111">Description</span><span class="sxs-lookup"><span data-stu-id="a122e-111">DESCRIPTION</span></span>

<span data-ttu-id="a122e-112">L' `Save-Module` applet de commande télécharge un module et toutes les dépendances à partir d’un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="a122e-112">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="a122e-113">`Save-Module` télécharge et enregistre la version la plus récente d’un module.</span><span class="sxs-lookup"><span data-stu-id="a122e-113">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="a122e-114">Les fichiers sont enregistrés dans un chemin d’accès spécifié sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a122e-114">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="a122e-115">Le module n’est pas installé, mais le contenu est disponible pour inspection par un administrateur.</span><span class="sxs-lookup"><span data-stu-id="a122e-115">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="a122e-116">Le module enregistré peut ensuite être copié à l' `$env:PSModulePath` emplacement approprié de l’ordinateur hors connexion.</span><span class="sxs-lookup"><span data-stu-id="a122e-116">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="a122e-117">`Get-PSRepository` affiche les référentiels inscrits de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a122e-117">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="a122e-118">Vous pouvez utiliser l' `Find-Module` applet de commande pour rechercher des dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="a122e-118">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="a122e-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a122e-119">EXAMPLES</span></span>

### <span data-ttu-id="a122e-120">Exemple 1 : enregistrer un module</span><span class="sxs-lookup"><span data-stu-id="a122e-120">Example 1: Save a module</span></span>

<span data-ttu-id="a122e-121">Dans cet exemple, un module et ses dépendances sont enregistrés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a122e-121">In this example, a module and its dependencies are saved to the local computer.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

<span data-ttu-id="a122e-122">`Save-Module` utilise le paramètre **Name** pour spécifier le module, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="a122e-122">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="a122e-123">Le paramètre **path** spécifie l’emplacement où stocker le module téléchargé.</span><span class="sxs-lookup"><span data-stu-id="a122e-123">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="a122e-124">Le paramètre de **dépôt** spécifie un référentiel inscrit, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="a122e-124">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="a122e-125">Une fois le téléchargement terminé, `Get-ChildItem` affiche le contenu du **chemin d’accès** où les fichiers sont stockés.</span><span class="sxs-lookup"><span data-stu-id="a122e-125">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="a122e-126">Exemple 2 : enregistrer une version spécifique d’un module</span><span class="sxs-lookup"><span data-stu-id="a122e-126">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="a122e-127">Cet exemple montre comment utiliser un paramètre tel que **MaximumVersion** ou **RequiredVersion** pour spécifier une version de module.</span><span class="sxs-lookup"><span data-stu-id="a122e-127">This example shows how to use a parameter such as **MaximumVersion**, or **RequiredVersion** to specify a module version.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

<span data-ttu-id="a122e-128">`Save-Module` utilise le paramètre **Name** pour spécifier le module, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="a122e-128">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="a122e-129">Le paramètre **path** spécifie l’emplacement où stocker le module téléchargé.</span><span class="sxs-lookup"><span data-stu-id="a122e-129">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="a122e-130">Le paramètre de **dépôt** spécifie un référentiel inscrit, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="a122e-130">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="a122e-131">**MaximumVersion** spécifie que la version **2.1.0** est téléchargée et enregistrée.</span><span class="sxs-lookup"><span data-stu-id="a122e-131">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="a122e-132">Une fois le téléchargement terminé, `Get-ChildItem` affiche le contenu du **chemin d’accès** où les fichiers sont stockés.</span><span class="sxs-lookup"><span data-stu-id="a122e-132">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="a122e-133">Exemple 3 : Rechercher et enregistrer une version spécifique d’un module</span><span class="sxs-lookup"><span data-stu-id="a122e-133">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="a122e-134">Dans cet exemple, une version de module obligatoire est trouvée dans le référentiel et enregistrée sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a122e-134">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

<span data-ttu-id="a122e-135">`Find-Module` utilise le paramètre **Name** pour spécifier le module, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="a122e-135">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="a122e-136">Le paramètre de **dépôt** spécifie un référentiel inscrit, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="a122e-136">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="a122e-137">**RequiredVersion** spécifie la version **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="a122e-137">**RequiredVersion** specifies version **1.6.5**.</span></span>

<span data-ttu-id="a122e-138">L’objet est envoyé dans le pipeline à `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="a122e-138">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="a122e-139">Le paramètre **path** spécifie l’emplacement où stocker le module téléchargé.</span><span class="sxs-lookup"><span data-stu-id="a122e-139">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="a122e-140">Une fois le téléchargement terminé, `Get-ChildItem` affiche le contenu du **chemin d’accès** où les fichiers sont stockés.</span><span class="sxs-lookup"><span data-stu-id="a122e-140">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="a122e-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a122e-141">PARAMETERS</span></span>

### <span data-ttu-id="a122e-142">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="a122e-142">-AcceptLicense</span></span>

<span data-ttu-id="a122e-143">Accepter automatiquement le contrat de licence si le package l’exige.</span><span class="sxs-lookup"><span data-stu-id="a122e-143">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="a122e-144">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="a122e-144">-AllowPrerelease</span></span>

<span data-ttu-id="a122e-145">Vous permet d’enregistrer un module marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="a122e-145">Allows you to save a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a122e-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a122e-146">-Confirm</span></span>

<span data-ttu-id="a122e-147">Vous invite à confirmer l’exécution de l' `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="a122e-147">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="a122e-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="a122e-148">-Credential</span></span>

<span data-ttu-id="a122e-149">Spécifie un compte d’utilisateur qui dispose des droits d’enregistrement d’un module.</span><span class="sxs-lookup"><span data-stu-id="a122e-149">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="a122e-150">-Force</span><span class="sxs-lookup"><span data-stu-id="a122e-150">-Force</span></span>

<span data-ttu-id="a122e-151">Force l' `Save-Module` exécution sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a122e-151">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a122e-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a122e-152">-InputObject</span></span>

<span data-ttu-id="a122e-153">Accepte un objet **PSRepositoryItemInfo** .</span><span class="sxs-lookup"><span data-stu-id="a122e-153">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="a122e-154">Par exemple, `Find-Module` la sortie vers une variable et l’utilisation de cette variable en tant qu’argument **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="a122e-154">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a122e-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a122e-155">-LiteralPath</span></span>

<span data-ttu-id="a122e-156">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="a122e-156">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a122e-157">La valeur du paramètre **LiteralPath** est utilisée exactement comme entrée.</span><span class="sxs-lookup"><span data-stu-id="a122e-157">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="a122e-158">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a122e-158">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a122e-159">Si le chemin d’accès comprend des caractères d’échappement, placez-les entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a122e-159">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="a122e-160">PowerShell n’interprète pas les caractères placés entre guillemets simples comme séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a122e-160">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a122e-161">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a122e-161">-MaximumVersion</span></span>

<span data-ttu-id="a122e-162">Spécifie la version maximale ou la plus récente du module à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="a122e-162">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="a122e-163">Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="a122e-163">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a122e-164">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a122e-164">-MinimumVersion</span></span>

<span data-ttu-id="a122e-165">Spécifie la version minimale d’un module unique à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="a122e-165">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="a122e-166">Vous ne pouvez pas ajouter ce paramètre si vous tentez d’installer plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="a122e-166">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="a122e-167">Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="a122e-167">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a122e-168">-Name</span><span class="sxs-lookup"><span data-stu-id="a122e-168">-Name</span></span>

<span data-ttu-id="a122e-169">Spécifie un tableau de noms de modules à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="a122e-169">Specifies an array of names of modules to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a122e-170">-Path</span><span class="sxs-lookup"><span data-stu-id="a122e-170">-Path</span></span>

<span data-ttu-id="a122e-171">Spécifie l’emplacement sur l’ordinateur local où stocker un module enregistré.</span><span class="sxs-lookup"><span data-stu-id="a122e-171">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="a122e-172">Accepte les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="a122e-172">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a122e-173">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a122e-173">-Proxy</span></span>

<span data-ttu-id="a122e-174">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="a122e-174">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="a122e-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a122e-175">-ProxyCredential</span></span>

<span data-ttu-id="a122e-176">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="a122e-176">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="a122e-177">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="a122e-177">-Repository</span></span>

<span data-ttu-id="a122e-178">Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="a122e-178">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="a122e-179">Utilisez `Get-PSRepository` pour afficher les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="a122e-179">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a122e-180">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a122e-180">-RequiredVersion</span></span>

<span data-ttu-id="a122e-181">Spécifie le numéro de version exact du module à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="a122e-181">Specifies the exact version number of the module to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a122e-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a122e-182">-WhatIf</span></span>

<span data-ttu-id="a122e-183">Montre ce qui se passerait si le `Save-Module` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="a122e-183">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="a122e-184">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a122e-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a122e-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a122e-185">CommonParameters</span></span>

<span data-ttu-id="a122e-186">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a122e-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a122e-187">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a122e-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a122e-188">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a122e-188">INPUTS</span></span>

### <span data-ttu-id="a122e-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a122e-189">System.String[]</span></span>

### <span data-ttu-id="a122e-190">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="a122e-190">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="a122e-191">System.String</span><span class="sxs-lookup"><span data-stu-id="a122e-191">System.String</span></span>

### <span data-ttu-id="a122e-192">System.Uri</span><span class="sxs-lookup"><span data-stu-id="a122e-192">System.Uri</span></span>

### <span data-ttu-id="a122e-193">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="a122e-193">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="a122e-194">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a122e-194">OUTPUTS</span></span>

### <span data-ttu-id="a122e-195">System.Object</span><span class="sxs-lookup"><span data-stu-id="a122e-195">System.Object</span></span>

## <span data-ttu-id="a122e-196">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a122e-196">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a122e-197">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="a122e-197">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a122e-198">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a122e-198">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a122e-199">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="a122e-199">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a122e-200">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a122e-200">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a122e-201">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a122e-201">RELATED LINKS</span></span>
