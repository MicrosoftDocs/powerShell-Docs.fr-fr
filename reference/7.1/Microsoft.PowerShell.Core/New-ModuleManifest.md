---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 21d9f21414eec761fbab77ffcc35a9f57706263a
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879267"
---
# New-ModuleManifest

## SYNOPSIS
Crée un manifeste de module.

## SYNTAXE

### Tous

```
New-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-PowerShellVersion <Version>] [-CLRVersion <Version>] [-DotNetFrameworkVersion <Version>]
 [-PowerShellHostName <String>] [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>]
 [-RequiredAssemblies <String[]>] [-FileList <String[]>] [-ModuleList <Object[]>]
 [-FunctionsToExport <String[]>] [-AliasesToExport <String[]>] [-VariablesToExport <String[]>]
 [-CmdletsToExport <String[]>] [-DscResourcesToExport <String[]>] [-CompatiblePSEditions <String[]>]
 [-PrivateData <Object>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ReleaseNotes <String>] [-Prerelease <String>] [-RequireLicenseAcceptance]
 [-ExternalModuleDependencies <String[]>] [-HelpInfoUri <String>] [-PassThru]
 [-DefaultCommandPrefix <String>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## Description

L' `New-ModuleManifest` applet de commande crée un fichier manifeste de module ( `.psd1` ), remplit ses valeurs et enregistre le fichier manifeste dans le chemin d’accès spécifié.

Les auteurs de modules peuvent utiliser cette applet de commande afin de créer un manifeste pour leur module. Un manifeste de module est un `.psd1` fichier qui contient une table de hachage. Les clés et valeurs de la table de hachage décrivent le contenu et les attributs du module, définissent les conditions préalables, et déterminent la façon dont les composants sont traités. Les manifestes ne sont pas nécessaires pour un module.

`New-ModuleManifest` crée un manifeste qui contient toutes les clés de manifeste couramment utilisées, vous pouvez donc utiliser la sortie par défaut comme modèle de manifeste. Pour ajouter ou modifier des valeurs, ou pour ajouter des clés de module que cette applet de commande n’ajoute pas, ouvrez le fichier résultant dans un éditeur de texte.

Chaque paramètre, à l’exception de **path** et **PassThru**, crée une clé de manifeste de module et sa valeur.
Dans un manifeste de module, seule la clé **ModuleVersion** est obligatoire. À moins qu’il ne soit spécifié dans la description du paramètre, si vous omettez un paramètre de la commande, `New-ModuleManifest` crée une chaîne de commentaire pour la valeur associée qui n’a aucun effet.

Dans PowerShell 2,0, `New-ModuleManifest` vous invite à entrer les valeurs des paramètres couramment utilisés qui ne sont pas spécifiés dans la commande, en plus des valeurs de paramètre requises. À compter de PowerShell 3,0, `New-ModuleManifest` invites lorsque les valeurs de paramètres requises ne sont pas spécifiées.

Si vous envisagez de publier votre module dans le PowerShell Gallery, le manifeste doit contenir des valeurs pour certaines propriétés. Pour plus d’informations, consultez [métadonnées requises pour les éléments publiés dans le PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) dans la documentation de la Galerie.

## EXEMPLES

### Exemple 1 : créer un manifeste de module

Cet exemple crée un nouveau manifeste de module dans le fichier spécifié par le paramètre **path** .
Le paramètre **PassThru** envoie la sortie au pipeline et au fichier.

La sortie indique les valeurs par défaut de toutes les clés du manifeste.

```powershell
New-ModuleManifest -Path C:\ps-test\Test-Module\Test-Module.psd1 -PassThru
```

```Output
#
# Module manifest for module 'Test-Module'
#
# Generated by: ContosoAdmin
#
# Generated on: 7/12/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'e1826c6e-c420-4eef-9ac8-185e3669ca6a'

# Author of this module
Author = 'ContosoAdmin'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) ContosoAdmin. All rights reserved.'

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
        # RequireLicenseAcceptance = $false

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

### Exemple 2 : créer un nouveau manifeste avec des paramètres préremplis

Cet exemple crée un manifeste de module. Elle utilise les paramètres **PowerShellVersion** et **AliasesToExport** pour ajouter des valeurs aux clés de manifeste correspondantes.

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### Exemple 3 : créer un manifeste qui requiert d’autres modules

Cet exemple utilise un format de chaîne pour spécifier le nom du module **BitsTransfer** et le format de la table de hachage pour spécifier le nom, un **GUID** et une version du module **PSScheduledJob** .

