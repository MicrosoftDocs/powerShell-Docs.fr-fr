---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Écriture d’une ressource DSC personnalisée avec les classes PowerShell
ms.openlocfilehash: f2500bfb41302cbeaf3cb9d23b843f26f01c1d5b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="1f156-103">Écriture d’une ressource DSC personnalisée avec les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f156-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="1f156-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1f156-104">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="1f156-105">Grâce à l’introduction des classes PowerShell dans Windows PowerShell 5.0, vous pouvez maintenant définir une ressource DSC en créant une classe.</span><span class="sxs-lookup"><span data-stu-id="1f156-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="1f156-106">La classe définit à la fois le schéma et l’implémentation de la ressource. Il est donc inutile de créer un fichier MOF séparé.</span><span class="sxs-lookup"><span data-stu-id="1f156-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="1f156-107">La structure des dossiers d’une ressource basée sur une classe est également plus simple, car le dossier **DSCResources** n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1f156-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="1f156-108">Dans une ressource DSC basée sur une classe, le schéma est défini comme propriétés de la classe qui peuvent être modifiées à l’aide d’attributs pour spécifier le type de la propriété.</span><span class="sxs-lookup"><span data-stu-id="1f156-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="1f156-109">La ressource est implémentée par les méthodes **Get()**, **Set()** et **Test()** (équivalentes aux fonctions **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource** d’une ressource de script).</span><span class="sxs-lookup"><span data-stu-id="1f156-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="1f156-110">Dans cette rubrique, nous allons créer une ressource simple nommée **FileResource** qui gère un fichier situé dans un chemin spécifié.</span><span class="sxs-lookup"><span data-stu-id="1f156-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="1f156-111">Pour plus d’informations sur les ressources DSC, consultez [Création de ressources DSC Windows PowerShell personnalisées](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="1f156-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="1f156-112">**Remarque :** Les collections génériques ne sont pas prises en charge dans les ressources de classe.</span><span class="sxs-lookup"><span data-stu-id="1f156-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="1f156-113">Structure des dossiers pour une ressource de classe</span><span class="sxs-lookup"><span data-stu-id="1f156-113">Folder structure for a class resource</span></span>

<span data-ttu-id="1f156-114">Pour implémenter une ressource personnalisée DSC avec une classe PowerShell, créez la structure de dossiers suivante.</span><span class="sxs-lookup"><span data-stu-id="1f156-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="1f156-115">La classe est définie dans **MyDscResource.psm1** et le manifeste du module est défini dans **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="1f156-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="1f156-116">Créer la classe</span><span class="sxs-lookup"><span data-stu-id="1f156-116">Create the class</span></span>

<span data-ttu-id="1f156-117">Le mot clé class vous permet de créer une classe PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f156-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="1f156-118">Pour spécifier qu’une classe est une ressource DSC, utilisez l’attribut **DscResource()**.</span><span class="sxs-lookup"><span data-stu-id="1f156-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="1f156-119">Le nom de la classe correspond au nom de la ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="1f156-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="1f156-120">Déclarer des propriétés</span><span class="sxs-lookup"><span data-stu-id="1f156-120">Declare properties</span></span>

<span data-ttu-id="1f156-121">Le schéma de la ressource DSC est défini comme propriétés de la classe.</span><span class="sxs-lookup"><span data-stu-id="1f156-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="1f156-122">Nous déclarons trois propriétés de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="1f156-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="1f156-123">Notez que les propriétés sont modifiées par les attributs.</span><span class="sxs-lookup"><span data-stu-id="1f156-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="1f156-124">La signification des attributs est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1f156-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="1f156-125">**DscProperty(Key)** : la propriété est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1f156-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="1f156-126">La propriété est une clé.</span><span class="sxs-lookup"><span data-stu-id="1f156-126">The property is a key.</span></span> <span data-ttu-id="1f156-127">Les valeurs de toutes les propriétés marquées comme des clés doivent être combinées pour pouvoir identifier de manière unique une instance de ressource au sein d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="1f156-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="1f156-128">**DscProperty(Mandatory)** : la propriété est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1f156-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="1f156-129">**DscProperty(NotConfigurable)** : la propriété est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="1f156-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="1f156-130">Les propriétés marquées avec cet attribut ne peuvent pas être définies par une configuration. Elles sont toutefois remplies par la méthode **Get()** quand celle-ci est présente.</span><span class="sxs-lookup"><span data-stu-id="1f156-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="1f156-131">**DscProperty()** : la propriété est configurable, mais elle n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1f156-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="1f156-132">Les propriétés **$Path** et **$SourcePath** sont des chaînes.</span><span class="sxs-lookup"><span data-stu-id="1f156-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="1f156-133">**$CreationTime** est une propriété [DateTime](https://technet.microsoft.com/library/system.datetime.aspx).</span><span class="sxs-lookup"><span data-stu-id="1f156-133">The **$CreationTime** is a [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) property.</span></span> <span data-ttu-id="1f156-134">La propriété **$Ensure** est un type d’énumération, défini de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="1f156-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="1f156-135">Implémentation des méthodes</span><span class="sxs-lookup"><span data-stu-id="1f156-135">Implementing the methods</span></span>

