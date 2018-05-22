---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="9914f-102">Nouvelles fonctionnalités de langage dans PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9914f-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="9914f-103">PowerShell 5.0 offre les nouveaux éléments de langage suivants dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="9914f-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="9914f-104">Mot clé classe</span><span class="sxs-lookup"><span data-stu-id="9914f-104">Class keyword</span></span>

<span data-ttu-id="9914f-105">Le mot clé **class** définit une nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="9914f-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="9914f-106">Il s’agit d’un véritable type .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9914f-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="9914f-107">Les membres de la classe sont publics, mais uniquement dans l’étendue du module.</span><span class="sxs-lookup"><span data-stu-id="9914f-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="9914f-108">Vous ne pouvez pas faire référence au nom de type sous forme de chaîne (par exemple, `New-Object` ne fonctionne pas), et dans cette version, vous ne pouvez pas utiliser de littéral de type (par exemple, `[MyClass]`) en dehors du fichier de script/module dans lequel la classe est définie.</span><span class="sxs-lookup"><span data-stu-id="9914f-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="9914f-109">Mot clé Enum et énumérations</span><span class="sxs-lookup"><span data-stu-id="9914f-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="9914f-110">La prise en charge du mot clé **enum** a été ajoutée. Il utilise le saut de ligne comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="9914f-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="9914f-111">Limitations actuelles : vous ne pouvez pas définir un énumérateur en termes de lui-même, mais vous pouvez initialiser un enum en termes d’un autre enum, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9914f-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="9914f-112">De plus, le type de base ne peut pas être spécifié actuellement. Il s’agit toujours de [int].</span><span class="sxs-lookup"><span data-stu-id="9914f-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="9914f-113">Une valeur d’énumérateur doit être une constante au moment de l’analyse. Vous ne pouvez pas lui affecter le résultat d’une commande appelée.</span><span class="sxs-lookup"><span data-stu-id="9914f-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="9914f-114">Les énumérations prennent en charge les opérations arithmétiques, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9914f-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="9914f-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="9914f-115">Import-DscResource</span></span>

<span data-ttu-id="9914f-116">**Import-DscResource** est désormais un mot clé véritablement dynamique.</span><span class="sxs-lookup"><span data-stu-id="9914f-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="9914f-117">PowerShell analyse le module racine du module spécifié et recherche les classes qui contiennent l’attribut **DscResource**.</span><span class="sxs-lookup"><span data-stu-id="9914f-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="9914f-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="9914f-118">ImplementingAssembly</span></span>

<span data-ttu-id="9914f-119">Un nouveau champ, **ImplementingAssembly**, a été ajouté à ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="9914f-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="9914f-120">Elle a comme valeur l’assembly dynamique créé pour un module de script si le script définit des classes, ou l’assembly chargé pour les modules binaires.</span><span class="sxs-lookup"><span data-stu-id="9914f-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="9914f-121">Il n’est pas défini quand ModuleType = Manifest.</span><span class="sxs-lookup"><span data-stu-id="9914f-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="9914f-122">La réflexion sur le champ **ImplementingAssembly** découvre des ressources dans un module.</span><span class="sxs-lookup"><span data-stu-id="9914f-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="9914f-123">Cela signifie que vous pouvez découvrir des ressources écrites en PowerShell ou d’autres langages managés.</span><span class="sxs-lookup"><span data-stu-id="9914f-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="9914f-124">Champs avec initialiseurs :</span><span class="sxs-lookup"><span data-stu-id="9914f-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="9914f-125">Static est pris en charge. Il fonctionne comme un attribut, comme les contraintes de type. Il peut donc être spécifié dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="9914f-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="9914f-126">Un type est facultatif.</span><span class="sxs-lookup"><span data-stu-id="9914f-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="9914f-127">Tous les membres sont publics.</span><span class="sxs-lookup"><span data-stu-id="9914f-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="9914f-128">Constructeurs et instanciation</span><span class="sxs-lookup"><span data-stu-id="9914f-128">Constructors and instantiation</span></span>

