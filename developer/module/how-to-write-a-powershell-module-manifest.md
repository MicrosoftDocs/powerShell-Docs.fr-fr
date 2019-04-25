---
title: Comment écrire un manifeste de Module PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082292"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Guide pratique pour écrire un manifeste de module PowerShell

Après avoir écrit votre module Windows PowerShell, vous pouvez éventuellement ajouter un manifeste de module. Un manifeste de module est un fichier de script PowerShell que vous pouvez utiliser pour inclure des informations sur le module. Par exemple, vous pouvez décrire l’auteur, spécifiez les fichiers dans le module (par exemple, les modules imbriqués), exécuter des scripts pour personnaliser l’environnement utilisateur, chargement des fichiers de mise en forme et de type, définissent la configuration système requise et limitent les membres qui exporte le module.

## <a name="creating-a-module-manifest"></a>Création d’un manifeste de Module

Un *manifeste de module* est un fichier de données de Windows PowerShell (.psd1) qui décrit le contenu d’un module et détermine le mode de traitement d’un module. Le fichier manifest lui-même est un fichier texte qui contient une table de hachage des clés et valeurs. Vous liez un fichier manifeste à un module en nommant le même que le module et en le plaçant dans la racine du répertoire du module.

Pour les modules simples qui contiennent uniquement un seul .psm1 ou un assembly binaire, un manifeste de module est facultatif. Toutefois, il est recommandé d’utiliser un manifeste de module autant que possible, car elles sont utiles pour vous aider à organiser votre code et pour gérer les informations de contrôle de version. En outre, un manifeste de module est nécessaire pour exporter un assembly qui est installé dans le global assembly cache. Un manifeste de module est également requis pour les modules qui prennent en charge la fonctionnalité d’aide actualisable. Autrement dit, l’aide actualisable utilise le **HelpInfoUri** clés dans le manifeste de module pour rechercher le fichier d’informations (HelpInfo XML) aide qui contient l’emplacement des fichiers d’aide mis à jour pour le module. Pour plus d’informations sur l’aide actualisable, consultez [Supporting Updatable Help](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Pour créer et utiliser un manifeste de module

1. Pour créer un manifeste de module, vous disposez de plusieurs options :

   1. Directement créer la table de hachage avec les informations minimales requises et enregistrez-le dans un fichier .psd1 qui a le même nom que votre module. Une fois que vous avez fait, vous pouvez ouvrir le fichier et ajouter manuellement les valeurs appropriées.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Ou appelez le [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) applet de commande, avec une ou plusieurs des valeurs par défaut passés comme paramètres. (Notez que le seul le nom du fichier est requis pour générer un manifeste, toutefois.) Cela va créer un manifeste de module avec toutes les manifestes valeurs que vous avez fourni explicitement indiqués et avec le reste contenant la valeur par défaut approprié.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Enfin, vous pouvez également créer un fichier .psd1 vide, copiez le modèle en bas de cette rubrique dans le fichier et renseignez les valeurs appropriées. Dans ce cas, la seule condition serait pour vous assurer que le fichier a été le même nom que le module.

2. Ajouter dans tous les éléments supplémentaires au manifeste que vous souhaitez avoir dans le fichier.

   En règle générale, cela sera probablement le faire dans quelque éditeur de texte que vous préférez, tel que le bloc-notes. Toutefois, cela est techniquement un fichier de script contenant du code, donc vous pouvez souhaiter modifier dans un environnement de développement ou de script réel, tels que PowerShell ISE. Là encore, notez que tous les éléments d’un fichier manifeste sont facultatives, à l’exception du nombre de ModuleVersion.

   Pour obtenir une description des clés et des valeurs que vous pouvez avoir dans un manifeste de module, consultez le **éléments de manifeste de Module** ci-dessous. Pour plus d’informations, consultez les descriptions de paramètre dans le [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) applet de commande.

3. Si vous le souhaitez, vous pouvez choisir Ajouter du code supplémentaire dans le manifeste de module, pour résoudre les scénarios qui ne sont pas couverts par les éléments de manifeste de module de base.

   Pour des raisons de sécurité, PowerShell s’exécute uniquement un petit sous-ensemble des opérations disponibles dans un fichier de manifeste de module. En règle générale, vous pouvez utiliser la **si** instruction, les opérateurs arithmétiques et de comparaison et les types de données PowerShell base.

4. Une fois que vous avez créé votre manifeste de module, vous pouvez le tester (pour confirmer que les chemins d’accès décrites dans le manifest sont correctes) avec un appel à [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. N’oubliez pas que votre manifeste de module se trouve dans le niveau supérieur du répertoire qui contient votre module.

   Lorsque vous copiez votre module sur un système et l’importer, PowerShell utilise le manifeste de module pour importer votre module.

6. Si vous le souhaitez, vous pouvez tester directement votre manifeste de module avec un appel à [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) par le manifeste lui-même dot sourcing.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Éléments de manifeste de module

Le tableau suivant décrit les éléments que vous pouvez avoir dans un manifeste de module

|Élément|Par défaut|Description|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Type : chaîne|' '|Module ou binaire module fichier de script associé à ce manifeste. Versions précédentes de PowerShell appelé le ModuleToProcess à cet élément.<br /><br /> Les types possibles pour le module racine peuvent être vides (qui rendront ce un **manifeste** module), le nom d’un module de script (.psm1, ce qui rend cela un **Script** module), ou le nom d’un module binaire (.exe ou .dll, ce qui rend cela un **binaire** module). Placer le nom d’un manifeste de module (.psd1) ou un fichier de script (.ps1) dans cet élément entraîne une erreur se produit.|
|ModuleVersion<br /><br /> Type : chaîne|1.0|Numéro de version de ce module. La chaîne doit être en mesure de convertir [System.Version]. Autrement dit, « #. #. #. #. # ». `Import-Module` chargera le premier module qu’il trouve sur le **$psModulePath** qui correspond au nom et au moins une valeur ModuleVersion, comme le `-MinimumVersion` paramètre. Pour importer une version spécifique, utilisez le`-RequiredVersion` paramètre, à la place.<br /><br /> Exemple : `ModuleVersion = '1.0'`|
|GUID<br /><br /> Type : chaîne|GUID générés automatiquement|ID utilisé pour identifier de manière unique ce module. Notez que vous ne pouvez pas actuellement importer un module par GUID.<br /><br /> Exemple : `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Auteur<br /><br /> Type : chaîne|Aucune|Auteur de ce module.<br /><br /> Exemple : `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Type : chaîne|Unknown|Entreprise ou fournisseur de ce module.<br /><br /> Exemple : `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Type : chaîne|(c) [currentYear] [auteur]. Tous droits réservés.|Déclaration de copyright pour ce module.<br /><br /> Exemple : `Copyright = '2016 AuthorName. All rights reserved.'`|
|Description<br /><br /> Type : chaîne|' '|Description de la fonctionnalité fournie par ce module.<br /><br /> Exemple : `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Type : chaîne|' '|Version minimale du moteur Windows PowerShell requis par ce module. Valeurs valides actuelles sont 1.0, 2.0, 3.0, 4.0 et 5.0.<br /><br /> Exemple : `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Type : chaîne|' '|Spécifie le nom de l’hôte Windows PowerShell qui est requis par le module. Ce nom est fourni par Windows PowerShell. Pour rechercher le nom d’un programme hôte, dans le programme, tapez : `$host.name` .<br /><br /> Exemple : `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Type : chaîne|' '|Version minimale de l’hôte Windows PowerShell requis par ce module.<br /><br /> Exemple : `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Type : chaîne|' '|Version minimale du Microsoft .NET Framework requise par ce module.<br /><br /> Exemple : `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Type : chaîne|' '|Version minimale du common language runtime (CLR) requis par ce module.<br /><br /> Exemple : `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Type : chaîne|' '|Architecture de processeur (aucun, X86, Amd64) requis par ce module. Les valeurs valides sont x86, AMD64, IA64 et None (valeur inconnue ou non spécifiée).<br /><br /> Exemple : `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type : [chaîne []]|@()|Modules qui doivent être importés dans l’environnement global avant d’importer ce module. Cette opération charge tous les modules, sauf si elles ont déjà été chargés. (Par exemple, certains modules peuvent déjà être chargés par un autre module.). Il est également possible de spécifier une version spécifique à charger à l’aide de `RequiredVersion` plutôt que `ModuleVersion`. Lorsque vous utilisez `ModuleVersion` il chargera la version la plus récente disponible avec un minimum de la version spécifiée.<br /><br /> Exemple : `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Exemple : `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Type : [chaîne []]|@()|Assemblys qui doivent être chargés avant d’importer ce module.<br /><br /> Notez que contrairement à RequiredModules, PowerShell chargera le RequiredAssemblies s’ils ne sont pas déjà chargés.|
|ScriptsToProcess<br /><br /> Type : [chaîne []]|@()|Fichiers de script (.ps1) qui sont exécutés dans l’état de session de l’appelant quand le module est importé. Cela peut être la session globale état ou, pour les modules imbriqués, l’état de session d’un autre module. Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de connexion.<br /><br /> Ces scripts sont exécutés avant qu’un des modules répertoriés dans le manifeste sont chargé.|
|TypesToProcess<br /><br /> Type : [objet []]|@()|Type de fichiers (.ps1xml) à charger lors de l’importation de ce module.|
|FormatsToProcess<br /><br /> Type : [objet []]|@()|Mettre en forme (.ps1xml) de fichiers à charger lors de l’importation de ce module.|
|NestedModules<br /><br /> Type : [objet []]|@()|Modules à importer en tant que modules imbriqués du module spécifié dans RootModule/ModuleToProcess.<br /><br /> Ajout d’un nom de module à cet élément est similaire à l’appel `Import-Module` à partir de votre code de script ou l’assembly. La principale différence est qu’il est plus facile de voir ce que vous chargez ici dans le fichier manifeste. En outre, si un module ne parvient pas à charger ici, vous ne serez pas encore avez chargé votre module réelle.<br /><br /> En plus des autres modules, vous pourrez également charger des fichiers de script (.ps1) ici. Ces fichiers seront exécutera dans le contexte du module racine. (Cela équivaut à dot sourcing le script dans votre module racine.)|
|FunctionsToExport<br /><br /> Type : String|'*'|Spécifie les fonctions exportées par le module (caractère générique sont autorisés) à l’état de session de l’appelant. Par défaut, toutes les fonctions sont exportées. Vous pouvez utiliser cette clé pour limiter les fonctions exportées par le module.<br /><br /> État de session de l’appelant peut être la session globale état ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque le chaînage des modules imbriqués, toutes les fonctions exportées par un module imbriqué seront exportées vers l’état de session global, sauf si un module dans la chaîne empêche la fonction à l’aide de la clé de FunctionsToExport.<br /><br /> Si le manifeste exporte également les alias pour les fonctions, cette clé peut supprimer des fonctions dont les alias sont répertoriés dans la clé AliasesToExport, mais cette clé ne peut pas ajouter les alias de fonction à la liste.|
|CmdletsToExport<br /><br /> Type : String|'*'|Spécifie les applets de commande exportées par le module (caractère générique sont autorisés). Par défaut, toutes les applets de commande sont exportées. Vous pouvez utiliser cette clé pour restreindre les applets de commande qui sont exportées par le module.<br /><br /> État de session de l’appelant peut être la session globale état ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous sont le chaînage des modules imbriqués, toutes les applets de commande exportées par un module imbriqué seront finalement exportés à l’état de session global, sauf si un module dans la chaîne empêche l’applet de commande à l’aide de la clé de CmdletsToExport.<br /><br /> Si le manifeste exporte également les alias pour les applets de commande, cette clé peut supprimer des applets de commande dont les alias sont répertoriés dans la clé AliasesToExport, mais cette clé ne peut pas ajouter des alias d’applet de commande à la liste.|
|VariablesToExport<br /><br /> Type : String|'*'|Spécifie les variables exportées par le module (caractère générique sont autorisés) à l’état de session de l’appelant. Par défaut, toutes les variables sont exportées. Vous pouvez utiliser cette clé pour limiter les variables qui sont exportées par le module.<br /><br /> État de session de l’appelant peut être la session globale état ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous sont le chaînage des modules imbriqués, toutes les variables qui sont exportées par un module imbriqué seront exportés vers l’état de session global, sauf si un module dans la chaîne indique que la variable à l’aide de la clé VariablesToExport.<br /><br /> Si le manifeste exporte également les alias pour les variables, cette clé peut supprimer des variables dont les alias sont répertoriées dans la clé AliasesToExport, mais cette clé ne peut pas ajouter des alias de variable à la liste.|
|AliasesToExport<br /><br /> Type : String|'*'|Spécifie les alias exportées par le module (caractère générique sont autorisés) à l’état de session de l’appelant. Par défaut, tous les alias sont exportées. Vous pouvez utiliser cette clé pour limiter les alias exportés par le module.<br /><br /> État de session de l’appelant peut être la session globale état ou, pour les modules imbriqués, l’état de session d’un autre module. Lorsque vous sont le chaînage des modules imbriqués, tous les alias exportés par un module imbriqué seront finalement exportés à l’état de session global, sauf si un module dans la chaîne empêche l’alias à l’aide de la clé AliasesToExport.|
|ModuleList<br /><br /> Type : [chaîne []]|@()|Spécifie tous les modules qui sont empaquetés avec ce module. Ces modules peuvent être entrés par nom (une chaîne séparée par des virgules) ou sur une table de hachage avec les clés ModuleName et GUID. La table de hachage peut avoir également une clé ModuleVersion facultative. La clé ModuleList est conçue pour agir en tant qu’un inventaire de module. Ces modules ne sont pas traitées automatiquement.|
|FileList<br /><br /> Type : [chaîne []]|@()|Liste de tous les fichiers sont empaquetés avec ce module. Comme avec ModuleList, FileList consiste à vous aider en tant qu’une liste d’inventaire et n’est pas traitée dans le cas contraire.|
|PrivateData<br /><br /> Type : [object]|' '|Spécifie des données privées devant être transmis au module racine spécifié par la clé RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Type : chaîne|' '|HelpInfo URI de ce module.|
|DefaultCommandPrefix<br /><br /> Type : chaîne|' '|Préfixe par défaut pour les commandes exportées à partir de ce module. Remplacer le préfixe par défaut à l’aide `Import-Module` -préfixe.|

## <a name="sample-module-manifest"></a>Exemple de manifeste de Module

Le manifeste de module d’exemple suivant montre les clés et les valeurs par défaut dans un manifeste de module. Cet exemple a été créé à l’aide de la `New-ModuleManifest` applet de commande dans Windows PowerShell 3.0. Lorsque vous créez plusieurs modules, vous pouvez utiliser cette applet de commande pour créer un modèle de manifeste qui peut ensuite être modifié pour différents modules.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Voir aussi

[Écrire un Module PowerShell de Windows](./writing-a-windows-powershell-module.md)
