---
description: Décrit comment vous pouvez utiliser des classes pour créer vos propres types personnalisés.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des classes
ms.openlocfilehash: 99b72762469032cc24f21d957600b67d0a0db292
ms.sourcegitcommit: 16d62a98449e3ddaf8d7c65bc1848ede1fd8a3e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "93206274"
---
# <a name="about-classes"></a>À propos des classes

## <a name="short-description"></a>Description courte
Décrit comment vous pouvez utiliser des classes pour créer vos propres types personnalisés.

## <a name="long-description"></a>Description longue

PowerShell 5,0 ajoute une syntaxe formelle pour définir des classes et d’autres types définis par l’utilisateur. L’ajout de classes permet aux développeurs et aux professionnels de l’informatique d’adopter PowerShell pour un plus grand nombre de cas d’utilisation. Il simplifie le développement des artefacts PowerShell et accélère la couverture des surfaces de gestion.

Une déclaration de classe est un plan utilisé pour créer des instances d’objets au moment de l’exécution. Lorsque vous définissez une classe, le nom de la classe est le nom du type. Par exemple, si vous déclarez une classe nommée **Device** et que vous initialisez une variable `$dev` sur une nouvelle instance de **Device** , `$dev` est un objet ou une instance de type **Device** . Chaque instance de l' **appareil** peut avoir des valeurs différentes dans ses propriétés.

## <a name="supported-scenarios"></a>Scénarios pris en charge

- Définir des types personnalisés dans PowerShell à l’aide d’une sémantique de programmation orientée objet familière comme des classes, des propriétés, des méthodes, l’héritage, etc.
- Déboguez les types à l’aide du langage PowerShell.
- Générer et gérer des exceptions à l’aide de mécanismes formels.
- Définir les ressources DSC et leurs types associés à l’aide du langage PowerShell.

## <a name="syntax"></a>Syntaxe

Les classes sont déclarées à l’aide de la syntaxe suivante :

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

Les classes sont instanciées à l’aide de l’une des syntaxes suivantes :

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> Lorsque vous utilisez la `[<class-name>]::new()` syntaxe, les crochets autour du nom de la classe sont obligatoires. Les crochets signalent une définition de type pour PowerShell.

### <a name="example-syntax-and-usage"></a>Exemple de syntaxe et d’utilisation

Cet exemple montre la syntaxe minimale nécessaire pour créer une classe utilisable.

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

## <a name="class-properties"></a>Propriétés de la classe

Les propriétés sont des variables déclarées au niveau de la portée de la classe. Une propriété peut être de n’importe quel type intégré ou d’une instance d’une autre classe. Les classes n’ont aucune restriction quant au nombre de propriétés qu’elles possèdent.

### <a name="example-class-with-simple-properties"></a>Exemple de classe avec des propriétés simples

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

### <a name="example-complex-types-in-class-properties"></a>Exemples de types complexes dans les propriétés de classe

Cet exemple définit une classe de **rack** vide à l’aide de la classe **Device** . Les exemples ci-dessous montrent comment ajouter des appareils au rack et comment commencer avec un rack préchargé.

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

## <a name="class-methods"></a>Méthodes de classe

Les méthodes définissent les actions qu’une classe peut effectuer. Les méthodes peuvent accepter des paramètres qui fournissent des données d’entrée. Les méthodes peuvent retourner une sortie. Les données retournées par une méthode peuvent être de n’importe quel type de données défini.

Lors de la définition d’une méthode pour une classe, vous référencez l’objet de classe actuel à l’aide de la `$this` variable automatique. Cela vous permet d’accéder aux propriétés et autres méthodes définies dans la classe actuelle.

### <a name="example-simple-class-with-properties-and-methods"></a>Exemple de classe simple avec des propriétés et des méthodes

Extension de la classe **rack** pour ajouter et supprimer des périphériques.

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

## <a name="output-in-class-methods"></a>Sortie dans les méthodes de classe

Les méthodes doivent avoir un type de retour défini. Si une méthode ne retourne pas de sortie, le type de sortie doit être `[void]` .

Dans les méthodes de classe, aucun objet n’est envoyé au pipeline, à l’exception de ceux mentionnés dans l' `return` instruction. Il n’y a pas de sortie accidentelle vers le pipeline à partir du code.

> [!NOTE]
> Cette approche est fondamentalement différente de la façon dont les fonctions PowerShell gèrent la sortie, où tout est dirigé vers le pipeline.