<span data-ttu-id="1f156-136">Les méthodes **Get()**, **Set()** et **Test()** sont équivalentes aux fonctions **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource** d’une ressource de script.</span><span class="sxs-lookup"><span data-stu-id="1f156-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="1f156-137">Ce code comprend également la fonction CopyFile(), une fonction d’assistance qui copie le fichier de **$SourcePath** vers **$Path**.</span><span class="sxs-lookup"><span data-stu-id="1f156-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
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
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
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
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="1f156-138">Le fichier dans son intégralité</span><span class="sxs-lookup"><span data-stu-id="1f156-138">The complete file</span></span>
<span data-ttu-id="1f156-139">Voici le fichier dans son intégralité.</span><span class="sxs-lookup"><span data-stu-id="1f156-139">The complete class file follows.</span></span>

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
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
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
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
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
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## <a name="create-a-manifest"></a><span data-ttu-id="1f156-140">Créer un manifeste</span><span class="sxs-lookup"><span data-stu-id="1f156-140">Create a manifest</span></span>

<span data-ttu-id="1f156-141">Pour rendre une ressource de classe disponible pour le moteur DSC, vous devez inclure une instruction **DscResourcesToExport** dans le fichier manifeste qui indique au module d’exporter les ressources.</span><span class="sxs-lookup"><span data-stu-id="1f156-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="1f156-142">Notre manifeste ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="1f156-142">Our manifest looks like this:</span></span>

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

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="1f156-143">Tester la ressource</span><span class="sxs-lookup"><span data-stu-id="1f156-143">Test the resource</span></span>

<span data-ttu-id="1f156-144">Après avoir enregistré la classe et les fichiers manifeste dans la structure de dossiers comme décrit précédemment, vous pouvez créer une configuration qui utilise la nouvelle ressource.</span><span class="sxs-lookup"><span data-stu-id="1f156-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="1f156-145">Pour plus d’informations sur l’exécution d’une configuration DSC, consultez [Application des configurations](enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="1f156-145">For information about how to run a DSC configuration, see [Enacting configurations](enactingConfigurations.md).</span></span> <span data-ttu-id="1f156-146">La configuration suivante vérifie si le fichier situé à l’emplacement `c:\test\test.txt` existe et, dans le cas contraire, copie le fichier à partir de `c:\test.txt` (vous devez créer `c:\test.txt` avant d’exécuter la configuration).</span><span class="sxs-lookup"><span data-stu-id="1f156-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="1f156-147">Prise en charge de PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1f156-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="1f156-148">**Remarque :** **PsDscRunAsCredential** est pris en charge dans PowerShell 5.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1f156-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="1f156-149">La propriété **PsDscRunAsCredential** peut être utilisée dans le bloc de ressources [Configurations DSC](configurations.md) pour spécifier que la ressource doit être exécutée sous un jeu d’informations d’identification spécifié.</span><span class="sxs-lookup"><span data-stu-id="1f156-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="1f156-150">Pour plus d’informations, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="1f156-150">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="1f156-151">Exiger ou désactiver PsDscRunAsCredential pour votre ressource</span><span class="sxs-lookup"><span data-stu-id="1f156-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="1f156-152">L’attribut **DscResource()** accepte un paramètre facultatif, **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="1f156-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="1f156-153">Ce paramètre prend une des trois valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f156-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="1f156-154">`Optional` **PsDscRunAsCredential** est facultatif pour les configurations qui appellent cette ressource.</span><span class="sxs-lookup"><span data-stu-id="1f156-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="1f156-155">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1f156-155">This is the default value.</span></span>
- <span data-ttu-id="1f156-156">`Mandatory` **PsDscRunAsCredential** doit être utilisé pour toute configuration qui appelle cette ressource.</span><span class="sxs-lookup"><span data-stu-id="1f156-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="1f156-157">`NotSupported` Les configurations qui appellent cette ressource ne peuvent pas utiliser **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="1f156-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="1f156-158">`Default` Identique à `Optional`.</span><span class="sxs-lookup"><span data-stu-id="1f156-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="1f156-159">Par exemple, utilisez l’attribut suivant pour spécifier que votre ressource personnalisée ne prend pas en charge **PsDscRunAsCredential** :</span><span class="sxs-lookup"><span data-stu-id="1f156-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="1f156-160">Accéder au contexte de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="1f156-160">Access the user context</span></span>

<span data-ttu-id="1f156-161">Pour accéder au contexte utilisateur dans une ressource personnalisée, vous pouvez utiliser la variable automatique `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="1f156-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="1f156-162">Par exemple, le code suivant écrit le contexte de l’utilisateur sous lequel la ressource s’exécute dans le flux de sortie des messages :</span><span class="sxs-lookup"><span data-stu-id="1f156-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="1f156-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f156-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="1f156-164">Concepts</span><span class="sxs-lookup"><span data-stu-id="1f156-164">Concepts</span></span>
[<span data-ttu-id="1f156-165">Création de ressources personnalisées de configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f156-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)