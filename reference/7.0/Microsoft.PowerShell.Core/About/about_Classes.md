---
description: Décrit comment vous pouvez utiliser des classes pour créer vos propres types personnalisés.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des classes
ms.openlocfilehash: 27950034806caf53b2cdbe50329709a8ab177aee
ms.sourcegitcommit: 16d62a98449e3ddaf8d7c65bc1848ede1fd8a3e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "93206277"
---
# <a name="about-classes"></a><span data-ttu-id="0c318-104">À propos des classes</span><span class="sxs-lookup"><span data-stu-id="0c318-104">About Classes</span></span>

## <a name="short-description"></a><span data-ttu-id="0c318-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="0c318-105">Short description</span></span>
<span data-ttu-id="0c318-106">Décrit comment vous pouvez utiliser des classes pour créer vos propres types personnalisés.</span><span class="sxs-lookup"><span data-stu-id="0c318-106">Describes how you can use classes to create your own custom types.</span></span>

## <a name="long-description"></a><span data-ttu-id="0c318-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="0c318-107">Long description</span></span>

<span data-ttu-id="0c318-108">PowerShell 5,0 ajoute une syntaxe formelle pour définir des classes et d’autres types définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0c318-108">PowerShell 5.0 adds a formal syntax to define classes and other user-defined types.</span></span> <span data-ttu-id="0c318-109">L’ajout de classes permet aux développeurs et aux professionnels de l’informatique d’adopter PowerShell pour un plus grand nombre de cas d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="0c318-109">The addition of classes enables developers and IT professionals to embrace PowerShell for a wider range of use cases.</span></span> <span data-ttu-id="0c318-110">Il simplifie le développement des artefacts PowerShell et accélère la couverture des surfaces de gestion.</span><span class="sxs-lookup"><span data-stu-id="0c318-110">It simplifies development of PowerShell artifacts and accelerates coverage of management surfaces.</span></span>

<span data-ttu-id="0c318-111">Une déclaration de classe est un plan utilisé pour créer des instances d’objets au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c318-111">A class declaration is a blueprint used to create instances of objects at run time.</span></span> <span data-ttu-id="0c318-112">Lorsque vous définissez une classe, le nom de la classe est le nom du type.</span><span class="sxs-lookup"><span data-stu-id="0c318-112">When you define a class, the class name is the name of the type.</span></span> <span data-ttu-id="0c318-113">Par exemple, si vous déclarez une classe nommée **Device** et que vous initialisez une variable `$dev` sur une nouvelle instance de **Device** , `$dev` est un objet ou une instance de type **Device** .</span><span class="sxs-lookup"><span data-stu-id="0c318-113">For example, if you declare a class named **Device** and initialize a variable `$dev` to a new instance of **Device** , `$dev` is an object or instance of type **Device** .</span></span> <span data-ttu-id="0c318-114">Chaque instance de l' **appareil** peut avoir des valeurs différentes dans ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="0c318-114">Each instance of **Device** can have different values in its properties.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="0c318-115">Scénarios pris en charge</span><span class="sxs-lookup"><span data-stu-id="0c318-115">Supported scenarios</span></span>

- <span data-ttu-id="0c318-116">Définir des types personnalisés dans PowerShell à l’aide d’une sémantique de programmation orientée objet familière comme des classes, des propriétés, des méthodes, l’héritage, etc.</span><span class="sxs-lookup"><span data-stu-id="0c318-116">Define custom types in PowerShell using familiar object-oriented programming semantics like classes, properties, methods, inheritance, etc.</span></span>
- <span data-ttu-id="0c318-117">Déboguez les types à l’aide du langage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c318-117">Debug types using the PowerShell language.</span></span>
- <span data-ttu-id="0c318-118">Générer et gérer des exceptions à l’aide de mécanismes formels.</span><span class="sxs-lookup"><span data-stu-id="0c318-118">Generate and handle exceptions using formal mechanisms.</span></span>
- <span data-ttu-id="0c318-119">Définir les ressources DSC et leurs types associés à l’aide du langage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c318-119">Define DSC resources and their associated types by using the PowerShell language.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c318-120">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c318-120">Syntax</span></span>

