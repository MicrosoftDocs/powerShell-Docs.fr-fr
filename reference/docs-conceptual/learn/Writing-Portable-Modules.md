---
ms.date: 12/14/2018
keywords: powershell,applet de commande
title: Écriture de modules portables
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747719"
---
# <a name="portable-modules"></a>Modules portables

Windows PowerShell est écrit pour [.NET Framework][] alors que PowerShell Core est écrit pour [.NET Core][]. Modules portables sont des modules qui fonctionnent dans Windows PowerShell et PowerShell Core. Bien que .NET Framework et .NET Core sont hautement compatibles, il existe des différences dans les API disponibles entre les deux. Il existe également des différences dans les API disponibles dans Windows PowerShell et PowerShell Core. Modules destinées à être utilisée dans les deux environnements doivent être conscient de ces différences.

## <a name="porting-an-existing-module"></a>Portage d’un Module existant

### <a name="porting-a-pssnapin"></a>Portage d’un PSSnapIn

PowerShell SnapIns (PSSnapIn) ne sont pas pris en charge dans PowerShell Core. Toutefois, il est facile de convertir un PSSnapIn à un module PowerShell. En règle générale, le code d’inscription PSSnapIn est dans un fichier source unique d’une classe qui dérive de [PSSnapIn][]. Supprimer ce fichier source à partir de la build ; Il n’est plus nécessaire.

Utilisez [New-ModuleManifest][] pour créer un nouveau manifeste de module qui remplace la nécessité pour le code d’inscription PSSnapIn. Certaines des valeurs à partir de la PSSnapIn (par exemple, Description) peuvent être réutilisés dans le manifeste de module.

Le `RootModule` propriété dans le manifeste de module doit être définie sur le nom de l’assembly (dll) qui implémente les applets de commande.

### <a name="the-net-portability-analyzer-aka-apiport"></a>L’Analyseur de portabilité .NET (également appelé APIPort)

Pour les modules de port écrits pour Windows PowerShell fonctionne avec PowerShell Core, commencez par le [Analyseur de portabilité .NET][]. Exécutez cet outil sur votre assembly compilé pour déterminer si les API .NET utilisé dans le module sont compatibles avec .NET Framework, .NET Core et autres runtimes .NET. L’outil suggère des API de remplacement s’ils existent. Sinon, vous devrez peut-être ajouter [vérifications à l’exécution][] et limiter les fonctionnalités non disponibles dans les runtimes spécifiques.

## <a name="creating-a-new-module"></a>Création d’un Module

Si vous créez un nouveau module, la recommandation consiste à utiliser le [INTERFACE CLI .NET][].

### <a name="installing-the-powershell-standard-module-template"></a>Installation du modèle de Module PowerShell Standard

Une fois l’interface CLI .NET est installée, installez une bibliothèque de modèles pour générer un module PowerShell simple.
Le module sera compatible avec Windows PowerShell, PowerShell Core, Windows, Linux et macOS.

L’exemple suivant montre comment installer le modèle :

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

### <a name="creating-a-new-module-project"></a>Création d’un nouveau projet de Module

Une fois que le modèle est installé, vous pouvez créer un nouveau projet de module PowerShell à l’aide de ce modèle. Dans cet exemple, le module d’exemple est appelé « myModule ».

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

### <a name="building-the-module"></a>Créer le Module

Utilisez les commandes CLI de .NET standard pour générer le projet.

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

### <a name="testing-the-module"></a>Le Module de test

Après avoir généré le module, vous pouvez importer et exécuter l’applet de commande d’exemple.

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

## <a name="net-standard-library"></a>Bibliothèque .NET standard

[.NET standard][] est une spécification formelle des API .NET qui sont disponibles dans toutes les implémentations de .NET. Ciblage de .NET Standard fonctionne avec les versions de .NET Framework et .NET Core qui sont compatibles avec cette version de .NET Standard de code managé.

