---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: ae3d0e3c9f70381884f3e12b19111e4c4eb47307
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203909"
---
# <span data-ttu-id="84f83-103">Install-Script</span><span class="sxs-lookup"><span data-stu-id="84f83-103">Install-Script</span></span>

## <span data-ttu-id="84f83-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="84f83-104">SYNOPSIS</span></span>
<span data-ttu-id="84f83-105">Installe un script.</span><span class="sxs-lookup"><span data-stu-id="84f83-105">Installs a script.</span></span>

## <span data-ttu-id="84f83-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="84f83-106">SYNTAX</span></span>

### <span data-ttu-id="84f83-107">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="84f83-107">NameParameterSet (Default)</span></span>

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]

```

### <span data-ttu-id="84f83-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="84f83-108">InputObject</span></span>

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="84f83-109">Description</span><span class="sxs-lookup"><span data-stu-id="84f83-109">DESCRIPTION</span></span>

<span data-ttu-id="84f83-110">L' `Install-Script` applet de commande acquiert une charge utile de script à partir d’un référentiel, vérifie que la charge utile est un script PowerShell valide et copie le fichier de script vers un emplacement d’installation spécifié.</span><span class="sxs-lookup"><span data-stu-id="84f83-110">The `Install-Script` cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="84f83-111">Les référentiels par défaut `Install-Script` fonctionnent sur peuvent être configurés par le biais des `Register-PSRepository` applets de commande,, `Set-PSRepository` `Unregister-PSRepository` et `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="84f83-111">The default repositories `Install-Script` operates against are configurable through the `Register-PSRepository`, `Set-PSRepository`, `Unregister-PSRepository`, and `Get-PSRepository` cmdlets.</span></span> <span data-ttu-id="84f83-112">En cas de fonctionnement sur plusieurs dépôts, `Install-Script` installe le premier script qui correspond aux critères de recherche spécifiés ( **Name** , **MinimumVersion** ou **MaximumVersion** ) à partir du premier référentiel sans aucune erreur.</span><span class="sxs-lookup"><span data-stu-id="84f83-112">When operating against multiple repositories, `Install-Script` installs the first script that matches the specified search criteria ( **Name** , **MinimumVersion** , or **MaximumVersion** ) from the first repository without any error.</span></span>

## <span data-ttu-id="84f83-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="84f83-113">EXAMPLES</span></span>

### <span data-ttu-id="84f83-114">Exemple 1 : Rechercher un script et l’installer</span><span class="sxs-lookup"><span data-stu-id="84f83-114">Example 1: Find a script and install it</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

<span data-ttu-id="84f83-115">La première commande recherche le script nommé `Required-Script2` à partir du référentiel local1 et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="84f83-115">The first command finds the script named `Required-Script2` from the Local1 repository and displays the results.</span></span>

<span data-ttu-id="84f83-116">La deuxième commande recherche le `Required-Script2` script, puis utilise l’opérateur de pipeline pour le passer à l' `Install-Script` applet de commande pour l’installer.</span><span class="sxs-lookup"><span data-stu-id="84f83-116">The second command finds the `Required-Script2` script, and then uses the pipeline operator to pass it to the `Install-Script` cmdlet to install it.</span></span>

<span data-ttu-id="84f83-117">La troisième commande utilise l' `Get-Command` applet de commande pour obtenir `Required-Script2` , puis affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="84f83-117">The third command uses the `Get-Command` cmdlet to get `Required-Script2`, and then displays the results.</span></span>

<span data-ttu-id="84f83-118">La quatrième commande utilise l' `Get-InstalledScript` applet de commande pour obtenir `Required-Script2` et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="84f83-118">The fourth command uses the `Get-InstalledScript` cmdlet to get `Required-Script2` and display the results.</span></span>

