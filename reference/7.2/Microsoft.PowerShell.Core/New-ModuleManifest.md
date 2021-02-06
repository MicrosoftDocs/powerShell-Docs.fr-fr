---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 713c35b2f9f651d455ac08401aa1f7eb48676174
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "99598181"
---
# <span data-ttu-id="ed94c-102">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="ed94c-102">New-ModuleManifest</span></span>

## <span data-ttu-id="ed94c-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ed94c-103">SYNOPSIS</span></span>
<span data-ttu-id="ed94c-104">Crée un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-104">Creates a new module manifest.</span></span>

## <span data-ttu-id="ed94c-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ed94c-105">SYNTAX</span></span>

### <span data-ttu-id="ed94c-106">Tous</span><span class="sxs-lookup"><span data-stu-id="ed94c-106">All</span></span>

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

## <span data-ttu-id="ed94c-107">Description</span><span class="sxs-lookup"><span data-stu-id="ed94c-107">DESCRIPTION</span></span>

<span data-ttu-id="ed94c-108">L' `New-ModuleManifest` applet de commande crée un fichier manifeste de module ( `.psd1` ), remplit ses valeurs et enregistre le fichier manifeste dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="ed94c-108">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="ed94c-109">Les auteurs de modules peuvent utiliser cette applet de commande afin de créer un manifeste pour leur module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-109">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="ed94c-110">Un manifeste de module est un `.psd1` fichier qui contient une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="ed94c-110">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="ed94c-111">Les clés et valeurs de la table de hachage décrivent le contenu et les attributs du module, définissent les conditions préalables, et déterminent la façon dont les composants sont traités.</span><span class="sxs-lookup"><span data-stu-id="ed94c-111">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="ed94c-112">Les manifestes ne sont pas nécessaires pour un module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-112">Manifests aren't required for a module.</span></span>

<span data-ttu-id="ed94c-113">`New-ModuleManifest` crée un manifeste qui contient toutes les clés de manifeste couramment utilisées, vous pouvez donc utiliser la sortie par défaut comme modèle de manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-113">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="ed94c-114">Pour ajouter ou modifier des valeurs, ou pour ajouter des clés de module que cette applet de commande n’ajoute pas, ouvrez le fichier résultant dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="ed94c-114">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="ed94c-115">Chaque paramètre, à l’exception de **path** et **PassThru**, crée une clé de manifeste de module et sa valeur.</span><span class="sxs-lookup"><span data-stu-id="ed94c-115">Each parameter, except for **Path** and **PassThru**, creates a module manifest key and its value.</span></span>
<span data-ttu-id="ed94c-116">Dans un manifeste de module, seule la clé **ModuleVersion** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ed94c-116">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="ed94c-117">À moins qu’il ne soit spécifié dans la description du paramètre, si vous omettez un paramètre de la commande, `New-ModuleManifest` crée une chaîne de commentaire pour la valeur associée qui n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="ed94c-117">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="ed94c-118">Dans PowerShell 2,0, `New-ModuleManifest` vous invite à entrer les valeurs des paramètres couramment utilisés qui ne sont pas spécifiés dans la commande, en plus des valeurs de paramètre requises.</span><span class="sxs-lookup"><span data-stu-id="ed94c-118">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="ed94c-119">À compter de PowerShell 3,0, `New-ModuleManifest` invites lorsque les valeurs de paramètres requises ne sont pas spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ed94c-119">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="ed94c-120">Si vous envisagez de publier votre module dans le PowerShell Gallery, le manifeste doit contenir des valeurs pour certaines propriétés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-120">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="ed94c-121">Pour plus d’informations, consultez [métadonnées requises pour les éléments publiés dans le PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) dans la documentation de la Galerie.</span><span class="sxs-lookup"><span data-stu-id="ed94c-121">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="ed94c-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ed94c-122">EXAMPLES</span></span>

### <span data-ttu-id="ed94c-123">Exemple 1 : créer un manifeste de module</span><span class="sxs-lookup"><span data-stu-id="ed94c-123">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="ed94c-124">Cet exemple crée un nouveau manifeste de module dans le fichier spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-124">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="ed94c-125">Le paramètre **PassThru** envoie la sortie au pipeline et au fichier.</span><span class="sxs-lookup"><span data-stu-id="ed94c-125">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="ed94c-126">La sortie indique les valeurs par défaut de toutes les clés du manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-126">The output shows the default values of all keys in the manifest.</span></span>

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

