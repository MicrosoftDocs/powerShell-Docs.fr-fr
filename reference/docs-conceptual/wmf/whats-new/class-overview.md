---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Création de types personnalisés à l’aide de classes PowerShell
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147839"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="44b15-103">Création de types personnalisés à l’aide de classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="44b15-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="44b15-104">PowerShell 5.0 offre la possibilité de définir des classes et d’autres types définis par l’utilisateur suivant une syntaxe et une sémantique formelles similaires à celles des autres langages de programmation orientés objet.</span><span class="sxs-lookup"><span data-stu-id="44b15-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="44b15-105">L’objectif est de permettre aux développeurs et aux professionnels de l’informatique d’utiliser PowerShell pour une plus grande variété de cas d’usage, de simplifier le développement des artefacts PowerShell (tels que les ressources DSC) et d’accélérer la couverture des surfaces de gestion.</span><span class="sxs-lookup"><span data-stu-id="44b15-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="44b15-106">Scénarios pris en charge dans cette version</span><span class="sxs-lookup"><span data-stu-id="44b15-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="44b15-107">Définition de ressources DSC et de leurs types associés à l’aide du langage PowerShell</span><span class="sxs-lookup"><span data-stu-id="44b15-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="44b15-108">Définition de types personnalisés dans PowerShell à l’aide de constructions de programmation orientées objet bien connues, telles que les classes, propriétés, méthodes, etc.</span><span class="sxs-lookup"><span data-stu-id="44b15-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="44b15-109">Prise en charge de l’héritage avec la classe dans PowerShell et ressource DSC de base de classe</span><span class="sxs-lookup"><span data-stu-id="44b15-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="44b15-110">Débogage de types à l’aide du langage PowerShell</span><span class="sxs-lookup"><span data-stu-id="44b15-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="44b15-111">Génération et gestion des exceptions à l’aide de mécanismes formels et au niveau approprié</span><span class="sxs-lookup"><span data-stu-id="44b15-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="44b15-112">Déclarer une classe de base</span><span class="sxs-lookup"><span data-stu-id="44b15-112">Declare Base Class</span></span>

<span data-ttu-id="44b15-113">Il est possible de déclarer une classe PowerShell comme type de base d’une autre classe PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44b15-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

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

<span data-ttu-id="44b15-114">Vous pouvez également utiliser des types .NET Framework existants comme classes de base :</span><span class="sxs-lookup"><span data-stu-id="44b15-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="44b15-115">Appeler un constructeur de classe de base</span><span class="sxs-lookup"><span data-stu-id="44b15-115">Call Base Class Constructor</span></span>

<span data-ttu-id="44b15-116">Pour appeler un constructeur de classe de base à partir d’une sous-classe, utilisez le mot clé **base** :</span><span class="sxs-lookup"><span data-stu-id="44b15-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="44b15-117">Si une classe de base a un constructeur par défaut (sans paramètre), vous pouvez omettre un appel de constructeur explicite :</span><span class="sxs-lookup"><span data-stu-id="44b15-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="44b15-118">Appeler une méthode de classe de base</span><span class="sxs-lookup"><span data-stu-id="44b15-118">Call Base Class Method</span></span>

<span data-ttu-id="44b15-119">Vous pouvez substituer des méthodes existantes dans les sous-classes.</span><span class="sxs-lookup"><span data-stu-id="44b15-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="44b15-120">Pour cela, déclarez les méthodes à l’aide des mêmes nom et signature :</span><span class="sxs-lookup"><span data-stu-id="44b15-120">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="44b15-121">Pour appeler des méthodes de classe de base à partir d’implémentations remplacées, effectuez une conversion de type vers la classe de base (`[baseClass]$this`) lors de l’appel :</span><span class="sxs-lookup"><span data-stu-id="44b15-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

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

<span data-ttu-id="44b15-122">Toutes les méthodes PowerShell sont virtuelles.</span><span class="sxs-lookup"><span data-stu-id="44b15-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="44b15-123">Vous pouvez masquer les méthodes .NET non virtuelles d’une sous-classe avec la même syntaxe que pour un remplacement, c’est-à-dire en déclarant des méthodes portant le même nom et la même signature.</span><span class="sxs-lookup"><span data-stu-id="44b15-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

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

