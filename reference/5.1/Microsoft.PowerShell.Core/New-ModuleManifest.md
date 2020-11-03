---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 50a3d85b3d598653a03bc6bf8e82c249bba42759
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202273"
---
# <span data-ttu-id="98e2f-103">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="98e2f-103">New-ModuleManifest</span></span>

## <span data-ttu-id="98e2f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="98e2f-104">SYNOPSIS</span></span>
<span data-ttu-id="98e2f-105">Crée un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-105">Creates a new module manifest.</span></span>

## <span data-ttu-id="98e2f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="98e2f-106">SYNTAX</span></span>

### <span data-ttu-id="98e2f-107">Tous</span><span class="sxs-lookup"><span data-stu-id="98e2f-107">All</span></span>

```
New-ModuleManifest [-Path] <string> [-NestedModules <Object[]>] [-Guid <guid>] [-Author <string>]
 [-CompanyName <string>] [-Copyright <string>] [-RootModule <string>] [-ModuleVersion <version>]
 [-Description <string>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-PowerShellVersion <version>] [-ClrVersion <version>] [-DotNetFrameworkVersion <version>]
 [-PowerShellHostName <string>] [-PowerShellHostVersion <version>] [-RequiredModules <Object[]>]
 [-TypesToProcess <string[]>] [-FormatsToProcess <string[]>] [-ScriptsToProcess <string[]>]
 [-RequiredAssemblies <string[]>] [-FileList <string[]>] [-ModuleList <Object[]>]
 [-FunctionsToExport <string[]>] [-AliasesToExport <string[]>] [-VariablesToExport <string[]>]
 [-CmdletsToExport <string[]>] [-DscResourcesToExport <string[]>] [-CompatiblePSEditions <string[]>]
 [-PrivateData <Object>] [-Tags <string[]>] [-ProjectUri <uri>] [-LicenseUri <uri>] [-IconUri <uri>]
 [-ReleaseNotes <string>] [-HelpInfoUri <string>] [-PassThru] [-DefaultCommandPrefix <string>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="98e2f-108">Description</span><span class="sxs-lookup"><span data-stu-id="98e2f-108">DESCRIPTION</span></span>

<span data-ttu-id="98e2f-109">L' `New-ModuleManifest` applet de commande crée un fichier manifeste de module ( `.psd1` ), remplit ses valeurs et enregistre le fichier manifeste dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="98e2f-109">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="98e2f-110">Les auteurs de modules peuvent utiliser cette applet de commande afin de créer un manifeste pour leur module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-110">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="98e2f-111">Un manifeste de module est un `.psd1` fichier qui contient une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="98e2f-111">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="98e2f-112">Les clés et valeurs de la table de hachage décrivent le contenu et les attributs du module, définissent les conditions préalables, et déterminent la façon dont les composants sont traités.</span><span class="sxs-lookup"><span data-stu-id="98e2f-112">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="98e2f-113">Les manifestes ne sont pas nécessaires pour un module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-113">Manifests aren't required for a module.</span></span>

<span data-ttu-id="98e2f-114">`New-ModuleManifest` crée un manifeste qui contient toutes les clés de manifeste couramment utilisées, vous pouvez donc utiliser la sortie par défaut comme modèle de manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-114">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="98e2f-115">Pour ajouter ou modifier des valeurs, ou pour ajouter des clés de module que cette applet de commande n’ajoute pas, ouvrez le fichier résultant dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="98e2f-115">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="98e2f-116">Chaque paramètre, à l’exception de **path** et **PassThru** , crée une clé de manifeste de module et sa valeur.</span><span class="sxs-lookup"><span data-stu-id="98e2f-116">Each parameter, except for **Path** and **PassThru** , creates a module manifest key and its value.</span></span>
<span data-ttu-id="98e2f-117">Dans un manifeste de module, seule la clé **ModuleVersion** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="98e2f-117">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="98e2f-118">À moins qu’il ne soit spécifié dans la description du paramètre, si vous omettez un paramètre de la commande, `New-ModuleManifest` crée une chaîne de commentaire pour la valeur associée qui n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="98e2f-118">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="98e2f-119">Dans PowerShell 2,0, `New-ModuleManifest` vous invite à entrer les valeurs des paramètres couramment utilisés qui ne sont pas spécifiés dans la commande, en plus des valeurs de paramètre requises.</span><span class="sxs-lookup"><span data-stu-id="98e2f-119">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="98e2f-120">À compter de PowerShell 3,0, `New-ModuleManifest` invites lorsque les valeurs de paramètres requises ne sont pas spécifiées.</span><span class="sxs-lookup"><span data-stu-id="98e2f-120">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="98e2f-121">Si vous envisagez de publier votre module dans le PowerShell Gallery, le manifeste doit contenir des valeurs pour certaines propriétés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-121">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="98e2f-122">Pour plus d’informations, consultez [métadonnées requises pour les éléments publiés dans le PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) dans la documentation de la Galerie.</span><span class="sxs-lookup"><span data-stu-id="98e2f-122">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="98e2f-123">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="98e2f-123">EXAMPLES</span></span>

### <span data-ttu-id="98e2f-124">Exemple 1 : créer un manifeste de module</span><span class="sxs-lookup"><span data-stu-id="98e2f-124">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="98e2f-125">Cet exemple crée un nouveau manifeste de module dans le fichier spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-125">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="98e2f-126">Le paramètre **PassThru** envoie la sortie au pipeline et au fichier.</span><span class="sxs-lookup"><span data-stu-id="98e2f-126">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="98e2f-127">La sortie indique les valeurs par défaut de toutes les clés du manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-127">The output shows the default values of all keys in the manifest.</span></span>

```powershell
New-ModuleManifest -Path C:\ps-test\Test-Module\Test-Module.psd1 -PassThru
```

```Output
#
# Module manifest for module 'Test-Module'
#
# Generated by: ContosoAdmin
#
# Generated on: 1/22/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = '47179120-0bcb-4f14-8d80-f4560107f85c'