Les erreurs sans fin d’écriture écrites dans le flux d’erreur à partir d’une méthode de classe ne sont pas transmises. Vous devez utiliser `throw` pour mettre en surface une erreur de fin.
À l’aide des `Write-*` applets de commande, vous pouvez toujours écrire dans les flux de sortie de PowerShell à partir d’une méthode de classe. Toutefois, cela doit être évité afin que la méthode émette des objets en utilisant uniquement l' `return` instruction.

### <a name="method-output"></a>Sortie de la méthode

Cet exemple montre aucune sortie accidentelle vers le pipeline à partir des méthodes de classe, sauf sur l' `return` instruction.

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

## <a name="constructor"></a>Constructeur

Les constructeurs vous permettent de définir des valeurs par défaut et de valider la logique d’objet au moment de la création de l’instance de la classe. Les constructeurs ont le même nom que la classe. Les constructeurs peuvent avoir des arguments pour initialiser les données membres du nouvel objet.

La classe peut avoir zéro, un ou plusieurs constructeurs définis. Si aucun constructeur n’est défini, la classe reçoit un constructeur sans paramètre par défaut. Ce constructeur initialise tous les membres avec leurs valeurs par défaut. Les types d’objets et les chaînes reçoivent des valeurs NULL. Quand vous définissez un constructeur, aucun constructeur sans paramètre par défaut n’est créé. Créez un constructeur sans paramètre si vous en avez besoin.

### <a name="constructor-basic-syntax"></a>Syntaxe de base du constructeur

Dans cet exemple, la classe d’appareil est définie avec des propriétés et un constructeur.
Pour utiliser cette classe, l’utilisateur doit fournir des valeurs pour les paramètres répertoriés dans le constructeur.

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

### <a name="example-with-multiple-constructors"></a>Exemple avec plusieurs constructeurs

Dans cet exemple, la classe d' **appareil** est définie avec des propriétés, un constructeur par défaut et un constructeur pour initialiser l’instance.

Le constructeur par défaut affecte la valeur **non définie** à la **personnalisation** et laisse le **modèle** et la **référence SKU de fournisseur** avec des valeurs NULL.

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

## <a name="hidden-attribute"></a>Attribut hidden

L' `hidden` attribut masque une propriété ou une méthode. La propriété ou la méthode est toujours accessible à l’utilisateur et est disponible dans toutes les étendues dans lesquelles l’objet est disponible. Les membres masqués sont masqués dans l’applet de commande `Get-Member` et ne peuvent pas être affichés à l’aide de la saisie semi-automatique via la touche Tab ou IntelliSense en dehors

Pour plus d’informations, consultez [About_hidden](About_hidden.md).

### <a name="example-using-hidden-attributes"></a>Exemple utilisant des attributs masqués

Lors de la création d’un objet **rack** , le nombre d’emplacements pour les périphériques est une valeur fixe qui ne doit pas être modifiée à tout moment. Cette valeur est connue au moment de la création.

L’utilisation de l’attribut hidden permet au développeur de conserver le nombre d’emplacements masqués et d’empêcher la modification non intentionnelle de la taille du rack.

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

La propriété des **emplacements** d’avis n’est pas affichée dans la `$r1` sortie. Toutefois, la taille a été modifiée par le constructeur.

## <a name="static-attribute"></a>Attribut statique

L' `static` attribut définit une propriété ou une méthode qui existe dans la classe et qui n’a pas besoin d’une instance.

Une propriété statique est toujours disponible, indépendamment de l’instanciation de classe. Une propriété statique est partagée entre toutes les instances de la classe. Une méthode statique est toujours disponible. Toutes les propriétés statiques sont actives pour l’intégralité de l’étendue de la session.

### <a name="example-using-static-attributes-and-methods"></a>Exemple utilisant des méthodes et des attributs statiques

Supposons que les racks instanciés ici existent dans votre centre de données. Par conséquent, vous aimeriez effectuer le suivi des racks dans votre code.

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

### <a name="testing-static-property-and-method-exist"></a>Le test de la propriété et de la méthode statiques existe

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

Notez que le nombre de racks augmente chaque fois que vous exécutez cet exemple.

## <a name="property-validation-attributes"></a>Attributs de validation de propriété

Les attributs de validation vous permettent de vérifier que les valeurs affectées aux propriétés répondent aux spécifications définies. La validation est déclenchée au moment où la valeur est affectée. Consultez [about_Functions_Advanced_Parameters](about_functions_advanced_parameters.md).

### <a name="example-using-validation-attributes"></a>Exemple utilisant des attributs de validation

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