<span data-ttu-id="84f83-119">La cinquième commande récupère `Required-Script2` et utilise l’opérateur de pipeline pour la passer à l' `Format-List` applet de commande afin de mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="84f83-119">The fifth command gets `Required-Script2` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="84f83-120">Exemple 2 : installer un script avec l’étendue AllUsers</span><span class="sxs-lookup"><span data-stu-id="84f83-120">Example 2: Install a script with AllUsers scope</span></span>

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

<span data-ttu-id="84f83-121">La première commande installe le script nommé `Required-Script3` et lui attribue l’étendue ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="84f83-121">The first command installs the script named `Required-Script3` and assigns it AllUsers scope.</span></span>

<span data-ttu-id="84f83-122">La deuxième commande obtient le script installé `Required-Script3` et affiche des informations à son sujet.</span><span class="sxs-lookup"><span data-stu-id="84f83-122">The second command gets the installed script `Required-Script3` and displays information about it.</span></span>

<span data-ttu-id="84f83-123">La troisième commande récupère `Required-Script3` et utilise l’opérateur de pipeline pour la passer à l' `Format-List` applet de commande afin de mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="84f83-123">The third command gets `Required-Script3` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="84f83-124">Exemple 3 : installer un script et ses dépendances</span><span class="sxs-lookup"><span data-stu-id="84f83-124">Example 3: Install a script and its dependencies</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

<span data-ttu-id="84f83-125">La première commande recherche le script nommé `Script-WithDependencies2` et ses dépendances dans le référentiel local1 et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="84f83-125">The first command finds the script named `Script-WithDependencies2` and its dependencies in the Local1 repository and displays the results.</span></span>

<span data-ttu-id="84f83-126">La deuxième commande installe `Script-WithDependencies2` .</span><span class="sxs-lookup"><span data-stu-id="84f83-126">The second command installs `Script-WithDependencies2`.</span></span>

<span data-ttu-id="84f83-127">La troisième commande utilise l' `Get-InstalledScript` applet de commande script pour obtenir les scripts installés et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="84f83-127">The third command uses the `Get-InstalledScript` script cmdlet to get installed scripts and display the results.</span></span>

<span data-ttu-id="84f83-128">La quatrième commande utilise l' `Get-InstalledModule` applet de commande pour obtenir les modules installés et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="84f83-128">The fourth command uses the `Get-InstalledModule` cmdlet to get installed modules and display the results.</span></span>

<span data-ttu-id="84f83-129">La cinquième commande utilise l' `Find-Script` applet de commande pour rechercher les scripts dont le nom commence par `Required-Script` et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="84f83-129">The fifth command uses the `Find-Script` cmdlet to find scripts where the name begins with `Required-Script` and display the results.</span></span>

<span data-ttu-id="84f83-130">La sixième commande installe les scripts dont le nom commence par `Required-Script` dans le référentiel local1.</span><span class="sxs-lookup"><span data-stu-id="84f83-130">The sixth command installs the scripts where the name begins with `Required-Script` in the Local1 repository.</span></span>

<span data-ttu-id="84f83-131">La commande finale obtient les scripts installés et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="84f83-131">The final command gets installed scripts and displays the results.</span></span>

## <span data-ttu-id="84f83-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="84f83-132">PARAMETERS</span></span>

### <span data-ttu-id="84f83-133">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="84f83-133">-AcceptLicense</span></span>

<span data-ttu-id="84f83-134">Accepter automatiquement le contrat de licence au cours de l’installation si le module l’exige.</span><span class="sxs-lookup"><span data-stu-id="84f83-134">Automatically accept the license agreement during installation if the module requires it.</span></span>

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

### <span data-ttu-id="84f83-135">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="84f83-135">-AllowPrerelease</span></span>

<span data-ttu-id="84f83-136">Vous permet d’installer un script marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="84f83-136">Allows you to install a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="84f83-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="84f83-137">-Confirm</span></span>

<span data-ttu-id="84f83-138">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="84f83-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="84f83-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="84f83-139">-Credential</span></span>