### <span data-ttu-id="ed94c-127">Exemple 2 : créer un nouveau manifeste avec des paramètres préremplis</span><span class="sxs-lookup"><span data-stu-id="ed94c-127">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="ed94c-128">Cet exemple crée un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-128">This example creates a new module manifest.</span></span> <span data-ttu-id="ed94c-129">Elle utilise les paramètres **PowerShellVersion** et **AliasesToExport** pour ajouter des valeurs aux clés de manifeste correspondantes.</span><span class="sxs-lookup"><span data-stu-id="ed94c-129">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="ed94c-130">Exemple 3 : créer un manifeste qui requiert d’autres modules</span><span class="sxs-lookup"><span data-stu-id="ed94c-130">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="ed94c-131">Cet exemple utilise un format de chaîne pour spécifier le nom du module **BitsTransfer** et le format de la table de hachage pour spécifier le nom, un **GUID** et une version du module **PSScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-131">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID**, and a version of the **PSScheduledJob** module.</span></span>

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

<span data-ttu-id="ed94c-132">Cet exemple montre comment utiliser les formats de table de hachage et de chaîne du paramètre **ModuleList**, **RequiredModules** et **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-132">This example shows how to use the string and hash table formats of the **ModuleList**, **RequiredModules**, and **NestedModules** parameter.</span></span> <span data-ttu-id="ed94c-133">Vous pouvez combiner des chaînes et des tables de hachage dans la même valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="ed94c-133">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="ed94c-134">Exemple 4 : créer un manifeste qui prend en charge l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="ed94c-134">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="ed94c-135">Cet exemple utilise le paramètre **HelpInfoUri** pour créer une clé **HelpInfoUri** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-135">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="ed94c-136">La valeur du paramètre et de la clé doit commencer par **http** ou **https**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-136">The value of the parameter and the key must begin with **http** or **https**.</span></span> <span data-ttu-id="ed94c-137">Cette valeur indique au système d'aide actualisable où trouver le fichier XML d'informations HelpInfo sur l'aide actualisable du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-137">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="ed94c-138">Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="ed94c-138">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="ed94c-139">Pour plus d’informations sur le fichier XML HelpInfo, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="ed94c-139">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="ed94c-140">Exemple 5 : obtention d’informations sur le module</span><span class="sxs-lookup"><span data-stu-id="ed94c-140">Example 5 - Getting module information</span></span>

<span data-ttu-id="ed94c-141">Cet exemple montre comment obtenir les valeurs de configuration d’un module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-141">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="ed94c-142">Les valeurs du manifeste de module sont reflétées dans les valeurs des propriétés de l’objet de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-142">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="ed94c-143">L' `Get-Module` applet de commande est utilisée pour récupérer le module **Microsoft. PowerShell. Diagnostics** à l’aide du paramètre **List** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-143">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="ed94c-144">La commande envoie le module à l' `Format-List` applet de commande pour afficher toutes les propriétés et valeurs de l’objet de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-144">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

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

## <span data-ttu-id="ed94c-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ed94c-145">PARAMETERS</span></span>

### <span data-ttu-id="ed94c-146">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="ed94c-146">-AliasesToExport</span></span>

<span data-ttu-id="ed94c-147">Spécifie les alias exportés par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-147">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="ed94c-148">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-148">Wildcards are permitted.</span></span>

<span data-ttu-id="ed94c-149">Vous pouvez utiliser ce paramètre pour limiter les alias exportés par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-149">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="ed94c-150">Elle peut supprimer des alias de la liste des alias exportés, mais elle ne peut pas ajouter d’alias à la liste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-150">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="ed94c-151">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **AliasesToExport** avec `*` la valeur (All), ce qui signifie que tous les alias définis dans le module sont exportés par le manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-151">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="ed94c-152">-Auteur</span><span class="sxs-lookup"><span data-stu-id="ed94c-152">-Author</span></span>

<span data-ttu-id="ed94c-153">Spécifie l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-153">Specifies the module author.</span></span>

<span data-ttu-id="ed94c-154">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé d' **auteur** avec le nom de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ed94c-154">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

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

### <span data-ttu-id="ed94c-155">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="ed94c-155">-CmdletsToExport</span></span>

<span data-ttu-id="ed94c-156">Spécifie les applets de commande exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-156">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="ed94c-157">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-157">Wildcards are permitted.</span></span>