### <a name="declare-implemented-interface"></a><span data-ttu-id="44b15-124">Déclarer une interface implémentée</span><span class="sxs-lookup"><span data-stu-id="44b15-124">Declare Implemented Interface</span></span>

<span data-ttu-id="44b15-125">Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points (:), si aucun type de base n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="44b15-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="44b15-126">Séparez tous les noms de types par des virgules.</span><span class="sxs-lookup"><span data-stu-id="44b15-126">Separate all type names by using commas.</span></span> <span data-ttu-id="44b15-127">Cela ressemble à la syntaxe C#.</span><span class="sxs-lookup"><span data-stu-id="44b15-127">It's similar to C# syntax.</span></span>

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

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="44b15-128">Nouvelles fonctionnalités de langage dans PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="44b15-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="44b15-129">PowerShell 5.0 offre les nouveaux éléments de langage suivants dans PowerShell :</span><span class="sxs-lookup"><span data-stu-id="44b15-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="44b15-130">Mot clé classe</span><span class="sxs-lookup"><span data-stu-id="44b15-130">Class keyword</span></span>

<span data-ttu-id="44b15-131">Le mot clé `class` définit une nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="44b15-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="44b15-132">Il s’agit d’un véritable type .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44b15-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="44b15-133">Les membres de la classe sont publics, mais uniquement dans l’étendue du module.</span><span class="sxs-lookup"><span data-stu-id="44b15-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="44b15-134">Il n’est pas possible de faire référence au nom de type sous forme de chaîne (par exemple, `New-Object` ne fonctionne pas) ou, dans cette version, d’utiliser un littéral de type (par exemple, `[MyClass]`) en dehors du fichier de script ou du module dans lequel la classe est définie.</span><span class="sxs-lookup"><span data-stu-id="44b15-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="44b15-135">Mot clé Enum et énumérations</span><span class="sxs-lookup"><span data-stu-id="44b15-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="44b15-136">La prise en charge du mot clé `enum` a été ajoutée. Il utilise le saut de ligne comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="44b15-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="44b15-137">Il n’est pas possible à l’heure actuelle de définir un énumérateur par lui-même.</span><span class="sxs-lookup"><span data-stu-id="44b15-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="44b15-138">Vous pouvez en revanche l’initialiser à partir d’un autre enum, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="44b15-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="44b15-139">Par ailleurs, le type de base n’est pas spécifiable ; il s’agit toujours de `[int]`.</span><span class="sxs-lookup"><span data-stu-id="44b15-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="44b15-140">Une valeur d’énumérateur doit être une constante au moment de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="44b15-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="44b15-141">Il ne peut pas s’agir du résultat d’une commande appelée.</span><span class="sxs-lookup"><span data-stu-id="44b15-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="44b15-142">Les énumérations prennent en charge les opérations arithmétiques, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="44b15-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="44b15-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="44b15-143">Import-DscResource</span></span>

<span data-ttu-id="44b15-144">`Import-DscResource` est maintenant un mot clé véritablement dynamique.</span><span class="sxs-lookup"><span data-stu-id="44b15-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="44b15-145">PowerShell analyse le module racine du module spécifié et recherche les classes qui contiennent l’attribut **DscResource**.</span><span class="sxs-lookup"><span data-stu-id="44b15-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="44b15-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="44b15-146">ImplementingAssembly</span></span>

<span data-ttu-id="44b15-147">Un nouveau champ, **ImplementingAssembly**, a été ajouté à **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="44b15-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="44b15-148">Elle a comme valeur l’assembly dynamique créé pour un module de script si le script définit des classes, ou l’assembly chargé pour les modules binaires.</span><span class="sxs-lookup"><span data-stu-id="44b15-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="44b15-149">Il n’est pas défini quand **ModuleType** a la valeur **Manifest**.</span><span class="sxs-lookup"><span data-stu-id="44b15-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="44b15-150">La réflexion sur le champ **ImplementingAssembly** découvre des ressources dans un module.</span><span class="sxs-lookup"><span data-stu-id="44b15-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="44b15-151">Cela signifie que vous pouvez découvrir des ressources écrites en PowerShell ou d’autres langages managés.</span><span class="sxs-lookup"><span data-stu-id="44b15-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="44b15-152">Champs avec initialiseurs :</span><span class="sxs-lookup"><span data-stu-id="44b15-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="44b15-153">`Static` est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="44b15-153">`Static` is supported.</span></span> <span data-ttu-id="44b15-154">Il fonctionne comme un attribut, tout comme les contraintes de type.</span><span class="sxs-lookup"><span data-stu-id="44b15-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="44b15-155">Il peut être spécifié dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="44b15-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="44b15-156">Un type est facultatif.</span><span class="sxs-lookup"><span data-stu-id="44b15-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="44b15-157">Tous les membres sont publics.</span><span class="sxs-lookup"><span data-stu-id="44b15-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="44b15-158">Constructeurs et instanciation</span><span class="sxs-lookup"><span data-stu-id="44b15-158">Constructors and instantiation</span></span>

