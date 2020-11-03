---
description: Décrit comment vous pouvez utiliser des classes pour développer dans PowerShell avec la configuration d’état souhaité (DSC).
keywords: powershell,applet de commande
Locale: en-US
ms.date: 1/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des classes et de DSC
ms.openlocfilehash: 6ac48bc58078e0494a33b0383be97e5075c92d6c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207273"
---
# <a name="about-classes-and-desired-state-configuration"></a>À propos des classes et de la configuration d’état souhaité

## <a name="short-description"></a>Description courte

Décrit comment vous pouvez utiliser des classes pour développer dans PowerShell avec la configuration d’état souhaité (DSC).

## <a name="long-description"></a>Description longue

À compter de Windows PowerShell 5,0, le langage a été ajouté pour définir des classes et d’autres types définis par l’utilisateur, en utilisant une syntaxe et une sémantique formelles similaires à celles d’autres langages de programmation orientés objet. L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’adopter Windows PowerShell pour un plus grand nombre de cas d’usage, de simplifier le développement des artefacts PowerShell tels que les ressources DSC et d’accélérer la couverture des surfaces de gestion.

## <a name="supported-scenarios"></a>Scénarios pris en charge

Les scénarios suivants sont pris en charge :

- Définir les ressources DSC et leurs types associés à l’aide du langage PowerShell.
- Définir des types personnalisés dans PowerShell à l’aide de constructions de programmation orientée objet familières, telles que des classes, des propriétés, des méthodes et l’héritage.
- Déboguez les types à l’aide du langage PowerShell.
- Générez et gérez des exceptions à l’aide de mécanismes formels et au niveau approprié.

## <a name="define-dsc-resources-with-classes"></a>Définir des ressources DSC avec des classes

Hormis les modifications de syntaxe, les principales différences entre une ressource DSC définie par la classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :

- Un fichier MOF (Management Object Format) n’est pas obligatoire.
- Aucun sous-dossier DSCResource dans le dossier de module n’est nécessaire.
- Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.

## <a name="create-a-class-defined-dsc-resource-provider"></a>Créer un fournisseur de ressources DSC défini par une classe

L’exemple suivant est un fournisseur de ressources DSC défini par une classe qui est enregistré en tant que module, MyDSCResource. psm1. Vous devez toujours inclure une propriété de clé dans un fournisseur de ressources DSC défini par une classe.

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

## <a name="create-a-module-manifest"></a>Créer un manifeste de module

Après avoir créé le fournisseur de ressources DSC défini par une classe et l’avoir enregistré en tant que module, créez un manifeste de module pour ce module. Pour rendre une ressource de classe disponible pour le moteur DSC, vous devez inclure une instruction `DscResourcesToExport` dans le fichier manifeste qui indique au module d’exporter les ressources. Dans cet exemple, le manifeste de module suivant est enregistré en tant que MyDscResource.psd1.

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

## <a name="deploy-a-dsc-resource-provider"></a>Déployer un fournisseur de ressources DSC

Déployez le nouveau fournisseur de ressources DSC en créant un dossier MyDscResource dans `$pshome\Modules` ou `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` .

Il est inutile de créer un sous-dossier DSCResource. Copiez les fichiers de module et de manifeste de module (MyDscResource.psm1 et MyDscResource.psd1) dans le dossier MyDscResource.

Désormais, vous pouvez créer et exécuter un script de configuration comme vous le feriez avec n’importe quelle ressource DSC.

## <a name="create-a-dsc-configuration-script"></a>Créer un script de configuration DSC

Après avoir enregistré la classe et les fichiers manifeste dans la structure de dossiers comme décrit précédemment, vous pouvez créer une configuration qui utilise la nouvelle ressource. La configuration suivante fait référence au module MyDSCResource. Enregistrez la configuration en tant que script, MyResource.ps1.

Pour plus d’informations sur l’exécution d’une configuration DSC, consultez [vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers).

Avant d’exécuter la configuration, créez `C:\test.txt` . La configuration vérifie si le fichier existe dans `c:\test\test.txt` . Si le fichier n’existe pas, la configuration copie le fichier à partir de `C:\test.txt` .

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

Exécutez ce script comme vous le feriez pour n’importe quel script de configuration DSC. Pour démarrer la configuration, dans une console PowerShell avec élévation de privilèges, exécutez la commande suivante :

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a>Héritage dans les classes PowerShell

