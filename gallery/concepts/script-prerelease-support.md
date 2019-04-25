---
ms.date: 10/17/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Préversions des scripts
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084638"
---
# <a name="prerelease-versions-of-scripts"></a>Préversions des scripts

À compter de la version 1.6.0, PowerShellGet et PowerShell Gallery prennent en charge l’identification des versions supérieures à 1.0.0 comme des préversions. Avant cette fonctionnalité, les packages en préversion devaient avoir un numéro de version commençant par 0. L’objectif de ces fonctionnalités est de fournir une meilleure prise en charge de la convention de gestion des versions [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) sans perdre la compatibilité descendante avec les versions 3 et supérieures de PowerShell, ou les versions existantes de PowerShellGet. Cette rubrique étudie les fonctionnalités propres aux scripts. Les fonctionnalités équivalentes des modules sont décrites dans la rubrique [Préversions de module](module-prerelease-support.md). À l’aide de ces fonctionnalités, les éditeurs peuvent identifier un script avec une version 2.5.0-alpha et publier plus tard une version 2.5.0 prête pour la production qui remplace la préversion.

Voici des exemples de fonctionnalités de script en préversion, à un niveau supérieur :

- Ajout d’un suffixe PrereleaseString à la chaîne de version dans le manifeste de script. Quand le script est publié dans PowerShell Gallery, ces données sont extraites du manifeste et utilisées pour identifier les packages en préversion.
- L’acquisition de packages en préversion nécessite d’ajouter l’indicateur -AllowPrerelease aux commandes PowerShellGet Find-Script, Install-Script, Update-Script et Save-Script. Sans cet indicateur, les packages en préversion ne s’affichent pas.
- Les versions de script affichées par Find-Script, Get-InstalledScript et celles qui se trouvent dans PowerShell Gallery sont affichées avec le suffixe PrereleaseString, par exemple 2.5.0-alpha.

Les détails des fonctionnalités sont présentés ci-dessous.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identification d’une version de script comme préversion

La prise en charge des préversions par PowerShellGet est plus facile pour les scripts que pour les modules. La gestion des versions de script est prise en charge uniquement par PowerShellGet, il n’y a donc aucun problème de compatibilité quand vous ajoutez la chaîne de préversion. Pour identifier un script dans PowerShell Gallery comme préversion, ajoutez un suffixe de préversion à une chaîne de version correctement mise en forme dans les métadonnées de script.

Voici à quoi ressemble un exemple de section d’un manifeste de script avec une préversion :

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Pour utiliser un suffixe de préversion, la chaîne de version doit remplir les conditions suivantes :

- Un suffixe de préversion peut être spécifié uniquement quand le numéro de version comprend 3 segments : Majeure.Mineure.Build.
  Ce format est compatible avec SemVer v1.0.0
- Le suffixe de préversion est une chaîne qui commence par un trait d’union et peut contenir des caractères alphanumériques ASCII [0-9A-Za-z-]
- Seules les chaînes de préversion SemVer v1.0.0 sont prises en charge pour l’instant. Par conséquent, le suffixe de préversion **ne doit pas** contenir de point ou de signe + [.+], lesquels sont autorisés dans SemVer 2.0
- Exemples de chaînes PrereleaseString prises en charge : -alpha, -alpha1, -BETA, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impact de la gestion de versions des préversions sur l’ordre de tri et les dossiers d’installation

L’ordre de tri change quand vous utilisez une préversion, ce qui est important quand vous publiez dans PowerShell Gallery et quand vous installez des scripts à l’aide des commandes PowerShellGet. Si deux versions de script existent avec le numéro de version, l’ordre de tri est basé sur la partie de la chaîne qui suit le trait d’union. Par conséquent, 2.5.0-alpha est inférieur à 2.5.0-bêta, qui est inférieur à 2.5.0-gamma. Si deux scripts ont le même numéro de version et qu’un seul a un suffixe PrereleaseString, le script **sans** suffixe de préversion est assimilé à la version prête pour la production et trié comme une version supérieure à la préversion. Par exemple, entre les versions 2.5.0 et 2.5.0-bêta, la version 2.5.0 est considérée comme supérieure.

Quand vous publiez dans PowerShell Gallery, par défaut, la version du script qui est publié doit être supérieure à n’importe quelle version déjà publiée qui se trouve dans PowerShell Gallery. Un éditeur peut mettre à jour la version 2.5.0-alpha vers 2.5.0-bêta ou 2.5.0 (sans suffixe de préversion).

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Rechercher et acquérir des packages en préversion avec les commandes PowerShellGet

Le traitement de packages en préversion à l’aide des commandes PowerShellGet Find-Script, Install-Script, Update-Script et Save-Script nécessite l’ajout de l’indicateur -AllowPrerelease. Si -AllowPrerelease est spécifié, les packages en préversion présents sont inclus. S’il n’est pas spécifié, les packages en préversion ne s’affichent pas.

Les seules exceptions dans les commandes de script PowerShellGet sont Get-InstalledScript et certains cas avec Uninstall-Script.

- Get-InstalledScript affiche toujours automatiquement les informations de préversion dans la chaîne de version, si elles sont présentes.
- Uninstall-Script désinstalle par défaut la version la plus récente d’un script, si **aucune version** n’est spécifiée. Ce comportement n’a pas changé. Toutefois, si une préversion est spécifiée à l’aide de `-RequiredVersion`, `-AllowPrerelease` est obligatoire.

## <a name="examples"></a>Exemples

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha

PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

Uninstall-Script supprime la version actuelle d’un script quand -RequiredVersion n’est pas fourni.
Si -RequiredVersion est spécifié et qu’il s’agit d’une préversion, -AllowPrerelease doit être ajouté à la commande.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a>Plus d’informations

- [Préversions de module](module-prerelease-support.md)
- [Find-Script](/powershell/module/powershellget/find-script)
- [Install-Script](/powershell/module/powershellget/install-script)
- [Save-Script](/powershell/module/powershellget/save-script)
- [Update-Script](/powershell/module/powershellget/update-script)
- [Get-InstalledScript](/powershell/module/powershellget/get-installedscript)
- [Uninstall-Script](/powershell/module/powershellget/uninstall-script)