<span data-ttu-id="0c318-121">Les classes sont déclarées à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="0c318-121">Classes are declared using the following syntax:</span></span>

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

<span data-ttu-id="0c318-122">Les classes sont instanciées à l’aide de l’une des syntaxes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c318-122">Classes are instantiated using either of the following syntaxes:</span></span>

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> <span data-ttu-id="0c318-123">Lorsque vous utilisez la `[<class-name>]::new()` syntaxe, les crochets autour du nom de la classe sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="0c318-123">When using the `[<class-name>]::new()` syntax, brackets around the class name are mandatory.</span></span> <span data-ttu-id="0c318-124">Les crochets signalent une définition de type pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c318-124">The brackets signal a type definition for PowerShell.</span></span>

### <a name="example-syntax-and-usage"></a><span data-ttu-id="0c318-125">Exemple de syntaxe et d’utilisation</span><span class="sxs-lookup"><span data-stu-id="0c318-125">Example syntax and usage</span></span>

<span data-ttu-id="0c318-126">Cet exemple montre la syntaxe minimale nécessaire pour créer une classe utilisable.</span><span class="sxs-lookup"><span data-stu-id="0c318-126">This example shows the minimum syntax needed to create a usable class.</span></span>

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a><span data-ttu-id="0c318-127">Propriétés de la classe</span><span class="sxs-lookup"><span data-stu-id="0c318-127">Class properties</span></span>

<span data-ttu-id="0c318-128">Les propriétés sont des variables déclarées au niveau de la portée de la classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-128">Properties are variables declared at class scope.</span></span> <span data-ttu-id="0c318-129">Une propriété peut être de n’importe quel type intégré ou d’une instance d’une autre classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-129">A property may be of any built-in type or an instance of another class.</span></span> <span data-ttu-id="0c318-130">Les classes n’ont aucune restriction quant au nombre de propriétés qu’elles possèdent.</span><span class="sxs-lookup"><span data-stu-id="0c318-130">Classes have no restriction in the number of properties they have.</span></span>

### <a name="example-class-with-simple-properties"></a><span data-ttu-id="0c318-131">Exemple de classe avec des propriétés simples</span><span class="sxs-lookup"><span data-stu-id="0c318-131">Example class with simple properties</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a><span data-ttu-id="0c318-132">Exemples de types complexes dans les propriétés de classe</span><span class="sxs-lookup"><span data-stu-id="0c318-132">Example complex types in class properties</span></span>

<span data-ttu-id="0c318-133">Cet exemple définit une classe de **rack** vide à l’aide de la classe **Device** .</span><span class="sxs-lookup"><span data-stu-id="0c318-133">This example defines an empty **Rack** class using the **Device** class.</span></span> <span data-ttu-id="0c318-134">Les exemples ci-dessous montrent comment ajouter des appareils au rack et comment commencer avec un rack préchargé.</span><span class="sxs-lookup"><span data-stu-id="0c318-134">The examples, following this one, show how to add devices to the rack and how to start with a pre-loaded rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a><span data-ttu-id="0c318-135">Méthodes de classe</span><span class="sxs-lookup"><span data-stu-id="0c318-135">Class methods</span></span>

<span data-ttu-id="0c318-136">Les méthodes définissent les actions qu’une classe peut effectuer.</span><span class="sxs-lookup"><span data-stu-id="0c318-136">Methods define the actions that a class can perform.</span></span> <span data-ttu-id="0c318-137">Les méthodes peuvent accepter des paramètres qui fournissent des données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="0c318-137">Methods may take parameters that provide input data.</span></span> <span data-ttu-id="0c318-138">Les méthodes peuvent retourner une sortie.</span><span class="sxs-lookup"><span data-stu-id="0c318-138">Methods can return output.</span></span> <span data-ttu-id="0c318-139">Les données retournées par une méthode peuvent être de n’importe quel type de données défini.</span><span class="sxs-lookup"><span data-stu-id="0c318-139">Data returned by a method can be any defined data type.</span></span>