<span data-ttu-id="ed94c-158">Vous pouvez utiliser ce paramètre pour limiter les applets de commande exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-158">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="ed94c-159">Elle peut supprimer des applets de commande de la liste des applets de commande exportées, mais elle ne peut pas ajouter d’applets de commande à la liste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-159">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="ed94c-160">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **CmdletsToExport** avec `*` la valeur (All), ce qui signifie que toutes les applets de commande définies dans le module sont exportées par le manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-160">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="ed94c-161">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="ed94c-161">-CompanyName</span></span>

<span data-ttu-id="ed94c-162">Identifie la société ou le fournisseur qui a créé le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-162">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="ed94c-163">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **CompanyName** avec la valeur « Unknown ».</span><span class="sxs-lookup"><span data-stu-id="ed94c-163">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

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

### <span data-ttu-id="ed94c-164">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="ed94c-164">-CompatiblePSEditions</span></span>

<span data-ttu-id="ed94c-165">Spécifie le des éditions PS compatible du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-165">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="ed94c-166">Pour plus d’informations sur PSEdition, consultez [modules avec des éditions PowerShell compatibles](/powershell/scripting/gallery/concepts/module-psedition-support).</span><span class="sxs-lookup"><span data-stu-id="ed94c-166">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="ed94c-167">-Copyright</span><span class="sxs-lookup"><span data-stu-id="ed94c-167">-Copyright</span></span>

<span data-ttu-id="ed94c-168">Spécifie une déclaration de copyright pour le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-168">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="ed94c-169">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé de **Copyright** avec la valeur `(c) <year> <username>. All rights reserved.` où `<year>` est l’année en cours et `<username>` est la valeur de la clé d' **auteur** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-169">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

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

### <span data-ttu-id="ed94c-170">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="ed94c-170">-DefaultCommandPrefix</span></span>

<span data-ttu-id="ed94c-171">Spécifie un préfixe qui est ajouté aux noms de toutes les commandes du module lorsqu’elles sont importées dans une session.</span><span class="sxs-lookup"><span data-stu-id="ed94c-171">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="ed94c-172">Entrez une chaîne de préfixe.</span><span class="sxs-lookup"><span data-stu-id="ed94c-172">Enter a prefix string.</span></span> <span data-ttu-id="ed94c-173">Les préfixes empêchent les conflits de noms de commande dans la session d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ed94c-173">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="ed94c-174">Les utilisateurs du module peuvent remplacer ce préfixe en spécifiant le paramètre **prefix** de l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="ed94c-174">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="ed94c-175">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ed94c-175">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ed94c-176">Description</span><span class="sxs-lookup"><span data-stu-id="ed94c-176">-Description</span></span>

<span data-ttu-id="ed94c-177">Décrit le contenu du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-177">Describes the contents of the module.</span></span>

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

### <span data-ttu-id="ed94c-178">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="ed94c-178">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="ed94c-179">Spécifie la version minimale de Microsoft .NET Framework dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="ed94c-179">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="ed94c-180">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="ed94c-180">-DscResourcesToExport</span></span>

<span data-ttu-id="ed94c-181">Spécifie les ressources de configuration d’état souhaité (DSC) exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-181">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="ed94c-182">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-182">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ed94c-183">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="ed94c-183">-ExternalModuleDependencies</span></span>

<span data-ttu-id="ed94c-184">Liste des modules externes dont ce module dépend.</span><span class="sxs-lookup"><span data-stu-id="ed94c-184">A list of external modules that this module is depends on.</span></span>

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

### <span data-ttu-id="ed94c-185">-FileList</span><span class="sxs-lookup"><span data-stu-id="ed94c-185">-FileList</span></span>

<span data-ttu-id="ed94c-186">Spécifie tous les éléments qui sont inclus dans le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-186">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="ed94c-187">Cette clé est conçue pour agir en tant qu'inventaire de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-187">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="ed94c-188">Les fichiers répertoriés dans la clé sont inclus lors de la publication du module, mais les fonctions ne sont pas exportées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ed94c-188">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

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

### <span data-ttu-id="ed94c-189">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="ed94c-189">-FormatsToProcess</span></span>

<span data-ttu-id="ed94c-190">Spécifie les fichiers de mise en forme ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-190">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="ed94c-191">Lorsque vous importez un module, PowerShell exécute l' `Update-FormatData` applet de commande avec les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-191">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="ed94c-192">Étant donné que les fichiers de mise en forme ne sont pas étendus, ils affectent tous les États de session de la session.</span><span class="sxs-lookup"><span data-stu-id="ed94c-192">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="ed94c-193">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="ed94c-193">-FunctionsToExport</span></span>