# Author of this module
Author = 'ContosoAdmin'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 ContosoAdmin. All rights reserved.'

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

### <span data-ttu-id="98e2f-128">Exemple 2 : créer un nouveau manifeste avec des paramètres préremplis</span><span class="sxs-lookup"><span data-stu-id="98e2f-128">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="98e2f-129">Cet exemple crée un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-129">This example creates a new module manifest.</span></span> <span data-ttu-id="98e2f-130">Elle utilise les paramètres **PowerShellVersion** et **AliasesToExport** pour ajouter des valeurs aux clés de manifeste correspondantes.</span><span class="sxs-lookup"><span data-stu-id="98e2f-130">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="98e2f-131">Exemple 3 : créer un manifeste qui requiert d’autres modules</span><span class="sxs-lookup"><span data-stu-id="98e2f-131">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="98e2f-132">Cet exemple utilise un format de chaîne pour spécifier le nom du module **BitsTransfer** et le format de la table de hachage pour spécifier le nom, un **GUID** et une version du module **PSScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-132">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID** , and a version of the **PSScheduledJob** module.</span></span>

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

<span data-ttu-id="98e2f-133">Cet exemple montre comment utiliser les formats de table de hachage et de chaîne du paramètre **ModuleList** , **RequiredModules** et **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-133">This example shows how to use the string and hash table formats of the **ModuleList** , **RequiredModules** , and **NestedModules** parameter.</span></span> <span data-ttu-id="98e2f-134">Vous pouvez combiner des chaînes et des tables de hachage dans la même valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="98e2f-134">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="98e2f-135">Exemple 4 : créer un manifeste qui prend en charge l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="98e2f-135">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="98e2f-136">Cet exemple utilise le paramètre **HelpInfoUri** pour créer une clé **HelpInfoUri** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-136">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="98e2f-137">La valeur du paramètre et de la clé doit commencer par **http** ou **https** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-137">The value of the parameter and the key must begin with **http** or **https** .</span></span> <span data-ttu-id="98e2f-138">Cette valeur indique au système d'aide actualisable où trouver le fichier XML d'informations HelpInfo sur l'aide actualisable du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-138">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="98e2f-139">Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="98e2f-139">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="98e2f-140">Pour plus d’informations sur le fichier XML HelpInfo, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="98e2f-140">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="98e2f-141">Exemple 5 : obtention d’informations sur le module</span><span class="sxs-lookup"><span data-stu-id="98e2f-141">Example 5 - Getting module information</span></span>

<span data-ttu-id="98e2f-142">Cet exemple montre comment obtenir les valeurs de configuration d’un module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-142">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="98e2f-143">Les valeurs du manifeste de module sont reflétées dans les valeurs des propriétés de l’objet de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-143">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="98e2f-144">L' `Get-Module` applet de commande est utilisée pour récupérer le module **Microsoft. PowerShell. Diagnostics** à l’aide du paramètre **List** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-144">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="98e2f-145">La commande envoie le module à l' `Format-List` applet de commande pour afficher toutes les propriétés et valeurs de l’objet de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-145">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

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

