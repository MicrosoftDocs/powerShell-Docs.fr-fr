---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Install-Script
ms.openlocfilehash: 4c3fd9393ccb7ee5c3b010f1114b6596a74fdee2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="install-script"></a>Install-Script

Installe les fichiers de script PowerShell à partir de référentiels en ligne sur l’ordinateur local.


## <a name="description"></a>Description

L’applet de commande Install-Script acquiert une charge utile de script à partir d’un référentiel, vérifie que la charge utile est un script PowerShell valide et copie le fichier de script à un emplacement d’installation spécifié.

Les référentiels par défaut sur lesquels Install-Script opère sont configurables via les applets de commande Register-PSRepository, Set-PSRepository, Unregister-PSRepository et Get-PSRepository. Quand elle fonctionne sur plusieurs référentiels, Install-Script installe le premier script qui correspond aux critères de recherche spécifiés (Name, MinimumVersion ou MaximumVersion) à partir du premier référentiel sans aucune erreur.


L’applet de commande Install-Script télécharge un ou plusieurs modules à partir d’une galerie en ligne, les valide et les installe sur l’ordinateur local selon l’étendue d’installation spécifiée.

L’applet de commande Install-Script obtient un ou plusieurs modules qui répondent aux critères spécifiés à partir d’une galerie en ligne, vérifie que les résultats de la recherche sont des modules valides et copie les dossiers des modules à l’emplacement d’installation.

Quand aucune étendue n’est définie ou que la valeur du paramètre Scope est AllUsers, le module est installé dans %systemdrive%:\Program Files\WindowsPowerShell\Modules. Quand la valeur de Scope est CurrentUser, le module est installé dans $home\Documents\WindowsPowerShell\Modules.

Vous pouvez filtrer vos résultats selon les versions minimales et exactes des modules spécifiés.

- Aucune prise en charge des versions côte à côte pour les fichiers de script PowerShell
- Prise en charge de l’installation de dépendances de scripts
- **Untrusted prompt :** (Invite pour les référentiels non approuvés) L’acceptation par l’utilisateur est obligatoire pour installer les modules à partir d’un référentiel non approuvé.
- -Force réinstalle le module installé
- RequiredVersion installe la version spécifiée côte à côte avec les versions existantes sur PowerShell versions 5.0 ou ultérieures.

Les caractères génériques ne sont pas pris en charge dans -Name sur les applets de commande Install-Module, Save-Module, Uninstall-Module, Install-Script, Save-Script et Uninstall-Script.

### <a name="scope"></a>Étendue
Spécifie l’étendue d’installation du module. Les valeurs acceptables pour ce paramètre sont : AllUsers et CurrentUser.

L’étendue d’installation par défaut est AllUsers.

L’étendue AllUsers permet d’installer les modules à un emplacement qui est accessible à tous les utilisateurs de l’ordinateur, autrement dit $env:SystemDrive\Program Files\WindowsPowerShell\Modules.

L’étendue CurrentUser permet d’installer les modules uniquement dans $home\Documents\WindowsPowerShell\Modules, afin que le module ne soit disponible que pour l’utilisateur actuel.


Spécifie l’étendue d’installation du script. Les valeurs valides sont : AllUsers et CurrentUser. La valeur par défaut est CurrentUser.

L’étendue AllUsers indique d’installer un script dans %systemdrive%:\ProgramFiles\WindowsPowerShell\Scripts afin que le script soit disponible pour tous les utilisateurs. L’étendue CurrentUser indique d’installer le script dans $home\Documents\WindowsPowerShell\Scripts afin que le script ne soit disponible que pour l’utilisateur actuel.


## <a name="nopathupdate"></a>NoPathUpdate