<span data-ttu-id="ed94c-194">Spécifie les fonctions exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-194">Specifies the functions that the module exports.</span></span> <span data-ttu-id="ed94c-195">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-195">Wildcards are permitted.</span></span>

<span data-ttu-id="ed94c-196">Vous pouvez utiliser ce paramètre pour limiter les fonctions exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-196">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="ed94c-197">Elle peut supprimer des fonctions de la liste des alias exportés, mais elle ne peut pas ajouter de fonctions à la liste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-197">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="ed94c-198">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **FunctionsToExport** avec `*` la valeur (All), ce qui signifie que toutes les fonctions définies dans le module sont exportées par le manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-198">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="ed94c-199">-Guid</span><span class="sxs-lookup"><span data-stu-id="ed94c-199">-Guid</span></span>

<span data-ttu-id="ed94c-200">Spécifie un identificateur unique pour le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-200">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="ed94c-201">Le **GUID** peut être utilisé pour faire la distinction entre les modules portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ed94c-201">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="ed94c-202">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **GUID** dans le manifeste et génère un **GUID** pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="ed94c-202">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="ed94c-203">Pour créer un nouveau **GUID** dans PowerShell, tapez `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="ed94c-203">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="ed94c-204">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="ed94c-204">-HelpInfoUri</span></span>

<span data-ttu-id="ed94c-205">Spécifie l’adresse Internet du fichier XML HelpInfo du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-205">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="ed94c-206">Entrez un Uniform Resource Identifier (URI) qui commence par **http** ou **https**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-206">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="ed94c-207">Le fichier XML HelpInfo prend en charge la fonctionnalité d’aide actualisable qui a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ed94c-207">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="ed94c-208">Il contient des informations sur l'emplacement des fichiers d'aide téléchargeables pour le module, et les numéros de version des fichiers d'aide les plus récents pour chacun des paramètres régionaux pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ed94c-208">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="ed94c-209">Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="ed94c-209">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="ed94c-210">Pour plus d’informations sur le fichier XML HelpInfo, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="ed94c-210">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="ed94c-211">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ed94c-211">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ed94c-212">-IconUri</span><span class="sxs-lookup"><span data-stu-id="ed94c-212">-IconUri</span></span>

<span data-ttu-id="ed94c-213">Spécifie l’URL d’une icône pour le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-213">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="ed94c-214">L’icône spécifiée est affichée sur la page Web de la Galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-214">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="ed94c-215">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="ed94c-215">-LicenseUri</span></span>

<span data-ttu-id="ed94c-216">Spécifie l’URL des termes du contrat de licence pour le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-216">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="ed94c-217">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="ed94c-217">-ModuleList</span></span>

<span data-ttu-id="ed94c-218">Répertorie tous les modules qui sont inclus dans ce module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-218">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="ed94c-219">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-219">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="ed94c-220">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="ed94c-220">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="ed94c-221">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="ed94c-221">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="ed94c-222">Cette clé est conçue pour agir en tant qu'inventaire de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-222">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="ed94c-223">Les modules répertoriés dans la valeur de cette clé ne sont pas traités automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ed94c-223">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="ed94c-224">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="ed94c-224">-ModuleVersion</span></span>

<span data-ttu-id="ed94c-225">Spécifie la version du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-225">Specifies the module's version.</span></span>

<span data-ttu-id="ed94c-226">Ce paramètre n’est pas obligatoire, mais une clé **ModuleVersion** est requise dans le manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-226">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="ed94c-227">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **ModuleVersion** avec une valeur de 1,0.</span><span class="sxs-lookup"><span data-stu-id="ed94c-227">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

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

### <span data-ttu-id="ed94c-228">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="ed94c-228">-NestedModules</span></span>

<span data-ttu-id="ed94c-229">Spécifie les modules de script ( `.psm1` ) et les modules binaires ( `.dll` ) qui sont importés dans l’état de session du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-229">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="ed94c-230">Les fichiers de la clé **NestedModules** s’exécutent dans l’ordre dans lequel ils sont listés dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="ed94c-230">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="ed94c-231">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-231">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="ed94c-232">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="ed94c-232">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="ed94c-233">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="ed94c-233">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="ed94c-234">En règle générale, les modules imbriqués contiennent les commandes dont le module racine a besoin pour son traitement interne.</span><span class="sxs-lookup"><span data-stu-id="ed94c-234">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="ed94c-235">Par défaut, les commandes dans les modules imbriqués sont exportées de l’état de session du module vers l’état de session de l’appelant, mais le module racine peut restreindre les commandes qu’il exporte.</span><span class="sxs-lookup"><span data-stu-id="ed94c-235">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="ed94c-236">Par exemple, à l’aide d’une `Export-ModuleMember` commande.</span><span class="sxs-lookup"><span data-stu-id="ed94c-236">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="ed94c-237">Les modules imbriqués dans l’état de session du module sont disponibles pour le module racine, mais ils ne sont pas retournés par une `Get-Module` commande dans l’état de session de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ed94c-237">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="ed94c-238">Les scripts ( `.ps1` ) qui sont répertoriés dans la clé **NestedModules** sont exécutés dans l’état de session du module, et non dans l’état de session de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ed94c-238">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="ed94c-239">Pour exécuter un script dans l'état de session de l'appelant, répertoriez le nom du fichier de script dans la valeur de la clé **ScriptsToProcess** du manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-239">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

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

### <span data-ttu-id="ed94c-240">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ed94c-240">-PassThru</span></span>

<span data-ttu-id="ed94c-241">Écrit le manifeste de module résultant dans la console et crée un `.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="ed94c-241">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="ed94c-242">Par défaut, cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="ed94c-242">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="ed94c-243">-Path</span><span class="sxs-lookup"><span data-stu-id="ed94c-243">-Path</span></span>

