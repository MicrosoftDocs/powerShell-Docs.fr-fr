---
description: Décrit comment vous pouvez utiliser des classes pour développer dans PowerShell avec la configuration d’état souhaité (DSC).
keywords: powershell,applet de commande
Locale: en-US
ms.date: 1/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des classes et de DSC
ms.openlocfilehash: b66129aa8479013e6397c3e60798a5d2b1929f6b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207805"
---
# <a name="about-classes-and-desired-state-configuration"></a><span data-ttu-id="b58b9-104">À propos des classes et de la configuration d’état souhaité</span><span class="sxs-lookup"><span data-stu-id="b58b9-104">About Classes and Desired State Configuration</span></span>

## <a name="short-description"></a><span data-ttu-id="b58b9-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="b58b9-105">Short description</span></span>

<span data-ttu-id="b58b9-106">Décrit comment vous pouvez utiliser des classes pour développer dans PowerShell avec la configuration d’état souhaité (DSC).</span><span class="sxs-lookup"><span data-stu-id="b58b9-106">Describes how you can use classes to develop in PowerShell with Desired State Configuration (DSC).</span></span>

## <a name="long-description"></a><span data-ttu-id="b58b9-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="b58b9-107">Long description</span></span>

<span data-ttu-id="b58b9-108">À compter de Windows PowerShell 5,0, le langage a été ajouté pour définir des classes et d’autres types définis par l’utilisateur, en utilisant une syntaxe et une sémantique formelles similaires à celles d’autres langages de programmation orientés objet.</span><span class="sxs-lookup"><span data-stu-id="b58b9-108">Starting in Windows PowerShell 5.0, language was added to define classes and other user-defined types, by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="b58b9-109">L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’adopter PowerShell pour un plus grand nombre de cas d’usage, de simplifier le développement des artefacts PowerShell tels que les ressources DSC et d’accélérer la couverture des surfaces de gestion.</span><span class="sxs-lookup"><span data-stu-id="b58b9-109">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts such as DSC resources, and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="b58b9-110">Scénarios pris en charge</span><span class="sxs-lookup"><span data-stu-id="b58b9-110">Supported scenarios</span></span>

<span data-ttu-id="b58b9-111">Les scénarios suivants sont pris en charge :</span><span class="sxs-lookup"><span data-stu-id="b58b9-111">The following scenarios are supported:</span></span>

- <span data-ttu-id="b58b9-112">Définir les ressources DSC et leurs types associés à l’aide du langage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b58b9-112">Define DSC resources and their associated types by using the PowerShell language.</span></span>
- <span data-ttu-id="b58b9-113">Définir des types personnalisés dans PowerShell à l’aide de constructions de programmation orientée objet familières, telles que des classes, des propriétés, des méthodes et l’héritage.</span><span class="sxs-lookup"><span data-stu-id="b58b9-113">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, and inheritance.</span></span>
- <span data-ttu-id="b58b9-114">Déboguez les types à l’aide du langage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b58b9-114">Debug types by using the PowerShell language.</span></span>
- <span data-ttu-id="b58b9-115">Générez et gérez des exceptions à l’aide de mécanismes formels et au niveau approprié.</span><span class="sxs-lookup"><span data-stu-id="b58b9-115">Generate and handle exceptions by using formal mechanisms, and at the right level.</span></span>

## <a name="define-dsc-resources-with-classes"></a><span data-ttu-id="b58b9-116">Définir des ressources DSC avec des classes</span><span class="sxs-lookup"><span data-stu-id="b58b9-116">Define DSC resources with classes</span></span>

<span data-ttu-id="b58b9-117">Hormis les modifications de syntaxe, les principales différences entre une ressource DSC définie par la classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b58b9-117">Apart from syntax changes, the major differences between a class-defined DSC resource and a cmdlet DSC resource provider are the following items:</span></span>

- <span data-ttu-id="b58b9-118">Un fichier MOF (Management Object Format) n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b58b9-118">A Management Object Format (MOF) file is not required.</span></span>
- <span data-ttu-id="b58b9-119">Aucun sous-dossier DSCResource dans le dossier de module n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b58b9-119">A DSCResource subfolder in the module folder is not required.</span></span>
- <span data-ttu-id="b58b9-120">Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="b58b9-120">A PowerShell module file can contain multiple DSC resource classes.</span></span>

## <a name="create-a-class-defined-dsc-resource-provider"></a><span data-ttu-id="b58b9-121">Créer un fournisseur de ressources DSC défini par une classe</span><span class="sxs-lookup"><span data-stu-id="b58b9-121">Create a class-defined DSC resource provider</span></span>