<span data-ttu-id="0c318-140">Lors de la définition d’une méthode pour une classe, vous référencez l’objet de classe actuel à l’aide de la `$this` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="0c318-140">When defining a method for a class, you reference the current class object by using the `$this` automatic variable.</span></span> <span data-ttu-id="0c318-141">Cela vous permet d’accéder aux propriétés et autres méthodes définies dans la classe actuelle.</span><span class="sxs-lookup"><span data-stu-id="0c318-141">This allows you to access properties and other methods defined in the current class.</span></span>

### <a name="example-simple-class-with-properties-and-methods"></a><span data-ttu-id="0c318-142">Exemple de classe simple avec des propriétés et des méthodes</span><span class="sxs-lookup"><span data-stu-id="0c318-142">Example simple class with properties and methods</span></span>

<span data-ttu-id="0c318-143">Extension de la classe **rack** pour ajouter et supprimer des périphériques.</span><span class="sxs-lookup"><span data-stu-id="0c318-143">Extending the **Rack** class to add and remove devices to or from it.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a><span data-ttu-id="0c318-144">Sortie dans les méthodes de classe</span><span class="sxs-lookup"><span data-stu-id="0c318-144">Output in class methods</span></span>

<span data-ttu-id="0c318-145">Les méthodes doivent avoir un type de retour défini.</span><span class="sxs-lookup"><span data-stu-id="0c318-145">Methods should have a return type defined.</span></span> <span data-ttu-id="0c318-146">Si une méthode ne retourne pas de sortie, le type de sortie doit être `[void]` .</span><span class="sxs-lookup"><span data-stu-id="0c318-146">If a method doesn't return output, then the output type should be `[void]`.</span></span>

<span data-ttu-id="0c318-147">Dans les méthodes de classe, aucun objet n’est envoyé au pipeline, à l’exception de ceux mentionnés dans l' `return` instruction.</span><span class="sxs-lookup"><span data-stu-id="0c318-147">In class methods, no objects get sent to the pipeline except those mentioned in the `return` statement.</span></span> <span data-ttu-id="0c318-148">Il n’y a pas de sortie accidentelle vers le pipeline à partir du code.</span><span class="sxs-lookup"><span data-stu-id="0c318-148">There's no accidental output to the pipeline from the code.</span></span>

> [!NOTE]
> <span data-ttu-id="0c318-149">Cette approche est fondamentalement différente de la façon dont les fonctions PowerShell gèrent la sortie, où tout est dirigé vers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="0c318-149">This is fundamentally different from how PowerShell functions handle output, where everything goes to the pipeline.</span></span>

<span data-ttu-id="0c318-150">Les erreurs sans fin d’écriture écrites dans le flux d’erreur à partir d’une méthode de classe ne sont pas transmises.</span><span class="sxs-lookup"><span data-stu-id="0c318-150">Non-terminating errors written to the error stream from inside a class method are not passed through.</span></span> <span data-ttu-id="0c318-151">Vous devez utiliser `throw` pour mettre en surface une erreur de fin.</span><span class="sxs-lookup"><span data-stu-id="0c318-151">You must use `throw` to surface a terminating error.</span></span>
<span data-ttu-id="0c318-152">À l’aide des `Write-*` applets de commande, vous pouvez toujours écrire dans les flux de sortie de PowerShell à partir d’une méthode de classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-152">Using the `Write-*` cmdlets, you can still write to PowerShell's output streams from within a class method.</span></span> <span data-ttu-id="0c318-153">Toutefois, cela doit être évité afin que la méthode émette des objets en utilisant uniquement l' `return` instruction.</span><span class="sxs-lookup"><span data-stu-id="0c318-153">However, this should be avoided so that the method emits objects using only the `return` statement.</span></span>

### <a name="method-output"></a><span data-ttu-id="0c318-154">Sortie de la méthode</span><span class="sxs-lookup"><span data-stu-id="0c318-154">Method output</span></span>

<span data-ttu-id="0c318-155">Cet exemple montre aucune sortie accidentelle vers le pipeline à partir des méthodes de classe, sauf sur l' `return` instruction.</span><span class="sxs-lookup"><span data-stu-id="0c318-155">This example demonstrates no accidental output to the pipeline from class methods, except on the `return` statement.</span></span>

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a><span data-ttu-id="0c318-156">Constructeur</span><span class="sxs-lookup"><span data-stu-id="0c318-156">Constructor</span></span>