<span data-ttu-id="84f83-140">Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour installer un script pour un fournisseur de package ou une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="84f83-140">Specifies a user account that has rights to install a script for a specified package provider or source.</span></span>

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

### <span data-ttu-id="84f83-141">-Force</span><span class="sxs-lookup"><span data-stu-id="84f83-141">-Force</span></span>

<span data-ttu-id="84f83-142">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="84f83-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="84f83-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="84f83-143">-InputObject</span></span>

<span data-ttu-id="84f83-144">Utilisé pour l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="84f83-144">Used for pipeline input.</span></span>

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

### <span data-ttu-id="84f83-145">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="84f83-145">-MaximumVersion</span></span>

<span data-ttu-id="84f83-146">Spécifie la version maximale d’un seul script à installer.</span><span class="sxs-lookup"><span data-stu-id="84f83-146">Specifies the maximum version of a single scripts to install.</span></span> <span data-ttu-id="84f83-147">Vous ne pouvez pas ajouter ce paramètre si vous tentez d’installer plusieurs scripts.</span><span class="sxs-lookup"><span data-stu-id="84f83-147">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="84f83-148">Les paramètres **MaximumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="84f83-148">The **MaximumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="84f83-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="84f83-149">-MinimumVersion</span></span>

<span data-ttu-id="84f83-150">Spécifie la version minimale d’un script unique à installer.</span><span class="sxs-lookup"><span data-stu-id="84f83-150">Specifies the minimum version of a single script to install.</span></span> <span data-ttu-id="84f83-151">Vous ne pouvez pas ajouter ce paramètre si vous tentez d’installer plusieurs scripts.</span><span class="sxs-lookup"><span data-stu-id="84f83-151">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="84f83-152">Les paramètres **MinimumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="84f83-152">The **MinimumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="84f83-153">-Name</span><span class="sxs-lookup"><span data-stu-id="84f83-153">-Name</span></span>

<span data-ttu-id="84f83-154">Spécifie un tableau de noms de scripts à installer.</span><span class="sxs-lookup"><span data-stu-id="84f83-154">Specifies an array of names of scripts to install.</span></span>

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

### <span data-ttu-id="84f83-155">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="84f83-155">-NoPathUpdate</span></span>

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

### <span data-ttu-id="84f83-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="84f83-156">-PassThru</span></span>

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

### <span data-ttu-id="84f83-157">-Proxy</span><span class="sxs-lookup"><span data-stu-id="84f83-157">-Proxy</span></span>

<span data-ttu-id="84f83-158">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="84f83-158">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="84f83-159">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="84f83-159">-ProxyCredential</span></span>

<span data-ttu-id="84f83-160">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="84f83-160">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="84f83-161">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="84f83-161">-Repository</span></span>

<span data-ttu-id="84f83-162">Spécifie le nom convivial d’un référentiel inscrit avec l’applet de commande `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="84f83-162">Specifies the friendly name of a repository that has been registered with the `Register-PSRepository` cmdlet.</span></span> <span data-ttu-id="84f83-163">La valeur par défaut est tous les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="84f83-163">The default is all registered repositories.</span></span>

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

### <span data-ttu-id="84f83-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="84f83-164">-RequiredVersion</span></span>

<span data-ttu-id="84f83-165">Spécifie le numéro de version exact du script à installer.</span><span class="sxs-lookup"><span data-stu-id="84f83-165">Specifies the exact version number of the script to install.</span></span>

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

### <span data-ttu-id="84f83-166">-Étendue</span><span class="sxs-lookup"><span data-stu-id="84f83-166">-Scope</span></span>

<span data-ttu-id="84f83-167">Spécifie l’étendue d’installation du script.</span><span class="sxs-lookup"><span data-stu-id="84f83-167">Specifies the installation scope of the script.</span></span>
<span data-ttu-id="84f83-168">Les valeurs valides sont : AllUsers et CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="84f83-168">Valid values are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="84f83-169">L’étendue AllUsers permet d’installer les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur, c’est-à-dire `$env:ProgramFiles\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="84f83-169">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, `$env:ProgramFiles\WindowsPowerShell\Scripts`.</span></span>

