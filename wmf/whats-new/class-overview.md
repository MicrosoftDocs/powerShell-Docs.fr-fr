---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Création de types personnalisés à l’aide de classes PowerShell
ms.openlocfilehash: 0dd5bbaca50abb746e15a7bb64a706c7eceee905
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855534"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Création de types personnalisés à l’aide de classes PowerShell

PowerShell 5.0 offre la possibilité de définir des classes et d’autres types définis par l’utilisateur suivant une syntaxe et une sémantique formelles similaires à celles des autres langages de programmation orientés objet. L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’utiliser PowerShell pour une plus grande variété de cas d’usage, de simplifier le développement des artefacts PowerShell (tels que les ressources DSC) et d’accélérer la couverture des surfaces de gestion.

## <a name="supported-scenarios-in-this-release"></a>Scénarios pris en charge dans cette version

- Définition de ressources DSC et de leurs types associés à l’aide du langage PowerShell
- Définition de types personnalisés dans PowerShell à l’aide de constructions de programmation orientées objet bien connues, telles que les classes, propriétés, méthodes, etc.
- Prise en charge de l’héritage avec la classe dans PowerShell et ressource DSC de base de classe
- Débogage de types à l’aide du langage PowerShell
- Génération et gestion des exceptions à l’aide de mécanismes formels et au niveau approprié

# <a name="declare-base-class"></a>Déclarer une classe de base

Il est possible de déclarer une classe PowerShell comme type de base d’une autre classe PowerShell.

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

Vous pouvez également utiliser des types .NET Framework existants comme classes de base :

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

# <a name="call-base-class-constructor"></a>Appeler un constructeur de classe de base

Pour appeler un constructeur de classe de base à partir d’une sous-classe, utilisez le mot clé **base** :

```powershell
class A
{
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

Si une classe de base a un constructeur par défaut (sans paramètre), vous pouvez omettre un appel de constructeur explicite :

```powershell
class C : B
{
    C([int]$c) {}
}
```

# <a name="call-base-class-method"></a>Appeler une méthode de classe de base

Vous pouvez substituer des méthodes existantes dans les sous-classes. Pour cela, déclarez les méthodes à l’aide des mêmes nom et signature :

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

Pour appeler des méthodes de classe de base à partir d’implémentations remplacées, effectuez une conversion de type vers la classe de base (`[baseClass]$this`) lors de l’appel :

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Toutes les méthodes PowerShell sont virtuelles. Vous pouvez masquer les méthodes .NET non virtuelles d’une sous-classe avec la même syntaxe que pour un remplacement, c’est-à-dire en déclarant des méthodes portant le même nom et la même signature.

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

# <a name="declare-implemented-interface"></a>Déclarer une interface implémentée

Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points (:), si aucun type de base n’est spécifié. Séparez tous les noms de types par des virgules. Cela ressemble à la syntaxe C#.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

# <a name="new-language-features-in-powershell-50"></a>Nouvelles fonctionnalités de langage dans PowerShell 5.0

PowerShell 5.0 offre les nouveaux éléments de langage suivants dans PowerShell :

## <a name="class-keyword"></a>Mot clé classe

Le mot clé `class` définit une nouvelle classe. Il s’agit d’un véritable type .NET Framework. Les membres de la classe sont publics, mais uniquement dans l’étendue du module. Il n’est pas possible de faire référence au nom de type sous forme de chaîne (par exemple, `New-Object` ne fonctionne pas) ou, dans cette version, d’utiliser un littéral de type (par exemple, `[MyClass]`) en dehors du fichier de script ou du module dans lequel la classe est définie.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Mot clé Enum et énumérations

La prise en charge du mot clé `enum` a été ajoutée. Il utilise le saut de ligne comme délimiteur. Il n’est pas possible à l’heure actuelle de définir un énumérateur par lui-même. Vous pouvez en revanche l’initialiser à partir d’un autre enum, comme dans l’exemple suivant. Par ailleurs, le type de base n’est pas spécifiable ; il s’agit toujours de `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Une valeur d’énumérateur doit être une constante au moment de l’analyse. Il ne peut pas s’agir du résultat d’une commande appelée.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Les énumérations prennent en charge les opérations arithmétiques, comme illustré dans l’exemple suivant.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` est maintenant un mot clé véritablement dynamique. PowerShell analyse le module racine du module spécifié et recherche les classes qui contiennent l’attribut **DscResource**.

## <a name="implementingassembly"></a>ImplementingAssembly

Un nouveau champ, **ImplementingAssembly**, a été ajouté à **ModuleInfo**. Elle a comme valeur l’assembly dynamique créé pour un module de script si le script définit des classes, ou l’assembly chargé pour les modules binaires. Il n’est pas défini quand **ModuleType** a la valeur **Manifest**.

La réflexion sur le champ **ImplementingAssembly** découvre des ressources dans un module. Cela signifie que vous pouvez découvrir des ressources écrites en PowerShell ou d’autres langages managés.

Champs avec initialiseurs :

```powershell
[int] $i = 5
```

`Static` est pris en charge. Il fonctionne comme un attribut, tout comme les contraintes de type. Il peut être spécifié dans n’importe quel ordre.

```powershell
static [int] $count = 0
```

Un type est facultatif.

```powershell
$s = "hello"
```

Tous les membres sont publics.

## <a name="constructors-and-instantiation"></a>Constructeurs et instanciation

Les classes PowerShell peuvent avoir des constructeurs. Ils portent le même nom que leur classe. Les constructeurs peuvent être surchargés. Les constructeurs statiques sont pris en charge. Les propriétés avec des expressions d’initialisation sont initialisées avant l’exécution du code dans un constructeur. Les propriétés statiques sont initialisées avant le corps d’un constructeur statique, et les propriétés d’instance sont initialisées avant le corps du constructeur non statique. Actuellement, il n’existe aucune syntaxe pour appeler un constructeur à partir d’un autre constructeur (comme la syntaxe C\# « : this() »). La solution de contournement consiste à définir une méthode `Init()` commune.

### <a name="creating-instances"></a>Créer des instances

> [!NOTE]
> Dans PowerShell 5.0, `New-Object` ne fonctionne pas avec des classes définies dans PowerShell. Par ailleurs, le nom de type n’est visible que lexicalement, ce qui signifie qu’il n’est pas visible en dehors du module ou du script qui définit la classe. Les fonctions peuvent retourner des instances d’une classe définie dans PowerShell. Ces instances fonctionnent en dehors du module ou du script.

1. Instanciation à l’aide du constructeur par défaut.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Appel d’un constructeur avec un paramètre

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Passage d’un tableau à un constructeur avec plusieurs paramètres.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

La méthode pseudo-statique `new()` fonctionne avec les types .NET, comme dans l’exemple suivant.

```powershell
[hashtable]::new()
```

### <a name="discovering-constructors"></a>Découvrir des constructeurs

Vous pouvez maintenant voir les surcharges de constructeurs avec `Get-Member`, ou comme dans cet exemple :

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` énumère les constructeurs, ce qui vous permet d’afficher les surcharges comme toute autre méthode. Cette syntaxe est également beaucoup plus rapide que `New-Object`.