- Le paramètre de commutateur NoPathUpdate sur l’applet de commande Install-Script contourne l’invite d’ajout de l’emplacement d’installation de script à la variable d’environnement PATH.
- Toute utilisation de la commande WITH –NoPathUpdate spécifiée entraîne l’absence d’invite et la mise à jour de PATH NOT (le paramètre force peut être ignoré ici).
- -Force sans –NoPathUpdate entraîne l’absence d’invite et la mise à jour de PATH.
- Si ni –Force ni –NoPathUpdate ne sont spécifiés, l’utilisateur voit l’invite.
- Tout cela s’applique uniquement lors de la première utilisation d’Install-Script dans une étendue donnée.


## <a name="notes"></a>Remarques

Cette applet de commande s’exécute sur Windows PowerShell 3.0 ou versions ultérieures de Windows PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.

Si un module installé ne peut pas être importé (autrement dit, s’il ne dispose pas d’un fichier .psm1, .psd1 ou .dll du même nom dans le dossier), l’installation échoue, sauf si vous ajoutez le paramètre Force à votre commande.

Si une version du module sur l’ordinateur correspond à la valeur spécifiée pour le paramètre Name et que vous n’avez pas ajouté le paramètre MinimumVersion ou RequiredVersion, Install-Script se poursuit de manière silencieuse sans installer ce module. Si les paramètres MinimumVersion ou RequiredVersion sont spécifiés et que le module existant ne correspond pas aux valeurs de ce paramètre, une erreur se produit. Pour être plus précis : si la version du module actuellement installé est inférieure à la valeur du paramètre MinimumVersion ou différente de la valeur du paramètre RequiredVersion, une erreur se produit. Si la version du module installé est supérieure à la valeur du paramètre MinimumVersion ou égale à la valeur du paramètre RequiredVersion, Install-Script se poursuit de manière silencieuse sans installer ce module.

Install-Script retourne une erreur s’il n’existe aucun module dans la galerie en ligne qui correspond au nom spécifié.

Pour installer plusieurs modules, spécifiez un tableau de noms de modules, séparés par des virgules. Vous ne pouvez pas ajouter MinimumVersion ou RequiredVersion si vous spécifiez plusieurs noms de modules.

Par défaut, les modules sont installés dans le dossier Program Files, afin d’éviter toute confusion quand vous installez les ressources DSC (Configuration de l’état souhaité) de Windows PowerShell. Vous pouvez diriger plusieurs objets PSGetItemInfo vers Install-Script ; il s’agit d’une autre façon de spécifier plusieurs modules à installer dans une seule commande.

Pour éviter d’exécuter des modules qui contiennent du code malveillant, les modules installés ne sont pas automatiquement importés par l’installation. Comme bonne pratique de sécurité, évaluez le code du module avant d’exécuter des applets de commande ou des fonctions dans un module pour la première fois.


## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande

```powershell
Get-Command -Name Install-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Install-Script](http://go.microsoft.com/fwlink/?LinkId=619784)

## <a name="example-commands"></a>Exemples de commandes

```powershell


# Piping Find-Script output to Install-Script cmdlet

Find-Script -Repository Local1 -Name Required-Script2

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script2                    local1               Description for the Required-Script2 script


Find-Script -Repository Local1 -Name Required-Script2 | Install-Script

Get-Command Required-Script2

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
ExternalScript  Required-Script2.ps1                                2.0       C:\Users\manikb\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1


Get-InstalledScript Required-Script2

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script2                    local1               Description for the Required-Script2 script


Get-InstalledScript Required-Script2 | fl * -Force


Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : manikb
CompanyName                :
Copyright                  : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://manikb-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\manikb\Documents\WindowsPowerShell\Scripts


# Installing a script to AllUsers scope

Install-Script -Repository Local1 -Name Required-Script3 -Scope AllUsers
Get-InstalledScript -Name Required-Script3

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Get-InstalledScript -Name Required-Script3  | fl * -Force


Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : manikb
CompanyName                :
Copyright                  : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://manikb-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


# Installing a script with dependent scripts and modules

