---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Écriture d’une ressource DSC personnalisée avec les classes PowerShell
ms.openlocfilehash: 0759685b04688f574d72b62a15833832ad19e816
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401666"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Écriture d’une ressource DSC personnalisée avec les classes PowerShell

> S'applique à : Windows PowerShell 5.0

Grâce à l’introduction des classes PowerShell dans Windows PowerShell 5.0, vous pouvez maintenant définir une ressource DSC en créant une classe. La classe définit à la fois le schéma et l’implémentation de la ressource. Il est donc inutile de créer un fichier MOF séparé. La structure des dossiers d’une ressource basée sur une classe est également plus simple, car le dossier **DSCResources** n’est plus nécessaire.

Dans une ressource DSC basée sur une classe, le schéma est défini comme propriétés de la classe qui peuvent être modifiées à l’aide d’attributs pour spécifier le type de la propriété. La ressource est implémentée par les méthodes **Get()**, **Set()** et **Test()** (équivalentes aux fonctions **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource** d’une ressource de script).

Dans cette rubrique, nous allons créer une ressource simple nommée **FileResource** qui gère un fichier situé dans un chemin spécifié.

Pour plus d’informations sur les ressources DSC, consultez [Création de ressources DSC Windows PowerShell personnalisées](authoringResource.md)

>**Remarque :** Collections génériques ne sont pas pris en charge dans les ressources de classe.

## <a name="folder-structure-for-a-class-resource"></a>Structure des dossiers pour une ressource de classe

Pour implémenter une ressource personnalisée DSC avec une classe PowerShell, créez la structure de dossiers suivante. La classe est définie dans **MyDscResource.psm1** et le manifeste du module est défini dans **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a>Créer la classe

Le mot clé class vous permet de créer une classe PowerShell. Pour spécifier qu’une classe est une ressource DSC, utilisez l’attribut **DscResource()**. Le nom de la classe correspond au nom de la ressource DSC.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Déclarer des propriétés

Le schéma de la ressource DSC est défini comme propriétés de la classe. Nous déclarons trois propriétés de la manière suivante.

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

Notez que les propriétés sont modifiées par les attributs. La signification des attributs est la suivante :

- **Dscproperty (Key)**: La propriété est requise. La propriété est une clé. Les valeurs de toutes les propriétés marquées comme des clés doivent être combinées pour pouvoir identifier de manière unique une instance de ressource au sein d’une configuration.
- **Dscproperty (Mandatory)**: La propriété est requise.
- **Dscproperty (notconfigurable)**: Propriété en lecture seule. Les propriétés marquées avec cet attribut ne peuvent pas être définies par une configuration. Elles sont toutefois remplies par la méthode **Get()** quand celle-ci est présente.
- **DscProperty()**: La propriété est configurable, mais il n’est pas obligatoire.

Les propriétés **$Path** et **$SourcePath** sont des chaînes. **$CreationTime** est une propriété [DateTime](/dotnet/api/system.datetime). La propriété **$Ensure** est un type d’énumération, défini de la manière suivante.

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>Implémentation des méthodes

Les méthodes **Get()**, **Set()** et **Test()** sont équivalentes aux fonctions **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource** d’une ressource de script.

Ce code comprend également la fonction CopyFile(), une fonction d’assistance qui copie le fichier de **$SourcePath** vers **$Path**.

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

### <a name="the-complete-file"></a>Le fichier dans son intégralité
Voici le fichier dans son intégralité.

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


## <a name="create-a-manifest"></a>Créer un manifeste

Pour rendre une ressource de classe disponible pour le moteur DSC, vous devez inclure une instruction **DscResourcesToExport** dans le fichier manifeste qui indique au module d’exporter les ressources. Notre manifeste ressemble à ceci :

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

## <a name="test-the-resource"></a>Tester la ressource

Après avoir enregistré la classe et les fichiers manifeste dans la structure de dossiers comme décrit précédemment, vous pouvez créer une configuration qui utilise la nouvelle ressource. Pour plus d’informations sur l’exécution d’une configuration DSC, consultez [Application des configurations](../pull-server/enactingConfigurations.md). La configuration suivante vérifie si le fichier situé à l’emplacement `c:\test\test.txt` existe et, dans le cas contraire, copie le fichier à partir de `c:\test.txt` (vous devez créer `c:\test.txt` avant d’exécuter la configuration).

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

## <a name="supporting-psdscrunascredential"></a>Prise en charge de PsDscRunAsCredential

>**Remarque :** **PsDscRunAsCredential** est pris en charge dans PowerShell 5.0 et versions ultérieures.

La propriété **PsDscRunAsCredential** peut être utilisée dans le bloc de ressources [Configurations DSC](../configurations/configurations.md) pour spécifier que la ressource doit être exécutée sous un jeu d’informations d’identification spécifié.
Pour plus d’informations, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](../configurations/runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Exiger ou désactiver PsDscRunAsCredential pour votre ressource

L’attribut **DscResource()** accepte un paramètre facultatif, **RunAsCredential**.
Ce paramètre prend une des trois valeurs suivantes :

- `Optional` **PsDscRunAsCredential** est facultatif pour les configurations qui appellent cette ressource. Il s'agit de la valeur par défaut.
- `Mandatory` **PsDscRunAsCredential** doit être utilisé pour toute configuration qui appelle cette ressource.
- `NotSupported` Les configurations qui appellent cette ressource ne peuvent pas utiliser **PsDscRunAsCredential**.
- `Default` Identique à `Optional`.

Par exemple, utilisez l’attribut suivant pour spécifier que votre ressource personnalisée ne prend pas en charge **PsDscRunAsCredential** :

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a>Accéder au contexte de l’utilisateur

Pour accéder au contexte utilisateur dans une ressource personnalisée, vous pouvez utiliser la variable automatique `$global:PsDscContext`.

Par exemple, le code suivant écrit le contexte de l’utilisateur sous lequel la ressource s’exécute dans le flux de sortie des messages :

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Voir aussi
### <a name="concepts"></a>Concepts
[Création de ressources personnalisées de configuration d’état souhaité Windows PowerShell](authoringResource.md)