```powershell
$moduleSettings = @{
  RequiredModules = ("BitsTransfer", @{
    ModuleName="PSScheduledJob"
    ModuleVersion="1.0.0.0";
    GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"
  })
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

Cet exemple montre comment utiliser les formats de table de hachage et de chaîne du paramètre **ModuleList**, **RequiredModules** et **NestedModules** . Vous pouvez combiner des chaînes et des tables de hachage dans la même valeur de paramètre.

### Exemple 4 : créer un manifeste qui prend en charge l’aide actualisable

Cet exemple utilise le paramètre **HelpInfoUri** pour créer une clé **HelpInfoUri** dans le manifeste de module. La valeur du paramètre et de la clé doit commencer par **http** ou **https**. Cette valeur indique au système d'aide actualisable où trouver le fichier XML d'informations HelpInfo sur l'aide actualisable du module.

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](./About/about_Updatable_Help.md).
Pour plus d’informations sur le fichier XML HelpInfo, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).

### Exemple 5 : obtention d’informations sur le module

Cet exemple montre comment obtenir les valeurs de configuration d’un module. Les valeurs du manifeste de module sont reflétées dans les valeurs des propriétés de l’objet de module.

L' `Get-Module` applet de commande est utilisée pour récupérer le module **Microsoft. PowerShell. Diagnostics** à l’aide du paramètre **List** . La commande envoie le module à l' `Format-List` applet de commande pour afficher toutes les propriétés et valeurs de l’objet de module.

```powershell
Get-Module Microsoft.PowerShell.Diagnostics -List | Format-List -Property *
```

```Output
LogPipelineExecutionDetails : False
Name                        : Microsoft.PowerShell.Diagnostics
Path                        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics\Micro
                              soft.PowerShell.Diagnostics.psd1
Definition                  :
Description                 :
Guid                        : ca046f10-ca64-4740-8ff9-2565dba61a4f
HelpInfoUri                 : https://go.microsoft.com/fwlink/?LinkID=210596
ModuleBase                  : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics
PrivateData                 :
Version                     : 3.0.0.0
ModuleType                  : Manifest
Author                      : Microsoft Corporation
AccessMode                  : ReadWrite
ClrVersion                  : 4.0
CompanyName                 : Microsoft Corporation
Copyright                   : Microsoft Corporation. All rights reserved.
DotNetFrameworkVersion      :
ExportedFunctions           : {}
ExportedCmdlets             : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
ExportedCommands            : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
FileList                    : {}
ModuleList                  : {}
NestedModules               : {}
PowerShellHostName          :
PowerShellHostVersion       :
PowerShellVersion           : 3.0
ProcessorArchitecture       : None
Scripts                     : {}
RequiredAssemblies          : {}
RequiredModules             : {}
RootModule                  :
ExportedVariables           : {}
ExportedAliases             : {}
ExportedWorkflows           : {}
SessionState                :
OnRemove                    :
ExportedFormatFiles         : {C:\Windows\system32\WindowsPowerShell\v1.0\Event.format.ps1xml,
                              C:\Windows\system32\WindowsPowerShell\v1.0\Diagnostics.format.ps1xml}
