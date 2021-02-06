---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: e2574121cc6b8500f0c5e9e0f76ac25d1c081a8c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99595501"
---
# <span data-ttu-id="5b93a-102">Install-Script</span><span class="sxs-lookup"><span data-stu-id="5b93a-102">Install-Script</span></span>

## <span data-ttu-id="5b93a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5b93a-103">SYNOPSIS</span></span>
<span data-ttu-id="5b93a-104">Installe un script.</span><span class="sxs-lookup"><span data-stu-id="5b93a-104">Installs a script.</span></span>

## <span data-ttu-id="5b93a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="5b93a-105">SYNTAX</span></span>

### <span data-ttu-id="5b93a-106">NameParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="5b93a-106">NameParameterSet (Default)</span></span>

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5b93a-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="5b93a-107">InputObject</span></span>

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5b93a-108">Description</span><span class="sxs-lookup"><span data-stu-id="5b93a-108">DESCRIPTION</span></span>

<span data-ttu-id="5b93a-109">L' `Install-Script` applet de commande acquiert une charge utile de script à partir d’un référentiel, vérifie que la charge utile est un script PowerShell valide et copie le fichier de script vers un emplacement d’installation spécifié.</span><span class="sxs-lookup"><span data-stu-id="5b93a-109">The `Install-Script` cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="5b93a-110">Les référentiels par défaut `Install-Script` fonctionnent sur peuvent être configurés par le biais des `Register-PSRepository` applets de commande,, `Set-PSRepository` `Unregister-PSRepository` et `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="5b93a-110">The default repositories `Install-Script` operates against are configurable through the `Register-PSRepository`, `Set-PSRepository`, `Unregister-PSRepository`, and `Get-PSRepository` cmdlets.</span></span> <span data-ttu-id="5b93a-111">En cas de fonctionnement sur plusieurs dépôts, `Install-Script` installe le premier script qui correspond aux critères de recherche spécifiés (**Name**, **MinimumVersion** ou **MaximumVersion**) à partir du premier référentiel sans aucune erreur.</span><span class="sxs-lookup"><span data-stu-id="5b93a-111">When operating against multiple repositories, `Install-Script` installs the first script that matches the specified search criteria (**Name**, **MinimumVersion**, or **MaximumVersion**) from the first repository without any error.</span></span>

## <span data-ttu-id="5b93a-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5b93a-112">EXAMPLES</span></span>

### <span data-ttu-id="5b93a-113">Exemple 1 : Rechercher un script et l’installer</span><span class="sxs-lookup"><span data-stu-id="5b93a-113">Example 1: Find a script and install it</span></span>

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

<span data-ttu-id="5b93a-114">La première commande recherche le script nommé `Required-Script2` à partir du référentiel local1 et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b93a-114">The first command finds the script named `Required-Script2` from the Local1 repository and displays the results.</span></span>

<span data-ttu-id="5b93a-115">La deuxième commande recherche le `Required-Script2` script, puis utilise l’opérateur de pipeline pour le passer à l' `Install-Script` applet de commande pour l’installer.</span><span class="sxs-lookup"><span data-stu-id="5b93a-115">The second command finds the `Required-Script2` script, and then uses the pipeline operator to pass it to the `Install-Script` cmdlet to install it.</span></span>

<span data-ttu-id="5b93a-116">La troisième commande utilise l' `Get-Command` applet de commande pour obtenir `Required-Script2` , puis affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b93a-116">The third command uses the `Get-Command` cmdlet to get `Required-Script2`, and then displays the results.</span></span>

<span data-ttu-id="5b93a-117">La quatrième commande utilise l' `Get-InstalledScript` applet de commande pour obtenir `Required-Script2` et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b93a-117">The fourth command uses the `Get-InstalledScript` cmdlet to get `Required-Script2` and display the results.</span></span>

<span data-ttu-id="5b93a-118">La cinquième commande récupère `Required-Script2` et utilise l’opérateur de pipeline pour la passer à l' `Format-List` applet de commande afin de mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="5b93a-118">The fifth command gets `Required-Script2` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="5b93a-119">Exemple 2 : installer un script avec l’étendue AllUsers</span><span class="sxs-lookup"><span data-stu-id="5b93a-119">Example 2: Install a script with AllUsers scope</span></span>

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