Find-Script -Repository Local1 -Name Script-WithDependencies2 -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0        Script-WithDependencies2            local1               Description for the Script-WithDependencies2 script
2.5        RequiredModule1                     local1               RequiredModule1 module
2.5        RequiredModule2                     local1               RequiredModule2 module
2.5        RequiredModule3                     local1               RequiredModule3 module
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Install-Script -Repository Local1 -Name Script-WithDependencies2
Get-InstalledScript

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script
2.0        Script-WithDependencies2            local1               Description for the Script-WithDependencies2 script


Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        RequiredModule1                     local1               RequiredModule1 module
2.5        RequiredModule2                     local1               RequiredModule2 module
2.5        RequiredModule3                     local1               RequiredModule3 module


Find-Script -Repository Local1 -Name Required-Script*

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Install-Script -Repository Local1 -Name Required-Script*

Get-InstalledScript

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


# Find a script and install it

# The first command finds the script named Required-Script2 from the Local1 repository and displays the results.
# The second command finds the Required-Script2 script, and then uses the pipeline operator to pass it to the Install-Script cmdlet to install it.
# The third command uses the Get-Command cmdlet to get Required-Script2, and then displays the results.
# The fourth command uses the Get-InstalledScript cmdlet to get Required-Script2 and display the results.
# The fifth command gets RequiredScript2 and uses the pipeline operator to pass it to the Format-List cmdlet to format the output.

Find-Script -Repository "Local1" -Name "Required-Script2"

Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
Get-Command -Name "Required-Script2"

Get-InstalledScript -Name "Required-Script2"

Get-InstalledScript -Name "Required-Script2" | Format-List * 


# Install a script with AllUsers scope

# The first command installs the script named Required-Script3 and assigns it AllUsers scope.
# The second command gets the installed script Required-Script3 and displays information about it.
# The third command gets Required-Script3 and uses the pipeline operator to pass it to the Format-List cmdlet to format the output.

Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
Get-InstalledScript -Name "Required-Script3"
Get-InstalledScript -Name "Required-Script3" | Format-List * 


# Install a script with its dependent scripts and modules

# The first command finds the script named Script-WithDependencies2 and its dependencies in the Local1 repository and displays the results.
# The second command installs Script-WithDependencies2.
# The third command uses the Get-InstalledScript script cmdlet to get installed scripts and display the results.
# The fourth command uses the Get-InstalledModule cmdlet to get installed modules and display the results.
# The fifth command uses the Find-Script cmdlet to find scripts where the name begins with Required-Script and display the results.
# The sixth command installs the scripts where the name begins with Required-Script in the Local1 repository. 
# The final command gets installed scripts and displays the results.

Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
Get-InstalledScript
Get-InstalledModule
Find-Script -Repository "Local1" -Name "Required-Script*"
Install-Script -Repository "Local1" -Name "Required-Script*"
Get-InstalledScript

```

Vous pouvez également utiliser Get-Command –Name <InstalledScriptFileName> pour l’obtenir. Deux nouveaux emplacements d’installation sont ajoutés à la variable d’environnement PATH lors de la première utilisation d’une étendue spécifiée.
```powershell
$env:Path -split ';'| Where-Object {$\_} | Select-Object -Last 2
C:\\Program Files\\WindowsPowerShell\\Scripts
C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Get-Command Required-Script2
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script2.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Required-Script2.ps1
```

```powershell

# Install a module by name
Install-Script -Name MyDscModule

# Install multiple modules
Install-Script ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Script -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Script -Name ContosoServer -RequiredVersion 1.1.3

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Script -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Script ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Script ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Script ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Script ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Script ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Script ContosoClient -Force

# Install a module with dependencies
Install-Script -Name 


# Install a script from the registered repository with ScriptSourceLocation
Install-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Install-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Install-Script -Name *Azure*

# Find all versions of a script
Install-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Install-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Install-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Install-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Installing a script to default AllUsers scope and with RequiredVersion
Install-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script from the specified repository
Install-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Install-Script

# Find available scripts from few registered repositories
Install-Script -Repository PSGallery, PrivatePSGallery

```

```powershell
 Added the logic for checking and failing the install script operation when there is a command with same name is already available on the system.
Also updated the prompt message.

 Examples:
PS C:\WINDOWS\system32> install-script get-childitem -Repository localrepo
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:1
+ install-script get-childitem -Repository localrepo
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 
 
 PS C:\WINDOWS\system32> install-script get-childitem,contosos -Repository localrepo
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:1
+ install-script get-childitem,contosos -Repository localrepo
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 PackageManagement\Install-Package : No match was found for the specified search criteria and script name 'contosos'. Try Get-ScriptRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\powershellget\1.0.0.1\PSModule.psm1:2891 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : ObjectNotFound: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
     + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage

 PS C:\WINDOWS\system32>

 
 
 PS C:\WINDOWS\system32> find-script get-childitem -Repository localrepo | install-script
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:51
+ find-script get-childitem -Repository localrepo | install-script
+                                                   ~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 
 PS C:\WINDOWS\system32>

 PS C:\WINDOWS\system32> Install-Package -Name Get-ChildItem -source LocalRepo  -ProviderName powershellget -Type Script
WARNING: A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.

```

```powershell

Prompt ONCE per USER and per SCOPE for adding the script installation location to PATH environment variable.

- Prompt message for CurrentUser scope: (Complete message will be scrubbed later)

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):


- Prompt message for –AllUsers scope is same as above with $env:ProgramFiles\WindowsPowerShell\Scripts .

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Program Files\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Program Files\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Program Files\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):


- To prompt only once per scope, user acceptance for PATH variable change will be added to the user specific settings file under %localappdata%\Microsoft\windows\PowerShell\PowerShellGet
%localappdata%\Microsoft\windows\PowerShell\PowerShellGet\PowerShellGetSettings.XML. 
This settings file will be used to not prompt again.

After prompting for CurrentUser scope: 
    true or false for CurrentUserScope_AllowPATHChangeForScripts key based on user input.

After prompting for AllUsers scope: 
    true or false for AllUsersScope_AllowPATHChangeForScripts key based on user input.

- If user accepts the prompt
                Check and add $home\Documents\WindowsPowerShell\Scripts to user specific PATH environment variable.
                Check and add $env:ProgramFiles\WindowsPowerShell\Scripts to system specific PATH environment variable only when Install-Script cmdlet is used in an administrator process.
                Check and add above two paths to $env:PATH variable of the current process.

- If user denies the prompt, script installation will be proceeded without making any changes to the PATH environment variable.



Example:             
PS C:\windows\system32> Install-Script -Name $scriptName -Repository $repositoryName -Scope $Scope -Verbose

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Program Files\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Program Files\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Program Files\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n


```

## <a name="install-script-cmdlet-in-pipeline-operations"></a>Applet de commande Install-Script dans les opérations de pipeline

```powershell

# Find a module and install it
Find-Script -Name "MyDSC*" | Install-Script

# Find a module and install it to the CurrentUser scope
Find-Script -Name "MyDSC*" | Install-Script -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Script to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Script
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Script cmdlet by using the pipeline operator. The Install-Script cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Script cmdlet from the same module, Install-Script attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Script
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Script
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Prise en charge des versions côte à côte sur PowerShell 5.0 ou version ultérieure

PowerShellGet assure la prise en charge des versions de modules côte à côte dans les applets de commande Install-Script, Update-Script et Publish-Script qui s’exécutent dans Windows PowerShell 5.0 ou versions ultérieures.

### <a name="install-script-examples"></a>Exemples Install-Script

```powershell
# Install a version of the module
Install-Script -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Script -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Script -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Script -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a>Installer un module avec ses dépendances

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Script -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a>Scénarios d’erreur

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Script'
Install-Script ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Script'
Install-Script ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Script'
Install-Script ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Script'
Install-Script ContosoClient,ContosoServer -MinimumVersion 2.0

```

## <a name="installing-a-script-with-dependent-scripts-and-modules"></a>Installation d’un script avec des modules et scripts dépendants

