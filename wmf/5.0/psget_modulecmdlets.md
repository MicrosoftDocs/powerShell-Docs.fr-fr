---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 02aebbd2557298b1b88229fdf5f67bdd08cea452
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190602"
---
# <a name="powershellget-cmdlets-for-module-management"></a>Applets de commande PowerShellGet pour la gestion des modules

- [Find-DscResource](https://technet.microsoft.com/library/mt654006.aspx)
- [Find-Module](https://technet.microsoft.com/library/dn807167.aspx)
- [Find-Script](https://technet.microsoft.com/library/mt654001.aspx)
- [Get-InstalledModule](https://technet.microsoft.com/en-us/library/mt653990.aspx)
- [Get-InstalledScript](https://technet.microsoft.com/en-us/library/mt653994.aspx)
- [Get-PSRepository](https://technet.microsoft.com/en-us/library/dn807170.aspx)
- [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx)
- [Install-Script](https://technet.microsoft.com/en-us/library/mt653998.aspx)
- [New-ScriptFileInfo](https://technet.microsoft.com/en-us/library/mt653995.aspx)
- [Publish-Module](https://technet.microsoft.com/en-us/library/dn807163.aspx)
- [Publish-Script](https://technet.microsoft.com/en-us/library/mt654003.aspx)
- [Register-PSRepository](https://technet.microsoft.com/en-us/library/dn807168.aspx)
- [Save-Module](https://technet.microsoft.com/en-us/library/mt653992.aspx)
- [Save-Script](https://technet.microsoft.com/en-us/library/mt654004.aspx)
- [Set-PSRepository](https://technet.microsoft.com/en-us/library/dn807165.aspx)
- [Test-ScriptFileInfo](https://technet.microsoft.com/en-us/library/mt654005.aspx)
- [Uninstall-Module](https://technet.microsoft.com/en-us/library/mt653996.aspx)
- [Uninstall-Script](https://technet.microsoft.com/en-us/library/mt653989.aspx)
- [Update-Module](https://technet.microsoft.com/en-us/library/dn807166.aspx)
- [Update-ModuleManifest](https://technet.microsoft.com/en-us/library/mt654002.aspx)
- [Update-Script](https://technet.microsoft.com/en-us/library/mt653997.aspx)
- [Update-ScriptFileInfo](https://technet.microsoft.com/en-us/library/mt653991.aspx)
- [Unregister-PSRepository](https://technet.microsoft.com/en-us/library/dn807161.aspx)

## <a name="module-dependency-installation-support-get-installedmodule-and-uninstall-module-cmdlets"></a>Prise en charge de l’installation des dépendances de modules, applets de commande Get-InstalledModule et Uninstall-Module
- Ajout de la population de dépendances de modules dans l’applet de commande Publish-Module. Les listes RequiredModules et NestedModules de PSModuleInfo sont utilisées lors de la préparation de la liste des dépendances d’un module à publier.
- Ajout de la prise en charge de l’installation des dépendances dans les applets de commande Install-Module et Update-Module. Les dépendances de modules sont installées et mises à jour par défaut.
- Ajout d’un paramètre -IncludeDependencies à l’applet de commande Find-Module pour inclure les dépendances de modules dans les résultats.
- Ajout de la prise en charge de -MaximumVersion dans les applets de commande Find-Module, Install-Module et Update-Module.
- Ajout des nouvelles applets de commande Get-InstalledModule et Uninstall-Module.

## <a name="powershellget-cmdlets-demo-with-module-dependencies-support"></a>Démonstration d’applets de commande PowerShellGet avec prise en charge des dépendances de modules :

### <a name="ensure-that-module-dependencies-are-available-on-the-repository"></a>Vérifiez que les dépendances de modules sont disponibles dans le dépôt :
```powershell
Find-Module -Repository LocalRepo -Name RequiredModule1,RequiredModule2,RequiredModule3,NestedRequiredModule1,NestedRequiredModule2,NestedRequiredModule3 | Sort-Object -Property Name

Version    Name                     Repository    Description
-------    ----                     ----------    -----------
2.5        NestedRequiredModule1    LocalRepo     NestedRequiredModule1 module
2.5        NestedRequiredModule2    LocalRepo     NestedRequiredModule2 module
2.0        NestedRequiredModule3    LocalRepo     NestedRequiredModule3 module
2.5        RequiredModule1          LocalRepo     RequiredModule1 module
2.5        RequiredModule2          LocalRepo     RequiredModule2 module
2.0        RequiredModule3          LocalRepo     RequiredModule3 module
```

### <a name="create-a-module-with-dependencies-that-are-specified-in-the-requiredmodules-and-nestedmodules-properties-of-its-module-manifest"></a>Créez un module avec des dépendances spécifiées dans les propriétés RequiredModules et NestedModules de son manifeste de module.
```powershell
$RequiredModules = @('RequiredModule1',
                     @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.5'; },
                     @{ModuleName = 'RequiredModule3'; RequiredVersion = '2.0'; })

$NestedRequiredModules = @('TestDepWithNestedRequiredModules1.psm1', 'NestedRequiredModule1',
                            @{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '1.5'; },
                            @{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.0'; })

New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\TestDepWithNestedRequiredModules1\TestDepWithNestedRequiredModules1.psd1' `
-NestedModules $NestedRequiredModules -RequiredModules $RequiredModules -ModuleVersion "1.0" -Description "TestDepWithNestedRequiredModules1 module"
```

###  <a name="publish-two-versions-10-and-20-of-the-testdepwithnestedrequiredmodules1-module-with-dependencies-to-the-repository"></a>Publiez deux versions (**« 1.0 »** et **« 2.0 »**) du module TestDepWithNestedRequiredModules1 avec des dépendances dans le dépôt.
```powershell
Publish-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -NuGetApiKey "MyNuGet-ApiKey-For-LocalRepo"
```

###  <a name="find-the-testdepwithnestedrequiredmodules1-module-with-its-dependencies-by-specifying--includedependencies"></a>Recherchez le module TestDepWithNestedRequiredModules1 avec ses dépendances en spécifiant -IncludeDependencies.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo –IncludeDependencies -MaximumVersion "1.0"

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.5        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
```

### <a name="use-find-module-metadata-to-find-the-module-dependencies"></a>Utilisez les métadonnées de Find-Module pour rechercher les dépendances du module.
```powershell
$psgetModuleInfo = Find-Module -Repository MSPSGallery -Name ModuleWithDependencies2
$psgetModuleInfo.Dependencies.ModuleName

RequiredModule1
RequiredModule2
RequiredModule3
NestedRequiredModule1
NestedRequiredModule2
NestedRequiredModule3

$psgetModuleInfo.Dependencies

Name Value
---- -----
ModuleName RequiredModule1
CanonicalId PowerShellGet:RequiredModule1/#http://psget/psGallery/api/v2/

ModuleName RequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:RequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName RequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:RequiredModule3/2.5#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule1
CanonicalId PowerShellGet:NestedRequiredModule1/#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:NestedRequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:NestedRequiredModule3/2.5#http://psget/psGallery/api/v2/
```

###  <a name="install-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Installez le module TestDepWithNestedRequiredModules1 avec des dépendances.
```powershell
Install-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -RequiredVersion "1.0"
Get-InstalledModule

Version    Name                    Repository   Description
-------    ----                    ----------   -----------
1.0        NestedRequiredModule1   LocalRepo    NestedRequiredModule1 module
2.5        NestedRequiredModule2   LocalRepo    NestedRequiredModule2 module
2.0        NestedRequiredModule3   LocalRepo    NestedRequiredModule3 module
1.0        RequiredModule1         LocalRepo    RequiredModule1 module
2.5        RequiredModule2                    LocalRepo    RequiredModule2 module
2.0        RequiredModule3                    LocalRepo    RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1  LocalRepo    TestDepWithNestedRequiredModules1 module
```

###  <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Mettez à jour le module TestDepWithNestedRequiredModules1 avec des dépendances.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

###  <a name="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget"></a>Exécutez l’applet de commande Uninstall-Module pour désinstaller un module que vous avez installé à l’aide de PowerShellGet.
Si d’autres modules dépendent du module que vous souhaitez supprimer, PowerShellGet génère une erreur.
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

## <a name="save-module-cmdlet"></a>Applet de commande Save-Module
```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3
```

## <a name="update-modulemanifest-cmdlet"></a>Applet de commande Update-ModuleManifest
Cette nouvelle applet de commande aide à mettre à jour le fichier manifeste avec des valeurs de propriétés d’entrée. Elle accepte tous les mêmes paramètres que Test-ModuleManifest.

Nous constatons que de nombreux auteurs de modules souhaiteraient spécifier « \* » dans des valeurs exportées telles que FunctionsToExport, CmdletsToExport, et ainsi de suite. Lors de la publication de module dans PowerShell Gallery, les commandes et fonctions non spécifiées ne sont pas peuplées correctement dans la galerie. Nous suggérons donc aux auteurs de modules de mettre à jour leurs manifestes avec les valeurs appropriées.

Si vous avez des modules qui ont des propriétés exportées, Update-ModuleManifest remplit le fichier manifeste spécifié avec les informations des applets de commande, variables, fonctions exportées, et ainsi de suite :
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

Après Update-ModuleManifest :
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

Pour chaque module, il existe également des champs de métadonnées associés. Pour afficher correctement les métadonnées dans PowerShell Gallery, vous pouvez utiliser Update-ModuleManifest pour remplir ces champs sous PrivateData.
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```
La table de hachage PrivateData du modèle de fichier manifeste a les propriétés suivantes :
```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```
***Remarque :*** DscResourcesToExport est pris en charge uniquement dans la dernière version PowerShell version 5.0. Nous ne pourrons pas mettre à jour le champ si vous exécutez une version précédente de PowerShell.