<span data-ttu-id="5b93a-120">La première commande installe le script nommé `Required-Script3` et lui attribue l’étendue ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="5b93a-120">The first command installs the script named `Required-Script3` and assigns it AllUsers scope.</span></span>

<span data-ttu-id="5b93a-121">La deuxième commande obtient le script installé `Required-Script3` et affiche des informations à son sujet.</span><span class="sxs-lookup"><span data-stu-id="5b93a-121">The second command gets the installed script `Required-Script3` and displays information about it.</span></span>

<span data-ttu-id="5b93a-122">La troisième commande récupère `Required-Script3` et utilise l’opérateur de pipeline pour la passer à l' `Format-List` applet de commande afin de mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="5b93a-122">The third command gets `Required-Script3` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="5b93a-123">Exemple 3 : installer un script et ses dépendances</span><span class="sxs-lookup"><span data-stu-id="5b93a-123">Example 3: Install a script and its dependencies</span></span>

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

<span data-ttu-id="5b93a-124">La première commande recherche le script nommé `Script-WithDependencies2` et ses dépendances dans le référentiel local1 et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b93a-124">The first command finds the script named `Script-WithDependencies2` and its dependencies in the Local1 repository and displays the results.</span></span>

<span data-ttu-id="5b93a-125">La deuxième commande installe `Script-WithDependencies2` .</span><span class="sxs-lookup"><span data-stu-id="5b93a-125">The second command installs `Script-WithDependencies2`.</span></span>

<span data-ttu-id="5b93a-126">La troisième commande utilise l' `Get-InstalledScript` applet de commande script pour obtenir les scripts installés et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b93a-126">The third command uses the `Get-InstalledScript` script cmdlet to get installed scripts and display the results.</span></span>

<span data-ttu-id="5b93a-127">La quatrième commande utilise l' `Get-InstalledModule` applet de commande pour obtenir les modules installés et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b93a-127">The fourth command uses the `Get-InstalledModule` cmdlet to get installed modules and display the results.</span></span>

<span data-ttu-id="5b93a-128">La cinquième commande utilise l' `Find-Script` applet de commande pour rechercher les scripts dont le nom commence par `Required-Script` et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b93a-128">The fifth command uses the `Find-Script` cmdlet to find scripts where the name begins with `Required-Script` and display the results.</span></span>

<span data-ttu-id="5b93a-129">La sixième commande installe les scripts dont le nom commence par `Required-Script` dans le référentiel local1.</span><span class="sxs-lookup"><span data-stu-id="5b93a-129">The sixth command installs the scripts where the name begins with `Required-Script` in the Local1 repository.</span></span>

<span data-ttu-id="5b93a-130">La commande finale obtient les scripts installés et affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="5b93a-130">The final command gets installed scripts and displays the results.</span></span>

## <span data-ttu-id="5b93a-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5b93a-131">PARAMETERS</span></span>

### <span data-ttu-id="5b93a-132">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5b93a-132">-AcceptLicense</span></span>

<span data-ttu-id="5b93a-133">Accepter automatiquement le contrat de licence au cours de l’installation si le module l’exige.</span><span class="sxs-lookup"><span data-stu-id="5b93a-133">Automatically accept the license agreement during installation if the module requires it.</span></span>

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

### <span data-ttu-id="5b93a-134">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="5b93a-134">-AllowPrerelease</span></span>

<span data-ttu-id="5b93a-135">Vous permet d’installer un script marqué comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="5b93a-135">Allows you to install a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="5b93a-136">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5b93a-136">-Confirm</span></span>

<span data-ttu-id="5b93a-137">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5b93a-137">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5b93a-138">-Credential</span><span class="sxs-lookup"><span data-stu-id="5b93a-138">-Credential</span></span>