```powershell
# Installing a script with dependent scripts and modules
Find-Script -Repository GalleryINT -Name Script-WithDependencies2 -IncludeDependencies
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script

Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
Get-InstalledModule
Install-Script -Repository GalleryINT -Name Script-WithDependencies2 -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
Get-InstalledModule
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module

# Contents of Script-WithDependencies2 file.
<#PSScriptInfo
.VERSION 2.0
.GUID 90082fa1-0b84-49fb-a00e-0a624fbb6584
.AUTHOR manikb
.COMPANYNAME Microsoft Corporation
.COPYRIGHT (c) 2015 Microsoft Corporation. All rights reserved.
.TAGS Tag1 Tag2 Tag-Script-WithDependencies2-2.0
.LICENSEURI http://script-withdependencies2.com/license
.PROJECTURI http://script-withdependencies2.com/
.ICONURI http://script-withdependencies2.com/icon
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS Required-Script1,Required-Script2,Required-Script3
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
Script-WithDependencies2 release notes
#>
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'}
#Requires -Module @{RequiredVersion = '2.5'; ModuleName = 'RequiredModule3'}
#Requires -Module @{ModuleVersion = '1.1'; ModuleName = 'RequiredModule4'; MaximumVersion = '2.0'}
#Requires -Module @{MaximumVersion = '1.5'; ModuleName = 'RequiredModule5'}
<#
.DESCRIPTION
Description for the Script-WithDependencies2 script
#>
Param()
Function Test-FunctionFromScript\_Script-WithDependencies2 { Get-Date }
Workflow Test-WorkflowFromScript\_Script-WithDependencies2 { Get-Date }
```

## <a name="install-script-and-get-installedscript-cmdlets"></a>Applets de commande Install-Script et Get-InstalledScript
L’applet de commande Install-Script permet d’installer un fichier de script spécifique et ses dépendances à l’étendue spécifiée. Par défaut, les scripts sont installés dans l’étendue AllUsers. L’applet de commande Get-InstalledScript permet d’obtenir la liste des fichiers de script qui ont été installés à l’aide de l’applet de commande Install-Script.

Note d’utilisation : Pour permettre la gestion et la localisation des scripts une fois qu’ils sont installés, Install-script crée un dossier par défaut pour le stockage des scripts dans $home\Documents\WindowsPowerShell\Scripts et ajoute ce dossier à votre environnement PATH. Si la modification du chemin constitue un problème, utilisez Save-Script au lieu d’Install-Script. Get-InstalledScripts et Uninstall-Script ne fonctionnent qu’avec les scripts placés sur le système à l’aide d’Install-Script.
```powershell
# Install locations for scripts:
# Default scope is AllUsers.
# AllUsers scope --> "$env:ProgramFiles\\WindowsPowerShell\\Scripts"
# CurrentUser scope -->; "$env:USERPROFILE\\Documents\\WindowsPowerShell\\Scripts"

# Piping Find-Script output to Install-Script cmdlet
Find-Script -Repository GalleryINT -Name Required-Script2 | Install-Script -Scope CurrentUser -Verbose
VERBOSE: Repository details, Name = 'GalleryINT', Location = 'https://customgallery.cloudapp.net/api/v2/'; IsTrusted = 'True'; IsRegistered = 'True'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.5' of script 'Required-Script2'".
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'GalleryINT'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://customgallery.cloudapp.net/api/v2/items/psscript/' and PackageManagementProvider is 'NuGet'.
VERBOSE: Searching repository 'https://customgallery.cloudapp.net/api/v2/items/psscript/FindPackagesById()?id='Required-Script2'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'Required-Script2'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.5' of script 'Required-Script2'".
VERBOSE: The installation scope is specified to be 'CurrentUser'.
VERBOSE: The specified script will be installed in 'C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts' and its dependent modules will be installed in
'C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading script 'Required-Script2' with version '2.5' from the repository 'https://customgallery.cloudapp.net/api/v2/items/psscript/'.
VERBOSE: Script 'Required-Script2' was installed successfully.

Get-InstalledScript Required-Scri\*
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script

Get-InstalledScript Required-Script2 | Format-List \* -Force
Name : Required-Script2
Version : 2.5
Type : Script
Description : Description for the Required-Script2 script
Author : manikb
CompanyName :
Copyright : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate : 10/30/2015 1:25:15 AM
LicenseUri : http://required-script2.com/license
ProjectUri : http://required-script2.com/
IconUri : http://required-script2.com/icon
Tags : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript}
Includes : {Function, DscResource, Cmdlet, Workflow...}
PowerShellGetFormatVersion :
ReleaseNotes : Required-Script2 release notes
Dependencies : {}
RepositorySourceLocation : https://customgallery.cloudapp.net/api/v2/
Repository : GalleryINT
PackageManagementProvider : NuGet
AdditionalMetadata : {Type, releaseNotes, copyright, PackageManagementProvider...}
InstalledLocation : C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Installed script file is immediately available for usage.
```