<span data-ttu-id="b58b9-122">L’exemple suivant est un fournisseur de ressources DSC défini par une classe qui est enregistré en tant que module, MyDSCResource. psm1.</span><span class="sxs-lookup"><span data-stu-id="b58b9-122">The following example is a class-defined DSC resource provider that is saved as a module, MyDSCResource.psm1.</span></span> <span data-ttu-id="b58b9-123">Vous devez toujours inclure une propriété de clé dans un fournisseur de ressources DSC défini par une classe.</span><span class="sxs-lookup"><span data-stu-id="b58b9-123">You must always include a key property in a class-defined DSC resource provider.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
    This resource manages the file in a specific path.
    [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
        This property is the fully qualified path to the file that is
        expected to be present or absent.

        The [DscProperty(Key)] attribute indicates the property is a
        key and its value uniquely identifies a resource instance.
        Defining this attribute also means the property is required
        and DSC will ensure a value is set before calling the resource.

        A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
        This property defines the fully qualified path to a file that will
        be placed on the system if $Ensure = Present and $Path does not
        exist.

        NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
        This property reports the file's create timestamp.

        [DscProperty(NotConfigurable)] attribute indicates the property is
        not configurable in DSC configuration.  Properties marked this way
        are populated by the Get() method to report additional details
        about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#

        This method is equivalent of the Test-TargetResource script
        function. It should return True or False, showing whether the
        resource is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
{
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }
        return $this
    }

    <#
        Helper method to check if the file exists and it is correct file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif( $item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }
        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if(-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid code
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
# This module defines a class for a DSC "FileResource" provider.

enum Ensure
{
    Absent
    Present
}

<# This resource manages the file in a specific path.
[DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource{

    <# This is a key property
        [DscResourceKey()] also means the property is required.
        It is guaranteed to be set, other properties may not
        be set if the configuration did not specify values.
    #>
    [DscResourceKey()]
    [string]$Path

    <#
        [DscResourceMandatory()] means the property is required.
        It is guaranteed to be set, other properties may not be set
        if the configuration did not specify values.
    #>
    [DscResourceMandatory()]
    [Ensure] $Ensure

    <#
        [DscResourceMandatory()] means the property is required.
    #>
    [DscResourceMandatory()]
    [string] $SourcePath

    [DscResource

    <#
        This method replaces the Set-TargetResource DSC script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = Test-Path -path $this.Path -PathType Leaf
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $this.Path"
                Remove-Item -LiteralPath $this.Path
            }
        }
    }

    <#

        This method replaces the Test-TargetResource function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>

    [bool] Test()
    {
        if(Test-Path -path $this.Path -PathType Container)
        {
            throw "Path '$this.Path' is a directory path."
        }

        $fileExists = Test-Path -path $this.Path -PathType Leaf

        if($this.ensure -eq [Ensure]::Present)
        {
            return $fileExists
        }

        return (-not $fileExists)
    }

    <#
        This method replaces the Get-TargetResource function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>

    [FileResource] Get()
    {
        $file = Get-item $this.Path
        return $this
    }

    <#
        Helper method to copy file from source to path.
        Because this resource provider run under system,
        Only the Administrators and system have full
        access to the new created directory and file
    #>
    CopyFile()
    {
        if(Test-Path -path $this.SourcePath -PathType Container)
        {
            throw "SourcePath '$this.SourcePath' is a directory path"
        }

        if( -not (Test-Path -path $this.SourcePath -PathType Leaf))
        {
            throw "SourcePath '$this.SourcePath' is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid lines
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -path $this.Path -PathType Container)
        {
            throw "Path '$this.Path' is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <a name="create-a-module-manifest"></a><span data-ttu-id="b58b9-124">Créer un manifeste de module</span><span class="sxs-lookup"><span data-stu-id="b58b9-124">Create a module manifest</span></span>

<span data-ttu-id="b58b9-125">Après avoir créé le fournisseur de ressources DSC défini par une classe et l’avoir enregistré en tant que module, créez un manifeste de module pour ce module.</span><span class="sxs-lookup"><span data-stu-id="b58b9-125">After creating the class-defined DSC resource provider, and saving it as a module, create a module manifest for the module.</span></span> <span data-ttu-id="b58b9-126">Pour rendre une ressource de classe disponible pour le moteur DSC, vous devez inclure une instruction `DscResourcesToExport` dans le fichier manifeste qui indique au module d’exporter les ressources.</span><span class="sxs-lookup"><span data-stu-id="b58b9-126">To make a class-based resource available to the DSC engine, you must include a `DscResourcesToExport` statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="b58b9-127">Dans cet exemple, le manifeste de module suivant est enregistré en tant que MyDscResource.psd1.</span><span class="sxs-lookup"><span data-stu-id="b58b9-127">In this example, the following module manifest is saved as MyDscResource.psd1.</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

}
```

## <a name="deploy-a-dsc-resource-provider"></a><span data-ttu-id="b58b9-128">Déployer un fournisseur de ressources DSC</span><span class="sxs-lookup"><span data-stu-id="b58b9-128">Deploy a DSC resource provider</span></span>

<span data-ttu-id="b58b9-129">Déployez le nouveau fournisseur de ressources DSC en créant un dossier MyDscResource dans `$pshome\Modules` ou `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="b58b9-129">Deploy the new DSC resource provider by creating a MyDscResource folder in `$pshome\Modules` or `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="b58b9-130">Il est inutile de créer un sous-dossier DSCResource.</span><span class="sxs-lookup"><span data-stu-id="b58b9-130">You do not need to create a DSCResource subfolder.</span></span> <span data-ttu-id="b58b9-131">Copiez les fichiers de module et de manifeste de module (MyDscResource.psm1 et MyDscResource.psd1) dans le dossier MyDscResource.</span><span class="sxs-lookup"><span data-stu-id="b58b9-131">Copy the module and module manifest files (MyDscResource.psm1 and MyDscResource.psd1) to the MyDscResource folder.</span></span>

<span data-ttu-id="b58b9-132">Désormais, vous pouvez créer et exécuter un script de configuration comme vous le feriez avec n’importe quelle ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="b58b9-132">From this point, you create and run a configuration script as you would with any DSC resource.</span></span>

## <a name="create-a-dsc-configuration-script"></a><span data-ttu-id="b58b9-133">Créer un script de configuration DSC</span><span class="sxs-lookup"><span data-stu-id="b58b9-133">Create a DSC configuration script</span></span>

<span data-ttu-id="b58b9-134">Après avoir enregistré la classe et les fichiers manifeste dans la structure de dossiers comme décrit précédemment, vous pouvez créer une configuration qui utilise la nouvelle ressource.</span><span class="sxs-lookup"><span data-stu-id="b58b9-134">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="b58b9-135">La configuration suivante fait référence au module MyDSCResource.</span><span class="sxs-lookup"><span data-stu-id="b58b9-135">The following configuration references the MyDSCResource module.</span></span> <span data-ttu-id="b58b9-136">Enregistrez la configuration en tant que script, MyResource.ps1.</span><span class="sxs-lookup"><span data-stu-id="b58b9-136">Save the configuration as a script, MyResource.ps1.</span></span>

<span data-ttu-id="b58b9-137">Pour plus d’informations sur l’exécution d’une configuration DSC, consultez [vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers).</span><span class="sxs-lookup"><span data-stu-id="b58b9-137">For information about how to run a DSC configuration, see [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/dscforengineers).</span></span>

<span data-ttu-id="b58b9-138">Avant d’exécuter la configuration, créez `C:\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="b58b9-138">Before you run the configuration, create `C:\test.txt`.</span></span> <span data-ttu-id="b58b9-139">La configuration vérifie si le fichier existe dans `c:\test\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="b58b9-139">The configuration checks if the file exists at `c:\test\test.txt`.</span></span> <span data-ttu-id="b58b9-140">Si le fichier n’existe pas, la configuration copie le fichier à partir de `C:\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="b58b9-140">If the file does not exist, the configuration copies the file from `C:\test.txt`.</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "C:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

<span data-ttu-id="b58b9-141">Exécutez ce script comme vous le feriez pour n’importe quel script de configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="b58b9-141">Run this script as you would any DSC configuration script.</span></span> <span data-ttu-id="b58b9-142">Pour démarrer la configuration, dans une console PowerShell avec élévation de privilèges, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b58b9-142">To start the configuration, in an elevated PowerShell console, run the following:</span></span>

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="b58b9-143">Héritage dans les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="b58b9-143">Inheritance in PowerShell classes</span></span>

### <a name="declare-base-classes-for-powershell-classes"></a><span data-ttu-id="b58b9-144">Déclarer des classes de base pour les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="b58b9-144">Declare base classes for PowerShell classes</span></span>

<span data-ttu-id="b58b9-145">Vous pouvez déclarer une classe PowerShell comme type de base pour une autre classe PowerShell, comme illustré dans l’exemple suivant, dans lequel **fruit** est un type de base pour **Apple** .</span><span class="sxs-lookup"><span data-stu-id="b58b9-145">You can declare a PowerShell class as a base type for another PowerShell class, as shown in the following example, in which **fruit** is a base type for **apple** .</span></span>

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a><span data-ttu-id="b58b9-146">Déclarer des interfaces implémentées pour les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="b58b9-146">Declare implemented interfaces for PowerShell classes</span></span>

<span data-ttu-id="b58b9-147">Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points ( `:` ) si aucun type de base n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="b58b9-147">You can declare implemented interfaces after base types, or immediately after a colon (`:`) if there is no base type specified.</span></span> <span data-ttu-id="b58b9-148">Séparez tous les noms de types par des virgules.</span><span class="sxs-lookup"><span data-stu-id="b58b9-148">Separate all type names by using commas.</span></span> <span data-ttu-id="b58b9-149">Cela est similaire à la syntaxe C#.</span><span class="sxs-lookup"><span data-stu-id="b58b9-149">This is similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableTest : test, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

### <a name="call-base-class-constructors"></a><span data-ttu-id="b58b9-150">Appeler les constructeurs de classe de base</span><span class="sxs-lookup"><span data-stu-id="b58b9-150">Call base class constructors</span></span>

<span data-ttu-id="b58b9-151">Pour appeler un constructeur de classe de base à partir d’une sous-classe, ajoutez le `base` mot clé, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b58b9-151">To call a base class constructor from a subclass, add the `base` keyword, as shown in the following example:</span></span>

```powershell
class A {
    [int]$a
    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

    [B]::new().a # return 103
```

<span data-ttu-id="b58b9-152">Si une classe de base a un constructeur par défaut (aucun paramètre), vous pouvez omettre un appel de constructeur explicite, comme indiqué.</span><span class="sxs-lookup"><span data-stu-id="b58b9-152">If a base class has a default constructor (no parameters), you can omit an explicit constructor call, as shown.</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a><span data-ttu-id="b58b9-153">Appeler des méthodes de la classe de base</span><span class="sxs-lookup"><span data-stu-id="b58b9-153">Call base class methods</span></span>

<span data-ttu-id="b58b9-154">Vous pouvez substituer des méthodes existantes dans les sous-classes.</span><span class="sxs-lookup"><span data-stu-id="b58b9-154">You can override existing methods in subclasses.</span></span> <span data-ttu-id="b58b9-155">Pour effectuer la substitution, déclarez les méthodes à l’aide du même nom et de la même signature.</span><span class="sxs-lookup"><span data-stu-id="b58b9-155">To do the override, declare methods by using the same name and signature.</span></span>

```powershell
class baseClass
{
    [int]days() {return 100500}
}
class childClass1 : baseClass
{
    [int]days () {return 200600}
}

    [childClass1]::new().days() # return 200600
```

<span data-ttu-id="b58b9-156">Pour appeler des méthodes de la classe de base à partir d’implémentations substituées, effectuez un cast vers la classe `([baseclass]$this)` de base lors de l’appel.</span><span class="sxs-lookup"><span data-stu-id="b58b9-156">To call base class methods from overridden implementations, cast to the base class `([baseclass]$this)` on invocation.</span></span>

```powershell
class childClass2 : baseClass
{
    [int]days()
    {
        return 3 * ([baseClass]$this).days()
    }
}

    [childClass2]::new().days() # return 301500
```

<span data-ttu-id="b58b9-157">Toutes les méthodes PowerShell sont virtuelles.</span><span class="sxs-lookup"><span data-stu-id="b58b9-157">All PowerShell methods are virtual.</span></span> <span data-ttu-id="b58b9-158">Vous pouvez masquer les méthodes .NET non virtuelles dans une sous-classe en utilisant la même syntaxe que pour les méthodes override : DECLARE portant le même nom et la même signature.</span><span class="sxs-lookup"><span data-stu-id="b58b9-158">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="current-limitations-with-class-inheritance"></a><span data-ttu-id="b58b9-159">Limitations actuelles avec héritage de classe</span><span class="sxs-lookup"><span data-stu-id="b58b9-159">Current limitations with class inheritance</span></span>

<span data-ttu-id="b58b9-160">Une limitation de l’héritage de classes est qu’il n’existe aucune syntaxe pour déclarer des interfaces dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b58b9-160">A limitation with class inheritance is that there is no syntax to declare interfaces in PowerShell.</span></span>

## <a name="defining-custom-types-in-powershell"></a><span data-ttu-id="b58b9-161">Définition de types personnalisés dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="b58b9-161">Defining custom types in PowerShell</span></span>

<span data-ttu-id="b58b9-162">Windows PowerShell 5,0 a introduit plusieurs éléments de langage.</span><span class="sxs-lookup"><span data-stu-id="b58b9-162">Windows PowerShell 5.0 introduced several language elements.</span></span>

### <a name="class-keyword"></a><span data-ttu-id="b58b9-163">Mot clé classe</span><span class="sxs-lookup"><span data-stu-id="b58b9-163">Class keyword</span></span>

<span data-ttu-id="b58b9-164">Définit une nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="b58b9-164">Defines a new class.</span></span>
<span data-ttu-id="b58b9-165">Le `class` mot clé est un type de .NET Framework true.</span><span class="sxs-lookup"><span data-stu-id="b58b9-165">The `class` keyword is a true .NET Framework type.</span></span>
<span data-ttu-id="b58b9-166">Les membres de la classe sont publics.</span><span class="sxs-lookup"><span data-stu-id="b58b9-166">Class members are public.</span></span>

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="b58b9-167">Mot clé Enum et énumérations</span><span class="sxs-lookup"><span data-stu-id="b58b9-167">Enum keyword and enumerations</span></span>

<span data-ttu-id="b58b9-168">La prise en charge du `enum` mot clé a été ajoutée et est une modification avec rupture.</span><span class="sxs-lookup"><span data-stu-id="b58b9-168">Support for the `enum` keyword was added and is a breaking change.</span></span> <span data-ttu-id="b58b9-169">Le `enum` délimiteur est actuellement un saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="b58b9-169">The `enum` delimiter is currently a newline.</span></span> <span data-ttu-id="b58b9-170">Une solution de contournement pour ceux qui utilisent déjà `enum` consiste à insérer une esperluette ( `&` ) avant le mot.</span><span class="sxs-lookup"><span data-stu-id="b58b9-170">A workaround for those who are already using `enum` is to insert an ampersand (`&`) before the word.</span></span> <span data-ttu-id="b58b9-171">Limitations actuelles : vous ne pouvez pas définir un énumérateur en termes de lui-même, mais vous pouvez l’initialiser `enum` en termes d’un autre `enum` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b58b9-171">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize `enum` in terms of another `enum`, as shown in the following example:</span></span>

<span data-ttu-id="b58b9-172">Le type de base ne peut pas être spécifié actuellement.</span><span class="sxs-lookup"><span data-stu-id="b58b9-172">The base type cannot currently be specified.</span></span> <span data-ttu-id="b58b9-173">Le type de base est toujours [int].</span><span class="sxs-lookup"><span data-stu-id="b58b9-173">The base type is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="b58b9-174">Une valeur d’énumérateur doit être une constante au moment de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="b58b9-174">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="b58b9-175">La valeur de l’énumérateur ne peut pas être définie sur le résultat d’une commande appelée.</span><span class="sxs-lookup"><span data-stu-id="b58b9-175">The enumerator value cannot be set to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="b58b9-176">`Enum` prend en charge les opérations arithmétiques, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b58b9-176">`Enum` supports arithmetic operations, as shown in the following example:</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a><span data-ttu-id="b58b9-177">Mot clé Hidden</span><span class="sxs-lookup"><span data-stu-id="b58b9-177">Hidden keyword</span></span>

<span data-ttu-id="b58b9-178">Le `hidden` mot clé, introduit dans Windows PowerShell 5,0, masque les membres de classe des résultats par défaut `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="b58b9-178">The `hidden` keyword, introduced in Windows PowerShell 5.0, hides class members from default `Get-Member` results.</span></span> <span data-ttu-id="b58b9-179">Spécifiez la propriété Hidden comme indiqué dans la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="b58b9-179">Specify the hidden property as shown in the following line:</span></span>

```powershell
hidden [type] $classmember = <value>
```

<span data-ttu-id="b58b9-180">Les membres masqués ne sont pas affichés à l’aide de la saisie semi-automatique par tabulation ou IntelliSense, sauf si la saisie semi-automatique se produit dans la classe qui définit le membre masqué.</span><span class="sxs-lookup"><span data-stu-id="b58b9-180">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="b58b9-181">Un nouvel attribut, **System. Management. Automation. hiddenattribute,** , a été ajouté, afin que le code C# puisse avoir la même sémantique dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b58b9-181">A new attribute, **System.Management.Automation.HiddenAttribute** , was added, so that C# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="b58b9-182">Pour plus d’informations, consultez [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).</span><span class="sxs-lookup"><span data-stu-id="b58b9-182">For more information, see [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).</span></span>

### <a name="import-dscresource"></a><span data-ttu-id="b58b9-183">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="b58b9-183">Import-DscResource</span></span>

<span data-ttu-id="b58b9-184">`Import-DscResource` est maintenant un mot clé véritablement dynamique.</span><span class="sxs-lookup"><span data-stu-id="b58b9-184">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="b58b9-185">PowerShell analyse le module racine du module spécifié et recherche les classes qui contiennent l’attribut DscResource.</span><span class="sxs-lookup"><span data-stu-id="b58b9-185">PowerShell parses the specified module's root module, searching for classes that contain the DscResource attribute.</span></span>

### <a name="properties"></a><span data-ttu-id="b58b9-186">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b58b9-186">Properties</span></span>

<span data-ttu-id="b58b9-187">Un nouveau champ, `ImplementingAssembly` , a été ajouté à `ModuleInfo` .</span><span class="sxs-lookup"><span data-stu-id="b58b9-187">A new field, `ImplementingAssembly`, was added to `ModuleInfo`.</span></span> <span data-ttu-id="b58b9-188">Si le script définit des classes, ou si l’assembly chargé pour les modules binaires `ImplementingAssembly` est défini sur l’assembly dynamique créé pour un module de script.</span><span class="sxs-lookup"><span data-stu-id="b58b9-188">If the script defines classes, or the loaded assembly for binary modules `ImplementingAssembly` is set to the dynamic assembly created for a script module.</span></span> <span data-ttu-id="b58b9-189">Il n’est pas défini quand ModuleType = Manifest.</span><span class="sxs-lookup"><span data-stu-id="b58b9-189">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="b58b9-190">La réflexion sur le `ImplementingAssembly` champ Découvre des ressources dans un module.</span><span class="sxs-lookup"><span data-stu-id="b58b9-190">Reflection on the `ImplementingAssembly` field discovers resources in a module.</span></span> <span data-ttu-id="b58b9-191">Cela signifie que vous pouvez découvrir des ressources écrites en PowerShell ou d’autres langages managés.</span><span class="sxs-lookup"><span data-stu-id="b58b9-191">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="b58b9-192">Champs avec initialiseurs.</span><span class="sxs-lookup"><span data-stu-id="b58b9-192">Fields with initializers.</span></span>

`[int] $i = 5`

<span data-ttu-id="b58b9-193">Static est pris en charge et fonctionne comme un attribut, comme les contraintes de type, de sorte qu’il peut être spécifié dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="b58b9-193">Static is supported and works like an attribute, similar to the type constraints, so it can be specified in any order.</span></span>

`static [int] $count = 0`

<span data-ttu-id="b58b9-194">Un type est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b58b9-194">A type is optional.</span></span>

`$s = "hello"`

<span data-ttu-id="b58b9-195">Tous les membres sont publics.</span><span class="sxs-lookup"><span data-stu-id="b58b9-195">All members are public.</span></span> <span data-ttu-id="b58b9-196">Les propriétés nécessitent un saut de ligne ou un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="b58b9-196">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="b58b9-197">Si aucun type d’objet n’est spécifié, le type de propriété est **Object** .</span><span class="sxs-lookup"><span data-stu-id="b58b9-197">If no object type is specified, the property type is **Object** .</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="b58b9-198">Constructeurs et instanciation</span><span class="sxs-lookup"><span data-stu-id="b58b9-198">Constructors and instantiation</span></span>

<span data-ttu-id="b58b9-199">Les classes PowerShell peuvent avoir des constructeurs qui ont le même nom que leur classe.</span><span class="sxs-lookup"><span data-stu-id="b58b9-199">PowerShell classes can have constructors that have the same name as their class.</span></span> <span data-ttu-id="b58b9-200">Les constructeurs peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="b58b9-200">Constructors can be overloaded.</span></span> <span data-ttu-id="b58b9-201">Les constructeurs statiques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b58b9-201">Static constructors are supported.</span></span>
<span data-ttu-id="b58b9-202">Les propriétés avec des expressions d’initialisation sont initialisées avant l’exécution du code dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="b58b9-202">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="b58b9-203">Les propriétés statiques sont initialisées avant le corps d’un constructeur statique, et les propriétés d’instance sont initialisées avant le corps du constructeur non statique.</span><span class="sxs-lookup"><span data-stu-id="b58b9-203">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="b58b9-204">Actuellement, il n’existe aucune syntaxe pour appeler un constructeur à partir d’un autre constructeur, tel que la syntaxe C# : `": this()")` .</span><span class="sxs-lookup"><span data-stu-id="b58b9-204">Currently, there is no syntax for calling a constructor from another constructor such as the C# syntax: `": this()")`.</span></span> <span data-ttu-id="b58b9-205">La solution de contournement consiste à définir une méthode Init commune.</span><span class="sxs-lookup"><span data-stu-id="b58b9-205">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="b58b9-206">Voici les méthodes d’instanciation des classes :</span><span class="sxs-lookup"><span data-stu-id="b58b9-206">The following are ways of instantiating classes:</span></span>

- <span data-ttu-id="b58b9-207">Instanciation à l’aide du constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b58b9-207">Instantiating by using the default constructor.</span></span> <span data-ttu-id="b58b9-208">Notez que `New-Object` n’est pas pris en charge dans cette version.</span><span class="sxs-lookup"><span data-stu-id="b58b9-208">Note that `New-Object` is not supported in this release.</span></span>

  `$a = [MyClass]::new()`

- <span data-ttu-id="b58b9-209">Appel d’un constructeur avec un paramètre.</span><span class="sxs-lookup"><span data-stu-id="b58b9-209">Calling a constructor with a parameter.</span></span>

  `$b = [MyClass]::new(42)`

- <span data-ttu-id="b58b9-210">Passage d’un tableau à un constructeur avec plusieurs paramètres</span><span class="sxs-lookup"><span data-stu-id="b58b9-210">Passing an array to a constructor with multiple parameters</span></span>

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

<span data-ttu-id="b58b9-211">Pour cette version, le nom de type est uniquement visible lexicalement, ce qui signifie qu’il n’est pas visible en dehors du module ou du script qui définit la classe.</span><span class="sxs-lookup"><span data-stu-id="b58b9-211">For this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="b58b9-212">Les fonctions peuvent retourner des instances d’une classe définie dans PowerShell, et les instances fonctionnent bien en dehors du module ou du script.</span><span class="sxs-lookup"><span data-stu-id="b58b9-212">Functions can return instances of a class defined in PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="b58b9-213">Les `Get-Member` constructeurs de listes de paramètres **statiques** vous permettent d’afficher les surcharges comme toute autre méthode.</span><span class="sxs-lookup"><span data-stu-id="b58b9-213">The `Get-Member` **Static** parameter lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="b58b9-214">Cette syntaxe est également beaucoup plus rapide que `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="b58b9-214">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