<span data-ttu-id="84f83-170">L’étendue CurrentUser permet d’installer les modules uniquement dans `$home\Documents\WindowsPowerShell\Scripts` , afin que le module ne soit disponible que pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="84f83-170">The CurrentUser scope lets modules be installed only to `$home\Documents\WindowsPowerShell\Scripts`, so that the module is available only to the current user.</span></span>

<span data-ttu-id="84f83-171">Quand aucune **étendue** n’est définie, la valeur par défaut est définie en fonction de la session active :</span><span class="sxs-lookup"><span data-stu-id="84f83-171">When no **Scope** is defined, the default will be set based on the current session:</span></span>

- <span data-ttu-id="84f83-172">Pour une session PowerShell avec élévation de privilèges, l' **étendue** est définie par défaut sur ALLUSERS ;</span><span class="sxs-lookup"><span data-stu-id="84f83-172">For an elevated PowerShell session, **Scope** defaults to AllUsers;</span></span>
- <span data-ttu-id="84f83-173">Pour les sessions PowerShell non élevées dans [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) et ultérieures, la **portée** est CurrentUser ;</span><span class="sxs-lookup"><span data-stu-id="84f83-173">For non-elevated PowerShell sessions in [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) and above, **Scope** is CurrentUser;</span></span>
- <span data-ttu-id="84f83-174">Pour les sessions PowerShell non élevées dans PowerShellGet versions 1.6.7 et antérieures, la **portée** n’est pas définie et `Install-Module` échoue.</span><span class="sxs-lookup"><span data-stu-id="84f83-174">For non-elevated PowerShell sessions in PowerShellGet versions 1.6.7 and earlier, **Scope** is undefined, and `Install-Module` fails.</span></span>

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

### <span data-ttu-id="84f83-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="84f83-175">-WhatIf</span></span>

<span data-ttu-id="84f83-176">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="84f83-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="84f83-177">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="84f83-177">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="84f83-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="84f83-178">CommonParameters</span></span>

<span data-ttu-id="84f83-179">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="84f83-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="84f83-180">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="84f83-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="84f83-181">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="84f83-181">INPUTS</span></span>

### <span data-ttu-id="84f83-182">System.String[]</span><span class="sxs-lookup"><span data-stu-id="84f83-182">System.String[]</span></span>

### <span data-ttu-id="84f83-183">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="84f83-183">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="84f83-184">System.String</span><span class="sxs-lookup"><span data-stu-id="84f83-184">System.String</span></span>

### <span data-ttu-id="84f83-185">System.Uri</span><span class="sxs-lookup"><span data-stu-id="84f83-185">System.Uri</span></span>

### <span data-ttu-id="84f83-186">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="84f83-186">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="84f83-187">SORTIES</span><span class="sxs-lookup"><span data-stu-id="84f83-187">OUTPUTS</span></span>

### <span data-ttu-id="84f83-188">System.Object</span><span class="sxs-lookup"><span data-stu-id="84f83-188">System.Object</span></span>
## <span data-ttu-id="84f83-189">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="84f83-189">NOTES</span></span>

## <span data-ttu-id="84f83-190">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="84f83-190">RELATED LINKS</span></span>

[<span data-ttu-id="84f83-191">Find-Script</span><span class="sxs-lookup"><span data-stu-id="84f83-191">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="84f83-192">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="84f83-192">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="84f83-193">Save-Script</span><span class="sxs-lookup"><span data-stu-id="84f83-193">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="84f83-194">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="84f83-194">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="84f83-195">Update-Script</span><span class="sxs-lookup"><span data-stu-id="84f83-195">Update-Script</span></span>](Update-Script.md)