## <span data-ttu-id="98e2f-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="98e2f-146">PARAMETERS</span></span>

### <span data-ttu-id="98e2f-147">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="98e2f-147">-AliasesToExport</span></span>

<span data-ttu-id="98e2f-148">Spécifie les alias exportés par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-148">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="98e2f-149">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-149">Wildcards are permitted.</span></span>

<span data-ttu-id="98e2f-150">Vous pouvez utiliser ce paramètre pour limiter les alias exportés par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-150">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="98e2f-151">Elle peut supprimer des alias de la liste des alias exportés, mais elle ne peut pas ajouter d’alias à la liste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-151">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="98e2f-152">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **AliasesToExport** avec `*` la valeur (All), ce qui signifie que tous les alias définis dans le module sont exportés par le manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-152">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="98e2f-153">-Auteur</span><span class="sxs-lookup"><span data-stu-id="98e2f-153">-Author</span></span>

<span data-ttu-id="98e2f-154">Spécifie l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-154">Specifies the module author.</span></span>

<span data-ttu-id="98e2f-155">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé d' **auteur** avec le nom de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="98e2f-155">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

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

### <span data-ttu-id="98e2f-156">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="98e2f-156">-ClrVersion</span></span>

<span data-ttu-id="98e2f-157">Spécifie la version minimale du Common Language Runtime (CLR) de Microsoft .NET Framework dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="98e2f-157">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="98e2f-158">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="98e2f-158">-CmdletsToExport</span></span>

<span data-ttu-id="98e2f-159">Spécifie les applets de commande exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-159">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="98e2f-160">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-160">Wildcards are permitted.</span></span>

<span data-ttu-id="98e2f-161">Vous pouvez utiliser ce paramètre pour limiter les applets de commande exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-161">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="98e2f-162">Elle peut supprimer des applets de commande de la liste des applets de commande exportées, mais elle ne peut pas ajouter d’applets de commande à la liste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-162">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="98e2f-163">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **CmdletsToExport** avec `*` la valeur (All), ce qui signifie que toutes les applets de commande définies dans le module sont exportées par le manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-163">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="98e2f-164">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="98e2f-164">-CompanyName</span></span>

<span data-ttu-id="98e2f-165">Identifie la société ou le fournisseur qui a créé le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-165">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="98e2f-166">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **CompanyName** avec la valeur « Unknown ».</span><span class="sxs-lookup"><span data-stu-id="98e2f-166">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

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

### <span data-ttu-id="98e2f-167">-Confirm</span><span class="sxs-lookup"><span data-stu-id="98e2f-167">-Confirm</span></span>

<span data-ttu-id="98e2f-168">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98e2f-168">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="98e2f-169">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="98e2f-169">-CompatiblePSEditions</span></span>

<span data-ttu-id="98e2f-170">Spécifie le des éditions PS compatible du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-170">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="98e2f-171">Pour plus d’informations sur PSEdition, consultez [modules avec des éditions PowerShell compatibles](/powershell/scripting/gallery/concepts/module-psedition-support).</span><span class="sxs-lookup"><span data-stu-id="98e2f-171">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="98e2f-172">-Copyright</span><span class="sxs-lookup"><span data-stu-id="98e2f-172">-Copyright</span></span>

<span data-ttu-id="98e2f-173">Spécifie une déclaration de copyright pour le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-173">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="98e2f-174">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé de **Copyright** avec la valeur `(c) <year> <username>. All rights reserved.` où `<year>` est l’année en cours et `<username>` est la valeur de la clé d' **auteur** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-174">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

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

### <span data-ttu-id="98e2f-175">Description</span><span class="sxs-lookup"><span data-stu-id="98e2f-175">-Description</span></span>

<span data-ttu-id="98e2f-176">Décrit le contenu du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-176">Describes the contents of the module.</span></span>

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

### <span data-ttu-id="98e2f-177">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="98e2f-177">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="98e2f-178">Spécifie la version minimale de Microsoft .NET Framework dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="98e2f-178">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="98e2f-179">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="98e2f-179">-DscResourcesToExport</span></span>

<span data-ttu-id="98e2f-180">Spécifie les ressources de configuration d’état souhaité (DSC) exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-180">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="98e2f-181">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-181">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="98e2f-182">-FileList</span><span class="sxs-lookup"><span data-stu-id="98e2f-182">-FileList</span></span>