<span data-ttu-id="ed94c-244">Spécifie le chemin d'accès et le nom de fichier du nouveau manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-244">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="ed94c-245">Entrez un chemin d’accès et un nom de fichier avec une `.psd1` extension de nom de fichier, par exemple `$pshome\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="ed94c-245">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="ed94c-246">Le paramètre **path** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ed94c-246">The **Path** parameter is required.</span></span>

<span data-ttu-id="ed94c-247">Si vous spécifiez le chemin d’accès à un fichier existant, `New-ModuleManifest` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ed94c-247">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="ed94c-248">Le manifeste doit se trouver dans le répertoire du module, et le nom du fichier manifeste doit être le même que le nom du répertoire du module, mais avec une `.psd1` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="ed94c-248">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="ed94c-249">Vous ne pouvez pas utiliser de variables, telles que `$PSHOME` ou `$HOME` , en réponse à une invite pour une valeur de paramètre de **chemin d’accès** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-249">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="ed94c-250">Pour utiliser une variable, incluez le paramètre **Path** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="ed94c-250">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="ed94c-251">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="ed94c-251">-PowerShellHostName</span></span>

<span data-ttu-id="ed94c-252">Spécifie le nom du programme hôte PowerShell requis par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-252">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="ed94c-253">Entrez le nom du programme hôte, par exemple **Windows PowerShell ISE hôte** ou **ConsoleHost**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-253">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost**.</span></span> <span data-ttu-id="ed94c-254">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-254">Wildcards aren't permitted.</span></span>

<span data-ttu-id="ed94c-255">Pour rechercher le nom d’un programme hôte, dans le programme, tapez `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="ed94c-255">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="ed94c-256">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="ed94c-256">-PowerShellHostVersion</span></span>

<span data-ttu-id="ed94c-257">Spécifie la version minimale du programme hôte PowerShell qui fonctionne avec le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-257">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="ed94c-258">Entrez un numéro de version, par exemple 1.1.</span><span class="sxs-lookup"><span data-stu-id="ed94c-258">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="ed94c-259">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="ed94c-259">-PowerShellVersion</span></span>

<span data-ttu-id="ed94c-260">Spécifie la version minimale de PowerShell qui fonctionne avec ce module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-260">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="ed94c-261">Par exemple, vous pouvez entrer 1,0, 2,0 ou 3,0 comme valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="ed94c-261">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span> <span data-ttu-id="ed94c-262">Elle doit être au format X. X.</span><span class="sxs-lookup"><span data-stu-id="ed94c-262">It must be in an X.X format.</span></span> <span data-ttu-id="ed94c-263">Par exemple, si vous envoyez `5` , PowerShell génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="ed94c-263">For example, if you submit `5`, PowerShell will throw an error.</span></span>

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

### <span data-ttu-id="ed94c-264">-Version préliminaire</span><span class="sxs-lookup"><span data-stu-id="ed94c-264">-Prerelease</span></span>

<span data-ttu-id="ed94c-265">Chaîne de version préliminaire de ce module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-265">Prerelease string of this module.</span></span> <span data-ttu-id="ed94c-266">L’ajout d’une chaîne de préversion identifie le module comme une version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="ed94c-266">Adding a Prerelease string identifies the module as a prerelease version.</span></span> <span data-ttu-id="ed94c-267">Lorsque le module est publié dans le PowerShell Gallery, ces données sont utilisées pour identifier les packages de version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="ed94c-267">When the module is published to the PowerShell Gallery, this data is used to identify prerelease packages.</span></span> <span data-ttu-id="ed94c-268">Pour acquérir des packages de version préliminaire à partir de la Galerie, vous devez utiliser le paramètre **AllowPrerelease** avec les commandes PowerShellGet `Find-Module` ,, `Install-Module` `Update-Module` et `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="ed94c-268">To acquire prerelease packages from the Gallery, you must use the **AllowPrerelease** parameter with the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span>

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