### <a name="declare-base-classes-for-powershell-classes"></a>Déclarer des classes de base pour les classes PowerShell

Vous pouvez déclarer une classe PowerShell comme type de base pour une autre classe PowerShell, comme illustré dans l’exemple suivant, dans lequel **fruit** est un type de base pour **Apple** .

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a>Déclarer des interfaces implémentées pour les classes PowerShell

Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points ( `:` ) si aucun type de base n’est spécifié. Séparez tous les noms de types par des virgules. Cela est similaire à la syntaxe C#.

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

### <a name="call-base-class-constructors"></a>Appeler les constructeurs de classe de base

Pour appeler un constructeur de classe de base à partir d’une sous-classe, ajoutez le `base` mot clé, comme indiqué dans l’exemple suivant :

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

Si une classe de base a un constructeur par défaut (aucun paramètre), vous pouvez omettre un appel de constructeur explicite, comme indiqué.

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a>Appeler des méthodes de la classe de base

Vous pouvez substituer des méthodes existantes dans les sous-classes. Pour effectuer la substitution, déclarez les méthodes à l’aide du même nom et de la même signature.

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

Pour appeler des méthodes de la classe de base à partir d’implémentations substituées, effectuez un cast vers la classe `([baseclass]$this)` de base lors de l’appel.

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

Toutes les méthodes PowerShell sont virtuelles. Vous pouvez masquer les méthodes .NET non virtuelles dans une sous-classe en utilisant la même syntaxe que pour les méthodes override : DECLARE portant le même nom et la même signature.

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

### <a name="current-limitations-with-class-inheritance"></a>Limitations actuelles avec héritage de classe

Une limitation de l’héritage de classes est qu’il n’existe aucune syntaxe pour déclarer des interfaces dans PowerShell.

## <a name="defining-custom-types-in-powershell"></a>Définition de types personnalisés dans PowerShell

Windows PowerShell 5,0 a introduit plusieurs éléments de langage.

### <a name="class-keyword"></a>Mot clé classe

Définit une nouvelle classe.
Le `class` mot clé est un type de .NET Framework true.
Les membres de la classe sont publics.

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a>Mot clé Enum et énumérations

La prise en charge du `enum` mot clé a été ajoutée et est une modification avec rupture. Le `enum` délimiteur est actuellement un saut de ligne. Une solution de contournement pour ceux qui utilisent déjà `enum` consiste à insérer une esperluette ( `&` ) avant le mot. Limitations actuelles : vous ne pouvez pas définir un énumérateur en termes de lui-même, mais vous pouvez l’initialiser `enum` en termes d’un autre `enum` , comme indiqué dans l’exemple suivant :