<span data-ttu-id="98e2f-183">Spécifie tous les éléments qui sont inclus dans le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-183">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="98e2f-184">Cette clé est conçue pour agir en tant qu'inventaire de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-184">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="98e2f-185">Les fichiers répertoriés dans la clé sont inclus lors de la publication du module, mais les fonctions ne sont pas exportées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="98e2f-185">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

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

### <span data-ttu-id="98e2f-186">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="98e2f-186">-FormatsToProcess</span></span>

<span data-ttu-id="98e2f-187">Spécifie les fichiers de mise en forme ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-187">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="98e2f-188">Lorsque vous importez un module, PowerShell exécute l' `Update-FormatData` applet de commande avec les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-188">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="98e2f-189">Étant donné que les fichiers de mise en forme ne sont pas étendus, ils affectent tous les États de session de la session.</span><span class="sxs-lookup"><span data-stu-id="98e2f-189">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="98e2f-190">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="98e2f-190">-FunctionsToExport</span></span>

<span data-ttu-id="98e2f-191">Spécifie les fonctions exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-191">Specifies the functions that the module exports.</span></span> <span data-ttu-id="98e2f-192">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-192">Wildcards are permitted.</span></span>

<span data-ttu-id="98e2f-193">Vous pouvez utiliser ce paramètre pour limiter les fonctions exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-193">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="98e2f-194">Elle peut supprimer des fonctions de la liste des alias exportés, mais elle ne peut pas ajouter de fonctions à la liste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-194">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="98e2f-195">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **FunctionsToExport** avec `*` la valeur (All), ce qui signifie que toutes les fonctions définies dans le module sont exportées par le manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-195">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="98e2f-196">-Guid</span><span class="sxs-lookup"><span data-stu-id="98e2f-196">-Guid</span></span>

<span data-ttu-id="98e2f-197">Spécifie un identificateur unique pour le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-197">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="98e2f-198">Le **GUID** peut être utilisé pour faire la distinction entre les modules portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="98e2f-198">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="98e2f-199">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **GUID** dans le manifeste et génère un **GUID** pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="98e2f-199">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="98e2f-200">Pour créer un nouveau **GUID** dans PowerShell, tapez `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="98e2f-200">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="98e2f-201">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="98e2f-201">-HelpInfoUri</span></span>

<span data-ttu-id="98e2f-202">Spécifie l’adresse Internet du fichier XML HelpInfo du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-202">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="98e2f-203">Entrez un Uniform Resource Identifier (URI) qui commence par **http** ou **https** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-203">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https** .</span></span>

<span data-ttu-id="98e2f-204">Le fichier XML HelpInfo prend en charge la fonctionnalité d’aide actualisable qui a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="98e2f-204">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="98e2f-205">Il contient des informations sur l'emplacement des fichiers d'aide téléchargeables pour le module, et les numéros de version des fichiers d'aide les plus récents pour chacun des paramètres régionaux pris en charge.</span><span class="sxs-lookup"><span data-stu-id="98e2f-205">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="98e2f-206">Pour plus d’informations sur l’aide actualisable, voir [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="98e2f-206">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="98e2f-207">Pour plus d’informations sur le fichier XML HelpInfo, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="98e2f-207">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="98e2f-208">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="98e2f-208">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="98e2f-209">-IconUri</span><span class="sxs-lookup"><span data-stu-id="98e2f-209">-IconUri</span></span>

<span data-ttu-id="98e2f-210">Spécifie l’URL d’une icône pour le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-210">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="98e2f-211">L’icône spécifiée est affichée sur la page Web de la Galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-211">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="98e2f-212">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="98e2f-212">-LicenseUri</span></span>

<span data-ttu-id="98e2f-213">Spécifie l’URL des termes du contrat de licence pour le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-213">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="98e2f-214">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="98e2f-214">-ModuleList</span></span>

<span data-ttu-id="98e2f-215">Répertorie tous les modules qui sont inclus dans ce module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-215">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="98e2f-216">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-216">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="98e2f-217">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="98e2f-217">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="98e2f-218">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="98e2f-218">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="98e2f-219">Cette clé est conçue pour agir en tant qu'inventaire de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-219">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="98e2f-220">Les modules répertoriés dans la valeur de cette clé ne sont pas traités automatiquement.</span><span class="sxs-lookup"><span data-stu-id="98e2f-220">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="98e2f-221">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="98e2f-221">-ModuleVersion</span></span>

<span data-ttu-id="98e2f-222">Spécifie la version du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-222">Specifies the module's version.</span></span>