ExportedTypeFiles           : {C:\Windows\system32\WindowsPowerShell\v1.0\GetEvent.types.ps1xml}
```

## PARAMETERS

### -AliasesToExport

Spécifie les alias exportés par le module. Les caractères génériques sont autorisés.

Vous pouvez utiliser ce paramètre pour limiter les alias exportés par le module. Elle peut supprimer des alias de la liste des alias exportés, mais elle ne peut pas ajouter d’alias à la liste.

Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **AliasesToExport** avec `*` la valeur (All), ce qui signifie que tous les alias définis dans le module sont exportés par le manifeste.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -Auteur

Spécifie l'auteur du module.

Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé d' **auteur** avec le nom de l’utilisateur actuel.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Name of the current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -CmdletsToExport

Spécifie les applets de commande exportées par le module. Les caractères génériques sont autorisés.

Vous pouvez utiliser ce paramètre pour limiter les applets de commande exportées par le module. Elle peut supprimer des applets de commande de la liste des applets de commande exportées, mais elle ne peut pas ajouter d’applets de commande à la liste.

Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **CmdletsToExport** avec `*` la valeur (All), ce qui signifie que toutes les applets de commande définies dans le module sont exportées par le manifeste.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -CompanyName

Identifie la société ou le fournisseur qui a créé le module.

Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **CompanyName** avec la valeur « Unknown ».

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: "Unknown"
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompatiblePSEditions

Spécifie le des éditions PS compatible du module. Pour plus d’informations sur PSEdition, consultez [modules avec des éditions PowerShell compatibles](/powershell/scripting/gallery/concepts/module-psedition-support).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Copyright

Spécifie une déclaration de copyright pour le module.

Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé de **Copyright** avec la valeur `(c) <year> <username>. All rights reserved.` où `<year>` est l’année en cours et `<username>` est la valeur de la clé d' **auteur** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (c) <year> <username>. All rights reserved.
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultCommandPrefix

Spécifie un préfixe qui est ajouté aux noms de toutes les commandes du module lorsqu’elles sont importées dans une session. Entrez une chaîne de préfixe. Les préfixes empêchent les conflits de noms de commande dans la session d'un utilisateur.

Les utilisateurs du module peuvent remplacer ce préfixe en spécifiant le paramètre **prefix** de l’applet de commande `Import-Module` .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### Description

Décrit le contenu du module.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DotNetFrameworkVersion

Spécifie la version minimale de Microsoft .NET Framework dont le module a besoin.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DscResourcesToExport

Spécifie les ressources de configuration d’état souhaité (DSC) exportées par le module. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ExternalModuleDependencies

Liste des modules externes dont ce module dépend.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileList

Spécifie tous les éléments qui sont inclus dans le module.

Cette clé est conçue pour agir en tant qu'inventaire de module. Les fichiers répertoriés dans la clé sont inclus lors de la publication du module, mais les fonctions ne sont pas exportées automatiquement.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

Spécifie les fichiers de mise en forme ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.

Lorsque vous importez un module, PowerShell exécute l' `Update-FormatData` applet de commande avec les fichiers spécifiés.
Étant donné que les fichiers de mise en forme ne sont pas étendus, ils affectent tous les États de session de la session.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FunctionsToExport

Spécifie les fonctions exportées par le module. Les caractères génériques sont autorisés.

Vous pouvez utiliser ce paramètre pour limiter les fonctions exportées par le module. Elle peut supprimer des fonctions de la liste des alias exportés, mais elle ne peut pas ajouter de fonctions à la liste.

Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **FunctionsToExport** avec `*` la valeur (All), ce qui signifie que toutes les fonctions définies dans le module sont exportées par le manifeste.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -Guid

Spécifie un identificateur unique pour le module. Le **GUID** peut être utilisé pour faire la distinction entre les modules portant le même nom.

Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **GUID** dans le manifeste et génère un **GUID** pour la valeur.

Pour créer un nouveau **GUID** dans PowerShell, tapez `[guid]::NewGuid()` .

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A GUID generated for the module
Accept pipeline input: False
Accept wildcard characters: False
```

### -HelpInfoUri

Spécifie l’adresse Internet du fichier XML HelpInfo du module. Entrez un Uniform Resource Identifier (URI) qui commence par **http** ou **https**.

Le fichier XML HelpInfo prend en charge la fonctionnalité d’aide actualisable qui a été introduite dans PowerShell 3,0. Il contient des informations sur l'emplacement des fichiers d'aide téléchargeables pour le module, et les numéros de version des fichiers d'aide les plus récents pour chacun des paramètres régionaux pris en charge.

Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](./About/about_Updatable_Help.md).
Pour plus d’informations sur le fichier XML HelpInfo, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

Spécifie l’URL d’une icône pour le module. L’icône spécifiée est affichée sur la page Web de la Galerie pour le module.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseUri

Spécifie l’URL des termes du contrat de licence pour le module.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleList

Répertorie tous les modules qui sont inclus dans ce module.

Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**. La table de hachage peut également avoir une clé **GUID** facultative. Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.

Cette clé est conçue pour agir en tant qu'inventaire de module. Les modules répertoriés dans la valeur de cette clé ne sont pas traités automatiquement.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleVersion

Spécifie la version du module.