<span data-ttu-id="0c318-157">Les constructeurs vous permettent de définir des valeurs par défaut et de valider la logique d’objet au moment de la création de l’instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-157">Constructors enable you to set default values and validate object logic at the moment of creating the instance of the class.</span></span> <span data-ttu-id="0c318-158">Les constructeurs ont le même nom que la classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-158">Constructors have the same name as the class.</span></span> <span data-ttu-id="0c318-159">Les constructeurs peuvent avoir des arguments pour initialiser les données membres du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="0c318-159">Constructors might have arguments, to initialize the data members of the new object.</span></span>

<span data-ttu-id="0c318-160">La classe peut avoir zéro, un ou plusieurs constructeurs définis.</span><span class="sxs-lookup"><span data-stu-id="0c318-160">The class can have zero or more constructors defined.</span></span> <span data-ttu-id="0c318-161">Si aucun constructeur n’est défini, la classe reçoit un constructeur sans paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c318-161">If no constructor is defined, the class is given a default parameterless constructor.</span></span> <span data-ttu-id="0c318-162">Ce constructeur initialise tous les membres avec leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c318-162">This constructor initializes all members to their default values.</span></span> <span data-ttu-id="0c318-163">Les types d’objets et les chaînes reçoivent des valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="0c318-163">Object types and strings are given null values.</span></span> <span data-ttu-id="0c318-164">Quand vous définissez un constructeur, aucun constructeur sans paramètre par défaut n’est créé.</span><span class="sxs-lookup"><span data-stu-id="0c318-164">When you define constructor, no default parameterless constructor is created.</span></span> <span data-ttu-id="0c318-165">Créez un constructeur sans paramètre si vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="0c318-165">Create a parameterless constructor if one is needed.</span></span>

### <a name="constructor-basic-syntax"></a><span data-ttu-id="0c318-166">Syntaxe de base du constructeur</span><span class="sxs-lookup"><span data-stu-id="0c318-166">Constructor basic syntax</span></span>

<span data-ttu-id="0c318-167">Dans cet exemple, la classe d’appareil est définie avec des propriétés et un constructeur.</span><span class="sxs-lookup"><span data-stu-id="0c318-167">In this example, the Device class is defined with properties and a constructor.</span></span>
<span data-ttu-id="0c318-168">Pour utiliser cette classe, l’utilisateur doit fournir des valeurs pour les paramètres répertoriés dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="0c318-168">To use this class, the user is required to provide values for the parameters listed in the constructor.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a><span data-ttu-id="0c318-169">Exemple avec plusieurs constructeurs</span><span class="sxs-lookup"><span data-stu-id="0c318-169">Example with multiple constructors</span></span>

<span data-ttu-id="0c318-170">Dans cet exemple, la classe d' **appareil** est définie avec des propriétés, un constructeur par défaut et un constructeur pour initialiser l’instance.</span><span class="sxs-lookup"><span data-stu-id="0c318-170">In this example, the **Device** class is defined with properties, a default constructor, and a constructor to initialize the instance.</span></span>

<span data-ttu-id="0c318-171">Le constructeur par défaut affecte la valeur **non définie** à la **personnalisation** et laisse le **modèle** et la **référence SKU de fournisseur** avec des valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="0c318-171">The default constructor sets the **brand** to **Undefined** , and leaves **model** and **vendor-sku** with null values.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a><span data-ttu-id="0c318-172">Attribut hidden</span><span class="sxs-lookup"><span data-stu-id="0c318-172">Hidden attribute</span></span>

<span data-ttu-id="0c318-173">L' `hidden` attribut masque une propriété ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="0c318-173">The `hidden` attribute hides a property or method.</span></span> <span data-ttu-id="0c318-174">La propriété ou la méthode est toujours accessible à l’utilisateur et est disponible dans toutes les étendues dans lesquelles l’objet est disponible.</span><span class="sxs-lookup"><span data-stu-id="0c318-174">The property or method is still accessible to the user and is available in all scopes in which the object is available.</span></span> <span data-ttu-id="0c318-175">Les membres masqués sont masqués dans l’applet de commande `Get-Member` et ne peuvent pas être affichés à l’aide de la saisie semi-automatique via la touche Tab ou IntelliSense en dehors</span><span class="sxs-lookup"><span data-stu-id="0c318-175">Hidden members are hidden from the `Get-Member` cmdlet and can't be displayed using tab completion or IntelliSense outside the class definition.</span></span>