Vous pouvez également utiliser Get-Command –Name <InstalledScriptFileName> pour l’obtenir. Deux nouveaux emplacements d’installation sont ajoutés à la variable d’environnement PATH lors de la première utilisation d’une étendue spécifiée.
```powershell
$env:Path -split ';'| Where-Object {$\_} | Select-Object -Last 2
C:\\Program Files\\WindowsPowerShell\\Scripts
C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Get-Command Required-Script2
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script2.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Required-Script2.ps1

Find-Script -Repository LocalRepo1 -Name Demo-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script LocalRepo1 Script file description goes here

Find-Script -Repository LocalRepo1 -Name Demo-Script | Install-Script -Scope CurrentUser
Untrusted repository
You are installing the scripts from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the scripts from 'C:\\MyLocalRepo'?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"): Y

Get-InstalledScript Demo-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script LocalRepo1 Script file description goes here

Get-Command Demo-Script
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Demo-Script.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Demo-Script.ps1

# Using the installed script
Demo-Script
Demo-ScriptFunction
Demo-ScriptWorkflow

# Installing a script to default AllUsers scope and with RequiredVersion
Install-Script -Repository GalleryINT -Name Required-Script3 -RequiredVersion 2.0
Get-InstalledScript -Name Required-Script3

Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
Get-InstalledScript -Name Required-Script3 | Format-List Name,InstalledLocation -Force
Name : Required-Script3
InstalledLocation : C:\\Program Files\\WindowsPowerShell\\Scripts

Get-Command Required-Script3
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script3.ps1 C:\\Program Files\\WindowsPowerShell\\Scripts\\Required-Script3.ps1

# Installing a script with dependent scripts and modules
Find-Script -Repository GalleryINT -Name Script-WithDependencies2 -IncludeDependencies
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script

Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
Get-InstalledModule
Install-Script -Repository GalleryINT -Name Script-WithDependencies2 -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
Get-InstalledModule
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module

# Contents of Script-WithDependencies2 file.
<#PSScriptInfo
.VERSION 2.0
.GUID 90082fa1-0b84-49fb-a00e-0a624fbb6584
.AUTHOR manikb
.COMPANYNAME Microsoft Corporation
.COPYRIGHT (c) 2015 Microsoft Corporation. All rights reserved.
.TAGS Tag1 Tag2 Tag-Script-WithDependencies2-2.0
.LICENSEURI http://script-withdependencies2.com/license
.PROJECTURI http://script-withdependencies2.com/
.ICONURI http://script-withdependencies2.com/icon
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS Required-Script1,Required-Script2,Required-Script3
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
Script-WithDependencies2 release notes
#>
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'}
#Requires -Module @{RequiredVersion = '2.5'; ModuleName = 'RequiredModule3'}
#Requires -Module @{ModuleVersion = '1.1'; ModuleName = 'RequiredModule4'; MaximumVersion = '2.0'}
#Requires -Module @{MaximumVersion = '1.5'; ModuleName = 'RequiredModule5'}
<#
.DESCRIPTION
Description for the Script-WithDependencies2 script
#>
Param()
Function Test-FunctionFromScript\_Script-WithDependencies2 { Get-Date }
Workflow Test-WorkflowFromScript\_Script-WithDependencies2 { Get-Date }
```