<span data-ttu-id="5b93a-139">Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour installer un script pour un fournisseur de package ou une source spécifiés.</span><span class="sxs-lookup"><span data-stu-id="5b93a-139">Specifies a user account that has rights to install a script for a specified package provider or source.</span></span>

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

### <span data-ttu-id="5b93a-140">-Force</span><span class="sxs-lookup"><span data-stu-id="5b93a-140">-Force</span></span>

<span data-ttu-id="5b93a-141">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5b93a-141">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="5b93a-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5b93a-142">-InputObject</span></span>

<span data-ttu-id="5b93a-143">Utilisé pour l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="5b93a-143">Used for pipeline input.</span></span>

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

### <span data-ttu-id="5b93a-144">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5b93a-144">-MaximumVersion</span></span>

<span data-ttu-id="5b93a-145">Spécifie la version maximale d’un seul script à installer.</span><span class="sxs-lookup"><span data-stu-id="5b93a-145">Specifies the maximum version of a single scripts to install.</span></span> <span data-ttu-id="5b93a-146">Vous ne pouvez pas ajouter ce paramètre si vous tentez d’installer plusieurs scripts.</span><span class="sxs-lookup"><span data-stu-id="5b93a-146">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="5b93a-147">Les paramètres **MaximumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="5b93a-147">The **MaximumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="5b93a-148">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5b93a-148">-MinimumVersion</span></span>

<span data-ttu-id="5b93a-149">Spécifie la version minimale d’un script unique à installer.</span><span class="sxs-lookup"><span data-stu-id="5b93a-149">Specifies the minimum version of a single script to install.</span></span> <span data-ttu-id="5b93a-150">Vous ne pouvez pas ajouter ce paramètre si vous tentez d’installer plusieurs scripts.</span><span class="sxs-lookup"><span data-stu-id="5b93a-150">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="5b93a-151">Les paramètres **MinimumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="5b93a-151">The **MinimumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="5b93a-152">-Name</span><span class="sxs-lookup"><span data-stu-id="5b93a-152">-Name</span></span>

<span data-ttu-id="5b93a-153">Spécifie un tableau de noms de scripts à installer.</span><span class="sxs-lookup"><span data-stu-id="5b93a-153">Specifies an array of names of scripts to install.</span></span>

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

### <span data-ttu-id="5b93a-154">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="5b93a-154">-NoPathUpdate</span></span>

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

### <span data-ttu-id="5b93a-155">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5b93a-155">-PassThru</span></span>

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

### <span data-ttu-id="5b93a-156">-Proxy</span><span class="sxs-lookup"><span data-stu-id="5b93a-156">-Proxy</span></span>

<span data-ttu-id="5b93a-157">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="5b93a-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="5b93a-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="5b93a-158">-ProxyCredential</span></span>

<span data-ttu-id="5b93a-159">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.</span><span class="sxs-lookup"><span data-stu-id="5b93a-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="5b93a-160">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="5b93a-160">-Repository</span></span>

<span data-ttu-id="5b93a-161">Spécifie le nom convivial d’un référentiel inscrit avec l’applet de commande `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="5b93a-161">Specifies the friendly name of a repository that has been registered with the `Register-PSRepository` cmdlet.</span></span> <span data-ttu-id="5b93a-162">La valeur par défaut est tous les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="5b93a-162">The default is all registered repositories.</span></span>

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

### <span data-ttu-id="5b93a-163">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5b93a-163">-RequiredVersion</span></span>

<span data-ttu-id="5b93a-164">Spécifie le numéro de version exact du script à installer.</span><span class="sxs-lookup"><span data-stu-id="5b93a-164">Specifies the exact version number of the script to install.</span></span>

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

### <span data-ttu-id="5b93a-165">-Étendue</span><span class="sxs-lookup"><span data-stu-id="5b93a-165">-Scope</span></span>

<span data-ttu-id="5b93a-166">Spécifie l’étendue d’installation du script.</span><span class="sxs-lookup"><span data-stu-id="5b93a-166">Specifies the installation scope of the script.</span></span>
<span data-ttu-id="5b93a-167">Les valeurs valides sont : AllUsers et CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="5b93a-167">Valid values are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="5b93a-168">L’étendue AllUsers permet d’installer les modules dans un emplacement accessible à tous les utilisateurs de l’ordinateur, c’est-à-dire `$env:ProgramFiles\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="5b93a-168">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, `$env:ProgramFiles\WindowsPowerShell\Scripts`.</span></span>

