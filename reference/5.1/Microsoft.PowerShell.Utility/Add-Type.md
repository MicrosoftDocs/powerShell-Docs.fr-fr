---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: af7cd937ccfc7c5f05fd0213764ed51a3ba9f2bb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203366"
---
# <span data-ttu-id="0bc99-103">Add-Type</span><span class="sxs-lookup"><span data-stu-id="0bc99-103">Add-Type</span></span>

## <span data-ttu-id="0bc99-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0bc99-104">SYNOPSIS</span></span>
<span data-ttu-id="0bc99-105">Ajoute une classe Microsoft .NET Framework à une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-105">Adds a Microsoft .NET Framework class to a PowerShell session.</span></span>

## <span data-ttu-id="0bc99-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0bc99-106">SYNTAX</span></span>

### <span data-ttu-id="0bc99-107">FromSource (par défaut)</span><span class="sxs-lookup"><span data-stu-id="0bc99-107">FromSource (Default)</span></span>

```
Add-Type [-CodeDomProvider <CodeDomProvider>] [-CompilerParameters <CompilerParameters>]
 [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [<CommonParameters>]
```

### <span data-ttu-id="0bc99-108">FromMember</span><span class="sxs-lookup"><span data-stu-id="0bc99-108">FromMember</span></span>

```
Add-Type [-CodeDomProvider <CodeDomProvider>] [-CompilerParameters <CompilerParameters>]
 [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>] [-UsingNamespace <String[]>]
 [-Language <Language>] [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="0bc99-109">FromPath</span><span class="sxs-lookup"><span data-stu-id="0bc99-109">FromPath</span></span>

```
Add-Type [-CompilerParameters <CompilerParameters>] [-Path] <String[]>
 [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>]
 [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="0bc99-110">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="0bc99-110">FromLiteralPath</span></span>

```
Add-Type [-CompilerParameters <CompilerParameters>] -LiteralPath <String[]>
 [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>]
 [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="0bc99-111">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="0bc99-111">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

## <span data-ttu-id="0bc99-112">Description</span><span class="sxs-lookup"><span data-stu-id="0bc99-112">DESCRIPTION</span></span>

<span data-ttu-id="0bc99-113">L' `Add-Type` applet de commande vous permet de définir une classe Microsoft .NET Framework dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-113">The `Add-Type` cmdlet lets you define a Microsoft .NET Framework class in your PowerShell session.</span></span>
<span data-ttu-id="0bc99-114">Vous pouvez ensuite instancier des objets, à l’aide de l’applet de commande `New-Object` , et utiliser les objets comme vous le feriez pour n’importe quel objet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0bc99-114">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Framework object.</span></span> <span data-ttu-id="0bc99-115">Si vous ajoutez une `Add-Type` commande à votre profil PowerShell, la classe est disponible dans toutes les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-115">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="0bc99-116">Vous pouvez spécifier le type en désignant un assembly existant ou des fichiers de code source. Par ailleurs, vous pouvez spécifier le code source inline ou enregistré dans une variable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-116">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="0bc99-117">Vous pouvez même spécifier uniquement une méthode et `Add-Type` définir et générer la classe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-117">You can even specify only a method and `Add-Type` will define and generate the class.</span></span> <span data-ttu-id="0bc99-118">Sur Windows, vous pouvez utiliser cette fonctionnalité pour effectuer des appels d’appel de code non managé (P/Invoke) à des fonctions non managées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-118">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="0bc99-119">Si vous spécifiez le code source, `Add-Type` compile le code source spécifié et génère un assembly en mémoire qui contient les nouveaux types de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0bc99-119">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Framework types.</span></span>

<span data-ttu-id="0bc99-120">Vous pouvez utiliser les paramètres de `Add-Type` pour spécifier un autre langage et un autre compilateur, C# est l’option par défaut, les options du compilateur, les dépendances de l’assembly, l’espace de noms de la classe, les noms du type et l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="0bc99-120">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

## <span data-ttu-id="0bc99-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0bc99-121">EXAMPLES</span></span>

### <span data-ttu-id="0bc99-122">Exemple 1 : ajouter un type .NET à une session</span><span class="sxs-lookup"><span data-stu-id="0bc99-122">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="0bc99-123">Cet exemple ajoute la classe **BasicTest** à la session en spécifiant le code source stocké dans une variable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-123">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="0bc99-124">La classe **BasicTest** est utilisée pour ajouter des entiers, créer un objet et multiplier des entiers.</span><span class="sxs-lookup"><span data-stu-id="0bc99-124">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

<span data-ttu-id="0bc99-125">La `$Source` variable stocke le code source de la classe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-125">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="0bc99-126">Le type a une méthode statique appelée `Add` et une méthode non statique appelée `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-126">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="0bc99-127">L' `Add-Type` applet de commande ajoute la classe à la session.</span><span class="sxs-lookup"><span data-stu-id="0bc99-127">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="0bc99-128">Comme il utilise le code source en ligne, la commande utilise le paramètre **TypeDefinition** pour spécifier le code dans la `$Source` variable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-128">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="0bc99-129">La `Add` méthode statique de la classe **BasicTest** utilise les caractères double deux-points ( `::` ) pour spécifier un membre statique de la classe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-129">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="0bc99-130">Les entiers sont ajoutés et la somme est affichée.</span><span class="sxs-lookup"><span data-stu-id="0bc99-130">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="0bc99-131">L' `New-Object` applet de commande instancie une instance de la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-131">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="0bc99-132">Elle enregistre le nouvel objet dans la `$BasicTestObject` variable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-132">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="0bc99-133">`$BasicTestObject` utilise la `Multiply` méthode.</span><span class="sxs-lookup"><span data-stu-id="0bc99-133">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="0bc99-134">Les entiers sont multipliés et le produit est affiché.</span><span class="sxs-lookup"><span data-stu-id="0bc99-134">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="0bc99-135">Exemple 2 : examiner un type ajouté</span><span class="sxs-lookup"><span data-stu-id="0bc99-135">Example 2: Examine an added type</span></span>

<span data-ttu-id="0bc99-136">Cet exemple utilise l' `Get-Member` applet de commande pour examiner les objets `Add-Type` créés par les `New-Object` applets de commande et dans l' **exemple 1** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-136">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1** .</span></span>

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

<span data-ttu-id="0bc99-137">L' `Get-Member` applet de commande obtient le type et les membres de la classe **BasicTest** qui ont `Add-Type` été ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="0bc99-137">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="0bc99-138">La `Get-Member` commande révèle qu’il s’agit d’un objet **System. RuntimeType** , dérivé de la classe **System. Object** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-138">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="0bc99-139">Le `Get-Member` paramètre **static** obtient les propriétés et les méthodes statiques de la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-139">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="0bc99-140">La sortie indique que la `Add` méthode est incluse.</span><span class="sxs-lookup"><span data-stu-id="0bc99-140">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="0bc99-141">L' `Get-Member` applet de commande obtient les membres de l’objet stocké dans la `$BasicTestObject` variable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-141">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="0bc99-142">`$BasicTestObject` a été créé à l’aide de l' `New-Object` applet de commande avec la classe **BasicTest** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-142">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="0bc99-143">La sortie révèle que la valeur de la `$BasicTestObject` variable est une instance de la classe **BasicTest** et qu’elle comprend un membre appelé `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-143">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="0bc99-144">Exemple 3 : ajouter des types à partir d’un assembly</span><span class="sxs-lookup"><span data-stu-id="0bc99-144">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="0bc99-145">Cet exemple ajoute les classes de l' `Accessibility.dll` assembly à la session active.</span><span class="sxs-lookup"><span data-stu-id="0bc99-145">This example adds the classes from the `Accessibility.dll` assembly to the current session.</span></span>

```powershell
$AccType = Add-Type -AssemblyName "accessib*" -PassThru
```

<span data-ttu-id="0bc99-146">La `$AccType` variable stocke un objet créé avec l’applet de commande `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-146">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="0bc99-147">`Add-Type` utilise le paramètre **AssemblyName** pour spécifier le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0bc99-147">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="0bc99-148">Le `*` caractère générique astérisque () vous permet d’accéder à l’assembly approprié même si vous n’êtes pas sûr de son nom ou de son orthographe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-148">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="0bc99-149">Le paramètre **PassThru** génère des objets qui représentent les classes ajoutées à la session.</span><span class="sxs-lookup"><span data-stu-id="0bc99-149">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="0bc99-150">Exemple 4 : appeler des API Windows natives</span><span class="sxs-lookup"><span data-stu-id="0bc99-150">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="0bc99-151">Cet exemple montre comment appeler des API Windows natives dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-151">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="0bc99-152">`Add-Type` utilise le mécanisme d’appel de code non managé (P/Invoke) pour appeler une fonction dans `User32.dll` à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-152">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="0bc99-153">Cet exemple fonctionne uniquement sur les ordinateurs exécutant le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="0bc99-153">This example only works on computers running the Windows operating system.</span></span>

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

<span data-ttu-id="0bc99-154">La `$Signature` variable stocke la signature C# de la `ShowWindowAsync` fonction.</span><span class="sxs-lookup"><span data-stu-id="0bc99-154">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="0bc99-155">Pour vous assurer que la méthode résultante sera visible dans une session PowerShell, le `public` mot clé a été ajouté à la signature standard.</span><span class="sxs-lookup"><span data-stu-id="0bc99-155">To ensure that the resulting method will be visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="0bc99-156">Pour plus d’informations, consultez [fonction ShowWindowAsync](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span><span class="sxs-lookup"><span data-stu-id="0bc99-156">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="0bc99-157">La `$ShowWindowAsync` variable stocke l’objet créé par le `Add-Type` paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-157">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="0bc99-158">L' `Add-Type` applet de commande ajoute la `ShowWindowAsync` fonction à la session PowerShell en tant que méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0bc99-158">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="0bc99-159">La commande utilise le paramètre **MemberDefinition** pour spécifier la définition de méthode enregistrée dans la `$Signature` variable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-159">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="0bc99-160">La commande utilise les paramètres **Name** et **Namespace** pour spécifier le nom et l'espace de noms de la classe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-160">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="0bc99-161">Le paramètre **PassThru** génère un objet qui représente les types.</span><span class="sxs-lookup"><span data-stu-id="0bc99-161">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="0bc99-162">La nouvelle `ShowWindowAsync` méthode statique est utilisée dans les commandes pour réduire et restaurer la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-162">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="0bc99-163">La méthode accepte deux paramètres : le handle de fenêtre et un entier qui spécifie le mode d’affichage de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0bc99-163">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="0bc99-164">Pour réduire la console PowerShell, `ShowWindowAsync` utilise l' `Get-Process` applet de commande avec la `$PID` variable automatique pour recevoir le processus qui héberge la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="0bc99-164">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="0bc99-165">Elle utilise ensuite la propriété **MainWindowHandle** du processus actuel et la valeur `2` , qui représente la `SW_MINIMIZE` valeur.</span><span class="sxs-lookup"><span data-stu-id="0bc99-165">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="0bc99-166">Pour restaurer la fenêtre, `ShowWindowAsync` utilise la valeur `4` pour la position de la fenêtre, qui représente la `SW_RESTORE` valeur.</span><span class="sxs-lookup"><span data-stu-id="0bc99-166">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="0bc99-167">Pour agrandir la fenêtre, utilisez la valeur de `3` qui est représentée par `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-167">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

### <span data-ttu-id="0bc99-168">Exemple 5 : ajouter un type à partir d’un fichier de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bc99-168">Example 5: Add a type from a Visual Basic file</span></span>

<span data-ttu-id="0bc99-169">Cet exemple utilise l' `Add-Type` applet de commande pour ajouter la classe **VBFromFile** définie dans le `Hello.vb` fichier à la session active.</span><span class="sxs-lookup"><span data-stu-id="0bc99-169">This example uses the `Add-Type` cmdlet to add the **VBFromFile** class that's defined in the `Hello.vb` file to the current session.</span></span> <span data-ttu-id="0bc99-170">Le texte du `Hello.vb` fichier est affiché dans la sortie de la commande.</span><span class="sxs-lookup"><span data-stu-id="0bc99-170">The text of the `Hello.vb` file is shown in the command output.</span></span>

```powershell
Add-Type -Path "C:\PS-Test\Hello.vb"
[VBFromFile]::SayHello(", World")

# From Hello.vb

Public Class VBFromFile
  Public Shared Function SayHello(sourceName As String) As String
    Dim myValue As String = "Hello"
    return myValue + sourceName
  End Function
End Class
```

```Output
Hello, World
```

<span data-ttu-id="0bc99-171">`Add-Type` utilise le paramètre **path** pour spécifier le fichier source, `Hello.vb` , et ajoute le type défini dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="0bc99-171">`Add-Type` uses the **Path** parameter to specify the source file, `Hello.vb`, and adds the type defined in the file.</span></span> <span data-ttu-id="0bc99-172">La `SayHello` fonction est appelée en tant que méthode statique de la classe **VBFromFile** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-172">The `SayHello` function is called as a static method of the **VBFromFile** class.</span></span>

### <span data-ttu-id="0bc99-173">Exemple 6 : ajouter une classe avec JScript.NET</span><span class="sxs-lookup"><span data-stu-id="0bc99-173">Example 6: Add a class with JScript.NET</span></span>

<span data-ttu-id="0bc99-174">Cet exemple utilise JScript.NET pour créer une nouvelle classe, **FRectangle** , dans votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-174">This example uses JScript.NET to create a new class, **FRectangle** , in your PowerShell session.</span></span>

```powershell
Add-Type @'
 class FRectangle {
   var Length : double;
   var Height : double;
   function Perimeter() : double {
       return (Length + Height) * 2; }
   function Area() : double {
       return Length * Height;  } }
'@ -Language JScript

$rect = [FRectangle]::new()
$rect
```

```Output
Length Height
------ ------
     0      0
```

### <span data-ttu-id="0bc99-175">Exemple 7 : ajouter un compilateur F #</span><span class="sxs-lookup"><span data-stu-id="0bc99-175">Example 7: Add an F# compiler</span></span>

<span data-ttu-id="0bc99-176">Cet exemple montre comment utiliser l' `Add-Type` applet de commande pour ajouter un compilateur de code F # à votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-176">This example shows how to use the `Add-Type` cmdlet to add an F# code compiler to your PowerShell session.</span></span> <span data-ttu-id="0bc99-177">Pour exécuter cet exemple dans PowerShell, vous devez disposer du `FSharp.Compiler.CodeDom.dll` qui est installé avec le langage F #.</span><span class="sxs-lookup"><span data-stu-id="0bc99-177">To run this example in PowerShell, you must have the `FSharp.Compiler.CodeDom.dll` that is installed with the F# language.</span></span>

```powershell
Add-Type -Path "FSharp.Compiler.CodeDom.dll"
$Provider = New-Object Microsoft.FSharp.Compiler.CodeDom.FSharpCodeProvider
$FSharpCode = @"
let rec loop n =if n <= 0 then () else beginprint_endline (string_of_int n);loop (n-1)end
"@
$FSharpType = Add-Type -TypeDefinition $FSharpCode -CodeDomProvider $Provider -PassThru |
   Where-Object { $_.IsPublic }
$FSharpType::loop(4)
```

```Output
4
3
2
1
```

<span data-ttu-id="0bc99-178">`Add-Type` utilise le paramètre **path** pour spécifier un assembly et obtient les types dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0bc99-178">`Add-Type` uses the **Path** parameter to specify an assembly and gets the types in the assembly.</span></span>
<span data-ttu-id="0bc99-179">`New-Object` crée une instance du fournisseur de code F # et enregistre le résultat dans la `$Provider` variable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-179">`New-Object` creates an instance of the F# code provider and saves the result in the `$Provider` variable.</span></span> <span data-ttu-id="0bc99-180">La `$FSharpCode` variable enregistre le code F # qui définit la méthode de **boucle** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-180">The `$FSharpCode` variable saves the F# code that defines the **Loop** method.</span></span>

<span data-ttu-id="0bc99-181">La `$FSharpType` variable stocke les résultats de l' `Add-Type` applet de commande qui enregistre les types publics définis dans `$FSharpCode` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-181">The the `$FSharpType` variable stores the results of the `Add-Type` cmdlet that saves the public types defined in `$FSharpCode`.</span></span> <span data-ttu-id="0bc99-182">Le paramètre **TypeDefinition** spécifie le code source qui définit les types.</span><span class="sxs-lookup"><span data-stu-id="0bc99-182">The **TypeDefinition** parameter specifies the source code that defines the types.</span></span> <span data-ttu-id="0bc99-183">Le paramètre **CodeDomProvider** spécifie le compilateur de code source.</span><span class="sxs-lookup"><span data-stu-id="0bc99-183">The **CodeDomProvider** parameter specifies the source code compiler.</span></span> <span data-ttu-id="0bc99-184">Le paramètre **PassThru** indique `Add-Type` à de retourner un objet **Runtime** qui représente les types.</span><span class="sxs-lookup"><span data-stu-id="0bc99-184">The **PassThru** parameter directs `Add-Type` to return a **Runtime** object that represents the types.</span></span>
<span data-ttu-id="0bc99-185">Les objets sont envoyés dans le pipeline à l’applet de commande `Where-Object` , qui retourne uniquement les types publics.</span><span class="sxs-lookup"><span data-stu-id="0bc99-185">The objects are sent down the pipeline to the `Where-Object` cmdlet, which returns only the public types.</span></span> <span data-ttu-id="0bc99-186">L’applet **de commande Where-Object** est utilisée, car le fournisseur F # génère des types non publics pour prendre en charge le type public résultant.</span><span class="sxs-lookup"><span data-stu-id="0bc99-186">The **Where-Object** cmdlet is used because the F# provider generates non-public types to support the resulting public type.</span></span>

<span data-ttu-id="0bc99-187">La méthode Loop est appelée en tant que méthode statique du type stocké dans la `$FSharpType` variable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-187">The Loop method is called as a static method of the type stored in the `$FSharpType` variable.</span></span>

## <span data-ttu-id="0bc99-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0bc99-188">PARAMETERS</span></span>

### <span data-ttu-id="0bc99-189">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="0bc99-189">-AssemblyName</span></span>

<span data-ttu-id="0bc99-190">Spécifie le nom d'un assembly qui inclut les types.</span><span class="sxs-lookup"><span data-stu-id="0bc99-190">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="0bc99-191">`Add-Type` prend les types de l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="0bc99-191">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="0bc99-192">Ce paramètre est obligatoire lorsque vous créez des types basés sur un nom d’assembly.</span><span class="sxs-lookup"><span data-stu-id="0bc99-192">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="0bc99-193">Entrez le nom complet ou simple, également appelé « nom partiel », d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="0bc99-193">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="0bc99-194">Les caractères génériques sont autorisés dans le nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="0bc99-194">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="0bc99-195">Si vous entrez un nom simple ou partiel, `Add-Type` le résout en nom complet, puis utilise le nom complet pour charger l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0bc99-195">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="0bc99-196">Ce paramètre n’accepte pas de chemin d’accès ou de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="0bc99-196">This parameter doesn't accept a path or a file name.</span></span> <span data-ttu-id="0bc99-197">Pour entrer le chemin d’accès au fichier de bibliothèque de liens dynamiques (DLL) de l’assembly, utilisez le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-197">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0bc99-198">-CodeDomProvider</span><span class="sxs-lookup"><span data-stu-id="0bc99-198">-CodeDomProvider</span></span>

<span data-ttu-id="0bc99-199">Spécifie un générateur de code ou un compilateur.</span><span class="sxs-lookup"><span data-stu-id="0bc99-199">Specifies a code generator or compiler.</span></span> <span data-ttu-id="0bc99-200">`Add-Type` utilise le compilateur spécifié pour compiler le code source.</span><span class="sxs-lookup"><span data-stu-id="0bc99-200">`Add-Type` uses the specified compiler to compile the source code.</span></span> <span data-ttu-id="0bc99-201">La valeur par défaut est le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="0bc99-201">The default is the C# compiler.</span></span> <span data-ttu-id="0bc99-202">Utilisez ce paramètre si vous utilisez un langage qui ne peut pas être spécifié à l’aide du paramètre **Language** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-202">Use this parameter if you're using a language that can't be specified by using the **Language** parameter.</span></span> <span data-ttu-id="0bc99-203">Le **CodeDomProvider** que vous spécifiez doit pouvoir générer des assemblys à partir du code source.</span><span class="sxs-lookup"><span data-stu-id="0bc99-203">The **CodeDomProvider** that you specify must be able to generate assemblies from source code.</span></span>

```yaml
Type: System.CodeDom.Compiler.CodeDomProvider
Parameter Sets: FromSource, FromMember
Aliases: Provider

Required: False
Position: Named
Default value: C# compiler
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-204">-CompilerParameters</span><span class="sxs-lookup"><span data-stu-id="0bc99-204">-CompilerParameters</span></span>

<span data-ttu-id="0bc99-205">Spécifie les options du compilateur de code source.</span><span class="sxs-lookup"><span data-stu-id="0bc99-205">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="0bc99-206">Ces options sont envoyées au compilateur sans révision.</span><span class="sxs-lookup"><span data-stu-id="0bc99-206">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="0bc99-207">Ce paramètre vous permet de demander au compilateur de générer un fichier exécutable, d’incorporer des ressources ou de définir des options de ligne de commande, telles que l' `/unsafe` option.</span><span class="sxs-lookup"><span data-stu-id="0bc99-207">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span> <span data-ttu-id="0bc99-208">Ce paramètre implémente la classe **CompilerParameters** , **System. CodeDom. Compiler. CompilerParameters** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-208">This parameter implements the **CompilerParameters** class, **System.CodeDom.Compiler.CompilerParameters** .</span></span>

<span data-ttu-id="0bc99-209">Vous ne pouvez pas utiliser les paramètres **CompilerParameters** et **ReferencedAssemblies** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="0bc99-209">You can't use the **CompilerParameters** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.CodeDom.Compiler.CompilerParameters
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: CP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-210">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="0bc99-210">-IgnoreWarnings</span></span>

<span data-ttu-id="0bc99-211">Ignore les avertissements du compilateur.</span><span class="sxs-lookup"><span data-stu-id="0bc99-211">Ignores compiler warnings.</span></span> <span data-ttu-id="0bc99-212">Utilisez ce paramètre pour empêcher `Add-Type` de gérer les avertissements du compilateur comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="0bc99-212">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-213">-Langage</span><span class="sxs-lookup"><span data-stu-id="0bc99-213">-Language</span></span>

<span data-ttu-id="0bc99-214">Spécifie la langue utilisée dans le code source.</span><span class="sxs-lookup"><span data-stu-id="0bc99-214">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="0bc99-215">L' `Add-Type` applet de commande utilise la valeur de ce paramètre pour sélectionner le **CodeDomProvider** approprié.</span><span class="sxs-lookup"><span data-stu-id="0bc99-215">The `Add-Type` cmdlet uses the value of this parameter to select the appropriate **CodeDomProvider** .</span></span> <span data-ttu-id="0bc99-216">CSharp est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bc99-216">CSharp is the default value.</span></span> <span data-ttu-id="0bc99-217">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bc99-217">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="0bc99-218">CSharp</span><span class="sxs-lookup"><span data-stu-id="0bc99-218">CSharp</span></span>
- <span data-ttu-id="0bc99-219">CSharpVersion2</span><span class="sxs-lookup"><span data-stu-id="0bc99-219">CSharpVersion2</span></span>
- <span data-ttu-id="0bc99-220">CSharpVersion3</span><span class="sxs-lookup"><span data-stu-id="0bc99-220">CSharpVersion3</span></span>
- <span data-ttu-id="0bc99-221">JScript</span><span class="sxs-lookup"><span data-stu-id="0bc99-221">JScript</span></span>
- <span data-ttu-id="0bc99-222">VisualBasic</span><span class="sxs-lookup"><span data-stu-id="0bc99-222">VisualBasic</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp, CSharpVersion2, CSharpVersion3, JScript, VisualBasic

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-223">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0bc99-223">-LiteralPath</span></span>

<span data-ttu-id="0bc99-224">Spécifie le chemin d'accès aux fichiers de code source ou aux fichiers DLL d'assembly contenant les types.</span><span class="sxs-lookup"><span data-stu-id="0bc99-224">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="0bc99-225">Contrairement à **path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="0bc99-225">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="0bc99-226">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="0bc99-226">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0bc99-227">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="0bc99-227">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0bc99-228">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="0bc99-228">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-229">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="0bc99-229">-MemberDefinition</span></span>

<span data-ttu-id="0bc99-230">Spécifie les nouvelles propriétés ou méthodes de la classe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-230">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="0bc99-231">`Add-Type` génère le code de modèle qui est requis pour prendre en charge les propriétés ou les méthodes.</span><span class="sxs-lookup"><span data-stu-id="0bc99-231">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="0bc99-232">Sur Windows, vous pouvez utiliser cette fonctionnalité pour effectuer des appels d’appel de code non managé (P/Invoke) à des fonctions non managées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-232">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-233">-Name</span><span class="sxs-lookup"><span data-stu-id="0bc99-233">-Name</span></span>

<span data-ttu-id="0bc99-234">Spécifie le nom de la classe à créer.</span><span class="sxs-lookup"><span data-stu-id="0bc99-234">Specifies the name of the class to create.</span></span> <span data-ttu-id="0bc99-235">Ce paramètre est obligatoire durant la génération d'un type à partir d'une définition de membre.</span><span class="sxs-lookup"><span data-stu-id="0bc99-235">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="0bc99-236">Le nom de type et l'espace de noms doivent être uniques au sein d'une session.</span><span class="sxs-lookup"><span data-stu-id="0bc99-236">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="0bc99-237">Vous ne pouvez pas décharger un type ni le modifier.</span><span class="sxs-lookup"><span data-stu-id="0bc99-237">You can't unload a type or change it.</span></span>
<span data-ttu-id="0bc99-238">Pour modifier le code d’un type, vous devez modifier le nom ou démarrer une nouvelle session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-238">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="0bc99-239">Sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="0bc99-239">Otherwise, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-240">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="0bc99-240">-Namespace</span></span>

<span data-ttu-id="0bc99-241">Spécifie un espace de noms pour le type.</span><span class="sxs-lookup"><span data-stu-id="0bc99-241">Specifies a namespace for the type.</span></span>

<span data-ttu-id="0bc99-242">Si ce paramètre n’est pas inclus dans la commande, le type est créé dans l’espace de noms **Microsoft. PowerShell. Commands. AddType. AutogeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-242">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="0bc99-243">Si le paramètre est inclus dans la commande avec une valeur de chaîne vide ou une valeur de `$Null` , le type est généré dans l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="0bc99-243">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-244">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="0bc99-244">-OutputAssembly</span></span>

<span data-ttu-id="0bc99-245">Génère un fichier DLL pour l'assembly ayant le nom spécifié à l'emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="0bc99-245">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="0bc99-246">Entrez un chemin d’accès et un nom de fichier facultatifs.</span><span class="sxs-lookup"><span data-stu-id="0bc99-246">Enter an optional path and file name.</span></span> <span data-ttu-id="0bc99-247">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0bc99-247">Wildcard characters are permitted.</span></span> <span data-ttu-id="0bc99-248">Par défaut, `Add-Type` génère l’assembly uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0bc99-248">By default, `Add-Type` generates the assembly only in memory.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0bc99-249">-OutputType</span><span class="sxs-lookup"><span data-stu-id="0bc99-249">-OutputType</span></span>

<span data-ttu-id="0bc99-250">Spécifie le type de sortie de l'assembly de sortie.</span><span class="sxs-lookup"><span data-stu-id="0bc99-250">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="0bc99-251">Par défaut, aucun type de sortie n'est spécifié.</span><span class="sxs-lookup"><span data-stu-id="0bc99-251">By default, no output type is specified.</span></span> <span data-ttu-id="0bc99-252">Ce paramètre est valide uniquement quand un assembly de sortie est spécifié dans la commande.</span><span class="sxs-lookup"><span data-stu-id="0bc99-252">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="0bc99-253">Pour plus d’informations sur les valeurs, consultez [énumération OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span><span class="sxs-lookup"><span data-stu-id="0bc99-253">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="0bc99-254">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bc99-254">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="0bc99-255">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="0bc99-255">ConsoleApplication</span></span>
- <span data-ttu-id="0bc99-256">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="0bc99-256">Library</span></span>
- <span data-ttu-id="0bc99-257">Fichier WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="0bc99-257">WindowsApplication</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-258">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0bc99-258">-PassThru</span></span>

<span data-ttu-id="0bc99-259">Retourne un objet **System.Runtime** qui représente les types ajoutés.</span><span class="sxs-lookup"><span data-stu-id="0bc99-259">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="0bc99-260">Par défaut, cette applet de commande ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="0bc99-260">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-261">-Path</span><span class="sxs-lookup"><span data-stu-id="0bc99-261">-Path</span></span>

<span data-ttu-id="0bc99-262">Spécifie le chemin d'accès aux fichiers de code source ou aux fichiers DLL d'assembly contenant les types.</span><span class="sxs-lookup"><span data-stu-id="0bc99-262">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="0bc99-263">Si vous envoyez des fichiers de code source, `Add-Type` compile le code dans les fichiers et crée un assembly en mémoire des types.</span><span class="sxs-lookup"><span data-stu-id="0bc99-263">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="0bc99-264">L’extension de nom de fichier spécifiée dans la valeur de **path** détermine le compilateur utilisé par `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-264">The file name extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="0bc99-265">Si vous envoyez un fichier d’assembly, `Add-Type` utilise les types de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0bc99-265">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="0bc99-266">Pour spécifier un assembly en mémoire ou le Global Assembly Cache, utilisez le paramètre **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-266">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-267">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="0bc99-267">-ReferencedAssemblies</span></span>

<span data-ttu-id="0bc99-268">Spécifie les assemblys dont dépend le type.</span><span class="sxs-lookup"><span data-stu-id="0bc99-268">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="0bc99-269">Par défaut, `Add-Type` `System.dll` les références et `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-269">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="0bc99-270">Les assemblys que vous spécifiez à l'aide de ce paramètre sont référencés en plus des assemblys par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bc99-270">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="0bc99-271">Vous ne pouvez pas utiliser les paramètres **CompilerParameters** et **ReferencedAssemblies** dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="0bc99-271">You can't use the **CompilerParameters** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-272">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="0bc99-272">-TypeDefinition</span></span>

<span data-ttu-id="0bc99-273">Spécifie le code source qui contient les définitions de type.</span><span class="sxs-lookup"><span data-stu-id="0bc99-273">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="0bc99-274">Entrez le code source dans une chaîne ou une chaîne here-string, ou entrez une variable qui contient le code source.</span><span class="sxs-lookup"><span data-stu-id="0bc99-274">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="0bc99-275">Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="0bc99-275">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="0bc99-276">Incluez une déclaration d'espace de noms dans votre définition de type.</span><span class="sxs-lookup"><span data-stu-id="0bc99-276">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="0bc99-277">Si vous omettez la déclaration d'espace de noms, votre type risque d'avoir le même nom qu'un autre type ou que le raccourci d'un autre type, ce qui entraînera un remplacement involontaire.</span><span class="sxs-lookup"><span data-stu-id="0bc99-277">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="0bc99-278">Par exemple, si vous définissez un type appelé **exception** , les scripts qui utilisent une **exception** comme raccourci pour **System. exception** échoueront.</span><span class="sxs-lookup"><span data-stu-id="0bc99-278">For example, if you define a type called **Exception** , scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-279">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="0bc99-279">-UsingNamespace</span></span>

<span data-ttu-id="0bc99-280">Spécifie les autres espaces de noms nécessaires pour la classe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-280">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="0bc99-281">C’est très similaire au mot clé C#, `Using` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-281">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="0bc99-282">Par défaut, `Add-Type` fait référence à l’espace de noms **System** .</span><span class="sxs-lookup"><span data-stu-id="0bc99-282">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="0bc99-283">Lorsque le paramètre **MemberDefinition** est utilisé, `Add-Type` fait également référence à l’espace de noms **System. Runtime. InteropServices** par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bc99-283">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="0bc99-284">Les espaces de noms que vous ajoutez à l'aide du paramètre **UsingNamespace** sont référencés en plus des espaces de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bc99-284">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bc99-285">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0bc99-285">CommonParameters</span></span>

<span data-ttu-id="0bc99-286">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0bc99-286">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0bc99-287">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0bc99-287">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0bc99-288">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0bc99-288">INPUTS</span></span>

### <span data-ttu-id="0bc99-289">Aucun</span><span class="sxs-lookup"><span data-stu-id="0bc99-289">None</span></span>

<span data-ttu-id="0bc99-290">Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-290">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="0bc99-291">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0bc99-291">OUTPUTS</span></span>

### <span data-ttu-id="0bc99-292">None ou System. type</span><span class="sxs-lookup"><span data-stu-id="0bc99-292">None or System.Type</span></span>

<span data-ttu-id="0bc99-293">Quand vous utilisez le paramètre **PassThru** , `Add-Type` retourne un objet **System. type** qui représente le nouveau type.</span><span class="sxs-lookup"><span data-stu-id="0bc99-293">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="0bc99-294">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="0bc99-294">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="0bc99-295">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0bc99-295">NOTES</span></span>

<span data-ttu-id="0bc99-296">Les types que vous ajoutez existent uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0bc99-296">The types that you add exist only in the current session.</span></span> <span data-ttu-id="0bc99-297">Pour utiliser les types dans toutes les sessions, ajoutez-les à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-297">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="0bc99-298">Pour plus d’informations sur le profil, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0bc99-298">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="0bc99-299">Les noms de types et les espaces de noms doivent être uniques au sein d’une session.</span><span class="sxs-lookup"><span data-stu-id="0bc99-299">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="0bc99-300">Vous ne pouvez pas décharger un type ni le modifier.</span><span class="sxs-lookup"><span data-stu-id="0bc99-300">You can't unload a type or change it.</span></span> <span data-ttu-id="0bc99-301">Si vous avez besoin de modifier le code d’un type, vous devez modifier le nom ou démarrer une nouvelle session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bc99-301">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="0bc99-302">Sinon, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="0bc99-302">Otherwise, the command fails.</span></span>

<span data-ttu-id="0bc99-303">La classe **CodeDomProvider** pour certains langages, tels que IronPython et J#, ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="0bc99-303">The **CodeDomProvider** class for some languages, such as IronPython and J#, doesn't generate output.</span></span> <span data-ttu-id="0bc99-304">Par conséquent, les types écrits dans ces langages ne peuvent pas être utilisés avec `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="0bc99-304">As a result, types written in these languages can't be used with `Add-Type`.</span></span>

<span data-ttu-id="0bc99-305">Cette applet de commande est basée sur la [classe](/dotnet/api/system.codedom.compiler.codedomprovider)Microsoft .NET Framework CodeDomProvider.</span><span class="sxs-lookup"><span data-stu-id="0bc99-305">This cmdlet is based on the Microsoft .NET Framework [CodeDomProvider Class](/dotnet/api/system.codedom.compiler.codedomprovider).</span></span>

## <span data-ttu-id="0bc99-306">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0bc99-306">RELATED LINKS</span></span>

[<span data-ttu-id="0bc99-307">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="0bc99-307">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="0bc99-308">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="0bc99-308">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="0bc99-309">Add-Member</span><span class="sxs-lookup"><span data-stu-id="0bc99-309">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="0bc99-310">New-Object</span><span class="sxs-lookup"><span data-stu-id="0bc99-310">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="0bc99-311">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="0bc99-311">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="0bc99-312">Appel de code non managé (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="0bc99-312">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="0bc99-313">Where-Object</span><span class="sxs-lookup"><span data-stu-id="0bc99-313">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