<span data-ttu-id="0c318-176">Pour plus d’informations, consultez [About_hidden](About_hidden.md).</span><span class="sxs-lookup"><span data-stu-id="0c318-176">For more information, see [About_hidden](About_hidden.md).</span></span>

### <a name="example-using-hidden-attributes"></a><span data-ttu-id="0c318-177">Exemple utilisant des attributs masqués</span><span class="sxs-lookup"><span data-stu-id="0c318-177">Example using hidden attributes</span></span>

<span data-ttu-id="0c318-178">Lors de la création d’un objet **rack** , le nombre d’emplacements pour les périphériques est une valeur fixe qui ne doit pas être modifiée à tout moment.</span><span class="sxs-lookup"><span data-stu-id="0c318-178">When a **Rack** object is created, the number of slots for devices is a fixed value that shouldn't be changed at any time.</span></span> <span data-ttu-id="0c318-179">Cette valeur est connue au moment de la création.</span><span class="sxs-lookup"><span data-stu-id="0c318-179">This value is known at creation time.</span></span>

<span data-ttu-id="0c318-180">L’utilisation de l’attribut hidden permet au développeur de conserver le nombre d’emplacements masqués et d’empêcher la modification non intentionnelle de la taille du rack.</span><span class="sxs-lookup"><span data-stu-id="0c318-180">Using the hidden attribute allows the developer to keep the number of slots hidden and prevents unintentional changes the size of the rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

<span data-ttu-id="0c318-181">La propriété des **emplacements** d’avis n’est pas affichée dans la `$r1` sortie.</span><span class="sxs-lookup"><span data-stu-id="0c318-181">Notice **Slots** property isn't shown in `$r1` output.</span></span> <span data-ttu-id="0c318-182">Toutefois, la taille a été modifiée par le constructeur.</span><span class="sxs-lookup"><span data-stu-id="0c318-182">However, the size was changed by the constructor.</span></span>

## <a name="static-attribute"></a><span data-ttu-id="0c318-183">Attribut statique</span><span class="sxs-lookup"><span data-stu-id="0c318-183">Static attribute</span></span>

<span data-ttu-id="0c318-184">L' `static` attribut définit une propriété ou une méthode qui existe dans la classe et qui n’a pas besoin d’une instance.</span><span class="sxs-lookup"><span data-stu-id="0c318-184">The `static` attribute defines a property or a method that exists in the class and needs no instance.</span></span>

<span data-ttu-id="0c318-185">Une propriété statique est toujours disponible, indépendamment de l’instanciation de classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-185">A static property is always available, independent of class instantiation.</span></span> <span data-ttu-id="0c318-186">Une propriété statique est partagée entre toutes les instances de la classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-186">A static property is shared across all instances of the class.</span></span> <span data-ttu-id="0c318-187">Une méthode statique est toujours disponible.</span><span class="sxs-lookup"><span data-stu-id="0c318-187">A static method is available always.</span></span> <span data-ttu-id="0c318-188">Toutes les propriétés statiques sont actives pour l’intégralité de l’étendue de la session.</span><span class="sxs-lookup"><span data-stu-id="0c318-188">All static properties live for the entire session span.</span></span>

### <a name="example-using-static-attributes-and-methods"></a><span data-ttu-id="0c318-189">Exemple utilisant des méthodes et des attributs statiques</span><span class="sxs-lookup"><span data-stu-id="0c318-189">Example using static attributes and methods</span></span>

<span data-ttu-id="0c318-190">Supposons que les racks instanciés ici existent dans votre centre de données.</span><span class="sxs-lookup"><span data-stu-id="0c318-190">Assume the racks instantiated here exist in your data center.</span></span> <span data-ttu-id="0c318-191">Par conséquent, vous aimeriez effectuer le suivi des racks dans votre code.</span><span class="sxs-lookup"><span data-stu-id="0c318-191">So, you would like to keep track of the racks in your code.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a><span data-ttu-id="0c318-192">Le test de la propriété et de la méthode statiques existe</span><span class="sxs-lookup"><span data-stu-id="0c318-192">Testing static property and method exist</span></span>

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