### <span data-ttu-id="ed94c-269">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="ed94c-269">-PrivateData</span></span>

<span data-ttu-id="ed94c-270">Spécifie les données qui sont passées au module lors de son importation.</span><span class="sxs-lookup"><span data-stu-id="ed94c-270">Specifies data that is passed to the module when it's imported.</span></span>

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

### <span data-ttu-id="ed94c-271">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="ed94c-271">-ProcessorArchitecture</span></span>

<span data-ttu-id="ed94c-272">Spécifie l'architecture de processeur dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="ed94c-272">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="ed94c-273">Les valeurs valides sont x86, AMD64, IA64, MSIL et None (inconnu ou non spécifié).</span><span class="sxs-lookup"><span data-stu-id="ed94c-273">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

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

### <span data-ttu-id="ed94c-274">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="ed94c-274">-ProjectUri</span></span>

<span data-ttu-id="ed94c-275">Spécifie l’URL d’une page Web sur ce projet.</span><span class="sxs-lookup"><span data-stu-id="ed94c-275">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="ed94c-276">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="ed94c-276">-ReleaseNotes</span></span>

<span data-ttu-id="ed94c-277">Spécifie des notes de publication.</span><span class="sxs-lookup"><span data-stu-id="ed94c-277">Specifies release notes.</span></span>

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

### <span data-ttu-id="ed94c-278">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="ed94c-278">-RequiredAssemblies</span></span>

<span data-ttu-id="ed94c-279">Spécifie les fichiers d’assembly ( `.dll` ) dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="ed94c-279">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="ed94c-280">Entrez les noms de fichiers d'assembly.</span><span class="sxs-lookup"><span data-stu-id="ed94c-280">Enter the assembly file names.</span></span>
<span data-ttu-id="ed94c-281">PowerShell charge les assemblys spécifiés avant de mettre à jour des types ou des formats, d’importer des modules imbriqués ou d’importer le fichier de module spécifié dans la valeur de la clé **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-281">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="ed94c-282">Utilisez ce paramètre pour répertorier tous les assemblys dont le module a besoin, y compris les assemblys qui doivent être chargés pour mettre à jour les fichiers de mise en forme ou de type répertoriés dans les clés **FormatsToProcess** ou **TypesToProcess**, même si ces assemblys sont également répertoriés en tant que modules binaires dans la clé **NestedModules**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-282">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="ed94c-283">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="ed94c-283">-RequiredModules</span></span>

<span data-ttu-id="ed94c-284">Spécifie les modules qui doivent être dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="ed94c-284">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="ed94c-285">Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="ed94c-285">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="ed94c-286">Si les modules requis ne sont pas disponibles, la `Import-Module` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="ed94c-286">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="ed94c-287">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-287">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="ed94c-288">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="ed94c-288">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="ed94c-289">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="ed94c-289">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="ed94c-290">Dans PowerShell 2,0, `Import-Module` n’importe pas automatiquement les modules requis.</span><span class="sxs-lookup"><span data-stu-id="ed94c-290">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="ed94c-291">Elle vérifie simplement que les modules obligatoires se trouvent dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="ed94c-291">It just verifies that the required modules are in the global session state.</span></span>

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

### <span data-ttu-id="ed94c-292">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="ed94c-292">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="ed94c-293">Indicateur qui spécifie si le module requiert une acceptation explicite de l’utilisateur pour l’installation, la mise à jour, orsave.</span><span class="sxs-lookup"><span data-stu-id="ed94c-293">Flag to indicate whether the module requires explicit user acceptance for install, update, orsave.</span></span>

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

### <span data-ttu-id="ed94c-294">-RootModule</span><span class="sxs-lookup"><span data-stu-id="ed94c-294">-RootModule</span></span>