<span data-ttu-id="44b15-159">Les classes PowerShell peuvent avoir des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="44b15-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="44b15-160">Ils portent le même nom que leur classe.</span><span class="sxs-lookup"><span data-stu-id="44b15-160">They have the same name as their class.</span></span> <span data-ttu-id="44b15-161">Les constructeurs peuvent être surchargés.</span><span class="sxs-lookup"><span data-stu-id="44b15-161">Constructors can be overloaded.</span></span> <span data-ttu-id="44b15-162">Les constructeurs statiques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="44b15-162">Static constructors are supported.</span></span> <span data-ttu-id="44b15-163">Les propriétés avec des expressions d’initialisation sont initialisées avant l’exécution du code dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="44b15-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="44b15-164">Les propriétés statiques sont initialisées avant le corps d’un constructeur statique, et les propriétés d’instance sont initialisées avant le corps du constructeur non statique.</span><span class="sxs-lookup"><span data-stu-id="44b15-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="44b15-165">Actuellement, il n’existe aucune syntaxe pour appeler un constructeur à partir d’un autre constructeur (comme la syntaxe C\# « : this() »).</span><span class="sxs-lookup"><span data-stu-id="44b15-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="44b15-166">La solution de contournement consiste à définir une méthode `Init()` commune.</span><span class="sxs-lookup"><span data-stu-id="44b15-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="44b15-167">Créer des instances</span><span class="sxs-lookup"><span data-stu-id="44b15-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="44b15-168">Dans PowerShell 5.0, `New-Object` ne fonctionne pas avec des classes définies dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44b15-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="44b15-169">Par ailleurs, le nom de type n’est visible que lexicalement, ce qui signifie qu’il n’est pas visible en dehors du module ou du script qui définit la classe.</span><span class="sxs-lookup"><span data-stu-id="44b15-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="44b15-170">Les fonctions peuvent retourner des instances d’une classe définie dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44b15-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="44b15-171">Ces instances fonctionnent en dehors du module ou du script.</span><span class="sxs-lookup"><span data-stu-id="44b15-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="44b15-172">Instanciation à l’aide du constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="44b15-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="44b15-173">Appel d’un constructeur avec un paramètre</span><span class="sxs-lookup"><span data-stu-id="44b15-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="44b15-174">Passage d’un tableau à un constructeur avec plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="44b15-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="44b15-175">La méthode pseudo-statique `new()` fonctionne avec les types .NET, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="44b15-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="44b15-176">Découvrir des constructeurs</span><span class="sxs-lookup"><span data-stu-id="44b15-176">Discovering constructors</span></span>

