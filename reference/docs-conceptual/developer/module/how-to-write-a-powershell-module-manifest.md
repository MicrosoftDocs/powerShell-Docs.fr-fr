---
title: Comment écrire un manifeste de module PowerShell | Microsoft Docs
ms.date: 10/16/2019
ms.openlocfilehash: 734adab5ce26df6e26353de8e0bc9084e0fd3f3b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784909"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Comment écrire un manifeste de module PowerShell

Après avoir écrit votre module PowerShell, vous pouvez ajouter un manifeste de module facultatif qui contient des informations sur le module. Par exemple, vous pouvez décrire l’auteur, spécifier des fichiers dans le module (tels que les modules imbriqués), exécuter des scripts pour personnaliser l’environnement de l’utilisateur, charger des fichiers de type et de mise en forme, définir la configuration système requise et limiter les membres exportés par le module.

## <a name="creating-a-module-manifest"></a>Création d’un manifeste de module

Un **manifeste de module** est un fichier de données PowerShell ( `.psd1` ) qui décrit le contenu d’un module et détermine le mode de traitement d’un module. Le fichier manifeste est un fichier texte qui contient une table de hachage de clés et de valeurs. Vous liez un fichier manifeste à un module en nommant le manifeste de la même façon que le module, et en stockant le manifeste dans le répertoire racine du module.