<span data-ttu-id="ed94c-295">Spécifie le fichier principal ou racine du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-295">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="ed94c-296">Entrez le nom de fichier d’un script ( `.ps1` ), d’un module de script ( `.psm1` ), d’un manifeste de module ( `.psd1` ), d’un assembly ( `.dll` ), d’un fichier XML de définition d’applet de commande ( `.cdxml` ) ou d’un flux de travail ( `.xaml` ).</span><span class="sxs-lookup"><span data-stu-id="ed94c-296">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="ed94c-297">Quand le module est importé, les membres exportés à partir du fichier de module racine sont importés dans l'état de session de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="ed94c-297">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="ed94c-298">Si un module a un fichier manifeste et qu’aucun fichier racine n’a été désigné dans la clé **RootModule** , le manifeste devient le fichier primaire pour le module et le module devient un module de manifeste (ModuleType = manifest).</span><span class="sxs-lookup"><span data-stu-id="ed94c-298">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="ed94c-299">Pour exporter des membres à partir de `.psm1` `.dll` fichiers ou dans un module qui a un manifeste, les noms de ces fichiers doivent être spécifiés dans les valeurs des clés **RootModule** ou **NestedModules** dans le manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-299">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="ed94c-300">Dans le cas contraire, leurs membres ne sont pas exportés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-300">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="ed94c-301">Dans PowerShell 2,0, cette clé était appelée **ModuleToProcess**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-301">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span> <span data-ttu-id="ed94c-302">Vous pouvez utiliser le nom du paramètre **RootModule** ou son alias **ModuleToProcess** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-302">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

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

### <span data-ttu-id="ed94c-303">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="ed94c-303">-ScriptsToProcess</span></span>

<span data-ttu-id="ed94c-304">Spécifie les fichiers de script ( `.ps1` ) qui s’exécutent dans l’état de session de l’appelant lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-304">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="ed94c-305">Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de connexion.</span><span class="sxs-lookup"><span data-stu-id="ed94c-305">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="ed94c-306">Pour spécifier les scripts qui s'exécutent dans l'état de session du module, utilisez la clé **NestedModules**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-306">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="ed94c-307">-Tags</span><span class="sxs-lookup"><span data-stu-id="ed94c-307">-Tags</span></span>

<span data-ttu-id="ed94c-308">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="ed94c-308">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="ed94c-309">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="ed94c-309">-TypesToProcess</span></span>

<span data-ttu-id="ed94c-310">Spécifie les fichiers de type ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-310">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="ed94c-311">Lorsque vous importez le module, PowerShell exécute l' `Update-TypeData` applet de commande avec les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-311">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="ed94c-312">Étant donné que les fichiers de type ne sont pas étendus, ils affectent tous les États de session de la session.</span><span class="sxs-lookup"><span data-stu-id="ed94c-312">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="ed94c-313">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="ed94c-313">-VariablesToExport</span></span>

<span data-ttu-id="ed94c-314">Spécifie les variables exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-314">Specifies the variables that the module exports.</span></span> <span data-ttu-id="ed94c-315">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ed94c-315">Wildcards are permitted.</span></span>

<span data-ttu-id="ed94c-316">Vous pouvez utiliser ce paramètre pour limiter les variables exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-316">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="ed94c-317">Elle peut supprimer des variables de la liste des variables exportées, mais elle ne peut pas ajouter de variables à la liste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-317">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="ed94c-318">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **VariablesToExport** avec `*` la valeur (All), ce qui signifie que toutes les variables définies dans le module sont exportées par le manifeste.</span><span class="sxs-lookup"><span data-stu-id="ed94c-318">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="ed94c-319">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ed94c-319">-Confirm</span></span>

<span data-ttu-id="ed94c-320">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ed94c-320">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ed94c-321">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ed94c-321">-WhatIf</span></span>

<span data-ttu-id="ed94c-322">Montre ce qui se passe si `New-ModuleManifest` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ed94c-322">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="ed94c-323">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ed94c-323">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ed94c-324">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="ed94c-324">-ClrVersion</span></span>

<span data-ttu-id="ed94c-325">Spécifie la version minimale du Common Language Runtime (CLR) de Microsoft .NET Framework dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="ed94c-325">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="ed94c-326">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ed94c-326">CommonParameters</span></span>
<span data-ttu-id="ed94c-327">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ed94c-327">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ed94c-328">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ed94c-328">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ed94c-329">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ed94c-329">INPUTS</span></span>

### <span data-ttu-id="ed94c-330">None</span><span class="sxs-lookup"><span data-stu-id="ed94c-330">None</span></span>