<span data-ttu-id="98e2f-223">Ce paramètre n’est pas obligatoire, mais une clé **ModuleVersion** est requise dans le manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-223">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="98e2f-224">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **ModuleVersion** avec une valeur de 1,0.</span><span class="sxs-lookup"><span data-stu-id="98e2f-224">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

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

### <span data-ttu-id="98e2f-225">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="98e2f-225">-NestedModules</span></span>

<span data-ttu-id="98e2f-226">Spécifie les modules de script ( `.psm1` ) et les modules binaires ( `.dll` ) qui sont importés dans l’état de session du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-226">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="98e2f-227">Les fichiers de la clé **NestedModules** s’exécutent dans l’ordre dans lequel ils sont listés dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="98e2f-227">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="98e2f-228">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-228">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="98e2f-229">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="98e2f-229">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="98e2f-230">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="98e2f-230">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="98e2f-231">En règle générale, les modules imbriqués contiennent les commandes dont le module racine a besoin pour son traitement interne.</span><span class="sxs-lookup"><span data-stu-id="98e2f-231">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="98e2f-232">Par défaut, les commandes dans les modules imbriqués sont exportées de l’état de session du module vers l’état de session de l’appelant, mais le module racine peut restreindre les commandes qu’il exporte.</span><span class="sxs-lookup"><span data-stu-id="98e2f-232">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="98e2f-233">Par exemple, à l’aide d’une `Export-ModuleMember` commande.</span><span class="sxs-lookup"><span data-stu-id="98e2f-233">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="98e2f-234">Les modules imbriqués dans l’état de session du module sont disponibles pour le module racine, mais ils ne sont pas retournés par une `Get-Module` commande dans l’état de session de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="98e2f-234">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="98e2f-235">Les scripts ( `.ps1` ) qui sont répertoriés dans la clé **NestedModules** sont exécutés dans l’état de session du module, et non dans l’état de session de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="98e2f-235">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="98e2f-236">Pour exécuter un script dans l'état de session de l'appelant, répertoriez le nom du fichier de script dans la valeur de la clé **ScriptsToProcess** du manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-236">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

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

### <span data-ttu-id="98e2f-237">-PassThru</span><span class="sxs-lookup"><span data-stu-id="98e2f-237">-PassThru</span></span>

<span data-ttu-id="98e2f-238">Écrit le manifeste de module résultant dans la console et crée un `.psd1` fichier.</span><span class="sxs-lookup"><span data-stu-id="98e2f-238">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="98e2f-239">Par défaut, cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="98e2f-239">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="98e2f-240">-Path</span><span class="sxs-lookup"><span data-stu-id="98e2f-240">-Path</span></span>

<span data-ttu-id="98e2f-241">Spécifie le chemin d'accès et le nom de fichier du nouveau manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-241">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="98e2f-242">Entrez un chemin d’accès et un nom de fichier avec une `.psd1` extension de nom de fichier, par exemple `$pshome\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="98e2f-242">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="98e2f-243">Le paramètre **path** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="98e2f-243">The **Path** parameter is required.</span></span>

<span data-ttu-id="98e2f-244">Si vous spécifiez le chemin d’accès à un fichier existant, `New-ModuleManifest` remplace le fichier sans avertissement, sauf si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="98e2f-244">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="98e2f-245">Le manifeste doit se trouver dans le répertoire du module, et le nom du fichier manifeste doit être le même que le nom du répertoire du module, mais avec une `.psd1` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="98e2f-245">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="98e2f-246">Vous ne pouvez pas utiliser de variables, telles que `$PSHOME` ou `$HOME` , en réponse à une invite pour une valeur de paramètre de **chemin d’accès** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-246">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="98e2f-247">Pour utiliser une variable, incluez le paramètre **Path** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="98e2f-247">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="98e2f-248">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="98e2f-248">-PowerShellHostName</span></span>

<span data-ttu-id="98e2f-249">Spécifie le nom du programme hôte PowerShell requis par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-249">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="98e2f-250">Entrez le nom du programme hôte, par exemple **Windows PowerShell ISE hôte** ou **ConsoleHost** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-250">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost** .</span></span> <span data-ttu-id="98e2f-251">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-251">Wildcards aren't permitted.</span></span>

