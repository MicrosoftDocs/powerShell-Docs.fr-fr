---
ms.date: 01/10/2020
keywords: powershell,applet de commande
title: Écriture de modules portables
ms.openlocfilehash: 124e6efadfd07b8c5214a5c0446b1589f7142388
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "76022247"
---
# <a name="portable-modules"></a>Modules portables

Windows PowerShell est écrit pour [.NET Framework][] alors que PowerShell Core est écrit pour [.NET Core][]. Les modules portables sont des modules qui fonctionnent à la fois dans Windows PowerShell et PowerShell Core. Même si .NET Framework et .NET Core sont hautement compatibles, il existe des différences dans les API disponibles pour ces deux environnements. Il existe également des différences dans les API disponibles dans Windows PowerShell et PowerShell Core. Les modules destinés à être utilisés dans les deux environnements doivent prendre en compte ces différences.

## <a name="porting-an-existing-module"></a>Portage d’un module existant

### <a name="porting-a-pssnapin"></a>Portage d’un module PSSnapIn

Les composants logiciels enfichables PowerShell ([SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins)) ne sont pas pris en charge dans PowerShell Core. Mais vous pouvez facilement convertir un module PSSnapIn en module PowerShell. En règle générale, le code d’inscription PSSnapIn figure dans un fichier source unique d’une classe qui dérive de [PSSnapIn][].
Supprimez ce fichier source de la build car il n’est plus nécessaire.

Utilisez [New-ModuleManifest][] pour créer un manifeste de module qui évite la saisie du code d’inscription PSSnapIn. Certaines valeurs de **PSSnapIn** (par exemple, **Description**) peuvent être réutilisées dans le manifeste de module.

La propriété **RootModule** du manifeste de module doit être définie sur le nom de l’assembly (dll) qui implémente les applets de commande.

### <a name="the-net-portability-analyzer-aka-apiport"></a>Analyseur de portabilité .NET (également appelé APIPort)

Pour porter des modules écrits pour Windows PowerShell et les utiliser avec PowerShell Core, commencez par l’[Analyseur de portabilité .NET][]. Exécutez cet outil avec votre assembly compilé pour déterminer si les API .NET utilisées dans le module sont compatibles avec .NET Framework, .NET Core et autres runtimes .NET. Le cas échéant, l’outil suggère des API de remplacement. Sinon, vous devrez peut-être ajouter des [vérifications à l’exécution][] et limiter les fonctionnalités non disponibles dans des runtimes spécifiques.

## <a name="creating-a-new-module"></a>Création d’un module

Si vous créez un module, la recommandation consiste à utiliser l’[CLI .NET][].

### <a name="installing-the-powershell-standard-module-template"></a>Installation du modèle de module PowerShell standard

Une fois l’interface CLI .NET installée, installez une bibliothèque de modèles pour générer un module PowerShell simple.
Le module sera compatible avec Windows PowerShell, PowerShell Core, Windows, Linux et macOS.

L’exemple suivant présente l’installation du modèle :

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>Création d’un projet de module

Une fois le modèle installé, vous pouvez l’utiliser pour créer un projet de module PowerShell. Dans cet exemple, l’exemple de module s’appelle 'myModule'.

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>Génération du module

Utilisez les commandes CLI .NET standard pour générer le projet.

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>Test du module

Après avoir généré le module, vous pouvez importer et exécuter l’exemple d’applet de commande.

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

Les sections suivantes décrivent en détail certaines des technologies utilisées par ce modèle.

## <a name="net-standard-library"></a>Bibliothèque .NET Standard

[.NET Standard][] est une spécification formelle des API .NET disponibles dans toutes les implémentations .NET. Un code managé ciblant .NET Standard fonctionne avec les versions de .NET Framework et .NET Core compatibles avec cette version de .NET Standard.

> [!NOTE]
> Même si une API peut exister dans .NET Standard, l’implémentation de l’API dans .NET Core peut lever une `PlatformNotSupportedException` lors de l’exécution, et par conséquent, pour vérifier la compatibilité avec Windows PowerShell et PowerShell Core, il est recommandé d’exécuter des tests pour votre module dans les deux environnements.
> Exécutez également des tests sur Linux et macOS si votre module est destiné à une utilisation multiplateforme.

Le ciblage .NET Standard permet de s’assurer que, à mesure que le module évolue, les API incompatibles ne sont pas introduites accidentellement dans ce module. Les incompatibilités sont détectées lors de la compilation au lieu de l’exécution.