<span data-ttu-id="5b93a-169">L’étendue CurrentUser permet d’installer les modules uniquement dans `$home\Documents\WindowsPowerShell\Scripts` , afin que le module ne soit disponible que pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="5b93a-169">The CurrentUser scope lets modules be installed only to `$home\Documents\WindowsPowerShell\Scripts`, so that the module is available only to the current user.</span></span>

<span data-ttu-id="5b93a-170">Quand aucune **étendue** n’est définie, la valeur par défaut est définie en fonction de la session active :</span><span class="sxs-lookup"><span data-stu-id="5b93a-170">When no **Scope** is defined, the default will be set based on the current session:</span></span>

- <span data-ttu-id="5b93a-171">Pour une session PowerShell avec élévation de privilèges, l' **étendue** est définie par défaut sur ALLUSERS ;</span><span class="sxs-lookup"><span data-stu-id="5b93a-171">For an elevated PowerShell session, **Scope** defaults to AllUsers;</span></span>
- <span data-ttu-id="5b93a-172">Pour les sessions PowerShell non élevées dans [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) et ultérieures, la **portée** est CurrentUser ;</span><span class="sxs-lookup"><span data-stu-id="5b93a-172">For non-elevated PowerShell sessions in [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) and above, **Scope** is CurrentUser;</span></span>
- <span data-ttu-id="5b93a-173">Pour les sessions PowerShell non élevées dans PowerShellGet versions 1.6.7 et antérieures, la **portée** n’est pas définie et `Install-Module` échoue.</span><span class="sxs-lookup"><span data-stu-id="5b93a-173">For non-elevated PowerShell sessions in PowerShellGet versions 1.6.7 and earlier, **Scope** is undefined, and `Install-Module` fails.</span></span>

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

### <span data-ttu-id="5b93a-174">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5b93a-174">-WhatIf</span></span>

<span data-ttu-id="5b93a-175">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5b93a-175">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5b93a-176">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="5b93a-176">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5b93a-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b93a-177">CommonParameters</span></span>

<span data-ttu-id="5b93a-178">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5b93a-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b93a-179">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5b93a-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5b93a-180">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5b93a-180">INPUTS</span></span>

### <span data-ttu-id="5b93a-181">System.String[]</span><span class="sxs-lookup"><span data-stu-id="5b93a-181">System.String[]</span></span>

### <span data-ttu-id="5b93a-182">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="5b93a-182">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="5b93a-183">System.String</span><span class="sxs-lookup"><span data-stu-id="5b93a-183">System.String</span></span>

### <span data-ttu-id="5b93a-184">System.Uri</span><span class="sxs-lookup"><span data-stu-id="5b93a-184">System.Uri</span></span>

### <span data-ttu-id="5b93a-185">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="5b93a-185">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="5b93a-186">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5b93a-186">OUTPUTS</span></span>

### <span data-ttu-id="5b93a-187">System.Object</span><span class="sxs-lookup"><span data-stu-id="5b93a-187">System.Object</span></span>

## <span data-ttu-id="5b93a-188">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5b93a-188">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b93a-189">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="5b93a-189">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="5b93a-190">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="5b93a-190">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="5b93a-191">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="5b93a-191">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="5b93a-192">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5b93a-192">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="5b93a-193">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5b93a-193">RELATED LINKS</span></span>

[<span data-ttu-id="5b93a-194">Find-Script</span><span class="sxs-lookup"><span data-stu-id="5b93a-194">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="5b93a-195">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="5b93a-195">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="5b93a-196">Save-Script</span><span class="sxs-lookup"><span data-stu-id="5b93a-196">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="5b93a-197">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="5b93a-197">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="5b93a-198">Update-Script</span><span class="sxs-lookup"><span data-stu-id="5b93a-198">Update-Script</span></span>](Update-Script.md)