<span data-ttu-id="0c318-193">Notez que le nombre de racks augmente chaque fois que vous exécutez cet exemple.</span><span class="sxs-lookup"><span data-stu-id="0c318-193">Notice that the number of racks increases each time you run this example.</span></span>

## <a name="property-validation-attributes"></a><span data-ttu-id="0c318-194">Attributs de validation de propriété</span><span class="sxs-lookup"><span data-stu-id="0c318-194">Property validation attributes</span></span>

<span data-ttu-id="0c318-195">Les attributs de validation vous permettent de vérifier que les valeurs affectées aux propriétés répondent aux spécifications définies.</span><span class="sxs-lookup"><span data-stu-id="0c318-195">Validation attributes allow you to test that values given to properties meet defined requirements.</span></span> <span data-ttu-id="0c318-196">La validation est déclenchée au moment où la valeur est affectée.</span><span class="sxs-lookup"><span data-stu-id="0c318-196">Validation is triggered the moment that the value is assigned.</span></span> <span data-ttu-id="0c318-197">Consultez [about_Functions_Advanced_Parameters](about_functions_advanced_parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0c318-197">See [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span></span>

### <a name="example-using-validation-attributes"></a><span data-ttu-id="0c318-198">Exemple utilisant des attributs de validation</span><span class="sxs-lookup"><span data-stu-id="0c318-198">Example using validation attributes</span></span>

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="0c318-199">Héritage dans les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c318-199">Inheritance in PowerShell classes</span></span>

<span data-ttu-id="0c318-200">Vous pouvez étendre une classe en créant une nouvelle classe qui dérive d’une classe existante.</span><span class="sxs-lookup"><span data-stu-id="0c318-200">You can extend a class by creating a new class that derives from an existing class.</span></span> <span data-ttu-id="0c318-201">La classe dérivée hérite des propriétés de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="0c318-201">The derived class inherits the properties of the base class.</span></span> <span data-ttu-id="0c318-202">Vous pouvez ajouter ou remplacer des méthodes et des propriétés selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="0c318-202">You can add or override methods and properties as required.</span></span>

<span data-ttu-id="0c318-203">PowerShell ne prend pas en charge l’héritage multiple.</span><span class="sxs-lookup"><span data-stu-id="0c318-203">PowerShell does not support multiple inheritance.</span></span> <span data-ttu-id="0c318-204">Les classes ne peuvent pas hériter de plusieurs classes.</span><span class="sxs-lookup"><span data-stu-id="0c318-204">Classes cannot inherit from more than one class.</span></span> <span data-ttu-id="0c318-205">Toutefois, vous pouvez utiliser des interfaces à cet effet.</span><span class="sxs-lookup"><span data-stu-id="0c318-205">However, you can use interfaces for that purpose.</span></span>

<span data-ttu-id="0c318-206">L’implémentation de l’héritage est définie par l' `:` opérateur, ce qui signifie étendre cette classe ou implémenter ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="0c318-206">Inheritance implementation is defined by the `:` operator; which means to extend this class or implements these interfaces.</span></span> <span data-ttu-id="0c318-207">La classe dérivée doit toujours être la plus à gauche dans la déclaration de classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-207">The derived class should always be leftmost in the class declaration.</span></span>

### <a name="example-using-simple-inheritance-syntax"></a><span data-ttu-id="0c318-208">Exemple utilisant une syntaxe d’héritage simple</span><span class="sxs-lookup"><span data-stu-id="0c318-208">Example using simple inheritance syntax</span></span>

<span data-ttu-id="0c318-209">Cet exemple montre la syntaxe d’héritage de classe PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="0c318-209">This example shows the simple PowerShell class inheritance syntax.</span></span>

```powershell
Class Derived : Base {...}
```

<span data-ttu-id="0c318-210">Cet exemple montre l’héritage avec une déclaration d’interface venant après la classe de base.</span><span class="sxs-lookup"><span data-stu-id="0c318-210">This example shows inheritance with an interface declaration coming after the base class.</span></span>

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a><span data-ttu-id="0c318-211">Exemple d’héritage simple dans les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c318-211">Example of simple inheritance in PowerShell classes</span></span>

<span data-ttu-id="0c318-212">Dans cet exemple, les classes **rack** et **Device** utilisées dans les exemples précédents sont mieux définies pour : Évitez les répétitions de propriété, mieux Alignez les propriétés communes et réutilisez la logique métier courante.</span><span class="sxs-lookup"><span data-stu-id="0c318-212">In this example the **Rack** and **Device** classes used in the previous examples are better defined to: avoid property repetitions, better align common properties, and reuse common business logic.</span></span>

<span data-ttu-id="0c318-213">La plupart des objets dans le centre de données sont des ressources de l’entreprise, ce qui est judicieux de commencer à les suivre en tant que ressources.</span><span class="sxs-lookup"><span data-stu-id="0c318-213">Most objects in the data center are company assets, which makes sense to start tracking them as assets.</span></span> <span data-ttu-id="0c318-214">Les types d’appareils sont définis par l' `DeviceType` énumération, consultez [about_Enum](about_Enum.md) pour plus d’informations sur les énumérations.</span><span class="sxs-lookup"><span data-stu-id="0c318-214">Device types are defined by the `DeviceType` enumeration, see [about_Enum](about_Enum.md) for details on enumerations.</span></span>

<span data-ttu-id="0c318-215">Dans notre exemple, nous définissons uniquement `Rack` et, `ComputeServer` les deux extensions de la `Device` classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-215">In our example, we're only defining `Rack` and `ComputeServer`; both extensions to the `Device` class.</span></span>

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a><span data-ttu-id="0c318-216">Appel des constructeurs de classe de base</span><span class="sxs-lookup"><span data-stu-id="0c318-216">Calling base class constructors</span></span>

<span data-ttu-id="0c318-217">Pour appeler un constructeur de classe de base à partir d’une sous-classe, ajoutez le `base` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0c318-217">To invoke a base class constructor from a subclass, add the `base` keyword.</span></span>

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a><span data-ttu-id="0c318-218">Appeler des méthodes de classe de base</span><span class="sxs-lookup"><span data-stu-id="0c318-218">Invoke base class methods</span></span>

<span data-ttu-id="0c318-219">Pour substituer les méthodes existantes dans les sous-classes, déclarez les méthodes à l’aide du même nom et de la même signature.</span><span class="sxs-lookup"><span data-stu-id="0c318-219">To override existing methods in subclasses, declare methods using the same name and signature.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

<span data-ttu-id="0c318-220">Pour appeler des méthodes de la classe de base à partir d’implémentations substituées, effectuez un cast vers la classe de base ([BaseClass] $this) lors de l’appel.</span><span class="sxs-lookup"><span data-stu-id="0c318-220">To call base class methods from overridden implementations, cast to the base class ([baseclass]$this) on invocation.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a><span data-ttu-id="0c318-221">Hériter d’interfaces</span><span class="sxs-lookup"><span data-stu-id="0c318-221">Inheriting from interfaces</span></span>

<span data-ttu-id="0c318-222">Les classes PowerShell peuvent implémenter une interface à l’aide de la même syntaxe d’héritage que celle utilisée pour étendre les classes de base.</span><span class="sxs-lookup"><span data-stu-id="0c318-222">PowerShell classes can implement an interface using the same inheritance syntax used to extend base classes.</span></span> <span data-ttu-id="0c318-223">Étant donné que les interfaces autorisent plusieurs héritages, une classe PowerShell qui implémente une interface peut hériter de plusieurs types, en séparant les noms de type après le signe deux-points ( `:` ) par des virgules ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="0c318-223">Because interfaces allow multiple inheritance, a PowerShell class implementing an interface may inherit from multiple types, by separating the type names after the colon (`:`) with commas (`,`).</span></span> <span data-ttu-id="0c318-224">Une classe PowerShell qui implémente une interface doit implémenter tous les membres de cette interface.</span><span class="sxs-lookup"><span data-stu-id="0c318-224">A PowerShell class that implements an interface must implement all the members of that interface.</span></span> <span data-ttu-id="0c318-225">L’omission des membres de l’interface d’implémentation provoque une erreur d’analyse dans le script.</span><span class="sxs-lookup"><span data-stu-id="0c318-225">Omitting the implemention interface members causes a parse-time error in the script.</span></span>

> [!NOTE]
> <span data-ttu-id="0c318-226">PowerShell ne prend pas actuellement en charge la déclaration de nouvelles interfaces dans le script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c318-226">PowerShell does not currently support declaring new interfaces in PowerShell script.</span></span>

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a><span data-ttu-id="0c318-227">Importation de classes à partir d’un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c318-227">Importing classes from a PowerShell module</span></span>

<span data-ttu-id="0c318-228">`Import-Module` et l' `#requires` instruction importent uniquement les fonctions de module, les alias et les variables, comme défini par le module.</span><span class="sxs-lookup"><span data-stu-id="0c318-228">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="0c318-229">Les classes ne sont pas importées.</span><span class="sxs-lookup"><span data-stu-id="0c318-229">Classes are not imported.</span></span> <span data-ttu-id="0c318-230">L' `using module` instruction importe les classes définies dans le module.</span><span class="sxs-lookup"><span data-stu-id="0c318-230">The `using module` statement imports the classes defined in the module.</span></span> <span data-ttu-id="0c318-231">Si le module n’est pas chargé dans la session active, l' `using` instruction échoue.</span><span class="sxs-lookup"><span data-stu-id="0c318-231">If the module isn't loaded in the current session, the `using` statement fails.</span></span> <span data-ttu-id="0c318-232">Pour plus d’informations sur l' `using` instruction, consultez [about_Using](about_Using.md).</span><span class="sxs-lookup"><span data-stu-id="0c318-232">For more information about the `using` statement, see [about_Using](about_Using.md).</span></span>

## <a name="the-psreference-type-is-not-supported-with-class-members"></a><span data-ttu-id="0c318-233">Le type PSReference n’est pas pris en charge avec les membres de classe</span><span class="sxs-lookup"><span data-stu-id="0c318-233">The PSReference type is not supported with class members</span></span>

<span data-ttu-id="0c318-234">L’utilisation de la `[ref]` conversion de type avec un membre de classe échoue en silence.</span><span class="sxs-lookup"><span data-stu-id="0c318-234">Using the `[ref]` type-cast with a class member silently fails.</span></span> <span data-ttu-id="0c318-235">Les API qui utilisent `[ref]` des paramètres ne peuvent pas être utilisées avec des membres de classe.</span><span class="sxs-lookup"><span data-stu-id="0c318-235">APIs that use `[ref]` parameters cannot be used with class members.</span></span> <span data-ttu-id="0c318-236">**PSReference** a été conçu pour prendre en charge les objets com.</span><span class="sxs-lookup"><span data-stu-id="0c318-236">The **PSReference** was designed to support COM objects.</span></span> <span data-ttu-id="0c318-237">Les objets COM ont des cas où vous devez passer une valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="0c318-237">COM objects have cases where you need to pass a value in by reference.</span></span>

<span data-ttu-id="0c318-238">Pour plus d’informations sur le `[ref]` type, consultez [PSReference, classe](/dotnet/api/system.management.automation.psreference).</span><span class="sxs-lookup"><span data-stu-id="0c318-238">For more information about the `[ref]` type, see [PSReference Class](/dotnet/api/system.management.automation.psreference).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c318-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c318-239">See also</span></span>

- [<span data-ttu-id="0c318-240">About_hidden</span><span class="sxs-lookup"><span data-stu-id="0c318-240">About_hidden</span></span>](About_hidden.md)
- [<span data-ttu-id="0c318-241">À propos de l’énumération</span><span class="sxs-lookup"><span data-stu-id="0c318-241">about_Enum</span></span>](about_Enum.md)
- [<span data-ttu-id="0c318-242">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="0c318-242">about_Language_Keywords</span></span>](about_language_keywords.md)
- [<span data-ttu-id="0c318-243">about_Methods</span><span class="sxs-lookup"><span data-stu-id="0c318-243">about_Methods</span></span>](about_methods.md)
- [<span data-ttu-id="0c318-244">about_Using</span><span class="sxs-lookup"><span data-stu-id="0c318-244">about_Using</span></span>](about_using.md)
