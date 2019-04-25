---
ms.date: 09/26/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Préversions de module
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084859"
---
# <a name="prerelease-module-versions"></a>Préversions de module

À compter de la version 1.6.0, PowerShellGet et PowerShell Gallery prennent en charge l’identification des versions supérieures à 1.0.0 comme des préversions. Avant cette fonctionnalité, les packages en préversion devaient avoir un numéro de version commençant par 0. L’objectif de ces fonctionnalités est de fournir une meilleure prise en charge de la convention de gestion des versions [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) sans perdre la compatibilité descendante avec les versions 3 et supérieures de PowerShell, ou les versions existantes de PowerShellGet. Cette rubrique étudie les fonctionnalités propres aux modules. Les fonctionnalités équivalentes des scripts sont décrites dans la rubrique [Préversions de script](script-prerelease-support.md). À l’aide de ces fonctionnalités, les éditeurs peuvent identifier un module ou un script avec une version 2.5.0-alpha et publier plus tard une version 2.5.0 prête pour la production qui remplace la préversion.

Voici globalement en quoi consistent les fonctionnalités de module en préversion :

- L’ajout d’une chaîne de préversion à la section PSData du manifeste du module identifie le module comme une préversion. Lors de la publication du module sur PowerShell Gallery, ces données sont extraites du manifeste et utilisées pour identifier les packages en préversion.
- Il est nécessaire d’ajouter l’indicateur `-AllowPrerelease` aux commandes PowerShellGet `Find-Module`, `Install-Module`, `Update-Module` et `Save-Module` pour pouvoir acquérir des packages en préversion. Sans cet indicateur, les packages en préversion ne s’affichent pas.
- Les versions de module affichées par `Find-Module` et `Get-InstalledModule`, ainsi que celles qui se trouvent dans PowerShell Gallery, sont affichées sous forme de chaîne unique suivie de la chaîne de préversion, par exemple 2.5.0-alpha.

Les détails des fonctionnalités sont présentés ci-dessous.

Ces changements n’affectent pas la prise en charge des versions de module intégrée à PowerShell, et sont compatibles avec PowerShell 3.0, 4.0 et 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identification d’une version de module comme préversion

La prise en charge des préversions par PowerShellGet nécessite l’utilisation de deux champs dans le manifeste du module :

- La valeur ModuleVersion incluse dans le manifeste de module doit être une version en 3 parties si une préversion est utilisée, et doit être compatible avec la gestion de versions PowerShell existante. Le format de version est A.B.C, où A, B et C sont des entiers.
- La chaîne de préversion est spécifiée dans le manifeste de module, dans la section PSData de PrivateData.

Les exigences détaillées de la chaîne de préversion sont décrites ci-dessous.

Voici à quoi ressemble un exemple de section d’un manifeste de module qui définit un module comme préversion :

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

Les exigences détaillées de la chaîne de préversion sont les suivantes :

- Une chaîne de préversion peut être spécifiée uniquement quand la valeur ModuleVersion comprend 3 segments : Majeure.Mineure.Build. Ce format est compatible avec SemVer v1.0.0.
- Un trait d’union sépare le numéro de build et la chaîne de préversion. Un trait d’union peut être inclus dans la chaîne de préversion uniquement en première position.
- La chaîne de préversion peut contenir uniquement des caractères alphanumériques ASCII [0-9A-Za-z-]. Il est recommandé de commencer la chaîne de préversion par un caractère alphabétique, pour qu’elle soit plus facile à identifier comme préversion au moment d’analyser une liste de packages.
- Seules les chaînes de préversion SemVer v1.0.0 sont prises en charge pour l’instant. La chaîne de préversion **ne doit pas** contenir de point ou le signe + [.+], lesquels sont autorisé dans SemVer 2.0.
- Exemples de chaînes de préversion prises en charge : -alpha, -alpha1, -BETA, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impact de la gestion de versions des préversions sur l’ordre de tri et les dossiers d’installation

L’ordre de tri change quand vous utilisez une préversion, ce qui est important quand vous publiez dans PowerShell Gallery et quand vous installez des modules à l’aide des commandes PowerShellGet. Si la chaîne de préversion est spécifiée pour deux modules, l’ordre de tri est basé sur la partie de chaîne qui suit le trait d’union. Par conséquent, 2.5.0-alpha est inférieur à 2.5.0-bêta, qui est inférieur à 2.5.0-gamma. Si deux modules ont la même valeur ModuleVersion et qu’un seul a une chaîne de préversion, le module sans chaîne de préversion est assimilé à la version prête pour la production et classé comme une version supérieure à la préversion (qui inclut la chaîne de préversion). Par exemple, entre les versions 2.5.0 et 2.5.0-bêta, la version 2.5.0 est considérée comme supérieure.

Quand vous publiez dans PowerShell Gallery, par défaut, la version du module qui est publié doit avoir une version supérieure à n’importe quelle version déjà publiée qui se trouve dans PowerShell Gallery.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Rechercher et acquérir des packages en préversion avec les commandes PowerShellGet

Pour pouvoir gérer des packages en préversion avec les commandes PowerShellGet Find-Module, Install-Module, Update-Module et Save-Module, il est nécessaire d’ajouter l’indicateur -AllowPrerelease. Si l’indicateur -AllowPrerelease est spécifié, les packages en préversion présents sont inclus. S’il n’est pas spécifié, les packages en préversion ne s’affichent pas.

Les seules exceptions dans les commandes de module PowerShellGet sont Get-InstalledModule et certains cas avec Uninstall-Module.

- Get-InstalledModule affiche toujours automatiquement les informations de préversion dans la chaîne de version des modules.
- Uninstall-Module désinstalle par défaut la version la plus récente d’un module, si __aucune version__ n’est spécifiée. Ce comportement n’a pas changé. Toutefois, si une préversion est spécifiée à l’aide de -RequiredVersion, -AllowPrerelease est nécessaire.

## <a name="examples"></a>Exemples

Supposons que PowerShell Gallery dispose du module TestPackage dans les versions 1.8.0 et 1.9.0-alpha. Si `-AllowPrerelease` n’est pas spécifié, seule la version 1.8.0 est retournée.

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

Pour installer une préversion, spécifiez toujours -AllowPrerelease. La spécification d’une chaîne de version de préversion n’est pas suffisante.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

Échec de la commande précédente, car -AllowPrerelease n’a pas été spécifié. L’ajout de `-AllowPrerelease` permet à l’opération de réussir.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

L’installation côte à côte de versions d’un module qui diffèrent uniquement par la préversion spécifiée n’est pas prise en charge. Quand vous installez un module à l’aide de PowerShellGet, différentes versions du même module sont installées côte à côte en créant un nom de dossier qui utilise la valeur ModuleVersion. La valeur ModuleVersion, sans la chaîne de préversion, est utilisée comme nom du dossier. Si un utilisateur installe MyModule version 2.5.0-alpha, il est installé dans le dossier `MyModule\2.5.0`. Si l’utilisateur installe ensuite la version 2.5.0-bêta, celle-ci **remplace** le contenu du dossier `MyModule\2.5.0`. L’avantage de cette approche est qu’il est inutile de désinstaller la préversion après l’installation de la version prête pour la production. L’exemple ci-dessous correspond à ce que vous devez obtenir :

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

Uninstall-Module supprime la dernière version d’un module quand -RequiredVersion n’est pas fourni.
Si -RequiredVersion est spécifié et qu’il s’agit d’une préversion, -AllowPrerelease doit être ajouté à la commande.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>Plus d’informations

- [Préversions de script](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [Uninstall-Module](/powershell/module/powershellget/uninstall-module)