<span data-ttu-id="b58b9-215">La méthode pseudo-statique nommée **new** fonctionne avec les types .NET, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b58b9-215">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span> `[hashtable]::new()`

<span data-ttu-id="b58b9-216">Vous pouvez maintenant voir les surcharges de constructeurs avec `Get-Member`, ou comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="b58b9-216">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a><span data-ttu-id="b58b9-217">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b58b9-217">Methods</span></span>

<span data-ttu-id="b58b9-218">Une méthode de classe Windows PowerShell est implémentée sous forme de **ScriptBlock** ne comportant qu’un bloc de fin.</span><span class="sxs-lookup"><span data-stu-id="b58b9-218">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="b58b9-219">Toutes les méthodes sont publiques.</span><span class="sxs-lookup"><span data-stu-id="b58b9-219">All methods are public.</span></span> <span data-ttu-id="b58b9-220">L’exemple suivant montre comment définir une méthode nommée **DoSomething** .</span><span class="sxs-lookup"><span data-stu-id="b58b9-220">The following shows an example of defining a method named **DoSomething** .</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x)       # method syntax
    }
    private _doSomething($a) {}
}
```

### <a name="method-invocation"></a><span data-ttu-id="b58b9-221">Appel de méthode</span><span class="sxs-lookup"><span data-stu-id="b58b9-221">Method invocation</span></span>

<span data-ttu-id="b58b9-222">Les méthodes surchargées sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="b58b9-222">Overloaded methods are supported.</span></span> <span data-ttu-id="b58b9-223">Les méthodes surchargées sont nommées de la même manière qu’une méthode existante, mais elles sont différenciées par leurs valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b58b9-223">Overloaded methods are named the same as an existing method but differentiated by their specified values.</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a><span data-ttu-id="b58b9-224">Invocation</span><span class="sxs-lookup"><span data-stu-id="b58b9-224">Invocation</span></span>

<span data-ttu-id="b58b9-225">Consultez [appel de méthode](#method-invocation).</span><span class="sxs-lookup"><span data-stu-id="b58b9-225">See [Method invocation](#method-invocation).</span></span>

### <a name="attributes"></a><span data-ttu-id="b58b9-226">Attributs</span><span class="sxs-lookup"><span data-stu-id="b58b9-226">Attributes</span></span>

<span data-ttu-id="b58b9-227">Trois nouveaux attributs ont été ajoutés : `DscResource` , `DscResourceKey` et `DscResourceMandatory` .</span><span class="sxs-lookup"><span data-stu-id="b58b9-227">Three new attributes were added: `DscResource`, `DscResourceKey`, and `DscResourceMandatory`.</span></span>

### <a name="return-types"></a><span data-ttu-id="b58b9-228">Types de retour</span><span class="sxs-lookup"><span data-stu-id="b58b9-228">Return types</span></span>

<span data-ttu-id="b58b9-229">Le type de retour est un contrat.</span><span class="sxs-lookup"><span data-stu-id="b58b9-229">Return type is a contract.</span></span> <span data-ttu-id="b58b9-230">La valeur de retour est convertie au type attendu.</span><span class="sxs-lookup"><span data-stu-id="b58b9-230">The return value is converted to the expected type.</span></span>
<span data-ttu-id="b58b9-231">Si aucun type de retour n’est spécifié, le type de retour est void.</span><span class="sxs-lookup"><span data-stu-id="b58b9-231">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="b58b9-232">Il n’existe aucune diffusion en continu d’objets et d’objets qui ne peuvent pas être écrits dans le pipeline, que ce soit intentionnellement ou par accident.</span><span class="sxs-lookup"><span data-stu-id="b58b9-232">There is no streaming of objects and objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="b58b9-233">Étendue lexicale des variables</span><span class="sxs-lookup"><span data-stu-id="b58b9-233">Lexical scoping of variables</span></span>

<span data-ttu-id="b58b9-234">Voici un exemple illustrant le fonctionnement de l’étendue lexicale dans cette version.</span><span class="sxs-lookup"><span data-stu-id="b58b9-234">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42  # Script scope

function bar
{
    $d = 0  # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d  # error, not found dynamically
        return $script:d # no error

        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="example-create-custom-classes"></a><span data-ttu-id="b58b9-235">Exemple : créer des classes personnalisées</span><span class="sxs-lookup"><span data-stu-id="b58b9-235">Example: Create custom classes</span></span>

<span data-ttu-id="b58b9-236">L’exemple suivant crée plusieurs nouvelles classes personnalisées pour implémenter un langage de feuille de style dynamique (DSL) HTML.</span><span class="sxs-lookup"><span data-stu-id="b58b9-236">The following example creates several new, custom classes to implement an HTML Dynamic Stylesheet Language (DSL).</span></span> <span data-ttu-id="b58b9-237">L’exemple ajoute des fonctions d’assistance pour créer des types d’éléments spécifiques dans le cadre de la classe d’éléments, tels que les styles et les tables de titre, car les types ne peuvent pas être utilisés en dehors de la portée d’un module.</span><span class="sxs-lookup"><span data-stu-id="b58b9-237">The example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $Head
        $text += "`n</head>`n<body>`n"
        $text += $Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$Title</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($Attributes)
        {
            foreach ($attr in $Attributes.Keys)
            {
                $attributesText = " $attr=`"$($Attributes[$attr])`""
            }
        }

        return "<${tag}${attributesText}>$text</$tag>`n"
    }
    [string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#
function H1 {[Element] @{Tag = "H1"; Text = $args.foreach{$_} -join " "}}
function H2 {[Element] @{Tag = "H2"; Text = $args.foreach{$_} -join " "}}
function H3 {[Element] @{Tag = "H3"; Text = $args.foreach{$_} -join " "}}
function P  {[Element] @{Tag = "P" ; Text = $args.foreach{$_} -join " "}}
function B  {[Element] @{Tag = "B" ; Text = $args.foreach{$_} -join " "}}
function I  {[Element] @{Tag = "I" ; Text = $args.foreach{$_} -join " "}}
function HREF
{
    param (
        $Name,
        $Link
    )

    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
        [Parameter(Mandatory)]
        [object[]]
            $Data,
        [Parameter()]
        [string[]]
            $Properties = "*",
        [Parameter()]
        [hashtable]
            $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )

    $bodyText = ""
    # Add the header tags
    $bodyText +=  $Properties.foreach{TH $_}
    # Add the rows
    $bodyText += foreach ($row in $Data)
                {
                            TR (-join $Properties.Foreach{ TD ($row.$_) } )
                }

    $table = [Element] @{
                Tag = "Table"
                Attributes = $Attributes
                Text = $bodyText
            }
    $table
}
function TH  {([Element] @{Tag="TH"; Text=$args.foreach{$_} -join " "})}
function TR  {([Element] @{Tag="TR"; Text=$args.foreach{$_} -join " "})}
function TD  {([Element] @{Tag="TD"; Text=$args.foreach{$_} -join " "})}

function Style
{
    return  [Element]  @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

## <a name="see-also"></a><span data-ttu-id="b58b9-238">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b58b9-238">See also</span></span>

[<span data-ttu-id="b58b9-239">À propos de l’énumération</span><span class="sxs-lookup"><span data-stu-id="b58b9-239">about_Enum</span></span>](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[<span data-ttu-id="b58b9-240">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="b58b9-240">about_Hidden</span></span>](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[<span data-ttu-id="b58b9-241">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="b58b9-241">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="b58b9-242">about_Methods</span><span class="sxs-lookup"><span data-stu-id="b58b9-242">about_Methods</span></span>](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[<span data-ttu-id="b58b9-243">Créer des ressources de configuration d’état souhaité PowerShell personnalisées</span><span class="sxs-lookup"><span data-stu-id="b58b9-243">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)

