---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a>Nouvelles fonctionnalités de langage dans PowerShell 5.0

PowerShell 5.0 offre les nouveaux éléments de langage suivants dans Windows PowerShell :

## <a name="class-keyword"></a>Mot clé classe

Le mot clé **class** définit une nouvelle classe. Il s’agit d’un véritable type .NET Framework.
Les membres de la classe sont publics, mais uniquement dans l’étendue du module.
Vous ne pouvez pas faire référence au nom de type sous forme de chaîne (par exemple, `New-Object` ne fonctionne pas), et dans cette version, vous ne pouvez pas utiliser de littéral de type (par exemple, `[MyClass]`) en dehors du fichier de script/module dans lequel la classe est définie.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Mot clé Enum et énumérations

La prise en charge du mot clé **enum** a été ajoutée. Il utilise le saut de ligne comme délimiteur.
Limitations actuelles : vous ne pouvez pas définir un énumérateur en termes de lui-même, mais vous pouvez initialiser un enum en termes d’un autre enum, comme illustré dans l’exemple suivant.
De plus, le type de base ne peut pas être spécifié actuellement. Il s’agit toujours de [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Une valeur d’énumérateur doit être une constante au moment de l’analyse. Vous ne pouvez pas lui affecter le résultat d’une commande appelée.

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

**Import-DscResource** est désormais un mot clé véritablement dynamique.
PowerShell analyse le module racine du module spécifié et recherche les classes qui contiennent l’attribut **DscResource**.

## <a name="implementingassembly"></a>ImplementingAssembly

Un nouveau champ, **ImplementingAssembly**, a été ajouté à ModuleInfo. Elle a comme valeur l’assembly dynamique créé pour un module de script si le script définit des classes, ou l’assembly chargé pour les modules binaires. Il n’est pas défini quand ModuleType = Manifest.

La réflexion sur le champ **ImplementingAssembly** découvre des ressources dans un module. Cela signifie que vous pouvez découvrir des ressources écrites en PowerShell ou d’autres langages managés.

Champs avec initialiseurs :

```powershell
[int] $i = 5
```

Static est pris en charge. Il fonctionne comme un attribut, comme les contraintes de type. Il peut donc être spécifié dans n’importe quel ordre.

```powershell
static [int] $count = 0
```

Un type est facultatif.

```powershell
$s = "hello"
```

Tous les membres sont publics.

## <a name="constructors-and-instantiation"></a>Constructeurs et instanciation

Les classes Windows PowerShell peuvent avoir des constructeurs. Ils ont le même nom que leur classe. Les constructeurs peuvent être surchargés. Les constructeurs statiques sont pris en charge. Les propriétés avec des expressions d’initialisation sont initialisées avant l’exécution du code dans un constructeur. Les propriétés statiques sont initialisées avant le corps d’un constructeur statique, et les propriétés d’instance sont initialisées avant le corps du constructeur non statique. Actuellement, il n’existe aucune syntaxe pour appeler un constructeur à partir d’un autre constructeur (comme la syntaxe C\# « : this() »). La solution de contournement consiste à définir une méthode Init commune.

Voici comment instancier des classes dans cette version.

Instanciation à l’aide du constructeur par défaut. Notez que New-Object n’est pas pris en charge dans cette version.

```powershell
$a = [MyClass]::new()
```

Appel d’un constructeur avec un paramètre

```powershell
$b = [MyClass]::new(42)
```

Passage d’un tableau à un constructeur avec plusieurs paramètres
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

Dans cette version, New-Object ne fonctionne pas avec les classes définies dans Windows PowerShell. De plus, dans cette version, le nom de type est uniquement visible lexicalement, ce qui signifie qu’il n’est pas visible en dehors du module ou du script qui définit la classe. Les fonctions peuvent retourner des instances d’une classe définies dans Windows PowerShell, et les instances fonctionnent bien en dehors du module ou du script.

`Get-Member -Static` énumère les constructeurs, ce qui vous permet d’afficher les surcharges comme toute autre méthode. Les performances de cette syntaxe sont également beaucoup plus rapides que New-Object.

La méthode pseudo-statique nommée **new** fonctionne avec les types .NET, comme illustré dans l’exemple suivant.

```powershell
[hashtable]::new()
```

Vous pouvez maintenant voir les surcharges de constructeurs avec Get-Member, ou comme illustré dans cet exemple :

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Méthodes

Une méthode de classe Windows PowerShell est implémentée en tant que ScriptBlock ayant uniquement un bloc de fin. Toutes les méthodes sont publiques. L’exemple suivant montre comment définir une méthode nommée **DoSomething**.

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

Les méthodes surchargées (c’est-à-dire celles dont le nom est identique à celui d’une méthode existante, mais qui se distinguent par leurs valeurs spécifiées) sont également prises en charge.

## <a name="properties"></a>Propriétés

Toutes les propriétés sont publiques. Les propriétés nécessitent un saut de ligne ou un point-virgule. Si aucun type d’objet n’est spécifié, le type de propriété est object.

Les propriétés qui utilisent des attributs de validation ou de transformation d’argument (par exemple `[ValidateSet("aaa")]`) fonctionnent comme prévu.

## <a name="hidden"></a>Hidden

Un nouveau mot clé, **Hidden**, a été ajouté. Vous pouvez appliquer **Hidden** à des propriétés et des méthodes (notamment des constructeurs).

Les membres masqués sont publics, mais n’apparaissent pas dans la sortie de Get-Member, sauf si le paramètre -Force est ajouté.

Les membres masqués ne sont pas inclus en cas de saisie semi-automatique via la touche Tab ou lors de l’utilisation d’Intellisense, sauf si la saisie semi-automatique se produit dans la classe qui définit le membre masqué.

Un nouvel attribut, **System.Management.Automation.HiddenAttribute**, a été ajouté pour que le code C# puisse avoir la même sémantique dans Windows PowerShell.

## <a name="return-types"></a>Type de retour

Le type de retour est un contrat. La valeur de retour est convertie au type attendu. Si aucun type de retour n’est spécifié, le type de retour est void. Il n’existe aucune diffusion en continu d’objets. Les objets ne peuvent pas être écrits dans le pipeline, que ce soit intentionnellement ou par accident.

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

L’exemple suivant crée plusieurs classes personnalisées pour implémenter un langage DSL (Dynamic Style Sheet) HTML.
Ensuite, l’exemple ajoute des fonctions d’assistance pour créer des types d’éléments spécifiques dans le cadre de la classe d’éléments, tels que des tables et des styles de titre, car les types ne peuvent pas être utilisés en dehors de l’étendue d’un module.

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
# These are required because types aren’t visible outside of the module.
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
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
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