Pour les modules simples qui contiennent uniquement un `.psm1` assembly unique ou binaire, un manifeste de module est facultatif. Toutefois, il est recommandé d’utiliser un manifeste de module chaque fois que cela est possible, car ils sont utiles pour vous aider à organiser votre code et à gérer les informations de contrôle de version. Et un manifeste de module est nécessaire pour exporter un assembly qui est installé dans le [global assembly cache](/dotnet/framework/app-domains/gac). Un manifeste de module est également requis pour les modules qui prennent en charge la fonctionnalité d’aide actualisable. L’aide actualisable utilise la clé **HelpInfoUri** dans le manifeste de module pour rechercher le fichier d’informations d’aide (HelpInfo XML) qui contient l’emplacement des fichiers d’aide mis à jour pour le module. Pour plus d’informations sur l’aide actualisable, consultez [prise en charge de l’aide actualisable](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Pour créer et utiliser un manifeste de module

1. La meilleure pratique pour créer un manifeste de module consiste à utiliser l’applet [de commande New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) . Vous pouvez utiliser des paramètres pour spécifier une ou plusieurs des valeurs et des clés par défaut du manifeste. La seule exigence consiste à nommer le fichier. `New-ModuleManifest`crée un manifeste de module avec les valeurs spécifiées, et comprend les clés restantes et leurs valeurs par défaut. Si vous avez besoin de créer plusieurs modules, utilisez `New-ModuleManifest` pour créer un modèle de manifeste de module qui peut être modifié pour vos différents modules. Pour obtenir un exemple de manifeste de module par défaut, consultez l' [exemple de manifeste de module](#sample-module-manifest).

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   Une alternative consiste à créer manuellement la table de hachage du manifeste de module à l’aide des informations minimales requises, **ModuleVersion**. Vous enregistrez le fichier avec le même nom que votre module et vous utilisez l' `.psd1` extension de fichier. Vous pouvez ensuite modifier le fichier et ajouter les clés et les valeurs appropriées.

1. Ajoutez tous les éléments supplémentaires souhaités dans le fichier manifeste.

   Pour modifier le fichier manifeste, utilisez un éditeur de texte de votre choix. Toutefois, le fichier manifeste est un fichier de script contenant du code. vous pouvez donc le modifier dans un environnement de script ou de développement, par exemple Visual Studio Code. Tous les éléments d’un fichier manifeste sont facultatifs, à l’exception du numéro **ModuleVersion** .

   Pour obtenir une description des clés et des valeurs que vous pouvez inclure dans un manifeste de module, consultez le tableau des [éléments de manifeste de module](#module-manifest-elements) . Pour plus d’informations, consultez les descriptions des paramètres de l’applet de commande [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) .

1. Pour résoudre les scénarios qui peuvent ne pas être couverts par les éléments de manifeste du module de base, vous avez la possibilité d’ajouter du code supplémentaire à votre manifeste de module.

   Pour des raisons de sécurité, PowerShell exécute uniquement un petit sous-ensemble des opérations disponibles dans un fichier manifeste de module. En règle générale, vous pouvez utiliser l' `if` instruction, les opérateurs arithmétiques et de comparaison, ainsi que les types de données PowerShell de base.

1. Une fois que vous avez créé votre manifeste de module, vous pouvez le tester pour confirmer que tous les chemins d’accès décrits dans le manifeste sont corrects. Pour tester votre manifeste de module, utilisez [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

1. Assurez-vous que le manifeste de votre module se trouve dans le niveau supérieur du répertoire qui contient votre module.

   Quand vous copiez votre module sur un système et que vous l’importez, PowerShell utilise le manifeste de module pour importer votre module.

1. Si vous le souhaitez, vous pouvez tester directement le manifeste de votre module à l’aide d’un appel à [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) par le biais d’une source d’alimentation du manifeste.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Éléments de manifeste de module

Le tableau suivant décrit les éléments que vous pouvez inclure dans un manifeste de module.

|Élément|Default|Description|
|-------------|-------------|-----------------|
|**RootModule**<br /> Entrez : `String`|`<empty string>`|Module de script ou fichier de module binaire associé à ce manifeste. Les versions précédentes de PowerShell appelaient cet élément **ModuleToProcess**.<br /> Les types possibles pour le module racine peuvent être vides, ce qui crée un module de **manifeste** , le nom d’un module de script ( `.psm1` ) ou le nom d’un module binaire ( `.exe` ou `.dll` ). Le fait de placer le nom d’un manifeste de module ( `.psd1` ) ou d’un fichier de script ( `.ps1` ) dans cet élément génère une erreur. <br /> Exemple : `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> Entrez : `Version`|`'0.0.1'`|Numéro de version de ce module. Si une valeur n’est pas spécifiée, `New-ModuleManifest` utilise la valeur par défaut. La chaîne doit pouvoir être convertie vers le type `Version` , par exemple `#.#.#.#.#` . `Import-Module`charge le premier module qu’il trouve sur le **$PSModulePath** qui correspond au nom et a au moins une **ModuleVersion**, comme le paramètre **MinimumVersion** . Pour importer une version spécifique, utilisez le `Import-Module` paramètre **RequiredVersion** de l’applet de commande.<br /> Exemple : `ModuleVersion = '1.0'`|
|**GUID**<br /> Entrez : `GUID`|`'<GUID>'`|ID utilisé pour identifier de manière unique ce module. Si une valeur n’est pas spécifiée, `New-ModuleManifest` la valeur est générée automatiquement. Actuellement, vous ne pouvez pas importer un module par **GUID**. <br /> Exemple : `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**Author**<br /> Entrez : `String`|`'<Current user>'`|Auteur de ce module. Si une valeur n’est pas spécifiée, `New-ModuleManifest` utilise l’utilisateur actuel. <br /> Exemple : `Author = 'AuthorNameHere'`|
|**Prennent**<br /> Entrez : `String`|`'Unknown'`|Société ou fournisseur de ce module. Si une valeur n’est pas spécifiée, `New-ModuleManifest` utilise la valeur par défaut.<br /> Exemple : `CompanyName = 'Fabrikam'`|
|**Intellectuelle**<br /> Entrez : `String`|`'(c) <Author>. All rights reserved.'`| Déclaration de droits d’auteur pour ce module. Si une valeur n’est pas spécifiée, `New-ModuleManifest` utilise la valeur par défaut avec l’utilisateur actuel en tant que `<Author>` . Pour spécifier un auteur, utilisez le paramètre **auteur** . <br /> Exemple : `Copyright = '2019 AuthorName. All rights reserved.'`|
|**Description**<br /> Entrez : `String`|`<empty string>`|Description de la fonctionnalité fournie par ce module.<br /> Exemple : `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> Entrez : `Version`|`<empty string>`|Version minimale du moteur PowerShell requise par ce module. Les valeurs valides sont 1,0, 2,0, 3,0, 4,0, 5,0, 5,1, 6 et 7.<br /> Exemple : `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> Entrez : `String`|`<empty string>`|Nom de l’hôte PowerShell requis par ce module. Ce nom est fourni par PowerShell. Pour rechercher le nom d’un programme hôte, dans le programme, tapez : `$host.name` .<br /> Exemple : `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> Entrez : `Version`|`<empty string>`|Version minimale de l’hôte PowerShell requis par ce module.<br /> Exemple : `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> Entrez : `Version`|`<empty string>`|Version minimale de Microsoft .NET Framework requise par ce module. Ce composant requis est valide uniquement pour l’édition PowerShell Desktop, par exemple PowerShell 5,1.<br /> Exemple : `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> Entrez : `Version`|`<empty string>`|Version minimale du common language runtime (CLR) requise par ce module. Ce composant requis est valide uniquement pour l’édition PowerShell Desktop, par exemple PowerShell 5,1.<br /> Exemple : `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> Entrez : `ProcessorArchitecture`|`<empty string>`|Architecture du processeur (aucune, x86, amd64) requise par ce module. Les valeurs valides sont x86, AMD64, ARM, IA64, MSIL et None (inconnu ou non spécifié).<br /> Exemple : `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> Entrez : `Object[]`|`@()`|Modules qui doivent être importés dans l’environnement global avant l’importation de ce module. Cela charge tous les modules figurant dans la liste, sauf s’ils ont déjà été chargés. Par exemple, certains modules peuvent déjà être chargés par un module différent. Il est possible de spécifier une version spécifique à charger à l’aide de `RequiredVersion` plutôt que `ModuleVersion` . Lorsque `ModuleVersion` est utilisé, il chargera la version la plus récente disponible avec un minimum de la version spécifiée. Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.<br /> Exemple : `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> Exemple : `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> Entrez : `String[]`|`@()`|Assemblys qui doivent être chargés avant l’importation de ce module. Spécifie les noms de fichiers d’assembly ( `.dll` ) dont le module a besoin.<br /> PowerShell charge les assemblys spécifiés avant de mettre à jour des types ou des formats, d’importer des modules imbriqués ou d’importer le fichier de module spécifié dans la valeur de la clé RootModule. Utilisez ce paramètre pour répertorier tous les assemblys requis par le module.<br /> Exemple : `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**ScriptsToProcess**<br /> Entrez : `String[]`|`@()`|Fichiers de script ( `.ps1` ) qui sont exécutés dans l’état de session de l’appelant lors de l’importation du module. Il peut s’agir de l’état de session global ou, pour les modules imbriqués, de l’état de session d’un autre module. Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de journalisation.<br /> Ces scripts sont exécutés avant le chargement de l’un des modules répertoriés dans le manifeste. <br /> Exemple : `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> Entrez : `String[]`|`@()`|Fichiers de type ( `.ps1xml` ) à charger lors de l’importation de ce module. <br /> Exemple : `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> Entrez : `String[]`|`@()`|Fichiers de format ( `.ps1xml` ) à charger lors de l’importation de ce module. <br /> Exemple : `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> Entrez : `Object[]`|`@()`|Modules à importer en tant que modules imbriqués du module spécifié dans **RootModule** (alias :**ModuleToProcess**).<br /> L’ajout d’un nom de module à cet élément est similaire à `Import-Module` l’appel de dans votre script ou code assembleur. La principale différence à l’aide d’un fichier manifeste est qu’il est plus facile de voir ce que vous chargez. En cas d’échec du chargement d’un module, vous n’avez pas encore chargé votre module réel.<br /> Outre d’autres modules, vous pouvez également charger des fichiers de script ( `.ps1` ) ici. Ces fichiers s’exécutent dans le contexte du module racine. Cela équivaut à la source de points du script dans le module racine. <br /> Exemple : `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> Entrez : `String[]`|`@()`|Spécifie les fonctions à exporter à partir de ce module. pour des performances optimales, n’utilisez pas de caractères génériques et ne supprimez pas l’entrée, utilisez un tableau vide s’il n’y a aucune fonction à exporter. Par défaut, aucune fonction n’est exportée. Vous pouvez utiliser cette clé pour répertorier les fonctions exportées par le module.<br /> Le module exporte les fonctions vers l’état de session de l’appelant. L’état de session de l’appelant peut être l’état de session global ou, pour les modules imbriqués, l’état de session d’un autre module. Lors du chaînage de modules imbriqués, toutes les fonctions qui sont exportées par un module imbriqué seront exportées vers l’état de session global, sauf si un module de la chaîne restreint la fonction à l’aide de la clé **FunctionsToExport** .<br /> Si le manifeste exporte des alias pour les fonctions, cette clé peut supprimer les fonctions dont les alias sont répertoriés dans la clé **AliasesToExport** , mais cette clé ne peut pas ajouter d’alias de fonction à la liste. <br /> Exemple : `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> Entrez : `String[]`|`@()`|Spécifie les applets de commande à exporter à partir de ce module. pour des performances optimales, n’utilisez pas de caractères génériques et ne supprimez pas l’entrée, utilisez un tableau vide s’il n’y a pas d’applet de commande à exporter. Par défaut, aucune applet de commande n’est exportée. Vous pouvez utiliser cette clé pour répertorier les applets de commande exportées par le module.<br /> L’état de session de l’appelant peut être l’état de session global ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous enchaînez des modules imbriqués, toutes les applets de commande exportées par un module imbriqué sont exportées vers l’état de session global, sauf si un module de la chaîne restreint l’applet de commande à l’aide de la clé **CmdletsToExport** .<br /> Si le manifeste exporte des alias pour les applets de commande, cette clé peut supprimer les applets de commande dont les alias sont répertoriés dans la clé **AliasesToExport** , mais cette clé ne peut pas ajouter d’alias d’applet de commande à la liste. <br /> Exemple : `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> Entrez : `String[]`|`'*'`|Spécifie les variables exportées par le module vers l’état de session de l’appelant. Les caractères génériques sont autorisés. Par défaut, toutes les variables ( `'*'` ) sont exportées. Vous pouvez utiliser cette clé pour limiter les variables exportées par le module.<br /> L’état de session de l’appelant peut être l’état de session global ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous enchaînez des modules imbriqués, toutes les variables exportées par un module imbriqué sont exportées vers l’état de session global, sauf si un module de la chaîne restreint la variable à l’aide de la clé **VariablesToExport** .<br /> Si le manifeste exporte également des alias pour les variables, cette clé peut supprimer les variables dont les alias sont répertoriés dans la clé **AliasesToExport** , mais cette clé ne peut pas ajouter d’alias de variable à la liste. <br /> Exemple : `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> Entrez : `String[]`|`@()`|Spécifie les alias à exporter à partir de ce module. pour des performances optimales, n’utilisez pas de caractères génériques et ne supprimez pas l’entrée, utilisez un tableau vide s’il n’y a aucun alias à exporter. Par défaut, aucun alias n’est exporté. Vous pouvez utiliser cette clé pour répertorier les alias qui sont exportés par le module.<br /> Le module exporte les alias vers l’état de session de l’appelant. L’état de session de l’appelant peut être l’état de session global ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous enchaînez des modules imbriqués, tous les alias qui sont exportés par un module imbriqué seront finalement exportés dans l’état de session global, sauf si un module de la chaîne restreint l’alias à l’aide de la clé **AliasesToExport** . <br /> Exemple : `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> Entrez : `String[]`|`@()`|Spécifie les ressources DSC à exporter à partir de ce module. Les caractères génériques sont autorisés. <br /> Exemple : `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**ModuleList**<br /> Entrez : `Object[]`|`@()`|Spécifie tous les modules qui sont empaquetés avec ce module. Ces modules peuvent être entrés par nom, à l’aide d’une chaîne séparée par des virgules, ou en tant que table de hachage avec des clés **modulename** et **GUID** . La table de hachage peut également avoir une clé **ModuleVersion** facultative. La clé **ModuleList** est conçue pour agir en tant qu’inventaire de module. Ces modules ne sont pas traités automatiquement. <br /> Exemple : `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FileList**<br /> Entrez : `String[]`|`@()`|Liste de tous les fichiers empaquetés avec ce module. Comme avec **ModuleList**, **filelist** est une liste d’inventaire et n’est pas traité autrement. <br /> Exemple : `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> Entrez : `Object`|`@{...}`|Spécifie les données privées qui doivent être passées au module racine spécifié par la clé **RootModule** (alias : **ModuleToProcess**). **PrivateData** est une table de hachage qui comprend plusieurs éléments **: Tags**, **LicenseUri**, **ProjectURI**, **iconUri**, **ReleaseNotes**, **version préliminaire**, **RequireLicenseAcceptance**et **ExternalModuleDependencies**. |
|**Balises** <br /> Entrez : `String[]` |`@()`| Balises aide sur la découverte de modules dans les galeries en ligne. <br /> Exemple : `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> Entrez : `Uri` |`<empty string>`| URL de la licence pour ce module. <br /> Exemple : `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> Entrez : `Uri` |`<empty string>`| URL du site Web principal pour ce projet. <br /> Exemple : `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> Entrez : `Uri` |`<empty string>`| URL vers une icône représentant ce module. <br /> Exemple : `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**ReleaseNotes**<br /> Entrez : `String` |`<empty string>`| Spécifie les notes de publication du module. <br /> Exemple : `ReleaseNotes = 'The release notes provide information about the module.`|
|**Version préliminaire**<br /> Entrez : `String` |`<empty string>`| Ce paramètre a été ajouté dans PowerShellGet 1.6.6. Chaîne de préversion qui identifie le module comme une **version préliminaire dans** les galeries en ligne. <br /> Exemple : `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> Entrez : `Boolean`|`$true`| Ce paramètre a été ajouté dans PowerShellGet 1,5. Indicateur qui spécifie si le module requiert une acceptation explicite de l’utilisateur pour l’installation, la mise à jour ou l’enregistrement. <br /> Exemple : `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> Entrez : `String[]` |`@()`| Ce paramètre a été ajouté dans PowerShellGet v2. Liste des modules externes dont ce module dépend. <br /> Exemple : `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> Entrez : `String`|`<empty string>`|URI HelpInfo de ce module. <br /> Exemple : `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> Entrez : `String`|`<empty string>`|Préfixe par défaut pour les commandes exportées à partir de ce module. Remplacez le préfixe par défaut à l’aide de `Import-Module -Prefix` . <br /> Exemple : `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>Exemple de manifeste de module

L’exemple de manifeste de module suivant a été créé avec `New-ModuleManifest` dans PowerShell 7 et contient les clés et les valeurs par défaut.

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

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

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        RequireLicenseAcceptance = $true

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

## <a name="see-also"></a>Voir aussi

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[Global Assembly Cache](/dotnet/framework/app-domains/gac)

[Module d’importation](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)