Le type de base ne peut pas être spécifié actuellement. Le type de base est toujours [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Une valeur d’énumérateur doit être une constante au moment de l’analyse. La valeur de l’énumérateur ne peut pas être définie sur le résultat d’une commande appelée.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

`Enum` prend en charge les opérations arithmétiques, comme illustré dans l’exemple suivant :

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a>Mot clé Hidden

Le `hidden` mot clé, introduit dans Windows PowerShell 5,0, masque les membres de classe des résultats par défaut `Get-Member` . Spécifiez la propriété Hidden comme indiqué dans la ligne suivante :

```powershell
hidden [type] $classmember = <value>
```

Les membres masqués ne sont pas affichés à l’aide de la saisie semi-automatique par tabulation ou IntelliSense, sauf si la saisie semi-automatique se produit dans la classe qui définit le membre masqué.

Un nouvel attribut, **System. Management. Automation. hiddenattribute,** , a été ajouté, afin que le code C# puisse avoir la même sémantique dans PowerShell.

Pour plus d’informations, consultez [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` est maintenant un mot clé véritablement dynamique. PowerShell analyse le module racine du module spécifié et recherche les classes qui contiennent l’attribut DscResource.

### <a name="properties"></a>Propriétés

Un nouveau champ, `ImplementingAssembly` , a été ajouté à `ModuleInfo` . Si le script définit des classes, ou si l’assembly chargé pour les modules binaires `ImplementingAssembly` est défini sur l’assembly dynamique créé pour un module de script. Il n’est pas défini quand ModuleType = Manifest.

La réflexion sur le `ImplementingAssembly` champ Découvre des ressources dans un module. Cela signifie que vous pouvez découvrir des ressources écrites en PowerShell ou d’autres langages managés.

Champs avec initialiseurs.

`[int] $i = 5`

Static est pris en charge et fonctionne comme un attribut, comme les contraintes de type, de sorte qu’il peut être spécifié dans n’importe quel ordre.

`static [int] $count = 0`

Un type est facultatif.

`$s = "hello"`

Tous les membres sont publics. Les propriétés nécessitent un saut de ligne ou un point-virgule. Si aucun type d’objet n’est spécifié, le type de propriété est **Object** .

### <a name="constructors-and-instantiation"></a>Constructeurs et instanciation

Les classes PowerShell peuvent avoir des constructeurs qui ont le même nom que leur classe. Les constructeurs peuvent être surchargés. Les constructeurs statiques sont pris en charge.
Les propriétés avec des expressions d’initialisation sont initialisées avant l’exécution du code dans un constructeur. Les propriétés statiques sont initialisées avant le corps d’un constructeur statique, et les propriétés d’instance sont initialisées avant le corps du constructeur non statique. Actuellement, il n’existe aucune syntaxe pour appeler un constructeur à partir d’un autre constructeur, tel que la syntaxe C# : `": this()")` . La solution de contournement consiste à définir une méthode Init commune.

Voici les méthodes d’instanciation des classes :

- Instanciation à l’aide du constructeur par défaut. Notez que `New-Object` n’est pas pris en charge dans cette version.

  `$a = [MyClass]::new()`

- Appel d’un constructeur avec un paramètre.

  `$b = [MyClass]::new(42)`

- Passage d’un tableau à un constructeur avec plusieurs paramètres

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

Pour cette version, le nom de type est uniquement visible lexicalement, ce qui signifie qu’il n’est pas visible en dehors du module ou du script qui définit la classe. Les fonctions peuvent retourner des instances d’une classe définie dans PowerShell, et les instances fonctionnent bien en dehors du module ou du script.

Les `Get-Member` constructeurs de listes de paramètres **statiques** vous permettent d’afficher les surcharges comme toute autre méthode. Cette syntaxe est également beaucoup plus rapide que `New-Object`.

La méthode pseudo-statique nommée **new** fonctionne avec les types .NET, comme illustré dans l’exemple suivant. `[hashtable]::new()`

Vous pouvez maintenant voir les surcharges de constructeurs avec `Get-Member`, ou comme dans cet exemple :

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a>Méthodes

Une méthode de classe Windows PowerShell est implémentée sous forme de **ScriptBlock** ne comportant qu’un bloc de fin. Toutes les méthodes sont publiques. L’exemple suivant montre comment définir une méthode nommée **DoSomething** .

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

### <a name="method-invocation"></a>Appel de méthode

Les méthodes surchargées sont prises en charge. Les méthodes surchargées sont nommées de la même manière qu’une méthode existante, mais elles sont différenciées par leurs valeurs spécifiées.

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a>Invocation

Consultez [appel de méthode](#method-invocation).

### <a name="attributes"></a>Attributs

Trois nouveaux attributs ont été ajoutés : `DscResource` , `DscResourceKey` et `DscResourceMandatory` .

### <a name="return-types"></a>Types de retour

Le type de retour est un contrat. La valeur de retour est convertie au type attendu.
Si aucun type de retour n’est spécifié, le type de retour est void. Il n’existe aucune diffusion en continu d’objets et d’objets qui ne peuvent pas être écrits dans le pipeline, que ce soit intentionnellement ou par accident.

### <a name="lexical-scoping-of-variables"></a>Étendue lexicale des variables

Voici un exemple illustrant le fonctionnement de l’étendue lexicale dans cette version.

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

## <a name="example-create-custom-classes"></a>Exemple : créer des classes personnalisées

L’exemple suivant crée plusieurs nouvelles classes personnalisées pour implémenter un langage de feuille de style dynamique (DSL) HTML. L’exemple ajoute des fonctions d’assistance pour créer des types d’éléments spécifiques dans le cadre de la classe d’éléments, tels que les styles et les tables de titre, car les types ne peuvent pas être utilisés en dehors de la portée d’un module.

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

## <a name="see-also"></a>Voir aussi

[about_DesiredStateConfiguration](../../Microsoft.PowerShell.Core/About/about_desiredstateconfiguration.md)

[À propos de l’énumération](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Methods](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[Création de ressources personnalisées de configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/resources/authoringResource)