## <a name="methods"></a>Méthodes

Une méthode de classe Windows PowerShell est implémentée sous forme de **ScriptBlock** ne comportant qu’un bloc de fin. Toutes les méthodes sont publiques. L’exemple suivant montre comment définir une méthode nommée **DoSomething**.

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

Appel de méthode :

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Les méthodes surchargées sont également prises en charge.

## <a name="properties"></a>Propriétés

Toutes les propriétés sont publiques. Les propriétés nécessitent un saut de ligne ou un point-virgule. Si aucun type d’objet n’est spécifié, le type de propriété est object.

Les propriétés qui utilisent des attributs de validation ou de transformation d’argument (par exemple, `[ValidateSet("aaa")]`) fonctionnent comme prévu.

## <a name="hidden"></a>Hidden

Un nouveau mot clé, `Hidden`, a été ajouté. `Hidden` peut s’appliquer à des propriétés et à des méthodes (notamment des constructeurs).

Bien qu’ils soient publics, les membres masqués n’apparaissent pas dans la sortie de `Get-Member`, sauf si le paramètre -Force est ajouté. Les membres masqués ne sont pas inclus en cas de saisie semi-automatique via la touche Tab ou lors de l’utilisation d’Intellisense, sauf si la saisie semi-automatique se produit dans la classe qui définit le membre masqué.

Un nouvel attribut, **System.Management.Automation.HiddenAttribute**, a été ajouté pour que le code C\# puisse avoir la même sémantique dans PowerShell.

## <a name="return-types"></a>Type de retour

Le type de retour est un contrat. La valeur de retour est convertie au type attendu. S’il n’est pas spécifié, le type de retour est **void**. Il n’y a pas de diffusion en continu d’objets. Il n’est pas possible d’écrire des objets dans le pipeline, que ce soit intentionnellement ou par accident.

## <a name="attributes"></a>Attributes

Deux nouveaux attributs, **DscResource** et **DscProperty**, ont été ajoutés.

## <a name="lexical-scoping-of-variables"></a>Étendue lexicale des variables

Voici un exemple illustrant le fonctionnement de l’étendue lexicale dans cette version.

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a>Exemple de bout en bout

L’exemple suivant crée quelques classes personnalisées pour implémenter un langage DSL (Dynamic Style Sheet) HTML. Ensuite, l’exemple ajoute des fonctions d’assistance pour créer des types d’éléments spécifiques dans le cadre de la classe d’éléments, tels que des tables et des styles de titre, car les types ne peuvent pas être utilisés en dehors de l’étendue d’un module.

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
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
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
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
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
$bodyText += $Properties.foreach{TH $_}
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
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