Ce paramètre n’est pas obligatoire, mais une clé **ModuleVersion** est requise dans le manifeste. Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **ModuleVersion** avec une valeur de 1,0.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1.0
Accept pipeline input: False
Accept wildcard characters: False
```

### -NestedModules

Spécifie les modules de script ( `.psm1` ) et les modules binaires ( `.dll` ) qui sont importés dans l’état de session du module. Les fichiers de la clé **NestedModules** s’exécutent dans l’ordre dans lequel ils sont listés dans la valeur.

Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**. La table de hachage peut également avoir une clé **GUID** facultative. Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.

En règle générale, les modules imbriqués contiennent les commandes dont le module racine a besoin pour son traitement interne.
Par défaut, les commandes dans les modules imbriqués sont exportées de l’état de session du module vers l’état de session de l’appelant, mais le module racine peut restreindre les commandes qu’il exporte. Par exemple, à l’aide d’une `Export-ModuleMember` commande.

Les modules imbriqués dans l’état de session du module sont disponibles pour le module racine, mais ils ne sont pas retournés par une `Get-Module` commande dans l’état de session de l’appelant.

Les scripts ( `.ps1` ) qui sont répertoriés dans la clé **NestedModules** sont exécutés dans l’état de session du module, et non dans l’état de session de l’appelant. Pour exécuter un script dans l'état de session de l'appelant, répertoriez le nom du fichier de script dans la valeur de la clé **ScriptsToProcess** du manifeste.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Écrit le manifeste de module résultant dans la console et crée un `.psd1` fichier. Par défaut, cette applet de commande ne génère pas de sortie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d'accès et le nom de fichier du nouveau manifeste de module. Entrez un chemin d’accès et un nom de fichier avec une `.psd1` extension de nom de fichier, par exemple `$pshome\Modules\MyModule\MyModule.psd1` . Le paramètre **path** est obligatoire.

Si vous spécifiez le chemin d’accès à un fichier existant, `New-ModuleManifest` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule.

Le manifeste doit se trouver dans le répertoire du module, et le nom du fichier manifeste doit être le même que le nom du répertoire du module, mais avec une `.psd1` extension de nom de fichier.

> [!NOTE]
> Vous ne pouvez pas utiliser de variables, telles que `$PSHOME` ou `$HOME` , en réponse à une invite pour une valeur de paramètre de **chemin d’accès** . Pour utiliser une variable, incluez le paramètre **Path** dans la commande.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellHostName

Spécifie le nom du programme hôte PowerShell requis par le module. Entrez le nom du programme hôte, par exemple **Windows PowerShell ISE hôte** ou **ConsoleHost**. Les caractères génériques ne sont pas autorisés.

Pour rechercher le nom d’un programme hôte, dans le programme, tapez `$Host.Name` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellHostVersion

Spécifie la version minimale du programme hôte PowerShell qui fonctionne avec le module. Entrez un numéro de version, par exemple 1.1.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

Spécifie la version minimale de PowerShell qui fonctionne avec ce module. Par exemple, vous pouvez entrer 1,0, 2,0 ou 3,0 comme valeur du paramètre. Elle doit être au format X. X. Par exemple, si vous envoyez `5` , PowerShell génère une erreur.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version préliminaire

Chaîne de version préliminaire de ce module. L’ajout d’une chaîne de préversion identifie le module comme une version préliminaire. Lorsque le module est publié dans le PowerShell Gallery, ces données sont utilisées pour identifier les packages de version préliminaire. Pour acquérir des packages de version préliminaire à partir de la Galerie, vous devez utiliser le paramètre **AllowPrerelease** avec les commandes PowerShellGet `Find-Module` ,, `Install-Module` `Update-Module` et `Save-Module` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrivateData

Spécifie les données qui sont passées au module lors de son importation.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessorArchitecture

Spécifie l'architecture de processeur dont le module a besoin. Les valeurs valides sont x86, AMD64, IA64, MSIL et None (inconnu ou non spécifié).

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectUri

Spécifie l’URL d’une page Web sur ce projet.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReleaseNotes

Spécifie des notes de publication.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredAssemblies

Spécifie les fichiers d’assembly ( `.dll` ) dont le module a besoin. Entrez les noms de fichiers d'assembly.
PowerShell charge les assemblys spécifiés avant de mettre à jour des types ou des formats, d’importer des modules imbriqués ou d’importer le fichier de module spécifié dans la valeur de la clé **RootModule** .

Utilisez ce paramètre pour répertorier tous les assemblys dont le module a besoin, y compris les assemblys qui doivent être chargés pour mettre à jour les fichiers de mise en forme ou de type répertoriés dans les clés **FormatsToProcess** ou **TypesToProcess**, même si ces assemblys sont également répertoriés en tant que modules binaires dans la clé **NestedModules**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredModules

Spécifie les modules qui doivent être dans l'état de session global. Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe. Si les modules requis ne sont pas disponibles, la `Import-Module` commande échoue.

Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**. La table de hachage peut également avoir une clé **GUID** facultative. Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.

Dans PowerShell 2,0, `Import-Module` n’importe pas automatiquement les modules requis. Elle vérifie simplement que les modules obligatoires se trouvent dans l'état de session global.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequireLicenseAcceptance

Indicateur qui spécifie si le module requiert une acceptation explicite de l’utilisateur pour l’installation, la mise à jour, orsave.

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

### -RootModule

Spécifie le fichier principal ou racine du module. Entrez le nom de fichier d’un script ( `.ps1` ), d’un module de script ( `.psm1` ), d’un manifeste de module ( `.psd1` ), d’un assembly ( `.dll` ), d’un fichier XML de définition d’applet de commande ( `.cdxml` ) ou d’un flux de travail ( `.xaml` ). Quand le module est importé, les membres exportés à partir du fichier de module racine sont importés dans l'état de session de l'appelant.

Si un module a un fichier manifeste et qu’aucun fichier racine n’a été désigné dans la clé **RootModule** , le manifeste devient le fichier primaire pour le module et le module devient un module de manifeste (ModuleType = manifest).

Pour exporter des membres à partir de `.psm1` `.dll` fichiers ou dans un module qui a un manifeste, les noms de ces fichiers doivent être spécifiés dans les valeurs des clés **RootModule** ou **NestedModules** dans le manifeste. Dans le cas contraire, leurs membres ne sont pas exportés.

> [!NOTE]
> Dans PowerShell 2,0, cette clé était appelée **ModuleToProcess**. Vous pouvez utiliser le nom du paramètre **RootModule** ou son alias **ModuleToProcess** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ModuleToProcess

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

Spécifie les fichiers de script ( `.ps1` ) qui s’exécutent dans l’état de session de l’appelant lors de l’importation du module.
Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de connexion.

Pour spécifier les scripts qui s'exécutent dans l'état de session du module, utilisez la clé **NestedModules**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tags

Spécifie un tableau de balises.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypesToProcess

Spécifie les fichiers de type ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.

Lorsque vous importez le module, PowerShell exécute l' `Update-TypeData` applet de commande avec les fichiers spécifiés.
Étant donné que les fichiers de type ne sont pas étendus, ils affectent tous les États de session de la session.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariablesToExport

Spécifie les variables exportées par le module. Les caractères génériques sont autorisés.

Vous pouvez utiliser ce paramètre pour limiter les variables exportées par le module. Elle peut supprimer des variables de la liste des variables exportées, mais elle ne peut pas ajouter de variables à la liste.

Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **VariablesToExport** avec `*` la valeur (All), ce qui signifie que toutes les variables définies dans le module sont exportées par le manifeste.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

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

### -WhatIf

Montre ce qui se passe si `New-ModuleManifest` s’exécute. L’applet de commande n’est pas exécutée.

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

### -ClrVersion

Spécifie la version minimale du Common Language Runtime (CLR) de Microsoft .NET Framework dont le module a besoin.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’entrée vers cette applet de commande.

## SORTIES

### Aucune ou System.String

Par défaut, `New-ModuleManifest` ne génère pas de sortie. Toutefois, si vous utilisez le paramètre **PassThru** , il génère un objet **System. String** qui représente le manifeste de module.

## REMARQUES

`New-ModuleManifest` l’exécution sur des plateformes Windows et non Windows crée des fichiers de manifeste de module ( `.psd1` ) encodés en tant que **UTF8NoBOM**.

Les manifestes de module sont généralement facultatifs. Toutefois, un manifeste de module est nécessaire pour exporter un assembly installé dans le Global Assembly Cache.

Pour ajouter ou modifier des fichiers dans le `$pshome\Modules` répertoire, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

> [!NOTE]
> À compter de PowerShell 6,2, PowerShell tente de charger tous les fichiers DLL listés dans la propriété **filelist** du manifeste de module. Le chargement des DLL natives dans la **filelist** échoue dans le processus et l’erreur est ignorée. Toutes les DLL managées sont chargées dans le processus. Ce comportement a été supprimé dans PowerShell 7,1.

Dans PowerShell 2,0, de nombreux paramètres de `New-ModuleManifest` étaient obligatoires, même s’ils n’étaient pas requis dans un manifeste de module. À compter de PowerShell 3,0, seul le paramètre **path** est obligatoire.

Une session est une instance de l’environnement d’exécution de PowerShell. Une session peut avoir un ou plusieurs états de session. Par défaut, une session possède uniquement un état de session global, mais chaque module importé a son propre état de session. Les états de session permettent aux commandes de s'exécuter dans un module sans affecter l'état de session global.

L’état de session de l’appelant est l’état de session dans lequel un module est importé. En règle générale, il fait référence à l’état de session global, mais lorsqu’un module importe des modules imbriqués, l’appelant est le module et l’état de session de l’appelant est l’état de session du module.

## LIENS CONNEXES

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[Module d’importation](Import-Module.md)

[New-Module](New-Module.md)

[Remove-Module](Remove-Module.md)

[Test-ModuleManifest](Test-ModuleManifest.md)

[about_Modules](./About/about_Modules.md)