Toutefois, il n’est pas nécessaire de cibler .NET Standard pour qu’un module fonctionne avec Windows PowerShell et PowerShell Core, tant que vous utilisez une API compatible. Le langage intermédiaire (Intermediate Language, IL) est compatible entre les deux runtimes. Vous pouvez cibler .NET Framework 4.6.1, qui est compatible avec .NET Standard 2.0. Si vous n’utilisez pas les API en dehors de .NET Standard 2.0, votre module fonctionne avec PowerShell Core 6 sans recompilation.

## <a name="powershell-standard-library"></a>Bibliothèque PowerShell Standard

La bibliothèque [PowerShell Standard][] est une spécification formelle des API PowerShell disponibles dans toutes les versions de PowerShell supérieures ou égales à la version de cette norme.

Par exemple, [PowerShell Standard 5.1][] est compatible avec Windows PowerShell 5.1 et PowerShell Core 6.0 ou version ultérieure.

Nous vous recommandons de compiler votre module à l’aide de la bibliothèque PowerShell Standard. Cette bibliothèque garantit la disponibilité et l’implémentation des API dans Windows PowerShell et PowerShell Core 6.
PowerShell Standard garantit toujours une compatibilité ascendante. Un module généré à l’aide de PowerShell Standard Library 5.1 sera toujours compatible avec les futures versions de PowerShell.

## <a name="module-manifest"></a>Manifeste de module

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Indication de la compatibilité avec Windows PowerShell et PowerShell Core

Après avoir vérifié que votre module fonctionne avec Windows PowerShell et PowerShell Core, le manifeste de module doit indiquer explicitement la compatibilité à l’aide de la propriété [CompatiblePSEditions][]. La valeur `Desktop` signifie que le module est compatible avec Windows PowerShell, tandis que la valeur `Core` signifie que le module est compatible avec PowerShell Core. L’utilisation des valeurs `Desktop` et `Core` signifie que le module est compatible avec Windows PowerShell et PowerShell Core.

> [!NOTE]
> `Core` ne signifie pas automatiquement que le module est compatible avec Windows, Linux et macOS.
> La propriété **CompatiblePSEditions** a été introduite dans PowerShell v5. Les manifestes de modules qui utilisent la propriété **CompatiblePSEditions** ne peuvent pas être chargés dans les versions antérieures à PowerShell v5.

### <a name="indicating-os-compatibility"></a>Indication de la compatibilité du système d’exploitation

Tout d’abord, vérifiez que votre module fonctionne sur Linux et macOS. Indiquez ensuite la compatibilité avec ces systèmes d’exploitation dans le manifeste de module. Les utilisateurs pourront ainsi trouver plus facilement votre module pour leur système d’exploitation lors de la publication dans [PowerShell Gallery][].

Dans le manifeste de module, la propriété `PrivateData` comporte une sous-propriété `PSData`. La propriété facultative `Tags` de `PSData` utilise un tableau de valeurs qui s’affichent dans PowerShell Gallery. PowerShell Gallery prend en charge les valeurs de compatibilité suivantes :

| Tag               | Description                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatible avec PowerShell Core 6          |
| PSEdition_Desktop | Compatible avec Windows PowerShell         |
| Windows           | Compatible avec Windows                    |
| Linux             | Compatible avec Linux (aucune distribution spécifique) |
| macOS             | Compatible avec macOS                      |

Exemple :

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

## <a name="dependency-on-native-libraries"></a>dépendance envers les bibliothèques natives

Les modules destinés à être utilisés sur des systèmes d’exploitation ou des architectures de processeur différents peuvent dépendre d’une bibliothèque gérée qui dépend elle-même de certaines bibliothèques natives.

Avant PowerShell 7, vous deviez avoir un code personnalisé pour charger le fichier DLL natif appropriée afin que la bibliothèque gérée puisse le trouver.

Avec PowerShell 7, les fichiers binaires natifs à charger sont recherchés dans des sous-dossiers de l’emplacement de la bibliothèque gérée, à la suite d’un sous-ensemble de la notation [catalogue RID .NET][].

```
managed.dll folder
                |
                |--- 'win-x64' folder
                |       |--- native.dll
                |
                |--- 'win-x86' folder
                |       |--- native.dll
                |
                |--- 'win-arm' folder
                |       |--- native.dll
                |
                |--- 'win-arm64' folder
                |       |--- native.dll
                |
                |--- 'linux-x64' folder
                |       |--- native.so
                |
                |--- 'linux-x86' folder
                |       |--- native.so
                |
                |--- 'linux-arm' folder
                |       |--- native.so
                |
                |--- 'linux-arm64' folder
                |       |--- native.so
                |
                |--- 'osx-x64' folder
                |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[vérifications à l’exécution]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[CLI .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[Analyseur de portabilité .NET]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[Catalogue RID .NET]: https://docs.microsoft.com/dotnet/core/rid-catalog