<span data-ttu-id="9914f-129">Les classes Windows PowerShell peuvent avoir des constructeurs. Ils ont le même nom que leur classe.</span><span class="sxs-lookup"><span data-stu-id="9914f-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="9914f-130">Les constructeurs peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="9914f-130">Constructors can be overloaded.</span></span> <span data-ttu-id="9914f-131">Les constructeurs statiques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9914f-131">Static constructors are supported.</span></span> <span data-ttu-id="9914f-132">Les propriétés avec des expressions d’initialisation sont initialisées avant l’exécution du code dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="9914f-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="9914f-133">Les propriétés statiques sont initialisées avant le corps d’un constructeur statique, et les propriétés d’instance sont initialisées avant le corps du constructeur non statique.</span><span class="sxs-lookup"><span data-stu-id="9914f-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="9914f-134">Actuellement, il n’existe aucune syntaxe pour appeler un constructeur à partir d’un autre constructeur (comme la syntaxe C\# « : this() »).</span><span class="sxs-lookup"><span data-stu-id="9914f-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="9914f-135">La solution de contournement consiste à définir une méthode Init commune.</span><span class="sxs-lookup"><span data-stu-id="9914f-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="9914f-136">Voici comment instancier des classes dans cette version.</span><span class="sxs-lookup"><span data-stu-id="9914f-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="9914f-137">Instanciation à l’aide du constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9914f-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="9914f-138">Notez que New-Object n’est pas pris en charge dans cette version.</span><span class="sxs-lookup"><span data-stu-id="9914f-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="9914f-139">Appel d’un constructeur avec un paramètre</span><span class="sxs-lookup"><span data-stu-id="9914f-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="9914f-140">Passage d’un tableau à un constructeur avec plusieurs paramètres</span><span class="sxs-lookup"><span data-stu-id="9914f-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="9914f-141">Dans cette version, New-Object ne fonctionne pas avec les classes définies dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9914f-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="9914f-142">De plus, dans cette version, le nom de type est uniquement visible lexicalement, ce qui signifie qu’il n’est pas visible en dehors du module ou du script qui définit la classe.</span><span class="sxs-lookup"><span data-stu-id="9914f-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="9914f-143">Les fonctions peuvent retourner des instances d’une classe définies dans Windows PowerShell, et les instances fonctionnent bien en dehors du module ou du script.</span><span class="sxs-lookup"><span data-stu-id="9914f-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="9914f-144">`Get-Member -Static` énumère les constructeurs, ce qui vous permet d’afficher les surcharges comme toute autre méthode.</span><span class="sxs-lookup"><span data-stu-id="9914f-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="9914f-145">Les performances de cette syntaxe sont également beaucoup plus rapides que New-Object.</span><span class="sxs-lookup"><span data-stu-id="9914f-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="9914f-146">La méthode pseudo-statique nommée **new** fonctionne avec les types .NET, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9914f-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="9914f-147">Vous pouvez maintenant voir les surcharges de constructeurs avec Get-Member, ou comme illustré dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="9914f-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="9914f-148">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9914f-148">Methods</span></span>

<span data-ttu-id="9914f-149">Une méthode de classe Windows PowerShell est implémentée en tant que ScriptBlock ayant uniquement un bloc de fin.</span><span class="sxs-lookup"><span data-stu-id="9914f-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="9914f-150">Toutes les méthodes sont publiques.</span><span class="sxs-lookup"><span data-stu-id="9914f-150">All methods are public.</span></span> <span data-ttu-id="9914f-151">L’exemple suivant montre comment définir une méthode nommée **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="9914f-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="9914f-152">Appel de méthode :</span><span class="sxs-lookup"><span data-stu-id="9914f-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="9914f-153">Les méthodes surchargées (c’est-à-dire celles dont le nom est identique à celui d’une méthode existante, mais qui se distinguent par leurs valeurs spécifiées) sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="9914f-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="9914f-154">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9914f-154">Properties</span></span>

<span data-ttu-id="9914f-155">Toutes les propriétés sont publiques.</span><span class="sxs-lookup"><span data-stu-id="9914f-155">All properties are public.</span></span> <span data-ttu-id="9914f-156">Les propriétés nécessitent un saut de ligne ou un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="9914f-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="9914f-157">Si aucun type d’objet n’est spécifié, le type de propriété est object.</span><span class="sxs-lookup"><span data-stu-id="9914f-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="9914f-158">Les propriétés qui utilisent des attributs de validation ou de transformation d’argument (par exemple `[ValidateSet("aaa")]`) fonctionnent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="9914f-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="9914f-159">Hidden</span><span class="sxs-lookup"><span data-stu-id="9914f-159">Hidden</span></span>

<span data-ttu-id="9914f-160">Un nouveau mot clé, **Hidden**, a été ajouté.</span><span class="sxs-lookup"><span data-stu-id="9914f-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="9914f-161">Vous pouvez appliquer **Hidden** à des propriétés et des méthodes (notamment des constructeurs).</span><span class="sxs-lookup"><span data-stu-id="9914f-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="9914f-162">Les membres masqués sont publics, mais n’apparaissent pas dans la sortie de Get-Member, sauf si le paramètre -Force est ajouté.</span><span class="sxs-lookup"><span data-stu-id="9914f-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="9914f-163">Les membres masqués ne sont pas inclus en cas de saisie semi-automatique via la touche Tab ou lors de l’utilisation d’Intellisense, sauf si la saisie semi-automatique se produit dans la classe qui définit le membre masqué.</span><span class="sxs-lookup"><span data-stu-id="9914f-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="9914f-164">Un nouvel attribut, **System.Management.Automation.HiddenAttribute**, a été ajouté pour que le code C# puisse avoir la même sémantique dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9914f-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="9914f-165">Type de retour</span><span class="sxs-lookup"><span data-stu-id="9914f-165">Return types</span></span>

<span data-ttu-id="9914f-166">Le type de retour est un contrat. La valeur de retour est convertie au type attendu.</span><span class="sxs-lookup"><span data-stu-id="9914f-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="9914f-167">Si aucun type de retour n’est spécifié, le type de retour est void.</span><span class="sxs-lookup"><span data-stu-id="9914f-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="9914f-168">Il n’existe aucune diffusion en continu d’objets. Les objets ne peuvent pas être écrits dans le pipeline, que ce soit intentionnellement ou par accident.</span><span class="sxs-lookup"><span data-stu-id="9914f-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="9914f-169">Attributes</span><span class="sxs-lookup"><span data-stu-id="9914f-169">Attributes</span></span>

<span data-ttu-id="9914f-170">Deux nouveaux attributs, **DscResource** et **DscProperty**, ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="9914f-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="9914f-171">Étendue lexicale des variables</span><span class="sxs-lookup"><span data-stu-id="9914f-171">Lexical scoping of variables</span></span>

<span data-ttu-id="9914f-172">Voici un exemple illustrant le fonctionnement de l’étendue lexicale dans cette version.</span><span class="sxs-lookup"><span data-stu-id="9914f-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="9914f-173">Exemple de bout en bout</span><span class="sxs-lookup"><span data-stu-id="9914f-173">End-to-End Example</span></span>

<span data-ttu-id="9914f-174">L’exemple suivant crée plusieurs classes personnalisées pour implémenter un langage DSL (Dynamic Style Sheet) HTML.</span><span class="sxs-lookup"><span data-stu-id="9914f-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="9914f-175">Ensuite, l’exemple ajoute des fonctions d’assistance pour créer des types d’éléments spécifiques dans le cadre de la classe d’éléments, tels que des tables et des styles de titre, car les types ne peuvent pas être utilisés en dehors de l’étendue d’un module.</span><span class="sxs-lookup"><span data-stu-id="9914f-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