<span data-ttu-id="44b15-177">Vous pouvez maintenant voir les surcharges de constructeurs avec `Get-Member`, ou comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="44b15-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="44b15-178">`Get-Member -Static` énumère les constructeurs, ce qui vous permet d’afficher les surcharges comme toute autre méthode.</span><span class="sxs-lookup"><span data-stu-id="44b15-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="44b15-179">Cette syntaxe est également beaucoup plus rapide que `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="44b15-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="44b15-180">Méthodes</span><span class="sxs-lookup"><span data-stu-id="44b15-180">Methods</span></span>

<span data-ttu-id="44b15-181">Une méthode de classe Windows PowerShell est implémentée sous forme de **ScriptBlock** ne comportant qu’un bloc de fin.</span><span class="sxs-lookup"><span data-stu-id="44b15-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="44b15-182">Toutes les méthodes sont publiques.</span><span class="sxs-lookup"><span data-stu-id="44b15-182">All methods are public.</span></span> <span data-ttu-id="44b15-183">L’exemple suivant montre comment définir une méthode nommée **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="44b15-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="44b15-184">Appel de méthode :</span><span class="sxs-lookup"><span data-stu-id="44b15-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="44b15-185">Les méthodes surchargées sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="44b15-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="44b15-186">Propriétés</span><span class="sxs-lookup"><span data-stu-id="44b15-186">Properties</span></span>

<span data-ttu-id="44b15-187">Toutes les propriétés sont publiques.</span><span class="sxs-lookup"><span data-stu-id="44b15-187">All properties are public.</span></span> <span data-ttu-id="44b15-188">Les propriétés nécessitent un saut de ligne ou un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="44b15-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="44b15-189">Si aucun type d’objet n’est spécifié, le type de propriété est object.</span><span class="sxs-lookup"><span data-stu-id="44b15-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="44b15-190">Les propriétés qui utilisent des attributs de validation ou de transformation d’argument (par exemple, `[ValidateSet("aaa")]`) fonctionnent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="44b15-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="44b15-191">Hidden</span><span class="sxs-lookup"><span data-stu-id="44b15-191">Hidden</span></span>

<span data-ttu-id="44b15-192">Un nouveau mot clé, `Hidden`, a été ajouté.</span><span class="sxs-lookup"><span data-stu-id="44b15-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="44b15-193">`Hidden` peut s’appliquer à des propriétés et à des méthodes (notamment des constructeurs).</span><span class="sxs-lookup"><span data-stu-id="44b15-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="44b15-194">Bien qu’ils soient publics, les membres masqués n’apparaissent pas dans la sortie de `Get-Member`, sauf si le paramètre `-Force` est ajouté.</span><span class="sxs-lookup"><span data-stu-id="44b15-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="44b15-195">Les membres masqués ne sont pas inclus en cas de saisie semi-automatique via la touche Tab ou lors de l’utilisation d’Intellisense, sauf si la saisie semi-automatique se produit dans la classe qui définit le membre masqué.</span><span class="sxs-lookup"><span data-stu-id="44b15-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="44b15-196">Un nouvel attribut, **System.Management.Automation.HiddenAttribute**, a été ajouté pour que le code C\# puisse avoir la même sémantique dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44b15-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="44b15-197">Type de retour</span><span class="sxs-lookup"><span data-stu-id="44b15-197">Return types</span></span>

<span data-ttu-id="44b15-198">Le type de retour est un contrat.</span><span class="sxs-lookup"><span data-stu-id="44b15-198">Return type is a contract.</span></span> <span data-ttu-id="44b15-199">La valeur de retour est convertie au type attendu.</span><span class="sxs-lookup"><span data-stu-id="44b15-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="44b15-200">S’il n’est pas spécifié, le type de retour est **void**.</span><span class="sxs-lookup"><span data-stu-id="44b15-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="44b15-201">Il n’y a pas de diffusion en continu d’objets.</span><span class="sxs-lookup"><span data-stu-id="44b15-201">There is no streaming of objects.</span></span> <span data-ttu-id="44b15-202">Il n’est pas possible d’écrire des objets dans le pipeline, que ce soit intentionnellement ou par accident.</span><span class="sxs-lookup"><span data-stu-id="44b15-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="44b15-203">Attributes</span><span class="sxs-lookup"><span data-stu-id="44b15-203">Attributes</span></span>

<span data-ttu-id="44b15-204">Deux nouveaux attributs, **DscResource** et **DscProperty**, ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="44b15-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="44b15-205">Étendue lexicale des variables</span><span class="sxs-lookup"><span data-stu-id="44b15-205">Lexical scoping of variables</span></span>

<span data-ttu-id="44b15-206">Voici un exemple illustrant le fonctionnement de l’étendue lexicale dans cette version.</span><span class="sxs-lookup"><span data-stu-id="44b15-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="44b15-207">Exemple de bout en bout</span><span class="sxs-lookup"><span data-stu-id="44b15-207">End-to-End Example</span></span>

<span data-ttu-id="44b15-208">L’exemple suivant crée quelques classes personnalisées pour implémenter un langage DSL (Dynamic Style Sheet) HTML.</span><span class="sxs-lookup"><span data-stu-id="44b15-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="44b15-209">Ensuite, l’exemple ajoute des fonctions d’assistance pour créer des types d’éléments spécifiques dans le cadre de la classe d’éléments, tels que des tables et des styles de titre, car les types ne peuvent pas être utilisés en dehors de l’étendue d’un module.</span><span class="sxs-lookup"><span data-stu-id="44b15-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