> [!NOTE]
> Bien qu’une API peut-être exister dans .NET Standard, l’implémentation des API dans .NET Core peut lever une `PlatformNotSupportedException` lors de l’exécution, et par conséquent, pour vérifier la compatibilité avec Windows PowerShell et PowerShell Core, la meilleure pratique consiste à exécuter des tests pour votre module dans les deux environnements.
> Également exécuter des tests sur Linux et macOS si votre module est destiné à être inter-plateformes.

Ciblage de .NET Standard permet de s’assurer que, comme le module évolue, API incompatibles n’obtenir introduction accidentelle dans le module. Incompatibilités sont découvertes au moment de la compilation au lieu de l’exécution.

Toutefois, il n’est pas nécessaire pour cibler .NET Standard pour un module pour travailler avec Windows PowerShell et PowerShell Core, tant que vous utilisez une API compatible. Le langage intermédiaire (IL) est compatible entre les deux runtimes. Vous pouvez cibler .NET Framework 4.6.1, qui est compatible avec .NET Standard 2.0. Si vous n’utilisez pas les API en dehors de .NET Standard 2.0, votre module fonctionne avec PowerShell Core 6 sans recompilation.

## <a name="powershell-standard-library"></a>Bibliothèque Standard de PowerShell

Le [PowerShell Standard][] bibliothèque est une spécification formelle des APIs PowerShell disponibles dans toutes les versions de PowerShell supérieures ou égales à la version de cette norme.

Par exemple, [Standard PowerShell 5.1][] est compatible avec Windows PowerShell 5.1 et PowerShell Core 6.0 ou version ultérieure.

Nous vous recommandons de que vous compilez votre module à l’aide de la bibliothèque Standard de PowerShell. La bibliothèque garantit que les API sont disponibles et implémentée dans Windows PowerShell et PowerShell Core 6.
PowerShell Standard est destiné à toujours être compatible avec le transfert. Un module créé à l’aide de PowerShell 5.1 de bibliothèque Standard sera toujours compatible avec les futures versions de PowerShell.

## <a name="module-manifest"></a>Manifeste de module

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Indiquant la compatibilité avec Windows PowerShell et PowerShell Core

Après avoir vérifié que votre module fonctionne avec Windows PowerShell et PowerShell Core, le manifeste de module doit indiquer explicitement compatibilité à l’aide de la [CompatiblePSEditions][] propriété. La valeur `Desktop` signifie que le module est compatible avec Windows PowerShell, alors que la valeur `Core` signifie que le module est compatible avec PowerShell Core. Y compris les `Desktop` et `Core` signifie que le module est compatible avec Windows PowerShell et PowerShell Core.

> [!NOTE]
> `Core` ne pas automatiquement signifie que le module est compatible avec Windows, Linux et macOS.
> Le **CompatiblePSEditions** propriété a été introduite dans PowerShell v5. Manifestes de module qui utilisent le **CompatiblePSEditions** propriété ne parviennent pas à charger dans les versions antérieures PowerShell v5.

### <a name="indicating-os-compatibility"></a>Indiquant la compatibilité de système d’exploitation

Tout d’abord, vérifiez que votre module fonctionne sur Linux et macOS. Ensuite, indiquent la compatibilité avec ces systèmes d’exploitation dans le manifeste de module. Cela rend plus facile pour les utilisateurs à trouver votre module pour leur système d’exploitation lors de la publication à le [PowerShell Gallery][].

Dans le manifeste de module, le `PrivateData` propriété a un `PSData` sous-propriété. Le paramètre facultatif `Tags` propriété du `PSData` prend un tableau de valeurs qui s’affichent dans PowerShell Gallery. PowerShell Gallery prend en charge les valeurs de compatibilité suivantes :

| Légende               | Description                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatible avec PowerShell Core 6          |
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

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[vérifications à l’exécution]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[INTERFACE CLI .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[Standard PowerShell 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[Analyseur de portabilité .NET]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