<span data-ttu-id="ed94c-331">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ed94c-331">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ed94c-332">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ed94c-332">OUTPUTS</span></span>

### <span data-ttu-id="ed94c-333">Aucune ou System.String</span><span class="sxs-lookup"><span data-stu-id="ed94c-333">None or System.String</span></span>

<span data-ttu-id="ed94c-334">Par défaut, `New-ModuleManifest` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="ed94c-334">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="ed94c-335">Toutefois, si vous utilisez le paramètre **PassThru** , il génère un objet **System. String** qui représente le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-335">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="ed94c-336">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ed94c-336">NOTES</span></span>

<span data-ttu-id="ed94c-337">`New-ModuleManifest` l’exécution sur des plateformes Windows et non Windows crée des fichiers de manifeste de module ( `.psd1` ) encodés en tant que **UTF8NoBOM**.</span><span class="sxs-lookup"><span data-stu-id="ed94c-337">`New-ModuleManifest` running on Windows and non-Windows platforms creates module manifest (`.psd1`) files encoded as **UTF8NoBOM**.</span></span>

<span data-ttu-id="ed94c-338">Les manifestes de module sont généralement facultatifs.</span><span class="sxs-lookup"><span data-stu-id="ed94c-338">Module manifests are usually optional.</span></span> <span data-ttu-id="ed94c-339">Toutefois, un manifeste de module est nécessaire pour exporter un assembly installé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="ed94c-339">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="ed94c-340">Pour ajouter ou modifier des fichiers dans le `$pshome\Modules` répertoire, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="ed94c-340">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

> [!NOTE]
> <span data-ttu-id="ed94c-341">À compter de PowerShell 6,2, PowerShell tente de charger tous les fichiers DLL listés dans la propriété **filelist** du manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-341">Beginning in PowerShell 6.2, PowerShell attempts to load all the DLL files listed in **FileList** property of the module manifest.</span></span> <span data-ttu-id="ed94c-342">Le chargement des DLL natives dans la **filelist** échoue dans le processus et l’erreur est ignorée.</span><span class="sxs-lookup"><span data-stu-id="ed94c-342">Native DLLs is in the **FileList** fail to load in the process and the error is ignored.</span></span> <span data-ttu-id="ed94c-343">Toutes les DLL managées sont chargées dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ed94c-343">All managed DLLs are loaded in the process.</span></span> <span data-ttu-id="ed94c-344">Ce comportement a été supprimé dans PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="ed94c-344">This behavior was removed in PowerShell 7.1.</span></span>

<span data-ttu-id="ed94c-345">Dans PowerShell 2,0, de nombreux paramètres de `New-ModuleManifest` étaient obligatoires, même s’ils n’étaient pas requis dans un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-345">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="ed94c-346">À compter de PowerShell 3,0, seul le paramètre **path** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ed94c-346">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="ed94c-347">Une session est une instance de l’environnement d’exécution de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed94c-347">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="ed94c-348">Une session peut avoir un ou plusieurs états de session.</span><span class="sxs-lookup"><span data-stu-id="ed94c-348">A session can have one or more session states.</span></span> <span data-ttu-id="ed94c-349">Par défaut, une session possède uniquement un état de session global, mais chaque module importé a son propre état de session.</span><span class="sxs-lookup"><span data-stu-id="ed94c-349">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="ed94c-350">Les états de session permettent aux commandes de s'exécuter dans un module sans affecter l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="ed94c-350">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="ed94c-351">L’état de session de l’appelant est l’état de session dans lequel un module est importé.</span><span class="sxs-lookup"><span data-stu-id="ed94c-351">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="ed94c-352">En règle générale, il fait référence à l’état de session global, mais lorsqu’un module importe des modules imbriqués, l’appelant est le module et l’état de session de l’appelant est l’état de session du module.</span><span class="sxs-lookup"><span data-stu-id="ed94c-352">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="ed94c-353">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ed94c-353">RELATED LINKS</span></span>

[<span data-ttu-id="ed94c-354">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="ed94c-354">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="ed94c-355">Get-Module</span><span class="sxs-lookup"><span data-stu-id="ed94c-355">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="ed94c-356">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="ed94c-356">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="ed94c-357">New-Module</span><span class="sxs-lookup"><span data-stu-id="ed94c-357">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="ed94c-358">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="ed94c-358">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="ed94c-359">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="ed94c-359">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="ed94c-360">about_Modules</span><span class="sxs-lookup"><span data-stu-id="ed94c-360">about_Modules</span></span>](./About/about_Modules.md)
