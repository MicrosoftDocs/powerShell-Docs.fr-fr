---
description: Décrit comment utiliser des méthodes pour effectuer des actions sur des objets dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: cbeee3d7b840e33eb178513f4adeb22de02211e0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207310"
---
# <a name="about-methods"></a><span data-ttu-id="ee843-104">À propos des méthodes</span><span class="sxs-lookup"><span data-stu-id="ee843-104">About methods</span></span>

## <a name="short-description"></a><span data-ttu-id="ee843-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="ee843-105">Short description</span></span>
<span data-ttu-id="ee843-106">Décrit comment utiliser des méthodes pour effectuer des actions sur des objets dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee843-106">Describes how to use methods to perform actions on objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ee843-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="ee843-107">Long description</span></span>

<span data-ttu-id="ee843-108">PowerShell utilise des objets pour représenter les éléments dans les magasins de données ou l’état de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ee843-108">PowerShell uses objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="ee843-109">Par exemple, les objets FileInfo représentent les fichiers des lecteurs du système de fichiers et les objets ProcessInfo représentent les processus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ee843-109">For example, FileInfo objects represent the files in file system drives and ProcessInfo objects represent the processes on the computer.</span></span>

<span data-ttu-id="ee843-110">Les objets ont des propriétés, qui stockent des données sur l’objet et des méthodes qui vous permettent de modifier l’objet.</span><span class="sxs-lookup"><span data-stu-id="ee843-110">Objects have properties, which store data about the object, and methods that let you change the object.</span></span>

<span data-ttu-id="ee843-111">Une « méthode » est un ensemble d’instructions qui spécifient une action que vous pouvez effectuer sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="ee843-111">A "method" is a set of instructions that specify an action you can perform on the object.</span></span> <span data-ttu-id="ee843-112">Par exemple, l' `FileInfo` objet comprend la `CopyTo` méthode qui copie le fichier que l' `FileInfo` objet représente.</span><span class="sxs-lookup"><span data-stu-id="ee843-112">For example, the `FileInfo` object includes the `CopyTo` method that copies the file that the `FileInfo` object represents.</span></span>