<span data-ttu-id="98e2f-252">Pour rechercher le nom d’un programme hôte, dans le programme, tapez `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="98e2f-252">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="98e2f-253">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="98e2f-253">-PowerShellHostVersion</span></span>

<span data-ttu-id="98e2f-254">Spécifie la version minimale du programme hôte PowerShell qui fonctionne avec le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-254">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="98e2f-255">Entrez un numéro de version, par exemple 1.1.</span><span class="sxs-lookup"><span data-stu-id="98e2f-255">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="98e2f-256">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="98e2f-256">-PowerShellVersion</span></span>

<span data-ttu-id="98e2f-257">Spécifie la version minimale de PowerShell qui fonctionne avec ce module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-257">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="98e2f-258">Par exemple, vous pouvez entrer 1,0, 2,0 ou 3,0 comme valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="98e2f-258">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span>

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

### <span data-ttu-id="98e2f-259">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="98e2f-259">-PrivateData</span></span>

<span data-ttu-id="98e2f-260">Spécifie les données qui sont passées au module lors de son importation.</span><span class="sxs-lookup"><span data-stu-id="98e2f-260">Specifies data that is passed to the module when it's imported.</span></span>

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

### <span data-ttu-id="98e2f-261">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="98e2f-261">-ProcessorArchitecture</span></span>

<span data-ttu-id="98e2f-262">Spécifie l'architecture de processeur dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="98e2f-262">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="98e2f-263">Les valeurs valides sont x86, AMD64, IA64, MSIL et None (inconnu ou non spécifié).</span><span class="sxs-lookup"><span data-stu-id="98e2f-263">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

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

### <span data-ttu-id="98e2f-264">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="98e2f-264">-ProjectUri</span></span>

<span data-ttu-id="98e2f-265">Spécifie l’URL d’une page Web sur ce projet.</span><span class="sxs-lookup"><span data-stu-id="98e2f-265">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="98e2f-266">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="98e2f-266">-ReleaseNotes</span></span>

<span data-ttu-id="98e2f-267">Spécifie des notes de publication.</span><span class="sxs-lookup"><span data-stu-id="98e2f-267">Specifies release notes.</span></span>

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

### <span data-ttu-id="98e2f-268">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="98e2f-268">-RequiredAssemblies</span></span>

<span data-ttu-id="98e2f-269">Spécifie les fichiers d’assembly ( `.dll` ) dont le module a besoin.</span><span class="sxs-lookup"><span data-stu-id="98e2f-269">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="98e2f-270">Entrez les noms de fichiers d'assembly.</span><span class="sxs-lookup"><span data-stu-id="98e2f-270">Enter the assembly file names.</span></span>
<span data-ttu-id="98e2f-271">PowerShell charge les assemblys spécifiés avant de mettre à jour des types ou des formats, d’importer des modules imbriqués ou d’importer le fichier de module spécifié dans la valeur de la clé **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-271">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="98e2f-272">Utilisez ce paramètre pour répertorier tous les assemblys dont le module a besoin, y compris les assemblys qui doivent être chargés pour mettre à jour les fichiers de mise en forme ou de type répertoriés dans les clés **FormatsToProcess** ou **TypesToProcess** , même si ces assemblys sont également répertoriés en tant que modules binaires dans la clé **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-272">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="98e2f-273">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="98e2f-273">-RequiredModules</span></span>

<span data-ttu-id="98e2f-274">Spécifie les modules qui doivent être dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="98e2f-274">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="98e2f-275">Si les modules requis ne sont pas dans l’état de session global, PowerShell les importe.</span><span class="sxs-lookup"><span data-stu-id="98e2f-275">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="98e2f-276">Si les modules requis ne sont pas disponibles, la `Import-Module` commande échoue.</span><span class="sxs-lookup"><span data-stu-id="98e2f-276">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="98e2f-277">Entrez le nom de chaque module sous la forme d'une chaîne ou d'une table de hachage avec les clés **ModuleName** et **ModuleVersion** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-277">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="98e2f-278">La table de hachage peut également avoir une clé **GUID** facultative.</span><span class="sxs-lookup"><span data-stu-id="98e2f-278">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="98e2f-279">Vous pouvez combiner des chaînes et des tables de hachage dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="98e2f-279">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="98e2f-280">Dans PowerShell 2,0, `Import-Module` n’importe pas automatiquement les modules requis.</span><span class="sxs-lookup"><span data-stu-id="98e2f-280">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="98e2f-281">Elle vérifie simplement que les modules obligatoires se trouvent dans l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="98e2f-281">It just verifies that the required modules are in the global session state.</span></span>

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

### <span data-ttu-id="98e2f-282">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="98e2f-282">-ScriptsToProcess</span></span>

<span data-ttu-id="98e2f-283">Spécifie les fichiers de script ( `.ps1` ) qui s’exécutent dans l’état de session de l’appelant lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-283">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="98e2f-284">Vous pouvez utiliser ces scripts pour préparer un environnement, tout comme vous pouvez utiliser un script de connexion.</span><span class="sxs-lookup"><span data-stu-id="98e2f-284">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="98e2f-285">Pour spécifier les scripts qui s'exécutent dans l'état de session du module, utilisez la clé **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-285">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="98e2f-286">-Tags</span><span class="sxs-lookup"><span data-stu-id="98e2f-286">-Tags</span></span>

<span data-ttu-id="98e2f-287">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="98e2f-287">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="98e2f-288">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="98e2f-288">-TypesToProcess</span></span>

<span data-ttu-id="98e2f-289">Spécifie les fichiers de type ( `.ps1xml` ) qui s’exécutent lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-289">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="98e2f-290">Lorsque vous importez le module, PowerShell exécute l' `Update-TypeData` applet de commande avec les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-290">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="98e2f-291">Étant donné que les fichiers de type ne sont pas étendus, ils affectent tous les États de session de la session.</span><span class="sxs-lookup"><span data-stu-id="98e2f-291">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="98e2f-292">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="98e2f-292">-VariablesToExport</span></span>

<span data-ttu-id="98e2f-293">Spécifie les variables exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-293">Specifies the variables that the module exports.</span></span> <span data-ttu-id="98e2f-294">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-294">Wildcards are permitted.</span></span>

<span data-ttu-id="98e2f-295">Vous pouvez utiliser ce paramètre pour limiter les variables exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-295">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="98e2f-296">Elle peut supprimer des variables de la liste des variables exportées, mais elle ne peut pas ajouter de variables à la liste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-296">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="98e2f-297">Si vous omettez ce paramètre, `New-ModuleManifest` crée une clé **VariablesToExport** avec `*` la valeur (All), ce qui signifie que toutes les variables définies dans le module sont exportées par le manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-297">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="98e2f-298">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="98e2f-298">-DefaultCommandPrefix</span></span>

<span data-ttu-id="98e2f-299">Spécifie un préfixe qui est ajouté aux noms de toutes les commandes du module lorsqu’elles sont importées dans une session.</span><span class="sxs-lookup"><span data-stu-id="98e2f-299">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="98e2f-300">Entrez une chaîne de préfixe.</span><span class="sxs-lookup"><span data-stu-id="98e2f-300">Enter a prefix string.</span></span> <span data-ttu-id="98e2f-301">Les préfixes empêchent les conflits de noms de commande dans la session d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="98e2f-301">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="98e2f-302">Les utilisateurs du module peuvent remplacer ce préfixe en spécifiant le paramètre **prefix** de l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="98e2f-302">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="98e2f-303">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="98e2f-303">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="98e2f-304">-RootModule</span><span class="sxs-lookup"><span data-stu-id="98e2f-304">-RootModule</span></span>

<span data-ttu-id="98e2f-305">Spécifie le fichier principal ou racine du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-305">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="98e2f-306">Entrez le nom de fichier d’un script ( `.ps1` ), d’un module de script ( `.psm1` ), d’un manifeste de module ( `.psd1` ), d’un assembly ( `.dll` ), d’un fichier XML de définition d’applet de commande ( `.cdxml` ) ou d’un flux de travail ( `.xaml` ).</span><span class="sxs-lookup"><span data-stu-id="98e2f-306">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="98e2f-307">Quand le module est importé, les membres exportés à partir du fichier de module racine sont importés dans l'état de session de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="98e2f-307">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="98e2f-308">Si un module a un fichier manifeste et qu’aucun fichier racine n’a été désigné dans la clé **RootModule** , le manifeste devient le fichier primaire pour le module et le module devient un module de manifeste (ModuleType = manifest).</span><span class="sxs-lookup"><span data-stu-id="98e2f-308">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="98e2f-309">Pour exporter des membres à partir de `.psm1` `.dll` fichiers ou dans un module qui a un manifeste, les noms de ces fichiers doivent être spécifiés dans les valeurs des clés **RootModule** ou **NestedModules** dans le manifeste.</span><span class="sxs-lookup"><span data-stu-id="98e2f-309">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="98e2f-310">Dans le cas contraire, leurs membres ne sont pas exportés.</span><span class="sxs-lookup"><span data-stu-id="98e2f-310">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="98e2f-311">Dans PowerShell 2,0, cette clé était appelée **ModuleToProcess** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-311">In PowerShell 2.0, this key was called **ModuleToProcess** .</span></span> <span data-ttu-id="98e2f-312">Vous pouvez utiliser le nom du paramètre **RootModule** ou son alias **ModuleToProcess** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-312">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

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

### <span data-ttu-id="98e2f-313">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="98e2f-313">-WhatIf</span></span>

<span data-ttu-id="98e2f-314">Montre ce qui se passe si `New-ModuleManifest` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="98e2f-314">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="98e2f-315">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="98e2f-315">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="98e2f-316">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98e2f-316">CommonParameters</span></span>

<span data-ttu-id="98e2f-317">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="98e2f-317">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98e2f-318">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="98e2f-318">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98e2f-319">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="98e2f-319">INPUTS</span></span>

### <span data-ttu-id="98e2f-320">Aucun</span><span class="sxs-lookup"><span data-stu-id="98e2f-320">None</span></span>

<span data-ttu-id="98e2f-321">Vous ne pouvez pas diriger d’entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98e2f-321">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="98e2f-322">SORTIES</span><span class="sxs-lookup"><span data-stu-id="98e2f-322">OUTPUTS</span></span>

### <span data-ttu-id="98e2f-323">Aucune ou System.String</span><span class="sxs-lookup"><span data-stu-id="98e2f-323">None or System.String</span></span>

<span data-ttu-id="98e2f-324">Par défaut, `New-ModuleManifest` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="98e2f-324">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="98e2f-325">Toutefois, si vous utilisez le paramètre **PassThru** , il génère un objet **System. String** qui représente le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-325">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="98e2f-326">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="98e2f-326">NOTES</span></span>

<span data-ttu-id="98e2f-327">`New-ModuleManifest` crée des fichiers de manifeste de module ( `.psd1` ) encodés en tant que **UTF16** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-327">`New-ModuleManifest` creates module manifest (`.psd1`) files encoded as **UTF16** .</span></span>

<span data-ttu-id="98e2f-328">Les manifestes de module sont généralement facultatifs.</span><span class="sxs-lookup"><span data-stu-id="98e2f-328">Module manifests are usually optional.</span></span> <span data-ttu-id="98e2f-329">Toutefois, un manifeste de module est nécessaire pour exporter un assembly installé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="98e2f-329">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="98e2f-330">Pour ajouter ou modifier des fichiers dans le `$pshome\Modules` répertoire, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="98e2f-330">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="98e2f-331">Dans PowerShell 2,0, de nombreux paramètres de `New-ModuleManifest` étaient obligatoires, même s’ils n’étaient pas requis dans un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-331">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="98e2f-332">À compter de PowerShell 3,0, seul le paramètre **path** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="98e2f-332">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="98e2f-333">Une session est une instance de l’environnement d’exécution de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98e2f-333">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="98e2f-334">Une session peut avoir un ou plusieurs états de session.</span><span class="sxs-lookup"><span data-stu-id="98e2f-334">A session can have one or more session states.</span></span> <span data-ttu-id="98e2f-335">Par défaut, une session possède uniquement un état de session global, mais chaque module importé a son propre état de session.</span><span class="sxs-lookup"><span data-stu-id="98e2f-335">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="98e2f-336">Les états de session permettent aux commandes de s'exécuter dans un module sans affecter l'état de session global.</span><span class="sxs-lookup"><span data-stu-id="98e2f-336">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="98e2f-337">L’état de session de l’appelant est l’état de session dans lequel un module est importé.</span><span class="sxs-lookup"><span data-stu-id="98e2f-337">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="98e2f-338">En règle générale, il fait référence à l’état de session global, mais lorsqu’un module importe des modules imbriqués, l’appelant est le module et l’état de session de l’appelant est l’état de session du module.</span><span class="sxs-lookup"><span data-stu-id="98e2f-338">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="98e2f-339">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="98e2f-339">RELATED LINKS</span></span>

[<span data-ttu-id="98e2f-340">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="98e2f-340">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="98e2f-341">Get-Module</span><span class="sxs-lookup"><span data-stu-id="98e2f-341">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="98e2f-342">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="98e2f-342">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="98e2f-343">New-Module</span><span class="sxs-lookup"><span data-stu-id="98e2f-343">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="98e2f-344">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="98e2f-344">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="98e2f-345">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="98e2f-345">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="98e2f-346">about_Modules</span><span class="sxs-lookup"><span data-stu-id="98e2f-346">about_Modules</span></span>](./About/about_Modules.md)
