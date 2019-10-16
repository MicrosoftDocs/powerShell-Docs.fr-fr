---
title: Comment écrire un manifeste de module PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367098"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Guide pratique pour écrire un manifeste de module PowerShell

Une fois que vous avez écrit votre module Windows PowerShell, vous pouvez éventuellement ajouter un manifeste de module. Un manifeste de module est un fichier de script PowerShell que vous pouvez utiliser pour inclure des informations sur le module. Par exemple, vous pouvez décrire l’auteur, spécifier des fichiers dans le module (tels que les modules imbriqués), exécuter des scripts pour personnaliser l’environnement de l’utilisateur, charger des fichiers de type et de mise en forme, définir la configuration système requise et limiter les membres exportés par le module.

## <a name="creating-a-module-manifest"></a>Création d’un manifeste de module

Un *manifeste de module* est un fichier de données Windows PowerShell (. psd1) qui décrit le contenu d’un module et détermine le mode de traitement d’un module. Le fichier manifeste est un fichier texte qui contient une table de hachage de clés et de valeurs. Vous liez un fichier manifeste à un module en lui attribuant le même nom que le module et en le plaçant à la racine du répertoire du module.

Pour les modules simples qui contiennent uniquement un assembly. psm1 ou binaire unique, un manifeste de module est facultatif. Toutefois, il est recommandé d’utiliser un manifeste de module chaque fois que cela est possible, car ils sont utiles pour vous aider à organiser votre code et à gérer les informations de contrôle de version. En outre, un manifeste de module est nécessaire pour exporter un assembly installé dans le Global Assembly Cache. Un manifeste de module est également requis pour les modules qui prennent en charge la fonctionnalité d’aide actualisable. Autrement dit, l’aide actualisable utilise la clé **HelpInfoUri** dans le manifeste de module pour rechercher le fichier d’informations d’aide (HelpInfo XML) qui contient l’emplacement des fichiers d’aide mis à jour pour le module. Pour plus d’informations sur l’aide actualisable, consultez [prise en charge de l’aide actualisable](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Pour créer et utiliser un manifeste de module

1. Pour créer un manifeste de module, vous avez plusieurs options :

   1. Créez directement la table de hachage avec les informations minimales requises, puis enregistrez-la dans un fichier. psd1 portant le même nom que votre module. Une fois que vous avez effectué cette opération, vous pouvez ouvrir le fichier et ajouter manuellement les valeurs appropriées.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Sinon, appelez l’applet de commande [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) , avec une ou plusieurs des valeurs par défaut passées en tant que paramètres. (Notez toutefois que le seul nom du fichier est requis pour générer un manifeste.) Cette opération crée un manifeste de module avec toutes les valeurs de manifeste que vous avez spécifiées explicitement, et avec le reste contenant la valeur par défaut appropriée.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Enfin, vous pouvez également créer un fichier. psd1 vide et copier le modèle en bas de cette rubrique dans le fichier, puis renseigner les valeurs pertinentes. La seule exigence réelle dans ce cas est de s’assurer que le fichier a été nommé de la même façon que le module.

2. Ajoutez tout élément supplémentaire au manifeste que vous souhaitez avoir dans le fichier.

   En règle générale, cela est probablement effectué dans n’importe quel éditeur de texte, tel que le bloc-notes. Toutefois, il s’agit techniquement d’un fichier de script contenant du code. vous pouvez donc le modifier dans un environnement de script ou de développement réel, tel que Visual Studio Code. Là encore, Notez que tous les éléments d’un fichier manifeste sont facultatifs, à l’exception du numéro ModuleVersion.

   Pour obtenir une description des clés et des valeurs que vous pouvez avoir dans un manifeste de module, consultez les **éléments de manifeste de module** ci-dessous. Pour plus d’informations, consultez les descriptions des paramètres de l’applet de commande [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) .

3. Si vous le souhaitez, vous pouvez choisir d’ajouter du code supplémentaire à votre manifeste de module pour résoudre les scénarios qui ne seraient pas couverts par les éléments de manifeste du module de base.

   En raison des problèmes de sécurité, PowerShell n’exécutera qu’un petit sous-ensemble des opérations disponibles dans un fichier manifeste de module. En règle générale, vous pouvez utiliser l’instruction **If** , les opérateurs arithmétiques et de comparaison, ainsi que les types de données PowerShell de base.

4. Une fois que vous avez créé votre manifeste de module, vous pouvez le tester (pour confirmer que tous les chemins d’accès décrits dans le manifeste sont corrects) avec un appel à [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Assurez-vous que le manifeste de votre module se trouve dans le niveau supérieur du répertoire qui contient votre module.

   Quand vous copiez votre module sur un système et que vous l’importez, PowerShell utilise le manifeste de module pour importer votre module.

6. Si vous le souhaitez, vous pouvez tester directement le manifeste de votre module à l’aide d’un appel à [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) par le biais d’une source d’alimentation du manifeste.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Éléments de manifeste de module

Le tableau suivant décrit les éléments que vous pouvez avoir dans un manifeste de module

|Élément|Par défaut|Description|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Type : chaîne|' '|Module de script ou fichier de module binaire associé à ce manifeste. Les versions précédentes de PowerShell appelaient cet élément ModuleToProcess.<br /><br /> Les types possibles pour le module racine peuvent être vides (ce qui en fait un module de **manifeste** ), le nom d’un module de script (. psm1, qui en fait un module de **script** ), ou le nom d’un module binaire (. exe ou. dll, qui en fait un module **binaire** ). Le fait de placer le nom d’un manifeste de module (. psd1) ou d’un fichier de script (. ps1) dans cet élément provoquera une erreur.|
|ModuleVersion<br /><br /> Type : chaîne|1.0|Numéro de version de ce module. La chaîne doit pouvoir être convertie en [System. version]. Autrement dit, ' #. #. #. #. # '. `Import-Module` chargera le premier module qu’il trouve sur le **$psModulePath** qui correspond au nom, et a au moins une valeur ModuleVersion, en tant que paramètre `-MinimumVersion`. Pour importer une version spécifique, utilisez le paramètre @ no__t-0 à la place.<br /><br /> Exemple : `ModuleVersion = '1.0'`|
|GUID<br /><br /> Type : chaîne|GUID généré automatiquement|ID utilisé pour identifier de manière unique ce module. Notez que vous ne pouvez pas importer actuellement un module par GUID.<br /><br /> Exemple : `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Auteur<br /><br /> Type : chaîne|aucune.|Auteur de ce module.<br /><br /> Exemple : `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Type : chaîne|Unknown|Société ou fournisseur de ce module.<br /><br /> Exemple : `CompanyName = 'Fabrikam'`|
|Droits d’auteur<br /><br /> Type : chaîne|(c) [currentYear] [auteur]. Tous droits réservés.|Déclaration de droits d’auteur pour ce module.<br /><br /> Exemple : `Copyright = '2016 AuthorName. All rights reserved.'`|
|Description<br /><br /> Type : chaîne|' '|Description de la fonctionnalité fournie par ce module.<br /><br /> Exemple : `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Type : chaîne|' '|Version minimale du moteur Windows PowerShell requise par ce module. Les valeurs valides actuelles sont 1,0, 2,0, 3,0, 4,0 et 5,0.<br /><br /> Exemple : `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Type : chaîne|' '|Spécifie le nom de l’hôte Windows PowerShell requis par le module. Ce nom est fourni par Windows PowerShell. Pour rechercher le nom d’un programme hôte, dans le programme, tapez : `$host.name`.<br /><br /> Exemple : `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Type : chaîne|' '|Version minimale de l’hôte Windows PowerShell requis par ce module.<br /><br /> Exemple : `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Type : chaîne|' '|Version minimale de Microsoft .NET Framework requise par ce module.<br /><br /> Exemple : `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Type : chaîne|' '|Version minimale du common language runtime (CLR) requise par ce module.<br /><br /> Exemple : `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Type : chaîne|' '|Architecture du processeur (aucune, x86, amd64) requise par ce module. Les valeurs valides sont x86, AMD64, IA64 et None (valeur inconnue ou non spécifiée).<br /><br /> Exemple : `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type : [String []]|@()|Modules qui doivent être importés dans l’environnement global avant l’importation de ce module. Cela chargera tous les modules figurant dans la liste, sauf s’ils ont déjà été chargés. (Par exemple, certains modules peuvent déjà être chargés par un module différent). Il est également possible de spécifier une version spécifique à charger à l’aide de `RequiredVersion` plutôt que `ModuleVersion`. Lors de l’utilisation de `ModuleVersion`, le chargement de la version la plus récente est disponible avec un minimum de la version spécifiée.<br /><br /> Exemple : `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Exemple : `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Type : [String []]|@()|Assemblys qui doivent être chargés avant l’importation de ce module.<br /><br /> Notez que contrairement à RequiredModules, PowerShell chargera le RequiredAssemblies s’ils ne sont pas déjà chargés.|
|ScriptsToProcess<br /><br /> Type : [String []]|@()|Fichiers de script (. ps1) qui sont exécutés dans l’état de session de l’appelant lors de l’importation du module. Il peut s’agir de l’état de session global ou, pour les modules imbriqués, de l’état de session d’un autre module. Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de connexion.<br /><br /> Ces scripts sont exécutés avant le chargement de l’un des modules répertoriés dans le manifeste.|
|TypesToProcess<br /><br /> Type : [String []]|@()|Fichiers de type (. ps1xml) à charger lors de l’importation de ce module.|
|FormatsToProcess<br /><br /> Type : [String []]|@()|Fichiers de format (. ps1xml) à charger lors de l’importation de ce module.|
|NestedModules<br /><br /> Type : [String []]|@()|Modules à importer en tant que modules imbriqués du module spécifié dans RootModule/ModuleToProcess.<br /><br /> L’ajout d’un nom de module à cet élément est similaire à l’appel de `Import-Module` à partir de votre script ou de votre code d’assembly. La principale différence est qu’il est plus facile de voir ce que vous chargez ici dans le fichier manifeste. En outre, si le chargement d’un module échoue ici, vous n’avez pas encore chargé votre module réel.<br /><br /> En plus d’autres modules, vous pouvez également charger des fichiers de script (. ps1) ici. Ces fichiers s’exécutent dans le contexte du module racine. (Cela équivaut à la source de points du script dans votre module racine.)|
|FunctionsToExport<br /><br /> Type : [String []]|@()|Spécifie les fonctions exportées par le module (les caractères génériques sont autorisés mais déconseillés) à l’état de session de l’appelant. Par défaut, aucune fonction n’est exportée. Vous pouvez utiliser cette clé pour répertorier les fonctions exportées par le module.<br /><br /> L’état de session de l’appelant peut être l’état de session global ou, pour les modules imbriqués, l’état de session d’un autre module. Lors du chaînage de modules imbriqués, toutes les fonctions qui sont exportées par un module imbriqué seront exportées vers l’état de session global, sauf si un module de la chaîne restreint la fonction à l’aide de la clé FunctionsToExport.<br /><br /> Si le manifeste exporte également des alias pour les fonctions, cette clé peut supprimer les fonctions dont les alias sont répertoriés dans la clé AliasesToExport, mais cette clé ne peut pas ajouter d’alias de fonction à la liste.|
|CmdletsToExport<br /><br /> Type : [String []]|@()|Spécifie les applets de commande exportées par le module (les caractères génériques sont autorisés mais déconseillés). Par défaut, aucune applet de commande n’est exportée. Vous pouvez utiliser cette clé pour répertorier les applets de commande exportées par le module.<br /><br /> L’état de session de l’appelant peut être l’état de session global ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous enchaînez des modules imbriqués, toutes les applets de commande exportées par un module imbriqué seront finalement exportées dans l’état de session global, sauf si un module de la chaîne restreint l’applet de commande à l’aide de la clé CmdletsToExport.<br /><br /> Si le manifeste exporte également des alias pour les applets de commande, cette clé peut supprimer les applets de commande dont les alias sont répertoriés dans la clé AliasesToExport, mais cette clé ne peut pas ajouter d’alias d’applet de commande à la liste.|
|VariablesToExport<br /><br /> Type : chaîne|'*'|Spécifie les variables exportées par le module (les caractères génériques sont autorisés) à l’état de session de l’appelant. Par défaut, toutes les variables sont exportées. Vous pouvez utiliser cette clé pour limiter les variables exportées par le module.<br /><br /> L’état de session de l’appelant peut être l’état de session global ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous enchaînez des modules imbriqués, toutes les variables exportées par un module imbriqué sont exportées vers l’état de session global, sauf si un module de la chaîne restreint la variable à l’aide de la clé VariablesToExport.<br /><br /> Si le manifeste exporte également des alias pour les variables, cette clé peut supprimer les variables dont les alias sont répertoriés dans la clé AliasesToExport, mais cette clé ne peut pas ajouter d’alias de variable à la liste.|
|AliasesToExport<br /><br /> Type : [String []]|@()|Spécifie les alias exportés par le module (les caractères génériques sont autorisés mais déconseillés) à l’état de session de l’appelant. Par défaut, aucun alias n’est exporté. Vous pouvez utiliser cette clé pour répertorier les alias qui sont exportés par le module.<br /><br /> L’état de session de l’appelant peut être l’état de session global ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous enchaînez des modules imbriqués, tous les alias qui sont exportés par un module imbriqué seront finalement exportés dans l’état de session global, sauf si un module de la chaîne restreint l’alias à l’aide de la clé AliasesToExport.|
|ModuleList<br /><br /> Type : [String []]|@()|Spécifie tous les modules qui sont empaquetés avec ce module. Ces modules peuvent être entrés par nom (une chaîne séparée par des virgules) ou comme une table de hachage avec des clés ModuleName et GUID. La table de hachage peut également avoir une clé ModuleVersion facultative. La clé ModuleList est conçue pour agir en tant qu’inventaire de module. Ces modules ne sont pas traités automatiquement.|
|FileList<br /><br /> Type : [String []]|@()|Liste de tous les fichiers empaquetés avec ce module. Comme avec ModuleList, FileList est destiné à vous aider comme une liste d’inventaire et n’est pas traité autrement.|
|PrivateData<br /><br /> Type : [objet]|@{...}|Spécifie les données privées qui doivent être passées au module racine spécifié par la clé RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Type : chaîne|' '|URI HelpInfo de ce module.|
|DefaultCommandPrefix<br /><br /> Type : chaîne|' '|Préfixe par défaut pour les commandes exportées à partir de ce module. Remplacez le préfixe par défaut à l’aide de `Import-Module`-prefix.|

## <a name="sample-module-manifest"></a>Exemple de manifeste de module

L’exemple de manifeste de module suivant montre les clés et les valeurs par défaut dans un manifeste de module. Cet exemple a été créé à l’aide de l’applet de commande `New-ModuleManifest` dans Windows PowerShell 3,0. Lorsque vous créez plusieurs modules, vous pouvez utiliser cette applet de commande pour créer un modèle de manifeste qui peut ensuite être modifié pour différents modules.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
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

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Voir aussi

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)