## <a name="inheritance-in-powershell-classes"></a>Héritage dans les classes PowerShell

Vous pouvez étendre une classe en créant une nouvelle classe qui dérive d’une classe existante. La classe dérivée hérite des propriétés de la classe de base. Vous pouvez ajouter ou remplacer des méthodes et des propriétés selon les besoins.

PowerShell ne prend pas en charge l’héritage multiple. Les classes ne peuvent pas hériter de plusieurs classes. Toutefois, vous pouvez utiliser des interfaces à cet effet.

L’implémentation de l’héritage est définie par l' `:` opérateur, ce qui signifie étendre cette classe ou implémenter ces interfaces. La classe dérivée doit toujours être la plus à gauche dans la déclaration de classe.

### <a name="example-using-simple-inheritance-syntax"></a>Exemple utilisant une syntaxe d’héritage simple

Cet exemple montre la syntaxe d’héritage de classe PowerShell simple.

```powershell
Class Derived : Base {...}
```

Cet exemple montre l’héritage avec une déclaration d’interface venant après la classe de base.

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a>Exemple d’héritage simple dans les classes PowerShell

Dans cet exemple, les classes **rack** et **Device** utilisées dans les exemples précédents sont mieux définies pour : Évitez les répétitions de propriété, mieux Alignez les propriétés communes et réutilisez la logique métier courante.

La plupart des objets dans le centre de données sont des ressources de l’entreprise, ce qui est judicieux de commencer à les suivre en tant que ressources. Les types d’appareils sont définis par l' `DeviceType` énumération, consultez [about_Enum](about_Enum.md) pour plus d’informations sur les énumérations.

Dans notre exemple, nous définissons uniquement `Rack` et, `ComputeServer` les deux extensions de la `Device` classe.

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

### <a name="calling-base-class-constructors"></a>Appel des constructeurs de classe de base

Pour appeler un constructeur de classe de base à partir d’une sous-classe, ajoutez le `base` mot clé.

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

### <a name="invoke-base-class-methods"></a>Appeler des méthodes de classe de base

Pour substituer les méthodes existantes dans les sous-classes, déclarez les méthodes à l’aide du même nom et de la même signature.

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

Pour appeler des méthodes de la classe de base à partir d’implémentations substituées, effectuez un cast vers la classe de base ([BaseClass] $this) lors de l’appel.

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

### <a name="inheriting-from-interfaces"></a>Hériter d’interfaces

Les classes PowerShell peuvent implémenter une interface à l’aide de la même syntaxe d’héritage que celle utilisée pour étendre les classes de base. Étant donné que les interfaces autorisent plusieurs héritages, une classe PowerShell qui implémente une interface peut hériter de plusieurs types, en séparant les noms de type après le signe deux-points ( `:` ) par des virgules ( `,` ). Une classe PowerShell qui implémente une interface doit implémenter tous les membres de cette interface. L’omission des membres de l’interface d’implémentation provoque une erreur d’analyse dans le script.

> [!NOTE]
> PowerShell ne prend pas actuellement en charge la déclaration de nouvelles interfaces dans le script PowerShell.

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

## <a name="importing-classes-from-a-powershell-module"></a>Importation de classes à partir d’un module PowerShell

`Import-Module` et l' `#requires` instruction importent uniquement les fonctions de module, les alias et les variables, comme défini par le module. Les classes ne sont pas importées. L' `using module` instruction importe les classes définies dans le module. Si le module n’est pas chargé dans la session active, l' `using` instruction échoue. Pour plus d’informations sur l' `using` instruction, consultez [about_Using](about_Using.md).

## <a name="the-psreference-type-is-not-supported-with-class-members"></a>Le type PSReference n’est pas pris en charge avec les membres de classe

L’utilisation de la `[ref]` conversion de type avec un membre de classe échoue en silence. Les API qui utilisent `[ref]` des paramètres ne peuvent pas être utilisées avec des membres de classe. **PSReference** a été conçu pour prendre en charge les objets com. Les objets COM ont des cas où vous devez passer une valeur par référence.

Pour plus d’informations sur le `[ref]` type, consultez [PSReference, classe](/dotnet/api/system.management.automation.psreference).

## <a name="see-also"></a>Voir aussi

- [About_hidden](About_hidden.md)
- [À propos de l’énumération](about_Enum.md)
- [about_Language_Keywords](about_language_keywords.md)
- [about_Methods](about_methods.md)
- [about_Using](about_using.md)