<span data-ttu-id="ee843-113">Pour récupérer les méthodes de n’importe quel objet, utilisez l’applet de commande `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="ee843-113">To get the methods of any object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="ee843-114">Utilisez sa propriété **MemberType** avec la valeur « Method ».</span><span class="sxs-lookup"><span data-stu-id="ee843-114">Use its **MemberType** property with a value of "Method".</span></span> <span data-ttu-id="ee843-115">La commande suivante obtient les méthodes des objets processus.</span><span class="sxs-lookup"><span data-stu-id="ee843-115">The following command gets the methods of process objects.</span></span>

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

<span data-ttu-id="ee843-116">Pour exécuter ou « appeler » une méthode d’un objet, tapez un point (.), le nom de la méthode et un jeu de parenthèses « () ».</span><span class="sxs-lookup"><span data-stu-id="ee843-116">To perform or "invoke" a method of an object, type a dot (.), the method name, and a set of parentheses "()".</span></span> <span data-ttu-id="ee843-117">Si la méthode a des arguments, placez les valeurs d’argument à l’intérieur des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="ee843-117">If the method has arguments, place the argument values inside the parentheses.</span></span> <span data-ttu-id="ee843-118">Les parenthèses sont obligatoires pour chaque appel de méthode, même s’il n’y a pas d’arguments.</span><span class="sxs-lookup"><span data-stu-id="ee843-118">The parentheses are required for every method call, even when there are no arguments.</span></span> <span data-ttu-id="ee843-119">Si la méthode accepte plusieurs arguments, ceux-ci doivent être séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="ee843-119">If the method takes multiple arguments, they should be separated by commas.</span></span>

<span data-ttu-id="ee843-120">Par exemple, la commande suivante appelle la méthode Kill des processus pour terminer le processus du bloc-notes sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ee843-120">For example, the following command invokes the Kill method of processes to end the Notepad process on the computer.</span></span>

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

<span data-ttu-id="ee843-121">Cet exemple peut être réduit en combinant les instructions ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ee843-121">This example can be shortened by combining the above statements.</span></span>

```powershell
(Get-Process Notepad).Kill()
```

<span data-ttu-id="ee843-122">La `Get-Process` commande est placée entre parenthèses pour s’assurer qu’elle s’exécute avant l’appel de la méthode Kill.</span><span class="sxs-lookup"><span data-stu-id="ee843-122">The `Get-Process` command is enclosed in parentheses to ensure that it runs before the Kill method is invoked.</span></span> <span data-ttu-id="ee843-123">La `Kill` méthode est ensuite appelée sur l’objet retourné `Process` .</span><span class="sxs-lookup"><span data-stu-id="ee843-123">The `Kill` method is then invoked on the returned `Process` object.</span></span>

<span data-ttu-id="ee843-124">Une autre méthode très utile est la `Replace` méthode de chaînes.</span><span class="sxs-lookup"><span data-stu-id="ee843-124">Another very useful method is the `Replace` method of strings.</span></span> <span data-ttu-id="ee843-125">La `Replace` méthode remplace le texte dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ee843-125">The `Replace` method, replaces text within a string.</span></span> <span data-ttu-id="ee843-126">Dans l’exemple ci-dessous, le point (.) peut être placé immédiatement après le guillemet de fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="ee843-126">In the example below, the dot (.) can be placed immediately after the end quote of the string.</span></span>

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

<span data-ttu-id="ee843-127">Comme indiqué dans les exemples précédents, vous pouvez appeler une méthode sur un objet que vous avez obtenu à l’aide d’une commande, d’un objet dans une variable ou de tout ce qui produit un objet (par exemple, une chaîne entre guillemets).</span><span class="sxs-lookup"><span data-stu-id="ee843-127">As shown in the previous examples, you can invoke a method on an object that you get by using a command, an object in a variable, or anything that results in an object (like a string in quotes).</span></span>

<span data-ttu-id="ee843-128">À compter de PowerShell 4,0, l’appel de méthode à l’aide de noms de méthodes dynamiques est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ee843-128">Starting in PowerShell 4.0, method invocation by using dynamic method names is supported.</span></span>

### <a name="learning-about-methods"></a><span data-ttu-id="ee843-129">En savoir plus sur les méthodes</span><span class="sxs-lookup"><span data-stu-id="ee843-129">Learning about methods</span></span>

<span data-ttu-id="ee843-130">Pour rechercher les définitions des méthodes d’un objet, accédez à la rubrique d’aide relative au type d’objet dans MSDN et recherchez sa page de méthodes.</span><span class="sxs-lookup"><span data-stu-id="ee843-130">To find definitions of the methods of an object, go to help topic for the object type in MSDN and look for its methods page.</span></span> <span data-ttu-id="ee843-131">Par exemple, la page suivante décrit les méthodes de traitement des objets [System. Diagnostics. Process](/dotnet/api/system.diagnostics.process#methods).</span><span class="sxs-lookup"><span data-stu-id="ee843-131">For example, the following page describes the methods of process objects [System.Diagnostics.Process](/dotnet/api/system.diagnostics.process#methods).</span></span>

<span data-ttu-id="ee843-132">Pour déterminer les arguments d’une méthode, examinez la définition de la méthode, qui est semblable au diagramme de syntaxe d’une applet de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee843-132">To determine the arguments of a method, review the method definition, which is like the syntax diagram of a PowerShell cmdlet.</span></span>

<span data-ttu-id="ee843-133">Une définition de méthode peut avoir une ou plusieurs signatures de méthode, qui sont similaires aux jeux de paramètres des applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee843-133">A method definition might have one or more method signatures, which are like the parameter sets of PowerShell cmdlets.</span></span> <span data-ttu-id="ee843-134">Les signatures affichent tous les formats de commandes valides pour appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="ee843-134">The signatures show all of the valid formats of commands to invoke the method.</span></span>

<span data-ttu-id="ee843-135">Par exemple, la `CopyTo` méthode de la `FileInfo` classe contient les deux signatures de méthode suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee843-135">For example, the `CopyTo` method of the `FileInfo` class contains the following two method signatures:</span></span>

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

<span data-ttu-id="ee843-136">La première signature de méthode prend le nom de fichier de destination (et un chemin d’accès).</span><span class="sxs-lookup"><span data-stu-id="ee843-136">The first method signature takes the destination file name (and a path).</span></span> <span data-ttu-id="ee843-137">L’exemple suivant utilise la première `CopyTo` méthode pour copier le `Final.txt` fichier dans le `C:\Bin` répertoire.</span><span class="sxs-lookup"><span data-stu-id="ee843-137">The following example uses the first `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> <span data-ttu-id="ee843-138">Contrairement au mode d' _argument_ de PowerShell, les méthodes d’objet s’exécutent en mode _expression_ , qui est un transfert vers le .NET Framework sur lequel PowerShell est basé.</span><span class="sxs-lookup"><span data-stu-id="ee843-138">Unlike PowerShell's _argument_ mode, object methods execute in _expression_ mode, which is a pass-through to the .NET framework that PowerShell is built on.</span></span> <span data-ttu-id="ee843-139">En mode _expression_ , les arguments **bareword** (chaînes sans guillemets) ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="ee843-139">In _expression_ mode **bareword** arguments (unquoted strings) are not allowed.</span></span> <span data-ttu-id="ee843-140">Vous pouvez voir cette différence lorsque vous utilisez un chemin d’accès en tant que paramètre, par opposition au chemin d’accès en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="ee843-140">You can see this difference when using a the path as a parameter, versus the path as an argument.</span></span> <span data-ttu-id="ee843-141">Pour plus d’informations sur les modes d’analyse, consultez [about_Parsing](about_Parsing.md)</span><span class="sxs-lookup"><span data-stu-id="ee843-141">You can read more about parsing modes in [about_Parsing](about_Parsing.md)</span></span>

<span data-ttu-id="ee843-142">La deuxième signature de méthode accepte un nom de fichier de destination et une valeur booléenne qui détermine si le fichier de destination doit être remplacé, s’il existe déjà.</span><span class="sxs-lookup"><span data-stu-id="ee843-142">The second method signature takes a destination file name and a Boolean value that determines whether the destination file should be overwritten, if it already exists.</span></span>

<span data-ttu-id="ee843-143">L’exemple suivant utilise la deuxième `CopyTo` méthode pour copier le `Final.txt` fichier dans le `C:\Bin` répertoire, et pour remplacer les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="ee843-143">The following example uses the second `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory, and to overwrite existing files.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a><span data-ttu-id="ee843-144">Méthodes d’objets scalaires et de collections</span><span class="sxs-lookup"><span data-stu-id="ee843-144">Methods of Scalar objects and Collections</span></span>

<span data-ttu-id="ee843-145">Les méthodes d’un objet (« scalaire ») d’un type particulier sont souvent différentes des méthodes d’une collection d’objets du même type.</span><span class="sxs-lookup"><span data-stu-id="ee843-145">The methods of one ("scalar") object of a particular type are often different from the methods of a collection of objects of the same type.</span></span>

<span data-ttu-id="ee843-146">Par exemple, chaque processus a une `Kill` méthode, mais une collection de processus n’a pas de méthode Kill.</span><span class="sxs-lookup"><span data-stu-id="ee843-146">For example, every process has a `Kill` method, but a collection of processes does not have a Kill method.</span></span>

<span data-ttu-id="ee843-147">À compter de PowerShell 3,0, PowerShell tente d’éviter les erreurs de script qui résultent des différentes méthodes d’objets scalaires et de collections.</span><span class="sxs-lookup"><span data-stu-id="ee843-147">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing methods of scalar objects and collections.</span></span>

<span data-ttu-id="ee843-148">Si vous envoyez une collection, mais que vous demandez une méthode qui existe uniquement sur des objets (« scalaires ») uniques, PowerShell appelle la méthode sur chaque objet de la collection.</span><span class="sxs-lookup"><span data-stu-id="ee843-148">If you submit a collection, but request a method that exists only on single ("scalar") objects, PowerShell invokes the method on every object in the collection.</span></span>

<span data-ttu-id="ee843-149">Si la méthode existe sur les objets individuels et sur la collection, seule la méthode de la collection est appelée.</span><span class="sxs-lookup"><span data-stu-id="ee843-149">If the method exists on the individual objects and on the collection, only the collection's method is invoked.</span></span>

<span data-ttu-id="ee843-150">Cette fonctionnalité fonctionne également sur les propriétés des collections et des objets scalaires.</span><span class="sxs-lookup"><span data-stu-id="ee843-150">This feature also works on properties of scalar objects and collections.</span></span> <span data-ttu-id="ee843-151">Pour plus d’informations, consultez [about_Properties](about_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="ee843-151">For more information, see [about_Properties](about_Properties.md).</span></span>

### <a name="examples"></a><span data-ttu-id="ee843-152">Exemples</span><span class="sxs-lookup"><span data-stu-id="ee843-152">Examples</span></span>

<span data-ttu-id="ee843-153">L’exemple suivant exécute la méthode **Kill** des objets de processus individuels dans une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="ee843-153">The following example runs the **Kill** method of individual process objects in a collection of objects.</span></span>

<span data-ttu-id="ee843-154">La première commande démarre trois instances du processus Notepad.</span><span class="sxs-lookup"><span data-stu-id="ee843-154">The first command starts three instances of the Notepad process.</span></span> <span data-ttu-id="ee843-155">`Get-Process` Obtient les trois instances du processus Notepad et les enregistre dans la `$p` variable.</span><span class="sxs-lookup"><span data-stu-id="ee843-155">`Get-Process` gets all three instance of the Notepad process and saves them in the `$p` variable.</span></span>

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

<span data-ttu-id="ee843-156">La commande suivante exécute la méthode **Kill** sur les trois processus de la `$p` variable.</span><span class="sxs-lookup"><span data-stu-id="ee843-156">The next command runs the **Kill** method on all three processes in the `$p` variable.</span></span> <span data-ttu-id="ee843-157">Cette commande fonctionne même si une collection de processus n’a pas de `Kill` méthode.</span><span class="sxs-lookup"><span data-stu-id="ee843-157">This command works even though a collection of processes does not have a `Kill` method.</span></span>

```powershell
$p.Kill()
Get-Process Notepad
```

<span data-ttu-id="ee843-158">La `Get-Process` commande confirme que la `Kill` méthode a fonctionné.</span><span class="sxs-lookup"><span data-stu-id="ee843-158">The `Get-Process` command confirms that the `Kill` method worked.</span></span>

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

<span data-ttu-id="ee843-159">Cet exemple est fonctionnellement équivalent à l’utilisation de l' `Foreach-Object` applet de commande pour exécuter la méthode sur chaque objet de la collection.</span><span class="sxs-lookup"><span data-stu-id="ee843-159">This example is functionally equivalent to using the `Foreach-Object` cmdlet to run the method on each object in the collection.</span></span>

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a><span data-ttu-id="ee843-160">Méthodes ForEach et where</span><span class="sxs-lookup"><span data-stu-id="ee843-160">ForEach and Where methods</span></span>

<span data-ttu-id="ee843-161">À compter de PowerShell 4,0, le filtrage de collection à l’aide d’une syntaxe de méthode est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ee843-161">Beginning in PowerShell 4.0, collection filtering by using a method syntax is supported.</span></span> <span data-ttu-id="ee843-162">Cela permet d’utiliser deux nouvelles méthodes pour traiter les collections `ForEach` et `Where` .</span><span class="sxs-lookup"><span data-stu-id="ee843-162">This allows use of two new methods when dealing with collections `ForEach` and `Where`.</span></span>

<span data-ttu-id="ee843-163">Vous pouvez en savoir plus sur ces méthodes dans [about_arrays](about_arrays.md)</span><span class="sxs-lookup"><span data-stu-id="ee843-163">You can read more about these methods in [about_arrays](about_arrays.md)</span></span>

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a><span data-ttu-id="ee843-164">Appel d’une méthode spécifique quand plusieurs surcharges existent</span><span class="sxs-lookup"><span data-stu-id="ee843-164">Calling a specific method when multiple overloads exist</span></span>

<span data-ttu-id="ee843-165">Considérez le scénario suivant lors de l’appel de méthodes .NET.</span><span class="sxs-lookup"><span data-stu-id="ee843-165">Consider the following scenario when calling .NET methods.</span></span> <span data-ttu-id="ee843-166">Si une méthode prend un objet mais a une surcharge via une interface qui prend un type plus spécifique, PowerShell choisit la méthode qui accepte l’objet, sauf si vous effectuez un cast explicite vers cette interface.</span><span class="sxs-lookup"><span data-stu-id="ee843-166">If a method takes an object but has an overload via an interface taking a more specific type, PowerShell chooses the method that accepts the object unless you explicitly cast it to that interface.</span></span>

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

<span data-ttu-id="ee843-167">Dans cet exemple, la surcharge la plus spécifique `object` de la méthode **bar** a été choisie.</span><span class="sxs-lookup"><span data-stu-id="ee843-167">In this example the less specific `object` overload of the **Bar** method was chosen.</span></span>

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

<span data-ttu-id="ee843-168">Dans cet exemple, nous castons la méthode en interface **IFoo** pour sélectionner la surcharge plus spécifique de la méthode de la **barre** .</span><span class="sxs-lookup"><span data-stu-id="ee843-168">In this example we cast the method to the interface **IFoo** to select the more specific overload of the **Bar** method.</span></span>

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a><span data-ttu-id="ee843-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee843-169">See Also</span></span>

[<span data-ttu-id="ee843-170">about_Objects</span><span class="sxs-lookup"><span data-stu-id="ee843-170">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="ee843-171">about_Properties</span><span class="sxs-lookup"><span data-stu-id="ee843-171">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="ee843-172">Get-Member</span><span class="sxs-lookup"><span data-stu-id="ee843-172">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

